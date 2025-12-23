---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c5cdcccdb3ac16c5088e46e3f64e8cfc4139e0e4
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 16%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 현재 유지 관리 릴리스에 대한 기술 릴리스 정보를 간략히 소개합니다.

## 릴리스 23862 {#23862}

다음은 2025년 12월 23일에 공개적으로 릴리스된 유지 보수 릴리스 23862에 대한 지속적인 개선 사항을 요약한 것입니다. 이전 유지 관리 릴리스는 릴리스 23482.

이 유지 관리 릴리스에 대한 2026.1.0 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 참조하십시오.

### 개선 사항 {#enhancements-23862}

* CQ-4361812: rest api에 선택적 매개 변수 folderPath에 대한 지원이 추가되었습니다. 설명: 새 번역 프로젝트는 API에 의해 만들어지고 선택적 `folderPath` 매개 변수에 의해 지정된 경로 내에 배치됩니다. 그렇지 않으면 기본값은 루트 프로젝트 경로 `/content/projects`입니다.
* FORMS-21960: forms-spa와 유사하게 대화형 커뮤니케이션용 로컬에서 캔버스 편집에 대한 지원이 추가되었습니다.
* FORMS-22001: AEM Forms as a Cloud Service에서 대량 `/etc.clientlibs/toggles.json`개의 요청을 줄이기 위한 지침을 추가했습니다.
* FORMS-22496: Invoke 서비스에 원시 ResponseBody를 표시합니다.
* FORMS-22495: SetProperty 규칙에 자리 표시자 속성을 추가합니다.
* FORMS-21925: UBS 각주 서식: 양식을 로드하는 동안 양식의 모든 각주를 표시합니다.
* FORMS-20536: 매핑 없이 규칙 편집기의 eventPayload에 전체 응답 옵션을 표시합니다.
* SITES-37199: 주석 기능이 확인되지 않은 `authorizables.json` 호출을 통해 저장소 순회를 트리거하여 성능이 저하됩니다.
* SITES-37118: 제품 관리실의 Commerce Optimizer 지원.
* SITES-38029: 수정 이벤트에서 MSM 푸시를 추적하기 위한 로그를 추가합니다.
* SITES-37050: 게시된 다른 리소스에서 참조하는 콘텐츠 조각의 게시를 취소할 수 있는 &quot;강제 게시 취소&quot;를 지원합니다.
* SITES-37142: 컨텐츠 조각 PATCH을 통해 컨텐츠 조각을 체크인/체크아웃하는 기능이 추가되었습니다.
* SITES-37613: CF API 권한 끝점에서 사용자가 콘텐츠 조각을 체크 인할 수 있는 경우 체크 인 을 반환하고 사용자가 콘텐츠 조각을 체크 아웃할 수 있는 경우 체크 아웃을 반환합니다.
* SITES-37835: 제목은 동일하지만 제공된 이름은 없는 여러 콘텐츠 조각을 만들려고 할 때 충돌로 인해 실패하는 대신 새 이름을 자동으로 생성합니다.
* SITES-36823: 범용 편집기가 있는 Edge Delivery: 색인에 대한 역방향 매핑이 필요하지 않습니다.
* SITES-34751: 범용 편집기가 있는 Edge Delivery: 지원되지 않는 파일 형식 및 게시(조기 액세스) 시 경로를 사용할 수 없습니다.
* SITES-37888: 범용 편집기가 있는 Edge Delivery: 링크의 텍스트 동의어로 Alt 접미사를 사용합니다.
* SITES-19850: 범용 편집기가 있는 Edge Delivery: 스프레드시트의 여러 시트에 대한 지원을 추가합니다.
* SITES-32490: 범용 편집기가 있는 Edge Delivery: 블록 및 기본 콘텐츠에 데이터-오디오 구성 요소 및 사용자 정의 데이터-오디오 레이블에 대한 지원을 추가합니다.
* SITES-37794: 범용 편집기가 있는 Edge Delivery: 페이지 생성 마법사 간소화.
* SITES-36963: Workspace 지원을 위해 대상/세그먼트 끝점을 Target API v3로 마이그레이션합니다.

### 해결된 문제 {#fixed-issues-23862}

