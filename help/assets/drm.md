---
title: ' [!DNL Assets]의 Digital Rights Management'
description: ' [!DNL Experience Manager] as a [!DNL Cloud Service]에서 라이선스가 있는 자산에 대한 자산 만료 상태 및 정보를 관리하는 방법을 알아봅니다.'
contentOwner: AG
feature: 자산 관리,DRM
role: User,Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: 568c25d77eb42f7d5fd3c84d71333e083759712d
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 0%

---

# 자산 Digital Rights Management {#digital-rights-management-in-assets}

디지털 자산은 종종 사용 약관 및 기간을 지정하는 라이선스와 연결됩니다. [!DNL Adobe Experience Manager Assets]은(는) [!DNL Experience Manager] 플랫폼과 완전히 통합되므로 자산 만료 정보 및 자산 상태를 효율적으로 관리할 수 있습니다. 라이선스 정보를 자산과 연결할 수도 있습니다.

## 자산 만료 {#asset-expiration}

자산 만료는 자산에 대한 라이선스 요구 사항을 적용하는 효과적인 방법입니다. 게시된 자산이 만료되면 게시 취소되어 라이선스 위반이 발생할 수 있습니다. 관리자 권한이 없는 사용자는 만료된 자산을 편집, 복사, 이동, 게시 및 다운로드할 수 없습니다.

다음 위치에서 자산의 만료 상태를 볼 수 있습니다.

* **카드 보기**: 만료된 자산의 경우 카드의 플래그는 만료된 것으로 나타냅니다.
* **목록 보기**: 만료된 자산의 경우  **** 상태 열에는 만료 배너가  **** 표시됩니다.
* **타임라인**: 타임라인에서 자산의 만료 상태를 볼 수 있습니다. 자산을 선택하고 타임라인 을 선택합니다.
* **참조 레일**: 참조 레일에서 자산의 만료 상태를 볼 수도  **** 있습니다. 복합 자산과 참조된 하위 자산, 컬렉션 및 프로젝트 간의 자산 만료 상태 및 관계를 관리합니다.

1. 참조하는 웹 페이지와 복합 자산을 볼 자산으로 이동합니다.
1. 자산을 선택하고 [!DNL Experience Manager] 로고를 클릭합니다.
1. 메뉴에서 **[!UICONTROL 참조]**&#x200B;를 선택합니다.
1. 만료된 자산의 경우 참조 레일에는 맨 위에 만료 상태 **[!UICONTROL 자산이 만료됨]**&#x200B;이 표시됩니다. 자산이 만료된 하위 자산이 있는 경우 참조 레일에는 **[!UICONTROL 자산이 만료된 하위 자산이 있습니다]** 상태가 표시됩니다.

### 만료된 자산 검색 {#search-expired-assets}

검색 패널에서 만료된 하위 자산을 포함하여 만료된 자산을 검색할 수 있습니다.

1. [!DNL Assets] 콘솔에서 도구 모음의 **[!UICONTROL 검색]**&#x200B;을 클릭하여 [!DNL Experience Manager] 검색 상자를 표시합니다.

1. Omnisearch 상자에 커서를 두고 `Enter` 키를 선택하여 검색 결과 페이지를 표시합니다.

1. 전역 탐색 아이콘을 클릭하여 검색 패널을 표시합니다.

1. **[!UICONTROL 만료 상태]** 옵션을 클릭/탭하여 확장합니다.

1. **[!UICONTROL 만료됨]**&#x200B;을 선택합니다. 만료된 자산이 검색 결과에 표시됩니다.

**[!UICONTROL 만료]** 옵션을 선택하면 [!DNL Assets] 콘솔에는 조합 자산에서 참조하는 만료된 자산과 하위 자산만 표시됩니다. 만료된 하위 자산을 참조하는 복합 자산은 하위 자산이 만료된 직후 표시되지 않습니다. 대신, 다음 번에 스케줄러가 실행될 때 만료된 하위 자산을 참조한다는 것을 감지한 후 [!DNL Experience Manager] 가 표시됩니다.

게시된 자산의 만료 날짜를 현재 스케줄러 주기 이전 날짜로 수정하는 경우 예약은 여전히 다음 번에 이 자산을 실행할 때 만료된 자산으로 감지하고 그에 따라 이 상태를 반영합니다. 자산의 만료 날짜가 다른 시간대에 있는 사용자에 대해 다르게 표시됩니다.

