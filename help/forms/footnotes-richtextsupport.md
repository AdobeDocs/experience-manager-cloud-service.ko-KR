---
title: 적응형 양식에 각주를 추가하는 방법
description: 적응형 양식의 각주에 대해 리치 텍스트 편집기(RTE)를 사용하십시오.
feature: Adaptive Forms, Foundation Components
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
role: User, Developer
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 3%

---

# 각주 구성 요소 {#footnotecomponent}

>[!NOTE]
>
> Adobe은 [새로운 적응형 Forms 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 Forms 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)를 위해 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용할 것을 권장합니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 Forms을 작성하는 이전 방법에 대해 설명합니다.

**[!UICONTROL 각주]**&#x200B;은(는) 페이지의 끝에 표시되는 추가 정보나 참고 사항입니다. [!UICONTROL 각주]은(는) 숫자와 함께 텍스트에 위 첨자로 표시된 각주를 포함합니다.

각주는 페이지에 나타나는 순서대로 순차적으로 번호가 매겨집니다. 각주는 페이지 하단에 있는 번호에 해당하는 윗첨자로서 고유한 번호를 가진다. 숫자 옆에 보조 정보가 각주 설명으로 나타납니다.

![각주 설명](/help/forms/assets/footnote_description.png)


## 각주 사용 {#usesoffootnotes}

* 인용을 제공하는 데 도움이 됩니다.
* 기본 정보의 정상적인 흐름을 방해할 수 있는 추가 정보를 제공합니다.
* 괄호 정보 또는 저작권 권한을 제공합니다.

적응형 Forms에서 [!UICONTROL 각주]는 양식을 완성하거나 사용하는 방법에 대한 정보를 표시하는 데 사용됩니다. 적응형 Forms을 만드는 방법에 대한 자세한 내용은 [적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html)를 참조하십시오.

## 적응형 Forms 각주 {#using-footnote-adaptiveforms}

적응형 Forms에 각주를 추가하려면 다음 단계를 수행하십시오.
1. **편집** 모드에서 적응형 양식을 엽니다.
1. 구성 요소 브라우저에서 **[!UICONTROL Text]** 구성 요소를 적응형 양식으로 드래그 앤 드롭합니다.
1. 추가한 **[!UICONTROL Text]** 구성 요소를 선택하고 ![cmpr](assets/configure-icon.svg)을(를) 선택하여 해당 속성을 편집합니다.

   적응형 Forms의 ![각주](/help/forms/assets/footnote_rte.png)

1. 각주 설명을 추가할 텍스트를 선택하고 ![별](/help/forms/assets/asterisk.svg) 단추를 클릭하여 **[!UICONTROL 각주]** 구성 요소의 스타일을 지정하십시오.

1. 변경 내용 및 스타일을 저장하려면 ![확인](/help/forms/assets/save_icon.svg)을 클릭하세요.

   >[!NOTE]
   >
   >* 각주에 자동으로 번호가 지정되며 적응형 양식에 작성된 방식으로 표시됩니다.
   >* 중복된 각주가 있으면 모든 중복된 각주에 대해 숫자가 동일합니다.

1. 구성 요소 브라우저에서 **[!UICONTROL 각주 자리 표시자]** 구성 요소를 적응형 양식으로 드래그 앤 드롭합니다.

   >[!NOTE]
   >
   >* 게시 인스턴스에서 각주는 **[!UICONTROL 각주 자리 표시자]** 구성 요소가 적응형 양식에 배치된 위치에 표시됩니다.
   >* 다른 패널 사이를 탐색할 때 탐색 패널 내에 있는 **[!UICONTROL 각주 자리 표시자]**&#x200B;에는 보이는 각주만 표시됩니다.

1. 속성을 저장합니다.

런타임 시 숫자는 텍스트에 위 첨자로 표시되며 해당 설명은 적응형 양식에 [!UICONTROL 각주 자리 표시자]가 있는 위치의 **[!UICONTROL 각주]** 구성 요소에 표시됩니다. [!UICONTROL 각주]에서 해당 번호를 클릭하여 각주 설명으로 바로 이동할 수 있습니다.


## 추가 참조 {#see-also}

{{see-also}}