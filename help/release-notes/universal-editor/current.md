---
title: Universal Editor 2024.08.13 릴리스 노트
description: 다음은 범용 편집기 2024.08.13 릴리스의 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: aad4d0353fb5e2eacb518b72e935def931d0798a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Universal Editor 2024.08.13 릴리스 노트 {#release-notes}

다음은 범용 편집기 2024년 8월 13일 릴리스의 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **사용자 지정 데이터 형식**: 속성 패널에서 사용자 지정 필드를 만드는 기능을 사용하여 편집기를 고유한 데이터 요구 사항에 맞게 설정합니다.
   * 상거래 사용 사례에 대한 사용자 지정 제품 선택기를 개발하든, 백엔드의 값으로 드롭다운 목록을 채우든 간에, 이 기능은 작성자가 콘텐츠를 작성하는 데 사용하는 데이터에 대해 필요한 제어를 제공합니다.
* **컨테이너 간 드래그 앤 드롭**: [콘텐츠 트리 패널 내에서 드래그 앤 드롭을 통해 [다른 컨테이너에서 구성 요소를 이동](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components)할 수 있으므로 레이아웃 구성을 보다 유연하게 사용할 수 있습니다.](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode)
* **최적화된 GitHub 통합**: GitHub 응답에 대한 캐싱이 도입되어 태그 및 `universal-editor-cors-library` 검색 속도가 크게 빨라져 사용자 경험이 더 빠르고 매끄러워졌습니다.
* **Managed Services RPM 패키지**: 이제 Adobe에서 범용 편집기 서비스의 배포 및 관리를 간소화하는 RPM 패키지를 제공하여 유지 관리를 단순화하고 관리 서비스의 운영 오버헤드를 줄입니다.
* **구성 가능한 IMS 토큰 유효성 검사**: 토큰 관리의 유연성을 높이기 위해 IMS 토큰 유효성 검사는 이제 선택 사항입니다.
   * 이 구성 옵션을 사용하면 필요에 따라 유효성 검사를 비활성화하여 클라우드 게이트웨이 설정을 단순화할 수 있습니다.
* **Splunk 통합**: Splunk 로깅이 로컬 개발을 위해 [Universal Editor Service에 통합되었습니다.](/help/implementing/universal-editor/local-dev.md) 모니터링 및 진단을 개선했습니다.
   * 이 통합을 통해 효율적인 로그 추적, 더 원활한 작업 및 더 빠른 문제 해결을 수행할 수 있습니다.

## 버그 수정 {#bug-fixes}

* **향상된 게시 피드백**: 권한 부족으로 인해 게시가 실패하는 경우 게시 중 사용자에게 보내는 피드백이 단순히 실패를 표시하는 대신 명확한 경고를 표시하도록 개선되었습니다.
* **향상된 URL 처리**: 게시 실패를 일으키는 잘못된 URL 인코딩/디코딩 문제가 수정되었습니다.
* **정확한 데이터 처리**: 부동 소수점이 정수로 잘못 저장된 문제가 해결되어 콘텐츠 전반에서 정확한 데이터 처리가 보장됩니다.
* **보안 및 안정성**: 도커 이미지의 보안 취약점이 해결되었으며 구성 요소 선택기 및 탐색 표시와 같은 중요한 구성 요소에 대한 테스트 적용 범위가 구현되었으므로 보다 안전하고 안정적이며 안정적인 편집기 환경이 구축되었습니다.
