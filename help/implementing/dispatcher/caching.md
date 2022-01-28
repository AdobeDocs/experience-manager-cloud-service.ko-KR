---
title: AEM as a Cloud Service에서 캐싱
description: 'AEM as a Cloud Service에서 캐싱 '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: 265999e5e92fc7b0f78f41bee4545ca6cee618a5
workflow-type: tm+mt
source-wordcount: '1547'
ht-degree: 1%

---

# 소개 {#intro}

트래픽은 CDN을 통해 디스패처를 포함한 모듈을 지원하는 Apache 웹 서버 레이어에 전달됩니다. 성능을 향상시키기 위해 디스패처가 주로 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.
규칙을 Dispatcher 구성에 적용하여 모든 기본 캐시 만료 설정을 수정할 수 있으므로 CDN에서 캐싱이 가능합니다. Dispatcher는 다음의 경우 결과 캐시 만료 헤더를 준수합니다 `enableTTL` 는 dispatcher 구성에서 활성화되어 있습니다. 즉, 다시 게시되는 컨텐츠 외부에서 특정 컨텐츠를 새로 고침합니다.

이 페이지에서는 디스패처 캐시가 무효화되는 방법과 클라이언트측 라이브러리와 관련하여 브라우저 수준에서 캐싱이 작동하는 방식을 설명합니다.

## 캐싱 {#caching}

### HTML/텍스트 {#html-text}

* 기본적으로 브라우저에 의해 5분 동안 캐시되며, `cache-control` apache 레이어에서 방출하는 헤더. CDN은 이 값도 따릅니다.
* 기본 HTML/텍스트 캐싱 설정은 `DISABLE_DEFAULT_CACHING` 변수 `global.vars`:

```
Define DISABLE_DEFAULT_CACHING
```

예를 들어, 비즈니스 로직에서는 기본적으로 연령 헤더가 0으로 설정되므로 페이지 헤더를 세밀하게 조정해야 하는 경우(달력 일을 기반으로 하는 값 포함) 유용합니다. 그건, **기본 캐싱을 해제할 때는 주의하십시오.**

