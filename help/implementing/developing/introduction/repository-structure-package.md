---
title: 'AEM 프로젝트 저장소 구조 패키지  '
description: Adobe Experience Manager as a Cloud Service Maven 프로젝트에서는 프로젝트의 코드 하위 패키지가 배포되는 JCR 저장소 루트를 정의하는 유일한 목적이 되는 저장소 구조 하위 패키지 정의가 필요합니다.
exl-id: dec08410-d109-493d-bf9d-90e5556d18f0
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 2%

---

# AEM 프로젝트 저장소 구조 패키지

Adobe Experience Manager as a Cloud Service용 Maven 프로젝트에서는 프로젝트의 코드 하위 패키지가 배포되는 JCR 저장소 루트를 정의하는 유일한 목적이 되는 저장소 구조 하위 패키지 정의가 필요합니다. 이렇게 하면 Cloud Service으로 Experience Manager에 패키지를 설치하는 것이 JCR 리소스 종속성으로 자동 순서가 지정됩니다. 종속성이 누락되면 하위 구조가 상위 구조보다 먼저 설치되어 예기치 않게 제거되어 배포가 중단되는 시나리오가 발생할 수 있습니다.

코드 패키지가 코드 패키지에서 다루지 않은 **위치**&#x200B;에 배포되는 경우, 상위 리소스(JCR 루트에 가까운 JCR 리소스)는 저장소 구조 패키지에 열거되어 이러한 종속성을 설정해야 합니다.

![저장소 구조 패키지](./assets/repository-structure-packages.png)

저장소 구조 패키지는 패키지 유효성 검사기가 표준 루트이므로 &quot;잠재적인 충돌에서 안전한&quot; 영역을 결정하기 위해 사용하는 예상 및 일반적인 `/apps` 상태를 정의합니다.

저장소 구조 패키지에 포함할 가장 일반적인 경로는 다음과 같습니다.

+ `/apps` 시스템 제공 노드인 노드
+ `/apps/cq/...`,  `/apps/dam/...`,  `/apps/wcm/...` 및  `/apps/sling/...` 에 대한 일반적인 오버레이를 제공합니다 `/libs`.
+ `/apps/settings` 공유 컨텍스트 인식 구성 루트 경로

이 하위 패키지 **에는**&#x200B;의 컨텐츠가 없으며 필터 루트를 정의하는 `pom.xml`로만 구성됩니다.

## 저장소 구조 패키지 생성

Maven 프로젝트에 대한 저장소 구조 패키지를 만들려면 다음 `pom.xml`을 사용하여 빈 Maven 하위 프로젝트를 만들고, 상위 Maven 프로젝트에 맞게 프로젝트 메타데이터를 업데이트합니다.

코드 패키지가 배포하는 모든 JCR 저장소 경로 루트를 포함하려면 `<filters>` 을(를) 업데이트합니다.

