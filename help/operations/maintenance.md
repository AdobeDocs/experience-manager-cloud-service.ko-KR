---
title: Cloud Service의 유지 관리 작업
description: Cloud Service의 유지 관리 작업
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
translation-type: tm+mt
source-git-commit: 5351b4b9ceed04c572bafc02f47d6fa666e5580d
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 2%

---

# Cloud Service의 유지 관리 작업

유지 관리 작업은 저장소를 최적화하기 위해 일정에 따라 실행되는 프로세스입니다. Cloud Service으로 AEM을 사용하는 경우 유지 관리 작업의 운영 속성을 구성할 필요가 거의 없습니다. 고객은 애플리케이션 수준의 관심사에 리소스를 집중하여 인프라 작업을 Adobe으로 전환할 수 있습니다.

유지 관리 작업에 대한 자세한 내용은 다음 페이지를 참조하십시오.

* [AEM 유지 관리 가이드](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [작업 대시보드 유지 관리 작업](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## 유지 관리 작업 구성

이전 버전의 AEM에서는 유지 관리 카드(도구 > 작업 > 유지 관리)를 사용하여 유지 관리 작업을 구성할 수 있습니다. Cloud Service의 경우 유지 관리 카드를 더 이상 사용할 수 없으므로 클라우드 관리자를 사용하여 소스 제어에 구성을 커밋하고 배포해야 합니다. Adobe은 고객이 다른 유지 관리 작업을 구성할 수 있을 때(예: 데이터 저장소 가비지 수집) 고객 결정이 필요하지 않은 유지 관리 작업을 관리합니다(아래 표 참조).

>[!CAUTION]
>
>Adobe은 성능 저하 등의 문제를 줄이기 위해 고객의 유지 관리 작업 구성 설정을 재정의할 수 있는 권한을 가집니다.

다음 표는 AEM이 Cloud Service으로 릴리스될 때 사용할 수 있는 유지 관리 작업을 보여 줍니다.

| 유지 관리 작업 | 구성을 소유하는 사용자 | 구성 방법(선택 사항) |
|---|---|---|
| 데이터 저장소 가비지 컬렉션 | Adobe | 해당 없음 - 완전히 Adobe 소유 |
| 버전 삭제 | Adobe | Adobe이 완전히 소유하지만 향후 고객은 특정 매개 변수를 구성할 수 있습니다. |
| 감사 로그 삭제 | Adobe | Adobe이 완전히 소유하지만 향후 고객은 특정 매개 변수를 구성할 수 있습니다. |
| Lucene 바이너리 정리 | Adobe | 사용하지 않고 따라서 Adobe에 의해 비활성화됩니다. |
| 임시 작업 제거 | 고객 | github로 해야 합니다. <br> 폴더 또는 폴더 아래에 속성을  `/libs` 생성하여 기본 유지 관리 창 구성 노드를  `/apps/settings/granite/operations/maintenance/granite_weekly` 재정의합니다 `granite_daily`. 자세한 구성 내용은 아래 유지 관리 창 테이블을 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 다른 노드를 추가(이름을 지정) `granite_TaskPurgeTask`하여 유지 관리 작업을 활성화합니다. <br> OSGI 속성을 구성합니다( [AEM 6.5 유지 관리 작업 설명서 참조)](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| 워크플로우 삭제 | 고객 | github로 해야 합니다. <br> 폴더 아래에 속성을 생성하여 기본 유지 관리 창 구성 노드 `/libs` 를 `/apps/settings/granite/operations/maintenance/granite_weekly` 재정의합니다 `granite_daily`. 자세한 구성 내용은 아래 유지 관리 창 테이블을 참조하십시오. <br> 위의 노드 아래에 적절한 속성을 사용하여 다른 노드를 추가(이름을 지정) `granite_WorkflowPurgeTask`하여 유지 관리 작업을 활성화합니다. <br> OSGI 속성 구성을 참조하십시오.  [AEM 6.5 유지 관리 작업 설명서](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| 프로젝트 삭제 | 고객 | github로 해야 합니다. <br> 폴더 또는 폴더 아래에 속성을  `/libs` 생성하여 기본 유지 관리 창 구성 노드를  `/apps/settings/granite/operations/maintenance/granite_weekly` 재정의합니다 `granite_daily`. 자세한 구성 내용은 아래 유지 관리 창 테이블을 참조하십시오. <br> 적절한 속성을 사용하여 위의 노드 아래에 노드를 추가(이름을 지정) `granite_ProjectPurgeTask`하여 유지 관리 작업을 활성화합니다. <br> OSGI 속성 구성  [AEM 6.5 유지 관리 작업 설명서를 참조하십시오.](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

고객은 일별, 주별 또는 월별 유지 관리 기간 동안 실행할 워크플로우 삭제, 임시 태스크 삭제 및 프로젝트 삭제 유지 관리 작업을 각각 예약할 수 있습니다. 이러한 구성은 소스 제어에서 직접 편집해야 합니다. 아래 표에서는 각 창에 사용할 수 있는 구성 매개 변수에 대해 설명합니다.

<table>
 <tbody>
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
    <td>아래 위치 1 참조</td>
    <td>아래의 코드 샘플 1 참조</td>
  <td><p><strong>windowSchedule= daily</strong></p> (이 값은 변경할 수 없습니다.)
  <p><strong>windowStartTime= HH:</strong> Mm24시간 시경으로 사용 일별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</p>
  <p><strong>windowEndTime= HH:</strong> MM을 24시간 시간으로 사용 일별 유지 관리 창과 연관된 유지 관리 작업이 아직 완료되지 않은 경우 실행이 중지되는 시기를 정의합니다.</p>
  </td> 
  </tr>
  <tr>
    <td>매주</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>아래 위치 2 참조</td>
    <td>아래의 코드 샘플 2를 참조하십시오.</td>
    <td>
    <strong>windowSchedule= weekly</strong> (이 값은 변경할 수 없음) windowStartTime= HH:
    <strong> </strong> Mm24시간 시경으로 사용 주별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.
    <strong>windowEndTime= HH:</strong> MM을 24시간 시간으로 사용 아직 완료되지 않은 경우 주별 유지 관리 창과 연관된 유지 관리 작업의 실행을 중지해야 하는 시기를 정의합니다.
    <strong>windowScheduleWeeks= 1-7(예:[5,5])</strong> 배열의 첫 번째 값은 작업이 예약된 시작일이고 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 각각 windowStartTime 및 windowEndTime의 영향을 받습니다.
    </td> 
  </tr>
  <tr>
    <td>매월</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>아래 위치 3 참조</td>
    <td>아래의 코드 샘플 3 참조</td>
    <td>
    <strong>windowSchedule= daily</strong> (이 값은 변경할 수 없습니다) windowStartTime= HH:
    <strong> </strong> MM을 24시간 시경으로 사용합니다. 월별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.
    <strong>windowEndTime= HH:</strong> MM을 24시간 시간으로 사용 아직 완료되지 않은 경우 월별 유지 관리 창과 연관된 유지 관리 작업의 실행을 중지해야 하는 시기를 정의합니다.
    <strong>windowScheduleWeeks = 1-7(예:[5,5])</strong> 배열의 첫 번째 값은 작업이 예약된 시작일이고 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 각각 windowStartTime 및 windowEndTime의 영향을 받습니다.
    <strong>windowFirstLastStartDay= 0/10</strong> 을 사용하여 월의 첫 번째 주에 예약하거나 월의 마지막 주에 예약합니다. 값이 없으면 windowScheduleWeeks가 매월 관리하는 것처럼 매일 작업을 효과적으로 예약할 수 있습니다.
    </td> 
    </tr>
    </tbody>
</table>

위치:

1. /apps/settings/granite/operations/maintenance/granite_daily
2. /apps/settings/granite/operations/maintenance/granite_weekly
3. /apps/settings/granite/operations/maintenance/granite_monthly

코드 샘플:

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
