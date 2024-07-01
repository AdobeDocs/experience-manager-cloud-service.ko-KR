---
title: 결합 방법 - AEM Headless의 앱과 콘텐츠
description: 이 AEM Headless 개발자 여정의 부분에서는 콘텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션 등 AEM 프로젝트를 가져와 실행을 준비하는 방법에 대해 알아봅니다.
exl-id: bece84ad-4c8c-410c-847e-9ef3f79970cb
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: ht
source-wordcount: '1061'
ht-degree: 100%

---

# 결합 방법 - AEM Headless의 앱과 콘텐츠 {#put-it-all-together}

이 [AEM Headless 개발자 여정](overview.md)의 부분에서는 AEM 개발 도구와 Headless SDK를 사용하여 애플리케이션을 결합하는 방법을 숙지합니다.

## 지금까지의 스토리 {#story-so-far}

AEM Headless 번역 여정의 이전 문서인 [AEM Assets API를 통해 콘텐츠를 업데이트하는 방법](update-your-content.md)에서 API를 통해 AEM의 기존 Headless 콘텐츠를 업데이트하는 방법에 대해 알아보았습니다. 여기에서 알게 된 내용은 다음과 같습니다.

* AEM Assets HTTP API를 이해합니다.

## 목표 {#objective}

이 문서에서는 다음을 통해 AEM Headless 애플리케이션을 결합하는 방법을 이해하는 데 도움을 주고자 합니다.

* AEM Headless SDK 및 필요한 개발 도구에 대해 알아보기
* 실행하기 전에 콘텐츠를 시뮬레이션하기 위해 로컬 개발 런타임 설정
* AEM 콘텐츠 복제 기본 사항 이해

## AEM SDK {#the-aem-sdk}

AEM SDK를 사용하여 사용자 정의 코드를 빌드하고 배포합니다. 실행하기 전에 Headless 애플리케이션을 개발하고 테스트하기 위해 필요한 기본 도구입니다. 다음 아티팩트가 포함되어 있습니다.

* Quickstart jar - 작성자와 게시 인스턴스를 모두 설정하는 데 사용할 수 있는 실행 가능한 jar 파일
* Dispatcher 도구 - Windows 및 Unix® 기반 시스템에 대한 Dispatcher 모듈과 해당 종속성
* Java™ API Jar - AEM 개발에 사용할 수 있는 허용된 모든 Java™ API를 노출하는 Java™ Jar/Maven 종속성
* Javadoc jar - Java™ API jar용 javadoc

## AEM Headless SDK {#the-aem-headless-sdk}

AEM SDK와 달리 AEM **Headless SDK**&#x200B;는 라이브러리 세트입니다. 이를 사용하여 클라이언트는 HTTP를 통해 빠르고 쉽게 AEM Headless API와 상호 작용할 수 있습니다.

AEM Headless SDK에 대한 자세한 내용은 [설명서 여기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html)를 참조하십시오.

## 추가 개발 도구 {#additional-development-tools}

AEM SDK 외에도 로컬에서 코드와 콘텐츠를 간편하게 개발 및 테스트할 수 있는 추가 도구가 필요합니다.

* Java™
* Git
* Apache Maven
* Node.js 라이브러리
* 선택한 IDE

AEM은 Java™ 애플리케이션이므로 AEM as a Cloud Service 개발을 지원하려면 Java™ 및 Java™ SDK를 설치해야 합니다.

Git은 소스 제어를 관리하고 Cloud Manager의 변경 사항을 체크인한 다음 프로덕션 인스턴스에 배포하는 데 사용됩니다.

AEM은 Apache Maven을 사용하여 AEM Maven Project 원형에서 생성된 프로젝트를 빌드합니다. 모든 주요 IDE는 Maven에 대한 통합 지원을 제공합니다.

Node.js는 AEM 프로젝트의 `ui.frontend` 하위 프로젝트에 있는 프론트엔드 자산과 구동하는 데 사용되는 JavaScript 런타임 환경입니다. Node.js는 npm과 함께 배포되며, JavaScript 종속성을 관리하는 데 사용되는 실제 Node.js 패키지 관리자입니다.

## AEM 시스템의 구성 요소 개요 {#components-of-an-aem-system-at-a-glance}

다음으로 AEM 환경의 구성 부분을 살펴보겠습니다.

전체 AEM 환경은 작성자, 게시와 Dispatcher로 구성됩니다. 실행하기 전에 코드와 콘텐츠를 보다 쉽게 미리 볼 수 있도록 로컬 개발 런타임에 동일한 구성 요소가 제공됩니다.

* **Author 서비스**&#x200B;는 내부 사용자가 콘텐츠를 만들고 관리하고 미리 보는 곳입니다.

