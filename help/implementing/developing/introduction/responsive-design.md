---
title: 반응형 디자인
description: 반응형 설계를 통해 동일한 경험을 여러 방향의 여러 디바이스에서 효과적으로 표시할 수 있습니다.
exl-id: be645062-d6d6-45a2-97dc-d8aa235539b8
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 1%

---

# 반응형 디자인 {#responsive-design}

경험이 표시되는 클라이언트 뷰포트에 맞게 조정되도록 경험을 설계합니다. 응답형 디자인을 사용하면 동일한 페이지를 두 방향에서 여러 디바이스에 효과적으로 표시할 수 있습니다. 다음 이미지는 페이지가 뷰포트 크기의 변화에 응답할 수 있는 몇 가지 방법을 보여 줍니다.

* 레이아웃: 작은 뷰포트에는 단일 열 레이아웃을 사용하고 큰 뷰포트에는 다중 열 레이아웃을 사용합니다.
* 텍스트 크기: 큰 뷰포트에서는 텍스트 크기(예: 제목)를 크게 사용합니다.
* 컨텐츠: 작은 장치에 표시할 때 가장 중요한 컨텐츠만 포함합니다.
* 탐색: 다른 페이지에 액세스하기 위해 장치별 도구가 제공됩니다.
* 이미지: 창 차원에 따라 클라이언트 뷰포트에 적합한 이미지 렌디션을 제공합니다.

![반응형 디자인의 예](assets/responsive-example.png)

다양한 창 크기와 방향에 맞는 HTML5를 생성하는 Adobe Experience Manager(AEM) 애플리케이션을 개발합니다. 예를 들어, 다음 뷰포트 너비 범위는 다양한 디바이스 유형 및 방향에 해당합니다

* 최대 너비 480픽셀(전화, 세로)
* 최대 너비 767픽셀(휴대폰, 가로)
* 768픽셀에서 979픽셀 사이의 폭(태블릿, 세로)
* 980픽셀에서 1199픽셀 사이의 폭(태블릿, 가로)
* 너비 1200px 이상(데스크탑)

반응형 디자인 동작 구현에 대한 자세한 내용은 다음 항목을 참조하십시오.

