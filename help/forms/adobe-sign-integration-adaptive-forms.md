---
title: Adobe Sign을 AEM Forms과 통합하는 방법
description: Adobe Sign을 구성하는 방법 알아보기 [!DNL AEM Forms] as a Cloud Service?
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# 통합 [!DNL Adobe Sign] with [!DNL AEM Forms] as a Cloud Service  {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] 적응형 Forms에 대해 전자 서명 워크플로우를 활성화합니다. 전자 서명은 법률, 영업, 급여, 인적 자원 관리 및 기타 여러 분야에 대한 문서를 처리하기 위한 워크플로우를 개선합니다.

일반적인 [!DNL Adobe Sign] 및 응용 Forms 시나리오에서 사용자는 적응형 양식을 채워 서비스에 적용합니다. 예를 들어, 신용카드 신청서와 시민 혜택 양식입니다. 사용자가 애플리케이션 양식을 작성, 제출 및 서명하면 추가 작업을 위해 양식이 서비스 공급자에게 전송됩니다. 서비스 제공업체는 애플리케이션 및 사용 검토 [!DNL Adobe Sign] 승인됨으로 표시합니다. 유사한 전자 서명 워크플로우를 사용하려면 다음을 통합할 수 있습니다 [!DNL Adobe Sign] with [!DNL AEM Forms].

를 사용하려면 [!DNL Adobe Sign] with [!DNL AEM Forms], 구성 [!DNL Adobe Sign] AEM 클라우드 서비스에서:

## 전제 조건 {#prerequisites}

통합하려면 다음을 수행해야 합니다 [!DNL Adobe Sign] with [!DNL AEM Forms]:

