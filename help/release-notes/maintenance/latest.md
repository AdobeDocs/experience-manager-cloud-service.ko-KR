---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: f0dc0e0ccd196ab748e2bfcdb4ce404c1c91c213
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 23%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 12441 {#release-12441}

2023년 6월 27일에 릴리스된 유지 관리 릴리스 12441의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 12255의 업데이트입니다.

2023.7.0 기능 활성화는 이 유지 관리 릴리스에 대한 전체 기능 세트를 제공합니다. 다음을 참조하십시오. [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) 추가 정보.

### 향상된 기능 {#enhancements-12441}

- SITES-8769: ResponsiveGrid에서 StyleImpl 호출 개선
- FORMS-5054: 모든 기능에 대한 지원을 추가했습니다. [조각상](https://opensource.adobe.com/acrobat-sign/acrobat_sign_events/webhookeventsagreements.html) Adobe Sign에서 지원합니다.

### 해결된 문제 {#fixed-issues-12441}

- 접근성 관련된 다양한 업데이트
- SITES-12688: 페이지 편집기: 논리 연산자 또는 에셋 파인더 검색에서 제대로 작동하지 않음
- SITES-4951: 페이지 편집기: 페이지 편집기의 태그 검색에서 하위 태그를 찾을 수 없음
- SITES-12465: 경험 조각: 경험 조각 구성 요소 대화 상자에서 화살표 키가 작동하지 않음
- SITES-12893: 경험 조각: 경험 조각에 대한 순환 참조 유효성 검사 적용
- SITES-12715: Experience Fragments: Experience Fragments 폴더에 적용된 클라우드 서비스 구성이 지속되지 않음
- SITES-13097: 경험 조각: 경험 조각을 번역 프로젝트에 추가할 수 없음
- SITES-13165: GraphQL: null 값 필터링을 위한 기본 동작 복원
- SITES-12577: 링크 검사기: 변환기가 링크를 간헐적으로 다시 쓰지 않음
- SITES-13559: MSM: 구성 요소를 롤아웃할 때 &quot;수정할 수 없음&quot; 예외가 발생합니다.
- SITES-11757: MSM: 상위에서 롤아웃 구성 상속이 하위 페이지에 대해 다시 반환되지 않음
- SITES-14073: 사이트 관리자: 내보낼 속성이 없음을 선택하면 CSV 보고서가 500으로 실패합니다
- FORMS-7648: 숫자 상자 구성 요소에서 최대 자릿수 필드 유효성 검사가 작동하지 않습니다.
- FORMS-8177: Forms 서비스가 활성 상태일 때 &#39;com.adobe.aem.formsndocuments.publish.AssetReferenceProvider에서 자산 종속성 검색 실패&#39; 오류가 발생합니다.
- FORMS-8300: 사용자가 작업을 연 후 위임하려고 하면 위임 응답이 사용자의 AEM 받은 편지함 UI를 여는 대신 작업을 다시 로드합니다.
- FORMS-8500: IE 모드 옵션이 활성화된 Microsoft® Edge 브라우저에서 HTML5 Forms이 열리지 않습니다.
- FORMS-8541: 적응형 Forms 렌더링 시 Null 포인터 예외가 발생합니다.
- FORMS-8964: Google Chrome 또는 Mozilla Firefox의 Android™ 장치에서 양식을 열 때 텍스트 상자 구성 요소에 입력된 텍스트를 제거할 수 없습니다.
- FORMS-9026: 사용자가 복잡하고 유효한 JSON 스키마를 기반으로 적응형 양식을 만들고 관련 JSON 스키마 필드를 적응형 Forms 편집기로 드래그하여 적응형 Forms 필드를 만들고 적응형 Forms 편집기 창을 새로 고치면 모든 필드가 삭제되고 적응형 Forms 편집기가 비어 있습니다.
- FORMS-9263: 확인란 옵션의 표시 텍스트에 특수 문자가 포함되어 있는 경우 사용자는 이러한 확인란을 선택할 수 없습니다.
- FORMS-8668: 양식의 PDF 미리 보기를 렌더링하는 동안 일부 필요하지 않은 Java™ 스택 덤프가 오류 로그에 표시됩니다. 그러나 양식을 렌더링하는 데에는 문제가 없습니다.
- FORMS-8116: 규칙이 적응형 Forms 컨테이너 구성 요소에 적용되면 적용된 규칙이 저장되지 않습니다.
- FORMS-7906: 적응형 양식이 AEM Sites 컨테이너 구성 요소에 추가되면 규칙 편집기를 열 수 없습니다.
- FORMS-8846: 바인딩 참조 속성이 적응형 Forms 첨부 구성 요소에 대해 작동하지 않습니다.
- FORMS-9072: 양식 조각을 만드는 동안 스키마를 검색할 때 검색 결과가 선택할 스키마를 반환하지 않습니다.
- FORMS: AEM Forms 기능의 접근성을 개선하기 위해 접근성 관련 버그가 여러 개 수정되었습니다.


### 알려진 문제 {#known-issues-12441}

없음.

### 임베드된 기술 {#embedded-tech-12441}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak API 1.50.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
