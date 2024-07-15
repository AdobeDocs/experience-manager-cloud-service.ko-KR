---
title: Adobe 컨텐츠 패키지 Maven 플러그인
description: Content Package Maven 플러그인을 사용하여 AEM 애플리케이션 배포
exl-id: d631d6df-7507-4752-862b-9094af9759a0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: d757c94475f257ee4b05092671ae5e6384b8342e
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 4%

---

# Adobe 컨텐츠 패키지 Maven 플러그인 {#adobe-content-package-maven-plugin}

Adobe Content Package Maven 플러그인을 사용하여 패키지 배포 및 관리 작업을 Maven 프로젝트에 통합합니다.

빌드된 패키지를 AEM에 배포하는 작업은 Adobe Content Package Maven 플러그인에 의해 수행되며, AEM [패키지 관리자:](/help/implementing/developing/tools/package-manager.md)를 사용하여 일반적으로 수행되는 작업을 자동화할 수 있습니다.

* 파일 시스템의 파일에서 새 패키지를 만듭니다.
* AEM에서 패키지를 설치 및 제거합니다.
* AEM에 이미 정의된 패키지를 빌드합니다.
* AEM에 설치된 패키지 목록을 가져옵니다.
* AEM에서 패키지를 제거합니다.

이 문서에서는 Maven을 사용하여 이러한 작업을 관리하는 방법을 자세히 설명합니다. 그러나 [AEM 프로젝트와 패키지의 구성 방식을 이해하는 것도 중요합니다.](#aem-project-structure)

>[!NOTE]
>
>이러한 플러그인의 사용 가능한 최신 버전을 항상 사용하십시오.

>[!NOTE]
>
>**만들기** 패키지는 이제 [Apache Jackrabbit FileVault 패키지 Maven 플러그인이 소유합니다.](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
>
>이 문서에서는 Adobe Content Package Maven 플러그인이 수행한 AEM에 대한 구성된 패키지의 **deployment**&#x200B;에 대해 설명합니다.

## 패키지 및 AEM 프로젝트 구조 {#aem-project-structure}

AEM as a Cloud Service은 최신 AEM Project Archetype에 의해 구현된 패키지 관리 및 프로젝트 구조에 대한 최신 모범 사례를 준수합니다.

>[!TIP]
>
>AEM as a Cloud Service 설명서와 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 설명서에서 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 문서를 참조하십시오. 둘 다 AEM 6.5에 대해 완전히 지원됩니다.

## 콘텐츠 패키지 Maven 플러그인 가져오기 {#obtaining-the-content-package-maven-plugin}

플러그인은 [Maven 중앙 리포지토리에서 사용할 수 있습니다.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## 콘텐츠 패키지 Maven 플러그인 목표 및 매개 변수

Content Package Maven Plugin을 사용하려면 POM 파일의 빌드 요소 내에 다음 플러그인 요소를 추가합니다.

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

Maven이 플러그인을 다운로드할 수 있도록 하려면 이 페이지의 [콘텐츠 패키지 Maven 플러그인 가져오기](#obtaining-the-content-package-maven-plugin) 섹션에 제공된 프로필을 사용하십시오.

## 콘텐츠 패키지 Maven 플러그인의 목표 {#goals-of-the-content-package-maven-plugin}

콘텐츠 패키지 플러그인이 제공하는 목표 및 목표 매개 변수는 다음 섹션에 설명되어 있습니다. 공통 매개변수 섹션에 설명된 매개변수는 대부분의 목표에 사용할 수 있습니다. 하나의 목표에 적용되는 매개변수는 해당 목표에 대한 섹션에 설명되어 있습니다.

### 플러그인 접두사 {#plugin-prefix}

플러그 인 접두사는 `content-package`입니다. 다음 예제와 같이 이 접두사를 사용하여 명령줄에서 목표를 실행합니다.

```shell
mvn content-package:build
```

### 매개 변수 접두사 {#parameter-prefix}

달리 명시되지 않는 한 플러그인 목표 및 매개 변수는 다음 예제와 같이 `vault` 접두사를 사용합니다.

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### 프록시 {#proxies}

AEM용 프록시를 사용하는 목표는 Maven 설정에 있는 첫 번째 유효한 프록시 구성을 사용합니다. 프록시 구성을 찾을 수 없으면 프록시가 사용되지 않습니다. [일반 매개 변수](#common-parameters) 섹션에서 `useProxy` 매개 변수를 참조하십시오.

### 일반 매개 변수 {#common-parameters}

다음 표의 매개 변수는 **Goals** 열에 명시되어 있는 경우를 제외하고 모든 목표에 공통됩니다.

| 이름 | 유형 | 필수 | 기본 값 | 설명 | 목표 |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | 아니요 | `false` | 값이 `true`이면 오류가 발생할 때 빌드가 실패합니다. 값이 `false`이면 빌드가 오류를 무시합니다. | `package`을(를) 제외한 모든 목표 |
| `name` | `String` | `build`: 예, `install`: 아니요, `rm`: 예 | `build`: 기본값 없음, `install`: Maven 프로젝트의 `artifactId` 속성 값 | 작업할 패키지의 이름 | `ls`을(를) 제외한 모든 목표 |
| `password` | `String` | 예 | `admin` | AEM 인증에 사용되는 암호 | `package`을(를) 제외한 모든 목표 |
| `serverId` | `String` | 아니요 | 인증을 위해 사용자 이름과 암호를 검색할 서버 ID | `package`을(를) 제외한 모든 목표 |
| `targetURL` | `String` | 예 | `http://localhost:4502/crx/packmgr/service.jsp` | AEM 패키지 관리자의 HTTP 서비스 API의 URL | `package`을(를) 제외한 모든 목표 |
| `timeout` | `int` | 아니요 | `5` | 패키지 관리자 서비스와 통신하기 위한 연결 시간 제한(초) | `package`을(를) 제외한 모든 목표 |
| `useProxy` | `boolean` | 아니요 | `true` | 값이 `true`이면 Maven이 패키지 관리자에 대한 요청을 프록시하기 위해 찾은 첫 번째 활성 프록시 구성을 사용합니다. | `package`을(를) 제외한 모든 목표 |
| `userId` | `String` | 예 | `admin` | AEM으로 인증할 사용자 이름 | `package`을(를) 제외한 모든 목표 |
| `verbose` | `boolean` | 아니요 | `false` | 자세한 로깅 활성화 또는 비활성화 | `package`을(를) 제외한 모든 목표 |

### 빌드 {#build}

AEM 인스턴스에 이미 정의된 콘텐츠 패키지를 빌드합니다.

>[!NOTE]
>
>이 목표는 Maven 프로젝트 내에서 실행할 필요가 없습니다.

#### 매개변수 {#parameters}

빌드 목표에 대한 모든 매개 변수는 [일반 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### 설치 {#install}

저장소에 패키지를 설치합니다. 이 목표를 실행하려면 Maven 프로젝트가 필요하지 않습니다. 목표는 Maven 빌드 주기의 `install` 단계에 바인딩되어 있습니다.

#### 매개변수 {#parameters-1}

다음 매개 변수 외에 [일반 매개 변수](#common-parameters) 섹션의 설명을 참조하십시오.

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `artifact` | `String` | 아니요 | Maven 프로젝트의 `artifactId` 속성 값 | `groupId:artifactId:version[:packaging]` 형식의 문자열 |
| `artifactId` | `String` | 아니요 | 없음 | 설치할 아티팩트의 ID |
| `groupId` | `String` | 아니요 | 없음 | 설치할 아티팩트의 `groupId` |
| `install` | `boolean` | 아니요 | `true` | 패키지를 업로드할 때 패키지를 자동으로 압축 해제할지 여부를 결정합니다. |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | 아니요 | `localRepository` 시스템 변수의 값 | 시스템 속성이 항상 사용되므로 플러그인 구성을 사용하여 구성할 수 없는 로컬 Maven 저장소입니다 |
| `packageFile` | `java.io.File` | 아니요 | Maven 프로젝트에 대해 정의된 기본 아티팩트 | 설치할 패키지 파일의 이름 |
| `packaging` | `String` | 아니요 | `zip` | 설치할 아티팩트의 패키징 유형 |
| `pomRemoteRepositories` | `java.util.List` | 예 | Maven 프로젝트에 대해 정의된 `remoteArtifactRepositories` 속성의 값 | 이 값은 플러그인 구성을 사용하여 구성할 수 없으며 프로젝트에 지정해야 합니다. |
| `project` | `org.apache.maven.project.MavenProject` | 예 | 플러그인이 구성된 프로젝트 | 프로젝트에 플러그인 구성이 포함되어 있으므로 암시적인 Maven 프로젝트 |
| `repositoryId`(POM), `repoID`(명령줄) | `String` | 아니요 | `temp` | 아티팩트가 검색되는 저장소의 ID |
| `repositoryUrl`(POM), `repoURL`(명령줄) | `String` | 아니요 | 없음 | 객체를 검색할 저장소의 URL |
| 버전 | 문자열 | 아니요 | 없음 | 설치할 아티팩트의 버전입니다 |

### ls {#ls}

[패키지 관리자](/help/implementing/developing/tools/package-manager.md)에 배포된 패키지를 나열합니다.

#### 매개변수 {#parameters-2}

ls 목표의 모든 매개 변수는 [공통 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### rm {#rm}

[패키지 관리자](/help/implementing/developing/tools/package-manager.md)에서 패키지를 제거합니다.

#### 매개변수 {#parameters-3}

rm 목표의 모든 매개 변수는 [일반 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.

### 제거 {#uninstall}

패키지를 제거합니다. 패키지는 서버에 제거됨 상태로 유지됩니다.

#### 매개변수 {#parameters-4}

제거 목표의 모든 매개 변수는 [일반 매개 변수](#common-parameters) 섹션에 설명되어 있습니다.


### 도움말 {#help}

#### 매개변수 {#parameters-6}

| 이름 | 유형 | 필수 | 기본 값 | 설명 |
|---|---|---|---|---|
| `detail` | `boolean` | 아니요 | `false` | 각 목표에 대해 설정 가능한 모든 속성을 표시할지 여부를 결정합니다. |
| `goal` | `String` | 아니요 | 없음 | 이 매개 변수는 도움말을 표시할 목표의 이름을 정의합니다. 값을 지정하지 않으면 모든 목표에 대한 도움말이 표시됩니다. |
| `indentSize` | `int` | 아니요 | `2` | 각 수준의 들여쓰기에 사용할 공백 수입니다(정의된 경우 양수여야 함). |
| `lineLength` | `int` | 아니요 | `80` | 표시 라인의 최대 길이(정의된 경우 양수여야 함) |

## 패키지에 썸네일 이미지 또는 속성 파일 포함 {#including-a-thumbnail-image-or-properties-file-in-the-package}

기본 패키지 구성 파일을 대체하여 패키지 속성을 사용자 지정합니다. 예를 들어 [패키지 관리자](/help/implementing/developing/tools/package-manager.md)에서 패키지를 구분할 축소판 이미지를 포함합니다.

소스 파일은 파일 시스템의 어디에나 위치할 수 있습니다. POM 파일에서 빌드 리소스를 정의하여 패키지에 포함할 원본 파일을 `target/vault-work/META-INF`(으)로 복사합니다.

다음 POM 코드는 프로젝트 원본의 `META-INF` 폴더에 있는 파일을 패키지에 추가합니다.

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail and so on) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

다음 POM 코드는 패키지에 썸네일 이미지만 추가합니다. 썸네일 이미지의 이름은 `thumbnail.png`이어야 하며 패키지의 `META-INF/vault/definition` 폴더에 있어야 합니다. 이 예제에서 소스 파일은 프로젝트의 `/src/main/content/META-INF/vault/definition` 폴더에 있습니다.

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

최신 AEM Project Archetype은 온-프레미스 및 AMS 구현 모두에 대한 모범 사례 패키지 구조를 구현하며 모든 AEM 프로젝트에 권장됩니다.

>[!TIP]
>
>AEM as a Cloud Service 설명서와 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 설명서에서 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 문서를 참조하십시오. 둘 다 AEM 6.5에 대해 완전히 지원됩니다.
