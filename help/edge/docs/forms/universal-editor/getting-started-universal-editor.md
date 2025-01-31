---
title: 범용 편집기에서 AEM Forms Edge Delivery Services 시작하기 - 개발자 자습서
description: 이 튜토리얼에서는 새로운 AEM(Adobe Experience Manager Forms) 프로젝트를 시작하고 실행하는 방법을 안내합니다. 10~20분 내에 범용 편집기에서 고유한 Edge Delivery Services Forms을 만듭니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 23%

---


# 범용 편집기를 사용한 AEM Forms Edge Delivery Services 시작하기 (WYSIWYG)

오늘날 디지털 시대에는 사용자 친화적인 양식이 모든 조직에 필수적입니다. Edge Delivery Services Forms은 WYSIWYG(보이는 것) 기능을 제공하는 범용 편집기를 사용하여 만들어집니다. 효율적인 양식 작성을 위한 현대적이고 직관적인 인터페이스를 제공합니다.

AEM Forms은 데이터를 캡처하고 저장할 Edge Delivery Services Forms을 쉽게 만들 수 있도록 적응형 Forms 블록이라고 하는 블록을 제공합니다. [적응형 Forms 블록으로 사전 구성된 새 AEM 프로젝트를 만들거나](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [적응형 Forms 블록을 기존 AEM 프로젝트에 추가](#add-adaptive-forms-block-to-your-existing-aem-project)할 수 있습니다.

이 튜토리얼에서는 유니버설 편집기의 WYSIWYG 작성을 사용하여 새 Adobe Experience Manager 사이트 프로젝트 또는 기존 사이트 프로젝트를 사용하여 양식을 만들고, 미리 보고, 게시하는 과정을 안내합니다.


## 사전 요구 사항

* GitHub 계정이 있고 Git 기본 사항을 이해하고 있습니다.
* Google 또는 Microsoft SharePoint 계정이 있습니다.
* HTML, CSS 및 JavaScript의 기본 사항을 이해합니다.
* 로컬 개발을 위해 Node/npm이 설치되어 있습니다.

## 적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트 만들기

AEM Forms 상용구 템플릿을 사용하면 적응형 양식 블록으로 사전 구성된 AEM 프로젝트를 빠르게 시작할 수 있습니다. AEM 모범 사례를 따르고 양식을 바로 빌드하는 가장 빠르고 쉬운 방법입니다.

### AEM Forms 상용구 저장소 템플릿 시작하기

1. AEM 프로젝트의 GitHub 저장소를 만듭니다. 저장소를 만드는 방법은 다음과 같습니다.
   1. [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)로 이동합니다.

      ![AEM Forms 상용구](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. **이 템플릿 사용** 옵션을 클릭하고 **새 저장소 만들기** 옵션을 선택합니다.

      ![AEM Forms 상용구를 사용하여 새 저장소 만들기](/help/edge/docs/forms/assets/use-eds-form-template.png)

      **새 저장소 만들기** 화면이 열립니다.

   1. **새 저장소 만들기** 화면에서 **소유자**&#x200B;를 선택하고 **저장소 이름** 을 지정하십시오. Adobe은 저장소를 **공개**(으)로 설정할 것을 권장합니다. 따라서 **공개** 옵션을 선택하고 **저장소 만들기**&#x200B;를 클릭합니다.

      ![저장소를 공개로 설정](/help/edge/docs/forms/assets/name-eds-repo.png)

1. 저장소에 AEM Code Sync GitHub 앱을 설치합니다. 설치하는 방법은 다음과 같습니다.
   1. [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)로 이동합니다.
   1. **AEM 코드 동기화 설치** 화면에서 **저장소만 선택** 옵션을 선택하고 새로 만든 저장소를 선택합니다. **저장**&#x200B;을 클릭합니다.

   ![저장소를 공개로 설정](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. 이제 AEM Forms Boilerplate을 사용하여 만든 GitHub 저장소를 AEM 프로젝트 작성 환경에 연결합니다. 연결하는 방법은 다음과 같습니다.

   1. 앞서 AEM Forms 상용구를 사용하여 만든 GitHub 저장소로 이동합니다.
   1. 편집할 **fstab.yaml** 파일을 엽니다.

      ![fstab.yaml 파일 열기](/help/edge/docs/forms/assets/open-fstab.png)

   1. **fstab.yaml** 파일을 편집하여 프로젝트의 탑재 지점을 업데이트합니다. URL을 AEM as a Cloud Service 작성 인스턴스의 URL로 바꿉니다.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![fstab.yaml 파일 편집](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. 참조를 업데이트하고 모든 것이 정상이면 업데이트된 **fstab.yaml** 파일을 커밋하십시오.

      ![변경 내용 커밋](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      빌드 문제가 발생하면 [GitHub 빌드 문제 해결](#troubleshooting-github-build-issues)을 참조하십시오.

### 새 AEM 프로젝트 만들기

이제 GitHub 프로젝트가 있으므로 AEM as a Cloud Service 작성 인스턴스에서 새 AEM 프로젝트를 만들고 게시할 수 있습니다.
1. 새 AEM 프로젝트를 만들려면 다음 작업을 수행하십시오.

   1. AEM as a Cloud Service 제작 인스턴스에 로그인하고 **사이트**&#x200B;를 선택합니다.

      ![사이트 선택](/help/edge/assets/select-sites.png)

   1. **만들기** > **템플릿의 사이트**&#x200B;를 클릭합니다.

      ![사이트 만들기](/help/edge/docs/forms/assets/create-sites.png)

   1. Edge Delivery Services 사이트 템플릿을 선택하고 **다음**&#x200B;을(를) 클릭합니다.

      ![사이트 템플릿 선택](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * 작성 인스턴스에서 Edge Delivery Services 사이트 템플릿을 사용할 수 없는 경우 가져오기 단추를 클릭하여 템플릿을 업로드합니다.
      > * [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)에서 Edge Delivery Services 사이트 템플릿을 다운로드할 수 있습니다.

   1. 새 AEM 프로젝트를 생성하려면 다음 세부 정보를 입력하십시오.
      * **사이트 제목** - 사이트를 설명하는 제목을 추가합니다.
      * **사이트 제목** - 이전 단계에서 정의한 `site-name`을(를) 사용합니다.
      * **GitHub URL** - 이전 단계에서 생성한 GitHub 프로젝트의 URL을 사용합니다.

      ![AEM 사이트 만들기](/help/edge/docs/forms/assets/create-aem-site.png)

   1. **사이트 만들기** 대화 상자가 나타나면 **확인**&#x200B;을 클릭합니다.

      ![확인 클릭](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      몇 분 안에 새 AEM 프로젝트가 만들어집니다.

   1. 사이트 콘솔에서 새로 만든 AEM 프로젝트로 이동한 다음 **편집**을 클릭합니다.
이 경우 `index.html` 페이지가 일러스트레이션에 사용됩니다.

      ![AEM 사이트 편집](/help/edge/docs/forms/assets/edit-site.png)

      AEM 프로젝트가 유니버설 편집기에서 새 탭으로 열리고 WYSIWYG 작성이 활성화됩니다. 이제 AEM 프로젝트를 편집할 수 있습니다.

      ![유니버설 편집기에서 사이트 열기](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. 생성된 AEM 프로젝트 Publish

   AEM 프로젝트 편집이 완료되면 게시합니다. 게시하려면:

   1. 사이트 콘솔에서 모든 AEM 프로젝트 페이지를 선택하고 **빠른 Publish**&#x200B;을 클릭합니다.

      ![AEM Sites 프로젝트 게시](/help/edge/docs/forms/assets/publish-sites.png)

   1. **빠른 Publish** 확인 대화 상자가 나타나면 **Publish**&#x200B;을 클릭하여 게시 프로세스를 시작합니다.

      ![빠른 Publish 확인 대화 상자](/help/edge/docs/forms/assets/quick-publish.png)

      또는 범용 편집기 사용자 인터페이스에서 직접 AEM Project 페이지를 게시할 수 있습니다.

      ![빠른 Publish 확인 대화 상자](/help/edge/docs/forms/assets/qui.png)

   축하합니다! `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`에서 새 웹 사이트가 실행되고 있습니다.

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.
   * `<site-name>`은(는) 만든 사이트 이름의 이름을 나타냅니다.

   예를 들어 분기 이름이 `main`이고 저장소가 `edsforms`이고 소유자는 `wkndforms`이며 `site-name`이(가) `eds-forms`인 경우 웹 사이트가 `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`에 실행되고 실행됩니다

   >[!NOTE]
   >
   > * AEM 프로젝트의 `index.html` 페이지를 보려면 URL `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`을(를) 사용하십시오.
   > * AEM 프로젝트의 `index page` 이외의 페이지를 보려면 URL `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`을(를) 사용하십시오.

이제 [양식을 만들어 AEM 프로젝트에 추가](#add-edge-delivery-services-forms-to-aem-project)할 수 있습니다.

## 기존 AEM 프로젝트에 적응형 Forms 블록 추가

기존 AEM 프로젝트가 있는 경우 적응형 양식 블록을 현재 프로젝트에 통합하여 양식 만들기를 시작할 수 있습니다.

>[!NOTE]
>
>
> 이 단계는 [AEM 상용구](https://github.com/adobe-rnd/aem-boilerplate-xwalk)를 사용하여 빌드한 프로젝트에 적용됩니다. [AEM Forms 상용구](https://github.com/adobe-rnd/aem-boilerplate-forms)를 사용하여 AEM 프로젝트를 만든 경우 이 단계를 건너뛸 수 있습니다.

통합하는 방법은 다음과 같습니다.

1. 적응형 Forms 블록 GitHub 리포지토리([https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms))를 컴퓨터에 복제합니다.
1. 다운로드한 폴더 내에서 `blocks/form` 폴더를 찾아 이 폴더를 복사합니다.
1. AEM 프로젝트 GitHub 저장소를 컴퓨터에 복제합니다.
1. 이제 로컬 AEM Project 저장소의 `blocks` 폴더로 이동하여 복사한 양식 폴더를 붙여넣습니다.
1. GitHub의 AEM 프로젝트 저장소에 이러한 변경 사항을 커밋하고 푸시합니다.

이번 단계가 끝났습니다! 적응형 Forms 블록은 이제 AEM 프로젝트의 일부입니다. [양식을 만들어 AEM 프로젝트에 추가](#add-edge-delivery-services-forms-to-aem-site-project)할 수 있습니다.

## WYSIWYG을 사용하여 AEM Forms 작성

AEM Project를 WYSIWYG 작성용 유니버설 편집기에서 열고 프로젝트를 편집하고 적응형 양식 섹션을 추가하여 AEM Project 페이지에 Edge Delivery Services 양식을 포함할 수 있습니다.

1. 적응형 양식 섹션을 AEM Project 페이지에 추가합니다. 추가하려면:
   1. 사이트 콘솔에서 AEM 프로젝트로 이동한 다음 **편집**을 클릭합니다. 범용 편집기에서 편집할 AEM 프로젝트 페이지가 열립니다.
이 경우 `index.html` 페이지가 일러스트레이션에 사용됩니다.
   1. 콘텐츠 트리를 열고 적응형 양식 섹션을 추가하려는 위치로 이동합니다.
   1. **[!UICONTROL 추가]** 아이콘을 클릭하고 구성 요소 목록에서 **[!UICONTROL 적응형 양식]** 구성 요소를 선택합니다.

   ![콘텐츠 트리](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   적응형 양식 섹션이 지정된 위치에 추가됩니다. 이제 AEM Project 페이지에 양식 구성 요소를 추가할 수 있습니다.

1. 추가된 적응형 양식 섹션에 양식 구성 요소를 추가합니다. 양식 구성 요소를 추가하려면 다음을 수행합니다.
   1. 콘텐츠 트리에서 추가된 적응형 양식 섹션으로 이동합니다.

      ![적응형 양식 블록 추가됨](/help/edge/docs/forms/assets/adative-form-block.png)


   1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성요소** 목록에서 원하는 구성 요소를 추가합니다.

      ![구성 요소 추가](/help/edge/docs/forms/assets/add-component.png)

      또한 범용 편집기에서 직관적인 드래그 앤 드롭 기능을 제공하므로 필요한 적응형 Forms 구성 요소를 드래그 앤 드롭할 수도 있습니다.

   1. 추가된 적응형 양식 구성 요소를 선택하여 **[!UICONTROL 속성]**&#x200B;을 사용하여 속성을 업데이트합니다.

      ![속성 열기](/help/edge/docs/forms/assets/component-properties.png)

      아래 스크린샷에는 WYSIWYG 작성을 사용하여 AEM 프로젝트에서 작성된 양식이 표시됩니다.

      ![추가된 양식](/help/edge/docs/forms/assets/added-form-aem-sites.png)

   >[!NOTE]
   >
   > 변경 후 AEM 프로젝트 페이지를 다시 게시하는 것이 중요합니다. 그렇지 않으면 업데이트는 브라우저에 표시되지 않습니다.

1. AEM 프로젝트 페이지를 다시 게시합니다.

   1. 양식을 추가한 후 AEM 프로젝트 페이지를 다시 게시하려면 **Publish**&#x200B;을(를) 클릭하십시오.

      ![양식 게시](/help/edge/docs/forms/assets/publish-form.png)

   1. **Publish** 확인 대화 상자가 화면에 나타나면 **Publish**&#x200B;을(를) 클릭하여 게시를 시작합니다.

      ![양식 게시1](/help/edge/docs/forms/assets/publish-form1.png)

      **Publish** 단추를 클릭하면 `Publish started successfully` 메시지가 나타납니다.

      ![양식 게시](/help/edge/docs/forms/assets/publish-form2.png)

   이제 다음 URL에서 추가된 Edge Delivery Services 양식이 있는 AEM 프로젝트 페이지를 볼 수 있습니다.
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`

   예를 들어 분기 이름이 `main`이고 저장소는 `edsforms`이고 소유자는 `wkndforms`이고 사이트 이름은 `eds-forms`인 경우 URL은 다음과 같습니다.
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![인덱스 페이지](/help/edge/docs/forms/assets/publish-index-page.png)

적응형 Forms 블록에서 `.css` 및 `.js` 파일을 편집하고 [로컬 AEM 개발 환경을 설정](#set-up-local-aem-development-environment)하여 Edge Delivery Services Forms의 스타일을 지정하여 변경 내용을 브라우저에서 즉시 볼 수 있습니다.

## 로컬 AEM 개발 환경 설정

로컬에서 사용자 지정 스타일 및 구성 요소를 개발하기 위한 로컬 AEM 개발 환경을 설정할 수 있습니다. 로컬 AEM 개발 환경을 사용하여 시작하고 실행하려면 다음을 수행하십시오.

1. **AEM CLI를 설치합니다**: AEM CLI는 개발 작업을 간소화합니다. npm을 사용하여 전역적으로 설치해 보겠습니다.

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **GitHub 프로젝트 복제**: 다음 명령을 사용하여 GitHub에서 AEM 프로젝트 저장소를 복제하고 바꾸기 <owner> 저장소 소유자와 <repo> 저장소 이름은 바꿉니다.

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **로컬 환경 시작**: 프로젝트 디렉터리로 이동한 후 단일 명령으로 로컬 AEM 인스턴스를 시작합니다.

   ```
   cd <repo>
   aem up
   ```

적응형 Forms 블록 `blocks/form` 폴더에서 로컬 변경 작업을 수행하여 양식을 스타일링하고 코딩할 수 있습니다. 이 디렉터리에서 `.css` 또는 `.js` 파일을 편집하면 변경 내용이 즉시 브라우저에 반영됩니다.

변경 사항을 완료했으면 Git 명령을 사용하여 변경 사항을 커밋하고 푸시합니다. 이렇게 하면 다음 URL에서 액세스할 수 있는 미리보기 및 프로덕션 환경이 업데이트됩니다(자리 표시자를 프로젝트 세부 정보로 대체).

미리보기: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
프로덕션: `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## GitHub 빌드 문제 해결

잠재적인 문제를 해결하면 GitHub 빌드 프로세스를 원활하게 할 수 있습니다.

* **린팅 오류 처리**:
린팅 오류가 발생하는 경우 우회할 수 있습니다. [EDS Project]/package.json 파일을 열고 “lint” 스크립트를 `"lint": "npm run lint:js && npm run lint:css"`에서 `"lint": "echo 'skipping linting for now'"`로 수정합니다. 파일을 저장하고 변경 사항을 GitHub 프로젝트에 커밋합니다.

<!-- * **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file. -->
