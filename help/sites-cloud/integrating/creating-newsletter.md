---
title: Adobe Experience Manager 뉴스레터 만들기
description: 'Adobe Experience Manager 뉴스레터 만들기 '
feature: Administering
role: Admin
source-git-commit: f68f5a457bbbcd76681cccabe5a3f4c92b6f8770
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 2%

---


# Adobe Experience Manager 뉴스레터 만들기 {#creating-newsletter}

아래 표시된 단계를 수행하려면 먼저 다음을 수행해야 합니다 [통합](/help/sites-cloud/integrating/integrating-campaign-classic.md) Adobe Campaign Classic과 AEM as a Cloud Service. 이제 Adobe Campaign Classic과 AEM as a Cloud Service을 모두 구성했으므로 Adobe Experience Manager 뉴스레터를 만드는 방법을 알아봅니다.

1. AEM 작성자 인스턴스에서 페이지 왼쪽 상단에 있는 Adobe Experience Manager 로고를 클릭하고 을 선택합니다 **Sites**.
1. Campaign을 선택하고 **Create→Page**.
   ![브랜드 만들기](assets/create.png)
1. 브랜드 를 선택하고 을(를) 클릭합니다 **다음**.
1. 제목을 입력하고 을(를) 클릭합니다 **만들기** 및 **완료**.
1. 캠페인 페이지를 만들려면 다음 위치로 이동하십시오. **Campaigns→AdobeDemo→기본** 을(를) 클릭합니다. **Create→Page**.
   ![캠페인 페이지](assets/campaignpage.png)
1. 캠페인 템플릿을 선택하고 을(를) 클릭합니다 **다음** 및 **완료**.
1. 제목을 입력하고 을 클릭합니다. **만들기** 및 **완료**.
1. 이동 **Campaign→AdobeDemo→기본** 캠페인 페이지 확인란을 선택합니다. 클릭 **속성** 왼쪽 위에 있습니다.
   ![캠페인 속성](assets/propertiesedit.png)
1. 로 이동합니다. **Cloud Service** 탭:
   * Cloud Service 구성 드롭다운 목록에서 Adobe Campaign을 선택합니다.
   * Adobe Campaign 구성에 대해 원하는 이름을 선택합니다.
   * **저장** 및 **닫기**.
1. Adobe Campaign Classic 이메일 페이지를 만들려면 다음 위치로 이동하십시오. **Campaign→AdobeDemo→기본→CampaignPage** 을(를) 클릭합니다. **Create→Page**.
1. Adobe Campaign 이메일(예: AC 6.1) 템플릿을 선택하고 을(를) 클릭합니다 **다음**.
1. 만들기 페이지에서 뉴스레터의 제목을 입력하고 **만들기** 및 **완료**.
1. 이동 **Campaign→AdobeDemo→기본→CampaignPage** Campaign Classic 확인란을 선택하고 을(를) 클릭합니다. **편집** 왼쪽 상단에서 전자 메일 페이지를 엽니다.
1. 요구 사항에 따라 Adobe Campaign Classic 이메일 뉴스레터 페이지를 편집합니다.
1. 을(를) 클릭합니다. **페이지 정보** 왼쪽 위에 있는 단추를 클릭하고 **페이지 게시**.
1. 페이지를 게시해야 하는 구성을 선택합니다. **게시**를 클릭합니다. 
   ![게시 페이지](assets/publish.png)
1. 뉴스레터 페이지가 게시 인스턴스와 AEM Adobe Campaign Classic 구성에도 게시되었습니다.
   * 이제 뉴스레터 페이지가 Adobe Campaign Classic에 표시됩니다
1. 페이지 정보 버튼을 클릭하고 **워크플로우 시작**.
1. 선택 **Adobe Campaign 승인** 워크플로우 모델로 를 클릭하고 **워크플로우 시작** 버튼을 클릭합니다.
1. 면책조항이 페이지 맨 위에 나타납니다. 클릭 **완료** 검토를 확인하려면 을(를) 클릭하고 **확인**.
1. 클릭 **완료** 을(를) 선택합니다. **뉴스레터 승인** 다음 단계 드롭다운 목록에서 **확인** 버튼을 클릭합니다.

## 수신자 만들기 {#creating-recipient}

1. Adobe Campaign Classic 클라이언트 콘솔을 사용하여 Adobe Campaign Classic 서버를 엽니다.
1. 탐색기 보기로 이동합니다.
1. 왼쪽의 트리 보기에서 프로필 및 Target으로 이동하여 를 선택합니다 **수신자**.
   ![수신자](assets/recipients.png)
1. 수신자의 세부 정보를 입력합니다.
   * 이름을 입력합니다.
   * 성을 입력합니다.
   * 이메일을 입력합니다.
   * **저장**&#x200B;을 클릭합니다.

## Adobe Campaign Classic에서 이메일 게재 만들기 {#create-delivery}

1. Adobe Campaign Classic 클라이언트 콘솔을 사용하여 Adobe Campaign Classic 서버를 엽니다.
1. 탐색기 보기로 이동합니다.
1. 왼쪽의 트리 보기에서 를 선택합니다 **Campaign Management** 을(를) 선택합니다. **게재**.
1. 오른쪽 상단 모서리에서 을(를) 클릭합니다. **새로 만들기**.
1. 선택 **AEM 컨텐츠가 있는 이메일 게재** 게재 템플릿 드롭다운 목록에서 을(를) 클릭하고 **계속**.
1. 이메일 매개 변수 아래에 있는 시작 링크를 클릭합니다.
   * 보낸 사람 주소를 입력합니다.
   * 시작 필드를 입력합니다.
   * **확인**&#x200B;을 클릭합니다.
1. 클릭 **종료** 링크를 클릭한 다음 **추가** 타겟 선택 화면에서 클릭합니다.
1. 선택 **수신자** 을(를) 클릭합니다. **다음**.
   ![타겟 유형](assets/publish.png)
1. 만든 받는 사람을 선택합니다 [이전](#creating-recipient) 을(를) 클릭합니다. **완료**.
1. 수신자를 선택했습니다. **확인**&#x200B;을 클릭합니다.
1. 클릭 **동기화**.
1. 목록에서 이메일 페이지를 선택하고 을(를) 클릭합니다. **확인**.
1. 이메일 템플릿이 동기화됩니다. 클릭 **컨텐츠 새로 고침** 로드되지 않은 경우.
1. 클릭 **보내기** 전자 메일을 보내려면
1. 다음 화면에서 **가능한 한 빨리 배달** 을 클릭한 다음 **분석**.
   ![게재 대상](assets/deliverytarget.png)
1. 이제 게재를 만들 때 **배달 확인** 전자 메일 전송을 시작하려면 다음을 수행하십시오. **예**를 클릭하여 확인합니다.
   ![게재 확인](assets/confirmdelivery.png)
1. 게재가 시작되었습니다. **닫기**&#x200B;를 클릭합니다.
1. 클릭 **저장** 게재를 저장합니다.
