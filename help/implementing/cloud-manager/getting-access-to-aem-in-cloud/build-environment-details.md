---
title: Cloud Manager의 빌드 환경
description: Cloud Manager의 빌드 환경과 코드 빌드 및 테스트 방법에 대해 알아봅니다.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: e5404de6baae5373aefe5d03894864965b47b049
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 30%

---


# 빌드 환경 {#build-environment}

Cloud Manager의 빌드 환경과 코드 빌드 및 테스트 방법에 대해 알아봅니다.

>[!TIP]
>
>이 문서에서는 AEM as a Cloud Service 프로젝트 개발을 위한 Cloud Manager의 빌드 환경에 대해 설명합니다. AEM as a Cloud Service에서 콘텐츠 작성을 위해 지원하는 클라이언트 플랫폼에 대한 자세한 내용은 문서 [지원되는 클라이언트 플랫폼](/help/overview/supported-platforms.md)을 참조하십시오.

## 빌드 환경 세부 정보 {#build-environment-details}

Cloud Manager는 특수 빌드 환경을 사용하여 코드를 빌드하고 테스트합니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 22.04에서 파생되었습니다.
* Apache Maven 3.9.4가 설치되어 있습니다.
   * Adobe는 사용자가 [HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트할 것](#https-maven)을 권장합니다.
<!-- OLD Removed 1/16/25 * The Java versions installed are Oracle JDK 11.0.22 and Oracle JDK 8u401. -->
* 설치된 Java 버전은 Oracle JDK 11.0.22, Oracle JDK 17.0.10 및 Oracle JDK 21.0.4입니다.

<!-- OLD Removed 1/16/25 * **IMPORTANT:** By default, the JAVA_HOME environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. This default should be overridden for AEM Cloud Projects to use JDK 11. See the Setting the Maven JDK Version section for more details. -->
* **중요:** 기본적으로 `JAVA_HOME` 환경 변수는 Oracle JDK 8u401을 포함하는 `/usr/lib/jvm/jdk1.8.0_401`(으)로 설정됩니다. ***AEM Cloud Projects에서 JDK 21(기본 설정), 17 또는 11***&#x200B;을 사용하려면 이 기본값을 재정의해야 합니다. 자세한 내용은 [Maven JDK 버전 설정](#alternate-maven-jdk-version) 섹션을 참조하십시오.
* 필요한 몇 가지 추가 시스템 패키지가 설치되어 있습니다.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* [추가 시스템 패키지 설치](#installing-additional-system-packages) 섹션에 설명된 대로 빌드 시 다른 패키지를 설치할 수 있습니다.
* 각 빌드는 깨끗한 환경에서 실행되며, 빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 다음 세 가지 명령을 사용하여 실행됩니다.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven은 `adobe-public`이라는 프로필을 사용하여 자동으로 공개 Adobe 아티팩트 저장소를 포함하는 `settings.xml` 파일로 시스템 수준에서 구성됩니다. 자세한 내용은 [Adobe 공개 Maven 저장소](https://repo1.maven.org/)를 참조하십시오.

>[!NOTE]
>
>Cloud Manager에서는 `jacoco-maven-plugin`의 특정 버전을 정의하지는 않지만 사용되는 버전은 `0.7.5.201505241946` 이상이어야 합니다.

## HTTPS Maven 저장소 {#https-maven}

Cloud Manager [릴리스 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md)에서는 빌드 환경에 대한 롤링 업데이트(릴리스 2023.12.0으로 완료)를 시작했으며, 여기에는 Maven 3.8.8 업데이트가 포함되어 있습니다. Maven 3.8.1에 도입된 주요 변경 사항은 잠재적인 취약점을 완화하기 위한 보안 강화 기능입니다. 구체적으로 Maven은 이제 [Maven 릴리스 정보](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)에 설명된 바와 같이 안전하지 않은 모든 `http://*` 미러를 기본적으로 비활성화합니다.

이러한 보안 강화로 인해 일부 사용자는 빌드 단계에서 문제에 직면할 수 있으며, 특히 안전하지 않은 HTTP 연결을 사용하는 Maven 저장소에서 아티팩트를 다운로드할 때 이와 같은 문제가 보다 빈번하게 발생할 수 있습니다.

업데이트된 버전을 원활하게 사용하기 위해 Adobe는 사용자가 HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트할 것을 권장합니다. 이러한 조정은 업계에서 점점 더 보안 통신 프로토콜로 전환하는 추세에 맞춰 안전하고 안정적인 빌드 프로세스를 유지하는 데 도움이 될 것으로 기대합니다.

<!-- OLD below Removed 1/16/25

### Use a specific Java version

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 11. -->

<!-- OLD below Removed 1/16/25

#### Set the Maven JDK version

Adobe recommends that you set the JDK version for the entire Maven execution to `11` in a `.cloudmanager/java-version file`.

To do so, create a file named `.cloudmanager/java-version` in the git repository branch used by the pipeline. Edit the file so that it contains only the text, `11`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `11` is specified, Oracle 11 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-11.0.22`. -->

### 특정 Java 버전 사용 {#using-java-support}

Cloud Manager 빌드 프로세스는 Oracle 8 JDK를 사용하여 기본적으로 프로젝트를 빌드하지만 AEM Cloud Service 고객은 Maven 실행 JDK 버전을 21(권장), 17 또는 11로 설정해야 합니다.

#### Maven JDK 버전 설정 {#alternate-maven-jdk-version}

Maven 실행 JDK를 설정하려면 파이프라인에서 사용하는 Git 저장소 분기에 `.cloudmanager/java-version`(이)라는 파일을 만드십시오. `21` 또는 `17` 텍스트만 포함되도록 파일을 편집합니다. Cloud Manager에서도 `8` 값을 허용하지만 이 버전은 더 이상 AEM Cloud Service 프로젝트에 지원되지 않습니다. 다른 모든 값은 무시됩니다. `21` 또는 `17`을(를) 지정하면 Oracle Java 21 또는 Oracle Java 17이 사용됩니다.


#### Java 21 또는 Java 17을 사용하여 빌드로 마이그레이션하기 위한 사전 요구 사항 {#prereq-for-building}

Java 21 또는 Java 17을 사용하여 빌드로 마이그레이션하려면 먼저 최신 SonarQube 버전으로 업그레이드해야 합니다. 자세한 내용은 [Cloud Manager 2025.1.0의 릴리스 노트](/help/implementing/cloud-manager/release-notes/current.md#what-is-new)를 참조하십시오.

응용 프로그램을 새 Java 빌드 버전 및 런타임 버전으로 마이그레이션할 때 프로덕션에 배포하기 전에 개발 및 스테이지 환경에서 철저하게 테스트하십시오.

다음 배포 전략을 권장합니다.

1. https://experience.adobe.com/#/downloads에서 다운로드할 수 있는 Java 21로 로컬 SDK을 실행하고 애플리케이션을 배포하고 기능을 확인합니다. 로그에서 클래스 로딩 또는 바이트코드 직조 문제를 나타내는 오류가 없는지 확인합니다.
1. Java 21을 buildtime Java 버전으로 사용하도록 Cloud Manager 저장소에서 분기를 구성하고 이 분기를 사용하도록 DEV 파이프라인을 구성하고 파이프라인을 실행합니다. 유효성 검사 테스트를 실행합니다.
1. Java 21을 buildtime Java 버전으로 사용하도록 스테이지/프로덕션 파이프라인을 구성하고 파이프라인을 실행합니다.

##### 일부 번역 기능 {#translation-features}

다음 기능은 Java 21 런타임에 배포될 때 올바르게 작동하지 않을 수 있으며 Adobe은 이러한 문제를 2025년 초까지 해결할 것으로 예상합니다.

* 사람 번역을 사용할 때 `XLIFF`(XML 로컬라이제이션 교환 파일 형식)이(가) 실패합니다.
* 최신 Java 버전의 Locale 생성자가 변경되어 `I18n`(국제화)에서 언어 로케일 히브리어(`he`), 인도네시아어(`in`) 및 이디시(`yi`)를 제대로 처리하지 못합니다.

#### 런타임 요구 사항 {#runtime-requirements}

Java 21 런타임은 Java 21 및 Java 17을 사용하는 빌드에 사용되며 점차적으로 Java 11 빌드에도 적용됩니다(아래 참고 사항 참조). Java 21 업데이트를 수신하려면 환경이 AEM 릴리스 17098 이상 최신이어야 합니다. 호환성을 보장하려면 다음 조정이 필요합니다.

라이브러리 업데이트는 이전 Java 버전과 호환되는 상태로 유지되므로 언제든지 적용할 수 있습니다.

* **ASM의 최소 버전:**
`org.ow2.asm.*` 아티팩트에 번들로 제공되는 Java 패키지 `org.objectweb.asm`의 사용을 버전 9.5 이상으로 업데이트하여 최신 JVM 런타임 지원을 보장합니다.

* **Groovy의 최소 버전:**
최신 JVM 런타임 지원을 위해 Java 패키지 `org.apache.groovy` 또는 `org.codehaus.groovy`의 사용을 버전 4.0.22 이상으로 업데이트합니다.

  이 번들은 AEM Groovy Console과 같은 서드파티 종속성을 추가함으로써 간접적으로 포함될 수 있습니다.

AEM Cloud Service SDK은 Java 21과 호환되며, Cloud Manager 파이프라인을 실행하기 전에 Java 21과 프로젝트의 호환성을 확인하는 데 사용할 수 있습니다.

* **런타임 매개 변수 편집:**
Java 21을 사용하여 로컬로 AEM을 실행하는 경우 `MaxPermSize` 매개 변수로 인해 시작 스크립트(`crx-quickstart/bin/start` 또는 `crx-quickstart/bin/start.bat`)가 실패합니다. 해결 방법으로 스크립트에서 `-XX:MaxPermSize=256M`을(를) 제거하거나 환경 변수 `CQ_JVM_OPTS`을(를) 정의하여 `-Xmx1024m -Djava.awt.headless=true`(으)로 설정합니다.

  이 문제는 AEM Cloud Service SDK 버전 19149 이상에서 해결되었습니다.

>[!IMPORTANT]
>
>`.cloudmanager/java-version`을(를) `21` 또는 `17`(으)로 설정하면 Java 21 런타임이 배포됩니다. Java 21 런타임은 2025년 2월 4일 화요일부터 모든 환경(코드가 Java 11로 빌드된 환경뿐만 아니라)에 점진적 롤아웃을 예약합니다. 롤아웃은 샌드박스 및 개발 환경에서 시작된 다음 2025년 4월에 모든 프로덕션 환경으로 롤아웃됩니다. Java 21 런타임 *이전*&#x200B;을(를) 채택하려는 고객은 [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)에서 Adobe에 문의할 수 있습니다.


#### 빌드 시간 요구 사항 {#build-time-reqs}

Java 21 및 Java 17을 사용하여 프로젝트를 작성할 수 있으려면 다음 조정이 필요합니다. 이전 Java 버전과 호환되므로 Java 21 및 Java 17을 실행하기 전이라도 업데이트할 수 있습니다.

AEM Cloud Service 고객은 새로운 언어 기능을 활용할 수 있도록 가능한 한 빨리 Java 21로 프로젝트를 빌드하는 것이 좋습니다.

* **최소 버전 `bnd-maven-plugin`:**
최신 JVM 실행 시간을 지원하려면 `bnd-maven-plugin`의 사용을 버전 6.4.0으로 업데이트하십시오.

  버전 7 이상은 Java 11 이하와 호환되지 않으므로 해당 버전으로 업그레이드하는 것은 권장되지 않습니다.

* **최소 버전 `aemanalyser-maven-plugin`:**
최신 JVM 실행 시간을 지원하려면 `aemanalyser-maven-plugin`의 사용을 버전 1.6.6 이상으로 업데이트하십시오.

* **최소 버전 `maven-bundle-plugin`:**
최신 JVM 실행 시간을 지원하려면 `maven-bundle-plugin`의 사용을 버전 5.1.5 이상으로 업데이트하십시오.

  버전 6 이상은 Java 11 이하와 호환되지 않으므로 해당 버전으로 업그레이드하는 것은 권장되지 않습니다.

* **`maven-scr-plugin`의 종속성 업데이트:**
`maven-scr-plugin`은(는) Java 21 또는 Java 17과 직접 호환되지 않습니다. 그러나 다음 예와 같이 플러그인 구성에서 ASM 종속성 버전을 업데이트하여 설명자 파일을 생성할 수 있습니다.

```XML
<project>
  ...
  <build>
    ...
    <plugins>
      ...
      <plugin>
        <groupId>org.apache.felix</groupId>
        <artifactId>maven-scr-plugin</artifactId>
        <version>1.26.4</version>
        <executions>
          <execution>
            <id>generate-scr-scrdescriptor</id>
            <goals>
              <goal>scr</goal>
            </goals>
          </execution>
        </executions>
        <dependencies>
          <dependency>
            <groupId>org.ow2.asm</groupId>
            <artifactId>asm-analysis</artifactId>
            <version>9.7.1</version>
            <scope>compile</scope>
          </dependency>
        </dependencies>
      </plugin>
      ...
    </plugins>
    ...
  </build>
  ...
</project>
```

## 환경 변수 - 표준 {#environment-variables}

프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 할 수도 있습니다.

예를 들어 gulp와 같은 도구를 사용하여 빌드 시 JavaScript 축소가 발생하는 경우 다양한 환경에 대해 다른 축소 수준이 선호될 수 있습니다. 개발 빌드는 스테이징 및 프로덕션에 비해 더 가벼운 축소 수준을 사용할 수 있습니다.

이를 지원하기 위해 Cloud Manager는 모든 실행 시 빌드 컨테이너에 이러한 표준 환경 변수를 추가합니다.

| 변수 이름 | 정의 |
|---|---|
| `CM_BUILD` | 항상 `true`로 설정 |
| `BRANCH` | 실행에 대해 구성된 분기 |
| `CM_PIPELINE_ID` | 숫자 파이프라인 식별자 |
| `CM_PIPELINE_NAME` | 파이프라인 이름 |
| `CM_PROGRAM_ID` | 숫자 프로그램 식별자 |
| `CM_PROGRAM_NAME` | 프로그램 이름 |
| `ARTIFACTS_VERSION` | 스테이지 또는 프로덕션 파이프라인의 경우 Cloud Manager에서 생성된 통합 버전 |
| `CM_AEM_PRODUCT_VERSION` | 릴리스 버전 |

## 환경 변수 - 파이프라인 {#pipeline-variables}

빌드 프로세스에는 Git 저장소에 저장해서는 안 되는 특정 구성 변수가 필요할 수 있습니다. 또한 동일한 분기를 사용하는 파이프라인 실행 간에 이러한 변수를 조정해야 할 수 있습니다.

자세한 내용은 [파이프라인 변수 구성](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md)도 참조하십시오.

## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

일부 빌드가 완전히 작동하려면 추가 시스템 패키지가 필요합니다. 예를 들어 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으며 적절한 언어 인터프리터가 설치되어 있어야 합니다. APT를 호출하기 위해 `pom.xml`에서 [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/)을(를) 호출하여 이 설치 프로세스를 관리할 수 있습니다. 이 실행은 일반적으로 Cloud Manager 전용 Maven 프로필로 래핑해야 합니다. 이 예에서는 Python을 설치합니다.

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

이와 동일한 기술을 사용하여 언어별 패키지를 설치할 수 있습니다. 예를 들어 RubyGems의 경우 `gem` 또는 Python 패키지의 경우 `pip`를 사용할 수 있습니다.

>[!NOTE]
>
>이 방법으로 시스템 패키지를 설치하면 Adobe Experience Manager 실행에 사용되는 런타임 환경에 설치되지 않습니다. AEM 환경에 시스템 패키지를 설치해야 하는 경우 Adobe 담당자에게 문의하십시오.

>[!TIP]
>
>프론트엔드 빌드 환경에 대한 자세한 내용은 [프론트엔드 파이프라인으로 Sites 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)을 참조하십시오.
