---
title: 범용 편집기 2025.02.17 릴리스 정보
description: 다음은 범용 편집기 2025.02.17 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: c88aa13c6bc75c8f9cd624d00ef768290981c840
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 23%

---


# 범용 편집기 2025.02.17 릴리스 정보 {#release-notes}

유니버설 편집기의 2025년 2월 17일 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **미리 보기에 게시** - [유니버설 편집기를 사용하여 콘텐츠를 게시(또는 게시 취소)할 때](/help/sites-cloud/authoring/universal-editor/publishing.md) 이제 게시 환경 외에 [미리 보기 환경](/help/sites-cloud/authoring/sites-console/previewing-content.md)에 게시할지 선택할 수 있습니다
   * 이를 통해 게시하기 전에 콘텐츠를 검토할 수 있습니다.
* **구성 요소 정의에 모델과 필터를 정의할 수 있습니다** - 이제 구성 요소 정의에 [구성 요소가 사용하는 모델과 필터를 정의할 수 있습니다.](/help/implementing/universal-editor/component-definition.md#template)
   * 이 정보는 정의에서 중앙에서 유지 관리할 수 있으며 계측을 지정할 필요가 없습니다.
   * 이렇게 하면 컨테이너 간에 구성 요소를 이동할 수 있습니다.
* **컨테이너의 자식 요소는 암시적으로 구성 요소로 간주됩니다** - [항목이 `data-aue-resource`](/help/implementing/universal-editor/attributes-types.md#data-properties)인 항목을 컨테이너에 직접 자식으로 배치하는 경우 구성 요소로 간주되며 `data-aue-behavior="component"`을(를) 지정하지 않아도 이동할 수 있습니다.

## 기타 개선 사항 {#other-improvements}

* **AEM 6.5 에셋 선택기** - [AEM 6.5와 함께 범용 편집기를 실행할 때 이제 6.5 에셋 선택기가 제대로 열립니다.](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
