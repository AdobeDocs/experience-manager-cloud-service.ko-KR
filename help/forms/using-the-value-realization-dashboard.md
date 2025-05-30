---
title: 값 실현 대시보드를 사용하여 양식 및 문서 사용 트렌드 분석
description: Forms 사용 인사이트 대시보드를 사용하여 양식 및 양식 조각의 성능을 모니터링하고 이해하는 방법에 대해 알아봅니다.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components, Core Components
hide: true
hidefromtoc: true
source-git-commit: 09d383638d6caba596d22a7c6b544768de5245a0
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 1%

---

# 값 실현 대시보드를 사용하여 양식 및 문서 사용 트렌드 분석

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스 권한을 요청하려면 공식 주소에서 aem-forms-ea@adobe.com으로 이메일을 보내십시오. <span>

![값 실현 대시보드](/help/edge/docs/forms/universal-editor/assets/forms-insights-banner.svg)

&quot;Forms 사용 인사이트&quot; 대시보드에 표시된 지표를 정기적으로 모니터링하면 양식, 문서 및 양식 조각의 성능에 대한 중요한 인사이트를 얻을 수 있습니다. 이 데이터를 사용하여 양식 디자인, 조각 관리 및 전체 양식 전략에 대한 정보에 입각한 결정을 내릴 수 있습니다.

이 문서에서는 가치 실현 대시보드에 대한 자세한 사용 지침 및 지표 해석을 제공합니다. 대시보드의 개념적 개요 및 이점은 [가치 실현 대시보드 이해](/help/forms/aem-forms-value-realization-dashboard.md)를 참조하십시오.


## 사용 통찰력 대시보드 액세스

Forms 사용 통찰력 대시보드에 액세스하려면:

1. **Forms** > **Forms 및 문서**(으)로 이동
1. **제품 내 대시보드**&#x200B;를 클릭합니다. 대시보드가 새 창에 열립니다.

   ![값 실현 대시보드](/help/forms/assets/forms-usage-insights.png)

## 개요

대시보드는 다음 두 가지 기본 섹션으로 구성됩니다.

- **시간에 따른 양식 및 문서 활동:** 이 섹션에서는 선택한 기간 동안의 양식 사용 및 발전에 대한 통찰력을 제공합니다.
- **조각 사용:** 이 섹션에서 양식 조각의 채택 및 재사용을 모니터링할 수 있습니다.

## 시간에 따른 양식 및 문서 활동

이 섹션에는 4개의 차트가 포함되어 있으며 각 차트는 양식 활동의 다른 측면을 추적합니다. 모든 차트는 동일한 구조를 공유합니다.

- **차트 종류:** 선 차트 및 막대 차트
- **X축:** 날짜(일일 활동 표시)
- **Y축:** 수(추적된 활동의 발생 횟수를 나타냄)
- **기간:** 드롭다운 메뉴를 통해 조정 가능(옵션: &quot;최근 30일&quot;, &quot;최근 12개월&quot;)




### 양식 제출

- **목적:** 이 차트에는 선택한 기간 동안 양식이 성공적으로 제출된 횟수가 표시됩니다.

  ![Forms 제출 차트](/help/forms/assets/forms-submissions-vr-dashboard-form-insights.png)
- **추출할 정보:**
   - **트렌드 분석:** 양식 제출의 전반적인 트렌드를 확인합니다. 그 수가 증가, 감소, 혹은 비교적 일정하게 유지되는가?
   - **최대 기간:** 제출률이 비정상적으로 높은 일 또는 기간을 식별합니다. 이러한 스파이크에 대한 가능한 이유를 조사합니다(예: 마케팅 캠페인, 특정 이벤트).
   - **낮은 활동 기간:** 제출률이 낮은 기간을 식별하고 잠재적 원인(예: 양식 다운타임, 사용성 문제)을 조사합니다.
   - **비교 분석:** 서로 다른 기간(예: 지난 30일과 이전 30일)에 대한 제출률을 비교하여 성능 변화를 평가합니다.

### 문서 표현물

- **목적:** 이 차트는 양식 제출 결과로 생성된 문서 수를 추적합니다. 이는 양식이 문서(예: 계약, 보고서) 생성을 트리거하는 경우와 관련이 있습니다.

  ![문서 렌더링 차트](/help/forms/assets/document-rendetions-vr-dashboard-form-insights.png)


