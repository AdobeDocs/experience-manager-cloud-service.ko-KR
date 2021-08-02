---
title: AEM as a Cloud Service 릴리스 2020.5.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2020.5.0의 Cloud Manager 릴리스 노트
feature: 릴리스 정보
exl-id: 9f534858-d18f-4224-8b94-9583a05aed95
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 71%

---

# Adobe Experience Manager as a Cloud Service 2020.5.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2020.5.0 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2020.5.0의 Cloud Manager 릴리스 날짜는 2020년 5월 7일입니다.

## 새로운 기능 {#whats-new-cloud-manager}

* 고객이 클라우드 서비스로의 마이그레이션을 계획할 때 발생할 수 있는 문제를 식별하는 데 도움이 되는 6개의 추가 코드 품질 규칙이 추가되었습니다.
* 호환성 관련 문제 수를 요약하기 위해 새로운 지표 *Cloud Service 호환성*&#x200B;이 추가되었습니다.
* 만들지 못한 환경은 이미 삭제되지 않은 경우 이제 생성 실패 후 약 24시간 후에 자동으로 삭제됩니다.
* 활동 페이지 및 파이프라인 실행 목록 API의 성능이 개선되었습니다.
* 이제 코드 품질 로그에 예외에 대한 전체 스택 추적이 포함됩니다.

### 버그 수정  {#bug-fixes}

* 프로덕션 파이프라인이 실행되는 동안 잘못된 카드가 개요 페이지에 표시되었습니다.
* *DontImplementOrExtendProviderTypesPomCheck* 코드 품질 규칙은 경우에 따라 Null 포인터 예외를 생성할 수 있습니다.
* 개요 페이지의 일부 설명서 링크가 제대로 작동하지 않았습니다.
* Safari에서 환경 만들기 대화 상자가 올바르게 렌더링되지 않았습니다.
* 개요 페이지의 특정 카드에 개체 이름이 올바로 표시되지 않았습니다.
* 일부 경우, 이미지 작성에서 고객 패키지를 제대로 다운로드하지 못했습니다.
