---
title: AEM as a Cloud Service에서의 유지 관리 작업
description: AEM as a Cloud Service에서의 유지 관리 작업
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: def7f7071dac447397f40186de1380b8e5575608
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 4%

---

# AEM as a Cloud Service에서의 유지 관리 작업 {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="유지 관리 작업"
>abstract="유지 관리 작업은 저장소를 최적화하기 위해 일정에 따라 실행되는 프로세스입니다. AEM as a Cloud Service을 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요가 거의 없습니다. 고객은 애플리케이션 수준의 문제에 집중할 수 있으므로 인프라 운영을 Adobe에 집중할 수 있습니다."

유지 관리 작업은 저장소를 최적화하기 위해 일정에 따라 실행되는 프로세스입니다. AEM as a Cloud Service을 사용하면 고객이 유지 관리 작업의 운영 속성을 구성할 필요가 거의 없습니다. 고객은 애플리케이션 수준의 문제에 집중할 수 있으므로 인프라 운영을 Adobe에 집중할 수 있습니다.

## 유지 관리 작업 구성 {#maintenance-tasks-configuring}

이전 버전의 AEM에서는 유지 관리 카드( 도구 > 작업 > 유지 관리)를 사용하여 유지 관리 작업을 구성할 수 있습니다. AEM as a Cloud Service의 경우 유지 관리 카드를 더 이상 사용할 수 없으므로 Cloud Manager를 사용하여 소스 제어에 구성을 커밋하고 배포해야 합니다. Adobe은 고객이 구성할 수 없는 설정(예: 데이터 저장소 가비지 수집, 감사 로그 삭제, 버전 삭제)이 있는 유지 관리 작업을 관리합니다. 아래 표에 설명된 대로 기타 유지 관리 작업은 고객이 구성할 수 있습니다.

>[!CAUTION]
>
>Adobe은 성능 저하 등의 문제를 완화하기 위해 고객의 유지 관리 작업 구성 설정을 무시할 수 있는 권한을 갖습니다.

다음 표는 AEM as a Cloud Service 릴리스 시 사용할 수 있는 유지 관리 작업을 보여줍니다.

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>유지 관리 작업</th>
    <th>구성을 소유하는 사용자</th>
    <th>구성 방법(선택 사항)</th>
  </tr>  
  <tr>
    <td>데이터 저장소 가비지 수집</td>
    <td>Adobe</td>
    <td>해당 사항 없음 - 소유한 전체 Adobe</td>
  </td> 
  </tr>
  <tr>
    <td>버전 삭제</td>
    <td>Adobe</td>
    <td>작성 계층이 성능을 유지하려면 아래에 있는 각 컨텐츠 부분의 이전 버전을 <code>/content</code> 저장소의 노드는 다음 동작에 따라 제거됩니다.<br><br> <!--Alexandru: please leave the two line breaks in place, otherwise spacing won't render properly-->
     <ol>
       <li>30일 이전 버전이 제거됩니다</li>
       <li>최근 30일 동안 최신 5개 버전이 유지됩니다</li>
       <li>위의 규칙에 관계없이 최신 버전이 유지됩니다.</li>
     </ol><br>참고: 위에 설명된 동작은 2022년 3월 14일 이후에 생성된 새 환경에 대해 기본적으로 적용됩니다. 다른 설정이 필요한 경우 고객 지원 티켓을 제출하십시오.</td>
  </td>
  </tr>
  <tr>
    <td>감사 로그 삭제</td>
    <td>Adobe</td>
    <td>작성 계층이 성능을 유지하려면, <code>/content</code> 저장소의 노드는 다음 동작에 따라 제거됩니다.<br><br> <!-- See above for the two line breaks -->
     <ol>
       <li>복제 감사의 경우 3일 이상의 감사 로그가 제거됩니다</li>
       <li>DAM(자산) 감사의 경우 30일 이상의 감사 로그가 제거됩니다</li>
       <li>페이지 감사의 경우 3일 이상의 로그가 제거됩니다.</li>
     </ol><br>참고: 위에 설명된 동작은 2022년 3월 14일 이후에 생성된 새 환경에 대해 기본적으로 적용됩니다. 다른 설정이 필요한 경우 고객 지원 티켓을 제출하십시오.</td>
   </td>
  </tr>
  <tr>
    <td>Lucene 바이너리 정리</td>
    <td>Adobe</td>
    <td>사용하지 않으므로 Adobe에 의해 비활성화됩니다.</td>
  </td>
  </tr>
  <tr>
    <td>임시 작업 제거</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. 아래의 기본 제공 유지 관리 창 구성 노드 재정의 <code>/libs</code> 폴더 아래에 속성을 만들면 <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> 또는 <code>granite_daily</code>.</p>
    <p>추가 구성 세부 사항은 아래의 유지관리 창 테이블을 참조하십시오. 위의 노드 아래에 다른 노드를 추가하여 유지 관리 작업을 활성화합니다(이름을 지정합니다.) <code>granite_TaskPurgeTask</code>) 내의 아무 곳에나 삽입할 수 있습니다. OSGI 속성을 구성합니다.</p>
  </td>
  </tr>
    <tr>
    <td>워크플로우 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. 아래의 기본 제공 유지 관리 창 구성 노드 재정의 <code>/libs</code> 폴더 아래에 속성을 만들면 <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> 또는 <code>granite_daily</code>. 추가 구성 세부 사항은 아래의 유지관리 창 테이블을 참조하십시오.</p>
    <p>위의 노드 아래에 다른 노드를 추가하여 유지 관리 작업을 활성화합니다(이름을 지정합니다.) <code>granite_WorkflowPurgeTask</code>) 내의 아무 곳에나 삽입할 수 있습니다. OSGI 속성 구성 참조 <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html#regular-purging-of-workflow-instances">AEM 6.5 유지 관리 작업 설명서</a>.</p>
  </td>
  </tr>
  <tr>
    <td>프로젝트 삭제</td>
    <td>고객</td>
    <td>
    <p>git에서 수행해야 합니다. 아래의 기본 제공 유지 관리 창 구성 노드 재정의 <code>/libs</code> 폴더 아래에 속성을 만들면 <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> 또는 <code>granite_daily</code>. 추가 구성 세부 사항은 아래의 유지관리 창 테이블을 참조하십시오.</p>
    <p>위의 노드 아래에 다른 노드를 추가하여 유지 관리 작업을 활성화합니다(이름을 지정합니다.) <code>granite_ProjectPurgeTask</code>) 내의 아무 곳에나 삽입할 수 있습니다. OSGI 속성을 구성합니다.</p>
  </td>
  </tr>
  </tbody>
