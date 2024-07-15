---
title: AEM Forms의 로컬 개발 환경을 설정하려면 어떻게 해야 합니까?
description: Adobe Experience Manager Formsas a Cloud Service 를 위한 지역 개발 환경 설정
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 12877a77-094f-492a-af58-cffafecf79ae
source-git-commit: a070e945f23641cfdfd71511366e5b2c16ec22e8
workflow-type: tm+mt
source-wordcount: '2762'
ht-degree: 2%

---

# AEM Forms을 위한 로컬 개발 환경 설정 {#overview}

[!DNL  Adobe Experience Manager Forms]을(를) [!DNL  Cloud Service] 환경으로 설정하고 구성할 때 클라우드에서 개발, 스테이징 및 프로덕션 환경을 설정합니다. 또한 로컬 개발 환경을 설정하고 구성할 수도 있습니다.

클라우드 개발 환경에 로그인하지 않고 로컬 개발 환경을 사용하여 다음 작업을 수행할 수 있습니다.

* [양식 만들기](creating-adaptive-form.md) 및 관련 에셋(테마, 템플릿, 사용자 지정 제출 액션 등)
* [PDF 양식을 적응형 양식으로 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html?lang=ko-KR)
* 주문형 또는 배치 모드에서 [고객 커뮤니케이션](aem-forms-cloud-service-communications-introduction.md)을 생성하도록 응용 프로그램을 빌드합니다.

로컬 개발 인스턴스 또는 응용 프로그램에서 [고객 커뮤니케이션]을(를) 생성할 준비가 되면 추가 테스트 또는 프로덕션 환경으로 이동하기 위해 로컬 개발 환경에서 Cloud Service 환경으로 적응형 양식 또는 고객 커뮤니케이션 응용 프로그램을 내보낼 수 있습니다.

로컬 개발 환경에서 사용자 지정 구성 요소 및 미리 채우기 서비스와 같은 사용자 지정 코드를 개발 및 테스트할 수도 있습니다. 사용자 지정 코드가 테스트되고 준비되면 Cloud Service 개발 환경의 Git 저장소를 사용하여 사용자 지정 코드를 배포할 수 있습니다.

새 로컬 개발 환경을 설정하고 이를 사용하여 활동에 대해 개발하려면 나열된 순서로 다음 작업을 수행하십시오.

