---
title: UI 테스트
description: 사용자 정의 UI 테스트는 사용자 정의 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 0ea7255f4dfc5c9f2e99cb144ef58152a2565822
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 95%

---


# UI 테스트 {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI 테스트"
>abstract="사용자 정의 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다. UI 테스트는 언어 및 프레임워크(예: Java 및 Maven, Node 및 WebDriver.io 또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)에서 다양한 선택을 허용하도록 도커 이미지에 패키징된 Selenium 기반 테스트입니다."

사용자 정의 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다.

## 개요 {#custom-ui-testing}

AEM은 사용자 정의 애플리케이션에 대한 원활한 업데이트를 보장하기 위해 통합된 [Cloud Manager 품질 게이트](/help/implementing/cloud-manager/custom-code-quality-rules.md) 제품군을 제공합니다 특히 IT 테스트 게이트는 이미 AEM API를 사용하여 사용자 정의 테스트를 생성 및 자동화하고 있습니다.

UI 테스트는 언어 및 프레임워크(예: Java 및 Maven, Node 및 WebDriver.io 또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)에서 다양한 선택을 허용하도록 도커 이미지에 패키징된 Selenium 기반 테스트입니다. 또한 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 사용하여 UI 테스트 프로젝트를 쉽게 생성할 수 있습니다.

UI 테스트는 [전용 **사용자 정의 UI 테스트** 단계를 통해 각 Cloud Manager 파이프라인에 대한 특정 품질 게이트의 일부로 실행됩니다.](/help/implementing/cloud-manager/deploy-code.md) 회귀 및 새로운 기능을 포함한 모든 UI 테스트를 통해 오류를 감지하고 보고할 수 있습니다.

Java로 작성된 HTTP 테스트인 사용자 정의 기능 테스트와 달리 UI 테스트는 [UI 테스트 빌드](#building-ui-tests) 섹션에 정의된 규칙을 따르는 한 모든 언어로 작성된 테스트가 포함된 도커 이미지가 될 수 있습니다.

>[!TIP]
>
>Adobe는 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)에서 제공하는 구조와 언어(JavaScript 및 WDIO)를 따를 것을 권장합니다.

### 고객 옵트인 {#customer-opt-in}

Cloud Manager가 UI 테스트를 빌드하고 실행하려면 저장소에 파일을 추가하여 이 기능을 선택해야 합니다.

* 파일 이름은 `testing.properties`여야 합니다.
* 파일 콘텐츠는 `ui-tests.version=1`이어야 합니다.
* 파일은 UI 테스트 하위 모듈의 `pom.xml` 파일 옆에 있는 UI 테스트용 maven 하위 모듈 아래에 있어야 합니다.
* 파일은 빌드된 `tar.gz` 파일의 루트에 있어야 합니다.

이 파일이 없으면 UI 테스트 빌드 및 실행을 건너뜁니다.

빌드 아티팩트에 `testing.properties` 파일을 포함하려면 `assembly-ui-test-docker-context.xml` 파일에 `include` 문을 추가합니다.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!-- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>프로젝트에 이 줄이 포함되지 않은 경우 UI 테스트를 선택하도록 파일을 편집해야 합니다.
>
>파일에 편집하지 말라는 내용의 줄이 포함될 수 있습니다. 이는 옵트인 UI 테스트가 도입되기 전에 프로젝트에 도입되었고 클라이언트가 파일을 편집할 의도가 없었기 때문입니다. 이 경고는 간단히 무시할 수 있습니다.

## UI 테스트 빌드 {#building-ui-tests}

Maven 프로젝트는 도커 빌드 컨텍스트를 생성합니다. 이 도커 빌드 컨텍스트는 Cloud Manager 사용자가 실제 UI 테스트가 포함된 도커 이미지를 생성할 수 있도록 UI 테스트가 포함된 도커 이미지를 만드는 방법을 설명합니다.

이 섹션에서는 UI 테스트 프로젝트를 저장소에 추가하는 데 필요한 단계를 설명합니다.