* CQ-4361831: genai_dropdown_span을 발생시키는 해결된 문제가 정의되지 않았습니다.
* CQ-4360895: 동시 업데이트 중 프로젝트의 부정확한 번역 작업 상태 수를 수정했습니다.
* CQ-4361599: 2025.7 업그레이드 후 번역 작업에서 콘텐츠 조각을 건너뛰는 문제를 해결했습니다.
* CQ-4360747: 고정 반복 가능한 번역 작업은 빈 페이로드를 만들고 너무 자주 트리거합니다(ScheduleRepeatTranslationProject의 NullPointerException).
* CQ-4359994: 단일 및 다국어 프로젝트에 대한 destinationLanguage 필드 유형 불일치가 수정되었습니다.
* SITES-38153: UUID 기반 참조에 대한 cf 게시 참조 공급자를 수정합니다.
* SITES-37594: 태그 기능별 모델의 성능이 개선되었습니다.
* SITES-37337: FragmentCreateProcessor: 로그에 추가 오류 세부 정보를 제공합니다.
* SITES-33666: 콘텐츠 조각 편집기에서 현지화되지 않은 &#39;조각의 Json을 인쇄할 수 없음&#39; 오류 메시지입니다.
* SITES-33675: 콘텐츠 조각 편집기 > 관련 콘텐츠에 하드코딩된 &#39;정의되지 않음&#39; 문자열.
* SITES-30715: 콘텐츠 조각 편집기에서 현지화되지 않은 &#39;일반&#39; 문자열입니다.
* SITES-28592: 콘텐츠 조각 모델 편집기 > &#39;모델이 잠겨 있습니다&#39; 대화 상자에서 현지화되지 않은 문자열.
* SITES-977: 문자열 &quot;태그&quot; 및 &quot;컬렉션&quot;은 콘텐츠 조각 편집 페이지에서 현지화되지 않습니다.
* SITES-29699: 콘텐츠 조각 편집기에서 현지화되지 않은 유형의 허용된 에셋입니다.
* SITES-25240: 티저 모달의 Call to action 필드에는 레이블이 표시되지 않습니다.
* SITES-24869: 템플릿 편집기 > 구분 기호 > 정책에서 툴팁이 잘렸습니다.
* SITES-19313: 구성 요소를 템플릿 편집기에서 삭제된 템플릿으로 끌어다 놓으면 오류가 현지화되지 않습니다.
* SITES-18103: 페이지 편집기 > 워크플로우에서 현지화되지 않은 문자열.
* SITES-17501: 템플릿 편집기 > 구성 요소 정책 편집기의 현지화되지 않은 문자열.
* SITES-15091: 경험 조각의 텍스트 구성 요소 속성에서 문자열이 현지화되지 않습니다.
* SITES-8113: &#39;Assets&#39; 문자열이 도구 메뉴의 &#39;템플릿&#39;에 대한 &#39;이미지 선택&#39; 대화 상자에서 현지화되지 않았습니다.
* SITES-37587: PROD에서 라이브 카피를 작성할 때 RolloutManagerImpl의 NPE를 사용할 경우 여전히 실패합니다.
* SITES-37335: cq 태그와 관련된 콘솔에 오류를 표시하는 라이브 카피 페이지 속성.
* SITES-36972: 편집 가능한 도구 모음에 &quot;롤아웃&quot; 버튼이 없습니다.
* SITES-36570: 청크된 라이브 카피 만들기 토글이 활성화된 후 라이브 카피를 만들 수 없습니다.
* SITES-36158: 예외로 인해 작업이 실패하여 롤아웃이 실패합니다.
* SITES-35655: 새 CF 편집기에서 상속이 끊긴 후 활성 상속을 표시합니다.
* SITES-31425: 사이트의 시작 워크플로우에 지역화되지 않은 오류 메시지 `Error: {} field is required`이(가) 표시됩니다.
* SITES-19802: 툴팁이 핵심 구성 요소 사이트 > 목차에서 현지화되지 않았습니다.
* SITES-36543: 관리자가 체크아웃된 콘텐츠 조각을 편집할 수 있는 문제를 해결했습니다.
* SITES-36967: 끊어진 콘텐츠 조각에 대한 썸네일 데이터를 생성하려고 할 때 발생하는 NullPointerExceptions가 수정되었습니다.
* SITES-37791: `$`이(가) 포함된 문자열에 대해 FindAndReplace를 호출하지 못하는 문제가 해결되었습니다.
* SITES-37018: 허용되지 않는 템플릿 경로가 있는 페이지를 복사할 때 빈 오류 팝업이 표시됩니다.
* SITES-36243: 유니버설 편집기가 있는 Edge Delivery: `sling:OrderedFolder`을(를) 게시하는 동안 404를 수정했습니다.
* SITES-37684: 범용 편집기가 있는 Edge Delivery: 사이트가 많은 환경에서 성능 저하를 수정합니다.
* SITES-37840: 범용 편집기가 있는 Edge Delivery: Edge Delivery에 대한 오래된 액세스 토큰으로 인한 게시 오류를 수정합니다.
* SITES-37933: 범용 편집기가 있는 Edge Delivery: Launches에서 삭제된 리소스에 대한 게시 오류를 수정(게시 취소)합니다.
* SITES-37870: 범용 편집기가 있는 Edge Delivery: 다중 필드 지원이 활성화된 사용자 지정 페이지 메타데이터의 끊어진 렌더링을 수정합니다.
* SITES-37349: 범용 편집기가 있는 Edge Delivery: 단일 항목이 있는 다중 필드를 단일 목록 항목이 있는 목록으로 렌더링합니다.
* SITES-36148: 범용 편집기가 있는 Edge Delivery: 복합 다중 필드에 대한 데이터 자동 레이블을 수정합니다.

### 알려진 문제 {#known-issues-23862}

없음.

### 사용 중단된 기능 및 API {#deprecated-23862}

AEM as a Cloud Service에서 더 이상 사용되지 않는 기능과 API는 [사용 중단된 기능 및 API](/help/release-notes/deprecated-removed-features.md) 문서에 자세히 설명되어 있습니다.

### 보안 수정 {#security-23862}

AEM as a Cloud Service는 플랫폼의 보안 및 성능 최적화에 중점을 둡니다. 이 유지 관리 릴리스는 23개의 식별된 취약점을 해결하여 강력한 시스템 보호에 대한 노력을 강화합니다.

### 임베드된 기술 {#embedded-tech-23862}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM Oak | 1.88.0 | [Oak 1.88.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88.0/index.html) |
| AEM SLING API | 2.27.6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| Apache HTTP 서버 | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM 핵심 구성 요소 | 2.30.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (기본값) | [지원되는 Node.js 버전](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
