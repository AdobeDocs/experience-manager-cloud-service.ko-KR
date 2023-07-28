---
title: 트래픽을 필터링하기 위한 CDN 및 WAF 규칙 구성
description: CDN 및 웹 애플리케이션 방화벽 규칙을 사용하여 악성 트래픽을 필터링합니다.
source-git-commit: a9b8b4d6029d0975428b9cff04dbbec993d56172
workflow-type: tm+mt
source-wordcount: '2371'
ht-degree: 2%

---


# 트래픽을 필터링하기 위한 CDN 및 WAF 규칙 구성 {#configuring-cdn-and-waf-rules-to-filter-traffic}

>[!NOTE]
>
>이 기능은 아직 일반적으로 사용할 수 없습니다. 진행 중인 얼리어답터 프로그램에 참여하려면 다음 이메일을 보내십시오. **aemcs-waf-adopter@adobe.com**, 조직 이름 및 기능에 대한 관심 컨텍스트 등.

Adobe은 고객 웹 사이트에 대한 공격을 완화하려고 하지만, 악성 트래픽이 애플리케이션에 도달하지 않도록 특정 패턴과 일치하는 요청을 사전에 필터링하는 것이 유용할 수 있습니다. 가능한 접근 방식은 다음과 같습니다.

* 다음과 같은 Apache 계층 모듈 `mod_security`
* Cloud Manager의 구성 파이프라인을 통해 CDN에 배포된 규칙을 구성합니다.

이 문서에서는 두 가지 범주의 규칙을 제공하는 후자의 접근 방식에 대해 설명합니다.

1. **CDN 규칙**: IP, 경로 및 사용자 에이전트를 포함한 요청 속성 및 요청 헤더에 따라 요청을 차단하거나 허용합니다. 이러한 규칙은 모든 AEM as a Cloud Service 고객이 구성할 수 있습니다
1. **WAF** (웹 응용 프로그램 방화벽) 규칙: 악의적인 트래픽과 관련된 것으로 알려진 다양한 패턴과 일치하는 요청을 차단합니다. 이러한 규칙은 WAF 추가 기능에 라이선스를 부여한 고객이 구성할 수 있습니다. 자세한 내용은 Adobe 계정 팀에 문의하십시오. 얼리어답터 프로그램 중에는 추가 라이선스가 필요하지 않습니다.

이러한 규칙은 프로덕션(샌드박스가 아닌) 프로그램용 개발, 스테이지 및 프로덕션 클라우드 환경 유형에 배포할 수 있습니다. RDE 환경에 대한 지원은 향후에 제공될 예정입니다.

## 설정 {#setup}

1. 먼저 git에서 다음 폴더 및 파일 구조를 최상위 수준 폴더로 만듭니다.

   ```
   config/
        cdn/
           cdn.yaml
           _config.yaml
   ```

1. `_config.yaml` 구성에 대한 몇 가지 메타데이터를 설명합니다. &quot;종류&quot; 매개 변수는 &quot;CDN&quot;으로 설정해야 하며 버전은 현재 &quot;1&quot;인 스키마 버전으로 설정해야 합니다. 아래 스니펫을 참조하십시오.

   ```
   kind: "CDN"
   version: "1"
   ```

   <!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. `cdn.yaml` 아래 섹션에 설명된 대로 CDN 규칙 및 WAF 규칙 목록을 포함해야 합니다.
