---
title: Cloud Service으로 Experience Manager으로 마이그레이션하기 위한 단일 호출기
description: Cloud Service으로 Experience Manager으로 마이그레이션하기 위한 단일 호출기
translation-type: tm+mt
source-git-commit: 02e6581ec5a922d71c53e99212a1f8aecc405f6f
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 8%

---


# Cloud Service {#Overview}으로 Adobe Experience Manager으로 마이그레이션

>[!CONTEXTUALHELP]
>id="aemcloud_migration-overview"
>title="클라우드 서비스로 AEM으로 마이그레이션"
>abstract="다양한 Experience Manager 배포에서 Experience Manager으로 고객을 전환하고 기존 고객이 연결되고 지속적인 경험을 제공할 수 있도록 지원하기 위한 단계별 접근 방식을 설명합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en" text="새로운 기능과 다른 기능"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en" text="AEM as a Cloud Service 소개."

Adobe Experience Manager(AEM) Cloud Service은 컨테이너 기반 인프라, API 기반의 개발 및 DevOps 안내 프로세스를 기반으로 구축된 Experience Manager의 재설계 기반을 제공하므로 마케터와 개발자는 고객 경험 관리 혁신의 변화를 항상 앞서나갈 수 있습니다.

Cloud Service은 최신 클라우드 기본 아키텍처의 민첩성과 Adobe Experience Manager의 풍부한 기능과 확장성을 갖추고 브랜드 기업은 끊임없이 변화하는 소비자의 요구를 충족할 수 있습니다.

