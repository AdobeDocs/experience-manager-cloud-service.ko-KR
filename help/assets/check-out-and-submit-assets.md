---
title: 파일 체크 인 및 체크 아웃 [!DNL Assets]
description: 편집할 자산을 확인하고 변경 사항이 완료되면 다시 체크 인하는 방법을 알아봅니다.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 5%

---

# 파일 체크인 및 체크아웃 [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

[!DNL Adobe Experience Manager Assets] 편집할 자산을 확인하고 변경을 완료한 후 다시 체크 인할 수 있습니다. 자산을 체크 아웃한 후에는 자산을 편집, 주석 달기, 게시, 이동 또는 삭제할 수만 있습니다. 자산을 체크 아웃하면 자산이 잠깁니다. 다른 사용자는 자산을 다시 체크 인할 때까지 자산에서 이러한 작업을 수행할 수 없습니다 [!DNL Assets]. 그러나 잠긴 자산에 대한 메타데이터를 변경할 수 있습니다.

자산을 체크 아웃/체크 인하려면 자산에 대한 쓰기 액세스 권한이 필요합니다.

이 기능은 여러 사용자가 여러 팀 간의 워크플로우 편집에서 공동 작업하는 작성자가 변경한 내용을 다른 사용자가 덮어쓰지 않도록 하는 데 도움이 됩니다.

## 자산 체크아웃 {#checking-out-assets}

1. 에서 [!DNL Assets] 사용자 인터페이스에서 확인할 자산을 선택합니다. 여러 자산을 선택하여 체크아웃할 수도 있습니다.

1. 도구 모음에서 **[!UICONTROL 체크아웃]**. 다음 **[!UICONTROL 체크아웃]** 옵션 전환 **[!UICONTROL 체크 인]**.
다른 사용자가 체크 아웃한 자산을 편집할 수 있는지 확인하려면 다른 사용자로 로그인합니다. 아이콘 ![체크아웃 잠금 아이콘](assets/do-not-localize/checkout_lock.png) 체크 아웃한 자산의 축소판에 표시됩니다.

   ![카드 보기의 체크아웃 아이콘](assets/checkout-icon-card-view.png)

   자산을 선택합니다. 도구 모음에는 자산을 편집, 주석 달기, 게시 또는 삭제할 수 있는 옵션이 표시되지 않습니다.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   잠긴 자산의 메타데이터를 편집하려면 **[!UICONTROL 속성 보기]**.

1. 클릭 **[!UICONTROL 편집]** 자산을 편집 모드로 열려면 다음을 수행하십시오.

1. 자산을 편집하고 변경 사항을 저장합니다. 예를 들어, 이미지를 자르거나 저장합니다. 자산에 주석을 달거나 게시하도록 선택할 수도 있습니다.

1. 에서 편집한 자산을 선택합니다 [!DNL Assets] 인터페이스 및 클릭 **[!UICONTROL 체크 인]** 를 클릭합니다. 수정된 자산은에 체크 인됩니다. [!DNL Assets] 및 은 다른 사용자가 편집할 수 있도록 제공됩니다.

## 강제 체크인 {#forced-check-in}

관리자는 다른 사용자가 체크 아웃한 자산을 체크 인할 수 있습니다.

1. 에 로그인합니다. [!DNL Assets] 관리자로.
1. 에서 [!DNL Assets] 사용자 인터페이스는 다른 사용자가 체크 아웃한 자산을 한 개 이상 선택합니다.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. 도구 모음에서 **[!UICONTROL 잠금 해제]**. 자산이 다시 체크 인되고 다른 사용자가 편집할 수 있습니다.

## 우수 사례 및 제한 사항 {#tips-limitations}

* 삭제할 수 있습니다 *폴더* 여기에는 체크아웃 자산 파일이 포함되어 있습니다. 폴더를 삭제하기 전에 사용자가 디지털 자산을 체크 아웃하지 않았는지 확인합니다.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [체크인 및 체크아웃 이해 [!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [체크인 및 체크아웃 이해 비디오 튜토리얼 [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)

