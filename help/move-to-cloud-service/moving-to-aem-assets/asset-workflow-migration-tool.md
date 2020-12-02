---
title: 자산 워크플로우 마이그레이션 도구
description: '자산 워크플로우 마이그레이션 도구 '
translation-type: tm+mt
source-git-commit: 3a438de3c460d4dc5a8b8617f0ec0eefc56f1665
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 46%

---


# 자산 워크플로우 마이그레이션 도구 {#asset-workflow-migration}

자산 워크플로우 마이그레이션 도구는 AEM의 온프레미스 또는 AMS 배포에서 자산 처리 워크플로우를 AEM Assets as a Cloud Service에 사용할 프로필 및 OSGi 구성 처리로 자동 마이그레이션하는 데 사용됩니다.

## 소개 {#introduction}

이 섹션에서는 자산 워크플로우 마이그레이션 도구에 대한 리소스 및 구현 세부 사항을 설명합니다.

이 유틸리티를 사용하면 AEM 개발자가 기존 AEM Asset 처리 워크플로우를 AEM as a Cloud Service에 마이그레이션할 수 있습니다.

## 지원되는 워크플로 {#migration-support-for-workflows}

워크플로우는 다양한 수준의 마이그레이션 지원을 제공합니다. 이 [특정 워크플로 목록](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties)을 참조하십시오. 워크플로우는 제공된 지원을 기반으로 다음 카테고리로 분류됩니다. Adobe은 `SUPPORTED`, `REQUIRED` 또는 `OPTIONAL` 범주에 나열된 워크플로우의 마이그레이션을 지원합니다. 다른 카테고리에 언급된 워크플로우 단계는 지원되지 않습니다.

* `SUPPORTED`:Cloud Service [!DNL Experience Manager Assets] 로 지원되는 기능입니다.
* `OPTIONAL`:Cloud Service [!DNL Experience Manager Assets] 의 옵션 기능입니다.
* `REQUIRED`:워크플로우에 추가되는 필수 단계입니다.
* `UNNECESSARY`:기능은 Cloud Service [!DNL Experience Manager Assets] 로 필요하지 않습니다.
* `NUI_OOTB`:asset compute 서비스에서 제공하는  [기능입니다](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`:기본 커넥터에서 제공하는  [!DNL Dynamic Media] 기능입니다.
* `NUI_MIGRATED`:asset compute 서비스의  [처리 프로필로 마이그레이션되었습니다](/help/assets/asset-microservices-configure-and-use.md).
* `UNSUPPORTED`:현재 Cloud Service [!DNL Experience Manager Assets] 로 지원되지 않습니다.

## 자산 워크플로우 마이그레이션 도구 설치 {#installing-tool}

**[Git 리소스: AEM Assets as a Cloud Service - 워크플로우 마이그레이션](https://github.com/adobe/aem-cloud-migration)**&#x200B;을 참조하여 소스에서 코드 설치 및 빌드에 대해 알아보십시오.
