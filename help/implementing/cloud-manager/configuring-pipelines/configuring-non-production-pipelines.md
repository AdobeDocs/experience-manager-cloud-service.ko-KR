---
title: 비프로덕션 파이프라인 구성
description: Cloud Manager에서 비프로덕션 파이프라인 구성에 대해 알려면 이 페이지를 따르십시오
index: false
source-git-commit: fe3bd08e32cef20403d3d2799d027b3ed03e6d36
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# 비프로덕션 파이프라인 구성 {#configure-non-production-pipeline}

스테이징 및 프로덕션에 배포되는 기본 파이프라인 외에도 고객은 비프로덕션 파이프라인이라고도 하는 추가 파이프라인을 설정할 수 있습니다.

다음 두 가지 유형의 비프로덕션 파이프라인이 있습니다.

1. 코드 품질: Git 분기의 코드에서 코드 품질 검사를 실행합니다. 이 파이프라인은 빌드 및 코드 품질 단계를 실행합니다.
1. 배포: 이 파이프라인은 빌드 및 코드 품질 단계를 실행하는 것 외에도 선택한 비프로덕션 환경에 코드를 AEM as a Cloud Service 환경에 배포합니다.

## 새 비프로덕션 파이프라인 추가 {#adding-non-production-pipeline}

홈 화면에서는 이러한 파이프라인이 새 카드에 나열됩니다.

1. 액세스 권한 **파이프라인** Cloud Manager 홈 화면에서 카드를 생성할 수 있습니다. 클릭 **+추가** 을(를) 선택합니다. **비프로덕션 파이프라인 추가**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가**  대화 상자가 표시됩니다. 생성할 파이프라인 유형을 선택합니다 **코드 품질 파이프라인** 또는 **배포 파이프라인**.

   >[!NOTE]
   >배포 파이프라인의 경우 배포 환경을 선택해야 합니다.

   또한 **배포 트리거** 및 **중요한 지표 실패 동작** 변환 전: **배포 옵션**. 클릭 **계속**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. 선택 **[전체 스택 코드](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** 또는 **[프런트 엔드 코드](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. 을(를) 선택할 수 있습니다 **저장소** 그리고 **Git 분기**. 클릭 **저장**.

   >[!IMPORTANT]
   >선택한 환경에 대해 전체 스택 코드 파이프라인이 이미 존재하는 경우 이 선택이 비활성화됩니다.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

   >[!NOTE]
   >프런트 엔드 파이프라인 구성을 시작하기 전에 사용하기 쉬운 AEM 빠른 사이트 만들기 도구를 통해 엔드 투 엔드 워크플로우를 보려면 AEM 빠른 사이트 만들기 여정 를 참조하십시오. 이 설명서 사이트를 통해 AEM 사이트의 프런트 엔드 개발을 간소화하고 AEM 백엔드 지식이 없는 사용자를 신속하게 사용자 지정할 수 있습니다.

1. 이제 새로 생성된 비프로덕션 파이프라인이 **파이프라인** 카드.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   파이프라인은 아래와 같이 세 가지 작업이 있는 홈 화면의 카드에 표시됩니다.

   * **추가** - 새 파이프라인을 추가할 수 있습니다.
   * **보고서 정보에 액세스** - 사용자가 Cloud Manager Git 리포지토리에 액세스하는 데 필요한 정보를 얻을 수 있도록 해줍니다.
   * **추가 정보** - CI/CD 파이프라인 설명서 리소스를 이해하도록 이동합니다.