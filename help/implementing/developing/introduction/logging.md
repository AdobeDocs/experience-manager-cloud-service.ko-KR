---
title: 로깅
description: 중앙 로깅 서비스에 대한 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 1%

---


# 로깅{#logging}

Cloud Service로서 AEM은 고객이 고객층의 고유한 경험을 만들기 위해 사용자 지정 코드를 포함할 수 있는 플랫폼입니다. 이러한 점을 염두에 두고, 로깅은 클라우드 환경에서 사용자 지정 코드를 디버깅하고 특히 로컬 개발 환경을 위해 중요한 기능입니다.


<!-- ## Global Logging {#global-logging}

[Apache Sling Logging Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) is used to configure the root logger. This defines the global settings for logging in AEM as a Cloud Service:

* the logging level
* the location of the central log file
* the number of versions to be kept
* version rotation; either maximum size or a time interval
* the format to be used when writing the log messages
-->

## Cloud Service 로깅으로 AEM {#aem-as-a-cloud-service-logging}

AEM을 Cloud Service으로 사용하면 다음을 구성할 수 있습니다.

* 중앙 로깅 서비스를 위한 전역 매개 변수
* 요청 데이터 로깅; 요청 정보를 위한 전문 로깅 구성
* 개별 서비스에 대한 특정 설정

로컬 개발의 경우 로그 항목은 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다.

