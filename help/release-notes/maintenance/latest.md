---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: f4b2ea5dac880738e6412541f06b85a6a83ccf40
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 79%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 16799 {#release-16799}

2024년 6월 18일에 릴리스된 유지 관리 릴리스 16799의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 16544이었습니다.

이 유지 관리 릴리스(2024.6.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-16799}

* ASSETS-31977: 자산 이동, 복사 및 삭제 작업이 개선되었습니다.
* ASSETS-33618: Dynamic Media의 비디오에 대한 자동 트랜스크립션 및 번역 기능입니다.
* ASSETS-35185: ContentHub 및 DM에 대한 승인 작업을 수행했으며 damAssetLucene 속성에 속성이 추가되었습니다.
* ASSETS-35533: damAssetLucene 색인에 DRM 및 CAI 속성이 추가되었습니다.
* ASSETS-37280: 소스 자막(vtt)이 아직 처리 중인 경우 번역을 위한 작업이 순차적으로 처리됩니다.
* ASSETS-37559: 자산 삭제 이벤트가 개선되었습니다.
* ASSETS-37723: 자산 게시 이벤트를 구현합니다.
* ASSETS-37724: 자산 게시 취소 이벤트를 구현합니다.
* ASSETS-38614: 공유 링크 UI가 향상되었습니다.
* ASSETS-39601: Asset Live Copy 이름에 정규 표현식 검사를 자동으로 적용합니다.
* ASSETS-39454: 빠른 시작의 뷰어가 2024.5.0으로 업그레이드되었습니다.
* CNTBF-184: 콘텐츠 백플로우에서 `/conf` 아래 경로가 지원됩니다.

### 해결된 문제 {#fixed-issues-16799}

* ASSETS-37335: 필터에서 검색 패널을 편집하면 모든 상자가 선택 취소됩니다.
* ASSETS-38069: 타임라인 필터 선택에 대한 AEM DAM PDF 미리보기 문제가 발생합니다.
* ASSETS-38215: 기업용 AEM as a Cloud Service 구독에서 Adobe Stock 라이선스 버튼이 회색으로 표시됩니다.
* ASSETS-38578: 자산 링크 공유 보고서의 하이퍼링크가 잘못되었습니다.
* ASSETS-38678: 컬렉션 세부 사항에서 보기 설정이 손상되었습니다.
* ASSETS-39071: 원본 변환 MIME 유형이 null인 경우 웹 최적화 게재에서 예외가 발생할 수 있습니다.
* ASSETS-39316: 컬렉션에서 이름별 정렬이 작동하지 않습니다.
* ASSETS-39377: 원격 API에서 배압을 수신하면 OneDrive에서 일괄 가져오기가 실패할 수 있습니다.
* ASSETS-39428: 저작권 관리 UI에 렌더링 문제가 발생합니다.
* CQ-4357150: cq-content-sync 번들의 Guava.
* GRANITE-52573: 이중 슬래시 `//`가 포함된 요청은 상태 코드 400으로 거부됩니다.
* SCRNS-4194: Google Guava API에 대한 종속성이 제거됩니다.
* SCRNS-4360: 채널용 콘텐츠 공급자에서 관리자가 아닌 사용자를 위한 게시 관리 및 빠른 게시 버튼이 누락됩니다.
* SCRNS-4323: screens.html에서 실행이 숨겨지거나 비활성화됩니다.
* FORMS-14844: 적응형 Forms은 reCAPTCHA 확인에 실패하더라도 양식을 제출할 수 있습니다.
* FORMS-14984: 제출된 데이터에 &quot;submitMetaData&quot;가 없는 경우 CAPTCHA가 있는 Forms에서 유효성 검사를 건너뜁니다.
* FORMS-14477: 날짜 선택기 확인에서 규칙 편집기의 &quot;다음 이후&quot; 및 &quot;다음 이전&quot; 옵션이 작동하지 않습니다.
* FORMS-14019: 규칙 편집기의 &quot;서비스 호출&quot; 기능이 유니버설 편집기에서 작동하지 않습니다.
* FORMS-14336: 양식 필드를 선택하지 않으면 편집기가 전체 양식 요소에 포커스를 두고 열려야 합니다.
* FORMS-15061: 로더 서클은 규칙 편집기에서 서비스 호출 옵션을 사용할 때 무기한 유지됩니다.

### 알려진 문제 {#known-issues-16799}

>[!NOTE]
> AEM Engineering이 16461부터 시작하는 현재 AEM 릴리스에 영향을 미치는 론치 기능에 대한 회귀를 식별했습니다. 이러한 회귀로 인해 딥 페이지가 아닌 페이지를 포함하는 새 론치(새 릴리스가 적용된 후 생성됨)는 누락된 구성으로 인해 제대로 승격되지 않습니다.
> 귀하의 환경이 영향을 받는 경우 누락된 구성을 식별하고 업데이트하는 셸 스크립트를 고객 지원 센터에서 제공합니다(내부 참조 SITES-22457).
> 새로운 론치가 올바른 구성으로 생성되도록 보장하는 장기적인 수정 사항이 제공될 예정입니다. 그때까지 요청 시 내부 패치 릴리스도 제공됩니다.

#### Forms

* AEM SDK를 설치하고 를 추가할 때 `AEM Forms add-on v2024.05.04.00-240400`, 도커 서비스를 시작할 수 없습니다. 로컬 개발 환경에서 기록 문서를 생성하려면 도커 서비스가 필요합니다. 문제를 해결하려면 다음을 수행하십시오.
   1. 다운로드 [핫픽스](/help/forms/assets/sdk_hotfix.zip). 핫픽스를 다운로드할 때 `.zip` 폴더가 다운로드되었습니다.
   1. 다운로드한 핫픽스를 폴더에 추출합니다.
   1. 이전 항목 바꾸기 `sdk.sh` 및 `sdk.bat` 2단계에서 추출한 폴더에 최신 파일이 있는 파일.

### 변경 사항 공지 {#change-notice-16799}

* 이 릴리스에는 다음과 같은 새로운 제품 인덱스 버전이 포함되어 있습니다.
   * **damAssetLucene-11**
   * **조각-11**

  이전 색인 버전의 사용자 정의 버전은 새 제품 색인 버전과 자동으로 병합됩니다. 병합된 버전에 추가 사용자 정의 업데이트를 적용하십시오.

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
