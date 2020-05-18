---
title: AEM에서 자산 다운로드
description: AEM에서 자산을 다운로드하고 다운로드 기능을 활성화하거나 비활성화하는 방법에 대해 학습합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c978be66702b7f032f78a1509f2a11315d1ed89f
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 4%

---


# AEM에서 자산 다운로드 {#download-assets-from-aem}

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 다운로드한 자산은 ZIP 파일에 번들로 포함됩니다. 압축 ZIP 파일의 최대 파일 크기는 내보내기 작업에 대해 1GB입니다. 내보내기 작업당 최대 500개의 에셋이 허용됩니다.

>[!NOTE]
>
>자산을 다운로드할 수 있으려면 멤버는 에셋 다운로드를 트리거하는 워크플로우를 시작할 수 있는 권한이 있어야 합니다.

자산을 다운로드하려면 자산으로 이동하고 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 다운로드]** 아이콘을 탭/클릭합니다. 결과 대화 상자에서 다운로드 옵션을 지정합니다.

자산 유형 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전판 세트는 다운로드할 수 없습니다.

![AEM 자산에서 자산을 다운로드할 때 사용 가능한 옵션](assets/asset_download_dialog.png)

*그림: AEM 자산에서 자산을 다운로드할 때 사용할 수 있는 옵션입니다.*

내보내기/다운로드 옵션은 다음과 같습니다. 다이내믹 표현물은 다이내믹 미디어에만 고유하며 선택한 자산 외에 즉각적으로 표현물을 생성할 수 있습니다. 이 옵션은 다이내믹 미디어가 활성화된 경우에만 사용할 수 있습니다.

| 내보내기 또는 다운로드 옵션 | 설명 |
|---|---|
| [!UICONTROL 자산] | 표현물 없이 자산을 원래 양식으로 다운로드하려면 이 옵션을 선택합니다. |
| [!UICONTROL 표현물] | 표현물은 자산의 이진 표현입니다. 자산에는 업로드된 파일의 기본 표현이 있습니다. 그들은 어떤 수의 진술도 가질 수 있다. <br> 이 옵션을 사용하여 다운로드할 변환을 선택할 수 있습니다. 사용할 수 있는 변환은 선택한 자산에 따라 다릅니다. |
| [!UICONTROL 동적 표현물] | 동적 표현물은 다른 표현물을 즉석에서 생성합니다. 이 옵션을 선택하면 이미지 사전 설정 목록에서 선택하여 동적으로 만들 표현물도 선택할 수 있습니다. 또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 수정자(예: 이미지 반전) 선택 |
| [!UICONTROL 각 자산에 대해 별도의 폴더 만들기] | 자산을 다운로드하는 동안 폴더 계층을 유지하려면 이 옵션을 선택합니다. 기본적으로 폴더 계층은 무시되며 모든 자산은 로컬 시스템의 한 폴더에 다운로드됩니다. |

자산에 변환이 있는 경우 옵션 변환 옵션을 사용할 수 있습니다. 자산에 하위 자산이 포함된 경우 하위 자산 옵션을 사용할 수 있습니다.

다운로드할 폴더를 선택하면 폴더 아래의 전체 자산 계층 구조가 다운로드됩니다. 다운로드한 각 자산(상위 폴더 아래에 중첩된 하위 폴더의 자산 포함)을 개별 폴더에 포함하려면 각 자산에 대해 **[!UICONTROL 별도의 폴더 만들기를 선택합니다]**.

## 자산 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

AEM의 기본 서블릿을 사용하면 인증된 사용자가 서버와 네트워크를 과부시킬 수 있는 보이는 자산의 ZIP 파일을 만들기 위해 임의로 크기가 크고 동시 다운로드 요청을 발행할 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS 위험을 줄이기 위해 게시 인스턴스에 대해 `AssetDownloadServlet` 기본적으로 OSGi 구성 요소가 비활성화됩니다.

DAM에서 에셋을 다운로드할 수 있도록 하려면 에셋 공유 공유물 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe에서는 일상적인 다운로드 요구 사항에 영향을 주지 않고 가능한 낮은 다운로드 크기를 설정할 것을 권장합니다. 높은 가치는 성능에 영향을 줄 수 있습니다.

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
>* [Win 또는 Mac 데스크탑에서 AEM 데스크탑 앱을 사용하여 에셋 다운로드](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
>* [지원되는 Adobe Creative Cloud 앱에서 Adobe Assets Link를 사용하여 에셋 다운로드](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)

