---
title: UI 테스트 - Cloud Services
description: UI 테스트 - Cloud Services
translation-type: tm+mt
source-git-commit: bf3fb5178bc2ae72e19ecc1de82b08fac5089ecf
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---


# UI 테스트 {#ui-testing}

>[!CAUTION]
>
>이 기능은 아직 일반적으로 사용할 수 없습니다.


UI 테스트는 Selenium 기반 테스트로, Java 및 Maven, Node 및 WebDriver.io와 같은 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)에서 광범위한 선택을 할 수 있도록 Docker 이미지에 패키지되어 있습니다. Docker 이미지는 표준 도구로 만들 수 있지만 실행 중에는 특정 규칙을 준수해야 합니다. Docker 이미지를 실행하면 Selenium 서버가 자동으로 프로비저닝됩니다. 아래에 설명된 런타임 규칙을 통해 테스트 코드가 Selenium 서버와 테스트 중인 AEM 인스턴스 모두에 액세스할 수 있습니다.

## UI 테스트 작성 중 {#building-ui-tests}

UI 테스트는 마비안 프로젝트에서 생성된 Docker 빌드 컨텍스트에서 빌드됩니다. 클라우드 관리자는 Docker 빌드 컨텍스트를 사용하여 실제 UI 테스트가 포함된 Docker 이미지를 생성합니다. 요약하면 Maven 프로젝트가 Docker 빌드 컨텍스트를 생성하고 Docker 빌드 컨텍스트는 UI 테스트가 포함된 Docker 이미지를 만드는 방법을 설명합니다.

