---
title: 컨텐츠 전달
description: '컨텐츠 전달 '
translation-type: tm+mt
source-git-commit: d1c953e1caf440f18e488f07a32bcf5bc3880f67

---


# 클라우드 서비스로 AEM에서 컨텐츠 전달 {#content-delivery}

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

컨텐츠 유형 HTML/텍스트는 발송자 캐시와 CDN이 모두 존중하는 임계값인 300초(5분) 후에 만료되도록 설정됩니다. 게시 서비스를 다시 배포하는 동안 디스패처 캐시가 지워지고 이후에 새 게시 노드가 트래픽을 승인하기 전에 다시 데워집니다.

아래 섹션에서는 CDN 구성 및 디스패처 캐싱을 비롯한 컨텐츠 전달에 대해 자세히 설명합니다.

작성자 서비스에서 게시 서비스로의 복제에 대한 정보는 [여기에서](/help/operations/replication.md)확인할 수 있습니다.

>[!NOTE]
>트래픽은 Apache 웹 서버를 통과하며, 이 서버는 디스패처를 포함한 모듈을 지원합니다. 디스패처는 주로 성능을 향상시키기 위해 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.

## CDN {#cdn}

AEM에서는 다음 세 가지 옵션을 제공합니다.

1. Adobe Managed CDN - AEM의 기본 CDN 이 옵션은 완전히 통합되어 있으므로 권장됩니다.
1. 고객 CDN은 Adobe Managed CDN을 가리키며, 고객은 자신의 CDN을 AEM의 기본 CDN에 연결합니다. 첫 번째 옵션이 실행 가능하지 않은 경우, 기본 CDN과 AEM의 통합을 여전히 활용하므로 다음 우선 옵션입니다. 고객은 자신의 CDN을 계속 관리할 책임이 있습니다.
1. 고객 관리 CDN - 고객은 고유한 CDN을 가져오며, 이를 전적으로 관리합니다.

>[!CAUTION]
>첫 번째 옵션은 매우 권장합니다. 두 번째 옵션을 선택하면 Adobe는 잘못된 구성의 결과에 대한 책임을 지지 않습니다.

두 번째 및 세 번째 옵션은 사례별로 사용할 수 있습니다. 여기에는 실행 취소가 어려운 기존 CDN 벤더와의 통합을 비롯하여 특정 사전 요구 사항을 충족해야 합니다.

### Adobe Managed CDN {#adobe-managed-cdn}

Adobe의 기본 CDN을 사용하여 컨텐츠 전달을 준비하는 방법은 아래에 설명된 바와 같이 간단합니다.

1. 이 정보가 들어 있는 보안 양식에 대한 링크를 공유하여 서명된 SSL 인증서 및 비밀 키를 Adobe에 제공합니다. 이 작업에 대한 고객 지원 팀과 협력하십시오.
참고:클라우드 서비스로 제공되는 AEM은 DV(Domain Validated) 인증서를 지원하지 않습니다.
1. 그러면 고객 지원에서 FQDN을 가리키는 CNAME DNS 레코드의 타이밍을 `adobe-aem.map.fastly.net`조정합니다.
1. SSL 인증서가 만료되면 알림을 받게 되므로 새 SSL 인증서를 다시 제출할 수 있습니다.

기본적으로 Adobe Managed CDN 설정의 경우 모든 공개 트래픽이 프로덕션 및 비프로덕션(개발 및 스테이지) 환경 모두에 대해 게시 서비스로 이동할 수 있습니다. 지정된 환경에 대한 게시 서비스로 트래픽을 제한하려면(예: IP 주소 범위에 따라 스테이징을 제한) 고객 지원 센터에서 이러한 제한을 구성해야 합니다.

### 고객 CDN은 Adobe Managed CDN을 가리킵니다. {#point-to-point-CDN}

기존 CDN을 사용하지만 고객 관리 CDN의 요구 사항을 충족할 수 없는 경우에 지원됩니다. 이 경우 자체 CDN을 관리하지만 Adobe의 관리 CDN을 가리킵니다.

귀하는 다음 사항을 준수해야 합니다.

1. 기존 CDN이 있어야 합니다.
1. 관리
1. Aem에서 클라우드 서비스로 작동하도록 CDN을 구성할 수 있어야 합니다. 아래 구성 지침을 참조하십시오.
1. 관련 문제가 발생할 경우 대기 중인 엔지니어링 CDN 전문가가 있습니다.
1. 프로덕션으로 전환하기 전에 로드 테스트를 성공적으로 수행하고 통과해야 합니다.

구성 지침:

1. 도메인 이름으로 `X-Forwarded-Host` 헤더를 설정합니다.
1. Adobe의 CDN의 수신 주소인 원본 도메인으로 호스트 헤더를 설정합니다. 값은 Adobe에서 가져옵니다.
1. SNI 헤더를 원본으로 보냅니다. 호스트 헤더와 마찬가지로 sni 헤더는 원본 도메인이어야 합니다.
1. 트래픽을 AEM 서버로 올바르게 라우팅하는 데 필요한 `X-Edge-Key`를 설정합니다. 값은 Adobe에서 가져옵니다.

