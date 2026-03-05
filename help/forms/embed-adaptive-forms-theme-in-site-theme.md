---
title: AEM Sites 테마에 적응형 Forms 테마 포함
description: 'Sites 페이지와 포함된 적응형 Forms이 하나의 통합 테마 및 배포를 공유할 수 있도록 적응형 AEM Sites 테마(예: 캔버스)를 Forms 테마로 통합하는 방법에 대해 알아봅니다.'
keywords: 적응형 양식 테마, 사이트 테마, AEM Sites 테마, 양식 테마 통합, 프론트엔드 파이프라인, 테마 포함
feature: Adaptive Forms, Core Components
role: Developer
exl-id: a1f8c4d2-3e5b-4a2f-9b7e-2d4f6a8c1b0e
source-git-commit: 2aa13887949507ab74c45b4b6f3135aebd59c6ea
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# AEM Sites 테마에 적응형 Forms 테마 포함

적응형 Forms 테마(예: [AEM Forms 캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas))를 AEM Sites 테마에 포함할 수 있습니다. 이러한 방식으로 단일 테마는 사이트 페이지와 해당 페이지에 포함된 모든 적응형 Forms을 구동하며, 하나의 빌드와 [AEM 프론트엔드 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=ko)을 통한 하나의 배포가 있습니다.

이 문서는 표준(또는 사용자 지정) AEM Sites 테마를 유지 또는 사용자 지정하고 별도의 Forms 테마 배포를 관리하지 않고 적응형 양식 스타일을 포함하려는 개발자를 위한 것입니다.

## 사전 요구 사항 {#prerequisites}

시작하기 전에 다음을 확인하십시오.

