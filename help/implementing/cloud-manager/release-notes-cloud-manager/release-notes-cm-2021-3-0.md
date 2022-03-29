---
title: AEM as a Cloud Service 릴리스 2021.3.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.3.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: f826e0c6-3b1d-44f5-99a2-f792f5df3a55
source-git-commit: 95539851590456b6b5ecbfeb0df8fc7bc7dde74b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 1%

---

# Adobe Experience Manager as a Cloud Service 2021.3.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.3.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.3.0의 Cloud Manager 릴리스 날짜는 2021년 3월 11일입니다.

## Cloud Manager {#cloud-manager}

### 새로운 기능 {#what-is-new}

* 에 대한 기존 사용자 지정 도메인 이름 구성이 있는 환경이 있는 고객 [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) 및 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) 은 이전 기존 구성에 대한 메시지를 볼 수 있고 UI를 통해 자체 제공할 수 있습니다.

* 필수 권한이 있는 사용자는 이제 프로그램을 편집하여 셀프 서비스 방식으로 다음을 수행할 수 있습니다.
   * 자산을 사용하여 기존 프로그램에 사이트 솔루션을 추가하거나 그 반대로 추가합니다.
   * 사이트 및 자산을 모두 사용하는 기존 프로그램에서 사이트 또는 자산을 제거합니다.
   * 기존 프로그램 또는 새 프로그램으로 사용하지 않는 두 번째 솔루션 권한을 추가합니다.

* **AEM 푸시 업데이트** 이제 파이프라인 실행 및 활동 화면 모두에 대한 레이블이 표시됩니다.

* 환경이 최대 절전 모드이지만 AEM 업데이트도 사용 가능한 경우 **최대 절전 모드** 상태가 우선함 **업데이트 사용 가능**.

* 이제 사용자는 통합 셸의 사용자 프로필 아이콘(오른쪽 상단)으로 이동한 후 &#39;Cloud Manager 역할 보기&#39; 옵션을 선택하여 Cloud Manager 역할을 볼 수 있습니다.

* 레이블 **승인 신청** 의 레이블이 **프로덕션 승인** 더 명확해지려고

* 다음 **버전** 레이블의 레이블이 **Git 태그** 를 클릭합니다.

* 중요한 지표가 정의된 임계값을 충족하지 못할 때 동작을 정의하는 레이블을 실제 동작을 반영하도록 재설정했습니다. **즉시 취소** 및 **즉시 승인**.

* 클래스 및 메서드 사용 중단 목록이 버전을 기준으로 업데이트되었습니다 `2021.3.4997.20210303T022849Z-210225` AEM Cloud Service SDK의 구성 요소 중 하나를 선택합니다.

* 이제 Cloud Manager 프로덕션 파이프라인에 다음이 포함됩니다 [사용자 지정 UI 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) 기능.

### 버그 수정  {#bug-fixes}

* AEM 푸시 업그레이드 중에 일부 경우에 패키지 버전 관리를 건너뛰었습니다.

* 패키지가 다른 패키지에 포함된 경우 일부 품질 문제가 제대로 검색되지 않았습니다.

* 프로그램 추가 대화 상자를 열 때 생성되는 기본 프로그램 이름이 기존 프로그램 이름과 중복될 수 있습니다.

* 경우에 따라 사용자가 파이프라인을 시작한 후 바로 파이프라인 실행 페이지에서 나가는 경우 실행이 실제로 시작되지만 작업이 실패했음을 나타내는 오류 메시지가 표시됩니다.

* 고객 빌드에 잘못된 패키지가 발생하여 빌드 단계가 불필요하게 다시 시작되었습니다.

* 경우에 따라 해당 구성이 배포되지 허용 목록에 추가하다 않은 경우에도 IP 옆에 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* 모든 기존 프로덕션 파이프라인은 경험 감사 단계에서 자동으로 활성화됩니다.
