---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: fd687498a8c72bf5d47b7b97aadf22d7d1e8dd2b
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 26%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16799 {#release-16799}

다음은 2024년 6월 18일에 공개적으로 릴리스된 유지 보수 릴리스 16799에 대한 지속적인 개선 사항을 요약했습니다. 이전 유지 관리 릴리스는 릴리스 16544.

이 유지 관리 릴리스(2024.6.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-16799}

* ASSETS-31977: 에셋 이동, 복사 및 삭제 작업이 개선되었습니다.
* ASSETS-33618: Dynamic Media의 비디오에 대한 자동 전사 및 번역 기능.
* ASSETS-35185: ContentHub 및 DM에 대한 승인 작업을 수행하고 damAssetLucene 속성에 속성을 추가합니다.
* ASSETS-35533: DRM 및 CAI 속성을 damAssetLucene 인덱스에 추가합니다.
* ASSETS-37280: 소스 자막(vtt)이 처리 중일 때 번역에 대한 순차적 작업 처리.
* ASSETS-37559: 에셋 삭제 이벤트가 개선되었습니다.
* ASSETS-37723: 에셋 게시 이벤트를 구현합니다.
* ASSETS-37724: 자산 게시 취소 이벤트를 구현합니다.
* ASSETS-38614: 링크 UI 공유 개선 사항.
* ASSETS-39601: 유효성 검사 정규 표현식을 자산 라이브 카피 이름에 자동으로 적용합니다.
* ASSETS-39454: Quickstart에서 viewer 2024.5.0으로 업그레이드합니다.
* CNTBF-184: 지원 경로 `/conf` 컨텐츠 백플로우에서.

### 해결된 문제 {#fixed-issues-16799}

* ASSETS-37335: 필터에서 검색 패널을 편집하면 모든 상자의 선택이 취소됩니다.
* ASSETS-38069: 타임라인 필터 선택 시 AEM DAM PDF 미리 보기 문제.
* ASSETS-38215: Adobe Stock AEM 라이선스 단추가 기업 가입을 위해 as a Cloud Service으로 회색으로 표시됩니다.
* ASSETS-38578: 에셋 링크 공유 보고서의 잘못된 하이퍼링크.
* ASSETS-38678: 컬렉션 세부 사항에서 끊어진 설정을 봅니다.
* ASSETS-39071: 원본 렌디션 mimetype이 null인 경우 웹에 최적화된 전달에서 예외가 발생할 수 있습니다.
* ASSETS-39316: 이름별 정렬이 컬렉션에서 작동하지 않습니다.
* ASSETS-39377: 원격 API에서 역압을 받으면 OneDrive에서 대량 가져오기가 실패할 수 있습니다.
* ASSETS-39428: 저작권 관리 UI의 렌더링 문제.
* CQ-4357150: cq-content-sync 번들의 구아바
* GRANITE-52573: 이중 슬래시가 포함된 요청 `//` 거부되었습니다(상태 코드 400).
* SCRNS-4194: Google Guava API에 대한 종속성을 제거합니다.
* SCRNS-4360: 채널 컨텐츠 공급자에 관리자가 아닌 사용자를 위한 게시 관리 및 빠른 게시 단추가 없습니다.
* SCRNS-4323: screens.html에서 론치를 숨기거나 비활성화합니다.

### 알려진 문제 {#known-issues-16799}

>[!NOTE]
> AEM Engineering에서는 Analytics로 시작하는 현재 AEM 릴리스에 영향을 주는 론치 기능에 대한 회귀 문제를 16461. 이러한 회귀 현상으로 인해, 딥이 아닌 페이지를 포함하는 새 론치(새 릴리스가 적용된 후 생성됨)는 누락된 구성으로 인해 제대로 홍보되지 않습니다.
> 환경이 영향을 받는 경우 고객 지원을 통해 누락된 구성을 식별하고 업데이트하는 셸 스크립트를 사용할 수 있습니다(내부 참조 SITES-22457).
> 올바른 구성으로 새 론치를 만들 수 있도록 하는 보다 장기적인 수정 사항이 제공됩니다. 그때까지 온디맨드로 내부 패치 릴리스도 이용할 수 있습니다.

#### Forms

1. 사용자가 보다 큰 AEM Forms SDK 버전을 다운로드하는 경우 `AEM Forms add-on v2024.05.04.00-240400`, 배치 파일이 Docker 서비스를 시작하지 못했습니다. 이 문제를 해결하려면 다음을 수행하십시오.
   1. 다운로드 [폴더](/help/forms/assets/sdk_hotfix.zip).
   1. 다운로드한 폴더에서 콘텐츠를 추출하고 `sdk.sh` 및 `sdk.bat` 파일.
   1. 기존 항목 바꾸기 `sdk.sh` 및 `sdk.bat` AEM Forms SDK에 있는 파일과 새 파일.

### 변경 사항 공지 {#change-notice-16799}

* 이 릴리스에는 다음과 같은 새 제품 색인 버전이 포함되어 있습니다.
   * **damAssetLucene-11**
   * **fragments-11**

  이전 색인 버전의 사용자 지정 버전은 새 제품 색인 버전과 자동으로 병합됩니다. 병합된 버전에 추가 사용자 정의 업데이트를 적용하십시오.

* 2024년 9월부터 AEM as a Cloud Service는 Sling Model Exporter 프레임워크를 통해 Resource Resolver의 직렬화를 비활성화합니다. 자세한 내용은 [설명서](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md)를 참조하십시오.

### 사용 중단된 기능 및 API {#deprecated-16799}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능을 살펴보려면 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

### 임베드된 기술 {#embedded-tech-16799}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING API | 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.25.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
