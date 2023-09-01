---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 288f871b75e68fdbca1244099e490408ea66ff40
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 40%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 13323 {#release-13323}

다음은 2023년 9월 1일에 공개적으로 릴리스된 유지 보수 릴리스 13323에 대한 지속적인 개선 사항을 요약합니다. 이 유지 관리 릴리스는 릴리스 정보를 13239.

이 유지 관리 릴리스(2023.9.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-13323}

- GRANITE-46784: BearerAuthenticationHandler를 비활성화하는 옵션을 추가합니다.
- GRANITE-36205: 내부 oak 릴리스 버전을 최신 버전으로 업데이트합니다.
- ASSETS-26713: 새로운 경험 UI 대시보드에 대한 Touch UI 외부 링크 - 통합 쉘 통합 및 ui-touch에 최적화된 업그레이드.
- SKYOPS-63302: com.adobe.granite:com.adobe.granite.auth.saml을 v1.0.54로 업그레이드합니다.
- GRANITE-46634: 이벤트 클라이언트 1.4.0으로 업그레이드합니다.
- GRANITE-46788: 라이브러리를 Apache Commons IO 2.13.0, Commons Lang 3.13.0, Commons 코드 1.16.0 및 Commons Compress 1.23.0으로 업데이트합니다.
- GRANITE-46705: Apache Felix Http Jetty 4.1.14로 업데이트합니다.
- GRANITE-46631: Jackrabbit 버전을 2.20.11로 업데이트합니다.
- SKYOPS-61895: Jackrabbit Filevault 3.7.0으로 업데이트합니다.

### 해결된 문제 {#fixed-issues-13323}

- ASSETS-28461: DocumentCloud 뷰어가 PDF에 대해 작동하지 않음에서 13239.
- SKYOP-63290: 버킷의 잘못된 발생을 수정했습니다.
- SKYOPS-54607: 실패한 요청에 대해 Ratelimiter 서버로드 계산이 올바르지 않습니다.
- ASSETS-27648: ContentModelIT가 다른 번들의 제외 파일을 읽지 못했습니다.
- GRANITE-43744: 인증 요구 사항 및 단축 경로에서 잘못된 구성이 있는 경우 Sling 인증자가 제대로 작동하지 않습니다.
- GRANITE-46419: Auth0 Idp에 AEM 통합 문제가 있습니다.
- GRANITE-46292: AEM Cloud 업데이트 후 Okta SAML 구성이 작동하지 않습니다.
- GRANITE-47059: Granite Jetty SSL 번들을 제거합니다.

### 알려진 문제 {#known-issues-13323}

- SITES-15622: GraphQL - 숫자 및 부울 매개 변수가 있는 지속 쿼리 문제.
- SITES-15654: GraphQL - 같은 이름의 결합 및 속성 관련 문제

### 임베드된 기술 {#embedded-tech-13323}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.54-T20230817132355-3800a65 | [Oak API 1.54.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
