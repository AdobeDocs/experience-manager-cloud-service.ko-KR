---
title: Adobe Experience Manager as a Cloud Service용 마이크로 프론트엔드 콘텐츠 조각 선택기
description: 마이크로 프론트엔드 콘텐츠 조각 선택기를 사용하여 애플리케이션에서 콘텐츠 조각을 검색, 찾기 및 검색합니다.
role: Admin, User
source-git-commit: 32e1b3cef768b420f32b70202ddadc80db2b74e8
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 11%

---


# 마이크로 프론트엔드 콘텐츠 조각 선택기 {#micro-frontend-content-fragment-selector}

마이크로 프론트엔드 콘텐츠 조각 선택기는 Adobe Experience Manager(AEM) as a Cloud Service 저장소와 쉽게 통합하는 사용자 인터페이스를 제공합니다. 인터페이스에서 저장소의 콘텐츠 조각을 찾아보거나 검색하고 애플리케이션에서 사용할 수 있습니다.

Micro-Frontend 사용자 인터페이스는 콘텐츠 조각 선택기 패키지를 사용하여 애플리케이션에서 사용할 수 있습니다. 패키지에 대한 모든 업데이트는 애플리케이션에 자동으로 가져와서 로드됩니다.

![마이크로 프론트엔드 콘텐츠 조각 선택기 - 개요](/help/headless/assets/content-fragment-selector-overview.png)

콘텐츠 조각 선택기는 다음과 같은 많은 이점을 제공합니다.

* 모든 Adobe 애플리케이션과의 간편한 통합
* 콘텐츠 조각 선택기 패키지에 대한 업데이트는 애플리케이션에서 사용할 수 있는 콘텐츠 조각 선택기에 자동으로 배포되므로 유지 관리가 쉽습니다. 즉, 애플리케이션이 최신 수정 사항을 로드하기 위해 조치를 취할 필요가 없습니다.
* 애플리케이션 내에서 콘텐츠 조각 선택기 표시를 제어하는 속성을 사용하여 간편하게 맞춤화할 수 있습니다.
* 전체 텍스트 검색과 맞춤형 필터를 사용하면 작성 환경 내에서 콘텐츠 조각을 빠르게 탐색할 수 있습니다.
* 콘텐츠 조각 선택을 위해 IMS 조직 내에서 저장소를 전환하는 기능입니다.
* 콘텐츠 조각을 정렬하고 선택한 보기에서 보는 기능.

## 사전 요구 사항 {#prerequisites}

### IMS 인증 {#ims-authentication}

IMS 인증 워크플로가 필요한 경우 다음을 확인해야 합니다.

* 응용 프로그램이 `HTTPS`에서 실행 중입니다.
* 애플리케이션의 URL이 IMS 클라이언트에 대해 허용되는 리디렉션 URL 목록에 있습니다.
* IMS 로그인 흐름은 웹 브라우저의 팝업을 사용하여 구성 및 렌더링됩니다. 따라서 타깃 브라우저에서 팝업을 활성화하거나 허용해야 합니다.

또는 애플리케이션이 IMS 워크플로우로 이미 인증된 경우 대신 적절한 IMS 정보를 추가할 수 있습니다.

## 설치 {#installation}

`ContentFragmentSelector` 구성 요소를 사용합니다. 몇 가지 설치 옵션이 있습니다.

1. NPM 레지스트리(개인 Adobe 레지스트리)

   * `.npmrc`에 다음 추가:

     ```html
     @aem-sites:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-sites-release/
     ```

   * 그런 다음 설치

     ```html
     npm install @aem-sites/content-fragment-selector
     ```

1. Git 저장소

   * `package.json` 종속성에 다음 내용을 추가하십시오.

     ```html
     "@aem-sites/content-fragment-selector": "git+https://github.com/adobe/<your-private-repo-url>.git#version"
     ```

## 콘텐츠 조각 선택기 사용 {#using-the-Content-Fragment-selector}

