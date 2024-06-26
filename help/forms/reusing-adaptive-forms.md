---
title: 적응형 양식의 메타데이터 속성을 재사용하려면 어떻게 해야 합니까?
description: 기존 적응형 양식의 용도를 효율적으로 변경하여 새 적응형 양식을 만드는 방법을 살펴보십시오.
seo-description: You can reuse an existing Adaptive Form to create new Adaptive Forms.
feature: Adaptive Forms, Foundation Components
exl-id: fb8cf3a9-fd19-46bf-b40e-2af76ca68b9f
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 12%

---

# 적응형 양식의 메타데이터 속성 재사용 {#reusing-adaptive-forms}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/reusing-adaptive-forms.html) |
| AEM as a Cloud Service | 이 문서 |

기존 적응형 양식의 일부 속성을 사용하여 새 적응형 양식을 생성하려면 복사-붙여넣기 기능을 사용하면 됩니다. 또한 원하는 폴더 경로에 새 적응형 양식을 붙여넣을 수 있습니다. 모든 메타데이터 속성이 복제되고 XFA 및 XSD 기반 적응형 Forms에 대한 XFA 및 XSD도 복사됩니다.

>[!NOTE]
>
>상태 및 검토 세부 사항이 복사되지 않습니다. 예를 들어, 적응형 양식이 게시되어 있고 복사한 경우 붙여넣은 적응형 양식은 게시되지 않은 상태입니다. 마찬가지로 복사된 에셋이 검토 중인 경우 붙여넣은 에셋은 동일한 검토 하에 있지 않습니다.

## 적응형 양식 복사 {#copy-an-adaptive-form}

다음 방법 중 하나를 사용하여 적응형 양식을 복사합니다.

1. 복사 클릭 ![aem6forms_copy](assets/aem6forms_copy.png) 아이콘을 클릭합니다.

   >[!NOTE]
   >
   >빠른 작업은 마우스로 가리키면 썸네일에 표시되는 작업 항목입니다.

1. 적응형 양식을 선택합니다. 선택 프로세스는 다양한 보기에 따라 다릅니다.

   카드 보기인 경우 선택 항목을 클릭하여 선택 모드로 이동합니다 ![aem6forms_check-circle](assets/aem6forms_check-circle.png) 아이콘을 클릭하고 복사할 모든 적응형 Forms을 클릭합니다.

   목록 보기 상태인 경우 모든 적응형 Forms의 확인란을 클릭하여 선택합니다.

   >[!NOTE]
   >
   >적응형 Forms에 대해서만 복사-붙여넣기 기능이 지원되고 선택한 모든 에셋이 동일한 폴더에 있어야 하므로 선택한 모든 에셋은 적응형 Forms여야 합니다.

   에셋을 선택한 후 복사 를 클릭합니다 ![aem6forms_copy](assets/aem6forms_copy.png) 아이콘을 누르면 도구 모음에 선택한 적응형 양식이 복사됩니다.

## 적응형 양식 붙여넣기 {#paste-an-adaptive-form}

복사 작업을 클릭하면 자동으로 선택 모드가 종료되고 붙여넣기가 수행됩니다 ![붙여넣기](assets/Smock_Paste_18_N.svg) 아이콘 표시. 이제 원하는 폴더 경로로 이동한 다음 붙여넣기를 클릭합니다. ![붙여넣기](assets/Smock_Paste_18_N.svg) 아이콘을 클릭하여 복사한 적응형 양식을 붙여넣습니다.

동일한 폴더에 붙여넣거나 노드 이름이 동일한 다른 파일(CRX 저장소에 저장됨)이 이 대상 폴더에 있는 경우 1이 접미사에 추가됩니다(예: myaf는 myaf1이 되고 myaf1이 동일한 위치에 있는 경우 myaf는 myaf2가 됨). 다른 모든 속성은 원본 적응형 양식과 동일하게 유지됩니다.

붙여넣기를 클릭한 후 ![붙여넣기](assets/Smock_Paste_18_N.svg) 아이콘, 다시 숨겨집니다. 한 번에 한 번만 붙여넣을 수 있습니다. 동일한 에셋의 사본을 다시 생성하려면 해당 에셋을 다시 복사합니다.

## 새 적응형 양식의 콘텐츠 변경 {#change-contents-of-new-adaptive-form}

붙여넣은 적응형 Forms의 콘텐츠는 다음 접근 방식을 사용하여 변경하여 복사된 양식과 다르게 할 수 있습니다.

1. **메타데이터 속성 변경:**

   적응형 양식의 메타데이터 속성(예: 제목 및 설명)을 변경할 수 있습니다. 메타데이터 속성 및 변경 방법에 대한 자세한 내용은 다음을 참조하십시오. [양식 메타데이터 관리](manage-form-metadata.md)

1. **XFA/XSD 기반 적응형 Forms에 대한 XFA/XSD 변경:**

   적응형 Forms에서 사용되는 XFA/XSD를 변경할 수 있습니다. 이러한 적응형 Forms을 변경하는 방법은 다음을 참조하십시오. [양식 메타데이터 관리](manage-form-metadata.md)

1. **다시 게시:**

   붙여넣은 에셋이 복사한 에셋과 다릅니다. 최종 사용자가 사용할 수 있도록 새 에셋으로 게시할 수 있습니다. 에셋을 게시하는 방법을 알려면 <!-- see [Publishing and unpublishing forms](publishing-unpublishing-forms.md) -->


## 추가 참조 {#see-also}

{{see-also}}