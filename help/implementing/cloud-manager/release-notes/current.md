---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.1.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2025.1.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: f6c1aa32647bcabeb0781973f81b75c11edc6a5d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 19%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.1.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.1.0 릴리스에 대해 알아봅니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.1.0 릴리스 날짜는 2025년 1월 22일 수요일입니다.

다음 릴리스는 2025년 2월 13일 금요일에 예정되어 있습니다.


## 새로운 기능 {#what-is-new}

* **코드 품질 규칙 - SonarQube 서버 업그레이드:** Cloud Manager 코드 품질 단계는 2025년 2월 13일 목요일로 예정된 Cloud Manager 2025.2.0 릴리스에서 SonarQube Server 9.9를 사용하여 시작됩니다.

준비를 위해 업데이트된 SonarQube 규칙을 [코드 품질 규칙](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)에서 사용할 수 있습니다.

다음 파이프라인 텍스트 변수를 설정하여 새 규칙을 &quot;조기 확인&quot;할 수 있습니다.

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

또한 다음 변수를 설정하여 동일한 커밋에 대해 코드 품질 단계가 실행되도록 합니다(일반적으로 동일한 `commitId`에 대해 건너뜀).

`CM_DISABLE_BUILD_REUSE` = `true`

![변수 구성 페이지](/help/implementing/cloud-manager/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe은 기본 프로덕션 파이프라인과 동일한 분기로 구성된 새 CI/CD 코드 품질 파이프라인을 만들 것을 권장합니다. 2025년 2월 13일 릴리스에서 적절한 변수를 *이전*&#x200B;으로 설정하여 새로 적용된 규칙이 차단기를 도입하지 않는지 확인하십시오.

* **Java 17 및 Java 21 빌드 지원:** 고객은 이제 Java 17 또는 Java 21을 사용하여 빌드할 수 있으므로 성능 향상 및 새로운 언어 기능에 액세스할 수 있습니다. Maven 프로젝트 및 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)을 참조하십시오. 빌드 버전이 Java 17 또는 Java 21로 설정된 경우 배포되는 런타임은 Java 21입니다.

   * **기능 활성화**
      * 이 기능은 2025년 2월 13일 목요일에 모든 고객에 대해 활성화되고 새로운 SonarQube 버전의 기본 롤아웃이 시작됩니다.
      * 고객은 SonarQube 9.9 버전을 업그레이드하기 위해 위에 설명된 두 가지 변수 구성을 설정하여 *즉시*&#x200B;이 기능을 사용할 수 있습니다.

   * **Java 21 런타임 배포**
      * Java 21 런타임은 Java 17 또는 Java 21을 사용하여 빌드할 때 배포됩니다.
      * 모든 Cloud Manager 환경에 대한 점진적 롤아웃은 샌드박스 및 개발 환경의 경우 2월에 시작되며 4월에 프로덕션 환경으로 확장됩니다.
      * Java 21 런타임 *이전*&#x200B;을(를) 채택하려는 Java 11을 사용하여 빌드하는 고객은 [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)에서 Adobe에 문의할 수 있습니다.

* **&quot;CDN 구성&quot;이 &quot;도메인 매핑&quot;으로 이름이 변경되었습니다.** AEM Cloud Manager의 사용자 인터페이스 개선 사항의 일부로 이제 &quot;CDN 구성&quot; 레이블의 이름이 &quot;도메인 매핑&quot;으로 바뀌어 기능에 대한 용어 정렬이 개선되었습니다. <!-- CMGR-64738 -->

  ![&quot;CDN 구성&quot;이 사용자 인터페이스에서 &quot;도메인 매핑&quot;으로 이름이 변경됨](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)


<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->

<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
