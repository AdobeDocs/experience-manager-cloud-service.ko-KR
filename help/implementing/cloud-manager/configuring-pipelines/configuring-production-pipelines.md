---
title: 프로덕션 파이프라인 구성
description: 프로덕션 파이프라인 구성
index: false
source-git-commit: e0c21561a9a6e2940768ecb86da9b4d16e2fbfa8
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---


# 프로덕션 파이프라인 구성 {#configure-production-pipeline}

배포 관리자는 프로덕션 파이프라인을 구성할 책임이 있습니다.

>[!NOTE]
>프로그램 만들기가 완료되고, Git 리포지토리에 하나 이상의 분기가 있으며, 프로덕션 및 스테이지 환경 세트가 작성될 때까지 프로덕션 파이프라인을 설정할 수 없습니다.

코드를 배포하기 전에 [!UICONTROL Cloud Manager].

>[!NOTE]
>초기 설정 후 파이프라인 설정을 변경할 수 있습니다.

## 새 프로덕션 파이프라인 추가 {#adding-production-pipeline}

프로그램을 설정하고 [!UICONTROL Cloud Manager] UI 프로덕션 파이프라인을 추가할 준비가 되었습니다.

다음 단계에 따라 프로덕션 파이프라인에 대한 동작 및 환경 설정을 구성합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지.
클릭 **+추가** 을(를) 선택합니다. **프로덕션 파이프라인 추가**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **프로덕션 파이프라인 추가** 대화 상자가 표시됩니다. 파이프라인 이름을 입력합니다.

   또한 **배포 트리거** 및 **중요한 지표 실패 동작** 변환 전: **배포 옵션**. 클릭 **계속**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   배포 트리거를 정의하여 파이프라인을 시작할 수 있습니다.

   * **수동** - UI를 사용하여 파이프라인을 수동으로 시작합니다.
   * **Git 변경 시** - 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 선택하더라도 항상 파이프라인을 수동으로 시작할 수 있습니다.

      파이프라인 설정 또는 편집 중에 품질 게이트에서 중요한 오류가 발생하는 경우 배포 관리자에서 파이프라인의 동작을 정의할 수 있습니다.

      이 기능은 자동화된 프로세스를 원하는 고객에게 유용합니다. 사용 가능한 옵션은 다음과 같습니다.
   파이프라인을 시작하는 중요한 실패 지표 동작을 정의할 수 있습니다.

   * **매번 질문하기** - 기본 설정이며 중요 오류에 대해 수동으로 개입해야 합니다.
   * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
   * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.


1. 다음 **프로덕션 파이프라인 추가** 대화 상자에는 라는 레이블이 지정된 두 번째 탭이 포함되어 있습니다 **소스 코드**. **전체 스택 코드** 이 선택되어 있습니다. 을(를) 선택할 수 있습니다 **저장소** 그리고 **Git 분기**. 아래 설명된 대로 프로덕션 배포 옵션을 선택합니다. 클릭 **계속**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-fullstack1.png)

   프로덕션 배포 옵션:

   * **프로덕션에 배포하기 전에 일시 중지**: 이 옵션을 사용하면 프로덕션 전에 배포 최상위 일시 정지를 사용할 수 있습니다.
   * **예약됨**: 이 옵션을 사용하면 예약된 프로덕션 배포를 활성화할 수 있습니다.

1. 다음 **프로덕션 파이프라인 추가** 대화 상자에는 라는 레이블이 지정된 세 번째 탭이 포함되어 있습니다 **경험 감사**. 이 옵션은 항상 경험 감사에 포함해야 하는 URL 경로에 대한 테이블을 제공합니다.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   >[!IMPORTANT]
   >을(를) 클릭해야 합니다. **페이지 추가** 사용자 지정 링크를 정의하기 위해. 페이지 경로는 다음으로 시작해야 함 `/`.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit2.png)


   클릭 **새 페이지 추가** 경험 감사에 포함할 URL 경로를 제공합니다.

   예를 들어 다음을 포함하려는 경우 `https://wknd.site/us/en/about-us.html` 경험 감사에서 경로를 입력합니다 `/us/en/about-us.html` 이 필드에서 **저장**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

   테이블에 표시되는 URL은 다음과 같습니다.

   `https://publish-p12361-e112003.adobeaemcloud.com/us/en/about-us.html`

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

   최대 25개의 행을 포함할 수 있습니다. 이 섹션에 사용자가 제출한 페이지가 없는 경우, 기본적으로 사이트의 홈 페이지가 경험 감사에 포함됩니다.

   을(를) 참조하십시오. [경험 감사 결과 이해](/help/implementing/cloud-manager/experience-audit-testing.md) 자세한 내용

   >[!NOTE]
   > 구성된 페이지는 서비스에 전송되고 성능, 접근성, SEO(검색 엔진 최적화), 우수 사례 및 PWA(점진적 웹 앱) 테스트에 따라 평가됩니다.

1. 클릭 **저장**. 이제 새로 생성된 프로덕션 파이프라인이 **파이프라인** 카드.

   파이프라인은 아래와 같이 세 가지 작업이 있는 홈 화면의 카드에 표시됩니다.

   * **추가** - 새 파이프라인을 추가할 수 있습니다.
   * **보고서 정보에 액세스** - 사용자가 Cloud Manager Git 리포지토리에 액세스하는 데 필요한 정보를 얻을 수 있도록 해줍니다.
   * **추가 정보** - CI/CD 파이프라인 설명서 리소스를 이해하도록 이동합니다.