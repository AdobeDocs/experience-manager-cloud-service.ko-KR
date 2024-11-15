---
title: 속성 및 항목 유형
description: 범용 편집기에 필요한 데이터 특성 및 항목 유형에 대해 알아봅니다.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Architect, Developer
source-git-commit: edef86c67becf3b8094196d39baa9e69d6c81777
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 53%

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
| `data-aue-filter` | 다음을 정의합니다.<br>- 사용할 수 있는 RTE 기능<br>- 컨테이너에 추가할 수 있는 구성 요소<br>- 미디어 유형에 추가할 수 있는 자산 |
| `data-aue-label` | 편집기에 표시되는 선택 가능한 항목에 대한 사용자 지정 레이블을 정의합니다. |
| `data-aue-model` | 속성 패널에서 양식 기반 편집에 사용되는 모델을 정의합니다. |
| `data-aue-behavior` | 계기의 [동작을 정의합니다](#behaviors). 예를 들어, 독립 실행형 텍스트 또는 이미지는 구성 요소를 모방하여 이동하거나 삭제할 수 있습니다 |

## 항목 유형 {#item-types}

| `data-aue-type` | 설명 | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | 텍스트는 HTML 태그 내에서 편집할 수 있지만 간단한 텍스트 형식으로만 사용할 수 있으며 서식 있는 텍스트 형식(예: 제목 구성 요소에 일반적으로 사용되는 텍스트 형식)은 사용 불가 | 옵션 | 필수 | 해당 사항 없음 | 옵션 | 해당 사항 없음 | 옵션 |
| `richtext` | 전체 서식 있는 텍스트 기능으로 텍스트 편집 가능. RTE는 오른쪽 편집기 패널에 표시됨 | 옵션 | 필수 | 해당 사항 없음 | 옵션 | 해당 사항 없음 | 옵션 |
| `media` | 편집 가능한 자산은 이미지 또는 비디오와 같은 자산입니다 | 옵션 | 필수 | 옵션<br>자산 선택기로 전달되는 이미지 또는 비디오 필터 조건 목록 | 옵션 | 해당 사항 없음 | 옵션 |
| `container` | 편집 가능 항목은 단락 시스템이라는 구성 요소의 컨테이너 역할을 합니다. | 상황에 따라 다름 <br>아래 참조 | 상황에 따라 다름 <br>아래 참조 | 옵션<br>허용된 구성 요소 목록 | 옵션 | 해당 사항 없음 | 해당 사항 없음 |
| `component` | 편집 가능 항목은 구성 요소입니다. 추가 기능을 추가하지 않습니다. DOM의 이동/삭제 가능한 부분을 표시하고 속성 패널과 해당 필드를 여는 데 필요합니다. | 필수 | 해당 사항 없음 | 해당 사항 없음 | 옵션 | 옵션 | 해당 사항 없음 |
| `reference` | 편집 가능한 는 콘텐츠 조각, 경험 조각 또는 제품과 같은 참조입니다 | 상황에 따라 다름 <br>아래 참조 | 상황에 따라 다름 <br>아래 참조 | 옵션<br>콘텐츠 조각, 제품 또는 참조 선택기에 전달되는 경험 조각 필터 조건 목록 | 옵션 | 옵션 | 해당 사항 없음 |

`data-aue-resource`은(는) 콘텐츠 변경 내용이 기록되는 위치를 나타내는 기본 키이므로 항상 필요합니다.

* `data-aue-type`이(가) 설정된 태그에는 직접 필요하지 않습니다.
* 설정되지 않은 경우 가장 가까운 부모의 `data-aue-resource` 특성이 사용됩니다.

`data-aue-prop`은(는) 선택적 컨테이너인 컨테이너를 제외하고 컨텍스트에서 편집을 수행할 때마다 필요합니다(컨테이너가 콘텐츠 조각이고 prop이 다중 참조 필드를 가리키는 경우).

* `data-aue-prop`은(는) `data-aue-resource`의 기본 키에 대해 업데이트할 특성입니다.

## 동작 {#behaviors}

| `data-aue-behavior` | 설명 |
|---|---|
| `component` | 독립 실행형 텍스트, 서식 있는 텍스트 및 미디어 모방 구성 요소를 허용하여 페이지에서 이동 및 삭제할 수 있도록 하는 데 사용됩니다. |
| `container` | 컨테이너를 자체 구성 요소로 취급하여 페이지에서 이동 및 삭제할 수 있도록 하는 데 사용됩니다. |
