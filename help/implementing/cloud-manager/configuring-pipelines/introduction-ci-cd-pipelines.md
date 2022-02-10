---
title: CI/CD 파이프라인
description: Cloud Manager의 CI/CD 파이프라인과 이 파이프라인을 사용하여 코드를 효율적으로 배포하는 방법에 대해 알아봅니다.
index: true
source-git-commit: d1fe713f0c35a96cf6ba3172ea11986fd9d42fd6
workflow-type: tm+mt
source-wordcount: '1364'
ht-degree: 1%

---


# Cloud Manager CI/CD 파이프라인 {#intro-cicd}

Cloud Manager의 CI/CD 파이프라인과 이 파이프라인을 사용하여 코드를 효율적으로 배포하는 방법에 대해 알아봅니다.

## 소개 {#introduction}

Cloud Manager의 CI/CD 파이프라인은 소스 저장소에서 코드를 작성하고 환경에 배포하는 메커니즘입니다. 파이프라인은 소스 코드 리포지토리의 끌어오기 요청(즉, 코드 변경)과 같은 이벤트 또는 릴리스 케이던스와 일치시키기 위한 정규 일정에 의해 트리거될 수 있습니다.

파이프라인을 구성하려면 다음을 수행해야 합니다.

* 파이프라인을 시작할 트리거를 정의합니다.
* 프로덕션 배포를 제어하는 매개 변수를 정의합니다.
* 성능 테스트 매개 변수를 구성합니다.

Cloud Manager는 두 가지 유형의 파이프라인을 제공합니다.

