---
title: 클라우드 서비스로서의 Adobe Experience Manager 2020.5.0용 릴리스 노트
description: Experience Manager 2020.5.0용 릴리스 노트
translation-type: tm+mt
source-git-commit: 3dc0d1d77595f7b3e890fb4b390eef5bcf84ecd8
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 96%

---


# 클라우드 서비스 2020.5.0으로서의 AEM 릴리스 노트 {#release-notes}

이 페이지에서는 Experience Manager에 대한 일반 릴리스 노트를 Cloud Service 2020.5.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

클라우드 서비스 2020.5.0으로서의 [!DNL Experience Manager]의 출시일은 2020년 5월 7일입니다.

## AEM Sites의 새로운 기능 {#aem-sites}

클라우드 서비스로서의 AEM 릴리스 2020.5.0에 있는 AEM Sites의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

* 이제 일괄 처리 페이지 이동 및 롤아웃을 비동기 작업으로 처리한 후 자세한 작업 정보를 사용할 수 있습니다.
* 페이지 트리를 복사/붙여넣기할 때 이제 루트 페이지만 붙여넣거나 트리의 하위 페이지를 선택할 수 있습니다.
* Adobe Target 작업 영역으로 내보낸 AEM 경험 구성 요소는 이제 Target에서 고유한 오퍼 유형 및 오퍼 소스로 표시됩니다.
* MSM - *게시* 트리거를 사용하면 이제 Live Copy 소스에서 삭제된 Live Copy 구성 요소의 삭제 이벤트를 성공적으로 롤아웃합니다.
* MSM - Live Copy 구성 요소의 이름이 Live Copy 소스에서 동일한 구성 요소 롤아웃 후 *_msm_moved*&#x200B;로 변경되었습니다.


## Cloud Manager의 새로운 기능 {#cloud-manager}

클라우드 서비스로서의 AEM 릴리스 2020.5.0에 있는 Cloud Manager의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new}

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


