---
title: Edge Delivery Services Forms에 대한 실시간 사용자 모니터링
description: Forms Edge Delivery Services에 대한 실시간 사용자 모니터링에는 양식과의 사용자 상호 작용에 대한 지속적인 추적 및 분석이 포함됩니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Edge Delivery Services Forms에 대한 실시간 사용자 모니터링

Adobe Experience Manager은 RUM(Real User Monitoring)을 사용하여 Adobe Experience Manager 기반 사이트와의 방문자 상호 작용을 이해합니다. 성능 문제를 진단하고 실험 효과를 평가하는 데 도움이 됩니다. 실제 사용자 모니터링은 샘플링 기법을 사용하여 방문자의 개인 정보를 유지하므로 방문 중인 사이트에서 개인 정보가 수집되지 않도록 합니다. 개인 데이터를 RUM 데이터 수집에 추가하는 것은 허용되지 않습니다. Adobe Experience Manager의 Real User Monitoring은 방문자 개인 정보를 보존하고 데이터 수집을 최소화하도록 설계되었습니다.

## Edge Delivery Services Forms에 대한 실시간 사용자 모니터링 사용의 이점 {#advantages}

AEM은 다음에 대해 실시간 사용자 모니터링을 사용합니다.

* 사이트의 성능 병목 현상을 파악 및 해결하기 위해
* 고객 사이트에 대한 페이지 보기 수를 예측하려면
* 동일한 페이지에서 Adobe Experience Manager과 분석, 타기팅 또는 외부 라이브러리의 상호 작용을 이해하여 호환성을 향상합니다.

## 전제 조건

다음 URL에 액세스하여 Edge Delivery Services Forms에 대한 실시간 사용자 모니터링 대시보드를 볼 수 있습니다. https://data.aem.live/?ext=forms

![Edge Delivery Services Forms의 RUM 로그인 화면 ](/help/edge/assets/rum-login-screen.png)

Edge Delivery Services Forms의 실시간 사용자 모니터링 대시보드에 로그인하려면 다음을 입력합니다.
* **URL**: URL은 사용자 사이트 또는 도메인에 따라 다릅니다. 사용자는 요구 사항에 따라 대시보드를 보기 위해 사이트 또는 도메인을 필터링할 수 있습니다.
* **도메인 키**: 사용자가 도메인 키를 수동으로 생성합니다. 지원 또는 문의 사항은 다음을 참조하십시오. [RUM 도메인 키 생성](https://aemcs-workspace.adobe.com/rum/generate-domain-key) 설명서를 참조하십시오.

### Edge Delivery Services Forms에 대한 실시간 사용자 모니터링 대시보드

로그인 화면에 URL 및 도메인 키를 입력하면 Edge Delivery Services Forms에 대한 실시간 사용자 모니터링 대시보드에 액세스할 수 있습니다.

아래 그림은 Edge Delivery Services Forms용 RUM 대시보드를 보여줍니다.

![RUM Forms 대시보드](/help/edge/assets/rum-forms-dashboard.png)

### Forms용 RUM 대시보드의 다양한 주요 지표 {#different-metrics-rum-dashboard-forms}

다음 주요 지표를 사용하여 Adobe Experience Manager 기반 사이트와의 방문자 상호 작용을 평가할 수 있습니다.

* **양식 보기**: 지정된 날짜 범위 내 URL에 대해 렌더링된 총 양식 수입니다.
* **Formsubmission**: 지정된 날짜 범위 내에 있는 URL에 대해 제출된 총 양식 수입니다.
* **가장 큰 내용 페인트**: URL이 로드되는 속도를 보여주며 사용자가 URL을 요청하는 순간부터 뷰포트에 표시되는 가장 큰 콘텐츠 요소를 렌더링하는 데 걸리는 시간을 나타냅니다. 이 가장 큰 콘텐츠 요소는 이미지, 비디오 또는 실질적인 블록 수준의 텍스트 요소일 수 있습니다. URL 로드 속도에 대한 성능 등급은 다음과 같이 분류됩니다.
   * **양호**: 로드 시간이 2.5초 이하인 경우.
   * **확인**: 로드 시간이 2.5초 초과 4초 이하인 경우.
   * **나쁨**: 로드 시간이 4초를 초과하는 경우

* **누적 레이아웃 이동**: 페이지의 전체 수명 동안 발생하는 각 예기치 않은 레이아웃 이동에 대한 모든 개별 레이아웃 이동 점수의 총 합계를 측정합니다. 사용자가 페이지 요소와 상호 작용하려고 할 때 페이지 요소가 변경되면 사용자 환경이 나빠 페이지 성능을 식별하는 데 중요한 역할을 합니다. 이 점수의 범위는 0부터 임의의 양수까지입니다. 0은 이동이 없음을 나타내며, 숫자가 높을수록 페이지에서 더 많은 레이아웃 이동이 있음을 나타냅니다. 레이아웃 이동 점수를 평가하는 데 사용되는 성과 지표는 다음과 같이 분류됩니다.

   * **양호**: 레이아웃 전환 점수가 0.1 이하인 경우.
   * **확인**: 레이아웃 전환 점수가 0.1보다 크고 0.25 이하인 경우.
   * **나쁨**: 레이아웃 이동 점수가 0.25를 초과하는 경우.

* **다음 페인트에 대한 상호 작용**: 사용자가 페이지를 방문하는 동안 페이지가 클릭, 탭 및 키보드 입력에 응답하는 데 걸리는 시간을 고려하여 페이지가 사용자 상호 작용에 얼마나 빠르게 반응하는지 평가합니다. 최종 값은 어떤 예외 사항도 무시한 채 관찰된 가장 긴 상호 작용이다. 다음 페인트에 대한 상호 작용에 대한 성능 지표는 다음과 같이 분류됩니다.
   * **양호**: 사용자 작업 간의 지속 시간이 200밀리초(밀리초) 이하인 경우.
   * **확인**: 지속 시간이 200밀리초를 초과하고 500밀리초 이하인 경우
   * **나쁨**: 지속 시간이 500밀리초를 초과하는 경우.

