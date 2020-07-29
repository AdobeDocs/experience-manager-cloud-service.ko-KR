---
title: AEM 애플리케이션 프로젝트 - Cloud Service
description: AEM 애플리케이션 프로젝트 - Cloud Service
translation-type: tm+mt
source-git-commit: 9e27ff9510fda5ed238a25b2d63d1d9a3099a8b5
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 0%

---


# AEM 애플리케이션 프로젝트 만들기 {#aem-application-project}

## 마법사를 사용하여 AEM 응용 프로그램 프로젝트 만들기 {#using-wizard-to-create-an-aem-application-project}

새로운 고객을 위한 Cloud Manager의 시작점으로 최소한의 AEM 프로젝트를 제작할 수 있습니다. 이 프로세스는 [**AEM 프로젝트 원형을 기반으로 합니다&#x200B;**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Cloud Manager에서 AEM 애플리케이션 프로젝트를 만들려면 아래 절차를 따르십시오.

1. Cloud Manager에 로그인하고 기본 프로그램 설정이 완료되면 저장소가 비어 있는 경우 **개요** 화면에 특별 작업 카드가 표시됩니다.

   ![](assets/create-wizard1.png)

1. 만들기 **를** 클릭하여 **분기 및 프로젝트** 만들기 화면으로 이동합니다.

   ![](assets/create-wizard2.png)

1. 프로젝트 **생성 진행** 중 타일이 *프로그램 개요* 화면에 표시됩니다.

   ![](assets/create-wizard3.png)

1. 프로그램 생성이 완료되면 **프로그램 개요** 페이지에 환경 *추가 타일이* 나타납니다.
   ![](assets/create-wizard4.png)

   환경을 [추가하거나 관리하는](/help/implementing/cloud-manager/manage-environments.md) 방법을 알려면 환경 관리를 참조하십시오.

## 프로젝트 설정 {#setting-up-your-project}

### 프로젝트 설정 세부 사항 수정 {#modifying-project-setup-details}

Cloud Manager를 사용하여 성공적으로 구축 및 배포하려면 기존 AEM 프로젝트는 몇 가지 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven을 사용하여 빌드해야 합니다.
* Git 저장소의 루트에 *pom.xml* 파일이 있어야 합니다. 이 *pom.xml* 파일은 하위 모듈을 여러 개 참조할 수 있으며, 이 경우 다른 하위 모듈 등이 있을 수 있습니다. 필요한 경우.

* pom.xml ** 파일에서 추가 Maven 객체 저장소에 대한 참조를 추가할 수 있습니다. 암호로 [보호된 객체 리포지토리에](#password-protected-maven-repositories) 대한 액세스는 구성 시 지원됩니다. 그러나 네트워크 보호 객체 저장소에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 *target* 이라는 디렉토리에 포함되어 있는 컨텐츠 패키지 *zip*&#x200B;파일을 검색하여 찾을 수 있습니다. 모든 수의 하위 모듈에서는 콘텐츠 패키지를 생성할 수 있습니다.

* 배포 가능한 Dispatcher 가공물은 *conf* 및 conf.d라는 이름의 디렉토리가 있는 zip *파일(* target *디렉토리에 포함됨)을 검색하여* **&#x200B;검색됩니다.

* 둘 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서가 보장되지 않습니다. 특정 주문이 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다. 배포에서 패키지를 [건너뛸](#skipping-content-packages) 수 있습니다.


## 빌드 환경 세부 사항 {#build-environment-details}

Cloud Manager는 전문적인 빌드 환경을 사용하여 코드를 작성하고 테스트합니다. 이 환경에는 다음과 같은 속성이 있습니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 18.04에서 파생됩니다.
* Apache Maven 3.6.0이 설치되어 있습니다.
* Java 버전이 Oracle JDK 8u202 및 11.0.2를 설치했습니다.
* 다음과 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * 압축 해제
   * libpng
   * imagemagick
   * graphicsmagick

* 다른 패키지는 [아래](#installing-additional-system-packages)설명에 따라 빌드 시간에 설치할 수 있습니다.
* 모든 빌드는 본래 환경에서 수행됩니다. 빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 명령을 사용하여 실행됩니다. *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:pref-agent package*
* Maven은 공개 Adobe Artifact 저장소를 자동으로 포함하는 settings.xml 파일을 사용하여 시스템 수준에서 **구성됩니다** . (자세한 내용은 [Adobe Public Maven Repository](https://repo.adobe.com/) 를 참조하십시오.)

>[!NOTE]
>Cloud Manager가 특정 버전의 버전을 정의하지는 않지만, 사용된 버전 `jacoco-maven-plugin`은 적어도 같아야 합니다 `0.7.5.201505241946`.


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

파일 내에서 사용할 경우, 일반적으로 다음과 유사한 구문을 사용하여 이러한 변수를 Maven 속성에 매핑하는 데 유용합니다. `Maven pom.xml`

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


## Cloud Manager에서 마스터 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우, 개발자 워크스테이션에서 실행되는 경우와 달리 Cloud Manager 내에서 실행할 때 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우 Maven [Profiles를](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) 사용하여 Cloud Manager를 비롯한 다양한 환경에서 빌드가 달라지는 방법을 정의할 수 있습니다.

Cloud Manager 빌드 환경 내에서 마스터 프로필의 활성화는 위에 설명된 CM_BUILD 환경 변수를 찾아 수행해야 합니다. Cloud Manager 빌드 환경 외부에서만 사용하도록 만들어진 프로필은 이 변수의 개념을 찾아 수행해야 합니다.

예를 들어 빌드가 Cloud Manager 내에서 실행되는 경우에만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>개발자 워크스테이션에서 이 프로파일을 테스트하려면 명령줄(포함) 또는 IDE(Integrated Development Environment)에서 활성화할 수 `-PcmBuild`있습니다.

빌드가 Cloud Manager 외부에서 실행되는 경우에만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## 암호로 보호된 Maven 리포지토리 지원 {#password-protected-maven-repositories}

Cloud Manager에서 암호로 보호된 Maven 리포지토리를 사용하려면 암호(및 사용자 이름(선택 사항)를 비밀 [파이프라인 변수로](#pipeline-variables) 지정한 다음 git 리포지토리에 있는 파일 `.cloudmanager/maven/settings.xml` 에서 해당 암호를 참조합니다. 이 파일은 [마비설정 파일](https://maven.apache.org/settings.html) 스키마를 따릅니다. Cloud Manager 빌드 프로세스가 시작되면 이 파일의 `<servers>` 요소가 Cloud Manager에서 제공하는 기본 `settings.xml` 파일로 병합됩니다. 이 파일을 적절히 사용하면 서버 ID가 파일 내의 `<repository>` 및/또는 `<pluginRepository>` 요소 내부에서 `pom.xml` 참조됩니다. 일반적으로 이러한 `<repository>` 및/또는 `<pluginRepository>` 요소는 [Cloud Manager별 프로필]{#activating-maven-profiles-in-cloud-manager}내에 포함되지만 반드시 필요한 것은 아닙니다.

예를 들어 저장소가 https://repository.myco.com/maven2에 있고 Cloud Manager가 사용해야 하는 사용자 이름 `cloudmanager` 은 is이고 암호는 is `secretword`라고 가정해 봅시다.

먼저 파이프라인에서 암호를 암호로 설정합니다.

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

그런 다음 `.cloudmanager/maven/settings.xml` 파일에서 다음을 참조합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

마지막으로 파일 내의 서버 ID를 `pom.xml` 참조합니다.

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
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

## 콘텐츠 패키지 건너뛰기 {#skipping-content-packages}

Cloud Manager에서 빌드는 콘텐츠 패키지를 수에 관계없이 생성할 수 있습니다.
다양한 이유로, 컨텐츠 패키지를 배포하지 않고 판매하는 것이 좋을 수 있습니다. 예를 들어 테스트용으로만 사용되는 컨텐츠 패키지를 빌드하거나 빌드 프로세스의 다른 단계에서 다시 패키지되는 컨텐츠 패키지, 즉 다른 패키지의 하위 패키지로 사용할 경우 유용합니다.

이러한 시나리오를 수용하기 위해 Cloud Manager는 내장 콘텐츠 패키지의 속성에서 ***cloudManagerTarget*** 이라는 속성을 찾습니다. 이 속성을 none으로 설정하면 패키지를 건너뛰고 배포할 수 없습니다. 이 속성을 설정하는 메커니즘은 빌드가 콘텐츠 패키지를 생성하는 방법에 따라 달라집니다. 예를 들어 filevault-maven-plugin을 사용하면 다음과 같이 플러그인을 구성할 수 있습니다.

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

content-package-maven-plugin은 다음과 유사합니다.

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```
