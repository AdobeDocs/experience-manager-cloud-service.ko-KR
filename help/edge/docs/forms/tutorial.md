---
title: AEM Forms Edge Delivery Services 시작하기 - 개발자 자습서
description: 이 튜토리얼은 새로운 AEM(Adobe Experience Manager Forms) 프로젝트를 시작하고 실행하는 데 도움이 됩니다. 10분에서 20분 안에 나만의 양식을 만들 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 2aa70e78764616f41fe64e324c017873cfba1d5b
workflow-type: tm+mt
source-wordcount: '1770'
ht-degree: 12%

---


# 시작하기 - 개발자 튜토리얼

오늘날의 디지털 시대에는 사용자 친화적인 양식을 만드는 것이 모든 조직에 필수적입니다. AEM Forms Edge Delivery Services(EDS)를 사용하면 Google 문서 및 Microsoft Office와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다.

이러한 양식은 데이터를 Microsoft Excel 또는 Google Sheets 파일에 직접 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft Sharepoint의 활발한 에코시스템과 강력한 API를 사용하여 쉽게 제출 데이터를 처리하거나 기존 비즈니스 워크플로를 시작할 수 있습니다.

AEM Forms은 캡처된 데이터를 캡처하고 저장할 양식을 쉽게 생성할 수 있도록 적응형 Forms 블록이라고 하는 블록을 제공합니다. 적응형 Forms 블록이 사전 장착된 새 AEM 프로젝트를 생성하거나 적응형 Forms 블록을 기존 AEM 프로젝트에 추가할 수 있습니다.

이 AEM Forms 자습서에서는 새 Adobe Experience Manager(AEM) Forms 프로젝트를 사용하여 사용자 정의 양식을 만들고, 미리 보고, 게시하는 과정을 안내합니다. 기존 AEM 프로젝트에 적응형 Forms 블록을 추가하는 방법도 배우게 됩니다.

