---
title: 범용 편집기 2025.06.19 릴리스 정보
description: 다음은 범용 편집기 2025.06.19 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 5ffae9e548ca952975b3ea805808e227102ec99f
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# 범용 편집기 2025.06.19 릴리스 정보 {#release-notes}

다음은 범용 편집기 2025년 6월 19일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **속성 레일에서 다중 필드 지원** -
  이제 [컨테이너 구성 요소](/help/implementing/universal-editor/field-types.md#container)를 사용하면 다중 필드 속성을 만들 수 있습니다.
* **중첩된 속성 지원** - 이제 [`name` 필드](/help/implementing/universal-editor/field-types.md#nesting)는 속성 중첩을 활성화하는 경로를 지원합니다.
* **크기 조정 가능한 오른쪽 패널** - 이제 사이드 패널의 크기를 조절하여 사이드 패널에 표시되는 긴 콘텐츠를 더 잘 표현할 수 있습니다.

## 얼리 어답터 기능 {#early-adopter}

Adobe의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### **실행 취소/다시 실행** {#undo-redo}

이제 범용 편집기 콘텐츠 작성자는 실행 취소 및 다시 실행 기능을 사용할 수 있습니다.

* 여기에는 컨텍스트에서 수행된 편집, 속성 패널을 통한 편집, 블록 추가(또는 복제), 이동 및 삭제 작업이 모두 포함됩니다.
* 실행 취소 및 다시 실행 기능은 현재 브라우저 세션으로 제한됩니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 Adobe 고객 성공 관리자에 이메일을 보내주십시오.

## 기타 개선 사항 {#other-improvements}

* 컨테이너 간에 블록을 이동할 때 발생하는 리소스 키 충돌 오류가 해결되었습니다.
* 컨테이너의 마지막 블록을 복제하는 데 실패하는 문제가 해결되었습니다.
* 이제 액션 추가 드롭다운에는 적합한 플러그인이 `component-definition.json` 파일에 정의된 구성 요소만 나열됩니다.
* 게시 대화 상자에서 사용되는 수정 날짜가 수정되어 일부 상황에서 페이지가 수정된 것으로 인식되지 않아 다시 게시되지 않는 문제가 해결되었습니다.
* 컨테이너를 편집하면 하위 노드의 상속이 취소되는 MSM 상속 동작이 수정되었습니다.
* `fetchUrl`이 수정되어 한 컨테이너에서 다른 컨테이너로 블록을 이동하는 기능이 복원되었습니다.
