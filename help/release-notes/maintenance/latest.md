---
title: 의 최신 유지 관리 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
description: 의 최신 유지 관리 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 76da86d31e2780c2d22419cb8a338cf37963fad8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 5%

---


# 유지 관리 릴리스 노트 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service의 최신 유지 관리 릴리스에 대한 기술 릴리스 노트를 간략하게 설명합니다.

## 릴리스 10912 {#release-10912}

아래에 요약된 내용은 2023년 2월 3일에 발표된 유지 관리 릴리스 10912에 대한 지속적인 개선 사항입니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 9850의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [현재 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md) 자세한 내용

### 알려진 문제 {#known-issues}

CORS를 사용하는 경우 업그레이드하지 마십시오. 이 릴리스의 GraphQL 콘텐츠 전달 부분에 영향을 주는 문제를 해결했습니다. GraphQL 지속적인 쿼리가 캐시되는 방식에 대한 기본 AEM Dispatcher 구성의 변경으로 인해 CORS 구성을 사용하는 고객을 위한 GraphQL 콘텐츠 전달이 중단될 수 있습니다.

### 임베디드 기술 {#embedded-tech}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM WCM 코어 구성 요소 | 버전 2.21.2 | [GitHub](https://github.com/adobe/aem-core-wcm-components) |
