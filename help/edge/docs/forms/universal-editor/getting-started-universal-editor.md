---
title: 범용 편집기에서 AEM Forms용 Edge Delivery Services 시작하기 - 개발자 튜토리얼
description: 이 튜토리얼에서는 새로운 AEM(Adobe Experience Manager Forms) 프로젝트를 시작하고 실행하는 방법을 안내합니다. 10~20분 안에 범용 편집기에서 나만의 Edge Delivery Services 양식을 만들 수 있습니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: bcf8f9e5273819eaee09875ec81251fe4330701c
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 99%

---


# 범용 편집기(WYSIWYG)를 사용하여 AEM Forms용 Edge Delivery Services 시작하기

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| 범용 편집기 기반 작성 | 이 문서 |
| 문서 기반 작성 | [여기 클릭](/help/edge/docs/forms/tutorial.md) |


<span class="preview"> 이 기능은 얼리 액세스 프로그램을 통해 사용할 수 있습니다. 액세스 권한을 요청하려면 공식 주소를 통해 GitHub 조직 이름과 저장소 이름을 포함한 이메일을 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>으로 보내 주십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc, 조직 이름이 adobe, 저장소 이름이 abc인 경우입니다.</span>

오늘날의 디지털 시대에는 사용자 친화적인 양식을 만드는 것이 모든 조직에 필수적입니다. Edge Delivery Services 양식은 WYSIWYG(What-You-See-Is-What-You Get) 기능을 제공하는 범용 편집기를 사용하여 작성됩니다. 범용 편집기는 효율적인 양식 작성을 위한 현대적이고 직관적인 인터페이스를 제공합니다.

