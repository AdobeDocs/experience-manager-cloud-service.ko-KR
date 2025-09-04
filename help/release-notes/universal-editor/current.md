---
title: 범용 편집기 2025.09.04 릴리스 정보
description: 다음은 범용 편집기 2025.09.04 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 0c380e0faca1db0966d22d056dd1f824a731a7bc
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 71%

---


# 범용 편집기 2025.09.04 릴리스 정보 {#release-notes}

유니버설 편집기의 2025년 9월 4일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* [얼리어답터](#copy-paste)에 복사 및 붙여넣기를 사용할 수 있습니다.

### 실행 취소/다시 실행 {#undo-redo}

이제 범용 편집기 콘텐츠 작성자는 실행 취소 및 다시 실행 기능을 사용할 수 있습니다.

* 여기에는 컨텍스트에서 수행된 편집, 속성 패널을 통한 편집, 블록 추가(또는 복제), 이동 및 삭제 작업이 모두 포함됩니다.
* 실행 취소 및 다시 실행 기능은 현재 브라우저 세션으로 제한됩니다.

## 얼리 어답터 기능 {#early-adopter}

이들 출시 예정인 기능을 테스트하고 피드백을 공유하는 데 관심이 있다면 Adobe ID와 연결된 이메일 주소로 Adobe 고객 성공 관리자에 이메일을 보내 주십시오.

### 새 RTE {#new-rte}

링크 대화 상자에 페이지 선택기가 있는 새로운 ProseMirror RTE를 이제 오른쪽 패널에서 사용할 수 있습니다.

### 복사/붙여넣기 {#copy-paste}

이제 콘텐츠 작성자는 동일한 페이지 내에서 구성 요소를 복사하여 붙여넣을 수 있습니다.

## 기타 개선 사항 {#other-improvements}

* 편집기 도구 모음의 스타일이 예정된 새로운 RTE에 더 잘 부합하도록 업데이트되었습니다.
* 자산 선택기 대화 상자의 필터가 복원되었습니다.

## 사용 중단 {#deprecations}

* `text-input`및 `text-area`구성 요소는 [릴리스 2025.07.09](/help/release-notes/universal-editor/2025/2025-07-09.md)와 함께 공식적으로 더 이상 사용되지 않습니다.
   * `model-definition.json`에서 텍스트 구성 요소를 사용하여 속성 패널에 대한 텍스트 입력을 만드십시오.
