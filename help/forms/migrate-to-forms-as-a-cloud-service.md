---
title: 어떻게 AEM Forms as a Cloud Service 6.5 Forms에서 AEM으로 마이그레이션할 수 있습니까?
description: AEM as a Cloud Service으로 마이그레이션 여정 시작하기 | Adobe Experience Manager.  [!DNL AEM Forms] (On-Premise 및 AMS 환경)에서  [!DNL AEM Forms] as a Cloud Service 환경으로 마이그레이션합니다.
Keywords: 6.5 forms to cloud service, 6.5 forms to cs, migrate 6.5 forms to CS, migrate 6.5 forms to cloud service, upgrade 6.5 forms to CS, move 6.5 forms to CS, upgrade AEM 6.5 to CS, AEM Forms 6.5 to Cloud Service, AEM form migration to cloud service, Migration Journey to AEM as a Cloud Service | Adobe Experience Manager.
contentOwner: khsingh
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 1%

---

# [!DNL AEM Forms] (온-프레미스 및 AMS 환경)에서 &lbrace;1 an as a Cloud Service&rbrace;(으)로 마이그레이션[!DNL AEM Forms]  {#Harden-your-AEM-Forms-as-a-Cloud-Service-environment}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/upgrade-aem-forms/upgrade.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

적응형 Forms, 테마, 템플릿 및 클라우드 구성을 <!-- AEM 6.3 Forms AEM 6.4 Forms on OSGi and --> AEM 6.5 Forms as a Cloud Service on OSGi에서 [!DNL AEM] (으)로 마이그레이션하거나 업그레이드할 수 있습니다. as a Cloud Service 이러한 자산을 마이그레이션하기 전에 마이그레이션 유틸리티를 사용하여 이전 버전에서 사용된 형식을 [!DNL AEM] 형식으로 변환하십시오.
AEM as a Cloud Service으로의 마이그레이션 여정을 시작해 보겠습니다 | Adobe Experience Manager. 마이그레이션 유틸리티를 실행하면 다음 자산이 업데이트됩니다.

* 적응형 Forms에 대한 맞춤형 구성 요소
* 적응형 Forms 템플릿 및 테마
* 클라우드 구성
* 코드 편집기 스크립트는 재사용 가능한 기능으로 변환되고 시각적 규칙에 적용됩니다.

## Formsas a Cloud Service 로 마이그레이션할 고려 사항 {#consideration}

AEM 6.5 Forms에서 AEM Cloud Service으로 마이그레이션하려면 다음 사항을 고려해야 합니다.

* 이 서비스는 OSGi 환경의 [!DNL AEM Forms]에서만 콘텐츠를 마이그레이션하도록 도와줍니다. JEE의 [!DNL AEM Forms]에서 Cloud Service 환경으로 콘텐츠를 마이그레이션하는 작업은 지원되지 않습니다.

* (AEM 6.5 Forms 이전 버전만 해당) AEM 6.3 Forms as a Cloud Service 또는 이전 버전에서 사용할 수 있는 기본 제공 템플릿 및 테마를 기반으로 하는 적응형 Forms은 [!DNL AEM Forms]에서 지원되지 않습니다.

