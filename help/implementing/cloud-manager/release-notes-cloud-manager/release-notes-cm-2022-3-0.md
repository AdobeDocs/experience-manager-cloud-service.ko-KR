---
title: Adobe Experience Manager as a Cloud Service Cloud Manager 2022.3.0의 릴리스 노트
description: 다음은 AEM as a Cloud Service의 Cloud Manager 2022.3.0에 대한 릴리스 노트입니다.
feature: Release Information
exl-id: d09d48c5-6e0a-4a6a-85e9-1a60fdd6e5bf
source-git-commit: 68586304724530f83649cffee76cefef3e1c8627
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Experience Manager as a Cloud Service Cloud Manager 2022.3.0의 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.3.0에 대한 릴리스 노트를 문서화합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2022.3.0의 출시일은 2022년 3월 10일입니다. 다음 릴리스는 2022년 4월 7일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 개발자 역할을 사용하여 AEM 환경 로그에 액세스할 수 있습니다.

## 버그 수정 {#bug-fixes}

* Git 저장소 하위 집합에 잘못된 이름 값이 있으면 빌드 아티팩트 재사용 기능이 무효화됩니다. 이들 저장소 이름이 변경되어 Cloud Manager API/UI에 수정한 이름이 표시됩니다.
* 비프로덕션 파이프라인의 빌드 아티팩트가 프로덕션 전체 스택 파이프라인에서 부적절하게 재사용되었습니다.
* 코드 품질 파이프라인을 추가 또는 편집하는 경우 지표 오류를 처리할 옵션이 더 이상 표시되지 않습니다.
* 빌드 단계에서 예기치 않은 일부 파이프라인 변수가 발생할 수 있습니다.
