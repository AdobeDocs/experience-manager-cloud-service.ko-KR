---
title: 알려진 문제
description: 클라우드 서비스로서 Adobe Experience Manager의 알려진 문제와 관련된 릴리스 노트
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# 알려진 문제 {#known-issues}

이 문서에서는 클라우드 서비스 솔루션으로 알려진 Adobe Experience Manager의 문제점을 나열합니다. 목록은 Experience Manager의 각 연속 릴리스로 개정되고 업데이트됩니다.

[알려진 문제에 대한 자세한 내용은 지원](https://helpx.adobe.com/support/experience-manager.html) 센터에 문의하십시오.

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## 자산 {#assets}

<!-- Jira label: assets-cloud-known-issues -->

일부 알려진 문제는 다음과 같습니다.

* **메타데이터 스키마**:자산 등급 위젯으로 인해 JSP 컴파일 오류가 발생할 수 있습니다. 해결 방법은 메타데이터 스키마에서 자산 등급 구성 요소를 제거하는 것입니다. <!-- CQ-4282865 -->

자산 기능의 일부 제한 사항은 다음과 같습니다.

* AEM Assets를 클라우드 서비스로 사용하면 AEM 6.5 사이트가 AMS에 배포될 때 연결된 에셋 기능이 작동합니다.

### 향후 자산 기능 {#upcoming-assets-capabilities}

Adobe Experience Manager에서 아직 클라우드 서비스 배포 아키텍처로 사용할 수 없는 기본 기능을 기반으로 하는 Adobe Experience Manager Assets의 몇 가지 기능이 향후 출시될 예정입니다.

* 이 단계에서는 브랜드 포털에 게시할 수 없습니다. 자산 배포 사용 사례를 [위해 자산 공유](https://adobe-marketing-cloud.github.io/asset-share-commons/) 구현을 확장 및 배포할 수 있습니다.
* Adobe I/O의 AI 서비스를 활용하는 고급 태그 지정 기능은 현재 제공되지 않습니다.
* Commerce Integration Framework API에 대한 종속성으로 인해 이 단계에서 기능을 사용할 수 없습니다.
   * 사진 촬영 워크플로우 모델
   * 자산 속성 사용자 인터페이스의 제품 정보 탭이 채워지지 않습니다.
* InDesign Server 통합에 대한 종속성으로 인해 이 단계에서 기능을 사용할 수 없습니다.
   * 자산 템플릿 및 자산 카탈로그를 참조하십시오.
   * InDesign 파일의 여러 페이지 미리 보기

>[!MORELIKETHIS]
>
>* [AEM의 주요 변경 사항](aem-cloud-changes.md)
>* [사용 중단되거나 제거된 기능](deprecated-removed-features.md)
>* [릴리스 노트](home.md)

