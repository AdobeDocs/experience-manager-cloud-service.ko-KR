---
title: 'AEM 프로젝트 저장소 구조 패키지  '
description: Cloud Service Maven 프로젝트로 Adobe Experience Manager을 사용하려면 프로젝트의 코드 하위 패키지가 배포되는 JCR 리포지토리 루트를 정의하는 유일한 목적을 가진 저장소 구조 하위 패키지 정의가 필요합니다.
translation-type: tm+mt
source-git-commit: a6820eab30f2b318d62d2504cb17c12081a320a3
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 2%

---


# AEM 프로젝트 저장소 구조 패키지

Cloud Service으로 Adobe Experience Manager에 대한 전문적인 프로젝트를 제공하려면 프로젝트의 코드 하위 패키지가 배포되는 JCR 리포지토리 루트를 정의하는 유일한 목적을 가진 저장소 구조 하위 패키지 정의가 필요합니다. 이렇게 하면 Cloud Service이 JCR 리소스 종속성으로 자동 순서가 지정되므로 Experience Manager에 패키지를 설치할 수 있습니다. 종속성이 누락되면 상위 구조 앞에 하위 구조가 설치되고 따라서 예기치 않게 제거되어 배포가 중단되는 시나리오가 발생할 수 있습니다.

코드 패키지가 코드 패키지에 의해 **포함되지 않은 위치**&#x200B;에 배포되는 경우, 이러한 종속성을 설정하려면 모든 상위 리소스(JCR 루트에 가까운 JCR 리소스)를 저장소 구조 패키지에 열거해야 합니다.

![저장소 구조 패키지](./assets/repository-structure-packages.png)

저장소 구조 패키지는 패키지 유효성 검사기가 표준 루트로서 &quot;잠재적인 충돌에서 안전&quot; 영역을 결정하기 위해 사용하는 예상 일반 상태 `/apps`을 정의합니다.

저장소 구조 패키지에 포함할 가장 일반적인 경로는 다음과 같습니다.

+ `/apps` 시스템 제공 노드인
+ `/apps/cq/...`,  `/apps/dam/...`,  `/apps/wcm/...`및  `/apps/sling/...` 공통 오버레이를  `/libs`제공합니다.
+ `/apps/settings` 공유 컨텍스트 인식 구성 루트 경로란

이 하위 패키지 **에는**&#x200B;의 컨텐츠가 없으며 필터 루트를 정의하는 `pom.xml`로만 구성됩니다.

## 저장소 구조 패키지 생성

Maven 프로젝트에 대한 저장소 구조 패키지를 만들려면 다음 `pom.xml`을 사용하여 비어 있는 Maven 하위 프로젝트를 새로 만들고 상위 Maven 프로젝트에 맞게 프로젝트 메타데이터를 업데이트합니다.

코드 패키지가 배포하는 모든 JCR 리포지토리 경로 루트를 포함하려면 `<filters>`을 업데이트합니다.

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

저장소 구조 패키지를 사용하려면 모든 코드 패키지(`/apps`)에 배포하는 하위 패키지)를 통해 참조하고 FileVault 컨텐츠 패키지 Maven 플러그인 `<repositoryStructurePackage>` 구성을 통해 Maven 프로젝트를 참조합니다.

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

덜 일반적이고 보다 복잡한 사용 사례는 JCR 저장소의 동일한 영역에 설치하는 여러 코드 패키지의 배포를 지원합니다.

예:

+ 코드 패키지 A가 `/apps/a`에 배포됩니다.
+ 코드 패키지 B가 `/apps/a/b`에 배포됩니다.

패키지 수준 종속성이 코드 패키지 A의 코드 패키지 B에서 설정되지 않은 경우 코드 패키지 B가 먼저 `/apps/a`에 배포되고, 그 다음에 코드 패키지 B가 `/apps/a`에 배포되어 이전에 설치된 `/apps/a/b`가 제거됩니다.

이 경우:

+ 코드 패키지 A는 프로젝트의 저장소 구조 패키지에 `<repositoryStructurePackage>`을(를) 정의해야 합니다(`/apps`에 대한 필터가 있어야 함).
+ 코드 패키지 B가 코드 패키지 A에 의해 공유된 공간에 배포되기 때문에 코드 패키지 B는 코드 패키지 A에 `<repositoryStructurePackage>`을 정의해야 합니다.

## 오류 및 디버깅

저장소 구조 패키지가 올바르게 설정되지 않은 경우 Maven 빌드 시 오류가 보고됩니다.

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

이는 브레이킹 코드 패키지에 해당 필터 목록에 `/apps/some/path`이(가) 나열되는 `<repositoryStructurePackage>`이(가) 없음을 나타냅니다.

## 추가 리소스

+ [FileVault 컨텐츠 패키지 Maven 플러그인](http://jackrabbit.apache.org/filevault-package-maven-plugin/)