또한, 결함 또는 오류로 인해 스케줄러가 현재 사이클에서 만료된 자산을 감지하지 못하는 경우 스케줄러는 다음 사이클에서 이러한 자산을 다시 검사하여 만료된 상태를 감지합니다.

[!DNL Assets] 콘솔이 만료된 하위 자산과 함께 참조하는 조합 자산을 표시하도록 하려면 **[!UICONTROL Adobe CQ DAM 만료 알림]** 워크플로우를 [!DNL Experience Manager] 구성 관리자에서 구성하십시오.

1. [!DNL Experience Manager] 구성 관리자를 엽니다.
1. **[!UICONTROL Adobe CQ DAM 만료 알림]**&#x200B;을 선택합니다. 기본적으로 **[!UICONTROL 시간 기반 스케줄러]**&#x200B;가 선택되어 자산이 만료된 하위 자산인지 여부를 특정 시간에 확인할 작업을 예약합니다. 작업이 완료되면, 하위 자산이 만료된 자산과 참조된 자산이 검색 결과에 만료된 것으로 표시됩니다.

1. 작업을 주기적으로 실행하려면 **[!UICONTROL 시간 기반 스케줄러 규칙]** 필드를 지우고 **[!UICONTROL 기간별 스케줄러]** 필드에서 시간(초)을 수정합니다. 예를 들어 예제 표현식 &#39;0 &amp;ast; amp;ast; ?&#39; 00시간 후에 작업을 트리거합니다.

<!-- 1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Only the asset creator (the person who uploads a particular asset to Experience Manager Assets) receives an email when the asset expires. See how to configure email notification for additional details around configuring email notifications at the overall Experience Manager level.
-->

1. **[!UICONTROL 이전 알림(초]** 필드)에서 만료와 관련된 알림을 받으려면 자산이 만료되기 전 시간(초)을 지정합니다. 관리자 또는 자산 작성자인 경우, 지정된 시간 후에 자산이 만료된다는 메시지가 자산 만료 전에 메시지를 받게 됩니다.

   자산이 만료되면 만료를 확인하는 다른 알림을 받게 됩니다. 또한 만료된 자산이 비활성화됩니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## 자산 상태 {#asset-states}

[!DNL Assets] 콘솔은 자산에 대한 다양한 상태를 표시할 수 있습니다. 특정 자산의 현재 상태에 따라 해당 카드 보기에는 해당 상태를 설명하는 레이블(예: 만료됨, 게시됨, 승인됨, 거부됨)이 표시됩니다.

1. [!DNL Assets] 사용자 인터페이스에서 자산을 선택합니다.

1. 도구 모음에서 **[!UICONTROL 게시]**&#x200B;를 클릭합니다. 도구 모음에 **게시**&#x200B;가 표시되지 않으면 도구 모음에서 **[!UICONTROL 자세히]**&#x200B;를 클릭하고 **[!UICONTROL 게시]** 옵션을 찾습니다.

1. 메뉴에서 **[!UICONTROL 게시]**&#x200B;를 선택한 다음 확인 대화 상자를 닫습니다.
1. 선택 모드를 종료합니다. 자산에 대한 게시 상태가 카드 보기에서 자산 축소판 아래에 표시됩니다. 목록 보기에서 게시됨 열에는 자산이 게시된 시간이 표시됩니다.

1. 해당 자산 세부 사항 페이지를 표시하려면 [!DNL Assets] 인터페이스에서 자산을 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.

1. [!UICONTROL 고급] 탭에서 **[!UICONTROL 만료]** 필드에서 자산에 대한 만료 날짜를 설정합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭한 다음 **[!UICONTROL 닫기]**&#x200B;를 클릭하여 자산 콘솔을 표시합니다.
1. 자산에 대한 게시 상태는 카드 보기에서 자산 축소판 아래에 있는 만료된 상태를 나타냅니다. 목록 보기에서 자산의 상태가 **[!UICONTROL 만료됨]**&#x200B;으로 표시됩니다.

1. [!DNL Assets] 콘솔에서 폴더를 선택하고 폴더에 검토 작업을 만듭니다.
1. 검토 작업에서 자산을 검토 및 승인/거부하고 **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
1. 검토 작업을 만든 폴더로 이동합니다. 승인/거부한 자산의 상태가 카드 보기의 맨 아래에 표시됩니다. 목록 보기에서 승인 및 만료 상태가 적절한 열에 표시됩니다.

