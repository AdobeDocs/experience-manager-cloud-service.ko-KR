---
title: Cloud Service으로 AEM용 AEM Commerce 개발
description: AEM 프로젝트 원형형을 사용하여 상거래 기반의 AEM 프로젝트를 생성하는 방법을 살펴볼 수 있습니다. AEM을 Cloud Service SDK로 사용하여 프로젝트를 구축 및 로컬 개발 환경에 배포하는 방법을 살펴봅니다.
topics: Commerce, Development
feature: 전자 상거래 통합 프레임워크
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
translation-type: tm+mt
source-git-commit: 97574c964e757ffa4d108340f6a4d1819050d79a
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 8%

---

# AEM Commerce for AEM을 Cloud Service {#develop}으로 개발

Cloud Service으로 AEM용 CIF(Commerce Integration Framework)를 기반으로 하는 AEM Commerce 프로젝트를 개발하는 과정도 Cloud Service의 다른 AEM 프로젝트와 같은 규칙과 우수 사례를 따릅니다. 다음 사항을 먼저 검토하십시오.

- [AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [AEM as a Cloud Service 개발 지침](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Cloud Service SDK {#local}로 AEM을 사용하는 로컬 개발

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

CIF 프로젝트 작업을 수행하려면 로컬 개발 환경을 사용하는 것이 좋습니다. AEM용으로 제공되는 CIF Add-On을 Cloud Service으로 로컬 개발에도 사용할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 다운로드할 수 있습니다.

CIF Add-On은 Sling 기능 아카이브로 제공됩니다. Software Distribution portal에서 사용할 수 있는 zip 파일에는 두 개의 Sling Feature Archive 파일(AEM 작성자용 파일, AEM 게시 인스턴스용 파일) 1개가 있습니다.

**Cloud Service으로 AEM을 처음 사용하시나요?** AEM [를 Cloud Service SDK로 사용하여 로컬 개발 환경을 설정하는 방법에 대한 자세한 가이드를 확인하십시오](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### 필수 소프트웨어

다음은 로컬에 설치해야 합니다.

- [Cloud Service SDK로 AEM 사용](https://docs.adobe.com/content/help/en/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 이상)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### CIF Add-on 액세스

CIF Add-on은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 zip 파일로 다운로드할 수 있습니다. zip 파일에는 CIF Add-on이 **Sling 기능 아카이브**&#x200B;로 포함되어 있으며 AEM 패키지가 아닙니다. SDK 목록에 대한 액세스는 Cloud Service 라이선스로 AEM이 있는 경우에만 제한됩니다.

>[!TIP]
>
>항상 최신 CIF Add-On 버전을 사용하십시오.

### 로컬 설정

Cloud Service SDK로 AEM을 사용하는 로컬 CIF Add-on 개발의 경우 다음 단계를 수행하십시오.

1. 최신 AEM을 Cloud Service SDK로 다운로드
1. AEM .jar의 압축을 풀고 `crx-quickstart` 폴더를 만듭니다. 다음을 실행합니다.

   ```bash
   java -jar <jar name> -unpack
   ```

1. `crx-quickstart/install` 폴더 만들기
1. CIF Add-on의 올바른 Sling 기능 아카이브 파일을 `crx-quickstart/install` 폴더에 복사합니다.

   CIF Add-on zip 파일에는 두 개의 Sling 기능 아카이브 `.far` 파일이 포함되어 있습니다. 로컬 AEM을 Cloud Service SDK로 실행하는 방법에 따라 AEM 작성자 또는 AEM 게시에 올바른 SDK를 사용해야 합니다.

1. Magento GraphQL 끝점을 포함하는 `COMMERCE_ENDPOINT`이라는 이름의 로컬 OS 환경 변수를 만듭니다.

   Mac OSX 예:

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   예제 Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   이 변수는 AEM에서 상거래 시스템에 연결하는 데 사용됩니다. 또한 CIF Add-on에는 로컬 역방향 프록시가 포함되어 Commerce GraphQL 끝점을 로컬로 사용할 수 있습니다. CIF 작성 도구(제품 콘솔 및 피커)와 직접 GraphQL 호출을 수행하는 CIF 클라이언트측 구성 요소에 사용됩니다.

   이 변수는 Cloud Service 환경으로서 AEM용으로 설정해야 합니다. 변수에 대한 자세한 내용은 [AEM용 OSGi를 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development)로 구성을 참조하십시오.

1. (선택 사항) 단계 카탈로그 기능을 사용하려면 Magento 인스턴스에 대한 통합 토큰을 만들어야 합니다. 토큰을 만들려면 [시작하기](./getting-started.md#staging)의 단계를 따르십시오.

   이름이 `COMMERCE_AUTH_HEADER`인 OSGi 암호를 다음 값으로 설정합니다.

   ```xml
   Authorization: Bearer <Access Token>
   ```

   비밀에 대한 자세한 내용은 [AEM용 OSGi를 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development)로 구성을 참조하십시오.

1. Cloud Service SDK로 AEM 시작

>[!NOTE]
>
>5단계에서 환경 변수가 설정된 동일한 터미널 창에서 AEM을 Cloud Service SDK로 시작해야 합니다. 별도의 터미널 창에서 시작하거나 .jar 파일을 두 번 클릭하여 환경 변수가 표시되는지 확인합니다.

OSGI 콘솔을 통해 설정을 확인합니다. `http://localhost:4502/system/console/osgi-installer`. 목록에 피쳐 모델 파일에 정의된 대로 CIF 추가 기능 관련 번들, 컨텐츠 패키지 및 OSGI 구성이 포함되어야 합니다.

## 프로젝트 설정 {#project}

Cloud Service으로 AEM용 CIF 프로젝트를 부트스트래핑하는 방법은 두 가지가 있습니다.

### AEM 프로젝트 원형 사용

[AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype)은 CIF로 시작하기 위해 미리 구성된 프로젝트를 부트스트래핑하는 주 도구입니다. CIF 핵심 구성 요소 및 모든 필수 구성을 하나의 추가 옵션을 사용하여 생성된 프로젝트에 포함할 수 있습니다.

>[!TIP]
>
>[AEM Project Tranype 24 이상을 사용하여 프로젝트를 생성합니다.](https://github.com/adobe/aem-project-archetype/releases)

AEM 프로젝트를 생성하는 방법은 AEM 프로젝트 원형 [사용 지침](https://github.com/adobe/aem-project-archetype#usage)을 참조하십시오. 프로젝트에 CIF를 포함하려면 `includeCommerce` 옵션을 사용합니다.

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

CIF 핵심 구성 요소는 제공된 `all` 패키지를 포함하거나 CIF 컨텐츠 패키지 및 관련 OSGI 번들을 사용하여 개별적으로 프로젝트에 사용할 수 있습니다. 프로젝트에 CIF 핵심 구성 요소를 수동으로 추가하려면 다음 종속성을 사용합니다.

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
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

CIF 프로젝트를 시작하는 두 번째 옵션은 [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)를 복제하여 사용하는 것입니다. AEM Venia Reference Store는 AEM용 CIF Core Components의 사용을 보여 주는 샘플 참조 스토어프런트 응용 프로그램입니다. 이 프레임워크는 모범 사례 세트 및 고유한 기능을 개발할 수 있는 잠재적 시작점으로 고안되었습니다.

Venia Reference Store를 시작하려면 Git 리포지토리를 복제하고 필요에 따라 프로젝트를 사용자 정의하기만 하면 됩니다.

>[!NOTE]
>
>Venia Reference Store 프로젝트에는 Cloud Service 및 AEM 6.5의 AEM용 빌드 프로필이 2개 포함되어 있습니다. [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md)에서 해당 프로필이 어떻게 사용되는지 확인하십시오.

## 추가 리소스

- [AEM 프로젝트 전형](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
