---
title: 범용 편집기 2025.06.19 릴리스 정보
description: 다음은 범용 편집기 2025.06.19 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 5ffae9e548ca952975b3ea805808e227102ec99f
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 26%

---


# 범용 편집기 2025.06.19 릴리스 정보 {#release-notes}

유니버설 편집기 2025년 6월 19일 릴리스의 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **속성 레일의 다중 필드 지원** -
  [컨테이너 구성 요소](/help/implementing/universal-editor/field-types.md#container)를 사용하여 다중 필드 속성을 만들 수 있습니다.
* **중첩된 속성 지원** - 이제 [`name` 필드](/help/implementing/universal-editor/field-types.md#nesting)에서 속성 중첩을 사용하도록 설정하는 경로를 지원합니다.
* **크기 조정 가능한 오른쪽 패널** - 이제 측면 패널에 표시되는 더 긴 콘텐츠를 더 잘 고려할 수 있도록 측면 패널의 크기를 조정할 수 있습니다.

## 조기 채택 기능 {#early-adopter}

예정된 기능을 테스트하려면 Adobe의 얼리 어답터 프로그램에 참여하십시오.

### **실행 취소/다시 실행** {#undo-redo}

이제 범용 편집기 콘텐츠 작성자는 실행 취소 및 다시 실행을 사용할 수 있습니다.

* 여기에는 컨텍스트에서 수행한 편집, 속성 패널을 통해 수행한 편집, 블록 추가(또는 복제), 이동 및 삭제가 포함됩니다.
* 실행 취소 및 다시 실행은 현재 브라우저 세션으로 제한됩니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 Adobe 고객 성공 관리자에 이메일을 보내주십시오.

## 기타 개선 사항 {#other-improvements}

* 컨테이너 간 블록 이동 시 리소스 키 충돌 오류가 수정되었습니다.
* 컨테이너의 마지막 블록 복제에 실패하는 문제가 수정되었습니다.
* 이제 작업 추가 드롭다운에 `component-definition.json` 파일에 적절한 플러그인이 정의된 구성 요소만 나열됩니다.
* 게시 대화 상자에서 사용한 수정 날짜가 수정되었습니다. 일부 환경에서는 페이지가 수정된 것으로 인식되지 않고 다시 게시되지 않았습니다.
* 컨테이너를 편집하여 하위 노드의 상속을 취소한 MSM 상속 비헤이비어를 수정했습니다.
* `fetchUrl`이(가) 수정되어 한 컨테이너에서 다른 컨테이너로 이동 블록이 복원되었습니다.
