---
title: ' [!DNL AEM Assets] 의 콘텐츠를 작성하는 동안  [!DNL Edge Delivery Services]통합'
description: ' [!DNL AEM Assets] 다음 항목 [!DNL Edge Delivery Services]. This integration enables you to integrate [!DNL AEM Assets] 다음 항목 [!DNL Microsoft Word] 포함 [!DNL Google Docs], integrate [!DNL AEM Assets] 다음 항목 [!DNL Universal Editor], integrate [!DNL Dynamic Media] 다음 항목 [!DNL Edge Delivery Services], integrate [!DNL Dynamic Media with OpenAPI capabilities] 다음 항목 [!DNL Universal Editor] 통합 [!DNL Dynamic Media with OpenAPI capabilities] 다음 항목 [!DNL Microsoft Word] 및 [!DNL Google Docs]을 통합하는 방법에 대해 알아봅니다.'
tags: AEM Assets, Edge Delivery Services, Dynamic Media, Dynamic Media with OpenAPI capabilities, Universal Editor, Edge Delivery Services with Universal Editor
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: 79213bcfe5c5ccf7c60a31e6cb757f60a0ba87a7
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---


# [!DNL AEM Assets]의 콘텐츠를 작성하는 동안 [!DNL Edge Delivery Services] 통합 {#integrate-aem-assets-with-edge-delivery-services}

![범용 편집기와 AEM 자산 통합](/help/assets/assets/EDS2.png)

[[!DNL Edge Delivery Services]](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/overview)은(는) 구성 가능한 서비스 집합으로, 웹 사이트에서 콘텐츠를 작성하고 전달하는 방법에 대해 높은 수준의 유연성을 제공합니다. [AEM 콘텐츠 관리](/help/sites-cloud/authoring/author-publish.md) 및 [WYSIWYG 작성은  [!DNL Universal Editor] 뿐만 아니라 문서 기반 작성](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)을 사용하여 모두 사용할 수 있습니다.

다음 위치에서 콘텐츠를 편집할 수 있습니다.

