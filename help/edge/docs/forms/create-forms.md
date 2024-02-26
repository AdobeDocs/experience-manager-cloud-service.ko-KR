---
title: AEM Forms Edge Delivery Service 시작하기
description: 완벽한 형태를 만들어, 빨리! ⚡ AEM Forms Edge Delivery 문서 기반 작성 = 더 행복한 사용자 및 검색 엔진을 위한 빠른 속도와 SEO 친화적인 양식.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 4a3ebcf7985253ebca24e90ab57ae7eaf3e924e9
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 1%

---


# AEM Forms Edge Delivery Service에서 양식 만들기

오늘날 디지털 시대에서는 모든 조직에 사용자 친화적인 양식을 만드는 것이 필수적입니다. AEM Forms Edge Delivery를 사용하면 Word 또는 Google 문서와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다.

이러한 양식은 Microsoft Excel 또는 Google Sheets 파일에 직접 데이터를 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft Sharepoint의 생생한 에코시스템과 강력한 API를 사용하여 제출된 데이터를 쉽게 처리하거나 기존 비즈니스 워크플로우를 시작할 수 있습니다.

AEM Forms Edge Delivery는 캡처된 데이터를 캡처하고 저장할 양식을 쉽게 만들 수 있도록 양식 블록을 제공합니다. 양식 만들기를 시작하려면 AEM EDS 프로젝트에 양식 블록을 포함할 수 있습니다. 시작하겠습니다.


## 사전 요구 사항

시작하기 전에 다음 단계를 완료했는지 확인하십시오.

