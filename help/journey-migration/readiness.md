---
title: 준비 단계
description: AEM 설치를 클라우드로 이동할 준비가 되었는지 확인할 수 있도록 수행해야 하는 단계에 대해 알아봅니다.
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
feature: Migration
role: Admin
source-git-commit: 913b1beceb974243f0aa7486ddd195998d5e9439
workflow-type: tm+mt
source-wordcount: '1913'
ht-degree: 6%

---

# 준비 단계 {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="전환 계획"
>abstract="Cloud Service로의 전환 여정을 시작하기에 앞서 AEM as a Cloud Service에 익숙해지십시오. 주목할 만한 변경 사항과 대체되거나 더 이상 사용하지 않는 기능을 검토해 보십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html" text="Best Practices Analyzer"

AEM as a Cloud Service 마이그레이션 여정의 이 단계에서는 AEM as a Cloud Service을 숙지합니다. 도입된 주목할 만한 변경 사항을 검토하고 클라우드로의 성공적인 마이그레이션을 계획하는 데 필요한 사항을 이해할 수 있습니다.

## 지금까지의 스토리 {#story-so-far}

이전 문서인 [AEM as a Cloud Service으로 이동 시작하기](/help/journey-migration/getting-started.md)에서는 AEM as a Cloud Service으로 마이그레이션할 수 있도록 거쳐야 하는 단계 목록을 간략하게 설명합니다. 또한 마이그레이션을 통해 얻을 수 있는 이점에 대해서도 간략히 설명합니다.

## 목표 {#objective}

이 문서는 AEM 설치를 클라우드로 이동할 준비가 되었는지 확인할 수 있도록 고려해야 하는 요소를 이해하는 데 도움이 됩니다.

* 주목할 만한 변경 사항 및 사용되지 않는 기능에 대해 알아봅니다
* AEM as a Cloud Service으로의 마이그레이션을 계획하는 방법 이해

## AEM as a Cloud Service 아키텍처의 주요 변경 내용 검토 {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service은 AEM 프로젝트 관리를 위한 많은 새로운 기능과 가능성을 제공합니다.

이러한 개선 사항과 함께 AEM 및 Adobe Managed Services의 온프레미스 설치 간에 AEM as a Cloud Service과 비교하여 몇 가지 차이점이 도입되었습니다.

아래 표의 항목 목록은 AEM as a Cloud Service으로의 마이그레이션과 가장 관련이 있는 변경 사항의 하위 집합입니다. [Adobe Experience Manager as a Cloud Service의 주요 변경 내용](/help/release-notes/aem-cloud-changes.md)의 전체 목록을 확인할 수 있습니다.

