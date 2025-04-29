---
title: UUID 참조용 콘텐츠 조각 업그레이드
description: Headless 콘텐츠 게재를 위해 Adobe Experience Manager as a Cloud Service에서 최적화된 UUID 참조를 위해 콘텐츠 조각을 업그레이드하는 방법을 알아봅니다.
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
exl-id: 004d1340-8e3a-4e9a-82dc-fa013cea45a7
source-git-commit: fdfe0291ca190cfddf3bed363a8c2271a65593a1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 2%

---

# UUID 참조용 콘텐츠 조각 업그레이드 {#upgrade-content-fragments-for-UUID-references}

GraphQL 필터의 안정성을 최적화하기 위해 UUID(범용 고유 식별자)를 사용하도록 콘텐츠 조각에서 콘텐츠 및 조각 참조를 업그레이드할 수 있습니다.

원래 콘텐츠 조각 모델은 **콘텐츠 참조** 및 **조각 참조**&#x200B;의 데이터 형식을 제공했습니다. 이러한 두 참조는 모두 참조된 리소스를 가리키는 경로를 사용하며 리소스를 이동할 경우 이 경로가 오래된 경로가 될 수 있습니다. 이러한 참조가 대부분의 시나리오에서 충분치 않지만 콘텐츠 조각 모델 은 UUID를 기반으로 참조를 제공하도록 확장되었습니다.

* **콘텐츠 참조 (UUID)**
* **조각 참조(UUID)**.

이러한 새 참조 유형은 새 콘텐츠 조각 모델 및 조각에서 모두 사용하고 기존 인스턴스를 확장하는 데 사용할 수 있습니다.

기존 콘텐츠 조각 및 모델을 업그레이드하려면 여기에 설명된 절차를 실행할 수 있습니다.

