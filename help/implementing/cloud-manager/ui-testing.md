---
title: UI 테스트
description: 사용자 지정 UI 테스트는 사용자 지정 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택 기능입니다
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 2%

---


# UI 테스트 {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI 테스트"
>abstract="사용자 지정 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택 기능입니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다."

사용자 지정 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택 기능입니다.

## 개요 {#custom-ui-testing}

AEM은 [Cloud Manager 품질 게이트](/help/implementing/cloud-manager/custom-code-quality-rules.md) 사용자 정의 애플리케이션에 대한 원활한 업데이트를 위해 특히 IT는 AEM API를 사용하여 이미 사용자 지정 테스트를 만들고 자동화하는 게이트를 테스트합니다.

UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다. 또한, UI 테스트 프로젝트를 [AEM 프로젝트 원형.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

UI 테스트는 [전용 **사용자 지정 UI 테스트** 단계.](/help/implementing/cloud-manager/deploy-code.md) 회귀 및 새로운 기능을 포함한 모든 UI 테스트를 통해 오류를 감지하고 보고할 수 있습니다.

Java로 작성된 HTTP 테스트인 사용자 지정 기능 테스트와 달리, UI 테스트는 섹션에 정의된 규칙을 따르는 한 모든 언어로 작성된 테스트가 있는 Docker 이미지가 될 수 있습니다 [UI 테스트 작성.](#building-ui-tests)

>[!TIP]
>
>Adobe은 [AEM 프로젝트 원형.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)

### 고객 옵트인 {#customer-opt-in}

Cloud Manager에서 UI 테스트를 빌드하고 실행하려면 저장소에 파일을 추가하여 이 기능에 옵트인해야 합니다.

* 파일 이름은 다음과 같아야 합니다. `testing.properties`.
* 파일 내용은 `ui-tests.version=1`.
* 파일은 UI 테스트 옆에 있는 maven 하위 모듈 아래에 있어야 합니다 `pom.xml` UI 테스트 하위 모듈의 파일입니다.
* 파일은 빌드된 파일의 루트에 있어야 합니다 `tar.gz` 파일.

이 파일이 없으면 UI 테스트 빌드 및 실행을 건너뜁니다.

다음을 포함합니다 `testing.properties` 빌드 아티팩트에 있는 파일에서 `include` 의 문 `assembly-ui-test-docker-context.xml` 파일.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>프로젝트에 이 줄이 포함되어 있지 않으면 파일을 편집하여 UI 테스트를 수행해야 합니다.
>
>파일에 편집하지 말라는 줄이 포함되어 있을 수 있습니다. 이는 옵트인 UI 테스트가 도입되고 클라이언트의 파일이 파일을 편집하지 않았기 때문에, 프로젝트에 도입되기 때문입니다. 이것은 무시해도 된다.

## UI 테스트 작성 {#building-ui-tests}

Maven 프로젝트는 Docker 빌드 컨텍스트를 생성합니다. 이 Docker 빌드 컨텍스트는 실제 UI 테스트가 포함된 Docker 이미지를 생성하기 위해 Cloud Manager 사용자가 생성할 UI 테스트가 포함된 Docker 이미지를 만드는 방법을 설명합니다.

이 섹션에서는 리포지토리에 UI 테스트 프로젝트를 추가하는 데 필요한 단계에 대해 설명합니다.

>[!TIP]
>
>다음 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype) 프로그래밍 언어에 대한 특별한 요구 사항이 없는 경우 UI 테스트 프로젝트를 생성할 수 있습니다.

### Docker 빌드 컨텍스트 생성 {#generate-docker-build-context}

Docker 빌드 컨텍스트를 생성하려면 다음과 같은 Maven 모듈이 필요합니다.

* 가 포함된 아카이브를 생성합니다. `Dockerfile` 테스트로 Docker 이미지를 빌드하는 데 필요한 모든 다른 파일입니다.
* 를 사용하여 아카이브에 태그 지정 `ui-test-docker-context` 분류자.

이렇게 하는 가장 간단한 방법은 [Maven 어셈블리 플러그인](https://maven.apache.org/plugins/maven-assembly-plugin/) docker 빌드 컨텍스트 아카이브를 만들고 이 설명서에 올바른 분류자를 할당합니다.

다양한 기술 및 프레임워크를 사용하여 UI 테스트를 작성할 수 있지만, 이 섹션에서는 프로젝트가 다음과 유사한 방식으로 표현된다고 가정합니다.

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

다음 `pom.xml` 파일은 Maven 빌드를 처리합니다. 다음과 유사한 Maven 어셈블리 플러그인에 실행을 추가합니다.

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

이 실행은 Maven 어셈블리 플러그인에 포함된 지침에 따라 아카이브를 만들도록 지시합니다 `assembly-ui-test-docker-context.xml`가 **어셈블리 설명자** 플러그인의 전문에서 어셈블리 설명자는 아카이브에 속해야 하는 모든 파일을 나열합니다.

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

어셈블리 설명자는 플러그인이 유형의 아카이브를 만들도록 지시합니다 `.tar.gz` 그리고 `ui-test-docker-context` 분류자. 또한 다음과 같이 아카이브에 포함해야 하는 파일이 나열됩니다.

* A `Dockerfile`, Docker 이미지 작성에 필수입니다.
* 다음 `wait-for-grid.sh` 스크립트, 아래에 설명된 용도
* 의 Node.js 프로젝트에 의해 구현된 실제 UI 테스트 `test-module` 폴더

또한 어셈블리 설명자는 UI 테스트를 로컬에서 실행하는 동안 생성할 수 있는 일부 파일을 제외합니다. 이를 통해 더 작은 아카이브와 더 빠른 빌드가 보장됩니다.

Docker 빌드 컨텍스트가 포함된 아카이브는 Cloud Manager에 의해 자동으로 선택됩니다. 이 관리자는 배포 파이프라인 중에 테스트가 포함된 Docker 이미지를 작성합니다. 결국 Cloud Manager는 Docker 이미지를 실행하여 애플리케이션에 대한 UI 테스트를 실행합니다.

빌드는 0이나 1개의 아카이브를 생성해야 합니다. 0개의 아카이브를 생성하는 경우 기본적으로 테스트 단계가 전달됩니다. 빌드에서 두 개 이상의 아카이브를 만드는 경우 선택한 아카이브가 결정적이지 않습니다.

## UI 테스트 작성 {#writing-ui-tests}

이 섹션에서는 UI 테스트가 포함된 Docker 이미지가 따라야 하는 규칙을 설명합니다. Docker 이미지는 이전 섹션에 설명된 Docker 빌드 컨텍스트에서 빌드됩니다.

### 환경 변수 {#environment-variables}

다음 환경 변수가 런타임에 Docker 이미지에 전달됩니다.

| 변수 | 예 | 설명 |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Selenium 서버의 URL |
| `SELENIUM_BROWSER` | `chrome` | Selenium 서버에서 사용하는 브라우저 구현 |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | AEM 작성자 인스턴스의 URL |
| `AEM_AUTHOR_USERNAME` | `admin` | AEM 작성자 인스턴스에 로그인할 사용자 이름 |
| `AEM_AUTHOR_PASSWORD` | `admin` | AEM 작성자 인스턴스에 로그인할 암호입니다. |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | AEM 게시 인스턴스의 URL |
| `AEM_PUBLISH_USERNAME` | `admin` | AEM 게시 인스턴스에 로그인할 사용자 이름 |
| `AEM_PUBLISH_PASSWORD` | `admin` | AEM 게시 인스턴스에 로그인할 암호입니다. |
| `REPORTS_PATH` | `/usr/src/app/reports` | 테스트 결과의 XML 보고서를 저장해야 하는 경로입니다 |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Selenium에서 액세스할 수 있도록 하기 위해 파일을 업로드해야 하는 URL입니다 |

### Selenium 준비 대기 중 {#waiting-for-selenium}

테스트가 시작되기 전에 Selenium 서버가 작동 중인지 확인하는 것은 Docker 이미지의 책임입니다. Selenium 서비스를 기다리는 것은 두 단계로 이루어집니다.

1. 에서 Selenium 서비스의 URL을 읽습니다. `SELENIUM_BASE_URL` 환경 변수 입니다.
1. 정기적으로 폴링하여 [상태 끝점](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) 는 Selenium API에 의해 노출됩니다.

Selenium의 상태 끝점이 긍정적인 응답으로 응답하면 테스트가 시작될 수 있습니다.

### 테스트 보고서 생성 {#generate-test-reports}

Docker 이미지는 JUnit XML 형식으로 테스트 보고서를 생성하고 환경 변수에 지정된 경로에 저장해야 합니다 `REPORTS_PATH`. JUnit XML 형식은 테스트 결과를 보고하는 데 널리 사용되는 형식입니다. Docker 이미지가 Java 및 Maven을 사용하는 경우 다음과 같은 표준 테스트 모듈입니다 [Maven Suresfire 플러그인](https://maven.apache.org/surefire/maven-surefire-plugin/) 및 [Maven Failsafe 플러그인](https://maven.apache.org/surefire/maven-failsafe-plugin/) 은 즉시 이러한 보고서를 생성할 수 있습니다.

다른 프로그래밍 언어나 테스트 러너와 함께 Docker 이미지가 구현된 경우 선택한 도구에서 JUnit XML 보고서를 생성하는 방법을 확인하십시오.

### 파일 업로드 {#upload-files}

테스트는 경우에 따라 테스트 중인 응용 프로그램에 파일을 업로드해야 합니다. Selenium의 배포를 테스트와 관련하여 유연하게 유지하려면 자산을 Selenium에 직접 업로드할 수 없습니다. 대신 파일을 업로드하려면 다음 단계를 수행해야 합니다.

1. 에서 지정한 URL에 파일을 업로드합니다. `UPLOAD_URL` 환경 변수 입니다.
   * 다중 부분 양식이 있는 하나의 POST 요청에서 업로드를 수행해야 합니다.
   * 다중 부분 양식에는 단일 파일 필드가 있어야 합니다.
   * 이것은 다음과 같습니다 `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * 이러한 HTTP 요청을 수행하는 방법을 알아보려면 Docker 이미지에 사용되는 프로그래밍 언어의 설명서 및 라이브러리를 참조하십시오.
1. 업로드가 성공적으로 수행되면 요청은 를 반환합니다. `200 OK` 유형 응답 `text/plain`.
   * 응답의 컨텐츠는 불투명한 파일 핸들입니다.
   * 이 핸들은 `<input>` 응용 프로그램에서 파일 업로드를 테스트할 요소입니다.
