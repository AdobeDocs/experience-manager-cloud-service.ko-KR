---
title: AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션
description: AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션
feature: Dispatcher
exl-id: ff7397dd-b6e1-4d08-8e2d-d613af6b81b3
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1459'
ht-degree: 7%

---

# AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션 {#Dispatcher-in-the-cloud}

## AMS Dispatcher와 AEM as a Cloud Service 간의 주요 차이점 {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

AEM as a Cloud Service의 Apache 및 Dispatcher 구성은 AMS 구성과 매우 유사합니다. 주요 차이점은 다음과 같습니다.

* AEM as a Cloud Service에서는 일부 Apache 지시문이 사용되지 않을 수 있습니다(예: `Listen` 또는 `LogLevel`)
* AEM as a Cloud Service에서는 일부 Dispatcher 구성만 include 파일에 넣을 수 있으며 해당 이름이 중요합니다. 예를 들어 다른 호스트에서 재사용하려는 필터 규칙은 이라는 파일에 넣어야 합니다. `filters/filters.any`. 자세한 내용은 참조 페이지 를 참조하십시오.
* AEM as a Cloud Service에는 다음을 사용하여 작성된 필터 규칙을 허용하지 않도록 하는 추가 유효성 검사가 있습니다. `/glob` 보안 문제를 방지합니다. 이유 `deny *` 이(가) 대신 사용됨 `allow *` (사용할 수 없음) 고객은 로컬에서 Dispatcher를 실행하고 시행착오를 수행하며, 로그를 확인하여 Dispatcher 필터가 차단할 경로를 정확히 파악하여 추가할 수 있는 이점을 얻을 수 있습니다.

## AMS에서 AEM as a Cloud Service으로 Dispatcher 구성을 마이그레이션하기 위한 지침

Dispatcher 구성 구조에는 Managed ServicesAEM 와 as a Cloud Service 간에 차이가 있습니다. 아래에 제시된 는 AMS Dispatcher 구성 버전 2에서 AEM as a Cloud Service으로 마이그레이션하는 방법에 대한 단계별 안내서입니다.

## AMS를 AEM as a Cloud Service Dispatcher 구성으로 변환하는 방법

