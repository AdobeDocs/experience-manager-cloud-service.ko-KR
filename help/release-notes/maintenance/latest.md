---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 2677e8fbdf6b21ce2d1d848000401c826bc5f289
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 30%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 14538 {#release-14538}

다음은 2023년 12월 6일에 공개적으로 릴리스된 유지 보수 릴리스 14538에 대한 지속적인 개선 사항을 요약합니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 정보의 14227.

2023.12.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-14538}

* GRANITE-46723: 사용자 동기화 - 기본 동기화에서 IDP 기반 동기화로의 SAML 마이그레이션.
* OAK-10311: 복제 - Blob 비교를 최적화하여 AEM에서 큰 자산 배치의 복제 시간을 단축합니다.
* OAK-10511: 복제 - 네트워크 라운드 트립을 줄여 AEM의 대용량 에셋의 복제 시간을 단축합니다.
* GRANITE-48334: RUM에 대한 게시자 - 컬렉션 스크립트가 없습니다.

### 해결된 문제 {#fixed-issues-14538}

* CQ-4354867: ToggleCondition 참조가 InstanceActionServlet에 존재하지 않는 필드를 참조합니다.
* CQ-4349948: 사용자 → 보안 아래의 사용자 설정 편집에서 &#39;프로필 속성&#39; 문자열→ 지역화입니다.
* GRANITE-44541: 도구 → 보안 → 사용자 아래의 사용자 편집 > 키 저장소의 개인 키 파일 화면 추가 시 오류 대화 상자의 지역화.
* GRANITE-45341: 도구 → 보안 → 사용자 아래의 사용자 작업 활성화/비활성화에 대한 성공/실패 문자열의 현지화.
* GRANITE-46650: 오류 메시지 &quot;사용자 ID/암호 불일치&quot;의 지역화입니다. [도구] → [보안] → [사용자 만들기] 대화 상자의 문자열
* GRANITE-47764: Sling 모델 API 1.5.0으로 업데이트: Sling 모델의 정적 변수에 삽입하면 컴파일 오류가 발생합니다(SLING-11507).
* GRANITE-48452: 상태 코드 200으로 빈 clientlib을 보냅니다.
* GRANITE-48410: ResourceResolver가 닫히지 않았습니다.
* ASSETS-31297: Dynamic Media에서 복사한 에셋을 삭제하지 마십시오.
* ASSETS-30811: 바인딩된 Blocktag 서비스에 대한 참조 업데이트입니다.
* GRANITE-46418: AEM에서 Sling 이벤트 업데이트: GaugeSupport에 registerWithSuffix에 무한 재귀가 있습니다(SLING-11918).

### 알려진 문제 {#known-issues-14538}

없음.

### 임베드된 기술 {#embedded-tech-14538}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.58-T20231123092841-619e1bd | [Oak API 1.58.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.58.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
