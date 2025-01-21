---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a091dd6b1b69d77f9eeb50065e8946af0133f4f9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 37%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 19149 {#19149}

2025년 1월 21일에 공개적으로 릴리스된 유지 보수 릴리스 19149에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이전 유지 관리 릴리스는 릴리스 18751.

이 유지 관리 릴리스(2025.1.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-19149}

* ASSETS-45286: 다운로드 보관 비동기 작업에 대한 세부 진행 상황을 표시합니다.
* ASSETS-46296: 에셋 선택기에서 Dynamic Media 템플릿 지원
* ASSETS-44796: DAM 비동기 자산 작업에 대해 Assets 이벤트를 실행합니다.

### 해결된 문제 {#fixed-issues-19149}

* GRANITE-55074: 오류 응답에 CORS 응답 헤더가 설정되어 있는지 확인합니다.
* ASSETS-43755: 벌크 에셋과 관련되도록 확장성이 개선되었습니다.
* ASSETS-45399: 에셋 라이브 카피를 만든 후 Assets 콘솔로 리디렉션합니다.
* ASSETS-45462: 사용자 지정 폴더 썸네일과 관련된 브라우저 캐싱 문제.
* ASSETS-46398: DM 템플릿에 대한 다운로드 및 재처리 작업을 숨깁니다.
* ASSETS-44484: 연결된 Assets 구성을 다시 저장하는 데 문제가 있습니다.
* ASSETS-44122: 비동기 자산 복사 작업은 현재 폴더에 복사할 때 대상 폴더의 이름을 변경하지 않습니다.
* ASSETS-44463: 성공적인 메타데이터 내보내기 시 CSV 다운로드 버튼이 표시되지 않습니다.
* ASSETS-45134: 대상 제목을 가진 이동 작업은 모든 폴더 제목을 무시합니다.
* ASSETS-45137: Assets 보기를 통한 벌크 업로드와 충돌합니다.
* ASSETS-45758: 관계를 추가한 후 에셋 관계가 무한 사용/로드 애니메이션을 받습니다.
* ASSETS-44148: AEM의 NODE_MOVED 이벤트로 인해 로그에 불필요한 NPE가 발생할 수 있습니다.
* ASSETS-28607: 사용자 지정 비디오 썸네일을 설정할 때 JS 오류가 발생합니다.
* GRANITE-55781: Adobe Developer Console과 AEM 간의 그룹 동기화를 개선합니다. [사용자 그룹 및 제품 프로필 동기화의 변경 내용](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization)에 자세히 설명되어 있습니다.
* GRANITE-55754: SDK 시작 스크립트가 Java 21을 지원하는지 확인합니다.
* GRANITE-54248: 큰 에셋 폴더의 모든 항목을 스크롤할 수 없습니다.
* SCRNS-4597: 검색 결과 목록 보기 개선 사항.


### 알려진 문제 {#known-issues-19149}

없음.

### 사용 중단된 기능 및 API {#deprecated-19149}

권한 관리에 Adobe Admin Console을 사용하는 경우 다음 그룹은 더 이상 AEM에 동기화되지 않으므로 사용해서는 안 됩니다.
* _GROUP_NAME_SUFFIX로 끝나는 AEM 그룹.
* 다른 환경, 프로그램 또는 제품의 제품 프로필.

자세한 내용은 [사용자 그룹 및 제품 프로필 동기화의 변경](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization)을 확인하세요.


AEM as a Cloud Service에서 더이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-19149}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 4개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-19149}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.72.0 | [Oak API 1.72.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
