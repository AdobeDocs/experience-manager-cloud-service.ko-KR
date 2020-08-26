---
title: 코드 리팩토링 툴을 위한 통합 경험
description: 코드 리팩토링 툴을 위한 통합 경험
translation-type: tm+mt
source-git-commit: 03434343829e1a1fb95256a607619b55626c6afc
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 1%

---


# 코드 리팩토링 툴을 위한 통합 경험 {#unified-experience}

AEM과 Cloud Service으로 호환하는 데 필요한 코드 리팩토링 작업을 자동화하는 툴을 개발했습니다. 다양한 코드 리팩토링 툴의 설치 및 설정과 관련된 복잡성을 줄이기 위해 코드 및 리포지토리에서 작동하는 도구를 통합하는 플러그인을 개발했습니다.

## 이점 {#benefits}

Unified Experience 플러그인은 다음과 같은 이점을 제공합니다.

* 소스 코드에서 작동하는 툴을 플러그인으로 노출된 하나의 `node.js` 애플리케이션에 통합하여 사용자에게 일관된 사용자 경험을 `aio-cli ` 제공합니다.

* 단일 명령을 통해 모든 툴을 실행할 수 있는 기능과 필요한 경우 특정 툴을 유연하게 실행할 수 있는 기능을 제공합니다.

* 경험을 일관되게 유지하면서 새로운 도구 추가를 단순화하는 확장성을 제공합니다.

## 플러그인 이해 {#understanding-plugin}

The plugin consists of two main parts: `aio-cli-plugin-aem-cloud-service-migration`

* **사용자 인터페이스**

   * `aio-cli` 명령을 사용하여 하나 이상의 코드 리팩토링 도구 실행(순차적으로 실행할 도구 연결 사용)
   * `config.yaml` 필요한 입력 매개 변수를 사용하는 방법

* **기본 코드 리팩토링 도구 세트**

   코드 리팩토링 도구는 다음을 통해 해당 기능을 실행합니다.

   * 고객 코드의 각 섹션을 스캔하고 코드(우수 사례를 위한 코드 구현 기준)를 조작하여 출력 결과를 확인하고 배포할 수 있습니다.

   * 실행 중에 수행된 작업을 기록하는 요약 보고서 작성.

## 사용 가능 {#availability}

Git 리소스 [를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) to learn about the usage and how you can contribute for this plugin code that is open sources in GitHub.

>[!NOTE]
>현재 Dispatcher Converter만 플러그인과 통합되었습니다.
