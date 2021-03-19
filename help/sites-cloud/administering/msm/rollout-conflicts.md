---
title: 롤아웃 충돌
description: 다중 사이트 관리자 롤아웃 충돌을 관리하고 해결하는 방법을 알아봅니다.
feature: 다중 사이트 관리자
role: 관리자
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 2%

---


# 롤아웃 충돌 {#msm-rollout-conflicts}

블루프린트 분기 및 종속 Live Copy 분기 모두에서 페이지 이름이 같은 새 페이지가 작성되면 충돌이 발생할 수 있습니다. 롤아웃 시 이러한 충돌을 처리하고 해결해야 합니다.

## 충돌 처리 {#conflict-handling}

페이지가 충돌하는 경우(블루프린트 및 Live Copy 분기에) MSM을 사용하여 페이지가 어떻게 처리되어야 하는지를 정의할 수 있습니다.

롤아웃이 차단되지 않도록 가능한 정의는 다음과 같습니다.

* 롤아웃 시 우선 순위를 가지는 페이지(블루프린트 또는 Live Copy)
* 이름을 바꿀 페이지(및 방법)
* 게시된 모든 컨텐츠에 미치는 영향

AEM의 기본 동작은 게시된 컨텐트에 영향을 주지 않는다는 것입니다. 따라서 Live Copy 분기에 수동으로 만든 페이지가 게시되면 충돌 처리 및 롤아웃 후에도 해당 컨텐츠가 게시됩니다.

표준 기능 외에도 사용자 정의된 충돌 핸들러를 추가하여 다른 규칙을 구현할 수 있습니다. 또한 개별 프로세스로 게시 작업을 허용할 수 있습니다.

### 예제 시나리오 {#example-scenario}

다음 섹션에서는 블루프린트와 Live Copy 분기(수동으로 생성)에서 만들어진 새 페이지 `b`의 예를 사용하여 다양한 충돌 해결 방법을 보여 줍니다.

* 블루프린트:`/b`

   하위 페이지가 1개인 마스터 페이지 `bp-level-1`

* Live Copy: `/b`

   하위 페이지 `lc-level-1`이 1개인 Live Copy 분기에 수동으로 만든 페이지

   * 하위 페이지와 함께 `/b` 게시에서 활성화됨

#### 롤아웃 전 {#before-rollout}

|  | 롤아웃 전 블루프린트 | 롤아웃 전 Live Copy | 롤아웃 전에 게시 |
|---|---|---|---|
| 값 | `b` | `b` | `b` |
| 주석 | 블루프린트 분기에 만들어짐, 롤아웃 준비 | Live Copy 분기에 수동으로 만들기 | Live Copy 분기에 수동으로 만든 페이지 `b`의 컨텐츠를 포함합니다. |
| 값 | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 주석 |  | Live Copy 분기에 수동으로 만들기 | Live Copy 분기에 수동으로 만든 페이지 `child-level-1`의 컨텐츠를 포함합니다. |

## 롤아웃 관리자 및 충돌 처리 {#rollout-manager-and-conflict-handling}

롤아웃 관리자를 사용하여 충돌 관리를 활성화 또는 비활성화할 수 있습니다.

이 작업은 **일 CQ WCM 롤아웃 관리자**&#x200B;의 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 사용하여 수행됩니다. 롤아웃 관리자가 Live Copy에서 만든 페이지와 블루프린트에 있는 이름이 있는 충돌을 처리해야 하는 경우 **수동으로 만든 페이지**( `rolloutmgr.conflicthandling.enabled`)와 충돌하는 값을 true로 설정합니다.

