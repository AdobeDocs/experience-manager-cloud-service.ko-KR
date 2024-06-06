---
title: 적응형 Forms에서 테마를 만들고 사용하려면 어떻게 해야 합니까?
description: 테마를 사용하여 스타일을 지정하고 핵심 구성 요소를 사용하여 적응형 양식에 시각적 ID를 제공할 수 있습니다. 여러 적응형 Forms에서 테마를 공유할 수 있습니다.
keywords: 적응형 양식 스타일 지정 핵심 구성 요소. 핵심 구성 요소에서 테마 사용, 적응형 양식 스타일 지정, 테마 맞춤화
feature: Adaptive Forms, Core Components
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: aca3508d85a0382f679a8fa0ca986cfd13ee793b
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

테마는 CSS 파일, JavaScript 파일 등의 스타일 구성 요소 및 적응형 Forms의 스타일을 정의하는 리소스(예: 아이콘)가 포함된 패키지입니다. 적응형 양식 테마는 다음 구성 요소로 구성된 특정 조직을 따릅니다.

* `src/theme.scss`: 이 폴더에는 전체 테마에 광범위한 영향을 주는 CSS 파일이 포함되어 있습니다. 중앙 집중식 위치 역할을 하여 테마의 스타일 및 동작을 정의하고 관리할 수 있습니다. 이 파일을 편집하여 테마 전체에 공통으로 적용되는 변경 내용을 적용할 수 있으며, 이 변경 내용은 적응형 Forms 및 AEM Sites 페이지 모두의 모양 및 기능에 영향을 줍니다.

* `src/site`: 이 폴더에는 전체 AEM 사이트의 페이지에 적용되는 CSS 파일이 포함되어 있습니다. 이러한 파일은 AEM 사이트 페이지의 전체 기능 및 레이아웃에 영향을 주는 코드와 스타일로 구성됩니다. 여기서 수정한 사항은 사이트의 모든 페이지에 반영됩니다. [언제 사용해야 합니까?]

* `src/components`: 이 폴더의 CSS 파일은 개별 AEM 핵심 구성 요소용으로 설계되었습니다. 구성 요소의 각 전용 폴더에는 `.scss` 적응형 양식 내에서 특정 구성 요소의 스타일을 지정하는 파일입니다. 예를 들어 /src/components/accordion/_accordion.scss 파일에는 적응형 Forms 아코디언 구성 요소에 대한 스타일 정보가 들어 있습니다.

  ![적응형 양식 기반 테마 구조](/help/forms/assets/theme_structure.png)

* `src/resources`: 이 폴더에는 아이콘, 로고 및 글꼴과 같은 정적 파일이 포함되어 있습니다. 이러한 리소스는 테마의 시각적 요소와 전반적인 디자인을 개선하는 데 사용됩니다.

## 테마 만들기

Forms as Cloud Service은 적응형 Forms 기반 핵심 구성 요소에 대한 적응형 양식 스타일 테마를 아래에 나열했습니다.

