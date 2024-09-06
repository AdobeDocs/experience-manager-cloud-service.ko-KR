---
title: CI/CD 파이프라인
description: Cloud Manager의 CI/CD 파이프라인과 이를 사용하여 코드를 효율적으로 배포하는 방법에 대해 알아봅니다.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 35%

---


# Cloud Manager CI/CD 파이프라인 {#intro-cicd}

Cloud Manager의 CI/CD(Continuous Integration/Continuous Delivery) 파이프라인 및 이를 사용하여 코드를 효율적으로 배포하는 방법에 대해 알아봅니다.

## 소개 {#introduction}

Cloud Manager의 CI/CD 파이프라인은 소스 저장소에서 코드를 빌드하고 환경에 배포하는 메커니즘입니다. 이벤트는 Git(즉, 코드 변경)과 같은 소스 코드 저장소에서 가져오기 요청과 같은 파이프라인을 트리거합니다. 또는 릴리스 케이던스와 일치하도록 정기적인 일정에 따라 트리거할 수 있습니다.

파이프라인을 구성하려면 다음 작업을 수행해야 합니다.

* 파이프라인을 시작하는 트리거를 정의합니다.
* 프로덕션 배포를 제어하는 매개변수를 정의합니다.
* 성능 테스트 매개변수를 구성합니다.

Cloud Manager는 두 가지 유형의 파이프라인을 제공합니다.