충돌 관리가 비활성화되었을 때 AEM에는 [사전 정의된 동작이 있습니다.](#behavior-when-conflict-handling-deactivated)

## 충돌 핸들러 {#conflict-handlers}

AEM에서는 블루프린트에서 Live Copy로 컨텐츠를 롤아웃할 때 존재하는 페이지 충돌을 해결하기 위해 충돌 핸들러를 사용합니다. 페이지 이름 변경은 이러한 충돌을 해결하는 일반적인 방법(뿐만 아니라)입니다. 둘 이상의 충돌 핸들러를 사용하여 여러 가지 비헤이비어를 선택할 수 있습니다.

AEM 제공 서비스:

* [기본 충돌 처리기](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* [사용자 지정된 핸들러](#customized-handlers)를 구현할 수 있습니다.
* 각 개별 핸들러의 우선 순위를 설정할 수 있는 서비스 등급 메커니즘입니다.
   * 등급이 가장 높은 서비스가 사용됩니다.

### 기본 충돌 처리기 {#default-conflict-handler}

기본 충돌 핸들러는 `ResourceNameRolloutConflictHandler`입니다.

* 이 핸들러를 사용하면 블루프린트 페이지에 우선 순위가 지정됩니다.
* 사용자 지정된 핸들러의 등급이 더 높은 것으로 간주되므로 이 핸들러의 서비스 등급은 `service.ranking` 속성의 기본값 아래로 설정됩니다. 하지만, 등급은 필요한 경우 유연성을 보장하는 절대적인 최소값이 아닙니다.

이 충돌 핸들러는 블루프린트에 우선 순위를 지정합니다. 예를 들어 Live Copy 페이지 `/b`은(는) Live Copy 분기 내에서 `/b_msm_moved`로 이동됩니다.

* Live Copy:`/b`

   Live Copy 내에서 `/b_msm_moved`(으)로 이동됩니다. 이렇게 하면 백업 기능이 수행되므로 내용이 손실되지 않습니다.

   * `lc-level-1` 가 이동되지 않았습니다.

* 블루프린트: `/b`

   Live Copy 페이지 `/b`에 롤아웃됩니다.

   * `bp-level-1` Live Copy로 롤아웃됩니다.

#### 롤아웃 후 {#after-rollout}

|  | 롤아웃 후 블루프린트 | 롤아웃 후 Live Copy | 롤아웃 후 Live Copy | 롤아웃 후 게시 |
|---|---|---|---|---|
| 값 | `b` | `b` | `b_msm_moved` | `b` |
| 주석 |  | 블루프린트 페이지 `b`의 내용이 롤아웃되었습니다. | Live Copy 분기에 수동으로 만든 페이지 `b`의 컨텐츠가 있습니다. | 변경 없음 - Live Copy 분기에 수동으로 만들어졌고 이제 `b_msm_moved`이라고 하는 원본 페이지 `b`의 컨텐츠가 포함되어 있습니다. |
| 값 | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 주석 |  |  | 변경 없음 | 변경 없음 |

### 사용자 지정된 핸들러 {#customized-handlers}

사용자 지정된 충돌 핸들러를 사용하여 고유한 규칙을 구현할 수 있습니다. 서비스 등급 메커니즘을 사용하여 다른 핸들러와 상호 작용하는 방법을 정의할 수도 있습니다.

사용자 지정된 충돌 핸들러는 다음과 같은 일을 할 수 있습니다.

* 필요에 따라 이름을 지정합니다.
* 필요에 따라 개발/구성할 수 있습니다.
   * 예를 들어 Live Copy 페이지에 우선 순위가 지정되도록 핸들러를 개발할 수 있습니다.
* [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 사용하여 구성할 수 있습니다. 특히 다음과 같습니다.
   * **Service** Ranking은 다른 충돌 핸들러()와 관련된 순서를  `service.ranking`정의합니다.
      * 기본값은 `0`입니다.

### 충돌 처리가 비활성화된 경우 동작 {#behavior-when-conflict-handling-deactivated}

[충돌 처리를 수동으로 비활성화하면 ](#rollout-manager-and-conflict-handling) AEM은 충돌하는 페이지에 대해 작업을 수행하지 않습니다. 충돌하지 않는 페이지는 예상대로 롤아웃됩니다.

>[!CAUTION]
>
>충돌 처리가 비활성화되면 AEM에서는 충돌이 무시되고 있음을 표시하지 않습니다. 이 경우 이 비헤이비어는 명시적으로 구성되어야 하므로 원하는 비헤이비어로 간주됩니다.

이 경우 Live Copy가 효과적으로 우선합니다. 블루프린트 페이지 `/b`이(가) 복사되지 않고 Live Copy 페이지 `/b`은(는) 그대로 유지됩니다.

* 블루프린트: `/b`

   은 전혀 복사되지 않지만 무시됩니다.

* Live Copy:`/b`

   동일하게 유지

#### 롤아웃 후 {#after-rollout-no-conflict}

|  | 롤아웃 후 블루프린트 | 롤아웃 후 Live Copy | 롤아웃 후 게시 |
|---|---|---|---|
| 값 | `b` | `b` | `b` |
| 주석 |  | 변경 사항이 없습니다. Live Copy 분기에 수동으로 만든 페이지 `b`의 컨텐츠가 있습니다. | 변경 사항이 없습니다. Live Copy 분기에 수동으로 만든 페이지 `b`의 내용이 포함되어 있습니다. |
| 값 | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 주석 |  | 변경 없음 | 변경 없음 |

### 서비스 등급 {#service-rankings}

[OSGi](https://www.osgi.org/) 서비스 등급을 사용하여 개별 충돌 핸들러의 우선 순위를 정의할 수 있습니다.
