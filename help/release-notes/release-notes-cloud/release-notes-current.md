---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 0d2164920ca44ee6c872fdfe2090760a1506215d
workflow-type: tm+mt
source-wordcount: '1961'
ht-degree: 48%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.8.0) 일자는 2025년 8월 28일 금요일입니다. 다음 기능 릴리스(2025.9.0)는 2025년 9월 25일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440927?quality=12&captions=kor)

-->

## Experience Hub {#experience-hub}

[Experience Hub](/help/experience-hub.md)은(는) 모든 AEM 기능에 액세스하기 위한 중앙 시작 지점입니다. 사용자 담당자와 사용 가능한 라이선스에 따라 개인화되므로 각 사용자가 효율적으로 결과를 달성할 수 있습니다.

## AEM의 AI 지원 {#AI-assistant}

AEM용 [AI Assistant](/help/implementing/cloud-manager/ai-assistant-in-aem.md)는 AEM 제품 관련 질문에 대한 즉각적인 답변을 얻을 수 있도록 설계된 대화형 인터페이스를 제공합니다(*모든 사용자가 사용할 수 있음*). 지원 티켓 생성 작업을 자동화할 수 있습니다(*지원 관리자가 사용할 수 있음*). AEM에 직접 임베드되며 AEM Experience Hub, Cloud Manager 및 Author UI에서 액세스할 수 있습니다.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#enhancements-sites}

