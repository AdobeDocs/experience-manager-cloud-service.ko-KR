---
title: AEM으로 Campaign 뉴스레터 만들기
description: AEM as a Cloud Service을 사용하여 Adobe Campaign Classic과 함께 보낼 수 있는 뉴스레터를 만드는 방법을 알아봅니다.
feature: Authoring
role: User
exl-id: 60a6a9d0-f5e6-424f-b320-dd4943c55d45
source-git-commit: 6196f3fc67dbcfe03a71bb6a0796dd5d1d0f8546
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 1%

---


# AEM으로 Campaign 뉴스레터 만들기 {#creating-newsletters}

이 문서에서는 AEM as a Cloud Service을 사용하여 Adobe Campaign Classic과 함께 보낼 수 있는 뉴스레터를 만드는 방법을 알아봅니다.

AEM as a Cloud Service과 Adobe Campaign Classic 간의 통합을 활용하면 AEM의 강력한 작성 도구를 사용하여 뉴스레터를 만들 수 있습니다. 그런 다음 뉴스레터를 보낼 준비가 되면 Campaign의 수신자 관리 및 배포 기능을 사용하여 보낼 수 있습니다.

## 사전 요구 사항 {#prerequisites}

AEM으로 뉴스레터를 만들어 Campaign으로 보내려면 먼저 해야 합니다 [Adobe Campaign Classic과 AEM as a Cloud Service을 통합합니다.](/help/sites-cloud/integrating/integrating-campaign-classic.md)

## 뉴스레터 구조 만들기 {#create-structure}

뉴스레터 컨텐츠는 사이트 컨텐츠를 관리하는 것처럼 AEM에서 관리됩니다. 먼저 컨텐츠를 저장할 &quot;사이트&quot;를 만듭니다. 이 &quot;사이트&quot; 내에서 브랜드별로 뉴스레터를 수집할 수 있습니다.

1. AEM 작성자 인스턴스에 로그인합니다.

1. 기본 탐색 페이지에서 **Sites** 콘솔.

1. AEM의 표준 설치에는 **캠페인** 폴더를 입력합니다. 이 옵션을 선택하고 을(를) 클릭합니다. **만들기** 단추를 누른 다음 **페이지**.

   ![페이지 제작](assets/create-page.png)

1. 선택 **브랜드** 을(를) 사이트 템플릿으로 사용하고 **다음**.

   ![브랜드 만들기](assets/create-brand.png)

1. 을(를) 입력합니다. **제목** 을(를) 클릭합니다. **만들기** 그리고 **완료**.

   ![브랜드 세부 사항 제공](assets/create-brand-page.png)

이제 캠페인을 만들 수 있는 기본 컨텐츠 구조가 있습니다.

![컨텐츠 구조](assets/content-structure.png)

## 캠페인 만들기를 참조하십시오 {#create-campaign}

이제 캠페인에 대한 기본 콘텐츠 구조가 있으므로 캠페인 자체를 만들 수 있습니다. 이 캠페인은 여러 뉴스레터를 구성하는 데 사용됩니다.

1. 사용 [열 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) 사이트 콘솔에서 이전에 만든 브랜드를 선택합니다(이 경우 **WKND 이스케이프**)를 선택한 다음 을 선택합니다. **기본 영역**&#x200B;자동으로 만들어지는 을 만든 다음 **만들기** 단추를 누른 다음 **페이지**.

   ![캠페인 페이지 만들기](assets/create-campaign-page.png)

1. 선택 **캠페인** 을 템플릿으로 사용하고 **다음** 및 **완료**.

   ![캠페인 템플릿 선택](assets/select-campaign-template.png)

1. 을(를) 입력합니다. **제목** 을(를) 캠페인용으로 사용하고 을(를) **만들기** 및 **완료**.

   ![캠페인 제목](assets/campaign-title.png)

이제 뉴스레터를 만들 수 있는 캠페인이 제공됩니다.

![캠페인 구조](assets/campaign-structure.png)

## Campaign 구성 선택 {#campaign-configuration}

AEM은 여러 통합 구성을 지원할 수 있습니다. 새 캠페인의 경우 뉴스레터 컨텐츠를 전송하는 데 사용할 구성을 정의해야 합니다.

1. 사용 [열 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) 사이트 콘솔에서 이전에 만든 캠페인을 찾습니다(이 경우 **WKND Escape 여름 캠페인**)을 클릭한 다음 확인란을 사용하여 선택한 다음 **속성** 단추를 클릭합니다.

   ![캠페인 선택](assets/select-campaign.png)

