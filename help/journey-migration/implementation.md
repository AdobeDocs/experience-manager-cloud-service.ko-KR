---
title: 구현 단계
description: 코드와 컨텐츠가 클라우드로 마이그레이션할 준비가 되었는지 확인합니다.
source-git-commit: b6667e19ae111685ab4832a1859a62164b4e31c5
workflow-type: tm+mt
source-wordcount: '2422'
ht-degree: 9%

---

# 구현 단계 {#implementation-phase}

여정의 구현 단계에서 코드 및 컨텐츠를 AEM as a Cloud Service 으로 이동할 수 있도록 하는 도구를 살펴봅니다.

## 지금까지 그 이야기 {#story-so-far}

여정의 이전 부분에서 다음을 수행했습니다 [AEM as a Cloud Service의 변경 사항을 잘 알고 있습니다.](/help/journey-migration/getting-started.md)를 사용하여 배포가 클라우드로 이동할 준비가 되었는지 확인할 수 있습니다. [준비 단계](/help/journey-migration/readiness.md).

이 문서는 Adobe에서 제공하는 도구를 사용하여 코드 및 콘텐츠를 클라우드로 이동할 준비가 되었는지 확인하는 방법에 대한 조언을 계속 제공합니다.

## 목표 {#objective}

이 문서는 다음 용도로 사용됩니다.

* AEM as a Cloud Service에 코드를 배포하는 데 사용되는 AEM의 지속적인 통합 및 게재 프레임워크인 Cloud Manager를 소개합니다
* 컨텐츠 전송 도구를 빠르게 사용할 수 있습니다
* AEM as a Cloud Service 코드를 현대화하기 위해 사용해야 하는 코드 리팩터링 도구를 설명합니다.

## Cloud Manager 사용 {#using-cloud-manager}

시작하기 전에 Cloud Manager가 AEM as a Cloud Service에 코드를 배포하는 유일한 메커니즘이므로 Cloud Manager를 숙지해야 합니다.

조직에서 Cloud Manager를 사용하여 클라우드에서 AEM을 자체 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다.

아래 리소스를 참조하여 Cloud Manager 사용을 잘 알 수 있습니다.

* [Experience Manager as a Cloud Service에 온보딩](/help/onboarding/home.md): Experience Manager as a Cloud Service에 온보딩에 대한 셀프 헬프 리소스를 이해합니다.

* [Git와 Adobe Cloud Manager 통합](/help/implementing/cloud-manager/managing-code/integrating-with-git.md): 단일 Git 저장소를 사용하여 코드 배포에 대해 자세히 알아봅니다.

