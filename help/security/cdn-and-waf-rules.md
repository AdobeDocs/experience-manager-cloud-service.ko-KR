---
title: WAF 규칙을 사용하여 트래픽 필터 규칙 구성
description: WAF 규칙과 함께 트래픽 필터 규칙을 사용하여 트래픽을 필터링합니다
source-git-commit: ce7b6922f92208c06f85afe85818574bf2bc8f6d
workflow-type: tm+mt
source-wordcount: '2709'
ht-degree: 70%

---


# 트래픽을 필터링하기 위해 WAF 규칙으로 트래픽 필터 규칙 구성 {#configuring-cdn-and-waf-rules-to-filter-traffic}

>[!NOTE]
>
>이 기능은 아직 일반적으로 사용할 수 없습니다. 진행 중인 얼리 어답터 프로그램에 참여하려면 이메일 **aemcs-waf-adopter@adobe.com**&#x200B;으로 귀사 조직의 이름과 해당 기능에 가지고 있는 관심에 대한 맥락을 작성하여 보내 주십시오.

Adobe은 고객 웹 사이트에 대한 공격을 완화하려고 하지만, 악성 트래픽이 애플리케이션에 도달하지 않도록 특정 패턴과 일치하는 트래픽을 사전에 필터링하는 것이 유용할 수 있습니다. 가능한 접근법은 다음과 같습니다.

* `mod_security`와 같은 Apache 레이어 모듈
* Cloud Manager의 구성 파이프라인을 통해 CDN에 배포되는 트래픽 필터 규칙 구성

이 문서에서는 트래픽 필터 규칙 접근 방식에 대해 설명합니다. 이러한 규칙은 대부분 IP, 경로 및 사용자 에이전트를 포함한 요청 속성 및 요청 헤더에 따라 요청을 차단하거나 허용합니다. 모든 AEM as a Cloud Service Sites 및 Forms 고객이 이러한 규칙을 구성할 수 있습니다.

WAF(Web Application Firewall) 추가 기능에 라이선스를 부여하는 고객은 &quot;WAF 트래픽 필터 규칙&quot;(또는 줄여서 WAF 규칙)이라는 추가 규칙 범주를 구성할 수도 있습니다. 이러한 WAF 규칙은 악의적인 트래픽과 관련된 것으로 알려진 다양한 패턴과 일치하는 요청을 차단합니다. 예정된 기능의 라이선스에 대한 자세한 내용은 Adobe 계정 팀에 문의하십시오. 얼리 어답터 프로그램 중에는 추가 라이선스가 필요하지 않습니다.

트래픽 필터 규칙은 프로덕션(샌드박스가 아닌) 프로그램의 모든 클라우드 환경 유형(RDE, dev, stage, prod)에 배포할 수 있습니다.

## 설정 {#setup}

1. 먼저 git의 최상위 폴더에 다음 폴더와 파일 구조를 만듭니다.

   ```
   config/
        cdn/
           cdn.yaml
   ```

