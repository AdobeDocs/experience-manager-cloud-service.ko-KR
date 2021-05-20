---
title: 복제
description: 배포 및 문제 해결 복제
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: eb92c66f2b9e8e6ec859114da2de049747ec251e
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 2%

---

# 복제 {#replication}

Adobe Experience Manager as a Cloud Service은 [Sling 컨텐츠 배포](https://sling.apache.org/documentation/bundles/content-distribution.html) 기능을 사용하여 컨텐츠를 AEM 런타임의 외부에 있는 Adobe I/O에서 실행되는 파이프라인 서비스에 복제하도록 이동합니다.

>[!NOTE]
>
>자세한 내용은 [배포](/help/core-concepts/architecture.md#content-distribution)를 참조하십시오.

## 컨텐츠 게시 방법 {#methods-of-publishing-content}

### 빠른 게시 취소/게시 - 계획된 게시 취소/게시 취소 {#publish-unpublish}

작성자를 위한 이러한 표준 AEM 기능은 AEM Cloud Service과 변경되지 않습니다.

### 설정 및 해제 시간 - 트리거 구성 {#on-and-off-times-trigger-configuration}

**On Time** 및 **Off Time**&#x200B;의 추가 가능성은 페이지 속성](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)의 [기본 탭에서 사용할 수 있습니다.

이에 대한 자동 복제를 실현하려면 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md) **오프 트리거 구성**&#x200B;에서 **자동 복제**&#x200B;를 활성화해야 합니다.

![OSGi 켜기 트리거 구성](/help/operations/assets/replication-on-off-trigger.png)

### 트리 활성화 {#tree-activation}

트리 활성화를 수행하려면 다음을 수행합니다.

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포**&#x200B;로 이동합니다.
2. 카드 **forwardPublisher**&#x200B;를 선택합니다.
3. forwardPublisher Web Console UI에서 **배포**를 선택합니다.

   ![](assets/distribute.png "DistributeDistribution")
4. 경로 브라우저에서 경로를 선택하고 필요에 따라 노드, 트리 또는 삭제를 선택하고 **Submit**&#x200B;을 선택합니다.

### 컨텐츠 트리 게시 워크플로우 {#publish-content-tree-workflow}

아래 그림과 같이 **도구 - 워크플로우 - 모델**&#x200B;을 선택하고 **컨텐츠 트리 게시** 기본 워크플로우 모델을 복사하여 트리 복제를 트리거할 수 있습니다.

![](/help/operations/assets/publishcontenttreeworkflow.png)

원본 모델을 수정하거나 호출하지 마십시오. 대신 먼저 모델을 복사한 다음 해당 복사본을 수정하거나 호출해야 합니다.

모든 워크플로우와 마찬가지로 API를 통해 호출할 수도 있습니다. 자세한 내용은 [프로그래밍 방식으로 워크플로우와 상호 작용](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem)을 참조하십시오.

또는 `Publish Content Tree` 프로세스 단계를 사용하는 워크플로우 모델을 만들어 이를 수행할 수도 있습니다.

1. AEM as a Cloud Service 홈 페이지에서 **도구 - 워크플로우 - 모델**&#x200B;로 이동합니다.
1. Workflow Models 페이지에서 화면의 오른쪽 위 모서리에 있는 **Create** 키를 누릅니다
1. 모델에 제목과 이름을 추가합니다. 자세한 내용은 [워크플로우 모델 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)를 참조하십시오
1. 목록에서 새로 만든 모델을 선택하고 **Edit** 키를 누릅니다
1. 다음 창에서 프로세스 단계 를 현재 모델 플로우로 끌어서 놓습니다.

   ![프로세스 단계](/help/operations/assets/processstep.png)

1. 흐름의 Process 단계를 클릭하고 공구모양 아이콘을 눌러 **Configure**&#x200B;을 선택합니다
1. **프로세스** 탭을 클릭하고 드롭다운 목록에서 `Publish Content Tree` 를 선택합니다

   ![Treeactivation](/help/operations/assets/newstep.png)

1. **인수** 필드에서 추가 매개 변수를 설정합니다. 여러 개의 쉼표로 구분된 인수를 함께 실행할 수 있습니다. 예:

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >매개 변수 목록을 보려면 아래의 **매개 변수** 섹션을 참조하십시오.

1. **완료** 키를 눌러 워크플로우 모델을 저장합니다.

**매개 변수**

* `replicateAsParticipant` (부울 값, 기본값: `false`). `true`로 구성된 경우, 복제에서는 참가자 단계를 수행한 주도자의 `userid`을 사용하고 있습니다.
* `enableVersion` (부울 값, 기본값: `true`). 이 매개 변수는 복제 시 새 버전을 만들지 여부를 결정합니다.
* `agentId` (문자열 값, 기본값은 모든 활성화된 에이전트가 사용됨을 의미합니다.)
* `filters` (문자열 값, 기본값은 모든 경로가 활성화됨을 의미합니다.) 사용 가능한 값은 다음과 같습니다.
   * `onlyActivated` - 활성화됨으로 표시되지 않은 경로만 활성화됩니다.
   * `onlyModified` - 활성화 날짜보다 늦게 수정 날짜가 있고 이미 활성화된 경로만 활성화합니다.
   * 위의 파이프 &quot;|&quot;을 사용하여 ORed를 만들 수 있습니다. 예, `onlyActivated|onlyModified`.

**로깅**

트리 활성화 워크플로우 단계가 시작되면 INFO 로그 수준에 구성 매개 변수를 기록합니다. 경로가 활성화되면 INFO 문도 기록됩니다.

그러면 워크플로우 단계가 모든 경로를 복제한 후 최종 INFO 문이 기록됩니다.

또한 `com.day.cq.wcm.workflow.process.impl` 아래의 로거의 로그 수준을 DEBUG/TRACE으로 높여 더 많은 로그 정보를 얻을 수 있습니다.

오류가 발생하는 경우 워크플로우 단계가 `WorkflowException`으로 종료되고 여기에서 기본 예외를 래핑합니다.

아래에서는 샘플 게시 컨텐츠 트리 워크플로우 중에 생성된 로그 예제를 찾을 수 있습니다.

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**지원 다시 시작**

워크플로우는 컨텐츠를 청크 단위로 처리하며, 각 청크는 게시할 전체 컨텐츠의 하위 집합을 나타냅니다. 어떤 이유로든 워크플로우가 시스템에 의해 중지되면 다시 시작되고 아직 처리되지 않은 청크가 처리됩니다. 로그 문은 특정 경로에서 컨텐츠가 다시 시작되었다고 나타냅니다.

## 문제 해결 {#troubleshooting}

복제 문제를 해결하려면 AEM 작성자 서비스 웹 UI의 복제 큐로 이동합니다.

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포**&#x200B;로 이동합니다.
2. 카드 **forwardPublisher**를 선택합니다.
   ![](assets/status.png "StatusStatus")
3. 녹색이어야 하는 큐 상태를 확인합니다
4. 복제 서비스에 대한 연결을 테스트할 수 있습니다
5. 컨텐츠 게시물의 내역을 보여주는 **로그** 탭을 선택합니다

![](assets/logs.png "LogsLogs")

컨텐츠를 게시할 수 없는 경우에는 전체 게시가 AEM 게시 서비스에서 복귀됩니다.
이 경우 게시가 취소되는 원인이 되는 항목을 식별하려면 대기열을 검토해야 합니다. 빨간색 상태를 표시하는 큐를 클릭하면 보류 중인 항목이 있는 큐가 표시되며, 필요한 경우 단일 또는 모든 항목을 지울 수 있습니다.
