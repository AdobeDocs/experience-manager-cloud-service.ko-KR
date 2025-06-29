---
title: 지원되는 클라이언트 플랫폼
description: Adobe Experience Manager as a Cloud Service를 사용하여 콘텐츠를 작성하고 AEM으로 게시된 사이트에 액세스하는 데 지원되는 브라우저는 알아봅니다.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 7ddd0a75-621a-4499-91d1-7b3408a68269
source-git-commit: d53bfe103ff8e40c8221805a2d66faf3c5cd3823
workflow-type: ht
source-wordcount: '419'
ht-degree: 100%

---

# 지원되는 클라이언트 플랫폼 {#supported-platforms}

Adobe Experience Manager as a Cloud Service를 사용하여 콘텐츠를 작성하고 AEM으로 게시된 사이트에 액세스하는 데 지원되는 브라우저는 알아봅니다.

>[!TIP]
>
>이 문서에서는 AEM as a Cloud Service에서 지원하는 클라이언트 플랫폼을 설명합니다. AEM 프로젝트를 개발하기 위한 빌드 환경에 대한 자세한 내용은 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) 문서를 참조하십시오.

## 지원 수준 {#support-levels}

Adobe는 AEM 클라이언트 플랫폼에 대해 다음과 같은 지원 수준을 정의합니다.

| 지원 수준 | 설명 |
|---|---|
| A: 지원됨 | Adobe는 이 구성에 대한 전체 지원과 유지 관리를 제공합니다. 이 구성은 Adobe 품질 보증 프로세스에 따라 처리됩니다. |
| R: 제한된 지원 | 프로젝트에서 구성을 사용하기 위해 지원을 받으려면 Adobe에 공식적으로 요청해야 합니다. Adobe에서 요청을 확인하면 제한된 지원 프로그램 내에서 전체 지원을 제공합니다. 자세한 내용은 Adobe 고객 지원에 문의하십시오. |
| Z: 지원되지 않음 | 구성이 지원되지 않습니다. Adobe에서는 해당 구성이 작동하는지 여부에 대해 언급하지 않으며 이를 지원하지 않습니다. |

## 콘텐츠 작성에 지원되는 브라우저 {#authoring}

AEM 사용자 인터페이스는 노트북, 데스크탑 컴퓨터, 태블릿 기기(예: Apple iPad 또는 Microsoft Surface)의 대형 화면에 최적화되어 있습니다. 휴대폰 폼 팩터는 어떠한 작성 사용 사례에도 지원되지 않습니다.

Adobe Experience Manager 사용자 인터페이스는 [작성 방법](/help/edge/overview.md#authoring-method)에 따라 다음과 같은 클라이언트 플랫폼에서 작동합니다.

* [범용 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)
* [Sidekick](/help/edge/docs/sidekick.md)을 사용한 [문서 기반 작성](/help/edge/docs/authoring.md)

모든 브라우저는 기본 플러그인 및 추가 기능 세트에 대한 테스트를 완료했습니다.

| 브라우저 | 범용 편집기 지원 수준 | 페이지 편집기 지원 수준 | Sidekick 지원 수준 |
|---|---|---|---|
| Google Chrome (항상 최신 상태) | A: 지원됨 | A: 지원됨 | A: 지원됨 |
| Microsoft Edge (항상 최신 상태) | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| Mozilla Firefox (항상 최신 상태) | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| Mozilla Firefox 최신 ESR [1] | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| macOS의 Safari (항상 최신 상태) | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| iPadOS용 Safari (항상 최신 상태) | Z: 지원되지 않음 | A: 지원됨 | Z: 지원되지 않음 |

1. Firefox의 확장 지원 릴리스([mozilla.org에서 자세히 알아보기](https://www.mozilla.org/en-US/firefox/enterprise/))

>[!NOTE]
>
>**릴리스 주기가 빠른 브라우저 지원:**
>
>Firefox, Chrome, Edge는 정기적으로 업데이트를 릴리스합니다. Adobe는 해당 브라우저에서 향후 제공되는 버전에 대해서도 위에 나열된 지원 수준을 유지하기 위해 최선을 다하고 있습니다.

## 웹 사이트에 지원되는 브라우저 {#websites}

AEM에서 렌더링한 웹 사이트에 대한 브라우저 지원은 AEM 페이지 템플릿, 블록, 디자인 및 구성 요소 출력의 구현에 따라 달라집니다. 따라서 궁극적으로 프로젝트를 구현하는 개발자가 사이트의 호환성을 제어하게 됩니다.

AEM [프로젝트 상용구,](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md#create-github-project) [핵심 구성 요소,](/help/implementing/developing/components/overview.md#aem-core-components) [WKND 샘플 사이트](/help/implementing/developing/introduction/develop-wknd-tutorial.md)는 모든 최신 브라우저와 호환됩니다.