1. `cdn.yaml` 는 메타데이터와 트래픽 필터 규칙 및 WAF 규칙 목록을 포함해야 합니다.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
         ...
   ```

“kind” 매개변수는 “CDN”으로 설정되어야 하며 버전은 스키마 버전(현재 “1”)으로 설정되어야 합니다. 자세한 내용은 아래 예를 참조하십시오.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. WAF 규칙을 구성하려면 새로운 프로그램 시나리오와 기존 프로그램 시나리오에서 아래에 설명된 대로 Cloud Manager에서 WAF를 활성화해야 합니다. WAF용으로 별도의 라이선스를 구매해야 합니다.

   1. 새 프로그램에서 WAF를 구성하려면 아래와 같이 **보안** 탭의 **WAF-DDOS 보호** 확인란을 선택합니다. 계속해서 [프로덕션 프로그램 추가](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)에 설명된 단계에 따라 프로그램을 만듭니다.

   1. 기존 프로그램에서 WAF를 구성하려면 [프로그램 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) 설명서에 설명된 단계에 따라 **프로그램 편집** 옵션을 선택합니다. 그런 다음 마법사의 **보안** 탭에서 언제든지 WAF-DDOS 옵션을 선택 취소하거나 선택할 수 있습니다.

1. RDE 이외의 환경 유형의 경우 Cloud Manager 구성 파이프라인을 실행합니다. 이 파이프라인은 아래 설명된 대로 구성할 수 있습니다.

   1. Cloud Manager 홈 페이지의 파이프라인 카드에서 **프로덕션 파이프라인 추가** 또는 **비프로덕션 파이프라인 추가**&#x200B;를 선택하여 파이프라인 추가 마법사를 시작합니다.
   1. 구성 탭에서 **배포 파이프라인**&#x200B;을 선택합니다.

      ![배포 파이프라인 옵션 선택](/help/security/assets/deployment.png)

   1. 파이프라인에 이름을 지정하고 배포 트리거를 선택한 다음 **계속**&#x200B;을 선택합니다.
   1. **소스 코드** 탭에서 **타겟팅 배포**&#x200B;를 선택한 다음 **구성**&#x200B;을 선택합니다.

      ![타깃팅된 배포 선택](/help/security/assets/target-deployment.png)

   1. 필요에 따라 저장소와 분기를 선택합니다. 선택한 환경에 대한 구성 파이프라인이 있는 경우, 이 선택이 비활성화됩니다.

      ![구성 파이프라인 개요](/help/security/assets/config-pipeline.png)

      >[!NOTE]
      >
      > 이러한 파이프라인을 구성하거나 실행하려면 사용자가 배포 관리자로 로그인해야 합니다.
      > 또한 환경당 하나의 구성 파이프라인만 구성하고 실행할 수 있습니다.

   1. **저장**&#x200B;을 선택합니다. 새 파이프라인이 파이프라인 카드에 표시되며, 준비가 되면 실행할 수 있습니다.
   1. RDE의 경우 명령줄이 사용되지만 지금은 RDE가 지원되지 않습니다.

## 트래픽 필터 규칙 구문 {#rules-syntax}

다음을 구성할 수 있습니다. `traffic filter rules` IP, 사용자 에이전트, 요청 헤더, 호스트 이름, 지역 및 url과 같은 패턴을 일치시키십시오.

WAF 오퍼링에 라이선스를 부여하는 고객은 라는 특별한 카테고리의 트래픽 필터 규칙을 구성할 수도 있습니다. `WAF traffic filter rules` 하나 이상의 WAF 플래그를 참조하는 (또는 WAF 규칙은 줄임). 이 플래그는 아래 섹션에 나열되어 있습니다.

다음은 WAF 규칙을 포함하는 트래픽 필터 규칙 세트의 예입니다.

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

cdn.yaml 파일의 트래픽 필터 규칙 형식은 아래에 설명되어 있습니다. 이후 섹션에서 몇 가지 예를 참조하십시오.


| **속성** | **대부분의 트래픽 필터 규칙** | **WAF 트래픽 필터 규칙** | **유형** | **기본 값** | **설명** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | 규칙 이름(64자 길이, 영숫자 및 - 만 포함할 수 있음) |
| when | X | X | `Condition` | - | 기본 구조는 다음과 같습니다.<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>getter, 조건자 및 여러 조건을 결합하는 방법을 설명하는 아래의 조건 구조 구문을 참조하십시오. |
| action | X | X | `Action` | log | log, allow, block, log 또는 action object 기본값은 log입니다. |
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
| cookie | `string` | 지정된 이름의 쿠키를 반환합니다. |

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

### 작업 구조 {#action-structure}

다음에 의해 지정됨 `action` 작업 유형(허용, 블록, 로그)을 지정하고 다른 모든 옵션의 기본값을 가정하거나 을 통해 규칙 유형이 정의된 개체를 사용할 수 있는 필드입니다. `type` 해당 유형에 적용할 수 있는 기타 옵션과 함께 필수 필드입니다.

**작업 유형**

작업은 다음 표의 유형에 따라 우선 순위가 매겨지며, 실행 순서를 반영하도록 순서가 지정됩니다.

| **이름** | **허용된 속성** | **의미** |
|---|---|---|
| **허용** | `wafFlags` (옵션) | wafFlags가 없으면 추가 규칙 처리를 중지하고 응답을 제공합니다. wafFlags가 있으면 지정된 WAF 보호를 비활성화하고 추가 규칙 처리를 진행합니다. |
| **차단** | `status, wafFlags` (선택 사항이며 함께 사용할 수 없음) | wafFlags가 없으면 다른 모든 속성을 무시하고 HTTP 오류를 반환합니다. 오류 코드는 상태 속성에 의해 정의되거나 기본값이 406으로 설정됩니다. wafFlags가 있으면 지정된 WAF 보호를 활성화하고 추가 규칙 처리를 진행합니다. |
| **log** | `wafFlags` (옵션) | 규칙이 트리거되었다는 사실을 기록합니다. 그렇지 않으면 처리에 영향을 주지 않습니다. wafFlags는 영향을 주지 않습니다. |

### WAF 플래그 목록 {#waf-flags-list}

다음 `wafFlag` 속성은 다음을 포함할 수 있습니다.

| **플래그 ID** | **플래그 이름** | **설명** |
|---|---|---|
| SQLI | SQL 주입 | SQL 주입은 임의의 데이터베이스 쿼리를 실행하여 애플리케이션에 대한 액세스 권한을 얻거나 권한 있는 정보를 얻으려는 시도입니다. |
| BACKDOOR | 백도어 | 백도어 신호는 일반적인 백도어 파일이 시스템에 있는지 확인하려고 시도하는 요청입니다. |
| CMDEXE | 명령 실행 | 명령 실행은 사용자 입력을 통해 임의의 시스템 명령으로 대상 시스템을 제어하거나 손상시키려는 시도입니다. |
| XSS | 크로스 사이트 스크립팅 | 크로스 사이트 스크립팅은 악성 JavaScript 코드를 통해 사용자의 계정이나 웹 탐색 세션을 하이재킹하려는 시도입니다. |
| TRAVERSAL | 디렉터리 순회 | 디렉터리 순회는 민감한 정보를 얻기 위해 시스템 전체에서 권한 있는 폴더를 탐색하려는 시도입니다. |
| USERAGENT | 공격 툴링 | 공격 툴링은 자동화된 소프트웨어를 사용하여 보안 취약성을 식별하거나 발견된 취약성을 악용하려고 시도하는 것입니다. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI 공격은 2.16.0 이전 Log4J 버전에 있는 [Log4Shell 취약점](https://en.wikipedia.org/wiki/Log4Shell)을 활용하려고 시도합니다. |
| AWS SSRF | AWS-SSRF | SSRF(Server Side Request Forgery)는 웹 애플리케이션이 만든 요청을 대상 내부 시스템으로 전송하려고 시도하는 요청입니다. AWS SSRF 공격은 SSRF를 사용하여 AWS(Amazon Web Services) 키를 얻고 S3 버킷과 해당 데이터에 대한 액세스 권한을 얻습니다. |
| BHH | 잘못된 홉 헤더 | 잘못된 홉 헤더는 잘못된 형식의 TE(Transfer-Encoding) 또는 CL(Content-Length) 헤더나 올바른 형식의 TE 및 CL 헤더를 통한 HTTP 스머글링 시도를 나타냅니다. |
| ABNORMALPATH | 비정상 경로 | 비정상 경로는 원래 경로가 정규화된 경로와 다름을 나타냅니다(예: `/foo/./bar`는 `/foo/bar`로 정규화됨). |
| COMPRESSED | 압축 감지 | POST 요청 본문이 압축되어 검사할 수 없습니다. 예를 들어 “Content-Encoding: gzip” 요청 헤더가 지정되고 POST 본문이 일반 텍스트가 아닌 경우입니다. |
| DOUBLEENCODING | 이중 인코딩 | 이중 인코딩은 html 문자를 이중 인코딩하는 회피 기술을 확인합니다. |
| FORCEFULBROWSING | 강제 탐색 | 강제 탐색은 관리자 페이지에 액세스를 시도했지만 실패한 경우입니다. |
| NOTUTF8 | 잘못된 인코딩 | 잘못된 인코딩으로 인해 서버가 요청의 악성 문자를 응답으로 변환하여 서비스 거부 또는 XSS가 발생할 수 있습니다. |
| JSON-ERROR | JSON 인코딩 오류 | “Content-Type” 요청 헤더 내에 JSON을 포함하도록 지정되었지만 JSON 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문입니다. 흔히 프로그래밍 오류나 자동화된 요청 또는 악성 요청과 관련이 있습니다. |
| MALFORMED-DATA | 요청 본문의 형식이 잘못된 데이터 | “Content-Type” 요청 헤더에 따라 형식이 잘못된 POST, PUT 또는 PATCH 요청 본문입니다. 예를 들어 “Content-Type: application/x-www-form-urlencoded” 요청 헤더가 지정되고 json인 POST 본문을 포함하는 경우입니다. 흔히 프로그래밍 오류, 자동화된 요청 또는 악성 요청에 해당합니다. 에이전트 3.2 이상이 필요합니다. |
| SANS | 악성 IP 트래픽 | 악성 활동에 연루된 것으로 보고된 [SANS 인터넷 스톰 센터](https://isc.sans.edu/) IP 주소 목록입니다. |
| SIGSCI-IP | 네트워크 효과 | SignalSciences에서 플래그 지정한 IP: 결정 엔진의 악성 신호로 인해 IP가 플래그 지정될 때마다 해당 IP가 모든 고객에게 전파됩니다. 플래그 기간 동안 추가 신호를 포함하는 해당 IP 주소의 후속 요청이 기록됩니다. |
| NO-CONTENT-TYPE | 누락된 “Content-Type” 요청 헤더 | “Content-Type” 요청 헤더가 없는 POST, PUT 또는 PATCH 요청입니다. 이 경우 기본적으로 애플리케이션 서버는 “Content-Type: text/plain; charset=us-ascii”를 가정하게 됩니다. 자동화된 요청 및 악성 요청 중 대다수에서 “Content Type”이 누락되어 있을 수 있습니다. |
| NOUA | 사용자 에이전트 없음 | 자동화된 요청 및 악성 요청 중 대다수가 가짜 사용자 에이전트 또는 누락된 사용자 에이전트를 사용하여 요청 주체인 디바이스 유형을 식별하기 어렵게 만듭니다. |
| TORNODE | Tor 트래픽 | Tor는 사용자의 신원을 숨기는 소프트웨어입니다. Tor 트래픽 스파이크가 발생한다면 공격자가 자신의 위치를 숨기려고 시도하고 있음을 나타낼 수 있습니다. |
| DATACENTER | 데이터센터 트래픽 | 데이터센터 트래픽은 식별된 호스팅 제공업체에서 발생하는 비유기적 트래픽입니다. 이러한 유형의 트래픽은 일반적으로 실제 최종 사용자와 연결되지 않습니다. |
| NULLBYTE | Null 바이트 | Null 바이트는 일반적으로 요청에 표시되지 않으며, 요청이 잘못된 형식이고 잠재적으로 악성임을 나타냅니다. |
| IMPOSTOR | 검색 봇 사칭자 | 검색 봇 사칭자는 Google 또는 Bing 검색 봇으로 위장했지만 실제로는 그렇지 않은 사람입니다. 응답 자체에 의존하지는 않지만 먼저 클라우드에서 해결해야 하므로 사전 규칙에서 사용해서는 안 됩니다. |
| PRIVATEFILE | 비공개 파일 | 비공개 파일은 민감한 정보를 유출할 수 있는 Apache `.htaccess` 파일 또는 구성 파일 등으로서, 흔히 본질적으로 기밀입니다. |
| SCANNER | 스캐너 | 널리 사용되는 스캔 서비스 및 도구를 식별합니다. |
| RESPONSESPLIT | HTTP 응답 분할 | 헤더를 HTTP 응답에 삽입하기 위해 CRLF 문자가 애플리케이션에 대한 입력으로 제출되는 시점을 식별합니다. |
| XML-ERROR | XML 인코딩 오류 | “Content-Type” 요청 헤더 내에 XML을 포함하도록 지정되었지만 XML 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문입니다. 흔히 프로그래밍 오류나 자동화된 요청 또는 악성 요청과 관련이 있습니다. |

## 고려 사항 {#considerations}

* 충돌하는 두 규칙이 만들어졌을 때는 항상 허용 규칙이 차단 규칙보다 우선합니다. 예를 들어 특정 경로를 차단하는 규칙과 하나의 특정 IP 주소를 허용하는 규칙을 만들면 차단된 경로에서 해당 IP 주소의 요청이 허용됩니다.

* 규칙이 일치하여 차단되면 CDN은 `406` 반환 코드로 응답합니다.

* 구성 파일에는 git 저장소에 액세스할 수 있는 모든 사람이 읽을 수 있으므로 비밀이 포함되어서는 안 됩니다.

## 규칙 예 {#examples}

몇 가지 규칙 예는 다음과 같습니다. 속도 제한의 예는 아래쪽의 [속도 제한 섹션](#rules-with-rate-limits)을 참조하십시오.

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
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
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

다음 규칙은 /block-me 경로에 대한 요청을 차단하고 SQLI 또는 XSS 패턴과 일치하는 모든 요청을 차단합니다.

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

**예 4**

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
        action: block
```

