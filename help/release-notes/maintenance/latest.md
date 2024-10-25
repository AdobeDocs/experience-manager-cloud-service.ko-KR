---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9278ec9bb5bccd7b40cd65a120f296faba454b9c
workflow-type: ht
source-wordcount: '569'
ht-degree: 100%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 18311 {#18311}

2024년 10월 22일에 릴리스된 유지 관리 릴리스 18311의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이전 유지 관리 릴리스는 릴리스 18175였습니다.

이 유지 관리 릴리스(2024.10.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-18311}

* ASSETS-41820: 처리 감시를 위한 인덱싱 개선.
* ASSETS-43720: 처리 감시 기능 개선.
* ASSETS-42554: 대용량 폴더에 대한 성능 개선.
* SKYOPS-77603: 비즈니스 사용자의 리디렉션 관리.

### 해결된 문제 {#fixed-issues-18311}

* ASSETS-37534: 승인 대상에 사용되는 속성이 노출되지 않도록 검색 변경.
* ASSETS-38322: 게시 기준 공급자 구성 제거 및 게시 이벤트 기능 제거.
* ASSETS-40482: Scene7 비디오 플레이어의 재생/일시 정지 및 음소거/음소거 해제 버튼에 대한 접근성 문제.
* ASSETS-40593: 자산 > 파일에서 “속성” 버튼을 클릭하면 오류 페이지 발생.
* ASSETS-40598: 동기화되지 않은 자산을 동기화가 활성화된 폴더로 이동하는 경우 스마트 자르기 동기화.
* ASSETS-40743: 파일 이름에 특정 문자가 있는 경우 자산 바꾸기 대화 상자 트리거 시 문제.
* ASSETS-40825: 검색 양식을 편집한 후 자산 검색 패싯이 사라짐.
* ASSETS-41007: AEM에서 삭제하면 게재 시 때때로 고립된 자산이 남아 있음.
* ASSETS-41172: Dynamic Media 템플릿 이름에 특수 문자를 사용할 수 없음.
* ASSETS-41896: 폴더의 cq:discarded 속성에 언급된 자산은 Brand Portal에 게시되어서는 안 됨.
* ASSETS-42067: Dynamic Media 템플릿 - 다운로드 시 오류 발생.
* ASSETS-42070: Dynamic Media 템플릿 - 관리자가 아닌 사용자는 템플릿 생성/편집 액세스 권한이 있어야 함.
* ASSETS-42344: 연결된 자산 동기화 해제됨 - 다시 연결하고 고객에게 알리십시오.
* ASSETS-42620: 자산 버전의 미리보기 옵션 문제 - 자산을 열면 빈 미리보기가 표시됨.
* ASSETS-42701: 웹 최적화 이미지 게재 및 자르기 문제.
* ASSETS-42966: 여러 작업이 동일한 경로를 공유하는 경우 오류로 인해 비동기 바리케이드가 차단 해제될 수 있음.
* ASSETS-43072: Dynamic Media 템플릿 - 템플릿 참조 조회가 잘못된 참조로 인해 중단됨.
* ASSETS-43212: 메타데이터 스키마 편집기의 다국어화 문제.
* ASSETS-43202: 타임라인에서 인쇄할 주석 선택에 대한 수정 사항.
* ASSETS-43502: AEM CS 기존 이미지 사전 설정 이름이 편집 페이지에 표시되지 않음.
* ASSETS-43538: 비동기 복사 자산 작업이 소스 경로에 대해 잘못된 속성을 사용함.
* ASSETS-43798: 자산을 복사하기 전에 먼저 대상 경로를 확인하십시오.
* ASSETS-43945: 비동기 자산 작업 대기열의 재시도 지연 시간이 20분으로 늘어남.
* ASSETS-44025: 개별 자산을 선택하면 비동기 자산 삭제 작업이 실패함.
* SITES-26128: CreateLiveCopyStep에서 클래스 캐스트 예외 발생.
* SCRNS-4551: 비디오 구성 요소가 포함된 [SG Pools] Screens 채널이 브라우저 미리보기 및 플레이어에서 “일반 페이지 오류”를 표시함

### 알려진 문제 {#known-issues-18311}

* FORMS-15818: 구성 요소 설명자 항목 `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` 서버 로그에서 진술을 찾을 수 없음. 이는 해를 미치지 않는 로그 구문입니다.

### 사용 중단된 기능 및 API {#deprecated-18311}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-18311}

AEM as a Cloud Service는 플랫폼의 보안 및 성능을 최적화하는 데 사용됩니다. 이 유지 관리 릴리스에서는 강력한 시스템 보호에 대한 노력의 일환으로 식별된 취약점 3가지가 해결되었습니다.

### 임베드된 기술 {#embedded-tech-18311}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 2.27.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
