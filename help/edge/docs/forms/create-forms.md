---
title: AEM Forms Edge Delivery Service 시작하기 양식을 만듭니다.
description: 완벽한 양식을 빠르게 제작하십시오. ⚡ AEM Forms Edge Delivery 문서 기반 작성 = 놀라운 속도 및 만족도가 높은 사용자를 위한 SEO 친화적 양식과 검색 엔진.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 26%

---


# 적응형 양식 블록을 사용하여 양식 만들기

오늘날의 디지털 시대에는 사용자 친화적인 양식을 만드는 것이 모든 조직에 필수적입니다. AEM Forms Edge Delivery를 사용하면 Word 또는 Google Docs와 같은 익숙한 도구를 사용하여 양식을 만들 수 있습니다.

이러한 양식은 데이터를 Microsoft Excel 또는 Google Sheets 파일에 직접 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft Sharepoint의 활발한 에코시스템과 강력한 API를 사용하여 쉽게 제출 데이터를 처리하거나 기존 비즈니스 워크플로를 시작할 수 있습니다.

![문서 기반 작성 에코시스템](/help/edge/assets/document-based-authoring-workflow-create-form.png)

AEM Forms Edge Delivery는 캡처된 데이터를 캡처하고 저장할 양식을 쉽게 만들 수 있도록 적응형 양식 블록이라고 하는 블록을 제공합니다. AEM EDS 프로젝트에 적응형 양식 블록을 포함하여 양식 만들기를 시작할 수 있습니다. 시작하기


## 사전 요구 사항

시작하기 전에 다음 단계를 완료했는지 확인하십시오.

