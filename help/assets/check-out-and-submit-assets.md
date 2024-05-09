---
title: 파일 체크인 및 체크아웃 [!DNL Assets]
description: 편집할 자산을 체크아웃하고 변경 사항이 완료된 후 다시 체크인하는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 11%

---

# 파일 체크인 및 체크아웃 [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager Assets] 편집을 위해 자산을 체크아웃하고 변경을 완료한 후 다시 체크인할 수 있도록 해 줍니다. 에셋을 체크 아웃한 후에는 에셋만 편집, 주석 달기, 게시, 이동 또는 삭제할 수 있습니다. 에셋을 체크 아웃하면 에셋이 잠깁니다. 다른 사용자는에 자산을 다시 체크 인할 때까지 자산에 대해 이러한 작업을 수행할 수 없습니다. [!DNL Assets]. 그러나 여전히 잠긴 에셋의 메타데이터를 변경할 수 있습니다.

에셋을 체크아웃/체크인하려면 에셋에 대한 쓰기 액세스 권한이 필요합니다.

이 기능은 여러 사용자가 팀 간에 워크플로우 편집에 대해 공동 작업하는 작성자의 변경 사항을 다른 사용자가 무시하는 것을 방지하는 데 도움이 됩니다.

## 에셋 체크아웃 {#checking-out-assets}

1. 다음에서 [!DNL Assets] 사용자 인터페이스에서 체크 아웃할 자산을 선택합니다. 체크아웃할 자산을 여러 개 선택할 수도 있습니다.

1. 도구 모음에서 를 클릭합니다 **[!UICONTROL 체크아웃]**. 다음 **[!UICONTROL 체크아웃]** 옵션이 다음으로 전환 **[!UICONTROL 체크인]**.
체크 아웃한 에셋을 다른 사용자가 편집할 수 있는지 확인하려면 다른 사용자로 로그인합니다. 아이콘 ![체크아웃 잠금 아이콘](assets/do-not-localize/checkout_lock.png) 은 체크 아웃한 자산의 축소판에 표시됩니다.

   ![카드 보기의 체크아웃 아이콘](assets/checkout-icon-card-view.png)

   자산을 선택합니다. 도구 모음에는 에셋을 편집, 주석 달기, 게시 또는 삭제할 수 있는 옵션이 표시되지 않습니다.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   잠긴 에셋의 메타데이터를 편집하려면 **[!UICONTROL 속성 보기]**.

1. 클릭 **[!UICONTROL 편집]** 를 클릭하여 자산을 편집 모드로 엽니다.

1. 에셋을 편집하고 변경 사항을 저장합니다. 예를 들어 이미지를 자르고 저장합니다. 에셋에 주석을 달거나 게시하도록 선택할 수도 있습니다.

1. 에서 편집된 에셋을 선택합니다. [!DNL Assets] 인터페이스 및 클릭 **[!UICONTROL 체크인]** 을 클릭합니다. 수정된 자산이에 체크 인됨 [!DNL Assets] 다른 사용자가 편집할 수 있습니다.

## 강제 체크인 {#forced-check-in}

관리자는 다른 사용자가 체크 아웃한 에셋을 체크 인할 수 있습니다.

1. 에 로그인 [!DNL Assets] 관리자입니다.
1. 다음에서 [!DNL Assets] 사용자 인터페이스 다른 사용자가 체크아웃한 에셋을 하나 이상 선택합니다.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. 도구 모음에서 를 클릭합니다 **[!UICONTROL 잠금 해제]**. 에셋이 다시 체크 인되어 다른 사용자가 편집할 수 있습니다.

## 우수 사례 및 제한 사항 {#tips-limitations}

* 을(를) 삭제할 수 있습니다 *폴더* 체크 아웃된 에셋 파일이 들어 있습니다. 폴더를 삭제하기 전에 사용자가 디지털 자산을 체크아웃하지 않았는지 확인하십시오.

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [체크인 및 체크아웃 이해 [!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [체크인 및 체크아웃을 이해하는 비디오 튜토리얼 [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)