* 사이트 테마에 대해 **프론트엔드 파이프라인**&#x200B;이(가) 구성된 [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=ko)
* **사이트 테마 원본** - 예: [표준 사이트 템플릿 테마](https://github.com/adobe/aem-site-template-standard)&#x200B;(`theme/`, `src/theme.scss` 등이 있는 `src/components/`이(가) 포함된 저장소).
* **Forms 테마 소스** - 로컬로 복제되거나 다운로드된 [AEM Forms 캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas)&#x200B;(또는 다른 호환되는 적응형 Forms 테마)
* **Node.js 및 npm** - 사이트 테마를 빌드합니다(지원되는 버전은 테마 추가 정보 참조).
* **Maven** - 전체 사이트 템플릿 패키지를 빌드하는 경우(테마 전용 작업의 경우 선택 사항).

## 1단계: 적응형 양식 구성 요소 폴더 만들기 {#step-1-create-folder}

사이트 테마 저장소에서 Forms 테마가 위치할 폴더를 만듭니다.

```text
theme/src/components/adaptiveform/
```

모든 Forms 테마 자산은 이 폴더 아래에 배치되므로 기존 사이트 구성 요소와 별도로 유지됩니다.

## 2단계: Forms 테마 구성 요소 및 이미지 복사 {#step-2-copy-components-and-images}

**Forms 테마**(예: `aem-forms-theme-canvas`) 및 **사이트 테마** 경로 사용:

1. **구성 요소 폴더 복사**\
   Forms 테마에서 `src/components/`의 전체 콘텐츠를 다음과 같이 사이트 테마로 복사합니다.

   ```text
   theme/src/components/adaptiveform/
   ```

   따라서 다음과 같은 경로를 사용할 수 있습니다.

   ```text
   theme/src/components/adaptiveform/button/
   theme/src/components/adaptiveform/checkbox/
   theme/src/components/adaptiveform/container/
   … (one folder per component)
   ```

2. **이미지 복사**\
   Forms 테마 이미지를 사이트 테마에 복사합니다.

   ```text
   Forms theme:  src/resources/images/*
   Site theme:   theme/src/components/adaptiveform/resources/images/
   ```

   `theme/src/components/adaptiveform/resources/images/`이(가) 없으면 만든 다음 모든 이미지 자산(예: `question.svg`, `Chevron-Left.svg`, `busy-state.gif` 등)을 복사합니다.

## 3단계: 변수 및 mixin 복사 {#step-3-copy-variables-and-mixins}

Forms 테마는 `src/site/`에서 공유 변수와 mixin을 사용합니다. 이 두 파일만 **하위 폴더 내부가 아닌**&#x200B;의 `adaptiveform/`root`site`에 복사합니다.

| Source (Forms 테마) | 대상(사이트 테마) |
|---------------------------|---------------------------------------------------|
| `src/site/_variables.scss` | `theme/src/components/adaptiveform/_variables.scss` |
| `src/site/_mixin.scss` | `theme/src/components/adaptiveform/_mixin.scss` |

Forms 테마의 나머지 **폴더는**&#x200B;복사하지 `src/site/` 마십시오. 임베드된 양식 스타일에는 이 두 파일만 필요합니다.

## 4단계: SCSS에서 이미지 경로 수정 {#step-4-fix-image-paths}

Forms 테마에서 구성 요소 SCSS 파일은 종종 `./resources/` 또는 `url(resources/`과(와) 같은 경로를 사용하는 이미지를 참조합니다. `theme/src/components/adaptiveform/<component>/`(으)로 이동한 후 해당 경로는 `adaptiveform/resources/`(으)로 한 수준 올라가야 합니다.

**아래**&#x200B;마다 `.scss`찾기 및 바꾸기`theme/src/components/adaptiveform/`:

| 찾기 | 바꿀 내용 |
|------|------------------|
| `./resources/` | `../resources/` |
| `url(resources/` | `url(../resources/` |
| `url('resources/` | `url('../resources/` |

**예** - 이전(Forms 테마):

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(./resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

**이후**(사이트 테마):

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(../resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

바꾸기 후에는 각각 `url(../resources/images/...)` 및 `url('../resources/images/...')`이(가) 됩니다. 이미지(단추, 아코디언, 마법사, 컨테이너, 스크리블 등)를 참조하는 `adaptiveform/` 아래의 모든 SCSS 파일에 대해 이 작업을 반복합니다.

## 5단계: 적응형 양식 진입점 SCSS 만들기 {#step-5-create-adaptiveform-scss}

사이트 테마에 **`theme/src/components/adaptiveform/_adaptiveform.scss`**&#x200B;을(를) 만듭니다. 이 파일은 다음과 같아야 합니다.

1. 공유 변수와 mixin을 가져옵니다.
2. 각 적응형 양식 구성 요소의 기본 SCSS 파일을 가져옵니다.

다음을 전체 진입점으로 사용합니다(모든 핵심 구성 요소 기반 양식 구성 요소와 표준 통합 일치).

```scss
//== Adaptive Form components (forms theme integration)
// Variables and mixins for adaptive form components
@import 'variables';
@import 'mixin';

//== Core adaptive form components
@import './button/_button.scss';
@import './checkboxgroup/_checkboxgroup.scss';
@import './container/_container.scss';
@import './datepicker/_datepicker.scss';
@import './dropdown/_dropdown.scss';
@import './fileinput/_fileinput.scss';
@import './footer/_footer.scss';
@import './image/_image.scss';
@import './numberinput/_numberinput.scss';
@import './panelcontainer/_panelcontainer.scss';
@import './radiobutton/_radiobutton.scss';
@import './text/_text.scss';
@import './textinput/_textinput.scss';
@import './accordion/_accordion.scss';
@import './tabsontop/_tabsontop.scss';
@import './pageheader/_pageheader.scss';
@import './wizard/_wizard.scss';
@import './title/_title.scss';
@import './telephoneinput/_telephoneinput.scss';
@import './emailinput/_emailinput.scss';
@import './recaptcha/_recaptcha.scss';
@import './verticaltabs/_verticaltabs.scss';
@import './checkbox/_checkbox.scss';
@import './termsandconditions/_termsandconditions.scss';
@import './switch/_switch.scss';
@import './hcaptcha/_hcaptcha.scss';
@import './turnstile/_turnstile.scss';
@import './review/_review.scss';
@import './scribble/_scribble.scss';
@import './datetime/_datetime.scss';
```

Forms 테마에 일부 구성 요소가 누락된 경우(예: 스크리블 또는 captcha 없음) 해당 `@import`줄을 제거하거나 주석 처리하여 빌드 오류를 방지하십시오. 위의 목록은 [캔버스 테마](https://github.com/adobe/aem-forms-theme-canvas) 구조와 일치합니다.

## 6단계: 사이트 테마에서 적응형 양식 테마 가져오기 {#step-6-import-in-theme-scss}

**`theme/src/theme.scss`**&#x200B;에서 파일의 **end**&#x200B;에 단일 가져오기를 추가합니다(다른 구성 요소 가져오기 후).

```scss
//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

**예** - `theme.scss`의 끝:

```scss
// ... existing site component imports ...
@import './components/embed/_embed.scss';
@import './components/pdfviewer/_pdfviewer.scss';
@import './components/socialmediasharing/_social_media_sharing.scss';

//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

이는 기존 사이트 테마 구조에서 필요한 유일한 변경 사항입니다. 모든 폼별 코드는 `src/components/adaptiveform/`에 남아 있습니다.

## 7단계: 빌드 및 배포 {#step-7-build-and-deploy}

1. 테마 루트에서 사이트 테마를 빌드합니다.

   ```bash
   cd theme
   npm install
   npm run build
   ```

2. 기존 [프론트엔드 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=ko)을 통해 배포합니다. 배포 후 동일한 테마 CSS가 사이트 페이지와 포함된 적응형 Forms 모두에 적용됩니다.

## 문제 해결 {#troubleshooting}

| 문제 | 확인할 사항 |
|-------|-------------------------------|
| 빌드 실패: 이미지에 대한 &quot;파일을 찾을 수 없음&quot; | 모든 양식 이미지를 `theme/src/components/adaptiveform/resources/images/`에 넣습니다. `.scss`의 `adaptiveform/`마다 `../resources/`이(가) 아닌 이미지 경로에 `url(../resources/`(및 `./resources/`)을(를) 사용합니다. 번들로 `theme/src/`에서 경로를 확인하면 `theme/src/resources/images/`에 이미지를 넣고 SCSS에서 `resources/images/`(`../` 없음)을 사용합니다. |
| 빌드 실패: `_variables.scss` 또는 `_mixin.scss`에 대해 &quot;파일을 찾을 수 없음&quot; | Forms 테마 `src/site/`의 두 파일을 `theme/src/components/adaptiveform/` 하위 폴더 내부가 아닌 `site`(적응형 양식 루트)에 복사하십시오. |
| 빌드 실패: 구성 요소(예: `_scribble.scss`)에 대해 &quot;파일을 찾을 수 없음&quot; | Forms 테마에 해당 구성 요소가 포함되지 않을 수 있습니다. `theme/src/components/adaptiveform/_adaptiveform.scss`에서 해당 구성 요소에 대한 `@import` 줄을 제거하거나 주석 처리합니다. |
| 양식이 렌더링되지만 스타일이 없습니다. | 페이지에서 빌드된 테마 CSS가 포함된 클라이언트 라이브러리를 사용하며 `theme.scss`에 `@import './components/adaptiveform/_adaptiveform.scss';` 줄이 포함되어 있고 테마가 다시 빌드되고 배포되었는지 확인합니다. |
| 사이트와 양식 구성 요소 간 스타일 충돌 | 양식 구성 요소 클래스의 네임스페이스가 지정되었습니다(예: `cmp-adaptiveform-button`). 충돌이 표시되면 사용자 지정 사이트 CSS가 이러한 클래스를 무시하는지 확인하고 특이성 또는 순서를 조정하십시오. |

## 추가 참조 {#see-also}

* [테마를 사용하여 핵심 구성 요소 기반 적응형 Forms 스타일 지정](/help/forms/using-themes-in-core-components.md)
* [프론트엔드 파이프라인으로 개발](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=ko)