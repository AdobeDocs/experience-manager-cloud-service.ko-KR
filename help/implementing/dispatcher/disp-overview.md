---
title: 클라우드의 디스패처
description: '클라우드의 디스패처 '
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 2%

---

# 클라우드의 디스패처 {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="클라우드의 디스패처"
>abstract="이 페이지에서는 지원되는 Apache 모듈인 디스패처 도구를 다운로드하고 추출하는 방법에 대해 설명하고 기존 및 유연한 모드에 대한 높은 수준의 개요를 제공합니다."

## 소개 {#apache-and-dispatcher-configuration-and-testing}

이 페이지에서는 디스패처 도구 및 디스패처 도구를 다운로드하고 추출하는 방법에 대해 설명하고 지원되는 Apache 모듈과 기존 및 유연한 모드에 대한 높은 수준의 개요를 제공합니다. 또한 유효성 검사 및 디버깅 및 Dispatcher 구성을 AMS에서 AEM으로 Cloud Service으로 마이그레이션하는 것에 대한 추가 참조가 있습니다

## Dispatcher 도구 {#dispatcher-sdk}

Dispatcher 도구는 전체 AEM as a Cloud Service SDK에 포함되어 있으며 다음을 제공합니다.

* Dispatcher용 maven 프로젝트에 포함할 구성 파일이 포함된 vanilla 파일 구조입니다.
* 고객이 Dispatcher 구성에 Cloud Service 지원 지시어로 AEM만 포함되는지 확인할 수 있도록 툴을 제공합니다.        또한 도구에서 구문이 올바른지 확인하여 apache가 성공적으로 시작될 수 있습니다.
* 로컬에서 Dispatcher를 표시하는 Docker 이미지입니다.

## 도구 다운로드 및 추출 {#extracting-the-sdk}

[AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)에 포함된 Dispatcher 도구는 [소프트웨어 배포](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) 포털의 zip 파일에서 다운로드할 수 있습니다. 이 새 Dispatcher 도구 버전에서 사용할 수 있는 모든 새 구성을 사용하여 클라우드 이상에서 해당 AEM 버전을 실행하는 클라우드 환경에 배포할 수 있습니다.

macOS, Linux 및 Windows용 Dispatcher 도구를 번들로 제공하는 SDK의 압축을 해제합니다.

**macOS/Linux**&#x200B;의 경우 Dispatcher 도구를 실행 가능으로 만들고 실행합니다. 저장한 디렉토리 아래에 Dispatcher 도구 파일을 자동으로 추출합니다(여기서 `version`은 Dispatcher 도구의 버전입니다.).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Windows**&#x200B;의 경우 Dispatcher 도구 zip 아카이브를 추출합니다.

## Dispatcher 도구를 사용한 유효성 검사 및 디버깅 {#validation-debug}

디스패처 도구는 프로젝트의 Dispatcher 구성을 확인하고 디버깅하는 데 사용됩니다. 프로젝트의 Dispatcher 구성이 유연한 모드에서 구성되어 있는지 아니면 레거시 모드로 구성되어 있는지에 따라 아래 참조 페이지에서 이러한 도구를 사용하는 방법에 대해 자세히 알아보십시오.

* **유연한 모드**  - 권장 모드 및  [AEM Archetype 28 이상](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) 에 대한 기본값. 이 모드는 Cloud Manager 2021.7.0 릴리스 후에 생성된 새 환경에도 사용됩니다. 고객은 폴더 및 파일 `opt-in/USE_SOURCES_DIRECTLY`을 추가하여 이 모드를 활성화할 수 있습니다. 이 보다 유연한 모드를 사용하면 기존 모드에서 단일 `rewrite.rules` 파일이 필요한 rewrites 폴더 아래에 파일 구조에 제한이 없습니다. 또한 추가할 수 있는 규칙 수에는 제한이 없습니다. 폴더 구조 및 로컬 유효성 검사에 대한 자세한 내용은 [Dispatcher 도구를 사용하여 유효성 검사 및 디버깅](/help/implementing/dispatcher/validation-debug.md)을 참조하십시오.

* **레거시 모드**  - Dispatcher 구성 레거시 모드에 대한 폴더 구조 및 로컬 유효성 검사에 대한 자세한 내용은 Dispatcher 도구 [를 사용하여 확인 및 디버깅(기존)을 참조하십시오](/help/implementing/dispatcher/validation-debug-legacy.md)

AEM Archetype 28 이상에서 제공되는 레거시 구성 모델에서 보다 유연한 구성 모델로 마이그레이션하는 방법에 대한 자세한 내용은 [이 설명서](/help/implementing/dispatcher/validation-debug.md#migrating)을 참조하십시오.

## 지원되는 Apache 모듈 {#supported-directives}

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
| `mod_ssl (only the SSLProxyEngine directive)` | [https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

고객은 임의의 모듈을 추가할 수 없지만, 추가 모듈은 나중에 포함할 수 있습니다. 고객은 SDK에서 유효성 검사기의 명령을 실행하여 주어진 Dispatcher 버전에 사용할 수 있는 허용 목록에 추가하다 지시어 목록을 찾을 수 있습니다.

유효성 검사기의 허용 목록에 추가하다 명령을 실행하여 Apache 구성 파일에서 허용되는 지시문을 나열할 수 있습니다.

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

## 폴더 구조 {#folder-structure}

위의 Dispatcher 도구](#validation-debug) 섹션을 사용하여 유효성 검사 및 디버깅에 설명된 대로 프로젝트의 Apache 및 Dispatcher 폴더 구조는 프로젝트가 사용 중인 모드에 따라 약간 다릅니다.[

## AMS에서 Dispatcher 구성 마이그레이션 {#ams-aem}

Dispatcher 구성을 AMS에서 AEM으로 Cloud Service으로 마이그레이션하는 방법에 대한 자세한 내용은 [AMS에서 AEM](/help/implementing/dispatcher/ams-aem.md)로 Dispatcher 구성 마이그레이션 페이지를 참조하십시오.
