---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: cf45f9e6d89e0a166c09989b0fc8e793a54ce9ff
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 41%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2026.1.0) 일자는 2026년 1월 29일 금요일입니다. 다음 기능 릴리스(2026.2.0)는 2026년 2월 26일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2026년 1월 릴리스 개요 비디오를 통해 2026.1.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3479796/?captions=kor&quality=12)


## AEM Beta 프로그램 {#aem-beta-programs}

Adobe Experience Manager(AEM) 베타 프로그램은 고객이 프리릴리스 기능과 코드에 액세스하고, 피드백을 제공하고, AEM의 미래를 안내할 수 있는 방법입니다.

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

**참여의 이점**
Adobe이 개발 중인 기능에 일찍 액세스하면 고객과 파트너가 피드백을 제공하고 제품 개발을 구체화할 수 있습니다. 또한 GA 전에 새로운 기능을 채택할 준비를 하는 데 도움이 됩니다.

**현재 베타 프로그램**
다음 섹션에는 활성 Beta 프로그램이 나와 있습니다.

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

### 컨텐츠 MCP 서버 {#content-MCP}

AEM Cloud Service에는 이제 **콘텐츠 MCP 서버**&#x200B;가 포함되어 있으며, MCP 호환 도구를 통해 AI 기반 경험이 AEM 콘텐츠와 작동하는 표준화된 방법을 제공합니다.

채팅 앱 및 에이전트 플랫폼에서 작업하는 개발자 및 고급 사용자는 AEM을 사용자 정의 지표 및 자동화에 연결할 수 있으므로 콘텐츠 작업은 전체적인 비즈니스 워크플로의 일부가 됩니다.

AEM은 두 개의 서버를 제공합니다.

1. **읽기 전용 콘텐츠 MCP 서버** - 콘텐츠를 안전하게 검색하기 위한
1. **콘텐츠 읽기/쓰기 MCP 서버** - 콘텐츠 변경

이러한 MCP 서버에는 **페이지**, **콘텐츠 조각** 및 **Assets** 작업 도구가 포함되어 있으며 **ChatGPT**, **클라우드**, **커서** 및 **Microsoft Copilot Studio** MCP 클라이언트에서 사용할 수 있습니다.

자세한 내용은 [AEM Cloud Service와 MCP 사용](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md)을 참조하세요. 질문이나 피드백이 필요하면 [aemcs-mcp-feedback@adobe.com](mailto:aemcs-mcp-feedback@adobe.com)로 전자 메일을 보내세요.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**AI 검색**

AI 검색은 사용자 쿼리 뒤의 의미와 의도를 파악하여 기존의 키워드 일치를 넘어서는 지능적인 컨텍스트 인식 검색 경험을 제공합니다. AI와 머신 러닝을 기반으로, 쿼리가 다르게 표현되거나, 철자가 틀리거나, 동의어를 사용하거나, 다른 언어로 제출되는 경우에도 보다 정확한 결과를 제공하여 사용자가 적은 노력으로 관련 콘텐츠를 더 빨리 찾을 수 있도록 지원합니다.

