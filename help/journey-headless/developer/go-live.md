---
title: Headless 애플리케이션 실행 방법
description: 이 AEM Headless 개발자 여정의 부분에서는 Git에서 로컬 코드를 가져오고 CI/CD 파이프라인용 Cloud Manager Git으로 이동하여 Headless 애플리케이션을 라이브로 배포하는 방법에 대해 알아봅니다.
exl-id: 81616e31-764b-44b0-94a6-3ae24ce56bf6
solution: Experience Manager
feature: Headless
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 100%

---

# Headless 애플리케이션 실행 방법 {#go-live}

이 [AEM Headless 개발자 여정](overview.md)의 부분에서는 Git에서 로컬 코드를 가져오고 CI/CD 파이프라인용 Cloud Manager Git으로 이동하여 Headless 애플리케이션을 라이브로 배포하는 방법에 대해 알아봅니다.

## 지금까지의 스토리 {#story-so-far}

AEM Headless 번역 여정의 이전 문서인 [결합 방법 - AEM Headless의 앱과 콘텐츠](put-it-all-together.md)에서는 AEM 개발 도구를 사용하여 프로젝트의 모든 측면을 결합하는 방법에 대해 알아보았습니다.

이 문서는 이러한 기본 사항을 기본으로 하며, 이를 통해 자체 AEM Headless 프로젝트를 준비하여 실행하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

이 문서는 AEM Headless 게시 파이프라인을 이해하고 애플리케이션을 실행하기 전에 알아야 하는 성능을 고려하는 데 도움이 됩니다.

* 실행하기 전 애플리케이션을 안전하게 확장
* 성능 모니터링 및 문제 디버그

<!-- Alexandru: this is a bit redundant, to review again later

## Prepare your AEM Headless Application for Go-Live {#prepare-your-aem-headless-application-for-golive}

-->
AEM Headless 애플리케이션을 실행할 수 있도록 준비하려면 아래에 요약된 모범 사례를 따릅니다.

## 실행하기 전 Headless 애플리케이션을 안전하게 확장 {#secure-and-scale-before-launch}

1. GraphQL 요청이 있는 [토큰 기반 인증](/help/headless/security/authentication.md) 구성
1. [캐싱](/help/implementing/dispatcher/caching.md)을 구성합니다.

## 모델 구조와 GraphQL 출력 비교 {#structure-vs-output}

* 15kb 이상의 JSON(gzip 압축)을 출력하는 쿼리를 만드는 것을 피하십시오. 긴 JSON 파일은 리소스 집약으로 클라이언트 애플리케이션이 구문 분석할 수 있습니다.
* 중첩된 조각 계층 수준이 5단계를 초과하지 않도록 하십시오. 수준이 추가되면 콘텐츠 작성자는 변경 사항이 미치는 영향을 고려할 수 없습니다.
* 모델 내 종속성 계층이 있는 쿼리를 모델링하는 대신 여러 오브젝트 쿼리를 사용합니다. 이를 통해 콘텐츠를 많이 변경하지 않고도 JSON 출력을 보다 길고 유연하게 재구성할 수 있습니다.

## CDN 캐시 적중률 최대화 {#maximize-cdn}

* 표면에서 라이브 콘텐츠를 요청하지 않는 한 GraphQL 쿼리를 직접 사용하지 마십시오.
   * 가능하면 지속 쿼리를 사용합니다.
   * CDN에서 캐싱하려면 CDN TTL을 600초 이상 제공합니다.
   * AEM은 모델 변경이 기존 쿼리에 미치는 영향을 계산할 수 있습니다.
* 클라이언트 트래픽을 CDN으로 축소하고 더 높은 TTL을 할당하려면 JSON 파일/GraphQL 쿼리를 높고 낮은 콘텐츠 변경률 사이로 분할합니다. 원본 서버로 CDN을 최소화하여 JSON의 유효성을 다시 확인합니다.
* CDN의 콘텐츠를 효과적으로 무효화하려면 Soft Purge를 사용합니다. 이렇게 하면 CDN은 캐시 누락 없이 콘텐츠를 다시 다운로드할 수 있습니다.

## Headless 콘텐츠 다운로드 시간 개선 {#improve-download-time}

* HTTP 클라이언트가 HTTP/2를 사용하는지 확인합니다.
* HTTP 클라이언트가 gzip에 대한 헤더 요청을 수락하는지 확인하십시오.
* JSON과 참조된 아티팩트를 호스팅하는 데 사용되는 도메인 수를 최소화합니다.
* `Last-modified-since`를 활용하여 리소스를 새로 고칩니다.
* JSON 파일의 `_reference`출력을 사용하여 전체 JSON 파일을 구문 분석하지 않고도 자산 다운로드를 시작합니다.

## 프로덕션에 배포 {#deploy-to-production}

모든 항목을 테스트하고 제대로 작동하는지 확인하면 코드 업데이트를 [Cloud Manager의 중앙 집중식 Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html)로 푸시할 준비가 완료되었습니다.

