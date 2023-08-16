---
title: 롤아웃 충돌
description: 다중 사이트 관리자 롤아웃 충돌을 관리하고 해결하는 방법에 대해 알아봅니다.
feature: Multi Site Manager
role: Admin
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 94%

---

# 롤아웃 충돌 {#msm-rollout-conflicts}

블루프린트 분기 및 종속 Live Copy 분기 모두에서 동일한 페이지 이름의 새 페이지를 만들면 충돌이 발생할 수 있습니다. 이러한 충돌은 롤아웃 시 처리 및 해결해야 합니다.

## 충돌 처리 {#conflict-handling}

블루프린트 및 라이브 카피 분기에 충돌하는 페이지가 있는 경우 MSM을 사용하여 처리 방법(또는 처리 여부)을 정의할 수 있습니다.

롤아웃을 차단하지 않도록 다음과 같은 정의를 사용할 수 있습니다.

* 롤아웃 시 우선 순위가 높은 페이지(블루프린트 또는 Live Copy)
* 이름을 변경할 페이지 및 방법
* 게시된 콘텐츠에 미치는 영향

AEM의 기본 비헤이비어는 게시된 콘텐츠에 영향을 미치지 않는다는 것입니다. 따라서 Live Copy 분기에서 수동으로 생성된 페이지가 게시되어 있는 경우 해당 콘텐츠는 충돌 처리 및 롤아웃 이후에도 계속 게시됩니다.

표준 기능 이외에도 맞춤화된 충돌 핸들러를 추가하여 다른 규칙을 구현할 수 있습니다. 또한 개별 프로세스로 게시 작업을 허용할 수도 있습니다.

### 예시 상황 {#example-scenario}

다음 섹션에서는 블루프린트 및 Live Copy 분기 모두에 수동으로 생성된 새 페이지 `b`의 예를 사용하여 다양한 충돌 해결 방법을 설명합니다.

* 블루프린트: `/b`

  한 개의 하위 페이지 `bp-level-1`을 가지는 마스터 페이지

* Live Copy: `/b`

  한 개의 하위 페이지 `lc-level-1`을 가지는 Live Copy 분기에 수동으로 생성된 페이지

   * 게시에서 하위 페이지와 함께 `/b`로 활성화됨

#### 롤아웃 이전 {#before-rollout}

|  | 롤아웃 이전의 블루프린트 | 롤아웃 이전의 Live Copy | 롤아웃 이전의 게시 |
|---|---|---|---|
| 값 | `b` | `b` | `b` |
| 댓글 | 블루프린트 분기에 생성됨, 롤아웃 준비됨 | Live Copy 브론치에 수동으로 생성됨 | Live Copy 분기에 수동으로 생성된 페이지 `b`의 콘텐츠 포함 |
| 값 | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 댓글 |  | Live Copy 브론치에 수동으로 생성됨 | Live Copy 분기에 수동으로 생성된 페이지 `child-level-1`의 콘텐츠 포함 |

## 롤아웃 관리자 및 충돌 처리 {#rollout-manager-and-conflict-handling}

롤아웃 관리자를 사용하여 충돌 관리를 활성화 또는 비활성화할 수 있습니다.

이는 **일별 CQ WCM 롤아웃 관리자**&#x200B;의 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 사용하여 수행됩니다. 롤아웃 관리자가 블루프린트에 존재하는 이름으로 Live Copy에 생성된 페이지의 충돌을 처리해야 하는 경우 **수동으로 생성된 페이지와의 충돌 해결**(`rolloutmgr.conflicthandling.enabled`) 값을 true로 설정합니다.

