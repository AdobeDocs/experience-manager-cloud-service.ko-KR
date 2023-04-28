---
title: Creative Cloud 통합을 위한 컨텐츠 자동화
description: Creative Cloud 통합을 사용하여 자산의 변형 생성
contentOwner: AG
feature: Upload,Asset Processing,Publishing,Asset Compute Microservices,Workflow
role: User,Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 3%

---

# 을 사용하여 자산의 변형 생성 [!DNL Adobe Creative Cloud] 통합 {#content-automation}

컨텐츠 자동화 추가 기능 통합 [!DNL Adobe Experience Manager Assets] 로서의 [!DNL Cloud Service] 및 [!DNL Adobe Creative Cloud] 자산을 규모에 맞게 창의적으로 처리할 수 있는 API입니다. [!DNL Experience Manager] 클라우드 기반 사용 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md) 를 사용하려면 [!DNL Adobe Creative Cloud] 자산 작성 및 미디어 처리를 자동화하고 기능을 사용할 수 있습니다.

에서 자산을 편집하려면 [!DNL Adobe Photoshop] 및 [!DNL Adobe Lightroom]에서 자산을 다운로드할 필요는 없습니다. [!DNL Experience Manager Assets]를 편집하고 다시 업로드합니다. 에서 처리 프로필을 만들고 구성합니다 [!DNL Experience Manager]를 눌러 폴더에 프로필을 적용하고 폴더에 자산을 업로드합니다. 업로드된 자산은 처리 프로필을 기반으로 다시 처리되며, 이러한 자산의 변형을 받습니다. 일관되고 간편하게 일괄 처리를 수행할 수 있으므로 수작업을 줄일 수 있고 컨텐츠 속도를 높일 수 있으므로 탁월한 크리에이티브 기술이 필요하지 않습니다. 또한 개발자와 파트너는 이러한 API에 직접 액세스하여 자산 마이크로서비스를 확장하고 사용자 지정 논리를 포함할 수 있습니다.

사용자는 처리 프로필을 만들어 자산에서 다음과 같은 크리에이티브 작업을 자동화할 수 있습니다.

* **자동 톤**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 고유한 속성에 따라 지능적으로 빛과 색상을 수정합니다.

* **자동 직립**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 기울어진 원근감을 수정합니다. 예를 들어 수준 범위를 만듭니다.

   ![자동 톤](/help/assets/assets/content-automation-autotone.png)

   *그림: 자동 톤 및 자동 맞춤은 기울어진 이미지를 개선하는 데 도움이 됩니다.*

* **Lightroom 사전 설정**: 사용자 정의 사전 설정을 사용하여 이미지에 사용자 정의 모양을 적용하여 일관된 모양을 얻을 수 있습니다.

   ![Lightroom 사전 설정](/help/assets/assets/content-automation-lrpresets.png)

   *그림: Adobe Lightroom 사전 설정은 많은 이미지에 일관된 방식으로 이미지 품질을 개선합니다.*

* **이미지 컷아웃**: 인공 지능을 사용하여 돌출된 객체 주위에 선택 영역을 만들고 단일 명령으로 배경을 제거합니다.

   ![배경 제거 및 사진 이미지 잘라내기](/help/assets/assets/content-automation-backgroundremove.png)

* **이미지 마스크**: 인공 지능을 사용하여 하나의 명령으로 침목 객체 주위에 마스크를 만듭니다.

   ![AI를 사용하여 이미지 마스크](/help/assets/assets/content-automation-mask.png)

* **Photoshop 작업**: 일련의 [!DNL Adobe Photoshop] 파일 또는 파일 배치에 작업

   ![Photoshop 작업](/help/assets/assets/content-automation-psactions.png)

* **스마트 개체 바꾸기**: PSD 파일 내에 적용된 모든 효과 및 조정을 그대로 유지하면서 이미지를 교환하도록 하여 규모에 맞게 개인화를 수행합니까?

   ![개체를 깔끔하게 바꾸기](/help/assets/assets/content-automation-objectreplace.png)

## AEM as a Cloud Service 프로그램에 컨텐츠 자동화 사용 {#enable-content-automation}

