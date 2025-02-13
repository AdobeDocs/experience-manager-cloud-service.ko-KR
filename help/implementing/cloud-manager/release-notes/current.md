---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.2.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2025.2.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: ee7a99c5bf08b39a743d4b326ac23cc8546c512e
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 18%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.2.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.2.0 릴리스에 대해 알아봅니다.


[Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 참조하세요.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.2.0 릴리스 일자는 2025년 2월 13일 금요일입니다.

다음 릴리스는 2025년 3월 13일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **코드 품질 규칙 업데이트**

  2025년 2월 13일 목요일부터 Cloud Manager 코드 품질 단계는 이제 SonarQube 9.9.5.90363을 사용합니다.

  [이 링크](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)의 AEM as a Cloud Service에서 Cloud Manager에 사용할 수 있는 업데이트된 규칙은 Cloud Manager 파이프라인에 대한 보안 점수 및 코드 품질을 결정합니다.

* SonarQube 9.9는 이제 모든 고객을 위한 기본 코드 품질 검색 엔진입니다.

* **Java 17 및 Java 21 빌드 지원**

  이제 고객은 Java 17 또는 Java 21을 사용하여 빌드할 수 있으므로 성능 향상 및 새로운 언어 기능에 액세스할 수 있습니다. Maven 프로젝트 및 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)을 참조하십시오. 빌드 버전이 Java 17 또는 Java 21로 설정된 경우 배포되는 런타임은 Java 21입니다.

* Edge Delivery Services에 대한 **99.99% SLA 가동 시간 보고**

  이제 자격을 갖춘 Edge Delivery Services 프로그램에 고가용성 99.99% 가동 시간 보고를 사용할 수 있습니다. 이 기능을 활성화하려면 고객이 Edge Delivery Services 사이트를 성공적으로 온보딩하고 Cloud Manager 내에서 99.99% Service level agreement(SLA)를 적용해야 합니다.

  [SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)도 참조하세요.

* **Edge Delivery Services에 대한 사용자 초대 환경 개선**

  Edge Delivery Services과 연관된 콘텐츠 저장소로 사용자를 초대하는 기능이 개선되었습니다. <!-- CMGR-65331 -->

* **게시 인스턴스에 관리자 프로필을 자동으로 만들기**

  이전에는 Cloud Manager에서 게시 인스턴스에 관리자 프로필을 수동으로 만들 수 있었지만 기본적으로 자동 만들기를 지원하지 않았습니다. 이 업데이트를 통해 이제 게시 인스턴스에 관리자 프로필이 자동으로 만들어져 유용성이 향상되고 고객의 설정 시간이 단축됩니다.

  자세한 내용은 [사용자 지정 권한](/help/implementing/cloud-manager/custom-permissions.md)을 참조하세요.

  ![파이프라인 활동 필터링](/help/implementing/cloud-manager/release-notes/assets/product-profiles.png)

* **Cloud Service 환경을 위한 OAuth로 전환**

  이제 새로운 Cloud Service 환경에서는 이전에 사용한 JWT 인증 방법 대신 Adobe Developer Console 통합 프로젝트에 대한 OAuth 기반 서비스 간 인증을 사용합니다. JWT 인증은 더 이상 사용되지 않으며 2025년 6월에 사용이 종료됩니다.

* **EC(Elliptic Curve) 개인 키 지원(secp384r1)**

  Cloud Manager은 이제 `secp384r1` EC(Elliptic Curve) 개인 키를 지원하여 고객 관리 OV/EV SSL 인증서에 대한 향상된 보안 및 규정 준수를 제공합니다.
자세한 내용은 [고객 관리 OV/EV SSL 인증서 요구 사항](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)을 참조하십시오. <!-- CMGR-63636 -->

* **특수 테스트 환경**

  향상된 리소스가 포함된 새로운 개발 환경은 2025년 2월 27일부터 얼리어답터가 사용할 수 있습니다.


<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## 버그 수정

* **(UI) Cloud Manager의 도메인에 대해 CDN 구성을 방해하는 문제를 해결했습니다.**
Cloud Manager에서 CDN 구성을 추가하려는 고객이 드롭다운 메뉴에서 도메인을 선택하면 화면 오류가 발생합니다. 이 사용자 인터페이스 버그로 인해 프로덕션 환경의 도메인 매핑이 차단되어 구성 프로세스가 차단되었습니다.

  또한 사용자 인터페이스에서 제거되었지만 백엔드에서 일부 도메인에 액세스할 수 없는 상태가 유지되었습니다. 이 문제로 인해 기존 CDN 구성과 충돌이 발생했습니다.

  이 수정 사항으로 이제 오류가 발생하지 않고 드롭다운에서 도메인을 성공적으로 선택할 수 있습니다. 도메인 재구성을 방해하는 백엔드 불일치가 해결되었습니다. 마지막으로, 유효성 검사를 개선하여 충돌하는 도메인을 다시 추가하기 전에 올바르게 제거하도록 합니다.<!-- CMGR-64888 -->
* **(백엔드) SSL 만료 알림이 여러 번 전송되는 문제를 해결했습니다.**
매일 자정에 한 번 실행되도록 설계된 SSL 만료 알림 스케줄러가 매일 자정에 한 번, 오전 12시 30분에 두 번 잘못 트리거되는 버그가 확인되었습니다. 이 문제로 인해 만료 중인 SSL 인증서와 관련하여 중복 알림이 여러 개 전송되었습니다.

  이제 알림 스케줄러가 의도한 대로 하루에 한 번만 올바르게 실행됩니다. 또한 더 이상 중복 SSL 만료 알림을 받지 않습니다. <!-- CMGR-64748 -->




<!-- ## Known issues {#known-issues} -->
