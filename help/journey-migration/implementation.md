---
title: 구현 단계
description: 코드 및 콘텐츠를 클라우드로 마이그레이션할 준비가 되었는지 확인
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
source-git-commit: fedaa9b8a7baf707c71acd0535ad890254b6793a
workflow-type: tm+mt
source-wordcount: '2353'
ht-degree: 9%

---

# 구현 단계 {#implementation-phase}

여정의 구현 단계에서는 AEM as a Cloud Service으로 이동할 준비가 된 코드 및 콘텐츠를 만들 수 있는 도구를 살펴봅니다.

## 지금까지의 스토리 {#story-so-far}

여정의 이전 부분에서 다음을 수행했습니다. [AEM as a Cloud Service의 변경 사항에 익숙해지기](/help/journey-migration/getting-started.md)를 사용하여 배포를 클라우드로 이동할 준비가 되었는지 확인할 수 있습니다. [준비 단계](/help/journey-migration/readiness.md).

이 문서는 코드 및 콘텐츠를 클라우드로 이동할 준비가 되었는지 확인하기 위해 Adobe 제공 도구를 사용하는 방법에 대한 조언을 계속 제공합니다.

## 목표 {#objective}

이 문서의 목적은 다음과 같습니다.

* AEM as a Cloud Service으로 코드를 배포하는 데 사용되는 Cloud Manager, AEM 연속 통합 및 게재 프레임워크를 소개합니다
* 콘텐츠 전송 도구를 통해 최신 정보 제공
* AEM as a Cloud Service으로 코드를 현대화하기 위해 사용해야 하는 코드 리팩터링 도구에 대해 설명합니다

## Cloud Manager 사용 {#using-cloud-manager}

시작하기 전에 Cloud Manager가 AEM에 코드를 as a Cloud Service으로 배포하는 유일한 메커니즘이므로 숙지해야 합니다.

조직에서 Cloud Manager를 사용하여 클라우드에서 AEM을 자체 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다.

아래 리소스를 참조하여 Cloud Manager 사용에 익숙해질 수 있습니다.

* [온보딩 여정](/help/journey-onboarding/overview.md) Experience Manager as a Cloud Service 온보딩에 대한 자가 진단 리소스를 이해합니다.

* [Git와 Adobe Cloud Manager 통합](/help/implementing/cloud-manager/managing-code/integrating-with-git.md): 단일 Git 저장소를 사용하여 코드 배포에 대해 자세히 알아봅니다.

