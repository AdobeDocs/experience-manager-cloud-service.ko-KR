---
title: 적응형 Forms에서 테마를 만들고 사용하려면 어떻게 해야 합니까?
description: 테마를 사용하여 스타일을 지정하고 핵심 구성 요소를 사용하여 적응형 양식에 시각적 ID를 제공할 수 있습니다. 여러 적응형 Forms에서 테마를 공유할 수 있습니다.
keywords: 적응형 양식 스타일 지정 핵심 구성 요소. 핵심 구성 요소에서 테마 사용, 적응형 양식 스타일 지정, 테마 맞춤화
feature: Adaptive Forms, Core Components
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '2879'
ht-degree: 5%

---


# 테마를 사용하여 적응형 Forms 기반의 핵심 구성 요소 스타일 지정{#themes-for-af-using-core-components}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | 이 문서 |

테마를 만들고 적용하여 적응형 양식의 스타일을 지정할 수 있습니다. 테마에는 구성 요소 및 패널에 대한 스타일 지정 세부 사항이 포함되어 있습니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬과 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일은 해당 구성 요소에 반영됩니다. 테마는 적응형 양식에 대한 참조 없이 독립적으로 관리되며 여러 적응형 Forms에서 재사용할 수 있습니다.

이 문서에서는 테마를 사용하여 핵심 구성 요소 기반 적응형 Forms에 대한 사용자 지정 디자인을 디자인하는 방법을 알아봅니다.

## 스타일링 핵심 구성 요소에 사용할 수 있는 테마

Cloud Service으로서의 Forms은 적응형 Forms 기반의 핵심 구성 요소에 대해 아래에 나열된 테마를 제공합니다.

