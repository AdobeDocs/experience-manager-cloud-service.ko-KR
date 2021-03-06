---
title: Cloud Manager 테스트 개요
description: Cloud Manager가 사용자 지정 코드의 품질을 보장하기 위해 자동으로 실행하는 세 가지 유형의 테스트에 대한 개요를 살펴보십시오.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
source-git-commit: a9303c659730022b7417fc9082dedd26d7cbccca
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 5%

---


# Cloud Manager 테스트 개요 {#overview}

Cloud Manager에서 Cloud Services 파이프라인에 대해 지원하는 테스트에는 세 가지 카테고리가 있습니다.

1. [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)

   * 코드 품질 테스트는 애플리케이션 코드의 품질을 평가합니다.
   * 코드 품질 파이프라인은 모든 비프로덕션 및 프로덕션 파이프라인의 빌드 단계 바로 다음에 실행됩니다.
   * 다음 [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md) cloud Manager에서 실행되는 는 AEM Engineering의 우수 사례를 기반으로 만들어집니다.

1. [기능 테스트](/help/implementing/cloud-manager/functional-testing.md)

   * 기능 테스트는 프로덕션 파이프라인의 단계 테스트 단계의 일부입니다.

1. [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md)

   * Experience Audit 테스트는 모든 Cloud Manager 프로덕션 파이프라인에서 활성화되므로 건너뛸 수 없습니다.

이러한 테스트는 수행할 수 있습니다.

* 고객 서면
* Adobe
* 오픈 소스 도구를 사용하여 생성

>[!NOTE]
>
> 고객이 작성한 테스트와 Adobe 작성 테스트 모두 이러한 테스트를 실행하기 위해 설계된 컨테이너화된 인프라에서 실행됩니다.
