---
title: 사이트 테마
description: AEM 사이트 테마를 사용하여 사이트의 스타일 및 디자인을 사용자 지정하는 방법을 알아봅니다.
feature: Administering
role: Admin
source-git-commit: 0b00d579886a106f5f66cfc54d90eab9563724cd
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---


# 사이트 테마 {#site-themes}

AEM 사이트 테마를 사용하여 사이트의 스타일 및 디자인을 사용자 지정하는 방법을 알아봅니다.

## 개요 {#overview}

AEM 사이트 테마는 AEM 사이트의 스타일을 정의하고 AEM 사이트 테마의 구조를 준수하는 CSS, JavaScript 및 정적 리소스가 포함된 패키지입니다.

AEM 사이트 템플릿으로 만든 사이트를 통해 손쉽게 테마를 다운로드, 사용자 지정 및 재배포할 수 있습니다.

>[!NOTE]
>
>AEM 사이트 테마를 [AEM 사이트 템플릿.](site-templates.md) AEM 사이트 테마에 AEM 사이트에 대한 스타일 정보만 포함됩니다. AEM 사이트 템플릿은 다음을 위해 사이트 구조 및 초기 컨텐츠를 정의하며 AEM 사이트 테마를 포함합니다 [빠른 사이트 만들기](create-site.md)

## 사이트 테마 사용 {#using-themes}

사이트 테마는 다음 두 가지 방법으로 사용됩니다.

* 사이트 템플릿의 일부로 사용하여 스타일을 정의할 때 [사이트 만들기](create-site.md)
* 사이트 템플릿을 기반으로 사이트를 만든 후 다운로드되므로 프런트 엔드 개발자가 스타일을 추가로 사용자 지정할 수 있습니다.

>[!TIP]
>
>템플릿에서 사이트를 만들고 주제를 사용자 지정하는 프로세스에 대한 종단 간 설명은 [빠른 사이트 만들기 여정.](/help/journey-sites/quick-site/overview.md)

## 사이트 테마 구조 {#structure}

사이트 테마는 패키지 컨텐츠의 목적을 명확하게 반영하는 논리 구조의 패키지입니다. 사이트 테마는 프런트 엔드 프로젝트의 일반적인 다음 구조를 갖습니다.

* `src/main.ts`: JS 및 CSS 테마의 기본 시작 지점
* `src/site`: 전체 사이트에 적용되는 JS 및 CSS 파일
* `src/components`: AEM 구성 요소별 JS 및 CSS 파일
* `src/resources`: 아이콘, 로고 및 글꼴과 같은 정적 파일

## 표준 사이트 테마 {#standard-site-theme}

Adobe은 고유한 테마를 만드는 기준으로 사용할 수 있는 모범 사례 참조 테마를 제공합니다. [표준 사이트 테마는 GitHub에서 사용할 수 있습니다.](https://github.com/adobe/aem-site-template-standard-theme-e2e)

## 사이트 테마 개발 {#developing-themes}

Adobe은 새 사이트 테마를 만들기 위한 스크립트 세트로 AEM 사이트 테마 빌더를 제공합니다.

[AEM 사이트 테마 빌더는 GitHub의 사용 설명서와 함께 사용할 수 있습니다.](https://github.com/adobe/aem-site-theme-builder) 테마를 사용자 지정하려면 프런트 엔드 개발 경험이 필요합니다.
