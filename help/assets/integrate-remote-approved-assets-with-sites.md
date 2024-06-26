---
title: AEM Sites과 원격 AEM Assets 통합
description: Creative Cloud에서 승인된 AEM Assets을 사용하여 AEM 사이트를 구성하고 연결하는 방법에 대해 알아봅니다.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# AEM Sites과 원격 AEM Assets 통합  {#integrate-approved-assets}

다양한 온라인 플랫폼에서 매력적이고 일관된 브랜드 경험을 제공하기 위해서는 디지털 에셋을 효과적으로 관리하는 것이 중요합니다. OpenAPI 기능이 포함된 Dynamic Media은 AEM Sites과 AEM Assets as a Cloud Service 간의 원활한 통합을 통해 디지털 자산 관리를 향상시킵니다. 이 혁신적인 기능을 사용하면 여러 AEM 환경에서 서로 다른 유형의 승인된 디지털 에셋을 쉽게 공유 및 관리할 수 있으므로 사이트 작성자 및 콘텐츠 편집자를 위한 워크플로를 간소화할 수 있습니다.

Dynamic Media의 OpenAPI 기능을 사용하면 사이트 작성자가 AEM 페이지 편집기 내에서 직접 원격 DAM의 자산을 사용할 수 있습니다. [컨텐츠 조각](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html), 콘텐츠 생성 및 관리 프로세스 단순화.

사용자는 최대 수에 대한 제한 없이 여러 AEM Sites 인스턴스를 원격 DAM 배포에 연결할 수 있으므로 [연결된 Assets](use-assets-across-connected-assets-instances.md) 기능.

![이미지](/help/assets/assets/connected-assets-rdam.png)

초기 설정 후 사용자는 AEM Sites 인스턴스에서 페이지를 만들고 필요에 따라 에셋을 추가할 수 있습니다. 에셋을 추가할 때 로컬 DAM에 저장된 에셋을 선택하거나 원격 DAM에서 사용할 수 있는 에셋을 찾아 사용할 수 있습니다.

OpenAPI 기능이 포함된 Dynamic Media은 컨텐츠 조각의 원격 자산 액세스 및 사용, 원격 자산의 메타데이터 가져오기 등과 같은 몇 가지 다른 이점을 제공합니다. 다른 항목에 대해 자세히 알아보기 [연결된 Assets에 대한 OpenAPI 기능을 갖춘 Dynamic Media의 이점](/help/assets/dynamic-media-open-apis-faqs.md).

## 시작하기에 앞서 {#pre-requisits-sites-integration}

