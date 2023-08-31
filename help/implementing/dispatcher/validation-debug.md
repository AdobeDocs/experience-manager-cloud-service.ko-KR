---
title: Dispatcher 도구를 사용하여 확인 및 디버깅
description: 로컬 유효성 검사, 디버깅, 유연한 모드 파일 구조 및 레거시 모드에서 유연한 모드로 마이그레이션하는 방법에 대해 알아봅니다.
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
source-git-commit: fccce4fed057b9cf20825bce043b3ec95c3a5ab8
workflow-type: tm+mt
source-wordcount: '2988'
ht-degree: 1%

---

# Dispatcher 도구를 사용하여 확인 및 디버깅 {#Dispatcher-in-the-cloud}

## 소개 {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>클라우드의 Dispatcher 및 Dispatcher 도구를 다운로드하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [클라우드의 디스패처](/help/implementing/dispatcher/disp-overview.md) 페이지를 가리키도록 업데이트하는 중입니다. Dispatcher 구성이 레거시 모드인 경우 를 참조하십시오. [레거시 모드 설명서](/help/implementing/dispatcher/validation-debug-legacy.md).

다음 단원에서는 유연한 모드 파일 구조, 로컬 유효성 검사, 디버깅 및 레거시 모드에서 유연한 모드로 마이그레이션에 대해 설명합니다.

이 문서에서는 프로젝트의 Dispatcher 구성에 파일이 포함되어 있다고 가정합니다 `opt-in/USE_SOURCES_DIRECTLY`. 이 파일을 사용하면 SDK 및 런타임에서 기존 모드와 비교하여 개선된 방식으로 구성을 확인 및 배포하여 파일 수 및 크기에 대한 제한을 제거할 수 있습니다.

