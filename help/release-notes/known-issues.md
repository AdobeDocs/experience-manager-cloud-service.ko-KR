---
title: 알려진 문제
description: Adobe Experience Manager as a Cloud Service의 알려진 문제와 관련된 릴리스 노트
translation-type: tm+mt
source-git-commit: 165dc4af656ce1bc431d2f921775ebda4cf4de9f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---


# 알려진 문제 {#known-issues}

이 문서에서는 Adobe Experience Manager as a Cloud Service의 알려진 문제들을 나열합니다. 이 목록은 Experience Manager의 연속적인 각 릴리스를 통해 수정 및 업데이트됩니다.

알려진 문제에 대한 자세한 내용은 [지원 센터에 문의하십시오](https://helpx.adobe.com/kr/support/experience-manager.html).

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## 자산 {#assets}

<!-- Jira label: assets-cloud-known-issues -->

일부 알려진 문제는 다음과 같습니다.

* **메타데이터 스키마**: 사용된 자산 등급 위젯으로 인해 JSP 컴파일 오류가 발생했습니다. 메타데이터 스키마에서 제거되었습니다. <!-- CQ-4282865, CQ-4284633 -->

### 예정된 Assets 기능 {#upcoming-assets-capabilities}

기초 기능이 따라 달라지는 Adobe Experience Manager Assets의 몇 가지 기능이 Experience Manager as a Cloud Service 배포 아키텍처에서 아직은 사용할 수 없지만 이후 단계에서 사용할 수 있게 될 예정입니다.

* Commerce Integration Framework API에 대한 종속성으로 인해 이 단계에서 사용할 수 없는 기능:
   * 사진 촬영 워크플로우 모델.
   * 자산 속성 사용자 인터페이스의 제품 정보 탭이 채워져 있지 않습니다.
* InDesign 서버 통합에 대한 종속성으로 인해 이 단계에서 사용할 수 없는 기능:
   * 자산 템플릿 및 자산 카탈로그
   * Adobe InDesign 파일의 여러 페이지 미리 보기

>[!MORELIKETHIS]
>
>* [AEM의 주요 변경 사항](aem-cloud-changes.md)
>* [이제 사용되지 않는 기능과 제거된 기능](deprecated-removed-features.md)
>* [릴리스 노트](home.md)

