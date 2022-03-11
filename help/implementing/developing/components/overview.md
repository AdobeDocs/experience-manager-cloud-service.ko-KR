---
title: 구성 요소 개요
description: 구성 요소는 웹 사이트에 컨텐츠를 제공하는 특정 기능을 구현하는 모듈식 유닛입니다
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 6%

---

# 구성 요소 개요 {#components-overview}

이 페이지에서는 다음과 같은 Adobe Experience Manager(AEM) 구성 요소에 대한 개요를 제공합니다 [페이지 작성에 사용됨](/help/sites-cloud/authoring/fundamentals/components.md).

## 구성 요소란 무엇입니까? {#what-are-components}

AEM의 구성 요소는 다음과 같습니다.

* 웹 사이트에 컨텐츠를 제공하는 특정 기능을 실현하는 모듈식 유닛.
* 다시 사용할 수 있습니다.
* 리포지토리의 한 폴더 내에 자체 포함된 단위로 개발됩니다.
* 숨겨진 구성 파일이 없습니다.
* 다른 구성 요소를 포함할 수 있습니다.
* 모든 AEM 시스템 내에서 어디에서나 실행할 수 있으며 특정 구성 요소에서 실행되도록 제한할 수도 있습니다.
* 표준화된 사용자 인터페이스를 사용합니다.
* 구성할 수 있는 편집 동작이 있습니다.
* Granite UI 구성 요소를 기반으로 하위 요소를 사용하여 빌드된 대화 상자를 사용합니다.
* 를 사용하여 개발 [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=ko-KR).
* 기본 기능을 확장하는 사용자 지정된 구성 요소를 만들기 위해 개발할 수 있습니다.

구성 요소는 모듈이므로 다음 작업을 수행할 수 있습니다.

* 로컬 인스턴스에서 새 구성 요소를 개발합니다.
* 테스트 환경에 배포합니다.
* 작성자 및/또는 관리자가 컨텐츠를 추가하고 구성할 수 있는 라이브 작성 환경에 배포합니다.
* 웹 사이트 방문자를 위한 콘텐츠를 렌더링하는 데 사용되는 라이브 게시 환경에 배포합니다.

각 AEM 구성 요소:

* 리소스 유형입니다.
* 는 특정 기능을 완전히 구현하는 스크립트 컬렉션입니다.
* AEM 또는 포털 내에서 를 의미하는 격리된 상태에서 작동할 수 있습니다.

## AEM 핵심 구성 요소 {#aem-core-components}

[AEM 코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR) 는 개발 시간을 단축하고 웹 사이트의 유지 관리 비용을 절감할 수 있도록 AEM용 WCM(표준화된 웹 컨텐츠 관리) 구성 요소 세트입니다.

핵심 구성 요소는 AEM as a Cloud Service 및 과 함께 제공됩니다 [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 는 구성 요소 구현 및 사용 방법을 보여줍니다. 구성 요소는 모든 소스 코드와 함께 제공되며 수정 또는 확장 구성 요소의 시작점으로 사용하거나 그대로 사용할 수 있습니다.

### 사용 가능한 구성 요소 보기 {#viewing-available-components}

AEM 인스턴스에서 사용 가능한 모든 구성 요소에 대한 개요를 알려면 [구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md).

또는 CRXDE Lite을 사용하여 저장소에서 사용할 수 있는 모든 구성 요소 목록을 가져올 수도 있습니다.

1. in **[!UICONTROL CRXDE Lite]**, 선택 **[!UICONTROL 도구]** 도구 모음에서 **[!UICONTROL 쿼리]**: **[!UICONTROL 쿼리]** 탭.

1. 에서 **[!UICONTROL 쿼리]** 탭, 선택 `XPath` 로서의 **[!UICONTROL 유형]**.

1. **[!UICONTROL 쿼리]** 입력 필드에 다음 문자열을 입력합니다.

   `//element(*, cq:Component)`

1. 클릭 **[!UICONTROL 실행]** 구성 요소가 나열됩니다.
