---
title: 실행
description: 코드 및 콘텐츠가 클라우드에 준비되면 마이그레이션을 수행하는 방법을 알아봅니다
exl-id: 10ec0b04-6836-4e26-9d4c-306cf743224e
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 3%

---

# 실행 {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Go-Live 준비"
>abstract="AEM as a Cloud Service에서 원활하고 성공적으로 Go-Live를 진행하려면 코드 및 콘텐츠 고정 기간, 반복 테스트, 콘텐츠 추가, 성능 테스트, 보안 테스트 등에 대한 계획을 수립해야 합니다."

이 여정 부분에서는 코드와 컨텐츠를 모두 AEM as a Cloud Service으로 이동할 준비가 되면 마이그레이션을 계획하고 수행하는 방법을 배웁니다. 또한 마이그레이션을 수행할 때 모범 사례와 알려진 제한 사항이 무엇인지 알아봅니다.

## 지금까지의 스토리 {#story-so-far}

여정의 이전 단계에서

* [시작](/help/journey-migration/getting-started.md) 페이지에서 AEM as a Cloud Service으로 이동하는 방법을 배웠습니다.
* [준비 단계](/help/journey-migration/readiness.md)를 읽고 배포를 클라우드로 이동할 준비가 되었는지 확인했습니다.
* [구현 단계](/help/journey-migration/implementation.md)에서 코드 및 콘텐츠 클라우드를 준비할 수 있는 도구 및 프로세스에 익숙해집니다.

## 목표 {#objective}

이 문서는 여정의 이전 단계를 잘 알고 있는 경우 AEM as a Cloud Service으로 마이그레이션하는 방법을 이해하는 데 도움이 됩니다. 초기 프로덕션 마이그레이션을 수행하는 방법과 AEM as a Cloud Service으로 마이그레이션할 때 따라야 할 모범 사례를 알아봅니다.

## 초기 프로덕션 마이그레이션 {#initial-migration}

