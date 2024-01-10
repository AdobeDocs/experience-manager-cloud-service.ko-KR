---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 0b4c820159f918cb9b3a93d9ab36dc26b1d8da47
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 97%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 14697 {#release-14697}

2023년 12월 18일에 릴리스된 유지 관리 릴리스 14697의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이는 문제가 있었던 릴리스 14538을 대체합니다. 이전 유지 관리 릴리스는 릴리스 14227이었습니다.

이 유지 관리 릴리스(2023.12.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-14697}

* GRANITE-46723: 사용자 동기화 - 기본 동기화에서 IDP 기반 동기화로의 SAML 마이그레이션입니다.
* OAK-10311: 복제 - AEM에서 대규모 자산 일괄 처리의 복제 시간을 줄이기 위해 Blob 비교를 최적화합니다.
* OAK-10511: 복제 - 네트워크 왕복을 줄여 AEM에서 대규모 자산의 복제 시간을 줄입니다.
* GRANITE-48334: 게시자 - RUM에 대한 컬렉션 스크립트가 누락되었습니다.

### 해결된 문제 {#fixed-issues-14697}

* CQ-4354867: ToggleCondition 참조는 InstanceActionServlet에 존재하지 않는 필드를 의미합니다.
* CQ-4349948: 도구 → 보안 → 사용자 아래의 사용자 설정 편집에서 &#39;프로필 속성&#39; 문자열이 지역화되었습니다.
* GRANITE-44541: 도구 → 보안 → 사용자 아래의 사용자 편집 > 키 저장소의 비공개 키 파일 추가 화면에서 오류 대화 상자가 지역화되었습니다.
* GRANITE-45341: 도구 → 보안 → 사용자 아래의 사용자 작업 활성화/비활성화에 대한 성공/실패 문자열이 지역화되었습니다.
* GRANITE-46650: 도구 → 보안 → 사용자 만들기 대화 상자 아래의 “UserId/암호 불일치” 문자열의 오류 메시지가 지역화되었습니다.
* GRANITE-47764: Sling 모델 API 1.5.0 업데이트: Sling 모델의 정적 변수에 주입하면 컴파일 오류가 발생합니다(SLING-11507).
* GRANITE-48452: 상태 코드 200으로 빈 clientlibs를 보냅니다.
* GRANITE-48410: ResourceResolver가 닫히지 않았습니다.
* ASSETS-31297: 다이내믹 미디어에서 복사된 자산 삭제를 방지합니다.
* ASSETS-30811: Blocktag 서비스 바인딩에 대한 참조 업데이트입니다.
* GRANITE-46418: AEM의 Sling 이벤트 업데이트: GaugeSupport에는 RegisterWithSuffix(SLING-11918)의 무한 재귀가 있습니다.
* GRANITE-48937: Omnisearch가 aem/start.html 페이지에서 작동하지 않는 유지 관리 릴리스 14538의 회귀 문제가 해결되었습니다.

### 알려진 문제 {#known-issues-14697}

* GRANITE-49031: 회귀 결과 `@JsonIgnore` 임시 필드에서 주석이 무시되고 있습니다.

### 임베드된 기술 {#embedded-tech-14697}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.58-T20231123092841-619e1bd | [Oak API 1.58.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.58.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
