---
title: AEM 6.5 Forms 및 AEM 6.4 Forms에서 로 마이그레이션하는 방법 [!DNL AEM Forms] as a Cloud Service 환경?
description: 다음에서 마이그레이션 [!DNL AEM Forms] On-Premise 환경 [!DNL AEM Forms] as a Cloud Service 환경
contentOwner: khsingh
feature: Adaptive Forms
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: b11979acc23efe5f1af690443180a6b456d589ed
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 8%

---

# [!DNL AEM Forms]as a Cloud Service로 마이그레이션  {#Harden-your-AEM-Forms-as-a-Cloud-Service-environment}

에서 응용 Forms, 테마, 템플릿 및 클라우드 구성을 마이그레이션할 수 있습니다 <!-- AEM 6.3 Forms--> OSGi의 AEM 6.4 Forms 및 OSGi의 AEM 6.5 Forms으로 [!DNL AEM] as a Cloud Service. 이러한 자산을 마이그레이션하기 전에 마이그레이션 유틸리티를 사용하여 이전 버전에서 사용된 형식을 에서 사용하는 형식으로 변환합니다 [!DNL AEM] as a Cloud Service. 마이그레이션 유틸리티를 실행하면 다음 자산이 업데이트됩니다.

* 응용 Forms용 사용자 지정 구성 요소
* 적응형 Forms 템플릿 및 테마
* 클라우드 구성
* 코드 편집기 스크립트는 재사용 가능한 함수로 변환되고 시각적 규칙에 적용됩니다.

## 고려 사항 {#consideration}

* 이 서비스는 콘텐츠만 마이그레이션하는 데 도움이 됩니다 [!DNL AEM Forms] OSGi 환경에서 사용할 수 있습니다. 다음에서 컨텐츠 마이그레이션 [!DNL AEM Forms] Cloud Service 환경에서 JEE의 는 지원되지 않습니다.

* (AEM 6.3 Forms 또는 AEM 6.4 Forms 또는 AEM 6.5 Forms으로 업그레이드된 이전 버전 환경의 경우에만 해당) AEM 6.3 Forms 또는 이전 버전에서 사용할 수 있는 기본 템플릿 및 테마를 기반으로 하는 적응형 Forms은 지원되지 않습니다 [!DNL AEM Forms] as a Cloud Service.

* 확인 단계를 사용할 수 없습니다. 이러한 양식을 Cloud Service 환경으로 이동하기 전에 기존 적응형 Forms에서 확인 단계를 제거합니다.

* 응용 Forms에 대한 서명 단계는 사용할 수 없습니다. 기존 적응형 양식에서 서명 단계를 제거하십시오. 브라우저 내 서명 경험을 사용하도록 적응형 양식을 구성하십시오. 브라우저 내 서명 경험은 적응형 양식 제출 시 브라우저 내에 서명할 Adobe Sign 계약서를 표시합니다. 브라우저 내 서명 경험은 서명 속도를 높이고 서명자의 시간을 절약하는 데 도움이 됩니다.

## AEM 6.5 Forms와의 차이점

