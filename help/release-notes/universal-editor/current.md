---
title: 범용 편집기 2025.07.09 릴리스 정보
description: 다음은 범용 편집기 2025.07.09 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 199ee7e11f6706773bd426c3d27236d6ea791a6c
workflow-type: ht
source-wordcount: '368'
ht-degree: 100%

---


# 범용 편집기 2025.07.09 릴리스 정보 {#release-notes}

다음은 범용 편집기 2025년 7월 9일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* [컨테이너에서 **추가** 도구 모음 버튼을 클릭하면](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components) 하나의 구성 요소 유형만 허용되는 경우 드롭다운 메뉴에서 선택하지 않아도 즉시 삽입됩니다.
* [인증 헤더 도구 모음 옵션](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings)은 대부분의 경우 유용하지 않으므로 기능 토글 뒤로 배치되었습니다.
* [속성 패널에서 다중 필드에 대한 컨테이너 중첩이 허용되지 않으므로](/help/implementing/universal-editor/field-types.md#fields) 렌더링 루틴이 이제 필드 목록에서 중첩된 컨테이너를 필터링함으로써 잘못된 중첩을 방지합니다.

## 얼리 어답터 기능 {#early-adopter}

이들 출시 예정인 기능을 테스트하고 피드백을 공유하는 데 관심이 있다면 Adobe ID와 연결된 이메일 주소로 Adobe 고객 성공 관리자에 이메일을 보내 주십시오.

### 새 RTE {#new-rte}

링크 대화 상자에 페이지 선택기가 있는 새로운 ProseMirror RTE를 이제 오른쪽 패널에서 사용할 수 있습니다.

### 실행 취소/다시 실행 {#undo-redo}

이제 범용 편집기 콘텐츠 작성자는 실행 취소 및 다시 실행 기능을 사용할 수 있습니다.

* 여기에는 컨텍스트에서 수행된 편집, 속성 패널을 통한 편집, 블록 추가(또는 복제), 이동 및 삭제 작업이 모두 포함됩니다.
* 실행 취소 및 다시 실행 기능은 현재 브라우저 세션으로 제한됩니다.

## 기타 개선 사항 {#other-improvements}

* 속성 레일을 통해 편집할 때 단일 자산 참조 제거가 불가능했던 문제가 해결되었습니다.
* 자산 참조가 자동으로 배열로 변환되어 무한 로딩 상태가 발생함으로써 속성 패널이 무한정 로드되는 문제가 해결되었습니다.
   * 자산 참조 값은 이제 배열로 자동 변환되지 않고 그대로 저장됩니다.
* 모델이 정의되었지만 콘텐츠가 포함되지 않은 경우 속성 패널에 필드가 표시되지 않는 문제가 해결되었습니다.
   * 이로 인해 빈 콘텐츠 조각과 같이 비어 있는 세부 정보 응답에 대해 속성 패널에서 무한 로딩 상태가 발생했습니다.
* ESLint 구성이 업데이트된 규칙과 플러그인 지원을 포함하여 버전 9와의 호환성을 위해 리팩토링되었습니다.

## 사용 중단 {#deprecations}

* `text-input` 구성 요소는 이제 공식적으로 더 이상 사용되지 않습니다.
   * `model-definition.json`에서 텍스트 구성 요소를 사용하여 속성 패널에 대한 텍스트 입력을 만드십시오.
