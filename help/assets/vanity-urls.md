---
title: OpenAPI 기능이 있는 Dynamic Media를 사용하여 가상 URL 만들기
description: Dynamic Media OpenAPI 기능을 사용하여 긴 에셋 게재 URL을 짧은 브랜드 vanity URL로 변환합니다. 별칭 URL은 복잡한 게재 URL의 짧고, 깨끗하고, 기억하기 쉽고, 읽기 쉬운 버전입니다. vanity URL에 브랜드 이름, 제품 이름 및 관련 키워드를 포함하여 브랜드 가시성과 사용자 참여를 높일 수 있습니다
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 54c592e4db4cbaa884e298cc5e81115cd5573b28
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 0%

---


# 별칭 URL 사용{#vanity-urls}

[!DNL Dynamic Media OpenAPI capabilities]을(를) 사용하여 긴 자산 게재 URL을 짧은 브랜드 별칭 URL로 변환합니다. 표준 에셋 배달 URL에는 배달 URL을 복잡하게 만들고 기억하고 공유하기 어려운 시스템 생성 에셋 UUID가 포함됩니다. 이러한 자산 UUID를 단순 식별자(Vanity ID)로 대체하여 vanity URL을 생성합니다. 별칭 URL은 복잡한 게재 URL의 짧고 깨끗하며 읽기 쉬운 버전입니다.

