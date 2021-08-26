---
title: 파트너를 위한 Experience Manager으로 마이그레이션 안내서
description: 파트너를 위한 Experience Manager으로 마이그레이션 안내서
exl-id: 4d1addcf-b22d-41a3-ba5c-e5c42244e5cd
source-git-commit: f193c4e81b9b16d07e7ccff6c2f9705b7234f80b
workflow-type: tm+mt
source-wordcount: '2112'
ht-degree: 10%

---

# 파트너를 위한 Cloud Service으로 Adobe Experience Manager로의 마이그레이션 안내서 {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="AEM as a cloud Service로 마이그레이션"
>abstract="다양한 Experience Manager 배포에서 Cloud Service으로 Experience Manager에 이르기까지 고객을 전환하고 기존 고객이 연결되고 지속적인 경험을 제공할 수 있도록 지원하는 권장 단계별 접근 방식을 간략하게 설명합니다"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en" text="새로운 기능 및 다른 기능"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en" text="AEM as a Cloud Service 소개."

Adobe Experience Manager (AEM) as a Cloud Service은 컨테이너 기반 인프라, API 기반 개발 및 DevOps 프로세스를 기반으로 구축된 Experience Manager을 위한 재설계 기반을 제공하므로 마케터와 개발자는 고객 경험 관리 혁신에서 항상 앞서나갈 수 있습니다.

Cloud Service은 브랜드가 항상 진화하는 소비자 요구를 충족할 수 있도록 최신 클라우드 기본 아키텍처의 민첩성을 통해 Adobe Experience Manager의 다양한 기본 기능 및 확장성을 제공합니다.

