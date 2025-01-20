---
Title: Authoring a Form
Description: This article provides information on various form authoring platforms, including the Universal Editor, document-based authoring, and Adaptive Forms editors (Core Components and Foundation Components).
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Adaptive Forms editors, Adaptive Forms editors for Core Components authoring, Adaptive Forms editors for Foundation Components authoring
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# 양식 작성

Adobe Experience Manager은 양식을 작성할 수 있는 여러 편집기를 제공하고 지원합니다. 다음과 같은 기능을 사용할 수 있습니다.
* 범용 편집기(WYSIWYG 작성용)
* Microsoft Excel 또는 Google Sheets(문서 기반 작성이라고 함)
* 적응형 Forms 편집기(핵심 구성 요소 또는 기초 구성 요소 기반 작성용)

**[추가할 이미지]**

## 범용 편집기(WYSIWYG 작성용)

범용 편집기는 WYSIWYG(보이는 것) 기능을 제공하는 다용도 비주얼 편집기로 직관적인 양식 작성 환경을 제공합니다. 현대적이고 사용자 친화적인 디자인과 편리한 드래그 앤 드롭 인터페이스를 제공하므로 새 양식을 만들 때 유니버설 편집기를 사용하는 것이 좋습니다.

범용 편집기를 사용하여 양식을 만들려면 AEM 환경에서 사용할 수 있는 Edge Delivery Services 템플릿을 사용합니다. 이러한 양식은 Edge Delivery Services GitHub 저장소의 구성에서 모양과 느낌을 상속합니다. [AEM 환경과 Edge Delivery Services GitHub 리포지토리 간의 연결이 설정되어 있습니다](/help/edge/docs/forms/publishing-forms.md) 이러한 양식을 Edge Delivery Services에 게시할 수 있도록 설정합니다.

유니버설 편집기를 사용하여 만드는 방법에 대한 자세한 단계는 [유니버설 편집기로 콘텐츠 작성](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring) 문서를 참조하십시오.

## Microsoft Excel 또는 Google Sheets(문서 기반 작성이라고 함)

Microsoft Excel 또는 Google Sheets 파일로 문서 기반 작성을 사용하여 양식을 작성할 수 있으므로 Google Sheets, Microsoft Excel 및 Microsoft SharePoint의 강력한 에코시스템 및 API를 활용할 수 있습니다. 이 접근 방식은 고급 제출 서비스 없이 간단한 양식을 작성하는 데 특히 유용합니다.

Microsoft Excel 또는 Google Sheets를 사용하여 양식을 만들려면 [AEM Forms Boilerplate를 사용하여 AEM 프로젝트를 설정하고](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)해당 GitHub 리포지토리를 로컬 컴퓨터에 복제하십시오. AEM Forms Edge Delivery은 데이터를 캡처하고 저장하기 위한 양식을 만드는 프로세스를 간소화하는 적응형 Forms 블록이라는 기능을 제공합니다. Edge Delivery Services에서 적응형 Forms 블록을 사용하여 양식을 만들고 게시하는 방법에 대해 알아보려면 [양식 만들기](/help/edge/docs/forms/create-forms.md)를 참조하십시오.

## 적응형 Forms 편집기(핵심 구성 요소 또는 기초 구성 요소 기반 작성용)

매력적인 반응형 동적 양식을 작성할 수 있습니다. 적응형 양식 편집기는 적응형 Forms을 신속하게 만들 수 있는 사용자 친화적 마법사를 제공합니다. 양식 마법사에서는 양식을 효율적으로 만들기 위해 기초 또는 핵심 구성 요소, 테마, 데이터 모델 및 제출 옵션에 대해 사전 구성된 템플릿을 선택할 수 있는 간편한 탭 탐색 기능을 제공합니다.

[핵심 구성 요소가 포함된 양식 작성](/help/forms/creating-adaptive-form-core-components.md)을 사용하면 사용자 지정할 수 있는 표준화된 데이터 캡처 구성 요소를 활용할 수 있으므로 개발 시간이 단축되고 디지털 등록 환경의 유지 관리 비용이 절감됩니다. 이러한 양식은 Edge Delivery Services에서 적응형 Forms 블록을 사용하거나 AEM Publish 인스턴스를 통해 게시할 수 있습니다.

[기본 구성 요소를 사용하여 양식 작성](/help/forms/create-an-adaptive-form.md)에서 클래식 데이터 캡처 구성 요소를 사용합니다. 이러한 양식은 AEM Publish 인스턴스를 사용해야만 게시할 수 있습니다.

