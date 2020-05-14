---
title: 클라우드 서비스로서의 Adobe Experience Manager 2020.5.0용 릴리스 노트
description: Experience Manager 2020.5.0용 릴리스 노트
translation-type: tm+mt
source-git-commit: 94a732f56929ad4af23855152e258f82ad61ee2c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 29%

---


# 클라우드 서비스 2020.5.0으로서의 AEM 릴리스 노트 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.5.0으로서의 Experience Manager에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## Cloud Manager {#cloud-manager}

클라우드 서비스로서의 AEM 릴리스 2020.5.0에 있는 Cloud Manager의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new}

* 고객이 Cloud Service로의 마이그레이션을 계획할 때 발생할 수 있는 문제를 식별하는 데 도움이 되는 6개의 코드 품질 규칙이 추가되었습니다.
* 호환성 관련 문제 수를 요약하기 위해 새로운 지표 *클라우드 서비스* 호환성이 추가되었습니다.
* 만들지 못한 환경은 이미 삭제되지 않은 경우 생성 실패 후 약 24시간 후에 자동으로 삭제됩니다.
* 활동 페이지 및 파이프라인 실행 목록 API의 성능이 개선되었습니다.
* 이제 코드 품질 로그에 예외에 대한 전체 스택 추적이 포함됩니다.

### 버그 수정  {#bug-fixes}

* 프로덕션 파이프라인이 실행되는 동안 잘못된 카드가 개요 페이지에 표시되었습니다.
* DontImplementOrExtendProviderTypesPomCheck ** 코드 품질 규칙은 경우에 따라 Null 포인터 예외를 만들 수 있습니다.
* 개요 페이지의 일부 설명서 링크가 제대로 작동하지 않았습니다.
* Safari에서 환경 만들기 대화 상자가 올바르게 렌더링되지 않았습니다.
* 개요 페이지의 특정 카드에 개체 이름이 올바로 표시되지 않았습니다.
* 경우에 따라 빌드 이미지가 고객 패키지를 다운로드하지 못할 수도 있습니다.

