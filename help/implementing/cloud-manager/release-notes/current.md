---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보에 대해 간략히 알아봅니다.
feature: Release Information
role: Admin
source-git-commit: a823bcd1461b847983d0243cd9abd59efd8d7b6f
workflow-type: ht
source-wordcount: '465'
ht-degree: 100%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.8.0 릴리스 일자는 2024년 8월 14일입니다. 다음 릴리스는 2024년 9월 14일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* AEM Forms as a Cloud Service에서는 [추가 게시 지역](/help/operations/additional-publish-regions.md) 및 [99.99% SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)(서비스 수준 계약) 기능을 사용할 수 있습니다.
   * 이러한 향상된 기능을 사용하면 가동 시간은 늘리고 지연 시간은 줄여 더 높은 SLA를 달성할 수 있으므로, 전 세계에 분산된 사용자에게 최상의 경험을 보장할 수 있습니다.

## 얼리 어답터 프로그램 {#early-adoption}

Adobe의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### Cloud Manager에서의 Edge Delivery Services 지원 {#edge-delivery-services}

AEM Sites의 일부로 Edge Delivery Services에 라이선스를 부여한 경우, [이제 Cloud Manager에서 Edge Delivery Services를 직접 사이트에 온보딩하고](/help/implementing/cloud-manager/edge-delivery-services.md) 안내식 셀프서비스 경험을 사용하여 라이브로 전환할 수 있습니다.

이 기능은 모든 AEM 속성에 대해 통합된 경험을 제공합니다. 도메인 이름 관리, SSL 인증서 관리, CDN 매핑 등의 중요한 워크플로 간에 일관성을 보장합니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일로 `aemcs-cmedgedelsvs-program-adopter@adobe.com`에 이메일 주소를 보내 주십시오.

### DV(Domain Validated) 인증서

이제 Cloud Manager를 통해 [DV(Domain Validated) SSL 인증서를 셀프서비스로 생성하고 관리](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md)할 수 있습니다. 이 기능을 통해 귀하의 온라인 비즈니스를 위한 안전한 웹 사이트를 구축할 수 있는 가장 빠르고 쉬우며 비용 효율적인 솔루션이 제공됩니다.

이 새로운 기능을 테스트하고 피드백을 제공하려면 Adobe ID에 연결된 이메일 주소를 사용하여 `Grp-aemcs-dv-dert-adopter@adobe.com`으로 이메일을 보내 주십시오.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 사용합니다. 이를 사용하면 공개 또는 인증이 필요한 모든 웹 페이지를 감사할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 평가를 제공합니다.

새로운 대시보드를 사용해보고 싶으십니까? 시작하려면 Adobe ID에 연결된 이메일을 사용하여 `aem-lighthouse-pilot@adobe.com`으로 이메일을 보내 주십시오.

## 버그 수정

* 파이프라인이 삭제된 후에도 파이프라인 단계가 드물게 실행되는 문제가 수정되었습니다.
* 구성 파이프라인에서 `FAILED` 상태가 드물게 잘못 표시되는 문제가 해결되었습니다.
