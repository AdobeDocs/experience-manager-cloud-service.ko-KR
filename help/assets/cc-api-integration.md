---
title: Creative Cloud 통합을 위한 컨텐츠 자동화
description: Creative Cloud 통합을 사용하여 에셋 변형 생성
contentOwner: AG
feature: Upload, Asset Processing, Publishing, Asset Compute Microservices
role: User, Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 5%

---

# [!DNL Adobe Creative Cloud] 통합을 사용하여 자산의 변형 생성 {#content-automation}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

콘텐츠 자동화 추가 기능은 [!DNL Adobe Experience Manager Assets]을(를) [!DNL Cloud Service] 및 [!DNL Adobe Creative Cloud] API로 통합하여 규모에 맞게 창의적으로 자산을 처리합니다. [!DNL Experience Manager]은(는) 클라우드 기반의 [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용하여 [!DNL Adobe Creative Cloud] 기능을 사용하고 에셋 생성 및 미디어 처리를 자동화합니다.

[!DNL Adobe Photoshop] 및 [!DNL Adobe Lightroom]에서 자산을 편집하려면 [!DNL Experience Manager Assets]에서 자산을 다운로드하고 편집한 다음 다시 업로드할 필요가 없습니다. [!DNL Experience Manager]에서 처리 프로필을 만들고 구성하고, 프로필을 폴더에 적용하고, 에셋을 폴더에 업로드합니다. 업로드한 에셋은 처리 프로필에 따라 재처리되며 이러한 에셋의 변형을 얻을 수 있습니다. 일관되고 간편한 일괄 처리를 통해 수작업을 절약하고 컨텐츠 속도를 높일 수 있으므로 탁월한 크리에이티브 능력이 필요하지 않습니다. 또한 개발자와 파트너는 이러한 API에 직접 액세스하여 에셋 마이크로서비스를 확장하고 사용자 정의 논리를 포함할 수 있습니다.

사용자는 처리 프로필을 만들어 자산에 대한 다음 크리에이티브 작업을 자동화할 수 있습니다.

* **자동 톤**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 고유한 특성을 기반으로 빛과 색상을 지능적으로 수정합니다.

* **자동 올리기**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 왜곡된 관점을 수정합니다. 예를 들어 레벨 지표를 생성합니다.

  ![자동 톤](/help/assets/assets/content-automation-autotone.png)

  *그림: 자동 톤 및 자동 펴기를 사용하면 왜곡된 이미지를 개선할 수 있습니다.*

* **Lightroom 사전 설정**: 사용자 지정 사전 설정을 사용하여 일관된 모양을 얻기 위해 이미지에 사용자 정의 모양을 적용합니다.

  ![Lightroom 사전 설정](/help/assets/assets/content-automation-lrpresets.png)

  *그림: 많은 이미지에 대해 일관된 방식으로 이미지 품질을 개선하기 위한 Adobe Lightroom 사전 설정입니다.*

* **이미지 오려내기**: 인공 지능을 사용하여 중요 개체 주변에 선택 영역을 만들고 단일 명령으로 배경을 제거합니다.

  ![배경을 제거하고 사진에서 이미지를 잘라냅니다](/help/assets/assets/content-automation-backgroundremove.png)

* **이미지 마스크**: 단일 명령으로 중요 개체 주변에 마스크를 만드는 데 인공 지능을 사용합니다.

  ![AI를 사용하여 이미지 마스킹](/help/assets/assets/content-automation-mask.png)

* **Photoshop 작업**: 일련의 [!DNL Adobe Photoshop] 작업을 파일이나 파일 배치에 적용합니다.

  ![Photoshop 작업](/help/assets/assets/content-automation-psactions.png)

* **스마트 개체 바꾸기**: PSD 파일 내에 적용된 모든 효과와 조정을 유지하면서 이미지를 교환할 수 있도록 하여 규모에 맞게 개인화를 수행합니다.

  ![개체 스마트 바꾸기](/help/assets/assets/content-automation-objectreplace.png)

## AEM as a Cloud Service 프로그램을 위한 컨텐츠 자동화 활성화 {#enable-content-automation}

Cloud Manager을 사용하여 AEM as a Cloud Service 프로그램용 Content Automation 추가 기능을 활성화하려면 다음을 수행합니다.

1. 콘텐츠 자동화 추가 기능에 라이선스를 부여하려면 계정 담당자에게 문의하십시오.
1. Cloud Manager에 액세스하고 조직 선택기를 사용하여 조직으로 전환합니다.
1. **[!UICONTROL 프로그램 추가]**&#x200B;를 클릭하고 프로그램 이름을 지정하십시오.
1. **[!UICONTROL 계속]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Assets]**&#x200B;을(를) 확장하고 **[!UICONTROL 콘텐츠 자동화]**&#x200B;를 선택합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 파이프라인을 실행하여 [변경 내용을 Cloud Manager에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html)합니다.

