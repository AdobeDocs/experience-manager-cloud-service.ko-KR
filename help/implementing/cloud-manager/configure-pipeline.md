---
title: CI/CD 파이프라인 구성 - Cloud Services
description: CI/CD 파이프라인 구성 - Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: f3743451f7aeadae26e8a6814cfbed9667c4a242
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# CI-CD 파이프라인 구성 {#configure-ci-cd-pipeline}

Cloud Manager에는 두 가지 유형의 파이프라인이 있습니다.

* **프로덕션 파이프라인**:

   프로덕션 및 스테이지 환경 세트가 생성된 후에만 프로덕션 파이프라인을 추가할 수 있습니다.

   을(를) 참조하십시오. [프로덕션 파이프라인 설정](configure-pipeline.md#setting-up-the-pipeline) 자세한 내용

* **비프로덕션 파이프라인**:

   비프로덕션 파이프라인은 **개요** Cloud Manager의 사용자 인터페이스에서 페이지를 엽니다.

   을(를) 참조하십시오. [비프로덕션 및 코드 품질 전용 파이프라인](configure-pipeline.md#non-production-pipelines) 자세한 내용

   >[!NOTE]
   >파이프라인을 구성하려면 다음을 수행해야 합니다.
   > * 파이프라인을 시작할 트리거를 정의합니다.
   > * 프로덕션 배포를 제어하는 매개 변수를 정의합니다.
   > * 성능 테스트 매개 변수를 구성합니다.


## 프로덕션 파이프라인 설정 {#setting-up-production-pipeline}

배포 관리자는 프로덕션 파이프라인을 설정할 책임이 있습니다.

>[!NOTE]
>프로그램 만들기가 완료되고, Git 리포지토리에 하나 이상의 분기가 있으며, 프로덕션 및 스테이지 환경 세트가 작성될 때까지 프로덕션 파이프라인을 설정할 수 없습니다.

코드를 배포하기 전에 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>초기 설정 후 파이프라인 설정을 변경할 수 있습니다.

### 새 프로덕션 파이프라인 추가 {#adding-production-pipeline}

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

### 프로덕션 파이프라인 편집 {#editing-prod-pipeline}

에서 파이프라인 구성을 편집할 수 있습니다 **프로그램 개요** 페이지.

구성된 파이프라인을 편집하려면 아래 절차를 따르십시오.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **편집**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. 다음 **프로덕션 파이프라인 편집** 대화 상자가 표시됩니다.

   1. 다음 **구성** 탭에서 다음을 업데이트할 수 있습니다 **파이프라인 이름**, **배포 트리거**, 및 **중요한 지표 실패 동작**.

      >[!NOTE]
      >자세한 내용은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. 다음 **소스** 탭에서는 선택 또는 선택 취소할 수 있는 옵션이 제공됩니다 **프로덕션에 배포하기 전에 일시 정지** 및 **예약됨** 옵션 **프로덕션 배포 옵션**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. 다음 **경험 감사** 옵션을 사용하면 새 페이지를 업데이트하거나 추가할 수 있습니다.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. 클릭 **업데이트** 파이프라인 편집을 완료하면 됩니다.

### 추가 프로덕션 파이프라인 작업 {#additional-prod-actions}

#### 프로덕션 파이프라인 실행 {#run-prod}

파이프라인 카드에서 프로덕션 파이프라인을 실행할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **실행**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

#### 프로덕션 파이프라인 삭제 {#delete-prod}

파이프라인 카드에서 프로덕션 파이프라인을 삭제할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **삭제**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >이제 배포 관리자 역할의 사용자는 를 통해 셀프 서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다 **삭제** 옵션 을 클릭합니다.


## 비프로덕션 및 코드 품질 전용 파이프라인 {#non-production-pipelines}

스테이징 및 프로덕션에 배포되는 기본 파이프라인 외에도 고객은 비프로덕션 파이프라인이라고도 하는 추가 파이프라인을 설정할 수 있습니다.
다음과 같은 두 가지 유형의 비프로덕션 파이프라인이 있습니다.

1. 코드 품질: Git 분기의 코드에서 코드 품질 검사를 실행합니다. 이 파이프라인은 빌드 및 코드 품질 단계를 실행합니다.
1. 배포: 이 파이프라인은 빌드 및 코드 품질 단계를 실행하는 것 외에도 선택한 비프로덕션 환경에 코드를 AEM as a Cloud Service 환경에 배포합니다.

### 새 비프로덕션 파이프라인 추가 {#adding-non-production-pipeline}

홈 화면에서는 이러한 파이프라인이 새 카드에 나열됩니다.

1. 액세스 권한 **파이프라인** Cloud Manager 홈 화면에서 카드를 생성할 수 있습니다. 클릭 **+추가** 을(를) 선택합니다. **비프로덕션 파이프라인 추가**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가**  대화 상자가 표시됩니다. 생성할 파이프라인 유형을 선택합니다 **코드 품질 파이프라인** 또는 **배포 파이프라인**.

   >[!NOTE]
   >배포 파이프라인의 경우 배포 환경을 선택해야 합니다.

   또한 **배포 트리거** 및 **중요한 지표 실패 동작** 변환 전: **배포 옵션**. 클릭 **계속**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. **전체 스택 코드** 이 선택되어 있습니다. 을(를) 선택할 수 있습니다 **저장소** 그리고 **Git 분기**. 클릭 **저장**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

1. 이제 새로 생성된 비프로덕션 파이프라인이 **파이프라인** 카드.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   파이프라인은 아래와 같이 세 가지 작업이 있는 홈 화면의 카드에 표시됩니다.

   * **추가** - 새 파이프라인을 추가할 수 있습니다.
   * **보고서 정보에 액세스** - 사용자가 Cloud Manager Git 리포지토리에 액세스하는 데 필요한 정보를 얻을 수 있도록 해줍니다.
   * **추가 정보** - CI/CD 파이프라인 설명서 리소스를 이해하도록 이동합니다.

### 비프로덕션 파이프라인 편집 {#editing-nonprod-pipeline}

에서 파이프라인 구성을 편집할 수 있습니다 **파이프라인 카드** 변환 전: **프로그램 개요** 페이지.

구성된 비프로덕션 파이프라인을 편집하려면 아래 절차를 따르십시오.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 비프로덕션 파이프라인을 선택하고 을(를) 클릭합니다 **...**. 클릭 **편집**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. 다음 **프로덕션 파이프라인 편집** 대화 상자가 표시됩니다.

   1. 다음 **구성** 탭에서 다음을 업데이트할 수 있습니다 **파이프라인 이름**, **배포 트리거**, 및 **중요한 지표 실패 동작**.

      >[!NOTE]
      >자세한 내용은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. 다음 **소스 코드** 탭에서는 업데이트 가능 **저장소** 그리고 **Git 분기**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. 클릭 **업데이트** 비프로덕션 파이프라인의 편집을 완료하면 됩니다.

### 추가 비프로덕션 파이프라인 작업 {#additional-nonprod-actions}

#### 비프로덕션 파이프라인 실행 {#run-nonprod}

파이프라인 카드에서 프로덕션 파이프라인을 실행할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **실행**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

#### 비프로덕션 파이프라인 삭제 {#delete-nonprod}

파이프라인 카드에서 프로덕션 파이프라인을 삭제할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **삭제**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)


## 다음 단계 {#the-next-steps}

파이프라인을 구성한 후에는 코드를 배포해야 합니다.

자세한 내용은 [코드 배포](deploy-code.md) 자세한 내용
