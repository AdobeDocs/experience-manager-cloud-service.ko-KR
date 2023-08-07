---
title: AEM 6.5 Forms과 AEM Cloud Services의 차이점
description: Experience Manager Forms 사용자이며 Adobe Experience Manager Forms as a Cloud Service으로 업그레이드하고자 하십니까? AEM 6.5 Forms과 AEM Cloud Services를 비교하고 Cloud Service으로 업그레이드하거나 마이그레이션하기 전에 가장 두드러진 변경 사항에 대해 알아봅니다.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: 57acac078805bc195cb10c1e94462d5aa077b1af
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# 기존 Adobe Experience Manager 6.5 Forms 사용자의 주요 변경 사항  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service은 Adobe Experience Manager Forms 온-프레미스 및 와 비교하여 기존 기능에 몇 가지 주목할 만한 변경 사항을 제공합니다 [!DNL Adobe-Managed Service] 환경. 주요 차이점은 아래에 나와 있습니다.

## 클라우드 네이티브 기능

* 이 서비스에는 로드, 무중단 업그레이드, 새로운 기능 및 업데이트 출시 후 빈번한 가동 중지 시간, 최대 복원력 및 효율성에 최적화된 토폴로지 등에 따라 자동 확장이 가능한 클라우드 기반 아키텍처가 있습니다.

* 이 서비스에는 Adobe Experience Manager Cloud Service 인스턴스에 데이터를 저장하는 제출 작업이 포함되어 있지 않으므로 매우 안전합니다. 양식을 통해 캡처된 데이터는 구성된 데이터 저장소로 직접 전송됩니다.

* 양식을 더 빠른 속도로 전달하고 렌더링하는 데 도움이 되는 무료 CDN(콘텐츠 전달 네트워크)도 포함되어 있습니다.


## 개발 흐름에 대한 업데이트

* 이 서비스는 Cloud Service에 코드를 배포하기 전에 로컬 환경(로컬 컴퓨터)에서 사용자 지정 코드를 개발하고 테스트하는 SDK를 제공합니다. 개발자는 로컬 컴퓨터에서 SDK를 사용하여 사용자 지정 구성 요소, 테마, 워크플로 애플리케이션, 구성, 템플릿 등을 개발 및 테스트합니다. 로컬 개발 환경에서 사용자 지정 코드를 테스트한 후 사용자 지정 코드를 [Forms CS 환경 개발 또는 스테이징 환경](/help/implementing/cloud-manager/deploy-code.md) 프로덕션 환경으로 승격하기 전에 추가 테스트를 위해

* 개발자는 Cloud Service 및 로컬 개발 환경에 대한 코드를 공통적으로 유지 관리합니다 [git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). AEM Archetype을 기반으로 하는 git 저장소는 AEM as a Cloud Service 프로그램 생성 시 자동으로 생성됩니다.

  ![AEM as a cloud service 프로그램에서 git 저장소 자동 생성](/help/forms/assets/git-repo-local-and-forms-cs.png)

* Forms의 개발 흐름은 AEM Cloud Service용 AEM Archetype에 as a Cloud Service으로 맞춰집니다. 그러나 Adobe Experience Manager Maven 프로젝트가 AEM Cloud Service과 호환되도록 하려면 몇 가지 변경이 필요합니다. 높은 수준에서 AEM은 변경 가능한 콘텐츠와 변경 불가능한 콘텐츠 사이의 분할을 준수하기 위해 콘텐츠와 코드를 개별 하위 패키지로 분리해야 합니다. 사용 [저장소 현대화 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환될 수 있도록 콘텐츠와 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성했습니다.

* Forms as a Cloud Service으로 고객 번들을 사용하기 전에 최신 버전의 adobe-aemfd-docmanager로 사용자 지정 코드를 다시 컴파일하십시오.

* 사용 [AEM Forms as a Cloud Service 마이그레이션 유틸리티](/help/forms/migrate-to-forms-as-a-cloud-service.md) 적응형 Forms, 테마, 템플릿 및 클라우드 구성을 준비하고 마이그레이션하려면 <!-- AEM 6.3 Forms--> OSGi의 AEM 6.4 Forms 및 OSGi의 AEM 6.5 Forms [!DNL AEM] as a Cloud Service. 사용 [프로그램의 Git 저장소](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) 기존 적응형 양식 템플릿을 가져오려면 다음을 수행하십시오.

* 기본적으로 이메일은 HTTP 및 HTTPs 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) 이메일 전송을 위한 포트를 활성화하고 환경에 대한 SMTP 프로토콜을 활성화합니다.

