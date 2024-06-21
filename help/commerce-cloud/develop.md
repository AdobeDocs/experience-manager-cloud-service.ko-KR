---
title: AEM as a Cloud Service용 AEM Commerce 개발
description: AEM Project Archetype을 사용하여 상거래 지원 AEM 프로젝트를 생성하는 방법을 알아봅니다. AEM as a Cloud Service SDK를 사용하여 프로젝트를 빌드하고 로컬 개발 환경에 배포하는 방법에 대해 알아봅니다.
topics: Commerce, Development
feature: Commerce Integration Framework
version: Cloud Service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 4%

---

# AEM as a Cloud Service용 AEM Commerce 개발 {#develop}

AEM용 CIF(Commerce integration framework)를 기반으로 AEM Commerce 프로젝트를 개발하는 경우 as a Cloud Service의 다른 AEM AEM as a Cloud Service 프로젝트와 동일한 규칙과 모범 사례를 따릅니다. 먼저 다음을 검토하십시오.

- [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [AEM as a Cloud Service 개발 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)

## AEM as a Cloud Service SDK를 사용한 로컬 개발 {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

CIF 프로젝트에서 작업하려면 로컬 개발 환경을 사용하는 것이 좋습니다. as a Cloud Service으로 제공되는 CIF AEM 추가 기능은 로컬 개발에도 사용할 수 있습니다. 다음에서 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

CIF 추가 기능은 Sling 기능 아카이브로 제공됩니다. 소프트웨어 배포 포털에서 사용할 수 있는 zip 파일에는 두 개의 Sling 기능 아카이브 파일이 포함되어 있습니다. 하나는 AEM 작성자용 이고 다른 하나는 AEM 게시 인스턴스용 입니다.

**AEM을 as a Cloud Service으로 처음 사용하십니까?** 체크아웃 [AEM as a Cloud Service SDK를 사용한 로컬 개발 환경 설정에 대한 자세한 안내서](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=ko-KR).

### 필수 소프트웨어

다음은 로컬에 설치해야 합니다.

- [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java™ 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 이상)
- [Node.js v10+](https://nodejs.org/en)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### CIF 추가 기능 액세스

CIF 추가 기능은에서 zip 파일로 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). zip 파일에는 CIF 추가 기능이 다음과 같이 포함되어 있습니다. **Sling 기능 아카이브**: AEM 패키지가 아닙니다. SDK 목록은 AEM as a Cloud Service 라이선스로 액세스할 수 있습니다.

>[!TIP]
>
>항상 최신 CIF 추가 기능 버전을 사용하십시오.

### 로컬 설정

AEM as a Cloud Service SDK를 사용한 로컬 CIF 추가 기능 개발의 경우 다음 단계를 따르십시오.

1. 최신 AEM as a Cloud Service SDK 받기
1. AEM .jar의 압축을 풀고 `crx-quickstart` 폴더, 실행:

   ```bash
   java -jar <jar name> -unpack
   ```

1. 만들기 `crx-quickstart/install` 폴더
1. CIF 추가 기능의 올바른 Sling 기능 아카이브 파일을 `crx-quickstart/install` 폴더를 삭제합니다.

   CIF 추가 기능 zip 파일에는 두 개의 Sling 기능 아카이브가 포함되어 있습니다 `.far` 파일. 로컬 AEM as a Cloud Service SDK를 실행하는 방법에 따라 AEM Author 또는 AEM Publish에 대해 올바른 작성자를 사용해야 합니다.

1. 이름이 인 로컬 OS 환경 변수 만들기 `COMMERCE_ENDPOINT` Adobe Commerce GraphQL 끝점 유지 중

   macOS X 예:

   ```bash
   export COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   예제 Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   이 변수는 AEM에서 상거래 시스템에 연결하는 데 사용됩니다. 또한 CIF 추가 기능에는 Commerce GraphQL 끝점을 로컬에서 사용할 수 있도록 하는 로컬 역방향 프록시가 포함되어 있습니다. 이 프록시는 CIF 작성 도구(제품 콘솔 및 선택기) 및 직접 GraphQL 호출을 수행하는 CIF 클라이언트측 구성 요소에 사용됩니다.

   이 변수는 AEM as a Cloud Service 환경에도 설정해야 합니다. 변수에 대한 자세한 내용은 [AEM에 대한 OSGi 구성 as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html#local-development).

1. (선택 사항) 스테이징된 카탈로그 기능을 활성화하려면 Adobe Commerce 인스턴스에 대한 통합 토큰을 만들어야 합니다. 다음 단계를 수행합니다. [시작](./getting-started.md#staging) 토큰을 만듭니다.

   이름으로 OSGi 암호 설정 `COMMERCE_AUTH_HEADER` 다음 값으로:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   비밀에 대한 자세한 내용은 [AEM에 대한 OSGi 구성 as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html#local-development).

1. AEM as a Cloud Service SDK 시작

>[!NOTE]
>
>5단계에서 환경 변수가 설정된 동일한 터미널 창에서 AEM as a Cloud Service SDK를 시작해야 합니다. 별도의 터미널 창에서 시작하거나 .jar 파일을 두 번 클릭하여 시작하는 경우 환경 변수가 표시되는지 확인합니다.

OSGI 콘솔을 통해 설정을 확인합니다. `http://localhost:4502/system/console/osgi-installer`. 목록에는 기능 모델 파일에 정의된 대로 CIF 추가 기능 관련 번들, 콘텐츠 패키지 및 OSGI 구성이 포함되어야 합니다.

## 프로젝트 설정 {#project}

CIF AEM 프로젝트를 as a Cloud Service으로 Bootstrap 하는 방법에는 두 가지가 있습니다.

### AEM Project Archetype 사용

다음 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype) 은 CIF을 시작하기 위해 사전 구성된 프로젝트를 Bootstrap 하는 기본 도구입니다. CIF 코어 구성 요소 및 필요한 모든 구성은 하나의 추가 옵션과 함께 생성된 프로젝트에 포함될 수 있습니다.

