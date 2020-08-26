---
title: 코드 리팩토링 툴을 위한 통합 경험
description: 코드 리팩토링 툴을 위한 통합 경험
translation-type: tm+mt
source-git-commit: df41244712e1792e5265e4e6c8104962899c9b26
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---


# 코드 리팩토링 툴을 위한 통합 경험 {#unified-experience}

코드 리팩토링용 통합 경험 툴은 AEM을 디스패처 파일, 코드 및 저장소에서 작동하는 Cloud Service 코드 리팩토링 툴로 실행하기 위한 경험을 제공합니다.

이 도구를 사용하면 설치, 설정 및 실행 측면에서 각기 다른 실행 요구 사항이 있기 때문에 코드 리팩토링 도구를 사용하는 복잡성이 줄어듭니다.

![이미지](/help/move-to-cloud-service/assets/unified-1.png)

## 이점 {#benefits}

코드 리팩토링 통합 경험 도구는 같은 위치에서 소스 코드에서 작동하는 모든 코드 리팩토링 도구를 호출하고 실행합니다.

다음과 같은 도구를 함께 사용할 수 있습니다.

* 소스 코드 마이그레이션에서 작동하는 모든 툴을 사용자로 통합하여 사용자에게 일관된 사용자 경험을 제공할 수 `node.js` `aio-cli plugin` 있습니다.

* 단일 명령을 통해 전체 마이그레이션을 수행하는 프로비저닝과 요구 사항에 따라 특정 도구를 유연하게 실행할 수 있습니다.

* 플러그인에 새 도구 추가와 같은 새로운 도구의 추가 작업을 간소화하려면 개발자를 위한 새로운 명령을 추가하고 사용자를 위한 간단한 플러그인 업데이트를 추가하면 되므로 더 많은 부가 가치를 제공하는 일관된 환경을 유지할 수 있습니다.

## 플러그인 이해 {#understanding-plugin}

고객 `aio-cli-plugin-aem-cloud-service-migration` 의 로컬 시스템에서 고객 코드, 저장소 구조 또는 구성을 재구성합니다. 이 페이지에서는 통합 경험에 대한 자세한 요구 사항과 디자인 결정을 캡처합니다.
커뮤니티에서 맞춤형 사용 사례를 확장할 수 있는 오픈 소스로 제공됩니다.

이 도구는 모든 코드 리팩토링 도구를 사용자에게 일관된 사용자 경험을 제공하기 위해 노출되는 하나의 node.js 응용 프로그램 `aio-cli plugin` 으로 통합합니다. 이 플러그인은 고객의 로컬 코드 베이스를 스캔하고 AEM을 Cloud Service 호환 코드, 구성 및 패키지로 만들어 Cloud Service 환경에 배포할 수 있습니다.

The plugin consists of two main parts:

* **사용자 인터페이스**

   `aio-cli` 명령을 사용하여 하나 이상의 마이그레이션 도구(순차적으로 실행할 도구 연결)`config.yaml` 실행

* **기본 마이그레이션 도구 세트**

   마이그레이션 도구는 다음을 통해 해당 기능을 실행합니다.

   * 고객 코드의 각 섹션을 스캔하고 모범 사례를 위해 코드 구현을 기반으로 마이그레이션을 수행하여 출력 결과를 생성하고 이를 검증하여 배포할 수 있습니다.

   * 요약 보고서를 만들기 위해 마이그레이션 중에 수행한 작업을 일관되게 기록합니다.

## 사용 가능 {#availability}

를 설치하고 사용할 수 `aio-cli-plugin-aem-cloud-service-migration` 있습니다 `aio-cli`.

>[!NOTE]
>현재 이 도구는 Dispatcher Converter에만 통합되어 있습니다.

Git 리소스 [를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) to learn about the usage and how you can contribute for this plugin code that is open sources in GitHub.

