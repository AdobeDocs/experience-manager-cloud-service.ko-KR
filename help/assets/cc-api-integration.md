---
title: Creative Cloud 통합을 위한 컨텐츠 자동화
description: Creative Cloud 통합을 사용하여 에셋 변형 생성
contentOwner: AG
feature: Upload,Asset Processing,Publishing,Asset Compute Microservices,Workflow
role: User,Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 4%

---

# 을 사용하여 에셋의 변형 생성 [!DNL Adobe Creative Cloud] 통합 {#content-automation}

컨텐츠 자동화 추가 기능 통합 [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] 및 [!DNL Adobe Creative Cloud] 규모에 맞게 자산을 창의적으로 처리하기 위한 API입니다. [!DNL Experience Manager] 클라우드 기반 사용 [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md) 을(를) 사용하려면 [!DNL Adobe Creative Cloud] 자산 작성 및 미디어 처리를 자동화하는 기능입니다.

에서 에셋을 편집하려면 [!DNL Adobe Photoshop] 및 [!DNL Adobe Lightroom]에서 에셋을 다운로드할 필요는 없습니다. [!DNL Experience Manager Assets], 편집하고 다시 업로드하십시오. 에서 처리 프로필을 만들고 구성합니다 [!DNL Experience Manager]을 클릭하고, 폴더에 프로필을 적용하고, 폴더에 에셋을 업로드합니다. 업로드한 에셋은 처리 프로필에 따라 재처리되며 이러한 에셋의 변형을 얻을 수 있습니다. 일관되고 간편한 일괄 처리를 통해 수작업을 절약하고 컨텐츠 속도를 높일 수 있으므로 탁월한 크리에이티브 능력이 필요하지 않습니다. 또한 개발자와 파트너는 이러한 API에 직접 액세스하여 에셋 마이크로서비스를 확장하고 사용자 정의 논리를 포함할 수 있습니다.

사용자는 처리 프로필을 만들어 자산에 대한 다음 크리에이티브 작업을 자동화할 수 있습니다.

* **자동 톤**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 고유한 속성을 기반으로 지능적으로 빛 및 색 보정을 수행합니다.

* **자동 올림**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지에서 왜곡된 관점을 수정합니다. 예를 들어 레벨 지표를 생성합니다.

   ![자동 톤](/help/assets/assets/content-automation-autotone.png)

   *그림: 자동 톤 및 자동 곧게 펴기를 사용하면 왜곡된 이미지를 개선할 수 있습니다.*

* **Lightroom 사전 설정**: 사용자 정의 사전 설정을 사용하여 일관된 모양을 얻기 위해 이미지에 사용자 정의 모양을 적용합니다.

   ![Lightroom 사전 설정](/help/assets/assets/content-automation-lrpresets.png)

   *그림: 많은 이미지에 대해 일관된 방식으로 이미지 품질을 개선하기 위한 Adobe Lightroom 사전 설정.*

* **이미지 오려내기**: 인공 지능을 사용하여 현란한 오브젝트 주위에 선택 영역을 만들고 단일 명령으로 배경을 제거합니다.

   ![배경을 제거하고 사진에서 이미지 잘라내기](/help/assets/assets/content-automation-backgroundremove.png)

* **이미지 마스크**: 단일 명령으로 중요 오브젝트 주위에 마스크를 만들기 위해 인공 지능을 사용합니다.

   ![AI를 사용하여 이미지 마스크](/help/assets/assets/content-automation-mask.png)

* **Photoshop 작업**: 일련의 [!DNL Adobe Photoshop] 작업을 파일 또는 파일 배치에 추가합니다.

   ![Photoshop 작업](/help/assets/assets/content-automation-psactions.png)

* **스마트 오브젝트 교체**: PSD 파일 내에 적용된 모든 효과 및 조정을 유지하면서 이미지를 교체할 수 있도록 함으로써 개인화의 규모를 조절할 수 있습니다.

   ![개체를 지능적으로 바꾸기](/help/assets/assets/content-automation-objectreplace.png)

## AEM as a Cloud Service 프로그램에 Content Automation 사용 {#enable-content-automation}

Cloud Manager를 사용하여 AEM as a Cloud Service 프로그램용 Content Automation 추가 기능을 활성화하려면 다음을 수행하십시오.

