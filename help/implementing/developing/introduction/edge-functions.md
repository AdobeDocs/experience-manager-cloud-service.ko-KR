---
title: AEM Edge 함수
description: 최종 사용자에게 가까운 곳에서 개인화, 보안 및 동적 경험을 활성화하기 위해 AEM Edge 기능을 사용하여 CDN 계층에서 JavaScript을 실행하는 방법에 대해 알아봅니다.
feature: Developing, Edge Delivery Services
role: Developer
source-git-commit: f8000bef01d6b72fb3ac2ae81be9fc19ed1a67d1
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 3%

---


# AEM Edge 함수 {#aem-edge-functions}

>[!IMPORTANT]
>
>AEM Edge 함수는 **베타** 기능입니다. 기능 및 설명서는 예고 없이 변경될 수 있습니다. 조기 액세스 프로그램에 참여하고 피드백을 제공하려면 [aemcs-edge-functions-feedback@adobe.com](mailto:aemcs-edge-functions-feedback@adobe.com)에 전자 메일을 보내세요.

AEM Edge Functions를 사용하면 CDN 계층에서 JavaScript을 실행하여 데이터 처리를 최종 사용자에게 가깝게 할 수 있습니다. 이를 통해 지연 시간을 줄이고 원본을 왕복하지 않고도 응답형의 동적 경험을 사용할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

- 지리적 위치, 장치 유형 또는 사용자 특성과 같은 정보를 기반으로 콘텐츠 개인화
- CDN과 원본 사이의 미들웨어 역할
- 브라우저에 도달하기 전에 서드파티 API의 응답 다시 서식 지정 또는 집계
- 여러 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML 작성 및 서비스

AEM Edge 함수는 Edge Delivery Services 및 AEM Cloud Service Java 스택과 호환됩니다.

## 주요 이점 {#key-benefits}

| 이점 | 설명 |
|---|---|
| **성능** | 에지 SSR을 통한 빠른 TTFB가 완전히 렌더링된 HTML을 반환합니다. 병렬 페치 및 최적화된 네트워크 홉을 통한 지연 시간이 짧은 API 호출. |
| **SEO / 지역** | 서버 HTML은 첫 번째 크롤링에 색인화되었습니다. 완전히 렌더링된 콘텐츠가 AI 웹 크롤러에 대해 준비되었습니다. |
| **보안** | API 자격 증명을 서버측에서 보관하고 클라이언트 JavaScript에서 숨겨집니다. ID 공급자로 인증하고 콘텐츠 액세스를 제한합니다. |
| **개인화** | 지역 및 장치 신호를 기반으로 페이지가 로드되기 전에 콘텐츠를 개인화합니다. 타겟팅된 게재를 위해 에지에서 대상 조회를 실행합니다. |

## 사전 요구 사항 {#prerequisites}

