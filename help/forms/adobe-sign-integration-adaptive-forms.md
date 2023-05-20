---
title: Adobe Sign과 AEM Forms를 통합하는 방법은?
description: ' [!DNL AEM Forms] as a Cloud Service용 Adobe Sign을 구성하는 방법에 대해 알아보시겠어요?'
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 7b233d95e27325a7edb22948669f6c0d96e1f380
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 70%

---

# [!DNL AEM Forms] as a Cloud Service와 [!DNL Adobe Sign] 통합  {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign]은 적응형 양식용 전자 서명 워크플로를 가능하게 합니다. 전자 서명은 법무, 판매, 임금, 인적 자원 관리 등의 다양한 분야에서 문서를 처리하는 워크플로를 개선합니다.

대표적인 [!DNL Adobe Sign] 및 적응형 양식 시나리오에서 사용자는 서비스에 적용할 적응형 양식에 정보를 입력합니다. 신용 카드 신청 양식과 시민 혜택 양식을 예로 들 수 있습니다. 사용자가 신청 양식에 정보를 입력하고 이를 제출한 뒤 서명하면, 이후의 액션이 가능하도록 양식이 서비스 제공자에게 전달됩니다. 서비스 제공자는 신청서를 검토하고 [!DNL Adobe Sign]을 사용해 신청을 승인된 것으로 표시합니다. [!DNL Adobe Sign]을 [!DNL AEM Forms]에 통합하면 유사한 전자 서명 워크플로를 사용할 수 있습니다.

[!DNL Adobe Sign]을 [!DNL AEM Forms]에 사용하려면 AEM Cloud Service에서 [!DNL Adobe Sign]을 구성하십시오.

## 전제 조건 {#prerequisites}

[!DNL Adobe Sign]을 [!DNL AEM Forms]에 통합하려면 다음이 필요합니다.

