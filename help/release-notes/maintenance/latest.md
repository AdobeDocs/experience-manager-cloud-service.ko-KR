---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d16d908d39df3c7d72dc48ac877c1543d2442416
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 88%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15262 {#release-15262}

2024년 3월 6일에 릴리스된 유지 관리 릴리스 15262의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 14697이었습니다.

이 유지 관리 릴리스(2024.3.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-15262}

* ASSETS-30632: 목록 보기에서 별도의 Brand Portal 게시 상태 열이 추가되었습니다.
* ASSETS-30934: 자산 메타데이터 편집기에 `Iptc4xmpCore:AltTextAccessibility` 및 `Iptc4xmpCore:ExtDescrAccessibility` 속성에 대한 지원이 추가되었습니다.
* ASSETS-31297: 검사를 개선하여 Dynamic Media에서 복사된 자산 삭제를 방지합니다.
* ASSETS-33246: 인덱스 정의 `damAssetLucene-10`을 릴리스합니다.
* ASSETS-33590: 처리 프로필에서 비디오에 대한 webm 렌디션 지원을 추가합니다.
* GRANITE-36205: Oak 버전을 1.60-T20240131102219-0cde853으로 업데이트합니다.
* SITES-19326: Assets UI에서 링크를 업데이트하여 새 CF 편집기에서 CF를 엽니다.
* GUIDES-12945: AI 기반 스마트 제안을 통해 콘텐츠 참조를 추가하면서 콘텐츠를 작성합니다.
* GUIDES-12706: 웹 편집기에서 개선된 버전 기록 기능
* GUIDES-14948: 번역 패널에서 향상된 사용자 경험
* GUIDES-8782: 요소 삽입 대화 상자에서 향상된 검색 논리
* GUIDES-14681: 다이내믹 기준선을 사용하여 여러 출력 사전 설정을 게시할 수 있는 기능
* AEM Guides의 전체 개선 기능 목록은 [AEM Guides의 새로운 기능](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/whats-new-2024-2-0.html?lang=ko#release-info)을 참조하십시오.

### 해결된 문제 {#fixed-issues-15262}

* ASSETS-15977: 지원 중단된 v1 검색 이벤트와 파이프라인 제작자를 제거합니다.
* ASSETS-18088: Batik 라이브러리 종속성을 1.17로 업그레이드합니다.
* ASSETS-21965: 메타데이터 원본에 쓰기 워크플로는 자산 메타데이터 변경 시에만 실행해야 합니다.
* ASSETS-26368: 작업 구성이 존재하지 않는 경우 예약된 일괄 가져오기 작업이 제거되지 않습니다.
* ASSETS-26549: “jcr:lastModifiedBy”가 포함된 자산/노드: “workflow-process-service”는 목록 보기에서 “외부 사용자”로 표시됩니다.
* ASSETS-26842: “Firefly” 텍스트를 업데이트하여 처리 프로필에서 “App Builder”를 읽습니다.
* ASSETS-28708: 일부 IMS 토큰 요청에 대한 응답 시간이 매우 느려집니다.
* ASSETS-28767: 대용량 자산이 포함된 폴더가 없는 경우 자산의 게시 상태가 일관되지 않습니다. 게시된 자산.
* ASSETS-29011: 읽기 전용 사용자에게 스마트 자르기가 표시됩니다.
* ASSETS-29348: AssetMoveEventHandler에서 너무 많은 메모리를 사용할 수 있습니다.
* ASSETS-29738: woff 파일의 NullPointerException으로 인해 자산 업로드가 제한됩니다.
* ASSETS-30068: “작업이 완료되었지만 오류 있음”에 COMPLETED_WITH_ERROR 상태를 포함하도록 Asset Essentials를 일괄 가져옵니다.
* ASSETS-30261: 자산 이벤트의 잘못된 imsUserId가 파이프라인으로 전송됩니다.
* ASSETS-30538: PDF 파일 이동 후 페이지 보기 옵션이 누락됩니다.
* ASSETS-30626: 빈 assetId가 있는 자산에서 보고되는 게재 요청을 만들 수 없습니다.
* ASSETS-30756: 폴더 이름이 “html”로 끝나는 경우 자산 이동 마법사 작업을 수행할 수 없습니다.
* ASSETS-30810: 기존 YouTube 구성을 렌더링하기 전에 태그를 삭제합니다.
* ASSETS-31015: 파일 확장명이 .msg인 자산을 업로드할 수 없습니다.
* ASSETS-31038: 알림 서비스에서 수신한 작업 이벤트가 처리되고 있지 않습니다.
* ASSETS-31097: 순회 쿼리 경고가 발생하지 않도록 WCM 콘텐츠의 비동기 복사를 비활성화합니다.
* ASSETS-31256: “jcr:lastModifiedBy”가 포함된 자산/노드: “workflow-process-service”는 목록 보기에서 “외부 사용자”로 표시됩니다.
* ASSETS-31260: 드롭다운 JSON의 목록이 큰 경우 자산 메타데이터 양식 드롭다운 필드가 제대로 작동하지 않습니다.
* ASSETS-31280: 자산이 컬렉션에 추가되면 평면 구조에서 다운로드합니다.
* ASSETS-31301: `dynamicmedia_sly.js`는 Use API로 제대로 인스턴스화할 수 없습니다.
* ASSETS-31330: ko_KR: 현지화되지 않은 문자열이 자막 및 오디오 트랙에 있습니다.
* ASSETS-31405: 대규모 InDesign 레이아웃의 경우 InDesign Server 처리가 실패합니다.
* ASSETS-31570: 통합 셸 - 자산 세부 정보 “저장 및 닫기”, “취소” 버튼은 두 번 이상 눌러야 작동합니다.
* ASSETS-31673: 대용량 Dropbox 파일의 경우 일괄적으로 가져올 수 없습니다.
* ASSETS-32108: 보기 설정에서 AEM Assets는 사용자 정의 카드 크기를 저장하지 않음.
* ASSETS-32230: com.adobe.aem.repoapi bundle 번들의 최소 런타임 버전을 업그레이드합니다.
* ASSETS-32544: 메타데이터 내보내기 작업이 간헐적으로 실패합니다.
* ASSETS-32679: 자산(PDF) 미리보기에 캐싱 문제가 발생합니다.
* ASSETS-32754: 사용자가 이전에 로그인하지 않았다면 작업을 할당할 수 없습니다.
* ASSETS-32755: com/adobe/cq/dam/assetmove 작업 항목을 구성하여 순서가 지정된 대기열을 사용합니다.
* ASSETS-32899: 컬렉션 내 검색이 매우 느립니다.
* ASSETS-33098: AEM Assets 검색 패싯 “태그 설명”이 예상대로 작동하지 않습니다.
* ASSETS-33454: 타임라인에 표시되지 않는 작업 활동과 댓글을 검토합니다.
* ASSETS-34088: AEM Assets에서 PDF 미리보기가 작동하지 않습니다.
* ASSETS-34155: Dynamic Media - AEM 뷰어/2024.1.0이 업데이트되었습니다.
* ASSETS-34684: 콘텐츠 트리의 복수 값 dc:title을 처리합니다.
* ASSETS-34789: 파일 이름 충돌 검사를 통해 표준화 문제를 수정합니다.
* DXML-13276: AEM Guides - GraniteContent에서 인덱스를 통합하고 라이브러리에서 제거합니다.
* GRANITE-47995: “cq:isDelivered” 속성과의 충돌로 인해 삭제 작업이 실패할 수 있습니다.
* GRANITE-48079: OAuth 온라인 토큰 유효성 검사에 대한 POST 요청을 활성화합니다.
* GRANITE-48143: org.apache.sling.resourcemerger를 1.4.4로 업그레이드합니다.
* GRANITE-49031: Jackson 2.16.1로 업데이트합니다.
* SCRNS-3961: Screens - 시퀀스 채널: 페이드 전환에 사용되는 Jquery 애니메이션이 검은색 화면으로 연결됩니다.
* SITES-15868: 조각을 나열하는 성능을 개선합니다.
* SITES-16079: `/fragments/{id}/references`가 중복 요소를 반환하기 시작했습니다.
* SITES-16118: 조각이 패치되고 조각 필드가 모델에서 누락된 경우, 예외가 발생합니다.
* SITES-16121: 모델 날짜 필드를 검색하면 예외가 발생합니다.
* SITES-16207: POST /adobe/sites/cf/models 작업이 두 개의 서로 다른 확인 상태 코드를 반환합니다.
* SITES-17361: Sites-Headless 번들에 Jsoup을 다시 임베드합니다.
* SITES-17768: GraphQL은 콘텐츠 조각에서 참조되는 자산의 Dynamic Media URL을 출력합니다.
* SKYOPS-66622: buildTransform 지원 파이프라인을 실행하면 작성자 배포 충돌 루프가 발생합니다.
* SKYOPS-69977: 최신 업데이트 이후 적응형 이미지 서블릿이 이미지를 로드하지 않습니다.
* GUIDES-15045: 편집기의 맞춤법 검사를 사용하면 제안 사항을 선택할 수 없습니다.
* GUIDES-14968: 전역 탐색 버튼이 작동되지 않고 대시보드가 &#x200B;&#x200B;로드되지 않습니다.
* GUIDES-14943: 기본 PDF 게시의 조건 사전 설정 내 사용자 정의 속성이 기본 PDF 게시 시 작동하지 않습니다.
* GUIDES-15085: 기본 PDF 게시에서 Adobe Experience Manager Guides의 2023년 12월 릴리스에 대한 주요 참조가 해결되지 않습니다.
* GUIDES-13486: **기준선 필터** 파일이 웹 편집기의 파일 이름에서 작동하지 않습니다.
* AEM Guides에서 수정된 문제의 전체 목록은 [AEM Guides에서 수정된 문제](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/fixed-issues-2024-2-0.html?lang=ko#release-info)를 참조하십시오.

### 알려진 문제 {#known-issues-15262}

* 자산-35923: `UnsupportedClassVersionError` 업그레이드 후 CM 파이프라인 빌드 단계에서 `aem-sdk-api` 버전 `2024.2.15262.20240224T002940Z-231200`. **CM Java 버전을 11로 설정하려면 고객 작업이 필요합니다.**, 참조 [빌드 환경 / Maven JDK 버전 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)
* ASSETS-35860: AEM Assets 열 보기에서 시간대 변환이 잘못되었습니다.
* SCRNS-4171: Windows Screens로 업그레이드하고 채널을 게시할 때 Windows Screens15262 비어 있고 작동이 중지됩니다.
* GRANITE-50774: GraniteContent는 초기화 시 속성 값의 결정론적 순서를 사용해야 합니다.

### 변경 사항 공지 {#change-notice-15262}

**필요한 작업**

#### CM Java 버전을 11로 설정 {#set-java-version-11}

새 버전의 aem-sdk-api에는 Cloud Manager 빌드 환경 기본 JDK 버전 1.8과 호환되지 않는 Java 11 타겟으로 컴파일된 클래스가 포함되어 있습니다. 이 업데이트를 사용하려면 Maven이 JDK 11을 사용하여 실행되어야 합니다.

고객에게 다음을 추가하는 것이 좋습니다. `.cloudmanager/java-version` 다음 내용이 포함된 git 저장소의 루트에 파일을 추가합니다. `11`. [빌드 환경 / Maven JDK 버전 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)

#### Aem-cloud-testing-clients를 1.2.1로 업데이트 {#update-aem-cloud-testing-clients}

향후 변경 사항을 적용하려면 사용자 정의 기능 테스트에 사용되는 [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) 라이브러리를 최소 버전 **1.2.1로 업데이트해야 합니다.**

`it.tests/pom.xml`의 종속성이 업데이트되었는지 확인합니다.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

이 변경 사항은 2024년 4월 6일 이후에 필요합니다.

종속성 라이브러리를 업데이트할 수 없으면 “사용자 정의 기능 테스트” 단계에서 파이프라인 오류가 발생합니다.

### 임베드된 기술 {#embedded-tech-15262}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
