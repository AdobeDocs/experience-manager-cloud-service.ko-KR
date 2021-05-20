---
title: RemotePage 구성 요소
description: RemotePage 구성 요소는 AEM 내에서 원격 React SPA을 편집하는 사용자 지정 페이지 구성 요소입니다.
exl-id: d3465592-0392-49b0-b49d-de93983c1d6e
source-git-commit: eaa59b6ecfa50c4a6b4e316e5e305e48cb3d5676
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# RemotePage 구성 요소 {#remote-page-component}

외부 SPA과 AEM 간에 포함할 [통합 수준을 결정할 때 AEM 내에서 SPA을 보고 편집할 수 있어야 하는 것이 종종 분명합니다. ](/help/implementing/developing/headful-headless.md) RemotePage 구성 요소는 이러한 목적을 위해 사용자 지정 페이지 구성 요소입니다.

## 개요 {#overview}

RemotePage 구성 요소는 애플리케이션에서 생성된 `asset-manifest.json`에서 필요한 모든 자산을 가져와서 AEM 내에서 SPA을 렌더링하는 데 사용합니다.

* RemotePage를 사용하면 AEM Page 구성 요소의 본문에 SPA의 스크립트 및 스타일시트를 삽입할 수 있습니다.
* 가상 프런트 엔드 구성 요소를 사용하면 AEM SPA 편집기에서 섹션을 편집 가능으로 표시할 수 있습니다.
* 함께, 다른 도메인에 호스팅된 SPA을 AEM에서 편집할 수 있습니다.

편집 가능한 AEM의 외부 SPA에 대한 자세한 내용은 [AEM](editing-external-spa.md)에서 외부 SPA 편집 문서를 참조하십시오.

## 요구 사항 {#requirements}

* 개발 시 CORS 활성화
* 페이지 속성에서 원격 URL 구성
* AEM에서 SPA 렌더링
* 웹 응용 프로그램은 다음 중 하나와 같은 번들러 자산 매니페스트를 사용하고, 로드하려는 모든 CSS 및 JS 파일을 `entrypoints property` 도메인 루트에 나열하는 `asset-manifest.json` 파일을 노출해야 합니다.
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest
      ![entrypoints 속성 예](assets/asset-manifest-entrypoints.png)
* `body` 요소 아래에 있는 `<div id="root"></div>`에서 응용 프로그램을 초기화할 수 있어야 합니다. 앱을 인스턴스화하는 데 다른 마크업이 필요한 경우 `sling:resourceSuperType="spa-project-core/components/remotepage`이 있는 프록시 구성 요소의 HTL 스크립트에서 이에 따라 조정해야 합니다.

## 제한 사항 {#limitations}

* RemotePage 구성 요소의 현재 구현은 원격 React 응용 프로그램만 지원합니다.
* AEM에서 원격 렌더링을 수행할 때 애플리케이션의 루트 HTML 파일과 루트 DOM 노드의 인라인 CSS에 정의된 내부 CSS를 사용할 수 없습니다.

## 기술 세부 정보 {#technical-details}

AEM SPA 프로젝트의 나머지 부분처럼 RemotePage 구성 요소는 오픈 소스입니다. RemotePage 구성 요소에 대한 전체 기술 세부 사항은 [GitHub 리포지토리를 참조하십시오.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
