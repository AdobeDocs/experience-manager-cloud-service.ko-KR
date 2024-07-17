---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 6ca376bda8055d62e35e13053ff21f861c12b292
workflow-type: ht
source-wordcount: '548'
ht-degree: 100%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.6.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2024.6.0 출시 일자는 2024년 6월 6일입니다. 다음 릴리스는 2024년 7월 18일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 [자체 GitHub 저장소](/help/implementing/cloud-manager/managing-code/private-repositories.md)를 전체 스택 및 프론트엔드 파이프라인 모두의 소스로 사용할 수 있습니다.
   * 또한 [Git 하위 모듈](/help/implementing/cloud-manager/managing-code/git-submodules.md)을 통해 GitHub 저장소를 활용할 수 있으며, 가져오기 요청 검증에 사용되는 자동 생성 파이프라인에 대한 제어 기능을 강화하고 코드 스캔 단계에서 중요한 지표에 대한 동작을 정의할 수 있습니다.
   * [GitHub에 보고서 기록을 보존하고 파이프라인 이름을 지정하며 필요에 맞게 파이프라인 변수를 설정할 수도 있습니다.](/help/implementing/cloud-manager/managing-code/github-check-config.md)
* [셀프서비스 콘텐츠 복원](/help/operations/restore.md)은 최대 7일 동안 백업 복원 기능을 제공하며 다음과 같은 기능을 제공합니다.
   * 이전 24시간 동안 특정 시점 백업 복원
   * 최대 7일 동안 고정 시간 복원
* [새로운 OakPal 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-ui-content-package)이 Cloud Manager 코드 품질 검사에 추가되었습니다.
   * 2024년 6월에 추가된 모든 새로운 규칙은 획기적인 변경 사항입니다.
   * 이러한 새로운 규칙으로 인해 Cloud Manager 2024년 8월 릴리스부터 파이프라인에 장애가 발생하므로 가능한 한 빨리 이 문제를 해결해야 합니다.

## 얼리 어답터 프로그램 {#early-adoption}

Adobe의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### Cloud Manager에서의 Edge Delivery Services 지원 {#edge-delivery-services}

Adobe Experience Manager Sites의 일부로 Edge Delivery Services에 라이선스를 부여한 경우, [이제 Cloud Manager에서 Edge Delivery Services를 직접 사이트에 온보딩하고](/help/implementing/cloud-manager/edge-delivery-services.md) 안내식 셀프서비스 경험을 사용하여 라이브로 전환할 수 있습니다.

이를 통해 모든 AEM 속성에 대해 통합된 경험이 가능해지며 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑을 포함한 모든 중요한 워크플로와의 일관성이 보장됩니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `aemcs-cmedgedelsvs-program-adopter@adobe.com`에 이메일을 보내주십시오.

### DV(Domain Validated) 인증서

이제 Cloud Manager를 통해 [DV(Domain Validated) SSL 인증서를 셀프서비스로 생성하고 관리할 수 있습니다.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) 이를 통해 귀하의 온라인 비즈니스를 위한 안전한 웹 사이트를 구축할 수 있는 가장 빠르고 쉬우며 비용 효율적인 솔루션이 제공됩니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `Grp-aemcs-dv-dert-adopter@adobe.com`에 이메일을 보내주십시오.

<!-- RICK: REMOVED THIS SECTION AS PER EMAIL REQUEST TO DL-AEM-DOCS FROM SHWETA DUA, WEDNESDAY, JUNE 12, 2024 ### Client-Side Collection via Real Use Monitoring (RUM) {#rum}

You can leverage the [Real Use Monitoring (RUM) Data Service](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) to enable client-side collection for AEM as a Cloud Service.

Real Use Monitoring (RUM) Data Service offers a more precise reflection of user interactions, ensuring a reliable measure of website engagement. It is a great opportunity to gain advanced insights into your page performance. This is beneficial for customers who use either Adobe-managed CDN or non-Adobe managed CDN. For customers using a non-Adobe managed CDN, automated traffic reporting can now be enabled for them, thus removing the need to share any traffic report with Adobe.

If you are interested in testing this new feature and sharing your feedback, please send an email to `aemcs-rum-adopter@adobe.com` from the email address associated with your Adobe ID. Please include the domain name for production, stage, and dev environments in your email.  Availability of the early adopter program of this feature is limited.-->

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 사용합니다. 공개 또는 인증이 필요한 모든 웹 페이지에 대해 실행할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새 대시보드를 테스트해 보고 싶으십니까? Adobe ID와 연결된 이메일로 `aem-lighthouse-pilot@adobe.com`에 이메일을 보내 주시면 귀하의 시작을 도와드릴 수 있습니다.
