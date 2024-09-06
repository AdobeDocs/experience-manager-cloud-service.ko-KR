---
title: 저장소 액세스 정보
description: Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 Adobe 관리 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 96%

---


# 저장소 액세스 정보 {#accessing-repos}

Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 Adobe 관리 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.

## 개요 페이지에서 저장소 정보 액세스 {#overview-page}

Cloud Manager를 사용하면 파이프라인 카드에 있는 **저장소 정보 액세스** 버튼을 사용하여 Adobe 관리 저장소에 대한 저장소 액세스를 쉽게 검색할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

   ![환경 카드의 저장소 정보 액세스 버튼](assets/pipelines-card.png)

1. **저장소 정보 액세스** 버튼을 탭하거나 클릭하여 **저장소 정보** 대화 상자를 열고 다음을 확인합니다.

   * git 사용자 이름
   * git 암호
   * Cloud Manager git 저장소의 URL
   * 사전 설치 git 명령을 사용하여 git 저장소 및 푸시 코드에 대한 연결을 빠르게 추가할 수 있습니다.

   ![저장소 정보 창](assets/repository-info.png)

1. 암호에 액세스하려면 새로운 암호를 생성해야 합니다. 암호를 생성하려면 **암호 생성** 버튼을 탭하거나 클릭합니다.

1. **계속 진행하시겠습니까?** 대화 상자에서 **암호 생성**&#x200B;을 탭하거나 클릭하여 암호 생성을 확인합니다.

   ![암호 생성 확인](assets/confirm-password-generation.png)

1. 암호가 생성되어 **암호** 필드에 복사할 수 있도록 표시됩니다.

   * 암호를 생성하면 이전 암호가 무효화됩니다.
   * Cloud Manager는 암호를 저장하지 않습니다. 이 암호를 안전하게 저장하는 것은 귀하의 책임입니다.
   * Cloud Manager는 암호를 저장하지 않으므로 암호를 잊어버린 경우 새 암호를 다시 생성해야 합니다.

   ![생성된 암호의 예](assets/generated-password.png)

이러한 자격 증명을 사용하여 저장소의 로컬 복사본을 복제하고 해당 로컬 저장소를 변경할 수 있으며 준비가 되면 Cloud Manager의 원격 코드 저장소에 코드 변경 사항을 다시 커밋할 수 있습니다.

>[!NOTE]
>
>* **저장소 정보 액세스** 옵션은 **개발자** 또는 **배포 관리자** 역할이 있는 사용자에게 표시됩니다.
>* **저장소 정보 액세스** 버튼은 Adobe 관리 저장소에 대한 저장소 액세스 정보만 표시합니다. [비공개 저장소](private-repositories.md)에 대한 액세스 정보는 Cloud Manager에서 사용할 수 없습니다.

## 저장소 창에서 저장소 정보 액세스 {#repositories-window}

**저장소 정보 액세스** 단추는 [**저장소** 창](managing-repositories.md)의 도구 모음에서도 사용할 수 있습니다. Adobe 관리 저장소 액세스에 대한 정보와 동일한 내용이 표시됩니다.

## 액세스 암호 취소 {#revoke-password}

언제든지 액세스 암호를 취소할 수 있습니다. 암호를 취소하려면 [이 요청에 대한 지원 티켓을 만드십시오](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support).

티켓이 우선적으로 처리되며 1일 이내에 취소해야 합니다.
