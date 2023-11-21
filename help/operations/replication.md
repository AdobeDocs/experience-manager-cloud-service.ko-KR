---
title: 복제
description: AEM as a Cloud Service으로 배포 및 복제 문제 해결에 대해 알아봅니다.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 41%

---

# 복제 {#replication}

Adobe Experience Manager as a Cloud Service은 [Sling 콘텐츠 배포](https://sling.apache.org/documentation/bundles/content-distribution.html) AEM 런타임 외부에 있는 Adobe Developer에서 실행되는 파이프라인 서비스로 복제하도록 콘텐츠를 이동하는 기능입니다.

>[!NOTE]
>
>자세한 내용은 [배포](/help/overview/architecture.md#content-distribution)를 읽어 보십시오.

## 콘텐츠 게시 방법 {#methods-of-publishing-content}

>[!NOTE]
>
>벌크 게시 콘텐츠에 관심이 있는 경우 [콘텐츠 트리 워크플로 게시](#publish-content-tree-workflow).
>이 워크플로 단계는 Cloud Service을 위해 특별히 빌드되었으며 대용량 페이로드를 효율적으로 처리할 수 있습니다.
>벌크 게시 사용자 지정 코드를 빌드하는 것은 권장되지 않습니다.
>어떤 이유로든 사용자 정의해야 하는 경우, 기존 워크플로 API를 사용하여 이 워크플로/워크플로 단계를 트리거할 수 있습니다.
>게시해야 하는 콘텐츠만 게시하는 것이 좋습니다. 또한 필요하지 않은 경우 많은 수의 콘텐츠를 게시하지 않도록 주의하십시오. 그러나 콘텐츠 트리 게시 작업 과정을 통해 보낼 수 있는 콘텐츠 양에 대해서는 제한이 없습니다.

### 빠른 게시 취소/게시 - 예정된 게시 취소/게시 {#publish-unpublish}

이 기능을 사용하면 게시 관리 접근 방식을 통해 가능한 추가 옵션 없이 선택한 페이지를 즉시 게시할 수 있습니다.

자세한 내용은 [게시 관리](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication)를 참조하십시오.

### 설정 및 해제 시간 - 트리거 구성 {#on-and-off-times-trigger-configuration}

**설정 시간** 및 **해제 시간**&#x200B;의 추가적인 활용 방법은 [페이지 속성의 기본 탭](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)에서 확인할 수 있습니다.

이 기능에 대한 자동 복제를 구현하려면 **자동 복제** 다음에서 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md) **설정/해제 트리거 구성**:

![OSGi 설정/해제 트리거 구성](/help/operations/assets/replication-on-off-trigger.png)

### 게시 관리 {#manage-publication}

게시 관리는 빠른 게시보다 더 많은 옵션을 제공하여 하위 페이지 포함, 참조 맞춤화, 적용 가능한 워크플로 시작 및 나중에 게시할 수 있는 옵션 등을 가능하게 합니다.

나중에 게시 옵션에 대해 폴더의 하위 항목을 포함하면 이 문서에 설명된 콘텐츠 트리 게시 워크플로가 호출됩니다.

게시 관리에 대한 자세한 내용은 [게시 기본 사항 설명서](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication)를 참조하십시오.

### 콘텐츠 트리 게시 워크플로 {#publish-content-tree-workflow}

**도구 - 워크플로 - 모델**&#x200B;을 선택한 다음 아래와 같이 기본 워크플로 모델의 **콘텐츠 트리 게시**&#x200B;를 복사하여 트리 복제를 트리거할 수 있습니다.

![콘텐츠 트리 게시 워크플로 카드](/help/operations/assets/publishcontenttreeworkflow.png)

원래 모델을 호출하지 마십시오. 대신 먼저 모델을 복사하고 해당 복사본을 호출해야 합니다.

모든 워크플로와 마찬가지로 API를 통해 호출할 수도 있습니다. 자세한 내용은 [프로그래밍 방식으로 워크플로우와 상호 작용](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=ko-kr#extending-aem).

또는 다음을 사용하는 워크플로 모델을 만들 수 있습니다. `Publish Content Tree` 프로세스 단계:

1. AEM as a Cloud Service 홈페이지에서 **도구 - 워크플로 - 모델**.
1. 워크플로우 모델 페이지에서 를 누릅니다. **만들기** 화면의 오른쪽 상단에 있습니다.
1. 모델에 제목과 이름을 추가합니다. 자세한 내용은 [워크플로 모델 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)를 참조하십시오..
1. 목록에서 생성된 모델을 선택하고 키를 누릅니다 **편집**
1. 다음 창에서 프로세스 단계를 현재 모델 플로우로 드래그하여 놓습니다.

   ![프로세스 단계](/help/operations/assets/processstep.png)

1. 플로우에서 프로세스 단계를 선택하고 **구성** 렌치 아이콘을 눌러.
1. 다음 항목 선택 **프로세스** 탭하고 선택 `Publish Content Tree` 드롭다운 목록에서 을(를) 선택한 다음 **핸들러 진행** 확인란

   ![트리 활성화](/help/operations/assets/newstep.png)

1. **인수** 필드에서 추가 매개변수를 설정합니다. 여러 개의 쉼표로 구분된 인수를 함께 연결할 수 있습니다. 예:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >매개변수 목록은 아래의 **매개변수** 섹션을 참조하십시오.

1. **완료**&#x200B;를 눌러 워크플로 모델을 저장합니다.

**매개변수**

* `includeChildren`(부울 값, 기본값: `false`) 값 `false` 은 경로만 게시됨을 의미합니다. `true` 하위 항목도 게시됨을 의미합니다.
* `replicateAsParticipant`(부울 값, 기본값: `false`) `true`로 구성된 경우 복제는 참가자 단계를 수행한 원칙의 `userid`를 사용합니다.
* `enableVersion`(부울 값, 기본값: `true`) 이 매개변수는 복제 시 새 버전을 만들지 여부를 결정합니다.
* `agentId`(문자열 값, 기본값은 게시용 에이전트만 사용됨을 의미합니다.) agentId를 명시하는 것이 좋습니다(예: 값을 “게시”로 설정). 에이전트 설정 `preview` 은 미리보기 서비스에 게시합니다.
* `filters` (문자열 값, 기본값은 모든 경로가 활성화됨을 의미합니다.) 사용 가능한 값은 다음과 같습니다.
   * `onlyActivated` - (이미) 활성화된 페이지만 활성화합니다. 재활성화의 한 형태로 작동합니다.
   * `onlyModified` - 이미 활성화된 경로만 활성화하며 활성화 날짜 이후의 수정 날짜가 있습니다.
   * 위에서는 파이프 “|”을 사용하여 OR 구문을 만들 수 있습니다. (예: `onlyActivated|onlyModified`)

**로깅**

트리 활성화 워크플로 단계가 시작되면 INFO 로그 수준에 구성 매개 변수가 기록됩니다. 경로가 활성화되면 INFO 문도 기록됩니다.

워크플로 단계가 모든 경로를 복제한 후 최종 INFO 문이 기록됩니다.

또한 아래 로거의 로그 수준을 높일 수 있습니다 `com.day.cq.wcm.workflow.process.impl` 를 디버거/TRACE에 추가하여 더 많은 로그 정보를 얻습니다.

오류가 있는 경우 워크플로 단계는으로 종료됩니다. `WorkflowException`: 기본 예외를 래핑합니다.

다음은 샘플 게시 콘텐츠 트리 워크플로 중에 생성된 로그의 예입니다.

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**지원 다시 시작**

워크플로는 콘텐츠를 청크 단위로 처리하며, 각 청크는 게시할 전체 콘텐츠의 하위 집합을 나타냅니다. 시스템에서 워크플로우를 중지하면 아직 처리되지 않은 청크가 다시 시작되고 처리됩니다. 로그 문에는 특정 경로에서 콘텐츠가 다시 시작되었다고 표시됩니다.

### 복제 API {#replication-api}

AEM as a Cloud Service에 포함된 복제 API를 사용하여 콘텐츠를 게시할 수 있습니다.

자세한 내용은 [API 설명서](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html)를 참조하십시오.

**API 기본 사용**

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

리소스를 복제할 때는 위의 예처럼 기본적으로 활성 상태인 에이전트만 사용됩니다. AEM as a Cloud Service에서는 작성자를 게시 계층에 연결하는 &quot;게시&quot;라는 에이전트만 의미합니다.

미리보기 기능을 지원하기 위해 “미리보기”라는 새 에이전트가 추가되었으며, 이는 기본적으로 활성화되어 있지 않습니다. 이 에이전트는 작성자를 미리보기 계층에 연결하는 데 사용됩니다. 미리보기 에이전트를 통해서만 복제하려면 다음을 통해 이 미리보기 에이전트를 명시적으로 선택해야 합니다. `AgentFilter`.

다음 예를 참조하십시오.

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

이러한 필터를 제공하지 않고 “게시” 에이전트만 사용하는 경우, “미리보기” 에이전트가 사용되지 않으며 복제 작업이 미리보기 계층에 영향을 주지 않습니다.

복제 작업에 기본적으로 활성 상태인 에이전트가 하나 이상 포함된 경우 리소스의 전체 `ReplicationStatus`만 수정됩니다. 위의 예에서는 이 흐름이 적용되지 않았습니다. 복제에서 &quot;미리보기&quot; 에이전트를 사용하고 있었습니다. 따라서 새 를 사용해야 합니다 `getStatusForAgent()` 특정 에이전트 상태의 쿼리를 허용하는 메서드입니다. 이 메서드는 “게시” 에이전트에도 작동합니다. 제공된 에이전트를 사용하여 복제 작업을 수행한 경우 null이 아닌 값이 반환됩니다.

### 콘텐츠 무효화 방법 {#invalidating-content}

작성자의 Sling 콘텐츠 무효화(SCD)(기본 메서드)를 사용하거나 복제 API를 사용하여 게시 Dispatcher 플러시 복제 에이전트를 호출하여 콘텐츠를 직접 무효화할 수 있습니다. 다음을 참조하십시오 [캐싱](/help/implementing/dispatcher/caching.md) 자세한 내용은 페이지를 참조하십시오.

**복제 API 용량 제한**

한 번에 100개 이하의 경로를 복제하고 500개를 제한합니다. 제한 초과, a `ReplicationException` 이 throw됩니다.
애플리케이션 논리에 작은 단위의 복제가 필요하지 않은 경우 를 설정하여 이 제한을 극복할 수 있습니다. `ReplicationOptions.setUseAtomicCalls` 를 false로 설정하고, 원하는 수의 경로를 허용하지만 내부적으로 버킷을 생성하여 이 제한보다 낮게 유지합니다.

복제 호출당 전송되는 콘텐츠 크기는 `10 MB`를 초과해서는 안 됩니다. 이 규칙에는 노드 및 속성이 포함되지만 바이너리는 포함되지 않습니다(워크플로 패키지 및 콘텐츠 패키지는 바이너리로 간주됨).


## 문제 해결 {#troubleshooting}

복제 문제를 해결하려면 AEM 작성자 서비스 웹 UI의 복제 대기열로 이동합니다.

1. AEM 시작 메뉴에서 다음으로 이동합니다. **도구 > 배포 > 배포**
2. **게시** 카드를 선택합니다.
   ![상태](assets/publish-status.png "상태")
3. 녹색으로 표시되어야 하는 대기열 상태를 확인합니다
4. 복제 서비스에 대한 연결을 테스트할 수 있습니다
5. 콘텐츠 게시 내역을 표시하는 **로그** 탭을 선택합니다.

![로그](assets/publish-logs.png "로그")

콘텐츠를 게시할 수 없는 경우에는 전체 게시가 AEM 게시 서비스에서 되돌려집니다.
이 경우 편집 가능한 기본 대기열에 빨간색 상태가 표시되며 이를 검토하여 어떤 항목이 게시를 취소했는지 확인해야 합니다. 해당 대기열을 클릭하면 보류 중인 항목이 표시되며 필요한 경우 단일 항목 또는 모든 항목을 지울 수 있습니다.
