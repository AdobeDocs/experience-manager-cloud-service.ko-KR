---
title: 범용 편집기 2025.07.09 릴리스 정보
description: 다음은 범용 편집기 2025.07.09 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 199ee7e11f6706773bd426c3d27236d6ea791a6c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 25%

---


# 범용 편집기 2025.07.09 릴리스 정보 {#release-notes}

유니버설 편집기의 2025년 7월 9일 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* [컨테이너에서 **추가** 도구 모음 단추를 클릭할 때](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components) 구성 요소 형식이 하나만 허용되는 경우 드롭다운 메뉴에서 선택하지 않고 바로 삽입됩니다.
* [인증 헤더 도구 모음 옵션](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings)은(는) 대부분의 경우 유용하지 않으므로 기능 전환 뒤에 배치되었습니다.
* [속성 패널의 다중 필드에 대해 컨테이너를 중첩시킬 수 없으므로](/help/implementing/universal-editor/field-types.md#fields) 렌더링 루틴은 이제 필드 목록에서 중첩된 컨테이너를 필터링하여 잘못된 중첩을 방지합니다.

## 얼리 어답터 기능 {#early-adopter}

예정된 이러한 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 이메일 주소에서 Adobe Customer Success Manager에게 이메일을 보내십시오.

### 새 RTE {#new-rte}

링크 대화 상자에 페이지 선택기가 있는 새로운 ProseMirror RTE를 이제 오른쪽 패널에서 사용할 수 있습니다.

### 실행 취소/다시 실행 {#undo-redo}

이제 범용 편집기 콘텐츠 작성자는 실행 취소 및 다시 실행 기능을 사용할 수 있습니다.

* 여기에는 컨텍스트에서 수행된 편집, 속성 패널을 통한 편집, 블록 추가(또는 복제), 이동 및 삭제 작업이 모두 포함됩니다.
* 실행 취소 및 다시 실행 기능은 현재 브라우저 세션으로 제한됩니다.

## 기타 개선 사항 {#other-improvements}

* 속성 레일을 통해 편집할 때 단일 에셋 참조를 제거할 수 없는 문제가 수정되었습니다.
* 에셋 참조가 배열로 자동 변환되어 무한 로드 상태가 되므로 속성 패널이 무기한 로드되는 문제가 수정되었습니다.
   * 이제 에셋 참조 값은 배열로 자동 변환되지 않고 그대로 저장됩니다.
* 모델이 정의되어 있지만 콘텐츠가 들어 있지 않을 때 속성 패널에 필드가 표시되지 않는 문제가 수정되었습니다.
   * 이로 인해 빈 콘텐츠 조각과 같은 빈 세부 사항 응답에 대한 속성 패널에 대해 무한 로드 상태가 발생했습니다.
* ESLint 구성은 업데이트된 규칙 및 플러그인 지원을 포함하여 버전 9와의 호환성을 위해 리팩터링되었습니다.

## 사용 중단 {#deprecations}

* `text-input` 구성 요소는 이제 공식적으로 사용되지 않습니다.
   * `model-definition.json`에서 텍스트 구성 요소를 사용하여 속성 패널에 대한 텍스트 입력을 만듭니다.
