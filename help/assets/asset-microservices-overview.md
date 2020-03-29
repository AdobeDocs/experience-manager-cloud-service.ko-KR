---
title: 디지털 자산을 클라우드에서 처리하는 방법 살펴보기
description: 클라우드 기반의 확장 가능한 자산 처리 마이크로서비스를 사용하여 디지털 자산을 처리할 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 68b2214a4c8941365120bdef670e89b4c9058966

---


# 자산 마이크로서비스를 통한 자산 수집 및 처리 개요 {#asset-microservices-overview}

<!--
First half of content at https://git.corp.adobe.com/aklimets/project-nui/blob/master/docs/Project-Nui-Asset-Compute-Service.md is useful for this article.
TBD: Post-GA we will provide detailed information at \help\assets\asset-microservices-configure-and-use.md. However, for GA, all information is added, in short, in this article.
-->

Adobe Experience Manager as a Cloud Service는 Experience Manager 애플리케이션 및 기능을 이용할 수 있는 클라우드 기반의 방법을 제공합니다. 이 새로운 아키텍처의 주요 요소 중 하나는 자산 통합 및 처리, 자산 마이크로 서비스 힘입니다.

에셋 마이크로서비스는 다양한 에셋 유형 및 처리 옵션을 최적화하기 위해 Adobe에서 관리하는 클라우드 서비스를 사용하여 에셋을 확장 가능하고 탄력적으로 처리할 수 있습니다. 주요 이점은 다음과 같습니다.

* 리소스를 많이 사용하는 작업을 매끄럽게 처리할 수 있는 확장 가능한 아키텍처
* Experience Manager 환경의 성능에 영향을 주지 않는 효율적인 인덱싱 및 텍스트 추출
* 워크플로우가 Experience Manager 환경에서 에셋 처리를 처리할 필요가 최소화됩니다. 따라서 리소스를 절약하고 Experience Manager의 로드를 최소화하며 확장성을 제공합니다.
* 자산 처리 복원성이 개선되었습니다. 손상된 파일 또는 매우 큰 파일과 같은 일반 파일을 처리할 때 발생할 수 있는 문제는 더 이상 배포 성능에 영향을 주지 않습니다.
* 관리자를 위한 자산 처리의 간소화된 구성
* Adobe는 다양한 파일 유형에 대한 변환, 메타데이터 및 텍스트 추출을 처리하기 위해 가장 잘 알려진 구성을 제공하기 위해 자산 처리 설정을 관리 및 관리합니다
* 기본 Adobe 파일 처리 서비스는 해당하는 경우 사용되며 Adobe 독점 포맷의 [효율적인 처리와 고품질의 출력을 제공합니다](file-format-support.md).
* 사용자별 작업 및 통합을 추가하기 위해 사후 처리 워크플로우를 구성할 수 있습니다.

에셋 마이크로 서비스는 ImageMagick과 같은 타사 렌더링 도구가 필요하지 않게 하고 시스템 구성을 단순화하는 동시에 일반적인 파일 유형에 즉시 사용할 수 있는 기능을 제공합니다.

## 고급 아키텍처 {#asset-microservices-architecture}

고급 아키텍처 다이어그램은 시스템 전체의 자산 수집 및 처리 및 흐름의 주요 요소를 나타냅니다.

<!-- Proposed DRAFT diagram for asset microservices overview - see section "Asset processing - high-level diagram" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![자산 마이크로서비스를 통한 자산 수집 및 처리자산](assets/asset-microservices-overview.png "수집 및 처리")

자산 마이크로 서비스를 사용하여 통합 및 처리하는 주요 단계는 다음과 같습니다.

* 웹 브라우저나 Adobe Asset Link와 같은 클라이언트는 Experience Manager에 업로드 요청을 보내고 바이너리를 바이너리 클라우드 스토리지에 직접 업로드하기 시작합니다.
* 직접 이진 업로드가 완료되면 클라이언트는 Experience Manager에 알립니다.
* Adobe Experience Manager에서 자산 마이크로 서비스에 처리 요청을 보냅니다. 요청 내용은 Experience Manager에서 지정해야 하는 변환과 지정하는 처리 프로필 구성에 따라 달라집니다.
* 자산 마이크로서비스 백엔드는 요청을 수신하고 요청을 기반으로 하나 이상의 마이크로 서비스에 전달합니다. 각 마이크로서비스는 이진 클라우드 스토어에서 직접 원본 바이너리에 액세스합니다.
* 표현물과 같은 처리 결과는 바이너리 클라우드 스토리지에 저장됩니다.
* Adobe Experience Manager는 생성된 바이너리(표현물)에 대한 직접 포인터와 함께 처리가 완료되었음을 알리며, 이러한 포인터는 Experience Manager에서 업로드된 자산에 대해 사용할 수 있습니다