업데이트가 Cloud Manager에 업로드되면 [Cloud Manager의 CI/CD 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)을 사용하여 AEM as a Cloud Service에 배포할 수 있습니다.

[여기에서](/help/implementing/deploying/overview.md) 전반적으로 다룬 Cloud Manager CI/CD 파이프라인을 사용하여 코드 배포를 시작할 수 있습니다.

## 성능 모니터링 {#performance-monitoring}

사용자가 AEM Headless 애플리케이션 사용 시 최상의 사용자 경험이 있으면 아래에 설명된 핵심 성능 지표를 모니터링해야 합니다.

* 앱의 미리보기 및 프로덕션 버전 확인
* 현재 서비스 가용성 상태에 대한 AEM 상태 페이지 확인
* 성능 보고서 액세스
   * 게재 성능
      * CDN(Fastly) 성능 – 호출 수, 캐시 속도, 오류율 및 페이로드 트래픽 확인
      * 원본 서버 - 호출 수, 오류율, CPU 로드, 페이로드 트래픽
   * 작성자 성능
      * 사용자, 요청 및 로드 수 확인
* 앱 및 공간별 성능 보고서 액세스
   * 서버가 가동되면 일반 지표가 녹색/주황색/빨간색인지 확인한 다음 특정 앱 문제를 식별합니다.
   * 위에서 앱 또는 공간(예: Photoshop 데스크탑, Paywall)으로 필터링한 동일한 보고서 열기
   * Splunk 로그 API를 사용하여 서비스 및 애플리케이션 성능에 액세스
   * 다른 문제가 있는 경우 고객 지원 팀에 문의하십시오.

## 문제 해결 {#troubleshooting}

### 디버깅 {#debugging}

다음 모범 사례에 따라 디버깅에 대한 일반적인 방식을 사용합니다.

* 애플리케이션의 미리보기 버전을 사용하여 기능 및 성능 확인
* 애플리케이션의 프로덕션 버전을 사용하여 기능 및 성능 확인
* 콘텐츠 조각 편집기의 JSON 미리보기를 사용하여 확인
* 클라이언트 애플리케이션의 JSON을 검사하여 클라이언트 애플리케이션 또는 게재 문제가 있는지 확인합니다.
* GraphQL을 통해 JSON을 검사하여 캐싱된 콘텐츠 또는 AEM과 관련된 문제가 있는지 확인합니다.

### 지원을 통해 버그 로깅 {#logging-a-bug-with-support}

추가 지원이 필요한 경우, 지원을 통해 버그를 효율적으로 로깅하려면 다음 단계를 따릅니다.

* 문제 발생 시 필요한 경우 스크린샷 찍기
* 문제를 재현하는 방식 문서화
* 문제가 재현되는 콘텐츠 문서화
* 적합한 우선 순위로 AEM 지원 포털을 통해 문제 로깅

## 여정 종료 - 종료되었습니까? {#journey-ends}

축하합니다! AEM Headless 개발자 번역 여정을 완료하셨습니다! 이제 다음 사항을 이해할 수 있어야 합니다.

* Headless 콘텐츠 게재와 Headful 콘텐츠 게재의 차이점.
* AEM의 Headless 기능.
* AEM Headless 프로젝트를 구성하고 방법.
* AEM에서 Headless 콘텐츠를 만드는 방법
* AEM에서 Headless 콘텐츠를 검색하여 업데이트하는 방법.
* AEM Headless 프로젝트를 실행하는 방법.
* 실행 후 해야 할 일.

첫 번째 AEM Headless 프로젝트를 이미 실행했거나 이제 이에 필요한 모든 지식을 갖게 되었습니다. 좋습니다!

### 단일 페이지 애플리케이션 살펴보기 {#explore-spa}

하지만 AEM의 Headless 스토어는 여기서 멈추지 않습니다. [여정의 일부 시작하기](getting-started.md#integration-levels)에서 AEM이 Headless 게재 및 기존 전체 스택 모델뿐만 아니라 두 가지 장점을 결합한 하이브리드 모델을 지원하는 방법에 대해 간략하게 논의했던 것으로 기억할지 모릅니다.

프로젝트에 이러한 종류의 유연성이 필요한 경우 부가적인 여정인 [AEM을 통해 단일 페이지 애플리케이션(SPA)을 제작하는 방법](create-spa.md)(옵션)을 계속 진행합니다.

## 추가 리소스 {#additional-resources}

* [AEM as a Headless CMS 소개](/help/headless/introduction.md)
* [AEM 개발자 포털](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [AEM의 Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
* [AEM as a Cloud Service 배포 개요](/help/implementing/deploying/overview.md)
* [Cloud Manager를 사용하여 코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Cloud Manager Git 저장소를 외부 Git 저장소와 통합하고 프로젝트를 AEM as a Cloud Service에 배포합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)
