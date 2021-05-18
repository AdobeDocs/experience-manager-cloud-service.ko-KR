---
title: 헤드리스 애플리케이션을 사용하여 라이브하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 Git에서 로컬 코드를 가져와 CI/CD 파이프라인을 위해 Cloud Manager Git으로 이동하여 헤드리스 애플리케이션을 라이브로 배포하는 방법을 살펴볼 수 있습니다.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
source-git-commit: 4c743eede23f09f285d9da84b149226f7288fcc3
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 0%

---

# 헤드리스 응용 프로그램 {#go-live}을 사용하여 라이브하는 방법

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정](overview.md)의 이 부분에서 로컬 코드를 Git에서 가져와 CI/CD 파이프라인을 위해 Cloud Manager Git으로 이동하여 헤드리스 애플리케이션을 라이브로 배포하는 방법을 알아봅니다.

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서, [모두 함께 놓는 방법 - 앱 및 콘텐츠를 AEM 헤드리스](put-it-all-together.md)에서 라이브할 AEM 헤드리스 프로젝트를 준비하는 방법을 학습했고 이제 다음을 수행해야 합니다.

* 라이브해야 하는 요구 사항을 이해합니다.

이 문서는 이러한 기본 사항을 바탕으로 작성되므로 AEM 헤드리스 프로젝트를 라이브하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

이 문서는 AEM 헤드리스 게시 파이프라인과 애플리케이션을 라이브하기 전에 알아야 할 성능 고려 사항을 이해하는 데 도움이 됩니다.

* AEM SDK 및 필요한 개발 도구에 대해 자세히 알아보기
* 라이브되기 전에 컨텐츠를 시뮬레이션하도록 로컬 개발 런타임을 설정합니다.
* AEM 컨텐츠 복제 및 캐싱 기본 사항 이해
* 실행 전에 애플리케이션 보안 및 확장
* 성능 및 디버그 문제 모니터링

## AEM SDK {#the-aem-sdk}

AEM SDK는 사용자 지정 코드를 빌드하고 배포하는 데 사용됩니다. 라이브하기 전에 헤드리스 애플리케이션을 개발 및 테스트하기 위해 필요한 주요 툴입니다. 여기에는 다음과 같은 가공물이 포함됩니다.

* 빠른 시작 jar - 작성자 및 게시 인스턴스를 모두 설정하는 데 사용할 수 있는 실행 jar 파일입니다
* Dispatcher 도구 - Windows 및 UNIX 기반 시스템에 대한 Dispatcher 모듈 및 해당 종속성
* Java API Jar - AEM에서 개발하는 데 사용할 수 있는 모든 허용되는 Java API를 표시하는 Java Jar/Maven 종속성
* Javadoc jar - Java API jar용 javadocs

## 추가 개발 도구 {#additional-development-tools}

AEM SDK 외에도 자신의 코드와 컨텐츠를 로컬에서 개발 및 테스트할 수 있는 추가 툴이 필요합니다.

* Java
* Git
* Apache Maven
* Node.js 라이브러리
* 원하는 IDE

AEM은 Java 애플리케이션이므로 Java 및 Java SDK를 설치하여 Cloud Service으로 AEM 개발을 지원해야 합니다.

Git은 소스 제어를 관리하고 Cloud Manager의 변경 사항을 체크 인한 다음 프로덕션 인스턴스에 배포하는 데 사용할 수 있습니다.

AEM은 Apache Maven을 사용하여 AEM Maven Project 원형에서 생성된 프로젝트를 제작합니다. 모든 주요 IDE는 Maven에 대한 통합 지원을 제공합니다.

Node.js는 AEM 프로젝트의 `ui.frontend` 하위 프로젝트의 프런트 엔드 에셋을 사용하여 작업하는 데 사용되는 JavaScript 런타임 환경입니다. Node.js는 사실상의 Node.js 패키지 관리자로서 JavaScript 종속성을 관리하는 데 사용됩니다.

## AEM 시스템 구성 요소 개요 {#components-of-an-aem-system-at-a-glance}