* [Adobe Experience as a Cloud Service 구성](/help/security/ims-support.md#aem-configuration): Admin Console에서 제품 및 사용자 액세스 관리에 대해 알아봅니다.

## 제공된 Adobe 도구를 사용하여 컨텐츠 및 코드 클라우드를 준비합니다. {#use-tools-to-make-code-and-content-cloud-ready}

Cloud Service으로 전환하는 정확한 단계는 구입한 시스템과 사용자가 따르는 소프트웨어 개발 수명 주기 방침에 따라 다릅니다.

다음 그림은 AEM as a Cloud Service에서 사용할 코드와 컨텐츠를 변환하는 단계에 포함된 주요 단계를 보여줍니다.

![이미지](/help/journey-migration/assets/exec-image1.png)

아래 장에서 이를 수행하기 위해 사용해야 하는 도구에 대해 자세히 설명하는 작업을 시작할 것입니다.

## 콘텐츠 마이그레이션 {#content-migration}

현재 AEM 인스턴스에서 Cloud Service 인스턴스로 컨텐츠를 마이그레이션하기 위해 Adobe의 컨텐츠 전송 도구를 사용할 수 있습니다.

이 도구를 사용하여 소스 AEM 인스턴스에서 AEM 클라우드 서비스 인스턴스로 전송하려는 컨텐츠 하위 집합을 지정할 수 있습니다.

컨텐츠 마이그레이션은 여러 팀 간의 계획, 추적 및 공동 작업이 필요한 여러 단계로 진행되는 프로세스입니다.

도구 작동 방법 및 도구 사용 권장 방법에 대한 자세한 내용은 [컨텐츠 전송 도구 설명서](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## 코드 리팩터링 {#code-refactor}

### 개발을 위한 설정 {#set-up-for-development}

Cloud Services과 호환될 기존 기능의 리팩터링을 시작할 차례입니다.

이렇게 하려면 코드 리팩터링을 시작하는 데 필요한 기본 도구에 대한 설명서를 확인해야 합니다.


* 계획 중에 AEM as a Cloud Service과 호환되도록 리팩터링해야 하는 영역 목록이 있는 것이 좋습니다. 검토하실 수 있습니다 [개발 지침](/help/implementing/developing/introduction/development-guidelines.md) 를 위해 코드를 리팩터링하고 최적화하는 방법에 대한 자세한 내용.
* 방법 읽기 [구성 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=en#what-is-a-configuration) AEM as a Cloud Service.
* 를 다운로드하여 로컬 개발 환경을 설정하는 방법을 알아봅니다. [AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en)
* 마지막으로, 를 숙지하십시오. [AEM as a Cloud Service Java API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

또한 다음을 수행할 수도 있습니다.

* 이 비디오를 시청하여 Dispatcher SDK를 로컬로 설치하는 방법을 알아보십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* 이 비디오를 시청하여 Dispatcher SDK를 구성하는 방법을 알아보십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

### 사고방식의 변화 {#a-change-in-mindset}

AEM as a Cloud Service에서 코드를 개발하고 실행하려면 사고방식을 변경해야 합니다. 특히 인스턴스가 언제든지 중지될 수 있으므로 코드가 복원력이 있어야 합니다. 클라우드 서비스에서 실행 중인 코드는 항상 클러스터에서 실행되고 있다는 것을 알고 있어야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다.

AEM Maven 프로젝트가 클라우드 호환되도록 하려면 특정 변경 사항이 필요합니다. AEM as a Cloud Service은 *콘텐츠* 및 *코드* AEM에 배포하기 위한 개별 패키지:

* `/apps` 및 `/libs` AEM이 시작된 후(즉, 런타임 시) 변경할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다. 여기에는 만들기, 업데이트 또는 삭제 작업이 포함됩니다. 런타임 시 변경할 수 없는 영역을 변경하려고 하면 오류가 발생합니다.

* 저장소의 다른 모든 것(예: `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`)는 모두 변경할 수 있는 영역입니다. 즉, 런타임 시 변경할 수 있습니다.

자세한 내용은 [권장 패키지 구조](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure) 설명서.


### 클라우드 마이그레이션 도구 {#cloud-migration-tools}

Adobe은 코드 리팩터링 작업 중 일부를 가속화하는 데 도움이 되는 몇 가지 도구를 제공합니다. 이러한 툴과 이러한 툴이 해결할 문제를 이해하면 마이그레이션의 복잡성과 시간이 줄어듭니다.

* [자산 워크플로우 마이그레이션](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), 자산 처리 워크플로우를 자동으로 마이그레이션하는 데 사용되는 도구입니다
* [Dispatcher 변환기](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md): 기존 Dispatcher 구성을 AEM as a Cloud Service에 사용할 수 있는 형식으로 변환하는 도구입니다.
* [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=en): AEM Multimode 프로젝트를 입력으로 가져와 AEM as a Cloud Service one로 변환하는 도구입니다
* [인덱스 변환기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=en): 인덱스를 AEM as a Cloud Service과 호환되는 양식으로 변환하는 도구입니다
* [현대화 도구](/help/journey-migration/refactoring-tools/aem-modernization-tools.md): 기존 AEM 기능을 AEM as a Cloud Service의 최신 및 지원되는 기능으로 변환하는 데 사용할 수 있는 유틸리티 세트입니다.

로컬 개발 환경을 설정했으면 를 참조하여 AEM as a Cloud Service SDK를 숙지하십시오. [설명서](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

### 코드 동결 예약 {#schedule-a-code-freeze}

전환 여정의 일부로 코드 리팩터링 작업과 함께 활성 AEM에서 진행 중인 코드 개발을 관리하려면, AEM과 호환되도록 Maven 프로젝트 재구성을 완료할 때까지 코드 동결 기간을 예약하는 것이 좋습니다.

프로젝트 재구성이 완료되면 이 새 구조를 기반으로 새 코드 개발을 재개할 수 있습니다. 이렇게 하면 코드 배포 및 테스트 중 Cloud Manager 파이프라인 오류가 줄어듭니다.

>[!NOTE]
>컨텐츠 전송 및 코드 리팩터링 작업은 순차적으로 수행하지 않아도 됩니다. 이러한 작업은 서로 독립적으로 수행할 수 있습니다. 그러나 컨텐츠가 클라우드 서비스 환경에서 성공적으로 렌더링되도록 하려면 올바른 프로젝트 구조가 필요합니다.

## 코드 배포 및 테스트 우수 사례 {#best-practices}

Cloud Manager 파이프라인은 스테이지 환경에서 실행되는 테스트 실행을 지원합니다.

코드 품질 테스트에 대한 아래 문서의 우수 사례를 따르십시오.

* [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)은 테스트 스크립트 작성 프로세스를 설명하고 최소 50%의 권장 적용 범위의 개념을 설명하는 문서입니다.
* [사용자 지정 코드 품질 규칙 이해](/help/implementing/cloud-manager/custom-code-quality-rules.md) 는 AEM Engineering의 우수 사례를 기반으로 작성된 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙을 설명하는 것을 목표로 합니다.

## Go-Live 준비 {#preparing-for-go-live}

마이그레이션을 위한 소스 시스템 준비에는 시스템 및 AEM 관리자 수준 작업이 포함됩니다. 먼저 을 확인하여 컨텐츠 리포지토리가 잘 관리 상태인지 확인할 수 있습니다. [개정 정리](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) 그리고 [데이터 저장소 가비지 수집](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html) 작업 상태. AEM 버전 6.3을 실행 중인 경우(컨텐츠 전송 도구는 버전 6.3 이상에서 호환되므로) 오프라인 압축을 수행한 후 데이터 저장소 가비지 수집을 수행하는 것이 좋습니다.

[데이터 일관성 확인](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html) 컨텐츠 저장소가 마이그레이션 활동을 시작할 수 있도록 모든 AEM 버전에서 이 권장됩니다.

설치 및 구성하려면 시스템 관리자 수준 액세스 권한이 필요합니다 [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)

또한 사용하지 않은 자산, 페이지, AEM 프로젝트, 사용자 및 그룹을 검토하여 마이그레이션 시 시간을 절약하는 것이 좋습니다. 자세한 내용은 [컨텐츠 저장소 상태](#repository-health) 섹션을 참조하십시오.

### 컨텐츠 저장소 상태 {#repository-health}

다음에 액세스하면 [프로덕션 클론](#proof-of-migration) 저장소 상태를 확인하기 위해 진행 중입니다. 이전 섹션에서 언급했듯이 목표는 마이그레이션을 시작하기 전에 소스에서 리포지토리를 정리하고 압축하는 것입니다. 이 단계에서는 마이그레이션이 시작되면 문제를 해결하는 데 많은 시간을 절약할 수 있습니다.

| 작업 항목 | 주요 사항 |
|---------|----------|
| 사용자, 그룹 및 권한 | 멤버십에 대한 사용자, 그룹 및 복잡도를 이해해야 합니다. 마이그레이션 전에 소스에서 사용하지 않은 사용자, 그룹을 정리할 수 있는 기회를 찾습니다. |
| 불완전한 자산 처리 | AEM as a Cloud Service post 마이그레이션의 잠재적인 문제를 방지하기 위해 마이그레이션을 시작하기 전에 소스 시스템에서 자산 처리를 완료해 보십시오. |
| 컨텐츠 상태 | 마이그레이션을 시작하기 전에 잘못된 콘텐츠를 쿼리하고 제거하는 것이 좋습니다. 예를 들어, 원래 표현물이 없거나 워크플로우 처리에서 중단된 자산 또는 페이지를 찾습니다. 참조: [자산 상태](#asset-health). |

## 데이터 수집 중 {#gathering-data}

>[!NOTE]
> 다음 [컨텐츠 마이그레이션 전략 및 타임라인](#content-strategy-and-timeline) 섹션에서는 수집된 데이터를 추출하고 마이그레이션 계획을 만드는 방법을 자세히 설명합니다.

데이터를 수집하면 마이그레이션 활동 및 관련 작업을 계획하는 데 도움이 될 수 있습니다. 추출 및 수집 시간은 데이터 포인트를 마이그레이션 세트의 특정 크기와 연결할 수 있으므로 특히 유용합니다. 따라서 다음 데이터 포인트를 추정하여 계획을 세울 수 있습니다.

* 에 걸린 총 시간 [추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* 에 걸린 총 시간 [수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* 추가 작업에 걸린 총 시간 [추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
* 추가 작업에 걸린 총 시간 [수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)

한 가지 더 중요한 데이터 점은 를 완료하는 데 걸리는 시간입니다 [사용자 매핑](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md)를 채울 경우 컨텐츠 마이그레이션과 연결됩니다. 이 데이터 요소는 전체 추출 타임라인에 추가되고 추가 작업 중에 실행할 필요가 없으므로 보다 현실적인 추정에 대해 고려할 수 있습니다.

이러한 데이터 포인트를 통해 다음을 수행할 수도 있습니다 [KPI 설정](/help/journey-migration/readiness.md#establish-kpis) 및 기타 마이그레이션 관련 작업

### 마이그레이션 계획 {#migration-plan}

수집한 데이터 포인트를 기반으로(위 참조) 매크로 프로젝트 계획에 통합할 수 있는 마이그레이션 계획을 만들 수 있습니다. 이 단계에서는 모든 주요 이해 관계자가 마이그레이션 활동을 시각화하고 계획할 수 있습니다.

다음 표는 일반적인 마이그레이션 계획을 보여줍니다.

| 마이그레이션 반복 | 시작 날짜 | 예상 종료 날짜 | 종속성 | 예상 기간(일) | 추가 세부 정보/작업 항목 |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |  |  |  |  |  |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |  |  |  |  |  |

위의 표에서 볼 수 있듯이 특정 이름 지정 형식을 따라 마이그레이션 반복을 식별하는 것이 좋습니다. 예를 들면 다음과 같습니다. **PRDCLONE** 소스 AEM 환경 의 경우 **작성자/게시** AEM as a Cloud Service 환경의 경우 **CSSTAGE-AUTHOR** AEM as a Cloud Service 인스턴스 등에 대한 호출 섹션을 참조하십시오.

마이그레이션 계획에 영향을 주는 몇 가지 중요한 세부 사항:

**필요한 총 추출 수**

* 특정 환경의 작성 및 게시 추출은 서로 독립적이므로 두 개의 병렬 추출으로 간주됩니다.
* 특정 기간의 저장소 증가에 따른 추가 추출 수입니다.

**필요한 총 수집 수**

* 추출된 세트를 여러 Cloud Service 환경에 수집할 수 있으므로 이 항목을 계획에 캡처하는 것이 중요합니다.
* 추가 섭취 수.
* 소스 작성자에서 클라우드 서비스 작성자 인스턴스로 컨텐츠를 마이그레이션하고, 소스 게시에서 Cloud Service 게시으로 컨텐츠를 마이그레이션하는 것은 모든 작성 컨텐츠를 Cloud Service 게시으로 섭취하는 것을 방지하는 가장 좋은 방법입니다.

### 마이그레이션 추적기 {#migration-tracker}

마이그레이션 추적기를 사용하여 초기 실행과 최상위 실행 모두에 대한 시간을 기록할 수 있습니다. 이러한 데이터 포인트를 사용하면 최종 추가 전에 현실적인 컨텐츠 고정 요구 사항을 만들 수 있습니다.

추적기는 다음 작업도 지원합니다.

* 계획 또는 실행 타임라인에서 조정이 필요한 계획자의 편차를 확인합니다
* 필요한 모든 커뮤니케이션에서 사용할 수 있는 현실적인 상태 제공
* 초기 또는 향후 추가 마이그레이션 계획

다음 표에서는 기능 마이그레이션 추적기를 보여줍니다.

| 소스(환경/인스턴스/URL) | 대상(환경/인스턴스/URL) | 마이그레이션 세트 이름, 유형(초기 또는 추가) | 마이그레이션 세트 크기(MB) | 사용자 매핑(예 / 아니오) | 추출 기간(시작, 종료, 소요된 시간) | 수집 기간(시작, 종료, 소요된 시간) | 문제 / 해결 방법 / 세부 정보 |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |

## 컨텐츠 마이그레이션 전략 및 타임라인 {#content-strategyand-timeline}

다음 섹션에서는 컨텐츠 마이그레이션 전략 및 타임라인을 만드는 데 사용할 수 있는 중요한 단계 및 관련 작업을 보여줍니다.

![이미지](/help/journey-migration/assets/content-migration2.png)

### 맞춤 {#fitment}

* 개정 정리, 데이터 저장소 가비지 수집 및 데이터 일관성 검사를 수행합니다. 참조 - [Go-Live 준비](#preparing-for-go-live)
* [통계 수집](#gathering-data) AEM 소스 저장소 정보:
   * 세그먼트 저장소 크기
   * 인덱스 저장소 크기
   * 페이지 수
   * 자산 수
   * 사용자 및 그룹 수
* 다음 기능이 AEM 소스에서 활성화되어 있는지 확인합니다(AEM as a Cloud Service에도 필요).
   * 스마트 태그 지정
   * 유사성 검색
   * word 및 pdf 문서에서 텍스트를 포함하는 검색
* 모범 사례 분석기 수집 [보고서](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* 로 가져오기 [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * 자체 분석 권장 사항을 검토하여 AEM as a Cloud Service이 스토리지 요구 사항을 처리할 수 있는지 확인하십시오.
* 마이그레이션 계획을 계속하기 전에 모든 분류에 대한 Adobe 지원 티켓을 만듭니다.

### 마이그레이션 증명 {#proof-of-migration}

* 다음과 같은 작업을 수행하는 운영 클론을 요청합니다.
   * 동일한 네트워크 영역에 있습니다.
   * 사용자 및 그룹과 같은 프로덕션 콘텐츠를 제공합니다.
   * 작성자 및 게시 복제 - 클러스터 또는 게시 팜의 경우 각각 하나의 노드
* 마이그레이션될 컨텐츠의 하위 집합을 선택하여 다음과 같이 하십시오.
   * 사용 가능한 모든 컨텐츠 유형을 혼합한 것입니다
   * 모든 사용자 및 그룹 포함 [사용자 매핑](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md) 필수 여부
* 컨텐츠의 25% 또는 최대 1TB의 컨텐츠 중 적은 컨텐츠를 포함합니다.
* 하나 이상의 전체 및 [추가](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) 운영 클론에서 AEM as a Cloud Service 비프로덕션 환경으로 마이그레이션
* 다음과 같은 잠재적 문제를 해결합니다.
   * AEM 소스의 디스크 공간
   * AEM 소스와 AEM as a Cloud Service 간의 연결
   * 임의 [수집 관련 제한 사항](go-live.md#known-limitations).
* 걸린 시간 기록 [추출 및 수집](#gathering-data):
   * 일주일에 얼마나 많은 콘텐츠가 추가되는지 알아보십시오
   * 마이그레이션 증명에서 측정한 시간을 추출하여 [마이그레이션 계획](#migration-plan).

## 다음은 무엇입니까? {#what-is-next}

AEM 설치를 클라우드로 이동할 준비가 되었는지 평가하는 방법을 완전히 이해한 후 준비하는 데 필요한 도구를 사용하는 방법을 학습하므로 이제 로 이동할 차례입니다. [go-live 단계](/help/journey-migration/go-live.md).