프로덕션 마이그레이션을 수행하기 전에 [구현 단계](/help/journey-migration/implementation.md)의 [콘텐츠 마이그레이션 전략 및 타임라인](/help/journey-migration/implementation.md##strategy-timeline) 섹션에 설명된 마이그레이션 기능 및 증명 단계를 따르십시오.

* 클론에서 수행된 AEM as a Cloud Service 단계 마이그레이션 과정에서 얻은 경험을 기반으로 프로덕션에서 마이그레이션을 시작합니다.
   * Author-Author
   * Publish-Publish

* AEM as a Cloud Service 작성자 및 게시 계층 모두에 수집된 콘텐츠의 유효성을 검사합니다.
* 수집이 완료될 때까지 소스와 대상 모두에서 컨텐츠가 이동하지 않도록 컨텐츠 작성 팀에 지시합니다
* 새 콘텐츠를 추가, 편집 또는 삭제할 수 있지만 이동하지 마십시오. 이는 소스와 대상 모두에 적용됩니다.
* 전체 추출 및 수집에 [소요된 시간](/help/journey-migration/implementation.md#gathering-data)을 기록하여 향후 추가 마이그레이션 타임라인을 예측하십시오.
* 작성자와 게시 모두에 대해 [마이그레이션 플래너](/help/journey-migration/implementation.md#migration-plan)를 만듭니다.

## 증분 추가 {#top-up}

프로덕션에서 초기 마이그레이션 후 증분 추가 작업을 수행하여 클라우드 인스턴스에서 콘텐츠를 최신 상태로 유지해야 합니다. 이러한 이유로 다음 모범 사례를 따르는 것이 좋습니다.

* 컨텐츠 양에 대한 데이터를 수집합니다. 예를 들어 1주마다, 2주마다 또는 한 달마다.
* 48시간 이상의 콘텐츠 추출 및 수집을 피하는 방식으로 추가 작업을 계획해야 합니다. 콘텐츠 윗면이 주말 시간대에 맞춰지도록 하는 것이 좋습니다.
* 필요한 최상위 작업의 수를 계획하고 예상 값을 사용하여 Go-Live 날짜를 기준으로 계획을 수립합니다.

## 마이그레이션에 대한 코드 및 컨텐츠 고정 타임라인 식별 {#code-content-freeze}

앞에서 언급했듯이 코드 및 콘텐츠 고정 기간을 예약해야 합니다. 동결 기간을 계획하는 데 도움이 되는 질문은 다음과 같습니다.

* 콘텐츠 작성 활동을 얼마나 동결해야 합니까?
* 게재 팀에 새 기능 추가를 중지하도록 얼마 동안 요청해야 합니까?

첫 번째 질문에 답변하려면 비프로덕션 환경에서 체험판 실행을 수행하는 데 걸린 시간을 고려해야 합니다. 두 번째 질문에 답변하려면 새로운 기능을 추가하는 팀과 코드를 리팩터링하는 팀 간의 긴밀한 협업이 필요합니다. 기존 배포에 추가된 모든 코드도 클라우드 서비스 분기에 추가, 테스트 및 배포되도록 하는 것이 목표입니다. 일반적으로 코드 동결량이 더 적다는 의미입니다.

또한 최종 콘텐츠 추가 일정이 잡히면 콘텐츠 중지를 계획해야 합니다.

## 모범 사례 {#best-practices}

마이그레이션을 계획하거나 수행할 때는 다음 지침을 고려해야 합니다.

* 작성자에서 작성자로, Publish에서 Publish으로 마이그레이션
* 다음을 수행하는 데 사용할 수 있는 운영 클론 요청:
   * 저장소 통계 캡처
   * 마이그레이션 활동 증명
   * 마이그레이션 계획 준비
   * 컨텐츠 고정 요구 사항 식별
   * 프로덕션에서 마이그레이션을 수행할 때 프로덕션의 업사이징 요구 사항 파악

**콘텐츠 전송 도구 모범 사례**

라이브 진행 시 클론 대신 프로덕션에서 컨텐츠 마이그레이션을 실행해야 합니다. 초기 마이그레이션에 [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)을 사용한 다음, 더 작은 청크를 추출하고 소스 AEM에 대한 장기적인 로드를 방지하기 위해 추출 작업을 자주(매일) 실행하는 것이 좋습니다.

다음과 같은 이유로 운영 마이그레이션을 수행할 때는 클론에서 컨텐츠 전송 도구를 실행하지 않아야 합니다.

* 고객이 추가 마이그레이션 중에 컨텐츠 버전을 마이그레이션해야 하는 경우 클론에서 컨텐츠 전송 도구를 실행해도 버전이 마이그레이션되지 않습니다. 라이브 작성자에서 클론을 자주 재생성하더라도 클론이 생성될 때마다 컨텐츠 전송 도구에서 델타를 계산하는 데 사용하는 체크포인트가 재설정됩니다.
* 클론은 전체적으로 새로 고칠 수 없으므로 ACL 쿼리 패키지를 사용하여 프로덕션에서 클론으로 추가 또는 편집되는 콘텐츠를 패키징하고 설치해야 합니다. 이 방법의 문제는 소스 및 클론 모두에서 수동으로 삭제되지 않는 한 소스 인스턴스의 삭제된 컨텐츠는 클론에 도달하지 않는다는 것입니다. 이렇게 하면 프로덕션에서 삭제된 콘텐츠가 클론 및 AEM as a Cloud Service에서 삭제되지 않을 수 있습니다.

**콘텐츠 마이그레이션을 수행하는 동안 AEM 소스에 대한 로드 최적화**

AEM 소스의 로드는 추출 단계 동안 더 커집니다. 다음 사항에 주의하십시오.

* 컨텐츠 전송 도구는 4GB의 JVM 힙을 사용하는 외부 Java 프로세스입니다
* AzCopy가 아닌 버전은 바이너리를 다운로드하고 소스 AEM 작성자의 임시 공간에 저장하여 디스크 I/O를 사용한 다음 네트워크 대역폭을 사용하는 Azure 컨테이너에 업로드합니다
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)은(는) blob 저장소에서 디스크 I/O 및 네트워크 대역폭을 저장하는 Azure 컨테이너로 직접 blob을 전송합니다. AzCopy 버전에서는 여전히 디스크 및 네트워크 대역폭을 사용하여 세그먼트 저장소에서 Azure 컨테이너로 데이터를 추출하고 업로드합니다
* 컨텐츠 전송 툴 프로세스는 수집 로그만 스트리밍하고 디스크 I/O 또는 네트워크 대역폭에 관한 한 소스 인스턴스에 대한 로드가 많지 않으므로 수집 단계에서 시스템 리소스에 대한 부담이 적습니다.

## 알려진 제한 사항 {#known-limitations}

다음 제한 사항 중 하나라도 추출된 마이그레이션 세트의 일부로 해당되는 경우 전체 수집이 실패한다는 점을 고려하십시오.

* 이름이 150자를 초과하는 JCR 노드
* 16MB보다 큰 JCR 노드
* `rep:AuthorizableID`이(가) 포함된 모든 사용자/그룹이 이미 AEM as a Cloud Service에 있습니다.
* 추출되어 수집된 에셋이 마이그레이션의 다음 반복 전에 소스 또는 대상에서 다른 경로로 이동하는 경우.

## 에셋 상태 {#asset-health}

위의 섹션과 비교하여 다음 자산 문제로 인해 **does**&#x200B;이(가) 실패합니다. 그러나 다음 시나리오에서 적절한 단계를 수행하는 것이 좋습니다.

* 원본 렌디션이 누락된 모든 에셋
* 누락된 `jcr:content` 노드가 있는 모든 폴더입니다.

위의 두 항목은 [모범 사례 분석기](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) 보고서에서 확인 및 보고됩니다.

## 실행 체크리스트 {#Go-Live-Checklist}

자세한 내용은 [Go-Live 확인 목록](/help/journey-onboarding/go-live-checklist.md) 설명서를 참조하십시오.

## 다음 단계 {#what-is-next}

AEM as a Cloud Service으로 마이그레이션하는 방법을 이해하면 [Post-Go-Live](/help/journey-migration/post-go-live.md) 페이지에서 원활한 인스턴스 실행을 확인할 수 있습니다.
