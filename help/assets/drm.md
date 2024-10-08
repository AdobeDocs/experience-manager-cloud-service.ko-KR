---
title: ' [!DNL Assets]의 Digital Rights Management'
description: ' [!DNL Experience Manager] as a [!DNL Cloud Service]에서 사용 허가된 자산에 대한 자산 만료 상태 및 정보를 관리하는 방법을 알아봅니다.'
contentOwner: AG
feature: Asset Management,DRM
role: User, Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 6%

---

# 디지털 에셋 Digital Rights Management {#digital-rights-management-in-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/drm.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

디지털 에셋은 종종 사용 약관 및 기간을 지정하는 라이선스와 연결됩니다. [!DNL Experience Manager] 플랫폼을 사용하면 자산 만료 정보 및 라이선스 정보를 효율적으로 관리할 수 있습니다.

## 에셋 만료 {#asset-expiration}

에셋에 대한 라이선스 요구 사항을 적용하려면 에셋 만료 정보를 사용하십시오. 만료 정보는 게시된 에셋이 만료될 때 게시되지 않도록 하여 라이센스 위반을 방지합니다. 관리자 권한이 없는 사용자는 만료된 에셋을 편집, 복사, 이동, 게시 및 다운로드할 수 없습니다.

다음 위치에서 에셋의 만료 상태를 볼 수 있습니다.

* **카드 보기**: 만료된 에셋의 경우 카드의 플래그가 만료되었음을 나타냅니다.
* **목록 보기**: 만료된 에셋의 경우 **[!UICONTROL 상태]** 열에 **[!UICONTROL 만료됨]** 배너가 표시됩니다.
* **타임라인**: 타임라인에서 자산의 만료 상태를 볼 수 있습니다. 에셋을 선택하고 타임라인 을 선택합니다.
* **참조 레일**: **[!UICONTROL 참조]** 레일에서 자산의 만료 상태를 볼 수도 있습니다. 복합 에셋과 참조된 하위 에셋, 컬렉션 및 프로젝트 간의 에셋 만료 상태 및 관계를 관리합니다.

에셋에 대한 참조 웹 페이지 및 복합 에셋을 보려면 다음 단계를 수행합니다.

1. 에셋으로 이동하여 에셋을 선택하고 ![왼쪽 레일 콘텐츠 참조 아이콘](assets/do-not-localize/content-rail-icon.png)을 클릭합니다. 왼쪽 레일이 열립니다.
1. 왼쪽 레일에서 **[!UICONTROL 참조]**&#x200B;를 선택합니다.
1. 만료된 에셋의 경우 [!UICONTROL 참조]에 만료 상태가 **[!UICONTROL 에셋이 만료됨]**(으)로 표시됩니다. 에셋이 만료된 경우 [!UICONTROL 참조] 레일에 **[!UICONTROL 에셋이 만료된 하위 Assets]** 상태가 표시됩니다.

### 만료된 에셋 검색 {#search-expired-assets}

만료된 하위 자산을 포함하여 만료된 자산을 검색하려면 다음 단계를 수행합니다.

1. [!DNL Assets] 콘솔에서 도구 모음의 **[!UICONTROL 검색]**&#x200B;을 클릭하고 `Enter`을 누릅니다.

1. GlobalNav 아이콘을 클릭하고 **[!UICONTROL 만료 상태]** 옵션을 선택합니다.

1. **[!UICONTROL 만료됨]**&#x200B;을(를) 선택합니다. 검색 결과에 만료된 에셋이 표시됩니다.

**[!UICONTROL 만료됨]** 옵션을 선택하면 [!DNL Assets] 콘솔에는 복합 에셋에서 참조하는 만료된 에셋 및 하위 에셋만 표시됩니다. 만료된 하위 에셋을 참조하는 복합 에셋은 하위 에셋이 만료된 직후에 표시되지 않습니다. 대신 [!DNL Experience Manager]이(가) 다음에 스케줄러가 실행될 때 만료된 하위 자산을 참조한다는 것을 감지하면 표시됩니다.

게시된 에셋의 만료 날짜를 현재 스케줄러 주기보다 빠른 날짜로 수정할 수 있습니다. 하지만 다음에 실행될 때 [!DNL Experience Manager]에서 해당 에셋을 만료된 에셋으로 검색하고 보고서에 해당 상태를 반영합니다. 시간대가 다른 사용자에 대해 에셋의 만료 날짜가 다르게 표시됩니다.

