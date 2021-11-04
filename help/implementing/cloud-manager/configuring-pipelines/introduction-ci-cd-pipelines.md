---
title: CI-CD Pipelines
description: Follow this page to learn about Cloud Manager CI-CD Pipelines
index: false
source-git-commit: c6c1d3bef85afda0ff86ec073d0ac91ad532c93b
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---


# Cloud Manager CI-CD 파이프라인 {#intro-cicd}

## 소개 {#introduction}

Cloud Manager의 CI/CD 파이프라인은 소스 코드 리포지토리의 끌어오기 요청, 코드 변경 또는 릴리스 케이던스와 일치시키기 위한 일종의 정규 일정과 같은 일부 유형의 이벤트에 의해 트리거될 수 있습니다.

>[!NOTE]
>파이프라인을 구성하려면 다음을 수행해야 합니다.
>* 파이프라인을 시작할 트리거 정의
>* define the parameters controlling the production deployment
>* 성능 테스트 매개 변수 구성


Cloud Manager에는 두 가지 유형의 파이프라인이 있습니다.

* [프로덕션 파이프라인](#prod-pipeline)
* [비프로덕션 파이프라인](#non-prod-pipeline)

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config.png)


## 프로덕션 파이프라인 {#prod-pipeline}

A Production pipelines is a purpose built pipeline that includes a series of orchestrated steps to take source code all the way into production. 먼저 모든 스테이지 환경에 구축, 패키징, 테스트, 유효성 검사 및 배포를 포함합니다. 뿐만 아니라 프로덕션 및 스테이지 환경 세트를 만든 후에만 프로덕션 파이프라인을 추가할 수 있습니다.

Refer to [Configuring a Production Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) for more details.


## 비프로덕션 파이프라인 {#non-prod-pipeline}

A Non-Production Pipeline aims to run code-quality scans or to deploy source code into a development environment.

을(를) 참조하십시오. [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) 자세한 내용

## Cloud Manager의 CI-CD 파이프라인 이해 {#understand-pipelines}

다음 표에는 Cloud Manager의 모든 파이프라인과 해당 사용법이 요약되어 있습니다.

| 파이프라인 유형 | 배포 또는 코드 품질 | 소스 코드 | 사용 시기 | 언제 또는 왜 사용해야 합니까? |
|--- |--- |--- |---|---|---|
| 프로덕션 또는 비프로덕션 | 배포 | 프런트엔드 | 신속한 배포 시간<br>여러 프런트 엔드 파이프라인을 구성하여 환경에 따라 동시에 실행할 수 있습니다.<br>프런트 엔드 파이프라인 빌드가 빌드에서 저장소로 푸시됩니다. html 페이지가 제공될 때 이 저장소를 원본으로 사용하여 CDN에서 제공할 Frontend Code 정적 파일을 참조할 수 있습니다. | To exclusively deploy front end code containing one or more clientside UI applications. Front end code is any code that is served as a static file. AEM에서 제공하는 UI 코드와는 별개입니다. 여기에는 사이트 테마, 고객이 정의한 SPA, Firefly SPA 및 기타 모든 솔루션이 포함됩니다.<br>AEM 버전이어야 합니다. `2021.10.5933.20211012T154732Z` |
| 프로덕션 또는 비프로덕션 | 배포 | 전체 스택 | When Front end pipelines have not yet  been adopted.<br>For cases where the Front End code must be deployed at exactly the same time as the AEM Server code. | 하나 이상의 AEM 서버 응용 프로그램을 동시에 포함하는 AEM 서버 코드(변경할 수 없는 컨텐츠, Java 코드, OSGi 구성, HTTPD/dispatcher 구성, 포인터, 가변 컨텐츠, 글꼴)를 배포하려면 다음을 수행하십시오. |
| 비프로덕션 | Code Quality | 프런트엔드 | Cloud Manager에서 배포를 수행하지 않고 빌드 성공 및 코드 품질을 평가하도록 합니다.<br>Multiple pipelines can be configured and run. | Run code quality scans on front end code. |
| 비프로덕션 | 코드 품질 | Full Stack | To have Cloud Manager evaluate your build success and code quality without doing a deployment.<br>Multiple pipelines can be configured and run. | Run code quality scan on the full stack code. |

The following diagram illustrates Cloud Manager pipeline configurations with traditional, single front-end repository or independent front-end repository setup:

![](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Cloud Manager Front End Pipelines {#front-end}

프런트 엔드 파이프라인은 프런트 엔드 코드를 배포할 수 있도록 빨라진 프런트 엔드 파이프라인을 활성화하여 설계 및 개발 프로세스를 간소화할 수 있도록 지원합니다. 이렇게 구별된 파이프라인은 JavaScript 및 CSS를 AEM 배포 레이어에 테마로 배포하므로 AEM 런타임에서 전달된 페이지에서 참조할 수 있는 새로운 테마 버전이 제공됩니다. Front end code is any code that is served as a static file. AEM에서 제공하는 UI 코드와는 별개입니다. 여기에는 사이트 테마, 고객이 정의한 SPA, Firefly SPA 및 기타 모든 솔루션이 포함됩니다.

>[!IMPORTANT]
>AEM 버전을 사용해야 합니다. `2021.10.5933.20211012T154732Z ` 프런트엔드 파이프라인을 활용합니다.

>[!NOTE]
>A user logged in as Deployment Manager role can create and run multiple front end pipelines concurrently. 그러나 프로그램당 최대 300개의 파이프라인(모든 유형)이 있습니다.

These can be of the type Front End Code Quality or Front End Deployment pipelines.

### 프런트엔드 파이프라인을 구성하기 전에 {#before-start}

Before you start configuring the Front End pipelines, see AEM Quick Site Creation Journey for an end to end workflow through the easy-to-use AEM Quick Site Creation tool. 이 설명서 사이트를 통해 AEM 사이트의 프런트 엔드 개발을 간소화하고 AEM 백엔드 지식이 없는 사용자를 신속하게 사용자 지정할 수 있습니다.

### 프런트엔드 파이프라인 구성 {#configure-front-end}

프런트 엔드 파이프라인을 구성하는 방법에 대해 알아보려면 다음을 참조하십시오.

* [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Adding a Non-Production Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

## Full Stack Pipelines {#full-stack-pipeline}

전체 스택 파이프라인은 사용자에게 백엔드, 프런트엔드 및 HTTPD/디스패처 구성을 동시에 배포할 수 있는 옵션을 제공합니다.  It deploys code and content to the AEM runtime including front end code (JavaScript/CSS) packaged as AEM Client Libraries. 웹 계층 파이프라인이 구성되지 않은 경우 웹 계층 구성을 배포할 수 있습니다. 이는 &#39;uber&#39; 파이프라인을 나타내지만, 사용자에게 프런트 엔드 파이프라인과 웹 계층 구성 파이프라인을 통해 프런트 엔드 코드 또는 디스패처 구성을 각각 배타적으로 배포할 수 있는 옵션을 제공합니다.

다음 제한 사항이 적용됩니다.

1. 파이프라인을 구성하거나 실행하려면 사용자가 배포 관리자로 로그인해야 합니다.

1. 언제든지 환경당 전체 스택 파이프라인은 하나만 있을 수 있습니다.

1. 사용자는 환경에 대한 해당 웹 계층 구성 파이프라인이 없는 경우 디스패처 구성을 무시하거나 무시하도록 환경에 대한 전체 스택 파이프라인을 구성할 수 있습니다.

1. 환경에 대한 해당 웹 계층 구성 파이프라인이 있으면 환경에 대한 전체 스택 파이프라인이 디스패처 구성을 무시합니다.

These can be of the type Full Stack - Code Quality or Full Stack - Deployment pipeline.

### 전체 스택 파이프라인 구성 {#configure-full-stack}

전체 스택 파이프라인을 구성하는 방법에 대해 알아보려면 다음을 참조하십시오.

* [Adding a Production Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline))
* [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)