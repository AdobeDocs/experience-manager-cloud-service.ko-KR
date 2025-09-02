---
title: OpenAPI 기능과 Dynamic Media를 사용하여 이미지 최적화
description: OpenAPI 기능이 포함된 Dynamic Media의 이미지 최적화 기능을 사용하여 공개 게재 전에 신속하게 이미지를 최적화하는 방법에 대해 알아봅니다
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 74c5fbda5ee1ad46b5fcab5ba89f0fd96873e3cf
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 0%

---


# OpenAPI 기능과 Dynamic Media를 사용하여 이미지 최적화{#Optimize-images-using-Dynamic-Media-with-OpenAPI-Capabilities}

[!DNL Dynamic Media with OpenAPI capabilities]은(는) [!DNL Smart Crop], [!DNL Image Presets] 및 [!DNL Smart Imaging]과(와) 같은 이미지 최적화 기능을 제공합니다. 이러한 기능은 다양한 디바이스와 네트워크에서 빠르게 로드되는 고품질의 반응형 이미지를 제공하는 데 도움이 됩니다.

## 스마트 자르기{#smart-crop-using-dynamic-media-with-openapi-capabilities}

[스마트 자르기](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request)은(는) [!DNL Dynamic Media with OpenAPI capabilities]의 동적 크기 조정 기능입니다. [!DNL Smart Crop]은(는) AI 기반 콘텐츠 인식 자르기를 사용하여 자른 버전의 시각적 컨텍스트를 유지하면서 다양한 화면 크기에 대한 이미지를 지능적으로 자르는 고급 이미지 처리 기술입니다. AI가 이미지를 분석해 초점이나 원하는 관심 지점을 파악한 뒤 자른 모든 버전에서 초점을 유지하도록 이미지를 자동으로 자른다. 반응형 디자인의 핵심 요소인 [!DNL Smart Crop]은(는) 비용 효율적이고 시간 효율적인 이미지 자르기 방법을 제공합니다.

