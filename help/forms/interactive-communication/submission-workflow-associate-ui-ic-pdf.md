---
title: UI 연결에 대한 제출 워크플로우 — IC PDF 출력 생성
description: 제출 및 워크플로가 연결 UI에 대해 작동하는 방식을 이해하고 대화형 통신(IC) JSON에서 PDF을 생성하는 예제 워크플로를 따릅니다.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: a1b2c3d4-e5f6-4a7b-8c9d-0e1f2a3b4c5d
source-git-commit: a41459520feb03594212b91e68cfd8e2b1e610c4
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 3%

---

# 연계 UI에 대한 제출 워크플로우

>[!NOTE]
>
> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 이메일 주소를 통해 `aem-forms-ea@adobe.com`으로 이메일을 보내시기 바랍니다.

이 문서에서는 연결 UI에 대한 워크플로를 활성화할 때 제출 및 워크플로가 작동하는 방식에 대해 설명합니다. 그런 다음 제출 워크플로우를 구성하는 방법을 안내합니다. 이 연습에서는 대화형 통신(IC) 페이로드에서 PDF을 생성하는 것을 예로 사용하므로 다른 워크플로우 유형에 대해 단계를 조정할 수 있습니다.

<!--## Submission and workflow behavior {#submission-and-workflow-behavior}

When you enable **Configure Workflow for Update** for an Associate UI, submissions from the Associate UI can trigger an AEM workflow. The following explains where workflows run, who uses which environment, and how to plan for data and access.

### Where workflows run

AEM workflows always run on the **Author** instance. It does not matter whether the person submitting is an author or an associate—the workflow runs on Author. Plan your user groups and where you store workflow data with this in mind.

### Where associates use the Associate UI

Customer-facing associates use the Associate UI on the **Publish** instance only. You publish the Interactive Communication and expose the Associate UI through your Publish environment (for example, via your application or dispatcher). Associates do not use the Author instance. For step-by-step integration and how to invoke the Associate UI on the Publish instance, see [Integrate Associate UI in Your Application](/help/forms/interactive-communication/invoke-associate-ui.md).

### When an author submits from the Author instance

Authors can open the Associate UI on the Author instance—for example, to test the Interactive Communication or to submit on behalf of a customer. When they submit, the request is handled on Author and the workflow runs there. For this to work, the author must be in both **forms-associates** (to access the Associate UI) and **workflow-users** (to run the workflow).

### When an associate submits from the Publish instance

Associates open the Associate UI on the Publish instance, using the integration you set up. When they submit, the submission is sent to the Author instance and the workflow runs on Author. Associates sign in on Publish (for example, via [Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)) and do not need access to Author. To set up how associates open the Associate UI on Publish, see [Integrate Associate UI in Your Application](/help/forms/interactive-communication/invoke-associate-ui.md).-->

## 제출 워크플로우 구성

다음 단계는 사용자가 연결 UI에서 제출할 때 실행되는 워크플로우를 만드는 방법을 보여줍니다. 여기서는 **PDF에 IC 렌더링**&#x200B;을 예로 들며, 기본 **IC 렌더링 PDF 출력** 단계를 사용합니다. 사용자가 연결 UI에서 제출하면 페이로드가 워크플로로 전송됩니다. 이 단계에서는 페이로드의 **communicationDom**(IC-JSON)을 사용하여 PDF을 생성합니다.

### 페이로드 구조

워크플로우는 JSON 페이로드를 받습니다. **communicationDom** 필드에는 PDF 생성에 사용되는 IC-JSON이 있습니다. **IC 렌더링 PDF 출력** 단계에서는 템플릿 입력으로 사용합니다.

| 필드 | 설명 |
|-------|-------------|
| communicationDom | PDF 생성을 위한 IC-JSON |
| auditMeta | 감사 정보 |
| submitData | 제출된 양식 데이터(JSON) |
| 데이터 미리 채우기 | 데이터 미리 채우기(JSON) |
| referer, cookies, queryString, clientIP, userAgent, formSubmitter | 메타데이터 요청 |

### 워크플로우 모델 만들기

1. **기본:** 워크플로 모델을 만듭니다(예: 워크플로를 **pdfrenderworkflow**(으)로 추가).

   ![워크플로 모델 기본 탭](/help/forms/assets/associate-ui-add-workflow.png)

1. **변수:** 페이로드와 일치하는 변수를 추가하고 단계: **communicationDom**(JSON), **감사 메타데이터**(JSON), **출력 문서**(문서).

   ![워크플로 변수](/help/forms/assets/associate-ui-add-variables.png)

1. **단계:** **IC 렌더링 PDF 출력** 단계를 추가합니다.
   ![워크플로 단계 추가](/help/forms/assets/associate-ui-add-step.png)

1. **입력** 탭에서 **템플릿 선택(JsonObject)**&#x200B;을(를) **변수** → **communicationDom**(으)로 설정합니다. 단계와 모델을 저장합니다.

   ![IC 렌더링 PDF 출력 — 입력 탭](/help/forms/assets/associate-ui-input-variable.png)

1. **출력** 탭에서 **템플릿 선택(JsonObject)**&#x200B;을(를) **변수** → **communicationDom**(으)로 설정합니다. 단계와 모델을 저장합니다.

   ![워크플로 변수 및 캔버스](/help/forms/assets/assocaite-ui-output-variable.png)

### UI를 연결할 워크플로를 연결합니다.

[Associate UI 사용 및 구성](/help/forms/interactive-communication/enable-configure-associate-ui.md)에서 Associate View를 사용하도록 설정하고 **Workflow**&#x200B;에서 **Update에 대한 워크플로 구성**&#x200B;을(를) On으로 설정하고 이 워크플로 모델을 선택하십시오. 제출이 이 이 워크플로를 트리거하도록 IC와 [연결 UI를 통합](/help/forms/interactive-communication/invoke-associate-ui.md)합니다.

![대화형 통신 설정 - 연결 UI에 대한 워크플로 구성](/help/forms/assets/associate-ui-configure-workflow.png)

**워크플로 데이터 저장소 외부화**&#x200B;을 사용하도록 설정하면 워크플로 데이터가 외부 저장소(예: Azure)에 저장되도록 외부화를 구성합니다. [워크플로 데이터 외부화](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/create-aem-workflow/externalize-workflow.html)를 참조하십시오.

## 추가 참조

- [대화형 통신 편집기에서 UI 연결](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [대화형 커뮤니케이션용 연결 UI 활성화 및 구성](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [애플리케이션에 UI 연결 통합](/help/forms/interactive-communication/invoke-associate-ui.md)
- [워크플로 데이터 외부화](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/create-aem-workflow/externalize-workflow.html)
