---
title: AEM Forms용 Edge Delivery Services 시작하기 - 개발자 자습서
description: 이 튜토리얼에서는 새로운 AEM(Adobe Experience Manager Forms) 프로젝트를 시작하고 실행하는 방법을 안내합니다. 10~20분 안에 나만의 양식을 만들 수 있습니다.
feature: Edge Delivery Services
exl-id: bb7e93ee-0575-44e1-9c5e-023284c19490
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: tm+mt
source-wordcount: '1850'
ht-degree: 98%

---

# 시작하기 - 개발자 튜토리얼

오늘날의 디지털 시대에는 사용자 친화적인 양식을 만드는 것이 모든 조직에 필수적입니다. AEM Forms(EDS)용 Edge Delivery Services을 사용하면 Google 문서 및 Microsoft Office와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다.

이러한 양식은 데이터를 Microsoft Excel 또는 Google Sheets 파일에 직접 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft SharePoint의 활발한 에코시스템과 강력한 API를 사용하여 쉽게 제출 데이터를 처리하거나 기존 비즈니스 워크플로를 시작할 수 있습니다.

AEM Forms는 데이터를 캡처하고 캡처한 데이터를 저장하는 양식을 쉽게 만들 수 있는 적응형 양식 블록이라는 블록을 제공합니다. [적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트를 만들거나](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [기존 AEM 프로젝트에 적응형 양식 블록을 추가](#add-adaptive-forms-block-to-your-existing-aem-project)할 수 있습니다.

이 AEM Forms 튜토리얼에서는 새로운 Adobe Experience Manager(AEM) Forms 프로젝트를 사용하여 사용자 정의 양식을 만들고, 미리 보고, 게시하는 과정을 안내합니다.

## 사전 요구 사항

* GitHub 계정이 있고 Git 기본 사항을 이해하고 있습니다.
* Google 또는 Microsoft SharePoint 계정이 있습니다.
* HTML, CSS 및 JavaScript의 기본 사항을 이해합니다.
* 로컬 개발을 위해 Node/npm이 설치되어 있습니다.

**주의!** 이 튜토리얼에서는 macOS, Chrome 및 Visual Studio Code를 사용합니다. 단계는 다른 설정에 맞게 조정할 수 있지만 스크린샷과 특정 UI 요소는 선택한 운영 체제, 브라우저 및 코드 편집기에 따라 다를 수 있습니다.


## 적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트 만들기

AEM Forms 상용구 템플릿을 사용하면 적응형 양식 블록으로 사전 구성된 AEM 프로젝트를 빠르게 시작할 수 있습니다. AEM 모범 사례를 따르면서 바로 양식 작성을 시작하는 가장 빠르고 쉬운 방법입니다.

### AEM Forms 상용구 저장소 템플릿 시작하기

1. AEM 프로젝트의 GitHub 저장소를 만듭니다. 저장소를 만드는 방법은 다음과 같습니다.
   1. [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)로 이동합니다.

      ![AEM Forms 상용구](/help/edge/assets/aem-forms-boilerplate.png)
   1. **이 템플릿 사용** 옵션을 클릭하고 **새 저장소 만들기** 옵션을 선택합니다. 새 저장소 만들기 화면이 열립니다.

      ![AEM Forms 상용구를 사용하여 새 저장소 만들기](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. 새 저장소 만들기 화면에서 **소유자**&#x200B;를 선택하고 **저장소 이름**&#x200B;을 지정합니다. Adobe에서는 저장소를 **공개**&#x200B;로 설정할 것을 권장합니다. 따라서 **공개** 옵션을 선택하고 **저장소 만들기**&#x200B;를 클릭합니다.

   ![저장소를 공개로 설정](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. 저장소에 AEM Code Sync GitHub 앱을 설치합니다. 설치하는 방법은 다음과 같습니다.
   1. [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)로 이동합니다.
   1. AEM Code Sync 설치 화면에서 **저장소만 선택** 옵션을 선택하고 새로 만든 저장소를 선택합니다. 저장을 클릭합니다.

   ![저장소를 공개로 설정](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > IP 필터링과 함께 GitHub Enterprise를 사용하는 경우 허용 목록에 IP 3.227.118.73을 추가할 수 있습니다.

   축하합니다! `https://<branch>--<repo>--<owner>.hlx.page/`에서 새 웹 사이트가 실행되고 있습니다.

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.

   예를 들어 분기 이름이 `main`이고 저장소가 `wefinance`이며 소유자가 `wkndforms`인 경우 웹 사이트는 [https://main--wefinance--wkndforms.hlx.page/](https://main--wefinance--wkndforms.hlx.page/)에서 실행됩니다.



### 자체 콘텐츠 소스 연결

새로 만든 GitHub 저장소는 [Google Drive 폴더에 저장된 예시 콘텐츠](https://drive.google.com/drive/folders/1bvjfi6TqpYA7DvbX6kKc-m7FgHuJ4RUQ)를 가리킵니다. 이 읽기 전용 콘텐츠는 양식을 위한 훌륭한 시작점에 해당합니다. 자유롭게 사용자의 Google Drive에 복사하고 필요에 맞게 사용자 정의할 수 있습니다.

![Google Drive의 샘플 콘텐츠](/help/edge/assets/folder-with-sample-content.png)

샘플 콘텐츠를 자체 콘텐츠 폴더에 복사하고 GitHub 저장소를 자체 콘텐츠 폴더로 지정하는 방법은 다음과 같습니다.

1. Google Drive 또는 Microsoft SharePoint에서 AEM 콘텐츠를 위한 전용 폴더를 새로 만듭니다. 이 문서에서는 Microsoft SharePoint에서 만든 폴더를 사용합니다.

1. Adobe Experience Manager 사용자(helix@adobe.com)와 폴더를 공유합니다.

   ![액세스 관리 옵션을 사용하여 AEM 사용자와 폴더 공유 - SharePoint](/help/edge/assets/share-folder-with-aem-user.png)

   ![액세스 관리 옵션을 사용하여 AEM 사용자와 폴더 공유 - Google Drive](/help/edge/assets/share-google-drive-folder.png)


   Adobe Experience Manager 사용자에게 폴더에 대한 편집 권한을 제공해야 합니다.

   ![AEM 사용자와 폴더를 공유하고 편집 권한 제공 -SharePoint](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png)

   ![AEM 사용자와 폴더를 공유하고 편집 권한 제공 - Google Drive](/help/edge/assets/add-aem-user-google-folder.png)

1. [Google Drive 폴더에 저장된 예시 콘텐츠](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_)를 폴더에 복사합니다. 복사하는 방법은 다음과 같습니다.

   1. 파일을 함께 다운로드하거나 개별 파일을 다운로드합니다.

      ![샘플 콘텐츠 다운로드](/help/edge/assets/download-sample-content.png)

      `nav` 및 `footer` 파일은 페이지의 기본 레이아웃을 정의하며 프로젝트 전체에서 거의 변경되지 않습니다. 또한 대부분의 다른 콘텐츠 파일과 다른 특정한 구조를 하고 있습니다. 이러한 파일을 검토하면 AEM 프로젝트에서 콘텐츠가 어떻게 구성되어 있는지 파악할 수 있습니다.


   1. 이 파일을 Microsoft SharePoint 또는 Google 드라이브 폴더에 업로드합니다.

      ![Google Drive의 샘플 콘텐츠](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      샘플 콘텐츠의 `enquiry` 시트를 Google Drive 또는 Microsoft SharePoint의 폴더로 복사해야 합니다. 여기에 샘플 양식의 구조가 포함되어 있습니다.

1. 이제 콘텐츠 폴더를 설정했으므로 앞서 AEM Forms 상용구를 사용하여 만든 GitHub의 프로젝트에 이를 연결할 차례입니다. 연결하는 방법은 다음과 같습니다.

   1. 앞서 AEM Forms 상용구를 사용하여 만든 GitHub 저장소로 이동합니다.
   1. 편집할 `fstab.yaml`을 엽니다.
   1. 기존 참조를 AEM 사용자(helix@adobe.com)와 공유한 폴더 경로로 바꿉니다.

      ![Google Drive의 샘플 콘텐츠](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Microsoft SharePoint를 사용하는 경우 폴더 경로는 다음 형식을 사용합니다.

      ```HTML
      https://<tenant>.SharePoint.com/sites/<sp-site>/Shared%20Documents/<folder-name>
      ```

      예:

      ```HTML
      https://adobe.SharePoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Microsoft SharePoint에서의 파일 관리에 대한 자세한 내용은 [Adobe SharePoint 사용 방법](https://www.aem.live/docs/setup-customer-sharepoint)을 확인하십시오.


   1. 참조를 업데이트했고 모든 항목에 문제가 없으면 업데이트된 `fsatb.yaml` 파일을 커밋합니다. 빌드 문제가 발생하면 [GitHub 빌드 문제 해결](#troubleshooting-github-build-issues)을 참조하십시오.



      ![업데이트된 fsatab.yaml 파일 커밋](/help/edge/assets/commit-updated-fstab-yaml.png)

      그러면 콘텐츠 폴더가 웹 사이트에 연결됩니다. 참조를 업데이트한 후 처음에는 “404 Not Found” 오류가 발생할 수 있습니다. 이는 콘텐츠의 미리보기를 아직 완료하지 않았기 때문입니다. 다음 섹션에서는 콘텐츠 작성 및 미리보기를 시작하는 방법을 설명합니다.



### 콘텐츠 미리보기 및 게시

마지막 단계를 완료하고 나면 새 콘텐츠 소스는 비어 있지 않지만 미리보기 또는 라이브 단계로 승격되기 전까지 웹 사이트에 표시되지 않습니다. 현재 이로 인해 404 오류가 발생할 수 있습니다.

게시되지 않은 콘텐츠를 미리 보는 방법은 다음과 같습니다.

1. [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo)이라는 Chrome 확장 기능을 설치합니다.

   ![AEM SideKick 설치](/help/edge/assets/install-aem-sidekick.png)

   Chrome에 확장 기능을 설치한 후 고정하는 것을 잊지 마십시오. 이렇게 하면 쉽게 찾을 수 있습니다.

   ![AEM Sidekick 고정](/help/edge/assets/pin-aem-sidekick.png)

1. Sidekick Chrome 확장 기능을 설정하려면 이전에 공유한 Google Drive 또는 Microsoft SharePoint 폴더로 이동하여 브라우저 도구 모음에서 확장 기능 아이콘을 마우스 오른쪽 버튼으로 클릭하고 `Add this project`를 선택합니다.

   ![AEM Sidekick - 프로젝트 추가](/help/edge/assets/aem-sidekick-add-a-project.png)

   확장 기능이 설치되고 프로젝트가 추가되면 Google Drive에서 콘텐츠를 미리 보고 게시할 수 있습니다.

1. Microsoft SharePoint 또는 Google Drive 폴더에 있는 모든 문서를 선택합니다. Ctrl 키(Windows/Linux) 또는 Cmd 키(Mac)를 누른 상태에서 클릭하면 여러 문서를 선택할 수 있습니다.

   ![모든 파일 선택](/help/edge/assets/select-all-files.png)

1. Chrome 확장 기능 막대에 고정된 AEM Sidekick 아이콘을 클릭합니다. 화면에 도구 모음이 나타납니다. 콘텐츠를 미리 보거나 게시할 수 있습니다.

   `index`, `nav`, `footer` 및 `enquiry` 파일을 복사한 경우, 모두 자체 미리보기 및 게시 주기가 있는 별도의 문서이므로 모두 미리 보고 게시해야 합니다.

   파일을 미리 보고 나면 새 브라우저 탭에 문서가 표시됩니다. 샘플 양식을 미리 보려면 다음 URL로 이동합니다.


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.live
   ```

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.


   `https://<branch>--<repo>--<owner>.hlx.page/enquiry` URL.

   예를 들어 프로젝트 저장소의 이름이 “wefinance”이고 “wkndforms” 계정 아래에서 “main” 분기를 사용하는 경우 URL은 다음과 같습니다.

   [https://main--wefinance--wkndforms.hlx.page](https://main--wefinance--wkndforms.hlx.page)

### 양식 만들기

샘플 콘텐츠에는 “enquiry” 양식의 템플릿 역할을 하는 “enquiry” 시트가 포함되어 있습니다. 시트의 각 행은 [양식 필드](/help/edge/docs/forms/form-components.md#available-components)를 나타내며, 열 헤더는 [필드 속성](/help/edge/docs/forms/form-components.md#available-components)을 정의합니다. 이 샘플 양식을 사용하면 양식 작성을 시작하는 데 도움이 됩니다.

![문의 양식](/help/edge/docs/forms/assets/enquiry-form-microsoft-sharepoint.png)

필드 레이블 업데이트부터 시작해 보겠습니다. 편집을 위해 ‘enquiry’ 시트를 열고 제출 버튼 레이블을 `Let's Chat`으로 변경한 다음 AEM Sidekick을 사용하여 파일을 미리 보고 게시합니다.

![문의 양식](/help/edge/assets/enquiry-form-preview-publish.png)

파일을 미리 보거나 게시하면 파일의 JSON 버전이 새 탭에 나타납니다. 파일의 미리보기(.hlx.page) 또는 게시(.hlx.live) URL을 복사합니다.

![양식 스프레드시트의 JSON](/help/edge/assets//preview-and-publish-enquiry-form.png)

`enquiry` 파일을 열고 양식 블록의 URL을 이전 단계에서 복사한 파일의 URL로 바꿉니다. URL은 하이퍼링크여야 합니다.

![스프레드시트 URL의 .json URL이 포함된 문의 파일](/help/edge/assets/enquiry-doc-to-embed-form.png)

AEM Sidekick을 사용하여 문의 문서를 미리 보고 게시합니다.

![스프레드시트 URL의 .json URL이 포함된 문의 파일](/help/edge/assets/preview-and-publish-enquiry-document.png)


업데이트된 문의 양식을 미리 보려면 다음 URL로 이동합니다.


```HTML
    https://<branch>--<repository>--<owner>.hlx.page/enquiry
       
```

제출 버튼의 레이블이 `Let's Chat`으로 업데이트됩니다.

![문의 양식](/help/edge/assets/updated-form.png)

새 양식 만들기 및 게시에 대한 자세한 내용은 [양식 만들기](/help/edge/docs/forms/create-forms.md) 안내서를 참조하십시오.

### 스타일 및 기능 개발 시작


즉시 로컬 AEM 개발 환경을 시작하고 실행하려면 다음을 수행하십시오.

1. AEM CLI 설치: AEM CLI는 개발 작업을 단순화합니다. npm을 사용하여 전역적으로 설치해 보겠습니다.

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. GitHub 프로젝트 복제: 다음 명령을 사용하여 GitHub에서 프로젝트 저장소를 복제합니다. 이때 <owner> 저장소 소유자와 <repo> 저장소 이름은 바꿉니다.

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. 로컬 환경 시작: 프로젝트 디렉터리로 이동하고 다음 단일 명령으로 로컬 AEM 인스턴스를 실행합니다.

   ```
   cd <repo>
   aem up
   ```

적응형 양식 블록 `blocks/form` 폴더는 양식 스타일을 지정하고 코드를 작성할 수 있는 놀이터와도 같습니다. 이 디렉터리 내의 모든 `.css` 또는 `.js` 파일을 편집하면 변경 사항이 브라우저에 즉시 반영되는 것을 볼 수 있습니다.

작성 콘텐츠를 선보일 준비가 되셨습니까? Git을 사용하여 변경 사항을 커밋하고 푸시합니다. 이렇게 하면 다음 URL에서 액세스할 수 있는 미리보기 및 프로덕션 환경이 업데이트됩니다(플레이스홀더를 프로젝트 세부 정보로 교체).

미리보기: `https://<branch>--<repo>--<owner>.hlx.page/`
프로덕션: `https://<branch>--<repo>--<owner>.hlx.live/`

축하합니다! 로컬 개발 환경을 성공적으로 설정하고 변경 사항을 배포했습니다.



## 기존 AEM 프로젝트에 적응형 양식 블록 추가


>[!VIDEO](https://video.tv.adobe.com/v/3427789)

기존 AEM 프로젝트가 있는 경우 적응형 양식 블록을 현재 프로젝트에 통합하여 양식 만들기를 시작할 수 있습니다.

>[!NOTE]
>
>
> 이 단계는 [AEM 상용구](https://github.com/adobe/aem-boilerplate)를 사용하여 빌드한 프로젝트에 적용됩니다. [AEM Forms 상용구](https://github.com/adobe-rnd/aem-boilerplate-forms)를 사용하여 AEM 프로젝트를 만든 경우 이 단계를 건너뛸 수 있습니다.

통합하는 방법은 다음과 같습니다.

1. 적응형 양식 블록 저장소 [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)를 컴퓨터에 복제합니다.

1. 다운로드한 폴더 내에서 `blocks/form` 폴더를 찾습니다. 이 폴더를 복사합니다. 이제 AEM 프로젝트의 로컬 `blocks` 폴더로 이동하여 복사한 양식 폴더를 여기에 붙여넣습니다.

1. GitHub의 AEM 프로젝트에 이러한 변경 사항을 커밋하고 푸시합니다.


이번 단계가 끝났습니다! 적응형 양식 블록은 이제 AEM 프로젝트의 일부입니다. AEM 페이지에 양식을 만들고 추가할 수 있습니다.


## GitHub 빌드 문제 해결

잠재적인 문제를 해결하면 GitHub 빌드 프로세스를 원활하게 할 수 있습니다.

* **모듈 경로 오류 해결:**
“모듈 “../../scripts/lib-franklin.js”에 대한 경로를 확인할 수 없음” 오류가 발생하는 경우 [EDS Project]/blocks/forms/form.js 파일로 이동합니다. lib-franklin.js 파일을 aem.js 파일로 바꿔 import 문을 업데이트합니다.

* **린팅 오류 처리**:
린팅 오류가 발생하는 경우 우회할 수 있습니다. [EDS Project]/package.json 파일을 열고 “lint” 스크립트를 `"lint": "npm run lint:js && npm run lint:css"`에서 `"lint": "echo 'skipping linting for now'"`로 수정합니다. 파일을 저장하고 변경 사항을 GitHub 프로젝트에 커밋합니다.


## 추가 참조

{{see-more-forms-eds}}