Dispatcher 구성에 앞에서 언급한 파일이 포함되어 있지 않은 경우 Adobe은 다음에 설명된 대로 레거시 모드에서 유연한 모드로 마이그레이션할 것을 권장합니다. [레거시 모드에서 유연한 모드로 마이그레이션](#migrating) 섹션.

## 파일 구조 {#flexible-mode-file-structure}

프로젝트의 Dispatcher 하위 폴더 구조는 다음과 같습니다.

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   ├── my_site.vhost # Created by customer
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── my_site.vhost -> ../available_vhosts/my_site.vhost  # Created by customer
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
│── opt-in
│   └── USE_SOURCES_DIRECTLY
└── conf.dispatcher.d
    ├── available_farms
    │   ├── my_farm.farm # Created by customer
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   ├── marketing_query_parameters.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── my_farm.farm -> ../available_farms/my_farm.farm  # Created by customer
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
    │   ├── default_virtualhosts.any
    │   └── virtualhosts.any
    
```

다음은 수정할 수 있는 주요 파일에 대한 설명입니다.

**사용자 정의 가능 파일**

다음 파일은 사용자 지정할 수 있으며 배포 시 클라우드 인스턴스로 전송됩니다.

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

이러한 파일이 한 개 이상 있을 수 있습니다. 다음 항목이 포함됩니다. `<VirtualHost>` 호스트 이름과 일치하고 Apache가 서로 다른 규칙으로 각 도메인 트래픽을 처리할 수 있도록 하는 항목입니다. 파일은에서 만들어집니다. `available_vhosts` 디렉토리 및 의 심볼 링크로 활성화됨 `enabled_vhosts` 디렉토리. 다음에서 `.vhost` 파일, 다른 파일(예: 재작성 및 변수)이 포함됩니다.

>[!NOTE]
>
>유연한 모드에서는 절대 경로 대신 상대 경로를 사용해야 합니다.

ServerAlias와 일치하는 가상 호스트를 항상 하나 이상 사용할 수 있는지 확인합니다. `\*.local`, `localhost`, 및 `127.0.0.1` Dispatcher 무효화에 필요합니다. 서버 별칭 `*.adobeaemcloud.net` 및 `*.adobeaemcloud.com` 하나 이상의 vhost 구성에도 필요하며 내부 Adobe 프로세스에 필요합니다.

여러 vhost 파일이 있으므로 정확한 호스트를 일치시키려면 아래 예를 따르십시오.

```
<VirtualHost *:80>
    ServerName    "example.com"
    # Put names of which domains are used for your published site/content here
    ServerAlias     "*example.com" "\*.local" "localhost" "127.0.0.1" "*.adobeaemcloud.net" "*.adobeaemcloud.com"
    # Use a document root that matches the one in conf.dispatcher.d/default.farm
    DocumentRoot "${DOCROOT}"
    # URI dereferencing algorithm is applied at Sling's level, do not decode parameters here
    AllowEncodedSlashes NoDecode
    # Add header breadcrumbs for help in troubleshooting which vhost file is chosen
    <IfModule mod_headers.c>
        Header add X-Vhost "publish-example-com"
    </IfModule>
  ...
</VirtualHost>
```

* `conf.d/enabled_vhosts/<CUSTOMER_CHOICE>.vhost`

이 폴더에는 conf.dispatcher.d/available_vhosts 아래의 파일에 대한 상대 심볼 링크가 포함되어 있습니다.

이러한 심볼 링크를 만드는 데 필요한 명령 예:

Apple® macOS, Linux 및 WSL

```
ln -s ../available_vhosts/wknd.vhost wknd.vhost
```

Microsoft® Windows

```
mklink wknd.vhost ..\available_vhosts\wknd.vhost
```

>[!NOTE]
>
> Windows에서 심볼 링크로 작업하는 경우 상위 명령 프롬프트나 Linux용 Windows 하위 시스템에서 를 실행하거나 [심볼 링크 만들기](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links) 권한이 할당되었습니다.

* `conf.d/rewrites/rewrite.rules`

파일은 의 내부에서 포함됩니다. `.vhost` 파일. 다음에 대한 재작성 규칙 세트가 있습니다. `mod_rewrite`.

* `conf.d/variables/custom.vars`

파일은 의 내부에서 포함됩니다. `.vhost` 파일. 이 위치에 Apache 변수에 대한 정의를 추가할 수 있습니다.

* `conf.d/variables/global.vars`

파일은 `dispatcher_vhost.conf` 파일. 이 파일에서 Dispatcher를 변경하고 로그 수준을 다시 쓸 수 있습니다.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

이러한 파일을 하나 이상 가질 수 있으며 호스트 이름과 일치하는 팜을 포함하고 Dispatcher 모듈이 다른 규칙으로 각 팜을 처리할 수 있도록 합니다. 파일은에서 만들어집니다. `available_farms` 디렉토리 및 의 심볼 링크로 활성화됨 `enabled_farms` 디렉토리. 다음에서 `.farm` 파일, 필터, 캐시 규칙 등과 같은 기타 파일이 포함됩니다.

* `conf.dispatcher.d/enabled_farms/<CUSTOMER_CHOICE>.farm`

이 폴더에는 conf.dispatcher.d/available_farms 아래의 파일에 대한 상대 심볼 링크가 포함되어 있습니다.

이러한 심볼 링크를 만드는 데 필요한 명령 예:

Apple® macOS, Linux 및 WSL

```
ln -s ../available_farms/wknd.farm wknd.farm
```

Microsoft® Windows

```
mklink wknd.farm ..\available_farms\wknd.farm
```

>[!NOTE]
>
> Windows에서 심볼 링크로 작업하는 경우 상위 명령 프롬프트나 Linux용 Windows 하위 시스템에서 를 실행하거나 [심볼 링크 만들기](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links) 권한이 할당되었습니다.

* `conf.dispatcher.d/cache/rules.any`

파일은 의 내부에서 포함됩니다. `.farm` 파일. 캐싱 기본 설정을 지정합니다.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

파일은 의 내부에서 포함됩니다. `.farm` 파일. 백엔드에 전달할 요청 헤더를 지정합니다.

* `conf.dispatcher.d/filters/filters.any`

파일은 의 내부에서 포함됩니다. `.farm` 파일. 필터링해야 하는 트래픽을 변경하고 백엔드로 전환하지 않는 규칙 세트가 있습니다.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

파일은 의 내부에서 포함됩니다. `.farm` 파일. glob 일치로 일치시킬 호스트 이름 또는 URI 경로 목록이 있습니다. 이 일치는 요청을 제공하는 데 사용할 백엔드를 결정합니다.

* `opt-in/USE_SOURCES_DIRECTLY`

이 파일은 보다 유연한 Dispatcher 구성을 가능하게 하며 파일의 수와 크기에 대한 이전 제한 사항을 제거합니다. 또한 SDK 및 런타임에서 개선된 방법으로 구성을 확인하고 배포하게 됩니다.

위의 파일은 아래 나열된 변경 불가능한 구성 파일을 참조합니다. 변경 불가능한 파일에 대한 변경 사항은 클라우드 환경의 Dispatcher에서 처리되지 않습니다.

**변경할 수 없는 구성 파일**

이러한 파일은 기본 프레임워크의 일부이며 표준 및 모범 사례를 적용합니다. 파일은 클라우드 인스턴스로 전송되지 않으므로 로컬에서 수정하거나 삭제해도 배포에 영향을 주지 않으므로 변경할 수 없는 것으로 간주됩니다.

위의 파일은 아래 나열된 변경 불가능한 파일을 참조한 후 추가 문 또는 무시를 수행하는 것이 좋습니다. Dispatcher 구성이 클라우드 환경에 배포되면 로컬 개발에 사용된 버전에 관계없이 변경할 수 없는 파일의 최신 버전이 사용됩니다.

* `conf.d/available_vhosts/default.vhost`

샘플 가상 호스트를 포함합니다. 가상 호스트의 경우 이 파일의 복사본을 만들고 사용자 지정하고 `conf.d/enabled_vhosts` 사용자 지정된 복사본에 대한 심볼 링크를 만듭니다.
default.vhost 파일을에 직접 복사하지 마십시오 `conf.d/enabled_vhosts`.

ServerAlias와 일치하는 가상 호스트를 항상 사용할 수 있는지 확인합니다. `\*.local`, `localhost`, 및 `127.0.0.1` Dispatcher 무효화에 필요합니다. 서버 별칭 `*.adobeaemcloud.net` 및 `*.adobeaemcloud.com` 내부 Adobe 프로세스에 필요합니다.

* `conf.d/dispatcher_vhost.conf`

가상 호스트 및 전역 변수가 포함된 방법을 보여 주는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.d/rewrites/default_rewrite.rules`

기본 규칙인 재작성 규칙은 표준 프로젝트에 적합합니다. 맞춤화가 필요한 경우 `rewrite.rules`. 사용자 지정에서 필요에 맞는 기본 규칙을 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/available_farms/default.farm`

샘플 Dispatcher 팜을 포함합니다. 사용자 팜의 경우 이 파일의 복사본을 만들고 사용자 지정하고 `conf.d/enabled_farms` 사용자 지정된 복사본에 대한 심볼 링크를 만듭니다.

* `conf.dispatcher.d/cache/default_invalidate.any`

시작 시 기본 프레임워크의 일부인 가 생성됩니다. 다음을 수행함: **필수** 사용자가 정의하는 모든 팜에 이 파일을 포함하려면 `cache/allowedClients` 섹션.

* `conf.dispatcher.d/cache/default_rules.any`

표준 프로젝트에 적합한 기본 캐시 규칙입니다. 맞춤화가 필요한 경우 `conf.dispatcher.d/cache/rules.any`. 사용자 지정에서 필요에 맞는 기본 규칙을 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

표준 프로젝트에 적합한 백엔드로 전달할 기본 요청 헤더입니다. 맞춤화가 필요한 경우 `clientheaders.any`. 사용자 지정에서 필요에 맞는 기본 요청 헤더를 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/dispatcher.any`

Dispatcher 팜이 포함된 방법을 보여 주는 기본 프레임워크의 일부입니다.

* `conf.dispatcher.d/filters/default_filters.any`

표준 프로젝트에 적합한 기본 필터. 맞춤화가 필요한 경우 `filters.any`. 사용자 지정에서 필요에 맞는 기본 필터를 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/renders/default_renders.any`

기본 프레임워크의 일부인 이 파일은 시작 시 생성됩니다. 다음을 수행함: **필수** 사용자가 정의하는 모든 팜에 이 파일을 포함하려면 `renders` 섹션.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

표준 프로젝트에 적합한 기본 호스트 글로빙. 맞춤화가 필요한 경우 `virtualhosts.any`. 일치하는 기본 호스트 글로빙을 사용자 지정에 포함시켜서는 안 됩니다 **매** 들어오는 요청입니다.

## 지원되는 Apache 모듈 {#apache-modules}

다음을 참조하십시오 [지원되는 Apache 모듈](/help/implementing/dispatcher/disp-overview.md#supported-directives).

## 로컬 유효성 검사 {#local-validation-flexible-mode}

>[!NOTE]
>
>아래 섹션에는 SDK의 Mac 또는 Linux® 버전을 사용하는 명령이 포함되어 있지만 Windows SDK도 유사한 방식으로 사용할 수 있습니다.

사용 `validate.sh` 아래와 같은 스크립트:

```
$ validate.sh src/dispatcher
opt-in USE_SOURCES_DIRECTLY marker file detected
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv not found in deployment folder: /Users/foo/src - using files in 'conf.d' and 'conf.dispatcher.d' subfolders directly
processing configuration subfolder: conf.d
processing configuration subfolder: conf.dispatcher.d
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

스크립트에는 다음 세 가지 단계가 있습니다.

1. 유효성 검사기를 실행합니다. 구성이 올바르지 않으면 스크립트가 실패합니다.
2. 다음을 실행합니다. `httpd -t` apache httpd가 시작될 수 있도록 구문이 올바른지 테스트하는 명령입니다. 성공하면 구성을 배포할 준비가 되어 있어야 합니다.
3. 에 설명된 대로 변경할 수 없도록 설계된 Dispatcher SDK 구성 파일의 하위 집합이 있는지 확인합니다. [파일 구조 섹션](##flexible-mode-file-structure)은(는) 수정되지 않았으며 현재 SDK 버전과 일치합니다.

Cloud Manager 배포 중 `httpd -t` 구문 검사도 실행되며 모든 오류가 Cloud Manager에 포함됩니다 `Build Images step failure` 로그합니다.

>[!NOTE]
>
다음을 참조하십시오. [자동 재로드 및 유효성 검사](#automatic-loading) 실행을 위한 효율적인 대안을 위한 섹션 `validate.sh` 각 구성 수정 후.

### 단계 1 {#first-phase}

지시문이 허용 목록에추가된이 아닌 경우 이 도구는 오류를 기록하고 0이 아닌 종료 코드를 반환합니다. 또한 패턴을 사용하여 모든 파일을 추가로 스캔합니다 `conf.dispatcher.d/enabled_farms/*.farm` 및 이(가) 다음을 확인합니다.

* 를 통해 허용을 사용하는 필터 규칙이 없습니다. `/glob` (참조 [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957))를 참조하십시오.
* 관리 기능이 노출되지 않았습니다. 예를 들어 다음과 같은 경로에 액세스할 수 있습니다 `/crx/de or /system/console`.

유효성 검사 도구는 허용 목록에추가된이 아닌 Apache 지시문의 금지된 사용만 보고합니다. 이 정보는 실행 중인 환경의 Apache 모듈에서만 사용할 수 있으므로 Apache 구성과 관련된 구문 또는 의미 체계 문제를 보고하지 않습니다.

다음은 도구에서 출력하는 일반적인 유효성 검사 오류를 디버깅하기 위한 문제 해결 기술입니다.

**을(를) 찾을 수 없음 `conf.dispatcher.d` 아카이브의 하위 폴더**

Your archive should contain folders `conf.d` and `conf.dispatcher.d`. Note, that you should **not**
use the prefix `etc/httpd` in your archive.

**에서 팜을 찾을 수 없음`conf.dispatcher.d/enabled_farms`**

활성화된 팜은 언급된 하위 폴더에 있어야 합니다.

**포함된 파일(...)의 이름은 다음과 같아야 합니다. ...**

팜 구성에는 다음과 같은 두 개의 섹션이 있습니다. **필수** 특정 파일 포함: `/renders` 및 `/allowedClients` 다음에서 `/cache` 섹션. 이러한 섹션은 다음과 같아야 합니다.

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

팜 구성에는 고유한 파일을 포함할 수 있는 네 가지 섹션이 있습니다. `/clientheaders`, `filters`, `/rules` 위치: `/cache` 섹션 및 `/virtualhosts`. 포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 섹션 | 파일 이름 포함 |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

또는 다음을 포함할 수 있습니다 **기본값** 파일 버전(이름 앞에 단어 포함) `default_`, 예: `../filters/default_filters.any`.

**알려진 위치 외부에 있는 (...)에 문을 포함합니다.**

위 단락에 언급된 6개의 섹션 외에는 다음을 사용할 수 없습니다. `$include` 명령문, 예를 들어 다음과 같은 경우 이 오류가 발생합니다.

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**허용된 클라이언트/렌더링은 다음에서 포함되지 않습니다. ...**

이 오류는에 대해 &quot;include&quot;를 지정하지 않을 때 생성됩니다 `/renders` 및 `/allowedClients` 다음에서 `/cache` 섹션. 다음을 참조하십시오.
**포함된 파일(...)의 이름은 다음과 같습니다. ...** 섹션에 자세히 설명되어 있습니다.

**필터는 glob 패턴을 사용하여 요청을 허용하지 않아야 함**

이 있는 요청을 허용하는 것은 안전하지 않습니다. `/glob` 스타일 규칙: 전체 요청 라인에 대해 일치합니다. 예:

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

이 문은 다음에 대한 요청을 허용하기 위한 것입니다. `css` 파일을 다운로드할 수 있지만 **임의** 쿼리 문자열이 뒤따르는 리소스 `?a=.css`. 따라서 이러한 필터는 사용할 수 없습니다(CVE-2016-0957 참조).

**포함된 파일(...)이 알려진 파일과 일치하지 않음**

기본적으로 Apache 가상 호스트 구성에 있는 두 가지 유형의 파일은 rewrite와 variables를 포함하여 지정할 수 있습니다.

| 유형 | 파일 이름 포함 |
|-----------|---------------------------------|
| 재작성 | `conf.d/rewrites/rewrite.rules` |
| 변수 | `conf.d/variables/custom.vars` |

유연한 모드에서는 의 하위 디렉터리(어떤 수준이든)에 있는 한 다른 파일도 포함할 수 있습니다. `conf.d` 디렉토리가 다음과 같이 접두사로 추가되었습니다.

| 파일 상위 디렉터리 접두사 포함 |
|-------------------------------------|
| `conf.d/includes` |
| `conf.d/modsec` |
| `conf.d/rewrites` |

예를 들어 아래 새로 만든 디렉토리에 파일을 포함할 수 있습니다. `conf.d/includes` 디렉터리는 다음과 같습니다.

```
Include conf.d/includes/mynewdirectory/myincludefile.conf
```

또는 다음을 포함할 수 있습니다 **기본값** 이름이 인 규칙 다시 작성 버전 `conf.d/rewrites/default_rewrite.rules`.
변수 파일의 기본 버전은 없습니다.

**사용 중단된 구성 레이아웃이 감지되어 호환성 모드가 활성화됩니다.**

이 메시지는 구성에 사용되지 않는 버전 1 레이아웃이 포함되어 있으며, 전체 Apache 구성 및 파일이 포함되어 있음을 나타냅니다. `ams_` 접두사. 이 구성은 이전 버전과의 호환성을 위해 계속 지원되지만 새 레이아웃으로 전환해야 합니다.

첫 번째 단계는 **개별적으로 실행**, 래퍼에서 보다는 `validate.sh` 스크립트.

Maven 아티팩트 또는 `dispatcher/src` 하위 디렉토리이며 유효성 검사 실패를 보고합니다.

```
$ validator full -relaxed dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Windows에서 Dispatcher 유효성 검사기는 대/소문자를 구분합니다. 따라서 구성이 있는 경로의 대소문자를 고려하지 않으면 구성의 유효성을 검사하지 못할 수 있습니다. 예를 들면 다음과 같습니다.

```
bin\validator.exe -relaxed full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
```

Windows 탐색기에서 경로를 복사하여 붙여넣은 다음 명령 프롬프트에서 `cd` 명령입니다.

### 단계 2 {#second-phase}

이 단계에서는 도커 컨테이너에서 Apache HTTPD를 시작하여 Apache 구문을 확인합니다. Docker를 로컬에 설치해야 하지만 AEM을 실행할 필요는 없습니다.

>[!NOTE]
>
Windows 사용자는 Windows 10 Professional 또는 Docker를 지원하는 기타 배포를 사용해야 합니다. 이 요구 사항은 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 전제 조건입니다.
Windows와 macOS Adobe 모두에서 Docker Desktop을 사용하는 것이 좋습니다.

이 단계는 `bin/docker_run.sh src/dispatcher host.docker.internal:4503 8080`.

Cloud Manager 배포 중 `httpd -t` 구문 검사도 실행되며 모든 오류는 Cloud Manager 빌드 이미지 단계 오류 로그에 포함됩니다.

### 단계 3 {#third-phase}

이 단계에서 오류가 발생하면 Adobe에서 변경할 수 없는 파일을 하나 이상 변경했음을 의미합니다. 이 경우 변경할 수 없는 해당 파일을 의 새 버전으로 바꿔야 합니다 `src` sdk의 디렉터리입니다. 아래의 로그 샘플은 이 문제를 보여 줍니다.

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

이 단계는 `bin/docker_immutability_check.sh src/dispatcher`.

로컬 변경 불가능한 파일은 `bin/update_maven.sh src/dispatcher` Dispatcher 폴더의 스크립트. 여기서 `src/dispatcher` 는 Dispatcher 구성 디렉터리입니다. 이 스크립트는 또한 다음을 업데이트합니다. `pom.xml` maven 불변 검사도 업데이트되도록 상위 디렉터리에 있는 파일입니다.

## Apache 및 Dispatcher 구성 디버깅 {#debugging-apache-and-dispatcher-configuration}

를 사용하여 로컬에서 Apache Dispatcher를 실행할 수 있습니다. `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080`.

앞에서 설명한 대로 Docker를 로컬에 설치해야 하며, AEM을 실행할 필요는 없습니다. Windows 사용자는 Windows 10 Professional 또는 Docker를 지원하는 기타 배포를 사용해야 합니다. 이 요구 사항은 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 전제 조건입니다.

다음 전략을 사용하여 Dispatcher 모듈에 대한 로그 출력을 높이고 의 결과를 볼 수 있습니다. `RewriteRule` 로컬 및 클라우드 환경 모두에서 평가.

이러한 모듈에 대한 로그 수준은 변수에 의해 정의됩니다 `DISP_LOG_LEVEL` 및 `REWRITE_LOG_LEVEL`. 파일에서 설정할 수 있습니다 `conf.d/variables/global.vars`. 관련 부분은 다음과 같습니다.

```
# Log level for the dispatcher
#
# Possible values are: error, warn, info, debug and trace1
# Default value: warn
#
# Define DISP_LOG_LEVEL warn
 
# Log level for mod_rewrite
#
# Possible values are: error, warn, info, debug and trace1 - trace8
# Default value: warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL warn
```

로컬에서 Dispatcher를 실행하는 경우 로그가 터미널 출력에 직접 인쇄됩니다. 대부분의 경우 이러한 로그를 DEBUG로 만들어야 합니다. 이 작업은 도커를 실행할 때 디버그 수준을 매개 변수로 전달하여 수행할 수 있습니다. 예: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080`.

클라우드 환경의 로그는 Cloud Manager에서 사용할 수 있는 로깅 서비스를 통해 노출됩니다.

>[!NOTE]
>
AEM as a Cloud Service 환경의 경우 debug가 최대 세부 정보 수준입니다. 추적 로그 수준은 지원되지 않으므로 클라우드 환경에서 작업할 때 이 수준을 설정하지 않아야 합니다.

### 자동 재로드 및 유효성 검사 {#automatic-reloading}

>[!NOTE]
>
Windows 운영 체제의 제한으로 인해 이 기능은 macOS 및 Linux® 사용자만 사용할 수 있습니다.

로컬 유효성 검사를 실행하는 대신(`validate.sh`) 및 docker 컨테이너 시작(`docker_run.sh`) 구성을 수정할 때마다 `docker_run_hot_reload.sh` 스크립트. 스크립트는 구성 변경 사항을 감시하고 자동으로 다시 로드한 다음 유효성 검사를 다시 실행합니다. 이 옵션을 사용하면 디버깅할 때 상당한 시간을 절약할 수 있습니다.

다음 명령을 사용하여 스크립트를 실행할 수 있습니다. `./bin/docker_run_hot_reload.sh src/dispatcher host.docker.internal:4503 8080`

출력의 첫 번째 행은 다음에 대해 실행되는 것과 유사합니다. `docker_run.sh`. 예:

```
~ bin/docker_run_hot_reload.sh src host.docker.internal:8081 8082
opt-in USE_SOURCES_DIRECTLY marker file detected
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/15-check-pod-name.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until host.docker.internal is available
host.docker.internal resolves to 192.168.65.2
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
Running script /docker_entrypoint.d/80-frontend-domain.sh
Running script /docker_entrypoint.d/zzz-import-sdk-config.sh
WARN Mon Jul  4 09:53:54 UTC 2022: Pseudo symlink conf.d seems to point to a non-existing file!
INFO Mon Jul  4 09:53:55 UTC 2022: Copied customer configuration to /etc/httpd.
INFO Mon Jul  4 09:53:55 UTC 2022: Start testing
Cloud manager validator 2.0.43
2022/07/04 09:53:55 No issues found
INFO Mon Jul  4 09:53:55 UTC 2022: Testing with fresh base configuration files.
INFO Mon Jul  4 09:53:55 UTC 2022: Apache httpd informationServer version: Apache/2.4.54 (Unix)
```

## 환경당 다른 Dispatcher 구성 {#different-dispatcher-configurations-per-environment}

현재 동일한 Dispatcher 구성이 AEM의 모든 환경에 as a Cloud Service으로 적용됩니다. 런타임에 환경 변수가 있습니다. `ENVIRONMENT_TYPE` 현재 실행 모드(개발, 스테이지 또는 프로덕션)와 &quot;정의&quot;를 포함합니다. &quot;정의&quot;는 `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE`, 또는 `ENVIRONMENT_PROD`. Apache 구성에서 변수는 표현식에서 직접 사용할 수 있습니다. 또는 &quot;define&quot;을 사용하여 논리를 작성할 수 있습니다.

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

Dispatcher 구성에서 동일한 환경 변수를 사용할 수 있습니다. 더 많은 논리가 필요한 경우 위의 예제와 같이 변수를 정의한 다음 Dispatcher 구성 섹션에서 사용합니다.

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

또는 환경 비밀은 아니지만 httpd/dispatcher 구성에서 Cloud Manager 환경 변수를 사용할 수 있습니다. 프로그램에 여러 개발 환경이 있고 이러한 개발 환경 중 일부에 httpd/dispatcher 구성에 대한 값이 다른 경우 이 방법이 특히 중요합니다. 동일한 ${VIRTUALHOST} 구문은 위의 예제와 같이 사용되지만 위의 변수 파일에서 Define 선언은 사용되지 않습니다. 읽기 [Cloud Manager 설명서](/help/implementing/cloud-manager/environment-variables.md) Cloud Manager 환경 변수 구성에 대한 지침.

구성을 로컬에서 테스트할 때 변수를 전달하여 다양한 환경 유형을 시뮬레이션할 수 있습니다 `DISP_RUN_MODE` (으)로 `docker_run.sh` 직접 스크립트:

```
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
```

DISP_RUN_MODE에 대한 값을 전달하지 않을 때의 기본 실행 모드는 &quot;dev&quot;입니다.
사용 가능한 옵션 및 변수의 전체 목록을 보려면 스크립트를 실행합니다 `docker_run.sh` 인수 없이.

## 도커 컨테이너에서 사용 중인 Dispatcher 구성 보기 {#viewing-dispatcher-configuration-in-use-by-docker-container}

환경별 구성에서는 실제 Dispatcher 구성이 어떻게 표시되는지 파악하기 어려울 수 있습니다. 를 사용하여 도커 컨테이너를 시작한 후 `docker_run.sh`, 다음과 같이 덤프할 수 있습니다.

* 사용 중인 도커 컨테이너 ID 확인:

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

## 레거시 모드에서 유연한 모드로 마이그레이션 {#migrating}

Cloud Manager 2021.7.0 릴리스를 통해 새로운 Cloud Manager 프로그램은 [AEM Archetype 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ko-KR) 또는 그 이상(파일을 포함) **opt-in/USE_SOURCES_DIRECTLY**. 의 이전 제한 사항을 제거합니다. [레거시 모드](/help/implementing/dispatcher/validation-debug-legacy.md) 또한 SDK 및 런타임에서 개선된 방법으로 구성을 확인하고 배포하는 문제가 발생할 수 있습니다. Dispatcher 구성에 이 파일이 없는 경우 마이그레이션하는 것이 좋습니다. 안전한 전환을 보장하려면 다음 단계를 따르십시오.

1. **로컬 테스트.** 최신 Dispatcher 도구 SDK를 사용하여 폴더 및 파일을 추가합니다 `opt-in/USE_SOURCES_DIRECTLY`. Dispatcher가 로컬에서 작동하는지 테스트할 수 있도록 이 문서의 &quot;로컬 유효성 검사&quot; 지침을 따르십시오.
1. **클라우드 개발 테스트:**
   * 파일 커밋 `opt-in/USE_SOURCES_DIRECTLY` 비프로덕션 파이프라인에서 클라우드 개발 환경으로 배포되는 git 분기에
   * Cloud Manager를 사용하여 클라우드 개발 환경에 배포합니다.
   * 철저히 테스트해 보십시오. 상위 환경에 변경 사항을 배포하기 전에 Apache 및 Dispatcher 구성이 예상대로 작동하는지 확인하는 것이 중요합니다. 사용자 지정 구성과 관련된 모든 동작을 확인합니다. 배포된 Dispatcher 구성이 사용자 지정 구성을 반영하지 않는다고 판단되는 경우 고객 지원 티켓을 제출합니다.

   >[!NOTE]
   >
   유연한 모드에서는 절대 경로 대신 상대 경로를 사용해야 합니다.
1. **프로덕션에 배포:**
   * 파일 커밋 `opt-in/USE_SOURCES_DIRECTLY` 프로덕션 파이프라인에서 클라우드 스테이지 및 프로덕션 환경에 배포되는 git 분기에
   * Cloud Manager를 사용하여 스테이징에 배포합니다.
   * 철저히 테스트해 보십시오. 상위 환경에 변경 사항을 배포하기 전에 Apache 및 Dispatcher 구성이 예상대로 작동하는지 확인하는 것이 중요합니다. 사용자 지정 구성과 관련된 모든 동작을 확인합니다. 배포된 Dispatcher 구성이 사용자 지정 구성을 반영하지 않는다고 판단되는 경우 고객 지원 티켓을 제출합니다.
   * Cloud Manager를 사용하여 프로덕션에 배포를 계속합니다.
