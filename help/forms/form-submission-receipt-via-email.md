---
title: 이메일을 통해 양식 제출 승인 보내기
description: AEM Forms을 사용하면 양식 제출 시 사용자에게 승인을 보내는 이메일 제출 액션을 구성할 수 있습니다.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# 이메일을 통해 양식 제출 승인 보내기 {#sending-a-form-submission-acknowledgement-via-email}

## 적응형 양식 데이터 제출 {#adaptive-form-data-submission}

적응형 Forms은 몇 가지 기본 기능을 제공합니다 [작업 제출](configuring-submit-actions.md) 양식 데이터를 다른 엔드포인트에 제출하기 위한 워크플로우.

예를 들어 **[!UICONTROL 이메일 보내기]** 제출 액션은 적응형 양식의 성공적인 제출 시 이메일을 전송합니다. 양식 데이터 및 PDF을 이메일에 보내도록 구성할 수도 있습니다.

이 문서에서는 적응형 양식 및 적응형 양식에서 제공하는 다양한 구성에서 이메일 작업을 활성화하는 단계에 대해 자세히 설명합니다.

>[!NOTE]
>
>다음을 사용할 수도 있습니다 **[!UICONTROL 이메일을 통해 PDF 보내기]** 완료된 양식을 PDF 첨부 파일로 이메일로 보내는 옵션. 이 작업에 사용할 수 있는 구성 옵션은 **[!UICONTROL 이메일 보내기]** 작업. 이메일 PDF 작업은 XFA 기반 적응형 Forms에 대해서만 사용할 수 있습니다

## 이메일 전송 작업 {#email-action}

이메일 보내기 작업을 사용하면 작성자가 적응형 양식을 성공적으로 제출하면 하나 이상의 수신자에게 이메일을 자동으로 보낼 수 있습니다.

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

### 적응형 양식 필드 이름을 사용하여 이메일 콘텐츠를 동적으로 만들기 {#using-adaptive-form-field-names-to-dynamically-create-email-content}

적응형 양식의 필드 이름은 사용자가 양식을 제출한 후 해당 필드의 값으로 대체되는 자리 표시자라고 합니다.

다음에서 **[!UICONTROL 이메일 보내기]** 매크로 함수에서는 매크로 함수를 수행할 때 처리되는 자리 표시자를 사용할 수 있습니다. 이메일의 헤더(예: **[!UICONTROL 종료]**, **[!UICONTROL 참조]**, **[!UICONTROL 숨은 참조]**, **[!UICONTROL 제목]**)는 사용자가 양식을 제출할 때 생성됩니다.

자리 표시자를 정의하려면 다음을 지정합니다 `${<field name>}` 을(를) 선택한 후 필드에서 **[!UICONTROL 이메일 보내기]** 를 제출 동작으로 사용하십시오.

예를 들어 양식에 **[!UICONTROL 이메일 주소]** 필드, 명명된 `email_addr`, 사용자의 이메일 ID를 캡처하는 경우 **[!UICONTROL 종료]**, **[!UICONTROL 참조]**, 또는 **[!UICONTROL 숨은 참조]** 필드.

`${email_addr}`

사용자가 양식을 제출하면 이메일이 다음에 입력한 이메일 ID로 전송됩니다 `email_addr` 양식의 필드입니다.

>[!NOTE]
>
>에서 필드 이름을 찾을 수 있습니다 **[!UICONTROL 편집]** 필드에 대한 대화 상자입니다.

변수 자리 표시자도 **[!UICONTROL 제목]** 및 **[!UICONTROL 이메일 템플릿]** 필드.

예를 들면 다음과 같습니다.

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>반복 가능한 패널의 필드는 변수 자리 표시자로 사용할 수 없습니다.