자산 수집 및 처리의 기본 흐름입니다. 구성된 경우, Experience Manager는 고객의 워크플로우 모델을 시작하여 자산의 사후 처리를 수행할 수 있습니다. 예를 들어, 고객의 엔터프라이즈 시스템에서 정보를 가져와 자산 속성에 추가하는 등 고객 환경과 관련된 일부 사용자 지정 단계를 실행할 수 있습니다.

통합 및 처리 과정은 Adobe Experience Manager의 자산 마이크로 서비스 아키텍처의 핵심 개념입니다.

* **직접 이진 액세스**:자산은 Experience Manager 환경을 위해 구성되면 클라우드 바이너리 스토어로 전송(및 업로드됨)되고, 그런 다음 AEM, 자산 마이크로 서비스 및 클라이언트는 직접 액세스하여 작업을 수행할 수 있습니다. 이렇게 하면 네트워크 로드와 저장된 바이너리의 복제가 최소화됩니다.
* **외부 처리**:자산 처리는 AEM 환경 외부에서 수행되며, 핵심 디지털 자산 관리 기능을 제공하고 최종 사용자를 위한 시스템에서 대화형 작업을 지원하기 위해 리소스(CPU, 메모리)를 저장합니다

## 직접 이진 액세스를 통해 에셋 업로드 {#asset-upload-with-direct-binary-access}

제품 오퍼링의 일부인 Adobe Experience Manager 클라이언트는 기본적으로 모든 지원 업로드를 직접 바이너리 액세스로 지원합니다. 여기에는 웹 인터페이스, Adobe Asset Link 및 AEM 데스크탑 앱을 사용한 업로드가 포함됩니다.

AEM HTTP API에서 직접 작동하는 사용자 지정 업로드 도구를 사용할 수 있습니다. 이러한 API를 직접 사용하거나 업로드 프로토콜을 구현하는 다음 오픈 소스 프로젝트를 사용 및 확장할 수 있습니다.

* [오픈 소스 업로드 라이브러리](https://github.com/adobe/aem-upload)
* [오픈 소스 명령줄 툴](https://github.com/adobe/aio-cli-plugin-aem)

자세한 내용은 자산 [업로드를](add-assets.md)참조하십시오.

## 사용자 지정 자산 사후 처리 추가 {#add-custom-asset-post-processing}

대부분의 고객은 구성 가능한 자산 마이크로 서비스에서 모든 자산 처리 요구 사항을 충족해야 하지만, 일부 고객은 추가 자산 처리가 필요할 수 있습니다. 이는 특히 통합을 통해 다른 시스템에서 오는 정보를 기반으로 자산을 처리해야 하는 경우에 해당됩니다. 이러한 경우 사용자 지정 사후 처리 워크플로우를 사용할 수 있습니다.

사후 처리 워크플로우는 AEM 워크플로우 편집기에서 작성 및 관리되는 일반적인 AEM 워크플로우 모델입니다. 고객은 즉시 사용 가능한 워크플로우 단계 및 사용자 정의 워크플로우 사용을 포함하여 자산에서 추가 처리 단계를 수행하도록 워크플로우를 구성할 수 있습니다.

Adobe Experience Manager는 자산 처리가 완료된 후 사후 처리 워크플로우를 자동으로 트리거하도록 구성할 수 있습니다.

<!-- TBD asgupta, Engg: Create some asset-microservices-data-flow-diagram.
-->

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스 사용 시작](asset-microservices-configure-and-use.md)
>* [지원되는 파일 형식](file-format-support.md)
>* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [AEM Desktop App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)
>* [직접 바이너리 액세스에 대한 Apache Oak 설명서](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html)

