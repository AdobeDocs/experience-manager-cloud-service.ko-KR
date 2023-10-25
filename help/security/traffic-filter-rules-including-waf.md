---
title: WAF 규칙을 포함한 트래픽 필터 규칙
description: WAF(Web Application Firewall) 규칙을 포함한 트래픽 필터 규칙 구성
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: 221f6df73fe660c6f8dbf79affdccdd081ad3906
workflow-type: tm+mt
source-wordcount: '4210'
ht-degree: 43%

---


# WAF 규칙을 포함한 트래픽 필터 규칙 {#traffic-filter-rules-including-waf-rules}

>[!NOTE]
>
>이 기능은 아직 일반적으로 사용할 수 없습니다. 진행 중인 얼리 어답터 프로그램에 참여하려면 이메일 **aemcs-waf-adopter@adobe.com**&#x200B;으로 귀사 조직의 이름과 해당 기능에 가지고 있는 관심에 대한 맥락을 작성하여 보내 주십시오.

트래픽 필터 규칙을 사용하여 CDN 계층에서 요청을 차단하거나 허용할 수 있으며, 이는 다음과 같은 시나리오에서 유용할 수 있습니다.

* 새 사이트가 가동되기 전에 특정 도메인에 대한 액세스를 내부 회사 트래픽으로 제한
* 체적 DDoS 공격에 덜 취약하도록 비율 제한 설정
* 악의적인 것으로 알려진 IP 주소가 페이지를 타겟팅하지 못하도록 방지

이러한 트래픽 필터 규칙 중 일부는 모든 AEM as a Cloud Service Sites 및 Forms 고객이 사용할 수 있습니다. 주로 IP, 호스트 이름, 경로 및 사용자 에이전트를 포함한 요청 속성 및 요청 헤더에서 작동합니다.

