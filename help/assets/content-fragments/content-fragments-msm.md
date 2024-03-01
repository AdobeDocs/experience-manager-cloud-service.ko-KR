---
title: MSM 및 라이브 카피를 사용하여 콘텐츠 조각 재사용
description: 소스 콘텐츠와 동기화하면서 여러 위치에서 동일하거나 유사한 콘텐츠 조각 콘텐츠를 사용하기 위해 MSM의 라이브 카피 기능을 사용하는 방법에 대해 알아봅니다.
source-git-commit: 3ce1a982055c2f9c900edbd88e079deb6d3a036a
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 10%

---

# MSM을 사용하여 콘텐츠 조각 재사용 {#reuse-content-fragments-using-msm}

다중 사이트 관리자(MSM) 및 라이브 카피 기능을 사용하면 소스 콘텐츠와 동기화하면서 여러 위치에서 동일한 콘텐츠를 사용할 수 있습니다.

* MSM 라이브 카피를 사용하여 다음과 같은 작업을 수행할 수 있습니다.
   * 콘텐츠를 한 번 만든 다음
   * 이 콘텐츠를 동일한 사이트 또는 다른 사이트의 다른 영역 또는 애플리케이션에서 재사용할 수 있습니다.
* 그런 다음 MSM은 소스 콘텐츠와 해당 Live Copy 간의 라이브 관계를 유지하여 다음 작업을 수행합니다.
   * 소스 콘텐츠를 변경하면 소스 및 라이브 카피가 동기화됩니다.
   * 개별 하위 페이지 및/또는 구성 요소에 대한 라이브 관계의 연결 해제하여 Live Copy의 콘텐츠만 조정할 수 있습니다.

MSM 개념에 대한 자세한 개요는 를 참조하십시오. [콘텐츠 재사용: 다중 사이트 관리자 및 라이브 카피](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>[다중 사이트 관리자(MSM)](/help/sites-cloud/administering/msm/overview.md) Adobe Experience Manager의 기능을 사용하면 한 번 작성된 후 여러 웹 위치에서 재사용되는 콘텐츠를 재사용할 수 있습니다.

콘텐츠 조각에 MSM을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 콘텐츠 조각을 한 번 만든 다음 이러한 조각의 복사본을 만들어(연결) 사이트 또는 애플리케이션의 다른 영역에서 재사용할 수 있습니다.
* 소스 사본을 한 번 업데이트한 다음 변경 사항을 (라이브) 사본으로 푸시하여 여러 사본의 동기화를 유지합니다.
* 상위 조각과 하위 조각 간의 링크를 완전히 또는 해당 변형이나 필드에 대해 일시 중단하거나 영구적으로 중단하여 로컬 변경 작업을 수행합니다.

콘텐츠 조각 편집기 내의 기능과 결합된 콘텐츠 조각용 MSM을 사용하면 필드 수준에서 상속을 중단하거나 복원할 수 있습니다.

>[!CAUTION]
>
>콘텐츠 조각용 MSM은 를 통해 콘텐츠 조각을 사용하는 경우에만 사용할 수 있습니다. **에셋** 콘솔.
>
>MSM 기능은 *아님* 를 사용할 때 사용 가능 **컨텐츠 조각** 콘솔.

## 방법 {#how-to}

콘텐츠 조각(자산에도 적용 가능)에 대한 MSM 사용에 대한 자세한 내용은 다음 설명서를 참조하십시오.

* 사용 방법 [콘텐츠 조각(및 에셋)용 MSM](/help/assets/reuse-assets-using-msm.md)

* [라이브 카피 만들기](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >MSM을 사용하여 콘텐츠 조각의 사본을 만들려는 경우 **고유** 각 데이터 세트에 사용된 모든 데이터 유형에서 제약 조건을 제거해야 합니다 [컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md).

* [소스 및 라이브 카피의 속성 및 상태 보기](/help/assets/reuse-assets-using-msm.md#properties)
* [소스에서 라이브 카피로 수정 사항 전파](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* 상속 취소 및 복원 대상:
   * 의 필드 및 변형 [콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [관련 에셋의 메타데이터](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [관계 일시 중단 및 재개](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [라이브 관계 제거](/help/assets/reuse-assets-using-msm.md#detach)
* [콘텐츠 조각(및 에셋)에 대한 MSM과 사이트에 대한 MSM 비교](/help/assets/reuse-assets-using-msm.md#comparison)

## 제한 사항 {#limitations}

* 콘텐츠 조각에 대한 수정 시 트리거 및 관련 롤아웃 구성이 존재하지 않습니다.