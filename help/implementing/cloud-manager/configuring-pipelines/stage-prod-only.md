---
title: 스테이지 전용 및 프로덕션 전용 파이프라인 분할
description: 전용 파이프라인을 사용하여 스테이징 및 프로덕션 배포를 분할하는 방법에 대해 알아보십시오.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#staging-production-only-pipelines"
hide: true
hidefromtoc: true
index: false
exl-id: 7d76a87c-122c-4c4d-8071-957bef4c9cf1
source-git-commit: 51318172b826eb81dff86b3e8dfb6f2ded648c4c
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 48%

---

# 스테이지 전용 및 프로덕션 전용 파이프라인 분할 {#stage-prod-only}

전용 파이프라인을 사용하여 스테이징 및 프로덕션 배포를 분할할 수 있습니다.

## 개요 {#overview}

스테이징 환경과 프로덕션 환경은 긴밀하게 결합되어 있습니다. 기본적으로 이에 대한 배포는 단일 파이프라인에 연결됩니다. 이는 해당 프로그램의 스테이징 환경과 프로덕션 환경 모두에 배포되는 배포 파이프라인입니다. 이 결합은 일반적으로 적합하지만 단점이 있는 특정 사용 사례가 있습니다.

* 스테이징 전용에 배포하려면 파이프라인에서 **프로덕션으로 승격** 단계를 거부합니다. 그러나 실행은 취소된 것으로 표시됩니다.
* 스테이징 환경에서 최신 코드를 프로덕션에 배포하려면 코드가 변경되지 않았더라도 스테이징 배포를 포함한 전체 파이프라인을 다시 배포해야 합니다.
* 배포 중에는 환경을 업데이트할 수 없습니다. 프로덕션으로 승격하기 전에 며칠 동안 스테이징 환경에서 테스트를 일시 중지하면 프로덕션 환경이 잠긴 상태로 유지되어 업데이트할 수 없습니다. 이 시나리오로 인해 [환경 변수](/help/implementing/cloud-manager/environment-variables.md) 업데이트와 같은 비의존적인 작업이 불가능합니다.

스테이징 전용 및 프로덕션 전용 파이프라인은 전용 배포 옵션을 제공하여 이러한 사용 사례에 대한 솔루션을 제공합니다.

* **스테이징 전용 파이프라인**&#x200B;은 배포 및 테스트가 완료되면 실행이 완료된 스테이징 환경에만 배포됩니다. 스테이징 전용 파이프라인은 표준 결합 전체 스택 프로덕션 파이프라인과 동일하게 작동하지만 프로덕션 배포 단계(승인, 예약, 배포)는 수행하지 않습니다.
* **프로덕션 전용 배포 파이프라인:** 가장 최근의 성공적인 단계 실행을 선택하여 프로덕션에만 배포합니다. 그런 다음 아티팩트를 프로덕션에 배포합니다. 프로덕션 전용 파이프라인은 배포 아티팩트를 재사용하여 빌드 단계를 우회합니다.

전체 스택 프로덕션 파이프라인이 실행되는 동안에는 스테이징 전용 및 프로덕션 전용 파이프라인이 실행되지 않으며 그 반대의 경우도 마찬가지입니다. 단계 전용 및 전체 스택 프로덕션 파이프라인 모두 **Git 변경 시** 트리거가 구성되며 동일한 분기 및 저장소를 가리키는 경우 단계 전용 파이프라인만 자동으로 시작됩니다. 프로덕션 전용 파이프라인은 저장소에 직접 연결되지 않기 때문에 **`On Git Changes`**&#x200B;를 시작하지 않습니다.

프로덕션 전용 파이프라인이 수동으로 트리거되지 않으므로 **Git 변경 시** 저장소에 직접 연결되지 않습니다.

이러한 전용 파이프라인은 보다 유연한 기능을 제공하지만 작동 및 권장 사항에 대한 다음 세부 정보를 참고해야 합니다.

