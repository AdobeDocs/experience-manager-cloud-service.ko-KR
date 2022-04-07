---
title: Adobe Experience Manager as a Cloud Service Cloud Manager 2022.3.0의 릴리스 노트
description: 다음은 AEM as a Cloud Service의 Cloud Manager 2022.3.0에 대한 릴리스 노트입니다.
feature: Release Information
source-git-commit: 437be8c82a4dee6c9e56af09afa7e9048c8cb3c0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 3%

---


# Adobe Experience Manager as a Cloud Service Cloud Manager 2022.3.0의 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.3.0에 대한 릴리스 노트를 문서화합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 10의 Cloud Manager 릴리스 2022.3.0에 대한 릴리스 날짜(2022년 3월) 다음 릴리스는 2022년 4월 7일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* AEM 환경 로그에 액세스하는 작업은 개발자 역할을 사용하여 수행할 수 있습니다.

## 버그 수정 {#bug-fixes}

* 수동으로 만든 Git 리포지토리의 하위 집합에 잘못된 이름 값이 있어서 작성 객체 재사용 기능이 적용되지 않았습니다. 이러한 리포지토리의 이름이 변경되었으며 사용자는 Cloud Manager API/UI에서 수정된 이름을 볼 수 있습니다.
* 비프로덕션 파이프라인의 빌드 아티팩트가 프로덕션 전체 스택 파이프라인에서 잘못 재사용되었습니다.
* 코드 품질 파이프라인을 추가하거나 편집할 때 지표 오류를 처리하는 옵션이 더 이상 표시되지 않습니다.
* 일부 예기치 않은 파이프라인 변수 구성이 빌드 단계에서 발생할 수 있습니다.
