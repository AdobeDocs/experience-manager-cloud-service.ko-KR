---
title: AEM 노드 유형
description: AEM은 Sling을 기반으로 하며 두 가지 모두에서 제공하는 노드 유형이 있는 JCR 저장소를 사용하지만 AEM은 고유한 노드 유형 범위도 제공합니다.
translation-type: tm+mt
source-git-commit: 020cebfa714c098f032df963b7105503c741e748
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# AEM 노드 유형 {#aem-node-types}

AEM은 Sling을 기반으로 하며 JCR 저장소를 사용하기 때문에 이러한 두 가지 표준을 통해 제공되는 노드 유형을 AEM에서 사용할 수 있습니다.

* [JCR 노드 유형](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling 노드 유형](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

여기에 더요 AEM은 사용자 지정 노드 유형 범위를 제공합니다. 모든 관련 속성이 있는 최신 목록의 경우 [CRXDE](/help/implementing/developing/tools/crxde.md)를 사용하여 AEM 저장소의 다음 경로를 찾아봅니다.

`/jcr:system/jcr:nodeTypes`
