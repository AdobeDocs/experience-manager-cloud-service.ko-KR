---
title: AEM as a Cloud Service의 CDN
description: AEM 관리 CDN을 사용하는 방법과 자체 CDN을 AEM 관리 CDN으로 지정하는 방법을 알아봅니다.
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
role: Admin
source-git-commit: 62af306bbf645c4d70d0f07f95aa90e4d53e20f8
workflow-type: tm+mt
source-wordcount: '1744'
ht-degree: 11%

---


# AEM as a Cloud Service의 CDN {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="AEM as a Cloud Service의 CDN"
>abstract="AEM as Cloud Service는 CDN을 기본 제공합니다. 주요 목적은 브라우저 근처 가장자리에 CDN 노드에서 캐시 가능 콘텐츠를 게재하여 지연 시간을 줄이는 것입니다. AEM 애플리케이션 최적의 성능을 위해 완벽하게 관리 및 구성됩니다."

AEM as a Cloud Service에는 사용자의 브라우저와 가까운 에지 노드에서 캐시 가능 컨텐츠를 전달하여 지연 시간을 줄이도록 설계된 통합 CDN이 포함되어 있습니다. 이 완전 관리 CDN은 AEM 애플리케이션 성능에 최적화되어 있습니다.

AEM 관리 CDN은 대부분의 고객의 성능 및 보안 요구 사항을 충족합니다. 게시 계층의 경우 고객은 관리해야 하는 자체 CDN을 통해 트래픽을 라우팅하도록 선택할 수 있습니다. 이 옵션은 특히 고객이 대체하기 어려운 CDN 공급자와의 기존 레거시 통합을 보유하고 있는 경우 사안별로 사용할 수 있습니다.

