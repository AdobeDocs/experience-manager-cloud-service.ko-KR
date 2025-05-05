---
title: 복제
description: AEM as a Cloud Service의 배포 및 복제 문제 해결에 대해 알아봅니다.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
feature: Operations
role: Admin
source-git-commit: 9dac0b63fec56bede7db9331d47ef479b29e67d0
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 31%

---

# 복제 {#replication}

Adobe Experience Manager as a Cloud Service은 [Sling 콘텐츠 배포](https://sling.apache.org/documentation/bundles/content-distribution.html) 기능을 사용하여 콘텐츠를 이동하여 AEM 런타임 외부에 있는 Adobe Developer에서 실행되는 파이프라인 서비스를 복제합니다.

>[!NOTE]
>
>자세한 내용은 [배포](/help/overview/architecture.md#content-distribution)를 읽어 보십시오.

## 콘텐츠 게시 방법 {#methods-of-publishing-content}

>[!NOTE]
>
>콘텐츠 벌크 게시에 관심이 있는 경우 [트리 활성화 워크플로 단계](#tree-activation)를 사용하여 워크플로를 만드십시오. 그러면 대규모 페이로드를 효율적으로 처리할 수 있습니다.
>벌크 게시 사용자 지정 코드를 빌드하는 것은 권장되지 않습니다.
>어떤 이유로든 사용자 정의해야 하는 경우, 기존 워크플로 API를 사용하여 이 단계로 워크플로를 트리거할 수 있습니다.
>게시해야 하는 콘텐츠만 게시하는 것이 좋습니다. 그리고 필요하지 않은 경우 많은 수의 콘텐츠를 게시하지 않도록 주의하십시오. 그러나 트리 활성화 워크플로 단계가 있는 워크플로를 통해 보낼 수 있는 콘텐츠 양에 대해서는 제한이 없습니다.

### 빠른 게시 취소/게시 - 예정된 게시 취소/게시 {#publish-unpublish}

이 기능을 사용하면 게시 관리 접근 방식을 통해 가능한 추가 옵션 없이 선택한 페이지를 즉시 게시할 수 있습니다.

자세한 내용은 [게시 관리](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication)를 참조하십시오.

### 설정 및 해제 시간 - 트리거 구성 {#on-and-off-times-trigger-configuration}

**설정 시간** 및 **해제 시간**&#x200B;의 추가적인 활용 방법은 [페이지 속성의 기본 탭](/help/sites-cloud/authoring/sites-console/page-properties.md#basic)에서 확인할 수 있습니다.

이 기능에 대한 자동 복제를 구현하려면 [OSGi 구성에서 **자동 복제**&#x200B;를 사용하도록 설정](/help/implementing/deploying/configuring-osgi.md) **해제 트리거 구성**&#x200B;합니다.

![OSGi 설정/해제 트리거 구성](/help/operations/assets/replication-on-off-trigger.png)

### 게시 관리 {#manage-publication}

게시 관리는 빠른 게시보다 더 많은 옵션을 제공하여 하위 페이지 포함, 참조 맞춤화, 적용 가능한 워크플로 시작 및 나중에 게시할 수 있는 옵션 등을 가능하게 합니다.

나중에 게시 옵션에 대해 폴더의 하위 항목을 포함하면 이 문서에 설명된 콘텐츠 트리 게시 워크플로가 호출됩니다.

게시 관리에 대한 자세한 내용은 [게시 기본 사항 설명서](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication)를 참조하십시오.

### 트리 활성화 워크플로 단계 {#tree-activation}

트리 활성화 워크플로 단계는 깊은 계층의 콘텐츠 노드를 복제하기 위한 것입니다. 큐가 너무 커지면 자동으로 일시 중지되므로 다른 복제가 지연 시간을 최소화하면서 동시에 진행될 수 있습니다.

`TreeActivation` 프로세스 단계를 사용하는 워크플로 모델 만들기:

1. AEM as a Cloud Service 홈페이지에서 **도구 - 워크플로 - 모델**(으)로 이동합니다.
1. 워크플로 모델 페이지에서 화면 오른쪽 상단의 **만들기**&#x200B;를 누릅니다.
1. 모델에 제목과 이름을 추가합니다. 자세한 내용은 [워크플로 모델 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=ko)를 참조하십시오.
1. 목록에서 만든 모델을 선택하고 **편집**&#x200B;을 누릅니다.
1. 다음 창에서 기본적으로 나타나는 단계를 삭제합니다
1. 프로세스 단계를 현재 모델 플로우로 끌어서 놓습니다.

   ![프로세스 단계](/help/operations/assets/processstep.png)

1. 흐름에서 프로세스 단계를 선택하고 렌치 아이콘을 눌러 **구성**&#x200B;을(를) 선택합니다.
1. **프로세스** 탭을 선택하고 드롭다운 목록에서 `Publish Content Tree`을(를) 선택한 다음 **핸들러 고급** 확인란을 선택합니다

   ![트리 활성화](/help/operations/assets/new-treeactivationstep.png)

1. **인수** 필드에서 추가 매개변수를 설정합니다. 여러 개의 쉼표로 구분된 인수를 함께 연결할 수 있습니다. 예:

   `enableVersion=false,agentId=publish,chunkSize=50,maxTreeSize=500000,dryRun=false,filters=onlyModified,maxQueueSize=10`

   >[!NOTE]
   >
   >매개변수 목록은 아래의 **매개변수** 섹션을 참조하십시오.

1. **완료**&#x200B;를 눌러 워크플로 모델을 저장합니다.

**매개변수**

| 이름 | 기본 | 설명 |
| -------------- | ------- | --------------------------------------------------------------- |
| 경로 |         | 시작할 루트 경로 |
| agentId | 게시 | 사용할 복제 에이전트 이름 |
| 청크 크기 | 50 | 단일 복제에 번들로 묶을 경로 수 |
| maxTreeSize | 500000 | 트리로 작은 것으로 간주할 최대 노드 수 |
| maxQueueSize | 10 | 복제 큐의 최대 항목 수 |
| enableVersion | false | 버전 관리 활성화 |
| dryRun | false | true로 설정된 경우 복제는 실제로 호출되지 않습니다. |
| userId |         | 작업 전용입니다. 워크플로우에서는 해당 워크플로우를 호출하는 사용자가 사용됩니다 |
| 개의 필터 |         | 노드 필터 이름 목록입니다. 아래의 지원되는 필터 를 참조하십시오 |

**지원 필터**

| 이름 | 설명 |
| ------------- | ------------------------------------------- |
| only수정됨 | 노드: 마지막 게시 이후 수정된 신규 및 기존 노드 모두 |
| onlyActivated | 노드: 마지막 게시 전에 게시된 노드 |


**지원 다시 시작**

워크플로는 콘텐츠를 청크 단위로 처리하며, 각 청크는 게시할 전체 콘텐츠의 하위 집합을 나타냅니다.  시스템이 워크플로우를 중지하면 중단된 부분부터 계속 진행됩니다.

**워크플로 진행 상황 모니터링**

1. AEM as a Cloud Service 홈페이지에서 **도구 - 일반 - 작업**(으)로 이동합니다.
1. 워크플로우에 해당하는 행을 확인합니다. *progress* 열은 복제가 진행되는 방식을 나타냅니다. 예를 들어 41/564를 표시하고 새로 고침하면 52/564로 업데이트할 수 있습니다.

   ![트리 활성화 진행률](/help/operations/assets/treeactivation-progress.png)


1. 행을 선택하고 열면 워크플로우 실행 상태에 대한 추가 세부 정보가 제공됩니다.

   ![트리 활성화 상태 세부 정보](/help/operations/assets/treeactivation-progress-details.png)



### 콘텐츠 트리 게시 워크플로 {#publish-content-tree-workflow}

>[!NOTE]
>
>이 기능은 사용자 지정 워크플로에 포함할 수 있는 더 많은 성능 트리 활성화 단계를 위해 더 이상 사용되지 않습니다.

<details>
<summary>더 이상 사용되지 않는 기능에 대한 자세한 내용을 보려면 여기를 클릭하십시오 .</summary>

**도구 - 워크플로 - 모델**&#x200B;을 선택한 다음 아래와 같이 기본 워크플로 모델의 **콘텐츠 트리 게시**&#x200B;를 복사하여 트리 복제를 트리거할 수 있습니다.

![콘텐츠 트리 게시 워크플로 카드](/help/operations/assets/publishcontenttreeworkflow.png)

원래 모델을 호출하지 마십시오. 대신 먼저 모델을 복사하고 해당 복사본을 호출해야 합니다.

모든 워크플로와 마찬가지로 API를 통해 호출할 수도 있습니다. 자세한 내용은 [프로그래밍 방식으로 워크플로와 상호 작용](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=ko#extending-aem)을 참조하십시오.

또는 `Publish Content Tree` 프로세스 단계를 사용하는 워크플로 모델을 만들 수 있습니다.

1. AEM as a Cloud Service 홈페이지에서 **도구 - 워크플로 - 모델**(으)로 이동합니다.
1. 워크플로 모델 페이지에서 화면 오른쪽 상단의 **만들기**&#x200B;를 누릅니다.
1. 모델에 제목과 이름을 추가합니다. 자세한 내용은 [워크플로 모델 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=ko)를 참조하십시오.
1. 목록에서 만든 모델을 선택하고 **편집**&#x200B;을 누릅니다.
1. 다음 창에서 프로세스 단계를 현재 모델 플로우로 드래그하여 놓습니다.

   ![프로세스 단계](/help/operations/assets/processstep.png)

1. 흐름에서 프로세스 단계를 선택하고 렌치 아이콘을 눌러 **구성**&#x200B;을(를) 선택합니다.
1. **프로세스** 탭을 선택하고 드롭다운 목록에서 `Publish Content Tree`을(를) 선택한 다음 **핸들러 고급** 확인란을 선택합니다

   ![트리 활성화](/help/operations/assets/newstep.png)

1. **인수** 필드에서 추가 매개변수를 설정합니다. 여러 개의 쉼표로 구분된 인수를 함께 연결할 수 있습니다. 예:

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >매개변수 목록은 아래의 **매개변수** 섹션을 참조하십시오.

1. **완료**&#x200B;를 눌러 워크플로 모델을 저장합니다.

**매개변수**

* `includeChildren`(부울 값, 기본값: `false`) 값 `false`은(는) 경로만 게시됨을 의미하고 `true`은(는) 하위 항목도 게시됨을 의미합니다.
* `replicateAsParticipant`(부울 값, 기본값: `false`) `true`로 구성된 경우 복제는 참가자 단계를 수행한 원칙의 `userid`를 사용합니다.
* `enableVersion`(부울 값, 기본값: `false`) 이 매개변수는 복제 시 새 버전을 만들지 여부를 결정합니다.
* `agentId`(문자열 값, 기본값은 게시용 에이전트만 사용됨을 의미합니다.) agentId를 명시하는 것이 좋습니다(예: 값을 “게시”로 설정). 에이전트를 `preview`(으)로 설정하면 미리보기 서비스에 게시됩니다.
* `filters`(문자열 값, 기본값은 모든 경로가 활성화되었음을 의미합니다.) 사용 가능한 값은 다음과 같습니다.
   * `onlyActivated` - (이미) 활성화된 페이지만 활성화합니다. 재활성화의 한 형태로 작동합니다.
   * `onlyModified` - 이미 활성화된 경로만 활성화하며 활성화 날짜 이후의 수정 날짜가 있습니다.
   * 위에서는 파이프 “|”을 사용하여 OR 구문을 만들 수 있습니다. (예: `onlyActivated|onlyModified`)

**로깅**

트리 활성화 워크플로 단계가 시작되면 INFO 로그 수준에 구성 매개 변수가 기록됩니다. 경로가 활성화되면 INFO 문도 기록됩니다.

워크플로 단계가 모든 경로를 복제한 후 최종 INFO 문이 기록됩니다.

또한 `com.day.cq.wcm.workflow.process.impl` 아래의 로거의 로그 수준을 DEBUG/TRACE으로 높여 더 많은 로그 정보를 가져올 수 있습니다.

오류가 있으면 워크플로 단계가 `WorkflowException`(으)로 종료되어 기본 예외가 래핑됩니다.

다음은 샘플 게시 콘텐츠 트리 워크플로 중에 생성된 로그의 예입니다.

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

</details>

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

미리보기 기능을 지원하기 위해 “미리보기”라는 새 에이전트가 추가되었으며, 이는 기본적으로 활성화되어 있지 않습니다. 이 에이전트는 작성자를 미리보기 계층에 연결하는 데 사용됩니다. 미리보기 에이전트를 통해서만 복제하려면 `AgentFilter`을(를) 통해 이 미리보기 에이전트를 명시적으로 선택해야 합니다.

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

복제 작업에 기본적으로 활성 상태인 에이전트가 하나 이상 포함된 경우 리소스의 전체 `ReplicationStatus`만 수정됩니다. 위의 예에서는 이 흐름이 적용되지 않았습니다. 복제에서 &quot;미리보기&quot; 에이전트를 사용하고 있었습니다. 따라서 특정 에이전트 상태의 쿼리를 허용하는 새 `getStatusForAgent()` 메서드를 사용해야 합니다. 이 메서드는 “게시” 에이전트에도 작동합니다. 제공된 에이전트를 사용하여 복제 작업을 수행한 경우 null이 아닌 값이 반환됩니다.

### 콘텐츠 무효화 방법 {#invalidating-content}

작성자의 Sling 콘텐츠 무효화(SCD)(기본 메서드)를 사용하거나 복제 API를 사용하여 게시 Dispatcher 플러시 복제 에이전트를 호출하여 콘텐츠를 직접 무효화할 수 있습니다. 자세한 내용은 [캐싱](/help/implementing/dispatcher/caching.md) 페이지를 참조하십시오.

**복제 API 용량 제한**

한 번에 100개 이하의 경로를 복제하고 500개를 제한합니다. 한도를 초과하면 `ReplicationException`이(가) throw됩니다.
응용 프로그램 논리에 작은 단위의 복제가 필요하지 않은 경우 `ReplicationOptions.setUseAtomicCalls`을(를) false로 설정하여 이 제한을 극복할 수 있습니다. 이렇게 하면 원하는 수의 경로가 허용되며, 내부적으로 버킷이 생성되어 경로 수가 이 제한보다 낮게 유지됩니다.

복제 호출당 전송되는 콘텐츠 크기는 `10 MB`를 초과해서는 안 됩니다. 이 규칙에는 노드 및 속성이 포함되지만 바이너리는 포함되지 않습니다(워크플로 패키지 및 콘텐츠 패키지는 바이너리로 간주됨).


## 문제 해결 {#troubleshooting}

복제 문제를 해결하려면 AEM 작성자 서비스 웹 UI의 복제 대기열로 이동합니다.

1. AEM 시작 메뉴에서 **도구** > **배포** > **배포**&#x200B;로 이동합니다.
1. **게시** 카드를 선택합니다.

   ![상태](assets/publish-status.png "상태")

1. 녹색으로 표시되어야 하는 대기열 상태를 확인합니다
1. 복제 서비스에 대한 연결을 테스트할 수 있습니다
1. 콘텐츠 게시 내역을 표시하는 **로그** 탭을 선택합니다.

![로그](assets/publish-logs.png "로그")

콘텐츠를 게시할 수 없는 경우에는 전체 게시가 AEM 게시 서비스에서 되돌려집니다.

이 경우 편집 가능한 기본 대기열에 빨간색 상태가 표시되며 이를 검토하여 어떤 항목이 게시를 취소했는지 확인해야 합니다. 해당 대기열을 클릭하면 보류 중인 항목이 표시되며 필요한 경우 단일 항목 또는 모든 항목을 지울 수 있습니다.
