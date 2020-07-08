---
title: 복제
description: 배포 및 문제 해결 복제.
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 3%

---


# 복제 {#replication}

Adobe Experience Manager은 AEM 런타임 외부에 있는 Adobe I/O에서 실행되는 파이프라인 서비스로 [복제하기 위해 컨텐츠를 Cloud Service으로](https://sling.apache.org/documentation/bundles/content-distribution.html) 이동합니다.

>[!NOTE]
>
>자세한 [내용은 배포](/help/core-concepts/architecture.md#content-distribution) 를 참조하십시오.

## 컨텐츠 게시 방법 {#methods-of-publishing-content}

### 빠른 게시 취소/게시 - 계획된 게시 취소/게시 {#publish-unpublish}

작성자를 위한 이러한 표준 AEM 기능은 AEM Cloud Service과 함께 변경되지 않습니다.

### 트리 활성화 {#tree-activation}

트리 활성화를 수행하려면

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포로 이동합니다**
2. 카드 forwardPublisher **선택**
3. forwardPublisher 웹 콘솔 UI에서 [배포]를 **선택합니다**

   ![배포](assets/distribute.png "배포")
4. 경로 브라우저에서 경로를 선택하고 필요에 따라 노드, 트리 또는 삭제를 선택한 다음 제출을 **선택합니다**

## 문제 해결 {#troubleshooting}

복제 문제를 해결하려면 AEM Author 서비스 웹 UI의 복제 대기열로 이동합니다.

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포로 이동합니다**
2. 카드 forwardPublisher **선택**
   ![상태](assets/status.png "상태")
3. 녹색이어야 하는 큐 상태를 확인합니다.
4. 복제 서비스에 대한 연결을 테스트할 수 있습니다
5. 컨텐츠 **발행물의** 내역을 보여주는 [로그] 탭을 선택합니다.

![로그](assets/logs.png "로그")

컨텐츠를 게시할 수 없는 경우 AEM Publish 서비스에서 전체 게시가 되돌려집니다.
이러한 경우 발행물 취소를 일으킨 항목을 식별하기 위해 대기열을 검토해야 합니다. 빨간색 상태를 보여주는 큐를 클릭하면 보류 중인 항목이 있는 대기열이 나타나며 필요한 경우 단일 또는 모든 항목을 지울 수 있습니다.
