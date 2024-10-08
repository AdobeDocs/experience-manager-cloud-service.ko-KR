---
title: 자산 다운로드
description: ' [!DNL Adobe Experience Manager Assets] 에서 자산을 다운로드하고 다운로드 기능을 활성화하거나 비활성화합니다.'
contentOwner: Vishabh Gupta
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1354'
ht-degree: 4%

---

# [!DNL Adobe Experience Manager]에서 에셋 다운로드 {#download-assets-from-aem}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/download-assets-from-aem.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

정적 및 동적 변환을 포함한 에셋을 다운로드할 수 있습니다. 또는 [!DNL Adobe Experience Manager Assets]에서 직접 에셋에 대한 링크가 포함된 전자 메일을 보낼 수 있습니다. 다운로드한 에셋은 ZIP 파일에 번들로 제공됩니다. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

<!--
>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.
-->

이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전 메뉴 세트와 같은 에셋 유형은 다운로드할 수 없습니다.

다음 방법을 사용하여 Experience Manager에서 에셋을 다운로드할 수 있습니다.

<!-- * [Link Share](#link-share-download) -->

* [Experience Manager 사용자 인터페이스](#download-assets)
* [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [데스크톱 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## [!DNL Experience Manager] 인터페이스를 사용하여 에셋 다운로드 {#download-assets}

Experience Manager은 에셋 수량 및 크기를 기반으로 다운로드 경험을 최적화합니다. 사용자 인터페이스에서 실시간으로 더 작은 파일이 다운로드됩니다. [!DNL Experience Manager]은(는) 빠른 다운로드를 위해 ZIP 아카이브에 단일 자산을 포함시키지 않고 원본 파일에 대한 단일 자산 요청을 직접 다운로드합니다. Experience Manager은 비동기 요청으로 대규모 다운로드를 지원합니다. 100GB보다 큰 다운로드 요청은 최대 크기가 각각 100MB인 여러 ZIP 아카이브로 분할됩니다.

기본적으로 [!DNL Experience Manager]은(는) 다운로드 보관 파일 생성 시 [[!DNL Experience Manager] 받은 편지함](/help/sites-cloud/authoring/inbox.md)에서 알림을 트리거합니다.

![받은 편지함 알림](assets/inbox-notification-for-large-downloads.png)


### 대량 다운로드에 대한 이메일 알림 활성화 {#enable-emails-for-large-downloads}

비동기 다운로드는 다음 경우 트리거됩니다.

* 자산이 10개 이상인 경우
* 다운로드 크기가 100MB를 초과하는 경우
* 다운로드가 준비되는 데 30초 이상 걸리는 경우

비동기 다운로드가 백엔드에서 실행되는 동안 사용자는 계속 탐색하고 Experience Manager에서 더 작업할 수 있습니다. Experience Manager 받은 편지함 알림 외에도 Experience Manager은 다운로드 프로세스가 완료되면 사용자에게 알리기 위해 이메일을 보낼 수 있습니다. 이 기능을 사용하려면 관리자는 [SMTP 서버 연결을 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email)하여 전자 메일 서비스를 구성할 수 있습니다.

이메일 서비스가 구성되면 관리자 및 사용자는 Experience Manager 인터페이스에서 이메일 알림을 활성화할 수 있습니다.

이메일 알림을 활성화하려면:

1. [!DNL Experience Manager Assets]에 로그인합니다.
1. 오른쪽 상단에서 사용자 아이콘을 클릭한 다음 **[!UICONTROL 내 환경 설정]**&#x200B;을 클릭하여 사용자 환경 설정 창을 엽니다.
1. **[!UICONTROL 자산 다운로드 전자 메일 알림]** 확인란을 선택하고 **[!UICONTROL 수락]**&#x200B;을 클릭합니다.

   ![대량 다운로드에 대해 이메일 알림 사용](/help/assets/assets/enable-email-for-large-downloads.png)


에셋을 다운로드하려면 다음 단계를 따르십시오.

1. [!DNL Experience Manager] 사용자 인터페이스에서 **[!UICONTROL Assets]** > **[!UICONTROL 파일]**&#x200B;을(를) 클릭합니다.
1. 다운로드할 자산으로 이동합니다. 폴더를 선택하거나 폴더 내의 에셋을 하나 이상 선택합니다. 도구 모음에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)에서 에셋을 다운로드할 때 ![사용 가능한 옵션

1. 다운로드 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더를 만듭니다]** | 에셋에 대해 다운로드한 모든 렌디션이 포함된 각 에셋에 대한 폴더를 생성하려면 이 옵션을 선택합니다. 선택하지 않으면 각 에셋(및 다운로드를 위해 선택한 경우 렌디션)이 생성된 아카이브의 상위 폴더에 포함됩니다. |
   | **[!UICONTROL 이메일]** | 다른 사용자에게 이메일 알림(다운로드에 대한 링크 포함)을 보내려면 이 옵션을 선택합니다. 받는 사람 사용자는 `dam-users` 그룹의 구성원이어야 합니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> 배포 중 사용자 정의하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul>다음 위치에 테넌트별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> |
   | **[!UICONTROL 자산]** | 자산을 원래 양식으로 다운로드하려면 이 옵션을 선택합니다.<br>원본 에셋에 하위 에셋이 있는 경우 하위 에셋 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 표현물]** | 렌디션은 에셋의 바이너리 표현입니다. Assets에는 업로드된 파일의 기본 표현이 있습니다. 그들은 얼마든지 표현을 할 수 있다. <br> 이 옵션을 사용하면 다운로드하려는 표현물을 선택할 수 있습니다. 사용 가능한 렌디션은 선택한 에셋에 따라 다릅니다. |
   | **[!UICONTROL 스마트 자르기]** | [!DNL Experience Manager] 내에서 선택한 에셋의 모든 스마트 자르기 렌디션을 다운로드하려면 이 옵션을 선택하십시오. 스마트 자르기 렌디션이 포함된 zip 파일이 생성되고 로컬 컴퓨터에 다운로드됩니다. |
   | **[!UICONTROL 동적 렌디션]** | 일련의 대체 변환을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 [이미지 사전 설정](/help/assets/dynamic-media/image-presets.md) 목록에서 선택하여 동적으로 만들 변환도 선택합니다. <br>또한 측정 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 옵션은 [!DNL Dynamic Media]을(를) 활성화한 경우에만 사용할 수 있습니다. |

1. 대화 상자에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   대량 다운로드에 대해 이메일 알림이 활성화된 경우 보관된 zip 폴더의 다운로드 URL이 포함된 이메일이 받은 편지함에 나타납니다. 이메일의 다운로드 링크를 클릭하여 zip 아카이브를 다운로드합니다.

   ![대량 다운로드를 위한 이메일 알림](/help/assets/assets/email-for-large-notification.png)

   [!DNL Experience Manager] 받은 편지함에서 알림을 볼 수도 있습니다.

   ![대량 다운로드를 위한 받은 편지함 알림](/help/assets/assets/inbox-notification-for-large-downloads.png)

## 링크 공유를 사용하여 공유된 에셋 다운로드 {#link-share-download}

링크를 사용하여 자산을 공유하면 관심 있는 사람들이 [!DNL Assets]에 로그인할 필요 없이 자산을 편리하게 사용할 수 있습니다. [링크 공유 기능](/help/assets/share-assets.md#sharelink)을 참조하세요.

사용자가 공유 링크에서 자산을 다운로드할 때 [!DNL Assets]은(는) 더 빠르고 중단 없는 다운로드를 제공하는 비동기 서비스를 사용합니다. 다운로드할 자산은 받은 편지함의 백그라운드에서 관리할 수 있는 파일 크기의 ZIP 아카이브에 큐에 저장됩니다. 다운로드 용량이 큰 경우 다운로드가 100GB의 파일로 청크 처리됩니다.

[!UICONTROL 받은 편지함 다운로드]에 각 보관 파일의 처리 상태가 표시됩니다. 처리가 완료되면 받은 편지함에서 아카이브를 다운로드할 수 있습니다.

![받은 편지함 다운로드](assets/link-sharing-download-inbox.png)

## 에셋 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

[!DNL Experience Manager]의 기본 서블릿을 사용하면 인증된 사용자가 임의로 큰 동시 다운로드 요청을 발행하여 자산의 ZIP 파일을 만들 수 있습니다. 다운로드 준비는 성능에 영향을 주거나 서버와 네트워크에 과부하를 줄 수도 있습니다. 이 기능으로 인해 발생할 수 있는 DoS 유사 위험을 완화하기 위해 게시 인스턴스에 대해 `AssetDownloadServlet` OSGi 구성 요소를 사용할 수 없습니다. 작성자 인스턴스에서 다운로드 기능이 필요하지 않은 경우 작성자에서 서블릿을 비활성화합니다.

DAM에서 에셋을 다운로드할 수 있도록 하려면 Asset Share Commons 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화하십시오. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 허용되는 다운로드 크기를 가능한 한 낮게 설정할 것을 권장합니다. 값이 높으면 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 대상으로 하는 명명 규칙을 사용하여 폴더 만들기(즉, `config.publish`):

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 이름이 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`인 `nt:file` 형식의 파일을 만듭니다.
1. `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`을(를) 다음으로 채웁니다. 다운로드의 최대 크기(바이트)를 `asset.download.prezip.maxcontentsize` 값으로 설정합니다. 아래 샘플은 ZIP 다운로드의 최대 크기를 100KB 이하로 구성합니다.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 에셋 다운로드 서블릿 비활성화 {#disable-asset-download-servlet}

다운로드 기능이 필요하지 않은 경우 서블릿을 비활성화하여 DoS와 유사한 위험을 방지하십시오. 자산 다운로드 요청을 차단하도록 Dispatcher 구성을 업데이트하여 [!DNL Experience Manager] 작성자 및 게시 인스턴스에서 `Asset Download Servlet`을(를) 비활성화할 수 있습니다. OSGi 콘솔을 통해 서블릿을 수동으로 비활성화할 수도 있습니다.

1. Dispatcher 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성을 편집하고 [필터 섹션](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring)에 새 규칙을 추가하십시오.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

## OnTime 또는 OffTime 렌디션 {#on-off-time-rendition}

`OnOffTimeAssetAccessFilter` 서비스를 사용하려면 OSGi 구성을 만들어야 합니다. 이 서비스를 사용하면 설정/해제 시간 설정에 따라 에셋 자체 외에도 렌디션 및 메타데이터에 대한 액세스를 차단할 수 있습니다. OSGi 구성은 `com.day.cq.dam.core.impl.servlet.OnOffTimeAssetAccessFilter`에 대한 구성이어야 합니다. 아래 단계를 따르십시오.

1. Git의 프로젝트 코드에서 `/apps/system/config/com.day.cq.dam.core.impl.servlet.OnOffTimeAssetAccessFilter.cfg.json`에 구성 파일을 만듭니다. 파일에는 해당 OSGi 구성 요소에 대한 빈 OSGi 구성을 의미하는 `{}`이(가) 포함되어야 합니다. 이 작업을 수행하면 서비스가 활성화됩니다.
1. [!DNL Cloud Manager]을(를) 통해 이 새 구성을 포함한 코드를 배포합니다.
1. 배포되면 에셋의 설정/해제 시간 설정에 따라 렌디션 및 메타데이터에 액세스할 수 있습니다. 현재 날짜 또는 시간이 설정 시간 이전이나 해제 시간 이후인 경우 오류 메시지가 표시됩니다.
빈 OSGi 구성을 추가하는 방법에 대한 자세한 내용은 이 [안내서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=en)를 참조하십시오.

## 팁 및 제한 사항 {#tips-limitations}

* 빈 폴더를 다운로드하는 경우 [!DNL Experience Manager]에 ZIP 보관 파일 만들기에 대한 성공 메시지가 표시되지만 보관 파일은 만들어지지 않습니다.

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [DRM 보호 에셋 다운로드](drm.md)
>* [Win 또는 Mac 데스크톱에서 Experience Manager 데스크톱 앱을 사용하여 에셋 다운로드](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [지원되는 Adobe Creative Cloud 앱 내에서 Assets 링크 Adobe을 사용하여 에셋을 다운로드합니다](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)
