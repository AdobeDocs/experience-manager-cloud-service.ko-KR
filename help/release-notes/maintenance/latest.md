---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 67b9a5f73f1f8c599e902a0ac0d8efbc614c7f75
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 28%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 X {#X}

다음은 2025년 4월 1일에 공개적으로 릴리스된 유지 보수 릴리스 X에 대한 지속적인 개선 사항입니다. 이전 유지 관리 릴리스는 릴리스 19823.

2025.4.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-X}

FORMS-19068: 양식 데이터 통합 기능을 향상시키기 위해 Forms Manager API에 AEP 커넥터 제출 작업에 대한 지원이 추가되었습니다.

FORMS-18513: AEP Connector에서 데이터 트리 변환 지원을 구현하여 마법사 기능과 데이터 처리 기능을 개선했습니다.

FORMS-18432: OSGI 수준 변경 없이 선택적 미리 채우기 기능을 사용할 수 있도록 양식별(정규 표현식 기반) 클라이언트측 미리 채우기 구성이 구현되었습니다.

FORMS-17551: SharePoint 목록 통합에 대한 DoR(Document of Record) 지원이 추가되었습니다.

### 해결된 문제 {#fixed-issues-X}

FORMS-19028: 클라이언트측 미리 채우기 기능이 양식 이벤트 처리를 중단하여 양식 로드 시 값 커밋 및 DOMContentLoaded 이벤트가 제대로 트리거되지 않도록 합니다.

FORMS-18360: 데이터 조직 및 액세스 제어를 개선하기 위해 Forms 문서 관리의 팀 사이트에 대한 SharePoint 목록 범위 관리를 개선했습니다.

FORMS-18325: 양식 데이터 통합 및 처리 기능을 개선하기 위해 Adobe Experience Platform(AEP) 클라우드 구성을 추가했습니다.

FORMS-18213: 문서 명확성과 사용자 경험을 개선하기 위해 DoR(Document of Record)에서 비활성화된 필드를 숨기거나 제외하는 기능이 구현되었습니다.

FORMS-18189: 빈 클라이언트 라이브러리에 대한 오류 로깅을 방지하고 UI의 오류 표시를 개선하기 위해 사용자 지정 함수 처리를 수정했습니다.

FORMS-18426: 목록 이름에 특수 문자(예: &#39;-&#39;)가 포함된 경우 SharePoint 목록 조회 기능이 실패하여 SharePoint 목록과의 양식 통합에 영향을 줍니다.

FORMS-18375: 특정 구성 컨테이너를 선택하지 않은 경우 Foundation 구성 요소 기반 양식에서 `conf/global` 폴더에서 recaptcha 구성을 잘못 선택합니다.

FORMS-18304: Acrobat 및 LiveCycle ES4에서 유효성 검사를 통과한 PDF/A-1b 문서는 장치 종속적 색상 오류로 인해 AEM 6.5 Forms에서 비호환 문서로 잘못 플래그가 지정됩니다.

FORMS-18271: Forms 테마 편집기에 지역화되지 않은 오류 메시지가 표시되어 양식 구성 및 테마 맞춤화의 사용자 경험에 영향을 줍니다.

FORMS-18068: 리치 텍스트 필드를 사용하는 라디오 버튼 및 확인란 그룹에 대한 DoR(기록 문서)의 굵은 텍스트 렌더링 문제

FORMS-7016: 양식 편집기의 키보드 포커스 순서가 논리 탐색을 따르지 않습니다.

FORMS-6950: 파일 시스템 탐색기 트리뷰 구성 요소에 필요한 ARIA 역할 및 속성을 추가하여 화면 판독기 접근성을 개선하고 WCAG 4.1.2 이름, 역할, 값(레벨 A) 표준을 준수합니다.

### 알려진 문제 {#known-issues-X}

없음.

### 사용 중단된 기능 및 API {#deprecated-X}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-X}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 확인된 X 취약점을 해결하여 강력한 시스템 보호에 대한 약속을 강화합니다.

### 임베드된 기술 {#embedded-tech-X}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