1. 에서 **속성** 창에서 **Cloud Service** 탭하여 이 캠페인에 사용할 통합을 정의합니다.

   * 선택 **Adobe Campaign** 에서 **Cloud Service 구성** 드롭다운 목록.
   * 에서 원하는 Adobe Campaign 통합 구성을 선택합니다 **Adobe Campaign** 드롭다운 목록.
   * **저장 후 닫기**&#x200B;를 클릭합니다.

   ![Campaign 구성 속성](assets/campaign-configuration-properties.png)

이제 캠페인이 Adobe Campaign 통합에 연결됩니다. AEM에서 뉴스레터를 만들어 Adobe Campaign과 함께 보낼 준비가 되었습니다.

## 뉴스레터 만들기 {#create-newsletter}

이미 만들고 구성한 캠페인 콘텐츠 구조에 따라 뉴스레터를 만들고 관리합니다.

1. 사용 [열 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) 사이트 콘솔에서 이전에 구성한 캠페인을 찾습니다(이 경우 **WKND Escape 여름 캠페인**)을 선택하고 을(를) 클릭합니다. **만들기** 단추를 누른 다음 **페이지**.

   ![뉴스레터 만들기](assets/create-newsletter.png)

1. 페이지 만들기 마법사에서 **Adobe Campaign 이메일(AC 6.1)** 템플릿을 선택하고 **다음**.

   ![캠페인 이메일 템플릿 선택](assets/adobe-campaign-email-template.png)

1. 대상 **속성** 마법사의 단계에서 **제목** newsletter의 경우 **만들기** 및 **열기**.

   ![뉴스레터의 제목입니다](assets/create-newsletter-wizard-properties.png)

1. 요구 사항을 충족하는 다른 AEM 컨텐츠 페이지에서처럼 뉴스레터 페이지를 편집합니다.

이제 Adobe Campaign과 함께 뉴스레터를 보낼 준비가 되었습니다.

## 뉴스레터 게시 {#publishing-newsletter}

Adobe Campaign에서 보낼 수 있도록 뉴스레터를 게시해야 합니다.

1. 사용 [열 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) 사이트 콘솔에서 이전에 만든 뉴스레터를 찾습니다(이 경우 **WKND 이스케이프 여름 캠페인에 대한 첫 뉴스레터**)을 선택하고 을(를) 클릭합니다. **페이지 정보** 왼쪽 위에 있는 단추를 클릭하고 **페이지 게시**.

1. 페이지를 게시할 구성을 선택하고 을(를) 클릭합니다. **게시**.

   ![페이지 게시](assets/publish.png)

이제 뉴스레터 페이지가 AEM 게시 인스턴스에 게시되며 Adobe Campaign Classic에 표시됩니다. Adobe Campaign 내에서 선택하려면 승인해야 합니다.

1. 을(를) 클릭합니다. **페이지 정보** 뉴스레터에 대한 버튼을 한 번 더 클릭하고 을 선택합니다. **워크플로우 시작**.

1. 선택 **Adobe Campaign 승인** 워크플로우 모델(선택적으로 설명 제공)으로서 을 클릭하고 **워크플로우 시작** 버튼을 클릭합니다.

   ![워크플로우 시작](assets/start-workflow.png)

1. 승인 프로세스의 다음 단계를 제공하는 뉴스레터 페이지 편집기 맨 위에 배너가 나타납니다. 클릭 **완료**.

   ![워크플로우 승인](assets/approve-workflow.png)

1. 에서 **작업 항목 완료** 대화 상자, 선택 **뉴스레터 검토(관리자)** 에서 **다음 단계** 드롭다운 목록을 클릭하고 **확인** 버튼을 클릭합니다.

   ![뉴스레터 검토](assets/newsletter-review.png)

1. 뉴스레터 페이지 편집기의 맨 위에 나타나는 배너에서 다시 를 클릭합니다. **완료**.

1. 에서 **작업 항목 완료** 대화 상자, 선택 **뉴스레터 승인** 에서 **다음 단계** 드롭다운 목록을 클릭하고 **확인** 버튼을 클릭합니다.

   ![뉴스레터 승인](assets/newsletter-approval.png)

1. 대화 상자가 닫히면 승인 작업 과정이 완료되므로 뉴스레터 페이지 편집기 맨 위에 표시된 배너가 사라집니다.

이제 뉴스레터가 AEM에 게시되고 Adobe Campaign에서 사용할 수 있도록 승인됩니다.

>[!TIP]
>
>설명된 워크플로우 단계는 프로세스를 보여주기 위해 여기에서 단순화됩니다. 일반적인 작업 흐름에서 뉴스레터를 만들고 승인하는 것은 일반적으로 다른 역할입니다
>
>문서를 참조하십시오 [워크플로우 작업](/help/sites-cloud/authoring/workflows/overview.md) 워크플로우 사용에 대한 자세한 내용

