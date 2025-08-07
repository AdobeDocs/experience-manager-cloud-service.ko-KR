---
title: 적응형 양식 블록을 사용하여 양식 만들기
description: AEM Forms용 Edge Delivery Services 사용을 시작해 보십시오. 완벽한 양식을 빠르게 제작하십시오. AEM Forms Edge Delivery 문서 기반 작성 = 놀라운 속도 및 만족도가 높은 사용자를 위한 SEO 친화적 양식과 검색 엔진.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0cf881a2-3784-45eb-afe8-3435e5e95cf4
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 100%

---

# 적응형 양식 블록을 사용하여 양식 만들기

>[!VIDEO](https://video.tv.adobe.com/v/3427881?quality=12&learn=on)

AEM Forms Edge Delivery는 데이터를 캡처하고 캡처한 데이터를 저장하는 양식을 쉽게 만들 수 있는 적응형 양식 블록이라는 블록을 제공합니다. [적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트를 만들거나](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [기존 AEM 프로젝트에 적응형 양식 블록을 추가](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)할 수 있습니다.

이러한 양식은 데이터를 Microsoft Excel 또는 Google Sheets 파일에 직접 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft SharePoint의 활발한 에코시스템과 강력한 API를 사용하여 쉽게 제출 데이터를 처리하거나 기존 비즈니스 워크플로를 시작할 수 있습니다.

![문서 기반 작성 에코시스템](/help/edge/assets/document-based-authoring-workflow-create-form.png)


## 사전 요구 사항

시작하기 전에 다음 단계를 완료했는지 확인하십시오.

- [AEM Forms 상용구를 사용하는 AEM 프로젝트](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)를 설정하고, [기존 AEM 프로젝트에 적응형 양식 블록을 추가](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)하고, 로컬 컴퓨터의 해당 GitHub 저장소를 복제합니다.
<!--In this document, the local folder of your Edge Delivery Services (EDS) project is referred as `[EDS Project repository]`.  -->
- Google Sheets 또는 Microsoft SharePoint에 액세스할 수 있는지 확인하십시오. Microsoft SharePoint를 콘텐츠 소스로 설정하려면 [SharePoint 사용 방법](https://www.aem.live/docs/setup-customer-sharepoint)을 참조하십시오.



## 양식 만들기

<!--
+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery Service Site. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
2. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

3. on your local machine and copy the `form` folder. 
4. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

- **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

- **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project. -->

+++ 1단계: Microsoft Excel 또는 Google Sheets를 사용하여 양식을 작성합니다.

복잡한 프로세스를 탐색하는 대신 스프레드시트를 사용하여 쉽게 양식을 만들 수 있습니다. 양식 구조를 구성할 행과 열을 정의할 수 있습니다. 각 행은 개별 [양식 필드](/help/edge/docs/forms/form-components.md#available-components)를 나타내며, 열 헤더는 해당 [필드 속성](/help/edge/docs/forms/form-components.md#components-properties)을 정의합니다.

예를 들어 행이 [문의](/help/edge/assets/enquiry.xlsx) 스프레드시트의 필드를 간략하게 설명하고 열 헤더가 해당 속성을 정의하는 다음 스프레드시트를 고려해 보십시오.

![문의 스프레드시트](/help/edge/assets/enquiry-form-spreadsheet.png)

계속해서 양식을 만들려면

1. Microsoft SharePoint 또는 Google Drive에서 AEM Edge Delivery 프로젝트 폴더에 액세스합니다.

1. AEM Edge Delivery 프로젝트 디렉터리 내의 어느 곳에나 Microsoft Excel 통합 문서 또는 Google Sheets를 만듭니다. 예를 들어 Google Drive의 AEM Edge Delivery 프로젝트 디렉터리에 `enquiry`라는 스프레드시트를 만듭니다.

   <!-- ![Sample Content on Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)-->

1. [프로젝트에 지정된 구성에 따라](https://www.aem.live/docs/setup-customer-sharepoint) 시트가 해당 AEM 사용자(예: `forms@adobe.com`)와 공유되고 있는지 확인합니다. 사용자에게 시트에 대한 편집 권한을 부여합니다.

1. 작성된 스프레드시트를 연 다음 기본 시트 이름을 “shared-aem”로 바꿉니다.

   ![기본 시트의 이름을 “shared-default”로 바꾸기](/help/edge/assets/rename-sheet-to-shared-default.png)

   >[!IMPORTANT]
   >
   >**양식이 작성된 시트에는 지정할 수 있는 이름에 제한이 있습니다. 시트 이름으로는 `helix-default`와 `shared-aem`만 사용할 수 있습니다.**

1. 양식 필드를 추가하려면 “shared-aem” 시트에 행과 열 헤더를 삽입합니다. 각 행은 해당 필드 [속성](/help/edge/docs/forms/form-components.md#components-properties)을 정의하는 열 헤더로 [양식 필드](/help/edge/docs/forms/form-components.md#available-components)를 나타내야 합니다.


   빠른 시작을 하려면 [문의 스프레드시트](/help/edge/assets/enquiry.xlsx) 콘텐츠를 스프레드시트에 복사하는 것이 좋습니다. 콘텐츠를 복사하면 스프레드시트를 저장합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 봅니다.

   ![AEM Sidekick을 사용하여 시트 미리보기](/help/edge/assets/preview-form.png)

   미리보기 시 새 브라우저 탭에 시트 내용이 JSON 형식으로 표시됩니다. 이는 다음 섹션의 양식을 렌더링하는 데 필요하므로 미리보기 URL을 캡처해야 합니다. URL 형식은 다음과 같습니다.


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form-path>/<form-file-name>.json
   ```

   - `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   - `<repository>`는 GitHub 저장소를 나타냅니다.
   - `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.

   예를 들어 프로젝트 저장소의 이름이 “wefinance”이고 “wkndform” 계정 아래에서 “main” 분기를 사용하는 경우 URL은 다음과 같습니다.

`https://main--wefinance--wkndform.aem.page/enquiry.json`
&lt;!--(https://main--wefinance--wkndform.aem.page/enquiry.json)-->


+++

+++ 2단계: Edge Delivery Services 페이지를 사용하여 양식을 미리 봅니다.


지금까지 양식의 구조를 준비했습니다. 이제 양식을 미리 보려면 다음 작업을 수행하십시오.

1. Microsoft SharePoint 또는 Google Drive의 계정으로 연 다음 AEM Edge Delivery 프로젝트 디렉터리로 이동합니다.



1. 양식을 임베드할 문서 파일(예: index 파일)을 엽니다. 또는 [새 문서를 생성](/help/edge/assets/enquiry-form.docx)할 수 있습니다.

1. 양식을 추가하려는 문서 내에서 원하는 위치로 이동합니다.

1. 양식을 렌더링하기 위해 양식 블록을 작성합니다. 삽입 > 테이블을 선택하고 열 1개 및 행 2개가 있는 테이블을 만듭니다. 테이블의 이름을 “Form”으로 지정하고 두 번째 행에 미리보기 URL을 붙여넣습니다. 아래 그림과 같이 URL이 일반 텍스트가 아닌 하이퍼링크 형식이어야 합니다.

   | 양식 |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |


   ![웹 페이지에 적응형 양식 블록 추가](/help/edge/assets/enquiry-doc-to-embed-form.png)

   이 블록은 양식이 임베드된 플레이스홀더 역할을 합니다. 블록의 두 번째 행에서 `<form>.json` 파일의 미리보기 URL을 하이퍼링크로 추가합니다.

   >[!IMPORTANT]
   >
   >
   > URL 형식이 일반 텍스트로 표시되지 않고 하이퍼링크로 지정되었는지 확인합니다.


1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 문서를 미리 봅니다. 이제 페이지에 양식이 표시됩니다. 예를 들어 다음은 [문의 스프레드시트](/help/edge/assets/enquiry-form.docx)를 기반으로 한 양식입니다.


   [![샘플 EDS 양식](/help/edge/assets/updated-form.png)](https://main--wefinance--wkndform.aem.page/enquiry-form)

   이제 양식을 작성하고 제출 버튼을 클릭하면 스프레드시트가 아직 데이터를 허용하도록 설정되지 않았기 때문에 다음과 유사한 오류가 발생합니다.

   ![양식 제출 시 오류](/help/edge/assets/form-error.png)

+++


## 다음 단계

[스프레드시트를 준비](/help/edge/docs/forms/submit-forms.md)하여 양식 제출 시 데이터를 수신합니다.


