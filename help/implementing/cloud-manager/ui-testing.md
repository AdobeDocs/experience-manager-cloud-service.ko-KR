---
title: UI 테스트 - Cloud Services
description: UI 테스트 - Cloud Services
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 02db915e114c2af8329eaddbb868045944a3574d
workflow-type: tm+mt
source-wordcount: '1617'
ht-degree: 1%

---

# UI 테스트 {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI 테스트"
>abstract="UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다. Docker 이미지는 표준 도구를 사용하여 만들 수 있지만 실행 중에 특정 규칙을 준수해야 합니다. Docker 이미지를 실행할 때 Selenium 서버가 자동으로 프로비저닝됩니다. 아래 설명된 런타임 규칙을 통해 테스트 코드가 Selenium 서버와 테스트 중인 AEM 인스턴스에 모두 액세스할 수 있습니다."

UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다. Docker 이미지는 표준 도구를 사용하여 만들 수 있지만 실행 중에 특정 규칙을 준수해야 합니다. Docker 이미지를 실행할 때 Selenium 서버가 자동으로 프로비저닝됩니다. 아래 설명된 런타임 규칙을 통해 테스트 코드가 Selenium 서버와 테스트 중인 AEM 인스턴스에 모두 액세스할 수 있습니다.

>[!NOTE]
> 이 페이지에 설명된 대로 UI 테스트를 사용하려면 2021년 2월 10일 이전에 만들어진 단계 및 프로덕션 파이프라인을 업데이트해야 합니다.
> 자세한 내용은 [Cloud Manager의 CI-CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 파이프라인 구성에 대한 정보입니다.

## 사용자 지정 UI 테스트 {#custom-ui-testing}

AEM은 고객에게 Cloud Manager 품질 게이트의 통합 세트를 제공하여 애플리케이션을 원활하게 업데이트합니다. 특히 IT 테스트 게이트를 통해 고객은 이미 AEM API를 사용하는 자체 테스트를 만들고 자동화할 수 있습니다.

사용자 지정 UI 테스트 기능은 [옵션 기능](#customer-opt-in) 고객이 자신의 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있도록 해줍니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다. 여기에서 UI를 빌드하고 UI 테스트를 작성하는 방법에 대해 자세히 알아볼 수 있습니다. 또한 AEM Project Archetype을 사용하여 UI 테스트 프로젝트를 쉽게 생성할 수 있습니다.

고객은 GIT을 통해 사용자 지정 테스트를 만들고 UI용 테스트 세트를 만들 수 있습니다. UI 테스트는 각 Cloud Manager 파이프라인에 대한 특정 품질 게이트의 일부로서 특정 단계 및 피드백 정보와 함께 실행됩니다. 회귀 및 새로운 기능을 포함한 모든 UI 테스트를 통해 고객 컨텍스트 내에서 오류를 감지하고 보고할 수 있습니다.

고객 UI 테스트는 &quot;사용자 지정 UI 테스트&quot; 단계의 프로덕션 파이프라인에서 자동으로 실행됩니다.

Java로 작성된 HTTP 테스트인 사용자 지정 기능 테스트와 달리, UI 테스트는 다음에 정의된 규칙을 따르는 한 모든 언어로 작성된 테스트가 있는 Docker 이미지가 될 수 있습니다 [UI 테스트 작성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=en#building-ui-tests).

>[!NOTE]
>구조와 언어를 따르는 것이 좋습니다 *(js 및 wdio)* 간편하게 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) 시작점으로 사용하십시오.

### 고객 옵트인 {#customer-opt-in}

UI 테스트를 빌드하고 실행하려면 고객이 코드 리포지토리에 파일을 추가하고, UI 테스트 하위 모듈의 pom.xml 파일 옆에 있는 UI 테스트를 위한 maven 하위 모듈 아래에 있는 &quot;옵트인&quot;을 구현하고 이 파일이 빌드된 루트에 있는지 확인해야 합니다 `tar.gz` 파일.

*파일 이름*: `testing.properties`

*내용*: `ui-tests.version=1`

빌드되지 않은 경우 `tar.gz` 파일, UI 테스트 빌드 및 실행을 건너뜁니다

추가하려면 `testing.properties` 작성된 아티팩트에 파일을 추가하고 `include` 문 `assembly-ui-test-docker-context.xml` 파일(UI에서 테스트 하위 모듈). 프로젝트에 해당 줄이 포함되지 않은 경우 이 파일을 편집하여 UI 테스트를 받아야 합니다. 파일에 편집하지 말라는 줄이 있을 수 있다면 해당 조언을 무시하십시오.

    &quot;
    [..]
    &lt;includes>
    &lt;include>Dockerfile&lt;/include>
    &lt;include>wait-for-grid.sh&lt;/include>
    &lt;include>testing.properties&lt;/include> &lt;!>- Cloud Manager의 옵트인 테스트 모듈 —>
    &lt;/includes>
    [..]
    &quot;

>[!NOTE]
>이 섹션에 설명된 대로 UI 테스트를 사용하려면 2021년 2월 10일 전에 생성된 프로덕션 파이프라인을 업데이트해야 합니다. 이것은 사용자가 프로덕션 파이프라인을 편집하고 클릭해야 함을 의미합니다 **저장** 변경하지 않은 경우에도 UI에서 변경할 수 있습니다.
>을(를) 참조하십시오. [CI-CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager) 파이프라인 구성에 대해 자세히 알아보십시오 .

## UI 테스트 작성 {#building-ui-tests}

UI 테스트는 Maven 프로젝트에서 생성된 Docker 빌드 컨텍스트에서 빌드됩니다. Cloud Manager는 Docker 빌드 컨텍스트를 사용하여 실제 UI 테스트가 포함된 Docker 이미지를 생성합니다. 요약하면 Maven 프로젝트가 Docker 빌드 컨텍스트를 생성하고 Docker 빌드 컨텍스트는 UI 테스트가 포함된 Docker 이미지를 만드는 방법을 설명합니다.

이 섹션에서는 리포지토리에 UI 테스트 프로젝트를 추가하는 데 필요한 절차를 안내합니다. 프로그래밍 언어에 대한 특별한 요구 사항이 없는 경우 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype) 은 사용자를 위해 UI 테스트 프로젝트를 생성할 수 있습니다.

### Docker 빌드 컨텍스트 생성 {#generate-docker-build-context}

Docker 빌드 컨텍스트를 생성하려면 다음과 같은 Maven 모듈이 필요합니다.

- 가 포함된 아카이브를 생성합니다. `Dockerfile` 테스트로 Docker 이미지를 빌드하는 데 필요한 모든 다른 파일입니다.
- 를 사용하여 아카이브에 태그 지정 `ui-test-docker-context` 분류자.

이를 수행하는 가장 간단한 방법은 를 구성하는 것입니다 [Maven 어셈블리 플러그인](http://maven.apache.org/plugins/maven-assembly-plugin/) docker 빌드 컨텍스트 아카이브를 만들고 이 설명서에 올바른 분류자를 할당합니다.

다양한 기술 및 프레임워크를 사용하여 UI 테스트를 작성할 수 있지만, 이 섹션에서는 프로젝트가 다음과 유사한 방식으로 표현된다고 가정합니다.

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

이 실행은 Maven 어셈블리 플러그인에 포함된 지침에 따라 아카이브를 만들도록 지시합니다 `assembly-ui-test-docker-context.xml`플러그인의 은어에서 &quot;어셈블리 설명자&quot;라고 합니다. 어셈블리 설명자는 아카이브에 속해야 하는 모든 파일을 나열합니다.

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

어셈블리 설명자는 플러그인이 유형의 아카이브를 만들도록 지시합니다 `.tar.gz` 그리고 `ui-test-docker-context` 분류자. 또한 아카이브에 포함해야 하는 파일이 나열됩니다.

- A `Dockerfile`, Docker 이미지 작성에 필수입니다.
- 다음 `wait-for-grid.sh` 스크립트.
- 의 Node.js 프로젝트에 의해 구현된 실제 UI 테스트 `test-module` 폴더를 입력합니다.

또한 어셈블리 설명자는 UI 테스트를 로컬에서 실행하는 동안 생성할 수 있는 일부 파일을 제외합니다. 이를 통해 더 작은 아카이브와 더 빠른 빌드가 보장됩니다.

Docker 빌드 컨텍스트가 포함된 아카이브는 Cloud Manager에 의해 자동으로 선택되며, 이 경우 배포 파이프라인 중에 테스트가 포함된 Docker 이미지가 작성됩니다. 결국 Cloud Manager는 Docker 이미지를 실행하여 애플리케이션에 대한 UI 테스트를 실행합니다.

빌드는 0이나 1개의 아카이브를 생성해야 합니다. 아카이브 0을 생성하는 경우 기본적으로 테스트 단계가 전달됩니다. 빌드에서 두 개 이상의 아카이브를 만드는 경우 선택한 아카이브가 결정적이지 않습니다.

## UI 테스트 작성 {#writing-ui-tests}

이 섹션에서는 UI 테스트가 포함된 Docker 이미지가 따라야 하는 규칙을 설명합니다. Docker 이미지는 이전 섹션에 설명된 Docker 빌드 컨텍스트에서 빌드됩니다.

### 환경 변수 {#environment-variables}

다음 환경 변수가 런타임에 Docker 이미지에 전달됩니다.

| 변수 | 예 | 설명 |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Selenium 서버의 URL |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | Selenium 서버에서 사용하는 브라우저 구현 |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | AEM 작성자 인스턴스의 URL |
| `AEM_AUTHOR_USERNAME` | `admin` | AEM 작성자 인스턴스에 로그인할 사용자 이름 |
| `AEM_AUTHOR_PASSWORD` | `admin` | AEM 작성자 인스턴스에 로그인할 암호입니다. |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | AEM 게시 인스턴스의 URL |
| `AEM_PUBLISH_USERNAME` | `admin` | AEM 게시 인스턴스에 로그인할 사용자 이름 |
| `AEM_PUBLISH_PASSWORD` | `admin` | AEM 게시 인스턴스에 로그인할 암호입니다. |
| `REPORTS_PATH` | `/usr/src/app/reports` | 테스트 결과의 XML 보고서를 저장해야 하는 경로입니다 |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | Selenium에서 액세스할 수 있도록 하기 위해 파일을 업로드해야 하는 URL입니다 |

### Selenium이 준비되기를 기다리는 중 {#waiting-for-selenium}

테스트가 시작되기 전에 Selenium 서버가 작동 중인지 확인하는 것은 Docker 이미지의 책임입니다. Selenium 서비스를 기다리는 절차는 두 단계로 구성됩니다.

1. 에서 Selenium 서비스의 URL을 읽습니다. `SELENIUM_BASE_URL` 환경 변수 입니다.
2. 정기적으로 폴링하여 [상태 끝점](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) 는 Selenium API에 의해 노출됩니다.

Selenium의 상태 끝점이 긍정적인 응답으로 응답하면 테스트가 마지막으로 시작될 수 있습니다.

### 테스트 보고서 생성 {#generate-test-reports}

Docker 이미지는 JUnit XML 형식으로 테스트 보고서를 생성하고 환경 변수에 지정된 경로에 저장해야 합니다 `REPORTS_PATH`. JUnit XML 형식은 테스트 결과를 보고하기 위한 광범위한 형식입니다. Docker 이미지가 Java 및 Maven을 사용하는 경우 [Maven Suresfire 플러그인](https://maven.apache.org/surefire/maven-surefire-plugin/) 그리고 [Maven Failsafe 플러그인](https://maven.apache.org/surefire/maven-failsafe-plugin/). 다른 프로그래밍 언어나 테스트 러너와 함께 Docker 이미지가 구현된 경우 선택한 도구에 대한 설명서를 확인하여 JUnit XML 보고서를 생성하는 방법을 알아보십시오.

### 파일 업로드 {#upload-files}

테스트는 테스트 중인 응용 프로그램에 파일을 업로드해야 하는 경우가 있습니다. 테스트를 기준으로 하여 Selenium의 배포를 유연하게 유지 관리하기 위해 자산을 Selenium에 직접 업로드할 수 없습니다. 대신 파일을 업로드하는 것은 몇 가지 중간 단계를 거칩니다.

1. 에서 지정한 URL에 파일을 업로드합니다. `UPLOAD_URL` 환경 변수 입니다. 다중 부분 양식이 있는 하나의 POST 요청에서 업로드를 수행해야 합니다. 다중 부분 양식에는 단일 파일 필드가 있어야 합니다. 이것은 다음과 같습니다 `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. 이러한 HTTP 요청을 수행하는 방법을 알아보려면 Docker 이미지에 사용되는 프로그래밍 언어의 설명서 및 라이브러리를 참조하십시오.
2. 업로드가 성공적으로 수행되면 요청은 를 반환합니다. `200 OK` 유형 응답 `text/plain`. 응답의 컨텐츠는 불투명한 파일 핸들입니다. 이 핸들은 `<input>` 응용 프로그램에서 파일 업로드를 테스트할 요소입니다.
