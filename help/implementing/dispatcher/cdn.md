---
title: AEM as a Cloud Service의 CDN
description: AEM as a Cloud Service의 CDN
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: 95ec89fa4bb71a63121bc86a74a15cc7812ae342
workflow-type: tm+mt
source-wordcount: '1163'
ht-degree: 8%

---

# AEM as a Cloud Service의 CDN {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="AEM as a Cloud Service의 CDN"
>abstract="Cloud Service으로 AEM이 기본 CDN과 함께 제공됩니다. 주요 목적은 브라우저 근처 가장자리에 CDN 노드에서 캐시 가능 컨텐츠를 전달하여 지연 시간을 줄이는 것입니다. AEM 애플리케이션 최적의 성능을 위해 완벽하게 관리 및 구성됩니다."

Cloud Service으로 AEM이 기본 CDN과 함께 제공됩니다. 주요 목적은 브라우저 근처 가장자리에 CDN 노드에서 캐시 가능 콘텐츠를 전달하여 지연 시간을 줄이는 것입니다. AEM 애플리케이션 최적의 성능을 위해 완벽하게 관리 및 구성됩니다.

AEM 관리 CDN은 대부분의 고객의 성능 및 보안 요구 사항을 충족합니다. 게시 계층의 경우 고객이 선택적으로 자신의 CDN에서 가리키도록 할 수 있으며, 이를 관리해야 합니다. 중단하기 어려운 CDN 공급업체와 레거시 통합을 보유한 고객을 포함한 특정 전제 조건을 충족하는 것에 제한되지 않고, 이를 기반으로 케이스별로 허용됩니다.

다음 비디오도 참조하십시오 [Cloud 5 AEM CDN 1부](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) 및 [Cloud 5 AEM CDN 2부](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) 를 참조하십시오.

## AEM 관리 CDN  {#aem-managed-cdn}

Cloud Manager 셀프 서비스 UI를 사용하여 기본 제공 CDN을 사용하여 컨텐츠 전달을 준비하려면 아래 섹션을 따르십시오.

