---
title: 공유 큐 구성
seo-title: Configure shared queues
description: 에서 Forms 중심의 워크플로우에 공유 큐를 사용하는 방법을 알아봅니다 [!DNL AEM Forms] OSGi에서
seo-description: Learn how to use shared queues for Forms-centric workflows on [!DNL AEM Forms] on OSGi.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 2%

---


# 사용자의 받은 편지함 항목 공유 및 액세스 요청 {#share-and-request-access}

큐는 사용자의 AEM 받은 편지함에 있는 항목 목록입니다. 사용자에게 할당된 항목이나 사용자가 구성원으로 있는 그룹에 공유된 항목일 수 있습니다. 받은 편지함에 액세스하여 받은 편지함 항목을 보고 작업을 수행할 수 있습니다. 예를 들어 다른 사용자와 항목을 공유합니다.

받은 편지함 항목을 다른 사용자와 공유할 수도 있습니다. 다른 사용자가 받은 편지함 항목에 액세스할 수 있게 되면 사용자는 소유권을 주장하고 공유 항목에 적절한 작업을 수행할 수 있습니다. 마찬가지로 다른 사용자의 받은 편지함 항목에 대한 액세스를 요청할 수 있습니다.

## 전제 조건 {#pre-requisites}

로그인한 사용자는 [!DNL `workflow-users`] 그룹에 속해 있어야 합니다. 사용자는 공개 프로필을 활성화한 사용자 또는 로그인한 사용자에게만 읽기 권한이 있는 사용자에게만 항목을 공유하거나 항목에 대한 액세스를 요청할 수 있습니다.

## 받은 편지함의 단일 항목 또는 모든 항목을 다른 사용자와 공유

AEM 받은 편지함을 사용하면 받은 편지함의 단일 또는 모든 항목을 다른 사용자와 공유할 수 있습니다.

### 모든 받은 편지함 항목 공유

다음 단계를 수행하여 받은 편지함의 모든 항목을 다른 사용자와 공유합니다.

1. AEM 인스턴스에 로그인합니다. 탭하기 ![받은 편지함](assets/bell.svg) 아이콘 및 탭 **[!UICONTROL 모두 보기]**. 받은 편지함 항목 목록이 표시됩니다.
1. 탭하기 ![보기 선택기](assets/viewlist.svg) 또는 ![보기 선택기](assets/calendar.svg) 아이콘 옆에 있는 를 클릭합니다. **[!UICONTROL 만들기]** 버튼 및 탭 **[!UICONTROL 설정]**. 설정 대화 상자가 나타납니다.
1. 를 엽니다. **[!UICONTROL 공유]** 탭 을 클릭합니다.
1. 에 사용자 이름을 입력합니다. **[!UICONTROL 받은 편지함 항목에 대한 액세스 권한 부여]** 텍스트 상자 및 탭 **[!UICONTROL 승인]**. 단계를 반복하여 사용자를 더 추가합니다. 항목에 액세스할 수 있는 모든 사용자는 **사용자 이름** 섹션을 참조하십시오.
1. 탭 **[!UICONTROL 저장]**.

>[!NOTE]
>
>(Forms 중심의 워크플로우 항목에만 해당) **[할당자가 받은 편지함 공유를 통해 공유 허용](aem-forms-workflow-step-reference.md)** 옵션 **작업 할당** 단계를 수행하십시오. 위의 옵션이 활성화된 항목만 다른 사용자에게 표시됩니다.

### 개별 항목 공유

다음 단계를 수행하여 다른 사용자와 받은 편지함 항목을 공유합니다.

1. AEM 인스턴스에 로그인합니다. 탭하기 ![받은 편지함](assets/bell.svg) 아이콘 및 탭 **[!UICONTROL 모두 보기]**. 받은 편지함 항목 목록이 표시됩니다.
1. 항목을 선택하고 탭합니다 **[!UICONTROL 공유]**. 대화 상자가 나타납니다.
1. 이 항목을 공유할 사용자 추가 텍스트 상자에 사용자 이름을 입력하고 **[!UICONTROL 추가]**. 단계를 반복하여 사용자를 더 추가합니다. 항목에 액세스할 수 있는 모든 사용자는 **[!UICONTROL 사용자 이름]** 섹션을 참조하십시오.
1. 탭 **[!UICONTROL 저장]**.


