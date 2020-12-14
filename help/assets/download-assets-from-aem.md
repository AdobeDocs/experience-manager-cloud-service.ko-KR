---
title: 자산 다운로드
description: ' [!DNL Adobe Experience Manager Assets] 에서 에셋을 다운로드하고 다운로드 기능을 활성화하거나 비활성화합니다.'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3207151a76c51637551907d15a34f1a6b7450d02
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 4%

---


# [!DNL Adobe Experience Manager] {#download-assets-from-aem}에서 에셋 다운로드

정적 및 동적 표현물을 비롯한 자산을 다운로드할 수 있습니다. 또는 [!DNL Adobe Experience Manager Assets]에서 바로 자산에 대한 링크가 있는 이메일을 보낼 수 있습니다. 다운로드한 자산은 ZIP 파일에 번들로 포함됩니다. 압축 ZIP 파일의 최대 파일 크기는 내보내기 작업에 대해 1GB입니다. 내보내기 작업당 최대 500개의 에셋이 허용됩니다.

>[!NOTE]
>
>이메일 수신자는 이메일 메시지의 ZIP 다운로드 링크에 액세스하려면 `dam-users` 그룹의 구성원이어야 합니다. 자산을 다운로드할 수 있으려면 자산 다운로드를 트리거하는 워크플로우를 시작할 수 있는 권한이 구성원에게 있어야 합니다.

이미지 세트, 스핀 세트, 혼합 미디어 집합 및 캐러셀 집합을 다운로드할 수 없습니다.

다음 방법을 사용하여 Experience Manager 에셋을 다운로드할 수 있습니다.

* [Experience Manager 사용자 인터페이스](#download-in-aem)
* 자산 링크 공유 사용자 인터페이스
* [에셋 공유 공유물](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## [!DNL Experience Manager] 인터페이스 {#download-in-aem}를 사용하여 에셋 다운로드

비동기 다운로드 서비스는 대규모 자산을 매끄럽게 다운로드할 수 있는 프레임워크를 제공합니다. 작은 파일은 사용자 인터페이스에서 실시간으로 다운로드됩니다. 대용량 파일은 비동기적으로 다운로드되며 사용자는 받은 편지함의 Experience Manager 알림을 통해 완료 사실을 알 수 있습니다. [Experience Manager 받은 편지함](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html)에 대한 이해를 참조하십시오.

![다운로드 알림](assets/download-notification.png)

*그림:받은 편지함을 통해 알림  [!DNL Experience Manager] 다운로드*

비동기 다운로드는 다음 중 한 경우에 트리거됩니다.

* 10개 이상의 에셋이 있거나 100MB 이상이 다운로드되는 경우.
* 다운로드하는 데 30초 이상 걸리는 경우.

자산을 다운로드하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager] 사용자 인터페이스에서 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 클릭합니다.
1. 다운로드할 자산으로 이동합니다. 폴더를 선택하거나 폴더 내의 자산을 하나 이상 선택합니다. 도구 모음에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   ![자산을 다운로드할 때 사용 가능한 옵션  [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

   *그림:다운로드 대화 상자 옵션.*

1. [다운로드] 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]** | 다운로드한 각 자산을 로컬 컴퓨터의 한 폴더에 자산의 상위 폴더 아래에 중첩된 하위 폴더에 포함시키려면 이 옵션을 선택합니다. 이 옵션이 선택&#x200B;*이 아닌*&#x200B;인 경우 기본적으로 폴더 계층 구조는 무시되고 모든 자산이 로컬 컴퓨터의 한 폴더에 다운로드됩니다. |
   | **[!UICONTROL 이메일]** | 수신자에게 이메일 알림을 보내려면 이 옵션을 선택합니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> 배포 시 사용자 지정하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>다음 위치에 임차인별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL 자산]** | 표현물 없이 자산을 원래 형식으로 다운로드하려면 이 옵션을 선택합니다.<br>원본 자산에 하위 자산이 있는 경우 하위 자산 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 표현물]** | 표현물은 자산의 이진 표현입니다. 자산은 업로드된 파일의 기본 표현인 그들은 어떤 수의 진술도 가질 수 있다. <br> 이 옵션을 사용하여 다운로드할 변환을 선택할 수 있습니다. 사용할 수 있는 변환은 선택한 자산에 따라 다릅니다. |
   | **[!UICONTROL 스마트 자르기]** | [!DNL Experience Manager] 내에서 선택한 자산의 모든 스마트 자르기 변환을 다운로드하려면 이 옵션을 선택합니다. 스마트 자르기 변환이 있는 zip 파일이 만들어지고 로컬 컴퓨터에 다운로드됩니다. |
   | **[!UICONTROL 동적 표현물]** | 일련의 대체 변환을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택할 때 [이미지 사전 설정](/help/assets/dynamic-media/image-presets.md) 목록에서 선택하여 동적으로 만들 표현물도 선택할 수 있습니다. <br>또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 이 옵션은 [!DNL Dynamic Media]이(가) 활성화된 경우에만 사용할 수 있습니다. |

1. 대화 상자에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

## 자산 다운로드 서블릿 사용 {#enable-asset-download-servlet}

[!DNL Experience Manager]의 기본 서블릿을 통해 인증된 사용자가 임의의 크기로 동시 다운로드 요청을 발행하여 자산의 ZIP 파일을 만들 수 있습니다. 다운로드 준비 작업은 성능에 영향을 줄 수도 있고 서버와 네트워크를 과부할 수도 있습니다. 이 기능으로 인해 발생할 수 있는 DoS와 유사한 위험을 완화하려면 게시 인스턴스에 대해 `AssetDownloadServlet` OSGi 구성 요소가 비활성화됩니다.

DAM에서 에셋을 다운로드할 수 있도록 하려면 Asset Share Commons나 다른 포털과 유사한 구현을 사용할 경우 OSGi 구성을 통해 수동으로 서블릿을 활성화합니다. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 허용되는 다운로드 크기를 최대한 낮게 설정할 것을 권장합니다. 높은 가치는 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 대상으로 하는 이름 지정 규칙(즉, `config.publish`)을 사용하여 폴더를 만듭니다.

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 이름의 `nt:file` 유형의 새 파일을 만듭니다.
1. `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`을(를) 다음 항목으로 채웁니다. 다운로드에 대한 최대 크기(바이트)를 `asset.download.prezip.maxcontentsize` 값으로 설정합니다. 아래 샘플은 ZIP 다운로드의 최대 크기를 100kB를 초과하지 않도록 구성합니다.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 {#disable-asset-download-servlet} 비활성화

`Asset Download Servlet`은(는) 발송자 구성을 업데이트하여 자산 다운로드 요청을 차단함으로써 [!DNL Experience Manager] 게시 인스턴스에서 비활성화할 수 있습니다. 서브렛은 OSGi 콘솔을 통해 직접 비활성화할 수도 있습니다.

1. 디스패처 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성을 편집하고 [필터 섹션](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring)에 새 규칙을 추가합니다.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [DRM 보호 에셋 다운로드](drm.md)
>* [Win 또는 Mac 데스크탑에서 Experience Manager 데스크탑 앱을 사용하여 에셋 다운로드](https://helpx.adobe.com/kr/experience-manager/desktop-app/aem-desktop-app.html)
>* [지원되는 Adobe Creative Cloud 앱 내에서 Adobe 에셋 링크를 사용하여 에셋 다운로드](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)

