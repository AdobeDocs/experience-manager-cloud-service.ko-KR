---
title: Dispatcher in the Cloud
description: 'Dispatcher in the Cloud '
translation-type: tm+mt
source-git-commit: b7f3122db5b55d515965b638c2b4aa4bc2a67fe6

---


# Dispatcher in the Cloud {#Dispatcher-in-the-cloud}

## Apache 및 Dispatcher 구성 및 테스트 {#apache-and-dispatcher-configuration-and-testing}

이 섹션에서는 AEM을 클라우드 서비스 Apache 및 Dispatcher 구성으로 구성하는 방법과 Cloud 환경에 배포하기 전에 로컬로 유효성을 확인하고 실행하는 방법에 대해 설명합니다. 또한 클라우드 환경에서의 디버깅에 대해서도 설명합니다. Dispatcher에 대한 자세한 내용은 AEM Dispatcher [설명서를](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html)참조하십시오.

>[!NOTE]
>Windows 사용자는 Windows 10 Professional 또는 Docker를 지원하는 다른 배포를 사용해야 합니다. 로컬 컴퓨터에서 Dispatcher를 실행하고 디버깅하기 위한 사전 요구 사항입니다. 아래 섹션에는 Mac 또는 Linux 버전의 SDK를 사용하는 명령이 포함되어 있지만 Windows SDK는 유사한 방식으로 사용할 수 있습니다.

## 발송자 도구 {#dispatcher-sdk}

발송자 도구는 클라우드 서비스 SDK로서 전체 AEM에 포함되어 있으며 다음을 제공합니다.

* 발송자를 위한 고급 프로젝트에 포함할 구성 파일이 들어 있는 바닐라 파일 구조
* 고객이 발송자 구성을 로컬에서 확인할 수 있는 툴
* 발송자를 로컬로 불러오는 Docker 이미지.

## 도구 다운로드 및 추출 {#extracting-the-sdk}

디스패처 도구는 소프트웨어 배포 포털의 zip 파일에서 다운로드할 [수](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) 있습니다. SDK 목록에 대한 액세스는 클라우드 서비스 환경으로 AEM Managed Services 또는 AEM을 사용하는 것으로 제한됩니다. 새 디스패처 도구 버전에서 사용할 수 있는 모든 새 구성을 사용하여 클라우드 이상에서 해당 버전의 AEM을 실행하는 클라우드 환경에 배포할 수 있습니다.

**macOS 및** Linux의 경우 셸 스크립트를 컴퓨터의 폴더에 다운로드하고 실행 파일로 만들어 실행합니다. Dispatcher Tools 파일은 저장한 디렉토리 아래에 자동으로 추출됩니다(디스패처 도구 `version` 버전).

```bash
$ chmod +x DispatcherSDKv<version>.sh
$ ./DispatcherSDKv<version>.sh
Verifying archive integrity...  100%   All good.
Uncompressing DispatcherSDKv<version>  100% 
```

**Windows의**&#x200B;경우 zip 아카이브를 다운로드하고 압축을 해제합니다.

## 파일 구조 {#file-structure}

프로젝트 디스패처 하위 폴더의 구조는 아래에 설명되며, maven 프로젝트 디스패처 폴더에 복사해야 합니다.

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

다음 파일은 사용자 정의할 수 있으며 배포 시 Cloud 인스턴스로 전송됩니다.

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

이러한 파일 중 하나 이상을 보유할 수 있습니다. 호스트 이름과 일치하는 `<VirtualHost>` 항목이 포함되며 Apache가 다른 규칙으로 각 도메인 트래픽을 처리할 수 있도록 합니다. 파일은 `available_vhosts` 디렉토리에 생성되며 `enabled_vhosts` 디렉토리에서 심볼 링크를 사용하여 활성화됩니다. 파일에서 `.vhost` 다시 쓰기 및 변수와 같은 다른 파일이 포함됩니다.

* `conf.d/rewrites/rewrite.rules`

이 파일은 `.vhost` 파일 내에서 포함됩니다. 에 대한 다시 작성 규칙 세트가 `mod_rewrite`있습니다.

>[!NOTE]
>
>현재 사이트 특정 파일이 아닌 단일 다시 작성 파일을 사용해야 합니다. 파일 크기는 1MB 미만이어야 합니다.

* `conf.d/variables/custom.vars`

이 파일은 `.vhost` 파일 내에서 포함됩니다. 이 위치에 Apache 변수에 대한 정의를 배치할 수 있습니다.

* `conf.d/variables/global.vars`

이 파일은 `dispatcher_vhost.conf` 파일 내부에서 포함됩니다. 이 파일에서 디스패처를 변경하고 로그 수준을 다시 작성할 수 있습니다.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

이러한 파일 중 하나 이상을 가질 수 있으며, 여기에는 호스트 이름과 일치하는 팜이 포함되어 있으며 디스패처 모듈에서 각 팜을 다른 규칙으로 처리할 수 있습니다. 파일은 `available_farms` 디렉토리에 생성되며 `enabled_farms` 디렉토리에서 심볼 링크를 사용하여 활성화됩니다. 파일로부터 필터, 캐시 규칙 및 기타 `.farm` 파일과 같은 기타 파일이 포함됩니다.

* `conf.dispatcher.d/cache/rules.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 캐싱 기본 설정을 지정합니다.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 백 엔드로 전달해야 하는 요청 헤더를 지정합니다.

* `conf.dispatcher.d/filters/filters.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 이 클래스에는 필터링해야 하는 트래픽을 변경하고 백엔드로 만들지 않는 규칙 집합이 있습니다.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

이 파일은 `.farm` 파일 내에서 포함됩니다. 호스트 이름 또는 글로벌 일치와 일치할 URI 경로 목록이 있습니다. 이렇게 하면 요청을 제공하는 데 사용할 백엔드가 결정됩니다.

