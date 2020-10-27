---
title: 사용자 지정 코드 품질 규칙 - Cloud Services
description: 사용자 지정 코드 품질 규칙 - Cloud Services
translation-type: tm+mt
source-git-commit: 7fdbdd8bfe80d5f87d9917c905c8d04c4c277534
workflow-type: tm+mt
source-wordcount: '2285'
ht-degree: 0%

---


# 사용자 지정 코드 품질 규칙 {#custom-code-quality-rules}


이 페이지에서는 AEM Engineering의 모범 사례를 기반으로 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에 대해 설명합니다.

>[!NOTE]
>여기에 제공된 코드 샘플은 실례만을 위한 것입니다. SonarQube [개념](https://docs.sonarqube.org/7.4/user-guide/concepts/) 및 품질 규칙에 대한 자세한 내용은 개념을 참조하십시오.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 SonarQube 규칙에 대해 설명합니다.

### 위험한 기능 사용 안 함 {#do-not-use-potentially-dangerous-functions}

**키**:CQRules:CWE-676

**유형**:취약점

**심각도**:주요

**이후**:버전 2018.4.0

메서드 ***Thread.stop()*** 및 ***Thread.interrupt()*** 를 사용하면 재현하기 어려운 문제와 보안 취약점이 발생할 수 있습니다. 그들의 사용량은 엄격하게 감시되고 검증되어야 한다. 일반적으로 메시지 전달은 유사한 목표를 달성하는 더 안전한 방법입니다.

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

**키**:CQRules:CWE-134

**유형**:취약점

**심각도**:주요

**이후**:버전 2018.4.0

외부 소스의 형식 문자열(요청 매개 변수 또는 사용자 생성 컨텐츠)을 사용하면 응용 프로그램이 서비스 거부 공격에 노출될 수 있습니다. 형식 문자열이 외부에서 제어될 수 있지만 신뢰할 수 있는 소스에서만 허용되는 경우가 있습니다.

#### 비호환 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에는 항상 소켓 및 연결 시간 초과가 있어야 합니다. {#http-requests-should-always-have-socket-and-connect-timeouts}

**키**:CQRules:ConnectionTimeoutMechanism

**유형**:버그

**심각도**:중요

**이후**:버전 2018.6.0

AEM 응용 프로그램 내에서 HTTP 요청을 실행하는 경우 불필요한 스레드 소비를 방지하기 위해 적절한 시간 초과가 구성되도록 하는 것이 중요합니다. 안타깝게도 Java의 기본 HTTP 클라이언트(java.net.HttpUrlConnection)와 일반적으로 사용되는 Apache HTTP 구성 요소 클라이언트의 기본 동작은 시간 초과를 허용하지 않으므로 시간 초과는 명시적으로 설정해야 합니다. 또한 이러한 시간 제한은 60초를 초과할 수 없습니다.

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

### @ProviderType으로 주석을 단 제품 API는 고객이 구현하거나 확장할 수 없습니다. {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**키**:CQBP-84, CQBP-84-dependencies

**유형**:버그

**심각도**:중요

**이후**:버전 2018.7.0

AEM API에는 사용자 지정 코드로 사용되지만 구현되지 않는 Java 인터페이스 및 클래스가 포함되어 있습니다. 예를 들어 인터페이스 com.day.cq.wcm.api. *Page* 는 ***AEM에서만 구현되도록 디자인되었습니다***.

이러한 인터페이스에 새 메서드가 추가되어도 이러한 추가 메서드는 이러한 인터페이스를 사용하는 기존 코드에 영향을 주지 않으므로 이러한 인터페이스에 새 메서드를 추가하는 것은 역호환으로 간주됩니다. 그러나 사용자 지정 코드가 ***이러한 인터페이스 중 하나를 구현하면*** 해당 사용자 지정 코드에서는 고객에게 이전 버전과의 호환성 위험이 발생하게 됩니다.

AEM에서만 구현되도록 만들어진 인터페이스(및 클래스)에 *org.osgi.annotation.versioning.ProviderType* (또는 유사한 기존 주석 *aQute.bnd.annotation.ProviderType*)으로 주석을 달 수 있습니다. 이 규칙은 인터페이스가 사용자 지정 코드로 구현되거나 클래스가 확장되는 경우를 식별합니다.

#### 비호환 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### ResourceResolver 개체는 항상 닫아야 합니다. {#resourceresolver-objects-should-always-be-closed}

**키**:CQRules:CQBP-72

**유형**:코드 냄새

**심각도**:주요

**이후**:버전 2018.4.0

ResourceResolverFactory에서 가져온 ResourceResolver 개체는 시스템 리소스를 사용합니다. ResourceResolver를 더 이상 사용하지 않을 때 이러한 리소스를 다시 확보하기 위한 조치가 있지만 close() 메서드를 호출하여 열려 있는 모든 ResourceResolver 개체를 명시적으로 닫는 것이 더 효율적입니다.

한 가지 비교적 일반적인 오해는 기존 JCR 세션을 사용하여 만든 ResourceResolver 개체를 명시적으로 닫지 말아야 하거나 닫으면 기본 JCR 세션이 닫힐 수 있다는 것입니다. ResourceResolver를 연 방법에 관계없이 더 이상 사용하지 않을 때 닫아야 합니다. ResourceResolver는 Closed 가능 인터페이스를 구현하므로 명시적으로 close()를 호출하는 대신 try-with-resources 구문을 사용할 수도 있습니다.

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

### Sling 서블릿 경로를 사용하여 서블릿 등록 안 함 {#do-not-use-sling-servlet-paths-to-register-servlets}

**키**:CQRules:CQBP-75

**유형**:코드 냄새

**심각도**:주요

**이후**:버전 2018.4.0

Sling 설명서에 설명된 대로 [경로별 바인딩](http://sling.apache.org/documentation/the-sling-engine/servlets.html)서비스는 비활성화됩니다. 경로 바인딩된 서블릿은 표준 JCR 액세스 컨트롤을 사용할 수 없으므로 추가 보안 권한이 필요합니다. 경로 바인딩된 서블릿을 사용하는 대신 저장소에서 노드를 만들고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 비호환 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Catched Exceptions를 기록하거나 throw해야 하지만 둘 다 해서는 안 됩니다. {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**키**:CQRules:CQBP-44—CatchAndEitorLogOrThrow

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

일반적으로 예외 사항은 정확히 한 번 기록되어야 합니다. 예외를 여러 번 로깅하면 예외가 발생한 횟수가 불분명하므로 혼동을 일으킬 수 있습니다. 이를 이끄는 가장 일반적인 패턴은 벌목과 발견 된 예외를 던지는 것입니다.

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

### 즉시 throw 문이 나오는 로그 문을 사용하지 마십시오 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**키**:CQRules:CQBP-44—ContinuedLogAndThrow

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

메시지를 기록한 다음 즉시 예외를 throw하는 것이 피해야 할 일반적인 패턴입니다. 이는 일반적으로 예외 메시지가 로그 파일에서 중복될 것임을 나타냅니다.

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

### GET 또는 HEAD 요청을 처리할 때 INFO에서 로깅 방지 {#avoid-logging-at-info-when-handling-get-or-head-requests}

**키**:CQRules:CQBP-44—LogInfoInGetOrHeadRequests

**유형**:코드 냄새

**심각도**:마이너

일반적으로 INFO 로그 수준을 사용하여 중요한 작업을 구분해야 하며 기본적으로 AEM은 INFO 수준 이상 수준에서 로그하도록 구성되어 있습니다. GET과 HEAD 방법은 읽기 전용 작업만 되어야 하므로 중요한 작업을 구성하지 않아야 합니다. GET 또는 HEAD 요청에 응답하여 INFO 수준에서 로깅하면 상당한 로그 노이즈가 발생하므로 로그 파일에서 유용한 정보를 식별하기가 어렵습니다. GET 또는 HEAD 요청을 처리할 때 로깅은 문제가 발생한 경우 WARN 또는 ERROR 수준이나, 더 자세한 문제 해결 정보가 도움이 될 경우 DEBUG 또는 TRACE 수준에서 이루어져야 합니다.

>[!CAUTION]
>
>각 요청에 대한 access.log-type 로깅에는 적용되지 않습니다.

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

### 로깅 문의 첫 번째 매개 변수로 Exception.getMessage()를 사용하지 마십시오 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**키**:CQRules:CQBP-44—ExceptionGetMessageIsFirstLogParam

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

로그 메시지는 애플리케이션에서 예외가 발생한 위치에 대한 컨텍스트 정보를 제공하는 것이 좋습니다. 또한 스택 추적 사용을 통해 컨텍스트를 결정할 수 있지만 일반적으로 로그 메시지를 읽고 이해하는 것이 더 쉽습니다. 따라서 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것이 좋습니다. 예외 메시지에는 잘못된 사항이 포함되지만 로그 메시지는 예외 발생 시 애플리케이션이 어떤 작업을 수행했는지 로그 리더에게 알리는 데 사용해야 합니다. 예외 메시지는 여전히 기록됩니다.자신만의 메시지를 지정하면 로그를 쉽게 이해할 수 있습니다.

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

### 캐치 블록에 로그인하는 것은 경고 또는 오류 수준이어야 합니다. {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**키**:CQRules:CQBP-44—WrongLogLevelInCatchBlock

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

이름에서 알 수 있듯이 Java 예외는 항상 *예외적인* 상황에서 사용해야 합니다. 따라서 예외가 발견되면 로그 메시지가 적절한 수준에서 기록되도록(WARN 또는 ERROR) 해야 합니다. 그러면 해당 메시지가 로그에 올바로 표시됩니다.

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

### 콘솔에 스택 추적을 인쇄하지 않음 {#do-not-print-stack-traces-to-the-console}

**키**:CQRules:CQBP-44—ExceptionPrintStackTrace

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

앞에서 언급했듯이, 컨텍스트는 로그 메시지를 이해할 때 중요합니다. Exception.printStackTrace()를 사용하면 **스택 추적만** 표준 오류 스트림으로 출력되므로 모든 컨텍스트가 손실됩니다. 또한 AEM과 같은 다중 스레드 애플리케이션에서 이 방법을 동시에 사용하여 여러 개의 예외가 인쇄되는 경우 스택 추적이 겹칠 수 있으므로 상당한 혼란이 발생할 수 있습니다. 예외 사항은 로깅 프레임워크를 통해서만 기록되어야 합니다.

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

### 표준 출력 또는 표준 오류로 출력하지 않음 {#do-not-output-to-standard-output-or-standard-error}

**키**:CQRules:CQBP-44—LogLevelConsolePrinters

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

AEM에 로그인하는 작업은 항상 로깅 프레임워크(SLF4J)를 통해 수행해야 합니다. 표준 출력 또는 표준 오류 스트림에 직접 출력하면 로깅 프레임워크에서 제공하는 구조적 및 컨텍스트 정보가 손실되며 경우에 따라 성능 문제가 발생할 수 있습니다.

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

**키**:CQRules:CQBP-71

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

일반적으로 /libs 및 /apps로 시작하는 경로는 참조하는 경로로 가장 일반적으로 Sling 검색 경로(기본적으로 /libs,/apps로 설정됨)에 상대적인 경로로 저장되므로 하드코딩하지 않아야 합니다. 절대 경로를 사용하면 프로젝트 수명주기의 후반부에서만 나타날 수 있는 미묘한 결함이 발생할 수 있습니다.

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

### Sling 스케줄러는 사용할 수 없습니다. {#sonarqube-sling-scheduler}

**키**:CQRules:AMSCORE-554

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

Sling 스케줄러는 보장된 실행을 필요로 하는 작업에 사용해서는 안 됩니다. Sling Scheduled Jobs는 실행이 보장되며 클러스터된 환경과 비클러스터형 환경 모두에 더 적합합니다.

클러스터 환경에서 Sling [Jobs가 처리되는 방법에 대한 자세한 내용은 Apache Sling Eventing 및](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) Job Handling을 참조하십시오.

### AEM 더 이상 사용되지 않는 API {#sonarqube-aem-deprecated}

**키**:AMSCORE-553

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

AEM API 표면은 사용이 중단되어 더 이상 사용되지 않는 API를 식별하기 위해 지속적인 개정 하에 있습니다.

대부분의 경우, 이러한 API는 표준 Java *@Deprecated* 주석을 사용하고, 예를 들어, 에 의해 식별된 주석을 사용합니다 `squid:CallToDeprecatedMethod`.

그러나 AEM 컨텍스트에서 API가 더 이상 사용되지 않지만 다른 컨텍스트에서 더 이상 사용되지 않는 경우도 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.

## OakPAL 컨텐츠 규칙 {#oakpal-rules}

Cloud Manager에서 실행되는 OakPAL 검사 아래에서 확인하십시오.

>[!NOTE]
>OakPAL은 AEM 파트너(2019년 AEM Rockstar 북미 우승자)가 개발한 프레임워크로 독립형 Oak 저장소를 사용하여 컨텐츠 패키지를 검증합니다.

### 고객 패키지는 /libs 아래에 노드를 생성하거나 수정해서는 안 됩니다. {#oakpal-customer-package}

**키**:금지된 경로

**유형**:버그

**심각도**:차단기

**이후**:버전 2019.6.0

AEM 컨텐츠 저장소의 /libs 컨텐츠 트리를 고객이 읽기 전용으로 간주해야 하는 것은 오랫동안 모범 사례였습니다. 노드 및 속성을 */libs에서* 수정하면 주요 및 경미한 업데이트에 심각한 위험이 발생합니다. 법률 */법률* 수정 사항은 공식 채널을 통해서만 이루어져야 한다.

### 패키지에 중복된 OSGi 구성이 들어 있으면 안 됩니다. {#oakpal-package-osgi}

**키**:DuplicateOsgiConfigurations

**유형**:버그

**심각도**:주요

**이후**:버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성되는 것입니다. 따라서 작동 가능한 구성이 모호해집니다. 이 규칙은 동일한 런타임 모드(또는 런타임 모드 조합)에서 동일한 구성 요소가 여러 번 구성되는 문제를 식별한다는 점에서 &quot;실행 모드 인식&quot;입니다.

#### 비호환 코드 {#non-compliant-code-osgi}

```+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 호환 코드 {#compliant-code-osgi}

```+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### 구성 및 설치 폴더에는 OSGi 노드만 포함되어야 합니다. {#oakpal-config-install}

**키**:ConfigAndInstallShouldOnlyContainOsgiNodes

**유형**:버그

**심각도**:주요

**이후**:버전 2019.6.0

보안상의 이유로, */config/ 및 /install/* 가 포함된 경로는 AEM의 관리 사용자만 읽을 수 있고 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트가 들어 있는 경로 아래에 다른 유형의 컨텐츠를 배치하면 행정 및 비관리 사용자 간에 의도치 않게 달라지는 애플리케이션 동작이 발생합니다.

일반적인 문제는 구성 요소 대화 상자 `config` 내에 이름이 지정된 노드를 사용하거나 인라인 편집을 위해 리치 텍스트 편집기 구성을 지정할 때 발생합니다. 이 문제를 해결하려면 문제가 있는 노드의 이름을 호환 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 노드의 `configPath` 속성을 사용하여 새 위치를 `cq:inplaceEditing` 지정합니다.

#### 비호환 코드 {#non-compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 호환 코드 {#compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### 패키지가 겹치지 않아야 합니다. {#oakpal-no-overlap}

**키**:PackageOverlays

**유형**:버그

**심각도**:주요

**이후**:버전 2019.6.0

Similar to *Contains Duplicate OSGi Configurations* . Similar this is a common problem on complex projects where the same node path is written to multiple separate content packages. 컨텐츠 패키지 종속성을 사용하여 일관된 결과를 얻을 수 있지만, 완전히 겹치지 않는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI가 아니어야 합니다. {#oakpal-default-authoring}

**키**:ClassicUIAuthauthoringMode

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

OSGi 구성은 AEM 내의 기본 작성 모드를 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` 정의합니다. 클래식 UI는 AEM 6.4부터 사용되지 않으므로 이제 기본 작성 모드가 클래식 UI로 구성되면 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 터치 UI 대화 상자가 있어야 합니다. {#oakpal-components-dialogs}

**키**:ComponentWithOnlyClassicUIDialog

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

클래식 UI 대화 상자가 있는 AEM 구성 요소에는 최적의 작성 환경을 제공하고 클래식 UI가 지원되지 않는 Cloud Service 배포 모델과 호환되도록 항상 해당 터치 UI 대화 상자가 있어야 합니다. 이 규칙은 다음 시나리오를 확인합니다.

* 클래식 UI 대화 상자가 있는 구성 요소(즉, 대화 상자 하위 노드)에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 디자인 대화 상자(즉, design_dialog 노드)가 있는 구성 요소에는 해당 터치 UI 디자인 대화 상자(즉, 하위 노드)가 있어야 `cq:design_dialog` 합니다.
* 클래식 UI 대화 상자와 클래식 UI 디자인 대화 상자를 모두 포함하는 구성 요소에는 해당 터치 UI 대화 상자와 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

AEM 현대화 도구 설명서는 클래식 UI에서 터치 UI로 구성 요소를 변환하는 방법에 대한 설명서 및 도구를 제공합니다. 자세한 [내용은 AEM Modern](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) Tools를 참조하십시오.

### 패키지는 변경 가능한 컨텐츠와 불변경 컨텐츠를 혼합하지 않아야 합니다. {#oakpal-packages-immutable}

**키**:MutableMutableMixedPackage

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

Cloud Service 배포 모델과 호환하려면 개별 컨텐츠 패키지에 저장소의 불변경 영역에 대한 컨텐츠(즉, 고객 코드로 수정해서는 안 `/apps and /libs, although /libs` 되며 별도의 위반이 발생함) 또는 변경 영역(즉, 다른 모든 것)은 포함하되 둘 다 포함해서는 안 됩니다. 예를 들어, 두 패키지 모두 `/apps/myco/components/text and /etc/clientlibs/myco` 가 Cloud Service과 호환되지 않고 문제가 보고됩니다.

Refer to [AEM Project Structure](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) for more details.

### 역방향 복제 에이전트를 사용할 수 없습니다. {#oakpal-reverse-replication}

**키**:ReverseReplication

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

릴리스 노트에 설명된 대로 Cloud Service 배포에서는 역 복제 지원을 사용할 [수 없습니다.복제 에이전트 제거](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#replication-agents).

역방향 복제를 사용하는 고객은 대체 솔루션에 대해 Adobe에 문의해야 합니다.

