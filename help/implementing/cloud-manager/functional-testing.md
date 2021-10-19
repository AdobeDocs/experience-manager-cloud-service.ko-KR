---
title: 기능 테스트 - Cloud Services
description: 기능 테스트 - Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 058fa606bbc667a36b78d5271947e2741f36240f
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 1%

---

# 기능 테스트 {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="기능 테스트"
>abstract="기능 테스트는 세 가지 유형으로 분류됩니다. 제품 기능 테스트, 사용자 지정 기능 테스트 및 사용자 지정 UI 테스트"

기능 테스트는 세 가지 유형으로 분류됩니다.


* 제품 기능 테스트
* 사용자 지정 기능 테스트
* 사용자 지정 UI 테스트

## 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 AEM의 핵심 기능(예: 작성 및 복제)에 대한 안정적인 HTTP 통합 테스트 세트로서, 이 핵심 기능을 위반하는 경우 애플리케이션 코드에 대한 고객 변경 사항이 배포되지 않도록 합니다.

고객이 Cloud Manager에 새 코드를 배포할 때마다 제품 기능 테스트가 자동으로 실행되며 건너뛸 수 없습니다.

을(를) 참조하십시오. [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) 샘플 테스트.

## 사용자 지정 기능 테스트 {#custom-functional-testing}

파이프라인의 사용자 지정 기능 테스트 단계가 항상 존재하며 건너뛸 수 없습니다.

그러나 빌드에 의해 테스트 JAR이 생성되지 않으면 테스트가 기본적으로 전달됩니다.

