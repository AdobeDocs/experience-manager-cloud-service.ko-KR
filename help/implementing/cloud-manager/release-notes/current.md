---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.9.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.9.0 릴리스 정보에 대해 간략히 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: ht
source-wordcount: '367'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.9.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.9.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.9.0 릴리스 일자는 2024년 9월 5일입니다. 다음 릴리스는 2024년 10월 3일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **경험 감사 대시보드**

  Google Lighthouse로 구동되는 Adobe Cloud Manager의 [고급 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)는 핵심 웹 바이탈, SEO와 접근성 지표를 평가하여 AEM Sites의 품질 및 성능에 대한 인사이트를 제공합니다. 이로써 사용자는 개선이 필요한 영역을 식별하여, 실행 가능한 권장 사항을 제공하고 팀이 사용자 경험, 페이지 로드 시간, 사이트 규정 준수를 개선할 수 있도록 지원합니다. 이 대시보드는 중요한 사이트 지표의 모니터링을 간소화하고 AEM 애플리케이션이 고성능 및 접근성 기준을 충족하도록 합니다.

* **Adobe에서 생성 및 관리되는 도메인 유효성 검사 인증서:**

  이제 Cloud Manager를 통해 Adobe에서 [DV(Domain Validated) SSL 인증서를 셀프서비스로 생성하고 관리](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)할 수 있습니다. 이 기능을 통해 귀하의 온라인 조직 또는 비즈니스를 위한 안전한 웹 사이트를 구축할 수 있는 가장 빠르고 쉬우며 비용 효율적인 솔루션이 제공됩니다. <!-- CMGR-52403 -->

  >[!NOTE]
  >
  >[Content Hub](/help/assets/product-overview.md) 이 기능은 점진적 롤아웃의 일환으로 단계적으로 고객에게 제공될 예정입니다.

* **Cloud Manager에서의 Edge Delivery Services 지원:**

  AEM Sites의 일부로 Edge Delivery Services 에 라이선스를 부여한 경우 [이제 Cloud Manager를 통해 Edge Delivery Services를 직접 사이트에 온보딩할 수 있습니다](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md). 이 기능을 사용하여 안내식 셀프서비스 Go Live 경험을 제공합니다. 전체 AEM 속성에서 도메인 이름 관리, SSL 인증서, CDN 매핑과 같은 필수 워크플로를 통합하면 일관성과 효율성이 보장됩니다. <!-- CMGR-49859 -->

  >[!NOTE]
  >
  >[Content Hub](/help/assets/product-overview.md) 이 기능은 점진적 롤아웃의 일환으로 단계적으로 고객에게 제공될 예정입니다.

* GitHub 저장소를 사용하는 고객은 이제 웹 계층 구성 파이프라인을 만들고 사용할 수 있습니다. <!--( KEEP IN? SP: YES CMGR-59046 and Slack https://cq-dev.slack.com/archives/C07LFP5BZ2L/p1725407057847379 ) -->

<!--
## Early adoption program {#early-adoption}

For a chance to test some upcoming features, be a part of Adobe's early adoption program. -->


## 버그 수정

* SSL 인증서 테이블 보기의 페이지 매김이 예상대로 작동합니다. <!-- (CMGR-60804 - [UI] Pagination doesn't work for ssl certificates) -->
* 실행 시 **빌드 프로모션** 버튼을 사용하면 잘못된 아티팩트 버전이 승격됩니다. <!-- ( KEEP IN? SP: YES CMGR-59519 and Slack https://cq-dev.slack.com/archives/C07LFPN2R08/p1725408253474129 ) -->

<!-- * Slack message says next release? SP: REMOVE (Leave in for now) SSL Certificates table in Cloud Manager now enables pagination in the user experience. ( https://jira.corp.adobe.com/browse/CMGR-61041 and Slack https://cq-dev.slack.com/archives/C07LFRE9QJU/p1725408553760009 ) --<>