Edge Delivery Services 계층에 게시하려는 고객은 Adobe의 관리 CDN을 이용할 수 있습니다. [Adobe 관리 CDN](#aem-managed-cdn)을(를) 참조하십시오. <!-- CQDOC-21758, 5b -->


<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## Adobe Managed CDN {#aem-managed-cdn}

<!-- CQDOC-21758, 5a -->

Cloud Manager의 셀프서비스 UI를 통해 AEM의 내장된 CDN을 사용하여 컨텐츠 전달을 준비하려면 Adobe의 관리 CDN 기능을 활용할 수 있습니다. 이 기능을 사용하면 DV(도메인 유효성 검사) 또는 EV/OV(확장/조직 유효성 검사) 인증서와 같은 SSL 인증서 구성 및 설치를 포함하여 셀프서비스 CDN 관리를 처리할 수 있습니다. 이러한 메서드에 대한 자세한 내용은 다음을 참조하십시오.

* [Cloud Manager의 Edge Delivery Services](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)
* [사용자 정의 도메인 이름 소개](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
* [SSL 인증서 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)
* [CDN 구성](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md)

**트래픽 제한**

기본적으로 AEM 관리 CDN 설정의 경우 모든 공개 트래픽은 프로덕션 및 비프로덕션(개발 및 스테이징) 환경 모두에 대해 게시 서비스로 이동할 수 있습니다. Cloud Manager 사용자 인터페이스를 통해 특정 환경에 대한 게시 서비스로 트래픽을 제한할 수 있습니다(예: IP 주소 범위별로 스테이징 제한).

자세한 내용은 [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)를 참조하십시오.

>[!CAUTION]
>
>AEM의 관리 CDN은 허용된 IP의 요청만 처리합니다. 자체 CDN을 AEM 관리 CDN으로 지정하는 경우 CDN의 IP가 IP 허용 목록에 포함되어 있는지 확인합니다.

### CDN에서 트래픽 구성 {#cdn-configuring-cloud}

CDN에서 트래픽을 다음과 같은 다양한 방법으로 구성할 수 있습니다.

* [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)(선택적으로 라이선스가 부여된 고급 WAF 규칙 포함)으로 악성 트래픽 차단
* [요청 및 응답](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)의 특성 수정
* 301/302 [클라이언트측 리디렉션 적용](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)
* AEM이 아닌 백엔드에 대한 요청을 리버스 프록시로 전환하도록 [원본 선택기](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) 선언

Git의 YAML 파일을 사용하여 이러한 기능을 구성합니다. Cloud Manager [구성 파이프라인](/help/implementing/dispatcher/cdn-configuring-traffic.md)을(를) 사용하여 배포하십시오.

### CDN 오류 페이지 구성 {#cdn-error-pages}

CDN 오류 페이지를 구성하여 기본 브랜드가 지정되지 않은 페이지를 바꿀 수 있습니다. 이 사용자 지정 페이지는 AEM을 사용할 수 없는 드문 이벤트에 표시됩니다. 자세한 내용은 [CDN 오류 페이지 구성](/help/implementing/dispatcher/cdn-error-pages.md)을 참조하십시오.

### CDN에서 캐시된 콘텐츠 제거 {#purge-cdn}

HTTP Cache-Control 헤더를 사용하여 TTL을 설정하는 것은 콘텐츠 게재 성능과 콘텐츠 신선도의 균형을 맞추는 효과적인 방법입니다. 그러나 업데이트된 콘텐츠를 즉시 제공하는 것이 중요한 시나리오에서는 CDN 캐시를 직접 제거하는 것이 유용할 수 있습니다.

[제거 API 토큰 구성](/help/implementing/dispatcher/cdn-credentials-authentication.md/#purge-API-token) 및 [캐시된 CDN 콘텐츠 제거](/help/implementing/dispatcher/cdn-cache-purge.md)에 대해 읽어 보십시오.

### CDN에서의 기본 인증 {#basic-auth}

비즈니스 이해 관계자가 콘텐츠를 검토하는 등 가벼운 인증 사용 사례의 경우, 사용자 이름과 암호를 요구하는 기본 인증 대화 상자를 표시하여 콘텐츠를 보호하십시오. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md).

## 고객 관리 CDN은 AEM 관리 CDN에 지정 {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="고객 CDN(또는 프록시)은 AEM Managed CDN에 지정"
>abstract="AEM as Cloud Service는 고객이 기존 CDN을 사용할 수 있는 옵션을 제공합니다. 게시 계층의 경우 고객은 관리해야 할 자신의 CDN에서 지정할 수 있습니다(선택 사항). 이 시나리오는 중단할 수 없는 고객과 CDN 공급업체의 기존 통합을 포함하되 이에 국한되지 않고 특정 사전 요구 사항을 충족하는지에 따라 사례별로 지정됩니다."

고객이 기존 CDN(또는 로드 밸런서 또는 WAF과 같은 모든 종류의 역방향 프록시)을 사용해야 하는 경우, 이를 관리하고 AEM 관리 CDN을 가리키면 다음 사항이 충족됩니다.

* 고객은 교체해야 하는 기존 CDN이 있어야 합니다.
* 고객이 관리해야 합니다.
* 고객은 AEM as a Cloud Service에서 작동하도록 CDN을 구성할 수 있어야 합니다. 아래 표시된 구성 지침을 참조하십시오.
* 고객은 관련 문제가 발생할 경우 언제든지 연락할 수 있는 엔지니어링 CDN 전문가를 보유하고 있어야 합니다.
* 고객은 프로덕션으로 이동하기 전에 로드 테스트를 수행하고 성공적으로 통과해야 합니다.

구성 지침:

1. CDN을 Adobe CDN의 인그레스를 원본 도메인으로 지정합니다. 예: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`
1. SNI를 Adobe CDN의 인그레스로 설정합니다.
1. 호스트 헤더를 원본 도메인으로 설정합니다. 예: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. AEM에서 호스트 헤더를 확인할 수 있도록 `X-Forwarded-Host` 헤더를 도메인 이름으로 설정합니다. 예: `X-Forwarded-Host:example.com`.
1. `X-AEM-Edge-Key`을(를) 설정합니다. [이 문서](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value)에 설명된 대로 Cloud Manager 구성 파이프라인을 사용하여 값을 구성해야 합니다.

   * Adobe CDN이 요청 소스의 유효성을 검사하고 `X-Forwarded-*` 헤더를 AEM 애플리케이션에 전달할 수 있어야 합니다. 예를 들어 `X-Forwarded-For`은(는) 클라이언트 IP를 확인하는 데 사용됩니다. 따라서 `X-Forwarded-*` 헤더가 정확한지 확인하는 것은 신뢰할 수 있는 호출자(즉, 고객 관리 CDN)의 책임입니다(아래 참고 사항 참조).
   * 선택적으로, `X-AEM-Edge-Key`이(가) 없을 때 Adobe CDN 인그레스에 대한 액세스를 차단할 수 있습니다. Adobe CDN의 인그레스에 직접 액세스해야 하는 경우 Adobe에 알립니다(차단 예정).

주요 CDN 공급업체의 구성 예는 [샘플 CDN 공급업체 구성](#sample-configurations) 섹션을 참조하십시오.

라이브 트래픽을 수락하기 전에 Adobe 고객 지원 센터를 통해 종단 간 트래픽 라우팅이 올바르게 작동하는지 확인해야 합니다.

`X-AEM-Edge-Key`을(를) 설정한 후 요청이 다음과 같이 올바르게 라우팅되는지 테스트할 수 있습니다.

Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Windows에서는:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>자체 CDN을 사용하는 경우 Cloud Manager에 도메인 및 인증서를 설치할 필요가 없습니다. Adobe CDN의 라우팅은 기본 도메인 `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`을(를) 사용하여 수행되며, 이는 요청 `Host` 헤더에서 전송되어야 합니다. 요청 `Host` 헤더를 사용자 지정 도메인 이름으로 덮어쓰면 Adobe CDN을 통해 요청이 잘못 라우팅되거나 421 오류가 발생할 수 있습니다.

>[!NOTE]
>
>자체 CDN을 관리하는 고객은 AEM의 CDN으로 전송되는 헤더의 무결성을 보장해야 합니다. 예를 들어 고객이 모든 `X-Forwarded-*` 헤더를 지우고 알려진 값과 제어된 값으로 설정하는 것이 좋습니다. 예를 들어 `X-Forwarded-For`은(는) 클라이언트의 IP 주소를 포함해야 하지만 `X-Forwarded-Host`은 사이트의 호스트를 포함해야 합니다.

>[!NOTE]
>
>샌드박스 프로그램 환경은 고객이 제공한 CDN을 지원하지 않습니다.

고객 CDN과 AEM CDN 간의 추가 홉은 캐시 누락이 있는 경우에만 필요합니다. 이 문서에 설명된 캐시 최적화 전략을 사용하면 고객 CDN을 추가하면 무시할 수 있는 지연만 발생합니다.

이 고객 CDN 구성은 게시 계층에 대해 지원되지만 작성자 계층 앞에서는 지원되지 않습니다.

### 디버깅 구성

BYOCDN 구성을 디버깅하려면 값이 `edge=true`인 `x-aem-debug` 헤더를 사용합니다. 예:

Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -v -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>" -H "x-aem-debug: edge=true"
```

Windows에서는:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -v --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>" --header "x-aem-debug: edge=true"
```

이 프로세스는 `x-aem-debug` 응답 헤더의 요청에 사용된 특정 속성을 반영합니다. 예:

```
x-aem-debug: byocdn=true,edge=true,edge-auth=edge-auth,edge-key=edgeKey1,X-AEM-Edge-Key=set,host=publish-p87058-e257304-cmstg.adobeaemcloud.com,x-forwarded-host=wknd.site,adobe_unlocked_byocdn=true
```

이 프로세스에서는 호스트 값, 에지 인증 구성 및 x-forwarded-host 헤더 값과 같은 세부 정보를 확인할 수 있습니다. 또한 일치 항목이 존재하는 경우 에지 키가 설정되었는지 여부와 사용되는 키도 식별합니다.

### 샘플 CDN 공급업체 구성 {#sample-configurations}

다음은 여러 주요 CDN 공급업체의 몇 가지 구성 예입니다.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

### 일반적인 오류 {#common-errors}

제공된 샘플 구성은 필요한 기본 설정을 보여 줍니다. 하지만 고객 구성에는 AEM as a Cloud Service이 트래픽을 처리하는 데 필요한 헤더를 제거, 편집 또는 다시 정렬하는 다른 영향을 주는 규칙이 있을 수 있습니다. 다음은 AEM as a Cloud Service을 가리키도록 고객 관리 CDN을 구성할 때 발생하는 일반적인 오류입니다.

**게시 서비스 끝점으로 리디렉션**

요청이 403 금지된 응답을 수신하면 요청에 일부 필수 헤더가 누락되었음을 의미합니다. CDN이 Apex 및 `www` 도메인 트래픽을 모두 관리하고 있지만 `www` 도메인에 대한 올바른 헤더를 추가하지 않는 것이 일반적인 원인입니다. 이 문제는 AEM as a Cloud Service CDN 로그를 확인하고 필요한 요청 헤더를 확인하여 트리거할 수 있습니다.

**잘못된 리디렉션 오류 421**

`Requested host does not match any Subject Alternative Names (SANs) on TLS certificate` 메시지와 함께 421 오류가 발생하면 HTTP `Host`이(가) 인증서에 나열된 호스트와 일치하지 않습니다. 이 문제는 일반적으로 `Host` 또는 SNI 설정이 잘못되었음을 나타냅니다. `Host`과(와) SNI 설정이 모두 publish-p&lt;PROGRAM_ID>-e.adobeaemcloud.com 호스트를 가리켜야 합니다.

**리디렉션 루프가 너무 많음**

페이지에 &quot;너무 많은 리디렉션&quot; 루프가 발생하면 일부 요청 헤더가 강제로 자신에게 다시 돌아가는 리디렉션과 일치하는 CDN에 추가됩니다. 예:

* CDN 규칙은 apex 도메인 또는 www 도메인과 일치하도록 만들어지고 apex 도메인의 X-Forwarded-Host 헤더만 추가합니다.
* Apex 도메인에 대한 요청은 이 CDN 규칙과 일치하며, 이 규칙은 apex 도메인을 X-Forwarded-Host 헤더로 추가합니다.
* 리디렉션이 apex 도메인에 대해 호스트 헤더와 명시적으로 일치하는 원본(예: ^example.com)으로 요청이 전송됩니다.
* Apex 도메인에 대한 요청을 www 하위 도메인과의 https로 재작성하는 재작성 규칙이 트리거됩니다.
* 그런 다음 해당 리디렉션이 고객 에지로 전송되며, 여기서 CDN 규칙이 www 하위 도메인이 아닌 Apex 도메인에 대한 X-Forwarded-Host 헤더를 다시 추가하면서 트리거됩니다. 그런 다음 요청이 실패할 때까지 프로세스가 다시 시작됩니다.

이 문제를 해결하려면 SSL 리디렉션 전략, CDN 규칙, 리디렉션 및 다시 작성 규칙 조합을 평가합니다.

## 지리적 위치 헤더 {#geo-headers}

AEM 관리 CDN은 다음을 사용하여 각 요청에 헤더를 추가합니다.

* 국가 코드: `x-aem-client-country`
* 대륙 코드: `x-aem-client-continent`

>[!NOTE]
>
>고객 관리 CDN이 있는 경우 이러한 헤더는 실제 클라이언트가 아닌 고객의 CDN 프록시 서버의 위치를 반영합니다. 고객이 관리하는 CDN을 사용할 때는 고객이 자체 CDN을 통해 지리적 위치 헤더를 관리해야 합니다.

국가 코드 값은 [ISO 3166-1](https://ko.wikipedia.org/wiki/kr/ISO_3166-1)에 설명된 Alpha-2 코드입니다.

대륙 코드의 값은 다음과 같습니다.

* 아프리카
* 남극 대륙
* 아시아
* 유럽
* 나 북미
* 오세아니아
* 남아메리카

이 정보는 요청의 원본 국가를 기준으로 다른 URL로 리디렉션하는 데 유용합니다. 지역 정보에 따라 응답을 캐시하려면 Vary 헤더를 사용합니다. 예를 들어, 특정 국가 랜딩 페이지로 리디렉션하는 경우 항상 `Vary: x-aem-client-country`을(를) 포함해야 합니다. 필요한 경우 `Cache-Control: private`을(를) 사용하여 캐싱을 방지할 수 있습니다. [캐싱](/help/implementing/dispatcher/caching.md#html-text)도 참조하세요.
