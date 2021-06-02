---
title: 클라우드의 디스패처
description: '클라우드의 디스패처 '
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
source-git-commit: 6eb200fe661873374258a5953a07b38b2251da43
workflow-type: tm+mt
source-wordcount: '4233'
ht-degree: 5%

---

# 클라우드의 디스패처 {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="클라우드의 디스패처"
>abstract="이 섹션에서는 AEM을 Cloud Service Apache 및 Dispatcher 구성으로 구성하는 방법과 클라우드 환경에 배포하기 전에 로컬로 확인하고 실행하는 방법에 대해 설명합니다. 클라우드 환경에서의 디버깅에도 대해 설명합니다."

## Apache 및 Dispatcher 구성과 테스트 {#apache-and-dispatcher-configuration-and-testing}

이 섹션에서는 AEM을 Cloud Service Apache 및 Dispatcher 구성으로 구성하는 방법과 클라우드 환경에 배포하기 전에 로컬로 확인하고 실행하는 방법에 대해 설명합니다. 클라우드 환경에서의 디버깅에도 대해 설명합니다. Dispatcher에 대한 자세한 내용은 [AEM Dispatcher 설명서](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=ko-KR)를 참조하십시오.

>[!NOTE]
>Windows 사용자는 Windows 10 Professional이나 Docker를 지원하는 다른 배포를 사용해야 합니다. 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 전제 조건입니다. 아래 섹션에는 SDK의 Mac 또는 Linux 버전을 사용하는 명령이 포함되어 있지만 Windows SDK는 유사한 방식으로 사용할 수 있습니다.

## Dispatcher 도구 {#dispatcher-sdk}

Dispatcher 도구는 전체 AEM as a Cloud Service SDK에 포함되어 있으며 다음을 제공합니다.

* Dispatcher용 maven 프로젝트에 포함할 구성 파일이 포함된 vanilla 파일 구조입니다.
* 고객이 Dispatcher 구성에 Cloud Service 지원 지시어로 AEM만 포함되는지 확인할 수 있도록 툴을 제공합니다.        또한 도구에서 구문이 올바른지 확인하여 apache가 성공적으로 시작될 수 있습니다.
* 로컬에서 Dispatcher를 표시하는 Docker 이미지입니다.

## 도구 {#extracting-the-sdk} 다운로드 및 추출

[AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)에 포함된 Dispatcher 도구는 [소프트웨어 배포](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) 포털의 zip 파일에서 다운로드할 수 있습니다. 이 새 Dispatcher 도구 버전에서 사용할 수 있는 모든 새 구성은 클라우드 이상에서 해당 AEM 버전을 실행하는 클라우드 환경에 배포하는 데 사용할 수 있습니다.

macOS/Linux 및 Windows용 Dispatcher 도구를 번들로 제공하는 SDK의 압축을 해제합니다.

**macOS/Linux**&#x200B;의 경우 Dispatcher 도구를 실행 가능으로 만들고 실행합니다. 저장한 디렉토리 아래에 Dispatcher 도구 파일을 자동으로 추출합니다(여기서 `version`은 Dispatcher 도구의 버전입니다.).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Windows**&#x200B;의 경우 Dispatcher 도구 zip 아카이브를 추출합니다.

## 파일 구조 {#file-structure}

프로젝트의 Dispatcher 하위 폴더의 구조는 아래에 설명되어 있으며 maven 프로젝트 Dispatcher 폴더에 복사되어야 합니다.

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

이 파일은 `.vhost` 파일 내부에서 포함됩니다. 이 위치에 Apache 변수에 대한 정의를 지정할 수 있습니다.

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

>[!NOTE]
>
>AEM as a Cloud Service maven 원형 은 동일한 Dispatcher 구성 파일 구조를 생성합니다.

아래 섹션에서는 내부 릴리스를 배포할 때 Cloud Manager에서 관련 품질 게이트를 전달할 수 있도록 구성을 로컬로 확인하는 방법을 설명합니다.

## Dispatcher 구성에서 지원되는 디렉티브의 로컬 유효성 검사 {#local-validation-of-dispatcher-configuration}

유효성 검사 도구는 SDK에서 `bin/validator` as a Mac OS, Linux 또는 Windows 바이너리로 사용할 수 있으므로 고객은 릴리스를 빌드하고 배포하는 동안 Cloud Manager에서 수행할 것과 동일한 유효성 검사를 실행할 수 있습니다.

이 호출은 다음과 같이 호출됩니다.`validator full [-d folder] [-w allowlist] zip-file | src folder`

