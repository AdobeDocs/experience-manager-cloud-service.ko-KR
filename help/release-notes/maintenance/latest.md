---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d3cdc3d69c0002c5b124150050f905123457331c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 41%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 21193 {#21193}

다음은 2025년 6월 10일에 공개적으로 릴리스된 유지 보수 릴리스 21193에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 21005.

2025.6.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-21193}

* ASSETS-51245: Touch UI의 대용량 폴더 목록에 대한 성능이 향상되었습니다.
* ASSETS-51686: 간편한 작업 취소, 향상된 로깅 및 큰 결과를 위한 감사 다운로드를 포함하여 대량 작업 작업이 개선되었습니다.
* CQ-4360131: API 클라이언트가 올바른 구조화된 오류 정보를 수신할 수 있는 OpenAPI 엔드포인트에 대한 오류 응답이 개선되었습니다.

### 해결된 문제 {#fixed-issues-21193}

* ASSETS-41007: 삭제된 자산은 Content Hub에 계속 표시될 수 있습니다.
* ASSETS-50994: AemRequestEventFilter로 인해 Jetty 스레드가 과도하게 경합됩니다.
* ASSETS-50155: 중복된 메타데이터 변경 이벤트가 트리거되었습니다.
* ASSETS-50716: Assets 목록 보기의 제목별 정렬이 예상대로 작동하지 않습니다.
* ASSETS-50820: 자산 관계 API에 대한 잘못된 요청이 400 오류로 제대로 거부되는지 확인합니다.
* ASSETS-50562: 에셋 업로드 API는 이름 충돌에 대한 기본 동작으로 버전을 생성해야 합니다.
* ASSETS-50992: Assets API initiateUpload.json 엔드포인트는 &#39;application/json&#39;의 컨텐츠 유형을 반환해야 합니다.
* ASSETS-51322: 작업 실패 후 무기한 지속되는 비동기 바리케이드의 자동 제거 및 만료입니다.
* ASSETS-51809: 브라우저 캐싱으로 인해 CSV 편집기에 최근에 저장된 변경 사항이 표시되지 않았습니다.
* SITES-31678: 컨텍스트 인식 참조가 포함된 XF(경험 구성요소)가 XF 게시 API에서 올바른 언어 루트를 해결하지 못했습니다.


### 알려진 문제 {#known-issues-21193}

없음.

### 사용 중단된 기능 및 API {#deprecated-21193}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-21193}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 2개가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-21193}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.29.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
