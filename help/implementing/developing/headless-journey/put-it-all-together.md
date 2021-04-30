---
title: 모든 것을 하나로 통합하는 방법 - AEM 헤드리스에서 앱과 콘텐츠를
description: AEM 헤드리스 개발자 여정의 이 부분에서 컨텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션을 비롯한 AEM 프로젝트를 가져와 라이브할 수 있도록 준비하는 방법을 살펴봅니다.
hide: true
hidefromtoc: true
index: false
exl-id: 254fb9dd-36c8-43ce-aaea-ceb4d079503d
translation-type: tm+mt
source-git-commit: e8eb9d2c96d24601e50c48f6846a8c8bac8b0252
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# 모든 것을 통합하는 방법 - AEM 헤드리스 {#put-it-all-together}에서 앱과 콘텐츠를

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 이 부분에서는 ](overview.md) 컨텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션을 포함하여 AEM 프로젝트를 가져와 라이브되도록 준비하는 방법을 알아봅니다.

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서, [AEM Assets API를 통해 컨텐츠를 업데이트하는 방법](update-your-content.md) API를 통해 AEM에서 기존 헤드리스 컨텐츠를 업데이트하는 방법을 학습했고 이제 다음을 수행해야 합니다.

* AEM Assets HTTP API를 이해합니다.

이 문서는 이러한 기본 사항을 바탕으로 작성되므로 AEM 헤드리스 프로젝트를 라이브할 수 있도록 준비하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

* AEM의 로컬 개발 워크플로우란 무엇입니까?
* AEM SDK를 설치하여 컨텐츠를 테스트하는 데 사용할 수 있는 로컬 개발 런타임을
* 로컬 개발 런타임 외에 작업하는 데 필요한 개발 툴에 대해 알아봅니다.

## 로컬 개발 워크플로 {#the-local-development-workflow}

로컬 개발 프로젝트는 Apache Maven을 기반으로 구축되었으며 소스 제어에 Git을 사용합니다. 프로젝트를 업데이트하기 위해 개발자는 Eclipse, Visual Studio 코드 또는 IntelliJ와 같은 선호하는 통합 개발 환경을 다른 개발 환경에서 사용할 수 있습니다.

헤드리스 애플리케이션에서 인제스트할 코드 또는 컨텐츠 업데이트를 테스트하려면 AEM 작성자 및 게시 인스턴스의 로컬 인스턴스가 포함된 로컬 AEM 런타임에 업데이트를 배포해야 합니다.

업데이트 내용이 가장 중요한 위치(예: 작성자에서 컨텐츠 업데이트를 테스트하거나 게시 인스턴스에서 새 코드를 테스트하는 등)를 테스트해야 하므로 로컬 AEM 런타임의 각 구성 요소 간의 차이점을 확인하십시오.

프로덕션 시스템에서 디스패처와 http Apache 서버는 항상 AEM 게시 인스턴스 앞에 배치됩니다. AEM 시스템을 위한 캐싱 및 서비스 서비스를 제공하므로 디스패처에 대한 코드와 컨텐츠 업데이트를 테스트하는 것도 중요합니다.

모든 것이 테스트되고 제대로 작동하는지 확인한 다음 Cloud Manager의 중앙 Git 리포지토리로 코드 업데이트를 푸시할 수 있습니다.

업데이트를 Cloud Manager에 업로드한 후 Cloud Manager의 CI/CD 파이프라인을 사용하여 Cloud Service으로 AEM에 배포할 수 있습니다.


## AEM SDK {#the-aem-sdk}

AEM SDK는 사용자 지정 코드를 빌드하고 배포하는 데 사용됩니다. 여기에는 다음과 같은 가공물이 포함됩니다.

* 빠른 시작 jar - 작성자 및 게시 인스턴스를 모두 설정하는 데 사용할 수 있는 실행 jar 파일입니다
* Dispatcher 도구 - Windows 및 UNIX 기반 시스템에 대한 Dispatcher 모듈 및 해당 종속성
* Java API Jar - AEM에서 개발하는 데 사용할 수 있는 모든 허용되는 Java API를 표시하는 Java Jar/Maven 종속성
* Javadoc jar - Java API jar용 javadocs

## 로컬 개발 환경 설정 {#local-development-environment}

AEM 헤드가 없는 프로젝트를 시작할 수 있도록 준비하려면 프로젝트의 모든 구성 요소가 제대로 작동하는지 확인해야 합니다.

이를 위해서는 코드, 컨텐츠 및 구성 등 모든 작업을 통합하여 로컬 개발 환경에서 테스트하여 라이브할 수 있도록 해야 합니다.

로컬 개발 환경은 3개의 주요 영역으로 구성됩니다.

1. AEM 프로젝트 - AEM 개발자가 작업하려는 모든 사용자 정의 코드, 구성 및 컨텐츠를 포함합니다.
1. AEM 프로젝트에서 코드를 배포하는 데 사용되는 AEM 작성자 및 게시 서비스의 로컬 버전 로컬 AEM 런타임
1. Local Dispatcher 런타임 - Dispatcher 모듈을 포함하는 Apache httpd 웹 서버의 로컬 버전입니다.

## 개발 도구 {#development-tools}

AEM SDK 외에도 자신의 코드와 컨텐츠를 로컬에서 개발 및 테스트할 수 있는 추가 툴이 필요합니다.

* Java
* Git
* Apache Maven
* Node.js 라이브러리
* 원하는 IDE

AEM은 Java 애플리케이션이므로 Java 및 Java SDK를 설치하여 Cloud Service으로 AEM 개발을 지원해야 합니다.

Git은 소스 제어를 관리하고 Cloud Manager의 변경 사항을 체크 인한 다음 프로덕션 인스턴스에 배포하는 데 사용할 툴입니다.

AEM은 Apache Maven을 사용하여 AEM Maven Project 원형에서 생성된 프로젝트를 제작합니다. 모든 주요 IDE는 Maven에 대한 통합 지원을 제공합니다.

Node.js는 AEM 프로젝트의 ui.frontend 하위 프로젝트의 프런트 엔드 에셋을 사용하여 작업하는 데 사용되는 JavaScript 런타임 환경입니다. Node.js는 사실상의 Node.js 패키지 관리자로서 JavaScript 종속성을 관리하는 데 사용됩니다.

## 다음 {#what-is-next} 소개

AEM 헤드리스 프로젝트를 라이브로 촬영하는 [헤드리스 응용 프로그램을 사용하여 라이브하는 방법](go-live.md) 문서를 다시 검토하여 AEM 헤드리스 여정을 계속 진행해야 합니다!

## 추가 리소스 {#additional-resources}

* [로컬 개발 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-dispatcher-runtime)  - AEM용 개발을 시작하는 데 필요한 도구를 설치하는 방법을 알아봅니다.
* [AEM을 Cloud Service SDK로](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)  사용 - AEM SDK에 대해 자세히 살펴보십시오