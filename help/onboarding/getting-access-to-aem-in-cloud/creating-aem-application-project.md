---
title: AEM 애플리케이션 프로젝트 - 클라우드 서비스
description: AEM 애플리케이션 프로젝트 - 클라우드 서비스
translation-type: tm+mt
source-git-commit: 57206e36725e28051b2468d47da726e318bd763b

---


# Creating an AEM Application Project {#aem-application-project}

## 마법사를 사용하여 AEM 애플리케이션 프로젝트 만들기 {#using-wizard-to-create-an-aem-application-project}

Cloud Manager를 사용하면 신규 고객을 유치하기 위해 최소한의 AEM 프로젝트를 시작점으로 만들 수 있습니다. 이 프로세스는 AEM 프로젝트 [**원형형을 기반으로 합니다&#x200B;**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Cloud Manager에서 AEM 애플리케이션 프로젝트를 만들려면 아래 절차를 따르십시오.

1. Cloud Manager에 로그인하고 기본 프로그램 설정이 완료되면 저장소가 비어 있는 경우 **개요** 화면에 특별 작업 카드가 표시됩니다.

   ![](assets/create-wizard1.png)

1. 만들기를 **클릭하여** 분기 및 프로젝트 **만들기 화면으로** 이동합니다.

   ![](assets/create-wizard2.png)

1. 진행 **중인 프로젝트** 만들기 타일은 프로그램 개요 *화면에* 표시됩니다.

   ![](assets/create-wizard3.png)

1. 프로그램 만들기가 완료되면 [ **프로그램 개요** ] *페이지에 환경 추가 타일이* 나타납니다.
   ![](assets/create-wizard4.png)

   환경을 [추가 또는 관리하는](/help/implementing/cloud-manager/manage-environments.md) 방법에 대해서는 환경 관리를 참조하십시오.

## 프로젝트 설정 {#setting-up-your-project}

### 프로젝트 설정 세부 사항 수정 {#modifying-project-setup-details}

Cloud Manager를 사용하여 성공적으로 구축 및 배포하려면 기존 AEM 프로젝트가 몇 가지 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven을 사용하여 빌드해야 합니다.
* Git 저장소의 루트에 *pom.xml* 파일이 있어야 합니다. 이 *pom.xml* 파일은 하위 모듈 수를 참조할 수 있으며, 이 경우 다른 하위 모듈 등이 있을 수 있습니다. 필요한 경우.

* pom.xml 파일에서 추가 Maven 객체 저장소에 대한 참조를 추가할 *수* 있습니다. 그러나 암호로 보호되거나 네트워크로 보호된 객체 저장소에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 *target* 디렉토리에 포함되어 있는 컨텐츠 패키지 *zip*&#x200B;파일을 스캔하여 검색합니다. 모든 수의 하위 모듈에서는 컨텐츠 패키지를 생성할 수 있습니다.

* 배포 가능한 Dispatcher 객체는 *conf* 및 *conf*. *d라는 이름의 디렉토리가 있는 zip* 파일을 스캔하여 *검색합니다(다시 target*&#x200B;디렉토리에 포함).

* 두 개 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서가 보장되지 않습니다. 특정 주문이 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다. 배포에서 패키지를 [건너뛸](#skipping-content-packages) 수 있습니다.


## 빌드 환경 세부 사항 {#build-environment-details}

Cloud Manager는 전문 빌드 환경을 사용하여 코드를 빌드하고 테스트합니다. 이 환경에는 다음과 같은 속성이 있습니다.

* 빌드 환경은 Linux 기반이며 Ubuntu 18.04에서 파생된 것입니다.
* Apache Maven 3.6.0이 설치되어 있습니다.
* 설치된 Java 버전은 Oracle JDK 8u202입니다.
* 다음과 같은 몇 가지 추가 시스템 패키지가 설치되어 있습니다.

   * bzip2
   * 압축 해제
   * libpng
   * imagemagick
   * graphicsmagick

* 다른 패키지는 [아래에](#installing-additional-system-packages)설명된 대로 빌드 시에 설치할 수 있습니다.
* 모든 빌드는 본래 환경에서 수행됩니다.빌드 컨테이너는 실행 사이에 상태를 유지하지 않습니다.
* Maven은 항상 명령을 사용하여 실행됩니다. *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:pree-agent package*
* Maven은 공개 Adobe Artifact 저장소를 자동으로 포함하는 settings.xml 파일을 사용하여 시스템 수준에서 **구성됩니다** . (자세한 내용은 [Adobe Public Maven](https://repo.adobe.com/) Repository를 참조하십시오.)


## 환경 변수 {#environment-variables}

### 표준 환경 변수 {#standard-environ-variables}

경우에 따라 고객은 프로그램 또는 파이프라인에 대한 정보를 기반으로 빌드 프로세스를 변경해야 합니다.

예를 들어, gulp와 같은 도구를 통해 빌드 시간 JavaScript 축소가 수행되는 경우, 준비 및 제작을 위해 만드는 것이 아니라 개발 환경을 만들 때 다른 축소 수준을 사용하려고 할 수 있습니다.

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


### 사용자 지정 환경 변수 {#custom-environ-variables}

경우에 따라 고객의 빌드 프로세스는 git 리포지토리에 배치하기에 부적절한 특정 구성 변수에 따라 달라질 수 있습니다. Cloud Manager를 사용하면 Adobe 담당자가 고객별로 이러한 변수를 구성할 수 있습니다. 이러한 변수는 보안 저장소 위치에 저장되며 특정 고객의 빌드 컨테이너에서만 볼 수 있습니다. 이 기능을 사용하려는 고객은 Adobe 담당자에게 문의하여 변수를 구성해야 합니다.

구성되면 이러한 변수를 환경 변수로 사용할 수 있습니다. 이러한 속성을 Maven 속성으로 사용하려면 위에서 설명한 프로필 내에서 pom.xml 파일에서 참조할 수 있습니다.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>환경 변수 이름에는 영숫자와 밑줄(_) 문자만 사용할 수 있습니다. 관례에 따라, 이름은 모두 대문자여야 합니다.

## Cloud Manager에서 Maven 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우, 개발자 워크스테이션에서 실행되는 경우와 달리 Cloud Manager 내에서 실행할 때 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우 Maven [프로필을](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) 사용하여 Cloud Manager를 비롯한 다양한 환경에서 빌드가 어떻게 달라야 하는지 정의할 수 있습니다.

Cloud Manager 빌드 환경 내에서 Maven 프로필의 활성화는 위에 설명된 CM_BUILD 환경 변수를 검색하여 수행해야 합니다. Conversly, Cloud Manager 빌드 환경 외에서만 사용되는 프로필은 이 변수의 유용성을 찾아 수행해야 합니다.

예를 들어 빌드가 Cloud Manager 내에서 실행될 때만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

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

빌드가 Cloud Manager 외부에서 실행될 때만 간단한 메시지를 출력하려는 경우 다음을 수행합니다.

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


## 추가 시스템 패키지 설치 {#installing-additional-system-packages}

일부 빌드는 완전히 작동하려면 추가 시스템 패키지를 설치해야 합니다. 예를 들어 빌드는 Python 또는 Ruby 스크립트를 호출할 수 있으므로 적절한 언어 인터프리터가 설치되어 있어야 합니다. 이 작업은 APT를 호출하기 위해 [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) 을 호출하여 수행할 수 있습니다. 이 실행은 일반적으로 클라우드 관리자 전용 Maven 프로필로 래핑되어야 합니다. 예를 들어 Python을 설치하려면:

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

이와 동일한 기술을 사용하여 RubyGems용 또는 Python Packages용 `gem` 등 언어별 패키지를 설치할 `pip` 수 있습니다.

>[!NOTE]
>
>이러한 방식으로 시스템 패키지를 설치해도 Adobe Experience Manager 실행에 사용되는 런타임 환경에서는 설치하지 **않습니다** . AEM 환경에 시스템 패키지를 설치해야 하는 경우 Adobe 담당자에게 문의하십시오.

## 콘텐츠 패키지 건너뛰기 {#skipping-content-packages}

Cloud Manager에서 빌드는 콘텐츠 패키지를 수에 관계없이 생성할 수 있습니다.
다양한 이유로, 컨텐츠 패키지를 배포하지 않고 제품화하는 것이 좋을 수 있습니다. 예를 들어, 테스트용으로만 사용되거나 빌드 프로세스의 다른 단계에 의해 다시 패키지되는 컨텐츠 패키지를 작성할 때, 즉 다른 패키지의 하위 패키지로 유용할 수 있습니다.

이러한 시나리오를 수용하기 위해 Cloud Manager는 ***빌드된 콘텐츠 패키지의*** 속성에서 cloudManagerTarget이라는 속성을 찾습니다. 이 속성을 none으로 설정하면 패키지를 건너뛰고 배포하지 않습니다. 이 속성을 설정하는 메커니즘은 빌드가 콘텐츠 패키지를 생성하는 방법에 따라 다릅니다. 예를 들어 filevault-maven-plugin을 사용하면 다음과 같이 플러그인을 구성할 수 있습니다.

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
