---
title: AEM MCP를 사용하여 OpenAI ChatGPT 설정
description: AEM MCP 서버에 연결하도록 OpenAI ChatGPT를 구성하는 방법에 대해 알아봅니다
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 1f116225-168b-483c-9df6-c752a573b57b
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# AEM MCP를 사용하여 OpenAI ChatGPT 설정 {#setup-chatgpt}

다음 단계에 따라 OpenAI ChatGPT를 AEM의 MCP 서버에 연결합니다.

* MCP 연결 또는 도구가 구성된 영역에 하나 이상의 AEM MCP 서버 URL을 추가합니다.
* 연결을 트리거하고 리디렉션될 때 Adobe ID으로 로그인합니다.
* 채팅에서 프롬프트에서 구성된 AEM 도구를 참조하십시오. 예를 들면 다음과 같습니다.

  ```
  "Using the configured AEM MCP tools, list all sites in the author environment."
  ```

![ChatGPT 설정 대화 상자](assets/chatgpt-1.png)

![ChatGPT의 앱 및 커넥터 고급 설정 패널](assets/chatgpt-2.png)

![앱 및 커넥터 섹션에서 개발자 모드를 사용하도록 설정합니다.](assets/chatgpt-3.png)

![ChatGPT에서 새 앱을 만들기 위한 대화 상자입니다.](assets/chatgpt-4.png)

![ChatGPT의 새 앱 구성 양식입니다.](assets/chatgpt-5.png)

![앱 및 커넥터에 나열된 AEM 콘텐츠 MCP 서비스](assets/chatgpt-6.png)

![AEM 콘텐츠 MCP 서비스를 사용하도록 ChatGPT에 메시지 표시](assets/chatgpt-7.png)
