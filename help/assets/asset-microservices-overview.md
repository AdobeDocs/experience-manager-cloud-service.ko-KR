---
title: 자산 마이크로서비스를 사용하여 자산 처리
description: 클라우드 기반의 확장 가능한 자산 처리 마이크로서비스를 사용하여 디지털 자산을 처리합니다.
contentOwner: AG
feature: Asset Compute Microservices,Workflow,Release Information,Asset Processing
role: Architect,Admin
exl-id: 1e069b95-a018-40ec-be01-9a74ed883b77
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 3%

---

# 자산 마이크로서비스를 사용한 자산 수집 및 처리 개요 {#asset-microservices-overview}

Adobe Experience Manager as a [!DNL Cloud Service] Experience Manager 애플리케이션 및 기능을 활용하는 클라우드 기반의 방법을 제공합니다. 이 새로운 아키텍처의 주요 요소 중 하나는 자산 마이크로서비스 기반의 자산 수집 및 처리입니다. 자산 마이크로서비스 는 클라우드 서비스를 사용하여 자산을 확장 가능하고 탄력적인 처리를 제공합니다. Adobe은 다양한 자산 유형 및 처리 옵션을 최적으로 처리하기 위해 클라우드 서비스를 관리합니다. 클라우드 기반의 자산 마이크로서비스의 주요 이점은 다음과 같습니다.

* 리소스 집약적인 작업을 원활하게 처리할 수 있는 확장 가능한 아키텍처
* Experience Manager 환경의 성능에 영향을 주지 않는 효율적인 인덱싱 및 텍스트 추출.
* 워크플로우가 Experience Manager 환경에서 자산 처리를 처리할 필요성을 최소화합니다. 따라서 리소스를 확보하여 Experience Manager 로드를 최소화하고 확장성을 제공합니다.
* 자산 처리 복원 개선. 손상된 파일 또는 매우 큰 파일과 같은 일반 파일을 처리할 때 발생할 수 있는 문제는 더 이상 배포 성능에 영향을 주지 않습니다.
* 관리자를 위한 자산 처리 간소화된 구성
* 자산 처리 설정은 다양한 파일 유형에 대한 표현물, 메타데이터 및 텍스트 추출을 처리하기 위해 가장 잘 알려진 구성을 제공하기 위해 Adobe에서 관리 및 관리합니다
* 기본 Adobe 파일 처리 서비스는 해당하는 경우 사용되며 고품질의 출력을 제공하고 [Adobe 전용 포맷의 효율적인 처리](file-format-support.md).
* 사용자별 작업 및 통합을 추가하도록 사후 처리 워크플로우를 구성하는 기능.

자산 마이크로서비스 는 타사 렌더링 도구 및 메서드(예: [!DNL ImageMagick] 및 FFmpeg 코드 변환)을 단순화하는 동시에 일반적인 파일 형식에 대한 기본 기능을 기본적으로 제공합니다.

## 높은 수준의 아키텍처 {#asset-microservices-architecture}

높은 수준 아키텍처 다이어그램은 시스템 전체의 자산 수집 및 처리 및 흐름의 주요 요소를 나타냅니다.

<!-- Proposed DRAFT diagram for asset microservices overview - see section "Asset processing - high-level diagram" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![자산 마이크로서비스를 사용한 자산 수집 및 처리](assets/asset-microservices-overview.png "자산 마이크로서비스를 사용한 자산 수집 및 처리")

자산 마이크로서비스를 사용하여 수집 및 처리하는 주요 단계는 다음과 같습니다.

* 웹 브라우저나 Adobe Asset Link와 같은 클라이언트는 업로드 요청을 로 보냅니다 [!DNL Experience Manager] 바이너리 클라우드 스토리지에 직접 바이너리를 업로드하기 시작합니다.
* 직접 이진 업로드가 완료되면 클라이언트가 알림을 보냅니다 [!DNL Experience Manager].
* [!DNL Experience Manager] 자산 마이크로서비스에 처리 요청을 보냅니다. 요청 콘텐츠는 의 처리 프로필 구성에 따라 다릅니다 [!DNL Experience Manager] 생성할 변환을 지정합니다.
* 자산 마이크로서비스 백 엔드가 요청을 수신하고, 요청을 기반으로 하나 이상의 마이크로 서비스에 전달합니다. 각 마이크로 서비스는 이진 클라우드 스토어에서 직접 원본 바이너리에 액세스합니다.
* 표현물과 같은 처리 결과는 이진 클라우드 저장소에 저장됩니다.
* Experience Manager은 생성된 바이너리(표현물)에 대한 직접 포인터와 함께 처리가 완료되었다는 알림을 받습니다. 생성된 변환은에서 사용할 수 있습니다. [!DNL Experience Manager] 업로드한 자산에 대해 사용합니다.

