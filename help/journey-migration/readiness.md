---
title: 준비 단계
description: AEM 설치를 클라우드로 이동할 준비가 되었는지 확인하기 위해 수행해야 하는 단계에 대해 알아봅니다
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
source-git-commit: 13cb8ae059f0a77e517d2e64eae96a08f88ac075
workflow-type: tm+mt
source-wordcount: '2079'
ht-degree: 7%

---

# 준비 단계 {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="전환 계획"
>abstract="클라우드 서비스로 전환 여정을 시작하기 전에 먼저 AEM as a Cloud Service를 숙지하고, 이에 대한 주목할 만한 변경 사항을 검토하고, 교체되거나 더 이상 사용되지 않는 기능을 검토해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html" text="Best Practices Analyzer"

AEM as a Cloud Service 마이그레이션 여정의 이 단계에서는 AEM을 숙지하고, 도입된 주목할 만한 변경 사항을 검토하고, 클라우드로 성공적인 마이그레이션을 계획하는 데 필요한 사항을 이해할 수 있습니다.

## 지금까지의 이야기 {#story-so-far}

이전 문서 [AEM으로 이동 시작 as a Cloud Service](/help/journey-migration/getting-started.md)에서는 AEM as a Cloud Service으로 마이그레이션하기 위해 수행해야 하는 단계 목록과 이러한 작업의 이점을 간략하게 설명합니다.

## 목표 {#objective}

이 문서는 AEM 설치를 클라우드로 이동할 준비가 되었는지 확인하기 위해 고려해야 하는 요소를 이해하는 데 도움이 됩니다.

* 주요 변경 사항 및 더 이상 사용되지 않는 기능에 대해 알아봅니다
* AEM as a Cloud Service로의 마이그레이션을 계획하는 방법을 이해합니다

## AEM as a Cloud Service 아키텍처의 주요 변경 사항 검토 {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service는 AEM 프로젝트 관리를 위한 많은 새로운 기능과 가능성을 제공합니다.

이러한 개선 사항과 함께 AEM과 Adobe Managed Services의 온-프레미스 설치 간에 AEM as a Cloud Service과 비교하여 몇 가지 차이점이 발생했습니다.

아래 표의 항목 목록은 AEM as a Cloud Service로의 마이그레이션과 가장 관련이 있는 변경 사항의 하위 집합입니다. 주요 변경 사항의 전체 목록을 참조할 수 있습니다 [여기](/help/release-notes/aem-cloud-changes.md).

