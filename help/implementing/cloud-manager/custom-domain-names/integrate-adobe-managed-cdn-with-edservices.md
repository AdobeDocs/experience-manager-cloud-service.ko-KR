---
title: Cloud Manager의 Adobe Managed CDN과 Edge Delivery Services 통합
description: null
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 71ea3b810d4145d5581c29e26db9bc157c425a15
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 1%

---


# Cloud Manager의 Adobe Managed CDN과 Edge Delivery Services 통합 {#integrate-adbe-cdn-with-edservices-in-cm}

Adobe Managed CDN(AMC-D)은 기본적으로 Edge Delivery Services과 통합되어 Adobe Experience Manager(AEM) 사이트에 대해 전역적으로 분산된 성능 경험을 제공합니다.

이를 함께 사용하면 다음과 같은 이점이 있습니다.

* Adobe에서 관리하는 턴키, 엔터프라이즈급 CDN입니다.
* 요청을 가속화하고 캐싱을 최적화하며 일반적인 공격으로부터 보호하는 최신 에지 전달 계층입니다.
* 도메인 관리, SSL 인증서 및 파이프라인 기반 배포를 위한 통합 Cloud Manager 워크플로입니다.

<!--
Adobe's Edge Delivery Services (EDS) can take advantage of an Adobe managed CDN. EDS is a framework that optimizes website delivery for speed, simplicity, and scalability by pushing content closer to the user through edge nodes. It is not a replacement for a CDN, but rather a way to enhance content delivery, especially when you use the Adobe managed CDN. It offers you the following benefits:

* Adobe-Managed CDN: EDS can use an Adobe-managed CDN, offering features like self-service CDN management and automatic certificate renewal. 
* EDS and AEM: EDS is a feature of AEM as a Cloud Service and works alongside the AEM authoring environment. 
* Performance enhancement: EDS, in conjunction with an Adobe Managed CDN, improves website performance by caching content at edge locations closer to users, reducing latency. 
* Flexibility: EDS provides flexibility in content delivery, allowing your organization to choose between the Adobe-managed CDN or their own CDN setup, based on their needs and existing infrastructure. 
Self-Service CDN Management:
Adobe-managed CDN within EDS enables self-service configuration and management tasks like SSL certificate setup. 
 
Use Cases:
EDS with CDN integration is beneficial for various scenarios, including e-commerce storefronts and websites requiring high performance and scalability. -->

## Cloud Manager의 Adobe Managed CDN의 Edge Delivery Services 배포 옵션 {#deployment-options}

이 항목에서는 Edge Delivery Services을 Cloud Manager의 Adobe Managed CDN에 배포할 수 있는 두 가지 방법에 대해 설명하고, 중요한 것은 사용 사례에 가장 적합한 옵션을 결정하는 데 도움이 됩니다.

Edge Delivery Services은 다음 두 옵션 중 하나를 사용하여 설정할 수 있습니다. 각 기능은 서로 다릅니다.

|  | 배포 옵션 | 키 문서 | 기능 | 적합한 대상 |
| --- | --- | --- | --- | --- |
| 옵션 1 | *기존 AEM as a Cloud Service(AEMaaCS) 환경 사용* | [기존 환경에서 프록시 설정](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment) | 구성 파이프라인은 일반적으로 AEMaaCS 환경에서 사용할 수 있습니다. | Cloud Manager에서 이미 사이트를 실행하고 빠르고 위험도가 낮은 성능 향상을 원하는 팀 |
| 옵션 2 | *독립 실행형 &quot;Edge 환경&quot;으로 알려진 기존 AEMaaCS 환경이 없습니다*. | [기존 환경 없이 Edge Delivery 사이트 설정](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment) | 구성 파이프라인은 현재 제한된 Beta 프로그램을 통해 Edge 환경에만 사용할 수 있습니다.<br>Edge Delivery 구성 파이프라인 추가[를 참조하십시오.](help/implementing/cloud-manager/release-notes/current.md##add-eds-pipeline) | 전체 Edge Delivery 아키텍처 및 세분화된 라우팅을 수용하려는 새로운 빌드 또는 마이그레이션입니다. |

<!-- Ultimately this URL above will need to be updated on GA -->

| 옵션 | 요약 | 적합한 대상 | 주요 문서 |
| --- | --- | --- | --- |
| Adobe Managed CDN 프록시 | Adobe Managed CDN은 기존 AEM Sites 환경에 정면으로 배치됩니다. AMC-D가 에지 캐싱 및 TLS 종료를 처리하는 동안 현재 Sites 파이프라인은 &quot;원본&quot;으로 유지됩니다. | Cloud Manager에서 이미 사이트를 실행하고 빠르고 위험도가 낮은 성능 향상을 원하는 팀 | AMC-D 프록시 설정 |
| originSelectors로 파이프라인 구성 | 전용 Edge Delivery 구성 파이프라인은 정적 및 동적 콘텐츠를 Edge에 직접 게시합니다. AMC-D와 AEM 작성자/게시 계층 간 트래픽을 `originSelectors`합니다. | 전체 Edge Delivery 아키텍처 및 세분화된 라우팅을 수용하려는 새로운 빌드 또는 마이그레이션입니다. | Edge Delivery 파이프라인 구성 |

>[!TIP]
>
>어떤 경로를 선택해야 할지 모르십니까? 결정 지침은 아래의 [배포 모델 선택](#choose-deployment-model)을 참조하십시오.

## 배포 모델 선택 {#choose-deployment-model}

두 모델은 동일한 Cloud Manager 프로그램 내에서 함께 사용할 수 있으므로 단계별 마이그레이션이 가능합니다.

| 다음을 수행하는 경우 | 그런 다음... |
| :--- | :--- |
| 빠르고 최소한의 변경으로 롤아웃해야 하며 이미 Cloud Manager에서 Sites를 호스팅하고 있음 | AMC-D 프록시 |
| Edge Delivery용 콘텐츠를 재구조화하거나 여러 원본 간의 세밀한 라우팅을 원합니다. | Edge Deliver 파이프라인 구성 + `originSelectors` |

## 사전 요구 사항 {#prerequisites}

1. Cloud Manager에서 사이트 온보드 - 두 배포 모델 모두에 필요합니다. AEM 사이트 온보딩을 따르십시오.

2. 나만의 Git(BYOG) 가져오기(선택 사항) - Adobe Git 외부에 사이트 코드를 저장하는 경우 BYOG 온보딩을 완료합니다.

3. Edge Delivery 라이선스 - 프로그램에 Edge Delivery Services 라이선스가 부여되어 있는지 확인합니다.


