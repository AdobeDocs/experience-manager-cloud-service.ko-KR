---
title: AEM 헤드리스에서 앱과 콘텐츠를 모두 통합하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 컨텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션을 비롯한 AEM 프로젝트를 가져와 라이브로 전환하는 방법을 알아봅니다.
exl-id: bece84ad-4c8c-410c-847e-9ef3f79970cb
source-git-commit: 421ad8506435e8538be9c83df0b78ad8f222df0c
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 9%

---

# AEM 헤드리스에서 앱과 콘텐츠를 모두 통합하는 방법 {#put-it-all-together}

의 이 부분에서 [AEM Headless Developer 여정](overview.md)을 사용하면 AEM 개발 도구 및 Headless SDK를 사용하여 애플리케이션을 통합하는 방법을 잘 알 수 있습니다.

## 지금까지의 이야기 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서, [AEM Assets API를 통해 콘텐츠를 업데이트하는 방법](update-your-content.md) API를 통해 AEM에서 기존 헤드리스 콘텐츠를 업데이트하는 방법을 배웠으며 이제 다음을 수행해야 합니다.

* AEM Assets HTTP API를 이해합니다.

## 목표 {#objective}

이 문서는 다음 방법으로 AEM 헤드리스 애플리케이션을 함께 배치하는 방법을 이해하는 데 도움이 되기 위한 것입니다.

* 필요한 AEM Headless SDK 및 개발 도구에 대해 알아보기
* 라이브로 전환하기 전에 컨텐츠를 시뮬레이션하도록 로컬 개발 런타임 설정
* AEM 컨텐츠 복제 기본 사항 이해

## AEM SDK {#the-aem-sdk}

AEM SDK는 사용자 지정 코드를 작성하고 배포하는 데 사용됩니다. 이 툴은 라이브로 전환하기 전에 헤드리스 애플리케이션을 개발하고 테스트하는 데 필요한 주요 도구입니다. 여기에는 다음 가공물이 포함됩니다.

* Quickstart jar - 작성자 및 게시 인스턴스를 모두 설정하는 데 사용할 수 있는 실행 가능한 jar 파일입니다
* Dispatcher 도구 - Dispatcher 모듈 및 Windows 및 UNIX® 기반 시스템에 대한 종속성
* Java™ API Jar - AEM에 대해 개발하는 데 사용할 수 있는 모든 허용된 Java™ API를 표시하는 Java™ Jar/Maven 종속성입니다
* Javadoc jar - Java™ API jar용 javadocs

## AEM Headless SDK {#the-aem-headless-sdk}

AEM SDK인 AEM과 다릅니다 **헤드리스 SDK** 는 HTTP를 통해 AEM Headless API와 빠르고 쉽게 상호 작용하는 데 클라이언트가 사용할 수 있는 라이브러리 세트입니다.

AEM Headless SDK에 대한 자세한 내용은 [여기에서 설명서 작성](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html).

## 추가 개발 도구 {#additional-development-tools}

AEM SDK 외에, 코드 및 컨텐츠를 로컬에서 개발 및 테스트할 수 있는 추가 도구가 필요합니다.

* Java™
* Git
* Apache Maven
* Node.js 라이브러리
* 원하는 IDE

AEM은 Java™ 애플리케이션이므로 AEM as a Cloud Service 개발을 지원하려면 Java™ 및 Java™ SDK를 설치해야 합니다.

Git은 소스 제어를 관리하고 Cloud Manager 변경 사항을 체크 인한 다음 프로덕션 인스턴스에 배포하는 데 사용하는 것입니다.

AEM은 Apache Maven을 사용하여 AEM Maven 프로젝트 원형을 통해 생성된 프로젝트를 빌드합니다. 모든 주요 IDE는 Maven에 대한 통합 지원을 제공합니다.

Node.js는 AEM 프로젝트의 프런트 엔드 자산에서 작업하는 데 사용되는 JavaScript 런타임 환경입니다 `ui.frontend` 하위 프로젝트. Node.js는 npm과 함께 배포되며, JavaScript 종속성을 관리하는 데 사용되는 사실상의 Node.js 패키지 관리자입니다.

## AEM 시스템의 구성 요소 개요 {#components-of-an-aem-system-at-a-glance}

다음으로, AEM 환경의 구성 부분을 살펴보겠습니다.

전체 AEM 환경은 작성자, 게시 및 Dispatcher로 구성됩니다. 이러한 동일한 구성 요소를 로컬 개발 런타임에서 사용할 수 있으므로 라이브로 전환되기 전에 코드 및 콘텐츠를 보다 쉽게 미리 볼 수 있습니다.

