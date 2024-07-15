---
title: AEM as a Cloud Service에서의 유지 관리 작업
description: AEM as a Cloud Service의 유지 관리 작업과 이를 구성하는 방법에 대해 알아봅니다.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
feature: Operations
role: Admin
source-git-commit: f8ef7e36ad602af96c3a6055db31ac328da808e6
workflow-type: tm+mt
source-wordcount: '2106'
ht-degree: 30%

---

# AEM as a Cloud Service에서의 유지 관리 작업 {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="유지 관리 작업"
>abstract="유지 관리 작업은 저장소 최적화를 위해 일정에 따라 실행되는 프로세스입니다. AEM as a Cloud Service를 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요성이 최소화됩니다. 고객은 인프라 운영을 Adobe에게 맡긴 채 애플리케이션 수준의 우려사항에 자원을 집중시킬 수 있습니다."

유지 관리 작업은 저장소 최적화를 위해 일정에 따라 실행되는 프로세스입니다. AEM as a Cloud Service를 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요성이 최소화됩니다. 고객은 인프라 운영을 Adobe에게 맡긴 채 애플리케이션 수준의 우려사항에 자원을 집중시킬 수 있습니다.

## 유지 관리 작업 구성 {#maintenance-tasks-configuring}

이전의 AEM 버전에서는 유지 관리 카드(도구 > 운영 > 유지 관리)를 사용해 유지 관리 작업을 구성할 수 있었습니다. AEM as a Cloud Service의 경우 유지 관리 카드가 더 이상 이용 가능하지 않기 때문에 Cloud Manager를 사용해 소스 제어에 구성을 커밋하고 배포해야 합니다. Adobe은 고객이 구성할 수 없는 설정(예: 데이터스토어 가비지 수집)이 있는 유지 관리 작업을 관리합니다. 기타 유지 관리 작업은 아래 표에 설명한 대로 고객이 구성할 수 있습니다.

>[!CAUTION]
>
>Adobe은 성능 저하와 같은 문제를 완화하기 위해 고객의 유지 관리 작업 구성 설정을 재정의할 권한을 보유합니다.

다음 표는 사용 가능한 유지 관리 작업을 보여 줍니다.

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>유지 관리 작업</th>
    <th>구성 소유자</th>
    <th>구성 방법 (선택 사항)</th>
  </tr>  
  <tr>
    <td>데이터스토어 가비지 수집</td>
    <td>Adobe</td>
    <td>N/A - Adobe 완전 소유</td>
  </td> 
  </tr>
  <tr>
    <td>버전 삭제</td>
    <td>고객</td>
    <td>버전 제거는 현재 기본적으로 사용하지 않도록 설정되어 있지만 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">버전 제거 및 감사 로그 제거 유지 관리 작업</a> 섹션에 설명된 대로 정책을 구성할 수 있습니다.<br/><br/>제거가 곧 기본적으로 사용되며 해당 값은 재정의할 수 있습니다.<br>
   </td>
  </td>
  </tr>
  <tr>
    <td>감사 로그 삭제</td>
    <td>고객</td>
    <td>감사 로그 제거는 현재 기본적으로 사용하지 않도록 설정되어 있지만 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">버전 제거 및 감사 로그 제거 유지 관리 작업</a> 섹션에 설명된 대로 정책을 구성할 수 있습니다.<br/><br/>제거가 곧 기본적으로 사용되며 해당 값은 재정의할 수 있습니다.<br>
   </td>
   </td>
  </tr>
  <tr>
    <td>Lucene 바이너리 정리</td>
    <td>Adobe</td>
    <td>사용되지 않으므로 Adobe가 비활성화합니다.</td>
  </td>
  </tr>
  <tr>
    <td>애드혹 작업 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> 또는 <code>granite_monthly</code> 폴더 아래에 속성을 만들어 <code>/libs</code>에서 기본 제공 유지 관리 창 구성 노드를 재정의합니다.</p>
    <p>추가적인 구성 세부 정보는 아래의 유지 관리 창 표를 참조하십시오. 위의 노드 아래에 다른 노드를 추가하여 유지 관리 작업을 활성화합니다. <code>sling:resourceType</code> 특성이 <code>granite/operations/components/maintenance/task</code>(으)로 설정되고 <code>granite.maintenance.name</code> 특성이 <code>TaskPurge</code>(으)로 설정된 <code>granite_TaskPurgeTask</code>(으)로 이름을 지정합니다. OSGI 속성을 구성하십시오. 속성 목록은 <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code>을(를) 참조하십시오.</p>
  </td>
  </tr>
    <tr>
    <td>워크플로 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> 또는 <code>granite_monthly</code> 폴더 아래에 속성을 만들어 <code>/libs</code>에서 기본 제공 유지 관리 창 구성 노드를 재정의합니다. 추가적인 구성 세부 정보는 아래의 유지 관리 창 표를 참조하십시오.</p>
    <p>적절한 속성을 사용해 위 노드 아래에서 또 다른 노드를 추가하여(<code>granite_WorkflowPurgeTask</code>로 이름 지정) 유지 관리 작업을 활성화합니다. OSGI 속성을 구성합니다. <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html#regular-purging-of-workflow-instances">AEM 6.5 유지 관리 작업 문서</a>를 참조하십시오.</p>
  </td>
  </tr>
  <tr>
    <td>프로젝트 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> 또는 <code>granite_monthly</code> 폴더 아래에 속성을 만들어 <code>/libs</code>에서 기본 제공 유지 관리 창 구성 노드를 재정의합니다. 추가적인 구성 세부 정보는 아래의 유지 관리 창 표를 참조하십시오.</p>
    <p>적절한 속성을 사용해 위 노드 아래에서 또 다른 노드를 추가하여(<code>granite_ProjectPurgeTask</code>로 이름 지정) 유지 관리 작업을 활성화합니다. "프로젝트 Adobe 제거 구성" 아래의 OSGI 속성 목록을 참조하십시오.</p>
  </td>
  </tr>
  </tbody>
