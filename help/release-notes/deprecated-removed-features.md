---
title: 더 이상 사용되지 않으며 제거된 기능
description: ' [!DNL Adobe Experience Manager]  [!DNL Cloud Service]에서 더 이상 사용되지 않으며 제거된 기능에 관련된 릴리스 정보입니다.'
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
feature: Release Information
role: Admin
source-git-commit: 569ab7cfab02cfc5d5ad1c8f402a51df34f4bac6
workflow-type: tm+mt
source-wordcount: '3039'
ht-degree: 71%

---

# 더 이상 사용되지 않으며 제거된 기능 및 API {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="AEM as a Cloud Service에서 더 이상 사용되지 않으며 제거된 기능"
>abstract="AEM as a Cloud Service에는 클라우드 기반 배포 모델이 있습니다. 이 탭은 클라우드 기반 기능으로 대체된 기능을 강조 표시합니다."

Adobe은 API 및 구성을 포함한 기능을 정기적으로 검토하여 AEM as a Cloud Service의 성능, 보안 및 전반적인 가치에 대해 발전하는 표준을 충족하는지 확인합니다. 이러한 평가를 기반으로 특정 기능은 사용 중단 표시가 될 수 있습니다. 가능한 경우 Adobe에서 적절한 대체 기능을 제공합니다.

사용 중단이 발표되면 이 기능은 제한된 기간 동안만 사용할 수 있으며 고객은 지정된 제거 날짜 이전에 모든 사용을 제거해야 합니다. Adobe은 원활한 전환을 지원하기 위해 합당한 알림과 지침을 제공할 예정입니다.

사용 중단 기간 동안 Adobe은 이메일 알림, 작업 센터 알림 또는 Cloud Manager의 미리 알림을 통해 기능을 사용하지 않도록 전환하기 위해 수행해야 하는 작업을 고객에게 알려줍니다.

>[!WARNING]
>
>경우에 따라 새 Cloud Manager 빌드를 배포하거나 최신 버전의 AEM as a Cloud Service으로 업그레이드하기 전에 기능을 제거해야 할 수 있습니다.

## 사용되지 않는 기능 {#deprecated-features}

아래 표의 기능은 더 이상 사용되지 않는다고 발표되었지만 아직 제거되지 않았습니다.  대상 제거 날짜 이전에 기능 사용을 중지해야 하거나 성능, 가용성 및 보안과 관련된 문제가 발생할 수 있습니다.

