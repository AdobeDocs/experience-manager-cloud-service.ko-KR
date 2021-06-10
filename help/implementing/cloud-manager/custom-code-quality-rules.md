---
title: 사용자 지정 코드 품질 규칙 - Cloud Services
description: 사용자 지정 코드 품질 규칙 - Cloud Services
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
source-git-commit: bd9cb35016b91e247f14a851ad195a48ac30fda0
workflow-type: tm+mt
source-wordcount: '3403'
ht-degree: 0%

---

# 사용자 지정 코드 품질 규칙 {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="사용자 지정 코드 품질 규칙"
>abstract="이 페이지에서는 AEM Engineering의 우수 사례를 기반으로 작성된 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에 대해 설명합니다."

이 페이지에서는 AEM Engineering의 우수 사례를 기반으로 작성된 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에 대해 설명합니다.

>[!NOTE]
>여기에 제공된 코드 샘플은 예시적인 용도로만 제공됩니다. SonarQube 개념 및 품질 규칙에 대해 알아보려면 [개념](https://docs.sonarqube.org/7.4/user-guide/concepts/)을 참조하십시오.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 SonarQube 규칙을 강조 표시합니다.

### 위험한 함수 {#do-not-use-potentially-dangerous-functions} 사용 안 함

**키**:CQRules:CWE-676

**유형**:취약성

**심각도**:주요

**다음** 이후:버전 2018.4.0

***Thread.stop()*** 및 ***Thread.interrupt()*** 메서드는 재현할 수 없는 문제와 경우에 따라 보안 취약점이 발생할 수 있습니다. 사용량은 철저하게 모니터링하고 검증되어야 합니다. 일반적으로 메시지 전달은 유사한 목표를 달성하는 더 안전한 방법입니다.

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

### {#do-not-use-format-strings-which-may-be-externally-controlled} 외부에서 제어할 수 있는 형식 문자열을 사용하지 마십시오

**키**:CQRules:CWE-134

**유형**:취약성

**심각도**:주요

**다음** 이후:버전 2018.4.0

외부 소스의 형식 문자열(예: 요청 매개 변수 또는 사용자 생성 컨텐츠)을 사용하면 애플리케이션이 서비스 거부 공격을 받을 수 있습니다. 형식 문자열을 외부에서 제어할 수 있지만 신뢰할 수 있는 소스에서만 허용됩니다.

#### 비호환 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에는 항상 소켓이 있고 연결 시간 초과가 {#http-requests-should-always-have-socket-and-connect-timeouts} 있어야 합니다.

**키**:CQRules:ConnectionTimeoutMechanism

**유형**:버그

**심각도**:중요

**다음** 이후:버전 2018.6.0

AEM 애플리케이션 내에서 HTTP 요청을 실행할 때 불필요한 스레드 사용을 방지하기 위해 적절한 시간 초과가 구성되어 있는지 확인해야 합니다. 안타깝게도, Java의 기본 HTTP 클라이언트(java.net.HttpUrlConnection)와 일반적으로 사용되는 Apache HTTP 구성 요소 클라이언트의 기본 동작은 시간 초과를 하지 않는 것이므로 시간 초과를 명시적으로 설정해야 합니다. 또한 우수 사례로서 이러한 시간 초과는 60초 이내여야 합니다.

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

### ResourceResolver 개체는 항상 {#resourceresolver-objects-should-always-be-closed} 닫아야 합니다.

**키**:CQRules:CQBP-72

**유형**:코드 냄새

**심각도**:주요

**다음** 이후:버전 2018.4.0

ResourceResolverFactory에서 가져온 ResourceResolver 개체는 시스템 리소스를 사용합니다. ResourceResolver를 더 이상 사용하지 않을 때 이러한 리소스를 다시 사용하기 위한 적절한 조치가 있지만 close() 메서드를 호출하여 열려 있는 모든 ResourceResolver 개체를 명시적으로 닫는 것이 더 효율적입니다.

한 가지 비교적 일반적인 오해로는 기존 JCR 세션을 사용하여 만든 ResourceResolver 개체를 명시적으로 닫으면 안 되며, 이렇게 하면 기본 JCR 세션이 닫히게 됩니다. ResourceResolver가 열려 있는 방식에 관계없이 더 이상 사용하지 않을 경우 닫아야 합니다. ResourceResolver는 Closeable 인터페이스를 구현하므로 명시적으로 close()를 호출하는 대신 Try-with-resources 구문을 사용할 수도 있습니다.

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

### Sling 서블릿 경로를 사용하여 서블릿 {#do-not-use-sling-servlet-paths-to-register-servlets}을 등록하지 마십시오

**키**:CQRules:CQBP-75

**유형**:코드 냄새

**심각도**:주요

**다음** 이후:버전 2018.4.0

[Sling 설명서](http://sling.apache.org/documentation/the-sling-engine/servlets.html)에 설명된 대로 경로별 바인딩 서블릿이 중단됩니다. 경로 바인딩된 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으므로 추가 보안 권한이 필요합니다. 경로 바인딩된 서블릿을 사용하는 대신 저장소에서 노드를 만들고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 비호환 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### catch 예외가 기록되거나 throw되어야 하지만 모두 {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**키**:CQRules:CQBP-44—CatchAndEtherLogOrThrow

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

일반적으로 예외는 정확히 한 번만 기록되어야 합니다. 예외를 여러 번 로깅하면 예외가 몇 번 발생했는지 확실하지 않으므로 혼동을 일으킬 수 있습니다. 이를 유도하는 가장 일반적인 패턴은 로깅 및 catch 예외를 throw하는 것입니다.

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

### 즉시 throw 문 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement} 뒤에 로그 문이 오는 것을 방지합니다.

**키**:CQRules:CQBP-44—ContinuousLogAndThrow

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

메시지를 로깅한 다음 즉시 예외를 throw하는 것을 방지하는 또 다른 일반적인 패턴입니다. 일반적으로 이는 예외 메시지가 로그 파일에 복제된다는 것을 나타냅니다.

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

**키**:CQRules:CQBP-44—LogInfoInGetOrHeadRequests

**유형**:코드 냄새

**심각도**:Minor

일반적으로 INFO 로그 수준을 사용하여 중요한 작업을 구분해야 하며 기본적으로 AEM은 INFO 수준 이상으로 로그온하도록 구성되어 있습니다. GET 및 HEAD 방법은 읽기 전용 작업만 수행되어야 하므로 중요한 작업을 구성하지 않습니다. GET 또는 HEAD 요청에 응답하여 INFO 수준에서 로그인하면 상당한 로그 노이즈가 발생할 수 있으므로 로그 파일에서 유용한 정보를 식별하기가 어렵습니다. GET 또는 HEAD 요청을 처리할 때 로깅은 문제가 발생한 경우 WARN 또는 ERROR 수준에서, 또는 문제 해결 정보가 유용할 경우 DEBUG 또는 TRACE 수준에서 로깅해야 합니다.

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

### Exception.getMessage()를 로깅 문 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}의 첫 번째 매개 변수로 사용하지 마십시오

**키**:CQRules:CQBP-44—ExceptionGetMessageIsFirstLogParam

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

로그 메시지는 애플리케이션에서 예외가 발생한 위치에 대한 컨텍스트 정보를 제공하는 것이 좋습니다. 스택 추적을 사용하여 컨텍스트를 결정할 수도 있지만 일반적으로 로그 메시지는 읽고 이해하는 것이 더 쉽습니다. 따라서 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것은 좋지 않습니다. 예외 메시지에는 잘못된 내용이 포함되지만 로그 메시지는 예외 발생 시 응용 프로그램이 수행한 작업을 로그 판독기에 알리는 데 사용해야 합니다. 예외 메시지가 계속 기록됩니다.고유한 메시지를 지정하여 로그를 쉽게 이해할 수 있습니다.

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

### catch 블록에 로그인하는 것은 WARN 또는 ERROR 수준 {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}에 있어야 합니다.

**키**:CQRules:CQBP-44—WrongLogLevelInCatchBlock

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

이름에서 알 수 있듯이 Java 예외는 항상 *예외적인* 상황에서 사용해야 합니다. 따라서 예외가 발생했을 때 로그 메시지가 적절한 수준(WARN 또는 ERROR)에 기록되도록 하는 것이 중요합니다. 이렇게 하면 해당 메시지가 로그에 올바르게 표시됩니다.

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

### 스택 추적을 콘솔 {#do-not-print-stack-traces-to-the-console}에 인쇄하지 마십시오

**키**:CQRules:CQBP-44—ExceptionPrintStackTrace

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

앞에서 설명한 바와 같이, 로그 메시지를 이해할 때는 컨텍스트가 매우 중요합니다. Exception.printStackTrace()를 사용하면 **만**&#x200B;표준 오류 스트림으로 출력되므로 모든 컨텍스트가 손실됩니다. 또한 AEM과 같은 다중 스레드 애플리케이션에서 이 방법을 동시에 사용하여 여러 예외가 인쇄되는 경우 스택 추적이 겹쳐서 상당한 혼동을 일으킬 수 있습니다. 예외는 로깅 프레임워크를 통해서만 로깅해야 합니다.

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

### 표준 출력 또는 표준 오류 {#do-not-output-to-standard-output-or-standard-error}로 출력하지 마십시오.

**키**:CQRules:CQBP-44—LogLevelConsolePrinters

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

AEM에 로그인하는 작업은 항상 로깅 프레임워크(SLF4J)를 통해 수행해야 합니다. 표준 출력 또는 표준 오류 스트림에 직접 출력하면 로깅 프레임워크에서 제공하는 구조적 및 컨텍스트 정보가 손실되며, 경우에 따라 성능 문제가 발생할 수 있습니다.

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

### 하드코딩된 /apps 및 /libs 경로 {#avoid-hardcoded-apps-and-libs-paths} 방지

**키**:CQRules:CQBP-71

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2018.4.0

일반적으로 /libs 및 /apps로 시작하는 경로는 Sling 검색 경로(기본적으로 /libs,/apps로 설정됨)에 상대적인 경로로 가장 일반적으로 저장되므로 하드코딩하지 않아야 합니다. 절대 경로를 사용하면 프로젝트 라이프사이클에서 나중에 나타날 수 있는 미묘한 결함이 발생할 수 있습니다.

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

### Sling 스케줄러는 {#sonarqube-sling-scheduler} 사용할 수 없습니다.

**키**:CQRules:AMSCORE-554

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:Minor

**다음** 이후:버전 2020.5.0

Sling 스케줄러는 보장된 실행을 필요로 하는 작업에 사용해서는 안 됩니다. Sling 예약된 작업은 실행이 보장되며, 클러스터링된 환경과 비클러스터형 환경 모두에 더 적합합니다.

클러스터된 환경에서 Sling 작업을 처리하는 방법에 대한 자세한 내용은 [Apache Sling 이벤트 및 작업 처리](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) 를 참조하십시오.

### AEM에서 더 이상 사용되지 않는 API는 {#sonarqube-aem-deprecated}에 사용해서는 안 됩니다.

**키**:AMSCORE-553

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:Minor

**다음** 이후:버전 2020.5.0

AEM API 서피스는 사용이 중단되어 더 이상 사용되지 않는 API를 식별하기 위해 상수 수정 아래에 있습니다.

대부분의 경우 이러한 API는 표준 Java *@Deprecated* 주석 및 (`squid:CallToDeprecatedMethod`에 의해 식별됨)을 사용하여 더 이상 사용되지 않습니다.

그러나 API는 AEM 컨텍스트에서 더 이상 사용되지 않지만 다른 컨텍스트에서 더 이상 사용되지 않는 경우가 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.


## OakPAL 컨텐츠 규칙 {#oakpal-rules}

Cloud Manager에서 실행되는 OakPAL 검사 아래에 있습니다.

>[!NOTE]
>OakPAL은 AEM 파트너(및 2019 AEM Rockstar North America)에서 개발한 프레임워크로서 독립형 Oak 저장소를 사용하여 컨텐츠 패키지를 검증합니다.

### @ProviderType으로 주석 처리된 제품 API는 고객이 구현하거나 확장하면 안 됩니다 {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**키**:CQBP-84

**유형**:버그

**심각도**:중요

**다음** 이후:버전 2018.7.0

AEM API에는 사용자 지정 코드에 의해서만 사용되지만 구현되지 않는 Java 인터페이스 및 클래스가 포함되어 있습니다. 예를 들어 *com.day.cq.wcm.api.Page* 인터페이스는 ***AEM 전용***&#x200B;에 의해 구현되도록 디자인되었습니다.

이러한 인터페이스에 새 메서드를 추가하면 이러한 추가 메서드가 이러한 인터페이스를 사용하는 기존 코드에 영향을 주지 않으므로 이러한 인터페이스에 새 메서드를 추가하는 것은 이전 버전과 호환되는 것으로 간주됩니다. 그러나 사용자 지정 코드 ***이 이러한 인터페이스 중 하나를 구현하는 경우 해당 사용자 지정 코드가 고객에게 이전 버전과의 호환성 위험을 초래했습니다.***

AEM에서 구현하기 위한 인터페이스(및 클래스)에 *org.osgi.annotation.versioning.ProviderType*(또는 경우에 따라 유사한 이전 주석 *aQute.bnd.annotation.ProviderType*)이 주석 처리되었습니다. 이 규칙은 사용자 지정 코드에 의해 인터페이스가 구현되거나 클래스가 확장된 경우를 식별합니다.

#### 비호환 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 사용자 지정 DAM 자산 Lucene Oak 인덱스가 올바르게 구조화되어 있습니다. {#oakpal-damAssetLucene-sanity-check}

**키**:IndexDamAssetLucene

**유형**:버그

**심각도**:차단기

**다음** 이후:2021.6.0

자산 검색이 AEM Assets에서 올바르게 작동하려면 `damAssetLucene` Oak 색인이 일련의 지침을 따라야 합니다. 이 규칙은 이름이 `damAssetLucene`인 인덱스에 대해 특별히 다음 패턴을 확인합니다.

이름은 여기에 설명된 인덱스 정의 사용자 정의 지침을 따라야 합니다.

* 특히 이름은 `damAssetLucene-<indexNumber>-custom-<customerVersionNumber>` 패턴을 따라야 합니다.

* 인덱스 정의에는 `visualSimilaritySearch` 값을 포함하는 태그라는 여러 값이 있는 속성이 있어야 합니다.

* 인덱스 정의에는 `tika` 하위 노드가 있어야 하며 해당 하위 노드에는 config.xml 이라는 하위 노드가 있어야 합니다.

#### 비호환 코드 {#non-compliant-code-damAssetLucene}

```+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
```

#### 호환 코드 {#compliant-code-damAssetLucene}

```+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - reindexCount: -6952249853801250000
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 고객 패키지는 /libs {#oakpal-customer-package} 아래에 노드를 만들거나 수정해서는 안 됩니다.

**키**:금지된 경로

**유형**:버그

**심각도**:차단기

**다음** 이후:버전 2019.6.0

AEM 컨텐츠 저장소의 /libs 컨텐츠 트리를 고객이 읽기 전용으로 간주해야 하는 것은 오랜 우수 사례입니다. */libs*&#x200B;에서 노드 및 속성을 수정하면 주요 업데이트와 부분 업데이트에 상당한 위험이 생깁니다. */libs*&#x200B;에 대한 수정 사항은 공식 채널을 통해서만 Adobe이 수행해야 합니다.

### 패키지에 중복된 OSGi 구성이 포함되어 있지 않아야 합니다. {#oakpal-package-osgi}

**키**:DuplicateOsgiConfigurations

**유형**:버그

**심각도**:주요

**다음** 이후:버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성된 경우입니다. 이렇게 하면 작동 가능한 구성이 모호해집니다. 이 규칙은 동일한 실행 모드에서 동일한 구성 요소가 여러 번 구성되는(또는 실행 모드의 조합) 문제만 식별한다는 점에서 &quot;실행 모드 인식&quot;입니다.

>[!NOTE]
>이 규칙은 동일한 경로에서 동일한 구성이 여러 패키지에서 정의되는 문제를 발생시킵니다. 여기에는 동일한 패키지가 내장된 패키지의 전체 목록에 중복되는 경우를 포함합니다. 예를 들어 빌드에서 `com.myco:com.myco.ui.apps` 및 `com.myco:com.myco.all` 패키지를 생성하는 경우 여기서 `com.myco:com.myco.all`에 `com.myco:com.myco.ui.apps`이 포함된 경우 `com.myco:com.myco.ui.apps` 내의 모든 구성이 중복으로 보고됩니다. 일반적으로 [컨텐츠 패키지 구조 지침](/help/implementing/developing/introduction/aem-project-content-package-structure.md);을 따르지 않는 경우입니다.이 특정 예제에서 패키지 `com.myco:com.myco.ui.apps`에 `<cloudManagerTarget>none</cloudManagerTarget>` 속성이 없습니다.

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

### 구성 및 설치 폴더에는 OSGi 노드 {#oakpal-config-install}만 포함되어야 합니다.

**키**:ConfigAndInstallShouldOnlyContainOsgiNodes

**유형**:버그

**심각도**:주요

**다음** 이후:버전 2019.6.0

보안상의 이유로 */config/ 및 /install/*&#x200B;이 포함된 경로는 AEM의 관리 사용자만 읽을 수 있으며 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트가 들어 있는 경로에 다른 유형의 컨텐츠를 배치하면 관리 사용자와 비관리 사용자 간에 실수로 변하는 애플리케이션 동작이 발생합니다.

일반적인 문제는 구성 요소 대화 상자 내에서 또는 인라인 편집을 위해 리치 텍스트 편집기 구성을 지정할 때 `config` 라는 노드를 사용하는 것입니다. 이를 해결하려면 해당 노드의 이름을 호환 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 `cq:inplaceEditing` 노드에서 `configPath` 속성을 사용하여 새 위치를 지정합니다.

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

### 패키지는 {#oakpal-no-overlap}과 겹치지 않아야 합니다.

**키**:PackageOverlap

**유형**:버그

**심각도**:주요

**다음** 이후:버전 2019.6.0

*패키지에 중복 OSGi 구성을 포함하지 않아야 합니다.* 과 유사하며, 동일한 노드 경로가 여러 별도의 컨텐츠 패키지로 작성되는 복잡한 프로젝트에서 일반적으로 발생하는 문제입니다. 컨텐츠 패키지 종속성을 사용하여 일관된 결과를 보장할 수 있지만 완전히 겹치지 않는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI {#oakpal-default-authoring}가 아니어야 합니다.

**키**:ClassicUI작성 모드

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:Minor

**다음** 이후:버전 2020.5.0

OSGi 구성 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` 은 AEM 내에서 기본 작성 모드를 정의합니다. 클래식 UI는 AEM 6.4 이후 더 이상 사용되지 않으므로 기본 작성 모드가 클래식 UI로 구성되면 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 Touch UI 대화 상자 {#oakpal-components-dialogs}가 있어야 합니다.

**키**:ComponentWithOnlyClassicUIDialog

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:Minor

**다음** 이후:버전 2020.5.0

클래식 UI 대화 상자가 있는 AEM 구성 요소에는 항상 해당 터치 UI 대화 상자가 있어야 최적의 작성 경험을 제공하고 클래식 UI가 지원되지 않는 Cloud Service 배포 모델과 호환됩니다. 이 규칙은 다음 시나리오를 확인합니다.

* 클래식 UI 대화 상자(대화 상자 하위 노드)가 있는 구성 요소에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 디자인 대화 상자(즉, design_dialog 노드)가 있는 구성 요소에는 해당 터치 UI 디자인 대화 상자(즉, `cq:design_dialog` 하위 노드)가 있어야 합니다.
* 클래식 UI 대화 상자와 클래식 UI 디자인 대화 상자가 모두 있는 구성 요소에는 해당 터치 UI 대화 상자와 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

AEM 현대화 도구 설명서는 구성 요소를 클래식 UI에서 Touch UI로 변환하는 방법에 대한 설명서 및 도구를 제공합니다. 자세한 내용은 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html)를 참조하십시오.

### 패키지는 가변 콘텐츠와 변경할 수 없는 콘텐츠를 혼합하지 않아야 합니다. {#oakpal-packages-immutable}

**키**:가변 가능 혼합 패키지

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:Minor

**다음** 이후:버전 2020.5.0

Cloud Service 배포 모델과 호환하려면 개별 컨텐츠 패키지에 저장소의 변경할 수 없는 영역에 대한 컨텐츠가 포함되어야 합니다(즉, `/apps and /libs, although /libs`은 고객 코드로 수정하면 안 됨) 또는 가변 영역(즉, 다른 모든 것)이 포함되지만 둘 다 포함되지는 않습니다. 예를 들어, `/apps/myco/components/text and /etc/clientlibs/myco`을 모두 포함하는 패키지는 Cloud Service과 호환되지 않으므로 문제가 보고됩니다.

자세한 내용은 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 를 참조하십시오.

### 역방향 복제 에이전트는 {#oakpal-reverse-replication} 사용할 수 없습니다.

**키**:역복제

**유형**:코드 냄새/Cloud Service 호환성

**심각도**:Minor

**다음** 이후:버전 2020.5.0

[릴리스 노트에 설명된 대로 역방향 복제에 대한 지원은 Cloud Service 배포에서 사용할 수 없습니다.복제 에이전트 제거](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#replication-agents).

역방향 복제를 사용하는 고객은 대체 솔루션을 사용하려면 Adobe에 문의해야 합니다.

### OakPAL - 프록시 사용 클라이언트 라이브러리에 포함된 리소스는 {#oakpal-resources-proxy} 리소스라는 폴더에 있어야 합니다.

**키**:ClientlibProxyResource

**유형**:버그

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM 클라이언트 라이브러리에는 이미지 및 글꼴과 같은 정적 리소스가 포함될 수 있습니다. [Prerprocessor 사용](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors)에 설명된 대로, 프록시된 클라이언트 라이브러리를 사용할 때는 게시 인스턴스에서 효과적으로 참조되려면 리소스라는 하위 폴더에 정적 리소스를 포함해야 합니다.

#### 비호환 코드 {#non-compliant-proxy-enabled}

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

### OakPAL - Cloud Service이 호환되지 않는 워크플로우 프로세스 사용 {#oakpal-usage-cloud-service}

**키**:CloudService호환되지 않는 WorkflowProcess

**유형**:버그

**심각도**:주요

**다음** 이후:버전 2021.2.0

AEM Cloud Service의 자산 처리를 위해 Asset Micro-services로 이동하면서 AEM의 온프레미스 및 AMS 버전에서 사용된 여러 워크플로우 프로세스가 지원되지 않거나 필요하지 않게 되었습니다. [aem-cloud-migration](https://github.com/adobe/aem-cloud-migration)의 마이그레이션 도구를 사용하여 AEM Cloud Service 마이그레이션 중에 워크플로우 모델을 업데이트할 수 있습니다.

### OakPAL - 정적 템플릿의 사용이 편집 가능한 템플릿 {#oakpal-static-template} 사용을 중단할 수 없습니다.

**키**:정적 템플릿 사용

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

이전에는 AEM 프로젝트에서 정적 템플릿을 사용하는 것이 매우 일반적이었지만 편집 가능한 템플릿은 정적 템플릿에 없는 가장 유연한 기능을 제공하고 추가 기능을 지원하기 때문에 적극 권장됩니다. 자세한 내용은 [페이지 템플릿을 참조하십시오.](/help/implementing/developing/components/templates.md) 정적 템플릿에서 편집 가능한 템플릿으로 마이그레이션은  [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)를 사용하여 크게 자동화할 수 있습니다.

### OakPAL - 레거시 기초 구성 요소의 사용이 중단되었습니다. {#oakpal-usage-legacy}

**키**:LegacyFoundationComponentUsage

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

기존 기초 구성 요소(즉, `/libs/foundation` 아래의 구성 요소)는 WCM 코어 구성 요소를 위해 여러 AEM 릴리스에서 더 이상 사용되지 않습니다. 오버레이든 상속이든 사용자 지정 구성 요소의 기반으로서 레거시 기초 구성 요소의 사용은 금지되어 있으며 해당 코어 구성 요소로 변환해야 합니다. 이 변환은 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)에서 간편하게 수행할 수 있습니다.

### OakPAL - 지원되는 런타임 모드 이름 및 순서 지정만 {#oakpal-supported-runmodes} 사용해야 합니다.

**키**:지원되는 실행 모드

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service에서는 런타임 모드 이름에 엄격한 이름 지정 정책을 적용하고 이러한 런타임 모드에 대해 엄격한 순서를 지정합니다. 지원되는 실행 모드 목록은 [실행 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)에서 찾을 수 있으며, 이 모드로부터 나온 모든 편차는 문제로 식별됩니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드는 /oak:index {#oakpal-custom-search}의 직접 하위 노드여야 합니다.

**키**:OakIndexLocation

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service을 사용하려면 사용자 지정 검색 색인 정의(즉, oak:QueryIndexDefinition 유형의 노드)가 `/oak:index`의 직접 하위 노드여야 합니다. 다른 위치의 인덱스를 AEM Cloud Service과 호환되도록 이동해야 합니다. 검색 인덱스에 대한 자세한 내용은 [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en)에서 찾을 수 있습니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 comatVersion 2 {#oakpal-custom-search-compatVersion}이 있어야 합니다.

**키**:IndexCompatVersion

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service을 사용하려면 사용자 지정 검색 색인 정의(즉, oak:QueryIndexDefinition 유형의 노드)에 comatVersion 속성이 2로 설정되어 있어야 합니다. 다른 값은 AEM Cloud Service에서 지원되지 않습니다. 검색 인덱스에 대한 자세한 내용은 [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en)에서 찾을 수 있습니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드의 하위 노드는 nt:un구조화되지 않은 {#oakpal-descendent-nodes} 형식이어야 합니다.

**키**:IndexDescendantNodeType

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

사용자 지정 검색 색인 정의 노드에 순서가 없는 하위 노드가 있을 경우 문제를 해결하기 어려울 수 있습니다. 이러한 문제를 방지하려면 `oak:QueryIndexDefinition` 노드의 모든 하위 노드는 nt:unrecrugend 유형이어야 합니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 하위 {#oakpal-custom-search-index}이 있는 indexRules라는 하위 노드가 있어야 합니다.

**키**:IndexRulesNode

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

올바르게 정의된 사용자 지정 검색 색인 정의 노드에는 indexRules라는 하위 노드가 포함되어야 하며, 이 노드에는 하나 이상의 하위 노드가 있어야 합니다. 자세한 내용은 [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html)에 있습니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드는 {#oakpal-custom-search-definitions} 이름 지정 규칙을 따라야 합니다.

**키**:IndexName

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service을 사용하려면 사용자 지정 검색 색인 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)의 이름을 [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)에 설명된 특정 패턴에 따라 지정해야 합니다.

### OakPAL - 사용자 지정 검색 색인 정의 노드는 인덱스 유형 lucene {#oakpal-index-type-lucene} 을 사용해야 합니다.

**키**:인덱스 유형

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service을 사용하려면 사용자 지정 검색 색인 정의(즉, oak:QueryIndexDefinition 유형의 노드)에 값이 **lucene**&#x200B;로 설정된 유형 속성이 있어야 합니다. AEM Cloud Service으로 마이그레이션하기 전에 레거시 인덱스 유형을 사용한 색인화를 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)을 참조하십시오.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 시드 {#oakpal-property-name-seed}라는 속성을 포함할 수 없습니다.

**키**:IndexSeedProperty

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service에서는 사용자 지정 검색 색인 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)가 시드 라는 속성을 포함하지 못하도록 합니다. AEM Cloud Service으로 마이그레이션하기 전에 이 속성을 사용한 색인화를 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)을 참조하십시오.

### OakPAL - 사용자 지정 검색 색인 정의 노드에는 reindex {#oakpal-reindex-property} 라는 속성을 사용할 수 없습니다.

**키**:IndexReindexProperty

**유형**:코드 냄새

**심각도**:Minor

**다음** 이후:버전 2021.2.0

AEM Cloud Service에서는 사용자 지정 검색 색인 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)가 재색인이라는 속성을 포함하지 못하도록 합니다. AEM Cloud Service으로 마이그레이션하기 전에 이 속성을 사용한 색인화를 업데이트해야 합니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use)을 참조하십시오.
