---
title: 향상된 스마트 태그
description: Adobe Sensei의 AI 및 ML 서비스를 사용하여 컨텍스트 기반의 수사적 비즈니스 태그를 적용하여 에셋 검색과 콘텐츠 제작 시간을 향상시킬 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 41684858f1fe516046b9601c1d869fff180320e0
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 1%

---


# Experience Manager를 구성하여 에셋 스마트 태그 지정 {#configure-aem-for-smart-tagging}

분류 제어 어휘를 사용하여 자산에 태그를 지정하면 태그 기반 검색으로 자산을 쉽게 식별하고 검색할 수 있습니다. Adobe는 이미지 트레이닝을 위해 인공 지능과 머신 러닝 알고리즘을 사용하는 스마트 태그를 제공합니다. 스마트 태그는 [Adobe Sensei의](https://www.adobe.com/sensei/experience-cloud-artificial-intelligence.html) 인공 지능 프레임워크를 사용하여 태그 구조 및 비즈니스 분류 체계에 대한 이미지 인식 알고리즘을 교육합니다.

스마트 태그 기능은 추가 기능으로 구입할 수 있습니다 [!DNL Experience Manager]. 구입하면 Adobe 개발자 콘솔로 연결되는 링크가 포함된 이메일이 조직 관리자에게 전송됩니다. 관리자는 링크에 액세스하여 Adobe 개발자 콘솔을 [!DNL Experience Manager] 사용하여 스마트 태그를 통합합니다.

<!-- TBD: 
1. Can a similar flowchart be created about how training works in CS? ![flowchart](assets/flowchart.gif)
2. Is there a link to buy SCS or initiate a sales call.
3. Keystroke all steps and check all screenshots.
4. Post-GA, if time permits, create a video.
-->

## Adobe 개발자 콘솔과 통합 {#aio-integration}

SCS를 사용하여 이미지에 태그를 지정하려면 Adobe 개발자 콘솔을 사용하여 스마트 태그 서비스 [!DNL Adobe Experience Manager] 와 통합하십시오. 백엔드 [!DNL Experience Manager] 는 요청을 서비스로 전달하기 전에 Adobe 개발자 콘솔 게이트웨이로 서비스 자격 증명을 인증합니다.

* 공개 키 [!DNL Experience Manager] 를 생성하기 위한 구성을 만듭니다. OAuth 통합에 대한 공용 인증서를 얻습니다.
* Adobe 개발자 콘솔에서 통합을 만들고 생성된 공개 키를 업로드합니다.
* Adobe 개발자 콘솔의 API 키 및 기타 자격 증명을 사용하여 인스턴스를 [!DNL Experience Manager] 구성합니다.
* 자산 업로드 시 자동 태그 지정을 활성화합니다(선택 사항).

### Adobe 개발자 콘솔 통합을 위한 사전 요구 사항 {#prerequisite-for-aio-integration}

스마트 태그를 사용하려면 먼저 Adobe 개발자 콘솔에서 통합을 만들려면 다음을 확인하십시오.

* 조직에 대한 관리자 권한이 있는 Adobe ID 계정
* 조직에서 스마트 태그를 사용할 수 있습니다.

### Obtain a public certificate {#obtain-public-certificate}

공용 인증서를 사용하면 Adobe 개발자 콘솔에서 프로필을 인증할 수 있습니다. 내에서 인증서를 만듭니다 [!DNL Experience Manager].

1. 사용자 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL Adobe IMS 구성에 액세스합니다]**.

1. Adobe [!UICONTROL IMS 구성] 페이지에서 만들기를 **[!UICONTROL 클릭합니다]**. 클라우드 **[!UICONTROL 솔루션]** 메뉴에서 **[!UICONTROL 스마트 태그를 선택합니다]**.

1. 새 인증서 **[!UICONTROL 만들기를 선택합니다]**. 이름을 입력하고 인증서 **[!UICONTROL 만들기를 클릭합니다]**. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. 공개 **[!UICONTROL 키 다운로드를 클릭합니다]**.

   ![Experience Manager 스마트 태그 생성 공개 키](assets/aem_smarttags-config1.png)

