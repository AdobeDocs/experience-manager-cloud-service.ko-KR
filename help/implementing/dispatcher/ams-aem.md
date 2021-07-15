---
title: Dispatcher 구성을 AMS에서 AEM as a Cloud Service으로 마이그레이션
description: 'Dispatcher 구성을 AMS에서 AEM as a Cloud Service으로 마이그레이션 '
feature: Dispatcher
source-git-commit: 19444aacbb86f93e7a5ea8bda2ca3c03a0a44f98
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 14%

---

# Dispatcher 구성을 AMS에서 AEM as a Cloud Service으로 마이그레이션 {#Dispatcher-in-the-cloud}

## AMS Dispatcher와 AEM as a Cloud Service의 주요 차이점 {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

AEM as a Cloud Service의 Apache 및 Dispatcher 구성은 AMS 구성과 매우 유사합니다. 주요 차이점은 다음과 같습니다.

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

### 1단계: 유효성 검사기를 사용하여 배포 정보 생성

```
validator full -d out .
```

전체 구성을 확인하고 `out`에 배포 정보를 생성합니다.

### 2단계: 해당 배포 정보를 사용하여 Docker 이미지에서 Dispatcher 시작

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
