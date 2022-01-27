---
title: AEM as a Cloud Service용 AEM Commerce 개발
description: AEM 프로젝트 원형 을 사용하여 상거래 지원 AEM 프로젝트를 생성하는 방법을 알아봅니다. AEM as a Cloud Service SDK를 사용하여 프로젝트를 빌드 및 로컬 개발 환경에 배포하는 방법을 알아봅니다.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
source-git-commit: 3778ed83453ab3e1e01e662a43d4f86988da1668
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# AEM as a Cloud Service용 AEM Commerce 개발 {#develop}

AEM as a Cloud Service CIF(Commerce Integration Framework)를 기반으로 하는 AEM Commerce Projects를 개발해도 AEM의 다른 AEM 프로젝트처럼 동일한 규칙 및 우수 사례를 따릅니다. 다음 사항을 먼저 검토하십시오.

- [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [AEM as a Cloud Service 개발 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## AEM as a Cloud Service SDK를 사용한 로컬 개발 {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

CIF 프로젝트에서 작업하려면 로컬 개발 환경을 사용하는 것이 좋습니다. AEM as a Cloud Service에 제공된 CIF 추가 기능 또한 로컬 개발에 사용할 수 있습니다. 에서 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

CIF 추가 기능은 Sling 기능 아카이브로 제공됩니다. 소프트웨어 배포 포털에서 사용할 수 있는 zip 파일에는 AEM 작성자 및 AEM 게시 인스턴스용, 이렇게 두 개의 Sling 기능 아카이브 파일이 포함되어 있습니다.

**AEM as a Cloud Service을 처음 사용하십니까?** 체크 아웃 [AEM as a Cloud Service SDK를 사용하여 로컬 개발 환경을 설정하는 방법에 대한 자세한 안내서입니다](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### 필수 소프트웨어

로컬에 설치해야 합니다.

- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 이상)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### CIF 추가 기능 액세스

CIF 추가 기능은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). zip 파일에 CIF 추가 기능이 있습니다. **Sling 기능 아카이브**: AEM 패키지가 아닙니다. SDK 목록에 대한 액세스는 AEM as a Cloud Service 라이센스가 있는 것으로 제한됩니다.

>[!TIP]
>
>항상 최신 CIF 추가 기능 버전을 사용해야 합니다.

### 로컬 설정

AEM as a Cloud Service SDK를 사용한 로컬 CIF 추가 기능 개발에 대해서는 다음 단계를 수행합니다.

1. 최신 AEM as a Cloud Service SDK 가져오기
1. AEM .jar의 압축을 풀고 `crx-quickstart` 폴더, 실행:

   ```bash
   java -jar <jar name> -unpack
   ```

1. 만들기 `crx-quickstart/install` 폴더
1. CIF 추가 기능의 올바른 Sling Feature 아카이브 파일을 `crx-quickstart/install` 폴더를 입력합니다.

   CIF 추가 기능 zip 파일에는 두 개의 Sling 기능 아카이브가 포함되어 있습니다 `.far` 파일. 로컬 AEM as a Cloud Service SDK를 실행하는 방법에 따라 AEM 작성자 또는 AEM 게시용으로 올바른 SDK를 사용해야 합니다.

1. 이름이 인 로컬 OS 환경 변수를 만듭니다. `COMMERCE_ENDPOINT` Adobe Commerce GraphQL 종단점을 사용합니다.

   예제 Mac OSX:

   ```bash
   export COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   예제 Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   이 변수는 AEM에서 상거래 시스템에 연결하는 데 사용됩니다. 또한, CIF 추가 기능에는 Commerce GraphQL 끝점을 로컬에서 사용할 수 있도록 하는 로컬 역방향 프록시가 포함되어 있습니다. CIF 작성 도구(제품 콘솔 및 선택기)와 직접 GraphQL 호출을 수행하는 CIF 클라이언트측 구성 요소에 사용됩니다.

   이 변수는 AEM as a Cloud Service 환경에서도 설정해야 합니다. 변수에 대한 자세한 내용은 [AEM as a Cloud Service OSGi 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. (선택 사항) 준비된 카탈로그 기능을 활성화하려면 Adobe Commerce 인스턴스에 대한 통합 토큰을 만들어야 합니다. 다음 단계를 따르십시오. [시작하기](./getting-started.md#staging) 토큰을 만들려면

   이름으로 OSGi 암호 설정 `COMMERCE_AUTH_HEADER` 변환 후:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   비밀에 대한 자세한 내용은 [AEM as a Cloud Service OSGi 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. AEM as a Cloud Service SDK 시작

>[!NOTE]
>
>환경 변수가 5단계에서 설정되어 있는지 확인한 후 동일한 터미널 창에서 AEM as a Cloud Service SDK를 시작하십시오. 별도의 터미널 창에서 시작하거나 .jar 파일을 두 번 클릭하여 환경 변수가 표시되는지 확인합니다.

OSGI 콘솔을 통해 설정을 확인합니다. `http://localhost:4502/system/console/osgi-installer`. 이 목록에는 기능 모델 파일에 정의된 대로 CIF 추가 기능 관련 번들, 컨텐츠 패키지 및 OSGI 구성이 포함되어야 합니다.

## 프로젝트 설정 {#project}

AEM as a Cloud Service용으로 CIF 프로젝트를 부트스트랩하는 방법에는 두 가지가 있습니다.

### AEM 프로젝트 원형 사용

다음 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype) 는 CIF를 시작하기 위해 사전 구성된 프로젝트를 부트스트랩하는 기본 도구입니다. CIF 코어 구성 요소 및 모든 필수 구성은 한 개의 추가 옵션을 사용하여 생성된 프로젝트에 포함할 수 있습니다.

>[!TIP]
>
>항상 최신 버전의 를 사용하십시오 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype/releases) 프로젝트를 생성합니다.

AEM 프로젝트 원형 을 참조하십시오 [사용 지침](https://github.com/adobe/aem-project-archetype#usage) AEM 프로젝트를 생성하는 방법에 대해 설명합니다. 프로젝트에 CIF를 포함하려면 `includeCommerce` 선택 사항입니다.

예:

```bash
mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
 -D archetypeGroupId=com.adobe.aem \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=35 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D includeCommerce=y
```

CIF 코어 구성 요소 는 제공된 `all` CIF 컨텐츠 패키지 및 관련 OSGI 번들을 개별적으로 사용하거나 패키지로 사용할 수 있습니다. 프로젝트에 CIF 코어 구성 요소를 수동으로 추가하려면 다음 종속성을 사용하십시오.

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

### AEM Venia 참조 저장소 사용

CIF 프로젝트를 시작하는 두 번째 옵션은 를 복제하고 사용하는 것입니다 [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia). AEM Venia Reference Store는 AEM용 CIF 핵심 구성 요소의 사용을 보여 주는 샘플 참조 저장소 응용 프로그램입니다. 모범 사례 세트 및 사용자 고유의 기능을 개발하기 위한 잠재적 시작점으로 사용됩니다.

Venia 참조 스토어를 시작하려면 Git 리포지토리를 복제하고 필요에 따라 프로젝트 사용자 지정을 시작합니다.

>[!NOTE]
>
>Venia Reference Store 프로젝트에는 AEM as a Cloud Service 및 AEM 6.5용 빌드 프로필이 두 개 포함되어 있습니다. 다음을 확인하십시오. [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) 사용 방법을 확인합니다.

## 추가 리소스

- [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)
- [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
- [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
