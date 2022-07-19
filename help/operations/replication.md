---
title: 복제
description: 배포 및 문제 해결 복제
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: b79752c43cd9907236b511aa1be60b5b2256a7b8
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 4%

---

# 복제 {#replication}

Adobe Experience Manager as a Cloud Service은 [Sling 컨텐츠 배포](https://sling.apache.org/documentation/bundles/content-distribution.html) AEM 런타임 외부에 있는 Adobe I/O에서 실행되는 파이프라인 서비스에 복제하기 위해 컨텐츠를 이동하는 기능.

>[!NOTE]
>
>읽기 [배포](/help/overview/architecture.md#content-distribution) 추가 정보.

## 컨텐츠 게시 방법 {#methods-of-publishing-content}

### 빠른 게시 취소/게시 - 계획된 게시 취소/게시 {#publish-unpublish}

이렇게 하면 게시 관리 방법을 통해 가능한 추가 옵션 없이 선택한 페이지를 즉시 게시할 수 있습니다.

자세한 내용은 [게시 관리](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### 설정 및 해제 시간 - 트리거 구성 {#on-and-off-times-trigger-configuration}

의 추가적인 가능성 **시간** 및 **해제 시간** 다음에서 사용 가능 [페이지 속성의 기본 탭](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

자동 복제를 실현하려면 다음을 활성화해야 합니다 **자동 복제** 에서 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md) **트리거 구성 해제**:

![OSGi 켜기 트리거 구성](/help/operations/assets/replication-on-off-trigger.png)

### 게시 관리 {#manage-publication}

게시 관리는 빠른 게시보다 더 많은 옵션을 제공하여 하위 페이지 포함, 참조 맞춤화, 적용 가능한 워크플로 시작 등의 작업을 허용함과 동시에 나중에 게시할 수 있는 옵션을 제공합니다.

나중에 게시 옵션에 대한 폴더의 하위 항목을 포함하면 이 문서에 설명된 컨텐츠 트리 게시 작업 과정이 호출됩니다.

게시 관리에 대한 자세한 내용은 [Fundamentals 설명서 게시](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### 게시 콘텐츠 트리 워크플로 {#publish-content-tree-workflow}

다음을 선택하여 트리 복제를 트리거할 수 있습니다 **도구 - 워크플로우 - 모델** 복사 **컨텐츠 트리 게시** 아래와 같이 기본 워크플로우 모델:

![](/help/operations/assets/publishcontenttreeworkflow.png)

원본 모델을 수정하거나 호출하지 마십시오. 대신 먼저 모델을 복사한 다음 해당 복사본을 수정하거나 호출해야 합니다.

모든 워크플로우와 마찬가지로 API를 통해 호출할 수도 있습니다. 자세한 내용은 [프로그래밍 방식으로 워크플로우와 상호 작용](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

또는 을 사용하는 워크플로우 모델을 만들어 이를 수행할 수도 있습니다 `Publish Content Tree` 프로세스 단계:

1. AEM as a Cloud Service 홈페이지에서 **도구 - 워크플로우 - 모델**
1. 워크플로우 모델 페이지에서 **만들기** 화면 오른쪽 상단 모서리에서
1. 모델에 제목과 이름을 추가합니다. 자세한 내용은 [워크플로우 모델 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)
1. 목록에서 새로 생성된 모델을 선택하고 키를 누릅니다 **편집**
1. 다음 창에서 프로세스 단계 를 현재 모델 플로우로 끌어서 놓습니다.

   ![프로세스 단계](/help/operations/assets/processstep.png)

1. 플로우에서 프로세스 단계를 클릭하고 을 선택합니다 **구성** 렌치 아이콘을 눌러
1. 을(를) 클릭합니다. **프로세스** 탭을 선택하고 `Publish Content Tree` 드롭다운 목록에서

   ![Treeactivation](/help/operations/assets/newstep.png)

1. 에서 추가 매개 변수를 설정합니다. **인수** 필드. 여러 개의 쉼표로 구분된 인수를 함께 실행할 수 있습니다. 예:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >매개 변수 목록에 대해서는 **매개 변수** 섹션을 참조하십시오.

1. 누르기 **완료** 워크플로우 모델을 저장합니다.

**매개변수**

* `includeChildren` (부울 값, 기본값: `false`). false는 경로만 게시됨을 의미합니다. true는 아이들도 게시된다는 의미입니다.
* `replicateAsParticipant` (부울 값, 기본값: `false`). 로 구성된 경우 `true`로 지정하는 경우, 복제에서 `userid` 참가자 단계를 수행한 주도자.
* `enableVersion` (부울 값, 기본값: `true`). 이 매개 변수는 복제 시 새 버전을 만들지 여부를 결정합니다.
* `agentId` (문자열 값, 기본값은 게시용 에이전트만 사용됨을 의미합니다.) agentId에 대해 명시하는 것이 좋습니다. 예를 들어 값을 설정합니다. 게시합니다. 에이전트를 로 설정 `preview` 미리 보기 서비스에 게시됩니다.
* `filters` (문자열 값, 기본값은 모든 경로가 활성화됨을 의미합니다.) 사용 가능한 값은 다음과 같습니다.
   * `onlyActivated` - 활성화됨으로 표시되지 않은 경로만 활성화됩니다.
   * `onlyModified` - 활성화 날짜보다 늦게 수정 날짜가 있고 이미 활성화된 경로만 활성화합니다.
   * 위의 파이프 &quot;|&quot;을 사용하여 ORed를 만들 수 있습니다. 예, `onlyActivated|onlyModified`.

**로깅**

트리 활성화 워크플로우 단계가 시작되면 INFO 로그 수준에 구성 매개 변수를 기록합니다. 경로가 활성화되면 INFO 문도 기록됩니다.

그러면 워크플로우 단계가 모든 경로를 복제한 후 최종 INFO 문이 기록됩니다.

또한 아래의 로거의 로그 수준을 높일 수 있습니다 `com.day.cq.wcm.workflow.process.impl` 를 추가하여 더 많은 로그 정보를 얻을 수 있습니다.

오류가 발생하면 워크플로우 단계가 `WorkflowException`: 기본 예외를 래핑합니다.

아래에서는 샘플 게시 컨텐츠 트리 워크플로우 중에 생성된 로그 예제를 찾을 수 있습니다.

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**지원 다시 시작**

워크플로우는 컨텐츠를 청크 단위로 처리하며, 각 청크는 게시할 전체 컨텐츠의 하위 집합을 나타냅니다. 어떤 이유로든 워크플로우가 시스템에 의해 중지되면 다시 시작되고 아직 처리되지 않은 청크가 처리됩니다. 로그 문은 특정 경로에서 컨텐츠가 다시 시작되었다고 나타냅니다.

### 복제 API {#replication-api}

AEM as a Cloud Service에 포함된 복제 API를 사용하여 컨텐츠를 게시할 수 있습니다.

자세한 내용은 [API 설명서](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

**API의 기본 사용**

```
@Reference
Replicator replicator;
@Reference
ReplicationStatusProvider replicationStatusProvider;

....
Session session = ...
// Activate a single page to all agents, which are active by default
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en");
// Activate multiple pages (but try to limit it to approx 100 at max)
replicator.replicate(session,ReplicationActionType.ACTIVATE, new String[]{"/content/we-retail/en","/content/we-retail/de"});

// ways to get the replication status
Resource enResource = resourceResolver.getResource("/content/we-retail/en");
Resource deResource = resourceResolver.getResource("/content/we-retail/de");
ReplicationStatus enStatus = enResource.adaptTo(ReplicationStatus.class);
// if you need to get the status for more more than 1 resource at once, this approach is more performant
Map<String,ReplicationStatus> allStatus = replicationStatusProvider.getBatchReplicationStatus(enResource,deResource);
```

**특정 에이전트를 사용한 복제**

위의 예와 같이 리소스를 복제할 때 기본적으로 활성 상태인 에이전트만 사용됩니다. AEM as a Cloud Service에서 이 작업은 작성자를 게시 계층에 연결하는 &quot;게시&quot;라는 에이전트만 됩니다.

미리 보기 기능을 지원하기 위해 기본적으로 활성화되지 않은 &quot;미리 보기&quot;라는 새 에이전트가 추가되었습니다. 이 에이전트는 작성자를 미리 보기 계층에 연결하는 데 사용됩니다. 미리 보기 에이전트를 통해서만 복제하려면 을 통해 이 미리 보기 에이전트를 명시적으로 선택해야 합니다 `AgentFilter`.

이 작업을 수행하는 방법에 대해서는 아래 예를 참조하십시오.

```
private static final String PREVIEW_AGENT = "preview";

ReplicationStatus beforeStatus = enResource.adaptTo(ReplicationStatus.class); // beforeStatus.isActivated == false

ReplicationOptions options = new ReplicationOptions();
options.setFilter(new AgentFilter() {
  @Override
  public boolean isIncluded (Agent agent) {
    return agent.getId().equals(PREVIEW_AGENT);
  }
});
// will replicate only to preview
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en", options);

ReplicationStatus afterStatus = enResource.adaptTo(ReplicationStatus.class); // afterStatus.isActivated == false
ReplicationStatus previewStatus = afterStatus.getStatusForAgent(PREVIEW_AGENT); // previewStatus.isActivated == true
```

이러한 필터를 제공하지 않고 &quot;게시&quot; 에이전트만 사용하는 경우 &quot;미리 보기&quot; 에이전트가 사용되지 않고 복제 작업이 미리 보기 계층에 영향을 주지 않습니다.

전체 `ReplicationStatus` 기본적으로 활성 상태인 에이전트가 복제 작업에 하나 이상 포함된 경우에만 리소스의 가 수정됩니다. 위의 예에서 이는 복제가 &quot;미리 보기&quot; 에이전트를 사용하고 있기 때문에 해당되지 않습니다. 따라서 새 `getStatusForAgent()` 특정 에이전트에 대한 상태를 쿼리할 수 있는 메소드. 이 메서드는 &quot;게시&quot; 에이전트에서도 작동합니다. 제공된 에이전트를 사용하여 복제 작업이 수행된 경우 null이 아닌 값을 반환합니다.

### 콘텐츠를 무효화하는 방법 {#invalidating-content}

작성자의 Sling 컨텐츠 무효화(SCD)(기본 메서드)를 사용하거나 복제 API를 사용하여 게시 디스패처 초기화 복제 에이전트를 호출하여 컨텐츠를 직접 무효화할 수 있습니다. 자세한 내용은 [캐싱](/help/implementing/dispatcher/caching.md) 페이지를 참조하십시오.

**복제 API 용량 제한**

한 번에 100개 이하의 경로를 복제하여 500개를 하드 한도로 복제하는 것이 좋습니다. 하드 한도 위, `ReplicationException` 이 Throw됩니다.
응용 프로그램 로직에 원자성 복제가 필요하지 않으면 `ReplicationOptions.setUseAtomicCalls` false로 설정하면 경로 수가 허용되지만, 내부적으로 버킷을 만들어 이 제한 수준을 유지할 수 있습니다.

복제 호출당 전송되는 컨텐츠 크기는 초과해서는 안 됩니다 `10 MB`. 여기에는 노드 및 속성이 포함되지만 바이너리는 포함되지 않습니다(워크플로우 패키지 및 컨텐츠 패키지는 바이너리로 간주됨).


## 문제 해결 {#troubleshooting}

복제 문제를 해결하려면 AEM 작성자 서비스 웹 UI의 복제 큐로 이동합니다.

1. AEM 시작 메뉴에서 **도구 > 배포 > 배포**
2. 카드를 선택합니다 **게시**
   ![상태](assets/publish-status.png "상태")
3. 녹색이어야 하는 큐 상태를 확인합니다
4. 복제 서비스에 대한 연결을 테스트할 수 있습니다
5. 을(를) 선택합니다 **로그** 컨텐츠 게시 내역을 보여주는 탭

![로그](assets/publish-logs.png "로그")

컨텐츠를 게시할 수 없는 경우에는 전체 게시가 AEM 게시 서비스에서 복귀됩니다.
이 경우 편집 가능한 기본 대기열은 빨간색 상태를 표시하며 어떤 항목이 게시를 취소했는지 확인하기 위해 검토해야 합니다. 해당 대기열을 클릭하면 보류 중인 항목이 표시되며, 필요한 경우 단일 항목 또는 모든 항목을 지울 수 있습니다.
