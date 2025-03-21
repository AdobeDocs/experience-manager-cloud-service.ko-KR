---
title: MSM 모범 사례
description: Adobe 엔지니어링 및 컨설팅 팀에서 컴파일한 AEM 다중 사이트 관리자 시작 및 운영에 도움이 되는 모범 사례에 대해 알아봅니다.
feature: Multi Site Manager
role: Admin
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 94%

---

# MSM 모범 사례 {#msm-best-practices}

## 일반 {#general}

MSM은 콘텐츠 배포 자동화를 위한 구성 가능 프레임워크입니다. 구현은 종종 웹 사이트의 주요 부분을 포함하며 조직과 지역에 걸쳐 있습니다. 따라서 웹 사이트를 계획할 때와 마찬가지로 MSM 구현을 신중하게 계획하는 것이 좋습니다.

* 구현을 시작하기 전에 **구조 및 콘텐츠 흐름을 계획**&#x200B;하십시오.
* **필요한 만큼, 하지만 가능한 적게 맞춤화하십시오.** MSM은 높은 수준의 맞춤화(예: 롤아웃 구성)을 지원하지만 일반적으로 웹 사이트의 성능, 안정성 및 업그레이드 능력을 위한 가장 좋은 방법은 맞춤화를 최소화하는 것입니다.
* 성공을 보장하려면 초기에 **거버넌스** 모델을 수립하고 그에 따라 사용자를 교육하십시오. 거버넌스 관점에서 볼 때 가장 좋은 방법은 다른 로컬 사용자 및 그들의 Live Copy에 콘텐츠를 할당/연결하는 **로컬 콘텐츠 제작자의 권한을 최소화**&#x200B;하는 것입니다. 통제되지 않는 연결된 상속은 MSM 구조의 복잡성을 크게 증가시키고 성능과 안정성을 손상시킬 수 있기 때문입니다.
* 구조, 콘텐츠 흐름, 자동화 및 거버넌스에 대한 계획을 수립했다면 라이브 구현을 시작하기 전에 **시스템을 프로토타이핑하고 철저히 테스트**&#x200B;하십시오.
* **Adobe 컨설팅 및 주요 시스템 통합업체**&#x200B;는 MSM을 통한 콘텐츠 자동화 계획 및 구현에 대한 풍부한 경험을 바탕으로 MSM 프로젝트 시작 및 전체적인 구현에 도움이 될 수 있습니다.

## Live Copy 소스 및 블루프린트 구성 {#live-copy-sources-and-blueprint-configurations}