>[!NOTE]
>
>(Forms 중심의 워크플로우 항목에만 해당) **[할당자가 받은 편지함에서 명시적으로 공유할 수 있도록 허용](aem-forms-workflow-step-reference.md)** 옵션 **작업 할당** 단계를 수행하십시오. 위의 옵션이 활성화된 항목만 다른 사용자에게 표시됩니다.

## 받은 편지함 항목 액세스 요청 {#request-access}

다른 사용자의 받은 편지함 항목에 대한 액세스를 요청할 수 있습니다. 액세스 권한이 부여되면 공유 항목에 대해 적절한 작업을 보고, 요청하고 수행할 수 있습니다. 다른 사용자의 받은 편지함 항목에 대한 액세스를 요청하려면 다음 단계를 수행하십시오.

1. AEM 인스턴스에 로그인합니다. 탭하기 ![보기 선택기](assets/bell.svg) 아이콘 및 탭 **[!UICONTROL 모두 보기]**.
1. 탭하기 ![보기 선택기](assets/viewlist.svg) 또는 ![보기 선택기](assets/calendar.svg) 아이콘 옆에 있는 를 클릭합니다. **[!UICONTROL 만들기]** 버튼 및 탭 **[!UICONTROL 설정]**. 설정 대화 상자가 나타납니다.
1. 에 사용자 이름을 입력합니다. **[!UICONTROL 사용자의 받은 편지함 항목에 대한 액세스 요청]** 텍스트 상자 및 탭 **[!UICONTROL 요청]**. 사용자에게 요청이 전송되고 사용자 이름에 대한 요청 상태가 표시됩니다. 단계를 반복하여 사용자를 더 추가합니다.
1. 탭 **[!UICONTROL 저장]**. 요청은 사용자에게 받은 편지함 항목으로 전송됩니다. 사용자는 항목을 선택하고 승인 또는 거부 를 탭하여 액세스 권한을 부여하거나 거부할 수 있습니다.


## 다른 사용자가 공유한 클레임 항목 {#claim-items}

공유 항목에 대한 작업은 승인 후 시작할 수 있습니다. 여러 사용자가 단일 항목에서 작업할 수 없습니다. 항목을 청구하려면 다음 단계를 수행하십시오.

1. AEM 인스턴스에 로그인합니다. 받은 편지함 탭 ![받은 편지함](assets/bell.svg) 아이콘 및 탭 **[!UICONTROL 모두 보기]**.
1. 탭하기 ![컨텐츠만](assets/railleft.svg) 아이콘을 클릭하여 필터 선택기를 엽니다.
1. 탭하기 **[!UICONTROL 할당자 선택]** 드롭다운을 클릭하여 받은 편지함 항목을 사용자와 공유한 사용자를 보고 선택합니다.
1. 항목을 선택하고 탭합니다 **[!UICONTROL 청구]**. 항목이 받은 편지함에 추가됩니다.

## 요청된 항목 릴리스 {#release-items}

공유 항목은 승인 후 작업해야 합니다. 다른 사용자는 요구한 항목을 보거나 작업할 수 없습니다. 항목에 대해 계속 작업할 수 없으면 다시 풀로 해제할 수 있습니다.   품목을 릴리즈하면 다른 사용자가 해당 품목에 대해 청구 및 작업할 수 있습니다.

다음 단계를 수행하여 항목을 해제합니다.

1. AEM 인스턴스에 로그인합니다. 받은 편지함 탭 ![받은 편지함](assets/bell.svg) 아이콘 및 탭 **[!UICONTROL 모두 보기]**. 받은 편지함 항목 목록이 표시됩니다.
1. 릴리스할 항목을 선택하고 탭합니다 **[!UICONTROL 클레임 해제]**. 항목이 다시 풀에 추가됩니다. 이제 다른 사용자가 해당 항목을 요구할 수 있습니다.

## 제한 사항 {#limitations}

* 그룹과 항목을 공유할 수 없습니다.
* 프로젝트 작업 공유는 지원되지 않습니다.