* [미디어 쿼리](#using-media-queries)
* [유체 격자](#developing-a-fluid-grid)
* [응용 이미지](#using-adaptive-images)

디자인할 때 **에뮬레이터** 도구 모음을 사용하여 페이지를 다양한 화면 크기로 미리 볼 수 있습니다.

## 개발하기 전에 {#before-you-develop}

웹 페이지를 지원하는 AEM 애플리케이션을 개발하기 전에 몇 가지 디자인 결정을 내려야 합니다. 예를 들어 다음 정보가 필요합니다.

* 타깃팅하는 디바이스
* 대상 뷰포트 크기
* 타겟팅된 각 뷰포트 크기에 대한 페이지 레이아웃

### 애플리케이션 구조 {#application-structure}

일반적인 AEM 애플리케이션 구조는 모든 응답형 디자인 구현을 지원합니다.

* 페이지 구성 요소는 아래에 있습니다. `/apps/<application_name>/components`
* 템플릿은 아래에 있습니다. `/apps/<application_name>/templates`

## 미디어 쿼리 사용 {#using-media-queries}

미디어 쿼리를 사용하면 페이지 렌더링에 CSS 스타일을 선택적으로 사용할 수 있습니다. AEM 개발 도구 및 기능을 사용하면 애플리케이션에서 미디어 쿼리를 효과적이고 효율적으로 구현할 수 있습니다.

W3C 그룹은 [미디어 쿼리](https://www.w3.org/TR/css3-mediaqueries/) 이 CSS3 기능 및 구문을 설명하는 권장 사항입니다.

### CSS 파일 만들기 {#creating-the-css-file}

CSS 파일에서 타겟팅하는 장치의 속성을 기반으로 미디어 쿼리를 정의합니다. 다음 구현 전략은 각 미디어 쿼리의 스타일을 관리하는 데 효과적입니다.

* 사용 [클라이언트 라이브러리 폴더](clientlibs.md) 를 클릭하여 페이지를 렌더링할 때 어셈블되는 CSS를 정의합니다.
* 별도의 CSS 파일에서 각 미디어 쿼리와 관련 스타일을 정의합니다. 미디어 쿼리의 장치 기능을 나타내는 파일 이름을 사용하는 것이 유용합니다.
* 별도의 CSS 파일에서 모든 장치에 공통되는 스타일을 정의합니다.
* 클라이언트 라이브러리 폴더의 css.txt 파일에서 어셈블된 CSS 파일에 필요한 CSS 파일 목록을 정렬합니다.

다음 [WKND 자습서](develop-wknd-tutorial.md) 은 이 전략을 사용하여 사이트 디자인에 스타일을 정의합니다. WKND에서 사용하는 CSS 파일은 다음 위치에 있습니다. `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.

### AEM 페이지에서 미디어 쿼리 사용 {#using-media-queries-with-aem-pages}

[WKND 샘플 프로젝트](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 및 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 사용 [페이지 핵심 구성 요소,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/page.html) 페이지 정책을 통해 clientlib을 포함합니다.

자체 페이지 구성 요소가 페이지 핵심 구성 요소를 기반으로 하지 않는 경우 해당 구성 요소의 HTL 또는 JSP 스크립트에 클라이언트 라이브러리 폴더를 포함할 수도 있습니다. 이렇게 하면 반응형 그리드가 작동하는 데 필요한 미디어 쿼리가 있는 CSS 파일이 생성되고 참조됩니다.

#### HTL {#htl}

```html
<sly data-sly-use.clientlib="${'/libs/granite/sightly/templates/clientlib.html'}">
<sly data-sly-call="${clientlib.all @ categories='apps.weretail.all'}"/>
```

#### JSP {#jsp}

```xml
<ui:includeClientLib categories="apps.weretail.all"/>
```

JSP 스크립트는 스타일 시트를 참조하는 다음 HTML 코드를 생성합니다.

```xml
<link rel="stylesheet" href="/etc/designs/weretail/clientlibs-all.css" type="text/css">
<link href="/etc/designs/weretail.css" rel="stylesheet" type="text/css">
```

## 특정 장치에 대한 미리 보기 {#previewing-for-specific-devices}

에뮬레이터를 사용하면 페이지를 다양한 뷰포트 크기로 미리 볼 수 있으므로 응답형 디자인의 동작을 테스트할 수 있습니다. 사이트 콘솔에서 페이지를 편집할 때 **에뮬레이터** 아이콘을 클릭하여 에뮬레이터를 표시합니다.

![도구 모음의 에뮬레이터 아이콘](assets/emulator-icon.png)

에뮬레이터 도구 모음에서 를 탭하거나 클릭합니다. **장치** 아이콘을 클릭하면 장치를 선택할 수 있는 드롭다운 메뉴가 표시됩니다. 장치를 선택하면 페이지가 뷰포트 크기에 맞게 변경됩니다.

![에뮬레이터 도구 모음](assets/emulator.png)

### 장치 그룹 지정 {#specifying-device-groups}

에 표시되는 장치 그룹을 지정하려면 **장치** 목록, 추가 `cq:deviceGroups` 에 대한 속성 `jcr:content` 사이트의 템플릿 페이지에 있는 노드. 속성 값은 장치 그룹 노드에 대한 경로 배열입니다.

예를 들어 WKND 사이트의 템플릿 페이지는 `/conf/wknd/settings/wcm/template-types/empty-page/structure`. 및 `jcr:content` 그 아래에 있는 노드에는 다음 속성이 포함됩니다.

* 이름: `cq:deviceGroups`
* 유형: `String[]`
* 값: `mobile/groups/responsive`

장치 그룹 노드는 `/etc/mobile/groups` 폴더를 삭제합니다.

## 응답형 이미지 {#responsive-images}

반응형 페이지는 렌더링되는 장치에 동적으로 적응하여 사용자에게 더 나은 경험을 제공합니다. 하지만 페이지 로드 시간을 최소화하기 위해 자산을 중단점 및 장치에 최적화하는 것도 중요합니다.

[핵심 구성 요소의 이미지 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html) 응용 이미지 선택과 같은 기능입니다.

* 기본적으로 이미지 구성 요소는 [적응형 이미지 서블릿](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/adaptive-image-servlet.html) 적절한 표현물을 전달할 수 있습니다.
* [웹에 최적화된 이미지 제공](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) 는 DAM의 이미지 에셋을 WebP 형식으로 전달하고 이미지의 다운로드 크기를 평균 약 25% 줄일 수 있는 간단한 정책 확인란을 통해서도 사용할 수 있습니다.

## 레이아웃 컨테이너 {#layout-container}

AEM 레이아웃 컨테이너를 사용하면 응답형 레이아웃을 효율적이고 효과적으로 구현하여 페이지 차원을 클라이언트 뷰포트에 맞출 수 있습니다.

문서를 참조하십시오. [레이아웃 컨테이너 및 레이아웃 모드 구성](/help/sites-cloud/administering/responsive-layout.md) 레이아웃 컨테이너의 작동 방식과 콘텐츠에 대한 반응형 레이아웃을 활성화하는 방법에 대한 자세한 정보입니다.
