---
title: '[!DNL Adobe Experience Manager] as a Cloud Service 사전 릴리스 채널'
description: '[!DNL Adobe Experience Manager] as a Cloud Service 사전 릴리스 채널'
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: 6cd454eaf70400f3507bc565237567cace66991f
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 사전 릴리스 채널 {#prerelease-channel}


## 소개 {#introduction}

[!DNL Adobe Experience Manager] as a Cloud Service은 의 일정에 따라 월별 케이던스에 새로운 기능을 제공합니다 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=en#aem-as-cloud-service). 다음 달에 출시될 예정인 기능을 잘 알고 있으려면 표준 프로그램 개발 환경 또는 샌드박스 프로그램 환경에서 적절히 구성하여 사전 릴리스 채널에 가입할 수 있습니다. 고객은 사이트 콘솔의 변경 사항을 미리 볼 수 있을 뿐만 아니라 새로운 사전 릴리스 API에 대한 빌드 코드를 미리 볼 수 있습니다.

지정된 월의 사전 릴리스 기능 목록은 [월별 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md).

>[!VIDEO](/help/release-notes/assets/prerelease-overview.mp4)

## 사전 릴리스를 활성화하는 방법 {#enable-prerelease}

시험판 기능은 다음과 같은 다양한 방법으로 경험할 수 있습니다.

* 클라우드 환경(표준 프로그램 개발 환경 또는 샌드박스 프로그램 환경 유형)
* 로컬 SDK

### 클라우드 환경 {#cloud-environments}

클라우드 개발 환경의 Sites 콘솔에서 새로운 기능과 프로젝트 사용자 지정 결과를 보려면 다음을 수행하십시오.

* 사용 [Cloud Manager API의 환경 변수 엔드포인트](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchEnvironmentVariables), 설정 **AEM_RELEASE_CHANNEL** 값에 대한 환경 변수 **사전 릴리스**.

```
PATCH /program/{programId}/environment/{environmentId}/variables
[
        {
                "name" : "AEM_RELEASE_CHANNEL",
                "value" : "prerelease",
                "type" : "string"
        }
]
```

Cloud Manager CLI는 [https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)
```aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease”```


환경을 일반(사전 릴리스가 아닌) 채널의 동작으로 복원하려는 경우 변수를 삭제하거나 다른 값으로 설정할 수 있습니다

* 또는 다음을 통해 환경 변수를 구성할 수도 있습니다 [Cloud Manager UI](/help/implementing/cloud-manager/environment-variables.md).

### 로컬 SDK {#local-sdk}

사전 릴리스에서 maven 프로젝트를 참조하도록 함으로써 사전 릴리스의 새 API에 대한 코드와 로컬 Quickstart SDK의 사이트 콘솔에서 새로운 기능을 볼 수 있습니다 `API Jar` Maven Central에 있습니다. 사전 릴리스 모드에서 일반 Quickstart SDK를 시작하여 로컬 컴퓨터에서 이러한 사전 릴리스 기능을 볼 수도 있습니다.

* 소프트웨어 배포 포털에서 SDK를 다운로드하고 다음에 설명된 대로 설치합니다. [AEM as a Cloud Service SDK 액세스](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).
* SDK 빠른 시작을 시작할 때 인수를 포함합니다 `-r prerelease`.
* 값은 입니다. *끈적끈적끈적한* 첫 번째 시작 시에만 선택할 수 있습니다. 명령줄 옵션을 변경하려면 SDK를 다시 설치합니다.

월별 기능 릴리스 간에 여러 AEM 유지 관리 릴리스가 있을 수 있으므로 이러한 새로운 SDK를 다운로드하고 maven 프로젝트에서 새 SDK API Jar 버전을 참조할 수 있습니다. 유지 관리 릴리스에는 사전 릴리스 기능이 추가되지는 않지만 버그 수정, 보안 수정 및 성능 개선 사항과 같은 더 작은 변경 사항이 포함될 수 있습니다.
Javadocs가 Maven Central에 게시됩니다.

사전 릴리스 SDK에 대해 빌드하려면

1. maven central에 게시된 개별 사전 릴리스 sdk api jar를 참조하도록 maven 프로젝트의 pom.xml을 수정합니다. 이 팩에는 사전 릴리스 기능을 위한 새로운 Java api가 포함되어 있으며 sdk api jar에 대한 종속성이 있습니다. 동일한 버전을 사용합니다.

   예를 들어, 다음은 일반적인 API Jar를 참조하는 상위 pom의 종속성 관리 섹션의 코드 조각입니다.

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

   그런 다음 모듈의 사용:

   ```
    <dependencies>
     <dependency>
         <groupId>com.adobe.aem</groupId>
         <artifactId>aem-sdk-api</artifactId>
     </dependency>
   ```

   사전 릴리스 SDK로 변경하려면 종속성을 변경하기만 하면 됩니다 `com.adobe.aem:aem-sdk-api` to `com.adobe.aem:aem-prerelease-sdk-api` 아래에 명시된 대로:

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

   평소대로 개별 프로젝트에서 종속성을 사용할 수 있습니다.

1. 로컬 서버에 배포
1. 로컬에서 예상대로 작동하므로 문제가 해결되면 개발 분기에 코드를 커밋하고 Cloud Manager 비프로덕션 파이프라인을 사용하여 사전 릴리스 채널에 가입한 환경에 배포합니다

>[!CAUTION]
> 
> 다음 `aem-prerelease-sdk-api` Stage 또는 Production에 배포할 때에는 artifactId를 사용하지 않아야 합니다. 프로덕션 파이프라인을 통해 배포할 때에는 항상 aem-sdk-api를 사용합니다. 마찬가지로 사전 릴리스 API를 참조하는 코드는 프로덕션 파이프라인을 통해 배포하지 않아야 합니다.

다음 [AEM CS SDK build Analyzer maven 플러그인 v1.0 이상](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) 은 종속성을 검사하여 프리릴리스 api가 프로젝트에서 사용되는지 확인합니다. 분석기가 찾으면 시험판 sdk api를 사용하여 프로젝트를 분석합니다.

## 고려 사항 {#considerations}

사전 릴리스 채널과 관련하여 몇 가지 주목할 사항이 있습니다.

* 다음 달 릴리스에서 롤아웃되는 일부 기능은 사전 릴리스 채널에 포함되지 않을 수 있습니다.
* 사전 릴리스의 기능은 엄격한 품질 보증을 통해 제공되며, 베타 품질보다는 기능 완료를 목표로 합니다. 문제가 발견되면 일반 AEM 릴리스의 기능에 있는 버그가 의심되는 경우처럼 보고합니다.
* 사전 릴리스 채널에 대한 환경이 구성되어 있는지 확인하려면 AEM 콘솔의 **정보** 페이지를 방문하여 AEM 버전 번호가 *사전 릴리스* 접미사 ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE```.

![정보](/help/release-notes/assets/about.png)
