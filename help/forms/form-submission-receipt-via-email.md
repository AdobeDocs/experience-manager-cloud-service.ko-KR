---
title: 이메일을 통해 양식 제출 확인 보내기
seo-title: Sending a form submission acknowledgement via email
description: AEM Forms에서는 양식 제출 시 사용자에게 승인을 보내는 이메일 전송 작업을 구성할 수 있습니다.
seo-description: AEM Forms allows you to configure the email Submit Action that sends an acknowledgement to a user on submitting the form.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 574de3d5-69ba-4e2f-a8ab-c59f357e4386
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# 이메일을 통해 양식 제출 확인 보내기 {#sending-a-form-submission-acknowledgement-via-email}

## 적응형 양식 데이터 제출 {#adaptive-form-data-submission}

적응형 Forms은 몇 가지 기본 제공 [작업 제출](configuring-submit-actions.md) 다른 종단점에 양식 데이터를 제출하는 워크플로우입니다.

예: **[!UICONTROL 이메일 보내기]** 제출 작업은 적응형 양식을 성공적으로 제출할 때 이메일을 전송합니다. 양식 데이터와 이메일의 PDF을 보내도록 구성할 수도 있습니다.

이 문서에서는 적응형 양식에 이메일 작업을 활성화하는 단계 및 제공하는 다양한 구성에 대해 자세히 설명합니다.

>[!NOTE]
>
>를 사용할 수도 있습니다 **[!UICONTROL 이메일을 통해 PDF 보내기]** 완료된 양식을 PDF 첨부 파일로 이메일로 보내는 옵션. 이 작업에 사용할 수 있는 구성 옵션은 **[!UICONTROL 이메일 보내기]** 작업. 이메일 PDF 작업은 XFA 기반 적응형 Forms에만 사용할 수 있습니다

## 전자 메일 보내기 작업 {#email-action}

전자 메일 보내기 작업을 사용하면 작성자는 적응형 양식을 성공적으로 제출할 때 하나 이상의 수신자에게 전자 메일을 자동으로 보낼 수 있습니다.

<!-- >>[!NOTE]
>
>To use the Send email action, you need to configure the AEM mail service as described in [Configuring the mail service](/help/sites-administering/notification.md#configuring-the-mail-service).

### Enabling Send email action on an Adaptive Form {#enabling-email-action-on-an-adaptive-form}

1. Open an Adaptive Form in **[!UICONTROL edit]** mode.

1. In the **[!UICONTROL Content]** tab, tap **[!UICONTROL Form Container]** and tap ![configure](assets/configure-icon.svg) to view the Adaptive Form properties.  

1. In the **[!UICONTROL Submission]** section, select **[!UICONTROL Send email]** from the **[!UICONTROL Submit Action]** drop-down list.  

   ![Submit Actions](assets/submission-actions.png)

1. Specify valid email IDs in the **[!UICONTROL To]**, **[!UICONTROL CC]**, and **[!UICONTROL BCC]** fields.

   Specify the subject and the body of the email in the **[!UICONTROL Subject]** and **[!UICONTROL Email Template]** fields, respectively.

   You can also specify variable placeholders in the fields, in which case, the values of the fields are processed when the form is successfully submitted by an end user. For more information, see [Using Adaptive Form field names to dynamically create email content](form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Select **[!UICONTROL Include attachments]** if the form includes file attachments and you want to attach these files in the email.

   >[!NOTE]
   >
   >If you choose the **[!UICONTROL Send PDF via Email]** option, you must select the Include attachments option.

1. Click ![save](assets/save_icon.svg) to save the changes. -->

### 적응형 양식 필드 이름을 사용하여 전자 메일 콘텐츠를 동적으로 만들기 {#using-adaptive-form-field-names-to-dynamically-create-email-content}

적응형 양식의 필드 이름은 사용자가 양식을 제출한 후 해당 필드의 값으로 대체되는 자리 표시자라고 합니다.

에서 **[!UICONTROL 이메일 보내기]** 작업을 수행하면 작업이 수행될 때 처리되는 자리 표시자를 사용할 수 있습니다. 이것은 이메일의 헤더(예: **[!UICONTROL 종료]**, **[!UICONTROL CC]**, **[!UICONTROL 숨은 참조]**, **[!UICONTROL 제목]**)은 사용자가 양식을 제출할 때 생성됩니다.

자리 표시자를 정의하려면 `${<field name>}` 선택 후 필드에서 **[!UICONTROL 이메일 보내기]** 을 제출 작업으로 사용할 수 있습니다.

예를 들어 양식에 가 포함되어 있으면 **[!UICONTROL 이메일 주소]** 필드, 이름이 지정됨 `email_addr`의 경우 사용자의 이메일 ID를 캡처하기 위해에서 다음을 지정할 수 있습니다. **[!UICONTROL 종료]**, **[!UICONTROL CC]**, 또는 **[!UICONTROL 숨은 참조]** 필드.

`${email_addr}`

사용자가 양식을 제출하면 이메일이 `email_addr` 필드의 값을 지정합니다.

>[!NOTE]
>
>에서 필드 이름을 찾을 수 있습니다 **[!UICONTROL 편집]** 대화 상자를 엽니다.

변수 자리 표시자는 **[!UICONTROL 제목]** 및 **[!UICONTROL 이메일 템플릿]** 필드.

예:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>반복 가능한 패널의 필드는 변수 자리 표시자로 사용할 수 없습니다.

