---
title: Edge Delivery Services 컨텐츠 게시
description: 컨텐츠 게시가 Edge Delivery Services에서 작동하는 방법 및 Edge Delivery Services에서 AEM 컨텐츠를 게시하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
source-git-commit: e3bbcfa3fcef1ed1e5b6cf2da5a17c7e636b9539
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---


# Edge Delivery Services 컨텐츠 게시 {#publishing-edge}

Edge Delivery Services을 사용하면 콘텐츠 소스에 관계없이 콘텐츠를 원활하게 게시할 수 있습니다.

* 문서 기반 콘텐츠 - 다음을 참조하십시오. [섹션 게시](/help/edge/docs/authoring.md) Edge Delivery Services 설명서.
* AEM 콘텐츠 - 아래 세부 정보를 참조하십시오.

## AEM에서 플로우 게시 {#publishing-flow}

범용 편집기를 사용하여 AEM 콘텐츠를 작성할 때 게시는 를 클릭하는 것처럼 간단합니다. **게시** 단추를 클릭합니다. 문서를 참조하십시오. [범용 편집기로 콘텐츠 게시.](/help/implementing/universal-editor/publishing.md)

게시할 때의 정보 흐름은 다음과 같습니다. 작성자가 게시를 시작하면 이 흐름은 자동으로 표시되며 정보 목적으로 여기에 표시됩니다.

![AEM에서 Edge Delivery Services으로 게시할 때의 정보 흐름](assets/publishing-flow.png)

1. 콘텐츠 작성자는 범용 편집기에서 AEM 콘텐츠를 게시합니다.
1. 게시 이벤트가 파이프라인 Adobe 큐에 푸시됩니다.
1. Edge 게재 게시 서비스는 Edge 게재 관리 API에 관련 이벤트를 전달합니다.
1. 에지 전달은 AEM 작성자로부터 의미 있는 HTML을 가져오고 수집합니다.
1. AEM이 게시 상태로 업데이트되었습니다.

## 시작하는 방법 {#how-to-get-started}

이 기능에 액세스하려면 Adobe 담당자에게 문의하십시오.
