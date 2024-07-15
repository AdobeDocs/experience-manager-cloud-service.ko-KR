---
title: Content Hub 개요
description: Content Hub, 주요 이점, 액세스 방법, Content Hub에서 사용할 수 있는 옵션에 대한 피드백을 제공하는 방법에 대해 자세히 알아보십시오.
source-git-commit: 7224cca950e61bea298f246245bdb221fd8fa22e
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 6%

---


# Content Hub 개요 {#overview-content-hub}

![Content Hub 개요](assets/content-hub-overview.png)

Content Hub는 Experience Manager Assets as a Cloud Service의 일부로 제공되며, 이를 통해 조직과 비즈니스 파트너는 브랜드 콘텐츠를 더 간편하게 이용할 수 있습니다. 대규모로 활성화할 수 있도록 자산을 배포하고 마케팅 민첩성을 향상시키기 위한 온브랜드 콘텐츠 변형을 만드는 데 중점을 둡니다.

## 왜 Content Hub?

Content Hub은 다음과 같은 주요 이점을 제공합니다.

**직관적인 포털에서 사용할 수 있는 브랜드 승인 에셋을 모두 찾아 공유**

AEM Assets은 신뢰할 수 있는 단일 소스 역할을 하며 검색 환경을 개선하기 위해 모든 승인된 에셋을 Content Hub에서 플랫 계층 구조로 자동으로 사용할 수 있습니다.

**구성 가능한 사용자 인터페이스**

검색을 위한 필터, 에셋을 추가하거나 가져오는 동안 사용할 수 있는 필드, 에셋 속성, 브랜딩을 위한 배너 콘텐츠와 같은 Content Hub 내의 가장 일반적인 속성을 구성할 수 있으며 관리자는 요구 사항에 따라 Content Hub 사용자 인터페이스를 쉽게 구성할 수 있습니다.

**브랜드를 사용하는 동안 크리에이티브 이외의 사용자에게 콘텐츠를 편집하고 다시 혼합할 수 있는 권한을 부여합니다**

Content Hub을 사용하면 Adobe Express으로 새 컨텐츠를 만들 수 있습니다(Adobe Express 권한이 있는 경우). 사용하기 쉬운 도구로 기존 콘텐츠를 편집하고, 템플릿 및 브랜드 요소를 사용하여 브랜드 내 변형을 작성하고, Adobe Firefly의 최신 GenAI 기능을 사용하여 새 콘텐츠를 만들 수 있습니다.

**팀 간에 콘텐츠를 사용하는 방법에 대한 통찰력을 얻으십시오**

[!DNL Content Hub]은(는) 마케팅 캠페인, 채널 및 다른 지역에서 사용되는 자산 사용 통계와 같이 마케팅 이해 당사자가 자주 직면하는 일반적인 문제를 해결하면서 자산에 대한 중요한 통찰력을 제공합니다. 에셋의 성능과 인기를 명확하게 이해함으로써 사용자 경험을 개선하는 데 필수적인 실행 가능한 통찰력을 제공합니다.

## 사전 요구 사항 {#prerequisites-content-hub}

Content Hub에는 프로덕션 환경인 Experience Manager as a Cloud Service, 2024.6 릴리스 이상이 필요합니다(최소 버전은 2024.6.16799).

## Content Hub에 액세스하는 방법 {#access-content-hub}

[Content Hub을 설정하고](/help/assets/deploy-content-hub.md)사용자를 [Content Hub 제품 프로필](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile)에 추가한 후 다음과 같은 방법으로 Content Hub에 액세스할 수 있습니다.

* 다음 링크를 사용하여 Content Hub에 액세스합니다.

  `https://experience.adobe.com/#/assets/contenthub`

* experience.adobe com에 로그온하여 **[!UICONTROL 빠른 액세스]** 섹션에서 사용할 수 있는 **[!UICONTROL Experience Manager Assets Content Hub]**을(를) 클릭합니다.
  ![Content Hub 액세스](assets/access-content-hub.png)

* experience.adobe com에 로그온하고 제품 전환기에서 사용할 수 있는 **[!UICONTROL Experience Manager Assets Content Hub]**을(를) 클릭합니다.
  ![Content Hub 액세스 메서드 3](assets/access-content-hub-alternate.png)



## Content Hub 피드백 제공 {#provide-content-hub-feedback}