AEM에는 [충돌 관리가 비활성화되었을 때 실행되는 사전 정의된 비헤이비어](#behavior-when-conflict-handling-deactivated)가 있습니다.

## 충돌 핸들러 {#conflict-handlers}

AEM은 충돌 핸들러를 사용하여 블루프린트에서 Live Copy로 콘텐츠를 롤아웃할 때 발생하는 페이지 충돌을 해결합니다. 이러한 충돌을 해결하는 일반적인 방법은 페이지의 이름을 바꾸는 것입니다. 하나 이상의 충돌 핸들러를 작동하여 다양한 비헤이비어를 실행할 수 있습니다.

AEM은 다음을 제공합니다.

* [기본 충돌 핸들러](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* [맞춤화된 핸들러](#customized-handlers) 구현 가능성
* 각 개별 처리기의 우선 순위를 설정할 수 있는 서비스 순위 메커니즘
   * 순위가 가장 높은 서비스가 사용됩니다.

### 기본 충돌 핸들러 {#default-conflict-handler}

기본 충돌 핸들러는 `ResourceNameRolloutConflictHandler`입니다.

* 이 핸들러를 사용하면 블루프린트 페이지가 우선 순위를 갖습니다.
* 이 핸들러의 서비스 순위는 낮게 설정되어 있는데(`service.ranking` 속성의 기본값보다 낮음), 이는 맞춤화된 처리기에 더 높은 순위가 필요하다고 가정하기 때문입니다. 그러나 순위는 유연성을 보장하기 위한 절대적인 최소 조건이 아닙니다.

이 충돌 핸들러를 사용하면 블루프린트가 우선 순위를 갖습니다. 예를 들어 Live Copy 페이지 `/b`가 Live Copy 분기 내에서 `/b_msm_moved`로 이동하게 됩니다.

* Live Copy: `/b`

  Live Copy 내에서 `/b_msm_moved`로 이동합니다. 이는 백업 역할을 하며 콘텐츠가 손실되지 않도록 합니다.

   * `lc-level-1`은 이동하지 않습니다.

* 블루프린트: `/b`

  Live Copy 페이지 `/b`로 롤아웃됩니다.

   * `bp-level-1`은 Live Copy로 롤아웃됩니다.

#### 롤아웃 이후 {#after-rollout}

|  | 롤아웃 이후의 블루프린트 | 롤아웃 이후의 Live Copy | 롤아웃 이후의 Live Copy | 롤아웃 이후의 게시 |
|---|---|---|---|---|
| 값 | `b` | `b` | `b_msm_moved` | `b` |
| 댓글 |  | 롤아웃된 블루프린트 페이지 `b`의 콘텐츠가 있음 | Live Copy 분기에 수동으로 생성된 페이지 `b`의 콘텐츠가 있음 | 변경 내용 없음, Live Copy 분기에 수동으로 생성된 원본 페이지 `b`(이제 `b_msm_moved`로 바뀜)의 콘텐츠 포함 |
| 값 | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 댓글 |  |  | 변경 내용 없음 | 변경 내용 없음 |

### 맞춤화된 핸들러 {#customized-handlers}

맞춤화된 충돌 핸들러를 사용하면 나만의 규칙을 구현할 수 있습니다. 서비스 순위 메커니즘을 사용하여 이들 핸들러가 다른 핸들러와 상호 작용하는 방법을 지정할 수도 있습니다.

맞춤화된 충돌 핸들러는

* 요구 사항에 따라 이름이 지정될 수 있습니다.
* 요구 사항에 따라 개발/구성될 수 있습니다.
   * 예를 들어 Live Copy 페이지가 우선 순위를 갖도록 핸들러를 개발할 수 있습니다.
* [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 사용하여 구성되도록 디자인될 수 있습니다. 특히
   * **서비스 순위**&#x200B;는 다른 충돌 핸들러와 관련된 순서를 정의합니다(`service.ranking`).
      * 기본값은 `0`입니다.

### 충돌 처리가 비활성화되었을 때 실행되는 비헤이비어 {#behavior-when-conflict-handling-deactivated}

수동으로 [충돌 처리를 비활성화](#rollout-manager-and-conflict-handling)하면 AEM은 충돌이 발생한 페이지에 어떤 조치도 취하지 않습니다. 충돌이 발생하지 않은 페이지는 정상적으로 롤아웃됩니다.

>[!CAUTION]
>
>충돌 처리가 비활성화되어 있는 경우 AEM은 충돌이 무시되고 있음을 알리지 않습니다. 이러한 경우 이 비헤이비어를 명시적으로 구성해야 하므로 이를 원하는 비헤이비어로 간주합니다.

이 경우 Live Copy가 사실상 우선됩니다. 블루프린트 페이지 `/b`는 복사되지 않으며 Live Copy 페이지 `/b`는 그대로 유지됩니다.

* 블루프린트: `/b`

  복사되지 않고 무시됩니다.

* Live Copy: `/b`

  그대로 유지됩니다.

#### 롤아웃 이후 {#after-rollout-no-conflict}

|  | 롤아웃 이후의 블루프린트 | 롤아웃 이후의 Live Copy | 롤아웃 이후의 게시 |
|---|---|---|---|
| 값 | `b` | `b` | `b` |
| 댓글 |  | 변경 내용 없음, Live Copy 분기에 수동으로 생성된 페이지 `b`의 콘텐츠가 있음 | 변경 내용 없음, Live Copy 분기에 수동으로 생성된 페이지 `b`의 콘텐츠 포함 |
| 값 | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| 댓글 |  | 변경 내용 없음 | 변경 내용 없음 |

### 서비스 순위 {#service-rankings}

[OSGi](https://www.osgi.org/) 서비스 순위를 사용하여 개별 충돌 핸들러의 우선 순위를 정의할 수 있습니다.
