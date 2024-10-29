---
title: 구성 파이프라인 사용하기
description: 구성 파이프라인을 사용하여 로그 전달 설정, 제거 관련 유지 관리 작업 및 다양한 CDN 구성과 같은 다양한 구성을 AEM as a Cloud Service에 배포하는 방법에 대해 알아봅니다.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 2247fdd919057703f1c35145ba2bc9c6ec47250b
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 1%

---

# 구성 파이프라인 사용하기 {#config-pipelines}

구성 파이프라인을 사용하여 로그 전달 설정, 제거 관련 유지 관리 작업 및 다양한 CDN 구성과 같은 다양한 구성을 AEM as a Cloud Service에 배포하는 방법에 대해 알아봅니다.

## 개요 {#overview}

Cloud Manager 구성 파이프라인은 YAML 형식으로 생성된 구성 파일을 대상 환경에 배포합니다. 로그 전달, 제거 관련 유지 관리 작업 및 여러 CDN 기능을 포함하여 AEM as a Cloud Service의 다양한 기능을 이러한 방식으로 구성할 수 있습니다.

구성 파이프라인은 Cloud Manager을 통해 프로덕션(샌드박스가 아닌) 프로그램의 개발, 스테이지 및 프로덕션 환경 유형에 배포할 수 있습니다. [명령줄 도구](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline)를 사용하여 RDE(빠른 개발 환경)에 구성 파일을 배포할 수 있습니다.

이 문서의 다음 섹션에서는 구성 파이프라인 을 사용하는 방법과 그에 대한 구성을 구성하는 방법에 관한 중요한 정보에 대한 개요를 제공합니다. 구성 파이프라인에서 지원하는 기능의 전체 또는 하위 집합에서 공유되는 일반적인 개념에 대해 설명합니다.