## 수신자 만들기 {#creating-recipient}

AEM에서 만든 뉴스레터를 보내려면 먼저 Adobe Campaign Classic에서 수신자를 정의해야 합니다.

1. 클라이언트 콘솔을 사용하여 Adobe Campaign Classic에 로그인합니다.

1. 선택 **도구** -> **탐색기** 메뉴 모음에서 를 클릭합니다.

1. 탐색기에서 **프로필 및 Target** -> **수신자** 노드 아래에 있어야 합니다.

   ![수신자](assets/recipients.png)

1. 클릭 **새로 만들기** 를 클릭하여 수신자의 세부 정보를 제공합니다.

   * 이름
   * 성
   * 이메일 주소

1. **저장**&#x200B;을 클릭합니다.

이제 Adobe Campaign Classic을 사용하여 뉴스레터를 게재할 수 있는 수신자가 있습니다.

## 이메일 게재 만들기 {#create-delivery}

마지막 단계는 AEM에서 만든 뉴스레터를 Adobe Campaign Classic에서 추가한 수신자에게 보내는 것입니다.

1. 클라이언트 콘솔을 사용하여 Adobe Campaign Classic에 로그인합니다.

1. 선택 **도구** -> **탐색기** 메뉴 모음에서 를 클릭합니다.

1. 탐색기에서 **Campaign Management** -> **게재** 노드 및 **새로 만들기**.

   ![AEM 컨텐츠 전달](assets/delivery-aem-content.png)

1. 에서 **배달** 대화 상자, 선택 **AEM 컨텐츠가 있는 이메일 게재** 로서의 **게재 템플릿** 드롭다운 목록에서 를 클릭하고 **계속**.

   ![AEM 컨텐츠 전달](assets/aem-content-delivery.png)

1. 에서 **전자 메일 매개 변수** 섹션에서 **From** 링크 및 발신자 정보를 입력하고 **확인**.

   * 보낸 사람 주소
   * From 필드

   ![필드에서 정의](assets/delivery-from.png)

1. 에서 **전자 메일 매개 변수** 섹션에서 **종료** 링크를 클릭하여 열기 **Target 선택** 대화 상자를 클릭한 다음 **추가**.

   ![대상 선택](assets/select-target.png)

1. 에서 **대상 요소 선택** 대화 상자, 선택 **수신자** 을(를) 클릭합니다. **다음**.

   ![대상 요소 선택](assets/select-target-element.png)

1. 필터를 사용하여 수신자를 선택합니다 [이전에 생성됨](#creating-recipient) 을(를) 클릭합니다. **완료**.

   ![수신자 선택](assets/select-target-element-recipient.png)

1. 다시 **Target 선택** 대화 상자 **확인**.

1. 게재 창에서 **동기화**.

   ![동기화](assets/synchronize.png)

1. 에서 **AEM 콘텐츠과 동기화** 대화 상자의 목록에서 이전에 만든 뉴스레터를 선택하고 **확인**.

1. Adobe Campaign의 이메일 콘텐츠는 AEM에서 만든 뉴스레터 콘텐츠와 동기화됩니다.

   * 클릭 **컨텐츠 새로 고침** 컨텐츠가 자동으로 로드되지 않는 경우

1. 클릭 **보내기** 전자 메일을 보내려면

1. 에서 **기본 게재 대상으로 보내기** 대화 상자, 선택 **가능한 한 빨리 배달** 을 클릭한 다음 **분석**.

   ![게재 분석](assets/delivery-analysis.png)

1. 분석 단계에서는 컨텐츠를 수신자와 결합하여 게재를 만듭니다. 게재가 만들어졌으므로 이제 을(를) 클릭합니다. **배달 확인** 전자 메일 보내기를 클릭합니다. **예**&#x200B;를 클릭하여 확인합니다.

1. 게재가 시작되었습니다. **닫기**&#x200B;를 클릭합니다.

   ![제공](assets/delivering.png)

1. 클릭 **저장** 게재를 저장합니다.

뉴스레터가 전송되었습니다!

>[!TIP]
>
>이 예는 단일 수신자에게 뉴스레터를 전송하는 간소화된 게재를 보여줍니다. 물론 일반 게재에는 여러 다른 수신자가 포함될 수 있으며 Adobe Campaign에서 이 수신자를 간편하게 관리할 수 있습니다. 자세한 내용은 [Adobe Campaign Classic 설명서](https://experienceleague.adobe.com/docs/campaign-classic.html) 전달 및 수신자 관리에 대한 자세한 내용을 참조하십시오.
