---
Title: Authoring a Form
Description: This article provides information on various form authoring platforms, including the Universal Editor, document-based authoring, and Adaptive Forms editors (Core Components and Foundation Components).
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Adaptive Forms editors, Adaptive Forms editors for Core Components authoring, Adaptive Forms editors for Foundation Components authoring
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: ht
source-wordcount: '877'
ht-degree: 100%

---


# 양식 작성

Adobe Experience Manager는 양식을 작성할 수 있는 여러 편집기를 지원하고 제공합니다. 다음과 같은 기능을 사용할 수 있습니다.
* 범용 편집기 (WYSIWYG 작성용)
* Microsoft Excel 또는 Google Sheets (문서 기반 작성이라고도 함)
* 적응형 양식 편집기 (핵심 구성 요소 또는 기초 구성 요소 기반 작성용)

**[추가할 이미지]**

## 범용 편집기 (WYSIWYG 작성용)

범용 편집기는 WYSIWYG(What-You-See-Is-What-You Get) 기능을 제공하는 다목적 비주얼 편집기로서 직관적인 양식 생성 경험을 지원합니다. 새 양식을 생성할 때 사용자 친화적인 최신 디자인과 편리한 드래그 앤 드롭 인터페이스를 제공하는 범용 편집기를 사용하는 것이 좋습니다.

범용 편집기를 사용하여 양식을 생성하려면 AEM 환경에 제공되는 Edge Delivery Services 템플릿을 사용합니다. 이러한 양식은 Edge Delivery Services GitHub 저장소 구성의 디자인을 상속합니다. [AEM 환경과 Edge Delivery Services GitHub 저장소 간의 연결](/help/edge/docs/forms/publishing-forms.md)이 설정되어 Edge Delivery Services에서 이러한 양식을 게시할 수 있습니다.

범용 편집기를 사용하여 작성하는 자세한 단계는 [범용 편집기를 사용하여 콘텐츠 작성](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring) 문서를 참조하십시오.

## Microsoft Excel 또는 Google Sheets (문서 기반 작성이라고도 함)

Microsoft Excel 또는 Google Sheets 파일에서 문서 기반 작성을 사용하여 양식을 작성하면 Google Sheets, Microsoft Excel, Microsoft SharePoint의 강력한 에코시스템과 API를 활용할 수 있습니다. 이러한 접근 방식은 고급 제출 서비스를 사용하지 않고도 간단한 양식을 생성할 때 특히 유용합니다.

Microsoft Excel 또는 Google Sheets로 양식 만들기를 시작하려면 [AEM Forms 상용구를 사용하여 AEM 프로젝트를 설정하고](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) 로컬 컴퓨터에 해당 GitHub 저장소를 복제합니다. AEM Forms Edge Delivery는 양식 만들기 프로세스를 간소화하여 데이터를 캡처하고 저장하는 적응형 양식 블록이라는 기능을 제공합니다. Edge Delivery Services의 적응형 양식 블록을 사용하여 양식을 만들고 게시하는 방법을 알아보려면 [ 양식 만들기](/help/edge/docs/forms/create-forms.md)를 참조하십시오.

## 적응형 양식 편집기 (핵심 구성 요소 또는 기초 구성 요소 기반 작성용)

멋지고, 반응이 빠르고, 동적인 양식을 작성할 수 있습니다. 적응형 양식 편집기는 적응형 양식을 신속하게 만들 수 있는 사용자 친화적인 마법사를 제공합니다. 양식 마법사는 간단한 탭 탐색 기능을 통해서 기초 구성 요소나 핵심 구성 요소, 테마, 데이터 모델 및 제출 옵션용으로 미리 구성된 템플릿을 선택하여 양식을 효율적으로 만들 수 있습니다.

[핵심 구성 요소로 양식 작성](/help/forms/creating-adaptive-form-core-components.md) 사용자 정의할 수 있는 표준화된 데이터 캡처 구성 요소를 활용하여 디지털 등록 경험에 소요되는 개발 시간을 단축하고 유지 관리 비용을 줄일 수 있습니다. 이러한 양식은 Edge Delivery Services의 적응형 양식 블록을 사용하거나 AEM Publish 인스턴스를 통해 게시될 수 있습니다.

[기초 구성 요소를 사용하여 양식 작성](/help/forms/create-an-adaptive-form.md) 클래식 데이터 캡처 구성 요소를 사용합니다. 이러한 양식은 AEM 게시 인스턴스로만 게시될 수 있습니다.