### 고객 관리 CDN {#customer-managed-cdn}

기존 CDN을 사용해야 하는 경우 지원됩니다.  이 경우 AEM을 가리키도록 자체 CDN을 관리합니다.

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

### 캐싱 {#caching}

캐싱 프로세스는 아래에 표시된 규칙을 따릅니다.

### HTML/텍스트 {#html-text}

* 기본적으로, apache 레이어에서 방출하는 캐시 제어 헤더를 기반으로, 브라우저가 5분 동안 캐시합니다. CDN도 이 값을 따릅니다.
* aem을 클라우드 서비스 SDK 디스패처 도구로 `EXPIRATION_TIME` `global.vars` 사용할 때 변수를 정의하여 모든 HTML/텍스트 콘텐츠에 대해 재정의할 수 있습니다.

아래 파일에 다음 규칙이 `src/conf.dispatcher.d/cache` 있는지 확인해야 합니다.

```
/0000
{ /glob "*" /type "allow" }
```

* apache mod_headers 지시문을 통해 보다 세부적으로 분류된 수준에서 재정의할 수 있습니다. 예:

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200 s-maxage=200"
</LocationMatch>
```

아래 파일에 다음 규칙이 `src/conf.dispatcher.d/cache` 있는지 확인해야 합니다.

```
/0000
{ /glob "*" /type "allow" }
```

* 디스패처- [ttl AEM ACS Commons 프로젝트를](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)비롯한 다른 메서드는 값을 성공적으로 재정의하지 않습니다.

### 클라이언트측 라이브러리(js, css) {#client-side-libraries}

* aem의 클라이언트측 라이브러리 프레임워크를 사용하면 변경 사항이 고유한 경로를 갖는 새 파일로 매니페스트되므로 브라우저에서 무기한 캐시할 수 있는 방식으로 JavaScript 및 CSS 코드가 생성됩니다.  즉, 클라이언트 라이브러리를 참조하는 HTML은 필요에 따라 생성되므로 고객이 새로운 컨텐츠를 게시할 때 경험할 수 있습니다. &quot;불변의&quot; 값을 준수하지 않는 이전 브라우저의 경우 캐시 컨트롤은 &quot;불변의&quot; 또는 30일로 설정됩니다.
* 자세한 내용은 [클라이언트측 라이브러리 및 버전 일관성을](#content-consistency) 참조하십시오.

### 이미지 {#images}

* 캐시되지 않음

### 기타 컨텐츠 유형 {#other-content}

* 기본 캐싱 없음
* apache로 재정의할 수 `mod_headers`있습니다. 예:

```
<LocationMatch "\.(css|js)$">
    Header set Cache-Control "max-age=500 s-maxage=500"
