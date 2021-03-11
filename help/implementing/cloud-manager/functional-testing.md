---
title: 기능 테스트 - Cloud Services
description: 기능 테스트 - Cloud Services
translation-type: tm+mt
source-git-commit: 765334cff443d56e37f578647af4bcd133509481
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---


# 기능 테스트 {#functional-testing}

기능 테스트는 다음 3가지 유형으로 분류됩니다.

* 제품 기능 테스트
* 사용자 정의 기능 테스트
* 사용자 정의 UI 테스트

## 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 AEM의 핵심 기능(예: 작성 및 복제)을 중심으로 안정된 HTTP 통합 테스트 세트로, 이 핵심 기능을 위반하는 경우 애플리케이션 코드에 대한 고객 변경 사항이 배포되지 않도록 합니다.

고객이 Cloud Manager에 새 코드를 배포할 때마다 제품 기능 테스트가 자동으로 실행되므로 건너뛸 수 없습니다.

샘플 테스트를 보려면 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke)를 참조하십시오.

## 사용자 지정 기능 테스트 {#custom-functional-testing}

파이프라인의 사용자 지정 기능 테스트 단계는 항상 존재하며 건너뛸 수 없습니다.

그러나 빌드로 생성된 테스트 JAR가 없으면 기본적으로 테스트가 전달됩니다.

>[!NOTE]
>**로그 다운로드** 단추를 사용하면 테스트 실행 세부 양식의 로그가 포함된 ZIP 파일에 액세스할 수 있습니다. 이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 이러한 로그는 일반 다운로드 또는 세부 로그 기능을 사용하여 액세스할 수 있습니다. 자세한 내용은 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md)를 참조하십시오.

## 사용자 지정 UI 테스트 {#custom-ui-testing}

AEM은 애플리케이션을 원활하게 업데이트할 수 있도록 고객에게 Cloud Manager 품질 게이트의 통합 세트를 제공합니다. 특히 IT 테스트 게이트를 통해 이미 고객은 AEM API를 사용하는 자체 테스트를 작성하고 자동화할 수 있습니다.

사용자 지정 UI 테스트 기능은 고객이 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있도록 하는 선택적 기능 [고객 옵트인](#customer-opt-in)입니다. UI 테스트는 Selenium 기반 테스트로, Java 및 Maven, Node 및 WebDriver.io와 같은 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)에서 광범위한 선택을 할 수 있도록 Docker 이미지에 패키지되어 있습니다. 여기에서 UI를 빌드하고 UI 테스트를 작성하는 방법에 대해 자세히 알아볼 수 있습니다. 또한 AEM 프로젝트 원형을 사용하여 UI 테스트 프로젝트를 손쉽게 생성할 수 있습니다.

고객은 GIT을 통해 맞춤형 테스트와 UI용 테스트 세트를 만들 수 있습니다. UI 테스트는 특정 단계 및 피드백 정보와 함께 각 Cloud Manager 파이프라인에 대한 특정 품질 게이트의 일부로 실행됩니다. 회귀 및 새 기능을 비롯한 모든 UI 테스트를 통해 고객 컨텍스트 내에서 오류를 감지하고 보고할 수 있습니다.

고객 UI 테스트는 &quot;사용자 정의 UI 테스트&quot; 단계의 프로덕션 파이프라인에서 자동으로 실행됩니다.

java로 작성된 HTTP 테스트인 사용자 지정 기능 테스트와 달리, UI 테스트는 [UI 테스트 작성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=en#building-ui-tests)에 정의된 규칙을 따르는 한 모든 언어로 작성된 테스트가 있는 문서 이미지가 될 수 있습니다.

>[!NOTE]
>[AEM Project Tranype](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)에 편리하게 제공되는 구조 및 언어 *(js and wdio)*&#x200B;을(를) 따라 시작하는 것이 좋습니다.

### 고객 옵트인 {#customer-opt-in}

UI 테스트를 작성하고 실행하려면 고객은 UI 테스트 하위 모듈의 pom.xml 파일 옆에 있는 UI 테스트를 위한 mahen 하위 모듈 아래의 코드 저장소에 파일을 추가하여 &quot;옵트인&quot;을 하고 이 파일이 작성된 `tar.gz` 파일의 루트에 있는지 확인해야 합니다.

*파일 이름*:  `testing.properties`

*내용*:  `one line: ui-tests.version=1`

내장 `tar.gz` 파일에 없는 경우 UI 테스트 빌드 및 실행을 건너뜁니다.

>[!NOTE]
>이 섹션에 설명된 대로 UI 테스트를 사용하려면 2021년 2월 10일 이전에 생성된 프로덕션 파이프라인을 업데이트해야 합니다. 이것은 기본적으로 사용자가 프로덕션 파이프라인을 편집하고 UI에서 **저장**을 클릭해야 한다는 것을 의미합니다(변경 사항이 없는 경우).
>파이프라인 구성에 대한 자세한 내용은 [CI-CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)을 참조하십시오.

### 기능 테스트 작성 중 {#writing-functional-tests}

고객이 작성한 기능 테스트는 AEM에 배포할 아티팩트와 동일한 Maven 빌드에서 생성된 별도의 JAR 파일로 패키지화해야 합니다. 일반적으로 이 모듈은 별도의 메이벤 모듈입니다. 결과 JAR 파일에는 모든 필수 종속성이 포함되어야 하며, 일반적으로 jar-with-dependencies 설명자를 사용하여 maven-assembly-plugin을 사용하여 만듭니다.

또한 JAR에는 Cloud-Manager-TestType 매니페스트 헤더가 integration-test로 설정되어 있어야 합니다. 향후 헤더 값이 추가로 지원될 것으로 예상됩니다. maven-assembly-plugin에 대한 구성 예는 다음과 같습니다.

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

예를 들어 `com.myco.tests.aem.ExampleIT`이라는 클래스가 실행되지만 `com.myco.tests.aem.ExampleTest`이라는 클래스는 실행되지 않습니다.

테스트 클래스는 일반적인 JUnit 테스트여야 합니다. 테스트 인프라는 aem-testing-clients 테스트 라이브러리에서 사용하는 규칙과 호환되도록 설계되고 구성됩니다. 개발자는 이 라이브러리를 사용하고 모범 사례를 따를 것을 적극 권장합니다. 자세한 내용은 [Git 링크](https://github.com/adobe/aem-testing-clients)를 참조하십시오.

### 로컬 테스트 실행 {#local-test-execution}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans 등과 같은 주요 Java IDE에서 실행할 수 있습니다.

그러나 이러한 테스트를 실행할 때는 aem-testing-clients(및 기본 Sling Testing Clients)에 의해 기대되는 다양한 시스템 속성을 설정해야 합니다.

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

