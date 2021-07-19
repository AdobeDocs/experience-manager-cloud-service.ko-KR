---
title: 자산 마이크로서비스 구성 및 사용
description: 클라우드 기반의 자산 마이크로서비스 를 구성하고 사용하여 자산을 규모에 맞게 처리합니다.
contentOwner: AG
feature: asset compute 마이크로서비스,워크플로우,자산 처리
role: Architect,Admin
exl-id: 7e01ee39-416c-4e6f-8c29-72f5f063e428
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '2709'
ht-degree: 1%

---

# 자산 마이크로서비스 및 처리 프로필 사용 {#get-started-using-asset-microservices}

자산 마이크로서비스 는 클라우드 기반의 애플리케이션(작업자라고도 함)을 사용하여 자산을 확장 가능하고 탄력적으로 처리할 수 있도록 해줍니다. Adobe은 다양한 자산 유형 및 처리 옵션을 최적으로 처리하기 위해 서비스를 관리합니다.

자산 마이크로서비스 를 사용하면 이전 버전의 [!DNL Experience Manager]에서 사용할 수 있는 것보다 더 많은 형식의 [광범위한 파일 유형](/help/assets/file-format-support.md)을 처리할 수 있습니다. 예를 들어 이제 PSD 및 PSB 형식의 축소판 추출을 수행할 수 있지만 이전에 [!DNL ImageMagick] 과 같은 타사 솔루션이 필요했습니다.

자산 처리는 **[!UICONTROL 처리 프로필]**&#x200B;의 구성에 따라 달라집니다. Experience Manager은 기본 설정 을 제공하며 관리자가 더 구체적인 자산 처리 구성을 추가할 수 있도록 해줍니다. 관리자는 선택적 사용자 지정 작업을 포함하여 사후 처리 워크플로우 구성을 생성, 유지 관리 및 수정합니다. 워크플로우를 사용자 지정하여 개발자는 기본 서비스를 확장할 수 있습니다.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![자산 처리에 대한 높은 수준 ](assets/asset-microservices-flow.png "보기자산 처리에 대한 높은 수준의 보기")

>[!NOTE]
>
>여기에 설명된 자산 처리는 이전 버전의 [!DNL Experience Manager]에 있는 `DAM Update Asset` 워크플로우 모델을 대체합니다. 대부분의 표준 변환 생성 및 메타데이터 관련 단계는 자산 마이크로서비스 처리로 대체되며, 나머지 단계는 사후 처리 워크플로우 구성으로 대체할 수 있습니다.

## 자산 처리 옵션 이해 {#get-started}

[!DNL Experience Manager] 는 다음 수준의 처리를 허용합니다.

