---
title: 비프로덕션 파이프라인 편집
description: 비프로덕션 파이프라인 편집
index: true
source-git-commit: 7dc9f9a189927f3522445fac36a1606521f410b2
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# 비프로덕션 파이프라인 편집 {#edit-non-prod-pipeline}

에서 파이프라인 구성을 편집할 수 있습니다 **파이프라인 카드** 변환 전: **프로그램 개요** 페이지.

>[!IMPORTANT]
>실행 중인 파이프라인은 편집할 수 없습니다.

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

## 추가 비프로덕션 파이프라인 작업 {#additional-nonprod-actions}

### 비프로덕션 파이프라인 실행 {#run-nonprod}

파이프라인 카드에서 프로덕션 파이프라인을 실행할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **실행**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

### 비프로덕션 파이프라인 삭제 {#delete-nonprod}

파이프라인 카드에서 프로덕션 파이프라인을 삭제할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **삭제**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)
