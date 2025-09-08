---
title: Edge Delivery 사이트에 대한 푸시 무효화 설정
description: Edge Delivery 사이트에 대한 푸시 무효화를 구성하여 효율적으로 콘텐츠를 업데이트하고 캐싱을 제어하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: ht
source-wordcount: '173'
ht-degree: 100%

---

# 푸시 무효화 설정

푸시 무효화를 설정하면 작성자가 수행한 콘텐츠 업데이트가 게시될 때 관리 콘텐츠 전송 네트워크(CDN)에서 자동으로 제거해야 합니다. 이렇게 해야 최신 콘텐츠만 제공됩니다.

시스템에서 특정 URL 및 캐시 태그 또는 키에 따라 콘텐츠가 지워지면 이전 버전을 제거할 수 있습니다.

푸시 무효화를 활성화하려면 특정 속성을 프로젝트의 구성 파일에 추가해야 합니다. 예: SharePoint에서는 `.helix/config.xlsx`의 이름이 Microsoft Excel 통합 문서이고 Google 드라이브에서는 `.helix/config`의 이름이 Google 시트입니다.

다음 구성 속성은 프로덕션 호스트 이름과 CDN 관리 유형을 정의합니다.

| 키 | 값 | 댓글 |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | 프로덕션 사이트의 호스트 이름입니다. 예: `www.example.com` |
| `cdn.prod.type` | 관리됨 |   |

구성 시트가 변경되면 사용자는 [사이드 킥 도구](https://www.aem.live/docs/sidekick)를 사용하여 변경 사항을 미리 보고 활성화한 다음 업데이트를 적용해야 합니다.

[Cloud Manager에서의 Edge Delivery 할 일 목록 정보](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list)도 참조하십시오.
