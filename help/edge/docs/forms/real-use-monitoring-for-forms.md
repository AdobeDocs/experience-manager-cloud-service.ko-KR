---
title: AEM Forms as a Cloud Service Edge Delivery Services에 대한 RUM(Real Use Monitoring)
description: AEM Forms as a Cloud Service용 Edge Delivery Services에 대한 RUM(Real Use Monitoring)에는 양식과의 사용자 상호 작용에 대한 지속적인 추적 및 분석이 포함됩니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 6c56f753d2a32de6fe11fd47843cee5bcb8cac4e
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 45%

---


# AEM Forms as a Cloud Service Edge Delivery Services에 대한 RUM(Real Use Monitoring)

RUM(Real Use Monitoring)은 방문자가 AEM(Adobe Experience Manager) 웹 사이트와 상호 작용하는 방법에 대한 실제 통찰력을 얻을 수 있도록 해줍니다. 이 기본 제공 도구는 사용자 행동을 이해하고, 성능 문제를 진단하고, 웹 사이트 실험의 효과를 측정하는 데 유용한 데이터를 제공합니다. RUM은 실제 사용 상호 작용을 캡처하여 합성 테스트를 넘어 사이트 성능에 대한 보다 정확한 그림을 제공합니다.

단, RUM은 방문자 개인 정보 보호를 우선시합니다. 샘플링 기술을 사용하여 사용자의 대표적인 하위 집합에서 데이터를 수집하므로 PII(개인 식별 정보)가 캡처되지 않습니다. 또한 RUM은 성능 분석에 필요한 필수 지표만 수집하면서 데이터 최소화를 염두에 두고 설계되었습니다. 이 접근 방식을 사용하면 사용자의 신뢰를 유지하면서 AEM 사이트를 최적화할 수 있습니다.


## 전제 조건

다음 URL에 액세스하여 AEM Forms as a Cloud Service용 Edge Delivery Services 모니터링 대시보드를 볼 수 있습니다.

https://data.aem.live/?ext=forms

![Forms Edge Delivery Services의 RUM 로그인 화면](/help/edge/assets/rum-login-screen.png)

AEM Forms as a Cloud Service Edge Delivery Services 모니터링 대시보드에 로그인하려면 다음을 입력합니다.

* **URL**: URL은 사용자 사이트 또는 도메인에 따라 다릅니다. 사용자는 사이트 또는 도메인을 필터링하여 요구 사항에 따라 대시보드를 볼 수 있습니다.

* **도메인 키**: 사용자가 도메인 키를 수동으로 생성합니다. 양식에 대한 도메인 키를 얻으려면 Adobe 담당자에게 문의하십시오.

### AEM Forms as a Cloud Service Edge Delivery Services 대시보드 모니터링

로그인 화면에 URL 및 도메인 키를 입력하면 AEM Forms as a Cloud Service에 대한 Edge Delivery Services 모니터링 대시보드에 액세스할 수 있습니다.

아래 그림은 AEM Forms as a Cloud Service용 Edge Delivery Services 대시보드를 보여줍니다.

![RUM 양식 대시보드](/help/edge/assets/rum-forms-dashboard.png)

### Forms용 대시보드의 다양한 주요 지표 {#different-metrics-rum-dashboard-forms}

이 대시보드는 방문자가 Adobe Experience Manager(AEM) 웹 사이트의 양식과 상호 작용하는 방법에 대한 주요 통찰력을 제공합니다. 이러한 지표를 모니터링하여 개선할 영역을 식별하고 사용자 경험과 전환율을 향상시키기 위해 양식을 최적화할 수 있습니다.

* **양식 보기**: 양식의 총 표시 횟수를 추적합니다
* **양식 제출**: 완료된 총 제출 수 추적

* **최대 콘텐츠풀 페인트**: URL이 로드되는 속도를 표시하며, 이는 사용자가 URL을 요청하는 순간부터 뷰포트에 표시되는 최대 콘텐츠 요소를 렌더링하는 데 걸린 시간을 나타냅니다. 가장 큰 콘텐츠 요소는 이미지, 비디오 또는 상당한 블록 수준의 텍스트 요소일 수 있습니다. URL 로딩 속도에 대한 성능 등급은 다음과 같이 분류됩니다.
   * **좋음**: 로딩 시간이 2.5초 이하인 경우
   * **양호**: 로딩 시간이 2.5초를 초과하고 4초 이하인 경우
   * **좋지 않음**: 로딩 시간이 4초를 초과하는 경우

* **누적 레이아웃 이동**: 페이지의 전체 수명 동안 발생하는 예상치 못한 각 레이아웃 이동에 대한 모든 개별 레이아웃 이동 점수의 총합을 측정합니다. 사용자가 상호 작용을 시도하는 동안 페이지 요소가 이동하면 사용자 경험이 저하되므로, 페이지 성능을 확인하는 데 중요한 역할을 합니다. 이 점수 범위는 0부터 양수까지입니다. 0은 이동이 없음을 나타내고 숫자가 높을수록 페이지에서 레이아웃이 더 많이 이동했음을 의미합니다. 레이아웃 이동 점수를 평가하는 데 사용되는 성능 지표는 다음과 같이 분류됩니다.

   * **좋음**: 레이아웃 이동 점수가 0.1 이하인 경우
   * **양호**: 레이아웃 이동 점수가 0.1을 초과하고 0.25 이하인 경우
   * **좋지 않음**: 레이아웃 이동 점수가 0.25를 초과하는 경우

* **다음 페인트에 대한 상호 작용**: 사용자가 페이지를 방문하는 동안 페이지가 클릭, 탭 및 키보드 입력에 응답하는 데 걸리는 시간을 고려하여 페이지가 사용자 상호 작용에 대해 얼마나 빨리 반응하는지 평가합니다. 최종 값은 예외 항목을 무시하고 관찰된 가장 긴 상호 작용입니다. 다음 페인트에 대한 상호 작용의 성능 지표는 다음과 같이 분류됩니다.
   * **양호**: 사용자 작업 간의 지속 시간이 200밀리초(ms) 이하인 경우
   * **양호**: 지속 시간이 200ms를 초과하고 500ms 이하인 경우
   * **좋지 않음**: 지속 시간이 500ms를 초과하는 경우

## 실행 가능한 인사이트

이러한 지표를 분석하여 다음과 같은 기회를 식별할 수 있습니다.

* 양식을 단순화하고 필드 수를 줄입니다.
* 명확한 지침과 레이블로 양식 명확성을 개선합니다.
* 모바일 응답성을 위해 양식 레이아웃을 최적화합니다.
* 양식 로드 속도를 저하시키는 기술 문제를 해결하십시오.

이러한 영역에 초점을 맞춰 사용하기 쉬운 양식을 만들고 방문자가 이를 완료하도록 유도할 수 있으므로 궁극적으로 전환율이 높아집니다.

## 추가 참조

{{see-more-forms-eds}}