1. WAF 규칙을 일치시키려면 새 프로그램 시나리오와 기존 프로그램 시나리오 모두에 대해 아래에 설명된 대로 Cloud Manager에서 WAF를 활성화해야 합니다. WAF를 사용하려면 별도의 라이센스를 구입해야 합니다.

   1. 새 프로그램에서 WAF를 구성하려면 **WAF-DDOS 보호** 의 확인란 **보안** 아래 표시된 대로 탭으로 이동합니다. 에 설명된 단계를 따라 계속합니다. [프로덕션 프로그램 추가](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 프로그램을 만들려면

   1. 기존 프로그램에서 WAF를 구성하려면 **프로그램 편집** 옵션에 설명된 단계를 따릅니다. [프로그램 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) 설명서를 참조하십시오. 그런 다음 **보안** 마법사의 탭에서는 언제든지 WAF-DDOS 옵션을 선택 취소하거나 확인할 수 있습니다

1. RDE 이외의 환경 유형의 경우 아래 설명된 대로 구성할 수 있는 Cloud Manager 구성 파이프라인을 실행합니다.

   1. Cloud Manager 홈 페이지의 파이프라인 카드에서 을 선택합니다. **프로덕션 파이프라인 추가** 또는 **비프로덕션 파이프라인 추가** 파이프라인 추가 마법사를 시작하려면
   1. 선택 **배포 파이프라인** 구성 탭에서

      ![파이프라인 배포 옵션을 선택합니다](/help/security/assets/deployment.png)

   1. 파이프라인 이름을 지정하고 배포 트리거 를 선택한 다음 을(를) 선택합니다 **계속**
   1. 다음에서 **소스 코드** 탭, 선택 **타깃팅된 배포**&#x200B;을 선택한 다음 을 선택합니다. **구성**

      ![타깃팅된 배포 선택](/help/security/assets/target-deployment.png)

   1. 필요에 따라 저장소 및 분기를 선택합니다. 선택한 환경에 대한 구성 파이프라인이 있는 경우 이 선택이 비활성화됩니다.

      ![구성 파이프라인 개요](/help/security/assets/config-pipeline.png)

      >[!NOTE]
      >
      >환경당 하나의 구성 파이프라인만 구성하고 실행할 수 있습니다.

   1. **저장**&#x200B;을 선택합니다. 새 파이프라인이 파이프라인 카드에 표시되며 준비가 되면 실행할 수 있습니다.
   1. RDE의 경우 명령줄이 사용되지만 현재 RDE는 지원되지 않습니다.

## 규칙 구문 {#rules-syntax}

규칙 형식은 아래에 설명되어 있으며, 그 뒤에는 다음 섹션에서 몇 가지 예를 볼 수 있습니다.

| **속성** | **CDN 규칙** | **WAF 규칙** | **유형** | **기본값** | **설명** |
|---|---|---|---|---|---|
| 이름 | X | X | `string` | - | 규칙 이름(64자, 영숫자만 포함할 수 있음 및 - ) |
| 조건 | X | X | `Condition` | - | 기본 구조는 다음과 같습니다.<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>getter, 조건자 및 여러 조건을 결합하는 방법을 설명하는 아래 조건 구조 구문 을 참조하십시오. |
| 작업 | X | X | `Enum` | 로그(CDN 규칙) | CDN 규칙의 경우: allow, block, log. 기본값은 로그입니다.<br><br>WAF 규칙의 경우: `enableWafRules`, `disableWafRules`, 로그. 기본값 없음. |
| rateLimit | X |   | `RateLimit` | 정의되지 않음 | 속도 제한 구성입니다. 정의되지 않은 경우 속도 제한이 비활성화됩니다.<br><br>아래에 예와 함께 rateLimit 구문을 설명하는 별도의 섹션이 있습니다. |
| wafRules |   | X | `array[Enum]` | - | 활성화 또는 비활성화해야 하는 WAF 규칙 목록입니다.<br><br>예를 들면 SQLI 및 XSS가 있습니다. 전체 목록이 필요하면 아래 waf 규칙 목록 을 참조하십시오. |

### 조건 구조 {#condition-structure}

조건은 단순 조건 또는 조건 그룹일 수 있습니다.

**단순 조건**

단순 조건은 getter와 술어로 구성됩니다.

```
{ <getter>: <value>, <predicate>: <value> }
```

**그룹 조건**

조건 그룹은 여러 개의 단순 및/또는 그룹 조건으로 구성됩니다.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **속성** | **유형** | **설명** |
|---|---|---|
| **allOf** | `array[Condition]` | **및** 작업. 나열된 모든 조건이 true를 반환하는 경우 true |
| **임의 항목** | `array[Condition]` | **또는** 작업. 나열된 조건 중 하나라도 true를 반환하는 경우 true |

**게터**

| **속성** | **유형** | **설명** |
|---|---|---|
| reqProperty | `string` | 요청 속성입니다.<br><br>다음 중 하나: `path` , `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>도메인 속성은 요청 호스트 헤더의 소문자로 변환됩니다. 대/소문자를 구분하기 때문에 일치 항목이 누락되지 않도록 문자열 비교에 유용합니다.<br><br>다음 `clientCountry` 에 표시되는 두 개의 문자 코드를 사용합니다. [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) |
| reqHeader | `string` | 지정된 이름의 요청 헤더 반환 |
| queryParam | `string` | 지정된 이름의 쿼리 매개 변수를 반환합니다. |
| 쿠키 | `string` | 지정된 이름의 쿠키 반환 |

**조건자**

| **속성** | **유형** | **설명** |
|---|---|---|
| **같음** | `string` | getter 결과가 제공된 값과 같은 경우 true |
| **doesNotEqual** | `string` | getter 결과가 제공된 값과 같지 않으면 true입니다. |
| **관심 표시** | `string` | getter 결과가 제공된 패턴과 일치하는 경우 true |
| **notLike** | `string` | getter 결과가 제공된 패턴과 일치하지 않으면 true |
| **matches** | `string` | getter 결과가 제공된 regex와 일치하는 경우 true |
| **doesNotMatch** | `string` | getter 결과가 제공된 regex와 일치하지 않으면 true |
| **-** | `array[string]` | 제공된 목록에 getter 결과가 포함된 경우 true |
| **notIn** | `array[string]` | 입력한 목록에 getter 결과가 없는 경우 true |

**wafRules 목록**

다음 `wafRules` 속성에는 다음 규칙이 포함될 수 있습니다.

| **규칙 ID** | **규칙 이름** | **설명** |
|---|---|---|
| SQLI | SQL 삽입 | SQL 삽입은 임의의 데이터베이스 쿼리를 실행하여 응용 프로그램에 대한 액세스 권한을 얻거나 권한이 있는 정보를 얻으려는 시도입니다. |
| 백도어 | 백도어 | 백도어 신호는 시스템에 공통 백도어 파일이 있는지 확인하기 위한 요청입니다. |
| CMDEXE | 명령 실행 | Command Execution은 사용자 입력에 의한 임의의 시스템 명령을 통해 대상 시스템을 제어하거나 손상시키려는 시도이다. |
| XSS | 크로스 사이트 스크립팅 | 크로스 사이트 스크립팅은 악의적인 JavaScript 코드를 통해 사용자 계정 또는 웹 브라우징 세션을 납치하려는 시도입니다. |
| 순회 | 디렉터리 트래버스 | Directory Traversal은 중요한 정보를 얻기 위해 시스템 전체에서 권한이 있는 폴더를 탐색하려는 시도이다. |
| USERAGENT | 공격 도구 | 공격 툴링은 보안 취약점을 식별하거나 검색된 취약점을 악용하기 위해 자동화된 소프트웨어를 사용하는 것입니다. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI 공격에서 [Log4Shell 취약성](https://en.wikipedia.org/wiki/Log4Shell) 2.16.0 이전 버전의 Log4J에 있음 |
| AWS SSRF | AWS- | SSRF(Server Side Request Forgery)는 웹 애플리케이션에서 만든 요청을 대상 내부 시스템으로 보내는 요청입니다. AWS SSRF 공격은 SSRF를 사용하여 Amazon Web Services(AWS) 키를 가져오고 S3 버킷 및 해당 데이터에 대한 액세스 권한을 얻습니다. |
| BHH | 잘못된 홉 헤더 | 잘못된 홉 헤더는 잘못된 형식의 TE(Transfer-Encoding) 또는 CL(Content-Length) 헤더 또는 올바른 형식의 TE 및 CL 헤더를 통한 HTTP 밀수 시도를 나타냅니다 |
| 비정상 경로 | 비정상 경로 | 비정상 경로는 원래 경로가 표준화된 경로와 다르다는 것을 나타냅니다(예: `/foo/./bar` 다음으로 표준화: `/foo/bar`) |
| 압축됨 | 압축 감지됨 | POST 요청 본문은 압축되어 검사할 수 없습니다. 예를 들어 &quot;Content-Encoding: gzip&quot; 요청 헤더가 지정되어 있고 POST 본문이 일반 텍스트가 아닌 경우, |
| 이중 인코딩 | 이중 인코딩 | 이중 인코딩은 html 문자를 이중으로 인코딩하는 회피 기법을 확인합니다 |
| 강제 탐색 | 강제 탐색 | 강제 탐색은 관리자 페이지에 액세스하지 못한 시도입니다. |
| NOTUTF8 | 잘못된 인코딩 | 잘못된 인코딩으로 인해 서버가 요청의 악성 문자를 응답으로 변환하여 서비스 거부 또는 XSS를 초래할 수 있습니다 |
| JSON-오류 | JSON 인코딩 오류 | &quot;Content-Type&quot; 요청 헤더 내에서 JSON을 포함하도록 지정되지만 JSON 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문입니다. 이는 종종 프로그래밍 오류나 자동화된 요청 또는 악의적인 요청과 관련이 있습니다. |
| 잘못된 데이터 | 요청 본문의 잘못된 데이터 | &quot;Content-Type&quot; 요청 헤더에 따라 형식이 잘못된 POST, PUT 또는 PATCH 요청 본문. 예를 들어 &quot;Content-Type: application/x-www-form-urlencoded&quot; 요청 헤더가 지정되고 json인 POST 본문이 포함된 경우. 이는 프로그래밍 오류, 자동화된 요청 또는 악의적인 요청인 경우가 많습니다. 에이전트 3.2 이상이 필요합니다. |
| SAN | 악성 IP 트래픽 | [SANS Internet Storm Center](https://isc.sans.edu/) 악의적인 활동에 연루된 것으로 보고된 IP 주소 목록 |
| SIGSCI-IP | 네트워크 효과 | SignalSciences로 플래그가 지정된 IP: 의사 결정 엔진의 악성 신호로 인해 IP에 플래그가 지정될 때마다 해당 IP가 모든 고객에게 전파됩니다. 그런 다음 플래그 기간 동안 추가 신호를 포함하는 IP 주소의 후속 요청이 기록됩니다 |
| NO-콘텐츠-유형 | Content-Type 요청 헤더 누락 | &quot;Content-Type&quot; 요청 헤더가 없는 POST, PUT 또는 PATCH 요청입니다. 기본적으로 애플리케이션 서버는 &quot;Content-Type: text/plain; charset=us-ascii&quot;를 가정해야 합니다. 자동화된 요청 및 악의적인 요청의 상당수가 &quot;콘텐츠 유형&quot;을 누락할 수 있습니다. |
| 명사 | 사용자 에이전트 없음 | 많은 자동화된 악의적인 요청은 가짜 또는 누락된 사용자 에이전트를 사용하여 요청을 수행하는 디바이스의 유형을 식별하는 것을 어렵게 합니다. |
| 토르노드 | 토르 트래픽 | 토르는 사용자의 신원을 숨기는 소프트웨어이다. 토르 트래픽의 급증은 공격자가 자신의 위치를 마스크하려고 시도하고 있음을 나타낼 수 있습니다. |
| 데이터 센터 | 데이터 센터 트래픽 | 데이터 센터 트래픽은 식별된 호스팅 공급자에서 발생하는 비유기 트래픽입니다. 이 유형의 트래픽은 일반적으로 실제 최종 사용자와 관련이 없습니다. |
| 널바이트 | Null 바이트 | Null 바이트는 일반적으로 요청에 표시되지 않으며 요청의 형식이 잘못되어 악의적일 수 있음을 나타냅니다. |
| 사기꾼 | SearchBot 가져오기 | 검색 봇 사기꾼은 Google 또는 Bing 검색 봇을 가장하지만 합법적이지 않은 사람입니다. 참고: 는 응답에 직접 의존하지 않지만 먼저 클라우드에서 해결해야 하므로 사전 규칙에서 사용해서는 안 됩니다. |
| 개인 파일 | 비공개 파일 | 개인 파일은 일반적으로 Apache와 같은 속성에서 기밀입니다 `.htaccess` 파일 또는 중요한 정보를 유출할 수 있는 구성 파일 |
| 스캐너 | 스캐너 | 자주 사용되는 스캔 서비스 및 도구 식별 |
| RESPONSESPLIT | HTTP 응답 분할 | CRLF 문자가 HTTP 응답에 헤더를 삽입하기 위해 애플리케이션에 입력으로 제출되는 시점을 식별합니다 |
| XML 오류 | XML 인코딩 오류 | &quot;Content-Type&quot; 요청 헤더 내에서 XML을 포함하는 것으로 지정되었지만 XML 구문 분석 오류가 포함된 POST, PUT 또는 PATCH 요청 본문. 이는 종종 프로그래밍 오류나 자동화된 요청 또는 악의적인 요청과 관련이 있습니다. |

## 고려 사항 {#considerations}

* 충돌하는 두 규칙이 만들어지면 허용 규칙이 항상 블록 규칙보다 우선합니다. 예를 들어 특정 경로를 차단하는 규칙과 하나의 특정 IP 주소를 허용하는 규칙을 만드는 경우 차단된 경로의 해당 IP 주소에서의 요청이 허용됩니다.

* 규칙이 일치하고 차단되면 CDN은 `406` 반환 코드.

## 예 {#examples}

몇 가지 규칙 예가 나와 있습니다. 다음을 참조하십시오. [요금 제한 섹션](#rules-with-rate-limits) 속도 제한의 예를 보려면 더 아래로 이동하십시오.

**예 1**

이 규칙은 IP 192.168.1.1에서 오는 요청을 차단합니다.

```
data:
  rules:
    - name: "block-request-from-ip"
      when: { reqProperty: clientIp, equals: "192.168.1.1" }
      action: block
```

**예제 2**

이 규칙은 경로의 요청을 차단합니다. `/helloworld` Chrome이 포함된 사용자 에이전트를 사용하여 게시할 때:

```
data:
  rules:
    - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
      when:
        allOf:
          - { reqProperty: path, equals: /helloworld }
          - { reqProperty: tier, equals: publish }
          - { reqHeader: user-agent, matches: '.*Chrome.*'  }
      action: block
```

**예제 3**

이 규칙은 쿼리 매개 변수를 포함하는 요청을 차단합니다 `foo`, 그러나 IP 192.168.1.1에서 오는 모든 요청을 허용합니다.

```
data:
  rules:
    - name: "block-request-that-contains-query-parameter-foo"
      when: { queryParam: url-param, equals: foo }
      action: block
    - name: "allow-all-requests-from-ip"
      when: { reqProperty: clientIp, equals: 192.168.1.1 }
      action: allow
```

**예제 4**

이 규칙은 경로 /block-me에 대한 요청을 차단하며 SQLI 또는 XSS 패턴과 일치하는 모든 요청을 차단합니다.

```
data:
  rules:
    - name: "path-rule"
      when: { reqProperty: path, equals: /block-me }
      action: block

    - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
      when: { reqProperty: path, like: "*" }
      action: enableWafRules
      wafRules:
        - SQLI
        - XSS
```

## 비율 제한이 있는 규칙 {#rules-with-rate-limits}

때때로 시간 경과에 따른 일치가 특정 비율을 초과하는 경우에만 규칙과 일치하는 트래픽을 차단하는 것이 바람직합니다. 값 설정 `rateLimit` 속성은 규칙 조건과 일치하는 요청의 비율을 제한합니다.

### rateLimit 구조 {#ratelimit-structure}

| **속성** | **유형** | **기본값** | **설명** |
|---|---|---|---|
| 제한 | 10~10000의 정수 | 필수 | 규칙이 트리거되는 요청 비율(초) |
| 창 | 정수 열거형: 1, 10 또는 60 | 10 | 요청 속도가 계산되는 샘플링 기간(초) |
| 벌금 | 60~3600의 정수 | 300(5분) | 일치하는 요청이 차단되는 기간(초)(가장 가까운 분으로 반올림됨) |

### 예 {#ratelimiting-examples}

예제 1: 요청 속도가 지난 60초 동안 초당 100개의 요청을 초과하면 차단합니다 `/critical/resource` 60초 동안

```
- name: rate-limit-example
  when: { reqProperty: /critical/resource }
  action: block
  rateLimit: { limit: 100, window: 60, penalty: 60 }
```

예제 2: 요청 속도가 10초 동안 초당 10개의 요청을 초과하면 300초 동안 리소스를 차단합니다.

```
- name: rate-limit-using-defaults
  when: { reqProperty: /critical/resource }
  action: block
  rateLimit:
    limit: 10
```

## CDN 로그 {#cdn-logs}

AEM as a Cloud Service에서는 캐시 적중률 최적화, CDN 및 WAF 규칙 구성 등의 사용 사례에 유용한 CDN 로그에 대한 액세스를 제공합니다. CDN 로그가 Cloud Manager에 표시됨 **로그 다운로드** 대화 상자(작성자 또는 게시 서비스 선택 시)

작업이 &quot;허용&quot;되어 트래픽이 차단되지 않더라도 요청이 규칙과 일치하는 경우 규칙 이름이 규칙 속성에 표시됩니다.

일치하는 CDN 규칙은 CDN 히트인지, 전달인지 또는 누락인지에 관계없이 CDN에 대한 모든 요청에 대한 로그 항목에 표시됩니다. 그러나 WAF 규칙은 CDN 누락 또는 전달로 간주되지만 CDN 히트는 간주되지 않는 CDN에 대한 요청에 대해서만 로그 항목에 표시됩니다.

아래 예제는 샘플을 보여 줍니다 `cdn.yaml` CDN 규칙과 WAF 규칙과 일치하는 차단된 요청으로 인해 rules 속성에 값이 비어 있지 않은 두 개의 CDN 로그 항목이 각각 있습니다.


```
data:
  rules:
    - name: "path-rule"
      when: { reqProperty: path, equals: /block-me }
      action: block

    - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
      when: { reqProperty: path, like: "*" }
      action: enableWafRules
      wafRules:
        - SQLI
        - XSS
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cip": "147.160.230.112",
"rid": "974e67f6",
"ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/block-me",
"req_mthd": "GET",
"res_type": "",
"cache": "PASS",
"res_status": 406,
"res_bsize": 3362,
"server": "PAR",
"rules": "cdn=path-rule;waf=;action=blocked"
}
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cip": "147.160.230.112",
"ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"rid": "974e67f6",
"host": "example.com",
"url": "/?sqli=%27%29%20UNION%20ALL%20SELECT%20NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL--%20fAPK",
"req_mthd": "GET",
"res_type": "image/png",
"cache": "PASS",
"res_status": 406,
"res_bsize": 3362,
"server": "PAR",
"rules": "cdn=;waf=SQLI;action=blocked"
}
```

### 로그 형식 {#cdn-log-format}

다음은 CDN 로그에 사용되는 필드 이름 목록과 간단한 설명입니다.

| **필드 이름** | **설명** |
|---|---|
| *timestamp* | TLS 종료 후 요청이 시작된 시간 |
| *ttfb* | 의 약어 *첫 번째 바이트까지의 시간*. 요청 사이의 시간 간격이 응답 본문의 스트리밍을 시작하기 전 시점까지 시작되었습니다. |
| *cip* | 클라이언트 IP 주소입니다. |
| *rid* | 요청을 고유하게 식별하는 데 사용되는 요청 헤더의 값입니다. |
| *ua* | 주어진 HTTP 요청을 담당하는 사용자 에이전트입니다. |
| *호스트* | 요청이 의도한 권한. |
| *url* | 쿼리 매개 변수를 포함한 전체 경로입니다. |
| *req_mthd* | &quot;GET&quot; 또는 &quot;POST&quot;와 같이 클라이언트가 전송하는 HTTP 메서드입니다. |
| *res_type* | 리소스의 원래 미디어 유형을 나타내는 데 사용되는 콘텐츠 유형 |
| *cache* | 캐시의 상태입니다. 가능한 값은 히트, 누락 또는 패스입니다 |
| *res_status* | 정수 값으로서의 HTTP 상태 코드. |
| *res_bsize* | 응답에서 클라이언트로 보낸 본문 바이트. |
| *서버* | CDN 캐시 서버의 데이터 센터입니다. |
| *규칙* | CDN 규칙과 waf 규칙 모두에 일치하는 규칙의 이름입니다.<br><br>일치하는 CDN 규칙은 CDN 히트인지, 전달인지 또는 누락인지에 관계없이 CDN에 대한 모든 요청에 대한 로그 항목에 표시됩니다.<br><br>또한 일치 결과가 블록인지 여부를 나타냅니다. <br><br>예, &quot;`cdn=;waf=SQLI;action=blocked`&quot;<br><br>일치하는 규칙이 없으면 비어 있습니다. |