### 인증서가 만료된 경우 다시 구성 {#certrenew}

인증서가 만료되면 더 이상 신뢰되지 않습니다. 새 인증서를 추가하려면 다음 단계를 따르십시오. 만료된 인증서는 갱신할 수 없습니다.

1. 관리자로 [!DNL Experience Manager] 배포 로그인 도구 **** > **[!UICONTROL 보안]** > **[!UICONTROL 사용자를]**&#x200B;클릭합니다.

1. dam-update-service **** 사용자를 찾아 클릭합니다. Keystore **[!UICONTROL 탭을]** 클릭합니다.
1. 만료된 인증서로 기존 **[!UICONTROL 유사한 검색]** 키 저장소를 삭제합니다. Click **[!UICONTROL Save &amp; Close]**.

   ![새 보안 인증서를 추가하려면 Keystore에서 기존 유사검색항목 삭제](assets/smarttags_delete_similaritysearch_keystore.png)

   *그림: 새 보안 인증서를 추가하려면 Keystore의 기존`similaritysearch`항목을 삭제합니다.*

1. 사용자 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL Adobe IMS 구성에 액세스합니다]**. 사용 가능한 스마트 태그 구성을 엽니다. 공용 인증서를 다운로드하려면 [공용 인증서 **[!UICONTROL 다운로드]를 클릭합니다]**.

1. https://console.adobe.io [에](https://console.adobe.io) 액세스하여 프로젝트의 기존 서비스로 이동합니다. 새 인증서를 업로드하고 구성합니다. 구성에 대한 자세한 내용은 Adobe 개발자 콘솔 [만들기의 지침을 참조하십시오](#create-aio-integration).

### 통합 만들기 {#create-aio-integration}

스마트 태그를 사용하려면 Adobe 개발자 콘솔에서 통합을 만들어 API 키, 기술 계정 ID, 조직 ID 및 클라이언트 암호를 생성합니다.

1. https://console.adobe.io [브라우저에](https://console.adobe.io/) 액세스합니다. 적절한 계정을 선택하고 관련 조직 역할이 시스템 관리자인지 확인합니다.
1. 원하는 이름으로 프로젝트를 만듭니다. API **[!UICONTROL 추가를 클릭합니다]**.
1. API **[!UICONTROL 추가]** 페이지에서 **[!UICONTROL Experience Cloud]** 를 **[!UICONTROL 선택하고]**&#x200B;스마트 콘텐츠를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 공개 키 **[!UICONTROL 업로드를 선택합니다]**. 다운로드한 인증서 파일을 제공합니다 [!DNL Experience Manager]. 성공적으로 [!UICONTROL 업로드된 공개 키가] 표시됩니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. [!UICONTROL 새 서비스 계정(JWT) 자격 증명] 만들기 페이지에는 방금 구성된 서비스 계정에 대한 공개 키가 표시됩니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 제품 프로필 **[!UICONTROL 선택]** 페이지에서 **[!UICONTROL 스마트 콘텐츠 서비스를 선택합니다]**. 구성된 **[!UICONTROL API 저장을 클릭합니다]**. 페이지에 구성에 대한 자세한 정보가 표시됩니다. 스마트 태그를 더 구성할 때 Experience Manager에서 이러한 값을 복사하고 추가하려면 이 페이지를 열어 두십시오 [!DNL Experience Manager].

   ![개요 탭에서 통합에 제공된 정보를 검토할 수 있습니다.](assets/integration_details.png)

### 스마트 태그 구성 {#configure-smart-content-service}

통합을 구성하려면 Adobe 개발자 콘솔 통합에서 페이로드, 클라이언트 암호, 인증 서버 및 API 키 필드 값을 사용하십시오.

