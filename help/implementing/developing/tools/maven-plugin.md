---
title: Adobe 컨텐츠 패키지 Maven 플러그인
description: Content Package Maven 플러그인을 사용하여 AEM 응용 프로그램을 배포합니다.
exl-id: d631d6df-7507-4752-862b-9094af9759a0
source-git-commit: ba4e2427873fc9f5d91ee4f520df01018000a4c7
workflow-type: tm+mt
source-wordcount: '1851'
ht-degree: 6%

---

# Adobe 컨텐츠 패키지 Maven 플러그인 {#adobe-content-package-maven-plugin}

Content Package Maven 플러그인을 사용하여 패키지 배포 및 관리 작업을 Maven 프로젝트에 통합합니다.

AEM에 구축된 패키지의 배포는 Adobe Content Package Maven 플러그인에 의해 수행되며, AEM을 사용하여 정상적으로 수행되는 작업의 자동화를 활성화합니다 [패키지 관리자:](/help/implementing/developing/tools/package-manager.md)

* 파일 시스템의 파일에서 새 패키지를 만듭니다.
* AEM에서 패키지를 설치 및 제거합니다.
* AEM에 이미 정의된 패키지를 만듭니다.
* AEM에 설치된 패키지 목록을 확인합니다.
* AEM에서 패키지를 제거합니다.

