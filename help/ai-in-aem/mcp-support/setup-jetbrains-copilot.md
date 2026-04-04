---
title: GitHub Copilot 및 AEM MCP를 사용하여 JetBrains 설정
description: AEM MCP 서버에 연결하도록 JetBrains IDE에서 GitHub Copilot을 구성하는 방법에 대해 알아봅니다
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: e153da42-51e0-49ea-8457-10bb5e77e2de
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 1%

---

# GitHub Copilot 및 AEM MCP를 사용하여 JetBrains 설정 {#setup-jetbrains-copilot}

다음 단계에 따라 JetBrains IDE(예: IntelliJ IDEA, WebStorm 또는 PyCharm)의 GitHub Copilot을 AEM의 MCP 서버에 연결합니다.

1. 편집기 오른쪽에 있는 **GitHub Copilot 채팅** 아이콘을 클릭하여 JetBrains IDE에서 GitHub Copilot 채팅을 엽니다.

   ![GitHub Copilot 채팅이 포함된 JetBrains IDE가 열려 있습니다.](assets/jetbrains-copilot-1.png)

1. Copilot 채팅 패널에서 **설정** 아이콘을 클릭하여 MCP 구성을 엽니다.

   ![설정 아이콘이 강조 표시된 GitHub Copilot 채팅 패널.](assets/jetbrains-copilot-2.png)

1. **설정**&#x200B;에서 **도구 > GitHub Copilot > 모델 컨텍스트 프로토콜(MCP)**&#x200B;로 이동하고 **구성**&#x200B;을 클릭하여 `mcp.json` 구성 파일을 엽니다.

   ![GitHub Copilot 아래의 MCP(모델 컨텍스트 프로토콜) 구성을 표시하는 JetBrains 설정 대화 상자입니다.](assets/jetbrains-copilot-3.png)

1. 하나 이상의 AEM MCP 서버 URL을 `mcp.json` 파일에 추가합니다. 예:

   ```json
   {
     "servers": {
       "aem": {
         "url": "https://mcp.adobeaemcloud.com/adobe/mcp/content"
       }
     }
   }
   ```


   ![AEM MCP 서버 URL이 있는 mcp.json 구성 파일입니다.](assets/jetbrains-copilot-4.png)


1. 파일을 저장합니다. GitHub Copilot은 새 서버 구성을 자동으로 감지하고 **시작** 작업을 표시합니다.

   ![검색된 도구를 사용하여 구성된 AEM 서버를 표시하는 mcp.json 파일입니다.](assets/jetbrains-copilot-5.png)

1. **시작** 작업을 클릭하고 메시지가 표시되면 Adobe ID에 로그인하여 인증 흐름을 완료합니다.

1. Copilot 채팅 패널에 표시되는 **도구** 표시기를 클릭하여 검색된 도구를 검토하고 관리할 수 있습니다. 필요한 경우 개별 도구를 활성화하거나 비활성화합니다.


   ![사용 가능한 AEM MCP 도구를 보여 주는 도구 구성 대화 상자](assets/jetbrains-copilot-6.png)

1. GitHub Copilot 채팅 을 사용하여 개발 또는 콘텐츠 워크플로의 일부로 AEM 도구를 호출합니다.
