---
title: AI 도구를 사용한 로컬 개발
description: AEM as a Cloud Service 개발을 가속화하기 위해 프로젝트 컨텍스트, 에이전트 기술 및 MCP 서버를 사용하여 AI 코딩 도구를 구성하는 방법에 대해 알아봅니다.
feature: Developing
role: Developer
source-git-commit: 0bc00b6e14be6ba111ac26ce69f07e138ca400e4
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 0%

---


# AI 도구를 사용한 로컬 개발 {#local-development-with-ai-tools}

>[!IMPORTANT]
>
>이 문서에 설명된 기능은 **베타**&#x200B;입니다. Adobe에서 개발 중인 기능에 일찍 액세스하면 고객과 파트너가 피드백을 제공하고([aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com)(으)로 전자 메일을 보내) 제품 개발을 구체화할 수 있습니다. 또한 GA 전에 새로운 기능을 채택할 준비를 하는 데 도움이 됩니다.
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

>[!NOTE]
>
>이 문서에서는 **AEM Java 스택 개발**&#x200B;을 위한 AI 도구를 사용한 로컬 개발에 중점을 둡니다. Edge Delivery Services의 경우 [AI 도구를 사용하여 개발](https://www.aem.live/developer/ai-coding-agents)을 참조하십시오.

AI 코딩 에이전트(클라우드 코드, 커서, GitHub Copilot 및 유사한 도구)는 AEM의 기본 기술(Java, OSGi, Sling, JCR, HTL)에 대한 광범위한 지식을 가지고 있지만 코드 및 구성을 생성하기 위한 모범 사례나 일반적인 AEM 개발 문제를 디버깅하는 방법을 반드시 알고 있지는 않습니다.

네 가지 보완 구성 요소는 다음과 같은 문제를 해결합니다.

| 구성 요소 | 목적 |
|---|---|
| **AGENTS.md** | 모든 세션에 대한 AEM Cloud Service 프로젝트의 AI를 기반으로 하는 프로젝트별 컨텍스트 파일 |
| **에이전트 기술** | 구성 요소 생성 및 Dispatcher 구성과 같은 반복되는 개발 작업에 재사용 가능한 지침 세트 |
| **AEM 빠른 시작 로컬 MCP 서버** | 문제 해결을 지원하기 위해 로컬 AEM SDK 인스턴스의 실시간 런타임 데이터를 노출합니다 |
| **Dispatcher 로컬 MCP 서버** | 로컬 Dispatcher 인스턴스의 런타임 유효성 검사 및 검사 활성화 |

>[!NOTE]
>
> 또한 로컬 개발에 유용하지만 이 문서에서는 다루지 않는 것이 AEM Cloud Service의 원격 MCP 서버입니다. 자세한 내용은 [Cloud Service과 함께 MCP 사용](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md)을 참조하세요.

## AGENTS.md {#agentsmd}

`AGENTS.md`은(는) AEM 6.5 또는 Edge Delivery Services과 같은 다른 AEM 솔루션이 아닌 필수 AEM Cloud Service Java 스택 도메인 전문 지식을 기반으로 하기 위해 AI 코딩 도구가 모든 세션이 시작될 때 자동으로 로드하는 AEM 프로젝트 루트에 있는 Markdown 파일입니다.

`AGENTS.md`은(는) 복사하는 정적 파일이 아닙니다. 다음 섹션에서 설명한 `ensure-agents-md` 스킬에 의해 생성됩니다. 이 스킬은 `pom.xml`을(를) 읽어 프로젝트 이름을 해결하고 모듈을 검색하며 설치된 추가 기능을 감지하여 특정 프로젝트에 맞는 파일을 생성합니다.

>[!NOTE]
>
>프로젝트 루트에 `AGENTS.md`이(가) 있으면 `ensure-agents-md` 스킬이 더 이상 실행되지 않습니다. 프로젝트 구조가 변경되는 경우 파일을 직접 편집합니다.

## 에이전트 스킬 {#agent-skills}

스킬은 여러 단계 개발 워크플로우를 인코딩하는 지침 세트입니다. 호출되면 AI가 일반적인 지식에만 의존하지 않고 스킬의 절차를 따르며 일관되고 규칙을 준수하는 결과를 생성합니다.

