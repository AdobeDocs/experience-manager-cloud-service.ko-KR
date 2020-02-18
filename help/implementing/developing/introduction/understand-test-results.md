---
title: 테스트 결과 이해 - 클라우드 서비스
description: 테스트 결과 이해 - 클라우드 서비스
translation-type: tm+mt
source-git-commit: e1504c73e443d449f8fc9d5fbad433ea1a298843

---


# 테스트 결과 이해 {#understand-test-results}

Cloud Manager for Cloud Services 파이프라인 실행은 스테이지 환경에 대해 실행되는 테스트 실행을 지원합니다. 이는 실행 중인 AEM 환경에 대한 액세스 없이 오프라인으로 실행되는 빌드 및 단위 테스트 단계 동안 실행된 테스트와 대비됩니다.
이 컨텍스트에서는 두 가지 유형의 테스트가 실행됩니다.
* 고객이 직접 작성한 테스트
* Adobe 서면 테스트

두 테스트 유형은 모두 이러한 유형의 테스트를 실행하기 위해 설계된 컨테이너화된 인프라에서 실행됩니다.


## 코드 품질 테스트 {#code-quality-testing}

파이프라인의 일부로서 소스 코드가 스캔되어 배포가 특정 품질 기준을 충족하는지 확인합니다. 현재 이 기능은 SonarQube와 OakPAL을 사용한 컨텐츠 패키지 수준 검사를 조합하여 구현됩니다. 일반 Java 규칙과 AEM 특정 규칙을 결합하는 100개 이상의 규칙이 있습니다. 다음 표에는 테스트 기준에 대한 등급이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약점 <br/>B = 최소 1개의 작은 취약점<br/> C = 최소 1개의 주요 취약점 D = 최소 1 <br/>개의 치명적인 취약점 <br/>E = 최소 1개의 차단기 취약점 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 보조 버그 <br/>C = 최소 1개의 주요 버그 D = <br/>최소 1개의 중요 버그 E = 최소 1개의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 교정 비용은 다음과 같습니다. <br/><ul><li>&lt;=5%의 시간이 이미 애플리케이션에 들어갔지만, 등급은 A입니다. </li><li>평점은 6-10% 사이입니다. </li><li>평점은 11~20% 사이입니다. </li><li>평점은 21-50% 사이입니다.</li><li>50% 이상이 E입니다.</li></ul> | 중요 사항 | &lt; A |
| 범위 | 이 공식을 사용한 단위 테스트 라인 적용 범위와 조건 적용 범위의 혼합: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>위치:CT = 유닛 테스트를 실행하는 동안 최소 한 번 &#39;true&#39;로 평가된 조건 <br/>= CF = 장치 테스트를 실행하는 동안 최소 한 번 &#39;false&#39;로 평가된 조건 <br/>LC = 적용 라인 = lines_to_cover - indexed_lines <br/><br/> B = 총 조건 수 <br/>EL = 실행 라인의 총 수(lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | > 1 |
| 미해결 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 1 |
| 중복된 라인 | 중복된 블록에 포함된 라인 수입니다. <br/>코드 블록을 중복으로 간주하는 경우: <br/><ul><li>**Java가 아닌 프로젝트:**</li><li>연속 토큰과 중복 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 최소 다음 항목에 대해 분산되어야 합니다. </li><li>COBOL을 위한 코드 줄 30개 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li><li>**Java 프로젝트:**</li><li> 토큰 수와 줄 수에 관계없이 연속 문을 10개 이상 포함해야 합니다.</li></ul> <br/>중복 여부를 검색하는 동안 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |


>[!NOTE]
>
>자세한 정의는 [지표 정의를](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) 참조하십시오.

여기에서 규칙 목록을 다운로드할 수 있습니다. [code-quality-rules.xlsx](/help/implementing/cloud-manager/assets/CodeQuality-Rules-new-one.xlsx)

>[!NOTE]
>
>Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에 대한 자세한 [!UICONTROL 내용은]사용자 [지정 코드 품질 규칙을 참조하십시오](/help/implementing/cloud-manager/custom-code-quality-rules.md).

### 잘못된 긍정 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 &quot;거짓 긍정&quot;이라고 합니다.

이러한 경우, 소스 코드에 주석 속성으로 규칙 ID를 지정하는 표준 Java `@SuppressWarnings` 주석으로 주석을 달 수 있습니다. 예를 들어, 한 가지 일반적인 문제는 하드 코딩된 암호를 검색하는 SonarQube 규칙이 하드 코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

특정 예를 보려면 이 코드가 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube는 Blocker Vulnerability를 발생시킵니다. 코드를 검토한 후 이 취약점이 아님을 확인하고 적절한 규칙 ID로 이 코드에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나, 반면에 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 하드 코딩된 암호를 제거하는 것이 좋습니다.

>[!NOTE]
>
>주석을 가능한 구체적으로 지정하는 것이 가장 좋은 방법이지만, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 달 수 있으며 클래스 수준에서 주석을 달 수도 있습니다. `@SuppressWarnings`

## 기능 테스트 작성 {#writing-functional-tests}

고객이 작성한 기능 테스트는 AEM에 배포할 아티팩트와 동일한 Maven 빌드에서 생성된 별도의 JAR 파일로 패키지화해야 합니다. 일반적으로 이 모듈은 별도의 Maven 모듈입니다. 결과 JAR 파일은 필요한 모든 종속성을 포함해야 하며 일반적으로 jar-with-dependencies 설명자를 사용하여 maven-assembly-plugin을 사용하여 만듭니다.

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

이 JAR 파일 내에서 실행할 실제 테스트의 클래스 이름은 IT에서 종료되어야 합니다.

예를 들어 이름이 지정된 클래스는 `com.myco.tests.aem.ExampleIT` 실행되지만 이름이 지정된 클래스는 실행되지 `com.myco.tests.aem.ExampleTest` 않습니다.

테스트 클래스는 일반 JUnit 테스트여야 합니다. 테스트 인프라는 aem-testing-clients 테스트 라이브러리에서 사용하는 규칙과 호환되도록 디자인되고 구성됩니다. 개발자는 이 라이브러리를 사용하고 모범 사례를 따를 것을 적극 권장합니다. 자세한 내용은 [Git](https://github.com/adobe/aem-testing-clients) 링크를 참조하십시오.

## 사용자 정의 기능 테스트 {#custom-functional-test}

파이프라인의 사용자 지정 기능 테스트 단계는 항상 존재하며 건너뛸 수 없습니다.

그러나 빌드에 의해 생성된 테스트 JAR가 없으면 기본적으로 테스트가 전달됩니다. 이 단계는 단계 배포 직후 수행됩니다.

>[!NOTE]
>[ **로그** 다운로드] 단추를 사용하면 테스트 실행 세부 양식에 대한 로그가 포함된 ZIP 파일에 액세스할 수 있습니다. 이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 이러한 로그는 일반 다운로드 또는 세부 로그 기능을 사용하여 액세스할 수 있습니다. 자세한 내용은 [로그 액세스 및 관리를](/help/implementing/cloud-manager/manage-logs.md) 참조하십시오.

## 로컬 테스트 실행 {#local-test-execution}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans 등과 같은 주요 Java IDE에서 실행할 수 있습니다.

그러나 이러한 테스트를 실행할 때 반드시 aem-testing-clients(및 기본 Sling Testing Clients)가 기대하는 다양한 시스템 속성을 설정해야 합니다.

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