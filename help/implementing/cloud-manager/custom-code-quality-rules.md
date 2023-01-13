---
title: 사용자 정의 코드 품질 규칙
description: 이 페이지에서는 코드 품질 테스트의 일부로 Cloud Manager에서 실행하는 사용자 정의 코드 품질 규칙에 대해 설명합니다. 이러한 수정 사항은 Adobe Experience Manager 엔지니어링 팀의 우수 사례를 기반으로 합니다.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
source-git-commit: 2935338b847f7e852dfd31c93a61e737e8a3ec80
workflow-type: tm+mt
source-wordcount: '3485'
ht-degree: 43%

---

# 사용자 지정 코드 품질 규칙 {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="사용자 정의 코드 품질 규칙"
>abstract="이 페이지에서는 코드 품질 테스트의 일부로 Cloud Manager에서 실행하는 사용자 정의 코드 품질 규칙에 대해 설명합니다. 이러한 수정 사항은 Adobe Experience Manager 엔지니어링 팀의 우수 사례를 기반으로 합니다."

이 페이지에서는 Cloud Manager가 의 일부로 실행하는 사용자 지정 코드 품질 규칙에 대해 설명합니다 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md). Experience Manager 엔지니어링 팀의 우수 사례를 기반으로 합니다.

>[!NOTE]
>
>여기에 제공된 코드 샘플은 설명 목적으로만 제공됩니다. SonarQube 개념 및 품질 규칙에 대한 자세한 내용은 SonarQube [개념 설명서](https://docs.sonarqube.org/latest/)를 참조하십시오.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 SonarQube 규칙에 대해 자세히 설명합니다.

### 위험한 기능을 사용하지 마십시오 {#do-not-use-potentially-dangerous-functions}

* **키**: CQRules:CWE-676
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

메서드 `Thread.stop()` 및 `Thread.interrupt()` 는 재현하기 어려운 문제 및 경우에 따라 보안 취약점을 생성할 수 있습니다. 이러한 사용은 철저하게 모니터링되고 검증되어야 합니다. 일반적으로 메시지 전달은 유사한 목표를 달성하기 위한 보다 안전한 방법입니다.

#### 비호환 코드 {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### 호환 코드 {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### 외부에서 제어할 수 있는 형식 문자열을 사용하지 마십시오 {#do-not-use-format-strings-which-may-be-externally-controlled}

* **키**: CQRules:CWE-134
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

외부 소스의 형식 문자열(예: 요청 매개변수 또는 사용자 생성 콘텐츠)을 사용하면 애플리케이션이 서비스 거부 공격에 노출될 수 있습니다. 형식 문자열이 외부에서 제어될 수 있지만 신뢰할 수 있는 소스에서만 허용되는 환경이 있습니다.

#### 비호환 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에는 항상 소켓 및 연결 시간 초과가 있어야 합니다 {#http-requests-should-always-have-socket-and-connect-timeouts}

* **키**: CQRules:ConnectionTimeoutMechanism
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2018.6.0

Experience Manager 애플리케이션 내에서 HTTP 요청을 실행할 때 불필요한 스레드 사용을 방지하기 위해 적절한 시간 초과가 구성되어 있는지 확인해야 합니다. 안타깝게도 Java™의 기본 HTTP 클라이언트(`java.net.HttpUrlConnection`)과 일반적으로 사용되는 Apache HTTP 구성 요소 클라이언트는 제한 시간을 초과하지 않도록 해야 하므로 시간 제한을 명시적으로 설정해야 합니다. 또한 가장 좋은 방법은 이러한 시간 초과를 60초 이내로 설정하는 것입니다.

#### 비호환 코드 {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### 호환 코드 {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### 항상 ResourceResolver 개체를 닫습니다. {#resourceresolver-objects-should-always-be-closed}

* **키**: CQRules:CQBP-72
* **유형**: 코드 스멜
* **심각도**: 주요
* **이후**: 버전 2018.4.0

`ResourceResolverFactory`에서 가져온 `ResourceResolver` 개체는 시스템 리소스를 사용합니다. `ResourceResolver`가 더 이상 사용되지 않을 때 이러한 리소스를 회수하는 방법이 있지만 `close()` 메서드를 호출하여 열려 있는 `ResourceResolver` 개체를 명시적으로 닫는 것이 더 효율적입니다.

비교적 일반적인 오해는 `ResourceResolver` 기존 JCR 세션을 사용하여 만든 개체는 명시적으로 닫거나, 이렇게 하면 기본 JCR 세션이 닫히지 않아야 합니다. 이는 사실이 아닙니다. `ResourceResolver`를 여는 방법과 상관없이 더 이상 사용하지 않을 때는 닫아야 합니다. `ResourceResolver`는 `Closeable` 인터페이스를 구현하기 때문에 `close()`를 명시적으로 호출하는 대신 `try-with-resources` 구문을 사용하는 것도 가능합니다.

#### 비호환 코드 {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### 호환 코드 {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### 서블릿을 등록하는 데 Sling 서블릿 경로를 사용하지 마십시오 {#do-not-use-sling-servlet-paths-to-register-servlets}

* **키**: CQRules:CQBP-75
* **유형**: 코드 스멜
* **심각도**: 주요
* **이후**: 버전 2018.4.0

[슬링 설명서](https://sling.apache.org/documentation/the-sling-engine/servlets.html)에 설명된 대로 경로별로 서블릿을 바인딩하는 것은 권장되지 않습니다. 경로 바인딩 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으며, 결과적으로 엄격한 추가 보안이 요구됩니다. 경로 바인딩 서블릿을 사용하는 대신 저장소에 노드를 생성하고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 비호환 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### catch 예외가 기록되거나 throw되어야 하며 둘 다 예외가 아닙니다. {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **키**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

일반적으로 예외는 정확히 한 번 기록해야 합니다. 예외를 여러 번 기록하면 예외가 몇 번 발생했는지 알 수 없으므로 혼동이 발생할 수 있습니다. 이렇게 되는 가장 일반적인 패턴은 발생한 예외의 기록과 표시입니다.

#### 비호환 코드 {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### 호환 코드 {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Throw 문 바로 뒤에 로그 문을 사용하지 마십시오 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **키**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

피해야 할 또 다른 일반적인 패턴은 메시지를 기록한 다음 즉시 예외를 발생시키는 것입니다. 일반적으로 이 방법은 예외 메시지가 로그 파일에서 복제됨을 나타냅니다.

#### 비호환 코드 {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### 호환 코드 {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### GET 또는 HEAD 요청을 처리할 때 INFO에서 로깅을 사용하지 마십시오 {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **키**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **유형**: 코드 스멜
* **심각도**: 사소

일반적으로 INFO 로그 수준은 중요한 작업을 구분하는 데 사용해야 하며, 기본적으로 Experience Manager은 INFO 수준 이상으로 로그온하도록 구성되어 있습니다. GET 및 HEAD 메서드는 읽기 전용 작업이어야 하므로 중요한 작업을 구성하지 않습니다. GET 또는 HEAD 요청에 응답하여 INFO 수준에서 로그인하면 상당한 로그 노이즈가 발생할 수 있으므로 로그 파일에서 유용한 정보를 식별하기가 어렵습니다. GET 또는 HEAD 요청을 처리할 때 로깅은 문제가 발생했을 때 WARN 또는 ERROR 수준이거나 더 자세한 문제 해결 정보가 도움이 될 경우 DEBUG 또는 TRACE 수준이어야 합니다.

>[!NOTE]
>
>이 변수에는 적용되지 않습니다 `access.log`-각 요청에 대한 로깅을 입력합니다.

#### 비호환 코드 {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### 호환 코드 {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Exception.getMessage()를 로깅 문의 첫 번째 매개 변수로 사용하지 마십시오 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **키**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

가장 좋은 방법은 로그 메시지가 애플리케이션에서 예외가 발생한 위치에 대한 상황별 정보를 제공하는 것입니다. 스택 추적을 사용하여 컨텍스트를 결정할 수도 있지만 일반적으로 로그 메시지는 읽고 이해하는 것이 더 쉽습니다. 따라서 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것은 잘못된 관행입니다. 예외 메시지에는 잘못된 내용이 포함되어 있지만 로그 메시지는 예외가 발생했을 때 애플리케이션이 수행한 작업을 로그 판독기에 알리는 데 사용해야 합니다. 예외 메시지가 여전히 기록됩니다. 고유한 메시지를 지정하여 로그를 쉽게 이해할 수 있습니다.

#### 비호환 코드 {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### 호환 코드 {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### catch 블록에 로그인하는 것은 WARN 또는 ERROR 수준이어야 합니다. {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **키**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

이름에서 알 수 있듯이 예외사항은 항상 예외적인 상황에서 사용해야 합니다. 결과적으로 예외가 발생하면 로그 메시지가 WARN 또는 ERROR 중 적절한 수준으로 기록되도록 하는 것이 중요합니다. 이렇게 하면 해당 메시지가 로그에 올바르게 표시됩니다.

#### 비호환 코드 {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### 호환 코드 {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 콘솔에 스택 추적을 인쇄하지 마십시오 {#do-not-print-stack-traces-to-the-console}

* **키**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

앞에서 언급했듯이 로그 메시지를 이해할 때는 컨텍스트가 중요합니다. 사용 `Exception.printStackTrace()` 스택 추적만 표준 오류 스트림으로 출력되도록 하여 모든 컨텍스트를 잃게 합니다. 또한 Experience Manager과 같은 다중 스레드 응용 프로그램에서 이 방법을 사용하여 여러 예외가 동시에 인쇄되면 스택 추적이 겹칠 수 있으므로 큰 혼동을 일으킬 수 있습니다. 예외는 로깅 프레임워크에서만 기록되어야 합니다.

#### 비호환 코드 {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### 호환 코드 {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 표준 출력 또는 표준 오류로 출력하지 않습니다. {#do-not-output-to-standard-output-or-standard-error}

* **키**: CQRules:CQBP-44—LogLevelConsolePrinters
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

Experience Manager에 로그인하는 작업은 항상 로깅 프레임워크(SLF4J)를 통해 수행해야 합니다. 표준 출력 또는 표준 오류 스트림에 직접 출력하면 로깅 프레임워크에서 제공하는 구조적 및 컨텍스트 정보가 손실됩니다. 경우에 따라 성능 문제가 발생할 수 있습니다.

#### 비호환 코드 {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### 호환 코드 {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 하드 코딩된 /apps 및 /libs 경로 방지 {#avoid-hardcoded-apps-and-libs-paths}

* **키**: CQRules:CQBP-71
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2018.4.0

일반적으로 `/libs`와 `/apps`로 시작하는 경로는 슬링 검색 경로(기본적으로 `/libs,/apps`로 설정됨)에 상대적인 경로로 가장 일반적으로 저장되므로 하드 코딩해서는 안 됩니다. 절대 경로를 사용하면 프로젝트 수명 주기의 후반에만 나타나는 미묘한 결함이 발생할 수 있습니다.

#### 비호환 코드 {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### 호환 코드 {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling 스케줄러 사용 안 함 {#sonarqube-sling-scheduler}

* **키**: CQRules:AMSCORE-554
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

보장된 실행이 필요한 작업에 Sling Scheduler를 사용하지 마십시오. 슬링이 예약된 작업은 실행을 보장하며 클러스터된 환경과 비클러스터된 환경 모두에 더 적합합니다.

을(를) 참조하십시오. [Apache Sling 이벤트 및 작업 처리](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) 를 사용하여 클러스터된 환경에서 Sling 작업을 처리하는 방법을 자세히 알아보십시오.

### 더 이상 사용되지 않는 Experience Manager API는 사용하지 마십시오 {#sonarqube-aem-deprecated}

* **키**: AMSCORE-553
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

Experience Manager API 서피스는 사용이 중단되어 더 이상 사용되지 않는 API를 식별하기 위해 상수 수정 아래에 있습니다.

이러한 API는 표준 Java™을 사용하여 더 이상 사용되지 않는 경우가 많습니다 `@Deprecated` 주석 및 기타, `squid:CallToDeprecatedMethod`.

그러나 API는 Experience Manager 컨텍스트에서 더 이상 사용되지 않지만 다른 컨텍스트에서는 더 이상 사용되지 않는 경우가 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.


## OakPAL 콘텐츠 규칙 {#oakpal-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 OakPAL 검사에 대해 자세히 설명합니다.

>[!NOTE]
>
>OakPAL은 독립 실행형 Oak 저장소를 사용하여 콘텐츠 패키지의 유효성을 검사하는 프레임워크입니다. Experience Manager 파트너에 의해 개발되었으며 2019 Experience Manager 록스타 노스 아메리카 상을 수상한 바 있다.

### @ProviderType으로 주석을 단 제품 API는 고객이 구현하거나 확장하면 안 됩니다 {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **키**: CQBP-84
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2018.7.0

Experience Manager API에는 사용자 지정 코드에 의해서만 사용되지만 구현되지는 않는 Java™ 인터페이스 및 클래스가 포함되어 있습니다. 예: 인터페이스 `com.day.cq.wcm.api.Page` 는 Experience Manager로만 구현해야 합니다.

이러한 인터페이스에 새 메서드를 추가하면 이러한 추가 메서드가 이러한 인터페이스를 사용하는 기존 코드에 영향을 주지 않습니다. 따라서 이러한 인터페이스에 새로운 메서드를 추가하는 것은 이전 버전과 호환되는 것으로 간주됩니다. 그러나 사용자 정의 코드가 이러한 인터페이스 중 하나를 구현하는 경우 해당 사용자 정의 코드는 고객에게 역호환성 위험을 초래합니다.

Experience Manager에 의해 구현된 인터페이스 및 클래스는 `org.osgi.annotation.versioning.ProviderType` 또는 때로 유사한 이전 주석 `aQute.bnd.annotation.ProviderType`. 이 규칙은 이러한 인터페이스가 구현되거나 사용자 정의 코드에 의해 클래스가 확장되는 경우를 식별합니다.

#### 비호환 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 사용자 지정 Lucene Oak 색인에는 Tika 구성이 있어야 합니다. {#oakpal-indextikanode}

* **키**: IndexTikaNode
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 2021.8.0

즉시 사용 가능한 여러 Experience Manager Oak 색인에는 Tika 구성이 포함되어 있으며 이러한 인덱스의 사용자 지정에는 Tika 구성이 포함되어야 합니다. 이 규칙은 `damAssetLucene`, `lucene` 및 `graphqlConfig` 인덱스의 사용자 정의 항목을 확인하고 `tika` 노드가 누락되거나 `tika` 노드에 `config.xml`이라는 하위 노드가 누락된 경우 문제를 발생시킵니다.

인덱스 정의 사용자 정의에 대한 자세한 내용은 [인덱싱 문서](/help/operations/indexing.md#preparing-the-new-index-definition)를 참조하십시오.

#### 비호환 코드 {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
```

#### 호환 코드 {#compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 사용자 지정 Lucene Oak 색인은 동기화되어서는 안 됩니다 {#oakpal-indexasync}

* **키**: IndexAsyncProperty
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 2021.8.0

`lucene` 유형의 Oak 인덱스는 항상 비동기식으로 인덱싱되어야 합니다. 이렇게 하지 않으면 시스템이 불안정해질 수 있습니다. Lucene 인덱스 구조에 대한 자세한 내용은 [Oak 설명서.](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition)

#### 비호환 코드 {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

#### 호환 코드 {#compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 사용자 지정 DAM Asset Lucene Oak 인덱스가 올바르게 구조화됩니다  {#oakpal-damAssetLucene-sanity-check}

* **키**: IndexDamAssetLucene
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 2021.6.0

자산 검색이 Experience Manager Assets에서 올바르게 작동하려면 `damAssetLucene` Oak 색인은 이 색인과 관련된 지침 세트를 따라야 합니다. 이 규칙은 인덱스 정의에 `visualSimilaritySearch` 값이 포함된 `tags`라는 다중 값 속성이 있어야 하는지 확인합니다.

#### 비호환 코드 {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
      + tika
        + config.xml
```

#### 호환 코드 {#compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 고객 패키지는 /libs 아래에 노드를 만들거나 수정해서는 안 됩니다. {#oakpal-customer-package}

* **키**: BannedPath
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2019.6.0

그것은 오랫동안 지켜온 가장 좋은 방법이었습니다 `/libs` Experience Manager 컨텐츠 저장소의 컨텐츠 트리는 고객이 읽기 전용으로 간주해야 합니다. `/libs`에서 노드 및 속성을 수정하면 주 업데이트 및 부 업데이트에 상당한 위험이 발생합니다. 수정 사항 `/libs` Adobe이 공식 채널을 통해 해야 합니다.

### 패키지에 중복 OSGi 구성이 포함되어 있지 않아야 합니다. {#oakpal-package-osgi}

* **키**: DuplicateOsgiConfigurations
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성되는 경우입니다. 이 문제는 구성을 적용할 수 있다는 모호성을 만듭니다. 이 규칙은 동일한 실행 모드나 실행 모드의 조합에서 동일한 구성 요소가 여러 번 구성되는 문제만 식별하는 &quot;실행 모드 인식&quot;입니다.

>[!NOTE]
>
>이 규칙은 동일한 경로에서 동일한 구성이 여러 패키지에서 정의되는 문제를 발생시킵니다. 여기에는 동일한 패키지가 내장된 패키지의 전체 목록에 중복되는 경우를 포함합니다.
>
>예를 들어 빌드에서 이름이 인 패키지를 만드는 경우 `com.myco:com.myco.ui.apps` 및 `com.myco:com.myco.all` 여기서 `com.myco:com.myco.all` 침대 `com.myco:com.myco.ui.apps`, 및에서 모든 구성 `com.myco:com.myco.ui.apps` 은 중복으로 보고됩니다.
>
>이는 일반적으로 다음을 따르지 않는 경우입니다 [컨텐츠 패키지 구조 지침](/help/implementing/developing/introduction/aem-project-content-package-structure.md). 이 특정 예에서 패키지 `com.myco:com.myco.ui.apps`에는 `<cloudManagerTarget>none</cloudManagerTarget>` 속성이 없습니다.

#### 비호환 코드 {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 호환 코드 {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### 구성 및 설치 폴더에는 OSGi 노드만 포함되어야 합니다 {#oakpal-config-install}

* **키**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

보안상의 이유로 `/config/` 및 `/install/` 는 Experience Manager에서 관리 사용자가 읽기 전용이며 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트를 포함하는 경로에 다른 유형의 콘텐츠를 배치하면 관리 사용자와 비관리 사용자 간에 의도하지 않게 달라지는 애플리케이션 비헤이비어가 발생합니다.

일반적인 문제는 구성 요소 대화 상자 내에서 `config`라는 노드를 사용하거나 인라인 편집을 위해 리치 텍스트 편집기 구성을 지정할 때 발생합니다. 이 문제를 해결하려면 해당 노드의 이름을 호환 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 `configPath` 속성 `cq:inplaceEditing` 노드 아래에 새 위치를 지정합니다.

#### 비호환 코드 {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 호환 코드 {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### 패키지는 겹치지 않아야 합니다 {#oakpal-no-overlap}

* **키**: PackageOverlaps
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

[패키지에 중복된 OSGi 구성 규칙을 포함해서는 안 됨](#oakpal-package-osgi)과 마찬가지로, 여러 개의 개별 콘텐츠 패키지에 의해 동일한 노드 경로가 기록되는 복잡한 프로젝트에서 일반적인 문제입니다. 콘텐츠 패키지 종속성을 사용하면 일관된 결과를 보장할 수 있지만 중복을 완전히 피하는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI가 아니어야 합니다 {#oakpal-default-authoring}

* **키**: ClassicUIAuthoringMode
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

OSGi 구성 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` Experience Manager 내에서 기본 작성 모드를 정의합니다. 왜냐면 [클래식 UI는 Experience Manager 6.4 이후 더 이상 사용되지 않습니다](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html): 기본 작성 모드가 클래식 UI로 구성된 경우 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 터치 UI 대화 상자가 있어야 합니다 {#oakpal-components-dialogs}

* **키**: ComponentWithOnlyClassicUIDialog
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

클래식 UI 대화 상자가 있는 Experience Manager 구성 요소에는 항상 해당 터치 UI 대화 상자가 있어야 합니다. 둘 다 클래식 UI가 지원되지 않는 Cloud Service 배포 모델과 호환될 수 있는 최적의 작성 환경을 제공합니다. 이 규칙은 다음 시나리오를 확인합니다.

* 클래식 UI 대화 상자(즉, `dialog` 하위 노드)가 있는 구성 요소에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 디자인 대화 상자(즉, `design_dialog` 노드)가 있는 구성 요소에는 해당 터치 UI 디자인 대화 상자(즉, `cq:design_dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 대화 상자 및 클래식 UI 디자인 대화 상자가 모두 있는 구성 요소에는 해당 터치 UI 대화 상자 및 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

Experience Manager 현대화 도구 설명서는 구성 요소를 클래식 UI에서 Touch UI로 변환하는 방법에 대한 설명서 및 도구를 제공합니다. 자세한 내용은 [Experience Manager 현대화 도구 설명서](https://opensource.adobe.com/aem-modernize-tools/) 자세한 내용

### 패키지는 가변 콘텐츠와 변경할 수 없는 콘텐츠를 혼합하지 않아야 합니다 {#oakpal-packages-immutable}

* **키**: ImmutableMutableMixedPackage
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

Cloud Service 배포 모델과 호환되려면 개별 컨텐츠 패키지에 저장소의 변경할 수 없는 영역에 대한 컨텐츠가 포함되어야 합니다(`/apps` 및 `/libs`) 또는 변경할 수 있는 영역(에 없는 모든 것) `/apps` 또는 `/libs`). 예를 들어, 두 가지 모두를 포함하는 패키지 `/apps/myco/components/text` 및 `/etc/clientlibs/myco` 는 Cloud Service과 호환되지 않으므로 문제가 보고됩니다.

>[!NOTE]
>
>[고객 패키지는 /libs에서 노드를 생성하거나 수정해서는 안 됨](#oakpal-customer-package) 규칙은 항상 적용됩니다.

을(를) 참조하십시오. [Experience Manager 프로젝트 구조](/help/implementing/developing/introduction/aem-project-content-package-structure.md) 자세한 내용

### 역방향 복제 에이전트 사용 안 함 {#oakpal-reverse-replication}

* **키**: ReverseReplication
* **유형**: 코드 스멜/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

Experience Manager as a Cloud Service의 일부로 설명된 대로 역방향 복제에 대한 지원은 Cloud Service 배포에서 사용할 수 없습니다 [릴리스 노트.](/help/release-notes/aem-cloud-changes.md#replication-agents)

역방향 복제를 사용하는 고객은 대체 솔루션을 Adobe에 문의해야 합니다.

### 프록시 사용 클라이언트 라이브러리에 포함된 리소스는 resources 라는 폴더에 있어야 합니다 {#oakpal-resources-proxy}

* **키**: ClientlibProxyResource
* **유형**: 버그
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager 클라이언트 라이브러리에는 이미지 및 글꼴과 같은 정적 리소스가 포함될 수 있습니다. [프로세서 사용](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors) 문서에 설명된 대로 프록시 클라이언트 라이브러리를 사용할 때 게시 인스턴스에서 효과적으로 참조하려면 이러한 정적 리소스가 `resources`라는 하위 폴더에 포함되어 있어야 합니다.

#### 비호환 코드 {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 호환 코드 {#compliant-proxy-enabled}

```tet
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### 호환되지 않는 워크플로우 프로세스 Cloud Service 사용 {#oakpal-usage-cloud-service}

* **키**: CloudServiceIncompatibleWorkflowProcess
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service에서 자산 처리를 위해 자산 마이크로 서비스로 이동 시 Experience Manager의 온-프레미스 및 AMS 버전에서 사용된 몇 가지 워크플로우 프로세스가 지원되지 않거나 필요하지 않게 되었습니다.

의 마이그레이션 도구 [as a Cloud Service 자산 GitHub 저장소 Experience Manager](https://github.com/adobe/aem-cloud-migration) 는 Experience Manager as a Cloud Service으로 마이그레이션하는 동안 워크플로우 모델을 업데이트하는 데 사용할 수 있습니다.

### 정적 템플릿 사용은 편집 가능한 템플릿을 위한 것이 아닙니다 {#oakpal-static-template}

* **키**: StaticTemplateUsage
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

정적 템플릿은 Experience Manager 프로젝트에서 일반적으로 사용되지만, Adobe은 정적 템플릿에 없는 가장 유연한 추가 기능을 제공하고 지원하기 때문에 편집 가능한 템플릿을 권장합니다. 자세한 내용은 [페이지 템플릿](/help/implementing/developing/components/templates.md) 문서에서 확인할 수 있습니다.

정적 템플릿에서 편집 가능한 템플릿으로 마이그레이션은 [Experience Manager 현대화 도구.](https://opensource.adobe.com/aem-modernize-tools/)

### 레거시 기초 구성 요소의 사용이 중단되었습니다 {#oakpal-usage-legacy}

* **키**: LegacyFoundationComponentUsage
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

기존 기초 구성 요소(즉, `/libs/foundation`)에 로그인되어 있는지 확인하십시오 [여러 Experience Manager 릴리스에 사용되지 않음](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) 핵심 구성 요소를 고려합니다. 기존 Foundation 구성 요소를 오버레이 또는 상속 여부에 관계없이 사용자 정의 구성 요소의 기준으로 사용하는 것은 권장되지 않으며 해당 코어 구성 요소로 변환해야 합니다.

이 변환은 다음을 통해 용이하게 할 수 있습니다 [Experience Manager 현대화 도구.](https://opensource.adobe.com/aem-modernize-tools/)

### 지원되는 실행 모드 이름 및 순서 지정만 사용 {#oakpal-supported-runmodes}

* **키**: SupportedRunmode
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager은 실행 모드 이름에 대한 엄격한 이름 지정 정책을 적용하고 이러한 실행 모드에 대한 엄격한 순서를 적용합니다. 지원되는 실행 모드 목록은 문서에 있습니다 [Experience Manager에 배포 as a Cloud Service](/help/implementing/deploying/overview.md#runmodes) 그리고 이로부터 모든 편차는 문제로 식별됩니다.

### 사용자 지정 검색 색인 정의 노드는 /oak:index의 직접 하위 노드여야 합니다 {#oakpal-custom-search}

* **키**: OakIndexLocation
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service을 사용하려면 해당 사용자 지정 검색 색인 정의(예: 유형의 노드)가 필요합니다 `oak:QueryIndexDefinition`)의 직접 하위 노드 `/oak:index`. 다른 위치의 인덱스를 Experience Manager as a Cloud Service과 호환되도록 이동해야 합니다. 검색 인덱스에 대한 자세한 내용은 [콘텐츠 검색 및 인덱싱](/help/operations/indexing.md) 문서를 참조하십시오.

### 사용자 지정 검색 색인 정의 노드에는 compatVersion 2 가 있어야 합니다. {#oakpal-custom-search-compatVersion}

* **키**: IndexCompatVersion
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service을 사용하려면 사용자 지정 검색 색인 정의(예: 유형 노드)가 필요합니다 `oak:QueryIndexDefinition`)에는 가 있어야 합니다. `compatVersion` 속성 설정 `2`. 다른 값은 Experience Manager as a Cloud Service에서 지원되지 않습니다. 검색 인덱스에 대한 자세한 내용은 [콘텐츠 검색 및 인덱싱](/help/operations/indexing.md)를 참조하십시오.

### 사용자 지정 검색 색인 정의 노드의 하위 노드는 nt:unrecordinated 형식이어야 합니다. {#oakpal-descendent-nodes}

* **키**: IndexDescendantNodeType
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

사용자 지정 검색 색인 정의 노드에 순서가 없는 하위 노드가 있으면 문제를 해결하기 어려울 수 있습니다. 이러한 상황을 방지하려면 `oak:QueryIndexDefinition` 노드 유형 `nt:unstructured`.

### 사용자 지정 검색 색인 정의 노드에는 하위 노드가 있는 indexRules라는 하위 노드가 있어야 합니다 {#oakpal-custom-search-index}

* **키**: IndexRulesNode
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

올바르게 정의된 사용자 정의 검색 인덱스 정의 노드에는 `indexRules`라는 하위 노드가 있어야 하며, 이 노드에는 하나 이상의 하위 노드가 있어야 합니다. 자세한 내용은 [Oak 문서](https://jackrabbit.apache.org/oak/docs/query/lucene.html)에서 확인할 수 있습니다.

### 사용자 지정 검색 색인 정의 노드는 이름 지정 규칙을 따라야 합니다 {#oakpal-custom-search-definitions}

* **키**: IndexName
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service을 사용하려면 사용자 지정 검색 색인 정의(즉, 유형의 노드)가 필요합니다 `oak:QueryIndexDefinition`)은 문서에 설명된 특정 패턴에 따라 이름을 지정해야 합니다 [컨텐츠 검색 및 색인 지정](/help/operations/indexing.md)

### 사용자 지정 검색 색인 정의 노드는 인덱스 유형 Lucene을 사용해야 합니다  {#oakpal-index-type-lucene}

* **키**: IndexType
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 버전 2021.2.0(유형 및 심각도는 2021.8.0에 변경됨)

Experience Manager as a Cloud Service을 사용하려면 해당 사용자 지정 검색 색인 정의(예: 유형의 노드)가 필요합니다 `oak:QueryIndexDefinition`)에 `type` 값이 로 설정된 속성 `lucene`. 기존 인덱스 유형을 사용한 색인화는 Experience Manager as a Cloud Service으로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정](/help/operations/indexing.md#how-to-use) 추가 정보.

### 사용자 지정 검색 색인 정의 노드에는 시드 라는 속성을 포함할 수 없습니다 {#oakpal-property-name-seed}

* **키**: IndexSeedProperty
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service 사용자 지정 검색 색인 정의(즉, 유형의 노드)를 금지합니다 `oak:QueryIndexDefinition`) 접두사를 사용하지 않습니다. `seed`. 이 속성을 사용한 색인화는 Experience Manager as a Cloud Service으로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 인덱싱](/help/operations/indexing.md#how-to-use) 문서를 참조하십시오.

### 사용자 지정 검색 색인 정의 노드에는 다시 색인이라는 속성을 포함할 수 없습니다 {#oakpal-reindex-property}

* **키**: IndexReindexProperty
* **유형**: 코드 스멜
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service 사용자 지정 검색 색인 정의(즉, 유형의 노드)를 금지합니다 `oak:QueryIndexDefinition`) 접두사를 사용하지 않습니다. `reindex`. 이 속성을 사용한 색인화는 Experience Manager as a Cloud Service으로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 인덱싱](/help/operations/indexing.md#how-to-use) 문서를 참조하십시오.
