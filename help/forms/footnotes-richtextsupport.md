---
title: 각주 지원
description: 각주를 위한 RTE 지원.
source-git-commit: 6f6cf5657bf745a2e392a8bfd02572aa864cc69c
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 각주 구성 요소 {#footnotecomponent}

**[!UICONTROL 각주]** 페이지 끝에 나타나는 추가 정보 또는 노트입니다. [!UICONTROL 각주] 텍스트에 위 첨자로 표시된 메모를 포함합니다.

각주는 페이지에 나타나는 순서대로 번호가 매겨진다. 각 각주에는 페이지 하단에 있는 숫자에 해당하는 위 첨자로 고유한 숫자가 있습니다. 번호 옆에 보조 정보가 각주 설명으로 나타납니다.

![각주 설명](/help/forms/assets/footnote_description.png)


## 각주 사용 {#usesoffootnotes}

* 인용구를 제공하는 데 도움이 됩니다.
* 기본 정보의 정상적인 흐름을 방해할 수 있는 추가 정보를 제공합니다.
* 부모 정보 또는 저작권 권한을 제공합니다.

응용 Forms에서, [!UICONTROL 각주] 양식을 작성하거나 사용하는 방법에 대한 정보를 표시하는 데 사용됩니다. 적응형 Forms을 만드는 방법에 대한 자세한 내용은 [적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## 적응형 Forms의 각주 {#using-footnote-adaptiveforms}

적응형 Forms에서 각주를 추가하려면 다음 단계를 수행하십시오.
1. 에서 적응형 양식 열기 **편집** 모드.
1. 구성 요소 브라우저에서 **[!UICONTROL 텍스트]** 구성 요소를 적응형 양식에 추가합니다.
1. 을(를) 선택합니다 **[!UICONTROL 텍스트]** 구성 요소를 추가하고 탭합니다. ![cmppr](assets/configure-icon.svg) 속성을 편집하려면

   ![적응형 Forms의 각주](/help/forms/assets/footnote_rte.png)

1. 각주 설명을 추가할 텍스트를 선택하고  ![별](/help/forms/assets/asterisk.svg) 단추 스타일 지정 **[!UICONTROL 각주]** 구성 요소.

1. 클릭 ![check](/help/forms/assets/save_icon.svg) 변경 사항 및 스타일을 저장합니다.

   >[!NOTE]
   >
   >* 각주는 자동으로 번호가 매겨져 적응형 양식에 생성된 방식으로 나타납니다.
   >* 중복 각주가 있는 경우 중복 각주 모두에 대해 숫자가 동일합니다.


1. 구성 요소 브라우저에서 **[!UICONTROL 각주 자리 표시자]** 구성 요소를 적응형 양식에 추가합니다.
   >[!NOTE]
   >
   >* 게시 인스턴스에서 각주가 **[!UICONTROL 각주 자리 표시자]** 구성 요소는 적응형 양식에 배치됩니다.
   >* 다른 패널 사이를 탐색하면 보이는 각주만 **[!UICONTROL 각주 자리 표시자]** 탐색 패널 내에 표시됩니다.


1. 속성을 저장합니다.

런타임에 번호가 텍스트에 위 첨자로 표시되고 해당 설명이 **[!UICONTROL 각주]** 구성 요소 위치 [!UICONTROL 각주 자리 표시자] 적응형 양식에 배치됩니다. 각주 설명에서 해당 번호를 눌러 각주 설명으로 직접 이동할 수 있습니다 [!UICONTROL 각주].