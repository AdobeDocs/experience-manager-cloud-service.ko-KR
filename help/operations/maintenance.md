---
title: AEM as a Cloud Service에서의 유지 관리 작업
description: AEM as a Cloud Service에서의 유지 관리 작업
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 63%

---

# AEM as a Cloud Service에서의 유지 관리 작업 {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="유지 관리 작업"
>abstract="유지 관리 작업은 저장소 최적화를 위해 일정에 따라 실행되는 프로세스입니다. AEM as a Cloud Service를 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요성이 최소화됩니다. 고객은 인프라 운영을 Adobe에게 맡긴 채 애플리케이션 수준의 우려사항에 자원을 집중시킬 수 있습니다."

유지 관리 작업은 저장소 최적화를 위해 일정에 따라 실행되는 프로세스입니다. AEM as a Cloud Service를 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요성이 최소화됩니다. 고객은 인프라 운영을 Adobe에게 맡긴 채 애플리케이션 수준의 우려사항에 자원을 집중시킬 수 있습니다.

## 유지 관리 작업 구성 {#maintenance-tasks-configuring}

이전의 AEM 버전에서는 유지 관리 카드(도구 > 운영 > 유지 관리)를 사용해 유지 관리 작업을 구성할 수 있었습니다. AEM as a Cloud Service의 경우 유지 관리 카드가 더 이상 이용 가능하지 않기 때문에 Cloud Manager를 사용해 소스 제어에 구성을 커밋하고 배포해야 합니다. Adobe는 고객이 구성할 수 없는 설정들(예: 데이터스토어 가비지 수집, 감사 로그 삭제, 버전 삭제)이 포함되는 유지 관리 작업을 관리합니다. 기타 유지 관리 작업은 아래 표에 설명한 대로 고객이 구성할 수 있습니다.

>[!CAUTION]
>
>Adobe은 성능 저하와 같은 문제를 완화하기 위해 고객의 유지 관리 작업 구성 설정을 재정의할 권한을 보유합니다.

