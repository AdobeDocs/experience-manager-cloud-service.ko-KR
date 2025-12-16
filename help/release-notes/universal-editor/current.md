---
title: 범용 편집기 2025.12.12 릴리스 정보
description: 다음은 범용 편집기 2025.12.11 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b7b89587a81d0cadc81d4b2a486c022557c4a9fb
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 21%

---


# 범용 편집기 2025.12.12 릴리스 정보 {#release-notes}

다음은 범용 편집기 2025년 12월 12일 릴리스의 릴리스 정보입니다.

>[!TIP]
>
>릴리스하기 전에 **예정된** 범용 편집기 기능을 테스트하려면 [범용 편집기 미리보기 릴리스 정보](/help/release-notes/universal-editor/preview.md)를 참조하십시오.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* [리치 텍스트 편집기의 기존 표에 지원이 추가되었습니다.](/help/sites-cloud/authoring/universal-editor/authoring.md#formatting-options)
* [서식 있는 텍스트 편집기의 중첩 목록에 대해 Tab 키를 사용하도록 설정했습니다.](/help/sites-cloud/authoring/universal-editor/authoring.md#formatting-options)
* 이제 [meta 태그 `aem-dev-login`을(를) 통해 개발자 로그인 기능을 사용하지 않도록 설정할 수 있습니다.](/help/implementing/universal-editor/customizing.md#meta-tags)
* 이제 오버레이 섹션을 마우스 오른쪽 단추로 클릭하면 [상황에 맞는 옵션 메뉴가 표시됩니다.](/help/sites-cloud/authoring/universal-editor/authoring.md#context-options)
* [범위 들여쓰기](/help/implementing/universal-editor/configure-rte.md#indentation)가 이제 [서식 있는 텍스트 편집기에서 지원됩니다.](/help/sites-cloud/authoring/universal-editor/authoring.md#formatting-options)

## 얼리 어답터 기능 {#early-adopter}

아래 나열된 예정된 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 이메일 주소에서 Adobe Customer Success Manager에게 이메일을 보내십시오.

* 콘텐츠 조각에 대해 약식 복사가 구현되었습니다.

## 기타 개선 사항 {#other-improvements}

* 이제 다중 필드가 컨텍스트에서 변경되면 속성 레일이 동기화됩니다.
* 이제 AEM 6.5 인스턴스에서 예상대로 콘텐츠 조각 선택기가 열립니다.
* 이제 Esc 키를 누르면 리치 텍스트 편집기의 대화 상자가 닫힙니다.
* 이제 구성 요소를 선택한 경우에만 **구성 요소 제거** 작업을 사용할 수 있습니다.
* 이제 사용된 인스턴스를 기반으로 올바른(이전 또는 새) 콘텐츠 조각 편집기가 열립니다(호스트 이름이 AEM as a Cloud Service 패턴인 경우 새 편집기를 사용하고 그렇지 않으면 기존 편집기를 사용).
* 중복 작업에 필터 유효성 검사가 추가됩니다.
* 이제 속성 레일에서 긴 제목이 잘립니다.
* 이제 값이 10개가 넘는 다중 사이트 관리자 배열이 제대로 처리됩니다.
* 이름이 같은 여러 구성 요소를 만들 때 발생하는 충돌 오류가 이제 제대로 처리됩니다.
* 값이 10보다 큰 다중 사이트 관리자 배열 처리가 추가되었습니다.
