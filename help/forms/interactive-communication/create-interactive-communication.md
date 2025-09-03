---
title: 대화형 통신 만들기
description: 개인화된 데이터 기반 커뮤니케이션을 만듭니다. 안내서와 튜토리얼을 통해 주요 기능, 온보딩 단계 및 실제 사용 사례를 살펴보십시오.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: 764cfbbcb8efd407cff85bfc24928aa3f8e5e956
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 4%

---

# 대화형 통신 만들기

>[!NOTE]
>
> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 주소에서 `aem-forms-ea@adobe.com`(으)로 전자 메일을 보내십시오.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. Forms Experience Builder가 얼리어답터 프로그램 동안 계속 발전함에 따라 프롬프트, 예 및 우수 사례가 변경될 수 있습니다.

대화형 커뮤니케이션을 사용하면 고객 서비스, 청구, 온보딩 문서, 제안서, 계정 업데이트 등을 포함하여 개인화되고 대화형 커뮤니케이션을 만들고, 관리하고, 제공할 수 있습니다. 동적인 사용자별 컨텐츠가 업계 전반에 걸쳐 통신 경험을 향상시키는 모든 시나리오를 지원하도록 설계되었습니다.

수천 명의 고객에게 은행 거래 명세서, 보험 증권 또는 공과금 고지서를 보내야 한다고 상상해 보십시오. 각 속성에는 레이아웃은 동일하지만 개인화된 데이터가 있습니다. 대화형 통신(IC)을 통해 이를 효율적으로 수행할 수 있습니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/introimg.png)

이러한 문서를 수동으로 작성하는 것은 시간이 많이 소요될 수 있으며 특히 개인화 및 데이터 통합이 필요한 경우 종종 불일치가 발생할 수 있습니다. 대화형 통신 편집기를 사용하면 대화형 통신을 만드는 프로세스를 간소화할 수 있습니다.

## 전제 조건

* [작성자가 forms-users 그룹의 구성원인지 확인합니다.](/help/forms/setup-forms-cloud-service.md#configure-users)

## 대화형 통신 만들기

필요한 재사용 및 데이터 통합 수준에 따라 대화형 통신을 만들려면 다양한 시나리오 중에서 선택하십시오.

+++ 빈 대화형 통신 만들기

빈 대화형 커뮤니케이션을 만들면 레이아웃, 구조 및 논리를 완전히 제어하려는 경우 처음부터 시작할 수 있습니다.
따라야 할 단계:

1. **Adobe Experience Manager(AEM) Forms as a Cloud Service 인스턴스를 엽니다**.
1. **Forms > Forms 및 문서**(으)로 이동합니다.
1. **만들기 > 대화형 통신**&#x200B;을 클릭합니다.

   ![IC 문서 찾기](/help/forms/interactive-communication/assets/comm.png)

1. 만들기 화면에서 **템플릿** 필드를 비워 둡니다.

   ![IC 문서 찾기](/help/forms/interactive-communication/assets/create-ic-document.png)

1. 제목, 이름, 작성자 등 기타 세부 정보를 입력합니다.
1. 대화형 통신 편집기 UI를 입력하고 디자인을 시작하려면 **만들기**&#x200B;를 클릭하세요.
1. IC 편집기가 열리고 여기서 통신 디자인을 시작할 수 있습니다.
+++

+++ 템플릿 기반 대화형 통신 만들기

템플릿을 사용하면 머리글, 바닥글, 로고 또는 표준 서식과 같은 일관된 레이아웃 요소를 재사용하여 디자인 속도를 높일 수 있습니다.
템플릿은 브랜드 일관성을 보장하며 일반적으로 사용되는 통신 유형에 대한 시간을 절약합니다. 아래 단계를 수행합니다.

1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
1. **Forms > Forms 및 문서**(으)로 이동하여 **만들기 > 대화형 통신**&#x200B;을 클릭합니다.
1. 만들기 양식의 드롭다운에서 활성화된 템플릿을 **선택**&#x200B;합니다.
1. 제목, 이름, 작성자 등 기타 세부 정보를 입력합니다.
1. 선택한 템플릿 구조와의 통신을 디자인하려면 **만들기**&#x200B;를 클릭하세요.
1. IC 편집기가 열리고 여기서 통신 디자인을 시작할 수 있습니다.
+++

+++ 데이터가 상호 작용하는 대화형 통신 만들기

데이터 상호 작용 커뮤니케이션은 백엔드 데이터를 사용하여 컨텐츠를 자동으로 개인화합니다.
구조가 일정하게 유지되지만 수신자마다 데이터가 다른 명세서, 청구서 또는 통지에 이상적입니다. 따라야 할 단계:

1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
1. **Forms > Forms 및 문서**(으)로 이동하여 **만들기 > 대화형 통신**&#x200B;을 클릭합니다.
1. **양식 데이터 모델** 필드에서 미리 정의된 **FDM(양식 데이터 모델)**&#x200B;을 연결합니다.
1. 제목, 이름, 작성자 등 기타 세부 정보를 입력합니다.
1. 편집기 내의 **데이터 모델**&#x200B;을(를) 사용하여 필드를 동적 데이터(예: 고객 이름, 계좌 번호)에 바인딩하십시오.
1. 필요한 경우 **콘텐츠 영역, 하위 양식** 및 **조각**&#x200B;을 사용하여 데이터를 구조화하고 반복하십시오.
1. **PDF 미리 보기**&#x200B;를 사용하여 미리 보고 게재할 커뮤니케이션을 완료합니다.
1. IC 편집기가 열리고 여기서 통신 디자인을 시작할 수 있습니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/ic-ui.png)
+++

대화형 커뮤니케이션 구축을 통해 워크플로우를 간소화하고 효과적인 사용자별 경험을 제공할 수 있습니다.

## 다음 단계

[대화형 통신 템플릿 만들기](/help/forms/interactive-communication/create-interactive-communication-template.md)
[대화형 통신 조각 만들기](/help/forms/interactive-communication/create-interactive-communication-fragment.md)
