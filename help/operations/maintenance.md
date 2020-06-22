---
title: Cloud Service으로 AEM의 유지 관리 작업
description: 'Cloud Service으로 AEM의 유지 관리 작업 '
translation-type: tm+mt
source-git-commit: e9ee1064c5fa62b56c822a18ad6ca8cc4d09fa75
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 2%

---


# Cloud Service으로 AEM의 유지 관리 작업

유지 관리 작업은 저장소를 최적화하기 위해 일정에 따라 실행되는 프로세스입니다. AEM을 Cloud Service으로 사용할 경우 고객이 유지 관리 작업의 운영 속성을 구성할 필요가 거의 없습니다. 고객은 애플리케이션 수준의 문제에 리소스를 집중하여 인프라 작업을 Adobe에 맡길 수 있습니다.

유지 관리 작업에 대한 자세한 내용은 다음 페이지를 참조하십시오.

* [AEM 유지 관리 가이드](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [작업 대시보드 유지 관리 작업](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## 유지 관리 작업 구성

이전 버전의 AEM에서는 유지 관리 카드(도구 > 작업 > 유지 관리)를 사용하여 유지 관리 작업을 구성할 수 있습니다. AEM을 Cloud Service으로 사용하는 경우 유지 관리 카드를 더 이상 사용할 수 없으므로 클라우드 관리자를 사용하여 소스 제어 및 배포에 대한 구성을 커밋해야 합니다. Adobe는 고객이 다른 유지 관리 작업을 구성할 수 있을 때(예: 데이터 저장소 가비지 수집) 고객 결정이 필요하지 않은 유지 관리 작업을 관리합니다(아래 표 참조).

>[!CAUTION]
>
>Adobe는 성능 저하 등의 문제를 줄이기 위해 고객의 유지 관리 작업 구성 설정을 무시할 권한을 가집니다.

다음 표는 AEM을 Cloud Service으로 출시할 때 사용할 수 있는 유지 관리 작업을 보여줍니다.

| 유지 관리 작업 | 구성을 소유하는 사용자 | 구성 방법(선택 사항) |
|---|---|---|
| 데이터 저장소 가비지 컬렉션 | Adobe | 해당 없음 - Adobe 소유 제품 |
| 버전 삭제 | Adobe | Adobe가 완전히 보유하고 있지만 향후 고객은 특정 매개 변수를 구성할 수 있습니다. |
| 감사 로그 삭제 | Adobe | Adobe가 완전히 보유하고 있지만 향후 고객은 특정 매개 변수를 구성할 수 있습니다. |
| Lucene 바이너리 정리 | Adobe | Adobe에서 사용하지 않고 사용할 수 없습니다. |
| 임시 작업 제거 | 고객 | 기툴빗으로 해야 합니다 <br> 폴더 또는 폴더 아래에 속성을 생성하여 기본 유지 관리 창 구성 노드 `/libs` 를 재정의합니다 `/apps/settings/granite/operations/maintenance/granite_weekly``granite_daily`. 자세한 구성 내용은 아래 유지 관리 창 표를 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 다른 노드를 추가하여 유지 관리 작업 `granite_TaskPurgeTask`을 활성화합니다. <br> OSGI 속성을 구성합니다( [AEM 6.5 유지 관리 작업 설명서 참조)](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| 워크플로우 삭제 | 고객 | 기툴빗으로 해야 합니다 <br> 폴더 `/libs` 또는 폴더 아래에 속성을 만들어 기본 유지 관리 창 구성 노드`/apps/settings/granite/operations/maintenance/granite_weekly` 를 재정의합니다 `granite_daily`. 자세한 구성 내용은 아래 유지 관리 창 표를 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 다른 노드를 추가하여 유지 관리 작업 `granite_WorkflowPurgeTask`을 활성화합니다. <br> OSGI 속성 구성을 참조하십시오. AEM [6.5 유지 관리 작업 설명서](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| 프로젝트 삭제 | 고객 | 기툴빗으로 해야 합니다 <br> 폴더 또는 폴더 아래에 속성을 생성하여 기본 유지 관리 창 구성 노드 `/libs` 를 재정의합니다 `/apps/settings/granite/operations/maintenance/granite_weekly``granite_daily`. 자세한 구성 내용은 아래 유지 관리 창 표를 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 노드를 추가하여 유지 관리 작업 `granite_ProjectPurgeTask`을 활성화합니다. <br> OSGI 속성 구성: [AEM 6.5 유지 관리 작업 설명서를 참조하십시오.](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

고객은 일별, 주별 또는 월별 유지 관리 기간 동안 실행할 워크플로우 삭제, 임시 작업 삭제 및 프로젝트 삭제 유지 관리 작업을 예약할 수 있습니다. 이러한 구성은 소스 제어에서 직접 편집해야 합니다. 아래 표에서는 각 창에 사용할 수 있는 구성 매개 변수에 대해 설명합니다.

<table>
  <tr>
    <th>유지 관리 창 구성</th>
    <th>구성을 소유하는 사용자</th>
    <th>구성 유형</th>
    <th>위치</th>
    <th>예</th>
    <th>매개 변수</th>
  </tr>
  <tr>
    <td>일별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td><code>/apps/settings/granite/operations/maintenance/granite_daily </code></td>
    <td>아래의 코드 샘플 1 참조</td>
   <td>
    <ul>
    <li><strong>windowSchedule</strong> = 일별(이 값은 변경할 수 없음)</li>
    <li><strong>windowStartTime</strong> = HH:MM(24시간 시계에 사용) 일별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</li>
    <li><strong>windowEndTime</strong> = HH:MM(24시간)으로 사용) 일별 유지 관리 창과 연관된 유지 관리 작업이 아직 완료되지 않은 경우 실행을 중지해야 하는 시기를 정의합니다.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>매주</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td><code>/apps/settings/granite/operations/maintenance/granite_weekly</code></td>
    <td>아래의 코드 샘플 2 참조</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = 주별(이 값은 변경할 수 없음)</li>
    <li><strong>windowStartTime</strong> = HH:MM(24시간 시계에 사용) 주별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</li>
    <li><strong>windowEndTime</strong> = HH:MM(24시간)으로 사용) 주별 유지 관리 창과 연관된 유지 관리 작업이 아직 완료되지 않은 경우 실행을 중지해야 하는 시기를 정의합니다.</li>
    <li><strong>windowScheduleWeeks = 1-7에서 2개 값의 배열. 예: [5,5].</strong> 배열의 첫 번째 값은 작업이 예약되는 시작일이며 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 windowStartTime과 windowEndTime에 의해 각각 관리됩니다.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>매월</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td><code>/apps/settings/granite/operations/maintenance/granite_monthly</code></td>
    <td>아래의 코드 샘플 3 참조</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = 일별(이 값은 변경할 수 없음)</li>
    <li><strong>windowStartTime</strong> = HH:MM(24시간 시계에 사용) 월별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</li>
    <li><strong>windowEndTime</strong> = HH:MM(24시간)으로 사용) 아직 완료되지 않은 경우 월별 유지 관리 창과 연관된 유지 관리 작업의 실행을 중지해야 하는 시기를 정의합니다.</li>
    <li><strong>windowScheduleWeeks = 1-7에서 2개 값의 배열. 예: [5,5].</strong> 배열의 첫 번째 값은 작업이 예약되는 시작일이며 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 windowStartTime과 windowEndTime에 의해 각각 관리됩니다.</li>
    <li><strong>windowFirstLastStartDay - 0/1</strong> 0을 클릭하여 월의 첫 주에 예약하거나 월의 마지막 주에 예약합니다. 값이 없으면 windowScheduleWeeks가 매월 관리하는 것처럼 매일 작업을 효율적으로 예약하게 됩니다.</li>
    </ul> </td> 
  </tr>
</table>

코드 샘플 1

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

코드 샘플 2

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

코드 샘플 3

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