다음으로 AEM 환경의 구성 부분을 살펴보겠습니다.

전체 AEM 환경은 작성자, 게시 및 발송자로 구성됩니다. 이러한 동일한 구성 요소는 라이브되기 전에 코드와 컨텐츠를 보다 쉽게 미리 볼 수 있도록 로컬 개발 런타임에서 사용할 수 있습니다.

* **작성자** 서비스는 내부 사용자가 컨텐츠를 만들고, 관리하고 미리 보는 서비스입니다.

* **게시 서비스** 는 &quot;라이브&quot; 환경으로 간주되며 일반적으로 최종 사용자가 상호 작용하는 부분입니다. 작성 서비스에서 편집 및 승인된 컨텐츠는 게시 서비스로 배포됩니다. AEM 헤드리스 응용 프로그램의 가장 일반적인 배포 패턴은 AEM 게시 서비스에 응용 프로그램의 제작 버전을 연결하는 것입니다.

* **Dispatcher** 는 AEM 디스패처 모듈로 보강된 정적 웹 서버입니다. 게시 인스턴스에서 생성한 웹 페이지를 캐시하여 성능을 향상시킵니다.

## 로컬 개발 워크플로 {#the-local-development-workflow}

로컬 개발 프로젝트는 Apache Maven을 기반으로 구축되었으며 소스 제어에 Git을 사용합니다. 프로젝트를 업데이트하기 위해 개발자는 Eclipse, Visual Studio 코드 또는 IntelliJ와 같은 선호하는 통합 개발 환경을 다른 개발 환경에서 사용할 수 있습니다.

헤드리스 애플리케이션에서 인제스트할 코드 또는 컨텐츠 업데이트를 테스트하려면 AEM 작성자 및 게시 서비스의 로컬 인스턴스가 포함된 로컬 AEM 런타임에 업데이트를 배포해야 합니다.

업데이트 내용이 가장 중요한 위치를 테스트하는 것이 중요하므로 로컬 AEM 런타임에서 각 구성 요소 간의 차이를 주목하십시오. 예를 들어 제작 시 컨텐츠 업데이트를 테스트하거나 게시 인스턴스에서 새 코드를 테스트합니다.

프로덕션 시스템에서 디스패처와 http Apache 서버는 항상 AEM 게시 인스턴스 앞에 배치됩니다. AEM 시스템을 위한 캐싱 및 서비스 서비스를 제공하므로 디스패처에 대한 코드와 컨텐츠 업데이트를 테스트하는 것도 중요합니다.

## 로컬 개발 환경 {#previewing-your-code-and-content-locally-with-the-local-development-environment}을(를) 사용하여 로컬로 코드 및 컨텐츠 미리 보기

AEM 헤드가 없는 프로젝트를 시작할 수 있도록 준비하려면 프로젝트의 모든 구성 요소가 제대로 작동하는지 확인해야 합니다.

그러기 위해서는 모든 것을 함께 결합해야 합니다.코드, 컨텐츠 및 구성을 확인하고 로컬 개발 환경에서 테스트하여 라이브할 수 있도록 합니다.

로컬 개발 환경은 3개의 주요 영역으로 구성됩니다.

1. AEM 프로젝트 - AEM 개발자가 작업하려는 모든 사용자 정의 코드, 구성 및 컨텐츠를 포함합니다.
1. AEM 프로젝트에서 코드를 배포하는 데 사용되는 AEM 작성자 및 게시 서비스의 로컬 버전 로컬 AEM 런타임
1. Local Dispatcher 런타임 - Dispatcher 모듈을 포함하는 Apache httpd 웹 서버의 로컬 버전입니다.

로컬 개발 환경이 설정되면 정적 노드 서버를 로컬로 배포하여 Response 앱에 제공하는 컨텐츠를 시뮬레이션할 수 있습니다.

