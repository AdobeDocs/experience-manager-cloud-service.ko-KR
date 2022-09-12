---
title: 여러 단계 양식 시퀀스를 만드는 방법
description: 사용 [!DNL Experience Manager Forms]로 지정하는 경우 사용자가 적응형 양식을 탐색하고 채울 수 있도록 양식 패널 시퀀스를 정의할 수 있습니다. 사용 사례 접근 방식을 예로 들어 여러 단계로 구성된 양식 시퀀스를 만들어 보다 깊이 있게 살펴보십시오.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# 여러 단계 양식 시퀀스 소개 {#introduction-to-multi-step-form-sequence}

적응형 Forms을 통해 양식 작성자는 여러 단계로 구성된 데이터 캡처 경험을 손쉽게 만들 수 있습니다. 여러 패널을 만들고 각 패널을 다른 탐색 패턴과 연결하도록 내장된 지원이 포함되어 있습니다. 양식 작성자는 양식 필드를 논리 섹션으로 그룹화하고 그룹을 패널로 나타낼 수 있습니다. 패널 사이의 전체 탐색은 패널 레이아웃을 사용하여 제어됩니다. 작성자는 마법사 레이아웃을 사용하여 순차적으로 배치하거나 탭 레이아웃을 사용하여 임시 방식으로 패널을 다른 레이아웃으로 배치하도록 선택할 수 있습니다. 패널 레이아웃에 대한 자세한 내용은 [응용 Forms의 레이아웃 기능](layout-capabilities-adaptive-forms.md).

일반적인 양식 채우기 경험에는 데이터를 캡처하는 것보다 더 많은 단계가 포함됩니다. 전체 양식 제출에는 디지털 양식에 서명, 양식에 입력된 정보를 확인하는 단계, 결제 처리 등과 같은 다른 단계를 포함할 수 있습니다. 경우에 따라 다르다.

사용 사례에서 데이터 캡처 단계 세트를 요구하는 경우 또는 특정 단계를 따라야 하는 규정이 있는 경우, [!DNL Experience Manager Forms] 는 양식 간에 이러한 공통 구조를 적용하는 방법을 제공합니다. 양식 구조의 미리 작성된 구현에서는 양식의 단계 순서를 정의합니다. ![여러 단계 양식 시퀀스의 예](assets/formpipeline.png)

여러 단계 양식 시퀀스의 예

양식의 채우기, 확인, 서명 및 확인 단계에 대한 시퀀스를 만들어야 하는 사용 사례를 살펴보겠습니다. 이러한 시퀀스를 만드는 단계는 다음과 같습니다.

1. 양식 템플릿을 정의하고 필요한 패널을 여기에 추가합니다. 시퀀스의 각 단계마다 패널이 하나씩 있어야 합니다. 그러나 패널 내에 하위 패널을 포함할 수 있습니다.

   이 예제에서는 다음 패널을 추가할 수 있습니다.

   * **[!UICONTROL 채우기]**: 여기에는 데이터를 캡처하기 위한 양식 필드가 포함되어 있습니다. 여기서는 중첩된 하위 패널을 포함하여 개인, 가족, 재무 등과 같은 다양한 유형의 정보에 대한 섹션을 만들 수 있습니다.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL 전자 서명]**: 여기에는 다음 항목이 포함되어 있습니다 **[!UICONTROL Sign]** XFA 기반 적응형 양식에 사용할 수 있는 구성 요소입니다. 다음과 같은 서명 서비스를 제공합니다.

      * Adobe Document Cloud eSign 서비스
      * 스크리블 서명
   * **[!UICONTROL 확인]**: 여기에는 다음 항목이 포함되어 있습니다 **[!UICONTROL 요약]** 사용자가 양식에 서명하고 시퀀스의 확인(요약) 단계에 도달한 후 양식 제출을 확인하는 메시지를 표시하는 구성 요소입니다. 작성자가 [!UICONTROL 요약] 구성 요소를 만들고, 감사 메시지를 표시하고, 생성된 PDF에 대한 링크를 표시하는 등의 작업을 수행할 수 있습니다.



1. 루트 패널의 레이아웃을 다음으로 선택합니다. **[!UICONTROL 마법사]**.
1. 나머지 단계를 완료하여 양식 템플릿을 만듭니다. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

양식 서식 파일에서 양식 시퀀스를 정의한 후에는 요구 사항에 맞게 양식을 사용자 지정할 수 있지만 기본 구조가 제자리에 있는 양식을 만들 수 있습니다.
