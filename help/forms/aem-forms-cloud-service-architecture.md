---
title: AEM Forms as a Cloud Service 아키텍처
description: 의 아키텍처 이해 [!DNL AEM Forms] 플랫폼의 확장성, 복원력 및 성능 측면에 대해 as a Cloud Service으로 알아볼 수 있습니다.
exl-id: 9d677bee-50ca-460e-b503-6b7799900735
source-git-commit: b2c8e739c4e1c5289ca263360f4f59b8a2c05f5b
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 6%

---

# [!DNL AEM] Forms as a Cloud Service 아키텍처 {#architecture}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/aem-forms-architecture-deployment.html) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager Forms] as a Cloud Service은 기업이 복잡한 디지털 양식 및 통신을 생성, 관리, 게시 및 업데이트하면서 제출된 데이터를 백엔드 프로세스, 비즈니스 규칙 및 외부 데이터 저장소에 데이터를 저장하는 클라우드 기반 솔루션입니다. 확장됩니다 [!DNL Adobe Experience Manager as a Cloud Service]. 확장, 배포, 환경 및 기타 인프라에 대한 자세한 내용은 [의 아키텍처에 대한 소개 [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html).

AEM Forms은 디지털 등록과 고객 커뮤니케이션이라는 두 가지 주요 사용 사례를 as a Cloud Service으로 지원합니다. 다음 그림은 두 사용 사례의 아키텍처를 나타냅니다.

## Forms 디지털 등록

![Forms-Digital 등록](assets/forms-cloud-service-architecture-forms-digital-enrollment.svg)

## Forms Communications

![Forms 통신](assets/forms-cloud-service-architecture-forms-communications.svg)

## 구성 요소

Forms as a Cloud Service은 여러 구성 요소로 구성됩니다.

### CDN(Content Delivery Network)

모든 AEM Forms as a Cloud Service 프로그램은에 대한 액세스 권한이 있습니다. [기본 CDN 서비스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html). Forms as a Cloud Service 라이선스에 포함되어 있습니다.

### 작성자

작성자는 표준 작성자 실행 모드에서 실행되는 AEM Forms as a Cloud Service 인스턴스입니다. 내부 사용자, 양식 디자이너 및 개발자를 위한 것입니다. 작성 환경에서는 다음 기능을 사용할 수 있습니다.

* 양식 작성 및 관리
* PDF 또는 XDP 양식을 적응형 양식으로 전환하기 위해 Automated forms conversion 서비스에 연결.
* Forms 중심 워크플로우 만들기 및 실행.
* 적응형 양식 에셋 관리
* 통신 자산 관리.
* 브랜드 지향적이고 개인화된 커뮤니케이션을 생성, 조합 및 제공하기 위한 동기 RESTful API(실시간 API) 및 일괄 처리 API.
* PDF 문서를 결합하고, 재배열하고, 유효성을 검사하는 동기 API입니다.

### 게시

게시 인스턴스는 표준 게시 실행 모드에서 as a Cloud Service으로 실행되는 AEM Forms입니다. 게시 인스턴스는 양식 기반 애플리케이션의 최종 사용자(예: 공개 웹 사이트에 액세스하고 양식을 제출하는 사용자)를 위한 것입니다. 이를 통해 다음과 같은 기능을 사용할 수 있습니다.

* 최종 사용자를 위한 양식 렌더링 및 제출
* 최종 기록 시스템에서 추가 처리 및 보관을 위해 원시 제출 양식 데이터 전송.
* 데이터를 저장하기 위해 고객 관리 스토리지에 연결.
* Adobe Sign과 연결하여 적응형 양식 제출 기록에 전자 서명
* API를 동기화하여 브랜드 지향적이고 개인화된 커뮤니케이션을 만들고, 조합하고, 제공합니다.
* API를 동기화하여 PDF 문서를 결합하고, 재배열하고, 유효성을 확인합니다.

AEM 콘텐츠/데이터를 게시 서비스에서 작성자 서비스로 전송하는 데 as a Cloud Service으로 역방향 복제를 사용할 수 없습니다. 그러나 게시에서 실행 중인 적응형 Forms을 구성하여 작성자의 워크플로우에 데이터를 제출할 수 있습니다(워크플로우는 작성자에서만 실행할 수 있음). 이는 승인 사용 사례에 유용합니다.

#### Dispatcher

[디스패처](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) 는 엔터프라이즈급 웹 서버와 함께 사용할 수 있는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다.

### Adobe 서비스

**자동화된 양식 전환 서비스**

[Automated forms conversion 서비스](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html) 는 PDF 및 XFA 양식을 장치 친화적인 반응형 및 HTML5 기반 적응형 양식으로 자동 변환합니다.

**Adobe Sign**

Adobe Sign은 사용자가 브라우저나 모바일 장치를 사용하여 서명 프로세스를 전송, 서명, 추적 및 관리할 수 있는 클라우드 기반의 전자 서명 서비스입니다. Adobe Sign을 적응형 양식과 통합하여 서명 워크플로를 자동화하고, 단일 및 다중 서명 프로세스를 간소화하며, 적응형 양식에 전자적으로 서명할 수 있습니다.