이 일회용 페이지에서는 다양한 Experience Manager 배포에서 Experience Manager으로 고객을 전환할 것을 권장하는 단계적 접근 방식을 소개하고 기존 고객이 경험 관리를 위해 특별히 고안된 최신 플랫폼에서 일관된 경험을 제공할 수 있도록 지원합니다.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Cloud Service {#getting-started}으로 Adobe Experience Manager 시작하기

| 뭐가 다르죠? | 아키텍처 개요 |
|--------------------------|--------------------------|
| <ul><li>[현대 건축](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[자동 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=en#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)</li><li>[Asset Microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html)</li><li>[직접 액세스 바이너리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en#asset-upload-with-direct-binary-access)</li><li>[코드 및 컨텐츠 분리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[서비스로 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=en)</li><li>[관리 콘솔, 그룹/사용자 멤버십 및 ACL](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li></ul> | <ul><li>[AEM 아키텍처 소개](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[환경 스택](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[작성 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[게시 계층](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery) </li><li>[클라우드 관리자](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) (CI/CD)</li><li>[관리 ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) 콘솔을 통한  [ID 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - 런타임 아키텍처](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service - 런타임 아키텍처")

<br>

## Cloud Service {#developer-journey}으로서 Adobe Experience Manager의 개발자 여정

### 개발

Adobe Experience Manager의 코드 개발 기본은 Adobe Experience Manager 온-프레미스 및 Managed Services 솔루션에 비해 Cloud Service과 비슷하다.

개발자는 코드를 작성하고 로컬로 테스트한 다음 Cloud Service 환경으로 원격 Adobe Experience Manager으로 푸시됩니다.

Cloud Service의 구현에 대한 자체 도움말 리소스를 통해 Cloud Service을 Experience Manager 배포으로 사용자 정의하는 방법을 살펴볼 수 있습니다.

| 로컬 개발 설정 | 시작하기 전에 알아야 할 사항 |
|-----------|------------|
| <ol><li>자세한 내용은 [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing) 설명서를 참조하십시오.</li><li>Dispatcher SDK 설치 방법 이해[](https://video.tv.adobe.com/v/30601?captions=kor)</li><li>Dispatcher SDK 구성 방법을 이해하려면 [Dispatcher SDK 구성](https://video.tv.adobe.com/v/30602?captions=kor)을 시청하십시오.</li><li>자세한 내용은 [로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up) 설명서를 참조하십시오.</li><li>Experience Manager [walk-through](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing)에 대한 액세스 구성</li></ol> | <ol><li>[Development Essentials](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[개발 지침](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)</li><li>[Experience Manager 프로젝트 구조 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[디지털 기반 청사진](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[스타일 시스템](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=en#authoring)</li><li>[오버레이](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/overlays.html?lang=en#developing)</li><li>[Cloud Service API 참조로 Experience Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> 로컬 Experience Manager SDK[에서 WKND 개발 및 배포 방법에 대한 자습서 참조](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en)

### 배포

개발자는 코드를 작성하고 로컬로 테스트한 다음 Cloud Service 환경으로 원격 AEM으로 푸시됩니다.

Managed Services의 선택적 컨텐츠 전달 툴인 Cloud Manager가 필요합니다. 이제 Cloud Service 환경으로 AEM에 코드를 배포하는 유일한 메커니즘입니다.

Cloud Service 환경으로 AEM을 구성 및 배포하는 방법에 대한 자체 도움말 리소스를 참조하십시오.

1. [CM 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)
   * 프로덕션 파이프라인
   * 비프로덕션 및 코드 품질 전용 파이프라인
2. [배포 코드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#using-cloud-manager)
3. [테스트 결과 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en#using-cloud-manager)
4. **로그 액세스**
   * [CM UI 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)
   * [adobe i/o 클립 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
5. [운영 및 유지 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=en)
   * [OSGI 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#deploying)
   * [백업 및 복원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en)

>[!TIP]
> Experience Manager Cloud Service에 WKND 배포 방법[에 대한 자습서를 참조하십시오.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/develop-wknd-tutorial.html?lang=en)

### 도움말 및 리소스

1. [디버깅 팁 및 기법](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging) (로컬 SDK 및 Experience Manager 클라우드 개발 환경에서만 사용 가능)
4. [로그 및 로깅](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging) (빌드 단위 테스트, 코드 스캔, 빌드 이미지, 배포)
   * [Experience Manager Cloud Service 로그](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * 로컬 SDK 로그(호스트:port/crx-quickstart/logs 아래)

>[!NOTE]
> 추가 도움이 필요한 경우 다음을 수행할 수 있습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Manager 커뮤니티 및 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community) 탐색


<br>

## Cloud Service {#move-to-cloud}으로 Adobe Experience Manager으로 이동

**Cloud Service의 Experience Manager은 Experience Manager 사이트 및 자산을 위한 확장 가능하고 안전하며 민첩한 기술 기반을 제공하므로 마케터와 IT 담당자는 규모에 맞게 효과적인 경험을 전달하는 데 주력할 수 있습니다.**

Cloud Service을 통해 팀은 제품 업그레이드를 계획하지 않고 혁신에 집중할 수 있습니다. 새로운 제품 기능은 중단 없이 철저하게 테스트되어 팀에게 전달되므로 항상 최신 애플리케이션에 액세스할 수 있습니다.

클라우드 서비스로 전환하는 여정에는 계획, 실행 및 Go-live 후의 3단계가 포함됩니다.
성공적이고 원활한 전환을 위해 본 안내서에 나와 있는 우수 사례를 준수하고 적절한 계획을 세워야 합니다.

아래 그림은 권장되는 클라우드 서비스로의 전환 여정을 시각적으로 보여줍니다.

![이미지](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### 계획

Cloud Service으로 전환 작업을 시작하기 전에 Experience Manager에 익숙해지고 Cloud Service에 대한 주목할 만한 변경 사항을 검토하고 교체되거나 사용되지 않은 기능을 검토해야 합니다.

<table>
<tr>
<td>프로젝트 검색 및 평가</td>
<td><ul><li>Cloud Service 및 Experience Manager 6.x로서 Adobe Experience Manager 간의 중요한 차이점을 이해하려면 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">Cloud Service</a>으로 Experience Manager에 대한 주목할 만한 변경 사항을 참조하십시오.</li><li>더 이상 사용되지 않는 것으로 표시된 기능 및 기능에 대한 자세한 내용은 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=en#deprecated-features">더 이상 사용되지 않는 기능</a>을 참조하십시오.</li><li>[Cloud Service 마이그레이션만 해당] Cloud Service 준비 상태 평가:소스 환경에서 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Best Practices Analyzer(BPA)</a>를 실행합니다. </li><li>Experience Manager CS에서 주목할 만한 변경 사항 및 가치가 떨어진 기능에 대한 평가 완료</li></ul></td>
</tr>
<tr>
<td>리뷰</td>
<td><ul><li>검색 기반, 노력 평가 및 리소스 확보 연습</li></ul></td>
</tr>
<tr>
<td>측정</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">프로젝트 KPI</a>, 성공 기준 및 프로젝트 일정 설정</li></ul></td>
</tr>
</table>

>[!NOTE]
>모범 사례 분석기 보고서는 수동으로 수집하고 평가해야 하는 정보를 제공하여 AEM으로 전환하는 데 필요한 시간과 비용을 계산하는 프로세스를 가속화합니다.


<br>

### 실행

프로젝트의 실행 단계를 시작하기 전에 Cloud Service에 응답해야 합니다. 또한 Cloud Manager에 익숙해져야 합니다. 이는 Experience Manager Cloud Service 인스턴스에 프로젝트 코드를 배포하는 메커니즘입니다.

Cloud Manager를 사용하면 조직에서 클라우드에서 자체 Experience Manager을 관리할 수 있습니다. IT 팀 및 구현 파트너가 성능이나 보안을 훼손하지 않고 사용자 지정 또는 업데이트 전달을 신속하게 처리할 수 있도록 해주는 지속적인 통합 및 연속 전달([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=en#overview)) 프레임워크가 포함되어 있습니다.

#### 콘텐츠 마이그레이션

1. [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration) :기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용됩니다.
2. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#package-manager) :저장소의 변경 가능한 컨텐츠를 가져오고 내보내는 데 사용됩니다.


#### 리팩터/최적화

| 시작하기 | 리뷰 및 리팩터 코드 | 발송자 검토 |
|---|---|---|
| <ul><li>[로컬 개발 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[로컬 발송자 설정](https://video.tv.adobe.com/v/30602/?captions=kor)</li><li>[SDK API jar를 사용하여 코드 컴파일](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[AEM 개발 지침 검토](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>백그라운드 작업 및 긴 실행 작업</li><li>Sling 스케줄러</li><li>입력 스트림 사용량 등</li></ul></li></ul> | <ul><li>소스 환경에서 [Best Practices Analyzer(BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)를 실행합니다.[**마이그레이션 전용**]<ul><li>프로젝트 구조화 고려 사항([클라우드 원형을 기반으로 함](https://github.com/adobe/aem-project-archetype))<ul><li>코드와 컨텐츠의 분리(변경 및 불변경)</li><li>[사용자 정의 색인 정의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#indexing)</li><li>[사용자 정의 런타임 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)</li></ul></li></ul></li><li>필요한 변경 사항 검토 및 실행</li><li>[로컬 ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) SDK에 배포</li><li>AEM SDK를 통해 연기 테스트 수행</li></ul> | <ul><li>리팩토링할 [발송자 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#local-validation-of-dispatcher-configuration)을 검토합니다.</li><li>[Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en#introduction-dispatcher) 도구를 적절히 활용합니다. [**마이그레이션 전용**]</li><li>테스트는 [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)를 사용하여 수행할 수 있습니다.</li></ul> |

>[!TIP]
> 자산 고객:[Asset Cloud Migration](https://github.com/adobe/aem-cloud-migration) 도구를 사용하여 자산 검토 및 재지정 워크플로우


#### 배포/이동-라이브

1. [클라우드 관리에 ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=en#managing-code) 배포
2. [클라우드 관리자 품질 파이프라인을 통해 고객 코드 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)
3. [개발 환경에 배포](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**마이그레이션**] 전용 패키지 또는  [컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration(CTT)을 사용한 컨텐츠 전송
5. 권장되는 테스트 주기 수행(연기, QA 등)
6. Cloud Manager 프로덕션 파이프라인으로 홍보
7. 연기 테스트 유효성 검사
8. Go-Live

<br>

### Post Go-Live

Go-live 후 단계에서는 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

>[!TIP]
> Cloud Service 환경에서 AEM 문제를 해결하는 데 사용할 수 있는 도구
>1. [개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [로그 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### 툴 및 리소스

| 평가 | 리팩토링 | Experience Manager 현대화 | 콘텐츠 마이그레이션 |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[모범 사례 분석기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[통합 경험 플러그인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#refactoring-tools)</li></ul> | <ul><li>[정적 템플릿을 편집 가능한 템플릿](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[디자인 구성을 정책](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[기초 구성 요소를 코어 구성 요소](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[클래식 UI를 터치 사용 UI](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[컨텐츠 전송 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration)</li><li>[설치할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement)</li></ul> |

>[!NOTE]
> 추가 도움이 필요한 경우 다음을 수행할 수 있습니다.
>1. [Experience Manager 지원 팀에 문의](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Manager 커뮤니티 및 포럼](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community) 탐색

