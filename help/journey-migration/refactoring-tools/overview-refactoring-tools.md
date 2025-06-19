---
title: 리팩토링 도구 개요
description: AEM 리팩터링 도구 시작 방법 알아보기
exl-id: b8137e01-87e8-4298-b0cc-b376330cb730
source-git-commit: 879f4f3476ee369554188d6e3b7973d32454ed4b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---

<!-- Alexandru: temporarily commeting this out, since it breaks validation

>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Overview"
>abstract="Refactoring Tools is a solution developed by Adobe to help refactor existing AEM projects for compatibility with AEM as a Cloud Service. The tools are executed via Cloud Acceleration Manager (CAM) and automate key modernization tasks."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=ko" text="Guidelines and Best Practices"

-->

# 리팩토링 도구 개요 {#refactoring-tools-overview}

**리팩터링 도구** 기존 AEM 프로젝트를 **AEM as a Cloud Service(AEMaaCS)**&#x200B;와(과) 호환되도록 업데이트하는 프로세스를 간소화합니다. 이러한 도구는 일반적인 리팩터링 및 현대화 작업을 자동화하고 원활한 경험을 위해 **CAM(Cloud Acceleration Manager)**&#x200B;과(와) 통합됩니다.

이전에는 CLI 유틸리티로만 제공되었던 리팩터링 툴은 이제 자동화된 검사, 구성 생성 및 작업 실행과 같은 기능이 포함된 통합 인터페이스를 제공하여 수동 오버헤드를 줄이고 가시성을 향상시킵니다.

## 검사 워크플로우 {#inspection-workflow}

**검사 워크플로우**&#x200B;를 사용하면 리팩터링 도구 실행을 위한 준비 프로세스가 간소화됩니다.

### 주요 기능:

* **자동 트리거** - 프로젝트를 업로드하면 자동으로 검사가 시작됩니다.
* **구성 생성** - 도구는 업로드된 소스 코드를 검사하고 필요한 구성을 생성합니다.
* **페이로드 제출** - 이러한 구성은 실행을 위해 선택한 도구에 직접 전달됩니다.

## 사용 가능한 리팩터링 도구

### 저장소 현대화 도구 {#repo-modernizer}

**Repository Modernizer**&#x200B;는 AEMaaCS 표준 및 모범 사례에 맞게 AEM 프로젝트의 저장소 레이아웃 및 콘텐츠를 재구성합니다. 이 제품은 기존의 저장소 현대화 도구를 향상된 자동화 및 정확도로 대체합니다.

### 코드 변형자 {#code-transformer}

**코드 변환기**&#x200B;는 지능형 패턴 인식 및 AI 기반 분석을 사용하여 AEMaaCS와 호환되지 않는 코드 세그먼트를 감지하고 업데이트합니다. 이 도구는 마이그레이션 작업을 단순화하고 수동 코드 변경 사항을 줄입니다.

## 리팩터링 워크플로 단계 {#phases-in-refactoring-tools}

리팩터링 도구는 구조화된 2단계 프로세스를 따릅니다.

### 1단계: Source 코드 업로드

* CAM 인터페이스를 사용하여 소스 코드(ZIP 형식)를 업로드합니다.
* 업로드되면 **검사 워크플로**&#x200B;가 자동으로 트리거되어 프로젝트를 분석하고 도구 실행을 준비합니다.

>[!NOTE]
>검사 과정에서 다른 프로젝트 업로드는 허용되지 않습니다.

### 2단계: 리팩터링 작업 트리거

검사가 완료되면 하나 이상의 리팩터링 도구를 실행할 수 있습니다.

* **Repository Modernizer 실행** - 리포지토리 현대화 작업을 실행합니다.
* **코드 변환기 실행** - 검사 결과를 기준으로 코드 변환을 실행합니다.
* **모든 도구를 함께 실행** - 사용 가능한 모든 도구를 한 번의 작업으로 실행합니다.

>[!NOTE]
>리팩터링 작업은 소스 코드를 성공적으로 업로드하고 검사한 후에만 시작할 수 있습니다.

>[!NOTE]
>사용자는 여러 리팩터링 작업을 동시에 트리거할 수 있지만 각 작업은 개별적으로 실행됩니다.
