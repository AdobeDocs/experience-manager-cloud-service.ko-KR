---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.1.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2025.1.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: befb092169e2278a9e84c183d342003ef325c71e
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 9%

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

* **&quot;CDN 구성&quot;이 &quot;도메인 매핑&quot;으로 이름이 변경됨 :** AEM Cloud Manager의 사용자 인터페이스 개선 사항의 일부로 이제 &quot;CDN 구성&quot; 레이블의 이름이 &quot;도메인 매핑&quot;으로 변경됩니다. 이 변경 사항은 기능과 함께 용어 정렬을 향상시킵니다. <!-- CMGR-64738 -->

  ![&quot;CDN 구성&quot;이 사용자 인터페이스에서 &quot;도메인 매핑&quot;으로 이름이 변경됨](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)

* **한 번의 클릭으로 Edge Delivery 사이트 프로비저닝:** 이제 Cloud Manager을 통해 적절한 권한과 라이선스가 있는 사용자가 한 번의 클릭으로 샘플 Edge Delivery Services 사이트를 만들 수 있습니다. 이렇게 간소화된 프로세스는 다음과 같은 자동화된 기능을 제공합니다.

   * **GitHub 통합** - 기존 조직 내에 GitHub 리포지토리를 자동으로 만들고, Edge Delivery Services을 위한 표준 템플릿으로 사전 구성합니다.
   * **AEM 코드 동기화 앱 설치** - 저장소에 AEM 코드 동기화 응용 프로그램을 설치하여 원활한 동기화 및 배포를 보장합니다.
   * **컨텐츠 Collaboration 설정** - 컨텐츠 저장소에 대해 지정된 Google 드라이브 폴더를 연결하여 컨텐츠 관리를 위한 공동 작업 환경을 제공합니다.
   * **콘텐츠 게시** - 이제 사용자는 Cloud Manager 사용자 인터페이스에서 직접 프로비저닝된 사이트의 콘텐츠를 게시하여 워크플로를 단순화하고 효율성을 향상시킬 수 있습니다.
   * **향상된 Collaboration** - 이 플랫폼을 통해 사용자는 Google Drive 콘텐츠 저장소 폴더에 여러 공동 작업자를 추가할 수 있으므로 팀워크와 콘텐츠 기여가 향상됩니다.

  이러한 개선 사항은 자동화를 개선하고, 설정 프로세스를 간소화하며, Edge Delivery Services 사용자의 공동 작업을 향상시키는 것을 목표로 합니다. <!-- CMGR-59362 -->

  ![Edge Delivery 사이트 프로비저닝](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

  ![Edge Delivery 사이트 프로비저닝 대화 상자](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)

* **Edge Delivery Services 사이트에 대한 향상된 지원:** Cloud Manager은 이제 최신 Edge Delivery Services 사이트에 대한 온보딩을 지원합니다. 이 업데이트에는 CDN 및 게재 스택에 대한 포괄적인 리팩터링이 포함되어 있어 견고성 및 유지 관리성이 향상됩니다.

* **얼리 어답터 프로그램 업데이트 - Bitbucket 및 GitLab에 대한 PR 유효성 검사 지원:** Cloud Manager은 이제 Bitbucket 및 GitLab의 클라우드 및 자체 호스팅 버전에 대한 PR(가져오기 요청) 유효성 검사를 지원합니다. 이 기능을 사용하면 고객이 PR을 병합하기 전에 Adobe의 코드 품질 임계값에 대해 코드 변경 사항을 테스트할 수 있습니다. 이 향상된 기능은 병합 전에 더 높은 코드 품질을 보장함으로써 프로덕션 파이프라인의 코드 변경 성공률을 크게 향상시켜 마켓 출시 시간을 단축하고 개발 워크플로우를 간소화합니다.

이제 GitLab 및 Bitbucket에 대한 지원을 통해 &quot;자신만의 Git을 가져오세요&quot;에 대한 자세한 정보와 얼리 어답터로 등록하려면 [Cloud Manager 2024년 10월 릴리스 노트](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md##gitlab-bitbucket)를 참조하십시오.

* **파이프라인에 대한 고급 필터링 옵션:** 이제 Cloud Manager에는 파이프라인 페이지의 고급 필터링 옵션이 있으므로 관련 데이터에 빠르게 액세스하고 배포 효율성을 향상시킬 수 있습니다. 몇 가지 주요 기능은 다음과 같습니다.

   * **다중 기준 필터링:** 파이프라인 이름, 환경 및 배포 코드와 같은 필터를 사용하여 검색 결과를 구체화합니다.
   * **파이프라인 검색 간소화:** 더 빠른 탐색과 향상된 워크플로 관리를 위해 특정 파이프라인을 쉽게 찾을 수 있습니다.

  이러한 향상된 기능을 통해 보다 효율적이고 사용자 친화적으로 파이프라인을 관리하고 배포할 수 있습니다.

  ![파이프라인 필터 기능](/help/implementing/cloud-manager/release-notes/assets/pipeline-filters.png)

* Edge Delivery 서비스에 대한 **셀프 서비스 CDN 구성:** 이제 Edge Delivery 서비스의 새 채택자가 Cloud Manager을 통해 독립적으로 CDN을 구성할 수 있습니다. 이 업데이트는 `.hlx.page/live`에서 새 `.aem.page/live`(으)로 지원을 확장하여 사용자에게 보다 유연하고 능률적인 설정을 제공합니다.


<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->

<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