<table>
<thead>
  <tr>
    <th>변경 사항</th>
    <th>참조</th>
    <th>주요 사항</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>가변 및 가변 필터를 해당 패키지로 구분</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">AEM as a Cloud Service 주요 변경 사항</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM as a Cloud Service용 AEM 프로젝트 구조</a></td>
    <td>AEM as a Cloud Service에 배포할 수 있는 단일 패키지는 하위 패키지를 가질 수 있으며, 주로 고유한 패키지로 구분된 변경할 수 없는 콘텐츠를 포함할 수 있습니다.</td>
  </tr>
  <tr>
    <td>보고서 초기화</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Apache Sling RepoInit 설명서</a></td>
    <td>보고서 스크립트는 초기 노드 구조, 사용자, 그룹 또는 서비스 사용자를 만드는 우수 사례입니다. 이러한 스크립트는 실행 모드별로 타겟팅될 수 있고 코드 패키지 배포를 통해 관리할 수 있으므로 저장소 초기화 작업을 수행하는 데 매우 융통성을 제공합니다.</td>
  </tr>
  <tr>
    <td>사용자 지정 실행 모드가 허용되지 않습니다</td>
    <td></td>
    <td>AEM as a Cloud Service과 함께 즉시 제공된 실행 모드만 지원됩니다.<br>추가 개발 환경이 추가되면 모두 "개발" 실행 모드에 연결됩니다.</td>
  </tr>
  <tr>
    <td>Cloud Manager 파이프라인 실행은 를 배포할 수 있는 유일한 방법입니다</td>
    <td></td>
    <td>AEM as a Cloud Service에서 /system/console에 대한 액세스가 허용되지 않으므로 모든 OSGi 구성은 코드의 일부여야 하며 코드로 배포해야 합니다.<br>OSGi 구성은 Cloud Manager를 통해 개발자 콘솔을 통해 볼 수 있도록 읽기 전용 모드에서 사용할 수 있습니다</td>
  </tr>
  <tr>
    <td>복제 에이전트가 Sling 컨텐츠 배포로 대체됨</td>
    <td></td>
    <td>복제 에이전트의 개념은 컨텐츠 배포 사용으로 대체됩니다. 복제 에이전트를 활용하는 사용자 지정 사항이 있는 경우 재설계해야 합니다.<br>역방향 복제가 지원되지 않습니다.</td>
  </tr>
  <tr>
    <td>CRX/DE 및 패키지 관리자</td>
    <td></td>
    <td>CRX/DE는 개발 환경에서만 사용할 수 있습니다.<br>패키지 관리자는 모든 작성자 인스턴스에서 액세스할 수 있지만 배포되는 패키지에는 변경할 수 있는 컨텐츠만 포함되어야 합니다(예: /content 또는 /conf)</td>
  </tr>
  <tr>
    <td>CDN에 내장되어 있으며 CDN을 가져옵니다</td>
    <td></td>
    <td>AEM as a Cloud Service에는 대부분의 사용 사례에 최적화된 모든 환경에 대한 CDN이 포함되어 있습니다.<br>CDN을 고유한 CDN을 설정하려면 승인을 위해 Adobe 지원에 요청을 제출해야 합니다.<br>승인되면 CDN은 모든 환경에서 AEM 인스턴스를 가리키거나 정확하게 가리키지 않습니다.</td>
  </tr>
  <tr>
    <td>장기 실행 작업</td>
    <td></td>
    <td>컨테이너에서 실행되는 AEM 인스턴스가 특정 시점에 와서 실행될 수 있으므로 Sling 스케줄러 또는 Cron 작업과 같이 오래 실행되는 작업을 실행하지 마십시오.<br>Adobe I/O으로 오프로드할 수 있도록 이러한 기능을 재고하십시오.</td>
  </tr>
  <tr>
    <td>비동기 작업으로 전환</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/asynchronous-jobs.html?lang=en#configuring-asynchronous-msm-operations">비동기 작업 구성</a></td>
    <td>환경의 전체 성능을 개선하기 위해 특정 작업이 비동기 모드로 실행됩니다. 시스템 리소스를 사용할 수 있으면 비동기 작업을 큐에 넣고 실행합니다.</td>
  </tr>
  <tr>
    <td>토큰 기반 인증 및 통합 전략</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#the-server-to-server-flow">서버측 API에 대한 액세스 토큰 생성</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication">토큰 기반 인증 자습서</a></td>
    <td>AEM 외부 시스템에서 AEM 내에서 HTTP 작업을 수행하려고 하는 경우가 많습니다.<br>권장되는 방법은 AEM에서 암호를 사용하여 로컬 사용자 이름을 만드는 대신 여기에 설명된 전략을 구현하는 것입니다.</td>
  </tr>
  <tr>
    <td>파일 IO/디스크 사용</td>
    <td></td>
    <td>디스크 공간이 얼마나 할당되고 컨테이너의 인스턴스가 와서 이동할 수 있는지 보장할 수 없으므로 AEM 인스턴스에 첨부된 디스크에서 쓰거나 읽는 데 파일 I/O 작업을 사용하는 것이 좋습니다.</td>
  </tr>
  <tr>
    <td>DAM 자산 업데이트 워크플로우</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=en">asset compute 서비스</a></td>
    <td>DAM 자산 업데이트 워크플로우의 일부인 미디어 처리 단계가 이제 Asset compute 서비스로 대체됩니다</td>
  </tr>
  <tr>
    <td>AEM as a Cloud Service에서 자산 업로드 방법 및 지원되는 워크플로우 프로세스 단계</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/developer-reference-material-apis.html?lang=en#post-processing-workflows-steps">API 비교 및 지원되는 WF 프로세스 단계 업로드</a></td>
    <td>AEM as a Cloud Service에서 자산을 업로드하거나 다운로드하는 동안 자산이 이진 저장소에서 직접 스트리밍되거나 바이너리 저장소에서 바로 스트리밍됩니다.</br>일부 워크플로우 프로세스 단계가 AEMaaCS에서 지원되는 것은 아닙니다.</td>
  </tr>
  <tr>
    <td>워크플로 런처</td>
    <td></td>
    <td>코드에서 OOTB 또는 사용자 지정 DAM 자산 업데이트 워크플로우를 트리거하는 워크플로우 런처를 제거합니다.</br>AEM as a Cloud Service에 업로드된 모든 자산은 자산 처리 서비스에서 처리됩니다. 사용자 지정 단계는 다음을 참조하십시오. <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=en#post-processing-workflows"> 사후 처리 워크플로우</a> 사후 처리 워크플로우 설정 및 구성 방법에 대해 설명합니다.</td>
  </tr>
  <tr>
    <td>사용자 정의 표현물 단계</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html?lang=en#manage">처리 프로필</a></td>
    <td>사용자 지정 표현물 생성, 이미지 전환 또는 비디오 인코딩은 해당 처리 프로필을 만들어 자산 처리 서비스로 오프로드해야 합니다.</td>
  </tr>
  <tr>
    <td>콘텐츠 검색 및 색인화</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en">컨텐츠 검색 및 색인 지정 변경 사항</a></td>
    <td>지표의 기본 처리에 상당한 변화가 있으며, 인덱스가 들어올 때 발생합니다.<br>배포할 코드에서 Oak 인덱스를 관리하기 전에 Oak 인덱스를 완전히 이해하고 리팩터링합니다.</td>
  </tr>
  <tr>
    <td>일부 유지 관리 작업은 구성할 수 없습니다</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/maintenance.html?lang=en">AEM as a Cloud Service 유지 관리 작업</a></td>
    <td>AEM as a Cloud Service으로 특정 유지 관리 작업만 구성할 수 있습니다.</td>
  </tr>
  <tr>
    <td>게시 리포지토리 변경</td>
    <td></td>
    <td>/home에 있는 것 외에는 게시 리포지토리에 대한 직접 변경을 수행할 수 없습니다. 항상 작성자를 변경하고 배포하는 것이 좋습니다. 모든 코드 및 구성 변경 사항은 해당 Cloud Manager 파이프라인을 통해 배포해야 합니다.</td>
  </tr>
  <tr>
    <td>Dispatcher 구성 및 캐싱</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery">클라우드의 디스패처</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/caching.html?lang=en#other-content">캐시 관리<br></td>
    <td>Dispatcher 구성은 특정 구조를 따라야 합니다.<br>구성은 코드의 일부로 관리하고 Cloud Manager 파이프라인을 통해 배포해야 합니다.</td>
  </tr>
  <tr>
    <td>백업 및 복원</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en">AEM as a Cloud Service 백업 및 복원</a></td>
    <td></td>
  </tr>
  <tr>
    <td>인증 변경</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=ko-KR">AEM as a Cloud Service에 대한 IMS 지원</td>
    <td>이전에 Cloud Service으로 이동하기 전에 작성자와 게시 모두에서 SAML 2.0 통합을 사용하는 경우 AEM as a Cloud Service 작성자가 Adobe IMS와만 통합된다는 것이 주요 변경 사항입니다. 그러나 AEM as a Cloud Service 게시 계층은 여전히 SAML 또는 기타 인증 통합을 활용할 수 있습니다. AEM as a Cloud Service에서는 작성자, 관리자 및 개발자 사용자에 대해서만 IMS 인증 지원 서비스를 제공합니다. IMS 인증은 사이트 방문자와 같은 고객 사이트의 외부 최종 사용자를 지원하지 않습니다.</td>
  </tr>
