---
title: Forms as a Cloud Service 자주 묻는 질문
description: Forms as a Cloud Service 자주 묻는 질문
contentOwner: khsingh
exl-id: 0b14b680-7da5-4e0b-bd6a-c379d148f9d7
index: false
source-git-commit: 6355a6241c5b53585b80b2c2bc00556297766b49
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 3%

---

# 자주 묻는 질문 {#frequently-asked-questions}

* **코드 편집기를 사용하여 규칙을 만들 수 있습니까?**
시각적 편집기를 사용하여 규칙을 만들 수 있습니다. 코드 편집기는 [!DNL Forms] as a Cloud Service. 적응형 양식이 코드 편집기를 사용하여 개발된 규칙 스크립트를 사용하는 경우 [마이그레이션 유틸리티](migrate-to-forms-as-a-cloud-service.md) 코드 스크립트를 사용자 지정 함수로 변환하려면 다음을 수행하십시오. 시각적 편집기와 함께 사용자 지정 함수를 사용하여 코드 편집기로 얻은 결과를 계속 가져올 수 있습니다.

* **Cloud Service 인스턴스에 XFA 기반 적응형 양식을 만들 수 있습니까?**
예. Cloud Service 인스턴스에 XFA 기반 적응형 양식을 만들 수 있습니다. 그러나 AEM Forms as a Cloud Service SDK(로컬 개발 환경)에는 XFA 기반 적응형 Forms에 대한 지원을 사용할 수 없습니다. AEM Forms as a Cloud Service SDK와 함께 XFA 기반 적응형 Forms을 사용하려면 Adobe 지원 센터에 사용 사례 및 특정 요구 사항에 대한 자세한 내용을 문의하십시오.

<!-- * **Can I use an XDP as a Document of Record (DoR) template? Is Forms Designer included in AEM Forms as a Cloud Service license?** 

  Yes, you can use an XDP as a Document of Record template on Cloud Service instances. However, support to use XDP as a Document of Record template is not available for AEM Forms as a Cloud Service SDK (Local development environment). -->

* **컨텐츠를 온-프레미스에서 마이그레이션하거나 [!DNL Adobe-Managed Services] 환경 [!DNL Forms] as a Cloud Service 환경?**
예, 사용자 지정 코드, 컨텐츠 및 자산을 온-프레미스 또는 [!DNL Adobe-Managed Services] 환경 [!DNL Forms] as a Cloud Service 환경. 자세한 지침은 [Forms으로 마이그레이션 as a Cloud Service](migrate-to-forms-as-a-cloud-service.md).

