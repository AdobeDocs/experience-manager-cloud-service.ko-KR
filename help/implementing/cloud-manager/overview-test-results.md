---
title: Cloud Manager 테스트 개요
description: Cloud Manager가 사용자 정의 코드의 품질을 보장하기 위해 자동으로 실행하는 세 가지 테스트 유형에 대한 개요를 확인합니다.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 91%

---


# Cloud Manager 테스트 개요 {#overview}

Cloud Manager for Cloud Services 파이프라인에서 지원하는 테스트에는 세 가지 범주가 있습니다.

1. [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)

   * 코드 품질 테스트는 애플리케이션 코드의 품질을 평가합니다.
   * 코드 품질 파이프라인은 모든 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 직후에 실행됩니다.
   * Cloud Manager에서 실행하는 [사용자 정의 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md)은 AEM Engineering의 모범 사례를 기반으로 생성됩니다.

1. [기능 테스트](/help/implementing/cloud-manager/functional-testing.md)

   * 기능 테스트는 [프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)의 단계 테스트 단계의 일부이며, 선택적으로 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) 테스트 단계의 일부입니다.

1. [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md)

   * 경험 감사 테스트는 모든 Cloud Manager 프로덕션 파이프라인에서 활성화되며 건너뛸 수 없습니다.

이러한 테스트는 다음과 같이 작성할 수 있습니다.

* 고객 작성
* Adobe 작성
* 오픈 소스 도구로 작성

>[!NOTE]
>
> 고객 작성 테스트와 Adobe 작성 테스트는 모두 이러한 테스트를 실행하도록 설계된 컨테이너화된 인프라에서 실행됩니다.
