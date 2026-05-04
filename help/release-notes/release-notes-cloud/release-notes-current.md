---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: eff4f08ec399314df49246eb7431f5b100493780
workflow-type: tm+mt
source-wordcount: '2054'
ht-degree: 30%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Cloud Service] 현재 기능 릴리스(2026.4.0)인 [!DNL Adobe Experience Manager]의 릴리스 날짜는 2026년 4월 30일입니다. 다음 기능 릴리스(2026.5.0)는 2026년 5월 28일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 
## Release Video {#release-video}

Have a look at the April 2026 Release Overview video for a summary of the features added in the 2026.4.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3483060/?quality=12)
-->

## AEM Beta 프로그램 {#aem-beta-programs}

Adobe Experience Manager(AEM) 베타 프로그램은 고객이 프리릴리스 기능과 코드에 액세스하고, 피드백을 제공하고, AEM의 미래를 안내할 수 있는 방법입니다.

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

**참여의 이점**

Adobe이 개발 중인 기능에 일찍 액세스하면 고객과 파트너가 피드백을 제공하고 제품 개발을 구체화할 수 있습니다. 또한 GA 전에 새로운 기능을 채택할 준비를 하는 데 도움이 됩니다.

**현재 베타 프로그램**

다음 섹션에는 활성 Beta 프로그램이 나와 있습니다.

### AEM의 에이전트 {#agents-in-aem}

프로덕션, 거버넌스, 최적화, 검색 및 개발 전반에 걸쳐 강력하고 새로운 AEM 에이전트 기능을 살펴보려면 [여기에서 액세스하는 방법에 대해 알아보십시오.](/help/ai-in-aem/agents/overview.md)

<!--
### Agents in AEM (Explorer program) {#agents-in-aem-beta-program}

Gain early access to powerful, new AEM agentic capabilities across production, governance, optimization, discovery, and development. Your feedback directly shapes Adobe's roadmap and final features. See [Overview of Agents in AEM](/help/ai-in-aem/agents/overview.md) to learn more.

This program typically lasts 4-6 weeks, but can be tailored to be flexible around your ability to actively participate. 

To opt in to participate in this program, email [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com) and include the following details to the extent possible:

* Names and Adobe ID's of team members who will actively use agents.
* List Specific agents that you or your team will want to use. Or simply say "All Agents."

Customers selected for participation will be notified directly by Adobe. Participation is subject to eligibility considerations, including customer licensing and limited program capacity. While not all requests can be accommodated initially, additional customers may be considered in future beta waves.
-->

### AEM Foundation(Beta 프로그램) {#aem-foundation-beta-programs}