>[!NOTE]
>다음 **다운로드 로그** 단추를 사용하면 테스트 실행 세부 양식에 대한 로그가 포함된 ZIP 파일에 액세스할 수 있습니다. 이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 이러한 로그에는 일반적인 다운로드 또는 테일 로그 기능을 사용하여 액세스할 수 있습니다. 을(를) 참조하십시오. [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 자세한 내용

## 사용자 지정 UI 테스트 {#custom-ui-testing}

AEM은 고객에게 Cloud Manager 품질 게이트의 통합 세트를 제공하여 애플리케이션을 원활하게 업데이트합니다. 특히 IT 테스트 게이트를 통해 고객은 이미 AEM API를 사용하는 자체 테스트를 만들고 자동화할 수 있습니다.

사용자 지정 UI 테스트 기능은 [옵션 기능](#customer-opt-in) 고객이 자신의 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있도록 해줍니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다. 여기에서 UI를 빌드하고 UI 테스트를 작성하는 방법에 대해 자세히 알아볼 수 있습니다. 또한 AEM Project Archetype을 사용하여 UI 테스트 프로젝트를 쉽게 생성할 수 있습니다.

고객은 GIT을 통해 사용자 지정 테스트를 만들고 UI용 테스트 세트를 만들 수 있습니다. UI 테스트는 각 Cloud Manager 파이프라인에 대한 특정 품질 게이트의 일부로서 특정 단계 및 피드백 정보와 함께 실행됩니다. 회귀 및 새로운 기능을 포함한 모든 UI 테스트를 통해 고객 컨텍스트 내에서 오류를 감지하고 보고할 수 있습니다.

고객 UI 테스트는 &quot;사용자 지정 UI 테스트&quot; 단계의 프로덕션 파이프라인에서 자동으로 실행됩니다.

Java로 작성된 HTTP 테스트인 사용자 지정 기능 테스트와 달리, UI 테스트는 다음에 정의된 규칙을 따르는 한 모든 언어로 작성된 테스트가 있는 Docker 이미지가 될 수 있습니다 [UI 테스트 작성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=en#building-ui-tests).

>[!NOTE]
>구조와 언어를 따르는 것이 좋습니다 *(js 및 wdio)* 간편하게 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) 시작점으로 사용하십시오.

### 고객 옵트인 {#customer-opt-in}

UI 테스트를 빌드하고 실행하려면 고객이 코드 리포지토리에 파일을 추가하고, UI 테스트 하위 모듈의 pom.xml 파일 옆에 있는 UI 테스트를 위한 maven 하위 모듈 아래에 있는 &quot;옵트인&quot;을 구현하고 이 파일이 빌드된 루트에 있는지 확인해야 합니다 `tar.gz` 파일.

*파일 이름*: `testing.properties`

*내용*: `ui-tests.version=1`

빌드되지 않은 경우 `tar.gz` 파일, UI 테스트 빌드 및 실행을 건너뜁니다

추가하려면 `testing.properties` 작성된 아티팩트에 파일을 추가하고 `include` 문 `assembly-ui-test-docker-context.xml` 파일(UI 테스트 하위 모듈):

    &quot;
    [..]
    &lt;includes>
    &lt;include>Dockerfile&lt;/include>
    &lt;include>wait-for-grid.sh&lt;/include>
    &lt;include>testing.properties&lt;/include> &lt;!>- Cloud Manager의 옵트인 테스트 모듈 —>
    &lt;/includes>
    [..]
    &quot;

>[!NOTE]
>이 섹션에 설명된 대로 UI 테스트를 사용하려면 2021년 2월 10일 전에 생성된 프로덕션 파이프라인을 업데이트해야 합니다. 이것은 사용자가 프로덕션 파이프라인을 편집하고 클릭해야 함을 의미합니다 **저장** 변경하지 않은 경우에도 UI에서 변경할 수 있습니다.
>을(를) 참조하십시오. [CI-CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager) 파이프라인 구성에 대해 자세히 알아보십시오 .

### 기능 테스트 작성 {#writing-functional-tests}

고객이 작성한 기능 테스트는 AEM에 배포할 아티팩트와 동일한 Maven 빌드에서 생성한 별도의 JAR 파일로 패키지해야 합니다. 일반적으로 이는 별도의 Maven 모듈입니다. 결과 JAR 파일은 필요한 모든 종속성을 포함해야 하며 일반적으로 jar-with-dependencies 설명자를 사용하여 maven-assembly-plugin을 사용하여 만듭니다.

또한 JAR에는 Cloud-Manager-TestType 매니페스트 헤더가 통합 테스트로 설정되어 있어야 합니다. 앞으로는 추가 헤더 값이 지원됩니다. maven-assembly-plugin에 대한 구성 예는 다음과 같습니다.

```java
<build>
    <plugins>
        <!-- Create self-contained jar with dependencies -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>3.1.0</version>
            <configuration>
                <descriptorRefs>
                    <descriptorRef>jar-with-dependencies</descriptorRef>
                </descriptorRefs>
                <archive>
                    <manifestEntries>
                        <Cloud-Manager-TestType>integration-test</Cloud-Manager-TestType>
                    </manifestEntries>
                </archive>
            </configuration>
            <executions>
                <execution>
                    <id>make-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
```

이 JAR 파일 내에서 실행할 실제 테스트의 클래스 이름은 IT에서 끝나야 합니다.

예를 들어 `com.myco.tests.aem.ExampleIT` 이 실행되지만 `com.myco.tests.aem.ExampleTest` 그렇지 않습니다.

테스트 클래스는 일반적인 JUnit 테스트여야 합니다. 테스트 인프라는 aem-testing-clients 테스트 라이브러리에서 사용하는 규칙과 호환되도록 설계되고 구성됩니다. 개발자는 이 라이브러리를 사용하고 모범 사례를 따를 것을 적극 권장합니다. 을(를) 참조하십시오. [Git 링크](https://github.com/adobe/aem-testing-clients) 자세한 내용

### 로컬 테스트 실행 {#local-test-execution}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans 등과 같은 메인스트림 Java IDE에서 실행할 수 있습니다.

그러나 이러한 테스트를 실행할 때에는 aem-testing-client(및 기본 Sling Testing Clients)에 의해 기대되는 다양한 시스템 속성을 설정해야 합니다.

시스템 속성은 다음과 같습니다.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the author URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