* [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND 테마](https://github.com/adobe/aem-forms-theme-wknd)
* [이젤 테마](https://github.com/adobe/aem-forms-theme-easel)

다음을 수행할 수 있습니다. [다음 테마 중 하나를 사용자 지정하여 새 테마 만들기](#customize-a-theme-core-components).

![테마 맞춤화 워크플로](/help/forms/assets/workflow-of-customization-of-theme.png)

## 테마 맞춤화 {#customize-a-theme-core-components}

테마 맞춤화란 테마의 모양을 수정하고, 스타일링하고, 개인화하는 프로세스를 말합니다. 테마를 사용자 지정할 때 해당 디자인 요소, 레이아웃, 색상, 타이포그래피 및 경우에 따라 기본 코드가 변경됩니다. 테마가 제공하는 기본 구조와 기능을 유지하면서 웹 사이트 또는 애플리케이션에 고유하고 맞춤화된 디자인을 만들 수 있습니다.

### 사전 요구 사항 {#prerequisites-to-customize}

* 다음 내용에 대해 숙지하십시오. [Cloud Manager에서 파이프라인 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline) 또한 파이프라인 설정 방법에 대한 기본 지식을 갖추고 있으므로 테마 맞춤화를 효율적으로 관리하고 배포할 수 있습니다.
* 방법 알아보기 [기여자 역할이 있는 사용자 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html). 기여자 역할이 있는 사용자를 구성하는 방법을 이해하면 테마 맞춤화에 필요한 권한을 부여할 수 있습니다.
* 의 최신 릴리스 설치 [아파치 메이븐](https://maven.apache.org/download.cgi) Apache Maven은 Java™ 프로젝트에 일반적으로 사용되는 빌드 자동화 도구입니다. 최신 릴리스를 설치하면 테마 맞춤화에 필요한 종속성이 확보됩니다.
* 일반 텍스트 편집기를 설치합니다. 예를 들어 Microsoft® Visual Studio Code입니다. Microsoft® 같은 일반 텍스트 편집기를 사용하면 Visual Studio Code에서 테마 파일을 편집하고 수정할 수 있는 사용자 친화적인 환경을 제공합니다.

### 환경 설정

* [적응형 Forms 핵심 구성 요소 활성화](/help/forms/enable-adaptive-forms-core-components.md)  로컬 개발 및 Cloud Service 환경에 적합합니다.
* 구성 [프론트엔드 배포 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html) Cloud Service 환경용입니다. 또는 나중에 파이프라인을 구성할 수 있으므로 배포 파이프라인을 설정하기 전에 테스트 및 테마 세분화의 우선 순위를 지정할 수 있습니다.

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

이 문서에 제공된 예제는 **캔버스** 테마이지만 모든 테마를 복제하고 동일한 지침을 사용하여 맞춤화할 수 있습니다. 이러한 지침은 모든 테마에 적용되므로 특정 요구 사항에 따라 테마를 수정할 수 있습니다.

테마를 사용하여 핵심 구성 요소 기반 적응형 Forms에 대한 브랜드 경험을 만드는 프로세스부터 시작하겠습니다.

#### 1. 테마 복제 {#download-a-theme-core-components}

적응형 Forms 기반의 핵심 구성 요소에 대한 테마를 복제하려면 다음 테마 중 하나를 선택하십시오.

* [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND 테마](https://github.com/adobe/aem-forms-theme-wknd)
* [이젤 테마](https://github.com/adobe/aem-forms-theme-easel)

테마를 복제하려면 다음 지침을 수행하십시오.

1. 로컬 개발 환경에서 명령 프롬프트 또는 터미널 창을 엽니다.

1. 실행 `git clone` 테마를 복제하는 명령.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   바꾸기 [테마의 Git 저장소 경로] 해당 테마의 Git 저장소의 실제 URL 사용

   예를 들어 캔버스 테마를 복제하려면 다음 명령을 실행합니다.

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   명령을 성공적으로 실행한 후에는 컴퓨터의 시스템에서 테마의 로컬 복사본을 사용할 수 있습니다.  `aem-forms-theme-canvas` 폴더를 삭제합니다.


#### 2. 테마 이름 설정 {#set-name-of-theme}

1. IDE에서 테마 폴더를 엽니다. 예를 들어 를 열려면 `aem-forms-theme-canvas` 폴더가 표시됩니다.

1. `aem-forms-theme-canvas` 폴더로 이동합니다.

1. 다음 명령을 실행합니다.

   ```
      code .
   ```

   ![일반 텍스트 편집기에서 테마 폴더 열기](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   Visual Studio 코드에서 폴더가 열립니다.

1. 편집할 `package.json` 페이지를 엽니다.

1. 에 대한 값 설정 `name` 및 `version` 속성.

   ![캔버스 테마 이름 변경 이미지](/help/forms/assets/changename_canvastheme.png)

   >[!NOTE]
   >
   > * name 속성은 테마를 고유하게 식별하는 데 사용되며 지정된 이름은 **스타일** 의 탭 **양식 만들기 마법사**.
   > * 선택에 따라 테마 이름을 선택할 수 있는 옵션이 있습니다. 예를 들면 다음과 같습니다. `mytheme` 또는 `customtheme`. 그러나 이 경우 이름을 로 지정했습니다. `aem-forms-wknd-theme`.

1. 편집할 `package-lock.json` 페이지를 엽니다.
1. 에 대한 값 설정 `name` 및 `version` 속성. 다음에 대한 값이 `name` 및 `version` 의 속성 `Package-lock`.json 파일은 `Package.json` 파일.

   ![캔버스 테마 이름 변경 이미지](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (선택 사항) `ReadMe` 편집할 파일 및 테마 이름을 업데이트합니다.

   ![캔버스 테마 이름 변경 이미지](/help/forms/assets/changename_canvastheme-readme-file.png)

1. 파일을 저장하고 닫습니다.

**테마 이름을 설정하는 동안 고려 사항**

* 다음을 제거해야 합니다. `@aemforms` 의 테마 이름에서 `Package.json` 파일 및 `Package-lock.json` 파일. 이 경우 제거하지 못했습니다. `@aemforms` 맞춤화된 테마 이름에서 테마 배포 중 프론트엔드 파이프라인이 실패합니다.
* 테마를 업데이트하는 것이 좋습니다 `version` 위치: `Package.json` 파일 및 `Package-lock.json` 시간에 따른 테마 변경 및 개선 사항을 정확하게 반영하기 위한 파일입니다.
* 사용 방법, 설치 지침 및 기타 관련 세부 정보에 대한 중요한 정보는에서 테마 이름을 업데이트하는 것이 좋습니다. `ReadMe` 파일.

#### 3. 테마 맞춤화 {#customize-the-theme}

개별 구성 요소를 사용자 지정하거나 테마의 전역 변수를 사용하여 테마 수준을 변경할 수 있습니다. 전역 변수에 대한 변경 사항은 모든 개별 구성 요소에 영향을 줍니다. 예를 들어, 전역 변수를 사용하여 적응형 양식의 모든 구성 요소의 테두리 색상을 변경하고 밝은 채우기 색상을 사용하여 버튼 구성 요소를 사용하여 CTA(콜 투 액션)를 설정할 수 있습니다.

* [테마 수준 스타일 설정](#theme-customization-global-level)

* [구성 요소 수준 스타일 설정](#component-based-customization)

##### 테마 수준 스타일 설정{#theme-customization-global-level}

다음 `variable.scss` 파일에는 테마의 전역 변수가 포함되어 있습니다. 이러한 변수를 업데이트하여 테마 수준에서 스타일 관련 변경 사항을 적용할 수 있습니다. 테마 수준 스타일을 적용하려면 다음 단계를 수행합니다.

1. 편집할 `<your-theme-sources>/src/site/_variables.scss` 페이지를 엽니다.
1. 모든 속성의 값을 변경합니다. 예를 들어 기본 오류 색상은 `red`. 오류 색상을 변경하려면 `red` 끝 `blue`, 의 색상 16진수 코드 변경 `$errorvariable`. 예: `$error: #196ee5`
1. 파일을 저장하고 닫습니다.

   ![테마 편집](/help/forms/assets/edit_theme.png)

마찬가지로 `variable.scss` 글꼴 모음 및 유형, 테마 및 글꼴 색상, 글꼴 크기, 테마 간격, 오류 아이콘, 테마 테두리 스타일 및 여러 적응형 양식 구성 요소에 영향을 주는 더 많은 변수를 설정할 파일입니다.

##### 구성 요소 수준 스타일 설정 {#component-based-customization}

특정 적응형 양식 핵심 구성 요소의 글꼴, 색상, 크기 및 기타 CSS 속성을 변경할 수도 있습니다. 예를 들어, 단추, 확인란, 컨테이너, 바닥글 등이 있습니다. 특정 구성 요소의 CSS 파일을 편집하여 버튼 또는 확인란의 스타일을 지정하여 조직의 스타일에 맞출 수 있습니다. 구성 요소의 스타일을 사용자 정의하려면 다음을 수행합니다.

1. 파일 열기 `<your-theme-sources>/src/components/<component>/<component.scss>` 편집할 수 있습니다. 예를 들어 버튼 구성 요소의 글꼴 색상을 변경하려면 `<your-theme-sources>/src/components/button/button.scss`, 파일.
1. 요구 사항에 따라 의 값을 변경합니다. 예를 들어 마우스를 가리킬 때 버튼 구성 요소의 색상을 변경하려면 `green`, 값 변경 `color: $white` 의 속성 `cmp-adaptiveform-button__widget:hover` 클래스-16진수 코드 `#12B453` 또는 기타 그림자 `green`. 최종 코드는 다음과 같습니다.

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

1. IDE에서 테마 폴더를 엽니다. 예를 들어 `aem-forms-theme-canvas` 폴더가 표시됩니다.
1. 이름 바꾸기 `env_template` 파일 위치: `.env` 테마 폴더에 파일을 만들고 다음 매개 변수를 추가합니다.

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   예를 들어 양식의 URL은 `http://localhost:4502/editor.html/content/forms/af/contactusform.html`. 따라서 의 값은 다음과 같습니다.

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. 파일을 저장합니다.

   ![캔버스 테마 구조](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 로컬 환경을 사용하여 테마 테스트 {#start-a-local-proxy-server}

1. 테마 폴더의 루트로 이동합니다. 이 경우 테마 폴더 이름은 입니다. `aem-forms-theme-canvas`.
1. 명령 프롬프트 또는 터미널을 엽니다.
1. 실행 `npm install` 종속성을 설치합니다.
1. 실행 `npm run live` 로컬 브라우저에서 업데이트된 테마가 있는 양식을 미리 봅니다.

   >[!NOTE]
   >
   > 를 실행하는 동안 오류가 발생하는 경우 `npm run live` command, 다음 명령을 실행합니다. `npm run live` 명령:
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

이는 최신 배포입니다. 따라서 변경 작업을 수행하고 `_variables.scss` 및 `button.scss` 파일은 서버가 자동으로 변경 내용을 선택하고 최신 출력을 미리 봅니다. 라인 `[Browsersync] File event [change]` 는 서버가 최신 변경 사항을 인식했으며 로컬 환경에 변경 사항을 배포하고 있음을 나타냅니다.

![프록시 브라우저 동기화](/help/forms/assets/browser_sync.png)

테마 맞춤화에 대한 테마 수준과 구성 요소 수준 모두에서 적응형 양식(핵심 구성 요소)의 스타일을 지정하는 예제를 따르면 적응형 양식의 오류 메시지가 로 변경됩니다. `blue` 색상 - 버튼 구성 요소의 레이블 색상이 `green` 마우스로 가리키면

**테마 수준 스타일 미리 보기**

![예: 오류 색상이 파란색으로 설정됨](/help/forms/assets/theme-level-changes.png)

**구성 요소 수준 스타일 미리 보기**

![예: 가리키기 색상이 녹색으로 설정됨](/help/forms/assets/button-customization.png)

테마를 맞춤화하면 조직 요구 사항에 따라 핵심 구성 요소 기반 적응형 Forms에 대한 맞춤형 룩을 디자인할 수 있습니다.

###### Cloud Service 환경에서 호스팅되는 양식의 테마 테스트

AEM Forms as a Cloud Service 인스턴스에 호스팅된 적응형 양식에 대한 테마를 테스트할 수도 있습니다. 클라우드 인스턴스에서 호스팅된 적응형 Forms을 사용하여 테마를 테스트하기 위한 로컬 환경을 구성하고 설정하려면 다음 단계를 수행하십시오.

1. IDE에서 테마 폴더를 엽니다. 예를 들어 `aem-forms-theme-canvas` 폴더가 표시됩니다.
1. 이름 바꾸기 `env_template` 파일 위치: `.env` 파일을 만들고 다음 매개 변수를 추가합니다.

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   예를 들어 클라우드 환경에서 양식의 URL은 다음과 같습니다 `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`. 따라서 의 값은 다음과 같습니다.

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. 파일을 저장합니다.
1. 로컬 사용자를 만듭니다.

   >[!NOTE]
   >
   > 로컬 사용자를 만들려면 다음 작업을 수행하십시오.
   >
   > * 다음으로 이동 **[!UICONTROL AEM 홈]** > **[!UICONTROL 도구]** > **[!UICONTROL 보안]** > **[!UICONTROL 사용자]** .
   > * 사용자가 다음 그룹의 구성원인지 확인합니다. `forms-users` 그룹입니다.

1. 테마 폴더의 루트로 이동합니다. 이 경우 테마 폴더 이름은 입니다. `aem-forms-theme-canvas`.
1. 실행 `npm run live` 그리고 로컬 브라우저로 리디렉션됩니다.
1. 클릭 `SIGN IN LOCALLY (ADMIN TASKS ONLY)` 로컬 사용자의 자격 증명을 사용하여 로그인합니다.

적응형 양식에 최신 변경 사항을 미리 볼 수 있습니다. 테마 폴더에서 수정한 사항에 만족하면 프론트엔드 파이프라인을 사용하여 테마를 AEM Cloud Service 환경에 배포합니다.

#### 5. 테마 배포 {#deploy-the-theme}

프론트엔드 파이프라인을 사용하여 테마를 Cloud Service 환경에 배포하려면 다음을 수행하십시오.

* 5.1 [테마를 위한 저장소 만들기](#create-a-new-theme-repo)
* 5.2 [변경 사항을 저장소에 푸시](#committing-the-changes)
* 5.3 [프론트엔드 파이프라인 실행](#run-a-frontend-pipeline)

##### 5.1 테마를 위한 저장소 만들기{#create-a-new-theme-repo}

테마를 배포하려면 저장소가 필요합니다. 에 로그인 [AEM Cloud Manager 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) 테마에 새 저장소를 추가합니다.

1. 을(를) 클릭하여 테마에 대한 새 저장소 만들기 **[!UICONTROL 저장소]** > **[!UICONTROL 저장소 추가]**.

   ![새 테마 저장소 만들기](/help/forms/assets/createrepo_canvastheme.png)


1. 다음을 지정합니다. **저장소 이름** 다음에서 **저장소 추가** 대화 상자. 예를 들어 제공된 이름은 입니다. `custom-canvas-theme-repo`.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![캔버스 테마 저장소 추가](/help/forms/assets/addcanvasthemerepo.png)

1. 클릭 **[!UICONTROL 저장소 URL 복사]** 저장소의 URL을 복사합니다.

   ![캔버스 테마 URL](/help/forms/assets/copyurl_canvastheme.png)

   >[!NOTE]
   > 
   > * 여러 테마에 단일 저장소를 사용할 수 있습니다.
   > * 다른 테마를 배포하려면 별도의 프론트엔드 파이프라인을 만들어야 합니다.
   >* 예를 들어 와 동일한 저장소를 사용할 수 있습니다. `custom-canvas-theme-repo`, 캔버스 테마, WKND 테마 및 EASEL 테마. 그러나 테마를 배포하려면 별도의 프론트엔드 파이프라인을 만들어야 합니다. 특정 테마에 대한 향후 사용자 지정은 해당 프론트엔드 파이프라인을 사용하여 배포됩니다.

##### 5.2. 변경 사항을 저장소에 푸시합니다. {#committing-the-changes}

이제 변경 사항을 AEM Forms Cloud Service의 테마 저장소에 푸시합니다.

1. 테마 폴더의 루트로 이동합니다.  이 경우 테마 폴더 이름은 입니다. `aem-forms-theme-canvas`.
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

테마는 [프론트엔드 파이프라인.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). 테마를 배포하려면 다음 단계를 수행하십시오.

1. AEM Cloud Manager 저장소에 로그인합니다.
1. 다음을 클릭합니다. **[!UICONTROL 추가]** 단추 **[!UICONTROL 파이프라인]** 섹션.
1. 선택 **[!UICONTROL 비프로덕션 파이프라인 추가]** 또는 **[!UICONTROL 프로덕션 파이프라인 추가]** Cloud Service 환경을 기반으로 합니다. 예를 들어, 다음 **[!UICONTROL 프로덕션 파이프라인 추가]** 옵션이 선택되어 있습니다.
1. 다음에서 **[!UICONTROL 프로덕션 파이프라인 추가]** 대화 상자를 의 일부로 사용 **[!UICONTROL 구성]** 단계, 파이프라인의 이름을 지정합니다. 예를 들어 파이프라인의 이름은 입니다. `customcanvastheme`.
1. **[!UICONTROL 계속]**&#x200B;을 클릭합니다.
1. 다음 항목 선택 **[!UICONTROL 타깃팅된 배포]** > **[!UICONTROL 프론트엔드 코드]** 옵션, **[!UICONTROL 소스 코드]** 단계.
1. 다음 항목 선택 **[!UICONTROL 저장소]** 및 **[!UICONTROL Git 분기]** 최신 변경 사항이 있는 값입니다. 예를 들어 선택한 저장소 이름은 다음과 같습니다. `custom-canvas-theme-repo` 그리고 Git 분기는 `main`.
1. 다음 항목 선택 **[!UICONTROL 코드 위치]** 다음으로: `/`변경 사항이 루트 폴더에 있는 경우.
1. **[!UICONTROL 저장]**을 클릭합니다.
   ![프론트엔드 파이프라인 만들기](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   파이프라인 설정이 완료되면 콜 투 액션 카드가 업데이트됩니다.

1. 생성된 파이프라인을 마우스 오른쪽 버튼으로 클릭합니다.
1. 클릭 **[!UICONTROL 실행]** .

   ![실행-a-pipleine](/help/forms/assets/canvas-theme-run-pipeline.png)

빌드가 완료되면 작성자 인스턴스에서 테마를 사용할 수 있습니다. 다음 아래에 나타납니다. **[!UICONTROL 스타일]** 적응형 양식을 만드는 동안 적응형 양식 만들기 마법사에서 탭합니다.

![스타일 탭에서 사용할 수 있는 사용자 정의 테마](/help/forms/assets/custom-theme-style-tab.png)

맞춤화된 테마는 핵심 구성 요소 기반 적응형 Forms에 대한 브랜드 경험을 만드는 데 도움이 됩니다.

## 적응형 양식에 테마 적용 {#using-theme-in-adaptive-form}

적응형 양식에 테마를 적용하는 단계는 다음과 같습니다.

1. AEM Forms 작성자 인스턴스에 로그인합니다.

1. 선택 **Adobe Experience Manager** > **Forms** > **Forms 및 문서**.

1. 클릭 **만들기** > **적응형 Forms**. 적응형 양식 만들기 마법사가 열립니다.

1. 에서 핵심 구성 요소 템플릿 선택 **소스** 탭.
1. 에서 테마 선택 **스타일** 탭.
1. **만들기**&#x200B;를 클릭합니다.

적응형 양식 테마는 적응형 양식을 작성하는 동안 스타일을 정의하는 적응형 양식 템플릿의 일부로 사용됩니다.

## 모범 사례 {#best-practices}

* **다른 테마에서 에셋 피하기**

  테마를 편집할 때 다른 테마의 에셋(예: 이미지)을 찾아보고 추가할 수 있습니다. 예를 들어 페이지의 배경을 편집하는 경우 예를 들어 다음을 선택할 경우 **[!UICONTROL 페이지]** ![편집 단추](assets/edit-button.png)> **[!UICONTROL 배경]** > **[!UICONTROL 추가]** > **[!UICONTROL 이미지]**&#x200B;다른 테마의 이미지를 찾아보고 추가할 수 있는 대화 상자가 표시됩니다.

  자산이 다른 테마에서 추가되고 다른 테마가 이동 또는 삭제되는 경우 현재 테마와 관련된 문제에 직면할 수 있습니다. 다른 테마에서 에셋을 찾아보거나 추가하지 않는 것이 좋습니다.

* **컨테이너 패널 레이아웃 폭 변경**

  컨테이너 패널 레이아웃 너비는 변경하지 않는 것이 좋습니다. 컨테이너 패널의 너비를 지정하면 정적 패널이 되어 다른 디스플레이에 맞게 조정되지 않습니다.

* **양식 편집기 또는 테마 편집기를 사용하여 머리글 및 바닥글 작업**

  글꼴 스타일, 배경 및 투명도와 같은 스타일 옵션을 사용하여 머리글과 바닥글의 스타일을 지정하려면 테마 편집기를 사용하십시오.
로고 이미지, 머리글에 회사 이름 및 바닥글에 저작권 정보와 같은 정보를 제공하려면 양식 편집기 옵션을 사용합니다.

## 자주 묻는 질문 {#faq}

**Q:** 글로벌 수준과 구성 요소 수준 모두에서 테마 폴더를 맞춤화할 때 우선 순위가 필요한 맞춤화는 무엇입니까?

**Ans:** 전역 수준과 구성 요소 수준 모두에서 맞춤화가 수행되면 구성 요소 수준의 맞춤화가 우선합니다.

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
