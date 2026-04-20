---
title: AEM MCP로 Anthropic Claude 설정
description: AEM MCP 서버에 연결하도록 Anthropic Cloud를 구성하는 방법에 대해 알아봅니다
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 2b90b2b2-cdd0-4f1e-890f-2f58f578face
source-git-commit: fede808fcd8b082a71273bf9ffceb48b5332f45d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# AEM MCP로 Anthropic Claude 설정 {#setup-claude}

다음 단계에 따라 Anthropic Claude를 AEM의 MCP 서버에 연결합니다.

* Claude의 MCP 구성에서 하나 이상의 AEM MCP 서버 URL을 등록합니다.
* Adobe 로그인 플로우를 완료합니다.
* 필요한 경우 구성 영역의 특정 도구에 대해 자동 확인 을 활성화합니다. 이 옵션은 검색 또는 읽기 전용 작업에 권장됩니다.
* 대화를 시작하기 전에 MCP 서버를 선택해야 합니다.
* Claude에게 AEM 관련 작업을 수행하도록 요청합니다. Claude 귀하의 프롬프트에 따라 MCP 서버에 의해 노출 된 AEM 도구를 선택합니다.

AEM MCP용 Cloud를 구성하려면 아래 단계를 따르십시오.

>[!NOTE]
>
>Claude 사용자 인터페이스는 변경될 수 있으며 확정적이지 않습니다. 이러한 지시사항은 예시적인 목적을 위한 것입니다.

1. 클라우드 웹 앱의 왼쪽 아래 모서리에서 계정 메뉴를 열고 **설정**&#x200B;을 선택하여 설정 영역을 엽니다.

   ![설정을 선택한 클라우드의 계정 메뉴](assets/claude-1.png)

1. 설정 사이드바에서 **커넥터**&#x200B;를 선택합니다. Connectors 페이지에서 **사용자 지정 커넥터 추가**&#x200B;를 선택하여 사용자 지정 MCP 끝점을 등록합니다.

   사용자 지정 커넥터 추가 설정의 ![커넥터 페이지.](assets/claude-2.png)

1. **사용자 지정 커넥터 추가** 대화 상자에서 디스플레이 이름(예: **AEM Content MCP Service**)과 AEM MCP 서버 URL을 입력한 다음 **추가**&#x200B;를 선택합니다. 배포에 추가 옵션이 필요한 경우에만 **고급 설정**&#x200B;을 사용하십시오.

   ![이름 및 MCP URL이 포함된 사용자 지정 커넥터 대화 상자를 추가합니다.](assets/claude-3.png)

1. 커넥터 목록에서 사용자 지정 커넥터 항목(**CUSTOM** 레이블이 표시됨)을 찾은 다음 **연결**&#x200B;을 선택하여 로그인하고 커넥터를 클라우드 계정에 연결합니다.

   ![AEM 콘텐츠 MCP 서비스에 대해 선택한 Connect가 있는 커넥터 목록](assets/claude-4.png)

1. 커넥터가 해당 URL과 함께 목록에 나타나면 **AEM 콘텐츠 MCP 서비스** 옆의 **구성**&#x200B;을(를) 선택하여 커넥터 세부 정보를 열고 설치를 계속합니다.

   ![AEM Content MCP 서비스에 대해 선택한 구성이 있는 커넥터 목록](assets/claude-5.png)

1. **도구 권한** 페이지에서 기본값을 검토한 다음(예: **승인 필요**) 보안 정책에 따라 각 AEM 도구를 **항상 허용**, **권한 요청** 또는 **절대 허용 안 함**&#x200B;으로 설정합니다.

   ![AEM Content MCP 서비스에 대한 도구 권한](assets/claude-6.png)

1. 대화를 엽니다. 메시지 필드 왼쪽에 있는 도구 및 모델 메뉴(슬라이더 아이콘)를 선택하고 Connectors에서 **AEM 콘텐츠 MCP 서비스**&#x200B;를 사용하도록 설정한 다음 Claude가 해당 채팅에 MCP 도구를 사용할 수 있도록 프롬프트를 입력합니다.

   ![도구 메뉴에서 AEM 콘텐츠 MCP 서비스를 사용하는 채팅 작성기입니다.](assets/claude-7.png)

## Adobe Experience Manager 클라우드 커넥터 {#aem-claude-connector}

**Adobe Experience Manager 클라우드 커넥터**&#x200B;를 설치하려면 클라우드에서 **설정** > **커넥터**&#x200B;를 여십시오. [https://claude.ai/settings/connectors](https://claude.ai/settings/connectors)에서 바로 Connectors 페이지를 열 수도 있습니다. 커넥터는 AEM 워크플로우에 대한 늘어나는 도구 세트를 노출하는 MCP 서버를 등록합니다.

![connectors 디렉터리에서 Adobe Experience Manager 클라우드 커넥터를 설치합니다.](assets/claude-connector.png)