자산 수집 및 처리의 기본 흐름입니다. 구성된 경우 Experience Manager이 사용자 지정 워크플로우 모델을 시작하여 자산의 사후 처리를 수행할 수도 있습니다. 예를 들어, 엔터프라이즈 시스템에서 가져오기 정보 및 자산 속성에 추가와 같이 사용자 환경에 맞는 사용자 지정 단계를 실행합니다.

수집 및 처리 흐름은 Experience Manager을 위한 자산 마이크로서비스 아키텍처의 주요 개념입니다.

* **직접 이진 액세스**: Experience Manager 환경에 대해 구성된 자산을 클라우드 이진 저장소로 전송하고 업로드한 다음, [!DNL Experience Manager], 자산 마이크로서비스 및 최종 클라이언트가 직접 액세스하여 작업을 수행할 수 있습니다. 이렇게 하면 네트워크 로드 및 저장된 바이너리 중복을 최소화할 수 있습니다
* **외부 처리**: 자산 처리가 [!DNL Experience Manager] 핵심 DAM(Digital Asset Management) 기능을 제공하고 최종 사용자를 위한 시스템과 대화형 작업을 지원하기 위해 환경 및 은 리소스(CPU, 메모리)를 저장합니다

## 직접적인 바이너리 액세스를 사용하여 자산 업로드 {#asset-upload-with-direct-binary-access}

제품 오퍼링의 일부인 Experience Manager 클라이언트는 기본적으로 모든 지원 업로드에서 직접 바이너리 액세스를 사용할 수 있습니다. 여기에는 웹 인터페이스를 사용한 업로드, Adobe 자산 링크 및 [!DNL Experience Manager] 데스크탑 앱.

에서 직접 작동하는 사용자 지정 업로드 도구를 사용할 수 있습니다 [!DNL Experience Manager] HTTP API. 이러한 API를 직접 사용하거나 업로드 프로토콜을 구현하는 다음 오픈 소스 프로젝트를 사용 및 확장할 수 있습니다.

* [오픈 소스 업로드 라이브러리](https://github.com/adobe/aem-upload)
* [오픈 소스 명령줄 도구](https://github.com/adobe/aio-cli-plugin-aem)

자세한 내용은 [자산 업로드](add-assets.md).

## 사용자 지정 자산 사후 처리 추가 {#add-custom-asset-post-processing}

대부분의 고객은 구성 가능한 자산 마이크로서비스에서 모든 자산 처리 요구 사항을 가져와야 하지만, 일부 고객은 추가 자산 처리가 필요할 수 있습니다. 특히 통합을 통해 다른 시스템에서 오는 정보를 기반으로 자산을 처리해야 하는 경우 이러한 문제가 발생합니다. 이와 같은 경우 사용자 지정 사후 처리 워크플로우를 사용할 수 있습니다.

사후 처리 워크플로우는 일반적입니다 [!DNL Experience Manager] 워크플로우 모델, 작성 및 관리 [!DNL Experience Manager] 워크플로우 편집기. 고객은 사용 가능한 기본 워크플로우 단계 및 사용자 지정 워크플로우 사용을 포함하여 자산에서 추가 처리 단계를 수행하도록 워크플로우를 구성할 수 있습니다.

자산 처리가 완료된 후 사후 처리 워크플로우를 자동으로 트리거하도록 Adobe Experience Manager을 구성할 수 있습니다.

<!-- TBD asgupta, Engg: Create some asset-microservices-data-flow-diagram.
-->

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스 사용 시작](asset-microservices-configure-and-use.md)
>* [지원되는 파일 형식](file-format-support.md)
>* [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)
>* [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [직접 이진 액세스에 대한 Apache Oak 설명서](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html)