AEM as a Cloud Service 애플리케이션에서 콘텐츠 조각 선택기를 사용하도록 콘텐츠 조각 선택기를 설정하고 인증하면 콘텐츠 조각을 선택하거나 다양한 작업을 수행하여 저장소에서 조각을 검색할 수 있습니다.

![콘텐츠 조각 선택기](/help/headless/assets/content-fragment-selector-using.png)

* 오른쪽 상단의 **저장소** 선택기를 사용하여 사용할 저장소를 선택할 수 있습니다
* 맨 왼쪽 패널에서 다음 작업을 수행할 수 있습니다.
   * 선택한 저장소에서 폴더 숨기기 또는 표시
   * 특정 폴더를 선택하여 해당 폴더에 콘텐츠 조각 표시
* 기본 패널에서 다음 작업을 수행할 수 있습니다.
   * 콘텐츠 조각 선택
   * 콘텐츠 조각 검색
   * 현재 목록을 오름차순 또는 내림차순 모두 다양한 열에 따라 정렬
   * 보기 형식 표시기 참조
   * 필터 표시, 숨기기 및 지정

### 패널 숨기기/표시 {#hide-show-panel}

왼쪽 탐색 영역에서 폴더를 숨기려면 **폴더 숨기기** 아이콘을 클릭합니다. 변경 내용을 실행 취소하려면 **폴더 숨기기** 아이콘을 다시 클릭합니다.

### 저장소 전환기 {#repository-switcher}

콘텐츠 조각 선택기를 사용하여 조각을 선택할 저장소를 선택할 수 있습니다.

기본 패널 위쪽에 있는 **저장소** 드롭다운에서 원하는 저장소를 선택할 수 있습니다.

![콘텐츠 조각 선택기](/help/headless/assets/content-fragment-repository-selector.png)

드롭다운 목록에서 사용할 수 있는 저장소 옵션은 `index.html` 파일에 정의된 `repositoryId` 속성을 기반으로 하며, 이 속성은 현재 로그인한 사용자가 액세스한 선택한 IMS 조직의 환경을 기반으로 합니다.

소비자는 기본 설정 `repositoryID`을(를) 전달하여 특정 리포지토리에서 조각을 렌더링하고 리포지토리 전환기 렌더링을 중지할 수 있습니다.

### 콘텐츠 조각 폴더 {#content-fragments-folders}

콘텐츠 조각 저장소는 작업을 수행하는 데 사용할 수 있는 콘텐츠 조각 폴더의 모음입니다.

### 필터 {#filters}

콘텐츠 조각 선택기는 또한 검색 결과를 구체화하는 기본 필터 옵션을 제공합니다. 다음을 포함한 다양한 필터를 사용할 수 있습니다.

* **조각 모델**
* **로컬라이제이션**
* **상태**: 조각의 현재 상태; `New`, `Draft`, `Published`, `Modified`, `Unpublished`
* 태그
* 사용자
* 시간 및 날짜

![필터 옵션](/help/headless/assets/content-selector-filters.png)

기본 검색 필터를 만들어 나중에 사용할 수 있도록 저장할 수도 있습니다. 콘텐츠 조각에 대한 사용자 지정 검색 필터를 만들려면 `filterSchema` 속성을 사용할 수 있습니다.

### 검색 창 {#search-bar}

콘텐츠 조각 선택기를 사용하여 선택한 저장소 내에서 조각의 전체 텍스트 검색을 수행할 수 있습니다. 예를 들어 검색 막대에 `wave` 키워드를 입력하면 메타데이터 속성에서 `wave` 키워드가 언급된 모든 조각이 표시됩니다.

### 정렬 {#sorting}

콘텐츠 조각 선택기에서 다양한 속성을 기준으로 조각을 정렬할 수 있습니다. 조각을 오름차순 또는 내림차순으로 정렬할 수도 있습니다.

### 보기 유형 {#view-type}

콘텐츠 조각 선택기 를 사용하여 다음에서 조각을 볼 수 있습니다.

* **테이블 보기**