* 모든 HTML/텍스트 컨텐츠에 대해 `EXPIRATION_TIME` 변수 `global.vars` AEM as a Cloud Service SDK Dispatcher 도구 사용.
* 다음 apache mod_headers 지시문에 의해 보다 세밀하게 조정된 수준에서 재정의할 수 있습니다.

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   전역 캐시 제어 헤더 또는 광범위한 정규식과 일치하는 헤더를 설정하여 비공개로 유지할 콘텐츠에 적용하지 않도록 주의하십시오. 여러 지시어를 사용하여 규칙이 세밀하게 적용되도록 합니다. 이를 통해 AEM as a Cloud Service은 디스패처 설명서에 설명된 대로 디스패처가 사용할 수 없음을 감지하는 대상에 적용되었음을 감지하는 경우 캐시 헤더를 제거합니다. AEM에서 항상 캐싱 헤더를 적용하도록 하기 위해 **항상** 다음과 같이 옵션을 선택합니다.

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header unset Cache-Control
        Header unset Expires
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   다음 파일이 `src/conf.dispatcher.d/cache` 에는 다음 규칙(기본 구성에 있음)이 있습니다.

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* 특정 콘텐츠가 캐시되지 않도록 하려면 **CDN에서**&#x200B;를 설정하는 경우 Cache-Control 헤더를 로 설정합니다. *개인*. 예를 들어, 다음과 같은 경우 이름이 인 디렉토리 아래에 html 컨텐츠가 표시되지 않습니다 **보안** CDN에서 캐시되는 작업:

   ```
      <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
      Header unset Cache-Control
      Header unset Expires
      Header always set Cache-Control “private”
     </LocationMatch>
   ```

   >[!NOTE]
   >다음을 포함한 다른 메서드 [dispatcher-ttl AEM ACS Commons 프로젝트](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)은 값을 성공적으로 재정의하지 않습니다.

   >[!NOTE]
   >Dispatcher가 여전히 자체 콘텐츠를 캐시할 수 있습니다 [캐싱 규칙](https://helpx.adobe.com/experience-manager/kb/find-out-which-requests-does-aem-dispatcher-cache.html). 컨텐츠를 정말로 비공개로 만들려면 Dispatcher가 캐시하지 않도록 해야 합니다.

### 클라이언트측 라이브러리(js,css) {#client-side-libraries}

* AEM 클라이언트측 라이브러리 프레임워크를 사용하면 변경 사항이 고유한 경로가 있는 새 파일로 매니페스트되므로 브라우저에서 무기한 캐싱할 수 있는 방식으로 JavaScript 및 CSS 코드가 생성됩니다.  즉, 클라이언트 라이브러리를 참조하는 HTML이 필요에 따라 생성되므로 고객이 게시되는 새로운 컨텐츠를 경험할 수 있습니다. cache-control은 &quot;변경할 수 없음&quot; 값을 준수하지 않는 이전 브라우저의 경우 30일로 설정됩니다.
* 섹션을 참조하십시오. [클라이언트 측 라이브러리 및 버전 일관성](#content-consistency) 추가 세부 정보.

### 이미지 및 Blob 저장소에 충분히 저장될 수 있는 큰 컨텐츠 {#images}

* 기본적으로 캐시되지 않음
* 다음 apache를 통해 보다 자세한 세분화된 수준에서 설정할 수 있습니다 `mod_headers` 지시문:

   ```
      <LocationMatch "^/content/.*\.(jpeg|jpg)$">
        Header set Cache-Control "max-age=222"
        Header set Age 0
      </LocationMatch>
   ```

   너무 많이 캐시하지 않도록 주의하고 AEM에서 항상 &quot;always&quot; 옵션을 사용하여 캐싱을 적용하도록 하는 방법에 대해서는 위의 html/text 섹션에서 토론을 참조하십시오.

   파일이 `src/conf.dispatcher.d/`캐시에 기본 구성에 있는 다음 규칙이 있습니다.

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

   캐시되지 않고 비공개로 유지되어야 하는 자산이 LocationMatch 지시어 필터의 일부가 아닌지 확인합니다.

   >[!NOTE]
   >다음을 포함한 다른 메서드 [dispatcher-ttl AEM ACS Commons 프로젝트](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)은 값을 성공적으로 재정의하지 않습니다.

### 노드 저장소의 다른 컨텐츠 파일 유형 {#other-content}

* 기본 캐싱 없음
* 기본값은 `EXPIRATION_TIME` html/text 파일 유형에 사용되는 변수입니다
* 캐시 만료는 적절한 regex를 지정하여 html/text 섹션에 설명된 것과 동일한 LocationMatch 전략으로 설정할 수 있습니다

## Dispatcher 캐시 무효화 {#disp}

일반적으로 디스패처 캐시를 무효화할 필요는 없습니다. 대신 컨텐츠가 다시 게시되는 경우 Dispatcher가 캐시를 새로 고침하고 캐시 만료 헤더를 준수하는 CDN에 의존해야 합니다.

### 활성화/비활성화 중 Dispatcher 캐시 무효화 {#cache-activation-deactivation}

이전 AEM 버전과 마찬가지로 페이지를 게시하거나 게시 취소하면 Dispatcher 캐시에서 콘텐츠가 지워집니다. 캐싱 문제가 의심되는 경우 고객은 해당 페이지를 다시 게시하고 ServerAlias localhost와 일치하는 가상 호스트를 사용할 수 있는지 확인해야 합니다. 이 호스트는 디스패처 캐시 무효화에 필요합니다.


게시 인스턴스가 작성자로부터 페이지 또는 자산의 새 버전을 받으면 초기화 에이전트를 사용하여 해당 디스패처에서 적절한 경로를 무효화합니다. 업데이트된 경로는 디스패처 캐시에서 해당 상위 항목과 함께 최대 수준에서 제거됩니다(를 사용하여 구성할 수 있습니다. [statefileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level).

### 명시적 디스패처 캐시 무효화 {#explicit-invalidation}

일반적으로 Dispatcher에서 콘텐츠를 수동으로 무효화할 필요는 없지만 필요한 경우 무효화할 수 있습니다.

>[!NOTE]
>AEM as a Cloud Service 이전에는 디스패처 캐시를 무효화하는 두 가지 방법이 있었습니다.
>
>1. 게시 디스패처 초기화 에이전트를 지정하여 복제 에이전트를 호출합니다
>2. 직접 호출 `invalidate.cache` API(예: `POST /dispatcher/invalidate.cache`)

>
>디스패처의 `invalidate.cache` API 접근 방식은 특정 디스패처 노드만 처리하므로 더 이상 지원되지 않습니다. AEM as a Cloud Service은 개별 노드 수준이 아니라 서비스 수준에서 작동하므로 [AEM에서 캐시된 페이지 무효화](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) AEM as a Cloud Service 페이지는 더 이상 유효하지 않습니다.

복제 초기화 에이전트를 사용해야 합니다. 이 작업은 를 사용하여 수행할 수 있습니다. [복제 API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). 플러시 에이전트 종단점은 구성할 수 없지만 플러시 에이전트를 실행하는 게시 서비스와 일치하면서 디스패처를 가리키도록 사전 구성되어 있습니다. 플러시 에이전트는 일반적으로 OSGi 이벤트 또는 워크플로우에 의해 트리거될 수 있습니다.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 
-->

아래 표시된 다이어그램은 이를 보여줍니다.

![CDN](assets/cdnd.png "CDN")

디스패처 캐시가 지워지지 않을 우려가 있는 경우 문의하십시오. [고객 지원](https://helpx.adobe.com/support.ec.html) 필요한 경우 디스패처 캐시를 플러시할 수 있는 사람.

Adobe 관리 CDN은 TTL을 준수하므로 플러시할 필요가 없습니다. 만약 문제가 의심된다면 [고객 지원 문의](https://helpx.adobe.com/support.ec.html) 필요에 따라 Adobe 관리 CDN 캐시를 플러시할 수 있는 사용자를 지원합니다.

## 클라이언트 측 라이브러리 및 버전 일관성 {#content-consistency}

페이지는 HTML, Javascript, CSS 및 이미지로 구성됩니다. 고객은 [클라이언트측 라이브러리(clientlibs) 프레임워크](/help/implementing/developing/introduction/clientlibs.md) javascript 및 CSS 리소스를 HTML 페이지로 가져오기 위해 JS 라이브러리 간 종속성을 고려합니다.

clientlibs 프레임워크는 자동 버전 관리를 제공합니다. 즉, 개발자는 소스 제어에서 JS 라이브러리의 변경 사항을 체크 인할 수 있으며 최신 버전은 고객이 릴리스를 푸시할 때 사용할 수 있습니다. 이렇게 하지 않으면 개발자가 새 라이브러리 버전에 대한 참조를 사용하여 HTML을 수동으로 변경해야 합니다. 이는 많은 HTML 템플릿이 동일한 라이브러리를 공유하는 경우 특히 중요합니다.

새 버전의 라이브러리가 프로덕션에 릴리스되면 참조하는 HTML 페이지가 업데이트된 라이브러리 버전에 대한 새 링크로 업데이트됩니다. 주어진 HTML 페이지에 대해 브라우저 캐시가 만료되면 새로 고친 페이지(AEM)이 새 버전의 라이브러리를 참조할 수 있으므로 이전 라이브러리가 브라우저 캐시에서 로드될 염려가 없습니다. 즉, 새로 고친 HTML 페이지에는 모든 최신 라이브러리 버전이 포함됩니다.

이 메커니즘은 직렬화된 해시이며, 클라이언트 라이브러리 링크에 추가되므로 브라우저에서 CSS/JS를 캐시할 고유한 버전이 지정된 URL을 보장합니다. 직렬화된 해시는 클라이언트 라이브러리의 내용이 변경되는 경우에만 업데이트됩니다. 즉, 새 배포가 있어도 관련 없는 업데이트가 발생하는 경우(즉, 클라이언트 라이브러리의 기본 css/js에 대한 변경 사항이 없는 경우) 참조가 동일하게 유지되므로 브라우저 캐시가 중단되지 않습니다.

### 클라이언트 측 라이브러리의 긴 캐시 버전 활성화 - AEM as a Cloud Service SDK 빠른 시작 {#enabling-longcache}

HTML 페이지에 포함된 기본 clientlib은 다음 예와 같습니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

strict clientlib 버전 관리가 활성화되면 장기적인 해시 키가 클라이언트 라이브러리에 선택기로 추가됩니다. 따라서 clientlib 참조는 다음과 같습니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

모든 AEM as a Cloud Service 환경에서 Strict clientlib 버전 관리가 기본적으로 활성화됩니다.

로컬 SDK Quickstart에서 strict clientlib 버전 지정을 활성화하려면 다음 작업을 수행하십시오.

1. OSGi 구성 관리자로 이동합니다 `<host>/system/console/configMgr`
1. Granite HTML 라이브러리 관리자를 위한 OSGi 구성을 찾습니다.
   * 엄격한 버전 관리를 사용하려면 확인란을 선택합니다
   * Long term client side cache key 라는 필드에 / 값을 입력합니다.*;해시
1. 변경 사항을 저장합니다. AEM as a Cloud Service은 개발, 스테이지 및 프로덕션 환경에서 이 구성을 자동으로 활성화하므로 이 구성을 소스 제어에 저장할 필요가 없습니다.
1. 클라이언트 라이브러리의 내용이 변경될 때마다 새 해시 키가 생성되고 HTML 참조가 업데이트됩니다.
