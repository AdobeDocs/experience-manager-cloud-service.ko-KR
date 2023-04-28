---
title: Digital Rights Management [!DNL Assets]
description: 에서 라이선스가 있는 자산에 대한 자산 만료 상태 및 정보를 관리하는 방법을 알아봅니다. [!DNL Experience Manager] 로서의 [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,DRM
role: User,Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 4%

---

# 디지털 자산에 대한 Digital Rights Management {#digital-rights-management-in-assets}

디지털 자산은 종종 사용 약관 및 기간을 지정하는 라이선스와 연결됩니다. 사용 [!DNL Experience Manager] platform을 사용하면 자산 만료 정보 및 라이선스 정보를 효율적으로 관리할 수 있습니다.

## 자산 만료 {#asset-expiration}

자산에 대한 라이선스 요구 사항을 적용하려면 자산 만료 정보를 사용하십시오. 만료 정보는 게시된 자산이 만료되면 게시 취소되어 라이선스 위반을 방지합니다. 관리자 권한이 없는 사용자는 만료된 자산을 편집, 복사, 이동, 게시 및 다운로드할 수 없습니다.

다음 위치에서 자산의 만료 상태를 볼 수 있습니다.

* **카드 보기**: 만료된 자산의 경우 카드의 플래그는 만료된 것으로 나타냅니다.
* **목록 보기**: 만료된 자산의 경우 **[!UICONTROL 상태]** 열이 표시됩니다 **[!UICONTROL 만료됨]** 배너.
* **타임라인**: 타임라인에서 자산의 만료 상태를 볼 수 있습니다. 자산을 선택하고 타임라인 을 선택합니다.
* **참조 레일**: 에서 자산의 만료 상태를 볼 수도 있습니다 **[!UICONTROL 참조]** 레일. 복합 자산과 참조된 하위 자산, 컬렉션 및 프로젝트 간의 자산 만료 상태 및 관계를 관리합니다.

자산에 대한 참조 웹 페이지 및 복합 자산을 보려면 다음 단계를 수행합니다.

1. 자산으로 이동하고 자산을 선택한 다음 을 클릭합니다 ![왼쪽 레일 컨텐츠 참조 아이콘](assets/do-not-localize/content-rail-icon.png). 왼쪽 레일이 열립니다.
1. 선택 **[!UICONTROL 참조]** 왼쪽 레일에서
1. 만료된 자산의 경우 [!UICONTROL 참조] 만료 상태를 다음으로 표시 **[!UICONTROL 자산이 만료됨]**. 자산이 만료된 하위 자산인 경우 [!UICONTROL 참조] 레일에는 상태가 표시됩니다 **[!UICONTROL 자산이 만료된 하위 자산이 있습니다.]**.

### 만료된 자산 검색 {#search-expired-assets}

만료된 하위 자산을 포함하여 만료된 자산을 검색하려면 다음 단계를 수행합니다.

1. 에서 [!DNL Assets] 콘솔 **[!UICONTROL 검색]** 도구 모음에서 `Enter`.

1. 전역 탐색 아이콘을 클릭하고 **[!UICONTROL 만료 상태]** 선택 사항입니다.

1. 선택 **[!UICONTROL 만료됨]**. 검색 결과에 만료된 자산이 표시됩니다.

을(를) 선택하는 경우 **[!UICONTROL 만료됨]** 옵션, [!DNL Assets] 콘솔은 복합 자산에서 참조하는 만료된 자산 및 하위 자산만 표시합니다. 만료된 하위 자산을 참조하는 복합 자산은 하위 자산이 만료된 직후 표시되지 않습니다. 대신, 나중에 표시됩니다 [!DNL Experience Manager] 은 스케줄러가 다음에 실행될 때 만료된 하위 자산을 참조하는지 감지합니다.

게시된 자산의 만료 날짜를 현재 스케줄러 주기 이전 날짜로 수정할 수 있습니다. 그러나 예약은 다음 번에 실행될 때 여전히 만료된 자산과 같은 자산을 감지하고 [!DNL Experience Manager] 는 보고서의 상태를 반영합니다. 자산의 만료 날짜가 다른 시간대에 있는 사용자에 대해 다르게 표시됩니다.

또한 오류가 발생하여 스케줄러가 현재 사이클에서 만료된 자산을 감지하지 못하는 경우 스케줄러는 다음 사이클에서 이러한 자산을 다시 검사하여 만료된 상태를 감지합니다.

를 사용하려면 [!DNL Assets] 콘솔에 참조된 조합 자산과 만료된 하위 자산을 함께 표시하려면 다음을 구성합니다. **[!UICONTROL Adobe CQ DAM 만료 알림]** 의 워크플로우 [!DNL Experience Manager]. 시간 기반 스케줄러는 자산이 하위 자산이 만료되었는지 여부를 특정 시간에 확인할 작업을 예약합니다. 작업이 완료되면, 하위 자산이 만료된 자산과 참조된 자산이 검색 결과에 만료된 것으로 표시됩니다.

1. 액세스 권한 [!DNL Cloud Manager] 환경과 연결된 Git 리포지토리.
1. 이름이 인 파일 커밋 `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` 저장소에서 다음 내용을 볼 수 있습니다.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1. 다음 지침을 따르십시오. [에서 OSGi 구성을 수행하는 방법 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md).

다음 속성을 사용하여 스케줄러를 구성할 수 있습니다.

* A `true` 속성 값 `cq.dam.expiry.notification.scheduler.istimebased` 스케줄러를 시작합니다. * 속성 값 `cq.dam.expiry.notification.scheduler.timebased.rule` 는 시간을 정의하는 정규 표현식입니다. 위의 예에서는 00시간 후에 스케줄러 작업을 시작합니다.
* If `send_email` 가 로 설정되어 있습니다. `true`, 자산 생성자 (특정 자산을 업로드하는 사람) [!DNL Assets])은 자산이 만료되면 이메일을 받습니다.
* 스케줄러의 한 이터레이션에서 만료된 최대 자산 수는 속성의 값입니다 `asset_expired_limit`.
* 작업을 주기적으로 실행하려면 속성 값을 설정합니다 `cq.dam.expiry.notification.scheduler.istimebased` 로서의 `false` 속성 값을 설정하고 `cq.dam.expiry.notification.scheduler.period.rule` 시간(초)으로

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1. For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## 자산 상태 {#asset-states}

