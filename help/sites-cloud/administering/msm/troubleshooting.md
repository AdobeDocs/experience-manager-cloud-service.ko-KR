---
title: MSM 문제 해결 및 FAQ
description: 가장 일반적인 MSM 관련 문제를 해결하고 가장 일반적인 MSM 관련 질문에 대한 답변을 얻는 방법을 알아봅니다.
feature: 다중 사이트 관리자
role: Administrator
exl-id: 50f02f4f-a347-4619-ac90-b3136a7b1782
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# MSM 문제 해결 및 FAQ {#troubleshooting-msm}

## 첫 번째 단계 문제 해결 {#first-steps}

MSM에서 잘못된 동작이나 오류가 발생한 경우 시작 및 세부 문제 해결을 시작하기 전에 다음을 확인하십시오.

* 문제나 질문이 이미 해당 위치에서 처리되었을 수 있으므로 [MSM FAQ](#faq)를 확인하십시오.
* 많은 잘못된 인식과 함께 팁이 제공되므로 [MSM 우수 사례 문서](best-practices.md)를 확인하십시오.

## 블루프린트 및 Live Copy 상태에 대한 고급 정보 찾기 {#advanced-info}

MSM은 리소스 URL의 선택기로 요청할 수 있는 여러 서블릿을 등록합니다. UI에서 사용되지만, 직접 요청하여 페이지에 대한 고급 계산된 MSM 상태를 직접 볼 수도 있습니다.

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * 블루프린트 페이지에서 이 옵션을 사용하여 연결된 모든 Live Copy 목록과 추가 Live Copy 상태 정보를 검색합니다.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Live Copy 페이지에서 이 정보를 사용하여 블루프린트 페이지와의 연결에 대한 고급 정보를 검색합니다. 페이지가 Live Copy가 아닌 경우 아무 것도 반환되지 않습니다.

이러한 서블릿은 `com.day.cq.wcm.msm` 로거를 통해 DEBUG 로그 메시지를 생성하므로 유용할 수도 있습니다.

## 저장소에서 MSM 관련 정보 확인 {#checking-repo}

이전 서블릿은 MSM 관련 노드 및 mixin을 기반으로 계산된 정보를 반환했습니다. 정보는 다음과 같은 방법으로 저장소에 저장됩니다.

* `cq:LiveSync` mixin 유형
   * 이 항목은 `jcr:content` 노드에 설정되고 루트 Live Copy 페이지를 정의합니다.
   * 이러한 페이지에는 다음 속성을 통해 Live Copy에 대한 기본 및 필수 정보를 포함하는 `cq:LiveSyncConfig` 유형의 하위 노드가 있습니다.`cq:LiveCopy`
      * `cq:master` 는 Live Copy의 블루프린트 페이지를 가리킵니다.
      * `cq:rolloutConfigs` Live Copy에 적용된 활성 롤아웃 구성을 나타냅니다.
      * `cq:isDeep` 이 루트 Live Copy 페이지의 하위 페이지가 Live Copy에 포함된 경우 true입니다.
* `cq:LiveRelationship` mixin 유형
   * 모든 Live Copy 페이지에는 `jcr:content` 노드에 대한 이러한 mixin 유형이 있습니다.
   * 코드가 포함되어 있지 않으면 Live Copy 작업 외부의 작성 인터페이스를 통해 특정 지점의 페이지가 분리되거나 수동으로 생성되었습니다(만들기 또는 롤아웃).
* `cq:LiveSyncCancelled` mixin 유형
   * 일시 중단된 Live Copy 페이지의 `jcr:content` 노드에 추가되었습니다.
   * 일시 중단이 하위 페이지에도 유효한 경우, 동일한 노드에서 `cq:isCancelledForChildren` 속성이 true로 설정됩니다.

이러한 속성에 있는 정보는 UI에 반영되어야 하지만 문제 해결 시 MSM 작업이 발생할 때 저장소에서 직접 MSM 동작을 관찰하는 것이 도움이 될 수 있습니다.

이러한 속성을 아는 것은 리포지토리를 쿼리하고 특정 상태의 페이지 세트를 찾는 데 유용합니다. 예:

* `select * from cq:LiveSync` 모든 Live Copy 루트 페이지를 반환합니다.

## FAQ {#faq}

다음은 MSM 및 Live Copy와 관련된 몇 가지 FAQ입니다.

### MSM 롤아웃 중에 일부 속성(예: 제목, 주석)이 업데이트되지 않는 이유는 무엇입니까?{#missing-properties}

MSM 동기화 작업은 구성 가능성이 높습니다. 롤아웃 중에 수정되는 속성 또는 구성 요소는 해당 구성의 속성에 따라 직접 수정됩니다.

이 항목에 대한 자세한 내용은 [이 문서](best-practices.md)를 참조하십시오.

### 작성자 그룹에 대한 롤아웃 권한을 제거하려면 어떻게 해야 합니까?{#remove-rollout-permissions}

AEM 주체(사용자 또는 그룹)에 대해 설정하거나 제거할 수 있는 **롤아웃** 권한이 없습니다.

또는 다음 중 하나를 수행할 수 있습니다.

* 지정된 주도자에 대한 롤아웃 작업을 숨기도록 제품 UI를 사용자 지정합니다.
* 롤아웃이 허용되지 않는 작성자의 Live Copy 트리에서 쓰기 권한을 제거합니다.

### 접미사가 &quot;_msm_moved&quot;인 Live Copy 페이지가 표시되는 이유는 무엇입니까?{#moved-pages}

블루프린트 페이지가 롤아웃되면 해당 Live Copy 페이지를 업데이트하거나, 페이지가 아직 존재하지 않는 경우(예: 처음 롤아웃되거나 Live Copy 페이지가 수동으로 삭제되었을 때) 새 Live Copy 페이지를 만듭니다.

하지만 후자의 경우, `cq:LiveRelationship` 속성이 없는 페이지가 동일한 이름으로 존재하는 경우 Live Copy 페이지가 생성되기 전에 이 페이지의 이름이 적절하게 변경됩니다.

기본적으로 롤아웃에는 Live Copy 페이지가 작성될 때 블루프린트의 업데이트가 롤아웃되는 연결된 Live Copy 페이지가 필요하거나 페이지가 작성되지 않은 페이지가 필요합니다.

독립형 페이지가 있는 경우 MSM에서 이 페이지의 이름을 변경하고 연결된 별도의 Live Copy 페이지를 만듭니다.

Live Copy 하위 트리의 이러한 독립형 페이지는 일반적으로 **분리** 작업의 결과이거나, 작성자가 이전에 Live Copy 페이지를 수동으로 삭제한 다음 동일한 이름으로 다시 만들었습니다.

이를 방지하려면 **분리** 대신 Live Copy **일시 중단** 기능을 사용하십시오. **이 문서에서 [분리** 작업에 대한 자세한 내용을 알아봅니다.](creating-live-copies.md)
