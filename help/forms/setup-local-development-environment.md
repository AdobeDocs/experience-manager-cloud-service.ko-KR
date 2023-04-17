---
title: Adobe Experience Manager Forms as a Cloud Service에 대한 로컬 개발 환경 설정
description: Adobe Experience Manager Forms as a Cloud Service에 대한 로컬 개발 환경 설정
exl-id: 12877a77-094f-492a-af58-cffafecf79ae
source-git-commit: a4fd268cb143c1356de3db9d55b16ccb58b67d4b
workflow-type: tm+mt
source-wordcount: '3020'
ht-degree: 2%

---

# 로컬 개발 환경 및 초기 개발 프로젝트 설정 {#overview}

을 설정하고 구성할 때 [!DNL  Adobe Experience Manager Forms] 로서의 [!DNL  Cloud Service] 환경에서는 클라우드에 개발, 스테이징 및 프로덕션 환경을 설정합니다. 또한 로컬 개발 환경을 설정하고 구성할 수도 있습니다.

로컬 개발 환경을 사용하여 클라우드 개발 환경에 로그인하지 않고 다음 작업을 수행할 수 있습니다.

* [양식 만들기](creating-adaptive-form.md) 및 관련 자산(테마, 템플릿, 사용자 지정 제출 작업 등)
* [PDF 양식을 적응형 양식으로 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html)
* 생성할 응용 프로그램 빌드 [고객 커뮤니케이션](aem-forms-cloud-service-communications-introduction.md) 요청 시 또는 배치 모드에서 사용할 수 있습니다.

응용 양식 또는 관련 자산이 로컬 개발 인스턴스 또는 애플리케이션에서 생성하여 생성할 준비가 되면 [고객 커뮤니케이션] 준비가 되면 추가 테스트 또는 프로덕션 환경으로 이동하기 위해 적응형 양식 또는 고객 커뮤니케이션 애플리케이션을 로컬 개발 환경에서 Cloud Service 환경으로 내보낼 수 있습니다.

로컬 개발 환경에서 사용자 지정 구성 요소 및 미리 채우기 서비스와 같은 사용자 지정 코드를 개발하고 테스트할 수도 있습니다. 사용자 지정 코드가 테스트되고 준비되면 Cloud Service 개발 환경의 Git 저장소를 사용하여 사용자 지정 코드를 배포할 수 있습니다.

새 로컬 개발 환경을 설정하고 이를 사용하여 활동에 대해 개발하려면 나열된 순서로 다음 작업을 수행하십시오.

