---
title: AEM as a Cloud Service에서 MCP 사용
description: AEM as a Cloud Service과 함께 모델 컨텍스트 프로토콜을 사용하는 방법 알아보기
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: ddb7fc8c-affc-4374-8e08-d45d96017109
source-git-commit: b3704dad066b66b103fdec849879f889e895c09d
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 0%

---

# AEM as a Cloud Service에서 MCP 사용 {#using-mcp-with-aem-as-a-cloud-service}

## 소개 {#introduction}

이제 많은 Adobe Experience Manager(AEM) 팀이 Cursor, OpenAI ChatGPT, Anthropic Claude 및 Microsoft Copilot Studio와 같은 IDE(통합 개발 환경) 및 채팅 기반 애플리케이션에서 작업합니다. 이러한 애플리케이션은 MCP(Model Context Protocol)를 지원하므로 애플리케이션이 백엔드 도구를 대형 언어 모델(LLM)에 표준화된 방식으로 노출할 수 있습니다.

AEM의 MCP 통합을 통해 다양한 가상 사용자가 동일한 콘텐츠를 공동 작업할 수 있습니다.

* **개발자**&#x200B;는 IDE 또는 채팅 응용 프로그램에서 콘텐츠 작업 및 워크플로를 오케스트레이션할 수 있습니다
* **실무자** 및 콘텐츠 설계자는 AEM의 기존 권한 모델 내에 있는 동안 AI 지원을 통해 사이트, 콘텐츠 조각 및 에셋을 관리할 수 있습니다.

>[!IMPORTANT]
>
> 콘텐츠를 수정하거나 삭제하는 시나리오의 경우, 실무자는 MCP 도구를 직접 호출하기 보다는 AI Assistant 인터페이스를 사용해야 합니다. AI Assistant가 실행하는 AEM 에이전트에는 내장된 안전 장치가 포함됩니다.
>

이 문서에서는 AEM의 MCP 기능이 제공하는 기능, 지원되는 MCP 애플리케이션, 구성 방법 및 실제로 사용하는 방법에 대해 설명합니다.

## MCP가 AEM 고객에게 유용한 이유 {#why-mcp-is-useful-for-aem-customers}

최신 IDE 및 채팅 애플리케이션은 LLM이 MCP 서버 뒤에 노출된 도구를 호출하는 방법으로 MCP를 사용합니다. 고객은 낮은 수준의 API 사양에 따라 코드를 작성하는 대신 자연어로 의도를 설명할 수 있습니다. 예를 들어 *&quot;모든 페이지에서 이 캠페인에 대한 영웅 배너를 업데이트&quot;*&#x200B;하라는 메시지가 표시되면 LLM은 적절한 MCP 도구를 호출한 다음 AEM의 API와 상호 작용할 수 있습니다.

주요 이점은 다음과 같습니다.

* **API 배관 대신 자연어 상호 작용**
MCP 도구는 사용 가능한 작업과 호출 방법을 설명합니다. LLM은 이러한 스키마를 사용하여 호출할 도구와 매개 변수를 결정합니다.
* **응용 프로그램 간 일관된 경험**
여러 MCP 호환 애플리케이션에서 동일한 AEM MCP 도구를 사용할 수 있으므로 팀은 동일한 기본 AEM 기능을 호출하면서 가장 생산적인 위치에서 작업할 수 있습니다.
* **보안 및 거버넌스 유지**
AEM MCP 도구에 대한 요청은 인증된 사용자의 ID에서 실행되며, 각 도구는 사용자의 기존 AEM 권한을 시행합니다. AI 지원 작업은 AEM의 수동 작업과 동일한 액세스 규칙을 따릅니다.

## AEM 제공 MCP 서버 {#mcp-servers-provided-by-aem}

AEM은 MCP 서버를 HTTP 끝점으로 노출합니다. 아래 나열된 엔드포인트는 다음을 기준으로 합니다.

`https://mcp.adobeaemcloud.com/adobe/mcp/`

### MCP 서버 {#mcp-servers}

| **MCP 서버** | **끝점** | **설명** |
|---|---|----------------------------------------------------------------------------------------------------------------------|
| **콘텐츠** | `/content` | 페이지, 조각 및 에셋의 만들기, 읽기, 업데이트 및 삭제(CRUD)를 포함한 모든 하위 수준 콘텐츠 작업. |
| **컨텐츠(읽기 전용)** | `/content-readonly` | 페이지, 조각 및 에셋에 대한 읽기 전용 콘텐츠 작업(가져오기, 목록/검색). |
| **Cloud Manager** | `/cloudmanager` | 프로그램, 환경, 저장소 및 파이프라인을 포함하여 트리거될 수도 있는 Cloud Manager 엔티티를 관리합니다. <br><br>*이 MCP 서버는 현재&#x200B;**베타**에 있습니다. 액세스 권한을 요청하려면 사용 사례에 대한 설명을 [aemcs-mcp-feedback@adobe.com](mailto:aemcs-mcp-feedback@adobe.com)에 전자 메일을 보내십시오.* |