제품 관련 개선 사항을 추천하려면 Content Hub 사용자 인터페이스 상단의 조직 이름 옆에 있는 **[!UICONTROL 피드백]**&#x200B;을 클릭하세요.

제목, 권장 사항에 대한 설명을 지정하고 필요한 경우 파일을 첨부합니다. 피드백을 Adobe에 제출하려면 **[!UICONTROL 제출]**&#x200B;을 클릭하세요.

![Content Hub 피드백](assets/content-hub-feedback.png)

## 팀에 대한 Content Hub 설정 {#setup-content-hub}

팀을 위한 Content Hub을 설정하려면 다음 단계를 따르십시오.

1. [Cloud Manager을 사용하여 Experience Manager Assets용 Content Hub을 사용하도록 설정](deploy-content-hub.md#enable-content-hub).

1. [Content Hub 관리자 온보딩](deploy-content-hub.md#onboard-content-hub-administrator).

1. [주요 Content Hub 사용자 추가](deploy-content-hub.md#onboard-content-hub-consumer-users).

1. [Experience Manager 자산을 사용하여 자산을 승인할 DAM 작성자 또는 관리자](approve-assets.md).

1. [관리자가 다른 사용자를 위해 Content Hub 사용자 인터페이스를 구성할 수 있습니다](configure-content-hub-ui-options.md).

1. [팀에서 더 많은 사용자에게 Content Hub 액세스 권한을 부여합니다](deploy-content-hub.md#onboard-content-hub-consumer-users).

1. [Content Hub 포털에 액세스](#access-content-hub).

1. [Content Hub 피드백을 제공](#provide-content-hub-feedback).


## 주요 기능에 대해 자세히 알아보기 {#key-capabilities-content-module}

<table>
<td>
   <a href="/help/assets/configure-content-hub-ui-options.md">
   <img alt="Content Hub 배포" src="./assets/configure-assets.png" />
   </a>
   <div>
      <a href="/help/assets/configure-content-hub-ui-options.md">
      <strong>Content Hub 사용자 인터페이스 구성</strong>
      </a>
   </div>
   <p>
      <em>관리자가 Content Hub 사용자 인터페이스를 구성하는 방법을 알아봅니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-content-hub.md">
   <img alt="Content Hub에서 사용 가능한 자산 검색" src="./assets/search.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-content-hub.md">
      <strong>Content Hub에서 사용 가능한 자산 검색</strong>
      </a>
   </div>
   <p>
      <em>다양한 기능을 사용하여 검색 결과를 좁히는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/edit-images-content-hub.md">
   <img alt="Adobe Express를 사용하여 이미지 편집" src="./assets/edit-images-content-hub.png" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
      <strong>Adobe Express을 사용하여 이미지 편집</strong>
      </a>
   </div>
   <p>
      <em>Adobe Express을 사용하여 Content Hub에서 이미지의 변형을 만드는 방법을 알아봅니다</em>
   </p>
</td>
</table>
<table>
<td>
   <a href="/help/assets/share-assets-content-hub.md">
   <img alt="Content Hub에서 사용 가능한 에셋 공유" src="./assets/share-assets-banner.png" />
   </a>
   <div>
      <a href="/help/assets/share-assets-content-hub.md">
      <strong>Content Hub에서 사용 가능한 자산 공유</strong>
      </a>
   </div>
   <p>
      <em>하나 이상의 자산을 링크로 공유한 다음 액세스하는 방법에 대해 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/collections-content-hub.md">
   <img alt="Content Hub에서 컬렉션 관리" src="./assets/manage-collection.png" />
   </a>
   <div>
      <a href="/help/assets/collections-content-hub.md">
      <strong>Content Hub에서 컬렉션 관리</strong>
      </a>
   </div>
   <p>
      <em>에셋을 사용하여 컬렉션을 만든 다음 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Content Hub에서 사용 가능한 에셋 공유" src="./assets/asset-insights-banner.jpg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
      <strong>Content Hub에서 자산 통찰력 보기</strong>
      </a>
   </div>
   <p>
      <em> 콘텐츠 모듈은 마케팅 이해 당사자가 자주 직면하는 일반적인 문제를 해결하면서 자산에 대한 중요한 통찰력을 제공합니다.</em>
   </p>
</td>
</table>