</table>

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>유지 관리 창 구성</th>
    <th>구성 소유자</th>
    <th>구성 유형</th>
    <th>매개변수</th>
  </tr>
  <tr>
    <td>일별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
  <td>
  <p><strong>windowSchedule=daily</strong>(이 값은 변경해서는 안 됨)</p>
  <p>24시간 시계로 사용하는 <strong>windowStartTime=HH:MM</strong>입니다. 일별 유지 관리 창과 연계된 유지 관리 작업을 실행해야 하는 시점을 정의합니다.</p>
  <p>24시간 시계로 사용하는 <strong>windowEndTime=HH:MM</strong>입니다. 일별 유지 관리 창과 연계된 유지 관리 작업이 완료된 상태가 아닌 경우 실행을 정지해야 하는 시점을 정의합니다.</p>
  <p>이 일정 동안에는 유지 관리 작업을 두 번 이상 실행할 수 없습니다.</p>
  </td> 
  </tr>
  <tr>
    <td>주별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=weekly</strong>(이 값은 변경해서는 안 됨)</p>
    <p>24시간 시계로 사용하는 <strong>windowStartTime=HH:MM</strong>입니다. 주별 유지 관리 창과 연계된 유지 관리 작업을 실행해야 하는 시점을 정의합니다.</p>
    <p>24시간 시계로 사용하는 <strong>windowEndTime=HH:MM</strong>입니다. 주별 유지 관리 창과 연계된 유지 관리 작업이 완료된 상태가 아닌 경우 실행을 정지해야 하는 시점을 정의합니다.</p>
    <p>이 일정 동안에는 유지 관리 작업을 두 번 이상 실행할 수 없습니다.</p>
    <p><strong>windowScheduleWeekdays= Array of two values from 1-7 (예: [5,5])</strong> 배열의 첫 번째 값은 작업이 예약된 시작일이며 두 번째 값은 작업이 정지되어야 하는 종료일입니다. 정확한 시작 및 종료 시간은 각각 windowStartTime과 windowEndTime이 제어합니다.</p>
    </td>
  </tr>
  <tr>
    <td>월별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=monthly</strong>(이 값은 변경해서는 안 됨)</p>
    <p>24시간 시계로 사용하는 <strong>windowStartTime=HH:MM</strong>입니다. 월별 유지 관리 창과 연계된 유지 관리 작업을 실행해야 하는 시점을 정의합니다.</p>
    <p>24시간 시계로 사용하는 <strong>windowEndTime=HH:MM</strong>입니다. 월별 유지 관리 창과 연계된 유지 관리 작업이 완료된 상태가 아닌 경우 실행을 정지해야 하는 시점을 정의합니다.</p>
    <p>이 일정 동안에는 유지 관리 작업을 두 번 이상 실행할 수 없습니다.</p>
    <p><strong>windowScheduleWeekdays=Array of two values from 1-7 (example, [5,5])</strong> 배열의 첫 번째 값은 작업이 예약된 시작일이며 두 번째 값은 작업이 정지되어야 하는 종료일입니다. 정확한 시작 및 종료 시간은 각각 windowStartTime과 windowEndTime이 제어합니다.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0은 당월의 첫째 주에 예약하는 것이며 1은 당월 마지막 주에 예약하는 것을 뜻합니다. 값이 없으면 windowScheduleWeekdays(매월)가 제어하는 날에 작업이 효과적으로 예약됩니다.</p>
    </td>
    </tr>
    </tbody>