* Adobe Experience Manager Formsas a Cloud Service 는 Adobe Experience Manager Forms Adobe 6.5(On-Premise Managed Service) 환경과 몇 가지 주목할 만한 변경 사항을 제공합니다. 서비스로 마이그레이션을 진행하기 전에 [이 변경 사항에 대해 알아보고](notable-changes.md) [기능 수준의 차이점](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=ko#viewing-report)을 확인하여 조직에서 요구하는 기능을 기반으로 마이그레이션하기로 결정하십시오.




<!-- 
## Difference with AEM 6.5 Forms 

| Feature         | Difference with AEM 6.5 Forms    |
|--------------|-----------|
| HTML5 Forms (Mobile Forms)     | The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. |
| Adaptive Forms     | <li><b>XSD-Based Adaptive Forms:</b> The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. </li> <li><b> Adaptive Form templates:</b> Use build pipeline and corresponding Git repository of your program to import existing Adaptive Form templates. </li><li><b>Rule editor:</b> AEM Forms as a Cloud Service provides a hardened [Rule editor](rule-editor.md#visual-rule-editor). The code editor is not available on Forms as a Cloud Service. The migration utility helps you migrate your forms that have custom rules (created in code editor). The utility converts such rules into custom functions supported on Forms as a Cloud Service. You can use the reusable functions with Rule editor to continue obtaining results obtained with rule scripts  The `onSubmitError` or `onSubmitSuccess` functions are now available as actions the Rule Editor. </li> <li><b>Drafts and submissions:</b> The service does not retain metadata for drafts and submitted Adaptive Forms. </li> <li><b> Prefill Service:</b> By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server. </li><li><b>Submit actions:</b> The **Email as PDF** action is not available. The **Email** submit action provide options to send attachments and attach Document of Record (DoR) with email. </li>|
| Form Data Model | <li>Forms data model supports only HTTP and HTTPs endpoints to submit data. </li><li>Forms as a Cloud Service allows to use Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive, and services supporting general CRUD (Create, Read, Update, and Delete) operations as data stores. The service does not support JDBC connector, Mutual SSL for Rest connector, and x509 certificate-based authentication for SOAP data sources. </li>|
| Automated Forms Conversion Service     | The service does not provide meta-model for Automated Forms Conversion Service. You can [download it from Automated Forms Conversion Service documentation](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=ko#default-meta-model).|
|Configurations|<li>Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=ko#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment. </li> <li>If you use custom bundles, recompile your code with latest version of adobe-aemfd-docmanager before using these bundles with Forms as a Cloud Service.</li> |
| Document Manipulation APIs (Assembler Service)| The service does not support operations dependent on other services or applications: <li>Conversion of documents in a non-PDF format to a PDF format is not supported. For example, Microsoft Word to PDF, Microsoft Excel to PDF, and HTML to PDF are not supported</li><li>Adobe Distiller-based conversions are not supported. For example, PostScript(PS) to PDF</li><li>Forms Service-based conversions are not supported. For example, XDP to PDF Forms.</li><li>The service does not support converting a Signed PDF or Transparent PDF to another PDF format.</li>| -->

## 사전 요구 사항 {#prerequisites}

AEM Forms 6.5에서 AEM as a Cloud Service 환경으로 원활하게 전환하려면 다음 전제 조건을 고려하는 것이 중요합니다.

* Forms Cloud Service 프로그램에 대해 [Forms - 디지털 등록](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?lang=ko&#editing-program) 옵션을 사용하도록 설정하고 [파이프라인을 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=ko)합니다.

  ![시험 실행 결과](assets/enable-add-on.png)

* Cloud Service 환경에서 마이그레이션 유틸리티는 컨텐츠 전송 도구와 함께 작동합니다. 마이그레이션 유틸리티는 [!DNL AEM Forms]을(를) Cloud Serviceas a Cloud Service 과 호환되도록 만들고, 콘텐츠 전송 도구는 콘텐츠를 [!DNL AEM Forms] 환경에서 [!DNL AEM] 환경으로 마이그레이션합니다. 마이그레이션 유틸리티를 사용하기 전에 [AEM as a Cloud Service으로 이동](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html?lang=ko)하는 프로세스를 알아보십시오. 이 프로세스에서는 다음 도구를 사용합니다.
   * [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=ko&#cloud-migration): 컨텐츠 전송 도구를 사용하여 기존 환경에서 Cloud Service 환경으로 컨텐츠를 준비하고 전송할 수 있습니다. 사용자가 AEM Forms에서 클라우드 환경으로 쉽게 업그레이드할 수 있도록 지원합니다.
* as a Cloud Service [!DNL AEM Forms] 및 로컬 [!DNL AEM Forms] 환경에 대한 관리자 권한이 있는 계정입니다.
* [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 모범 사례 분석기, 콘텐츠 전송 도구 및 [!DNL AEM Forms] 마이그레이션 유틸리티를 다운로드하여 설치하십시오.

* [모범 사례 분석기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=ko#cloud-migration) 도구를 실행하고 보고된 문제를 해결합니다. Adobe Experience Manager Forms에서 Adobe Experience Manager Formsas a Cloud Service 로 마이그레이션하는 것과 관련된 가능한 문제에 대해서는 [Formsas a Cloud Service 에 대한 AEM 패턴 감지](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/using-best-practices-analyzer.html?lang=ko#viewing-report)를 참조하십시오.


<!-- * Download the latest [compatibility package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=ko#aem-65-forms-releases) for your [!DNL AEM Forms] version. -->




## [!DNL AEM 6.5 Forms]개의 자산을 AEM Cloud Service으로 마이그레이션 {#use-the-migration-utility}

[!DNL AEM Forms] 자산을 Cloud Serviceas a Cloud Service 과 호환되도록 하고 [!DNL AEM] 환경으로 전송하려면 다음 단계를 수행하십시오.

1. 기존 [!DNL AEM Forms] 환경의 [복제](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/correct-method-to-clone-the-aem-environment/qaq-p/363487?profile.language=ko)을(를) 만듭니다.

   >[!NOTE]
   >
   > 6.5에서 Cloud Service로 마이그레이션할 때는 복제된 환경을 사용하여 콘텐츠 전송 도구 및 마이그레이션 유틸리티를 실행하는 것이 좋습니다. 컨텐츠 전송 도구 및 마이그레이션 유틸리티는 컨텐츠 및 자산을 일부 변경합니다. 따라서 프로덕션 환경에서는 컨텐츠 전송 도구 나 마이그레이션 유틸리티를 실행하지 마십시오.

1. 관리자 권한으로 복제된 환경에 로그인합니다.

1. 복제된 환경에서 [콘텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=ko&#cloud-migration) 및 [ 소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)의 [!DNL AEM Forms] as a Cloud Service 마이그레이션 유틸리티를 다운로드하여 설치하십시오. AEM 패키지 관리자를 사용하여 도구 및 유틸리티를 설치할 수 있습니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 콘텐츠 마이그레이션]**&#x200B;으로 이동합니다.

1. **[!UICONTROL 마이그레이션을 위한 Forms 준비]** 카드를 엽니다. 브라우저에는 다섯 가지 옵션이 표시됩니다.
   * **[!UICONTROL AEM Forms Assets 마이그레이션]**
   * **[!UICONTROL 적응형 Forms 사용자 지정 구성 요소 마이그레이션]**
   * **[!UICONTROL 적응형 Forms 템플릿 마이그레이션]**
   * **[!UICONTROL AEM Forms 클라우드 구성 마이그레이션]**
   * **[!UICONTROL 코드 편집기 스크립트 마이그레이션]**

1. as a Cloud Service [!DNL AEM Forms] 자산을 [!DNL AEM]과(와) 호환되도록 하려면 옵션을 하나씩 사용하십시오.

   1. **[!UICONTROL AEM Forms Assets 마이그레이션]**&#x200B;을 선택하고 다음 화면에서 **[!UICONTROL 마이그레이션 시작]**&#x200B;을 선택합니다. [!DNL AEM Forms] 환경의 적응형 Forms as a Cloud Service 및 테마를 [!DNL AEM] 과(와) 호환되도록 합니다.

   1. **[!UICONTROL 적응형 Forms 사용자 지정 구성 요소 마이그레이션]**&#x200B;을 선택하고 사용자 지정 구성 요소 마이그레이션 페이지에서 **[!UICONTROL 마이그레이션 시작]**&#x200B;을 선택합니다. 적응형 Formsas a Cloud Service 용으로 개발된 모든 사용자 지정 구성 요소와 [!DNL AEM Forms] 환경의 구성 요소 오버레이가 [!DNL AEM] 과(와) 호환되도록 합니다.

   1. **[!UICONTROL 적응형 Forms 템플릿 마이그레이션]**&#x200B;을 선택하고 사용자 지정 구성 요소 마이그레이션 페이지에서 **[!UICONTROL 마이그레이션 시작]**&#x200B;을 선택합니다. `/apps` 또는 `/conf`에 있는 적응형 양식 템플릿을 만들고 AEM as a Cloud Service 템플릿 편집기를 사용하여 만들었으며 [!DNL AEM] 과(와) 호환됩니다.

   1. **[!UICONTROL AEM Forms 클라우드 구성 마이그레이션]**&#x200B;을 선택한 다음 구성 마이그레이션 페이지에서 **[!UICONTROL 마이그레이션 시작]**&#x200B;을 선택합니다. 다음 Cloud Service을 업데이트하고 새 위치로 이동합니다.

      * 양식 데이터 모델 Cloud Service
      * Google reCAPTCHA Cloud Service
      * [!DNL Adobe Sign] Cloud Service
      * Adobe Fonts Cloud Service

   1. **[!UICONTROL 코드 편집기 스크립트 마이그레이션]**&#x200B;을 선택하고, 재사용 가능한 기능을 저장할 위치를 지정하고, **[!UICONTROL 마이그레이션 시작]을 선택하십시오.

   Cloud Service은 규칙 편집기 스크립트를 지원하지 않습니다. **[!UICONTROL 코드 편집기 스크립트 마이그레이션]** 도구는 사용자 환경의 모든 규칙 스크립트를 재사용 가능한 함수로 변환하고 재사용 가능한 함수를 적절한 위치의 비주얼 편집기에 적용합니다. 이러한 재사용 가능한 기능은 클라이언트 라이브러리 형태로 저장되며 기존 기능을 그대로 유지하는 데 도움이 됩니다. 이 도구는 생성된 재사용 가능한 기능을 해당 적응형 Forms에 자동으로 적용합니다.

   Cloud Service으로 AEM Form 마이그레이션을 수행하려면 [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=ko#contentmanagement)를 사용하여 재사용 가능한 함수(클라이언트 라이브러리)를 패키지로 내보냅니다.

1. as a Cloud Service [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=ko#deploying-content-packages-via-cloud-manager-and-package-manager)재사용 가능한 함수(클라이언트 라이브러리) 패키지, [사용자 지정 코드, 구성 요소, 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html?lang=ko#cloud-manager), 사용자 지정 로케일별 라이브러리를 [!DNL AEM] 환경에 배포.

   <!-- 1. Install the latest [Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=ko&#cloud-migration) to your cloned [!DNL AEM Forms] environment. -->

1. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=ko&#cloud-migration)를 실행합니다. **[!UICONTROL 마이그레이션 세트 만들기]** 화면에서 매개 변수를 지정하는 동안 적응형 Forms, 테마, 템플릿, 양식 데이터 모델(FDM), Cloud Service, 사용자 지정 구성 요소 및 기타 AEM Forms 관련 자산의 경로를 **[!UICONTROL 포함할 경로]** 옵션에 지정하십시오. 지정된 [!DNL AEM Forms]개의 자산을 마이그레이션 세트에 추가합니다.

## 다양한 AEM Forms 관련 에셋의 경로

AEM Forms 6.5에서 Cloud Service로 마이그레이션할 때 다음 위치에서 AEM Forms 관련 에셋을 찾을 수 있습니다.

* **적응형 Forms**: `/content/dam/formsanddocuments/` 및 `/content/forms/af`에서 적응형 양식을 찾을 수 있습니다. 예를 들어 WKND 등록이라는 적응형 양식의 경우 경로 `/content/dam/formsanddocuments/wknd-registration` 및 `/content/forms/af/wknd-registration`을(를) 추가합니다.
* **양식 데이터 모델**: `/content/dam/formsanddocuments-fdm`에서 모든 양식 데이터 모델(FDM)을 찾을 수 있습니다. 예: `/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

* **클라이언트 라이브러리**: 클라이언트 라이브러리의 기본 경로는 `/etc/clientlibs/fd/theme`입니다.

* **적응형 양식 템플릿**: 템플릿의 기본 경로는 `/conf/<template folder>`입니다. 예를 들어, 기본 추가 경로 `/conf/ReferenceEditableTemplates/settings/wcm/templates/basic`이라는 이름의 템플릿에 대한 경우입니다.

* **적응형 양식 테마 및 클라이언트 라이브러리**: 테마의 기본 경로는 ` /content/dam/formsanddocuments-themes/`이고 클라이언트 라이브러리의 기본 경로는 `/etc/clientlibs/fd/theme`입니다. 예를 들어 WKND Theme이라는 템플릿의 경우 `/etc/clientlibs/reference-themes/wkndtheme-3-0`에 테마에 대한 ` /content/dam/formsanddocuments-themes/wkndtheme` 경로 및 클라이언트 라이브러리를 추가합니다. 다른 사용자 지정 경로에 테마와 클라이언트 라이브러리를 보유할 수도 있습니다.

* **클라우드 구성**: `/conf/`에서 클라우드 구성을 찾을 수 있습니다. 예를 들어 양식 데이터 모델(FDM) 클라우드 구성은 `/conf/global/settings/cloudconfigs/fdm`에 있습니다.

* **워크플로 모델**: `/conf/global/settings/workflow/models/`에서 AEM 워크플로 모델을 찾을 수 있습니다. 예를 들어 WKND 등록 이라는 워크플로우 모델의 경우 `/conf/global/settings/workflow/models/wknd-registration` 경로를 추가합니다.

아래 나열된 최상위 수준의 폴더 경로 또는 아래 설명된 특정 폴더 경로를 추가할 수 있습니다. AEM Forms 6.5에서 Cloud Service로 업그레이드할 때 특정 에셋과 모든 에셋 및 양식을 한 번에 마이그레이션할 수 있습니다.

* `/content/dam/formsanddocuments-fdm`
* `/content/dam/formsanddocuments/themes`
* `/content/forms/af`
* `/etc/clientlibs/fd/theme`

AEM Workflow 모델을 AEM Forms 6.5에서 Cloud Service으로 마이그레이션할 때 다음 경로를 지정하십시오.

* `/conf/global/settings/workflow/models/`
* `/conf/global/settings/workflow/launcher`
* `/var/workflow/models`

## 다음 보기

* [기존 Adobe Experience Manager 6.5 Forms 사용자의 주요 변경 내용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/notable-changes.html?lang=ko)
* [AEM Formsas a Cloud Service 에 온보드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service.html?lang=ko)
* [Cloud Service에서 첫 번째 적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html?lang=ko)

## 추가 정보

마이그레이션 유틸리티는 기초 구성 요소를 기반으로 적응형 Forms을 마이그레이션하는 데 도움이 됩니다. 또한 Formsas a Cloud Service 은 적응형 Forms 핵심 구성 요소를 지원합니다. 따라서 다음과 같은 작업을 수행할 수 있습니다.

* [독립형 적응형 Forms 기반의 핵심 구성 요소 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [AEM Sites 페이지에서 바로 핵심 구성 요소 기반 적응형 양식 만들기](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

AEM Formsas a Cloud Service 에 대해 자세히 알아보려면 다음을 참조하십시오.

* [AEM Forms Cloud Service 소개](/help/forms/home.md)
* [AEM Forms의 혁신 Cloud Service](/help/forms/latest-innovations.md)