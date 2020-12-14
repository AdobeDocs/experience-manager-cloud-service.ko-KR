---
title: Adobe Content Package Maven Plugin
description: Content Package Maven 플러그인을 사용하여 AEM 응용 프로그램을 배포합니다.
translation-type: tm+mt
source-git-commit: 2cdbbe9b8f6608cbdd299889be515d421e3d9ad3
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 7%

---


# Adobe Content Package Maven Plugin {#adobe-content-package-maven-plugin}

Adobe Content Package Maven 플러그인을 사용하여 패키지 배포 및 관리 작업을 Maven 프로젝트에 통합할 수 있습니다.

AEM에 구성된 패키지 배포는 Adobe Content Package Maven 플러그인에 의해 수행되며 AEM Package Manager를 사용하여 정상적으로 수행되는 작업을 자동화할 수 있습니다.

* 파일 시스템의 파일에서 새 패키지를 만듭니다.
* AEM에서 패키지를 설치하고 제거합니다.
* AEM에 이미 정의된 패키지를 빌드합니다.
* AEM에 설치된 패키지 목록을 가져옵니다.
* AEM에서 패키지를 제거합니다.

이 문서에서는 Maven을 사용하여 이러한 작업을 관리하는 방법에 대해 자세히 설명합니다. 그러나 AEM 프로젝트 및 해당 패키지의 구조를 구성하는 방법을 [이해하는 것도 중요합니다.](#aem-project-structure)

>[!NOTE]
>
>이제 패키지 생성이 [Apache Jackrabbit FileVault 패키지 Maven 플러그인](https://jackrabbit.apache.org/filevault-package-maven-plugin/)에 의해 소유됩니다. AEM에 구성된 패키지의 배포는 여기에 설명된 대로 Adobe Content Package Maven 플러그인에 의해 수행됩니다.

## 패키지 및 AEM 프로젝트 구조 {#aem-project-structure}

AEM 6.5는 온-프레미스 및 AMS 구현 모두에 대해 최신 AEM Project Lianype에서 구현되는 패키지 관리 및 프로젝트 구조에 대한 최신 모범 사례를 준수합니다.

>[!TIP]
>
>자세한 내용은 AEM의 [AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 아티클뿐만 아니라 [AEM 프로젝트 원형](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html) 설명서를 참조하십시오. 이 두 가지 모두 AEM 6.5에서 완벽하게 지원됩니다.

## Content Package Maven Plugin {#obtaining-the-content-package-maven-plugin} 입수하기

이 플러그인은 [Maven Central 저장소에서 사용할 수 있습니다.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## Content Package Maven 플러그인 목표 및 매개 변수

Content Package Maven 플러그인을 사용하려면 POM 파일의 빌드 요소 내에 다음 플러그인 요소를 추가하십시오.

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Maben이 플러그인을 다운로드할 수 있도록 하려면 이 페이지의 [Obging the Content Package Maven Plugin](#obtaining-the-content-package-maven-plugin) 섹션에 제공된 프로파일을 사용합니다.

## Content Package Maven Plugin {#goals-of-the-content-package-maven-plugin} 목표

Content Package 플러그인이 제공하는 목표 및 목표 매개 변수는 다음에 나오는 섹션에 설명되어 있습니다. 공통 매개변수 섹션에 설명된 매개 변수는 대부분의 목표에 사용할 수 있습니다. 한 목표에 적용되는 매개 변수는 해당 목표에 대한 섹션에 설명되어 있습니다.

### 플러그인 접두사 {#plugin-prefix}

플러그인 접두어는 `content-package`입니다. 다음 예제와 같이 명령줄에서 목표를 실행하려면 이 접두어를 사용합니다.

```shell
mvn content-package:build
```

### 매개 변수 접두사 {#parameter-prefix}

별도의 언급이 없는 한 플러그인 목표 및 매개 변수는 다음 예제와 같이 `vault` 접두어를 사용합니다.

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### 프록시 {#proxies}

AEM용 프록시를 사용하는 목표는 Maven 설정에 있는 첫 번째 유효한 프록시 구성을 사용합니다. 프록시 구성을 찾을 수 없으면 프록시가 사용되지 않습니다. [공통 매개 변수](#common-parameters) 섹션의 `useProxy` 매개 변수를 참조하십시오.

### 공통 매개 변수 {#common-parameters}

다음 표의 매개 변수는 **목표** 열에 언급된 경우를 제외하고 모든 목표에 공통입니다.

| 이름 | 유형 | 필수 | 기본 값 | 설명 | 목표 |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | 아니오 | `false` | 오류가 발생할 때 `true` 값이 있으면 빌드가 실패합니다. 값이 `false`이면 빌드가 오류를 무시합니다. | `package`을 제외한 모든 목표 |
| `name` | `String` | `build`:예,  `install`:아니요,  `rm`:예 | `build`:기본값 없음,  `install`:Maven 프로젝트의  `artifactId` 속성 값 | 수행할 패키지의 이름 | `ls`을 제외한 모든 목표 |
| `password` | `String` | 예 | `admin` | AEM의 인증에 사용되는 암호 | `package`을 제외한 모든 목표 |
| `serverId` | `String` | 아니오 | 인증을 위해 사용자 이름 및 암호를 검색할 서버 ID | `package`을 제외한 모든 목표 |
| `targetURL` | `String` | 예 | `http://localhost:4502/crx/packmgr/service.jsp` | AEM 패키지 관리자의 HTTP 서비스 API의 URL | `package`을 제외한 모든 목표 |
| `timeout` | `int` | 아니오 | `5` | 패키지 관리자 서비스와 통신하는 데 필요한 연결 시간(초) | `package`을 제외한 모든 목표 |
| `useProxy` | `boolean` | 아니오 | `true` | `true` 값을 지정하면 Maven이 패키지 관리자에 대한 프록시 요청을 위해 찾은 첫 번째 활성 프록시 구성을 사용합니다. | `package`을 제외한 모든 목표 |
| `userId` | `String` | 예 | `admin` | AEM으로 인증할 사용자 이름 | `package`을 제외한 모든 목표 |
| `verbose` | `boolean` | 아니오 | `false` | 자세한 로깅 활성화 또는 비활성화 | `package`을 제외한 모든 목표 |

### build {#build}

AEM 인스턴스에 이미 정의된 콘텐츠 패키지를 빌드합니다.

>[!NOTE]
>
>이 목표를 Maven 프로젝트 내에서 실행할 필요는 없습니다.

#### 매개 변수 {#parameters}

빌드 목표에 대한 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### {#install} 설치

저장소에 패키지를 설치합니다. 이 목표를 실행해도 Maven 프로젝트가 필요하지 않습니다. 목표는 Maven 빌드 라이프사이클의 `install` 단계에 바인딩됩니다.

#### 매개 변수 {#parameters-1}

다음 매개 변수 외에 [공통 매개 변수](#common-parameters) 섹션의 설명을 참조하십시오.

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|---|
| `artifact` | `String` | 아니오 | Maven 프로젝트의 `artifactId` 속성 값 | `groupId:artifactId:version[:packaging]` 형식의 문자열 |
| `artifactId` | `String` | 아니오 | 없음 | 설치할 아티팩트의 ID |
| `groupId` | `String` | 아니오 | 없음 | 설치할 아티팩트의 `groupId` |
| `install` | `boolean` | 아니오 | `true` | 패키지가 업로드될 때 자동으로 패키지의 압축을 해제할지 여부를 결정합니다. |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | 아니오 | `localRepository` 시스템 변수의 값 | 시스템 속성이 항상 사용되므로 플러그인 구성을 사용하여 구성할 수 없는 로컬 Maven 저장소 |
| `packageFile` | `java.io.File` | 아니오 | Maven 프로젝트에 대해 정의된 기본 아티팩트입니다. | 설치할 패키지 파일의 이름 |
| `packaging` | `String` | 아니오 | `zip` | 설치할 아티팩트의 패키징 유형 |
| `pomRemoteRepositories` | `java.util.List` | 예 | Maven 프로젝트에 대해 정의된 `remoteArtifactRepositories` 속성 값 | 이 값은 플러그인 구성을 사용하여 구성할 수 없으며 프로젝트에 지정해야 합니다. |
| `project` | `org.apache.maven.project.MavenProject` | 예 | 플러그인이 구성된 프로젝트 | 프로젝트에 플러그인 구성이 포함되어 있으므로 암시적으로 표시되는 Maben 프로젝트 |
| `repositoryId` (POM),  `repoID` (명령줄) | `String` | 아니오 | `temp` | 아티팩트가 검색되는 저장소의 ID |
| `repositoryUrl` (POM),  `repoURL` (명령줄) | `String` | 아니오 | 없음 | 아티팩트가 검색되는 저장소의 URL |
| version | 문자열 | 아니오 | 없음 | 설치할 아티팩트의 버전 |

### ls {#ls}

패키지 관리자에 배포된 패키지를 나열합니다.

#### 매개 변수 {#parameters-2}

ls 목표에 대한 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### rm {#rm}

패키지 관리자에서 패키지를 제거합니다.

#### 매개 변수 {#parameters-3}

rm 목표의 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### {#uninstall} 제거

패키지를 제거합니다. 패키지는 제거된 상태의 서버에 남아 있습니다.

#### 매개 변수 {#parameters-4}

제거 목표에 대한 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### package {#package}

콘텐츠 패키지를 만듭니다. 패키지 목표의 기본 구성에는 컴파일된 파일이 저장되는 디렉토리의 내용이 포함됩니다. 패키지 목표를 실행하려면 컴파일 빌드 단계가 완료되어야 합니다. 패키지 목표는 Maven 빌드 라이프사이클의 패키지 단계에 연결되어 있습니다.

#### 매개 변수 {#parameters-5}

다음 매개 변수 외에도 [공통 매개 변수](#common-parameters) 섹션의 `name` 매개 변수에 대한 설명을 참조하십시오.

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | 아니오 | 없음 | 사용할 아카이브 구성 |
| `builtContentDirectory` | `java.io.File` | 예 | Maven 빌드의 출력 디렉터리 값 | 패키지에 포함할 내용이 포함된 디렉토리 |
| `dependencies` | `java.util.List` | 아니오 | 없음 |  |
| `embeddedTarget` | `java.lang.String` | 아니오 | 없음 |  |
| `embeddeds` | `java.util.List` | 아니오 | 없음 |  |
| `failOnMissingEmbed` | `boolean` | 예 | `false` | `true` 값은 포함된 아티팩트가 프로젝트 종속성에서 찾을 수 없는 경우 빌드가 실패합니다. 값이 `false`이면 빌드가 이러한 오류를 무시합니다. |
| `filterSource` | `java.io.File` | 아니오 | 없음 | 이 매개 변수는 작업 공간 필터의 소스를 지정하는 파일을 정의합니다. 구성에 지정된 필터와 임베드 또는 하위 패키지를 통해 주입된 필터는 파일 컨텐츠와 병합됩니다. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | 아니오 | 없음 | 이 매개 변수에는 패키지 내용을 정의하는 필터 요소가 포함되어 있습니다. 이 파일을 실행하면 필터는 `filter.xml` 파일에 포함됩니다. 아래의 [필터 사용](#using-filters) 섹션을 참조하십시오. |
| `finalName` | `java.lang.String` | 예 | 마스터 프로젝트에 정의된 `finalName`(빌드 단계) | 생성된 패키지 ZIP 파일의 이름(파일 확장명이 `.zip` 없음) |
| `group` | `java.lang.String` | 예 | 마벤 프로젝트에 정의된 `groupID` | 콘텐츠 패키지에 대한 대상 설치 경로의 일부인 생성된 콘텐츠 패키지의 `groupId` |
| `outputDirectory` | `java.io.File` | 예 | Maven 프로젝트에 정의된 빌드 디렉터리 | 컨텐츠 패키지가 저장되는 로컬 디렉토리 |
| `prefix` | `java.lang.String` | 아니오 | 없음 |  |
| `project` | `org.apache.maven.project.MavenProject` | 예 | 없음 | 마벤 프로젝트 |
| `properties` | `java.util.Map` | 아니오 | 없음 | 이러한 매개 변수는 `properties.xml` 파일에서 설정할 수 있는 추가 속성을 정의합니다. 이러한 속성은 다음 사전 정의된 속성을 덮어쓸 수 없습니다.`group`(설정할 `group` 매개 변수 사용), `name`(설정할 `name` 매개 변수 사용), `version`(설정할 `version` 매개 변수 사용), `description`(프로젝트 설명에 따라 설정), `groupId`(`groupId`(마비되는 프로젝트 설명자의 &lt;a8/>), `artifactId`(`artifactId` 마스터 프로젝트 설명자), `dependencies`(설정할 `dependencies` 매개 변수 사용), `createdBy`(`user.name` 시스템 속성의 값), `created`(현재 시스템 시간), `requiresRoot`(설정할 `requiresRoot` 매개 변수 사용), `packagePath`(그룹 및 패키지 이름에서 자동으로 생성됨) |
| `requiresRoot` | `boolean` | 예 | false | 패키지에 루트가 필요한지 여부를 정의합니다. 이 속성은 `properties.xml` 파일의 `requiresRoot` 속성이 됩니다. |
| `subPackages` | `java.util.List` | 아니오 | 없음 |  |
| `version` | `java.lang.String` | 예 | Maven 프로젝트에 정의된 버전 | 콘텐츠 패키지의 버전 |
| `workDirectory` | `java.io.File` | 예 | Maven 프로젝트에 정의된 디렉터리(빌드 단계) | 패키지에 포함할 내용이 포함된 디렉토리 |

#### 필터 사용 {#using-filters}

필터 요소를 사용하여 패키지 컨텐츠를 정의합니다. 필터는 패키지의 `META-INF/vault/filter.xml` 파일에서 `workspaceFilter` 요소에 추가됩니다.

다음 필터 예제에서는 사용할 XML 구조를 보여 줍니다.

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode>
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

##### 가져오기 모드 {#import-mode}

`mode` 요소는 패키지를 가져올 때 저장소가 영향을 받는 방식을 정의합니다. 다음 값을 사용할 수 있습니다.

* **병합:** 저장소에 아직 없는 패키지의 콘텐트가 추가됩니다. 패키지와 저장소 모두에 있는 컨텐츠는 변경되지 않습니다. 저장소에서 제거된 콘텐츠가 없습니다.
* **바꾸기:** 저장소에 없는 패키지의 콘텐트가 저장소에 추가됩니다. 저장소의 컨텐츠는 패키지의 일치하는 컨텐츠로 대체됩니다. 패키지에 없는 콘텐츠는 저장소에서 제거됩니다.
* **업데이트:** 저장소에 없는 패키지의 콘텐트가 저장소에 추가됩니다. 저장소의 컨텐츠는 패키지의 일치하는 컨텐츠로 대체됩니다. 기존 컨텐츠가 저장소에서 제거됩니다.

필터에 `mode` 요소가 없으면 `replace`의 기본값이 사용됩니다.

### 도움말 {#help}

#### 매개 변수 {#parameters-6}

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `detail` | `boolean` | 아니오 | `false` | 각 목표에 대한 모든 설정 가능 속성을 표시할지 여부를 결정합니다. |
| `goal` | `String` | 아니오 | 없음 | 이 매개 변수는 도움말을 표시할 목표 이름을 정의합니다. 값을 지정하지 않으면 모든 목표에 대한 도움말이 표시됩니다. |
| `indentSize` | `int` | 아니오 | `2` | 각 수준의 들여쓰기에 사용할 공백 수(정의된 경우 양수여야 함) |
| `lineLength` | `int` | 아니오 | `80` | 표시 라인의 최대 길이(정의된 경우 양수여야 함) |

## 패키지 {#including-a-thumbnail-image-or-properties-file-in-the-package}에 축소판 이미지 또는 속성 파일 포함

기본 패키지 구성 파일을 교체하여 패키지 속성을 사용자 정의합니다. 예를 들어 축소판 이미지를 포함시켜 패키지 관리자와 패키지 공유에서 패키지를 구별할 수 있습니다.

소스 파일은 파일 시스템의 모든 위치에 위치할 수 있습니다. POM 파일에서 소스 파일을 `target/vault-work/META-INF`에 복사하여 패키지에 포함할 빌드 리소스를 정의합니다.

다음 POM 코드는 프로젝트 소스의 `META-INF` 폴더에 있는 파일을 패키지에 추가합니다.

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

다음 POM 코드는 축소판 이미지만 패키지에 추가합니다. 축소판 이미지의 이름은 `thumbnail.png`이어야 하며 패키지의 `META-INF/vault/definition` 폴더에 있어야 합니다. 이 예에서 소스 파일은 프로젝트의 `/src/main/content/META-INF/vault/definition` 폴더에 있습니다.

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## AEM 프로젝트 원형을 사용하여 AEM 프로젝트 생성 {#using-archetypes}

최신 AEM Project Tranype은 온-프레미스와 AMS 구현 모두에 대한 우수 사례 패키지 구조를 구현하며 모든 AEM 프로젝트에 권장됩니다.

>[!TIP]
>
>자세한 내용은 AEM의 [AEM 프로젝트 구조](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 아티클뿐만 아니라 [AEM 프로젝트 원형](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) 설명서를 참조하십시오. 이 두 가지 모두 AEM 6.5에서 완벽하게 지원됩니다.