| 기능 | AEM 6.5 Forms와의 차이점 |
|--------------|-----------|
| HTML5 Forms(모바일 Forms) | 이 서비스는 HTML 5 Forms(Mobile Forms)을 지원하지 않습니다. XDP 기반 양식을 HTML 5 Forms으로 렌더링하는 경우 AEM 6.5 Forms에서 기능을 계속 사용할 수 있습니다. |
| 적응형 양식 | <li><b>XSD 기반 응용 Forms:</b> 이 서비스는 HTML 5 Forms(Mobile Forms)을 지원하지 않습니다. XDP 기반 양식을 HTML 5 Forms으로 렌더링하는 경우 AEM 6.5 Forms에서 기능을 계속 사용할 수 있습니다. </li> <li><b> 적응형 양식 템플릿:</b> 빌드 파이프라인 및 프로그램의 해당 Git 저장소를 사용하여 기존 적응형 양식 템플릿을 가져옵니다. </li><li><b>규칙 편집기:</b> AEM Forms as a Cloud Service [규칙 편집기](rule-editor.md#visual-rule-editor). 코드 편집기는 Forms as a Cloud Service에서 사용할 수 없습니다. 마이그레이션 유틸리티는 코드 편집기에서 만든 사용자 지정 규칙이 있는 양식을 마이그레이션하는 데 도움이 됩니다. 이 유틸리티는 이러한 규칙을 Forms as a Cloud Service에서 지원되는 사용자 지정 함수로 변환합니다. 규칙 편집기와 함께 재사용 가능한 함수를 사용하여 규칙 스크립트로 얻은 결과를 계속 얻을 수 있습니다. `onSubmitError` 또는 `onSubmitSuccess` 이제 함수를 규칙 편집기에서 작업으로 사용할 수 있습니다. </li> <li><b>초안 및 제출:</b> 이 서비스는 초안 및 제출된 적응형 Forms에 대한 메타데이터를 유지하지 않습니다. </li> <li><b> 미리 채우기 서비스:</b> 기본적으로 미리 채우기 서비스는 AEM 6.5 Forms에서 서버의 데이터를 병합하는 대신 클라이언트의 적응형 양식과 데이터를 병합합니다. 이 기능은 적응형 양식을 미리 채우는 데 필요한 시간을 개선하는 데 도움이 됩니다. 항상 Adobe Experience Manager Forms 서버에서 병합 작업을 실행하도록 구성할 수 있습니다. </li><li><b>작업 제출:</b> 다음 **전자 메일을 PDF으로 보내기** 작업을 사용할 수 없습니다. 다음 **이메일** 제출 작업은 첨부 파일을 보내고 전자 메일에 기록 문서(DoR)를 첨부하는 옵션을 제공합니다. </li> |
| 양식 데이터 모델 | <li>Forms 데이터 모델은 데이터를 제출할 HTTP 및 HTTP 끝점만 지원합니다. </li><li>Forms as a Cloud Service에서는 일반 CRUD(만들기, 읽기, 업데이트 및 삭제) 작업을 지원하는 Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive 및 서비스를 데이터 저장소로 사용할 수 있습니다. 이 서비스는 JDBC 커넥터, Rest 커넥터에 대한 상호 SSL 및 SOAP 데이터 소스에 대한 x509 인증서 기반 인증을 지원하지 않습니다. </li> |
| automated forms conversion 서비스 | 이 서비스는 Automated forms conversion 서비스에 대한 메타 모델을 제공하지 않습니다. 다음을 수행할 수 있습니다 [automated forms conversion 서비스 설명서에서 다운로드](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model). |
| 구성 | <li>이메일은 기본적으로 HTTP 및 HTTP 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) 전자 메일 전송을 위한 포트를 활성화하고 환경에 대해 SMTP 프로토콜을 사용하도록 설정합니다. </li> <li>사용자 지정 번들을 사용하는 경우 Forms as a Cloud Service에서 이러한 번들을 사용하기 전에 최신 버전의 adobe-aemfd-docmanager로 코드를 다시 컴파일하십시오.</li> |
| 문서 조작 API(어셈블러 서비스) | 서비스는 다른 서비스 또는 응용 프로그램에 종속된 작업을 지원하지 않습니다. <li>PDF이 아닌 형식의 문서를 PDF 형식으로 변환할 수 없습니다. 예를 들어 Microsoft Word에서 PDF으로, Microsoft Excel에서 PDF으로, PDF으로 HTML은 지원되지 않습니다</li><li>Adobe Distiller 기반 전환은 지원되지 않습니다. 예를 들어 PostScript(PS)에서 PDF</li><li>Forms 서비스 기반 전환은 지원되지 않습니다. 예를 들어 XDP에서 PDF forms으로 이동합니다.</li><li>이 서비스는 서명된 PDF 또는 투명 PDF을 다른 PDF 형식으로 변환하는 것을 지원하지 않습니다.</li> |

## 사전 요구 사항 {#prerequisites}

* [Forms 활성화 - 디지털 등록](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?#editing-program) Forms Cloud Service 프로그램 및 [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

   ![시험 실행 결과](assets/enable-add-on.png)

* Cloud Service 환경에서 마이그레이션 유틸리티는 사용자 매핑 도구 및 컨텐츠 전송 도구와 함께 작동합니다. 마이그레이션 유틸리티는 다음을 수행합니다 [!DNL AEM Forms] Cloud Service 및 컨텐츠 전송 도구와 호환되는 자산은 사용자의 자산에서 컨텐츠를 마이그레이션합니다 [!DNL AEM Forms] 환경 [!DNL AEM] as a Cloud Service 환경. 마이그레이션 유틸리티를 사용하기 전에 [AEM으로 이동 as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html). 이 프로세스에는 다음의 두 가지 도구가 있습니다.
   * [사용자 매핑 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration): 사용자 매핑 도구는 사용자를 해당 Adobe IMS 사용자 계정에 매핑하도록 도와줍니다.
   * [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration): 컨텐츠 전송 도구를 사용하면 기존 환경의 컨텐츠를 준비하고 Cloud Service 환경으로 전송할 수 있습니다.
* 관리자 권한이 있는 계정 [!DNL AEM Forms] as a Cloud Service 및 지역 [!DNL AEM Forms] 환경.
* 모범 사례 분석기, 컨텐츠 전송 도구 및 를 다운로드하여 설치합니다 [!DNL AEM Forms] 마이그레이션 유틸리티 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)

