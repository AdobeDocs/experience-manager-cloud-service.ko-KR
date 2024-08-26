---
title: 원격 AEM Assets를 AEM Sites와 통합
description: 승인된 AEM Assets과 AEM 사이트를 구성하고 연결하는 방법에 대해 알아봅니다.
exl-id: 382e6166-3ad9-4d8f-be5c-55a7694508fa
source-git-commit: e2c0c848c886dc770846d064e45dcc52523ed8e3
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 14%

---

# 원격 AEM Assets를 AEM Sites와 통합  {#integrate-approved-assets}

다양한 온라인 플랫폼에서 매력적이고 일관된 브랜드 경험을 제공하기 위해서는 디지털 에셋을 효과적으로 관리하는 것이 중요합니다. OpenAPI 기능이 포함된 Dynamic Media은 AEM Sites과 AEM Assets as a Cloud Service 간의 원활한 통합을 통해 디지털 자산 관리를 향상시킵니다. 이 혁신적인 기능을 사용하면 여러 AEM 환경에서 서로 다른 유형의 승인된 디지털 에셋을 쉽게 공유 및 관리할 수 있으므로 사이트 작성자 및 콘텐츠 편집자를 위한 워크플로를 간소화할 수 있습니다.

Dynamic Media의 OpenAPI 기능을 사용하면 사이트 작성자가 AEM 페이지 편집기 및 [콘텐츠 조각](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html) 내에서 원격 DAM의 자산을 직접 사용할 수 있으므로 콘텐츠 생성 및 관리 프로세스를 단순화할 수 있습니다.

사용자는 최대 수에 대한 제한 없이 여러 AEM Sites 인스턴스를 원격 DAM 배포에 연결할 수 있으므로 [연결된 Assets](use-assets-across-connected-assets-instances.md) 기능에 비해 주목할 만한 이점이 있습니다.

![이미지](/help/assets/assets/connected-assets-rdam.png)

초기 설정 후 사용자는 AEM Sites 인스턴스에서 페이지를 만들고 필요에 따라 에셋을 추가할 수 있습니다. 에셋을 추가할 때 로컬 DAM에 저장된 에셋을 선택하거나 원격 DAM에서 사용할 수 있는 에셋을 찾아 사용할 수 있습니다.

OpenAPI 기능이 포함된 Dynamic Media은 컨텐츠 조각의 원격 자산 액세스 및 사용, 원격 자산의 메타데이터 가져오기 등과 같은 몇 가지 다른 이점을 제공합니다. 연결된 Assets에 대한 OpenAPI 기능을 갖춘 Dynamic Media의 다른 [이점에 대해 자세히 알아보세요](/help/assets/dynamic-media-open-apis-faqs.md).

## 시작하기에 앞서 {#pre-requisites-sites-integration}

OpenAPI 기능과 함께 Dynamic Media을 사용하여 원격 자산을 지원하려면 다음 작업을 수행해야 합니다.

* AEM 6.5 SP 18+ 또는 AEM as a Cloud Service

* 코어 구성 요소 릴리스 2.23.2 이상

