---
title: 기능 테스트
description: 코드의 품질과 안정성을 보장하기 위해 AEM as a Cloud Service 배포 프로세스에 빌드된 세 가지 다양한 기능 테스트에 대해 알아봅니다.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: f8d5b94d176dfbd5bcecf552f974dc77c5afe4e2
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---


# 기능 테스트 {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="기능 테스트"
>abstract="코드의 품질과 안정성을 보장하기 위해 AEM as a Cloud Service 배포 프로세스에 빌드된 세 가지 다양한 기능 테스트에 대해 알아봅니다."

에 빌드된 세 가지 다양한 기능 테스트 유형에 대해 알아봅니다 [AEM as a Cloud Service 배포 프로세스](/help/implementing/cloud-manager/deploy-code.md) 코드의 품질과 안정성을 보장하는 것.

## 개요 {#overview}

AEM as a Cloud Service에는 세 가지 유형의 기능 테스트가 있습니다.

* [제품 기능 테스트](#product-functional-testing)
* [사용자 지정 기능 테스트](#custom-functional-testing)
* [사용자 지정 UI 테스트](#custom-ui-testing)

모든 기능 테스트에 대해 자세한 테스트 결과를 `.zip` 파일을 **빌드 로그 다운로드** 빌드 개요 화면의 일부 [배포 프로세스.](/help/implementing/cloud-manager/deploy-code.md)

이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 해당 로그에 액세스하려면 문서를 참조하십시오 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 자세한 내용

제품 기능 테스트와 샘플 사용자 지정 기능 테스트는 모두 [AEM 테스트 클라이언트.](https://github.com/adobe/aem-testing-clients)

## 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 작성 및 복제 작업과 같은 AEM의 핵심 기능의 안정적인 HTTP 통합 테스트(IT) 세트입니다. 이러한 테스트는 Adobe에 의해 유지되며, 핵심 기능을 손상시키는 경우 사용자 지정 애플리케이션 코드에 대한 변경 사항이 배포되지 않도록 하기 위한 것입니다.

제품 기능 테스트는 Cloud Manager에 새 코드를 배포할 때마다 자동으로 실행되며 건너뛸 수 없습니다.

제품 기능 테스트는 오픈 소스 프로젝트로 유지 관리됩니다. 자세한 내용은 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) GitHub에서 자세히 알아보십시오.

## 사용자 지정 기능 테스트 {#custom-functional-testing}

제품 기능 테스트가 Adobe에 의해 정의되는 동안 자체 애플리케이션에 대해 자체 품질 테스트를 작성할 수 있습니다. 이 작업은 애플리케이션의 품질을 보장하기 위해 프로덕션 파이프라인의 일부로 사용자 정의 기능 테스트로 실행됩니다.

사용자 지정 기능 테스트는 푸시 업그레이드와 사용자 지정 코드 배포에 대해 모두 실행되며, 이는 AEM 코드 변경 사항이 애플리케이션 코드를 중단시키지 않도록 하는 좋은 기능 테스트를 작성하는 데 특히 중요합니다. 사용자 지정 기능 테스트 단계는 항상 존재하며 건너뛸 수 없습니다.

### 사용자 지정 기능 테스트 작성 {#writing-functional-tests}

Adobe이 제품 기능 테스트를 작성하는 데 사용하는 것과 동일한 도구를 사용하여 사용자 지정 기능 테스트를 작성할 수 있습니다. 를 사용하십시오 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) GitHub에서 테스트를 작성하는 방법의 예입니다.

사용자 지정 기능 테스트의 코드는 `it.tests` 프로젝트의 폴더입니다. 모든 기능 테스트가 포함된 단일 JAR를 생성해야 합니다. 빌드에서 두 개 이상의 테스트 JAR를 생성하는 경우 선택한 JAR가 비결정적입니다. 테스트 JAR이 0이면 기본적으로 테스트 단계가 전달됩니다. [AEM 프로젝트 원형 을 참조하십시오](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) 샘플 테스트.

테스트는 두 개 이상의 작성자 인스턴스, 두 개의 게시 인스턴스 및 디스패처 구성을 포함하여 Adobe 유지 관리 테스트 인프라에서 실행됩니다. 즉, 사용자 지정 기능 테스트가 전체 AEM 스택에 대해 실행됩니다.

사용자 지정 기능 테스트는 AEM에 배포할 아티팩트와 동일한 Maven 빌드에서 생성한 별도의 JAR 파일로 패키지해야 합니다. 일반적으로 이는 별도의 Maven 모듈입니다. 결과 JAR 파일에는 모든 필수 종속성이 포함되어야 하며, 일반적으로 `maven-assembly-plugin` 사용 `jar-with-dependencies` 설명자입니다.

또한 JAR에는 `Cloud-Manager-TestType` 매니페스트 헤더가 `integration-test`.

다음은 의 구성 예입니다 `maven-assembly-plugin`.

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

테스트 클래스는 일반적인 JUnit 테스트여야 합니다. 테스트 인프라는 `aem-testing-clients` 테스트 라이브러리. 개발자는 이 라이브러리를 사용하고 모범 사례를 따를 것을 적극 권장합니다.

자세한 내용은 [`aem-testing-clients` GitHub 리포지토리](https://github.com/adobe/aem-testing-clients) 자세한 내용

>[!TIP]
>
>[이 비디오 보기](https://www.youtube.com/watch?v=yJX6r3xRLHU) 사용자 지정 기능 테스트를 사용하여 CI/CD 파이프라인에 대한 신뢰도를 향상시키는 방법에 대해 설명합니다.

## 사용자 지정 UI 테스트 {#custom-ui-testing}

사용자 지정 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택 기능입니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다.

문서를 참조하십시오 [사용자 지정 UI 테스트](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) 추가 정보.

## 로컬 테스트 실행 {#local-test-execution}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans 등과 같은 메인스트림 Java IDE에서 실행할 수 있습니다. 제품 기능 테스트와 사용자 지정 기능 테스트는 모두 동일한 기술을 기반으로 하므로 두 테스트 모두 제품 테스트를 사용자 지정 테스트에 복사하여 로컬에서 실행할 수 있습니다.

그러나 이러한 테스트를 실행할 때는 `aem-testing-clients` (및 기본 Sling Testing Clients) 라이브러리입니다.

시스템 속성은 다음과 같습니다.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the publish URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
