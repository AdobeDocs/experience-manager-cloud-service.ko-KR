---
title: 에셋 다운로드
description: 다음에서 자산 다운로드 [!DNL Adobe Experience Manager Assets] 다운로드 기능을 활성화하거나 비활성화합니다.
contentOwner: Vishabh Gupta
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: 80ac947976bab2b0bfedb4ff9d5dd4634de6b4fc
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 5%

---

# 다음에서 자산 다운로드 [!DNL Adobe Experience Manager] {#download-assets-from-aem}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/download-assets-from-aem.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 또는 다음에서 바로 자산에 대한 링크가 있는 이메일을 보낼 수 있습니다 [!DNL Adobe Experience Manager Assets]. 다운로드한 자산은 ZIP 파일에 번들로 제공됩니다. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

<!--
>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.
-->

다음 자산 유형은 다운로드할 수 없습니다. 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전 메뉴 세트.

다음 방법을 사용하여 Experience Manager에서 자산을 다운로드할 수 있습니다.

<!-- * [Link Share](#link-share-download) -->

* [Experience Manager 사용자 인터페이스](#download-assets)
* [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## 을 사용하여 자산 다운로드 [!DNL Experience Manager] 인터페이스 {#download-assets}

Experience Manager은 자산 수량 및 크기를 기반으로 다운로드 경험을 최적화합니다. 작은 파일은 사용자 인터페이스에서 실시간으로 다운로드됩니다. [!DNL Experience Manager] ZIP 아카이브에 단일 자산을 포함시키지 않고 원본 파일에 대한 단일 자산 요청을 직접 다운로드하여 더 빠르게 다운로드할 수 있습니다. Experience Manager은 비동기 요청이 있는 대규모 다운로드를 지원합니다. 100GB보다 큰 다운로드 요청은 각각 최대 크기가 100GB인 여러 ZIP 아카이브로 분할됩니다.

기본적으로 [!DNL Experience Manager] 에서 알림 트리거 [[!DNL Experience Manager] 받은 편지함](/help/sites-cloud/authoring/getting-started/inbox.md) 다운로드 아카이브 생성 시.

![받은 편지함 알림](assets/inbox-notification-for-large-downloads.png)


### 대규모 다운로드에 대한 이메일 알림 활성화 {#enable-emails-for-large-downloads}

비동기 다운로드는 다음 경우 트리거됩니다.

* 자산이 10개 이상인 경우
* 다운로드 크기가 100MB를 초과하는 경우
* 다운로드를 준비하는 데 30초 이상 걸리는 경우

백엔드에서 비동기 다운로드가 실행되는 동안 사용자는 Experience Manager에서 계속 탐색하고 작업할 수 있습니다. Experience Manager은 받은 편지함 Experience Manager 알림 외에도 다운로드 프로세스가 완료되면 사용자에게 알리는 이메일을 보낼 수 있습니다. 이 기능을 활성화하기 위해 관리자는 [SMTP 서버 연결 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email).

이메일 서비스가 구성되면 관리자와 사용자는 Experience Manager 인터페이스에서 이메일 알림을 활성화할 수 있습니다.

이메일 알림을 활성화하려면

1. 에 로그인합니다. [!DNL Experience Manager Assets].
1. 오른쪽 상단 모서리에서 사용자 아이콘을 클릭한 다음 을(를) 클릭합니다 **[!UICONTROL 내 환경 설정]** 사용자 환경설정 창을 열려면
1. 을(를) 선택합니다 **[!UICONTROL 자산 다운로드 이메일 알림]** 확인란을 선택하고 **[!UICONTROL 수락]**.

   ![enable-email-notifications-for-large-downloads](/help/assets/assets/enable-email-for-large-downloads.png)


자산을 다운로드하려면 다음 단계를 수행하십시오.

1. in [!DNL Experience Manager] 사용자 인터페이스, **[!UICONTROL 자산]** > **[!UICONTROL 파일]**.
1. 다운로드할 자산으로 이동합니다. 폴더를 선택하거나 폴더 내에서 하나 이상의 자산을 선택합니다. 도구 모음에서 **[!UICONTROL 다운로드]**.

   ![다음에서 자산을 다운로드할 때 사용할 수 있는 옵션 [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

1. 다운로드 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]** | 자산에 대해 다운로드한 모든 표현물을 포함하는 각 자산에 대한 폴더를 만들려면 이 옵션을 선택합니다. 선택하지 않으면, 각 자산(및 다운로드용으로 선택한 경우 해당 표현물)이 생성된 아카이브의 상위 폴더에 포함됩니다. |
   | **[!UICONTROL 이메일]** | 다른 사용자에게 이메일 알림(다운로드 링크가 포함됨)을 보내려면 이 옵션을 선택합니다. 수신자 사용자는 `dam-users` 그룹에 속해 있어야 합니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> 배포 중에 사용자 지정하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>다음 위치에 임차인별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL 자산]** | 이 옵션을 선택하여 자산을 원래 양식으로 다운로드합니다.<br>원본 자산에 하위 자산이 있는 경우 하위 자산 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 렌디션]** | 표현물은 자산의 이진 표현입니다. 자산에는 업로드된 파일의 표현인 기본 표현이 있습니다. 레프리젠테이션들을 수 있어요 <br> 이 옵션을 사용하여 다운로드할 표현물을 선택할 수 있습니다. 사용 가능한 표현물은 선택한 자산에 따라 다릅니다. |
   | **[!UICONTROL 스마트 자르기]** | 내에서 선택한 자산의 모든 스마트 자르기 렌디션을 다운로드하려면 이 옵션을 선택합니다 [!DNL Experience Manager]. 스마트 자르기 렌디션이 있는 zip 파일이 만들어지고 로컬 컴퓨터에 다운로드됩니다. |
   | **[!UICONTROL 동적 렌디션]** | 일련의 대체 표현물을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택하면, [이미지 사전 설정](/help/assets/dynamic-media/image-presets.md) 목록. <br>또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 이 옵션은 [!DNL Dynamic Media] 활성화되었습니다. |

1. 대화 상자에서 **[!UICONTROL 다운로드]**.

   큰 다운로드에 대해 이메일 알림이 활성화되면 보관된 zip 폴더의 다운로드 URL이 포함된 이메일이 받은 편지함에 나타납니다. 이메일에서 다운로드 링크를 클릭하여 zip 아카이브를 다운로드합니다.

   ![대규모 다운로드용 이메일 알림](/help/assets/assets/email-for-large-notification.png)

   또한 [!DNL Experience Manager] 받은 편지함.

   ![inbox-notifications-for-large-downloads](/help/assets/assets/inbox-notification-for-large-downloads.png)

## 링크 공유를 사용하여 공유된 자산 다운로드 {#link-share-download}

링크를 사용하여 자산을 공유하는 것은 관심 있는 사람이 로그인하지 않고도 이용할 수 있는 편리한 방법입니다 [!DNL Assets]. 자세한 내용은 [링크 공유 기능](/help/assets/share-assets.md#sharelink).

사용자가 공유 링크에서 자산을 다운로드하면, [!DNL Assets] 는 빠르고 중단 없는 다운로드를 제공하는 비동기 서비스를 사용합니다. 다운로드할 자산은 받은 편지함의 백그라운드에서 관리할 수 있는 파일 크기의 ZIP 아카이브로 전송됩니다. 더 큰 다운로드의 경우 다운로드가 100GB의 파일로 청크됩니다.

다음 [!UICONTROL 받은 편지함 다운로드] 각 아카이브의 처리 상태를 표시합니다. 처리가 완료되면 받은 편지함에서 아카이브를 다운로드할 수 있습니다.

![받은 편지함 다운로드](assets/link-sharing-download-inbox.png)

## 자산 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

의 기본 서블릿 [!DNL Experience Manager] 인증된 사용자가 자산의 ZIP 파일을 만들기 위해 임의로 대규모 동시 다운로드 요청을 발행할 수 있도록 해줍니다. 다운로드 준비에는 성능 문제가 있거나 서버와 네트워크에 과부하가 될 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS와 유사한 위험을 줄이려면 `AssetDownloadServlet` 게시 인스턴스에 대해 OSGi 구성 요소가 비활성화됩니다. 작성자 인스턴스에 다운로드 기능이 필요하지 않은 경우 작성자에 대한 서블릿을 비활성화합니다.

DAM에서 자산을 다운로드할 수 있도록 하려면 Asset Share Commons 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 허용된 다운로드 크기를 가능한 한 낮게 설정할 것을 권장합니다. 높은 값은 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 대상으로 하는 이름 지정 규칙(즉, `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 새 유형의 파일을 만듭니다 `nt:file` 명명된 이름 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. 채우기 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 다음을 포함합니다. 다운로드에 대한 최대 크기(바이트)를 값으로 설정합니다. `asset.download.prezip.maxcontentsize`. 아래 샘플은 ZIP 다운로드의 최대 크기가 100KB를 초과하지 않도록 구성합니다.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 비활성화 {#disable-asset-download-servlet}

다운로드 기능이 필요하지 않은 경우 DoS와 유사한 위험을 방지하기 위해 서블릿을 비활성화하십시오. 다음 `Asset Download Servlet` 는 [!DNL Experience Manager] dispatcher 구성을 업데이트하여 모든 자산 다운로드 요청을 차단하여 인스턴스를 작성 및 게시합니다. OSGi 콘솔을 통해 직접 서블릿을 수동으로 비활성화할 수도 있습니다.

1. 디스패처 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성 및 새 규칙을 [필터 섹션](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

## 팁 및 제한 사항 {#tips-limitations}

* 빈 폴더를 다운로드하면, [!DNL Experience Manager] zip 아카이브 만들기에 대한 성공 메시지를 전달하지만 아카이브는 만들어지지 않습니다.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [에셋이 지원되는 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 에셋](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [DRM 보호 자산 다운로드](drm.md)
>* [Win 또는 Mac 데스크탑에서 Experience Manager 데스크탑 앱을 사용하여 자산 다운로드](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [지원되는 Adobe Creative Cloud 앱 내에서 Adobe 자산 링크를 사용하여 자산을 다운로드합니다](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)