AEM Forms는 데이터를 캡처하고 캡처한 데이터를 저장하는 Edge Delivery Services 양식을 쉽게 만들 수 있는 적응형 양식 블록이라는 블록을 제공합니다. [적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트를 만들거나](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [기존 AEM 프로젝트에 적응형 양식 블록을 추가](#add-adaptive-forms-block-to-your-existing-aem-project)할 수 있습니다.

<!-->
![Github 저장소 워크플로](/help/edge/assets/repo-workflow.png){width="50%" align="center" height="50%"}—>

이 튜토리얼에서는 범용 편집기의 WYSIWYG 작성 기능을 사용하여 새 Adobe Experience Manager 사이트 프로젝트나 기존 Adobe Experience Manager 사이트 프로젝트에서 직접 양식을 만들고, 미리 보고, 게시하는 방법을 안내합니다.


## 사전 요구 사항

* GitHub 계정이 있고 Git 기본 사항을 이해하고 있습니다.
* HTML, CSS 및 JavaScript의 기본 사항을 이해합니다.
* 로컬 개발을 위해 Node/npm이 설치되어 있습니다.

## 적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트 만들기

AEM Forms 상용구 템플릿을 사용하면 적응형 양식 블록으로 사전 구성된 AEM 프로젝트를 빠르게 시작할 수 있습니다. AEM 모범 사례를 따르면서 바로 양식 작성을 시작하는 가장 빠르고 쉬운 방법입니다.

### AEM Forms 상용구 저장소 템플릿 시작하기

1. AEM 프로젝트의 GitHub 저장소를 만듭니다. 저장소를 만드는 방법은 다음과 같습니다.
   1. [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)로 이동합니다.

      ![AEM Forms 상용구](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. **이 템플릿 사용** 옵션을 클릭하고 **새 저장소 만들기** 옵션을 선택합니다.

      ![AEM Forms 상용구를 사용하여 새 저장소 만들기](/help/edge/docs/forms/assets/use-eds-form-template.png)

      **새 저장소 만들기** 화면이 열립니다.

   1. **새 저장소 만들기** 화면에서 **소유자**&#x200B;를 선택하고 **저장소 이름**&#x200B;을 지정합니다. 저장소를 **공개**&#x200B;로 설정하는 것이 좋습니다. 따라서 **공개** 옵션을 선택하고 **저장소 만들기**&#x200B;를 클릭합니다.

      ![저장소를 공개로 설정](/help/edge/docs/forms/assets/name-eds-repo.png)

1. 저장소에 AEM Code Sync GitHub 앱을 설치합니다. 설치하는 방법은 다음과 같습니다.
   1. [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)로 이동합니다.
   1. **AEM Code Sync 설치** 화면에서 **저장소만 선택** 옵션을 선택하고 새로 만든 저장소를 선택합니다. **저장**&#x200B;을 클릭합니다.

   ![저장소를 공개로 설정](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. 이제 AEM Forms 상용구를 사용하여 만든 GitHub 저장소를 AEM 프로젝트 작성 환경에 링크합니다. 연결하는 방법은 다음과 같습니다.

   1. 앞서 AEM Forms 상용구를 사용하여 만든 GitHub 저장소로 이동합니다.
   1. 편집을 위해 **fstab.yaml** 파일을 엽니다.

      ![fstab.yaml 파일 열기](/help/edge/docs/forms/assets/open-fstab.png)

   1. **fstab.yaml** 파일을 편집하여 프로젝트의 마운트 지점을 업데이트합니다. URL을 AEM as a Cloud Service 작성 인스턴스의 URL로 바꿉니다.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![fstab.yaml 파일 편집](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. 참조를 업데이트했고 모든 항목에 문제가 없으면 업데이트된 **fstab.yaml** 파일을 커밋합니다.

      ![변경 사항 커밋](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      빌드 문제가 발생하면 [GitHub 빌드 문제 해결](#troubleshooting-github-build-issues)을 참조하십시오.

### 새 AEM 프로젝트 만들기

이제 GitHub 프로젝트가 있으므로 AEM as a Cloud Service 작성 인스턴스에서 새 AEM 프로젝트를 만들고 게시할 수 있습니다.
1. 새 AEM 프로젝트를 만드는 방법은 다음과 같습니다.

   1. AEM as a Cloud Service 작성 인스턴스에 로그인하고 **사이트**&#x200B;를 선택합니다.

      ![사이트 선택](/help/edge/assets/select-sites.png)

   1. **만들기** > **템플릿으로 사이트 만들기**&#x200B;를 선택합니다.

      ![create-sites](/help/edge/docs/forms/assets/create-sites.png)

   1. Edge Delivery Services 사이트 템플릿을 선택하고 **다음**&#x200B;을 클릭합니다.

      ![select-site-template](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * 작성 인스턴스에서 Edge Delivery Services 사이트 템플릿을 사용할 수 없는 경우, [가져오기] 버튼을 클릭하여 템플릿을 업로드합니다.
      > * [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)에서 Edge Delivery Services 사이트 템플릿을 다운로드할 수 있습니다.

   1. 새 AEM 프로젝트를 만들기 위해 다음 세부 정보를 입력합니다.
      * **사이트 제목** - 사이트를 설명하는 제목을 추가합니다.
      * **사이트 제목** - 이전 단계에서 정의한 `site-name`을 사용합니다.
      * **GitHub URL** - 이전 단계에서 만든 GitHub 프로젝트의 URL을 사용합니다.

      ![AEM 사이트 만들기](/help/edge/docs/forms/assets/create-aem-site.png)

   1. **사이트 만들기** 대화 상자가 표시되면 **확인**&#x200B;을 클릭합니다.

      ![확인 클릭](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      단 몇 분 만에 새로운 AEM 프로젝트가 생성됩니다.

   1. Sites 콘솔에서 새로 만든 AEM 프로젝트로 이동하여 **편집**을 클릭합니다.
이 경우 `index.html` 페이지는 설명 목적으로 사용됩니다.

      ![AEM 사이트 편집](/help/edge/docs/forms/assets/edit-site.png)

      AEM 프로젝트는 범용 편집기에서 새 탭으로 열려 WYSIWYG 작성이 가능합니다. 이제 AEM 프로젝트를 편집할 수 있습니다.

      ![사이트가 범용 편집기에서 열림](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. 새로 만든 AEM 프로젝트 게시

   AEM 프로젝트 편집을 마친 다음 게시합니다. 게시 방법은 다음과 같습니다.

   1. Sites 콘솔에서 AEM 페이지를 모두 선택하고 **빠른 게시**&#x200B;를 클릭합니다.

      ![AEM Sites 프로젝트 게시](/help/edge/docs/forms/assets/publish-sites.png)

   1. **빠른 게시** 확인 대화 상자가 표시되면 **게시**&#x200B;를 클릭하여 게시 프로세스를 시작합니다.

      ![빠른 게시 확인 대화 상자](/help/edge/docs/forms/assets/quick-publish.png)

      또는 범용 편집기 사용자 인터페이스에서 AEM 프로젝트 페이지를 바로 게시할 수도 있습니다.

      ![빠른 게시 확인 대화 상자](/help/edge/docs/forms/assets/qui.png)

   축하합니다! `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`에서 새 웹 사이트가 실행되고 있습니다.

   * `<branch>`는 GitHub 저장소의 분기를 나타냅니다.
   * `<repository>`는 GitHub 저장소를 나타냅니다.
   * `<owner>`는 GitHub 저장소를 호스팅하는 GitHub 계정의 사용자 이름을 나타냅니다.
   * `<site-name>`은 생성된 사이트 이름을 나타냅니다.

   예를 들어 분기 이름이 `main`이고 저장소가 `edsforms`이며 소유자가 `wkndforms`이고 `site-name`이 `eds-forms`인 경우 웹 사이트는 `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`에서 실행됩니다.

   >[!NOTE]
   >
   > * AEM 프로젝트의 `index.html` 페이지를 보려면 다음 URL을 사용합니다. `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
   > * AEM 프로젝트의 `index page` 이외의 페이지를 보려면 다음 URL을 사용합니다. `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`

이제 [AEM 프로젝트에 양식을 만들고 추가](#add-edge-delivery-services-forms-to-aem-project)할 수 있습니다.

## 기존 AEM 프로젝트에 적응형 양식 블록 추가

기존 AEM 프로젝트가 있는 경우 적응형 양식 블록을 현재 프로젝트에 통합하여 양식 만들기를 시작할 수 있습니다.

>[!NOTE]
>
>
> 이 단계는 [AEM 상용구](https://github.com/adobe-rnd/aem-boilerplate-xwalk)를 사용하여 빌드한 프로젝트에 적용됩니다. [AEM Forms 상용구](https://github.com/adobe-rnd/aem-boilerplate-forms)를 사용하여 AEM 프로젝트를 만든 경우 이 단계를 건너뛸 수 있습니다.

통합하는 방법은 다음과 같습니다.
1. **필수 파일 및 폴더 추가**
   1. [AEM 양식 보일러플레이트](https://github.com/adobe-rnd/aem-boilerplate-forms)에서 다음 폴더와 파일을 복사하여 AEM 프로젝트에 붙여넣습니다.

      * [양식 블록](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) 폴더
      * [form-common](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-common) 폴더
      * [form-components](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-components) 폴더
      * [form-editor-support.js](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) 파일
      * [form-editor-support.css](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) 파일

1. **구성 요소 정의 및 모델 파일 업데이트**
   1. AEM 프로젝트의 `../models/_component-definition.json` 파일로 이동하여 [AEM Forms 보일러플레이트의 _component-definition.json 파일](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-definition.json#L39-L48)의 변경 사항으로 업데이트합니다.

   1. AEM 프로젝트의 `../models/_component-models.json` 파일로 이동하여 [AEM Forms 보일러플레이트의 _component-models.json 파일](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-models.json#L24-L26)의 변경 사항으로 업데이트합니다.

1. **편집기 스크립트에 양식 편집기 추가**
   1. AEM Project의 `../scripts/editor-support.js` 파일로 이동하여 [AEM Forms 보일러플레이트의 editor-support.js 파일](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js#L105-L106)의 변경 사항으로 업데이트합니다.
1. **ESLint 구성 파일 업데이트**
   1. AEM 프로젝트에서 `../.eslintignore` 파일로 이동하고 다음 코드 라인을 추가하여 폼 블록 규칙 엔진과 관련된 오류를 방지합니다.

      ```
          blocks/form/rules/formula/*
          blocks/form/rules/model/*
      ```

1. GitHub의 AEM 프로젝트 저장소에 이러한 변경 사항을 커밋하고 푸시합니다.

이번 단계가 끝났습니다! 적응형 양식 블록은 이제 AEM 프로젝트의 일부입니다. 이제 [AEM 프로젝트에 양식을 만들고 추가](#add-edge-delivery-services-forms-to-aem-site-project)할 수 있습니다.

## WYSIWYG를 사용하여 양식 작성

WYSIWYG 작성을 위해 범용 편집기에서 AEM 프로젝트를 열어 프로젝트를 편집하고 AEM 프로젝트 페이지에 Edge Delivery Services 양식을 포함하도록 적응형 양식 섹션을 추가할 수 있습니다.

1. AEM 프로젝트 페이지에 적응형 양식 섹션을 추가합니다. 추가 방법은 다음과 같습니다.
   1. Sites 콘솔에서 AEM 프로젝트로 이동하여 편집할 사이트 페이지를 선택한 다음 **편집**을 클릭합니다. 편집할 수 있도록 AEM 프로젝트 페이지가 범용 편집기에서 열립니다.
이 경우 `index.html` 페이지는 설명 목적으로 사용됩니다.
   1. 콘텐츠 트리를 열고 적응형 양식 섹션을 추가할 섹션으로 이동합니다.
   1. **[!UICONTROL 추가]** 아이콘을 클릭하고 구성 요소 목록에서 **[!UICONTROL 적응형 양식]** 구성 요소를 선택합니다.

   ![콘텐츠 트리](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   적응형 양식 섹션이 추가되었습니다. 이제 AEM 프로젝트 페이지에 양식 구성 요소를 추가할 수 있습니다.

1. 추가된 적응형 양식 섹션에 양식 구성 요소를 추가합니다. 양식 구성 요소를 추가하는 방법은 다음과 같습니다.
   1. 콘텐츠 트리에서 추가된 적응형 양식 섹션으로 이동합니다.

      ![추가된 적응형 양식 블록](/help/edge/docs/forms/assets/adative-form-block.png)


   1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 원하는 구성 요소를 추가합니다.

      ![구성 요소 추가](/help/edge/docs/forms/assets/add-component.png)

      범용 편집기는 직관적인 드래그 앤 드롭 기능을 제공하므로 필요한 적응형 양식 구성 요소를 바로 끌어다 놓을 수도 있습니다.

   1. 추가된 적응형 양식 구성 요소를 선택하고 **[!UICONTROL 속성]**&#x200B;을 사용하여 해당 속성을 업데이트합니다.

      ![속성 열기](/help/edge/docs/forms/assets/component-properties.png)

   1. 양식 미리보기.
아래 스크린샷에는 WYSIWYG 작성 기능을 사용하여 AEM 프로젝트에서 작성된 양식이 표시됩니다.

      ![추가된 양식](/help/edge/docs/forms/assets/added-form-aem-sites.png)

      미리보기에 만족하면 사용자는 페이지를 계속 게시할 수 있습니다.

      >[!NOTE]
      >
      > 변경 사항을 적용한 후에는 AEM 프로젝트 페이지를 다시 게시하는 것이 중요합니다. 그렇지 않으면 브라우저에 업데이트 내용이 표시되지 않습니다.

1. AEM 프로젝트 페이지를 다시 게시합니다.

   1. 양식을 추가한 후 **게시**&#x200B;를 클릭하여 AEM 프로젝트 페이지를 다시 게시합니다.

      ![양식 게시](/help/edge/docs/forms/assets/publish-form.png)

   1. 화면에 **게시** 확인 대화 상자가 표시되면 **게시**&#x200B;를 클릭하여 게시를 시작합니다.

      ![양식 게시1](/help/edge/docs/forms/assets/publish-form1.png)

      **게시** 버튼을 클릭하면 `Publish started successfully` 메시지가 나타납니다.

      ![양식 게시2](/help/edge/docs/forms/assets/publish-form2.png)

   이제 다음 URL에서 Edge Delivery Services 양식이 추가된 AEM 프로젝트 페이지를 볼 수 있습니다.
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`

   예를 들어 분기 이름이 `main`이고 저장소가 `edsforms`이며 소유자가 `wkndforms`이고 사이트 이름이 `eds-forms`인 경우 URL은 다음과 같습니다.
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![색인 페이지](/help/edge/docs/forms/assets/publish-index-page.png)

적응형 양식 블록의 `.css` 및 `.js` 파일을 편집하고 [로컬 AEM 개발 환경을 설정](#set-up-local-aem-development-environment)하면 브라우저에서 변경 사항을 즉시 보고 Edge Delivery Services의 스타일을 지정할 수 있습니다.

>[!NOTE]
>
> [범용 편집기에서 독립 실행형 양식을 작성하여 Edge Delivery Services에 게시](/help/edge/docs/forms/universal-editor/create-forms.md)할 수도 있습니다.

## 로컬 AEM 개발 환경 설정

맞춤형 스타일과 구성 요소를 로컬에서 개발하기 위한 로컬 AEM 개발 환경을 설정할 수 있습니다. 로컬 AEM 개발 환경을 시작하고 실행하려면 다음 작업을 수행하십시오.

1. **AEM CLI 설치**: AEM CLI는 개발 작업을 단순화합니다. npm을 사용하여 전역적으로 설치해 보겠습니다.

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **GitHub 프로젝트 복제**: 다음 명령을 사용하여 GitHub에서 AEM 프로젝트 저장소를 복제합니다. 이때 <owner> 저장소 소유자와 <repo> 저장소 이름은 바꿉니다.

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **로컬 환경 시작**: 프로젝트 디렉터리로 이동하고 다음 단일 명령으로 로컬 AEM 인스턴스를 시작합니다.

   ```
   cd <repo>
   aem up
   ```

적응형 양식 블록 `blocks/form` 폴더에서 양식의 스타일과 코딩을 위한 로컬 변경을 할 수 있습니다. 이 디렉터리 내의 `.css` 또는 `.js` 파일을 편집하면 변경 사항이 브라우저에 즉시 반영되는 것을 볼 수 있습니다.

변경 작업을 완료한 후 Git 명령을 사용하여 변경 사항을 커밋하고 푸시합니다. 이렇게 하면 다음 URL에서 액세스할 수 있는 미리보기 및 프로덕션 환경이 업데이트됩니다(플레이스홀더를 프로젝트 세부 정보로 바꾸기).

미리보기: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`

프로덕션: `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## GitHub 빌드 문제 해결

잠재적인 문제를 해결하면 GitHub 빌드 프로세스를 원활하게 할 수 있습니다.

* **린팅 오류 처리**:
린팅 오류가 발생하는 경우 우회할 수 있습니다. [EDS Project]/package.json 파일을 열고 “lint” 스크립트를 `"lint": "npm run lint:js && npm run lint:css"`에서 `"lint": "echo 'skipping linting for now'"`로 수정합니다. 파일을 저장하고 변경 사항을 GitHub 프로젝트에 커밋합니다.

* **모듈 경로 오류 해결:**
“모듈 “../../scripts/lib-franklin.js”에 대한 경로를 확인할 수 없음” 오류가 발생하는 경우 [EDS Project]/blocks/forms/form.js 파일로 이동합니다. lib-franklin.js 파일을 aem.js 파일로 바꿔 import 문을 업데이트합니다.

## 추가 참조

{{universal-editor-see-also}}
