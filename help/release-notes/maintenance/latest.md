---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 60952db4172b882b71a0b230fc8f4c27154e9cc0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 67%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15977 {#release-15977}

2024년 4월 19일에 릴리스된 유지 관리 릴리스 15977의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 15939이었습니다.

2024.4.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-15977}

* GRANITE-51335: AEM 상태 검사가 최적화되어 인스턴스 안정성이 향상되었습니다.

### 해결된 문제 {#fixed-issues-15977}

* CQ-4357226: OAuth 자격 증명에 대한 IMS 구성 지원의 회귀 문제가 해결되었습니다.
* GRANITE-51335: Ratelimit가 5.0.4로 업그레이드되어 Felix 상태 검사 등록이 수정되었습니다.

### 알려진 문제 {#known-issues-15977}

* **(AEM Forms만 해당)** AEM Cloud Foundation 유지 관리 릴리스 15977을 설치한 후 적응형 양식 필드가 양식을 작성하는 도중 및 게시된 양식에 대해 잘못된 순서로 렌더링됩니다. AEM FormsAdobe 를 사용하는 경우 향후 유지 관리 릴리스에서 문제가 해결될 때까지 15977 릴리스로 업그레이드하지 않는 것이 좋습니다. 그렇게 하면 불편함을 피하는 데 도움이 될 수 있습니다.

### 사용 중단된 기능 및 API {#deprecated-15977}

* [Adobe Developer Console에서 JWT 자격 증명 사용 중단](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

* 2024년 5월 1일부터 Dynamic Media Adobe은 다음 사항에 대한 지원을 종료합니다.

   * SSL(Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS(전송 계층 보안) 1.0 및 1.1
   * TLS 1.2의 약한 암호는 다음과 같습니다.
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`


AEMas a Cloud Service 에서 더 이상 사용되지 않거나 제거된 내용은 [사용이 중단되거나 제거된 기능 및 API](/help/release-notes/deprecated-removed-features.md).

### 임베드된 기술 {#embedded-tech-15977}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.62.0 | [Oak API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.24.6 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
