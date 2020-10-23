---
title: 클라우드의 디스패처
description: '클라우드의 디스패처 '
translation-type: tm+mt
source-git-commit: 2bf7578ec5431f98ab7cfff55770766228ba63e2
workflow-type: tm+mt
source-wordcount: '4082'
ht-degree: 8%

---


# 클라우드의 디스패처 {#Dispatcher-in-the-cloud}

## Apache and Dispatcher configuration and testing {#apache-and-dispatcher-configuration-and-testing}

이 섹션에서는 AEM을 Cloud Service Apache 및 Dispatcher 구성으로 구성하는 방법과 Cloud 환경에 배포하기 전에 이를 로컬로 검증하고 실행하는 방법에 대해 설명합니다. 또한 클라우드 환경의 디버깅에 대해 설명합니다. Dispatcher에 대한 자세한 내용은 [AEM Dispatcher 설명서를 참조하십시오](https://docs.adobe.com/content/help/ko-KR/experience-manager-dispatcher/using/dispatcher.html).

>[!NOTE]
>
>Windows 사용자는 Windows 10 Professional 또는 Docker를 지원하는 기타 배포를 사용해야 합니다. 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 사전 요구 사항입니다. 아래 섹션에는 Mac 또는 Linux 버전의 SDK를 사용하는 명령이 포함되어 있지만 Windows SDK는 유사한 방식으로 사용할 수 있습니다.

>[!WARNING]
>
>Windows 사용자:cloud service 로컬 디스패처 도구(v2.0.20)로서 AEM의 현재 버전은 Windows와 호환되지 않습니다. Windows 호환성에 대한 업데이트를 받으려면 [Adobe](https://daycare.day.com/home.html) 지원 센터에 문의하십시오.

## 발송자 도구 {#dispatcher-sdk}

디스패처 도구는 Cloud Service SDK로서 전체 AEM에 포함되어 있으며 다음을 제공합니다.

* 발송자를 위한 고급 프로젝트에 포함할 구성 파일이 포함된 바닐라 파일 구조입니다.
* 고객이 디스패처 구성에 Cloud Service 지원 디렉티브로 AEM만 포함되는지 확인할 수 있는 도구        또한 Apache를 성공적으로 시작할 수 있도록 도구에서 구문이 올바른지 확인합니다.
* 발송자를 로컬로 불러오는 Docker 이미지.

## 도구 다운로드 및 추출 {#extracting-the-sdk}

AEM SDK로 [Cloud Service에](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)포함된 디스패처 도구는 [소프트웨어 배포](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) 포털의 zip 파일에서 다운로드할 수 있습니다. 이 새로운 발송자 도구 버전에서 사용 가능한 모든 새 구성을 사용하여 클라우드 이상에서 해당 버전의 AEM을 실행하는 클라우드 환경에 배포할 수 있습니다.
/Users/raiman/Documents/experience-manager-cloud-service.en/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.mdmacOS/Linux 및 Windows용 디스패처 도구를 번들로 제공하는 SDK의 압축을 해제합니다.

**macOS/Linux**&#x200B;의 경우 디스패처 도구를 가공할 수 있도록 만들고 실행합니다. 저장한 디렉토리 아래에 있는 Dispatcher 도구 파일 `version` 의 자체 추출이 이루어집니다(디스패처 도구 버전).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Windows**&#x200B;의 경우 Dispatcher 도구 zip 보관 파일을 추출합니다.

## 파일 구조 {#file-structure}

프로젝트 디스패처 하위 폴더의 구조는 아래에 설명되어 있으며 maven project dispatcher 폴더에 복사되어야 합니다.

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

다음 파일을 사용자 정의할 수 있으며 배포 시 클라우드 인스턴스로 전송됩니다.

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

이러한 파일 중 하나 이상을 보유할 수 있습니다. 호스트 이름과 일치하는 `<VirtualHost>` 항목이 포함되며 Apache가 다른 규칙으로 각 도메인 트래픽을 처리할 수 있습니다. 파일은 디렉토리에서 생성되며 `available_vhosts` 디렉토리의 심볼릭 링크로 `enabled_vhosts` 활성화됩니다. 파일에서 `.vhost` 다시 쓰기 및 변수와 같은 기타 파일이 포함됩니다.

* `conf.d/rewrites/rewrite.rules`

이 파일은 `.vhost` 파일 내에서 포함됩니다. 에 대한 다시 작성 규칙 세트가 있습니다 `mod_rewrite`.

>[!NOTE]
>
>현재는 사이트별 파일이 아닌 단일 다시 작성 파일을 사용해야 합니다. 파일 크기는 1MB 미만이어야 합니다.

* `conf.d/variables/custom.vars`

이 파일은 `.vhost` 파일 내에서 포함됩니다. 이 위치에 Apache 변수에 대한 정의를 배치할 수 있습니다.

* `conf.d/variables/global.vars`

이 파일은 `dispatcher_vhost.conf` 파일 내부에서 포함됩니다. 이 파일에서 디스패처를 변경하고 로그 수준을 다시 작성할 수 있습니다.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

이러한 파일 중 하나 이상을 가질 수 있으며, 팜이 호스트 이름과 일치하는 팜을 포함하고 디스패처 모듈이 서로 다른 규칙으로 각 팜을 처리하도록 허용합니다. 파일은 디렉토리에서 생성되며 `available_farms` 디렉토리의 심볼릭 링크로 `enabled_farms` 활성화됩니다. 파일에서 필터, 캐시 규칙 및 기타 파일 `.farm` 이 포함됩니다.

* `conf.dispatcher.d/cache/rules.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 캐싱 기본 설정을 지정합니다.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 백 엔드로 전달해야 하는 요청 헤더를 지정합니다.

* `conf.dispatcher.d/filters/filters.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 트래픽이 필터링되어야 하는 사항을 변경하고 백엔드로 만들지 않는 규칙 집합이 있습니다.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 호스트 이름 또는 URI 경로 목록이 글로벌 일치에 의해 일치됩니다. 요청을 제공하기 위해 사용할 백엔드를 결정합니다.

위 파일은 아래 나열된 불변경 구성 파일을 참조합니다. 변경할 수 없는 파일의 변경 사항은 클라우드 환경에서 디스패처가 처리하지 않습니다.

**변경 불가능한 구성 파일**

이러한 파일은 기본 프레임워크의 일부이며 표준 및 모범 사례를 적용합니다. 파일을 로컬에서 수정하거나 삭제해도 Cloud 인스턴스로 전송되지 않으므로 파일은 변경 불가능한 것으로 간주됩니다.

위의 파일은 아래 나열된 변경할 수 없는 파일을 참조한 다음 추가 문이나 오버라이드를 참조하는 것이 좋습니다. 발송자 구성이 클라우드 환경에 배포되면 로컬 개발에 사용된 버전에 관계없이 불변량 파일의 최신 버전이 사용됩니다.

* `conf.d/available_vhosts/default.vhost`

샘플 가상 호스트를 포함합니다. 자신의 가상 호스트에 대해 이 파일의 복사본을 만들고 사용자 요구에 맞게 변경하고 사용자 지정된 복사본에 대한 심볼 링크 `conf.d/enabled_vhosts` 를 만듭니다.

* `conf.d/dispatcher_vhost.conf`

가상 호스트 및 전역 변수가 포함된 방법을 보여주는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.d/rewrites/default_rewrite.rules`

표준 프로젝트에 적합한 기본 다시 작성 규칙. 사용자 지정이 필요한 경우 수정합니다 `rewrite.rules`. 사용자 정의에서는 기본 규칙이 요구 사항에 맞는 경우에도 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/available_farms/default.farm`

샘플 디스패처 팜을 포함합니다. 자신의 팜에 대해 이 파일의 복사본을 만들고 사용자 지정한 다음 사용자 지정된 복사본에 대한 심볼적인 링크 `conf.d/enabled_farms` 를 만듭니다.

* `conf.dispatcher.d/cache/default_invalidate.any`

시작 시 기본 프레임워크의 일부를 생성합니다. 정의한 모든 팜의 섹션에 이 파일을 **포함해야** 합니다 `cache/allowedClients` .

* `conf.dispatcher.d/cache/default_rules.any`

표준 프로젝트에 적합한 기본 캐시 규칙입니다. 사용자 지정이 필요한 경우 수정합니다 `conf.dispatcher.d/cache/rules.any`. 사용자 정의에서는 기본 규칙이 요구 사항에 맞는 경우에도 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

표준 프로젝트에 적합한 기본 요청 헤더가 백 엔드로 전달됩니다. 사용자 지정이 필요한 경우 수정합니다 `clientheaders.any`. 사용자 지정에서는 필요에 맞게 기본 요청 헤더를 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/dispatcher.any`

디스패처 팜이 포함된 방법을 보여주는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.dispatcher.d/filters/default_filters.any`

표준 프로젝트에 적합한 기본 필터입니다. 사용자 지정이 필요한 경우 수정합니다 `filters.any`. 사용자 정의에서는 기본 필터가 사용자의 요구 사항에 맞는 경우에도 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/renders/default_renders.any`

기본 프레임워크의 일부로 이 파일은 시작 시 생성됩니다. 정의한 모든 팜의 섹션에 이 파일을 **포함해야** 합니다 `renders` .

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

표준 프로젝트에 적합한 기본 호스트 글로빙입니다. 사용자 지정이 필요한 경우 수정합니다 `virtualhosts.any`. 사용자 지정에서는 들어오는 **모든** 요청과 일치하므로 기본 호스트 글로브를 포함해서는 안 됩니다.

>[!NOTE]
>
>Cloud Service 전문가 원형인 AEM은 동일한 발송자 구성 파일 구조를 생성합니다.

아래 섹션에서는 내부 릴리스를 배포할 때 Cloud Manager에서 관련 품질 게이트를 전달할 수 있도록 구성을 로컬로 검증하는 방법에 대해 설명합니다.

## Dispatcher 구성에서 지원되는 디렉티브의 로컬 유효성 검사 {#local-validation-of-dispatcher-configuration}

유효성 검사 도구는 Mac OS, Linux 또는 Windows 바이너리 `bin/validator` 로 SDK에서 사용할 수 있으므로 고객은 Cloud Manager가 릴리스를 빌드하고 배포하는 동안 수행하는 동일한 유효성 검사를 실행할 수 있습니다.

다음과 같이 호출됩니다. `validator full [-d folder] [-w whitelist] zip-file | src folder`

이 도구는 모든 파일을 패턴으로 스캔하여 디스패처 구성이 AEM에서 지원하는 적절한 지시어를 클라우드 서비스로 사용하고 있는지 확인합니다 `conf.d/enabled_vhosts/*.vhost`. Apache 구성 파일에 허용되는 지시어는 유효성 검사기의 명령을 실행하여 나열할 수 허용 목록에 추가하다 있습니다.

```
$ validator whitelist
Cloud manager validator 2.0.4
 
Whitelisted directives:
  <Directory>
  ...
  
```

아래 표는 지원되는 apache 모듈을 보여줍니다.

| 모듈 이름 | 참조 페이지 |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_auth_basic` | [https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html](https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html) |
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
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

고객은 임의의 모듈을 추가할 수 없지만, 향후 제품에 포함할 추가 모듈을 고려할 수 있습니다. 고객은 위에 설명된 대로 SDK에서 유효성 검사기의 명령을 실행하여 지정된 발송자 버전에 사용할 수 있는 지시어 목록을 찾을 수 있습니다허용 목록에 추가하다.

에는 허용 목록에 추가하다 고객 구성에서 허용되는 Apache 지시문 목록이 포함되어 있습니다. 지시문이 허용 목록에추가된 없으면 도구가 오류를 기록하고 0이 아닌 종료 코드를 반환합니다. 명령줄에허용 목록에 추가하다가 없는 경우(호출해야 하는 방식), 이 도구는 Cloud 환경에 배포하기 전에 Cloud Manager가 유효성 검사에 사용할 기본 허용 목록에 추가하다를 사용합니다.

또한 패턴을 사용하여 모든 파일을 추가로 스캔하고 다음을 `conf.dispatcher.d/enabled_farms/*.farm` 확인합니다.

* 을 통해 허용되는 필터 규칙이 없습니다 `/glob` ( [자세한 내용은 CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) 참조).
* 관리 기능이 노출되지 않습니다. 예를 들어 다음과 같은 경로에 액세스할 수 있습니다 `/crx/de or /system/console`.

마스터 아티팩트나 하위 `dispatcher/src` 디렉터리에 대해 실행하면 유효성 검사 실패가 보고됩니다.

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-whitelisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

유효성 검사 도구는 허용되지 않은 Apache 지시문의 금지된 사용만 허용 목록에추가된 보고합니다. 이 정보는 실행 중인 환경의 Apache 모듈에만 사용할 수 있으므로 Apache 구성에 대한 구문 또는 세미나 문제를 보고하지는 않습니다.

다음은 도구로 출력되는 일반적인 유효성 검사 오류를 디버깅하기 위한 문제 해결 기술입니다.

**보관 파일에서 하위 `conf.dispatcher.d` 폴더를 찾을 수 없음**

보관 파일에는 폴더 `conf.d` 와 폴더가 포함되어야 합니다 `conf.dispatcher.d`. 아카이브의 접두사를 ****&#x200B;사용하지 `etc/httpd` 않아야합니다.

**팜을 찾을 수 없습니다.`conf.dispatcher.d/enabled_farms`**

활성화된 팜은 언급된 하위 폴더에 있어야 합니다.

**포함된 파일(...)의 이름은 다음과 같아야 합니다....**

팜 구성에는 특정 파일을 포함해야 **하는** 두 개의 섹션이 있습니다. `/renders` 섹션 `/allowedClients` 에서 `/cache` 확인할 수 있습니다. 이러한 항목은 다음과 같이 표시되어야 합니다.

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

**파일을 알 수 없는 위치에 포함했습니다....**

자신의 파일을 포함할 수 있는 팜 구성에는 네 개의 섹션이 있습니다. `/clientheaders`, `filters`, `/rules` in `/cache` section and `/virtualhosts` 포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 섹션 | 파일 이름 포함 |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

또는 파일 이름에 단어(예: ) **가 추가되는 파일의** 기본 `default_`버전을 포함할 수있습니다. `../filters/default_filters.any`.

**include statement at (...)에 있는 모든 다른 위치에 있는...**

위의 단락에 언급된 6개 섹션 이외에, `$include` 명령문을 사용할 수 없습니다. 예를 들어 다음과 같이 이 오류가 생성됩니다.

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**허용된 클라이언트/렌더는 다음 제품에서 포함되지 않습니다....**

이 오류는 `/renders` `/allowedClients` `/cache` 섹션 및 섹션에 포함을 지정하지 않을 때 생성됩니다. 포함된&#x200B;**파일(...)의 이름을 지정해야 합니다....** 섹션을 참조하십시오.

**요청을 허용하기 위해 글로벌 패턴을 사용할 수 없습니다.**

전체 요청 라인(예: 전체 요청 라인)과 일치하는 `/glob` 스타일 규칙이 있는 요청을 허용한다는 것은 안전하지 않습니다.

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

이 문은 `css` 파일에 대한 요청을 허용하기 위한 것이지만, 쿼리 문자열 **이 뒤에 오는** 모든 리소스에 대한 요청도 허용합니다 `?a=.css`. 따라서 이러한 필터를 사용할 수 없습니다(CVE-2016-0957 참조).

**포함된 파일(...)과 알려진 파일이 일치하지 않습니다.**

Apache 가상 호스트 구성에는 다음과 같이 지정할 수 있는 두 가지 유형의 파일이 있습니다.재작성 및 변수.
포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 유형 | 파일 이름 포함 |
|-----------|---------------------------------|
| 다시 쓰기 | `conf.d/rewrites/rewrite.rules` |
| 변수 | `conf.d/variables/custom.vars` |

또는 이름이 인 **기본** 버전의 다시 작성 규칙을 포함할 수 `conf.d/rewrites/default_rewrite.rules`있습니다.
변수 파일의 기본 버전은 없습니다.

**더 이상 사용되지 않는 구성 레이아웃이 감지되어 호환성 모드를 사용하도록 설정**

이 메시지는 구성에 completeApache 구성 및 접두사가 있는 파일이 포함된 더 이상 사용되지 않는 버전 1 레이아웃이 있음을 `ams_` 나타냅니다. 이 기능은 여전히 백업 호환성을 위해 지원되지만 새 레이아웃으로 전환해야 합니다.

## apache httpd가 시작할 수 있도록 발송자 구성 구문의 로컬 유효성 검사 {#local-validation}

Dispatcher 모듈 구성에 지원되는 지시문만 포함되도록 설정되었으면 Apache를 시작할 수 있도록 구문이 올바른지 확인해야 합니다. 이를 테스트하려면 문서를 로컬로 설치해야 합니다. AEM이 실행되는 것은 필요하지 않습니다.

아래와 같이 `validate.sh` 스크립트를 사용하십시오.

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

스크립트에서는 다음을 수행합니다.

1. 이전 섹션의 유효성 검사기를 실행하여 지원되는 지시문만 포함하도록 합니다. 구성이 올바르지 않으면 스크립트가 실패합니다.
2. Apache httpd가 시작될 수 있도록 구문이 올바른지 테스트하는 `httpd -t command` 를 실행합니다. 성공하면 배포를 위해 구성을 준비해야 합니다.

## 로컬에서 Apache 및 Dispatcher 구성 테스트 {#testing-apache-and-dispatcher-configuration-locally}

Apache 및 Dispatcher 구성을 로컬로 테스트할 수도 있습니다. 위 설명에 따라 문서를 로컬로 설치하고 구성을 통해 유효성을 검사해야 합니다.

모든 발송자 구성 파일로 폴더를 출력하는 매개 변수를 사용하여 유효성 검사기 도구( `validator.sh` 앞에서 언급한 것과 다름)를 `-d` 실행합니다. 그런 다음 `docker_run.sh` 스크립트를 실행하여 해당 폴더를 인수로 전달합니다. 포트 번호를 제공하여(여기:8080)을 사용하여 디스패처 끝점을 노출하면 Docker 컨테이너가 시작되어 사용자의 구성으로 디스패처를 실행합니다.

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

이렇게 하면 4503 포트에서 로컬 Mac OS 시스템에서 실행되는 AEM 인스턴스를 가리키는 백 엔드가 있는 컨테이너에서 디스패처가 시작됩니다.

## Apache 및 Dispatcher 구성 디버깅 {#debugging-apache-and-dispatcher-configuration}

다음 전략을 사용하여 디스패처 모듈의 로그 출력을 높이고 로컬 및 클라우드 환경에서 `RewriteRule` 평가 결과를 확인할 수 있습니다.

이러한 모듈의 로그 수준은 변수와 변수에 의해 `DISP_LOG_LEVEL` 정의됩니다 `REWRITE_LOG_LEVEL`. 파일에 설정할 수 있습니다 `conf.d/variables/global.vars`. 관련 부분은 다음과 같습니다.

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

디스패처를 로컬로 실행할 때 로그는 터미널 출력에 직접 인쇄됩니다. 대부분의 경우, 이러한 로그가 DEBUG에 있어야 하며, Docker를 실행할 때 디버그 수준을 매개 변수로 전달하여 수행할 수 있습니다. 예: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

클라우드 환경을 위한 로그는 Cloud Manager에서 사용할 수 있는 로깅 서비스를 통해 노출됩니다.

## 환경별 서로 다른 Dispatcher 구성 {#different-dispatcher-configurations-per-environment}

현재 동일한 디스패처 구성이 Cloud Service 환경으로 모든 AEM에 적용됩니다. 런타임에는 정의 `ENVIRONMENT_TYPE` 와 함께 현재 실행 모드(dev, stage 또는 prod)를 포함하는 환경 변수가 있습니다. 정의 `ENVIRONMENT_DEV`는 `ENVIRONMENT_STAGE` 또는 `ENVIRONMENT_PROD`. Apache 구성에서 이 변수를 표현식에 직접 사용할 수 있습니다. 또는 정의를 사용하여 논리를 작성할 수 있습니다.

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

Dispatcher 구성에서는 동일한 환경 변수를 사용할 수 있습니다. 추가 로직이 필요한 경우 위의 예에서 보듯이 변수를 정의한 다음 발송자 구성 섹션에서 사용하십시오.

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

구성을 로컬로 테스트할 때 변수를 스크립트로 직접 전달하여 다양한 환경 유형 `DISP_RUN_MODE` 을 시뮬레이션할 수 `docker_run.sh` 있습니다.

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

DISP_RUN_MODE에 대한 값을 전달하지 않을 때의 기본 실행 모드는 &quot;dev&quot;입니다.
사용 가능한 옵션 및 변수의 전체 목록을 보려면 인수 없이 스크립트를 `docker_run.sh` 실행하십시오.

## Docker 컨테이너가 사용 중인 Dispatcher 구성 보기 {#viewing-dispatcher-configuration-in-use-by-docker-container}

환경별 구성에서는 실제 발송자 구성이 어떻게 보이는지 판단하기가 어려울 수 있습니다. 문서 컨테이너를 시작한 후 다음과 같이 폐기할 수 `docker_run.sh` 있습니다.

* 사용 중인 문서 컨테이너 ID 확인:

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

## Cloud Service의 AMS 디스패처와 AEM의 주요 차이점 {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

위의 참조 페이지에서 설명한 바와 같이, AEM의 Apache 및 Dispatcher 구성은 AMS 1과 매우 유사합니다. 주요 차이점은 다음과 같습니다.

* AEM에서 Cloud Service으로 일부 Apache 지시어를 사용할 수 없습니다(예: `Listen` 또는 `LogLevel`).
* AEM에서 Cloud Service으로 사용할 경우 일부 Dispatcher 구성만 포함 파일에 넣을 수 있으며 이름 지정도 중요합니다. 예를 들어 여러 호스트 간에 재사용할 필터 규칙을 호출한 파일에 추가해야 합니다 `filters/filters.any`. 자세한 내용은 참조 페이지를 참조하십시오.
* AEM의 Cloud Service에서는 보안 문제를 방지하기 위해 사용하는 필터 규칙을 사용하지 않기 위해 추가 유효성 검사 `/glob` 가 있습니다. 사용 `deny *` 이 `allow *` (사용할 수 없음) 대신 사용되므로, 고객은 Dispatcher 로컬에서 실행하고 시험버전 및 오류를 수행하여 Dispatcher 필터가 어떤 경로를 추가하도록 차단하는지 정확히 알기 위해 로그를 보는 것이 좋습니다.

## AMS에서 AEM으로 발송자 구성을 Cloud Service으로 마이그레이션하는 지침

디스패처 구성 구조는 Cloud Service으로 Managed Services과 AEM이 서로 다르다. 아래에 제시된 것은 AMS Dispatcher 구성 버전 2에서 AEM으로 Cloud Service으로 마이그레이션하는 방법에 대한 단계별 가이드입니다.

## AMS를 클라우드 서비스 발송자 구성으로 AEM으로 변환하는 방법

다음 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다. It assumes
that you have an archive with a structure similar to the one described in [Cloud Manager dispatcher configuration](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### 아카이브 추출 및 최종 접두사 제거

아카이브를 하나의 폴더로 추출하고, 바로 하위 폴더가 `conf`, `conf.d``conf.dispatcher.d` 및 `conf.modules.d`로 시작되도록 합니다. 그렇지 않으면 위쪽으로 옮겨라.

### 사용하지 않는 하위 폴더와 파일 제거

하위 폴더 `conf` 와 `conf.modules.d`일치하는 파일도 제거할 수 있습니다 `conf.d/*.conf`.

### 게시되지 않은 모든 가상 호스트 제거

가상 호스트 파일 `conf.d/enabled_vhosts` 의 이름 `author`, `unhealthy``health``lc` 또는 `flush` 해당 이름을 가진 가상 호스트 파일을제거합니다. All virtual host files in `conf.d/available_vhosts` that are not
linked to can be removed as well.

### 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 달기

가상 호스트 파일에 포트 80 이외의 다른 포트만 참조하는 섹션이 있는 경우

```
<VirtualHost *:443>
...
</VirtualHost>
```

해당 섹션을 제거하거나 주석을 답니다. 이러한 섹션의 문은 처리되지 않지만, 이 문을 계속 유지하면 아무것도 적용되지 않은 상태로 편집을 종료할 수 있으므로 혼동을 줄 수 있습니다.

### rewrites 확인

Enter directory `conf.d/rewrites`.

Remove any file named `base_rewrite.rules` and `xforwarded_forcessl_rewrite.rules` and remember to
remove `Include` statements in the virtual host files referring to them.

If `conf.d/rewrites` now contains a single file, it should be renamed to `rewrite.rules` and don&#39;t
forget to adapt the `Include` statements referring to that file in the virtual host files as well.

If the folder however contains multiple, virtual host specific files, their contents should be
copied to the `Include` statement referring to them in the virtual host files.

### 변수 확인

Enter directory `conf.d/variables`.

Remove any file named `ams_default.vars` and remember to remove `Include` statements in the virtual
host files referring to them.

If `conf.d/variables` now contains a single file, it should be renamed to `custom.vars` and don&#39;t
forget to adapt the `Include` statements referring to that file in the virtual host files as well.

If the folder however contains multiple, virtual host specific files, their contents should be
copied to the `Include` statement referring to them in the virtual host files.

### 허용 목록 제거

Remove the folder `conf.d/whitelists` and remove `Include` statements in the virtual host files referring to
some file in that subfolder.

### 더 이상 사용할 수 없는 변수 모두 바꾸기

모든 가상 호스트 파일에서 다음을 수행합니다.

이름 `PUBLISH_DOCROOT` 을 `DOCROOT`Remove 섹션, `DISP_ID``PUBLISH_FORCE_SSL` 또는 `PUBLISH_WHITELIST_ENABLED`

### 검사기를 실행하여 상태 확인

Run the dispatcher validator in your directory, with the `httpd` subcommand:

```
$ validator httpd .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

Apache 지시문이 표시되지 허용 목록에추가된 않으면 제거합니다.

### 게시되지 않은 모든 팜 제거

이름이 있는 팜 파일 `conf.dispatcher.d/enabled_farms``author`을 `unhealthy``health`모두`lc` 제거합니다 `flush` . All farm files in `conf.dispatcher.d/available_farms` that are not
linked to can be removed as well.

### 팜 파일 이름 변경

패턴과 일치하도록 모든 팜의 이름을 `conf.d/enabled_farms` 변경해야 `*.farm`합니다. 예를 들어 호출된 `customerX_farm.any` afarm 파일의 이름을 변경해야 합니다 `customerX.farm`.

### cache 확인

Enter directory `conf.dispatcher.d/cache`.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/cache` is now empty, copy the file `conf.dispatcher.d/cache/rules.any`
from the standard dispatcher configuration to this folder. The standard dispatcher
configuration can be found in the folder `src` of this SDK. Don&#39;t forget to adapt the
`$include` statements referring to the `ams_*_cache.any` rule files  in the farm files
as well.

If instead `conf.dispatcher.d/cache` now contains a single file with suffix `_cache.any`,
it should be renamed to `rules.any` and don&#39;t forget to adapt the `$include` statements
referring to that file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

Remove any file that has the suffix `_invalidate_allowed.any`.

Cloud 디스패처 구성 `conf.dispatcher.d/cache/default_invalidate_any` 의 기본 AEM에서 해당 위치로 파일을 복사합니다.

In each farm file, remove any contents in the `cache/allowedClients` section and replace it
with:

```
$include "../cache/default_invalidate.any"
```

### client headers 확인

Enter directory `conf.dispatcher.d/clientheaders`.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/clientheaders` now contains a single file with suffix `_clientheaders.any`,
it should be renamed to `clientheaders.any` and don&#39;t forget to adapt the `$include` statements
referring to that file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

기본 AEM `conf.dispatcher/clientheaders/default_clientheaders.any` 에서 Cloud Service 디스패처 구성으로 파일을 해당 위치에 복사합니다.

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

Enter directory `conf.dispatcher.d/filters`.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/filters` now contains a single file it should be renamed to
`filters.any` and don&#39;t forget to adapt the `$include` statements referring to that
file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

기본 AEM `conf.dispatcher/filters/default_filters.any` 에서 Cloud Service 디스패처 구성으로 파일을 해당 위치에 복사합니다.

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

다음 문으로 바꿉니다.

```
$include "../filters/default_filters.any"
```

### renders 확인

Enter directory `conf.dispatcher.d/renders`.

해당 폴더의 파일을 모두 제거합니다.

기본 AEM `conf.dispatcher.d/renders/default_renders.any` 에서 Cloud Service 디스패처 구성으로 파일을 해당 위치에 복사합니다.

In each farm file, remove any contents in the `renders` section and replace it
with:

```
$include "../renders/default_renders.any"
```

### virtualhosts 확인

Rename the directory `conf.dispatcher.d/vhosts` to `conf.dispatcher.d/virtualhosts` and enter it.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/virtualhosts` now contains a single file it should be renamed to
`virtualhosts.any` and don&#39;t forget to adapt the `$include` statements referring to that
file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

기본 AEM `conf.dispatcher/virtualhosts/default_virtualhosts.any` 에서 Cloud Service 디스패처 구성으로 파일을 해당 위치에 복사합니다.

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

다음 문으로 바꿉니다.

```
$include "../virtualhosts/default_virtualhosts.any"
```

### 검사기를 실행하여 상태 확인

다음 하위 명령을 사용하여 디렉토리에서 AEM을 Cloud Service 발송자 유효성 검사기로 `dispatcher` 실행합니다.

```
$ validator dispatcher .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

정의되지 않은 변수 `PUBLISH_DOCROOT`와 관련된 오류가 표시되면 이름을 `DOCROOT`로 바꿀 수 있습니다.

다른 모든 오류에 대해서는 유효성 검사기 도구 설명서의 문제 해결 섹션을 참조하십시오.

### 로컬 배포로 구성 테스트(Docker 설치 필요)

Using the script `docker_run.sh` in the AEM as a Cloud Service Dispatcher Tools, you can test that
your configuration does not contain any other error that would only show up in
deployment:

### 1단계:유효성 검사기를 사용하여 배포 정보 생성

```
validator full -d out .
```

This validates the full configuration and generates deployment information in `out`

### 2단계:해당 배포 정보를 사용하여 문서 이미지에서 디스패처 시작

macOS 컴퓨터에서 실행 중인 AEM 게시 서버를 사용하여 포트 4503에서 수신 대기하면 다음과 같이 해당 서버 앞에서 Dispatcher를 시작할 수 있습니다.

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

그러면 컨테이너가 시작되고 로컬 포트 8080에 Apache가 표시됩니다.

### 새 발송자 구성 사용

축하합니다! If the validator no longer reports any issue and the
docker container starts up without any failures or warnings, you&#39;re
ready to move your configuration to a `dispatcher/src` subdirectory
of your git repository.

**AMS Dispatcher 구성 버전 1을 사용하는 고객은 위의 지침을 따를 수 있도록 고객 지원에 문의하여 버전 1에서 버전 2로 마이그레이션할 수 있도록 지원하시기 바랍니다.**