<!-- **PDF Service API**
Adobe’s PDF Services API lets create, combine, export, and extract data from PDFs through powerful and flexible cloud-based APIs. -->

### 고객 관리 스토리지

Forms은 Blob Store, 데이터베이스 또는 스토리지 서비스와 같은 외부 스토리지 시스템에 컨텐츠를 저장하는 옵션을 as a Cloud Service으로 제공합니다. 민감한 개인 데이터(SPD) 요소가 포함된 처리 중인 워크플로 데이터(AEM Workflow 변수 데이터)를 고객 관리 저장소에 저장하여 안전하게 처리할 수도 있습니다. Adobe은 민감한 데이터를 고객이 관리하는 저장소에만 저장하는 것을 권장합니다.

다음을 사용할 수 있습니다. **통합 스토리지 커넥터** Blob 스토리지에 연결하고 **양식 데이터 모델** 데이터베이스 또는 백엔드 서비스(RESTful, SOAP, Azure Blob Storage 등)에 연결

### 문서 서비스

문서 서비스는 다음과 같이 구성됩니다.

* **출력 서비스(통신 - 문서 생성 API)** 비즈니스 서신, 명세서, 청구 처리 편지, 혜택 공지, 월별 청구서 또는 시작 키트와 같이 브랜드 승인을 받고, 개인화되고, 표준화된 문서를 만드는 데 도움이 됩니다.

* **어셈블러 서비스(통신 - 문서 조작 API)** 은 PDF 문서를 결합하고, 재배열하고, 유효성을 검사하는 데 도움이 됩니다.

* **기록 문서(DoR) 서비스** 기록 문서(DoR)를 생성하는 데 도움이 됩니다. 이 서비스는 Forms의 Author 및 Publish 인스턴스를 as a Cloud Service으로 구분하는 자체 Pod에서 실행됩니다. 이것은 더 나은 성능을 제공하고 부하에 따라 독립적으로 포드의 크기를 조정하는 데 도움이 됩니다.

### Cloud Manager

Cloud Manager는 의 필수 구성 요소입니다. [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=ko-KR). 고객의 운영 및 개발자 담당자를 위한 단일 진입점입니다. AEM 프로그램 및 환경을 관리할 수 있는 곳입니다. Cloud Manager는 다음과 같은 AEM as a Cloud Service의 주요 구성 요소를 만들고 구성할 수 있는 셀프서비스 포털로 발전해 왔습니다.