1. 해당 상태에 따라 자산을 검색하려면 **[!UICONTROL 검색]**&#x200B;을 클릭하여 Omnisearch 막대를 표시합니다.

1. `Return` 을 선택하고 [!DNL Experience Manager] 을 클릭하여 검색 패널을 표시합니다.
1. 검색 패널에서 **[!UICONTROL 게시 상태]**&#x200B;를 클릭하고 **[!UICONTROL 게시됨]**&#x200B;을 선택하여 [!DNL Assets]에서 게시된 자산을 검색합니다.

1. **[!UICONTROL 승인 상태]**&#x200B;를 클릭하고 적절한 옵션을 클릭하여 승인되었거나 거부된 자산을 검색합니다.

1. 만료 상태에 따라 자산을 검색하려면 검색 패널에서 **[!UICONTROL 만료 상태]** 를 선택하고 적절한 옵션을 선택합니다.

1. 다양한 검색 패싯에서 상태 조합을 기반으로 자산을 검색할 수도 있습니다. 예를 들어, 검색 패싯에서 적절한 옵션을 선택하여 검토 작업에서 승인되었으나 아직 만료되지 않은 게시된 자산을 검색할 수 있습니다.

## [!DNL Assets]의 Digital Rights Management {#digital-rights-management-in-assets-1}

이 기능은 [!DNL Adobe Experience Manager Assets]에서 라이선스가 부여된 자산을 다운로드하기 전에 사용권 계약에 동의함을 적용합니다.

보호된 자산을 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 클릭하면 사용권 계약에 동의하도록 라이선스 페이지로 리디렉션됩니다. 사용권 계약에 동의하지 않으면 **[!UICONTROL 다운로드]** 옵션을 사용할 수 없습니다.

선택한 항목에 여러 개의 보호된 자산이 포함되어 있는 경우 한 번에 한 개의 자산을 선택하고 사용권 계약에 동의한 다음 자산 다운로드를 계속 진행합니다.

다음 조건 중 하나가 충족되면 자산이 보호된 것으로 간주됩니다.

* 자산 메타데이터 속성 `xmpRights:WebStatement`은(는) 자산에 대한 사용권 계약이 포함된 페이지의 경로를 가리킵니다.
* 자산 메타데이터 속성 `adobe_dam:restrictions` 값은 사용권 계약을 지정하는 원시 HTML입니다.

>[!NOTE]
>
>[!DNL Experience Manager] 이전 릴리스에서 라이센스를 저장하는 데 사용되는 `/etc/dam/drm/licences` 위치는 더 이상 사용되지 않습니다.
>
>라이센스 페이지를 만들거나 수정하거나 이전 [!DNL Experience Manager] 릴리스에서 지원하는 경우, Adobe은 `/apps/settings/dam/drm/licenses` 또는 `/conf/*/settings/dam/drm/licenses` 아래에 저장하는 것을 권장합니다.

### DRM 보호 자산 다운로드 {#downloading-drm-assets}

1. 카드 보기에서 다운로드할 자산을 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 저작권 관리]** 페이지의 목록에서 다운로드할 자산을 선택합니다.
1. [!UICONTROL 라이센스] 창에서 **[!UICONTROL 동의]**&#x200B;를 선택합니다. 자산 옆에 확인 표시가 나타납니다. **[!UICONTROL 다운로드]** 옵션을 클릭합니다.

   >[!NOTE]
   >
   >**[!UICONTROL 다운로드]** 옵션은 보호된 자산에 대한 사용권 계약에 동의하도록 선택한 경우에만 활성화됩니다. 그러나 선택한 항목에 보호된 자산과 보호되지 않은 자산이 모두 포함되어 있으면 보호된 자산만 창에 나열되고 보호되지 않은 자산을 다운로드할 수 있는 **[!UICONTROL 다운로드]** 옵션이 활성화됩니다. 여러 개의 보호된 자산에 대한 사용권 계약을 동시에 수락하려면 목록에서 자산을 선택한 다음 **[!UICONTROL 동의]**&#x200B;를 선택하십시오.

1. 대화 상자에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭하여 자산 또는 해당 표현물을 다운로드합니다.