>[!TIP]
>
>[AEM Project Archetype](https://github.com/adobe/aem-project-archetype)은 프로그래밍 언어에 대한 특별한 요구 사항이 없는 사용자를 위해 UI 테스트 프로젝트를 생성할 수 있습니다.

### 도커 빌드 컨텍스트 생성 {#generate-docker-build-context}

도커 빌드 컨텍스트를 생성하려면 다음 작업을 수행하는 Maven 모듈이 필요합니다.

* 테스트로 도커 이미지를 빌드하는 데 필요한 `Dockerfile` 및 기타 모든 파일을 포함하는 아카이브를 생성합니다.
* 아카이브에 `ui-test-docker-context` 분류자로 태그를 지정합니다.

이를 수행하는 가장 간단한 방법은 도커 빌드 컨텍스트 아카이브를 만들고 여기에 올바른 분류자를 할당하도록 [Maven 어셈블리 플러그인](https://maven.apache.org/plugins/maven-assembly-plugin/)을 구성하는 것입니다.

다양한 기술과 프레임워크를 사용하여 UI 테스트를 빌드할 수 있지만 이 섹션에서는 프로젝트가 다음과 유사한 방식으로 배치되어 있다고 가정합니다.

```text
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

이 실행은 Maven 어셈블리 플러그인이 플러그인 전문 용어로 **어셈블리 설명자**&#x200B;라고 하는 `assembly-ui-test-docker-context.xml`에 포함된 지침을 기반으로 아카이브를 생성하도록 지시합니다. 어셈블리 설명자는 아카이브의 일부여야 하는 모든 파일을 나열합니다.

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

어셈블리 설명자는 플러그인에 `.tar.gz` 유형의 아카이브를 생성하고 `ui-test-docker-context` 분류자를 할당하도록 지시합니다. 또한 다음을 포함하여 아카이브에 포함되어야 하는 파일을 나열합니다.

* 도커 이미지 빌드에 필수인 `Dockerfile`
* 아래에 목적이 설명되어 있는 `wait-for-grid.sh` 스크립트
* `test-module` 폴더의 Node.js 프로젝트에서 구현한 실제 UI 테스트

어셈블리 설명자는 UI 테스트를 로컬에서 실행하는 동안 생성될 수 있는 일부 파일도 제외합니다. 이를 통해 아카이브 크기는 작아지고 빌드 속도는 빨라집니다.

도커 빌드 컨텍스트가 포함된 아카이브는 Cloud Manager에 의해 자동으로 선택되며, Cloud Manager는 배포 파이프라인 중에 테스트가 포함된 도커 이미지를 빌드합니다. 결국 Cloud Manager는 도커 이미지를 실행하여 애플리케이션에 대한 UI 테스트를 실행합니다.

빌드는 0개 또는 1개의 아카이브를 생성해야 합니다. 아카이브가 생성되지 않으면 테스트 단계가 기본적으로 통과합니다. 빌드가 둘 이상의 아카이브를 생성하는 경우 선택되는 아카이브는 비결정적입니다.

## UI 테스트 작성 {#writing-ui-tests}

이 섹션에서는 UI 테스트가 포함된 도커 이미지가 따라야 하는 규칙에 대해 설명합니다. Docker 이미지는 이전 섹션에서 설명한 도커 빌드 컨텍스트에서 빌드됩니다.

### 환경 변수 {#environment-variables}

다음 환경 변수는 런타임에 도커 이미지에 전달됩니다.

| 변수 | 예 | 설명 |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Selenium 서버의 URL |
| `SELENIUM_BROWSER` | `chrome` | Selenium 서버에서 사용하는 브라우저 구현 |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | AEM 작성자 인스턴스의 URL |
| `AEM_AUTHOR_USERNAME` | `admin` | AEM 작성자 인스턴스에 로그인하기 위한 사용자 이름 |
| `AEM_AUTHOR_PASSWORD` | `admin` | AEM 작성자 인스턴스에 로그인하기 위한 암호 |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | AEM 게시 인스턴스의 URL |
| `AEM_PUBLISH_USERNAME` | `admin` | AEM 게시 인스턴스에 로그인하기 위한 사용자 이름 |
| `AEM_PUBLISH_PASSWORD` | `admin` | AEM 게시 인스턴스에 로그인하기 위한 암호 |
| `REPORTS_PATH` | `/usr/src/app/reports` | 테스트 결과의 XML 보고서를 저장해야 하는 경로 |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Selenium에 액세스할 수 있도록 파일을 업로드해야 하는 URL |

### Selenium이 준비될 때까지 대기 {#waiting-for-selenium}

테스트가 시작되기 전에 Selenium 서버가 실행 중인지 확인하는 것은 도커 이미지의 책임입니다. Selenium 서비스 대기는 2단계 프로세스입니다.

1. `SELENIUM_BASE_URL` 환경 변수에서 Selenium 서비스의 URL을 읽습니다.
1. Selenium API에 의해 노출된 [상태 끝점](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready)에 정기적으로 폴링합니다.

Selenium의 상태 끝점이 긍정 응답을 보내면 테스트를 시작할 수 있습니다.

### 테스트 보고서 생성 {#generate-test-reports}

도커 이미지는 JUnit XML 형식으로 테스트 보고서를 생성하고 환경 변수 `REPORTS_PATH`에 지정된 경로에 저장해야 합니다. JUnit XML 형식은 테스트 결과를 보고하는 데 널리 사용되는 형식입니다. 도커 이미지가 Java 및 Maven을 사용하는 경우 [Maven Surefire 플러그인](https://maven.apache.org/surefire/maven-surefire-plugin/) 및 [Maven Failsafe 플러그인](https://maven.apache.org/surefire/maven-failsafe-plugin/)과 같은 표준 테스트 모듈은 즉시 이러한 보고서를 생성할 수 있습니다

도커 이미지가 다른 프로그래밍 언어 또는 테스트 실행자로 구현된 경우 선택한 도구에 대한 설명서에서 JUnit XML 보고서를 생성하는 방법을 확인하십시오.

### 스크린샷 및 비디오 캡처 {#capture-screenshots}

Docker 이미지는 추가 테스트 출력(예: 스크린샷, 비디오)을 생성하고 환경 변수에 지정된 경로에 저장할 수 있습니다 `REPORTS_PATH`. 아래에 있는 모든 파일 `REPORTS_PATH` 테스트 결과 아카이브에 포함됩니다.

UI 테스트 실행 중에 테스트 결과 아카이브를 만든 경우 테스트 로그 파일의 끝에 테스트 결과 아카이브 위치에 대한 참조가 포함됩니다.

```
[...]

===============================================================
The detailed test results can be downloaded from the URL below.
Note: the link will expire after 60 days

    https://results-host/test-results.zip

===============================================================
```

### 파일 업로드 {#upload-files}

경우에 따라 테스트 중인 애플리케이션에 파일을 업로드해야 합니다. 테스트에 비해 Selenium을 유연하게 배치하기 위해 에셋을 Selenium에 직접 업로드 할 수 없습니다. 대신 파일을 업로드하려면 다음 단계가 필요합니다.

1. `UPLOAD_URL` 환경 변수로 지정된 URL에서 파일을 업로드합니다.
   * 업로드는 다중 부분 양식으로 된 하나의 POST 요청으로 수행되어야 합니다.
   * 다중 부분 양식에는 단일 파일 필드가 있어야 합니다.
   * 이는 `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`에 해당합니다.
   * 이러한 HTTP 요청을 수행하는 방법을 알아보려면 도커 이미지에 사용된 프로그래밍 언어의 문서 및 라이브러리를 참조하십시오.
1. 업로드가 성공하면 요청은 `text/plain` 유형의 `200 OK` 응답을 반환합니다.
   * 응답의 내용은 불투명한 파일 핸들입니다.
   * `<input>` 요소의 파일 경로 대신 이 핸들을 사용하여 애플리케이션에서 파일 업로드를 테스트할 수 있습니다.
