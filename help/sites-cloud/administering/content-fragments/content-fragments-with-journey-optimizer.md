---
title: Adobe Journey Optimizer에서 컨텐츠 조각 사용
description: 콘텐츠 조각을 Adobe Journey Optimizer과 통합하고 사용하는 방법에 대해 알아봅니다.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: 4090ee41-80f1-4389-8961-e4af891f01ff
source-git-commit: 0fd7b2633488ceb14d34b1978a91a3a830d8762a
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 10%

---

# Adobe Journey Optimizer를 사용한 콘텐츠 조각 {#content-fragments-with-journey-optimizer}

[Adobe Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)을(를) 통해 고객에게 연관성 있고 상황에 맞는 개인화된 경험을 제공할 수 있습니다. Adobe Experience Manager(AEM) as a Cloud Service을 Adobe Journey Optimizer(AJO)와 통합하면 웹, SMS, 이메일 등을 포함하여 AJO 인바운드 채널 및 AJO 아웃바운드 채널에서 AEM 콘텐츠를 재사용할 수 있습니다.

예를 들어 다음 작업을 수행할 수 있습니다.

* [AEM 콘텐츠 조각](/help/sites-cloud/administering/content-fragments/overview.md)을(를) [Journey Optimizer 이메일](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/email-landing-page) 콘텐츠에 원활하게 통합
* AEM에서 직접 AJO 경험 미리보기

컨텐츠 조각과 AJO을 연결하면 AEM 컨텐츠에 액세스하고 활용하는 프로세스가 간소화되어 개인화되고 동적인 캠페인 및 여정을 만들 수 있습니다.

자세한 내용은 AJO 설명서를 참조하십시오.

* [AJO에서 콘텐츠 조각 사용](https://experienceleague.adobe.com/docs/journey-optimizer/using/integrations/aem-fragments.html#integrations)
* [컨텐츠 조각과 AJO 오퍼 통합](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/managing-offers-in-the-offer-library/configure-offers/add-representations#urls)

## Dispatcher 구성 {#dispatcher-configuration}

AJO이 [콘텐츠 조각 관리 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)를 통해 AEM 콘텐츠 조각에 액세스할 수 있도록 하려면 Dispatcher을 구성해야 합니다.

* `dispatcher/src/conf.dispatcher.d/filters/filters.any`에서:

* 추가:

  ```xml
  # Allow Content Fragments API requests, required for integration with AJO 
  /200 {/type "allow" /url "/adobe/sites/cf/*" }
  ```

## 추가 정보 {#further-information}

자세한 내용은 다음을 참조하십시오.

* [AJO 외부 참조 확장](/help/sites-cloud/administering/content-fragments/extension-content-fragment-ajo-external-references.md)