이 섹션에서는 저장소에 UI 테스트 프로젝트를 추가하는 데 필요한 단계를 안내합니다. 프로그래밍 언어에 대한 특별한 요구 사항이 없거나 급하게 사용하는 경우 [AEM Project Tranype](https://github.com/adobe/aem-project-archetype)에서 UI 테스트 프로젝트를 생성할 수 있습니다.

### Docker 빌드 컨텍스트 {#generate-docker-build-context} 생성

Docker 빌드 컨텍스트를 생성하려면 다음과 같은 Maven 모듈이 필요합니다.

- 테스트로 Docker 이미지를 만드는 데 필요한 `Dockerfile` 및 기타 모든 파일이 포함된 아카이브를 만듭니다.
- 아카이브에 `ui-test-docker-context` 분류자를 추가합니다.

이를 수행하는 가장 간단한 방법은 [Maven Assembly Plugin](http://maven.apache.org/plugins/maven-assembly-plugin/)을 구성하여 Docker 빌드 컨텍스트 아카이브를 만들고 올바른 분류자를 할당합니다.

다른 기술 및 프레임워크로 UI 테스트를 빌드할 수 있지만 이 섹션에서는 프로젝트가 다음과 유사한 방식으로 배치된다고 가정합니다.

```
├── Dockerfile
├── assembly-ui-test-docker-context.xml
├── pom.xml
├── test-module
│   ├── package.json
│   ├── index.js
│   └── wdio.conf.js
└── wait-for-grid.sh
```

`pom.xml` 파일은 Maven 빌드를 처리합니다. 다음과 유사한 Maven 어셈블리 플러그인에 실행을 추가합니다.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <descriptors>
            <descriptor>${project.basedir}/assembly-ui-test-docker-context.xml</descriptor>
        </descriptors>
        <tarLongFileMode>gnu</tarLongFileMode>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

이 실행은 Maben Assembly Plugin이 플러그인의 은어에 &quot;어셈블리 설명자&quot;라고 하는 `assembly-ui-test-docker-context.xml`에 포함된 지침에 따라 아카이브를 만들도록 지시합니다. 어셈블리 설명자는 아카이브에 속해야 하는 모든 파일을 나열합니다.

```xml
<assembly>
    <id>ui-test-docker-context</id>
    <includeBaseDirectory>false</includeBaseDirectory>
    <formats>
        <format>tar.gz</format>
    </formats>
    <fileSets>
        <fileSet>
            <directory>${basedir}</directory>
            <includes>
                <include>Dockerfile</include>
                <include>wait-for-grid.sh</include>
            </includes>
        </fileSet>
        <fileSet>
            <directory>${basedir}/test-module</directory>
            <excludes>
                <exclude>node/**</exclude>
                <exclude>node_modules/**</exclude>
                <exclude>reports/**</exclude>
            </excludes>
        </fileSet>
    </fileSets>
</assembly>
```

어셈블리 설명자는 플러그인이 `.tar.gz` 유형의 아카이브를 만들도록 지시하고 이 파일에 `ui-test-docker-context` 분류자를 할당합니다. 또한 아카이브에 포함되어야 하는 파일이 나열됩니다.

- Docker 이미지를 빌드해야 하는 `Dockerfile`
- 아래에 설명된 목적에 해당하는 `wait-for-grid.sh` 스크립트입니다.
- 실제 UI 테스트는 `test-module` 폴더의 Node.js 프로젝트에 의해 구현됩니다.

또한 어셈블리 설명자는 UI 테스트를 로컬로 실행하는 동안 생성할 수 있는 일부 파일을 제외합니다. 이렇게 하면 더 작은 아카이브와 빠른 빌드가 보장됩니다.

Docker 빌드 컨텍스트가 포함된 아카이브는 Cloud Manager에서 자동으로 선택되므로 배포 과정에서 테스트가 포함된 Docker 이미지를 만들 수 있습니다. Cloud Manager는 Docker 이미지를 실행하여 애플리케이션에 대한 UI 테스트를 실행합니다.

## UI 테스트 작성 중 {#writing-ui-tests}

이 섹션에서는 UI 테스트가 들어 있는 Docker 이미지가 따라야 하는 규칙을 설명합니다. Docker 이미지는 이전 섹션에 설명된 Docker 빌드 컨텍스트에서 빌드됩니다.

### 환경 변수 {#environment-variables}

다음 환경 변수는 런타임에 Docker 이미지에 전달됩니다.

| 변수 | 예 | 설명 |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Selenium 서버의 URL |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | Selenium Server에서 사용하는 브라우저 구현 |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | AEM 작성자 인스턴스의 URL |
| `AEM_AUTHOR_USERNAME` | `admin` | AEM 작성자 인스턴스에 로그인하는 사용자 이름 |
| `AEM_AUTHOR_PASSWORD` | `admin` | AEM 작성자 인스턴스에 로그인하는 암호 |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | AEM 게시 인스턴스의 URL |
| `AEM_PUBLISH_USERNAME` | `admin` | AEM 게시 인스턴스에 로그인하는 사용자 이름 |
| `AEM_PUBLISH_PASSWORD` | `admin` | AEM 게시 인스턴스에 로그인하는 암호 |
| `REPORTS_PATH` | `/usr/src/app/reports` | 테스트 결과의 XML 보고서를 저장해야 하는 경로 |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Selenium에서 파일에 액세스할 수 있도록 파일을 업로드해야 하는 URL |

### Selenium이 {#waiting-for-selenium} 준비되기를 기다리는 중

테스트가 시작되기 전에 Selenium 서버가 실행 중인지 확인하는 것은 Docker 이미지의 책임입니다. Selenium 서비스를 기다리는 것은 2단계 과정입니다.

1. `SELENIUM_BASE_URL` 환경 변수에서 Selenium 서비스의 URL을 읽습니다.
2. Selenium API에 의해 노출되는 [상태 끝점](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready)에 대한 정규 간격으로 폴링합니다.

Selenium의 상태 끝점이 긍정적인 응답으로 응답하면 테스트를 마침내 시작할 수 있습니다.

### 테스트 보고서 생성 {#generate-test-reports}

Docker 이미지는 테스트 보고서를 JUnit XML 형식으로 생성한 후 환경 변수 `REPORTS_PATH`에 의해 지정된 경로에 저장해야 합니다. JUnit XML 형식은 테스트 결과를 보고하는 광범위한 형식입니다. Docker 이미지가 Java 및 Maven을 사용하는 경우 [Maven Suresfire Plugin](https://maven.apache.org/surefire/maven-surefire-plugin/) 및 [Maven Failsafe Plugin](https://maven.apache.org/surefire/maven-failsafe-plugin/) 모두 사용하십시오. Docker 이미지가 다른 프로그래밍 언어로 구현되거나 테스트 러너를 사용하는 경우 선택한 도구에 대한 설명서를 참조하여 JUnit XML 보고서를 생성하는 방법을 확인하십시오.

### 파일 업로드(#upload-files)

테스트는 테스트 중인 응용 프로그램에 파일을 업로드해야 하는 경우가 있습니다. 테스트를 기준으로 Selenium 배포를 유연하게 유지하기 위해 자산을 Selenium에 직접 업로드할 수 없습니다. 대신 파일 업로드는 몇 가지 중간 단계를 거칩니다.

1. `UPLOAD_URL` 환경 변수에 의해 지정된 URL에서 파일을 업로드합니다. 업로드는 여러 부분으로 구성된 하나의 POST 요청에서 수행해야 합니다. 다중 부분 양식에는 단일 파일 필드가 있어야 합니다. 이것은 `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`과 같습니다. 이러한 HTTP 요청을 수행하는 방법에 대해 알아보려면 Docker 이미지에 사용되는 프로그래밍 언어의 설명서 및 라이브러리를 참조하십시오.
2. 업로드가 성공하면 `text/plain` 유형의 `200 OK` 응답이 반환됩니다. 응답의 내용은 불투명한 파일 핸들입니다. `<input>` 요소의 파일 경로 대신 이 핸들을 사용하여 응용 프로그램에서 파일 업로드를 테스트할 수 있습니다.