</tbody>
</table>

## 더 이상 사용되지 않는 기능 {#deprecated-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다.

다음 사항을 참조하는 것을 권장합니다. [더 이상 사용되지 않는 기능](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html#deprecated-features) Experience Manager as a Cloud Service에서 더 이상 사용되지 않음으로 표시된 기능을 숙지하고 AEM 배포에 미치는 영향을 확인하십시오.

## AEM 설치 검토 계획 {#review-planning}

AEM as a Cloud Service으로 도입된 변경 사항에 익숙해지면 클라우드로 이동하기 위해 필요한 변경 사항을 측정하기 위해 기존 설치에 대한 검토 계획을 시작할 차례입니다.

다음 그림은 검토 단계 중에 포함된 주요 단계를 보여줍니다.

![이미지](/help/journey-migration/assets/planning-phaseimg1.png)

다음으로, 각 단계가 구체적으로 무엇을 의미하는지 살펴보겠습니다.

### 클라우드 서비스 준비 평가 {#assess-cloud-readiness}

첫 번째 단계는 기존 AEM 버전에서 Cloud Service으로 이동할 준비를 평가하고 AEM as a Cloud Service과 호환되도록 리팩터링이 필요한 영역을 결정하는 것입니다.

주요 변경 사항 및 더 이상 사용되지 않는 기능에 대해 현재 AEM 소스 코드에 대한 포괄적인 평가를 수행하여 전환 여정에서 예상되는 작업 수준을 결정해야 합니다.

조사 결과 수는 일정 및 전반적인 프로젝트 성공에 직접적인 영향을 미칠 것이다. 따라서 게재를 계획하거나 AEM as a Cloud Service 모범 사례에 따라 진행해야 하는 사용자 지정 사항을 다시 디자인하는 데 필요한 대화를 시작하는 데 필요한 대화를 가능한 한 많이 발견하는 것이 좋습니다.

**모범 사례 분석기**

현재 AEM 버전에 대해 Best Practices Analyzer 를 실행하여 평가를 가속화할 수 있습니다. 그것이 어떻게 작동하는지를 잘 이해하는 것은 여러분의 평가 계획을 가속화하는 열쇠입니다.

다음 정보를 통해 작동 방식에 대해 자세히 알아볼 수 있습니다. [모범 사례 분석기](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) 설명서.

**클라우드 준비 평가 보고서 만들기**

다음 단계는 지금까지 얻은 모든 지식을 바탕으로 보고서를 만드는 것입니다. 이렇게 하려면 단계 및 프로덕션 인스턴스에서 모범 사례 분석기 보고서를 생성하여 [그런 다음 Cloud Acceleration Manager에 업로드합니다](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) 를 참조하십시오.

일반적인 보고서에는 다음 입력이 포함되어야 합니다.

* 특정 AEM 설치의 기능 세트를 자세히 설명하는 설명서
* AEM 사용자 지정 구성 및 코드에 대한 세부 사항
* 프로덕션 Dispatcher 구성
* CDN 구성 (있는 경우)

**보고서 관계**

모범 사례 분석기 보고서가 완료되면 관련 팀과 공유하여 결과를 확인하고 다음 단계를 계획합니다. 기본 설정에 따라 [인쇄 미리 보기](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam).

### 리소스 계획 검토 {#review-resource-planning}

Cloud Service으로 이동하는 데 필요한 작업 수준을 예측했으면 리소스를 식별하고, 팀을 만들고, 전환 프로세스에 대한 역할과 책임을 매핑해야 합니다.

### KPI 설정 {#establish-kpis}

이전에 KPI(주요 성과 지표)를 설정하지 않은 경우 AEM 구현에 대한 KPI를 설정하여 팀이 가장 중요한 사항에 집중할 수 있도록 하는 것이 좋습니다.

자세한 내용은 [KPI 개발](https://guided.adobe.com/welcome/aem/part6.html) 비즈니스 목표에 적합한 KPI를 선택하는 방법을 알아봅니다.

## 다음 단계 {#what-is-next}

AEM as a Cloud Service으로 이동하는 데 필요한 변경 사항의 범위를 이해하면 됩니다. [코드 및 컨텐츠 클라우드를 준비합니다.](/help/journey-migration/implementation.md) 마이그레이션을 실제로 수행하기 전에 이 작업을 수행하십시오.

## 추가 리소스 {#additional-resources}

* [Cloud Acceleration Manager 시작하기](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Cloud Acceleration Manager를 사용하여 클라우드로 빠르게 이동하는 방법에 대한 포괄적인 안내서입니다
* [AEM as a Cloud Service: 소개, 건축, 사고방식이 다르다](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=en#dashboard/learning)
* [AEM a Cloud Service 홈](/help/overview/home.md) - Experience Manager as a Cloud Service 설명서에 대한 개요를 알려면 여기에서 시작하십시오.
* [AEM as a Cloud Service 개요](/help/overview/home.md) - 이 안내서에서는 소개, 용어 및 아키텍처 등 Experience Manager as a Cloud Service에 대한 개요를 제공합니다.
* [온보딩 여정](/help/journey-onboarding/overview.md)- 이 안내서에서는 액세스 및 팀 설정 방법 등 Experience Manager as a Cloud Service으로 시작하는 방법에 대한 요약을 제공합니다