[AEM 환경과 Edge Delivery Services GitHub 저장소 간의 연결](/help/edge/docs/forms/publishing-forms.md)을 설정하여 Edge Delivery Services의 적응형 양식 편집기로 만든 양식을 게시할 수도 있습니다.

## 다양한 유형의 양식 작성을 어떻게 선택할 수 있습니까?

다음 표에서 간략히 소개된 각 작성 편집기의 기능 및 사용 사례를 기반으로 사용자 요구 사항과 양식 제출 요구 조건에 따라 올바른 편집기를 선택할 수 있습니다.

| **양식 작성 편집기** | **주요 접근 방식** | **기능** | **게시 방법** | **사용 사례** |
|--------|-----------|-------|-------|------------------------------------------------|
| **문서 기반 작성** | Google Docs와 Microsoft Office와 같은 익숙한 도구를 활용하여 양식을 만듭니다. | 양식은 스프레드시트를 사용하여 디자인되어 Google Sheets 또는 Microsoft Excel 시트에 직접 데이터를 제출할 수 있습니다. </br> </br> 이러한 양식은 더 빠르게 만들어 배포할 수 있습니다. 이러한 양식의 사용자 정의 구성 요소와 스타일을 개발하는 경우 AEM에 대한 사전 정보가 필요하지 않습니다. | 이러한 양식은 Edge Delivery Services에 게시되고 Google Lighthouse 점수가 매우 높습니다. </br> </br> 점수가 높으면 렌더링 속도가 빨라지고 SEO가 더 좋아집니다. | 이러한 양식은 신속한 프로토타이핑이나 고급 제출 서비스를 사용하지 않는 기본 양식에 적합합니다. </br> </br> 해당 양식은 스프레드시트에 데이터를 저장해야 하는 설문 조사, 등록이나 피드백 양식에 매우 적합합니다. 이러한 양식은 Edge Delivery Services에 게시됩니다. |
| **범용 편집기** </br> </br> 새 양식을 만드는 경우 범용 편집기를 사용하여 양식을 만듭니다. | 직관적인 양식을 생성하는 WYSIWYG 인터페이스를 제공합니다. | 양식은 직관적인 드래그 앤 드롭 인터페이스를 사용하여 디자인되었습니다. </br> </br> 이러한 양식은 해당 양식에 구성된 Edge Delivery Services GitHub 저장소의 디자인을 차용합니다. | 이러한 양식은 Edge Delivery Services에 게시되고 Google Lighthouse 점수가 매우 높습니다. </br> </br> 점수가 높으면 렌더링 속도가 빨라지고 SEO가 더 좋아집니다. | 이러한 양식은 Edge Delivery Service 사이트 및 페이지용 양식을 생성하는 경우에 적합합니다. 이러한 양식 시나리오에는 복잡한 양식, 복잡한 워크플로, 사용자 정의 액션 또는 외부 시스템과의 통합이 수반됨 |
| **적응형 양식 편집기** | 템플릿, 스타일 및 미리 정의된 필드를 사용하여 양식 작성을 빠르게 시작할 수 있는 마법사 기반 접근 방식을 제공합니다. | 이러한 편집기를 사용하여 핵심 구성 요소 기반 양식 또는 기초 구성 요소 기반 양식을 생성할 수 있습니다. | 이러한 양식은 Edge Delivery Services나 AEM 게시 인스턴스를 통해 게시될 수 있습니다. | 이러한 편집기를 사용하여 핵심 구성 요소 기반 양식 또는 기초 구성 요소 기반 양식을 생성할 수 있습니다. 복잡한 양식, 복잡한 워크플로, 사용자 정의 액션 또는 외부 시스템과의 통합을 수반하는 시나리오에 적합합니다. |


>[!NOTE]
>
>
> 이전에는 적응형 양식 편집기에 제공되었던 기능이 범용 편집기에 없는 경우 공식 이메일 주소를 사용하여 mailto:aem-forms-ea@adobe.com로 이메일을 보내 해당 기능을 요청할 수 있습니다.

## 관련 문서

* [Microsoft Excel 또는 Google Sheets를 사용하여 문서 기반 작성](/help/edge/docs/forms/create-forms.md)
* [WYSIWYG 작성용 범용 편집기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [적응형 양식(기초 구성 요소) 만들기](/help/forms/creating-adaptive-form.md)
* [적응형 양식(핵심 구성 요소) 만들기](/help/forms/create-an-adaptive-form.md)

## 추가 참조

{{see-more-forms-eds}}