>[!CAUTION]
>
>업그레이드 절차를 실행하기 전에 항상 [시험 실행을 실행](#execute-a-dry-run)하여 콘텐츠에 발생할 수 있는 모든 문제를 강조해야 합니다.

## 업그레이드된 항목 {#what-is-upgraded}

다음과 같이 업데이트되었습니다.

* 데이터 유형 필드:
   * **콘텐츠 참조**&#x200B;이(가) **콘텐츠 참조(UUID)**(으)로 변환됨
   * **조각 참조**&#x200B;이(가) **조각 참조(UUID)**(으)로 변환됨
* 이러한 필드에 있는 경로 기반 참조의 값은 해당 UUID로 대체됩니다

>[!NOTE]
>
>업그레이드 후에도 콘텐츠 조각 모델 편집기에서 두 데이터 유형을 계속 사용할 수 있습니다. 두 유형(UUID 기반 유형을 사용할 것으로 예상되지만)을 기반으로 새 필드를 생성하고 필요한 경우 업그레이드를 다시 실행할 수 있습니다.

## 업그레이드되지 않은 항목 {#what-is-not-upgraded}

다음 참조는 업그레이드되지 않습니다.

* 페이지 참조 - UUID는 아직 지원되지 않습니다.
* 잘못된 참조(예: 콘텐츠 조각 경로의 대상 또는 에셋 경로가 존재하지 않는 경우)

   * 콘텐츠 조각 경로 또는 에셋 경로가 잘못된 것처럼, 할당할 해당 UUID가 없는 잘못된 참조는 업그레이드되지 않습니다. 원본 참조는 그대로 유지됩니다.

   * [시험 실행](#execute-a-dry-run)을 사용하여 잘못된 참조를 제거하십시오.

  >[!NOTE]
  >
  >유효하지 않으면 업그레이드와 관계없이 사용할 수 없습니다.

## 업그레이드하지 말아야 할 경우 {#when-you-should-not-upgrade}

업그레이드하지 마십시오.

* UUID는 아직 페이지 참조에 지원되지 않으므로 콘텐츠 조각 중 하나라도 페이지 참조를 사용하는 경우

## UUID 참조의 제한 사항 {#limitations-of-uuid-references}

현재 UUID를 기반으로 참조를 사용할 때는 다음 제한이 적용됩니다.

* 모델

   * 컨텐츠 조각 UUID 또는 컨텐츠 참조 UUID 필드가 있는 새 컨텐츠 조각 모델을 OpenAPI를 통해 생성할 수 없습니다.
   * 모델에 대한 `id` 필드가 UUID 기반으로 변경되지 않았습니다. 모델의 base64 디코딩 경로를 사용합니다. 모델을 이동할 수 없으므로 이 값은 여전히 안정적입니다.

* 자산

   * OpenAPI를 통해 콘텐츠 조각을 만드는 경우 UUID 기반 참조 필드의 값을 설정하는 경우에도 조각 또는 에셋에 대한 참조를 지정하는 데 각각 `fragment-reference` 또는 `content-reference` 필드 형식을 사용해야 합니다.

## 계획 업그레이드 {#upgrade-planning}

업그레이드를 실행하기 전에 몇 가지 준비 단계를 수행해야 합니다.

### 시험 실행 {#execute-a-dry-run}

콘텐츠를 업그레이드할 때마다 *매*&#x200B;마다 먼저 시험 실행을 수행하는 것이 좋습니다. 이렇게 하면 잠재적인 문제를 강조 표시하는 항목이 있는 로그 파일이 만들어집니다.

* 잘못된 참조
* 페이지 참조

`dryRun` 모드에서 콘텐츠 업그레이드를 실행하여 다음 작업을 수행합니다.

* 잘못된 참조를 식별하여 로그 파일에 나열합니다.
그런 다음 실제 콘텐츠 업그레이드를 실행하기 전에 이러한 참조를 수정할 수 있습니다.
* 페이지 참조를 식별하여 로그 파일에 나열합니다.
페이지 참조가 검색되면 [콘텐츠 업그레이드를 실행하지 말아야 합니다](#when-you-should-not-upgrade).


### 컨텐츠 고정 적용 {#enforce-a-content-freeze}

콘텐츠 업그레이드 실행은 콘텐츠 동결 기간 동안 계획해야 합니다.

콘텐츠가 동결되는 기간은 업그레이드되는 콘텐츠 조각의 볼륨에 따라 다릅니다. 따라서 업그레이드의 범위는 몇 분에서 몇 시간 사이일 수 있으며 콘텐츠 업그레이드를 시작할 때 사용되는 매개 변수에 따라서도 달라집니다.

## 콘텐츠 업그레이드 실행 {#running-the-content-upgrade}

끝점을 사용하여 콘텐츠 업그레이드를 관리할 수 있습니다. `/libs/dam/cfm/maintenance.json`

>[!NOTE]
>
>끝점에 액세스하려면 계정에 `Administrator` 역할이 필요합니다.

### 콘텐츠 업그레이드 시작 {#start-a-content-upgrade}

| 엔드포인트 | HTTP 요청 유형 | 댓글 |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **요청 매개 변수** | **값** | |
| action | `start` | |
| serviceTypeId | `uuidUpgradeService` | 서비스 유형 ID(사전 정의된 고정 값). |
|  segmentSize | `1000` | 한 세그먼트(일괄 처리)에서 업그레이드할 콘텐츠 조각 또는 모델의 수입니다. |
| 기본 경로 | `/conf` | 다음 중 하나를 지정합니다.<ul><li>모든 AEM 구성을 업그레이드하기 위한 루트 `/conf`</li><li>선택한 AEM 구성 경로. 콘텐츠 업그레이드가 실행되는 <br>예: `/conf/wknd-shared`은(는) 단일 테넌트 `wknd-shared`만 업그레이드합니다.</li></ul> |
| 간격 | `10` | 콘텐츠 조각 또는 모델의 다음 세그먼트가 업그레이드되는 간격(초)입니다. |
| 모드 | `replicate`, `noReplicate` | <ul><li>`replicate`: 모든 AEM 게시 인스턴스에서 동일한 작업을 복제합니다.</li><li>`noReplicate`: AEM 작성자 인스턴스에서만 작업을 실행합니다.</li></ul> |
| dryRun |  `true`, `false` | <ul><li>`false`: 콘텐츠 변경 내용을 저장하지 않고 콘텐츠 업그레이드를 시뮬레이션합니다.</li><li>`true`: 콘텐츠 업그레이드를 수행하고 콘텐츠 변경 내용을 저장합니다.</li></ul> |
| **응답 세부 정보** | **값** | |
| jobId | `UUID` |  콘텐츠 업그레이드를 실행하는 작업의 ID입니다.<ul><li>이 ID는 이 실행과 관련된 모든 후속 호출에 필요합니다.</li><li>`mode` 값이 `replicate`(으)로 설정된 경우 AEM 게시 인스턴스에서의 실행도 동일한 `jobId` 아래에 있어야 합니다.</li></ul> |
| 매개 변수 | 콘텐츠 업그레이드 매개 변수 | 여기에는 콘텐츠 업그레이드를 시작하기 위해 제공되는 초기 매개 변수와 일부 내부 기본값이 포함됩니다. |


### 콘텐츠 업그레이드 요청 예 {#example-content-upgrade-request}

+++요청

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
 
{
    "action": "start",
    "serviceTypeId": "uuidUpgradeService",
    "segmentSize": 1000,
    "basePath": "/conf/wknd-shared",
    "interval": 10,
    "mode": "replicate",
    "dryRun": true
}
```

+++

+++응답

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:34:37 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 386
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "basePath": "/conf/wknd-shared",
    "topic": "cfm/maintenance",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  }
}
```

+++

### 콘텐츠 업그레이드 상태 가져오기 {#get-the-status-of-a-content-upgrade}

| 엔드포인트 | HTTP 요청 유형 | 댓글 |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `GET` | |
| **요청 매개 변수** | **값** | |
| action | 상태 | |
| jobId | `<UUID>` | 콘텐츠 업그레이드를 시작하기 위한 호출에서 반환된 `jobId`입니다. |
| **응답 세부 정보** | **값** | |
| 상태 | JSON 값 | 콘텐츠 업그레이드의 자세한 상태를 포함합니다.<ul><li>간격(초)마다 업데이트됩니다.</li><li>`uuidUpgradeService` 실행에는 다음 두 단계가 있습니다.<ol><li>0단계에서 콘텐츠 조각 모델 업그레이드</li><li>콘텐츠 조각 업그레이드 1단계</li></ol></li><li>각 단계에서 통계는 매 간격 후에 업데이트됩니다.</li><li>&quot;jobStatus&quot;: &quot;COMPLETED&quot;는 업그레이드를 성공적으로 완료된 것으로 표시합니다.</li><li>다른 상태 값은 설명이 따로 필요하지 않습니다.</li></ul> |

### 콘텐츠 업그레이드 상태 요청 예 {#example-content-upgrade-status-request}

+++요청

```http
GET http://localhost:4502/libs/dam/cfm/maintenance.json?action=status&jobId=91af43a6-63ff-45e5-ac7b-06ccf565bdfa
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
```

+++

+++응답

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:35:51 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 1116
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "eventProcessed": 1,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "confPath": "/conf/wknd-shared",
    "topic": "cfm/uuid-migration",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  },
  "status": {
    "jobStatus": "COMPLETED",
    "lastModified": 1729089310301,
    "currentPhaseIndex": 1,
    "phases": {
      "phase-0": {
        "bookmark": 1727183332520,
        "stats": {
          "successCount": 2,
          "skippedCount": 1,
          "errorCount": 0
        },
        "name": "modelUpgrade",
        "lastModified": 1729089290040,
        "isCompleted": true
      },
      "phase-1": {
        "bookmark": 1727183347990,
        "stats": {
          "successCount": 29,
          "skippedCount": 0,
          "errorCount": 1
        },
        "name": "cfUpgrade",
        "lastModified": 1729089310298,
        "isCompleted": true
      }
    }
  }
}
```

+++

+++샘플 로그 파일

HTTP 끝점에서 가져온 실행 중인 콘텐츠 업그레이드의 상태 외에도 AEM 로그는 콘텐츠 수준의 진행 상황에 대한 자세한 정보를 제공합니다. 예:

```xml
#Successful model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/article , status: SUCCESS, skips: [], errors: []
 
#Successful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/san-diego-surf-spots/san-diego-surfspots , status: SUCCESS, skips: [], errors: []
 
#Unsuccessful/Skipped model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/adventure , status: SKIPPED, skips: [Model: '/conf/wknd-shared/settings/dam/cfm/models/adventure', no upgradeable fields found], errors: []
 
#Unsuccessful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van , status: FAILED, skips: [], errors: [Path '/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van', Variation: 'master' Field 'featuredImage', Value '/content/dam/wknd-shared/en/magazine/western-australia/adobestock_156407519.jpeg' is invalid; will not upgrade this field.] 
```

또한 콘텐츠 조각 및 모델의 각 세그먼트(배치) 처리 후 누적 상태가 기록되어 지금까지의 진행 상황이 요약됩니다. 예:

```xml
com.adobe.cq.dam.cfm.impl.servicing.PhaseChainProcessor Phase phase-x, processed a segment, stats: {successCount=29, skippedCount=0, errorCount=1}
```

+++

### 콘텐츠 업그레이드 중단 {#abort-a-content-upgrade}

>[!CAUTION]
>
>콘텐츠 업그레이드 중단(시험 실행이 아님):
>
>* 이미 변경한 내용을 되돌리지 않습니다.
>* 은(는) 콘텐츠를 혼합 상태로 둘 수 있습니다
>
>이 작업은 주의하여 사용하십시오.

| 엔드포인트 | HTTP 요청 유형 | 댓글 |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **요청 매개 변수** | **값** | |
| action | abort | |
| jobId | `<UUID>` | 콘텐츠 업그레이드를 시작하기 위한 호출에서 반환된 `jobId`입니다. |
| **응답 세부 정보** | **값** | |
| 상태 | JSON 값 | 콘텐츠 업그레이드의 자세한 상태를 포함합니다.<ul><li>참고할 상태는 &quot;jobStatus&quot;: &quot;ABORTED&quot;입니다.<br>중단 작업 후에는 보류 중인 데이터 세그먼트가 처리되지 않습니다.</li><li>중단 전에 jobStatus가 &quot;COMPLETED&quot;이면 호출이 영향을 주지 않습니다.</li></ul> |

### 예 콘텐츠 업그레이드 요청 중단 {#example-abort-content-upgrade-request}

+++요청

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: Basic YWRtaW46YWRtaW4=
Accept: application/json
 
{
    "action": "abort",
    "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807"
    "mode": "replicate",
}
```

+++

+++응답

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:39:03 GMT
 
{
  "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807",
   ...
  "eventProcessed": 2,
  "parameters": {
    ...
    "abort": true,
    ...
  },
  "status": {
     "jobStatus": "ABORTED",
    ...
  }
}
```

+++