* **Publish 서비스** 는 “라이브” 환경으로 간주되며 일반적으로 최종 사용자는 이 서비스를 통해 상호 작용합니다. Author 서비스에서 편집 및 승인된 콘텐츠는 Publish 서비스로 배포됩니다. AEM Headless 애플리케이션의 가장 일반적인 배포 패턴은 애플리케이션의 프로덕션 버전을 AEM Publish 서비스에 연결하는 것입니다.

* **Dispatcher**&#x200B;는 AEM Dispatcher 모듈로 보강된 정적 웹 서버입니다. 게시 인스턴스에서 생성된 웹 페이지를 캐시하여 성능을 개선합니다.

## 로컬 개발 워크플로 {#the-local-development-workflow}

로컬 개발 프로젝트는 Apache Maven을 기반으로 빌드되어 소스 제어에 Git을 사용합니다. 프로젝트를 업데이트하려면 개발자는 Eclipse, Visual Studio Code 또는 IntelliJ 등 권장되는 통합 개발 환경을 사용할 수 있습니다.

Headless 애플리케이션에서 수집한 코드 또는 콘텐츠 업데이트를 테스트하려면 AEM 작성자 및 게시 서비스의 로컬 인스턴스가 포함된 로컬 AEM 런타임에 업데이트를 배포해야 합니다.

가장 중요한 위치에서 업데이트를 테스트해야 하므로 로컬 AEM 런타임에서 각 구성 요소의 차이를 메모해 두십시오. 예를 들어 작성자의 콘텐츠 업데이트를 테스트하거나 게시 인스턴스의 새 코드를 테스트합니다.

프로덕션 시스템에서 Dispatcher 및 http Apache 서버는 항상 AEM 게시 인스턴스 앞에 있습니다. 캐싱 및 보안 서비스를 AEM 시스템에 제공하므로 Dispatcher에 대한 코드 및 콘텐츠 업데이트를 테스트해야 합니다.

## 로컬 개발 환경을 사용하여 로컬에서 코드 및 콘텐츠 미리보기 {#previewing-your-code-and-content-locally-with-the-local-development-environment}

AEM Headless 프로젝트 실행을 준비하려면 프로젝트의 모든 구성 부분이 제대로 작동하는지 확인해야 합니다.

그러면 코드, 콘텐츠와 구성 등 모든 항목을 결합하고 로컬 개발 환경에서 테스트하여 실행 준비를 실시해야 합니다.

로컬 개발 환경은 세 가지 주요 영역으로 구성됩니다.

1. AEM Project - 이 프로젝트에는 AEM 개발자가 작업할 모든 사용자 정의 코드, 구성 및 콘텐츠가 포함됨
1. 로컬 AEM 런타임 - AEM 프로젝트에서 코드 배포에 사용되는 AEM 작성자 및 게시 서비스의 로컬 버전
1. 로컬 Dispatcher 런타임 - Dispatcher 모듈이 포함된 Apache htttpd 웹 서버의 로컬 버전

로컬 개발 환경이 설정되면 정적 노드 서버를 로컬로 배포하여 React 앱에 제공되는 콘텐츠를 시뮬레이션할 수 있습니다.

<!-- THIS TOPIC IS 404. IT DOES NOT APPEAR IN THE TOC OR ANYWHERE ELSE To get a more in-depth look at setting up a local development environment and all dependencies needed for content preview, see [Production Deployment documentation](https://experienceleague.adobe.com/docs/experience-manager-learn/headless-tutorial/graphql/multi-step/production-deployment.html). -->

## 다음 단계 {#whats-next}

AEM Headless 개발자 여정의 한 부분을 완료했으므로,

* AEM 개발 도구에 익숙해질 수 있습니다.
* 로컬 개발 워크플로를 이해할 수 있습니다.

AEM Headless 프로젝트를 실제로 실행할 수 있는 다음 문서인 [Headless 애플리케이션 실행 방법](/help/journey-headless/developer/go-live.md)을 검토하여 AEM Headless 여정을 계속하십시오.

## 추가 리소스 {#additional-resources}

* [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [로컬 AEM 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [클라이언트측 브라우저용 AEM Headless SDK (JavaScript)](https://github.com/adobe/aem-headless-client-js)
* [서버측/Node.js용 AEM Headless SDK (JavaScript)](https://github.com/adobe/aem-headless-client-nodejs)
* [Java™용 AEM Headless SDK](https://github.com/adobe/aem-headless-client-java)
* [AEM as a Headless CMS 소개](/help/headless/introduction.md)
* [AEM 개발자 포털](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [AEM의 Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
