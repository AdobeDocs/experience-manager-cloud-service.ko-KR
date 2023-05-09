---
title: Sites 페이지에 포함되거나 생성된 적응형 Forms에 대한 검토 만들기 및 관리
seo-title: Review is a mechanism that allows reviewer to perform different tasks for adaptive forms using Assign Task step
description: 검토는 검토자가 작업 할당 단계를 사용하여 적응형 양식에 대해 다른 작업을 수행할 수 있는 메커니즘입니다
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: daeb407e27b9f1d390fe40151ca16ec0196712e6
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 4%

---


# 사이트 페이지에서 Forms에 대한 검토 단계 {#review-step-forms-aem-sites-page}

사용 [단계 할당](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html#assign-task-step) AEM 워크플로우에서 검토자는 제출된 양식을 검토하고 작업을 수행합니다. 작업 할당 단계를 사용하여 제출된 양식을 검토하려면 다음 단계를 수행합니다.

1. [AEM 워크플로우 만들기](#create-an-aem-workflow)
1. [적응형 양식 컨테이너의 제출 작업 구성](#configure-submit-action)
1. [검토 후 적응형 양식 제출](#submit-af-after-review)

## AEM 워크플로우 만들기 {#create-an-aem-workflow}

1. 편집 모드에서 작성자 인스턴스를 엽니다.
1. 이동 **[!UICONTROL 도구]** >  **[!UICONTROL 워크플로우]** >  **[!UICONTROL 모델]** > **[!UICONTROL 만들기]** > **[!UICONTROL 모델 만들기]**
1. 워크플로우의 제목 을(를) 지정하고 **[작업 할당]** 단계
1. 탭 ![settings_icon](assets/settings_icon.png) 를 클릭합니다. 다음 **[!UICONTROL 작업 할당]** 대화 상자가 열립니다.
1. 열기 [!UICONTROL 양식 및 문서] 탭 및 열기 [!UICONTROL 미리 채워짐] 드롭다운 및 지정:

   * 다음을 사용하여 입력 데이터 파일 선택
   * 다음을 사용하여 입력 첨부 파일 선택

   ![검토 단계](/help/forms/assets/assigntask-review1.gif)

1. 열기 **[!UICONTROL 할당자]** 탭 및 열기 [!UICONTROL 미리 채워짐] 드롭다운 및 **[!UICONTROL 옵션 할당]**:

   ![검토 단계](/help/forms/assets/review-assignstep.png)

1. **[!UICONTROL 완료]**&#x200B;를 클릭하여 변경 내용을 저장합니다.

## 제출 작업 구성 {#configure-submit-action}

이제 사이트의 페이지에서 적응형 양식 컨테이너 구성 요소의 제출 작업을 구성합니다.

1. 사이트의 페이지로 이동합니다.
1. 탭 ![settings_icon](assets/settings_icon.png) 적응형 양식 컨테이너에 대한 설명입니다. 다음 **[!UICONTROL 적응형 양식 컨테이너]** 대화 상자가 열립니다.
1. 를 엽니다. **[!UICONTROL 제출]** 탭 및 **[!UICONTROL 작업 제출]** to [AEM 워크플로우 호출](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#invoke-an-aem-workflow)

1. 클릭 [완료] 설정을 저장하려면 을 클릭합니다.

![submissiontab-reviewstep](/help/forms/assets/submissiontab-reviewstep.gif)

## 검토 후 적응형 양식 제출 {#submit-af-after-review}

제출된 적응형 양식을 검토하고 확인하려면:

1. 이동 [!UICONTROL 도구] >  [!UICONTROL 워크플로우] >  [!UICONTROL 인스턴스]
1. 받은 편지함에서 인스턴스가 만들어지는 것을 볼 수 있습니다.
1. 인스턴스를 선택하고 를 클릭합니다 [!UICONTROL 열기].
1. 이제 제출된 양식을 볼 수 있습니다.

검토자는 다음과 같이 다양한 작업을 수행합니다.

* **제출**: 검토자가 양식을 완료하고 추가 처리를 위해 제출합니다.
* **저장**: 검토자는 양식을 제출하지 않고 현재 상태로 저장합니다.
* **재설정**: 검토자는 양식 변경 내용을 지우고 원래 상태로 복원합니다.
* **위임**: 검토자는 추가 작업이나 검토를 위해 양식의 소유권을 다른 사람에게 전송합니다.
