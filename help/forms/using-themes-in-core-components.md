---
title: 테마 만들기 및 사용
description: 테마를 사용하여 핵심 구성 요소를 사용하여 적응형 양식에 스타일을 지정하고 시각적 ID를 제공할 수 있습니다. 여러 적응형 Forms에서 테마를 공유할 수 있습니다.
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 5%

---

# 적응형 Forms(핵심 구성 요소)의 테마 {#themes-for-af-using-core-components}

핵심 구성 요소를 사용하여 적응형 양식에 스타일을 지정할 테마를 만들고 적용할 수 있습니다. 테마에는 구성 요소 및 패널에 대한 스타일 지정 세부 사항이 포함되어 있습니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소에 반영됩니다. 테마는 적응형 양식에 대한 참조 없이 독립적으로 관리됩니다.

다음을 수행하는 경우 [적응형 양식 만들기](/help/forms/creating-adaptive-form.md) 핵심 구성 요소를 사용하면 아래의 기본 테마가 표시됩니다. **스타일** 탭. 기본적으로 **캔버스** 테마를 사용할 수 있습니다.

>[!NOTE]
>
>적응형 양식 테마를 과 혼동하면 안 됩니다. [적응형 양식 템플릿.](/help/forms/template-editor.md) 적응형 양식 테마는 적응형 양식에 대한 스타일 정보만 포함합니다. 적응형 양식 템플릿은 양식 구조 및 초기 콘텐츠를 정의하며 새 템플릿을 만들 수 있는 테마를 포함합니다 [적응형 양식.](/help/forms/creating-adaptive-form.md)

## 핵심 구성 요소를 사용하여 적응형 Forms에서 캔버스 테마 사용 {#using-theme-in-adaptive-form}

적응형 양식에 테마를 적용하는 단계는 다음과 같습니다.

1. AEM Forms 작성자 인스턴스에 로그인합니다.

1. 누르기 **Adobe Experience Manager** > **Forms** > **Forms 및 문서**.

1. 클릭 **만들기** > **적응형 Forms**. 적응형 양식 만들기 마법사가 열립니다.

1. 에서 핵심 구성 요소 템플릿 선택 **소스** 탭.

   >[!NOTE]
   >
   > 핵심 구성 요소가 있는 적응형 양식을 만들면 스타일 탭 아래에 캔버스 테마가 표시됩니다. 이는 현재 사용할 수 있는 유일한 기본 테마입니다. 그러나 프론트엔드 파이프라인을 설정하여 테마를 원하는 대로 변경하고 향후 사용할 수 있도록 저장할 수 있습니다.

1. 에서 캔버스 테마 선택 **스타일** 탭.
1. **만들기**&#x200B;를 클릭합니다.

적응형 양식 테마는 적응형 양식을 작성하는 동안 스타일을 정의하는 적응형 양식 템플릿의 일부로 사용됩니다.

## 테마 맞춤화 {#customizing-theme}

테마를 맞춤화하려면

* [cloud Manager에서 파이프라인 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)
* 를 사용하여 사용자 구성 [기여자 역할](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html).
* 다음 항목이 있어야 합니다. [git에 대한 기본 지식](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git) 및 Cloud Service Git 리포지토리입니다.

캔버스 테마를 사용자 지정하려면 다음을 수행하십시오.

