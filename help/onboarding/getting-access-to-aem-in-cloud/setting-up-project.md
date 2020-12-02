---
title: 프로젝트 설정 세부 정보
description: 프로젝트 설정 세부 정보 - Cloud Services
translation-type: tm+mt
source-git-commit: 207d0742e8bf46065c7e20bec7d88b0776c246b2
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---


# 프로젝트 {#project-setup-details} 설정

## 프로젝트 설정 세부 정보 수정 {#modifying-project-setup-details}

Cloud Manager를 사용하여 성공적으로 구축 및 배포하려면 기존 AEM 프로젝트는 몇 가지 기본 규칙을 준수해야 합니다.

* 프로젝트는 Apache Maven을 사용하여 빌드해야 합니다.
* Git 저장소의 루트에 *pom.xml* 파일이 있어야 합니다. 이 *pom.xml* 파일은 하위 모듈 수를 여러 개 참조할 수 있습니다. 이 경우 다른 하위 모듈 등이 있을 수 있습니다. 필요한 경우.

* *pom.xml* 파일에서 추가 Maven 객체 저장소에 대한 참조를 추가할 수 있습니다. 구성 시 [암호로 보호된 객체 저장소](#password-protected-maven-repositories)에 대한 액세스가 지원됩니다. 그러나 네트워크 보호 객체 저장소에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 *target*&#x200B;이라는 디렉토리에 포함되어 있는 컨텐트 패키지 *zip* 파일을 검색하여 검색합니다. 모든 수의 하위 모듈에서는 콘텐츠 패키지를 생성할 수 있습니다.

* 배포 가능한 Dispatcher 가공물은 *conf* 및 *conf.d*&#x200B;라는 이름의 디렉토리가 있는 *zip* 파일(다시 이 디렉토리에 포함됨)을 검색하여 검색합니다.**

* 둘 이상의 컨텐츠 패키지가 있는 경우 패키지 배포 순서가 보장되지 않습니다. 특정 주문이 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다. 배포에서 패키지가 [생략되었을 수 있습니다.](#skipping-content-packages)


## 클라우드 관리자에서 마비성 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우, 개발자 워크스테이션에서 실행되는 경우와 달리 Cloud Manager 내에서 실행할 때 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)를 사용하여 Cloud Manager를 비롯한 다른 환경에서 빌드가 달라야 하는 방법을 정의할 수 있습니다.

Cloud Manager 빌드 환경 내에서 마스터 프로필의 활성화는 위에 설명된 CM_BUILD 환경 변수를 찾아 수행해야 합니다. 반대로, Cloud Manager 빌드 환경 외부에서만 사용하도록 만들어진 프로필은 이 변수가 없음을 확인하여 수행해야 합니다.

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
>개발자 워크스테이션에서 이 프로파일을 테스트하려면 명령줄(`-PcmBuild` 포함) 또는 IDE(Integrated Development Environment)에서 활성화할 수 있습니다.

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

## 암호로 보호된 전문가 저장소 지원 {#password-protected-maven-repositories}

>[!NOTE]
>암호로 보호된 Maven 저장소의 아티팩트는 이 메커니즘을 통해 배포된 코드가 현재 Cloud Manager의 Quality Gates를 통해 실행되지 않으므로 매우 조심스럽게 사용해야 합니다. 따라서 드문 경우나 AEM에 연결되지 않은 코드에만 사용해야 합니다. 또한 이진 파일과 함께 전체 프로젝트 소스 코드뿐 아니라 Java 소스도 배포하는 것이 좋습니다.

Cloud Manager에서 암호로 보호된 Maven 리포지토리를 사용하려면 암호(및 사용자 이름(선택 사항)를 비밀 [파이프라인 변수](#pipeline-variables)로 지정한 다음 git 저장소의 파일 내에 `.cloudmanager/maven/settings.xml`라는 이름의 암호를 참조합니다. 이 파일은 [마비설정 파일](https://maven.apache.org/settings.html) 스키마를 따릅니다. 클라우드 관리자 빌드 프로세스가 시작되면 이 파일의 `<servers>` 요소가 클라우드 관리자가 제공하는 기본 `settings.xml` 파일로 병합됩니다. `adobe` 및 `cloud-manager`로 시작하는 서버 ID는 예약으로 간주되며 사용자 지정 서버에서 사용해서는 안됩니다. 이러한 접두사 중 하나 또는 기본 ID `central`와 일치하지 않는 **서버 ID는 클라우드 관리자에 의해 미러링되지 않습니다.** 이 파일을 사용하면 서버 ID가 `pom.xml` 파일 내의 `<repository>` 및/또는 `<pluginRepository>` 요소 내부에서 참조됩니다. 일반적으로 이러한 `<repository>` 및/또는 `<pluginRepository>` 요소는 [Cloud Manager 특정 프로필](#activating-maven-profiles-in-cloud-manager)에 포함되지만 반드시 필요한 것은 아닙니다.

예를 들어 저장소가 https://repository.myco.com/maven2에 있고 클라우드 관리자가 사용해야 하는 사용자 이름은 `cloudmanager`이고 암호는 `secretword`입니다.

먼저 파이프라인에서 암호를 암호로 설정합니다.

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

그런 다음 `.cloudmanager/maven/settings.xml` 파일에서 이 항목을 참조합니다.

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

마지막으로 `pom.xml` 파일 내에서 서버 ID를 참조합니다.

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
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
    </profile>
</profiles>
```

### 소스 배포 {#deploying-sources}

바이너리와 함께 Java 소스를 Maven 저장소에 배포하는 것이 좋습니다.

프로젝트에서 maven-source-plugin을 구성합니다.

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### 프로젝트 소스 배포 {#deploying-project-sources}

이진 파일과 함께 전체 프로젝트 소스를 Maven 저장소에 배포하는 것이 좋습니다. 이를 통해 정확한 결함을 다시 작성할 수 있습니다.

프로젝트에서 maven-assembly-plugin을 구성합니다.

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## 콘텐츠 패키지 {#skipping-content-packages} 건너뛰기

Cloud Manager에서 빌드는 콘텐츠 패키지를 수에 관계없이 생성할 수 있습니다.
다양한 이유로, 컨텐츠 패키지를 배포하지 않고 판매하는 것이 좋을 수 있습니다. 예를 들어 테스트용으로만 사용되는 컨텐츠 패키지를 빌드하거나 빌드 프로세스의 다른 단계에서 다시 패키지되는 컨텐츠 패키지, 즉 다른 패키지의 하위 패키지로 사용할 경우 유용합니다.

이러한 시나리오를 수용하기 위해 Cloud Manager는 빌드된 콘텐츠 패키지의 속성에서 ***cloudManagerTarget***&#x200B;이라는 속성을 찾습니다. 이 속성을 none으로 설정하면 패키지를 건너뛰고 배포할 수 없습니다. 이 속성을 설정하는 메커니즘은 빌드가 콘텐츠 패키지를 생성하는 방법에 따라 달라집니다. 예를 들어 filevault-maven-plugin을 사용하면 다음과 같이 플러그인을 구성할 수 있습니다.

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
