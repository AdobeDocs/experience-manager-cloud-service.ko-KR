---
title: 로깅
description: 중앙 로깅 서비스에 대한 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 95511543b3393d422e2cfa23f9af246365d3a993

---


# 로깅{#logging}

클라우드 서비스로서 AEM에서는 다음을 구성할 수 있습니다.

* 중앙 로깅 서비스를 위한 전역 매개 변수
* 요청 데이터 로깅;요청 정보를 위한 전문 로깅 구성
* 개별 서비스에 대한 특정 설정

로컬 개발의 경우 로그 항목은 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다.

>[!NOTE]
>
>클라우드 서비스로 AEM에 로그인하는 것은 Sling 원칙을 기반으로 합니다. 자세한 [내용은](https://sling.apache.org/site/logging.html) Sling 로깅을 참조하십시오.

<!-- ## Global Logging {#global-logging}

[Apache Sling Logging Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) is used to configure the root logger. This defines the global settings for logging in AEM as a Cloud Service:

* the logging level
* the location of the central log file
* the number of versions to be kept
* version rotation; either maximum size or a time interval
* the format to be used when writing the log messages
-->

## 로거 및 개인 서비스 작가 {#loggers-and-writers-for-individual-services}

글로벌 로깅 설정 외에도 AEM을 클라우드 서비스로 사용하면 개별 서비스에 대한 특정 설정을 구성할 수 있습니다.

* 특정 로깅 수준
* 로거(로그 메시지를 제공하는 OSGi 서비스)

따라서 단일 서비스의 로그 메시지를 별도의 파일로 보낼 수 있습니다. 개발 또는 테스트 중에 특히 유용할 수 있습니다.예를 들어, 특정 서비스에 대해 로그 수준이 향상되어야 하는 경우

클라우드 서비스로 AEM에서는 다음을 사용하여 로그 메시지를 파일에 기록합니다.

1. OSGi **서비스** (로거)는 로그 메시지를 기록합니다.
1. Logging **Logger** 는 이 메시지를 가져와서 사양에 따라 형식을 지정합니다.
1. 로깅 **작성기는** 이러한 모든 메시지를 사용자가 정의한 실제 파일에 기록합니다.

이러한 요소는 적절한 요소에 대해 다음 매개 변수로 연결됩니다.

* **로거(로깅 로거)**

   메시지를 생성하는 서비스를 정의합니다.

<!-- * **Log File (Logging Logger)**

  Define the physical file for storing the log messages.

  This is used to link a Logging Logger with a Logging Writer. The value must be identical to the same parameter in the Logging Writer configuration for the connection to be made.

* **Log File (Logging Writer)**

  Define the physical file that the log messages will be written to.

  This must be identical to the same parameter in the Logging Writer configuration, or the match will not be made. If there is no match then an implicit Writer will be created with default configuration (daily log rotation).
-->

### Standard Logger 및 Writer {#standard-loggers-and-writers}

> [!IMPORTANT]
> 이러한 구성 요소는 필요한 경우 사용자 정의할 수 있지만, 표준 구성은 대부분의 설치에 적합합니다. 그러나 표준 로깅 구성을 사용자 정의해야 하는 경우 `dev` 환경에서만 수행해야 합니다.

특정 로거 및 작성기는 클라우드 서비스 설치로 표준 AEM에 포함됩니다.

첫 번째는 `request` 로그와 `access` 로그를 모두 제어하는 특별한 경우입니다.

* 로거:

   * Apache Sling 사용자 정의 가능한 요청 데이터 로거

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * 요청 컨텐츠에 대한 메시지를 `request.log`작성합니다.

* 링크 대상:

   * Apache Sling 요청 로거

      (org.apache.sling.engine.impl.log.RequestLogger)

   * 또는 에 메시지를 `request.log` 씁니다 `access.log`.

다른 쌍은 표준 구성을 따릅니다.

* 로거:

   * Apache Sling 로깅 로거 구성

      (org.apache.sling.commons.log.LogManager.factory.config)

   * 에 `Information` 메시지를 씁니다 `logs/error.log`.

* 작성기에 대한 링크:

   * Apache Sling 로깅 작성기 구성

      (org.apache.sling.commons.log.LogManager.factory.writer)

* 로거:

   * Apache Sling 로깅 로거 구성(org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * 서비스에 `Warning` 대한 메시지를 `../logs/error.log` `org.apache.pdfbox`씁니다.

* 특정 작성기에 링크하지 않으므로 기본 구성(일별 로그 회전)이 있는 암시적 작성기를 만들어 사용합니다.

AEM에 클라우드 서비스 인스턴스(`request`및 `access``error` 로그)로 제공되는 세 가지 로그 외에도 디스패처 문제를 디버깅하는 데 사용되는 다른 로그가 있습니다. 자세한 내용은 Apache [및 Dispatcher 구성](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html#debugging-apache-and-dispatcher-configuration)디버깅을 참조하십시오.

모범 사례의 경우 현재 AEM에 있는 구성을 Cloud Service Maven 전형으로 정렬하는 것이 좋습니다. 이러한 설정은 특정 환경 유형에 대해 서로 다른 로그 설정 및 수준을 설정합니다.

* 및 `local dev` 환경의 경우 로거를 DEBUG `dev` 수준으로 **** 설정합니다. `error.log`
* for `stage`the logger to **WARN** level to the `error.log`
* for `prod`the set logger to **ERROR** level to the `error.log`

아래 각 구성에 대한 예를 살펴보십시오.

* `dev` 환경:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.file="logs/error.log"
    org.apache.sling.commons.log.level="debug"
    org.apache.sling.commons.log.names="[${package}]"
    org.apache.sling.commons.log.additiv="true"
    org.apache.sling.commons.log.pattern="${symbol_escape}{0,date,yyyy-MM-dd HH:mm:ss.SSS} {4} [{3}] {5}" />
```


* `stage` 환경:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.file="logs/error.log"
    org.apache.sling.commons.log.level="warn"
    org.apache.sling.commons.log.names="[${package}]"
    org.apache.sling.commons.log.additiv="true"
    org.apache.sling.commons.log.pattern="${symbol_escape}{0,date,yyyy-MM-dd HH:mm:ss.SSS} {4} [{3}] {5}" />
```

* `prod` 환경:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.file="logs/error.log"
    org.apache.sling.commons.log.level="error"
    org.apache.sling.commons.log.names="[${package}]"
    org.apache.sling.commons.log.additiv="true"
    org.apache.sling.commons.log.pattern="${symbol_escape}{0,date,yyyy-MM-dd HH:mm:ss.SSS} {4} [{3}] {5}" />
```

## 로그 수준 설정 {#setting-the-log-level}

클라우드 환경의 로그 수준을 변경하려면 Sling Logging OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지는 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 신속하게 변경하는 메커니즘이 있을 수 있습니다.

>[!NOTE]
>
> 아래 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 해당 변경 사항을 만든 다음 AEM을 클라우드 서비스 인스턴스로 푸시해야 합니다. 이 방법에 대한 자세한 내용은 클라우드 서비스로 [AEM에 배포를 참조하십시오](/help/implementing/deploying/overview.md).

### 디버그 로그 수준 활성화 {#activating-the-debug-log-level}

>[!WARNING]
>
> DEBUG 로그 수준을 전역적으로 활성화하면 대량의 정보가 생성되므로 간을 전환하기 어렵습니다. 디버깅이 필요한 서비스에만 사용하도록 설정하는 것이 좋습니다. 자세한 내용은 로거 및 개인 [서비스 작성자를 참조하십시오](logging.md#loggers-and-writers-for-individual-services).

기본 로그 수준은 INFO입니다. 즉, DEBUG 메시지가 기록되지 않습니다.
디버그 로그 수준을 활성화하려면

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

property to debug. 로그를 많은 로그를 생성하므로 DEBUG 로그 수준에서 로그를 필요 이상으로 오래 보관하지 마십시오.
디버그 파일의 행은 일반적으로 DEBUG로 시작되며 로그 수준, 설치 프로그램 작업 및 로그 메시지를 제공합니다. 예:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

로그 수준은 다음과 같습니다.

| 0 | 치명적인 오류 | 작업이 실패하여 설치 프로그램을 계속할 수 없습니다. |
|---|---|---|
| 1 | 오류 | 작업이 실패했습니다. 설치가 진행되지만 CRX의 일부가 제대로 설치되지 않아 작동하지 않습니다. |
| 2 | 경고 | 작업에 성공했지만 문제가 발생했습니다. CRX가 제대로 작동하지 않거나 작동하지 않을 수 있습니다. |
| 3 | 정보 | 작업이 성공했습니다. |

### 로거 및 작가 제작 {#creating-your-own-loggers-and-writers}

로거/기록기 쌍을 정의할 수 있습니다.

1. Apache Sling Logger Configuration의 새 인스턴스를 [만듭니다](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. 로거를 지정합니다.

<!-- 1. Create a new instance of the Factory Configuration [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

    1. Specify the Log File - this must match that specified for the Logger.
    1. Configure the other parameters as required. -->

### 로깅 구성 {#configure-logging}

>[!NOTE]
>
>Adobe Experience Manager를 사용하여 작업할 때는 이러한 서비스에 대한 구성 설정을 관리하는 몇 가지 방법이 있습니다.

특정 상황에서는 다른 로그 수준으로 사용자 정의 로그를 만들 수 있습니다. 다음과 같은 방법으로 저장소에서 이 작업을 수행할 수 있습니다.

1. 아직 존재하지 않는 경우 프로젝트에 대한 새 구성 폴더( `sling:Folder`)를 `/apps/<*project-name*>/config`만듭니다.
1. 에서 새 Apache `/apps/<*project-name*>/config`Sling 로깅 로거 구성의 노드를 만듭니다.

   * 이름:(로거인 경우) `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>`

      여기서 은 인스턴스를 식별하기 위해 입력해야 하는 자유 텍스트로 `<*identifier*>` 대체됩니다(이 정보는 생략할 수 없음).

      예, `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * 유형: `sling:OsgiConfig`
   >[!NOTE]
   >
   >기술적인 요구 사항은 아니지만 `<*identifier*>` 고유하게 만드는 것이 좋습니다.

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

또한 Felix Console에서는 Sling Log 지원에 대한 정보를 `../system/console/slinglog`제공합니다.for example `https://localhost:4502/system/console/slinglog`.draf