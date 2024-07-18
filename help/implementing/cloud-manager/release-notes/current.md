---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.7.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.7.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: a5cd55bcdc6044dd8db26f009b955216cda5daee
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 58%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.7.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.7.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2024.7.0의 릴리스 날짜는 2024년 7월 18일입니다. 다음 릴리스는 2024년 8월 8일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 커밋에서 파이프라인을 시작하기 위한 [프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline) 및 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline) 트리거 **Git 변경 시**&#x200B;를 이제 [개인 저장소에서 사용할 수 있습니다.](/help/implementing/cloud-manager/managing-code/private-repositories.md)
   * 이는 8월 중순까지 완료되는 대로 단계적으로 출시될 예정입니다.
* 이제 [Adobe 관리 DV 인증서를 추가할 때 ](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md)각 도메인에 대한 인증서를 만드는 대신 여러 도메인을 포함하는 단일 인증서를 추가할 수 있습니다.
* 프로그램에 Sites 또는 Forms 솔루션 이상이 있는 한 [추가 게시 영역](/help/operations/additional-publish-regions.md)이 없는 솔루션은 프로그램에 추가할 수 있습니다.
* 프로그램에 Sites 또는 Forms 솔루션 이상이 있는 한 [99.99% SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)가 없는 솔루션을 프로그램에 추가할 수 있습니다.
* [경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)가 여러 가지 방법으로 향상되었습니다.
   * 이제 CDN을 통해 `.com` 끝점에 대해 감사가 실행되어 이전 `.net` 접근 방식이 대체되었습니다.
      * 이 변경 사항은 실제 사용자 경험을 보다 정확하게 시뮬레이션하며 웹 사이트 관리 및 최적화에 대해 보다 현명한 결정을 내리는 데 도움이 됩니다.
   * 경험 감사 UI에 다음과 같은 여러 가지 기능이 개선되었습니다.
      * 성능, 모범 사례, SEO 및 접근성에 대한 트렌드 보기가 추가되었습니다.
      * 이제 Lighthouse 원시 보고서 링크를 보다 직관적인 방식으로 스캔 스냅샷 세부 정보 패널에 직접 볼 수 있습니다.
      * 등대 권장 사항 섹션이 향상되었습니다.
   * PWA 지표는 Lighthouse 버전 12.0.0에 따라 제거되었으며 이 지표는 제거되었습니다.

## 얼리 어답터 프로그램 {#early-adoption}

Adobe의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### Cloud Manager에서의 Edge Delivery Services 지원 {#edge-delivery-services}

Adobe Experience Manager Sites의 일부로 Edge Delivery Services에 라이선스를 부여한 경우, [이제 Cloud Manager에서 Edge Delivery Services를 직접 사이트에 온보딩하고](/help/implementing/cloud-manager/edge-delivery-services.md) 안내식 셀프서비스 경험을 사용하여 라이브로 전환할 수 있습니다.

이를 통해 모든 AEM 속성에 대해 통합된 경험이 가능해지며 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑을 포함한 모든 중요한 워크플로와의 일관성이 보장됩니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `aemcs-cmedgedelsvs-program-adopter@adobe.com`에 이메일을 보내주십시오.

### DV(Domain Validated) 인증서

이제 Cloud Manager를 통해 [DV(Domain Validated) SSL 인증서를 셀프서비스로 생성하고 관리할 수 있습니다.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) 이를 통해 귀하의 온라인 비즈니스를 위한 안전한 웹 사이트를 구축할 수 있는 가장 빠르고 쉬우며 비용 효율적인 솔루션이 제공됩니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-aemcs-dv-dert-adopter@adobe.com`에 이메일을 보내주십시오.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 사용합니다. 공개 또는 인증이 필요한 모든 웹 페이지에 대해 실행할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새 대시보드를 테스트해 보고 싶으십니까? Adobe ID와 연결된 이메일로 `aem-lighthouse-pilot@adobe.com`에 이메일을 보내 주시면 귀하의 시작을 도와드릴 수 있습니다.
