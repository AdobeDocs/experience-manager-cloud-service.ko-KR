---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 01f148dbe885c96b27f88a88e7020a1008f4c1d3
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 98%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 14029 {#release-14029}

2023년 10월 25일에 릴리스된 유지 관리 릴리스 14029의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 13804의 업데이트입니다.

이 유지 관리 릴리스(2023.11.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-14029}

* ASSETS-28551: 내 링크 공유 UI의 확장성 개선
* ASSETS-28566: dam:metadataForm Lucene 인덱스 추가
* ASSETS-29281: RAPI를 업데이트하여 v2 다운로드 이벤트 보내기

### 해결된 문제 {#fixed-issues-14029}

* ASSETS-25199: 이미지 코어 구성 요소에 적합한 스마트 자르기가 표시되지 않음
* ASSETS-26142: 검색 요청이 실패 또는 중단된 경우 Unified-shell.js customEnvLabel이 설정되지 않거나 다시 시도됨
* ASSETS-26416: 상대적 날짜 조건자는 검색 양식에서 항상 “1일 전”으로 정의됨
* ASSETS-27321: 팀 멤버십 변경 사항에서 그룹 캐시 지우기
* ASSETS-27591: 이전 org.json에 대한 종속성 수정
* ASSETS-28439: 전역 차단 목록이 구성되지 않은 경우의 스마트 태그 차단 목록 NPE
* ASSETS-28612: “repository-api”의 BlockedTagResolver 수정
* ASSETS-28634: Adobe Stock의 Omnisearch 필드에 자산 데이터가 자동으로 추가되지 않음
* ASSETS-28727: 처리 프로필 구성 목록에 지정된 사용자 정의 높이 및 폭 값이 표시되지 않음
* ASSETS-29056: 트랜스코딩 렌디션 AEM 표준 처리 프로필 추가
* ASSETS-29105: RDE 기능 모델의 SecurityProviderRegistration requiredServicePids에 제한 공급자가 없음
* ASSETS-29106: 통합 셸이 AEM에 활성화되면 Adobe Stock 보기에 오류 발생
* ASSETS-29115: 제한 공급자 경로의 구성 속성 제거
* ASSETS-29208: 서비스 CompleteUploadAssetServlet 등록 이전에 작성자 Pod에 전송된 요청으로 인해 자산 업로드 오류 발생
* ASSETS-29297: 체크아웃된 필터 옵션으로 검색 저장을 생성하는 동안 문제 발생
* ASSETS-29363: 메타데이터 프로필에서 IPTC의 기본값이 적용되지 않음
* ASSETS-29404: 링크 공유 보고서가 쿼리 제한에 도달함
* ASSETS-29431: 이전 기능 플래그 제거
* ASSETS-29443: Granite 셀 헤더 모드가 “선택”으로 변경되면 통합 쉘 Hero가 계속 표시되고 클릭 가능
* ASSETS-29476: scene7DAMService.getS7FileReference(asset) API 호출은 예상 값을 반환하지 않음
* ASSETS-29515: “jcr:lastModifiedBy”가 포함된 자산/노드: “workflow-process-service”는 목록 보기에서 “외부 사용자”로 표시됨
* ASSETS-29579: NonAdmin 사용자는 이미지 세트를 생성할 수 없음
* ASSETS-29631: 보안 게재/검색에 dam:roles 사용
* ASSETS-29689: dc:roles(및 새 속성 dam:roles)는 AEM 측에서 필터링되어야 함
* ASSETS-29738: NullPointerException으로 인해 자산 업로드 제한 실패
* ASSETS-29779: Blob 스토리지에 없으므로 소규모 자산은 webp로 처리할 수 없음
* ASSETS-29892: 자산 수가 많은 폴더에서 메타데이터 내보내기 실패
* ASSETS-29996: PROD 인스턴스에서만 자산을 간헐적으로 업로드하는 경우 수정자로 “외부 사용자” 설정
* ASSETS-30167: 자산을 업로드한 후 adobe_dam:restrictions에 대한 HTML이 중단됨
* ASSETS-30276: 공유 링크 UI: assetdetails에서 공유할 수 없음
* ASSETS-30434: 자산 처리가 완료되면 이벤트가 파이프라인에 전송되지 않음
* ASSETS-30519: REDMetricsServletFilter에 RAPI 추가
* CQ-4354413: QueryBuilder: 대괄호가 포함된 쿼리가 xpath로 잘못 번역됨
* CQ-4354834: 받은 편지함 작업에 댓글을 추가할 수 없음
* CQ-4354836: 프로젝트 콘솔에서 워크플로를 시작하거나 작업을 생성할 수 없음
* CQ-4354867: ToggleCondition 참조는 InstanceActionServlet에 존재하지 않는 필드를 의미함
* CQ-4354895: AEM 번역 키트: 10월 12일
* GRANITE-45560: 이벤트 봉투에 공통 스키마 표시
* GRANITE-47267: Apache Felix Http Jetty 4.2.18 업데이트
* GRANITE-47599: 13323 업그레이드 이후 콘텐츠 가져오기 실패(JCRVLT-721)
* GRANITE-47873: Apache Felix Webconsole 4.9.6 업데이트

### 알려진 문제 {#known-issues-14029}

* ASSETS-31015: 알 수 없는 파일 확장명을 가진 에셋에 파일을 업로드할 수 없습니다.

### 임베드된 기술 {#embedded-tech-14029}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [Oak API 1.56.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