로컬 개발 환경 설정 및 컨텐츠 미리 보기에 필요한 모든 종속성을 자세히 살펴보려면 [프로덕션 배포 설명서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=en#prerequisites)를 참조하십시오.

## AEM 헤드리스 응용 프로그램을 Go-Live {#prepare-your-aem-headless-application-for-golive} 준비합니다.

이제 아래에 설명된 모범 사례를 따라 AEM 헤드리스 애플리케이션을 시작할 준비가 되었습니다.

### {#secure-and-scale-before-launch} 실행 전에 헤드리스 응용 프로그램의 보안 및 크기 조절

1. GraphQL 요청으로 [토큰 기반 인증](/help/assets/content-fragments/graphql-authentication-content-fragments.md)을 구성합니다.
1. [캐싱](/help/implementing/dispatcher/caching.md)을 구성합니다.

### 모델 구조와 GraphQL 출력 비교 {#structure-vs-output}

* 15kb 이상의 JSON(gzip 압축)을 출력하는 쿼리를 만들지 마십시오. 긴 JSON 파일은 클라이언트 응용 프로그램이 구문 분석하기 위해 리소스를 많이 사용합니다.
* 5개 이상의 중첩 수준 조각 계층을 피하십시오. 추가 수준을 통해 컨텐츠 작성자는 변경 사항의 영향을 고려하기가 어렵습니다.
* 모델 내의 종속성 계층 구조 쿼리를 모델링 대신 다중 개체 쿼리를 사용합니다. 따라서 많은 컨텐츠 변경 작업을 수행하지 않고도 JSON 출력을 다시 구성할 수 있는 보다 장기적인 유연성을 확보할 수 있습니다.

### CDN 캐시 히트 비율 최대화 {#maximize-cdn}

* 표면으로부터 라이브 컨텐츠를 요청하지 않는 한 직접 GraphQL 쿼리를 사용하지 마십시오.
   * 가능하면 지속적인 쿼리를 사용하십시오.
   * CDN이 TTL을 캐시하려면 600초 이상의 CDN TTL을 제공합니다.
   * AEM은 기존 쿼리에 대한 모델 변경 영향을 계산할 수 있습니다.
* 클라이언트 트래픽을 CDN으로 줄이고 높은 TTL을 할당하기 위해 낮은 및 높은 컨텐츠 변경률 간에 JSON 파일/GraphQL 쿼리를 분할할 수 있습니다. 이렇게 하면 원본 서버와 JSON의 유효성을 다시 검사하는 CDN이 최소화됩니다.
* CDN에서 컨텐츠를 능동적으로 무효화하려면 소프트 숙지를 사용합니다. 이를 통해 CDN은 캐시 오류를 발생시키지 않고 컨텐츠를 다시 다운로드할 수 있습니다.

### 헤드리스 콘텐츠 다운로드 시간 개선 {#improve-download-time}

* HTTP 클라이언트가 HTTP/2를 사용하는지 확인합니다.
* HTTP 클라이언트가 gzip에 대한 헤더 요청을 수락하는지 확인하십시오.
* JSON 및 참조된 아티팩트를 호스트하는 데 사용되는 도메인 수를 최소화합니다.
* `Last-modified-since`을 활용하여 리소스를 새로 고칩니다.
* 전체 JSON 파일을 구문 분석할 필요 없이 JSON 파일에서 `_reference` 출력을 사용하여 에셋 다운로드를 시작합니다.

## 프로덕션 {#deploy-to-production}에 배포

모든 것이 테스트되고 제대로 작동하는지 확인한 후 코드 업데이트를 Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html)의 중앙 Git 리포지토리로 푸시할 준비가 되었습니다.[

업데이트를 Cloud Manager에 업로드한 후 [Cloud Manager의 CI/CD 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)을(를) 사용하여 Cloud Service으로 AEM에 배포할 수 있습니다.

Cloud Manager CI/CD 파이프라인을 활용하여 코드 배포를 시작할 수 있습니다. 파이프라인은 대부분 [여기](/help/implementing/deploying/overview.md)에 포함되어 있습니다.

## 성능 모니터링 {#performance-monitoring}

사용자가 AEM 헤드리스 애플리케이션을 사용할 때 최상의 경험을 얻으려면 아래 설명에 따라 주요 성능 지표를 모니터링해야 합니다.

* 앱의 미리 보기 및 제작 버전 확인
* 현재 서비스 가용성 상태에 대한 AEM 상태 페이지 확인
* 성능 보고서 액세스
   * 전달 성능
      * 명확한 (CDN) - 호출 수, 캐시 속도, 오류 속도, 페이로드 트래픽 확인
      * 원본 서버 - 호출 수, 오류 속도, CPU 로드, 페이로드 트래픽
   * 작성자 성능
      * 사용자, 요청 및 로드 수 확인
* 앱 및 공간별 성능 보고서 액세스
   * 서버가 작동하면 일반 지표가 녹색/주황색/빨간색 인지 확인한 다음 특정 앱 문제를 식별합니다
   * 앱/공간에 대해 필터링된 위의 동일한 보고서 열기(예: Photoshop 데스크톱, 유료화 등)
   * Splunk 로그 API를 사용하여 서비스 및 애플리케이션 성능에 액세스
   * 다른 문제가 있을 경우 고객 지원에 문의하십시오.

## 문제 해결 {#troubleshooting}

### 디버깅 {#debugging}

디버깅에 대한 일반적인 방법으로 다음 우수 사례를 따르십시오.

* 애플리케이션의 미리 보기 버전을 사용하여 기능 및 성능 확인
* 애플리케이션의 제작 버전을 사용하여 기능 및 성능 확인
* 컨텐츠 조각 편집기의 JSON 미리 보기를 사용하여 유효성 확인
* 클라이언트 응용 프로그램의 JSON에서 Inspect을 사용하여 클라이언트 응용 프로그램 또는 전달 문제가 있는지 확인
* GraphQL을 사용하여 JSON을 Inspect으로 사용하여 캐시된 컨텐츠 또는 AEM과 관련된 문제가 있는지 확인

### 지원 {#logging-a-bug-with-support} 관련 버그 기록

추가 지원이 필요할 경우 지원 기능으로 버그를 효율적으로 기록하려면 아래 단계를 따르십시오.

* 필요한 경우 문제 스크린샷 적용
* 문제를 재현할 수 있는 방법을 문서화합니다.
* 발행물이 작성한 내용을 문서로 작성
* AEM 지원 포털을 통해 적절한 우선 순위로 문제를 기록

## 다음 {#what-is-next} 소개

AEM 헤드리스 개발자 여정의 이 부분을 완료하셨다면 다음을 수행해야 합니다.

* AEM 컨텐츠 복제 및 캐싱 기본 사항을 이해합니다.
* 헤드리스 애플리케이션에 맞게 라이브되도록 시뮬레이트하는 데 필요한 도구 구성 방법을 알아봅니다.
* 애플리케이션을 실행하기 전에 보안을 설정하고 크기를 조절하는 방법을 알아봅니다.
* 성능 및 디버그 문제를 모니터하는 방법을 이해합니다.

## 여정이 끝나요? 아니면 끝나요?{#journey-ends}

축하합니다! AEM 헤드리스 개발자 여정을 완료했습니다. 이제 다음을 이해해야 합니다.

* 헤드리스 콘텐츠와 헤드리스 콘텐츠 전달 간의 차이점
* AEM 헤드리스 기능
* 헤드리스 프로젝트를 구성하고 AEM 헤드리스 프로젝트를 구성하는 방법
* AEM에서 헤드리스 컨텐츠를 만드는 방법
* AEM에서 헤드리스 컨텐츠를 검색하고 업데이트하는 방법.
* AEM 헤드리스 프로젝트를 라이브하는 방법
* 라이브하고 나면 어떻게 하죠?

## 추가 리소스 {#additional-resources}

* [Cloud Service으로 AEM에 배포 개요](/help/implementing/deploying/overview.md)
* [Cloud Service SDK로서 AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [로컬 AEM 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [Cloud Manager를 사용하여 코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Cloud Manager Git 리포지토리를 외부 Git 리포지토리와 통합하고 프로젝트를 AEM에 Cloud Service으로 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)