>[!NOTE]
>
>프로덕션 전용 파이프라인은 항상 스테이징 전용 파이프라인의 아티팩트를 사용합니다. 이 프로세스는 표준 결합 프로덕션 파이프라인이 그 사이에 다른 것을 스테이징하기 위해 배포한 경우에도 동일하게 적용됩니다.
>
>* 이런 시나리오는 원치 않는 코드 롤백이 발생할 수 있습니다.
>* Adobe에서는 프로덕션 전용 파이프라인과 스테이징 전용 파이프라인을 사용하기 시작한 후에는 표준 결합 프로덕션 파이프라인 사용을 중지할 것을 권장합니다.
>* 여전히 표준 결합 파이프라인과 스테이징/프로덕션 전용 파이프라인을 모두 실행하려는 경우 코드 롤백을 방지하기 위해 아티팩트를 재사용하는 것을 염두에 두어야 합니다.

## 파이프라인 만들기 {#pipeline-creation}

프로덕션 전용 및 스테이징 전용 파이프라인은 표준 결합 [프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 및 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)과 유사한 방식으로 생성됩니다. 자세한 내용은 해당 문서를 참조하십시오.

1. **파이프라인** 창에서 **파이프라인 추가**&#x200B;를 클릭합니다.

   * **비프로덕션 파이프라인 추가**&#x200B;를 선택하여 [스테이지 전용 파이프라인을 만듭니다](#stage-only).
   * **프로덕션 전용 파이프라인 추가**&#x200B;를 선택하여 [프로덕션 전용 파이프라인을 생성](#prod-only)합니다.

![프로덕션/스테이징 전용 파이프라인 만들기](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-stage-pipeline.png)

>[!NOTE]
>
>해당 파이프라인이 이미 있다면 특정 옵션이 회색으로 표시될 수 있습니다.
>
>* 스테이징 전용 파이프라인이 아직 없으면 **프로덕션 전용 파이프라인 추가**&#x200B;를 사용할 수 없습니다.
>* 표준 결합 파이프라인이 이미 있으면 **프로덕션 파이프라인 추가**&#x200B;를 사용할 수 없습니다.
>* 프로그램당 하나의 프로덕션 전용 파이프라인과 하나의 스테이징 전용 파이프라인만 허용됩니다.

### 스테이지 전용 파이프라인 만들기 {#stage-only}

1. **비프로덕션 파이프라인 추가** 대화 상자의 **구성** 탭에서 파이프라인의 **배포 파이프라인** 필드를 선택합니다.
1. 비프로덕션 파이프라인 이름 필드에 자유 텍스트 이름을 입력합니다.
1. 원하는 배포 옵션을 선택한 다음 **계속**&#x200B;을 클릭합니다.

   ![비프로덕션 파이프라인 추가 대화 상자의 구성 탭](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-1.png)

1. **Source 코드** 탭에서 **전체 스택 코드**&#x200B;을(를) 선택합니다. 이 옵션은 전체 AEM 애플리케이션(백엔드, Dispatcher/웹 계층 구성 및 리포지토리의 모든 프론트엔드 모듈)을 빌드하고 배포합니다.

1. **적합한 배포 환경** 드롭다운 목록에서 **단계** 환경을 파이프라인의 배포 환경으로 선택합니다. 단계를 선택하면 단계 환경 전용 파이프라인이 만들어집니다(프로덕션 프로모션은 별도의 파이프라인을 통해 수행됨).

1. 각 드롭다운 목록에서 **저장소** 및 **Git 분기**&#x200B;를 선택한 다음 **계속**&#x200B;을 클릭합니다.

   ![비프로덕션 파이프라인 추가 대화 상자의 Source 코드 탭](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-2.png)

1. **경험 감사** 탭에서 지정된 사이트 URL은 Cloud Manager에서 페이지 품질을 감사하는 게시된 URL입니다.

