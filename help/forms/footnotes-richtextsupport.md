---
title: 적응형 양식에 각주를 추가하는 방법
description: 적응형 양식의 각주에 대해 리치 텍스트 편집기(RTE)를 사용하십시오.
feature: Adaptive Forms, Foundation Components
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
source-git-commit: eaab351460363b83c7d3667e048235506cc71c41
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 12%

---

# 각주 구성 요소 {#footnotecomponent}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>

**[!UICONTROL 각주]** 는 페이지 끝에 표시되는 정보 또는 참고의 추가 비트입니다. [!UICONTROL 각주] 는 숫자로 텍스트에 표시된 메모를 위 첨자로 구성합니다.

각주는 페이지에 나타나는 순서대로 순차적으로 번호가 매겨집니다. 각주는 페이지 하단에 있는 번호에 해당하는 윗첨자로서 고유한 번호를 가진다. 숫자 옆에 보조 정보가 각주 설명으로 나타납니다.

![각주 설명](/help/forms/assets/footnote_description.png)


## 각주 사용 {#usesoffootnotes}

* 인용을 제공하는 데 도움이 됩니다.
* 기본 정보의 정상적인 흐름을 방해할 수 있는 추가 정보를 제공합니다.
* 괄호 정보 또는 저작권 권한을 제공합니다.

적응형 Forms에서 [!UICONTROL 각주] 양식을 완성하거나 사용하는 방법에 대한 정보를 표시하는 데 사용됩니다. 적응형 Forms을 만드는 방법에 대한 자세한 내용은 다음을 참조하십시오. [적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## 적응형 Forms 각주 {#using-footnote-adaptiveforms}

적응형 Forms에 각주를 추가하려면 다음 단계를 수행하십시오.
1. 에서 적응형 양식 열기 **편집** 모드.
1. 구성 요소 브라우저에서 **[!UICONTROL 텍스트]** 구성 요소를 적응형 양식에 추가합니다.
1. 다음 항목 선택 **[!UICONTROL 텍스트]** 추가하고 선택한 구성 요소 ![cmppr](assets/configure-icon.svg) 속성을 편집합니다.

   ![적응형 Forms 각주](/help/forms/assets/footnote_rte.png)

1. 각주 설명을 추가할 텍스트를 선택하고  ![별](/help/forms/assets/asterisk.svg) 스타일을 지정하는 단추 **[!UICONTROL 각주]** 구성 요소.

1. 클릭 ![check](/help/forms/assets/save_icon.svg) 변경 내용 및 스타일을 저장합니다.

   >[!NOTE]
   >
   >* 각주에 자동으로 번호가 지정되며 적응형 양식에 작성된 방식으로 표시됩니다.
   >* 중복된 각주가 있으면 모든 중복된 각주에 대해 숫자가 동일합니다.

1. 구성 요소 브라우저에서 **[!UICONTROL 각주 플레이스홀더]** 구성 요소를 적응형 양식에 추가합니다.
   >[!NOTE]
   >
   >* 게시 인스턴스에서 각주는 다음 위치에 표시됩니다. **[!UICONTROL 각주 플레이스홀더]** 구성 요소가 적응형 양식에 배치됩니다.
   >* 다른 패널 사이를 탐색할 때 화면에 표시되는 각주만 **[!UICONTROL 각주 플레이스홀더]** 탐색 패널에 표시됩니다.

1. 속성을 저장합니다.

런타임 시 숫자는 텍스트에 위 첨자로 나타나고 해당 설명은 **[!UICONTROL 각주]** 다음의 위치에 있는 구성 요소 [!UICONTROL 각주 플레이스홀더] 은 적응형 양식에 배치됩니다. 에서 해당 번호를 클릭하여 각주 설명으로 직접 이동할 수 있습니다. [!UICONTROL 각주].


## 추가 참조 {#see-also}

{{see-also}}