---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 8a1ed1e44db0154854af73a96339d8e416afd3b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 53%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 13420 {#release-13420}

2023년 9월 12일에 릴리스된 유지 관리 릴리스 13420의 지속적인 개선 사항이 아래에 요약되어 있습니다. 이 유지 관리 릴리스에서는 릴리스 13323를 대체합니다.

이 유지 관리 릴리스(2023.9.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-13420}

- ASSETS-19544: 마지막으로 수정한 자산 속성이 이제 처리를 요청하는 사용자로 설정됩니다.

### 해결된 문제 {#fixed-issues-13420}

- ASSETS-27628: 에셋 검색 패널을 사용자 정의할 때 잘못된 &quot;채널&quot; 노드가 생성됨
- ASSETS-27539: 업로드 제한 사항 정규 표현식 일치.
- ASSETS-26530: 통합 쉘은 사용자를 원래 페이지로 다시 불러오지 않습니다.
- ASSETS-22719: 스마트 자르기 중단점 이름 지정의 대괄호로 스마트 자르기 편집 기능이 중단됩니다.
- ASSETS-27726: linkshare.html을 Google으로 인덱싱해서는 안 됩니다.
- ASSETS-27791: 메타데이터 스키마 유효성 검사는 첫 번째 필드에 대해서만 발생합니다.
- ASSETS-25544: 비활성화된 CDN 캐시 무효화 단추가 수정되었습니다.
- ASSETS-26575: 이미지 집합을 만들 때 이름이 잘리는 문제가 해결되었습니다.
- ASSETS-26705: DM이 아닌 폴더 에셋 및 콘텐츠 조각에 대한 불필요한 처리가 수정되었습니다.
- ASSETS-25740: 아래쪽 화살표 키를 사용하여 &#39;스마트 자르기 편집&#39; 페이지에서 편집/자르기 컨트롤의 이름 및 역할에 내레이션을 지정하지 않은 고정 화면 판독기입니다.
- CQ-4354266: 받은 편지함 항목을 열 수 없습니다.
- CQ-4354347: AEM 번역을 업데이트했습니다.
- DISP-1009: 첫 번째 헤더가 아닌 사용자 에이전트는 X-Forwarded-Host를 트리밍합니다.
- 다양한 접근성 및 보안 관련 수정 사항.

### 알려진 문제 {#known-issues-13420}

없음.

### 임베드된 기술 {#embedded-tech-13420}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.54-T20230817132355-3800a65 | [Oak API 1.54.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
