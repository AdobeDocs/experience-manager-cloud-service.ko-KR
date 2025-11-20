---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.10.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.10.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
source-git-commit: c5918c887be60c5198b762d860fe72afd31df352
workflow-type: tm+mt
source-wordcount: '1894'
ht-degree: 59%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2025.10.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2025.10.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.10.0) 일자는 2025년 10월 30일 금요일입니다. 다음 기능 릴리스(2025.11.0)는 2025년 11월 20일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440927?captions=kor&quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#new-sites}

* [콘텐츠 조각용 시작](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md): 콘텐츠 작성자는 이제 콘텐츠 조각용 시작을 사용하여 구조화된 콘텐츠의 향후 변형을 만들고 예약할 수 있습니다. 새로운 콘텐츠 조각 콘솔을 사용하면 소스 분기와 동기화할 수 있는 향후 콘텐츠를 위한 분기로 콘텐츠 조각 시작을 생성, 편집, 관리 및 예약할 수 있습니다. 새로운 비교 보기는 향후 게시를 위해 Launch를 커밋하기 전에 모든 콘텐츠 변경 사항에 대한 명확한 개요를 제공합니다.

* AEM 콘텐츠 조각용 [콘텐츠 모델 편집기](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)가 AEM의 다른 React Spectrum 기반 인터페이스와 일치하도록 현대화되었습니다. 이제 사용자 인터페이스 구현 및 확장성 모델은 콘텐츠 조각 편집기 및 범용 편집기와 일치합니다. 새 모델 편집기는 새 콘텐츠 모델 관리 UI에서 열면 기본적으로 제공됩니다. Touch UI에서 콘텐츠 모델을 열면 Touch UI 편집기가 열리고 새 편집기를 사용할 수 있습니다.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Experience Manager Forms의 새로운 기능 {#new-features-forms}

**적응형 양식 및 양식 조각을 위한 범용 편집기**

이제 범용 편집기는 적응형 Forms 및 재사용 가능한 양식 조각을 만들기 위한 통합 작성 환경을 제공합니다. 작성자는 강력한 확장 기능 및 포괄적인 제출 기능을 활용하여 직관적인 WYSIWYG 환경 내에서 양식을 시각적으로 디자인할 수 있습니다. 편집기는 보안 강화를 위해 reCAPTCHA 유효성 검사를 통합하고, 사전 채우기 서비스를 제공하여 수동 입력을 줄이고, 모든 장치에서 반응형 디자인을 지원합니다.

**사용 가능한 확장:**

* **규칙 편집기**: 시각적 규칙 편집기를 사용하면 양식 작성자가 코딩, 이벤트 기반 규칙 지원, 즉각적인 유효성 검사 및 오류 처리 없이 양식 필드에 동적 동작을 추가할 수 있습니다.
* **양식 속성**: 사용자가 편집기 내에서 직접 제출 작업, 미리 채우기 서비스, 감사 메시지 및 기타 양식 관련 동작을 구성할 수 있도록 도와주는 마법사입니다.
* **양식 데이터 Source 및 바인드 참조**: 데이터 소스 확장을 사용하면 양식 작성자가 데이터 모델과 연결된 구성 요소를 적응형 양식에 직접 추가하고 모든 구성 요소에 대한 트리 선택에서 바인드 참조를 선택할 수 있습니다.

**지원되는 제출 액션:**

유니버설 편집기는 사용자 지정 제출 동작, Microsoft SharePoint에 제출, Microsoft OneDrive에 제출, Azure Blob Storage에 제출, REST 끝점에 제출, AEM 워크플로 호출, Power Automate 흐름 호출, Marketo Engage에 제출, Adobe Experience Platform(AEP)에 제출, 스프레드시트에 제출, 양식 데이터 모델(FDM)을 사용하여 제출, Workfront Fusion에 제출 및 이메일 보내기 등 광범위한 제출 워크플로를 지원합니다.

자세한 내용은 [Forms용 Edge Delivery Services 유니버설 편집기 설명서](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 참조하세요. 제출 액션을 구성하는 방법에 대한 자세한 내용은 [적응형 양식 제출 액션](/help/edge/docs/forms/universal-editor/submit-action.md)을 참조하십시오.

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

### 릴리스 관리의 새로운 기능 {#new-features-release-management}

**자동 유지 관리 업데이트 일시 중지**

라이브 기간, 라이브 이벤트, 최대 매출 등의 순간은 중단되어서는 안 됩니다. [새로운 셀프 서비스 기능](/help/implementing/deploying/quiet-hours-update-free-periods.md)은 중요한 순간에 자동 유지 관리 업데이트를 중지하므로 팀은 집중 상태를 유지할 수 있습니다.

* 사용 중지 시간: 매일 설정된 시간 동안 자동 유지 관리를 차단합니다. 업무 시간, 야간 작동 또는 오전 컷오버에 이상적입니다.
* 업데이트 불가 기간: 일주일 내내 자동 유지 관리를 차단합니다. 출시, 프로모션 또는 연례 중지 기간에 사용합니다.

>[!NOTE]
>
>9월 25일에 제한 공개 기능으로 사용 가능합니다.
>프로그램에서 활성화하려면 [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com)에 이메일을 보내십시오.

### 더 많은 대상으로 AEM 로그 전달 {#log-forwarding}

이제 AEM 로그를 Amazon S3, Sumo Logic, Dynatrace 및 고유한 New Relic 계정(Adobe 제공 계정이 아님)에 전달할 수 있습니다. 이러한 로깅 대상에 대해 AEM 로그(Apache/Dispatcher 포함)가 지원되지만 CDN 로그는 지원되지 않습니다.

[지원되는 로그 전달 대상](/help/implementing/developing/introduction/log-forwarding.md)의 전체 집합을 확인하세요.

### Edge Delivery Services용 파이프라인 구성 {#config-pipeline-eds}

이제 구성 파이프라인이 Edge Delivery Services으로 빌드된 사이트에 대해 지원되므로 이 기능은 AEM Author 및 AEM Publish 게재 이상으로 확장됩니다. 구성 파이프라인 을 사용하여 트래픽 필터 규칙 및 원본 선택기를 포함하여 CDN 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

Edge Delivery 구성 파이프라인은 Cloud Manager 파이프라인 변수를 통해 비밀 또한 지원합니다.

[Edge Delivery 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)를 참조하십시오.

### 곧 Java API 지원 중단 예정 {#java-api-deprecation}

사용되지 않는 몇몇 API는 8월 31일에 삭제될 예정이라고 공지되었으므로 더 이상 참조할 수 없습니다. 지원이 중단된 API 사용이 코드에서 감지되면 액션 센터 알림을 받게 되며, 11월 13일 이후에는 Cloud Manager 빌드 중에 사용 제거의 중요성을 강조하는 알림이 표시됩니다. [사용 중단 문서](/help/release-notes/deprecated-removed-features.md#aem-apis)에서 자세한 내용을 확인할 수 있으며, 편의를 위해 아래에 해당 API 목록을 제공합니다.

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

### Java 11 런타임 사용 중단 {#java11-runtime-deprecation}

Adobe은 2025년 10월 14일에 **Stage** 및 **Production** 환경을 더 높은 성능의 **Java 21 런타임**(으)로 업그레이드했습니다. 1월 말부터 AEM Cloud Service SDK 및 클라우드 환경은 모두 Java 11 런타임과 작동하지 않습니다.

>[!NOTE]
>
> 최신 성능 최적화 및 언어 개선 사항을 활용하려면 Java 17 또는 Java 21(권장)로 빌드하는 것이 좋습니다. Java 8 및 Java 11을 사용한 빌드는 현재 지원되지만 향후 릴리스에서는 더 이상 사용되지 않을 예정입니다. 사용 중단에 앞서 별도의 커뮤니케이션이 이루어집니다. *이 문서*&#x200B;의 [빌드 시간 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 섹션을 참조하십시오.
>

### AEM Java 로그 구성 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급된 대로 AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

**11월 20일**&#x200B;부터 지원되지 않는 사용자 지정 로깅 무시가 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 현재 구성에 영향을 받을 수 있는 고객에게는 Adobe에서 개별적으로 안내를 드렸습니다.

사용자 정의 로깅 동작에 의존하는 모든 다운스트림 프로세스를 검토하고 업데이트해 주시기 바랍니다. 예:

* 로그 전달 시스템이 사용자 정의 로그 형식을 기대하는 경우, 수집 규칙을 조정해야 할 수도 있습니다.
* 이전에 로그 수준을 변경하여 로그의 세부 정보를 줄인 적이 있는 경우 기본 수준으로 되돌리면 로그 볼륨이 증가할 수 있습니다.

### 에지 컴퓨팅 (Beta 프로그램) {#edge-computing}

에지 컴퓨팅을 사용하면 CDN 계층에서 JavaScript를 실행할 수 있어 데이터 처리가 최종 사용자에게 더 가까워집니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 브라우저에 제공하기 전에 서드파티 API의 응답(및 여러 API 응답 집계)을 다시 포맷
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공
* ChatGPT 및 Claude와 같은 LLM을 위한 MCP 서버를 사용자 정의 도구에 액세스하도록 노출

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

### Edge Delivery Services에 대한 Edge 인증(Beta 프로그램) {#edge-authentication}

Edge 인증을 사용하면 ID 공급자(IdP)로 인증된 사용자만 Edge Delivery Services 페이지에 액세스하도록 제한할 수 있습니다. 이 작업은 OpenID Connect(OIDC) 구성 YAML 파일을 배포하는 방법으로 수행됩니다.

원하는 경우 사용 사례에 대한 간단한 설명과 질문을 담은 이메일을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 보내십시오.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### 라이브 트래픽을 수락하기 전에 코드 테스트를 위한 카나리아 프로덕션 배포(Beta 프로그램) {#canary-beta}

최종 사용자에게 노출하기 전에 내부용 테스트 트래픽으로 프로덕션 빌드의 유효성을 검사합니다. 프로덕션으로 배송하고, 카나리아 트래픽만 라우팅하고(특수 헤더 사용), 동작을 모니터링한 다음 라이브 트래픽으로 승격하거나 고객에게 영향을 주지 않고 롤백합니다.

코드 릴리스를 프로덕션에 배포하되, 라이브 트래픽을 수락할지 아니면 롤백할지 여부를 결정하기 전에 내부 테스트 트래픽으로만 이를 제한합니다.

액세스를 요청하고 피드백을 공유하려면 [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com)에 이메일을 보내십시오.


### AI 답변 - AEM Sites(Beta 프로그램)에 대한 스마트하고 컨텍스트 인식 응답 {#ai-answers-beta}

AI 답변에서는 방문자가 콘텐츠와 상호 작용할 수 있는 새로운 방법을 소개합니다. RAG(Retrieval-Augmented Generation) 기술을 기반으로 하는 이 솔루션은 AEM 관리 데이터를 사용하여 디지털 환경 내에서 정확하고 일관된 답변을 직접 제공합니다.

AI Answers Beta 프로그램 출시를 준비하고 있으며, 이제 고객을 초대하여 관심 사항을 등록하고자 합니다. 베타는 용량이 매우 제한적이기 때문에 조기 가입이 우선적 고려를 받게 된다. Beta에 참여하면 AEM 클라우드 서비스 환경에서 AI 답변을 탐색하고, 성능과 정확성을 검증하며, 향후 사용 환경을 미리 구체화할 수 있습니다.

참여를 요청하거나 업데이트를 받으려면 [feedback-ai-answers@adobe.com](mailto:feedback-ai-answers@adobe.com)에 문의하세요.


### RDE용 스냅샷 (Alpha 프로그램) {#rde-snapshot-program}

알파 버전에서는 신속한 개발 환경(RDEs)에서 현재 코드와 콘텐츠 상태의 스냅샷을 찍는 기능을 지원하며, 이는 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 피드백을 제공하는 데 관심이 있으시면 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)으로 이메일을 보내주십시오.

### 애플리케이션 성능 모니터링(APM) 기능 확장(Alpha 프로그램) {#apm-alpha}

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