* [개발 도구 설정](#setup-development-tools-for-AEM-projects)

* [로컬 작성자 및 게시 인스턴스 설정](#set-up-local-experience-manager-environment-for-development)

* [로컬 개발 인스턴스에 Forms 아카이브 추가 및 사용자 구성](#add-forms-archive-configure-users)

* [마이크로 서비스를 위한 로컬 개발 환경 설정](#docker-microservices)

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

로컬 개발 환경을 설정하려면 다음 소프트웨어가 필요합니다. 로컬 개발 환경 설정을 시작하기 전에 다음 코드를 다운로드하십시오.

| 소프트웨어 | 설명 | 다운로드 링크 |
|---|---|---|
| Adobe Experience Manager as a Cloud Service SDK | SDK에 포함 [!DNL Adobe Experience Manager] QuickStart 및 Dispatcher 도구 | 에서 최신 SDK를 다운로드합니다. [소프트웨어 배포](#software-distribution) |  |
| Adobe Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능) | 적응형 Forms 및 기타 Adobe Experience Manager Forms 기능을 만들고, 스타일을 지정하고, 최적화하는 도구 | 다운로드 위치 [소프트웨어 배포](#software-distribution) |
| (선택 사항) Adobe Experience Manager Forms 참조 컨텐츠 | 적응형 Forms 및 기타 Adobe Experience Manager Forms 기능을 만들고, 스타일을 지정하고, 최적화하는 도구 | 다운로드 위치 [소프트웨어 배포](#software-distribution) |
| (선택 사항) Adobe Experience Manager Forms Designer | 적응형 Forms 및 기타 Adobe Experience Manager Forms 기능을 만들고, 스타일을 지정하고, 최적화하는 도구 | 다운로드 위치 [소프트웨어 배포](#software-distribution) |

### 소프트웨어 배포에서 최신 버전의 소프트웨어를 다운로드합니다 {#software-distribution}

최신 버전의 Adobe Experience Manager as a Cloud Service SDK를 다운로드하려면 Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능), 양식 참조 자산 또는 Forms 디자이너를 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html):

1. 에 로그인합니다. <https://experience.adobe.com/#/downloads> Adobe ID 사용

   >[!NOTE]
   >
   > AEM as a Cloud Service SDK를 다운로드하려면 Adobe 조직에 AEM as a Cloud Service이 제공되어야 합니다.

1. 로 이동합니다 **[!UICONTROL AEM as a Cloud Service]** 탭.
1. 게시된 날짜별로 내림차순으로 정렬합니다.
1. 최신 Adobe Experience Manager as a Cloud Service SDK, Experience Manager Forms 기능 아카이브(AEM Forms 추가 기능), 양식 참조 자산 또는 Forms 디자이너를 클릭합니다.
1. EULA를 검토하고 수락하십시오. 탭하기 **[!UICONTROL 다운로드]** 버튼을 클릭합니다.

## AEM 프로젝트용 개발 도구 설정 {#setup-development-tools-for-AEM-projects}

Adobe Experience Manager Forms 프로젝트는 사용자 지정 코드 베이스입니다. 여기에는 Cloud Manager를 통해 배포되는 코드, 구성 및 컨텐츠가 포함되어 있습니다 [!DNL Adobe Experience Manager] as a Cloud Service. 다음 [AEM Project Maven Archetype](https://github.com/adobe/aem-project-archetype) 프로젝트에 대한 기준 구조를 제공합니다.

에 사용할 다음 개발 도구를 설정합니다. [!DNL Adobe Experience Manager] 개발 프로젝트:

* [Java™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#local-development-environment-set-up)
* [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-git)
* [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#node-js)
* [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-maven)

이전에 언급된 개발 도구를 설정하는 자세한 지침은 [개발 도구 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html).

## 개발을 위한 로컬 Experience Manager 환경 설정

Cloud Service SDK는 QuickStart 파일을 제공합니다. 로컬 버전의 Experience Manager을 실행합니다. 로컬로 작성자 또는 게시 인스턴스를 실행할 수 있습니다.

QuickStart는 로컬 개발 환경을 제공하지만 사용 가능한 일부 기능은 없습니다. [!DNL Adobe Experience Manager] as a Cloud Service. 따라서 항상 [!DNL Adobe Experience Manager] 기능을 스테이지 또는 프로덕션으로 이동하기 전에 as a Cloud Service 개발 환경.

로컬 Experience Manager 환경을 설치 및 구성하려면 다음 단계를 수행하십시오.

* [다운로드 및 추출](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) a [!DNL Adobe Experience Manager] as a Cloud Service SDK
* [작성자 인스턴스 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#set-up-local-aem-author-service)
* [게시 인스턴스 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#set-up-local-aem-publish-service)

## 로컬 작성자 및 게시 인스턴스에 Forms 아카이브 추가 및 Forms 관련 사용자 구성 {#add-forms-archive-configure-users}

Forms 아카이브를 Experience Manager 인스턴스에 추가하고 양식별 사용자를 구성하려면 나열된 단계를 수행하십시오.

### 최신 Forms 추가 기능 아카이브 설치 {#add-forms-archive}

Adobe Experience Manager Forms as a Cloud Service 기능 아카이브는 로컬 개발 환경에서 적응형 Forms을 생성, 스타일 지정 및 최적화하는 도구를 제공합니다. 패키지를 설치하여 적응형 양식을 만들고 [!DNL AEM Forms]. 패키지를 설치하려면 다음을 수행하십시오.

1. 최신 다운로드 및 추출 [!DNL AEM Forms] 운영 체제를 위한 아카이브 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

1. crx-quickstart/install 디렉토리로 이동합니다. 폴더가 없으면 폴더를 만듭니다.

1. AEM 인스턴스를 중지하고 [!DNL AEM Forms] 추가 기능 아카이브, `aem-forms-addon-<version>.far`를 누르고 설치 폴더에서 인스턴스를 다시 시작합니다.

### 사용자 및 권한 구성 {#configure-users-and-permissions}

Form Developer 및 Form Programming 및 [이러한 사용자를 사전 정의된 양식 그룹에 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=en#accessing) 필요한 권한을 제공하려면 다음을 수행하십시오. 아래 표에는 각 양식 사용자 유형에 대한 모든 사용자 유형과 사전 정의된 그룹이 나와 있습니다.

| 사용자 유형 | AEM 그룹 |
|---|---|
| 실무자 | [!DNL forms-users] (AEM Forms 사용자), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], 및 [!DNL fdm-authors] |
| 양식 개발자 | [!DNL forms-users] (AEM Forms 사용자), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], 및 [!DNL fdm-authors] |
| 고객 경험 리드 또는 UX 디자이너 | [!DNL forms-users], [!DNL template-authors] |
| AEM 관리자 | [!DNL aem-administrators], [!DNL fd-administrators] |
| 최종 사용자 | 사용자가 적응형 양식을 보고 제출하기 위해 로그인해야 하는 경우 이러한 사용자를 [!DNL forms-users] 그룹에 속해 있어야 합니다. </br> 적응형 Forms에 액세스하는 데 사용자 인증이 필요하지 않으면 그러한 사용자에게 그룹을 할당하지 마십시오. |

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

AEM Forms as a Cloud Services은 문서 작성 및 다른 마이크로서비스 사용을 위한 문서 기반 SDK 환경을 제공합니다. 플랫폼별 바이너리 및 적응을 수동으로 구성할 수 있습니다. 환경을 설정하려면 다음을 수행하십시오.

1. 설치 및 구성 Docker:

   * (Microsoft® Windows용) 설치 [Docker Desktop](https://www.docker.com/products/docker-desktop). 다음을 구성합니다 `Docker Engine` 및 `docker-compose` 사용자 시스템에 있는

   * (Apple macOS) 설치 [Mac용 Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac). 여기에는 Docker 엔진, Docker CLI 클라이언트, Docker Compose, Docker Content Trust, Kubernetes 및 Credential Helper가 포함됩니다.

   * (Linux®의 경우) 설치 [Docker 엔진](https://docs.docker.com/engine/install/#server) 및 [Docker 작성](https://docs.docker.com/compose/install/) 사용자 시스템에 있는
   >[!NOTE]
   >
   > * Apple macOS의 허용 목록에 추가하다 경우 로컬 AEM 작성자 인스턴스가 포함된 폴더를 게시합니다.
   >
   > * Windows용 Docker Desktop은 두 개의 백엔드인 Hyper-V를 지원합니다.
      > (기존) 및 WSL2(최신). 파일 공유 자동
      > WSL2 사용 시 Docker에서 관리(최신) 당신은
      > Hyper-V(레거시)를 사용하는 동안 파일 공유를 명시적으로 구성합니다.


1. 작성자 및 게시 인스턴스와 동시에 aem-sdk와 같은 폴더를 만듭니다. 예: C:\aem-sdk

1. 추출 `aem-forms-addon-<version>.zip\aem-forms-addon-native-<version>.zip` 파일.

   ![추출된 aem forms 추가 기본](assets/microservice-docker.png)

1. 환경 변수 AEM_HOME을 만들고 로컬 AEM 작성자 설치를 가리킵니다. 예: C:\aem\author\

1. 편집할 sdk.bat 또는 sdk.sh를 엽니다. 로컬 AEM 작성자 설치를 가리키도록 AEM_HOME을 설정합니다. 예: C:\aem\author\

1. 명령 프롬프트를 열고 `aem-forms-addon-native-<version>` 폴더를 입력합니다.

1. 로컬 AEM 작성자 인스턴스가 작동되고 실행 중인지 확인합니다. 다음 명령을 실행하여 SDK를 시작합니다.

   * (Microsoft® Windows) `sdk.bat start`
   * (Linux® 또는 Apple macOS의 경우) `AEM_HOME=[local AEM Author installation] ./sdk.sh start`

   >[!NOTE]
   >
   > sdk.sh 파일에서 환경 변수를 정의한 경우 명령줄에서 이 변수를 지정하는 것은 선택 사항입니다. 셸 스크립트를 업데이트하지 않고 명령을 실행할 수 있도록 명령줄에서 환경 변수를 정의하는 옵션이 제공됩니다.

   ![start-sdk-command](assets/start-sdk.png)

이제 로컬 개발 환경을 사용하여 기록 문서를 렌더링할 수 있습니다. 테스트하려면 XDP 파일을 환경에 업로드하고 렌더링합니다. 예, <http://localhost:4502/libs/xfaforms/profiles/default.print.pdf?template=crx:///content/dam/formsanddocuments/cheque-request.xdp> xdp 파일을 PDF 문서로 변환합니다.

## Experience Manager 원형 기반 Forms용 개발 프로젝트 설정 {#forms-cloud-service-local-development-environment}

이 프로젝트를 사용하여 응용 Forms 만들기, 구성 업데이트, 오버레이 배포, 사용자 지정 적응형 양식 구성 요소 만들기, 테스트 및 로컬 사용자 지정 코드 만들기 [!DNL Experience Manager Forms] SDK. 로컬에서 테스트한 후 프로젝트를  [!DNL Experience Manager Forms] as a Cloud Service 프로덕션 및 비프로덕션 환경 프로젝트를 배포할 때 다음 AEM Forms 자산도 배포됩니다.

| 테마 | 템플릿 | 양식 데이터 모델 |
---------|----------|---------
| 캔버스 3.0 | 기본 | Microsoft® Dynamics 365 |
| 조용한 | 비어 있음 | Salesforce |
| Urbane |  |  |
| 울트라마린 |  |  |
| 베릴 |  |  |

>[!NOTE]
>
> AEM Archetype 버전 30 이상 기반 프로젝트를 설정하여 Microsoft® Dynamics 365 및 Salesforce Form Data Models를 AEM Forms as a Cloud Service으로 가져오고 사용할 수 있습니다.
AEM Archetype 버전 32 이상 기반 프로젝트를 설정하여 AEM Forms as a Cloud Service으로 Tranquil, Urbane 및 Ultramarine 테마를 가져오고 사용할 수 있습니다.

프로젝트를 설정하려면 다음을 수행하십시오.

1. **로컬 개발 인스턴스에서 Cloud Manager Git 리포지토리 복제:**  Cloud Manager Git 리포지토리에는 기본 AEM 프로젝트가 포함되어 있습니다. 이것은 [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Cloud Manager UI에서 셀프 서비스 Git 계정 관리를 사용하여 Cloud Manager Git 리포지토리를 복제하여 로컬 개발 환경에서 프로젝트를 가져올 수 있습니다. 리포지토리 액세스에 대한 자세한 내용은 [저장소 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html).

<!-- 1. 
After the repository is cloned, [integrate your Git repo with Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html)

**Make cloned AEM project compatible with [!DNL AEM Forms] as a Cloud Service:** Remove uber-jar and other non-cloud dependencies from the pom.xml files of the project. You can refer the pom.xml files of the [sample AEM project](assets/FaaCSample.zip) for the list of required dependencies and update your AEM project accordingly. You can also refer [AEM Project Structure](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) to learn changes required to make an AEM project compatible with AEM as a Cloud Service.  -->

1. **만들기 [!DNL Experience Manager Forms] 로서의 [Cloud Service] 프로젝트:** 만들기 [!DNL Experience Manager Forms] 로서의 [Cloud Service] 최신 프로젝트 기반 [AEM Archetype](https://github.com/adobe/aem-project-archetype) 또는 나중에 사용합니다. Archetype은 개발자가 을 위한 개발을 쉽게 시작할 수 있도록 지원합니다 [!DNL AEM Forms] as a Cloud Service. 또한 빠르게 시작할 수 있도록 몇 가지 샘플 테마 및 템플릿이 포함되어 있습니다.

   명령 프롬프트를 열고 아래 명령을 실행하여 [!DNL Experience Manager Forms] as a Cloud Service 프로젝트.

   ```shell
   mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion=40 -D aemVersion="cloud" -D appTitle="Borgo AEM Forms" -D appId="bgaemforms" -D groupId="com.bgaemforms" -D includeFormsenrollment="y" -D includeFormscommunications="y" -D includeExamples="y" -D 
   
   mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="41" -D appTitle=mysite -D appId=mysite -D groupId=com.mysite -D includeFormsenrollment="y" -D aemVersion="cloud"
   ```

   변경 `appTitle`, `appId`, 및 `groupId` 위 명령에서 사용자 환경을 반영합니다. 또한 includeFormsenrolment, includeFormscommunications 및 includeFormsheadless에 대한 값을 로 설정합니다. `y` 또는 `n` 라이선스 및 요구 사항에 따라 다릅니다. includeFormsadless는 코어 구성 요소를 기반으로 적응형 Forms을 만들어야 합니다.

   * 를 사용하십시오 `includeFormsenrollment=y` 적응형 Forms을 만드는 데 필요한 Forms 관련 구성, 테마, 템플릿, 핵심 구성 요소 및 종속성을 포함하는 선택 사항입니다. Forms Portal을 사용하는 경우 `includeExamples=y` 선택 사항입니다. 또한 프로젝트에 Forms Portal 핵심 구성 요소가 추가됩니다.

   * 를 사용하십시오 `includeFormscommunications=y` 고객 커뮤니케이션 기능을 포함하는 데 필요한 Forms 핵심 구성 요소 및 종속성을 포함하는 옵션.

1. 프로젝트를 로컬 개발 환경에 배포합니다. 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

   `mvn -PautoInstallPackage clean install`

   전체 명령 목록이 필요하면 [빌드 및 설치](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing)

1. [코드를 [!DNL AEM Forms] as a Cloud Service 환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases).

## 로컬 Dispatcher 도구 설정 {#setup-local-dispatcher-tools}

Dispatcher는 CDN과 AEM 게시 계층 간에 보안 및 성능 레이어를 제공하는 Apache HTTP 웹 서버 모듈입니다. Dispatcher는 전체 Experience Manager 아키텍처의 필수적인 부분이며 로컬 개발 환경에 포함되어야 합니다.

다음 단계를 수행하여 로컬 Dispatcher를 구성한 다음 Forms 관련 규칙을 추가합니다.

### 로컬 Dispatcher 설정 {#setup-local-dispatcher}

다음 [!DNL Experience Manager] as a Cloud Service SDK에는 권장 Dispatcher 도구 버전이 포함되어 있어서 Dispatcher를 로컬에서 구성, 유효성 검사 및 시뮬레이션을 용이하게 합니다. Dispatcher 도구는 Docker 기반이며 Apache HTTP Web Server 및 Dispatcher 구성 파일을 호환되는 형식으로 변환하고 Docker 컨테이너에서 실행되는 Dispatcher에 배포하는 명령줄 도구를 제공합니다.

Dispatcher에서 캐싱이 [!DNL AEM Forms] 클라이언트에서 적응형 Forms을 미리 채우려면 다음을 수행하십시오. 미리 입력된 양식의 렌더링 속도가 향상됩니다.

Dispatcher 설정에 대한 자세한 지침은 [로컬 Dispatcher 도구 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#local-development-environment-set-up)

### Dispatcher에 Forms 특정 규칙 추가 {#forms-specific-rules-to-dispatcher}

다음 단계를 수행하여 Experience Manager Forms as a Cloud Service에 대한 Dispatcher 캐시를 구성합니다.

1. AEM 프로젝트를 열고 다음 위치로 이동합니다. `\src\conf.dispatcher.d\available_farms`
1. 의 사본 만들기 `default.farm` 파일. (예: `forms.farm`)
1. 새로 만든 `forms.farm` 파일을 편집하고 다음 코드를 바꿉니다.

   ```json
   #/ignoreUrlParams {
   #/0001 { /glob "*" /type "deny" }
   #/0002 { /glob "q" /type "allow" }
   #}
   ```

   with

   ```json
   /ignoreUrlParams {
   /0001 { /glob "*" /type "deny" }
   /0002 { /glob "dataRef" /type "allow" }
   }
   ```

1. 파일을 저장하고 닫습니다.
1. 이동 `conf.d/enabled_farms` 그리고 `forms.farm` 파일.
1. 프로젝트를 컴파일하고 [!DNL AEM Forms] as a Cloud Service 환경.

### 캐싱에 대한 고려 사항 {#considerations-about-caching}

* Dispatcher 캐싱은 [!DNL AEM Forms] 클라이언트에서 적응형 Forms을 미리 채우려면 다음을 수행하십시오. 미리 입력된 양식의 렌더링 속도가 향상됩니다.
* 보안 콘텐츠 기능 캐싱은 기본적으로 비활성화됩니다. 이 기능을 활성화하려면 [보안 콘텐츠 캐싱](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=en) 문서
* Dispatcher는 일부 응용 Forms 및 관련 응용 Forms을 무효화하지 못할 수 있습니다. 이러한 문제를 해결하려면 [[!DNL AEM Forms] 캐싱](troubleshooting-caching-performance.md) 문제 해결 섹션 을 참조하십시오.
* 현지화된 적응형 Forms 캐싱:
   * URL 형식 사용 `http://host:port/content/forms/af/<afName>.<locale>.html` 를 입력하여 대신 현지화된 적응형 양식 버전을 요청합니다. `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`
   * 브라우저 로케일 옵션은 기본적으로 비활성화됩니다. 브라우저 로케일 설정을 변경하려면
* URL 형식을 사용하는 경우 `http://host:port/content/forms/af/<adaptivefName>.html`및 구성 관리자에서 브라우저 로케일 사용 이 비활성화되어 있으면 현지화되지 않은 적응형 양식 버전이 제공됩니다. 현지화되지 않은 언어는 적응형 양식을 개발하는 동안 사용되는 언어입니다. 브라우저(브라우저 로케일)에 대해 구성된 로케일은 고려되지 않으며, 현지화되지 않은 적응형 양식 버전이 제공됩니다.
* URL 형식을 사용하는 경우 `http://host:port/content/forms/af/<adaptivefName>.html`, 구성 관리자에서 브라우저 로케일 사용 을 활성화하면 현지화된 버전의 적응형 양식이 제공됩니다(사용 가능한 경우). 현지화된 적응형 양식의 언어는 브라우저(브라우저 로케일)에 대해 구성된 로케일을 기반으로 합니다. 이로 인해 [적응형 양식의 첫 번째 인스턴스만 캐싱]. 인스턴스에서 문제가 발생하지 않도록 하려면 다음을 참조하십시오 [적응형 양식의 첫 번째 인스턴스만 캐시됩니다](troubleshooting-caching-performance.md) 문제 해결 섹션 을 참조하십시오.

로컬 개발 환경이 준비되었습니다.

## 기존 AEM Archetype 기반 프로젝트에 대한 응용 Forms 코어 구성 요소 활성화 {#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project}

AEM Forms as a Cloud Service용 AEM Archetype 버전 40 이상 기반 프로그램을 사용하는 경우 코어 구성 요소 가 사용자 환경에 자동으로 활성화됩니다. 환경에 대한 코어 구성 요소 활성화 시 **응용 Forms(핵심 구성 요소)** 템플릿 및 캔버스 테마가 환경에 추가됩니다. AEM SDK 버전이 2023.02.0보다 오래된 경우, [확인 `prerelease` 환경에 활성화된 플래그](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) 적응형 Forms 코어 구성 요소는 2023.02.0 릴리스 전 사전 릴리스의 일부입니다.

이전 버전의 Archetype을 기반으로 AEM Forms as a Cloud Service 환경에 적응형 Forms 코어 구성 요소를 활성화하려면 WCM 코어 구성 요소 예 아티팩트와 Forms 코어 구성 요소 아티팩트(예 포함)를 프로젝트에 포함합니다.

1. 일반 텍스트 코드 편집기에서 AEM Archetype 프로젝트 폴더를 엽니다. 예: VS 코드.

1. 로컬 환경에서 AEM Archetype 프로젝트의 최상위 .pom 파일(상위 pom)을 열고 다음 속성을 파일에 추가하고 저장합니다.

   ```XML
   <properties>
       <core.forms.components.version>2.0.4</core.forms.components.version> <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
       <core.wcm.components.version>2.21.2</core.wcm.components.version>
   </properties>
   ```

   최신 버전의 경우 `core.forms.components` 및 `core.wcm.components`, check [핵심 구성 요소 설명서](https://github.com/adobe/aem-core-forms-components).

1. 최상위 수준(상위) ppm.xml 파일의 종속성 섹션에서 다음 종속성을 추가합니다.

   ```XML
       <!-- Forms Core Component Dependencies -->
               <dependency>
                   <groupId>com.adobe.aem</groupId>
                   <artifactId>core-forms-components-core</artifactId>
                   <version>${core.forms.components.version}</version>
               </dependency>
               <dependency>
                   <groupId>com.adobe.aem</groupId>
                   <artifactId>core-forms-components-apps</artifactId>
                   <version>${core.forms.components.version}</version>
                   <type>zip</type>
               </dependency>
               <dependency>
                   <groupId>com.adobe.aem</groupId>
                   <artifactId>core-forms-components-af-core</artifactId>
                   <version>${core.forms.components.version}</version>
               </dependency>
               <dependency>
                   <groupId>com.adobe.aem</groupId>
                   <artifactId>core-forms-components-af-apps</artifactId>
                   <version>${core.forms.components.version}</version>
                   <type>zip</type>
               </dependency>
               <dependency>
                   <groupId>com.adobe.aem</groupId>
                   <artifactId>core-forms-components-examples-apps</artifactId>
                   <type>zip</type>
                   <version>${core.forms.components.version}</version>
               </dependency>
               <dependency>
                   <groupId>com.adobe.aem</groupId>
                   <artifactId>core-forms-components-examples-content</artifactId>
                   <type>zip</type>
                   <version>${core.forms.components.version}</version>
               </dependency>
       <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. all/pom.xml 파일을 열고 다음 종속성을 추가하여 응용 Forms 코어 구성 요소 아티팩트를 AEM Archetype 프로젝트에 추가합니다.

   ```XML
       <dependency>
           <groupId>com.adobe.aem</groupId>
           <artifactId>core-forms-components-af-apps</artifactId>
           <type>zip</type>
       </dependency>
       <dependency>
           <groupId>com.adobe.aem</groupId>
           <artifactId>core-forms-components-examples-apps</artifactId>
           <type>zip</type>
       </dependency>
       <dependency>
           <groupId>com.adobe.aem</groupId>
           <artifactId>core-forms-components-examples-content</artifactId>
           <type>zip</type>
       </dependency>
   ```

   >[!NOTE]
   다음 응용 Forms 코어 구성 요소 가공물이 프로젝트에 포함되어 있지 않은지 확인하십시오.
   `<dependency>`
   `<groupId>com.adobe.aem</groupId>`
   `<artifactId>core-forms-components-apps</artifactId>`
   `</dependency>`
   및
   `<dependency>`
   `<groupId>com.adobe.aem</groupId>`
   `<artifactId>core-forms-components-core</artifactId>`
   `</dependency>`

1. [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html). 성공적인 파이프라인 실행 후 환경에 적응형 Forms 코어 구성 요소 가 활성화됩니다. 또한 적응형 Forms(핵심 구성 요소) 템플릿 및 캔버스 테마가 Forms as a Cloud Service 환경에 추가됩니다.


## 로컬 개발 환경 업그레이드 {#upgrade-your-local-development-environment}

SDK를 새 버전으로 업그레이드하려면 전체 로컬 개발 환경을 대체해야 하므로 로컬 리포지토리의 모든 코드, 구성 및 컨텐츠가 손실됩니다. 파기하지 않아야 하는 모든 코드, 구성 또는 컨텐츠가 Git에 안전하게 커밋되거나 로컬 Experience Manager 인스턴스에서 CRX-Packages로 내보내지지 않도록 합니다.

### SDK를 업그레이드할 때 컨텐츠 손실을 방지하는 방법 {#avoid-content-loss-when-upgrading--SDK}

SDK를 업그레이드하면 새 저장소([AEM 프로젝트 설정](#forms-cloud-service-local-development-environment)). 즉, 이전 SDK의 리포지토리에 수행된 모든 변경 사항이 손실됩니다. SDK 업그레이드 사이에 컨텐츠를 유지할 수 있는 실용적인 전략을 보려면 를 참조하십시오 [AEM SDK를 업그레이드할 때 컨텐츠 손실을 방지하는 방법](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#optional-local-aem-runtime-set-up-tasks)

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

### 새로운 SDK 환경에 Forms 관련 컨텐츠를 백업하고 가져옵니다 {#backup-and-import-Forms-specific-content-to-new-SDK-environment}

기존 SDK에서 새 SDK 환경으로 자산을 백업하고 이동하려면 다음을 수행하십시오.

* 기존 컨텐츠의 백업을 만듭니다.

* 새로운 SDK 환경을 설정합니다.

* 새 SDK 환경에 백업을 가져옵니다.

### 기존 컨텐츠의 백업 만들기 {#create-backup-of-your-existing-content}

응용 Forms, 템플릿, 양식 데이터 모델, 테마, 구성 및 사용자 지정 코드를 백업합니다. 다음 작업을 수행하여 백업을 만들 수 있습니다.

1. [다운로드](import-export-forms-templates.md#manage-forms-and-related-assets) 적응형 Forms, 테마 및 PDF forms.
1. 적응형 양식 템플릿을 내보냅니다.

1. 양식 데이터 모델 다운로드

1. 편집 가능한 템플릿, 클라우드 구성 및 워크플로우 모델을 내보냅니다. 기존 SDK에서 이전에 언급된 모든 항목을 내보내려면 [CRX-Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html) 다음 필터를 사용하여 다음을 수행하십시오.

   * /conf/ReferenceEditableTemplates
   * /conf/global/settings/cloudconfigs
   * /conf/global/settings/wcm
   * /var/workflow/models
   * /conf/global/settings/workflow
1. 로컬 개발 환경에서 전자 메일 구성, 제출 및 미리 채우기 작업 코드를 내보냅니다. 이러한 설정 및 구성을 내보내려면 로컬 개발 환경에서 다음 폴더 및 파일의 복사본을 만드십시오.

   * `[Archetype Project in Cloud Service Git]/core/src/main/java/com/<program name>/core/service`
   * `[Archetype Project in Cloud Service Git] /core/src/main/java/com/<program name>/core/servlets/FileAttachmentServlet.java`
   * `[Archetype Project in Cloud Service Git]/ui.apps/src/main/content/jcr_root/apps/<program name>/config`

### 새 SDK 환경에 백업 가져오기 {#import-the-backup-to-your-new-SDK-environment}

적응형 Forms, 템플릿, 양식 데이터 모델, 테마, 구성 및 사용자 지정 코드를 새로운 환경에 가져올 수 있습니다. 다음 작업을 수행하여 백업을 가져올 수 있습니다.

1. [가져오기](import-export-forms-templates.md#manage-forms-and-related-assets) 새로운 SDK 환경에 적응형 Forms, 테마 및 PDF forms.
1. 새 SDK 환경에 적응형 양식 템플릿을 가져옵니다.

1. 양식 데이터 모델을 새 SDK 환경에 업로드합니다.

1. 편집 가능한 템플릿, 클라우드 구성 및 워크플로우 모델을 가져옵니다. 이전에 언급된 모든 항목을 새 SDK 환경에 가져오려면 이러한 항목이 포함된 CRX-Package를 새 SDK 환경으로 가져옵니다.

1. 로컬 개발 환경에서 이메일 구성, 제출 및 미리 채우기 작업 코드를 가져옵니다. 이러한 설정 및 구성을 가져오려면 이전 Archetype 프로젝트의 다음 파일을 새 Archetype 프로젝트로 배치합니다.

   * `[Archetype Project in Cloud Service Git]/core/src/main/java/com/<program name>/core/service`
   * `[Archetype Project in Cloud Service Git] /core/src/main/java/com/<program name>/core/servlets/FileAttachmentServlet.java`
   * `[Archetype Project in Cloud Service Git]/ui.apps/src/main/content/jcr_root/apps/<program name>/config`

이제 새 환경에 이전 환경의 양식 및 관련 자산이 있습니다.
