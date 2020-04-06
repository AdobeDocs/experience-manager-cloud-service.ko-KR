---
title: AEM 시스템 개요
description: AEM 시스템 개요
translation-type: tm+mt
source-git-commit: aa6bb878ea4c58ba1e2fbf82d53effaa1a72d668

---


# AEM 시스템 개요 {#aem-system}

이 페이지에서는 Adobe Experience Manager(AEM) 시스템 개요를 설명합니다.

## 배경 {#background}

이 패턴은 AEM 시스템의 개요를 제공하는 일반 정보를 식별하는 데 사용됩니다. 정보에는 다음과 같은 항목이 포함될 수 있습니다.

AEM 버전 사용된 AEM 제품(사이트, 자산, 양식 등)노드 수(페이지, 자산 등)

## 패턴 데이터 {#pattern-data}

다음 개체는 패턴의 JSON 표현에 포함됩니다.

* **item.message**:는 패턴의 메시지를 나타냅니다.
* **item.context**:개요 정보에 대한 추가 정보를 참조하십시오.
   * *유형*:컨텍스트 데이터의 유형(&quot;aem.version&quot;, &quot;aem.product&quot; 또는 &quot;node.count&quot;입니다.
   * *데이터*:다음 유형에 해당하는 데이터를 포함하는 JSON 개체:&quot;version&quot;(문자열), &quot;product&quot;(문자열) 또는 &quot;count&quot;(정수)

### 가능한 의미 및 위험 {#possible-implications}

해당 없음.

### 가능한 솔루션 {#possible-solutions}

해당 없음.
