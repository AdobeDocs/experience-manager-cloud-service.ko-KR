---
title: 클라우드 서비스로서의 Adobe Experience Manager Assets의 주목할 만한 변경 사항
description: Adobe Experience Manager 6.5와 비교하여 AEM Cloud Service의 Adobe Experience Manager 자산에 대한 주목할 만한 변경 사항.
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

클라우드 서비스로서 Adobe Experience Manager는 AEM 프로젝트를 관리할 수 있는 새로운 기능과 다양한 기능을 제공합니다. 그러나 Adobe Experience Manager Assets 온프레미스 또는 Adobe Managed Service는 Adobe Experience Manager와 클라우드 서비스 간 차이점이 많습니다. 이 문서에서는 중요한 차이점을 조명합니다.

>[!NOTE]
>
>이 문서에서는 Experience Manager Assets as a Cloud Service와 관련된 주목할 만한 변경 사항을 소개합니다. 클라우드 서비스로 Experience Manager의 일반적인 [변경 사항을 참조하십시오](/help/release-notes/aem-cloud-changes.md).

Adobe Experience Manager 6.5와 비교할 때 주요 차이점은 다음과 같습니다.

* [자산 통합](#asset-ingestion)
* [클래식 UI 제거](#classic-ui)

## 자산 통합 {#asset-ingestion}

자산 업로드는 자산 수집의 크기를 더 잘 조정하고 업로드 속도를 높여 효율성을 위해 최적화되었습니다. 제품 기능(웹 유저 인터페이스, 데스크탑 클라이언트)이 업데이트되었습니다. 그러나 이는 일부 기존 사용자 지정에 영향을 줄 수 있습니다.

* Adobe Experience Manager는 업로드 및 다운로드에 대한 직접적인 바이너리 액세스 원칙을 사용하고 자산 처리를 위한 에셋 마이크로 서비스를 사용합니다. 자산 [문제 개요를 참조하십시오](/help/assets/asset-microservices-overview.md).
   * 직접 이진 액세스를 [통해](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access)에셋 업로드
   * 자세한 내용은 [직접 바이너리 업로드 프로토콜 및 API를 참조하십시오](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* 이전 AEM 버전의 기본 워크플로우 **[!UICONTROL DAM 자산 업데이트]**&#x200B;는 이제 사용할 수 없습니다. 대신 에셋 마이크로서비스는 대부분의 기본 에셋 처리(변환, 메타데이터 추출, 색인화를 위한 텍스트 추출)를 포괄하는 확장 가능하고 쉽게 사용할 수 있는 서비스를 제공합니다.
   * 자산 마이크로서비스 [구성 및 사용 참조](/help/assets/asset-microservices-configure-and-use.md)
   * 처리 중에 사용자 지정된 워크플로우 단계를 위해 [사후 처리 워크플로우를](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) 사용할 수 있습니다.
* Assets that come in via Package Manager require manual reprocessing using the **[!UICONTROL Reprocess Asset]** action in the Assets interface.

자산 마이크로서비스로 생성된 표준 변환은 자산 저장소 노드에서 역호환이 가능한 방식으로 저장됩니다(동일한 이름 지정 규칙).

## 에셋 마이크로 서비스 개발 및 테스트 {#developing-testing-asset-microservices}

Asset Microservices는 Cloud Manager에서 관리하는 고객 프로그램 및 환경에서 Experience Manager에 자동으로 프로비저닝되고 연결된 기본 클라우드 서비스입니다. Experience Manager를 확장하거나 사용자 지정을 수행하는 개발자는 기존 컨텐츠(또는 클라우드 환경에서 생성된 표현물이 있는 자산)를 사용하여 자산을 사용, 표시, 다운로드를 사용하여 코드를 테스트하고 확인할 수 있습니다.

자산 처리 및 처리를 포함한 코드 및 프로세스에 대한 전체 유효성 검사를 수행하려면 파이프라인을 사용하여 코드 변경 사항을 클라우드 개발 환경에 배포하고 자산 마이크로 서비스 처리를 전체 실행으로 테스트합니다.

## 클래식 UI 제거 {#classic-ui}

Experience Manager에서 클라우드 서비스로 클래식 UI를 더 이상 사용할 수 없습니다.
