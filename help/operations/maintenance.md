---
title: AEM as a Cloud Service의 유지 관리 작업
description: AEM as a Cloud Service의 유지 관리 작업
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: 068ae08fddd482e4367b4bf1c8cc3776bbb4cc6b
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---

# AEM as a Cloud Service의 유지 관리 작업

유지 관리 작업은 저장소를 최적화하기 위해 일정에 따라 실행되는 프로세스입니다. AEM을 Cloud Service으로 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요가 최소화됩니다. 고객은 애플리케이션 수준의 문제에 집중할 수 있으므로 인프라 운영을 Adobe에 집중할 수 있습니다.

유지 관리 작업에 대한 자세한 내용은 다음 페이지를 참조하십시오.

* [AEM 유지 관리 안내서](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [작업 대시보드 유지 관리 작업](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## 유지 관리 작업 구성

이전 버전의 AEM에서는 유지 관리 카드( 도구 > 작업 > 유지 관리)를 사용하여 유지 관리 작업을 구성할 수 있습니다. AEM as a Cloud Service의 경우 유지 관리 카드를 더 이상 사용할 수 없으므로 Cloud Manager를 사용하여 소스 제어에 구성을 커밋하고 배포해야 합니다. Adobe은 고객이 다른 유지 관리 작업을 구성할 수 있을 때(아래 표 참조) 고객 결정을 필요로 하지 않는 유지 관리 작업(예: 데이터 저장소 가비지 수집)을 관리합니다.

>[!CAUTION]
>
>Adobe은 성능 저하 등의 문제를 완화하기 위해 고객의 유지 관리 작업 구성 설정을 무시할 수 있는 권한을 갖습니다.

다음 표는 AEM as a Cloud Service 릴리스 시 사용할 수 있는 유지 관리 작업을 보여줍니다.

| 유지 관리 작업 | 구성을 소유하는 사용자 | 구성 방법(선택 사항) |
|---|---|---|
| 데이터 저장소 가비지 수집 | Adobe | 해당 사항 없음 - 소유한 전체 Adobe |
| 버전 삭제 | Adobe | Adobe이 완전히 소유하지만 향후에는 고객이 특정 매개 변수를 구성할 수 있습니다. |
| 감사 로그 삭제 | Adobe | Adobe이 완전히 소유하지만 향후에는 고객이 특정 매개 변수를 구성할 수 있습니다. |
| Lucene 바이너리 정리 | Adobe | 사용하지 않으므로 Adobe에 의해 비활성화됩니다. |
| 임시 작업 제거 | 고객 | github에서 수행해야 합니다. <br> 또는 폴더에 속성을  `/libs` 만들어 아래의 바로 사용 가능한 유지 관리 창 구성 노드 `/apps/settings/granite/operations/maintenance/granite_weekly` 를 재정의합니다 `granite_daily`. 추가 구성 세부 사항은 아래의 유지관리 창 테이블을 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 다른 노드를 추가하여 유지 관리  `granite_TaskPurgeTask`작업을 활성화합니다. <br> OSGI 속성 구성 은  [AEM 6.5 Maintenance Task 설명서 를 참조하십시오](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| 워크플로우 삭제 | 고객 | github에서 수행해야 합니다. <br> 폴더 아래에 속성을  `/libs` 만들어 아래의 바로 사용 가능한 유지 관리 창 구성 노드를 `/apps/settings/granite/operations/maintenance/granite_weekly` 재정의합니다  `granite_daily`. 추가 구성 세부 사항은 아래의 유지관리 창 테이블을 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 다른 노드를 추가하여 유지 관리  `granite_WorkflowPurgeTask`작업을 활성화합니다. <br> OSGI 속성 구성 은  [AEM 6.5 Maintenance Task 설명서 를 참조하십시오](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| 프로젝트 삭제 | 고객 | github에서 수행해야 합니다. <br> 또는 폴더에 속성을  `/libs` 만들어 아래의 바로 사용 가능한 유지 관리 창 구성 노드 `/apps/settings/granite/operations/maintenance/granite_weekly` 를 재정의합니다 `granite_daily`. 추가 구성 세부 사항은 아래의 유지관리 창 테이블을 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 노드를 추가하여 유지 관리  `granite_ProjectPurgeTask`작업을 활성화합니다. <br> OSGI 속성 구성  [AEM 6.5 Maintenance Task Documentation 을 참조하십시오](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

고객은 일별, 주별 또는 월별 유지 관리 기간 동안 각 워크플로우 삭제, 임시 태스크 삭제 및 프로젝트 삭제 유지 관리 작업을 실행하도록 예약할 수 있습니다. 이러한 구성은 소스 제어에서 직접 편집해야 합니다. 아래 표에서는 각 창에 사용할 수 있는 구성 매개 변수에 대해 설명합니다. 또한 테이블 뒤에 제공된 위치 및 코드 샘플도 참조하십시오.

<table>
 <tbody>
  <tr>
    <th>유지 관리 창 구성</th>
    <th>구성을 소유하는 사용자</th>
    <th>구성 유형</th>
    <th>매개 변수</th>
  </tr>
  <tr>
    <td>일별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
  <td>
  <p><strong>windowSchedule=daily</strong> (이 값은 변경할 수 없습니다.)</p>
  <p><strong>windowStartTime=HH:</strong> 24시간 클럭으로 사용 일별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</p>
  <p><strong>windowEndTime=HH:</strong> 24시간 클럭으로 사용 일별 유지 관리 창과 연관된 유지 관리 작업이 아직 완료되지 않은 경우 실행을 중지해야 하는 시기를 정의합니다.</p>
  </td> 
  </tr>
  <tr>
    <td>매주</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=weekly</strong> (이 값은 변경할 수 없음)</p>
    <p><strong>windowStartTime=HH:</strong> 24시간 클럭으로 사용 주별 유지 관리 기간과 연관된 유지 관리 작업 실행 시기를 정의합니다.</p>
    <p><strong>windowEndTime=HH:</strong> 24시간 클럭으로 사용 아직 완료되지 않은 경우 주간 유지 관리 창과 연관된 유지 관리 작업이 실행을 중지해야 하는 시기를 정의합니다.</p>
    <p><strong>windowScheduleWeekle= 1-7에서 2개의 값 배열(예:[5,5])</strong>  배열의 첫 번째 값은 작업이 예약된 시작일이고 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 각각 windowStartTime 및 windowEndTime에 의해 제어됩니다.</p>
    </td>
  </tr>
  <tr>
    <td>매월</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=daily</strong> (이 값은 변경할 수 없습니다.)</p>
    <p><strong>windowStartTime=HH:</strong> 24시간 클럭으로 사용 월별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</p>
    <p><strong>windowEndTime=HH:</strong> 24시간 클럭으로 사용 아직 완료되지 않은 경우 월별 유지 관리 창과 연관된 유지 관리 작업이 실행을 중지해야 하는 시기를 정의합니다.</p>
    <p><strong>windowScheduleWeekle=1-7에서 2개 값의 배열(예:[5,5])</strong>  배열의 첫 번째 값은 작업이 예약된 시작일이고 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 각각 windowStartTime 및 windowEndTime에 의해 제어됩니다.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0을 사용하여 월의 첫 번째 주에 예약하거나 월의 마지막 주에 예약하십시오. 값이 없을 경우, 매달 windowScheduleWeekday에 의해 관리되는 방식으로 매일 일자리를 예약할 수 있습니다.</p>
    </td> 
    </tr>
    </tbody>
</table>

**위치**:

* 일별 - /apps/settings/granite/operations/maintenance/granite_daily
* 주별 - /apps/settings/granite/operations/maintenance/granite_weekly
* 월별 - /apps/settings/granite/operations/maintenance/granite_monthly

**코드 샘플**:

코드 샘플 1(일별)

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

코드 샘플 2(주별)

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

코드 샘플 3(월별)

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