</table>

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>유지 관리 창 구성</th>
    <th>구성을 소유하는 사용자</th>
    <th>구성 유형</th>
    <th>매개변수</th>
  </tr>
  <tr>
    <td>일별</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
  <td>
  <p><strong>windowSchedule=daily</strong> (이 값은 변경할 수 없습니다.)</p>
  <p><strong>windowStartTime=HH:MM</strong> 를 24시간 시간으로 사용. 일별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</p>
  <p><strong>windowEndTime=HH:MM</strong> 를 24시간 시간으로 사용. 일별 유지 관리 창과 연관된 유지 관리 작업이 아직 완료되지 않은 경우 실행을 중지해야 하는 시기를 정의합니다.</p>
  </td> 
  </tr>
  <tr>
    <td>매주</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=weekly</strong> (이 값은 변경할 수 없습니다.)</p>
    <p><strong>windowStartTime=HH:MM</strong> 를 24시간 시간으로 사용. 주별 유지 관리 기간과 연관된 유지 관리 작업 실행 시기를 정의합니다.</p>
    <p><strong>windowEndTime=HH:MM</strong> 를 24시간 시간으로 사용. 아직 완료되지 않은 경우 주간 유지 관리 창과 연관된 유지 관리 작업이 실행을 중지해야 하는 시기를 정의합니다.</p>
    <p><strong>windowScheduleWeekle= 1-7에서 2개의 값 배열(예: [5,5])</strong> 배열의 첫 번째 값은 작업이 예약되는 시작일이고 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 각각 windowStartTime 및 windowEndTime에 의해 제어됩니다.</p>
    </td>
  </tr>
  <tr>
    <td>매월</td>
    <td>고객</td>
    <td>JCR 노드 정의</td>
    <td>
    <p><strong>windowSchedule=daily</strong> (이 값은 변경할 수 없습니다.)</p>
    <p><strong>windowStartTime=HH:MM</strong> 를 24시간 시간으로 사용. 월별 유지 관리 창과 연관된 유지 관리 작업의 실행을 시작하는 시기를 정의합니다.</p>
    <p><strong>windowEndTime=HH:MM</strong> 를 24시간 시간으로 사용. 아직 완료되지 않은 경우 월별 유지 관리 창과 연관된 유지 관리 작업이 실행을 중지해야 하는 시기를 정의합니다.</p>
    <p><strong>windowScheduleWeekle=1-7에서 2개 값의 배열(예: [5,5])</strong> 배열의 첫 번째 값은 작업이 예약되는 시작일이고 두 번째 값은 작업이 중지되는 종료일입니다. 시작 및 종료의 정확한 시간은 각각 windowStartTime 및 windowEndTime에 의해 제어됩니다.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0 을 클릭하여 해당 월의 첫 번째 주 또는 1에서 해당 월의 마지막 주에 예약합니다. 값이 없을 경우, 매달 windowScheduleWeekday에 의해 관리되는 방식으로 매일 일자리를 예약할 수 있습니다.</p>
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
