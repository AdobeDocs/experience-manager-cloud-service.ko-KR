---
title: Cloud Service의 Adobe Experience Manager 에셋의 주목할 만한 변화
description: Adobe Experience Manager 6.5에 비해 AEM Cloud Service의 Adobe Experience Manager 에셋에 대한 주목할 만한 변화.
translation-type: tm+mt
source-git-commit: 2f5925613219a475a4e7d780f7d2bb3da8148e31
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 14%

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Cloud Service으로 자리매김한 Adobe Experience Manager은 AEM 프로젝트를 관리할 수 있는 다양한 새로운 기능과 가능성을 제공합니다. 그러나 Cloud Service에 비해 온-프레미스 또는 Adobe 관리 서비스의 Experience Manager 자산 간에 Experience Manager과 많은 차이점이 있습니다. 이 문서에서는 자산 기능에 대한 중요한 차이점을 설명합니다.

Experience Manager 6.5와 비교할 때 주요 차이점은 다음과 같습니다.

* [자산 수집 및 업로드](#asset-ingestion).
* [클라우드 기본 처리를 위한 에셋 마이크로서비스](#asset-microservices)
* [클래식 UI 제거](#classic-ui).

>[!NOTE]
>
>이 문서에서는 AEM Assets의 주목할 만한 변경 사항을 집중적으로 다룹니다. AEM에 대한 Cloud Service 및 기타 모듈에서의 일반적인 변경 사항은 다음을 참조하십시오.
>
>* [클라우드 서비스로서의 Adobe Experience Manager 소개](/help/overview/introduction.md)
>* [클라우드 서비스로서의 AEM에 대한 개요 - 새로운 기능 및 다른 기능](/help/overview/what-is-new-and-different.md)
>* 클라우드 서비스로서의 Adobe Experience Manager [아키텍처](/help/core-concepts/architecture.md)
>* [클라우드 서비스로서의 AEM에 대한 주목할 만한 변경 사항(릴리스 노트)](/help/release-notes/aem-cloud-changes.md)
>* [ 클라우드 서비스로서의 AEM Sites에 대한 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
>* [클라우드 서비스로서의 Adobe Experience Manager 자습서](https://docs.adobe.com/content/help/ko-KR/experience-manager-learn/cloud-service/overview.html)


## 자산 수집 및 업로드 {#asset-ingestion}

자산 업로드는 자산 수집의 더 나은 비율과 더 빠른 업로드를 가능하게 하여 효율성을 위해 최적화되었습니다. 제품 기능(웹 사용자 인터페이스, 데스크탑 클라이언트)이 업데이트되었습니다. 그러나 기존 사용자 지정 기능에 영향을 줄 수 있습니다.

* Experience Manager은 자산 처리를 위해 업로드 및 다운로드 및 자산 마이크로서비스에 직접 이진 액세스 원칙을 사용합니다. 자산 섭취 [개요를 참조하십시오](/help/assets/asset-microservices-overview.md).
   * 직접 바이너리 액세스 [를 사용하여 에셋 업로드](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * 자세한 내용은 [직접 바이너리 업로드 프로토콜 및 API를 참조하십시오](/help/assets/developer-reference-material-apis.md#upload-binary).
* 이전 AEM 버전의 기본 워크플로우 **[!UICONTROL DAM 자산 업데이트]**&#x200B;는 이제 사용할 수 없습니다. 대신 에셋 마이크로서비스는 대부분의 기본 에셋 처리(변환, 메타데이터 추출, 색인화를 위한 텍스트 추출)를 포괄하는 확장 가능하고 쉽게 사용할 수 있는 서비스를 제공합니다.
   * 에셋 [마이크로서비스 구성 및 사용 참조](/help/assets/asset-microservices-configure-and-use.md)
   * 처리 중에 사용자 정의된 워크플로우 단계를 [사용하려면 사후 처리 워크플로우를](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) 사용할 수 있습니다.
* Assets that come in via Package Manager require manual reprocessing using the **[!UICONTROL Reprocess Asset]** action in the Assets interface.

자산 마이크로서비스로 생성된 표준 변환은 자산 저장소 노드에서 역호환이 가능한 방식으로 저장됩니다(동일한 이름 지정 규칙).

## 에셋 마이크로 서비스 개발 및 테스트 {#asset-microservices}

에셋 마이크로서비스는 클라우드 서비스를 사용하여 자산을 확장 가능하고 탄력적으로 처리할 수 있습니다. Adobe은 다양한 자산 유형 및 처리 옵션을 최적으로 처리하기 위해 클라우드 서비스를 관리합니다. 에셋 마이크로서비스는 ImageMagick과 같은 타사 렌더링 툴과 방법이 필요하지 않고 구성을 단순화하는 동시에 일반적인 파일 유형에 즉시 사용 가능한 기능을 제공합니다. 이전 버전의 Experience Manager에서 [가능한 것보다 더 많은 포맷을 즉시](/help/assets/file-format-support.md) 포함하는 다양한 파일 유형을 처리할 수 있습니다. 예를 들어 이전에는 ImageMagick과 같은 타사 솔루션이 필요했던 PSD 및 PSB 포맷의 축소판 추출을 수행할 수 있습니다. 처리 프로필 구성에 대해 ImageMagick의 복잡한 구성을 사용할 [!UICONTROL 수] 없습니다. 비디오 [!DNL Dynamic Media] 를 FFmpeg 트랜스코딩할 때 사용하고 MP4 비디오의 [기본 트랜스코딩에 처리 프로필을 사용합니다](/help/assets/manage-video-assets.md#transcode-video).

에셋 마이크로서비스는 클라우드 관리자에서 관리되는 고객 프로그램 및 환경에서 자동으로 프로비저닝되고 Experience Manager에 연결된 클라우드 기반의 서비스입니다. 개발자는 Experience Manager을 확장하거나 사용자 정의하기 위해 기존 컨텐츠 또는 에셋을 클라우드 환경에서 생성된 변환과 함께 사용하여 에셋을 테스트 및 표시하고 다운로드하여 코드를 확인할 수 있습니다.

자산 처리 및 처리를 포함한 코드 및 프로세스에 대한 엔드 투 엔드 유효성 검사를 수행하려면 파이프라인을 사용하여 코드 변경 사항을 클라우드 개발 환경 [에 배포하고 전체 에셋](/help/implementing/cloud-manager/configure-pipeline.md) 마이크로서비스 처리를 실행하여 테스트합니다.

## 클래식 UI 제거 {#classic-ui}

Experience Manager에서 클래식 UI를 Cloud Service으로 더 이상 사용할 수 없습니다. 표준 인터페이스는 터치 지원 UI입니다.