Cloud Manager의 기존 AEM as a Cloud Service 프로그램에 컨텐츠 자동화 추가 기능을 추가해야 하는 경우

1. 프로그램 카드에서 ...를 클릭합니다.

1. **[!UICONTROL 프로그램 편집]**&#x200B;을 선택한 다음 **[!UICONTROL 솔루션 및 추가 기능]** 탭을 선택하십시오.

1. **[!UICONTROL Assets]**&#x200B;을(를) 확장하고 **[!UICONTROL 콘텐츠 자동화]**&#x200B;를 선택합니다.
1. **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.
1. 파이프라인을 실행하여 [변경 내용을 Cloud Manager에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html)합니다.

## 처리 프로필을 사용하여 크리에이티브 에셋을 일괄적으로 편집 {#process-assets}

처리 프로필을 사용하여 자동으로 변형을 만들려면 다음 단계를 수행합니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 처리 프로필]**&#x200B;로 이동합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하고 **[!UICONTROL 이름]**&#x200B;을(를) 지정하십시오.

1. **[!UICONTROL Creative]** 탭을 선택하고 출력 폴더를 지정한 다음 **[!UICONTROL 새로 추가]**&#x200B;를 선택하여 Creative 구성을 추가합니다.

1. **[!UICONTROL 렌디션 이름]**(또는 출력 이름), **[!UICONTROL 확장]**(또는 파일 형식)을 제공하고, **[!UICONTROL 품질]**(또는 출력 매개 변수)을 선택하고, **[!UICONTROL 포함]** 및 **[!UICONTROL 제외]** MIME 형식 목록(또는 입력 에셋 필터)을 선택한 다음 필요한 크리에이티브 작업을 선택하십시오.

   [!UICONTROL 처리 프로필]](assets/creative-processing-profile.png)의 ![[!UICONTROL Creative] 탭

1. 일부 작업에는 추가 매개 변수(에셋)가 필요합니다. 필요한 경우 이러한 추가 매개 변수의 값을 제공합니다.

1. 동일한 처리 프로필의 일부로 더 많은 크리에이티브 작업을 추가하거나 프로필을 저장합니다.

1. 폴더에 처리 프로필을 적용합니다. 폴더의 **[!UICONTROL 속성]** 페이지에서 **[!UICONTROL 자산 처리]**&#x200B;를 선택하고 적용할 처리 프로필을 선택하십시오.

처리 프로필을 DAM 폴더에 적용하면 이 폴더에서 업로드되거나 업데이트된 모든 에셋이 표준 처리와 함께 정의된 작업을 실행합니다. 하위 폴더는 상위 폴더에 적용된 것과 동일한 프로필을 상속합니다. 사용자는 이 상속을 재정의할 수 있습니다.

기존 자산을 처리하려면 자산을 선택하고 **[!UICONTROL 재처리]** 옵션을 선택한 다음 필요한 처리 프로필을 선택하십시오.

## 팁 및 제한 사항 {#limitations-best-practices}

* [!DNL Experience Manager]은(는) 자산 처리를 환경당 분당 300개 요청 및 조직당 분당 700개 요청으로 제한합니다.
* 파일 크기는 [!DNL Adobe Photoshop] API 작업의 경우 4GB로 제한되고 [!DNL Adobe Lightroom] 작업의 경우 1GB로 제한됩니다.

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [처리 프로필을 통해 자산 마이크로서비스 구성 및 사용](/help/assets/asset-microservices-configure-and-use.md).
>* [통합 [!DNL Experience Manager] 와 [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [자산 마이크로서비스를 사용한 자산 수집 및 처리: 개요](/help/assets/asset-microservices-overview.md).
