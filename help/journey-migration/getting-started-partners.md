---
title: 파트너용 Experience Manager as a Cloud Service 마이그레이션 안내서
description: 파트너용 Experience Manager as a Cloud Service 마이그레이션 안내서
exl-id: 9d5a72b8-06af-4b82-ab20-e65aea7903b3
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 21%

---

# 파트너용 Adobe Experience Manager as a Cloud Service으로 마이그레이션 안내서 {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="AEM as a Cloud Service로 마이그레이션"
>abstract="고객을 다양한 Experience Manager 배포에서 Experience Manager as a Cloud Service로 전환하고, 기존 고객이 연결된 경험을 지속적으로 제공할 수 있도록 지원하는 단계적 접근 방식에 대해 설명합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=ko-KR" text="새로운 기능 및 차이점은?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/introduction.html?lang=ko-KR" text="AEM as a Cloud Service 소개."

AEM as a Cloud Service(Adobe Experience Manager)은 Experience Manager 기반 인프라, API 기반 개발 및 가이드 DevOps 프로세스를 기반으로 구축된 컨테이너용 재설계 기반을 제공하여 마케터와 개발자가 항상 고객 경험 관리의 혁신을 주도할 수 있도록 합니다.

Cloud Service은 Adobe Experience Manager의 풍부한 기본 기능과 확장성을 최신 클라우드 기반 아키텍처의 민첩성과 함께 제공하여 브랜드가 지속적으로 변화하는 소비자 수요를 충족할 수 있도록 합니다.

이 한 페이지 분량의 문서에서는 고객을 다양한 Experience Manager 배포에서 Experience Manager as a Cloud Service로 전환하고 기존 고객이 경험 관리를 위해 특별히 제작된 이 현대적인 플랫폼에서 연결된 경험을 지속적으로 제공할 수 있도록 지원하는 단계적 접근 방식에 대해 설명합니다.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

마이그레이션 여정에 대한 일반적인 설명은 아래 다이어그램을 참조하십시오.

![이미지](/help/journey-migration/assets/migration-process.png)

## Adobe Experience Manager as a Cloud Service 시작하기 {#getting-started}

