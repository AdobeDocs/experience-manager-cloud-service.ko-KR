---
title: 브랜드 포털에서 AEM Assets 클라우드 서비스 구성
description: 브랜드 포털에서 AEM Assets 클라우드 서비스를 구성합니다.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: d644fc348ff6d62c03100941b96c03049f345763

---


# Brand Portal에서 AEM Assets 구성 {#configure-aem-assets-with-brand-portal}

이제 AEM(Adobe Experience Manager) Assets은 Adobe I/O를 통해 Brand Portal에 구성되며, Brand Portal은 Brand Portal 임차인의 인증을 위해 IMS 토큰을 받습니다.

## 전제 조건 {#prerequisites}

Brand Portal에 AEM Assets을 구성하려면 다음이 필요합니다.

* AEM Assets 클라우드 인스턴스 실행
* Brand Portal 임차인 URL.
* Brand Portal 임차인의 IMS 조직에 대한 시스템 관리자 권한이 있는 사용자.

**추가 쿼리는** 지원 센터에 문의하십시오.

## 구성 만들기 {#create-new-configuration}

Adobe I/O에서 구성을 만들어 브랜드 포털에서 AEM Assets 클라우드 인스턴스를 구성할 수 있습니다.

나열된 시퀀스에서 다음 단계를 수행합니다.
1. [공개 인증서 받기](#public-certificate)
1. [Adobe I/O 통합 만들기](#createnewintegration)
1. [IMS 계정 구성 만들기](#create-ims-account-configuration)
1. [클라우드 서비스 구성](#configure-the-cloud-service)
1. [구성 테스트](#test-configuration)

### IMS 구성 만들기 {#create-ims-configuration}

IMS 구성은 AEM Assets 작성자 인스턴스로 Brand Portal 임차인을 인증합니다.

IMS 구성에는 다음 두 단계가 포함됩니다.

* [공개 인증서 받기](#public-certificate)
* [IMS 계정 구성 만들기](#create-ims-account-configuration)

### 공개 인증서 받기 {#public-certificate}

공개 인증서를 사용하여 Adobe I/O에서 프로필을 인증할 수 있습니다.

1. AEM Assets 클라우드 인스턴스에 로그인합니다.

1. From **tool** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![Adobe IMS 계정 구성 UI](assets/ims-configuration1.png)

1. Adobe IMS 구성 페이지가 열립니다.

   **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   It will take you to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page.

1. 기본적으로 **인증서** 탭이 열립니다.

   **클라우드 솔루션**&#x200B;에서 **[!UICONTROL Adobe Brand Portal]**&#x200B;을 선택합니다.

1. Mark the check box **[!UICONTROL Create new certificate]** and specify an **alias** for the certificate. 별칭은 대화 상자의 이름 역할을 합니다.

1. **[!UICONTROL 인증서 만들기]**&#x200B;를 클릭합니다. 대화 상자가 나타납니다. **[!UICONTROL 확인]**&#x200B;을 클릭하여 공개 인증서를 생성합니다.

   ![인증서 만들기](assets/ims-config2.png)

1. **[!UICONTROL 공개 키 다운로드]**&#x200B;를 클릭하고 컴퓨터에 *AEM-Adobe-IMS.crt* 인증서 파일을 저장합니다. 이 인증서 파일은 [Adobe I/O 통합을 만드는](#createnewintegration) 데 사용됩니다.

   ![인증서 다운로드](assets/ims-config3.png)

1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   **계정** 탭에서 Adobe IMS 계정을 만듭니다. 이를 위해서는 통합 세부 정보가 필요합니다. 지금은 이 페이지를 열어 두십시오.

   새 탭을 열고 [Adobe I/O 통합을 만들어](#createnewintegration) IMS 계정 구성에 대한 통합 세부 정보를 가져옵니다.

### Adobe I/O 통합 만들기 {#createnewintegration}

Adobe I/O 통합은 IMS 계정 구성을 설정하는 데 필요한 API 키, 클라이언트 암호 및 페이로드(JWT)를 생성합니다.

1. Brand Portal 임차인의 IMS 조직에 대한 시스템 관리자 권한으로 Adobe I/O 콘솔에 로그인합니다.

   기본 URL: [https://console.adobe.io/](https://console.adobe.io/)

1. **[!UICONTROL 통합 만들기]**&#x200B;를 클릭합니다.

1. **[!UICONTROL API에 액세스]**&#x200B;를 선택하고 **[!UICONTROL 계속]**&#x200B;을 클릭합니다.

   ![새 통합 만들기](assets/create-new-integration1.png)

1. 새 통합 페이지 만들기가 열립니다.

   드롭다운 목록에서 조직을 선택합니다.

   **[!UICONTROL Experience Cloud]**&#x200B;에서 **[!UICONTROL AEM Brand Portal]**&#x200B;을 선택하고 **[!UICONTROL 계속]**&#x200B;을 클릭합니다.

   Brand Portal 옵션이 비활성화되어 있는 경우 **[!UICONTROL Adobe 서비스]** 옵션 위의 드롭다운 상자에서 올바른 조직을 선택했는지 확인합니다. 조직을 모르는 경우 관리자에게 문의하십시오.

   ![통합 만들기](assets/create-new-integration2.png)

1. 통합의 이름과 설명을 지정합니다. **[!UICONTROL 컴퓨터에서 파일 선택]**&#x200B;을 클릭하고 [공개 인증서 받기](#public-certificate) 섹션에서 다운로드한 `AEM-Adobe-IMS.crt` 파일을 업로드합니다.

1. 조직의 프로필을 선택합니다.

   또는 기본 프로필 **[!UICONTROL Assets Brand Portal]**&#x200B;을 선택하고 **[!UICONTROL 통합 만들기]**&#x200B;를 클릭합니다. 통합이 생성됩니다.

1. 통합 정보를 보려면 **[!UICONTROL 통합 세부 사항 계속]**&#x200B;을 클릭합니다.

   **[!UICONTROL API 키]**&#x200B;를 복사합니다.

   **[!UICONTROL 클라이언트 암호 검색]**&#x200B;을 클릭하고 클라이언트 암호 키를 복사합니다.

   ![통합 API 키, 클라이언트 암호 및 페이로드 정보](assets/create-new-integration3.png)

1. **[!UICONTROL JWT]** 탭으로 이동하고 **[!UICONTROL JWT 페이로드]**&#x200B;를 복사합니다.

   API 키, 클라이언트 암호 키 및 JWT 페이로드 정보를 사용하여 IMS 계정 구성을 만듭니다.

### IMS 계정 구성 만들기 {#create-ims-account-configuration}

다음 단계를 수행했는지 확인합니다.

* [공개 인증서 받기](#public-certificate)
* [Adobe I/O 통합 만들기](#createnewintegration)

**IMS 계정 구성을 만드는 단계:**

1. IMS 구성 페이지를 열고 **[!UICONTROL 계정]** 탭을 엽니다. [공개 인증서 받기](#public-certificate)섹션의 끝에 페이지를 열어 두었습니다.

1. IMS 계정의 **[!UICONTROL 직책]**&#x200B;을 지정합니다.

   **[!UICONTROL 인증 서버]**&#x200B;에 URL [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)을 입력합니다.

   [Adobe I/O 통합 만들기](#createnewintegration)에서 마지막에 복사한 API 키, 클라이언트 암호 및 JWT 페이로드를 붙여 넣습니다.

   **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   통합이 생성됩니다.

   ![IMS 계정 구성](assets/create-new-integration6.png)


1. IMS 구성을 선택하고 **[!UICONTROL 상태 확인]**&#x200B;을 클릭합니다. 대화 상자가 나타납니다.

   ]**확인**[!UICONTROL &#x200B;을 클릭합니다. 연결이 성공하면 *토큰이 검색되었습니다.* 메시지가 나타납니다.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>상태 확인을 전달하는 IMS 구성은 하나만 있어야 합니다. IMS 구성을 여러 개 만들지 마십시오.
>
>구성이 상태 검사를 통과하지 않으면 구성이 잘못되었습니다. 이를 삭제하고 유효한 새 구성을 만들어야 합니다.



### 클라우드 서비스 구성 {#configure-the-cloud-service}

Brand Portal 클라우드 서비스 구성을 만들려면 다음 단계를 수행하십시오.

1. AEM Assets 클라우드 인스턴스에 로그인합니다.

1. From **tool** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

   Brand Portal 구성 페이지가 열립니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

1. 구성의 **[!UICONTROL 제목]**&#x200B;을 지정합니다.

   [IMS 계정 구성 만들기](#create-ims-account-configuration) 단계에서 생성한 IMS 구성을 선택합니다.

   **[!UICONTROL 서비스 URL]**&#x200B;에 Brand Portal 임차인 URL을 입력합니다.

   ![](assets/create-cloud-service.png)

1. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 클라우드 구성이 생성됩니다. 이제 AEM Assets 클라우드 인스턴스가 브랜드 포털 임차인으로 구성됩니다.

### 구성 테스트 {#test-configuration}

1. AEM Assets 클라우드 인스턴스에 로그인합니다.

1. 도구 **도구** ![패널에서 배포](assets/tools.png) > **[!UICONTROL 배포]******&#x200B;를탐색합니다.

   ![](assets/test-bpconfig1.png)

1. 배포 페이지가 열립니다.

   브랜드 포털에 게시 아래에 브랜드 포털 배포 에이전트가 `bpdistributionagent0` 만들어집니다 ****.

   Click **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >기본적으로 브랜드 포털 테넌트에 대해 하나의 배포 에이전트가 만들어집니다.

1. 배포 에이전트 페이지가 열립니다. 기본적으로 배포 **[!UICONTROL 대기열을 채우는]** 상태 탭이 열립니다.

   배포 에이전트에는 두 개의 대기열이 있습니다.
   * **처리 대기열**:브랜드 포털에 자산을 배포하기 위해.

   * **error-queue**:for the assets where distribution has failed.
   >[!NOTE]
   >
   >오류를 검토하고 **오류 큐를** 정기적으로 지우는 것이 좋습니다.

   ![](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets and Brand Portal, click **[!UICONTROL Test Connection]**.

   ![](assets/test-bpconfig4.png)

   테스트 패키지가 성공적으로 배달되었다는 메시지가 페이지 하단에 나타납니다.

   >[!NOTE]
   >
   >자산(실행 중인 큐)의 배포가 실패할 수 있으므로 배포 에이전트를 비활성화하지 마십시오.


AEM Assets 클라우드 인스턴스가 브랜드 포털로 성공적으로 구성되었으므로 이제 다음을 수행할 수 있습니다.

* [AEM Assets에서 Brand Portal에 자산 게시](publish-to-brand-portal.md)
* [AEM Assets에서 Brand Portal에 폴더 게시](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [AEM Assets에서 Brand Portal에 컬렉션 게시](publish-to-brand-portal.md#publish-collections-to-brand-portal)

위의 내용 외에도 메타데이터 스키마, 이미지 사전 설정, 검색 패싯 및 태그를 AEM Assets의 브랜드 포털에 게시할 수 있습니다.

* [브랜드 포털에 사전 설정, 스키마 및 패싯 게시](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [태그를 Brand Portal에 게시](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


자세한 내용은 [브랜드 포털 설명서를](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) 참조하십시오.


## 배포 로그 {#distribution-logs}

배포 에이전트에서 수행한 작업에 대한 자세한 내용은 로그를 확인할 수 있습니다.

예를 들어, 구성을 확인하기 위해 AEM 자산에서 브랜드 포털에 자산을 게시했습니다.

1. 연결 테스트에 표시된 대로 단계(1-4단계) **[!UICONTROL 를]** 따라 배포 에이전트 페이지로 이동합니다.

1. 로그를 **[!UICONTROL 클릭하여]** 배포 로그를 봅니다. 여기서 처리 및 오류 로그를 볼 수 있습니다.

   ![](assets/test-bpconfig5.png)

배포 에이전트가 다음 로그를 생성합니다.

* 정보:배포 에이전트를 활성화하는 성공적인 구성을 트리거하는 시스템 생성 로그입니다.
* DSTRQ1(요청 1):테스트 연결 시 트리거됩니다.

자산을 게시할 때 다음 요청 및 응답 로그가 생성됩니다.

**배포 에이전트 요청**:
* DSTRQ2(요청 2):자산 게시 요청이 트리거됩니다.
* DSTRQ3(요청 3):시스템이 다른 요청을 트리거하여 자산이 있는 폴더를 게시하고 브랜드 포털에서 폴더를 복제합니다.

**배포 에이전트 응답**:
* queue-bdistributionAgent0(DSTRQ2):자산이 브랜드 포털에 게시됩니다.
* queue-bdistributionAgent0(DSTRQ3):시스템이 브랜드 포털에서 자산을 포함하는 폴더를 복제합니다.

위의 예에서 추가 요청 및 응답이 트리거됩니다. 자산이 처음으로 게시되었기 때문에 시스템이 브랜드 포털에서 상위 폴더(경로 추가)를 찾을 수 없으므로 자산이 게시되는 브랜드 포털에서 동일한 이름으로 상위 폴더를 만들기 위한 추가 요청을 트리거합니다.

>[!NOTE]
>
>상위 폴더가 브랜드 포털에 없거나(위 예에서) 상위 폴더가 AEM 자산에서 수정된 경우에 대한 추가 요청이 생성됩니다.



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
