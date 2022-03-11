---
title: 자산 워크플로우 마이그레이션 도구
description: 자산 워크플로우 마이그레이션 도구
exl-id: a95caf5e-e6b2-463f-bebd-b791104fd25c
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 29%

---

# 자산 워크플로우 마이그레이션 도구 {#asset-workflow-migration}

자산 워크플로우 마이그레이션 도구는 AEM의 온프레미스 또는 AMS 배포에서 자산 처리 워크플로우를 AEM Assets as a Cloud Service에 사용할 프로필 및 OSGi 구성 처리로 자동 마이그레이션하는 데 사용됩니다.

## 소개 {#introduction}

이 섹션에서는 자산 워크플로우 마이그레이션 도구에 대한 리소스 및 구현 세부 사항을 설명합니다.

이 유틸리티를 사용하면 AEM 개발자가 기존 AEM Asset 처리 워크플로우를 AEM as a Cloud Service에 마이그레이션할 수 있습니다.

## 지원되는 워크플로우 {#migration-support-for-workflows}

워크플로우는 다양한 수준의 마이그레이션 지원을 제공합니다. 다음 보기 [특정 워크플로우 목록](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). 워크플로우는 제공된 지원을 기반으로 다음 카테고리로 분류됩니다. Adobe은 다음에 나열된 워크플로우의 마이그레이션을 지원합니다 `SUPPORTED`, `REQUIRED`, 또는 `OPTIONAL` 카테고리. 다른 카테고리에 언급된 워크플로우 단계는 지원되지 않습니다.

* `SUPPORTED`: 에서 지원되는 기능 [!DNL Experience Manager Assets] as a Cloud Service.
* `OPTIONAL`: 의 선택적 기능 [!DNL Experience Manager Assets] as a Cloud Service.
* `REQUIRED`: 워크플로우에 추가된 필수 단계입니다.
* `UNNECESSARY`: 기능은에서 필요하지 않습니다 [!DNL Experience Manager Assets] as a Cloud Service.
* `NUI_OOTB`: 에서 제공하는 기능 [asset compute 서비스](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: 기본적으로 제공되는 기능 [!DNL Dynamic Media] 커넥터.
* `NUI_MIGRATED`: 마이그레이션됨 [asset compute 서비스의 처리 프로필](/help/assets/asset-microservices-configure-and-use.md).
* `UNSUPPORTED`: 현재에서 지원되지 않음 [!DNL Experience Manager Assets] as a Cloud Service.

## 자산 워크플로우 마이그레이션 도구 사용 {#use-workflow-migrator}

* **[!DNL Adobe I/O]CLI**: Adobe은 를 통해 자산 워크플로우 마이그레이션 도구를 사용하는 것을 권장합니다. `aio-cli-plugin-aem-cloud-service-migration` ([!DNL Experience Manager] 로서의 [!DNL Cloud Service] 코드 리팩터링 플러그인 [!DNL Adobe I/O] CLI). 플러그인을 설치하고 사용하는 방법에 대해 알아보려면 [Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction).

* **독립형 유틸리티**: 자산 워크플로우 마이그레이션 도구는 독립형 유틸리티로 실행할 수도 있습니다. 소스에서 코드 설치 및 빌드에 대한 자세한 내용은 [Git 리소스: [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] - 워크플로우 마이그레이션](https://github.com/adobe/aem-cloud-migration).