* 콘텐츠 조각 관리자 UI에서 이제 콘텐츠 조각의 워크플로 상태를 확인할 수 있으며, 선택한 조각에 대한 과거 및 현재 실행 중인 워크플로에 대한 자세한 정보를 제공합니다.
* 경로 대신 UUID를 통해 조각을 열어 새 콘텐츠 조각 편집기에서 콘텐츠 조각을 여는 성능이 일반적인 시나리오에서 25% 증가했습니다.
* 참조된 조각을 사용하여 콘텐츠 조각을 복사할 때 참조된 조각의 사본은 이제 상위 조각 사본과 동일한 위치에 저장됩니다.
* 이제 폴더 설정에서 사용자 지정 작업 영역을 구성하여 콘텐츠 조각을 Adobe Target의 구성된 작업 영역으로 내보낼 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Content Hub의 새로운 기능 {#new-features-content-hub}

**필터 속성을 통한 대량 검색**

이제 Content Hub을 통해 필요한 에셋을 보다 빠르게 검색할 수 있습니다. 새로운 일괄 검색 기능을 사용하면 구분 기호로 구분된 필터 속성에 대해 여러 값을 입력하고(예: 여러 SKU ID) 단일 검색을 사용하여 일치하는 모든 에셋을 즉시 검색할 수 있습니다.

### OpenAPI 기능을 갖춘 Dynamic Media의 새로운 기능 {#new-features-dynamic-media-with-openapi}

**OpenAPI URL을 사용하는 SEO에 친숙한 DM**

DM에서 OpenAPI를 사용하여 자산 전달을 위한 별칭 URL을 만들고, 긴 시스템 생성 UUID를 읽을 수 있는 짧은 식별자로 바꿉니다. 이렇게 하면 SEO 링크가 친화적이고 브랜드 또는 캠페인과 더 잘 부합할 수 있습니다. vanity URL은 기존 워크플로를 중단하지 않고 런타임 시 자동으로 원래 에셋 UUID로 확인됩니다.

>[!NOTE]
>
>이 기능은 9월 10일에 제한된 가용성 기능으로 제공됩니다. [Adobe 고객 지원 사례를 만들어 제출](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)하여 배포에 사용할 수 있도록 설정할 수 있습니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Experience Manager Forms의 새로운 기능 {#new-features-forms}

**날짜 및 시간 입력 구성 요소**

이제 [날짜 및 시간 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-time-component)를 사용할 수 있으므로 사용자가 달력 및 시계 인터페이스를 사용하거나 지원되는 형식으로 값을 수동으로 입력하여 날짜와 시간을 모두 선택할 수 있습니다.

**파일 업로드에 대한 향상된 오류 처리**

[첨부 파일 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)에서 이제 허용 목록에 대해 업로드된 파일 형식을 자동으로 확인합니다. 사용자가 지원되지 않는 형식으로 파일을 업로드하면 제출 중에 양식에 오류가 표시됩니다. 또한 구성 요소는 파일 내용을 확인하여 파일 형식을 확인하므로 양식의 전반적인 보안을 강화할 수 있습니다.

**사용자 지정 제출 액션에 대해 지정된 오류 응답**

[사용자 지정 제출 액션](/help/forms/custom-submit-action-troubleshooting.md)에서 처리되지 않은 오류가 발생하면 시스템이 오류 코드 502를 반환합니다. 이렇게 하면 이 문제가 사용자 지정 제출 액션과 관련이 있음을 식별하여 디버깅을 더 쉽게 할 수 있습니다.

**기록 문서에서 숨겨진 필드 제외**

새 속성을 사용하면 [기록 문서](/help/forms/generate-document-of-record-core-components.md#document-of-record-settings)에서 숨겨진 필드를 제외할 수 있습니다. 기본적으로 이 옵션은 선택되어 있지 않으며 모든 양식 필드에 적용됩니다.


### AEM Forms의 프리릴리스 기능

**AFP 표현물 생성 및 동기화**

이제 [AEM Forms 통신 API](/help/forms/document-generation-afp-api.md)를 사용하여 XDP 파일을 AFP 형식으로 변환할 수 있습니다. AFP는 대규모 기업용 인쇄에서 널리 사용되는 고성능 포맷이다.

**규칙 편집기의 개선 사항**

* [함수 목록의 유효성 검사 메서드](/help/forms/rule-editor-enhancements-use-cases.md#validate-method-in-function-list): 이제 유효성 검사 및 재설정 메서드가 패널, 필드 및 양식 수준에서 실행을 지원합니다. 이전에는 양식 수준에서만 지원되었습니다.
* [최신 JavaScript 지원](/help/forms/rule-editor-core-components-difference-tables.md): 사용자 지정 기능에 대해 ECMAScript 2019 이상 기능에 대한 지원을 추가하여 보다 효율적이고 모듈식이며 재사용 가능한 코드를 작성할 수 있습니다.
* [규칙 편집기의 DoR 옵션 다운로드](/help/forms/rule-editor-enhancements-use-cases.md#downloaddor-as-ootb-fuction-in-rule-editor): 기록 문서(DoR)를 다운로드하는 함수가 규칙 편집기에서 기본 제공(OOTB) 옵션으로 추가되었습니다.

  ![기록 문서](/help/forms/assets/document-of-record-rn.gif)

* [규칙 편집기의 동적 변수](/help/forms/rule-editor-enhancements-use-cases.md#support-for-dynamic-variables-in-rules): 이제 규칙 편집기에서 동적(임시) 변수를 사용하여 조건 및 작업을 보다 유연하게 정의할 수 있습니다. 숨겨진 필드는 더 이상 임시 값을 저장하는 데 필요하지 않습니다.
* [사용자 지정 이벤트 기반 규칙 지원](/help/forms/rule-editor-enhancements-use-cases.md#custom-event-based-rules-support): 이제 사용자 지정 이벤트를 정의하고 해당 이벤트를 기반으로 규칙을 트리거할 수 있습니다.
* [컨텍스트 인식 반복 가능 패널 규칙](/help/forms/rule-editor-enhancements-use-cases.md#context-based-rule-execution-for-repeatable-panels): 반복 가능 패널에서 규칙이 마지막 패널 인스턴스에만 적용되지 않고 컨텍스트를 기반으로 실행됩니다.
* [매개 변수에 의해 트리거된 규칙](/help/forms/rule-editor-enhancements-use-cases.md#url-and-browser-parameter-based-rules-in-adaptive-forms): 이제 규칙 편집기에서 쿼리 매개 변수, UTM 매개 변수 또는 브라우저 매개 변수를 기반으로 규칙 실행을 지원합니다.
* [양식별 사용자 지정 함수](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#organizing-custom-functions-across-different-forms): Edge Delivery Services Forms은 이제 양식별 사용자 지정 함수 스크립트를 지원하므로 재사용 가능한 논리를 보다 유연하게 관리할 수 있습니다.
* [사용자 지정 함수에 대한 정적 가져오기](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#static-imports-for-custom-functions): 이제 유니버설 편집기의 규칙 편집기에서 정적 가져오기를 지원하므로 개발자가 여러 양식에서 함수를 구성, 공유 및 다시 사용할 수 있습니다.

### AEM Forms의 새로운 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스하고 개발을 구체화할 수 있는 특별한 기회를 제공합니다.

이들 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

**스크리블 서명 구성 요소**

이제 [스크리블 서명 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/scribble-signature)를 사용하여 사용자가 계약 양식과 같은 양식에 서명을 추가할 수 있습니다. 이 구성 요소를 사용하면 마우스, 스타일러스 또는 터치스크린을 사용하여 양식 내에서 직접 서명을 그릴 수 있습니다.

**규칙 편집기에서 직접 API 통합**

적응형 Forms은 이제 양식 데이터 모델 없이도 시각적 규칙 편집기에서 [직접 API 통합](/help/forms/api-integration-in-rule-editor.md)을(를) 지원합니다. 작성자는 URL 또는 cURL 가져오기를 사용하여 API를 구성하고, 입력/출력 매개 변수를 매핑하며, 인증을 통해 보안 호출을 수행할 수 있습니다.

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### JavaScript 컴파일 업데이트 {#javascript-compilation}

이제 기본 클라이언트측 라이브러리(clientlibs) JavaScript 컴파일이 ECMASCRIPT5 대신 ECMASCRIPT_2018을 타깃팅합니다. 과거에는 재정의할 수 있었지만, 이 업데이트를 통해 기본적으로 성능 향상, 최신 JavaScript 구문 및 기능이 활성화됩니다.

### 예정된 Java API 사용 중단 {#java-api-deprecation}

더 이상 사용되지 않는 여러 API는 8월 31일에 제거를 타깃팅하므로 더 이상 참조해서는 안 됩니다. 9월 초에는 API 사용이 감지되면 작업 센터 알림이 전송되고, 9월 25일 이후에는 Cloud Manager 빌드 시 알림이 표시되어 사용 제거의 중요성을 강화합니다. 자세한 내용은 [사용 중단 문서](/help/release-notes/deprecated-removed-features.md#aem-apis)을(를) 참조하십시오. 그러나 편의상 이러한 API는 아래에 나열되어 있습니다.

<details>
  <summary>를 확장하여 Java API 사용 중단을 확인합니다.</summary>

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

</details>

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Java 11 런타임 사용 중단 {#java11-runtime-deprecation}

*Java 11 런타임*&#x200B;은 이제 더 이상 사용되지 않으며, 대부분의 환경은 이미 성능이 더 좋은 **Java 21 런타임**&#x200B;으로 업그레이드되었습니다.

지원되지 않는 종속성으로 인해 환경을 업그레이드할 수 없는 경우([Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 참조), Adobe로부터 구체적인 다음 단계가 포함된 이메일을 받았을 것입니다. **2025년 10월 1일**&#x200B;까지 모든 필수 업데이트가 완료되어 중단 없이 환경을 업그레이드할 수 있는지 확인하십시오.

참고: 런타임 버전은 코드의 빌드 버전과 별도입니다. Java 21을 사용한 빌드를 권장하지만 현재로서는 Java 11 빌드도 여전히 지원됩니다. Java 11 빌드에 대한 별도의 사용 중단 공지는 앞으로 공유될 예정입니다.

### AEM Java 로그 구성 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급된 대로 AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

**9월 25일**&#x200B;부터 지원되지 않는 사용자 지정 로깅 무시가 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 현재 구성에 영향을 받을 수 있는 고객에게는 Adobe에서 개별적으로 안내를 드렸습니다.

사용자 정의 로깅 동작에 의존하는 모든 다운스트림 프로세스를 검토하고 업데이트해 주시기 바랍니다. 예:

* 로그 전달 시스템이 사용자 정의 로그 형식을 기대하는 경우, 수집 규칙을 조정해야 할 수도 있습니다.
* 이전에 로그 수준을 변경하여 로그의 세부 정보를 줄인 적이 있는 경우 기본 수준으로 되돌리면 로그 볼륨이 증가할 수 있습니다.

### Edge 컴퓨팅(Beta 프로그램) {#edge-computing}

에지 컴퓨팅을 사용하면 CDN 계층에서 JavaScript를 실행할 수 있어 데이터 처리가 최종 사용자에게 더 가까워집니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 콘텐츠 접근 권한을 부여하기 전에 ID 공급자를 통해 사용자 인증
* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 서드파티 API의 응답을 다시 서식 지정(및 여러 API 응답 집계)한 후 브라우저에 전달
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공
* ChatGPT 및 Claude와 같은 LLM을 위한 MCP 서버를 사용자 정의 도구에 액세스하도록 노출

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

### Edge Delivery Services를 위한 CDN 구성 (Beta 프로그램) {#cdn-eds-beta}

Adobe 관리 CDN은 [구성 파이프라인 문서](/help/operations/config-pipeline.md#configurations)에 설명된 대로 유연한 구성 옵션을 제공합니다.

이제 Beta에서 CDN 원본 선택기, 응답 및 요청 변환, CDN 로그 전달 등을 포함하는 기능에 대한 구성 파이프라인을 배포할 수 있습니다. 사용 사례에 대한 자세한 내용은 [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com)에 문의해 주십시오.

### RDE용 스냅샷 (Alpha 프로그램) {#rde-snapshot-program}

알파 버전에서는 신속한 개발 환경(RDEs)에서 현재 코드와 콘텐츠 상태의 스냅샷을 찍는 기능을 지원하며, 이는 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 피드백을 제공하는 데 관심이 있으시면 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)으로 이메일을 보내주십시오.

### 더 많은 대상으로 AEM 로그 전달 (Beta 프로그램) {#log-forwarding-beta}

로그는 Cloud Manager에서 다운로드할 수 있지만 많은 조직에서 이러한 로그를 선호하는 로깅 대상으로 스트리밍하는 것이 유용하다고 생각합니다. AEM은 이미 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch), Splunk로의 AEM 및 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성하고 구성 파이프라인을 사용하여 배포합니다.

이제 Beta 버전에서는 AEM 로그를 Amazon S3, Sumo Logic, Dynatrace 및 사용자의 New Relic 계정(Adobe 제공 계정이 아닌 경우)으로 전달할 수 있습니다. AEM 로그(Apache/Dispatcher 포함)가 이러한 로깅 대상에 대해 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 이메일 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)으로 문의하십시오.

자세한 내용은 [로그 전달 설명서](/help/implementing/developing/introduction/log-forwarding.md)에서 확인하십시오.

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
