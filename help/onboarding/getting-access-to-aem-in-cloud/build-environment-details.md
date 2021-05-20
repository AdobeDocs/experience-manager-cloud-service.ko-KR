---
title: 빌드 환경 세부 정보
description: 빌드 환경 세부 사항 - Cloud Services
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: c3b70f513455dfeaac6bc20c05fc9c35dcddf73e
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# 빌드 환경 이해 {#understanding-build-environment}

## 빌드 환경 세부 정보 {#build-environment-details}

Cloud Manager는 전문 빌드 환경을 사용하여 코드를 빌드하고 테스트합니다. 이 환경에는 다음 속성이 있습니다.

* 빌드 환경은 Ubuntu 18.04에서 파생된 Linux 기반입니다.
* Apache Maven 3.6.0이 설치됩니다.
* 설치된 Java 버전은 Oracle JDK 8u202 및 11.0.2입니다.
* 필요한 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* [아래에 설명된 대로 다른 패키지는 빌드 시간에 설치할 수 있습니다.](#installing-additional-system-packages)
* 모든 빌드는 원시 환경에서 수행됩니다.빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 다음 세 가지 명령을 사용하여 실행됩니다.

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent packageco-maven-plugin:prepare-agent package`
* Maven은 `adobe-public` 프로필을 사용하여 공용 Adobe **Artifact** 저장소를 자동으로 포함하는 settings.xml 파일을 사용하여 시스템 수준에서 구성됩니다. (자세한 내용은 [Public Maven 저장소 Adobe](https://repo.adobe.com/) 를 참조하십시오.)

>[!NOTE]
>Cloud Manager에서 `jacoco-maven-plugin`의 특정 버전을 정의하지는 않지만 사용되는 버전은 적어도 `0.7.5.201505241946`이어야 합니다.

### Java 11 지원 사용 {#using-java-support}

Cloud Manager는 이제 Java 8과 Java 11을 모두 사용하여 고객 프로젝트 빌드를 지원합니다. 기본적으로 프로젝트는 Java 8을 사용하여 빌드됩니다.

프로젝트에서 Java 11을 사용하려는 고객은 [Apache Maven Toolchain 플러그인](https://maven.apache.org/plugins/maven-toolchains-plugin/)을 사용하여 이를 수행할 수 있습니다.

이렇게 하려면 pom.xml 파일에서 다음과 같은 `<plugin>` 항목을 추가합니다.

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
           </jdk>
        </toolchains>
    </configuration>
</plugin>
```

>[!NOTE]
>지원되는 공급업체 값은 `oracle` 및 `sun`이며, 지원되는 버전 값은 `1.8`, `1.11` 및 `11`입니다.

>[!NOTE]
>Cloud Manager 프로젝트 빌드는 여전히 Java 8을 사용하여 Maven을 호출하고 있으므로 [Apache Maven Enforcer 플러그인](https://maven.apache.org/enforcer/maven-enforcer-plugin/)과 같은 플러그인을 통해 도구 체인 플러그인에 구성된 Java 버전을 확인하거나 적용하면 작동하지 않으므로 이러한 플러그인을 사용하지 않아야 합니다.

## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

경우에 따라 고객은 프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 합니다.

예를 들어, 빌드 타임 JavaScript 축소가 수행되는 경우 gulp와 같은 도구를 통해 개발 환경을 구축할 때 스테이지 및 프로덕션을 위해 빌드하는 것이 아니라 다른 축소 수준을 사용하려는 경우가 있을 수 있습니다.

이를 지원하기 위해 Cloud Manager는 모든 실행을 위해 이러한 표준 환경 변수를 빌드 컨테이너에 추가합니다.

| **변수 이름** | **정의** |
|---|---|
| CM_BUILD | 항상 &quot;true&quot;로 설정합니다. |
| 분기 | 실행을 위해 구성된 분기 |
| CM_PIPELINE_ID | 숫자 파이프라인 식별자 |
| CM_PIPELINE_NAME | 파이프라인 이름 |
| CM_PROGRAM_ID | 숫자 프로그램 식별자 |
| CM_PROGRAM_NAME | 프로그램 이름 |
| ARTIFACTS_VERSION | 스테이지 또는 프로덕션 파이프라인의 경우 Cloud Manager에서 생성한 가상 버전 |
| CM_AEM_PRODUCT_VERSION | 릴리스 이름 |

### 파이프라인 변수 {#pipeline-variables}

경우에 따라 고객의 빌드 프로세스는 Git 리포지토리에 배치하기에 적합하지 않거나 동일한 분기를 사용하여 파이프라인 실행 간에 변경해야 하는 특정 구성 변수에 따라 달라질 수 있습니다.

Cloud Manager를 사용하면 이러한 변수를 파이프라인별로 Cloud Manager API 또는 Cloud Manager CLI를 통해 구성할 수 있습니다. 변수는 일반 텍스트로 저장되거나, 나머지는 암호화될 수 있습니다. 어느 경우든 변수는 빌드 환경 내에서 `pom.xml` 파일 또는 다른 빌드 스크립트 내에서 참조할 수 있는 환경 변수로 사용할 수 있습니다.

CLI를 사용하여 변수를 설정하려면 다음과 같은 명령을 실행합니다.

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

현재 변수를 나열할 수 있습니다.

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

변수 이름에는 영숫자와 밑줄(_) 문자만 사용할 수 있습니다. 규칙에 의해, 이름은 모두 대문자여야 합니다. 파이프라인당 변수 제한은 200개입니다. 문자열 유형 변수의 경우 각 이름은 100자 미만이어야 하며, secretString 유형 변수의 경우 각 값은 2048자 미만이어야 합니다.

`Maven pom.xml` 파일 내에서 사용하는 경우 일반적으로 다음과 유사한 구문을 사용하여 이러한 변수를 Maven 속성에 매핑하는 것이 좋습니다.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

일부 빌드는 완전히 작동하려면 추가 시스템 패키지를 설치해야 합니다. 예를 들어, 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으므로 적절한 언어 해석기를 설치해야 합니다. 이 작업은 [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/)을 호출하여 APT를 호출하여 수행할 수 있습니다. 일반적으로 이 실행은 Cloud Manager 관련 Maven 프로필에 래핑되어야 합니다. 예를 들어, python을 설치하려면

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

이와 동일한 기술을 사용하여 언어 특정 패키지(예: RubyGems의 경우 `gem` 사용, Python 패키지의 경우 `pip` 사용)를 설치할 수 있습니다.

>[!NOTE]
>이러한 방식으로 시스템 패키지를 설치하면 Adobe Experience Manager을 실행하는 데 사용되는 런타임 환경에 **을 설치하지 않습니다.** AEM 환경에 시스템 패키지가 설치되어 필요한 경우 Adobe 담당자에게 문의하십시오.