1. **페이지 경로** 필드에서 감사할 페이지를 지정한 다음 **![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) 페이지 추가**&#x200B;를 클릭합니다.

   경험 감사는 성능, 접근성, 점진적 웹 앱, 모범 사례, SEO 및 기타 품질 검사를 위해 추가하는 각 경로를 분석합니다. ![교차 크기 400 아이콘](https://spectrum.adobe.com/static/icons/ui_18/CrossSize400.svg)을 클릭하여 여러 경로를 추가하고 제거할 수 있습니다.

   ![비프로덕션 파이프라인 추가 대화 상자의 경험 감사 탭](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-3.png)

1. **저장**&#x200B;을 클릭합니다.


### 프로덕션 전용 파이프라인 생성 {#prod-only}

1. **프로덕션 전용 파이프라인 추가** 대화 상자의 **파이프라인 이름** 텍스트 필드에 파이프라인의 자유 텍스트 이름을 입력합니다.
1. **파이프라인 이름** 필드에 원하는 이름을 입력합니다.
1. **프로덕션 배포 옵션**&#x200B;에서 **프로덕션에 배포하기 전에 일시 중지**&#x200B;를 선택합니다.

   이 옵션은 프로덕션 단계 바로 앞에 수동 승인 게이트를 삽입합니다. 파이프라인은 승인자(예: 배포 관리자 또는 비즈니스 소유자)가 프로덕션 배포를 승인하거나 취소할 때까지 중지되고 기다립니다.

   변경 제어 또는 마지막 확인 시 를 사용합니다.

1. 이러한 옵션을 사용하여 프로덕션 전용 파이프라인을 만들려면 **저장**&#x200B;을 클릭합니다.

   ![프로덕션 전용 파이프라인 만들기](/help/implementing/cloud-manager/configuring-pipelines/assets/add-production-only-pipeline.png)

## 스테이지 전용 및 프로덕션 전용 파이프라인 실행 {#running}

[다른 파이프라인과 같이](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) 새 파이프라인을 시작할 수 있습니다. 스테이지 전용 파이프라인의 실행 세부 정보에서 직접 프로덕션 전용 파이프라인을 트리거할 수도 있습니다.

<!-- * Stage-only and prod-only pipelines offer a new [emergency mode](#emergency-mode) to skip testing.
Prod-only pipeline run can be triggered directly from the execution details of a [stage-only pipeline](#stage-only-run).


### Emergency Mode {#emergency-mode}

When starting production-only and staging-online pipelines, you are prompted to confirm the start and how it starts.

* **Normal Mode** is a standard run and includes stage testing steps.
* **Emergency Mode** skips stage testing steps.

![Emergency Mode](/help/assets/configure-pipelines/emergency-mode.png) -->

### 스테이지 전용 파이프라인 실행 {#stage-only-run}

테스트 단계 후에 실행 세부 정보에 **빌드 승격** 단추가 나타납니다. 이 실행의 스테이지 아티팩트를 프로덕션에 배포하는 프로덕션 전용 파이프라인을 트리거하려면 이 플러그인을 클릭합니다. 이 단추는 최근에 성공한 스테이지 전용 실행에서만 표시됩니다.

![스테이징 전용 파이프라인 실행](/help/implementing/cloud-manager/configuring-pipelines/assets/stage-only-pipelines-run.png)

**빌드 홍보**&#x200B;를 클릭하면 관련 프로덕션 전용 파이프라인의 실행을 확인하는 대화 상자가 열립니다. 시작하려면 **실행**&#x200B;을 클릭하세요.

![빌드 승격 - 파이프라인 실행 대화 상자](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-run.png)

아무 것도 없는 경우 셋업(Setup) 대화상자가 나타납니다.

![빌드 승격 - 올바른 파이프라인 대화 상자가 없음](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-no-valid-pipeline.png)


### 프로덕션 전용 파이프라인 실행 {#prod-only-run}

**프로덕션 전용** 파이프라인의 경우 Cloud Manager은 프로덕션에 배포된 소스 아티팩트를 표시합니다. 소스 실행에 대한 **아티팩트 준비** 단계를 확인한 다음 열어 세부 정보와 로그를 확인합니다.


![아티팩트 세부 정보](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-only-pipelines-run.png)