## 속도 제한이 있는 규칙 {#rules-with-rate-limits}

시간 경과에 따라 일치가 특정 속도를 초과하는 경우에만 규칙과 일치하는 트래픽을 차단하는 것이 바람직한 경우가 있습니다. `rateLimit` 속성의 값을 설정하면 규칙 조건과 일치하는 요청의 속도가 제한됩니다.

### rateLimit 구조 {#ratelimit-structure}

| **속성** | **유형** | **기본값** | **의미** |
|---|---|---|---|
| limit | 10에서 10000 사이의 정수 | required | 규칙이 트리거되는 초당 요청의 요청 속도입니다.. |
| window | 정수 열거형: 1, 10 또는 60 | 10 | 요청 속도를 계산하는 샘플링 기간(초). |
| penalty | 60에서 3600 사이의 정수 | 300(5분) | 일치하는 요청이 차단되는 기간(초 단위로 반올림). |
| groupBy | 배열[게터] | 없음 | 속도 제한 카운터는 요청 속성 집합(예: clientIp)으로 집계됩니다. |

### 예 {#ratelimiting-examples}

**예 1**

이 규칙은 지난 60초 동안 100req/sec를 초과하는 경우 5m 동안 클라이언트를 차단합니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**예 2**

지난 60초 동안 100req/sec를 초과하는 경우 경로/중요/리소스의 60초 차단 요청:

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

