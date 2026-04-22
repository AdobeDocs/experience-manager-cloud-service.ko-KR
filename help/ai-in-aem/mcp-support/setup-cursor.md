---
title: AEM MCP를 사용하여 커서 설정
description: AEM MCP 서버에 연결하도록 커서를 구성하는 방법에 대해 알아봅니다
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: f0897898-cb1d-4af6-859c-f5a1c0ec6168
source-git-commit: f7a5c43a4a4dd6629225f3628a7c592056d6d144
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# AEM MCP를 사용하여 커서 설정 {#setup-cursor}

다음 단계에 따라 Cursor를 AEM의 MCP 서버에 연결합니다.

* 커서의 MCP 설정에서 하나 이상의 AEM MCP URL이 포함된 새 MCP 서버 항목을 만듭니다.
* 메시지가 표시되면 Adobe ID을 사용하여 인증합니다.
* 필요한 경우 도구 이름을 클릭하여 개별 도구를 활성화하거나 비활성화합니다. 모든 도구는 기본적으로 활성화되어 있습니다.
* 커서 편집기 또는 채팅을 사용하여 개발 또는 콘텐츠 워크플로의 일부로 AEM 도구를 호출합니다.

>[!NOTE]
>
>Cursor 사용자 인터페이스는 변경될 수 있으며 확정적이지 않습니다. 이러한 지시사항은 예시적인 목적을 위한 것입니다.

1. Cursor가 MCP 서버에 연결되는 방법을 구성할 수 있도록 **커서 설정**&#x200B;을 엽니다.

   ![커서 설정 대화 상자](assets/cursor-1.png)

1. **도구 및 MCP**&#x200B;를 연 다음 **사용자 지정 MCP 추가**&#x200B;를 선택하여 사용자 지정 MCP 서버 항목을 시작합니다.

   ![사용자 지정 MCP 서버를 추가하는 옵션이 있는 도구 및 MCP 패널](assets/cursor-2.png)

1. 사용자 지정 MCP 서버 양식에 **이름**, AEM MCP **URL**(또는 URL) 및 기타 필수 필드를 입력한 다음 **저장**&#x200B;합니다.

   ![Cursor의 사용자 지정 MCP 서버 설정 양식입니다.](assets/cursor-3.png)

1. 연결 대화 상자가 나타나면 새 MCP 서버가 승인되도록 **Connect**&#x200B;를 눌러 로그인을 완료합니다.

   ![Cursor에 새 MCP 서버의 연결 대화 상자가 있습니다.](assets/cursor-4.png)

1. **채팅** 또는 편집기에서 구성된 MCP 서버가 워크플로에 참여할 수 있도록 **AEM 도구**&#x200B;를 호출하는 프롬프트를 작성하십시오.

   ![새 AEM MCP 서비스를 사용하도록 커서에 메시지를 표시합니다.](assets/cursor-5.png)