| 뭐가 다르죠? | 아키텍처 개요 |
|--------------------------|--------------------------|
| <ul><li>[현대 건축](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[자동 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)</li><li>[에셋 마이크로서비스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[직접 액세스 바이너리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html?lang=en)</li><li>[코드와 컨텐츠 분리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=en)</li><li>[Replication as a Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/replication.html?lang=ko)</li><li>[Admin Console, 그룹/사용자 멤버십 및 ACL](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li></ul> | <ul><li>[AEM Architecture 소개](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[환경 스택](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[작성자 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[계층 게시](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=en)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=en) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html) (CI/CD)</li><li>[Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=ko-KR) 경유 [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li><li>[Asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - 런타임 아키텍처](/help/overview/assets/concepts-03.png "AEM as a Cloud Service - 런타임 아키텍처")

<br>

## Adobe Experience Manager as a Cloud Service의 개발자 여정 {#developer-journey}

### 개발

코드 개발의 기본 사항은 Adobe Experience Manager as a Cloud Service에서 Adobe Experience Manager On Premise 및 Managed Services 솔루션과 유사합니다.

개발자는 코드를 작성하여 로컬에서 테스트한 다음 원격 Adobe Experience Manager as a Cloud Service 환경으로 푸시합니다.

Experience Manager as a Cloud Service 배포를 사용자 지정하는 방법에 대해 알아보려면 Experience Manager as a Cloud Service에 대한 구현에 대한 자가 진단 리소스 를 참조하십시오.

| 로컬 개발 설정 | 시작하기 전에 알아야 할 사항 |
|-----------|------------|
| <ol><li>리뷰 [ADOBE EXPERIENCE MANAGER SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en) 설명서에서 자세히 알아보십시오.</li><li>시청 [Dispatcher SDK 설치](https://video.tv.adobe.com/v/30601) dispatcher SDK 설치 방법을 이해하려면</li><li>시청 [Dispatcher SDK 구성](https://video.tv.adobe.com/v/30602) dispatcher SDK 구성 방법을 이해하려면</li><li>리뷰 [로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up) 설명서 를 참조하십시오.</li><li>Experience Manager에 대한 액세스 구성 [연습](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing)</li></ol> | <ol><li>[개발 기본 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en)</li><li>[개발 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=en)</li><li>[Experience Manager 프로젝트 구조 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=en)</li><li>[핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[Digital Foundation 블루프린트](https://solutionpartners.adobe.com/content/dam/solution/en/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[스타일 시스템](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/style-system.html?lang=en)</li><li>[오버레이](/help/implementing/developing/introduction/overlays.md)</li><li>[Experience Manager as a Cloud Service API 참조](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/)</li></ol> |

>[!TIP]
> 방법에 대한 튜토리얼 보기 [로컬 Experience Manager SDK에서 WKND 개발 및 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### 배포

개발자는 코드를 작성하고 로컬에서 테스트한 다음 원격 AEM as a Cloud Service 환경에 푸시합니다.

Managed Services용 선택적 콘텐츠 게재 도구였던 Cloud Manager가 필요합니다. 이는 코드를 AEM as a Cloud Service 환경에 배포하기 위한 유일한 메커니즘입니다.

AEM as a Cloud Service 환경을 구성하고 배포하는 방법에 대해서는 자가 진단 리소스 를 참조하십시오.

1. [CM 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/introduction-ci-cd-pipelines.html?lang=en)
   * 프로덕션 파이프라인
   * 비프로덕션 및 코드 품질 전용 파이프라인
2. [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=en)
3. [테스트 결과 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en)
4. **로그 액세스**
   * [CM UI 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html?lang=en)
   * [Adobe i/o cli를 통해](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
5. [작업 및 유지 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/home.html?lang=en)
   * [OSGI 구성 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=en)
   * [백업 및 복원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html?lang=en)

>[!TIP]
> 방법에 대한 튜토리얼 보기 [Experience Manager Cloud Service에 WKND 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### 도움말 및 리소스

1. [디버깅 팁 및 요령](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=en) (로컬 SDK 및 Experience Manager 클라우드 개발 환경에서만 사용 가능)
4. [로그 및 로깅](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging) (빌드 단위 테스트, 코드 스캔, 빌드 이미지, 배포)
   * [Experience Manager Cloud Service 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * 로컬 SDK 로그(host:port/crx-quickstart/logs 아래)

>[!NOTE]
> 추가 도움말은 다음과 같습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. 탐색 [Experience Manager 커뮤니티 및 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

<br>

## Adobe Experience Manager as a Cloud Service로 이동 {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Adobe Experience Manager as a Cloud Service로 이동"
>abstract="이 한 페이지 분량의 문서에서는 고객을 다양한 Experience Manager 배포에서 Experience Manager as a Cloud Service로 전환하고 기존 고객이 경험 관리를 위해 특별히 제작된 이 현대적인 플랫폼에서 연결된 경험을 지속적으로 제공할 수 있도록 지원하는 단계적 접근 방식에 대해 설명합니다."

**Experience Manager as a Cloud Service은 Experience Manager Sites 및 Assets에 확장 가능하고 안전하며 민첩한 기술 기반을 제공하므로 마케터와 IT 담당자가 규모에 맞게 효과적인 경험을 전달하는 데 집중할 수 있습니다.**

Experience Manager as a Cloud Service을 통해 팀은 제품 업그레이드를 계획하는 대신 혁신에 집중할 수 있습니다. 새로운 제품 기능은 중단 없이 철저하게 테스트되고 팀에게 전달되므로 항상 최신 애플리케이션에 액세스할 수 있습니다.

클라우드 서비스로 전환하는 여정에는 계획, 실행 및 Go-live 후의 3단계가 포함됩니다.
성공적이고 원활한 전환을 위해 본 안내서에 나와 있는 우수 사례를 준수하고 적절한 계획을 세워야 합니다.

아래 그림은 권장되는 Cloud Service 전환 여정의 높은 수준의 표현을 보여 줍니다.

![이미지](/help/journey-migration/assets/home-img1.png)

<br>

### 계획

Cloud Service으로 전환 여정을 시작하기 전에 Experience Manager as a Cloud Service에 대해 숙지하고, 이에 대한 주목할 만한 변경 사항을 검토하고, 교체되거나 더 이상 사용되지 않는 기능을 검토해야 합니다.

<table>
<tr>
<td>프로젝트 검색 및 평가</td>
<td><ul><li>다음을 참조하십시오 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=en">Experience Manager as a Cloud Service의 주요 변경 사항</a> Adobe Experience Manager as a Cloud Service과 Experience Manager 6.x 간의 중요한 차이점을 이해합니다.</li><li>다음을 참조하십시오 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html?lang=en">더 이상 사용되지 않는 기능</a> 더 이상 사용되지 않는 것으로 표시된 기능에 대해 자세히 알아보십시오.</li><li>[Cloud Service 마이그레이션만 해당] Cloud Service 준비 평가 : <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en">Best Practices Analyzer(BPA)</a> 소스 환경에서 </li><li>Experience Manager CS에서 주목할 만한 변경 사항 및 사용되지 않는 기능에 대한 평가를 완료합니다.</li></ul></td>
</tr>
<tr>
<td>리뷰</td>
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

프로젝트의 실행 단계를 시작하기 전에 Cloud Service에 온보딩해야 합니다. 또한 Cloud Manager를 숙지해야 합니다. 프로젝트 코드를 Experience Manager Cloud Service 인스턴스에 배포하는 메커니즘입니다.

Cloud Manager를 통해 조직은 클라우드에서 Experience Manager을 자체 관리할 수 있습니다. 여기에는 지속적인 통합 및 지속적인 게재([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/overview/ci-cd-pipelines.html?lang=en)) IT 팀과 구현 파트너가 성능 또는 보안을 손상하지 않고 맞춤화 또는 업데이트를 신속하게 전달할 수 있는 프레임워크입니다.

#### 콘텐츠 마이그레이션

1. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration) : 기존 콘텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용됩니다.
2. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#package-manager) : 저장소의 변경 가능한 콘텐츠를 가져오고 내보내는 데 사용됩니다.


#### 리팩터링/최적화

| 시작하기 | 리뷰 및 리팩터링 코드 | Dispatcher 검토 |
|---|---|---|
| <ul><li>[로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[로컬 Dispatcher 설정](https://video.tv.adobe.com/v/30602/)</li><li>[SDK API Jar를 사용하여 코드 컴파일](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en)</li><li>[AEM 개발 지침 검토](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=en)<ul><li>백그라운드 작업 및 장기 실행 작업</li><li>Sling 스케줄러</li><li>스트림 사용량 입력 등</li></ul></li></ul> | <ul><li>실행 [Best Practices Analyzer(BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en) 소스 환경에서.[**마이그레이션만 해당**]<ul><li>프로젝트 구조화 고려 사항(기반) [Cloud 원형](https://github.com/adobe/aem-project-archetype))<ul><li>코드와 콘텐츠 분리(변경 가능 및 변경 불가능)</li><li>[사용자 정의 색인 정의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=en)</li><li>[사용자 지정 실행 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=en)</li></ul></li></ul></li><li>필요한 변경 사항을 검토하고 실행합니다.</li><li>[배포](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) 로컬 SDK의 it</li><li>AEM SDK를 통해 스모크 테스트 수행</li></ul> | <ul><li>리뷰 [Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=en) 리팩터링용</li><li>사용 [Dispatcher 변환기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en) 필요한 경우 도구. [**마이그레이션만 해당**]</li><li>검사는 다음을 사용하여 수행할 수 있습니다. [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)</li></ul> |

>[!TIP]
> Assets 고객 : 을 사용하여 Assets 워크플로 검토 및 리팩터링 [Asset Cloud 마이그레이션](https://github.com/adobe/aem-cloud-migration) 공구 설비


#### 배포/라이브

1. [Cloud Manager에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html?lang=en) git
2. 다음을 통해 고객 코드 실행 [Cloud Manager 품질 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-quality-testing.html?lang=en)
3. [개발 환경에 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**마이그레이션만 해당**] 패키지 또는 [컨텐츠 전송 도구](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md)(CTT)
5. 권장 테스트 주기 수행(연기, QA 등)
6. Cloud Manager 프로덕션 파이프라인으로 승격
7. 스모크 테스트 유효성 검사
8. 실행

<br>

### Go-Live 후

Go-live 후 단계에서는 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

>[!TIP]
> AEM as a Cloud Service 환경 문제를 해결하는 데 도구를 사용할 수 있습니다
>1. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=en)
>2. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html?lang=en)
>3. [로그 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html?lang=en)

<br>

### 도구 및 리소스

| 평가 | 리팩터링 | Experience Manager 현대화 | 콘텐츠 마이그레이션 |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en)</li></li> | <ul><li>[통합 경험 플러그인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html?lang=en)</li></ul> | <ul><li>[정적 템플릿을 편집 가능한 템플릿](https://opensource.adobe.com/aem-modernize-tools/pages/structure.html)</li><li>[디자인 구성을 정책](https://opensource.adobe.com/aem-modernize-tools/pages/policy.html) <li>[기초 구성 요소를 핵심 구성 요소로 변환](https://opensource.adobe.com/aem-modernize-tools/pages/component.html)</li><li>[클래식 UI를 터치 사용 UI](https://opensource.adobe.com/aem-modernize-tools/pages/all-in-one.html)</li></ul> | <ul><li>[콘텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=ko)</li><li>[패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement)</li></ul> |

>[!NOTE]
> 추가 도움말은 다음과 같습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. 탐색 [Experience Manager 커뮤니티 및 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)