각각의 MCP 서버에 의해 노출된 특정 툴들은 시간이 지남에 따라 진화할 수 있다. 실제로 MCP 지원 응용 프로그램에 다음과 같은 프롬프트를 통해 도구를 검색하도록 요청할 수 있습니다.

```
"List all AEM MCP tools available from this server and describe what they do."
```

MCP 클라이언트는 MCP 프로토콜을 사용하여 툴 리스트 및 스키마를 검색하고, 이는 LLM이 사용할 수 있다.

## 지원되는 MCP 애플리케이션 {#supported-mcp-applications}

AEM의 MCP 서버는 정의된 MCP 호환 애플리케이션 세트와 호환되도록 설계되었습니다. 각 애플리케이션은 자체 구성 경험을 제공하지만 높은 수준의 단계는 유사합니다.

### 채팅 애플리케이션(웹 및 데스크탑) {#chat-applications}

* 인류 클로드
* OpenAI 채팅GPT

### 개발자 도구(IDE 확장, 데스크탑 앱, CLI) {#developer-tools}

* 인류 클라우드 코드(CLI, JetBrains, VS 코드, 커서)
* 코드 보강(CLI, JetBrains, VS 코드, 커서)
* 데스크탑 앱 수준 올리기
* Cline(JetBrains, VS 코드, 커서)
* 커서
* GitHub Copilot(VS 코드)
* Kiro(데스크탑 앱, CLI)
* OpenAI 코드(데스크탑 앱)
* OpenAI Codex CLI
* 윈드서프

### 엔터프라이즈 플랫폼 {#enterprise-platforms}

* Microsoft Copilot Studio

## 설정 개요 {#setup-overview}

AEM용 MCP 구성에는 다음 두 가지 주요 부분이 포함됩니다.

1. **각 MCP 클라이언트 응용 프로그램에서 구성** 응용 프로그램에서 AEM MCP 서버에 연결하고 OAuth 로그인을 수행하는 방법을 알 수 있도록
1. **MCP 서버 선택** 프롬프트를 시작하기 전에 MCP 클라이언트가 MCP 서버를 사용할 것을 알 수 있도록 합니다.

### AEM 구성 {#aem-configuration}

기본적으로 AEM 내에서 개별 사용자가 가질 수 있는 권한은 AEM의 MCP 서버에 대한 액세스를 제어합니다. 사용자가 MCP 클라이언트 애플리케이션을 통해 인증되면 MCP 도구는 AEM의 수동 작업과 동일한 액세스 규칙을 적용합니다. 사용자는 이미 수행 권한이 부여된 작업만 수행할 수 있습니다.

#### 허용된 MCP 클라이언트 애플리케이션 {#permitted-mcp-client-applications}

기본적으로 허용되는 MCP 클라이언트 애플리케이션은 다음과 같습니다.

* 인류 클로드
* 인류 클로드 코드
* 코드 보강
* 추가 들여쓰기
* Cline
* 커서
* GitHub Copilot
* 키로
* Microsoft Copilot Studio
* OpenAI 채팅GPT
* OpenAI 코드
* OpenAI Codex CLI
* 윈드서프

#### MCP 서버 제한 {#restricting-mcp-servers}

모든 MCP 서버는 기본적으로 허용 목록에추가된입니다. 관리자는 조직, 프로그램 또는 환경 수준에서 특정 MCP 서버에 대한 액세스를 제한할 수 있습니다. 이 제한 사항은 조직 내에서 사용자가 사용할 수 있는 MCP 기능을 세부적으로 제어할 수 있도록 해 줍니다.

#### MCP 클라이언트 액세스 관리 {#managing-mcp-client-access}

또한 관리자는 조직의 정책에 필요한 경우 특정 MCP 클라이언트 애플리케이션에 대한 액세스를 비활성화할 수 있습니다. Adobe에서 추가 MCP 클라이언트 제품에 대한 지원을 활성화하려면 제품 웹 사이트에 대한 링크를 보내십시오. 허용 목록에 추가하다 사용자 정의 MCP 클라이언트를 다운로드해야 하는 경우 연락하십시오.

모든 MCP 서버 관련 요청에 대해 언제든지 **aemcs-mcp-feedback@adobe.com**&#x200B;로 문의하십시오.

### MCP 클라이언트 애플리케이션 구성 {#mcp-client-application-configuration}