## 로컬라이제이션

* 현지화된 적응형 Forms의 URL 규칙은 이제 URL에서 로케일 지정을 지원합니다. 새 URL 규칙을 사용하면 Dispatcher 또는 CDN에서 현지화된 양식을 캐싱할 수 있습니다. Cloud Service 환경에서 URL 형식을 사용합니다 `http://host:port/content/forms/af/<afName>.<locale>.html` 을(를) 대신해 지역화된 버전의 적응형 양식을 요청하려면 `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe Dispatcher 또는 CDN 캐싱을 사용하는 것이 좋습니다. 미리 채워진 양식의 렌더링 속도를 개선하는 데 도움이 됩니다.


## 적응형 양식

* **규칙 편집기:** AEM Forms은 강화 기능을 as a Cloud Service으로 제공합니다 [규칙 편집기](rule-editor.md#visual-rule-editor). 코드 편집기는 Forms as a Cloud Service으로 사용할 수 없습니다.

  다음 [마이그레이션 유틸리티](/help/forms/migrate-to-forms-as-a-cloud-service.md) 는 사용자 지정 규칙(코드 편집기에서 생성)이 있는 양식을 마이그레이션하는 데 도움이 됩니다. 유틸리티는 이러한 규칙을 Forms as a Cloud Service에서 지원되는 사용자 지정 함수로 변환합니다. 규칙 편집기와 함께 재사용 가능한 기능을 사용하여 규칙 스크립트로 얻은 결과를 계속 얻을 수 있습니다. 다음 `onSubmitError` 또는 `onSubmitSuccess` 이제 함수를 규칙 편집기에서 작업으로 사용할 수 있습니다.

* **미리 채우기 서비스:** 기본적으로 미리 채우기 서비스는 AEM 6.5 Forms의 서버에서 데이터를 병합하는 것과 반대로 클라이언트에서 데이터를 적응형 양식과 병합합니다. 이 기능은 적응형 양식을 미리 채우는 데 필요한 시간을 개선하는 데 도움이 됩니다. Adobe Experience Manager Forms 서버에서 병합 작업을 실행하도록 언제든지 구성할 수 있습니다.

* **제출 액션:** 다음 **이메일** 제출 액션은 첨부 파일을 전송하고 이메일에 기록 문서(DoR)를 첨부할 수 있는 옵션을 제공합니다. 대신 사용할 수 있습니다. **전자 메일을 PDF으로** 작업은 AEM 6.5 Forms에서 사용할 수 있습니다.

* **Automated forms conversion 서비스**: 서비스가 Automated forms conversion 서비스에 대한 메타 모델을 제공하지 않습니다. 다음을 수행할 수 있습니다. [automated forms conversion 서비스 설명서에서 다운로드합니다](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

* **XSD 기반 적응형 Forms:** XDP-template을 사용하여 기록 문서에 대한 템플릿을 디자인할 수 있습니다. 이 서비스는 XFA 기반 적응형 Forms을 지원하지 않습니다

* **구성 요소**: 다음을 사용할 수 있습니다 [적응형 Forms 핵심 구성 요소](/help/forms/creating-adaptive-form-core-components.md) 양식을 디자인할 수 있습니다. 이러한 구성 요소는 WCM 핵심 구성 요소를 기반으로 하며 BEM 표준을 따르고 쉽게 맞춤화할 수 있습니다. 이 서비스는 양식 내 서명 경험을 지원하지 않으며, 적응형 양식에 대한 요약 및 확인 구성 요소를 포함하지 않습니다

## Forms 포털

* Forms 포털의 검색 및 목록, 초안 및 제출, 링크 구성 요소를 사용하여 로그인한 사용자의 양식을 나열할 수 있습니다. Forms 포털의 익명 사용에 대한 지원은 즉시 사용할 수 없습니다(OOTB). Forms 포털을 사용자 지정하여 로그인하지 않은 사용자의 양식을 표시할 수 있습니다.

* 이 서비스는 초안 및 제출된 적응형 Forms에 대한 메타데이터를 보존하지 않습니다.

## 문서 서비스:

Forms은 문서 생성 및 문서 조작 RESTful API를 as a Cloud Service으로 제공합니다. 필요에 따라 다음 API를 사용하여 주문형 또는 일괄로 문서를 생성하거나 조작할 수 있습니다.

* **문서 서비스: 문서 생성 API(출력 서비스)**: 단일 API 호출 또는 배치에서 여러 DATA XML 파일이 있는 템플릿은 하나만 사용할 수 있습니다. 단일 API 호출에서 여러 데이터 파일에 여러 템플릿을 사용하는 것은 지원되지 않습니다.

* **문서 조작 API(어셈블러 서비스)**:

   * 문서 서비스나 응용 프로그램에 의존하는 작업은 사용할 수 없습니다. 예를 들어 Microsoft Word에서 PDF, Microsoft Excel에서 PDF, HTML에서 PDF, PostScript(PS)에서 PDF, XDP에서 PDF forms으로 변환할 수 없습니다. 이러한 작업은 각각 Microsoft Office, Adobe Acrobat, Adobe Distiller, Forms Document Service를 사용합니다.

   * 커뮤니케이션 문서 조작 API가 있는 문서를 사용하기 전에 PDF 형식이 아닌 문서를 PDF 형식으로 변환합니다. 예를 들어, 문서가 Microsoft Office, HTML, PostScript(PS), XDP 형식인 경우 PDF 문서에 이들 문서를 사용하기 전에 PDF 형식으로 변환하십시오. 다음을 사용할 수 있습니다. [변환 PDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) 이러한 전환에 대한 서비스입니다.

* 디지털 서명, 암호화, Reader 확장, 프린터로 전송, PDF 변환 및 바코드 Forms 서비스에 AEM 6.5 Forms 환경을 사용할 수 있습니다.


## 데이터 통합(양식 데이터 모델)

* 또한 이 서비스는 JDBC 커넥터, Microsoft Dynamics, SalesForce, SOAP 기반 웹 서비스 및 OData를 지원하는 서비스를 지원합니다.

* AEM 사용자 프로필을 연결하여 사용자 정보를 검색하고 업데이트할 수도 있습니다.

* Forms 데이터 모델은 HTTP 및 HTTPS 끝점에서만 데이터를 제출할 수 있도록 지원합니다. 이 서비스는 REST 커넥터에 대한 상호 SSL 및 SOAP 데이터 소스에 대한 x509 인증서 기반 인증을 지원하지 않습니다.

* Forms as a Cloud Service에서는 일반적인 CRUD(만들기, 읽기, 업데이트 및 삭제) 작업을 지원하는 Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive 및 서비스를 데이터 저장소로 사용할 수 있으며, Open API 사양 2.0과 Open API 3.0 사양이 모두 지원됩니다.


## 전자 서명

* 이 서비스는 Adobe Sign과의 OOTB 통합을 제공하며 전자 서명에 대한 DocuSign을 지원합니다.

* 이 서비스는 Adobe Sign 역할도 지원합니다. 비즈니스 사용자를 위한 적응형 Forms 편집기에서 역할을 구성하여 서명 워크플로를 쉽게 구성할 수 있습니다.


## HTML5 양식

* AEM 6.5 Forms 환경을 사용하여 다음을 수행할 수 있습니다.

   * xdp 기반 양식을 HTML5 Forms으로 렌더링합니다. 이 서비스는 HTML5 Forms(모바일 Forms)를 지원하지 않습니다.

   * 오프라인으로 데이터를 캡처하고 다음에 온라인으로 돌아올 때 동기화합니다. [AEM Forms 작업 공간](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) 앱.

## 대화형 통신

* 커뮤니케이션 API를 사용하여 맞춤형 문서를 온디맨드로 제작하거나 Forms에서 as a Cloud Service으로 일괄 처리할 수 있습니다. 대화형 통신 및 에이전트 UI 사용 사례에 AEM 6.5 Forms 환경을 사용할 수 있습니다.

## 다음 보기

* [AEM Forms(온-프레미스 및 AMS 환경)에서 AEM Forms as a Cloud Service으로 마이그레이션](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [AEM Sites 페이지에 적응형 Forms 추가 또는 생성](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [적응형 양식 만들기(핵심 구성 요소)](/help/forms/creating-adaptive-form-core-components.md)

## 추가 정보

* [AEM Forms as a Cloud Service 소개](/help/forms/home.md)
* [로컬 개발 환경 및 초기 개발 프로젝트 설정](/help/forms/setup-local-development-environment.md)
