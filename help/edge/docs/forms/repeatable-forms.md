---
title: 양식에 반복 가능한 섹션 추가
description: EDS 양식에 반복 가능한 섹션 추가
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 8%

---

# 양식에 반복 가능한 섹션 추가

적응형 양식 블록은 양식의 섹션 또는 구성 요소를 반복 가능하도록 추가하거나 만들 수 있는 기능을 제공합니다. 이를 통해 같은 유형의 데이터에 여러 번 정보를 입력할 수 있어 근무경력이나 학력 등 정보수집이 용이하다.

예를 들어 개인의 작업 경험에 대한 정보를 수집하는 데 사용되는 양식을 생각해 보십시오. 각 이전 작업의 세부 정보를 캡처하는 반복 가능한 섹션이 있을 수 있습니다. 반복 가능 섹션에는 일반적으로 회사 이름, 직책, 고용 날짜 및 직무 책임과 같은 필드가 포함됩니다. 사용자는 반복 가능 섹션의 여러 인스턴스를 추가하여 보유하고 있는 각 작업에 대한 정보를 입력할 수 있습니다.



이 문서의 끝 부분에서는 다음 방법을 배웁니다.

* [양식에 반복 가능한 섹션 만들기](#add-repeatable-sections-to-a-form)
* [양식의 최소 또는 최대 반복 횟수 설정](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## 반복 가능한 섹션 만들기

양식에서 반복 가능한 섹션을 만들면 사용자가 동일한 데이터 세트의 여러 인스턴스를 입력할 수 있으므로 반복 정보를 효율적으로 수집할 수 있습니다. 양식에 반복 가능한 섹션을 만들려면 다음 작업을 수행하십시오.

1. Microsoft SharePoint 또는 Google Workspace에서 Edge Deliver 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.

1. 을(를) 사용하여 양식 필드 추가 `type` 속성이 로 설정됨 `fieldset`
1. 지정 `Name` 필드의 을 참조하십시오. 이름 속성은 반복 가능한 섹션을 만드는 데 사용됩니다.
1. 설정을 통한 반복 기능 활성화 `repeatable` 끝 `true`.
1. 설명 지정 `label` 필드용입니다. 반복 가능 섹션의 머리글 역할을 합니다.

   Job 지원 양식 내의 고용 내역 섹션에 대한 설명은 아래 이미지를 참조하십시오.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. 섹션에 포함할 각 필드에 대해 다음을 설정합니다. `Fieldset` 3단계에서 선택한 것과 동일한 이름의 속성입니다.

   예를 들어 을 지정합니다. `experience` 에 포함할 모든 관련 필드의 필드 집합 속성에서 `employment history` 섹션.

   ![반복 가능한 섹션 필드 및 해당 속성의 예](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 를 클릭하여 시트를 미리 보고 게시합니다. 반복 가능 섹션이 양식에 추가됩니다.

   반복 가능 섹션 아래에서 사용자는 직관적인 방법을 찾을 수 있습니다 **추가** 단추, 여러 섹션을 쉽게 추가할 수 있습니다.

   ![반복 가능한 섹션, 추가 단추, 여러 섹션 추가 ](/help/edge/assets/repeatable-section-example.png)


## 최소 및 최대 반복 설정

형식 설계에서는 반복 가능한 섹션의 최소 및 최대 반복을 설정하는 것이 좋습니다. 이를 통해 사용자를 효과적으로 안내하면서 제어 및 일관성을 확립할 수 있습니다. 최소 또는 최대 반복 횟수를 설정하려면

1. Microsoft SharePoint 또는 Google Workspace에서 Edge Deliver 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.

1. 의 필드용 `type` `fieldset` 및 `repeatable` 속성이 로 설정됨 `true`:

   * 설정 `min` 속성을 사용하여 구역을 반복할 수 있는 최소 횟수를 지정합니다.

   * 설정 `max` 속성을 사용하여 섹션을 반복할 수 있는 최대 횟수를 지정합니다.

   ![최소 및 최대 속성을 설정하여 섹션을 반복할 수 있는 횟수를 지정합니다](/help/edge/assets/repeatable-section-set-min-max.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

   반복 가능한 섹션을 추가하면 사용자는 직관적인 방법을 찾게 됩니다 **삭제** 아이콘을 클릭하면 반복 가능한 섹션을 더 쉽게 제거할 수 있습니다. 추가한 후에는 이러한 섹션을 `min` 속성. 이렇게 하면 양식 완료에 대해 설정된 최소 요구 사항을 준수할 수 있습니다.

<!--

For example, consider a form used to collect information from users applying for a loan. . You may have a repeatable section for capturing details of each co-applicant. The repeatable section would typically contain fields such as co-co-applicant

The form allows users to provide personal information, including details of the co-applicants. Users can enter details for co-applicants, with this section being repeatable.

![Repeatable sections in forms](/help/forms/assets/eds-repeatable.png)

## Prerequisites

The [Adaptive Form block is enabled](/help/edge/docs/forms/create-forms.md) for your Edge Delivery Services project. 

## Add a repeatable section to a form 

Let's take an example of a loan application form. The form enables users to submit personal information. You can include co-applicant details using repeatable sections, with the option to add a minimum and maximum of three co-applicant sections.

"_You can use a Microsoft Excel file on your SharePoint Site or Google Sheet file on Google Drive to develop a form. Examples in this document are based on a [Microsoft Excel file on your SharePoint Site](https://www.aem.live/docs/setup-customer-sharepoint)._" 


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


## 더 보기

* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [양식을 활성화하여 데이터 전송](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [양식의 테마 및 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)
* [양식 구성 요소 및 해당 속성](/help/edge/docs/forms/form-components.md)