자세한 내용은 [Assets 보기](/help/assets/search-assets-view.md#ai-search) 및 [관리자 보기](/help/assets/search-assets.md#ai-search)의 AI 검색을 참조하십시오.

**데스크톱 앱 3.0.1 릴리스**

[데스크톱 앱 3.0.1(2025년 12월 20일)](https://experienceleague.adobe.com/ko/docs/experience-manager-desktop-app/using/release-notes)은(는) 주요 워크플로에서 안정성, 성능 및 안정성을 향상시킵니다. 이 릴리스는 AEM 작성자의 동기화 문제를 수정하여 일관된 폴더 이름 지정을 보장하고, 활성 전송 중 앱을 중단 없이 사용할 수 있으며, 비동기 처리를 통해 UI 응답성을 향상하고, 페이지 매김으로 대규모 파일 전송을 최적화하며, 대규모 폴더 업로드 및 다운로드 중 작성자 서버 다시 시작 및 충돌을 비롯한 안정성 문제를 해결합니다.

**Adobe Asset Link CEP 2026.01.0 릴리스**

[Adobe Asset Link CEP 2026.01.0](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)에서는 동일한 AEM 폴더에서 누락된 다른 자산을 자동으로 다시 연결하는 새로운 InDesign 누락 링크 다시 연결 옵션을 도입했습니다. 이 기능은 파일 이름을 기반으로 하는 에셋과 일치하므로 끊어진 링크를 복원할 때 수작업이 크게 줄어듭니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

**적응형 Forms(Foundation 구성 요소)의 각주 자리 표시자 개선 사항**

* 줄 바꿈이 있는 [여러 줄 지원을 추가했습니다](/help/forms/footnotes-richtextsupport.md). 따라서 각주 콘텐츠를 보다 명확하고 표현적으로 표시할 수 있습니다.
* 이제 각주는 연결된 패널의 가시성에 관계없이 각주 플레이스홀더 내에서 지속적으로 볼 수 있으므로 중요한 정보에 일관되게 액세스할 수 있습니다.
  ![각주 설명](/help/forms/assets/footnote-description.png){height=50%}

### AEM Forms의 새로운 얼리 액세스 기능 {#forms-new-early-access-features}

**JSON 배열에서 값 검색**

사용자 지정 함수 기능을 [JSON 배열에서 값을 추출](/help/forms/invoke-service-enhancements-rule-editor.md#retrieve-property-values-from-a-json-array)(API 호출을 통해 수신)하는 것으로 확장했으며 적응형 양식 필드에 직접 바인딩했습니다. 이제 최소한의 수동 데이터 매핑으로 비즈니스 논리 및 규칙을 개발할 수 있습니다.

**게시 인스턴스에서 연결 UI 실행**

이제 게시 인스턴스에서 직접 [UI 연결](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)을 실행할 수 있습니다. 이를 통해 에이전트는 연결 UI에 액세스하고 고객을 위한 커뮤니케이션을 쉽게 개인화할 수 있습니다.

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. 
-->

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] Foundation 중요 알림으로서의 [!DNL Cloud Service] {#foundation-notices}

#### Java API 사용 중단 {#java-api-deprecation}

2026/2/26/2026 제거를 대상으로 하는 더 이상 사용되지 않는 API는 코드에서 더 이상 사용되지 않아야 합니다. 배포 블록을 방지하려면 2026년 3월 26일 이전에 API 사용을 제거하십시오. 중요 날짜:

* **2026년 1월 26일부터**: 작업 센터 알림 전자 메일이 **환경당 매주**&#x200B;에 이러한 API 사용을 제거하기 위한 미리 알림으로 전송됩니다.
* **2026년 2월 26일**: 이러한 API를 사용하는 코드가 포함된 Cloud Manager 파이프라인은 **코드 품질** 단계 동안 **일시 중지**&#x200B;됩니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인을 진행할 수 있도록 문제를 재정의할 수 있습니다.
* **2026년 3월 26일**: 이러한 API를 사용하는 코드가 포함된 Cloud Manager 파이프라인은 **코드 품질** 단계 동안 **실패**&#x200B;되며, 사용이 제거될 때까지 새 코드의 **배포를 차단**&#x200B;합니다.
* **2026년 4월 30일**: 이러한 API를 계속 사용하는 환경은 **더 이상 중요한 Adobe 릴리스 업데이트를 받지 못할 수 있습니다**.

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
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

#### Java 11 런타임 사용 중단 {#java11-runtime-deprecation}

Adobe은 2025년 10월 14일에 **Stage** 및 **Production** 환경을 더 높은 성능의 **Java 21 런타임**(으)로 업그레이드했습니다. **2월 9일**(2월 11일까지 점진적 롤아웃)부터 AEM Cloud Service SDK과 클라우드 환경 모두 Java 11 런타임과 작동하지 않습니다.

>[!NOTE]
>
> 최신 성능 최적화 및 언어 개선 사항을 활용하려면 Java 17 또는 Java 21(권장)로 빌드하는 것이 좋습니다. Java 8 및 Java 11을 사용한 빌드는 현재 지원되지만 향후 릴리스에서는 더 이상 사용되지 않을 예정입니다. 사용 중단에 앞서 별도의 커뮤니케이션이 이루어집니다. *이 문서*&#x200B;의 [빌드 시간 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 섹션을 참조하십시오.
>

#### AEM Java 로그 구성 시행 {#logconfig-policy}

AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하려면 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

지원되지 않는 사용자 지정 로깅 재정의 *이(가) 이제 무시됩니다*. 대부분의 고객은 영향을 받지 않았으며 Adobe은 현재 구성이 영향을 받을 수 있는 고객에게 연락했습니다.

사용자 정의 로깅 동작에 의존하는 모든 다운스트림 프로세스를 검토하고 업데이트해 주시기 바랍니다. 예:

* 로그 전달 시스템이 사용자 정의 로그 형식을 기대하는 경우, 수집 규칙을 조정해야 할 수도 있습니다.
* 이전에 로그 수준을 변경하여 로그의 세부 정보를 줄인 적이 있는 경우 기본 수준으로 되돌리면 로그 볼륨이 증가할 수 있습니다.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 얼리 어답터 기능 {#foundation-early-adopter}

#### 자동 유지 관리 업데이트 일시 중지 {#pause-updates}

라이브 기간, 라이브 이벤트, 최대 매출 등의 순간은 중단되어서는 안 됩니다. [새로운 셀프 서비스 기능](/help/implementing/deploying/quiet-hours-update-free-periods.md)은 중요한 순간에 자동 유지 관리 업데이트를 중지하므로 팀은 집중 상태를 유지할 수 있습니다.

* 사용 중지 시간: 매일 설정된 시간 동안 자동 유지 관리를 차단합니다. 업무 시간, 야간 작동 또는 오전 컷오버에 이상적입니다.
* 업데이트 불가 기간: 일주일 내내 자동 유지 관리를 차단합니다. 출시, 프로모션 또는 연례 중지 기간에 사용합니다.

>[!NOTE]
>
>9월 25일에 제한 공개 기능으로 사용 가능합니다.
>프로그램에서 활성화하려면 [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com)에 이메일을 보내십시오.
>

#### AEM Edge 기능(Beta 프로그램) {#edge-functions}

AEM Edge 기능(*Edge 컴퓨팅*)을 사용하면 CDN 계층에서 JavaScript을 실행하여 데이터 처리를 최종 사용자에게 더 가깝게 할 수 있습니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 브라우저에 제공하기 전에 서드파티 API의 응답(및 여러 API 응답 집계)을 다시 포맷
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공
* ChatGPT 및 Claude와 같은 LLM을 위한 MCP 서버를 사용자 정의 도구에 액세스하도록 노출

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

#### Edge Delivery Services에 대한 Edge 인증(Beta 프로그램) {#edge-authentication}

Edge 인증을 사용하면 ID 공급자(IdP)로 인증된 사용자만 Edge Delivery Services 페이지에 액세스하도록 제한할 수 있습니다. 이 작업은 OpenID Connect(OIDC) 구성 YAML 파일을 배포하는 방법으로 수행됩니다.

원하는 경우 사용 사례에 대한 간단한 설명과 질문을 담은 이메일을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 보내십시오.

#### 라이브 트래픽을 수락하기 전에 코드 테스트를 위한 카나리아 프로덕션 배포(Beta 프로그램) {#canary-beta}

최종 사용자에게 노출하기 전에 내부용 테스트 트래픽으로 프로덕션 빌드의 유효성을 검사합니다. 프로덕션으로 배송하고, 카나리아 트래픽만 라우팅하고(특수 헤더 사용), 동작을 모니터링한 다음 라이브 트래픽으로 승격하거나 고객에게 영향을 주지 않고 롤백합니다.

코드 릴리스를 프로덕션에 배포하되, 라이브 트래픽을 수락할지 아니면 롤백할지 여부를 결정하기 전에 내부 테스트 트래픽으로만 이를 제한합니다.

액세스를 요청하고 피드백을 공유하려면 [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com)에 이메일을 보내십시오.

#### RDE용 스냅샷(Beta 프로그램) {#rde-snapshot-program}

Beta에서 RDE(빠른 개발 환경)는 이제 코드 및 컨텐츠의 현재 상태에 대한 스냅샷을 생성하는 기능을 지원하며 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 사용 및 피드백 제공에 관심이 있는 경우 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)에 전자 메일을 보내십시오.

#### AEM Java 및 Dispatcher 개발용 IDE에 대한 AI 도구(Beta 프로그램) {#ai-dev-beta}

Java 스택 팀은 기능 전달 속도를 높이고 코드 품질을 개선하기 위해 Cursor, Claude Code, Visual Studio 및 IntelliJ와 같은 도구에서 AI 지원 개발을 점점 더 많이 사용하고 있습니다. Beta에 참여하여 다음을 수행할 수 있습니다.

* 실제 경험을 공유하여 미래의 Adobe 지원 AI 기능을 구체화합니다.
* AI 에이전트가 AEM 코드 및 Dispatcher 구성을 생성하고 디버깅하는 데 사용할 수 있는 IDE 도구를 사용해 보십시오

자세한 내용은 [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)(으)로 전자 메일을 보내십시오.

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

기타 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
