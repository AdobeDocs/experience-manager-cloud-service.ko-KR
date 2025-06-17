---
title: Adobe Experience Manager as a Cloud Service 프리릴리스 채널
description: 프리릴리스 채널을 사용하여 AEM as a Cloud Service에 대한 예정된 기능을 미리 보는 방법에 대해 알아보십시오.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
feature: Release Information
role: Admin
source-git-commit: 36da09746f02daad82875329b0aa53ee4eb7c074
workflow-type: ht
source-wordcount: '889'
ht-degree: 100%

---


# Adobe Experience Manager as a Cloud Service 프리릴리스 채널 {#prerelease-channel}

프리릴리스 채널을 사용하여 AEM as a Cloud Service에 대한 예정된 기능을 미리 보는 방법에 대해 알아보십시오.

## 소개 {#introduction}

Adobe Experience Manager as a Cloud Service는 정기적으로 새로운 기능을 제공합니다. 지정된 기능 릴리스에 대한 새로운 기능 및 출시 예정 기능 목록은 [릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)에 게시됩니다.

출시 예정 기능은 일반적으로 다음 두 가지 방법 중 하나로 제공됩니다.

* 얼리 어답터 프로그램의 일부
* 프리릴리스 채널의 일부

이 문서는 프리릴리스 채널을 활성화하는 방법을 설명합니다. 프리릴리스 채널은 향후 AEM의 기능 릴리스에 도입될 초기 기능에 액세스할 수 있습니다. 이를 통해 향후 릴리스에 앞서 새로운 기능을 검증하고 도입 계획을 세울 수 있습니다. AEM 릴리스 일정에 대한 자세한 내용은 [Adobe Experience Manager (AEM) as a Cloud Service 릴리스 정보](/help/release-notes/home.md)를 참조하십시오.

## 프리릴리스 채널을 활성화하여 출시 예정 기능 액세스 및 사용 {#enable-prerelease}

프리릴리스 채널은 모든 개발 또는 샌드박스 환경에서 활성화할 수 있습니다. 스테이징 또는 프로덕션 환경에서는 프리릴리스 채널을 활성화할 수 없습니다.

프리릴리스 채널은 두 가지 방법으로 접속할 수 있습니다.