* [개발 도구 설정](#setup-development-tools-for-AEM-projects)

* [로컬 작성자 및 Publish 인스턴스 설정](#set-up-local-experience-manager-environment-for-development)

* [로컬 개발 인스턴스에 Forms 아카이브 추가 및 사용자 구성](#add-forms-archive-configure-users)

* [마이크로서비스를 위한 로컬 개발 환경 설정](#docker-microservices)

* [개발 프로젝트 설정](#forms-cloud-service-local-development-environment)

* [로컬 Dispatcher 도구 설정](#setup-local-dispatcher-tools)

<!--
You can use the local development environment to create and test Adaptive Forms without connecting to the Cloud Service. [!DNL AEM Forms] provides an SDK to help test all the cloud-ready functionalities on the local development environment. When your forms and related assets are ready and tested on the local development environment, you can import these forms and related assets to an [!DNL AEM Forms] as a Cloud Service instance for publishing. 

You can also develop and test custom code like custom components and prefill service on the local development environment. When the custom code is tested and ready, you can use the Git repository of your [!DNL AEM Forms] as a Cloud Service development environment to deploy the custom code. 

>[!NOTE]
>
> Pre-pilot release does not support using an [!DNL AEM Forms] as a Cloud Service development instance to create forms. You can create forms, related assets, and custom code only on a local development environment.-->

<!--
You configure two types of development environments:

* **[!DNL AEM Forms] as a Cloud Service development environment:** Use the [[!DNL AEM Forms] as a Cloud Service](setup-forms-cloud-service.md) environment to store, manage, and publish Adaptive Forms and related assets. Do not use an [!DNL AEM Forms] as a Cloud Service environment to create Adaptive Forms and related assets <!--, form-centric workflows, a form data model, or to generate a Document of Record. -->

<!--
* **Local development environment:** You can use the local development environment to create and test Adaptive Forms without connecting to the service. Adobe provides a SDK for the local development to help test all the cloud-ready functionalities. 
Use a local development environment:
    
    * To create forms and related assets (themes, templates, custom Submit Actions, and more) and convert PDF forms to Adaptive Forms. After an Adaptive Form or related assets are ready on the local development instance, you can export the Adaptive Form and related assets from the local development environment to an [!DNL AEM Forms] as a Cloud Service development environment for publishing.  
    
    * To update configuration settings and develop and test custom code like custom components and prefill service. When the custom code is tested and ready, you can use the Git repository of your [!DNL AEM Forms] as a Cloud Service development environment to deploy the custom code.  

You can use the local development environment to create and test Adaptive Forms without connecting to the service. Adobe provides a SDK for the local development to help test all the cloud-ready functionalities. When your forms and related assets are ready and tested on the local development environment, you can import these forms and related assets to an [!DNL AEM Forms] as a Cloud Service instance for publishing. 

You can use the [development tools](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/dev-tools.html) to write custom code, customize or create new Adaptive Forms components, create a custom prefill service, or modify default configurations of an [!DNL AEM Forms] as a Cloud Service instance. 

-->

## 사전 요구 사항

로컬 개발 환경을 설정하려면 다음 소프트웨어가 필요합니다. 로컬 개발 환경 설정을 시작하기 전에 다음을 다운로드합니다.

| 소프트웨어 | 설명 | 다운로드 링크 |
|---|---|---|
| ADOBE EXPERIENCE MANAGER AS A CLOUD SERVICE SDK | SDK에 [!DNL Adobe Experience Manager] 빠른 시작 및 Dispatcher 도구가 포함되어 있습니다. | [소프트웨어 배포](#software-distribution)에서 최신 SDK 다운로드 |  |
| Adobe Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능) | 적응형 Forms 및 기타 Adobe Experience Manager Forms 기능을 만들고, 스타일을 지정하고, 최적화하는 도구 | [소프트웨어 배포](#software-distribution)에서 다운로드 |
| (선택 사항) Adobe Experience Manager Forms 참조 컨텐츠 | 적응형 Forms 및 기타 Adobe Experience Manager Forms 기능을 만들고, 스타일을 지정하고, 최적화하는 도구 | [소프트웨어 배포](#software-distribution)에서 다운로드 |
| (선택 사항) Adobe Experience Manager Forms Designer | 적응형 Forms 및 기타 Adobe Experience Manager Forms 기능을 만들고, 스타일을 지정하고, 최적화하는 도구 | [소프트웨어 배포](#software-distribution)에서 다운로드 |

### 소프트웨어 배포에서 최신 버전의 소프트웨어 다운로드 {#software-distribution}

[소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 최신 버전의 Adobe Experience Manager as a Cloud Service SDK, Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능), 양식 참조 자산 또는 Forms Designer을 다운로드하려면 다음을 수행하십시오.

1. Adobe ID으로 <https://experience.adobe.com/#/downloads>에 로그인

   >[!NOTE]
   >
   > AEM as a Cloud Service SDK를 다운로드하려면 AEM as a Cloud Service에 대한 Adobe 조직을 프로비저닝해야 합니다.

1. **[!UICONTROL AEM as a Cloud Service]** 탭으로 이동합니다.
1. 게시한 날짜별로 내림차순으로 정렬합니다.
1. 최신 Adobe Experience Manager as a Cloud Service SDK, Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능), 양식 참조 자산 또는 Forms Designer을 클릭합니다.

   >[!NOTE]
   >
   > Adobe Experience Manager as a Cloud Service SDK와의 원활한 호환성을 위해 최신 버전의 Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능), 양식 참조 에셋 또는 Forms Designer을 다운로드하는 것이 좋습니다.

1. EULA를 검토하고 수락합니다. **[!UICONTROL 다운로드]** 버튼을 선택합니다.

## AEM 프로젝트용 개발 도구 설정 {#setup-development-tools-for-AEM-projects}

Adobe Experience Manager Forms 프로젝트는 사용자 지정 코드 베이스입니다. 여기에는 코드 구성 및 Cloud Manageras a Cloud Service 를 통해 [!DNL Adobe Experience Manager]에 배포된 콘텐츠가 포함되어 있습니다. [AEM Project Maven Archetype](https://github.com/adobe/aem-project-archetype)은(는) 프로젝트의 기준 구조를 제공합니다.

개발을 위해 [!DNL Adobe Experience Manager] 프로젝트에 사용할 다음 개발 도구를 설정하십시오.

* [Java™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#local-development-environment-set-up)
* [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-git)
* [npm(Node.js)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#node-js)
* [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-maven)

이전에 언급된 개발 도구를 설정하는 자세한 지침은 [개발 도구 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html)을 참조하십시오.

## 개발을 위한 로컬 Experience Manager 환경 설정

Cloud Service SDK는 QuickStart 파일을 제공합니다. 로컬 버전의 Experience Manager을 실행합니다. 작성자 또는 Publish 인스턴스를 로컬에서 실행할 수 있습니다.

as a Cloud Service 빠른 시작은 로컬 개발 환경을 제공하지만 [!DNL Adobe Experience Manager]에서 모든 기능을 사용할 수 있는 것은 아닙니다. as a Cloud Service 따라서 기능을 스테이징 또는 프로덕션으로 이동하기 전에 항상 [!DNL Adobe Experience Manager] 개발 환경에서 기능과 코드를 테스트하십시오.

로컬 Experience Manager 환경을 설치하고 구성하려면 다음 단계를 수행하십시오.

* [!DNL Adobe Experience Manager] as a Cloud Service SDK를 [다운로드 및 추출](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
* [작성자 인스턴스 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#set-up-local-aem-author-service)
* [Publish 인스턴스 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#set-up-local-aem-publish-service)

## 로컬 작성자 및 Publish 인스턴스에 Forms 아카이브 추가 및 Forms 관련 사용자 구성 {#add-forms-archive-configure-users}

나열된 순서로 다음 단계를 수행하여 Forms 아카이브를 Experience Manager 인스턴스에 추가하고 양식별 사용자를 구성합니다.

### 최신 Forms 추가 기능 아카이브 설치 {#add-forms-archive}

Adobe Experience Manager Forms as a Cloud Service 스타일 아카이브는 로컬 개발 환경에서 적응형 Forms을 만들고 최적화하는 도구를 제공합니다. 패키지를 설치하여 적응형 양식을 만들고 [!DNL AEM Forms]의 다양한 다른 기능을 사용하십시오. 패키지를 설치하려면:

1. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 운영 체제에 대한 최신 [!DNL AEM Forms] 보관 파일을 다운로드하고 추출하십시오.

1. crx-quickstart/install 디렉토리로 이동합니다. 폴더가 없으면 만듭니다.

1. AEM 인스턴스를 중지하고 [!DNL AEM Forms] 추가 기능 보관 파일 `aem-forms-addon-<version>.far`을(를) 설치 폴더에 배치합니다.
1. 활성 명령 창으로 이동하고 `Ctrl + C` 명령을 눌러 SDK를 다시 시작합니다.

   >[!NOTE]
   >
   > SDK를 다시 시작하려면 &#39;Ctrl + C&#39; 명령을 사용하는 것이 좋습니다. Java 프로세스 중지와 같은 대체 방법을 사용하여 AEM SDK를 다시 시작하면 AEM 개발 환경이 일치하지 않을 수 있습니다.

<!--**Q**: I've set up a Aem as a Cloud Service environment and added the Forms Add-On for a project. After the .far file addition, the bundles are not in the active state and are in installed state only due to the missing dependencies. How to make the bundles in the active state?
**A**: To resolve the issue:
1. Start the AEM and wait for it to start completely (all bundles up)
1. Stop aem (ctrl + c). Place the forms far in the install folder.
1. Restart AEM.-->


### 사용자 및 권한 구성 {#configure-users-and-permissions}

양식 개발자 및 양식 전문가와 같은 사용자를 만들고 [이러한 사용자를 사전 정의된 양식 그룹에 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=en#accessing)하여 필요한 권한을 제공하십시오. 아래 표에는 모든 유형의 사용자와 각 유형의 양식 사용자에 대해 사전 정의된 그룹이 나열되어 있습니다.

| 사용자 유형 | AEM 그룹 |
|---|---|
| 양식 전문가 / | [!DNL forms-users](AEM Forms 사용자), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors] 및 [!DNL fdm-authors] |
| 양식 개발자 | [!DNL forms-users](AEM Forms 사용자), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors] 및 [!DNL fdm-authors] |
| Customer Experience Lead 또는 UX Designer | [!DNL forms-users], [!DNL template-authors] |
| AEM 관리자 | [!DNL aem-administrators], [!DNL fd-administrators] |
| 최종 사용자 | 적응형 양식을 보고 제출하려면 사용자가 로그인해야 하는 경우 해당 사용자를 [!DNL forms-users] 그룹에 추가하십시오. </br> 응용 Forms에 액세스하는 데 사용자 인증이 필요하지 않으면 해당 사용자에게 그룹을 할당하지 마십시오. |

<!--  

## Set up a local AEM instance for development

Perform the following steps in the listed order to set up and configure your local development environment:

1. **Set up an AEM author instance:** You require an author instance to create Adaptive Forms. Download and extract the latest AEM SDK archive. Run the quick start file in author run mode to set up an author instance. For detailed instructions, see [default local instance](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html).  

1. **Install the latest [!DNL AEM Forms] add-on feature archive:** [!DNL AEM Forms] add-on feature archive provides tools to create, style, and optimize Adaptive Forms on the local development environment. Install the package to create an Adaptive Form and use various other features of [!DNL AEM Forms]. To install the package:

    1. Download and extract the latest [!DNL AEM Forms] archive for your operating system from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

    1. Navigate to the crx-quickstart/install directory. If the folder does not exist, create it.

    1. Stop your Cloud ready AEM instance, place the [!DNL AEM Forms] add-on feature archive, `aem-forms-addon-<version>.far`,  in the install folder, and restart the instance.

1. **Configure users and permissions:** Create users like Form Developer and Form Practitioner a nd add these users to pre-defined forms group to provide them required permissions. The table below lists all types of users and pre-defined groups for each type of forms users:
  
    | User Type | AEM Group |
    |---|---|
    | Form Practitioner  | forms-users (AEM Forms Users), template-authors  |
    | Form Developer | forms-users (AEM Forms Users), template-authors |
    | End-User| everyone* |

    `*` When a user should log in to access or submit Adaptive Forms, add such users to the everyone group.  -->

<!--    
### Set up an AEM project for the development tasks related to local AEM 6.5.5 Forms instance

Use this project to update configurations, create overlays, develop custom Adaptive Form components, and custom code using the local development environment. To set up the project:

1. **Install and configure Maven and set up an AEM project based on Apache Maven:** Apache Maven is an open-source tool for managing software projects. It helps automate builds and provides quality project information. It is the recommended build management tool for AEM projects. For detailed instructions to set up an AEM project based on Apache Maven, see [How to Build AEM Projects using Apache Maven](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/ht-projects-maven.html).

1. Configure the project to use [uber-jar](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=en#install-aem-forms-jee-installer) version 6.5.5 or later and [[!DNL AEM Forms] Client SDK](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/) version 6.0.160 or later.  

1. **Set Up an Integrated Development Environment:**  Set up an IDE of your choice for development, see [Set Up an Integrated Development Environment](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) for detailed instructions.
 -->

## 기록 문서(DoR)에 대한 로컬 개발 환경 설정{#docker-microservices}

AEM Forms as a Cloud Service은 기록 문서를 보다 쉽게 개발하고 다른 마이크로서비스를 사용할 수 있는 도커 기반 SDK 환경을 제공합니다. 플랫폼별 바이너리 및 적응물을 수동으로 구성할 필요가 없습니다. 환경을 설정하려면 다음을 수행하십시오.

1. 도커 설치 및 구성:

   * (Microsoft® Windows의 경우) [Docker Desktop](https://www.docker.com/products/docker-desktop)을 설치합니다. 컴퓨터에서 `Docker Engine` 및 `docker-compose`을(를) 구성합니다.

   * (Apple macOS) [Mac용 Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)을 설치합니다. 여기에는 Docker 엔진, Docker CLI 클라이언트, Docker 작성, Docker 컨텐츠 신뢰, Kubernetes 및 Credential Helper가 포함됩니다.

   * (Linux®의 경우) 컴퓨터에 [Docker 엔진](https://docs.docker.com/engine/install/#server) 및 [Docker 구성](https://docs.docker.com/compose/install/)을 설치합니다.

   >[!NOTE]
   >
   > * Apple macOS의 경우 로컬 AEM 작성자 인스턴스가 포함된 허용 목록에 추가하다 폴더입니다.
   >
   > * Windows용 Docker Desktop은 Hyper-V라는 두 개의 백엔드를 지원합니다.
   > (기존) 및 WSL2(최신). 파일 공유가 자동으로 수행됩니다.
   > WSL2(최신)를 사용할 때 Docker에서 관리합니다. 다음을 수행해야 합니다.
   > hyper-V(레거시)를 사용하는 동안 파일 공유를 명시적으로 구성하십시오.

1. 작성자 및 게시 인스턴스와 동시에 폴더를 만듭니다(예: aem-sdk). 예: C:\aem-sdk.

1. `aem-forms-addon-<version>.zip\aem-forms-addon-native-<version>.zip` 파일을 추출합니다.

   ![기본 AEM 양식에 추출된 AEM 양식 추가](assets/microservice-docker.png)

1. 환경 변수 AEM_HOME을 생성하고 로컬 AEM Author 설치를 가리킵니다. 예: C:\aem\author\.

1. 편집할 sdk.bat 또는 sdk.sh를 엽니다. 로컬 AEM Author 설치를 가리키도록 AEM_HOME을 설정합니다. 예: C:\aem\author\.

1. 명령 프롬프트를 열고 `aem-forms-addon-native-<version>` 폴더로 이동합니다.

1. 로컬 AEM 작성자 인스턴스가 실행 중인지 확인합니다. 다음 명령을 실행하여 SDK를 시작합니다.

   * Microsoft® Windows에서

     ```shell
     sdk.bat start
     ```


   * Linux® 또는 Apple macOS

     ```Shell
     % export AEM_HOME=[local AEM Author installation]
     % ./sdk.sh start
     ```


   >[!NOTE]
   >
   > sdk.sh 파일에서 환경 변수를 정의한 경우 명령줄에서 이 변수를 지정하는 것은 선택 사항입니다. 셸 스크립트를 업데이트하지 않고 명령을 실행하기 위해 명령줄에서 환경 변수를 정의하는 옵션이 제공됩니다.

   ![start-sdk-command](assets/start-sdk.png)

이제 로컬 개발 환경을 사용하여 기록 문서를 렌더링할 수 있습니다. 테스트하려면 XDP 파일을 환경에 업로드하고 렌더링합니다. 예를 들어 <http://localhost:4502/libs/xfaforms/profiles/default.print.pdf?template=crx:///content/dam/formsanddocuments/cheque-request.xdp>은(는) XDP 파일을 PDF 문서로 변환합니다.

## Experience Manager Archetype을 기반으로 Forms에 대한 개발 프로젝트 설정 {#forms-cloud-service-local-development-environment}

이 프로젝트를 사용하여 로컬 [!DNL Experience Manager Forms] SDK에서 적응형 Forms을 만들고, 구성 업데이트를 배포하고, 오버레이하고, 사용자 지정 적응형 양식 구성 요소를 만들고, 테스트하고, 사용자 지정 코드를 만듭니다. as a Cloud Service 로컬에서 테스트한 후 프로젝트를 [!DNL Experience Manager Forms] 프로덕션 및 비프로덕션 환경에 배포할 수 있습니다. 프로젝트를 배포하면 다음 AEM Forms 에셋도 배포됩니다.

| 테마 | 템플릿 | 양식 데이터 모델(FDM) |
---------|----------|---------
| 캔버스 3.0 | 기본 | Microsoft® Dynamics 365 |
| 고요해 | 비어 있음 | Salesforce |
| 우르바네 |   |  |
| 울트라마린 |  |  |
| 베릴 |  |  |

>[!NOTE]
>
> AEM Archetype 버전 30 이상 기반 프로젝트를 설정하여 AEM Formsas a Cloud Service 과 함께 Microsoft® Dynamics 365 및 Salesforce FDM(양식 데이터 모델)을 가져오고 사용합니다.
> AEM Archetype 버전 32 이상을 설정하여 AEM Formsas a Cloud Service 에서 Tranquil, Urbane 및 Ultramarine 테마를 사용하고 사용할 수 있습니다.

프로젝트를 설정하려면 다음을 수행하십시오.

1. **로컬 개발 인스턴스에서 Cloud Manager Git 저장소를 복제합니다.** Cloud Manager Git 저장소에 기본 AEM 프로젝트가 포함되어 있습니다. [AEM Archetype](https://github.com/adobe/aem-project-archetype/)을(를) 기반으로 합니다. Cloud Manager UI의 셀프서비스 Git 계정 관리를 사용하여 Cloud Manager Git 저장소를 복제하여 프로젝트를 로컬 개발 환경에서 가져옵니다. 저장소에 액세스하는 방법에 대한 자세한 내용은 [저장소에 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html)를 참조하십시오.

<!-- 1. 
After the repository is cloned, [integrate your Git repo with Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html)

**Make cloned AEM project compatible with [!DNL AEM Forms] as a Cloud Service:** Remove uber-jar and other non-cloud dependencies from the pom.xml files of the project. You can refer the pom.xml files of the [sample AEM project](assets/FaaCSample.zip) for the list of required dependencies and update your AEM project accordingly. You can also refer [AEM Project Structure](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) to learn changes required to make an AEM project compatible with AEM as a Cloud Service.  -->

1. **최신 [AEM Archetype](https://github.com/adobe/aem-project-archetype) 이상을 기반으로 [!DNL Experience Manager Forms]을(를) [Cloud Service] 프로젝트로 만들기:** [!DNL Experience Manager Forms]을(를) [Cloud Service] 프로젝트로 만들기 as a Cloud Service Archetype을 통해 개발자는 [!DNL AEM Forms]에 대한 개발을 쉽게 시작할 수 있습니다. 또한 빠르게 시작하는 데 도움이 되는 몇 가지 샘플 테마 및 템플릿이 포함되어 있습니다.

   as a Cloud Service 명령 프롬프트를 열고 아래 명령을 실행하여 [!DNL Experience Manager Forms] 프로젝트를 만듭니다.

   ```shell
   mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="41" -D appTitle=mysite -D appId=mysite -D groupId=com.mysite -D includeFormsenrollment="y" -D aemVersion="cloud"
   ```

   환경을 반영하도록 위의 명령에서 `appTitle`, `appId` 및 `groupId`을(를) 변경하십시오. 또한 라이선스 및 요구 사항에 따라 includeFormsenrollment, includeFormscommunications 및 includeFormsheadless의 값을 `y` 또는 `n`(으)로 설정합니다. includeFormsheadless는 핵심 구성 요소를 기반으로 하는 적응형 Forms을 만드는 데 필수입니다.

   * 응용 Forms을 만드는 데 필요한 Forms 관련 구성, 테마, 템플릿, 핵심 구성 요소 및 종속성을 포함하려면 `includeFormsenrollment=y` 옵션을 사용하십시오. Forms 포털을 사용하는 경우 `includeExamples=y` 옵션을 설정합니다. 또한 Forms 포털 핵심 구성 요소를 프로젝트에 추가합니다.

   * 고객 커뮤니케이션 기능을 포함하는 데 필요한 Forms 핵심 구성 요소 및 종속성을 포함하려면 `includeFormscommunications=y` 옵션을 사용하십시오.

     >[!WARNING]
     >
     >* 버전 45의 Archetype 프로젝트를 만들 때 [AEM Archetype 프로젝트 폴더]/pom.xml은 처음에 양식 핵심 구성 요소 버전을 2.0.64로 설정합니다. Archetype 프로젝트를 빌드하거나 배포하기 전에 Forms 핵심 구성 요소 버전을 2.0.62로 업데이트합니다.

1. 로컬 개발 환경에 프로젝트를 배포합니다. 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

   `mvn -PautoInstallPackage clean install`

   전체 명령 목록은 [빌드 및 설치](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing)를 참조하십시오.

1. as a Cloud Service [코드를  [!DNL AEM Forms] 환경에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases).

## 로컬 Dispatcher 도구 설정 {#setup-local-dispatcher-tools}

Dispatcher은 CDN과 AEM Publish 계층 간에 보안 및 성능 계층을 제공하는 Apache HTTP 웹 서버 모듈입니다. Dispatcher은 전체 Experience Manager 아키텍처의 필수적인 부분이며 로컬 개발 환경의 일부여야 합니다.

다음 단계를 수행하여 로컬 Dispatcher을 구성한 다음 Forms 관련 규칙을 추가합니다.

### 로컬 Dispatcher 설정 {#setup-local-dispatcher}

[!DNL Experience Manager] Dispatcher SDK에는 로컬에서 as a Cloud Service 구성, 유효성 검사 및 시뮬레이션을 용이하게 하는 권장 Dispatcher 도구 버전이 포함되어 있습니다. Dispatcher 도구는 Docker 기반이며 Apache HTTP 웹 서버 및 Dispatcher 구성 파일을 호환되는 형식으로 변환하고 Docker 컨테이너에서 실행되는 Dispatcher에 배포하는 명령줄 도구를 제공합니다.

Dispatcher에서 캐싱을 사용하면 [!DNL AEM Forms]이(가) 클라이언트에서 적응형 Forms을 미리 채울 수 있습니다. 미리 채워진 양식의 렌더링 속도를 향상시킵니다.

Dispatcher 설정에 대한 자세한 지침은 [로컬 Dispatcher 도구 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#local-development-environment-set-up)을 참조하세요.

### Dispatcher에 Forms 관련 규칙 추가 {#forms-specific-rules-to-dispatcher}

Experience Manager Formsas a Cloud Service 용 Dispatcher 캐시를 구성하려면 다음 단계를 수행하십시오.

1. AEM 프로젝트를 열고 `\src\conf.dispatcher.d\available_farms`(으)로 이동
1. `default.farm` 파일의 복사본을 만듭니다. 예: `forms.farm`
1. 편집하기 위해 만든 `forms.farm` 파일을 열고 다음 코드를 바꿉니다.

   ```json
   #/ignoreUrlParams {
   #/0001 { /glob "*" /type "deny" }
   #/0002 { /glob "q" /type "allow" }
   #}
   ```

   포함

   ```json
   /ignoreUrlParams {
   /0001 { /glob "*" /type "deny" }
   /0002 { /glob "dataRef" /type "allow" }
   }
   ```

1. 파일을 저장하고 닫습니다.
1. `conf.d/enabled_farms`(으)로 이동하여 `forms.farm` 파일에 대한 심볼 링크를 만듭니다.
1. as a Cloud Service 프로젝트를 컴파일하여 [!DNL AEM Forms] 환경에 배포합니다.

### 캐싱에 대한 고려 사항 {#considerations-about-caching}

* Dispatcher 캐싱을 사용하면 [!DNL AEM Forms]이(가) 클라이언트에서 적응형 Forms을 미리 채울 수 있습니다. 미리 채워진 양식의 렌더링 속도를 향상시킵니다.
* 보안 콘텐츠 기능 캐싱은 기본적으로 비활성화되어 있습니다. 이 기능을 사용하려면 [보안 콘텐츠 캐싱](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=en) 문서에 제공된 지침을 수행할 수 있습니다
* Dispatcher이 일부 적응형 Forms 및 관련 적응형 Forms을 무효화하지 못할 수 있습니다. 이러한 문제를 해결하려면 문제 해결 섹션에서 [[!DNL AEM Forms] 캐싱](troubleshooting-caching-performance.md)을 참조하세요.
* 현지화된 적응형 Forms 캐싱:
   * URL 형식 `http://host:port/content/forms/af/<afName>.<locale>.html`을(를) 사용하여 `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` 대신 지역화된 버전의 적응형 양식을 요청하세요.
   * 브라우저 로케일 옵션은 기본적으로 비활성화되어 있습니다. 브라우저 로케일 설정을 변경하려면
* URL 형식 `http://host:port/content/forms/af/<adaptivefName>.html`을(를) 사용하고 구성 관리자에서 브라우저 로케일 사용을 사용하지 않도록 설정하면 현지화되지 않은 버전의 적응형 양식이 제공됩니다. 현지화되지 않은 언어는 적응형 양식을 개발하는 동안 사용되는 언어입니다. 브라우저에 대해 구성된 로케일(브라우저 로케일)은 고려되지 않으며 현지화되지 않은 버전의 적응형 양식이 제공됩니다.
* URL 형식 `http://host:port/content/forms/af/<adaptivefName>.html`을(를) 사용하고 구성 관리자에서 브라우저 로케일 사용을 활성화하면 지역화된 버전의 적응형 양식이 제공됩니다(사용 가능한 경우). 현지화된 적응형 양식의 언어는 브라우저에 대해 구성된 로케일(브라우저 로케일)을 기반으로 합니다. [적응형 양식의 첫 번째 인스턴스만 캐싱]할 수 있습니다. 인스턴스에서 문제가 발생하지 않도록 하려면 문제 해결 섹션에서 [적응형 양식의 첫 번째 인스턴스만 캐시됨](troubleshooting-caching-performance.md)을 참조하십시오.

로컬 개발 환경이 준비되었습니다.

## AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 양식 핵심 구성 요소 활성화

AEM Formsas a Cloud Service 에서 적응형 Forms 구성 요소를 활성화하면 AEM Forms Cloud Service 인스턴스를 사용하여 적응형 Forms 및 Headless Forms 기반의 핵심 구성 요소를 만들고, 게시하고, 여러 채널에 전달할 수 있습니다. Headless Adaptive Forms를 사용하려면 적응형 양식 핵심 구성 요소 활성화 환경이 필요합니다.

지침은 [AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 Forms 핵심 구성 요소 사용](/help/forms/enable-adaptive-forms-core-components.md)을 참조하십시오.


## 로컬 개발 환경 업그레이드 {#upgrade-your-local-development-environment}

SDK를 새 버전으로 업그레이드하려면 전체 로컬 개발 환경을 교체해야 하므로 로컬 저장소의 모든 코드, 구성 및 콘텐츠가 손실됩니다. 폐기해서는 안 되는 코드, 구성 또는 콘텐츠가 Git에 안전하게 커밋되거나 로컬 Experience Manager 인스턴스에서 CRX-Packages로 내보내지는지 확인합니다.

### SDK를 업그레이드할 때 콘텐츠 손실을 방지하는 방법 {#avoid-content-loss-when-upgrading--SDK}

SDK를 업그레이드하면 새 저장소([AEM 프로젝트 설정](#forms-cloud-service-local-development-environment))를 포함하여 완전히 새로운 작성자 및 Publish 인스턴스가 생성됩니다. 즉, 이전 SDK의 저장소에 대한 모든 변경 사항이 손실됩니다. SDK 업그레이드 사이에서 콘텐츠를 유지하는 데 도움이 되는 실행 가능한 전략에 대해서는 [AEM SDK를 업그레이드할 때 콘텐츠 손실을 방지하는 방법](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#optional-local-aem-runtime-set-up-tasks)을 참조하십시오

<!--When you update any  Forms-specifc configuration, create overlays, develop custom Adaptive Form components, or develop and test any custom code in AEM project for the development tasks related to local development instance, use the AEM project cloned from the Cloud Manager Git repository to [deploy the custom code and other changes to your [!DNL AEM Forms] as a Cloud Service's production or non-production environment](https://video.tv.adobe.com/v/30191?quality=9).

## Upgrade your local development environment {#update-local-setup}

Update the local AEM setup (AEM SDK) to latest version at least monthly on, or shortly after, the last Thursday of each month, which is the release cadence for AEM as a Cloud Service "feature releases". You can download local AEM SDK from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

Updating the AEM SDK to a new version requires replacing the entire local development environment, resulting in a loss of all code, configuration and content in the local AEM repositories. Ensure that any code, config or content that should not be destroyed is safely committed to Git, or exported from the local AEM instance as AEM Packages.

### How to avoid content loss when upgrading the AEM SDK {#avoid-content-loss-when-upgrading--AEM-SDK}

Upgrading the AEM SDK is effectively creating a brand new AEM runtime ([Set up a local AEM instance](setup-forms-cloud-service.md)), including a new repository ([Set up AEM project](#forms-cloud-service-local-development-environment)), meaning any changes made to a prior AEM SDK's repository are lost. The following are viable strategies for aiding in persisting content between AEM SDK upgrades, and can be used discretely or in concert:

1. Create a content package dedicated to containing the sample content to aid in development and maintain it in Git. Any content that should be persisted through AEM SDK upgrades would be persisted into this package and re-deployed after upgrading the AEM SDK.
1. Use [oak-upgrade](https://jackrabbit.apache.org/oak/docs/migration.html) with the `includepaths` directive, to copy content from the prior AEM SDK repository to the new AEM SDK repository.
1. Back up any content using AEM Package Manager and content packages on the prior AEM SDK and re-install them on the new AEM SDK.

Remember, using the above approaches to maintain code between AEM SDK upgrades, indicates a development anti-pattern. Non-disposable code should originate in your Development IDE and flow into AEM SDK via deployments.

For information about troubleshooting, stopping local AEM environment, run modes, and deployment, see [Set up local AEM Runtime](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#local-development-environment-set-up).-->

### Forms 관련 콘텐츠를 새 SDK 환경으로 백업 및 가져오기 {#backup-and-import-Forms-specific-content-to-new-SDK-environment}

기존 SDK에서 새 SDK 환경으로 에셋을 백업하고 이동하려면 다음을 수행하십시오.

* 기존 컨텐츠의 백업을 만듭니다.

* 새 SDK 환경을 설정합니다.

* 새 SDK 환경으로 백업을 가져옵니다.

### 기존 컨텐츠의 백업 만들기 {#create-backup-of-your-existing-content}

적응형 Forms, 템플릿, 양식 데이터 모델(FDM), 테마, 구성 및 사용자 지정 코드를 백업합니다. 다음 작업을 수행하여 백업을 작성할 수 있습니다.

1. [다운로드](import-export-forms-templates.md#manage-forms-and-related-assets) 적응형 Forms, 테마 및 PDF forms.
1. 적응형 양식 템플릿을 내보냅니다.

1. 양식 데이터 모델 다운로드

1. 편집 가능한 템플릿, 클라우드 구성 및 워크플로우 모델을 내보냅니다. 기존 SDK에서 이전에 언급된 모든 항목을 내보내려면 다음 필터를 사용하여 [CRX-패키지](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html)를 만드십시오.

   * /conf/ReferenceEditableTemplates
   * /conf/global/settings/cloudconfigs
   * /conf/global/settings/wcm
   * /var/workflow/models
   * /conf/global/settings/workflow
1. 로컬 개발 환경에서 이메일 구성 내보내기, 제출 및 작업 코드 미리 채우기. 이러한 설정 및 구성을 내보내려면 로컬 개발 환경에서 다음 폴더 및 파일의 복사본을 만듭니다.

   * `[Archetype Project in Cloud Service Git]/core/src/main/java/com/<program name>/core/service`
   * `[Archetype Project in Cloud Service Git] /core/src/main/java/com/<program name>/core/servlets/FileAttachmentServlet.java`
   * `[Archetype Project in Cloud Service Git]/ui.apps/src/main/content/jcr_root/apps/<program name>/config`

### 새 SDK 환경으로 백업 가져오기 {#import-the-backup-to-your-new-SDK-environment}

적응형 Forms, 템플릿, 양식 데이터 모델, 테마, 구성 및 사용자 지정 코드를 새로운 환경으로 가져옵니다. 다음 작업을 수행하여 백업을 가져올 수 있습니다.

1. 새로운 SDK 환경으로 적응형 Forms, 테마 및 PDF forms [가져오기](import-export-forms-templates.md#manage-forms-and-related-assets).
1. 적응형 양식 템플릿을 새 SDK 환경으로 가져옵니다.

1. 양식 데이터 모델을 새 SDK 환경에 업로드합니다.

1. 편집 가능한 템플릿, 클라우드 구성 및 워크플로우 모델을 가져옵니다. 새 SDK 환경에서 이전에 언급된 모든 항목을 가져오려면 이러한 항목이 포함된 CRX 패키지를 새 SDK 환경으로 가져옵니다.

1. 로컬 개발 환경에서 이메일 구성 가져오기, 제출 및 작업 코드 미리 채우기. 이러한 설정 및 구성을 가져오려면 이전 Archetype 프로젝트에서 새 Archetype 프로젝트에 다음 파일을 배치합니다.

   * `[Archetype Project in Cloud Service Git]/core/src/main/java/com/<program name>/core/service`
   * `[Archetype Project in Cloud Service Git] /core/src/main/java/com/<program name>/core/servlets/FileAttachmentServlet.java`
   * `[Archetype Project in Cloud Service Git]/ui.apps/src/main/content/jcr_root/apps/<program name>/config`

이제 새 환경에 이전 환경의 양식 및 관련 자산이 있습니다.
