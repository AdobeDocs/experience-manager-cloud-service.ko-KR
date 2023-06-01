---
title: AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 Forms 핵심 구성 요소 활성화
seo-title: Step-by-Step Guide for enabling Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment
description: 단계별 안내서를 통해 AEM Forms as a Cloud Service에서 적응형 Forms 핵심 구성 요소를 활성화하는 방법에 대해 알아보십시오. 튜토리얼에서는 이 강력한 기능을 AEM Forms 환경에 쉽게 사용할 수 있도록 하는 과정을 안내합니다.
seo-description: Learn how to enable Adaptive Forms Core Components on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
hide: true
hidefromtoc: true
source-git-commit: 7dc36220c1f12177037aaa79d864c1ec2209a301
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 3%

---


# AEM Forms as a Cloud Service 및 로컬 개발 환경에서 적응형 Forms 핵심 구성 요소 활성화 {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

AEM Forms as a Cloud Service에서 적응형 Forms 핵심 구성 요소를 활성화하면 AEM Forms Cloud Service 인스턴스를 사용하여 적응형 Forms 및 Headless Forms 기반의 핵심 구성 요소를 만들고, 게시하고, 여러 채널에 전달할 수 있습니다. Headless 적응형 Forms을 사용하려면 적응형 Forms 핵심 구성 요소 사용 환경이 필요합니다.

## 고려 사항