| 기능 | 사용되지 않는 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| Sites | [Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md) | [OpenAPI를 사용한 콘텐츠 조각 배달](/help/headless/aem-content-fragment-delivery-with-openapi.md)<br>함께 제공<br> [콘텐츠 조각 및 콘텐츠 조각 모델 관리 OpenAPI](/help/headless/content-fragment-openapis.md) |
| Sites | [PWA 기능](/help/sites-cloud/authoring/sites-console/enable-pwa.md) | 없음 |
| Sites | [SPA 편집기](/help/implementing/developing/hybrid/introduction.md) | AEM에서 Headless 콘텐츠를 관리하기 위한 권장 편집기:<br>- 시각적 편집을 위한 [범용 편집기](/help/edge/wysiwyg-authoring/authoring.md)<br>- 양식 기반 편집을 위한 [콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-managing.md) |
| [!DNL Sites] | [JavaScript Use API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) | [Java Use API](https://experienceleague.adobe.com/ko/docs/experience-manager-htl/content/java-use-api) |
| [!DNL Sites] | **소셜 미디어 상태**&#x200B;에 대한 경험 조각 속성. | 이 기능은 곧 제거될 예정입니다. |
| Sites | [Experience Cloud 설정 자동화](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) | 없음 |
| [!DNL Sites] | 템플릿 기반 간단 콘텐츠 조각. | 현재는 [모델 기반 구조 콘텐츠 조각](/help/assets/content-fragments/content-fragments-models.md)입니다. |
| [!DNL Assets] | `DAM Asset Update` 수집된 이미지를 처리하는 워크플로입니다. | 이제 자산 수집은 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. |
| [!DNL Assets] | 자산을 [!DNL Experience Manager]에 직접 업로드합니다. [지원 중단된 자산 업로드 API](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api)를 참조하십시오. | [다이렉트 이진 업로드](/help/assets/add-assets.md)를 사용합니다. 기술적인 세부 정보는 [직접 업로드 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오. |
| [!DNL Assets] | [!DNL ImageMagick]과 같은 호출 명령줄 도구를 포함하여 `DAM Asset Update` 워크플로의 [일부 워크플로 단계](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps)는 지원되지 않습니다. | [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)는 많은 워크플로에 대한 대체 기능을 제공합니다. 사용자 정의 처리에는 [후 처리 워크플로](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용하십시오. |
| [!DNL Assets] | 비디오의 FFmpeg 코드 변환. | FFmpeg 썸네일 생성의 경우 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. FFmpeg 코드 변환의 경우 [Dynamic Media](/help/assets/manage-video-assets.md)를 사용합니다. |
| [!DNL Foundation] | 복제 에이전트의 “배포” 탭 아래에 있는 트리 복제 UI (2021년 9월 30일 이후 제거) | [게시 관리](/help/operations/replication.md#manage-publication) 또는 [트리 활성화 워크플로 단계](/help/operations/replication.md#tree-activation) 접근 방식. |
| [!DNL Foundation] | 복제 에이전트 관리 화면의 배포 탭과 복제 API를 사용하여 10MB보다 큰 콘텐츠 패키지를 복제할 수 없습니다. | [게시 관리](/help/operations/replication.md#manage-publication) 또는 [트리 활성화 워크플로 단계](/help/operations/replication.md#tree-activation) |
| [!DNL Foundation] | Adobe Developer Console 프로젝트에서 생성된 자격 증명을 사용하는 통합에서는 JWT(서비스 계정) 자격 증명에 대한 지원이 점차 중단됩니다. 2024년 5월 1일부터 Adobe Developer Console에서는 새 서비스 계정(JWT) 자격 증명을 만들 수 없습니다. 기존 서비스 계정(JWT) 자격 증명은 2025년 1월 1일까지 구성된 통합에 사용할 수 있으며, 그 이후에는 작동이 중단되므로 고객은 OAuth 서버 간 자격 증명으로 마이그레이션해야 합니다. [자세히 알아보기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console). | Adobe I/O OAuth 서버 간 자격 증명으로 [마이그레이션](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview)합니다. |
| [!DNL Foundation] | 콘텐츠 계층 구조 복제에 사용된 콘텐츠 트리 게시 워크플로 및 관련 콘텐츠 트리 게시 워크플로 단계. | 성능이 더 뛰어난 [트리 활성화 워크플로 단계](/help/operations/replication.md#tree-activation)를 사용하십시오. |
| [!DNL Foundation] | YUI를 사용하여 JavaScript 클라이언트 라이브러리를 압축/축소합니다. Adobe은 YUI 라이브러리를 더 이상 업데이트할 계획이 없습니다. | Adobe에서는 구현을 위해 Google Closure Compiler(GCC)로 전환할 것을 권장합니다. |

## 제거된 기능 {#removed-features}

이 섹션에는 제거된 기능이 나열됩니다.

| 영역 | 기능 | 대체 | 목표 제거 날짜 |
| ------------ | ------------------ | ----------- | ------------------- |
| 사용자 인터페이스 | 클래식 UI는 제품 사용자 인터페이스에서 제거됩니다. 링크 검사기, 버전 제거 및 일부 Cloud Service 구성과 같은 일부 선택 기능에서 몇 가지 클래식 UI 대화 상자를 사용할 수 있습니다. 예정된 [제품 업데이트](/help/release-notes/home.md) 이후에는 클래식 UI를 사용할 수 없습니다. | 표준 UI | 제거됨 |
| [!DNL Dynamic Media] | [!DNL Experience Manager] as a [!DNL Cloud Service]에서 [Dynamic Media Classic](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/sites/administering/integration/scene7#integration)과 [Dynamic Media 하이브리드 모드](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/assets/dynamic/config-dynamic#dynamic)와의 이전 통합을 사용할 수 없습니다. | [!DNL Experience Manager] as a [!DNL Cloud Service]에 제공되는 [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md)를 사용하십시오. | 제거됨 |
| [!DNL Sites] | 포털 디렉터 및 포틀릿 구성 요소 | 이들 기능은 [!DNL Experience Manager] 6.4에서 더 이상 사용되지 않으며 이제 [!DNL Experience Manager]에서 제거되었습니다. | 제거됨 |
| [!DNL Sites] | 디자인 가져오기 | 런타임 시 [!DNL Experience Manager] 저장소의 변경 불가능한 섹션을 사용할 수 없으므로 이 기능은 제거되었습니다. | 제거됨 |
| [!DNL Assets] | Assets 핵심 서비스 및 Creative Cloud 서비스와 공유 중인 [!DNL Assets]를 사용할 수 없습니다. | [!DNL Adobe Creative Cloud]와의 통합을 위해 [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)를 사용하십시오. | 제거됨 |
| [!DNL Foundation] | Apache Sling 데이터 소스 지원 (OSGi 번들 org.apache.sling.datasource) | 해당 사항 없음 | 제거됨 |
| [!DNL Foundation] | JST 스크립팅 템플릿 지원 (OSGi 번들 org.apache.sling.scripting.jst) | 해당 사항 없음 | 제거됨 |
| [!DNL Foundation] | Apache Felix Http Whiteboard 지원 | OSGi Http Whiteboard | 2022년 3월 |
| [!DNL Foundation] | com.adobe.granite.oauth.server 지원 | Adobe IMS 통합 | 2023년 3월 |
| [!DNL Foundation] | [서비스 사용자 ID 가져오기](https://sling.apache.org/apidocs/sling12/org/apache/sling/serviceusermapping/ServiceUserMapper.html#getServiceUserID-org.osgi.framework.Bundle-java.lang.String-)를 위한 org.apache.sling.serviceusermapping 기능 지원 | 해당 사항 없음 | 8/30/24 |
| [!DNL Foundation] | Java 11 런타임은 더 이상 사용되지 않으며 Adobe에서 Java 21 런타임으로 대체되었습니다. 코드는 여전히 Java 11을 사용하여 작성할 수 있습니다(Java 17 및 21은 기타 옵션) | Java 21 런타임이 적용됩니다. 호환성을 보장하려면 [런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)에 설명된 대로 라이브러리 버전을 업데이트해야 합니다 | 25/3/5/29 |

## 더 이상 사용되지 않는 API {#aem-apis}

아래 표의 API(확장하려면 클릭)는 더 이상 사용되지 않는 것으로 발표되었지만 아직 제거되지 않았습니다.  대상 제거 날짜 이전에 이러한 API 사용을 중지해야 하거나 성능, 가용성 및 보안과 관련된 문제가 발생할 수 있습니다. 일부 API는 아래 API 제거 지침 섹션을 참조합니다.

<details>
  <summary>더 이상 사용되지 않는 API 목록을 보려면 펼쳐보십시오.</summary>
<table style="table-layout:auto">
  <tr>
    <th>패키지/클래스</th>
    <th>댓글</th>
    <th>사용 중단일</th>
    <th>목표 제거 날짜</th>
  </tr>
<tbody>
  <tr>
    <td>org.apache.sling.commons.auth<br>org.apache.sling.commons.auth.spi</td>
    <td>대안으로 Sling의 인증 코어/인증 코어 SPI 인터페이스를 사용하십시오. <a href="#org.apache.sling.commons.auth">아래의 제거 노트를 참조하십시오.</a></td>
    <td>2015</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
<td>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.util<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread</td>
    <td>Eclipse Jetty 및 Felix Http Jetty 패키지는 더 이상 지원되지 않습니다. <a href="#org.eclipse.jetty">아래의 제거 노트를 참조하십시오.</a></td>
    <td>5/27/2021</td>
    <td>8/31/2025</td>
  </tr>
 <tr>     <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>해당 API는 AEM as a Cloud Service에서 사용할 수 없습니다. <a href="#com.mongodb">아래의 제거 노트를 참조하십시오.</a></td>
    <td>5/27/2021</td>
    <td>8/31/2025</td>
  </tr>
   <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Apache Abdera가 2017년부터 중단됨에 따라 해당 API는 더 이상 사용되지 않습니다. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">아래의 제거 노트를 참조하십시오.</a></td>
    <td>7/29/2021</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Apache Abdera가 2017년부터 중단됨에 따라 해당 API는 더 이상 사용되지 않습니다. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">아래의 제거 노트를 참조하십시오.</a></td>
    <td>4/8/2019</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Apache Felix Http Whiteboard는 더 이상 지원되지 않습니다. 코드를 OSGi Http Whiteboard로 마이그레이션합니다. <a href="#org.apache.felix.http.whiteboard">아래의 제거 노트를 참조하십시오.</a></td>
    <td>1/27/2022</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>이 API는 더 이상 사용되지 않습니다. JDK에서 제공하는 XML API로 코드를 마이그레이션하십시오.</td>
    <td>1/27/2022</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>AEM as a Cloud Service은 이 내부 로그백 API를 지원하지 않습니다. <a href="#ch.qos.logback">아래의 제거 노트를 참조하십시오.</a></td>
    <td>1/27/2022</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>AEM as a Cloud Service은 이 내부 log4j API를 지원하지 않습니다. <a href="#org.slf4j">아래의 제거 노트를 참조하십시오.</a></td>
    <td>1/27/2022</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1은 2015년에 서비스가 종료되었으며 더 이상 지원되지 않습니다. <a href="#org.apache.log4j">아래의 제거 노트를 참조하십시오.</a></td>
    <td>1/27/2022</td>
    <td>8/31/2025</td>
  </tr>
  <tr>  <td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>Google Guava Core Libraries는 더 이상 사용되지 않습니다.</td>
    <td>5/15/2023</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.slf4j.event</td>
    <td>AEM as a Cloud Service은 이 내부 slf4j API를 지원하지 않습니다. <a href="#org.slf4j">아래의 제거 노트를 참조하십시오.</a></td>
    <td>4/11/2022</td>
    <td>8/31/2025</td>
  </tr> 
    <tr>
    <td>com.drew.*</td>
    <td>이미지와 비디오에서 메타데이터를 추출하려면 Cloud Service의 Asset Compute, Apache POI 또는 Apache Tika를 통해 수행해야 합니다.</td>
    <td>9/17/2024</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.blob.*</td>
    <td>이 API는 내부적으로만 사용할 수 있습니다.</td>
    <td>9/23/2024</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.memory</td>
    <td>이 API는 내부적으로만 사용할 수 있습니다.</td>
    <td>9/23/2024</td>
    <td>8/31/2025</td>
  </tr>
  <tr>
<td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n<br>org.apache.felix.webconsole.spi</td>
    <td>Felix 웹 콘솔은 클라우드 환경에서 지원되지 않습니다. <a href="#org.apache.felix.webconsole">아래의 제거 노트를 참조하십시오.</a></td>
    <td>4/30/2021</td>
    <td>8/31/2025</td>
  </tr>
<td>org.bson<br/>org.bson.assertions<br/>org.bson.codecs<br/>org.bson.codecs.configuration<br/>org.bson.codecs.pojo<br/>org.bson.codecs.pojo.annotations<br/>org.bson.conversions<br/>org.bson.diagnostics<br/>org.bson.internal<br/>org.bson.io<br/>org.bson.json<br/>org.bson.types<br/>org.bson.util</td>
    <td>해당 API는 AEM as a Cloud Service에서 사용할 수 없습니다.</td>
    <td>10/31/2022</td>
    <td>8/31/2025</td>
  </tr>  
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td><a href="https://johnzon.apache.org/index.html">javax.json</a>의 Apache Johnzon 구현이 권장되며 사용해야 합니다. </td>
    <td>4/30/2021</td>
    <td>TBD</td>
  </tr>
  <tr>
<td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2는 유지 관리 모드입니다. 대신 Commons Lang 3을 사용해야 합니다. <a href="#apache.commons">아래의 제거 노트를 참조하십시오.</a></td>
    <td>4/30/2021</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Commons Collections 3은 유지 관리 모드입니다. 대신 Commons Collections 4를 사용해야 합니다. <a href="#apache.commons">아래의 제거 노트를 참조하십시오.</a></td>
    <td>4/30/2021</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>이 API는 더 이상 사용되지 않습니다. 대신 Apache Sling의 빌더를 사용하십시오.</td>
    <td>10/31/2022</td>
    <td>TBD</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>AEM as a Cloud Service는 이 API를 지원하지 않습니다.</td>
    <td>5/15/2023</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.day.cq.xss<br>com.day.cq.xss.taglib<br>com.day.cq.xss.impl</td>
    <td>대신 org.apache.sling.xss를 사용하십시오.</td>
    <td>12/12/2023</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.adobe.granite.xss<br>com.adobe.granite.xss.impl</td>
    <td>대신 org.apache.sling.xss를 사용하십시오.</td>
    <td>12/12/2023</td>
    <td>TBD</td>
  </tr>
  </tbody>
</table>
</details>

## 제거된 API {#removed-apis}

이 섹션에는 더 이상 사용되지 않고 제거된 API가 나열됩니다. 일부 API는 아래 API 제거 지침 섹션을 참조합니다.

<details>
  <summary>제거된 API의 목록을 보려면 이를 펼치십시오.</summary>
<table style="table-layout:auto">
  <tr>
    <th>패키지/클래스</th>
    <th>댓글</th>
  </tr>
<tbody>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>대안으로 Sling의 검색 API를 사용하십시오.</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>맞춤형 지속성 관리자는 AEM as a Cloud Service에서 지원되지 않습니다.</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Apache Felix HealthCheck API를 대신 사용하는 것이 좋습니다.</td>
  </tr>
  <tr> <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml</td>
    <td>Eclipse Jetty 및 Felix Http Jetty 패키지는 더 이상 지원되지 않습니다.</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Apache Felix 메타타입 및 SCR API는 더 이상 사용되지 않습니다.  대신 OSGi 메타타입 및 선언 서비스 API를 사용합니다.</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>로그 구현 클래스는 AEM as a Cloud Service와 호환되지 않습니다.</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>레거시 AEM 6.x API.</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>해당 API는 Cloud Service에서 사용할 수 없습니다.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Apache Xerces와 관련된 Util 클래스는 주요 버전 변경이 발생하는 후속 릴리스에서 제거됩니다. 이들 Util은 FileVault에서 내부용으로 사용되므로 해당 API는 공개 API 표면에서 더 이상 사용되지 않습니다.</td>
  </tr>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>레거시 AEM 6.x API. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">아래의 제거 노트를 참조하십시오.</a></td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>AEM as a Cloud Service는 이 내부 로그백 API를 지원되지 않습니다.</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>보안 취약성으로 인해 Handlebars를 4.0.5에서 4.3.0으로 업그레이드해야 합니다. 업그레이드된 Handlebars에는 이 패키지가 더 이상 존재하지 않습니다.</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>이 API는 더 이상 지원되지 않습니다. 대신 org.apache.sling.api.resource.ResourceResolverFactory를 사용하십시오.</td>
  </tr>
  <tr>
    <td>org.apache.sling.repoinit.jcr<br>org.apache.sling.repoinit.parser.operations</td>
    <td>해당 API는 AEM as a Cloud Service에서 사용할 수 없습니다.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.cache</td>
    <td>이 API는 내부적으로만 사용할 수 있습니다.</td>
  </tr>
</tbody>
</table>
</details>

## API 제거 지침 {#api-removal-guidance}

이 섹션은 위의 표에 있는 다양한 API에 대한 API 제거 지침을 반영합니다.

### `org.apache.sling.commons.auth*` 제거 {#org.apache.sling.commons.auth}

`org.apache.sling.commons.auth` 및/또는 `org.apache.sling.commons.auth.spi`를 사용하는 경우 코드를 `org.apache.sling.auth` 응답으로 마이그레이션하여 사용을 바꿀 수 있습니다. `org.apache.sling.auth.spi`. [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)의 이전 버전을 사용하고 있다면 최신 버전으로 업데이트하십시오.

액션 목록:

* ACS AEM Commons를 최신 버전(최소 6.11.0)으로 업데이트
* `org.apache.sling.commons.auth` 및/또는 `org.apache.sling.commons.auth.spi`에서 `org.apache.sling.auth` 응답으로 마이그레이션합니다. `org.apache.sling.auth.spi`

### `org.apache.felix.webconsole*` 제거 {#org.apache.felix.webconsole}

`org.apache.felix.webconsole*`의 패키지를 사용하는 경우 프로젝트에서 이 코드를 제거합니다. Cloud Service에서 웹 콘솔에 액세스할 수 없습니다.

액션 목록:

* `org.apache.felix.webconsole*`에서 패키지를 사용하여 코드 제거

### `org.eclipse.jetty*` 제거 {#org.eclipse.jetty}

패키지 `org.eclipse.jetty` 또는 하위 패키지 중 하나를 사용하는 경우 비슷한 기능을 가진 다른 서드파티 라이브러리로 마이그레이션하는 것이 좋습니다. 마이그레이션이 불가능한 경우 아래 목록에서 필요한 번들을 프로젝트에 추가하십시오.

액션 목록:

* `org.eclipse.jetty` 패키지 사용을 다른 서드파티 라이브러리/자체 코드로 바꾸거나
* 이 목록에서 필요한 번들을 선택하여 프로젝트에 추가합니다.
   * `org.eclipse.jetty:jetty-client:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-http:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-io:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-security:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-servlet:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-server:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util-ajax:9.4.54.v20240208`

### `com.mongodb` 제거 {#com.mongodb}

프로젝트에 Mongo 클라이언트 API를 추가합니다.

액션 목록:

* 프로젝트에 이 번들 추가
   * `org.mongodb:mongo-java-driver:3.12.7`

### `Apache Commons Lang 2 and Apache Commons Collections 3` 제거 {#apache.commons}

유지 관리되지 않는 Apache Commons 라이브러리의 사용을 제거하고 지원 버전의 사용으로 대체합니다. 대부분의 경우 패키지 가져오기를 조정해야 하며 일부 경우에는 클래스 또는 메서드의 이름이 바뀌었을 뿐입니다. [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)의 이전 버전을 사용하고 있다면 최신 버전으로 업데이트하십시오.

액션 목록:

* ACS AEM Commons를 최신 버전(최소 6.11.0)으로 업데이트
* `org.apache.commons.lang*`의 가져오기를 `org.apache.commons.lang3`(으)로 바꾸기
* `org.apache.commons.collections*`의 가져오기를 `org.apache.commons.collecitons4`(으)로 바꾸기

### `org.apache.abdera*` 및 `org.apache.sling.atom.taglib` 사용 {#org.apache.abdera_or_org.apache.sling.atom.taglib}

`org.apache.abdera` 및 `org.apache.sling.atom.taglib`의 모든 패키지 사용을 비슷한 기능을 제공하는 서드파티 라이브러리나 자체 코드로 바꿉니다.

액션 목록:

* `org.apache.abdera` 및 `org.apache.sling.atom.taglib`의 패키지 사용을 다른 서드파티 라이브러리/자체 코드로 바꿉니다.

### `org.apache.felix.http.whiteboard` 사용 {#org.apache.felix.http.whiteboard}

`org.apache.felix.http.whiteboard` 사용을 [OSGi Http Whiteboard](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html)로 바꿉니다. 공식 OSGi API는 비슷한 기능을 가지고 있으며, 대부분 교체 시 서비스 등록 속성만 변경하면 됩니다.

액션 목록:

* `org.apache.felix.http.whiteboard`의 사용을 [OSGi Http Whiteboard](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html)로 바꾸기

### `ch.qos.logback*` 사용 {#ch.qos.logback}

Cloud Service에서는 로그백이 지원되지 않습니다. 모든 사용을 제거하십시오. [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)의 이전 버전을 사용하고 있다면 최신 버전으로 업데이트하십시오.

액션 목록:

* ACS AEM Commons를 최신 버전(최소 6.11.0)으로 업데이트
* `ch.qos.logback`에서 패키지를 사용하여 코드 제거

### `org.slf4j.event and org.slf4j.spi` 사용 {#org.slf4j}

`org.slf4j.event` 또는 `org.slf4j.spi`을(를) 사용하는 경우 해당 사용을 모두 제거하십시오. [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)의 이전 버전을 사용하고 있다면 최신 버전으로 업데이트하십시오.

액션 목록:

* ACS AEM Commons를 최신 버전(최소 6.11.0)으로 업데이트
* `org.slf4j.event` 및 `org.slf4j.spi`을(를) 사용하여 코드 제거

### `org.apache.log4j` 사용 {#org.apache.log4j}

`org.apache.log4j`을(를) 사용하는 경우 SLF4J(`org.slf4j`) 또는 Log4J 2.x(`org.apache.logging.log4j`)(으)로 전환합니다.

액션 목록:

* `org.apache.log4j`의 사용을 `org.slf4j` 사용(권장) 또는 `org.apache.logging.log4j`(으)로 바꾸기

## OSGI 구성 {#osgi-configuration}

아래 섹션은 AEM as a Cloud Service OSGi 구성 표면을 반영하며 고객이 구성할 수 있는 내용을 설명합니다.

1. 고객 코드는 나열된 OSGi 구성을 구성해서는 안 됩니다.
1. 속성을 구성할 수 있지만 표시된 유효성 검사 규칙을 준수해야 하는 OSGi 구성 목록입니다. 이러한 규칙에는 속성 선언이 필요한지 여부, 해당 유형 및 경우에 따라 허용되는 값 범위가 포함됩니다.

고객 코드는 나열되지 않은 모든 OSGi 구성을 구성할 수 있습니다.

Cloud Manager 빌드 프로세스 중에 이러한 규칙의 유효성이 검사됩니다. 시간이 지남에 따라 다른 규칙이 추가될 수 있으며, 예상 시행 일자는 테이블에 명시되어 있습니다. 고객은 목표 시행 일자까지 이러한 규칙을 준수해야 합니다. 제거 날짜 이후에 규칙을 준수하지 않으면 Cloud Manager 빌드 프로세스에서 오류가 발생합니다. Maven 프로젝트에는 로컬 SDK 개발 중 OSGI 구성 오류에 플래그를 지정하도록 [AEM as a Cloud Service SDK Build Analyzer Maven Plugin](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin)을 포함해야 합니다.

OSGI 구성에 대한 추가 정보는 [이 위치](/help/implementing/deploying/configuring-osgi.md)에서 확인할 수 있습니다.

### 더 이상 사용되지 않는 OSGi 속성(곧 수정될 예정) {#deprecated-unmodifiable-osgi-properties}

다음 OSGi 구성 요소 PID에 대한 속성은 더 이상 사용되지 않으며 시행일까지 사용이 중단되어야 합니다.

| **OSGI 구성 요소 ID** | **수정할 수 없는 속성** | **사용 중단** | **적용** |
|---|---|---|---|
| **`org.apache.sling.commons.log.LogManager`** | 모두 | 4/24/25 | 2025년 8월 31일(구성이 6월에 무시됨) |
| **`org.apache.sling.commons.log.LogManager.factory.config`** | org.apache.sling.commons.log.file, org.apache.sling.commons.log.pattern | 4/24/25 | 2025년 8월 31일(구성이 6월에 무시됨) |
| **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** | 모두 | 2024 | 8/31/25 |
| **`com.adobe.granite.toggle.impl.dev.DynamicToggleProviderImpl`** | 모두 | 6/3/25 | 8/31/25 |
| **`org.apache.http.proxyconfigurator`** | 모두 | 6/3/25 | 8/31/25 |

### 수정할 수 없는 OSGi 속성 {#unmodifiable-osgi-properties}

아래 설명된 대로 다음 OSGi 구성 요소 PID에 대한 속성을 수정할 수 없습니다.

| **OSGI 구성 요소 ID** | **수정할 수 없는 속성** |
|---|---|
| **`com.day.cq.auth.impl.cug.CugSupportImpl`** |
| **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** | 모두 |
| **`com.adobe.granite.toggle.impl.ToggleRouterImpl`** | 모두 |
| **`org.apache.sling.engine.impl.log.RequestLoggerFilter`** | 모두 |
| **`org.apache.sling.feature.apiregions.impl`** | 모두 |
| **`org.apache.sling.jcr.resource.internal.helper.jcr.BinaryDownloadUriProvider`** | 모두 |
| **`com.adobe.cq.unifiedshell.impl.discovery.DiscoveryServlet`** | 모두 |
| **`com.adobe.cq.unifiedshell.impl.ui.FrameErrorHandler`** | 모두 |
| **`com.adobe.cq.unifiedshell.impl.config.UnifiedShellConfService`** | 모두 |
| **`com.adobe.cq.unifiedshell.impl.config.RepositoryIdentifier`** | 모두 |
| **`org.apache.sling.feature.apiregions.factory`** | 모두 |
| **`com.adobe.granite.toggle.monitor.systemproperty`** | 모두 |


### 향후 강제 적용된 OSGi 속성 제한 {#future-restrictions-osgi-properties}

향후 Adobe에서는 다음 OSGi 속성 제한을 적용하여 사용을 중단해야 합니다.

| OSGi 구성 요소 PID |   | 필수 | 유형 | 제한(적용되는 경우) |
|---|---|---|---|---|
| `com.day.cq.mailer.DefaultMailService` | `smtp.host` |   | 문자열 |   |
|   | `smtp.port` | 예 | 정수 | 465, 587 또는 25 중 하나 |
|   | `smtp.user` |   | 문자열 |   |
|   | `smtp.password` |   | 문자열 |   |
|   | `from.address` |   | 문자열 |   |
|   | `smtp.ssl` |   | 문자열 |   |
|   | `smtp.starttls` |   | 부울 |   |
|   | `smtp.requiretls` |   | 부울 |   |
|   | `debug.email` |   | 부울 |   |
|   | `oauth.flow` |   | 부울 |   |
| `org.apache.sling.commons.log.LogManager.factory.config` | `org.apache.sling.commons.log.level` | 예 | 문자열 | &quot;INFO&quot;, &quot;DEBUG&quot; 또는 &quot;TRACE&quot; |
|   | `org.apache.sling.commons.log.names` |   | 문자열 배열 |   |
|   | `org.apache.sling.commons.log.additiv` |   | 부울 |   |
| `com.day.cq.commons.impl.ExternalizerImpl` | `externalizer.domains` | 아니요 | 문자열[] |   |
|   | `externalizer.encodedpath` | 아니요 | 부울 |   |
|   | `externalizer.host` | 아니요 | 문자열 |   |
|   | `externalizer.contextpath` | 아니요 | 문자열 |   |

### OSGi 속성 제한 {#restrictions-osgi-properties}

이러한 OSGi 속성의 값은 아래에 설명된 규칙으로 제한됩니다.

| OSGi 구성 요소 PID |   | 필수 | 유형 | 제한(적용되는 경우) |
|---|---|---|---|---|
| `org.apache.felix.eventadmin.impl.EventAdmin` | `org.apache.felix.eventadmin.ThreadPoolSize` | 예 | 정수 | 2-100 |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | 더블 | -- |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | 정수 | -- |
|   | `org.apache.felix.eventadmin.RequireTopic` |   | 부울 | -- |
|   | `org.apache.felix.eventadmin.IgnoreTimeout` | 예 | 문자열 배열 | `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*`을(를) 적어도 모두 포함해야 합니다. |
|   | `org.apache.felix.eventadmin.IgnoreTopic` |   | 문자열 배열 | -- |
| `org.apache.felix.http` | `org.apache.felix.http.timeout` |   | 정수 |   |
|   | `org.apache.felix.http.session.timeout` |   | 정수 |   |
|   | `org.apache.felix.http.jetty.threadpool.max` |   | 정수 |   |
|   | `org.apache.felix.http.jetty.headerBufferSize` |   | 정수 |   |
|   | `org.apache.felix.http.jetty.requestBufferSize` |   | 정수 |   |
|   | `org.apache.felix.http.jetty.responseBufferSize` |   | 정수 |   |
|   | `org.apache.felix.http.jetty.maxFormSize` |   | 정수 |   |
|   | `org.apache.felix.https.jetty.session.cookie.httpOnly` |   | 부울 |   |
|   | `org.apache.felix.https.jetty.session.cookie.secure` |   | 부울 |   |
|   | `org.eclipse.jetty.servlet.SessionIdPathParameterName` |   | 문자열 |   |
|   | `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding` |   | 부울 |   |
|   | `org.eclipse.jetty.servlet.SessionCookie` |   | 문자열 |   |
|   | `org.eclipse.jetty.servlet.SessionDomain` |   | 문자열 |   |
|   | `org.eclipse.jetty.servlet.SessionPath` |   | 문자열 |   |
|   | `org.eclipse.jetty.servlet.MaxAge` |   | 정수 |   |
|   | `org.eclipse.jetty.servlet.SessionScavengingInterval` |   | 정수 |   |
|   | `org.apache.felix.jetty.gziphandler.enable` |   | 부울 |   |
|   | `org.apache.felix.jetty.gzip.minGzipSize` |   | 정수 |   |
|   | `org.apache.felix.jetty.gzip.compressionLevel` |   | 정수 |   |
|   | `org.apache.felix.jetty.gzip.inflateBufferSize` |   | 정수 |   |
|   | `org.apache.felix.jetty.gzip.syncFlush` |   | 부울 |   |
|   | `org.apache.felix.jetty.gzip.excludedUserAgents` |   | 문자열 |   |
|   | `org.apache.felix.jetty.gzip.includedMethods` |   | 문자열 배열 |   |
|   | `org.apache.felix.jetty.gzip.excludedMethods` |   | 문자열 배열 |   |
|   | `org.apache.felix.jetty.gzip.includedPaths` |   | 문자열 배열 |   |
|   | `org.apache.felix.jetty.gzip.excludedPaths` |   | 문자열 배열 |   |
|   | `org.apache.felix.jetty.gzip.includedMimeTypes` |   | 문자열 배열 |   |
|   | `org.apache.felix.http.session.invalidate` |   | 부울 |   |
|   | `org.apache.felix.http.session.container.attribute` |   | 문자열 배열 |   |
|   | `org.apache.felix.http.session.uniqueid` |   | 부울 |   |
| `org.apache.sling.scripting.cache` | `org.apache.sling.scripting.cache.size` | 예 | 정수 | >= 2048 |
|   | `org.apache.sling.scripting.cache.additional_extensions` | 예 | 문자열 배열 | 은(는) &quot;js&quot;를 포함해야 합니다 |
| `org.apache.sling.engine.impl.log.RequestLogger` | `request.log.output` | 아니요 | 문자열 |   |
|   | `request.log.outputtype` | 아니요 | 문자열 |   |
|   | `request.log.entry.format` | 아니요 | 문자열 |   |
|   | `request.log.exit.format` | 아니요 | 문자열 |   |
|   | `request.log.enabled` | 아니요 | 문자열 |   |
|   | `access.log.output` | 아니요 | 문자열 |   |
|   | `access.log.outputtype` | 아니요 | 문자열 |   |
|   | `access.log.enabled` | 아니요 | 문자열 |   |
| `org.apache.sling.servlets.resolver.SlingServletResolver` | `servletresolver.servletRoot` | 아니요 | 문자열 |   |
|   | `servletresolver.cacheSize` | 아니요 | 정수 |   |
|   | `servletresolver.paths` | 아니요 | 문자열[] |   |
|   | `servletresolver.defaultExtensions` | 아니요 | 문자열 |   |
|   | `servletresolver.mountProviders` | 아니요 | 부울 |   |
|   | `servletresolver.scriptUser` | 아니요 | 문자열 | 더 이상 사용되지 않음, 사용 안 함 |

## Java 버전 21 런타임 업데이트 {#java-runtime-update-21}

Adobe Experience Manager as a Cloud Service이 Java 21 런타임으로 전환되었습니다. 호환성을 보장하려면 [런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)에 명시된 라이브러리 버전을 업데이트해야 합니다.

