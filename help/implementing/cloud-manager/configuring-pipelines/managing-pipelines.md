---
title: 파이프라인 관리
description: 편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: 01a89f779689733fb82a556291e091026def63e0
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 60%

---


# 파이프라인 관리 {#managing-pipelines}

편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.

## 파이프라인 카드 {#pipeline-card}

Cloud Manager의 **프로그램 개요** 페이지에 있는 **파이프라인** 카드는 모든 파이프라인과 현재 상태에 대한 개요를 제공합니다.

![Cloud Manager의 파이프라인 카드](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

각 파이프라인 옆에 있는 줄임표 버튼을 클릭하여 다음 작업을 수행할 수 있습니다.

* [파이프라인 실행](#running-pipelines)
* [파이프라인 편집](#editing-pipelines)
* [파이프라인 삭제](#deleting-pipelines)
* [세부 정보 보기](#view-details)

파이프라인 목록의 맨 아래에는 일반 옵션이 있습니다.

* **추가** - [새 프로덕션 파이프라인을 추가](configuring-production-pipelines.md)하거나 [새 비프로덕션 파이프라인을 추가](configuring-non-production-pipelines.md)합니다.
* **모두 표시** - 파이프라인 화면으로 사용자를 이동하여 더 자세한 테이블에서 모든 파이프라인을 볼 수 있습니다.
* **저장소 액세스 정보** - Cloud Manager git 저장소에 액세스하는 데 필요한 정보를 표시합니다.
* **자세히 알아보기** - CI/CD 파이프라인 설명서 리소스로 이동합니다.

## 파이프라인 창 {#pipelines}

다음 **파이프라인** 선택한 프로그램에 대한 모든 파이프라인의 전체 목록이 창에 표시됩니다. 에서 사용할 수 있는 정보보다 더 포괄적인 정보를 제공하므로 유용합니다. [파이프라인 카드.](#pipeline-card)

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음에서 **프로그램 개요** 페이지, 탭 또는 클릭 **파이프라인** 탭을으로 전환합니다. **파이프라인** 창.

1. 여기에서 프로그램의 모든 파이프라인 목록을 확인하고 에서와 같이 파이프라인 실행을 시작 및 중지할 수 있습니다. **파이프라인 카드**.

파이프라인이 실행 중인 경우 마우스를 위로 가져갑니다. **상태** 열에는 실행에 대한 세부 사항이 표시됩니다.

![파이프라인 실행 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

탭 또는 클릭 **세부 정보 보기** 다음 위치로 이동합니다. [파이프라인 실행에 대한 세부 사항입니다.](#view-details)

## 활동 창 {#activity}

다음 **활동** 선택한 프로그램에 대한 모든 파이프라인 실행의 전체 목록이 창에 표시됩니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음에서 **프로그램 개요** 페이지, 탭 또는 클릭 **활동** 탭을으로 전환합니다. **활동** 창.

1. 여기에서 현재 및 이전 실행을 포함하여 프로그램에 대한 모든 파이프라인 실행 목록을 볼 수 있습니다.

파이프라인이 실행 중인 경우 마우스를 위로 가져갑니다. **상태** 열에는 실행에 대한 세부 사항이 표시됩니다.

![파이프라인 실행 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

탭 또는 클릭 **세부 정보 보기** 다음 위치로 이동합니다. [파이프라인 실행에 대한 세부 사항입니다.](#view-details)

## 파이프라인 실행 {#running-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 실행할 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **실행**&#x200B;을 선택합니다.

1. 파이프라인 실행이 시작되고 **상태** 열에 표시됩니다.

줄임표 버튼을 다시 클릭하고 **[세부 정보 보기](#view-details)**&#x200B;를 선택하면 실행 세부 정보를 볼 수 있습니다.

파이프라인 유형에 따라 줄임표 버튼을 다시 클릭하고 **취소**&#x200B;를 선택하여 실행을 취소할 수 있습니다.

## 파이프라인 편집 {#editing-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 편집할 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **편집**&#x200B;을 선택합니다.

1. **프로덕션 파이프라인 편집** 또는 **비프로덕션 파이프라인 편집** 대화 상자가 표시되어 파이프라인을 생성할 때 입력한 것과 동일한 세부 정보를 편집할 수 있습니다.

   * 파이프라인에 사용할 수 있는 모든 필드 및 구성 옵션에 대한 자세한 내용은 다음 페이지를 참조하십시오.
      * [프로덕션 파이프라인 구성](configuring-production-pipelines.md)
      * [비프로덕션 파이프라인 구성](configuring-non-production-pipelines.md)

1. 파이프라인 편집이 완료되면 **업데이트**&#x200B;를 클릭합니다.

>[!NOTE]
>
>실행 중인 파이프라인은 편집할 수 없습니다.

## 파이프라인 삭제 {#deleting-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **삭제**&#x200B;를 선택합니다.

>[!NOTE]
>
>실행 중인 파이프라인은 삭제할 수 없습니다.

## 파이프라인 세부 정보 보기 {#view-details}

파이프라인의 세부 정보를 보고 마지막 실행의 상태와 로그를 볼 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **세부 정보 보기**&#x200B;를 선택합니다.

1. 실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

![파이프라인 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

여기에서 파이프라인의 다양한 단계 상태를 확인하고 진단 목적으로 빌드 로그를 검색할 수 있습니다. 문서 보기 [코드 배포](/help/implementing/cloud-manager/deploy-code.md) 코드 배포 및 테스트 실행에 대한 자세한 내용을 보려면 를 클릭하십시오.

파이프라인 실행의 모든 단계가 아직 시작되지 않은 단계는 회색으로 표시됩니다. 완료된 단계는 해당 기간을 표시합니다.

파이프라인 단계가 완료되면 요약이 표시됩니다.

![단계 요약](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

을(를) 탭하거나 클릭합니다 **세부 정보 보기** 표시할 링크 **기간** 섹션. 여기에는 해당 프로그램의 기록 트렌드를 기반으로 하는 파이프라인의 평균 지속 시간이 포함됩니다.

![지속 시간](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

>[!NOTE]
>
>실행 중이거나 한 번 이상 실행된 파이프라인의 세부 정보만 볼 수 있습니다.

## 파이프라인 취소 {#cancel}

파이프라인이 유효성 검사 또는 빌드 이미지 단계에 있는 경우 파이프라인 실행을 안전하게 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 프로그램 개요 페이지에서 취소하려는 파이프라인의 줄임표 버튼을 클릭합니다. **파이프라인** 카드.

   ![파이프라인 취소](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. 탭 또는 클릭 **취소**.

또는 파이프라인 세부 정보 페이지에서 파이프라인을 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 의 탭 **프로그램 개요** 페이지를 연 다음 취소하려는 파이프라인을 탭하거나 클릭합니다.

1. 실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

   ![파이프라인 세부 정보 취소](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. 탭 또는 클릭 **취소**.