1. [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [사용자 정의 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

>[!NOTE]
>
>사용자 지정 도메인은 Cloud Manager에서 지원됩니다 **전용** AEM 관리 CDN을 사용하는 경우. CDN을 가져와서 [AEM 관리 CDN에 가리키기](#point-to-point-CDN) 해당 특정 CDN을 사용하여 Cloud Manager가 아닌 도메인을 관리해야 합니다.

**트래픽 제한**

기본적으로 AEM 관리 CDN 설정의 경우 모든 공용 트래픽은 프로덕션 및 비프로덕션(개발 및 스테이지) 환경 모두에 대해 게시 서비스로 이동할 수 있습니다. 지정된 환경에 대한 게시 서비스로 트래픽을 제한하려는 경우(예: IP 주소 범위에 따라 스테이징을 제한하는) Cloud Manager UI를 통해 셀프 서비스 방식으로 이 작업을 수행할 수 있습니다.

자세한 내용은 [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)를 참조하십시오.

>[!CAUTION]
>
>허용되는 IP의 요청만 AEM 관리 CDN에 의해 제공됩니다. 고유한 CDN을 AEM 관리 CDN에 연결하는 경우 CDN의 IP가에 포함되어 있는지 허용 목록에 추가하다 확인합니다.

## 고객 CDN은 AEM Managed CDN을 가리킵니다 {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="고객 CDN은 AEM Managed CDN을 가리킵니다"
>abstract="AEM as Cloud Service은 고객이 기존 CDN을 사용할 수 있는 옵션을 제공합니다. 게시 계층의 경우 고객이 선택적으로 자신의 CDN에서 가리키도록 할 수 있으며, 이를 관리해야 합니다. 중단하기 어려운 CDN 공급업체와 레거시 통합을 보유한 고객을 포함한 특정 전제 조건을 충족하는 것에 제한되지 않고, 이를 기반으로 케이스별로 허용됩니다."

고객이 기존 CDN을 사용해야 하는 경우 다음을 충족하는 것을 제공하여 고객이 CDN을 관리하고 AEM 관리 CDN을 가리킬 수 있습니다.

* 고객은 교체해야 하는 번거로운 기존 CDN이 있어야 합니다.
* 고객이 관리해야 합니다.
* 고객은 AEM as a Cloud Service에서 작동하도록 CDN을 구성할 수 있어야 합니다. 아래 표시된 구성 지침을 참조하십시오.
* 고객은 관련 문제가 발생할 경우 호출되는 엔지니어링 CDN 전문가가 있어야 합니다.
* 고객은 프로덕션으로 이동하기 전에 로드 테스트를 수행하고 성공적으로 통과해야 합니다.

구성 지침:

1. CDN을 Adobe CDN의 주소를 원래 도메인으로 가리킵니다. (예: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`)
1. SNI는 Adobe CDN의 수신로도 설정되어야 합니다.
1. 호스트 헤더를 원본 도메인으로 설정합니다. 예: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. 설정 `X-Forwarded-Host` 헤더에 사용할 수 있습니다. 예: `X-Forwarded-Host:example.com`.
1. 설정 `X-AEM-Edge-Key`. 값은 Adobe에서 가져와야 합니다.

   * Adobe CDN이 요청 소스의 유효성을 확인하고 를 전달할 수 있도록 필요합니다 `X-Forwarded-*` 헤더 를 AEM 애플리케이션에 추가합니다. 예,`X-Forwarded-For` 클라이언트 IP를 확인하는 데 사용됩니다. 따라서 는 신뢰할 수 있는 호출자(즉, 고객 관리 CDN)의 책임이 되므로 `X-Forwarded-*` header(아래 참고 참조).
   * 선택적으로, `X-AEM-Edge-Key` 이 없습니다. Adobe CDN 수신(차단하려면)에 직접 액세스해야 하는 경우 Adobe에 알려주십시오.

자세한 내용은 [샘플 CDN 공급업체 구성](#sample-configurations) 주요 CDN 공급업체의 구성 예에 대한 섹션을 참조하십시오.

라이브 트래픽을 수락하기 전에 엔드 투 엔드 트래픽 라우팅이 올바르게 작동하는지 Adobe의 고객 지원 센터에서 확인해야 합니다.

를 가져온 후 `X-AEM-Edge-Key`를 설정하는 경우, 요청이 다음과 같이 올바르게 라우팅되는지 테스트할 수 있습니다.

Linux의 경우:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Windows에서:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>고유한 CDN을 사용하는 경우 Cloud Manager에 도메인 및 인증서를 설치할 필요가 없습니다. CDN Adobe의 라우팅은 기본 도메인을 사용하여 수행됩니다 `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.

>[!NOTE]
>
>자체 CDN을 관리하는 고객은 AEM CDN으로 전송되는 헤더의 무결성을 보장해야 합니다. 예를 들어, 고객이 모두 지우는 것이 좋습니다 `X-Forwarded-*` 헤더를 설정하고 이를 알려진 및 제어 값으로 설정합니다. 예, `X-Forwarded-For` 는 클라이언트의 IP 주소를 포함해야 하는 반면, `X-Forwarded-Host` 에는 사이트의 호스트가 포함되어야 합니다.

>[!NOTE]
>
>샌드박스 프로그램 환경은 고객이 제공하는 CDN을 지원하지 않습니다.

고객 CDN과 AEM CDN 간의 추가 홉은 캐시 누락 경우에만 필요합니다. 이 문서에 설명된 캐시 최적화 전략을 사용하여 고객 CDN을 추가하면 지연 시간이 거의 발생하지 않습니다.

이 고객 CDN 구성은 게시 계층에 대해 지원되지만 작성 계층 앞에는 있지 않습니다.

### 샘플 CDN 공급업체 구성 {#sample-configurations}

아래에 나와 있는 예는 여러 주요 CDN 공급업체의 몇 가지 구성 예입니다.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

## 컨텐츠 처리 {#content-disposition}

게시 계층의 경우 BLOB 제공 기본값은 첨부 파일로 사용됩니다. 이 값은 표준을 사용하여 대체할 수 있습니다 [콘텐츠 처리 헤더](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Disposition) 참조하십시오.

다음은 구성이 어떻게 표시되어야 하는지에 대한 예입니다.

```
<LocationMatch "^\/content\/dam.*\.(pdf).*">
 Header unset Content-Disposition
 Header set Content-Disposition inline
</LocationMatch>
```

## 지리적 위치 헤더 {#geo-headers}

AEM 관리 CDN은 다음을 사용하여 각 요청에 헤더를 추가합니다.

* 국가 코드: `x-aem-client-country`
* 대륙 코드: `x-aem-client-continent`

>[!NOTE]
>
>고객 관리 CDN의 경우 이러한 헤더는 실제 클라이언트가 아닌 고객 CDN 프록시 서버의 위치를 반영합니다.  따라서 고객 관리 CDN의 경우 지리적 위치 헤더를 고객 CDN에서 관리해야 합니다.

국가 코드 값은 설명된 알파-2 코드입니다 [여기](https://en.wikipedia.org/wiki/ISO_3166-1).

대륙 코드 값은 다음과 같습니다.

* AF 아프리카
* 남극
* 아시아
* 유럽 연합
* 북미
* OC 오세아니아
* SA 남아메리카

이 정보는 요청의 원본(국가)을 기준으로 다른 URL로 리디렉션하는 등의 사용 사례에 유용할 수 있습니다. 지역 정보에 종속되는 응답을 캐시하려면 Vary 헤더를 사용합니다. 예를 들어, 특정 국가 랜딩 페이지로의 리디렉션은 항상 을 포함해야 합니다 `Vary: x-aem-client-country`. 필요한 경우 `Cache-Control: private` 캐싱 방지 참조 - [캐싱](/help/implementing/dispatcher/caching.md#html-text).