다음 [!DNL Assets] 콘솔에 자산의 다양한 상태가 표시될 수 있습니다. 특정 자산의 현재 상태에 따라 해당 카드 보기에는 해당 상태를 설명하는 레이블(예: 만료됨, 게시됨, 승인됨, 거부됨)이 표시됩니다.

1. 에서 [!DNL Assets] 사용자 인터페이스에서 자산을 선택합니다.

1. 선택 **[!UICONTROL 게시]** 를 클릭합니다. 표시되지 않으면 [!UICONTROL 게시] 도구 모음에서 옵션을 클릭하여 **[!UICONTROL 자세히]** 도구 모음에서 **[!UICONTROL 게시]** 선택 사항입니다.

1. 선택 **[!UICONTROL 게시]** 메뉴에서 확인 대화 상자를 닫습니다.

1. 선택 모드를 종료합니다. 자산에 대한 게시 상태가 카드 보기에서 자산 축소판 아래에 표시됩니다. 목록 보기에서 게시됨 열에는 자산이 게시된 시간이 표시됩니다.

1. 해당 자산 세부 사항 페이지를 표시하려면 [!DNL Assets] 인터페이스, 자산 선택 및 클릭 **[!UICONTROL 속성]**.

1. 에서 [!UICONTROL 고급] 탭에서 자산의 만료 날짜를 설정합니다. **[!UICONTROL 만료]** 필드.

1. 클릭 **[!UICONTROL 저장]** 을 클릭한 다음 **[!UICONTROL 닫기]** 자산 콘솔을 표시합니다.

1. 자산에 대한 게시 상태는 카드 보기에서 자산 축소판 아래에 있는 만료된 상태를 나타냅니다. 목록 보기에서 자산의 상태가 **[!UICONTROL 만료됨]**.

1. 에서 [!DNL Assets] 콘솔에서 폴더를 선택하고 폴더에 검토 작업을 만듭니다.

1. 검토 작업에서 자산을 검토 및 승인/거부하고 **[!UICONTROL 완료]**.

