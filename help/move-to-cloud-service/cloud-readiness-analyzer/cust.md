---
title: 사용자 지정 검색됨
description: 사용자 지정 검색됨
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---


# 사용자 지정 검색됨 {#cust-pattern}

이 페이지에서는 사용자 지정 감지된 패턴 코드에 대해 설명합니다.

## 배경 {#background}

이 패턴 코드는 AEM 인스턴스에 대한 사용자 지정을 식별하는 데 사용됩니다. AEM의 사용자 지정이 일반적이기 때문에 이 패턴이 반드시 문제가 있음을 나타내는 것은 아닙니다. 업그레이드 플랜에 미치는 영향과 관련하여 평가할 수 있도록 사용자 지정 기록을 식별합니다.

감지된 사용자 지정에는 다음이 포함됩니다.

* 고객 코드(패키지) 및 구성
* 타사 패키지
* 타사 서비스와 통합
* 비표준 Oak 인덱스

## 패턴 데이터 {#pattern-data}

다음 개체는 패턴의 JSON 표현에 포함됩니다.

* **item.message**: 는 패턴의 메시지를 나타냅니다.
* **item.context**: 는 개요 정보에 대한 추가 정보를 나타냅니다.
   * *type*: customization.detected.
   * *데이터*: 사용자 지정을 설명하는 데이터가 포함된 JSON 개체

### 가능한 의미 및 위험 {#possible-implications}

해당되지 않습니다.

### 가능한 솔루션  {#possible-solutions}

해당되지 않습니다.