</table>

**위치**:

* 일별 - /apps/settings/granite/operations/maintenance/granite_daily
* 주별 - /apps/settings/granite/operations/maintenance/granite_weekly
* 월별 - /apps/settings/granite/operations/maintenance/granite_monthly

**코드 샘플**:

코드 샘플 1 (일별)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
  xmlns:jcr="http://www.jcp.org/jcr/1.0" 
  jcr:primaryType="sling:Folder"
  sling:configCollectionInherit="true"
  sling:configPropertyInherit="true"
  windowSchedule="daily"
  windowStartTime="03:00"
  windowEndTime="05:00"
 />
```

코드 샘플 2 (주별)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="weekly"
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

코드 샘플 3 (월별)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="monthly"
   windowFirstLastStartDay=0
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

## 버전 삭제 및 감사 로그 삭제 유지 관리 작업 {#purge-tasks}

버전 및 감사 로그를 지우면 저장소 크기가 줄어들고 일부 시나리오에서는 성능이 향상될 수 있습니다.

>[!NOTE]
>
>AEM Guides 고객은 버전 삭제를 구성하지 않아야 합니다.

### 기본값 {#defaults}

현재는 기본적으로 제거가 활성화되어 있지 않지만 향후 변경될 예정입니다. 기본 제거가 활성화되기 전에 생성된 환경은 제거가 예기치 않게 발생하지 않도록 보다 보수적인 임계값을 갖습니다. 기본 삭제 정책에 대한 자세한 내용은 아래의 버전 삭제 및 감사 로그 삭제 섹션을 참조하십시오.
<!-- Version purging and audit log purging are on by default, with different default values for environments with ids higher than **TBD** versus those with ids lower than that value. -->

<!-- ### Overriding the default values with a new configuration {#override} -->

아래 설명된 대로 구성 파일을 선언하고 배포하여 기본 제거 값을 재정의할 수 있습니다.

<!-- The reason for this behavior is to clarify the ambiguity over whether the default purge values would take effect once you remove the declaration. -->

### 구성 적용 {#configure-purge}

다음 단계에 설명된 대로 구성 파일을 선언하고 배포합니다.

>[!NOTE]
>구성 파일에 버전 제거 노드를 배포한 후에는 선언된 상태를 유지하고 제거하지 말아야 합니다. 그럴 경우 구성 파이프라인이 실패합니다.
> 
>마찬가지로, 구성 파일에 감사 로그 제거 노드를 배포한 후에는 선언된 상태를 유지하고 제거하지 않아야 합니다.

**1** - Git에서 프로젝트의 최상위 폴더에 다음 폴더 및 파일 구조를 만듭니다.

```
config/
     mt.yaml
```

**2** - 다음을 포함하는 구성 파일의 속성을 선언합니다.

* 값이 &quot;MaintenanceTasks&quot;인 &quot;kind&quot; 속성.
* &quot;version&quot; 속성(현재 버전 1)입니다.
* 속성이 `envTypes`인 선택적 &quot;metadata&quot; 개체로, 이 구성이 유효한 환경 유형(dev, stage, prod)의 쉼표로 구분된 목록입니다. 메타데이터 개체가 선언되지 않으면 모든 환경 유형에 대해 구성이 유효합니다.
* `versionPurge` 및 `auditLogPurge` 개체가 모두 있는 데이터 개체입니다.

아래 `versionPurge` 및 `auditLogPurge` 개체의 정의 및 구문을 참조하십시오.

다음 예제와 유사하게 구성을 구성해야 합니다.

```
kind: "MaintenanceTasks"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  versionPurge:
    maximumVersions: 15
    maximumAgeDays: 20
    paths: ["/content"]
    minimumVersions: 1
    retainLabelledVersions: false
  auditLogPurge:
    rules:
      - replication:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["Activate", "Deactivate", "Delete", "Test", "Reverse", "Internal Poll"]
      - pages:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["PageCreated", "PageModified", "PageMoved", "PageDeleted", "VersionCreated", "PageRestored", "PageValid", "PageInvalid"]
      - dam:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["ASSET_EXPIRING", "METADATA_UPDATED", "ASSET_EXPIRED", "ASSET_REMOVED", "RESTORED", "ASSET_MOVED", "ASSET_VIEWED", "PROJECT_VIEWED", "PUBLISHED_EXTERNAL", "COLLECTION_VIEWED", "VERSIONED", "ADDED_COMMENT", "RENDITION_UPDATED", "ACCEPTED", "DOWNLOADED", "SUBASSET_UPDATED", "SUBASSET_REMOVED", "ASSET_CREATED", "ASSET_SHARED", "RENDITION_REMOVED", "ASSET_PUBLISHED", "ORIGINAL_UPDATED", "RENDITION_DOWNLOADED", "REJECTED"]