위의 파일은 아래 나열된 변경할 수 없는 구성 파일을 참조합니다. 변경할 수 없는 파일의 변경 사항은 클라우드 환경에서 디스패처가 처리하지 않습니다.

**변경 불가능한 구성 파일**

이러한 파일은 기본 프레임워크의 일부이며 표준 및 모범 사례를 적용합니다. 파일을 로컬에서 수정하거나 삭제해도 Cloud 인스턴스로 전송되지 않으므로 파일은 변경할 수 없는 것으로 간주됩니다.

위의 파일은 아래 나열된 변경할 수 없는 파일을 참조한 다음 추가 문이나 오버라이드를 참조하는 것이 좋습니다. 발송자 구성이 클라우드 환경에 배포되면 로컬 개발에 사용된 버전에 관계없이 변경 불가능한 파일의 최신 버전이 사용됩니다.

* `conf.d/available_vhosts/default.vhost`

샘플 가상 호스트를 포함합니다. 자신의 가상 호스트에 대해 이 파일의 복사본을 만들고 사용자 요구에 맞게 변경한 다음 원하는 복사본으로 이동하여 `conf.d/enabled_vhosts` 심볼릭 링크를 만듭니다.

* `conf.d/dispatcher_vhost.conf`

가상 호스트 및 전역 변수가 포함되는 방법을 설명하는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.d/rewrites/default_rewrite.rules`

표준 프로젝트에 적합한 기본 다시 작성 규칙입니다. 사용자 지정이 필요한 경우 수정합니다 `rewrite.rules`. 사용자 정의에서 기본 규칙이 사용자의 요구 사항에 맞는 경우 기본 규칙을 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/available_farms/default.farm`

샘플 디스패처 팜을 포함합니다. 자신의 팜에 대해 이 파일의 복사본을 만들고 사용자 요구에 맞게 변경한 다음 원하는 복사본에 대한 심볼릭 링크를 `conf.d/enabled_farms` 만듭니다.

* `conf.dispatcher.d/cache/default_invalidate.any`

기본 프레임워크의 일부이며 시작 시 생성됩니다. 정의한 모든 팜의 **섹션에 이 파일을 포함해야** 합니다 `cache/allowedClients` .

* `conf.dispatcher.d/cache/default_rules.any`

표준 프로젝트에 적합한 기본 캐시 규칙 사용자 지정이 필요한 경우 수정합니다 `conf.dispatcher.d/cache/rules.any`. 사용자 정의에서 기본 규칙이 사용자의 요구 사항에 맞는 경우 기본 규칙을 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

