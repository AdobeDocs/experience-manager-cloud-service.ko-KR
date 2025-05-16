---
title: ' [!DNL Dynamic Media] Prime 및 Ultimate 사용'
description: ' [!DNL Dynamic Media] Prime 및 Ultimate 서비스를 활성화하는 방법을 알아봅니다.'
feature: Asset Management
role: User, Admin
exl-id: 0ee161f5-bf44-41f1-928e-c07574fd43cc
source-git-commit: 603602dc70f9d7cdf78b91b39e3b7ff5090a6bc0
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 4%

---

# [!DNL Dynamic Media] Prime 및 Ultimate 사용 {#enable-dynamic-media-prime-and-ultimate}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services와의 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

[!DNL Adobe Experience Manager] as a Cloud Service을 사용하면 [!DNL Dynamic Media] Prime 및 Ultimate 오퍼링에 액세스하여 디지털 워크플로우를 간소화하고 컨텐츠 관리를 최적화할 수 있습니다. [Dynamic Media Prime 및 Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md)을(를) 참조하여 각각의 이점 및 차이점에 대해 알아보십시오.

이 문서에서는 [!DNL Dynamic Media] Prime 및 Ultimate 서비스를 사용하도록 설정하는 전체 워크플로우를 제공합니다.

## [!DNL Dynamic Media] Ultimate 사용 {#enable-dynamic-media-ultimate}

[!DNL Dynamic Media] Ultimate을 사용하려면:

