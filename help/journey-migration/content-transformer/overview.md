---
title: 콘텐츠 변환기 개요
description: 콘텐츠 변환기를 사용하여 BPA에서 보고한 콘텐츠 관련 문제를 감지하고 해결하는 방법에 대해 알아봅니다.
exl-id: aa3397ff-3dd6-4c67-9064-cb9b19bf1c73
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 3%

---

# 개요 {#overview-ct}

CT(콘텐츠 변환기)는 Adobe에서 개발한 도구로, 현재 AEM 구현(온-프레미스 또는 Managed Services)에서 AEM as a Cloud Service으로 콘텐츠를 마이그레이션하기 전에 [BPA(모범 사례 분석기)](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)에서 보고한 콘텐츠 관련 문제를 자동으로 감지하고 해결하는 데 사용할 수 있습니다.

콘텐츠 변환기는 사용자가 이동 또는 삭제와 같은 대량 작업을 수행할 수 있도록 함으로써 다음 [BPA 패턴 범주](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html)(아래 표에 표시됨)에 해당하는 문제를 해결하는 데 도움이 될 수 있습니다. 이를 통해 마이그레이션 프로젝트에 소요되는 시간을 크게 줄이고 복잡성을 줄일 수 있습니다.

## 콘텐츠 변환기에서 다루는 패턴 범주 및 제안된 솔루션 {#pattern-categories-and-benefits}

| 패턴 코드 | 의심 유형/하위 유형 | 콘텐츠를 AEM as a Cloud Service으로 마이그레이션하기 전에 잠재적인 수정 사항 |
|--------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| ACV | missing.jcrcontent <br> missing.original.rendition <br> metadata.descendants.violation | 이러한 자산을 다른 위치로 이동하거나 삭제하여 AEM as a Cloud Service으로 마이그레이션되지 않도록 합니다. |
| CAV | content.area.violation | AEM as a Cloud Service으로 마이그레이션되지 않도록 일시적으로 경로를 `/etc/packages/content-transformation/paths`(으)로 이동하십시오. |
| DOPI | deprecated.ordered.index | 더 이상 사용되지 않는 색인을 제거합니다. |
| OAUI | non.migrated.oauth.users | 이러한 사용자를 제거하여 AEM as a Cloud Service으로 마이그레이션되지 않도록 하십시오. |
| PCX | page.complexity.medium <br> page.complexity.high | 페이지/하위 항목을 삭제하거나 다른 위치로 이동하여 AEM as a Cloud Service으로 마이그레이션되지 않도록 하십시오. |
| REP | forward.replication <br> reverse.replication <br> standard.replication.agent.modification <br> custom.replication.agent.detection | 생성된 복제 에이전트를 제거합니다. <br> 또는 <br> 수정/추가된 속성을 제거합니다. |
| URS | clientlibs.location <br> file.location <br> node.location <br> workflow.location | 마이그레이션 도중 문제가 발생하지 않도록 올바른 위치로 이동하십시오. |
| URS | node.size | 노드를 `/etc/packages/content-transformation/paths`(으)로 임시로 이동하여 AEM as a Cloud Service으로 마이그레이션되지 않도록 하십시오. |

## 콘텐츠 변환기에서 제공하는 이점 {#benefits}

콘텐츠 변환기는 다음과 같은 이점을 제공합니다.

* 실패 시 안전(Fail-Safe): 문제를 해결하기 위해 저장소를 수정할 때마다 콘텐츠 변환기에 의해 패키지가 생성됩니다. 필요한 경우 패키지를 설치하여 이전 상태로 되돌릴 수 있습니다.
* 사용하기 쉬움: 콘텐츠 변환기는 콘텐츠 전송 도구와 통합되었으며 직관적인 간단한 사용자 인터페이스가 제공됩니다.
* 시간 절약: 한 패턴 카테고리에 속하는 콘텐츠 문제가 많으면 콘텐츠 변환기를 사용하여 몇 번의 클릭으로 이 문제를 모두 해결할 수 있습니다.