표준 프로젝트에 적합한 기본 요청 헤더가 백 엔드로 전달됩니다. 사용자 지정이 필요한 경우 수정합니다 `clientheaders.any`. 사용자 지정에서 기본 요청 헤더가 사용자의 요구 사항에 맞는 경우에도 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/dispatcher.any`

디스패처 팜이 포함된 방법을 설명하는 데 사용되는 기본 프레임워크의 일부입니다.

* `conf.dispatcher.d/filters/default_filters.any`

표준 프로젝트에 적합한 기본 필터. 사용자 지정이 필요한 경우 수정합니다 `filters.any`. 사용자 정의에서 기본 필터가 사용자의 요구 사항에 맞는 경우 기본 필터를 먼저 포함할 수 있습니다.

* `conf.dispatcher.d/renders/default_renders.any`

기본 프레임워크의 일부로 이 파일은 시작 시 생성됩니다. 정의한 모든 팜의 **섹션에 이 파일을 포함해야** 합니다 `renders` .

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

표준 프로젝트에 적합한 기본 호스트 글로벌 빙입니다. 사용자 지정이 필요한 경우 수정합니다 `virtualhosts.any`. 사용자 지정에서는 들어오는 **모든** 요청과 일치하므로 기본 호스트 글로브를 포함해서는 안 됩니다.

>[!NOTE]
>클라우드 서비스 마비로서 AEM은 동일한 발송자 구성 파일 구조를 생성합니다.

아래 섹션에서는 내부 릴리스를 배포할 때 Cloud Manager에서 관련 품질 게이트를 전달할 수 있도록 구성을 로컬로 확인하는 방법에 대해 설명합니다.

## 발송자 구성의 로컬 유효성 검사 {#local-validation-of-dispatcher-configuration}

유효성 검사 도구는 Mac OS, Linux 또는 Windows 바이너리의 SDK에서 사용할 수 `bin/validator` 있으므로 고객은 릴리스를 빌드하고 배포하는 동안 Cloud Manager가 수행하는 동일한 유효성 검사를 실행할 수 있습니다.

이 메서드는 다음과 같이 호출됩니다. `validator full [-d folder] [-w whitelist] zip-file | src folder`

이 도구는 Apache 및 디스패처 구성의 유효성을 검사합니다. 패턴으로 모든 파일을 스캔하고 화이트리스트 `conf.d/enabled_vhosts/*.vhost` 지시문만 사용하는지 확인합니다. Apache 구성 파일에서 허용되는 지시어는 유효성 검사기의 화이트 리스트 명령을 실행하여 나열할 수 있습니다.

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

고객은 임의의 모듈을 추가할 수 없지만, 추가 모듈은 향후 제품에 포함시킬 수 있도록 고려될 수 있습니다. 고객은 Dispatcher 도구 설명서에 설명된 대로 SDK에서 &quot;유효성 검사기 화이트 리스트&quot;를 실행하여 지정된 Dispatcher 버전에 사용할 수 있는 지시어 목록을 찾을 수 있습니다.

화이트 리스트에는 고객 구성에서 허용되는 Apache 지시문 목록이 포함되어 있습니다. 지시문이 화이트리스트에 추가되지 않으면 도구는 오류를 기록하고 0이 아닌 종료 코드를 반환합니다. 명령줄에 허용 목록이 표시되지 않는 경우(호출해야 하는 방식), 이 도구는 Cloud Manager가 유효성 검사에 사용할 기본 허용 목록을 사용하여 Cloud 환경에 배포합니다.

또한 패턴을 사용하여 모든 파일을 추가로 스캔하고 다음을 `conf.dispatcher.d/enabled_farms/*.farm` 확인합니다.

* 을 통해 허용하는 필터 규칙이 없습니다 `/glob` ( [자세한 내용은 CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) 참조).
* 관리 기능이 노출되지 않습니다. 예를 들어 다음과 같은 경로에 액세스할 수 `/crx/de or /system/console`있습니다.

maven 아티팩트 또는 `dispatcher/src` 하위 디렉토리에 대해 실행하면 유효성 검사 실패가 보고됩니다.

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-whitelisted directives:
 conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
 conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

유효성 검사 도구는 화이트리스트에 포함되지 않은 금지된 Apache 지시문의 사용만 보고합니다. 이 정보는 실행 중인 환경에서 Apache 모듈에만 사용할 수 있으므로 Apache 구성과의 구문 또는 세미나 문제를 보고하지 않습니다.

유효성 검사 오류가 보고되지 않으면 구성이 배포할 준비가 됩니다.

다음은 도구에 의해 출력되는 일반적인 유효성 검사 오류를 디버깅하기 위한 문제 해결 기술입니다.

**보관 파일에서`conf.dispatcher.d`하위 폴더를 찾을 수 없음**

아카이브는 폴더 `conf.d` 및 `conf.dispatcher.d`폴더를 포함해야 합니다. 아카이브에 접두사를 ****&#x200B;사용하지 `etc/httpd` 마십시오.

**에서 팜을 찾을 수 없습니다.`conf.dispatcher.d/enabled_farms`**

사용 가능한 팜은 언급된 하위 폴더에 있어야 합니다.

**포함된 파일(...)의 이름은 다음과 같아야 합니다....**

팜 구성에는 특정 파일을 **포함해야 하는** 두 개의 섹션이 있습니다.In the `/renders` section `/allowedClients` in the `/cache` . 이러한 항목은 다음과 같아야 합니다.

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

**알 수 없는 위치에 파일 포함:...**

자신의 파일을 포함할 수 있는 팜 구성에는 네 개의 섹션이 있습니다. `/clientheaders`섹션 `filters`및 `/rules` 섹션 `/cache` `/virtualhosts`내 포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 섹션 | 파일 이름 포함 |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

또는 파일 이름에 단어(예: **** `default_`예: `../filters/default_filters.any`Adobe

**에 있는 문 포함(...)은 알려진 모든 위치 외부에 있습니다....**

위의 단락에 언급된 6개 섹션과는 별도로 `$include` 명령문을 사용할 수 없습니다. 예를 들어 다음과 같은 경우 이 오류가 발생합니다.

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**허용된 클라이언트/렌더링은 다음 제품에서 포함되지 않습니다....**

이 오류는 `/renders` `/allowedClients` `/cache` 섹션에 포함을 지정하지 않으면 생성됩니다. **포함된**&#x200B;파일(...)의 이름은 다음과 같습니다....섹션을 참조하십시오.

**요청을 허용하려면 글로벌 패턴을 사용하지 않아야 합니다.**

전체 요청 라인(예: 전체 요청 라인)에 대해 일치하는 `/glob` 스타일 규칙이 있는 요청을 허용하는 것은 안전하지 않습니다.

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

이 문은 `css` 파일에 대한 요청을 허용하기 위한 것이지만 쿼리 문자열이 **뒤에 오는** 모든 `?a=.css`리소스에 대한 요청도 허용합니다. 따라서 이러한 필터를 사용할 수 없습니다(CVE-2016-0957 참조).

**포함된 파일(...)이 알려진 파일과 일치하지 않습니다.**

Apache 가상 호스트 구성에는 다음과 같이 지정할 수 있는 두 가지 유형의 파일이 있습니다.재작성 및 변수
포함된 파일의 이름은 다음과 같이 지정해야 합니다.

| 유형 | 파일 이름 포함 |
|-----------|---------------------------------|
| 다시 쓰기 | `conf.d/rewrites/rewrite.rules` |
| 변수 | `conf.d/variables/custom.vars` |

또는 이름이 **있는 재작성 규칙의** 기본 `conf.d/rewrites/default_rewrite.rules`버전을 포함할 수 있습니다.
변수 파일의 기본 버전은 없습니다.

**더 이상 사용되지 않는 구성 레이아웃이 감지되어 호환성 모드를 사용하도록 설정**

이 메시지는 구성에 전체 Apache 구성과 `ams_` 접두사가 있는 파일이 포함된 더 이상 사용되지 않는 버전 1 레이아웃이 있음을 나타냅니다. 이 기능은 여전히 백워드 호환성을 위해 지원되지만 새 레이아웃으로 전환해야 합니다.

## 로컬에서 Apache 및 Dispatcher 구성 테스트 {#testing-apache-and-dispatcher-configuration-locally}

Apache 및 Dispatcher 구성을 로컬로 테스트할 수도 있습니다. Docker를 로컬에 설치하고 위에 설명된 유효성 검사를 통과하려면 구성이 필요합니다.

&quot;`-d`&quot; 매개 변수를 사용하여 유효성 검사기는 디스패처가 필요한 모든 구성 파일과 함께 폴더를 출력합니다.

그런 다음 `docker_run.sh` 스크립트가 해당 폴더를 가리키며, 구성이 포함된 컨테이너를 시작합니다.

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

그러면 백 엔드가 포트 4503의 로컬 Mac OS 시스템에서 실행 중인 AEM 인스턴스를 가리키는 컨테이너에서 디스패처가 시작됩니다.

## Apache 및 Dispatcher 구성 디버깅 {#debugging-apache-and-dispatcher-configuration}

다음 전략을 사용하여 디스패처 모듈의 로그 출력을 늘리고 로컬 및 클라우드 환경 모두에서 `RewriteRule` 평가 결과를 확인할 수 있습니다.

이러한 모듈의 로그 수준은 변수와 `DISP_LOG_LEVEL` 에 의해 정의됩니다 `REWRITE_LOG_LEVEL`. 파일에 설정할 수 `conf.d/variables/global.vars`있습니다. 관련 부분은 다음과 같습니다.

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

Dispatcher를 로컬로 실행할 때 로그가 터미널 출력에 직접 인쇄됩니다. 대부분의 경우 이러한 로그는 DEBUG에 있어야 하며 Docker를 실행할 때 디버그 수준을 매개 변수로 전달하여 수행할 수 있습니다. 예:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

클라우드 환경용 로그는 Cloud Manager에서 사용할 수 있는 로깅 서비스를 통해 노출됩니다.

## 환경당 다른 Dispatcher 구성 {#different-dispatcher-configurations-per-environment}

현재 동일한 디스패처 구성이 클라우드 서비스 환경으로 모든 AEM에 적용됩니다. 런타임에는 현재 실행 모드(dev, stage 또는 prod)와 정의가 `ENVIRONMENT_TYPE` 포함된 환경 변수가 있습니다. 정의는 `ENVIRONMENT_DEV`또는 `ENVIRONMENT_STAGE` 일 수 `ENVIRONMENT_PROD`있습니다. Apache 구성에서 이 변수를 표현식에 직접 사용할 수 있습니다. 또는 정의를 사용하여 논리를 작성할 수 있습니다.

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

Dispatcher 구성에서 동일한 환경 변수를 사용할 수 있습니다. 더 많은 논리가 필요한 경우 위의 예에서 보듯이 변수를 정의한 다음 Dispatcher 구성 섹션에서 사용하십시오.

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

구성을 로컬로 테스트할 때 변수를 스크립트에 직접 전달하여 다양한 환경 유형을 시뮬레이션할 `DISP_RUN_MODE` 수 `docker_run.sh` 있습니다.

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

DISP_RUN_MODE에 대한 값을 전달하지 않을 때의 기본 실행 모드는 &quot;dev&quot;입니다.
사용 가능한 옵션 및 변수의 전체 목록을 보려면 인수 `docker_run.sh` 없이 스크립트를 실행하십시오.

## Docker 컨테이너가 사용 중인 Dispatcher 구성 보기 {#viewing-dispatcher-configuration-in-use-by-docker-container}

환경별 구성을 사용하면 실제 디스패처 구성의 모양을 결정하기가 어려울 수 있습니다. After have started your docker container with `docker_run.sh` it can be disposed as follows:

* 사용 중인 문서 컨테이너 ID 확인:

```
$ docker ps
CONTAINER ID       IMAGE
d75fbd23b29        adobe/aem-ethos/dispatcher-publish:...
```

* 컨테이너 ID로 다음 명령줄을 실행합니다.

```
$ docker exec d75fbd23b29 httpd-test
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
  /publishfarm {
    /clientheaders {
...
```

## 클라우드 서비스로서의 AMS Dispatcher와 AEM의 주요 차이점 {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

위의 참조 페이지에서 설명한 바와 같이 AEM의 클라우드 서비스로 Apache 및 Dispatcher 구성은 AMS 1과 매우 유사합니다. 주요 차이점은 다음과 같습니다.

* AEM에서 클라우드 서비스로 일부 Apache 지시어를 사용할 수 없습니다(예: `Listen` 또는 `LogLevel`).
* AEM에서 클라우드 서비스로, 일부 디스패처 구성만 포함 파일에 포함할 수 있으며 해당 이름의 중요성도 높습니다. 예를 들어 여러 호스트 간에 재사용할 필터 규칙을 호출한 파일에 넣어야 합니다. `filters/filters.any` 자세한 내용은 참조 페이지를 참조하십시오.
* AEM에서 클라우드 서비스로 사용할 경우 보안 문제를 방지하기 위해 를 사용하여 작성된 필터 규칙을 허용하지 `/glob` 않도록 하기 위한 추가 유효성 검사가 있습니다. Dispatcher `deny *` 를 사용하지 않고 사용할 `allow *` 것이기 때문에 고객은 Dispatcher를 로컬에서 실행하여 시험버전 및 오류를 수행하여 Dispatcher 필터가 어떤 경로를 차단한 것인지 정확하게 확인하여 추가할 수 있습니다.

## Cloud Service로서 AMS에서 AEM으로 디스패처 구성을 마이그레이션하는 지침

디스패처 구성 구조는 Managed Services와 클라우드 서비스로서의 AEM이 서로 다릅니다. 아래에 제시된 것은 AMS Dispatcher 구성 버전 2에서 AEM으로 클라우드 서비스로 마이그레이션하는 방법에 대한 단계별 가이드입니다.

## AMS를 클라우드 서비스 디스패처 구성으로 AEM으로 변환하는 방법

다음 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다. Cloud Manager 디스패처 구성에 설명된 구조와 유사한 구조를 갖는 [아카이브가 있는 것으로 가정합니다.](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### 아카이브 추출 및 최종 접두사 제거

아카이브를 하나의 폴더로 추출하고, 바로 아래 하위 폴더가 `conf`, `conf.d``conf.dispatcher.d` 및 `conf.modules.d`로 시작되도록 합니다. 그렇지 않으면 계층 구조에서 위로 이동합니다.

### 사용되지 않은 하위 폴더 및 파일 제거

하위 폴더 `conf` 및 `conf.modules.d`일치하는 파일뿐만 아니라 제거할 수 `conf.d/*.conf`있습니다.

### 게시되지 않은 모든 가상 호스트 제거

가상 호스트 파일의 이름을 `conf.d/enabled_vhosts``author`, `unhealthy``health`또는`lc` 가상 호스트 `flush` 파일에서 제거합니다. 연결되지 않은 `conf.d/available_vhosts` 모든 가상 호스트 파일도 제거할 수 있습니다.

### 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 추가

여전히 가상 호스트 파일에 포트 80 이외의 다른 포트를 참조하는 섹션이 있는 경우(예:

```
<VirtualHost *:443>
...
</VirtualHost>
```

제거 또는 주석 달기 이러한 섹션의 명령문은 처리되지 않지만, 이 명령문을 계속 유지하면 아무 효과도 없이 편집할 수 있으므로 혼동됩니다.

### 재작성 확인

Enter directory `conf.d/rewrites`.

이름을 `base_rewrite.rules` 지정하고 `xforwarded_forcessl_rewrite.rules` `Include` 이름을 참조하는 가상 호스트 파일에서 명령문을 다시 이동시키는 것을 기억하십시오.

이제 `conf.d/rewrites` 단일 파일이 들어 있는 경우 이름을 가상 호스트 파일에서 해당 파일을 참조하는 `rewrite.rules` `Include` 문을 수정해야 합니다.

그러나 폴더에 여러 개의 가상 호스트 특정 파일이 들어 있는 경우 가상 호스트 파일에서 해당 파일을 참조하는 `Include` 문에 해당 콘텐트가 추가됩니다.

### 변수 확인

Enter directory `conf.d/variables`.

이름이 지정된 파일을 `ams_default.vars` 제거하고 가상 호스트 파일에서 해당 파일을 참조하는 `Include` 문을 제거해야 합니다.

이제 `conf.d/variables` 단일 파일이 들어 있는 경우 이름을 가상 호스트 파일에서 해당 파일을 참조하는 `custom.vars` `Include` 문을 수정해야 합니다.

그러나 폴더에 여러 개의 가상 호스트 특정 파일이 들어 있는 경우 가상 호스트 파일에서 해당 파일을 참조하는 `Include` 문에 해당 콘텐트가 추가됩니다.

### 화이트 리스트 제거

폴더를 `conf.d/whitelists` 제거하고 가상 호스트 파일에서 해당 하위 폴더의 일부 파일을 참조하는 `Include` 문을 제거합니다.

### 더 이상 사용할 수 없는 모든 변수 바꾸기

모든 가상 호스트 파일에서:

이름을 `PUBLISH_DOCROOT` 다음으로 `DOCROOT``DISP_ID``PUBLISH_FORCE_SSL` 바꾸기또는 `PUBLISH_WHITELIST_ENABLED`

### 유효성 검사기를 실행하여 상태 확인

다음 하위 명령을 사용하여 디렉토리에서 `httpd` 검사기를 실행합니다.

```
$ validator httpd .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인하십시오.

화이트리스트에 포함되지 않은 Apache 지시문이 표시되면 제거합니다.

### 게시되지 않은 모든 팜 제거

이름이 `conf.dispatcher.d/enabled_farms``author`, `unhealthy``health`또는 이름이 있는 팜 파일을`lc` 제거합니다 `flush` . 연결되지 않은 팜 파일도 `conf.dispatcher.d/available_farms` 모두 제거할 수 있습니다.

### 팜 파일 이름 변경

의 모든 팜은 패턴과 일치하도록 이름을 `conf.d/enabled_farms` 변경해야 `*.farm`합니다. 따라서 호출된 Afarm 파일의 이름을 변경해야 `customerX_farm.any` 합니다 `customerX.farm`.

### 캐시 확인

Enter directory `conf.dispatcher.d/cache`.

사전 수정된 파일을 제거합니다 `ams_`.

이제 `conf.dispatcher.d/cache` 비어 있으면 표준 발송자 `conf.dispatcher.d/cache/rules.any`구성에서 이 폴더로 파일을 복사합니다. 표준 디스패처 구성은 이 SDK 폴더에 `src` 있습니다. 팜 파일에서도`$include` 규칙 파일을 참조하는 문을 `ams_*_cache.any` 수정해야 합니다.

대신 `conf.dispatcher.d/cache` 이제 접미어가 붙은 단일 파일이 `_cache.any`포함된 경우 이름이 다음으로 변경되어야 `rules.any` 하며 팜 파일에서도 해당 파일을 참조하는 `$include` 문을 수정해야 합니다.

그러나 폴더에 해당 패턴이 있는 팜 특정 파일이 여러 개 포함되어 있는 경우 해당 컨텐츠를 팜 파일에서 해당 파일을 참조하는 `$include` 문으로 복사해야 합니다.

접미어가 붙은 파일을 `_invalidate_allowed.any`제거합니다.

Cloud 디스패처 구성의 기본 AEM `conf.dispatcher.d/cache/default_invalidate_any` 에서 해당 위치로 파일을 복사합니다.

각 팜 파일에서 `cache/allowedClients` 섹션의 내용을 제거하고 다음으로 바꿉니다.

```
$include "../cache/default_invalidate.any"
```

### 클라이언트 헤더 확인

Enter directory `conf.dispatcher.d/clientheaders`.

사전 수정된 파일을 제거합니다 `ams_`.

이제 `conf.dispatcher.d/clientheaders` 접미어가 붙은 단일 파일이 `_clientheaders.any`포함된 경우 이름이 로 변경되어야 `clientheaders.any` 하며 팜 파일에서도 해당 파일을 참조하는 `$include` 문을 수정해야 합니다.

그러나 폴더에 해당 패턴이 있는 팜 특정 파일이 여러 개 포함되어 있는 경우 해당 컨텐츠를 팜 파일에서 해당 파일을 참조하는 `$include` 문으로 복사해야 합니다.

기본 AEM `conf.dispatcher/clientheaders/default_clientheaders.any` 에서 클라우드 서비스 디스패처 구성으로 해당 위치로 파일을 복사합니다.

각 팜 파일에서 모든 클립헤더에는 다음과 같이 보이는 문이 포함됩니다.

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

with the statement:

```
$include "../clientheaders/default_clientheaders.any"
```

### 필터 확인

Enter directory `conf.dispatcher.d/filters`.

사전 수정된 파일을 제거합니다 `ams_`.

이제 `conf.dispatcher.d/filters` 하나의 파일이 포함된 경우 이름을 로`filters.any` 변경해야 하며 팜 파일에서 해당 파일을 참조하는 `$include` 문을 수정해야 합니다.

그러나 폴더에 해당 패턴이 있는 팜 특정 파일이 여러 개 포함되어 있는 경우 해당 컨텐츠를 팜 파일에서 해당 파일을 참조하는 `$include` 문으로 복사해야 합니다.

기본 AEM `conf.dispatcher/filters/default_filters.any` 에서 클라우드 서비스 디스패처 구성으로 해당 위치로 파일을 복사합니다.

각 팜 파일에서 필터를 바꾸면 다음과 같이 보이는 문이 포함됩니다.

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

with the statement:

```
$include "../filters/default_filters.any"
```

### 렌더링 확인

Enter directory `conf.dispatcher.d/renders`.

해당 폴더의 모든 파일을 제거합니다.

기본 AEM `conf.dispatcher.d/renders/default_renders.any` 에서 클라우드 서비스 디스패처 구성으로 해당 위치로 파일을 복사합니다.

각 팜 파일에서 `renders` 섹션의 내용을 제거하고 다음으로 바꿉니다.

```
$include "../renders/default_renders.any"
```

### 가상 호스트 확인

디렉토리 이름을 `conf.dispatcher.d/vhosts` 변경하여 `conf.dispatcher.d/virtualhosts` 입력합니다.

사전 수정된 파일을 제거합니다 `ams_`.

이제 `conf.dispatcher.d/virtualhosts` 하나의 파일이 포함된 경우 이름을 로`virtualhosts.any` 변경해야 하며 팜 파일에서 해당 파일을 참조하는 `$include` 문을 수정해야 합니다.

그러나 폴더에 해당 패턴이 있는 팜 특정 파일이 여러 개 포함되어 있는 경우 해당 컨텐츠를 팜 파일에서 해당 파일을 참조하는 `$include` 문으로 복사해야 합니다.

기본 AEM `conf.dispatcher/virtualhosts/default_virtualhosts.any` 에서 클라우드 서비스 디스패처 구성으로 해당 위치로 파일을 복사합니다.

각 팜 파일에서 필터를 바꾸면 다음과 같이 보이는 문이 포함됩니다.

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

with the statement:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### 유효성 검사기를 실행하여 상태 확인

하위 명령을 사용하여 AEM을 디렉터리에서 클라우드 서비스 디스패처 유효성 검사기로 `dispatcher` 실행합니다.

```
$ validator dispatcher .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인하십시오.

정의되지 않은 변수와 관련된 오류가 표시되면 `PUBLISH_DOCROOT`이름을 `DOCROOT`로 변경합니다.

다른 모든 오류에 대해서는 유효성 검사기 도구 설명서의 문제 해결 섹션을 참조하십시오.

### 로컬 배포로 구성 테스트(Docker 설치 필요)

AEM의 스크립트를 `docker_run.sh` 클라우드 서비스 디스패처 도구로 사용하여 구성에 배포에만 표시되는 다른 오류가 없는지 테스트할 수 있습니다.

### 1단계:유효성 검사기를 사용하여 배포 정보 생성

```
validator full -d out .
```

이렇게 하면 전체 구성을 검증하고 `out`

### 2단계:해당 배포 정보를 사용하여 문서 이미지에서 디스패처 시작

macOS 컴퓨터에서 AEM 게시 서버를 실행하고 포트 4503에서 수신 대기하면 다음과 같이 해당 서버 앞에서 디스패처를 시작할 수 있습니다.

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

이렇게 하면 컨테이너가 시작되고 로컬 포트 8080에 Apache가 표시됩니다.

### 새 디스패처 구성 사용

축하합니다! 유효성 검사기가 더 이상 문제를 보고하지 않고 도커 컨테이너가 아무런 오류나 경고 없이 시작하는 경우 구성을 git 저장소의 `dispatcher/src` 하위 디렉터리로 다시 이동할 수 있습니다.

**AMS Dispatcher 구성 버전 1을 사용하는 고객은 위의 지침을 따를 수 있도록 고객 지원에 문의하여 버전 1에서 버전 2로 마이그레이션할 수 있도록 지원해야 합니다.**

## 발송자 및 CDN {#dispatcher-cdn}

게시 서비스 컨텐츠 전달에는 다음이 포함됩니다.

* CDN(일반적으로 Adobe에서 관리)
* AEM 디스패처
* AEM 게시

데이터 흐름은 다음과 같습니다.

1. 브라우저에 URL이 추가됩니다.
1. DNS에 매핑된 CDN에 대한 요청
1. 컨텐츠가 CDN에 완전히 캐시되는 경우 CDN은 브라우저에 컨텐츠를 제공합니다
1. 컨텐츠가 완전히 캐시되지 않으면 CDN은 디스패처에 대해 콜아웃(역방향 프록시)합니다
1. 컨텐츠가 디스패처에 완전히 캐시되는 경우 디스패처는 이를 CDN에 제공합니다
1. 컨텐츠가 완전히 캐시되지 않으면 디스패처는 AEM 게시로 아웃(역방향 프록시)을 호출합니다
1. 컨텐츠는 브라우저에 의해 렌더링되며, 이것은 헤더에 따라 캐시될 수도 있습니다

대부분의 컨텐츠는 디스패처 캐시와 CDN이 모두 존중하는 임계값인 5분 후 만료되도록 설정됩니다. 게시 서비스를 다시 배포하는 동안 디스패처 캐시가 지워지고 이후에 새 게시 노드가 트래픽을 승인하기 전에 다시 데워집니다.

아래 섹션에서는 CDN 구성 및 디스패처 캐싱을 비롯한 컨텐츠 전달에 대해 자세히 설명합니다.

작성자 서비스에서 게시 서비스로의 복제에 대한 정보는 [여기에서](/help/operations/replication.md)확인할 수 있습니다.

>[!NOTE]
>트래픽은 Apache 웹 서버를 통과하며, 이 서버는 디스패처를 포함한 모듈을 지원합니다. 디스패처는 주로 성능을 향상시키기 위해 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.

### CDN {#cdn}

AEM에서는 다음 세 가지 옵션을 제공합니다.

1. Adobe Managed CDN - AEM의 기본 CDN 이 옵션은 완전히 통합되어 있으므로 권장됩니다.
1. 고객 관리 CDN - 고객은 고유한 CDN을 가져오며, 이를 전적으로 관리합니다.
1. Adobe Managed CDN을 가리킵니다. 고객은 AEM의 기본 CDN을 가리킵니다.

>[!CAUTION]
>첫 번째 옵션은 매우 권장합니다. 두 번째 옵션을 선택하면 Adobe는 잘못된 구성의 결과에 대한 책임을 지지 않습니다.

두 번째 및 세 번째 옵션은 사례별로 사용할 수 있습니다. 여기에는 실행 취소가 어려운 기존 CDN 벤더와의 통합을 비롯하여 특정 사전 요구 사항을 충족해야 합니다.

#### Adobe Managed CDN {#adobe-managed-cdn}

Adobe의 기본 CDN을 사용하여 컨텐츠 전달을 준비하는 방법은 아래에 설명된 바와 같이 간단합니다.

1. 이 정보가 들어 있는 보안 양식에 대한 링크를 공유하여 서명된 SSL 인증서 및 비밀 키를 Adobe에 제공합니다. 이 작업에 대한 고객 지원 팀과 협력하십시오.
참고:클라우드 서비스로 제공되는 AEM은 DV(Domain Validated) 인증서를 지원하지 않습니다.
1. 그러면 고객 지원에서 FQDN을 가리키는 CNAME DNS 레코드의 타이밍을 `adobe-aem.map.fastly.net`조정합니다.
1. SSL 인증서가 만료되면 알림을 받게 되므로 새 SSL 인증서를 다시 제출할 수 있습니다.

기본적으로 Adobe Managed CDN 설정의 경우 모든 공개 트래픽이 프로덕션 및 비프로덕션(개발 및 스테이지) 환경 모두에 대해 게시 서비스로 이동할 수 있습니다. 지정된 환경에 대한 게시 서비스로 트래픽을 제한하려면(예: IP 주소 범위에 따라 스테이징을 제한) 고객 지원 센터에서 이러한 제한을 구성해야 합니다.

#### 고객 관리 CDN {#customer-managed-cdn}

제공된 고유한 CDN을 관리할 수 있습니다.

1. 기존 CDN이 있습니다.
1. 지원되는 CDN이어야 합니다. 현재 Akamai가 지원됩니다. 조직에서 현재 지원되지 않는 CDN을 관리하려면 고객 지원에 문의하십시오.
1. 관리
1. Aem에서 클라우드 서비스로 작동하도록 CDN을 구성할 수 있어야 합니다. 아래 구성 지침을 참조하십시오.
1. 관련 문제가 발생할 경우 대기 중인 엔지니어링 CDN 전문가가 있습니다.
1. 구성 지침에 설명된 대로 CDN 노드의 화이트 리스트를 Cloud Manager에 제공해야 합니다.
1. 프로덕션으로 전환하기 전에 로드 테스트를 성공적으로 수행하고 통과해야 합니다.

구성 지침:

1. 환경 만들기/업데이트 API를 화이트리스트에 추가할 CIDR 목록과 함께 호출하여 CDN 벤더의 화이트 리스트를 Adobe에 제공합니다.
1. 도메인 이름으로 `X-Forwarded-Host` 헤더를 설정합니다.
1. Aem을 클라우드 서비스 수신 클라이언트로 원본 도메인으로 호스트 헤더를 설정합니다. 값은 Adobe에서 가져옵니다.
1. SNI 헤더를 원본으로 보냅니다. SNI 헤더는 원본 도메인이어야 합니다.
1. 트래픽을 AEM 서버로 올바르게 라우팅하는 데 필요한 `X-Edge-Key` 항목을 설정합니다. 값은 Adobe에서 가져옵니다.

라이브 트래픽을 수락하기 전에 엔드 투 엔드 트래픽 라우팅이 제대로 작동하는지 Adobe 고객 지원으로 확인해야 합니다.

#### Adobe Managed CDN {#point-to-point-CDN}

기존 CDN을 사용하지만 고객 관리 CDN의 요구 사항을 충족할 수 없는 경우에 지원됩니다. 이 경우 자체 CDN을 관리하지만 Adobe의 관리 CDN을 가리킵니다.

고객은 프로덕션으로 가기 전에 로드 테스트를 성공적으로 수행하고 통과해야 합니다.

구성 지침:

1. 도메인 이름으로 `X-Forwarded-Host` 헤더를 설정합니다.
1. Adobe의 CDN의 수신 주소인 원본 도메인으로 호스트 헤더를 설정합니다. 값은 Adobe에서 가져옵니다.
1. SNI 헤더를 원본으로 보냅니다. 호스트 헤더와 마찬가지로 sni 헤더는 원본 도메인이어야 합니다.
1. 트래픽을 AEM 서버로 올바르게 라우팅하는 데 필요한 `X-Edge-Key`를 설정합니다. 값은 Adobe에서 가져옵니다.

#### CDN 캐시 무효화 {#CDN-cache-invalidation}

캐시 무효화는 다음과 같은 규칙을 따릅니다.

* 일반적으로 HTML 컨텐츠는 디스패처가 방출하는 캐시 제어 헤더를 기반으로 하여 CDN에서 5분 동안 캐시됩니다.
* 클라이언트 라이브러리(JavaScript 및 CSS)는 변경할 수 없는 값을 준수하지 않는 오래된 브라우저에 대해 캐시 제어 설정을 사용하여 30일 동안 무기한 캐시됩니다. 클라이언트 라이브러리는 클라이언트 라이브러리가 변경되면 변경되는 고유한 경로에서 제공됩니다. 즉, 클라이언트 라이브러리를 참조하는 HTML이 필요에 따라 생성되므로 새 컨텐츠를 게시한 즉시 경험할 수 있습니다.
* 기본적으로 이미지는 캐시되지 않습니다.

라이브 트래픽을 수락하기 전에 고객은 엔드 투 엔드 트래픽 라우팅이 제대로 작동하는지 Adobe 고객 지원으로 확인해야 합니다.

## 명시적 디스패처 캐시 무효화 {#explicit-invalidation}

앞에서 설명한 바와 같이, 트래픽은 Apache 웹 서버를 통과하며, 이 서버는 디스패처를 포함한 모듈을 지원합니다. 디스패처는 주로 성능을 향상시키기 위해 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.

일반적으로 디스패처의 컨텐츠를 수동으로 무효화할 필요는 없지만 필요에 따라 아래에 설명된 대로 무효화할 수 있습니다.

AEM을 클라우드 서비스로 사용하기 전에는 디스패처 캐시를 무효화하는 두 가지 방법이 있었습니다.

1. 게시 디스패처 플러시 에이전트를 지정하여 복제 에이전트를 호출합니다.
2. API를 직접 `invalidate.cache` 호출(예: POST /dispatcher/invalidate.cache)

이 `invalidate.cache` 방법은 특정 디스패처 노드만 해결하므로 더 이상 지원되지 않습니다.
클라우드 서비스로서의 AEM은 개별 노드 수준이 아니라 서비스 수준에서 작동하므로 Dispatcher 도움말 [설명서의](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html) 무효화 지침이 더 이상 정확하지 않습니다.
대신 복제 플러시 에이전트를 사용해야 합니다. 이 작업은 복제 API를 사용하여 수행할 수 있습니다. Replication API 설명서는 [여기에서](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) 사용할 수 있으며 캐시 플러시의 예는 API [예제 페이지](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) , 특히 사용 가능한 모든 에이전트에 대해 ACTIVATE 유형의 복제 작업을 발급하는 `CustomStep` 예 등을 참조하십시오. 플러시 에이전트 종단점은 구성할 수 없지만 발송자를 가리키도록 미리 구성되었으며 플러시 에이전트를 실행하는 게시 서비스와 일치합니다. 일반적으로 플러시 에이전트는 OSGi 이벤트 또는 워크플로우에 의해 트리거될 수 있습니다.

아래 다이어그램은 이를 보여줍니다.

![](assets/cdn.png "CDNCDN")

디스패처 캐시가 지워지지 않을 우려가 있는 경우 필요한 경우 디스패처 캐시를 플러시할 수 있는 고객 지원에 문의하십시오.

Adobe 관리 CDN은 TTL을 준수하므로 플러시할 필요가 없습니다. 문제가 의심되는 경우 필요에 따라 Adobe 관리 CDN 캐시를 플러시할 수 있는 고객 지원에 문의하십시오.

### 활성화/비활성화 중 Dispatcher 캐시 무효화 {#cache-activation-deactivation}

이전 버전의 AEM과 마찬가지로 페이지를 게시 또는 게시 취소하면 디스패처 캐시에서 콘텐츠가 지워집니다. 캐싱 문제가 의심되는 경우 고객은 해당 페이지를 다시 게시해야 합니다.

게시 인스턴스가 작성자로부터 페이지 또는 자산의 새 버전을 받으면 플러시 에이전트를 사용하여 디스패처의 적절한 경로를 무효화합니다. 업데이트된 경로가 해당 부모와 함께 디스패처 캐시에서 최대 수준에서 제거됩니다( [상태 파일 수준으로](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)구성 가능).

### 최신 컨텐츠 및 버전 일관성 {#content-consistency}

* 페이지는 HTML, Javascript, CSS 및 이미지로 구성됩니다.
* JS 라이브러리 간의 종속성을 고려하여 Clientlibs 프레임워크를 활용하여 Javascript 및 CSS 리소스를 HTML 페이지로 가져오는 것이 좋습니다.
* 자동 버전 관리가 제공되므로 개발자는 소스 제어에서 JS 라이브러리의 변경 내용을 체크 인할 수 있으며 릴리스가 푸시될 때 최신 버전을 사용할 수 있습니다. 이렇게 하지 않으면 개발자는 새 버전의 라이브러리를 참조하는 HTML을 수동으로 변경해야 합니다. 이는 많은 HTML 템플릿이 동일한 라이브러리를 공유하는 경우에 특히 유용합니다.
* 새로운 버전의 라이브러리가 프로덕션에 릴리스되면 참조하는 HTML 페이지가 업데이트된 라이브러리 버전에 대한 새 링크로 업데이트됩니다. 주어진 HTML 페이지에 대한 브라우저 캐시가 만료되면 새로 고쳐진 페이지(AEM에서)가 이제 새 버전의 라이브러리를 참조할 수 있으므로 이전 라이브러리가 브라우저 캐시에서 로드될 우려가 없습니다. 즉, 새로 고쳐진 HTML 페이지에는 모든 최신 라이브러리 버전이 포함됩니다.
