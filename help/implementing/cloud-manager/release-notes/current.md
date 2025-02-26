---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.2.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2025.2.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: aaef376b733c10643e44205e55a0921c22008990
workflow-type: ht
source-wordcount: '639'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.2.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.2.0 릴리스에 대해 알아봅니다.


또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.2.0 릴리스 일자는 2025년 2월 13일 목요일입니다.

다음 릴리스는 2025년 3월 13일 목요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **코드 품질 규칙 업데이트**

  2025년 2월 13일 목요일부터 Cloud Manager 코드 품질 단계는 SonarQube 9.9.5.90363을 사용합니다.

  [이 링크](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)에서 AEM as a Cloud Service의 Cloud Manager에 대해 사용할 수 있는 업데이트된 규칙은 Cloud Manager 파이프라인의 보안 점수와 코드 품질을 결정합니다.

* SonarQube 9.9는 이제 모든 고객을 위한 기본 코드 품질 스캐닝 엔진입니다.

* **Java 17 및 Java 21 빌드 지원**

  이제 Java 17 또는 Java 21을 사용하여 성능 향상 및 새로운 언어 기능을 활용할 수 있습니다. Maven 프로젝트 및 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)을 참조하십시오. 빌드 버전이 Java 17 또는 Java 21로 설정된 경우 배포되는 런타임은 Java 21입니다.

* **Edge Delivery Services에 대한 99.99% SLA 가동 시간 보고 기능**

  고가용성을 위한 99.99% 가동 시간 보고 기능이 적격 Edge Delivery Services 프로그램에서 제공됩니다. 이 기능을 활성화하려면 Cloud Manager에서 Edge Delivery Services 사이트 온보딩을 완료하고 99.99% SLA(서비스 수준 계약)를 적용해야 합니다.

  [SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)를 참조하십시오.

* **Edge Delivery Services에 대한 사용자 초대 경험 개선**

  Edge Delivery Services와 연결된 콘텐츠 저장소로 사용자를 초대하는 기능이 개선되었습니다. <!-- CMGR-65331 -->

* **게시 인스턴스에서 관리자 프로필 자동 생성**

  이전에는 Cloud Manager에서 게시 인스턴스에 대한 관리자 프로필을 수동으로 생성할 수 있었지만 기본적으로 자동 생성 기능이 지원되지 않았습니다. 이번 업데이트를 통해 게시 인스턴스에서 관리자 프로필이 자동으로 생성되어 사용 편의성이 향상되고 설정 시간이 단축되었습니다.

  자세한 내용은 [사용자 정의 권한](/help/implementing/cloud-manager/custom-permissions.md)을 참조하십시오.

  ![파이프라인 활동 필터링](/help/implementing/cloud-manager/release-notes/assets/product-profiles.png)

* **OAuth for Cloud Service 환경으로 전환**

  새로운 Cloud Service 환경에서는 Adobe Developer Console 통합 프로젝트에 이전의 JWT 인증 방식 대신 OAuth 기반 서비스 간 인증을 사용합니다. JWT 인증 방식은 더 이상 지원되지 않으며, 2025년 6월에 서비스가 종료됩니다.

* **EC(타원 곡선) 비공개 키 지원 (secp384r1)**

  Cloud Manager에서 `secp384r1` EC(타원 곡선) 비공개 키를 지원하여 고객이 관리하는 OV/EV SSL 인증서의 보안성과 규정 준수 수준이 향상되었습니다.
자세한 내용은 [고객 관리 OV/EV SSL 인증서 요구 사항](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements)을 참조하십시오. <!-- CMGR-63636 -->

* **전문화된 테스트 환경**

  2025년 2월 27일부터 얼리 어답터에 대해 향상된 리소스를 갖춘 새로운 개발 환경이 제공됩니다.


<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## 버그 수정

* **(UI) Cloud Manager에서 도메인에 대한 CDN 구성 문제가 수정되었습니다.**
Cloud Manager에서 도메인에 대한 CDN 구성을 추가할 때 드롭다운 메뉴에서 도메인을 선택하면 화면 오류가 발생하는 문제가 수정되었습니다. 이 사용자 인터페이스 버그로 인해 프로덕션 환경에서 도메인 매핑이 차단되어 CDN 구성을 진행할 수 없었습니다.

  또한 일부 도메인이 사용자 인터페이스에서 제거되었음에도 백엔드에서 계속 액세스할 수 없는 문제가 발생하여 기존 CDN 구성과 충돌이 발생했습니다.

  이번 수정을 통해 이제 드롭다운에서 도메인을 정상적으로 선택할 수 있습니다. 도메인 재구성을 차단하는 백엔드의 불일치 문제도 해결되었습니다. 또한 개선된 유효성 검사를 통해 충돌하는 도메인을 올바르게 제거한 후 다시 추가할 수 있습니다.<!-- CMGR-64888 -->
* **(백엔드) SSL 만료 알림이 여러 번 전송되는 문제가 해결되었습니다.**
SSL 만료 알림 스케줄러는 원래 자정에 한 번 실행되도록 설정되어 있었으나, 자정과 오전 12시 30분에 두 번 실행되는 오류가 발생하여 만료되는 SSL 인증서에 대해 중복된 알림이 전송되었습니다.

  이번 수정으로 인해 알림 스케줄러가 하루 한 번만 실행되며, 더 이상 중복된 SSL 만료 알림을 받지 않게 됩니다. <!-- CMGR-64748 -->




<!-- ## Known issues {#known-issues} -->
