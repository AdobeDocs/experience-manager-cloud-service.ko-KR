---
title: 구성 요소 개요
description: 구성 요소는 웹 사이트에 콘텐츠를 표시할 특정 기능을 실현하는 모듈식 단위입니다.
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# 구성 요소 개요 {#components-overview}

이 페이지는 [페이지 작성에 사용되는](/help/sites-cloud/authoring/fundamentals/components.md) 구성 요소와 같은 Adobe Experience Manager(AEM) 구성 요소에 대한 개요를 제공합니다.

## 구성 요소란 무엇입니까? {#what-are-components}

AEM의 구성 요소는

* 웹 사이트에 콘텐츠를 표시할 특정 기능을 실현하는 모듈식 단위입니다.
* 재사용할 수 있습니다.
* 저장소의 한 폴더에 자체 포함되는 단위로 개발했습니다.
* 숨겨진 구성 파일이 없습니다.
* 다른 구성 요소를 포함할 수 있습니다.
* AEM 시스템 내의 어느 곳에나 실행할 수 있고 특정 구성 요소에서의 실행이 제한될 수도 있습니다.
* 표준화된 사용자 인터페이스가 있습니다.
* 구성할 수 있는 편집 비헤이비어가 있습니다.
* Granite UI 구성 요소 기반의 하위 요소를 사용하여 빌드한 대화 상자를 사용합니다.
* [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=ko-KR)을 사용하여 개발되었습니다.
* 기본 기능을 확장하는 사용자 지정된 구성 요소를 만들기 위해 개발할 수 있습니다.

구성 요소가 모듈식이므로 다음과 같은 작업을 수행할 수 있습니다.

* 로컬 인스턴스에서 새 구성 요소를 개발합니다.
* 테스트 환경에 배포합니다.
* 작성자 및/또는 관리자가 콘텐츠를 추가 및 구성할 수 있는 라이브 작성 환경에 배포합니다.
* 웹 사이트 방문자의 콘텐츠를 렌더링하는 데 사용되는 라이브 게시 환경에 배포합니다.

각 AEM 구성 요소:

* 리소스 유형입니다.
* 특정 기능을 완벽하게 실현하는 스크립트 모음입니다.
* AEM 또는 포털과 별개로 작동할 수 있습니다.

## AEM 핵심 구성 요소 {#aem-core-components}

[AEM 핵심 구성 요소는 AEM에서 개발 시간을 가속화고 웹 사이트의 유지 관리 비용을 절감할 수 있는 표준화된 웹 콘텐츠 관리(WCM) 구성 요소입니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR)

AEM as a Cloud Service와 함께 핵심 구성 요소를 제공하고, [WKND 튜토리얼](/help/implementing/developing/introduction/develop-wknd-tutorial.md)은 구성 요소를 구현하고 사용하는 방법을 보여 줍니다. 구성 요소는 모든 소스 코드와 함께 제공되고, 그대로 사용하거나 수정 또는 확장된 구성 요소의 시작점으로 사용할 수 있습니다.

### 사용 가능한 구성 요소 보기 {#viewing-available-components}

AEM 인스턴스에 사용 가능한 모든 구성 요소에 대한 개요를 보려면 [구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md)을 사용하십시오.

또는 CRXDE Lite를 사용하여 저장소에 사용 가능한 모든 구성 요소 목록을 가져올 수도 있습니다.

1. **[!UICONTROL CRXDE Lite]**&#x200B;의 도구 모음에서 **[!UICONTROL 도구]**&#x200B;를 선택한 다음 **[!UICONTROL 쿼리]**&#x200B;를 선택하여 **[!UICONTROL 쿼리]** 탭을 엽니다.

1. **[!UICONTROL 쿼리]** 탭에서 `XPath`를 **[!UICONTROL 유형]**&#x200B;으로 선택합니다.

1. **[!UICONTROL 쿼리]** 입력 필드에 다음 문자열을 입력합니다.

   `//element(*, cq:Component)`

1. **[!UICONTROL 실행]**&#x200B;을 클릭하면 구성 요소가 나열됩니다.