* AEM as a Cloud Service에 대해 다음 [환경 변수](/help/implementing/cloud-manager/environment-variables.md#add-variables)를 설정합니다.

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX`이(가) 프로그램 ID <br>을(를) 참조합니다.
     `eYYYY`이(가) 환경 ID를 참조합니다.

  이러한 변수는 로컬 Sites 인스턴스로 작동하는 AEM as a Cloud Service 환경의 Cloud Manager 사용자 인터페이스를 사용하여 설정됩니다.

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId]: IMS 클라이언트 ID를 가져오려면 Adobe 지원 티켓을 제출해야 합니다.

     또는 다음 단계에 따라 AEM Sites 인스턴스에서 AEM 6.5에 대한 [OSGi 설정](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html)을 구성하십시오.

   1. 콘솔에 로그인하고 **[!UICONTROL OSGi] >**를 클릭하거나
직접 URL 사용(예: `https://localhost:4502/system/console/configMgr`)

   1. **차세대 Dynamic Media 구성**(`NextGenDynamicMediaConfigImpl`) OSGi 구성을 다음과 같이 구성하여 값을 원격 자산 환경의 값으로 바꿉니다.

      ```text
        imsClient="<ims-client-ID>"
        enabled=B"true"
        imsOrg="<ims-org>@AdobeOrg"
        repositoryId="<repo-id>.adobeaemcloud.com"
      ```

      `imsOrg`은(는) 필수 입력이 아닙니다.
      `repositoryId` = &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot;
여기서 `pXXXX`은(는) 프로그램 ID를 나타냅니다.
      `eYYYY`이(가) 환경 ID를 참조합니다.

      ![차세대 Dynamic Media 구성 OSGi 구성 창](/help/assets/assets/remote-assets-osgi.png)

  [IMS 인증](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html)에 대해 자세히 알아보세요.

  OSGi 구성 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.

   * AEM as a Cloud Service용 [Adobe Experience Manager as a Cloud Service에 대한 OSGi 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html)
   * AEM 6.5용 [OSGi 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html)

* 원격 DAM AEM as a Cloud Service 인스턴스에 로그인하기 위한 IMS 액세스 원격 DAM 환경에 대한 IMS 액세스 권한이 있는 사이트 작성자를 의미합니다.

* AEM Sites 인스턴스에서 이미지 v3 구성 요소를 구성합니다. 구성 요소가 없으면 [콘텐츠 패키지](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0)를 다운로드하여 설치하십시오.

## HTTPS 구성 {#https}

일반적으로 HTTP를 사용하여 모든 프로덕션 AEM 인스턴스를 실행하는 것이 좋습니다. 단, 로컬 개발 환경은 이와 같이 설정되지 않을 수 있습니다. 그러나 OpenAPI가 포함된 Dynamic Media를 사용하는 원격 자산이 작동하려면 HTTPS가 필요합니다.

개발 환경을 포함하여 원격 자산을 사용하려는 곳에서 [이 안내서를 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html)하여 HTTPS를 구성하십시오.

## 원격 DAM에서 자산 액세스 {#fetch-assets}

OpenAPI 기능이 포함된 Dynamic Media을 사용하면 로컬 AEM Sites 페이지 편집기 및 AEM 콘텐츠 조각의 원격 DAM 인스턴스에서 사용할 수 있는 자산에 액세스할 수 있습니다.

![이미지](/help/assets/assets/open-APIs.png)

### AEM 페이지 편집기에서 원격 자산 액세스 {#access-assets-page-editor}

AEM Sites 인스턴스에서 AEM 페이지 편집기 내의 원격 자산을 사용하려면 아래 단계를 따르십시오. 이 통합은 AEM as a Cloud Service 및 AEM 6.5에서 수행할 수 있습니다.

1. 원격 자산을 추가해야 하는 AEM **[!UICONTROL 페이지]**&#x200B;가 있는 **[!UICONTROL 사이트]** > _웹 사이트_(으)로 이동합니다.
1. 페이지를 선택하고 **[!UICONTROL 편집(_e_)]**&#x200B;을 클릭합니다. AEM **[!UICONTROL 페이지 편집기]**&#x200B;가 열립니다.
1. 레이아웃 컨테이너를 클릭하고 **[!UICONTROL 이미지]** 구성 요소를 추가합니다.
1. **[!UICONTROL 이미지]** 구성 요소를 클릭하고 ![설정 아이콘](/help/assets/assets/do-not-localize/settings-icon.svg) 아이콘을 클릭합니다.
1. **[!UICONTROL 페이지에서 추천 이미지 상속]** 옵션을 선택 취소합니다.
1. **[!UICONTROL 선택]**&#x200B;을 클릭하고 **[!UICONTROL 원격]**을(를) 선택합니다.
   ![이미지](/help/assets/assets/uncheck-inherit-option.jpg)

   로그인하라는 메시지가 표시됩니다.
1. 자산을 선택하고 **[!UICONTROL 선택]**&#x200B;을 클릭합니다.
1. 대체 텍스트를 추가하고 **[!UICONTROL 완료]**를 클릭합니다.
   <br> 원격 자산이 이미지 구성 요소에 나타납니다. 자산이 페이지에 로드될 때 또는 &#39;미리 보기&#39; 탭을 사용하여 자산의 게재 URL을 확인할 수도 있습니다. 게재 URL은 자산이 원격으로 액세스되고 있음을 나타냅니다.

AEM 페이지 편집기에서 이미지 핵심 구성 요소 v3 및 티저 핵심 구성 요소 v2에 대해서만 기본 원격 자산에 액세스할 수 있습니다. 사용자 지정 구성 요소를 포함한 다른 구성 요소의 경우 해당 구성 요소와 자산 선택기를 통합하려면 사용자 지정이 필요합니다.

#### 비디오: AEM 페이지 편집기에서 원격 자산 액세스

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### AEM 콘텐츠 조각의 원격 자산 액세스 {#access-assets-content-fragment}

AEM Sites 인스턴스에서 AEM 콘텐츠 조각 내의 원격 자산을 사용하려면 아래 단계를 따르십시오. 이 통합은 AEM as a Cloud Service이 아닌 AEM 6.5에서 수행할 수 있습니다.

1. **[!UICONTROL Assets]** > **[!UICONTROL 파일]**(으)로 이동합니다.
1. 콘텐츠 조각이 있는 에셋 폴더를 선택합니다.
1. 콘텐츠 조각을 선택하고 **[!UICONTROL 편집(_e_)]**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >AEM 콘텐츠 조각 모델이 없는 경우 [하나 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en)해야 할 수 있습니다.

1. 텍스트 구성 요소 옆에 있는 ![확인 표시 아이콘](/help/assets/assets/do-not-localize/checkmark-icon.svg) 아이콘을 클릭합니다.
1. 원격 DAM에서 자산을 가져오려면 **[!UICONTROL 원격]**&#x200B;을(를) 선택하십시오. <br>
필요에 따라 **[!UICONTROL 로컬]** 또는 **[!UICONTROL 원격]** DAM 저장소를 선택할 수 있습니다.

   ![이미지](/help/assets/assets/cf-pick.jpg)
로그인하라는 메시지가 표시됩니다.
1. 자산을 선택하고 **[!UICONTROL 선택]**을 클릭합니다.
   <br> 원격 자산 URL이 텍스트 구성 요소에 나타납니다.

#### 비디오: AEM 콘텐츠 조각에서 원격 자산 액세스

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Edge Delivery Services의 원격 자산 액세스 {#access-assets-eds}

Edge Delivery Services에서 원격 자산에 액세스할 수도 있습니다. 자세한 내용은 [OpenAPI 기능이 있는 Assets as a Cloud Service API를 사용하여 전달된 Dynamic Media 자산 활용](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi)을 참조하십시오.
