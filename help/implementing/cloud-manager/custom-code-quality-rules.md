---
title: 사용자 지정 코드 품질 규칙 - Cloud Services
description: 사용자 지정 코드 품질 규칙 - Cloud Services
translation-type: tm+mt
source-git-commit: 96aa0ef43613e6ae72bf4c454be46329abb19a0c
workflow-type: tm+mt
source-wordcount: '3278'
ht-degree: 0%

---


# 사용자 지정 코드 품질 규칙 {#custom-code-quality-rules}


이 페이지에서는 AEM Engineering의 우수 사례를 기반으로 만들어진 Cloud Manager가 실행하는 사용자 지정 코드 품질 규칙에 대해 설명합니다.

>[!NOTE]
>여기에 제공된 코드 샘플은 실례만을 위한 것입니다. SonarQube 개념 및 품질 규칙에 대해 알려면 [개념](https://docs.sonarqube.org/7.4/user-guide/concepts/)을 참조하십시오.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 SonarQube 규칙에 대해 설명합니다.

### 잠재적으로 위험한 함수 {#do-not-use-potentially-dangerous-functions} 사용 안 함

**키**:CQRules:CWE-676

**유형**:취약성

**심각도**:주요

**이후**:버전 2018.4.0

***Thread.stop()*** 및 ***Thread.interrupt()*** 메서드는 재현하기 어려운 문제를 만들 수 있으며 경우에 따라 보안 취약점도 발생합니다. 사용량은 철저하게 모니터링하고 검증되어야 한다. 일반적으로 메시지 전달은 유사한 목표를 달성하는 더 안전한 방법입니다.

#### 호환되지 않는 코드 {#non-compliant-code}

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

### 외부적으로 제어될 수 있는 형식 문자열을 사용하지 마십시오 {#do-not-use-format-strings-which-may-be-externally-controlled}

**키**:CQRules:CWE-134

**유형**:취약성

**심각도**:주요

**이후**:버전 2018.4.0

요청 매개 변수 또는 사용자 생성 컨텐츠와 같은 외부 소스의 형식 문자열을 사용하면 응용 프로그램을 서비스 거부 공격에 노출할 수 있습니다. 형식 문자열이 외부에서 제어될 수 있지만 신뢰할 수 있는 소스에서만 허용되는 경우가 있습니다.

#### 호환되지 않는 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청은 항상 소켓 및 연결 시간 초과가 {#http-requests-should-always-have-socket-and-connect-timeouts}이어야 합니다.

**키**:CQRules:ConnectionTimeoutMechanism

**유형**:버그

**심각도**:중요

**이후**:버전 2018.6.0

AEM 응용 프로그램 내에서 HTTP 요청을 실행할 때 불필요한 스레드 소비를 방지하기 위해 적절한 시간 초과가 구성되도록 하는 것이 중요합니다. 안타깝게도 Java의 기본 HTTP 클라이언트(java.net.HttpUrlConnection)와 일반적으로 사용되는 Apache HTTP 구성 요소 클라이언트의 기본 동작은 시간 초과를 허용하지 않기 때문에 시간 초과를 명시적으로 설정해야 합니다. 또한 우수 사례로서 이러한 시간 제한은 60초를 초과할 수 없습니다.

#### 호환되지 않는 코드 {#non-compliant-code-2}

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

### @ProviderType으로 주석을 단 제품 API는 고객이 구현하거나 확장하면 안 됩니다. {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**키**:CQBP-84, CQBP-84-종속성

**유형**:버그

**심각도**:중요

**이후**:버전 2018.7.0

AEM API에는 사용자 지정 코드로 사용되어야 하지만 구현되지는 않는 Java 인터페이스와 클래스가 포함되어 있습니다. 예를 들어 *com.day.cq.wcm.api.Page* 인터페이스는 ***AEM 전용***&#x200B;에 의해 구현되도록 디자인되었습니다.

이러한 인터페이스에 새 메서드가 추가되어도 이러한 추가 메서드는 이러한 인터페이스를 사용하는 기존 코드에 영향을 주지 않으며, 그 결과 이러한 인터페이스에 새 메서드를 추가하는 것은 역호환으로 간주됩니다. 그러나 사용자 지정 코드 ***이(가) 이러한 인터페이스 중 하나를 구현하는 경우 해당 사용자 지정 코드가 고객에게 역호환성 위험을 야기했습니다.***

AEM에서만 구현되도록 만들어진 인터페이스(및 클래스)는 *org.osgi.annotation.versioning.ProviderType*(또는 유사한 기존 주석 *aQute.bnd.annotation.ProviderType*)으로 주석을 달 수 있습니다. 이 규칙은 사용자 지정 코드로 인터페이스가 구현되거나 클래스가 확장되는 경우를 식별합니다.

#### 호환되지 않는 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### ResourceResolver 객체는 항상 {#resourceresolver-objects-should-always-be-closed}을(를) 닫아야 합니다.

**키**:CQRules:CQBP-72

**유형**:코드 냄새

**심각도**:주요

**이후**:버전 2018.4.0

ResourceResolverFactory에서 얻은 ResourceResolver 개체는 시스템 리소스를 사용합니다. ResourceResolver를 더 이상 사용하지 않을 때 이러한 리소스를 다시 회수하기 위한 조치가 있지만 close() 메서드를 호출하여 열려 있는 모든 ResourceResolver 객체를 명시적으로 닫는 것이 더 효율적입니다.

한 가지 비교적 일반적인 오해는 기존 JCR 세션을 사용하여 만든 ResourceResolver 객체를 명시적으로 닫지 말아야 하거나 닫으면 기본 JCR 세션이 닫힐 수 있다는 것입니다. ResourceResolver를 연 방법에 관계없이 더 이상 사용하지 않을 때 닫아야 합니다. ResourceResolver는 Closeable 인터페이스를 구현하므로 명시적으로 close()를 호출하지 않고 try-with-resources 구문을 사용할 수도 있습니다.

#### 호환되지 않는 코드 {#non-compliant-code-4}

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

### Sling 서블릿 경로를 사용하여 {#do-not-use-sling-servlet-paths-to-register-servlets} 서블릿 등록 안 함

**키**:CQRules:CQBP-75

**유형**:코드 냄새

**심각도**:주요

**이후**:버전 2018.4.0

[Sling 설명서](http://sling.apache.org/documentation/the-sling-engine/servlets.html)에 설명된 대로 경로별 바인딩 서블릿이 비활성화됩니다. 경로 바인딩된 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으므로 추가 보안 권한이 필요합니다. 경로 바인딩된 서블릿을 사용하는 대신 저장소에서 노드를 만들고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 호환되지 않는 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### catch Exceptions는 기록되거나 throw되어야 하지만 둘 다 {#caught-exceptions-should-be-logged-or-thrown-but-not-both}은(는) 아닙니다.

**키**:CQRules:CQBP-44—CatchAndEitorLogOrThrow

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

일반적으로 예외 사항을 한 번만 기록해야 합니다. 예외 사항을 여러 번 기록하면 예외가 발생한 횟수가 명확하지 않아 혼동을 일으킬 수 있습니다. 이를 유도하는 가장 일반적인 패턴은 벌목과 catch 된 예외를 throw하는 것입니다.

#### 호환되지 않는 코드 {#non-compliant-code-6}

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

### 즉시 throw 문 다음에 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement} throw 문이 나오는 것을 피하십시오.

**키**:CQRules:CQBP-44—ContinuousLogAndThrow

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

메시지를 기록한 다음 즉시 예외를 throw하는 것이 피해야 할 일반적인 패턴입니다. 이는 일반적으로 예외 메시지가 로그 파일에 중복될 수 있음을 나타냅니다.

#### 호환되지 않는 코드 {#non-compliant-code-7}

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

일반적으로 INFO 로그 수준은 중요한 작업을 구분하는 데 사용해야 하며, 기본적으로 AEM은 INFO 수준 이상으로 로깅하도록 구성되어 있습니다. GET 및 HEAD 방법은 읽기 전용 작업이어야 하므로 중요한 작업을 구성하지 않아야 합니다. GET 또는 HEAD 요청에 대한 응답으로 INFO 수준에서 기록하면 상당한 로그 노이즈가 발생하여 로그 파일에서 유용한 정보를 식별하기가 어렵습니다. GET 또는 HEAD 요청을 처리할 때 로깅은 문제가 발생한 경우 WARN 또는 ERROR 수준에 있어야 하며, 더 자세한 문제 해결 정보가 유용할 경우 DEBUG 또는 TRACE 수준에 있어야 합니다.

>[!CAUTION]
>
>각 요청에 대한 access.log-type 로깅에는 적용되지 않습니다.

#### 호환되지 않는 코드 {#non-compliant-code-8}

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

### Exception.getMessage()를 로깅 문 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}의 첫 번째 매개 변수로 사용하지 마십시오.

**키**:CQRules:CQBP-44—ExceptionGetMessageIsFirstLogParam

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

로그 메시지는 애플리케이션에서 예외가 발생한 위치에 대한 컨텍스트 정보를 제공하는 것이 좋습니다. 스택 추적을 사용하여 컨텍스트를 결정할 수도 있지만 일반적으로 로그 메시지를 읽고 이해하는 것이 더 쉽습니다. 따라서 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것은 좋지 않습니다. 예외 메시지에는 잘못된 사항이 포함되지만 로그 메시지를 사용하여 예외 발생 시 애플리케이션이 어떤 작업을 수행했는지 로그 리더에게 알려야 합니다. 예외 메시지는 여전히 기록됩니다.고유한 메시지를 지정하면 로그를 쉽게 이해할 수 있습니다.

#### 호환되지 않는 코드 {#non-compliant-code-9}

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

### catch 블록에 로그인하는 것은 WARN 또는 ERROR 수준 {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}이어야 합니다.

**키**:CQRules:CQBP-44—WrongLogLevelInCatchBlock

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

이름에서 알 수 있듯이 Java 예외는 항상 *예외적인* 환경에서 사용해야 합니다. 따라서 예외가 발견되면 로그 메시지가 적절한 수준(WARN 또는 ERROR)에 기록되도록 하는 것이 중요합니다. 그러면 해당 메시지가 로그에 올바로 표시됩니다.

#### 호환되지 않는 코드 {#non-compliant-code-10}

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

### 콘솔 {#do-not-print-stack-traces-to-the-console}에 스택 추적을 인쇄하지 마십시오.

**키**:CQRules:CQBP-44—ExceptionPrintStackTrace

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

앞에서 언급했듯이, 컨텍스트는 로그 메시지를 이해할 때 매우 중요합니다. Exception.printStackTrace()를 사용하면 **만** 스택 추적이 표준 오류 스트림으로 출력되어 모든 컨텍스트를 잃게 됩니다. 또한 AEM과 같은 다중 스레드 응용 프로그램에서 이 방법을 동시에 사용하여 여러 예외가 인쇄되는 경우 스택 추적이 겹칠 수 있어 상당한 혼란이 발생할 수 있습니다. 예외는 로깅 프레임워크를 통해서만 기록되어야 합니다.

#### 호환되지 않는 코드 {#non-compliant-code-11}

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

### 표준 출력 또는 표준 오류 {#do-not-output-to-standard-output-or-standard-error}로 출력하지 마십시오.

**키**:CQRules:CQBP-44—LogLevelConsolePrinters

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

AEM에 로그인하는 작업은 항상 로깅 프레임워크(SLF4J)를 통해 수행해야 합니다. 표준 출력 또는 표준 오류 스트림에 직접 출력하면 로깅 프레임워크에서 제공하는 구조적 및 상황에 맞는 정보가 손실되며 경우에 따라 성능 문제가 발생할 수 있습니다.

#### 호환되지 않는 코드 {#non-compliant-code-12}

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

### 하드 코딩된 /apps 및 /libs 경로 {#avoid-hardcoded-apps-and-libs-paths} 방지

**키**:CQRules:CQBP-71

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2018.4.0

일반적으로 /libs 및 /apps로 시작하는 경로는 Sling 검색 경로(기본적으로 /libs,/apps로 설정됨)에 상대적인 경로로 가장 일반적으로 저장되므로 하드코딩하지 않아야 합니다. 절대 경로를 사용하면 프로젝트 라이프사이클에서 나중에 나타날 수 있는 미묘한 결함이 발생할 수 있습니다.

#### 호환되지 않는 코드 {#non-compliant-code-13}

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

Sling 스케줄러는 보장된 실행을 필요로 하는 작업에 사용해서는 안 됩니다. Sling Scheduled Jobs는 실행을 보장하며 클러스터된 환경과 비클러스터형 환경 모두에 더 적합합니다.

클러스터 환경에서 Sling 작업이 처리되는 방법에 대한 자세한 내용은 [Apache Sling 이벤트 및 작업 처리](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html)를 참조하십시오.

### AEM 가치 하락 API를 {#sonarqube-aem-deprecated} 사용할 수 없습니다.

**키**:AMSCORE-553

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

AEM API 표면은 사용이 중단되어 더 이상 사용되지 않는 API를 식별하기 위해 지속적인 개정 하에 있습니다.

대부분의 경우, 이러한 API는 표준 Java *@Deprecated* 주석과 `squid:CallToDeprecatedMethod`에 의해 식별되는 것과 같이 더 이상 사용되지 않습니다.

그러나 AEM 컨텍스트에서 API를 사용하지 않지만 다른 컨텍스트에서 더 이상 사용할 수 없는 경우도 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.

## OakPAL 컨텐츠 규칙 {#oakpal-rules}

Cloud Manager에서 실행되는 OakPAL 검사 아래에서 확인할 수 있습니다.

>[!NOTE]
>OakPAL은 AEM 파트너(2019년 AEM Rockstar 북미 우승자)가 개발한 프레임워크로 독립형 Oak 저장소를 사용하여 컨텐츠 패키지를 검증합니다.

### 고객 패키지는 /libs {#oakpal-customer-package} 아래에 노드를 만들거나 수정해서는 안됩니다.

**키**:금지된 경로

**유형**:버그

**심각도**:차단기

**이후**:버전 2019.6.0

AEM 컨텐츠 저장소의 /libs 컨텐츠 트리를 고객이 읽기 전용으로 간주하는 것은 오랜 우수 사례입니다. */libs*&#x200B;에서 노드 및 속성을 수정하면 주요 및 부 업데이트에 심각한 위험이 발생합니다. */libs*&#x200B;의 수정 사항은 공식 채널을 통해 Adobe에 의해서만 이루어져야 합니다.

### 패키지에는 중복된 OSGi 구성이 들어 있지 않아야 합니다 {#oakpal-package-osgi}.

**키**:DuplicateOsgiConfiguration

**유형**:버그

**심각도**:주요

**이후**:버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성되는 것입니다. 따라서 작동 가능한 구성에 대한 모호성이 만들어집니다. 이 규칙은 동일한 런타임 모드(또는 런타임 모드 조합)에서 동일한 구성 요소가 여러 번 구성되는 문제를 식별한다는 점에서 &quot;실행 모드 인식&quot;입니다.

>[!NOTE]
>이 규칙은 동일한 경로에서 동일한 구성이 여러 패키지에서 정의되는 문제를 발생시킵니다. 예를 들어 동일한 패키지가 전체 기본 패키지 목록에 중복되는 경우도 있습니다. 예를 들어 빌드가 `com.myco:com.myco.ui.apps` 및 `com.myco:com.myco.all`이라는 패키지를 생성하는 경우 `com.myco:com.myco.all`에 `com.myco:com.myco.ui.apps`이(가) 포함된 경우 `com.myco:com.myco.ui.apps` 내의 모든 구성이 중복으로 보고됩니다. 이는 일반적으로 [컨텐트 패키지 구조 지침](/help/implementing/developing/aem-project-content-package-structure.md);을 따르지 않는 경우입니다.이 예제에서 패키지 `com.myco:com.myco.ui.apps`에 `<cloudManagerTarget>none</cloudManagerTarget>` 속성이 없습니다.

#### 호환되지 않는 코드 {#non-compliant-code-osgi}

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

### 구성 및 설치 폴더에는 OSGi 노드 {#oakpal-config-install}만 포함되어야 합니다.

**키**:ConfigAndInstallShouldOnlyContainOsgiNodes

**유형**:버그

**심각도**:주요

**이후**:버전 2019.6.0

보안상의 이유로 */config/ 및 /install/*&#x200B;을 포함하는 경로는 AEM의 관리 사용자만 읽을 수 있고 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트가 들어 있는 경로 아래에 다른 유형의 컨텐츠를 배치하면 의도치 않게 관리 사용자와 비관리 사용자 간에 달라지는 애플리케이션 동작이 발생합니다.

일반적인 문제는 구성 요소 대화 상자 내에 `config`이라는 노드를 사용하거나 인라인 편집을 위해 리치 텍스트 편집기 구성을 지정할 때 사용합니다. 이 문제를 해결하려면 문제가 있는 노드의 이름을 호환 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 `cq:inplaceEditing` 노드의 `configPath` 속성을 사용하여 새 위치를 지정합니다.

#### 호환되지 않는 코드 {#non-compliant-code-config-install}

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

### 패키지는 {#oakpal-no-overlap}과(와) 겹치지 않아야 합니다.

**키**:PackageOverlays

**유형**:버그

**심각도**:주요

**이후**:버전 2019.6.0

동일한 노드 경로가 여러 별도의 컨텐츠 패키지로 작성되는 복잡한 프로젝트에서 일반적으로 발생하는 문제입니다. 이 문제는 *패키지에 중복 OSGi 구성을 포함하지 않아야 합니다*. 컨텐츠 패키지 종속성을 사용하여 일관된 결과를 얻을 수 있지만, 완전히 겹치지 않는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI {#oakpal-default-authoring}이어야 합니다.

**키**:ClassicUIAuthauthoringMode

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

OSGi 구성 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl`은 AEM 내의 기본 작성 모드를 정의합니다. 클래식 UI는 AEM 6.4부터 사용되지 않으므로 이제 기본 작성 모드가 클래식 UI로 구성되면 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 터치 UI 대화 상자 {#oakpal-components-dialogs}가 있어야 합니다.

**키**:ComponentWithOnlyClassicUIDialog

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

클래식 UI 대화 상자가 있는 AEM 구성 요소에는 최적의 작성 환경을 제공하고 클래식 UI가 지원되지 않는 Cloud Service 배포 모델과 호환되도록 항상 해당 터치 UI 대화 상자가 있어야 합니다. 이 규칙은 다음 시나리오를 확인합니다.

* 클래식 UI 대화 상자를 사용하는 구성 요소(즉, 대화 상자 하위 노드)에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 디자인 대화 상자(즉, design_dialog 노드)가 있는 구성 요소에는 해당 터치 UI 디자인 대화 상자(즉, `cq:design_dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 대화 상자와 클래식 UI 디자인 대화 상자를 모두 포함하는 구성 요소에는 해당 터치 UI 대화 상자와 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

AEM 현대화 도구 설명서는 클래식 UI에서 터치 UI로 구성 요소를 변환하는 방법에 대한 설명서 및 도구를 제공합니다. 자세한 내용은 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html)를 참조하십시오.

### 패키지는 변경할 수 없는 콘텐츠와 변경할 수 없는 콘텐츠를 혼합해서는 안 됩니다. {#oakpal-packages-immutable}

**키**:ImmutableMutableMixedPackage

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

Cloud Service 배포 모델과 호환하려면 개별 컨텐츠 패키지에 저장소의 변경 불가능한 영역에 대한 컨텐츠(즉, `/apps and /libs, although /libs`은(는) 고객 코드로 수정해서는 안 되며 별도의 위반이 발생함) 또는 변경 가능 영역(즉, 다른 모든 것)은 포함하지만 둘 다 포함해서는 안됩니다. 예를 들어, `/apps/myco/components/text and /etc/clientlibs/myco`을 모두 포함하는 패키지는 Cloud Service과 호환하지 않으며 문제가 보고됩니다.

자세한 내용은 [AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)를 참조하십시오.

### 역방향 복제 에이전트를 사용할 수 없습니다. {#oakpal-reverse-replication}

**키**:ReverseReplication

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:마이너

**이후**:버전 2020.5.0

[릴리스 노트에 설명된 대로 Cloud Service 배포에서는 역방향 복제 지원을 사용할 수 없습니다.복제 에이전트 제거](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#replication-agents).

역방향 복제를 사용하는 고객은 대체 솔루션에 대해 Adobe에 문의해야 합니다.

### OakPAL - 프록시 사용 클라이언트 라이브러리에 포함된 리소스는 리소스 {#oakpal-resources-proxy} 폴더에 있어야 합니다.

**키**:ClientlibProxyResource

**유형**:버그

**심각도**:마이너

**이후**:버전 2021.2.0

AEM 클라이언트 라이브러리에는 이미지 및 글꼴과 같은 정적 리소스가 포함될 수 있습니다. [프리프로세서 사용](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors)에 설명된 대로, 프록시 클라이언트 라이브러리를 사용할 때에는 정적 리소스를 리소스라는 하위 폴더에 포함해야 게시 인스턴스에서 효과적으로 참조됩니다.

#### 호환되지 않는 코드 {#non-compliant-proxy-enabled}

```
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 호환 코드 {#compliant-proxy-enabled}

```
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### OakPAL - 호환되지 않는 Cloud Service 워크플로 프로세스 사용 {#oakpal-usage-cloud-service}

**키**:CloudServiceIncompatibleWorkflowProcess

**유형**:버그

**심각도**:주요

**이후**:버전 2021.2.0

AEM Cloud Service에서 자산 처리를 위해 Asset Micro-services로 이동하면 AEM의 온-프레미스 및 AMS 버전에서 사용된 여러 워크플로우 프로세스가 지원되지 않거나 불필요하게 되었습니다. [aem-cloud-migration](https://github.com/adobe/aem-cloud-migration)의 마이그레이션 도구를 사용하여 AEM Cloud Service 마이그레이션 동안 워크플로우 모델을 업데이트할 수 있습니다.

### OakPAL - 편집 가능한 템플릿 대신 정적 템플릿 사용 안 함 {#oakpal-static-template}

**키**:StaticTemplateUsage

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

정적 템플릿은 AEM 프로젝트에서 일반적으로 사용되지만 편집 가능한 템플릿은 가장 유연하게 제공하고 정적 템플릿에 없는 추가 기능을 지원하기 때문에 권장됩니다. 자세한 내용은 [페이지 템플릿을 참조하십시오.](/help/implementing/developing/components/templates.md) 정적인 템플릿과 편집 가능한 템플릿에 대한 마이그레이션은  [AEM 현대화 툴을 사용하여 대부분 자동화할 수 있습니다](https://opensource.adobe.com/aem-modernize-tools/).

### OakPAL - 레거시 기초 구성 요소의 사용이 거부됨 {#oakpal-usage-legacy}

**키**:LegacyFoundationComponentUsage

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

이전 기본 구성 요소(즉, `/libs/foundation` 아래의 구성 요소)는 WCM 핵심 구성 요소를 선호하는 여러 AEM 릴리스에서 더 이상 사용되지 않습니다. 오버레이 또는 상속을 통해 사용자 지정 구성 요소의 기초로 기존 기본 구성 요소를 사용하는 것은 거절되며 해당 핵심 구성 요소로 변환해야 합니다. 이 변환은 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)에서 용이하게 할 수 있습니다.

### OakPAL - 지원되는 런타임 모드 이름 및 주문만 {#oakpal-supported-runmodes} 사용

**키**:SupportedRunmode

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service은 런타임 모드 이름에 대해 엄격한 이름 지정 정책을 적용하고 이러한 런타임 모드에 대해서는 엄격한 순서를 따릅니다. 지원되는 런타임 모드 목록은 [Runmodes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)에서 찾을 수 있으며, 이와 다른 부분은 문제로 식별됩니다.

### OakPAL - 사용자 정의 검색 색인 정의 노드는 /oak:index {#oakpal-custom-search}의 직접 자식이어야 합니다.

**키**:OakIndexLocation

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service에서는 사용자 정의 검색 색인 정의(예: oak:QueryIndexDefinition 유형의 노드)가 `/oak:index`의 직접 하위 노드여야 합니다. 다른 위치의 색인은 AEM Cloud Service과 호환되도록 이동해야 합니다. 검색 색인에 대한 자세한 내용은 [콘텐츠 검색 및 인덱싱](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en)을 참조하십시오.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 2의 comatVersion {#oakpal-custom-search-compatVersion}이(가) 있어야 합니다.

**키**:IndexCompatVersion

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service에서는 사용자 정의 검색 색인 정의(예: oak:QueryIndexDefinition 유형의 노드)에 comatVersion 속성이 2로 설정되어 있어야 합니다. 다른 값은 AEM Cloud Service에서 지원되지 않습니다. 검색 색인에 대한 자세한 내용은 [콘텐츠 검색 및 인덱싱](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en)을 참조하십시오.

### OakPAL - 사용자 지정 검색 인덱스 정의 노드의 하위 노드는 nt:unstructured {#oakpal-descendent-nodes} 유형이어야 합니다.

**키**:IndexDescendantNodeType

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

사용자 지정 검색 색인 정의 노드에 순서가 없는 하위 노드가 있으면 문제를 해결하기 어려울 수 있습니다. 이를 방지하려면 `oak:QueryIndexDefinition` 노드의 모든 하위 노드 유형이 nt:unstructured인 것이 좋습니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 {#oakpal-custom-search-index} 하위 노드가 있는 indexRules라는 하위 노드가 있어야 합니다.

**키**:IndexRulesNode

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

올바르게 정의된 사용자 지정 검색 색인 정의 노드에는 indexRules라는 하위 노드가 있어야 하며, 그 다음 노드에는 1개 이상의 하위 노드가 있어야 합니다. 자세한 내용은 [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html)에서 확인할 수 있습니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드는 이름 지정 규칙 {#oakpal-custom-search-definitions}을 따라야 합니다.

**키**:IndexName

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service은 사용자 정의 검색 색인 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)를 [컨텐트 검색 및 인덱싱](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)에 설명된 특정 패턴에 따라 이름을 지정해야 합니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드는 인덱스 유형 lucene {#oakpal-index-type-lucene} 을 사용해야 합니다.

**키**:IndexType

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service에는 사용자 정의 검색 색인 정의(예: oak:QueryIndexDefinition 유형의 노드)에 값이 **lucene**&#x200B;으로 설정된 type 속성이 있어야 합니다. AEM Cloud Service으로 마이그레이션하기 전에 기존 색인 유형을 사용한 인덱싱을 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 인덱싱](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)을 참조하십시오.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 시드 {#oakpal-property-name-seed}이라는 속성을 포함할 수 없습니다.

**키**:IndexSeedProperty

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service에서는 사용자 정의 검색 색인 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)가 seed라는 속성을 포함하지 못하도록 합니다. AEM Cloud Service으로 마이그레이션하기 전에 이 속성을 사용한 인덱싱을 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 인덱싱](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)을 참조하십시오.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 reindex {#oakpal-reindex-property}이라는 속성이 포함되지 않아야 합니다.

**키**:IndexReindexProperty

**유형**:코드 냄새

**심각도**:마이너

**이후**:버전 2021.2.0

AEM Cloud Service에서는 사용자 정의 검색 색인 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)가 reindex라는 속성을 포함하지 못하도록 합니다. AEM Cloud Service으로 마이그레이션하기 전에 이 속성을 사용한 인덱싱을 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 인덱싱](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)을 참조하십시오.






