---
title: 롤아웃 충돌
description: 다중 사이트 관리자 롤아웃 충돌을 관리하고 해결하는 방법을 알아봅니다.
feature: 다중 사이트 관리자
role: Admin
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 2%

---

# 롤아웃 충돌 {#msm-rollout-conflicts}

블루프린트 분기와 종속 Live Copy 분기 모두에서 동일한 페이지 이름을 사용하는 새 페이지가 생성되면 충돌이 발생할 수 있습니다. 이러한 충돌은 롤아웃 시 처리하고 해결해야 합니다.

## 충돌 처리 {#conflict-handling}

페이지가 충돌하는 경우(블루프린트 및 Live Copy 분기에) MSM을 사용하여 페이지가 처리되는 방식을 정의할 수 있습니다(또는 처리되는 경우에도).

롤아웃이 차단되지 않도록 하기 위해 가능한 정의는 다음과 같습니다.

* 롤아웃 중 우선 순위가 있는 페이지(블루프린트 또는 Live Copy)는 무엇입니까
* 어떤 페이지의 이름을 바꿀(및 방법)
* 게시된 콘텐츠에 어떻게 영향을 줍니까

기본적으로 AEM의 기본 동작은 게시된 컨텐츠는 영향을 받지 않습니다. 따라서 Live Copy 분기에서 수동으로 만든 페이지가 게시되었더라도 충돌 처리 및 롤아웃 후에도 해당 컨텐츠가 계속 게시됩니다.

표준 기능 외에 사용자 지정된 충돌 처리기를 추가하여 다른 규칙을 구현할 수 있습니다. 작업을 개별 프로세스로 게시할 수도 있습니다.

### 예제 시나리오 {#example-scenario}

다음 섹션에서는 블루프린트와 Live Copy 분기(수동으로 생성됨)에서 만들어진 새 페이지 `b`의 예를 사용하여 다양한 충돌 해결 방법을 보여줍니다.

* 블루프린트: `/b`

   하위 페이지가 1개인 마스터 페이지, `bp-level-1`

* Live Copy: `/b`

   Live Copy 분기에서 수동으로 만든 페이지, 하위 페이지가 1개 있는 `lc-level-1`

   * 하위 페이지와 함께 `/b`(으)로 게시할 때 활성화됨

#### 롤아웃 전 {#before-rollout}

|  | 롤아웃 전 블루프린트 | 롤아웃 전 Live Copy | 롤아웃 전에 게시 |
|---|---|---|---|
| 값 | `b` | `b` | `b` |
| 주석 | 블루프린트 분기에 만들어짐, 롤아웃 준비 | Live Copy 분기에서 수동으로 만들기 | Live Copy 분기에서 수동으로 만든 페이지 `b`의 콘텐츠를 포함합니다 |
| 값 | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 주석 |  | Live Copy 분기에서 수동으로 만들기 | Live Copy 분기에서 수동으로 만든 페이지 `child-level-1`의 컨텐츠가 포함되어 있습니다. |

## 롤아웃 관리자 및 충돌 처리 {#rollout-manager-and-conflict-handling}

롤아웃 관리자를 사용하여 충돌 관리를 활성화하거나 비활성화할 수 있습니다.

이 작업은 **일 CQ WCM 롤아웃 관리자**&#x200B;의 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 사용하여 수행됩니다. 롤아웃 관리자가 블루프린트에 있는 이름으로 Live Copy에 작성된 페이지의 충돌을 처리해야 하는 경우 값 **이 수동으로 만든 페이지**( `rolloutmgr.conflicthandling.enabled`)와의 충돌을 true로 설정합니다.