* [지원되는 구성](#configurations) - 구성 파이프라인으로 배포할 수 있는 구성 목록
* [구성 파이프라인 만들기 및 관리](#creating-and-managing) - 구성 파이프라인을 만드는 방법.
* [일반 구문](#common-syntax) - 구성 간에 공유된 구문
* [폴더 구조](#folder-structure) - 구성에 필요한 구조 구성 파이프라인을 설명합니다.
* [비밀 환경 변수](#secret-env-vars) - 환경 변수를 사용하여 구성에 비밀을 표시하지 않는 예입니다.

## 지원되는 구성 {#configurations}

다음 표는 이러한 구성의 포괄적인 목록을 제공하며, 개별 구성 구문 및 기타 정보를 설명하는 전용 설명서에 대한 링크를 제공합니다.

| 유형 | YAML `kind` 값 | 설명 |
|---|---|---|
| [WAF을 포함한 트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | 악성 트래픽을 차단하는 규칙 선언 |
| [변형 요청](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | 규칙을 선언하여 트래픽 요청의 모양을 변환합니다. |
| [응답 변환](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | 규칙을 선언하여 지정된 요청에 대한 응답의 모양을 변환합니다. |
| [클라이언트측 리디렉션](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) | `CDN` | 301/302 스타일 클라이언트측 리디렉션 선언 |
| [원본 선택기](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Adobe이 아닌 애플리케이션을 포함하여 다양한 백엔드로 트래픽을 라우팅하는 규칙을 선언합니다. |
| [CDN 오류 페이지](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | 구성 파일에서 자체 호스팅된 정적 콘텐츠의 위치를 참조하여 AEM 원본에 연결할 수 없는 경우 기본 오류 페이지를 재정의합니다. |
| [CDN 삭제](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | CDN을 제거하는 데 사용되는 Purge API 키 선언 |
| [고객 관리 CDN HTTP 토큰](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | 고객 CDN에서 Adobe CDN을 호출하는 데 필요한 X-AEM-Edge-Key 값 선언 |
| [기본 인증](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | 특정 URL [(얼리어답터만 사용 가능)을(를) 보호하는 기본 인증 대화 상자에 대한 사용자 이름과 암호를 선언합니다](/help/release-notes/release-notes-cloud/release-notes-current.md#foundation-early-adopter) |
| [버전 제거 유지 관리 작업](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | 컨텐츠 버전을 제거해야 하는 시점을 기준으로 규칙을 선언하여 AEM 저장소를 최적화합니다 |
| [감사 로그 제거 유지 관리 작업](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | 로그를 제거해야 하는 시점을 기준으로 규칙을 선언하여 AEM 감사 로그를 최적화하여 성능 향상 |
| [로그 전달](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | 아직 사용할 수 없음 - 로그를 다양한 대상(예: Splunk, Datadog, HTTPS)에 전달하기 위한 엔드포인트 및 자격 증명을 구성합니다. |

## 구성 파이프라인 생성 및 관리 {#creating-and-managing}

파이프라인을 만들고 구성하는 방법에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline) 문서를 참조하십시오.

Cloud Manager에서 구성 파이프라인을 만들 때 파이프라인을 구성할 때 **전체 스택 코드**&#x200B;이 아닌 **대상 배포**&#x200B;를 선택해야 합니다.

앞에서 설명한 대로 RDE에 대한 구성은 파이프라인이 아닌 [명령줄 도구](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline)를 사용하여 배포됩니다.


## 일반 구문 {#common-syntax}

각 구성 파일은 다음 예제 코드 조각과 유사한 속성으로 시작됩니다.

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
```

| 속성 | 설명 | 기본값 |
|---|---|---|
| `kind` | 로그 전달, 트래픽 필터 규칙 또는 요청 변환 등 구성 유형을 결정하는 문자열입니다 | 필수, 기본값 없음 |
| `version` | 스키마 버전을 나타내는 문자열 | 필수, 기본값 없음 |
| `envTypes` | 이 문자열 배열은 `metadata` 노드의 자식 속성입니다. 가능한 값은 dev, stage, prod 또는 모든 조합이며 구성이 처리될 환경 유형을 결정합니다. 예를 들어 배열에 `dev`만 포함된 경우 구성이 스테이지 또는 프로덕션 환경에 배포되더라도 구성이 로드되지 않습니다. | 모든 환경 유형(개발, 스테이지, 프로덕션) |

`yq` 유틸리티를 사용하여 구성 파일의 YAML 형식을 로컬로 확인할 수 있습니다(예: `yq cdn.yaml`).

## 폴더 구조 {#folder-structure}

`/config` 또는 유사한 이름의 폴더는 트리의 맨 위에 있어야 하며 그 아래 트리 어딘가에 YAML 파일이 하나 더 있어야 합니다.

예:

```text
/config
  cdn.yaml
```

또는

```text
/config
  /dev
    cdn.yaml
```

`/config` 아래의 폴더 이름 및 파일 이름은 임의의 이름입니다. 그러나 YAML 파일에는 유효한 [`kind` 속성 값이 있어야 합니다.](#configurations)

일반적으로 구성은 모든 환경에 배포됩니다. 각 환경에 대해 모든 속성 값이 동일하면 단일 YAML 파일로 충분합니다. 하지만 낮은 환경을 테스트하는 등의 경우에는 환경마다 속성 값이 다른 것이 일반적입니다.

다음 섹션에서는 파일을 구조화하기 위한 몇 가지 전략을 설명합니다.

### 모든 환경을 위한 단일 구성 파일 {#single-file}

파일 구조는 다음과 유사합니다.

```text
/config
  cdn.yaml
  logForwarding.yaml
```

모든 환경 및 모든 구성 유형(CDN, 로그 전달 등)에 대해 동일한 구성으로 충분한 경우 이 구조를 사용합니다. 이 시나리오에서는 `envTypes` 배열 속성에 모든 환경 유형이 포함됩니다.

```yaml
   kind: "cdn"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

암호 유형 환경 변수를 사용하면 `${{SPLUNK_TOKEN}}` 참조에 표시된 대로 [암호 속성](#secret-env-vars)이 환경별로 달라질 수 있습니다

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

### 환경 유형별 개별 파일 {#file-per-env}

파일 구조는 다음과 유사합니다.

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

속성 값에 차이가 있을 수 있는 경우 이 구조를 사용합니다. 예를들어, 파일에서 `envTypes` 배열 값은 접미사와 일치해야 합니다
값이 `["dev"]`인 `cdn-dev.yaml` 및 `logForwarding-dev.yaml`, 값이 `["stage"]`인 `cdn-stage.yaml` 및 `logForwarding-stage.yaml` 등입니다.

### 환경당 폴더 {#folder-per-env}

이 전략에서는 환경당 별도의 `config` 폴더가 있으며 각 폴더에 대해 Cloud Manager에서 선언된 별도의 파이프라인이 있습니다.

이 접근 방식은 각 개발 환경에 고유한 속성 값이 있는 경우 특히 유용합니다.

파일 구조는 다음과 유사합니다.

```text
/config/dev1
  cdn.yaml
  logForwarding.yaml
/config/dev2
  cdn.yaml
  logForwarding.yaml
/config/prod  
  cdn.yaml
  logForwarding.yaml
```

이 방법의 변형은 환경당 별도의 분기를 유지 관리하는 것입니다.

## 보안 환경 변수 {#secret-env-vars}

중요한 정보를 소스 제어에 저장할 필요가 없도록 구성 파일은 **secret** 유형의 Cloud Manager 환경 변수를 지원합니다. 로그 전달을 비롯한 일부 구성의 경우 특정 속성에 대해 보안 환경 변수가 필수입니다.

아래 코드 조각은 구성에 보안 환경 변수 `${{SPLUNK_TOKEN}}`이(가) 사용되는 방법의 예입니다.

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

환경 변수를 사용하는 방법에 대한 자세한 내용은 [Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md) 문서를 참조하십시오.
