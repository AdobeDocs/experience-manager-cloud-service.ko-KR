---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 6e491a68dedc55609349db75ac13691aeda2f0dc
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 20%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 13099 {#release-13099}

다음은 2023년 8월 15일에 공개적으로 릴리스된 유지 보수 릴리스 13099에 대한 지속적인 개선 사항을 요약합니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 12874의 업데이트입니다.

이 유지 관리 릴리스(2023.8.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-13099}

- SITES-13906: GraphQL - graphql-java 20.1로 업그레이드
- SITES-8972: GraphQL - 열거형 데이터 유형에 JSON에 옵션 레이블을 추가합니다.
- SITES-9689: GraphQL - 컨텐츠 참조 데이터 유형을 위해 JSON에 제목 및 설명을 추가합니다.
- SITES-13052: 컨텐츠 조각 - 컨텐츠 조각을 Adobe Target으로 내보냅니다.

### 해결된 문제 {#fixed-issues-13099}

- SITES-14937: MSM - 라이브 카피에서 저장 및 닫기 누르기 시 상위 값에서 롤아웃 구성 상속 이 전환됩니다.
- SITES-14847: 콘텐츠 조각 - 콘텐츠 조각 링크가 강조 표시되지 않습니다.
- SITES-11620: 콘텐츠 조각 - 참조 경로가 UI에서 약간 잘립니다.
- SITES-14171: GraphQL - 경우에 따라 캐시된 데이터에 대한 순환 참조가 중단되지 않습니다.
- SITES-14577: 경험 조각 - 벌크 게시가 라이브 카피에 대해 작동하지 않습니다.
- SITES-14341: 관리자 UI - 삭제 권한이 제거될 때 &#39;속성&#39; 버튼의 일관되지 않은 동작.
- SITES-11000: 관리자 UI - 참조: 일부 페이지에 들어오는 링크가 없습니다.
- SITES-11559: 관리자 UI - 참조: 수신 링크에 잘못된 페이지가 표시됨.
- SITES-14337: 관리자 UI - 편집기 페이지를 열면 특정 경우에 오류가 발생합니다.
- SITES-13425: ContextHub - ContextHub 버튼을 클릭할 때 메뉴 모음이 표시되지 않습니다.
- FORMS-9971: 적응형 양식이 다른 로케일에서 렌더링되면 구성 요소의 가시성이 잘못 해석되고 적용됩니다.
- FORMS-9888: 적응형 양식이 양식 제출 시 외부 URL(감사 페이지)로 리디렉션되도록 설정되면 외부 URL로 리디렉션되지 않습니다.
- FORMS-9845: 규칙 편집기를 사용하여 드롭다운을 지운 후 이전에 제공된 값이 해당 정리에도 불구하고 유지됩니다.
- FORMS-9263: 확인란의 레이블에 특수 문자가 포함되어 있고 사용자가 확인란을 클릭하면 각 확인란이 선택되지 않습니다.
- FORMS-9254: 사용자가 약관 구성 요소의 텍스트를 스크롤할 때 전체 텍스트를 스크롤하기 전에도 구성 요소 내의 확인란이 자동으로 활성화됩니다.
- FORMS-9045: 스크립트 태그가 기본 XDP에서 외부 조각 참조를 확인하지 않습니다.
- FORMS-9026: 빈 문자열이 있는 열거형이 있고 오류 없이 유효성을 검사하는 JSON 스키마를 사용하여 적응형 양식을 만들려고 하면 프로세스가 실패로 끝납니다. 그런 다음 페이지를 새로 고치면 양식이 제대로 로드되지 않고 로그에 오류와 함께 빈 양식이 표시됩니다.
- FORMS-8964: Android™ Chrome/Firefox에서 최대 문자 제한에 도달하면 텍스트 상자 구성 요소에서 텍스트를 편집할 수 없게 됩니다.
- FORMS-8668: 기능 양식 렌더링에도 불구하고 오류 로그에 과도한 Java™ 스택이 덤프되어 로그 파일이 흐려집니다.
- FORMS-8554: 소극적 로드가 활성화된 적응형 Forms이 작성자 인스턴스의 미리보기 모드에서 작동하지 않습니다.
- FORMS-8177: 양식 서비스가 활성 상태일 때 예외 &quot;com.adobe.aem.formsndocuments.publish.AssetReferenceProvider가 자산 종속성을 검색하지 못했습니다.&quot; 발생합니다. 양식 서비스를 비활성화하면 오류가 사라집니다.
- FORMS-3691: 일부 오브젝트에 IFE(함수 표현식을 즉시 호출함) 범위가 없습니다. IIFE를 사용하는 기본 목적은 함수 내에 변수에 대한 범위를 만들어 해당 변수가 전역 범위를 오염시키지 않도록 하는 것입니다.


### 알려진 문제 {#known-issues-13099}

- SITES-15359: 콘텐츠 조각 - 변형 이름 패턴이 이 있는 변형과 올바르게 일치하지 않음 ```'_'``` 리소스 이름.
- SITES-15463: 사이트 템플릿 - 템플릿을 게시할 수 없습니다(해결 방법: 배포 콘솔 사용).
- FORMS-10444: 적응형 Forms 템플릿 - 템플릿을 게시할 수 없습니다(해결 방법: 배포 콘솔 사용).
- CQ-4354191: 워크플로 - nt:unstructured 노드에 있는 복제 메타데이터로 인해 사용자 지정 런처가 여러 번 트리거될 수 있습니다(해결 방법: 겹치지 않도록 복제 메타데이터 속성을 제외하도록 런처를 업데이트).

### 임베드된 기술 {#embedded-tech-13099}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
