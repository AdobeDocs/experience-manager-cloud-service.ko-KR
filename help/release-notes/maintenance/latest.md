---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: acaed9eed20e8134574fd326e23ac68130ac019b
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 14%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 12874 {#release-12874}

2023년 8월 2일에 공개적으로 릴리스된 유지 보수 릴리스 12874에 대한 지속적인 개선 사항을 요약하면 다음과 같습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 12790의 업데이트입니다.

이 유지 관리 릴리스(2023.8.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 향상된 기능 {#enhancements-12874}

- 색인 정의의 새 버전: `/oak:index/damAssetLucene-9`
- ASSETS-18351: 비보안 패싯으로 전환하여 검색 성능을 개선합니다.
- ASSETS-17896: 스마트 태그를 기반으로 색인에서 기능 벡터 제거 - 유사성 검색
- ASSETS-8715: &quot;jcr:content/metadata/dam:status&quot; 속성에 대해 null 확인/null 아님 확인을 추가합니다.
- GRANITE-45138: 예측된 태그 동적 부스트 속성에서 속성 인덱스를 제거합니다.
- ASSETS-17614: Scene7 ID를 인덱싱된 속성으로 추가합니다(null 확인 및 null 확인 아님).
- ASSETS-14516: &#39;새 UI&#39; 휴지통 기능에 대한 속성을 인덱스에 추가합니다.
- ASSETS-16270: 병합된 제목 속성을 인덱스에 추가합니다(정렬에 사용).
- ASSETS-24478: 색인에서 잠재적으로 크기가 큰 5개의 속성 제거(고객 색인 데이터의 분석을 기반으로 함)
- ASSETS-3383: &#39;assetsOmnisearch&#39; 태그를 추가합니다.

AEM 릴리스 12874 이상에는 damAssetLucene 인덱스의 새 버전(damAssetLucene-9)이 포함되어 있습니다. 가장 반응형 검색 경험을 제공하기 위해 damAssetLucene-9는 기본 검색 색인에 의해 반환된 패싯 카운트(이하 &quot;비보안&quot; 모드)에 대한 액세스 제어를 더 이상 평가하지 않도록 Oak 쿼리 결과 페이시트의 비헤이비어를 변경합니다.

따라서 현재 사용자가 액세스할 수 없는 에셋을 포함하는 Facet 카운트 값이 사용자에게 제공될 수 있습니다. 따라서 사용자는 이러한 에셋에 액세스하거나 다운로드하거나 읽을 수 없으며 에셋의 존재 여부에 대한 추가 정보도 얻을 수 없습니다.

이전 동작을 원하는 경우 고객은 다음에 설명된 단계를 따라야 합니다 [콘텐츠 검색 및 색인화](/help/operations/indexing.md) damAssetLucene-9 인덱스의 사용자 지정 버전을 이전 &quot;통계적&quot; 패싯 모드로 만듭니다.

### 해결된 문제 {#fixed-issues-12874}

- ASSETS-24379: ReplicateOnModifyListener를 개선했습니다.
- ASSETS-25794: 시작 시 고가의 쿼리를 실행하게 했던 S7ConfigResolverImpl 문제를 해결했습니다.
- ASSETS-25473: 복제 권한이 없는 사용자에게 빠른 게시 옵션이 표시되는 버그를 수정했습니다.
- ASSETS-24803: 뷰어 기능에서 XSS 취약성을 해결했습니다.
- ASSETS-25489: 스마트 자르기가 잘못된 접미사로 다운로드되던 문제를 수정했습니다.
- ASSETS-25435: 동적 변환용 다운로드에서 WidthxHeight 필드가 누락되는 오류를 해결했습니다
- ASSETS-25741: 시각적 별표(`*`) &#39;기본&#39; 탭 섹션의 필수 &#39;폭&#39; 편집 필드 기호입니다.
- ASSETS-25759: 고대비 흑백 모드에서 드롭다운 요소에 대한 포커스 가시성이 개선되었습니다.
- ASSETS-25749: 키보드 탭을 사용하여 탐색할 때 초점이 비디오 아래의 여러 컨트롤로 이동하지 않아 액세스할 수 없는 문제를 해결했습니다.
- ASSETS-26074: 비디오가 아닌 에셋의 이름에 대한 127자 제한을 복원했습니다.
- ASSETS-21428: 메타데이터 스키마 편집기의 여러 줄 필드가 다음 필드와 겹치는 문제가 수정되었습니다
- ASSETS-21989: 302 및 401 응답에서 CORS 헤더를 덮어써서 원격 DAM 로그인을 방지하는 문제가 수정되었습니다
- ASSETS-22603: 에셋 다운로드 보고서를 볼 때 열 이름 및 값에 영향을 주는 문제가 해결되었습니다
- ASSETS-23120: 리소스 확인자 누출과 관련된 AssetLastModifiedProcess 문제가 수정되었습니다.
- ASSETS-24938: 에셋 폴더 속성 대화 상자의 저장 단추가 저장 + 닫기와 같이 작동하던 문제를 해결했습니다
- ASSETS-25456: 긴 이름을 가진 에셋이 에셋 속성 편집기에서 작업을 클릭할 수 없는 문제가 수정되었습니다
- ASSETS-25832: 전체 액세스 폴더의 자산을 읽기 전용 액세스 폴더로 연결할 때 발생하는 문제를 해결했습니다.
- ASSETS-25397: 새 UI에서 이름이 변경된 에셋의 새 이름이 검색 결과에 반영되지 않는 문제가 수정되었습니다
- ASSETS-26102: CI Hub 커넥터에서 업로드를 방해하는 문제를 해결했습니다
- ASSETS-26172: 영구 Sling 작업 노드에 저장된 일괄 가져오기 진행률 로그 컨텐츠의 크기가 감소되었습니다.
- ASSETS-26292: Java API에서 더 이상 사용되지 않는 AssetManager createOrUpdateAsset() 및 createOrReplaceAsset() 메서드
- ASSETS-26399: 컬렉션이 Brand Portal에 게시되지 않는 문제를 해결했습니다
- ASSETS-26533: 긴 처리 요청에 대한 시간 초과로 이어질 수 있는 Indesign Server 통합 문제를 해결했습니다
- ASSETS-26549: 업로드된 모든 에셋에 대해 &quot;외부 사용자&quot;가 마지막으로 수정된 사용자로 표시되는 에셋 목록 보기의 문제를 해결했습니다
- ASSETS-26551: 작성자에서 삭제된 에셋의 게시가 취소되지 않는 문제가 해결되었습니다.
- ASSETS-26571: 목록에 실패한 보고서 작업이 여러 개 있는 경우 페이지를 로드하지 못하는 에셋 보고서 페이지의 문제를 해결했습니다
- ASSETS-26147: window.top.opener가 설정되어 있지만 window.opener가 설정되지 않은 경우 통합 쉘이 iframe을 /ui에 리디렉션하려고 시도하는 문제를 해결했습니다
- ASSETS-26576: 잘못된 폴더 계층 구조가 만들어진 Dropbox 가져오기 문제를 해결했습니다
- ASSETS-26671: 대량 가져오기에 DCIM 폴더 내에 있는 파일이 포함되지 않는 문제가 수정되었습니다
- ASSETS-26700: 변경 사항 없이 공용 폴더의 속성 페이지를 저장하면 3개의 불필요한 그룹이 생성되는 문제를 해결했습니다
- CQ-4353449: 읽기 전용 태그 지정 권한이 있는 사용자가 태그 지정 UI를 사용하여 태그를 만들 수 있는 문제를 해결했습니다
- GRANITE-46601: JDK 11.0.20에서 빠른 시작 SDK가 시작되지 않는 문제를 해결했습니다
- SKYOPS-33168: CM 개발자 콘솔에서 확장 없이 자산 이름에 대한 /content/dam을 로드할 수 없는 문제를 해결했습니다
- SKYOPS-61484: RDEProvider 서비스에서 사용하지 않은 ${sling.home} 토큰이 병합된 OSGi 구성에서 지속되도록 하는 문제가 해결되었습니다
- 다양한 보안, 접근성 및 현지화 수정 사항

### 알려진 문제 {#known-issues-12874}

- GRANITE-46851: 컨텐츠 배포의 테스트 연결이 작동하지 않음

### 임베드된 기술 {#embedded-tech-12874}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.0 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
