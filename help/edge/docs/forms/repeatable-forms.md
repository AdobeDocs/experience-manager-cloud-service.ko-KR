---
title: 양식에 반복 가능한 섹션 추가
description: EDS 양식에 반복 가능한 섹션 추가
feature: Edge Delivery Services
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 100%

---

# 양식에 반복 가능한 섹션 추가

적응형 양식 블록을 사용하여 반복 가능한 양식의 섹션 또는 구성 요소를 추가하거나 만들 수 있습니다. 이를 통해 사용자는 경력이나 학력 등과 같은 정보를 수집하기 쉽도록 동일한 데이터 유형에 대한 정보를 여러 번 입력할 수 있습니다.

예를 들어 개인 경력에 대한 정보를 수집하는 데 사용되는 양식을 고려해 보십시오. 이전 작업의 세부 정보를 캡처하는 반복 가능한 섹션이 있을 수 있습니다. 반복 가능한 섹션은 일반적으로 회사 이름, 직책, 고용일, 직무 등과 같은 필드를 포함합니다. 사용자는 반복 가능한 섹션의 여러 인스턴스를 추가하여 각 직무에 대한 정보를 입력할 수 있습니다.

이 문서가 작성되면 다음 방법을 파악할 수 있습니다.

* [양식에서 반복 가능한 섹션을 만드는 방법](#add-repeatable-sections-to-a-form)
* [양식에서 최소 또는 최대 반복 횟수를 설정하는 방법](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## 반복 가능한 섹션을 만드는 방법

양식에서 반복 가능한 섹션을 만들면 사용자는 동일한 데이터 세트의 여러 인스턴스를 입력하여 반복적인 정보를 효율적으로 수집할 수 있습니다. 양식에서 반복 가능한 섹션을 만들려면

1. Microsoft SharePoint 또는 Google Workspace의 Edge Delivery 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.

1. `type` 속성이 `fieldset`로 설정된 상태에서 양식 필드 추가
1. 필드 `Name`을 지정합니다. 이름 속성은 반복 가능한 섹션을 만드는 데 사용됩니다.
1. `repeatable`를 `true`로 설정하여 반복 기능을 활성화합니다.
1. 필드에 설명 `label`을 지정합니다. 반복 가능한 섹션의 제목으로 사용됩니다.

   입사지원서 양식 내 근무 기록 섹션에 대한 일러스트레이션은 아래 이미지를 참조하십시오.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. 섹션에 포함할 각 필드에 대해 해당 `Fieldset` 속성을 3단계에서 선택한 동일한 이름으로 설정합니다.

   예를 들어 `employment history` 섹션에 포함될 모든 관련 필드의 Fieldset 속성에 `experience`를 지정합니다.

   ![반복 가능한 섹션 필드 및 해당 속성의 예](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다. 반복 가능한 섹션이 양식에 추가됩니다.

   반복 가능한 섹션 아래에서 사용자는 직관적인 **추가** 버튼을 찾아 여러 섹션을 간편하게 추가할 수 있습니다.

   ![반복 가능한 섹션, 여러 섹션을 추가하는 추가 버튼 ](/help/edge/assets/repeatable-section-example.png)


## 최소 및 최대 반복 횟수 설정

양식 디자인에서 반복 가능한 섹션의 최소 및 최대 반복 횟수를 설정하는 것이 좋습니다. 이렇게 하면 사용자를 효과적으로 안내하면서 제어 기능을 설정하고 일관성을 유지할 수 있습니다. 최소 또는 최대 반복 횟수를 설정하려면

1. Microsoft SharePoint 또는 Google Workspace의 Edge Delivery 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.

1. `type`, `fieldset` 및 `repeatable` 속성의 필드가 `true`로 설정된 경우

   * `min` 속성을 설정하여 섹션을 반복할 수 있는 최소 횟수를 지정합니다.

   * `max` 속성을 설정하여 섹션을 반복할 수 있는 최대 횟수를 지정합니다.

   ![최소 및 최대 속성을 설정하여 섹션을 반복할 수 있는 횟수를 지정합니다.](/help/edge/assets/repeatable-section-set-min-max.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

   반복 가능한 섹션이 추가되면 사용자는 직관적인 **삭제** 아이콘을 찾아 반복 가능한 섹션을 더 쉽게 제거할 수 있습니다. 추가되면 이 세션은 `min` 속성으로 지정된 인스턴스보다 더 적은 수의 인스턴스로 줄어들 수 없습니다. 이렇게 하면 양식을 완성하는 데 필요한 최소 요구 사항을 준수할 수 있습니다.

<!--

For example, consider a form used to collect information from users applying for a loan. . You may have a repeatable section for capturing details of each co-applicant. The repeatable section would typically contain fields such as co-co-applicant

The form allows users to provide personal information, including details of the co-applicants. Users can enter details for co-applicants, with this section being repeatable.

![Repeatable sections in forms](/help/forms/assets/eds-repeatable.png)

## Prerequisites

The [Adaptive Forms Block is enabled](/help/edge/docs/forms/create-forms.md) for your Edge Delivery Services project. 

## Add a repeatable section to a form 

Let's take an example of a loan application form. The form enables users to submit personal information. You can include co-applicant details using repeatable sections, with the option to add a minimum and maximum of three co-applicant sections.

"_You can use a Microsoft Excel file on your SharePoint Site or Google Sheet file on Google Drive to develop a form. Examples in this document are based on a [Microsoft Excel file on your SharePoint Site](https://www.aem.live/docs/setup-customer-SharePoint)._" 


To add repeatable sections in Edge Delivery:

1. [Author a form using Microsoft Excel](#author-form)
2. [Preview and publish the form](#preview-form)

### Author a form using Microsoft Excel {#author-form}

1. Go to your Edge Deliver project folder on Microsoft SharePoint or Google Workspace and open your spreadsheet. For example, open an a spreadsheet named `loan-application.xlsx`.

1. Add a new columns labeled `Repeatable` to the sheet contaning your form fields. By default, the `shared-default` sheet contains the form fields.  

1. Add new columns labeled as `Repeatable`, `Min`, and `Max` in your Microsoft Excel file.
1. Specify the value for the `Repeatable` column as `True` for the fieldset that you want to make repeatable.
1. Specify the values for the `Min` and `Max` columns. The `Min` value represents the minimum number of occurrences for which the panel repeats, while the `Max` value represents the maximum number of occurrences for which the panel repeats.
1. Save your Microsoft Excel file.
     
>[!NOTE]
>
> Here is the [Loan application](/help/forms/assets/loan-application.xlsx) excel sheet for your reference. 

### Preview/Publish the form using your Edge Delivery Service

1. Open or create new document file in a Microsft SharePoint Site to embed the Excel sheet  in it using a `Form Block`. For example, open the `index` file and add a `Form Block`.
2. Open the command prompt, navigate to your AEM Edge Delivery project directory on your local machine, and execute the command as `aem up`.

The form is accessible at `https://localhost:3000`, where clicking the `Add` button adds new repeatable section for entering co-applicant details. You can also delete the the repeatable section by clicking the `Delete` button. 

>[!NOTE]
>
> If you encounter a "Page Not Found" error while accessing your form at localhost, add the directory name of the Microsoft SharePoint Site in front of the URL where your form is located. For example, `http://localhost:3000/<dir-name>/`

-->


## 추가 참조

{{see-more-forms-eds}}