트래픽 필터 규칙의 하위 범주는 Enhanced Security 라이센스 또는 WAF-DDoS Protection Security 라이센스가 필요합니다. 이러한 강력한 규칙은 WAF(Web Application Firewall) 트래픽 필터 규칙(또는 WAF 규칙)이라고 하며 [플래그](#waf-flags-list) 이 문서의 뒷부분에 설명되어 있습니다. Sites 및 Forms 고객은 이 고급 기능의 라이선스에 대한 자세한 내용을 Adobe 계정 팀에 문의할 수 있습니다.

트래픽 필터 규칙은 Cloud Manager 구성 파이프라인을 통해 프로덕션(샌드박스가 아닌) 프로그램의 개발, 스테이지 및 프로덕션 환경 유형에 배포할 수 있습니다. RDE에 대한 지원은 향후에 제공될 것입니다.

## 이 문서 구성 방법 {#how-organized}

이 문서는 다음 섹션으로 구성됩니다.

* **트래픽 보호 개요:** 악성 트래픽으로부터 보호하는 방법을 알아봅니다.
* **규칙 구성을 위한 제안 프로세스:** 웹 사이트를 보호하기 위한 높은 수준의 방법론에 대해 읽어 보십시오.
* **설정:** 고급 WAF 규칙을 포함한 트래픽 필터 규칙을 설정, 구성 및 배포하는 방법에 대해 알아봅니다.
* **규칙 구문:** 에서 트래픽 필터 규칙을 선언하는 방법을 참조하십시오. `cdn.yaml` 구성 파일입니다. 여기에는 모든 Sites 및 Forms 고객이 사용할 수 있는 트래픽 필터 규칙과 해당 기능에 라이선스를 부여한 사용자를 위한 WAF 규칙의 하위 범주가 모두 포함됩니다.
* **규칙 예:** 시작하는 데 도움이 되는 선언된 규칙의 예를 참조하십시오.
* **비율 제한 규칙:** 속도 제한 규칙을 사용하여 사이트를 대량 공격으로부터 보호하는 방법에 대해 알아봅니다.
* **CDN 로그:** 선언된 규칙 및 WAF 플래그가 트래픽과 일치하는 항목을 확인합니다.
* **대시보드 도구:** CDN 로그를 분석하여 새로운 트래픽 필터 규칙을 제안합니다.
* **자습서:** 대시보드 도구 를 사용하여 올바른 규칙을 선언하는 방법을 포함하여 이 기능에 대한 실용적인 지식입니다.
<!-- About the tutorial: sets the context for a linked tutorial, which gives you practical knowledge about the feature, including how to use dashboard tooling to declare the right rules. -->

## 트래픽 보호 개요 {#traffic-protection-overview}

현재 디지털 환경에서 악의적인 트래픽은 항상 존재하는 위협입니다. Dell은 위험의 심각성을 인식하고 고객 애플리케이션을 보호하고 공격 발생 시 이를 완화할 수 있는 몇 가지 접근 방식을 제공합니다.

가장자리에서 Adobe 관리 CDN은 플러드 및 반사/증폭 공격을 포함하여 네트워크 레이어(레이어 3 및 4)의 DDoS 공격을 흡수합니다.

기본적으로 Adobe은 특정 임계값을 초과하는 예기치 않게 높은 트래픽의 버스트로 인한 성능 저하를 방지하기 위해 조치를 취합니다. 사이트 가용성에 영향을 미치는 DDoS 공격이 발생하면 Adobe 운영팀에 경고가 표시되고 이를 완화하기 위한 조치를 취합니다.

고객은 컨텐츠 전달 흐름의 다양한 계층에서 규칙을 구성하여 애플리케이션 계층 공격(레이어 7)을 완화하기 위한 사전 조치를 취할 수 있습니다.

예를 들어 Apache 계층에서 고객은 다음 중 하나를 구성할 수 있습니다. [dispatcher 모듈](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#configuring-access-to-content-filter) 또는 [ModSecurity](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection.html?lang=en) 특정 콘텐츠에 대한 액세스를 제한합니다.

또한 이 문서에서 설명하는 바와 같이 트래픽 필터 규칙은 Cloud Manager의 구성 파이프라인을 사용하여 CDN에 배포할 수 있습니다. IP 주소, 경로 및 헤더와 같은 속성을 기반으로 하는 트래픽 요청 기반 트래픽 필터 규칙 외에도 고객은 WAF 규칙이라고 하는 강력한 하위 범주의 트래픽 필터 규칙에 라이선스를 부여할 수 있습니다.

## 제안된 프로세스 {#suggested-process}

다음은 올바른 트래픽 필터 규칙을 제안하기 위한 높은 수준의 권장 종단 간 프로세스입니다.

1. 에 설명된 대로 비프로덕션 및 프로덕션 구성 파이프라인을 구성합니다. [설정](#setup) 섹션.
1. WAF 트래픽 필터 규칙의 하위 범주에 라이선스를 부여한 고객은 Cloud Manager에서 해당 라이선스를 활성화해야 합니다.
1. 라이선스가 부여된 경우 WAF 규칙을 비롯한 트래픽 필터 규칙을 사용하는 방법을 구체적으로 이해하려면 자습서를 읽고 시도해 보십시오. 이 자습서에서는 개발 환경에 규칙 배포, 악성 트래픽 시뮬레이션 및 [CDN 로그](#cdn-logs), 및 분석 [대시보드 도구](#dashboard-tooling).
1. 권장되는 초기 규칙을 복사할 위치: `cdn.yaml` 및 구성을 로그 모드에서 프로덕션에 배포합니다.
1. 일부 트래픽을 수집한 후 다음을 사용하여 결과를 분석합니다. [대시보드 도구](#dashboard-tooling) 일치하는 항목이 있는지 확인합니다. 긍정 오류(false positive)를 검색하고 필요한 조정을 수행하여 궁극적으로 블록 모드에서 기본 규칙을 활성화합니다.
1. CDN 로그 분석에 따라 사용자 정의 규칙을 추가하고, 개발 환경에서 시뮬레이션된 트래픽으로 먼저 테스트한 후 로그 모드에서 스테이지 및 프로덕션에 배포하고 차단 모드로 배포합니다.
1. 지속적으로 트래픽을 모니터링하여 위협 환경이 발전함에 따라 규칙을 변경합니다.

## 설정 {#setup}

1. 먼저 Git의 프로젝트에서 다음 폴더 및 파일 구조를 만들고 최상위 수준 폴더를 만듭니다.

   ```
   config/
        cdn.yaml
   ```

1. `cdn.yaml` 메타데이터와 트래픽 필터 규칙 및 WAF 규칙 목록을 포함해야 합니다.

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

다음 `kind` 매개 변수는 다음으로 설정해야 합니다. `CDN` 및 버전은 현재 인 스키마 버전으로 설정해야 합니다. `1`. 아래 추가 예를 참조하십시오.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. WAF 규칙을 구성하려면 신규 및 기존 프로그램 시나리오 모두에 대해 아래에 설명된 대로 Cloud Manager에서 WAF를 활성화해야 합니다. WAF용으로 별도의 라이선스를 구매해야 합니다.

   1. 새 프로그램에서 WAF를 구성하려면 **WAF-DDOS 보호** 의 확인란 **보안** 다음을 수행할 때 탭 [프로덕션 프로그램을 추가합니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

   1. 기존 프로그램에서 WAF를 구성하려면 [프로그램 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) 및 **보안** 탭 선택 취소 또는 확인 **WAF-DOS** 언제든지 옵션을 선택할 수 있습니다.

1. RDE 이외의 환경 유형의 경우 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 생성합니다.

   * [프로덕션 파이프라인에 대해서는 이 문서 를 참조하십시오.](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [비프로덕션 파이프라인에 대해서는 이 문서 를 참조하십시오.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

RDE의 경우 명령이 사용되지만 RDE는 현재 지원되지 않습니다.

## 트래픽 필터 규칙 구문 {#rules-syntax}

IPS, 사용자 에이전트, 요청 헤더, 호스트 이름, 지역 및 URL과 같은 패턴을 일치하도록 `traffic filter rules`을 구성할 수 있습니다.

향상된 보안 또는 WAF-DDoS 보호 보안 서비스 라이센스를 얻은 고객은 `WAF traffic filter rules` 하나 이상을 참조하는 (또는 WAF 규칙) [플래그](#waf-flags-list).

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

의 트래픽 필터 규칙 형식 `cdn.yaml` 파일은 아래에 설명되어 있습니다. 몇 가지 보기 [기타 예](#examples) 의 별도 섹션과 이후 섹션에서 [비율 제한 규칙](#rate-limit-rules).


| **속성** | **대부분의 트래픽 필터 규칙** | **WAF 트래픽 필터 규칙** | **유형** | **기본 값** | **설명** |
|---|---|---|---|---|---|
| 이름 | X | X | `string` | - | 규칙 이름(64자 길이, 영숫자 및 - 만 포함할 수 있음) |
| when | X | X | `Condition` | - | 기본 구조는 다음과 같습니다.<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[getter, 조건자 및 여러 조건을 결합하는 방법을 설명하는 아래의 조건 구조 구문을 참조하십시오.](#condition-structure) |
| action | X | X | `Action` | 로그 | log, allow, block, log 또는 action 오브젝트 기본값은 로그입니다. |
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
| reqProperty | `string` | 요청 속성입니다.<br><br>다음 중 하나입니다. `path`, `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>도메인 속성은 요청의 호스트 헤더를 소문자로 변환한 것입니다. 문자열을 비교할 때 유용합니다. 즉, 대소문자 구분으로 인해 일치 항목이 누락되는 일이 없습니다.<br><br>`clientCountry`는 [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol)에 표시된 두 개의 문자 코드를 사용합니다. |
| reqHeader | `string` | 지정된 이름의 요청 헤더를 반환합니다. |
| queryParam | `string` | 지정된 이름의 쿼리 매개변수를 반환합니다. |
| reqCookie | `string` | 지정된 이름의 쿠키를 반환합니다. |
| postParam | `string` | 본문에서 지정된 이름의 매개 변수를 반환합니다. 본문이 컨텐츠 유형인 경우에만 작동합니다. `application/x-www-form-urlencoded` |

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
| **존재함** | `boolean` | true로 설정되어 있고 속성이 있는 경우 또는 false로 설정되어 있고 속성이 없는 경우 true |

### 액션 구조 {#action-structure}

액션 유형(allow, block, log)을 지정하고 다른 모든 옵션에 기본값을 가정하는 문자열이거나 `type` 필수 필드를 통해 해당 유형에 적용되는 다른 옵션과 함께 규칙 유형을 정의하는 오브젝트일 수 있는 `action` 필드로 지정합니다.

**액션 유형**

액션의 실행 순서를 반영하도록 정렬되어 있는 다음 표의 액션 유형에 따라 액션의 우선순위를 지정합니다.

| **이름** | **허용된 속성** | **의미** |
|---|---|---|
| **허용** | `wafFlags` (옵션) | wafFlags가 없으면 추가 규칙 처리를 중지하고 응답 제공을 진행합니다. wafFlags가 있으면 지정된 WAF 보호를 비활성화하고 추가 규칙 처리를 진행합니다. |
| **블록** | `status, wafFlags` (옵션이면 상호 배타적) | wafFlags가 없으면 다른 모든 속성을 무시하는 HTTP 오류를 반환하고, 상태 속성으로 오류 코드를 정의하거나 406을 기본으로 표시합니다. wafFlags가 있으면 지정된 WAF 보호를 활성화하고 추가 규칙 처리를 진행합니다. |
| **로그** | `wafFlags` (옵션) | 규칙이 트리거되었다는 사실을 로그 기록하지 않으면 처리에 영향을 주지 않습니다. wafFlags는 영향을 주지 않음 |

### WAF 플래그 목록 {#waf-flags-list}

다음 `wafFlags` 라이센스 가능한 WAF 트래픽 필터 규칙에서 사용할 수 있는 속성은 다음을 참조할 수 있습니다.

| **플래그 ID** | **플래그 이름** | **설명** |
|---|---|---|
| SQLI | SQL 주입 | SQL 주입은 임의의 데이터베이스 쿼리를 실행하여 애플리케이션에 대한 액세스 권한을 얻거나 권한 있는 정보를 얻으려는 시도입니다. |
| BACKDOOR | 백도어 | 백도어 신호는 일반적인 백도어 파일이 시스템에 있는지 확인하려고 시도하는 요청입니다. |
| CMDEXE | 명령 실행 | 명령 실행은 사용자 입력을 통해 임의의 시스템 명령으로 대상 시스템을 제어하거나 손상시키려는 시도입니다. |
| XSS | 크로스 사이트 스크립팅 | 크로스 사이트 스크립팅은 악성 JavaScript 코드를 통해 사용자의 계정이나 웹 탐색 세션을 하이재킹하려는 시도입니다. |
| TRAVERSAL | 디렉터리 순회 | 디렉터리 순회는 민감한 정보를 얻기 위해 시스템 전체에서 권한 있는 폴더를 탐색하려는 시도입니다. |
| USERAGENT | 공격 툴링 | 공격 툴링은 자동화된 소프트웨어를 사용하여 보안 취약성을 식별하거나 발견된 취약성을 악용하려고 시도하는 것입니다. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI 공격은 2.16.0 이전 Log4J 버전에 있는 [Log4Shell 취약점](https://en.wikipedia.org/wiki/Log4Shell)을 활용하려고 시도합니다. |
| BHH | 잘못된 홉 헤더 | 잘못된 홉 헤더는 잘못된 형식의 TE(Transfer-Encoding) 또는 CL(Content-Length) 헤더나 올바른 형식의 TE 및 CL 헤더를 통한 HTTP 스머글링 시도를 나타냅니다. |
| ABNORMALPATH | 비정상 경로 | 비정상 경로는 원래 경로가 정규화된 경로와 다름을 나타냅니다(예: `/foo/./bar`는 `/foo/bar`로 정규화됨). |
| DOUBLEENCODING | 이중 인코딩 | 이중 인코딩은 html 문자를 이중 인코딩하는 회피 기술을 확인합니다. |
| NOTUTF8 | 잘못된 인코딩 | 잘못된 인코딩으로 인해 서버가 요청의 악성 문자를 응답으로 변환하여 서비스 거부 또는 XSS가 발생할 수 있습니다. |
| JSON-ERROR | JSON 인코딩 오류 | “Content-Type” 요청 헤더 내에 JSON을 포함하도록 지정되었지만 JSON 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문입니다. 흔히 프로그래밍 오류나 자동화된 요청 또는 악성 요청과 관련이 있습니다. |
| MALFORMED-DATA | 요청 본문의 형식이 잘못된 데이터 | “Content-Type” 요청 헤더에 따라 형식이 잘못된 POST, PUT 또는 PATCH 요청 본문입니다. 예를 들어 “Content-Type: application/x-www-form-urlencoded” 요청 헤더가 지정되고 json인 POST 본문을 포함하는 경우입니다. 흔히 프로그래밍 오류, 자동화된 요청 또는 악성 요청에 해당합니다. 에이전트 3.2 이상이 필요합니다. |
| SANS | 악성 IP 트래픽 | 악성 활동에 연루된 것으로 보고된 [SANS 인터넷 스톰 센터](https://isc.sans.edu/) IP 주소 목록입니다. |
| SIGSCI-IP | 네트워크 효과 | SignalSciences에서 플래그 지정한 IP: 결정 엔진의 악성 신호로 인해 IP가 플래그 지정될 때마다 해당 IP가 모든 고객에게 전파됩니다. 플래그 기간 동안 추가 신호를 포함하는 해당 IP 주소의 후속 요청이 기록됩니다. |
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

## 규칙 예 {#examples}

몇 가지 규칙 예는 다음과 같습니다. 다음을 참조하십시오. [요금 제한 섹션](#rules-with-rate-limits) 등급 제한 규칙의 예는 더 아래에 있습니다.

**예 1**

다음 규칙은 IP 192.168.1.1에서 오는 요청을 차단합니다.

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

이 규칙은 경로 요청을 차단합니다. `/block-me`및 가 와(과) 일치하는 모든 요청을 차단함 `SQLI` 또는 `XSS` 패턴. 이 예에는 다음을 참조하는 WAF 트래픽 필터 규칙이 포함되어 있습니다. `SQLI` 및 `XSS` [플래그](#waf-flags-list): 별도의 라이센스가 필요합니다.

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

## 비율 제한 규칙 {#rate-limits-rules}

시간 경과에 따라 일치가 특정 속도를 초과하는 경우에만 규칙과 일치하는 트래픽을 차단하는 것이 바람직한 경우가 있습니다. `rateLimit` 속성의 값을 설정하면 규칙 조건과 일치하는 요청의 속도가 제한됩니다.

속도 제한 규칙은 WAF 플래그를 참조할 수 없습니다. 모든 Sites 및 Forms 고객이 사용할 수 있습니다.

### rateLimit 구조 {#ratelimit-structure}

| **속성** | **유형** | **기본값** | **의미** |
|---|---|---|---|
| limit | 10에서 10000 사이의 정수 | required | 규칙이 트리거되는 요청 비율(CDN POP당)(초당 요청 수)입니다. |
| window | 정수 열거형: 1, 10 또는 60 | 10 | 요청 속도를 계산하는 샘플링 기간(초). |
| penalty | 60에서 3600 사이의 정수 | 300(5분) | 일치하는 요청이 차단되는 기간(초 단위로 반올림). |
| groupBy | 배열[getter] | 없음 | 처리율 제한 장치 카운터는 요청 속성 세트(예: clientIp)로 집계됩니다. |

### 예 {#ratelimiting-examples}

**예 1**

이 규칙은 지난 60초 동안 100req/sec(CDN POP당)를 초과하는 경우 5m 동안 클라이언트를 차단합니다.

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

지난 60초 동안 100req/sec(CDN POP당)를 초과하는 경우 경로/중요/리소스의 60초 차단 요청:

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

## CDN 로그 {#cdn-logs}

AEM as a Cloud Service에서 제공하는 CDN 로그 액세스는 캐시 적중률 최적화, CDN 및 WAF 규칙 구성을 포함한 사용 사례에 유용합니다. CDN 로그는 Cloud Manager에서 작성자 또는 게시 서비스를 선택할 때 **로그 다운로드** 대화 상자에 나타납니다.

CDN 로그가 최대 5분 지연될 수 있습니다.

다음 `rules` 속성은 일치하는 트래픽 필터 규칙을 설명하며 다음 패턴을 포함합니다.

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

예:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

규칙은 다음의 방식으로 진행됩니다.

* 일치하는 규칙의 고객이 선언한 규칙 이름이 matches 속성에 나열됩니다.
* 작업 속성은 규칙이 차단, 허용 또는 로깅의 영향을 미쳤는지 여부를 설명합니다.
* WAF에 라이센스가 부여되고 활성화되어 있으면 구성에 waf 규칙이 나열되었는지 여부에 관계없이 waf 속성은 감지된 모든 waf 규칙(예: SQLI; 고객이 선언한 이름과 독립적임)을 나열합니다.
* 고객이 선언한 규칙이 일치하지 않고 waf 규칙이 일치하지 않으면 규칙 속성 속성이 비어 있습니다.

일반적으로 일치하는 규칙은 CDN 적중, 통과 또는 실패 여부에 관계없이 CDN에 대한 모든 요청의 로그 항목에 나타납니다. 단, WAF 규칙은 CDN 적중이 아니라 CDN 실패 또는 통과로 간주되는 CDN 요청에 대해서만 로그 항목에 나타납니다.

아래 예제는 샘플을 보여 줍니다 `cdn.yaml` 및 두 개의 CDN 로그 항목:


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
| *timestamp* | TLS 종료 후 요청이 시작된 시간입니다.. |
| *ttfb* | *Time To First Byte(첫 번째 바이트까지의 시간)*&#x200B;의 약어입니다. 요청이 시작된 후 응답 본문의 스트리밍이 시작되기까지의 시간 간격입니다. |
| *cli_ip* | 클라이언트 IP 주소입니다. |
| *cli_country* | 클라이언트 국가의 2글자 [ISO 3166-1](https://en.wikipedia.org/wiki/ISO_3166-1) Alpha-2 국가 코드입니다. |
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

Adobe은 Cloud Manager를 통해 다운로드한 CDN 로그를 수집하기 위해 컴퓨터에 대시보드 도구를 다운로드하는 메커니즘을 제공합니다. 이 도구를 사용하면 트래픽을 분석하여 WAF 규칙을 포함하여 선언할 적절한 트래픽 필터 규칙을 마련할 수 있습니다.

대시보드 도구는 다음에서 직접 복제할 수 있습니다. [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) Github 리포지토리.

[튜토리얼 보기](#tutorial) 대시보드 도구 사용 방법에 대한 구체적인 지침

## 튜토리얼 {#tutorial}

Adobe은 Cloud Manager를 통해 다운로드한 CDN 로그를 수집하기 위해 컴퓨터에 대시보드 도구를 다운로드하는 메커니즘을 제공합니다. 이 도구를 사용하면 트래픽을 분석하여 WAF 규칙을 포함하여 선언할 적절한 트래픽 필터 규칙을 마련할 수 있습니다. 이 섹션에서는 먼저 개발 환경의 대시보드 도구에 익숙해지도록 한 다음 해당 지식을 활용하여 프로덕션 환경에서 규칙을 만드는 방법에 대한 지침을 제공합니다.

대시보드 도구는 다음에서 직접 복제할 수 있습니다. [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) GitHub 리포지토리.


### 대시보드 도구 이해하기 {#dashboard-getting-familiar}

1. 개발 환경과 연결된 Cloud Manager 비프로덕션 구성 파이프라인을 만듭니다. 먼저 **배포 파이프라인** 옵션을 선택합니다. 그런 다음 을 선택합니다 **타깃팅된 배포**, Config, 리포지토리 및 git 분기를 실행하고 코드 위치를 /config로 설정합니다.

   ![비프로덕션 파이프라인 선택 배포 추가](/help/security/assets/waf-select-pipeline1.png)

   ![비프로덕션 파이프라인 추가 타깃팅 선택](/help/security/assets/waf-select-pipeline2.png)

[비프로덕션 파이프라인 설정에 대한 자세한 내용은 이 문서 를 참조하십시오.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

1. 작업 영역에서 루트 수준에서 폴더 구성을 만들고 이라는 파일을 추가합니다 `cdn.yaml`를 사용하여 간단한 규칙을 선언하고 차단 모드가 아닌 로그 모드로 설정합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    # Log request on simple path
    - name: log-rule-example
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            equals: '/log/me'
      action: log
```

1. 구성 파이프라인을 사용하여 변경 사항을 커밋 및 푸시하고 구성을 배포합니다.

   ![구성 파이프라인 실행](/help/security/assets/waf-run-pipeline.png)

1. 구성이 배포되면 액세스를 시도합니다. `https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me` 웹 브라우저나 아래의 curl 명령 사용. 해당 페이지가 존재하지 않으므로 404 오류 페이지가 표시됩니다.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Cloud Manager에서 CDN 로그를 다운로드하고 규칙 속성이 규칙 이름과 일치하면서 규칙이 예상대로 일치하는지 확인합니다.

   ```
   "rules": "match=log-rule-example"
   ```

   ![로그 다운로드 를 선택합니다](/help/security/assets/waf-download-logs1.png)

   ![로그 다운로드](/help/security/assets/waf-download-logs2.png)

1. 대시보드 도구를 사용하여 도커 이미지를 로드하고 추가 정보를 따라 CDN 로그를 수집합니다. 다음 스크린샷에 표시된 대로 올바른 기간, 올바른 환경 및 올바른 필터를 선택합니다.

   ![대시보드에서 시간 선택](/help/security/assets/dashboard-select-time.png)

   ![대시보드에서 환경 선택](/help/security/assets/dashboard-select-env.png)

1. 올바른 필터가 적용되면 예상 데이터가 로드된 대시보드를 볼 수 있습니다. 아래 스크린샷에서는 아일랜드에 있는 동일한 IP가 웹 브라우저와 curl을 사용하여 지난 2시간 동안 규칙 로그 규칙 예가 3번 트리거되었습니다.

   ![개발 대시보드 데이터 보기](/help/security/assets/dashboard-see-data-logmode.png)
   ![개발 대시보드 데이터 위젯 보기](/help/security/assets/dashboard-see-data-logmode2.png)

1. 이제 cdn.yaml 를 변경하여 예상대로 페이지가 차단되도록 규칙을 차단 모드로 전환합니다. 그런 다음 앞에서 수행한 대로 구성 파이프라인을 커밋, 푸시 및 트리거합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    # Log request on simple path
    - name: log-rule-example
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            equals: '/log/me'
      action: block
```

1. 구성이 배포되면 액세스를 시도합니다. `https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me` 웹 브라우저나 아래의 curl 명령 사용. 요청이 차단되었음을 나타내는 406 오류 페이지가 표시됩니다.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. 다시 한 번 Cloud Manager에서 CDN 로그를 다운로드하고(참고: CDN 로그에 새 요청이 노출되는 데 최대 5분이 소요될 수 있음) 이전에 수행한 대로 대시보드 도구에서 가져오십시오. 완료되면 대시보드를 새로 고칩니다. 아래 스크린샷에서 볼 수 있듯이 `/log/me` 은(는) 규칙에 의해 차단됩니다.

   ![제품 대시보드 데이터 보기](/help/security/assets/dashboard-see-data-blockmode.png)
   ![제품 대시보드 데이터 보기](/help/security/assets/dashboard-see-data-blockmode2.png)

1. WAF 트래픽 필터를 활성화한 경우(기능이 GA인 경우 추가 라이선스가 필요), 로그 모드에서 WAF 트래픽 필터 규칙을 반복하고 규칙을 배포합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: log-waf-flags
        when:
          reqProperty: tier
          matches: "author|publish"
        action:
          type: log
          wafFlags:
              - SANS
              - SIGSCI-IP
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
```

1. 다음과 같은 도구 사용 [니토](https://github.com/sullo/nikto/tree/master) 일치하는 요청을 생성합니다. 아래 명령은 1분 이내에 약 550개의 악의적인 요청을 전송합니다.

   ```
   ./nikto.pl -useragent "MyAgent (Demo/1.0)" -D V -Tuning 9 -ssl -h https://publish-pXXXXX-eYYYYY.adobeaemcloud.com
   ```

1. Cloud Manager에서 CDN 로그를 다운로드하고(표시되는 데 최대 5분이 소요될 수 있음) 일치하는 선언된 규칙과 WAF 플래그가 모두 표시되는지 확인합니다.

   보다시피, Nikto에 의해 생성된 여러 요청은 WAF에 의해 악의적인 것으로 플래그가 지정되었습니다. 우리는 Nikto가 CMDEXE, SQLI 및 NULLBYTE 취약성을 악용하려고 시도했음을 알 수 있다. 이제 작업을 로그에서 차단으로 변경하고 Nikto를 사용하여 검사를 다시 트리거하면 이전에 플래그가 지정된 모든 요청이 이번에 차단됩니다.

   ![WAF 데이터 보기](/help/security/assets/dashboard-see-data-waf.png)


   요청이 WAF 플래그와 일치할 때마다 선언된 규칙의 일부가 아니더라도 해당 WAF 플래그가 표시됩니다. 따라서 일치 규칙을 아직 선언하지 않은 잠재적으로 새로운 악성 트래픽을 항상 알 수 있습니다. 예:

   ```
   "rules": "match=log-waf-flags,waf=SQLI,action=blocked"
   ```

1. 로그 모드에서 속도 제한을 사용하는 규칙을 사용하여 반복합니다. 구성 파이프라인을 커밋, 푸시 및 트리거하여 구성을 적용합니다.

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
          limit: 10
          window: 1
          penalty: 60
          groupBy:
            - reqProperty: clientIp
        action: log
```

1. 다음과 같은 도구 사용 [Vegeta](https://github.com/tsenart/vegeta) 트래픽을 생성합니다.

   ```
   echo "GET https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com" | vegeta attack -duration=5s | tee results.bin | vegeta report
   ```

1. 도구를 실행한 후 CDN 로그를 다운로드하고 대시보드에서 수집하여 속도 제한 규칙이 트리거되었는지 확인할 수 있습니다

   ![WAF 데이터 보기](/help/security/assets/waf-dashboard-ratelimiter-1.png)

   ![WAF 데이터 보기](/help/security/assets/waf-dashboard-ratelimiter-2.png)

   보시다시피 **limit-requests-client-ip** 이(가) 트리거되었습니다.

   트래픽 필터 규칙의 작동 방식을 잘 알고 있으므로 프로덕션 환경으로 이동할 수 있습니다.

### 프로덕션 환경에 규칙 배포 {#dashboard-prod-env}

처음에 규칙을 로그 모드로 선언하여 긍정 오류(false positive)가 없는지 확인해야 합니다. 이는 잘못 차단되는 합법적인 트래픽을 의미합니다.

1. 프로덕션 환경과 연결된 프로덕션 구성 파이프라인을 만듭니다.

1. 아래의 권장 규칙을 cdn.yaml에 복사합니다. 웹 사이트의 라이브 트래픽의 고유한 특성을 기반으로 규칙을 수정할 수 있습니다. 구성 파이프라인을 커밋, 푸시 및 트리거합니다. 규칙이 로그 모드에 있는지 확인합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
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
    # Enable recommended WAF protections (only works if WAF is enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        matches: "author|publish"
      action:
        type: log
        wafFlags:
          - SANS
          - SIGSCI-IP
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
    # Disable protection against CMDEXE on /bin
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

1. 인지하고 있을 수 있는 악의적인 트래픽을 차단하기 위해 추가 규칙을 추가합니다. 예를 들어 사이트를 공격하는 특정 IP가 있습니다.

1. 사이트의 트래픽 볼륨에 따라 몇 분, 몇 시간 또는 며칠 후에 Cloud Manager에서 CDN 로그를 다운로드하고 대시보드로 분석합니다.

1. 다음은 몇 가지 고려 사항입니다.
   1. 선언된 규칙과 일치하는 트래픽은 차트와 요청 로그에 표시되므로 선언된 규칙이 트리거되는지 쉽게 확인할 수 있습니다.
   1. 트래픽 일치 WAF 플래그는 규칙에 기록하지 않았더라도 차트 및 요청 로그에 표시됩니다. 따라서 항상 새로운 악성 트래픽을 알고 있으며 필요에 따라 새 규칙을 만들 수 있습니다. 선언된 규칙에 반영되지 않은 WAF 플래그를 보고 선언하는 것이 좋습니다.
   1. 일치하는 규칙의 경우 요청 로그에서 긍정 오류(false positive)를 검사하고 규칙을 필터링할 수 있는지 확인하십시오. 예를 들어 특정 경로에 대해서만 긍정 오류(false positive)일 수 있습니다.

1. 적절한 규칙을 설정하여 차단 모드를 설정하고 추가 규칙을 추가하는 것도 고려하십시오. 더 많은 트래픽으로 더 자세히 분석할 때 일부 규칙은 로그 모드로 유지되어야 합니다.

1. 구성을 다시 배포합니다.

1. 자주 사용하는 기준으로 대시보드를 반복하여 분석합니다.