* [[!DNL Microsoft Word] 또는 [!DNL Google Docs]](#integrate-dynamic-media-with-edge-delivery-services)
* [[!DNL Universal Editor]](#integrate-aem-assets-with-universal-editor-UE)

콘텐츠를 편집한 후 Edge Delivery Services에 게시할 수 있습니다.

## [!DNL AEM Assets]의 문서 기반 작성 흐름과 [!DNL Edge Delivery Services] 통합 {#integrate-dynamic-media-with-edge-delivery-services}

[!DNL AEM Assets]이(가) [!DNL Microsoft Word] 또는 [!DNL Google Docs]과(와) 같은 문서 기반 작성 도구와 통합되면 작성 도구에 자산 선택기를 제공합니다. 이 자산 선택기를 사용하여 [!DNL AEM Assets]에 액세스하고 승인된 자산을 콘텐츠에 삽입합니다.
[!DNL Edge Delivery Services] 웹 사이트가 이미 있는 경우 [[!DNL AEM Assets] plugin](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) 설명서를 참조하여 [!DNL AEM Assets]을(를) 기존 [!DNL AEM] 프로젝트와 통합하는 방법에 대해 알아보십시오.
문서 기반 작성 도구에서 작성한 [ 포함 콘텐츠를 게시할 ](#integrate-aem-assets-with-microsoft-word-and-google-docs) 웹 사이트가 없는 경우 다음 [필수 구성 요소 [!DNL AEM Assets]  및 ](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs)문서 기반 작성 환경과 통합[!DNL Edge Delivery Services]하기[!DNL AEM Assets] 섹션을 따르십시오.

### 사전 요구 사항{#integrate-aem-assets-with-microsoft-word-and-google-docs}

시작하기 전에 문서 기반 작성 환경이 준비되었는지 확인합니다.

* [!DNL AEM]을(를) 문서 기반 작성 도구와 통합하여 작성 환경을 설정합니다. 작성 환경을 설정하는 방법에 대해 알아보려면 [시작하기 - 개발자 자습서](https://www.aem.live/developer/tutorial)를 참조하십시오.

### 문서 기반 작성 환경과 [!DNL AEM Assets] 통합{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

[!DNL AEM Assets] 또는 [!DNL Microsoft Word]에서 콘텐츠를 작성하는 동안 에셋을 사용하도록 [!DNL Google Docs] Sidekick 플러그인을 구성하십시오.

* Microsoft Word 또는 Google Docs에서 AEM Assets에 액세스하고 사용하는 방법에 대해 알아보려면 [[!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors)을(를) 참조하십시오.
* 구성 세부 정보는 [구성 [!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin)을 참조하십시오.
  ![ms word 및 google 문서에서 openAPI 기능과 함께 dynamic media 사용](/help/assets/assets/my-assets-sidebar.png)

## [!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하여 자산 게재 {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

[!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하여 전달된 에셋을 사용할 수도 있습니다. 다음과 같은 많은 이점을 제공합니다.

* [!DNL AEM Assets Cloud Services]에서 브랜드 승인 에셋(이미지, 비디오, PDF 및 기타 에셋 유형)에만 액세스할 수 있습니다.
* 거버넌스 (에셋 참조와 사본 비교)를 통해 만료, 삭제 및 업데이트와 같은 에셋 라이프사이클 이벤트를 자동으로 전파할 수 있습니다.
* 동적 이미지 렌디션 및 스마트 자르기.
* 즉시 사용 가능한 적응형 비디오 스트리밍 및 PDF용 원본 에셋 제공과 같은 리치 미디어 최적화 및 제공.
<!--

* Asset-level impressions report ([limited availability](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

-->

기능에 대한 자세한 내용은 [[!DNL Dynamic Media with OpenAPI capabilities]](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview) 설명서를 참조하십시오.

### 사전 요구 사항 {#dynamic-media-with-universal-editor-and-edge-delivery-services}

에셋 참조를 사용하려면 다음을 수행해야 합니다.

* [!DNL Dynamic Media with Open API capabilities]이(가) 활성화된 Assets Cloud Service 환경에 대한 권한 부여.
* [!DNL Dynamic Media] 라이선스.
* 이미지 에셋에 대한 복사 참조가 활성화된 [!DNL AEM Assets sidekick plugin]이(가) 활성화되었습니다. 자세한 내용은 문서 기반 작성에 대해서는 [이 설명서](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode)를 참조하고 유니버설 편집기 기반 작성에 대해서는 [이 설명서](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview)를 참조하십시오.
* Assets이 승인되었습니다. 승인된 자산에는 Assets Cloud Services 백 엔드 또는 UI 작업을 통해 `dam:status=Approved`이(가) 있습니다.

### [!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하여 전달된 자산 사용{#Using-Dynamic-Media-with-edge-delivery-services}

[!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하여 콘텐츠의 이미지, 비디오 및 기타 에셋 유형을 전달하는 방법을 알아보려면 다음 링크를 선택하십시오.

* [콘텐츠에 이미지 추가](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [콘텐츠에 비디오 추가](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [콘텐츠에 PDF, Zip 파일 등 이미지가 아닌 자산과 비디오 자산을 추가하십시오.](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

OpenAPI 기능과 Dynamic Media를 사용하여 콘텐츠의 자산을 전달하는 방법을 배우려면 이 비디오 를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## 샘플 [!DNL Edge Delivery Services] 사이트{#dynamic-media-with-google-docs-and-ms-word}

[의 문서 기반 작성 기능을 사용하여 빌드된 사이트인 ](https://aem-dynamicmedia-demo--dm--hlxsites.aem.live/travel-hospitality/wknd-trvl-home)WKND Travel[!DNL Edge Delivery Services]을 참조하십시오. 사이트의 컨텐츠는 [Google Docs](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT)에서 작성되었으며 [!DNL Dynamic Media with OpenAPI capabilities]은(는) 컨텐츠의 자산을 전달하는 데 사용됩니다. 작성 후 컨텐츠는 문서에서 직접 게시됩니다. 이 [ 사이트에 대한 문서 기반 작성 설정을 만드는 데 사용되는 모든 필수 파일, 폴더, 구성, 웹 사이트의 스타일 및 기능 코드에 대해 알아보려면 이 ](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks)Git 저장소[!DNL Edge Delivery Services (EDS)]를 살펴보십시오.

## [!DNL AEM Assets]에 대해 [!DNL Universal Editor]을(를) [!DNL Edge Delivery Services] 기반 작성 흐름과 통합 {#integrate-aem-assets-with-universal-editor-UE}

[!DNL Universal Editor]과(와) 통합하도록 [!DNL AEM Assets]을(를) 설정합니다. 이 통합을 통해 [!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하여 자산을 전달할 수 있습니다.

* [에서 사용자 지정 자산 선택 함수를 추가하는 방법에 대해 알아보려면  [!DNL Edge Delivery] Configuration in](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site)Site[!DNL Universal Editor]을 참조하세요. 사용자 지정 에셋 선택기를 사용하면 에셋을 [!DNL Universal Editor] 콘텐츠에 직접 삽입할 수 있습니다.
* [에서 작성하는 동안 ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview)에 액세스하고 자산을 삽입하는 방법을 알아보려면 [!DNL AEM Assets]확장 개요[!DNL Universal Editor]를 참조하십시오.