* AEM Boilerplate를 사용하여 EDS(Edge Delivery Service) Github 프로젝트를 설정하고 로컬 컴퓨터에서 해당 Github 저장소를 복제합니다. 다음을 참조하십시오 [개발자 자습서](https://www.aem.live/developer/tutorial) 을 참조하십시오. 이 문서에서는 EDS(Edge Delivery Service) 프로젝트의 로컬 폴더를 참조하십시오. `[EDS Project repository]` .
* 복제 [Forms 블록 저장소](https://github.com/adobe/afb) 로컬 컴퓨터에서. EDS 웹 페이지에서 양식을 렌더링하는 코드가 포함되어 있습니다. 이 문서에서는 Forms 블록 저장소의 로컬 폴더를 다음과 같이 합니다. `[Forms Block repository]`.
* Google Sheets 또는 Microsoft SharePoint에 액세스할 수 있는지 확인합니다.


## 양식 만들기

+++ 1단계: Edge Delivery Service(EDS) 프로젝트에 양식 블록을 추가합니다.

다음 `Form block` eds 사이트에 양식을 추가하는 기능이 포함되어 있습니다. 블록은 AEM Boilerplate을 사용하여 생성된 프로젝트에 포함되지 않습니다. Edge Delivery Service 프로젝트에 양식 블록을 포함하려면 다음을 수행하십시오.

1. 다음 위치로 이동 `[Forms Block repository]/blocks` 로컬 컴퓨터의 폴더를 복사하고 `form` 폴더를 삭제합니다.

1. 다음 위치로 이동 `[EDS Project repository]/blocks/` 로컬 컴퓨터의 폴더를 붙여 넣고 `form` 폴더를 삭제합니다.

1. 체크인 `form` 폴더 및 기본 파일을 GitHub의 Edge 게재 서비스 프로젝트에 추가합니다.

   양식 블록이 GitHub의 EDS 프로젝트 저장소에 추가됩니다. GitHub 빌드가 실패하지 않는지 확인합니다.

   * &quot;&#39;../../scripts/lib-franklin.js&#39; 모듈에 대한 경로를 확인할 수 없습니다.&quot; 오류가 발생하면 `[EDS Project]/blocks/forms/form.js` 파일. import 문에서 `lib-franklin.js` 파일이 포함된 파일 `aem.js` 파일.

   * 린팅 오류가 발생하면 언제든지 무시하십시오. 린팅 검사를 무시하려면 `[EDS Project]\package.json` 에서 &quot;lint&quot; 스크립트를 파일링하고 업데이트합니다. `"lint": "npm run lint:js && npm run lint:css"` 끝 `"lint": "echo 'skipping linting for now'"`. 파일을 저장하고 GitHub 프로젝트에 커밋합니다.

이제 양식을 만들어 사이트에 추가할 수 있습니다.

+++

+++ 2단계: Microsoft Excel 또는 Google 시트를 사용하여 양식을 작성합니다.

복잡한 프로세스 대신 스프레드시트를 사용하여 양식을 쉽게 만들 수 있습니다. 먼저 스프레드시트에 행 및 열 헤더를 추가할 수 있습니다. 여기서 각 행은 양식 필드를 정의하고 각 열 헤더는 해당 양식 필드의 속성을 정의합니다.

예를 들어 다음 스프레드시트에서 행은 의 필드를 정의합니다 `contact us` 양식 및 열 머리글은 해당 필드의 속성을 정의합니다.

![연락처 스프레드시트](/help/edge/assets/contact-us-form-spreadsheet.png)

양식을 만들려면 다음 작업을 수행하십시오.

1. Microsoft SharePoint 또는 Google 드라이브에서 AEM Edge 게재 프로젝트 폴더를 엽니다.

1. AEM Edge 배달 프로젝트 디렉터리 아래 아무 곳에나 Microsoft Excel 통합 문서 또는 Google 시트를 만듭니다. 예를 들어, 라는 이름의 스프레드시트를 만듭니다 `contact-us` Google 드라이브의 AEM Edge 게재 프로젝트 디렉터리입니다.

1. 시트가 AEM 사용자와 공유되어 있는지 확인합니다(예: `helix@adobe.com`) [프로젝트에 대해 구성됨](https://www.aem.live/docs/setup-customer-sharepoint) 및 사용자는 시트에 대한 편집 권한이 있습니다.

1. 생성한 스프레드시트를 열고 기본 시트의 이름을 &quot;shared-default&quot;로 변경합니다.

   ![기본 시트의 이름을 &quot;shared-default&quot;로 바꿉니다.](/help/edge/assets/rename-sheet-to-shared-default.png)

1. 양식의 필드를 추가하려면 행 및 열 머리글을 `shared-default` 시트. 여기서 각 행은 양식 필드를 정의하고 각 열 머리글은 [속성](/help/edge/docs/forms/eds-form-field-properties))을 참조하십시오.

   빠르게 시작하려면 의 내용을 복사할 수 있습니다. [연락처 스프레드시트](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) 스프레드시트로 복사합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)

1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 를 클릭하여 시트를 미리 보고 게시합니다.

   ![AEM Sidekick을 사용하여 시트 미리보기 및 게시](/help/edge/assets/preview-form.png)

   미리보기 및 게시 시 브라우저는 시트의 콘텐츠를 JSON 형식으로 표시하는 새 탭을 엽니다. 나중에 양식을 렌더링하는 데 필요하므로 라이브 URL을 메모해 두십시오.

   URL 형식은 다음과 같습니다.

   ```JSON
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

+++

+++ 3단계: EDS(Edge Delivery Service) 페이지를 사용하여 양식을 미리 봅니다.


지금까지 양식 블록을 EDS 프로젝트에 추가하고 양식 구조를 준비했습니다. 이제 양식을 미리 보려면 다음을 수행하십시오.

1. Microsoft SharePoint 또는 Google 드라이브 계정으로 이동하여 AEM Edge 게재 프로젝트 디렉터리를 엽니다.

1. 양식을 포함할 문서 파일을 엽니다. 예를 들어 색인 파일을 엽니다. 새 문서 파일을 만들 수도 있습니다.

1. 문서 내에서 양식을 추가할 위치로 이동합니다.

1. 아래 표시된 것과 유사한 &#39;Form&#39;이라는 블록을 파일에 추가합니다.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   두 번째 행에는 이전 섹션에 하이퍼링크로 기록한 URL이 포함됩니다. 개발 또는 테스트 목적으로 미리보기 URL(.page URL)을 사용하거나 프로덕션용으로 게시 URL(.live)을 사용합니다.

   >[!IMPORTANT]
   >
   >
   > URL이 일반 텍스트로 표시되지 않고 하이퍼링크되어 있는지 확인합니다.


1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 을 클릭하여 페이지를 미리 봅니다. 이제 페이지에 양식이 표시됩니다.

   예를 들어 다음은 을 기반으로 하는 양식입니다 [연락처 스프레드시트](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![샘플 EDS 양식](/help/edge/assets/eds-form.png)

   이제 양식을 작성하고 제출 단추를 클릭하면 스프레드시트가 아직 데이터를 수락하도록 설정되지 않았으므로 다음과 유사한 오류가 발생합니다.

   ![양식 제출 오류](/help/edge/assets/form-error.png)

+++


## 다음 단계

[스프레드시트 준비](/help/edge/docs/forms/submit-forms.md) 양식 제출 시 데이터 수신을 시작합니다.



## 더 보기

* [양식 필드 속성](/help/edge/docs/forms/eds-form-field-properties)
* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [데이터를 전송할 양식 활성화](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-eds-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [테마 및 양식 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)