* 를 실행합니다. [모범 사례 분석기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) 도구를 사용하여 보고된 문제를 수정했습니다.

<!-- * Download the latest [compatibility package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases) for your [!DNL AEM Forms] version. -->

## 마이그레이션 [!DNL AEM Forms] assets  {#use-the-migration-utility}

다음 단계를 수행하여 다음을 수행합니다. [!DNL AEM Forms] Cloud Service과 호환되는 자산으로 전송 [!DNL AEM] as a Cloud Service 환경.

1. 만들기 [복제](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/correct-method-to-clone-the-aem-environment/qaq-p/363487) 기존 [!DNL AEM Forms] 환경.

   컨텐츠 전송 도구 및 마이그레이션 유틸리티를 실행하려면 항상 복제된 환경을 사용하십시오. 컨텐츠 전송 도구 및 마이그레이션 유틸리티를 사용하여 컨텐츠 및 자산을 일부 변경할 수 있습니다. 따라서 프로덕션 환경에서 컨텐츠 전송 도구 및 마이그레이션 유틸리티를 실행하지 마십시오.

1. 관리 권한으로 복제 환경에 로그인합니다.

1. 를 실행합니다. [사용자 매핑 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration) 사용자를 해당 Adobe IMS 사용자 계정에 매핑합니다. 에 로그인하려면 Adobe IMS 사용자 계정이 필요합니다 [!DNL AEM Forms] as a Cloud Service 인스턴스.

1. 를 다운로드하여 설치합니다. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) 및 [!DNL AEM Forms] as a Cloud Service 마이그레이션 유틸리티 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 복제 환경. AEM Package Manager를 사용하여 도구 및 유틸리티를 설치할 수 있습니다.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 컨텐츠 마이그레이션]**.

1. 를 엽니다. **[!UICONTROL Forms 마이그레이션 준비]** 카드. 브라우저에는 5개의 옵션이 표시됩니다.
   * **[!UICONTROL AEM Forms 에셋 마이그레이션]**
   * **[!UICONTROL 응용 Forms 사용자 지정 구성 요소 마이그레이션]**
   * **[!UICONTROL 적응형 Forms 템플릿 마이그레이션]**
   * **[!UICONTROL AEM Forms 클라우드 구성 마이그레이션]**
   * **[!UICONTROL 코드 편집기 스크립트 마이그레이션]**

1. 다음 옵션을 사용하여 [!DNL AEM Forms] 와 호환되는 자산 [!DNL AEM] as a Cloud Service:

   1. 탭 **[!UICONTROL AEM Forms 자산 마이그레이션]**, 그리고 다음 화면에서 를 누릅니다. **[!UICONTROL 마이그레이션 시작]**. 응용 Forms 및 테마를 [!DNL AEM Forms] 환경 호환 [!DNL AEM] as a Cloud Service .

   1. 탭 **[!UICONTROL 응용 Forms 사용자 지정 구성 요소 마이그레이션]** 사용자 지정 구성 요소 마이그레이션 페이지에서 **[!UICONTROL 마이그레이션 시작]**. 여기에는 적응형 Forms 및 구성 요소 오버레이용으로 개발된 모든 사용자 지정 구성 요소가 [!DNL AEM Forms] 환경 호환 [!DNL AEM] as a Cloud Service .

   1. 탭 **[!UICONTROL 적응형 Forms 템플릿 마이그레이션]** 사용자 지정 구성 요소 마이그레이션 페이지에서 **[!UICONTROL 마이그레이션 시작]**. /apps 또는 /conf에 있는 적응형 양식 템플릿을 만들고 이 템플릿과 호환되는 AEM 템플릿 편집기를 사용하여 만듭니다. [!DNL AEM] as a Cloud Service .

   1. 탭 **[!UICONTROL AEM Forms Cloud 구성 마이그레이션]** 구성 마이그레이션 페이지에서 **[!UICONTROL 마이그레이션 시작]**. 다음 Cloud Services을 업데이트하고 새 위치로 이동합니다.

      * 양식 데이터 모델 Cloud Service
      * Google reCAPTCHA Cloud Service
      * [!DNL Adobe Sign] 클라우드 서비스
      * Adobe Fonts Cloud Service
   1. 탭 **[!UICONTROL 코드 편집기 스크립트 마이그레이션]**&#x200B;를 클릭하고 재사용 가능한 기능을 저장할 위치를 지정하고 **[!UICONTROL 마이그레이션 시작].

   Cloud Service은 규칙 편집기 스크립트를 지원하지 않습니다. 다음 **[!UICONTROL 코드 편집기 스크립트 마이그레이션]** 도구는 환경의 모든 규칙 스크립트를 재사용 가능한 함수로 변환하고 재사용 가능한 함수를 적절한 위치에서 시각적 편집기에 적용합니다. 이러한 재사용 가능한 함수는 클라이언트 라이브러리 형태로 저장되고 기존 기능을 그대로 유지하는 데 도움이 됩니다. 이 도구는 생성된 재사용 가능한 함수를 해당 적응형 Forms에 자동으로 적용합니다.

   를 사용하십시오 [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement) 재사용 가능한 함수(클라이언트 라이브러리)를 패키지로 내보내기

