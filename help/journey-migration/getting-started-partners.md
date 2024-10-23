---
title: 파트너용 Experience Manager as a Cloud Service 마이그레이션 안내서
description: 파트너용 Experience Manager as a Cloud Service 마이그레이션 안내서
exl-id: 9d5a72b8-06af-4b82-ab20-e65aea7903b3
feature: Migration
role: Admin
source-git-commit: 7c704aa09ae4a6a3368b1eccb12982360a3350b3
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 17%

---

# 파트너용 Adobe Experience Manager as a Cloud Service 마이그레이션 안내서 {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="AEM as a Cloud Service로 마이그레이션"
>abstract="고객을 다양한 Experience Manager 배포에서 Experience Manager as a Cloud Service로 전환하고, 기존 고객이 연결된 경험을 지속적으로 제공할 수 있도록 지원하는 단계적 접근 방식에 대해 설명합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html" text="새로운 기능 및 차이점은?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/introduction.html" text="AEM as a Cloud Service 소개."

Adobe Experience Manager(AEM as a Cloud Service)는 Experience Manager을 위한 업데이트된 아키텍처를 제공합니다. 이 기반은 컨테이너 기반 인프라, API 기반 개발 및 DevOps 프로세스를 기반으로 구축됩니다. 이를 통해 마케터와 개발자는 고객 경험 관리의 혁신적인 기능을 주도할 수 있습니다.

Cloud Service은 Adobe Experience Manager의 풍부한 기본 기능과 확장성을 현대적인 클라우드 기반 아키텍처의 민첩성과 결합하여 브랜드가 지속적으로 발전하는 소비자 수요를 충족할 수 있도록 합니다.

이 페이지에서는 이전 Experience Manager 배포에서 Experience Manager as a Cloud Service 로 고객을 전환하는 데 권장되는 단계별 접근 방식을 간략하게 설명합니다. 특별히 제작된 새로운 플랫폼은 연결된 지속적인 경험을 제공하는 데 도움이 됩니다.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

마이그레이션 여정에 대한 일반적인 설명은 아래 다이어그램을 참조하십시오.

![마이그레이션 여정의 일반 표시](/help/journey-migration/assets/migration-process.png)

## Adobe Experience Manager as a Cloud Service 시작하기 {#getting-started}