1. 검토 작업을 만든 폴더로 이동합니다. 승인/거부한 자산의 상태가 카드 보기의 맨 아래에 표시됩니다. 목록 보기에서 승인 및 만료 상태가 적절한 열에 표시됩니다.

1. 해당 상태에 따라 자산을 검색하려면 다음을 클릭합니다 **[!UICONTROL 검색]** 검색 창을 표시합니다.

1. 선택 `Return` 을(를) 클릭합니다. [!DNL Experience Manager].

1. 검색 패널에서 **[!UICONTROL 게시 상태]** 을(를) 선택합니다. **[!UICONTROL 게시됨]** 에서 게시된 자산을 검색하려면 [!DNL Assets].

1. 승인되거나 거부된 자산을 검색하려면 **[!UICONTROL 승인 상태]** 적절한 옵션을 선택합니다.

1. 만료 상태를 기준으로 자산을 검색하려면 을(를) 선택합니다 **[!UICONTROL 만료 상태]** 검색 패널에서 해당 옵션을 선택합니다.

1. 다양한 검색 패싯에서 상태 조합을 기반으로 자산을 검색할 수도 있습니다. 예를 들어, 검토 작업에서 승인되고 만료되지 않은 게시된 자산을 검색할 수 있습니다. 이러한 자산을 검색하려면 검색 패싯에서 적절한 옵션을 선택합니다.

## Digital Rights Management [!DNL Assets] {#digital-rights-management-in-assets-1}

DRM 기능은 라이선스 자산을 [!DNL Assets].

보호된 자산을 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 입력하면 라이센스 계약에 동의하도록 라이센스 페이지로 리디렉션됩니다. 사용권 계약에 동의하지 않으면 **[!UICONTROL 다운로드]** 옵션을 사용할 수 없습니다.

선택한 항목에 여러 개의 보호된 자산이 포함되어 있는 경우 한 번에 한 개의 자산을 선택하고 사용권 계약에 동의한 다음 자산 다운로드를 계속 진행합니다.

다음 조건 중 하나가 충족되면 자산이 보호된 것으로 간주됩니다.

* 자산 메타데이터 속성 `xmpRights:WebStatement` 자산에 대한 사용권 계약이 들어 있는 페이지의 경로를 가리킵니다.
* 자산 메타데이터 속성 값 `adobe_dam:restrictions` 는 사용권 계약을 지정하는 원시 HTML입니다.

>[!NOTE]
>
>위치 `/etc/dam/drm/licences` 는 이전 릴리스에서 라이센스를 저장하는 데 사용됩니다. [!DNL Experience Manager]. 위치는 이제 더 이상 사용되지 않습니다. 라이센스 페이지를 만들거나 수정하거나 이전 페이지에서 페이지를 포팅하는 경우 [!DNL Experience Manager] 릴리스, Adobe은 이러한 자산을 `/apps/settings/dam/drm/licenses` 또는 `/conf/*/settings/dam/drm/licenses` 위치.

### DRM 보호 자산 다운로드 {#downloading-drm-assets}

1. 카드 보기에서 다운로드할 자산을 선택하고 선택합니다 **[!UICONTROL 다운로드]**.
1. In the **[!UICONTROL Copyright Management]** page, select the asset you want to download from the list.
1. 에서 [!UICONTROL 라이선스] 창 **[!UICONTROL 동의]**. 자산 옆에 확인 표시가 나타납니다. 을(를) 선택합니다 **[!UICONTROL 다운로드]** 선택 사항입니다.

   >[!NOTE]
   >
   >다음 **[!UICONTROL 다운로드]** 이 옵션은 보호된 자산에 대한 사용권 계약에 동의하도록 선택한 경우에만 활성화됩니다. 그러나 선택한 항목에 보호된 자산과 보호되지 않은 자산이 모두 포함되어 있으면 창과 창에 보호된 자산만 나열됩니다 **[!UICONTROL 다운로드]** 보호되지 않은 자산을 다운로드할 수 있는 옵션이 제공됩니다. To simultaneously accept license agreements for multiple protected assets, select the assets from the list and then choose **[!UICONTROL Agree]**.

1. 자산 또는 해당 표현물을 다운로드하려면 다음을 선택합니다 **[!UICONTROL 다운로드]** 클릭합니다.

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
