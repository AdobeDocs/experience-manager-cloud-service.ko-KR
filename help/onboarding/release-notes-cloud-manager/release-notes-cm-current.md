---
title: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2021.4.0
description: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2021.4.0
feature: 릴리스 정보
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
translation-type: tm+mt
source-git-commit: 69694f2067c53667803d38bbf7bc752f3b3afac6
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---

# Adobe Experience Manager에서 Cloud Service 2021.4.0 {#release-notes}으로 Cloud Manager에 대한 릴리스 노트

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2021.4.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

Cloud Service 2021.4.0인 AEM의 Cloud Manager에 대한 릴리스 날짜는 2021년 4월 08일입니다.
다음 릴리스는 2021년 5월 6일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-april}

* 프로그램 추가 및 편집 워크플로우에 대한 UI 업데이트를 통해 보다 직관적으로 만들 수 있습니다.

* 이제 필요한 권한을 가진 사용자는 UI를 통해 상거래 끝점을 제출할 수 있습니다.

* 이제 환경 변수의 범위가 작성자 또는 게시와 같은 특정 서비스로 지정될 수 있습니다. AEM 버전 `2021.03.5104.20210328T185548Z` 이상이 필요합니다.

* 파이프라인이 구성되지 않은 경우에도 **Git** 관리 단추가 파이프라인 카드에 표시됩니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 27로 업데이트되었습니다.

* Cloud Manager에서 만든 Adobe I/O 개발자 콘솔의 프로젝트는 더 이상 의도치 않게 편집하거나 삭제할 수 없습니다.

* 사용자가 새 환경을 추가하면 환경을 만들면 다른 영역으로 이동할 수 없다는 메시지가 표시됩니다.

* 이제 환경 변수의 범위가 작성자 또는 게시와 같은 특정 서비스로 지정될 수 있습니다. AEM 버전 2021.03.5104.20210328T185548Z 이상이 필요합니다.

* 환경이 삭제되었을 때 파이프라인을 시작할 때의 오류 메시지가 명확해졌습니다.

* 이제 Eclipse 프로젝트에서 제공하는 OSGi 번들은 규칙 `CQBP-84--dependencies`에서 제외됩니다.

### 버그 수정 {#bug-fixes-cm-april}

* 파이프라인의 경험 감사 페이지를 편집할 때 슬래시(`( / )`)로 시작하는 입력 경로가 더 이상 보류 중인 상태로 돌아가지 않습니다.

* 새 프로덕션 파이프라인이 생성되면 사용자가 컨텐츠 감사 재정의를 추가하지 않은 경우 기본 홈 페이지가 감사되지 않았습니다.

* 다운로드 가능한 문제 CSV 파일에서 `CloudServiceIncompatibleWorkflowProcess` 문제의 심각도가 잘못되었습니다.

* `Runmode` 검사가 비폴더 노드에서 잘못된 양수를 생성하고 있었습니다.