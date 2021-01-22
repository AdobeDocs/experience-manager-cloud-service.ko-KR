---
title: AEM as a Cloud Service에서 캐싱
description: 'AEM as a Cloud Service에서 캐싱 '
translation-type: tm+mt
source-git-commit: a02e035a842e7c633aaa926d0ab092b2c7aed5cb
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 1%

---


# 소개 {#intro}

트래픽은 CDN을 통해 디스패처를 포함한 모듈을 지원하는 Apache 웹 서버 레이어로 전달됩니다. 성능을 높이기 위해 디스패처는 주로 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.
규칙을 디스패처 구성에 적용하여 모든 기본 캐시 만료 설정을 수정할 수 있으므로 CDN에서 캐싱할 수 있습니다. 디스패처는 또한 `enableTTL`이(가) 디스패처 구성에서 활성화된 경우 결과 캐시 만료 헤더를 보존하며, 이는 다시 게시되는 컨텐츠 외부에서도 특정 컨텐츠를 새로 고침한다는 것을 의미합니다.

이 페이지에서는 발송자 캐시가 무효화되는 방식뿐만 아니라 클라이언트측 라이브러리와 관련하여 브라우저 수준에서 캐싱이 작동하는 방법도 설명합니다.

## {#caching} 캐싱

### HTML/텍스트 {#html-text}

* 기본적으로 apache 레이어에서 방출한 `cache-control` 헤더를 기반으로, 브라우저가 5분 동안 캐시합니다. CDN도 이 값을 준수합니다.
* `global.vars`에서 `DISABLE_DEFAULT_CACHING` 변수를 정의하여 기본 HTML/텍스트 캐싱 설정을 비활성화할 수 있습니다.

```
Define DISABLE_DEFAULT_CACHING
```

이 기능은 기본적으로 연령 헤더가 0으로 설정되므로 비즈니스 논리에서 연령 헤더(달력을 기준으로 값)를 세밀하게 조정해야 하는 경우에 유용합니다. 즉, **기본 캐싱을 끌 때는 주의하십시오.**

* aem을 Cloud Service SDK Dispatcher 도구로 사용하여 `global.vars`에서 `EXPIRATION_TIME` 변수를 정의하여 모든 HTML/Text 컨텐츠에 대해 재정의할 수 있습니다.
* 다음과 같은 apache mod_headers 지시문으로 더 세부적으로 분류된 수준에서 재정의할 수 있습니다.

   ```
   <LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   전역 캐시 제어 헤더나 와이드 정규식과 일치하는 헤더를 설정할 때는 주의를 기울여 비공개로 유지하려는 내용에 적용되지 않도록 합니다. 여러 지시문을 사용하여 규칙이 세부적으로 적용되도록 하십시오. 이와 함께, Cloud Service으로 AEM은 디스패처 설명서에 설명된 대로 디스패처가 사용할 수 없는 것으로 감지된 대상에 적용되었음을 감지하면 캐시 헤더를 제거합니다. AEM에서 항상 캐시를 적용하려면 다음과 같이 &quot;always&quot; 옵션을 추가할 수 있습니다.

   ```
   <LocationMatch "\.(html)$">
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   `src/conf.dispatcher.d/cache` 아래의 파일에 기본 구성에 있는 다음 규칙이 있는지 확인해야 합니다.

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* 특정 콘텐츠가 캐시되지 않도록 하려면 Cache-Control 헤더를 *private*&#x200B;으로 설정합니다. 예를 들어, 다음 예제에서는 **myfolder** 디렉토리의 html 콘텐츠가 캐시되지 않도록 합니다.

   ```
      <LocationMatch "/myfolder/.*\.(html)$">.  // replace with the right regex
      Header set Cache-Control “private”
     </LocationMatch>
   ```

   >[!NOTE]
   >[dispatcher-ttl AEM ACS Commons 프로젝트](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/) 등 다른 메서드는 값을 성공적으로 재정의하지 않습니다.

### 클라이언트측 라이브러리(js,css) {#client-side-libraries}

