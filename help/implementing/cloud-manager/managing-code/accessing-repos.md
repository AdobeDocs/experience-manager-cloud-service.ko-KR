---
title: 저장소 액세스 정보
description: Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 Adobe 관리 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0b39fc4dcaf86d436547d3941b1f12bca8c5bc9b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 11%

---


# 저장소 액세스 정보 {#accessing-repos}

Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 Adobe 관리 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.

## 개요 페이지에서 저장소 정보 액세스 {#overview-page}

Cloud Manager를 사용하면 Adobe 관리 저장소에 대한 저장소 액세스 정보를 쉽게 검색할 수 있습니다. **저장소 정보 액세스** 파이프라인 카드에서 자주 사용할 수 있는 버튼입니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **파이프라인** 의 카드 **프로그램 개요** 페이지를 가리키도록 업데이트하는 중입니다.

   ![환경 카드의 저장소 정보 액세스 버튼](assets/pipelines-card.png)

1. 을(를) 탭하거나 클릭합니다 **저장소 정보 액세스** 단추를 클릭하여 열기 **저장소 정보** 대화 상자 및 보기:

   * git 사용자 이름
   * git 암호입니다.
   * Cloud Manager git 저장소의 URL
   * git 저장소에 원격으로 빠르게 추가하고 코드를 푸시할 수 있는 git 명령이 사전 빌드되었습니다.

   ![저장소 정보 창](assets/repository-info.png)

1. 암호에 액세스하려면 새 암호를 생성해야 합니다. 이렇게 하려면 다음을 탭하거나 클릭합니다 **암호 생성** 단추를 클릭합니다.

1. 에서 암호 생성 확인 **확실합니까?** 탭하거나 클릭하여 표시되는 대화 상자 **암호 생성**.

   ![암호 생성 확인](assets/confirm-password-generation.png)

1. 암호가 생성되고에서 복사할 수 있도록 표시됩니다. **암호** 필드.

   * 암호를 생성하면 이전 암호가 무효화됩니다.
   * Cloud Manager는 암호를 저장하지 않습니다. 이 암호를 안전하게 저장하는 것은 사용자의 책임입니다.
   * Cloud Manager는 암호를 저장하지 않으므로 암호를 푼 경우 새 암호를 다시 생성해야 합니다.

   ![생성된 암호의 예](assets/generated-password.png)

이러한 자격 증명을 사용하여 저장소의 로컬 복사본을 복제하고, 해당 로컬 저장소를 변경하고, 준비가 되면 Cloud Manager의 원격 코드 저장소에 코드 변경 사항을 다시 커밋할 수 있습니다.

>[!NOTE]
>
>* **저장소 정보 액세스** 옵션은 **개발자** 또는 **배포 관리자** 역할이 있는 사용자에게 표시됩니다.
>* 다음 **저장소 정보 액세스** 단추는 Adobe 관리 저장소에 대한 저장소 액세스 정보만 표시합니다. 다음에 대한 액세스 정보: [개인 저장소](private-repositories.md) 는 Cloud Manager에서 사용할 수 없습니다.

## 저장소 창에서 저장소 정보에 액세스 {#repositories-window}

An **저장소 정보 액세스** 단추는 의 도구 모음에서도 사용할 수 있습니다 [**저장소** 창.](managing-repositories.md) Adobe 관리 저장소에 액세스하는 것과 동일한 정보가 표시됩니다.

## 액세스 암호 취소 {#revoke-password}

액세스 암호는 언제든지 취소할 수 있습니다. 그렇게 해 주십시오 [이 요청에 대한 지원 티켓을 만듭니다.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

티켓은 우선순위가 높은 것으로 처리되며 하루 안에 취소되어야 합니다.
