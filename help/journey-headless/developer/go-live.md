---
title: 헤드리스 애플리케이션을 사용하여 라이브로 전환하는 방법
description: AEM Headless 개발자 여정의 이 부분에서 Git에서 로컬 코드를 가져와서 CI/CD 파이프라인용 Cloud Manager Git으로 이동하여 헤드리스 애플리케이션을 라이브로 배포하는 방법을 알아봅니다.
exl-id: 81616e31-764b-44b0-94a6-3ae24ce56bf6
source-git-commit: 270eb35023e34eed2cd17674372794c6c2cc7757
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 0%

---

# 헤드리스 애플리케이션을 사용하여 라이브로 전환하는 방법 {#go-live}

의 이 부분에서 [AEM Headless Developer 여정](overview.md), Git에서 로컬 코드를 가져와서 CI/CD 파이프라인용 Cloud Manager Git으로 이동하여 헤드리스 애플리케이션을 라이브로 배포하는 방법을 알아봅니다.

## 지금까지의 이야기 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서, [AEM 헤드리스에서 앱과 콘텐츠를 모두 통합하는 방법](put-it-all-together.md) AEM 개발 도구를 사용하여 프로젝트의 모든 패싯을 통합하는 방법을 알아보았습니다.

이 문서는 이러한 기본 사항을 기반으로 하여 라이브로 전환하기 위해 고유한 AEM 헤드리스 프로젝트를 준비하는 방법을 이해합니다.

## 목표 {#objective}

이 문서는 애플리케이션을 사용하기 전에 AEM 헤드리스 게시 파이프라인과 알아야 하는 성능 고려 사항을 이해하는 데 도움이 됩니다.

* Launch 전에 애플리케이션 보안 및 확장
* 성능 및 디버그 문제 모니터링

<!-- Alexandru: this is a bit redundant, to review again later

## Prepare your AEM Headless Application for Go-Live {#prepare-your-aem-headless-application-for-golive}

-->
AEM 헤드리스 애플리케이션을 시작할 준비가 되도록 하려면 아래에 요약된 우수 사례를 따르십시오.

## Launch 전에 헤드리스 애플리케이션 보안 및 확장 {#secure-and-scale-before-launch}

1. 구성 [토큰 기반 인증](/help/headless/security/authentication.md) GraphQL 요청 사용
1. 구성 [캐싱](/help/implementing/dispatcher/caching.md).

## 모델 구조와 GraphQL 출력 {#structure-vs-output}

* 15kb 이상의 JSON(gzip 압축)을 출력하는 쿼리를 만들지 마십시오. 긴 JSON 파일은 클라이언트 애플리케이션에서 구문 분석하기 위해 리소스를 많이 사용합니다.
* 5개 이상의 중첩 조각 계층 수준은 피하십시오. 추가 수준을 사용하면 컨텐츠 작성자가 변경 사항의 영향을 고려하기가 어렵습니다.
* 모델 내에서 종속성 계층 구조를 사용하는 쿼리를 모델링하는 대신 다중 개체 쿼리를 사용합니다. 따라서 많은 컨텐츠 변경 작업을 수행하지 않고도 JSON 출력을 재구성할 수 있는 장기적인 유연성을 얻을 수 있습니다.

## CDN 캐시 적중률 최대화 {#maximize-cdn}

* 서피스에서 라이브 컨텐츠를 요청하지 않는 한 직접 GraphQL 쿼리를 사용하지 마십시오.
   * 가능하면 항상 지속적인 쿼리를 사용합니다.
   * CDN이 TTL을 캐시할 수 있도록 600초 이상의 CDN TTL을 제공합니다.
   * AEM에서는 기존 쿼리에 대한 모델 변경의 영향을 계산할 수 있습니다.
* 클라이언트 트래픽을 CDN으로 줄이고 더 높은 TTL을 할당하기 위해 낮은 컨텐츠와 높은 컨텐츠 변경률 간에 JSON 파일/GraphQL 쿼리를 분할합니다. 이렇게 하면 원본 서버와 JSON의 유효성을 다시 검사하는 CDN이 최소화됩니다.
* CDN에서 컨텐츠를 적극적으로 무효화하려면 소프트 삭제를 사용합니다. 이렇게 하면 CDN이 캐시 누락을 유발하지 않고 컨텐츠를 다시 다운로드할 수 있습니다.

## 헤드리스 컨텐츠 다운로드 시간 개선 {#improve-download-time}

* HTTP 클라이언트가 HTTP/2를 사용하는지 확인합니다.
* HTTP 클라이언트가 gzip에 대한 Headers 요청을 수락하는지 확인합니다.
* JSON 및 참조된 아티팩트를 호스팅하는 데 사용되는 도메인 수를 최소화합니다.
* 활용 `Last-modified-since` 리소스를 새로 고치려면
* 사용 `_reference` 전체 JSON 파일을 구문 분석할 필요 없이 자산 다운로드를 시작하기 위해 JSON 파일에 출력됩니다.

