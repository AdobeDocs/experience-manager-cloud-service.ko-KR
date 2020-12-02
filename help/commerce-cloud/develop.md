---
title: AEM용 AEM Commerce를 Cloud Service으로 개발
description: AEM 프로젝트 원형을 사용하여 커머스 지원 AEM 프로젝트를 생성하는 방법을 학습합니다. AEM을 Cloud Service SDK로 사용하여 프로젝트를 구축 및 로컬 개발 환경에 배포하는 방법을 알아봅니다.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
translation-type: tm+mt
source-git-commit: 6be2ed60f4e672b99a85b55f833b8ae2f1b952b0
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 8%

---


# AEM용 AEM Commerce를 Cloud Service {#develop}로 개발

Cloud Service으로 AEM용 CIF(Commerce Integration Framework)를 기반으로 하는 AEM 커머스 프로젝트를 개발하는 경우 Cloud Service의 다른 AEM 프로젝트와 같은 규칙과 모범 사례를 따르게 됩니다. 다음 사항을 먼저 검토하십시오.

- [AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [AEM as a Cloud Service 개발 지침](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## AEM을 Cloud Service SDK {#local}로 사용하는 로컬 개발

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

CIF 프로젝트를 사용하는 경우 로컬 개발 환경을 사용하는 것이 좋습니다. Cloud Service 환경으로 AEM용으로 제공되는 CIF Add-On은 로컬 개발에도 사용할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 다운로드할 수 있습니다.

CIF Add-On은 Sling 기능 아카이브로 제공됩니다. 소프트웨어 배포 포털에서 사용할 수 있는 zip 파일에는 두 개의 Sling Feature 아카이브 파일이 포함되어 있습니다. 하나는 AEM 작성자용, 다른 하나는 AEM 게시 인스턴스용 파일입니다.

**AEM을 Cloud Service으로 처음 사용하는 경우** AEM [를 Cloud Service SDK로 사용하여 로컬 개발 환경을 설정하는 방법에 대한 자세한 가이드를 확인하십시오](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### 필수 소프트웨어

다음은 로컬에 설치해야 합니다.

- [CLOUD SERVICE SDK로 AEM 사용](https://docs.adobe.com/content/help/en/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 이상)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### CIF Add-on 액세스

CIF Add-on은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 zip 파일로 다운로드할 수 있습니다. zip 파일에는 CIF Add-on이 **Sling Feature Archive**&#x200B;으로 들어 있으며 AEM 패키지가 아닙니다. SDK 목록에 대한 액세스는 Cloud Service 라이선스로 AEM이 있는 경우에만 제한됩니다.

>[!TIP]
>
>항상 최신 CIF Add-On 버전을 사용하십시오.

### 로컬 설정

Cloud Service SDK로 AEM을 사용하는 로컬 CIF Add-on 개발의 경우 다음 단계를 수행하십시오.

1. 최신 AEM을 Cloud Service SDK로 다운로드
1. AEM .jar의 압축을 풀고 `crx-quickstart` 폴더를 만듭니다. 다음을 실행하십시오.

   ```bash
   java -jar <jar name> -unpack
   ```

1. `crx-quickstart/install` 폴더 만들기
1. CIF Add-on의 올바른 Sling 기능 아카이브 파일을 `crx-quickstart/install` 폴더에 복사합니다.

   CIF Add-on zip 파일에는 두 개의 Sling 기능 아카이브 `.far` 파일이 포함되어 있습니다. 로컬 AEM을 Cloud Service SDK로 실행하려는 방법에 따라 AEM 작성자 또는 AEM 게시물에 올바른을 사용해야 합니다.

1. Magento GraphQL 끝점을 포함하는 `COMMERCE_ENDPOINT`이라는 로컬 OS 환경 변수를 만듭니다.

   Mac OSX 예:

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   예제 Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   이 변수는 Cloud Service 환경으로서 AEM에 대해서도 설정해야 합니다.

   변수에 대한 자세한 내용은 [AEM용 OSGi를 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development)로 구성을 참조하십시오.

1. (선택 사항) 스테이지 카탈로그 기능을 활성화하려면 Magento 인스턴스에 대한 통합 토큰을 만들어야 합니다. 토큰을 만들려면 [시작하기](./getting-started.md#staging)의 단계를 따르십시오.

   이름이 `COMMERCE_AUTH_HEADER`인 OSGi 암호를 다음 값으로 설정합니다.

   ```xml
   Authorization: Bearer <Access Token>
   ```

   비밀에 대한 자세한 내용은 [AEM용 OSGi를 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development)로 구성을 참조하십시오.

1. AEM을 Cloud Service SDK로 시작

1. 로컬 GraphQL 프록시 서버 시작

   Magento GraphQL 끝점을 CIF Add-on 및 CIF 구성 요소에서 로컬로 사용할 수 있게 하려면 다음 명령을 사용합니다. GraphQL 끝점은 `http://localhost:3002/graphql`에서 사용할 수 있습니다.
Mac OSX 예:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial ''
   ```

   예제 Windows:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial '""'
   ```

   인수 `--proxyPartial`은(는) 빈 문자열을 받아야 합니다.

   GraphQL 쿼리 도구를 `http://localhost:3002/graphql`으로 가리키면 로컬 GraphQL 프록시를 테스트하고 몇 개의 쿼리를 테스트할 수 있습니다.

1. AEM SDK에 로그인하고 로컬 GraphQL 프록시 서버를 사용하도록 CIF를 구성합니다.

   CIF Cloud Service 구성(도구 > Cloud Services > CIF 구성)으로 이동합니다. 프로젝트에서 사용하는 구성의 속성 보기를 엽니다.

   `GraphQL Proxy Path` 속성에 대해 로컬 프록시 서버 끝점 `http://localhost:3002/graphql`을(를) 사용합니다. 구성을 저장합니다.

>[!NOTE]
>
>8단계의 구성을 프로젝트 보고서에 푸시하지 마십시오. 이 구성은 로컬 개발 설정에 대해서만 필요합니다. CLOUD SERVICE 환경으로 AEM은 온보드 중에 GraphQL 프록시로 이미 설정되어 있습니다.

OSGI 콘솔을 통해 설정을 확인합니다. `http://localhost:4502/system/console/osgi-installer` 목록에는 기능 모델 파일에 정의된 대로 CIF Add-on 관련 번들, 컨텐츠 패키지 및 OSGI 구성이 포함되어야 합니다.

## 프로젝트 설정 {#project}

AEM용 CIF 프로젝트를 Cloud Service으로 부트스트랩하는 방법은 두 가지가 있습니다.

### AEM 프로젝트 원형 사용

[AEM Project Tranype](https://github.com/adobe/aem-project-archetype)은 CIF를 시작하기 위해 미리 구성된 프로젝트를 부트스트래핑하는 주 도구입니다. CIF 핵심 구성 요소 및 모든 필수 구성은 하나의 추가 옵션을 사용하여 생성된 프로젝트에 포함시킬 수 있습니다.

>[!TIP]
>
>프로젝트를 생성하려면 [AEM Project 원형형 24 이상](https://github.com/adobe/aem-project-archetype/releases)을 사용하십시오.

AEM 프로젝트를 생성하는 방법은 AEM 프로젝트 원형 유형 [사용 지침](https://github.com/adobe/aem-project-archetype#usage)을 참조하십시오. 프로젝트에 CIF를 포함하려면 `includeCommerce` 옵션을 사용합니다.

예:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=24 \
 -D aemVersion=cloud \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

CIF 핵심 구성 요소는 제공된 `all` 패키지를 포함하거나 CIF 컨텐츠 패키지 및 관련 OSGI 번들을 개별적으로 사용하여 모든 프로젝트에서 사용할 수 있습니다. 프로젝트에 CIF 핵심 구성 요소를 수동으로 추가하려면 다음 종속성을 사용하십시오.

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### AEM Venia Reference Store 사용

CIF 프로젝트를 시작하는 두 번째 옵션은 [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)를 복제하여 사용하는 것입니다. AEM Venia Reference Store는 AEM용 CIF Core Components의 사용을 보여 주는 예제 참조 스토어프런트 응용 프로그램입니다. 사용자 고유의 기능을 개발할 수 있는 잠재적 시작점뿐만 아니라 모범 사례 세트로도 사용됩니다.

Venia Reference Store를 시작하려면 Git 리포지토리를 복제하고 필요에 따라 프로젝트 사용자 지정을 시작합니다.

>[!NOTE]
>
>Venia Reference Store 프로젝트에는 AEM용 Cloud Service 및 AEM 6.5용 빌드 프로필이 두 개 포함되어 있습니다. 이러한 프로필이 어떻게 사용되고 있는지 확인하려면 [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md)을 확인하십시오.

## 추가 리소스

- [AEM 프로젝트 전형](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
