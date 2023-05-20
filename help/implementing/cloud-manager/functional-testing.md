---
title: 기능 테스트
description: 코드의 품질과 신뢰성을 보장하기 위해 AEM as a Cloud Service 배포 프로세스에 내장된 세 가지 유형의 기능 테스트에 대해 알아봅니다.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 7d15440159a8e24314753acd5b37fcd2c5e8ec4c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---


# 기능 테스트 {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="기능 테스트"
>abstract="코드의 품질과 신뢰성을 보장하기 위해 AEM as a Cloud Service 배포 프로세스에 내장된 세 가지 유형의 기능 테스트에 대해 알아봅니다."

코드의 품질과 신뢰성을 보장하기 위해 [AEM as a Cloud Service 배포 프로세스](/help/implementing/cloud-manager/deploy-code.md)에 내장된 세 가지 유형의 기능 테스트에 대해 알아봅니다.

## 범위

Cloud Manager 파이프라인의 기능 테스트 단계의 목적은 애플리케이션의 필수 기능이 예상대로 작동하는지 확인하는 것입니다.

이 테스트 단계는 코드를 프로덕션에 배포하기 전에 자동화된 테스트의 마지막 단계입니다.

기능 테스트는 Cloud Manager의 파이프라인 실행 외부에서 수행되는 유닛 테스트, 통합 테스트 또는 기능 테스트와 같은 다른 테스트 전략을 대체하는 것이 아니라 보완하고 확장해야 합니다.

## 개요 {#overview}

AEM as a Cloud Service의 기능 테스트에는 세 가지 유형이 있습니다.

* [제품 기능 테스트](#product-functional-testing)
* [사용자 정의 기능 테스트](#custom-functional-testing)
* [사용자 정의 UI 테스트](#custom-ui-testing)

모든 기능 테스트의 경우 [배포 프로세스](/help/implementing/cloud-manager/deploy-code.md)의 일부로 빌드 개요 화면에서 **빌드 로그 다운로드** 버튼을 사용하여 자세한 테스트 결과를 `.zip` 파일로 다운로드할 수 있습니다.

이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 이러한 로그에 액세스하는 방법에 대한 자세한 내용은 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 문서를 참조하십시오.

제품 기능 테스트와 샘플 사용자 정의 기능 테스트는 모두 [AEM 테스트 클라이언트](https://github.com/adobe/aem-testing-clients)를 기반으로 합니다.

### 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 작성 및 복제 작업과 같은 AEM의 핵심 기능에 대한 안정적인 HTTP 통합 테스트(IT) 세트입니다. 이러한 테스트는 Adobe에서 유지 관리하며 핵심 기능이 손상된 경우 사용자 정의 애플리케이션 코드에 대한 변경 사항이 배포되는 것을 방지하기 위함이 목적입니다.

* [프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md): 제품 기능 테스트는 새 코드를 Cloud Manager에 배포할 때마다 자동으로 실행되며 건너뛸 수 없습니다.
* [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md): 비프로덕션 파이프라인을 실행할 때마다 실행되도록 제품 기능 테스트를 선택적으로 선택할 수 있습니다.

제품 기능 테스트는 오픈 소스 프로젝트로 유지 관리됩니다. 자세한 내용은 GitHub의 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) 문서를 참조하십시오.

### 사용자 정의 기능 테스트 {#custom-functional-testing}

제품 기능 테스트는 Adobe에 의해 정의되지만 자체 애플리케이션에 대한 자체 품질 테스트를 작성할 수 있습니다. 이는 애플리케이션 품질을 보장하기 위해 [프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)의 일부이거나 선택적으로 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)의 일부인 사용자 정의 기능 테스트로 실행됩니다.

사용자 정의 기능 테스트는 사용자 정의 코드 배포와 푸시 업그레이드 모두에 대해 실행되므로 AEM 코드 변경으로 인해 애플리케이션 코드가 손상되지 않도록 우수한 기능 테스트를 작성하는 것이 특히 중요합니다. 사용자 정의 기능 테스트 단계는 항상 존재하며 건너뛸 수 없습니다.

자세한 내용은 [Java 기능 테스트](/help/implementing/cloud-manager/java-functional-testing.md)를 참조하십시오.


### 사용자 정의 UI 테스트 {#custom-ui-testing}

사용자 정의 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io 또는 Selenium을 기반으로 빌드된 기타 프레임워크와 기술 등의 언어 및 프레임워크에서 다양한 선택을 허용하도록 도커 이미지에 패키징된 Selenium 기반 테스트입니다.

자세한 내용은 [사용자 정의 UI 테스트](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing)를 참조하십시오.

