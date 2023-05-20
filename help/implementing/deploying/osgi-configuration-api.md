---
title: OSGi 구성 API
description: AEM as a Cloud Service OSGi 구성 표면에 대한 설명
feature: Deploying
exl-id: 94d3df65-71d7-4442-8412-fe2cca7e79ff
source-git-commit: cba6648d7ef18f3cccbd9562f3a66d9c683ae852
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---

# OSGi 구성 API

아래 두 목록은 고객이 구성할 수 있는 사항을 설명하는 AEM as a Cloud Service OSGi 구성 표면을 반영합니다.

1. 고객 코드로 구성하지 않아야 하는 OSGi 구성 목록
1. 속성을 구성할 수 있지만 표시된 유효성 검사 규칙을 준수해야 하는 OSGi 구성 목록입니다. 이러한 규칙에는 속성 선언이 필요한지 여부, 속성 유형 및 경우에 따라 허용되는 값 범위가 포함됩니다.

OSGI 구성이 나열되지 않으면 고객 코드로 구성할 수 있습니다.

이러한 규칙은 Cloud Manager 빌드 프로세스 중에 검증됩니다. 시간이 지남에 따라 추가 규칙을 추가할 수 있으며 예상 적용 날짜가 표에 명시되어 있습니다. 고객은 목표 시행 날짜까지 이러한 규칙을 준수해야 합니다. 제거 날짜 이후에 규칙을 준수하지 않으면 Cloud Manager 빌드 프로세스에서 오류가 발생합니다. Maven 프로젝트에는 [AEM as a Cloud Service SDK Build Analyzer Maven Plugin](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html) 로컬 SDK 개발 중에 OSGI 구성 오류에 플래그를 지정합니다.

OSGI 구성에 대한 추가 정보는 다음에서 확인할 수 있습니다. [이 위치](/help/implementing/deploying/configuring-osgi.md).

## 수정할 수 없는 OSGi 구성 {#osgi-configurations-that-cannot-be-modified}

* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
* **`org.apache.felix.http (Factory)`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (공고일: 2021년 8월 25일, 시행일: 2021년 11월 26일)

## 빌드 유효성 검사 규칙에 따른 OSGi 구성 {#osgi-configurations-subject-to-build-validation-rules}

* **`org.apache.felix.eventadmin.impl.EventAdmin`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
   * `org.apache.felix.eventadmin.ThreadPoolSize`
      * 유형: 정수
      * 필수 범위: 2-100
   * `org.apache.felix.eventadmin.AsyncToSyncThreadRatio`
      * 유형: double
   * `org.apache.felix.eventadmin.Timeout`
      * 유형: 정수
   * `org.apache.felix.eventadmin.RequireTopic`
      * 유형: 부울
   * `org.apache.felix.eventadmin.IgnoreTimeout`
      * 필수
      * 유형: 문자열 배열
      * 필수 범위: 적어도 다음 중 하나를 포함해야 합니다. `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*`
   * `org.apache.felix.eventadmin.IgnoreTopic`
      * 유형: 문자열 배열
* **`org.apache.felix.http`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
   * `org.apache.felix.http.timeout`
      * 유형: 정수
   * `org.apache.felix.http.session.timeout`
      * 유형: 정수
   * `org.apache.felix.http.jetty.threadpool.max`
      * 유형: 정수
   * `org.apache.felix.http.jetty.headerBufferSize`
      * 유형: 정수
   * `org.apache.felix.http.jetty.requestBufferSize`
      * 유형: 정수
   * `org.apache.felix.http.jetty.responseBufferSize`
      * 유형: 정수
   * `org.apache.felix.http.jetty.maxFormSize`
      * 유형: 정수
   * `org.apache.felix.https.jetty.session.cookie.httpOnly`
      * 유형: 부울
   * `org.apache.felix.https.jetty.session.cookie.secure`
      * 유형: 부울
   * `org.eclipse.jetty.servlet.SessionIdPathParameterName`
      * 유형: 문자열
   * `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding`
      * 유형: 부울
   * `org.eclipse.jetty.servlet.SessionCookie`
      * 유형: 문자열
   * `org.eclipse.jetty.servlet.SessionDomain`
      * 유형: 문자열
   * `org.eclipse.jetty.servlet.SessionPath`
      * 유형: 문자열
   * `org.eclipse.jetty.servlet.MaxAge`
      * 유형: 정수
   * `org.eclipse.jetty.servlet.SessionScavengingInterval`
      * 유형: 정수
   * `org.apache.felix.jetty.gziphandler.enable`
      * 유형: 부울
   * `org.apache.felix.jetty.gzip.minGzipSize`
      * 유형: 정수
   * `org.apache.felix.jetty.gzip.compressionLevel`
      * 유형: 정수
   * `org.apache.felix.jetty.gzip.inflateBufferSize`
      * 유형: 정수
   * `org.apache.felix.jetty.gzip.syncFlush`
      * 유형: 부울
   * `org.apache.felix.jetty.gzip.excludedUserAgents`
      * 유형: 문자열
   * `org.apache.felix.jetty.gzip.includedMethods`
      * 유형: 문자열 배열
   * `org.apache.felix.jetty.gzip.excludedMethods`
      * 유형: 문자열 배열
   * `org.apache.felix.jetty.gzip.includedPaths`
      * 유형: 문자열 배열
   * `org.apache.felix.jetty.gzip.excludedPaths`
      * 유형: 문자열 배열
   * `org.apache.felix.jetty.gzip.includedMimeTypes`
      * 유형: 문자열 배열
   * `org.apache.felix.jetty.gzip.excludedMimeTypes`
      * 유형: 문자열 배열
   * `org.apache.felix.http.session.invalidate`
      * 유형: 부울
   * `org.apache.felix.http.session.container.attribute`
      * 유형: 문자열 배열
   * `org.apache.felix.http.session.uniqueid`
      * 유형: 부울
* **`org.apache.sling.scripting.cache`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
   * `org.apache.sling.scripting.cache.size`
      * 유형: 정수
      * 필수 범위: >= 2048
   * `org.apache.sling.scripting.cache.additional_extensions`
      * 필수
      * 유형: 문자열 배열
      * 필수 범위: js를 포함해야 함
* **`com.day.cq.mailer.DefaultMailService`** (공고일: 2021년 4월 30일, 시행일: 2021년 7월 31일)
   * `smtp.host`
      * 유형: 문자열
   * `smtp.port`
      * 유형: 정수
      * 필수 범위: 465, 587 또는 25
   * `smtp.user`
      * 유형: 문자열
   * `smtp.password`
      * 유형: 문자열
   * `from.address`
      * 유형: 문자열
   * `smtp.ssl`
      * 유형: 문자열
   * `smtp.starttls`
      * 유형: 부울
   * `smtp.requiretls`
      * 유형: 부울
   * `debug.email`
      * 유형: 부울
   * `oauth.flow`
      * 유형: 부울
* **`org.apache.sling.commons.log.LogManager.factory.config`** (공고일: 21/11/16, 시행일: 21/21/2/16)
   * `org.apache.sling.commons.log.level`
      * 유형: 열거형
      * 필수 범위: 정보, 디버그 또는 TRACE
   * `org.apache.sling.commons.log.names`
      * 유형: 문자열
   * `org.apache.sling.commons.log.file`
      * 유형: 문자열
   * `org.apache.sling.commons.log.additiv`
      * 유형: 부울