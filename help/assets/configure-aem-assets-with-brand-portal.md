---
title: Brand Portal을 사용하여 AEM Assets을 [!DNL Cloud Service] 으로 구성
description: Brand Portal에서 AEM Assets 구성.
contentOwner: Vishabh Gupta
feature: Brand Portal,Asset Distribution,Configuration
role: Admin
exl-id: 078e522f-bcd8-4734-95db-ddc8772de785
source-git-commit: ab84fe6c5b1ea16de2b4dff9bf5dc55ba196fb6f
workflow-type: tm+mt
source-wordcount: '2402'
ht-degree: 20%

---

# Brand Portal을 사용하여 AEM Assets을 [!DNL Cloud Service]으로 구성 {#configure-aem-assets-with-brand-portal}

Adobe Experience Manager Assets Brand Portal을 구성하면 Adobe Experience Manager Assets에서 승인된 브랜드 자산을 [!DNL Cloud Service] 인스턴스로 Brand Portal에 게시하고 Brand Portal 사용자에게 배포할 수 있습니다.

## Cloud Manager를 사용하여 Brand Portal 활성화 {#activate-brand-portal}

Cloud Manager 사용자는 AEM Assets에 대해 [!DNL Cloud Service] 인스턴스로 Brand Portal을 활성화합니다. 활성화 워크플로우는 백엔드에 필수 구성(인증 토큰, IMS 구성 및 Brand Portal 클라우드 서비스)을 만들고 Cloud Manager에서 Brand Portal 테넌트의 상태를 반영합니다. Brand Portal을 활성화하면 AEM Assets 사용자가 자산을 Brand Portal에 게시하여 Brand Portal 사용자에게 배포할 수 있습니다.

**전제 조건**

AEM Assets에서 [!DNL Cloud Service] 인스턴스로 Brand Portal을 활성화하려면 다음 항목이 필요합니다.