다음 표는 AEM as a Cloud Service 릴리스 당시 이용 가능한 유지 관리 작업을 설명합니다.

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
    <td>Adobe</td>
    <td>기존 환경(2023년 6월 1일 이전에 생성된 환경)의 경우 지우기는 비활성화되며 고객이 명시적으로 활성화하지 않는 한 향후 활성화되지 않습니다. 이 때 고객이 사용자 지정 값으로 환경을 구성할 수도 있습니다.<br><br> <!--Alexandru: please leave the two line breaks in place, otherwise spacing won't render properly-->새 환경(2023년 6월 1일부터 생성된 환경)은 기본적으로 아래 값으로 제거가 활성화되며, 고객은 사용자 지정 값으로 을 구성할 수 있습니다.
     <ol>
       <li>30일 넘는 구 버전 삭제</li>
       <li>지난 30일 이내 가장 최근의 5개 버전은 유지</li>
       <li>위의 규칙과 관계없이 가장 최근 버전은 보존됩니다.</li>
       <br>특정 날짜에 표시된 대로 사이트 페이지를 렌더링해야 하는 규제 요구 사항이 있는 고객은 전문 외부 서비스와 통합하는 것이 좋습니다.
     </ol></td>
  </td>
  </tr>
  <tr>
    <td>감사 로그 삭제</td>
    <td>Adobe</td>
    <td>기존 환경(2023년 6월 1일 이전에 생성된 환경)의 경우 지우기는 비활성화되며 고객이 명시적으로 활성화하지 않는 한 향후 활성화되지 않습니다. 이 때 고객이 사용자 지정 값으로 환경을 구성할 수도 있습니다.<br><br> <!-- See above for the two line breaks -->새 환경(2023년 6월 1일부터 생성된 환경)은 기본적으로 <code>/content</code> 다음 동작에 따른 저장소의 노드:
     <ol>
       <li>복제 감사의 경우, 3일 넘는 감사 로그 삭제</li>
       <li>DAM(애셋) 감사의 경우, 30일 넘는 감사 로그 삭제</li>
       <li>페이지 감사의 경우, 3일 넘는 감사 로그 삭제</li>
       <br>편집 불가능한 감사 로그를 생성하기 위한 규정 요구 사항이 있는 고객은 전문 외부 서비스와 통합하는 것이 좋습니다.
     </ol></td>
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
    <p>git에서 수행해야 합니다. 아래의 기본 제공 유지 관리 창 구성 노드 재정의 <code>/libs</code> 폴더 아래에 속성을 생성하여 <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> 또는 <code>granite_monthly</code>.</p>
    <p>추가적인 구성 세부 정보는 아래의 유지 관리 창 표를 참조하십시오. 위의 노드 아래에 다른 노드를 추가하여 유지 관리 작업을 활성화합니다. 이름 지정 <code>granite_TaskPurgeTask</code>, 속성 포함 <code>sling:resourceType</code> 을 로 설정 <code>granite/operations/components/maintenance/task</code> 및 속성 <code>granite.maintenance.name</code> 을 로 설정 <code>TaskPurge</code>. OSGI 속성을 구성합니다. 다음을 참조하십시오. <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code> 속성 목록.</p>
  </td>
  </tr>
    <tr>
    <td>워크플로 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. 아래의 기본 제공 유지 관리 창 구성 노드 재정의 <code>/libs</code> 폴더 아래에 속성을 생성하여 <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> 또는 <code>granite_monthly</code>. 추가적인 구성 세부 정보는 아래의 유지 관리 창 표를 참조하십시오.</p>
    <p>적절한 속성을 사용해 위 노드 아래에서 또 다른 노드를 추가하여(<code>granite_WorkflowPurgeTask</code>로 이름 지정) 유지 관리 작업을 활성화합니다. OSGI 속성을 구성합니다. <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html#regular-purging-of-workflow-instances">AEM 6.5 유지 관리 작업 문서</a>를 참조하십시오.</p>
  </td>
  </tr>
  <tr>
    <td>프로젝트 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. 아래의 기본 제공 유지 관리 창 구성 노드 재정의 <code>/libs</code> 폴더 아래에 속성을 생성하여 <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> 또는 <code>granite_monthly</code>. 추가적인 구성 세부 정보는 아래의 유지 관리 창 표를 참조하십시오.</p>
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
    <p><strong>windowScheduleWeekdays= 1~7의 두 값 배열(예: [5,5])</strong> 배열의 첫 번째 값은 작업이 예약된 시작일이며 두 번째 값은 작업이 중지되는 종료일입니다. 정확한 시작 및 종료 시간은 각각 windowStartTime과 windowEndTime이 제어합니다.</p>
    </td>
  </tr>
  <tr>
    <td>월별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=monthly</strong> (이 값은 변경해서는 안 됨)</p>
    <p>24시간 시계로 사용하는 <strong>windowStartTime=HH:MM</strong>입니다. 월별 유지 관리 창과 연계된 유지 관리 작업을 실행해야 하는 시점을 정의합니다.</p>
    <p>24시간 시계로 사용하는 <strong>windowEndTime=HH:MM</strong>입니다. 월별 유지 관리 창과 연계된 유지 관리 작업이 완료된 상태가 아닌 경우 실행을 정지해야 하는 시점을 정의합니다.</p>
    <p>이 일정 동안에는 유지 관리 작업을 두 번 이상 실행할 수 없습니다.</p>
    <p><strong>windowScheduleWeekdays=1-7 사이의 두 값 배열(예: [5,5])</strong> 배열의 첫 번째 값은 작업이 예약된 시작일이며 두 번째 값은 작업이 중지되는 종료일입니다. 정확한 시작 및 종료 시간은 각각 windowStartTime과 windowEndTime이 제어합니다.</p>
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