이 문서에서는 Maven을 사용하여 이러한 작업을 관리하는 방법에 대해 자세히 설명합니다. 하지만 또한 이해하는 것이 중요합니다 [AEM 프로젝트 및 해당 패키지의 구성 방법.](#aem-project-structure)

>[!NOTE]
>
>패키지 **생성** 는 이제 가 소유합니다 [Apache Jackrabbit FileVault Package Maven 플러그인입니다.](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
>* 다음 `content-package-maven-plugin` 더 이상 릴리스 1.0.2에서 패키지를 지원하지 않습니다.
>* 이 문서에서는 **배포** AEM에 구축된 패키지 중 하나는 Adobe Content Package Maven 플러그인에 의해 수행됩니다.


## 패키지 및 AEM 프로젝트 구조 {#aem-project-structure}

AEM은 최신 AEM Project Archetype에 의해 구현된 대로 패키지 관리 및 프로젝트 구조에 대한 최신 모범 사례를 준수합니다.

>[!TIP]
>
>자세한 내용은 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) AEM as a Cloud Service 설명서 및 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 설명서. 둘 다 AEM 6.5에서 완전히 지원됩니다.

## Content Package Maven 플러그인 가져오기 {#obtaining-the-content-package-maven-plugin}

플러그인은 [Maven 중앙 저장소.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## 컨텐츠 패키지 Maven 플러그인 목표 및 매개 변수

Content Package Maven 플러그인을 사용하려면 POM 파일의 빌드 요소 내에 다음 플러그인 요소를 추가합니다.

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>1.0.4</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Maven이 플러그인을 다운로드하도록 하려면, [Content Package Maven 플러그인 가져오기](#obtaining-the-content-package-maven-plugin) 섹션을 참조하십시오.

## Content Package Maven 플러그인의 목표 {#goals-of-the-content-package-maven-plugin}

컨텐츠 패키지 플러그인이 제공하는 목표 및 목표 매개 변수는 다음에 나오는 섹션에 설명되어 있습니다. 일반 매개 변수 섹션에 설명된 매개 변수는 대부분의 목표에 사용할 수 있습니다. 하나의 목표에 적용되는 매개 변수는 해당 목표에 대한 섹션에 설명되어 있습니다.

### 플러그인 접두사 {#plugin-prefix}

플러그인 접두사는 다음과 같습니다. `content-package`. 다음 예제와 같이 명령줄에서 목표를 실행하려면 이 접두사를 사용합니다.

```shell
mvn content-package:build
```

### 매개 변수 접두사 {#parameter-prefix}

별도로 언급되지 않는 한 플러그인 목표 및 매개 변수는 `vault` 접두사를 추가합니다.

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### 프록시 {#proxies}

AEM용 프록시를 사용하는 목표는 Maven 설정에 있는 첫 번째 유효한 프록시 구성을 사용합니다. 프록시 구성이 없으면 프록시가 사용되지 않습니다. 자세한 내용은 `useProxy` 의 매개 변수 [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

### 공통 매개 변수 {#common-parameters}

다음 표의 매개 변수는 **목표** 열.

| 이름 | 유형 | 필수 | 기본 값 | 설명 | 목표 |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | 아니요 | `false` | 값 `true` 오류가 발생하면 빌드가 실패합니다. 값 `false` 빌드가 오류를 무시합니다. | 목표를 제외한 모든 목표 `package` |
| `name` | `String` | `build`: 예, `install`: 아니요 `rm`: 예 | `build`: 기본값 없음, `install`: 의 값 `artifactId` Maven 프로젝트의 속성 | 작업할 패키지의 이름입니다. | 목표를 제외한 모든 목표 `ls` |
| `password` | `String` | 예 | `admin` | AEM을 사용한 인증에 사용되는 암호 | 목표를 제외한 모든 목표 `package` |
| `serverId` | `String` | 아니요 | 인증을 위해 사용자 이름 및 암호를 검색할 서버 ID입니다 | 목표를 제외한 모든 목표 `package` |
| `targetURL` | `String` | 예 | `http://localhost:4502/crx/packmgr/service.jsp` | AEM 패키지 관리자의 HTTP 서비스 API의 URL입니다 | 목표를 제외한 모든 목표 `package` |
| `timeout` | `int` | 아니요 | `5` | 패키지 관리자 서비스와 통신하는 데 필요한 연결 제한 시간(초)입니다 | 목표를 제외한 모든 목표 `package` |
| `useProxy` | `boolean` | 아니요 | `true` | 값 `true` 패키지 관리자에 요청을 프록시하기 위해 Maven이 찾은 첫 번째 활성 프록시 구성을 사용하도록 합니다. | 목표를 제외한 모든 목표 `package` |
| `userId` | `String` | 예 | `admin` | AEM에 인증할 사용자 이름 | 목표를 제외한 모든 목표 `package` |
| `verbose` | `boolean` | 아니요 | `false` | 자세한 로깅 활성화 또는 비활성화 | 목표를 제외한 모든 목표 `package` |

### 빌드 {#build}

AEM 인스턴스에 이미 정의된 컨텐츠 패키지를 만듭니다.

>[!NOTE]
>
>이 목표를 Maven 프로젝트 내에서 실행할 필요가 없습니다.

#### 매개변수 {#parameters}

빌드 목표에 대한 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

### 설치 {#install}

저장소에 패키지를 설치합니다. 이 목표를 실행할 때에는 Maven 프로젝트가 필요하지 않습니다. 그 목표는 . `install` Maven 빌드 라이프사이클의 단계입니다.

#### 매개변수 {#parameters-1}

다음 매개 변수 외에 의 설명을 참조하십시오. [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `artifact` | `String` | 아니요 | 의 값 `artifactId` Maven 프로젝트의 속성 | 양식의 문자열입니다 `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | 아니요 | 없음 | 설치할 아티팩트의 ID입니다 |
| `groupId` | `String` | 아니요 | 없음 | 다음 `groupId` 설치할 아티팩트 |
| `install` | `boolean` | 아니요 | `true` | 패키지를 업로드할 때 자동으로 압축 해제할지 여부를 결정합니다 |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | 아니요 | 의 값 `localRepository` 시스템 변수 | 시스템 속성이 항상 사용되므로 플러그인 구성을 사용하여 구성할 수 없는 로컬 Maven 저장소 |
| `packageFile` | `java.io.File` | 아니요 | Maven 프로젝트에 대해 정의된 기본 객체 | 설치할 패키지 파일의 이름입니다 |
| `packaging` | `String` | 아니요 | `zip` | 설치할 아티팩트의 패키징 유형입니다 |
| `pomRemoteRepositories` | `java.util.List` | 예 | 의 값 `remoteArtifactRepositories` Maven 프로젝트에 대해 정의된 속성 | 이 값은 플러그인 구성을 사용하여 구성할 수 없으며 프로젝트에 지정해야 합니다. |
| `project` | `org.apache.maven.project.MavenProject` | 예 | 플러그인이 구성된 프로젝트 | 프로젝트에 플러그인 구성이 포함되어 있으므로 암시적 Maven 프로젝트 |
| `repositoryId` (POM), `repoID` (명령줄) | `String` | 아니요 | `temp` | 아티팩트가 검색되는 저장소의 ID입니다 |
| `repositoryUrl` (POM), `repoURL` (명령줄) | `String` | 아니요 | 없음 | 아티팩트가 검색되는 저장소의 URL입니다 |
| 버전 | 문자열 | 아니요 | 없음 | 설치할 아티팩트 버전 |

### ls {#ls}

에 배포되는 패키지를 나열합니다 [패키지 관리자.](/help/implementing/developing/tools/package-manager.md)

#### 매개변수 {#parameters-2}

ls 목표의 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

### rm {#rm}

에서 패키지 제거 [패키지 관리자.](/help/implementing/developing/tools/package-manager.md)

#### 매개변수 {#parameters-3}

rm 목표의 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

### 제거 {#uninstall}

패키지를 제거합니다. 패키지는 제거된 상태로 서버에 남아 있습니다.

#### 매개변수 {#parameters-4}

제거 목표의 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

### 패키지 {#package}

컨텐츠 패키지를 만듭니다. 패키지 목표의 기본 구성에는 컴파일된 파일이 저장된 디렉토리의 내용이 포함됩니다. 패키지 목표를 실행하려면 컴파일 빌드 단계가 완료되어야 합니다. 패키지 목표는 Maven 빌드 라이프사이클의 패키지 단계에 바인딩됩니다.

#### 매개변수 {#parameters-5}

다음 매개 변수 외에 `name` 의 매개 변수 [공통 매개 변수](#common-parameters) 섹션을 참조하십시오.

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | 아니요 | 없음 | 사용할 아카이브 구성 |
| `builtContentDirectory` | `java.io.File` | 예 | Maven 빌드의 출력 디렉터리 값 | 패키지에 포함할 컨텐츠가 들어 있는 디렉토리 |
| `dependencies` | `java.util.List` | 아니요 | 없음 |  |
| `embeddedTarget` | `java.lang.String` | 아니요 | 없음 |  |
| `embeddeds` | `java.util.List` | 아니요 | 없음 |  |
| `failOnMissingEmbed` | `boolean` | 예 | `false` | 값 `true` 포함된 아티팩트가 프로젝트 종속성에 없으면 빌드가 실패합니다. 값 `false` 빌드가 이러한 오류를 무시합니다. |
| `filterSource` | `java.io.File` | 아니요 | 없음 | 이 매개 변수는 작업 공간 필터의 소스를 지정하는 파일을 정의합니다. 구성에 지정되고 포함 또는 하위 패키지를 통해 삽입된 필터는 파일 컨텐츠와 병합됩니다. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | 아니요 | 없음 | 이 매개 변수에는 패키지 컨텐츠를 정의하는 필터 요소가 포함됩니다. 가 실행되면 필터가 `filter.xml` 파일. 자세한 내용은 [필터 사용](#using-filters) 섹션을 참조하십시오. |
| `finalName` | `java.lang.String` | 예 | 다음 `finalName` maven 프로젝트에 정의됨(빌드 단계) | 생성된 패키지 ZIP 파일의 이름으로, `.zip` 파일 확장명 |
| `group` | `java.lang.String` | 예 | 다음 `groupID` maven 프로젝트에 정의됨 | 다음 `groupId` 컨텐츠 패키지에 대한 대상 설치 경로의 일부인 생성된 컨텐츠 패키지 |
| `outputDirectory` | `java.io.File` | 예 | Maven 프로젝트에 정의된 빌드 디렉터리 | 컨텐츠 패키지가 저장되는 로컬 디렉토리 |
| `prefix` | `java.lang.String` | 아니요 | 없음 |  |
| `project` | `org.apache.maven.project.MavenProject` | 예 | 없음 | Maven 프로젝트 |
| `properties` | `java.util.Map` | 아니요 | 없음 | 이러한 매개 변수는에서 설정할 수 있는 추가 속성을 정의합니다 `properties.xml` 파일. 이러한 속성은 다음 사전 정의된 속성을 덮어쓸 수 없습니다. `group` (사용) `group` 설정할 매개 변수), `name` (사용) `name` 설정할 매개 변수), `version` (사용) `version` 설정할 매개 변수), `description` (프로젝트 설명에서 설정), `groupId` (`groupId` Maven 프로젝트 설명자), `artifactId` (`artifactId` Maven 프로젝트 설명자), `dependencies` (사용) `dependencies` 설정할 매개 변수), `createdBy` (값 `user.name` 시스템 등록 정보), `created` (현재 시스템 시간), `requiresRoot` (사용) `requiresRoot` 설정할 매개 변수), `packagePath` (그룹 및 패키지 이름에서 자동으로 생성됨) |
| `requiresRoot` | `boolean` | 예 | false | 패키지에 루트가 필요한지 여부를 정의합니다. 이렇게 되면 `requiresRoot` 속성 `properties.xml` 파일. |
| `subPackages` | `java.util.List` | 아니요 | 없음 |  |
| `version` | `java.lang.String` | 예 | Maven 프로젝트에 정의된 버전 | 컨텐츠 패키지의 버전입니다. |
| `workDirectory` | `java.io.File` | 예 | Maven 프로젝트(빌드 단계)에 정의된 디렉터리 | 패키지에 포함할 컨텐츠가 들어 있는 디렉토리 |

#### 필터 사용 {#using-filters}

필터 요소를 사용하여 패키지 콘텐츠를 정의합니다. 필터가 `workspaceFilter` 요소의 요소 `META-INF/vault/filter.xml` 패키지의 파일입니다.

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

다음 `mode` 요소는 패키지를 가져올 때 저장소가 미치는 영향을 정의합니다. 다음 값을 사용할 수 있습니다.

* **병합:** 저장소에 아직 없는 패키지의 콘텐츠가 추가됩니다. 패키지와 저장소 모두에 있는 컨텐츠는 변경되지 않습니다. 저장소에서 콘텐츠가 제거되지 않습니다.
* **바꾸기:** 저장소에 없는 패키지의 콘텐츠가 저장소에 추가됩니다. 저장소의 컨텐츠는 패키지의 일치하는 컨텐츠로 대체됩니다. 패키지에 존재하지 않으면 저장소에서 컨텐츠가 제거됩니다.
* **업데이트:** 저장소에 없는 패키지의 콘텐츠가 저장소에 추가됩니다. 저장소의 컨텐츠는 패키지의 일치하는 컨텐츠로 대체됩니다. 기존 컨텐츠가 저장소에서 제거됩니다.

필터에 없음 포함 `mode` 요소, 기본값은 `replace` 이 사용됩니다.

### 도움말 {#help}

#### 매개변수 {#parameters-6}

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `detail` | `boolean` | 아니요 | `false` | 각 목표에 대한 모든 설정 가능한 속성을 표시할지 여부를 결정합니다 |
| `goal` | `String` | 아니요 | 없음 | 이 매개 변수는 도움말을 표시할 목표의 이름을 정의합니다. 값을 지정하지 않으면 모든 목표에 대한 도움말이 표시됩니다. |
| `indentSize` | `int` | 아니요 | `2` | 각 레벨의 들여쓰기에 사용할 공백 수(정의된 경우 양수여야 함) |
| `lineLength` | `int` | 아니요 | `80` | 디스플레이 라인의 최대 길이(정의된 경우 양수여야 함) |

## 패키지에 축소판 이미지 또는 속성 파일 포함 {#including-a-thumbnail-image-or-properties-file-in-the-package}

기본 패키지 구성 파일을 대체하여 패키지 속성을 사용자 지정합니다. 예를 들어 의 패키지를 구분할 수 있도록 축소판 이미지를 포함합니다 [패키지 관리자.](/help/implementing/developing/tools/package-manager.md)

소스 파일은 파일 시스템의 어느 곳에서든 찾을 수 있습니다. POM 파일에서 소스 파일을 `target/vault-work/META-INF` 를 참조하십시오.

다음 POM 코드는 `META-INF` 패키지에 대한 프로젝트 소스의 폴더:

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

다음 POM 코드는 패키지에 축소판 이미지만 추가합니다. 축소판 이미지의 이름을 지정해야 합니다 `thumbnail.png`, 및은(는) `META-INF/vault/definition` 패키지의 폴더입니다. 이 예제에서 소스 파일은 `/src/main/content/META-INF/vault/definition` 프로젝트의 폴더:

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

## AEM Project Archetype을 사용하여 AEM 프로젝트 생성 {#using-archetypes}

최신 AEM 프로젝트 원형 은 온프레미스 및 AMS 구현 모두에 대한 모범 사례 패키지 구조를 구현하며 모든 AEM 프로젝트에 권장됩니다.

>[!TIP]
>
>자세한 내용은 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) AEM as a Cloud Service 설명서 및 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 설명서. 둘 다 AEM 6.5에서 완전히 지원됩니다.
