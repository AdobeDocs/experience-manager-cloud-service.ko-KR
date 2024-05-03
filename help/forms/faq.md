---
title: AEM Forms as a Cloud Service에 대한 FAQ
description: Forms as a Cloud Service 자주 묻는 질문
contentOwner: khsingh
role: User
feature: Adaptive Forms, FAQ
index: false
exl-id: 0b14b680-7da5-4e0b-bd6a-c379d148f9d7
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 89%

---

# 자주 묻는 질문 {#frequently-asked-questions}

* **코드 편집기를 사용하여 규칙을 생성할 수 있습니까?**
비주얼 편집기를 사용하여 규칙을 생성할 수 있습니다. 코드 편집기는 [!DNL Forms] as a Cloud Service에서 사용할 수 없습니다. 적응형 양식이 코드 편집기를 사용하여 개발된 규칙 스크립트를 사용하는 경우 [마이그레이션 유틸리티](migrate-to-forms-as-a-cloud-service.md)를 사용하여 코드 스크립트를 사용자 정의 함수로 변환하십시오. 사용자 정의 함수를 Visual Editor와 함께 사용하여 코드 편집기를 통해 얻은 결과를 유지할 수 있습니다.

* **클라우드 서비스 인스턴스에서 XFA 기반 적응형 양식을 만들 수 있습니까?**
예. 클라우드 서비스 인스턴스에서 XFA 기반 적응형 양식을 만들 수 있습니다. 그러나 XFA 기반 적응형 양식에 대한 지원은 AEM Forms as a Cloud Service SDK(로컬 개발 환경)에서는 사용할 수 없습니다. AEM Forms as a Cloud Service SDK를 통한 XFA 기반 적응형 양식을 사용하려는 경우 Adobe 지원 팀에 문의하여 사용 사례 및 특정 요구 사항에 대해 자세히 알아보십시오.

<!-- * **Can I use an XDP as a Document of Record (DoR) template? Is Forms Designer included in AEM Forms as a Cloud Service license?** 

  Yes, you can use an XDP as a Document of Record template on Cloud Service instances. However, support to use XDP as a Document of Record template is not available for AEM Forms as a Cloud Service SDK (Local development environment). -->

* **온프레미스 또는 [!DNL Adobe-Managed Services] 환경에서 [!DNL Forms] as a Cloud Service 환경으로 콘텐츠를 마이그레이션할 수 있습니까?**
예. 온프레미스 또는 [!DNL Adobe-Managed Services] 환경에서 [!DNL Forms] as a Cloud Service 환경으로 사용자 정의 코드, 콘텐츠 및 자산을 마이그레이션할 수 있습니다. 자세한 지침은 [Forms as a Cloud Service로 마이그레이션](migrate-to-forms-as-a-cloud-service.md)을 참조하십시오.

