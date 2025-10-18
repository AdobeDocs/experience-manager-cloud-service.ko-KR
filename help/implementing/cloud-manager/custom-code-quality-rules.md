---
title: 사용자 정의 코드 품질 규칙
description: 철저한 테스트를 통한 고품질 코드를 보장하기 위해 Adobe Experience Manager 엔지니어링 모범 사례를 기반으로 하는 Cloud Manager의 사용자 정의 코드 품질 규칙에 대해 알아보십시오.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 62e4b038c3fbae0ca5b6bb08c1d9d245842aeab2
workflow-type: tm+mt
source-wordcount: '4349'
ht-degree: 64%

---

# 사용자 정의 코드 품질 규칙 {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="사용자 정의 코드 품질 규칙"
>abstract="철저한 테스트를 통한 고품질 코드를 보장하기 위해 Adobe Experience Manager 엔지니어링 모범 사례를 기반으로 하는 Cloud Manager의 사용자 정의 코드 품질 규칙에 대해 알아보십시오."

철저한 테스트를 통해 고품질 코드를 보장하기 위해 Adobe Experience Manager 엔지니어링 모범 사례를 기반으로 하는 Cloud Manager의 사용자 지정 코드 품질 규칙에 대해 알아봅니다. [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)도 참조하세요.

전체 SonarQube 규칙은 Adobe 독점 정보로 인해 다운로드할 수 없습니다. *현재* 규칙 전체 목록을 [이 링크를 사용하여](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx)다운로드할 수 있습니다. 규칙에 대한 설명과 예를 보려면 이 문서를 계속 읽어 보십시오.

>[!IMPORTANT]
>
>2025년 2월 13일 목요일(Cloud Manager 2025.2.0)부터 Cloud Manager 코드 품질은 업데이트된 SonarQube 9.9 버전과 [여기에서 다운로드](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS-2024-12-0.xlsx)할 수 있는 업데이트된 규칙 목록을 사용합니다.

