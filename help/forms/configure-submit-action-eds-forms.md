---
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
description: 적응형 양식은 여러 제출 액션을 제공합니다. 제출 액션은 적응형 양식이 제출 후 처리되는 방식을 정의합니다. 기본 제공 제출 액션을 사용하거나 직접 만들 수 있습니다.
keywords: 적응형 양식에 대한 제출 액션을 선택하고, 적응형 양식을 sharepoint 목록에 연결하고, 적응형 양식을 sharepoint 문서 라이브러리에 연결하고, 적응형 양식을 양식 데이터 모델(FDM)에 연결하는 방법
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
exl-id: 3f8950c3-9022-4e9f-b3ed-723245201e45
source-git-commit: 2c3e8f6f8dab1004a6fbd9be8f5604b1570a1808
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 19%

---

# Edge Delivery Services Forms에 대한 작업 제출

| 버전 | 문서 링크 |
|---------|-----------------------------|
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service(Foundation 구성 요소) | [여기 클릭](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (핵심 구성 요소) | [여기 클릭](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service(Edge Delivery Services) | 이 문서 |

제출 액션은 사용자가 양식을 제출할 때 데이터 저장, 워크플로우 트리거 또는 서드파티 시스템과의 통합과 같은 작업을 정의합니다. 구성할 수 있는 제출 액션 유형은 Edge Delivery Services Forms을 만드는 데 사용된 작성 방법에 따라 다릅니다.

[범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 사용하거나 [문서 기반 Forms](/help/edge/docs/forms/overview.md) 작성을 사용하여 Edge Delivery Services Forms을 만들고 그에 따라 다른 제출 동작으로 양식을 구성할 수 있습니다.

## 범용 편집기에서 만든 Forms에 대한 제출 액션

다음 제출 액션은 [범용 편집기에서 작성된 적응형 Forms](/help/edge/docs/forms/universal-editor/create-forms.md)에서 지원됩니다.

* [이메일 보내기](/help/forms/configure-submit-action-send-email.md)
* [Power Automate 플로우 호출](/help/forms/forms-microsoft-power-automate-integration.md)
* [SharePoint에 제출](/help/forms/configure-submit-action-sharepoint.md)
* [Workfront Fusion 호출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [양식 데이터 모델(FDM)을 사용하여 제출](/help/forms/integrate-adaptive-form-with-fdm.md)
* [Azure Blob Storage에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
* [REST 끝점에 제출](/help/forms/configure-submit-action-restpoint.md)
* [OneDrive에 제출](/help/forms/configure-submit-action-onedrive.md)
* [AEM Workflow 호출](/help/forms/configure-submit-action-workflow.md)
* [Marketo Engage에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [Adobe Experience Platform(AEP)에 제출](/help/forms/aem-forms-aep-connector.md)
* [스프레드시트에 제출](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

**양식 속성 편집** 확장의 **제출** 탭을 사용하여 유니버설 편집기에서 만든 양식에 대해 제출 액션을 구성할 수 있습니다.

<!--**How to Configure Submit Action for Forms authored in Universal Editor?**
You can configure the submit action for forms created in the Universal Editor using the **Submission** tab of the **Edit Form Properties** extension.

![Form properties icon](/help/forms/assets/ue-form-properties-icon.png)

![Universal Editor Form Properties](/help/forms/assets/ue-form-properties.png)-->

>[!NOTE]
>
> * 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 보이지 않는 경우 Extension Manager에서 **양식 속성 편집** 확장을 사용하도록 설정하십시오.
> * 범용 편집기에서 확장을 활성화하거나 비활성화하는 방법에 대해 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.

## 문서 기반 Forms에 대한 작업 제출

문서 기반 Forms은 스프레드시트에만 제출할 수 있습니다. 스프레드시트를 설정하여 제출된 데이터를 받는 방법에 대해 알아보려면 [Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수락](/help/edge/docs/forms/submit-forms.md) 문서에 있는 지침을 참조하십시오.

## 추가 참조 {#see-also}

{{af-submit-action}}
