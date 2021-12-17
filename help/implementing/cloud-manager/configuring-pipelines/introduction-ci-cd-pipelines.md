---
title: CI-CD 파이프라인
description: Cloud Manager CI-CD 파이프라인에 대해 알아보려면 이 페이지를 따르십시오
index: true
source-git-commit: 3d48bd507305e7a1d3efa2b61123afdae1f52ced
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---


# Cloud Manager CI-CD 파이프라인 {#intro-cicd}

## 소개 {#introduction}

Cloud Manager의 CI/CD 파이프라인은 소스 코드 리포지토리의 끌어오기 요청, 코드 변경 또는 릴리스 케이던스와 일치시키기 위한 일종의 정규 일정과 같은 일부 유형의 이벤트에 의해 트리거될 수 있습니다.

>[!NOTE]
>파이프라인을 구성하려면 다음을 수행해야 합니다.
>* 파이프라인을 시작할 트리거 정의
>* 프로덕션 배포를 제어하는 매개 변수 정의
>* 성능 테스트 매개 변수 구성


Cloud Manager에는 두 가지 유형의 파이프라인이 있습니다.

* [프로덕션 파이프라인](#prod-pipeline)
* [비프로덕션 파이프라인](#non-prod-pipeline)

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)


## 프로덕션 파이프라인 {#prod-pipeline}

프로덕션 파이프라인은 소스 코드를 프로덕션에 완전히 투입하기 위해 일련의 오케스트레이션된 단계를 포함하는 목적으로 빌드된 파이프라인입니다. 먼저 모든 스테이지 환경에 구축, 패키징, 테스트, 유효성 검사 및 배포를 포함합니다. 뿐만 아니라 프로덕션 및 스테이지 환경 세트를 만든 후에만 프로덕션 파이프라인을 추가할 수 있습니다.

을(를) 참조하십시오. [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 자세한 내용


## 비프로덕션 파이프라인 {#non-prod-pipeline}

비프로덕션 파이프라인은 코드 품질 검사를 실행하거나 소스 코드를 개발 환경에 배포하는 것을 목표로 합니다.

을(를) 참조하십시오. [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) 자세한 내용

## Cloud Manager의 CI-CD 파이프라인 이해 {#understand-pipelines}

다음 표에는 Cloud Manager의 모든 파이프라인과 해당 사용법이 요약되어 있습니다.

| 파이프라인 유형 | 배포 또는 코드 품질 | 소스 코드 | 사용 시기 | 언제 또는 왜 사용해야 합니까? |
|--- |--- |--- |---|---|
| 프로덕션 또는 비프로덕션 | 배포 | 프런트엔드 | 신속한 배포 시간<br>여러 프런트 엔드 파이프라인을 구성하여 환경에 따라 동시에 실행할 수 있습니다.<br>프런트 엔드 파이프라인 빌드가 빌드에서 저장소로 푸시됩니다. html 페이지가 제공될 때 이 저장소를 원본으로 사용하여 CDN에서 제공할 Frontend Code 정적 파일을 참조할 수 있습니다. | 하나 이상의 클라이언트측 UI 응용 프로그램이 포함된 프런트 엔드 코드를 독점적으로 배포하려면 프런트 엔드 코드는 정적 파일로 제공되는 모든 코드입니다. AEM에서 제공하는 UI 코드와는 별개입니다. 여기에는 사이트 테마, 고객이 정의한 SPA, Firefly SPA 및 기타 모든 솔루션이 포함됩니다.<br>AEM 버전 2021.10.5933.20211012T154732Z에 있어야 합니다.<br>Sites가 활성화되어 있어야 합니다. |
| 프로덕션 또는 비프로덕션 | 배포 | 전체 스택 | 프런트 엔드 파이프라인이 아직 채택되지 않은 경우<br>프런트 엔드 코드를 AEM 서버 코드와 정확히 동시에 배포해야 하는 경우 | 하나 이상의 AEM 서버 응용 프로그램을 동시에 포함하는 AEM 서버 코드(변경할 수 없는 컨텐츠, Java 코드, OSGi 구성, HTTPD/dispatcher 구성, 포인터, 가변 컨텐츠, 글꼴)를 배포하려면 다음을 수행하십시오. |
| 비프로덕션 | 코드 품질 | 프런트엔드 | Cloud Manager를 평가하도록 합니다. 배포를 수행하지 않고 빌드 성공 및 코드 품질을 확인합니다.<br>여러 파이프라인을 구성하고 실행할 수 있습니다. | 프런트 엔드 코드에서 코드 품질 검사를 실행합니다. |
| 비프로덕션 | 코드 품질 | 전체 스택 | Cloud Manager를 평가하도록 합니다. 배포를 수행하지 않고 빌드 성공 및 코드 품질을 확인합니다.<br>여러 파이프라인을 구성하고 실행할 수 있습니다. | 전체 스택 코드에서 코드 품질 검사를 실행합니다. |


다음 다이어그램은 기존의 단일 프런트 엔드 저장소 또는 독립 프런트 엔드 저장소 설정을 사용하는 Cloud Manager 파이프라인 구성을 보여줍니다.

![](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Cloud Manager 프런트엔드 파이프라인 {#front-end}

프런트 엔드 파이프라인은 프런트 엔드 코드를 배포할 수 있도록 빨라진 프런트 엔드 파이프라인을 활성화하여 설계 및 개발 프로세스를 간소화할 수 있도록 지원합니다. 이렇게 구별된 파이프라인은 JavaScript 및 CSS를 AEM 배포 레이어에 테마로 배포하므로 AEM 런타임에서 전달된 페이지에서 참조할 수 있는 새로운 테마 버전이 제공됩니다. 프런트 엔드 코드는 정적 파일로 제공되는 모든 코드입니다. AEM에서 제공하는 UI 코드와는 별개입니다. 여기에는 사이트 테마, 고객이 정의한 SPA, Firefly SPA 및 기타 모든 솔루션이 포함됩니다.

>[!IMPORTANT]
>AEM 버전을 사용해야 합니다. `2021.10.5933.20211012T154732Z ` 프런트엔드 파이프라인을 활용합니다.

>[!NOTE]
>배포 관리자 역할로 로그인한 사용자는 여러 프런트 엔드 파이프라인을 동시에 만들고 실행할 수 있습니다. 그러나 프로그램당 최대 300개의 파이프라인(모든 유형)이 있습니다.

프런트엔드 코드 품질 또는 프런트 엔드 배포 파이프라인 유형일 수 있습니다.

### 프런트엔드 파이프라인을 구성하기 전에 {#before-start}

프런트엔드 파이프라인 구성을 시작하기 전에 [AEM 빠른 사이트 만들기 여정](/help/journey-sites/quick-site/overview.md) 사용하기 쉬운 AEM 빠른 사이트 만들기 도구를 통해 전체 워크플로우를 완료하십시오. 이 설명서 사이트를 통해 AEM 사이트의 프런트 엔드 개발을 간소화하고 AEM 백엔드 지식이 없는 사용자를 신속하게 사용자 지정할 수 있습니다.

### 프런트엔드 파이프라인 구성 {#configure-front-end}

프런트 엔드 파이프라인을 구성하는 방법에 대해 알아보려면 다음을 참조하십시오.

* [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### 프런트엔드 파이프라인을 사용한 사이트 개발 {#developing-with-front-end-pipeline}

프런트엔드 파이프라인을 통해 프런트엔드 개발자에게 더 많은 독립성이 부여되며, 개발 프로세스를 통해 상당한 속도를 향상시킬 수 있습니다.

을(를) 참조하십시오. [이 문서](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) 이 프로세스의 전체 가능성을 얻기 위해 몇 가지 고려 사항과 함께 이 프로세스가 작동하는 방식에 대해 설명합니다.

## 전체 스택 파이프라인 {#full-stack-pipeline}

전체 스택 파이프라인은 사용자에게 백엔드, 프런트엔드 및 HTTPD/디스패처 구성을 동시에 배포할 수 있는 옵션을 제공합니다.  AEM 클라이언트 라이브러리로 패키지된 프런트 엔드 코드(JavaScript/CSS)를 포함하여 코드 및 컨텐츠를 AEM 런타임으로 배포합니다. 웹 계층 파이프라인이 구성되지 않은 경우 웹 계층 구성을 배포할 수 있습니다. 이는 &#39;uber&#39; 파이프라인을 나타내지만, 사용자에게 프런트 엔드 파이프라인과 웹 계층 구성 파이프라인을 통해 프런트 엔드 코드 또는 디스패처 구성을 각각 배타적으로 배포할 수 있는 옵션을 제공합니다.
전체 스택 - 코드 품질 또는 전체 스택 - 배포 파이프라인 유형일 수 있습니다.

다음 제한 사항이 적용됩니다.

1. 파이프라인을 구성하거나 실행하려면 사용자가 배포 관리자로 로그인해야 합니다.

1. 언제든지 환경당 전체 스택 파이프라인은 하나만 있을 수 있습니다.

1. 사용자는 환경에 대한 해당 웹 계층 구성 파이프라인이 없는 경우 디스패처 구성을 무시하거나 무시하도록 환경에 대한 전체 스택 파이프라인을 구성할 수 있습니다.

1. 환경에 대한 해당 웹 계층 구성 파이프라인이 있으면 환경에 대한 전체 스택 파이프라인이 디스패처 구성을 무시합니다.


### 전체 스택 파이프라인 구성 {#configure-full-stack}

전체 스택 파이프라인을 구성하는 방법에 대해 알아보려면 다음을 참조하십시오.

* [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)