---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 3be366e5fa0a7625203a052426be6a2fd2412cf6
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 98%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16145 {#release-16145}

2024년 5월 1일에 릴리스된 유지 관리 릴리스 16145의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 15977이었습니다.

2024.5.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-16145}

* ASSETS-23489: 저장소 인사이트가 개선되었습니다.
* ASSETS-26926: Dynamic Media 업로드 폴링이 개선되었습니다.
* ASSETS-30351: 다운로드 대화 상자는 Dynamic Media 변환 크기가 비동기식으로 로드됩니다.
* ASSETS-30379: 다운로드 시 DRM 라이선스 해상도가 개선되었습니다.
* ASSETS-31058: 변환 탭의 AEM 자산 UI에 Surface 스마트 자르기 렌디션을 표시하고 사용자가 이러한 렌디션을 클릭하면 스마트 자르기 이미지를 생성합니다.
* ASSETS-31218: 자산 게재 API에 명명된 smartcrop에 대한 지원이 추가됩니다.
* ASSETS-31979: 비동기 자산 작업 중에 시각적 표시기를 추가하고 UI 기능을 비활성화합니다.
* ASSETS-32735: 자산 메타데이터 업데이트 이벤트가 개선되었습니다.
* ASSETS-34661: DM 미리보기 및/또는 AEMaaCS 게시의 게재 URL에 대한 API.
* ASSETS-37259: XMP 구문 분석이 개선되었습니다.
* ASSETS-37263: 실패한 자산 비동기 작업 취소를 허용합니다.
* CNTBF-114: 콘텐츠 백플로우가 개선되었습니다.
* CNTBF-148: 콘텐츠 백플로우가 개선되었습니다.
* CQ-4356992: 최신 AEM 및 Granite 번역.
* SITES-19326: Assets UI에서 링크를 업데이트하여 새 CF 편집기에서 CF를 엽니다.
* SITES-20686: GraphQL - _dmS7Url을 통해 Dynamic Media URL이 표시됩니다(이미지가 아닌 자산의 경우).
* SKYOPS-68091: Java 11.0.20으로 업데이트됩니다.

### 해결된 문제 {#fixed-issues-16145}

* ASSETS-32321: 상위 폴더에 &#39;jcr:content&#39; 하위 노드가 누락된 경우 사후 처리 워크플로 해결이 실패합니다.
* ASSETS-33856: JPEG 이미지 사전 설정이 파일을 TXT로 다운로드합니다.
* ASSETS-34096: 비동기 다운로드 보고서에 대한 터치 UI 보기가 수정되었습니다.
* ASSETS-34493: 다중 회사 기능 토글을 활성화한 후 다운로드 대화 상자를 로드하는 동안 오류가 발생합니다.
* ASSETS-34824: DM 비활성화 폴더에 대한 복사 URL이 비어 있는 것으로 표시됩니다.
* ASSETS-35226: DAM 루트에 지정된 경우 사후 처리 워크플로가 확인되지 않습니다.
* ASSETS-35559: DM 일괄 업로드 실패 로그를 WARN으로 감소시킵니다.
* ASSETS-35860: AEM Assets 열 보기에서 시간대 전환이 잘못되었습니다.
* ASSETS-35935: 페이로드 검토를 닫은 후 폴더 탐색이 잘못되었습니다.
* ASSETS-35961: 자르기 추가 버튼이 이미지 프로필에서 작동하지 않습니다.
* ASSETS-36227: 게시 시 FolderPreviewUpdaterImpl 서비스가 비활성화됩니다.
* ASSETS-36943: CF 및 기타 비 CF 항목이 목록 보기의 폴더에 있는 경우 정렬 열이 누락됩니다.
* ASSETS-36990: 많은 수의 속성으로 인해 내보낸 메타데이터 작업이 실패하거나 느려집니다.
* ASSETS-37113: 쿼리가 CF 결과만 반환하는 경우 자산 재처리 작업이 즉시 종료됩니다.
* ASSETS-37260: AEM의 메타데이터 내보내기 작업이 잘못된 CSV를 생성할 수 있습니다.
* ASSETS-37261: AEM Assets에서 PPTx 및 PDF 주석에 대해 문제가 발생합니다.
* ASSETS-37282: 큰 폴더를 여는 요청에 시간이 오래 소요될 수 있습니다.
* ASSETS-37330: OneDrive에서 일괄 가져오기 작업을 수행하면 잘못된 AEM 폴더 구조가 생성됩니다.
* ASSETS-37609: 레거시 scene7 conf 조회를 제거합니다.
* ASSETS-38016: 일부 메타데이터 업데이트가 이벤트에서 제대로 추적되지 않습니다.
* CQ-4357161: AEM 받은 편지함 페이로드 화면이 404를 반환합니다.
* GRANITE-50041: 드롭다운 옵션에 “변환 추가” 옵션만 있는 경우 해상도가 1440px 폭을 초과하면 변환 추가가 작동하지 않습니다.
* GRANITE-50279: Coral Datepicker 구성 요소의 주 이름이 잘못되었습니다.
* SCRNS-3949: 화면 채널 가져오기 요청 시간이 너무 깁니다.
* SCRNS-3981: [시퀀스 채널] 요소 로드/언로드 이벤트 시퀀스가 &#x200B;&#x200B;왜곡되면 검은색 화면이 표시됩니다.
* SCRNS-4180: [시퀀스 채널] 대체 썸네일에서 복구 시 지속 시간이 -1인 비디오가 있는 채널에 대해 빈 화면이 표시되면서 시퀀스가 &#x200B;&#x200B;중지됩니다.
* SCRNS-4245: [시퀀스 채널] 비디오가 로드되고 대체 썸네일에서 전환될 때 빈 화면의 지속 시간이 제한됩니다.
* SITES-16055: 각 속성 페이지 내에서 Live Copy 및 Live Copy 소스 링크가 수정되었습니다.
* SCRNS-4243: 관리자가 아닌 사용자를 위한 콘텐츠 공급자에 버튼이 누락되었습니다.

### 알려진 문제 {#known-issues-16145}

없음.

### 사용 중단된 기능 및 API {#deprecated-16145}

* [Adobe Developer Console에서 JWT 자격 증명 사용 중단](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

* 2024년 5월 1일부터 Adobe Dynamic Media는 다음에 대한 지원을 종료합니다.

   * SSL(보안 소켓 계층) 2.0
   * SSL 3.0
   * TLS(전송 계층 보안) 1.0 및 1.1
   * TLS 1.2의 다음과 같은 약한 암호:
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


AEM as a Cloud Service에서 더 이상 사용되지 않는 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

### 임베드된 기술 {#embedded-tech-16145}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.62.0 | [Oak API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.24.6 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
