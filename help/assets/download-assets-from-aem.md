---
title: 자산 다운로드
description: ' [!DNL Adobe Experience Manager Assets] 에서 자산을 다운로드하고 다운로드 기능을 활성화하거나 비활성화합니다.'
contentOwner: AG
feature: 자산 관리
role: Business Practitioner
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: 715e6e56294172989aa8e512b5cbc6679312e379
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 4%

---

# [!DNL Adobe Experience Manager] {#download-assets-from-aem}에서 자산 다운로드

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 또는 [!DNL Adobe Experience Manager Assets]에서 직접 자산에 대한 링크가 있는 이메일을 보낼 수 있습니다. 다운로드한 자산은 ZIP 파일에 번들로 제공됩니다. 압축 ZIP 파일의 최대 파일 크기는 내보내기 작업의 1GB입니다. 내보내기 작업당 최대 500개의 총 자산이 허용됩니다.

>[!NOTE]
>
>전자 메일의 수신자는 전자 메일 메시지의 ZIP 다운로드 링크에 액세스하려면 `dam-users` 그룹의 구성원이어야 합니다. 자산을 다운로드하려면 구성원이 자산 다운로드를 트리거하는 워크플로우를 시작할 권한이 있어야 합니다.

자산 유형 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전 세트는 다운로드할 수 없습니다.

다음 방법을 사용하여 Experience Manager 자산을 다운로드할 수 있습니다.

* [Experience Manager 사용자 인터페이스](#download-in-aem)
* [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## [!DNL Experience Manager] 인터페이스를 사용하여 자산 다운로드 {#download-in-aem}

비동기 다운로드 서비스는 대형 자산을 원활하게 다운로드할 수 있는 프레임워크를 제공합니다. 사용자 인터페이스에서 작은 파일이 실시간으로 다운로드됩니다. 큰 파일은 비동기식으로 다운로드되고 사용자는 받은 편지함의 Experience Manager 알림을 통해 완료 알림을 받게 됩니다. [Experience Manager 받은 편지함 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html)를 참조하십시오.

![다운로드 알림](assets/download-notification.png)

*그림:받은 편지함을 통해 알림을  [!DNL Experience Manager] 다운로드합니다.*

다음 경우 비동기 다운로드가 트리거됩니다.

* 자산을 10개 이상 다운로드하거나 100MB를 초과하는 경우.
* 다운로드를 준비하는 데 30초 이상 걸리는 경우

자산을 다운로드하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager] 사용자 인터페이스에서 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 클릭합니다.
1. 다운로드할 자산으로 이동합니다. 폴더를 선택하거나 폴더 내에서 하나 이상의 자산을 선택합니다. 도구 모음에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   ![다음에서 자산을 다운로드할 때 사용할 수 있는 옵션  [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

   *그림:다운로드 대화 상자 옵션.*

1. 다운로드 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]** | 다운로드할 각 자산을 자산의 상위 폴더 아래에 중첩된 하위 폴더에 로컬 컴퓨터의 한 폴더로 포함하려면 이 옵션을 선택합니다. 이 옵션이 *선택되지 않으면 기본적으로 폴더 계층 구조가 무시되고 모든 자산이 로컬 컴퓨터의 한 폴더로 다운로드됩니다.* |
   | **[!UICONTROL 이메일]** | 수신자에게 이메일 알림을 전송하려면 이 옵션을 선택합니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> 배포 중에 사용자 지정하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>다음 위치에 임차인별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL 자산]** | 이 옵션을 선택하면 변환 없이 자산을 원래 양식으로 다운로드합니다.<br>원본 자산에 하위 자산이 있는 경우 하위 자산 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 렌디션]** | 표현물은 자산의 이진 표현입니다. 자산에는 업로드된 파일의 표현인 기본 표현이 있습니다. 레프리젠테이션들을 수 있어요 <br> 이 옵션을 사용하여 다운로드할 표현물을 선택할 수 있습니다. 사용 가능한 표현물은 선택한 자산에 따라 다릅니다. |
   | **[!UICONTROL 스마트 자르기]** | [!DNL Experience Manager] 내에서 선택한 자산의 모든 스마트 자르기 렌디션을 다운로드하려면 이 옵션을 선택합니다. 스마트 자르기 렌디션이 있는 zip 파일이 만들어지고 로컬 컴퓨터에 다운로드됩니다. |
   | **[!UICONTROL 동적 렌디션]** | 일련의 대체 표현물을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택하는 경우 [이미지 사전 설정](/help/assets/dynamic-media/image-presets.md) 목록에서 선택하여 동적으로 만들 표현물도 선택합니다. <br>또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 이 옵션은 [!DNL Dynamic Media] 이 활성화된 경우에만 사용할 수 있습니다. |

1. 대화 상자에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

## 자산 다운로드 서블릿 {#enable-asset-download-servlet} 활성화

[!DNL Experience Manager]의 기본 서블릿을 사용하면 인증된 사용자가 자산의 ZIP 파일을 만들기 위해 임의로 대규모 동시 다운로드 요청을 발행할 수 있습니다. 다운로드 준비에는 성능 문제가 있거나 서버와 네트워크에 과부하가 될 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS와 유사한 위험을 완화하려면 게시 인스턴스에 대해 `AssetDownloadServlet` OSGi 구성 요소가 비활성화됩니다. 작성자 인스턴스에 다운로드 기능이 필요하지 않은 경우 작성자에 대한 서블릿을 비활성화합니다.

DAM에서 자산을 다운로드할 수 있도록 하려면 Asset Share Commons 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 허용된 다운로드 크기를 가능한 한 낮게 설정할 것을 권장합니다. 높은 값은 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 대상으로 하는 이름 지정 규칙(즉, `config.publish`)이 있는 폴더를 만듭니다.

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 유형의 새 파일을 만듭니다.`nt:file`
1. `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 을(를) 다음으로 채웁니다. 다운로드에 대한 최대 크기(바이트)를 `asset.download.prezip.maxcontentsize` 값으로 설정합니다. 아래 샘플은 ZIP 다운로드의 최대 크기를 100kB를 초과하지 않도록 구성합니다.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 {#disable-asset-download-servlet} 비활성화

다운로드 기능이 필요하지 않은 경우 DoS와 유사한 위험을 방지하기 위해 서블릿을 비활성화하십시오. Dispatcher 구성을 업데이트하여 모든 자산 다운로드 요청을 차단하여 [!DNL Experience Manager] 작성자 및 게시 인스턴스에서 `Asset Download Servlet`을(를) 비활성화할 수 있습니다. OSGi 콘솔을 통해 직접 서블릿을 수동으로 비활성화할 수도 있습니다.

1. 디스패처 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성을 편집하고 [필터 섹션](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring)에 새 규칙을 추가합니다.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [DRM 보호 자산 다운로드](drm.md)
* [Win 또는 Mac 데스크탑에서 Experience Manager 데스크탑 앱을 사용하여 자산 다운로드](https://helpx.adobe.com/kr/experience-manager/desktop-app/aem-desktop-app.html)
* [지원되는 Adobe Creative Cloud 앱 내에서 Adobe 자산 링크를 사용하여 자산을 다운로드합니다](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)