- **추출할 정보:**
   - **양식 제출과 상관 관계:** 문서 표현물의 트렌드를 양식 제출의 트렌드와 비교합니다. 이상적으로, 이것들은 밀접하게 연관되어야 한다. 불일치는 문서 생성 프로세스에 문제가 있음을 나타낼 수 있습니다.
   - **문서 생성 볼륨:** 생성 중인 문서의 전체 볼륨을 평가하여 문서 생성 시스템의 워크로드를 파악합니다.

### 작성된 양식


- **목적:** 이 차트에는 선택한 기간 내에 만든 새 양식의 수가 표시됩니다.

  ![Forms이 차트를 만들었습니다](/help/forms/assets/forms-created-vr-dashboard-form-insights.png)

- **추출할 정보:**
   - **양식 만들기 속도:** 새 양식을 만드는 속도를 추적합니다. 조직 내 새 양식에 대한 수요에 대한 통찰력을 제공합니다.
   - **생성 스파이크:** 양식 생성 활동이 비정상적으로 높은 기간을 식별합니다. 이는 새로운 양식이 필요한 특정 프로젝트 또는 이니셔티브를 나타낼 수 있습니다.

### Forms 게시됨

- **목적:** 이 차트는 선택한 기간 내에 게시(사용 가능)된 양식 수를 추적합니다.

  ![Forms에 게시된 차트](/help/forms/assets/forms-publish-vr-dashboard-form-insights.png)


- **추출할 정보:**
   - **양식 배포 비율:** 사용자에게 새 양식을 배포하는 비율을 모니터링합니다.
   - **만들기와 게시 사이의 지연:** &quot;Forms이 만들어짐&quot; 차트와 &quot;Forms이 게시됨&quot; 차트 사이의 시간 차이를 분석합니다. 양식 승인 또는 배포 프로세스에 병목 현상이 발생할 수 있습니다.

## 조각 사용

이 섹션에서는 여러 양식에 통합할 수 있는 재사용 가능한 구성 요소인 양식 조각의 사용에 대한 통찰력을 제공합니다.

![Forms에 게시된 차트](/help/forms/assets/fragment-usage-vr-dashboard-form-insights.png)

### 사용 중인 양식 조각 수

- **차트 종류:** 숫자 표시(단일 값 표시)
- **목적:** 현재 활성 양식에서 사용 중인 고유한 총 양식 조각 수를 표시합니다.
- **추출할 정보:**
   - **조각 채택:** 조직 내 양식 조각의 전체 채택 여부를 평가합니다. 숫자가 높을수록 재사용 가능한 구성 요소의 사용이 증가함을 나타냅니다.

### 양식 조각 재사용

- **차트 종류:** 숫자 표시(단일 값 표시)
- **목적:** 다른 양식에서 양식 단편을 다시 사용한 총 횟수를 표시합니다. 이 지표는 중복을 방지하고 일관성을 유지하기 위해 조각을 얼마나 효과적으로 활용하는지를 나타냅니다.
- **추출할 정보:**
   - **조각 재사용 비율:** 기존 조각이 새 양식에서 재사용되는 비율을 모니터링합니다. 이 수치가 높을수록 재사용 가능한 구성 요소의 활용도가 높아지고 효율성이 향상됩니다.

## 예제 시나리오

- **시나리오:** &quot;양식 제출&quot;이 갑자기 줄어든 것을 발견했습니다.
   - **작업:** 양식 다운타임, 사용 가능성 문제 또는 양식의 랜딩 페이지 트래픽 감소와 같은 잠재적 원인을 조사합니다.
- **시나리오:** &quot;양식 조각 재사용&quot; 값이 낮습니다.
   - **작업:** 양식 조각을 사용하여 얻을 수 있는 이점을 팀에 홍보하고, 조각이 잘 구성되어 있고 쉽게 찾을 수 있도록 하며, 조각을 효과적으로 만들고 재사용하는 방법에 대한 교육을 제공합니다.
- **시나리오:** &quot;Forms 생성됨&quot;과 &quot;Forms 게시됨&quot; 사이에 상당한 차이가 있습니다.
   - **작업:** 양식 승인 및 배포 프로세스를 검토하여 병목 현상을 식별하고 제거하십시오.



## 추가 참조

- [가치 실현 대시보드 이해](/help/forms/aem-forms-value-realization-dashboard.md)
