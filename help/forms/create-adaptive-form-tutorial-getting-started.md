---
title: 적응형 Forms 시작하기
description: 단계별 튜토리얼을 통해 모바일 반응이 좋은 적응형 양식을 만드는 방법에 대해 알아봅니다. 이러한 양식은 여러 디바이스에 매끄럽게 적응하여 원활한 경험을 보장합니다.
keywords: 적응형 Forms, 반응형 Forms, HTML5 Forms
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: e6c58c835798b16158ab4aca26e381ab8f36afd3
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---


# 적응형 양식 만들기(핵심 구성 요소) - 튜토리얼

오늘날 사용자는 모든 상호 작용에 모바일 친화적인 경험을 기대하며 양식도 예외는 아닙니다. 적응형 양식을 사용하면 모바일 친화적일 뿐만 아니라 사용자 참여를 개선하고 양식을 완료하는 데 걸리는 시간을 단축할 수 있습니다.

이 튜토리얼에서는 적응형 양식을 만드는 방법에 대한 단계별 안내서를 제공합니다. 사용 사례와 여러 안내서로 분류되며, 각 안내서에서는 적응형 양식에 새 기능을 추가하는 방법을 알려줍니다.

자습서가 끝나면 다음 작업을 수행할 수 있습니다.

* 적응형 양식 및 해당 데이터 모델 만들기
* 적응형 양식 스타일 지정
* 적응형 양식 규칙 편집기를 사용하여 비즈니스 규칙 작성
* 적응형 양식 필드 미리 채우기
* 양식에 전자 서명 추가
* Google reCAPTCHA를 사용하여 봇에서 양식 Protect
* 다양한 언어를 위한 적응형 양식 현지화
* 구조화된 데이터를 생성하도록 양식 구성
* REST 끝점에 데이터를 전송하도록 양식 설정
* 적응형 양식 게시


## 핵심 구성 요소 기반 양식을 만드는 이유는 무엇입니까?

AEM Forms은 양식 경험을 만들 수 있는 기초 구성 요소 및 핵심 구성 요소를 제공합니다. 핵심 구성 요소는 새로운 양식 경험을 만드는 현대적이고 권장되는 방법입니다. 핵심 구성 요소를 사용하는 이유 이러한 구성 요소는 가벼운 오픈 소스(github에서 사용 가능)이며, 뛰어난 Google 등대 및 웹 바이탈 점수를 제공하고, 접근성을 준수하며, AEM Sites의 모든 친숙한 기능(버전 관리 및 현지화 등)을 제공합니다. 또한 이러한 구성 요소는 스타일링이 더 쉬우므로 조직의 브랜딩 지침에 따라 모양을 쉽게 사용자 지정할 수 있습니다. 여기에는 서드파티 종속성이 없으며 JavaScript 및 CSS에 대한 지식을 가진 개발자가 이러한 구성 요소를 쉽게 사용자 지정할 수 있습니다.

![적응형 Forms 기반의 핵심 구성 요소를 만드는 이유는 무엇입니까? 이러한 구성 요소는 가볍고, 스타일을 쉽게 지정하고, 높은 등대 점수를 제공하고, 접근성 표준을 지원하고, 쉽게 사용자 지정하고, 오픈 소스를 제공하고, github에서 사용할 수 있으며, 타사 라이브러리에 종속되지 않으며, AEM 개발자 및 AEM 작성자를 위한 학습 곡선이 거의 없습니다. AEM Forms 핵심 구성 요소 위에는 AEM WCM 핵심 구성 요소의 모든 기능이 있습니다.](/help/forms/assets/cc-core-components-benefits.png){width="50%"}

## 사용 사례: 적응형 Forms으로 간소화된 주택 대출 사전 자격

이 자습서에서는 대형 은행을 위한 적응형 양식을 작성합니다. 사용 사례는 다음과 같습니다.

잠재적 주택 구매자는 은행 웹사이트 또는 지점을 방문하여 주택 대출 옵션을 탐색한다. 기존 애플리케이션 프로세스는 시간이 오래 걸리고 복잡하기 때문에 사전에 설명서를 작성해야 하는 경우가 많습니다. 이는 일부 구매자들이 이 과정을 시작하는 것을 지연시켜 은행의 리드 세대와 구매자가 자신 있게 자신들의 꿈의 집을 찾는 능력을 방해한다.

대화형 주택 융자 사전 자격 양식을 개발해야 합니다. 이 양식은 기본 정보를 수집하고, 입력에 따라 차주를 사전 검증하고, 예상 대출 금액, 잠재 계약금 요구 사항 및 다양한 대출 유형을 기반으로 한 이자율을 제공합니다. 사전 자격을 갖춘 사용자는 사전 자격 양식에서 직접 전체 대출 신청을 시작할 수 있습니다.

양식은 적응형 양식을 사용하여 작성됩니다. 이를 통해 정확한 주택대출 사전자격을 위해 필요한 금융데이터를 수집하면서 개인화된 경험을 할 수 있다.

자습서를 완료하면 양식이 다음 양식과 같이 표시되고 작동합니다.

![여기에 작업 양식 추가](/help/forms/assets/cc-tutorial-final-form.png)

## 개발 환경 설정

적응형 양식을 Cloud Service 환경에 배포하기 전에 로컬 컴퓨터에서 직접 빌드하고 테스트할 수 있습니다. Adobe은에 로컬 개발을 위한 AEM SDK를 제공하여 다음을 수행할 수 있습니다.