[에서 ](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles)스마트 자르기 렌디션을 만들기[, ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#creating-image-profiles)폴더에 적용[!DNL Admin View] 또는 [렌디션을 편집](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#applying-an-image-profile-to-folders)하는 방법에 대해 알아보려면 [Dynamic Media 이미지 프로필](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#editing-the-smart-crop-or-smart-swatch-of-a-single-image) 문서를 참조하세요. 이 [!DNL Smart Crop]비디오[에서 단계별로 ](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use)을(를) 만드는 방법을 알아봅니다.

[!DNL Smart Crop] 매개 변수에는 명명된-smartcrop-profiles가 있고 자산에 적용되어야 합니다. [ 매개 변수 및 이름이 ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request)인 프로필이 적용되는 방법에 대한 자세한 내용은 [!DNL Smart Crop]스마트 자르기 프로필[!DNL Smart Crop]을 참조하세요.

>[!IMPORTANT]
>
> 관리자 보기에서만 [!DNL Smart Crop] 변환을 만들 수 있습니다.

## 이미지 사전 설정{#image-presets-using-dynamic-media-with-openapi-capabilities}

[의 ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=preset&t=request)이미지 사전 설정[!DNL Dynamic Media with OpenAPI capabilities] 기능을 사용하여 즉석으로 이미지를 변형하십시오. [!DNL image preset]은(는) 출력 이미지에 대해 미리 정의된 크기 조정 및 서식 규칙 집합입니다.

[!DNL Dynamic Media with OpenAPI capabilities]은(는) 사전 설정 이름을 사용하여 즉시 이미지를 변형하고 해당 렌디션을 즉시 생성합니다. 사전 설정 매개 변수가 포함된 [!DNL Dynamic Media with OpenAPI] 배달 URL을 통해 이미지를 요청하면 [!DNL DM with OpenAPI]에서 사전 설정의 변형을 적용하고 필요 시 렌디션을 만들어 사용자에게 전달합니다.

[!DNL Dynamic Media with OpenAPI] 게재 URL을 통해 여러 이미지에 하나의 사전 설정을 적용할 수 있습니다. 이렇게 하면 각 에셋을 수동으로 편집하지 않고도 에셋 간에 일관된 서식이 유지됩니다.

[이미지 사전 설정 관리](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets) 문서를 참조하여 [관리자 보기에서 이미지 사전 설정을 만드는 방법](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-image-presets)과 다른 화면 크기에 맞게 자산을 자동으로 조정하는 [응답형 이미지 사전 설정을 만드는 방법](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-a-responsive-image-preset)에 대해 알아보십시오.

### 이미지 사전 설정 사용의 이점{#benefits-of-image-presets}

[!DNL Image Presets]은(는) [!DNL Dynamic Media with OpenAPI]에서 이미지를 관리하고 전달하는 데 여러 가지 이점을 제공합니다. 몇 가지 주요 이점은 다음과 같습니다.

* 사전 설정을 사용하면 이미지 게재 URL이 더 짧아집니다. 게재 URL을 더 길게 만드는 여러 이미지 수정자를 추가하는 대신 단일 사전 설정을 사용하십시오. 짧은 URL을 사용하면 보다 쉽게 관리할 수 있으며 웹 사이트, 모바일 앱, 이메일 및 기타 채널 간에 일관된 이미지 제공을 보장합니다.
* 이미지 사전 설정은 소스 이미지 파일에서 just-in-time 변환을 만듭니다. 이 온디맨드 렌디션 생성 기능을 사용하면 동일한 파일의 정적 렌디션을 여러 개 만들고 저장할 필요가 없으므로 시간과 저장소가 절약됩니다.
* 한 번에 하나의 사전 설정을 큰 에셋 세트에 적용하여 각 에셋을 개별적으로 수동으로 편집하지 않고 일관된 서식을 보장하며 확장성을 활성화합니다.
* 사전 설정의 매개 변수를 업데이트하면 해당 사전 설정을 사용하는 모든 이미지의 형식이 자동으로 다시 지정됩니다. 이렇게 하면 서식 업데이트가 중앙 집중화되므로 개별 에셋이나 웹 코드를 다시 편집할 필요가 없어 편집 작업이 간소화됩니다.
* CDN에서 캐시한 동적 변환을 통해 효율성과 성능을 향상시켜 전체 장치와 네트워크에서 로드 속도가 빨라지고 성능이 최적화됩니다.

### 이미지 사전 설정 사용{#use-image-presets-using-dynamic-media-with-openapi-capabilities}

[!DNL Image Presets]을(를) 만든 후 다음 워크플로에 사용할 수 있습니다.
* [이미지 게재 URL의 사전 설정을 사용하여 최종 사용자에게 전달하기 전에 바로 렌디션을 만듭니다](#use-presets-in-delivery-urls)
* [AEM Sites에서 작성하는 동안 사전 설정 사용](#use-presets-during-authoring-in-aem-sites)

#### 이미지 게재 URL에서 사전 설정 사용{#use-presets-in-delivery-urls}

사전 설정을 사용하면 게재 URL을 더 짧고 쉽게 사용할 수 있습니다.  각 사전 설정 이름은 게재 URL에서 고유 식별자 역할을 합니다. 에셋의 게재 URL에 여러 수정자를 추가하는 대신 사전 설정 이름을 참조하여 렌디션을 즉시 생성합니다. [Dynamic Media 이미지 사전 설정을 이미지에 적용하는 방법에 대해 알아봅니다](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-presets).
다음 예제에서는 사전 설정이 있는 URL과 사전 설정이 없는 URL을 비교합니다.

**사전 설정이 없는 URL(긴 URL)**:

`https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?width=400&height=300&fit=crop&qualit=85&sharpen=true`

**사전 설정이 있는 URL(짧은 URL)**:

`https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?preset=thumbnail`.
사전 설정 썸네일은 동일한 이미지 수정자 설정을 번들로 묶습니다.

#### AEM Sites에서 작성하는 동안 사전 설정 사용{#use-presets-during-authoring-in-aem-sites}

[!DNL Image Presets] 지원이 활성화된 경우 작성자가 [!DNL AEM Sites] 작성 페이지에서 페이지를 편집하는 동안 [!DNL Dynamic Media]을(를) 선택할 수 있습니다.
작성 페이지에서 이미지 사전 설정을 사용하려면 다음 단계를 수행하십시오.
1. 사이트 작성 페이지로 이동합니다.
1. [AEM 페이지 편집기에서 원격 자산 액세스](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) 섹션의 단계를 실행하여 [!DNL Asset Selector] 패널을 사용하여 자산을 선택하십시오.
1. [!DNL asset selector] 패널에서 **[!UICONTROL 사전 설정 형식]**(으)로 스크롤하고 `Preset=Preset Name`이미지 수정자&#x200B;**[!UICONTROL 필드에]**&#x200B;을(를) 지정합니다.
   ![사전 설정](/help/assets/assets/preset-in-asset-selector-panel.png)

## 스마트 이미징{#use-smart-imaging-using-dynamic-media-with-openapi-capabilities}

이미지 게재에 [!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하면 [스마트 이미징](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/)을 통해 이미지가 자동으로 최적화됩니다. 최적화된 전달을 통해 이미지 로드 속도 향상, 시각적 품질 극대화, 파일 크기 최소화 등의 이점을 얻을 수 있습니다. 따라서 전체 장치와 네트워크에서 페이지를 가장 빠르게 로드하고 일관되게 높은 시각적 품질을 제공하는 동시에 최소한의 대역폭을 소비하여 웹 사이트를 더 빠르고 반응하게 만듭니다.

[!DNL Smart Imaging]에는 다음 기능이 포함되어 있습니다.
* [자동 포맷 전환](#auto-format-conversion)
* [네트워크 대역폭 최적화](#network-bandwidth-optimisation)

### 자동 포맷 전환{#auto-format-conversion}

[!DNL Dynamic Media with OpenAPI] [이미지를 AVIF 또는 WEBP와 같은 웹에 최적화된 최신 형식으로 자동 변환](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=auto-format&t=request). 전환은 요청된 형식에 관계없이 브라우저의 기능과 [라이선스 권한](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate)에 따라 다릅니다.
AVIF 및 WEBP 형식은 더 나은 압축을 제공하여 이미지를 더 작고 빠르게 전달 및 로드할 수 있도록 합니다. AVIF는 모든 브라우저 기능을 처리할 때 기본 형식으로 사용됩니다.
[!DNL Dynamic Media with OpenAPI]은(는) `auto-format` 쿼리 매개 변수를 사용하여 최적화된 배달을 위해 이미지를 다양한 형식으로 변환하는 브라우저의 동작을 제어합니다. 자동 형식 전환에는 **자동 승격** 및 **자동 강등**&#x200B;이 포함됩니다. 시스템이 전달을 위해 JPEG 또는 PNG보다 웹에 최적화된 형식(AVIF 또는 WEBP)을 프로모션하는 것을 자동 프로모션이라고 합니다.

기본적으로 `auto-format` 쿼리 매개 변수는 `true`(으)로 설정됩니다. `auto-format`을(를) 사용하도록 설정하면(true) 시스템에서 요청된 형식을 무시하고 이미지 특성, 브라우저 기능 및 [라이선스 권한](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate)에 따라 웹에 최적화된 형식(AVIF 또는 WEBP)을 자동으로 선택합니다.

`auto-format`이(가) true이면 시스템은 다음 순서로 이미지 형식을 전달합니다.
* ***AVIF***: 브라우저가 지원하고 라이선스에서 허용하는 경우 AVIF가 전달됩니다. 이를 자동 프로모션이라고 합니다.
* ***WEBP***: AVIF가 지원되지 않거나 사용이 허가되지 않은 경우 WEBP가 전달됩니다. 자동 프로모션이기도 합니다.
* ***JPEG***: AVIF 및 WEBP가 지원되지 않고 이미지에 알파 채널(투명도)이 없는 경우에만 JPEG이 제공됩니다. 이를 자동 강등이라고 합니다.
* ***PNG***: 브라우저가 최신 형식을 지원하지 않고 이미지에 알파 채널(투명도)이 있는 경우 PNG가 전달됩니다. 이는 자동 강등이라고도 합니다.

쿼리 매개 변수를 `auto-format`(으)로 설정하여 `false`을(를) 사용하지 않도록 설정한 다음 필요한 형식을 지정하여 해당 형식으로 제공된 이미지를 가져옵니다.

### 네트워크 대역폭 최적화{#network-bandwidth-optimisation}

이미지는 클라이언트의 네트워크 상태에 따라 자동으로 최적화되므로 더 빠른 게재와 원활한 로드를 보장합니다. [Quality](#quality-parameter) 및 [Max-Quality](#max-quality-parameter) 매개 변수는 이미지 압축 수준을 제어하여 품질을 자동으로 조정합니다. 값은 1에서 100 사이입니다.

`quality` 및 `max-quality ` 매개 변수의 다음 주요 동작을 참조하십시오.

* [!DNL quality]과(와) [!DNL max-quality]을(를) 모두 지정하면 [!DNL quality]이(가) 우선합니다.
* [!DNL quality]만 지정하면 네트워크 속도에 따라 로드 시간과 관계없이 품질이 제공됩니다.
* [!DNL max-quality]만 지정하면 네트워크 상태에 따라 이미지 품질이 자동으로 조정되어 최상의 품질을 지정된 [!DNL max-quality] 값까지 제공합니다.
* 둘 다 지정되지 않은 경우 시스템은 `max-quality`의 기본값 `85`을(를) 사용하여 동적 최적화를 적용합니다.

#### 품질 매개 변수{#quality-parameter}

품질 매개 변수는 로드 속도보다 이미지 품질의 우선 순위를 지정합니다. 출력 이미지 품질을 요청된 값(1에서 100 사이)으로 수정하고 네트워크 조건을 무시합니다. [품질 매개 변수](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request)에 대해 자세히 알아보세요.

#### 최대 품질 매개 변수{#max-quality-parameter}

최대 품질은 클라이언트의 네트워크 속도에 따라 이미지 품질과 로드 시간의 균형을 맞춥니다. 속도가 느린 네트워크의 이미지 품질을 낮춰 더 빠른 로드 시간을 우선시하는 동시에 주어진 네트워크 조건에 가장 높은 품질(1-100)을 제공합니다. [최대 품질 매개 변수](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request)에 대해 자세히 알아보세요.



