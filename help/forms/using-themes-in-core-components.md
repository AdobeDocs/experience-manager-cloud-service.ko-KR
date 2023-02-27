---
title: 테마 만들기 및 사용
description: 테마를 사용하여 핵심 구성 요소를 사용하여 적응형 양식에 시각화를 지정하고 시각적 ID를 제공할 수 있습니다. 여러 적응형 Forms에서 테마를 공유할 수 있습니다.
source-git-commit: 1357b36dc3d14d2ceceb6761cb005b592472890a
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 5%

---


# 응용 Forms의 테마(핵심 구성 요소) {#themes-for-af-using-core-components}

핵심 구성 요소를 사용하여 테마를 만들고 적용하여 적응형 양식의 스타일을 조정할 수 있습니다. 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 스타일은 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성을 포함합니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소를 반영합니다. 테마는 적응형 양식에 대한 참조 없이 독립적으로 관리됩니다.

다음 경우에 [적응형 양식 만들기](/help/forms/creating-adaptive-form.md) 핵심 구성 요소를 사용하여 기본 제공 테마는 **스타일** 탭. 기본적으로 **캔버스** 테마를 사용할 수 있습니다.

>[!NOTE]
>
>적응형 양식 테마를 [적응형 양식 템플릿.](/help/forms/template-editor.md) 적응형 양식 테마에 적응형 양식에 대한 스타일 정보만 포함됩니다. 적응형 양식 템플릿은 양식 구조 및 초기 컨텐츠를 정의하며, 새로운 양식을 만들 수 있도록 테마를 포함합니다 [적응형 양식.](/help/forms/creating-adaptive-form.md)

## 핵심 구성 요소를 사용하여 적응형 Forms에서 캔버스 테마 사용 {#using-theme-in-adaptive-form}

적응형 양식에 테마를 적용하는 단계는 다음과 같습니다.

1. AEM Forms 작성자 인스턴스에 로그인합니다.

1. 탭 **Adobe Experience Manager** > **Forms** > **Forms 및 문서**.

1. 클릭 **만들기** > **응용 Forms**. 적응형 양식 만들기 마법사가 열립니다.

1. 에서 핵심 구성 요소 템플릿을 선택합니다 **소스** 탭.

   >[!NOTE]
   >
   > 핵심 구성 요소로 적응형 양식을 만들면 스타일 탭 아래에 캔버스 테마가 표시됩니다. 현재 사용할 수 있는 유일한 기본 테마입니다. 하지만 테마를 원하는 대로 변경하고 프런트 엔드 파이프라인을 설정하여 나중에 사용할 수 있도록 저장할 수 있습니다.

1. 에서 캔버스 테마를 선택합니다 **스타일** 탭.
1. **만들기**&#x200B;를 클릭합니다.

적응형 양식 테마는 적응형 양식을 만드는 동안 스타일을 정의하기 위해 적응형 양식 템플릿의 일부로 사용됩니다.

## 테마 사용자 지정 {#customizing-theme}

테마를 사용자 지정하려면

* [Cloud Manager에서 파이프라인 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)
* 을 사용하여 사용자 구성 [기여자 역할](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html).
* 다음을 수행해야 합니다. [Git에 대한 기본 지식](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git) 및 Git 리포지토리 Cloud Service.