* [Adobe Experience as a Cloud Service 구성](/help/security/ims-support.md#aem-configuration): Admin Console에서 제품 및 사용자 액세스 관리에 대해 알아봅니다.

## Adobe 제공 도구를 사용하여 콘텐츠 및 코드 클라우드를 준비하십시오. {#use-tools-to-make-code-and-content-cloud-ready}

Cloud Service으로 전환하는 정확한 단계는 구입한 시스템과 사용자가 따르는 소프트웨어 개발 수명 주기 방침에 따라 다릅니다.

다음 그림은 AEM에서 사용할 코드 및 콘텐츠를 as a Cloud Service으로 변환하는 단계와 관련된 주요 단계를 보여 줍니다.

![이미지](/help/journey-migration/assets/exec-image1.png)

이를 위해 아래 단원에서 사용해야 하는 도구에 대해 자세히 설명하겠습니다.

## 콘텐츠 마이그레이션 {#content-migration}

현재 AEM 인스턴스에서 Cloud Service 인스턴스로 콘텐츠를 마이그레이션하려면 Adobe의 콘텐츠 전송 도구를 사용할 수 있습니다.

이 도구를 사용하여 소스 AEM 인스턴스에서 AEM 클라우드 서비스 인스턴스로 전송하려는 컨텐츠 하위 집합을 지정할 수 있습니다.

콘텐츠 마이그레이션은 여러 팀 간의 계획, 추적 및 협업이 필요한 여러 단계로 진행되는 프로세스입니다.

도구 작동 방식과 권장 사용 방법에 대한 자세한 내용은 [컨텐츠 전송 도구 설명서](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## 코드 리팩터링 {#code-refactor}

### 개발을 위한 설정 {#set-up-for-development}

이제 Cloud Services과 호환될 수 있도록 기존 기능을 리팩터링할 때입니다.

이렇게 하려면 코드 리팩터링을 시작해야 하는 기본 도구에 대해 자세히 설명하는 설명서를 살펴야 합니다.


* 계획 중에 AEM as a Cloud Service과 호환되도록 리팩터링해야 하는 영역 목록을 갖는 것이 좋습니다. 다음을 검토할 수 있습니다. [개발 지침](/help/implementing/developing/introduction/development-guidelines.md) Cloud Service을 위해 코드를 리팩터링하고 최적화하는 방법에 대한 자세한 내용.
* 방법 자세히 알아보기 [구성 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=en#what-is-a-configuration) AEM에서 as a Cloud Service.
* 를 다운로드하여 로컬 개발 환경을 설정하는 방법에 대해 알아봅니다. [AEM AS A CLOUD SERVICE SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en)
* 마지막으로, 다음을 숙지하십시오. [AEM as a Cloud Service Java API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

또한 다음을 수행할 수도 있습니다.

* 이 비디오를 통해 로컬에서 Dispatcher SDK를 설치하는 방법을 알아보십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Dispatcher SDK를 구성하는 방법을 이해하려면 이 비디오를 시청하십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

### 마음가짐의 변화 {#a-change-in-mindset}

AEM as a Cloud Service으로 코드를 개발하고 실행하려면 사고방식의 변화가 필요합니다. 특히 인스턴스가 언제든지 중지될 수 있으므로 코드가 복원력이 있어야 합니다. 클라우드 서비스에서 실행 중인 코드는 항상 클러스터에서 실행되고 있다는 것을 알고 있어야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다.

AEM Maven 프로젝트가 클라우드와 호환되려면 특정 변경 사항이 필요합니다. AEM as a Cloud Service에는 *콘텐츠* 및 *코드* AEM에 배포할 개별 패키지로

* `/apps` 및 `/libs` 는 AEM 시작 후(즉, 런타임 시) 변경할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다. 여기에는 만들기, 업데이트 또는 삭제 작업이 포함됩니다. 런타임 시 변경할 수 없는 영역을 변경하려고 하면 오류가 발생합니다.

* 저장소의 다른 모든 항목(예: `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`)는 모두 변경할 수 있는 영역입니다. 즉, 런타임 시 변경할 수 있습니다.

자세한 내용은 다음을 참조하십시오 [권장 패키지 구조](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure) 설명서를 참조하십시오.


### 클라우드 마이그레이션 도구 {#cloud-migration-tools}

Adobe은 일부 코드 리팩터링 작업을 가속화하는 데 도움이 되는 몇 가지 도구를 제공합니다. 이러한 툴과 툴이 해결하는 문제를 이해하면 마이그레이션 복잡성과 시간이 줄어듭니다.

* [자산 워크플로우 마이그레이션](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md): 자산 처리 워크플로우를 자동으로 마이그레이션하는 데 사용되는 도구입니다
* [Dispatcher 변환기](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md): 기존 Dispatcher 구성을 AEM as a Cloud Service으로 사용할 수 있는 형식으로 변환하는 도구입니다.
* [저장소 현대화 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=en): AEM 다중 모드 프로젝트를 입력으로 취하여 AEM as a Cloud Service 프로젝트로 변환하는 도구입니다
* [인덱스 변환기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=en): 인덱스를 AEM as a Cloud Service과 호환되는 양식으로 변환하는 도구입니다
* [현대화 도구](/help/journey-migration/refactoring-tools/aem-modernization-tools.md): 기존 AEM 기능을 AEMas a Cloud Service 의 현대적이고 지원되는 기능으로 변환하는 데 사용할 수 있는 유틸리티의 세트입니다.

로컬 개발 환경을 설정했으면 를 참조하여 AEM as a Cloud Service SDK에 익숙해집니다. [설명서](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

### 코드 고정 예약 {#schedule-a-code-freeze}

전환 여정의 일부로 코드 리팩터링 작업과 함께 활성 AEM에서 진행 중인 코드 개발을 관리하려면, AEM as a Cloud Service과 호환되도록 Maven 프로젝트 재구성을 완료할 때까지 코드 동결 기간을 예약하는 것이 좋습니다.

프로젝트 재구성이 완료되면 이 새 구조를 기반으로 새 코드 개발을 재개할 수 있습니다. 이렇게 하면 코드 배포 및 테스트 중 Cloud Manager 파이프라인 오류가 줄어듭니다.

>[!NOTE]
>컨텐츠 전송 및 코드 리팩터링 작업은 순차적으로 수행하지 않아도 됩니다. 이러한 작업은 서로 독립적으로 수행할 수 있습니다. 그러나 컨텐츠가 클라우드 서비스 환경에서 성공적으로 렌더링되도록 하려면 올바른 프로젝트 구조가 필요합니다.

## 코드 배포 및 테스트 우수 사례 {#best-practices}

Cloud Manager 파이프라인은 스테이지 환경에 대해 실행되는 테스트 실행을 지원합니다.

코드 품질 테스트에 대한 아래 문서의 모범 사례를 따르십시오.

* [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)는 테스트 스크립트를 작성하는 프로세스를 설명하고 최소 50%의 권장 적용 범위의 개념을 설명하는 문서입니다.
* [사용자 지정 코드 품질 규칙 이해](/help/implementing/cloud-manager/custom-code-quality-rules.md) AEM Engineering의 모범 사례를 기반으로 작성된 Cloud Manager에서 실행되는 사용자 정의 코드 품질 규칙 을 설명하는 것이 목적입니다.

## Go-Live 준비 {#preparing-for-go-live}

마이그레이션을 위한 소스 시스템을 준비하려면 시스템 및 AEM 관리자 수준 작업이 필요합니다. 먼저 다음을 확인하여 콘텐츠 저장소가 유지 관리 상태가 양호한지 확인할 수 있습니다. [개정 정리](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) 및 [데이터 저장소 가비지 수집](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html) 작업 상태. 컨텐츠 전송 도구가 버전 6.3부터 호환되므로 AEM 버전 6.3을 실행 중인 경우 오프라인 압축을 수행한 다음 데이터 저장소 가비지 수집을 수행하는 것이 좋습니다.

[데이터 일관성 검사](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html) 모든 AEM 버전에서 콘텐츠 저장소가 마이그레이션 활동을 시작하기에 좋은 상태인지 확인하는 것이 좋습니다.

설치 및 구성하려면 시스템 관리자 수준 액세스 권한이 필요합니다. [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)

또한 사용하지 않은 자산, 페이지, AEM 프로젝트, 사용자 및 그룹을 검토하여 마이그레이션 시간을 절약하는 것이 좋습니다. 다음을 참조하십시오. [콘텐츠 저장소 상태](#repository-health) 섹션.

### 콘텐츠 저장소 상태 {#repository-health}

에 대한 액세스 권한 부여 [운영 클론](#proof-of-migration) 이(가) 설정되어 있습니다. 저장소의 상태를 확인하려면 계속 진행하십시오. 이전 섹션에서 언급했듯이 마이그레이션이 시작되기 전에 소스에서 저장소를 정리하고 압축하는 것이 목표입니다. 이 단계를 수행하면 마이그레이션이 시작된 후 문제를 해결하는 데 드는 시간을 절약할 수 있습니다.

| 작업 항목 | 주요 개선 사항 |
|---------|----------|
| 사용자, 그룹 및 권한 | 사용자, 그룹 및 멤버십의 복잡성에 대해 이해해야 합니다. 마이그레이션 전에 소스에서 사용하지 않는 사용자, 그룹을 정리할 수 있는 기회를 찾습니다. |
| 불완전한 자산 처리 | 마이그레이션을 시작하기 전에 소스 시스템에서 자산 처리를 완료하여 AEM as a Cloud Service 사후 마이그레이션에서 발생할 수 있는 문제를 방지하십시오. |
| 콘텐츠 상태 | 마이그레이션을 시작하기 전에 잘못된 콘텐츠를 쿼리하고 제거하는 것이 좋습니다. 예를 들어 원본 렌디션이 없거나 워크플로우 처리에 남아 있는 에셋 또는 페이지를 찾습니다. 추가 정보 [에셋 상태](#asset-health). |

## 데이터 수집 중 {#gathering-data}

>[!NOTE]
> 다음 [컨텐츠 마이그레이션 전략 및 타임라인](#content-strategy-and-timeline) 이 섹션에서는 수집된 데이터를 외삽하고 마이그레이션 계획을 만드는 방법에 대해 자세히 설명합니다.

데이터를 수집하면 마이그레이션 활동 및 관련 작업을 계획하는 데 도움이 될 수 있습니다. 데이터 포인트를 마이그레이션 세트의 특정 크기와 연결할 수 있으므로 추출 및 수집 시간이 특히 유용합니다. 따라서 다음 데이터 포인트를 외삽하여 계획을 수립할 수 있습니다.

* 에 대해 걸린 총 시간 [추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* 에 대해 걸린 총 시간 [수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* 추가 작업에 소요된 총 시간 [추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
* 추가 작업에 소요된 총 시간 [수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)


<!-- Alexandru: hiding this for now

One more important datapoint is the amount of time it takes to complete the [user mapping](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), if this is coupled with the content migration. You can take this data point into consideration for more realistic estimates, since it will be added to the overall extraction timeline and it may not be required to run it during top-ups.

-->

이러한 데이터 포인트는 다음 작업에도 유용합니다. [KPI 설정](/help/journey-migration/readiness.md#establish-kpis) 및 기타 마이그레이션 관련 작업.

### 마이그레이션 계획 {#migration-plan}

수집한 데이터 포인트(위 참조)를 기반으로 매크로 프로젝트 계획에 통합할 수 있는 마이그레이션 계획을 만들 수 있습니다. 이 단계를 통해 모든 주요 이해 당사자는 마이그레이션 활동을 시각화하고 계획할 수 있습니다.

다음 표는 일반적인 마이그레이션 계획을 보여 줍니다.

| 마이그레이션 반복 | 시작 날짜 | 예상 종료 일자 | 종속성 | 예상 기간(일) | 추가 세부 정보/작업 항목 |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |  |  |  |  |  |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |  |  |  |  |  |

위의 표에서 볼 수 있듯이 특정 이름 지정 형식을 따라 마이그레이션 반복을 식별하는 것이 유용합니다. 예를 들면 다음과 같습니다. **PRDCLONE** 소스 AEM 환경용 **작성자/게시** AEM as a Cloud Service 환경의 경우 **CSSTAGE-AUTHOR** AEM as a Cloud Service 인스턴스 등등.

마이그레이션 계획에 영향을 주는 몇 가지 중요한 세부 정보:

**필요한 총 추출 수**

* 특정 환경의 작성자 및 게시 추출은 서로 독립적이므로 두 개의 병렬 추출로 간주됩니다.
* 특정 기간의 저장소 증가를 기반으로 하는 추가 추출 수입니다.

**필요한 총 수집 수**

* 추출된 세트는 여러 Cloud Service 환경으로 수집할 수 있으므로 이 항목을 플랜에 캡처하는 것이 중요합니다.
* 추가 수집 수.
* 소스 작성자에서 Cloud Service 작성자 인스턴스로 콘텐츠를 마이그레이션하고 소스 게시에서 Cloud Service 게시로 콘텐츠를 마이그레이션하는 것은 모든 작성자 콘텐츠를 Cloud Service 게시로 수집하지 않는 가장 좋은 방법입니다.

### 마이그레이션 추적기 {#migration-tracker}

마이그레이션 추적기를 사용하여 초기 실행과 위로 실행 모두에 대한 시간을 기록할 수 있습니다. 이러한 데이터 포인트는 최종 추가 작업 전에 사실적인 콘텐츠 고정 요구 사항을 작성하는 데 도움이 됩니다.

추적기는 또한 다음을 수행하는 데 도움이 됩니다.

* 계획 또는 Go-Live 타임라인에서 조정이 필요한 계획자의 변경 사항을 식별합니다
* 필요한 모든 통신에 사용할 수 있는 실제 상태 제공
* 초기 또는 향후 추가 마이그레이션 계획

다음 표는 기능 마이그레이션 추적기를 보여 줍니다.

| 소스(환경/인스턴스/URL) | 대상(환경/인스턴스/URL) | 마이그레이션 세트 이름, 유형(초기 또는 추가) | 마이그레이션 세트 크기(MB) | 사용자 매핑 (예 / 아니요) | 추출 기간(시작, 종료, 소요 시간) | 수집 기간(시작, 종료, 소요 시간) | 문제 / 해결 방법 / 세부 정보 |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |

## 컨텐츠 마이그레이션 전략 및 타임라인 {#content-strategyand-timeline}

다음 섹션에서는 컨텐츠 마이그레이션 전략 및 타임라인을 수립하는 데 사용할 수 있는 중요한 단계 및 관련 작업을 보여줍니다.

![이미지](/help/journey-migration/assets/content-migration2.png)

### 장비 {#fitment}

* 개정 정리, 데이터 저장소 가비지 수집 및 데이터 일관성 검사를 수행합니다. 참조: [Go-Live 준비](#preparing-for-go-live)
* [통계 수집](#gathering-data) AEM 소스 리포지토리 정보:
   * 세그먼트 저장소 크기
   * 인덱스 저장소 크기
   * 페이지 수
   * 에셋 수
   * 사용자 및 그룹 수
* AEM 소스에서 다음 기능을 활성화할지(AEM as a Cloud Service에서도 필요) 확인합니다.
   * 스마트 태그 지정
   * 유사성 검색
   * Word 및 PDF 문서에서 포함 텍스트 검색
* Best Practice Analyzer 수집 [보고서](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* 로 가져오기 [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * 자체 분석 권장 사항을 검토하여 AEM에서 스토리지 요구 사항을 as a Cloud Service으로 처리할 수 있는지 확인하십시오.
* 마이그레이션 계획을 계속하기 전에 설명이 필요한 Adobe 지원 티켓을 만드십시오.

### 마이그레이션 증명 {#proof-of-migration}

* 다음과 같은 운영 클론 요청:
   * 동일한 네트워크 영역에 있음
   * 사용자 및 그룹과 같은 프로덕션 콘텐츠를 제공합니다.
   * 작성자 및 게시 복제 - 클러스터 또는 게시 팜의 경우 각각 하나의 노드
* 다음과 같이 마이그레이션할 콘텐츠의 하위 집합을 선택하십시오.
   * 사용 가능한 모든 콘텐츠 유형이 혼합되어 있습니다
   * 모든 사용자 및 그룹 포함
* 컨텐츠의 25% 또는 최대 1TB의 컨텐츠 중 더 적은 것을 포함합니다.
* 하나 이상의 전체 실행 및 [추가](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) 운영 클론에서 AEM as a Cloud Service 비운영 환경으로 마이그레이션
* 다음과 같은 잠재적 문제를 해결합니다.
   * AEM 소스의 디스크 공간
   * AEM 소스와 AEM as a Cloud Service 간의 연결
   * 임의 [수집 관련 제한 사항](go-live.md#known-limitations).
* 다음에 대한 소요 시간 기록 [추출 및 수집](#gathering-data):
   * 일주일에 추가되는 콘텐츠 양을 파악할 수 있습니다.
   * 마이그레이션 증명에서 측정된 시간을 추정하여 다음을 만듭니다. [마이그레이션 계획](#migration-plan).

## 다음 단계 {#what-is-next}

AEM 설치를 클라우드로 이전할 준비가 되었는지 평가하는 방법을 완전히 이해했다면 이를 준비하는 데 필요한 도구를 사용하는 방법에 대해 알아보았으므로 이제 로 넘어갈 차례입니다. [go-live 단계](/help/journey-migration/go-live.md).