| 뭐가 다르죠? | 아키텍처 개요 |
|--------------------------|--------------------------|
| <ul><li>[최신 아키텍처](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[자동 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)</li><li>[자산 마이크로서비스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[직접 액세스 바이너리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[코드와 콘텐츠 분리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)</li><li>[서비스로 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/replication.html)</li><li>[관리 콘솔, 그룹/사용자 멤버십 및 ACL](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li></ul> | <ul><li>[AEM 아키텍처 소개](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html#underlying-technology)</li><li>[환경 스택](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[작성자 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html#underlying-technology)</li><li>[Publish 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)(CI/CD)</li><li>[Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)을 통해 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li><li>[Asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - 런타임 아키텍처](/help/overview/assets/concepts-03.png "AEM as a Cloud Service - 런타임 아키텍처")

<br>

## Adobe Experience Manager as a Cloud Service의 개발자 여정 {#developer-journey}

### 개발

Adobe Experience Manager as a Cloud Service의 코드 개발 기본 사항은 Adobe Experience Manager On Premise 및 Managed Services 솔루션의 기본 사항과 유사합니다.

개발자는 코드를 작성하여 로컬에서 테스트한 다음 원격 Adobe Experience Manager as a Cloud Service 환경에 푸시합니다.

자체 도움말 리소스 를 참조하여 Experience Manager as a Cloud Service Experience Manager as a Cloud Service 배포를 사용자 정의하는 방법에 대해 알아보십시오.

| 로컬 개발 설정 | 시작하기 전에 알아야 할 사항 |
|-----------|------------|
| <ol><li>자세한 내용은 [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html) 설명서를 검토하십시오.</li><li>Dispatcher SDK 설치 방법을 이해하려면 [Dispatcher SDK 설치](https://video.tv.adobe.com/v/30601)를 시청하십시오</li><li>Dispatcher SDK를 구성하는 방법을 이해하려면 [Dispatcher SDK 구성](https://video.tv.adobe.com/v/30602)을 시청하십시오</li><li>자세한 내용은 [로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html#local-development-environment-set-up) 설명서를 검토하십시오.</li><li>[연습](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html#accessing) Experience Manager에 대한 액세스를 구성하는 중</li></ol> | <ol><li>[Development Essentials](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>[개발 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)</li><li>[Experience Manager 프로젝트 구조 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)</li><li>[핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko)</li><li>[Digital Foundation 블루프린트](https://solutionpartners.adobe.com/content/dam/solution/en/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[스타일 시스템](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/style-system.html)</li><li>[오버레이](/help/implementing/developing/introduction/overlays.md)</li><li>[Experience Manager as a Cloud Service API 참조](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/)</li></ol> |

>[!TIP]
> 로컬 Experience Manager SDK에서 [WKND를 개발 및 배포하는 방법에 대한 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=ko)을 참조하세요.

### 배포 중

개발자는 코드를 작성하여 로컬에서 테스트한 다음 원격 AEM as a Cloud Service 환경에 푸시합니다.

Managed Services용 선택적 컨텐츠 전달 도구였던 Cloud Manager이 이제 필수입니다. AEM as a Cloud Service 환경에 코드를 배포하는 유일한 메커니즘입니다.

AEM as a Cloud Service 환경을 구성하고 배포하는 방법에 대한 자가 진단 리소스 를 참조하십시오.

1. [CM 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/introduction-ci-cd-pipelines.html)
   * 프로덕션 파이프라인
   * 비프로덕션 및 코드 품질 전용 파이프라인
2. [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html)
3. [테스트 결과 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html)
4. **로그 액세스**
   * [CM UI를 통해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html)
   * [Adobe i/o cli를 통해](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)
5. [작업 및 유지 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/home.html)
   * [OSGI 구성 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html)
   * [백업 및 복원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html)

>[!TIP]
> [Experience Manager Cloud Service에 WKND를 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=ko)하는 방법에 대한 튜토리얼을 참조하세요.

### 도움말 및 리소스

1. [디버깅 팁 및 요령](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html#debugging-aem-as-a-cloud-service)
2. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html)(로컬 SDK 및 Experience Manager 클라우드 개발 환경에서만 사용 가능)
4. [로그 및 로깅](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)
   * [CM 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html#debugging)(빌드 단위 테스트, 코드 스캔, 빌드 이미지, 배포)
   * [Experience Manager Cloud Service 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)(aemerror, aemaaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * 로컬 SDK 로그(host:port/crx-quickstart/logs 아래)

>[!NOTE]
> 추가 도움말은 다음과 같습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
>2. [커뮤니티 및 포럼 Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

<br>

## Adobe Experience Manager as a Cloud Service로 이동 {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Adobe Experience Manager as a Cloud Service로 이동"
>abstract="이 한 페이지 분량의 문서에서는 고객을 다양한 Experience Manager 배포에서 Experience Manager as a Cloud Service로 전환하고 기존 고객이 경험 관리를 위해 특별히 제작된 이 현대적인 플랫폼에서 연결된 경험을 지속적으로 제공할 수 있도록 지원하는 단계적 접근 방식에 대해 설명합니다."

**Experience Manager Assets은 Experience Manager Sites 및 as a Cloud Service에 확장 가능하고 안전하며 민첩한 기술 기반을 제공하여 마케터와 IT가 규모에 맞게 효과적인 경험을 제공하는 데 집중할 수 있도록 합니다.**

Experience Manageras a Cloud Service 을 통해 팀은 제품 업그레이드를 계획하는 대신 혁신에 집중할 수 있습니다. 새로운 제품 기능은 중단 없이 철저하게 테스트되고 팀에게 전달되므로 항상 최신 애플리케이션에 액세스할 수 있습니다.

Cloud Service 전환 여정은 계획, 실행 및 Go-live 후의 세 단계로 구성됩니다.
성공적이고 원활한 전환을 위해 본 안내서에 나와 있는 우수 사례를 준수하고 적절한 계획을 세워야 합니다.

아래 그림은 권장되는 Cloud Service 전환 여정의 높은 수준의 표현을 보여 줍니다.

![Cloud Service에 대한 권장 전환 여정의 상위 수준 표시](/help/journey-migration/assets/home-img1.png)

<br>

### 계획 수립

Cloud Service으로 전환 여정을 시작하기 전에 다음을 수행해야 합니다.

* Experience Manager as a Cloud Service 숙지
* 이에 대한 주목할 만한 변경 사항을 검토합니다
* 교체되거나 더 이상 사용되지 않는 기능 검토

<table>
<tr>
<td>프로젝트 검색 및 평가</td>
<td><ul><li>Adobe Experience Manager as a Cloud Service과 Experience Manager 6.x 간의 중요한 차이점을 이해하려면 {0 Experience Manager as a Cloud Service 변경 내용}주목할 만한 변경 사항</a>을 참조하십시오.<a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html"></li><li>더 이상 사용되지 않는 것으로 표시된 기능에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html">더 이상 사용되지 않는 기능</a>을 참조하세요.</li><li>[Cloud Service 마이그레이션만 해당] Cloud Service 준비 평가 : 소스 환경에서 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html">BPA(모범 사례 분석기) 실행</a> </li><li>Experience Manager CS에서 주목할 만한 변경 사항 및 사용되지 않는 기능에 대한 평가를 완료합니다.</li></ul></td>
</tr>
<tr>
<td>검토</td>
<td><ul><li>검색을 기반으로 노력 추정 및 리소스 측정 연습 수행</li></ul></td>
</tr>
<tr>
<td>측정</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">프로젝트 KPI 설정</a>, 성공 기준 및 프로젝트 타임라인</li></ul></td>
</tr>
</table>

>[!NOTE]
>모범 사례 분석기 보고서는 수동으로 수집하고 평가해야 하는 정보를 제공하여 AEM as a Cloud Service으로 전환하는 데 필요한 시간과 비용을 계산하는 프로세스를 가속화합니다.


<br>

### 실행

프로젝트의 실행 단계를 시작하기 전에 Cloud Service에 온보딩해야 합니다. 또한 Cloud Manager을 숙지해야 합니다. 프로젝트 코드를 Experience Manager Cloud Service 인스턴스에 배포하는 메커니즘입니다.

Cloud Manager을 통해 조직은 클라우드에서 Experience Manager을 자체 관리할 수 있습니다. IT 팀과 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 사항 또는 업데이트를 신속하게 전달할 수 있는 지속적인 통합 및 연속 제공([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/overview/ci-cd-pipelines.html)) 프레임워크가 포함되어 있습니다.

#### 콘텐츠 마이그레이션

1. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html#migration) : 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용됩니다.
2. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html#package-manager) : 저장소의 변경 가능한 콘텐츠를 가져오고 내보내는 데 사용됩니다.


#### 리팩터링/최적화

| 시작하기 | 리뷰 및 리팩터링 코드 | Dispatcher 검토 |
|---|---|---|
| <ul><li>[로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html#local-development-environment-set-up)</li><li>[로컬 Dispatcher 설치](https://video.tv.adobe.com/v/30602/)</li><li>[SDK API Jar를 사용하여 코드를 컴파일합니다](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>[AEM 개발 지침 검토](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)<ul><li>백그라운드 작업 및 장기 실행 작업</li><li>Sling 스케줄러</li><li>스트림 사용량 입력 등</li></ul></li></ul> | <ul><li>소스 환경에서 [BPA(모범 사례 분석기)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html)을(를) 실행합니다.[**마이그레이션만**]<ul><li>프로젝트 구조 고려 사항([Cloud Archetype](https://github.com/adobe/aem-project-archetype) 기반)<ul><li>코드와 콘텐츠 분리(변경 가능 및 변경 불가능)</li><li>[사용자 지정 인덱스 정의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)</li><li>[사용자 지정 실행 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html)</li></ul></li></ul></li><li>필요한 변경 사항을 검토하고 실행합니다.</li><li>로컬 SDK에서 [배포](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=ko)</li><li>AEM SDK를 통해 스모크 테스트 수행</li></ul> | <ul><li>리팩터링에 대한 [Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) 검토</li><li>해당되는 경우 [Dispatcher 변환기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/dispatcher-transformation-utility-tools.html) 도구를 사용하십시오. [**마이그레이션만**]</li><li>테스트는 [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)를 사용하여 수행할 수 있습니다.</li></ul> |

>[!TIP]
> Assets 고객 : [Asset Cloud 마이그레이션](https://github.com/adobe/aem-cloud-migration) 도구를 사용하여 Assets 워크플로 검토 및 리팩터링


#### 배포/라이브

1. [Cloud Manager에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html) git
2. [Cloud Manager 품질 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-quality-testing.html)을 통해 고객 코드 실행
3. [개발 환경에 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html#debugging)
4. 패키지 또는 [콘텐츠 전송 도구를 사용하여 [**마이그레이션만**] 콘텐츠 전송](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md)(CTT)
5. 권장 테스트 주기 수행(연기, QA 등)
6. Cloud Manager 프로덕션 파이프라인으로 홍보
7. 스모크 테스트 유효성 검사
8. 실행

<br>

### Go-live 후

Go-live 후 단계에서는 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

>[!TIP]
> AEM as a Cloud Service 환경 문제를 해결하는 데 도구 사용 가능
>1. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)
>2. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html)
>3. [로그 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html)

<br>

### 도구 및 리소스

| 평가 | 리팩터링 | Experience Manager 현대화 | 콘텐츠 마이그레이션 |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[모범 사례 분석기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html)</li></li> | <ul><li>[통합 경험 플러그 인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html)</li></ul> | <ul><li>[정적 템플릿을 편집 가능한 템플릿으로 설정](https://opensource.adobe.com/aem-modernize-tools/pages/structure.html)</li><li>[정책에 대한 구성 디자인](https://opensource.adobe.com/aem-modernize-tools/pages/policy.html) <li>[핵심 구성 요소에 기초 구성 요소](https://opensource.adobe.com/aem-modernize-tools/pages/component.html)</li><li>[클래식 UI에서 터치 사용 UI로](https://opensource.adobe.com/aem-modernize-tools/pages/all-in-one.html)</li></ul> | <ul><li>[컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html)</li><li>[패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html#contentmanagement)</li></ul> |

>[!NOTE]
> 추가 도움말은 다음과 같습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
>2. [커뮤니티 및 포럼 Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)
