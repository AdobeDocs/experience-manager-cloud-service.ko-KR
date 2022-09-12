---
title: AEM 6.5 Forms 및 AEM 6.4 Forms에서 로 마이그레이션하는 방법 [!DNL AEM Forms] as a Cloud Service 환경?
description: 다음에서 마이그레이션 [!DNL AEM Forms] On-Premise 환경 [!DNL AEM Forms] as a Cloud Service 환경
contentOwner: khsingh
feature: Adaptive Forms
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: 8e28cff5b964005278858b6c8dd8a0f5f8156eaa
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 3%

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
