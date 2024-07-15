---
title: AEM 노드 유형
description: AEM은 Sling을 기반으로 하며 두 가지 모두에서 제공하는 노드 유형이 있는 JCR 저장소를 사용하지만 AEM은 다양한 자체 노드 유형을 제공합니다.
exl-id: 82cc28ca-37e2-4ca3-b3e4-cc03bbc5bdf5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 6%

---

# AEM 노드 유형 {#aem-node-types}

AEM은 Sling을 기반으로 하며 JCR 저장소를 사용하므로 다음 두 표준에서 제공하는 노드 유형을 AEM에서 사용할 수 있습니다.

* [JCR 노드 유형](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling 노드 유형](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

이 외에도. AEM은 다양한 사용자 지정 노드 유형을 제공합니다. 연결된 모든 속성이 있는 최신 목록을 보려면 [CRXDE를 사용](/help/implementing/developing/tools/crxde.md)하여 AEM 저장소에서 다음 경로를 찾아보십시오.

`/jcr:system/jcr:nodeTypes`