* aem 클라이언트측 라이브러리 프레임워크를 사용하면 모든 변경 사항이 고유한 경로를 갖는 새 파일로 매니페스트되므로 브라우저에서 무기한 캐시할 수 있는 방식으로 JavaScript 및 CSS 코드가 생성됩니다.  즉, 클라이언트 라이브러리를 참조하는 HTML이 필요에 따라 생성되므로 고객이 새 컨텐츠를 게시한 즉시 경험할 수 있습니다. &quot;변경할 수 없는&quot; 값을 준수하지 않는 이전 브라우저의 경우 캐시 컨트롤은 &quot;변경할 수 없음&quot; 또는 30일로 설정됩니다.
* 자세한 내용은 [클라이언트측 라이브러리 및 버전 일관성](#content-consistency) 섹션을 참조하십시오.

### Blob 저장소 {#images}에 저장할 수 있을 만큼 큰 이미지 및 컨텐츠

* 기본적으로 캐시되지 않음
* 다음 apache `mod_headers` 지시문으로 더 세분화된 수준에서 설정할 수 있습니다.

   ```
      <LocationMatch "^\.*.(jpeg|jpg)$">
        Header set Cache-Control "max-age=222"
        Header set Age 0
      </LocationMatch>
   ```

   너무 많이 캐시하지 않도록 주의하고 AEM에서 항상 &quot;항상&quot; 옵션을 사용하여 캐시를 강제 적용하는 방법에 대해 위의 html/text 섹션에 있는 토론을 참조하십시오.

   `src/conf.dispatcher.d/`cache 아래의 파일에 기본 구성에 있는 다음 규칙이 있는지 확인해야 합니다.

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

   캐시되지 않고 비공개로 유지되도록 설정된 에셋이 LocationMatch 지시어 필터에 속하지 않는지 확인합니다.

   >[!NOTE]
   >[dispatcher-ttl AEM ACS Commons 프로젝트](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/) 등 다른 메서드는 값을 성공적으로 재정의하지 않습니다.

### 노드 저장소의 다른 콘텐트 파일 형식 {#other-content}

* 기본 캐싱 없음
* 기본값은 html/텍스트 파일 유형에 사용되는 `EXPIRATION_TIME` 변수로 설정할 수 없습니다.
* 캐시 만료는 적절한 regex를 지정하여 html/text 섹션에 설명된 것과 동일한 LocationMatch 전략으로 설정할 수 있습니다

## 발송자 캐시 무효화 {#disp}

일반적으로 디스패처 캐시를 무효화할 필요는 없습니다. 대신 컨텐츠가 다시 게시되고 있고 캐시 만료 헤더를 준수하는 CDN은 디스패처가 캐시를 새로 고침하는 데 의존해야 합니다.

### 활성화/비활성화 중 디스패처 캐시 무효화 {#cache-activation-deactivation}

이전 버전의 AEM처럼 페이지를 게시 또는 게시 취소하면 디스패처 캐시에서 내용이 지워집니다. 캐싱 문제가 의심되는 경우 고객은 해당 페이지를 다시 게시해야 합니다.

게시 인스턴스가 작성자로부터 페이지 또는 자산의 새 버전을 받으면 플러시 에이전트를 사용하여 디스패처에 있는 적절한 경로를 무효화합니다. 업데이트된 경로가 해당 부모와 함께 디스패처 캐시에서 최대 수준(이 경로를 [statfileslevel](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)으로 구성할 수 있습니다.

### 명시적 디스패처 캐시 무효화 {#explicit-invalidation}

일반적으로 디스패처의 컨텐츠를 수동으로 무효화할 필요는 없지만 필요에 따라 아래에 설명된 대로 무효화할 수 있습니다.

AEM에서 Cloud Service으로 사용하기 전에는 디스패처 캐시를 무효화하는 두 가지 방법이 있었습니다.

1. 게시 디스패처 플러시 에이전트를 지정하여 복제 에이전트를 호출합니다.
2. `invalidate.cache` API를 직접 호출(예: `POST /dispatcher/invalidate.cache`)

디스패처의 `invalidate.cache` API 접근 방식은 특정 디스패처 노드만 해결하므로 더 이상 지원되지 않습니다. CLOUD SERVICE은 개별 노드 수준이 아니라 서비스 수준에서 작동하므로 [AEM에서 캐시된 페이지 무효화](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html) 페이지의 무효화 지침은 더 이상 AEM에서 Cloud Service으로 유효하지 않습니다.
대신 복제 플러시 에이전트를 사용해야 합니다. 복제 API를 사용하여 수행할 수 있습니다. 복제 API 설명서는 [여기](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html)에서 사용할 수 있으며 캐시 플러싱의 예를 보려면 [API 예제 페이지](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) 특히 `CustomStep` 예제는 ACTIVATE 유형의 복제 작업을 사용 가능한 모든 에이전트에 실행하는 방법을 참조하십시오. 플러시 에이전트 끝점은 구성할 수 없지만 플러시 에이전트를 실행하는 게시 서비스와 일치하도록 사전 구성되어 있습니다. 일반적으로 플러시 에이전트는 OSGi 이벤트 또는 워크플로우에 의해 트리거될 수 있습니다.

아래 다이어그램은 이를 보여 줍니다.

![](assets/cdnd.png "CDNCDN")

디스패처 캐시가 지워지지 않을 우려가 있는 경우 필요한 경우 디스패처 캐시를 플러시할 수 있는 [고객 지원](https://helpx.adobe.com/support.ec.html)에 문의하십시오.

Adobe 관리 CDN은 TTL을 유지하므로 플러시할 필요가 없습니다. 문제가 의심되는 경우 필요에 따라 Adobe 관리 CDN 캐시를 플러시할 수 있는 [고객 지원 센터](https://helpx.adobe.com/support.ec.html) 지원에 문의하십시오.

## 클라이언트측 라이브러리 및 버전 일관성 {#content-consistency}

페이지는 HTML, Javascript, CSS 및 이미지로 구성됩니다. 고객은 JS 라이브러리 간의 종속성을 고려하여 [클라이언트측 라이브러리(clientlibs) 프레임워크](/help/implementing/developing/introduction/clientlibs.md)를 활용하여 Javascript 및 CSS 리소스를 HTML 페이지로 가져올 수 있습니다.

clientlibs 프레임워크는 자동 버전 관리를 제공합니다. 즉, 개발자는 소스 제어에서 JS 라이브러리의 변경 사항을 확인할 수 있으며 고객이 릴리스를 중단할 때 최신 버전을 사용할 수 있습니다. 이렇게 하지 않으면 개발자는 새 버전의 라이브러리에 대한 참조를 사용하여 HTML을 수동으로 변경해야 합니다. 이는 많은 HTML 템플릿이 동일한 라이브러리를 공유하는 경우 특히 유용합니다.

새로운 버전의 라이브러리가 프로덕션에 릴리스되면 참조하는 HTML 페이지가 업데이트된 라이브러리 버전에 대한 새로운 링크로 업데이트됩니다. 지정된 HTML 페이지에 대한 브라우저 캐시가 만료되면 (AEM의) 새로 고친 페이지가 이제 라이브러리의 새 버전을 참조할 수 있으므로 이전 라이브러리가 브라우저 캐시에서 로드될 우려가 없습니다. 즉, 새로 고친 HTML 페이지에는 모든 최신 라이브러리 버전이 포함됩니다.

이 메커니즘은 직렬화된 해시로, 클라이언트 라이브러리 링크에 추가되어 CSS/JS를 캐시하기 위해 브라우저에 고유한 버전 URL을 보장합니다. 직렬화된 해시는 클라이언트 라이브러리의 내용이 변경될 때에만 업데이트됩니다. 즉, 새 배포와 함께 관련 없는 업데이트가 발생하는 경우(즉, 클라이언트 라이브러리의 기본 css/js에 대한 변경 사항 없음) 참조는 동일하게 유지되므로 브라우저 캐시를 중단 없이 진행할 수 있습니다.

### 클라이언트 측 라이브러리의 긴 캐시 버전 활성화 - Cloud Service SDK로 AEM 빠른 시작 {#enabling-longcache}

기본 clientlib은 다음 예와 같은 HTML 페이지에 포함됩니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

strict clientlib 버전 관리가 활성화되면 장기적인 해시 키가 클라이언트 라이브러리에 선택기로 추가됩니다. 따라서 clientlib 참조는 다음과 같습니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

엄격한 clientlib 버전 관리는 기본적으로 모든 AEM에서 Cloud Service 환경으로 활성화됩니다.

로컬 SDK에서 strict clientlib 버전 매기기를 활성화하려면 Quickstart에서 다음 작업을 수행합니다.

1. OSGi 구성 관리자 `<host>/system/console/configMgr`로 이동합니다.
1. Adobe Granite HTML 라이브러리 관리자용 OSGi 구성을 찾습니다.
   * 엄격한 버전 관리를 활성화하려면 확인란을 선택합니다.
   * 장기 클라이언트측 캐시 키라는 레이블이 있는 필드에 / 값을 입력합니다.*;해시
1. 변경 사항을 저장합니다. AEM은 개발, 준비 및 프로덕션 환경에서 이 구성을 자동으로 활성화하므로 이 구성을 소스 제어에 저장할 필요가 없습니다.
1. 클라이언트 라이브러리의 내용이 변경될 때마다 새 해시 키가 생성되고 HTML 참조가 업데이트됩니다.
