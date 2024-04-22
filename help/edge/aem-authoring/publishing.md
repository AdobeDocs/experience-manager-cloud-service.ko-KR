---
title: Edge Delivery Services용 콘텐츠 게시
description: Edge Delivery Services를 통한 콘텐츠 게시 방법과 Edge Delivery Services를 사용한 AEM 콘텐츠 게시 방법을 알아보십시오.
feature: Edge Delivery Services
exl-id: 32fbb144-9175-47a9-bb5a-ca15f3fcd2d8
source-git-commit: 11f721b4a617c99e30329d7196f42d7b48067f1b
workflow-type: ht
source-wordcount: '280'
ht-degree: 100%

---


# Edge Delivery Services용 콘텐츠 게시 {#publishing-edge}

Edge Delivery Services를 사용하여 콘텐츠 소스에 관계없이 원활하게 콘텐츠를 게시합니다.

* 문서 기반 콘텐츠 - Edge Delivery Services 설명서의 [게시 섹션](/help/edge/docs/authoring.md)을 참조하십시오.
* AEM 콘텐츠 - 자세한 내용은 아래를 참조하십시오.

## AEM에서 흐름 게시 {#publishing-flow}

Universal Editor를 사용하여 AEM 콘텐츠를 작성하는 경우, Universal Editor의 **게시** 버튼을 클릭하기만 하면 간단하게 게시할 수 있습니다. [Universal Editor를 사용하여 콘텐츠 게시](/help/sites-cloud/authoring/universal-editor/publishing.md) 문서를 참조하십시오.

게시할 때 정보 흐름은 다음과 같습니다. 작성자가 게시를 시작하면 이 흐름은 자동으로 이루어지며, 여기에 정보 제공 목적으로 설명되어 있습니다.

>[!NOTE]
>
>작성 UI 또는 워크플로에서 게시된 경로는 하루에 최대 5000개까지 허용됩니다. 대량 게시 작업 부하를 유발하는 통합은 지원되지 않습니다.

![AEM에서 Edge Delivery Services로 게시할 때 정보 흐름](assets/publishing-flow.png)

1. 콘텐츠 작성자는 Universal Editor에서 AEM 콘텐츠를 게시합니다.
1. 게시 이벤트가 Adobe 파이프라인 큐로 푸시됩니다.
1. Edge Delivery Services 게시 서비스는 관련 이벤트를 Edge Delivery Services 관리 API에 전달합니다.
1. Edge Delivery는 AEM 작성자에서 유의미한 HTML을 가져와서 수집합니다.
1. AEM은 게시 상태로 업데이트됩니다.

>[!NOTE]
>
>기본적으로 Edge Delivery Services 관리 API는 보호되지 않으며 인증 없이 문서를 게시하거나 게시 취소하는 데 사용될 수 있습니다. [작성자에 대한 인증 구성](https://www.aem.live/docs/authentication-setup-authoring)에 설명된 대로 관리 API에 대한 인증을 구성하려면 게시 서비스에 대한 액세스 권한을 부여하는 API_KEY를 사용하여 프로젝트를 프로비저닝해야 합니다. [Slack의 Adobe 팀에 문의](/help/edge/docs/slack.md)하여 안내를 받으십시오.