&quot;rules&quot; 속성은 일치하는 트래픽 필터 규칙을 설명하며, 다음 패턴을 포함합니다.

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

예:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

규칙은 다음과 같은 방식으로 동작합니다.

* 일치하는 규칙의 고객이 선언한 규칙 이름이 matches 속성에 나열됩니다.
* 작업 속성은 규칙이 차단, 허용 또는 로깅의 영향을 미쳤는지 여부를 설명합니다.
* waf에 라이센스가 부여되고 활성화되어 있으면 waf 속성은 구성에 waf 규칙이 나열되었는지 여부에 관계없이 감지된 모든 waf 규칙(예: SQLI, 고객이 선언한 이름과 독립적임)을 나열합니다.
* 고객이 선언한 규칙이 일치하지 않고 waf 규칙이 일치하지 않으면 rules 속성 속성이 비어 있습니다.

일반적으로 일치하는 규칙은 CDN 히트인지, 전달인지 또는 누락인지에 관계없이 CDN에 대한 모든 요청에 대한 로그 항목에 나타납니다. 단, WAF 규칙은 CDN 적중이 아니라 CDN 실패 또는 통과로 간주되는 CDN 요청에 대해서만 로그 항목에 나타납니다.

아래 예는 샘플 cdn.yaml 및 두 개의 CDN 로그 항목을 보여 줍니다.


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
| *rules* | 일치하는 규칙의 이름입니다.<br><br>또한 일치에 따라 차단되었는지 여부도 나타냅니다. <br><br>예: “`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`”<br><br>일치하는 규칙이 없으면 비어 있습니다. |