* [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND 테마](https://github.com/adobe/aem-forms-theme-wknd)
* [이젤 테마](https://github.com/adobe/aem-forms-theme-easel)

## 테마의 구조 이해

테마는 CSS 파일, JavaScript 파일 등의 스타일 구성 요소와 적응형 Forms의 스타일을 정의하는 리소스(예: 아이콘)가 포함된 패키지입니다. 적응형 양식 테마는 다음 구성 요소로 구성된 특정 조직을 따릅니다.

* `src/theme.scss`: 이 폴더에는 전체 테마에 광범위한 영향을 주는 CSS 파일이 포함되어 있습니다. 중앙 집중식 위치 역할을 하여 테마의 스타일 및 동작을 정의하고 관리할 수 있습니다. 이 파일을 편집하여 테마 전체에 공통으로 적용되는 변경 내용을 적용할 수 있으며, 이 변경 내용은 적응형 Forms 및 AEM Sites 페이지 모두의 모양 및 기능에 영향을 줍니다.

* `src/site`: 이 폴더에는 전체 AEM 사이트의 페이지에 적용되는 CSS 파일이 포함되어 있습니다. 이러한 파일은 AEM 사이트 페이지의 전체 기능 및 레이아웃에 영향을 주는 코드와 스타일로 구성됩니다. 여기서 수정한 사항은 사이트의 모든 페이지에 반영됩니다. [언제 사용하시겠습니까?]

* `src/components`: 이 폴더의 CSS 파일은 개별 AEM 핵심 구성 요소용으로 디자인되었습니다. 구성 요소의 각 전용 폴더에는 적응형 양식 내에서 특정 구성 요소를 스타일링하는 `.scss` 파일이 포함되어 있습니다. 예를 들어 /src/components/accordion/_accordion.scss 파일에는 적응형 Forms 아코디언 구성 요소에 대한 스타일 정보가 들어 있습니다.

  ![적응형 양식 기반 테마 구조](/help/forms/assets/theme_structure.png)

* `src/resources`: 이 폴더에는 아이콘, 로고 및 글꼴과 같은 정적 파일이 포함되어 있습니다. 이러한 리소스는 테마의 시각적 요소와 전반적인 디자인을 개선하는 데 사용됩니다.

## 테마 만들기

Forms as Cloud Service은 적응형 Forms 기반 핵심 구성 요소에 대한 적응형 양식 스타일 테마를 아래에 나열했습니다.

* [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND 테마](https://github.com/adobe/aem-forms-theme-wknd)
* [이젤 테마](https://github.com/adobe/aem-forms-theme-easel)

[이러한 테마를 사용자 지정하여 새 테마를 만들 수 있습니다](#customize-a-theme-core-components).

![테마 맞춤화의 워크플로](/help/forms/assets/workflow-of-customization-of-theme.png)

## 테마 맞춤화 {#customize-a-theme-core-components}

테마 맞춤화란 테마의 모양을 수정하고, 스타일링하고, 개인화하는 프로세스를 말합니다. 테마를 사용자 지정할 때 해당 디자인 요소, 레이아웃, 색상, 타이포그래피 및 경우에 따라 기본 코드가 변경됩니다. 테마가 제공하는 기본 구조와 기능을 유지하면서 웹 사이트 또는 애플리케이션에 고유하고 맞춤화된 디자인을 만들 수 있습니다.

### 사전 요구 사항 {#prerequisites-to-customize}

* [Cloud Manager에서 파이프라인 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)에 대해 잘 알고 있으며 파이프라인 설정 방법에 대한 기본 지식이 있으면 테마 맞춤화를 효율적으로 관리하고 배포하는 데 도움이 됩니다.
* [기여자 역할로 사용자를 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html)하는 방법을 알아봅니다. 기여자 역할이 있는 사용자를 구성하는 방법을 이해하면 테마 맞춤화에 필요한 권한을 부여할 수 있습니다.
* [Apache Maven의 최신 릴리스를 설치하십시오.](https://maven.apache.org/download.cgi) Apache Maven은 일반적으로 Java™ 프로젝트에 사용되는 빌드 자동화 도구입니다. 최신 릴리스를 설치하면 테마 맞춤화에 필요한 종속성이 확보됩니다.
* 일반 텍스트 편집기를 설치합니다. 예를 들어 Microsoft® Visual Studio Code입니다. Microsoft® 같은 일반 텍스트 편집기를 사용하면 Visual Studio Code에서 테마 파일을 편집하고 수정할 수 있는 사용자 친화적인 환경을 제공합니다.

### 환경 설정

* 로컬 개발 및 Cloud Service 환경에 대해 [적응형 Forms 핵심 구성 요소를 활성화](/help/forms/enable-adaptive-forms-core-components.md).
* Cloud Service 환경에 대해 [프론트엔드 배포 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html)을 구성하십시오. 또는 나중에 파이프라인을 구성할 수 있으므로 배포 파이프라인을 설정하기 전에 테스트 및 테마 세분화의 우선 순위를 지정할 수 있습니다.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

전제 조건을 학습하고 개발 환경을 구성한 후에는 특정 요구 사항에 따라 테마를 맞춤화하거나 스타일링할 준비가 되었습니다.

### 테마 맞춤화 {#steps-to-customize-a-theme-core-components}

테마 맞춤화는 여러 단계로 진행됩니다. 테마를 사용자 정의하려면 나열된 순서대로 단계를 수행합니다.

1. [테마 복제](#download-a-theme-core-components)
1. [테마 이름 설정](#set-name-of-theme)
1. [테마 맞춤화](#customize-the-theme)
1. [테마 테스트](#test-the-theme)
1. [테마 배포](#deploy-the-theme)

문서에 제공된 예제는 **캔버스** 테마를 기반으로 하지만 모든 테마를 복제하고 동일한 지침을 사용하여 사용자 지정할 수 있습니다. 이러한 지침은 모든 테마에 적용되므로 특정 요구 사항에 따라 테마를 수정할 수 있습니다.

테마를 사용하여 핵심 구성 요소 기반 적응형 Forms에 대한 브랜드 경험을 만드는 프로세스부터 시작하겠습니다.

#### 1. 테마 복제 {#download-a-theme-core-components}

적응형 Forms 기반의 핵심 구성 요소에 대한 테마를 복제하려면 다음 테마 중 하나를 선택하십시오.

* [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND 테마](https://github.com/adobe/aem-forms-theme-wknd)
* [이젤 테마](https://github.com/adobe/aem-forms-theme-easel)

테마를 복제하려면 다음 지침을 수행하십시오.

1. 로컬 개발 환경에서 명령 프롬프트 또는 터미널 창을 엽니다.

1. `git clone` 명령을 실행하여 테마를 복제합니다.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   테마의 Git 저장소의 [경로]를 테마의 해당 Git 저장소의 실제 URL로 바꿉니다

   예를 들어 캔버스 테마를 복제하려면 다음 명령을 실행합니다.

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   명령을 성공적으로 실행한 후에는 `aem-forms-theme-canvas` 폴더의 컴퓨터에서 테마의 로컬 복사본을 사용할 수 있습니다.


#### 2. 테마 이름 설정 {#set-name-of-theme}

1. IDE에서 테마 폴더를 엽니다. 예를들어 Visual Studio 코드 편집기에서 `aem-forms-theme-canvas` 폴더를 열려면

1. `aem-forms-theme-canvas` 폴더로 이동합니다.

1. 다음 명령을 실행합니다.

   ```
      code .
   ```

   ![일반 텍스트 편집기에서 테마 폴더를 엽니다](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   Visual Studio 코드에서 폴더가 열립니다.

1. 편집할 `package.json` 페이지를 엽니다.

1. `name` 및 `version` 특성에 대한 값을 설정하십시오.

   ![캔버스 테마 이름 변경 이미지](/help/forms/assets/changename_canvastheme.png)

   >[!NOTE]
   >
   > * 이름 특성은 테마를 고유하게 식별하는 데 사용되며 지정된 이름은 **양식 만들기 마법사**&#x200B;의 **스타일** 탭에 표시됩니다.
   > * 선택에 따라 테마 이름을 선택할 수 있습니다(예: `mytheme` 또는 `customtheme`). 그러나 이 경우 이름을 `aem-forms-wknd-theme`(으)로 지정했습니다.

1. 편집할 `package-lock.json` 페이지를 엽니다.
1. `name` 및 `version` 특성에 대한 값을 설정하십시오. `Package-lock`.json 파일의 `name` 및 `version` 특성 값이 `Package.json` 파일의 값과 일치하는지 확인하십시오.

   ![캔버스 테마 이름 변경 이미지](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (선택 사항) 편집할 `ReadMe` 파일을 열고 테마 이름을 업데이트합니다.

   ![캔버스 테마 이름 변경 이미지](/help/forms/assets/changename_canvastheme-readme-file.png)

1. 파일을 저장하고 닫습니다.

**테마 이름을 설정하는 동안 고려 사항**

* `Package.json` 파일 및 `Package-lock.json` 파일의 테마 이름에서 `@aemforms`을(를) 제거해야 합니다. 맞춤화된 테마 이름에서 `@aemforms`을(를) 제거하지 못하면 테마를 배포하는 동안 프론트엔드 파이프라인이 실패합니다.
* `Package.json` 파일 및 `Package-lock.json` 파일의 `version` 테마를 업데이트하여 테마에 대한 시간 경과에 따른 변경 내용 및 개선 사항을 정확하게 반영하는 것이 좋습니다.
* 사용 방법, 설치 지침 및 기타 관련 세부 정보를 보려면 `ReadMe` 파일의 테마 이름을 업데이트하는 것이 좋습니다.

#### 3. 테마 맞춤화 {#customize-the-theme}

개별 구성 요소를 사용자 지정하거나 테마의 전역 변수를 사용하여 테마 수준을 변경할 수 있습니다. 전역 변수에 대한 변경 사항은 모든 개별 구성 요소에 영향을 줍니다. 예를 들어, 전역 변수를 사용하여 적응형 양식의 모든 구성 요소의 테두리 색상을 변경하고 밝은 채우기 색상을 사용하여 버튼 구성 요소를 사용하여 CTA(콜 투 액션)를 설정할 수 있습니다.

* [테마 수준 스타일 설정](#theme-customization-global-level)

* [구성 요소 수준 스타일 설정](#component-based-customization)

##### 테마 수준 스타일 설정{#theme-customization-global-level}

`variable.scss` 파일에 테마의 전역 변수가 포함되어 있습니다. 이러한 변수를 업데이트하여 테마 수준에서 스타일 관련 변경 사항을 적용할 수 있습니다. 테마 수준 스타일을 적용하려면 다음 단계를 수행합니다.

1. 편집할 `<your-theme-sources>/src/site/_variables.scss` 페이지를 엽니다.
1. 모든 속성의 값을 변경합니다. 예를 들어 기본 오류 색상은 `red`입니다. 오류 색상을 `red`에서 `blue`(으)로 변경하려면 `$errorvariable`의 색상 16진수 코드를 변경하십시오. 예: `$error: #196ee5`
1. 파일을 저장하고 닫습니다.

   ![테마 편집](/help/forms/assets/edit_theme.png)

마찬가지로 `variable.scss` 파일을 사용하여 글꼴 모음과 문자, 테마와 글꼴 색상, 글꼴 크기, 테마 간격, 오류 아이콘, 테마 테두리 스타일 및 여러 적응형 양식 구성 요소에 영향을 주는 더 많은 변수를 설정할 수 있습니다.

##### 구성 요소 수준 스타일 설정 {#component-based-customization}

특정 적응형 양식 핵심 구성 요소의 글꼴, 색상, 크기 및 기타 CSS 속성을 변경할 수도 있습니다. 예를 들어, 단추, 확인란, 컨테이너, 바닥글 등이 있습니다. 특정 구성 요소의 CSS 파일을 편집하여 버튼 또는 확인란의 스타일을 지정하여 조직의 스타일에 맞출 수 있습니다. 구성 요소의 스타일을 사용자 정의하려면 다음을 수행합니다.

1. 편집할 `<your-theme-sources>/src/components/<component>/<component.scss>` 파일을 엽니다. 예를 들어 단추 구성 요소의 글꼴 색을 변경하려면 `<your-theme-sources>/src/components/button/button.scss` 파일을 엽니다.
1. 요구 사항에 따라 의 값을 변경합니다. 예를 들어 마우스로 가리키면 단추 구성 요소의 색상을 `green`(으)로 변경하려면 `cmp-adaptiveform-button__widget:hover` 클래스의 `color: $white` 속성 값을 16진수 코드 `#12B453` 또는 `green`의 다른 음영으로 변경합니다. 최종 코드는 다음과 같습니다.

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. 파일을 저장하고 닫습니다.

   ![텍스트 상자 CSS 편집](/help/forms/assets/edit_color_textbox.png)

   >
   >
   > 테마 및 구성 요소 수준에서 스타일이 정의되면 구성 요소 수준에서 정의된 스타일이 우선합니다.

#### 4. 맞춤화된 테마 테스트 {#test-the-theme}

로컬 환경에서 변경 사항을 미리 보고 테스트하고, 다른 AEM 구성 요소에 대한 요구 사항에 따라 테마를 사용자 정의하려면 다음 단계를 수행하십시오.

* 4.1 [테스트를 위한 로컬 환경 구성](#rename-env-file-theme-folder)
* 4.2 [로컬 환경을 사용하여 테마 테스트](#start-a-local-proxy-server)

##### 4.1. 테스트를 위한 로컬 환경 구성 {#rename-env-file-theme-folder}

1. IDE에서 테마 폴더를 엽니다. 예를들어 Visual Studio 코드 편집기에서 `aem-forms-theme-canvas` 폴더를 엽니다.
1. `env_template` 파일의 이름을 테마 폴더의 `.env` 파일로 바꾸고 다음 매개 변수를 추가합니다.

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   예를들어, 양식의 URL은 `http://localhost:4502/editor.html/content/forms/af/contactusform.html`입니다. 따라서 의 값은 다음과 같습니다.

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. 파일을 저장합니다.

   ![캔버스 테마 구조](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 로컬 환경을 사용하여 테마 테스트 {#start-a-local-proxy-server}

1. 테마 폴더의 루트로 이동합니다. 이 경우 테마 폴더 이름은 `aem-forms-theme-canvas`입니다.
1. 명령 프롬프트 또는 터미널을 엽니다.
1. `npm install`을(를) 실행하여 종속성을 설치합니다.
1. `npm run live`을(를) 실행하여 로컬 브라우저에서 업데이트된 테마가 있는 양식을 미리 봅니다.

   >[!NOTE]
   >
   > `npm run live` 명령을 실행하는 동안 오류가 발생하면 `npm run live` 명령 앞에 다음 명령을 실행하십시오.
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

이는 최신 배포입니다. 따라서 변경 작업을 수행하고 `_variables.scss` 및 `button.scss` 파일을 저장할 때마다 서버는 자동으로 변경 내용을 선택하고 최신 출력을 미리 봅니다. `[Browsersync] File event [change]` 줄은 서버가 최신 변경 내용을 인식했으며 로컬 환경에 변경 내용을 배포하고 있음을 의미합니다.

![프록시 브라우저 동기화](/help/forms/assets/browser_sync.png)

테마 맞춤화에 대한 테마 수준과 구성 요소 수준 모두에서 적응형 양식(핵심 구성 요소)의 스타일을 지정하는 예제를 따랐으므로 적응형 양식의 오류 메시지는 `blue` 색상으로 변경되고, 마우스로 가리키면 단추 구성 요소의 레이블 색상은 `green` 색상으로 변경됩니다.

**테마 수준 스타일 미리 보기**

![예: 파란색으로 설정된 오류 색상](/help/forms/assets/theme-level-changes.png)

**구성 요소 수준 스타일 미리 보기**

![예: 가리킨 색상이 녹색으로 설정됨](/help/forms/assets/button-customization.png)

테마를 맞춤화하면 조직 요구 사항에 따라 핵심 구성 요소 기반 적응형 Forms에 대한 맞춤형 룩을 디자인할 수 있습니다.

###### Cloud Service 환경에서 호스팅되는 양식의 테마 테스트

AEM Forms as a Cloud Service 인스턴스에서 호스팅된 적응형 양식에 대한 테마를 테스트할 수도 있습니다. 클라우드 인스턴스에서 호스팅된 적응형 Forms을 사용하여 테마를 테스트하기 위한 로컬 환경을 구성하고 설정하려면 다음 단계를 수행하십시오.

1. IDE에서 테마 폴더를 엽니다. 예를들어 Visual Studio 코드 편집기에서 `aem-forms-theme-canvas` 폴더를 엽니다.
1. `env_template` 파일의 이름을 `.env` 파일로 바꾸고 다음 매개 변수를 추가합니다.

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   예를 들어 클라우드 환경에서 양식의 URL은 `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`입니다. 따라서 의 값은 다음과 같습니다.

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. 파일을 저장합니다.
1. 로컬 사용자를 만듭니다.

   >[!NOTE]
   >
   > 로컬 사용자를 만들려면 다음 작업을 수행하십시오.
   >
   > * **[!UICONTROL AEM 홈]** > **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL 사용자]**(으)로 이동합니다.
   > * 사용자가 `forms-users` 그룹의 구성원인지 확인하십시오.

1. 테마 폴더의 루트로 이동합니다. 이 경우 테마 폴더 이름은 `aem-forms-theme-canvas`입니다.
1. `npm run live`을(를) 실행하면 로컬 브라우저로 리디렉션됩니다.
1. `SIGN IN LOCALLY (ADMIN TASKS ONLY)`을(를) 클릭하고 로컬 사용자의 자격 증명을 사용하여 로그인합니다.

적응형 양식에 최신 변경 사항을 미리 볼 수 있습니다. 테마 폴더에서 수정한 사항에 만족하면 프론트엔드 파이프라인을 사용하여 테마를 AEM Cloud Service 환경에 배포합니다.

#### 5. 테마 배포 {#deploy-the-theme}

프론트엔드 파이프라인을 사용하여 테마를 Cloud Service 환경에 배포하려면 다음을 수행하십시오.

* 5.1 [테마에 대한 저장소 만들기](#create-a-new-theme-repo)
* 5.2 [변경 내용을 리포지토리에 푸시](#committing-the-changes)
* 5.3 [프론트엔드 파이프라인 실행](#run-a-frontend-pipeline)

##### 5.1 테마를 위한 저장소 만들기{#create-a-new-theme-repo}

테마를 배포하려면 저장소가 필요합니다. [AEM Cloud Manager 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)에 로그인하고 테마에 대한 새 저장소를 추가하십시오.

1. **[!UICONTROL 저장소]** > **[!UICONTROL 저장소 추가]**&#x200B;를 클릭하여 테마에 대한 새 저장소를 만듭니다.

   ![새 테마 저장소 만들기](/help/forms/assets/createrepo_canvastheme.png)


1. **저장소 추가** 대화 상자에서 **저장소 이름**&#x200B;을 지정하십시오. 예를 들어 제공된 이름은 `custom-canvas-theme-repo`입니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![캔버스 테마 저장소 추가](/help/forms/assets/addcanvasthemerepo.png)

1. **[!UICONTROL 저장소 URL 복사]**&#x200B;를 클릭하여 저장소의 URL을 복사합니다.

   ![캔버스 테마 URL](/help/forms/assets/copyurl_canvastheme.png)

   >[!NOTE]
   > 
   > * 여러 테마에 단일 저장소를 사용할 수 있습니다.
   > * 다른 테마를 배포하려면 별도의 프론트엔드 파이프라인을 만들어야 합니다.
   >* 예를 들어 캔버스 테마, WKND 테마 및 EASEL 테마에 대해 `custom-canvas-theme-repo`과(와) 동일한 리포지토리를 사용할 수 있습니다. 그러나 테마를 배포하려면 별도의 프론트엔드 파이프라인을 만들어야 합니다. 특정 테마에 대한 향후 사용자 지정은 해당 프론트엔드 파이프라인을 사용하여 배포됩니다.

##### 5.2. 변경 사항을 저장소에 푸시합니다. {#committing-the-changes}

이제 변경 사항을 AEM Forms Cloud Service의 테마 저장소에 푸시합니다.

1. 테마 폴더의 루트로 이동합니다.  이 경우 테마 폴더 이름은 `aem-forms-theme-canvas`입니다.
1. 명령 프롬프트 또는 터미널을 엽니다.
1. 다음 명령을 나열된 순서로 실행합니다.

   ```
   git remote add [alias-name-for-repository] [URL of repository]
   git add .
   git commit
   git push [name-for-createdrepository]
   ```

   예:

   ```
   git remote add canvascloudthemerepo https://git.cloudmanager.adobe.com/stage-aemformsdev/customcanvastheme/
   git add .
   git commit
   git push canvascloudthemerepo 
   ```

   ![변경 내용 커밋됨](/help/forms/assets/cmd_git_push.png)



##### 5.3 프론트엔드 파이프라인 실행 {#run-a-frontend-pipeline}

테마는 [프론트엔드 파이프라인을 사용하여 배포됩니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). 테마를 배포하려면 다음 단계를 수행하십시오.

1. AEM Cloud Manager 저장소에 로그인합니다.
1. **[!UICONTROL 파이프라인]** 섹션에서 **[!UICONTROL 추가]** 단추를 클릭합니다.
1. Cloud Service 환경에 따라 **[!UICONTROL 비프로덕션 파이프라인 추가]** 또는 **[!UICONTROL 프로덕션 파이프라인 추가]**&#x200B;를 선택합니다. 예를 들어 **[!UICONTROL 프로덕션 파이프라인 추가]** 옵션이 선택되어 있습니다.
1. **[!UICONTROL 구성]** 단계의 일부로 **[!UICONTROL 프로덕션 파이프라인 추가]** 대화 상자에서 파이프라인의 이름을 지정합니다. 예를 들어 파이프라인 이름은 `customcanvastheme`입니다.
1. **[!UICONTROL 계속]**&#x200B;을 클릭합니다.
1. 다음 위치에서 **[!UICONTROL 타깃팅된 배포]** > **[!UICONTROL 프론트엔드 코드]** 옵션을 선택하십시오.
**[!UICONTROL Source 코드]** 단계.
1. 최신 변경 사항이 있는 **[!UICONTROL 저장소]** 및 **[!UICONTROL Git 분기]** 값을 선택하십시오. 예를 들어 선택한 저장소 이름은 `custom-canvas-theme-repo`이고 Git 분기는 `main`입니다.
1. 변경 내용이 루트 폴더에 있는 경우 **[!UICONTROL 코드 위치]**&#x200B;을(를) `/`(으)로 선택합니다.
1. **[!UICONTROL 저장]**을 클릭합니다.
   ![프론트엔드 파이프라인 만들기](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   파이프라인 설정이 완료되면 콜 투 액션 카드가 업데이트됩니다.

1. 생성된 파이프라인을 마우스 오른쪽 버튼으로 클릭합니다.
1. **[!UICONTROL 실행]** 을 클릭합니다.

   ![run-a-pipleine](/help/forms/assets/canvas-theme-run-pipeline.png)

빌드가 완료되면 작성자 인스턴스에서 테마를 사용할 수 있습니다. 적응형 양식을 만드는 동안 적응형 양식 만들기 마법사의 **[!UICONTROL 스타일]** 탭에 나타납니다.

![스타일 탭에서 사용할 수 있는 사용자 지정 테마](/help/forms/assets/custom-theme-style-tab.png)

맞춤화된 테마는 핵심 구성 요소 기반 적응형 Forms에 대한 브랜드 경험을 만드는 데 도움이 됩니다.

## 적응형 양식에 테마 적용 {#using-theme-in-adaptive-form}

적응형 양식에 테마를 적용하는 단계는 다음과 같습니다.

1. AEM Forms 작성자 인스턴스에 로그인합니다.

1. **Adobe Experience Manager** > **Forms** > **Forms 및 문서**&#x200B;를 선택합니다.

1. **만들기** > **적응형 Forms**&#x200B;을 클릭합니다. 적응형 양식 만들기 마법사가 열립니다.

1. **Source** 탭에서 핵심 구성 요소 템플릿을 선택합니다.
1. **스타일** 탭에서 테마를 선택합니다.
1. **만들기**&#x200B;를 클릭합니다.

적응형 양식 테마는 적응형 양식을 작성하는 동안 스타일을 정의하는 적응형 양식 템플릿의 일부로 사용됩니다.

## 모범 사례 {#best-practices}

* **다른 테마에서 자산 사용 안 함**

  테마를 편집할 때 다른 테마의 에셋(예: 이미지)을 찾아보고 추가할 수 있습니다. 예를 들어 페이지의 배경을 편집하는 경우 예를 들어 **[!UICONTROL 페이지]** ![편집 단추](assets/edit-button.png)> **[!UICONTROL 배경]** > **[!UICONTROL 추가]** > **[!UICONTROL 이미지]**&#x200B;를 선택하면 다른 테마의 이미지를 찾아보고 추가할 수 있는 대화 상자가 표시됩니다.

  자산이 다른 테마에서 추가되고 다른 테마가 이동 또는 삭제되는 경우 현재 테마와 관련된 문제에 직면할 수 있습니다. 다른 테마에서 에셋을 찾아보거나 추가하지 않는 것이 좋습니다.

* **컨테이너 패널 레이아웃 너비 변경**

  컨테이너 패널 레이아웃 너비는 변경하지 않는 것이 좋습니다. 컨테이너 패널의 너비를 지정하면 정적 패널이 되어 다른 디스플레이에 맞게 조정되지 않습니다.

* **머리글 및 바닥글 작업에 양식 편집기 또는 테마 편집기 사용**

  글꼴 스타일, 배경 및 투명도와 같은 스타일 옵션을 사용하여 머리글과 바닥글의 스타일을 지정하려면 테마 편집기를 사용하십시오.
로고 이미지, 머리글에 회사 이름 및 바닥글에 저작권 정보와 같은 정보를 제공하려면 양식 편집기 옵션을 사용합니다.

## 자주 묻는 질문 {#faq}

**Q:** 글로벌 수준과 구성 요소 수준 모두에서 테마 폴더를 사용자 지정할 때 우선 순위가 높은 사용자 지정은 무엇입니까?

**Ans:** 전역 수준과 구성 요소 수준 모두에서 사용자 지정이 이루어지면 구성 요소 수준의 사용자 지정이 우선합니다.

<!--

## See next

* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generate Document of Record for Adaptive Forms (Core Components](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Create an Adaptive Forms with Repeatable sections](/help/forms/create-forms-repeatable-sections.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)


>[!MORELIKETHIS]
>
>* [Enable Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment](/help/forms/enable-adaptive-forms-core-components.md)

-->


## 추가 참조 {#see-also}

{{see-also}}
* [다양한 화면 크기 및 장치 유형에 대한 양식 레이아웃 설정](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [적응형 Forms(핵심 구성 요소)를 위한 기록 문서 생성](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [반복 가능한 섹션이 포함된 적응형 Forms 만들기](/help/forms/create-forms-repeatable-sections.md)
* [샘플 테마 템플릿 및 양식 데이터 모델](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)
* [AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 양식 핵심 구성 요소 활성화](/help/forms/enable-adaptive-forms-core-components.md)