AEM 환경과 Edge Delivery Services GitHub 리포지토리 간에 [연결을 설정하여 Edge Delivery Services에 적응형 Forms 편집기를 사용하여 만든 양식을 게시할 수도 있습니다](/help/edge/docs/forms/publishing-forms.md).

## 다양한 양식 작성 유형 중에서 선택하는 방법

다음 표에서는 각 작성 편집기의 기능 및 사용 사례를 간략하게 설명하므로, 요구 사항 및 양식 제출 요구 사항에 따라 적합한 기능을 선택할 수 있습니다.

| **양식 작성 편집기** | **키 접근 방식** | **기능** | **게시 메서드** | **사용 사례** |
|--------|-----------|-------|-------|------------------------------------------------|
| **문서 기반 작성** | 양식 작성을 위해 Google Docs 및 Microsoft Office와 같은 친숙한 도구를 활용합니다. | Forms은 Google Sheets 또는 Microsoft Excel Sheets에 직접 제출된 데이터로 스프레드시트를 사용하여 설계되었습니다. </br> </br> 이러한 양식을 더 빨리 만들고 배포할 수 있습니다. 이러한 양식에 대한 사용자 정의 구성 요소 및 스타일을 개발하기 위해 AEM에 대한 사전 지식이 필요하지 않습니다. | 이러한 양식은 Edge Delivery Services에 게시되며 Google Lighthouse 점수가 매우 높습니다. </br> </br> 점수가 높으면 렌더링 속도가 빨라지고 SEO가 향상됩니다. | 이러한 양식은 고급 제출 서비스가 필요하지 않은 빠른 프로토타이핑 또는 기본 양식에 이상적입니다. </br> </br> 스프레드시트의 데이터 저장이 필요한 설문 조사, 등록 또는 피드백 양식에 적합합니다. 이러한 양식은 Edge Delivery 서비스에 게시됩니다 |
| **유니버설 편집기** </br> </br> 새 양식을 만드는 경우 유니버설 편집기를 사용하여 양식을 만드십시오. | 직관적인 양식 생성을 위한 WYSIWYG 인터페이스를 제공합니다. | Forms은 직관적인 드래그 앤 드롭 인터페이스를 사용하여 설계되었습니다. </br> </br> 이러한 양식은 해당 양식에 대해 구성된 Edge Delivery Services GitHub 리포지토리에서 디자인을 차용합니다. | 이러한 양식은 Edge Delivery Services에 게시되며 Google Lighthouse 점수가 매우 높습니다. </br> </br> 점수가 높으면 렌더링 속도가 빨라지고 SEO가 향상됩니다. | 이러한 양식은 Edge Delivery 서비스 사이트 및 페이지에 대한 양식을 만드는 데 이상적입니다. 복잡한 양식, 복잡한 워크플로우, 사용자 지정 작업 또는 외부 시스템과의 통합이 포함된 이러한 양식 시나리오 |
| **적응형 Forms 편집기** | 템플릿, 스타일 지정 및 사전 정의된 필드를 사용하여 양식 작성을 빠르게 시작하는 마법사 기반 접근 방식을 제공합니다. | 이러한 편집기를 사용하여 핵심 구성 요소 기반 양식 또는 기초 구성 요소 기반 양식을 만듭니다. | 이러한 양식은 Edge Delivery Services에 게시하거나 AEM Publish 인스턴스를 통해 게시할 수 있습니다. | 이러한 편집기를 사용하여 핵심 구성 요소 기반 양식 또는 기초 구성 요소 기반 양식을 만듭니다. 복잡한 양식, 복잡한 워크플로, 사용자 지정 작업 또는 외부 시스템과의 통합과 관련된 시나리오에 이상적입니다. |


>[!NOTE]
>
>
> 이전에 적응형 Forms 편집기에서 사용할 수 있었던 유니버설 편집기에서 누락된 기능이 발견되면 공식 이메일 주소를 사용하여 mailto:aem-forms-ea@adobe.com으로 이메일을 보내 요청할 수 있습니다.

## 관련 문서

* [Microsoft Excel 또는 Google Sheets를 사용하여 문서 기반 작성](/help/edge/docs/forms/create-forms.md)
* [WYSIWYG 작성용 유니버설 편집기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [적응형 양식 만들기(기초 구성 요소)](/help/forms/creating-adaptive-form.md)
* [적응형 양식 만들기(핵심 구성 요소)](/help/forms/create-an-adaptive-form.md)

## 추가 참조

{{see-more-forms-eds}}