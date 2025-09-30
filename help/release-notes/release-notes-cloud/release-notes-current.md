---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: f5510d83ed2ff52496fd7e83ba29010684731938
workflow-type: tm+mt
source-wordcount: '1957'
ht-degree: 46%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.9.0) 일자는 2025년 9월 25일 금요일입니다. 다음 기능 릴리스(2025.10.0)는 2025년 10월 30일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites 프리릴리스의 새로운 기능 {#prerelease-sites}

AEM 컨텐츠 조각용 컨텐츠 모델 편집기가 AEM의 다른 React 스펙트럼 기반 인터페이스와 일치하도록 현대화되었습니다. 사용자 인터페이스 구현 및 확장성 모델은 이제 콘텐츠 조각 편집기 및 유니버설 편집기와 일치합니다. 새 콘텐츠 모델 관리 UI에서 열면 새 모델 편집기가 기본적으로 제공됩니다. Touch UI에서 콘텐츠 모델을 열면 Touch UI 편집기가 열리고 새 편집기를 사용해 볼 수 있는 옵션이 제공됩니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#new-features-assets-view}

**Dynamic Media 템플릿의 하위 문자열을 사용하여 텍스트 서식 개선**

이제 Dynamic Media 템플릿 텍스트 레이어 내의 하위 문자열에 서식을 적용할 수 있습니다. 선택한 단어 또는 구는 별도의 레이어로 처리되어 글꼴, 글꼴 크기, 색상 등을 조정할 수 있습니다. 하위 문자열 레이어는 매개 변수화되므로 템플릿의 게재 URL을 사용하여 실시간으로 업데이트할 수 있습니다

### OpenAPI 기능을 갖춘 Dynamic Media의 새로운 기능 {#new-features-dynamic-media-with-openapi}

**OpenAPI URL을 사용하는 SEO 친화적 DM**

OpenAPI를 사용하여 DM에서 자산 전달을 위한 Vanity URL을 생성하고, 긴 시스템 생성 UUID를 짧고 읽기 쉬운 식별자로 대체합니다. 이렇게 하면 링크의 SEO 친화도가 향상되고 브랜드 또는 캠페인에 더 잘 부합하게 됩니다. Vanity URL은 기존 워크플로를 방해하지 않고 런타임에 원래 자산의 UUID에 자동으로 매핑됩니다.

>[!NOTE]
>
>이 기능은 제한된 가용성 기능으로 사용할 수 있습니다. 기능을 배포에 사용할 수 있도록 [Adobe 고객 지원 사례를 만들고 제출](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)할 수 있습니다.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Experience Manager Forms의 새로운 기능 {#new-features-forms}

**SharePoint 목록 첨부 파일에 대한 양식 데이터 모델 워크플로 단계 호출**

이제 양식 데이터 모델 호출 워크플로우 단계에서 SharePoint 목록 기반 양식 데이터 모델에서 Base64 인코딩 첨부 파일 배열에 대한 워크플로우측 메타데이터 처리를 지원합니다. 이 향상된 기능을 통해 워크플로 단계는 파일 이름, MIME 유형 및 각 첨부 파일에 대한 사용자 지정 속성과 같은 메타데이터를 전달하고, 저장하고, 검색할 수 있습니다. 이 기능은 보다 포괄적인 데이터 관리를 가능하게 하며 원활한 다운스트림 통합을 지원합니다. 자세한 내용은 [SharePoint 목록 첨부 파일에 대한 양식 데이터 모델 호출 워크플로 단계의 향상된 지원](/help/forms/aem-forms-workflow-step-reference.md#invoke-form-data-model-fdm-service-step)을 참조하십시오.

### AEM Forms의 프리릴리스 기능

**규칙 편집기 개선 사항**

규칙 편집기는 이제 향상된 탐색을 지원하고 입력 매개 변수에서 함수 및 수학 표현식을 사용할 수 있습니다.

**이벤트 페이로드를 사용하여 탐색 기능 향상**

이제 서비스 호출 처리기의 `Navigate To` 작업이 `EVENT_PAYLOAD`을(를) 지원하므로 양식 작성자가 이벤트 응답에 따라 후속 작업을 구성할 수 있습니다. 이러한 향상된 기능을 통해 사후 제출 워크플로우를 보다 유연하게 디자인할 수 있으므로 보다 원활한 전환과 보다 개인화된 사용자 경험을 보장할 수 있습니다. 자세한 내용은 [이벤트 페이로드 지원을 통해 탐색 기능 향상](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service)을 참조하십시오.

**입력 매개 변수에서 함수 및 수학 표현식 지원**

이제 입력 매개 변수가 함수 호출과 수학 표현식을 모두 지원하므로 양식 작성자가 동적으로 계산된 값을 직접 전달할 수 있습니다. 이러한 향상된 기능을 통해 규칙 구성을 간소화하고 추가 필드를 사용할 필요가 없으며 복잡한 논리 및 계산 기반 시나리오에 보다 유연하게 대처할 수 있습니다. 자세한 내용은 입력 매개 변수에서 [함수 및 수학 표현식 지원](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters)을 참조하십시오.

### AEM Forms의 새로운 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스하고 개발을 구체화할 수 있는 특별한 기회를 제공합니다.

이들 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

대화형 통신 편집기에서 **PDF 미리 보기**

사용자는 데이터 없이, 로컬 JSON 데이터 파일을 통해 또는 데이터 모델의 데이터를 통해 대화형 통신 PDF를 미리 볼 수 있으므로 유연한 데이터 기반 테스트가 가능합니다. 자세한 내용은 [대화형 통신 편집기에서 PDF 미리 보기](/help/forms/interactive-communication/pdf-preview-in-interactive-communication-editor-with-different-data-options.md)를 참조하십시오.

**대화형 통신에서 사용자 지정 글꼴 지원**

사용자 정의 글꼴 기능을 사용하면 대화형 통신에 사용자 정의 또는 조직에서 승인한 글꼴을 포함할 수 있으므로, 장치 및 플랫폼 간에 일관되고 브랜드화된 PDF 렌더링이 가능합니다. 자세한 내용은 [대화형 통신에서 사용자 지정 글꼴 지원](/help/forms/interactive-communication/add-custom-fonts-to-interactive-communication-editor.md)을 참조하십시오.

**대화형 통신 가져오기 및 내보내기**

이 기능을 사용하면 다양한 환경에서 대화형 커뮤니케이션을 마이그레이션하고 재사용할 수 있습니다. 이제 대화형 통신을 관련 조각 및 데이터 모델과 함께 한 환경에서 내보내고 다른 환경으로 가져올 수 있습니다. 자세한 내용은 [대화형 통신 가져오기 및 내보내기](/help/forms/interactive-communication/import-and-export-interactive-communications.md)를 참조하십시오.

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

### Release Management의 새로운 기능 {#new-features-release-management}

**자동 유지 관리 업데이트 일시 중지**

라이브 기간, 라이브 이벤트, 매출 절정 등 이러한 순간은 결코 중단될 수 없습니다. [새로운 셀프 서비스 기능](/help/implementing/deploying/quiet-hours-update-free-periods.md) 자동 유지 관리 업데이트가 필요할 때 중지되므로 팀이 계속 집중할 수 있습니다.

* 자동 중지 시간: 매일 설정된 시간 동안 자동 유지 관리를 차단합니다. 업무 시간, 야간 운영 또는 아침 휴식에 이상적입니다.
* 업데이트 불가 기간: 전체 주 동안 자동 유지 관리를 차단합니다. 론치, 프로모션 또는 연간 결빙에 사용합니다.

>[!NOTE]
>
>9월 25일에 제한된 가용성 기능으로 제공됩니다.
>&#x200B;>프로그램에서 활성화하려면 [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com)에 전자 메일을 보내십시오.

### Eclipse용 AEM 개발자 도구 새 릴리스 {#aem-develeper-tools-for-eclipse}

AEM Developer Tools for Eclipse 버전 1.4.0이 릴리스되었습니다. 이 버전에서는 Eclipse IDE 2022-12 이상에 대한 지원이 추가되었으며 현재 버전(2025-09)의 유효성을 검사했습니다. 이제 이 툴은 최신 버전의 AEM Project Archetype에서 작동하며 Sling IDE 툴 1.3.0의 개선 사항을 통합합니다.

[Eclipse 마켓플레이스](https://marketplace.eclipse.org/content/aem-developer-tools-eclipse)에서 설치하고 [AEM 개발자 도구 페이지](https://eclipse.adobe.com)를 참조하십시오.

### 곧 Java API 지원 중단 예정 {#java-api-deprecation}

더 이상 사용되지 않는 여러 API는 8월 31일에 제거되도록 표시되었으므로 더 이상 참조해서는 안 됩니다. 코드에서 더 이상 사용되지 않는 API 사용이 감지되면 작업 센터 알림을 받게 되며 11월 13일 이후에는 Cloud Manager 빌드 중에 알림이 표시되어 사용 제거의 중요성을 강화합니다. [사용 중단 문서](/help/release-notes/deprecated-removed-features.md#aem-apis)에서 자세한 내용을 확인할 수 있으며, 편의를 위해 아래에 해당 API 목록을 제공합니다.

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

*Java 11 런타임*&#x200B;은(는) 더 이상 사용되지 않으며 대부분의 환경이 이미 고성능 **Java 21 런타임**(으)로 업그레이드되었습니다.

지원되지 않는 종속성([Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 참조)으로 인해 환경을 업그레이드할 수 없는 경우 다음 단계로 Adobe에서 이메일을 받았어야 합니다. 여기에서 설명한 대로 Adobe에서 **2025년 9월 18일**&#x200B;에 **개발** 및 **RDE** 환경을 업그레이드하여 사이트 및 프로세스를 확인하고 문제를 해결할 수 있습니다. **Stage** 및 **Production**&#x200B;에 대한 업그레이드는 **2025년 10월 14일**&#x200B;에 진행될 예정입니다.

>[!NOTE]
>
>런타임 버전은 코드의 빌드 버전과 별개입니다. Java 21을 사용하여 빌드하는 것이 좋지만 현재로서는 Java 11 빌드가 계속 허용됩니다. Java 11 빌드에 대한 별도의 사용 중단 공지는 앞으로 공유될 예정입니다.

### AEM Java 로그 구성 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급된 대로 AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

**10월 30일**&#x200B;부터 지원되지 않는 사용자 지정 로깅 무시가 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 현재 구성에 영향을 받을 수 있는 고객에게는 Adobe에서 개별적으로 안내를 드렸습니다.

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

### Edge Delivery Services용 Edge 인증(Beta 프로그램) {#edge-authentication}

Edge 인증을 사용하면 ID 공급자(IdP)로 인증된 사용자만 Edge Delivery Services 페이지에 대한 액세스를 제한할 수 있습니다. 이 작업은 OpenID Connect(OIDC) 구성 YAML 파일을 배포하여 수행됩니다.

필요한 경우 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 사용 사례에 대한 간단한 설명과 질문이 있는 전자 메일을 보내십시오.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### 라이브 트래픽을 수락하기 전에 코드를 테스트하는 카나리아 프로덕션 배포(Beta 프로그램) {#canary-beta}

최종 사용자에게 노출하기 전에 내부 전용 테스트 트래픽으로 프로덕션 빌드의 유효성을 검사합니다. 프로덕션으로 배송하고, 카나리아 트래픽만 라우팅하고(특수 헤더 사용), 동작을 모니터링한 다음 라이브 트래픽으로 승격하거나 고객에게 영향을 주지 않고 롤백합니다.

코드 릴리스를 프로덕션에 배포하지만 라이브 트래픽을 수락할지 및 롤백할지 여부를 결정하기 전에 내부 테스트 트래픽으로만 제한합니다.

액세스를 요청하고 피드백을 공유하려면 [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com)에 전자 메일을 보내십시오.

### RDE용 스냅샷 (Alpha 프로그램) {#rde-snapshot-program}

알파 버전에서는 신속한 개발 환경(RDEs)에서 현재 코드와 콘텐츠 상태의 스냅샷을 찍는 기능을 지원하며, 이는 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 피드백을 제공하는 데 관심이 있으시면 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)으로 이메일을 보내주십시오.

### 더 많은 대상으로 AEM 로그 전달 (Beta 프로그램) {#log-forwarding-beta}

로그는 Cloud Manager에서 다운로드할 수 있지만 많은 조직에서 이러한 로그를 선호하는 로깅 대상으로 스트리밍하는 것이 유용하다고 생각합니다. AEM은 이미 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch), Splunk로의 AEM 및 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성하고 구성 파이프라인을 사용하여 배포합니다.

이제 Beta 버전에서는 AEM 로그를 Amazon S3, Sumo Logic, Dynatrace 및 사용자의 New Relic 계정(Adobe 제공 계정이 아닌 경우)으로 전달할 수 있습니다. AEM 로그(Apache/Dispatcher 포함)가 이러한 로깅 대상에 대해 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 이메일 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)으로 문의하십시오.

자세한 내용은 [로그 전달 설명서](/help/implementing/developing/introduction/log-forwarding.md)에서 확인하십시오.

### 확장된 APM(Application Performance Monitoring)(Alpha 프로그램) {#apm-alpha}

AEM Cloud Service는 현재 가시성을 위해 Adobe에서 제공하는 [New Relic One](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) 및 고객 관리 [Dynatrace](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace)을(를) 지원합니다. 추가 APM 옵션에 대한 지원을 살펴볼 때 사용 사례와 함께 선호하는 공급업체 또는 기술을 [aemcs-apm-beta@adobe.com](mailto:aemcs-apm-beta@adobe.com)에 전자 메일을 보내십시오.


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
