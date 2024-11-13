---
title: 푸시 무효화 설정
description: 자체 프로덕션 CDN을 구축하기 위해 푸시 무효화를 구성하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: abd0fa0ea3e6e18187bcb60731ec6fe823a98e45
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 2%

---

# 푸시 무효화 설정

푸시 무효화를 사용하면 작성자가 게시한 콘텐츠 업데이트가 CDN(Managed Content Delivery Network)에서 자동으로 제거됩니다. 이렇게 하면 최신 콘텐츠만 제공됩니다.

시스템에서는 특정 URL과 캐시 태그 또는 키를 기준으로 콘텐츠를 지워 오래된 버전이 삭제되도록 합니다.

푸시 무효화를 활성화하려면 프로젝트의 구성 파일에 특정 속성을 추가해야 합니다. 예를 들어 SharePoint의 이름이 `.helix/config.xlsx`인 Microsoft Excel 통합 문서나 Google Drive의 이름이 `.helix/config`인 Google 시트 등이 있습니다.

다음 구성 속성은 프로덕션 호스트의 이름과 CDN 관리 유형을 정의합니다.

| key | 값 | 댓글 |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | 프로덕션 사이트의 호스트 이름입니다. 예: `www.example.com` |
| `cdn.prod.type` | 관리됨 |   |

구성 시트가 변경되면 사용자는 업데이트를 적용하려면 [Sidekick 도구](/help/edge/docs/sidekick.md)를 사용하여 미리 보고 활성화해야 합니다.

[Cloud Manager의 Edge Delivery 할 일 목록](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list)도 참조하세요.
