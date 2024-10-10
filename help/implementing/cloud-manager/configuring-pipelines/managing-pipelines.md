---
title: 파이프라인 관리
description: 편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f7a8e823f058115f11241f0864517432a7dea5ab
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 34%

---


# 파이프라인 관리 {#managing-pipelines}

편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.

## 파이프라인 카드 {#pipeline-card}

Cloud Manager의 **프로그램 개요** 페이지에 있는 **파이프라인** 카드는 모든 파이프라인과 현재 상태에 대한 개요를 제공합니다.

![Cloud Manager의 파이프라인 카드](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

각 파이프라인 옆에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 다음 작업을 수행할 수 있습니다.

* [파이프라인 실행](#running-pipelines)
* [파이프라인 취소](#cancel)
* [파이프라인 편집](#editing-pipelines)
* [파이프라인 삭제](#deleting-pipelines)
* [파이프라인의 마지막 실행 세부 정보 보기](#view-details)

파이프라인 목록의 맨 아래에는 다음과 같은 일반 옵션이 있습니다.

* **추가** - [새 프로덕션 파이프라인을 추가](configuring-production-pipelines.md) 또는 [새 비프로덕션 파이프라인을 추가](configuring-non-production-pipelines.md)
* **모두 표시** - 파이프라인 화면으로 사용자를 이동하여 더 자세한 테이블에서 모든 파이프라인을 볼 수 있습니다.
* **저장소 액세스 정보** - Cloud Manager git 저장소에 액세스하는 데 필요한 정보를 표시합니다.
* **자세히 알아보기** - CI/CD 파이프라인 설명서 리소스로 이동합니다.

## 파이프라인 페이지 {#pipelines}

**파이프라인** 페이지에는 선택한 프로그램에 대한 모든 파이프라인의 전체 목록이 표시됩니다. 이 정보는 [파이프라인 카드](#pipeline-card)에서 사용할 수 있는 것보다 더 포괄적인 정보를 제공하므로 유용합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 ![파이프라인 탭 - 워크플로 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **파이프라인** 탭을 클릭합니다.

1. **파이프라인** 페이지에서 **파이프라인 카드**&#x200B;에서와 같이 프로그램에 대한 모든 파이프라인 목록을 보고 파이프라인 실행을 시작 및 중지할 수 있습니다.

파이프라인이 실행 중인 경우 **상태** 열의 ![정보 - 보통 아이콘](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg)을 클릭하여 실행에 대한 세부 정보가 포함된 팝업을 표시합니다. 팝업에서 **세부 정보 보기**&#x200B;를 클릭하여 [파이프라인 실행에 대한 세부 정보를 봅니다](#view-details).

![파이프라인 실행 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)


파이프라인 옆에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 [편집](#editing-pipelines) 또는 [실행 취소](#cancel)와 같은 파이프라인 상태에 적합한 추가 작업을 수행할 수도 있습니다.

![파이프라인 작업](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

## 활동 페이지 {#activity}

**활동** 페이지에는 선택한 프로그램에 대한 모든 파이프라인 실행과 기타 중요한 프로그램 이벤트의 전체 목록이 표시됩니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지의 사이드 메뉴에서 ![벨 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) **활동**&#x200B;을 클릭합니다.

1. **활동** 페이지에서 현재 및 이전 실행을 포함하여 프로그램에 대한 모든 파이프라인 실행 목록을 볼 수 있습니다.

파이프라인이 실행 중인 경우 **상태** 열에서 ![정보 - 보통 아이콘](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg)을 클릭하여 실행 정보를 보여주는 팝업을 표시할 수 있습니다.

![파이프라인 실행 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

파이프라인 실행을 나타내는 행을 클릭하여 [파이프라인 실행에 대한 세부 정보를 봅니다](#view-details).

![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 자세한 내용을 보거나 로그를 다운로드하는 등 파이프라인 실행에 대한 추가 작업을 수행할 수도 있습니다. 그러면 [파이프라인 세부 정보 페이지](#view-details)로 이동합니다.

![파이프라인 실행 작업](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## 파이프라인 실행 {#running-pipelines}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

1. 실행하는 파이프라인 옆에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 ![실행 - 재생 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PlayCircle_18_N.svg) **실행**&#x200B;을 클릭합니다.

   파이프라인 실행이 시작되고 **상태** 열에 진행률이 표시됩니다.

![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 다시 클릭하고 **[세부 정보 보기](#view-details)**&#x200B;를 클릭하면 실행 세부 정보를 볼 수 있습니다.

파이프라인 유형에 따라 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 다시 클릭하고 **취소**&#x200B;를 클릭하여 실행을 취소할 수 있습니다.

## 파이프라인 편집 {#editing-pipelines}

파이프라인이 실행되고 있지 않으면 편집할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

1. 편집할 파이프라인 옆에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **편집**&#x200B;을 클릭합니다.

1. **프로덕션 파이프라인 편집** 또는 **비프로덕션 파이프라인 편집** 대화 상자에서 파이프라인을 만들 때 입력한 것과 동일한 세부 정보를 편집합니다.

   파이프라인에 사용할 수 있는 필드 및 구성 옵션에 대한 자세한 내용은 다음 페이지를 참조하십시오.
   * [프로덕션 파이프라인 구성](configuring-production-pipelines.md)
   * [비프로덕션 파이프라인 구성](configuring-non-production-pipelines.md)

1. 완료되면 **업데이트**&#x200B;를 클릭하세요.

>[!NOTE]
>
>웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다. 제한 사항에 대한 자세한 내용 및 전체 목록은 [Cloud Manager에 개인 GitHub 저장소 추가](/help/implementing/cloud-manager/managing-code/private-repositories.md)를 참조하십시오.

## 파이프라인 삭제 {#deleting-pipelines}

파이프라인이 실행되고 있지 않으면 삭제할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

1. 실행하는 파이프라인 옆에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **삭제**&#x200B;를 클릭합니다.


## 파이프라인의 마지막 실행 세부 정보 보기 {#view-details}

파이프라인의 세부 정보를 확인하여 가장 최근 실행의 상태 및 로그를 볼 수 있습니다. 하지만 파이프라인이 현재 실행 중이거나 한 번 이상 실행된 경우에만 세부 정보에 액세스할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

1. 드롭다운 메뉴에서 실행하는 파이프라인 옆에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **마지막 실행 보기**&#x200B;를 클릭합니다.

   실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

   ![파이프라인 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

   여기에서 파이프라인의 다양한 단계 상태를 확인하고 진단 목적으로 빌드 로그를 검색할 수 있습니다. 코드 배포 및 테스트 실행에 대한 자세한 내용은 [코드 배포](/help/implementing/cloud-manager/deploy-code.md)를 참조하십시오.

   모든 파이프라인 실행 단계는 아직 시작되지 않은 단계가 회색으로 바뀌어 표시됩니다. 완료된 단계에는 기간이 표시됩니다.

   파이프라인 단계가 완료되면 요약이 표시됩니다.

   ![단계 요약](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

1. **세부 정보 보기**&#x200B;를 클릭하여 **기간** 섹션을 확장합니다. 그러면 프로그램의 기록 추세를 기반으로 파이프라인의 평균 기간을 볼 수 있습니다.

   ![기간](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

1. 파이프라인에 문제 플래그를 지정하는 **코드 검색** 단계가 포함된 경우 **세부 정보 다운로드**&#x200B;를 클릭하여 통과하지 못한 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md) 목록에 액세스하십시오.

   ![코드 품질 문제](assets/managing-pipelines-code-quality-issues.png)

   CSV 파일에는 프로젝트와 관련하여 문제가 있는 코드의 경로를 표시하는 **프로젝트 파일 위치** 열이 포함되어 있습니다. 반대로 **파일 위치** 열은 Maven이 생성한 경로를 반영합니다.

   ![프로젝트 코드 스캔 문제 세부 정보](assets/managing-pipelines-code-quality-details.png)

## 파이프라인 취소 {#cancel}

유효성 검사 또는 이미지 빌드 단계에 있는 경우 파이프라인 실행을 안전하게 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 프로그램 개요 페이지에서 **파이프라인** 카드에서 취소할 파이프라인의 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

   ![파이프라인 취소](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. **취소**&#x200B;를 클릭합니다.

또는 파이프라인 세부 정보 페이지에서 파이프라인을 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 ![파이프라인 탭 - 워크플로 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **파이프라인** 탭으로 이동하여 취소할 파이프라인을 선택합니다.

   실행 중인 파이프라인의 세부 정보 페이지로 이동합니다.

   ![파이프라인 세부 정보 취소](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. **취소**&#x200B;를 클릭합니다.
