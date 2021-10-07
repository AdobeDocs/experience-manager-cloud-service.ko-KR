---
title: AEM 노드 유형
description: AEM은 Sling을 기반으로 하며 두 가지 모두에서 제공하는 노드 유형으로 JCR 저장소를 사용하지만 AEM에서는 고유한 노드 유형 범위를 제공합니다.
exl-id: 82cc28ca-37e2-4ca3-b3e4-cc03bbc5bdf5
source-git-commit: 08559417c8047c592f2db54321afe68836b75bd1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# AEM 노드 유형 {#aem-node-types}

AEM은 Sling을 기반으로 하며 JCR 저장소를 사용하므로 이 두 표준에서 제공하는 노드 유형은 AEM에서 사용할 수 있습니다.

* [JCR 노드 유형](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling 노드 유형](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

여기에 더요 AEM에서는 다양한 사용자 지정 노드 유형을 제공합니다. 모든 연결된 속성이 있는 최신 목록의 경우 [CRXDE](/help/implementing/developing/tools/crxde.md)을 사용하여 AEM 저장소에서 다음 경로를 찾아봅니다.

`/jcr:system/jcr:nodeTypes`