* [!DNL Cloud Service] 인스턴스로 실행 중인 AEM Assets.
* Cloud Manager 제품의 프로필에 할당된 Cloud Manager에 액세스할 수 있는 사용자. 자세한 내용은 [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html#accessing-cloud-manager)액세스 를 참조하십시오.

>[!NOTE]
>
>[!DNL Cloud Service] 인스턴스로 AEM Assets은 하나의 Brand Portal 테넌트와만 연결할 수 있습니다. AEM Assets에 [!DNL Cloud Service] 인스턴스로 여러 환경(개발, 프로덕션 및 스테이지)이 있을 수 있으며, 여기서 Brand Portal은 하나의 환경에서 활성화됩니다.

**Brand Portal 활성화 절차**

AEM Assets에 대한 환경을 [!DNL Cloud Service] 인스턴스로 만들거나 별도로 Brand Portal을 활성화할 수 있습니다. 환경이 이미 만들어졌다고 가정하고 이제 Brand Portal을 활성화해야 합니다.

1. Cloud Manager에 로그인하고 **[!UICONTROL 환경]**&#x200B;으로 이동합니다.

   **[!UICONTROL 환경]** 페이지에는 모든 기존 환경의 목록이 표시됩니다.

1. 목록에서 환경(하나씩)을 선택하여 환경 세부 사항을 확인합니다.

   Brand Portal은 사용 가능한 환경 중 하나에 액세스할 수 있으며 **[!UICONTROL 환경 정보]**&#x200B;에 반영됩니다.

   Brand Portal과 연관된 환경이 발견되면 **[!UICONTROL Brand Portal 활성화]** 단추를 클릭하여 활성화 워크플로우를 시작합니다.

   ![Brand Portal 활성화](assets/create-environment4.png)

1. 활성화 워크플로우가 백엔드에서 필요한 구성을 만들므로 Brand Portal 테넌트를 활성화하는 데 몇 분이 소요됩니다. Brand Portal 테넌트가 활성화되면 상태가 활성화됨으로 변경됩니다.

   ![상태 보기](assets/create-environment5.png)


>[!NOTE]
>
>Brand Portal은 [!DNL Cloud Service] 인스턴스와 AEM Assets의 동일한 IMS 조직에서 활성화되어야 합니다.
>
>IMS 조직(org1-existing)에 대해 Adobe 개발자 콘솔](#manual-configuration))을 사용하여 수동으로 구성한 기존 Brand Portal 클라우드 구성([)이 있고 다른 IMS 조직(org2-new)에 대해 [!DNL Cloud Service] 인스턴스가 구성된 경우, Cloud Manager에서 Brand Portal을 활성화하면 Brand Portal IMS 조직이 `org2-new`로 재설정됩니다. `org1-existing`에 수동으로 구성된 클라우드 구성은 AEM Assets 작성자 인스턴스에 표시되지만, Cloud Manager에서 Brand Portal을 활성화한 후에는 더 이상 사용할 수 없습니다.
>
>기존 Brand Portal 클라우드 구성 및 [!DNL Cloud Service] 인스턴스로 AEM Assets이 동일한 IMS 조직(org1)을 사용하는 경우 Cloud Manager에서 Brand Portal을 활성화하기만 하면 됩니다.
>
>자동 생성된 설정은 수정하지 마십시오.

**참고 항목**:
* [AEM Assets에서 Cloud Service으로 사용자 및 역할 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html)

* [Cloud Manager에서 환경 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments)


**Brand Portal 테넌트에 로그인**:

Cloud Manager에서 Brand Portal 테넌트가 활성화되면 Admin Console에서 또는 테넌트 URL을 사용하여 Brand Portal에 직접 로그인할 수 있습니다.

Brand Portal 테넌트의 기본 URL은 다음과 같습니다. `https://<tenant-id>.brand-portal.adobe.com/`

여기서 테넌트 ID는 IMS 조직입니다.

Brand Portal URL을 모르는 경우 다음 단계를 수행하십시오.

1. [Admin Console](http://adminconsole.adobe.com/)에 로그인하고 **[!UICONTROL Products]**&#x200B;로 이동합니다.
1. 왼쪽 레일에서 **[!UICONTROL Adobe Experience Manager Brand Portal - Brand Portal]**&#x200B;을 선택합니다.
1. **[!UICONTROL Brand Portal]**&#x200B;로 이동 을 클릭하여 브라우저에서 직접 Brand Portal을 엽니다.

   또는 **[!UICONTROL Brand Portal]** 링크로 이동 링크에서 Brand Portal 테넌트 URL을 복사하여 브라우저에 붙여 넣어 Brand Portal 인터페이스를 엽니다.

   ![Brand Portal 액세스](assets/access-bp-on-cloud.png)


**연결 테스트**

다음 단계를 수행하여 AEM Assets as a [!DNL Cloud Service] 인스턴스와 Brand Portal 임차인 간의 연결을 확인합니다.

1. AEM Assets에 로그인합니다.

1. **도구** 패널에서 **[!UICONTROL 배포]** > **[!UICONTROL 배포]**&#x200B;로 이동합니다.

   ![](assets/test-bpconfig1.png)

   Brand Portal 배포 에이전트(**[!UICONTROL bpdistributionagent0]**)는 **[!UICONTROL Brand Portal에 게시]**&#x200B;에 만들어집니다.

   ![](assets/test-bpconfig2.png)


1. **[!UICONTROL Brand Portal에 게시]**&#x200B;를 클릭하여 분배 에이전트를 엽니다.

   **[!UICONTROL 상태]** 탭 아래에서 분배 큐를 볼 수 있습니다.

   분배 에이전트에는 두 개의 큐가 있습니다.
   * **처리 큐**: Brand Portal에 자산을 분배하기 위해 사용됩니다.

   * **오류 큐**: 배포가 실패한 자산에 대해 입니다.
   >[!NOTE]
   >
   >오류를 검토하고 **error-queue** 를 정기적으로 지우는 것이 좋습니다.

   ![](assets/test-bpconfig3.png)

1. AEM Assets을 [!DNL Cloud Service](으)로 연결하고 Brand Portal 간의 연결을 확인하려면 **[!UICONTROL 연결 테스트]** 아이콘을 클릭합니다.

   ![](assets/test-bpconfig4.png)

   *테스트 패키지가 성공적으로 전달되었다는 메시지가 나타납니다*.

   >[!NOTE]
   >
   >자산 분배(큐에서 실행)가 실패하는 원인이 될 수 있으므로 분배 에이전트를 비활성화하지 마십시오.

AEM Assets as a0/> 인스턴스와 Brand Portal 임차인 간의 연결을 확인하려면 AEM Assets의 자산을 Brand Portal에 게시합니다. [!DNL Cloud Service] 연결에 성공하면 게시된 자산이 Brand Portal 인터페이스에 표시됩니다.


이제 다음을 수행할 수 있습니다.

* [AEM Assets의 자산을 Brand Portal에 게시](publish-to-brand-portal.md)
* [AEM Assets의 폴더를 Brand Portal에 게시](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [AEM Assets의 컬렉션을 Brand Portal에 게시](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Brand Portal의 자산을 AEM Assets에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html)  - Brand Portal의 자산 소싱
* [사전 설정, 스키마 및 패싯을 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [태그를 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

자세한 내용은 [Brand Portal 설명서](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html)를 참조하십시오.

**분배 로그**

자산 게시 작업 과정에 대한 분배 에이전트 로그를 모니터링할 수 있습니다.

이제 AEM Assets에서 Brand Portal으로 자산을 게시하여 로그를 보도록 하겠습니다.

1. **연결 테스트** 섹션에 표시된 대로 절차(1에서 4)를 수행하고 분배 에이전트 페이지로 이동합니다.
1. **[!UICONTROL 로그]**&#x200B;를 클릭하여 처리 및 오류 로그를 확인합니다.

   ![](assets/test-bpconfig5.png)

분배 에이전트가 다음 로그를 생성했습니다.

* 정보: 분배 에이전트의 성공적인 구성을 트리거하는 시스템 생성 로그입니다.
* DSTRQ1(요청 1): 테스트 연결에 대해 트리거합니다.

자산을 게시할 때 다음 요청 및 응답 로그가 생성됩니다.

**분배 에이전트 요청**:

* DSTRQ2(요청 2): 자산 게시 요청이 트리거됩니다.
* DSTRQ3(요청 3): 시스템이 다른 요청을 트리거하여 AEM Assets 폴더(자산이 있는 폴더)를 게시하고 Brand Portal에서 폴더를 복제합니다.

**분배 에이전트 응답**:

* queue-bpdistributionagent0(DSTRQ2): 자산이 Brand Portal에 게시됩니다.
* queue-bpdistributionagent0(DSTRQ3): 시스템이 Brand Portal에서 AEM Assets 폴더(자산 포함)를 복제합니다.

위의 예에서 추가적인 요청 및 응답이 트리거됩니다. 자산이 처음으로 게시되었기 때문에 시스템이 Brand Portal에서 상위 폴더(경로 추가)를 찾을 수 없어서 자산이 게시된 Brand Portal에서 동일한 이름으로 상위 폴더를 만들라는 추가 요청을 트리거했습니다.

>[!NOTE]
>
>상위 폴더가 Brand Portal에 없거나 AEM Assets에서 수정된 경우에 추가 요청이 생성됩니다.

AEM Assets에서 Brand Portal을 [!DNL Cloud Service](으)로 활성화하기 위한 자동화 워크플로우와 함께 Adobe 개발자 콘솔을 사용하여 AEM Assets을 [!DNL Cloud Service]로 수동으로 구성하는 다른 방법이 있습니다. 이 방법은 더 이상 권장되지 않습니다.

>[!NOTE]
>
>Brand Portal 테넌트를 활성화하는 동안 문제가 발생하는 경우 Adobe 지원 센터에 문의하십시오.

## Adobe 개발자 콘솔을 사용한 수동 구성 {#manual-configuration}

다음 섹션에서는 Adobe 개발자 콘솔을 사용하여 Brand Portal을 사용하여 AEM Assets을 [!DNL Cloud Service]으로 수동으로 구성하는 방법에 대해 설명합니다.

이전에는 AEM Assets as a [!DNL Cloud Service] 가 Brand Portal 테넌트의 인증을 위해 IMS(Adobe Identity Management Services) 계정 토큰을 전달하는 Adobe 개발자 콘솔을 통해 Brand Portal으로 수동으로 구성되었습니다. AEM Assets과 Adobe 개발자 콘솔 모두에 구성이 필요합니다.

1. AEM Assets에서 IMS 계정을 만들고 공개 키(인증서)를 생성합니다.
1. Adobe 개발자 콘솔에서 Brand Portal 테넌트(조직)에 대한 프로젝트를 만듭니다.
1. 프로젝트에서 공개 키로 API를 구성하여 서비스 계정 연결을 만듭니다.
1. 서비스 계정 자격 증명과 JWT(JSON 웹 토큰) 페이로드 정보를 가져옵니다.
1. AEM Assets에서 서비스 계정 자격 증명과 JWT 페이로드를 사용하여 IMS 계정을 구성합니다.
1. AEM Assets에서 IMS 계정 및 Brand Portal 끝점(조직 URL)을 사용하여 Brand Portal 클라우드 서비스를 구성합니다.
1. AEM Assets에서 Brand Portal으로 자산을 게시하여 구성을 테스트합니다.

>[!NOTE]
>
>[!DNL Cloud Service] 인스턴스로서의 AEM Assets은 하나의 Brand Portal 테넌트로만 구성해야 합니다.

**전제 조건**

Brand Portal을 사용하여 AEM Assets를 구성하려면 다음 항목이 필요합니다.

* AEM Assets을 [!DNL Cloud Service] 인스턴스로 실행 중인 경우
* Brand Portal 테넌트 URL
* Brand Portal 임차인의 IMS 조직에 대한 시스템 관리자 권한이 있는 사용자

## 구성 만들기 {#create-new-configuration}

지정된 시퀀스에서 다음 단계를 수행하여 Brand Portal을 사용하여 AEM Assets을 구성합니다.

1. [공개 인증서 받기](#public-certificate)
1. [서비스 계정(JWT) 연결 만들기](#createnewintegration)
1. [IMS 계정 구성](#create-ims-account-configuration)
1. [클라우드 서비스 구성](#configure-the-cloud-service)

### IMS 구성 만들기 {#create-ims-configuration}

IMS 구성은 Brand Portal 테넌트로 AEM Assets을 [!DNL Cloud Service] 인스턴스로 인증합니다.

IMS 구성에는 두 단계가 포함됩니다.

* [공개 인증서 받기](#public-certificate)
* [IMS 계정 구성](#create-ims-account-configuration)

### 공개 인증서 받기 {#public-certificate}

공개 키(인증서)는 Adobe 개발자 콘솔에서 프로필을 인증합니다.

1. AEM Assets에 로그인합니다.
1. **도구** 패널에서 **[!UICONTROL 보안]** > **[!UICONTROL Adobe IMS 구성]**&#x200B;으로 이동합니다.
1. Adobe IMS 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 이 페이지는 **[!UICONTROL Adobe IMS 기술 계정 구성]** 페이지로 리디렉션됩니다. 기본적으로 **인증서** 탭이 열립니다.
1. **[!UICONTROL 클라우드 솔루션]** 드롭다운 목록에서 **[!UICONTROL Adobe Brand Portal]**&#x200B;을 선택합니다.
1. **[!UICONTROL 새 인증서 만들기]** 확인란을 선택하고 공개 키에 대해 **별칭**&#x200B;을 지정합니다. 별칭은 공개 키의 이름으로 사용됩니다.
1. **[!UICONTROL 인증서 만들기]**&#x200B;를 클릭합니다. 그런 다음 **[!UICONTROL 확인]**&#x200B;을 클릭하여 공개 키를 생성합니다.

   ![인증서 만들기](assets/ims-config2.png)

1. **[!UICONTROL 공개 키 다운로드]** 아이콘을 클릭하고 공개 키(CRT) 파일을 컴퓨터에 저장합니다.

   공개 키는 나중에 Brand Portal 테넌트에 대한 API를 구성하고 Adobe 개발자 콘솔에서 서비스 계정 자격 증명을 생성하는 데 사용됩니다.

   ![인증서 다운로드](assets/ims-config3.png)

1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   **계정** 탭에서 Adobe 개발자 콘솔에 생성된 서비스 계정 자격 증명이 필요한 Adobe IMS 계정이 만들어집니다. 우선은 이 페이지를 열어 두십시오.

   새 탭을 열고 [Adobe 개발자 콘솔에 서비스 계정(JWT) 연결을 만들어](#createnewintegration) IMS 계정을 구성하기 위한 자격 증명과 JWT 페이로드를 가져옵니다.

### 서비스 계정(JWT) 연결 만들기 {#createnewintegration}

Adobe 개발자 콘솔에서 프로젝트 및 API는 Brand Portal 테넌트(조직) 수준에서 구성됩니다. API를 구성하면 서비스 계정(JWT) 연결이 만들어집니다. 키 쌍(개인 및 공개 키)을 생성하거나 공개 키를 업로드하여 API를 구성하는 두 가지 방법이 있습니다. Brand Portal으로 AEM Assets을 구성하려면 AEM Assets에서 공개 키(인증서)를 생성하고 공개 키를 업로드하여 Adobe 개발자 콘솔에서 자격 증명을 만들어야 합니다. 이러한 자격 증명은 AEM Assets에서 IMS 계정을 구성하는 데 필요합니다. IMS 계정이 구성되면 AEM Assets에서 Brand Portal 클라우드 서비스를 구성할 수 있습니다.

서비스 계정 자격 증명과 JWT 페이로드를 생성하려면 다음 단계를 수행합니다.

1. IMS 조직(Brand Portal 테넌트)에 대한 시스템 관리자 권한으로 Adobe 개발자 콘솔에 로그인합니다. 기본 URL은 [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >오른쪽 위 모서리에 있는 드롭다운(조직) 목록에서 올바른 IMS 조직(Brand Portal 테넌트)을 선택했는지 확인합니다.

1. **[!UICONTROL 새 프로젝트 만들기]**&#x200B;를 클릭합니다. 조직에 대해 시스템 생성 이름이 있는 빈 프로젝트가 만들어집니다.

   **[!UICONTROL 프로젝트 편집]**&#x200B;을 클릭하여 **[!UICONTROL 프로젝트 제목]** 및 **[!UICONTROL 설명]**&#x200B;을 업데이트하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 프로젝트 개요]** 탭에서 **[!UICONTROL API 추가]**&#x200B;를 클릭합니다.

1. **[!UICONTROL API 추가 창]**&#x200B;에서 **[!UICONTROL AEM Brand Portal]**&#x200B;을 선택하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   AEM Brand Portal 서비스에 대한 액세스 권한이 있는지 확인합니다.

1. **[!UICONTROL API 구성]** 창에서 **[!UICONTROL 공개 키 업로드]**&#x200B;를 클릭합니다. 그런 다음 **[!UICONTROL 파일]**&#x200B;을 선택하고 [공개 인증서 가져오기](#public-certificate) 섹션에서 다운로드한 공개 키(.crt 파일)를 업로드합니다.

   **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   ![공개 키 업로드](assets/service-account3.png)

1. 공개 키를 확인하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. **[!UICONTROL Assets Brand Portal]** 를 기본 제품 프로필로 선택하고 **[!UICONTROL 구성된 API]** 저장 을 클릭합니다.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![제품 프로필 선택](assets/service-account4.png)

1. API가 구성되면 API 개요 페이지로 리디렉션됩니다. **[!UICONTROL 자격 증명]** 아래의 왼쪽 탐색에서 **[!UICONTROL 서비스 계정(JWT)]** 옵션을 클릭합니다.

   >[!NOTE]
   >
   >자격 증명을 보고 JWT 토큰 생성, 자격 증명 세부 사항 복사, 클라이언트 암호 검색 등의 작업을 수행할 수 있습니다.

1. **[!UICONTROL 클라이언트 자격 증명]** 탭에서 **[!UICONTROL 클라이언트 ID]**&#x200B;를 복사합니다.

   **[!UICONTROL 클라이언트 암호 검색]**&#x200B;을 클릭하고 **[!UICONTROL 클라이언트 암호 키]**&#x200B;를 복사합니다.

   ![서비스 계정 자격 증명](assets/service-account5.png)

1. **[!UICONTROL JWT 생성]** 탭으로 이동하여 **[!UICONTROL JWT 페이로드]** 정보를 복사합니다.

이제 클라이언트 ID(API 키), 클라이언트 암호 및 JWT 페이로드를 [AEM Assets에서 IMS 계정](#create-ims-account-configuration)을 구성할 수 있습니다.

<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create a new integration page opens. 
   
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

   The API Key, Client Secret key, and JWT payload information will be used to create IMS account configuration.

-->

### IMS 계정 구성 {#create-ims-account-configuration}

다음 절차를 수행했는지 확인하십시오.

* [공개 인증서 받기](#public-certificate)
* [서비스 계정(JWT) 연결 만들기](#createnewintegration)

다음 단계를 수행하여 IMS 계정을 구성합니다.

1. IMS 구성을 열고 **[!UICONTROL 계정]** 탭으로 이동합니다. 공개 인증서](#public-certificate)를 가져오는 동안 페이지를 열어 두었습니다.[

1. IMS 계정에 대한 **[!UICONTROL 제목]**&#x200B;을 지정합니다.

   **[!UICONTROL 인증 서버]** 필드에서 URL을 지정합니다. [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   [서비스 계정(JWT) 연결](#createnewintegration)을 만드는 동안 복사한 **[!UICONTROL API 키]** 필드, **[!UICONTROL 클라이언트 암호]** 및 **[!UICONTROL 페이로드]**(JWT 페이로드)에 클라이언트 ID를 지정합니다.

   **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   IMS 계정이 구성되었습니다.

   ![IMS 계정 구성](assets/create-new-integration6.png)


1. IMS 계정 구성을 선택하고 **[!UICONTROL 상태 확인]**&#x200B;을 클릭합니다.

   대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 구성이 성공하면 *토큰이 성공적으로 검색되었습니다.*&#x200B;라는 메시지가 나타납니다.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>IMS 구성은 하나만 있어야 합니다.
>
>IMS 구성이 상태 검사를 통과하는지 확인합니다. 구성이 상태 검사를 통과하지 않으면 구성이 잘못된 것입니다. 이 구성을 삭제하고 유효한 새 구성을 만들어야 합니다.

### 클라우드 서비스 구성 {#configure-the-cloud-service}

다음 단계를 수행하여 Brand Portal 클라우드 서비스를 구성합니다.

1. AEM Assets에 로그인합니다.

1. **도구** 패널에서 **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**&#x200B;로 이동합니다.

1. Brand Portal 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

1. 구성에 대한 **[!UICONTROL 제목]**&#x200B;을 지정합니다.

   [IMS 계정을 구성하는 동안 만든 IMS 구성을 선택합니다](#create-ims-account-configuration).

   **[!UICONTROL 서비스 URL]** 필드에서 Brand Portal 테넌트 URL을 지정합니다.

   ![](assets/create-cloud-service.png)

1. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 클라우드 구성이 만들어집니다.

   이제 AEM Assets as a [!DNL Cloud Service] 인스턴스가 Brand Portal 테넌트로 구성됩니다.

이제 분배 에이전트를 확인하고 자산을 Brand Portal에 게시하여 구성을 테스트할 수 있습니다.

<!--
### Test configuration {#test-configuration}

Perform the following steps to validate the configuration:

1. Log in to AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

    ![](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)


1. Click **[!UICONTROL Publish to Brand Portal]** to open the distribution agent. 

   You can see the distribution queues under the **[!UICONTROL Status]** tab. 
   
   A distribution agent contains two queues: 
   * **processing-queue**: for the distribution of assets to Brand Portal. 

   * **error-queue**: for the assets where distribution has failed. 
   
   >[!NOTE]
   >
   >It is recommended to review the failures and  clear the **error-queue** periodically.  

   ![](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets as a [!DNL Cloud Service] and Brand Portal, click on the **[!UICONTROL Test Connection]** icon.

   ![](assets/test-bpconfig4.png)

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

   ![](assets/test-bpconfig5.png)

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
