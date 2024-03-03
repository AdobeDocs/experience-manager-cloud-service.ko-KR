---
title: AEM Forms Edge Delivery Services 양식 게시
description: AEM Forms Edge Delivery Services 양식 게시
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 10%

---


# 양식 게시

데이터 수집 또는 제출을 위해 고객과 양식을 공유할 준비가 되면 이를 게시하여 고객이 양식을 쉽게 사용할 수 있도록 할 수 있습니다.

![문서 기반 작성 에코시스템](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## 전제 조건

* 다음 [적응형 양식 블록은 GitHub의 EDS 프로젝트에 대해 활성화됩니다](/help/edge/docs/forms/create-forms.md).
* 양식이 완전히 테스트되어 사용할 준비가 되었습니다.
* 사용자 [스프레드시트가 구성되었습니다.](/help/edge/docs/forms/submit-forms.md) 데이터를 승인합니다.

## 양식 게시

+++ 1. 스프레드시트 게시

1. Microsoft SharePoint 또는 Google 드라이브 계정을 열고 AEM Edge 게재 프로젝트 디렉터리로 이동합니다.

1. 양식이 있는 스프레드시트를 엽니다. 예를 들어 `enquiry` 양식 Microsoft Excel 통합 문서입니다.

1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 를 클릭하여 시트를 미리 봅니다.

   ![AEM Sidekick을 사용하여 시트 미리 보기](/help/edge/assets/preview-form.png)

   미리보기 작업이 성공적으로 완료되면 스프레드시트 콘텐츠가 JSON 형식으로 변환됩니다. 그런 다음 미리보기 페이지는 이 콘텐츠를 구조화된 테이블 형식으로 표시합니다. 예를 들어 첨부된 이미지는 &#39;문의&#39; 양식의 콘텐츠를 보여 줍니다.

   ![Forms 미리보기 JSON 형식](/help/edge/assets/forms-preview-json-format.png)

1. AEM Sidekick을 사용하여 시트를 게시합니다. 다음 섹션에서 양식을 렌더링하는 데 필요하므로 게시 URL을 캡처해야 합니다. URL 형식은 다음과 같습니다.


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` 는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>` 는 GitHub 저장소를 나타냅니다.
   * `<owner>` 는 GitHub 리포지토리를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.

   예를 들어 프로젝트의 저장소 이름이 &quot;포털&quot;이고 계정 &quot;wkndforms&quot; 아래에 있으며 &quot;주&quot; 분기를 사용하는 경우 URL은 다음과 같습니다.

   `https://main--portal--wkndforms.hlx.page/enquiry.json`

+++

+++ 2. 웹 페이지에 양식 추가

추가 `<form>.json` 양식 작성기가 양식을 쉽게 작성하고 제출할 수 있도록 해 주는 고객 상호 작용을 용이하게 하는 웹 페이지입니다.


웹 페이지에 양식을 추가하려면:

1. Microsoft SharePoint 또는 Google 드라이브 계정에 액세스하여 다음 페이지로 이동합니다. `[AEM Edge Delivery project directory]`.

1. 양식을 포함할 문서 파일을 엽니다. 예를 들어 `index.docx` 파일 또는 다른 방법으로 새 문서를 만듭니다.

1. 문서에서 양식을 삽입할 섹션을 식별하고 그에 따라 해당 섹션으로 이동합니다.

1. 아래 제공된 예제와 유사하게 &#39;Form&#39;이라는 블록을 파일에 추가합니다.

   | 양식 |
   |---|
   | [https://main--portal--wkndforms.hlx.live/enquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   이 블록은 양식이 포함된 자리 표시자 역할을 합니다. 블록의 두 번째 행에 의 URL을 추가합니다. `<form>.json` 파일을 하이퍼링크로 표시합니다.

   >[!IMPORTANT]
   >
   >
   > URL이 일반 텍스트로 표시되지 않고 하이퍼링크로 포맷되어 있는지 확인합니다.

   개발 또는 테스트 목적으로 미리보기 URL(.page URL)을 사용하거나 프로덕션용으로 게시 URL(.live)을 사용합니다. 다음은 미리보기 및 게시 URL의 예입니다.

   **미리보기 URL**
| 양식 | |—| | [https://main--portal--wkndforms.hlx.page/enquiry.json](https://main--portal--wkndforms.hlx.page/enquiry.json)  |


   **게시 URL**
| 양식 | |—| | [https://main--portal--wkndforms.hlx.live/enquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json)  |

1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 을 클릭하여 웹 페이지를 미리 봅니다. 이제 페이지에 양식이 표시됩니다. 예를 들어 다음은 을 기반으로 하는 양식입니다 [조회 스프레드시트](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![샘플 EDS 양식](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

1. AEM Sidekick을 사용하여 양식을 게시합니다. 이제 고객이 양식을 작성하여 제출할 수 있습니다.

+++

## 문제 해결

+++ 양식에 데이터를 제출할 수 없음

다음 메시지와 유사한 오류가 발생하면 스프레드시트가 구성되지 않은 것입니다. [제출된 항목 수락](/help/edge/docs/forms/submit-forms.md) 아직 데이터가 없습니다.

![양식 제출 시 오류](/help/edge/assets/form-error.png)

+++


## 더 보기

* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [양식을 활성화하여 데이터 전송](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [양식의 테마 및 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)
