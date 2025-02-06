---
title: 범용 편집기 2054.01.16 릴리스 정보
description: 다음은 범용 편집기 2025.01.16 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 77%

---


# 범용 편집기 2025.01.16 릴리스 정보 {#release-notes}

다음은 범용 편집기 2025년 1월 16일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **CORS 라이브러리 &lt;3.0.0 사용 중단** - 향후 호환성을 보장하고 보안을 강화하기 위해 범용 편집기는 이제
  `@Adobe Express/universal-editor-cors` 라이브러리의 버전 3.0.0 이상을 독점적으로 지원합니다.
   * 이제 라이브러리가 [`universal-editor-service.adobe.io/cors.js`](http://universal-editor-service.adobe.io/cors.js)을(를) 통해서만 전달됩니다.
   * 사용자가 이전 버전의 CORS 라이브러리를 사용하는 페이지를 열 때 사용자에게 사용 중단 알림이 나타나 업데이트를 요청합니다.
* **랜딩 페이지 확장 기능 포인트** - 범용 편집기의 랜딩 페이지의 사이드 레일에 [새로운 확장 기능 포인트](/help/implementing/universal-editor/customizing.md#extending)가 표시되도록 도입되었습니다.
   * 이제 개발자는 확장 기능이 편집기, 랜딩 페이지 또는 둘 다에 적용될 수 있는지 여부를 지정하여 더 다양한 사용자 정의와 사용성을 제공할 수 있습니다.

## 기타 개선 사항 {#other-improvements}

* **랜딩 페이지의 최근 항목에 잘못된 URL이 수정됨** - 유니버설 편집기의 랜딩 페이지에 있는 &quot;최근 항목&quot; 목록에 표시된 URL이 끊어진 문제가 해결되었습니다.
* **통합된 셸의 테마 동기화** - 이제 범용 편집기가 테마를 시스템의 통합된 셸 설정과 동적으로 동기화하고 라이트 모드와 다크 모드 사이를 자동으로 조정합니다.
   * 이를 통해 조각 및 자산 선택기를 포함한 마이크로 프론트엔드 전반에 걸쳐 시각적 모양이 일관되게 표시됩니다.
