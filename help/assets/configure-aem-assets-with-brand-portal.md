---
title: Brand Portal을 사용하여 AEM Assets as a [!DNL Cloud Service]  구성
description: Brand Portal을 사용하여 AEM Assets을 구성하는 방법에 대해 알아봅니다. 구성을 사용하면 승인된 브랜드 자산을 AEM 인스턴스에서 Brand Portal으로 게시하고 Brand Portal 사용자에게 배포할 수 있습니다.
contentOwner: AK
feature: Brand Portal, Asset Distribution, Configuration
role: Admin
exl-id: 078e522f-bcd8-4734-95db-ddc8772de785
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1784'
ht-degree: 9%

---

# Brand Portal로 Experience Manager Assets 구성 {#configure-aem-assets-with-brand-portal}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/brandportal/configure-aem-assets-with-brand-portal.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

Adobe Experience Manager Assets Brand Portal을 구성하면 승인된 브랜드 자산을 Adobe Experience Manager Assets에서 [!DNL Cloud Service] 인스턴스로 Brand Portal에 게시하고 Brand Portal 사용자에게 배포할 수 있습니다.

## Cloud Manager을 사용하여 Brand Portal 활성화 {#activate-brand-portal}

Cloud Manager 사용자는 Experience Manager Assets에 대한 Brand Portal을 [!DNL Cloud Service] 인스턴스로 활성화합니다. 활성화 워크플로우는 백엔드에 필요한 구성(인증 토큰, IMS 구성 및 Brand Portal 클라우드 서비스)을 만들고 Cloud Manager의 Brand Portal 테넌트의 상태를 반영합니다. Brand Portal을 활성화하면 Experience Manager Assets 사용자가 에셋을 Brand Portal에 게시하고 Brand Portal 사용자에게 배포할 수 있습니다.

**전제 조건**

Experience Manager Assets에서 Brand Portal을 [!DNL Cloud Service] 인스턴스로 활성화하려면 다음이 필요합니다.

