---
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
description: 적응형 양식은 여러 제출 액션을 제공합니다. 제출 액션은 적응형 양식이 제출 후 처리되는 방식을 정의합니다. 기본 제공 제출 액션을 사용하거나 직접 만들 수 있습니다.
keywords: 적응형 양식에 대한 제출 액션을 선택하고, 적응형 양식을 sharepoint 목록에 연결하고, 적응형 양식을 sharepoint 문서 라이브러리에 연결하고, 적응형 양식을 양식 데이터 모델(FDM)에 연결하는 방법
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 47%

---

# 적응형 양식 제출 액션

| 버전 | 문서 링크 |
|---------|-----------------------------|
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html?lang=ko) |
| AEM as a Cloud Service(Foundation 구성 요소) | [여기 클릭](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (핵심 구성 요소) | [여기 클릭](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service(Edge Delivery Services) | 이 문서 |


양식 제출은 사용자 여정의 중요한 마지막 단계이며, 수집된 데이터가 처리되고 작업이 수행되는 단계입니다. 이 문서에서는 범용 편집기에서 적응형 양식의 제출 작업을 구성하고 관리하는 방법에 대한 포괄적인 안내서를 제공합니다.

### 학습 내용

이 문서를 끝까지 읽으면 다음을 수행하는 방법에 대해 이해할 수 있습니다.

- 양식에 대한 다양한 유형의 제출 작업 구성
- 외부 시스템과의 통합을 위해 REST 엔드포인트 제출 설정
- 양식 응답에 대한 이메일 제출 구성
- 특정 비즈니스 요구 사항에 맞게 사용자 정의 제출 작업 구현
- 제출 중 양식 유효성 검사 및 오류 시나리오 처리

### 타깃 대상자

이 안내서는 다음을 위해 설계되었습니다.

- 제출 논리를 구현하는 **양식 개발자**
- 양식을 백엔드 시스템에 연결하는 **시스템 통합업체**
- 양식 워크플로를 정의하는 **비즈니스 분석가**
- 양식 제출 프로세스를 설계하는 **기술 설계자**

## 범용 편집기에서 만든 Forms에 대한 제출 액션

다음 제출 액션은 [범용 편집기에서 작성된 적응형 Forms](/help/edge/docs/forms/universal-editor/create-forms.md)에서 지원됩니다.

- [이메일 보내기](/help/forms/configure-submit-action-send-email.md)
- [Power Automate 플로우 호출](/help/forms/forms-microsoft-power-automate-integration.md)
- [SharePoint에 제출](/help/forms/configure-submit-action-sharepoint.md)
- [Workfront Fusion 호출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [양식 데이터 모델(FDM)을 사용하여 제출](/help/forms/integrate-adaptive-form-with-fdm.md)
- [Azure Blob Storage에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
- [REST 끝점에 제출](/help/forms/configure-submit-action-restpoint.md)
- [OneDrive에 제출](/help/forms/configure-submit-action-onedrive.md)
- [AEM Workflow 호출](/help/forms/configure-submit-action-workflow.md)
- [Marketo Engage에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)
- [Adobe Experience Platform(AEP)에 제출](/help/forms/aem-forms-aep-connector.md)
- [스프레드시트에 제출](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

**양식 속성 편집** 확장의 **제출** 탭을 사용하여 유니버설 편집기에서 만든 양식에 대해 제출 액션을 구성할 수 있습니다.

**범용 편집기에서 작성된 Forms에 대한 제출 액션을 구성하는 방법**
**양식 속성 편집** 확장의 **제출** 탭을 사용하여 유니버설 편집기에서 만든 양식에 대해 제출 액션을 구성할 수 있습니다.

![양식 속성 아이콘](/help/forms/assets/ue-form-properties-icon.png)

![유니버설 편집기 양식 속성](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
> - 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 보이지 않는 경우 Extension Manager에서 **양식 속성 편집** 확장을 사용하도록 설정하십시오.
> - 범용 편집기에서 확장을 활성화하거나 비활성화하는 방법에 대해 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.



