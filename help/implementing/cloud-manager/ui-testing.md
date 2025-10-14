---
title: UI 테스트
description: 사용자 정의 UI 테스트는 사용자 정의 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 498a58c89910f41e6b86c5429629ec9282028987
workflow-type: tm+mt
source-wordcount: '2601'
ht-degree: 56%

---


# UI 테스트 {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI 테스트"
>abstract="사용자 정의 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다. UI 테스트는 언어 및 프레임워크에서 다양한 선택을 허용하도록 도커 이미지에 패키징된 Selenium 기반 테스트입니다. Java 및 Maven, Node 및 WebDriver.io 또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술 등."

사용자 정의 UI 테스트는 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있는 선택적 기능입니다.

## 개요 {#custom-ui-testing}

AEM은 사용자 정의 애플리케이션에 대한 원활한 업데이트를 보장하기 위해 통합된 [Cloud Manager 품질 게이트](/help/implementing/cloud-manager/custom-code-quality-rules.md) 제품군을 제공합니다 특히 IT 테스트 게이트는 이미 AEM API를 사용한 사용자 정의 테스트의 만들기 및 자동화를 지원합니다.

UI 테스트는 언어 및 프레임워크(예: Cypress, Selenium, Java 및 Maven, JavaScript)에서 다양한 선택을 허용하도록 Docker 이미지에 패키징되어 있습니다. 또한 [AEM Project Archetype](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/developing/archetype/overview)을(를) 사용하여 UI 테스트 프로젝트를 쉽게 생성할 수 있습니다.

Adobe는 실시간 리로딩 및 자동 대기 기능을 제공하여 테스트 중 시간을 절약하고 생산성을 향상시키는 데 도움이 되는 Cypress의 사용을 권장합니다. 또한 Cypress는 간단하고 직관적인 구문을 제공하므로 테스트를 처음 사용하는 사용자도 쉽게 배우고 사용할 수 있습니다.

UI 테스트는 [**사용자 지정 UI 테스트**](/help/implementing/cloud-manager/deploy-code.md) 단계에서 품질 게이트로 실행됩니다. [프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)에서 필요하며 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)에서 선택 사항입니다. 회귀 및 새로운 기능을 포함한 모든 UI 테스트를 통해 오류를 감지 및 보고할 수 있습니다.

