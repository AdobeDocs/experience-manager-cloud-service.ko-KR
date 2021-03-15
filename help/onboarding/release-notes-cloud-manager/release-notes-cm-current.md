---
title: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2021.3.0
description: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2021.3.0
translation-type: tm+mt
source-git-commit: c6fe5e9dab0e119271c6cea272dddabe7babb1e4
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---


# Adobe Experience Manager에서 Cloud Service 2021.3.0 {#release-notes}으로 Cloud Manager에 대한 릴리스 노트

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2021.3.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM에서 Cloud Service 2021.3.0으로 Cloud Manager의 릴리스 날짜는 2021년 3월 11일입니다.
다음 릴리스는 2021년 4월 8일에 예정되어 있습니다.

## Cloud Manager {#cloud-manager}

### 새로운 기능 {#what-is-new}

* [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) 및 [사용자 정의 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn)에 대해 기존 사용자 정의 도메인 이름 구성을 가진 환경을 사용하는 고객은 기존 구성에 대한 메시지를 볼 수 있으며 UI를 통해 직접 제공할 수 있습니다.

* 이제 필요한 권한을 가진 사용자는 셀프 서비스 방식으로 프로그램을 편집할 수 있습니다.
   * 자산(또는 그 반대로)이 있는 기존 프로그램에 사이트 솔루션을 추가합니다.
   * 사이트 및 자산을 모두 포함하는 기존 프로그램에서 사이트(또는 자산)를 제거합니다.
   * 기존 프로그램 또는 새 프로그램으로 사용하지 않은 두 번째 솔루션 권한을 추가합니다.

* **이제** 파이프라인 실행과 활동 화면 모두에 대해 AEM 푸시 업데이트 프로그램이 표시됩니다.

* 환경이 최대 절전 모드이지만 사용 가능한 AEM 업데이트도 있는 경우 **최대 절전 모드** 상태가 **사용 가능한 업데이트**&#x200B;보다 우선합니다.

* 이제 사용자는 통합 셸의 사용자 프로필 아이콘(오른쪽 상단)으로 이동한 후 &#39;클라우드 관리자 역할 보기&#39; 옵션을 선택하여 클라우드 관리자 역할을 볼 수 있습니다.

* 레이블 **승인 신청**&#x200B;이(가) **프로덕션 승인**&#x200B;으로 다시 표시되었습니다.

* **버전** 레이블은 프로덕션 파이프라인 실행 화면에서 **Git 태그**&#x200B;에 다시 표시되었습니다.

* 중요한 지표가 정의된 임계값에 도달하지 못할 때 동작을 정의하는 레이블의 실제 행동을 반영하도록 레이블을 재정의했습니다.**즉시 취소** 및 **즉시 승인**.

* 클래스 및 메서드 사용 중단 목록은 AEM Cloud Service SDK의 `2021.3.4997.20210303T022849Z-210225` 버전을 기준으로 업데이트되었습니다.

* 이제 클라우드 관리자 프로덕션 파이프라인에 [사용자 지정 UI 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) 기능이 포함됩니다.

### 버그 수정  {#bug-fixes}

* AEM 푸시 업그레이드 중에 일부의 경우 패키지 버전 관리를 건너뛰었습니다.

* 패키지가 다른 패키지에 포함된 경우 일부 품질 문제를 제대로 찾지 못했습니다.

* 프로그램 추가 대화 상자를 열 때 생성된 기본 프로그램 이름이 기존 프로그램 이름과 중복될 수 있습니다.

* 때때로 사용자가 파이프라인을 시작한 직후 파이프라인 실행 페이지를 벗어나는 경우 작업이 실패했지만 실제로 실행이 시작된다는 오류 메시지가 표시됩니다.

* 고객 빌드로 인해 잘못된 패키지가 발생했을 때 빌드 단계가 불필요하게 다시 시작되었습니다.

* 경우에 따라 해당 구성이 배포되지 허용 목록에 추가하다 않았더라도 IP 옆에 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* 모든 기존 프로덕션 파이프라인은 경험 감사 단계를 통해 자동으로 활성화됩니다.