---
title: Universal Editor 2026.05.07 릴리스 노트
description: 다음은 범용 편집기 2026.05.07 릴리스의 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 4f66cd6048d7a78bea33c0f9c21017983b9032d5
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 12%

---


# Universal Editor 2026.05.07 릴리스 노트 {#release-notes}

유니버설 편집기의 2026년 5월 7일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>릴리스하기 전에 **예정된** 범용 편집기 기능을 테스트하려면 [범용 편집기 미리보기 릴리스 정보](/help/release-notes/universal-editor/preview.md)를 참조하십시오.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* 이제 [구성 요소를 편집기에서 드래그 앤 드롭하여 이동할 수 있습니다.](/help/sites-cloud/authoring/universal-editor/authoring.md#drag-and-drop-move)
* 범용 편집기 UI와 백엔드 시스템 간의 지연 시간을 줄이기 위해 서비스 작업자가 도입되었습니다.
* 이제 콘텐츠 조각(AEM 6.5, OpenAPI 및 GraphQL)의 모든 어댑터에 자산 선택기의 필터가 포함되어 일관성을 보장하고 사용자가 허용된 자산만 선택할 수 있습니다.
* 이제 `content:patch` 의도가 제공됩니다.
* 접근성을 돕기 위해 작성자 흐름 및 랜드마크가 정의되었습니다.

## 기타 향후 개선 사항 {#other-improvements}

* `assignImageDimensionFields`에서 불필요한 형식 어설션이 제거되었습니다.
* `add` 작업의 서버측 처리가 문자열 값을 반복하여 패치 대신 개체로 처리하는 문제가 해결되었습니다.