<!-- You can use package manager or Experience Manager UI to [export and import Forms and related assets](import-export-forms-templates.md), use the migration utility to make your existing assets compatible with [!DNL Forms] as a Cloud Service, use the [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#best-practices-analyzer) tool to find the features and APIs that require changes and updated before migration, and use the [Content Transfer Tools](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/home.html) to move your custom code without refactoring it. -->

* **AEM [!DNL Forms] as a Cloud Service [!DNL Java™] API 참조 설명서를 어디에서 얻을 수 있습니까?**
[!DNL Maven Central Repository]에서 Java™ API 참조 설명서를 다운로드할 수 있습니다. 다운로드 방법:
   1. [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api)로 이동합니다.
   1. 최신 버전의 [!DNL Experience Manager Forms] SDK가 포함된 페이지를 찾아 엽니다.
   1. 모든 파일을 보려면 모두 보기 옵션을 클릭합니다.
   1. `aem-forms-sdk-api-<version>-javadocs`.jar을 다운로드하고 추출합니다.
   1. API 참조 설명서를 보려면 index.html 파일을 엽니다.

* **적응형 양식에 대한 [!DNL JavaScript™] API 참조는 어디에서 얻을 수 있습니까?**
[!DNL  Maven Central Repository]에서 [!DNL JavaScript™] API 참조 설명서를 다운로드할 수 있습니다. 다운로드 방법:
   1. [[!DNL Maven Central Repository]를 엽니다](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. 최신 버전의 [!DNL Experience Manager Forms] SDK가 포함된 페이지를 찾아 엽니다.
   1. 모든 파일을 보려면 모두 보기 옵션을 클릭합니다.
   1. `aem-forms-sdk-api-<version>-jsdoc.jar`을 다운로드하고 추출합니다.
   1. API 참조 설명서를 보려면 index.html 파일을 엽니다.

* **기존 테마 및 템플릿을 계속 사용할 수 있습니까?**
예. [마이그레이션 유틸리티](migrate-to-forms-as-a-cloud-service.md)를 사용하여 [!DNL AEM Forms] as a Cloud Service로 이동한 후 AEM 6.4 Forms 및 AEM 6.5 Forms로 생성된 테마를 계속 사용할 수 있습니다.

  [!DNL AEM Forms] as a Cloud Service [Archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment)를 기반으로 프로젝트를 생성하고 포함된 샘플 테마 및 템플릿을 사용할 수도 있습니다.

* **스키마 호환 데이터를 생성할 수 있습니까?**
예. 적응형 양식을 생성하여 스키마 호환 데이터를 생성할 수 있습니다.

<!-- * **Can I pass custom parameters to the prefill service?**
Custom parameters are planned for an upcoming release. -->

* **보안 콘텐츠를 캐싱할 수 있습니까?**
보안 콘텐츠 캐싱 기능은 기본적으로 비활성화되어 있습니다. 이 기능을 활성화하려면 [보안 콘텐츠 캐싱](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=ko-KR)에 제공된 지침을 수행하면 됩니다.

* **현지화된 적응형 양식이 있습니다. 현지화된 버전을 렌더링하지 않습니까? 원인은 무엇이며 해결 방법은 무엇입니까?**

  현지화된 적응형 양식의 URL 규칙은 이제 URL에 로케일 지정을 지원합니다. 새로운 URL 규칙을 사용하면 Dispatcher 또는 CDN에서 현지화된 양식을 캐싱할 수 있습니다. Cloud Service 환경에서 URL 형식(`http://host:port/content/forms/af/<afName>.<locale>.html`)을 사용하여 `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` 대신 적응형 양식의 현지화된 버전을 요청합니다. Dispatcher 또는 CDN 캐싱을 사용하는 것이 좋습니다. 미리 입력된 양식의 렌더링 속도를 개선하는 데 도움이 됩니다.

* **적응형 양식을 업데이트했습니다. 고객이 업데이트된 버전을 사용할 수 없습니까?**
기본적으로 CDN은 5분마다 캐시를 &#x200B;&#x200B;새로 고치고 5분 동안 대기한 후 업데이트된 버전을 확인합니다.

* **적응형 양식의 서명 단계를 사용하여 브라우저 내 서명 경험을 만들 수 있습니까?**
아니요. [!DNL Forms] as a Cloud Service에 대해 서명 단계를 사용할 수 없습니다. 적응형 양식에서 서명 단계를 제거합니다. 서명 단계 대신 사용자가 제출 후 적응형 양식에 서명하도록 허용합니다. 브라우저 내 서명 경험을 계속 제공하는 데 도움이 됩니다.

* **적응형 양식에서 확인 단계를 사용할 수 있습니까?**
아니요. [!DNL Forms] as a Cloud Service에 대해 확인 단계를 사용할 수 없습니다. 이러한 양식을 Cloud Service 환경으로 이동하기 전에 기존 적응형 양식에서 유효성 검사 단계를 제거하십시오.

* **적응형 양식에 차트를 추가할 수 있습니까?**
예. 적응형 양식에 차트를 추가할 수 있습니다. 적응형 양식은 차트 구성 요소를 제공합니다. 이를 사용하여 적응형 양식에 차트를 추가할 수 있습니다.

* **FDM(양식 데이터 모델)을 관계형 데이터베이스 모델에 연결할 수 있습니까?**
FDM(양식 데이터 모델)을 [!DNL RESTful web services], [!DNL SOAP-based web services], [!DNL OData services]및 Experience Manager 사용자 프로필을 데이터 소스로 사용하는 옵션이 포함되어 있습니다. FDM(양식 데이터 모델)을 관계형 데이터베이스와 연결할 수 없습니다.

* **인증에 FDM(양식 데이터 모델)을 사용하는 사용자 정의 인증서를 사용할 수 있습니까?**
FDM(양식 데이터 모델)은 인증에 사용자 정의 인증서를 사용하는 방법을 제공하지 않습니다. 따라서 x509 및 양방향 SSL과 같은 사용자 정의 인증서는 지원되지 않습니다.

* **Forms Portal 제출 액션 적응형 양식을 사용할 수 있습니까?**

  기존 적응형 Forms을 수정하여 사용할 수 있습니다 [REST 끝점에 제출](configuring-submit-actions.md#submit-to-rest-endpoint), [이메일 보내기](configuring-submit-actions.md#send-email), [양식 데이터 모델(FDM)을 사용하여 제출](configuring-submit-actions.md#submit-using-form-data-model), 및 [AEM 워크플로우 호출](configuring-submit-actions.md#invoke-an-aem-workflow) 작업을 제출합니다. Forms 포털 및 Forms 포털 제출 액션은 아직 사용할 수 없습니다. 이들 기능의 가용성에 대한 정보는 월별 릴리스 정보를 참고하십시오.

* **[!DNL AEM Forms] as a Cloud Service와 함께 [!DNL AEM Forms] 앱을 사용할 수 있습니까?**

  적응형 양식은 반응형 디자인을 제공합니다. 이러한 양식은 기본 디바이스에 따라 모양, 디자인 및 인터랙티브 요소를 변경합니다. 기능의 가용성에 대해 월별 릴리스 정보를 참조하면서 모바일 디바이스에서 적응형 양식을 계속 사용할 수 있습니다.

* **초기 GA 릴리스에 포함되지 않은 기능은 무엇입니까?**
Forms Portal, [!DNL AEM Forms] 앱, Adobe Analytics와의 통합 및 Adobe Target과의 통합은 초기 GA 릴리스에 포함되지 않습니다. 새로운 기능에 대한 정보는 월별 릴리스 정보를 확인하십시오.

* **[JSON 스키마는 적응형 양식을 생성](adaptive-form-json-schema-form-model.md)하기 위해 설계되었습니다. JSON 스키마는 적응형 양식의 일부 구성 요소에 대한 이벤트를 정의합니다. AEM Forms as a Cloud Service는 이벤트를 지원합니까?**
Experience Manager 6.5 Forms 환경에서 JSON 스키마를 기반으로 적응형 양식을 생성하고 [마이그레이션 유틸리티](migrate-to-forms-as-a-cloud-service.md)를 사용하여 이러한 적응형 양식을 AEM Forms as a Cloud Service로 마이그레이션합니다. 유틸리티는 이러한 이벤트를 클라이언트 라이브러리로 변환하므로 Cloud Service 환경에서 이벤트에 대해 적응형 양식을 계속 사용할 수 있습니다.

<!-- 

* **Is there any AEM Forms as a Cloud Service connector for Microsoft Power Automate?**

  Yes, Adobe provides an Adobe Experience Manager connector to access [Adobe Experience Manager Forms - Communication capabilities](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html) through Microsoft Power Automate. You can create a PDF document that is based on a form design and XML form data or create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) and other Printer Definition Language documents. 

  You can get started with Adobe Experience Manager easily with just a few steps:

  1. Generate the Service credentials: Use Adobe Experience Manager Developer Console to [generate](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?#generate-service-credentials) the service credentials.  
  
  1. Setup your connection: Add your service credentials to the Adobe Experience Manager Connector. You can get crdential from service credential JSON and copy these credential details to your one-time connection setup:

    * AEM Server
    * Organization ID 
    * Client ID
    * Client Secret
    * Technical Account ID
    * Meta Scopes
    * Private Key - base64 encoded keys are accepted
    * Adobe IMS Host URL

    <br> 
    
    ![Use your Service Credential JSON for credential details](assets/forms-aem-pa-connector-connection.png)

    A sample Service Credential JSON file fields mapped to Adobe Experience Manager connector for Microsoft Power Automate.

    -->
