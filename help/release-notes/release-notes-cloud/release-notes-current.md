---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: ed358f58ba0dd4d5a9b283291702f867774515e4
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 49%

---

# [!DNL Adobe Experience Manager] as a Cloud Service의 최신 릴리스 정보 {#release-notes}

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.12.0) 일자는 2025년 12월 11일 금요일입니다. 다음 기능 릴리스(2026.1.0)는 2026년 1월 29일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440927?captions=kor&quality=12)

-->

## AEM 베타 프로그램 {#aem-beta-programs}

Adobe Experience Manager(AEM) 베타 프로그램은 고객이 프리릴리스 기능과 코드에 액세스하고, 피드백을 제공하고, AEM의 미래를 안내할 수 있는 방법입니다.

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

**참여의 이점**
Adobe이 개발 중인 기능에 일찍 액세스하면 고객과 파트너가 피드백을 제공하고 제품 개발을 구체화할 수 있습니다. 또한 GA 전에 새로운 기능을 채택할 준비를 하는 데 도움이 됩니다.

**현재 베타 프로그램**
다음 섹션에는 활성 Beta 프로그램이 나와 있습니다.

### AEM의 에이전트(Beta 프로그램) {#agents-in-aem-beta-program}

프로덕션, 거버넌스, 최적화, 검색 및 개발 전반에 걸쳐 강력하고 새로운 AEM 에이전트 기능에 신속하게 액세스할 수 있습니다. 귀하의 피드백은 Adobe의 로드맵과 최종 기능을 직접 만듭니다. 자세한 내용은 [AEM의 에이전트 개요](/help/ai-in-aem/agents/overview.md)를 참조하십시오.

이 프로그램은 일반적으로 4~6주 동안 진행되지만 능동적으로 참여할 수 있는 능력을 중심으로 유연하게 조정할 수 있습니다.

이 프로그램에 참여하도록 옵트인하려면 [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com)에 전자 메일을 보내고 가능한 범위 내에서 다음 세부 정보를 포함하십시오.

* 에이전트를 적극적으로 사용할 팀원의 이름과 Adobe ID.
* 사용자 또는 팀이 사용할 특정 에이전트를 나열합니다. 아니면 그냥 &quot;모든 요원&quot;이라고 해

### AEM Foundation(Beta 프로그램) {#aem-foundation-beta-programs}