1. [배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#deploying-content-packages-via-cloud-manager-and-package-manager) 재사용 가능한 함수(클라이언트 라이브러리) 패키지, [사용자 지정 코드, 구성 요소, 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html#cloud-manager), 사용자 지정 로케일 특정 라이브러리를 [!DNL AEM] as a Cloud Service 환경.

   <!-- 1. Install the latest [Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) to your cloned [!DNL AEM Forms] environment. -->

1. 를 실행합니다. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration). 에서 매개 변수를 지정하는 동안 **[!UICONTROL 마이그레이션 세트 만들기]** 화면에서 적응형 Forms, 테마, 템플릿, 양식 데이터 모델, Cloud Services, 사용자 지정 구성 요소 및 기타 AEM Forms 관련 자산의 경로를 **[!UICONTROL 포함할 경로]** 선택 사항입니다. 지정된 항목이 추가됩니다 [!DNL AEM Forms] 자산이 마이그레이션 세트에 포함되어 있습니다.

## 다양한 AEM Forms 관련 자산의 경로

* **응용 Forms**: 에서 적응형 양식을 찾을 수 있습니다 `/content/dam/formsanddocuments/`및 /content/forms/af. 예를 들어 WKND Registration이라는 적응형 양식의 경우 경로를 추가합니다 `/content/dam/formsanddocuments/wknd-registration` 및 `/content/forms/af/wknd-registration`.
* **양식 데이터 모드**: 모든 양식 데이터 모델은 `/content/dam/formsanddocuments-fdm`. (예: `/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`)

* **클라이언트 라이브러리**: 클라이언트 라이브러리의 기본 경로는 입니다. `/etc/clientlibs/fd/theme`.

* **적응형 양식 템플릿**: 템플릿의 기본 경로는 다음과 같습니다 `/conf/<template folder>`. 예를 들어 기본 추가 경로라는 템플릿의 경우 `/conf/ReferenceEditableTemplates/settings/wcm/templates/basic`.

* **적응형 양식 테마 및 클라이언트 라이브러리**: 테마의 기본 경로는 다음과 같습니다 ` /content/dam/formsanddocuments-themes/` 클라이언트 라이브러리의 기본 경로는 입니다. `/etc/clientlibs/fd/theme`. 예를 들어 WKND 테마 추가 경로라는 이름의 템플릿의 경우 ` /content/dam/formsanddocuments-themes/wkndtheme` 및 의 테마를 위한 클라이언트 라이브러리 `/etc/clientlibs/reference-themes/wkndtheme-3-0`. 다른 사용자 지정 경로에 테마 및 클라이언트 라이브러리를 보유할 수도 있습니다.

* **클라우드 구성**: 에서 클라우드 구성을 찾을 수 있습니다. `/conf/`. 예를 들어 양식 데이터 모델 클라우드 구성은 입니다 `/conf/global/settings/cloudconfigs/fdm`.

* **워크플로우 모델**: AEM 워크플로우 모델은 `/conf/global/settings/workflow/models/`. 예를 들어 WKND Registration이라는 워크플로우 모델의 경우 경로 추가 `/conf/global/settings/workflow/models/wknd-registration`

아래에 나열된 최상위 폴더 경로나 아래에 설명된 대로 특정 폴더 경로를 추가할 수 있습니다. 특정 자산과 모든 자산 및 양식을 한 번에 마이그레이션할 수 있도록 해줍니다.

* /content/dam/formsanddocuments-fdm
* /content/dam/formsanddocuments/themes
* /content/forms/af
* /etc/clientlibs/fd/테마

AEM 워크플로우 모델을 마이그레이션하려면 다음 경로를 지정합니다.

* /conf/global/settings/workflow/models/
* /conf/global/settings/workflow/launcher
* /var/workflow/models
