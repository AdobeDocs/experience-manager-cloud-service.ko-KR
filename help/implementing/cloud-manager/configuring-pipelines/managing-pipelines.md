---
title: 파이프라인 관리
description: 편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 3%

---

# 파이프라인 관리 {#managing-pipelines}

편집, 실행 및 삭제를 포함하여 기존 파이프라인을 관리하는 방법을 알아봅니다.

## 파이프라인 카드 {#pipeline-card}

다음 **파이프라인** 카드 **프로그램 개요** cloud Manager의 페이지에서는 모든 파이프라인과 해당 현재 상태에 대한 개요를 제공합니다.

![Cloud Manager의 파이프라인 카드](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

각 파이프라인 옆에 있는 줄임표 단추를 클릭하여 다음 작업을 수행할 수 있습니다.

* [파이프라인 실행](#running-pipelines)
* [파이프라인 편집](#editing-pipelines)
* [파이프라인 삭제](#deleting-pipelines)
* [세부 사항 보기](#view-details)

파이프라인 목록 하단에는 일반적인 옵션이 있습니다.

* **추가** - 종료 [새 프로덕션 파이프라인 추가](configuring-production-pipelines.md) 또는 [새 비프로덕션 파이프라인 추가](configuring-non-production-pipelines.md)
* **모두 표시** - 사용자를 파이프라인 화면으로 이동하여 보다 자세한 테이블에 있는 모든 파이프라인을 확인합니다.
* **보고서 정보에 액세스** - Cloud Manager git 저장소에 액세스하는 데 필요한 정보를 표시합니다
* **추가 정보** - CI/CD 파이프라인 설명서 리소스로 이동합니다.

## 파이프라인 실행 {#running-pipelines}

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭한 다음 실행하는 파이프라인 옆에 있는 생략 부호 버튼을 클릭합니다. 선택 **실행** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. 파이프라인 실행이 시작되고 로 표시됩니다 **상태** 열.

생략 부호 단추를 다시 클릭하고 을 선택하여 실행 세부 사항을 볼 수 있습니다 **[세부 사항 보기](#view-details)**

파이프라인 유형에 따라 줄임표 버튼을 다시 클릭하고 을 선택하여 실행을 취소할 수 있습니다 **취소**.

## 파이프라인 편집 {#editing-pipelines}

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭하고 편집할 파이프라인 옆에 있는 줄임표 단추를 클릭한 다음 를 선택합니다 **편집** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. 다음 **프로덕션 파이프라인 편집** 또는 **비프로덕션 파이프라인 편집** 파이프라인을 생성할 때 입력한 것과 동일한 세부 정보를 편집할 수 있는 대화상자가 표시됩니다.

   * 파이프라인에 사용할 수 있는 모든 필드 및 구성 옵션에 대한 자세한 내용은 다음 페이지를 참조하십시오.
      * [프로덕션 파이프라인 구성](configuring-production-pipelines.md)
      * [비프로덕션 파이프라인 구성](configuring-non-production-pipelines.md)

1. 클릭 **업데이트** 파이프라인 편집을 완료하면 됩니다.

>[!NOTE]
>
>실행 중인 파이프라인은 편집할 수 없습니다.

## 파이프라인 삭제 {#deleting-pipelines}

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭한 다음 실행하는 파이프라인 옆에 있는 생략 부호 버튼을 클릭합니다. 선택 **삭제** 메뉴 아래의 제품에서 사용할 수 있습니다.

>[!NOTE]
>
>실행 중인 파이프라인은 삭제할 수 없습니다.

## 세부 사항 보기 {#view-details}

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭한 다음 실행하는 파이프라인 옆에 있는 생략 부호 버튼을 클릭합니다. 선택 **세부 사항 보기** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. 실행 중인 파이프라인의 세부 사항 페이지로 이동합니다.

![파이프라인 세부 정보](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

여기에서 파이프라인의 다양한 단계 상태를 확인하고 진단 목적으로 빌드 로그를 검색할 수 있습니다. 문서를 참조하십시오 [코드 배포](/help/implementing/cloud-manager/deploy-code.md) 추가 정보.

>[!NOTE]
>
>실행 중이거나 한 번 이상 실행된 파이프라인의 세부 사항만 볼 수 있습니다.