차이점을 파악하려면 다음 URL 형식을 참조하십시오.
* [표준 게재 URL](#standard-urls)
* [별칭 URL](#vanity-url)

표준 게재 URL은 `aaid` 다음에 UUID가 사용되지만 vanity URL은 `avid` 다음에 사용자 지정 식별자(vanity identifier)가 사용됩니다.

짧고 간단한 단축 식별자를 사용하여 게재 URL을 짧고, 깔끔하고, 읽을 수 있고, 기억하기 쉽고, 공유할 수 있도록 합니다. 브랜드 이름, 제품 이름 및 관련 키워드를 단축 ID로 사용하여 브랜드 가시성 및 사용자 참여를 높이십시오.

사용자가 vanity URL을 클릭하면 [!DNL Dynamic Media with OpenAPI]이(가) 수집 시 원본 자산 위치에 자동으로 매핑되고 전달 시 자산을 사용자에게 서버로 보내는 데 올바르게 확인됩니다.

[가상 URL을 만드는 방법](#create-vanity-urls)을 알아보세요.

## 표준 게재 URL{#standard-urls}

표준 [!DNL Dynamic Media with OpenAPI] 자산 배달 URL에는 시스템에서 생성한 고유 식별자가 포함되어 있으며, 다음 형식을 따릅니다.

***형식:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:aaid:aem:<asset-uuid>/as/<seoname>.<format>`

표준 게재 URL에는 `aaid` 뒤의 *(*&#x200B;실제 자산 식별자`urn:`)과 `urn:aaid:aem:`에서 `/as/<seoname>.<format>` 사이의 UUID가 포함됩니다.

***예:*** `https://delivery-p30902-e145436.adobeaemcloud.com/adobe/assets/urn:aaid:aem:43341ab1-4086-44d2-b7ce-ee546c35613b/as/check.jpeg`

위의 예에서 `43341ab1-4086-44d2-b7ce-ee546c35613b`은(는) UUID입니다.

## 별칭 URL{#vanity-url}

vanity URL은 에셋 UUID 대신 vanity 식별자를 포함하며 다음 형식을 따릅니다.

***형식:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/as/<seoname>.<format>`

별칭 URL에는 `avid` 다음의 *(*&#x200B;실제 별칭 식별자`urn:`)과 `urn:avid:aem:`에서 `/<seoname>.<format>` 사이의 별칭 ID가 포함됩니다.

***예:*** `https://delivery-p30902-e145436.adobeaemcloud.com/adobe/assets/urn:avid:aem:VanityCheck/as/check.jpeg`

위의 예에서 `VanityCheck`은(는) UUID를 대체한 vanity ID입니다.

## 주요 기능 및 이점 살펴보기{#capabilities-and-benefits-of-vanity-urls}

의미 있는 단축 ID를 사용하여 표준 자산 게재 URL을 사용자 지정하면 몇 가지 이점이 있고 측정 가능한 영향이 제공됩니다. vanity URL의 주요 기능 및 이점 중 일부는 다음과 같습니다.

### 주요 기능{#key-capabilities}

* **URL 사용자 지정:** 배달 URL의 긴 식별자(자산 UUID)를 더 짧은 브랜드 정렬 대체 요소로 바꾸어 더 깨끗한 배달 URL을 생성합니다.
* **실시간 리디렉션:** Vanity URL이 워크플로를 중단하지 않고 런타임에 원본 에셋 UUID로 리디렉션됩니다. 시스템이 기술 라우팅을 처리하는 동안 주소 표시줄에 클린 URL이 표시됩니다.
* **간편한 링크 관리:** 자산 전달 성능에 영향을 주지 않고 언제든지 vanity URL을 사용자 지정합니다.

### 주요 이점{#key-benefits}

* **사용자 환경 개선:** 깔끔하고 짧은 vanity URL을 읽을 수 있고 사용자에게 친숙하며 기억하기 쉽고 공유하기 쉽습니다.

* **사용자 참여를 개선합니다.** 브랜드 URL은 사용자 신뢰도와 신뢰를 구축합니다. 사용자는 전문적인 브랜드 링크를 클릭할 가능성이 높으므로 클릭스루 비율이 높아집니다.

* **SEO 최적화:** 관련 키워드를 포함하는 URL은 검색 엔진 순위 및 검색 기능을 개선합니다.

* **향상된 브랜드 가시성:** 브랜드별 URL은 이메일, 소셜 미디어 및 광고 캠페인을 포함하여 모든 마케팅 채널에서 브랜드 존재를 강화합니다.
또한 모든 통신에서 브랜드 URL을 일관되게 사용하면 브랜드 정체성과 인식이 강화됩니다.

* **캠페인 추적 및 분석:** 다양한 캠페인 및 채널에 대해 고유한 vanity URL을 사용하여 트래픽 소스 및 전환 성능에 대한 자세한 통찰력을 얻으십시오.

## 사전 요구 사항{#prerequisites-for-creating-vanity-id}

vanity URL을 만들려면 이미 [공개 게재용 자산을 승인](/help/assets/manage-organize-assets-view.md#manage-asset-status)했는지 확인하십시오.

## 별칭 URL 만들기{#create-vanity-urls}

vanity URL을 만들려면 다음 단계를 수행하십시오.
1. [에셋 메타데이터 설정](#set-up-asset-metadata)
1. [Cloud Manager 환경 변수 생성 및 매핑](#map-cloud-manager-environment-variable)
1. [게재할 별칭 URL이 필요한 자산 승인](/help/assets/manage-organize-assets-view.md#manage-asset-status)
1. [별칭 URL 생성](#generate-vanity-urls)

### 에셋 메타데이터 설정{#set-up-asset-metadata}

다음을 실행하여 자산의 메타데이터 양식에서 vanity ID를 설정합니다.
1. [!DNL Dynamic Media with OpenAPI] 게재를 위해 에셋을 포함하는 폴더의 세부 정보 페이지로 이동합니다.
1. 다음 중 하나를 수행하여 [해당 메타데이터 양식을 편집](/help/assets/metadata-assets-view.md#edit-metadata-forms)합니다.
   * 새 메타데이터 필드를 추가하고 필수 vanity ID를 해당 필드의 값으로 지정합니다.
   * 기존 메타데이터 속성 값을 필수 vanity ID로 대체하여 기존 필드를 업데이트합니다. vanity ID를 만들기 위한 [모범 사례](#best-practices)를 알아봅니다.
     ![별칭 ID](/help/assets/assets/vanity-id-metadata.png)
[메타데이터 스키마](/help/assets/metadata-schemas.md)에 대해 자세히 알아보세요.

     >[!NOTE]
     >
     > * 각 에셋에 대해 고유한 단축 ID를 사용합니다. 항상 동일한 메타데이터 양식을 공유하는 에셋에 vanity URL을 통해 OpenAPI를 제공하는 DM에 대한 고유한 vanity ID가 있는지 확인하십시오. 두 에셋이 동일한 vanity ID를 공유하는 경우 OpenAPI가 있는 DM은 해당 ID를 가장 최근에 받은 에셋을 전달하여 ID의 이전 권한을 다른 에셋으로 재정의합니다.
     >
     > * 단일 자산에는 여러 단축 ID가 있을 수 있습니다. [Adobe 지원에 문의](https://helpx.adobe.com/in/contact.html)하여 필요한 vanity ID 생성을 요청합니다.

자산 메타데이터 양식에서 별칭 ID를 설정한 후 [이 메타데이터 필드를 시스템의 게재 메커니즘에 매핑](#map-cloud-manager-environment-variable)합니다.

### Cloud Manager 환경 변수 생성 및 매핑{#map-cloud-manager-environment-variable}

다음 단계를 실행하여 환경 변수를 만들고 vanity ID가 있는 메타데이터 필드에 매핑합니다.

1. [Cloud Manager 환경의 구성 페이지로 이동](/help/implementing/cloud-manager/environment-variables.md)한 후 다음을 수행합니다.
   1. `ASSET_DELIVERY_VANITY_ID` 변수를 추가합니다. 이것이 열쇠입니다.
   1. 값 필드를 사용하여 vanity ID를 보유하는 메타데이터 속성에 매핑합니다. 매핑은 `dc:<your-metadata-property>` 형식을 따릅니다. 여기서 메타데이터 매핑 접두사(예: dc:)는 메타데이터 구성 속성에 따라 달라집니다.
      ![ASSET_DELIVERY_VANITY_ID 변수](/help/assets/assets/environment-config.png)
1. 변경 사항을 저장하여 환경에서 Pod를 다시 시작합니다.

### 게재할 자산 승인{#approve-assets-for-delivery}

Cloud Manager 환경의 `ASSET_DELIVERY_VANITY_ID` 변수를 vanity ID가 있는 자산 메타데이터 속성에 매핑한 후 [게재할 vanity URL이 필요한 자산을 승인](/help/assets/manage-organize-assets-view.md#manage-asset-status)합니다.

### 별칭 URL 생성{#generate-vanity-urls}

표준 게재 URL에서 다음과 같이 대체하여 vanity URL로 변환합니다.

* **UUID**&#x200B;을(를) **vanity ID**(으)로 바꾸십시오.
* `aaid`에서 `avid`(으)로 바꾸기

표준 URL에서 가상 URL로의 [URL 변환](#standard-urls)을 참조하십시오.
에셋에 대해 [OpenAPI 배달 URL을 사용하여 Dynamic Media를 복사](/help/assets/approve-assets.md#copy-delivery-url-for-approved-assets)하는 방법을 알아봅니다.

사용자가 vanity URL을 클릭하면 [!DNL Dynamic Media with OpenAPI]이(가) 수집 시 vanity ID를 원래 자산 UUID에 자동으로 매핑하고 배달 시 올바르게 확인하여 지연 없이 사용자에게 자산을 제공합니다. 자산 전달 성능에 영향을 주지 않고 실시간으로 vanity URL을 사용자 지정할 수 있습니다.

[AEM Cloud Service의 고급 사용자 지정 기능을 사용하여 vanity URL의 영향을 개선합니다.](#scale-using-vanity-url)

## vanity URL을 사용하여 크기 조정{#scale-using-vanity-url}

AEM as a Cloud Service을 사용하면 웹 주소 내에서 [DNS 및 CDN 이름을 사용자 지정](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/introduction)할 수 있습니다. 이러한 AEMCS 기능을 단축 URL과 함께 사용하면 AEMCS를 깔끔하고 설명적이며 브랜드가 지정되고 직관적이며 [위에서 언급한 이점](#key-benefits)을 제공하는 고유한 웹 주소로 변환할 수 있습니다.

다음 vanity URL 및 사용자 지정 가능한 구성 요소를 참조하십시오.

**가상 URL 형식:**

`https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/as/<seoname>.<format>`

<table style="border-collapse:collapse; table-layout:auto; width:auto;">
<tr valign="top">
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>https://delivery&#8209;&lt;tenant&gt;.adobeaemcloud.com</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#customize-dns">이 DNS 사용자 지정</a></div>
</td>
<td style="padding:0 6px; white-space:nowrap; text-align:center;">/</td>
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>adobe/assets/urn:avid:aem:</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#rewrite-cdn-rules">다시 작성 규칙으로 URL 사용자 지정</a></div>
</td>
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>&lt;vanity-id&gt;</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#create-vanity-urls">가상 ID 만들기</a></div>
</td>
<td style="padding:0 4px; white-space:nowrap; text-align:left; width:1%;">
<code>/as/&lt;seoname&gt;.&lt;format&gt;</code>
</td>
</tr>
</table>

**사용자 지정된 DNS 및 CDN 이름이 있는 별칭 URL 형식:**

`https://<custom-dns>` `/` `dam/assets/` `<vanity-id>` `/as/<seoname>.<format>`

**사용자 지정 URL 구성 요소**

* ***[DNS 이름(호스트 이름):](#customize-DNS)*** `https://delivery-<tenant>.adobeaemcloud.com`은(는) 자산을 호스팅하는 서버 도메인입니다. [호스트 이름을 변경하려면 DNS를 사용자 지정](#customize-DNS)합니다.
* ***[CDN 다시 쓰기 규칙:](#rewrite-cdn-rules)*** `adobe/assets/urn:avid:aem:`은(는) 자산 유형 및 게재 방법을 식별하는 경로 구조입니다. 도메인 경로를 수정하려면 [CDN 규칙을 다시 작성](#rewrite-cdn-rules)하십시오.

### DNS 사용자 지정{#customize-dns}

[Adobe 지원에 요청](https://helpx.adobe.com/in/contact.html)하여 게재 계층에 필요한 사용자 지정 DNS를 생성합니다. 사용자 지정 DNS 이름을 만들려면 다음 [모범 사례](#best-practices)를 따르십시오.

### CDN 규칙 다시 작성{#rewrite-cdn-rules}

다음 단계를 실행하여 전송할 CDN 규칙을 다시 작성합니다.

1. AEM 저장소로 이동하여 YAML 구성 파일을 생성합니다.
2. [설정](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-error-pages#setup) 섹션의 단계를 실행하여 CDN 규칙을 구성하고 Cloud Manager 구성 파이프라인을 통해 구성을 배포합니다.
도메인 경로를 만들려면 다음 [모범 사례](#best-practices)를 따르십시오.
   [CDN 재작성 규칙에 대해 자세히 알아보세요](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#request-transformations).

다음은 vanity URL에 확장자가 있는 파일 이름을 추가하기 위한 규칙 재작성 예입니다. 특정 요구 사항에 따라 이러한 재작성 규칙을 사용자 정의합니다. 추가 지원이 필요하면 [Adobe 지원 팀에 문의](https://helpx.adobe.com/in/contact.html):

```- name: cdn-rewrite-rule
  when:
    allOf:
      - reqProperty: tier
        equals: delivery
```

#### SVG, GIF 및 PDF의 경우 {#svg-gif-pdf}

```
    type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:svg|gif|pdf|docx|xlsx))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/original/as/\1\2
```

#### 비디오용{#video}

MP4, MOV, AVI 및 MKV를 포함한 비디오

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:mp4|mov|avi|mkv))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/play\2
```

#### 이미지용{#image}

SVG을 제외한 모든 이미지 유형의 경우.

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.[^/]+)(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/as/\1\2
```

## 깔끔한 vanity URL을 만들기 위한 모범 사례를 따르십시오{#best-practices}

vanity ID, 사용자 지정 DNS 및 도메인 이름을 만들려면 다음 모범 사례를 따르십시오.

1. vanity ID에는 공백, 슬래시, 하이픈 등과 같은 특수 문자를 사용하지 마십시오. 사전 정의된 매핑을 사용하여 단축 ID의 특수 문자가 바뀝니다.
1. vanity ID, 사용자 정의 DNS 및 도메인 이름에서 브랜드 이름, 제품 이름 및 관련 키워드를 사용하여 브랜드 가시성 및 사용자 참여를 높이십시오.
1. 의미를 전달하는 짧고 설명적인 단어나 문자열을 사용합니다.
1. 클릭에 사용자를 초대하는 텍스트를 사용합니다.