</LocationMatch>
```

*캐시 헤더를 설정하는 다른 방법도 작동합니다.

라이브 트래픽을 수락하기 전에 고객은 엔드 투 엔드 트래픽 라우팅이 제대로 작동하는지 Adobe 고객 지원으로 확인해야 합니다.

## Dispatcher {#disp}

트래픽은 Apache 웹 서버를 통과하며, 이 서버는 디스패처를 포함한 모듈을 지원합니다. 디스패처는 주로 성능을 향상시키기 위해 게시 노드에서 처리를 제한하는 캐시로 사용됩니다.

HTML/텍스트 유형의 컨텐츠는 300s(5분) 만료에 해당하는 캐시 헤더로 설정됩니다.

이 섹션의 나머지 부분에서는 디스패처 캐시 무효화와 관련된 고려 사항에 대해 설명합니다.

### 활성화/비활성화 중 Dispatcher 캐시 무효화 {#cache-activation-deactivation}

이전 버전의 AEM과 마찬가지로 페이지를 게시 또는 게시 취소하면 디스패처 캐시에서 콘텐츠가 지워집니다. 캐싱 문제가 의심되는 경우 고객은 해당 페이지를 다시 게시해야 합니다.

게시 인스턴스가 작성자로부터 페이지 또는 자산의 새 버전을 받으면 플러시 에이전트를 사용하여 디스패처의 적절한 경로를 무효화합니다. 업데이트된 경로가 해당 부모와 함께 디스패처 캐시에서 최대 수준에서 제거됩니다( [상태 파일 수준으로](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)구성할 수 있습니다.

### 명시적 디스패처 캐시 무효화 {#explicit-invalidation}

일반적으로 디스패처의 컨텐츠를 수동으로 무효화할 필요는 없지만 필요에 따라 아래에 설명된 대로 무효화할 수 있습니다.

AEM을 클라우드 서비스로 사용하기 전에는 디스패처 캐시를 무효화하는 두 가지 방법이 있었습니다.

1. 게시 디스패처 플러시 에이전트를 지정하여 복제 에이전트를 호출합니다.
2. API `invalidate.cache` 를 직접 호출(예: `POST /dispatcher/invalidate.cache`)

이 `invalidate.cache` 방법은 특정 디스패처 노드만 해결하므로 더 이상 지원되지 않습니다.
클라우드 서비스로서의 AEM은 개별 노드 수준이 아니라 서비스 수준에서 작동하므로 AEM에서 캐시된 페이지 무효화 [페이지의 무효화](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html) 지침은 클라우드 서비스로 AEM에 대해 유효하지 않습니다.
대신 복제 플러시 에이전트를 사용해야 합니다. 이 작업은 복제 API를 사용하여 수행할 수 있습니다. Replication API 설명서는 [여기에서](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) 사용할 수 있으며 캐시 플러시의 예는 API [예제 페이지](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) , 특히 사용 가능한 모든 에이전트에 대해 ACTIVATE 유형의 복제 작업을 발급하는 `CustomStep` 예 등을 참조하십시오. 플러시 에이전트 종단점은 구성할 수 없지만 발송자를 가리키도록 미리 구성되었으며 플러시 에이전트를 실행하는 게시 서비스와 일치합니다. 일반적으로 플러시 에이전트는 OSGi 이벤트 또는 워크플로우에 의해 트리거될 수 있습니다.

아래 다이어그램은 이를 보여줍니다.

![](assets/cdnc.png "CDNCDN")

디스패처 캐시가 지워지지 않을 우려가 있는 경우 필요한 경우 디스패처 캐시를 플러시할 수 있는 고객 지원에 문의하십시오.

Adobe 관리 CDN은 TTL을 준수하므로 플러시할 필요가 없습니다. 문제가 의심되는 경우 필요에 따라 Adobe 관리 CDN 캐시를 플러시할 수 있는 고객 지원에 문의하십시오.

## 클라이언트측 라이브러리 및 버전 일관성 {#content-consistency}

페이지는 물론 HTML, Javascript, CSS 및 이미지로 구성됩니다. 고객은 Client-Side Libraries (clientlibs) 프레임워크를 활용하여 Javascript 및 CSS 리소스를 HTML 페이지로 가져와서 JS 라이브러리 간의 종속성을 고려하도록 권장합니다.

clientlibs 프레임워크는 자동 버전 관리를 제공하므로 개발자는 소스 제어에서 JS 라이브러리의 변경 사항을 확인할 수 있으며 고객이 릴리스를 추진할 때 최신 버전을 사용할 수 있습니다. 이렇게 하지 않으면 개발자는 새 버전의 라이브러리를 참조하는 HTML을 수동으로 변경해야 합니다. 이는 많은 HTML 템플릿이 동일한 라이브러리를 공유하는 경우에 특히 유용합니다.

새로운 버전의 라이브러리가 프로덕션에 릴리스되면 참조하는 HTML 페이지가 업데이트된 라이브러리 버전에 대한 새 링크로 업데이트됩니다. 주어진 HTML 페이지에 대한 브라우저 캐시가 만료되면 새로 고쳐진 페이지(AEM에서)가 이제 새 버전의 라이브러리를 참조할 수 있으므로 이전 라이브러리가 브라우저 캐시에서 로드될 우려가 없습니다. 즉, 새로 고쳐진 HTML 페이지에는 모든 최신 라이브러리 버전이 포함됩니다.

이 메커니즘은 직렬화된 해시로서, 클라이언트 라이브러리 링크에 추가되어 브라우저가 CSS/JS를 캐시할 수 있도록 버전에 따라 고유한 URL을 보장합니다. 직렬화된 해시는 클라이언트 라이브러리의 콘텐트가 변경될 때만 업데이트됩니다. 즉, 새 배포와 함께 관련 없는 업데이트가 발생하는 경우(즉, 클라이언트 라이브러리의 기본 css/js가 변경되지 않음) 참조가 동일하게 유지되므로 브라우저 캐시가 중단되지 않습니다.

### 클라이언트측 라이브러리의 긴 캐시 버전 활성화 - AEM을 클라우드 서비스 SDK로 빠른 시작 {#enabling-longcache}

기본 clientlib은 다음 예와 같이 HTML 페이지에 포함됩니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

strict clientlib 버전 관리가 활성화되면 장기적인 해시 키가 클라이언트 라이브러리에 선택기로 추가됩니다. 따라서 clientlib 참조는 다음과 같이 표시됩니다.

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Strict clientlib 버전 관리는 기본적으로 모든 AEM에서 클라우드 서비스 환경으로 활성화됩니다.

로컬 SDK에서 strict clientlib 버전 지정을 활성화하려면 Quickstart에서 다음 작업을 수행합니다.

1. OSGi 구성 관리자로 이동합니다. <host>/system/console/configMgr
1. Adobe Granite HTML Library Manager용 OSGi 구성을 찾습니다.
   * 엄격한 버전 관리를 활성화하려면 확인란을 선택합니다.
   * Long term client side cache key 레이블이 지정된 필드에 / 값을 입력합니다.*;해시
1. 변경 사항을 저장합니다. AEM을 클라우드 서비스로 사용하면 개발, 준비 및 프로덕션 환경에서 이 구성이 자동으로 활성화되므로 소스 제어에서 이 구성을 저장할 필요가 없습니다.
1. 클라이언트 라이브러리의 콘텐트가 변경될 때마다 새 해시 키가 생성되고 HTML 참조가 업데이트됩니다.