<table>
<thead>
  <tr>
    <th>변경 사항</th>
    <th>참조</th>
    <th>주요 개선 사항</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>변경 가능한 필터 및 변경 불가능한 필터를 해당 패키지로 구분</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html">AEM as a Cloud Service 주요 변경 사항</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM as a Cloud Service의 AEM 프로젝트 구조</a></td>
    <td>AEM as a Cloud Service에 배포할 수 있는 단일 패키지에는 하위 패키지가 있을 수 있으며, 주로 고유한 패키지로 구분된 변경 가능한 콘텐츠 및 변경 불가능한 콘텐츠를 포함합니다.</td>
  </tr>
  <tr>
    <td>초기 보고서</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Apache Sling RepoInit 설명서</a></td>
    <td>Repoinit 스크립트는 초기 노드 구조, 사용자, 그룹 또는 서비스 사용자를 만드는 가장 좋은 방법입니다. 이러한 스크립트는 실행 모드별로 타깃팅하고 코드 패키지 배포를 통해 관리할 수 있으므로 저장소 초기화 작업을 수행하는 데 많은 유연성을 제공합니다.</td>
  </tr>
  <tr>
    <td>사용자 지정 실행 모드가 허용되지 않습니다.</td>
    <td></td>
    <td>AEM as a Cloud Service에서 즉시 제공되는 실행 모드만 지원됩니다.<br>추가 개발 환경이 추가되면 모두 "개발" 실행 모드에 연결됩니다.</td>
  </tr>
  <tr>
    <td>Cloud Manager 파이프라인 실행만이 배포할 수 있는 유일한 방법입니다.</td>
    <td></td>
    <td>AEM as a Cloud Service에서는 /system/console에 대한 액세스가 허용되지 않으므로 모든 OSGi 구성은 코드의 일부여야 하며 코드로 배포해야 합니다.<br>OSGi 구성은 Cloud Manager을 통해 Developer Console을 통해 볼 수 있는 읽기 전용 모드로 사용할 수 있습니다</td>
  </tr>
  <tr>
    <td>복제 에이전트가 Sling 콘텐츠 배포로 대체됨</td>
    <td></td>
    <td>복제 에이전트의 개념은 컨텐츠 배포 사용(Sing Content Distribution)으로 대체됩니다. 복제 에이전트를 사용하는 사용자 정의가 있는 경우 다시 디자인해야 합니다.<br>역방향 복제는 지원되지 않습니다.</td>
  </tr>
  <tr>
    <td>CRX/DE 및 패키지 관리자</td>
    <td></td>
    <td>CRX/DE는 개발 환경에서만 허용됩니다.<br>패키지 관리자는 모든 작성자 인스턴스에서 액세스할 수 있지만 배포될 패키지에는 변경 가능한 콘텐츠만 포함되어야 합니다(예: /content 또는 /conf).</td>
  </tr>
  <tr>
    <td>내장 CDN 및 자체 CDN 받기</td>
    <td></td>
    <td>AEM as a Cloud Service에는 대부분의 사용 사례에 맞게 최적화된 모든 환경의 CDN이 포함되어 있습니다.<br>자체 CDN을 설정하려면 Adobe 지원 팀에 승인을 요청해야 합니다.<br>승인되면 CDN은 모든 환경의 AEM 인스턴스가 아니라 Fastly를 가리킵니다.</td>
  </tr>
  <tr>
    <td>장기 실행 작업</td>
    <td></td>
    <td>컨테이너에서 실행되는 AEM 인스턴스는 언제든지 왔다 갔다 할 수 있으므로 슬링 스케줄러 또는 크론 작업과 같은 장기 실행 작업은 피하십시오.<br>이러한 기능을 Adobe Developer으로 오프로드할 수 있도록 다시 생각해 보십시오.</td>
  </tr>
  <tr>
    <td>비동기 작업으로 전환</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/asynchronous-jobs.html#configuring-asynchronous-msm-operations">비동기 작업 구성</a></td>
    <td>환경의 전체 성능을 향상시키기 위해 특정 작업은 비동기 모드에서 실행됩니다. 비동기 작업은 시스템 리소스를 사용할 수 있을 때 큐에 추가되어 실행됩니다.</td>
  </tr>
  <tr>
    <td>토큰 기반 인증 및 통합 전략</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html#the-server-to-server-flow">서버측 API에 대한 액세스 토큰 생성</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication">토큰 기반 인증 자습서</a></td>
    <td>AEM 외부의 시스템은 AEM 내에서 HTTP 작업을 수행하려고 하는 것이 일반적입니다.<br>AEM에서 암호를 사용하여 로컬 사용자 이름을 만드는 대신 여기에 설명된 전략을 구현하는 것이 좋습니다.</td>
  </tr>
  <tr>
    <td>파일 IO/디스크 사용</td>
    <td></td>
    <td>할당된 디스크 공간의 양을 보장할 수 없으며 컨테이너의 인스턴스는 왔다 갔다 합니다. 따라서 파일 I/O 작업을 사용하여 AEM 인스턴스에 연결된 디스크에서 쓰거나 읽는 것은 권장되지 않습니다.</td>
  </tr>
  <tr>
    <td>DAM 자산 업데이트 워크플로우</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html">Asset compute 서비스</a></td>
    <td>DAM 자산 업데이트 워크플로우의 일부인 미디어 처리 단계가 이제 Asset compute 서비스로 대체됩니다</td>
  </tr>
  <tr>
    <td>AEM as a Cloud Service의 에셋 업로드 방법 및 지원되는 워크플로 프로세스 단계</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis.html#post-processing-workflows-steps">API 비교 및 지원되는 WF 프로세스 단계 업로드</a></td>
    <td>AEM as a Cloud Service에서 에셋의 업로드 또는 다운로드 중에 에셋이 바이너리 스토리지에서 바로 또는 바이너리 스토리지 외부로 스트리밍됩니다. <br>일부 워크플로 프로세스 단계는 AEMaaCS에서 지원되지 않습니다.</td>
  </tr>
  <tr>
    <td>워크플로 런처</td>
    <td></td>
    <td>코드에서 기본 제공 또는 사용자 지정 DAM 자산 업데이트 워크플로우를 트리거하는 워크플로우 런처를 제거합니다. <br>AEM as a Cloud Service에 업로드된 모든 자산은 자산 처리 서비스에서 처리됩니다. 사용자 지정 단계는 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows"> 사후 처리 워크플로</a>에서 사후 처리 워크플로를 설정하고 구성하는 방법을 참조하십시오.</td>
  </tr>
  <tr>
    <td>사용자 지정 렌디션 단계</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html">처리 프로필</a></td>
    <td>사용자 지정 렌디션 생성, 이미지 변환 또는 비디오 인코딩은 해당 처리 프로필을 만들어 Asset Processing Service로 오프로드해야 합니다.</td>
  </tr>
  <tr>
    <td>콘텐츠 검색 및 색인화</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html">콘텐츠 검색 및 색인화 변경 사항</a></td>
    <td>인덱스의 기본 처리 및 시작 시기에 상당한 변화가 있습니다.<br>배포하는 코드에서 관리하기 전에 Oak 색인을 완전히 이해하고 리팩터링합니다.</td>
  </tr>
  <tr>
    <td>일부 유지 관리 작업은 구성할 수 없음</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/maintenance.html">AEM as a Cloud Service 유지 관리 작업</a></td>
    <td>AEM as a Cloud Service에서는 특정 유지 관리 작업만 구성할 수 있습니다.</td>
  </tr>
  <tr>
    <td>Publish 저장소 변경 사항</td>
    <td></td>
    <td>/home 아래의 변경 사항을 제외하고는 Publish 저장소에 대한 직접 변경은 허용되지 않습니다. 작성자의 모든 변경 사항을 배포하는 것이 좋습니다. 모든 코드 및 구성 변경 사항은 해당 Cloud Manager 파이프라인을 통해 배포되어야 합니다.</td>
  </tr>
  <tr>
    <td>Dispatcher 구성 및 캐싱</td>
    <td>클라우드의 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html">Dispatcher</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/caching.html#other-content">캐시 관리<br></td>
    <td>Dispatcher 구성은 특정 구조를 따라야 합니다.<br>구성을 코드의 일부로 관리하고 Cloud Manager 파이프라인을 통해 배포해야 합니다.</td>
  </tr>
  <tr>
    <td>백업 및 복원</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html">AEM as a Cloud Service 백업 및 복원</a></td>
    <td></td>
  </tr>
  <tr>
    <td>인증 변경 사항</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html">AEM as a Cloud Service에 대한 IMS 지원</td>
    <td>Cloud Service으로 이동하기 전에 작성자와 게시 모두에서 SAML 2.0 통합을 이전에 사용 중이었던 경우 주요 변경 사항은 AEM as a Cloud Service 작성자가 Adobe IMS와만 통합된다는 것입니다. 그러나 AEM as a Cloud Service Publish 계층은 여전히 SAML 또는 기타 인증 통합을 사용할 수 있습니다. AEM as a Cloud Service에서는 작성자, 관리 및 개발 사용자에 대해서만 IMS 인증 지원 서비스를 제공합니다. IMS 인증은 사이트 방문자와 같은 고객 사이트의 외부 최종 사용자를 지원하지 않습니다.</td>
  </tr>
