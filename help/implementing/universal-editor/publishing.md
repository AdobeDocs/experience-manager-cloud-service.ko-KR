---
title: Universal Visual Editor로 콘텐츠 게시
description: Universal Visual Editor에서 콘텐츠를 게시하는 방법과 앱에서 게시된 콘텐츠를 처리하는 방법에 대해 알아봅니다.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 0f62245d31074ab7a64d86b97ef3b1a8d7533001
workflow-type: ht
source-wordcount: '367'
ht-degree: 100%

---


# Universal Visual Editor로 콘텐츠 게시 {#publishing}

Universal Visual Editor에서 콘텐츠를 게시하는 방법과 앱에서 게시된 콘텐츠를 처리하는 방법에 대해 알아봅니다.

## AEM과의 유사점 {#similarities}

Universal Visual Editor로 콘텐츠를 게시하는 프로세스는 AEM 사용자에게 익숙한 방식으로 작동합니다. AEM에서 게시할 때 콘텐츠는 작성자 계층에서 게시 계층으로 복제됩니다.

## 차이점 {#differences}

Universal Visual Editor를 통한 게시가 AEM과 다른 부분은 편집기 자체가 아닌 Universal Editor가 가능하게 하는 앱의 외부 호스팅입니다.

외부에서 호스팅되는 경우 작성자가 편집기 내에서 앱을 열 때 작성자 계층에서 콘텐츠가 로드되고 방문자가 앱에 액세스할 때 게시 계층에서 콘텐츠가 로드되도록 하는 것이 해당 웹 앱의 관심사입니다.

## 앱에서 계층 감지 {#detecting}

편집기 내에서 열려 있음을 감지할 때 적절한 작성자 또는 게시 엔드포인트를 선택하는 앱의 간단한 조건문으로 작성자 또는 게시 계층에 액세스해야 하는지 여부를 결정할 수 있습니다.

또 다른 방법은 서로 다르게 구성된 두 개의 환경에 앱을 배포하여 하나는 작성자 계층에서 콘텐츠를 검색하고 다른 하나는 게시 계층에서 콘텐츠를 검색하도록 하는 것입니다. 작성자가 Universal Editor에서 게시된 URL을 열 수 있도록 하기 위해 게시 측 URL을 작성자 환경의 해당 URL로 “전환”하여(예: `author` 하위 도메인 추가) 작성자가 자동으로 리디렉션되도록 하는 작은 스크립트를 작성할 수 있습니다.

## 요약 {#summary}

Universal Editor의 목적은 특정 패턴을 적용하지 않고 구현을 위한 모든 것을 간단하고 복잡하지 않게 유지하면서 완전히 분리된 방식으로 목표를 달성할 수 있도록 하는 것입니다.

마찬가지로 Universal Editor는 특정 프로젝트에서 콘텐츠를 게재할 계층을 결정하는 방법에 대한 요구 사항을 제공하지 않습니다. 이를 통해 다양한 가능성을 실현하고 프로젝트에서 자체 요구 사항에 가장 적합한 솔루션을 결정할 수 있도록 합니다.