캔버스 테마를 사용자 지정하는 방법:
1. [캔버스 테마 복제](#1-download-canvas-theme-download-canvas-theme)
1. [테마 구조 이해](#2-understand-structure-of-the-canvas-theme-structure-of-canvas-theme)
1. [package.json 및 package_lock.json의 이름 변경](#changename-packagelock-packagelockjson)
1. [만들기 ](#3-create-the-env-file-in-a-theme-folder-creating-env-file-theme-folder)
1. [로컬 프록시 서버 시작](#4-start-a-local-proxy-server-starting-a-local-proxy-server)
1. [테마 사용자 지정](#customize-the-theme-customizing-theme)
1. [변경 사항 커밋](#6-committing-the-changes-committing-the-changes)
1. [파이프라인 배포](#7-deploying-the-customized-theme-deploy-customized-theme)

### 1. 캔버스 테마 복제 {#download-canvas-theme}

명령 프롬프트를 열고 다음 명령을 실행하여 캔버스 테마를 복제합니다.

```
git clone https://github.com/adobe/aem-forms-theme-canvas
```

>[!NOTE]
>
> 양식 작성 마법사의 스타일 탭에 package.json 파일과 동일한 테마 이름이 표시됩니다.

### 2. 주제 구조를 이해합니다 {#structure-of-canvas-theme}

적응형 양식 테마는 CSS, JavaScript 및 양식 스타일을 정의하고 적응형 양식 테마의 구조를 준수하는 정적 리소스가 포함된 패키지입니다. 적응형 양식 테마는 프런트 엔드 프로젝트의 일반적인 다음 구조를 갖습니다.

* `src/components`: AEM 코어 구성 요소에 해당하는 JavaScript 및 CSS 파일
* `src/resources`: 아이콘, 로고 및 글꼴과 같은 정적 파일
* `src/site`: 전체 AEM Sites 페이지에 적용되는 JavaScript 및 CSS 파일
* `src/theme.ts`: JavaScript 및 CSS 테마의 기본 시작 지점
* `src\theme.scss`: 전체 테마에 적용되는 JavaScript 및 CSS 파일

다음 `src/components` 폴더에는 단추, 확인란, 컨테이너, 바닥글 등과 같은 모든 AEM 핵심 구성 요소에 대해 특정 JavaScript 및 CSS 파일이 있습니다. AEM 구성 요소에 해당하는 CSS 파일을 편집하여 단추 또는 확인란의 스타일을 지정할 수 있습니다.

![테마 편집](/help/forms/assets/theme_structure.png)

테마를 사용자 지정하기 위해 로컬 프록시 서버를 시작하여 실제 AEM 컨텐츠를 기반으로 테마 사용자 지정을 실시간으로 볼 수 있습니다.

### 3. 캔버스 테마의 package.json 및 package_lock.json에서 이름을 변경합니다 {#changename-packagelock-packagelockjson}

캔버스 테마의 이름과 버전을 `package.json` 및 `package_lock.json` 파일.

>[!NOTE]
>
> 이름에 `@aemforms` 태그에 가깝게 포함했습니다. 사용자가 제공한 이름으로 간단한 텍스트여야 합니다.

![캔버스 테마 사진](/help/forms/assets/changename_canvastheme.png)

### 4. 테마 폴더에 .env 파일을 만듭니다. {#creating-env-file-theme-folder}

만들기 `.env` 파일을 테마 폴더에 넣고 다음 매개 변수를 추가합니다.

* **AEM url**
AEM_URL=https://[author-instance]

* **AEM 사이트 이름**
AEM_ADAPTIVE_FORM=Form_name

* **AEM 프록시 포트**
AEM_PROXY_PORT=7000


![캔버스 테마 구조](/help/forms/assets/env-file-canvas-theme.png)

### 5. 로컬 프록시 서버 시작 {#starting-a-local-proxy-server}

1. 명령줄에서 로컬 컴퓨터의 테마 루트로 이동합니다.
1. `npm install`을 실행하면 npm이 종속성을 가져오고 프로젝트를 설치합니다.
1. `npm run live`를 실행하면 프록시 서버가 시작됩니다.

   ![npm 실행](/help/forms/assets/theme_proxy.png)


1. 탭 또는 클릭 **로컬로 로그인(관리 작업만 해당)** AEM 관리자가 제공한 프록시 사용자 자격 증명으로 로그인합니다.

   ![로컬에서 로그인](/help/forms/assets/local_signin.png)

   >[!NOTE]
   >
   > * 로컬에 로그인할 로컬 사용자를 만듭니다. 테마 디자이너의 기여자 역할을 제공합니다.
   > * AEM URL을 `http://localhost:[port]/` 에서 `.env` 캔버스 테마 파일에서는 브라우저로 직접 리디렉션됩니다.


1. 로그인한 후 브라우저에서 AEM 관리자가 제공한 샘플 콘텐츠로의 경로를 표시하도록 URL을 변경합니다.

   * 예를 들어 제공된 경로가 `/content/formname.html?wcmmode=disabled`인 경우로 URL을 변경합니다. `http://localhost:[port]/content/forms/af/formname.html?wcmmode=disabled`

   ![프록시화된 샘플 콘텐츠](/help/forms/assets/sample_af.png)

적응형 양식으로 이동하여 적응형 양식에 적용된 캔버스 테마를 확인합니다.

### 6. 테마 사용자 정의 {#customize-theme}

1. 편집기에서 파일을 엽니다 `<your-theme-sources>/src/site/_variables.scss`.

   >[!NOTE]
   >
   > 사이트의 모든 적응형 양식 구성 요소에 스타일을 지정하려면 `site/_variables.scss` 파일.

1. 에 대한 변수 편집 `font colour` to `red`.

   ![테마 편집](/help/forms/assets/edit_theme.png)

   **다양한 AEM 구성 요소의 스타일을 지정합니다**

   편집기에서 CSS 파일을 변경하여 적응형 양식의 여러 구성 요소에 스타일을 지정할 수 있습니다. 캔버스 테마 폴더에는 각 적응형 양식 핵심 구성 요소에 대해 다른 CSS 폴더가 있습니다.

   ![코어 구성 요소](/help/forms/assets/theme-component.png)

   테마 편집기에서 특정 구성 요소의 스타일을 지정하려면 테마 폴더에서 CSS를 편집할 수 있습니다. 예를 들어 텍스트 상자 필드의 테두리 색상을 변경하려면 편집기에서 CSS 파일을 열고 테두리 색상을 변경합니다.

   ![텍스트 상자 CSS 편집](/help/forms/assets/edit_color_textbox.png)

1. 파일을 저장하면 프록시 서버가 줄을 통해 변경 사항을 인식합니다 `[Browsersync] File event [change]`.

   ![프록시 브라우저 동기화](/help/forms/assets/browser_sync.png)

1. 로컬 프록시 서버의 브라우저로 다시 전환하면 변경 내용이 즉시 표시됩니다.

   ![AF 테마 변경](/help/forms/assets/edit_theme_af.png)

테마 디자이너는 로컬 프록시 서버의 변경 내용을 미리 보고 다른 AEM 구성 요소에 대한 요구 사항에 따라 테마를 사용자 지정합니다.

변경 사항을 AEM Git 리포지토리에 커밋하기 전에 [Git 리포지토리 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git).

### 7. 변경 사항 커밋 {#committing-the-changes}

테마를 변경하고 로컬 프록시 서버로 테스트한 후 변경 사항을 AEM Forms Cloud Service의 Git 리포지토리에 커밋하십시오. 따라서 적응형 Forms 작성자가 사용할 수 있도록 Forms Cloud Service 환경에서 사용자 지정된 테마를 사용할 수 있습니다.

AEM Forms Cloud Service의 Git 리포지토리에 변경 사항을 커밋하기 전에 로컬 시스템에서 리포지토리의 복제가 필요합니다. 저장소를 복제하려면

1. 을(를) 클릭하여 새 테마 저장소를 만듭니다 **[!UICONTROL 저장소]** 선택 사항입니다.

   ![새 테마 리포지토리 만들기](/help/forms/assets/createrepo_canvastheme.png)

1. 클릭 **[!UICONTROL 저장소 추가]** 그리고 **저장소 이름** 에서 **저장소 추가** 대화 상자 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![캔버스 테마 리포지토리 추가](/help/forms/assets/addcanvasthemerepo.png)

1. 클릭 **[!UICONTROL 저장소 URL 복사]** 생성된 저장소의 URL을 복사하기 위해

   ![캔버스 테마 URL](/help/forms/assets/copyurl_canvastheme.png)

1. 명령 프롬프트를 열고 위에 생성한 클라우드 저장소를 복제합니다.

   ```
   git clone https://git.cloudmanager.adobe.com/aemforms/Canvasthemerepo/
   ```

1. 편집 중인 테마 리포지토리의 파일을 다음과 유사한 명령을 사용하여 클라우드 저장소로 이동합니다
   `cp -r [source-theme-folder]/* [destination-cloud-repo]`
예를 들어 이 명령을 사용합니다 
`cp -r [C:/cloned-git-canvas/*] [C:/cloned-repo]`
1. 클라우드 저장소의 디렉토리에서 다음 명령을 사용하여 이동한 테마 파일을 커밋합니다.

   ```text
   git add .
   git commit -a -m "Adding theme files"
   git push
   ```

1. 사용자 지정 항목이 Git 리포지토리에 푸시됩니다.

   ![변경 내용 커밋됨](/help/forms/assets/cmd_git_push.png)

사용자 지정은 이제 Git 리포지토리에 안전하게 저장됩니다.


### 8. 프런트 엔드 파이프라인 실행 {#deploy-pipeline}

1. 프런트 엔드 파이프라인을 만들어 사용자 지정된 테마를 배포합니다. 학습 [맞춤형 테마를 배포하기 위해 전방 파이프라인을 설정하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline).
1. 생성된 프런트 엔드 파이프라인을 실행하여 사용자 지정된 테마 폴더를 **[!UICONTROL 스타일]** 적응형 양식 만들기 마법사의 탭입니다.

>[!NOTE]
>
>나중에 캔버스 테마 폴더를 수정한 경우 위의 파이프라인을 다시 실행해야 합니다. 따라서 파이프라인의 이름을 기억해야 합니다.

## 테마를 사용자 지정하는 예 {#example-to-customize-a-theme}

1. AEM Forms 작성자 인스턴스에 로그인합니다.
1. 핵심 구성 요소를 사용하여 만든 적응형 양식을 엽니다.
1. 명령 프롬프트를 사용하여 로컬 프록시 서버를 시작하고 **로컬로 로그인(관리 작업만 해당)**.
1. 로그인하면 브라우저로 리디렉션되고 적용된 테마를 볼 수 있습니다.
1. 다운로드 [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas) 다운로드한 zip 폴더를 추출합니다.
1. 기본 설정 편집기에서 추출된 zip 폴더를 엽니다.
1. 만들기 `.env` 테마 폴더에 있는 파일 및 매개 변수 추가: **AEM URL**, **AEM_ADAPTIVE_FORM** 및 **AEM_PROXY_PORT**.
1. 캔버스 테마 폴더에서 텍스트 상자의 CSS 파일을 열고 테두리 색상을 다음과 같이 변경합니다 `red` 색상을 지정하고 변경 내용을 저장합니다.
1. 브라우저를 다시 열면 변경 사항이 적응형 양식에 즉시 반영됩니다.
1. 복제된 저장소에서 캔버스 테마 폴더를 이동합니다.
1. 변경 사항을 커밋하고 프런트 엔드 파이프라인을 실행합니다.

파이프라인이 실행되면 스타일 탭 아래에서 테마를 사용할 수 있습니다.

## 우수 사례 {#best-practices}

* **다른 테마에서 자산 방지**

   테마를 편집할 때 다른 주제의 자산(예: 이미지)을 찾아보고 추가할 수 있습니다. 예를 들어 페이지의 배경을 편집하는 경우 예를 들어 **[!UICONTROL 페이지]** ![편집 단추](assets/edit-button.png)> **[!UICONTROL 배경]** > **[!UICONTROL 추가]** > **[!UICONTROL 이미지]**&#x200B;다른 테마에서 이미지를 탐색하고 추가할 수 있는 대화 상자가 표시됩니다.

   다른 테마에서 자산이 추가되고 다른 테마가 이동되거나 삭제되는 경우 현재 테마에 문제가 발생할 수 있습니다. 다른 테마의 자산을 탐색하고 추가하지 않는 것이 좋습니다.

* **컨테이너 패널 레이아웃 너비 변경**

   컨테이너 패널 레이아웃 너비를 변경하지 않는 것이 좋습니다. 컨테이너 패널의 너비를 지정하면 정적이 되고 다른 디스플레이에 조정되지 않습니다.

* **머리글 및 바닥글 작업에 양식 편집기 또는 테마 편집기 사용**

   글꼴 스타일, 배경 및 투명도와 같은 스타일 옵션을 사용하여 머리글 및 바닥글 스타일을 지정하려면 테마 편집기를 사용합니다.
로고 이미지, 머리글의 회사 이름, 바닥글에 저작권 정보 등의 정보를 제공하려면 양식 편집기 옵션을 사용하십시오.