>[!NOTE]
>
>Cloud Service으로 AEM에 로그인하는 것은 Sling 원칙을 기반으로 합니다. 자세한 [내용은 Sling](https://sling.apache.org/site/logging.html) Logging을 참조하십시오.

## Cloud Service Java 로깅으로 AEM {#aem-as-a-cloud-service-java-logging}

### 표준 로거 및 작가 {#standard-loggers-and-writers}

>[!IMPORTANT]
>
>표준 구성은 대부분의 설치에 적합하지만 필요할 경우 사용자 정의할 수 있습니다. 그러나 표준 로깅 구성을 사용자 정의해야 하는 경우 `dev` 환경에서만 수행해야 합니다.

특정 로거 및 작가는 Cloud Service 설치로서 표준 AEM에 포함됩니다.

첫 번째는 로그 `request` 와 로그를 모두 제어하는 특수 `access` 경우입니다.

* 로거:

   * Apache Sling 사용자 정의 가능한 요청 데이터 로거

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * 요청 컨텐트에 대한 메시지를 다음으로 `request.log`작성합니다.

* 링크:

   * Apache Sling 요청 로거

      (org.apache.sling.engine.impl.log.RequestLogger)

   * 또는 `request.log` 에 메시지를 씁니다 `access.log`.

다른 쌍은 표준 구성을 따릅니다.

* 로거:

   * Apache Sling 로깅 로거 구성

      (org.apache.sling.commons.log.LogManager.factory.config)

   * 메시지를 `Information` 씁니다 `logs/error.log`.

* 작성기에 대한 링크:

   * Apache Sling Logging Writer 구성

      (org.apache.sling.commons.log.LogManager.factory.writer)

* 로거:

   * Apache Sling 로깅 로거 구성(org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * 서비스에 대한 메시지 `Warning` 를 씁니다 `../logs/error.log` `org.apache.pdfbox`.

* 특정 작성기에 링크하지 않으므로 기본 구성이 있는 암시적 작성기를 만들고 사용합니다.

**Cloud Service HTTP 요청 로깅으로 AEM**

AEM WCM 및 보관소에 대한 모든 액세스 요청은 여기에 등록되어 있습니다.

출력 예:

**Cloud Service HTTP 요청/응답 액세스 로깅의 AEM**

각 액세스 요청은 응답과 함께 여기에 등록됩니다.

출력 예:

**Apache 웹 서버/Dispatcher 로깅**

Dispatcher 문제 디버깅에 사용되는 로그입니다. 자세한 내용은 Apache [및 Dispatcher 구성 디버깅을 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/).

<!-- Besides the three types of logs present on an AEM as a Cloud Service instance (`request`, `access` and `error` logs) there is another dispatcher/overview.html#debugging-apache-and-dispatcher-configuration.

leftover text from the last breakaway chunk (re dispatcher) -->

모범 사례의 경우 현재 AEM에 Cloud Service Maven 원형으로서 존재하는 구성에 정렬하는 것이 좋습니다. 이러한 설정은 특정 환경 유형에 대해 서로 다른 로그 설정 및 수준을 설정합니다.

* `local dev` 및 `dev` 환경의 경우 로거 **를 DEBUG** 수준으로 `error.log`
* for `stage`the logger to **WARN** level to the `error.log`
* for `prod`set logger to **ERROR** level to the `error.log`

아래 각 구성에 대한 예를 참조하십시오.

* `dev` 환경:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="debug"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```


* `stage` 환경:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="warn"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```

* `prod` 환경:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="error"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```

### 로거 및 개인 서비스 작가 {#loggers-and-writers-for-individual-services}

전역 로깅 설정 외에도 AEM을 Cloud Service으로 사용하면 개별 서비스에 대한 특정 설정을 구성할 수 있습니다.

* 특정 로깅 수준
* 로거(로그 메시지를 제공하는 OSGi 서비스)

단일 서비스의 로그 메시지를 별도의 파일로 보낼 수 있습니다. 개발 또는 테스트 중에 특히 유용할 수 있습니다. 예를 들어 특정 서비스에 대해 로그 수준이 향상되어야 할 경우

AEM은 Cloud Service으로 다음을 사용하여 로그 메시지를 파일에 기록합니다.

1. OSGi 서비스 **** (로거)는 로그 메시지를 기록합니다.
1. Logging **Logger는 이 메시지를 가져와서** 사용자의 사양에 따라 포맷합니다.
1. 로깅 **기록기는** 이러한 모든 메시지를 사용자가 정의한 물리적 파일에 기록합니다.

이러한 요소는 해당 요소에 대해 다음 매개 변수로 연결됩니다.

* **로거(로깅 로거)**

   메시지를 생성하는 서비스를 정의합니다.

<!-- * **Log File (Logging Logger)**

  Define the physical file for storing the log messages.

  This is used to link a Logging Logger with a Logging Writer. The value must be identical to the same parameter in the Logging Writer configuration for the connection to be made.

* **Log File (Logging Writer)**

  Define the physical file that the log messages will be written to.

  This must be identical to the same parameter in the Logging Writer configuration, or the match will not be made. If there is no match then an implicit Writer will be created with default configuration (daily log rotation).
-->

### 로그 수준 설정 {#setting-the-log-level}

클라우드 환경의 로그 수준을 변경하려면 Sling Logging OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지는 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 빠르게 변경하는 메커니즘이 있을 수 있습니다.

>[!NOTE]
>
>아래에 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 구성 변경 사항을 만든 다음 Cloud Service 인스턴스로 AEM에 푸시해야 합니다. 이 방법에 대한 자세한 내용은 Cloud Service [로 AEM에 배포를 참조하십시오](/help/implementing/deploying/overview.md).

**디버그 로그 수준 활성화**

>[!WARNING]
>
>DEBUG 로그 수준을 전역적으로 활성화하면 많은 양의 정보가 생성되므로 간을 이동하기 어렵습니다. 디버깅이 필요한 서비스에만 사용하도록 설정하는 것이 좋습니다. 자세한 내용은 로거 [및 개인 서비스 작성자를 참조하십시오](logging.md#loggers-and-writers-for-individual-services).

기본 로그 수준은 INFO입니다. 즉, DEBUG 메시지는 기록되지 않습니다.
디버그 로그 수준을 활성화하려면

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

property to debug. 로그를 많은 로그를 생성하므로 로그를 필요 이상으로 길게 DEBUG 로그 수준으로 남겨두지 마십시오.
디버그 파일의 한 줄은 대개 DEBUG로 시작하고 로그 수준, 설치 프로그램 작업 및 로그 메시지를 제공합니다. 예:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패했으며 설치 관리자를 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX의 일부가 올바르게 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX가 제대로 작동하지 않거나 작동하지 않을 수 있습니다. |
| 3 | 정보 | 그 행동은 성공했다. |

### 로거 및 작가 제작 {#creating-your-own-loggers-and-writers}

로거/작성기 쌍을 정의할 수 있습니다.

1. Factory Configuration Apache Sling Logging [Logger 구성의 새 인스턴스를 만듭니다](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. 로거를 지정합니다.

<!-- 1. Create a new instance of the Factory Configuration [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

    1. Specify the Log File - this must match that specified for the Logger.
    1. Configure the other parameters as required. -->

### 로깅 구성 {#configure-logging}

>[!NOTE]
>
>Adobe Experience Manager을 사용하는 경우 이러한 서비스에 대한 구성 설정을 관리하는 방법이 몇 가지 있습니다.

특정 상황에서는 다른 로그 수준의 사용자 지정 로그를 만들 수 있습니다. 다음과 같은 방법으로 저장소에서 이 작업을 수행할 수 있습니다.

1. 아직 존재하지 않는 경우 프로젝트에 사용할 새 구성 폴더( `sling:Folder`)를 만듭니다 `/apps/<*project-name*>/config`.
1. 아래에서 새 Apache `/apps/<*project-name*>/config`Sling Logging Logger 구성 노드를 만듭니다.

   * 이름: `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>` (로거인 경우)

      여기서 `<*identifier*>` 는 인스턴스를 식별하기 위해 입력한 자유 텍스트로 대체됩니다(이 정보를 생략할 수 없음).

      예, `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * 유형: `sling:OsgiConfig`
   >[!NOTE]
   >
   >기술적인 요건은 아니지만, `<*identifier*>` 고유한 것을 만드는 것이 좋다.

<!-- 1. Set the following properties on this node:

    * Name: `org.apache.sling.commons.log.file`

      Type: String

      Value: specify the Log File; for example, `logs/myLogFile.log`

    * Name: `org.apache.sling.commons.log.names`

      Type: String[] (String + Multi)

      Value: specify the OSGi services for which the Logger is to log messages; for example, all of the following:

        * `org.apache.sling`
        * `org.apache.felix`
        * `com.day`

    * Name: `org.apache.sling.commons.log.level`

      Type: String

      Value: specify the log level required ( `debug`, `info`, `warn` or `error`); for example `debug`

    * Configure the other parameters as required:

        * Name: `org.apache.sling.commons.log.pattern`

          Type: `String`

          Value: specify the pattern of the log message as required; for example,

          `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`

   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` supports up to six arguments.

   >
   >
   >{0} The timestamp of type `java.util.Date`
   >{1} the log marker
   >{2} the name of the current thread
   >{3} the name of the logger
   >{4} the log level
   >{5} the log message

   >
   >
   >If the log call includes a `Throwable` the stacktrace is appended to the message.

   >[!CAUTION]
   >
   >org.apache.sling.commons.log.names must have a value.

   >[!NOTE]
   >
   >Log writer paths are relative to the `crx-quickstart` location.
   >
   >
   >Therefore, a log file specified as:
   >
   >
   >`logs/thelog.log`

   >
   >
   >writes to:
   >
   >
   >`` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log`.
   >
   >
   >And a log file specified as:
   >
   >
   >`../logs/thelog.log`

   >
   >
   >writes to a directory:
   >
   >
   >` <*cq-installation-dir*>/logs/`
   >``(i.e. next to ` `<*cq-installation-dir*>/`crx-quickstart/`)
 -->

<!-- open question: see if we need to leave the above warning note in place, but adjust it so that it doesn't mention filenames -->

<!-- 1. This step is only necessary when a new Writer is required (i.e. with a configuration that is different to the default Writer).

   >[!CAUTION]
   >
   >A new Logging Writer Configuration is only required when the existing default is not suitable.

   >
   >
   >If no explicit Writer is configured the system will automatically generate an implicit Writer based on the default.

   Under `/apps/<*project-name*>/config`, create a node for the new `Apache Sling Logging Writer` Configuration:

    * Name: `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` (as this is a Writer)

      As with the Logger, `<*identifier*>` is replaced by free text that you (must) enter to identify the instance (you cannot omit this information). For example, `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

    * Type: `sling:OsgiConfig`

   >[!NOTE]
   >
   >Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

   Set the following properties on this node:

    * Name: `org.apache.sling.commons.log.file`

      Type: `String`

      Value: specify the Log File so that it matches the file specified in the Logger;

      for this example, `../logs/myLogFile.log`.

    * Configure the other parameters as required:

        * Name: `org.apache.sling.commons.log.file.number`

          Type: `Long`

          Value: specify the number of log files you want kept; for example, `5`

        * Name: `org.apache.sling.commons.log.file.size`

          Type: `String`

          Value: specify as required to control file rotation by size/date; for example, `'.'yyyy-MM-dd`

   >[!NOTE]
   >
   >`org.apache.sling.commons.log.file.size` controls the rotation of the log file by setting either:
   >
   >* a maximum file size
   >* a time/date schedule
   >
   >to indicate when a new file will be created (and the existing file renamed according to the name pattern).
   >
   >* A size limit can be specified with a number. If no size indicator is given, then this is taken as the number of bytes, or you can add one of the size indicators - `KB`, `MB`, or `GB` (case is ignored).
   >* A time/date schedule can be specified as a `java.util.SimpleDateFormat` pattern. This defines the time period after which the file will be rotated; also the suffix appended to the rotated file (for identification).
   >
   >The default is '.'yyyy-MM-dd (for daily log rotation).
   >
   >So for example, at midnight of January 20th 2010 (or when the first log message after this occurs to be precise), ../logs/error.log will be renamed to ../logs/error.log.2010-01-20. Logging for the 21st of January will be output to (a new and empty) ../logs/error.log until it is rolled over at the next change of day.
   >
   >      | `'.'yyyy-MM` |Rotation at the beginning of each month |
   >      |---|---|
   >      | `'.'yyyy-ww` |Rotation at the first day of each week (depends on the locale). |
   >      | `'.'yyyy-MM-dd` |Rotation at midnight each day. |
   >      | `'.'yyyy-MM-dd-a` |Rotation at midnight and midday of each day. |
   >      | `'.'yyyy-MM-dd-HH` |Rotation at the top of every hour. |
   >      | `'.'yyyy-MM-dd-HH-mm` |Rotation at the beginning of every minute. |
   >
   >      Note: When specifying a time/date:
   >      1. You should "escape" literal text within a pair of single quotes (' ');
   >      this is to avoid certain characters being interpreted as pattern letters.
   >      1. Only use characters allowed for a valid file name anywhere in the option.

1. Read your new log file with your chosen tool.

   The log file created by this example will be `../crx-quickstart/logs/myLogFile.log`. -->

또한 Felix Console은 Sling Log 지원에 대한 정보를 제공합니다. `../system/console/slinglog`for example `https://localhost:4502/system/console/slinglog`.draf

## 로그 액세스 및 관리 {#manage-logs}

로그에 액세스하고 관리하는 방법에 대한 자세한 내용은 [Cloud Manager 설명서를 참조하십시오](/help/implementing/cloud-manager/manage-logs.md).