---
title: 사이트 테마
description: AEM 사이트 테마를 사용하여 게시 게재를 사용한 기존 AEM 작성 프로젝트의 사이트 스타일 및 디자인을 맞춤화하는 방법에 대해 알아봅니다.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
solution: Experience Manager Sites
source-git-commit: 9efba01add46c09e9839da6bb96b138d48018e54
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 72%

---


# 사이트 테마 {#site-themes}

{{traditional-aem}}

AEM 사이트 테마를 사용하여 게시 게재를 사용한 기존 AEM 작성 프로젝트의 사이트 스타일 및 디자인을 맞춤화하는 방법에 대해 알아봅니다.

## 개요 {#overview}

AEM 사이트 테마는 CSS, JavaScript, 그리고 AEM 사이트의 스타일을 정의하며 AEM 사이트 테마의 구조를 준수하는 정적 리소스를 포함하는 패키지입니다.

AEM 사이트 템플릿으로 만든 사이트를 사용하면 [게시 게재를 통해 기존 AEM 제작 프로젝트의 테마를 손쉽게 다운로드하고, 맞춤화하고, 재배포할 수 있습니다.](/help/sites-cloud/authoring/author-publish.md)

>[!NOTE]
>
>AEM 사이트 테마를 [AEM 사이트 템플릿과 혼동하면 안 됩니다](site-templates.md). AEM 사이트 테마는 AEM 사이트에 대한 스타일 정보만 포함합니다. AEM 사이트 템플릿은 사이트 구조 및 최초 콘텐츠를 정의하며 [빠른 사이트 생성](create-site.md)을 위한 AEM 사이트 테마를 포함합니다.

## 사이트 테마 사용 {#using-themes}

두 가지 방법으로 사이트 테마를 사용할 수 있습니다.

* 사이트 템플릿의 일부로 사용하여 [사이트 생성](create-site.md) 시 스타일을 지정할 수 있습니다.
* 사이트 템플릿을 기반으로 사이트를 만든 후 다운로드하여 프론트엔드 개발자가 스타일을 맞춤화하도록 할 수 있습니다.

>[!TIP]
>
>템플릿으로 사이트를 만들고 테마를 맞춤화하는 프로세스에 대한 전체적인 설명은 [빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)에서 확인할 수 있습니다.

## 사이트 테마 구조 {#structure}

사이트 테마는 패키지 콘텐츠의 목적을 명확하게 반영하는 논리적 구조를 갖춘 패키지입니다. 일반적인 프론트엔드 프로젝트의 경우 Adobe은 사이트 테마에 대해 다음 구조를 권장합니다.

* `src/theme.ts`: JS 및 CSS 테마의 주요 진입점
* `src/site`: 전체 사이트에 적용되는 JS 및 CSS 파일
* `src/components`: AEM 구성 요소와 관련된 JS 및 CSS 파일
* `src/resources`: 아이콘, 로고 및 글꼴과 같은 정적 파일

특정 프로젝트 요구 사항에 따라 기본 진입점 `src/theme.ts`이(가) 유지되는 한 테마 구조가 달라질 수 있습니다.

## 표준 사이트 테마 {#standard-site-theme}

Adobe는 나만의 테마를 만들 때 기준으로 사용할 수 있는 모범 참조 테마를 제공합니다. [표준 사이트 테마는 GitHub에서 사용할 수 있습니다.](https://github.com/adobe/aem-site-template-standard/tree/main/theme)

## 사이트 테마 개발 {#developing-themes}

Adobe는 새 사이트 테마를 만들기 위한 스크립트 세트로 AEM 사이트 테마 빌더를 제공합니다.

[GitHub의 사용 설명서와 함께 AEM 사이트 테마 빌더를 사용할 수 있습니다.](https://github.com/adobe/aem-site-theme-builder) 테마를 맞춤화하려면 프론트엔드 개발 경험이 필요합니다.