* 활성 [Adobe Sign 개발자 계정](https://acrobat.adobe.com/us/en/sign/developer-form.html).
* An [Adobe Sign API 애플리케이션](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* 의 자격 증명(클라이언트 ID 및 클라이언트 암호) [!DNL Adobe Sign] API 애플리케이션.
* 사용 [동일한 암호화 키](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=en#make-sure-you-properly-replicate-encryption-keys-when-needed) 작성자 및 게시 인스턴스용.
* (정부 ID 기반 인증에만 해당) [인증 방법 활성화](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html#AuditReport) 정부 ID 인증용.

## 구성 [!DNL Adobe Sign] with [!DNL AEM Forms] {#configure-adobe-sign-with-aem-forms}

사전 요구 사항이 준비되면 다음 단계를 수행하여 을 구성합니다 [!DNL Adobe Sign] with [!DNL AEM Forms] 작성자 인스턴스에 표시합니다.

1. AEM Forms 작성자 인스턴스에서 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**.
1. 설정 **[!UICONTROL 구성 브라우저]** 페이지, 탭 **[!UICONTROL 만들기]**.
1. 에서 **[!UICONTROL 구성 만들기]** 대화 상자에서 다음을 지정합니다 **[!UICONTROL 제목]** 구성에 대해 **[!UICONTROL 클라우드 구성]**, 탭 **[!UICONTROL 만들기]**. Cloud Services을 저장할 구성 컨테이너를 만듭니다. 폴더 이름에 공백이 없는지 확인합니다.
1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** 이전 단계에서 만든 구성 컨테이너를 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드.

1. 구성 페이지에서 **[!UICONTROL 만들기]** 만들기 [!DNL Adobe Sign]AEM Forms의 구성.
1. 에서 **[!UICONTROL 일반]** 의 탭 **[!UICONTROL Adobe Sign 구성 만들기]** 페이지에서, **[!UICONTROL 이름]** 구성에 대해 를 탭하고 **[!UICONTROL 다음]**. 원할 경우 **[!UICONTROL 제목]** 을(를) 찾아 **[!UICONTROL 축소판]** 참조하십시오.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. 구성하는 데 URL이 필요합니다 [!DNL Adobe Sign] 애플리케이션 [!DNL AEM Forms] 을 참조하십시오.

1. 에 대한 OAuth 설정 구성 [!DNL Adobe Sign] 애플리케이션:

   1. 브라우저 창을 열고 [!DNL Adobe Sign] 개발자 계정.
   1. 에 대해 구성된 응용 프로그램을 선택합니다 [!DNL AEM Forms], 탭 **[!UICONTROL 애플리케이션에 대한 OAuth 구성]**.
   1. 에서 **[!UICONTROL 리디렉션 URL]** 상자에서 이전 단계에서 복사한 URL을 추가하고 을(를) 클릭합니다 **[!UICONTROL 저장]**.
   1. 에 대해 다음 OAuth 설정을 사용하도록 설정합니다. [!DNL Adobe Sign] 응용 프로그램을 클릭하고 **[!UICONTROL 저장]**.
   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   에 대한 OAuth 설정을 구성하는 단계별 정보입니다 [!DNL Adobe Sign] 응용 프로그램을 사용하여 키를 얻습니다. [애플리케이션에 대한 oAuth 설정 구성](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 개발자 설명서입니다.

   ![OAuth 구성](assets/oauthconfig_new.png)

1. 로 돌아갑니다. **[!UICONTROL Adobe Sign 구성 만들기]** 페이지. 에서 **[!UICONTROL 설정]** 탭, **[!UICONTROL OAuth URL]** 필드에 기본 URL이 설명되어 있습니다. URL의 형식은 다음과 같습니다.

   `https://<shard>/public/oAuth/v2`

   예:
   `https://secure.na1.echosign.com/public/oauth/v2`

   다음의 경우:

   **na1** 기본 데이터베이스 공유 항목을 나타냅니다. 데이터베이스 공유 값에 대한 값을 수정할 수 있습니다. 다음을 확인합니다. [!DNL Adobe Sign] 클라우드 구성은 [올바른 공유](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   다른 [!DNL Adobe Sign] Adobe Experience Manager 기능 또는 구성 요소에 대해 구성하는 경우 [!DNL Adobe Sign] 클라우드 구성이 동일한 공유 항목을 가리킵니다.

1. 을(를) 지정합니다. **[!UICONTROL 클라이언트 ID]** (응용 프로그램 ID라고도 함) 및 **[!UICONTROL 클라이언트 암호]**. 이전 단계에서 만든 Adobe Sign 애플리케이션의 클라이언트 ID 및 클라이언트 암호 를 사용합니다.

1. 을(를) 선택합니다 **[!UICONTROL 첨부 파일용 Adobe Sign 활성화]** 적응형 양식에 첨부된 파일을 해당 양식에 추가 옵션 [!DNL Adobe Sign] 서명을 위해 문서를 보냈습니다.

1. 탭 **[!UICONTROL Adobe Sign에 연결]**. 자격 증명을 입력하라는 메시지가 표시되면 만드는 동안 사용되는 계정의 사용자 이름과 암호를 입력합니다 [!DNL Adobe Sign] 응용 프로그램. 에 대한 액세스 확인을 묻는 경우 `your developer account`, 클릭 **[!UICONTROL 액세스 허용]**. 자격 증명이 올바르고 [!DNL AEM Forms] 액세스 권한 [!DNL Adobe Sign] 개발자 계정에 다음과 유사한 성공 메시지가 표시됩니다.

   ![Adobe Sign Cloud 구성 성공](assets/adobe-sign-cloud-configuration-success.png)

1. 탭 **[!UICONTROL 만들기]** 를 클릭하여 [!DNL Adobe Sign] 구성.

1. 구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL 게시]**&#x200B;를 클릭하고 구성을 선택한 다음 를 클릭합니다. **[!UICONTROL 게시]**. 해당 게시 환경에 구성을 복제합니다.

1. 개발자, 스테이지 및 프로덕션 인스턴스(왼쪽)에서 위의 모든 단계를 반복하여 구성을 완료합니다 [!DNL Adobe Sign] with [!DNL AEM Forms] 사용자 환경.

이제 다음을 수행할 수 있습니다 [적응형 양식에 Adobe Sign 필드 추가 사용](working-with-adobe-sign.md). Cloud Service에 사용되는 구성 컨테이너를 사용 중인 모든 적응형 Forms에 추가해야 합니다 [!DNL Adobe Sign]. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

## (AEM 워크플로우의 경우에만) 구성 [!DNL Adobe Sign] 서명 상태를 동기화할 스케줄러 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

사용 시 [!DNL Adobe Sign] 적응형 양식에 서명하는 워크플로우 단계. 양식은 워크플로우 단계의 구성에 따라 서명자 간에 서로 전달하거나 모든 서명자에게 동시에 전송할 수 있습니다. [!DNL Adobe Sign] 활성화된 적응형 Forms은 모든 서명자가 서명 프로세스를 완료한 후에만 Experience Manager Forms 서버에 제출됩니다.

기본적으로 [!DNL Adobe Sign] 스케줄러 서비스는 24시간마다 후에 (투표) 서명자 응답을 확인합니다. 환경의 기본 간격을 변경할 수 있습니다.

기본 간격을 변경하려면 [cron 식](https://en.wikipedia.org/wiki/Cron#CRON_expression) 대상 **sign.status.exp** 속성 **Adobe Sign 구성 서비스** 구성.

예를 들어 매일 오전 00:00에 구성 서비스를 실행하려면 **sign.status.exp** 속성 **Adobe Sign 구성 서비스** 지정할 구성 `0 0 0 1/1 * ? *`. 다음 JSON 파일은 매일 오전 00:00에 구성 서비스를 실행하는 샘플을 표시합니다.

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

구성 값을 설정하려면 [AEM SDK를 사용하여 OSGi 구성 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), 및 [구성 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) Cloud Service 인스턴스에 매핑해야 합니다.

<!-- , perform the following steps:

1. Log in to [!DNL AEM Forms] Server with admin credentials and navigate to **[!UICONTROL Tools]** &gt;**[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   You can also open the following URL in a browser window:
   `https://server/system/console/configMgr`

1. Locate and open the **[!UICONTROL Adobe Sign Configuration Service]** option. Specify a [cron expression](https://en.wikipedia.org/wiki/Cron#CRON_expression) in the **Status Update Scheduler Expression** field and click **Save**. For example, to run the configuration service daily at 00:00 am, specify `0 0 0 1/1 * ? *` in the **Status Update Scheduler Expression** field.

Default interval to sync status of [!DNL Adobe Sign] is now changed. -->

## 관련 문서 {#related-articles}

* [적응형 양식에서 Adobe Sign 사용](working-with-adobe-sign.md)

* [적응형 Forms과 Adobe Sign 사용 우수 사례](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
