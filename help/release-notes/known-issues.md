---
title: 알려진 문제
description: 클라우드 서비스로서의 Adobe Experience Manager의 알려진 문제와 관련된 릴리스 노트
translation-type: ht
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# 알려진 문제 {#known-issues}

이 문서에서는 클라우드 서비스로서의 Adobe Experience Manager의 알려진 문제들을 나열합니다. 이 목록은 Experience Manager의 연속적인 각 릴리스를 통해 수정 및 업데이트됩니다.

알려진 문제에 대한 자세한 내용은 [지원 센터에 문의하십시오](https://helpx.adobe.com/kr/support/experience-manager.html).

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## 자산 {#assets}

<!-- Jira label: assets-cloud-known-issues -->

일부 알려진 문제는 다음과 같습니다.

* **메타데이터 스키마**: 자산 등급 위젯으로 인해 JSP 컴파일 오류가 발생할 수 있습니다. 해결 방법은 메타데이터 스키마에서 자산 등급 구성 요소를 제거하는 것입니다. <!-- CQ-4282865 -->

자산 기능의 일부 제한 사항은 다음과 같습니다.

* 클라우드 서비스로서의 AEM Assets를 사용 시 AEM 6.5 Sites가 AMS에 배포되어 있으면 연결된 자산 기능이 작동합니다.

### 예정된 Assets 기능 {#upcoming-assets-capabilities}

기초 기능이 따라 달라지는 Adobe Experience Manager Assets의 몇 가지 기능이 클라우드 서비스로서의 Adobe Experience Manager 배포 아키텍처에서 아직은 사용할 수 없지만 이후 단계에서 사용할 수 있게 될 예정입니다.

* 이 단계에서는 Brand Portal에 게시 기능을 사용할 수 없습니다. 자산 배포 사용 사례를 위한 [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) 구현을 확장 및 배포할 수 있습니다.
* 현재는 Adobe I/O의 AI 서비스를 활용하는 향상된 스마트 태깅 기능을 사용할 수 없습니다.
* Commerce Integration Framework API에 대한 종속성으로 인해 이 단계에서 사용할 수 없는 기능:
   * 사진 촬영 워크플로우 모델.
   * 자산 속성 사용자 인터페이스의 제품 정보 탭이 채워져 있지 않습니다.
* InDesign 서버 통합에 대한 종속성으로 인해 이 단계에서 사용할 수 없는 기능:
   * 자산 템플릿 및 자산 카탈로그.
   * InDesign 파일의 여러 페이지 미리 보기

>[!MORELIKETHIS]
>
>* [AEM의 주요 변경 사항](aem-cloud-changes.md)
>* [이제 사용되지 않는 기능과 제거된 기능](deprecated-removed-features.md)
>* [릴리스 노트](home.md)