* **Author 서비스**&#x200B;는 내부 사용자가 콘텐츠를 만들고 관리하고 미리 보는 곳입니다.

* **Publish 서비스** 는 “라이브” 환경으로 간주되며 일반적으로 최종 사용자는 이 서비스를 통해 상호 작용합니다. Author 서비스에서 편집 및 승인된 콘텐츠는 Publish 서비스로 배포됩니다. AEM Headless 애플리케이션의 가장 일반적인 배포 패턴은 애플리케이션의 프로덕션 버전을 AEM Publish 서비스에 연결하는 것입니다.

* **디스패처** 는 AEM Dispatcher 모듈을 사용하여 증강된 정적 웹 서버입니다. 성능을 개선하기 위해 게시 인스턴스에서 생성한 웹 페이지를 캐시합니다.

## 로컬 개발 워크플로우 {#the-local-development-workflow}

로컬 개발 프로젝트는 Apache Maven을 기반으로 구축되었으며 소스 제어에 Git을 사용합니다. 프로젝트를 업데이트하기 위해 개발자는 Eclipse, Visual Studio Code 또는 IntelliJ와 같은 선호하는 통합 개발 환경을 사용할 수 있습니다.

헤드리스 애플리케이션에서 수집하는 코드 또는 컨텐츠 업데이트를 테스트하려면 AEM 작성자 및 게시 서비스의 로컬 인스턴스를 포함하는 로컬 AEM 런타임에 업데이트를 배포해야 합니다.

업데이트가 가장 중요한 위치를 테스트하는 것이 중요하므로 로컬 AEM 런타임에서 각 구성 요소 간의 차이점을 주의해야 합니다. 예를 들어, 작성자에서 컨텐츠 업데이트를 테스트하거나 게시 인스턴스에서 새 코드를 테스트합니다.

프로덕션 시스템에서는 Dispatcher와 http Apache 서버가 항상 AEM 게시 인스턴스 앞에 있습니다. AEM 시스템에 캐싱 및 보안 서비스를 제공하므로 Dispatcher에 대해 코드 및 콘텐츠 업데이트를 테스트하는 것이 가장 중요합니다.

## 로컬 개발 환경을 사용하여 로컬로 코드 및 컨텐츠 미리 보기 {#previewing-your-code-and-content-locally-with-the-local-development-environment}

AEM 헤드리스 프로젝트를 시작할 수 있도록 준비하려면 프로젝트의 모든 구성 부분이 제대로 작동하는지 확인해야 합니다.

이를 위해서는 모든 것을 통합해야 합니다. 실시간으로 준비하려면 로컬 개발 환경에서 코드, 컨텐츠 및 구성을 테스트하십시오.

로컬 개발 환경은 다음 세 가지 주요 영역으로 구성됩니다.

1. AEM 프로젝트 - 이 프로젝트에는 AEM 개발자가 작업하려는 모든 사용자 지정 코드, 구성 및 컨텐츠가 포함되어 있습니다
1. AEM 프로젝트에서 코드를 배포하는 데 사용되는 AEM 작성자 및 게시 서비스의 로컬 버전 로컬 AEM 런타임
1. Local Dispatcher 런타임 - Dispatcher 모듈을 포함하는 Apache httpd 웹 서버의 로컬 버전입니다.

로컬 개발 환경이 설정되면 정적 노드 서버를 로컬로 배포하여 React 앱에 대한 콘텐츠 서비스를 시뮬레이션할 수 있습니다.

<!-- THIS TOPIC IS 404. IT DOES NOT APPEAR IN THE TOC OR ANYWHERE ELSE To get a more in-depth look at setting up a local development environment and all dependencies needed for content preview, see [Production Deployment documentation](https://experienceleague.adobe.com/docs/experience-manager-learn/headless-tutorial/graphql/multi-step/production-deployment.html). -->

## 다음 단계 {#whats-next}

AEM Headless 개발자 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* AEM 개발 도구에 익숙해지십시오
* 로컬 개발 워크플로우 이해

다음 번에 문서를 검토하여 AEM 헤드리스 여정을 계속 진행합니다 [헤드리스 애플리케이션을 사용하여 라이브로 전환하는 방법](/help/journey-headless/developer/go-live.md) AEM Headless 프로젝트를 라이브로 전환하는 곳!

## 추가 리소스 {#additional-resources}

* [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [로컬 AEM 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [클라이언트측 브라우저용 AEM Headless SDK (JavaScript)](https://github.com/adobe/aem-headless-client-js)
* [server-side/Node.js용 AEM Headless SDK (JavaScript)](https://github.com/adobe/aem-headless-client-nodejs)
* [Java™용 AEM Headless SDK](https://github.com/adobe/aem-headless-client-java)

