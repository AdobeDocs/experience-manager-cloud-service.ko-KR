---
title: 유니버설 편집기가 콘텐츠를 게시하는 방법
description: 유니버설 편집기가 콘텐츠를 게시하는 방법, 사이트 콘솔의 프로세스와 차이점 및 이 콘텐츠와 사용할 나만의 앱을 개발할 때 고려할 사항에 대해 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0ee6689460ac0ecc5c025fb6a940d69a16699c85
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 25%

---


# 유니버설 편집기가 콘텐츠를 게시하는 방법 {#publishing}

유니버설 편집기가 콘텐츠를 게시하는 방법, 사이트 콘솔의 프로세스와 차이점 및 이 콘텐츠와 사용할 나만의 앱을 개발할 때 고려할 사항에 대해 알아봅니다.

>[!TIP]
>
>이 문서에서는 개발자를 위한 유니버설 편집기 게시 프로세스에 대한 세부 사항을 다룹니다. 콘텐츠 작성자의 경우 [콘텐츠를 게시하는 프로세스는 여기에 설명되어 있습니다.](/help/sites-cloud/authoring/universal-editor/publishing.md)

## 사이트 콘솔 프로세스와의 유사성 {#similarities}

[AEM 페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md) 및 [사이트 콘솔 사용자의 경우](/help/sites-cloud/authoring/sites-console/introduction.md) 유니버설 편집기를 사용하여 콘텐츠를 게시하는 프로세스는 익숙한 대로 작동합니다. AEM에서 게시할 때 콘텐츠는 작성자 서비스에서 게시 서비스(또는 가능한 경우 및 작성자가 게시할 때 선택한 옵션에 따라 [미리보기 서비스](/help/sites-cloud/authoring/sites-console/previewing-content.md)로 복제됩니다.

## 차이점 {#differences}

유니버설 편집기로 게시할 때 약간 다른 점은 편집기 자체가 아니라, 유니버설 편집기가 가능하게 하는 앱의 외부 호스팅입니다.

외부적으로 호스팅되는 경우, 편집기 내에서 작성자가 앱을 열 때 작성자 서비스에서 콘텐츠가 로드되고, 방문자가 앱에 액세스할 때 게시 서비스에서 콘텐츠가 로드되도록 하는 것이 웹 앱의 문제입니다.

## 앱에서 서비스 감지 {#detecting}

작성자 또는 게시 서비스에 액세스해야 하는지 여부를 결정하는 작업은 편집기 내에서 해당 작성자 또는 게시 끝점이 열려 있음을 감지할 때 앱의 간단한 조건문을 사용하여 적절한 작성자 또는 게시 끝점을 선택할 수 있습니다.

다른 옵션은 다르게 구성된 두 개의 다른 환경에 앱을 배포하여 작성자 서비스에서 콘텐츠를 검색하고 게시 서비스에서 콘텐츠를 검색하도록 하는 것입니다. 작성자가 유니버설 편집기에서 게시된 URL을 열 수 있도록 하기 위해 작성자가 자동으로 리디렉션될 수 있도록 작성자 환경(예: `author` 하위 도메인을 앞에 붙여서)에서 게시측 URL을 이와 동등한 것으로 &quot;변환&quot;하는 작은 스크립트를 만들 수 있습니다.

## 요약 {#summary}

Universal Editor의 목적은 특정 패턴을 적용하지 않고 구현을 위한 모든 것을 간단하고 복잡하지 않게 유지하면서 완전히 분리된 방식으로 목표를 달성할 수 있도록 하는 것입니다.

마찬가지로 유니버설 편집기는 특정 프로젝트가 콘텐츠를 제공할 서비스를 결정하는 방법에 대한 요구 사항을 만들지 않습니다. 오히려 몇 가지 가능성을 지원하며 프로젝트에서 자체 요구 사항에 가장 적합한 솔루션을 결정할 수 있습니다.

## 추가 리소스 {#additional-resources}

유니버설 편집기의 기술 세부 정보에 대한 자세한 내용은 다음 개발자 문서를 참조하십시오.

* [Universal Editor 소개](/help/implementing/universal-editor/introduction.md) - Universal Editor를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공하는 방법에 대해 알아봅니다.
* [AEM에서 Universal Editor 시작하기](/help/implementing/universal-editor/getting-started.md) - Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
* [Universal Editor 아키텍처](/help/implementing/universal-editor/architecture.md) - Universal Editor의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](/help/implementing/universal-editor/attributes-types.md) - Universal Editor에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [Universal Editor 인증](/help/implementing/universal-editor/authentication.md) - Universal Editor의 인증 방법에 대해 알아봅니다.
