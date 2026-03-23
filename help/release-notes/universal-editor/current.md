---
title: 범용 편집기 2026.03.19 릴리스 정보
description: 다음은 범용 편집기 2026.03.19 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 048e86fe7930173bb33de9252607e2910520b575
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 34%

---


# 범용 편집기 2026.03.19 릴리스 정보 {#release-notes}

유니버설 편집기의 2026년 3월 19일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>릴리스하기 전에 **예정된** 범용 편집기 기능을 테스트하려면 [범용 편집기 미리보기 릴리스 정보](/help/release-notes/universal-editor/preview.md)를 참조하십시오.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* [홈 화면](/help/sites-cloud/authoring/universal-editor/navigation.md#home-button)(으)로 다시 이동할 때 속성의 항목이 축소됩니다.
* [자산 선택기](/help/implementing/universal-editor/configure-assets-selector.md)에서 이제 [필터 정의를 지원합니다.](/help/implementing/universal-editor/filtering.md)
* 선택한 항목에 사용할 수 있는 작업이 없으면 [상황에 맞는 메뉴](/help/sites-cloud/authoring/universal-editor/authoring.md#context-menu)에 이를 나타내는 메시지가 표시됩니다.

## 기타 개선 사항 {#other-improvements}

* 모델/필터/구성 요소 정의가 있는 경우 편집기에서 한 앱에서 다른 앱으로 전환할 때 다시 표시됩니다.
* DA를 백엔드로 사용할 때 이미지를 제거하면 더 이상 빈 이미지 태그가 남지 않습니다.
* 블록의 클래스는 이제 DA를 백 엔드로 사용할 때 올바르게 처리됩니다.
* 이제 Open API가 원격 자산을 개체로 제대로 저장합니다.

## 호환성이 손상되는 변경 {#breaking-change}

* 안정성을 향상시키려면 모든 확장을 `@adobe/uix-guest` >= `1.1.7`(으)로 업데이트해야 합니다.
