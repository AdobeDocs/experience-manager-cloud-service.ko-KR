---
title: Dispatcher 도구(기존)를 사용하여 유효성 검사 및 디버깅
description: Dispatcher 도구(기존)를 사용하여 유효성 검사 및 디버깅
feature: Dispatcher
hidefromtoc: true
source-git-commit: 0a68f87e3124ac1a1c37ba66381f7e69cffaf243
workflow-type: tm+mt
source-wordcount: '2305'
ht-degree: 0%

---

# Dispatcher 도구(기존)를 사용하여 유효성 검사 및 디버깅  {#Dispatcher-tools-legacy}

## 소개 {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>클라우드의 Dispatcher 및 Dispatcher 도구를 다운로드하는 방법에 대한 자세한 내용은 Cloud](/help/implementing/dispatcher/disp-overview.md) 페이지의 [Dispatcher 를 참조하십시오.

다음 섹션에서는 레거시 모드 파일 구조, 로컬 유효성 검사, 디버깅 및 기존 모드에서 [유연한 모드](/help/implementing/dispatcher/validation-debug.md)로 마이그레이션하는 방법에 대해 설명합니다.

이 문서에서는 프로젝트의 Dispatcher 구성에 파일 옵트인/USE_SOURCES_DIRECT가 포함되지 않는다고 가정합니다. 따라서 파일 수와 크기(예:

* 사이트에 고유한 파일이 아닌 사용해야 하는 단일 재작성 파일입니다.
* 사용자 지정 가능한 파일의 내용 합계는 1MB보다 작아야 합니다.

Cloud Manager 2021.7.0 릴리스부터 새 Cloud Manager 프로그램은 위의 파일을 포함하는 AEM 원형 28 이상을 사용하여 maven 프로젝트 구조를 생성합니다.

마이그레이션 섹션 [기존 모드에서 유연한 모드](#migrating-flexible)로 마이그레이션에 설명된 대로 레거시 모드에서 유연한 모드로 마이그레이션하는 것이 좋습니다&#x200B;**적극 권장**. 또한 유연한 모드를 사용하면 SDK 및 런타임에서 개선된 방식으로 구성을 확인하고 배포합니다.

## 파일 구조 {#legacy-mode-file-structure}

프로젝트의 Dispatcher 하위 폴더(레거시 모드)의 구조는 다음과 같습니다.

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── default.vhost -> ../available_vhosts/default.vhost
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
└── conf.dispatcher.d
    ├── available_farms
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── default.farm -> ../available_farms/default.farm
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
        ├── default_virtualhosts.any
        └── virtualhosts.any
```

다음은 수정할 수 있는 주목할 만한 파일에 대한 설명입니다.

**사용자 정의 가능한 파일**

다음 파일은 사용자 지정할 수 있으며 배포 시 클라우드 인스턴스로 전송됩니다.

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

이러한 파일을 하나 이상 보유할 수 있습니다. 여기에는 호스트 이름과 일치하고 Apache가 다른 규칙으로 각 도메인 트래픽을 처리할 수 있도록 허용하는 `<VirtualHost>` 항목이 포함되어 있습니다. 파일은 `available_vhosts` 디렉토리에 만들어지고 `enabled_vhosts` 디렉토리에 심볼 링크로 활성화됩니다. `.vhost` 파일에서 rewrites 및 변수와 같은 다른 파일이 포함됩니다.

* `conf.d/rewrites/rewrite.rules`

이 파일은 `.vhost` 파일 내부에서 포함됩니다. `mod_rewrite`에 대한 재작성 규칙 세트가 있습니다.

>[!NOTE]
>
>현재 사이트에 고유한 파일이 아닌 단일 재작성 파일을 사용해야 합니다. 일반적으로 사용자 지정 가능한 파일의 콘텐츠 합계는 1MB보다 작아야 합니다.

* `conf.d/variables/custom.vars`

이 파일은 `.vhost` 파일 내부에서 포함됩니다. 이 위치에 Apache 변수에 대한 정의를 추가할 수 있습니다.

* `conf.d/variables/global.vars`

이 파일은 `dispatcher_vhost.conf` 파일 내부에서 포함됩니다. 이 파일에서 Dispatcher를 변경하고 로그 수준을 다시 작성할 수 있습니다.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

이러한 파일 중 하나 이상이 있을 수 있으며 이러한 파일에는 호스트 이름을 일치시키고 Dispatcher 모듈에서 각 팜을 다른 규칙으로 처리할 수 있도록 하는 팜이 포함되어 있습니다. 파일은 `available_farms` 디렉토리에 만들어지고 `enabled_farms` 디렉토리에 심볼 링크로 활성화됩니다. `.farm` 파일에서 필터, 캐시 규칙 등의 다른 파일이 포함됩니다.

* `conf.dispatcher.d/cache/rules.any`

이 파일은 `.farm` 파일 내부에서 포함됩니다. 캐싱 기본 설정을 지정합니다.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

이 파일은 `.farm` 파일 내부에서 포함됩니다. 백엔드에 전달해야 하는 요청 헤더를 지정합니다.

* `conf.dispatcher.d/filters/filters.any`

이 파일은 `.farm` 파일 내부에서 포함됩니다. 여기에는 필터링해야 하는 트래픽을 변경하고 백엔드로 만들지 않는 규칙 세트가 있습니다.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

이 파일은 `.farm` 파일 내부에서 포함됩니다. 전체 일치로 일치시킬 호스트 이름 또는 URI 경로 목록이 있습니다. 이렇게 하면 요청을 제공하는 데 사용할 백엔드가 결정됩니다.

위의 파일은 아래 나열된 변경할 수 없는 구성 파일을 참조합니다. 변경할 수 없는 파일에 대한 변경 사항은 클라우드 환경에서 Dispatcher가 처리하지 않습니다.

**변경할 수 없는 구성 파일**

이러한 파일은 기본 프레임워크의 일부이며 표준 및 모범 사례를 적용합니다. 파일은 로컬로 수정하거나 삭제해도 클라우드 인스턴스로 전송되지 않으므로 배포에 영향을 주지 않으므로 변경할 수 없습니다.

위의 파일은 아래 나열된 변경할 수 없는 파일을 참조한 후 추가 문 또는 무시를 참조하는 것이 좋습니다. Dispatcher 구성이 클라우드 환경에 배포되면 로컬 개발에 사용된 버전에 관계없이 최신 버전의 변경할 수 없는 파일이 사용됩니다.

* `conf.d/available_vhosts/default.vhost`

샘플 가상 호스트를 포함합니다. 가상 호스트의 경우 이 파일의 복사본을 만들고 사용자 지정한 다음 `conf.d/enabled_vhosts`(으)로 이동하여 사용자 지정된 복사본에 대한 심볼 링크를 만듭니다.

* `conf.d/dispatcher_vhost.conf`

가상 호스트 및 글로벌 변수가 포함된 방법을 보여주는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.d/rewrites/default_rewrite.rules`

표준 프로젝트에 적합한 기본 재작성 규칙입니다. 사용자 지정이 필요한 경우 `rewrite.rules`을 수정합니다. 사용자 지정에서는 사용자의 요구 사항에 맞는 경우 먼저 기본 규칙을 포함할 수 있습니다.

* `conf.dispatcher.d/available_farms/default.farm`

샘플 Dispatcher 팜을 포함합니다. 팜의 경우 이 파일의 복사본을 만들고 사용자 지정하고 `conf.d/enabled_farms`으로 이동하여 사용자 지정된 복사본에 대한 심볼 링크를 만듭니다.

* `conf.dispatcher.d/cache/default_invalidate.any`

시작 시 기본 프레임워크의 일부로 생성됩니다. 정의한 모든 팜에 이 파일을 포함하려면 **필수**&#x200B;입니다(`cache/allowedClients` 섹션).

* `conf.dispatcher.d/cache/default_rules.any`

표준 프로젝트에 적합한 기본 캐시 규칙. 사용자 지정이 필요한 경우 `conf.dispatcher.d/cache/rules.any`을 수정합니다. 사용자 지정에서는 사용자의 요구 사항에 맞는 경우 먼저 기본 규칙을 포함할 수 있습니다.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

표준 프로젝트에 적합한 기본 요청 헤더가 백엔드에 전달됩니다. 사용자 지정이 필요한 경우 `clientheaders.any`을 수정합니다. 사용자 지정에서는 사용자의 요구 사항에 맞는 경우 먼저 기본 요청 헤더를 포함할 수 있습니다.

* `conf.dispatcher.d/dispatcher.any`

Dispatcher 팜이 포함된 방법을 보여주는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.dispatcher.d/filters/default_filters.any`

표준 프로젝트에 적합한 기본 필터입니다. 사용자 지정이 필요한 경우 `filters.any`을 수정합니다. 사용자 지정에서 사용자의 요구 사항에 맞는 경우 먼저 기본 필터를 포함할 수 있습니다.

* `conf.dispatcher.d/renders/default_renders.any`

기본 프레임워크의 일부로, 시작 시 이 파일이 생성됩니다. 정의한 모든 팜에 이 파일을 포함하려면 **필수**&#x200B;입니다(`renders` 섹션).

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

표준 프로젝트에 적합한 기본 호스트 글로빙. 사용자 지정이 필요한 경우 `virtualhosts.any`을 수정합니다. 사용자 지정에서는 모든&#x200B;**수신 요청과 일치하므로 기본 호스트 글로빙을 포함하지 않아야 합니다.**

## 지원되는 Apache 모듈 {#apache-modules}

[지원되는 Apache 모듈](/help/implementing/dispatcher/disp-overview.md#supported-directives)을 참조하십시오.

## 로컬 유효성 검사 {#local-validation-legacy-mode}

>[!NOTE]
>아래 섹션에는 SDK의 Mac 또는 Linux 버전을 사용하는 명령이 포함되어 있지만 Windows SDK는 유사한 방식으로 사용할 수도 있습니다.

아래 표시된 대로 `validate.sh` 스크립트를 사용하십시오.

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv found in deployment folder: /tmp/dispatcher_validation_1625150390 - using files listed there
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until localhost is available
localhost resolves to ::1
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {

...

}
Syntax OK
Phase 2 finished
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt

...

no immutable file has been changed - check is SUCCESSFUL
Phase 3 finished
```

스크립트는 다음을 수행합니다.

1. 유효성 검사기를 실행합니다. 구성이 올바르지 않으면 스크립트가 실패합니다.
2. `httpd -t` 명령을 실행하여 구문이 올바른지 여부를 테스트하여 apache httpd를 시작할 수 있습니다. 성공하면 구성을 배포할 준비가 되어 있어야 합니다.
3. [파일 구조 섹션](##legacy-mode-file-structure)에 설명된 대로 변경할 수 없도록 만들어진 Dispatcher SDK 구성 파일의 하위 세트가 수정되지 않았는지 확인합니다. 이 확인은 AEM SDK 버전 v2021.1.4738에서 도입되었으며 Dispatcher 도구 버전 2.0.36도 포함되어 있습니다. 이 업데이트 전에 고객은 변경할 수 없는 파일의 로컬 SDK 수정 사항이 클라우드 환경에도 적용된다고 잘못 간주했을 수 있습니다.

Cloud Manager 배포 중에 `httpd -t` 구문 검사가 실행되며 모든 오류가 Cloud Manager `Build Images step failure` 로그에 포함됩니다.

### 1단계 {#first-phase}

지시어가 허용 목록에추가된이 아닌 경우 도구에서 오류를 기록하고 0이 아닌 종료 코드를 반환합니다. 또한 패턴 `conf.dispatcher.d/enabled_farms/*.farm`을 사용하여 모든 파일을 추가로 검색하고 다음을 확인합니다.

* `/glob`을 통해 허용되는 을 사용하는 필터 규칙이 없습니다([CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) 참조).
* 관리 기능이 노출되지 않습니다. 예를 들어 `/crx/de or /system/console` 과 같은 경로에 액세스합니다.

유효성 검사 도구는 허용 목록에추가된이 아닌 금지된 Apache 지시문의 사용만 보고합니다. 이 정보는 실행 중인 환경의 Apache 모듈만 사용할 수 있으므로 Apache 구성과 구문 또는 세미나적 문제를 보고하지 않습니다.

다음은 도구에서 출력하는 일반적인 유효성 검사 오류를 디버깅하는 문제 해결 기법입니다.

**보관 위치에서  `conf.dispatcher.d` 하위 폴더를 찾을 수 없습니다.**

보관 파일에는 `conf.d` 및 `conf.dispatcher.d` 폴더가 있어야 합니다. **이 아닌**을 사용해야 합니다
보관 위치에서 접두사 `etc/httpd`를 사용합니다.

**에서 팜을 찾을 수 없습니다.`conf.dispatcher.d/enabled_farms`**

사용 가능한 팜은 지정한 하위 폴더에 있어야 합니다.

**포함된 파일(...)의 이름은 다음과 같습니다. ...**

팜 구성에는 **에**이 포함되어야 하는 섹션이 두 개 있습니다
특정 파일: `/cache` 섹션의 `/renders` 및 `/allowedClients`. 그
섹션은 다음과 같이 표시되어야 합니다.

```
/renders {
    $include "../renders/default_renders.any"
}
```

및:

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**알 수 없는 위치에 포함된 파일: ...**

팜 구성에는 사용자의 파일을 포함할 수 있는 네 개의 섹션이 있습니다. `/cache` 섹션 및 `/virtualhosts`의 `/clientheaders`, `filters`, `/rules`. 포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 섹션 | 파일 이름 포함 |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

또는 이러한 파일의 **기본** 버전을 포함할 수 있습니다. 이러한 파일의 이름은 `default_` 앞에 추가됩니다. `../filters/default_filters.any`.

**알려진 위치 외부의 (...)에 문을 포함합니다. ...**

위의 단락에 언급된 6개 섹션과 별도로, 허용되지 않습니다
`$include` 문을 사용하려면, 예를 들어, 다음과 같이 이 오류가 생성됩니다.

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**허용된 클라이언트/렌더링은 다음 항목에 포함되지 않습니다. ...**

이 오류는 `/cache` 섹션에서 `/renders` 및 `/allowedClients`에 대한 include를 지정하지 않을 때 생성됩니다. 자세한 내용은
다음 이름을 지정해야 합니다. ...**섹션을 참조하십시오.**

**요청을 허용하려면 glob 패턴을 사용하지 않아야 합니다.**

전체 요청 라인에 대해 일치하는 `/glob` 스타일 규칙을 사용하는 요청을 허용한다는 것은 안전하지 않습니다(예: ).

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

이 문은 `css` 파일에 대한 요청을 허용하기 위한 것이지만, 쿼리 문자열 `?a=.css`이 뒤따르는 **any** 리소스에 대한 요청도 허용합니다. 따라서 이러한 필터를 사용할 수 없습니다(CVE-2016-0957 참조).

**포함된 파일(...)과 알려진 파일이 일치하지 않습니다.**

Apache 가상 호스트 구성에는 다음과 같이 지정할 수 있는 두 가지 유형의 파일이 있습니다. rewrites 및 variables.
포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 유형 | 파일 이름 포함 |
|-----------|---------------------------------|
| Rewrites | `conf.d/rewrites/rewrite.rules` |
| 변수 | `conf.d/variables/custom.vars` |

또는 이름이 `conf.d/rewrites/default_rewrite.rules`인 rewrite 규칙의 **기본** 버전을 포함할 수 있습니다.
변수 파일의 기본 버전은 없습니다.

**사용 중단된 구성 레이아웃이 검색되어 호환성 모드를 사용하도록 설정합니다.**

이 메시지는 구성에 완료된 를 포함하는 더 이상 사용되지 않는 버전 1 레이아웃이 있음을 나타냅니다
`ams_` 접두사가 있는 Apache 구성 및 파일입니다. 이 변수는 여전히 이전 버전에서 지원됩니다
호환성은 새 레이아웃으로 전환해야 합니다.

첫 번째 단계는 래퍼 `validate.sh` 스크립트가 아니라 별도로 **실행**&#x200B;될 수도 있습니다.

maven 아티팩트 또는 `dispatcher/src` 하위 디렉토리에 대해 실행하면 검증 실패를 보고합니다.

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Windows에서 디스패처 유효성 검사기는 대/소문자를 구분합니다. 이와 같이 구성이 있는 경로의 대소문자화를 준수하지 않는 경우 구성을 검증할 수 없습니다. 예를 들면 다음과 같습니다.

```
bin\validator.exe full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
  
```

Windows 탐색기에서 경로를 복사하여 붙여 넣은 다음 `cd` 명령을 사용하여 명령 프롬프트에서 해당 경로에 붙여 넣어 이 오류를 방지합니다.

### 2단계 {#second-phase}

이 단계에서는 이미지에서 Docker를 시작하여 Apache 구문을 확인합니다. Docker는 로컬에 설치해야 하지만 AEM을 실행할 필요는 없습니다.

>[!NOTE]
>Windows 사용자는 Windows 10 Professional이나 Docker를 지원하는 다른 배포를 사용해야 합니다. 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 전제 조건입니다.

이 단계는 다음 명령 `bin/docker_run.sh out host.internal.docker:4503 8080`에 필요한 출력 디렉토리를 생성하는 `validator full -d out src/dispatcher`을 통해 독립적으로 실행할 수도 있습니다.

Cloud Manager 배포 중에 `httpd -t` 구문 검사가 실행되고 모든 오류가 Cloud Manager 빌드 이미지 단계 실패 로그에 포함됩니다.

### 3단계 {#third-phase}

이 단계에 오류가 있는 경우 Adobe에서 하나 이상의 변경할 수 없는 파일을 변경했으며 해당 변경할 수 없는 파일을 SDK의 `src` 디렉토리에 제공된 새 버전으로 대체해야 한다는 의미입니다. 아래의 로그 샘플은 이 문제를 보여줍니다.

```
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt
(...)
checking existing 'conf.dispatcher.d/clientheaders/default_clientheaders.any' for changes
immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed:
--- /etc/httpd/conf.dispatcher.d/clientheaders/default_clientheaders.any
+++ /etc/httpd-actual/conf.dispatcher.d/clientheaders/default_clientheaders.any
@@ -40,4 +40,3 @@
"Sling-uploadmode"
"x-requested-with"
"If-Modified-Since"
-"Authorization"
** error: immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed!
  
```

이 단계는 다음 명령 `bin/docker_immutability_check.sh out`에 필요한 출력 디렉토리를 생성하는 `validator full -d out src/dispatcher`을 통해 독립적으로 실행할 수도 있습니다.

## Apache 및 Dispatcher 구성 디버깅 {#debugging-apache-and-dispatcher-configuration}

`./bin/docker_run.sh out docker.for.mac.localhost:4503 8080` 을 사용하여 Apache 디스패처를 로컬로 실행할 수 있습니다.

앞에서 설명한 바와 같이 Docker는 로컬에 설치해야 하며 AEM을 실행할 필요는 없습니다. Windows 사용자는 Windows 10 Professional이나 Docker를 지원하는 다른 배포를 사용해야 합니다. 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 전제 조건입니다.

다음 전략을 사용하여 Dispatcher 모듈에 대한 로그 출력을 높이고 로컬 및 클라우드 환경 모두에서 `RewriteRule` 평가 결과를 볼 수 있습니다.

이러한 모듈의 로그 수준은 변수 `DISP_LOG_LEVEL` 및 `REWRITE_LOG_LEVEL`에 의해 정의됩니다. `conf.d/variables/global.vars` 파일에서 설정할 수 있습니다. 관련 부분은 다음과 같습니다.

```
# Log level for the dispatcher
#
# Possible values are: Error, Warn, Info, Debug and Trace1
# Default value: Warn
#
# Define DISP_LOG_LEVEL Warn
 
# Log level for mod_rewrite
#
# Possible values are: Error, Warn, Info, Debug and Trace1 - Trace8
# Default value: Warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to Trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL Warn
```

Dispatcher를 로컬에서 실행할 때 로그가 터미널 출력에 직접 인쇄됩니다. 대부분의 경우 이러한 로그가 DEBUG에 있어야 하며 Docker를 실행할 때 디버그 수준을 매개 변수로 전달하여 수행할 수 있습니다. 예: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

클라우드 환경에 대한 로그는 Cloud Manager에서 사용할 수 있는 로깅 서비스를 통해 노출됩니다.

## 환경마다 다른 Dispatcher 구성 {#different-dispatcher-configurations-per-environment}

현재 동일한 Dispatcher 구성이 모든 AEM에 Cloud Service 환경으로 적용됩니다. 런타임에는 정의 및 현재 실행 모드(dev, stage 또는 prod)가 포함된 환경 변수 `ENVIRONMENT_TYPE`이 있습니다. 정의는 `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` 또는 `ENVIRONMENT_PROD`일 수 있습니다. Apache 구성에서 변수를 표현식에서 직접 사용할 수 있습니다. 또는 정의를 사용하여 논리를 작성할 수 있습니다.

```
# Simple usage of the environment variable
ServerName ${ENVIRONMENT_TYPE}.company.com
 
# When more logic is required
<IfDefine ENVIRONMENT_STAGE>
  # These statements are for stage
  Define VIRTUALHOST stage.example.com
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  # These statements are for production
  Define VIRTUALHOST prod.example.com
</IfDefine>
```

Dispatcher 구성에서는 동일한 환경 변수를 사용할 수 있습니다. 추가 논리가 필요한 경우 위의 예에 표시된 대로 변수를 정의한 다음 Dispatcher 구성 섹션에서 사용하십시오.

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

구성을 로컬로 테스트할 때 변수 `DISP_RUN_MODE`을 `docker_run.sh` 스크립트에 직접 전달하여 다른 환경 유형을 시뮬레이션할 수 있습니다.

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

DISP_RUN_MODE에 대한 값을 전달하지 않을 때 기본 실행 모드가 &quot;dev&quot;입니다.
사용 가능한 옵션 및 변수의 전체 목록을 보려면 인수 없이 `docker_run.sh` 스크립트를 실행하십시오.

## Docker 컨테이너에서 사용 중인 Dispatcher 구성 보기 {#viewing-dispatcher-configuration-in-use-by-docker-container}

환경별 구성을 사용하면 실제 Dispatcher 구성이 어떻게 표시되는지 확인하는 것이 어려울 수 있습니다. Docker 컨테이너를 `docker_run.sh` 시작한 후 다음과 같이 덤프할 수 있습니다.

* 사용 중인 Docker 컨테이너 ID를 확인합니다.

```
$ docker ps
CONTAINER ID       IMAGE
d75fbd23b29        adobe/aem-ethos/dispatcher-publish:...
```

* 해당 컨테이너 ID로 다음 명령줄을 실행합니다.

```
$ docker exec d75fbd23b29 httpd-test
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
  /publishfarm {
    /clientheaders {
...
```

## 기존 모드에서 유연한 모드로 마이그레이션 {#migrating-flexible}

Cloud Manager 2021.7.0 릴리스를 통해 새 Cloud Manager 프로그램은 AEM 원형 28 이상을 사용하여 maven 프로젝트 구조를 생성합니다. 이 구조에는 **옵트인/USE_SOURCES_DIRECT** 파일이 포함됩니다. 따라서 파일 수와 크기 주변에 이전 모드의 제한 사항이 제거되어 SDK 및 런타임에서 개선된 방식으로 구성을 확인하고 배포합니다. Dispatcher 구성에 이 파일이 없는 경우에는 마이그레이션하는 것이 좋습니다. [유연한 모드](/help/implementing/dispatcher/validation-debug.md#migrating) 페이지에 설명된 메서드를 사용합니다.