* 신선한 AEM Forms as a Cloud Service 프로그램을 만들 때, [적응형 Forms 핵심 구성 요소 및 Headless 적응형 Forms이 귀하의 환경에 대해 이미 활성화되었습니다](#are-adaptive-forms-core-components-enabled-for-my-environment).

* 핵심 구성 요소가 있는 이전 Forms as a Cloud Service 프로그램이 있는 경우 [활성화되지 않음](#enable-components), 다음을 수행할 수 있습니다. [적응형 Forms 핵심 구성 요소 종속성 추가](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) 를 AEM as a Cloud Service 저장소에 배포하고 Cloud Service 환경에 배포하여 Headless 적응형 Forms을 활성화하십시오.

* 기존 Cloud Service 환경에서 다음 옵션을 제공하는 경우 [핵심 구성 요소 기반 적응형 Forms 만들기](creating-adaptive-form-core-components.md), 적응형 Forms 핵심 구성 요소 및 Headless 적응형 Forms은 귀하의 환경에 대해 이미 활성화되어 있으며, 적응형 Forms의 Headless 표현이 필요한 모바일, 웹, 기본 앱 및 서비스와 같은 채널에 Headless 양식으로 핵심 구성 요소 기반 적응형 Forms을 제공할 수 있습니다.


## 적응형 Forms 핵심 구성 요소 및 Headless 적응형 Forms 활성화 {#enable-headless-forms}

AEM Forms as a Cloud Service 환경을 위한 적응형 Forms 핵심 구성 요소 및 Headless 적응형 Forms을 활성화하려면 나열된 순서로 다음 단계를 수행하십시오


![](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. AEM Forms as a Cloud Service Git 저장소 복제 {#clone-git-repository}

1. 에 로그인 [Cloud Manager](https://my.cloudmanager.adobe.com/) 조직 및 프로그램을 선택합니다.

1. 다음 위치로 이동 **파이프라인** 의 카드 **프로그램 개요** 페이지를 클릭하고 **저장소 정보 액세스** 버튼을 클릭하여 Git 저장소에 액세스하고 관리합니다. 이 페이지에는 다음 정보가 포함되어 있습니다.

   * Cloud Manager Git 저장소의 URL.
   * Git 저장소(사용자 이름 및 암호) Git 사용자 이름의 자격 증명.

   클릭 **암호 생성** 암호를 보거나 생성합니다.

1. 로컬 컴퓨터에서 터미널 또는 명령 프롬프트를 열고 다음 명령을 실행합니다.

   ```Shell
   git clone [Git Repository URL]
   ```

   메시지가 표시되면 자격 증명을 제공합니다. 저장소가 로컬 컴퓨터에 복제됩니다.


## 2. Git 저장소에 적응형 Forms 핵심 구성 요소 종속성 추가 {#add-adaptive-forms-core-components-dependencies}

1. 일반 텍스트 코드 편집기에서 Git 저장소 폴더를 엽니다. 예: VS 코드.
1. 를 엽니다. `[AEM Repository Folder]\pom.xml` 편집할 파일입니다.
1. 버전 바꾸기 `core.forms.components.version`, `core.forms.components.af.version` 및 `core.wcm.components.version` 에 지정된 버전을 가진 구성 요소 [핵심 구성 요소 설명서](https://github.com/adobe/aem-core-forms-components). 구성 요소가 존재하지 않는 경우 이러한 구성 요소를 추가합니다.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![최신 버전의 Forms 핵심 구성 요소 언급](/help/forms/assets/latest-forms-component-version.png)

1. 의 종속성 섹션에서 다음을 수행합니다 `[AEM Repository Folder]\pom.xml` 파일을 추가하고 다음 종속성을 추가한 다음 파일을 저장합니다.

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

1. 를 엽니다. `[AEM Repository Folder]/all/pom.xml` 편집할 파일입니다. 에 다음 종속성을 추가합니다. `<embeddeds>` 섹션을 만들고 파일을 저장합니다.

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
   >  바꾸기 `${appId}` appId와 함께 사용할 수 있습니다.
   >
   >  를 찾으려면 `${appId}`, `[AEM Repository Folder]/all/pom.xml` 파일, 검색 `-packages/application/install` 용어. 다음 앞에 있는 텍스트 `-packages/application/install` 용어: `${appId}`. 예를 들어 다음 코드는 `myheadlessform` 은(는) `${appId}`.
   >
   >   
   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. 다음에서 `<dependencies>` 의 섹션 `[AEM Repository Folder]/all/pom.xml` 파일을 추가하고 다음 종속성을 추가한 다음 파일을 저장합니다.

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

1. 를 엽니다. `[AEM Repository Folder]/ui.apps/pom.xml` 편집할 수 있습니다. 추가 `af-core bundle` 종속성을 설정하고 파일을 저장합니다.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >다음 적응형 Forms 핵심 구성 요소 아티팩트가 프로젝트에 포함되지 않았는지 확인합니다.
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

* [로컬 개발 환경에 업데이트된 코드를 빌드하고 배포합니다(AEM as a Cloud Service SDK)](#core-components-on-aem-forms-local-sdk)

* [AEM Forms as a Cloud Service 환경에서 업데이트된 코드 빌드 및 배포](#core-components-on-aem-forms-cs)

### 로컬 개발 환경에 업데이트된 코드 빌드 및 배포 {#core-components-on-aem-forms-local-sdk}

1. 명령 프롬프트 또는 터미널을 엽니다.

1. Git 저장소 프로젝트의 루트 디렉토리로 이동합니다.

1. 다음 명령을 실행하여 환경에 대한 패키지를 빌드합니다.

   ```Shell
       mvn clean install
   ```



   패키지가 성공적으로 빌드되면 다음에서 찾을 수 있습니다. [Git 저장소 폴더]\all\target\[appid].all-[버전].zip

1. 사용 [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=ko) 를 배포하려면 [AEM Archetype 프로젝트 폴더]\all\target\[appid].all-[버전]로컬 개발 환경의 .zip 패키지


### AEM Forms as a Cloud Service 환경에서 업데이트된 코드 빌드 및 배포 {#core-components-on-aem-forms-cs}

1. 터미널 또는 명령 프롬프트를 엽니다.
1. 다음으로 이동 `[AEM Repository Folder]` 다음 명령을 나열된 순서로 실행합니다

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. 파일이 Git 저장소에 커밋되면 [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

   파이프라인 실행이 성공하면 해당 환경에 대해 적응형 Forms 핵심 구성 요소가 활성화됩니다. 또한 적응형 Forms(핵심 구성 요소) 템플릿과 Canvas 3.0 테마가 Forms as a Cloud Service 환경에 추가되어 적응형 Forms 기반의 핵심 구성 요소를 사용자 정의하고 만들 수 있는 선택 사항을 제공합니다.


## FAQ {#faq}

### 핵심 구성 요소란 무엇입니까? {#core-components}

다음 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko) 는 AEM에서 개발 시간을 단축하고 웹 사이트의 유지 관리 비용을 절감할 수 있는 표준화된 웹 컨텐츠 관리(WCM) 구성 요소입니다.

### 핵심 구성 요소 활성화에 모든 기능이 추가됩니까? {#core-components-capabilities}

환경에 대한 적응형 Forms 핵심 구성 요소가 활성화되면 적응형 양식 템플릿 기반의 빈 핵심 구성 요소 및 Canvas 3.0 테마가 환경에 추가됩니다. 환경에 맞는 적응형 Forms 핵심 구성 요소를 활성화한 후 다음을 수행할 수 있습니다.

* [적응형 Forms 기반의 핵심 구성 요소 만들기](/help/forms/creating-adaptive-form-core-components.md).
* [적응형 양식 템플릿을 기반으로 핵심 구성 요소 만들기](/help/forms/template-editor.md).
* [적응형 양식 템플릿을 기반으로 핵심 구성 요소에 대한 사용자 지정 테마 만들기](/help/forms/using-themes-in-core-components.md).
* [모바일, 웹, 기본 앱 및 양식의 Headless 표시가 필요한 서비스와 같은 채널에 핵심 구성 요소 기반 적응형 양식의 JSON 표시를 제공합니다](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html).

### 내 환경에 대해 적응형 Forms 핵심 구성 요소가 활성화됩니까? {#enable-components}

적응형 Forms 핵심 구성 요소가 환경에 대해 활성화되어 있는지 확인하려면 다음을 수행하십시오.

1. [AEM Forms as a Cloud Service 저장소 복제](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. 를 엽니다. `[AEM Repository Folder]/all/pom.xml` AEM Forms Cloud Service Git 저장소의 파일입니다.

1. 다음 종속성을 검색합니다.

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![all/pom.xml에서 core-forms-components-af-core 아티팩트 찾기](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   종속성이 있는 경우 환경에 대해 적응형 Forms 핵심 구성 요소가 활성화됩니다.