* 로컬에서 양식을 만들고, 사용자 지정하고, 테스트합니다.
* 양식 테마 디자인 및 로컬에서 구성 빌드,
* 완료된 자산을 클라우드에 쉽게 배포할 수 있습니다.

AEM SDK를 사용한 로컬 개발은 시간을 절약하고 개발 프로세스를 간소화합니다


**시작할 준비가 되셨습니까?**

1. [AEM 프로젝트용 개발 도구 설정](/help/forms/setup-local-development-environment.md#set-up-development-tools-for-aem-projects): 의 최신 릴리스를 다운로드하여 설치합니다. [Java 11™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#local-development-environment-set-up), [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-git), [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#node-js), 및 [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#install-maven). 또한 일반 텍스트 편집기를 설치하십시오. 이 자습서의 예제는 Visual Studio 코드를 기반으로 합니다.

1. [AEM SDK 설치](/help/forms/setup-local-development-environment.md#set-up-local-experience-manager-environment-for-development): 최신 버전의 AEM SDK를 다운로드하여 설치합니다. AEM 개발에 필수적인 도구를 제공합니다. AEM SDK 버전을 기록해 두십시오.

   ![소프트웨어 배포](/help/forms/assets/software-distribution.png)

   ![AEM SDK 설치](/help/forms/assets/start-aem-sdk.png)

1. [AEM Forms 추가 기능 추가](/help/forms/setup-local-development-environment.md#add-forms-archive-to-local-author-and-publish-instances-and-configure-forms-specific-users): 에서 AEM SDK 버전에 일치하는 AEM Forms 추가 기능을 다운로드하여 설치합니다. [소프트웨어 배포](https://experience.adobe.com/#/downloads) 포털.
   ![install-aem-forms-add-on](/help/forms/assets/install-aem-forms-add-on.png)

   +++AEM Forms 추가 기능 설치:

   AEM Forms 추가 기능을 설치하려면:

   1. AEM SDK를 중지합니다.
   1. AEM Forms 추가 기능(.far) 파일을 `AEM SDK/crx-quickstart/install` 폴더,
   1. AEM SDK를 다시 시작합니다.

+++

1. [사용자 권한 구성](/help/forms/setup-local-development-environment.md#configure-users-and-permissions): 개발, 작성 및 기타 권한을 가진 사용자를 만들고 이러한 사용자를 사전 정의된 양식 그룹에 추가합니다.


1. [적응형 Forms 템플릿 추가](/help/forms/setup-local-development-environment.md#set-up-a-development-project-for-forms-based-on-experience-manager-archetype): AEM Archetype 48 이상을 사용하여 새 AEM 프로젝트를 만들고 AEM SDK에 배포합니다. 프로젝트는 적응형 Forms 템플릿을 AEM SDK에 추가합니다.

   ![적응형 양식 템플릿](/help/forms/assets/adaptive-forms-templates.png)

   +++AEM SDK에 적응형 Forms 템플릿 추가:

   1. 아래 명령을 실행하여 AEM 프로젝트를 만듭니다.

      ```
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="48" -D appTitle=securbank -D appId=securbank -D groupId=com.securbank -D includeFormsenrollment="y" -D aemVersion="cloud"
      ```

      ![AEM-Archetype-Project](/help/forms/assets/aem-archetype-project.png)

   1. 로컬 개발 환경에 프로젝트를 배포합니다. 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

      ```
      cd securbank
      
      mvn -PautoInstallPackage clean install
      ```

   AEM 프로젝트를 배포하면 환경에 적응형 Forms 템플릿을 볼 수 있습니다.

+++


로컬 AEM Forms 개발 환경 설정에 대한 자세한 지침 및 단계별 안내서는 다음을 참조하십시오. [AEM Forms용 로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md) 기사.



## 다음 단계

개발 환경을 구성하면 적응형 양식을 만들 수 있습니다. 다음 문서에서는 다음 방법을 배웁니다.

* 빈 템플릿에서 적응형 양식 만들기
* 정보를 표시하고 쉽게 수락할 수 있는 레이아웃 필드입니다.
* 양식을 미리 봅니다.

<!-- 

### Step 2: Create Form Data Model

A form data model lets you connect an adaptive form to disparate data sources. For example, AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. You can use the form data model with an adaptive form to retrieve, update, delete, and add data to connected data sources.

Goals of article:

* Create the form data model using Rest endpoint.
* Add data model objects so you can form the data model.
* Configure read and write services for the form data model.
* Test form data model and configured services with test data.

### Step 4: Apply rules to adaptive form fields

AEM Forms provide an editor to write rules on adaptive form objects. These rules define actions to trigger on form objects based on preset conditions, user inputs, and user actions on the form. It helps ensure accuracy and speeds up the form-filling experience.

Goals:

* Create and apply rules to adaptive form fields.
* Use rules to trigger form data model services to update the data to database.

### Step 5: Style your adaptive form

Adaptive forms provide OOTB themes and allows you to customize an existing theme to make a brand specific theme. 


A theme contains styling details for components and panels, and you can reuse a theme in different forms. Styles include properties such as background colors, state colors, transparency, alignment, and size. When you apply the theme to your form, the specified style reflects on corresponding components of your form.

Goals:

* Apply an out of the box theme to an adaptive form.
* Create your brand specific theme.


### Step 6: Publish your adaptive form

You can publish adaptive forms as a stand-alone form (single page application), include in AEM Sites page, or include in a non-AEM Sites page.

Goals:

* Publish the adaptive form as an AEM Page.
* Embed the adaptive form in an AEM Sites Page.
* Embed the adaptive form in an external webpage (a non-AEM webpage hosted outside AEM).

-->