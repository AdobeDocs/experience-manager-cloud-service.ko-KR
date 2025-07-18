---
title: ' [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service]의 주요 변경 내용'
description: ' [!DNL Adobe Experience Manager] 6.5와 비교하여  [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] 에 대한 주목할 만한 변경 사항입니다.'
feature: Release Information
role: User, Leader, Architect, Admin
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 9%

---

# [!DNL Experience Manager Assets]을(를) [!DNL Cloud Service]&#x200B;(으)로 주요 변경 내용 {#notable-changes}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]은(는) Experience Manager 프로젝트를 관리할 수 있는 많은 새로운 기능과 가능성을 제공합니다. [!DNL Experience Manager Assets] 온-프레미스 또는 Adobe Managed Service로 호스팅 간에 [!DNL Experience Manager] as a [!DNL Cloud Service]와(과) 많은 차이가 있습니다. 이 문서에서는 [!DNL Assets] 기능의 중요한 차이점을 조명합니다.

[!DNL Experience Manager] 6.5와 비교한 주요 차이점은 다음 영역에 있습니다.

* [자산 수집, 업로드 및 처리](#asset-ingestion).
* [클라우드 네이티브 처리를 위한 자산 마이크로서비스](#asset-microservices).
* [클래식 UI 제거](#classic-ui).

## 자산 수집, 처리 및 배포 {#asset-ingestion-distribution}

에셋 업로드는 수집의 확장, 업로드 속도 향상, 마이크로 서비스를 사용한 빠른 처리 및 대량 수집을 통해 효율성에 최적화됩니다. 제품 기능(웹 사용자 인터페이스, 데스크탑 클라이언트)이 업데이트됩니다. 또한 이러한 사항은 일부 기존 사용자 지정에 영향을 줄 수 있습니다.

* [!DNL Experience Manager]은(는) 직접 이진 액세스 원칙을 사용하여 자산을 업로드 및 다운로드하고 자산 마이크로서비스를 사용하여 자산을 처리합니다. [마이크로서비스 개요](/help/assets/asset-microservices-overview.md)를 참조하세요.
   * 직접 이진 액세스[&#128279;](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access)를 사용하여 에셋을 업로드합니다.
   * 자세한 내용은 [다이렉트 이진 업로드 프로토콜 및 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오.
   * 기본 CRUD 작업에 사용 가능한 API 메서드를 비교하려면 [API 및 에셋 작업](/help/assets/developer-reference-material-apis.md#use-cases-and-apis)을 참조하십시오.
* 이전 버전의 [!DNL Experience Manager]에서 기본 워크플로우 **[!UICONTROL DAM 자산 업데이트]**&#x200B;를 더 이상 사용할 수 없습니다. 대신 에셋 마이크로서비스 는 대부분의 기본 에셋 처리(렌디션, 메타데이터 추출 및 색인을 위한 텍스트 추출)를 포함하는 확장 가능하고 사용 가능한 서비스를 제공합니다.
   * [자산 마이크로서비스 구성 및 사용](/help/assets/asset-microservices-configure-and-use.md)을 참조하세요.
   * 처리에서 워크플로 단계를 사용자 지정하려면 [사후 처리 워크플로](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용할 수 있습니다.

* 변환 없이 이진 파일을 제공하는 웹 사이트 구성 요소는 직접 다운로드를 사용할 수 있습니다. Sling GET 서블릿은 기본적으로 이 기능을 활성화하도록 업데이트됩니다. 일부 변환한 바이너리를 전달하는 웹 사이트 구성 요소(예: 서블릿을 통해 크기 조정)는 그대로 계속 작동할 수 있습니다.

에셋 마이크로서비스와 함께 생성된 표준 렌디션은 동일한 이름 지정 규칙을 사용하여 에셋 저장소 노드에 이전 버전과 호환되는 방식으로 저장됩니다.

## 에셋 마이크로서비스 개발 및 테스트 {#asset-microservices}

자산 마이크로서비스는 클라우드 서비스를 사용하여 확장 가능하고 탄력적인 자산 처리 워크플로를 제공합니다. Adobe는 다양한 자산 유형 및 옵션을 최적으로 처리할 수 있는 클라우드 서비스를 관리합니다. 에셋 마이크로서비스 를 사용하면 [!DNL ImageMagick]과(와) 같은 타사 렌더링 도구 및 메서드가 필요하지 않고 구성을 단순화하는 동시에 일반적인 파일 형식에 즉시 사용 가능한 기능을 제공할 수 있습니다. 이제 이전 버전의 Experience Manager에서 가능한 것보다 더 많은 형식을 즉시 다루는 [광범위한 파일 형식](/help/assets/file-format-support.md)을 처리할 수 있습니다. 예를 들어 이전에 [!DNL ImageMagick]과 같은 타사 솔루션이 필요했던 PSD 및 PSB 형식의 썸네일 추출이 가능합니다. [!UICONTROL 처리 프로필] 구성에 [!DNL ImageMagick]의 복잡한 구성을 사용할 수 없습니다. 비디오의 고급 FFmpeg 코드 변환에는 [!DNL Dynamic Media]을(를) 사용하고 [MP4 비디오의 기본 코드 변환](/help/assets/manage-video-assets.md#transcode-video)에는 처리 프로필을 사용합니다.

에셋 마이크로서비스 는 Cloud Manager에서 관리되는 고객 프로그램 및 환경에서 자동으로 프로비저닝되고 [!DNL Experience Manager]에 연결되는 클라우드 네이티브 서비스입니다. [!DNL Experience Manager]을(를) 확장하거나 사용자 지정하기 위해 개발자는 클라우드 환경에서 생성된 변환과 함께 기존 콘텐츠 또는 에셋을 사용할 수 있습니다. 이 기능을 사용하면 에셋을 사용, 표시 또는 다운로드하여 코드를 테스트하고 확인할 수 있습니다.

자산 수집 및 처리를 포함하여 코드 및 프로세스에 대한 전체적인 유효성 검사를 수행하려면 [파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 사용하여 클라우드 개발 환경에 코드 변경 사항을 배포하고 자산 마이크로서비스 처리를 완전히 실행하여 테스트하십시오.

## 기능 패리티가 [!DNL Experience Manager] 6.5임 {#cloud-service-feature-status}

[!DNL Experience Manager] as a [!DNL Cloud Service]은(는) 많은 새로운 기능을 도입했으며 기존 기능을 보다 효율적으로 사용할 수 있는 방법을 도입했습니다. 그러나 [!DNL Cloud Service]&#x200B;(으)로 [!DNL Experience Manager] 6.5에서 [!DNL Experience Manager]&#x200B;(으)로 이동할 때 일부 기능은 다르게 작동하거나, 사용할 수 없거나, 부분적으로 사용할 수 있습니다. 다음은 이러한 기능 목록입니다. 또한 [사용되지 않거나 제거된 기능](/help/release-notes/deprecated-removed-features.md)을 참조하세요.

| 기능 또는 사용 사례 | [!DNL Cloud Service]&#x200B;(으)로 [!DNL Experience Manager]의 상태 | 댓글 |
|-----|-----|-----|
| [자산 검색 복제](/help/assets/detect-duplicate-assets.md) | 다르게 작동합니다. | [작동 방식 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/managing/duplicate-detection)을 참조하세요. |
| [FPO(배치 전용) 표현물의 경우](/help/assets/configure-fpo-renditions.md) | 다르게 작동합니다. | 처리 프로필은 에셋 마이크로서비스 를 사용하여 FPO 렌디션을 생성합니다. Experience Manager 6.5에서는 [!DNL ImageMagick]과(와) 같은 서드파티 솔루션을 사용하여 렌디션을 생성할 수 있습니다. |
| 메타데이터 원본에 쓰기 | 다르게 작동합니다. | 기본적으로 비활성화되어 있습니다. 필요한 경우 해당 워크플로우 런처를 활성화합니다. 에셋 마이크로서비스 는 원본에 쓰기(writeback)를 처리합니다. |
| 패키지 관리자를 사용하여 업로드된 자산 처리 | 이 작업에는 수동 개입이 필요합니다 | **[!UICONTROL 자산 재처리]** 작업을 사용하여 수동으로 재처리합니다. |
| MIME 유형 감지 | 지원되지 않습니다. | 확장이 없거나 잘못된 디지털 에셋을 업로드하는 경우 원하는 대로 처리되지 않을 수 있습니다. 사용자는 DAM에 확장명 없이 이진 파일을 저장할 수 있습니다.  [!DNL Experience Manager] 6.5[&#128279;](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/administer/detect-asset-mime-type-with-tika)에서 MIME 형식 검색을 참조하십시오. |
| 조합 자산에 대한 하위 자산 생성 | 지원되지 않습니다. | 주석과 같은 종속 사용 사례가 이행되지 않을 수 있습니다. [하위 자산 만들기 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/managing/managing-linked-subassets#generate-subassets)를 참조하세요. 일부 파일 형식의 PDF 미리 보기는 [2021.7.0 릴리스](/help/release-notes/release-notes-cloud/release-notes-current.md)부터 사용할 수 있습니다. |
| 이미지 편집 | 지원되지 않음 | Experience Manager as a Cloud Service에서는 에셋 편집이 지원되지 않습니다. [Experience Manager에서 작동 방식 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/managing/manage-assets#editing-images)을 참조하세요. |
| 홈 페이지 | 지원되지 않음 | [[!DNL Assets] 홈 페이지 환경 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/using/assets-home-page) 보기 |
| ZIP 아카이브에서 자산 추출 | 지원되지 않음 | [ZIP 추출( [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/managing/manage-assets#extractzip))을 참조하세요. |
| Assets 등급 | 지원되지 않음 | 메타데이터 스키마 편집기의 등급 위젯은 지원되지 않습니다. |
| 콘텐츠 처리 필터 | 지원되지 않음 | `ContentDispositionFilter`의 일반적인 사용 사례는 관리자가 HTML 파일을 제공하고 다운로드하지 않고 인라인으로 PDF 파일을 열도록 [!DNL Experience Manager]을(를) 구성할 수 있도록 하는 것입니다. 게시 인스턴스에서는 Dispatcher 구성을 사용하여 처리를 관리할 수 있습니다. 작성 인스턴스에서는 Adobe이 컨텐츠 처리 헤더를 수정하는 것을 권장하지 않습니다. [콘텐츠 처리 필터 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/security/content-disposition-filter)를 참조하세요. |
| 제품 사진 촬영 템플릿 | 지원되지 않음 | [제품 사진 촬영 템플릿 [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/sites/authoring/projects/managing-product-information)을 참조하세요. |
| 고급 번역 | 지원되지 않음 | [!DNL Experience Manager]에서 [!DNL Cloud Service]&#x200B;(으)로 스마트 변환이 지원되지 않습니다. |
| WebDAV | 지원되지 않음 | 다른 방법은 [[!DNL Creative Cloud] 통합](/help/assets/aem-cc-integration-best-practices.md) 또는 [개발자 참조 자료](/help/assets/developer-reference-material-apis.md)를 참조하세요. |
| 클래식 UI | 지원되지 않음 | 터치 지원 사용자 인터페이스만 사용할 수 있습니다. |

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
>[!DNL Experience Manager]에 [!DNL Cloud Service]&#x200B;(으)로 다음 리소스를 사용할 수 있습니다.
>
>* [사용되지 않거나 제거된 기능 목록](/help/release-notes/deprecated-removed-features.md)
>* [소개](/help/overview/introduction.md)
>* [새로운 기능 및 차이점](/help/overview/what-is-new-and-different.md)
>* [아키텍처](/help/overview/architecture.md)
>* [주요 변경 내용](/help/release-notes/aem-cloud-changes.md)
>* [주요 변경 내용 [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [비디오 자습서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/overview)