## 프로덕션에 배포 {#deploy-to-production}

모든 것이 테스트되고 제대로 작동하는지 확인한 후에는 코드 업데이트를 [Cloud Manager의 중앙 집중식 Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html).

업데이트가 Cloud Manager에 업로드되면 다음을 사용하여 AEM as a Cloud Service에 배포할 수 있습니다 [Cloud Manager의 CI/CD 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

광범위하게 적용되는 Cloud Manager CI/CD 파이프라인을 활용하여 코드 배포를 시작할 수 있습니다 [여기](/help/implementing/deploying/overview.md).

## 성능 모니터링 {#performance-monitoring}

AEM 헤드리스 애플리케이션을 사용할 때 최상의 경험을 얻으려면 아래에 자세히 설명된 대로 주요 성능 지표를 모니터링하는 것이 중요합니다.

* 앱의 미리 보기 및 프로덕션 버전 확인
* 현재 서비스 가용성 상태에 대한 AEM 상태 페이지 확인
* 성능 보고서 액세스
   * 게재 성능
      * CDN(기본) 성능 - 호출 수, 캐시 비율, 오류율 및 페이로드 트래픽 확인
      * 원본 서버 - 호출 수, 오류율, CPU 로드, 페이로드 트래픽
   * 작성자 성능
      * 사용자 수, 요청 및 로드 확인
* 앱 및 공간별 성능 보고서에 액세스
   * 서버가 작동하면 일반 지표가 녹색/주황색/빨간색 인지 확인한 다음 특정 앱 문제를 식별합니다
   * 앱 또는 공간으로 필터링된 위에서 동일한 보고서 열기(예: Photoshop 데스크탑, 페이월)
   * Splunk 로그 API를 사용하여 서비스 및 응용 프로그램 성능에 액세스합니다
   * 다른 문제가 있을 경우 고객 지원 센터에 문의하십시오.

## 문제 해결 {#troubleshooting}

### 디버깅 {#debugging}

디버깅에 대한 일반적인 접근 방법으로 다음 우수 사례를 따르십시오.

* 응용 프로그램의 미리 보기 버전을 사용하여 기능 및 성능 유효성 검사
* 애플리케이션의 프로덕션 버전을 사용하여 기능 및 성능 확인
* 컨텐츠 조각 편집기의 JSON 미리 보기를 사용하여 유효성 검사
* 클라이언트 애플리케이션의 JSON을 Inspect하여 클라이언트 애플리케이션 또는 배달 문제가 있는지 확인합니다
* GraphQL을 사용하여 JSON을 Inspect에서 캐시된 컨텐츠 또는 AEM과 관련된 문제가 있는지 확인합니다

### 지원을 통해 버그 로깅 {#logging-a-bug-with-support}

추가 지원이 필요한 경우 지원 센터에 버그를 효율적으로 기록하려면 아래 단계를 따르십시오.

* 필요한 경우 문제 스크린샷을 수행합니다
* 문제를 재현할 수 있는 방법을 문서화합니다.
* 문제가 재현되는 내용을 문서화합니다.
* AEM 지원 포털을 통해 적절한 우선 순위로 문제 기록

## 여정이 끝나요? 아니면 끝나요? {#journey-ends}

축하합니다! AEM Headless Developer 여정을 완료했습니다! 이제 다음을 이해할 수 있습니다.

* 헤드리스와 제목이 없는 콘텐츠 전달 간의 차이입니다.
* AEM 헤드리스 기능.
* Headless 프로젝트를 구성하고 AEM 하는 방법입니다.
* AEM에서 헤드리스 컨텐츠를 만드는 방법.
* AEM에서 헤드리스 콘텐츠를 검색하고 업데이트하는 방법입니다.
* AEM Headless 프로젝트를 사용하여 라이브로 전환하는 방법
* Go-Live 후 수행할 작업.

첫 번째 AEM Headless 프로젝트를 이미 시작했거나 이제 필요한 모든 정보를 가지고 있습니다. 잘했어요!

### 단일 페이지 애플리케이션 살펴보기 {#explore-spa}

하지만 AEM의 헤드리스 가게들은 여기서 멈출 필요가 없습니다. 당신은 [여정의 시작하기](getting-started.md#integration-levels) AEM에서 헤드리스 게재 및 기존의 전체 스택 모델을 지원할 뿐만 아니라 두 가지 장점을 결합하는 하이브리드 모델을 지원하는 방법에 대해 간략하게 설명합니다.

이러한 종류의 유연성이 프로젝트에 필요한 경우 여정의 추가 부분인 선택 사항을 계속 진행합니다. [AEM을 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법.](create-spa.md)

## 추가 리소스 {#additional-resources}

* [AEM에 대한 as a Cloud Service 배포 개요](/help/implementing/deploying/overview.md)
* [Cloud Manager를 사용하여 코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Cloud Manager Git 리포지토리를 외부 Git 리포지토리와 통합 및 AEM에 프로젝트 배포 as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)