* **[적응형 Forms 블록이 사전 장착된 새 AEM 프로젝트 만들기](#create-a-new-eds-project-pre-equipped-with-adaptive-forms-block)**
* **[기존 AEM 프로젝트에 적응형 Forms 블록 추가](#add-adaptive-forms-block-to-an-existing-eds-project)**



## 사전 요구 사항

* GitHub 계정이 있으며 Git 기본 사항을 이해합니다.
* Google 또는 Microsoft SharePoint 계정이 있습니다.
* HTML, CSS 및 JavaScript의 기본 사항을 이해합니다.
* 로컬 개발을 위해 Node/npm이 설치되어 있습니다.

**앞장 서!** 이 자습서에서는 macOS, Chrome 및 Visual Studio 코드를 사용합니다. 다른 설정에 맞게 단계를 조정할 수 있지만 스크린샷 및 특정 UI 요소는 선택한 운영 체제, 브라우저 및 코드 편집기에 따라 다를 수 있습니다.


## 적응형 Forms 블록이 사전 장착된 새 AEM 프로젝트 만들기

AEM Forms Boilerplate 템플릿을 사용하면 적응형 Forms 블록으로 사전 구성된 AEM 프로젝트를 빠르게 시작할 수 있습니다. AEM 모범 사례를 따르고 양식을 바로 빌드하는 가장 빠르고 쉬운 방법입니다.

### AEM Forms 보일러플레이트 저장소 템플릿 시작

1. AEM 프로젝트용 Github 저장소를 만듭니다. 저장소를 생성하려면:
   1. 다음으로 이동 [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms Boilerplate](/help/edge/assets/aem-forms-boilerplate.png)
   1. 다음을 클릭합니다. **이 템플릿 사용** 옵션을 선택하고 **새 저장소 만들기** 옵션을 선택합니다. 새 저장소 만들기 화면이 열립니다.

      ![AEM Forms Boilerplate를 사용하여 새 저장소 만들기](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. 새 저장소 만들기 화면에서 **소유자**, 및 지정 **저장소 이름** . Adobe은 저장소를 로 설정할 것을 권장합니다. **공용**. 따라서 **공용** 옵션 및 클릭 **저장소 만들기**.

   ![저장소를 공개로 설정](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. 저장소에 AEM 코드 동기화 GitHub 앱을 설치합니다. 설치하려면:
   1. 다음으로 이동 [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. AEM 코드 동기화 설치 화면에서 다음을 선택합니다. **저장소만 선택** 옵션을 선택하고 새로 만든 저장소를 선택합니다. 저장을 클릭합니다.

   ![저장소를 공개로 설정](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > IP 필터링과 함께 Github Enterprise를 사용하는 경우 허용 목록에 다음 IP를 추가할 수 있습니다. 3.227.118.73

   축하합니다! 새 웹 사이트가 실행 중입니다. `https://<branch>--<repo>--<owner>.hlx.page/`.

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.

   예를 들어 분기 이름이 인 경우 `main`, 리포지토리: `wefinance`, 그리고 소유자는 `wkndforms`, 웹 사이트 실행 위치: [https://main--wefinance--wkndforms.hlx.page/](https://main--wefinance--wkndforms.hlx.page/).



### 고유한 콘텐츠 소스 연결

새로 만든 Github 저장소는 다음을 가리킵니다 [Google 드라이브 폴더에 저장된 컨텐츠 예](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_). 이 읽기 전용 콘텐츠는 양식에 좋은 시작점을 제공합니다. 자유롭게 자신의 Google 드라이브에 복사하고 필요에 맞게 사용자 지정할 수 있습니다.

![Google 드라이브의 샘플 컨텐츠](/help/edge/assets/folder-with-sample-content.png)

샘플 콘텐츠를 자신의 콘텐츠 폴더로 복사하고 Github 저장소를 자신의 콘텐츠 폴더로 지정하려면 다음을 수행하십시오.

1. Google 드라이브 또는 Microsoft SharePoint에서 AEM 콘텐츠에만 해당하는 새 폴더를 만듭니다. 이 문서에서는 Microsoft SharePoint에서 만든 폴더를 사용합니다.

1. Adobe Experience Manager 사용자(helix@adobe.com)와 폴더를 공유합니다.

   ![액세스 관리 옵션을 사용하여 AEM 사용자와 폴더 공유 - SharePoint](/help/edge/assets/share-folder-with-aem-user.png)

   ![액세스 관리 옵션을 사용하여 AEM 사용자 - Google 드라이브와 폴더 공유](/help/edge/assets/share-google-drive-folder.png)


   Adobe Experience Manager 사용자에게 폴더에 대한 편집 권한을 제공했는지 확인합니다.

   ![AEM 사용자와 폴더 공유, 편집 권한 제공-SharePoint](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png)

   ![AEM 사용자와 폴더 공유, 편집 권한 제공 - Google 드라이브](/help/edge/assets/add-aem-user-google-folder.png)

1. 다음을 복사합니다. [Google 드라이브 폴더에 저장된 컨텐츠 예](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_) 폴더로 이동합니다. 복사하려면:

   1. 파일을 함께 다운로드하거나 개별 파일을 다운로드합니다.

      ![샘플 콘텐츠 다운로드](/help/edge/assets/download-sample-content.png)

      다음 `index`, `nav`, 및 `footer` 파일은 페이지의 기본 레이아웃을 정의하며 프로젝트 전체에서 거의 변경되지 않습니다. 또한 대부분의 다른 콘텐츠 파일과 다른 특정 구조를 가지고 있습니다. 이러한 파일을 검사하면 AEM 프로젝트에서 콘텐츠가 구성되는 방식을 파악할 수 있습니다.


   1. 이 파일을 Microsoft SharePoint 또는 Google 드라이브 폴더에 업로드합니다.

      ![Google 드라이브의 샘플 컨텐츠](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      다음을 복사했는지 확인합니다.  `enquiry` 샘플 콘텐츠에서 Google 드라이브 또는 Microsoft SharePoint의 폴더로 시트합니다. 여기에는 샘플 양식에 대한 구조가 포함되어 있습니다.

1. 이제 콘텐츠 폴더를 설정했으므로 이전에 AEM Forms Boilerplate을 사용하여 만든 GitHub의 프로젝트에 연결해야 합니다. 연결하려면:

   1. AEM Forms Boilerplate을 사용하여 이전에 만든 GitHub 저장소로 이동합니다.
   1. 를 엽니다. `fstab.yaml` 편집할 수 있습니다.
   1. 기존 참조를 AEM 사용자와 공유한 폴더 경로(helix@adobe.com)로 바꿉니다.

      ![Google 드라이브의 샘플 컨텐츠](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Microsoft SharePoint을 사용하는 경우 폴더 경로는 다음 형식을 사용합니다.

      ```HTML
      https://<tenant>.sharepoint.com/sites/  <sp-site>/Shared%20Documents/<folder-name>
      ```

      예:

      ```HTML
      https://adobe.sharepoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Microsoft SharePoint 내에서 를 사용하여 파일을 관리하는 방법에 대한 자세한 내용은 [Adobe Sharepoint 사용 방법](https://www.aem.live/docs/setup-customer-sharepoint).



   1. 업데이트된 항목 커밋 `fsatb.yaml` 파일, 참조를 업데이트하면 모든 것이 정상입니다. 빌드 문제가 발생하는 경우 다음을 참조하십시오. [GitHub 빌드 문제 해결](#troubleshooting-github-build-issues).



      ![업데이트된 fsatab.yaml 파일 커밋](/help/edge/assets/commit-updated-fstab-yaml.png)

      이렇게 하면 콘텐츠 폴더가 웹 사이트에 연결됩니다. 참조를 업데이트하면 처음에 &quot;404 찾을 수 없음&quot; 오류가 발생할 수 있습니다. 이는 콘텐츠가 아직 미리보기되지 않았기 때문입니다. 다음 섹션에서는 콘텐츠 작성 및 미리보기를 시작하는 방법을 설명합니다.

      ![업데이트된 fsatab.yaml 파일 커밋](/help/edge/assets/aem-forms-project-folder-error.png)

### 콘텐츠 미리보기 및 게시

마지막 단계를 완료한 후 새 콘텐츠 소스는 비어 있지 않지만 미리보기 또는 라이브 단계로 승격될 때까지 웹 사이트에 표시되지 않습니다. 현재 이로 인해 404 오류가 발생할 수 있습니다.

게시되지 않은 콘텐츠를 미리 보려면 다음과 같이 하십시오.

1. 라는 Chrome 확장 프로그램 설치 [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![설치 AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

   Chrome에 확장 프로그램을 설치한 후 잊지 말고 고정하십시오. 이렇게 하면 쉽게 찾을 수 있습니다.

   ![핀 AEM Sidekick](/help/edge/assets/pin-aem-sidekick.png)

1. Sidekick Chrome 확장을 설정하려면 이전에 공유한 Google Drive 또는 Microsoft SharePoint 폴더로 이동한 다음 브라우저 도구 모음에서 확장 아이콘을 마우스 오른쪽 단추로 클릭하고 를 선택합니다 `Add this project`.

   ![AEM Sidekick - 프로젝트 추가](/help/edge/assets/aem-sidekick-add-a-project.png)

   확장이 설치되고 프로젝트가 추가되면 바로 Google 드라이브에서 콘텐츠를 미리 보고 게시할 준비가 된 것입니다.

1. Microsoft SharePoint 또는 Google Drive 폴더의 모든 문서를 선택합니다. Ctrl 키(Windows/Linux) 또는 Cmd 키(Mac)를 누른 채로 을 클릭하여 여러 문서를 선택할 수 있습니다.

   ![모든 파일 선택](/help/edge/assets/select-all-files.png)

1. Chrome 확장 프로그램 모음에 고정된 AEM Sidekick 아이콘을 클릭합니다. 화면에 도구 모음이 표시됩니다. 콘텐츠를 미리 보거나 게시하도록 선택할 수 있습니다.

   복사한 경우 `index`, `nav`, `footer` 및 `enquiry` 파일, 이 모든 문서는 자체 미리보기 및 게시 주기가 있는 별도의 문서이므로 모든 문서를 미리보기(및 게시)해야 합니다.

   파일을 미리 보면 새 브라우저 탭에 문서가 표시됩니다. 샘플 양식을 미리 보려면 다음 URL로 이동하십시오.


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.live
   ```

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.


   `https://<branch>--<repo>--<owner>.hlx.page/enquiry` URL.

   예를 들어 프로젝트의 저장소 이름이 &quot;wefinance&quot;이고 계정 소유자 &quot;wkndforms&quot; 아래에 있으며 &quot;main&quot; 분기를 사용하는 경우 URL은 다음과 같습니다.



   [https://main--wefinance--wkndforms.hlx.page](https://main--wefinance--wkndforms.hlx.page).

### 양식 업데이트

1. Microsoft SharePoint 또는 Google 드라이브 폴더로 이동합니다.

1. 를 엽니다. `enquiry.xlsx` 편집할 수 있습니다.

   ![문의 양식](/help/edge/assets/enquiry-form-microsoft-sharepoint.png)

1. 제출 단추의 레이블을 다음으로 변경 `Let's Chat`.

   ![문의 양식](/help/edge/assets/enquiry-form-microsoft-sharepoint.png)

1. AEM Sidekick을 사용하여 미리보기 및 게시 `enquiry.xlsx` 파일.

   ![문의 양식](/help/edge/assets/enquiry-form-preview-publish.png)

1. 조회 양식을 미리 보려면 다음 URL로 이동하십시오.


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.page/enquiry
   ```

   제출 단추의 레이블이 업데이트됩니다. 이제 양식을 작성하고 제출 단추를 클릭하면 스프레드시트가 유효하지 않기 때문에 다음과 유사한 오류가 발생합니다 [아직 데이터를 수락하도록 설정](/help/edge/docs/forms/submit-forms.md).


### 스타일 및 기능 개발 시작


로컬 AEM 개발 환경을 즉시 설치하고 실행하려면 다음 작업을 수행하십시오.

1. AEM CLI 설치: AEM CLI는 개발 작업을 단순화합니다. npm을 사용하여 전체적으로 설치하겠습니다.

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Github 프로젝트 복제: 다음 명령을 사용하여 GitHub에서 프로젝트 저장소를 복제하고 바꾸기 <owner> 저장소 소유자 및 <repo> 저장소 이름:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. 로컬 환경 시작: 프로젝트 디렉토리로 이동하고 단일 명령으로 로컬 AEM 인스턴스를 실행합니다.

   ```
   cd <repo>
   aem up
   ```

적응형 Forms 블록 `blocks/form` 폴더는 양식의 스타일 및 코드를 위한 플레이그라운드입니다! 모두 편집 `.css` 또는 `.js` 이 디렉토리에 있는 파일을 사용하면 변경 사항이 즉시 브라우저에 반영됩니다.

작품을 선보일 준비가 되셨습니까? Git을 사용하여 변경 사항을 커밋하고 푸시합니다. 이렇게 하면 다음 URL에서 액세스할 수 있는 미리보기 및 프로덕션 환경이 업데이트됩니다(자리 표시자를 프로젝트 세부 정보로 대체).

미리 보기: `https://<branch>--<repo>--<owner>.hlx.page/`
프로덕션: `https://<branch>--<repo>--<owner>.hlx.live/`
축하합니다! 로컬 개발 환경을 설정하고 변경 사항을 배포했습니다.



## 기존 AEM 프로젝트에 적응형 Forms 블록 추가


>[!VIDEO](https://video.tv.adobe.com/v/3427789)

기존 AEM 프로젝트가 있는 경우 적응형 Forms 블록을 현재 프로젝트에 통합하여 양식 만들기를 시작할 수 있습니다. 통합하려면:

1. 적응형 Forms 블록 저장소 https://github.com/adobe-rnd/aem-boilerplate-forms 를 컴퓨터에 복제합니다.

1. 다운로드한 폴더 내에서 `blocks/form` 폴더를 삭제합니다. 이 폴더를 복사합니다. 이제 AEM 프로젝트의 로컬로 이동합니다. `blocks` 폴더를 복사한 양식 폴더를 여기에 붙여 넣습니다.

1. GitHub의 AEM 프로젝트에 이러한 변경 사항을 커밋하고 푸시합니다.


이번 단계가 끝났습니다! 적응형 Forms 블록은 이제 AEM 프로젝트의 일부입니다. AEM 페이지에 양식을 만들고 추가할 수 있습니다.


## GitHub 빌드 문제 해결

잠재적인 문제를 해결하면 GitHub 빌드 프로세스를 원활하게 할 수 있습니다.

* **모듈 경로 오류 해결:**
“모듈 “../../scripts/lib-franklin.js”에 대한 경로를 확인할 수 없음” 오류가 발생하는 경우 [EDS Project]/blocks/forms/form.js 파일로 이동합니다. lib-franklin.js 파일을 aem.js 파일로 바꿔 import 문을 업데이트합니다.

* **린팅 오류 처리**:
린팅 오류가 발생하는 경우 우회할 수 있습니다. [EDS Project]/package.json 파일을 연 다음 &quot;lint&quot; 스크립트를 &quot;lint&quot;: &quot;npm run lint:js &amp;&amp; npm run lint:css&quot;에서 “lint“: &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;&quot;로 수정합니다. 파일을 저장하고 변경 사항을 GitHub 프로젝트에 커밋합니다.


## 참고 항목

* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [양식을 Microsoft Excel 또는 Google Sheets에 직접 제출](/help/edge/docs/forms/submit-forms.md)
* [양식 보기 변경](/help/edge/docs/forms/style-theme-forms.md)