- AEM as a Cloud Service 환경
- Cloud Service 환경의 작성자 인스턴스에 대한 AEM 관리자 제품 프로필, Edge Delivery Services 사이트용 Admin Console의 Cloud Manager 배포 관리자 역할 **또는**
- [Node.js 및 npm](https://nodejs.org/)

## 설정 {#setup}

### Adobe CLI 설치 {#install-adobe-cli}

Adobe Developer CLI(`aio`)를 설치합니다.

```bash
npm install -g @adobe/aio-cli
```

AEM Edge 기능 플러그인 설치:

```bash
aio plugins install @adobe/aio-cli-plugin-aem-edge-functions
```

사용자 환경에 대한 플러그인 인증 및 구성:

```bash
aio login
aio aem edge-functions setup
```

setup 명령은 로그인한 다음 AEM Edge 기능을 사용할 AEM 환경을 선택하라는 메시지를 표시합니다.

### 보일러판 복제 {#boilerplate}

[aem-edge-functions-boilerplate](https://github.com/adobe/aem-edge-functions-boilerplate)을(를) 고유한 저장소에 복사한 다음 종속성을 설치하십시오.

```bash
npm install
```

## 첫 번째 함수 만들기 {#create-your-function}

AEM Edge 기능 서비스는 YAML 구성 파일에서 선언되고 Cloud Manager 구성 파이프라인을 통해 배포됩니다.

### &#x200B;1. 구성 파이프라인 설정 {#configuration-pipeline}

Edge 함수를 생성하기 전에 Cloud Manager에서 환경에 대한 구성 파이프라인이 있는지 확인하십시오. 그렇지 않으면 먼저 [구성 파이프라인을 만들기](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)하십시오.

>[!NOTE]
>
>RDE(빠른 개발 환경)를 사용하는 경우 구성 파이프라인을 거치지 않고 `aio aem rde:install -t env-config ./config`을(를) 사용하여 직접 구성을 배포할 수 있습니다.

### &#x200B;2. Edge 기능 서비스 선언 {#declare-services}

구성 디렉터리에 이름이 `edgeFunctions.yaml`인 파일을 만듭니다.

```yaml
kind: "EdgeFunctions"
version: "1"
data:
  services:
    - name: first-function
    - name: second-function
    # Uncomment to enable secrets
    # secrets:
    #   - key: API_TOKEN
    #     value: ${{ API_TOKEN_SECRET }}
```

이 구성은 최대 3개의 서비스를 지원합니다. 최상위 키는 다음과 같습니다.

| 키 | 설명 |
|---|---|
| `services` | `name`에 의해 각각 식별된 Edge 함수 서비스 목록입니다. |
| `configs` | 모든 Edge 함수 서비스에 환경 변수로 노출된 키/값 쌍입니다. |
| `secrets` | 모든 Edge 함수 서비스에 노출된 Cloud Manager 비밀을 참조하는 키/값 쌍입니다. |

### &#x200B;3. CDN Origin Selector 규칙 추가 {#cdn-routing}

Edge 함수는 원본 선택기 규칙을 통해 CDN 트래픽을 라우팅하여 호출됩니다. `cdn.yaml` 구성 파일에 다음 내용을 추가하거나 없는 경우 만듭니다.

```yaml
kind: 'CDN'
version: '1'
data:
  originSelectors:
    rules:
      - name: route-to-first-function
        when: { reqProperty: path, equals: "/weather" }
        action:
          type: selectAemOrigin
          originName: edgefunction-first-function
      - name: route-to-second-function
        when: { reqProperty: path, equals: "/hello-world" }
        action:
          type: selectAemOrigin
          originName: edgefunction-second-function
```

원본 선택기 규칙을 사용하면 특정 경로, 도메인 또는 요청 헤더와 같은 CDN 규칙 엔진에서 사용할 수 있는 조건을 기반으로 트래픽을 Edge 함수에 라우팅할 수 있습니다. 전체 규칙 구문은 [원본 선택기](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors)를 참조하십시오.

### &#x200B;4. 구성 배포 {#deploy-configuration}

`edgeFunctions.yaml`과(와) `cdn.yaml`을(를) 모두 Cloud Manager Git 저장소에 커밋하고 구성 파이프라인을 트리거합니다. 파이프라인이 정상적으로 완료되면 Edge 함수 엔드포인트를 사용할 수 있는 위치:

- `publish-pXXXXX-eYYYYY.adobeaemcloud.com/weather`
- `publish-pXXXXX-eYYYYY.adobeaemcloud.com/hello-world`

여기서 `pXXXXX-eYYYYY`은(는) 환경 좌표입니다. 사용자 지정 도메인이 구성되어 있으면 해당 도메인 경로(예: `example.com/weather`)에서도 함수를 연결할 수 있습니다.

## AEM Edge 기능 코드 작성 및 배포 {#build-deploy}

### 빌드 {#build}

배포를 위해 Edge 함수 코드를 패키징합니다.

```bash
aio aem edge-functions build
```

### 배포 {#deploy}

빌드된 패키지를 명명된 edge 함수 서비스에 배포합니다. `function-name` 인수는 `name`의 `edgeFunctions.yaml` 값과 일치해야 합니다.

```bash
aio aem edge-functions deploy <function-name>
```

## 로컬 개발 {#local-development}

### 로컬에서 실행 {#local-run}

`http://127.0.0.1:7676`에서 로컬 개발 서버 시작:

```bash
aio aem edge-functions serve
```

로컬 런타임에서 지원하는 기능에 대한 자세한 내용은 이 [JavaScript 계산 설명서](https://www.fastly.com/documentation/guides/compute/javascript/)를 참조하세요.

### 테스트 {#test}

[Mocha](https://mochajs.org/)&#x200B;(으)로 테스트 도구 모음 실행:

```bash
npm run test
```

### 원격 디버깅 {#remote-debugging}

Adobe Managed CDN은 원격 디버거를 노출하지 않지만 로그 스트리밍을 노출합니다. 배포된 함수에 대한 로그를 추적하여 터미널에서 직접 `console.log` 출력을 받습니다.

```bash
aio aem edge-functions tail-logs <function-name>
```

## 구성 참조 {#configuration-reference}

### 원본 {#origins}

기본적으로 Edge 함수는 모든 원본에서 가져올 수 있습니다. 함수를 정의된 원본 집합으로 제한하려면 `origins`의 `edgeFunctions.yaml` 아래에 선언하십시오.

```yaml
origins:
  - name: my-origin-name
    domain: example.com
```

`backend` 가져오기 옵션을 사용하여 함수 코드에서 명명된 원본을 참조합니다.

```js
const request = new Request("https://example.com/test");
const response = await fetch(request, { backend: "my-origin-name" });
```

### 서비스 구성 {#service-configuration}

`configs`에서 `edgeFunctions.yaml` 키를 사용하여 환경 변수를 함수에 노출합니다. 값이 `config_default`(이)라는 구성 저장소에 저장됩니다.

```yaml
configs:
  - key: LOG_LEVEL
    value: DEBUG
```

함수 코드에서 구성 값을 읽습니다.

```js
import { ConfigStore } from "fastly:config-store";

const config = new ConfigStore('config_default');
const logLevel = config.get('LOG_LEVEL') || 'info';
```

>[!NOTE]
>
>- 구성 저장소 이름은 항상 `config_default`입니다.
>- 키 이름은 대소문자를 구분합니다.
>- 구성 저장소는 동일한 환경의 모든 Edge 함수 서비스에서 공유됩니다.

### 서비스 암호 {#service-secrets}

`edgeFunctions.yaml`에서 암호가 참조되고 저장되지 않습니다. `value` 필드는 `${{SECRET_REFERENCE}}` 구문을 사용하여 Cloud Manager 암호를 지정해야 합니다. 먼저 Cloud Manager에서 기본 암호를 정의합니다. [Cloud Manager 암호 변수](/help/implementing/cloud-manager/environment-variables.md)를 참조하십시오.

```yaml
secrets:
  - key: API_TOKEN
    value: ${{ API_TOKEN_SECRET }}
```

상용구에서 `SecretStoreManager` 도우미를 사용하여 함수 코드의 암호를 검색합니다.

```js
import { SecretStoreManager } from "./lib/config";

const apiToken = await SecretStoreManager.getSecret('API_TOKEN');
```

>[!NOTE]
>
>- 암호 저장소의 이름은 항상 `secret_default`입니다.
>- 키 이름은 대소문자를 구분합니다.
>- 비밀은 일단 생성되면 변경할 수 없습니다.
>- 비밀 저장소는 동일한 환경의 모든 Edge Function 서비스에서 공유됩니다.

### 로깅 {#logging}

AEM Edge 함수는 [AEM 로그 전달](/help/implementing/developing/introduction/log-forwarding.md) 기능과 통합됩니다. `logForwarding.yaml`과(와) 함께 `edgeFunctions.yaml` 파일 만들기:

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["rde", "dev", "stage", "prod"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

함수 코드의 로거를 사용하여 구조화된 로그 항목을 작성합니다.

```js
import { Logger } from "fastly:logger";

const logger = new Logger("customerSplunk");
logger.log(JSON.stringify({
  method: event.request.method,
  url: event.request.url
}));
```

>[!NOTE]
>
>AEM Edge 기능 로그 항목을 포함하는 CDN 로그는 Java 스택 환경용 Cloud Manager에서 다운로드할 수 있지만 Edge Delivery Services 사이트에는 다운로드할 수 없습니다.
>
