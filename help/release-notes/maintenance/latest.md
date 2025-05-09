---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 437125b6819edf70539ebacb4a8beddb755fcb7a
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 30%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 20626 {#20626}

다음은 2025년 4월 29일에 공개적으로 릴리스된 유지 보수 릴리스 20626에 대한 지속적인 개선 사항을 요약한 것입니다. 이전 유지 관리 릴리스는 릴리스 20476.

2025.5.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-20626}

* ASSETS-46413, ASSETS-46580: 새 검토 상태 &quot;미리보기&quot;가 추가되었습니다.
* ASSETS-49542: 비디오 및 오디오 기록 및 번역에 지원되는 언어를 확장합니다.
* ASSETS-48264: 렌디션에 대한 PNG 품질 지원 확장.

### 해결된 문제 {#fixed-issues-20626}

* ASSETS-50387: GenStudio에서 사용할 컨텐츠 조각 기본 썸네일 수정.
* ASSETS-49006: 사용자에게 쓰기 권한이 없는 경우 비디오 속성을 표시합니다.
* ASSETS-46757, ASSETS-46997: 스마트 자르기 편집기에서 접근성을 개선합니다.
* ASSETS-48018: Assets 게시 보고서에서 에셋 참조 추적을 개선합니다.
* ASSETS-35846: 작성자와 게재 계층 간 액세스 일관성을 개선합니다.
* ASSETS-48171: 캔버스를 사용하여 Dynamic Media 템플릿의 일관성을 개선합니다.
* ASSETS-49813: 만료 알림을 개선합니다.
* ASSETS-47768, ASSETS-49825, ASSETS-49008, ASSETS-48287: 대량 작업에 대한 관리 및 가시성을 개선합니다.
* ASSETS-50003, ASSETS-50004: 에셋 다운로드에 포함된 렌디션에 대한 이름 지정 및 제어 기능을 개선합니다.
* ASSETS-47939: Content Hub에 대한 응답 구성을 개선합니다.
* ASSETS-46738: 매우 큰 컬렉션의 성능을 개선합니다.
* ASSETS-50121: 에셋 게시 이벤트의 안정성을 개선합니다.
* ASSETS-48490: 이미지 수집 중 자동화된 처리의 복원력을 개선합니다.
* ASSETS-28106, ASSETS-49404: 전체 텍스트 검색의 견고성을 개선합니다.
* ASSETS-50006, ASSETS-50423: 큰 폴더 내에서 검색 및 순회 성능을 개선합니다.
* ASSETS-46021: Safari 및 모바일 브라우저에 대한 비디오 표시를 개선합니다.
* ASSETS-49002: Dynamic Media 템플릿 편집 처리를 개선합니다.
* ASSETS-48376: Content Hub UI의 기타 개선 사항.
* ASSETS-48504, ASSETS-49378: UI 동작에 대한 기타 개선 사항입니다.
* ASSETS-49540: 자산 관계 OpenAPI를 실험 단계 외부로 이동합니다.
* ASSETS-40284: Adobe Stock 통합에 대한 설명서를 업데이트합니다.
* ASSETS-49739: 자산 선택기에서 Figma를 통합합니다.

#### AEM 안내서 {#guides}

* GUIDES-21734: XMLEditorConfig에서 ID 자동 생성 옵션을 활성화한 경우에도 이러한 요소가 스니펫을 통해 추가되거나 템플릿을 통해 만들어지면 요소에 대해 새 ID가 생성되지 않습니다.
* GUIDES-25969: DITA 주제의 외부 링크에서 `scope=external` 특성이 누락된 경우 특히 마이크로서비스가 활성화된 경우 오류 로그에서 이 특성이 누락된 파일을 표시하지 않고 HTML5 게시가 실패합니다.
* GUIDES-27288: 새 AEM Sites 게시를 사용하여 생성된 랜딩 페이지를 매핑하기 위해 메타데이터 속성을 전달할 수 없습니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

### 알려진 문제 {#known-issues-20626}

없음.

### 사용 중단된 기능 및 API {#deprecated-20626}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-20626}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 11개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-20626}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.78.0 | [Oak API 1.78.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