이 안내서는 다양한 Experience Manager 배포에서 Cloud Service으로 Experience Manager에 이르기까지 고객을 전환하고 이를 통해 기존 고객이 경험 관리를 위해 특별히 제작된 최신 플랫폼에서 지속적으로 연결된 경험을 제공할 수 있도록 지원하는 데 대해 권장하는 단계별 접근 방식을 간략하게 설명합니다.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Adobe Experience Manager as a Cloud Service 시작하기 {#getting-started}

| 뭐가 다르죠? | 아키텍처 개요 |
|--------------------------|--------------------------|
| <ul><li>[현대 건축](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[자동 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=en#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=ko-KR)</li><li>[자산 마이크로서비스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html)</li><li>[직접 액세스 바이너리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en#asset-upload-with-direct-binary-access)</li><li>[코드와 컨텐츠 분리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Replication as a Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=ko-KR)</li><li>[Admin Console, 그룹/사용자 멤버십 및 ACL](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li></ul> | <ul><li>[AEM 아키텍처 소개](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[환경 스택](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[작성 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[게시 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) (CI/CD)</li><li>[Admin ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) Console을  [통한 ID 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - 런타임 아키텍처](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service - 런타임 아키텍처")

<br>

## Adobe Experience Manager as a Cloud Service의 개발자 여정 {#developer-journey}

### 개발

코드 개발에 대한 기본 사항은 Adobe Experience Manager 온-프레미스 및 Managed Services 솔루션과 비교하여 Adobe Experience Manager에 Cloud Service으로 유사합니다.

개발자가 코드를 작성하고 로컬에서 테스트한 다음 원격 Adobe Experience Manager에 Cloud Service 환경으로 푸시됩니다.

Experience Manager을 Cloud Service 배포으로 사용자 지정하는 방법에 대해 알려면 Cloud Service로서의 구현을 위한 자습 리소스를 참조하십시오.

| 로컬 개발 설정 | 시작하기 전에 알아야 할 사항 |
|-----------|------------|
| <ol><li>자세한 내용은 [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing) 설명서를 참조하십시오.</li><li>[Dispatcher SDK 설치](https://video.tv.adobe.com/v/30601)를 시청하고 Dispatcher SDK를 설치하는 방법을 알아보십시오</li><li>[Dispatcher SDK 구성](https://video.tv.adobe.com/v/30602)에서 Dispatcher SDK를 구성하는 방법을 알아보십시오</li><li>자세한 내용은 [로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up) 설명서를 참조하십시오</li><li>Experience Manager [둘러보기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing)에 대한 액세스 구성</li></ol> | <ol><li>[개발 핵심 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[개발 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)</li><li>[Experience Manager 프로젝트 구조 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR)</li><li>[Digital Foundation 블루프린트](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[스타일 시스템](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=en#authoring)</li><li>[오버레이](/help/implementing/developing/introduction/overlays.md)</li><li>[Cloud Service API 참조로서의 Experience Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> 로컬 Experience Manager SDK에서 [WKND를 개발 및 배포하는 방법에 대한 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)를 참조하십시오

### 배포

개발자가 코드를 작성하고 로컬로 테스트한 다음 원격 AEM에 Cloud Service 환경으로 푸시됩니다.

Managed Services용 선택적 콘텐츠 전달 도구인 Cloud Manager가 필요합니다. 이제 Cloud Service 환경으로 AEM에 코드를 배포하는 유일한 메커니즘입니다.

AEM as a Cloud Service 환경으로 구성 및 배포하는 방법에 대한 자습 리소스를 참조하십시오.

1. [CM 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)
   * 프로덕션 파이프라인
   * 비프로덕션 및 코드 품질 전용 파이프라인
2. [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#using-cloud-manager)
3. [테스트 결과 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en#using-cloud-manager)
4. **로그 액세스**
   * [CM UI 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)
   * [Adobe i/o cli 를 통해](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
5. [작업 및 유지 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=en)
   * [OSGI 구성 구성 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#deploying)
   * [백업 및 복원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en)

>[!TIP]
> [WKND를 Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)에 배포하는 방법에 대한 자습서를 참조하십시오

### 도움말 및 리소스

1. [디버깅 팁 및 트릭](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging) (로컬 SDK 및 Experience Manager Cloud 개발 환경에서만 사용 가능)
4. [로그 및 로깅](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging) (빌드 단위 테스트, 코드 스캔, 빌드 이미지, 배포)
   * [Experience Manager Cloud Service 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * 로컬 SDK 로그(호스트:port/crx-quickstart/logs 아래)

>[!NOTE]
> 추가적인 도움이 필요하면 다음을 수행할 수 있습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Manager 커뮤니티 및 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community) 탐색


<br>

## Adobe Experience Manager으로 Cloud Service으로 이동 {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Adobe Experience Manager으로 Cloud Service으로 이동"
>abstract="이 안내서는 다양한 Experience Manager 배포에서 Cloud Service으로 Experience Manager에 이르기까지 고객을 전환하고 이를 통해 기존 고객이 경험 관리를 위해 특별히 제작된 최신 플랫폼에서 지속적으로 연결된 경험을 제공할 수 있도록 지원하는 데 대해 권장하는 단계별 접근 방식을 간략하게 설명합니다."

**Experience Manager as a Cloud Service은 Experience Manager 사이트 및 자산에 확장 가능하고 안전하며 민첩한 기술 기반을 제공하므로 마케터와 IT 담당자가 규모에 맞게 효과적인 경험을 전달하는 데 주력할 수 있습니다.**

Experience Manager을 Cloud Service으로 사용하면 팀이 제품 업그레이드를 계획하지 않고 혁신에 집중할 수 있습니다. 새로운 제품 기능은 중단 없이 철저하게 테스트되어 팀에게 전달되므로 항상 최신 애플리케이션에 액세스할 수 있습니다.

클라우드 서비스로 전환하는 여정에는 계획, 실행 및 Go-live 후의 3단계가 포함됩니다.
성공적이고 원활한 전환을 위해 본 안내서에 나와 있는 우수 사례를 준수하고 적절한 계획을 세워야 합니다.

아래 그림은 권장되는 클라우드 서비스로의 전환 여정을 시각적으로 보여줍니다.

![이미지](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### 계획

Cloud Service으로 전환 여정을 시작하기 전에 먼저 Experience Manager을 Cloud Service으로 숙지하고,에 대한 주목할 만한 변경 사항을 검토하고, 교체되거나 더 이상 사용되지 않는 기능을 검토해야 합니다.

<table>
<tr>
<td>프로젝트 검색 및 평가</td>
<td><ul><li>Cloud Service 로서의 Adobe Experience Manager과 Experience Manager 6.x의 중요한 차이점을 파악하려면 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">Cloud Service로서의 Experience Manager에 대한 주목할 만한 변경 사항</a>을 참조하십시오.</li><li>더 이상 사용되지 않음으로 표시된 기능에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=en#deprecated-features">더 이상 사용되지 않는 기능</a>을 참조하십시오.</li><li>[Cloud Service 마이그레이션만 해당] Cloud Service 준비 평가 : 소스 환경에서 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">우수 사례 분석기(BPA)</a>를 실행합니다 </li><li>Experience Manager CS의 주요 변경 사항 및 더 이상 사용되지 않는 기능에 대한 평가를 완료합니다</li></ul></td>
</tr>
<tr>
<td>리뷰</td>
<td><ul><li>검색을 기반으로 작업 추정 및 리소스 수집 연습 수행</li></ul></td>
</tr>
<tr>
<td>측정</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">프로젝트 KPI</a>, 성공 기준 및 프로젝트 타임라인 설정</li></ul></td>
</tr>
</table>

>[!NOTE]
>모범 사례 분석기 보고서는 수동으로 수집하고 평가해야 하는 정보를 제공하여 AEM으로 전환하는 데 필요한 시간과 비용을 계산하는 프로세스를 가속화합니다.


<br>

### 실행

프로젝트의 실행 단계를 시작하기 전에 Cloud Service에 온보딩해야 합니다. 또한 Cloud Manager를 숙지해야 합니다. 프로젝트 코드를 Experience Manager Cloud Service 인스턴스에 배포하는 메커니즘입니다.

조직에서 Cloud Manager를 사용하여 클라우드에서 Experience Manager을 자체 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 지속적인 통합 및 지속적 배포([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=en#overview)) 프레임워크가 포함되어 있습니다.

#### 컨텐츠 마이그레이션

1. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration) : 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 target AEM Cloud Service 인스턴스로 이동하는 데 사용됩니다.
2. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#package-manager) : 저장소의 가변 콘텐츠를 가져오고 내보내는 데 사용됩니다.


#### 리팩터링/최적화

| 시작하기 | 검토 및 리팩터링 코드 | Dispatcher 검토 |
|---|---|---|
| <ul><li>[로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[로컬 Dispatcher 설정](https://video.tv.adobe.com/v/30602/)</li><li>[SDK API jar를 사용하여 코드를 컴파일합니다](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[AEM 개발 지침 검토](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>백그라운드 작업 및 장기 실행 작업</li><li>Sling 스케줄러</li><li>입력 스트림 사용량 등</li></ul></li></ul> | <ul><li>소스 환경에서 [우수 사례 분석기(BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)를 실행합니다.[**마이그레이션만**]<ul><li>프로젝트 구조 고려 사항([Cloud Archetype](https://github.com/adobe/aem-project-archetype) 기반)<ul><li>코드와 컨텐츠 분리(가변 및 변경할 수 없음)</li><li>[사용자 지정 인덱스 정의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#indexing)</li><li>[사용자 지정 실행 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)</li></ul></li></ul></li><li>필요한 변경 사항에 대해 검토 및 실행</li><li>[](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) 로컬 SDK에 배포</li><li>AEM SDK를 통해 연기 테스트 수행</li></ul> | <ul><li>리팩터링용 [Dispatcher 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#local-validation-of-dispatcher-configuration) 검토</li><li>적절한 경우 [Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en#introduction-dispatcher) 도구를 활용하십시오. [**마이그레이션만**]</li><li>테스트는 [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)를 사용하여 수행할 수 있습니다</li></ul> |

>[!TIP]
> Assets 고객 : [Asset Cloud 마이그레이션을 사용하여 자산 워크플로우 검토 및 리팩터링](https://github.com/adobe/aem-cloud-migration) 도구


#### 배포/Go-Live

1. [클라우드 관리에 ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=en#managing-code) 배포
2. [Cloud Manager 품질 파이프라인을 통해 고객 코드 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)
3. [개발 환경에 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**패키지**] 또는 CTT( [컨텐츠 전송 도구)를 사용한 마이그레이션 전용](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)
5. 권장 테스트 주기(연기, QA 등)를 수행합니다
6. Cloud Manager 프로덕션 파이프라인으로 승격
7. 연기 테스트 유효성 검사
8. Go-Live

<br>

### Go-Live 후

Go-live 후 단계에서는 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

>[!TIP]
> 도구는 AEM as a Cloud Service 환경 문제를 해결하는 데 사용할 수 있습니다
>1. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [로그 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### 도구 및 리소스

| 평가 | 리팩터링 | Experience Manager 현대화 | 컨텐츠 마이그레이션 |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[모범 사례 분석기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[통합 경험 플러그인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#refactoring-tools)</li></ul> | <ul><li>[정적 템플릿을 편집 가능한 템플릿](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[디자인 구성을 정책](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[기초 구성 요소를 코어 구성 요소](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[클래식 UI를 터치 사용 UI](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration)</li><li>[설치할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement)</li></ul> |

>[!NOTE]
> 추가적인 도움이 필요하면 다음을 수행할 수 있습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Manager 커뮤니티 및 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community) 탐색