>[!TIP]
>
>항상 최신 버전의 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype/releases) 프로젝트를 생성할 수 있습니다.

AEM 프로젝트 원형 을 참조하십시오. [사용 지침](https://github.com/adobe/aem-project-archetype#usage) AEM 프로젝트를 생성하는 방법에 대해 설명합니다. CIF을 프로젝트에 포함하려면 `includeCommerce` 옵션을 선택합니다.

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

CIF 핵심 구성 요소는 제공된 을 포함하여 모든 프로젝트에서 사용할 수 있습니다 `all` CIF 콘텐츠 패키지 및 관련 OSGI 번들을 사용하여 개별적으로 또는 패키징합니다. 프로젝트에 CIF 핵심 구성 요소를 수동으로 추가하려면 다음 종속성을 사용하십시오.

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

CIF 프로젝트를 시작하는 두 번째 옵션은 를 복제하여 사용하는 것입니다. [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia). AEM Venia 참조 저장소는 AEM용 CIF 핵심 구성 요소의 사용을 보여 주는 샘플 참조 상점 응용 프로그램입니다. 모범 사례 세트 및 고유한 기능을 개발하기 위한 잠재적인 시작점으로 설계되었습니다.

Venia 참조 저장소를 시작하려면 Git 저장소를 복제하고 필요에 따라 프로젝트 맞춤화를 시작합니다.

>[!NOTE]
>
>Venia 참조 스토어 프로젝트에는 AEM as a Cloud Service과 AEM 6.5용 빌드 프로필이 두 개 포함되어 있습니다. 확인 [프로젝트 readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) 어떻게 쓰이는지 보실 수 있습니다.

## 추가 리소스

- [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)
- [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
- [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
