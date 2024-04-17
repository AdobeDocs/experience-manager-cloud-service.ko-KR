---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 5e216e45a1400299efcc418007ddbe93f0c571a1
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 30%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15939 {#release-15939}

다음은 2024년 4월 17일에 공개적으로 릴리스된 유지 보수 릴리스 15939에 대한 지속적인 개선 사항을 요약한 것입니다. 이전 유지 관리 릴리스는 릴리스 15860.

2024.4.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 참조하십시오.

### 개선 사항 {#enhancements-15939}

* GRANITE-39892: 대기열 크기 제한 및 게시 준비에 대한 배포를 업데이트합니다.
* GRANITE-48777: com.adobe.granite.security.user-0.4.84 done으로 QS 업데이트
* GRANITE-49421: 세그먼트 서비스 사용자에 대한 속성이 추가되었습니다.
* GRANITE-49855: 새로운 commons.json 사용의 경우 빠른 시작 빌드에 실패하는 기능 모델 분석기를 작성합니다.
* GRANITE-47995: cq:isDelivered의 쓰기를 전환할 수 있습니다.
* GRANITE-36205: 내부 oak 릴리스 버전을 최신 버전으로 업데이트합니다.
* GRANITE-50156 AEMCS 선호도를 범용 편집기의 IMS 사용자 ID에 바인딩합니다.
* GRANITE-50556: 횡단보도 번들을 v0.1.18로 업그레이드하십시오.
* GRANITE-50728: FileVault를 3.7.3-T20240308111857-81fa88f1로 업데이트합니다.
* GRANITE-50957: QS를 com.adobe.granite.repository에 1.8.114로 업데이트합니다.
* GRANITE-50158: YAML 로더의 서버 자격 증명 흐름에 OAuth 서버에 대한 지원을 추가합니다.
* GRANITE-51327: Oak를 최신 공개 릴리스(1.62.0)로 업데이트합니다.
* SKYOPS-68091 Java 11 런타임 이미지를 버전 3.0.0으로 업데이트합니다.
* SKYOPS-70421: org.apache.sling.servlet-helpers 번들 업그레이드
* SKYOPS-73483: AEM에서 토큰 로깅을 허용합니다.

### 해결된 문제 {#fixed-issues-15939}

* GRANITE-46901: 메시징 클라이언트에 지표를 추가합니다.
* GRANITE-48793: QS를 com.adobe.granite.crx-explorer-1.1.28로 업데이트합니다.
* GRANITE-48937: aem/start.html 페이지에서 Omnisearch가 작동하지 않습니다.
* GRANITE-49638: RUM 변환기 팩토리에 대한 잘못된 콘텐츠 유형 구성을 수정합니다.
* GRANITE-50141: IMSProviderImpl이 로그를 스팸 처리하고 있습니다.
* SITES-20949: Youtube에서 referrerpolicy=&quot;strict-origin-when-cross-origin&quot;을 추가한 후 ComponentsIT.testEmbed가 실패했습니다.
* SITES-21233: 핵심 구성 요소 업데이트 - GS1US로 업그레이드한 후 아코디언을 15860.
* SKYOPS-74819: Apache Commons의 중복 키에 대한 이전 버전과의 호환성이 끊어졌습니다.
* SKYOPS-67087: 특정 경우에 Clientlib 집계가 작동하지 않습니다.
* CQ-4355415: AEM 알림 링크가 6.5 SP18에서 작동하지 않습니다.

### 알려진 문제 {#known-issues-15939}

없음.

### 사용 중단된 기능 및 API {#deprecated-15939}

* [Adobe Developer Console에서 JWT 자격 증명 사용 중단](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

AEM as a Cloud Service에서 더 이상 사용되지 않거나 제거된 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 확인하십시오.

### 임베드된 기술 {#embedded-tech-15939}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.62.0 | [Oak API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.24.6 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
