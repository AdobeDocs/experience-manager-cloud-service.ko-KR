---
title: RemotePage 구성 요소
description: RemotePage 구성 요소는 AEM 내에서 원격 반응 SPA을 편집하기 위한 사용자 지정 페이지 구성 요소입니다.
translation-type: tm+mt
source-git-commit: 6a88b93a4005b858eec222fd7ae15df9db269d31
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---

# RemotePage 구성 요소 {#remote-page-component}

외부 SPA과 AEM 간에 포함할 [통합 수준을 결정할 때 AEM 내에서 SPA을 보고 편집할 수 있어야 하는 것이 일반적입니다. ](/help/implementing/developing/headful-headless.md) RemotePage 구성 요소는 이 목적을 위해 사용자 지정 페이지 구성 요소입니다.

## 개요 {#overview}

RemotePage 구성 요소는 애플리케이션에서 생성된 `asset-manifest.json`에서 필요한 모든 에셋을 가져오고 AEM 내에서 SPA을 렌더링하는 데 사용합니다.

## 요구 사항 {#requirements}

* 개발 시 CORS 활성화
* 페이지 속성에서 원격 URL 구성
* AEM에서 SPA 렌더링

## 제한 사항 {#limitations}

* RemotePage 구성 요소의 현재 구현은 원격 응답 애플리케이션만 지원합니다.
* AEM에서 원격 렌더링을 수행할 때 애플리케이션의 루트 HTML 파일과 루트 DOM 노드의 인라인 CSS에 정의된 내부 CSS를 사용할 수 없습니다.

## 기술 세부 정보 {#technical-details}

나머지 AEM SPA 프로젝트와 마찬가지로 RemotePage 구성 요소는 오픈 소스입니다. RemotePage 구성 요소에 대한 전체 기술 세부 정보는 [GitHub 리포지토리를 참조하십시오.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
