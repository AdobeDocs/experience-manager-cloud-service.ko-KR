---
title: WAF 규칙이 포함된 트래픽 필터 규칙
description: 웹 애플리케이션 방화벽(WAF)이 포함된 트래픽 필터 규칙 구성
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: 9f23b91df3139115ca442de03457bb50a1e1cb71
workflow-type: tm+mt
source-wordcount: '3669'
ht-degree: 91%

---


# WAF 규칙이 포함된 트래픽 필터 규칙 {#traffic-filter-rules-including-waf-rules}

트래픽 필터 규칙을 사용하여 CDN 계층에서 요청을 차단하거나 허용할 수 있으므로 이는 다음과 같은 시나리오에 유용할 수 있습니다.

* 새 사이트가 라이브로 전환되기 전 회사 내부 트래픽으로 특정 도메인에 대한 액세스 제한
* 대규모 DoS 공격에 대한 취약성을 줄이기 위해 속도 제한 설정
* 악성으로 알려진 IP 주소가 사용자 페이지를 타겟팅하지 않도록 함

대부분의 트래픽 필터 규칙은 모든 AEM as a Cloud Service Sites 및 Forms 고객이 사용할 수 있습니다. 이 규칙은 IP, 호스트 이름, 경로 및 사용자 에이전트를 포함하여 요청 속성과 요청 헤더에서 주로 작동합니다.

