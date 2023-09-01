---
title: 콘텐츠 조각 작성
description: 콘텐츠 조각용 콘텐츠를 작성한 다음 목적에 따라 해당 콘텐츠의 변형을 만드는 방법을 이해합니다. 이렇게 하면 Headless 게재 및 페이지 작성을 위한 유연성을 높일 수 있습니다.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '2208'
ht-degree: 4%

---


# 콘텐츠 조각 작성 {#authoring-content-fragments}

콘텐츠 조각 작성은 Headless 게재 및 페이지 작성에 모두 중점을 둡니다.

콘텐츠 조각에 사용할 수 있는 편집기는 두 개입니다. 이 섹션에 설명된 편집기:

* 은 headless 콘텐츠 전달을 위해 개발되었지만 (모든 시나리오에 사용할 수 있음)
* 다음에서 사용할 수 있습니다. **컨텐츠 조각** 콘솔

이 편집기는 다음을 제공합니다.

* [자동 저장](#saving-autosaving)편집을 실수로 손실하지 않도록 하려면 를 사용하십시오.
* [콘텐츠 참조로 에셋 인라인 업로드](#reference-images)를 클릭하여 자산 DAM에 업로드해야 합니다.
* [미리 보기](#preview-content-fragment) 콘텐츠 조각에서 제공하는 렌더링된 경험.
* 다음에 대한 기능: [게시](#publish-content-fragment) 및 [게시 취소](#unpublish-content-fragment) 편집기에서 가져왔습니다.
* 다음에 대한 기능: [연결된 언어 사본 보기 및 열기](#view-language-copies) 를 입력합니다.
* 다음에 대한 기능: [버전 세부 사항 보기](#view-version-history) 를 입력합니다.
   * 선택한 버전으로 되돌릴 수도 있습니다.
* 다음에 대한 기능: [상위 참조 보기 및 열기](#view-parent-references).
* 다음을 사용하는 콘텐츠 조각 및 해당 참조의 계층 구조 보기 [구조 트리](#structure-tree).

>[!CAUTION]
>
>이 섹션에 설명된 편집기는 다음과 같습니다 *전용* 다음에서 사용 가능 *온라인* Adobe Experience Manager(AEM as a Cloud Service)

>[!CAUTION]
>
>콘텐츠 조각을 편집하려면 다음 작업을 수행해야 합니다 [적절한 권한](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). 문제가 발생하는 경우 시스템 관리자에게 문의하십시오.
> 
>예를 들어 가 없는 경우 `edit` 편집기의 권한은 읽기 전용입니다.

>[!NOTE]
>
>에 대한 전체 정보는 자산 설명서 를 참조하십시오. [원본 콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-variations.md) - 다음 두 가지 모두에서 사용할 수 있습니다. **에셋** 콘솔 및 **컨텐츠 조각** 콘솔.

>[!NOTE]
>
>필요한 경우 프로젝트 팀이 편집기를 사용자 지정할 수 있습니다. 다음을 참조하십시오 [콘텐츠 조각 콘솔 및 편집기 맞춤화](/help/implementing/developing/extending/content-fragments-console-and-editor.md) 을 참조하십시오.

## 콘텐츠 조각 편집기 {#content-fragment-editor}

콘텐츠 조각 편집기를 처음 열면 네 개의 기본 영역이 표시됩니다.

* 상단 도구 모음: 주요 정보 및 작업
   * 콘텐츠 조각 콘솔에 대한 링크(홈 아이콘)
   * 모델 및 폴더에 대한 정보
   * 링크 대상 [미리보기(모델에 대해 기본 미리보기 URL 패턴이 구성된 경우)](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-fragment-model-properties)
   * [게시](#publish-content-fragment), 및 [게시 취소](#unpublish-content-fragment) 작업
   * 모두 표시 옵션 **상위 참조** (링크 아이콘)
   * 조각 **[상태](/help/sites-cloud/administering/content-fragments/managing.md#statuses-content-fragments)**&#x200B;및 마지막으로 저장한 정보
   * 원본(에셋 기반) 편집기로 전환하는 토글
* 왼쪽 패널: 다음을 표시합니다. **[변형](#variations)** 컨텐츠 조각 및 해당 **필드**:
   * 이러한 링크는 다음 용도로 사용할 수 있습니다. [콘텐츠 조각 구조 탐색](#navigate-structure)
* 오른쪽 패널: 탭을 제공합니다. [속성(메타데이터) 및 태그 표시](#view-properties-tags), 다음에 대한 정보 [버전 기록](#view-version-history)및 관련 정보 [언어 복사](#view-language-copies)
   * 다음에서 **속성** 탭 다음을 업데이트할 수 있습니다 **제목** 및 **설명** 조각 또는 **변형**
* 중앙 패널: 선택한 변형의 실제 필드와 콘텐츠를 표시합니다.
   * 콘텐츠 편집 허용
   * if **탭 자리 표시자** 필드는 여기에 표시된 모델 내에서 정의되며 탐색에 사용할 수 있습니다. 필드는 가로로 표시되거나 드롭다운 목록으로 표시됩니다

![콘텐츠 조각 편집기 - 개요](assets/cf-authoring-overview.png)

>[!CAUTION]
>
>콘텐츠 조각 모델은 종종 다음과 같은 데이터 필드를 정의할 수 있습니다. **제목** 및 **설명**. 이러한 필드가 있는 경우 사용자 정의 필드이며 *중앙 패널* 조각을 편집할 때
>
>콘텐츠 조각 및 그 변형에는 다음과 같은 메타데이터 필드(변형 속성)도 있습니다. **제목** 및 **설명**. 이들 필드는 컨텐츠 조각의 필수적인 부분이며 조각 생성 시 초기에 정의됩니다. 다음에서 업데이트할 수 있습니다. *오른쪽 패널* 조각을 편집할 때

## 콘텐츠 조각 구조 탐색 {#navigate-structure}

단일 콘텐츠 조각

* 다음 두 가지 수준으로 구성됩니다.

   * **[변형](#variations)** / 콘텐츠 조각
   * **필드** - 콘텐츠 조각 모델에서 정의되며 모든 변형에서 사용됩니다.

* 다양한 참조를 포함할 수 있습니다.

### 변형 및 필드 {#variations-and-fields}

왼쪽 패널에서 다음을 볼 수 있습니다.

* 목록 **[변형](#variations)** 이 조각에 대해 만들어진 항목:
   * **기본** 는 콘텐츠 조각을 처음 만들 때 표시되는 변형이며, 나중에 다른 변형을 추가할 수 있습니다
   * 편집할 변형을 선택하고 열 수 있습니다
   * 다음을 수행할 수도 있습니다. [변형 만들기](#create-variation)
* 다음 **필드** 조각 및 그 변형 내:
   * 아이콘은 다음을 나타냅니다. [데이터 유형](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)
   * 텍스트는 필드 이름입니다.
   * 이러한 링크를 함께 사용하면 ( 현재 변형의 경우) 중앙 패널의 필드 콘텐츠에 직접 연결할 수 있습니다

### 링크 팔로우 {#follow-links}

편집기의 여러 부분에서 링크 아이콘이 표시됩니다. 이 옵션은 표시된 항목(예: 콘텐츠 조각 모델, 상위 참조 또는 참조되는 조각)을 여는 데 사용할 수 있습니다.

![콘텐츠 조각 편집기 - 링크 아이콘](assets/cf-authoring-link-icon.png)

### 구조 트리 {#structure-tree}

를 엽니다. **구조 트리** 탭으로 이동하여 콘텐츠 조각의 계층 구조 및 참조를 표시합니다. 링크 아이콘을 사용하여 참조로 이동합니다.

![콘텐츠 조각 편집기 - 구조 트리](assets/cf-authoring-structure-tree.png)

>[!NOTE]
>
>다음을 참조하십시오 [콘텐츠 조각 구조 분석 - 구조 트리](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree) 을 참조하십시오.

## 저장 및 자동 저장 {#saving-autosaving}

<!-- CHECK: cannot be saved, no undo, redo -->

모든 업데이트를 수행하면 콘텐츠 조각이 자동으로 저장됩니다. 마지막으로 저장한 시간이 상단 도구 모음에 표시됩니다.

## 변형 {#variations}

[변형](/help/sites-cloud/administering/content-fragments/overview.md#main-and-variations) 는 AEM 콘텐츠 조각의 중요한 기능입니다. 이 도구를 사용하여 의 복사본을 만들고 편집할 수 있습니다. **기본** headless 콘텐츠 전달 및 페이지 작성을 보다 유연하게 만들 수 있는 특정 채널 및 시나리오에서 사용할 콘텐츠.

편집기에서 다음 작업을 수행할 수 있습니다.

* [변형 만들기](#create-variation) / **기본** 콘텐츠

* 콘텐츠 편집에 필요한 변형 선택

* [변형 이름 바꾸기](#rename-variation)

* [변형 삭제](#delete-variation)

### 변형 만들기 {#create-variation}

콘텐츠 조각의 변형을 만들려면 다음 작업을 수행하십시오.

1. 왼쪽 패널에서 **더하기 기호** (**변형 만들기**)의 오른쪽에 있습니다. **변형**.

   >[!NOTE]
   >
   >첫 번째 변형을 만들면 기존 변형이 동일한 패널에 나열됩니다.

   ![콘텐츠 조각 편집기 - 첫 번째 변형 만들기](assets/cf-authoring-create-variation-01.png)

1. 대화 상자에서 **제목** 변형 및 **설명** 필요한 경우:

   ![콘텐츠 조각 편집기 - 변형 만들기 대화 상자](assets/cf-authoring-create-variation-02.png)

1. **만들기** 변형. 목록에 표시됩니다.

### 변형 이름 바꾸기 {#rename-variation}

이름 바꾸기 **변형**:

1. 필요한 변형을 선택합니다.

1. 를 엽니다. **속성** 오른쪽 패널의 탭입니다.

1. 변형 업데이트 **제목**.

1. 누르거나 **반환** 또는 다른 필드로 이동하여 변경 사항을 자동으로 저장합니다. 제목이에서 업데이트됩니다. **변형** 왼쪽 패널입니다.


### 변형 삭제 {#delete-variation}

콘텐츠 조각의 변형을 삭제하려면

>[!NOTE]
>
>삭제할 수 없습니다. **기본**.

1. 변형을 선택합니다.

1. 다음에서 **변형** 패널에서 삭제 아이콘(휴지통)을 선택합니다.

   ![콘텐츠 조각 편집기 - 변형 삭제 아이콘](assets/cf-authoring-delete-variation.png)

1. 대화 상자가 열립니다. 선택 **삭제** 작업을 확인합니다.

## 여러 줄 텍스트 필드 편집 - 일반 텍스트 또는 Markdown {#edit-multi-line-text-fields-plaintext-markdown}

**[여러 줄 텍스트](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** 필드에는 다음 세 가지 형식 중 하나가 있을 수 있습니다.

* 일반 텍스트
* [Markdown](/help/sites-cloud/administering/content-fragments/markdown.md)
* [리치 텍스트](#edit-multi-line-text-fields-rich-text)

일반 텍스트 또는 Markdown으로 정의된 필드에는 (화면 내) 서식 옵션이 없는 간단한 텍스트 상자가 있습니다.

![콘텐츠 조각 편집기 - 여러 줄 텍스트 - 전체 화면](assets/cf-authoring-multilinetext-plaintext-markdown.png)

## 여러 줄 텍스트 필드 편집 - 서식 있는 텍스트 {#edit-multi-line-text-fields-rich-text}

대상 **[여러 줄 텍스트](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** 로 정의된 필드 **리치 텍스트**, 다양한 기능을 사용할 수 있습니다.

* 콘텐츠를 편집합니다.
   * 실행 취소 / 다시 실행
   * 텍스트로 붙여넣기/붙여넣기
   * 복사
   * 단락 형식 선택
   * 테이블 만들기/관리
   * 텍스트 서식 지정, 굵게, 기울임체, 밑줄, 색상
   * 단락 정렬 설정
   * 목록 만들기/관리, 글머리 기호, 번호 매기기
   * 텍스트 들여쓰기, 감소, 증가
   * 현재 서식 지우기
   * 링크 삽입
   * 이미지 에셋에 대한 참조 선택 및 삽입
   * 특수 문자 추가
* [전체 화면 편집기](#full-screen-editor-rich-text) - 전체 화면과 흐름 간 전환
* [통계](#statistics-rich-text)
* [비교 및 동기화](#compare-and-synchronize-rich-text)

예:

![콘텐츠 조각 편집기 - 여러 줄 텍스트 - 전체 화면 전환](assets/cf-authoring-multilinetext-fullscreen-toggle.png)

>[!NOTE]
>
>여러 줄 텍스트 필드도 적절하게 표시됩니다 [아이콘](#fields-datatypes-icons) 다음에서 **필드** 패널.

### 전체 화면 편집기 - 리치 텍스트 {#full-screen-editor-rich-text}

전체 화면 편집기는 인플로우와 동일한 편집 옵션을 제공하지만 텍스트를 위한 더 많은 공간을 제공합니다.

예:

![콘텐츠 조각 편집기 - 여러 줄 텍스트 - 전체 화면](assets/cf-authoring-multilinetext-fullscreen.png)

### 통계 - 리치 텍스트 {#statistics-rich-text}

작업 **통계** 여러 줄 필드에 텍스트에 대한 다양한 정보를 표시합니다.

예:

![콘텐츠 조각 편집기 - 통계](assets/cf-authoring-multilinetext-statistics.png)

### 비교 및 동기화 - 리치 텍스트 {#compare-and-synchronize-rich-text}

작업 **비교** 은(는) 이 있는 경우 여러 줄 필드에 사용할 수 있습니다. **변형** 열어요

다중 라인 필드가 전체 화면으로 열리고,

* 다음 두 항목에 대한 컨텐츠 표시: **기본** 및 현재 **변형** 다른 점이 강조 표시된 상태로 동시에

* 차이점은 색상으로 표시됩니다.

   * 녹색은 변형에 추가된 콘텐츠를 나타냅니다.
   * 빨간색은 변형에서 제거된 콘텐츠를 나타냅니다.
   * 파란색은 대체된 텍스트를 나타냅니다.

* 다음을 제공합니다. **동기화** 작업 : 콘텐츠를 동기화합니다. **기본** 현재 변형으로

   * if **기본** 이(가) 업데이트되었습니다. 그러면 이러한 변경 사항이 변형으로 전송됩니다
   * 변형이 업데이트된 경우 다음 변경 사항은에서 콘텐츠로 덮어쓰기됩니다. **기본**

  >[!CAUTION]
  >
  >동기화는 변경 내용을 복사하는 데에만 사용할 수 있습니다. *출처:**기본**변형에*.
  >
  >변경 사항 전송 중 *변형에서으로&#x200B;**기본*** 은 옵션으로 사용할 수 없습니다.

예를 들어 변형 컨텐츠가 완전히 다시 작성되었으므로 동기화하면 해당 새 컨텐츠가 의 컨텐츠로 대체됩니다 **기본**:

![콘텐츠 조각 편집기 - 비교 및 동기화](assets/cf-authoring-multilinetext-compare.png)

## 참조 관리 {#manage-references}

### 조각 참조 {#fragment-references}

[조각 참조](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments) 을 사용하여 다음을 수행할 수 있습니다.

* [기존 콘텐츠 조각에 대한 참조 만들기](#create-reference-existing-content-fragment)
* [컨텐츠 조각을 만든 다음 참조합니다.](#create-reference-content-fragment)

#### 기존 콘텐츠 조각에 대한 참조 만들기 {#create-reference-existing-content-fragment}

기존 콘텐츠 조각에 대한 참조를 만들려면 다음 작업을 수행하십시오.

1. 필드를 선택합니다.
1. 선택 **기존 조각 추가**.
1. 조각 선택기에서 필요한 조각을 선택합니다.

   >[!NOTE]
   >
   >한 번에 하나의 조각만 선택할 수 있습니다.

#### 컨텐츠 조각 만들기 및 참조 {#create-reference-content-fragment}

또는 다음을 수행할 수 있습니다. [선택 **새 조각 만들기** 을(를) 열려면 **만들기** 대화 상자](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment). 이 조각을 만들면 참조됩니다.

### 콘텐츠 참조 {#content-references}

[콘텐츠 참조](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference) 이미지, 페이지 및 경험 조각과 같은 다른 AEM 콘텐츠 유형을 참조하는 데 사용됩니다.

#### 참조 이미지 {#reference-images}

위치 **콘텐츠 참조** 두 가지 필드 모두:

* 저장소에 이미 존재하는 에셋 참조
* 필드에 직접 업로드하십시오. 이렇게 하면 **에셋** 업로드할 콘솔

  >[!NOTE]
  >
  >이미지를 로 직접 업로드하려면 **콘텐츠 참조** 필드, it **필수**:
  >
  >* 다음 권한 보유 **루트 경로** 정의됨(에서) [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference)). 이미지가 저장되는 위치를 지정합니다.
  >* include **이미지** 허용된 콘텐츠 유형 목록

자산을 추가하려면 다음 중 하나를 수행할 수 있습니다.

* 새 에셋 파일을 (예: 파일 시스템에서) **콘텐츠 참조** 필드
* 사용 **에셋 추가** 작업을 선택한 후 다음 중 하나를 선택합니다. **에셋 찾아보기** 또는 **업로드** 을(를) 사용하여 적절한 선택기를 열려면 다음을 수행하십시오.

  ![콘텐츠 조각 편집기 - 에셋 옵션 추가](assets/cf-authoring-add-asset-options.png)

#### 참조 페이지 {#reference-pages}

AEM 페이지, 경험 조각 또는 기타 콘텐츠 유형에 대한 참조를 추가하려면 다음을 수행하십시오.

1. 선택 **콘텐츠 경로 추가**.

1. 입력 필드에 필요한 경로를 추가합니다.

1. 다음을 사용하여 확인 **추가**.

### 상위 참조 보기 {#view-parent-references}

상단 도구 모음에서 링크 아이콘을 선택하면 모든 상위 참조 목록이 열립니다.

예:

![콘텐츠 조각 편집기 - 참조 표시](assets/cf-authoring-show-references-link.png)

관련 참조가 모두 나열된 창이 열립니다. 참조를 열려면 이름, 제목 또는 링크 아이콘을 선택합니다.

예:

![콘텐츠 조각 편집기 - 참조 표시](assets/cf-authoring-show-references.png)

## 속성 및 태그 보기 {#view-properties-tags}

오른쪽 패널의 속성 탭에서 속성(메타데이터) 및 태그를 볼 수 있습니다. 속성은 다음 중 하나일 수 있습니다.

* 대상: **컨텐츠 조각** - 경우 **기본** 현재 선택됨
* 특정 **변형**

![콘텐츠 조각 편집기 - 속성](assets/cf-authoring-properties.png)

### 속성 및 태그 편집 {#edit-properties-tags}

속성 탭(오른쪽 패널)에서 다음을 편집할 수도 있습니다.

* **제목**
* **설명**
* **태그**: 드롭다운 또는 선택 대화 상자 사용

  ![콘텐츠 조각 편집기 - 태그 관리](assets/cf-authoring-edit-tags.png)

### 콘텐츠 조각 모델 열기 {#open-content-fragment-model}

다음을 보유한 경우: **기본** 이 옵션을 선택하면 기본 콘텐츠 조각 모델의 이름이 속성 섹션에 표시됩니다. 링크 아이콘을 선택하면 모델이 별도의 탭에서 열립니다.

예:

![콘텐츠 조각 편집기 - 콘텐츠 조각 모델 열기](assets/cf-authoring-open-model.png)

## 버전 내역 보기 {#view-version-history}

다음에서 **버전 기록** 오른쪽 패널의 탭에는 현재 및 이전 버전에 대한 세부 정보가 표시됩니다.

>[!NOTE]
>
>콘텐츠 조각이 게시되면 새 버전이 만들어집니다.

![콘텐츠 조각 편집기 - 버전 내역 개요](assets/cf-authoring-version-history-overview.png)

### 버전으로 되돌리기 {#revert-version}

모든 버전으로 되돌릴 수 있습니다.

특정 버전으로 되돌리려면 다음을 수행하십시오.

1. 버전 옆에 있는 세 점 아이콘을 선택합니다.

1. 선택 **되돌리기**.

![콘텐츠 조각 편집기 - 버전 내역 되돌리기](assets/cf-authoring-version-history-revert.png)

## 언어 사본 보기 {#view-language-copies}

다음에서 **언어 속성** 모든 관련 언어 사본의 탭 세부 정보가 표시됩니다. 링크 아이콘을 선택하면 별도의 탭에서 복사본이 열립니다.

예:

![콘텐츠 조각 편집기 - 언어 사본 열기](assets/cf-authoring-open-language-copies.png)

>[!NOTE]
>
>콘텐츠 조각 번역 및 언어 사본 만들기에 대한 자세한 내용은 [AEM Headless 번역 여정](/help/journey-headless/translation/overview.md).


## 조각 미리보기 {#preview-content-fragment}

콘텐츠 조각 편집기는 작성자가 외부 프론트엔드 애플리케이션에서 편집 내용을 미리 볼 수 있는 옵션을 제공합니다.

이 기능을 사용하려면 먼저 다음을 수행해야 합니다.

* IT 팀과 함께 JSON 출력을 소비하여 콘텐츠 조각을 렌더링할 외부 프론트엔드 애플리케이션을 설정합니다.
* 외부 프론트엔드 애플리케이션이 설정되면 **기본 미리보기 URL 패턴** 을(를) (으)로 정의해야 합니다. [적절한 콘텐츠 조각 모델의 속성](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties).

URL이 정의된 경우 **미리 보기** 버튼이 활성 상태입니다. 이 단추를 선택하여 외부 응용 프로그램을 시작(별도의 탭에서)하여 콘텐츠 조각을 렌더링할 수 있습니다.

## 조각 게시 {#publish-content-fragment}

다음을 수행할 수 있습니다. **게시** 다음 중 하나에 대한 조각

* 인스턴스 미리 보기
* 게시 인스턴스

편집기 또는 콘솔에서 조각을 게시할 수 있습니다. 다음을 참조하십시오 [조각 게시 및 미리보기](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) 전체 세부 정보.

## 조각 게시 취소 {#unpublish-content-fragment}

다음을 수행할 수도 있습니다. **게시 취소** 다음 중 하나에서 조각 생성:

* 인스턴스 미리 보기
* 게시 인스턴스

편집기 또는 콘솔에서 조각의 게시를 취소할 수 있습니다. 다음을 참조하십시오 [조각 게시 취소](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) 전체 세부 정보.

## 필드, 데이터 유형 및 아이콘 {#fields-datatypes-icons}

다음 **필드** 패널 에는 콘텐츠 조각 내의 모든 필드가 나열됩니다. 아이콘은 **[데이터 유형](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)**:

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><p><b>한 줄 텍스트</b></p> </td>
   <td><p> <img src="assets/cf-authoring-single-line-text-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>여러 줄 텍스트</b></p> </td>
   <td><p> <img src="assets/cf-authoring-multi-line-text-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>숫자</b></p> </td>
   <td><p> <img src="assets/cf-authoring-number-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>부울</b></p> </td>
   <td><p> <img src="assets/cf-authoring-boolean-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>날짜 및 시간</b></p> </td>
   <td><p> <img src="assets/cf-authoring-date-time-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>열거</b></p> </td>
   <td><p> <img src="assets/cf-authoring-enumeration-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>태그</b></p> </td>
   <td><p> <img src="assets/cf-authoring-tags-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>콘텐츠 참조</b></p> </td>
   <td><p> <img src="assets/cf-authoring-content-reference-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>조각 참조</b></p> </td>
   <td><p> <img src="assets/cf-authoring-fragment-reference-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>JSON 오브젝트</b></p> </td>
   <td><p> <img src="assets/cf-authoring-json-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>탭 플레이스홀더</b></p><p>실제 아이콘으로 표시되지 않지만 <b>탭 자리 표시자</b> 는 왼쪽 패널과 중앙 패널에 표시됩니다.</p> </td>
   <td><p> <img src="assets/cf-authoring-tab-icon.png"> </p></td>
  </tr>
 </tbody>
</table>