1. 사용자 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL Adobe IMS 구성에 액세스합니다]**.
1. Adobe **[!UICONTROL IMS 기술 계정 구성]** 페이지에 액세스하여 원하는 **[!UICONTROL 제목을 제공합니다]**.
1. 인증 **[!UICONTROL 서버]** 필드에서 `https://ims-na1.adobelogin.com` URL을 제공합니다.
1. API **[!UICONTROL 키]** 필드에서 **[!UICONTROL 클라이언트 ID]** 를 [!DNL Adobe Developer Console]제공합니다.
1. [ **[!UICONTROL 클라이언트 암호]** ] 필드에서 **[!UICONTROL 클라이언트 암호를]** 의 암호 [!DNL Adobe Developer Console]로 지정합니다. 클라이언트 암호 **[!UICONTROL 검색]** 옵션을 클릭하여 확인합니다.
1. 프로젝트의 왼쪽 여백 [!DNL Adobe Developer Console]에서 **[!UICONTROL 서비스 계정(JWT)]** 을 클릭합니다. JWT **[!UICONTROL 생성]** 탭을 클릭합니다. 복사 **[!UICONTROL 를]** 클릭하여 표시된 JWT 페이로드를 **[!UICONTROL 복사합니다]**. 페이로드 필드 **[!UICONTROL 에 이]** 값을 [!DNL Experience Manager]입력합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

### 구성 유효성 확인 {#validate-the-configuration}

구성을 완료한 후 다음 단계에 따라 구성을 확인합니다.

1. 사용자 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL Adobe IMS 구성에 액세스합니다]**.

1. 스마트 태그 구성을 선택합니다. 도구 모음 **[!UICONTROL 에서 상태]** 확인을 클릭합니다. **[!UICONTROL 확인]**&#x200B;을 클릭합니다. 정상 [!UICONTROL 구성] 메시지가 표시된 대화 상자에서 구성이 작동하는지 확인합니다.

![스마트 태그 구성 유효성 확인](assets/smart-tag-config-validation.png)

## 새로 업로드한 자산에 대한 스마트 태그 지정 사용(선택 사항) {#enable-smart-tagging-for-uploaded-assets}

1. 에서 [!DNL Experience Manager]도구 > 워크플로우 > 모델 **[!UICONTROL 으로 이동합니다]**.
1. 워크플로우 **[!UICONTROL 모델]** 페이지에서 **[!UICONTROL DAM 자산]** 업데이트 워크플로우 모델을선택합니다.
1. 도구 **[!UICONTROL 모음에서]** 편집을 클릭합니다.
1. 사이드 패널을 확장하여 단계를 표시합니다. DAM 워크플로우 섹션에서 **[!UICONTROL 사용할 수 있는 스마트 태그]** 자산 **[!UICONTROL 단계를 드래그하여]** 축소판 처리단계 뒤에 놓습니다.

   ![DAM 자산 업데이트 워크플로우에서 프로세스 축소판 단계 이후 스마트 태그 자산 추가](assets/chlimage_1-105.png)

   *그림: DAM 자산 업데이트 워크플로우에서 프로세스 축소판 단계 후에 스마트 태그 자산 단계를 추가합니다.*

1. 구성할 단계를 엽니다. [ **[!UICONTROL 고급 설정]**] 아래에서 [ **[!UICONTROL 처리기 고급]** ] 옵션을 선택해야 합니다.

   ![워크플로우의 다음 단계로 이동할 핸들러를 설정하는 중입니다.](assets/smart-tags-workflow-handler-setting.png)

1. 태그를 **[!UICONTROL 예측할 때 오류를 무시하도록 워크플로우에]** 하려면 인수 탭에서 오류 **** 무시를 선택합니다. 폴더에서 스마트 태그 지정 사용 여부에 관계없이 업로드될 때 자산에 태그를 지정하려면 스마트 태그 플래그 **[!UICONTROL 무시]**&#x200B;를 선택합니다.

1. 확인 **[!UICONTROL 을]** 클릭하여 프로세스 단계를 닫은 다음 워크플로우를 저장합니다. 동기화를 **[!UICONTROL 클릭합니다]**.

>[!MORELIKETHIS]
>
>* [스마트 서비스를 사용하여 에셋에 태그 지정](smart-tags.md)

