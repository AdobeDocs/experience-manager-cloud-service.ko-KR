---
title: 코드 리팩터링 도구를 위한 통합 경험
description: 코드 리팩터링 도구를 위한 통합 경험
exl-id: 856bce12-7d5e-4f8c-b252-7752bcbeebc4
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# 코드 리팩터링 도구에 대한 통합 경험 {#unified-experience}

Adobe는 AEM as a Cloud Service과 호환되어야 하는 코드 리팩터링 작업 중 일부를 자동화하는 도구를 개발했습니다. 다른 코드 리팩터링 도구의 설치 및 설정과 관련된 복잡성을 줄이기 위해 코드 및 리포지토리에서 작동하는 도구를 통합하는 플러그인을 개발했습니다.

## 이점 {#benefits}

통합 경험 플러그인은 다음과 같은 이점을 제공합니다.

* 소스 코드에서 작동하는 도구를 `aio-cli ` 플러그인으로 노출된 하나의 `node.js` 애플리케이션에 통합하여 사용자에게 일관된 사용자 경험을 제공합니다.

* 단일 명령을 통해 모든 도구를 실행할 수 있는 기능과 필요에 따라 특정 도구를 실행할 수 있는 유연성을 제공합니다.

* 경험을 일관되게 유지하면서 새로운 도구 추가를 간소화하는 확장성을 제공합니다.

## 플러그인 이해 {#understanding-plugin}

`aio-cli-plugin-aem-cloud-service-migration` 플러그인은 다음 두 가지 주요 부분으로 구성됩니다.

* **사용자 인터페이스**

   * `aio-cli` 하나 이상의 코드 리팩터링 도구를 실행하는 명령(순차적으로 실행할 도구 체인을 통해).
   * `config.yaml` 필요한 입력 매개 변수를 가져옵니다.

* **기본 코드 리팩터링 도구 세트**

   코드 리팩터링 도구는 다음을 통해 기능을 실행합니다.

   * 고객 코드의 각 섹션을 스캔하고 코드를 조작(우수 사례를 위해 코드 구현 기반)하여 유효성을 검사하고 배포할 수 있는 출력을 생성합니다.

   * 실행 중에 수행된 작업을 기록할 요약 보고서를 생성합니다.

## 사용 가능 {#availability}

[Git 리소스 를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 을 사용하여 GitHub에서 열려 있는 이 플러그인 코드에 대한 사용 및 참가 방법에 대해 알아봅니다.

>[!NOTE]
>현재 플러그인은 AEM Dispatcher Converter 및 Repository Modernizer와 통합되었습니다.
