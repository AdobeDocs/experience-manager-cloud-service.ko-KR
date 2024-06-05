---
title: 파이프라인 관리
description: 편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 54%

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

**파이프라인** 창에는 선택한 프로그램에 대한 모든 파이프라인의 전체 목록이 표시됩니다. 이는 [파이프라인 카드](#pipeline-card)에서 제공되는 정보보다 더 포괄적인 정보를 담고 있으므로 유용합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 다음에서 **프로그램 개요** 페이지에서 **파이프라인** 탭을으로 전환합니다. **파이프라인** 창.

1. 여기에서 프로그램에 대한 모든 파이프라인 목록을 확인하고 에서와 같이 파이프라인 실행을 시작 및 중지할 수 있습니다. **파이프라인 카드**.

파이프라인이 실행 중인 경우 의 정보 아이콘을 탭합니다. **상태** 열에는 실행에 대한 세부 사항이 표시됩니다.

![파이프라인 실행 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

**세부 정보 보기**&#x200B;를 탭하거나 클릭하면 [파이프라인 실행에 대한 세부 정보를 확인할 수 있습니다.](#view-details)

파이프라인의 생략 부호를 탭하거나 클릭하여 다음과 같은 파이프라인 상태에 적합한 추가 작업을 수행할 수도 있습니다. [편집](#editing-pipelines) 또는 [실행을 취소합니다.](#cancel)

![파이프라인 작업](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

## 활동 창 {#activity}

다음 **활동** 창에는 선택한 프로그램에 대한 모든 파이프라인 실행과 기타 중요한 프로그램 이벤트의 전체 목록이 표시됩니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음에서 **프로그램 개요** 페이지에서 **활동** 탭을으로 전환합니다. **활동** 창.

1. 여기에서는 현재 실행과 이전 실행을 포함하여 프로그램에 대한 모든 파이프라인 실행 목록을 볼 수 있습니다.

파이프라인이 실행 중인 경우 의 정보 아이콘을 탭합니다. **상태** 열에는 실행에 대한 세부 사항이 표시됩니다.

![파이프라인 실행 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

파이프라인 실행을 나타내는 행을 탭하거나 클릭하면 [파이프라인 실행에 대한 세부 사항입니다.](#view-details)

줄임표 버튼을 탭하거나 클릭하여 자세한 내용을 보거나 로그를 다운로드하는 등 파이프라인 실행에 대한 추가 작업을 수행할 수도 있습니다. [파이프라인 세부 정보 페이지.](#view-details)

![파이프라인 실행 작업](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## 파이프라인 실행 {#running-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 다음에서 카드 **프로그램 개요** 을(를) 페이징한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭합니다. **실행** 메뉴에서 삭제할 수 있습니다.

1. 파이프라인 실행이 시작되고 **상태** 열에 표시됩니다.

줄임표 버튼을 다시 클릭하고 **[세부 정보 보기](#view-details)**&#x200B;를 선택하면 실행 세부 정보를 볼 수 있습니다.

파이프라인 유형에 따라 줄임표 버튼을 다시 클릭하고 **취소**&#x200B;를 선택하여 실행을 취소할 수 있습니다.

## 파이프라인 편집 {#editing-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 다음에서 카드 **프로그램 개요** 편집할 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 을 선택합니다 **편집** 메뉴에서 삭제할 수 있습니다.

1. **프로덕션 파이프라인 편집** 또는 **비프로덕션 파이프라인 편집** 대화 상자가 표시되어 파이프라인을 생성할 때 입력한 것과 동일한 세부 정보를 편집할 수 있습니다.

   * 파이프라인에 사용할 수 있는 필드 및 구성 옵션에 대한 자세한 내용은 다음 페이지를 참조하십시오.
      * [프로덕션 파이프라인 구성](configuring-production-pipelines.md)
      * [비프로덕션 파이프라인 구성](configuring-non-production-pipelines.md)

1. 클릭 **업데이트** 파이프라인 편집이 완료되면

>[!NOTE]
>
>실행 중인 파이프라인은 편집할 수 없습니다.

## 파이프라인 삭제 {#deleting-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 다음에서 카드 **프로그램 개요** 을(를) 페이징한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭합니다. **삭제** 메뉴에서 삭제할 수 있습니다.

>[!NOTE]
>
>실행 중인 파이프라인은 삭제할 수 없습니다.

## 파이프라인 세부 정보 보기 {#view-details}

파이프라인의 세부 정보를 보고 마지막 실행의 상태와 로그를 볼 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 다음에서 카드 **프로그램 개요** 을(를) 페이징한 다음 실행하는 파이프라인 옆에 있는 줄임표 버튼을 클릭합니다. **세부 정보 보기** 메뉴에서 삭제할 수 있습니다.

1. 실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

![파이프라인 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

여기에서 파이프라인의 다양한 단계 상태를 확인하고 진단 목적으로 빌드 로그를 검색할 수 있습니다. 문서 보기 [코드 배포](/help/implementing/cloud-manager/deploy-code.md) 코드 배포 및 테스트 실행에 대한 자세한 내용을 보려면 를 클릭하십시오.

모든 파이프라인 실행 단계는 아직 시작되지 않은 단계가 회색으로 바뀌어 표시됩니다. 완료된 단계에는 기간이 표시됩니다.

파이프라인 단계가 완료되면 요약이 표시됩니다.

![단계 요약](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

다음 항목 선택 **세부 정보 보기** 표시할 링크 **기간** 섹션. 여기에는 해당 프로그램의 과거 트렌드를 기반으로 한 파이프라인의 평균 기간이 포함됩니다.

![기간](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

>[!NOTE]
>
>실행 중이거나 한 번 이상 실행된 파이프라인의 세부 정보만 볼 수 있습니다.

## 파이프라인 취소 {#cancel}

파이프라인이 유효성 검사 또는 빌드 이미지 단계에 있는 경우 파이프라인 실행을 안전하게 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 프로그램 개요 페이지에서 취소할 파이프라인의 줄임표 버튼을 클릭합니다. **파이프라인** 카드.

   ![파이프라인 취소](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. 선택 **취소**.

또는 파이프라인 세부 정보 페이지에서 파이프라인을 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 의 탭 **프로그램 개요** 페이지를 만들고 취소할 파이프라인을 선택합니다.

1. 실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

   ![파이프라인 세부 정보 취소](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. 선택 **취소**.