* 프로그램 만들기 및 관리
* 프로그램 내에서 AEM 환경 만들기 및 관리
* 고객 코드 및 구성을 특정 환경에 배포하기 위한 파이프라인 생성 및 관리
* 이러한 구성 요소에 대한 중요 라이프사이클 이벤트 알림(예: 제품 업데이트) Cloud Manager에 대한 자세한 내용은 다음을 참조하십시오. [Adobe Cloud Manager 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) 및 [Cloud Manager 소개](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

### 개발자 콘솔

개발자 콘솔은 실행 중인 각 Forms as a Cloud Service 환경에 대한 다양한 세부 정보를 제공합니다. 이러한 세부 사항은 환경을 디버깅하는 데 유용합니다. 자세한 내용은 [Developer Console을 사용하여 AEM as a Cloud Service 디버깅](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html).

<!--

+++CDN (Content Delivery Network):

Every AEM Forms as a Cloud Service program has access to Fastly CDN service. It is included in the licence of Forms as a Cloud Services.

+++

+++Adaptive Forms
Adaptive Forms enable customers to author web-friendly reflowable web forms and fragments that are used by the customers for their data capture needs. This feature enables customers to manage their complex data capture needs easily, by leveraging multiple integrations with Adobe Sign, Document Services, Form Data Model, Automated Forms Conversion service, and more.

+++

+++Automated Forms Conversion Service (AFCS)
Automated Forms Conversion service helps accelerate digitization and modernization of data capture experience through automated conversion of PDF forms to adaptive forms. The service, powered by Adobe Sensei, automatically converts your PDF forms to device-friendly, responsive, and HTML5-based adaptive forms. While leveraging the existing investments in PDF Forms and XFA, the service also applies appropriate validations, styling, and layout to adaptive form fields during conversion.

+++

+++Form Data Model
The Form Data Model (FDM) feature is the standard way of creating data integrations with external/internal data sources and using them across the different Forms as a Cloud Service features. FDM provides a rich editor for customers to integrate, define, and manage relationships between the different entities and data sources and perform operations on them. Form data is stored in a data store hosted on the customer premises. Organizations can also use blob store hosted by the cloud provider and Adobe Experince Platform to store data.

+++

+++Forms Workflows
Forms-centric workflows is an extension to the default AEM Workflow and provides our customers with additional workflow capabilities like Form Data review, task assignment, and document services invocation.

+++

+++Communications
Forms as a Cloud Service offering consists of multiple services tailored specifically for document processing.

+++

+++Document of Record
A Document of Record is a PDF version of a form. It provides an ability to keep a record of the information  that you provide and submit in an Adaptive Form in PDF fromat. The service provides a default DoR template and tools to develop a custom template.

+++

## Terminologies

<!-- ## Cloud Manager{#cloud-manager}

Cloud Manager is an essential component to [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en). Each new tenant of the [!DNL AEM Forms] as a Cloud Service is first provisioned for Cloud Manager access. Cloud Manager is the single-entry point for the operations and developer persona of our customers. It is the place from where the AEM programs and environments can be managed. Cloud Manager has evolved as a self-service portal where the main components of the AEM as a Cloud Service can be created and configured:

* Creating and managing programs
* Creating and managing the AEM environments within the programs
* Creating and managing the pipelines for deploying the customer code and configuration to a particular environment
* Getting notified of important lifecycle events for these components (for example, product updates)
For more information about Cloud Manager, see [Understand Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) and [Introduction to Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

## Users and Authentication {#users-and-authentication}

AEM as a Cloud Service includes Admin Console support for AEM instances and Adobe Identity Management System (IMS) based authentication. The Admin Console allows administrators to centrally manage all Experience Cloud users. Users and Groups can be assigned to product profiles associated with AEM as a Cloud Service instances, allowing them to log in to that instance. For more information about users, authentication, and, and accessing an instance of AEM as a Cloud Service, see [IMS Support for [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#introduction).

Various personas are involved in a typical [!DNL AEM Forms] project. After you log in to your [!DNL AEM Forms] as a Cloud Service instance, you can [add users in admin console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html) for personas applicable to your organization or project and [assign users to built-in groups](forms-groups-privileges-tasks.md) to provide them required privileges.

To learn various in-built [!DNL AEM Forms] specific user groups and privileges available on [!DNL AEM Forms] as a Cloud Services instance, see [Configure, user, roles and groups](forms-groups-privileges-tasks.md). 

## Developer Experience {#developer-experience}

The new architecture supporting AEM as a Cloud Service brings some key changes to the overall developer experience. One of the major goals for the changes to developer experience is to allow migration to AEM as a Cloud Service as quickly as possible, with little modifications to existing custom code.

## Cloud development {#cloud-development}

Here are the guidelines to run your existing code smoothly on AEM as a Cloud Service environment:

* Store your code and configurations to the Git repository of the associated Cloud Manager program. It makes managing and integrating code with CI/CD a breeze.  
* Make application code and configuration compatible with the baseline [!DNL AEM Forms] images. Using the latest APIs helps to build faster and secure applications.
* Use the Cloud Manager pipeline associated with the Cloud Manager environment to build and deploy applications. It helps you bring the latest features and bug fixed for [!DNL AEM Forms] as a Cloud Service to your environment.
* Try that your custom applications pass all the code quality, security, and performance gates enforced in the pipeline. It helps build secure and better performing applications which leads to better customer experience. You can always use Cloud Manager UI to skip some checks.
This process is commonly referred to as cloud-first development. [!DNL AEM Forms] as a Cloud Service also provides an SDK to support rapid development before the pending code and configuration changes are attempted in the cloud.
Some interfaces that were previously part of the AEM QuickStart are no longer available to the users of the AEM as a Cloud Service environment. For instance, the Web Console where OSGI bundles and their associated configuration are managed. The CRXDE Lite content repository browser becomes only accessible on non-production environment types. A subset of the Web Console functionalities that developers require, especially when it comes to diagnostics and status purposes, is made available via a new developer console.
Also, one of the most common requirements for developers is quick access to the log files of the various environments. With [!DNL AEM Cloud Service], the log files of the different nodes in the Author, Publish are made available via the Cloud Manager, either in the form of files that can be downloaded or via APIs for tailing the logs. Due to the clear separation of code and content, developers can use a particular process for updating content as part of a deployment. The typical use cases for mutable content are:
* Standard “default” content that is part of the customer project (for example, folders, templates, workflows...)
* Search index definitions
* ACLs and permissions
* Service users and user groups
Set up your development environment, [Configure your CI/CD Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html), and learn to [deploy your code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) on the environment. -->

### 적응형 양식 작성 {#local-development}

다음을 설정하고 구성할 때 [!DNL AEM Forms] as a Cloud Service 환경에서는 개발, 스테이징 및 프로덕션 환경을 설정합니다. 또한 신속한 반복 및 개발을 위해 로컬 개발 환경을 설정하고 구성합니다. AEM SDK를 다운로드하고 설정할 수 있습니다. [!DNL AEM Forms] 로컬 설정을 위한 추가 기능 아카이브 [!DNL Forms] as a Cloud Service 개발 환경.  자세한 지침은 [로컬 개발 환경 설정](setup-local-development-environment.md).

## 디버깅 {#debugging}

AEM as a Cloud Service은 셀프서비스, 확장 가능한 클라우드 인프라에서 실행됩니다. AEM 개발자는 빌드 및 배포에서 AEM 애플리케이션 실행에 대한 세부 정보를 얻기 위해 AEMas a Cloud Service 의 다양한 측면을 이해하고 디버깅해야 합니다. 자세한 내용은 [디버깅 AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html).