```

구성이 유효하려면 다음 사항에 유의하십시오.

* 모든 속성을 정의해야 합니다. 상속된 기본값은 없습니다.
* 아래 속성 표의 유형(정수, 문자열, 부울 등)은 준수해야 합니다.

>[!NOTE]
>`yq`을(를) 사용하여 구성 파일의 YAML 형식을 로컬로 확인할 수 있습니다(예: `yq mt.yaml`).

**3** - 비프로덕션 및 프로덕션 구성 파이프라인을 구성합니다.

RDE(신속한 개발 환경)는 제거를 지원하지 않습니다. 프로덕션(샌드박스가 아닌) 프로그램의 다른 환경 유형의 경우 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 만듭니다.

자세한 내용은 [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)을 참조하십시오.

### 버전 삭제 {#version-purge}

>[!NOTE]
>
>AEM Guides 고객은 버전 삭제를 구성하지 않아야 합니다.

#### 버전 삭제 기본값 {#version-purge-defaults}

<!-- For version purging, environments with an id higher than **TBD** have the following default values: -->

현재는 기본적으로 제거가 활성화되어 있지 않지만 향후 변경될 예정입니다.

기본 제거가 활성화된 후에 생성된 환경에는 다음 기본값이 사용됩니다.

* 30일 이전 버전은 제거됩니다.
* 최근 30일 동안의 최신 5개 버전이 유지됩니다.
* 위의 규칙과 관계없이 최신 버전(현재 파일 포함)은 유지됩니다.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

기본 지우기가 활성화되기 전에 생성된 환경에는 아래 나열된 기본값이 있지만 성능을 최적화하기 위해 해당 값을 낮추는 것이 좋습니다.

* 7년 이전의 버전은 제거됩니다.
* 지난 7년 동안의 모든 버전이 유지됩니다.
* 7년 후에는 (현재 파일 외에) 최신 버전 이외의 버전이 제거됩니다.

#### 버전 삭제 속성 {#version-purge-properties}

허용되는 속성은 다음과 같습니다.

*default*&#x200B;을(를) 나타내는 열은 기본값이 적용될 때 미래의 기본값을 나타냅니다. *TBD*&#x200B;은(는) 아직 결정되지 않은 환경 ID를 반영합니다.

| 속성 | envs>TBD의 향후 기본값 | envs&lt;=TBD의 향후 기본값 | required | 유형 | 값 |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| 경로 | [&quot;/content&quot;] | [&quot;/content&quot;] | 예 | 문자열 배열 | 새 버전을 만들 때 버전을 제거할 경로를 지정합니다.  고객은 이 속성을 선언해야 하지만 허용되는 값은 &quot;/content&quot;뿐입니다. |
| maximumAgeDays | 30 | 2557 (7년 + 2윤일) | 예 | 정수 | 구성된 값보다 오래된 버전은 제거됩니다. 값이 0이면 버전 연령을 기준으로 퍼지가 수행되지 않습니다. |
| maximumVersion | 5 | 0(제한 없음) | 예 | 정수 | n번째 최신 버전보다 오래된 버전은 모두 제거됩니다. 값이 0이면 버전 수에 따라 제거가 수행되지 않습니다. |
| 최소 버전 | 1 | 1 | 예 | 정수 | 나이에 상관없이 유지되는 최소 버전 수. 최소 1개의 버전은 항상 유지되며 값은 1 이상이어야 합니다. |
| retainLabelledVersioned | false | false | 예 | 부울 | 명시적으로 레이블이 지정된 버전을 제거에서 제외할지 여부를 결정합니다. 더 나은 저장소 최적화를 위해 이 값을 false로 설정하는 것이 좋습니다. |


**속성 상호 작용**

다음 예제는 속성이 결합될 때 상호 작용하는 방법을 보여 줍니다.

예:

```
maximumAgeDays = 30
maximumVersions = 10
minimumVersions = 2
```

`maximumVersions` 속성이 10으로 설정되어 있으므로 23일에 11개의 버전이 있는 경우 다음 번에 제거 유지 관리 작업이 실행될 때 가장 오래된 버전이 삭제됩니다.

31일에 5개의 버전이 있는 경우 `minimumVersions` 속성이 2로 설정되어 있으므로 3개만 삭제됩니다.

예:

```
maximumAgeDays = 30
maximumVersions = 0
minimumVersions = 1
```

`maximumVersions` 속성이 0으로 설정되어 30일 이상 버전이 삭제되지 않습니다.

30일 넘는 이전 버전 하나가 유지됩니다.

### 감사 로그 삭제 {#audit-purge}

#### 감사 로그 삭제 기본값 {#audit-purge-defaults}

<!-- For audit log purging, environments with an id higher than **TBD** have the following default values: -->

현재는 기본적으로 제거가 활성화되어 있지 않지만 향후 변경될 예정입니다.

기본 제거가 활성화된 후에 생성된 환경에는 다음 기본값이 사용됩니다.

* 7일 넘는 복제, DAM 및 페이지 감사 로그는 제거됩니다.
* 가능한 모든 이벤트가 기록됩니다.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

기본 지우기가 활성화되기 전에 생성된 환경에는 아래 나열된 기본값이 있지만 성능을 최적화하기 위해 해당 값을 낮추는 것이 좋습니다.

* 7년 이상 된 복제, DAM 및 페이지 감사 로그는 제거됩니다.
* 가능한 모든 이벤트가 기록됩니다.

>[!NOTE]
>편집 불가능한 감사 로그를 생성하기 위한 규정 요구 사항이 있는 고객은 전문화된 외부 서비스와 통합하는 것이 좋습니다.

#### 감사 로그 삭제 속성 {#audit-purge-properties}

허용되는 속성은 다음과 같습니다.

*default*&#x200B;을(를) 나타내는 열은 기본값이 적용될 때 미래의 기본값을 나타냅니다. *TBD*&#x200B;은(는) 아직 결정되지 않은 환경 ID를 반영합니다.


| 속성 | envs>TBD의 향후 기본값 | envs&lt;=TBD의 향후 기본값 | required | 유형 | 값 |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| 규칙 | - | - | 예 | 오브젝트 | 복제, 페이지, dam 노드 중 하나 이상. 이러한 각 노드는 아래의 속성을 사용하여 규칙을 정의합니다. 모든 속성을 선언해야 합니다. |
| maximumAgeDays | 7일 | 전체 2557(7년 + 2윤일) | 예 | 정수 | 복제, 페이지 또는 dam의 경우: 감사 로그가 유지되는 일 수입니다. 구성된 값보다 오래된 감사 로그는 제거됩니다. |
| contentPath | &quot;/content&quot; | &quot;/content&quot; | 예 | 문자열 | 관련 유형에 대해 감사 로그가 삭제되는 경로. &quot;/content&quot;로 설정해야 합니다. |
| 유형 | 모든 값 | 모든 값 | 예 | 열거형 배열 | **복제**&#x200B;의 경우 열거된 값은 활성화, 비활성화, 삭제, 테스트, 역방향, 내부 폴링입니다. **페이지**&#x200B;의 경우 열거된 값은 PageCreated, PageModified, PageMoved, PageDeleted, VersionCreated, PageRestored, PageRolled Out, PageValid, PageInvalid입니다. **dam**&#x200B;의 경우 열거형 값은 ASSET_EXPIRING, METADATA_UPDATED, ASSET_EXPIRED, ASSET_REMOVED, RESTORED, ASSET_MOVED, ASSET_VIEWED, PROJECT_VIEWED, PUBLISHED_EXTERNAL, COLLECTION_VIEWED, VERSIONED, ADDED_COMMENT, RENDITION_UPDATED, ACCEPTED, DOWNLOADED, SUBASSET_UPDATED, ASSET_CREATED, ASSET_SHARED, RENDITION_DOWNLOADED, REJECTED입니다. |
