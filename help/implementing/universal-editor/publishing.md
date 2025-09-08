---
title: 범용 편집기가 콘텐츠를 게시하는 방법
description: 범용 편집기가 콘텐츠를 게시하는 방법, Sites 콘솔의 프로세스와 다른 점, 그리고 범용 편집기와 함께 작동하는 자체 앱을 개발할 때 고려할 사항에 대해 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
exl-id: 60f0bb4a-ee60-4f73-83ae-8568735474ad
source-git-commit: b967a09df7c2e0f5094a6836fcf5311008081dc0
workflow-type: ht
source-wordcount: '564'
ht-degree: 100%

---

# 범용 편집기가 콘텐츠를 게시하는 방법 {#publishing}

범용 편집기가 콘텐츠를 게시하는 방법, Sites 콘솔의 프로세스와 다른 점, 그리고 범용 편집기와 함께 작동하는 자체 앱을 개발할 때 고려할 사항에 대해 알아봅니다.

>[!TIP]
>
>이 문서는 개발자를 위해 범용 편집기의 게시 프로세스에 대한 세부 정보를 다룹니다. 콘텐츠 작성자의 경우, [콘텐츠 게시 프로세스는 여기에 설명되어 있습니다](/help/sites-cloud/authoring/universal-editor/publishing.md).

## Sites 콘솔 프로세스와의 유사점 {#similarities}

[AEM 페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md) 및 [Sites 콘솔](/help/sites-cloud/authoring/sites-console/introduction.md) 사용자의 경우, 범용 편집기로 콘텐츠를 게시하는 프로세스는 사용자에게 익숙한 방식으로 작동합니다. 즉, AEM에서 게시할 때 콘텐츠는 작성자 계층에서 게시 계층으로 복제됩니다(사용 가능한 경우 및 작성자가 게시할 때 선택하는 옵션에 따라 [미리보기 서비스](/help/sites-cloud/authoring/sites-console/previewing-content.md)로 복제되기도 함).

## 차이점 {#differences}

범용 편집기를 통한 게시가 AEM과 다른 부분은 편집기 자체가 아닌 범용 편집기가 가능하게 하는 앱의 외부 호스팅입니다.

외부에서 호스팅되는 경우 작성자가 편집기 내에서 앱을 열 때 작성자 서비스에서 콘텐츠가 로드되고 방문자가 앱에 액세스할 때 게시 서비스에서 콘텐츠가 로드되도록 하는 것이 해당 웹 앱의 관심사입니다.

## 앱에서 서비스 감지 {#detecting}

편집기 내에서 열려 있음을 감지할 때 적절한 작성자 또는 게시 엔드포인트를 선택하는 앱의 간단한 조건문으로 작성자 또는 게시 서비스에 액세스해야 하는지 여부를 결정할 수 있습니다.

또 다른 방법은 서로 다르게 구성된 두 개의 환경에 앱을 배포하여 하나는 작성자 서비스에서 콘텐츠를 검색하고 다른 하나는 게시 서비스에서 콘텐츠를 검색하도록 하는 것입니다. 작성자가 범용 편집기에서 게시된 URL을 열 수 있도록 하기 위해 게시 측 URL을 작성자 환경의 해당 URL로 “전환”하여(예: `author` 하위 도메인 추가) 작성자가 자동으로 리디렉션되도록 하는 작은 스크립트를 작성할 수 있습니다.

## 요약 {#summary}

범용 편집기의 목적은 특정 패턴을 적용하지 않고 구현을 위한 모든 것을 간단하고 복잡하지 않게 유지하면서 완전히 분리된 방식으로 목표를 달성할 수 있도록 하는 것입니다.

마찬가지로 범용 편집기는 특정 프로젝트에서 콘텐츠를 게재할 서비스를 결정하는 방법에 대한 요구 사항을 제공하지 않습니다. 이를 통해 다양한 가능성을 실현하고 프로젝트에서 자체 요구 사항에 가장 적합한 솔루션을 결정할 수 있도록 합니다.

## 추가 리소스 {#additional-resources}

범용 편집기의 기술적 세부 사항에 대해 자세히 알아보려면 이 개발자 문서를 참조하십시오.

* [범용 편집기 소개](/help/implementing/universal-editor/introduction.md) - 범용 편집기를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공하는 방법에 대해 알아봅니다.
* [AEM에서 범용 편집기 시작하기](/help/implementing/universal-editor/getting-started.md) - 범용 편집기에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
* [범용 편집기 아키텍처](/help/implementing/universal-editor/architecture.md) - 범용 편집기의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](/help/implementing/universal-editor/attributes-types.md) - 범용 편집기에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [범용 편집기 인증](/help/implementing/universal-editor/authentication.md) - 범용 편집기의 인증 방법에 대해 알아봅니다.
