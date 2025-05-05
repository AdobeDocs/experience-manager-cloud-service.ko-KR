---
title: 자산 관계
description: 몇 가지 일반적인 특성을 공유하는 디지털 에셋의 연결 방법을 알아봅니다. 또한 에셋 관계를 사용하여 디지털 에셋 간의 소스에서 파생된 관계를 만듭니다.
role: User
feature: Collaboration,Asset Management
solution: Experience Manager, Experience Manager Assets
source-git-commit: 77dab2731f8d442bf999bf1614ef060944794574
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 9%

---

# 자산 관계 {#related-assets}

[!DNL Adobe Experience Manager Assets]을(를) 사용하면 관련 에셋 기능을 사용하여 조직의 필요에 따라 에셋을 수동으로 연결할 수 있습니다. 예를 들어 유사한 주제에 대한 에셋 또는 이미지/비디오와 라이선스 파일을 연결할 수 있습니다. 특정 공통 속성을 공유하는 에셋의 관계를 설정할 수 있습니다. 이 기능을 사용하여 에셋 간의 소스/파생 관계를 만들 수도 있습니다. 예를 들어 INDD 파일에서 생성된 PDF 파일이 있는 경우 PDF 파일을 해당 소스 INDD 파일과 연결할 수 있습니다.

이 기능을 사용하면 저해상도 PDF 파일 또는 JPG 파일을 공급업체 또는 에이전시와 공유할 수 있으며 고해상도 INDD 파일을 요청 시에만 사용할 수 있습니다.

>[!NOTE]
>
>에셋에 대한 편집 권한이 있는 사용자만 에셋을 연결 및 연결 해제할 수 있습니다.

## 에셋 관련 단계 {#steps-to-relate-assets}

1. [!DNL Experience Manager] 인터페이스에서 연결할 자산의 **[!UICONTROL 속성]** 페이지를 엽니다.

   ![에셋과 연결할 에셋의 속성 페이지를 엽니다](assets/asset-properties-relate-assets.png)

1. 다른 에셋을 선택한 에셋과 연결하려면 **[!UICONTROL 에셋 관계]** ![에셋 관계](assets/do-not-localize/link-relate.png)를 클릭합니다.
1. 다음 중 하나를 수행하십시오.

   * 에셋의 원본 파일을 연결하려면 목록에서 **[!UICONTROL Source 추가]**&#x200B;를 선택하십시오. 단일 자산만 소스로 연결할 수 있습니다.
   * 파생 파일을 연결하려면 목록에서 **[!UICONTROL 파생 추가]**&#x200B;를 선택하십시오. 이 범주에서 여러 자산을 연결할 수 있습니다.
   * 자산 간에 양방향 관계를 만들려면 목록에서 **[!UICONTROL 다른 항목 추가]**&#x200B;를 선택하십시오. 이 범주에서 여러 자산을 연결할 수 있습니다.

1. **[!UICONTROL Assets 선택]** 화면에서 연결할 에셋의 위치로 이동하여 선택합니다. Shift 키를 누른 채 클릭하여 한 번에 하나의 자산을 선택하거나 여러 자산을 선택할 수 있습니다. 이 경우 Assets 보기에서 [지원되는 파일 형식](/help/assets/supported-file-formats-assets-view.md)이 포함될 수 있습니다.

   ![관련 에셋 추가](assets/add-related-asset.png)

1. **[!UICONTROL 선택]**&#x200B;을 클릭합니다. 3단계에서 선택한 관계에 따라 관련 에셋이 **[!UICONTROL 에셋 관계]** 섹션의 해당 범주 아래에 나열됩니다. 예를 들어 관련된 에셋이 현재 에셋의 원본 파일인 경우 **[!UICONTROL Source]** 아래에 나열됩니다.

   ![Assets 관계 예](assets/asset-relations-example.png)

1. 각 섹션의 모든 관련 에셋([!UICONTROL Source], [!UICONTROL 파생] 및 [!UICONTROL 기타])에 사용할 수 있는 **[!UICONTROL 관계 해제]** ![에셋 관계 해제](assets/do-not-localize/link-unrelate-icon.png)을 클릭하여 에셋의 관계를 해제합니다.

## 관련 에셋 번역 {#translating-related-assets}

관련 에셋 기능을 사용하여 에셋 간의 소스/파생 관계를 만드는 것도 번역 워크플로에서 유용합니다. 파생된 에셋에서 번역 워크플로우를 실행하면 [!DNL Experience Manager Assets]에서 원본 파일이 참조하는 모든 에셋을 자동으로 가져와서 번역을 위해 포함합니다. 이렇게 하면 소스 에셋에서 참조하는 에셋이 소스 및 파생된 에셋과 함께 번역됩니다. 원본 파일이 다른 에셋과 관련된 경우 [!DNL Experience Manager Assets]은(는) 참조된 에셋을 가져와서 번역을 위해 포함시킵니다.

[AEM에서 자산 번역](/help/assets/translate-assets.md)을 참조하세요.

## 다음 단계 {#next-steps}

* Assets 보기 사용자 인터페이스에서 사용 가능한 [!UICONTROL 피드백] 옵션을 사용하여 제품 피드백 제공

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백 제공

* [고객 지원 센터](https://experienceleague.adobe.com/ko?support-solution=General#support) 문의

>[!MORELIKETHIS]
>
>* [자산의 버전 보기](/help/assets/manage-organize-assets-view.md#view-versions)
>* [AEM에서 자산 번역](/help/assets/translate-assets.md)
>* [Assets 보기에서 지원되는 파일 형식](/help/assets/supported-file-formats-assets-view.md).
