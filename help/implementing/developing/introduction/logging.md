---
title: 로깅
description: 중앙 로깅 서비스에 대한 전역 매개 변수, 개별 서비스에 대한 특정 설정 또는 데이터 로깅을 요청하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 0e4de19f4ae53414d90f6979980f3ce79f49394d

---


# 로깅{#logging}

클라우드 서비스로서 AEM에서는 다음을 구성할 수 있습니다.

* 중앙 로깅 서비스를 위한 전역 매개 변수
* 요청 데이터 로깅;요청 정보를 위한 전문 로깅 구성
* 개별 서비스에 대한 특정 설정;예를 들어 개별 로그 파일과 로그 메시지의 형식

로컬 개발의 경우 로그 항목은 `/crx-quickstart/logs` 폴더의 로컬 파일에 기록됩니다.

클라우드 환경에서 개발자는 Cloud Manager를 통해 로그를 다운로드하거나 명령줄 툴을 사용하여 로그를 추적할 수 있습니다.

>[!NOTE]
>
>클라우드 서비스로 AEM에 로그인하는 것은 Sling 원칙을 기반으로 합니다. 자세한 [내용은](https://sling.apache.org/site/logging.html) Sling 로깅을 참조하십시오.

## 전역 로깅 {#global-logging}

[Apache Sling 로깅](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) 구성은 루트 로거를 구성하는 데 사용됩니다. 이렇게 하면 AEM에서 클라우드 서비스로 로그인하기 위한 전역 설정이 정의됩니다.

* 로깅 수준
* 중앙 로그 파일의 위치
* 유지할 버전 수
* 버전 회전;최대 크기 또는 시간 간격
* 로그 메시지를 작성할 때 사용할 형식

## 로거 및 개인 서비스 작가 {#loggers-and-writers-for-individual-services}

글로벌 로깅 설정 외에도 AEM을 클라우드 서비스로 사용하면 개별 서비스에 대한 특정 설정을 구성할 수 있습니다.

* 특정 로깅 수준
* 개별 로그 파일의 위치
* 유지할 버전 수
* 버전 회전;최대 크기 또는 시간 간격
* 로그 메시지를 작성할 때 사용할 형식
* 로거(로그 메시지를 제공하는 OSGi 서비스)

따라서 단일 서비스의 로그 메시지를 별도의 파일로 보낼 수 있습니다. 개발 또는 테스트 중에 특히 유용할 수 있습니다.예를 들어, 특정 서비스에 대해 로그 수준이 향상되어야 하는 경우

클라우드 서비스로 AEM에서는 다음을 사용하여 로그 메시지를 파일에 기록합니다.

1. OSGi **서비스** (로거)는 로그 메시지를 기록합니다.
1. Logging **Logger** 는 이 메시지를 가져와서 사양에 따라 형식을 지정합니다.
1. 로깅 **작성기는** 이러한 모든 메시지를 사용자가 정의한 실제 파일에 기록합니다.

이러한 요소는 적절한 요소에 대해 다음 매개 변수로 연결됩니다.

* **로거(로깅 로거)**

   메시지를 생성하는 서비스를 정의합니다.

* **로그 파일(로깅 로거)**

   로그 메시지를 저장할 물리적 파일을 정의합니다.

   로깅 로거를 로깅 작성기와 연결하는 데 사용됩니다. 연결이 이루어지려면 로깅 작성기 구성에서 동일한 매개 변수와 값이 동일해야 합니다.

* **로그 파일(로깅 작성기)**

   로그 메시지가 작성될 실제 파일을 정의합니다.

   로깅 기록기 구성에서 동일한 매개 변수와 동일해야 하며 그렇지 않으면 일치하지 않습니다. 일치하는 항목이 없으면 암시적 작성기가 기본 구성(일별 로그 회전)으로 만들어집니다.

### Standard Logger 및 Writer {#standard-loggers-and-writers}

특정 로거 및 작성기는 클라우드 서비스 설치로 표준 AEM에 포함됩니다.

첫 번째 경우는 `request.log` 및 `access.log` 파일을 모두 제어하는 특별한 경우입니다.

* 로거:

   * Apache Sling 사용자 정의 가능한 요청 데이터 로거

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * 요청 컨텐츠에 대한 메시지를 `request.log`작성합니다.

* 링크 대상:

   * Apache Sling 요청 로거

      (org.apache.sling.engine.impl.log.RequestLogger)

   * 또는 에 메시지를 `request.log` 씁니다 `access.log`.

이러한 구성 요소는 필요한 경우 사용자 정의할 수 있지만, 표준 구성은 대부분의 설치에 적합합니다.

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

## 로그 수준 설정 {#setting-the-log-level}

클라우드 환경의 로그 수준을 변경하려면 Sling Logging OSGI 구성을 수정한 후 전체 재배포해야 합니다. 이는 즉각적이지는 않으므로 많은 트래픽을 받는 프로덕션 환경에서 자세한 로그를 활성화하는 것에 주의하십시오. 앞으로 로그 수준을 보다 신속하게 변경하는 메커니즘이 있을 수 있습니다.

> [!NOTE]
> 
> 아래 나열된 구성 변경 사항을 수행하려면 로컬 개발 환경에서 해당 변경 사항을 만든 다음 AEM을 클라우드 서비스 인스턴스로 푸시해야 합니다. 이 방법에 대한 자세한 내용은 클라우드 서비스로 [AEM에 배포를 참조하십시오](/help/implementing/deploying/overview.md).

### 디버그 로그 수준 활성화 {#activating-the-debug-log-level}

> [!WARNING]
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

   1. 로그 파일을 지정합니다.
   1. 로거를 지정합니다.
   1. 필요에 따라 다른 매개 변수를 구성합니다.

1. 팩토리 구성 Apache Sling 로깅 [작성기 구성의 새 인스턴스를 만듭니다](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. 로그 파일 지정 - 로거에 대해 지정된 파일과 일치해야 합니다.
   1. 필요에 따라 다른 매개 변수를 구성합니다.

### 사용자 정의 로그 파일 만들기 {#create-a-custom-log-file}

>[!NOTE]
>
>Adobe Experience Manager를 사용하여 작업할 때는 이러한 서비스에 대한 구성 설정을 관리하는 몇 가지 방법이 있습니다.

특정 상황에서는 다른 로그 수준의 사용자 정의 로그 파일을 만들 수 있습니다. 다음과 같은 방법으로 저장소에서 이 작업을 수행할 수 있습니다.

1. 아직 존재하지 않는 경우 프로젝트에 대한 새 구성 폴더( `sling:Folder`)를 `/apps/<*project-name*>/config`만듭니다.
1. 에서 새 Apache `/apps/<*project-name*>/config`Sling 로깅 로거 구성의 노드를 만듭니다.

   * 이름:(로거인 경우) `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>`

      여기서 은 인스턴스를 식별하기 위해 입력해야 하는 자유 텍스트로 `<*identifier*>` 대체됩니다(이 정보는 생략할 수 없음).

      예, `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * 유형: `sling:OsgiConfig`
   >[!NOTE]
   >
   >기술적인 요구 사항은 아니지만 `<*identifier*>` 고유하게 만드는 것이 좋습니다.

1. 이 노드에서 다음 속성을 설정합니다.

   * 이름: `org.apache.sling.commons.log.file`

      유형:문자열

      값:로그 파일 지정;예를 들면 `logs/myLogFile.log`

   * 이름: `org.apache.sling.commons.log.names`

      유형:문자열[] (문자열 + 다중)

      값:로거가 메시지를 기록할 OSGi 서비스를 지정합니다.예를 들어, 다음 모두

      * `org.apache.sling`
      * `org.apache.felix`
      * `com.day`
   * 이름: `org.apache.sling.commons.log.level`

      유형:문자열

      값:필요한 로그 수준( `debug`, `info``warn` 또는 `error`)을 지정합니다.for example `debug`

   * 필요에 따라 다른 매개 변수를 구성합니다.

      * 이름: `org.apache.sling.commons.log.pattern`

         유형: `String`

         값:필요에 따라 로그 메시지 패턴을 지정합니다.예를 들면

         `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`
   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` 는 최대 6개의 인수를 지원합니다.

   >{0} 유형의 타임스탬프 `java.util.Date`
   >
   >{1} 로그 마커{2} 현재 스레드의 이름{3} 로거 이름{4} 로그 수준{5} 로그 메시지

   >로그 호출에 스택 추적이 포함된 `Throwable` 경우 메시지에 스택이 추가됩니다.

   >[!CAUTION]
   org.apache.sling.commons.log.names에는 값이 있어야 합니다.

   >[!NOTE]
   로그 작성기 경로는 `crx-quickstart` 위치에 상대적입니다.
   따라서 다음과 같이 지정된 로그 파일입니다.
   `logs/thelog.log`

   >쓰기:
   `` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log&#39;.
   그리고 다음과 같이 지정된 로그 파일
   `../logs/thelog.log`

   >디렉토리에 쓰기:
   ` <*cq-installation-dir*>/logs/`
&quot;(예: ` `&lt;*cq-installation-dir*>/`crx-quickstart/`)

1. 이 단계는 새 작성기가 필요한 경우에만 필요합니다(예: 기본 작성기와 다른 구성).

   >[!CAUTION]
   새 로깅 작성자 구성은 기존 기본값이 적절하지 않은 경우에만 필요합니다.

   >명시적 작성기가 구성되지 않은 경우 시스템은 기본값을 기반으로 암시적 작성기를 자동으로 생성합니다.

   에서 `/apps/<*project-name*>/config`새 구성에 대한 노드를 `Apache Sling Logging Writer` 만듭니다.

   * 이름:( `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` 작성기로서)

      로거(Logger)와 마찬가지로, 인스턴스를 식별하기 위해 입력해야 하는 자유 텍스트로 `<*identifier*>` 대체됩니다(이 정보를 생략할 수 없음). 예, `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

   * 유형: `sling:OsgiConfig`
   >[!NOTE]
   기술적인 요구 사항은 아니지만 `<*identifier*>` 고유하게 만드는 것이 좋습니다.

   이 노드에서 다음 속성을 설정합니다.

   * 이름: `org.apache.sling.commons.log.file`

      유형: `String`

      값:로거에 지정된 파일과 일치하도록 로그 파일을 지정합니다.

      예를 들면 다음과 같습니다 `../logs/myLogFile.log`.

   * 필요에 따라 다른 매개 변수를 구성합니다.

      * 이름: `org.apache.sling.commons.log.file.number`

         유형: `Long`

         값:보관할 로그 파일의 수를 지정합니다.예를 들면 `5`

      * 이름: `org.apache.sling.commons.log.file.size`

         유형: `String`

         값:파일 회전을 크기/날짜별로 제어하기 위해 필요에 따라 지정합니다.예를 들면 `'.'yyyy-MM-dd`
   >[!NOTE]
   `org.apache.sling.commons.log.file.size` 다음 중 하나를 설정하여 로그 파일의 회전을 제어합니다.
   * 최대 파일 크기
   * 시간/날짜 일정
   를 클릭하여 새 파일을 만들 시기를 지정합니다(및 이름 패턴에 따라 이름이 변경된 기존 파일).
   * 크기 제한은 숫자로 지정할 수 있습니다. 크기 표시기를 지정하지 않으면 바이트 수로 표시되거나 크기 표시기( `KB`, `MB`또는 `GB` 대/소문자 무시) 중 하나를 추가할 수 있습니다.
   * 시간/날짜 일정을 `java.util.SimpleDateFormat` 패턴으로 지정할 수 있습니다. 이 설정은 파일을 회전할 기간을 정의합니다.또한 회전된 파일(식별을 위해)에 접미사를 추가합니다.
   기본값은 &#39;.&#39;입니다.yyyy-MM-dd(일별 로그 회전의 경우).
   예를 들어, 2010년 1월 20일 자정(또는 이 시간 이후 첫 번째 로그 메시지가 정확히 표시되었을 때), ../logs/error.log의 이름이 ../logs/error.log.2010-01-20으로 변경됩니다. 1월 21일에 대한 로깅은 다음 날 변경 시 롤오버될 때까지 ../logs/error.log에 출력됩니다(새 및 비어 있음).
       | `&#39;.&#39;yyyy-MM&#39;|매월 초에 회전|
    |—|—|
    | &quot;.&#39;yyyy-ww&#39;|각 주의 첫째 날에 회전(로케일에 따라 다름) |
       | `&#39;.&#39;yyyy-MM-dd&#39;|매일 자정에 회전 |
       | `&#39;.&#39;yyyy-MM-dd-a&#39;|매일 자정과 정오에 회전 |
       | `&#39;.&#39;yyyy-MM-dd-HH&#39;|매 시간 맨 위에 있는 회전. |
       | `&#39;.&#39;yyyy-MM-dd-HH-mm&#39;|매 분 시작 시 회전. |
 참고     
     사항:시간/날짜를 지정할 때:
      1. 단일 따옴표(&#39; &#39;); 쌍 내에서 &quot;escape&quot; 리터럴 텍스트를 사용해야 합니다.
  이는 특정 문자가 패턴 문자로 해석되지 않도록 하기     위한 것입니다.
       1. 옵션의 아무 위치에서나 유효한 파일 이름에 허용되는 문자만 사용하십시오.
   

1. 선택한 도구로 새 로그 파일을 읽습니다.

   이 예제로 만든 로그 파일은 `../crx-quickstart/logs/myLogFile.log`표시됩니다.

또한 Felix Console에서는 Sling Log 지원에 대한 정보를 `../system/console/slinglog`제공합니다.예를 `https://localhost:4502/system/console/slinglog`들면 다음과 같습니다.