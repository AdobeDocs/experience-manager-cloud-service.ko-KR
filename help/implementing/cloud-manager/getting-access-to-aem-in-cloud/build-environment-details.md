---
title: 빌드 환경
description: Cloud Manager의 빌드 환경과 코드 빌드 및 테스트 방법에 대해 알아봅니다.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 77%

---


# 빌드 환경 {#build-environment}

Cloud Manager의 빌드 환경과 코드 빌드 및 테스트 방법에 대해 알아봅니다.

## 빌드 환경 세부 정보 {#build-environment-details}

Cloud Manager는 특수 빌드 환경을 사용하여 코드를 빌드하고 테스트합니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 22.04에서 파생되었습니다.
* Apache Maven 3.9.4가 설치되어 있습니다.
   * Adobe는 사용자가 [HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트할 것](#https-maven)을 권장합니다.
* 설치된 Java 버전은 Oracle JDK 11.0.22 및 Oracle JDK 8u401입니다.
* **중요**: 기본적으로 `JAVA_HOME` 환경 변수는 Oracle JDK 8u401을 포함하는 `/usr/lib/jvm/jdk1.8.0_401`(으)로 설정됩니다. *_JDK 11_*&#x200B;을 사용하려면 AEM Cloud Projects에서 이 기본값을 재정의해야 합니다. 자세한 내용은 [Maven JDK 버전 설정](#alternate-maven-jdk-version) 섹션을 참조하십시오.
* 필요한 몇 가지 추가 시스템 패키지가 설치되어 있습니다.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* [추가 시스템 패키지 설치](#installing-additional-system-packages) 섹션에 설명된 대로 빌드 시 다른 패키지를 설치할 수 있습니다.
* 모든 빌드는 깨끗한 환경에서 수행되며, 빌드 컨테이너는 실행 사이에 어떤 상태도 유지하지 않습니다.
* Maven은 항상 다음 세 가지 명령을 사용하여 실행됩니다.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven은 `adobe-public`이라는 프로필을 사용하여 자동으로 공개 Adobe 아티팩트 저장소를 포함하는 `settings.xml` 파일로 시스템 수준에서 구성됩니다. 자세한 내용은 [Adobe 공개 Maven 저장소](https://repo1.maven.org/)를 참조하십시오.

>[!NOTE]
>
>Cloud Manager에서는 `jacoco-maven-plugin`의 특정 버전을 정의하지는 않지만 사용되는 버전은 `0.7.5.201505241946` 이상이어야 합니다.

## HTTPS Maven 저장소 {#https-maven}

Cloud Manager [릴리스 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md)에서는 빌드 환경에 대한 롤링 업데이트(릴리스 2023.12.0으로 완료)를 시작했으며, 여기에는 Maven 3.8.8 업데이트가 포함되어 있습니다. Maven 3.8.1에 도입된 주요 변경 사항은 잠재적인 취약점을 완화하기 위한 보안 강화 기능입니다. 구체적으로 Maven은 이제 [Maven 릴리스 정보](http://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)에 설명된 바와 같이 안전하지 않은 모든 `http://*` 미러를 기본적으로 비활성화합니다.

이러한 보안 강화로 인해 일부 사용자는 빌드 단계에서 문제에 직면할 수 있으며, 특히 안전하지 않은 HTTP 연결을 사용하는 Maven 저장소에서 아티팩트를 다운로드할 때 이와 같은 문제가 보다 빈번하게 발생할 수 있습니다.

업데이트된 버전을 원활하게 사용하기 위해 Adobe는 사용자가 HTTP 대신 HTTPS를 사용하도록 Maven 저장소를 업데이트할 것을 권장합니다. 이러한 조정은 업계에서 점점 더 보안 통신 프로토콜로 전환하는 추세에 맞춰 안전하고 안정적인 빌드 프로세스를 유지하는 데 도움이 될 것으로 기대합니다.

### 특정 Java 버전 사용 {#using-java-support}

기본적으로 프로젝트는 Oracle 8 JDK를 사용하는 Cloud Manager 빌드 프로세스를 통해 빌드되지만 AEM Cloud Service 고객은 Maven을 실행하는 데 사용되는 JDK 버전을 `11`(으)로 설정하는 것이 좋습니다.

#### Maven JDK 버전 설정 {#alternate-maven-jdk-version}

`.cloudmanager/java-version` 파일에서 전체 Maven 실행에 대한 JDK 버전을 `11`(으)로 설정하는 것이 좋습니다.

이렇게 하려면 파이프라인에서 사용하는 git 저장소 분기에 `.cloudmanager/java-version`이라는 파일을 생성합니다. `11` 텍스트만 포함되도록 파일을 편집합니다. Cloud Manager에서도 `8` 값을 허용하지만 이 버전은 더 이상 AEM Cloud Service 프로젝트에 지원되지 않습니다. 다른 모든 값은 무시됩니다. `11`을(를) 지정하면 Oracle 11이 사용되고 `JAVA_HOME` 환경 변수가 `/usr/lib/jvm/jdk-11.0.22`(으)로 설정됩니다.

## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 할 수도 있습니다.

예를 들어 작성 시간 JavaScript 축소가 gulp와 같은 도구를 통해 이루어진다면 스테이징과 프로덕션을 위한 빌드가 아닌 개발 환경을 위한 빌드를 만들 때 다른 축소 수준을 사용하려는 욕구가 있을 수 있습니다.

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

### 파이프라인 변수 {#pipeline-variables}

빌드 프로세스가 git 저장소에 배치하기에 부적절하거나 동일한 분기를 사용하는 파이프라인 실행 간에 달라져야 하는 특정 구성 변수에 따라 달라질 수 있습니다.

자세한 내용은 [파이프라인 변수 구성](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) 문서를 참조하십시오

## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

완벽한 작동을 위해서는 일부 빌드에 추가 시스템 패키지를 설치해야 합니다. 예를 들어 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으며 적절한 언어 인터프리터가 설치되어 있어야 합니다. 이 작업은 APT를 호출하기 위해 `pom.xml`에서 [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/)를 호출하여 수행할 수 있습니다. 이 실행은 일반적으로 Cloud Manager 전용 Maven 프로필로 래핑해야 합니다. 이 예에서는 Python을 설치합니다.

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