Adobe은 이 기능을 아직 일반적으로 사용할 수 없으므로 **[분기의 ](https://github.com/adobe/skills/tree/beta/skills/aem/cloud-service/skills)adobe/skills**`beta` 리포지토리에서 AEM as a Cloud Service 기술을 게시합니다.

| 스킬 | 목적 |
|---|---|
| `ensure-agents-md` | 프로젝트의 실제 모듈 구조에 맞게 조정된 부트스트랩 `AGENTS.md` 및 `CLAUDE.md` |
| `create-component` | 구성 요소 정의, 대화 상자 XML, HTL 템플릿, 슬링 모델, 단위 테스트 및 clientlib과 같은 전체 AEM 구성 요소의 스캐폴드 |
| `dispatcher` | 구성 작성, 기술 자문, 사고 대응, 성능 조정 및 보안 강화를 다루는 AI 기반 Dispatcher 및 Apache HTTPD 구성 지원 |
| `workflow` | 모든 AEM as a Cloud Service 워크플로 기술을 위한 단일 진입점입니다. 워크플로 모델 디자인, 사용자 지정 프로세스 단계 및 참가자 선택기 개발, 런처 구성, 워크플로 트리거 및 디버깅 중단/실패 워크플로, Cloud Manager 로그를 사용한 문제 트리징, 스레드 풀 분석 및 Granite 워크플로 엔진을 위한 Sling 작업 진단을 포함한 프로덕션 지원에 대해 다룹니다. |

### 스킬 설치 {#install-skills}

AI 코딩 도구와 일치하는 방법을 선택합니다. 기술을 한 번 설치하면 해당 컴퓨터의 모든 프로젝트에 사용할 수 있습니다.

#### 클로드 코드 {#claude-code}

```bash
# Add the Adobe Skills marketplace (one-time setup)
/plugin marketplace add adobe/skills#beta

# Install all available skills
/plugin install aem-cloud-service@adobe-skills
```

#### Npx 스킬 {#npx-skills}

```bash
# Install all available skills
npx skills add https://github.com/adobe/skills/tree/beta/skills/aem/cloud-service --all
```

#### 스킬 향상(GitHub CLI 확장) {#upskill-github-cli-extension}

```bash
# Install the gh-upskill extension (one-time setup)
gh extension install trieloff/gh-upskill

# Install all available skills
gh upskill adobe/skills --branch beta --path skills/aem/cloud-service --all
```

### ensure-agents-md 스킬 사용 {#use-the-ensure-agents-md-skill}

기술을 설치한 후 아직 `AGENTS.md`이(가) 없는 AEM Cloud Service 프로젝트에서 AI 도우미를 엽니다. 스킬은 첫 번째 요청을 처리하기 전에 자동으로 실행되어 명시적인 호출이 필요 없이 프로젝트 루트에서 두 파일을 모두 만듭니다.

### 구성 요소 만들기 스킬 사용 {#use-the-create-component-skill}

처음 사용 시 스킬은 `project` 및 기존 구성 요소에서 `package`, `group` 및 `pom.xml`을(를) 자동으로 감지하고 감지된 값을 확인하도록 요청한 다음 프로젝트 루트에서 `.aem-skills-config.yaml`을(를) 만듭니다. 처음 사용하기 전에 수동 구성이 필요하지 않습니다.

파일을 미리 만들려면 프로젝트 루트에 다음 구조로 `.aem-skills-config.yaml`을(를) 배치하십시오.

```yaml
configured: true

project: "wknd"                                    # Check /apps/{project}/ or pom.xml
package: "com.adobe.aem.guides.wknd.core"          # Check core/pom.xml
group: "WKND Components"                           # Check existing component .content.xml files
```

파일은 스킬 디렉토리 외부에 있으며 스킬이 업데이트될 때 덮어써지지 않습니다.

AI 채팅에서 구성 요소에 대해 설명합니다.

```
Create an AEM component called "Hero Banner"

Dialog specification:
Title (title) - Textfield, mandatory
Subtitle (subtitle) - Textfield
Background Image (backgroundImage) - Fileupload
CTA Text (ctaText) - Textfield
CTA Link (ctaLink) - Pathfield
```

에이전트는 확인을 위해 필드 사양을 되풀이한 다음 모든 구성 요소 파일을 생성합니다. 지원되는 패턴에는 복합 중첩 항목이 있는 다중 필드, 조건부 표시/숨기기 논리, Sling 리소스 병합을 통한 핵심 구성 요소 확장 및 AEM Mocks를 사용하는 JUnit 5 테스트가 포함됩니다.

### Dispatcher 스킬 사용 {#use-the-dispatcher-skill}

Dispatcher 또는 Apache HTTPD 구성 작업에 대한 Dispatcher 기술을 호출합니다. 이 스킬은 요청의 성격에 따라 6개의 전문가 하위 스킬 중 하나로 요청을 라우팅합니다.

| 하위 스킬 | 목적 |
|---|---|
| `workflow-orchestrator` | 설계, 구성 변경, 검증 및 후속 작업에 이르는 전체 작업 |
| `config-authoring` | 구체적인 구성 변경 사항: 필터, 캐시 규칙, 재작성, vhost, 헤더 및 팜 |
| `technical-advisory` | 개념 지침, 정책 설명 및 인용 지원 권장 사항 |
| `incident-response` | 런타임 실패, 캐시 예외 항목 및 회귀 |
| `performance-tuning` | 캐시 효율성, 지연 시간 및 처리량 최적화 |
| `security-hardening` | 노출 검토 및 생산 경화 |

광범위한 요청 또는 처음 요청의 경우 `workflow-orchestrator` 하위 스킬로 시작합니다. 대상 작업의 경우, 특정 관심사와 해당 전문가에게 기술 경로를 설명하십시오.

Dispatcher 기술은 오케스트레이션 및 자문 지침을 처리합니다. 아래에 설명된 Dispatcher MCP 서버는 로컬 증거가 필요할 때 이 기술이 사용하는 7가지 유효성 검사 및 런타임 도구를 제공합니다.

## AEM Quickstart MCP 서버 {#aem-quickstart-mcp-server}

모델컨텍스트 프로토콜(MCP)은 AI 코딩 도구가 외부 데이터 소스와 서비스에 연결할 수 있도록 하는 개방형 표준이다. AEM 빠른 시작 MCP 서버는 로컬 AEM SDK 인스턴스에 설치되면 연결된 AI 도구에 런타임 데이터를 직접 노출하는 컨텐츠 패키지로서 에이전트가 로그를 검색하고 OSGi 오류를 진단하며 IDE를 종료하지 않고 요청 처리를 검사할 수 있습니다.

### 콘텐츠 패키지 설치 {#install-the-content-package}

[소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Abeta)에서 콘텐츠 패키지를 다운로드하고 `com.adobe.aem:com.adobe.aem.mcp-server-contribs-content`의 패키지 관리자를 사용하여 `/crx/packmgr`을(를) 로컬 빠른 시작에 설치합니다.

**호환성:**&#x200B;이(가) AEM SDK `2026.2.24678.20260226T154829Z-260200` 이상에서 확인되었습니다.

### 사용 가능한 도구 {#available-tools}

| 도구 | 설명 |
|---|---|
| `aem-logs` | 정규 표현식 패턴, 로그 레벨 및 항목 카운트로 필터링 가능한 AEM 및 OSGi 로그 항목을 검색합니다. |
| `diagnose-osgi-bundle` | 번들 또는 DS 구성 요소가 시작되지 않는 이유를 진단하고 누락된 패키지, 충족되지 않은 참조 및 구성 문제를 보고합니다. |
| `recent-requests` | 경로 정규 표현식으로 필터링 가능한 Sling의 전체 내부 처리 추적(리소스 해상도, 스크립트 해상도, 필터 체인)을 사용하여 최근 HTTP 요청을 반환합니다. |

### IDE 구성 {#configure-your-ide}

#### 커서 {#cursor}

커서 설정에서 새 사용자 지정 MCP 서버를 추가합니다.

```json
"aem-cs-sdk": {
  "type": "streamable-http",
  "url": "http://localhost:4502/bin/mcp",
  "headers": {
    "Authorization": "Basic YWRtaW46YWRtaW4="
  }
}
```

#### IntelliJ IDEA를 사용한 GitHub Copilot {#github-copilot-with-ihtellij-idea}

**도구 > GitHub Copilot > 모델 컨텍스트 프로토콜(MCP)**&#x200B;로 이동하고 **구성**&#x200B;을 클릭합니다. 추가:

```json
"aem-cs-sdk": {
  "url": "http://localhost:4502/bin/mcp",
  "requestInit": {
    "headers": {
      "Authorization": "Basic YWRtaW46YWRtaW4="
    }
  }
}
```

#### 기타 IDE {#other-ides}

모든 MCP 클라이언트는 `http://localhost:4502/bin/mcp` 헤더가 있는 `Authorization: Basic YWRtaW46YWRtaW4=`을(를) 지정하여 연결할 수 있습니다. IDE의 MCP 설정을 사용하여 사용자 지정 헤더를 구성합니다.

>[!NOTE]
>
>값 `Basic YWRtaW46YWRtaW4=`은(는) 로컬 빠른 시작에 대한 기본 자격 증명인 `admin:admin`의 Base64 인코딩입니다. 비로컬 환경에서는 사용하지 마십시오.

## Dispatcher 서버 {#dispatcher-mcp-server}

Dispatcher MCP 서버는 AEM Dispatcher SDK과 번들로 제공됩니다. AI 도구를 통해 Dispatcher 및 Apache HTTPD 구성의 유효성을 검사하고, 요청 처리를 추적하고, Docker에서 로컬로 실행되는 Dispatcher 인스턴스에 대해 캐시 동작을 검사할 수 있습니다.

Dispatcher 스킬과 달리 Dispatcher MCP 서버는 7개의 MCP 도구만 노출하며 프롬프트 또는 리소스는 노출하지 않습니다.

### 사전 요구 사항 {#prerequisites}

- Docker Desktop 4.x 이상(설치 및 실행 중)
- AEM Dispatcher SDK은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Abeta)에서 다운로드되었습니다.

