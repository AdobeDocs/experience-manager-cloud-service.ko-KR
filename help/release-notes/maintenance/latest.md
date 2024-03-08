---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 87f76de41074debb2acc8ef4f71baf174d0d01ad
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 9%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 15262 {#release-15262}

다음은 2024년 3월 6일에 공개적으로 릴리스된 유지 보수 릴리스 15262에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 14697.

2024.3.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-15262}

* ASSETS-30632: 목록 보기에 별도의 Brand Portal 게시 상태 열이 추가되었습니다.
* ASSETS-30934: 다음에 대한 지원을 추가했습니다. `Iptc4xmpCore:AltTextAccessibility` 및 `Iptc4xmpCore:ExtDescrAccessibility` 속성을 자산 메타데이터 편집기에 추가합니다.
* ASSETS-31297: Dynamic Media에서 복사한 에셋이 삭제되지 않도록 검사를 개선합니다.
* ASSETS-33246: 릴리스 색인 정의 `damAssetLucene-10`.
* ASSETS-33590: 처리 프로필에서 비디오에 대한 webm 렌디션 지원을 추가합니다.
* GRANITE-36205: oak 버전을 1.60-T20240131102219-0cde853으로 업데이트합니다.
* SITES-19326: 에셋 UI의 링크를 업데이트하여 새 CF 편집기에서 CF를 엽니다.
* GUIDES-12945: 콘텐츠를 작성하는 동안 콘텐츠 참조를 추가하는 AI 기반 스마트 제안
* GUIDES-12706: 웹 편집기의 버전 내역 기능 개선
* GUIDES-14948: 번역 패널의 향상된 사용자 경험
* GUIDES-8782: 요소 삽입 대화 상자에서 검색 논리가 개선되었습니다
* GUIDES-14681: 동적 기준선을 사용하여 여러 출력 사전 설정을 게시하는 기능
* AEM Guides의 전체 개선 사항 목록은 을 참조하십시오. [AEM Guides의 새로운 기능](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/whats-new-2024-2-0.html?lang=en#release-info)

### 해결된 문제 {#fixed-issues-15262}

* ASSETS-15977: 더 이상 사용되지 않는 v1 검색 이벤트 및 파이프라인 생성자를 제거합니다.
* ASSETS-18088: 기본 라이브러리 종속성을 1.17로 업그레이드합니다.
* ASSETS-21965: 메타데이터 원본에 쓰기 워크플로우는 자산 메타데이터 변경 시에만 실행해야 합니다.
* ASSETS-26368: 작업 구성이 없는 경우 예약된 일괄 가져오기 작업이 제거되지 않습니다.
* ASSETS-26549: &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot;가 있는 자산/노드는 목록 보기에서 &quot;외부 사용자&quot;로 표시됩니다.
* ASSETS-26842: 처리 프로필에서 &quot;Firefly&quot; 텍스트를 업데이트하여 &quot;App Builder&quot;를 읽습니다.
* ASSETS-28708: 일부 IMS 토큰 요청에 대해 매우 느리게 응답합니다.
* ASSETS-28767: 큰 숫자가 들어 있는 폴더의 경우 에셋의 게시 상태가 일치하지 않습니다. 게시된 에셋 중
* ASSETS-29011: 스마트 자르기는 읽기 전용 사용자에게 표시됩니다.
* ASSETS-29348: AssetMoveEventHandler가 너무 많은 메모리를 사용할 수 있습니다.
* ASSETS-29738: woff 파일에 대한 NullPointerException으로 인해 자산 업로드 제한에 실패합니다.
* ASSETS-30068: &quot;작업이 완료되었지만 오류가 있음&quot;에 대해 COMPLETED_WITH_ERROR 상태를 포함하도록 Asset Essentials를 대량으로 가져옵니다.
* ASSETS-30261: 자산 이벤트에 대해 파이프라인으로 전송된 잘못된 imsUserId입니다.
* ASSETS-30538: PDF 파일을 이동한 후 페이지 보기 옵션이 누락되었습니다.
* ASSETS-30626: 빈 assetId가 있는 자산에 대해 보고된 게재 요청을 만들지 못했습니다.
* ASSETS-30756: 폴더 이름이 &#39;html&#39;로 끝나면 자산 이동 마법사 작업이 실패합니다.
* ASSETS-30810: 기존 youtube 구성을 렌더링하기 전에 태그를 정리합니다.
* ASSETS-31015: .msg 파일 이름 확장명의 자산을 업로드할 수 없습니다.
* ASSETS-31038: 알림 서비스에 의해 수신된 작업 이벤트가 처리되지 않습니다.
* ASSETS-31097: WCM 콘텐츠에 대해 비동기 복사를 비활성화하여 통과 쿼리 경고를 방지합니다.
* ASSETS-31256: &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot;가 있는 자산/노드는 목록 보기에서 &quot;외부 사용자&quot;로 표시됩니다.
* ASSETS-31260: 드롭다운 JSON에 큰 목록이 있는 경우 에셋 메타데이터 양식 드롭다운 필드가 제대로 작동하지 않습니다.
* ASSETS-31280: 컬렉션에 추가할 때 자산이 평면화된 구조로 다운로드되도록 합니다.
* 자산-31301: `dynamicmedia_sly.js` use API로 올바르게 인스턴스화할 수 없습니다.
* ASSETS-31330: ko_KR: 자막 및 오디오 트랙에 지역화되지 않은 문자열.
* ASSETS-31405: 대형 InDesign 레이아웃에 대해 InDesign 서버 처리에 실패합니다.
* ASSETS-31570: 통합 쉘 - 자산 세부 사항 &quot;저장 및 닫기&quot;, &quot;취소&quot; 단추를 두 번 이상 눌러야 작동합니다.
* ASSETS-31673: 대용량 Dropbox 파일에 대한 대량 가져오기에 실패했습니다.
* ASSETS-32108: AEM Assets이 보기 설정에서 사용자 정의 카드 크기를 저장하지 않습니다.
* ASSETS-32230: com.adobe.aem.repoapi 번들의 최소 런타임 버전을 업그레이드합니다.
* ASSETS-32544: 메타데이터 내보내기 작업이 간헐적으로 실패합니다.
* ASSETS-32679: 에셋(PDF) 미리보기 관련 캐싱 문제
* ASSETS-32754: 이전에 로그인하지 않은 사용자에게 작업을 할당할 수 없습니다.
* ASSETS-32755: 순서가 지정된 큐를 사용하도록 com/adobe/cq/dam/assetmove 작업 주제를 구성합니다.
* ASSETS-32899: 컬렉션 내부 검색이 매우 느립니다.
* ASSETS-33098: AEM Assets 검색 패싯 &quot;태그 조건자&quot;가 예상대로 작동하지 않습니다.
* ASSETS-33454: 작업 활동 및 타임라인에 표시되지 않는 주석을 검토합니다.
* ASSETS-34088: AEM Assets에서 PDF 미리 보기가 작동하지 않습니다.
* ASSETS-34155: Dynamic Media - 업데이트된 AEM Viewer / 2024.1.0.
* ASSETS-34684: 컨텐츠 트리에서 multivalue dc:title을 처리합니다.
* ASSETS-34789: 파일 이름 충돌 검사에서 표준화 문제를 수정합니다.
* DXML-13276: AEM Guides - GraniteContent에서 색인을 통합하고 라이브러리에서 제거합니다.
* GRANITE-47995: &quot;cq:isDelivered&quot; 속성과의 충돌로 인해 삭제 작업이 실패할 수 있습니다.
* GRANITE-48079: OAuth 온라인 토큰 유효성 검사에 대한 POST 요청을 활성화합니다.
* GRANITE-48143: org.apache.sling.resourcemerger를 1.4.4로 업그레이드 .
* GRANITE-49031: Jackson 2.16.1로 업데이트합니다.
* SCRNS-3961: Screens - 시퀀스 채널: 페이드 전환에 사용되는 Jquery 애니메이션은 검정색 화면으로 연결됩니다.
* SITES-15868: 조각 목록 성능을 개선합니다.
* SITES-16079 `/fragments/{id}/references` 중복을 반환하기 시작했습니다.
* SITES-16118: 조각이 패치되고 조각 필드가 모델에서 누락된 경우 예외가 발생합니다.
* SITES-16121: 모델 날짜 필드를 검색하면 예외가 발생합니다.
* SITES-16207: /adobe/sites/cf/models POST 작업은 두 개의 다른 확인 상태 코드를 반환합니다.
* SITES-17361: sites-headless 번들에 Jsup를 다시 임베드합니다.
* SITES-17768: GraphQL을 사용하여 콘텐츠 조각에서 참조된 에셋에 대한 Dynamic Media URL을 출력합니다.
* SKYOPS-66622: buildTransform이 활성화된 파이프라인을 실행한 후 작성자 배포 충돌이 반복됩니다.
* SKYOPS-69977: 적응형 이미지 서블릿이 최신 업데이트 후 이미지를 로드하지 않습니다.
* GUIDES-15045: 편집기의 맞춤법 검사에서는 제안 사항을 선택할 수 없습니다.
* GUIDES-14968: 전역 탐색 버튼이 작동하지 않고 대시보드가 로드되지 않습니다.
* GUIDES-14943: 기본 PDF 게시에서 조건 사전 설정 내의 사용자 지정 특성이 기본 PDF 게시에서 작동하지 않습니다.
* GUIDES-15085: 기본 PDF 게시에서 Adobe Experience Manager Guides의 2023년 12월 릴리스에 대한 주요 참조가 확인되지 않습니다.
* GUIDES-13486: **기준선 필터** 웹 편집기에서 파일이 파일 이름으로 작동하지 않습니다.
* AEM Guides에서 수정된 전체 문제 목록은 을 참조하십시오. [AEM Guides 해결 문제](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/fixed-issues-2024-2-0.html?lang=en#release-info)

### 알려진 문제 {#known-issues-15262}

#### `UnsupportedClassVersionError` 업그레이드 후 CM 파이프라인 빌드 단계에서 `aem-sdk-api` 버전 `2024.2.15262.20240224T002940Z-231200`

새 버전의 aem-sdk-api에는 Cloud Manager 빌드 환경 기본 JDK 버전 1.8과 호환되지 않는 Java 11 타겟으로 컴파일된 클래스가 포함되어 있습니다. 이 업데이트를 사용하려면 Maven이 JDK 11을 사용하여 실행되어야 합니다.

고객에게 다음을 추가하는 것이 좋습니다. `.cloudmanager/java-version` 다음 내용이 포함된 git 저장소의 루트에 파일을 추가합니다. `11`. [빌드 환경 / Maven JDK 버전 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/build-environment-details.html?lang=en#alternate-maven-jdk-version)

### 변경 공지 {#change-notice-15262}

**필요한 작업**

예정된 변경 내용을 적용하려면 라이브러리가 필요합니다. [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) 최소 버전 이상으로 업데이트하기 위해 사용자 정의 기능 테스트에 사용됨 **1.2.1**

다음에서 종속성을 확인하십시오. `it.tests/pom.xml` 이(가) 업데이트되었습니다.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

이 변경 사항은 2024년 4월 6일 이후에 필요합니다.

종속성 라이브러리를 업데이트하지 않으면 &quot;사용자 정의 기능 테스트&quot; 단계에서 파이프라인 오류가 발생합니다.

### 임베드된 기술 {#embedded-tech-15262}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
