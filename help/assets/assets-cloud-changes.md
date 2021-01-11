---
title: ' [!DNL Adobe Experience Manager Assets] 에  [!DNL Cloud Service]의 주목할 만한 변경 사항'
description: '[!DNL Adobe Experience Manager 6.5와 비교하여  [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] 에 대한 주목할 만한 변경 사항.'
translation-type: tm+mt
source-git-commit: ed449eea146ec18bdc4d25ae4938f9a36180037d
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 3%

---


# [!DNL Experience Manager Assets] [!DNL Cloud Service](으)로 주목할 만한 변경 사항{#notable-changes}

[!DNL Adobe Experience Manager] as a는  [!DNL Cloud Service] Experience Manager 프로젝트를 관리할 수 있는 새로운 기능과 다양한 기능을 제공합니다. [!DNL Experience Manager Assets]과 [!DNL Experience Manager]의 비교할 때 온프레미스 또는 Adobe 관리 서비스로 호스팅되는 데는 많은 차이가 있습니다. [!DNL Cloud Service] 이 문서에서는 [!DNL Assets] 기능에 대한 중요한 차이점을 설명합니다.

[Experience Manager] 6.5와 비교할 때의 주요 차이점은 다음 영역에 있습니다.

* [자산 수집, 업로드 및 처리](#asset-ingestion).
* [클라우드 기본 처리를 위한 에셋 마이크로서비스](#asset-microservices).
* [클래식 UI 제거](#classic-ui).

## 자산 수집 및 처리 {#asset-ingestion}

자산 업로드는 통합 크기 조정, 업로드 시간 단축, 마이크로 서비스를 사용한 처리 시간 단축, 일괄 처리 등의 작업을 효율적으로 수행할 수 있도록 최적화되어 있습니다. 제품 기능(웹 사용자 인터페이스, 데스크탑 클라이언트)이 업데이트됩니다. 또한 기존 사용자 지정 사항에도 영향을 줄 수 있습니다.

* [!DNL Experience Manager] 직접 이진 액세스 원칙을 사용하여 자산을 업로드 및 다운로드하고 자산 마이크로 서비스를 사용하여 자산을 처리합니다. [마이크로서비스 개요](/help/assets/asset-microservices-overview.md)를 참조하십시오.
   * 자산 업로드 [에 직접 이진 액세스](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access)가 있습니다.
   * 자세한 내용은 [직접 이진 업로드 프로토콜 및 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오.
   * 기본 CRUD 작업에 사용할 수 있는 API 메서드를 비교하려면 [API 및 자산 작업](/help/assets/developer-reference-material-apis.md#use-cases-and-apis)을 참조하십시오.
* 이전 버전의 기본 워크플로우 **[!UICONTROL DAM 자산 업데이트]**&#x200B;는 이제 사용할 수 없습니다. [!DNL Experience Manager] 대신 에셋 마이크로서비스는 대부분의 기본 에셋 처리(변환, 메타데이터 추출 및 색인화를 위한 텍스트 추출)를 포괄하는 확장 가능하고 쉽게 사용할 수 있는 서비스를 제공합니다.
   * [자산 마이크로서비스 구성 및 사용](/help/assets/asset-microservices-configure-and-use.md) 참조
   * 처리에서 사용자 지정된 워크플로우 단계를 수행하려면 [사후 처리 워크플로](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용할 수 있습니다.
* 패키지 관리자를 사용하여 업로드한 자산은 [!DNL Assets] 인터페이스에서 **[!UICONTROL 자산 재처리]** 작업을 사용하여 수동 재처리가 필요합니다.
* 확장자가 없거나 확장이 잘못된 디지털 자산은 원하는 대로 처리되지 않습니다. 예를 들어, 이러한 자산을 업로드할 때 아무런 반응이 없거나 잘못된 처리 프로필이 자산에 적용될 수 있습니다. 사용자는 DAM에 이진 파일을 저장할 수 있습니다.

자산 마이크로서비스로 생성된 표준 변환은 자산 저장소 노드(동일한 이름 지정 규칙)에서 역호환이 가능한 방식으로 저장됩니다.

## 에셋 마이크로서비스 개발 및 테스트 {#asset-microservices}

에셋 마이크로서비스는 클라우드 서비스를 사용하여 에셋을 확장 가능하고 탄력적으로 처리할 수 있습니다. Adobe은 다양한 자산 유형 및 처리 옵션을 적절하게 처리하기 위해 클라우드 서비스를 관리합니다. 에셋 마이크로서비스를 사용하면 일반적인 파일 유형에 즉시 사용 가능한 기능을 제공하면서 타사 렌더링 도구와 방법(예: ImageMagick)이 필요하지 않고 구성을 간소화할 수 있습니다. 이제 이전 버전의 Experience Manager에서 가능한 것보다 더 많은 형식을 즉시 포함하는 [다양한 파일 유형](/help/assets/file-format-support.md)을 처리할 수 있습니다. 예를 들어, 이전에는 ImageMagick과 같은 타사 솔루션을 필요로 했던 PSD 및 PSB 포맷의 축소판 추출을 수행할 수 있습니다. [!UICONTROL 처리 프로필] 구성에는 ImageMagick의 복잡한 구성을 사용할 수 없습니다. 비디오를 고급 FFmpeg 트랜스코딩하려면 [!DNL Dynamic Media]을(를) 사용하고 MP4 비디오의 기본 트랜스코딩에는 처리 프로필을 사용합니다](/help/assets/manage-video-assets.md#transcode-video).[

Asset Microservices는 Cloud Manager에서 관리되는 고객 프로그램 및 환경에서 자동으로 프로비저닝되고 Experience Manager에 연결된 클라우드 기본 서비스입니다. Experience Manager을 확장하거나 사용자 정의하기 위해 개발자는 클라우드 환경에서 생성된 표현물과 함께 기존 컨텐츠 또는 에셋을 사용하여 에셋을 테스트 및 확인할 수 있으며 에셋을 사용, 표시, 다운로드를 사용하여 코드를 테스트하고 확인할 수 있습니다.

자산 통합 및 처리를 포함한 코드 및 프로세스에 대한 엔드 투 엔드 유효성 검사를 수행하려면 [파이프라인](/help/implementing/cloud-manager/configure-pipeline.md)을 사용하여 코드 변경 사항을 클라우드 개발 환경에 배포하고 자산 마이크로서비스 처리를 완전히 실행하여 테스트합니다.

## 클래식 UI 제거 {#classic-ui}

클래식 UI는 더 이상 Experience Manager에서 [!DNL Cloud Service]으로 사용할 수 없습니다. 표준 인터페이스는 터치 지원 UI입니다.

>[!MORELIKETHIS]
>
>* [소개 [!DNL Adobe Experience Manager] 는 [!DNL Cloud Service]](/help/overview/introduction.md)
>* [개요 [!DNL Experience Manager] as a [!DNL Cloud Service] - 새로운 기능과 다른 사항](/help/overview/what-is-new-and-different.md)
>* [!DNL Experience Manager]의 [아키텍처](/help/core-concepts/architecture.md)([!DNL Cloud Service])
>* [다음으로  [!DNL Experience Manager] 주목할 만한 변경 사항 [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)
>* [다음으로  [!DNL Experience Manager Sites] 주목할 만한 변경 사항 [!DNL Cloud Service]](/help/sites-cloud/sites-cloud-changes.md)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