>[!NOTE]
>
>`client version 1.43 is too new`이(가) 표시되면 셸 또는 `DOCKER_API_VERSION=1.41`에서 `mcp.json`을(를) 설정하십시오.

### Dispatcher SDK 설치 {#install-the-dispatcher-sdk}

**macOS 및 Linux:**

```bash
chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
./aem-sdk-dispatcher-tools-<version>-unix.sh
cd dispatcher-sdk-<version>
chmod +x ./bin/docker_run_mcp.sh
./bin/docker_run_mcp.sh test
```

**창:**

```powershell
Expand-Archive aem-sdk-dispatcher-tools-<version>-windows.zip
```

`./bin/docker_run_mcp.sh help`을(를) 실행하여 복사-붙여넣기 IDE 구성을 검색하고 `./bin/docker_run_mcp.sh version`을(를) 실행하여 번들 MCP 및 SDK 버전을 확인합니다. 연결 문제를 조사하려면 `./bin/docker_run_mcp.sh diagnose`을(를) 사용하십시오.

### 커서 구성 {#configure-cursor}

`aem-dispatcher-mcp`에 `~/.cursor/mcp.json` 항목 추가:

```json
{
  "mcpServers": {
    "aem-dispatcher-mcp": {
      "command": "<path_to_dispatcher_sdk>/bin/docker_run_mcp.sh",
      "env": {
        "DOCKER_API_VERSION": "1.43",
        "AEM_DEPLOYMENT_MODE": "cloud",
        "MCP_LOG_LEVEL": "trace",
        "MCP_LOG_FILE": "/tmp/dispatcher-mcp.log",
        "DISPATCHER_CONFIG_PATH": "<path_to_dispatcher_src>"
      }
    }
  }
}
```