[AEM Foundation Beta 프로그램](#foundation-early-adopter)을 참조하세요.

### Cloud Manager (Beta 프로그램) {#cloud-manager-beta-programs}

[Cloud Manager 베타 프로그램](/help/implementing/cloud-manager/release-notes/current.md)을 참조하세요.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### AI 번역 통합 {#ai-translation-integration}

이제 AEM 사용자는 콘텐츠 번역을 위해 LLM(Large Language Model)을 활용하여 사람 번역 품질을 기계 번역 속도로 제공할 수 있습니다. 기존 타사 번역 서비스와 유사하게, Azure OpenAI는 AEM에서 번역 공급업체로 구성할 수 있으며 향후 릴리스에 예정된 추가 LLM에 대한 지원을 제공합니다. 고객은 이 기능을 위해 자체 LLM 라이센스를 사용합니다. 또한 기업 번역 스타일 가이드를 AEM에 업로드하여 번역 규칙을 추출하여 브랜드와 스타일의 일관성을 보장할 수 있습니다. 자세한 내용은 [AI 번역 통합 구성](/help/sites-cloud/administering/translation/ai-translation-integration.md)을 참조하십시오.

### 콘텐츠 조각 편집기 {#cf-editor}

이제 새로운 콘텐츠 조각 편집기를 사용하여 콘텐츠 조각의 JSON 표현식을 미리 볼 수 있습니다. 이렇게 하면 렌더링과 관계없이 콘텐츠 구조를 확인하고 이 기능에 대해 AEM Touch UI의 이전 콘텐츠 조각 편집기와의 패리티를 복원하는 데 도움이 됩니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**이제 Adobe Workfront 및 Adobe 이외의 애플리케이션에 콘텐츠 관리자를 사용할 수 있습니다**

이제 Adobe Workfront 및 타사 애플리케이션에서 Content Advisor를 사용할 수 있으므로 지능형 에셋 검색 및 콘텐츠 재사용이 Adobe Express 및 AEM Sites 이상으로 확장됩니다. 이 릴리스에서는 AI 기반 검색, 컨텍스트 인식 권장 사항, 캠페인 개요 기반 검색, Dynamic Media 렌디션에 대한 액세스, 콘텐츠 조각 검색, 필터 및 Adobe Workfront 워크플로 및 외부 애플리케이션에 대한 에셋 메타데이터를 비롯한 전체 콘텐츠 관리자 경험을 제공합니다.

이제 선호하는 애플리케이션 내에서 AEM Assets에서 승인된 에셋을 직접 검색, 평가 및 재사용할 수 있으므로, Adobe 및 비 Adobe 애플리케이션 모두에서 일관된 에셋 사용, 효율성 향상 및 간소화된 콘텐츠 생성이 가능합니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 기능

* **OSGi로 reCAPTCHA 클라우드 구성 재정의** 
소스 파일과 함께 보관하는 reCAPTCHA Enterprise 프로젝트 ID, 사이트 키 및 비밀은 [컨텍스트 인식 구성 재정의를 추가하고 Cloud Manager을 통해 배포](/help/forms/captcha-adaptive-forms.md#override-recaptcha-osgi)한 후 각 Cloud Service 환경에서 다른 값으로 확인할 수 있습니다.

* **인증서 기반 인증** 
Microsoft SharePoint 목록에 제출하는 적응형 Forms은 이제 OAuth URL 인증과 함께 [인증서 기반 인증](/help/forms/connect-forms-to-sharepoint-list.md#certificate-based-authentication)을 지원합니다. 인증서 기반 로그인의 경우 AEM 및 Microsoft Azure에서 인증서 별칭 및 테넌트 세부 정보를 등록합니다.

* **규칙 편집기 개선 사항**

   * 이제 적응형 Forms 규칙 편집기는 [기본 제공(OOTB) 트리거와 사용자 지정 이벤트](/help/forms/rule-editor-enhancements-use-cases.md#simplified-grammar-for-ootb-and-custom-events)에 대한 발송 이벤트 및 트리거 시 이벤트 규칙에 대한 간소화된 문법을 지원하므로 작성자는 사용자 지정 트리거에 대한 문법으로만 국한되지 않습니다.
   * 이제 핵심 구성 요소를 기반으로 하는 적응형 Forms에 대한 규칙에 AND 또는 OR 논리[&#128279;](/help/forms/rule-editor-enhancements-use-cases.md#combined-when-conditions-with-the-file-attachment-component)를 사용하는 다른 조건과 함께 파일 첨부 구성 요소가 포함되면, 규칙은 첨부 파일 상태와 다른 검사가 모두 의도한 대로 평가될 때만 해당 작업을 실행합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 새 기능 {#foundation-new}

#### AEM Java 및 Dispatcher 개발을 위한 IDE AI 도구 {#ai-dev}

Java 스택 팀은 기능 전달 속도를 높이고 코드 품질을 개선하기 위해 Cursor, Claude Code, Visual Studio 및 IntelliJ와 같은 도구에서 AI 지원 개발을 점점 더 많이 사용하고 있습니다.

코딩 에이전트는 IDE 도구를 사용하여 AEM 코드 및 Dispatcher 구성을 생성하고 디버깅할 수 있습니다. 한 가지 예로서, 아래 비디오 연습에서는 에이전트 기술을 사용하여 AEM 구성 요소를 빌드하는 방법을 보여 줍니다.

[AI 도구를 사용한 로컬 개발](/help/ai-in-aem/local-development-with-ai-tools.md)에 대해 자세히 알아보고 [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com)에 질문이나 피드백을 언제든지 이메일로 보내주십시오.


>[!VIDEO](https://video.tv.adobe.com/v/3484978/?learn=on&enablevpops)

#### Experience Governance MCP 서버 {#gov-mcp-server}

Experience Governance MCP Server는 이제 GA(일반적으로 사용 가능)되었습니다. MCP(Model Context Protocol)를 지원하는 AI 개발자 도구 및 챗봇과 통합되어 챗봇 또는 IDE에서 자연어 프롬프트를 사용하여 브랜드 무결성 및 규정 준수를 보호할 수 있습니다. 브랜드 거버넌스 규칙에 대해 콘텐츠(텍스트, 이미지, 페이지)를 평가하고 브랜드 구성 및 사용 가능한 거버넌스 검사를 검색할 수 있습니다.

[AEM MCP 서버](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md) 및 [거버넌스 에이전트](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/ai-in-aem/agents/governance/overview)에 대해 자세히 알아보세요.


>[!VIDEO](https://video.tv.adobe.com/v/3486258/?learn=on&enablevpops)

#### 클라우드 커넥터 {#aem-claude-connector}

클라우드 사용자는 Anthropic의 [커넥터 마켓플레이스](https://claude.ai/settings/connectors)를 탐색하여 [Adobe Experience Manager 커넥터 설치](/help/ai-in-aem/mcp-support/setup-claude.md#aem-claude-connector)를 한 번 클릭할 수 있습니다. 이 MCP 서버는 프롬프트를 통한 콘텐츠 편집을 포함하여 AEM과 상호 작용하는 점점 더 많은 도구를 노출합니다.

#### AEM OIDC - 새로운 기능 게시 {#aem-oidc-on-publish-new-features}

* 수정: 원래 요청의 쿼리 매개 변수는 인증 후 손실됨
* OIDC 인증 [설명서](/help/security/open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier.md#custom-redirect-after-authentication)에서 인증 후 사용자 지정 리디렉션

#### Microsoft Graph API에 대한 메일 서비스 지원 {#mail-service-graph-api}

이제 AEM의 메일 서비스는 Microsoft Graph API를 사용하여 Microsoft® Outlook(Microsoft 365를 통해)을 지원합니다. 이 기능은 메일 서비스에서 이미 지원되는 SMTP를 허용하지 않는 조직에 특히 유용합니다. 인증은 OAuth 2.0을 통해 수행됩니다. [구성 방법을 알아보세요](/help/security/oauth2-support-for-mail-service.md#microsoft-graph-api).

#### CDN 로그를 Sumo 논리에 전달할 수 있습니다. {#sumo-cdn-logforwarding}

이제 [로그 전달 기능](/help/implementing/developing/introduction/log-forwarding.md#sumologic)에서 CDN 로그를 Sumo 논리에 보낼 수 있습니다. 이전에는 Sumo Logic으로의 로그 전달이 AEM 로그로 제한되었습니다.

### [!DNL Cloud Service] Foundation 중요 알림으로서의 [!DNL Experience Manager] {#foundation-notices}

#### IMS 인증 리치 오류 {#ims-auth-rich-errors}

IMS 통합 문제를 해결하기 위해 `imsauth`에서 *다양한 오류*&#x200B;에 대한 지원을 추가했습니다.

이러한 오류는 HTTP 상태 코드만 반환하는 대신 인증 및 액세스를 차단할 수 있는 문제를 진단하고 해결하는 데 도움이 되는 추가 컨텍스트를 제공합니다.

#### Java API 사용 중단 {#java-api-deprecation}

더 이상 사용되지 않는 API의 사용을 제거하는 것이 중요합니다.

**4월 14** 이후, 2/26/2026 제거를 대상으로 하는 API를 사용하여 코드를 포함하는 Cloud Manager 파이프라인이 코드 품질&#x200B;**단계에서 실패했습니다.** 더 이상 사용되지 않는 API 사용이 제거될 때까지 배포가 차단됩니다. *시간이 중요한 업데이트를 릴리스할 수 없으며 비즈니스 운영에 영향을 줄 수 있습니다.*

**2026년 6월 11일**&#x200B;부터 더 이상 사용되지 않는 API를 계속 사용하는 환경은 중요한 Adobe 릴리스 업데이트를 받지 않습니다&#x200B;**. 따라서 성능 및 가용성에 대한 Adobe의 표준 약정이 적용되지 않습니다.**&#x200B;그 결과, 새로운 기능이나 버그 수정을 받지 않고, 애플리케이션 안정성과 가동 시간에 부정적인 영향을 미치고, 보안 위험 노출이 더 증가할 수 있습니다.

[사용 중단 문서](/help/release-notes/deprecated-removed-features.md#aem-apis)에서 자세한 내용을 확인할 수 있으며, 편의를 위해 아래에 해당 API 목록을 제공합니다.

+++ 확장하여 사용 중단 Java API 보기

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 얼리 어답터 기능 {#foundation-early-adopter}

#### AEM Edge 기능(Beta 프로그램) {#edge-functions}

[AEM Edge 함수](/help/implementing/developing/introduction/edge-functions.md)를 사용하면 CDN 계층에서 JavaScript을 실행하여 최종 사용자에게 더 가까운 데이터 처리를 제공할 수 있습니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 브라우저에 제공하기 전에 서드파티 API의 응답(및 여러 API 응답 집계)을 다시 포맷
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공
* 사용자 정의 도구에 액세스하기 위해 ChatGPT 및 Cloud와 같은 AI 지원자용 MCP 서버 노출

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

#### 웹 계층 구성 파이프라인 문제 해결(Beta 프로그램) {#devagent-webtier}

개발 에이전트의 [파이프라인 문제 해결](/help/ai-in-aem/agents/brand-experience/development/development.md) 기능을 사용하면 개발자가 AEM as a Cloud Service 배포에서 문제를 효율적으로 진단하고 해결할 수 있습니다. 개발 에이전트는 이제 전체 스택 파이프라인(배포 및 코드 품질)을 지원하는 것 외에도 Beta 프로그램의 일부로 **웹 계층 구성 파이프라인**&#x200B;에 대한 문제 해결을 지원합니다.

Beta에 대한 액세스를 요청하려면 [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com)에 전자 메일을 보내십시오. AEM의 에이전트에 대한 기존 액세스 권한이 필요합니다.

#### 복제 AI 문제 해결(Alpha 프로그램) {#replication-ai-troubleshooting-alpha}

AEM 작성자 및 기타 인터페이스에서 AI Assistant를 사용하여 차단된 대기열과 같은 복제 관련 문제를 해결할 수 있습니다. Alpha 프로그램에 참여하려면 [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com)로 전자 메일을 보내 관심 분야를 설명하십시오.

#### AEM 6.5에서 AEM Cloud Service로 마이그레이션하기 위한 IDE AI 도구(Beta 프로그램) {#cm-ide-migration}

IDE AI 도구를 사용하여 [모범 사례 분석기 보고서](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)의 권장 사항에 따라 활동하여 AEM 6.5에서 AEM as a Cloud Service(Java 스택)으로 마이그레이션을 가속화하십시오.

자세한 정보를 확인하고 기능에 대한 액세스를 요청하려면 [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com)에 전자 메일을 보내십시오.

#### Edge Delivery Services에 대한 Edge 인증(Beta 프로그램) {#edge-authentication}

Edge 인증을 사용하면 ID 공급자(IdP)로 인증된 사용자만 Edge Delivery Services 페이지에 액세스하도록 제한할 수 있습니다. 이 작업은 OpenID Connect(OIDC) 구성 YAML 파일을 배포하는 방법으로 수행됩니다.

원하는 경우 사용 사례에 대한 간단한 설명과 질문을 담은 이메일을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 보내십시오.

#### 라이브 트래픽을 수락하기 전에 코드 테스트를 위한 카나리아 프로덕션 배포(Beta 프로그램) {#canary-beta}

최종 사용자에게 노출하기 전에 내부용 테스트 트래픽으로 프로덕션 빌드의 유효성을 검사합니다. 프로덕션으로 배송하고, 카나리아 트래픽만 라우팅하고(특수 헤더 사용), 동작을 모니터링한 다음 라이브 트래픽으로 승격하거나 고객에게 영향을 주지 않고 롤백합니다.

액세스를 요청하고 피드백을 공유하려면 [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com)에 이메일을 보내십시오.

#### RDE용 스냅샷(Beta 프로그램) {#rde-snapshot-program}

Beta에서 RDE(빠른 개발 환경)는 이제 코드 및 콘텐츠의 현재 상태에 대한 스냅숏을 만드는 기능 [을(를) 지원하며](/help/implementing/developing/introduction/rapid-development-environments.md#snapshots)은(는) 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 사용 및 피드백 제공에 관심이 있는 경우 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)에 전자 메일을 보내십시오.

#### 애플리케이션 성능 모니터링(APM) 기능 확장(Alpha 프로그램) {#apm-alpha}

AEM Cloud Service는 가시성 확보를 위해 현재 Adobe에서 제공하는 [New Relic One](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) 및 고객이 관리하는 [Dynatrace](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace)를 지원합니다. 추가 APM 옵션에 대한 지원을 살펴볼 때 사용 사례와 함께 선호하는 공급업체 또는 기술을 명시한 이메일을 [aemcs-apm-beta@adobe.com](mailto:aemcs-apm-beta@adobe.com)에 보내십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