이 도구는 Dispatcher 구성이 `conf.d/enabled_vhosts/*.vhost` 패턴으로 모든 파일을 스캔하여 AEM as a Cloud Service에서 지원하는 적절한 지시어를 사용하고 있는지 확인합니다.

Windows에서 디스패처 유효성 검사기는 대/소문자를 구분합니다. 이와 같이 구성이 있는 경로의 대소문자화를 준수하지 않는 경우 구성을 검증할 수 없습니다. 예를 들면 다음과 같습니다.

```
bin\validator.exe full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
  
```

Windows 탐색기에서 경로를 복사하여 붙여 넣은 다음 `cd` 명령을 사용하여 명령 프롬프트에서 해당 경로에 붙여 넣어 이 오류를 방지합니다.

유효성 검사기의 허용 목록에 추가하다 명령을 실행하여 Apache 구성 파일에서 허용되는 지시문을 나열할 수 있습니다.

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

아래 표에는 지원되는 Apache 모듈이 나와 있습니다.

| 모듈 이름 | 참조 페이지 |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_proxy` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html) |
| `mod_proxy_http` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

고객은 임의의 모듈을 추가할 수 없지만, 향후 제품에 포함하기 위해 추가 모듈을 고려할 수 있습니다. 고객은 위에 설명된 대로 SDK에서 유효성 검사기의 명령허용 목록에 추가하다를 실행하여 주어진 Dispatcher 버전에 사용할 수 있는 지시어 목록을 찾을 수 있습니다.

이허용 목록에 추가하다는 고객 구성에서 허용되는 Apache 지시문 목록을 포함합니다. 지시어가 허용 목록에추가된이 아닌 경우 도구에서 오류를 기록하고 0이 아닌 종료 코드를 반환합니다. 명령줄허용 목록에 추가하다에가 제공되지 않는 경우(이 옵션이 호출되어야 하는 방식), 이 도구는 Cloud Manager가 클라우드 환경에 배포하기 전에 유효성 검사에 사용할 기본 허용 목록에 추가하다를 사용합니다.

또한 패턴 `conf.dispatcher.d/enabled_farms/*.farm`을 사용하여 모든 파일을 추가로 검색하고 다음을 확인합니다.

* `/glob`을 통해 허용되는 을 사용하는 필터 규칙이 없습니다([CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) 참조)
* 관리 기능이 노출되지 않습니다. 예를 들어 `/crx/de or /system/console` 과 같은 경로에 액세스합니다.

maven 아티팩트 또는 `dispatcher/src` 하위 디렉토리에 대해 실행하면 검증 실패를 보고합니다.

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

유효성 검사 도구는 허용 목록에추가된이 아닌 금지된 Apache 지시문의 사용만 보고합니다. 이 정보는 실행 중인 환경의 Apache 모듈만 사용할 수 있으므로 Apache 구성과 구문 또는 세미나적 문제를 보고하지 않습니다.

다음은 도구에서 출력하는 일반적인 유효성 검사 오류를 디버깅하는 문제 해결 기법입니다.

**보관 위치에서  `conf.dispatcher.d` 하위 폴더를 찾을 수 없습니다.**

보관 파일에는 `conf.d` 및 `conf.dispatcher.d` 폴더가 있어야 합니다. **이 아닌**을 사용해야 합니다
보관 위치에서 접두사 `etc/httpd`를 사용합니다.

**에서 팜을 찾을 수 없습니다.`conf.dispatcher.d/enabled_farms`**

사용 가능한 팜은 지정한 하위 폴더에 있어야 합니다.

**포함된 파일(...)의 이름은 다음과 같습니다....**

팜 구성에는 **에**이 포함되어야 하는 섹션이 두 개 있습니다
특정 파일:`/cache` 섹션의 `/renders` 및 `/allowedClients`. 그
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

**알 수 없는 위치에 포함된 파일:...**

팜 구성에는 사용자의 파일을 포함할 수 있는 네 개의 섹션이 있습니다.`/cache` 섹션 및 `/virtualhosts`의 `/clientheaders`, `filters`, `/rules`. 포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 섹션 | 파일 이름 포함 |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

또는 이러한 파일의 **기본** 버전을 포함할 수 있습니다. 이러한 파일의 이름은 `default_` 앞에 추가됩니다.`../filters/default_filters.any`.

**알려진 위치 외부의 (...)에 문을 포함합니다....**

위의 단락에 언급된 6개 섹션과 별도로, 허용되지 않습니다
`$include` 문을 사용하려면, 예를 들어, 다음과 같이 이 오류가 생성됩니다.

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**허용된 클라이언트/렌더링은 다음 항목에 포함되지 않습니다....**

이 오류는 `/cache` 섹션에서 `/renders` 및 `/allowedClients`에 대한 include를 지정하지 않을 때 생성됩니다. 자세한 내용은
다음 이름을 지정해야 합니다....**섹션을 참조하십시오.**

**요청을 허용하려면 glob 패턴을 사용하지 않아야 합니다.**

전체 요청 라인에 대해 일치하는 `/glob` 스타일 규칙을 사용하는 요청을 허용한다는 것은 안전하지 않습니다(예: ).

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

이 문은 `css` 파일에 대한 요청을 허용하기 위한 것이지만, 쿼리 문자열 `?a=.css`이 뒤따르는 **any** 리소스에 대한 요청도 허용합니다. 따라서 이러한 필터를 사용할 수 없습니다(CVE-2016-0957 참조).

**포함된 파일(...)과 알려진 파일이 일치하지 않습니다.**

Apache 가상 호스트 구성에는 다음과 같이 지정할 수 있는 두 가지 유형의 파일이 있습니다.rewrites 및 variables.
포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 유형 | 파일 이름 포함 |
|-----------|---------------------------------|
| Rewrites | `conf.d/rewrites/rewrite.rules` |
| 변수 | `conf.d/variables/custom.vars` |

또는 이름이 `conf.d/rewrites/default_rewrite.rules`인 rewrite 규칙의 **기본** 버전을 포함할 수 있습니다.
변수 파일의 기본 버전은 없습니다.

**사용 중단된 구성 레이아웃이 검색되어 호환성 모드를 사용하도록 설정합니다.**

이 메시지는 구성에 완료된 를 포함하는 더 이상 사용되지 않는 버전 1 레이아웃이 있음을 나타냅니다
`ams_` 접두사가 있는 Apache 구성 및 파일입니다. 이 기능은 여전히 이전 버전에서 지원됩니다
호환성은 새 레이아웃으로 전환해야 합니다.

## Apache httpd가 {#local-validation}을 시작할 수 있도록 Dispatcher 구성 구문의 로컬 유효성 검사

Dispatcher 모듈 구성에 지원되는 지시문만 포함되도록 설정되면 Apache를 시작할 수 있도록 구문이 올바른지 확인해야 합니다. 이를 테스트하려면 Docker가 로컬에 설치되어 있어야 합니다. AEM을 실행할 필요는 없습니다.

아래 표시된 대로 `validate.sh` 스크립트를 사용하십시오.

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
2019/06/19 16:02:55 No issues found
Phase 1 finished
Phase 2: httpd -t validation in docker image
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
...
}
Syntax OK
Phase 2 finished
```

스크립트는 다음을 수행합니다.

1. 이전 섹션의 유효성 검사기를 실행하여 지원되는 지시문만 포함되도록 합니다. 구성이 올바르지 않으면 스크립트가 실패합니다.
2. 이 코드는 `httpd -t command`을 실행하여 Apache httpd가 시작될 수 있도록 구문이 올바른지 테스트합니다. 성공하면 구성을 배포할 준비가 되어 있어야 합니다.
3. [파일 구조 섹션](#file-structure)에 설명된 대로 변경할 수 없도록 만들어진 Dispatcher SDK 구성 파일의 하위 세트가 수정되지 않았는지 확인합니다. 이 확인은 AEM SDK 버전 v2021.1.4738에서 도입되었으며 Dispatcher 도구 버전 2.0.36도 포함되어 있습니다. 이 업데이트 전에 고객은 변경할 수 없는 파일의 로컬 SDK 수정 사항이 클라우드 환경에도 적용된다고 잘못 간주했을 수 있습니다.

Cloud Manager 배포 중에 `httpd -t syntax` 확인도 실행되며, 모든 오류가 Cloud Manager `Build Images step failure` 로그에 포함됩니다.

## 로컬로 Apache 및 Dispatcher 구성을 테스트합니다 {#testing-apache-and-dispatcher-configuration-locally}.

또한 로컬로 Apache 및 Dispatcher 구성을 테스트할 수도 있습니다. 위에서 설명한 유효성 검사를 전달하려면 Docker를 로컬로 설치하고 구성이 필요합니다.

모든 Dispatcher 구성 파일과 함께 폴더를 출력하는 `-d` 매개 변수를 사용하여 유효성 검사기 도구를 실행합니다(앞에서 언급한 `validator.sh`과 다릅니다). 그런 다음 `docker_run.sh` 스크립트를 실행하여 해당 폴더를 인수로 전달합니다. 포트 번호를 제공하여8080)로 Dispatcher 종단점을 노출하기 위해 Docker 컨테이너가 시작되고 구성으로 Dispatcher가 실행됩니다.

```
$ validator full -d out src/dispatcher
2019/06/19 16:02:55 No issues found
$ docker_run.sh out docker.for.mac.localhost:4503 8080
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
Starting httpd server
...
```

이렇게 하면 포트 4503에서 로컬 Mac OS 시스템에서 실행되는 AEM 인스턴스를 가리키는 백엔드가 있는 컨테이너에서 Dispatcher가 시작됩니다.

## Apache 및 Dispatcher 구성 디버깅 {#debugging-apache-and-dispatcher-configuration}

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

## 환경당 다른 Dispatcher 구성 {#different-dispatcher-configurations-per-environment}

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

## Docker 컨테이너에 의해 사용 중인 Dispatcher 구성 보기 {#viewing-dispatcher-configuration-in-use-by-docker-container}

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

## AMS Dispatcher와 AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service} 간의 주요 차이점

위의 참조 페이지에 설명된 대로 AEM as a Cloud Service의 Apache 및 Dispatcher 구성은 AMS 구성과 매우 유사합니다. 주요 차이점은 다음과 같습니다.

* AEM as a Cloud Service에서 일부 Apache 지시문은 사용할 수 없습니다(예: `Listen` 또는 `LogLevel`)
* AEM as a Cloud Service에서 일부 Dispatcher 구성만 포함 파일에 넣을 수 있으며 해당 이름이 중요합니다. 예를 들어 다른 호스트에서 다시 사용할 필터 규칙은 `filters/filters.any` 파일에 넣어야 합니다. 자세한 내용은 참조 페이지 를 참조하십시오.
* AEM as a Cloud Service에는 보안 문제를 방지하기 위해 `/glob`을 사용하여 작성된 필터 규칙을 허용하지 않는 추가 유효성 검사가 있습니다. `deny *`은 `allow *` 대신 사용되므로(사용할 수 없음), 고객은 Dispatcher를 로컬에서 실행하고 시험판 및 오류를 수행하여 이 작업을 추가할 수 있도록 Dispatcher 필터가 차단 중인 경로를 정확하게 파악할 수 있는 이점을 누릴 수 있습니다.

## AMS에서 AEM as a Cloud Service으로 Dispatcher 구성을 마이그레이션하는 지침

Dispatcher 구성 구조는 Managed Services과 AEM as a Cloud Service 간에 차이가 있습니다. 아래에 나와 있는 는 AMS Dispatcher 구성 버전 2에서 AEM으로 Cloud Service으로 마이그레이션하는 방법에 대한 단계별 안내서입니다.

## AMS를 AEM as a Cloud Service Dispatcher 구성으로 변환하는 방법

다음 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다. 이 경우
[Cloud Manager Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)에 설명된 것과 유사한 구조를 갖는 보관 파일이 있어야 합니다.

### 아카이브 추출 및 최종 접두사 제거

아카이브를 폴더에 추출하고, 바로 아래 하위 폴더가 `conf`, `conf.d`,
`conf.dispatcher.d` 및 `conf.modules.d`. 그렇지 않으면 계층 구조에서 위로 이동합니다.

### 사용하지 않는 하위 폴더와 파일 제거

하위 폴더 `conf` 및 `conf.modules.d` 와 `conf.d/*.conf`와 일치하는 파일을 제거합니다.

### 게시되지 않은 모든 가상 호스트 제거

`author`, `unhealthy`, `health`,
이름에 `lc` 또는 `flush`. `conf.d/enabled_vhosts` `conf.d/available_vhosts`에 없는 모든 가상 호스트 파일
에 연결된 도 제거할 수 있습니다.

### 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 달기

가상 호스트 파일에 포트 80 이외의 다른 포트만 참조하는 섹션이 있는 경우

```
<VirtualHost *:443>
...
</VirtualHost>
```

해당 섹션을 제거하거나 주석을 답니다. 이러한 섹션의 문은 처리되지 않지만, 이 문을 계속 유지하면 아무것도 적용되지 않은 상태로 편집을 종료할 수 있으므로 혼동을 줄 수 있습니다.

### rewrites 확인

`conf.d/rewrites` 디렉토리를 입력합니다.

`base_rewrite.rules` 및 `xforwarded_forcessl_rewrite.rules` 파일을 제거하고 다음 작업을 수행해야 합니다.
가상 호스트 파일에서 이를 참조하는 `Include` 문을 제거합니다.

이제 `conf.d/rewrites`에 단일 파일이 포함되어 있는 경우 이름을 `rewrite.rules`로 변경하고 그렇지 않은 경우
가상 호스트 파일에서도 해당 파일을 참조하는 `Include` 문을 수정해야 합니다.

그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 컨텐츠는 다음과 같습니다
가상 호스트 파일에서 이를 참조하는 `Include` 문에 복사됩니다.

### 변수 확인

`conf.d/variables` 디렉토리를 입력합니다.

`ams_default.vars` 파일을 제거하고 가상 파일에서 `Include` 문을 제거해야 합니다
이들을 참조하는 호스트 파일입니다.

이제 `conf.d/variables`에 단일 파일이 포함되어 있는 경우 이름을 `custom.vars`로 변경하고 그렇지 않은 경우
가상 호스트 파일에서도 해당 파일을 참조하는 `Include` 문을 수정해야 합니다.

그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 컨텐츠는 다음과 같습니다
가상 호스트 파일에서 이를 참조하는 `Include` 문에 복사됩니다.

### 허용 목록 제거

폴더 `conf.d/whitelists`을 제거하고 을 참조하는 가상 호스트 파일에서 `Include` 문을 제거합니다
해당 하위 폴더에 있는 일부 파일입니다.

### 더 이상 사용할 수 없는 변수 모두 바꾸기

모든 가상 호스트 파일에서 다음을 수행합니다.

`PUBLISH_DOCROOT` 이름을 `DOCROOT` 로 변경합니다.
`DISP_ID`, `PUBLISH_FORCE_SSL` 또는 `PUBLISH_WHITELIST_ENABLED` 변수를 참조하는 섹션을 제거합니다.

### 검사기를 실행하여 상태 확인

`httpd` 하위 명령을 사용하여 디렉토리에서 Dispatcher 검사기를 실행합니다.

```
$ validator httpd .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

허용 목록에추가된이 아닌 Apache 지시문이 표시되면 제거합니다.

### 게시되지 않은 모든 팜 제거

`author`, `unhealthy`, `health`,
이름에 `lc` 또는 `flush`. `conf.dispatcher.d/enabled_farms` `conf.dispatcher.d/available_farms`에 없는 모든 팜 파일
에 연결된 도 제거할 수 있습니다.

### 팜 파일 이름 변경

`conf.d/enabled_farms`의 모든 팜 이름은 `*.farm` 패턴과 일치하도록 이름을 변경해야 합니다(예:
`customerX_farm.any`라는 팜 파일의 이름은 `customerX.farm`로 변경해야 합니다.

### cache 확인

`conf.dispatcher.d/cache` 디렉토리를 입력합니다.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/cache`이 비어 있으면 `conf.dispatcher.d/cache/rules.any` 파일을 복사합니다
표준 Dispatcher 구성에서 이 폴더로 표준 Dispatcher
구성은 이 SDK의 `src` 폴더에서 찾을 수 있습니다. 적응하는 것을 잊지 마세요
팜 파일에서 `ams_*_cache.any` 규칙 파일을 참조하는 `$include` 문
또한.

대신 `conf.dispatcher.d/cache`에 접미사가 `_cache.any`인 단일 파일이 포함되어 있는 경우,
이름을 `rules.any`로 변경하고 `$include` 문을 수정해야 합니다
팜 파일에서도 해당 파일을 참조합니다.

그러나 폴더에 해당 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 내용이 포함됩니다
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

`_invalidate_allowed.any` 접미사가 있는 파일을 제거합니다.

기본값에서 `conf.dispatcher.d/cache/default_invalidate_any` 파일을 복사합니다
Cloud Dispatcher 구성의 AEM을 해당 위치에 지정합니다.

각 팜 파일에서 `cache/allowedClients` 섹션의 내용을 제거하고 바꿉니다
사용:

```
$include "../cache/default_invalidate.any"
```

### client headers 확인

`conf.dispatcher.d/clientheaders` 디렉토리를 입력합니다.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/clientheaders`에 접미사가 `_clientheaders.any`인 단일 파일이 포함되어 있으면
이름을 `clientheaders.any`로 변경하고 `$include` 문을 수정해야 합니다
팜 파일에서도 해당 파일을 참조합니다.

그러나 폴더에 해당 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 내용이 포함됩니다
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

기본값에서 `conf.dispatcher/clientheaders/default_clientheaders.any` 파일을 복사합니다
AEM as a Cloud Service Dispatcher 구성을 해당 위치에 지정합니다.

각 팜 파일에서 다음과 같은 clientheader 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

다음 문으로 바꿉니다.

```
$include "../clientheaders/default_clientheaders.any"
```

### filter 확인

`conf.dispatcher.d/filters` 디렉토리를 입력합니다.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/filters`에 단일 파일이 포함되어 있으면 이름을 로 변경해야 합니다.
`filters.any` 및에서 이를 참조하는 `$include` 문을 수정하는 것을 잊지 마십시오
파일을 팜 파일에도 포함합니다.

그러나 폴더에 해당 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 내용이 포함됩니다
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

기본값에서 `conf.dispatcher/filters/default_filters.any` 파일을 복사합니다
AEM as a Cloud Service Dispatcher 구성을 해당 위치에 지정합니다.

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

다음 문으로 바꿉니다.

```
$include "../filters/default_filters.any"
```

### renders 확인

`conf.dispatcher.d/renders` 디렉토리를 입력합니다.

해당 폴더의 파일을 모두 제거합니다.

기본값에서 `conf.dispatcher.d/renders/default_renders.any` 파일을 복사합니다
AEM as a Cloud Service Dispatcher 구성을 해당 위치에 지정합니다.

각 팜 파일에서 `renders` 섹션의 내용을 제거하고 바꿉니다
사용:

```
$include "../renders/default_renders.any"
```

### virtualhosts 확인

`conf.dispatcher.d/vhosts` 디렉토리 이름을 `conf.dispatcher.d/virtualhosts` 로 변경하고 입력합니다.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/virtualhosts`에 단일 파일이 포함되어 있으면 이름을 로 변경해야 합니다.
`virtualhosts.any` 및에서 이를 참조하는 `$include` 문을 수정하는 것을 잊지 마십시오
파일을 팜 파일에도 포함합니다.

그러나 폴더에 해당 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 내용이 포함됩니다
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

기본값에서 `conf.dispatcher/virtualhosts/default_virtualhosts.any` 파일을 복사합니다
AEM as a Cloud Service Dispatcher 구성을 해당 위치에 지정합니다.

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

다음 문으로 바꿉니다.

```
$include "../virtualhosts/default_virtualhosts.any"
```

### 검사기를 실행하여 상태 확인

`dispatcher` 하위 명령을 사용하여 디렉토리에서 AEM as a Cloud Service Dispatcher 검사기를 실행합니다.

```
$ validator dispatcher .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

정의되지 않은 변수 `PUBLISH_DOCROOT`와 관련된 오류가 표시되면 이름을 `DOCROOT`로 바꿀 수 있습니다.

다른 모든 오류에 대해서는 유효성 검사기 도구 설명서의 문제 해결 섹션을 참조하십시오.

### 로컬 배포로 구성을 테스트합니다(Docker 설치 필요).

AEM에서 스크립트 `docker_run.sh`을 Cloud Service Dispatcher 도구로 사용하여 테스트할 수 있습니다
구성에
배포:

### 1단계:유효성 검사기를 사용하여 배포 정보 생성

```
validator full -d out .
```

전체 구성을 확인하고 `out`에 배포 정보를 생성합니다.

### 2단계:해당 배포 정보를 사용하여 Docker 이미지에서 Dispatcher 시작

macOS 컴퓨터에서 실행 중인 AEM 게시 서버를 사용하여 포트 4503에서 수신 대기합니다.
다음과 같이 해당 서버 앞에서 Dispatcher를 시작할 수 있습니다.

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

그러면 컨테이너가 시작되고 로컬 포트 8080에 Apache가 표시됩니다.

### 새 Dispatcher 구성 사용

축하합니다! 유효성 검사기가 더 이상 문제를 보고하지 않고
docker 컨테이너는 아무런 오류 또는 경고 없이 시작됩니다.
구성을 `dispatcher/src` 하위 디렉토리로 이동할 준비가 됨
git 리포지토리(.

**AMS Dispatcher 구성 버전 1을 사용하는 고객은 고객 지원 센터에 문의하여 버전 1에서 버전 2로 마이그레이션함으로써 위의 지침을 따를 수 있도록 해야 합니다.**