| 옵션 | 설명 | 활용 사례 적용 |
|---|---|---|
| [기본 구성](#default-config) | 현재 상태로 사용할 수 있으며 수정할 수 없습니다. 이 구성은 매우 기본적인 변환 생성 기능을 제공합니다. | <ul> <li>[!DNL Assets] 사용자 인터페이스에 사용되는 표준 축소판(48, 140 및 319픽셀) </li> <li> 큰 미리 보기(웹 표현물 - 1280픽셀) </li><li> 메타데이터 및 텍스트 추출.</li></ul> |
| [사용자 지정 구성](#standard-config) | 사용자 인터페이스를 통해 관리자가 구성합니다. 기본 옵션을 확장하여 표현물 생성에 대한 더 많은 옵션을 제공합니다. 즉시 사용 가능한 옵션을 확장하여 다양한 형식 및 표현물을 제공합니다. | <ul><li>FPO 표현물. </li> <li>이미지 파일 형식 및 해상도 변경</li> <li> 구성된 파일 형식에 조건부 적용 </li> </ul> |
| [사용자 지정 프로필](#custom-config) | 사용자 지정 응용 프로그램을 통해 사용자 지정 코드를 사용하여 [Asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html)를 호출하도록 사용자 인터페이스를 통해 관리자가 구성합니다. 클라우드 기반의 확장 가능한 방법에서 더 복잡한 요구 사항을 지원합니다. | [허용되는 사용 사례](#custom-config)를 참조하십시오. |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## 지원되는 파일 형식 {#supported-file-formats}

자산 마이크로서비스 는 메타데이터를 처리, 생성 또는 추출할 수 있는 다양한 파일 형식을 지원합니다. MIME 유형의 전체 목록과 각 유형에 대해 지원되는 기능은 [지원되는 파일 형식](file-format-support.md) 을 참조하십시오.

## 기본 구성 {#default-config}

일부 기본값은 Experience Manager에 필요한 기본 표현물을 사용할 수 있도록 사전 구성되어 있습니다. 기본 구성에서는 메타데이터 추출 및 텍스트 추출 작업을 사용할 수도 있습니다. 사용자는 자산 업로드 또는 업데이트를 즉시 시작할 수 있으며 기본 처리가 기본적으로 제공됩니다.

기본 구성을 사용하면 가장 기본적인 처리 프로필만 구성됩니다. 이러한 처리 프로필은 사용자 인터페이스에 표시되지 않으며 수정할 수 없습니다. 업로드된 자산을 처리하기 위해 항상 실행됩니다. 이러한 기본 처리 프로필에서는 [!DNL Experience Manager]에 필요한 기본 처리가 모든 자산에서 완료되도록 합니다.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## 표준 구성 {#standard-config}

[!DNL Experience Manager] 는 사용자의 요구 사항에 따라 일반적인 형식에 대한 보다 구체적인 표현물을 생성하는 기능을 제공합니다. 관리자는 추가 [!UICONTROL 처리 프로필]을 만들어 이러한 변환을 쉽게 만들 수 있습니다. 그런 다음 사용 가능한 프로필 중 하나 이상을 특정 폴더에 할당하여 추가 처리를 완료합니다. 예를 들어, 추가 처리에서는 웹, 모바일 및 태블릿에 대한 렌디션을 생성할 수 있습니다. 다음 비디오에서는 [!UICONTROL 처리 프로필]을 만들고 적용하는 방법과 만들어진 표현물에 액세스하는 방법을 보여줍니다.

* **표현물 너비 및 높이**: 변환 너비와 높이 사양은 생성된 출력 이미지의 최대 크기를 제공합니다. 자산 마이크로서비스는 가능한 가장 큰 렌디션을 생성하려고 합니다. 이 렌디션의 너비와 높이는 각각 지정된 너비와 높이보다 크지 않습니다. 종횡비는 유지되며, 이것은 원본과 동일합니다. 빈 값은 자산 처리가 원래 픽셀 차원을 가정함을 의미합니다.

* **MIME 유형 포함 규칙**: 특정 MIME 유형의 자산이 처리되면 먼저 표현물 사양에 대해 제외된 MIME 유형 값에 대해 MIME 유형을 확인합니다. 해당 목록과 일치하는 경우 자산(차단 목록)에 대해 이 특정 표현물이 생성되지 않습니다. 그렇지 않으면 포함된 MIME 유형에 대해 MIME 유형이 선택되어 있으며 목록과 일치하면 렌디션이 생성됩니다(허용 목록).

* **특수 FPO 변환**: 에서  [!DNL Experience Manager] 문서에 대형 자산 [!DNL Adobe InDesign] 을 배치할 때 크리에이티브 전문가가 자산을  [배치한 후 상당한 시간을 기다립니다](https://helpx.adobe.com/indesign/using/placing-graphics.html). 한편 사용자가 [!DNL InDesign] 사용을 차단합니다. 따라서 크리에이티브 플로우가 중단되고 사용자 경험에 부정적인 영향을 줍니다. Adobe을 사용하면 [!DNL InDesign] 문서에 작은 크기의 렌디션을 일시적으로 배치할 수 있습니다. 이 렌디션은 나중에 전체 해상도 자산으로 대체할 수 있습니다. [!DNL Experience Manager] 배치에만 사용되는 표현물(FPO)을 제공합니다. 이러한 FPO 변환은 파일 크기가 작지만 동일한 종횡비입니다.

처리 프로필에는 FPO(For Placement Only) 표현물이 포함될 수 있습니다. 처리 프로필에 대해 켜야 하는지 확인하려면 [!DNL Adobe Asset Link] [설명서](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)를 참조하십시오. 자세한 내용은 [자산 링크 Adobe 완료 설명서](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)를 참조하십시오.

### 표준 프로필 만들기 {#create-standard-profile}

표준 처리 프로필을 만들려면 다음 단계를 수행합니다.

1. 관리자는 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**&#x200B;에 액세스합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 폴더에 적용할 때 프로필을 고유하게 식별하는 데 도움이 되는 이름을 제공합니다.
1. FPO 변환을 생성하려면 **[!UICONTROL 이미지]** 탭에서 **[!UICONTROL FPO 표현물 만들기]**&#x200B;를 활성화합니다. **[!UICONTROL Quality]** 값을 1에서 100 사이에 입력합니다.
1. 다른 변환을 생성하려면 **[!UICONTROL 새로 추가]**&#x200B;를 클릭하고 다음 정보를 제공합니다.

   * 각 변환의 파일 이름입니다.
   * 각 표현물의 파일 형식(PNG, JPEG, GIF 또는 WebP)입니다.
   * 각 표현물의 너비 및 높이(픽셀 단위)입니다. 값을 지정하지 않으면 원본 이미지의 전체 픽셀 크기가 사용됩니다.
   * 각 JPEG 및 WebP 표현물의 품질 백분율.
   * 프로필의 적용을 정의하기 위해 MIME 유형을 포함 및 제외합니다.

   ![처리 프로필 추가](assets/processing-profiles-image.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

<!-- TBD: Update the video link when a new video is available from Tech Marketing.

The following video demonstrates the usefulness and usage of standard profile.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)
-->

<!-- This image was removed per cqdoc-15624, as requested by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## 사용자 지정 프로필 및 사용 사례 {#custom-config}

[!DNL Asset Compute Service] 은 기본 처리, Photoshop 파일과 같은 Adobe 관련 형식 처리 및 사용자 지정 또는 조직별 처리 구현과 같은 다양한 사용 사례를 지원합니다. 이전에 필요한 DAM 자산 업데이트 워크플로우 사용자 지정은 자동으로 처리되거나 처리 프로필 구성을 통해 처리됩니다. 이러한 처리 옵션에서 비즈니스 요구 사항을 충족하지 않는 경우 [!DNL Asset Compute Service] 을 개발하여 기본 기능을 확장하는 것이 좋습니다. 개요는 [확장성 이해 및 사용 시기](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html)를 참조하십시오.

>[!NOTE]
>
>Adobe은 기본 구성 또는 표준 프로필을 사용하여 비즈니스 요구 사항을 수행할 수 없는 경우에만 사용자 지정 애플리케이션을 사용하는 것이 좋습니다.

이미지, 비디오, 문서 및 기타 파일 형식을 축소판, 추출된 텍스트 및 메타데이터, 아카이브 등의 다양한 변환으로 변환할 수 있습니다.

개발자는 [!DNL Asset Compute Service]을 사용하여 지원되는 사용 사례에 사용자 지정 응용 프로그램](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html)을 만들 수 있습니다. [ [!DNL Experience Manager] 관리자는 사용자 정의 프로파일을 사용하여 사용자 인터페이스에서 이러한 사용자 정의 애플리케이션을 호출할 수 있습니다. [!DNL Asset Compute Service] 에서는 외부 서비스를 호출하는 다음과 같은 사용 사례를 지원합니다.

* [!DNL Adobe Photoshop]의 [ImageCutout API](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout)를 사용하고 결과를 변환으로 저장합니다.
* 서드파티 시스템에 문의하여 데이터를 업데이트하십시오(예: PIM 시스템).
* Photoshop 템플릿을 기반으로 다양한 표현물을 생성하려면 [!DNL Photoshop] API를 사용하십시오.
* [Lightroom API Adobe](https://github.com/AdobeDocs/lightroom-api-docs#supported-features)를 사용하여 수집된 자산을 최적화하고 이를 변환으로 저장합니다.

>[!NOTE]
>
>사용자 지정 응용 프로그램을 사용하여 표준 메타데이터를 편집할 수 없습니다. 사용자 지정 메타데이터만 수정할 수 있습니다.

### 사용자 지정 프로필 만들기 {#create-custom-profile}

사용자 지정 프로필을 만들려면 다음 단계를 수행하십시오.

1. 관리자는 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**&#x200B;에 액세스합니다. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 사용자 지정]** 탭을 클릭합니다. **[!UICONTROL 새로 추가]**&#x200B;를 클릭합니다. 표현물의 원하는 파일 이름을 입력합니다.
1. 다음 정보를 제공합니다.

   * 각 변환의 파일 이름 및 지원되는 파일 확장자입니다.
   * [Firefly 사용자 지정 앱의 끝점 URL입니다](https://experienceleague.adobe.com/docs/asset-compute/using/extend/deploy-custom-application.html). 앱은 Experience Manager 계정이 있는 조직과 동일해야 합니다.
   * 서비스 매개 변수를 [에 추가하여 추가 정보나 매개 변수를 사용자 지정 응용 프로그램](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html#extend)에 전달합니다.
   * 처리를 몇 가지 특정 파일 형식으로 제한하는 MIME 유형을 포함 및 제외합니다.

   **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

사용자 지정 응용 프로그램은 헤드리스 [Project Firefly](https://github.com/AdobeDocs/project-firefly) 앱입니다. 사용자 지정 응용 프로그램은 처리 프로필로 설정된 경우 제공된 모든 파일을 가져옵니다. 응용 프로그램에서 파일을 필터링해야 합니다.

>[!CAUTION]
>
>Firefly 앱 및 [!DNL Experience Manager] 계정이 동일한 조직의 계정이 아닌 경우 통합이 작동하지 않습니다.

### 사용자 지정 프로필의 예 {#custom-profile-example}

사용자 지정 프로필의 사용을 설명하기 위해 캠페인 이미지에 사용자 지정 텍스트를 적용하는 사용 사례를 생각해 보겠습니다. Photoshop API를 활용하는 처리 프로필을 만들어 이미지를 편집할 수 있습니다.

asset compute 서비스 통합을 통해 Experience Manager은 [!UICONTROL 서비스 매개 변수] 필드를 사용하여 이러한 매개 변수를 사용자 지정 애플리케이션에 전달할 수 있습니다. 그런 다음 사용자 지정 애플리케이션에서 Photoshop API를 호출하고 이 값을 API에 전달합니다. 예를 들어, 글꼴 이름, 텍스트 색상, 텍스트 가중치 및 텍스트 크기를 전달하여 캠페인 이미지에 사용자 지정 텍스트를 추가할 수 있습니다.

<!-- TBD: Check screenshot against the interface. -->

![custom-processing-profile](assets/custom-processing-profile.png)

*그림: 서비스  [!UICONTROL 매개 ] 변수필드를 사용하여 추가된 정보를 사용자 지정 애플리케이션에 미리 정의된 매개 변수에 전달합니다. 이 예에서 캠페인 이미지가 업로드되면 이미지는 `Arial-BoldMT` 글꼴의 `Jumanji` 텍스트로 업데이트됩니다.*

## 처리 프로필을 사용하여 자산 처리 {#use-profiles}

이러한 폴더에 업로드되거나 업데이트된 자산에 대해 처리할 Experience Manager을 위해 추가 사용자 지정 처리 프로필을 만들어 특정 폴더에 적용합니다. 기본 제공 표준 처리 프로필은 항상 실행되지만 사용자 인터페이스에 표시되지 않습니다. 사용자 지정 프로필을 추가하면 두 프로필을 사용하여 업로드한 자산을 처리합니다.

다음 방법 중 하나를 사용하여 폴더에 처리 프로필을 적용합니다.

* 관리자는 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**&#x200B;에서 처리 프로필 정의를 선택하고 **[!UICONTROL 폴더에 프로필 적용]** 작업을 사용할 수 있습니다. 특정 폴더로 이동하여 선택한 다음 해당 프로필의 애플리케이션을 확인할 수 있는 컨텐츠 브라우저가 열립니다.
* 사용자는 자산 사용자 인터페이스에서 폴더를 선택하고 **[!UICONTROL 속성]** 작업을 사용하여 폴더 속성 화면을 열고 **[!UICONTROL 자산 처리]** 탭을 클릭한 다음, [!UICONTROL 처리 프로필] 목록에서 해당 폴더에 대한 적절한 처리 프로필을 선택할 수 있습니다. 변경 사항을 저장하려면 **[!UICONTROL 저장 및 닫기]**를 클릭합니다.
   ![자산 속성 탭에서 폴더에 처리 프로필 적용](assets/folder-properties-processing-profile.png)

* 사용자는 Assets 사용자 인터페이스에서 폴더 또는 특정 자산을 선택하여 처리 프로필을 적용한 후 맨 위에 있는 옵션에서 ![자산 재처리 아이콘](assets/do-not-localize/reprocess-assets-icon.png) **[!UICONTROL 자산 재처리]** 옵션을 선택할 수 있습니다.

>[!TIP]
>
>하나의 처리 프로필만 폴더에 적용할 수 있습니다. 렌디션을 더 생성하려면 기존 처리 프로필에 변환 정의를 더 추가하십시오.

처리 프로필이 폴더에 적용되면, 이 폴더 또는 해당 하위 폴더에 업로드된 모든 새 자산(또는 업데이트됨)이 구성된 추가 처리 프로필을 사용하여 처리됩니다. 이 처리에는 표준 기본 프로필 외에도 추가됩니다.

>[!NOTE]
>
>폴더에 적용된 처리 프로필은 전체 트리에 대해 작동하지만 하위 폴더에 적용된 다른 프로필로 오버라이드할 수 있습니다. 자산이 폴더에 업로드되면 Experience Manager은 포함된 폴더의 속성에서 처리 프로필을 확인합니다. 적용되지 않으면 처리 프로필이 적용되도록 계층의 상위 폴더가 선택됩니다.

자산이 처리되었는지 확인하려면 왼쪽 레일의 [!UICONTROL 표현물] 보기에서 생성된 표현물을 미리 봅니다. 자산 미리 보기를 열고 왼쪽 레일을 열어 **[!UICONTROL 표현물]** 보기에 액세스합니다. 특정 자산의 유형이 MIME 유형 포함 규칙과 일치하는 처리 프로필의 특정 표현물은 표시 및 액세스 가능해야 합니다.

![추가 표현물](assets/renditions-additional-renditions.png)

*그림: 상위 폴더에 적용된 처리 프로필에서 생성한 두 개의 추가 표현물의 예입니다.*

## 사후 처리 워크플로우 {#post-processing-workflows}

처리 프로필을 사용하여 처리할 수 없는 자산의 추가 처리가 필요한 경우, 구성에 추가 사후 처리 워크플로우를 추가할 수 있습니다. 사후 처리를 사용하면 자산 마이크로서비스를 사용하여 구성 가능한 처리 위에 완전히 사용자 지정된 처리를 추가할 수 있습니다.

사후 처리 워크플로우는 구성된 경우 마이크로 서비스 처리가 완료된 후 [!DNL Experience Manager]에 의해 자동으로 실행됩니다. 워크플로우를 트리거하기 위해 워크플로우 런처를 수동으로 추가할 필요가 없습니다. 해당 예는 다음과 같습니다.

* 자산을 처리하는 사용자 지정 워크플로우 단계입니다.
* 외부 시스템(예: 제품 또는 프로세스 정보)의 자산에 메타데이터 또는 속성을 추가하는 통합.
* 외부 서비스에서 추가 처리를 수행했습니다.

[!DNL Experience Manager]에 사후 처리 워크플로우 구성을 추가하려면 다음 단계를 수행합니다.

* 하나 이상의 워크플로우 모델을 만듭니다. 이러한 사용자 지정 모델을 이 설명서에서 *사후 처리 워크플로우 모델*&#x200B;이라고 합니다. 일반 [!DNL Experience Manager] 워크플로우 모델입니다.
* 이러한 모델에 필요한 워크플로우 단계를 추가합니다. 기본 워크플로우에서 단계를 검토하고 필요한 모든 기본 단계를 사용자 지정 워크플로우에 추가합니다. 이 단계는 워크플로우 모델 구성을 기반으로 자산에 대해 실행됩니다. 예를 들어 자산 업로드 시 스마트 태깅을 자동으로 수행하려면 단계를 사용자 지정 사후 처리 워크플로우 모델에 추가합니다.
* 끝에 [!UICONTROL DAM 자산 업데이트 워크플로우 완료 프로세스] 단계를 추가합니다. 이 단계를 추가하면 Experience Manager이 처리가 종료되고 자산이 처리됨으로 표시될 수 있음을 알 수 있습니다. 즉, 자산에 *New*&#x200B;이 표시됩니다.
* 경로(폴더 위치) 또는 정규 표현식으로 사후 처리 워크플로우 모델의 실행을 구성할 수 있도록 해주는 사용자 지정 워크플로우 러너 서비스에 대한 구성을 만듭니다.

사후 처리 워크플로우에서 사용할 수 있는 표준 워크플로우 단계에 대한 자세한 내용은 개발자 참조 설명서의 사후 처리 워크플로우](developer-reference-material-apis.md#post-processing-workflows-steps)워크플로우 단계 를 참조하십시오.[

### 사후 처리 워크플로우 모델 만들기 {#create-post-processing-workflow-models}

사후 처리 워크플로우 모델은 일반적인 [!DNL Experience Manager] 워크플로우 모델입니다. 다른 저장소 위치 또는 자산 유형에 대해 다른 처리가 필요한 경우 다른 모델을 만듭니다.

필요에 따라 처리 단계가 추가됩니다. 사용 가능한 지원되는 단계와 사용자 지정 구현된 워크플로우 단계를 모두 사용할 수 있습니다.

각 사후 처리 워크플로우의 마지막 단계가 `DAM Update Asset Workflow Completed Process`인지 확인합니다. 마지막 단계는 Experience Manager이 자산 처리가 완료되는 시점을 파악하는 데 도움이 됩니다.

### 사후 처리 워크플로우 실행 구성 {#configure-post-processing-workflow-execution}

자산 마이크로서비스가 업로드된 자산의 처리를 완료한 후 사후 처리 워크플로우를 정의하여 자산을 추가로 처리할 수 있습니다. 워크플로우 모델을 사용하여 사후 처리를 구성하려면 다음 중 하나를 수행할 수 있습니다.

* [폴더 속성에서 워크플로우 모델을 적용합니다](#apply-workflow-model-to-folder).
* [사용자 지정 워크플로우 러너 서비스를 구성합니다](#configure-custom-workflow-runner-service).

#### 폴더에 워크플로우 모델 적용 {#apply-workflow-model-to-folder}

일반적인 사후 처리 사용 사례의 경우 메서드를 사용하여 워크플로우를 폴더에 적용하는 것이 좋습니다. 폴더 [!UICONTROL 속성]에 워크플로우 모델을 적용하려면 다음 단계를 수행합니다.

1. 워크플로우 모델을 만듭니다.
1. 폴더를 선택하고 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 클릭한 다음 **[!UICONTROL 자산 처리]** 탭을 클릭합니다.
1. **[!UICONTROL 자동 시작 워크플로우]**&#x200B;에서 필요한 워크플로우를 선택하고 워크플로우의 제목을 제공한 다음 변경 사항을 저장합니다.

   ![속성의 폴더에 사후 처리 워크플로우 적용](assets/post-processing-profile-workflow-for-folders.png)

#### 사용자 지정 워크플로우 러너 서비스 구성 {#configure-custom-workflow-runner-service}

폴더에 워크플로우를 적용하여 쉽게 구현할 수 없는 고급 구성에 대한 사용자 지정 워크플로우 런너 서비스를 구성할 수 있습니다. 예를 들어 정규 표현식을 사용하는 워크플로우입니다. Adobe CQ DAM 사용자 지정 워크플로우 러너(`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`)는 OSGi 서비스입니다. 구성에 대해 다음 두 가지 옵션을 제공합니다.

* 경로별 사후 처리 워크플로우(`postProcWorkflowsByPath`): 다양한 저장소 경로에 따라 여러 워크플로우 모델을 나열할 수 있습니다. 콜론을 사용하여 경로와 모델을 구분합니다. 단순 저장소 경로가 지원됩니다. 이러한 매개 변수를 `/var` 경로의 워크플로우 모델에 매핑합니다. 예: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* 표현식에 의한 사후 처리 워크플로우(`postProcWorkflowsByExpression`): 다른 정규 표현식을 기반으로 하여 여러 워크플로우 모델을 나열할 수 있습니다. 표현식과 모델은 콜론으로 구분해야 합니다. 정규 표현식은 표현물이나 파일 중 하나를 지정하지 않고 자산 노드를 직접 가리켜야 합니다. 예: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

OSGi 구성을 배포하는 방법은 [배포 대상 [!DNL Experience Manager]](/help/implementing/deploying/overview.md)을 참조하십시오.

## 우수 사례 및 제한 사항 {#best-practices-limitations-tips}

* 워크플로우를 디자인할 때 모든 유형의 표현물에 대한 요구 사항을 고려합니다. 나중에 표현물이 필요할 것으로 예상하지 않으면 워크플로우에서 해당 작성 단계를 제거합니다. 변환은 나중에 일괄 삭제할 수 없습니다. 원치 않는 변환은 [!DNL Experience Manager]을 장시간 사용한 후에 많은 저장 공간이 필요할 수 있습니다. 개별 자산의 경우 사용자 인터페이스에서 렌디션을 수동으로 제거할 수 있습니다. 여러 자산의 경우 [!DNL Experience Manager]을 사용자 지정하여 특정 표현물을 삭제하거나 자산을 삭제하고 다시 업로드할 수 있습니다.
* 현재, 지원은 표현물 생성으로 제한됩니다. 새 자산을 생성할 수 없습니다.
* 현재 메타데이터 추출의 파일 크기 제한은 약 10GB입니다. 매우 큰 자산을 업로드할 때 메타데이터 추출 작업이 실패하는 경우가 있습니다.

>[!MORELIKETHIS]
>
>* [asset compute 서비스 소개](https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html).
>* [확장성 및 사용 시기를 이해합니다](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html).
>* [사용자 정의 응용 프로그램을 만드는 방법](https://experienceleague.adobe.com/docs/asset-compute/using/extend/develop-custom-application.html).
>* [다양한 사용 사례에 대해 지원되는 MIME 유형입니다](/help/assets/file-format-support.md).


<!-- TBD: 
* How/where can admins check what's already configured and provisioned.
* How/where to request for new provisioning/purchase.
-->
