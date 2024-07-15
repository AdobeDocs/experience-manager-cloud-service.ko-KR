---
Title: How to integrate AEM workflow with an Adaptive Form?
Description: Explore the process of automated workflow initiation with AEM Forms Submit Action.
keywords: AEM 워크플로, 적응형 양식과 AEM 워크플로 통합, AEM 워크플로 호출 제출 액션
feature: Adaptive Forms, Core Components
exl-id: b7788e3d-acd8-4867-b232-f9767cf6b2f5
title: "적응형 양식에 대한 제출 액션을 구성하는 방법"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 56%

---

# AEM 적응형 양식과 AEM 워크플로 통합: 비즈니스 프로세스 간소화

**[!UICONTROL AEM 워크플로 호출]** 제출 액션은 적응형 양식을 AEM 워크플로와 연결합니다. 양식이 제출되면 연결된 워크플로가 작성자 인스턴스에서 자동으로 시작됩니다. 데이터 파일, 첨부 파일 및 기록 문서를 워크플로우의 페이로드 위치 또는 변수에 저장할 수 있습니다. 워크플로가 외부 데이터 스토리지로 표시되고 외부 데이터 스토리지로 구성되면 변수 옵션만 제공됩니다. 워크플로 모델에 제공되는 변수 목록에서 선택할 수 있습니다. 워크플로 생성 시점이 아닌 이후 단계에서 워크플로가 외부 데이터 스토리지로 표시되면 필수 변수 구성이 마련되었는지 확인합니다.

>[!NOTE]
>
>  사용자가 워크플로를 시작할 때 실행되는 일련의 단계를 정의하기 위해 [워크플로 모델을 만드는](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=ko#extending-aem) 방법을 알아봅니다. 워크플로가 일시적인지 또는 여러 리소스를 사용하는지 여부와 같은 모델 속성을 정의할 수도 있습니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

## 장점

AEM 워크플로우와 적응형 Forms을 통합하면 다음과 같은 몇 가지 이점이 있습니다.

* AEM Workflow 통합을 통해 양식 제출을 수반하는 복잡한 비즈니스 프로세스를 자동화할 수 있습니다.
* AEM Workflow는 조건부 논리를 지원하므로 양식 데이터 또는 외부 요인에 따라 동적 결정을 할 수 있습니다.
* AEM Workflow는 사전 정의된 규칙 및 조건에 따라 작업을 라우팅하므로, 작업이 올바른 개인 또는 그룹에 할당되도록 합니다.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## 적응형 Forms과 AEM Workflow 통합 {#steps-to-integrate-workflow-with-af}

적응형 양식에 대해 [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=ko#extending-aem)을(를) 사용하여 자동화된 프로세스를 설정하려면 다음 단계를 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. **[!UICONTROL 작업 제출]** 드롭다운 목록에서 **[!UICONTROL AEM 워크플로 호출]** 을 선택합니다.
   ![전자 메일 보내기의 작업 구성](/help/forms/assets/configure-invoke-aem-workflow.png)

1. **[!UICONTROL 워크플로 모델]** 드롭다운 목록에서 워크플로 모델을 선택하십시오.
1. **[!UICONTROL 데이터 파일 저장 사용]** 드롭다운 목록에서 옵션을 선택하십시오.

   **데이터 파일**: 적응형 양식에 제출된 데이터가 포함됩니다. **[!UICONTROL 데이터 파일 경로]** 옵션을 사용하여 페이로드를 기준으로 파일 이름과 파일 경로를 지정할 수 있습니다. 예를 들어 `/addresschange/data.xml` 경로는 `addresschange`라는 폴더를 만들고 페이로드를 기준으로 배치합니다. 또한 `data.xml`만 지정하여 폴더 계층 구조를 만들지 않고도 제출된 데이터만 전송할 수 있습니다. 워크플로가 외부 데이터 스토리지로 표시되면 변수 옵션을 사용하고 워크플로 모델에 제공되는 변수 목록에서 변수를 선택합니다.

1. **[!UICONTROL 다음을 사용하여 첨부 파일 저장]** 드롭다운 목록에서 옵션을 선택하십시오.

   **첨부 파일**: **[!UICONTROL 첨부 파일 경로]** 옵션을 사용하여 폴더 이름을 지정하면 적응형 양식에 업로드된 첨부 파일을 저장할 수 있습니다. 페이로드를 기준으로 폴더를 생성합니다. 워크플로가 외부 데이터 스토리지로 표시되면 변수 옵션을 사용하고 워크플로 모델에 제공되는 변수 목록에서 변수를 선택합니다.

1. **[!UICONTROL 사용 기록 문서]** 드롭다운 목록에서 옵션을 선택하십시오.

   **기록 문서**: 적응형 양식에 생성된 기록 문서가 포함됩니다. **[!UICONTROL 기록 문서 경로]** 옵션을 사용하여 페이로드를 기준으로 기록 문서 파일 이름과 파일 경로를 지정할 수 있습니다. 예를 들어 `/addresschange/DoR.pdf` 경로는 `addresschange`라는 폴더를 만들고 페이로드를 기준으로 `DoR.pdf`를 배치합니다. 또한 `DoR.pdf`만 지정하여 폴더 계층 구조를 만들지 않고도 기록 문서만 저장할 수 있습니다. 워크플로가 외부 데이터 스토리지로 표시되면 변수 옵션을 사용하고 워크플로 모델에 제공되는 변수 목록에서 변수를 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!NOTE]
>
> [Forms 중심의 AEM 워크플로 - 비즈니스 프로세스 자동화를 위한 단계 참조](/help/forms/aem-forms-workflow-step-reference.md)에 대해 자세히 알아보십시오.

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## 관련 문서

{{af-submit-action}}
