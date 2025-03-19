---
title: 범용 편집기 2025.03.10 릴리스 정보
description: 다음은 범용 편집기 2025.03.10 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b3c98f5e41dbc5e1714d0ed418a317199c735b73
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 23%

---


# 범용 편집기 2025.03.10 릴리스 정보 {#release-notes}

유니버설 편집기의 2025년 3월 10일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **구성 요소 이동:** [컨테이너 간 구성 요소 이동](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components)은(는) 이제 대상 컨테이너의 구성 요소 필터를 확인합니다.
   * 더 이상 컨테이너 간에 구성 요소를 이동하기 위해 대상 컨테이너와 대상 컨테이너 모두에 대해 동일한 [필터 정의](/help/implementing/universal-editor/filtering.md)를 보유해야 하는 요구 사항이 없습니다.
* **잠긴 페이지:** 유니버설 편집기 서비스는 [페이지의 잠금 상태](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page)를 관찰하고 잠기지 않았거나 사용자가 잠근 페이지에만 씁니다.

## 기타 개선 사항 {#other-improvements}

* Headless 캔버스에 대한 유효성 검사를 수정했습니다.

## 사용 중단 {#deprecation}

* npm 또는 `https://unviersal-editor-service.experiencecloud.live/corslib/*`을(를) 통해 제공된 `universal-editor-cors` 라이브러리는 더 이상 사용할 수 없습니다.
   * 대신 `https://universal-editor-service.adobe.io/cors.js`을(를) 가리키는 스크립트 태그를 사용해야 합니다.
   * 범용 편집기에서 사용할 페이지를 올바르게 계측하는 방법에 대한 자세한 내용은 [AEM 개발자를 위한 유니버설 편집기 개요](/help/implementing/universal-editor/developer-overview.md)를 참조하십시오.
   * 잘못된 메서드를 사용하면 하루에 한 번 사용 중단 메시지가 표시됩니다.