이 새 Maven 하위 프로젝트를 상위 프로젝트 `<modules>` 목록에 추가해야 합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- ====================================================================== -->
    <!-- P A R E N T  P R O J E C T  D E S C R I P T I O N                      -->
    <!-- ====================================================================== -->
    <parent>
        <groupId>com.my-company</groupId>
        <artifactId>my-app</artifactId>
        <version>x.x.x</version>
        <relativePath>../pom.xml</relativePath>
    </parent>

    <!-- ====================================================================== -->
    <!-- P R O J E C T  D E S C R I P T I O N                                   -->
    <!-- ====================================================================== -->
    <artifactId>ui.apps.structure</artifactId>
    <packaging>content-package</packaging>
    <name>UI Apps Structure - Repository Structure Package for /apps</name>

    <description>
        Empty package that defines the structure of the Adobe Experience Manager repository the code packages in this project deploy into.
        Any roots in the code packages of this project should have their parent enumerated in the filters list below.
    </description>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.jackrabbit</groupId>
                <artifactId>filevault-package-maven-plugin</artifactId>
                <extensions>true</extensions>
                <properties>
                    <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
                <configuration>
                    <properties>
                        <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                        <cloudManagerTarget>none</cloudManagerTarget>
                    </properties>
                    <filters>

                        <!-- /apps root -->
                        <filter><root>/apps</root></filter>

                        <!--
                        Examples of complex roots


                        Overlays of /libs typically require defining the overlayed structure, at each level here.

                        For example, adding a new section to the main AEM Tools navigation, necessitates the following rules:

                        <filter><root>/apps/cq</root></filter>
                        <filter><root>/apps/cq/core</root></filter>
                        <filter><root>/apps/cq/core/content</root></filter>
                        <filter><root>/apps/cq/core/content/nav/</root></filter>
                        <filter><root>/apps/cq/core/content/nav/tools</root></filter>


                        Any /apps level Context-aware configurations need to enumerated here. 
                        
                        For example, providing email templates under `/apps/settings/notification-templates/com.day.cq.replication` necessitates the following rules:

                        <filter><root>/apps/settings</root></filter>
                        <filter><root>/apps/settings/notification-templates</root></filter>
                        <filter><root>/apps/settings/notification-templates/com.day.cq.replication</root></filter>
                        -->

                    </filters>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

## 저장소 구조 패키지 참조

저장소 구조 패키지를 사용하려면 FileVault 컨텐츠 패키지 Maven 플러그인 `<repositoryStructurePackage>` 구성을 통해 모든 코드 패키지( `/apps`에 배포하는 하위 패키지)를 통해 참조합니다.

`ui.apps/pom.xml` 및 다른 코드 패키지 `pom.xml`에서 프로젝트의 저장소 구조 패키지(#repository-structure-package) 구성에 대한 참조를 FileVault 패키지 Maven 플러그인에 추가합니다.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <repositoryStructurePackages>
          <repositoryStructurePackage>
              <groupId>${project.groupId}</groupId>
              <artifactId>ui.apps.structure</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
</build>
<dependencies>
    <!-- Add the dependency for the repository structure package so it resolves -->
    <dependency>
        <groupId>${project.groupId}</groupId>
        <artifactId>ui.apps.structure</artifactId>
        <version>${project.version}</version>
        <type>zip</type>
    </dependency>
    ...
</dependencies>
```

## 다중 코드 패키지 사용 사례

덜 일반적이고 더 복잡한 사용 사례에서는 JCR 저장소의 동일한 영역에 설치하는 여러 코드 패키지의 배포를 지원합니다.

예:

+ 코드 패키지 A가 `/apps/a`에 배포됩니다.
+ 코드 패키지 B가 `/apps/a/b`에 배포됩니다.

패키지 수준 종속성이 코드 패키지 A의 코드 패키지 B에서 설정되지 않은 경우 코드 패키지 B는 먼저 `/apps/a`에 배포되고, 코드 패키지 B가 `/apps/a`에 배포되어 이전에 설치된 `/apps/a/b`가 제거될 수 있습니다.

이 경우:

+ 코드 패키지 A는 프로젝트의 저장소 구조 패키지에서 `<repositoryStructurePackage>`을(를) 정의해야 합니다(`/apps`에 대한 필터가 있어야 함).
+ 코드 패키지 B는 코드 패키지 A가 공유하는 공간에 배포되므로 코드 패키지 B는 코드 패키지 A에서 `<repositoryStructurePackage>`을(를) 정의해야 합니다.

## 오류 및 디버깅

저장소 구조 패키지가 올바르게 설정되지 않은 경우 Maven 빌드 시 오류가 보고됩니다.

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

이는 브레이크 코드 패키지에 해당 필터 목록에 `/apps/some/path`을 나열하는 `<repositoryStructurePackage>`이 없음을 나타냅니다.

## 추가 리소스

+ [FileVault 콘텐츠 패키지 Maven 플러그인](http://jackrabbit.apache.org/filevault-package-maven-plugin/)
