---
title: 클라우드의 Dispatcher
description: Dispatcher 도구, 지원되는 Apache 모듈, 레거시 및 유연한 모드에 대해 알아봅니다.
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
source-git-commit: 127b79d766a4dfc33a2ed6016e191e771206d791
workflow-type: ht
source-wordcount: '993'
ht-degree: 100%

---

# 클라우드의 Dispatcher {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="클라우드의 Dispatcher"
>abstract="이 페이지에서는 지원되는 Apache 모듈인 Dispatcher 도구를 다운로드하고 추출하는 방법을 설명하고 레거시 모드와 유연한 모드에 대한 높은 수준의 개요를 제공합니다."

## 소개 {#apache-and-dispatcher-configuration-and-testing}

이 페이지에서는 Dispatcher 도구를 다운로드하고 추출하는 방법을 설명하고 지원되는 Apache 모듈과 레거시 모드 및 유연한 모드에 대한 높은 수준의 개요를 제공합니다. 또한 유효성 검사 및 디버깅과 AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션에 대한 추가 참조가 있습니다. <!-- ERROR: NOT FOUND (HTTP ERROR 404) Also, see [this video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-dispatcher-cloud.html) for additional details about deploying dispatcher files in a cloud service environment. -->

## Dispatcher 도구 {#dispatcher-sdk}

Dispatcher 도구는 전체 AEM as a Cloud Service SDK의 일부이며 다음을 제공합니다.

* Dispatcher용 Maven 프로젝트에 포함될 구성 파일이 있는 바닐라 파일 구조입니다.
* 도구를 사용하여 고객은 Dispatcher 구성에 AEM as a Cloud Service 지원 지시문만 있는지 확인합니다. 또한 도구를 사용하여 Apache의 성공적인 시작을 위해 구문이 올바른지 확인합니다.
* 로컬로 Dispatcher를 호출하는 도커 이미지입니다.

## 도구 다운로드 및 추출 {#extracting-the-sdk}

[소프트웨어 배포](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) 포털의 zip 파일에서 [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)의 일부인 Dispatcher 도구를 다운로드할 수 있습니다. 새 Dispatcher 도구 버전에 사용 가능한 새 구성을 사용하여 클라우드에서 해당 버전의 AEM 이상을 실행 중인 클라우드 환경에 배포할 수 있습니다.

macOS, Linux® 및 Windows용 Dispatcher 도구를 번들로 제공하는 SDK의 압축을 풉니다.

**macOS/Linux**&#x200B;의 경우 실행 가능한 Dispatcher 도구 아티팩트를 만들어 실행합니다. 파일을 저장한 디렉터리에서 Dispatcher Tools 파일이 자동으로 압축 해제됩니다(여기서 `version`은 Dispatcher 도구 버전임).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Windows**&#x200B;의 경우 Dispatcher 도구 zip 아카이브를 추출합니다.

## Dispatcher 도구를 사용하여 확인 및 디버깅 {#validation-debug}

Dispatcher 도구를 사용하여 프로젝트의 Dispatcher 구성을 확인하고 디버그합니다. 프로젝트의 Dispatcher 구성이 유연한 모드 또는 레거시 모드로 구조화되어 있는지 여부에 따라 아래 참조 페이지에서 해당 도구를 사용하는 방법에 대해 자세히 알아봅니다.

* **유연한 모드** - 권장 모드이면서 [AEM Archetype 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ko) 이상에 대한 기본값으로 Cloud Manager 2021.7.0 릴리스 이후에 생성된 새 환경의 Cloud Manager에서도 사용됩니다. 고객은 폴더와 파일을 추가하여 이 모드를 활성화할 수 있습니다`opt-in/USE_SOURCES_DIRECTLY`. 보다 유연한 이 모드를 사용하게 되면 레거시 모드에서 단일 `rewrite.rules` 파일이 필수였던 rewrites 폴더의 파일 구조에는 제한 사항이 없습니다. 또한 추가할 수 있는 규칙 수에는 제한 사항이 없습니다. 폴더 구조 및 로컬 유효성 확인에 대한 자세한 내용은 [Dispatcher 도구를 사용하여 확인 및 디버깅](/help/implementing/dispatcher/validation-debug.md)을 참조하십시오.

* **레거시 모드** - Dispatcher 구성 레거시 모드의 폴더 구조 및 로컬 유효성 확인에 대한 자세한 내용은 [Dispatcher 도구를 사용하여 확인 및 디버깅(레거시)](/help/implementing/dispatcher/validation-debug-legacy.md)을 참조하십시오.

레거시 구성 모델에서 AEM Archetype 28 이상과 함께 제공되는 보다 유연한 모델로 마이그레이션하는 방법에 대한 자세한 내용은 [이 설명서](/help/implementing/dispatcher/validation-debug.md#migrating)를 참조하십시오.

## 콘텐츠 배치 {#content-disposition}

게시 계층의 경우 Blob를 제공하는 기본값은 첨부 파일로 제공됩니다. Dispatcher의 표준 [콘텐츠 배치 헤더](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Disposition)를 사용하여 이 설정을 재정의합니다.

다음은 구성 형태의 예제입니다.

```
<LocationMatch "^\/content\/dam.*\.(pdf).*">
 Header unset Content-Disposition
 Header set Content-Disposition inline
</LocationMatch>
```

## 지원되는 Apache 모듈 {#supported-directives}

아래 표는 지원되는 Apache 모듈을 보여 줍니다.

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
| `mod_macro` | [https://httpd.apache.org/docs/2.4/mod/mod_macro.html](https://httpd.apache.org/docs/2.4/mod/mod_macro.html) |
| `mod_include (no directives supported)` | [https://httpd.apache.org/docs/2.4/mod/mod_include.html](https://httpd.apache.org/docs/2.4/mod/mod_include.html) |


고객은 임의의 모듈을 추가할 수 없지만 추가 모듈을 포함 대상으로 고려할 수 있습니다. 고객은 SDK에서 검사기의 허용 목록 명령을 실행하여 지정된 Dispatcher 버전에 사용 가능한 지시문 목록을 찾을 수 있습니다.

검사기의 허용 목록 명령을 실행하여 Apache 구성 파일에 허용된 지시문을 나열할 수 있습니다.

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

## 폴더 구조 {#folder-structure}

프로젝트의 Apache 및 Dispatcher 폴더 구조는 위의 [Dispatcher 도구를 사용하여 확인 및 디버깅](#validation-debug) 섹션에 설명된 대로 프로젝트가 사용 중인 모드에 따라 약간 다릅니다.

## AMS에서 Dispatcher 구성 마이그레이션 {#ams-aem}

AMS의 Dispatcher 구성을 AEM as a Cloud Service로 마이그레이션하는 방법에 대한 자세한 내용은 AMS에서 [AEM as a Cloud Service로 Dispatcher 구성 마이그레이션](/help/implementing/dispatcher/ams-aem.md) 페이지를 참조하십시오.
