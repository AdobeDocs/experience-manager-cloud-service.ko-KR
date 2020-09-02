---
title: 빌드 환경 세부 사항
description: 빌드 환경 세부 사항 - Cloud Services
translation-type: tm+mt
source-git-commit: 3344e6a8c0c09903f44606673106d884516b4471
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---


# 빌드 환경 이해 {#understanding-build-environment}

## 빌드 환경 세부 사항 {#build-environment-details}

Cloud Manager는 전문적인 빌드 환경을 사용하여 코드를 작성하고 테스트합니다. 이 환경에는 다음과 같은 속성이 있습니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 18.04에서 파생됩니다.
* Apache Maven 3.6.0이 설치되어 있습니다.
* 설치된 Java 버전은 Oracle JDK 8u202 및 11.0.2입니다.
* 다음과 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * 압축 해제
   * libpng
   * imagemagick
   * graphicsmagick

* 다른 패키지는 [아래](#installing-additional-system-packages)설명에 따라 빌드 시간에 설치할 수 있습니다.
* 모든 빌드는 본래 환경에서 수행됩니다.빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 명령을 사용하여 실행됩니다. *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:pref-agent package*
* Maven은 공개 Adobe Artifact 저장소를 자동으로 포함하는 settings.xml 파일을 사용하여 시스템 수준에서 **구성됩니다** . (자세한 내용은 [Adobe Public Maven Repository](https://repo.adobe.com/) 를 참조하십시오.)

>[!NOTE]
>Cloud Manager가 특정 버전의 버전을 정의하지는 않지만, 사용된 버전 `jacoco-maven-plugin`은 적어도 같아야 합니다 `0.7.5.201505241946`.

### Java 11 지원 사용 {#using-java-support}

Cloud Manager는 이제 Java 8과 Java 11을 모두 사용하여 고객 프로젝트 작성을 지원합니다. 기본적으로 프로젝트는 Java 8을 사용하여 빌드됩니다.

프로젝트에서 Java 11을 사용하려는 고객은 [Apache Maven 도구 체인 플러그인을 사용할 수 있습니다](https://maven.apache.org/plugins/maven-toolchains-plugin/).

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
>지원되는 공급업체 값은 `oracle` 및 `sun`입니다.
>
>지원되는 버전 값은 `1.8`, `1.11`및 `11`입니다.

## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

경우에 따라 고객은 프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 합니다.

예를 들어, gulp와 같은 도구를 통해 빌드 타임 JavaScript 미니폴리션을 수행하는 경우, 준비 및 제작을 위해 만드는 것이 아니라 개발 환경을 위해 빌드할 때 다른 미니어션 수준을 사용하려고 할 수 있습니다.

이를 지원하기 위해 Cloud Manager는 모든 실행을 위해 이러한 표준 환경 변수를 빌드 컨테이너에 추가합니다.

| **변수 이름** | **정의** |
|---|---|
| CM_BUILD | 항상 &quot;true&quot;로 설정 |
| 분기 | 실행을 위해 구성된 분기 |
| CM_PIPELINE_ID | 숫자 파이프라인 식별자 |
| CM_PIPELINE_NAME | 파이프라인 이름 |
| CM_PROGRAM_ID | 숫자 프로그램 식별자 |
| CM_PROGRAM_NAME | 프로그램 이름 |
| ARTIFACTS_VERSION | 스테이지 또는 프로덕션 파이프라인의 경우 Cloud Manager에서 생성된 합성 버전 |
| CM_AEM_PRODUCT_VERSION | 릴리스 이름 |

### 파이프라인 변수 {#pipeline-variables}

경우에 따라 고객의 빌드 프로세스는 Git 리포지토리에 배치하기에 적합하지 않거나 동일한 분기를 사용하여 파이프라인 실행 간에 변경해야 하는 특정 구성 변수에 따라 달라질 수 있습니다.

Cloud Manager를 사용하면 이러한 변수를 Cloud Manager API 또는 Cloud Manager CLI를 통해 파이프라인별로 구성할 수 있습니다. 변수는 일반 텍스트로 저장하거나 안전하게 암호화할 수 있습니다. 두 경우 모두 빌드 환경 내에서 변수를 환경 변수로 사용할 수 있으며 이 변수는 `pom.xml` 파일 또는 기타 빌드 스크립트 내에서 참조할 수 있습니다.

CLI를 사용하여 변수를 설정하려면 다음과 같은 명령을 실행합니다.

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

현재 변수는 나열할 수 있습니다.

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

변수 이름에는 영숫자 및 밑줄(_) 문자만 사용할 수 있습니다. 관례상, 이름은 모두 대문자여야 합니다. 파이프라인당 변수 수는 200자로 제한됩니다. 각 이름은 100자 미만이어야 하며, 각 값은 2048자 미만이어야 합니다.

파일 내에서 사용하는 경우 일반적으로 다음과 유사한 구문을 사용하여 이러한 변수를 Maven 속성에 매핑하는 것이 유용합니다. `Maven pom.xml`

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

일부 빌드는 완전히 작동하도록 추가 시스템 패키지를 설치해야 합니다. 예를 들어 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으므로 적절한 언어 인터프리터를 설치해야 합니다. 이 작업은 APT를 호출하기 위해 [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) 을 호출하여 수행할 수 있습니다. 이 실행은 일반적으로 클라우드 관리자별 Maven 프로필로 둘러싸야 합니다. 예를 들어, python을 설치하려면:

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

이와 동일한 기술을 사용하여 RubyGems용 또는 Python Packages `gem` 용 언어 관련 패키지를 설치할 수 `pip` 있습니다.

>[!NOTE]
>
>이러한 방식으로 시스템 패키지를 설치해도 Adobe Experience Manager을 실행하는 데 사용되는 런타임 환경에 설치되지 **않습니다** . AEM 환경에 시스템 패키지를 설치해야 하는 경우 Adobe 담당자에게 문의하십시오.