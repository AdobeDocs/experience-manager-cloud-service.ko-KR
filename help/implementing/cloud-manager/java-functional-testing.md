---
title: Java™ 기능 테스트
description: AEM as a Cloud Service를 위한 Java™ 기능 테스트를 작성하는 방법을 알아봅니다.
exl-id: e014b8ad-ac9f-446c-bee8-adf05a6b4d70
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 95%

---

# Java™ 기능 테스트

AEM as a Cloud Service를 위한 Java™ 기능 테스트를 작성하는 방법을 알아봅니다.

## 기능 테스트 시작하기 {#getting-started-functional-tests}

Cloud Manager에서 새 코드 저장소를 만들면 `it.tests` 폴더와 샘플 테스트 사례가 자동으로 만들어집니다.

>[!NOTE]
>
>Cloud Manager에서 `it.tests` 폴더를 자동으로 만들기 전에 저장소가 만들어진 경우 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests)을 사용하여 최신 버전을 생성할 수도 있습니다.

`it.tests` 폴더에 콘텐츠가 생기면 자체 테스트를 위한 기반으로 이를 사용할 수 있으며, 이후 다음과 같은 작업을 수행할 수 있습니다.

1. [테스트 사례를 개발합니다.](#writing-functional-tests)
1. [로컬에서 테스트를 실행합니다.](#local-test-execution)
1. Cloud Manager 저장소에 코드를 커밋하고 Cloud Manager 파이프라인을 실행합니다.

## 사용자 정의 기능 테스트 작성 {#writing-functional-tests}

Adobe가 제품 기능 테스트를 작성하는 데 사용하는 것과 동일한 도구를 사용하여 사용자 정의 기능 테스트를 작성할 수 있습니다. 테스트 작성 방법의 예로 GitHub의 [제품 기능 테스트](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke)를 사용하십시오.

사용자 정의 기능 테스트를 위한 코드는 프로젝트의 `it.tests` 폴더에 있는 Java™ 코드입니다. 모든 기능 테스트와 함께 단일 JAR을 생성해야 합니다. 빌드가 둘 이상의 테스트 JAR을 생성하는 경우 선택되는 JAR은 비결정적입니다. 테스트 JAR이 0이면 테스트 단계가 기본적으로 통과합니다. 샘플 테스트는 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests)을 참조하십시오.

테스트는 최소 두 개의 작성자 인스턴스, 두 개의 게시 인스턴스 및 Dispatcher 구성을 포함하여 Adobe에서 유지 관리하는 테스트 인프라에서 실행됩니다. 이렇게 설정하면 사용자 정의 기능 테스트가 전체 AEM 스택에 대해 실행됩니다.

### 기능 테스트 구조 {#functional-tests-structure}

사용자 정의 기능 테스트는 AEM에 배포할 아티팩트와 동일한 Maven 빌드에서 생성된 별도의 JAR 파일로 패키징되어야 합니다. 일반적으로 이 빌드는 별도의 Maven 모듈입니다. 결과 JAR 파일은 필요한 모든 종속성을 포함해야 하며 일반적으로 `jar-with-dependencies` 설명자를 사용하는 `maven-assembly-plugin`을 통해 생성됩니다.

또한 JAR의 `Cloud-Manager-TestType` 매니페스트 헤더가 `integration-test`로 설정되어야 합니다.

다음은 `maven-assembly-plugin`에 대한 예의 구성입니다.

```XML
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
</build>
```

이 JAR 파일 내에서 실행할 실제 테스트의 클래스 이름은 `IT`로 끝나야 합니다.

예를 들어 `com.myco.tests.aem.it.ExampleIT`라는 클래스는 실행되지만 `com.myco.tests.aem.it.ExampleTest`라는 클래스는 실행되지 않습니다.

또한 코드 스캔의 적용 범위 검사에서 테스트 코드를 제외하려면 테스트 코드가 `it`이라는 패키지 아래에 있어야 합니다(적용 범위 제외 필터는 `**/it/**/*.java`).

테스트 클래스는 일반 JUnit 테스트여야 합니다. 테스트 인프라는 `aem-testing-clients` 테스트 라이브러리에서 사용하는 규칙과 호환되도록 설계 및 구성됩니다. 개발자는 이 라이브러리를 사용하고 모범 사례를 따르는 것이 좋습니다.

자세한 내용은 [`aem-testing-clients`GitHub 저장소](https://github.com/adobe/aem-testing-clients)를 참조하십시오.

>[!TIP]
>
>[이 비디오를 시청](https://www.youtube.com/watch?v=yJX6r3xRLHU)하여 사용자 정의 기능 테스트를 사용하여 CI/CD 파이프라인에 대한 신뢰도를 높이는 방법을 알아보십시오.

### 사전 요구 사항 {#prerequisites}

1. Cloud Manager의 테스트는 기술 관리 사용자를 통해 실행됩니다.

>[!NOTE]
>
>로컬 시스템에서 기능 테스트를 실행하려면 동일한 동작이 가능하도록 관리자와 유사한 권한을 가진 사용자를 만드십시오.

1. 기능 테스트 범위가 지정된 컨테이너화된 인프라는 다음 경계로 제한됩니다.


| 유형 | 값 | 설명 |
|----------------------|-------|--------------------------------------------------------------------|
| CPU | 0.5 | 테스트 실행당 예약된 CPU 시간 |
| 메모리 | 0.5Gi | 테스트에 할당된 메모리 양(기비바이트 값) |
| 시간 초과 | 30m | 테스트가 종료되기까지의 기간입니다. |
| 권장 기간 | 15m | 이 시간보다 오래 걸리지 않도록 테스트를 작성하는 것이 좋습니다. |

>[!NOTE]
>
> 더 많은 리소스가 필요한 경우, 고객 지원 사례를 만들고 사용 사례를 설명하십시오. Adobe 팀에서 귀하의 요청을 검토하고 적절한 지원을 제공할 것입니다.

#### 종속성

* aem-cloud-testing-clients:

기능 테스트를 실행하는 데 사용되는 컨테이너화된 인프라의 향후 변경 사항에는 라이브러리가 필요합니다. [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) 최소 버전 이상으로 업데이트하기 위해 사용자 정의 기능 테스트에 사용됨 **1.2.1**
다음에서 종속성을 확인하십시오. `it.tests/pom.xml` 이(가) 업데이트되었습니다.

```
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

>[!NOTE]
>
>이 변경 사항은 2024년 4월 6일 이전에 수행되어야 합니다.
>종속성 라이브러리를 업데이트할 수 없으면 “사용자 정의 기능 테스트” 단계에서 파이프라인 오류가 발생합니다.

### 로컬 테스트 실행 {#local-test-execution}

Cloud Manager 파이프라인에서 기능 테스트를 활성화하기 전에 [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) 또는 실제 AEM as a Cloud Service 인스턴스를 사용하여 로컬에서 기능 테스트를 실행하는 것이 좋습니다.

#### IDE에서 실행 {#running-in-an-ide}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans와 같은 주요 Java™ IDE에서 실행할 수 있습니다. 제품 기능 테스트와 사용자 정의 기능 테스트는 모두 동일한 기술을 기반으로 하므로 둘 다 제품 테스트를 사용자 정의 테스트에 복사하여 로컬로 실행할 수 있습니다.

단, 이러한 테스트를 실행할 때 `aem-testing-clients`(및 기본 Sling 테스트 클라이언트) 라이브러리에서 예상하는 여러 시스템 속성을 설정해야 합니다.

시스템 속성은 다음과 같습니다.

| 속성 | 설명 | 예 |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | Cloud Service와 일치하도록 인스턴스의 수를 `2`로 설정해야 합니다. | `2` |
| `sling.it.instance.url.1` | 작성자 URL로 설정해야 합니다. | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | 첫 번째 인스턴스의 실행 모드를 `author`로 설정해야 합니다. | `author` |
| `sling.it.instance.adminUser.1` | 작성자 관리 사용자로 설정해야 합니다. | `admin` |
| `sling.it.instance.adminPassword.1` | 작성자 관리 암호로 설정해야 합니다. |                         |
| `sling.it.instance.url.2` | 게시 URL로 설정해야 합니다. | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | 두 번째 인스턴스의 실행 모드를 `publish`로 설정해야 합니다. | `publish` |
| `sling.it.instance.adminUser.2` | 게시 관리 사용자로 설정해야 합니다. | `admin` |
| `sling.it.instance.adminPassword.2` | 게시 관리 암호로 설정해야 합니다. |                         |



#### Maven을 사용하여 모든 테스트 실행 {#using-maven}

1. 셸을 열고 저장소의 `it.tests` 폴더로 이동합니다.

1. Maven을 사용하여 테스트를 시작하는 데 필요한 매개변수를 제공하는 다음 명령을 실행합니다.

```shell
mvn verify -Plocal \
    -Dit.author.url=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.author.user=<user> \
    -Dit.author.password=<password> \
    -Dit.publish.url=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.publish.user=<user> \
    -Dit.publish.password=<password>
```

