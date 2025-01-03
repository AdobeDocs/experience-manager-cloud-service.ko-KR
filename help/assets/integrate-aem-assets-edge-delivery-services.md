---
title: AEM Assets를 통합하면서 Edge Delivery Services용 콘텐츠 작성
description: AEM Assets을 Edge Delivery Services과 통합하는 방법을 알아봅니다. 이 통합을 통해 AEM Assets을 Microsoft Word 및 Google 문서와 통합하고, AEM Assets을 범용 편집기와 통합하고, Dynamic Media을 OpenAPI 기능과 통합하고, Dynamic Media을 OpenAPI 기능과 통합하여 Microsoft Word 및 Google 문서를 통합할 수 있습니다.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: e6fd7b1d16aac5e7021a8c309f6483f98746e85e
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 3%

---

# AEM Assets를 통합하면서 Edge Delivery Services용 콘텐츠 작성 {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

![EDS2](/help/assets/assets/EDS2.png)

[Edge Delivery Services](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/overview)은(는) 구성 가능한 서비스 집합으로, 웹 사이트에서 콘텐츠를 작성하고 전달하는 방법에 대해 높은 수준의 유연성을 제공합니다. 범용 편집기와 문서 기반 작성](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)을 사용하여 [AEM 콘텐츠 관리](/help/sites-cloud/authoring/author-publish.md) 및 [WYSIWYG 작성을 모두 사용할 수 있습니다.

다음 위치에서 콘텐츠를 편집할 수 있습니다.

* [Microsoft Word 또는 Google 문서](#integrate-aem-assets-with-document-based-authoring-tools)

* [범용 편집기](#integrate-aem-assets-with-universal-editor)

콘텐츠를 편집한 후 Edge Delivery Services에 게시할 수 있습니다.

## AEM Assets과 Edge Delivery Services의 문서 기반 작성 플로우 통합 {#integrate-aem-assets-with-document-based-authoring-tools}

Microsoft Word 또는 Google 문서와 같은 문서 기반 작성 도구와 AEM Assets 통합은 편집기에 자산 선택기를 직접 제공합니다. 이 에셋 선택기를 사용하여 AEM Assets에 액세스하고 승인된 에셋을 문서에 삽입합니다.

이미 Edge Delivery Services 웹 사이트가 있는 경우 [AEM Assets 플러그인](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md)을 참조하여 AEM Assets을 기존 AEM 프로젝트와 통합하십시오. Edge Delivery Services 웹 사이트가 없는 경우 아래 [필수 구성 요소](#integrate-aem-assets-with-microsoft-word-and-google-docs) 및 [문서 기반 작성 환경과 AEM Assets 통합](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs) 섹션을 참조하십시오.

### 사전 요구 사항{#integrate-aem-assets-with-microsoft-word-and-google-docs}

시작하기 전에 문서 기반 작성 환경이 준비되었는지 확인합니다.

* 문서 기반 작성 도구와 AEM을 통합하여 작성 환경을 설정합니다. 작성 환경을 설정하려면 [시작하기 - 개발자 자습서](https://www.aem.live/developer/tutorial)를 참조하십시오.

### 문서 기반 작성 환경과 AEM Assets 통합{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Microsoft Word 또는 AEM Assets 문서에서 콘텐츠를 작성하는 동안 에셋을 사용하도록 Google Sidekick 플러그인을 구성합니다.

* Microsoft Word 또는 Google 문서에서 AEM Assets에 액세스하고 사용하는 방법에 대해 알아보려면 [Adobe Experience Manager Assets Sidekick 플러그인](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors)을 참조하십시오.
* 구성 세부 정보는 [Adobe Experience Manager Assets Sidekick 플러그인 구성](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin)을 참조하십시오.
  ![my-assets-sidebar](/help/assets/assets/my-assets-sidebar.png)

## OpenAPI 기능과 함께 Dynamic Media을 사용하여 자산 제공 {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

OpenAPI 기능과 함께 DM을 사용하여 제공되는 에셋을 사용할 수도 있습니다. 다음과 같은 많은 이점을 제공합니다.

* AEM Assets Cloud Service에서 브랜드 승인 에셋(이미지, 비디오, PDF 및 기타 에셋 유형)에만 액세스합니다.
* 거버넌스 (에셋 참조와 사본 비교)를 통해 만료, 삭제 및 업데이트와 같은 에셋 라이프사이클 이벤트를 자동으로 전파할 수 있습니다.
* 동적 이미지 렌디션 및 스마트 자르기.
* 즉시 사용할 수 있는 적응형 비디오 스트리밍 및 PDF을 위한 원본 에셋 제공과 같은 리치 미디어 최적화 및 제공.
* 자산 수준 노출 횟수 보고서([제한된 가용성](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

기능에 대한 자세한 내용은 [OpenAPI 기능이 있는 Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview) 설명서를 참조하십시오.

### 사전 요구 사항 {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

에셋 참조를 사용하려면 다음을 수행해야 합니다.

* Open API 기능이 있는 Assets이 활성화된 Dynamic Media Cloud Service 환경에 대한 권한.
* Dynamic Media 라이선스.
* AEM Assets 사이드 킥 플러그인이 활성화되었으며 이미지 에셋에 대한 복사 참조가 활성화되었습니다. 자세한 내용은 문서 기반 작성에 대해서는 [this](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode)을(를) 참조하고 유니버설 편집기 기반 작성에 대해서는 [this](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview)을(를) 참조하십시오.
* Assets이 승인되었습니다. 승인된 자산에는 Assets Cloud Service 백엔드 또는 UI 작업을 통해 `dam:status=Approved`이(가) 있습니다.

### OpenAPI 기능과 함께 Dynamic Media을 사용하여 제공된 에셋 사용{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

OpenAPI 기능과 함께 Dynamic Media을 사용하여 제공되는 에셋을 사용하면서 콘텐츠를 작성하려면 다음을 참조하십시오.

* [이미지 참조 사용](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [비디오 참조 사용](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [PDF, Zip 파일 등과 같은 비이미지 및 비디오 자산에 대한 자산 참조 사용](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

OpenAPI 기능과 함께 Dynamic Media을 사용하여 에셋을 제공하는 방법을 알아보려면 이 비디오 를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## 샘플 Edge Delivery Services 사이트{#example-of-an-Edge-Delivery-Services-site}

[WKND 여행](https://aem-dynamicmedia-demo--dm--hlxsites.aem.live/travel-hospitality/wknd-trvl-home)을 참조하세요. 이 사이트는 Edge Delivery Services의 문서 기반 작성 기능을 사용하여 빌드됩니다. 자산 전달을 위해 Dynamic Media과 함께 OpenAPI 기능을 사용하여 사이트의 콘텐츠를 [Google 문서](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT)에서 작성합니다. 작성된 콘텐츠는 문서에서 직접 게시됩니다. 이 문서 기반 작성 설정의 경우 모든 필수 파일, 폴더, 구성, 웹 사이트의 스타일 및 기능 코드가 이 [Git 저장소](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks)에 저장됩니다.

## AEM Assets과 Edge Delivery Services의 범용 편집기 기반 작성 플로우 통합 {#integrate-aem-assets-with-universal-editor}

AEM Assets과 통합하도록 범용 편집기를 설정합니다. 이 통합을 통해 OpenAPI 기능과 함께 Dynamic Media을 사용하여 에셋을 게재할 수 있습니다.

* 범용 편집기에서 사용자 지정 자산 선택기 함수를 추가하려면 [Edge Delivery 사이트의 구성](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site)을 참조하십시오. 사용자 지정 에셋 선택기를 사용하면 에셋을 유니버설 편집기 콘텐츠에 직접 삽입할 수 있습니다.
* 범용 편집기에서 작성하는 동안 AEM Assets에 액세스하고 자산을 삽입하는 방법을 알아보려면 [확장 개요](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview)를 참조하십시오.
