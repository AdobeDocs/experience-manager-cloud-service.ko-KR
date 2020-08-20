---
title: 다음에서 [!DNL Adobe Experience Manager Assets]에셋 다운로드
description: 자산 다운로드 [!DNL Adobe Experience Manager Assets] 명령 다운로드 기능을 활성화하거나 비활성화합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3cbf0cc85c7c415f6585e92e509eb7fefb5ede82
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 4%

---


# 자산 다운로드 [!DNL Adobe Experience Manager] {#download-assets-from-aem}

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 또는 자산을 직접 연결하는 링크가 포함된 이메일을 보낼 수도 있습니다 [!DNL Adobe Experience Manager Assets]. 다운로드한 자산은 ZIP 파일에 번들로 포함됩니다. 압축 ZIP 파일의 최대 파일 크기는 내보내기 작업에 대해 1GB입니다. 내보내기 작업당 최대 500개의 에셋이 허용됩니다.

>[!NOTE]
>
>이메일 수신자는 이메일 메시지의 ZIP 다운로드 링크에 액세스하려면 `dam-users` 그룹의 구성원이어야 합니다. 자산을 다운로드할 수 있으려면 멤버는 에셋 다운로드를 트리거하는 워크플로우를 시작할 수 있는 권한이 있어야 합니다.

자산 유형 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전판 세트는 다운로드할 수 없습니다.

자산을 다운로드하려면 다음 단계를 수행하십시오.

1. Experience Manager 사용자 인터페이스에서 **[!UICONTROL 자산]** > **[!UICONTROL 파일을 클릭합니다]**.
1. 다운로드할 자산으로 이동합니다. 폴더를 선택하거나 폴더 내에서 하나 이상의 자산을 선택합니다. 도구 모음에서 다운로드를 **[!UICONTROL 클릭합니다]**.

   ![자산을 다운로드할 때 사용 가능한 옵션 [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

   *그림:다운로드 대화 상자 옵션.*

1. 다운로드 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]** | 다운로드한 각 자산을 로컬 컴퓨터의 한 폴더에 자산의 상위 폴더 아래에 중첩된 하위 폴더에 포함시키려면 이 옵션을 선택합니다. 이 옵션을 선택하지 *않으면* 기본적으로 폴더 계층은 무시되고 모든 에셋이 로컬 컴퓨터의 한 폴더에 다운로드됩니다. |
   | **[!UICONTROL 이메일]** | 수신자에게 이메일 알림을 보내려면 이 옵션을 선택합니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> 배포 시 사용자 지정하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>다음 위치에 임차인별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL 자산]** | 표현물 없이 자산을 원래 형식으로 다운로드하려면 이 옵션을 선택합니다.<br>원본 자산에 하위 자산이 있는 경우 하위 자산 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 표현물]** | 표현물은 자산의 이진 표현입니다. 자산에는 업로드된 파일의 기본 표현이 있습니다. 그들은 어떤 수의 진술도 가질 수 있다. <br> 이 옵션을 사용하여 다운로드할 변환을 선택할 수 있습니다. 사용할 수 있는 변환은 선택한 자산에 따라 다릅니다. |
   | **[!UICONTROL 스마트 자르기]** | AEM 내에서 선택한 자산의 모든 스마트 자르기 변환을 다운로드하려면 이 옵션을 선택합니다. 스마트 자르기 변환이 있는 zip 파일이 만들어지고 로컬 컴퓨터에 다운로드됩니다. |
   | **[!UICONTROL 동적 표현물]** | 일련의 대체 표현물을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택할 때 [이미지 사전 설정](/help/assets/dynamic-media/image-presets.md) 목록에서 선택하여 동적으로 만들 표현물도 선택할 수 있습니다. <br>또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 이 옵션은 활성화된 경우에만 사용할 수 [!DNL Dynamic Media] 있습니다. |

1. 대화 상자에서 다운로드를 **[!UICONTROL 클릭합니다]**.

## 자산 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

AEM의 기본 서블릿을 사용하면 인증된 사용자가 서버와 네트워크에 과부하를 줄 수 있는 보이는 자산의 ZIP 파일을 만들기 위해 임의로 크기가 크고 동시 다운로드 요청을 발행할 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS 위험을 줄이기 위해 게시 인스턴스에 대해 `AssetDownloadServlet` 기본적으로 OSGi 구성 요소가 비활성화됩니다.

DAM에서 에셋을 다운로드할 수 있도록 하려면 에셋 공유 공유물 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 가능한 한 낮은 다운로드 크기를 설정할 것을 권장합니다. 높은 가치는 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 대상으로 하는 이름 지정 규칙이 있는 폴더(예: `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 `nt:file` 명명된 형식의 새 파일을 만듭니다 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. 다음 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 으로 채웁니다. 다운로드의 최대 크기(바이트)를 값으로 설정합니다 `asset.download.prezip.maxcontentsize`. 아래 샘플은 ZIP 다운로드의 최대 크기를 100kB를 초과하지 않도록 구성합니다.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 비활성화 {#disable-asset-download-servlet}

AEM 게시 인스턴스에서 자산 다운로드 요청을 차단하도록 디스패처 구성을 업데이트하여 이 요청을 비활성화할 `Asset Download Servlet` 수 있습니다. OSGi 콘솔을 통해 서블릿을 수동으로 비활성화할 수도 있습니다.

1. 발송자 구성을 통해 자산 다운로드 요청을 차단하려면 구성을 편집하고 `dispatcher.any` 필터 섹션에 새 규칙을 [추가합니다](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [DRM 보호 에셋 다운로드](drm.md)
>* [Win 또는 Mac 데스크탑에서 Experience Manager 데스크탑 앱을 사용하여 에셋 다운로드](https://helpx.adobe.com/kr/experience-manager/desktop-app/aem-desktop-app.html)
>* [지원되는 Adobe Creative Cloud 앱 내에서 Adobe 에셋 링크를 사용하여 에셋 다운로드](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)