[일반 페이지](creating-live-copies.md#creating-a-live-copy-of-a-page) 또는 [블루프린트 구성](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)을 사용하여 Live Copy를 만들 수 있습니다. 두 가지 모두 유용한 사용 사례입니다.

블루프린트 구성을 사용할 때의 추가적인 이점은 다음과 같습니다.

* 작성자는 블루프린트의 **롤아웃** 옵션을 통해 이 블루프린트에서 상속되는 Live Copy에 수정 사항을 명시적으로 푸시할 수 있습니다.
* 작성자는 **사이트 생성**&#x200B;을 통해 손쉽게 언어를 선택하고 Live Copy 구조를 구성할 수 있습니다.
* 블루프린트와 연결된 Live Copy에 대한 기본 롤아웃 구성을 정의할 수 있습니다.

블루프린트 구성이 참조되지 않는 경우 Live Copy 자체에서만 롤아웃을 시작할 수 있으며, 기본적으로 콘텐츠는 소스에서 가져옵니다.

라이브 카피로 사이트를 만들 때, 전체 MSM 기능 세트를 사용할 수 있도록 블루프린트 구성을 만드는 것이 유용합니다.

>[!NOTE]
>
>권한 탭의 CUG는 블루프린트에서 Live Copy로 롤아웃할 수 없습니다. Live Copy를 구성할 때 이 규칙을 염두에 두고 계획을 세우십시오.

## 구성 요소 및 컨테이너 동기화 {#components-and-container-synchronization}

일반적으로 구성 요소 동기화와 관련된 MSM의 롤아웃 규칙은 다음과 같습니다.

* 구성 요소는 블루프린트에 포함된 리소스를 동기화하여 롤아웃합니다.
* 컨테이너는 현재 리소스만 동기화합니다.

이는 구성 요소는 총계로 취급되며 롤아웃 시 구성 요소 자체 및 모든 하위 항목은 블루프린트의 구성 요소 및 하위 항목으로 대체됨을 의미합니다. 즉, 이러한 구성 요소에 리소스를 로컬로 추가하면 이는 롤아웃 시 블루프린트 콘텐츠로 손실됩니다.

로컬로 추가된 구성 요소가 롤아웃 시 유지되도록 구성 요소의 중첩을 지원하려면 해당 구성 요소를 컨테이너로 선언해야 합니다.

>[!NOTE]
>
>구성 요소에 `cq:isContainer` 속성을 추가하여 이를 컨테이너로 지정하십시오.

## 사이트 생성 {#create-site}

AEM에는 Live Copy를 만들기 위한 두 가지 주요 접근 방식이 있습니다.

* [Live Copy 생성](creating-live-copies.md#creating-a-live-copy-of-a-page) - 보다 일반적인 접근 방식으로 간주되며, 원하는 페이지에서 Live Copy를 만들 수 있습니다. Live Copy의 콘텐츠 구조는 소스와 정확하게 일치합니다.

* [사이트 생성](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) - 보다 전문화된 접근 방식으로, 주로 다국어 구조가 있는 웹 사이트를 만들 때 사용합니다.

다음은 사이트 생성 시 염두에 두어야 할 몇 가지 고려 사항입니다.

* 사이트를 만들려면 [블루프린트 구성](creating-live-copies.md#managing-blueprint-configurations)이 필요합니다.
* 새 사이트에 생성할 언어 경로를 선택하려면 해당하는 언어 루트가 블루프린트(소스)에 존재해야 합니다.
* [새 사이트 Live Copy로 생성](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)되면(**만들기** 및 **사이트** 사용) 이 Live Copy의 처음 두 가지 수준은 *약식*&#x200B;입니다. 페이지의 하위 항목은 라이브 관계에 속하지 않지만, 트리거와 일치하는 라이브 관계가 있는 경우 롤아웃은 계속 적용됩니다.

다음을 피하는 것이 좋습니다.

* 수동으로 블루프린트(첫 번째 수준 아래)에 언어 추가
* 수동으로 언어 루트 바로 아래에 콘텐츠 추가 - 이렇게 하면 롤아웃 시 이 새 콘텐츠가 Live Copy로 자동으로 전달되지 않습니다.

## MSM 및 다국어 웹 사이트 {#msm-and-multilingual-websites}

MSM은 두 가지 방법으로 다국어 웹 사이트 생성을 지원할 수 있습니다.

언어 마스터를 만들 때 다음 사항에 유의하십시오.

* MSM 자체는 **콘텐츠 번역을 지원하지 않지만**, 이를 지원하는 서드파티 번역 커넥터와 통합할 수 있습니다. 다음 사항을 참고하십시오.
   * MSM을 사용하면 페이지 및/또는 구성 요소 수준에서 상속을 취소할 수 있습니다. 이렇게 하면 텍스트 롤아웃 시 Live Copy의 번역된 콘텐츠를 아직 번역되지 않은 블루프린트 콘텐츠로 덮어쓰는 것을 방지할 수 있습니다.
      * 일부 서드파티 번역 커넥터는 이러한 MSM 상속 관리를 자동화합니다.
      * 자세한 내용은 귀사의 번역 서비스 공급업체에 문의하십시오.
      * 언어 마스터를 만들고 번역하기 위한 또 다른 접근 방식은 AEM의 기본 번역 통합 프레임워크와 함께 언어 사본을 사용하는 것입니다.

자세한 내용은 [다국어 사이트를 위한 콘텐츠 번역](/help/sites-cloud/administering/translation/overview.md) 및 [번역 모범 사례](/help/sites-cloud/administering/translation/best-practices.md)를 참조하십시오.

## 구조 변경 및 롤아웃 {#structure-changes-and-rollouts}

블루프린트/소스 트리의 콘텐츠 구조에 대한 수정 사항은 Live Copy에 다르게 반영됩니다. 이는 수정 유형에 따라 달라집니다.

* 블루프린트에서 새 페이지를 **생성**&#x200B;하면 표준 롤아웃 구성을 통한 롤아웃 이후 해당하는 페이지가 Live Copy에 생성됩니다.
* 블루프린트에서 페이지를 **삭제**&#x200B;하면 표준 롤아웃 구성을 통한 롤아웃 이후 해당하는 페이지가 Live Copy에서 삭제됩니다.
* 블루프린트에서 새 페이지를 **이동**&#x200B;해도 표준 롤아웃 구성을 통한 롤아웃 이후 해당하는 페이지가 Live Copy에서 이동하지 **않습니다**.
   * 이 비헤이비어의 이유는 페이지 이동이 페이지 삭제를 묵시적으로 포함하기 때문입니다. 작성자의 페이지를 삭제하면 게시 시 해당 콘텐츠가 자동으로 비활성화되므로 예기치 않은 비헤이비어가 발생할 수 있습니다. 링크, 책갈피 등과 같은 관련 항목에도 추가적인 영향을 미칠 수 있습니다.
      * 각 Live Copy 페이지의 콘텐츠 상속이 업데이트되어 블루프린트에 해당 소스의 새 위치가 반영됩니다.
      * 블루프린트에서 라이브 카피로의 페이지 이동을 완전히 실현하려면 [페이지 이동 모범 사례]를 참고하십시오.(#page-move)

### 페이지 이동 모범 사례 {#page-move}

Live Copy에서 페이지를 이동할 때 다음 모범 사례를 고려하십시오.

>[!NOTE]
>
>다음은 [롤아웃 트리거 시](live-copy-sync-config.md#rollout-triggers)에만 작동합니다.

1. 사용자 정의 롤아웃 구성을 만듭니다.
   * 이 새 구성은 `PageMoveAction` 작업을 포함해야 합니다.
   * 이 구성에 다른 작업을 추가하지 마십시오.
1. 새 구성을 배치합니다.
   * 각 페이지를 Live Copy의 이전 위치에서 삭제할 때 페이지 이동을 완전히 롤아웃하려면 다음 작업을 수행하십시오.
      * 생성된 구성을 표준 롤아웃 구성 앞에 배치합니다. 표준 롤아웃 구성은 이전 위치에서의 페이지 삭제 작업을 처리합니다.
      * Live Copy의 이전 위치에 각 페이지를 유지하면서 페이지 이동을 롤아웃하려면(즉, 콘텐츠를 복제하려면) 다음 작업을 수행하십시오.
         * 생성된 구성을 표준 롤아웃 구성 뒤에 배치합니다. 이렇게 하면 콘텐츠가 Live Copy에서 삭제되거나 게시에서 비활성화되지 않습니다.

## 롤아웃 맞춤화 {#customizing-rollouts}

MSM 롤아웃 구성은 맞춤화가 매우 용이합니다. 롤아웃을 자동화하면 광범위한 결과를 초래할 수 있습니다. 가장 좋은 방법은 다음 활동을 수행하기 전에 매우 신중하게 계획을 세우는 것입니다.

* [onModify 트리거](#onmodify)와 같은 롤아웃 자동화
* [노드 유형/속성](#node-types-properties) 맞춤화
* 이후 워크플로 시작
* 롤아웃의 일부로 콘텐츠 활성화

### onModify {#onmodify}

[롤아웃 트리거](live-copy-sync-config.md#rollout-triggers) `onModify`를 사용할 때에는 다음을 참고하십시오.

* `onModify` 트리거를 사용하여 롤아웃을 자동화하면 모든 페이지 수정 시 롤아웃이 트리거되므로 작성 성능에 부정적인 영향을 미칠 수 있습니다.
* 롤아웃 결과는 예상과 다를 수 있습니다. 그 이유는 다음과 같습니다.
   * 최종 수정 이벤트의 순서를 지정할 수 없기 때문입니다.
   * 이벤트 기반 아키텍처가 롤아웃 관리자에게 전달된 이벤트의 순서를 보장할 수 없기 때문입니다.
* 이러한 롤아웃 구성을 사용하면 동일한 리소스의 동시 업데이트가 발생할 경우 커밋 충돌이 발생할 수 있기 때문입니다.

따라서 자동 롤아웃 실행의 이점이 잠재적 성능 문제를 능가하는 경우에만 `onModify` 트리거를 사용하는 것이 좋습니다.

### 노드 유형/속성 {#node-types-properties}

MSM을 사용하면 롤아웃 작업 외에도 롤아웃되는 노드 속성을 맞춤화할 수 있습니다. [MSM OSGi 구성을 사용하면 노드 유형을 소스에서 Live Copy로 복사하지 못하도록 제외](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization)할 수 있습니다.

## 추가 정보 {#further-information}

MSM 및 Live Copy에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [Live Copy 생성 및 동기화](creating-live-copies.md)
* [Live Copy 개요 콘솔](live-copy-overview.md)
* [Live Copy 동기화 구성](live-copy-sync-config.md)
* [MSM 롤아웃 충돌](rollout-conflicts.md)