1. 콘텐츠 자동화 추가 기능에 라이선스를 부여하려면 계정 담당자에게 문의하십시오.
1. Cloud Manager에 액세스하고 조직 선택기를 사용하여 조직으로 전환합니다.
1. 클릭 **[!UICONTROL 프로그램 추가]** 및 프로그램 이름을 지정합니다.
1. **[!UICONTROL 계속]**&#x200B;을 클릭합니다.
1. 확장 **[!UICONTROL 에셋]** 및 선택 **[!UICONTROL 콘텐츠 자동화]**.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 파이프라인 실행 대상 [cloud Manager에 변경 사항 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

Cloud Manager의 기존 AEM as a Cloud Service 프로그램에 콘텐츠 자동화 추가 기능을 추가해야 하는 경우:

1. 프로그램 카드에서 ...를 클릭합니다.

1. 선택 **[!UICONTROL 프로그램 편집]** 다음을 선택합니다. **[!UICONTROL 솔루션 및 추가 기능]** 탭.

1. 확장 **[!UICONTROL 에셋]** 및 선택 **[!UICONTROL 콘텐츠 자동화]**.
1. **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.
1. 파이프라인 실행 대상 [cloud Manager에 변경 사항 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

## 처리 프로필을 사용하여 크리에이티브 에셋을 일괄적으로 편집 {#process-assets}

처리 프로필을 사용하여 자동으로 변형을 만들려면 다음 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 에셋]** > **[!UICONTROL 처리 프로필]**.

1. 선택 **[!UICONTROL 만들기]**, 및 지정 **[!UICONTROL 이름]**.

1. 다음 항목 선택 **[!UICONTROL Creative]** 탭에서 출력 폴더를 지정하고 다음을 선택합니다 **[!UICONTROL 새로 추가]** 크리에이티브 구성을 추가합니다.

1. 제공 **[!UICONTROL 렌디션 이름]** (또는 출력 이름), **[!UICONTROL 확장]** (또는 파일 유형), 선택 **[!UICONTROL 품질]** (또는 출력 매개 변수), 선택 **[!UICONTROL 포함]** 및 **[!UICONTROL 제외]** MIME 유형 목록(또는 입력 에셋 필터)에서 필요한 크리에이티브 작업을 선택합니다.

   ![[!UICONTROL Creative] 의 탭 [!UICONTROL 처리 프로필]](assets/creative-processing-profile.png)

1. 일부 작업에는 추가 매개 변수(에셋)가 필요합니다. 필요한 경우 이러한 추가 매개 변수의 값을 제공합니다.

1. 동일한 처리 프로필의 일부로 더 많은 크리에이티브 작업을 추가하거나 프로필을 저장합니다.

1. 폴더에 처리 프로필을 적용합니다. 폴더의 **[!UICONTROL 속성]** 페이지, 선택 **[!UICONTROL 자산 처리]**&#x200B;을(를) 클릭하고 적용할 처리 프로필을 선택합니다.

처리 프로필을 DAM 폴더에 적용하면 이 폴더에서 업로드되거나 업데이트된 모든 에셋이 표준 처리와 함께 정의된 작업을 실행합니다. 하위 폴더는 상위 폴더에 적용된 것과 동일한 프로필을 상속합니다. 사용자는 이 상속을 재정의할 수 있습니다.

기존 에셋을 처리하려면 에셋을 선택하고 **[!UICONTROL 재처리]** 필요한 처리 프로필을 선택합니다.

## 팁 및 제한 사항 {#limitations-best-practices}

* [!DNL Experience Manager] 자산 처리를 환경당 분당 300개 요청 및 조직당 분당 700개 요청으로 제한합니다.
* 의 경우 파일 크기는 4GB로 제한됩니다. [!DNL Adobe Photoshop] API 작업 및 1GB [!DNL Adobe Lightroom] 작업.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [에셋이 지원되는 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 에셋](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [처리 프로필을 통해 에셋 마이크로서비스 구성 및 사용](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] 와 통합 [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [자산 마이크로서비스를 통한 자산 수집 및 처리: 개요](/help/assets/asset-microservices-overview.md).