* [프로덕션 파이프라인](#prod-pipeline)
* [비프로덕션 파이프라인](#non-prod-pipeline)

![파이프라인 유형](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## 프로덕션 파이프라인 {#prod-pipeline}

프로덕션 파이프라인은 프로덕션 사용을 위해 소스 코드를 배포하기 위해 일련의 오케스트레이션된 단계를 포함하는 다목적 빌드 파이프라인입니다. 이러한 단계에는 첫 번째 빌드, 패키징, 테스트, 유효성 검사 및 모든 스테이징 환경으로 배포가 포함됩니다. 따라서 프로덕션 파이프라인은 프로덕션 및 스테이징 환경 세트가 만들어진 후에만 추가할 수 있습니다.

>[!TIP]
>
>문서를 참조하십시오 [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 자세한 내용

## 비프로덕션 파이프라인 {#non-prod-pipeline}

비프로덕션 파이프라인은 주로 코드 품질 검사를 실행하거나 소스 코드를 개발 환경에 배포하는 데 사용됩니다.

>[!TIP]
>
>문서를 참조하십시오 [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) 자세한 내용

## 코드 소스 {#code-sources}

프로덕션 및 비프로덕션 외에도 파이프라인은 배포하는 코드 유형으로 구별할 수 있습니다.

* **[전체 스택 파이프라인](#full-stack-pipeline)** - HTTPD/Dispatcher 구성과 함께 하나 이상의 AEM 서버 애플리케이션을 포함하는 백엔드 및 프런트 엔드 코드 빌드를 동시에 배포
* **[프런트엔드 파이프라인](#front-end)** - 하나 이상의 클라이언트측 UI 애플리케이션을 포함하는 프런트 엔드 코드 빌드 배포
* **[웹 계층 구성 파이프라인](#web-tier-config-pipelines)** - HTTPD/Dispatcher 구성을 배포합니다.

이러한 내용은 이 문서의 뒷부분에 자세히 설명되어 있습니다.

### Cloud Manager의 CI-CD 파이프라인 이해 {#understand-pipelines}

다음 표에는 Cloud Manager에서 사용할 수 있는 모든 파이프라인과 그 사용법이 요약되어 있습니다.

| 파이프라인 유형 | 배포 또는 코드 품질 | 소스 코드 | 목적 | 메모 |
|--- |--- |--- |---|---|
| 프로덕션 또는 비프로덕션 | 배포 | 전체 스택 | HTTPD/Dispatcher 구성과 함께 백엔드 및 프런트 엔드 코드 빌드를 동시에 배포합니다 | 프런트 엔드 코드를 AEM 서버 코드와 동시에 배포해야 하는 경우.<br>프런트 엔드 파이프라인 또는 웹 계층 구성 파이프라인이 아직 채택되지 않은 경우 |
| 프로덕션 또는 비프로덕션 | 배포 | 프런트엔드 | 하나 이상의 클라이언트측 UI 응용 프로그램을 포함하는 프런트 엔드 코드 빌드를 배포합니다. | 여러 동시 프런트엔드 파이프라인 지원<br>전체 스택 배포보다 훨씬 빠름 |
| 프로덕션 또는 비프로덕션 | 배포 | 웹 계층 구성 | HTTPD/Dispatcher 구성을 배포합니다. | 몇 분 후에 배포됩니다. |
| 비프로덕션 | 코드 품질 | 전체 스택 | 배포 없이 전체 스택 코드에서 코드 품질 검사 실행 | 여러 파이프라인 지원 |
| 비프로덕션 | 코드 품질 | 프런트엔드 | 배포 없이 프런트 엔드 코드에서 코드 품질 검사 실행 | 여러 파이프라인 지원 |
| 비프로덕션 | 코드 품질 | 웹 계층 구성 | 배포 없이 Dispatcher 구성에서 코드 품질 검사 실행 | 여러 파이프라인 지원 |

다음 다이어그램은 기존, 단일 프런트 엔드 저장소 또는 독립적인 프런트 엔드 저장소 설정을 사용하는 Cloud Manager의 파이프라인 구성을 보여줍니다.

![Cloud Manager 파이프라인 구성](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## 전체 스택 파이프라인 {#full-stack-pipeline}

전체 스택 파이프라인은 백엔드 코드, 프런트 엔드 코드 및 웹 계층 구성을 모두 AEM 런타임으로 동시에 배포합니다.

* 백엔드 코드 - Java 코드, OSGi 구성, 포인트 및 가변 컨텐츠 등의 변경할 수 없는 컨텐츠
* 프런트 엔드 코드 - JavaScript, CSS, 글꼴과 같은 애플리케이션 UI 리소스
* 웹 계층 구성 - HTTPD/Dispatcher 구성

전체 스택 파이프라인은 &#39;uber&#39; 파이프라인을 나타내며, 모든 작업을 한 번에 수행하는 동시에 사용자에게 프런트 엔드 파이프라인과 웹 계층 구성 파이프라인을 통해 프런트 엔드 코드 또는 Dispatcher 구성을 각각 단독 배포할 수 있는 옵션을 제공합니다.

전체 스택 파이프라인 패키지 프런트 엔드 코드(JavaScript/CSS)는 [AEM 클라이언트 라이브러리.](/help/implementing/developing/introduction/clientlibs.md)

전체 스택 파이프라인은 [웹 계층 구성 파이프라인](#web-tier-config-pipelines) 가 구성되어 있지 않습니다.

다음 제한 사항이 적용됩니다.

* 사용자는 **배포 관리자** 역할을 사용하여 파이프라인을 구성하거나 실행할 수 있습니다.
* 언제든지 환경당 하나의 전체 스택 파이프라인만 있을 수 있습니다.

또한 를 도입하도록 선택하면 전체 스택 파이프라인이 어떻게 동작하는지 알 수 있습니다 [웹 계층 구성 파이프라인.](#web-tier-config-pipelines)

* 해당 웹 계층 구성 파이프라인이 있으면 환경에 대한 전체 스택 파이프라인이 Dispatcher 구성을 무시합니다.
* 환경에 대한 해당 웹 계층 구성 파이프라인이 없으면 사용자는 Dispatcher 구성을 포함하거나 무시하도록 전체 스택 파이프라인을 구성할 수 있습니다.

전체 스택 파이프라인은 코드 품질 파이프라인 또는 배포일 수 있습니다.

## 프런트엔드 파이프라인 {#front-end}

프런트 엔드 코드는 정적 파일로 제공되는 모든 코드입니다. AEM에서 제공하는 UI 코드와는 별도이며 사이트 테마, 고객 정의 SPA, Firefly SPA 및 기타 솔루션을 포함할 수 있습니다.

프런트엔드 파이프라인은 백엔드 개발을 위한 프런트 엔드 코드 비동기적 배포를 가속화하여 설계 및 개발 프로세스를 간소화하는 데 도움이 됩니다. 이 전용 파이프라인은 JavaScript 및 CSS를 AEM 배포 레이어에 테마로 배포하므로 AEM에서 제공한 페이지에서 참조할 수 있는 새로운 테마 버전이 제공됩니다.

>[!IMPORTANT]
>
>AEM 버전을 사용해야 합니다. `2021.10.5933.20211012T154732Z ` 또는 AEM Sites이 프런트엔드 파이프라인을 활용하도록 활성화되면 더 이상 이 옵션을 사용할 수 없습니다.

>[!NOTE]
>
>을 사용하는 사용자 **배포 관리자** 역할은 여러 프런트 엔드 파이프라인을 동시에 생성하고 실행할 수 있습니다.
>
>그러나 프로그램당 최대 300개의 파이프라인(모든 유형)이 있습니다. 프런트엔드 코드 품질 또는 프런트 엔드 배포 파이프라인이 될 수 있습니다.

프런트엔드 파이프라인은 코드 품질 파이프라인 또는 배포일 수 있습니다.

### 프런트엔드 파이프라인을 구성하기 전에 {#before-start}

프런트엔드 파이프라인을 구성하기 전에 [AEM 빠른 사이트 만들기 여정](/help/journey-sites/quick-site/overview.md) 사용하기 쉬운 AEM 빠른 사이트 만들기 도구를 통한 종단 간 안내서입니다. 이 여정을 통해 프런트 엔드 개발을 간소화할 수 있고, 백 엔드 AEM 지식 없이도 사이트를 신속하게 사용자 정의할 수 있습니다.

### 프런트엔드 파이프라인 구성 {#configure-front-end}

프런트 엔드 파이프라인을 구성하는 방법에 대해 알아보려면 다음 문서를 참조하십시오.

* [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### 프론트엔드 파이프라인으로 Sites 개발 {#developing-with-front-end-pipeline}

프런트엔드 파이프라인을 통해 프런트엔드 개발자에게 더 많은 독립성을 부여하여 개발 프로세스를 가속화할 수 있습니다.

문서를 참조하십시오 [프런트엔드 파이프라인을 사용한 사이트 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) 이 프로세스의 전체 가능성을 얻기 위해 몇 가지 고려 사항과 함께 이 프로세스가 작동하는 방식에 대해 설명합니다.

### 전체 스택 파이프라인 구성 {#configure-full-stack}

전체 스택 파이프라인을 구성하는 방법에 대해 알아보려면 다음 문서를 참조하십시오.

* [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)


## 웹 계층 구성 파이프라인 {#web-tier-config-pipelines}

웹 계층 구성 파이프라인은 다른 코드 변경 사항에서 HTTPD/Dispatcher 구성을 분리하여 AEM 런타임으로 독점적으로 배포할 수 있도록 합니다. Dispatcher 구성 변경 사항만 배포하려는 사용자를 제공하는 간소화된 파이프라인이며 몇 분 안에 이를 가속화하는 방법입니다.

>[!TIP]
>
>웹 계층 구성 파이프라인을 사용하면 프로젝트에 더 적합한 구조에 따라 전체 스택 파이프라인과 동일한 소스 위치에 웹 구성을 저장하거나 다른 위치에 저장할 것인지 선택할 수 있습니다.

다음 제한 사항이 적용됩니다.

* AEM 버전을 사용해야 합니다. `2021.12.6151.20211217T120950Z` 웹 계층 구성 파이프라인을 활용하기 위한 최신 버전입니다.
* 다음을 수행해야 합니다. [dispatcher 도구의 유연한 모드로 옵트인합니다.](/help/implementing/dispatcher/disp-overview.md#validation-debug) 웹 계층 구성 파이프라인을 활용합니다.
* 사용자는 **배포 관리자** 역할을 사용하여 파이프라인을 구성하거나 실행할 수 있습니다.
* 언제든지 환경당 하나의 웹 계층 구성 파이프라인만 있을 수 있습니다.
* 해당 전체 스택 파이프라인이 실행 중인 경우 웹 계층 구성 파이프라인을 구성할 수 없습니다.
* 웹 계층 구조는 문서에 정의된 대로 유연한 모드 구조를 준수해야 합니다 [클라우드의 디스패처.](/help/implementing/dispatcher/disp-overview.md#validation-debug)

또한 [전체 스택 파이프라인](#full-stack-pipeline) 은 웹 계층 파이프라인을 도입하면 동작합니다.

* 웹 계층 구성 파이프라인이 환경에 대해 구성되지 않은 경우 실행 및 배포 중에 해당 전체 스택 파이프라인을 구성하여 Dispatcher 구성을 포함하거나 무시할 수 있습니다.
* 환경에 대해 웹 계층 구성 파이프라인이 구성되면 해당 전체 스택 파이프라인(있는 경우)이 실행 및 배포 중에 디스패처 구성을 무시합니다.
* 웹 계층 구성 파이프라인이 삭제되면 실행 중에 해당 전체 스택 파이프라인이 Dispatcher 구성을 배포하도록 재설정됩니다.

웹 계층 구성 파이프라인은 코드 형식 또는 배포일 수 있습니다.

### 웹 계층 구성 파이프라인 구성 {#configure-web-tier-config-pipelines}

웹 계층 구성 파이프라인을 구성하는 방법에 대해 알아보려면 다음 문서를 참조하십시오.

* [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)