Java로 작성된 HTTP 테스트인 사용자 정의 기능 테스트와 달리 UI 테스트는 도커 이미지가 될 수 있습니다. 테스트는 [UI 테스트 빌드](#building-ui-tests) 섹션에 정의된 규칙을 따르는 한 모든 언어로 작성할 수 있습니다.

>[!TIP]
>
>[AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress)에 제공된 코드에 따라 UI 테스트에 Cypress를 사용하는 것이 좋습니다.
> 
>또한 Adobe는 WebdriverIO([AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) 참조)가 포함된 JavaScript 및 WebDriver([AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver) 참조)가 포함된 Java를 기반으로 하는 UI 테스트 모듈 예제를 제공합니다.

## UI 테스트 시작하기 {#get-started-ui-tests}

이 섹션에서는 Cloud Manager에서 실행할 UI 테스트를 설정하는 데 필요한 단계를 설명합니다.

1. 사용할 테스트 프레임워크를 결정합니다.

   * Cypress(기본값)의 경우 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress)의 샘플 코드를 사용하거나 Cloud Manager 저장소의 `ui.tests` 폴더에서 자동으로 생성된 샘플 코드를 사용합니다.

   * 플레이라이트의 경우 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright)의 샘플 코드를 사용하십시오.

   * Webdriver.IO의 경우 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio)의 샘플 코드를 사용합니다.

   * Selenium WebDriver의 경우 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)의 샘플 코드를 사용합니다.

   * 다른 프로그래밍 언어의 경우, 이 문서의 [UI 테스트 빌드](#building-ui-tests) 섹션을 참조하여 테스트 프로젝트를 설정합니다.

1. 이 문서의 [고객 옵트인](#customer-opt-in) 섹션에 따라 UI 테스트가 활성화되어 있는지 확인합니다.

1. 자신의 테스트 케이스를 개발하고 [테스트를 로컬로 실행](#run-ui-tests-locally)하십시오.

1. Cloud Manager 저장소에 코드를 커밋하고 Cloud Manager 파이프라인을 실행합니다.

## UI 테스트 빌드 {#building-ui-tests}

Maven 프로젝트는 Docker 빌드 컨텍스트를 생성합니다. 이 Docker 빌드 컨텍스트는 UI 테스트가 포함된 Docker 이미지(Cloud Manager에서 이를 사용해 실제 UI 테스트가 포함된 Docker 이미지를 생성)를 만드는 방법을 설명합니다.

이 섹션에서는 UI 테스트 프로젝트를 저장소에 추가하는 데 필요한 단계를 설명합니다.

>[!TIP]
>
>[AEM Project Archetype](https://github.com/adobe/aem-project-archetype)은 프로그래밍 언어에 대한 특별한 요구 사항이 없는 사용자를 위해 다음 설명을 준수하는 UI 테스트 프로젝트를 생성할 수 있습니다.

### Docker 빌드 컨텍스트 생성 {#generate-docker-build-context}

Docker 빌드 컨텍스트를 생성하려면 다음 작업을 수행하는 Maven 모듈이 필요합니다.

* 테스트로 Docker 이미지를 빌드하는 데 필요한 `Dockerfile` 및 기타 모든 파일을 포함하는 아카이브를 생성합니다.
* 아카이브에 `ui-test-docker-context` 분류자로 태그를 지정합니다.

가장 간단한 방법은 도커 빌드 컨텍스트 아카이브를 만들고 여기에 올바른 분류자를 할당하도록 [Maven 어셈블리 플러그인](https://maven.apache.org/plugins/maven-assembly-plugin/)을 구성하는 것입니다.

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

어셈블리 설명자는 플러그인에 `.tar.gz` 유형의 아카이브를 생성하고 `ui-test-docker-context` 분류자를 할당하도록 지시합니다. 또한 다음을 포함하여 아카이브에 포함해야 하는 파일을 나열합니다.

* Docker 이미지 빌드에 필수인 `Dockerfile`
* 아래에 목적이 설명되어 있는 `wait-for-grid.sh` 스크립트
* `test-module` 폴더의 Node.js 프로젝트에서 구현한 실제 UI 테스트

어셈블리 설명자는 UI 테스트를 로컬에서 실행하는 동안 생성될 수 있는 일부 파일도 제외합니다. 이를 통해 아카이브 크기는 작아지고 빌드 속도는 빨라집니다.

Cloud Manager은 배포 파이프라인 동안 도커 빌드 컨텍스트 아카이브를 자동으로 선택하고 테스트 이미지를 빌드합니다. 결국 Cloud Manager은 도커 이미지를 실행하여 애플리케이션에 대한 UI 테스트를 실행합니다.

빌드는 0개 또는 1개의 아카이브를 생성해야 합니다. 아카이브가 생성되지 않으면 테스트 단계가 기본적으로 통과합니다. 빌드가 둘 이상의 아카이브를 생성하는 경우 선택되는 아카이브는 비결정적입니다.

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
>프로젝트에 이 줄이 포함되지 않은 경우 UI 테스트를 선택하도록 파일을 편집합니다.
>
>파일에 편집하지 말라는 내용의 줄이 포함될 수 있습니다. 그 이유는 옵트인 UI 테스트가 도입되기 전에 프로젝트에 도입되고 있으며 클라이언트가 파일을 편집할 의도가 없었기 때문입니다. 권고 사항을 무시해도 됩니다.

Adobe에서 제공하는 샘플을 사용하는 경우 다음을 참조하십시오.

* [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)으로 생성된 JavaScript 기반 `ui.tests` 폴더의 경우 아래 명령을 실행하여 필요한 구성을 추가할 수 있습니다.

  ```shell
  echo "ui-tests.version=1" > testing.properties
  
  if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
    awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
  fi
  ```

* Adobe에서 제공한 Cypress 및 Java Selenium 테스트 샘플에는 이미 옵트인 플래그가 설정되어 있습니다.

## UI 테스트 작성 {#writing-ui-tests}

이 섹션에서는 UI 테스트가 포함된 Docker 이미지가 따라야 하는 규칙에 대해 설명합니다. Docker 이미지는 이전 섹션에서 설명한 Docker 빌드 컨텍스트에서 빌드됩니다.

### 환경 변수 {#environment-variables}

다음 환경 변수는 프레임워크에 따라 런타임 시 Docker 이미지로 전달됩니다.

>[!NOTE]
>
> 이러한 값은 파이프라인 실행 중에 자동으로 설정되므로 파이프라인 변수로 수동으로 설정할 필요가 없습니다.

| 변수 | 예 | 설명 | 테스트 프레임워크 |
|----------------------------|----------------------------------|----------------------------------------------------------------------------------------------------|---------------------|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | Selenium 서버의 URL | Selenium 전용 |
| `SELENIUM_BROWSER` | `chrome` | Selenium 서버에서 사용하는 브라우저 구현 | Selenium 전용 |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | AEM 작성자 인스턴스의 URL | 모두 |
| `AEM_AUTHOR_USERNAME` | `admin` | AEM 작성자 인스턴스에 로그인할 사용자 이름 | 모두 |
| `AEM_AUTHOR_PASSWORD` | `admin` | AEM 작성자 인스턴스에 로그인하기 위한 암호 | 모두 |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | AEM 게시 인스턴스의 URL | 모두 * |
| `AEM_PUBLISH_USERNAME` | `admin` | AEM 게시 인스턴스에 로그인할 사용자 이름 | 모두 * |
| `AEM_PUBLISH_PASSWORD` | `admin` | AEM 게시 인스턴스에 로그인하기 위한 암호 | 모두 * |
| `REPORTS_PATH` | `/usr/src/app/reports` | 테스트 결과의 XML 보고서를 저장해야 하는 경로 | 모두 |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | 테스트 프레임워크에서 액세스할 수 있도록 파일을 업로드해야 하는 URL | 모두 |
| `PROXY_HOST` | `proxy-host` | 테스트 프레임워크에서 사용할 내부 HTTP 프록시의 호스트 이름 | Selenium을 제외한 모든 항목 |
| `PROXY_HTTPS_PORT` | `8071` | HTTPS 연결을 위한 프록시 서버 수신 포트(비어 있을 수 있음) | Selenium을 제외한 모든 항목 |
| `PROXY_HTTP_PORT` | `8070` | HTTP 연결을 위한 프록시 서버 수신 포트(비어 있을 수 있음) | Selenium을 제외한 모든 항목 |
| `PROXY_CA_PATH` | `/path/to/root_ca.pem` | 테스트 프레임워크에서 사용할 CA 인증서 경로 | Selenium을 제외한 모든 항목 |
| `PROXY_OBSERVABILITY_PORT` | `8081` | 프록시 서버의 HTTP `healthcheck` 포트 | Selenium을 제외한 모든 항목 |
| `PROXY_RETRY_ATTEMPTS` | `12` | 프록시 서버 준비 대기 중 권장 재시도 횟수 | Selenium을 제외한 모든 항목 |
| `PROXY_RETRY_DELAY` | `5` | 프록시 서버 준비 대기 중 재시도 사이의 제안된 지연 시간 | Selenium을 제외한 모든 항목 |

`* these values will be empty if there is no publish instance`

Adobe 테스트 샘플은 구성 매개변수에 액세스하기 위한 도우미 기능을 제공합니다.

Cypress: 표준 기능 `Cypress.env('VARIABLE_NAME')` 사용
<!-- BOTH URLs are 404 JavaScript: See the [`lib/config.js`](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests.wdio/test-module/lib/config.js) module
* Java: See the [`Config`](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) class -->

### 테스트 보고서 생성 {#generate-test-reports}

Docker 이미지는 JUnit XML 형식으로 테스트 보고서를 생성하고 환경 변수 `REPORTS_PATH`에 지정된 경로에 저장해야 합니다. JUnit XML 형식은 테스트 결과를 보고하는 데 널리 사용되는 형식입니다. Docker 이미지가 Java 및 Maven을 사용하는 경우 [Maven Surefire 플러그인](https://maven.apache.org/surefire/maven-surefire-plugin/) 및 [Maven Failsafe 플러그인](https://maven.apache.org/surefire/maven-failsafe-plugin/)과 같은 표준 테스트 모듈은 즉시 이러한 보고서를 생성할 수 있습니다

Docker 이미지가 다른 프로그래밍 언어 또는 테스트 실행자로 구현된 경우 선택한 도구에 대한 설명서에서 JUnit XML 보고서를 생성하는 방법을 확인하십시오.

>[!NOTE]
>
>UI 테스트 단계의 결과는 테스트 보고서만을 기반으로 평가됩니다. 테스트 실행에 맞게 보고서를 생성했는지 확인하십시오.
>
>STDERR에 오류를 로깅하거나 0이 아닌 종료 코드를 반환하는 대신 어설션을 사용하십시오. 이렇게 하지 않으면 배포 파이프라인이 정상적으로 진행될 수 있습니다.
>
>테스트 실행 중에 HTTP 프록시가 사용된 경우 결과에 `request.log` 파일이 포함됩니다.

### 사전 요구 사항 {#prerequisites}

* Cloud Manager의 테스트는 기술 관리 사용자를 통해 실행됩니다.

>[!NOTE]
>
>로컬 시스템에서 기능 테스트를 실행하려면 동일한 동작이 가능하도록 관리자와 유사한 권한을 가진 사용자를 만드십시오.

* 기능 테스트 범위가 지정된 컨테이너화된 인프라는 다음 경계로 제한됩니다.

| 유형 | 값 | 설명 |
|----------------------|-------|-----------------------------------------------------------------------|
| CPU | 2.0 | 테스트 실행당 예약된 CPU 시간입니다. |
| 메모리 | 1Gi | 테스트에 할당된 메모리 양입니다. 값은 GB입니다. |
| 시간 초과 | 30m | 테스트가 실행되는 시간입니다. |
| 권장 기간 | 15m | Adobe은 테스트를 이 시간 제한 미만으로 유지하는 것을 권장합니다. |

>[!NOTE]
>
> 추가 리소스가 필요한 경우 고객 지원 사례를 만들고 사용 사례를 설명합니다. Adobe은 요청을 검토하고 적절한 지원을 제공합니다.

## Selenium 관련 세부 정보

>[!NOTE]
>
>이 섹션은 Selenium이 테스트 인프라로 선택된 경우에만 적용됩니다.

### Selenium이 준비될 때까지 대기 {#waiting-for-selenium}

테스트가 시작되기 전에 Selenium 서버가 실행 중인지 확인하는 것은 Docker 이미지의 책임입니다. Selenium 서비스 대기는 2단계 프로세스입니다.

1. `SELENIUM_BASE_URL` 환경 변수에서 Selenium 서비스의 URL을 읽습니다.
1. Selenium API에 의해 노출된 [상태 끝점](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready)에 정기적으로 폴링합니다.

Selenium의 상태 엔드포인트가 긍정 응답을 보내면 테스트를 시작할 수 있습니다.

Adobe의 UI 테스트 샘플은 `wait-for-grid.sh`을(를) 사용합니다. 도커 시작 시 실행되고 그리드가 준비된 후에만 테스트를 실행합니다.


### 스크린샷 및 비디오 캡처 {#capture-screenshots}

Docker 이미지는 추가 테스트 출력(예: 스크린샷 또는 비디오)을 생성하고 환경 변수 `REPORTS_PATH`에 의해 지정된 경로에 저장할 수 있습니다. `REPORTS_PATH` 아래에 있는 모든 파일은 테스트 결과 아카이브에 포함됩니다.

기본적으로 Adobe에서 제공하는 테스트 샘플은 실패한 테스트에 대한 스크린샷을 만듭니다.

도우미 기능을 사용하여 테스트를 통해 스크린샷을 만들 수 있습니다.

<!-- BOTH URLS ARE 404
* JavaScript: [takeScreenshot command](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [Commands](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java) -->

UI 테스트 실행 중에 테스트 결과 아카이브가 만들어지면 `Download Details`사용자 지정 UI 테스트&#x200B;[**단계** 아래의 ](/help/implementing/cloud-manager/deploy-code.md) 버튼을 클릭하여 Cloud Manager에서 다운로드할 수 있습니다.

### 파일 업로드 {#upload-files}

경우에 따라 테스트 중인 애플리케이션에 파일을 업로드해야 합니다. 테스트에 비해 Selenium을 유연하게 배치하기 위해 에셋을 Selenium에 직접 업로드할 수 없습니다. 대신 파일을 업로드하려면 다음 단계가 필요합니다.

1. `UPLOAD_URL` 환경 변수로 지정된 URL에서 파일을 업로드합니다.
   * 업로드는 다중 부분 양식으로 된 하나의 POST 요청으로 수행되어야 합니다.
   * 다중 부분 양식에는 단일 파일 필드가 있어야 합니다.
   * `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`과(와) 동일합니다.
   * 이러한 HTTP 요청을 수행하는 방법을 알아보려면 도커 이미지에 사용된 프로그래밍 언어의 문서 및 라이브러리를 참조하십시오.

   <!-- BOTH URLS ARE 404
   * The Adobe test samples provide helper functions for uploading files:
     * JavaScript: See the [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) command.
     * Java: See the [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java) class. -->

1. 업로드가 성공하면 요청은 `text/plain` 유형의 `200 OK` 응답을 반환합니다.
   * 응답의 내용은 불투명한 파일 핸들입니다.
   * `<input>` 요소의 파일 경로 대신 이 핸들을 사용하여 애플리케이션에서 파일 업로드를 테스트할 수 있습니다.

## Cypress 관련 세부 정보

>[!NOTE]
>
>이 섹션은 Cypress가 선택된 테스트 인프라인 경우에만 적용됩니다.

### HTTP 프록시 설정

도커 컨테이너의 진입점은 `PROXY_HOST` 환경 변수의 값을 확인해야 합니다.

이 값이 비어 있으면 추가 단계가 필요하지 않으며 HTTP 프록시를 사용하지 않고 테스트를 실행해야 합니다.

비어 있지 않으면 진입점 스크립트는 다음을 수행해야 합니다.

1. 다음 값을 사용하여 빌드된 `HTTP_PROXY` 환경 변수를 내보내어 UI 테스트 실행을 위한 HTTP 프록시 연결을 구성합니다.
   * `PROXY_HOST` 변수가 제공하는 프록시 호스트
   * `PROXY_HTTPS_PORT` 또는 `PROXY_HTTP_PORT` 변수가 제공하는 프록시 포트(값이 비어 있지 않은 변수가 사용됨)
2. HTTP 프록시에 연결할 때 사용할 CA 인증서를 설정합니다. 해당 위치는 `PROXY_CA_PATH` 변수에 의해 제공됩니다.
   * `NODE_EXTRA_CA_CERTS` 환경 변수를 내보냅니다.
3. HTTP 프록시가 준비될 때까지 기다립니다.
   * 준비 상태를 확인하기 위해 `PROXY_HOST`, `PROXY_OBSERVABILITY_PORT`, `PROXY_RETRY_ATTEMPTS` 및 `PROXY_RETRY_DELAY` 환경 변수를 사용할 수 있습니다.
   * cURL 요청을 사용하여 `Dockerfile`에 cURL을 설치했는지 확인할 수 있습니다.

예제 구현은 [GitHub](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/run.sh)에 있는 Cypress 샘플 테스트 모듈의 진입점에서 찾을 수 있습니다.

## 극작가별 세부 정보

>[!NOTE]
>
> 이 섹션은 `Playwright`이(가) 선택한 테스트 인프라인 경우에만 적용됩니다.

### HTTP 프록시 설정

>[!NOTE]
>
> 제시된 예에서 Adobe은 Chrome이 프로젝트 브라우저로 사용 중이라고 가정합니다.

비어 있지 않은 `PROXY_HOST` 환경 변수가 제공된 경우 Cypress와 마찬가지로 테스트에서 HTTP 프록시를 사용해야 합니다.

이 경우 다음과 같이 편집해야 합니다.

#### Dockerfile

cURL 및 `libnss3-tools`을(를) 설치합니다. `certutil.` 제공

```dockerfile
RUN apt -y update \
    && apt -y --no-install-recommends install curl libnss3-tools \
    && rm -rf /var/lib/apt/lists/*
```

#### 진입점 스크립트

`PROXY_HOST` 환경 변수가 제공된 경우 다음을 수행하는 bash 스크립트를 포함합니다.

1. `HTTP_PROXY` 및 `NODE_EXTRA_CA_CERTS`과(와) 같은 프록시 관련 변수 내보내기
2. `certutil`을(를) 사용하여 Chromium™용 프록시 CA 인증서를 설치합니다.
3. HTTP 프록시가 준비될 때까지(또는 실패 시 종료) 기다립니다.

예제 구현:

```bash
# setup proxy environment variables and CA certificate
if [ -n "${PROXY_HOST:-}" ]; then
  if [ -n "${PROXY_HTTPS_PORT:-}" ]; then
    export HTTP_PROXY="https://${PROXY_HOST}:${PROXY_HTTPS_PORT}"
  elif [ -n "${PROXY_HTTP_PORT:-}" ]; then
    export HTTP_PROXY="http://${PROXY_HOST}:${PROXY_HTTP_PORT}"
  fi
  if [ -n "${PROXY_CA_PATH:-}" ]; then
    echo "installing certificate"
    mkdir -p $HOME/.pki/nssdb
    certutil -d sql:$HOME/.pki/nssdb -A -t "CT,c,c" -n "EaaS Client Proxy Root" -i $PROXY_CA_PATH
    export NODE_EXTRA_CA_CERTS=${PROXY_CA_PATH}
  fi
  if [ -n "${PROXY_OBSERVABILITY_PORT:-}" ] && [ -n "${HTTP_PROXY:-}" ]; then
    echo "waiting for proxy"
    curl --silent  --retry ${PROXY_RETRY_ATTEMPTS:-3} --retry-connrefused --retry-delay ${PROXY_RETRY_DELAY:-10} \
      --proxy ${HTTP_PROXY} --proxy-cacert ${PROXY_CA_PATH:-""} \
      ${PROXY_HOST}:${PROXY_OBSERVABILITY_PORT}
    if [ $? -ne 0 ]; then
      echo "proxy is not ready"
      exit 1
    fi
  fi
fi
```

#### 극작가 구성

`playwright.config.js` 환경 변수가 설정된 경우 프록시를 사용하도록 극작가 구성(예: `HTTP_PROXY`에서)을 수정하십시오.

예제 구현:

```javascript
const proxyServer = process.env.HTTP_PROXY || ''
```

```javascript
// enable proxy if set
if (proxyServer !== '') {
 cfg.use.proxy = {
  server: proxyServer,
 }
}
```

>[!NOTE]
>
> 예제 구현은 [GitHub](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright)의 극작가 샘플 테스트 모듈에서 찾을 수 있습니다.


## 로컬에서 UI 테스트 실행 {#run-ui-tests-locally}

Cloud Manager 파이프라인에서 UI 테스트를 활성화하기 전에 Adobe에서는 [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)에 대해 로컬로 UI 테스트를 실행하는 것이 좋습니다. 또는 실제 AEM as a Cloud Service 인스턴스에 대해 를 실행합니다.

### Cypress 테스트 샘플 {#cypress-sample}

1. 셸을 열고 저장소의 `ui.tests/test-module` 폴더로 이동합니다.

1. Cypress 및 기타 사전 요구 사항 설치

   ```shell
   npm install
   ```

1. 테스트 실행에 필요한 환경 변수 설정

   ```shell
   export AEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_AUTHOR_USERNAME=<user>
   export AEM_AUTHOR_PASSWORD=<password>
   export AEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_PUBLISH_USERNAME=<user>
   export AEM_PUBLISH_PASSWORD=<password>
   export REPORTS_PATH=target/
   ```

1. 다음 명령 중 하나로 테스트 실행

   ```shell
   npm test              # Using default Cypress browser
   npm run test-chrome   # Using Google Chrome browser
   npm run test-firefox  # Using Firefox browser
   ```

>[!NOTE]
>
>로그 파일은 저장소의 `target/` 폴더에 저장됩니다.
>
>자세한 내용은 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/README.md)를 참조하십시오.

### JavaScript WebdriverIO 테스트 샘플 {#javascript-sample}

1. 셸을 열고 저장소의 `ui.tests` 폴더로 이동합니다.

1. 다음 명령을 실행하여 Maven을 사용하여 테스트를 시작합니다.

   ```shell
   mvn verify -Pui-tests-local-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>* 이 명령은 독립형 Selenium 인스턴스를 시작하고 그에 대한 테스트를 실행합니다.
>* 로그 파일은 저장소의 `target/reports` 폴더에 저장됩니다.
>* 테스트에서 테스트를 위해 ChromeDriver의 최신 릴리스를 자동으로 다운로드하므로 최신 크롬 버전이 실행 중인지 확인해야 합니다.
>
>자세한 내용은 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio)를 참조하십시오.

### 극작가 테스트 샘플 {#playwright-sample}

1. 셸을 열고 저장소의 `ui.tests` 폴더로 이동합니다.

1. Maven을 사용하여 도커 이미지를 작성하려면 아래 명령을 실행하십시오.

   ```shell
   mvn clean package -Pui-tests-docker-build
   ```

1. 아래 명령을 실행하여 Maven을 사용해 테스트를 시작합니다.

   ```shell
   mvn verify -Pui-tests-docker-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>로그 파일은 저장소의 `target/` 폴더에 저장됩니다.
>
>자세한 내용은 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright)를 참조하십시오.


### Java Selenium WebDriver 테스트 샘플 {#java-sample}

1. 셸을 열고 저장소의 `ui.tests/test-module` 폴더로 이동합니다.

1. 아래 명령을 실행하여 Maven을 사용해 테스트를 시작합니다.

   ```shell
   # Start selenium docker image
   # we mount /tmp/shared as a shared volume that will be used between selenium and the test module for uploads
   docker run -d -p 4444:4444 -v /tmp/shared:/tmp/shared selenium/standalone-chromium:latest
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:4444
   ```

>[!NOTE]
>
>로그 파일은 저장소의 `target/reports` 폴더에 저장됩니다.
>
>자세한 내용은 [AEM 테스트 샘플 저장소](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md)를 참조하십시오.
