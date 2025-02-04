---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a3c414f9b5e575856a942e02661e8c70a7083495
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 89%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 19149 {#19149}

2025년 1월 21일에 릴리스된 유지 관리 릴리스 19149의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 18751이었습니다.

이 유지 관리 릴리스(2025.1.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-19149}

* ASSETS-45286: 다운로드 보관 비동기 작업에 대한 세부적인 진행 상황 표시.
* ASSETS-46296: 자산 선택기에서 Dynamic Media 템플릿 지원.
* ASSETS-44796: DAM 비동기 자산 작업에 대한 자산 이벤트 발생.

### 해결된 문제 {#fixed-issues-19149}

* GRANITE-55074: 오류 응답에 CORS 응답 헤더가 설정되어 있는지 확인 가능.
* ASSETS-43755: 대량 자산 관계에 대한 확장성 개선.
* ASSETS-45399: 자산 Live Copy 생성 후 Assets 콘솔로 리디렉션.
* ASSETS-45462: 사용자 정의 폴더 썸네일의 브라우저 캐싱 문제.
* ASSETS-46398: DM 템플릿에 대한 다운로드 및 재처리 작업 숨기기.
* ASSETS-44484: 연결된 자산 구성을 다시 저장하는 문제.
* ASSETS-44122: 비동기 복사 자산 작업이 현재 폴더로 복사될 때 대상 폴더의 이름이 바뀌지 않음.
* ASSETS-44463: 메타데이터 내보내기가 성공적으로 완료되어도 CSV 다운로드 버튼이 표시되지 않음.
* ASSETS-45134: 대상 제목으로 작업을 이동하면 모든 폴더 제목을 덮어씀.
* ASSETS-45137: 자산 보기를 통한 일괄 업로드와 충돌.
* ASSETS-45758: 자산 관계를 추가한 후 자산 관계에 바쁨/로딩 애니메이션이 무한 표시.
* ASSETS-44148: AEM에서 NODE_MOVED 이벤트로 인해 로그에 잘못된 NPE 발생.
* ASSETS-28607: 사용자 정의 비디오 썸네일을 설정하는 도중 JS 오류 발생.
* GRANITE-55781: Adobe Developer Console과 AEM 간의 그룹 동기화 개선. [사용자 그룹 및 제품 프로필 동기화의 변경 사항](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization)에 대한 추가 세부 정보.
* GRANITE-55754: SDK 시작 스크립트가 Java 21 지원 가능.
* GRANITE-54248: 대용량 자산 폴더의 모든 항목을 스크롤할 수 없음.
* SCRNS-4597: 검색 결과 목록 보기 개선.


### 알려진 문제 {#known-issues-19149}

없음.

### 사용 중단된 기능 및 API {#deprecated-19149}

AEM as a Cloud Service에서 더이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

#### 사용자 그룹 및 제품 프로필 동기화의 변경 사항

권한 관리를 위해 Adobe Admin Console을 사용할 때는 더 이상 AEM과 동기화되지 않으므로 다음 그룹을 사용해서는 안 됩니다.
* _GROUP_NAME_SUFFIX로 끝나는 AEM 그룹.
* 다른 환경, 프로그램 또는 제품의 제품 프로필.

자세한 내용은 [사용자 그룹 및 제품 프로필 동기화의 변경 사항](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization)을 확인해 주십시오.

#### SPA 편집기 사용 중단 {#deprecate-spa-editor}

[SPA 편집기](/help/implementing/developing/hybrid/introduction.md)는 릴리스 2025.1.0부터 새 프로젝트에 대해 더 이상 사용되지 않습니다. SPA 편집기는 기존 프로젝트에 대해 계속 지원되지만 새 프로젝트에 사용해서는 안 됩니다.

AEM에서 Headless 콘텐츠를 관리하기 위한 기본 편집기는 다음과 같습니다.

* 비주얼 편집용 [유니버설 편집기](/help/edge/wysiwyg-authoring/authoring.md).
* 양식 기반 편집용 [콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-managing.md).

### 보안 수정 {#security-19149}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 4개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-19149}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