* 활성 [Adobe Sign 개발자 계정](https://acrobat.adobe.com/us/en/sign/developer-form.html).
* [Adobe Sign API 애플리케이션](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* [!DNL Adobe Sign] API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 보안).
* 작성자에 대해 [동일한 암호 키](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=en#make-sure-you-properly-replicate-encryption-keys-when-needed)를 사용하고 인스턴스를 게시합니다.
* (정부 ID 기반 인증만 해당) 정부 ID 인증을 위한 [인증 방법](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport)을 활성화합니다.

## [!DNL AEM Forms]를 사용하여 [!DNL Adobe Sign] 구성 {#configure-adobe-sign-with-aem-forms}

전제 조건이 갖추어지면 다음 단계를 통해 작성자 인스턴스에서 [!DNL AEM Forms]를 사용하여 [!DNL Adobe Sign]을 구성하십시오.

1. AEM Forms 작성자 인스턴스에서 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**.
1. 다음에서 **[!UICONTROL 구성 브라우저]** 페이지, 탭 **[!UICONTROL 만들기]**.
1. 다음에서 **[!UICONTROL 구성 만들기]** 대화 상자, 지정 **[!UICONTROL 제목]** 구성의 경우 활성화 **[!UICONTROL 클라우드 구성]**, 및 탭 **[!UICONTROL 만들기]**. 이를 통해 Cloud Service를 저장하는 구성 컨테이너가 생성됩니다. 폴더 이름에는 공백이 없어야 합니다.
1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** 이전 단계에서 생성한 구성 컨테이너를 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때에서 컨테이너 이름을 지정합니다 **[!UICONTROL 구성 컨테이너]** 필드.

1. 구성 페이지에서 을 누릅니다. **[!UICONTROL 만들기]** 만들려면 [!DNL Adobe Sign] AEM Forms의 구성
1. 다음에서 **[!UICONTROL 일반]** 의 탭 **[!UICONTROL Adobe Sign 구성 만들기]** 페이지, 지정 **[!UICONTROL 이름]** 구성을 보려면 다음을 누르십시오. **[!UICONTROL 다음]**. 다음을 선택적으로 지정할 수 있습니다. **[!UICONTROL 제목]** 을(를) 찾아 선택 **[!UICONTROL 축소판]** 구성.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. 이 URL은 이후 단계에서 [!DNL AEM Forms]를 사용해 [!DNL Adobe Sign]을 구성하는 데 필요합니다. 누르기 **[!UICONTROL 다음]**.

1. 다음에서 **[!UICONTROL 설정]** 탭, **[!UICONTROL OAuth URL]** 필드에는 기본 URL이 포함되어 있습니다. URL 형식은 다음과 같습니다.

   `https://<shard>/public/oAuth/v2`

   예:
   `https://secure.na1.echosign.com/public/oauth/v2`

   여기에서

   **na1**&#x200B;은 기본값 데이터베이스 분할을 의미합니다. 데이터베이스 분할의 값을 수정할 수 있습니다. [!DNL  Adobe Sign] 클라우드 구성이 [올바른 분할](https://helpx.adobe.com/sign/using/identify-account-shard.html)을 가리켜야 합니다.

   Adobe Experience Manager 기능이나 구성 요소에 대한 또 다른 [!DNL Adobe Sign] 구성을 생성하는 경우, 모든 [!DNL Adobe Sign] 클라우드 구성이 동일한 분할을 가리켜야 합니다.

   >[!NOTE]
   >
   > 유지 **Adobe Sign 구성 만들기** 페이지가 열립니다. 닫지 마세요. 다음을 검색할 수 있습니다. **클라이언트 ID** 및 **클라이언트 암호** 에 대한 OAuth 설정을 구성한 후 [!DNL Adobe Sign] 다음 단계에 설명된 대로 애플리케이션.


1. [!DNL Adobe Sign] 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 [!DNL Adobe Sign] 개발자 계정에 로그인합니다.
   1. 다음에 대해 구성된 애플리케이션 선택 [!DNL AEM Forms], 및 탭 **[!UICONTROL 애플리케이션에 대한 OAuth 구성]**.
   1. 다음에서 **[!UICONTROL 리디렉션 URL]** 상자에서 이전 단계(7단계)에서 복사한 URL을 추가하고 을 클릭합니다. **[!UICONTROL 저장]**.
   1. 에 대해 다음 범위 활성화 [!DNL Adobe Sign] 애플리케이션 및 클릭 **[!UICONTROL 저장]**.
   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   [!DNL Adobe Sign] 애플리케이션에 대한 OAuth 설정을 구성하고 키를 얻는 방법에 대한 단계별 정보는 [애플리케이션에 대한 oAuth 설정 구성](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 개발자 문서를 참조하십시오.

   ![OAuth Config](assets/oauthconfig_new.png)

1. 로 돌아가기 **[!UICONTROL Adobe Sign 구성 만들기]** 페이지를 가리키도록 업데이트하는 중입니다. 다음에서 **[!UICONTROL 설정]** 탭에서 [**[!UICONTROL 클라이언트 ID]** (애플리케이션 ID라고도 함) 및 **[!UICONTROL 클라이언트 암호]**]. 사용 [Adobe Sign 애플리케이션의 클라이언트 ID 및 클라이언트 암호](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) 이전 단계에서 을(를) 만들었습니다.

1. 다음 항목 선택 **[!UICONTROL 첨부 파일에 Adobe Sign 사용]** 적응형 양식에 첨부된 파일을 해당 파일에 추가하는 옵션 [!DNL Adobe Sign] 서명을 위해 문서를 보냈습니다.

1. 누르기 **[!UICONTROL Adobe Sign에 연결]**. 자격 증명을 입력하라는 메시지가 뜨면 [!DNL Adobe Sign] 애플리케이션 생성 시 사용한 계정의 사용자 이름과 비밀번호를 입력합니다. 다음에 대한 액세스를 확인해달라는 메시지가 뜨는 경우 `your developer account`, 클릭 **[!UICONTROL 액세스 허용]**. 자격 증명이 올바르고 [!DNL Adobe Sign] 개발자 계정에 대한 [!DNL AEM Forms]의 액세스를 허용하면 아래에 제시된 것과 비슷한 성공 메시지가 표시됩니다.

   ![Adobe Sign 클라우드 구성 성공](assets/adobe-sign-cloud-configuration-success.png)

1. 누르기 **[!UICONTROL 만들기]** 을(를) 만들려면 [!DNL Adobe Sign] 구성.

1. 구성을 선택하고 **[!UICONTROL 게시]**&#x200B;을 클릭하고 구성을 선택한 다음 을 클릭합니다 **[!UICONTROL 게시]**. 해당 게시 환경에 구성이 복사됩니다.

1. 위의 모든 단계를 개발자, 스테이지 및 생산 인스턴스(어느 것이든 남은 인스턴스에)에 반복하여, 해당 환경을 위한 [!DNL AEM Forms]를 사용한 [!DNL Adobe Sign] 구성을 완료합니다.

이제 [적응형 양식에 Adobe Sign 필드 추가를 사용](working-with-adobe-sign.md)할 수 있습니다. Cloud Service에 사용되는 구성 컨테이너를 [!DNL Adobe Sign]을 위해 활성화하고자 하는 모든 적응형 양식에 추가해야 합니다. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

## (AEM Workflow만 해당) [!DNL Adobe Sign] 스케줄러를 구성하여 서명 상태 동기화 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

[!DNL Adobe Sign] 워크플로 단계를 사용해 적응형 양식에 서명할 때, 워크플로 단계의 구성에 따라 양식이 서명자들 간에 전달되거나 모든 서명자에게 동시에 전달될 수 있습니다. [!DNL Adobe Sign]이 활성화된 적응형 양식은 모든 서명자가 서명 프로세스를 완료한 후에만 Experience Manager Forms Server에 제출됩니다.

기본값으로 [!DNL Adobe Sign] 스케줄러 서비스는 서명자 응답을 24시간마다 점검(가져옴)합니다. 해당 환경에 맞게 기본값 간격을 변경할 수 있습니다.

기본값 간격을 변경하려면 **Adobe Sign 구성 서비스** 구성의 **sign.status.exp** 속성에 대해 [cron 표현식](https://en.wikipedia.org/wiki/Cron#CRON_expression)을 지정하십시오.

예를 들어 매일 오전 00:00에 구성 서비스를 실행하려면 **Adobe Sign 구성 서비스** 구성의 **sign.status.exp** 속성을 설정하여 `0 0 0 1/1 * ? *`를 지정하십시오. 다음의 JSON 파일은 매일 오전 00:00에 구성 서비스를 실행하는 예를 나타낸 것입니다.

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

구성의 값을 설정하려면 [AEM SDK를 사용해 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process)하십시오.

<!-- , perform the following steps:

1. Log in to [!DNL AEM Forms] Server with admin credentials and navigate to **[!UICONTROL Tools]** &gt;**[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   You can also open the following URL in a browser window:
   `https://server/system/console/configMgr`

1. Locate and open the **[!UICONTROL Adobe Sign Configuration Service]** option. Specify a [cron expression](https://en.wikipedia.org/wiki/Cron#CRON_expression) in the **Status Update Scheduler Expression** field and click **Save**. For example, to run the configuration service daily at 00:00 am, specify `0 0 0 1/1 * ? *` in the **Status Update Scheduler Expression** field.

Default interval to sync status of [!DNL Adobe Sign] is now changed. -->

## 관련 문서 {#related-articles}

* [적응형 양식에서 Adobe Sign 사용](working-with-adobe-sign.md)

* [적응형 양식과 Adobe Sign을 사용하는 모범 사례](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