* 실행 중인 Experience Manager Assets을 [!DNL Cloud Service] 인스턴스로 만듭니다.
* Cloud Manager에 대한 액세스 권한이 있고 Cloud Manager 제품의 프로필에 할당된 사용자입니다. 자세한 내용은 [Cloud Manager 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html#accessing-cloud-manager)를 참조하십시오.

>[!NOTE]
>
>Brand Portal 테넌트와 연결하려면 Experience Manager Assets as a [!DNL Cloud Service] 인스턴스에 구성된 프로덕션 환경이 필요합니다.

Brand Portal을 활성화하는 **단계**

Brand Portal을 [!DNL Cloud Service] 인스턴스로서 또는 별도로 만드는 동안 Experience Manager Assets의 프로덕션 환경을 활성화할 수 있습니다. 환경이 이미 생성되었으며 이제 Brand Portal을 활성화해야 한다고 가정해 보겠습니다.

1. Cloud Manager Adobe에 로그인한 다음 **[!UICONTROL 환경]**(으)로 이동합니다.

   **[!UICONTROL 환경]** 페이지에 모든 기존 환경의 목록이 표시됩니다.

1. 목록에서 환경을 하나씩 선택하여 환경 세부 정보를 확인합니다.

   Brand Portal은 사용 가능한 환경 중 하나에 대한 권한이 있으며 **[!UICONTROL 환경 정보]**&#x200B;에 반영됩니다.

   Brand Portal과 연결된 환경을 찾으면 **[!UICONTROL Brand Portal 활성화]** 단추를 클릭하여 활성화 워크플로를 시작합니다.

   ![Brand Portal 활성화](assets/create-environment4.png)

1. 활성화 워크플로우는 백엔드에 필요한 구성을 만들기 때문에 Brand Portal 테넌트를 활성화하는 데 몇 분이 걸립니다. Brand Portal 테넌트가 활성화되면 상태가 활성화됨으로 변경됩니다.

   ![상태 보기](assets/create-environment5.png)


>[!NOTE]
>
>Brand Portal은 [!DNL Cloud Service] 인스턴스로 Experience Manager Assets과 동일한 IMS 조직에서 활성화되어야 합니다.
>
>IMS 조직(org1-existing)에 대한 기존 Brand Portal 클라우드 구성([Adobe Developer Console을 사용하여 수동으로 구성](#manual-configuration))이 있고 다른 IMS 조직(org2-new)에 대해 Experience Manager Assets as a [!DNL Cloud Service] 인스턴스가 구성된 경우 Cloud Manager에서 Brand Portal을 활성화하면 Brand Portal IMS 조직이 `org2-new`(으)로 재설정됩니다. `org1-existing`에 수동으로 구성된 클라우드 구성이 Experience Manager Assets 작성자 인스턴스에 표시되지만 Cloud Manager에서 Brand Portal을 활성화한 후에는 더 이상 사용되지 않습니다.
>
>기존 Brand Portal 클라우드 구성과 [!DNL Cloud Service] 인스턴스로서의 Experience Manager Assets이 동일한 IMS 조직(org1)을 사용하는 경우 Cloud Manager에서 Brand Portal만 활성화하면 됩니다.
>
>자동 생성된 설정은 수정하지 마십시오.

**참고 항목**:

* [Experience Manager Assetsas a Cloud Service 에서 사용자 및 역할 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html)

* [Cloud Manager에서 환경 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments)


**Brand Portal 테넌트에 로그인**:

Cloud Manager에서 Brand Portal 테넌트를 활성화한 후 Admin Console에서 또는 테넌트 URL을 사용하여 직접 Brand Portal에 로그인할 수 있습니다.

Brand Portal 테넌트의 기본 URL: `https://<tenant-id>.brand-portal.adobe.com/`.

여기서 테넌트 id는 IMS 조직입니다.


Brand Portal URL을 잘 모를 경우 다음 단계를 수행하십시오.

1. [Admin Console](https://adminconsole.adobe.com/)에 로그인하여 **[!UICONTROL 제품]**(으)로 이동합니다.
1. 왼쪽 패널에서 **[!UICONTROL Adobe Experience Manager Brand Portal - Brand Portal]**&#x200B;을(를) 선택합니다.
1. 브라우저에서 Brand Portal을 직접 열려면 **[!UICONTROL Brand Portal으로 이동]**&#x200B;을 클릭하세요.

   또는 **[!UICONTROL Brand Portal으로 이동]** 링크에서 Brand Portal 테넌트 URL을 복사하여 브라우저에 붙여 넣어 Brand Portal 인터페이스를 엽니다.

   ![Brand Portal 액세스](assets/access-bp-on-cloud.png)


**연결 테스트**

Experience Manager Assets as a [!DNL Cloud Service] 인스턴스와 Brand Portal 테넌트 간의 연결을 확인하려면 다음 단계를 수행하십시오.

1. Experience Manager Assets에 로그인합니다.

1. **도구** 패널에서 **[!UICONTROL 배포]** > **[!UICONTROL 배포]**(으)로 이동합니다.

   ![배포 옵션으로 이동](assets/test-bpconfig1.png)

   Brand Portal 배포 에이전트(**[!UICONTROL bpdistributionagent0]**)가 **[!UICONTROL Publish to Brand Portal]**&#x200B;에 만들어졌습니다.

   ![배포 에이전트 만들기](assets/test-bpconfig2.png)

1. 배포 에이전트를 열려면 **[!UICONTROL Brand Portal으로 Publish]**&#x200B;를 클릭하십시오.

   **[!UICONTROL 상태]** 탭에서 배포 큐를 볼 수 있습니다.

   분배 에이전트에는 두 개의 큐가 있습니다.
   * **processing-queue**: Brand Portal에 자산 배포용

   * **error-queue**: 배포가 실패한 자산에 대한.

   >[!NOTE]
   >
   >오류를 검토하고 주기적으로 **오류 큐**&#x200B;를 지우는 것이 좋습니다.

   ![자산 배포에 대한 처리 큐](assets/test-bpconfig3.png)

1. Experience Manager Assets as a [!DNL Cloud Service]와(과) Brand Portal 간의 연결을 확인하려면 **[!UICONTROL 연결 테스트]** 아이콘을 클릭합니다.

   ![AEM과 Brand Portal 간의 연결 확인](assets/test-bpconfig4.png)

   *테스트 패키지가 배달되었습니다*.

   >[!NOTE]
   >
   >자산 분배(큐에서 실행)가 실패하는 원인이 될 수 있으므로 분배 에이전트를 비활성화하지 마십시오.

Experience Manager Assets as a [!DNL Cloud Service] 인스턴스와 Brand Portal 테넌트 간의 연결을 확인하려면 Experience Manager Assets에서 Brand Portal으로 자산을 게시합니다. 연결에 성공하면 게시된 에셋이 Brand Portal 인터페이스에 표시됩니다.


이제 다음과 같은 작업을 수행할 수 있습니다.

* [Experience Manager Assets에서 Brand Portal으로 Publish 에셋](publish-to-brand-portal.md)
* [Experience Manager Assets에서 Brand Portal으로 Publish 폴더](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Experience Manager Assets에서 Brand Portal으로 Publish 컬렉션](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Brand Portal에서 Experience Manager Assets으로 Publish 자산](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=ko) - Brand Portal의 자산 소싱
* [사전 설정, 스키마 및 패싯을 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [태그를 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

자세한 내용은 [Brand Portal 설명서](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html)를 참조하세요.

**배포 로그**

자산 게시 워크플로우에 대한 분배 에이전트 로그를 모니터링할 수 있습니다.

이제 Experience Manager Assets에서 Brand Portal으로 자산을 게시하고 로그를 확인합니다.

1. **연결 테스트** 섹션에 표시된 대로 1에서 4까지의 단계를 수행하고 분배 에이전트 페이지로 이동합니다.
1. 처리 및 오류 로그를 보려면 **[!UICONTROL 로그]**&#x200B;를 클릭하십시오.

   ![처리 및 오류 로그](assets/test-bpconfig5.png)

분배 에이전트가 다음 로그를 생성했습니다.

* INFO: 분배 에이전트의 성공적인 구성을 트리거하는 시스템 생성 로그입니다.
* DSTRQ1(요청 1): 연결 테스트 시 트리거입니다.

자산을 게시할 때 다음 요청 및 응답 로그가 생성됩니다.

**분배 에이전트 요청**:

* DSTRQ2(요청 2): 자산 게시 요청이 트리거됩니다.
* DSTRQ3(요청 3): 시스템이 다른 요청을 트리거하여 Experience Manager Assets 폴더(자산이 있음)를 게시하고 Brand Portal에서 폴더를 복제합니다.

**분배 에이전트 응답**:

* queue-bpdistributionagent0(DSTRQ2): 자산이 Brand Portal에 게시됩니다.
* queue-bpdistributionagent0(DSTRQ3): 시스템이 Brand Portal의 Experience Manager Assets 폴더(에셋 포함)를 복제합니다.

위의 예에서 추가 요청 및 응답이 트리거됩니다. 자산이 처음으로 게시되었기 때문에 시스템이 Brand Portal에서 상위 폴더(경로 추가)를 찾을 수 없었고, 따라서 자산이 게시된 Brand Portal에서 동일한 이름으로 상위 폴더를 만들라는 추가 요청을 트리거했습니다.

>[!NOTE]
>
>상위 폴더가 Brand Portal에 없거나 Experience Manager Assets에서 수정된 경우 추가 요청이 생성됩니다.

Experience Manager Assets에서 Brand Portal을 [!DNL Cloud Service](으)로 활성화하는 자동화 워크플로와 함께, Adobe Developer Console을 사용하여 Brand Portal을 사용하여 Experience Manager Assets을 [!DNL Cloud Service](으)로 수동으로 구성하는 다른 방법이 있습니다. 이는 더 이상 권장되지 않습니다.

>[!NOTE]
>
>Brand Portal 테넌트를 활성화하는 동안 문제가 발생하는 경우 고객 지원 센터에 문의하십시오.

## Adobe Developer Console을 사용한 수동 구성 {#manual-configuration}

>[!NOTE]
>
> 2024년 6월 이후부터는 새 JWT 자격 증명을 만들 수 없습니다. 앞으로 OAuth 자격 증명만 생성됩니다.
> 자세한 내용은 [OAuth 구성 만들기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#creating-oauth-configuration:~:text=For%20example%3A-,Creating%20an%20OAuth%20configuration,-To%20create%20a)를 참조하십시오.

다음 섹션에서는 Adobe Developer Console을 사용하여 Brand Portal을 사용하여 Experience Manager Assets as a [!DNL Cloud Service]을(를) 수동으로 구성하는 방법에 대해 설명합니다.

이전에는 Experience Manager Assets as a [!DNL Cloud Service]이(가) Brand Portal 테넌트의 인증을 위해 Adobe IMS(Identity Management 서비스) 계정 토큰을 조달하는 Adobe Developer Console을 통해 Brand Portal으로 수동으로 구성되었습니다. Experience Manager Assets 및 Adobe Developer Console 모두에서 구성이 필요합니다.

<!--1. In Experience Manager Assets, create an IMS account and generate a public key (certificate).-->
<!--1. Under the project, configure an API using the public key to create a service account connection.
1. Get the service account credentials and JSON Web Token (JWT) payload information.
1. In Experience Manager Assets, configure the IMS account using the service account credentials and JWT payload.-->
1. Adobe 개발자 콘솔에서 Brand Portal 테넌트(조직)에 대한 프로젝트를 만듭니다.
1. Experience Manager Assets에서 IMS 계정 및 Brand Portal 끝점(조직 URL)을 사용하여 Brand Portal 클라우드 서비스를 구성합니다.
1. Experience Manager Assets에서 Brand Portal으로 자산을 게시하여 구성을 테스트합니다.

>[!NOTE]
>
>Experience Manager Assets as a [!DNL Cloud Service] 인스턴스는 하나의 Brand Portal 테넌트로만 구성해야 합니다.

**전제 조건**

Brand Portal을 사용하여 Experience Manager Assets을 구성하려면 다음 항목이 필요합니다.

* 실행 중인 Experience Manager Assets을 [!DNL Cloud Service] 인스턴스로
* Brand Portal 테넌트 URL
* Brand Portal 테넌트의 IMS 조직에 대한 시스템 관리자 권한이 있는 사용자

## 구성 만들기 {#create-new-configuration}

지정된 시퀀스에서 다음 단계를 수행하여 Brand Portal을 사용하여 Experience Manager Assets을 구성합니다.

1. [Adobe Developer Console에서 OAuth 자격 증명 구성](#config-oauth)
1. [OAuth를 사용하여 새 Adobe IMS 통합 만들기](#create-ims-account-configuration)
1. [클라우드 서비스 구성](#configure-cloud-service)
   <!--1. [Obtain public certificate](#public-certificate)-->
<!--1. [Create service account (JWT) connection](#createnewintegration) 
1. [Configure IMS account](#create-ims-account-configuration)-->

<!--
### Create IMS configuration {#create-ims-configuration}

The IMS configuration authenticates your Experience Manager Assets as a [!DNL Cloud Service] instance with the Brand Portal tenant. 

IMS configuration includes two steps:

* [Obtain public certificate](#public-certificate) 
* [Configure IMS account](#create-ims-account-configuration)
-->
<!--

### Obtain public certificate {#public-certificate}

The public key (certificate) authenticates your profile on Adobe Developer Console.

1. Login to Experience Manager Assets.
1. From the **Tools** panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.
1. In Adobe IMS Configurations page, click **[!UICONTROL Create]**. It will redirect to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page. By default, the **Certificate** tab opens.
1. Select **[!UICONTROL Adobe Brand Portal]** in the **[!UICONTROL Cloud Solution]** drop-down list.  
1. Select the **[!UICONTROL Create new certificate]** check box and specify an **alias** for the public key. The alias serves as name of the public key. 
1. Click **[!UICONTROL Create certificate]**. Then, click **[!UICONTROL OK]** to generate the public key.

   ![Create Certificate](assets/ims-config2.png)

1. Click the **[!UICONTROL Download Public Key]** icon and save the public key (CRT) file on your machine.

   The public key is used later to configure API for your Brand Portal tenant and generate service account credentials in Adobe Developer Console.  

   ![Download Certificate](assets/ims-config3.png)

1. Click **[!UICONTROL Next]**.

    In the **Account** tab, Adobe IMS account is created which requires the service account credentials that are generated in Adobe Developer Console. Keep this page open for now.

    Open a new tab and [create a service account (JWT) connection in Adobe Developer Console](#createnewintegration) to get the credentials and JWT payload for configuring the IMS account. 
-->
<!--

### Create service account (JWT) connection {#createnewintegration}

In Adobe Developer Console, projects and APIs are configured at Brand Portal tenant (organization) level. Configuring an API creates a service account (JWT) connection. There are two methods to configure API, by generating a key pair (private and public keys) or by uploading a public key. To configure Experience Manager Assets with Brand Portal, you must generate a public key (certificate) in Experience Manager Assets and create credentials in Adobe Developer Console by uploading the public key. These credentials are required to configure the IMS account in Experience Manager Assets. Once the IMS account is configured, you can configure the Brand Portal cloud service in Experience Manager Assets.

Perform the following steps to generate the service account credentials and JWT payload:

1. Login to Adobe Developer Console with system administrator privileges on the IMS organization (Brand Portal tenant). The default URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Ensure that you have selected the correct IMS organization (Brand Portal tenant) from the drop-down (organization) list located at the upper-right corner.

1. Click **[!UICONTROL Create new project]**. A blank project with a system-generated name is created for your organization. 

   Click **[!UICONTROL Edit project]** to update the **[!UICONTROL Project Title]** and **[!UICONTROL Description]**, and click **[!UICONTROL Save]**.
   
1. In the **[!UICONTROL Project overview]** tab, click **[!UICONTROL Add API]**.

1. In the **[!UICONTROL Add an API window]**, select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Next]**. 

   Ensure that you have access to the Experience Manager Brand Portal service.

1. In the **[!UICONTROL Configure API]** window, click **[!UICONTROL Upload your public key]**. Then, click **[!UICONTROL Select a File]** and upload the public key (.crt file) that you have downloaded in the [obtain public certificate](#public-certificate) section. 

   Click **[!UICONTROL Next]**.

   ![Upload Public Key](assets/service-account3.png)

1. Verify the public key and click **[!UICONTROL Next]**.

1. Select **[!UICONTROL Assets Brand Portal]** as the default product profile and click **[!UICONTROL Save configured API]**. 

   ![Select Product Profile](assets/service-account4.png)

1. Once the API is configured, you are redirected to the API overview page. From the left navigation under **[!UICONTROL Credentials]**, click the **[!UICONTROL Service Account (JWT)]** option.

   >[!NOTE] 
   >
   >* You can view the credentials and perform actions such as generate JWT tokens, copy credential details, retrieve client secret, and so on.
   >* Currently, only the Adobe's Developer Console Service Account (JWT) credential type is supported. Do not use the `OAuth Server-to-Server` credential type until it is supported in mid-April. Read more at [JWT Credentials Deprecation in Adobe Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html).

1. From the **[!UICONTROL Client Credentials]** tab, copy the **[!UICONTROL client ID]**. 

   Click **[!UICONTROL Retrieve Client Secret]** and copy the **[!UICONTROL client secret]**.

   ![Service Account Credentials](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]** information. 

You can now use the client ID (API key), client secret, and JWT payload to [configure the IMS account](#create-ims-account-configuration) in Experience Manager Assets.
-->
<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create an integration page. 
   
   Select your organization from the drop-down list.

   In **[!UICONTROL Experience Cloud]**, Select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Continue]**. 

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Create Integration](assets/create-new-integration2.png)

1. Specify a name and description for the integration. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Select the profile of your organization. 

   Or, select the default profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Create Integration]**. The integration is created.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information. 

   Copy the **[!UICONTROL API Key]** 
   
   Click **[!UICONTROL Retrieve Client Secret]** and copy the Client Secret key.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigate to **[!UICONTROL JWT]** tab, and copy the **[!UICONTROL JWT payload]**.

   The API Key, Client Secret key, and JWT payload information is used to create IMS account configuration.

-->

### Adobe Developer Console에서 OAuth 자격 증명 구성 {#config-oauth}

[Adobe Developer Console에서 OAuth 자격 증명을 구성하고](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#credentials-in-the-developer-console) Brand Portal API를 선택합니다.

### OAuth를 사용하여 새 Adobe IMS 통합 만들기 {#create-ims-account-configuration}

[OAuth를 사용하여 새 Adobe IMS 통합을 만들고](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#creating-oauth-configuration) 클라우드 솔루션 아래의 드롭다운에서 Brand Portal을 선택합니다.

<!--
Ensure that you have performed the following steps:

* [Obtain public certificate](#public-certificate)
* [Create service account (JWT) connection](#createnewintegration)
-->

<!--1. Open the IMS Configuration and navigate to the **[!UICONTROL Account]** tab. Keep the page open while [obtaining the public certificate](#public-certificate).

1. Specify a **[!UICONTROL Title]** for the IMS account.

   In the **[!UICONTROL Authorization Server]** field, specify the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)  
-->
<!--
1. Complete the configuration based on details from the [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/). Click **[!UICONTROL Create]**.
-->
<!--Specify client ID in the **[!UICONTROL API key]** field, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]** (JWT payload) that you have copied while [creating the service account (JWT) connection](#createnewintegration).

   The IMS account is configured. 

   ![IMS Account configuration](assets/create-new-integration6.png)

 <!--  
1. Select the IMS account configuration and click **[!UICONTROL Check Health]**.

   Click **[!UICONTROL Check]** in the dialog box. On successful configuration, a message appears that the *Token is retrieved successfully*.

   ![Adobe IMS Configurations Check Health.](assets/create-new-integration5.png)
-->
<!--
>[!CAUTION]
>
>You must have only one IMS configuration.
>
>Ensure that the IMS configuration passes the health check. If the configuration does not pass the health check, it is invalid. You must delete it and create another valid configuration.
-->

### 클라우드 서비스 구성 {#configure-cloud-service}

Brand Portal 클라우드 서비스를 구성하려면 다음 단계를 수행하십시오.

1. Experience Manager Assets에 로그인합니다.

1. **Cloud Service** 패널에서 **[!UICONTROL 도구]** > **[!UICONTROL AEM Brand Portal]**(으)로 이동합니다.

1. Brand Portal 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

1. 구성에 대한 **[!UICONTROL 제목]**&#x200B;을 지정합니다.

   [IMS 계정을 구성](#create-ims-account-configuration)하는 동안 만든 IMS 구성을 선택하십시오.

   **[!UICONTROL 서비스 URL]** 필드에 Brand Portal 테넌트 URL을 지정하십시오.

   ![Brand Portal 구성 대화 상자](assets/create-cloud-service.png)

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다. 클라우드 구성이 생성됩니다.

   이제 Experience Manager Assets as a [!DNL Cloud Service] 인스턴스가 Brand Portal 테넌트로 구성되었습니다.

이제 분배 에이전트를 확인하고 자산을 Brand Portal에 게시하여 구성을 테스트할 수 있습니다.

SPS에서 보안 IP 미리 보기가 활성화된 경우 **허용 목록에 추가하다**
한 회사에 대해 [보안 미리 보기가 활성화](#https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=en)된 Dynamic Media-Scene7을 사용하는 경우, 회사 관리자 [SPS(Scene7 Publishing System) 플래시 UI를 사용하는 각 지역의 공개 이그레스 IP](#https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=en#testing-the-secure-testing-service)를 Scene7허용 목록에 추가하다 하는 것이 좋습니다.
이그레스 IP는 다음과 같습니다.

| **지역** | **이그레스 IP** |
|--- |--- |
| NA | 130.248.160.68, 20.94.203.130 |
| EMEA | 51.132.146.75, 130.248.244.202, 130.248.244.203, 130.248.244.204, 130.248.244.210, 130.248.244.211, 130.248.244.212 |
| APAC | 63.140.44.54 |

<!--
### Test configuration {#test-configuration}

Perform the following steps to validate the configuration:

1. Login to AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

    ![test-bpconfig1](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![test-bpconfig2](assets/test-bpconfig2.png)


1. Click **[!UICONTROL Publish to Brand Portal]** to open the distribution agent. 

   You can see the distribution queues under the **[!UICONTROL Status]** tab. 
   
   A distribution agent contains two queues: 
   * **processing-queue**: for the distribution of assets to Brand Portal. 

   * **error-queue**: for the assets where distribution has failed. 
   
   >[!NOTE]
   >
   >It is recommended to review the failures and  clear the **error-queue** periodically.  

   ![test-bpconfig3](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets as a [!DNL Cloud Service] and Brand Portal, click the **[!UICONTROL Test Connection]** icon.

   ![test-bpconfig4](assets/test-bpconfig4.png)

   A message appears that your *test package is successfully delivered*.

   >[!NOTE]
   >
   >Avoid disabling the distribution agent, as it can cause the distribution of the assets (running-in-queue) to fail.

You can now:

* [Publish assets from AEM Assets to Brand Portal](publish-to-brand-portal.md)
* [Publish folders from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publish collections from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Publish assets from Brand Portal to AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) - Asset Sourcing in Brand Portal
* [Publish presets, schemas, and facets to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publish tags to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

See [Brand Portal documentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) for more information.

## Distribution logs {#distribution-logs}

You can monitor the distribution agent logs for the asset publishing workflow. 

For example, we have published an asset from AEM Assets to Brand Portal to validate the configuration. 

1. Follow the steps (from 1 to 4) as shown in the [Test Configuration](#test-configuration) section and navigate to the distribution agent page.
1. Click **[!UICONTROL Logs]** to view the processing and error logs.

   ![ctest-bpconfig4](assets/ctest-bpconfig4.png)

The distribution agent has generated the following logs:

* INFO: This is a system-generated log that triggers on successful configuration of the distribution agent. 
* DSTRQ1 (Request 1): Triggers on test connection.

On publishing the asset, the following request and response logs are generated:

**Distribution agent request**:

* DSTRQ2 (Request 2): The asset publishing request is triggered.
* DSTRQ3 (Request 3): The system triggers another request to publish the AEM Assets folder (in which the asset exists) and replicates the folder in Brand Portal.

**Distribution agent response**:

* queue-bpdistributionagent0 (DSTRQ2): The asset is published to Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): The system replicates the AEM Assets folder (containing the asset) in Brand Portal.

In the above example, an additional request and response is triggered. The system could not find the parent folder (Add Path) in Brand Portal because the asset was published for the first time, therefore, it triggered an additional request to create a parent folder with the same name in Brand Portal where the asset is published.  

>[!NOTE]
>
>Additional request is generated in case the parent folder does not exist in Brand Portal or has been modified in AEM Assets. 
-->

<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
-->

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)
