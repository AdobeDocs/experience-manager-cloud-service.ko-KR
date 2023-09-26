---
title: 코드 리팩터링 도구에 대한 통합 경험
description: 코드 리팩터링 도구에 대한 통합 경험에 대해 알아봅니다.
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 1%

---

# 코드 리팩터링 도구에 대한 통합 경험 {#unified-experience}

Adobe은 Adobe Experience Manager(AEM) as a Cloud Service과 호환하는 데 필요한 일부 코드 리팩터링 작업을 자동화하는 도구를 개발했습니다. 다양한 코드 리팩터링 도구의 설치 및 설정과 관련된 복잡성을 줄이기 위해, Adobe은 코드 및 저장소에서 작동하는 도구를 통합하는 플러그인을 개발했습니다.

## 이점 {#benefits}

통합 경험 플러그인은 다음과 같은 이점을 제공합니다.

* 소스 코드에서 작동하는 도구를 하나로 통합 `node.js` 다음으로 노출된 애플리케이션 `aio-cli ` 사용자에게 일관된 사용자 경험을 제공하는 플러그인입니다.

* 단일 명령을 통해 모든 도구를 실행하는 동시에 필요에 따라 특정 도구를 실행할 수 있는 유연성을 제공합니다.

* 새로운 툴을 간편하게 추가할 수 있을 뿐만 아니라 일관된 환경을 유지할 수 있습니다.

## 플러그인 이해 {#understanding-plugin}

다음 `aio-cli-plugin-aem-cloud-service-migration` 플러그인은 다음 두 가지 주요 부분으로 구성됩니다.

* **사용자 인터페이스**

   * `aio-cli` 하나 이상의 코드 리팩터링 도구를 실행하는 명령(순차적으로 실행될 도구를 체인으로 연결).
   * `config.yaml` 필수 입력 매개 변수를 사용합니다.

* **기본 코드 리팩터링 도구 세트**

  코드 리팩터링 도구는 다음과 같은 방법으로 기능을 실행합니다.

   * 고객 코드의 각 섹션을 스캔하고 모범 사례에 대한 코드 구현을 기반으로 코드를 조작하여 확인 및 배포할 수 있는 출력을 생성합니다.

   * 실행 중에 수행된 작업을 기록하는 요약 보고서 만들기

## 사용 가능 {#availability}

다음을 참조하십시오 [Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 사용 및 GitHub에서 오픈 소스로 제공되는 이 플러그인 코드에 기여할 수 있는 방법에 대해 알아볼 수 있습니다.

>[!NOTE]
>현재 플러그인은 AEM Dispatcher Converter 및 Repository Modernizer와 통합됩니다.