1. [활성화 [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi)
1. [구성 [!DNL Dynamic Media] 솔루션](#configure-dynamic-media-solutions)
1. [ [!DNL Dynamic Media] 회사 만들기 및 나열](#create-and-list-dynamic-media-companies)
1. [게재 계층에서 사용자 지정 도메인 구성](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the [!DNL AEM] [!DNL Dynamic Media] API card](#onboarding-api-keys)
-->

[!DNL Dynamic Media Prime]을(를) 사용하도록 설정해야 하는 경우 [사용 [!DNL Dynamic Media Prime]](#enable-dynamic-media-prime)에서 제공되는 빠른 링크를 참조하십시오.

### 활성화 [!DNL Dynamic Media with OpenAPI] {#activate-dynamic-media-with-openapi}

OpenAPI 기능이 있는 [!DNL Dynamic Media]은(는) DAM을 애자일 및 효율적인 콘텐츠 공급망 생태계의 핵심으로 하여 자산 거버넌스 및 게재를 보장합니다.

[!DNL Dynamic Media] Ultimate을 활성화하는 첫 번째 단계는 Cloud Service 환경에 대해 [[!DNL Dynamic Media] OpenAPI를 사용하여](/help/assets/dynamic-media-open-apis-overview.md)을(를) 활성화하는 것입니다.

#### 시작할 준비 {#prerequisites}

활성화 프로세스를 시작하기 전에 다음 요구 사항을 충족하는지 확인하십시오.

1. [Cloud Manager 액세스](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [프로그램에  [!DNL Dynamic Media] 솔루션](#configure-dynamic-media-solutions)이 포함되어 있습니다.
1. [!DNL Dynamic Media] Prime 또는 Ultimate 라이선스가 있습니다.

#### Cloud Service 환경에서 [!DNL Dynamic Media with OpenAPI] 기능 사용 {#enable-dynamic-media-with-openapi-capabilites-in-your-CS-environment}

다음 단계를 실행하여 클라우드 서비스 환경에 [!DNL Dynamic Media with OpenAPI]을(를) 사용하도록 설정합니다.

1. [Cloud Manager UI로 이동](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. 기존 환경에 대한 액세스 권한이 없는 경우 [환경을 만듭니다](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-environments).

1. 환경 세부 정보 페이지의 **[!UICONTROL 환경 정보]** 섹션에 있는 **[!UICONTROL Dynamic Media]** 행에서 **[!UICONTROL 활성화하려면 클릭]**&#x200B;을(를) 선택하십시오.

   ![OpenAPI 기능을 사용하여 Dynamic Media 활성화](/help/assets/assets/activate-adv-capabiliites-of-dm-openAPI.png)

1. 확인 대화 상자에서 **[!UICONTROL 활성화]**&#x200B;를 클릭하여 [!DNL Dynamic Media with OpenAPI] 활성화 프로세스를 시작합니다. 활성화가 성공하면 Cloud Manager에 다음 상태 업데이트가 표시됩니다.
   1. **[!UICONTROL 환경 단계]**: **[!UICONTROL 실행 중]**
   1. ![DM 활성화됨](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media &#x200B;]**:**[!UICONTROL &#x200B; OpenAPI 기능이 활성화됨&#x200B;]**

      ![활성화 성공](/help/assets/assets/activation-successful.png){width="700" align="left"}

#### 활성화 다시 시도 {#retry-activation}

활성화에 실패하면 Cloud Manager에 다음 상태 업데이트가 표시됩니다.

* **[!UICONTROL 환경 단계]**: **[!UICONTROL OpenAPI를 사용한 DM 실패]**
* ![DM 활성화됨](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media &#x200B;]**:**[!UICONTROL &#x200B; OpenAPI 기능을 활성화하지 못함&#x200B;]**

  ![활성화 다시 시도](/help/assets/assets/retry-dm-openapi-failed-activation.png){width="700" align="left"}

활성화를 다시 시작하려면 **[!UICONTROL 다시 시도하려면 클릭]**&#x200B;을 선택하세요.

또는 다음 단계를 실행하여 활성화 프로세스를 재시작합니다.

1. 모든 환경을 나열하는 페이지로 이동합니다.

1. 환경 행의 끝에 있는 추가 옵션(![추가 옵션](/help/assets/assets/three-dots.svg))을 클릭합니다.

1. 활성화를 다시 시작하려면 **[!UICONTROL OpenAPI 활성화로 DM 다시 시도]**&#x200B;를 선택하십시오.

   ![환경 세부 정보 페이지에서 활성화 다시 시도](/help/assets/assets/restart-activation-process-from-list-environment-page.png)

### [!DNL Dynamic Media] 솔루션 구성 {#configure-dynamic-media-solutions}

Cloud Manager에서 사용 가능한 기존 또는 새로운 환경에서 [Dynamic Media with OpenAPI](/help/assets/dynamic-media-open-apis-overview.md)의 기본 및 고급 기능을 사용하도록 [!UICONTROL Dynamic Media] 솔루션을 구성하십시오.

#### 시작할 준비 {#prerequisites-to-configure-dynamic-media-solutions}

[!UICONTROL Dynamic Media] 솔루션을 구성하려면 다음 사항이 있는지 확인하십시오.

1. [Cloud Manager 액세스](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [!DNL Dynamic Media] Ultimate 라이선스가 있습니다.

#### 자산 배달을 위한 [!DNL Dynamic Media] 솔루션 구성 {#configure-dynamic-media-solutions-for-asset-delivery}

다음 단계를 실행합니다.

1. [새 프로그램을 만들거나](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-program) 기존 프로그램으로 이동하여 **[!UICONTROL 편집]**&#x200B;을 클릭합니다. **[!UICONTROL 프로덕션 설정]** 페이지에 **[!UICONTROL 솔루션 및 추가 기능]** 탭이 표시됩니다.

1. **[!UICONTROL Assets]**, **[!UICONTROL Assets Prime]**, **[!UICONTROL Assets Ultimate]** 또는 **[!UICONTROL 사이트]**&#x200B;를 선택하여 **[!UICONTROL Dynamic Media]** 솔루션을 프로그램에 추가하십시오.

1. **[!UICONTROL Dynamic Media]** 솔루션을 선택하고 **[!UICONTROL 계속]**&#x200B;을 클릭하여 **[!UICONTROL Dynamic Media]** 솔루션을 프로그램에 추가합니다. 이 작업은 프로그램의 모든 기존 환경을 다시 시작하고 [!DNL Dynamic Media] 솔루션을 추가합니다. 또한 프로그램에서 만드는 새 환경은 자동으로 [!DNL Dynamic Media]을(를) 받습니다.

   ![프로덕션에 설정](/help/assets/assets/set-up-for-prod.png){width="500" align="left"}

[활성화 [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi)를 참조하여 환경에서 OpenAPI 기능을 사용하여 [!DNL Dynamic Media]의 기능을 사용해 보세요.

### [!DNL Dynamic Media]개 회사 만들기 및 나열 {#create-and-list-dynamic-media-companies}

AEM 클라우드 서비스 환경에서 [!DNL Dynamic Media]개의 회사를 만들고 나열하여 AEM 환경 내의 구성을 관리합니다.

#### 시작할 준비 {#prerequisites-to-create-and-list-dynamic-media-companies}

IMS 조직에서 기존 회사(계정)를 보거나 새 [!DNL Dynamic Media] 회사(계정)를 추가하려면 다음을 수행해야 합니다.

1. [Cloud Manager 액세스](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. [!DNL Dynamic Media] Ultimate 라이선스가 있습니다.

#### IMS 조직에서 [!DNL Dynamic Media]개 회사 만들고 나열 {#create-and-list-dynamic-media-companies-in-your-ims-organisation}

다음 단계를 실행하여 [!DNL AEM] 환경 내에서 구성할 수 있는 새 [!DNL Dynamic Media] 회사(계정)를 만들고 나열합니다.

1. [Cloud Manager 라이선스 페이지](https://experience-stage.adobe.com/#/@ssahnichstage/cloud-manager/license)&#x200B;(으)로 이동합니다.

1. **[!UICONTROL 회사 추가]**&#x200B;를 클릭하면 **[!UICONTROL Dynamic Media 회사 만들기]** 대화 상자가 표시됩니다.

1. 고유한 [!DNL Dynamic Media] 회사 이름을 지정하고, 회사 지역을 선택하고, 쉼표로 구분된 회사 관리자 전자 메일 ID 목록을 추가하십시오.

   ![Dynamic Media 회사 만들기](/help/assets/assets/create-dynamic-media-company.png){width="500" align="left"}

1. 회사 만들기를 시작하려면 **[!UICONTROL 만들기]**&#x200B;를 클릭하세요. 이 작업은 **[!UICONTROL [!DNL Dynamic Media]개의 회사]** 섹션에 새 행을 추가하고 **[!UICONTROL 설정]**&#x200B;을(를) 회사의 **[!UICONTROL 상태]**(으)로 표시합니다.

   ![Dynamic Media 회사 만들기를 시작했습니다](/help/assets/assets/dm-company-creation-initiated.png)

1. **선택 사항:** 회사의 세부 정보를 보려면 ![정보 아이콘](/help/assets/assets/info-icon-solid-black.svg)을 클릭하세요. 회사를 만들 때 **[!UICONTROL STATUS]**&#x200B;이(가) **[!UICONTROL 준비]**(으)로 업데이트됩니다.

   ![Dynamic Media 회사 정보](/help/assets/assets/dm-company-information.png)

1. Dynamic Media 관리자는 [!DNL AEM] Cloud Service 환경에서 [구성 [!DNL Dynamic Media]](/help/assets/dynamic-media/config-dm.md#architecture-diagram-of-dynamic-media) 회사를 시작하는 단계 목록이 포함된 시작 전자 메일을 사서함에서 확인합니다.

   ![환영 전자 메일](/help/assets/assets/welcome-email.png)

#### 회사 만들기 다시 시도 {#retry-company-creation}

[!DNL Dynamic Media] 회사 만들기에 실패한 경우 실패 상태에 따라 다음 단계를 수행하십시오.

1. **[!UICONTROL 상태]**&#x200B;가 보류 중인 경우 문제 해결을 위해 고객 지원 팀에 문제를 제기하십시오.


   ![보류 중인 상태](/help/assets/assets/company-creation-pending-status.png){width="350" align="center"}



1. **[!UICONTROL Status]**&#x200B;이(가) 실패한 경우 실패 이유에 따라 다시 시도하십시오.

   ![실패 상태](/help/assets/assets/company-creation-failure-status.png){width="380" align="center"}

### 선택 사항: 게재 계층에서 사용자 정의 도메인 구성 {#configure-custom-domain-in-delivery-tier}

AEM as a Cloud Service에는 기본 도메인이 제공되지만 필요에 따라 사용자 정의할 수 있습니다. Cloud Manager을 사용하여 사용자 정의 도메인을 게재 계층에 연결합니다.

#### 시작할 준비 {#prerequisites-to-configure-custom-domain-in-delivery-tier}

구성 프로세스를 시작하기 전에 다음 요구 사항을 충족하는지 확인하십시오.

1. [Cloud Manager 액세스](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [이미 활성화됨 [!DNL Dynamic Media with OpenAPI] 환경에서 활성화됨](#activate-dynamic-media-with-openapi).
1. 준비 상태에서 [!DNL Dynamic Media with OpenAPI]을(를) 사용하도록 설정했습니다.
1. 게재 계층에 사용할 도메인에 대한 EV 또는 OV 유형 인증서. 자세한 내용은 [SSL 인증서 소개](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates)를 참조하십시오.

#### Cloud Manager을 사용하여 게재 계층에서 사용자 정의 도메인 구성 {#configure-custom-domain-in-delivery-tier-using-cloud-manager}

Cloud Manager에서 다음 단계를 실행하여 게재 계층에서 사용자 정의 도메인을 구성합니다.

1. [고객 관리 SSL 인증서 추가](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert).

1. [사용자 지정 도메인 이름 추가](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings).

1. 환경 세부 정보 페이지로 이동하고 [CDN 구성을 추가](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/domain-mappings/add-domain-mapping)합니다. 구성을 추가하는 동안 **[!UICONTROL CDN 구성]** 대화 상자의 **[!UICONTROL 계층]** 필드에서 **[!UICONTROL 배달]**&#x200B;을 선택합니다.

   ![CDN 구성](/help/assets/assets/select-delivery-tier-in-configure-cdn-form.png)

   구성을 추가한 후 **[!UICONTROL CDN 구성]**&#x200B;의 **[!UICONTROL STATUS]**&#x200B;이(가) **[!UICONTROL 적용됨]**&#x200B;으로 업데이트됩니다.

   ![CDN 배포 상태 구성](/help/assets/assets/cdn-configuration-deployment-status.png)

1. 추가 옵션(![추가 옵션](/help/assets/assets/three-dots.svg))을 클릭하고 **[!UICONTROL 라이브 준비]**&#x200B;를 선택하여 **[!UICONTROL 라이브 준비]** 대화 상자를 표시합니다.

   ![라이브 준비 옵션](/help/assets/assets/go-live-readiness-option.png)

1. **[!UICONTROL CNAME 구성]** 단계를 실행하여 DNS 서비스 공급자의 DNS 레코드에 [cdn.adobeaemcloud.com](http://cdn.adobeaemcloud.com/)&#x200B;(CNAME 레코드)을 매핑합니다. 이 매핑을 통해 사용자 정의 도메인에서 받은 요청을 Adobe의 CDN으로 리디렉션할 수 있습니다.

   ![실시간 준비 대화 상자](/help/assets/assets/go-live-readiness-dialogbox.png){width="500" align="left"}

1. **[!UICONTROL 확인]**&#x200B;을 클릭하세요. **[!UICONTROL 상태]**&#x200B;가 **[!UICONTROL 확인]**(으)로 업데이트됩니다. 사용자 정의 도메인을 게재 URL에서 사용할 준비가 되었습니다.


   ![CDN 구성](/help/assets/assets/cdn-configurations-varified.png)



<!--
### Onboard API keys {#onboarding-api-keys}

Create an API key to access [!DNL Dynamic Media] with OpenAPIs and the delivery tier backed Asset Selector.

#### Prepare yourself for API keys onboarding process {#prerequisites-for-onboarding-api-keys} 

To start the API keys onboarding process, ensure you have:

1. [Access to Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Activated [!DNL Dynamic Media with OpenAPI] in your environment](#activate-dynamic-media-with-openapi).
1. [Access to the Adobe Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis#create-adobe-developer-console-adc-project).

#### Onboard the API keys using [!DNL AEM Dynamic Media] API card {#onboarding-api-keys-using-aem-dynamic-media-api-card}

Use the [Adobe Developer Console](https://developer.adobe.com/developer-console/) to onboard the API keys to:

1. [Access Dynamic Media APIs](#access-dynamic-media-apis)
1. [Access Delivery tier backed Asset Selector](#access-delivery-tier-backed-asset-selector)

#### Create an API key to access [!DNL Dynamic Media] with OpenAPIs {#access-dynamic-media-apis}

Execute the following steps to create an API key to access [!DNL Dynamic Media] with OpenAPIs:

1. Navigate to the **[!UICONTROL Admin Console]**. The Admin Console displays the **[!UICONTROL author]**, **[!UICONTROL delivery]** and **[!UICONTROL publish]** instances.
![instances on admin console](/help/assets/assets/delivery-instance-admin-console.png)
1. Select the **[!UICONTROL delivery]** instance to display the product profile with **[!UICONTROL AEM Dynamic Media enable API Services]** enabled by default. The product profile looks like this: **[!UICONTROL AEM Assets DM OpenAPI Users - delivery  - Program [ID Number] - Environment [ID Number]]**. 

   ![product profile on admin console](/help/assets/assets/admin-console-product-profile.png)

   >[!NOTE]
   >
   >This delivery instance is common for [!DNL Content Hub] and [!DNL Dynamic Media] with OpenAPI capabilities.

1. Navigate to the [Adobe Developer console](https://developer.adobe.com/console) and [create a new project](https://developer.adobe.com/dep/guides/dev-console/create-project/). See [Invoke OpenAPI-based AEM APIs for server to server authentication](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) to learn about creating a new project.
1. Select **[!UICONTROL AEM Dynamic Media API]** to access to the [!DNL Dynamic Media with OpenAPI capabilities] and click **[!UICONTROL Next]**.
![adobe developer console](/help/assets/assets/adobe-developer-console.png)
1. Select **[!UICONTROL Server-to-Server Authentication]** and click **[!UICONTROL Next]**. See [Server to Server authentication](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) to learn more about this authentication type.
![server-to-server-authentication](/help/assets/assets/server-to-server-authentication.png)
1. Select **[!UICONTROL OAuth Server-to-Server]**, specify a unique **[!UICONTROL Credential name]** and click **[!UICONTROL Next]**.
![oauth server to server credential](/help/assets/assets/oauth-server-server-and-credential-name.png)
1. Select your product profile (mentioned in step 2) to access the APIs using the environment's delivery endpoint and click **[!UICONTROL Save configured API]**.
![select product profile](/help/assets/assets/select-product-profile.png)
1. Select **[!UICONTROL AEM Dynamic Media API]**. Use the **[!UICONTROL OAuth Server-to-Server]** to fetch the **X-API-key** and access the token for the **authorization** header. 
![oauth server to server](/help/assets/assets/oauth-server-to-server-credentials.png)
Execute the below steps to use [Dynamic Media with OpenAPIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) using the **[!UICONTROL OAuth Server-to-Server]** credentials. 
    1. Copy the **[!UICONTROL API KEY (Client ID)]** and replace the `X-Api-Key` in the cURL.
    1. Click **[!UICONTROL Generate access token]** to generate an access token and replace `YOUR_JWT_HERE` with the token in the cURL.

The cURL looks like this:
```
headers: {
    'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    `},
```
See [Search Assets API](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/search-assets-api#search-assets-api-header) for more information.

### Access Delivery tier backed Asset Selector {#access-delivery-tier-backed-asset-selector}

TBD: Wiki in progress..
-->

## [!DNL Dynamic Media] Prime 사용 {#enable-dynamic-media-prime}

[!DNL Dynamic Media] Prime을 사용하려면:

1. [OpenAPI로 Dynamic Media 활성화](#activate-dynamic-media-with-openapi)
1. [선택 사항: 게재 계층에서 사용자 지정 도메인 구성](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the AEM Dynamic Media API card](#onboarding-api-keys)
-->