`<path_to_dispatcher_sdk>`을(를) 추출된 Dispatcher SDK 위치로 바꾸고 `<path_to_dispatcher_src>`을(를) 프로젝트의 Dispatcher `src` 디렉터리로 바꿉니다. `DISPATCHER_CONFIG_PATH`이(가) 정의된 파일을 포함하는 구성 루트로 `/docroot`을(를) 설정합니다. `MCP_LOG_LEVEL` 및 `MCP_LOG_FILE`은(는) 선택적 디버깅 설정입니다. `client version 1.43 is too new`이(가) 표시되면 `DOCKER_API_VERSION`을(를) `1.41`(으)로 설정하십시오. 다른 MCP 서버가 이미 구성된 경우 `aem-dispatcher-mcp` 항목을 바꾸지 않고 추가하십시오. 저장한 후 Cursor를 다시 시작합니다.

다른 IDE도 유사한 방식으로 구성할 수 있습니다. SDK `docs/DispatcherMCP.md`에는 클라우드 데스크톱 및 VS 코드에 대한 전체 예제가 포함되어 있습니다.

### 사용 가능한 도구 {#available-tools-dispatcher}

| 도구 | 설명 |
|---|---|
| `validate` | Dispatcher 및 Apache HTTPD 구성을 확인합니다. |
| `lint` | 모드 인식 정적 검사 및 모범 사례 분석 실행 |
| `sdk` | Dispatcher SDK 워크플로 실행: `validate`, `validate-full`, `three-phase-validate`, `docker-test`, `check-files`, `diff-baseline` |
| `trace_request` | 런타임 증거로 요청 동작 추적 |
| `inspect_cache` | 대상 URL에 대한 캐시 및 docroot 동작을 검사합니다 |
| `monitor_metrics` | Dispatcher 및 HTTPD 로그에서 런타임 지표를 읽습니다 |
| `tail_logs` | 관련 있는 Dispatcher 및 HTTPD 런타임 로그 |

MCP 표면은 의도적으로 이 7가지 도구만을 노출하며, 프롬프트 및 리소스는 스킬 레이어에 남습니다. 전체 참조 설명서는 추출된 Dispatcher SDK 내의 `docs/DispatcherMCP.md`에서 사용할 수 있습니다.