AEM에는 충돌 관리가 비활성화되었을 때 미리 정의된 동작이 있습니다.](#behavior-when-conflict-handling-deactivated)[

## 충돌 처리기 {#conflict-handlers}

AEM에서는 충돌 핸들러를 사용하여 블루프린트에서 Live Copy로 컨텐츠를 롤아웃할 때 존재하는 페이지 충돌을 해결합니다. 페이지 이름 바꾸기는 이러한 충돌을 해결하는 일반적인(뿐만 아니라) 방법입니다. 두 개 이상의 충돌 처리기를 작동하여 다양한 동작을 선택할 수 있습니다.

AEM은 다음을 제공합니다.

* [기본 충돌 처리기](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* [사용자 지정된 처리기](#customized-handlers)를 구현할 수 있습니다.
* 각 개별 처리기의 우선 순위를 설정할 수 있는 서비스 등급 메커니즘입니다
   * 순위가 가장 높은 서비스가 사용됩니다.

### 기본 충돌 처리기 {#default-conflict-handler}

기본 충돌 처리기는 `ResourceNameRolloutConflictHandler`입니다.

* 이 핸들러를 사용하면 블루프린트 페이지에 우선 순위가 지정됩니다.
* 사용자 지정된 처리기에 더 높은 등급이 필요하다는 가정 하에 이 처리기의 서비스 등급이 낮습니다(즉, `service.ranking` 속성의 기본값 미만). 그러나 필요할 때 등급을 유연하게 사용하기 위한 절대 최소는 아닙니다.

이 충돌 처리기가 블루프린트에 우선합니다. 예를 들어 Live Copy 페이지 `/b`가 Live Copy 분기 내에서 `/b_msm_moved`로 이동됩니다.

* Live Copy: `/b`

   Live Copy 내에서 `/b_msm_moved`(으)로 이동됩니다. 이렇게 하면 백업 기능이 수행되며 컨텐츠가 손실되지 않습니다.

   * `lc-level-1` 가 이동되지 않습니다.

* 블루프린트: `/b`

   Live Copy 페이지 `/b`에 롤아웃됩니다.

   * `bp-level-1` 가 Live Copy에 롤아웃됩니다.

#### 롤아웃 후 {#after-rollout}

|  | 롤아웃 후 블루프린트 | 롤아웃 후 Live Copy | 롤아웃 후 Live Copy | 롤아웃 후 게시 |
|---|---|---|---|---|
| 값 | `b` | `b` | `b_msm_moved` | `b` |
| 주석 |  | 롤아웃된 블루프린트 페이지 `b`의 컨텐츠가 있습니다. | Live Copy 분기에서 수동으로 만든 페이지 `b` 컨텐츠가 있습니다. | 변경되지 않음, Live Copy 분기에서 수동으로 만들어졌고 이제 `b_msm_moved`으로 호출되는 원래 페이지 `b`의 컨텐츠가 포함되어 있습니다. |
| 값 | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 주석 |  |  | 변경 없음 | 변경 없음 |

### 사용자 지정된 처리기 {#customized-handlers}

사용자 지정된 충돌 처리기를 통해 고유한 규칙을 구현할 수 있습니다. 서비스 등급 메커니즘을 사용하여 다른 핸들러와 상호 작용하는 방법을 정의할 수도 있습니다.

사용자 지정된 충돌 처리기는 다음 작업을 수행할 수 있습니다.

* 필요에 따라 이름을 지정합니다.
* 필요에 따라 개발/구성됩니다.
   * 예를 들어 Live Copy 페이지에 우선순위가 부여되도록 핸들러를 개발할 수 있습니다.
* [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 사용하여 구성할 수 있도록 설계할 수 있습니다. 특히
   * **서비스** 전송은 다른 충돌 처리기(  `service.ranking`)와 관련된 순서를 정의합니다.
      * 기본값은 `0`입니다.

### 충돌 처리가 비활성화된 경우 동작 {#behavior-when-conflict-handling-deactivated}

수동으로 [충돌 처리를 비활성화하는 경우](#rollout-manager-and-conflict-handling) AEM에서 충돌하는 페이지에서 작업을 수행하지 않습니다. 충돌하지 않는 페이지는 예상대로 롤아웃됩니다.

>[!CAUTION]
>
>충돌 처리가 비활성화되면, AEM에서는 충돌이 무시되고 있음을 표시하지 않습니다. 이러한 경우 이 동작은 명시적으로 구성해야 하므로 원하는 동작으로 간주됩니다.

이 경우 Live Copy가 효과적으로 우선합니다. 블루프린트 페이지 `/b`이 복사되지 않고 Live Copy 페이지 `/b`에 아무런 영향이 없습니다.

* 블루프린트: `/b`

   은 전혀 복사되지 않지만 무시됩니다.

* Live Copy: `/b`

   계속 똑같아

#### 롤아웃 후 {#after-rollout-no-conflict}

|  | 롤아웃 후 블루프린트 | 롤아웃 후 Live Copy | 롤아웃 후 게시 |
|---|---|---|---|
| 값 | `b` | `b` | `b` |
| 주석 |  | 변경되지 않음, Live Copy 분기에서 수동으로 만든 페이지 `b` 컨텐츠가 있습니다. | 변경되지 않음, Live Copy 분기에서 수동으로 만든 페이지 `b`의 컨텐츠가 포함되어 있습니다 |
| 값 | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 주석 |  | 변경 없음 | 변경 없음 |

### 서비스 등급 {#service-rankings}

[OSGi](https://www.osgi.org/) 서비스 등급을 사용하여 개별 충돌 처리기의 우선순위를 정의할 수 있습니다.
