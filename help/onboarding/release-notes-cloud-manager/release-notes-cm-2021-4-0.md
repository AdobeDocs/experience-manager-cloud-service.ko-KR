---
title: AEM as a Cloud Service 릴리스 2021.4.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.4.0의 Cloud Manager 릴리스 노트
feature: 릴리스 정보
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---


# Adobe Experience Manager as a Cloud Service 2021.4.0 {#release-notes} 의 Cloud Manager 릴리스 노트

이 페이지에서는 AEM as a Cloud Service 2021.4.0 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.4.0의 Cloud Manager 릴리스 날짜는 2021년 4월 8일입니다.
다음 릴리스는 2021년 5월 6일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-april}

* 프로그램 추가 및 편집 워크플로우에 대한 UI를 업데이트하여 보다 직관적으로 사용할 수 있습니다.

* 이제 필요한 권한이 있는 사용자는 UI를 통해 상거래 종료 지점을 제출할 수 있습니다.

* 이제 환경 변수 범위를 특정 서비스(작성자 또는 게시)로 지정할 수 있습니다. AEM 버전 `2021.03.5104.20210328T185548Z` 이상이 필요합니다.

* 파이프라인이 구성되지 않은 경우에도 **Git** 관리 단추가 파이프라인 카드에 표시됩니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 27로 업데이트되었습니다.

* Cloud Manager에서 만든 Adobe I/O 개발자 콘솔의 프로젝트는 더 이상 실수로 편집하거나 삭제할 수 없습니다.

* 사용자가 새 환경을 추가하면 환경이 만들어지면 다른 지역으로 이동할 수 없다는 메시지가 표시됩니다.

* 이제 환경 변수 범위를 특정 서비스(작성자 또는 게시)로 지정할 수 있습니다. AEM 버전 2021.03.5104.20210328T185548Z 이상이 필요합니다.

* 환경이 삭제되었을 때 파이프라인을 시작할 때 오류 메시지가 명확해졌습니다.

* Eclipse 프로젝트에서 제공하는 OSGi 번들은 이제 규칙 `CQBP-84--dependencies`에서 제외됩니다.

### 버그 수정 {#bug-fixes-cm-april}

* 파이프라인의 경험 감사 페이지를 편집할 때 슬래시 `( / )`으로 시작하는 입력 경로는 더 이상 단계가 보류 중인 상태로 고정되지 않습니다.

* 새 프로덕션 파이프라인이 생성될 때 사용자가 컨텐츠 감사 무시를 추가하지 않으면 기본 홈 페이지가 감사되지 않습니다.

* 다운로드 가능한 문제 CSV 파일에서 `CloudServiceIncompatibleWorkflowProcess`에 대한 문제에 잘못된 심각도가 있었습니다.

* `Runmode` 검사에서 비폴더 노드에서 긍정 오류(false positive)가 발생했습니다.