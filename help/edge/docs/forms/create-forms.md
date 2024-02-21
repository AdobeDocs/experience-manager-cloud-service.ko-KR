---
title: AEM Forms Edge Delivery Service 시작하기
description: 완벽한 형태를 만들어, 빨리! ⚡ AEM Forms Edge Delivery 문서 기반 작성 = 더 행복한 사용자 및 검색 엔진을 위한 빠른 속도와 SEO 친화적인 양식.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: f37a99cd5cbfb745cb591e3be2a46a5f52139cb2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 1%

---


# AEM Forms Edge Delivery Service에서 양식 만들기

오늘날 디지털 시대에서는 모든 조직에 사용자 친화적인 양식을 만드는 것이 필수적입니다. AEM Forms Edge Delivery를 사용하면 Word 또는 Google 문서와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다.

이러한 양식은 Microsoft Excel 또는 Google Sheets 파일에 직접 데이터를 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft Sharepoint의 생생한 에코시스템과 강력한 API를 사용하여 제출된 데이터를 쉽게 처리하거나 기존 비즈니스 워크플로우를 시작할 수 있습니다.

## 사전 요구 사항

* Github 계정이 있습니다.
* Google Sheets 또는 Microsoft SharePoint에 액세스할 수 있습니다.
* Git, HTML, CSS 및 JavaScript의 기본 사항을 이해합니다.
* 로컬 개발을 위해 노드 및 NPM이 설치되어 있습니다.

## 시작하기 전

