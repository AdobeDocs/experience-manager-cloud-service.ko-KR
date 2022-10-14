---
title: 기능 테스트
description: 코드의 품질과 신뢰성을 보장하기 위해 AEM as a Cloud Service 배포 프로세스에 내장된 세 가지 유형의 기능 테스트에 대해 알아봅니다.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: ht
source-wordcount: '898'
ht-degree: 100%

---


# 기능 테스트 {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="기능 테스트"
>abstract="코드의 품질과 신뢰성을 보장하기 위해 AEM as a Cloud Service 배포 프로세스에 내장된 세 가지 유형의 기능 테스트에 대해 알아봅니다."

코드의 품질과 신뢰성을 보장하기 위해 [AEM as a Cloud Service 배포 프로세스](/help/implementing/cloud-manager/deploy-code.md)에 내장된 세 가지 유형의 기능 테스트에 대해 알아봅니다.

## 개요 {#overview}

AEM as a Cloud Service의 기능 테스트에는 세 가지 유형이 있습니다.

* [제품 기능 테스트](#product-functional-testing)
* [사용자 정의 기능 테스트](#custom-functional-testing)
* [사용자 정의 UI 테스트](#custom-ui-testing)

모든 기능 테스트의 경우 [배포 프로세스](/help/implementing/cloud-manager/deploy-code.md)의 일부로 빌드 개요 화면에서 **빌드 로그 다운로드** 버튼을 사용하여 자세한 테스트 결과를 `.zip` 파일로 다운로드할 수 있습니다.

이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 이러한 로그에 액세스하는 방법에 대한 자세한 내용은 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 문서를 참조하십시오.

제품 기능 테스트와 샘플 사용자 정의 기능 테스트는 모두 [AEM 테스트 클라이언트](https://github.com/adobe/aem-testing-clients)를 기반으로 합니다.

## 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 작성 및 복제 작업과 같은 AEM의 핵심 기능에 대한 안정적인 HTTP 통합 테스트(IT) 세트입니다. 이러한 테스트는 Adobe에서 유지 관리하며 핵심 기능이 손상된 경우 사용자 정의 애플리케이션 코드에 대한 변경 사항이 배포되는 것을 방지하기 위함이 목적입니다.

제품 기능 테스트는 새 코드를 Cloud Manager에 배포할 때마다 자동으로 실행되며 건너뛸 수 없습니다.

제품 기능 테스트는 오픈 소스 프로젝트로 유지 관리됩니다. 자세한 내용은 GitHub의 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) 문서를 참조하십시오.

## 사용자 정의 기능 테스트 {#custom-functional-testing}

제품 기능 테스트는 Adobe에 의해 정의되지만 자체 애플리케이션에 대한 자체 품질 테스트를 작성할 수 있습니다. 이는 애플리케이션 품질을 보장하기 위해 프로덕션 파이프라인의 일부인 사용자 정의 기능 테스트로 실행됩니다.

사용자 정의 기능 테스트는 사용자 정의 코드 배포와 푸시 업그레이드 모두에 대해 실행되므로 AEM 코드 변경으로 인해 애플리케이션 코드가 손상되지 않도록 우수한 기능 테스트를 작성하는 것이 특히 중요합니다. 사용자 정의 기능 테스트 단계는 항상 존재하며 건너뛸 수 없습니다.

### 사용자 정의 기능 테스트 작성 {#writing-functional-tests}

Adobe가 제품 기능 테스트를 작성하는 데 사용하는 것과 동일한 도구를 사용하여 사용자 정의 기능 테스트를 작성할 수 있습니다. 테스트 작성 방법의 예로 GitHub의 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke)를 사용하십시오.

사용자 정의 기능 테스트를 위한 코드는 프로젝트의 `it.tests` 폴더에 있는 Java 코드입니다. 모든 기능 테스트와 함께 단일 JAR을 생성해야 합니다. 빌드가 둘 이상의 테스트 JAR을 생성하는 경우 선택되는 JAR은 비결정적입니다. 테스트 JAR이 0이면 테스트 단계가 기본적으로 통과합니다. 샘플 테스트는 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests)을 참조하십시오.

테스트는 최소 2개의 작성자 인스턴스, 2개의 게시 인스턴스 및 Dispatcher 구성을 포함하여 Adobe에서 유지 관리하는 테스트 인프라에서 실행됩니다. 즉, 사용자 정의 기능 테스트가 전체 AEM 스택에 대해 실행됩니다.

사용자 정의 기능 테스트는 AEM에 배포할 아티팩트와 동일한 Maven 빌드에서 생성된 별도의 JAR 파일로 패키징되어야 합니다. 일반적으로 이 모듈은 별도의 Maven 모듈입니다. 결과 JAR 파일은 필요한 모든 종속성을 포함해야 하며 일반적으로 `jar-with-dependencies` 설명자를 사용하는 `maven-assembly-plugin`을 통해 생성됩니다.

또한 JAR의 `Cloud-Manager-TestType` 매니페스트 헤더가 `integration-test`로 설정되어야 합니다.

다음은 `maven-assembly-plugin`에 대한 예의 구성입니다.

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

이 JAR 파일 내에서 실행할 실제 테스트의 클래스 이름은 `IT`로 끝나야 합니다.

예를 들어 `com.myco.tests.aem.it.ExampleIT`라는 클래스는 실행되지만 `com.myco.tests.aem.it.ExampleTest`라는 클래스는 실행되지 않습니다.

또한 코드 스캔의 적용 범위 검사에서 테스트 코드를 제외하려면 테스트 코드가 `it`이라는 패키지 아래에 있어야 합니다(적용 범위 제외 필터는 `**/it/**/*.java`).

테스트 클래스는 일반 JUnit 테스트여야 합니다. 테스트 인프라는 `aem-testing-clients` 테스트 라이브러리에서 사용하는 규칙과 호환되도록 설계 및 구성됩니다. 개발자는 이 라이브러리를 사용하고 모범 사례를 따르는 것이 좋습니다.

자세한 내용은 [`aem-testing-clients`GitHub 저장소](https://github.com/adobe/aem-testing-clients)를 참조하십시오.

>[!TIP]
>
>[이 비디오를 시청](https://www.youtube.com/watch?v=yJX6r3xRLHU)하여 사용자 정의 기능 테스트를 사용하여 CI/CD 파이프라인에 대한 신뢰도를 높이는 방법을 알아보십시오.

## 사용자 정의 UI 테스트 {#custom-ui-testing}

사용자 정의 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다. UI 테스트는 언어 및 프레임워크(예: Java 및 Maven, Node 및 WebDriver.io 또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)에서 다양한 선택을 허용하도록 도커 이미지에 패키징된 Selenium 기반 테스트입니다.

자세한 내용은 [사용자 정의 UI 테스트](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) 문서를 참조하십시오.

## 로컬 테스트 실행 {#local-test-execution}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans 등과 같은 주요 Java IDE에서 실행할 수 있습니다. 제품 기능 테스트와 사용자 정의 기능 테스트는 모두 동일한 기술을 기반으로 하므로 둘 다 제품 테스트를 사용자 정의 테스트에 복사하여 로컬로 실행할 수 있습니다.

그러나 이러한 테스트를 실행할 때 `aem-testing-clients`(및 기본 Sling 테스트 클라이언트) 라이브러리에서 예상하는 다양한 시스템 속성을 설정해야 합니다.

시스템 속성은 다음과 같습니다.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, for example, admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the publish URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
