---
title: Adobe Experience Manager as a Cloud Service 사전 릴리스 채널
description: 사전 릴리스 채널을 사용하여 AEM as a Cloud Service에 예정된 기능의 미리 보기를 가져오는 방법을 알아봅니다.
exl-id: cfc91699-0087-40fa-a76c-0e5e1e03a5bd
source-git-commit: 5b38e7d0ad97cdf8b7d0d5da79cf3d6721fa618a
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 21%

---


# Adobe Experience Manager as a Cloud Service 사전 릴리스 채널 {#prerelease-channel}

사전 릴리스 채널을 사용하여 AEM as a Cloud Service에 예정된 기능의 미리 보기를 가져오는 방법을 알아봅니다.

## 소개 {#introduction}

Adobe Experience Manager as a Cloud Service은 월간 케이던스에 새로운 기능을 제공합니다 [Experience Manager은 도로 맵을 출시합니다.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html#aem-as-cloud-service)

다음 달에 활성화되도록 예약된 기능을 잘 알고 있으려면 개발 환경 또는 샌드박스 환경을 구성하여 액세스할 수 있는 사전 릴리스 채널에 가입할 수 있습니다. AEM UI를 통해 액세스할 수 있는 변경 사항과 새로운 사전 릴리스 API에 대한 빌드 코드를 미리 볼 수 있습니다.

지정된 월의 사전 릴리스 기능 목록은 [월별 릴리스 노트입니다.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## AEM as a Cloud Service 릴리스 {#releases}

AEM as a Cloud Service에는 두 가지 유형의 릴리스가 있습니다.

* **월별 릴리스** AEM as a Cloud Service에 기능 및 기능 추가
* **중요 업데이트** 보안 업데이트, 성능 개선 사항 및 버그 수정을 추가하고 매일 적용됩니다.

이 패턴은 서비스를 중단하지 않고 지속적인 릴리스를 보장합니다.

사전 릴리스 채널을 사용하면 예정된 기능을 평가하고 자체 프로젝트에 대해 가능한 구현을 계획하기 위해 예정된 월별 릴리스에 예약된 기능을 미리 볼 수 있습니다. 이를 통해 다음 월별 릴리스를 미리 계획할 수 있습니다.

예를 들어 5월이고 사전 릴리스 채널을 구독하는 경우 예정된 6월 릴리스의 기능을 평가할 수 있습니다.

![사전 릴리스 케이던스 그래픽](assets/prerelease-cadence.png)

사전 릴리스는 예정된 AEMaaCS 기능에 1개월 동안 롤링을 제공하여 프로젝트 및 사용자 정의에 새로운 기능의 영향을 평가하고 이러한 기능, 테스트 및 사용자 트레이닝의 계획 롤아웃을 평가할 수 있는 시간을 제공합니다.

사전 릴리스 채널을 효과적으로 활용하려면 4단계가 필요합니다.

1. [일정 표시](#mark-calendars)
1. [릴리스 노트 검토](#release-notes)
1. [새로운 기능에 액세스하여 사용해 보십시오](#new-features)
1. [사용자 교육](#train-users)

## 일정 표시 {#mark-calendars}

월별 릴리스는 미리 예약되어 있으며 릴리스 날짜는 다음에 게시됩니다. [Adobe Experience League.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html#aem-as-cloud-service)

예정된 기능을 검토하고 테스트할 시간을 계획할 수 있도록 릴리스 날짜를 확인하십시오.

## 릴리스 노트 검토 {#release-notes}

달력에 릴리스 날짜가 표시되어 있으면 반드시 [Adobe Experience League](/help/release-notes/release-notes-cloud/release-notes-current.md) 최신 릴리스 노트는 릴리스 날짜의 웹 사이트입니다.

각 릴리스에는 해당 릴리스의 새로운 기능뿐만 아니라 사전 릴리스 평가에 사용할 수 있는 기능까지 문서화하는 릴리스 노트가 포함되어 있습니다. 미리 알고 AEMaaCS의 최신 기능을 활용할 수 있습니다.

다음을 수행할 수도 있습니다 [알려진 문제 확인](/help/release-notes/known-issues.md) 모든 릴리스와 함께 게시되므로 평가나 새로운 기능의 최종 채택에 문제가 될 수 있는 모든 기술 문제를 해결할 수 있습니다.

## 시험판 채널을 활성화하여 새로운 기능에 액세스하고 사용해 보십시오 {#new-features}

모든 개발 또는 샌드박스 환경에서 사전 릴리스 채널을 활성화할 수 있습니다. 스테이징 또는 프로덕션 환경에서는 사전 릴리스를 활성화할 수 없습니다.

다음과 같이 다양한 방식으로 프리릴리스 기능을 경험할 수 있습니다.

* [클라우드 환경](#cloud-environments)
* [로컬 SDK](#local-sdk)

### 클라우드 환경 {#cloud-environments}

사전 릴리스를 사용하도록 클라우드 환경을 업데이트하려면 새 환경 변수를 추가해야 합니다. Cloud Manager UI를 사용하거나 CLI를 통해 수행할 수 있습니다.

#### UI를 사용하여 환경 변수 추가 {#add-with-ui}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 사전 릴리스를 활성화할 프로그램으로 이동합니다.

1. 를 통해 사전 릴리스를 활성화할 환경을 선택하고 해당 구성에 액세스합니다 **프로그램** > **환경** > **환경 구성**.

1. 새 추가 [환경 변수:](../implementing/cloud-manager/environment-variables.md)

   | 이름 | 값 | 적용된 서비스 | 유형 |
   |------|-------|-----------------|------|
   | `AEM_RELEASE_CHANNEL` | `prerelease` | 모두 | 변수 |

1. 변경 내용을 저장하면 환경은 프리릴리스 기능 전환이 활성화되며 새로 고침됩니다.

   ![새 환경 변수](assets/env-configuration-prerelease.png)

#### CLI를 사용하여 환경 변수 추가 {#add-with-cli}

Cloud Manager API 및 CLI를 사용하여 환경 변수를 업데이트할 수도 있습니다.

* 사용 [Cloud Manager API의 환경 변수 엔드포인트,](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchEnvironmentVariables) 설정 `AEM_RELEASE_CHANNEL` 값에 대한 환경 변수 `prerelease`.

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

* [Cloud Manager CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) 사용 가능

   ```shell
   aio cloudmanager:environment:set-variables <ENVIRONMENT_ID> --programId=<PROGRAM_ID> --variable AEM_RELEASE_CHANNEL “prerelease
   ```

환경을 정기적인(비 프리릴리스) 채널의 비헤이비어로 복원하고자 하는 경우 변수를 삭제하거나 다른 값으로 다시 설정할 수 있습니다.

### 로컬 SDK {#local-sdk}

사전 릴리스를 참조하도록 Maven 프로젝트를 구성하여 사전 릴리스의 새 API에 대한 코드와 로컬 Quickstart SDK의 사이트 콘솔에서 새로운 기능을 볼 수 있습니다 `API Jar` Maven Central에 있습니다. 사전 릴리스 모드에서 일반 Quickstart SDK를 시작하여 로컬 개발 환경에서 이러한 사전 릴리스 기능을 볼 수도 있습니다.

#### 사전 릴리스 모드에서 Quickstart SDK 시작 {#prerelease-mode}

1. 소프트웨어 배포 포털에서 SDK를 다운로드하고 다음에 설명된 대로 설치합니다. [AEM as a Cloud Service SDK에 액세스합니다.](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
1. SDK 빠른 시작을 실행하면 인수 `-r prerelease`를 포함합니다.

값은 고정되므로 처음 시작할 때만 선택할 수 있습니다. 명령줄 옵션을 변경하려면 SDK를 다시 설치합니다.

월별 기능 릴리스 간에는 여러 AEM 유지 관리 릴리스가 있으므로 이들 새 SDK를 다운로드하고 Maven 프로젝트에 새 SDK API Jar 버전을 참조할 수 있습니다. 유지 관리 릴리스에는 프리릴리스 기능이 추가되지 않지만 버그 수정, 보안 수정 및 성능 개선과 같은 사소한 변경 내용이 포함될 수 있습니다.
JavaDoc은 Maven Central에 게시됩니다.

#### 사전 릴리스 SDK에 대해 빌드 {#build-sdk}

1. maven 프로젝트 수정 `pom.xml` maven Central에 게시된 개별 사전 릴리스 SDK API jar를 참조하려면 다음을 수행하십시오. 이 팩에는 사전 릴리스 기능을 위한 새로운 Java API가 포함되어 있으며 SDK API jar에 대한 종속성이 있습니다. 동일한 버전을 사용합니다.

   예를 들어, 다음은 일반적인 API jar를 참조하는 상위 pom의 종속성 관리 섹션의 코드 조각입니다.

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

   프리릴리스 SDK를 변경하려면 아래의 설명처럼 `com.adobe.aem:aem-sdk-api`에서 `com.adobe.aem:aem-prerelease-sdk-api`로 종속성을 변경하기만 하면 됩니다.

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

1. 로컬 서버에 배포.

1. 로컬에서 예상대로 작동하므로 문제가 해결되면 개발 분기에 코드를 커밋하고 Cloud Manager 비프로덕션 파이프라인을 사용하여 사전 릴리스 채널에 가입한 환경에 배포합니다.

>[!CAUTION]
> 
> 다음 `aem-prerelease-sdk-api` 스테이지나 프로덕션에 배포할 때에는 artifactId를 사용하지 않아야 합니다. 항상 `aem-sdk-api` 프로덕션 파이프라인을 통해 배포할 때. 마찬가지로 사전 릴리스 API를 참조하는 코드는 프로덕션 파이프라인을 통해 배포하지 않아야 합니다.

다음 [AEM CS SDK build Analyzer maven 플러그인 v1.0 이상](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing) 은 종속성을 검사하여 프리릴리스 API가 프로젝트에서 사용되는지 확인합니다. 분석기가 찾으면 시험판 SDK API를 사용하여 프로젝트를 분석합니다.

## 사용자 교육 {#train-users}

사전 릴리스 채널에서 새로운 기능을 테스트하고 프로젝트에서 이러한 기능을 활용하기로 결정했으면 사용자를 교육해야 합니다.

Adobe Experience League은 AEMaaCS를 학습하기 위한 많은 리소스를 제공합니다.

* [AEMaaCS 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html)
* [튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-tutorials/overview.html)
* [월별 릴리스 개요 비디오](/help/release-notes/release-notes-cloud/release-notes-current.md#release-video) 릴리스 정보

## 고려 사항 {#considerations}

사전 릴리스 채널을 사용할 때에는 몇 가지 주목할 필요가 있습니다.

* 사전 릴리스 채널에는 반드시 다음 릴리스에서 롤아웃할 새 기능이 모두 포함되어 있지는 않습니다.
* 프리릴리스에 있는 기능은 엄격한 품질 보증을 통해 출시되며 Beta 품질이 아닌 완전한 품질을 갖춘 기능을 제공하기 위해 설계되었습니다. 문제가 발생하는 경우 정규 AEM 릴리스의 기능에서 버그가 의심되는 경우와 마찬가지로 보고하십시오.
* 사전 릴리스 채널에 대한 환경이 구성되어 있는지 확인하려면 AEM 콘솔의 **정보** 페이지를 방문하여 AEM 버전 번호가 *사전 릴리스* 접미사 ```Adobe Experience Manager 2021.4.5226.20210427T070726Z-210429-PRERELEASE```.

![](/help/release-notes/assets/about.png) 정보
