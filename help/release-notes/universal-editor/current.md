---
title: 범용 편집기 2025.10.30 릴리스 정보
description: 다음은 범용 편집기 2025.10.30 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: e3e571bef450ddc09eb30ab7d73b144ea521a87b
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 58%

---


# 범용 편집기 2025.10.30 릴리스 정보 {#release-notes}

유니버설 편집기의 2025년 10월 30일 릴리스에 대한 릴리스 정보입니다.

>[!TIP]
>
>릴리스하기 전에 **예정된** 범용 편집기 기능을 테스트하려면 [범용 편집기 미리보기 릴리스 정보](/help/release-notes/universal-editor/preview.md)를 참조하십시오.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* [새 RTE](#new-rte)에서 이제 이미지를 삽입할 수 있습니다.
   * 이 기능은 OOtB에서 비활성화되며 [필터 정의를 통해 명시적으로 활성화해야 합니다.](/help/implementing/universal-editor/configure-rte.md#toolbar)

## 얼리 어답터 기능 {#early-adopter}

이들 출시 예정인 기능을 테스트하고 피드백을 공유하는 데 관심이 있다면 Adobe ID와 연결된 이메일 주소로 Adobe 고객 성공 관리자에 이메일을 보내 주십시오.

### 새 RTE {#new-rte}

링크 대화 상자에 페이지 선택기가 있는 새로운 ProseMirror RTE를 이제 오른쪽 패널에서 사용할 수 있습니다. [이 RTE는 유연한 구성 옵션을 제공합니다.](/help/implementing/universal-editor/configure-rte.md)

## 기타 개선 사항 {#other-improvements}

* 작업이 실행 취소된 경우 이제 업데이트 이벤트에 대한 알림이 표시됩니다.
* `No results` 문자열은 이제 범용 편집기 태그의 브라우저 로캘에 따라 다릅니다.
* 유니버설 편집기의 게시 단추에 있는 추가 줄 바꿈을 수정했습니다.
* API 패치를 정리했습니다.
* 이제 콘텐츠 선택 버튼이 Safari에 표시됩니다.
* RPM 빌드가 수정되었습니다.
* 저장한 후 텍스트 편집 텍스트가 다시 업데이트되지 않도록 CORS를 업데이트합니다.
