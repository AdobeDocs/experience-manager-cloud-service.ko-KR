---
title: AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션
description: AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션
feature: Dispatcher
exl-id: ff7397dd-b6e1-4d08-8e2d-d613af6b81b3
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 7%

---

# AMS에서 AEM as a Cloud Service로 Dispatcher 구성 마이그레이션 {#Dispatcher-in-the-cloud}

## AMS Dispatcher과 AEM as a Cloud Service의 주요 차이점 {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

AEM as a Cloud Service의 Apache 및 Dispatcher 구성은 AMS 구성과 매우 유사합니다. 주요 차이점은 다음과 같습니다.

* AEM as a Cloud Service에서 일부 Apache 지시문이 사용되지 않을 수 있습니다(예: `Listen` 또는 `LogLevel`)
* AEM as a Cloud Service에서는 일부 Dispatcher 구성만 include 파일에 넣을 수 있으며 해당 이름을 지정해야 합니다. 예를 들어 다른 호스트에서 재사용하려는 필터 규칙은 `filters/filters.any` 파일에 넣어야 합니다. 자세한 내용은 참조 페이지 를 참조하십시오.
* AEM as a Cloud Service에는 보안 문제를 방지하기 위해 `/glob`을(를) 사용하여 작성된 필터 규칙을 허용하지 않도록 하는 추가 유효성 검사가 있습니다. `deny *`이(가) 사용할 수 없는 `allow *`보다 사용되기 때문에 고객은 Dispatcher을 로컬로 실행하고 시행착오를 수행하여 로그를 보고 Dispatcher 필터가 차단 중인 경로를 정확히 파악하여 추가할 수 있습니다.
* AEM as a Cloud Service에서는 현재 [유연한 Dispatcher 구성 소스 모드를 사용](/help/implementing/dispatcher/disp-overview.md#validation-debug)하도록 옵트인하는 것이 좋습니다. 예를 들어 웹 계층 구성 파이프라인을 사용하거나 구성 파일의 개수 및 구조에 보다 유연하게 대처할 수 있습니다.

## AMS에서 AEM as a Cloud Service으로 Dispatcher 구성을 마이그레이션하기 위한 지침

Dispatcher 구성 구조에는 Managed Services과 AEM as a Cloud Service 간에 차이가 있습니다. 다음은 AMS Dispatcher 구성 버전 2에서 AEM as a Cloud Service으로 마이그레이션하는 방법에 대한 단계별 안내서입니다.

## AMS를 AEM as a Cloud Service Dispatcher 구성으로 변환하는 방법

다음 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다. 다음과 같습니다.
[Cloud Manager Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)에 설명된 것과 유사한 구조의 아카이브가 있습니다.

### 아카이브 추출 및 최종 접두사 제거

폴더에 보관 파일의 압축을 풀고 바로 아래 하위 폴더가 `conf`, `conf.d`(으)로 시작하는지 확인합니다.
`conf.dispatcher.d` 및 `conf.modules.d`. 그렇지 않은 경우 계층 구조에서 위로 이동합니다.

### 사용하지 않는 하위 폴더 및 파일 제거

`conf` 및 `conf.modules.d` 하위 폴더와 `conf.d/*.conf`와(과) 일치하는 파일을 제거합니다.

### 게시되지 않은 모든 가상 호스트 제거

`conf.d/enabled_vhosts`에서 `author`, `unhealthy`, `health`이(가) 있는 가상 호스트 파일을 제거하십시오.
이름에 `lc` 또는 `flush`이(가) 있습니다. `conf.d/available_vhosts`에 없는 모든 가상 호스트 파일
에 연결된 도 제거할 수 있습니다.

### 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 달기

가상 호스트 파일에 포트 80 이외의 다른 포트만 참조하는 섹션이 있는 경우

```
<VirtualHost *:443>
...
</VirtualHost>
```

해당 섹션을 제거하거나 주석을 답니다. 이 섹션의 문은 처리되지 않지만
계속 유지하면 효과가 없는 편집으로 끝날 수 있으므로 혼란스럽습니다.

### rewrites 확인

`conf.d/rewrites` 디렉터리를 입력하십시오.

`base_rewrite.rules` 및 `xforwarded_forcessl_rewrite.rules` 파일을 제거하고 다음 작업을 수행하십시오.
가상 호스트 파일에서 이 문을 참조하는 `Include` 문을 제거합니다.

이제 `conf.d/rewrites`에 단일 파일이 포함되어 있는 경우 이름을 `rewrite.rules`(으)로 변경하고 이름을 변경하지 마십시오
가상 호스트 파일에서도 해당 파일을 참조하는 `Include` 문을 수정하지 마십시오.

그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 파일의 내용은 다음과 같아야 합니다
가상 호스트 파일에서 이를 참조하는 `Include` 문으로 복사되었습니다.

### 변수 확인

`conf.d/variables` 디렉터리를 입력하십시오.

이름이 `ams_default.vars`인 파일을 제거하고 가상 파일에서 `Include` 문을 제거해야 합니다.
이 파일을 참조하는 호스트 파일입니다.

이제 `conf.d/variables`에 단일 파일이 포함되어 있는 경우 이름을 `custom.vars`(으)로 변경하고 이름을 변경하지 마십시오
가상 호스트 파일에서도 해당 파일을 참조하는 `Include` 문을 수정하지 마십시오.

그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 파일의 내용은 다음과 같아야 합니다
가상 호스트 파일에서 이를 참조하는 `Include` 문으로 복사되었습니다.

### 허용 목록 제거

다음을 참조하는 가상 호스트 파일에서 `conf.d/whitelists` 폴더를 제거하고 `Include` 문을 제거합니다.
해당 하위 폴더에 있는 일부 파일입니다.

### 더 이상 사용할 수 없는 변수 모두 바꾸기

모든 가상 호스트 파일에서 다음을 수행합니다.

`PUBLISH_DOCROOT` 이름을 `DOCROOT`(으)로 바꾸기
이름이 `DISP_ID`, `PUBLISH_FORCE_SSL` 또는 `PUBLISH_WHITELIST_ENABLED`인 변수를 참조하는 섹션 제거

### 검사기를 실행하여 상태 확인

`httpd` 하위 명령을 사용하여 디렉터리에서 Dispatcher 유효성 검사기를 실행합니다.

```
$ validator httpd .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다
파일.

허용 목록에추가된이 아닌 Apache 지시문이 표시되면 제거합니다.

### 게시되지 않은 모든 팜 제거

`conf.dispatcher.d/enabled_farms`에서 `author`, `unhealthy`, `health`이(가) 있는 팜 파일 제거
이름에 `lc` 또는 `flush`이(가) 있습니다. `conf.dispatcher.d/available_farms`에 없는 모든 팜 파일
에 연결된 도 제거할 수 있습니다.

### 팜 파일 이름 바꾸기

`conf.dispatcher.d/enabled_farms`에 있는 모든 팜의 이름을 `*.farm` 패턴과 일치하도록 변경해야 합니다. 예를 들어
`customerX_farm.any`(이)라는 팜 파일의 이름은 `customerX.farm`(으)로 변경해야 합니다.

### 캐시 확인

`conf.dispatcher.d/cache` 디렉터리를 입력하십시오.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

`conf.dispatcher.d/cache`이(가) 비어 있으면 `conf.dispatcher.d/cache/rules.any` 파일을 복사하십시오.
표준 Dispatcher 구성에서 이 폴더로. 표준 Dispatcher
이 SDK의 `src` 폴더에서 구성을 찾을 수 있습니다. 다음 사항에 적응하는 것을 잊지 마십시오.
팜 파일의 `ams_*_cache.any` 규칙 파일을 참조하는 `$include` 문
또한.

대신 `conf.dispatcher.d/cache`에 접미사 `_cache.any`이(가) 포함된 단일 파일이 있으면
이름을 `rules.any`(으)로 변경하고 `$include` 문을 수정해야 합니다.
팜 파일에서도 이 파일을 참조합니다.

그러나 폴더에 해당 패턴을 가진 팜 관련 파일이 여러 개 있는 경우 해당 파일의 내용
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

접미사 `_invalidate_allowed.any`이(가) 있는 파일을 제거하십시오.

기본값에서 `conf.dispatcher.d/cache/default_invalidate_any` 파일을 복사합니다.
Cloud Dispatcher 구성의 AEM을 해당 위치에 추가합니다.

각 팜 파일에서 `cache/allowedClients` 섹션의 내용을 제거하고 바꿉니다
포함:

```
$include "../cache/default_invalidate.any"
```

### 클라이언트 헤더 확인

`conf.dispatcher.d/clientheaders` 디렉터리를 입력하십시오.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/clientheaders`에 접미사 `_clientheaders.any`이(가) 포함된 단일 파일이 있는 경우
이름을 `clientheaders.any`(으)로 변경하고 `$include` 문을 수정해야 합니다.
팜 파일에서도 이 파일을 참조합니다.

그러나 폴더에 해당 패턴을 가진 팜 관련 파일이 여러 개 있는 경우 해당 파일의 내용
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

기본값에서 `conf.dispatcher/clientheaders/default_clientheaders.any` 파일을 복사합니다.
해당 위치에 대한 AEM as a Cloud Service Dispatcher 구성.

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

`conf.dispatcher.d/filters` 디렉터리를 입력하십시오.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/filters`에 단일 파일이 포함된 경우 이름을 로 변경해야 합니다.
`filters.any` 및 이를 참조하는 `$include` 문을 조정하는 것을 잊지 마십시오.
팜 파일에 있는 파일도 마찬가지입니다.

그러나 폴더에 해당 패턴을 가진 팜 관련 파일이 여러 개 있는 경우 해당 파일의 내용
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

기본값에서 `conf.dispatcher/filters/default_filters.any` 파일을 복사합니다.
해당 위치에 대한 AEM as a Cloud Service Dispatcher 구성.

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

다음 문으로 바꿉니다.

```
$include "../filters/default_filters.any"
```

### renders 확인

`conf.dispatcher.d/renders` 디렉터리를 입력하십시오.

해당 폴더의 파일을 모두 제거합니다.

기본값에서 `conf.dispatcher.d/renders/default_renders.any` 파일을 복사합니다.
해당 위치에 대한 AEM as a Cloud Service Dispatcher 구성.

각 팜 파일에서 `renders` 섹션의 내용을 제거하고 바꿉니다
포함:

```
$include "../renders/default_renders.any"
```

### virtualhosts 확인

`conf.dispatcher.d/vhosts` 디렉터리의 이름을 `conf.dispatcher.d/virtualhosts`(으)로 변경하고 입력하십시오.

`ams_` 접두어가 있는 파일을 모두 제거합니다.

이제 `conf.dispatcher.d/virtualhosts`에 단일 파일이 포함된 경우 이름을 로 변경해야 합니다.
`virtualhosts.any` 및 이를 참조하는 `$include` 문을 조정하는 것을 잊지 마십시오.
팜 파일에 있는 파일도 마찬가지입니다.

그러나 폴더에 해당 패턴을 가진 팜 관련 파일이 여러 개 있는 경우 해당 파일의 내용
팜 파일에서 이를 참조하는 `$include` 문에 복사해야 합니다.

기본값에서 `conf.dispatcher/virtualhosts/default_virtualhosts.any` 파일을 복사합니다.
해당 위치에 대한 AEM as a Cloud Service Dispatcher 구성.

각 팜 파일에서 다음과 같은 filter 포함 문을

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

다음 문으로 바꿉니다.

```
$include "../virtualhosts/default_virtualhosts.any"
```

### 검사기를 실행하여 상태 확인

`dispatcher` 하위 명령을 사용하여 디렉터리에서 AEM as a Cloud Service Dispatcher 유효성 검사기를 실행합니다.

```
$ validator dispatcher .
```

누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다
파일.

정의되지 않은 변수 `PUBLISH_DOCROOT`와 관련된 오류가 표시되면 이름을 `DOCROOT`로 바꿀 수 있습니다.

다른 모든 오류에 대해서는 의 문제 해결 섹션을 참조하십시오.
유효성 검사기 도구 설명서.

### 로컬 배포로 구성 테스트(Docker 설치 필요)

AEM as a Cloud Service Dispatcher 도구에서 `docker_run.sh` 스크립트를 사용하여 다음을 테스트할 수 있습니다.
구성에 에만 표시되는 다른 오류가 포함되어 있지 않습니다.
배포:

### 1단계: 유효성 검사기를 사용하여 배포 정보 생성

```
validator full -d out .
```

전체 구성을 확인하고 `out`에서 배포 정보를 생성합니다.

### 2단계: 해당 배포 정보를 사용하여 도커 이미지에서 Dispatcher 시작

macOS 컴퓨터에서 실행 중인 AEM 게시 서버가 포트 4503에서 수신 대기하는 경우
다음과 같이 해당 서버 앞에서 Dispatcher 시작을 실행할 수 있습니다.

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

그러면 컨테이너가 시작되고 로컬 포트 8080에 Apache가 표시됩니다.

### 새 Dispatcher 구성 사용

축하합니다! 유효성 검사기가 더 이상 문제를 보고하지 않고
docker 컨테이너가 아무런 오류 또는 경고 없이 시작됩니다.
구성을 `dispatcher/src` 하위 디렉터리로 이동할 준비가 되었습니다.
git 저장소의

**AMS Dispatcher 구성 버전 1을 사용하는 고객은 고객 지원 센터에 문의하여 위의 지침을 따르도록 버전 1에서 버전 2로 마이그레이션해야 합니다.**