* [프로덕션 파이프라인](#prod-pipeline)
* [비프로덕션 파이프라인](#non-prod-pipeline)

![파이프라인 유형](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## 프로덕션 파이프라인 {#prod-pipeline}

프로덕션 파이프라인은 프로덕션 사용을 위해 소스 코드를 배포하기 위한 일련의 조정된 단계로 구성된 특별히 빌드된 파이프라인입니다. 이 단계에는 모든 스테이징 환경에 대한 첫 번째 빌드, 패키징, 테스트, 검증 및 배포가 포함됩니다. 따라서 프로덕션 파이프라인은 프로덕션 및 스테이징 환경 세트가 생성된 후에만 추가할 수 있습니다.

>[!TIP]
>
>[프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)을 참조하십시오.

## 비프로덕션 파이프라인 {#non-prod-pipeline}

비프로덕션 파이프라인은 주로 코드 품질 검사를 실행하거나 소스 코드를 개발 환경에 배포하는 역할을 합니다.

>[!TIP]
>
>[비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)을 참조하십시오.

## 코드 소스 {#code-sources}

파이프라인은 프로덕션 및 비프로덕션 환경 외에도 배포하는 코드 유형에 따라 다를 수 있습니다.

* **[전체 스택 파이프라인](#full-stack-pipeline)** - HTTPD/Dispatcher 구성과 함께 하나 이상의 AEM 서버 애플리케이션을 포함하는 백엔드 및 프론트엔드 코드 빌드를 동시에 배포합니다.
* **[구성 파이프라인](#config-deployment-pipeline)** - 로그 전달 및 제거 관련 유지 관리 작업과 같은 기능에 대한 구성을 빠르게 배포할 수 있습니다. 또한 트래픽 필터 규칙(웹 애플리케이션 방화벽(WAF) 규칙 등)과 같은 다양한 CDN(Content Delivery Network) 구성이 포함됩니다. 또한 요청 및 응답 변환, 원본 선택기, 클라이언트측 리디렉션, 오류 페이지, CDN 키, 제거 API 키 및 기본 인증을 관리할 수 있습니다. 자세한 내용은 [구성 파이프라인 사용](/help/operations/config-pipeline.md)을 참조하십시오.
* **[프론트엔드 파이프라인](#front-end)** - 하나 이상의 클라이언트측 사용자 인터페이스 응용 프로그램을 포함하는 프론트엔드 코드 빌드를 배포합니다.
* **[웹 계층 구성 파이프라인](#web-tier-config-pipelines)** - HTTPD/Dispatcher 구성을 배포합니다.

이러한 파이프라인 유형에 대해서는 이 문서의 후반부에 자세히 설명되어 있습니다.

### Cloud Manager의 CI-CD 파이프라인 이해 {#understand-pipelines}

다음 표에는 Cloud Manager에서 사용할 수 있는 파이프라인과 그 사용법이 요약되어 있습니다.

| 파이프라인 유형 | 배포 또는 코드 품질 | Source 코드 | 용도 | 메모 |
| --- | --- | --- | --- | ---|
| 프로덕션 또는 비프로덕션 | 배포 | 전체 스택 | HTTPD/Dispatcher 구성과 함께 백엔드 및 프론트엔드 코드 빌드 동시 배포 | 프론트엔드 코드를 AEM 서버 코드와 동시에 배포해야 하는 경우에 사용됩니다. 프론트엔드 파이프라인 또는 웹 계층 구성 파이프라인이 아직 채택되지 않은 경우에 사용됩니다. |
| 프로덕션 또는 비프로덕션 | 배포 | 프론트엔드 | 하나 이상의 클라이언트측 UI 애플리케이션을 포함하는 프론트엔드 코드 빌드 배포 | 여러 개의 동시 프론트엔드 파이프라인을 지원합니다<br>전체 스택 배포보다 훨씬 빠릅니다. |
| 프로덕션 또는 비프로덕션 | 배포 | 웹 계층 구성 | HTTPD/Dispatcher 구성 배포 | 몇 분 만에 배포 |
| 프로덕션 또는 비프로덕션 | 배포 | 구성 | CDN, 로그 전달 및 제거 유지 관리 작업과 관련된 [많은 기능에 대한 구성](/help/operations/config-pipeline.md)을 배포합니다. | 몇 분 만에 배포 |
| 비프로덕션 | 코드 품질 | 전체 스택 | 배포 없이 전체 스택 코드에서 코드 품질 검사 실행 | 여러 파이프라인 지원 |
| 비프로덕션 | 코드 품질 | 프론트엔드 | 배포 없이 프론트엔드 코드에서 코드 품질 검사 실행 | 여러 파이프라인 지원 |
| 비프로덕션 | 코드 품질 | 웹 계층 구성 | 배포 없이 Dispatcher 구성에서 코드 품질 검사 실행 | 여러 파이프라인 지원 |

다음 다이어그램은 기존의 단일 프론트엔드 저장소 또는 독립적인 프론트엔드 저장소 설정을 사용하는 Cloud Manager의 파이프라인 구성을 보여 줍니다.

![Cloud Manager 파이프라인 구성](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## 전체 스택 파이프라인 {#full-stack-pipeline}

전체 스택 파이프라인은 AEM 런타임에 백엔드 코드, 프론트엔드 코드 및 웹 계층 구성을 동시에 배포합니다.

* 백엔드 코드 - 변경 가능한 콘텐츠 외에도 Java 코드, OSGi 구성, repinit와 같이 변경 불가능한 콘텐츠
* 프론트엔드 코드 - JavaScript, CSS, 글꼴과 같은 애플리케이션 UI 리소스
* 웹 계층 구성 - HTTPD/Dispatcher 구성

전체 스택 파이프라인은 &#39;uber&#39; 파이프라인을 나타냅니다. 모든 작업을 동시에 처리하면서도 사용자가 프론트엔드 코드 또는 Dispatcher 구성을 별도로 배포할 수 있도록 합니다. 이 배포는 각각 프론트엔드 파이프라인 및 웹 계층 구성 파이프라인을 통해 수행됩니다.

전체 스택 파이프라인은 프론트엔드 코드(JavaScript/CSS)를 [AEM 클라이언트 라이브러리](/help/implementing/developing/introduction/clientlibs.md)로 패키징합니다.

[웹 계층 구성 파이프라인](#web-tier-config-pipelines)이 구성되지 않은 경우 전체 스택 파이프라인이 웹 계층 구성을 배포할 수 있습니다.

다음 제한 사항이 적용됩니다.

* 파이프라인을 구성하거나 실행하려면 사용자가 **배포 관리자** 역할로 로그인해야 합니다.
* 언제든지 환경당 하나의 전체 스택 파이프라인만 있을 수 있습니다.

또한 [웹 계층 구성 파이프라인](#web-tier-config-pipelines)을 도입하기로 선택한 경우 전체 스택 파이프라인이 작동하는 방식을 알고 있어야 합니다.

* 해당 웹 계층 구성 파이프라인이 있는 경우 환경에 대한 전체 스택 파이프라인은 Dispatcher 구성을 무시합니다.
* 환경에 해당하는 웹 계층 구성 파이프라인이 존재하지 않는 경우 사용자는 전체 스택 파이프라인을 구성하거나 Dispatcher 구성을 무시할 수 있습니다.

전체 스택 파이프라인은 코드 품질 파이프라인 또는 배포일 수 있습니다.

### 전체 스택 파이프라인 구성 {#configure-full-stack}

[프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code)를 참조하십시오.
[비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code)를 참조하십시오.

## 파이프라인 구성 {#config-deployment-pipeline}

구성 파이프라인을 사용하면 로그 전달, 제거 관련 유지 관리 작업 및 트래픽 필터 규칙(예: WAF(Web Application Firewall) 규칙)을 비롯한 다양한 CDN 구성에 대한 설정을 빠르게 배포할 수 있습니다. 또한 요청 및 응답 변환, 원본 선택기, 클라이언트측 리디렉션, 오류 페이지, 고객 관리 CDN 키, 제거 API 키 및 기본 인증을 관리할 수 있습니다.

지원되는 기능의 전체 목록을 보려면 [구성 파이프라인 사용](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)을 참조하고, 올바르게 배포되도록 저장소에서 구성을 관리하는 방법에 대해 알아보십시오.

### 구성 파이프라인 구성 {#configure-config-deployment}

[프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment)를 참조하십시오.
[비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment)를 참조하십시오.

## 프론트엔드 파이프라인 {#front-end}

프론트엔드 코드는 정적 파일로 제공되는 모든 코드입니다. AEM에서 제공하는 UI 코드와 별개이며 사이트 테마, 고객 정의 SPA, SPA 및 기타 솔루션을 포함할 수 있습니다.

프론트엔드 파이프라인은 백엔드 개발과 비동기적으로 프론트엔드 코드 배포를 가속화하여 팀이 설계 및 개발 프로세스를 간소화할 수 있습니다. 이 전용 파이프라인은 JavaScript 및 CSS를 AEM 배포 계층에 테마로 배포하므로 AEM에서 제공하는 페이지에서 참조할 수 있는 새 테마 버전이 생성됩니다.

>[!NOTE]
>
>**배포 관리자** 역할이 있는 사용자는 여러 프론트엔드 파이프라인을 동시에 만들고 실행할 수 있습니다.
>
>단, 프로그램당 최대 300개의 파이프라인으로 제한됩니다(모든 유형에서).

프론트엔드 파이프라인은 코드 품질 파이프라인 또는 배포 파이프라인일 수 있습니다.

### 프론트엔드 파이프라인을 구성하기 전에 {#before-start}

프론트엔드 파이프라인을 구성하기 전에 [AEM 빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)에서 사용하기 쉬운 AEM 빠른 사이트 생성 도구에 대한 전체 안내서를 검토하십시오. 이 여정을 사용하면 프론트엔드 개발을 간소화할 수 있고, 백엔드 AEM 지식 없이 사이트를 빠르게 사용자 정의할 수 있습니다.

### 프론트엔드 파이프라인 구성 {#configure-front-end}

[프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)를 참조하십시오.
[비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)를 참조하십시오.

### 프론트엔드 파이프라인으로 Sites 개발 {#developing-with-front-end-pipeline}

프론트엔드 파이프라인을 사용하면 프론트엔드 개발자에게 더 많은 독립성을 부여하고 개발 프로세스를 가속화할 수 있습니다.

이 프로세스의 잠재력을 최대한 활용하기 위해 알아야 할 몇 가지 고려 사항과 함께 이 프로세스가 작동하는 방식에 대한 자세한 내용은 [프론트엔드 파이프라인으로 사이트 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)을 참조하십시오.

## 웹 계층 구성 파이프라인 {#web-tier-config-pipelines}

웹 계층 구성 파이프라인을 사용하면 HTTPD/Dispatcher 구성을 AEM 런타임에 독점적으로 배포하여 다른 코드 변경과 분리할 수 있습니다. Dispatcher 구성 변경 사항만 배포하려는 사용자에게 단 몇 분 만에 신속하게 배포할 수 있는 가속화된 파이프라인입니다.

>[!TIP]
>
>웹 계층 구성 파이프라인을 사용하면 프로젝트 구조에 가장 적합한 것에 따라 웹 구성을 전체 스택 파이프라인과 동일하거나 다른 소스 위치에 저장할 수 있습니다.

다음 제한 사항이 적용됩니다.

* 웹 계층 구성 파이프라인을 사용하려면 AEM 버전 `2021.12.6151.20211217T120950Z` 이상을 사용해야 합니다.
* [유연한 Dispatcher 도구 모드를 옵트인](/help/implementing/dispatcher/disp-overview.md#validation-debug)하여 웹 계층 구성 파이프라인을 사용합니다.
* 파이프라인을 구성하거나 실행하려면 사용자가 **배포 관리자** 역할로 로그인해야 합니다.
* 언제든지 환경당 하나의 웹 계층 구성 파이프라인만 있을 수 있습니다.
* 해당 전체 스택 파이프라인이 실행 중일 때 사용자는 웹 계층 구성 파이프라인을 구성할 수 없습니다.
* 웹 계층 구조는 [클라우드의 Dispatcher](/help/implementing/dispatcher/disp-overview.md#validation-debug) 문서에 정의된 대로 유연한 모드 구조를 준수해야 합니다.

또한 웹 계층 파이프라인을 도입할 때 [전체 스택 파이프라인](#full-stack-pipeline)이 어떻게 작동하는지 알고 있어야 합니다.

* 웹 계층 구성 파이프라인이 환경에 대해 설정되지 않은 경우 사용자는 전체 스택 파이프라인을 구성하는 동안 Dispatcher 구성을 포함하거나 무시하도록 선택할 수 있습니다. 이 선택은 실행 및 배포 중에 수행됩니다.
* 웹 계층 구성 파이프라인이 환경에 대해 구성되면 해당 전체 스택 파이프라인(있는 경우)은 실행 및 배포 중에 Dispatcher 구성을 무시합니다.
* 웹 계층 구성 파이프라인이 삭제된 후에 해당 전체 스택 파이프라인이 실행 중에 Dispatcher 구성을 배포하도록 재설정됩니다.

웹 계층 구성 파이프라인은 `Code quality` 또는 `Deployment` 형식일 수 있습니다.

### 웹 계층 파이프라인 구성 {#configure-web-tier}

[프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment)를 참조하십시오.
[비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment)를 참조하십시오.

## 파이프라인 유형에 대한 비디오 개요 {#video}

파이프라인 유형에 대한 빠른 개요는 다음 비디오 (2분 26초)를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/342363)
