---
title: 적응형 양식 분석 보고서 보기 및 이해
description: 적응형 양식은 Adobe Analytics와 원활하게 통합되어 게시된 양식 및 문서에 대한 성능 지표를 캡처하고 추적합니다.
keywords: 적응형 Forms 분석 보고서, Adobe 분석 보고서, Forms 분석 보고서 보기 및 이해
topic-tags: develop
feature: Adaptive Forms
role: Admin, User
level: Intermediate
exl-id: 756dee1f-4685-4783-961d-b172a5bd0692
source-git-commit: 975f767e75a268a1638227ae20a533f82724c80a
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 97%

---

# 적응형 양식 분석 보고서 보기 및 이해 {#viewing-and-understanding-aem-forms-analytics-reports}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM as a Cloud Service | 이 문서 |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html) |

빠르게 변화하는 디지털 분석 환경에서 정보에 입각한 결정을 내리고 디지털 경험을 최적화하려면 지속적으로 글로벌 트렌드에 적응해야 합니다. 문제 해결을 위해 적응형 양식은 Adobe Analytics와 원활하게 통합되어 게시된 양식 및 문서에 대한 성능 지표를 캡처하고 추적합니다. 이러한 지표를 분석하는 목적은 양식의 유용성과 효율성을 높일 수 있는 지표 및 분석을 사용하여 데이터를 기반으로 정보에 입각한 결정을 내리는 것입니다.

주요 성과 지표를 포착 및 추적함으로써 기업은 개선 가능한 영역을 식별하고, 사용자 경험을 최적화하고, 궁극적으로 더 나은 결과를 도출하여 예외적인 고객 경험을 만들 수 있습니다.

## 적응형 양식에 Adobe Analytics 설정 {#setup-adobe-analytics-to-aem-forms}

AEM Forms Analytics 보고서의 경우 Experience Cloud 설정 자동화를 통해 먼저 Adobe Analytics를 AEM Forms에 통합합니다. 데이터 집계 및 인사이트 생성 간소화를 위해 추적 스크립트와 Experience Platform Launch API와의 통합 기능을 관리하려면 적응형 양식의 Experience Cloud 설정 자동화에 Adobe Analytics 라이선스, 데이터 수집(이전 명칭 Adobe Launch)이 필요합니다. 전체 설정 정보를 보려면 [Experience Cloud 설정 자동화를 통해 적응형 양식용 Adobe Analytics를 사용할 수 있도록 설정](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md)을 참조하십시오.

## 적응형 양식 Adobe Analytics 보고서 보기 {#view-adobe-analytics-report}

1. AEM 인스턴스에서 **[!UICONTROL Forms]** >> **[!UICONTROL 양식 및 문서]**&#x200B;로 이동합니다.
1. 양식을 선택하면 왼쪽에 표시된 대로 Adobe Analytics가 Adobe Analytics에 활성화된 양식에 통합됩니다.

   ![보고서 보기](assets/activ-aa.png){width="100%"}

1. **Adobe Analytics**&#x200B;를 클릭하여 보고서를 보고 성능 데이터를 분석합니다.

## 적응형 양식 분석 보고서 이해 {#understanding-aem-forms-analytics-reports}

Adobe Analytics는 양식 사용에 대한 중요한 인사이트 확보를 위해 설계된 포괄적인 적응형 양식 성능 지표를 제공합니다. 해당 지표는 다음과 같습니다.

### **적응형 양식의 성과는 어떻습니까?** {#how-your-adaptive-form-is-performing}

지표 양식 렌디션, 양식 제출, 유효성 검사 오류와 고유 방문자 수를 사용하여 양식의 사용량과 효율성을 평가할 수 있습니다.

* **양식 렌디션**: 양식 렌디션에 양식이 렌더링되거나 열린 횟수가 표시됩니다.

* **양식 제출**: 양식 제출은 사용자가 적응형 양식을 작성하고 제출한 횟수를 나타냅니다.

* **유효성 검사 오류**: 유효성 검사 오류는 양식 필드에 발생한 유효성 검사 관련 총 오류 수를 표시합니다.