>[!NOTE]
>
>여기에 제공된 코드 샘플은 설명 목적으로만 제공됩니다. SonarQube 개념 및 품질 규칙에 대한 자세한 내용은 SonarQube [개념 설명서](https://docs.sonarsource.com/sonarqube/latest/)를 참조하십시오.

## SonarQube 규칙 {#sonarqube-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 SonarQube 규칙에 대해 자세히 설명합니다.

### 잠재적으로 위험한 기능을 사용하지 않음 {#do-not-use-potentially-dangerous-functions}

* **키**: CQRules:CWE-676
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

`Thread.stop()` 및 `Thread.interrupt()` 메서드는 재현하기 어려운 문제와 경우에 따라 보안 취약성을 발생시킬 수 있습니다. 이러한 사용은 철저하게 모니터링되고 검증되어야 합니다. 일반적으로 메시지 전달은 유사한 목표를 달성하기 위한 보다 안전한 방법입니다.

#### 비준수 코드 {#non-compliant-code}

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

#### 준수 코드 {#compliant-code}

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

### 외부에서 제어할 수 있는 형식 문자열을 사용하지 않음 {#do-not-use-format-strings-which-may-be-externally-controlled}

* **키**: CQRules:CWE-134
* **유형**: 취약성
* **심각도**: 주요
* **이후**: 버전 2018.4.0

외부 소스의 형식 문자열(예: 요청 매개변수 또는 사용자 생성 콘텐츠)을 사용하면 애플리케이션이 서비스 거부 공격에 노출될 수 있습니다. 형식 문자열이 외부에서 제어될 수 있지만 신뢰할 수 있는 소스에서만 허용되는 환경이 있습니다.

#### 비준수 코드 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 요청에 항상 소켓 및 연결 시간 초과가 포함되어 있어야 함 {#http-requests-should-always-have-socket-and-connect-timeouts}

* **키**: CQRules:ConnectionTimeoutMechanism
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2018.6.0

Experience Manager 애플리케이션 내에서 HTTP 요청을 할 때는 불필요한 스레드 소비를 방지하기 위해 적절한 시간 초과를 구성해야 합니다.
기본적으로 Java™ HTTP 클라이언트(java.net.HttpUrlConnection)와 널리 사용되는 Apache HTTP 구성 요소 클라이언트는 모두 시간 초과를 적용하지 않으므로 수동으로 구성해야 합니다. 시간 초과는 60초 이하로 설정하는 것이 좋습니다.

#### 비준수 코드 {#non-compliant-code-2}

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

#### 준수 코드 {#compliant-code-1}

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

public void orDoThis () {
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

### 항상 ResourceResolver 오브젝트를 닫아야 함 {#resourceresolver-objects-should-always-be-closed}

* **키**: CQRules:CQBP-72
* **유형**: `Code Smell`
* **심각도**: 주요
* **이후**: 버전 2018.4.0

`ResourceResolverFactory`에서 가져온 ResourceResolver 개체는 시스템 리소스를 사용합니다. `ResourceResolver`가 더 이상 사용되지 않을 때 이러한 리소스를 회수하는 방법이 있지만 `close()` 메서드를 호출하여 열려 있는 `ResourceResolver` 오브젝트를 명시적으로 닫는 것이 더 효율적입니다.

일반적인 오해 중 하나는 기존 JCR 세션으로 만든 `ResourceResolver` 개체를 명시적으로 닫지 말아야 하거나 닫으면 JCR 세션에 영향을 준다는 것입니다. 이 정보는 올바르지 않습니다. `ResourceResolver`은(는) 더 이상 필요하지 않으면 항상 닫아야 합니다. `ResourceResolver`이(가) `Closeable` 인터페이스를 구현하므로 `try-with-resources`을(를) 직접 호출하는 대신 `close()` 구문을 사용할 수도 있습니다.

#### 비준수 코드 {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### 준수 코드 {#compliant-code-2}

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

### Sling 서블릿 경로를 사용하여 서블릿을 등록하지 않음 {#do-not-use-sling-servlet-paths-to-register-servlets}

* **키**: CQRules:CQBP-75
* **유형**: `Code Smell`
* **심각도**: 주요
* **이후**: 버전 2018.4.0

[`Sling` 설명서](https://sling.apache.org/documentation/the-sling-engine/servlets.html)에 설명된 대로 경로별로 서블릿을 바인딩하는 것은 권장되지 않습니다. 경로 바인딩 서블릿은 표준 JCR 액세스 제어를 사용할 수 없으며, 결과적으로 엄격한 추가 보안이 요구됩니다. 경로 바인딩 서블릿을 사용하는 대신 저장소에 노드를 생성하고 리소스 유형별로 서블릿을 등록하는 것이 좋습니다.

#### 비준수 코드 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### 발견된 예외를 기록하거나 표시하되 둘 다 해서는 안 됨 {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **키**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

일반적으로 예외는 정확히 한 번 기록해야 합니다. 예외를 여러 번 기록하면 혼동이 발생할 수 있습니다. 예외가 몇 번 발생했는지 불분명하기 때문이다. 이 효과로 이어지는 가장 일반적인 패턴은 발생한 예외를 로깅하고 throw하는 것입니다.

#### 비준수 코드 {#non-compliant-code-6}

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

#### 준수 코드 {#compliant-code-3}

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

### Throw 문 바로 뒤에 Log 문을 사용하지 않음 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **키**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

피해야 할 또 다른 일반적인 패턴은 메시지를 기록한 다음 즉시 예외를 발생시키는 것입니다. 이러한 사례는 일반적으로 예외 메시지가 로그 파일에 중복됨을 나타냅니다.

#### 비준수 코드 {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### 준수 코드 {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### GET 또는 HEAD 요청을 처리할 때 INFO에서 로깅하지 않음 {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **키**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **유형**: `Code Smell`
* **심각도**: 사소

일반적으로 INFO 로그 수준은 중요한 작업을 구분하는 데 사용되어야 하며 기본적으로 Experience Manager는 INFO 수준 또는 그 이상에서 기록되도록 구성됩니다. GET 및 HEAD 메서드는 읽기 전용 작업이어야 하므로 중요한 작업을 구성하지 않습니다. GET 또는 HEAD 요청에 대한 응답으로 INFO 수준에서 로깅하면 상당한 로그 노이즈가 발생하여 로그 파일에서 유용한 정보를 식별하기가 더 어려워질 수 있습니다. GET 또는 HEAD 요청을 처리할 때 문제가 발생하면 WARN 또는 ERROR 수준에서 기록합니다. 자세한 문제 해결 정보가 필요한 경우 디버그 또는 TRACE 수준을 사용합니다.

>[!NOTE]
>
>각 요청에 대해 `access.log` 형식의 로깅에는 적용되지 않습니다.

#### 비준수 코드 {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### 준수 코드 {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Logging 문의 첫 번째 매개변수로 Exception.getMessage()를 사용하지 않음 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **키**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

가장 좋은 방법은 로그 메시지가 애플리케이션에서 예외가 발생한 위치에 대한 상황별 정보를 제공하는 것입니다. 스택 추적을 사용하여 컨텍스트를 결정할 수도 있지만 일반적으로 로그 메시지는 읽고 이해하는 것이 더 쉬울 것입니다. 따라서 예외를 기록할 때 예외 메시지를 로그 메시지로 사용하는 것은 잘못된 관행입니다. 예외 메시지는 무엇이 잘못되었는지 설명하지만, 로그 메시지는 예외 발생 시 애플리케이션이 무엇을 하고 있었는지에 대해 판독기에 알려주어야 합니다. 예외 메시지는 계속 기록됩니다. 고유한 메시지를 지정하면 로그를 쉽게 이해할 수 있습니다.

#### 비준수 코드 {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### 준수 코드 {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Catch 블록에 로그인할 때 WARN 또는 ERROR 수준을 유지해야 함 {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **키**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

이름에서 알 수 있듯이 Java™ 예외는 예외적인 상황에서 항상 사용되어야 합니다. 결과적으로 예외가 발생하면 로그 메시지가 WARN 또는 ERROR 중 적절한 수준으로 기록되도록 하는 것이 중요합니다. 이 프로세스에서는 이러한 메시지가 로그에 올바르게 표시되는지 확인합니다.

#### 비준수 코드 {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### 준수 코드 {#compliant-code-7}

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

* **키**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

앞에서 언급했듯이 로그 메시지를 이해할 때는 컨텍스트가 중요합니다. `Exception.printStackTrace()`를 사용하면 스택 추적만 표준 오류 스트림으로 출력되므로 모든 컨텍스트가 손실됩니다. 또한 Experience Manager와 같은 다중 스레드 애플리케이션에서 이 방법을 사용하여 여러 예외를 병렬로 인쇄하면 스택 추적이 겹쳐서 상당한 혼동을 일으킬 수 있습니다. 예외는 로깅 프레임워크에서만 기록되어야 합니다.

#### 비준수 코드 {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### 준수 코드 {#compliant-code-8}

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

* **키**: CQRules:CQBP-44—LogLevelConsolePrinters
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

Experience Manager에서의 로깅은 항상 로깅 프레임워크(SLF4J)를 통해 수행되어야 합니다. 표준 출력 또는 표준 오류 스트림으로 직접 출력하면 로깅 프레임워크에서 제공하는 구조 및 컨텍스트 정보가 손실될 수 있습니다. 그에 따라 성능 문제가 발생할 수도 있습니다.

#### 비준수 코드 {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### 준수 코드 {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 하드 코딩된 앱 및 라이브러리 경로 방지 {#avoid-hardcoded-apps-and-libs-paths}

* **키**: CQRules:CQBP-71
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2018.4.0

`/libs` 및 `/apps`로 시작하는 경로는 일반적으로 하드코딩해서는 안 됩니다. 이러한 경로는 일반적으로 `Sling` 검색 경로를 기준으로 저장되며 기본값은 `/libs,/apps`입니다. 절대 경로를 사용하면 프로젝트 수명 주기의 후반에만 나타나는 미묘한 결함이 발생할 수 있습니다.

#### 비준수 코드 {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### 준수 코드 {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling 스케줄러를 사용하지 않음 {#sonarqube-sling-scheduler}

* **키**: CQRules:AMSCORE-554
* **유형**: `Code Smell`/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

보장된 실행이 필요한 작업에는 `Sling` 스케줄러를 사용하지 마십시오. Sling의 예정된 작업은 실행을 보장하며 클러스터된 환경과 클러스터되지 않은 환경 모두에 더 적합합니다.

클러스터된 환경에서 슬링 작업이 처리되는 방법에 대한 자세한 내용은 [`Apache Sling` 이벤트 및 작업 처리](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html)를 참조하십시오.

### 더 이상 사용되지 않는 Experience Manager API를 사용하지 않음 {#sonarqube-aem-deprecated}

* **키**: AMSCORE-553
* **유형**: `Code Smell`/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

Experience Manager API 영역은 사용이 권장되지 않아 더 이상 사용되지 않는 것으로 간주되는 API를 식별하기 위해 지속적으로 수정되고 있습니다.

대부분의 경우 이러한 API는 표준 Java™ `@Deprecated` 주석을 사용하여 더 이상 사용되지 않으며, `squid:CallToDeprecatedMethod`에 의해 식별됩니다.

그러나 Experience Manager의 컨텍스트에서는 API가 더 이상 사용되지 않지만 다른 컨텍스트에서는 사용되는 경우가 있습니다. 이 규칙은 이 두 번째 클래스를 식별합니다.

### 슬링 모델에서 @Inject과 함께 @Optional 주석 사용 안 함 {#sonarqube-slingmodels-inject-optional}

* **키**: InjectAnnotationWithOptionalInjectionCheck
* **유형**: 소프트웨어 품질
* **심각도**: 사소
* **이후**: 버전 2023.11

`Apache Sling` 프로젝트는 `@Inject`(필드 또는 클래스 수준)과 결합할 때 성능이 저하될 수 있으므로 슬링 모델의 컨텍스트에서 `DefaultInjectionStrategy.OPTIONAL` 주석을 사용하지 못하도록 합니다. 대신 보다 구체적인 주입(예: `@ValueMapValue` 또는 `@OsgiInjector` 주석)을 사용해야 합니다.

권장 주석에 대한 자세한 내용과 이 권장 사항을 먼저 만든 이유를 보려면 [`Apache Sling` 설명서](https://sling.apache.org/documentation/bundles/models.html#discouraged-annotations-1)를 확인하십시오.


### HTTPClient 인스턴스 재사용 {#sonarqube-reuse-httpclient}

* **키**: AEMSRE-870
* **유형**: 소프트웨어 품질
* **심각도**: 사소
* **이후**: 버전 2023.11

AEM 애플리케이션은 종종 HTTP 프로토콜을 사용하여 다른 애플리케이션에 연결하며, Apache HttpClient는 이를 위해 자주 사용되는 라이브러리입니다. 그러나 이러한 HttpClient 개체를 만들면 약간의 오버헤드가 발생하므로 이러한 개체를 가능한 한 재사용해야 합니다.

이 규칙은 이러한 HttpClient 개체가 메서드 내에서 private이 아니라 클래스 수준에서 전역적이므로 재사용할 수 있는지 확인합니다. 이 경우 클래스 또는 `activate()` 메서드의 생성자에서 HttpClient 필드를 설정해야 합니다(이 클래스가 OSGi 구성 요소/서비스인 경우).

HttpClient의 [최적화 안내서](https://hc.apache.org/httpclient-legacy/performance.html)에서 HttpClient 사용과 관련된 몇 가지 모범 사례를 확인하십시오.

#### 비준수 코드 {#non-compliant-code-14}

```java
public void doHttpCall() {
  HttpClient httpclient = HttpClients.createDefault();
  // do something with the httpclient
}
```

#### 준수 코드 {#compliant-code-11}

```java
public class myClass {

  HttpClient httpclient;

  public void doHttpCall() {
    // do something with the httpclient
  }

}
```

## OakPAL 콘텐츠 규칙 {#oakpal-rules}

다음 섹션에서는 Cloud Manager에서 실행되는 OakPAL 검사에 대해 자세히 설명합니다.

>[!NOTE]
>
>OakPAL은 독립 실행형 Oak 저장소를 사용하여 콘텐츠 패키지의 유효성을 검사하는 프레임워크입니다. 2019년 Experience Manager 록스타 북미 어워드 수상 Experience Manager 파트너가 개발하였다.

### 고객은 로 주석이 달린 제품 API를 구현하거나 확장해서는 안 됩니다@ProviderType{#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **키**: CQBP-84
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2018.7.0

Experience Manager API에는 사용자 정의 코드에 의해서만 사용되지만 구현되지는 않는 Java™ 인터페이스 및 클래스가 포함되어 있습니다. 예를 들어 Experience Manager만 `com.day.cq.wcm.api.Page` 인터페이스를 구현해야 합니다.

이러한 인터페이스에 새 메서드를 추가해도 추가된 메서드는 이러한 인터페이스를 사용하는 기존 코드에 영향을 주지 않습니다. 결과적으로 이러한 인터페이스에 새 메서드를 추가해도 이전 버전과 호환되는 것으로 간주됩니다. 그러나 사용자 정의 코드로 이러한 인터페이스 중 하나를 구현하는 경우 해당 사용자 정의 코드로 인해 이전 버전과 호환되지 않는 문제가 발생합니다.

Experience Manager에 의해 구현되도록 의도된 인터페이스와 클래스는 `org.osgi.annotation.versioning.ProviderType` 또는 경우에 따라 유사한 기존 주석 `aQute.bnd.annotation.ProviderType`으로 주석을 추가할 수 있습니다. 이 규칙은 사용자 지정 코드가 이러한 인터페이스를 구현하거나 클래스를 확장하는 경우를 식별합니다.

#### 비준수 코드 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 사용자 정의 Lucene Oak 인덱스에 Tika 구성을 포함해야 함 {#oakpal-indextikanode}

* **키**: IndexTikaNode
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 2021.8.0

기본 제공되는 여러 Experience Manager Oak 인덱스에는 Tika 구성이 포함되며 이러한 인덱스의 사용자 정의 항목에는 Tika 구성이 포함되어야 합니다. 이 규칙은 `damAssetLucene`, `lucene` 및 `graphqlConfig` 인덱스의 사용자 정의 항목을 확인하고 `tika` 노드가 누락되거나 `tika` 노드에 `config.xml`이라는 하위 노드가 누락된 경우 문제를 발생시킵니다.

인덱스 정의 사용자 정의에 대한 자세한 내용은 [인덱싱 설명서](/help/operations/indexing.md#preparing-the-new-index-definition)를 참조하십시오.

#### 비준수 코드 {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
```

#### 준수 코드 {#compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 사용자 정의 Lucene Oak 인덱스를 동기화하지 않음 {#oakpal-indexasync}

* **키**: IndexAsyncProperty
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 2021.8.0

`lucene` 유형의 Oak 인덱스는 항상 비동기식으로 인덱싱되어야 합니다. 이렇게 하지 않으면 시스템이 불안정해질 수 있습니다. Lucene 인덱스 구조에 대한 자세한 내용은 [Oak 설명서](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition)를 참조하세요.

#### 비준수 코드 {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - type: lucene
      - tags: [visualSimilaritySearch]
      + tika
        + config.xml
```

#### 준수 코드 {#compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 사용자 정의 DAM Asset Lucene Oak 인덱스를 올바르게 구성해야 함 {#oakpal-damAssetLucene-sanity-check}

* **키**: IndexDamAssetLucene
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 2021.6.0

Experience Manager Assets에서 에셋 검색이 올바르게 작동하려면 `damAssetLucene` Oak 인덱스의 사용자 정의가 이 인덱스와 관련된 일련의 지침을 따라야 합니다. 이 규칙은 인덱스 정의에 `tags` 값을 포함하는 `visualSimilaritySearch`(이)라는 다중 값 속성이 있어야 하는지 확인합니다.

#### 비준수 코드 {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - type: lucene
      + tika
        + config.xml
```

#### 준수 코드 {#compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 고객 패키지는 libs에서 노드를 생성하거나 수정해서는 안 됨 {#oakpal-customer-package}

* **키**: BannedPath
* **유형**: 버그
* **심각도**: 심각
* **이후**: 버전 2019.6.0

Experience Manager 콘텐츠 저장소의 `/libs` 콘텐츠 트리는 고객이 읽기 전용으로 간주해야 하는 것이 오랜 모범 사례였습니다. `/libs`에서 노드 및 속성을 수정하면 주 업데이트 및 부 업데이트에 상당한 위험이 발생합니다. 공식 채널을 통해 Adobe을 사용하여 `/libs`을(를) 수정하십시오.

### 패키지에 중복된 OSGi 구성을 포함하지 않음 {#oakpal-package-osgi}

* **키**: DuplicateOsgiConfigurations
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

복잡한 프로젝트에서 발생하는 일반적인 문제는 동일한 OSGi 구성 요소가 여러 번 구성되는 경우입니다. 이러한 문제가 발생하면 인해 어떤 구성이 적용 가능할지 모호해집니다. 이 규칙은 동일한 구성 요소가 동일한 실행 모드 또는 실행 모드 조합에서 여러 번 구성된 문제만 식별한다는 점에서 “실행 모드 인식” 규칙입니다.

>[!NOTE]
>
>이 규칙은 빌드된 패키지의 전체 목록에서 동일한 패키지가 중복되는 경우를 포함하여 동일한 경로의 동일한 구성이 여러 패키지에 정의되는 문제를 일으킵니다.
>
>예를 들어 빌드가 `com.myco:com.myco.ui.apps` 및 `com.myco:com.myco.all`이라는 패키지를 생성하는 경우 여기서 `com.myco:com.myco.all`은 `com.myco:com.myco.ui.apps`를 임베드하므로 `com.myco:com.myco.ui.apps` 내의 모든 구성이 중복 요소로 보고됩니다.
>
>일반적으로 이러한 상황은 [콘텐츠 패키지 구조 지침](/help/implementing/developing/introduction/aem-project-content-package-structure.md)을(를) 따르지 않는 경우입니다. 이 예제에서는 패키지 `com.myco:com.myco.ui.apps`에 `<cloudManagerTarget>none</cloudManagerTarget>` 속성이 없습니다.

#### 비준수 코드 {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 준수 코드 {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### 구성 및 설치 폴더에 OSGi 노드만 포함해야 함 {#oakpal-config-install}

* **키**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

보안상의 이유로 `/config/` 및 `/install/`가 포함된 경로는 Experience Manager의 관리 사용자만 읽을 수 있으며 OSGi 구성 및 OSGi 번들에만 사용해야 합니다. 이러한 세그먼트를 포함하는 경로에 다른 유형의 콘텐츠를 배치하면 관리 사용자와 비관리 사용자 간에 의도하지 않게 애플리케이션 동작이 달라집니다.

일반적인 문제는 구성 요소 대화 상자 내에서 `config`라는 노드를 사용하거나 인라인 편집을 위해 리치 텍스트 편집기 구성을 지정할 때 발생합니다. 이 문제를 해결하려면 문제가 있는 노드의 이름을 규정 준수 이름으로 변경해야 합니다. 리치 텍스트 편집기 구성의 경우 `cq:inplaceEditing` 노드의 `configPath` 속성을 사용하여 새 위치를 지정하십시오.

#### 비준수 코드 {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 준수 코드 {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### 패키지를 겹치지 않음 {#oakpal-no-overlap}

* **키**: PackageOverlaps
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2019.6.0

[패키지에 중복된 OSGi 구성 규칙을 포함해서는 안 됨](#oakpal-package-osgi)과 마찬가지로, 여러 개의 개별 콘텐츠 패키지에 의해 동일한 노드 경로가 기록되는 복잡한 프로젝트에서 일반적인 문제입니다. 콘텐츠 패키지 종속성을 사용하면 일관된 결과를 보장할 수 있지만 중복을 완전히 피하는 것이 좋습니다.

### 기본 작성 모드는 클래식 UI가 아니어야 합니다. {#oakpal-default-authoring}

* **키**: ClassicUIAuthoringMode
* **유형**: `Code Smell`/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

`com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` OSGi 구성은 Experience Manager 내의 기본 작성 모드를 정의합니다. Experience Manager 6.4 이후 Classic UI가 더 이상 사용되지 않으므로 기본 작성 모드가 Classic UI로 구성되면 문제가 발생합니다.

### 대화 상자가 있는 구성 요소에는 터치 UI 대화 상자가 있어야 함 {#oakpal-components-dialogs}

* **키**: ComponentWithOnlyClassicUIDialog
* **유형**: `Code Smell`/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

클래식 UI 대화 상자가 있는 Experience Manager 구성 요소에는 항상 해당 터치 UI 대화 상자가 있어야 합니다. 둘 다 클래식 UI가 더 이상 지원되지 않는 Cloud Service 배포 모델과 호환되는 최적의 제작 환경을 제공합니다. 이 규칙은 다음 시나리오를 확인합니다.

* Classic UI 대화 상자(즉, `dialog` 하위 노드)가 있는 구성 요소에는 해당 터치 UI 대화 상자(즉, `cq:dialog` 하위 노드)가 있어야 합니다.
* Classic UI 디자인 대화 상자(예: `design_dialog` 노드)가 있는 구성 요소에는 해당 터치 UI 디자인 대화 상자(예: `cq:design_dialog` 하위 노드)가 있어야 합니다.
* Classic UI 대화 상자 및 Classic UI 디자인 대화 상자가 모두 있는 구성 요소에는 해당 터치 UI 대화 상자 및 해당 터치 UI 디자인 대화 상자가 모두 있어야 합니다.

Experience Manager 현대화 도구 설명서는 구성 요소를 Classic UI에서 Touch UI로 변환하는 방법에 대한 문서와 도구를 제공합니다. 자세한 내용은 [Experience Manager 현대화 도구 설명서](https://opensource.adobe.com/aem-modernize-tools/)를 참조하십시오.

### 패키지에 변경 가능한 콘텐츠 및 변경 불가능한 콘텐츠를 혼합하지 않음 {#oakpal-packages-immutable}

* **키**: ImmutableMutableMixedPackage
* **유형**: `Code Smell`/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

Cloud Service 배포 모델과 호환되려면 개별 콘텐츠 패키지에 저장소의 변경 불가능한 영역(`/apps` 및 `/libs`) 또는 변경 가능한 영역(`/apps` 또는 `/libs`에 있지 않은 모든 것)에 대한 콘텐츠가 포함되어 있어야 하지만 둘 다 포함되어서는 안 됩니다. 예를 들어 `/apps/myco/components/text` 및 `/etc/clientlibs/myco`이(가) 모두 포함된 패키지는 Cloud Service과 호환되지 않으므로 문제가 보고됩니다.

>[!NOTE]
>
>[고객 패키지는 libs에서 노드를 만들거나 수정해서는 안 됨](#oakpal-customer-package) 규칙이 항상 적용됩니다.

자세한 내용은 [Experience Manager 프로젝트 구조 설명서](/help/implementing/developing/introduction/aem-project-content-package-structure.md)를 참조하십시오.

### 역방향 복제 에이전트를 사용하지 않음 {#oakpal-reverse-replication}

* **키**: ReverseReplication
* **유형**: `Code Smell`/Cloud Service 호환성
* **심각도**: 사소
* **이후**: 버전 2020.5.0

Experience Manager as a Cloud Service의 [릴리스 정보](/help/release-notes/aem-cloud-changes.md#replication-agents)에서 설명한 대로 Cloud Service 배포에서는 역방향 복제에 대한 지원을 사용할 수 없습니다.

역방향 복제를 사용하는 고객은 Adobe에 대체 솔루션을 문의해야 합니다.

### 프록시가 활성화된 클라이언트 라이브러리에 포함된 리소스는 “resources” 폴더에 있어야 함 {#oakpal-resources-proxy}

* **키**: ClientlibProxyResource
* **유형**: 버그
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager 클라이언트 라이브러리에는 이미지 및 글꼴과 같은 정적 리소스가 포함될 수 있습니다. 문서 [프로세서 사용](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors)에 설명된 대로 프록시 클라이언트 라이브러리를 사용할 때 게시 인스턴스에서 효과적으로 참조하려면 이러한 정적 리소스가 `resources`이라는 하위 폴더에 포함되어 있어야 합니다.

#### 비준수 코드 {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 준수 코드 {#compliant-proxy-enabled}

```tet
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Cloud Service의 호환되지 않는 워크플로 프로세스 사용 {#oakpal-usage-cloud-service}

* **키**: CloudServiceIncompatibleWorkflowProcess
* **유형**: 버그
* **심각도**: 주요
* **이후**: 버전 2021.2.0

Adobe Experience Manager as a Cloud Service의 에셋 처리를 위해 에셋 마이크로 서비스로 이동하면서, 이제 온-프레미스 및 AMS 버전에서 사용되는 여러 워크플로 프로세스가 지원되지 않습니다. 이러한 많은 워크플로우가 불필요하게 되었습니다.

[Experience Manager as a Cloud Service Assets GitHub 저장소](https://github.com/adobe/aem-cloud-migration)에 있는 마이그레이션 도구를 사용하여 Experience Manager as a Cloud Service로 마이그레이션하는 동안 워크플로 모델을 업데이트할 수 있습니다.

### 편집 가능한 템플릿을 위해 정적 템플릿을 사용하지 않음 {#oakpal-static-template}

* **키**: StaticTemplateUsage
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

이전까지는 Experience Manager 프로젝트에서 정적 템플릿을 매우 흔히 사용했지만 이제는 가장 유연하고 정적 템플릿에 없는 추가 기능을 지원하는 편집 가능한 템플릿을 사용하는 것이 좋습니다. 자세한 내용은 [페이지 템플릿](/help/implementing/developing/components/templates.md) 문서에서 확인할 수 있습니다.

정적 템플릿에서 편집 가능한 템플릿으로의 마이그레이션은 [Experience Manager 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)를 사용하여 대부분 자동화할 수 있습니다.

### 기존 기초 구성 요소를 사용하지 않음 {#oakpal-usage-legacy}

* **키**: LegacyFoundationComponentUsage
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

기존 기초 구성 요소(예: `/libs/foundation` 아래의 구성 요소)는 핵심 구성 요소를 위한 여러 Experience Manager 릴리스에서 더 이상 사용되지 않습니다. 오버레이 또는 상속 여부에 관계없이 기존 기초 구성 요소를 사용자 정의 구성 요소의 기반으로 사용하는 것은 권장되지 않으며 해당 핵심 구성 요소로 변환해야 합니다.

[Experience Manager 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/)를 통해 이 변환을 용이하게 할 수 있습니다.

### 지원되는 실행 모드 이름 및 순서만 사용해야 함 {#oakpal-supported-runmodes}

* **키**: SupportedRunmode
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service는 실행 모드 이름에 대해 엄격한 이름 지정 정책을 시행하고 해당 실행 모드에 대해 엄격한 순서를 적용합니다. 지원되는 실행 모드 목록은 [Experience Manager as a Cloud Service에 배포](/help/implementing/deploying/overview.md#runmodes) 문서에 있으며, 이 목록에서 벗어난 모든 항목은 문제로 식별됩니다.

### 사용자 정의 검색 인덱스 정의 노드는 `/oak:index`의 직접 하위 노드여야 함 {#oakpal-custom-search}

* **키**: OakIndexLocation
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(예: `oak:QueryIndexDefinition` 유형의 노드)가 `/oak:index`의 직접 하위 노드여야 합니다. Experience Manager as a Cloud Service와 호환되려면 다른 위치의 인덱스를 이동해야 합니다. 검색 인덱스에 대한 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md) 문서를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드의 compatVersion을 2로 설정해야 함 {#oakpal-custom-search-compatVersion}

* **키**: IndexCompatVersion
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(예: `oak:QueryIndexDefinition` 유형의 노드)에 `2`로 설정된 `compatVersion` 속성이 있어야 합니다. Adobe Experience Manager as a Cloud Service은 다른 값을 지원하지 않습니다. 검색 인덱스에 대한 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md)를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드의 하위 노드 유형은 `nt:unstructured `여야 함{#oakpal-descendent-nodes}

* **키**: IndexDescendantNodeType
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

사용자 정의 검색 인덱스 정의 노드에 순서가 지정되지 않은 하위 노드가 있으면 문제를 해결하기 어려운 문제가 발생할 수 있습니다. 이러한 상황을 방지하려면 `oak:QueryIndexDefinition` 노드의 모든 하위 노드가 `nt:unstructured` 유형인 것이 좋습니다.

### 사용자 정의 검색 인덱스 정의 노드에 하위 노드가 있는 “indexRules” 하위 노드를 포함해야 함 {#oakpal-custom-search-index}

* **키**: IndexRulesNode
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

올바르게 정의된 사용자 정의 검색 인덱스 정의 노드에는 `indexRules`(이)라는 하위 노드가 있어야 하며, 이 노드에는 하나 이상의 하위 노드가 있어야 합니다. 자세한 내용은 [Oak 문서](https://jackrabbit.apache.org/oak/docs/query/lucene.html)에서 확인할 수 있습니다.

### 사용자 정의 검색 인덱스 정의 노드는 명명 규칙을 준수해야 함 {#oakpal-custom-search-definitions}

* **키**: IndexName
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(예: `oak:QueryIndexDefinition` 유형의 노드)를 [콘텐츠 검색 및 색인화](/help/operations/indexing.md) 문서에 설명된 특정 패턴에 따라 지정해야 합니다.

### 사용자 정의 검색 인덱스 정의 노드는 lucene 유형의 인덱스를 사용해야 함 {#oakpal-index-type-lucene}

* **키**: IndexType
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 버전 2021.2.0(유형 및 심각도는 2021.8.0에 변경됨)

Experience Manager as a Cloud Service를 사용하려면 사용자 정의 검색 인덱스 정의(예: `oak:QueryIndexDefinition` 유형의 노드)에 값이 `lucene`으로 설정된 `type` 속성이 있어야 합니다. 기존 인덱스 유형을 사용하는 색인화는 Experience Manager as a Cloud Service로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md#how-to-use)를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드에 “seed” 속성을 포함하지 않음 {#oakpal-property-name-seed}

* **키**: IndexSeedProperty
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service에서는 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)에 `seed`라는 속성을 포함할 수 없습니다. 이 속성을 사용하는 색인화는 Experience Manager as a Cloud Service로 마이그레이션하기 전에 업데이트해야 합니다. 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md#how-to-use) 문서를 참조하십시오.

### 사용자 정의 검색 인덱스 정의 노드에 “reindex” 속성을 포함하지 않음 {#oakpal-reindex-property}

* **키**: IndexReindexProperty
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2021.2.0

Experience Manager as a Cloud Service에서는 사용자 정의 검색 인덱스 정의(즉, `oak:QueryIndexDefinition` 유형의 노드)에 `reindex`라는 속성을 포함할 수 없습니다. 이 속성을 사용하는 색인화는 Experience Manager as a로 마이그레이션하기 전에 업데이트해야 합니다.
Cloud Service. 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md#how-to-use) 문서를 참조하십시오.

### 사용자 지정 DAM 자산 Lucene 노드는 `queryPaths`을(를) 지정하지 않아야 합니다. {#oakpal-damAssetLucene-queryPaths}

* **키**: IndexDamAssetLucene
* **유형**: 버그
* **심각도**: Blocker
* **이후**: 버전 2022.1.0

#### 비준수 코드 {#non-compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-1
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - queryPaths: [/content/dam]
      - type: lucene
      + tika
        + config.xml
```

#### 준수 코드 {#compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### 사용자 지정 검색 인덱스 정의에 `compatVersion`이(가) 포함된 경우 2로 설정해야 합니다. {#oakpal-compatVersion}

* **키**: IndexCompatVersion
* **유형**: `Code Smell`
* **심각도**: 주요
* **이후**: 버전 2022.1.0


### `includedPaths`을(를) 지정하는 인덱스 노드는 같은 값으로 `queryPaths`도 지정해야 합니다. {#oakpal-included-paths-without-query-paths}

* **키**: IndexIncludedPathsWithoutQueryPaths
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2023.1.0

사용자 지정 인덱스의 경우 동일한 값으로 `includedPaths` 및 `queryPaths`을(를) 구성하십시오. 하나가 지정된 경우 다른 하나가 일치해야 합니다. 그러나 사용자 지정 버전을 포함하여 `damAssetLucene`의 인덱스에 대한 특별한 경우가 있습니다. 이러한 경우 `includedPaths`만 제공하십시오.

### 일반 노드 형식에 `nodeScopeIndex`을(를) 지정하는 인덱스 노드는 `includedPaths` 및 `queryPaths`도 지정해야 합니다. {#oakpal-full-text-on-generic-node-type}

* **키**: IndexFulltextOnGenericType
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2023.1.0

`nodeScopeIndex` 또는 `nt:unstructured`과(와) 같은 &quot;일반&quot; 노드 형식에 대해 `nt:base` 속성을 설정할 때는 `includedPaths` 및 `queryPaths` 속성도 지정해야 합니다.
노드 형식 `nt:base`은(는) &quot;일반&quot;으로 간주할 수 있습니다. 모든 노드 형식은 이 형식에서 상속되기 때문입니다. 따라서 `nodeScopeIndex`에서 `nt:base`을(를) 설정하면 저장소의 모든 노드를 인덱싱합니다. 마찬가지로 저장소에 이 형식의 노드가 많으므로 `nt:unstructured`도 &quot;일반&quot;으로 간주됩니다.

#### 비준수 코드 {#non-compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

#### 준수 코드 {#compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
  - includedPaths: ["/content/dam/"] 
  - queryPaths: ["/content/dam/"]
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

### 쿼리 엔진의 queryLimitReads 속성을 재정의하면 안 됩니다. {#oakpal-query-limit-reads}

* **키**: OverrideOfQueryLimitReads
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2023.1.0

기본값을 재정의하면 특히 더 많은 콘텐츠가 추가될 때 페이지 읽기 속도가 느려질 수 있습니다.

### 동일한 색인의 여러 활성 버전 {#oakpal-multiple-active-versions}

* **키**: IndexDetectMultipleActiveVersionsOfSameIndex
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2023.1.0

#### 비준수 코드 {#non-compliant-code-multiple-active-versions}

```text
+ oak:index
  + damAssetLucene-1-custom-1
    ...
  + damAssetLucene-1-custom-2
    ...
  + damAssetLucene-1-custom-3
    ...
```

#### 준수 코드 {#compliant-code-multiple-active-versions}

```text
+ damAssetLucene-1-custom-3
    ...
```


### 완전히 맞춤화된 색인 정의의 이름은 공식 지침을 준수해야 합니다 {#oakpal-fully-custom-index-name}

* **키**: IndexValidFullyCustomName
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2023.1.0

전체 사용자 지정 인덱스 이름에 필요한 패턴은 `[prefix].[indexName]-custom-[version]`입니다. 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md) 문서에서 확인할 수 있습니다.

### 동일한 색인 정의에서 다른 분석 값을 가진 동일한 속성 {#oakpal-same-property-different-analyzed-values}

#### 비준수 코드 {#non-compliant-code-same-property-different-analyzed-values}

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
```

#### 준수 코드 {#compliant-code-same-property-different-analyzed-values}

예:

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

예:

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

분석된 속성이 명시적으로 설정되지 않은 경우 기본값은 false입니다.

### 태그 속성 {#tags-property}

* **키**: IndexHasValidTagsProperty
* **유형**: `Code Smell`
* **심각도**: 사소
* **이후**: 버전 2023.1.0

특정 인덱스의 경우 태그 속성과 현재 값을 유지해야 합니다. 태그 속성에 새 값을 추가하는 것은 가능하지만, 기존 값(또는 속성을 모두 삭제)을 삭제하면 예기치 않은 결과가 발생할 수 있습니다.

### UI 콘텐츠 패키지에 색인 정의 노드를 배포하면 안 됨 {#oakpal-ui-content-package}

* **키**: IndexNotUnderUIContent
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 UI 콘텐츠 패키지에 사용자 정의 검색 색인 정의(유형 `oak:QueryIndexDefinition`의 노드)를 배포할 수 없도록 합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/implementing/cloud-manager/release-notes/current.md)부터 파이프라인 오류가 발생할 수 있으므로 가능한 한 빨리 이 문제를 해결해야 합니다.

### damAssetLucene 유형의 사용자 정의 전체 텍스트 인덱스 정의에 &#39;damAssetLucene&#39; 접두사가 올바르게 있어야 합니다. {#oakpal-dam-asset-lucene}

* **키**: CustomFulltextIndexesOfTheDamAssetCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 `damAssetLucene`의 사용자 정의 전체 텍스트 색인 정의에 `damAssetLucene` 이외의 접두사가 붙지 못하도록 합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/implementing/cloud-manager/release-notes/current.md)부터 파이프라인 오류가 발생할 수 있으므로 가능한 한 빨리 이 문제를 해결하십시오.

### 색인 정의 노드에는 동일한 이름의 속성이 포함되면 안 됨 {#oakpal-index-property-name}

* **키**: DuplicateNameProperty
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 사용자 정의 검색 색인 정의(즉, 유형 `oak:QueryIndexDefinition`의 노드)에 동일한 이름의 속성을 포함하는 것을 금지합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/implementing/cloud-manager/release-notes/current.md)부터 파이프라인 오류가 발생할 수 있으므로 가능한 한 빨리 이 문제를 해결하십시오.

### 특정 기본 제공 색인 정의는 사용자 정의할 수 없음 {#oakpal-customizing-ootb-index}

* **키**: RestrictIndexCustomization
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service는 다음 OOTB 색인의 무단 수정을 금지합니다.

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/implementing/cloud-manager/release-notes/current.md)부터 파이프라인 오류가 발생할 수 있으므로 가능한 한 빨리 이 문제를 해결하십시오.

### 분석기의 토큰라이저 구성은 &#39;토큰라이저&#39;라는 이름으로 만들어야 합니다. {#oakpal-tokenizer}

* **키**: AnalyzerTokenizerConfigCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.6.0

AEM Cloud Service에서는 분석기에서 이름이 잘못된 토큰라이저를 만들 수 없습니다. 토큰화는 항상 `tokenizer`로 정의되어야 합니다.

>[!WARNING]
>
>[Cloud Manager 2024년 8월 릴리스](/help/implementing/cloud-manager/release-notes/current.md)부터 파이프라인 오류가 발생할 수 있으므로 가능한 한 빨리 이 문제를 해결하십시오.

### 색인화 정의 구성에 공백이 포함되어서는 안 됨 {#oakpal-indexing-definitions-spaces}

* **키**: PathSpacesCheck
* **유형**: 개선
* **심각도**: 사소
* **이후**: 버전 2024.7.0

AEM Cloud Service는 공백이 있는 속성을 포함하는 색인화 &#x200B;&#x200B;정의 생성을 금지합니다.
