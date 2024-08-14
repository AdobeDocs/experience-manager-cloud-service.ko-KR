---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보에 대해 알아봅니다.
feature: Release Information
role: Admin
source-git-commit: bf8bab5a195dde6cf15a2fd52e51d58c0215fdf3
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 30%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 일자는 2024년 8월 12일 화요일입니다. 다음 릴리스는 2024년 9월 14일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 AEM Formsas a Cloud Service 에서 [추가 게시 영역](/help/operations/additional-publish-regions.md) 및 [99.99% SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)(서비스 수준 계약)을 사용할 수 있습니다.
   * 이러한 향상된 기능을 통해 가동 시간을 늘리고 지연 시간을 줄임으로써 더 높은 SLA를 달성하여 전 세계에 분포한 사용자에게 동급 최고의 경험을 제공할 수 있습니다.

## 조기 채택 프로그램 {#early-adoption}

Adobe의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### Cloud Manager의 Edge Delivery Services 지원 {#edge-delivery-services}

AEM Sites의 일부로 Edge Delivery Services 라이선스가 부여된 경우 [이제 Cloud Manager에서 직접 Edge Delivery Services을 사용하여 사이트를 온보딩하고](/help/implementing/cloud-manager/edge-delivery-services.md) 안내식 셀프서비스 환경을 사용하여 라이브로 전환할 수 있습니다.

이 기능은 모든 AEM 속성에 대해 통합 환경을 제공합니다. 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑과 같은 중요한 워크플로에서 일관성을 보장합니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 `aemcs-cmedgedelsvs-program-adopter@adobe.com`(으)로 전자 메일을 보내세요.

### DV(도메인 확인) 인증서

이제 Cloud Manager을 사용하여 [셀프서비스에서 도메인 확인(DV) SSL 인증서를 생성하고 관리](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md)할 수 있습니다. 이 기능은 온라인 비즈니스를 위한 안전한 웹 사이트를 만들 수 있는 가장 빠르고 쉽고 비용 효율적인 솔루션을 제공합니다.

이 새로운 기능을 테스트하고 피드백을 제공하려면 Adobe ID에 연결된 전자 메일 주소를 사용하여 `Grp-aemcs-dv-dert-adopter@adobe.com`에게 전자 메일을 보내세요.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 사용합니다. 이를 사용하여 공개 또는 인증이 필요한 웹 페이지를 감사할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 평가를 제공합니다.

새로운 대시보드를 시험해 보는 것이 궁금하신가요? 먼저 Adobe ID에 연결된 전자 메일을 사용하여 `aem-lighthouse-pilot@adobe.com`에게 전자 메일을 보냅니다.

## 버그 수정

* 파이프라인이 삭제된 후 파이프라인 단계가 실행되는 드문 문제가 수정되었습니다.
* 드문 경우지만 구성 파이프라인이 `FAILED` 상태를 잘못 표시하는 문제가 해결되었습니다.
