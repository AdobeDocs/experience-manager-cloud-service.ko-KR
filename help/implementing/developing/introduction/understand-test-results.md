---
title: 테스트 결과 이해 - Cloud Services
description: 테스트 결과 이해 - Cloud Services
translation-type: tm+mt
source-git-commit: 736a7c8d56a957e511451b0ba06affd9643f75e5
workflow-type: tm+mt
source-wordcount: '1697'
ht-degree: 2%

---


# 테스트 결과 이해 {#understand-test-results}

클라우드 서비스에 대한 Cloud Manager 파이프라인 실행은 스테이지 환경에서 실행되는 테스트 실행을 지원합니다. 이는 실행 중인 AEM 환경에 대한 액세스 권한 없이 오프라인으로 실행되는 빌드 및 단위 테스트 단계 동안 실행된 테스트와 대비됩니다.

Cloud Manager에서 Cloud Services 파이프라인을 지원하는 세 가지 범주가 있습니다.

1. [코드 품질 테스트](#code-quality-testing)
1. [기능 테스트](#functional-testing)
1. [컨텐츠 감사 테스트](#content-audit-testing)

이러한 테스트는 다음을 수행할 수 있습니다.

* 고객 서면
* Adobe
* 오픈 소스 툴

   >[!NOTE]
   > 고객이 작성한 테스트와 Adobe으로 작성된 테스트 모두 이러한 유형의 테스트를 실행하기 위해 설계된 통합 인프라에서 실행됩니다.


## 코드 품질 테스트 {#code-quality-testing}

이 단계에서는 애플리케이션 코드의 품질을 평가합니다. 코드 품질만 파이프라인의 핵심 목표이며 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다.

다양한 유형의 파이프라인에 [대한 자세한 내용은 CI-CD 파이프라인](/help/implementing/cloud-manager/configure-pipeline.md) 구성을 참조하십시오.

### 사용자 지정 코드 품질 규칙 이해 {#understanding-code-quality-rules}

코드 품질 테스트에서는 소스 코드가 배포가 특정 품질 기준을 충족하는지 확인하기 위해 스캔됩니다. 현재 이 기능은 SonarQube와 OakPAL을 사용한 컨텐츠 패키지 레벨 검사를 조합하여 구현됩니다. 일반 Java 규칙과 AEM별 규칙을 결합하는 규칙이 100개 이상 있습니다. AEM별 규칙 중 일부는 AEM Engineering의 모범 사례를 기반으로 생성되며 [사용자 지정 코드 품질 규칙이라고 합니다](/help/implementing/cloud-manager/custom-code-quality-rules.md).

규칙 목록은 [여기에서 다운로드할 수 있습니다](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx).

이 단계의 결과는 *평등으로 전달됩니다*. 다음 표에 테스트 기준에 대한 등급이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약점 <br/>B = 최소 1개의 작은 취약점<br/> C = 최소 1개의 주요 취약점 <br/>D = 최소 1개의 치명적인 취약점 <br/>E = 최소 1개의 차단기 취약점 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 보조 버그 <br/>C = 최소 1개의 주요 버그 <br/>D = 최소 1개의 중요 버그 E = 최소 1개의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 수정 비용은 다음과 같습니다. <br/><ul><li>애플리케이션 사용 시간의 &lt;=5%, 평점은 A </li><li>평점 6~10% 사이의 B </li><li>평점은 11~20% </li><li>평점은 21~50%</li><li>50% 이상이 E입니다.</li></ul> | 중요 사항 | &lt; A |
| 범위 | 이 공식을 사용하여 단위 테스트 라인 적용 범위와 조건 적용 범위를 혼합합니다. <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where:CT = 장치 테스트를 실행하는 동안 최소 한 번 &#39;true&#39;로 평가된 조건 <br/>CF = 장치 테스트를 실행하는 동안 최소 한 번 &#39;false&#39;로 평가된 조건 <br/>LC = 적용 라인 = lines = lines_to_cover - inded_lines <br/><br/> B = 총 조건 수 <br/>EL = 실행 라인의 총 수(lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | > 1 |
| 미해결 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 라인 | 중복된 블록에 포함된 라인 수입니다. <br/>코드 블록을 중복으로 간주하는 경우: <br/><ul><li>**Java가 아닌 프로젝트:**</li><li>연속된 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 다음과 같은 경우에 배포해야 합니다. </li><li>COBOL을 위한 30줄의 코드 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li><li>**Java 프로젝트:**</li><li> 토큰과 줄 수에 관계없이 10개 이상의 연속문과 중복 문이 있어야 합니다.</li></ul> <br/>중복 여부를 검색하는 동안 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수입니다. | 정보 | > 0 |

>[!NOTE]
>
>자세한 [정의는 지표 정의를](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) 참조하십시오.


>[!NOTE]
>
>Cloud [!UICONTROL Manager에서]실행되는 사용자 지정 코드 품질 규칙에 대한 자세한 내용은 [사용자 지정 코드 품질 규칙을 참조하십시오](/help/implementing/cloud-manager/custom-code-quality-rules.md).

### 잘못된 양질 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며, 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 &#39;거짓 긍정&#39;이라고 한다.

이러한 경우, 소스 코드에 주석 달기 시 규칙 ID를 주석 속성으로 지정하는 표준 Java `@SuppressWarnings` 주석으로 주석을 달 수 있습니다. 예를 들어, 한 가지 일반적인 문제는 하드코딩된 암호를 검색하는 SonarQube 규칙이 하드 코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

특정 예를 살펴보려면, 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 이 코드가 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube가 Blocker 취약점을 발생시킵니다. 코드를 검토한 후 이 취약점이 아님을 확인하고 적절한 규칙 ID로 이 코드에 주석을 달 수 있습니다.

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

그러면 하드 코딩된 암호를 제거하는 것이 좋습니다.

>[!NOTE]
>
>주석을 가능한 구체적으로 지정하는 것이 가장 좋은 방법이지만, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 다는 것은 클래스 수준에서 주석을 달 수 있습니다. `@SuppressWarnings`

>[!NOTE]
>명시적 보안 테스트 단계는 없지만 코드 품질 단계 동안 평가된 보안 관련 코드 품질 규칙은 여전히 있습니다. Cloud Service의 보안에 대한 자세한 내용은 [AEM용 보안](/help/security/cloud-service-security-overview.md) 개요를 Cloud Service으로 참조하십시오.

## 기능 테스트 {#functional-testing}

기능 테스트는 두 가지 유형으로 분류됩니다.

* 제품 기능 테스트
* 사용자 정의 기능 테스트

### 제품 기능 테스트 {#product-functional-testing}

제품 기능 테스트는 AEM의 핵심 기능(예: 작성 및 복제)을 중심으로 안정된 HTTP 통합 테스트 세트로, 이 핵심 기능을 위반하는 경우 애플리케이션 코드에 대한 고객 변경 사항이 배포되지 않도록 합니다.

고객이 Cloud Manager에 새 코드를 배포하면 자동으로 제품 기능 테스트가 실행되므로 건너뛸 수 없습니다.

샘플 테스트에 대해서는 [제품 기능 테스트를](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) 참조하십시오.

### 사용자 정의 기능 테스트 {#custom-functional-testing}

파이프라인의 사용자 지정 기능 테스트 단계는 항상 존재하며 건너뛸 수 없습니다.

그러나 빌드로 생성된 테스트 JAR가 없으면 기본적으로 테스트가 전달됩니다.

>[!NOTE]
>[ **로그** 다운로드] 단추를 사용하면 테스트 실행 세부 양식에 대한 로그가 포함된 ZIP 파일에 액세스할 수 있습니다. 이러한 로그에는 실제 AEM 런타임 프로세스의 로그가 포함되지 않습니다. 이러한 로그는 일반 다운로드 또는 세부 로그 기능을 사용하여 액세스할 수 있습니다. 자세한 [내용은 로그](/help/implementing/cloud-manager/manage-logs.md) 액세스 및 관리를 참조하십시오.


#### 기능 테스트 작성 {#writing-functional-tests}

고객이 작성한 기능 테스트는 AEM에 배포할 가공물과 동일한 Maven 빌드에 의해 생성된 별도의 JAR 파일로 패키지화해야 합니다. 일반적으로 이 모듈은 별도의 Maven 모듈입니다. 결과 JAR 파일은 필요한 모든 종속성을 포함해야 하며, 일반적으로 jar-with-dependencies 설명자를 사용하여 maven-assembly-plugin을 사용하여 생성합니다.

또한 JAR에는 Cloud-Manager-TestType 매니페스트 헤더가 통합 테스트에 설정되어 있어야 합니다. 향후 헤더 값이 추가로 지원될 것으로 예상됩니다. maven-assembly-plugin에 대한 예제 구성은 다음과 같습니다.

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

테스트 클래스는 일반 JUnit 테스트여야 합니다. 테스트 인프라는 aem-testing-clients 테스트 라이브러리에 사용되는 규칙과 호환되도록 설계 및 구성됩니다. 개발자는 이 라이브러리를 사용하고 최상의 작업 방법을 따를 것을 적극 권장합니다. 자세한 내용은 [Git](https://github.com/adobe/aem-testing-clients) 링크를 참조하십시오.

#### 로컬 테스트 실행 {#local-test-execution}

테스트 클래스는 JUnit 테스트이므로 Eclipse, IntelliJ, NetBeans 등과 같은 주요 Java IDE에서 실행할 수 있습니다.

그러나 이러한 테스트를 실행할 때는 aem-testing-clients(및 기본 Sling Testing Clients)가 기대하는 다양한 시스템 속성을 설정해야 합니다.

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


## 컨텐츠 감사 테스트 {#content-audit-testing}

콘텐츠 감사는 Google의 오픈 소스 툴인 Lighthouse를 기반으로 하는 Cloud Manager Sites Production 파이프라인에서 사용할 수 있는 기능입니다. 이 기능은 모든 Cloud Manager 프로덕션 파이프라인에서 사용할 수 있습니다.

배포 프로세스를 검증하고 변경 사항이 배포되었는지 확인하는 데 도움이 됩니다.

1. 성능, 접근성, 모범 사례, SEO(검색 엔진 최적화) 및 PWA(점진적 웹 앱)에 대한 기준 표준을 준수합니다.

1. 이러한 차원에 회귀 현상을 포함하지 마십시오.

Cloud Manager의 콘텐츠 감사 기능을 사용하면 최종 사용자가 사이트의 디지털 경험을 최고 수준의 표준으로 유지할 수 있습니다. 이 결과는 정보 제공용이며 사용자가 현재 점수와 이전 점수 사이의 점수 및 변경 사항을 볼 수 있도록 합니다. 이러한 통찰력은 현재 배포에서 발생하는 회귀 여부를 확인하는 데 유용합니다.

### 컨텐츠 감사 결과 이해 {#understanding-content-audit-results}

컨텐츠 감사는 프로덕션 파이프라인 실행 페이지를 통해 집계된 세부 페이지 수준 테스트 결과를 제공합니다.

* 집계 수준 지표는 감사된 페이지의 평균 점수를 측정합니다.
* 드릴다운을 통해 개별 페이지 수준 점수를 사용할 수도 있습니다.
* 컨텐츠 감사 중 확인된 문제를 해결하는 방법에 대한 지침과 함께 개별 테스트의 결과가 무엇인지 확인하기 위해 점수의 세부 사항을 확인할 수 있습니다.
* 테스트 결과의 내역은 Cloud Manager 내에 유지되므로 고객은 파이프라인 실행에 도입된 변경 사항이 이전 실행의 회귀 여부를 확인할 수 있습니다.

#### 집계 점수 {#aggregate-scores}

각 테스트 유형(성능, 접근성, SEO, 우수 사례 및 PWA)에 대한 집계 수준 점수가 있습니다.

집계 수준 점수는 실행에 포함된 페이지의 평균 점수를 가져옵니다. 집계 수준의 변경은 현재 실행 내의 페이지의 평균 점수를 이전 실행의 평균 점수와 비교하여, 포함하여 구성된 페이지의 컬렉션이 실행 간에 변경된 경우에도 나타냅니다.

변경 지표의 값은 다음 중 하나일 수 있습니다.

* **양수 값** - 마지막 프로덕션 파이프라인 실행 이후 선택한 테스트에서 페이지가 개선되었습니다.

* **음수 값** - 마지막 프로덕션 파이프라인 실행 이후 선택한 테스트에서 페이지가 회귀되었습니다.

* **변경** 없음 - 마지막 프로덕션 파이프라인 실행 이후 페이지에 동일한 점수가 부여됨

* **N/A** - 비교할 이전 점수가 없습니다.

   <!-- ![](assets/content-audit-test1.png) -->

#### 페이지 수준 점수 {#page-level-scores}

테스트를 드릴다운하여 보다 자세한 페이지 수준 점수를 확인할 수 있습니다. 사용자는 테스트를 실행한 이전 시간의 변경과 함께 특정 테스트에 대해 개별 페이지의 점수가 어떻게 기록되는지 확인할 수 있습니다.

개별 페이지의 세부 사항을 클릭하면 평가된 페이지의 요소에 대한 정보와 개선 가능성이 감지되는 문제를 해결하는 지침을 제공합니다. 테스트 및 관련 지침의 세부 사항은 Google Lighthouse에서 제공합니다.

<!-- ![](assets/page-level-scores.png) -->