[AEM Foundation Beta 프로그램](#foundation-early-adopter)을 참조하세요.

### Cloud Manager (Beta 프로그램) {#cloud-manager-beta-programs}

[Cloud Manager 베타 프로그램](/help/implementing/cloud-manager/release-notes/current.md)을 참조하세요.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**AEM Assets과의 통합을 위한 새 버전의 Figma 플러그인을 사용할 수 있습니다**

* AEM 저장소에서 Figma 문서로 에셋을 가져오는 동안 비디오 파일(MP4, MOV, WebM), 애니메이션 파일(GIF) 및 벡터 파일(SVG)을 지원합니다.

* AEM 저장소에 있는 에셋과 비교하여 Figure 문서에 사용된 에셋에 대한 업데이트가 있는지 확인하고 업데이트가 있는 경우 최신 버전의 에셋을 가져올 수 있습니다.

* PNG(크기 조절) 및 JPG(이미지 크기 조절 및 품질) 파일 형식을 내보내는 동안 내보내기 구성을 지원합니다.

  ![Figma 플러그인](/help/assets/assets/figma-v2-plugin.png)

**업로드된 자산에 대한 맬웨어 검색**

이제 AEM Assets에는 업로드된 파일에 대한 자동 맬웨어 검사가 포함되어 있으므로, 위험으로부터 저장소를 보호하기 위해 DAM에 들어가기 전에 의심스러운 자산이 격리되도록 합니다. 관리자는 스캔 설정 및 격리 보존 정책을 구성하여 보안 제어를 간소화할 수 있습니다.



## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- ### Pre-Release features in AEM Forms 

**Rule Editor Enhancements**

The Rule Editor now supports enhanced navigation and allows use of function and mathematical expressions in input parameters.

**Enhanced Navigation with Event Payload Support**
 
The `Navigate To` action in the Invoke Service handlers now supports `EVENT_PAYLOAD`, enabling form authors to configure follow-up actions based on event responses. This enhancement offers greater flexibility in designing post-submission workflows, ensuring smoother transitions and more personalized user experiences. For more information, see [Enhanced Navigation with Event Payload Support](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Function and Mathematical Expression Support in Input Parameters**
 
Input parameters now support both function calls and mathematical expressions, enabling form authors to pass dynamically computed values directly. This enhancement streamlines rule configurations, eliminates the need for extra fields, and makes forms more adaptable to complex logic and calculation-driven scenarios. For more information, see [Function and Mathematical Expression Support in Input Parameters](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters). -->

### AEM Forms의 새로운 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스하고 개발을 구체화할 수 있는 특별한 기회를 제공합니다.

이들 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### 향상된 대화형 통신 기능

##### 템플릿 잠금

템플릿 내의 콘텐츠 및 레이아웃 요소를 잠궈 브랜드 무결성을 유지하고 무단 수정을 방지합니다. 이를 통해 모든 커뮤니케이션에서 디자인 일관성을 유지할 수 있습니다.

##### 컨텐츠 오버플로 지원

플로우 레이아웃에 대한 &quot;컨텐츠 내에서 페이지 나누기 허용&quot; 옵션을 소개합니다. 이 향상된 기능을 통해 여러 페이지를 매끄럽게 편집하고 복잡한 문서에 대해 더 나은 텍스트 관리를 할 수 있습니다.

##### XDP 파일 편집

대화형 통신 편집기는 이제 조각 통합을 포함하여 XDP 편집을 지원합니다. 이제 Microsoft Windows 데스크톱에서만 실행되는 Forms Designer 대신 브라우저에서 XDP 파일을 편집할 수 있습니다.

##### 동적 페이지 번호 매기기

여러 페이지 문서 간에 명확하고 일관된 페이지 매김을 위해 마스터 페이지에 &quot;##의 페이지 번호&quot;를 자동으로 표시합니다.

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

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 새 기능 {#foundation-new}

#### 곧 Java API 지원 중단 예정 {#java-api-deprecation}

사용되지 않는 몇몇 API는 8월 31일에 삭제될 예정이라고 공지되었으므로 더 이상 참조할 수 없습니다. 코드에서 더 이상 사용되지 않는 API 사용이 감지되면 작업 센터 알림을 받게 되며 1월 29일 이후에는 Cloud Manager 빌드 중에 알림이 표시되어 사용 제거의 중요성을 강화합니다. [사용 중단 문서](/help/release-notes/deprecated-removed-features.md#aem-apis)에서 자세한 내용을 확인할 수 있으며, 편의를 위해 아래에 해당 API 목록을 제공합니다.

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

Adobe은 2025년 10월 14일에 **Stage** 및 **Production** 환경을 더 높은 성능의 **Java 21 런타임**(으)로 업그레이드했습니다. **1월 말**&#x200B;부터 AEM Cloud Service SDK과 클라우드 환경은 모두 Java 11 런타임에서 작동하지 않습니다.

>[!NOTE]
>
> 최신 성능 최적화 및 언어 개선 사항을 활용하려면 Java 17 또는 Java 21(권장)로 빌드하는 것이 좋습니다. Java 8 및 Java 11을 사용한 빌드는 현재 지원되지만 향후 릴리스에서는 더 이상 사용되지 않을 예정입니다. 사용 중단에 앞서 별도의 커뮤니케이션이 이루어집니다. *이 문서*&#x200B;의 [빌드 시간 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 섹션을 참조하십시오.
>

#### AEM Java 로그 구성 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급된 대로 AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

**1월 29일**&#x200B;부터 지원되지 않는 사용자 지정 로깅 무시가 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 현재 구성에 영향을 받을 수 있는 고객에게는 Adobe에서 개별적으로 안내를 드렸습니다.

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

#### 에지 컴퓨팅 (Beta 프로그램)

에지 컴퓨팅을 사용하면 CDN 계층에서 JavaScript를 실행할 수 있어 데이터 처리가 최종 사용자에게 더 가까워집니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

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


#### AI 답변 - AEM Sites(Beta 프로그램)에 대한 스마트하고 컨텍스트 인식 응답 {#ai-answers-beta}

AI 답변에서는 방문자가 콘텐츠와 상호 작용할 수 있는 새로운 방법을 소개합니다. RAG(Retrieval-Augmented Generation) 기술을 기반으로 하는 이 솔루션은 AEM 관리 데이터를 사용하여 디지털 환경 내에서 정확하고 일관된 답변을 직접 제공합니다.

AI Answers Beta 프로그램 출시를 준비하고 있으며, 이제 고객을 초대하여 관심 사항을 등록하고자 합니다. 베타는 용량이 매우 제한적이기 때문에 조기 가입이 우선적 고려를 받게 된다. Beta에 참여하면 AEM 클라우드 서비스 환경에서 AI 답변을 탐색하고, 성능과 정확성을 검증하며, 향후 사용 환경을 미리 구체화할 수 있습니다.

참여를 요청하거나 업데이트를 받으려면 [feedback-ai-answers@adobe.com](mailto:feedback-ai-answers@adobe.com)에 문의하세요.

#### RDE용 스냅샷(Beta 프로그램) {#rde-snapshot-program}

Beta에서 RDE(빠른 개발 환경)는 이제 코드 및 컨텐츠의 현재 상태에 대한 스냅샷을 생성하는 기능을 지원하며 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 사용 및 피드백 제공에 관심이 있는 경우 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)에 전자 메일을 보내십시오.

#### AI를 통한 AEM 개발 가속화(Alpha 프로그램) {#ai-dev-alpha}

AEM Java 스택 팀은 기능 전달 속도를 높이고 코드 품질을 개선하기 위해 Cursor, Claude Code, Visual Studio 및 IntelliJ와 같은 도구에서 AI 지원 개발을 사용하는 경우가 늘고 있습니다. 미래의 Adobe 지원 AI 기능을 구축하는 데 도움이 되는 실제 경험을 모으고 있습니다.

[aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)에 전자 메일을 보내 팀의 작업과 Adobe에서 제공할 내용을 공유하십시오.

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
