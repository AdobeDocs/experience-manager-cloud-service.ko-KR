---
title: Universal Editor로 콘텐츠 게시
description: Universal Editor가 콘텐츠를 게시하는 방식과 앱이 게시된 콘텐츠를 처리하는 방법에 대해 살펴보세요.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 69%

---


# Universal Editor로 콘텐츠 게시 {#publishing}

Universal Editor가 콘텐츠를 게시하는 방식과 앱이 게시된 콘텐츠를 처리하는 방법에 대해 살펴보세요.

## AEM과의 유사점 {#similarities}

AEM 사용자의 경우 범용 편집기를 사용하여 콘텐츠를 게시하는 프로세스는 익숙한 대로 작동합니다. AEM에서 게시할 때 콘텐츠는 작성자 계층에서 게시 계층으로 복제됩니다.

## 차이점 {#differences}

유니버설 편집기로 게시할 때 약간 다른 점은 편집기 자체가 아니라, 유니버설 편집기가 가능하게 하는 앱의 외부 호스팅입니다.

외부에서 호스팅되는 경우 작성자가 편집기 내에서 앱을 열 때 작성자 계층에서 콘텐츠가 로드되고 방문자가 앱에 액세스할 때 게시 계층에서 콘텐츠가 로드되도록 하는 것이 해당 웹 앱의 관심사입니다.

## 앱에서 계층 감지 {#detecting}

편집기 내에서 열려 있음을 감지할 때 적절한 작성자 또는 게시 엔드포인트를 선택하는 앱의 간단한 조건문으로 작성자 또는 게시 계층에 액세스해야 하는지 여부를 결정할 수 있습니다.

또 다른 방법은 서로 다르게 구성된 두 개의 환경에 앱을 배포하여 하나는 작성자 계층에서 콘텐츠를 검색하고 다른 하나는 게시 계층에서 콘텐츠를 검색하도록 하는 것입니다. 작성자가 유니버설 편집기에서 게시된 URL을 열 수 있도록 하기 위해 작은 스크립트를 만들어 게시측 URL을 작성자 환경의 동등한 URL로 &quot;변환&quot;할 수 있습니다(예: `author` 하위 도메인)으로 변경하여 작성자가 자동으로 리디렉션되도록 합니다.

## 요약 {#summary}

Universal Editor의 목적은 특정 패턴을 적용하지 않고 구현을 위한 모든 것을 간단하고 복잡하지 않게 유지하면서 완전히 분리된 방식으로 목표를 달성할 수 있도록 하는 것입니다.

마찬가지로 Universal Editor는 특정 프로젝트에서 콘텐츠를 게재할 계층을 결정하는 방법에 대한 요구 사항을 제공하지 않습니다. 오히려 몇 가지 가능성을 지원하며 프로젝트에서 자체 요구 사항에 가장 적합한 솔루션을 결정할 수 있습니다.

## 추가 리소스 {#additional-resources}

유니버설 편집기로 콘텐츠를 작성하는 방법에 대해 알아보려면 이 문서 를 참조하십시오.

* [Universal Editor로 콘텐츠 작성](authoring.md) - 콘텐츠 작성자가 Universal Editor를 사용하여 콘텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아봅니다.

유니버설 편집기의 기술 세부 정보에 대한 자세한 내용은 다음 개발자 문서를 참조하십시오.

* [Universal Editor 소개](/help/implementing/universal-editor/introduction.md) - Universal Editor를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공하는 방법에 대해 알아봅니다.
* [AEM에서 Universal Editor 시작하기](/help/implementing/universal-editor/getting-started.md) - Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
* [Universal Editor 아키텍처](/help/implementing/universal-editor/architecture.md) - Universal Editor의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](/help/implementing/universal-editor/attributes-types.md) - Universal Editor에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [Universal Editor 인증](/help/implementing/universal-editor/authentication.md) - Universal Editor의 인증 방법에 대해 알아봅니다.