또한 오류가 발생하여 스케줄러가 현재 주기에서 만료된 에셋을 감지할 수 없는 경우 스케줄러는 다음 주기에서 이러한 에셋을 다시 검사하고 만료된 상태를 감지합니다.

[!DNL Assets] 콘솔에서 만료된 하위 자산과 함께 참조 복합 자산을 표시할 수 있도록 하려면 [!DNL Experience Manager]에서 **[!UICONTROL Adobe CQ DAM 만료 알림]** 워크플로우를 구성하십시오. 시간 기반 스케줄러는 자산이 하위 자산으로 만료되었는지 여부를 특정 시간에 확인하기 위해 작업을 예약합니다. 작업이 완료되면 만료된 하위 에셋 및 참조된 에셋이 검색 결과에 만료된 것으로 표시됩니다.

1. 환경과 연결된 [!DNL Cloud Manager] Git 저장소에 액세스합니다.
1. 다음 내용이 포함된 `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` 파일을 리포지토리에 커밋합니다.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1.  [!DNL Experience Manager] as a [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md)에서 [OSGi 구성을 수행하는 방법 지침을 따르십시오.

다음 속성을 사용하여 스케줄러를 구성할 수 있습니다.

* `cq.dam.expiry.notification.scheduler.istimebased` 속성의 `true` 값이 스케줄러를 시작합니다. * 속성 `cq.dam.expiry.notification.scheduler.timebased.rule`의 값은 시간을 정의하는 정규식입니다. 위의 예에서는 00시간에 스케줄러 작업을 시작합니다.
* `send_email`이(가) `true`(으)로 설정된 경우 에셋이 만료되면 에셋 생성자(특정 에셋을 [!DNL Assets]에 업로드하는 사람)에게 전자 메일이 전송됩니다.
* 스케줄러의 한 반복에서 만료된 최대 자산 수는 `asset_expired_limit` 속성의 값입니다.
* 작업을 주기적으로 실행하려면 `cq.dam.expiry.notification.scheduler.istimebased` 속성의 값을 `false`(으)로 설정하고 `cq.dam.expiry.notification.scheduler.period.rule` 속성의 값을 초 단위로 설정합니다.

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1. For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## 자산 상태 {#asset-states}

[!DNL Assets] 콘솔에서는 자산의 다양한 상태를 표시할 수 있습니다. 특정 에셋의 현재 상태에 따라 해당 카드 보기에는 만료됨, 게시됨, 승인됨, 거부됨 등과 같은 에셋 상태를 설명하는 레이블이 표시됩니다.

1. [!DNL Assets] 사용자 인터페이스에서 자산을 선택합니다.

1. 도구 모음에서 **[!UICONTROL Publish]**&#x200B;을(를) 선택합니다. 도구 모음에 [!UICONTROL Publish] 옵션이 표시되지 않으면 도구 모음에서 **[!UICONTROL 자세히]**&#x200B;를 클릭하고 **[!UICONTROL Publish]** 옵션을 찾습니다.

1. 메뉴에서 **[!UICONTROL Publish]**&#x200B;을(를) 선택한 다음 확인 대화 상자를 닫습니다.

1. 선택 모드를 종료합니다. 에셋의 게시 상태는 카드 보기의 에셋 썸네일 하단에 나타납니다. 목록 보기의 게시됨 열에는 에셋이 게시된 시간이 표시됩니다.

1. 자산 세부 정보 페이지를 표시하려면 [!DNL Assets] 인터페이스에서 자산을 선택하고 **[!UICONTROL 속성]**&#x200B;을(를) 클릭합니다.

1. [!UICONTROL 고급] 탭에서 **[!UICONTROL 만료]** 필드에서 에셋의 만료 날짜를 설정합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭한 다음 **[!UICONTROL 닫기]**&#x200B;를 클릭하여 자산 콘솔을 표시합니다.

1. 에셋의 게시 상태는 카드 보기의 에셋 썸네일 하단에 만료됨 상태를 나타냅니다. 목록 보기에서 에셋의 상태가 **[!UICONTROL 만료됨]**(으)로 표시됩니다.

1. [!DNL Assets] 콘솔에서 폴더를 선택하고 폴더에 대한 검토 작업을 만듭니다.

1. 검토 작업에서 에셋을 검토하고 승인/거부하고 **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

1. 검토 작업을 생성한 폴더로 이동합니다. 승인/거부한 에셋의 상태가 카드 보기의 맨 아래에 표시됩니다. 목록 보기에서 승인 및 만료 상태가 적절한 열에 표시됩니다.

1. 상태를 기준으로 자산을 검색하려면 **[!UICONTROL 검색]**&#x200B;을 클릭하여 검색 창을 표시합니다.

1. `Return`을(를) 선택하고 [!DNL Experience Manager]을(를) 클릭합니다.

1. 검색 패널에서 **[!UICONTROL Publish 상태]**&#x200B;를 클릭하고 **[!UICONTROL 게시됨]**&#x200B;을(를) 선택하여 [!DNL Assets]에서 게시된 에셋을 검색합니다.

1. 승인 또는 거부된 자산을 검색하려면 **[!UICONTROL 승인 상태]**&#x200B;를 선택하고 적절한 옵션을 선택하십시오.

1. 만료 상태를 기준으로 자산을 검색하려면 검색 패널에서 **[!UICONTROL 만료 상태]**&#x200B;를 선택하고 적절한 옵션을 선택합니다.

1. 다양한 검색 패싯 아래의 상태 조합을 기반으로 에셋을 검색할 수도 있습니다. 예를 들어 검토 작업에서 승인되고 만료되지 않은 게시된 에셋을 검색할 수 있습니다. 이러한 에셋을 검색하려면 검색 패싯에서 적절한 옵션을 선택합니다.

## [!DNL Assets]의 Digital Rights Management {#digital-rights-management-in-assets-1}

DRM 기능은 [!DNL Assets]에서 라이선스가 있는 에셋을 다운로드하기 전에 라이선스 계약 수락을 시행합니다.

보호된 자산을 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 클릭하면 사용권 계약에 동의하도록 라이선스 페이지로 리디렉션됩니다. 사용권 계약에 동의하지 않으면 **[!UICONTROL 다운로드]** 옵션을 사용할 수 없습니다.

선택 항목에 여러 개의 보호된 자산이 포함된 경우 한 번에 하나의 자산을 선택하고 라이선스 계약에 동의한 다음 자산 다운로드를 진행합니다.

다음 조건 중 하나가 충족되면 자산이 보호되는 것으로 간주됩니다.

* 에셋 메타데이터 속성 `xmpRights:WebStatement`은(는) 에셋에 대한 라이선스 계약이 포함된 페이지의 경로를 가리킵니다.
* 에셋 메타데이터 HTML `adobe_dam:restrictions`의 값이 사용권 계약을 지정하는 원시 속성입니다.

>[!NOTE]
>
>위치 `/etc/dam/drm/licences`은(는) [!DNL Experience Manager]의 이전 릴리스에서 라이선스를 저장하는 데 사용되었습니다. 해당 위치는 이제 더 이상 사용되지 않습니다. Adobe 라이선스 페이지를 만들거나 수정하거나 이전 [!DNL Experience Manager] 릴리스의 페이지를 포트하는 경우 `/apps/settings/dam/drm/licenses` 또는 `/conf/*/settings/dam/drm/licenses` 위치에 해당 에셋을 저장하는 것이 좋습니다.

### DRM 보호 에셋 다운로드 {#downloading-drm-assets}

1. 카드 보기에서 다운로드할 자산을 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 선택합니다.
1. In the **[!UICONTROL Copyright Management]** page, select the asset you want to download from the list.
1. [!UICONTROL 라이선스] 창에서 **[!UICONTROL 동의]**&#x200B;를 선택합니다. 자산 옆에 확인 표시가 나타납니다. **[!UICONTROL 다운로드]** 옵션을 선택하십시오.

   >[!NOTE]
   >
   >**[!UICONTROL 다운로드]** 옵션은 보호된 자산에 대한 사용권 계약에 동의하도록 선택한 경우에만 사용할 수 있습니다. 그러나 선택한 항목이 보호된 자산과 보호되지 않은 자산을 모두 포함하는 경우 보호된 자산만 창에 나열되며 **[!UICONTROL 다운로드]** 옵션을 사용하여 보호되지 않은 자산을 다운로드할 수 있습니다. To simultaneously accept license agreements for multiple protected assets, select the assets from the list and then choose **[!UICONTROL Agree]**.

1. 에셋 또는 해당 렌디션을 다운로드하려면 대화 상자에서 **[!UICONTROL 다운로드]**&#x200B;를 선택합니다.

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
