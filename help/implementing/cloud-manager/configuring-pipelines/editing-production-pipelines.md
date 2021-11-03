---
title: 프로덕션 파이프라인 편집
description: 프로덕션 파이프라인 편집
index: false
source-git-commit: 881b4d75a15af55aaf1203e8d673059aab15b793
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# 프로덕션 파이프라인 편집 {#edit-prod-pipeline}

에서 파이프라인 구성을 편집할 수 있습니다 **프로그램 개요** 페이지.

>[!IMPORTANT]
>실행 중인 파이프라인은 편집할 수 없습니다.

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

## 추가 프로덕션 파이프라인 작업 {#additional-prod-actions}

### 프로덕션 파이프라인 실행 {#run-prod}

파이프라인 카드에서 프로덕션 파이프라인을 실행할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **실행**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

### 프로덕션 파이프라인 삭제 {#delete-prod}

파이프라인 카드에서 프로덕션 파이프라인을 삭제할 수 있습니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지.

1. 클릭 **...** 에서 **파이프라인** 카드를 클릭하고 **삭제**&#x200B;아래 그림과 같이,

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >이제 배포 관리자 역할의 사용자는 를 통해 셀프 서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다 **삭제** 옵션 을 클릭합니다.