</tbody>
</table>

## 더 이상 사용되지 않는 기능 {#deprecated-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다.

Adobe은 [사용되지 않는 기능](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html#deprecated-features)을 참조하여 Experience Manageras a Cloud Service 에서 더 이상 사용되지 않는 것으로 표시된 기능을 숙지할 것을 권장합니다. AEM 배포에 어떤 영향이 있는지 확인하십시오.

## AEM 설치 검토 계획 {#review-planning}

AEM as a Cloud Service에 도입된 변경 사항을 숙지한 후에는 기존 설치에 대한 검토 계획을 시작할 수 있습니다. 이렇게 하면 클라우드로 이동하는 데 필요한 변경 사항의 수준을 측정하는 데 도움이 됩니다.

다음 그림은 검토 단계 중에 포함된 주요 단계를 보여줍니다.

![검토 단계 중에 포함된 주요 단계](/help/journey-migration/assets/planning-phaseimg1.png)

다음으로 이러한 각 단계가 무엇을 의미하는지 자세히 살펴봅니다.

### Cloud Service 준비 평가 {#assess-cloud-readiness}

첫 번째 단계는 기존 AEM 버전에서 Cloud Service으로 이동할 준비를 평가하고 리팩터링이 AEM as a Cloud Service과 호환되어야 하는 영역을 결정하는 것입니다.

주요 변경 사항 및 더 이상 사용되지 않는 기능에 대해 현재 AEM 소스 코드에 대한 포괄적인 평가를 수행하여 전환 여정에서 예상되는 작업 수준을 결정합니다.

결과의 수는 타임라인 및 전체 프로젝트 성공에 직접적인 영향을 미칠 수 있습니다. 따라서 Adobe은 게재를 계획할 수 있도록 가능한 한 많이 찾는 것을 권장합니다. 또는 대화를 시작하여 AEM as a Cloud Service 모범 사례에 맞게 필요한 사용자 지정 사항을 다시 디자인할 수 있습니다.

**모범 사례 분석기**

현재 AEM 버전에 대해 모범 사례 분석기를 실행하여 평가를 가속화할 수 있습니다. 어떻게 작동하는지 잘 이해하는 것은 평가 계획을 가속화하는 데 중요합니다.

[모범 사례 분석기](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) 설명서를 참조하여 작동 방식을 확인할 수 있습니다.

**클라우드 준비 평가 보고서 만들기**

다음 단계는 지금까지 얻은 모든 지식을 기반으로 보고서를 만드는 것입니다. 단계 및 프로덕션 인스턴스에서 모범 사례 분석기 보고서를 생성하여 보고서를 만들고, [실행 가능한 항목에 대한 간단한 보고서를 위해 Cloud Acceleration Manager에 업로드합니다](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam).

일반적인 보고서에는 다음 입력이 포함되어야 합니다.

* 특정 AEM 설치의 기능 세트를 자세히 설명하는 설명서
* AEM 사용자 지정 구성 및 코드에 대한 세부 사항
* 프로덕션 Dispatcher 구성
* CDN 구성 (있는 경우)

**보고서 연결**

모범 사례 분석기 보고서가 완료되면 관련 팀과 공유하여 결과를 확인하고 다음 단계를 계획할 수 있습니다. 환경 설정에 따라 [인쇄 미리 보기](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam)를 사용하여 인쇄된 버전의 보고서를 배포할 수도 있습니다.

### 리소스 계획 검토 {#review-resource-planning}

Cloud Service으로 이동하는 데 필요한 작업 수준을 예측했으면 리소스를 식별하고, 팀을 만들고, 전환 프로세스에 대한 역할과 책임을 매핑해야 합니다.

### KPI 설정 {#establish-kpis}

이전에 KPI(주요 성과 지표)를 설정하지 않은 경우 AEM 구현에 대한 KPI를 설정하여 팀이 가장 중요한 사항에 집중할 수 있도록 하는 것이 좋습니다.

비즈니스 목표에 적합한 KPI를 선택하는 방법에 대해 알아보려면 [KPI 개발](https://experienceleague.adobe.com/welcome/aem/part6.html)을 참조하십시오.

## 다음 단계 {#what-is-next}

AEM as a Cloud Service으로 이동하는 데 필요한 변경 사항의 범위를 이해했으면 실제로 마이그레이션을 수행하기 전에 [코드 및 콘텐츠 클라우드를 준비](/help/journey-migration/implementation.md)할 차례입니다.

## 추가 리소스 {#additional-resources}

* [Cloud Acceleration Manager 시작하기](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Cloud Acceleration Manager을 사용하여 클라우드로의 이동 속도를 높이는 방법에 대한 포괄적인 안내서입니다.
* [AEM as a Cloud Service: 소개, 아키텍처 및 다른 생각](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=en#dashboard/learning)
* [Cloud Service 홈 AEM](/help/overview/introduction.md) - Experience Manager as a Cloud Service 설명서에 대한 개요를 보려면 여기에서 시작하십시오.
* [AEM as a Cloud Service 개요](/help/overview/introduction.md) - 이 안내서에서는 소개, 용어 및 아키텍처를 포함하여 Experience Manager as a Cloud Service에 대한 개요를 제공합니다.
* [온보딩 여정](/help/journey-onboarding/overview.md)- 이 안내서에서는 Experience Manager as a Cloud Service을 시작하는 방법과 액세스 및 팀 설정 방법에 대한 요약을 제공합니다.