<!-- You can use package manager or Experience Manager UI to [export and import Forms and related assets](import-export-forms-templates.md), use the migration utility to make your existing assets compatible with [!DNL Forms] as a Cloud Service, use the [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#best-practices-analyzer) tool to find the features and APIs that require changes and updated before migration, and use the [Content Transfer Tools](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/home.html) to move your custom code without refactoring it. -->

* **AEM은 어디서 구할 수 있나요 [!DNL Forms] as a Cloud Service [!DNL Java™] API 참조 설명서?**
에서 Java™ API 참조 설명서를 다운로드할 수 있습니다. [!DNL Maven Central Repository]. 다운로드하려면:
   1. 이동 [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. 최신 버전의 가 포함된 페이지를 찾아 엽니다. [!DNL Experience Manager Forms] SDK.
   1. 모든 파일을 보려면 모두 보기 옵션을 클릭합니다.
   1. 다운로드 및 추출 `aem-forms-sdk-api-<version>-javadocs`.jar
   1. index.html 파일을 열어 API 참조 설명서를 확인합니다.

* **어디로 가야 하나요 [!DNL JavaScript™] 응용 Forms에 대한 API 참조?**
다운로드 가능 [!DNL JavaScript™] 다음에서 API 참조 설명서[!DNL  Maven Central Repository]. 다운로드하려면:
   1. 열기 [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. 최신 버전의 가 포함된 페이지를 찾아 엽니다. [!DNL Experience Manager Forms] SDK.
   1. 모든 파일을 보려면 모두 보기 옵션을 클릭합니다.
   1. 다운로드 및 추출 `aem-forms-sdk-api-<version>-jsdoc.jar`.
   1. index.html 파일을 열어 API 참조 설명서를 확인합니다.

* **기존 테마 및 템플릿을 계속 사용할 수 있습니까?**
예. 테마를 사용한 후 AEM 6.4 Forms 및 AEM 6.5 Forms으로 만든 테마를 계속 사용할 수 있습니다. [마이그레이션 유틸리티](migrate-to-forms-as-a-cloud-service.md) 이동 [!DNL AEM Forms] as a Cloud Service.

   을 기반으로 프로젝트를 만들 수도 있습니다 [!DNL AEM Forms] as a Cloud Service [원형](setup-local-development-environment.md#forms-cloud-service-local-development-environment) 포함된 샘플 테마 및 템플릿을 사용합니다.

* **스키마 준수 데이터를 생성할 수 있습니까?**
예. 적응형 Forms을 만들어 스키마 준수 데이터를 생성할 수 있습니다.

<!-- * **Can I pass custom parameters to the prefill service?**
Custom parameters are planned for an upcoming release. -->

* **보안 콘텐츠를 캐시할 수 있습니까?**
보안 콘텐츠 기능 캐싱은 기본적으로 비활성화됩니다. 이 기능을 활성화하려면 [보안 콘텐츠 캐싱](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=ko-KR).

* **현지화된 적응형 양식; 현지화된 버전을 렌더링하고 있지 않습니까? 원인이 무엇이고 어떻게 해결할 수 있습니까?**

   현지화된 적응형 Forms의 URL 규칙은 이제 URL에서 로케일 지정을 지원합니다. 새 URL 규칙을 사용하면 Dispatcher 또는 CDN에 현지화된 양식을 캐싱할 수 있습니다. Cloud Service 환경에서 URL 형식을 사용합니다 `http://host:port/content/forms/af/<afName>.<locale>.html` 를 입력하여 대신 현지화된 적응형 양식 버전을 요청합니다. `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe은 Dispatcher 또는 CDN 캐싱을 사용하는 것을 권장합니다. 미리 입력된 양식의 렌더링 속도를 개선하는 데 도움이 됩니다.

* **적응형 양식을 업데이트했습니다. 업데이트된 버전을 고객이 사용할 수 있습니까?**
기본적으로 CDN은 5분마다 캐시를 새로 고침하고 5분 정도 기다렸다가 업데이트된 버전을 확인합니다.

* **적응형 양식의 서명 단계를 사용하여 브라우저 내 서명 경험을 만들 수 있습니까?**
아니요. 서명 단계는 [!DNL Forms] as a Cloud Service. 응용 Forms에서 서명 단계를 제거합니다. 사용자가 제출 후 서명 단계 대신 적응형 양식에 서명할 수 있도록 허용합니다. 따라서 브라우저 내 서명 환경을 계속 제공할 수 있습니다.

* **적응형 양식에서 확인 단계를 사용할 수 있습니까?**
아니요. 확인 단계는 [!DNL Forms] as a Cloud Service. 이러한 양식을 Cloud Service 환경으로 이동하기 전에 기존 적응형 Forms에서 확인 단계를 제거합니다.

* **적응형 양식에 차트를 추가할 수 있습니까?**
예, 차트를 응용 Forms에 추가할 수 있습니다. 적응형 Forms은 차트 구성 요소를 제공합니다. 이 차트를 사용하여 적응형 양식에 차트를 추가할 수 있습니다.

* **양식 데이터 모델을 관계형 데이터베이스 모델에 연결할 수 있습니까?**
양식 데이터 모델을 [!DNL RESTful web services], [!DNL SOAP-based web services], [!DNL OData services], 및 사용자 프로필을 데이터 소스로 Experience Manager. 관계형 데이터베이스에 양식 데이터 모델을 연결할 수 없습니다.

* **인증에 양식 데이터 모델과 함께 사용자 지정 인증서를 사용할 수 있습니까?**
양식 데이터 모델은 인증에 사용자 지정 인증서를 사용하는 메서드를 제공하지 않습니다. 따라서 x509 및 양방향 SSL과 같은 사용자 지정 인증서는 지원되지 않습니다.

* **Forms Portal 제출 작업 적응형 Forms을 사용할 수 있습니까?**

   기존 적응형 Forms을 수정하여 사용할 수 있습니다 [REST 엔드포인트에 제출](configuring-submit-actions.md#submit-to-rest-endpoint), [이메일 보내기](configuring-submit-actions.md#send-email), [양식 데이터 모델을 사용하여 제출](configuring-submit-actions.md#submit-using-form-data-model), 및 [AEM 워크플로우 호출](configuring-submit-actions.md#invoke-an-aem-workflow) 작업을 제출합니다. Forms 포털 및 Forms 포털 제출 작업은 아직 사용할 수 없습니다. 월별 릴리스 노트에서 기능을 이용할 수 있는지 확인하십시오.

* **사용할 수 있나요 [!DNL AEM Forms] 앱 사용 [!DNL AEM Forms] as a Cloud Service?**

   적응형 양식은 반응형 디자인을 제공합니다. 이러한 양식은 기본 디바이스에 따라 모양, 디자인 및 인터랙티브 요소를 변경합니다. 모바일 장치에서 응용 Forms을 계속 사용할 수 있지만, 기능을 사용할 수 있는지 여부에 대한 월별 릴리스 노트는 계속 사용할 수 있습니다.

* **초기 GA 릴리스의 일부가 아닌 기능은 무엇입니까?**
Forms 포털, [!DNL AEM Forms] 앱, Adobe Analytics와의 통합 및 Adobe Target과의 통합은 초기 GA 릴리스의 일부가 아닙니다. 새로운 기능에 대한 정보는 월별 릴리스 노트를 참조하십시오.

* **저는 [적응형 양식을 만들기 위한 JSON 스키마](adaptive-form-json-schema-form-model.md). JSON 스키마는 적응형 양식의 일부 구성 요소에 대한 이벤트를 정의합니다. AEM Forms은 이벤트를 as a Cloud Service으로 지원합니까?**
Experience Manager 6.5 Forms 환경에서 JSON 스키마를 기반으로 하여 적응형 양식을 작성하고 을 사용합니다. [마이그레이션 유틸리티](migrate-to-forms-as-a-cloud-service.md) 이러한 적응형 Forms을 AEM Forms as a Cloud Service으로 마이그레이션하려면 다음을 수행하십시오. 이 유틸리티는 이러한 이벤트를 클라이언트 라이브러리로 변환하며 Cloud Service 환경에서 이벤트와 함께 응용 Forms을 계속 사용할 수 있습니다.

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


