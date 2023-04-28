---
title: 의 주요 변경 사항 [!DNL Adobe Experience Manager Assets] 로서의 [!DNL Cloud Service]
description: 에 대한 주요 변경 사항 [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] 로서의 [!DNL Cloud Service] 에 비해 [!DNL Adobe Experience Manager] 6.5.
feature: Release Information
role: User,Leader,Architect,Admin
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 11%

---

# 에 대한 주요 변경 사항 [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 에서는 Experience Manager 프로젝트를 관리할 많은 새로운 기능과 가능성을 제공합니다. 두 사이에는 많은 차이점이 있다 [!DNL Experience Manager Assets] 온-프레미스 또는 Adobe 관리 서비스로 호스팅 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. 이 문서에서는 [!DNL Assets] 기능.

와 비교되는 주요 차이점 [!DNL Experience Manager] 6.5는 다음 영역에 있습니다.

* [자산 수집, 업로드 및 처리](#asset-ingestion).
* [클라우드 기반의 처리를 위한 자산 마이크로서비스](#asset-microservices).
* [클래식 UI 제거](#classic-ui).

## 자산 수집, 처리 및 배포 {#asset-ingestion-distribution}

자산 업로드는 섭취 비율 개선, 업로드 속도 개선, 마이크로서비스를 사용한 처리 속도 향상 및 일괄 처리를 활성화하여 효율성을 제공하도록 최적화되었습니다. 제품 기능(웹 사용자 인터페이스, 데스크탑 클라이언트)이 업데이트됩니다. 또한 이는 일부 기존 사용자 정의에 영향을 줄 수 있습니다.

* [!DNL Experience Manager] 직접 이진 액세스 원칙을 사용하여 자산을 업로드 및 다운로드하고 자산 마이크로서비스를 사용하여 자산을 처리합니다. 자세한 내용은 [마이크로 서비스 개요](/help/assets/asset-microservices-overview.md).
   * 자산 업로드 [직접 이진 액세스](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * 자세한 내용은 [직접 이진 업로드 프로토콜 및 API](/help/assets/developer-reference-material-apis.md#upload-binary).
   * 기본 CRUD 작업을 위해 사용 가능한 API 메서드를 비교하려면 를 참조하십시오 [API 및 자산 작업](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* 이전 버전의 기본 워크플로우 **[!UICONTROL DAM 자산 업데이트]**&#x200B;는 이제 사용할 수 없습니다. [!DNL Experience Manager] 대신 자산 마이크로서비스 는 대부분의 기본 자산 처리(렌디션, 메타데이터 추출 및 색인화를 위한 텍스트 추출)를 다루는 확장 가능하고 손쉽게 사용할 수 있는 서비스를 제공합니다.
   * 자세한 내용은 [asset microservices 구성 및 사용](/help/assets/asset-microservices-configure-and-use.md)
   * 처리에서 사용자 지정된 워크플로우 단계를 수행하려면 다음을 수행합니다. [사후 처리 워크플로우](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) 사용할 수 있습니다.

* 변환하지 않고 이진 파일을 제공하는 웹 사이트 구성 요소는 직접 다운로드를 사용할 수 있습니다. Sling GET 서블릿은 개발자가 기본적으로 이를 수행할 수 있도록 업데이트됩니다. 변환한 바이너리를 전달하는 웹 사이트 구성 요소(예: 서블릿을 통해 크기 조정)는 계속 그대로 수행할 수 있습니다.

자산 마이크로서비스와 함께 생성된 표준 변환은 동일한 이름 지정 규칙을 사용하여 자산 저장소 노드에서 이전 버전과 호환되는 방식으로 저장됩니다.

## 자산 마이크로서비스 개발 및 테스트 {#asset-microservices}

에셋 마이크로서비스는 클라우드 서비스를 사용하여 확장 가능하고 탄력적인 에셋 처리 워크플로를 제공합니다. Adobe는 다양한 에셋 유형 및 옵션을 최적으로 처리할 수 있는 클라우드 서비스를 관리합니다. 자산 마이크로서비스 는 타사 렌더링 도구 및 메서드(예: [!DNL ImageMagick])을 사용하여 구성을 단순화하는 동시에 일반적인 파일 유형에 대한 기본 기능을 제공합니다. 이제 다음을 처리할 수 있습니다 [광범위한 파일 유형](/help/assets/file-format-support.md) 이전 버전의 Experience Manager에서 사용할 수 있는 것보다 더 많은 형식을 기본적으로 제공합니다. 예를 들어 PSD 및 PSB 형식의 축소판 추적은 이전에 필요한 다음과 같은 타사 솔루션을 사용할 수 있습니다 [!DNL ImageMagick]. 의 복잡한 구성은 사용할 수 없습니다 [!DNL ImageMagick] 대상 [!UICONTROL 처리 프로필] 구성. 사용 [!DNL Dynamic Media] 고급 FFmpeg 코드 비디오 코드 변환 및 처리 프로필 사용 [MP4 비디오의 기본 코드 변환](/help/assets/manage-video-assets.md#transcode-video).

자산 마이크로서비스는 자동으로 프로비저닝되고 연결되는 클라우드 기반의 서비스입니다 [!DNL Experience Manager] ( Cloud Manager에서 관리되는 고객 프로그램 및 환경). 확장 또는 사용자 정의하려면 [!DNL Experience Manager], 개발자는 클라우드 환경에서 생성된 표현물과 함께 기존 컨텐츠 또는 자산을 사용하여 자산을 테스트 및 확인하고, 자산을 사용, 표시, 다운로드하여 코드를 확인할 수 있습니다.

자산 수집 및 처리를 포함하여 코드 및 프로세스에 대한 종합적인 유효성 검사를 수행하려면 다음을 사용하여 클라우드 개발 환경에 코드 변경 사항을 배포합니다 [파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 자산 마이크로서비스 처리를 완벽하게 실행하여 테스트합니다.

## 기능 패리티 [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] 로서의 [!DNL Cloud Service] 에서는 기존 기능이 작동하는 많은 새로운 기능과 더 많은 성능 방법을 소개합니다. 그러나 다음 위치에서 이동할 때 [!DNL Experience Manager] 6.5에서 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]로 로그인하면 일부 기능이 다르게 작동하거나, 사용할 수 없거나, 부분적으로 사용할 수 있다는 것을 알 수 있습니다. 다음은 이러한 기능 목록입니다. 또한 다음을 참조하십시오. [더 이상 사용되지 않는 및 제거된 기능](/help/release-notes/deprecated-removed-features.md).

| 기능 또는 사용 사례 | 상태 [!DNL Experience Manager] 로서의 [!DNL Cloud Service] | 댓글 |
|-----|-----|-----|
| [중복된 자산 탐지](/help/assets/manage-digital-assets.md#detect-duplicate-assets) | 다르게 작동합니다. | 자세한 내용은 [작동 방식 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html). |
| [배치만(FPO) 표현물의 경우](/help/assets/configure-fpo-renditions.md) | 다르게 작동합니다. | 처리 프로필은 자산 마이크로서비스를 사용하여 FPO 변환을 생성합니다. Experience Manager 6.5에서는 [!DNL ImageMagick] 은 표현물을 생성하는 데 사용할 수 있습니다. |
| 메타데이터 원본에 쓰기 | 다르게 작동합니다. | 기본적으로 비활성화됨. 필요한 경우 해당 워크플로우 런처를 활성화합니다. 원본에 쓰기 작업은 자산 마이크로서비스에 의해 처리됩니다. |
| 패키지 관리자를 사용하여 업로드한 자산 처리 | 수동 개입 필요 | 를 사용하여 수동으로 재처리 **[!UICONTROL 자산 재처리]** 작업. |
| MIME 유형 탐지 | 지원되지 않음. | 확장 없이 또는 잘못된 확장이 있는 디지털 자산을 업로드하는 경우 원하는 대로 처리되지 않을 수 있습니다. 사용자는 DAM에서 확장 없이 이진 파일을 저장할 수 있습니다. 자세한 내용은 [의 MIME 유형 탐지 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html). |
| 복합 자산에 대한 하위 자산 생성 | 지원되지 않음. | 주석과 같은 종속 사용 사례는 이행되지 않을 수 있습니다. 자세한 내용은 [하위 자산 만들기 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html#generate-subassets). 시작 시 일부 파일 형식의 PDF 미리 보기를 사용할 수 있습니다 [2021.7.0 릴리스](/help/release-notes/release-notes-cloud/release-notes-current.md). |
| 이미지 편집 | 지원되지 않음 | 자산 편집은 Experience Manager as a Cloud Service에서 지원되지 않습니다. 자세한 내용은 [Experience Manager 6.5에서 작동 방식](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#editing-images). |
| 홈 페이지 | 지원되지 않음 | 자세한 내용은 [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html) |
| ZIP 보관소에서 자산 추출 | 지원되지 않음 | 자세한 내용은 [의 ZIP 추출 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#extractzip). |
| 자산 등급 | 지원되지 않음 | 메타데이터 스키마 편집기의 등급 위젯은 지원되지 않습니다. |
| 콘텐츠 처리 필터 | 지원되지 않음 | 의 일반적인 사용 사례 `ContentDispositionFilter` 는 관리자가 구성할 수 있도록 하는 것입니다 [!DNL Experience Manager] HTML 파일을 제공하고 PDF 파일을 다운로드하는 대신 인라인으로 엽니다. 게시 인스턴스에서 Dispatcher 구성을 사용하여 처리를 관리할 수 있습니다. 작성자 인스턴스에서 Adobe은 컨텐츠 처리 헤더를 수정하는 것을 권장하지 않습니다. 자세한 내용은 [의 콘텐츠 처리 필터 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/content-disposition-filter.html). |
| 제품 사진 촬영 템플릿 | 지원되지 않음 | 자세한 내용은 [제품 사진 촬영 템플릿 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/projects/managing-product-information.html). |
| 스마트 번역 | 지원되지 않음 | [스마트 번역](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/translation/smart-translation-search-feature-video-use.html) 에서 지원되지 않음 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. |
| WebDAV | 지원되지 않음 | 대체 요소에 대해서는 [[!DNL Creative Cloud] 통합](/help/assets/aem-cc-integration-best-practices.md) 또는 [개발자 참조 자료](/help/assets/developer-reference-material-apis.md). |
| 클래식 UI | 지원되지 않음 | 터치 사용 사용자 인터페이스만 사용할 수 있습니다. |

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
>다음은에 사용할 수 있습니다 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]:
>
>* [더 이상 사용되지 않는 및 제거된 기능 목록](/help/release-notes/deprecated-removed-features.md)
>* [소개](/help/overview/introduction.md)
>* [새로운 기능 및 차이점](/help/overview/what-is-new-and-different.md)
>* [아키텍처](/help/overview/architecture.md)
>* [주요 변경 내용](/help/release-notes/aem-cloud-changes.md)
>* [주요 변경 내용 [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [비디오 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

