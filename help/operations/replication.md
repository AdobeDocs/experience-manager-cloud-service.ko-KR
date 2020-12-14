---
title: 복제
description: 배포 및 문제 해결 복제.
translation-type: tm+mt
source-git-commit: abb45225e880f3d08b9d26c29e243037564acef0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# 복제 {#replication}

Adobe Experience Manager은 Cloud Service의 [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) 기능을 사용하여 컨텐츠를 AEM 런타임 외부에 있는 Adobe I/O에서 실행되는 파이프라인 서비스로 복제하도록 이동합니다.

>[!NOTE]
>
>자세한 내용은 [배포](/help/core-concepts/architecture.md#content-distribution)를 참조하십시오.

## 콘텐츠 게시 방법 {#methods-of-publishing-content}

### 빠른 게시 취소/게시 - 계획된 게시 취소/게시 취소 {#publish-unpublish}

작성자를 위한 이러한 표준 AEM 기능은 AEM Cloud Service과 함께 변경되지 않습니다.

### 설정 및 해제 시간 - 트리거 구성 {#on-and-off-times-trigger-configuration}

**On Time** 및 **Off Time**&#x200B;의 추가 가능성은 페이지 속성](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)의 [기본 탭에서 사용할 수 있습니다.

자동 복제를 실현하려면 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md) **오프 트리거 구성**&#x200B;에서 **자동 복제**&#x200B;를 활성화해야 합니다.

![트리거 구성 해제](/help/operations/assets/replication-on-off-trigger.png)

### 트리 활성화 {#tree-activation}

트리 활성화를 수행하려면:

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포**&#x200B;로 이동합니다.
2. 카드 **forwardPublisher** 선택
3. forwardPublisher 웹 콘솔 UI에서 한 번, **배포** 선택

   ![배포](assets/distribute.png "배포")
4. 경로 브라우저에서 경로를 선택하고 필요에 따라 노드 추가, 트리 또는 삭제를 선택하고 **제출**

## 문제 해결 {#troubleshooting}

복제 문제를 해결하려면 AEM 작성자 서비스 웹 UI의 복제 대기열로 이동합니다.

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포**&#x200B;로 이동합니다.
2. 카드 **forwardPublisher** 선택
   ![](assets/status.png "StatusStatus")
3. 녹색이어야 하는 큐 상태를 확인합니다.
4. 복제 서비스에 대한 연결을 테스트할 수 있습니다.
5. 콘텐트 발행물의 내역을 표시하는 **로그** 탭을 선택합니다

![로그 ](assets/logs.png "로그")

콘텐츠를 게시할 수 없는 경우 전체 게시가 AEM 게시 서비스에서 되돌려집니다.
이러한 경우 게시를 취소하도록 만든 항목을 식별하려면 대기열을 검토해야 합니다. 빨간색 상태를 표시하는 큐를 클릭하면 보류 중인 항목이 있는 대기열이 표시되며 필요한 경우 단일 또는 모든 항목을 지울 수 있습니다.
