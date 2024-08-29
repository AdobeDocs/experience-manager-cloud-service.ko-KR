---
title: Forms 포털 연결 구성 요소를 사용하여 AEM Sites 페이지에 양식 링크를 추가하는 방법
description: AEM Sites 페이지에 양식 링크를 추가하는 방법을 알아봅니다.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
source-git-commit: 31f18027d856cbd161457c4a01d6c7c17d1c2b89
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 1%

---


# 사이트 페이지에 양식 링크 추가

은행 웹 사이트 시나리오에서 **링크** Forms 포털 구성 요소는 사용자를 사이트의 다양한 섹션에 있는 특정 양식으로 안내하여 탐색 기능을 향상시킵니다. 웹 사이트 전체에 전략적으로 배치되는 대출 신청서, 계정 개설 양식 또는 피드백 설문 조사와 같은 양식에 대한 직접 참조를 제공합니다. **링크** 구성 요소는 Sites 페이지 내의 특정 적응형 Forms으로 사용자를 안내하는 링크를 삽입합니다. 예를 들어 은행 홈페이지에서 익명의 사용자는 일반 조회양식에 접근할 수 있고, 로그인한 사용자는 대출신청서나 거래승인서 등 보다 안전한 양식에 직접 접근할 수 있다.

![링크 아이콘](/help/forms/assets/link-forms.png)

## 전제 조건

Forms 포털 구성 요소의 다양한 기능을 살펴보기 전에 환경에 대해 핵심 구성 요소가 활성화되었는지 확인하십시오. 사용자 환경에 대해 핵심 구성 요소를 활성화하는 방법에 대한 자세한 지침을 보려면 [여기를 클릭](/help/forms/enable-adaptive-forms-core-components.md)하십시오.

최신 핵심 구성 요소를 환경에 배포하면 작성 환경에서 Forms 포털 구성 요소에 액세스할 수 있습니다.

## Sites 페이지에 링크 구성 요소 추가

Sites 페이지에 **Link** 포털 구성 요소를 추가하려면 다음 단계를 수행하십시오.

1. **편집** 모드로 AEM Sites 페이지를 엽니다.
1. **[!UICONTROL 페이지 정보]** > **[!UICONTROL 템플릿 편집]**(으)로 이동
   ![템플릿 정책 편집](/help/forms/assets/save-form-as-draft-edit-template.png)

1. **[!UICONTROL 정책]**&#x200B;을 클릭하고 **[AEM Archetype 프로젝트 이름] - Forms 및 통신 포털**&#x200B;에서 **[!UICONTROL 링크]** 확인란을 선택합니다.

   ![정책 선택](/help/forms/assets/add-link.png)

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
1. 이제 작성 모드에서 AEM Sites 페이지를 다시 엽니다.
1. 페이지 편집기 내에서 Forms 포털 구성 요소를 추가할 수 있는 섹션을 찾습니다.

1. **추가** 아이콘을 클릭합니다. 아이콘은 새 구성 요소를 추가하는 옵션을 나타내는 더하기 기호(+)입니다.

   **추가** 아이콘을 클릭하면 삽입할 다양한 구성 요소를 표시하는 **새 구성 요소 삽입** 대화 상자가 표시됩니다.

   >[!NOTE]
   >
   > 또는 구성 요소를 드래그 앤 드롭할 수도 있습니다.

1. 대화 상자에서 사용 가능한 구성 요소를 탐색하고 목록에서 원하는 구성 요소를 선택합니다. 예를 들어 목록에서 **Link** 구성 요소를 선택하여 **Link** Forms 포털 구성 요소를 추가합니다.

   ![구성 요소 연결](/help/forms/assets/add-link-in-sites.png)

이제 **Link** 구성 요소의 속성을 구성하십시오.

## 링크 구성 요소의 속성 이해

원활한 사용자 경험을 위해 구성 대화 상자를 사용하여 **링크** 구성 요소 속성을 쉽게 사용자 지정할 수 있습니다. 구성하려면 구성 요소를 선택한 다음 ![구성 아이콘](assets/configure_icon.png)을 선택합니다. **[!UICONTROL 링크]** 대화 상자가 열립니다.

### 탭 표시

![탭 표시](/help/forms/assets/link-asset-tab.png)

**[!UICONTROL 표시]** 탭에서 링크 캡션 및 도구 설명을 입력하여 링크가 나타내는 양식을 쉽게 식별할 수 있습니다.

### 자산 정보 탭

![Assets 정보 탭](/help/forms/assets/link-asset-info.png)

**[!UICONTROL 자산 정보]** 탭에서 자산이 저장되는 저장소 경로를 지정합니다.

### 쿼리 매개 변수 탭

![쿼리 매개 변수 탭](/help/forms/assets/link-query-tab.png)

**[!UICONTROL 쿼리 매개 변수]** 탭에서 키-값 쌍 형식으로 추가 매개 변수를 지정합니다. 링크를 클릭하면 이러한 추가 매개 변수가 양식과 함께 전달됩니다.

## 링크 구성 요소를 사용하여 사이트 페이지에서 양식 링크 보기

**Link** 구성 요소의 **Assets 정보** 속성 탭에 지정된 적응형 양식에 대한 링크를 보려면 사이트 페이지를 미리 봅니다. 링크를 클릭하면 화면에 사용자의 양식이 표시됩니다. 사용자는 권한에 따라 양식에 액세스할 수 있습니다.

![쿼리 매개 변수 탭](/help/forms/assets/link-forms.png)

## 관련 문서

{{forms-portal-see-also}}

## 추가 참조 {#see-also}

{{see-also}}