1. [캔버스 테마 복제](#1-download-canvas-theme-download-canvas-theme)
1. [테마의 구조 이해](#2-understand-structure-of-the-canvas-theme-structure-of-canvas-theme)
1. [package.json 및 package_lock.json의 이름 변경](#changename-packagelock-packagelockjson)
1. [만들기 ](#3-create-the-env-file-in-a-theme-folder-creating-env-file-theme-folder)
1. [로컬 프록시 서버 시작](#4-start-a-local-proxy-server-starting-a-local-proxy-server)
1. [테마 맞춤화](#customize-the-theme-customizing-theme)
1. [변경 내용 커밋](#6-committing-the-changes-committing-the-changes)
1. [파이프라인 배포](#7-deploying-the-customized-theme-deploy-customized-theme)

### 1. 캔버스 테마 복제 {#download-canvas-theme}

명령 프롬프트를 열고 다음 명령을 실행하여 캔버스 테마를 복제합니다.

```
git clone https://github.com/adobe/aem-forms-theme-canvas
```

>[!NOTE]
>
> 양식 만들기 마법사의 스타일 탭에는 package.json 파일과 동일한 테마 이름이 표시됩니다.

### 2. 테마의 구조 이해 {#structure-of-canvas-theme}

적응형 양식 테마는 CSS, JavaScript 및 양식의 스타일을 정의하고 적응형 양식 테마의 구조를 준수하는 정적 리소스를 포함하는 패키지입니다. 적응형 양식 테마는 다음과 같은 프론트엔드 프로젝트 구조를 가지고 있습니다.

* `src/components`: AEM 핵심 구성 요소와 관련된 JavaScript 및 CSS 파일
* `src/resources`: 아이콘, 로고 및 글꼴과 같은 정적 파일
* `src/site`: 전체 AEM Sites 페이지에 적용되는 JavaScript 및 CSS 파일
* `src/theme.ts`: JavaScript 및 CSS 테마의 주요 진입점
* `src\theme.scss`: 전체 테마에 적용되는 JavaScript 및 CSS 파일

다음 `src/components` 폴더에는 버튼, 확인란, 컨테이너, 바닥글 등과 같은 모든 AEM 핵심 구성 요소에 고유한 JavaScript 및 CSS 파일이 있습니다. AEM 구성 요소와 관련된 CSS 파일을 편집하여 버튼이나 확인란의 스타일을 지정할 수 있습니다.

![테마 편집](/help/forms/assets/theme_structure.png)

테마를 맞춤화하려면 로컬 프록시 서버를 시작하여 실제 AEM 콘텐츠를 기반으로 테마 맞춤화를 실시간으로 확인할 수 있습니다.

### 3. 캔버스 테마의 package.json 및 package_lock.json에서 이름 변경 {#changename-packagelock-packagelockjson}

에서 캔버스 테마의 이름 및 버전을 업데이트합니다. `package.json` 및 `package_lock.json` 파일.

>[!NOTE]
>
> 이름은 다음과 같을 수 없습니다. `@aemforms` 태그에 가깝게 배치하십시오. 사용자 제공 이름으로 단순 텍스트여야 합니다.

![캔버스 테마 사진](/help/forms/assets/changename_canvastheme.png)

### 4. 테마 폴더에 .env 파일 만들기 {#creating-env-file-theme-folder}

만들기 `.env` 테마 폴더에 파일을 만들고 다음 매개 변수를 추가합니다.

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
   > * 로컬로 로그인할 로컬 사용자를 만듭니다. 테마 디자이너에 대한 기여자 역할을 제공합니다.
   > * AEM URL을 로 지정하는 경우 `http://localhost:[port]/` 다음에서 `.env` 캔버스 테마 파일이며, 브라우저로 직접 리디렉션됩니다.

1. 로그인한 후 브라우저에서 AEM 관리자가 제공한 샘플 콘텐츠로의 경로를 표시하도록 URL을 변경합니다.

   * 예를 들어 제공된 경로가 `/content/formname.html?wcmmode=disabled`인 경우, URL을 다음으로 변경 `http://localhost:[port]/content/forms/af/formname.html?wcmmode=disabled`

   ![프록시화된 샘플 콘텐츠](/help/forms/assets/sample_af.png)

적응형 양식으로 이동하여 적응형 양식에 적용된 캔버스 테마를 확인하십시오.

### 6. 테마 맞춤화 {#customize-theme}

1. 편집기에서 파일을 엽니다. `<your-theme-sources>/src/site/_variables.scss`.

   >[!NOTE]
   >
   > 를 편집하여 사이트에서 모든 적응형 양식 구성 요소의 스타일을 직접 지정할 수 있습니다. `site/_variables.scss` 파일.

1. 다음에 대한 변수 편집 `font colour` 끝 `red`.

   ![테마 편집](/help/forms/assets/edit_theme.png)

   **다른 AEM 구성 요소의 스타일 지정**

   편집기에서 CSS 파일을 변경하여 적응형 양식의 여러 구성 요소를 스타일링할 수 있습니다. 캔버스 테마 폴더에 각 적응형 양식 핵심 구성 요소에 대한 다양한 CSS 폴더가 있습니다.

   ![핵심 구성 요소](/help/forms/assets/theme-component.png)

   테마 편집기에서 특정 구성 요소의 스타일을 지정하려면 테마 폴더에서 CSS를 편집할 수 있습니다. 예를 들어 텍스트 상자 필드의 테두리 색상을 변경하려면 편집기에서 CSS 파일을 열고 테두리 색상을 변경합니다.

   ![텍스트 상자 CSS 편집](/help/forms/assets/edit_color_textbox.png)

1. 파일을 저장하면 프록시 서버는 라인을 통해 변경 내용을 인식합니다 `[Browsersync] File event [change]`.

   ![프록시 브라우저 동기화](/help/forms/assets/browser_sync.png)

1. 로컬 프록시 서버의 브라우저로 다시 전환하면 변경 내용이 즉시 표시됩니다.

   ![AF 테마 변경](/help/forms/assets/edit_theme_af.png)

테마 디자이너는 로컬 프록시 서버의 변경 내용을 미리 보고 다양한 AEM 구성 요소에 대한 요구 사항에 따라 테마를 사용자 지정합니다.

변경 사항을 AEM Git 저장소에 커밋하기 전에 [Git 저장소 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git).

### 7. 변경 사항을 커밋합니다. {#committing-the-changes}

테마를 변경하고 로컬 프록시 서버로 테스트한 후 변경 내용을 AEM Forms Cloud Service의 Git 저장소에 커밋합니다. 적응형 Forms 작성자가 사용할 수 있도록 Forms Cloud Service 환경에서 맞춤화된 테마를 사용할 수 있습니다.

AEM Forms Cloud Service의 Git 저장소에 변경 사항을 커밋하기 전에 로컬 컴퓨터에 리포지토리의 복제본이 필요합니다. 저장소를 복제하려면 다음을 수행하십시오.

1. 을(를) 클릭하여 새 테마 저장소를 만듭니다 **[!UICONTROL 저장소]** 옵션을 선택합니다.

   ![새 테마 저장소 만들기](/help/forms/assets/createrepo_canvastheme.png)

1. 클릭 **[!UICONTROL 저장소 추가]** 및 지정 **저장소 이름** 다음에서 **저장소 추가** 대화 상자. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![캔버스 테마 저장소 추가](/help/forms/assets/addcanvasthemerepo.png)

1. 클릭 **[!UICONTROL 저장소 URL 복사]** 생성된 저장소의 URL을 복사합니다.

   ![캔버스 테마 URL](/help/forms/assets/copyurl_canvastheme.png)

1. 명령 프롬프트를 열고 위에서 만든 클라우드 저장소를 복제합니다.

   ```
   git clone https://git.cloudmanager.adobe.com/aemforms/Canvasthemerepo/
   ```

1. 다음과 유사한 명령을 사용하여 편집 중인 테마 저장소의 파일을 클라우드 저장소로 이동합니다.
   `cp -r [source-theme-folder]/* [destination-cloud-repo]`
예를 들어 이 명령을 사용합니다 `cp -r [C:/cloned-git-canvas/*] [C:/cloned-repo]`
1. 클라우드 저장소의 디렉터리에서 다음 명령을 사용하여 이동한 테마 파일을 커밋합니다.

   ```text
   git add .
   git commit -a -m "Adding theme files"
   git push
   ```

1. 맞춤화는 Git 저장소에 푸시됩니다.

   ![변경 내용 커밋됨](/help/forms/assets/cmd_git_push.png)

이제 맞춤화는 Git 저장소에 안전하게 저장됩니다.


### 8. 프론트엔드 파이프라인 실행 {#deploy-pipeline}

1. 프론트엔드 파이프라인을 만들어 맞춤화된 테마를 배포합니다. 학습 [맞춤화된 테마를 배포하기 위해 최전선 파이프라인을 설정하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline).
1. 생성된 프론트엔드 파이프라인을 실행하여 아래에 맞춤화된 테마 폴더를 배포합니다. **[!UICONTROL 스타일]** 적응형 양식 만들기 마법사의 탭입니다.

>[!NOTE]
>
>나중에 캔버스 테마 폴더에서 수정하는 경우 위의 파이프라인을 다시 실행해야 합니다. 따라서 파이프라인의 이름을 기억해야 합니다.

## 테마 맞춤화 예제 {#example-to-customize-a-theme}

1. AEM Forms 작성자 인스턴스에 로그인합니다.
1. 핵심 구성 요소를 사용하여 만든 적응형 양식을 엽니다.
1. 명령 프롬프트를 사용하여 로컬 프록시 서버를 시작하고 **로컬로 로그인(관리 작업만 해당)**.
1. 로그인하고 나면 브라우저로 리디렉션되고 적용된 테마가 표시됩니다.
1. 다운로드 [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas) 다운로드한 zip 폴더의 압축을 풉니다.
1. 원하는 편집기에서 추출한 zip 폴더를 엽니다.
1. 만들기 `.env` 테마 폴더의 파일을 만들고 매개 변수를 추가합니다. **AEM URL**, **AEM_ADAPTIVE_FORM** 및 **AEM_PROXY_PORT**.
1. 캔버스 테마 폴더에서 텍스트 상자의 CSS 파일을 열고 테두리 색을 변경하여 다음과 같이 합니다. `red` 색상을 지정하고 변경 사항을 저장합니다.
1. 브라우저를 다시 열면 변경 사항이 즉시 적응형 양식에 반영됩니다.
1. 복제된 저장소의 캔버스 테마 폴더를 이동합니다.
1. 변경 사항을 커밋하고 프론트엔드 파이프라인을 실행합니다.

파이프라인이 실행되면 스타일 탭에서 테마를 사용할 수 있습니다.

## 우수 사례 {#best-practices}

* **다른 테마에서 에셋 피하기**

  테마를 편집할 때 다른 테마의 에셋(예: 이미지)을 찾아보고 추가할 수 있습니다. 예를 들어 페이지의 배경을 편집하는 경우 예를 들어 다음을 선택할 경우 **[!UICONTROL 페이지]** ![편집 단추](assets/edit-button.png)> **[!UICONTROL 배경]** > **[!UICONTROL 추가]** > **[!UICONTROL 이미지]**&#x200B;다른 테마의 이미지를 찾아보고 추가할 수 있는 대화 상자가 표시됩니다.

  자산이 다른 테마에서 추가되고 다른 테마가 이동 또는 삭제되는 경우 현재 테마와 관련된 문제에 직면할 수 있습니다. 다른 테마에서 에셋을 찾아보거나 추가하지 않는 것이 좋습니다.

* **컨테이너 패널 레이아웃 폭 변경**

  컨테이너 패널 레이아웃 너비는 변경하지 않는 것이 좋습니다. 컨테이너 패널의 너비를 지정하면 정적 패널이 되어 다른 디스플레이에 맞게 조정되지 않습니다.

* **머리글 및 바닥글 작업에 양식 편집기 또는 테마 편집기 사용**

  글꼴 스타일, 배경 및 투명도와 같은 스타일 옵션을 사용하여 머리글과 바닥글의 스타일을 지정하려면 테마 편집기를 사용하십시오.
로고 이미지, 머리글에 회사 이름, 바닥글에 저작권 정보 등의 정보를 제공하려면 양식 편집기 옵션을 사용합니다.
