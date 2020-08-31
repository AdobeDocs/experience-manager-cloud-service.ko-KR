---
title: 구성 요소 개요
description: 구성 요소는 웹 사이트에 컨텐츠를 제공하기 위한 특정 기능을 구현하는 모듈형 유닛입니다
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 7%

---


# 구성 요소 개요 {#components-overview}

이 페이지에서는 페이지 작성에 [사용된 것과 같은 Adobe Experience Manager(AEM) 구성 요소에 대한 개요를 제공합니다](/help/sites-cloud/authoring/fundamentals/components.md).

## 구성 요소란? {#what-are-components}

AEM의 구성 요소는 다음과 같습니다.

* 웹 사이트에 컨텐츠를 제공하기 위한 특정 기능을 실현하는 모듈형 유닛
* 재사용
* 저장소의 한 폴더 내에 독립된 단위로 개발되었습니다.
* 숨겨진 구성 파일이 없습니다.
* 다른 구성 요소를 포함할 수 있습니다.
* 모든 AEM 시스템 내에서 실행할 수 있으며 특정 구성 요소에서 실행되도록 제한할 수 있습니다.
* 사용자 인터페이스가 표준화되었습니다.
* 구성할 수 있는 편집 비헤이비어가 있어야 합니다.
* [MOCK] Use dialog box that are built using sub-elements based on Granite UI components.
* HTL을 사용하여 [개발됩니다](https://docs.adobe.com/content/help/ko-KR/experience-manager-htl/using/overview.html).
* 기본 기능을 확장하는 사용자 지정된 구성 요소를 만들기 위해 개발할 수 있습니다.

구성 요소는 모듈이므로 다음을 수행할 수 있습니다.

* 로컬 인스턴스에서 새 구성 요소를 개발합니다.
* 테스트 환경에 배포합니다.
* 작성자 및/또는 관리자가 컨텐츠를 추가하고 구성할 수 있는 라이브 제작 환경에 배포합니다.
* 웹 사이트 방문자의 컨텐츠를 렌더링하는 데 사용되는 라이브 게시 환경에 배포합니다.

각 AEM 구성 요소:

* 리소스 유형입니다.
* 특정 기능을 완벽하게 구현하는 스크립트 모음입니다.
* AEM 또는 포털 내에서 또는 포털 내에서 격리된 상태에서 작동할 수 있습니다.

## AEM 핵심 구성 요소 {#aem-core-components}

[AEM 코어 구성 요소는](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html) 개발 시간을 단축하고 웹 사이트의 유지 관리 비용을 줄일 수 있도록 AEM용 표준화된 WCM(Web Content Management) 구성 요소 세트입니다.

핵심 구성 요소는 AEM에 Cloud Service으로 제공되며 [WKND 자습서에서는 구성 요소를 구현하고 사용하는 방법을 설명합니다](/help/implementing/developing/introduction/develop-wknd-tutorial.md) . 구성 요소는 모든 소스 코드와 함께 제공되며, 수정하거나 확장된 구성 요소의 시작점으로 사용할 수 있습니다.

### 사용 가능한 구성 요소 보기 {#viewing-available-components}

AEM 인스턴스에서 사용 가능한 모든 구성 요소에 대한 개요를 보려면 구성 요소 [콘솔을 사용하십시오](/help/sites-cloud/authoring/features/components-console.md).

또는 CRXDE Lite을 사용하여 저장소에서 사용 가능한 모든 구성 요소 목록을 가져올 수도 있습니다.

1. CRXDE Lite의 **[!UICONTROL 도구 모음]**&#x200B;에서 도구 **[!UICONTROL 를 선택한 다음]** 쿼리 **[!UICONTROL 를 선택하면]** QueryTab을 **[!UICONTROL 열 수 있습니다]** .

1. [ **[!UICONTROL 쿼리]** ] 탭에서 `XPath` 유형으로 **[!UICONTROL 선택합니다]**.

1. **[!UICONTROL 쿼리]** 입력 필드에 다음 문자열을 입력합니다.

   `//element(*, cq:Component)`

1. 실행 **[!UICONTROL 을]** 클릭하면 구성 요소가 나열됩니다.

