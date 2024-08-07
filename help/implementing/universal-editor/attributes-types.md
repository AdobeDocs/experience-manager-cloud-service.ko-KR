---
title: 속성 및 항목 유형
description: 범용 편집기에 필요한 데이터 특성 및 항목 유형에 대해 알아봅니다.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 79%

---


# 속성 및 유형 {#attributes-types}

범용 편집기에 필요한 데이터 특성 및 항목 유형에 대해 알아봅니다.

## 소개 {#introduction}

Universal Editor에서 앱을 편집할 수 있으려면 앱이 적절하게 구성되어야 합니다. 여기에는 편집기가 앱의 콘텐츠를 편집하는 데 필요한 적절한 메타데이터가 포함됩니다. 이 문서에서는 해당 메타데이터의 특성 및 항목 유형에 대해 자세히 설명합니다.

>[!NOTE]
>
>콘텐츠 유효성 검사는 서버측에서 수행됩니다. Universal Editor는 단순히 데이터 속성을 이용합니다. 모델/구조에 적합한지 확인하는 작업은 API 수준에서 수행해야 합니다.

## 데이터 속성 {#data-properties}

| 데이터 속성 | 설명 |
|---|---|
| `data-aue-resource` | 리소스에 대한 URN은 [AEM에서 Universal Editor 시작하기 문서의 페이지 계측](getting-started.md#instrument-thepage) 섹션을 참조하십시오. |
| `data-aue-prop` | 리소스의 속성은 [AEM에서 Universal Editor 시작하기 문서의 페이지 계측](getting-started.md#instrument-thepage) 섹션을 참조하십시오. |
| `data-aue-type` | [편집 가능한 항목의 유형](#item-types)(예: 텍스트, 이미지, 참조) |
| `data-aue-filter` | 사용할 수 있는 참조 정의 |
| `data-aue-label` | 편집기에 표시되는 선택 가능한 항목에 대한 사용자 정의 레이블 정의 <br>`data-aue-model`이 설정된 경우, 레이블은 모델을 통해 검색 |
| `data-aue-model` | 속성 레일에서 양식 기반의 편집에 사용될 모델 정의 |
| `data-aue-behavior` | 계기의 [동작을 정의합니다](#behaviors). 예를 들어, 독립 실행형 텍스트 또는 이미지는 구성 요소를 모방하여 이동하거나 삭제할 수 있습니다 |

## 항목 유형 {#item-types}

| `data-aue-type` | 설명 | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | 텍스트는 HTML 태그 내에서 편집할 수 있지만 간단한 텍스트 형식으로만 사용할 수 있으며 서식 있는 텍스트 형식(예: 제목 구성 요소에 일반적으로 사용되는 텍스트 형식)은 사용 불가 | 옵션 | 필수 | 해당 사항 없음 | 옵션 | 해당 사항 없음 | 옵션 |
| `richtext` | 전체 서식 있는 텍스트 기능으로 텍스트 편집 가능. RTE는 오른쪽 편집기 패널에 표시됨 | 옵션 | 필수 | 해당 사항 없음 | 옵션 | 해당 사항 없음 | 옵션 |
| `media` | 편집 가능한 자산은 이미지 또는 비디오와 같은 자산입니다 | 옵션 | 필수 | 옵션<br>자산 선택기로 전달되는 이미지 또는 비디오 필터 조건 목록 | 옵션 | 해당 사항 없음 | 옵션 |
| `container` | 편집 가능 항목은 단락 시스템이라는 구성 요소의 컨테이너 역할을 합니다. | 상황에 따라 다름 <br>아래 참조 | 상황에 따라 다름 <br>아래 참조 | 옵션<br>허용된 구성 요소 목록 | 옵션 | 해당 사항 없음 | 해당 사항 없음 |
| `component` | 편집 가능 항목은 구성 요소입니다. 추가 기능을 추가하지 않습니다. DOM의 이동/삭제 가능한 부분을 표시하고 속성 레일 및 해당 필드를 여는 데 필요함 | 필수 | 해당 사항 없음 | 해당 사항 없음 | 옵션 | 옵션 | 해당 사항 없음 |
| `reference` | 편집 가능한 는 콘텐츠 조각, 경험 조각 또는 제품과 같은 참조입니다 | 상황에 따라 다름 <br>아래 참조 | 상황에 따라 다름 <br>아래 참조 | 옵션<br>콘텐츠 조각, 제품 또는 참조 선택기에 전달되는 경험 조각 필터 조건 목록 | 옵션 | 옵션 | 해당 사항 없음 |

사용 사례에 따라 다름 `data-aue-prop` 또는 `data-aue-resource`가 필요할 수도 있고 필요하지 않을 수도 있습니다. 예:

* GraphQL을 통해 콘텐츠 조각을 쿼리하고 상황에 따라 목록을 편집할 수 있도록 하려면 `data-aue-resource`가 필요합니다.
* 참조된 콘텐츠 조각의 콘텐츠를 렌더링하는 구성 요소가 있고 구성 요소 내에서 참조를 업데이트하려는 경우 `data-aue-prop`이 필요합니다.

## 동작 {#behaviors}

| `data-aue-behavior` | 설명 |
|---|---|
| `component` | 독립 실행형 텍스트, 서식 있는 텍스트 및 미디어 모방 구성 요소를 허용하여 페이지에서 이동 및 삭제할 수 있도록 하는 데 사용됩니다. |
| `container` | 컨테이너를 자체 구성 요소로 취급하여 페이지에서 이동 및 삭제할 수 있도록 하는 데 사용됩니다. |