Cloud Manager를 사용하여 AEM as a Cloud Service 프로그램에 대한 컨텐츠 자동화 추가 기능을 활성화하려면

1. Content Automation 추가 기능의 라이센스를 얻으려면 계정 담당자에게 문의하십시오.
1. Cloud Manager에 액세스하고 조직 선택기를 사용하여 조직으로 전환합니다.
1. 클릭 **[!UICONTROL 프로그램 추가]** 그리고 프로그램 이름을 지정합니다.
1. **[!UICONTROL 계속]**&#x200B;을 클릭합니다.
1. 확장 **[!UICONTROL 자산]** 을(를) 선택합니다. **[!UICONTROL 컨텐츠 자동화]**.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 다음 대상 파이프라인 실행 [cloud Manager에 변경 사항 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

Cloud Manager의 기존 AEM as a Cloud Service 프로그램에 컨텐츠 자동화 추가 기능을 추가해야 하는 경우:

1. 프로그램 카드에서 ...을 클릭합니다.

1. 선택 **[!UICONTROL 프로그램 편집]** 그런 다음 **[!UICONTROL 솔루션 및 추가 기능]** 탭.

1. 확장 **[!UICONTROL 자산]** 을(를) 선택합니다. **[!UICONTROL 컨텐츠 자동화]**.
1. **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.
1. 다음 대상 파이프라인 실행 [cloud Manager에 변경 사항 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

## 처리 프로필을 사용하여 크리에이티브 자산을 일괄적으로 편집 {#process-assets}

처리 프로필을 사용하여 변형을 자동으로 만들려면 다음 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**.

1. 선택 **[!UICONTROL 만들기]**, 및에 대해 **[!UICONTROL 이름]**.

1. 을(를) 선택합니다 **[!UICONTROL Creative]** 탭에서 출력 폴더를 지정하고 **[!UICONTROL 새로 추가]** 크리에이티브 구성을 추가합니다.

1. 제공 **[!UICONTROL 표현물 이름]** (또는 출력 이름), **[!UICONTROL 확장]** (또는 파일 형식)를 선택하거나 **[!UICONTROL 품질]** (또는 출력 매개 변수)를 선택하거나 **[!UICONTROL 포함]** 및 **[!UICONTROL 제외]** MIME 유형 목록(또는 입력 자산 필터)을 설정하고 필요한 광고 작업을 선택합니다.

   ![[!UICONTROL Creative] 탭 [!UICONTROL 처리 프로필]](assets/creative-processing-profile.png)

1. 일부 작업에는 추가 매개 변수(자산)가 필요합니다. 필요한 경우 이러한 추가 매개 변수에 대한 값을 제공합니다.

1. 동일한 처리 프로필의 일부로 크리에이티브 작업을 더 추가하거나 프로필을 저장합니다.

1. 처리 프로필을 폴더에 적용합니다. 폴더 **[!UICONTROL 속성]** 페이지를 선택하고 **[!UICONTROL 자산 처리]**&#x200B;을 선택하고 적용할 처리 프로필을 선택합니다.

처리 프로필을 DAM 폴더에 적용하면 이 폴더에서 업로드하거나 업데이트된 모든 자산이 표준 처리 외에도 정의된 작업을 실행합니다. 하위 폴더는 상위 폴더에 적용된 프로필과 동일한 프로필을 상속합니다. 사용자는 이 상속을 무시할 수 있습니다.

기존 자산을 처리하려면 자산을 선택하고 을(를) 선택합니다 **[!UICONTROL 재처리]** 옵션을 선택한 다음 필수 처리 프로필을 선택합니다.

## 팁 및 제한 사항 {#limitations-best-practices}

* [!DNL Experience Manager] 자산 처리를 환경당 분당 300개의 요청 및 조직당 분당 700개의 요청으로 제한합니다.
* 파일 크기는 4GB로 제한됩니다 [!DNL Adobe Photoshop] API 작업 및 1GB의 경우 [!DNL Adobe Lightroom] 작업.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [처리 프로필을 통해 자산 마이크로서비스 구성 및 사용](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] 와 통합 [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [자산 마이크로서비스를 사용한 자산 수집 및 처리: 개요](/help/assets/asset-microservices-overview.md).