각 사용자는 이 단계를 수행하거나 MCP 클라이언트 애플리케이션의 관리자는 지원되는 경우 이를 수행할 수 있습니다. 구성 세부 정보는 애플리케이션마다 조금씩 다릅니다. MCP 클라이언트는 빠르게 발전하고 있으며, 원격 MCP 서버에 대한 지원이 활발히 개발되고 있다. 원격 서버를 추가하기 위한 기능에 액세스하려면 개발자 모드를 활성화해야 할 수 있지만 일반적인 프로세스는 다음과 같습니다.

1. 하나 이상의 AEM MCP 서버 URL 추가
   * 위의 표에서 하나 이상의 MCP 끝점을 구성합니다. 예:`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. 연결 트리거
   * MCP 클라이언트 애플리케이션이 AEM MCP 서버에 연결을 시도하도록 구성을 저장하거나 활성화합니다
1. Adobe ID으로 로그인
   * 메시지가 표시되면 Adobe 로그인 플로우를 완료하여 애플리케이션이 Adobe ID에 연결된 OAuth 토큰을 얻을 수 있습니다
1. 검색된 도구 확인
   * 인증되면 애플리케이션은 서버에서 MCP 도구를 검색합니다. 그런 다음 LLM에서 AEM 작업을 수행하라는 메시지를 표시할 수 있습니다.

다음은 지원되는 애플리케이션이며, 일부 애플리케이션은 단계별 안내서에 연결됩니다.

#### 채팅 애플리케이션(웹 및 데스크탑) {#setup-chat-applications}

* [인류 클로드](/help/ai-in-aem/mcp-support/setup-claude.md)
* [OpenAI 채팅GPT](/help/ai-in-aem/mcp-support/setup-chatgpt.md)

#### 개발자 도구(IDE 확장, 데스크탑 앱, CLI) {#setup-developer-tools}

* 인류 클라우드 코드(CLI, JetBrains, VS 코드, 커서)
* 코드 보강(CLI, JetBrains, VS 코드, 커서)
* 데스크탑 앱 수준 올리기
* Cline(JetBrains, VS 코드, 커서)
* [커서](/help/ai-in-aem/mcp-support/setup-cursor.md)
* GitHub Copilot(VS 코드)
* Kiro(데스크탑 앱, CLI)
* OpenAI 코드(데스크탑 앱)
* OpenAI Codex CLI
* 윈드서프

#### 엔터프라이즈 플랫폼 {#setup-enterprise-platforms}

* [Microsoft Copilot Studio](/help/ai-in-aem/mcp-support/setup-microsoft-copilot-studio.md)

## 인증 {#authentication}

Adobe에서 호스팅하는 MCP 서버는 OAuth를 구현하고 Adobe의 ID 시스템과 통합됩니다.

* MCP 클라이언트 응용 프로그램이 AEM MCP 서버에 연결되면 사용자는 Adobe 로그인 대화 상자를 보고 **Adobe ID**&#x200B;로 인증합니다
* 성공적인 로그인 후 시스템은 MCP 클라이언트 애플리케이션이 조직에서 허용되고 요청된 MCP 서버가 허용되는지 확인합니다. 둘 중 하나가 실패하면 오류 메시지가 표시됩니다.

![MCP 클라이언트가 허용되지 않는 오류](assets/MCP-Client-not-permitted.png)

* 확인되면 MCP 서버는 애플리케이션이 후속 도구 호출에 사용하는 토큰을 발행합니다
* MCP 도구는 사용자의 AEM 권한을 준수합니다. AEM에서 컨텐츠 조각을 수정할 수 있는 권한이 있는 사용자만 MCP를 통해 수정할 수 있습니다.

이 접근 방식은 AI 지원 작업이 기존의 AEM 보안 및 거버넌스 모델을 준수하도록 합니다.

## AEM에서 MCP 사용 {#using-mcp-with-aem}

AEM 및 MCP 클라이언트 애플리케이션이 구성되면 선택한 애플리케이션에서 작업하고 LLM에 AEM 작업을 수행하도록 요청할 수 있습니다. LLM은 MCP 도구 스키마를 읽고 호출할 도구를 선택한 다음 필요에 따라 순서를 지정하여 요청을 이행합니다.

>[!IMPORTANT]
>
>여러 단계를 포함하거나 이미지 및 텍스트와 같은 다양한 콘텐츠 유형을 타깃팅하는 프롬프트는 사고 모델에서 가장 잘 작동합니다. 자동 모드에 의존하지 않고 MCP 클라이언트에서 사고 모델을 활성화하거나 사고 옵션을 선택합니다.

### 예제 사용 사례 {#example-usecases}

몇 가지 대표적인 시나리오는 다음과 같습니다.

* **환경 검색**
   * 환경 및 라이센스를 나열하여 워크플로우를 실행할 위치를 결정합니다.

* **사이트 관리**
   * 사이트 나열
   * 페이지 및 페이지 컨텐츠를 작성, 읽기, 업데이트 및 삭제합니다.

* **콘텐츠 조각 관리**
   * 콘텐츠 조각 검색
   * 새 조각 만들기
   * 캠페인 메시지가 변경되면 기존 조각을 업데이트합니다.

* **Assets 관리**
   * 에셋 가져오기
   * 기존 에셋 찾기
   * 자산을 게시합니다.

### 예제 워크플로우 {#example-workflows}

다음 예는 LLM이 MCP 도구를 함께 연결하는 방법을 보여줍니다.

1. **페이지에서 참조한 콘텐츠 조각을 사용하여 작업**
   * **페이지 콘텐츠 가져오기** - `get-aem-page-content`과(와) 같은 도구를 호출하여 페이지를 검색하고 `fragmentPath` 속성을 찾습니다.
   * **조각 경로를 확인합니다** - `resolve_fragment_path`을(를) 사용하여 경로를 UUID로 변환합니다.
   * **조각 데이터 가져오기** - `get_fragment`을(를) 호출하여 현재 필드를 검색합니다.
   * **조각 업데이트** - `patch_fragment`을(를) 호출하여 조각 콘텐츠에 변경 내용을 적용합니다.
1. **모델을 기반으로 새 콘텐츠 만들기**
   * **모델 검색** - `list_models`을(를) 사용하여 사용 가능한 콘텐츠 조각 모델을 확인합니다.
   * **모델 검사** - `get_model`을(를) 사용하여 모델의 필드 스키마를 이해합니다.
   * **콘텐츠 만들기** - `create_fragment`을(를) 사용하여 프롬프트에서 파생된 값으로 새 조각을 만듭니다.
1. **기존 콘텐츠를 안전하게 업데이트 중**
   * **현재 데이터 읽기** - `get_fragment`을(를) 사용하여 기존 데이터와 ETag를 검색합니다.
   * **JSON 패치 적용** - ETag 및 JSON 패치 문서와 함께 `patch_fragment`을(를) 사용하여 조각을 업데이트하여 낙관적 동시성을 지원합니다.

사용자의 관점에서 이러한 워크플로우는 다음과 같은 프롬프트로 시작할 수 있습니다.

```
"Create a new content fragment for the spring campaign based on our hero banner model and fill in its fields from this brief."
```

LLM은 필요한 MCP 도구를 자동으로 선택하고 조정합니다.

## 예상 관리 {#expectation-management}

MCP를 통해 LLM을 사용할 때는 다음 사항에 유의하십시오.

* **매우 강력하지만 확실하지 않음**
LLM은 복잡한 작업을 수행할 수 있지만 가끔 오류가 발생하기 쉽습니다. 동일한 프롬프트가 명확한 이유 없이 약간 다른 결과나 프레젠테이션을 산출할 수 있습니다. 프로덕션 콘텐츠에 변경 사항을 적용하기 전에 항상 출력을 검토하십시오.

* **진화하는 기능**
LLM 모델은 지속적으로 개선되고 있습니다. 시간이 지나면서 목표를 달성하기 위해 MCP 도구를 결합하는 새로운 방법을 발견하는 것이 더 똑똑해집니다. 오늘 여러 개의 프롬프트가 필요한 작업은 내일 하나의 프롬프트와 원활하게 작동할 수 있습니다.

* **사람의 감독이 필요합니다.**
LLM을 감독이 필요한 지식을 갖춘 조수로 생각하십시오. 광범위한 지식을 가지고 있으며 창의적인 해결책을 고안할 수 있지만, 지도와 검토를 통해 이점을 얻을 수 있습니다. 특히 중요한 작업의 결과를 확인하고 결과가 예상과 일치하지 않을 때 피드백을 제공합니다.

* **도구 실행 자동 확인**
Claude와 같은 일부 MCP 클라이언트 응용 프로그램은 LLM에 의해 요청된 도구 실행을 자동 승인하는 옵션을 제공합니다. 이 옵션은 콘텐츠 검색 또는 검색과 같은 읽기 전용 작업에는 편리할 수 있지만, 콘텐츠를 업데이트하거나 삭제하는 도구에는 주의하십시오. AEM 환경을 수정하는 작업을 확인하기 전에 각 도구 실행 요청을 검토하십시오.

## 제한 사항 {#limitations}

AEM은 현재 [지원되는 MCP 응용 프로그램](#supported-mcp-applications)에 나열된 응용 프로그램에서 MCP 서버 구성을 지원합니다.

허용 목록에 추가하다 다른 MCP 클라이언트 응용 프로그램을 사용하려면 **aemcs-mcp-feedback@adobe.com**&#x200B;에 연락하여 추가 클라이언트를 요청하거나 사용자 지정 클라이언트 지원을 요청하십시오.