* [클라우드 환경](#cloud-environments)
* [로컬 SDK](#local-sdk)

### 클라우드 환경 {#cloud-environments}

클라우드 환경을 업데이트하여 프리릴리스 채널을 사용하려면 새 환경 변수를 추가해야 합니다. Cloud Manager UI를 사용하거나 CLI를 통해 이 작업을 수행할 수 있습니다.

#### UI를 사용하여 환경 변수 추가 {#add-with-ui}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 프리릴리스 채널을 활성화할 프로그램으로 이동합니다.

1. 프리릴리스 채널을 활성화하고자 하는 환경을 선택한 다음 **프로그램** > **환경** > **환경 구성**&#x200B;을 통해 해당 구성에 액세스합니다.

1. 새 [환경 변수](/help/implementing/cloud-manager/environment-variables.md) 추가

   | 이름 | 값 | 적용된 서비스 | 유형 |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | 모두 | 변수 |

1. 변경 내용을 저장하면 환경은 프리릴리스 채널이 활성화되며 새로 고침됩니다.

   ![새 환경 변수](assets/env-configuration-prerelease.png)

#### CLI를 사용하여 환경 변수 추가 {#add-with-cli}

Cloud Manager API 및 CLI를 사용하여 환경 변수를 업데이트할 수도 있습니다.

* [Cloud Manager API의 환경 변수 엔드포인트](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables)를 사용하여 `AEM_RELEASE_CHANNEL` 환경 변수를 `prerelease` 값으로 설정합니다.

  ```text
  PATCH /program/{programId}/environment/{environmentId}/variables
  [
          {
                  "name" : "AEM_RELEASE_CHANNEL",
                  "value" : "prerelease",
                  "type" : "string"
          }
  ]
  ```

* [Cloud Manager CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)를 사용할 수도 있습니다.

  ```shell
  aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL "prerelease
  ```

환경을 표준 동작(프리릴리스 채널이 아닌 경우)으로 복원하기 위해 변수를 삭제할 수 있습니다.

### 로컬 SDK {#local-sdk}

Maven 프로젝트에서 Maven Central에 위치한 프리릴리스 채널 `API Jar`를 참조하도록 구성하여 로컬 SDK 빠른 시작에 있는 프리릴리스 채널의 출시 예정 기능 및 새 API에 대한 코드를 액세스할 수 있습니다. 또한 프리릴리스 모드에서 일반 SDK 빠른 시작을 시작하여 이들 프리릴리스 채널을 로컬 개발 환경에서도 액세스할 수 있습니다.

#### 프리릴리스 모드에서 SDK 빠른 시작 {#prerelease-mode}

1. [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)에 액세스에 설명된 바와 같이 소프트웨어 배포에서 SDK를 다운로드한 다음 설치합니다.
1. SDK 빠른 시작을 실행하면 인수 `-r prerelease`를 포함합니다.

값은 고정되므로 처음 시작할 때만 선택할 수 있습니다. SDK를 다시 설치하여 명령줄 옵션을 변경합니다.

월별 기능 릴리스 간에는 여러 AEM 유지 관리 릴리스가 있으므로 이들 새 SDK를 다운로드하고 Maven 프로젝트에 새 SDK API Jar 버전을 참조할 수 있습니다. 유지 관리 릴리스에는 프리릴리스 기능이 추가되지 않지만 버그 수정, 보안 수정 및 성능 개선과 같은 사소한 변경 내용이 포함될 수 있습니다.
JavaDoc은 Maven Central에 게시됩니다.

#### 프리릴리스 SDK에 대해 구축 {#build-sdk}

1. Maven 프로젝트의 `pom.xml`을 수정하고 Maven Central에 게시되는 개별 프리릴리스 SDK API Jar를 참조합니다. 여기에는 프리릴리스 기능에 대한 새 Java API가 포함되어 있으며 이는 SDK API Jar에 종속됩니다. 동일한 버전을 사용합니다.

   예를 들어 상위 pom의 종속성 관리 섹션에 일반 API Jar를 참조하는 스니펫이 있다고 가정해 보겠습니다.

   ```
   <dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
        </dependency>
   ```

   모듈의 사용은 다음과 같습니다.

   ```
    <dependencies>
     <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-sdk-api</artifactId>
     </dependency>
   ```

   프리릴리스 SDK를 변경하려면 아래 설명처럼 `com.adobe.aem:aem-sdk-api`에서 `com.adobe.aem:aem-prerelease-sdk-api`로 종속성을 변경하기만 하면 됩니다.

   ```
   <dependencyManagement>
    <dependencies>
      <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-prerelease-sdk-api</artifactId>
            <version>${aem.sdk.api}</version>
            <scope>provided</scope>
      </dependency>
   <dependencies>
      <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-prerelease-sdk-api</artifactId>
      </dependency>
   ```

   평소와 같이 개별 프로젝트에서는 종속성을 사용할 수 있습니다.

1. 로컬 서버에 배포하십시오.

1. 로컬에서 의도한 대로 작동하는 경우 개발 분기에 코드를 커밋하고 Cloud Manager 비프로덕션 파이프라인을 사용하여 [프리릴리스 채널을 사용하는 환경](#cloud-environments)에 배포합니다.

>[!CAUTION]
> 
> 스테이지 및 프로덕션에 배포 시 `aem-prerelease-sdk-api` artifactId를 사용해야 합니다. 프로덕션 파이프라인을 통해 배포 시 항상 `aem-sdk-api`를 사용하십시오. 마찬가지로 프리릴리스 API를 참조하는 코드는 프로덕션 파이프라인을 통해 배포할 수 없습니다.

[AEM CS SDK Build Analyzer Maven 플러그인 v1.0 이상](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing)은 종속성 검사를 통해 프로젝트에서 프리릴리스 API가 사용되는지 감지합니다. 분석기가 사용을 감지하면 프리릴리스 SDK API를 사용하여 프로젝트를 분석합니다.

## 고려 사항 {#considerations}

다음은 프리릴리스 채널 사용 시 알아 두어야 할 몇 가지 항목입니다.

* 프리릴리스 채널에 다음 릴리스에서 출시될 모든 새로운 기능이 반드시 포함되는 것은 아닙니다.
* 프리릴리스에 있는 기능은 엄격한 품질 보증을 통해 출시되며 Beta 품질이 아닌 완전한 품질을 갖춘 기능을 제공하기 위해 설계되었습니다. 문제가 발생하는 경우 정규 AEM 릴리스의 기능에서 버그가 의심되는 경우와 마찬가지로 보고하십시오.
* 환경이 프리릴리스 채널에 대해 구성되는지 파악하려면 AEM 콘솔의 **정보** 페이지로 이동하여 AEM 버전 번호에 `Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE`와 같이 `PRERELEASE` 접미사가 포함되는지 확인하십시오.

![정보](/help/release-notes/assets/about.png)
