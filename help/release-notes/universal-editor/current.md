---
title: 범용 편집기 2054.01.16 릴리스 정보
description: 다음은 범용 편집기 2025.01.16 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 14bc45917f56ecf358278848e7e830afb1fedccd
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 19%

---


# 범용 편집기 2025.01.16 릴리스 정보 {#release-notes}

다음은 범용 편집기 2025년 1월 16일 릴리스의 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **CORS 라이브러리 사용 중단 &lt; 3.0.0** - 향후 호환성을 보장하고 보안을 강화하기 위해 이제 유니버설 편집기에서 버전 3.0.0 이상을 독점적으로 지원합니다.
  `@Adobe Express/universal-editor-cors` 라이브러리입니다.
   * 라이브러리는 이제 [`universal-editor-service.adobe.io/cors.js`.](http://universal-editor-service.adobe.io/cors.js)을(를) 통해서만 전달됩니다.
   * 이전 버전의 CORS 라이브러리를 사용하는 페이지를 열면 사용자에 대한 사용 중단 알림이 표시되어 업데이트할 것인지 묻는 메시지가 표시됩니다.
* **랜딩 페이지의 확장 지점** - [새 확장 지점](/help/implementing/universal-editor/customizing.md#extending)이 도입되어 유니버설 편집기의 랜딩 페이지의 측면 레일에 확장이 표시됩니다.
   * 이제 개발자는 확장이 편집기나 랜딩 페이지 또는 두 페이지 모두에 적용할 수 있는지 여부를 지정하여 더 나은 사용자 지정 및 유용성을 제공할 수 있습니다.

## 기타 개선 사항 {#other-improvements}

* **랜딩 페이지의 최근 항목에 잘못된 URL이 수정됨** - 유니버설 편집기의 랜딩 페이지에 있는 &quot;최근 항목&quot; 목록에 표시된 URL이 끊어진 문제가 해결되었습니다.
* **통합 셸의 테마 동기화** - 이제 유니버설 편집기에서 테마를 시스템의 통합 셸 설정과 동적으로 동기화하여 밝은 모드와 어두운 모드 간에 자동으로 조정됩니다.
   * 이렇게 하면 조각 및 자산 선택기를 포함하여 마이크로 프론트엔드에서 일관되게 시각적 모양을 유지할 수 있습니다.