* **고유 방문자 수**: 고유 방문자 수는 방문자가 양식을 렌더링한 횟수를 나타냅니다. 고유 방문자 수에 대한 자세한 내용은 [고유 방문자 수, 방문자 수와 고객 행동](https://experienceleague.adobe.com/docs/analytics/components/metrics/visits.html)을 참조하십시오.

  ![양식 성능](assets/forms-performance.png){width="100%"}

### **양식 방문자 수** {#visitors-to-your-forms}

이를 통해 양식의 방문자 활동에 대한 중요한 인사이트를 확보할 수 있습니다.

* **방문 및 제출 수**: 날짜 범위 내 양식 방문 빈도와 해당 양식 제출 횟수에 대해 설명합니다. 이 대한 자세한 내용은 [방문](https://experienceleague.adobe.com/docs/analytics/components/metrics/visits.html)을 클릭합니다.
* **고유 방문자 수 및 총 방문 수**: 새 사용자와 재방문 사용자를 구분합니다. 예를 들어 방문자는 한 달 동안 매일 사이트를 방문할 수 있지만 여전히 하나의 고유 방문자로 계산됩니다. 자세한 내용은 [고유 방문자 수](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html)를 참조하십시오.

  ![양식 방문자 수](assets/forms-visitors.png){width="100%"}

### **디바이스 유형** {#device-type}

디바이스 유형은 양식에 액세스하는 데 사용되는 디바이스 유형을 식별하는 데 도움이 됩니다. 디바이스 유형을 모바일 디바이스 유형으로 분류합니다. 예를 들어 이 경우는 모바일 디바이스 유형이고, 다른 경우는 모바일 디바이스 유형, 휴대폰입니다. 휴대폰, 태블릿, 미디어 플레이어, 게임 콘솔 등 다양한 유형의 모바일 디바이스가 있습니다.

![디바이스 유형](assets/device-type.png){width="100%"}

### **지리적 분류** {#geographical-breakdown}

양식에 액세스하는 위치를 보여 줍니다. 양식 사용자에 대한 지역별 정보를 제공합니다. 예: 이미지에 표시된 대로 양식 사용자에 대한 지역별 정보가 인도임을 확인할 수 있습니다.

![지리적 분류](assets/geographical-breakdown.png){width="100%"}

### **트래픽의 주요 소스 및 방문 빈도가 높은 양식** {#top-sources-of-traffic-and-popular-forms}

이렇게 하면 양식을 참조하는 기본 소스 또는 링크를 식별할 수 있습니다. 예를 들어 아래 주어진 이미지에 18.9%는 **입력/책갈피 표시**&#x200B;이고, 70.49%는 **검색 엔진**&#x200B;을 기준으로 하고, 24%는 **기타 웹 사이트**&#x200B;에 있는 적응형 양식용 검색 인스턴스가 표시됩니다. 요구 사항에 따라 차원 항목을 정의할 수 있습니다. 또한 가장 많이 방문한 양식이나 방문 빈도가 높은 양식을 정렬할 수 있습니다.

![추천한 사이트](assets/referred-sites.png){width="100%"}

### **상위 양식의 사용자 활동** {#user-activity-on-top-forms}

사용자가 이용하는 필드 방문, 양식 렌디션, 유효성 검사 오류, 포기한 양식, 양식 제출 등에 대한 포괄적인 보기를 통해 가장 많이 방문한 양식에 대한 인사이트를 확보합니다. 아래 주어진 이미지에서 알 수 있듯이 양식 이벤트 지표를 기준으로 신청서 양식을 가장 많이 방문합니다.

![사용자 활동](assets/user-activity.png){width="100%"}

### **양식 작성에 사용된 시간의 타임라인** {#timeline-for-time-spent-on-forms}

시간 경과에 따라 양식 작성에 사용한 시간으로 이용 패턴을 식별하는 데 도움이 됩니다.

![양식 작성에 사용한 시간](assets/time-spent-on-forms.png){width="100%"}

### **방문자가 양식 작성 시 도움을 받을 수 있는 영역** {#areas-requiring-assistance}

도움말 보기, 유효성 검사 오류, 필드 방문과 같은 지표에 사용자가 도움이 필요한 영역이나 필드의 오류를 추적할 수 있는 방법이 표시됩니다. 예를 들어 아래 이미지에서 **전체 이름**, **전화번호**, **DoB**&#x200B;와 같은 필드가 있는 양식에서 이를 확인합니다. **전체 이름** 필드에 12회 방문하고 12회 방문 중 8회에는 유효성 검사 오류가 있으며, 이 필드에서 도움말을 보려면 도움말 아이콘을 1회 클릭합니다. 다른 양식 필드의 지표 데이터를 볼 수 있습니다.

![도움 영역](assets/assisting-areas.png){width="100%"}

### **방문자가 양식을 포기하기 전 마지막으로 본 양식 필드** {#last-form-field-that-visitors-viewed}

이를 통해 사용자는 양식을 포기하기 전 시간을 보낸 양식 필드를 분석할 수 있습니다. 예를 들어 아래 이미지에서 알 수 있듯이 포기한 양식 5개 중 2개는 **전체 이름** 필드에 남고, 2개는 **전화번호** 필드에 남고, 나머지 1개는 **텍스트 입력**&#x200B;에 남게 됩니다.

![필드 방문자](assets/field-visitors.png){width="100%"}

## 추가 참조 {#see-also}

* [Experience Cloud 설정 자동화를 사용하여 적응형 양식용 Adobe Analytics 활성화](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md)
* [AEM Sites 페이지 또는 경험 조각에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [AEM Forms과 Adobe Analytics 통합](/help/forms/integrate-aem-forms-with-adobe-analytics.md)
