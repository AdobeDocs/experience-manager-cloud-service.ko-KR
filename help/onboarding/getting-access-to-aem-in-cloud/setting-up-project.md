---
title: 프로젝트 설정 세부 정보
description: 프로젝트 설정 세부 사항 - Cloud Services
exl-id: 76af0171-8ed5-4fc7-b5d5-7da5a1a06fa8
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# 프로젝트 {#project-setup-details} 설정

## 프로젝트 설정 세부 정보 수정 {#modifying-project-setup-details}

Cloud Manager를 사용하여 성공적으로 빌드하고 배포하려면 기존 AEM 프로젝트를 다음 몇 가지 기본 규칙을 준수해야 합니다.

* Apache Maven을 사용하여 프로젝트를 빌드해야 합니다.
* Git 리포지토리의 루트에 *pom.xml* 파일이 있어야 합니다. 이 *pom.xml* 파일은 여러 개의 하위 모듈을 참조할 수 있습니다. 이 경우 다른 하위 모듈 등이 있을 수 있습니다. 필요한 경우.

* *pom.xml* 파일의 추가 Maven 아티팩트 저장소에 대한 참조를 추가할 수 있습니다. 구성 시 [암호로 보호된 아티팩트 저장소](#password-protected-maven-repositories)에 대한 액세스가 지원됩니다. 그러나 네트워크 보호 아티팩트 리포지토리에 대한 액세스는 지원되지 않습니다.
* 배포 가능한 컨텐츠 패키지는 *target*&#x200B;이라는 디렉터리에 포함된 컨텐츠 패키지 *zip* 파일을 검색하여 찾습니다. 임의의 하위 모듈 개수로 컨텐츠 패키지를 생성할 수 있습니다.

* 배포 가능한 Dispatcher 가공물은 *zip* 파일(다시, *conf* 및 *conf.d*&#x200B;이라는 디렉터리가 있는 *target* 디렉터리에 포함됨)을 검색하여 검색합니다.

* 두 개 이상의 컨텐츠 패키지가 있는 경우 패키지 배포를 순서 지정할 수 없습니다. 특정 순서가 필요한 경우 컨텐츠 패키지 종속성을 사용하여 순서를 정의할 수 있습니다. 패키지는 배포에서 [건너뛸 수 있습니다.](#skipping-content-packages)


## Cloud Manager에서 Maven 프로필 활성화 {#activating-maven-profiles-in-cloud-manager}

일부 제한된 경우에는 개발자 워크스테이션에서 실행되는 경우와 달리 Cloud Manager 내에서 실행할 때 빌드 프로세스를 약간 변경해야 할 수 있습니다. 이러한 경우 [Maven 프로필](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)을 사용하여 Cloud Manager를 비롯한 다른 환경에서 빌드가 어떻게 다른지 정의할 수 있습니다.

Cloud Manager 빌드 환경 내의 Maven 프로필 활성화는 위에 설명된 CM_BUILD 환경 변수를 찾아 수행해야 합니다. 반대로 Cloud Manager 빌드 환경 외부에서만 사용하도록 만들어진 프로필은 이 변수가 없는 경우를 찾아 작성해야 합니다.

예를 들어 빌드가 Cloud Manager 내에서 실행될 때만 단순 메시지를 출력하려는 경우 다음을 수행합니다.

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
>개발자 워크스테이션에서 이 프로필을 테스트하려면 명령줄(`-PcmBuild` 사용) 또는 IDE(Integrated Development Environment)에서 프로필을 활성화할 수 있습니다.

빌드가 Cloud Manager 외부에서 실행될 때만 간단한 메시지를 출력하려면 다음을 수행합니다.

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

## 암호로 보호된 Maven 저장소 지원 {#password-protected-maven-repositories}

>[!NOTE]
>암호로 보호된 Maven 저장소의 가공물은 이 메커니즘을 통해 배포된 코드가 현재 Cloud Manager의 품질 게이트를 통해 실행되지 않으므로 매우 신중하게 사용해야 합니다. 따라서 드문 경우와 AEM에 연결되지 않은 코드에만 사용해야 합니다. Java 소스뿐만 아니라 전체 프로젝트 소스 코드도 바이너리와 함께 배포하는 것이 좋습니다.

Cloud Manager에서 암호로 보호된 Maven 리포지토리를 사용하려면 암호(및 선택적으로 사용자 이름)를 암호 [파이프라인 변수](#pipeline-variables) 암호로 지정한 다음, git 리포지토리의 `.cloudmanager/maven/settings.xml` 파일 내에서 해당 암호를 참조합니다. 이 파일은 [Maven 설정 파일](https://maven.apache.org/settings.html) 스키마를 따릅니다. Cloud Manager 빌드 프로세스가 시작되면 이 파일의 `<servers>` 요소가 Cloud Manager에서 제공하는 기본 `settings.xml` 파일에 병합됩니다. `adobe` 및 `cloud-manager` 로 시작하는 서버 ID는 예약된 것으로 간주되므로 사용자 지정 서버에서 사용해서는 안 됩니다. 서버 ID **이 이러한 접두사 중 하나와 일치하지 않거나 기본 ID `central`가 Cloud Manager에 의해 미러링되지 않습니다.** 이 파일이 배치되면 서버 ID는 `pom.xml` 파일 내의 `<repository>` 및/또는 `<pluginRepository>` 요소 내에서 참조됩니다. 일반적으로 이러한 `<repository>` 및/또는 `<pluginRepository>` 요소는 [Cloud Manager 관련 프로필](#activating-maven-profiles-in-cloud-manager) 내에 포함되지만, 반드시 필요한 것은 아닙니다.

예를 들어 저장소가 https://repository.myco.com/maven2에 있고 Cloud Manager에서 사용해야 하는 사용자 이름은 `cloudmanager`이고 암호는 `secretword`입니다.

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

마지막으로 `pom.xml` 파일 내의 서버 ID를 참조합니다.

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

### 소스 배포 중 {#deploying-sources}

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

### 프로젝트 소스 배포 중 {#deploying-project-sources}

이진 파일과 함께 전체 프로젝트 소스를 Maven 저장소에 배포하는 것이 좋습니다. 이렇게 하면 정확한 아티팩트를 다시 빌드할 수 있습니다.

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

## 컨텐츠 패키지 건너뛰기 {#skipping-content-packages}

Cloud Manager에서 빌드는 다양한 컨텐츠 패키지를 생성할 수 있습니다.
다양한 이유로 컨텐츠 패키지를 개발하지만 배포하지는 않는 것이 좋을 수 있습니다. 예를 들어 테스트에만 사용하거나 빌드 프로세스의 다른 단계에서 다시 패키징하는 컨텐츠 패키지를 만들 때, 즉 다른 패키지의 하위 패키지로 사용할 수 있습니다.

이러한 시나리오를 수용하기 위해 Cloud Manager는 빌드된 컨텐츠 패키지의 속성에서 ***cloudManagerTarget***&#x200B;이라는 속성을 찾습니다. 이 속성을 none으로 설정하면 패키지를 건너뛰고 배포하지 않습니다. 이 속성을 설정하는 메커니즘은 빌드가 컨텐츠 패키지를 만드는 방식에 따라 다릅니다. 예를 들어 filervault-maven-plugin을 사용하여 다음과 같이 플러그인을 구성합니다.

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

content-package-maven-plugin을 사용하면 비슷합니다.

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
