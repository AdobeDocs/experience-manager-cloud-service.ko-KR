---
title: AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 양식 핵심 구성 요소 활성화
seo-title: Step-by-Step Guide for enabling Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment
description: 단계별 안내서를 통해 AEM Forms as a Cloud Service에서 적응형 양식 핵심 구성 요소를 활성화하는 방법에 대해 알아봅니다. 튜토리얼은 이 과정에 대해 소개하고 AEM Forms 환경의 강력한 기능을 쉽게 활성화할 수 있도록 해 줍니다.
seo-description: Learn how to enable Adaptive Forms Core Components on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
source-git-commit: 57acac078805bc195cb10c1e94462d5aa077b1af
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 93%

---


# AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 양식 핵심 구성 요소 활성화 {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | 이 문서 |

AEM Forms as a Cloud Service에서 적응형 양식 핵심 구성 요소를 활성화하면 여러 채널에 AEM Forms Cloud Service 인스턴스를 사용하여 핵심 구성 요소 기반 적응형 양식 및 Headless 양식을 만들고, 게시하고, 게재할 수 있습니다. Headless Adaptive Forms를 사용하려면 적응형 양식 핵심 구성 요소 활성화 환경이 필요합니다.

## 고려 사항

* 새로운 AEM Forms as a Cloud Service 프로그램을 만들 때 내 환경에 맞는 [적응형 양식 핵심 구성 요소 및 Headless 적응형 양식이 이미 활성화되어 있습니다](#are-adaptive-forms-core-components-enabled-for-my-environment).

* 핵심 구성 요소가 [임베드되지 않은](#enable-components) 이전 Forms as a Cloud Service 프로그램이 있는 경우 AEM as a Cloud Service 저장소에 [적응형 양식 핵심 구성 요소 종속성을 추가](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment)하고 Cloud Service 환경에 저장소를 배포하여 Headless 적응형 양식을 활성화할 수 있습니다.

* 기존 Cloud Service 환경에서 다음 옵션을 제공하는 경우 [핵심 구성 요소 기반 적응형 Forms 만들기](creating-adaptive-form-core-components.md), 적응형 Forms 핵심 구성 요소 및 Headless 적응형 Forms은 귀하의 환경에 대해 이미 활성화되어 있으며, 적응형 Forms의 Headless 표현이 필요한 모바일, 웹, 기본 앱 및 서비스와 같은 채널에 Headless 양식으로 핵심 구성 요소 기반 적응형 Forms을 제공할 수 있습니다.


## 적응형 양식 핵심 구성 요소 및 Headless 적응형 양식 활성화 {#enable-headless-forms}

AEM Forms as a Cloud Service 환경에 맞게 적응형 양식 핵심 구성 요소와 Headless 적응형 양식을 활성화하려면 나열된 순서대로 다음 단계를 수행하십시오.


![핵심 구성 요소 및 Headless 적응형 양식 활성화](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. AEM Forms as a Cloud Service Git 저장소 복제 {#clone-git-repository}

1. [Cloud Manager](https://my.cloudmanager.adobe.com/)에 로그인하고 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 **저장소 정보 액세스** 버튼을 클릭하여 Git 저장소에 액세스하고 관리합니다. 페이지에는 다음 정보가 포함됩니다.

   * Cloud Manager Git 저장소의 URL.
   * Git 저장소(사용자 이름 및 암호) 및 Git 사용자 이름의 자격 증명입니다.

   **암호 생성**&#x200B;을 클릭하여 암호를 보거나 생성합니다.

1. 로컬 컴퓨터에서 터미널 또는 명령 프롬프트를 열고 다음 명령을 실행합니다.

   ```Shell
   git clone [Git Repository URL]
   ```

   메시지가 표시되면 자격 증명을 제공합니다. 저장소를 로컬 컴퓨터에 복제합니다.


## 2. Git 저장소에 적응형 양식 핵심 구성 요소 종속성 추가 {#add-adaptive-forms-core-components-dependencies}

1. 일반 텍스트 코드 편집기에서 Git 저장소 폴더를 엽니다. 예: VS 코드.
1. 편집할 `[AEM Repository Folder]\pom.xml` 페이지를 엽니다.
1. `core.forms.components.version`, `core.forms.components.af.version` 및 `core.wcm.components.version` 구성 요소의 버전을 [핵심 구성 요소 설명서](https://github.com/adobe/aem-core-forms-components)에 지정된 버전으로 바꿉니다. 구성 요소가 없으면 이러한 구성 요소를 추가합니다.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![최신 버전의 양식 핵심 구성 요소 멘션](/help/forms/assets/latest-forms-component-version.png)

1. `[AEM Repository Folder]\pom.xml` 파일의 종속성 섹션에서 다음 종속성을 추가하고 파일을 저장합니다.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
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

1. 편집할 `[AEM Repository Folder]/all/pom.xml` 페이지를 엽니다. `<embeddeds>` 섹션에서 다음 종속성을 추가하고 파일을 저장합니다.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  `${appId}`를 appId로 바꿉니다.
   >
   >  `[AEM Repository Folder]/all/pom.xml` 파일에서 `${appId}`를 찾으려면 `-packages/application/install` 용어를 검색합니다. `-packages/application/install` 용어 앞의 텍스트는 `${appId}`입니다. 예: 다음 코드 `myheadlessform`은 `${appId}`입니다.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. `[AEM Repository Folder]/all/pom.xml` 파일의 `<dependencies>` 섹션에서 다음 종속성을 추가하고 파일을 저장합니다.

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
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

1. 편집할 `[AEM Repository Folder]/ui.apps/pom.xml`을 엽니다. `af-core bundle` 종속성을 추가하고 파일을 저장합니다.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >다음 적응형 양식 핵심 구성 요소 아티팩트가 프로젝트에 포함되지 않았는지 확인합니다.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > 및
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. 파일을 저장하고 닫습니다.

## 3. 업데이트된 코드 빌드 및 배포

업데이트된 코드를 로컬 개발 및 Cloud Service 환경에 배포하여 두 환경 모두에서 핵심 구성 요소를 활성화합니다.

* [로컬 개발 환경(AEM as a Cloud Service SDK)에서 업데이트된 코드 빌드 및 배포](#core-components-on-aem-forms-local-sdk)

* [AEM Forms as a Cloud Service 환경에서 업데이트된 코드 빌드 및 배포](#core-components-on-aem-forms-cs)

### 로컬 개발 환경에서 업데이트된 코드 빌드 및 배포 {#core-components-on-aem-forms-local-sdk}

1. 명령 프롬프트 또는 터미널을 엽니다.

1. Git 저장소 프로젝트의 루트 디렉터리로 이동합니다.

1. 다음 명령을 실행하여 환경에 맞는 패키지를 빌드합니다.

   ```Shell
       mvn clean install
   ```



   패키지가 정상적으로 빌드되면 [Git 저장소 폴더]\all\target\[appid].all-[version].zip에서 찾을 수 있습니다.

1. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en)를 사용하여 로컬 개발 환경에서 [AEM Archetype 프로젝트 폴더]\all\target\[appid].all-[version].zip 패키지를 배포합니다.


### AEM Forms as a Cloud Service 환경에서 업데이트된 코드 빌드 및 배포 {#core-components-on-aem-forms-cs}

1. 터미널 또는 명령 프롬프트를 엽니다.
1. `[AEM Repository Folder]`로 이동하고 나열된 순서대로 다음 명령을 실행합니다.

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. 파일이 Git 저장소에 커밋되면 [파이프라인을 실행합니다](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

   파이프라인 실행이 성공하면 해당 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화됩니다. 또한 적응형 양식(핵심 구성 요소) 템플릿 및 Canvas 3.0 테마가 Forms as a Cloud Service 환경에 추가되면 핵심 구성 요소 기반 적응형 양식을 사용자 정의하고 만들 수 있는 옵션이 제공됩니다.


## 자주 묻는 질문 {#faq}

### 핵심 구성 요소란 무엇입니까? {#core-components}

[핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)는 AEM에서 개발 시간을 가속화고 웹 사이트의 유지 관리 비용을 절감할 수 있는 표준화된 웹 콘텐츠 관리(WCM) 구성 요소입니다.

### 핵심 구성 요소를 활성화하는 경우 추가되는 모든 기능은 무엇입니까? {#core-components-capabilities}

내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되면 빈 핵심 구성 요소 기반 적응형 양식 템플릿 및 Canvas 3.0 테마가 해당 환경에 추가됩니다. 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되면 다음과 같은 작업을 수행할 수 있습니다.

* [핵심 구성 요소 기반 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md).
* [핵심 구성 요소 기반 적응형 양식 템플릿 만들기](/help/forms/template-editor.md).
* [핵심 구성 요소 기반 적응형 양식 템플릿의 사용자 정의 테마 만들기](/help/forms/using-themes-in-core-components.md).
* [모바일, 웹, 기본 앱 등 채널과 양식의 Headless 표현식이 필요한 서비스에 핵심 구성 요소 기반 적응형 양식의 JSON 표현식 제공](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html).

### 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되어 있습니까? {#enable-components}

내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되어 있는지 확인하려면:

1. [AEM Forms as a Cloud Service 저장소 복제](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. `[AEM Repository Folder]/all/pom.xml` AEM Forms Cloud Service Git 저장소 파일을 엽니다.

1. 다음 종속성을 검색합니다.

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![all/pom.xml에서 core-forms-components-af-core 아티팩트 찾기](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   종속성이 있는 경우 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화됩니다.

