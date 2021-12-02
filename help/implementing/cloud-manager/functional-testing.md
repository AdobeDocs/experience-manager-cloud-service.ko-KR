---
title: 기능 테스트 - Cloud Services
description: 기능 테스트 - Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 02db915e114c2af8329eaddbb868045944a3574d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 9%

---

# 기능 테스트 {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="기능 테스트"
>abstract="기능 테스트는 세 가지 유형으로 분류됩니다. 제품 기능 테스트, 사용자 지정 기능 테스트 및 사용자 지정 UI 테스트"

기능 테스트는 세 가지 유형으로 분류됩니다.


* [제품 기능 테스트](#product-functional-testing)
* [사용자 지정 기능 테스트](#custom-functional-testing)
* [사용자 지정 UI 테스트](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing)

## 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 AEM의 핵심 기능(예: 작성 및 복제)에 대한 안정적인 HTTP 통합 테스트 세트로서, 이 핵심 기능을 위반하는 경우 애플리케이션 코드에 대한 고객 변경 사항이 배포되지 않도록 합니다.

고객이 Cloud Manager에 새 코드를 배포할 때마다 제품 기능 테스트가 자동으로 실행되며 건너뛸 수 없습니다.

을(를) 참조하십시오. [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) 샘플 테스트.

## 사용자 지정 기능 테스트 {#custom-functional-testing}

파이프라인의 사용자 지정 기능 테스트 단계가 항상 존재하며 건너뛸 수 없습니다.

빌드는 0이나 하나의 테스트 JAR를 생성해야 합니다. 테스트 JAR이 0이면 기본적으로 테스트 단계가 전달됩니다. 빌드에서 두 개 이상의 테스트 JAR를 생성하는 경우 선택한 JAR가 비결정적입니다.

>[!NOTE]
>The **Download Log** button allows access to a ZIP file containing the logs for the test execution detailed form. These logs do not include the logs of the actual AEM runtime process – those can be accessed using the regular Download or Tail Logs functionality. 을(를) 참조하십시오. [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 자세한 내용


## 기능 테스트 작성 {#writing-functional-tests}

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

이 JAR 파일 내에서 실행할 실제 테스트의 클래스 이름은 `IT`.

예를 들어 `com.myco.tests.aem.it.ExampleIT` 이 실행되지만 `com.myco.tests.aem.it.ExampleTest` 그렇지 않습니다.

또한 코드 스캔의 검사 검사 시 테스트 코드를 제외하려면 테스트 코드가 이름이 인 패키지 미만이어야 합니다 `it` (적용 범위 제외 필터는 `**/it/**/*.java`).

테스트 클래스는 일반적인 JUnit 테스트여야 합니다. 테스트 인프라는 aem-testing-clients 테스트 라이브러리에서 사용하는 규칙과 호환되도록 설계되고 구성됩니다. 개발자는 이 라이브러리를 사용하고 모범 사례를 따를 것을 적극 권장합니다. 을(를) 참조하십시오. [Git 링크](https://github.com/adobe/aem-testing-clients) 자세한 내용

## 로컬 테스트 실행 {#local-test-execution}

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
