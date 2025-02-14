---
title: 지원되는 클라이언트 플랫폼
description: Adobe Experience Manager as a Cloud Service으로 콘텐츠를 작성하고 AEM으로 게시된 사이트에 액세스하는 데 지원되는 브라우저를 알아봅니다.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 22d4e6b5f87221b2739cf1dd9d59b4652a014316
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---


# 지원되는 클라이언트 플랫폼 {#supported-platforms}

Adobe Experience Manager as a Cloud Service으로 콘텐츠를 작성하고 AEM으로 게시된 사이트에 액세스하는 데 지원되는 브라우저를 알아봅니다.

>[!TIP]
>
>이 문서에서는 AEM as a Cloud Service에서 지원하는 클라이언트 플랫폼을 다룹니다. AEM 프로젝트 개발을 위한 빌드 환경에 대한 자세한 내용은 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) 문서를 참조하십시오.

## 지원 수준 {#support-levels}

Adobe은 AEM의 클라이언트 플랫폼에 대한 다음 수준의 지원을 정의합니다.

| 지원 수준 | 설명 |
|---|---|
| A: 지원됨 | Adobe은 이 구성에 대한 전체 지원 및 유지 관리 기능을 제공합니다. 이 구성은 Adobe의 품질 보증 프로세스에서 다룹니다. |
| R: 제한된 지원 | 지원을 받으려면 프로젝트에서 구성을 사용하도록 Adobe에 정식으로 요청해야 합니다. Adobe에서 확인하면 Adobe은 제한된 지원 프로그램 내에서 모든 지원을 제공합니다. 자세한 내용은 Adobe 고객 지원 센터에 문의하십시오. |
| Z: 지원되지 않음 | 구성이 지원되지 않습니다. Adobe은 구성의 작동 여부에 대해 설명하지 않으며 이를 지원하지 않습니다. |

## 컨텐츠 작성에 지원되는 브라우저 {#authoring}

AEM 사용자 인터페이스는 노트북, 데스크탑 컴퓨터 및 태블릿 장치(예: Apple iPad 또는 Microsoft Surface)에 있는 더 큰 화면에 최적화되어 있습니다. 작성 사용 사례에 대해서는 휴대폰 폼 팩터가 지원되지 않습니다.

Adobe Experience Manager 사용자 인터페이스는 [작성 방법에 따라 다음 클라이언트 플랫폼에서 작동합니다.](/help/edge/authoring-methods.md)

* [범용 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)
* [Sidekick](/help/edge/docs/sidekick.md)을(를) 사용하여 [문서 기반 작성](/help/edge/docs/authoring.md)

모든 브라우저는 기본 플러그인 및 추가 기능 세트로 테스트됩니다.

| 브라우저 | 유니버설 편집기 지원 수준 | 페이지 편집기 지원 수준 | Sidekick 지원 수준 |
|---|---|---|---|
| Google Chrome(에버그린) | A: 지원됨 | A: 지원됨 | A: 지원됨 |
| Microsoft Edge (에버그린) | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| Mozilla Firefox (evergreen) | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| Mozilla Firefox 최신 ESR [1] | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| macOS의 Safari(에버그린) | A: 지원됨 | A: 지원됨 | Z: 지원되지 않음 |
| iOS의 Safari(evergreen) [2] | Z: 지원되지 않음 | A: 지원됨 | Z: 지원되지 않음 |

1. Firefox의 확장 지원 릴리스([mozilla.org에 대한 자세한 정보](https://www.mozilla.org/en-US/firefox/enterprise/))
1. Apple iPad만 지원

>[!NOTE]
>
>**빠른 릴리스 주기를 사용하는 브라우저 지원:**
>
>Firefox, Chrome 및 Edge 릴리스 업데이트는 정기적으로 제공됩니다. Adobe은 이러한 브라우저의 향후 버전에 대해 위에 나열된 대로 지원 수준을 유지하기 위해 최선을 다하고 있습니다.

## 웹 사이트에 대해 지원되는 브라우저 {#websites}

AEM에서 렌더링하는 웹 사이트에 대한 브라우저 지원은 AEM 페이지 템플릿, 블록, 디자인 및 구성 요소 출력의 구현에 따라 다릅니다. 따라서 프로젝트를 구현하는 개발자는 궁극적으로 사이트의 호환성을 제어합니다.

AEM [프로젝트 보일러 플레이트,](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md#create-github-project) [핵심 구성 요소,](/help/implementing/developing/components/overview.md#aem-core-components) 및 [WKND 샘플 사이트](/help/implementing/developing/introduction/develop-wknd-tutorial.md)는 모두 최신 브라우저와 호환됩니다.