트래픽 필터 규칙의 하위 범주는 향상된 보안 라이선스와 WAF-DDoS 보호 라이선스 중 하나가 필요합니다. 이러한 강력한 규칙은 WAF(웹 애플리케이션 방화벽) 트래픽 필터 규칙(이하 WAF 규칙)이라고 하며 이 문서 후반부에 설명된 [WAF 플래그](#waf-flags-list)에 액세스할 수 있습니다.

Cloud Manager 구성 파이프라인을 통해 트래픽 필터 규칙을 프로덕션(비샌드박스) 프로그램의 dev, stage 및 prod 환경 유형에 배포할 수 있습니다. RDE에 대한 지원은 향후 제공될 예정입니다.

[튜토리얼을 참고하면](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html) 이 기능에 대한 전문 지식을 빠르게 습득할 수 있습니다.

>[!NOTE]
>요청/응답 수정, 리디렉션 선언 및 비 AEM 오리진으로의 프록시 지정을 포함하여 CDN에서 트래픽을 구성하는 다른 옵션에 관심이 있으십니까? [방법을 알아보고 사용해 보십시오.](/help/implementing/dispatcher/cdn-configuring-traffic.md) 얼리어답터 프로그램에 참여함으로써.


## 이 문서를 구성하는 방식 {#how-organized}

이 문서는 다음 섹션으로 구성되어 있습니다.

* **트래픽 보호 개요:** 악성 트래픽으로부터 사용자를 보호하는 방법에 대해 알아보십시오.
* **규칙을 구성하는 프로세스 제안:** 웹 사이트 보호를 위한 높은 수준의 방법론을 읽어 보십시오.
* **설정:** 고급 WAF 규칙을 포함하여 트래픽 필터 규칙을 설정, 구성 및 배포하는 방법에 대해 알아보십시오.
* **규칙 구문:** `cdn.yaml` 구성 파일에서 트래픽 필터 규칙을 선언하는 방법에 대해 알아보십시오. 여기에는 모든 Sites 및 Forms 고객이 사용할 수 있는 트래픽 필터 규칙과 함께 해당 기능에 라이선스를 부여하는 고객을 위한 WAF 규칙의 하위 범주가 모두 포함되어 있습니다.
* **규칙 예:** 진행 과정을 알아보려면 선언된 규칙의 예를 참조하십시오.
* **속도 제한 규칙:** 대규모 공격으로부터 사이트를 보호하려면 속도 제한 규칙을 사용하는 방법에 대해 알아보십시오
* **CDN 로그:** 선언된 규칙과 WAF 플래그가 트래픽과 일치하는지 확인하십시오.
* **대시보드 도구:** CDN 로그를 분석하여 새로운 트래픽 필터 규칙을 구상해 보십시오.
* **권장 스타터 규칙:** 규칙 집합을 시작하는 데 필요한 규칙입니다.
* **튜토리얼:** 대시보드 도구로 올바른 규칙을 선언하는 방법을 비롯해 기능에 대한 실질적인 지식입니다.

**aemcs-waf-adopter@adobe.com**&#x200B;으로 메일을 보내어 트래픽 필터 규칙에 대한 피드백을 제공하거나 질문을 보내 주시기 바랍니다.

## 트래픽 보호 개요 {#traffic-protection-overview}

오늘날 디지털 환경에서 악성 트래픽은 항상 우리를 위협하는 존재입니다. 위험의 심각성을 인지하고 고객 애플리케이션을 보호하고 공격 시 이를 완화하기 위한 여러 가지 방법을 제공합니다.

Edge에서 Adobe Managed CDN은 대규모 및 반사/증폭 공격(레이어 3 및 4)을 포함하여 네트워크 레이어의 DoS 공격을 흡수합니다.

기본적으로 Adobe는 특정 임계값을 초과하는 높은 수준의 트래픽 버스트로 인해 발생하는 성능 저하를 방지하기 위한 조치를 취합니다. DoS 공격이 사이트 가용성에 영향을 미치는 경우 Adobe 운영 팀에 경고하여 완화 조치를 취하도록 합니다.

고객은 콘텐츠 게재 흐름의 다양한 레이어에서 규칙을 구성하여 애플리케이션 레이어 공격(레이어 7)을 완화하기 위한 사전 조치를 취할 수 있습니다.

예를 들어 Apache 계층에서 고객은 [Dispatcher 모듈](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter)과 [ModSecurity](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection.html) 중 하나를 구성하여 특정 콘텐츠에 대한 액세스를 제한할 수 있습니다.

이 문서의 설명에 따라 Cloud Manager의 구성 파이프라인을 사용하여 트래픽 필터 규칙을 Adobe Managed CDN에 배포할 수 있습니다. IP 주소, 경로 및 헤더 등 속성 기반의 트래픽 필터 규칙 또는 속도 제한 설정 기반의 규칙 외에도 고객은 WAF 규칙이라는 트래픽 필터 규칙의 강력한 하위 범주에 라이선스를 부여할 수도 있습니다.

## 권장 프로세스 {#suggested-process}

다음 프로세스는 올바른 트래픽 필터 규칙을 권장하는 높은 수준의 엔드 투 엔드 프로세스입니다.

1. [설정](#setup) 섹션의 설명에 따라 비프로덕션 및 프로덕션 구성 파이프라인을 구성하십시오.
1. WAF 트래픽 필터 규칙의 하위 범주에 라이선스를 부여한 고객은 Cloud Manager에서 해당 규칙을 활성화해야 합니다.
1. 라이선스가 부여된 경우, WAF 규칙 등 트래픽 필터 규칙을 사용하는 방법을 구체적으로 이해하려면 튜토리얼을 읽고 테스트해 보십시오. 튜토리얼은 개발 환경에 규칙을 배포하고, 악성 트래픽을 시뮬레이션하고, [CDN 로그](#cdn-logs)를 다운로드하고, [대시보드 도구](#dashboard-tooling)로 로그를 분석하는 과정에 대해 소개합니다.
1. 권장 스타터 규칙을 `cdn.yaml`에 복사하고 로그 모드에서 구성을 프로덕션 환경에 배포하십시오.
1. 일부 트래픽을 수집한 후 일치 항목이 있는지 확인하려면 [대시보드 도구](#dashboard-tooling)를 사용하여 결과를 분석하십시오. 긍정 오류를 파악하고 필요한 사항을 조정하여 최종적으로 차단 모드에서 스타터 규칙을 활성화할 수 있습니다.
1. CDN 로그 분석 기반의 사용자 정의 규칙을 추가하여 먼저 개발 환경에서 시뮬레이션된 트래픽으로 테스트한 후 로그 모드에서 스테이지 및 프로덕션 환경에 배포한 다음 차단 모드에서 배포하십시오.
1. 트래픽을 지속적으로 모니터링하면서 위협 환경이 변함에 따라 규칙을 변경하십시오.

## 설정 {#setup}

1. 먼저 Git 내 프로젝트의 최상위 폴더에 다음 폴더와 파일 구조를 만드십시오.

   ```
   config/
        cdn.yaml
   ```

1. `cdn.yaml`은 메타데이터와 트래픽 필터 규칙 및 WAF 규칙 목록을 포함해야 합니다.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
       # Block simple path
       - name: block-path
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/block/me'
         action: block
   ```

`kind` 매개변수는 `CDN`으로 설정되어야 하며 버전은 스키마 버전(현재 `1`)으로 설정되어야 합니다. 아래 추가 예를 참조하십시오.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (for example, "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. WAF 규칙에 라이선스가 부여된 경우, 신규 및 기존 프로그램 시나리오 모두에 대해 아래에 설명된 대로 Cloud Manager에서 기능을 활성화해야 합니다.

   1. 새 프로그램에서 WAF를 구성하려면 [프로덕션 프로그램 추가 시 **보안 탭**&#x200B;의 **WAF-DDOS 보호** 확인란을 선택하십시오.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

   1. 기존 프로그램에서 WAF를 구성하려면 **보안** 탭에서 [프로그램을 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)하여 언제든지 **WAF-DDOS** 옵션을 선택 취소하거나 선택하십시오.

1. RDE 이외의 환경 유형의 경우 Cloud Manager에서 타겟팅 배포 구성 파이프라인을 만드십시오.

   * [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)을 참조하십시오.
   * [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)을 참조하십시오.

RDE의 경우 명령이 사용되지만 RDE는 현재 지원되지 않습니다.

**메모**

* `yq`을 사용하여 구성 파일(예: `yq cdn.yaml`)의 YAML 서식을 로컬에서 확인할 수 있습니다.

## 트래픽 필터 규칙 구문 {#rules-syntax}

IPS, 사용자 에이전트, 요청 헤더, 호스트 이름, 지역 및 URL과 같은 패턴을 일치하도록 `traffic filter rules`을 구성할 수 있습니다.

향상된 보안 또는 WAF-DDoS 보호 보안 제품에 라이선스를 부여한 고객은 하나 이상의 [WAF 플래그](#waf-flags-list)를 참조하는 `WAF traffic filter rules`(이하 WAF 규칙)이라고 하는 트래픽 필터 규칙의 특수 범주를 구성할 수도 있습니다.

다음은 WAF 규칙도 포함하는 트래픽 필터 규칙 세트의 예입니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

`cdn.yaml` 파일의 트래픽 필터 규칙 형식은 아래에서 설명합니다. 이후 섹션 및 [속도 제한 규칙](#rate-limit-rules)에 대한 별도의 섹션에서 [기타 예](#examples)를 참조하십시오.


| **속성** | **대부분의 트래픽 필터 규칙** | **WAF 트래픽 필터 규칙** | **유형** | **기본 값** | **설명** |
|---|---|---|---|---|---|
| 이름 | X | X | `string` | - | 규칙 이름(64자 길이, 영숫자 및 - 만 포함할 수 있음) |
| when | X | X | `Condition` | - | 기본 구조는 다음과 같습니다.<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[getter, 조건자 및 여러 조건을 결합하는 방법을 설명하는 아래의 조건 구조 구문을 참조하십시오.](#condition-structure) |
| action | X | X | `Action` | 로그 | log, allow, block 또는 action 오브젝트. 기본값은 log임 |
| rateLimit | X |   | `RateLimit` | 정의되지 않음 | 속도 제한 구성입니다. 속도 제한은 정의되지 않은 경우 비활성화됩니다.<br><br>예제와 함께 rateLimit 구문을 설명하는 별도의 섹션이 아래에 추가로 있습니다. |

### 조건 구조 {#condition-structure}

조건은 단순 조건이거나 조건 그룹일 수 있습니다.

**단순 조건**

단순 조건은 getter와 조건자로 구성됩니다.

```
{ <getter>: <value>, <predicate>: <value> }
```

**그룹 조건**

조건 그룹은 여러 단순 조건 및/또는 그룹 조건으로 구성됩니다.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **속성** | **유형** | **의미** |
|---|---|---|
| **allOf** | `array[Condition]` | **and** 작업입니다. 나열된 모든 조건이 true를 반환하는 경우 true |
| **anyOf** | `array[Condition]` | **or** 작업입니다. 나열된 조건 중 하나라도 true를 반환하는 경우 true |

**getter**

| **속성** | **유형** | **설명** |
|---|---|---|
| reqProperty | `string` | 요청 속성입니다.<br><br>다음 중 하나:<br><ul><li>`path`: 쿼리 매개변수 없이 URL의 전체 경로를 반환합니다.</li><li>`queryString`: URL의 쿼리 부분을 반환합니다.</li><li>`method`: 요청에 사용된 HTTP 메서드를 반환합니다.</li><li>`tier`: `author`, `preview` 또는 `publish` 중 하나를 반환합니다.</li><li>`domain`: (`Host` 헤더에 정의된) 도메인 속성을 소문자로 반환합니다.</li><li>`clientIp`: 클라이언트 IP를 반환합니다.</li><li>`clientCountry`: 두 자리 코드를 반환합니다(클라이언트가 위치한 국가를 식별하는 [https://en.wikipedia.org/wiki/kr/Regional_indicator_symbol](https://en.wikipedia.org/wiki/kr/Regional_indicator_symbol)).</li></ul> |
| reqHeader | `string` | 지정된 이름의 요청 헤더를 반환합니다. |
| queryParam | `string` | 지정된 이름의 쿼리 매개변수를 반환합니다. |
| reqCookie | `string` | 지정된 이름의 쿠키를 반환합니다. |
| postParam | `string` | 요청 본문에서 이름이 지정된 POST 매개변수를 반환합니다. 본문이 콘텐츠 유형 `application/x-www-form-urlencoded`인 경우에만 적용 |

**조건자**

| **속성** | **유형** | **의미** |
|---|---|---|
| **equals** | `string` | getter 결과가 제공된 값과 같은 경우 true |
| **doesNotEqual** | `string` | getter 결과가 제공된 값과 같지 않은 경우 true |
| **like** | `string` | getter 결과가 제공된 패턴과 일치하는 경우 true |
| **notLike** | `string` | getter 결과가 제공된 패턴과 일치하지 않는 경우 true |
| **matches** | `string` | getter 결과가 제공된 정규 표현식과 일치하는 경우 true |
| **doesNotMatch** | `string` | getter 결과가 제공된 정규 표현식과 일치하지 않는 경우 true |
| **in** | `array[string]` | 제공된 목록에 getter 결과가 포함되어 있는 경우 true |
| **notIn** | `array[string]` | 제공된 목록에 getter 결과가 포함되어 있지 않은 경우 true |
| **존재함** | `boolean` | true로 설정되고 속성이 있는 경우 또는 false로 설정되고 속성이 없는 경우 true임 |

**메모**

* 요청 속성 `clientIp`은 다음 조건자 `equals`, `doesNotEqual`, `in`, `notIn`에만 사용할 수 있습니다. `in` 및 `notIn` 조건자 사용 시 `clientIp`은 IP 범위와 비교될 수도 있습니다. 다음 예에서 조건을 구현하여 IP 클라이언트가 192.168.0.0/24의 IP 범위(즉 192.168.0.0에서 192.168.0.255까지)에 있는지 평가할 수 있습니다.

```
when:
  reqProperty: clientIp
  in: [ "192.168.0.0/24" ]
```

* 정규 표현식을 사용하여 작업할 때 [regex101](https://regex101.com/) 및 [Fastly Fiddle](https://fiddle.fastly.dev/)을 사용하는 것이 좋습니다. 이 [문서](https://developer.fastly.com/reference/vcl/regex/#best-practices-and-common-mistakes)에서 Fastly가 정규 표현식을 처리하는 방법에 대한 자세한 내용을 알아볼 수 있습니다.


### 액션 구조 {#action-structure}

`action`은 작업(허용, 차단 또는 로그)을 지정하는 문자열이거나 작업 유형(허용, 차단 또는 로그)과 wafFlags 및/또는 상태와 같은 옵션으로 구성된 오브젝트일 수 있습니다.

**액션 유형**

액션의 실행 순서를 반영하도록 정렬되어 있는 다음 표의 액션 유형에 따라 액션의 우선순위를 지정합니다.

| **이름** | **허용된 속성** | **의미** |
|---|---|---|
| **허용** | `wafFlags` (선택 사항), `alert` (선택 사항이며 아직 릴리스되지 않음) | wafFlags가 없으면 추가 규칙 처리를 중지하고 응답 제공을 진행합니다. wafFlags가 있으면 지정된 WAF 보호를 비활성화하고 추가 규칙 처리를 진행합니다. <br>경고가 지정된 경우 규칙이 5분 동안 10번 트리거되면 작업 센터 알림이 전송됩니다. 이 기능은 아직 릴리스되지 않았습니다. [트래픽 필터 규칙 경고](#traffic-filter-rules-alerts) early adopter 프로그램에 참여하는 방법에 대한 섹션. |
| **블록** | `status, wafFlags` (선택 사항이며 함께 사용할 수 없음), `alert` (선택 사항이며 아직 릴리스되지 않음) | wafFlags가 없으면 다른 모든 속성을 무시하는 HTTP 오류를 반환하고, 상태 속성으로 오류 코드를 정의하거나 406을 기본으로 표시합니다. wafFlags가 있으면 지정된 WAF 보호를 활성화하고 추가 규칙 처리를 진행합니다. <br>경고가 지정된 경우 규칙이 5분 동안 10번 트리거되면 작업 센터 알림이 전송됩니다. 이 기능은 아직 릴리스되지 않았습니다. [트래픽 필터 규칙 경고](#traffic-filter-rules-alerts) early adopter 프로그램에 참여하는 방법에 대한 섹션. |
| **로그** | `wafFlags` (선택 사항), `alert` (선택 사항이며 아직 릴리스되지 않음) | 규칙이 트리거되었다는 사실을 로그 기록하지 않으면 처리에 영향을 주지 않습니다. wafFlags는 영향을 주지 않습니다. <br>경고가 지정된 경우 규칙이 5분 동안 10번 트리거되면 작업 센터 알림이 전송됩니다. 이 기능은 아직 릴리스되지 않았습니다. [트래픽 필터 규칙 경고](#traffic-filter-rules-alerts) early adopter 프로그램에 참여하는 방법에 대한 섹션. |

### WAF 플래그 목록 {#waf-flags-list}

라이선스가 부여될 수 있는 WAF 트래픽 필터 규칙에 사용할 수 있는 `wafFlags` 속성에 대해서는 다음을 참조하십시오.

| **플래그 ID** | **플래그 이름** | **설명** |
|---|---|---|
| SQLI | SQL 주입 | SQL 주입은 임의의 데이터베이스 쿼리를 실행하여 애플리케이션에 대한 액세스 권한을 얻거나 권한 있는 정보를 얻으려는 시도입니다. |
| BACKDOOR | 백도어 | 백도어 신호는 일반적인 백도어 파일이 시스템에 있는지 확인하려고 시도하는 요청입니다. |
| CMDEXE | 명령 실행 | 명령 실행은 사용자 입력을 통해 임의의 시스템 명령으로 대상 시스템을 제어하거나 손상시키려는 시도입니다. |
| XSS | 크로스 사이트 스크립팅 | 크로스 사이트 스크립팅은 악성 JavaScript 코드를 통해 사용자의 계정이나 웹 탐색 세션을 하이재킹하려는 시도입니다. |
| TRAVERSAL | 디렉터리 순회 | 디렉터리 순회는 민감한 정보를 얻기 위해 시스템 전체에서 권한 있는 폴더를 탐색하려는 시도입니다. |
| USERAGENT | 공격 툴링 | 공격 툴링은 자동화된 소프트웨어를 사용하여 보안 취약성을 식별하거나 발견된 취약성을 악용하려고 시도하는 것입니다. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI 공격은 2.16.0 이전 Log4J 버전에 있는 [Log4Shell 취약점](https://en.wikipedia.org/wiki/kr/Log4Shell)을 활용하려고 시도합니다. |
| BHH | 잘못된 홉 헤더 | 잘못된 홉 헤더는 잘못된 형식의 TE(Transfer-Encoding) 또는 CL(Content-Length) 헤더나 올바른 형식의 TE 및 CL 헤더를 통한 HTTP 스머글링 시도를 나타냅니다. |
| CODEINJECTION | 코드 삽입 | 코드 삽입은 사용자 입력을 통해 임의의 애플리케이션 코드 명령으로 대상 시스템을 제어하거나 손상시키려는 시도입니다. |
| ABNORMALPATH | 비정상 경로 | 비정상 경로는 원래 경로가 정규화된 경로와 다름을 나타냅니다(예: `/foo/./bar`는 `/foo/bar`로 정규화됨). |
| DOUBLEENCODING | 이중 인코딩 | 이중 인코딩은 html 문자를 이중 인코딩하는 회피 기술을 확인합니다. |
| NOTUTF8 | 잘못된 인코딩 | 잘못된 인코딩으로 인해 서버가 요청의 악성 문자를 응답으로 변환하여 서비스 거부 또는 XSS가 발생할 수 있습니다. |
| JSON-ERROR | JSON 인코딩 오류 | “Content-Type” 요청 헤더 내에 JSON을 포함하도록 지정되었지만 JSON 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문입니다. 흔히 프로그래밍 오류나 자동화된 요청 또는 악성 요청과 관련이 있습니다. |
| MALFORMED-DATA | 요청 본문의 형식이 잘못된 데이터 | “Content-Type” 요청 헤더에 따라 형식이 잘못된 POST, PUT 또는 PATCH 요청 본문입니다. 예를 들어 “Content-Type: application/x-www-form-urlencoded” 요청 헤더가 지정되고 json인 POST 본문을 포함하는 경우입니다. 흔히 프로그래밍 오류, 자동화된 요청 또는 악성 요청에 해당합니다. 에이전트 3.2 이상이 필요합니다. |
| SANS | 악성 IP 트래픽 | 악성 활동에 연루된 것으로 보고된 [SANS 인터넷 스톰 센터](https://isc.sans.edu/) IP 주소 목록입니다. |
| NO-CONTENT-TYPE | 누락된 “Content-Type” 요청 헤더 | “Content-Type” 요청 헤더가 없는 POST, PUT 또는 PATCH 요청입니다. 이 경우 기본적으로 애플리케이션 서버는 “Content-Type: text/plain; charset=us-ascii”를 가정하게 됩니다. 자동화된 요청 및 악성 요청 중 대다수에서 “Content Type”이 누락되어 있을 수 있습니다. |
| NOUA | 사용자 에이전트 없음 | 자동화된 요청 및 악성 요청 중 대다수가 가짜 사용자 에이전트 또는 누락된 사용자 에이전트를 사용하여 요청 주체인 디바이스 유형을 식별하기 어렵게 만듭니다. |
| TORNODE | Tor 트래픽 | Tor는 사용자의 신원을 숨기는 소프트웨어입니다. Tor 트래픽 스파이크가 발생한다면 공격자가 자신의 위치를 숨기려고 시도하고 있음을 나타낼 수 있습니다. |
| NULLBYTE | Null 바이트 | Null 바이트는 일반적으로 요청에 표시되지 않으며, 요청이 잘못된 형식이고 잠재적으로 악성임을 나타냅니다. |
| PRIVATEFILE | 비공개 파일 | 비공개 파일은 민감한 정보를 유출할 수 있는 Apache `.htaccess` 파일 또는 구성 파일 등으로서, 흔히 본질적으로 기밀입니다. |
| SCANNER | 스캐너 | 널리 사용되는 스캔 서비스 및 도구를 식별합니다. |
| RESPONSESPLIT | HTTP 응답 분할 | 헤더를 HTTP 응답에 삽입하기 위해 CRLF 문자가 애플리케이션에 대한 입력으로 제출되는 시점을 식별합니다. |
| XML-ERROR | XML 인코딩 오류 | “Content-Type” 요청 헤더 내에 XML을 포함하도록 지정되었지만 XML 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문입니다. 흔히 프로그래밍 오류나 자동화된 요청 또는 악성 요청과 관련이 있습니다. |

## 고려 사항 {#considerations}

* 충돌하는 두 규칙이 만들어졌을 때는 항상 허용 규칙이 차단 규칙보다 우선합니다. 예를 들어 특정 경로를 차단하는 규칙과 하나의 특정 IP 주소를 허용하는 규칙을 만들면 차단된 경로에서 해당 IP 주소의 요청이 허용됩니다.

* 규칙이 일치하여 차단되면 CDN은 `406` 반환 코드로 응답합니다.

* git 저장소에 액세스할 수 있는 모든 사용자가 암호를 읽을 수 있으므로 구성 파일은 비밀을 포함해서는 안 됩니다.

* Cloud Manager에 정의된 IP 허용 목록은 트래픽 필터 규칙보다 우선합니다.

* WAF 규칙 일치는 히트가 아닌 CDN 실패 및 통과에 대한 CDN 로그에만 나타납니다.

## 규칙 예 {#examples}

몇 가지 규칙 예는 다음과 같습니다. 속도 제한 규칙의 예는 아래쪽의 [속도 제한 섹션](#rules-with-rate-limits)을 참조하십시오.

**예 1**

다음 규칙은 **IP 192.168.1.1**&#x200B;에서 오는 요청을 차단합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action:
           type: block
```

**예 2**

다음 규칙은 Chrome이 포함된 User-Agent로 게시할 때 `/helloworld` 경로에 대한 요청을 차단합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
        when:
          allOf:
          - { reqProperty: path, equals: /helloworld }
          - { reqProperty: tier, equals: publish }
          - { reqHeader: user-agent, matches: '.*Chrome.*'  }
        action:
          type: block
```

**예 3**

다음 규칙은 쿼리 매개변수 `foo`가 포함된 요청을 차단하지만 IP 192.168.1.1에서 오는 모든 요청은 허용합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when: { queryParam: url-param, equals: foo }
        action:
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action:
          type: allow
```

**예 4**

다음 규칙은 `/block-me` 경로에 대한 요청을 차단하고 `SQLI` 또는 `XSS` 패턴과 일치하는 모든 요청을 차단합니다. 이 예에는 `SQLI` 및 `XSS` [WAF 플래그](#waf-flags-list)를 참조하고 별도의 라이선스가 필요한 WAF 트래픽 필터 규칙이 포함되어 있습니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

**예 5**

이 규칙은 OFAC 국가에 대한 액세스를 차단합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - reqProperty: tier
              matches: "author|publish"
            - reqProperty: clientCountry
              in:
                - SY
                - BY
                - MM
                - KP
                - IQ
                - CD
                - SD
                - IR
                - LR
                - ZW
                - CU
                - CI
        action: block
```

## 속도 제한 규칙 {#rate-limits-rules}

특정 조건에 따라 트래픽이 수신 요청의 특정 속도를 초과하는 경우 트래픽을 차단하는 것이 바람직한 경우가 있습니다. `rateLimit` 속성의 값을 설정하면 규칙 조건과 일치하는 요청의 속도가 제한됩니다.

속도 제한 규칙은 WAF 플래그를 참조할 수 없습니다. 해당 플래그는 모든 Sites 및 Forms 고객이 사용할 수 있습니다.

속도 제한은 CDN POP당 계산됩니다. 예를 들어 몬트리올, 마이애미, 더블린의 POP에서 초당 각 80, 90, 120 요청에 대해 트래픽 속도를 경험하고 속도 제한 규칙이 100으로 제한 설정되어 있다고 가정하겠습니다. 이 경우 더블린으로 보내는 트래픽만 속도가 제한됩니다.

### rateLimit 구조 {#ratelimit-structure}

| **속성** | **유형** | **기본값** | **의미** |
|---|---|---|---|
| limit | 10에서 10000 사이의 정수 | required | 규칙이 트리거되는 초당 요청의 요청 속도(CDN POP당)입니다. |
| window | 정수 열거형: 1, 10 또는 60 | 10 | 요청 속도를 계산하는 샘플링 기간(초). 카운터의 정확도는 창의 크기에 따라 달라집니다(창이 클수록 정확도가 높아짐). 예를 들어 1초 시간 제한 창에서는 50% 정확도를 기대하고 60초 시간 제한 창에서는 90% 정확도를 기대할 수 있습니다. |
| penalty | 60에서 3600 사이의 정수 | 300(5분) | 일치하는 요청이 차단되는 기간(초 단위로 반올림). |
| groupBy | 배열[getter] | 없음 | 처리율 제한 장치 카운터는 요청 속성 세트(예: clientIp)로 집계됩니다. |


### 예 {#ratelimiting-examples}

**예 1**

이 규칙은 지난 10초 동안 평균 60req/sec(CDN POP당)를 초과하면 5분간 클라이언트를 차단합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**예 2**

지난 60초 동안 평균 100req/sec(CDN POP당)를 초과하면 경로/중요/리소스에서 60초간 요청을 차단합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when: { reqProperty: path, equals: /critical/resource }
        action:
          type: block
        rateLimit: { limit: 100, window: 60, penalty: 60 }
```

## 트래픽 필터 규칙 경고 {#traffic-filter-rules-alerts}

>[!NOTE]
>
>이 기능은 아직 릴리스되지 않았습니다. 얼리 어답터 프로그램을 통해 액세스 권한을 얻으려면, 이메일을 보내십시오. **aemcs-waf-adopter@adobe.com**.

5분 기간 내에 10번 트리거되는 경우 작업 센터 알림을 보내도록 규칙을 구성할 수 있으므로 특정 트래픽 패턴이 발생하면 경고하여 필요한 조치를 취할 수 있습니다. 자세히 알아보기 [작업 센터](/help/operations/actions-center.md)이메일 수신에 필요한 알림 프로필을 설정하는 방법을 포함합니다.

![작업 센터 알림](/help/security/assets/traffic-filter-rules-actions-center-alert.png)


경고 속성(현재 접두사가 있음) *실험* 기능은 아직 릴리스되지 않았으므로 모든 작업 유형(허용, 블록, 로그)의 작업 노드에 적용할 수 있습니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
          experimental_alert: true
```

## CDN 로그 {#cdn-logs}

AEM as a Cloud Service에서 제공하는 CDN 로그 액세스는 캐시 적중률 최적화, 트래픽 필터 규칙 구성을 포함한 사용 사례에 유용합니다. CDN 로그는 Cloud Manager에서 작성자 또는 게시 서비스를 선택할 때 **로그 다운로드** 대화 상자에 나타납니다.

CDN 로그는 최대 5분까지 지연될 수 있습니다.

`rules` 속성은 일치되는 트래픽 필터 규칙에 대해 설명하고 패턴은 다음과 같습니다.

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

예:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

규칙은 다음의 방식으로 진행됩니다.

* 고객이 선언한 일치하는 모든 규칙의 이름이 `match` 속성에 나열됩니다.
* `action` 속성은 규칙이 차단, 허용 또는 로깅에 영향을 주었는지 여부를 결정합니다.
* WAF에 라이선스가 부여되어 WAF가 활성화되면 `waf` 속성은 규칙에서의 WAF 플래그 나열 여부에 관계없이 감지된 모든 WAF 플래그(예: SQLI)을 나열합니다. 이는 선언할 수 있는 새로운 규칙에 대한 인사이트를 제공하기 위함입니다.
* 일치하는 고객이 선언한 규칙과 WAF 규칙이 없는 경우 `rules` 속성이 비어 있습니다.

앞서 설명한 것처럼 WAF 규칙 일치는 히트가 아닌 CDN 실패 및 통과에 대한 CDN 로그에만 나타납니다.

아래 예에서는 샘플 `cdn.yaml`과 로그 항목 두 개를 보여 줍니다.


```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS ]
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/block-me",
"method": "GET",
"res_ctype": "",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=path-rule,action=blocked"
}
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"rid": "974e67f6",
"host": "example.com",
"url": "/?sqli=%27%29%20UNION%20ALL%20SELECT%20NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL--%20fAPK",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

### 로그 형식 {#cdn-log-format}

다음은 CDN 로그에 사용되는 필드 이름 목록과 간단한 설명입니다.

| **필드 이름** | **설명** |
|---|---|
| *timestamp* | TLS 종료 후에 요청이 시작된 시간입니다. |
| *ttfb* | *Time To First Byte(첫 번째 바이트까지의 시간)*&#x200B;의 약어입니다. 요청이 시작된 후 응답 본문의 스트리밍이 시작되기까지의 시간 간격입니다. |
| *cli_ip* | 클라이언트 IP 주소입니다. |
| *cli_country* | 클라이언트 국가의 2글자 [ISO 3166-1](https://en.wikipedia.org/wiki/kr/ISO_3166-1) Alpha-2 국가 코드입니다. |
| *rid* | 요청을 고유하게 식별하는 데 사용되는 요청 헤더의 값입니다. |
| *req_ua* | 해당 HTTP 요청을 담당하는 사용자 에이전트입니다. |
| *host* | 요청이 의도한 대상 기관입니다. |
| *url* | 쿼리 매개변수를 포함한 전체 경로입니다. |
| *메서드* | “GET” 또는 “POST”와 같은 클라이언트에서 전송한 HTTP 메서드입니다. |
| *res_ctype* | 리소스의 원래 미디어 유형을 나타내는 데 사용되는 콘텐츠 유형입니다. |
| *cache* | 캐시의 상태입니다. 가능한 값은 HIT, MISS 또는 PASS입니다. |
| *상태* | HTTP 상태 코드입니다(정수 값). |
| *res_age* | 모든 노드에서 응답이 캐시되는 데 소요되는 시간(초)입니다. |
| *pop* | CDN 캐시 서버의 데이터센터입니다. |
| *rules* | 일치하는 모든 규칙의 이름입니다.<br><br>또한 일치에 따라 차단되었는지 여부도 나타냅니다. <br><br>예: “`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`”<br><br>일치하는 규칙이 없으면 비어 있습니다. |

## 대시보드 도구 {#dashboard-tooling}

Adobe는 Cloud Manager를 통해 다운로드한 CDN 로그를 수집하기 위해 대시보드 도구를 컴퓨터에 다운로드하는 메커니즘을 제공합니다. 이 도구를 사용하여 트래픽을 분석하면 WAF 규칙을 포함하여 선언할 적절한 트래픽 필터 규칙을 구상할 수 있습니다.

[AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) Github 저장소에서 바로 대시보드 도구를 복제할 수 있습니다.

대시보드 도구 사용법에 대한 구체적인 지침은 [튜토리얼](#tutorial)을 참조하십시오.

## 권장 스타터 규칙 {#recommended-starter-rules}

아래 권장 규칙을 시작하려는 `cdn.yaml`에 복사할 수 있습니다. 로그 모드에서 시작하여 트래픽을 분석한 다음 결과에 만족하면 차단 모드로 변경하십시오. 웹 사이트 라이브 트래픽의 고유 특성에 따라 규칙을 수정할 수 있습니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds 100 req/sec on a time window of 1sec
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 100
        window: 1
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    # Block requests coming from OFAC countries
    - name: block-ofac-countries
      when:
        allOf:
          - { reqProperty: tier, equals: publish }
          - reqProperty: clientCountry
            in:
              - SY
              - BY
              - MM
              - KP
              - IQ
              - CD
              - SD
              - IR
              - LR
              - ZW
              - CU
              - CI
      action: log
    # Enable recommended WAF protections (only works if WAF is licensed enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        matches: "author|publish"
      action:
        type: log
        wafFlags:
          - SANS
          - TORNODE
          - NOUA
          - SCANNER
          - USERAGENT
          - PRIVATEFILE
          - ABNORMALPATH
          - TRAVERSAL
          - NULLBYTE
          - BACKDOOR
          - LOG4J-JNDI
          - SQLI
          - XSS
          - CODEINJECTION
          - CMDEXE
          - NO-CONTENT-TYPE
          - UTF8
    # Disable protection against CMDEXE on /bin (only works if WAF is licensed enabled for your environment)
    - name: allow-cdmexe-on-root-bin
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            matches: "^/bin/.*"
      action:
        type: log
        wafFlags:
          - CMDEXE
```

## 튜토리얼 {#tutorial}

[튜토리얼 살펴보기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html)로 트래픽 필터 규칙에 대한 실질적인 지식과 경험을 얻습니다.

튜토리얼은 다음 과정에 대해 소개합니다.

* Cloud Manager 구성 파이프라인 설정
* 도구를 사용하여 악성 트래픽 시뮬레이션
* WAF 규칙이 포함된 트래픽 필터 규칙 선언
* 대시보드 도구를 사용하여 결과 분석
* 모범 사례
