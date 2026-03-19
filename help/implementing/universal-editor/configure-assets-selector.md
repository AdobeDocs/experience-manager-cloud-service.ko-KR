---
title: 범용 편집기를 위한 Assets 선택기 구성
description: 범용 편집기에서 사용하도록 자산 선택기를 구성하는 방법을 이해합니다.
feature: Developing
role: Admin, Developer
source-git-commit: 0ed57393afaf9af3258dacdcb043487f4a098e03
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# 범용 편집기를 위한 Assets 선택기 구성 {#configure-assets-selector}

범용 편집기에서 사용하도록 자산 선택기를 구성하는 방법을 이해합니다.

## 개요 {#overview}

유니버설 편집기는 [자산 선택기](/help/assets/overview-asset-selector.md#using-asset-selector)를 사용하여 작성자가 콘텐츠에 삽입할 자산을 검색하고 선택할 수 있도록 합니다.

자산 선택기는 [구성 요소 필터를 사용하여 유니버설 편집기 내에서 구성할 수 있습니다.](/help/implementing/universal-editor/filtering.md) 이 문서에서는 사용 가능한 구성 옵션에 대해 설명합니다.

>[!NOTE]
>
>범용 편집기 프로젝트를 시작할 때 자산 선택기에 대한 필터가 없습니다. 작성자는 사용자 권한이 일반적으로 허용하는 모든 에셋에 액세스할 수 있습니다.

## 필터 정의 {#filter-definition}

에셋 선택기에 대한 필터 정의는 간단한 구조를 사용합니다.

```json
[
  {
    "id": "assets-filter",
    "assets": {...}
   }
]
```

## 필터 옵션 {#filter-options}

`assets` 필터에는 다음 옵션이 있을 수 있습니다.

* `deliveryTier?`: - 사용할 다음 게재 계층 중 하나를 정의합니다.
   * `dm`: 필요한 경우 `publish`(으)로 폴백이 포함된 Dynamic Media(기본 설정)
   * `publish`: AEM 게시 인스턴스
* `repoNames?`: 문자열 - 이미지를 선택하는 데 사용할 수 있는 AEM 저장소 목록입니다.
   * 기본값: 모든 게재 저장소
* `selectionTier?`: 문자열 - 자산을 선택할 AEM 계층
   * 기본값: `["author", "delivery"]`
* `disableRemote?`: 부울 - 원격 리포지토리 지원을 사용하지 않도록 설정합니다.
* `preselectedTypes?`: 문자열 - 자산 선택기에서 기본 필터로 적용할 미리 선택된 파일 형식
* `minMaxDimensions?`: 개체 - 에셋 선택기에서 기본 필터로 적용할 최소 및/또는 최대 차원(픽셀 단위)을 제공합니다.
   * `widthMin?`: 숫자 - 최소 너비
   * `widthMax?`: 숫자 - 최대 너비
   * `heightMin?`: 숫자 - 최소 높이
   * `heightMax?`: 숫자 - 최대 높이
* `minMaxFileSize?`: 개체 - 자산 선택기에서 기본 필터로 적용할 최소 및/또는 최대 파일 크기(바이트)를 제공합니다.
   * `min?`: 숫자 - 최소 파일 크기
   * `max?`: 숫자 - 최대 파일 크기
* `customFileTypeFilters?`: 개체 - 에셋 선택기에 표시할 사용자 지정 파일 형식 필터를 제공합니다.
   * `label`: 문자열 - 자산 선택 UI에 표시될 레이블입니다.
   * `value`: 문자열 - 필터링할 파일 형식의 값
* `displayFilters?`: 부울 - 자산 선택기에서 필터 UI를 비활성화하는 데 사용됩니다. 기본적으로 true

## 예 {#example}

다음 예에는 설명을 위한 대부분의 옵션이 포함되어 있습니다.

```json
[
  {
    "id": "assets-filter",
    "assets": {
      "deliveryTier": "dm",
      "repoNames": ["thisRepo", "thatRepo"],
      "selectionTier": ["author", "delivery"],
      "disableRemote": true,
      "preselectedTypes": ["png", "svg", "jpg", "gif"],
      "minMaxDimensions": {
        "widthMin": 640,
        "widthMax": 640,
        "heightMin": 480,
        "heightMax": 480
      },
      "minMaxFileSize": {
        "min": 1024,
        "max": 1024
      }
    }
   }
]
```

## 추가 리소스 {#additional-resources}

자산 선택기에 대한 자세한 내용은 자산 설명서의 [Micro-Frontend 자산 선택기](/help/assets/overview-asset-selector.md#using-asset-selector) 문서를 참조하십시오.
