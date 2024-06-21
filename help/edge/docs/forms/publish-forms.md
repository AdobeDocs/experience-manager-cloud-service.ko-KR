---
title: AEM Forms Edge Delivery Services 양식 게시
description: AEM Forms Edge Delivery Services 양식 게시
feature: Edge Delivery Services
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 100%

---

# 양식 게시 및 데이터 수집 시작

데이터를 수집하거나 제출하기 위해 고객과 양식을 공유할 준비가 되면 고객이 양식을 쉽게 사용할 수 있도록 양식을 게시하기만 하면 됩니다.

![문서 기반 작성 생태계](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## 전제 조건

* [AEM Forms 상용구](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)를 기반으로 한 AEM 프로젝트가 있거나 [기존 AEM 프로젝트에 적응형 양식 블록을 추가했습니다.](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)
* 양식 전체를 테스트하여 사용할 준비가 되었습니다.
* [스프레드시트를 구성하여](/help/edge/docs/forms/submit-forms.md) 데이터를 수신할 수 있습니다.


## 양식 게시

+++ 1. 스프레드시트 게시

1. Microsoft SharePoint 또는 Google Drive의 계정으로 연 다음 AEM Edge Delivery 프로젝트 디렉터리로 이동합니다.

1. 양식이 있는 스프레드시트를 엽니다. 예: `enquiry` Microsoft Excel 통합 문서 양식입니다.

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 봅니다.

   ![AEM Sidekick을 사용하여 시트 미리보기](/help/edge/assets/preview-form.png)

   미리보기 작업이 정상적으로 완료되면 스프레드시트 콘텐츠는 JSON 형식으로 변환됩니다. 그런 다음 미리보기 페이지는 이 콘텐츠를 구조화된 테이블 형식으로 나타냅니다. 예를 들어 함께 제공되는 이미지는 “문의” 양식의 콘텐츠를 보여 줍니다.

   ![양식 미리보기 JSON 형식](/help/edge/assets/forms-preview-json-format.png)

1. AEM Sidekick을 사용하여 시트를 게시합니다. 이는 다음 섹션의 양식을 렌더링하는 데 필요하므로 게시 URL을 캡처해야 합니다. URL 형식은 다음과 같습니다.


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.

   예를 들어 프로젝트 저장소의 이름이 “portal”이고 “wkndforms” 계정 아래에서 “main” 분기를 사용하는 경우 URL은 다음과 같습니다.

   `https://main--portal--wkndforms.hlx.page/enquiry.json`

+++

+++ 2. 웹 페이지에 양식 추가

웹 페이지에 `<form>.json`을 추가하면 고객과 간편하게 상호 작용하여 양식 작성기에서 양식을 손쉽게 작성하고 제출할 수 있습니다.


웹 페이지에 양식을 추가하려면

1. Microsoft SharePoint 또는 Google Drive 계정에 액세스한 다음 `[AEM Edge Delivery project directory]`로 이동합니다.

1. 양식을 임베드하려는 문서 파일을 엽니다. 예를 들어 `index.docx` 파일을 열거나 새 문서를 만들 수 있습니다.

1. 양식을 삽입할 문서 내에서 원하는 섹션을 확인하고 이에 따라 해당 섹션으로 이동합니다.

1. 아래 제공된 예와 유사한 “Form”이라는 블록을 파일에 추가합니다.

   | 양식 |
   |---|
   | [https://main--wefinance--wkndforms.hlx.live/enquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |

   ![파일에 ‘Form’이라는 블록 추가](/help/edge/assets/enquiry-doc-to-embed-form.png)

   이 블록은 양식이 임베드된 플레이스홀더 역할을 합니다. 블록의 두 번째 행에서 `<form>.json` 파일의 URL을 하이퍼링크로 추가합니다.

   >[!IMPORTANT]
   >
   >
   > URL 형식이 일반 텍스트로 표시되지 않고 하이퍼링크로 지정되었는지 확인합니다.

   개발 또는 테스트 목적으로는 미리보기 URL(.page URL)을 사용하고, 프로덕션용으로는 게시 URL(.live)을 사용합니다. 다음은 미리보기 및 게시 URL의 예입니다.

   **미리보기 URL**

   | 양식 |
   |---|
   | [https://main--wefinance--wkndforms.hlx.page/enquiry.json](https://main--wefinance--wkndforms.hlx.page/enquiry.json) |


   **게시 URL**

   | 양식 |
   |---|
   | [https://main--wefinance--wkndforms.hlx.live/enquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 웹 페이지를 미리 봅니다. 이제 페이지에 양식이 표시됩니다. 예를 들어 다음은 [문의 스프레드시트](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0)를 기반으로 한 양식입니다.


   ![샘플 EDS 양식](/help/edge/assets/eds-form.png)

1. AEM Sidekick을 사용하여 양식을 게시합니다. 이제 고객은 양식을 작성하여 제출할 수 있습니다.

+++

## 문제 해결

+++ 양식에 데이터를 제출할 수 없음

다음 메시지와 유사한 오류가 발생하는 경우 스프레드시트가 [제출된 데이터를 수신](/help/edge/docs/forms/submit-forms.md)할 수 있도록 구성되지 않았음을 의미합니다.

![양식 제출 시 오류](/help/edge/assets/form-error.png)

+++


## 추가 참조

{{see-more-forms-eds}}