다음 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다. 에 설명된 것과 유사한 구조의 아카이브가 있다고 가정합니다 [Cloud Manager Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### 아카이브 추출 및 최종 접두사 제거

폴더에 아카이브의 압축을 풀고 바로 아래 하위 폴더가 `conf`, `conf.d`,
`conf.dispatcher.d` 및 `conf.modules.d`. 그렇지 않은 경우 계층 구조에서 위로 이동합니다.

### 사용하지 않는 하위 폴더 및 파일 제거

하위 폴더 제거 `conf` 및 `conf.modules.d`, 및 일치하는 파일 `conf.d/*.conf`.

### 게시되지 않은 모든 가상 호스트 제거

에서 가상 호스트 파일 제거 `conf.d/enabled_vhosts` 이(가) `author`, `unhealthy`, `health`,
`lc` 또는 `flush` 이름을 입력합니다. 의 모든 가상 호스트 파일 `conf.d/available_vhosts` 에 연결되어 있지 않은 항목도 제거할 수 있습니다.

### 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 달기

가상 호스트 파일에 포트 80 이외의 다른 포트만 참조하는 섹션이 있는 경우

```
<VirtualHost *:443>
...
</VirtualHost>
```

해당 섹션을 제거하거나 주석을 답니다. 이러한 섹션의 문은 처리되지 않지만, 이 문을 계속 유지하면 아무것도 적용되지 않은 상태로 편집을 종료할 수 있으므로 혼동을 줄 수 있습니다.

### rewrites 확인

디렉토리 입력 `conf.d/rewrites`.

이름이 인 모든 파일 제거 `base_rewrite.rules` 및 `xforwarded_forcessl_rewrite.rules` 및 다음을 제거해야 합니다. `Include` 이 문을 참조하는 가상 호스트 파일의 문입니다.

If `conf.d/rewrites` 이제 에는 단일 파일이 포함되어 있으며 이름을 로 변경해야 합니다. `rewrite.rules` 및 를 수정하는 것을 잊지 마십시오. `Include` 가상 호스트 파일에서도 해당 파일을 참조하는 문입니다.

그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 컨텐츠를 `Include` 가상 호스트 파일에서 이를 참조하는 문입니다.

### 변수 확인

디렉토리 입력 `conf.d/variables`.

이름이 인 모든 파일 제거 `ams_default.vars` 및 다음을 제거해야 합니다. `Include` 이 문을 참조하는 가상 호스트 파일의 문입니다.

If `conf.d/variables` 이제 에는 단일 파일이 포함되어 있으며 이름을 로 변경해야 합니다. `custom.vars` 및 를 수정하는 것을 잊지 마십시오. `Include` 가상 호스트 파일에서도 해당 파일을 참조하는 문입니다.

그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 컨텐츠를 `Include` 가상 호스트 파일에서 이를 참조하는 문입니다.

### 허용 목록 제거

폴더 제거 `conf.d/whitelists` 및 제거 `Include` 하위 폴더에 있는 일부 파일을 참조하는 가상 호스트 파일의 문입니다.

### 더 이상 사용할 수 없는 변수 모두 바꾸기

모든 가상 호스트 파일에서 다음을 수행합니다.

이름 바꾸기 `PUBLISH_DOCROOT` 끝 `DOCROOT`
다음 변수를 참조하는 섹션 제거 `DISP_ID`, `PUBLISH_FORCE_SSL` 또는 `PUBLISH_WHITELIST_ENABLED`

### 검사기를 실행하여 상태 확인

를 사용하여 디렉토리에서 Dispatcher 검사기를 실행합니다. `httpd` 하위 명령:

```
$ validator httpd .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

허용 목록에추가된이 아닌 Apache 지시문이 표시되면 제거합니다.

### 게시되지 않은 모든 팜 제거

에서 팜 파일 제거 `conf.dispatcher.d/enabled_farms` 이(가) `author`, `unhealthy`, `health`,
`lc` 또는 `flush` 이름을 입력합니다. 의 모든 팜 파일 `conf.dispatcher.d/available_farms` 에 연결되어 있지 않은 항목도 제거할 수 있습니다.

### 팜 파일 이름 바꾸기

의 모든 팜 `conf.dispatcher.d/enabled_farms` 패턴과 일치하도록 이름을 변경해야 합니다. `*.farm`, 예를 들어 팜 파일 `customerX_farm.any` 이름을 변경해야 함 `customerX.farm`.

### 캐시 확인

디렉토리 입력 `conf.dispatcher.d/cache`.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/cache` 은(는) 현재 비어 있습니다. 파일을 복사하십시오. `conf.dispatcher.d/cache/rules.any`
표준 Dispatcher 구성에서 이 폴더로. 표준 Dispatcher 구성은 폴더에서 찾을 수 있습니다 `src` 이 SDK의 다음 사항에 적응하는 것을 잊지 마십시오.
`$include` 를 참조하는 문 `ams_*_cache.any` 팜 파일의 규칙 파일도 참조하십시오.

대신 `conf.dispatcher.d/cache` 이제 접미사가 포함된 단일 파일 포함 `_cache.any`, 이름을 로 변경해야 합니다. `rules.any` 및 를 수정하는 것을 잊지 마십시오. `$include` 팜 파일에서도 이 파일을 참조하는 문입니다.

그러나 폴더에 해당 패턴을 가진 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 `$include` 팜 파일에서 이를 참조하는 문

접미사가 있는 모든 파일 제거 `_invalidate_allowed.any`.

파일 복사 `conf.dispatcher.d/cache/default_invalidate_any` 클라우드 Dispatcher 구성의 기본 AEM에서 해당 위치로.

각 팜 파일에서 `cache/allowedClients` 섹션 및 다음으로 바꾸기:

```
$include "../cache/default_invalidate.any"
```

### 클라이언트 헤더 확인

디렉토리 입력 `conf.dispatcher.d/clientheaders`.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/clientheaders` 이제 접미사가 포함된 단일 파일 포함 `_clientheaders.any`, 이름을 로 변경해야 합니다. `clientheaders.any` 및 를 수정하는 것을 잊지 마십시오. `$include` 팜 파일에서도 이 파일을 참조하는 문입니다.

그러나 폴더에 해당 패턴을 가진 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 `$include` 팜 파일에서 이를 참조하는 문

파일 복사 `conf.dispatcher/clientheaders/default_clientheaders.any` 기본 AEM as a Cloud Service Dispatcher 구성에서 해당 위치로

각 팜 파일에서 다음과 같은 clientheader include 문을 바꿉니다.

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

다음 문으로 바꿉니다.

```
$include "../clientheaders/default_clientheaders.any"
```

### filter 확인

디렉토리 입력 `conf.dispatcher.d/filters`.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/filters` 이제 에는 이름이 로 변경되어야 하는 단일 파일이 포함되어 있습니다.
`filters.any` 및 를 수정하는 것을 잊지 마십시오. `$include` 팜 파일에서도 이 파일을 참조하는 문입니다.

그러나 폴더에 해당 패턴을 가진 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 `$include` 팜 파일에서 이를 참조하는 문

파일 복사 `conf.dispatcher/filters/default_filters.any` 기본 AEM as a Cloud Service Dispatcher 구성에서 해당 위치로

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

다음 문으로 바꿉니다.

```
$include "../filters/default_filters.any"
```

### renders 확인

디렉토리 입력 `conf.dispatcher.d/renders`.

해당 폴더의 파일을 모두 제거합니다.

파일 복사 `conf.dispatcher.d/renders/default_renders.any` 기본 AEM as a Cloud Service Dispatcher 구성에서 해당 위치로

각 팜 파일에서 `renders` 섹션 및 다음으로 바꾸기:

```
$include "../renders/default_renders.any"
```

### virtualhosts 확인

디렉터리 이름 바꾸기 `conf.dispatcher.d/vhosts` 끝 `conf.dispatcher.d/virtualhosts` 입력한 다음

`ams_` 접두어가 있는 파일을 모두 제거합니다.

If `conf.dispatcher.d/virtualhosts` 이제 에는 이름이 로 변경되어야 하는 단일 파일이 포함되어 있습니다.
`virtualhosts.any` 및 를 수정하는 것을 잊지 마십시오. `$include` 팜 파일에서도 이 파일을 참조하는 문입니다.

그러나 폴더에 해당 패턴을 가진 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 `$include` 팜 파일에서 이를 참조하는 문

파일 복사 `conf.dispatcher/virtualhosts/default_virtualhosts.any` 기본 AEM as a Cloud Service Dispatcher 구성에서 해당 위치로

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

다음 문으로 바꿉니다.

```
$include "../virtualhosts/default_virtualhosts.any"
```

### 검사기를 실행하여 상태 확인

를 사용하여 디렉토리에서 AEM as a Cloud Service Dispatcher 검사기를 실행합니다. `dispatcher` 하위 명령:

```
$ validator dispatcher .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

정의되지 않은 변수 `PUBLISH_DOCROOT`와 관련된 오류가 표시되면 이름을 `DOCROOT`로 바꿀 수 있습니다.

다른 모든 오류에 대해서는 유효성 검사기 도구 설명서의 문제 해결 섹션을 참조하십시오.

### 로컬 배포로 구성 테스트(Docker 설치 필요)

스크립트 사용 `docker_run.sh` AEM as a Cloud Service Dispatcher 도구에서 구성에 배포에만 표시되는 다른 오류가 없는지 테스트할 수 있습니다.

### 1단계: 유효성 검사기를 사용하여 배포 정보 생성

```
validator full -d out .
```

전체 구성을 확인하고 의 배포 정보를 생성합니다. `out`

### 2단계: 해당 배포 정보를 사용하여 도커 이미지에서 Dispatcher 시작

macOS 컴퓨터에서 실행 중인 AEM 게시 서버를 사용하여 포트 4503에서 수신 대기하면 다음과 같이 해당 서버 앞에서 Dispatcher를 시작할 수 있습니다.

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

그러면 컨테이너가 시작되고 로컬 포트 8080에 Apache가 표시됩니다.

### 새 Dispatcher 구성 사용

축하합니다! 유효성 검사기가 더 이상 문제를 보고하지 않고 Docker 컨테이너가 아무런 오류 또는 경고 없이 시작하는 경우 구성을 로 이동할 수 있습니다. `dispatcher/src` git 저장소의 하위 디렉터리.

**AMS Dispatcher 구성 버전 1을 사용하는 고객은 고객 지원 센터에 문의하여 위의 지침을 따를 수 있도록 버전 1에서 버전 2로 마이그레이션하는 데 도움을 얻어야 합니다.**