* EDS(Edge Delivery Service) 프로젝트를 설정하고 복제합니다. 다음을 참조하십시오 [개발자 자습서](https://www.aem.live/developer/tutorial) 을 참조하십시오.
* 복제 [Forms 블록 저장소](https://github.com/adobe/afb). 여기에는 양식을 렌더링하는 데 필요한 Form 블록이 포함됩니다.

![Edge 게재 시작 Forms](/help/edge/assets/getting-started-with-eds-forms.png)

## EDS(Edge Delivery Service) 프로젝트에 양식 블록 추가 {#add-forms-block-to-an-eds-project}

AEM Forms Edge Delivery에는 캡처된 데이터를 캡처하고 저장할 양식을 쉽게 만들 수 있도록 양식 블록이 포함되어 있습니다. Edge Delivery Service 프로젝트에 양식 블록을 포함하려면 다음을 수행하십시오.

1. 로컬 개발 환경에서 EDS(Edge Delivery Service) 프로젝트 폴더로 이동합니다.


   ```Shell
   cd [EDS Project folder]
   ```

1. 다음 이름의 폴더 만들기 `form` EDS 프로젝트 디렉토리 아래에 예를 들어 EDS 프로젝트의 디렉터리 아래에 `Portal`, 폴더 만들기 `form`.

   ```Shell
   mkdir form
   ```


1. 추가 [Forms 차단](https://github.com/adobe/afb/tree/main/blocks/form) 파일을 &#39;form&#39; 폴더에 저장합니다.

   ```shell
   cp -R <source:path of the form block> <destination: path of the form folder created in the previous step>
   
   For example
   
   cp -R Documents/afb/blocks/form Documents/portal/blocks/
   ```

1. GitHub의 Edge 게재 서비스 프로젝트에 &#39;양식&#39; 폴더 및 기본 파일을 체크인합니다.

   ```Shell
   git add .
   git commit -m "Added form block"
   git push origin
   ```

   이제 EDS 양식을 렌더링할 준비가 되었습니다.

   >[!NOTE]
   >
   > * 가져오기 요청/eds 프로젝트 빌드가 실패하고 가져오기 관련 오류가 발생하는 경우 `franklin-lib.js` 파일, 가져오기 문을 업데이트하여 `aem.js` 파일 대신 `franklin-lib.js` 파일.
   > * 린팅 오류가 발생하면 언제든지 무시하십시오. 린팅 검사를 무시하려면에서 package.json 파일로 이동하여 &quot;lint&quot; 스크립트를 업데이트합니다 `"lint": "npm run lint:js && npm run lint:css"` 끝 `"lint": "echo 'skipping linting for now'"`. 그런 다음 변경 사항을 package.json 파일에 커밋합니다.

## Microsoft Excel 또는 Google Sheet를 사용하여 양식 만들기 {#create-a-form-for-an-eds-project}

웹 사이트 개발자가 양식을 만들고 웹 사이트 방문자로부터 수집할 정보를 선택할 수 있도록 하는 것이 유용합니다. 작성자는 복잡한 프로세스 대신 스프레드시트를 사용하여 양식을 쉽게 설정할 수 있습니다. 올바른 열 헤더를 추가한 다음 양식 블록을 사용하여 웹 사이트에 번거롭게 표시해야 합니다. 양식을 만들려면 다음 작업을 수행하십시오.

1. Microsoft SharePoint 또는 Google 드라이브의 AEM Edge 배달 프로젝트 디렉터리 아래 아무 곳에나 Microsoft Excel 통합 문서 또는 Google 시트를 만듭니다.

1. AEM 사용자(예: `helix@adobe.com`)을 프로젝트에 대해 구성한 경우 시트에 대한 편집 권한이 있습니다.

1. 만든 통합 문서를 열고 기본 시트의 이름을 &quot;shared-default&quot;로 변경합니다.

   ![기본 시트의 이름을 &quot;shared-default&quot;로 바꿉니다.](/help/edge/assets/rename-sheet-to-helix-default.png)

1. 의 내용을 복사합니다. [연락처 스프레드시트](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) 스프레드시트로 복사합니다.

   ![연락처 스프레드시트](/help/edge/assets/contact-us-form-spreadsheet.png)

1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 를 클릭하여 시트를 미리 보고 게시합니다.

   미리보기 및 게시 시 브라우저는 시트의 콘텐츠를 JSON 형식으로 표시하는 새 탭을 엽니다. 나중에 양식을 렌더링하는 데 필요하므로 라이브 URL을 메모해 두십시오.

   URL 형식은 다음과 같습니다.

   ```shell
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

## EDS(Edge Delivery Service) 페이지를 사용하여 양식 미리 보기 {#add-a-form-to-your-eds-page}

지금까지 EDS 프로젝트에 대한 양식 블록을 활성화하고 양식 구조를 준비했습니다. 이제 양식을 EDS 페이지에 포함하고 렌더링하려면 다음을 수행하십시오.

1. Microsoft SharePoint 또는 Google 드라이브의 AEM Edge 게재 프로젝트 디렉토리로 이동합니다.

1. 페이지에 양식을 추가하려면 해당 문서 파일을 엽니다. 예를 들어 색인 파일을 엽니다.

1. 문서 내에서 양식을 추가할 위치로 이동합니다.

1. 아래 표시된 것과 유사한 &#39;Form&#39;이라는 블록을 파일에 추가합니다.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   두 번째 행에는 이전 섹션에서 기록한 URL을 하이퍼링크로 포함합니다.

1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 을 클릭하여 페이지를 미리 보고 게시합니다. 양식이 렌더링됩니다.

   예를 들어 다음은 을 기반으로 하는 양식입니다 [연락처 스프레드시트](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![연락처(EDS 양식)](/help/edge/assets/eds-form.png)

   양식 블록은 양식을 렌더링하지만 아직 데이터를 수락할 준비가 되지 않았습니다. 제출 단추를 클릭하면 다음과 유사한 오류가 발생합니다.

   ![양식 제출 오류](/help/edge/assets/form-error.png)

   [데이터를 허용하도록 시트 준비](/help/edge/docs/forms/submit-forms.md). 데이터를 수락하기 위해 준비하는 시트 게시물에 데이터를 제출할 수 있습니다.


## 더 보기

* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [데이터를 전송할 양식 활성화](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-eds-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [테마 및 양식 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)