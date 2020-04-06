---
title: AEM 시스템 개요
description: AEM 시스템 개요
translation-type: tm+mt
source-git-commit: aa6bb878ea4c58ba1e2fbf82d53effaa1a72d668

---


# AEM 시스템 개요 {#aem-system}

이 페이지에서는 AEM을 이전 AEM 버전보다 크게 향상된 아키텍처와 함께 새로운 기능을 제공하는 클라우드 서비스로 설명합니다. 이 새로운 아키텍처로 업그레이드하려면 상당한 노력이 필요합니다.

## 설명 {#background}

ACRA 메타 패턴은 AEM으로의 업그레이드와 관련된 여러 문제를 클라우드 서비스로 식별하는 데 사용됩니다. 패턴의 *참조* 및 &quot;referencedBy&quot; 값과 *컨텍스트* 객체를 조합하여 몇 가지 유형의 권고 정보를 지원합니다. 컨텍스트 *객체 내의* 유형 ** 값은 감지된 특정 문제를 결정합니다.

ACRA 패턴에 포함된 준비 문제는 권고 조치를 야기하는 비교적 적은 인스턴스가 있을 것으로 예상됩니다. AEM과 관련된 다른 준비 문제가 있습니다. 클라우드 서비스에는 주의가 필요한 많은 인스턴스가 있을 수 있으며 이러한 문제는 자체 패턴 코드가 제공됩니다. (UUI 및 URS를 참조하십시오.)

## 패턴 데이터 {#pattern-data}

다음 개체는 패턴의 JSON 표현에 포함됩니다.

* **item.message**:준비 문제 유형. (아래를 참조하십시오.)
* **데이터**:유형에 해당하는 데이터를 포함하는 JSON 개체입니다.

### 가능한 의미 및 위험 {#possible-implications}

미정

### 가능한 솔루션 {#possible-solutions}

미정
