---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 8d5d8910a906e2adf17fa9c75f17634602c2e0b9
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 46%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 날짜는 2024년 6월 6일입니다. 다음 릴리스는 2024년 7월 11일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 다음을 수행할 수 있습니다. [고유한 GitHub 저장소 사용](/help/implementing/cloud-manager/managing-code/private-repositories.md) 전체 스택 및 프론트엔드 파이프라인 모두의 소스로 사용됩니다.
   * 또한 다음을 통해 GitHub 저장소를 활용할 수 있습니다. [git 하위 모듈,](/help/implementing/cloud-manager/managing-code/git-submodules.md) 가져오기 요청 유효성 검사에 사용되는 자동 생성 파이프라인에 대한 향상된 제어 기능을 제공하고 코드 스캔 단계 동안 중요한 지표에 대한 비헤이비어를 정의할 수 있도록 합니다.
   * [또한 다음을 선택할 수 있습니다.](/help/implementing/cloud-manager/managing-code/github-check-config.md) gitHub에서 보고서 기록을 보존하려면 파이프라인 이름을 지정하고 필요에 맞게 파이프라인 변수를 설정합니다.
* [셀프서비스 콘텐츠 복원](/help/operations/restore.md) 최대 7일 동안 백업 복구를 수행할 수 있으며 다음과 같은 기능이 제공됩니다.
   * 이전 24시간 동안 특정 시점 백업 복원
   * 최대 7일 동안 고정 시간 복원
* [새 OakPal 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-ui-content-package) 이(가) Cloud Manager 코드 품질 검사에 추가되었습니다.
   * 2024년 6월 현재 추가된 모든 새 규칙은 변경되지 않는 변경 사항입니다.
   * 이러한 새로운 규칙은 Cloud Manager 2024년 8월 릴리스부터 파이프라인이 실패하게 되므로 가능한 한 빨리 이러한 문제를 해결해야 합니다.

## 얼리 어답터 프로그램 {#early-adoption}

Adobe의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### Cloud Manager의 Edge Delivery Services 지원 {#edge-delivery-services}

Adobe Experience Manager Sites의 일부로 Edge Delivery Services 라이선스가 부여된 경우 [이제 Cloud Manager에서 직접 Edge Delivery Services을 사용하여 사이트를 온보딩할 수 있습니다](/help/implementing/cloud-manager/edge-delivery-services.md) 가이드 셀프 서비스 환경을 사용하여 라이브로 전환하십시오.

이렇게 하면 모든 AEM 속성에 대해 통합 환경을 제공하여 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑을 비롯한 모든 중요한 워크플로우와 일관성을 유지할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 (으)로 이메일을 보내십시오. `aemcs-cmedgedelsvs-program-adopter@adobe.com` 사용 중인 Adobe ID과 연결된 이메일 주소입니다.

### DV(도메인 확인) 인증서

이제 Cloud Manager를 사용하여 다음을 수행할 수 있습니다. [셀프서비스는 DV(도메인 유효성 검사) SSL 인증서를 생성하고 관리합니다.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) 이를 통해 온라인 비즈니스를 위한 안전한 웹 사이트를 만들 수 있는 가장 빠르고 쉽고 비용 효율적인 솔루션을 제공합니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 (으)로 이메일을 보내십시오. `Grp-aemcs-dv-dert-adopter@adobe.com` 사용 중인 Adobe ID과 연결된 이메일 주소입니다.

### RUM(실시간 사용 모니터링)을 통한 클라이언트측 수집 {#rum}

다음을 활용할 수 있습니다. [RUM(Real Use Monitoring) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) 클라이언트측 컬렉션을 AEM as a Cloud Service으로 활성화하려면

RUM(Real Use Monitoring) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여를 안정적으로 측정합니다. 이를 통해 페이지 성능에 대한 고급 인사이트를 얻을 수 있습니다. 이는 Adobe에서 관리하는 CDN 또는 Adobe에서 관리하지 않는 CDN을 사용하는 고객에게 유용합니다. Adobe가 관리하지 않는 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe와 공유할 필요가 없습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `aemcs-rum-adopter@adobe.com`에 이메일을 보내주십시오. 이메일에 프로덕션, 단계, 개발 환경의 도메인 이름이 포함되어야 합니다.  이 기능에 대한 얼리 어답터 프로그램의 가용성은 제한적입니다.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 사용합니다. 공개 또는 인증이 필요한 모든 웹 페이지에 대해 실행할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새 대시보드를 테스트해 보고 싶으십니까? Adobe ID와 연결된 이메일로 `aem-lighthouse-pilot@adobe.com`에 이메일을 보내 주시면 귀하의 시작을 도와드릴 수 있습니다.