* AEM Boilerplate를 사용하여 EDS(Edge Delivery Service) GitHub 프로젝트를 설정하고 로컬 컴퓨터에서 해당 GitHub 리포지토리를 복제합니다. 자세한 내용은 [개발자 튜토리얼](https://www.aem.live/developer/tutorial)을 참조하십시오. 이 문서에서 Edge Delivery Service(EDS) 프로젝트의 로컬 폴더란 `[EDS Project repository]`를 말합니다.
* Google Sheets 또는 Microsoft SharePoint에 액세스할 수 있는지 확인하십시오. Microsoft SharePoint을 컨텐츠 소스로 설정하려면 를 참조하십시오. [Sharepoint 사용 방법](https://www.aem.live/docs/setup-customer-sharepoint)



## 양식 만들기

+++ 1단계: 적응형 양식 블록을 EDS(Edge Delivery Service) 프로젝트에 추가합니다.

적응형 양식은 사용자가 Edge 게재 서비스 사이트용 양식을 만들 수 있도록 합니다. 그러나 이 블록은 기본 AEM 보일러판에 포함되지 않습니다(Edge Delivery Service 프로젝트를 만드는 데 사용됨). 적응형 양식 블록을 Edge Delivery Service 프로젝트에 원활하게 통합하려면 다음을 수행하십시오.

1. **적응형 양식 블록 저장소 복제**: 복제 [적응형 양식 블록 저장소](https://github.com/adobe/afb) 로컬 컴퓨터에서. 여기에는 EDS 웹 페이지에 양식을 렌더링하는 코드가 포함되어 있습니다. 이 문서에서 양식 블록 저장소의 로컬 폴더란 `[Adaptive Form Block repository]`를 말합니다.
1. **적응형 양식 블록 저장소를 찾습니다.** 액세스 [적응형 양식 블록 저장소]/blocks 폴더를 로컬 컴퓨터에 복사하고 `form` 폴더를 삭제합니다.
1. **적응형 양식 블록을 EDS 프로젝트에 붙여넣습니다.**
다음 위치로 이동 [EDS 프로젝트 저장소]로컬 컴퓨터의 /blocks/ 폴더를 만들고 양식 폴더를 붙여 넣습니다.
1. **GitHub에 변경 사항 커밋:** 양식 폴더 및 기본 파일을 GitHub의 Edge 게재 서비스 프로젝트에 체크 인합니다.

이 단계를 완료하면 적응형 양식 블록이 GitHub의 EDS(Edge Delivery Service) 프로젝트 저장소에 성공적으로 추가됩니다. 이제 양식을 만들어 EDS Sites 페이지에 추가할 수 있습니다.


**GitHub 빌드 문제 해결**

잠재적인 문제를 해결하여 원활한 GitHub 빌드 프로세스를 보장합니다.

* **모듈 경로 오류 해결:**
&quot;모듈 &quot;&#39;../../scripts/lib-franklin.js&#39;에 대한 경로를 확인할 수 없습니다.&quot; 오류가 발생하면 [EDS 프로젝트]/blocks/forms/form.js 파일입니다. lib-franklin.js 파일을 aem.js 파일로 바꾸어 가져오기 구문을 업데이트합니다.

* **린팅 오류 처리:**
만약 당신이 어떤 린팅 오류라도 발견한다면, 당신은 그것들을 우회할 수 있다. 를 엽니다. [EDS 프로젝트]/package.json 파일을 만들고 &quot;lint&quot; 스크립트를 &quot;lint&quot;: &quot;npm run lint:js &amp;&amp; npm run lint:css&quot;에서 &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;&quot;로 수정합니다. 파일을 저장하고 변경 내용을 GitHub 프로젝트에 커밋합니다.



+++

+++ 2단계: Microsoft Excel 또는 Google 시트를 사용하여 양식을 작성합니다.

복잡한 프로세스를 탐색하는 대신 스프레드시트를 사용하여 손쉽게 양식을 만들 수 있습니다. 먼저 스프레드시트에 행 및 열 헤더를 추가할 수 있습니다. 여기서 각 행은 양식 필드를 나타내고 각 열 헤더는 해당 필드의 속성을 정의합니다.

예를 들어 행이 다음에 대한 필드를 아웃라인하는 스프레드시트를 생각해 보십시오. `enquiry` 양식 및 열 머리글은 속성을 정의합니다.

![조회 스프레드시트](/help/edge/assets/enquiry-form-spreadsheet.png)

양식 만들기를 진행하려면 다음을 수행하십시오.

1. Microsoft SharePoint 또는 Google 드라이브의 AEM Edge 게재 프로젝트 폴더에 액세스합니다.

1. AEM Edge 배달 프로젝트 디렉터리 내 어디에나 Microsoft Excel 통합 문서 또는 Google 시트를 만듭니다. 예를 들어 Google Drive의 AEM Edge Delivery 프로젝트 디렉터리에 `enquiry`라는 스프레드시트를 만듭니다.

1. 시트가 적절한 AEM 사용자와 공유되어 있는지 확인합니다(예: `helix@adobe.com`) [프로젝트에 지정된 구성에 따라](https://www.aem.live/docs/setup-customer-sharepoint). 사용자에게 시트에 대한 편집 권한을 부여합니다.

1. 생성된 스프레드시트를 열고 기본 시트의 이름을 &quot;shared-default&quot;로 바꿉니다.

   ![기본 시트의 이름을 “shared-default”로 바꾸기](/help/edge/assets/rename-sheet-to-shared-default.png)

1. 양식 필드를 추가하려면 &#39;shared-default&#39; 시트에 행과 열 머리글을 삽입합니다. 각 행은 다음을 나타냅니다. [양식 필드](/help/edge/docs/forms/form-components.md#available-components), 열 헤더가 해당 필드를 정의하는 경우 [속성](/help/edge/docs/forms/form-components.md#components-properties).

   빠르게 시작하려면 의 콘텐츠를 복사하는 것이 좋습니다. [조회 스프레드시트](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) 스프레드시트로 이동합니다. 콘텐츠를 복사한 후 스프레드시트를 저장합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 를 클릭하여 시트를 미리 봅니다.

   ![AEM Sidekick을 사용하여 시트 미리 보기](/help/edge/assets/preview-form.png)

   미리 볼 때 새 브라우저 탭에 시트의 콘텐츠가 JSON 형식으로 표시됩니다. 다음 섹션의 양식을 렌더링하는 데 필요하므로 미리 보기 URL을 캡처해야 합니다. URL 형식은 다음과 같습니다.


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` 는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>` 는 GitHub 저장소를 나타냅니다.
   * `<owner>` 는 GitHub 리포지토리를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.

   예를 들어 프로젝트의 저장소 이름이 &quot;포털&quot;이고 계정 &quot;wkndforms&quot; 아래에 있으며 &quot;주&quot; 분기를 사용하는 경우 URL은 다음과 같습니다.

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ 3단계: Edge Delivery Service(EDS) 페이지를 사용하여 양식을 미리 봅니다.


지금까지 EDS 프로젝트에 적응형 양식 블록을 추가하고 양식 구조를 준비했습니다. 이제 양식을 미리 보려면 다음 작업을 수행하십시오.

1. **프로젝트 디렉터리에 액세스:** Microsoft SharePoint 또는 Google 드라이브 계정을 열고 AEM Edge 게재 프로젝트 디렉터리로 이동합니다.

1. **문서에 양식 포함:** 문서 파일(예: 인덱스 파일)을 열어 양식을 포함합니다. 또는 새 문서를 만들 수 있습니다.

1. **원하는 위치로 이동합니다.** 양식을 추가하려는 문서 내에서 원하는 위치로 이동합니다.

1. **적응형 양식 블록 추가:** 아래 그림과 같이 파일에 &#39;Form&#39;이라는 블록을 삽입합니다.

   | 양식 |
   |---|
   | [https://main--portal--wkndforms.hlx.live/enquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   이 블록은 양식이 포함된 자리 표시자 역할을 합니다. 블록의 두 번째 행에 의 미리보기 URL을 추가합니다. `<form>.json` 파일을 하이퍼링크로 표시합니다.

   >[!IMPORTANT]
   >
   >
   > URL이 일반 텍스트로 표시되지 않고 하이퍼링크로 포맷되어 있는지 확인합니다.


1. 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 문서를 미리 보기 위해 이제 페이지에 양식이 표시됩니다. 예를 들어 다음은 을 기반으로 하는 양식입니다 [조회 스프레드시트](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![샘플 EDS 양식](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   이제 양식을 작성하고 제출 버튼을 클릭하면 스프레드시트가 아직 데이터를 허용하도록 설정되지 않았기 때문에 다음과 유사한 오류가 발생합니다.

   ![양식 제출 시 오류](/help/edge/assets/form-error.png)

+++


## 다음 단계

[스프레드시트를 준비](/help/edge/docs/forms/submit-forms.md)하여 양식 제출 시 데이터를 수신합니다.



## 더 보기

* [양식 구성 요소](/help/edge/docs/forms/form-components.md)
* [양식 필드 속성](/help/edge/docs/forms/eds-form-field-properties)
* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [양식을 활성화하여 데이터 전송](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [양식의 테마 및 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)