* 다음 설정 [환경 변수](/help/implementing/cloud-manager/environment-variables.md#add-variables) AEM as a Cloud Service용:

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX` 는 프로그램 ID를 나타냅니다. <br>
     `eYYYY` 환경 ID를 참조합니다.

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId]

  또는 [OSGi 설정](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) 다음 단계에 따라 AEM Sites 인스턴스에서 AEM 6.5에 대해 설명합니다.

   1. 콘솔에 로그인하고 **[!UICONTROL OSGi] >** 또는 직접 URL을 사용하십시오. 예: `http://localhost:4502/system/console/configMgr`

   1. 추가 **[!UICONTROL 저장소 ID]**= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; 및 **[!UICONTROL ims 클라이언트]**= [IMSClientId]
자세히 알아보기 [IMS 인증](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

* 원격 DAM AEM as a Cloud Service 인스턴스에 로그인하기 위한 IMS 액세스

* 원격 DAM에서 OpenAPI 기능을 사용하는 Dynamic Media 토글을 켭니다.

* AEM Sites 인스턴스에서 이미지 v3 구성 요소를 구성합니다. 구성 요소가 없으면 을 다운로드하여 설치하십시오. [콘텐츠 패키지](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0).

## 원격 DAM에서 자산 액세스 {#fetch-assets}

OpenAPI 기능이 포함된 Dynamic Media을 사용하면 로컬 AEM Sites 페이지 편집기 및 AEM 콘텐츠 조각의 원격 DAM 인스턴스에서 사용할 수 있는 자산에 액세스할 수 있습니다.

![이미지](/help/assets/assets/open-APIs.png)

### AEM 페이지 편집기에서 원격 자산 액세스 {#access-assets-page-editor}

AEM Sites 인스턴스에서 AEM 페이지 편집기 내의 원격 자산을 사용하려면 아래 단계를 따르십시오. 이 통합은 AEM as a Cloud Service 및 AEM 6.5에서 수행할 수 있습니다.

1. 다음으로 이동 **[!UICONTROL 사이트]** > _웹 사이트_ AEM 위치 **[!UICONTROL 페이지]** 는 원격 자산을 추가해야 하는 내에 있습니다.
1. 특정 AEM으로 이동 **[!UICONTROL 페이지]** 웹 사이트 내 **[!UICONTROL 사이트]** 원격 자산을 추가할 섹션입니다.
1. 페이지를 선택하고 **[!UICONTROL 편집(_e_)]**. 더 AEM **[!UICONTROL 페이지 편집기]** 열림.
1. 레이아웃 컨테이너를 클릭하고 **[!UICONTROL 이미지]** 구성 요소.
1. 다음을 클릭합니다. **[!UICONTROL 이미지]** 구성 요소 및 클릭 ![설정 아이콘](/help/assets/assets/do-not-localize/settings-icon.svg) 아이콘.
1. 선택 취소 **[!UICONTROL 페이지에서 추천 이미지 상속]** 옵션을 선택합니다.
1. 클릭 **[!UICONTROL 선택]** 및 선택 **[!UICONTROL 원격]**.
   ![이미지](/help/assets/assets/uncheck-inherit-option.jpg)

   로그인하라는 메시지가 표시됩니다.
1. 에셋을 선택하고 **[!UICONTROL 선택]**.
1. 대체 텍스트를 추가하고 **[!UICONTROL 완료]**.
   <br> 원격 자산이 이미지 구성 요소에 나타납니다. 자산이 페이지에 로드될 때 또는 &#39;미리 보기&#39; 탭을 사용하여 자산의 게재 URL을 확인할 수도 있습니다. 게재 URL은 자산이 원격으로 액세스되고 있음을 나타냅니다.

AEM 페이지 편집기에서 이미지 핵심 구성 요소 v3 및 티저 핵심 구성 요소 v2에 대해서만 기본 원격 자산에 액세스할 수 있습니다. 사용자 지정 구성 요소를 포함한 다른 구성 요소의 경우 해당 구성 요소와 자산 선택기를 통합하려면 사용자 지정이 필요합니다.

#### 비디오: AEM 페이지 편집기에서 원격 자산 액세스

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### AEM 콘텐츠 조각의 원격 자산 액세스 {#access-assets-content-fragment}

AEM Sites 인스턴스에서 AEM 콘텐츠 조각 내의 원격 자산을 사용하려면 아래 단계를 따르십시오. 이 통합은 AEM as a Cloud Service이 아닌 AEM 6.5에서 수행할 수 있습니다.

1. 다음으로 이동 **[!UICONTROL Assets]** > **[!UICONTROL 파일]**.
1. 콘텐츠 조각이 있는 에셋 폴더를 선택합니다.
1. 콘텐츠 조각을 선택하고 **[!UICONTROL 편집(_e_)]**.

   >[!NOTE]
   >
   >AEM 콘텐츠 조각 모델이 없는 경우 다음을 수행해야 할 수 있습니다 [1개 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en).

1. 다음을 클릭합니다. ![확인 표시 아이콘](/help/assets/assets/do-not-localize/checkmark-icon.svg) 텍스트 구성 요소 옆에 있는 아이콘.
1. 선택 **[!UICONTROL 원격]** 원격 DAM에서 자산을 가져옵니다. <br>
다음 중 하나를 선택할 수 있습니다 **[!UICONTROL 로컬]** 또는 **[!UICONTROL 원격]** 필요에 따라 DAM 저장소를 생성합니다.

   ![이미지](/help/assets/assets/cf-pick.jpg)
로그인하라는 메시지가 표시됩니다.
1. 에셋을 선택하고 **[!UICONTROL 선택]**.
   <br> 원격 자산 URL이 텍스트 구성 요소에 나타납니다.

#### 비디오: AEM 콘텐츠 조각에서 원격 자산 액세스

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Edge Delivery Services의 원격 자산 액세스 {#access-assets-eds}

Edge Delivery Services에서 원격 자산에 액세스할 수도 있습니다. 자세한 내용은 [OpenAPI 기능이 있는 Dynamic Media을 사용하여 제공되는 Assets as a Cloud Service 의 자산 활용](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi).
