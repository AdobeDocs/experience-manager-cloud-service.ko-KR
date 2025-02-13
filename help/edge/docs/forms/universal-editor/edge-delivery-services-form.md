---
Title: How Edge Delivery Services Forms work?
Description: This article provides information on how Edge Delivery Services Forms work. It also provides information on various form authoring platforms, including the Universal Editor and document-based authoring.
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Working of Edge Delivery Services Forms, How Edge Delivery Services Forms work?
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
exl-id: db58ce85-139a-4cc1-8e18-73da76357299
source-git-commit: 320ab86bc73e874705d985b927e90eec3cad1cf9
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 57%

---


# Edge Delivery Services Forms

Adobe Edge Delivery Services Forms은 양식의 작성, 실행 및 처리 방식을 변환합니다. 조직은 Edge Delivery Services을 활용하여 빠르고 안전하며 가용성이 높은 디지털 양식을 제작할 수 있으므로 빠른 개발 환경으로 사용자 경험과 운영 효율성을 향상시킬 수 있습니다. Edge Delivery Services Forms을 사용하면 전환을 늘리고 비용을 절감하며 컨텐츠 전달을 가속화할 수 있습니다.

## Edge Delivery Services Forms의 이점

* **더 빠른 양식 만들기**: 완벽한 Lighthouse 점수로 고성능 양식을 작성하고 RUM(Real User Monitoring)을 사용하여 실제 성능을 지속적으로 모니터링합니다.

* **작성 프로세스 간소화**: 여러 소스의 콘텐츠를 쉽게 관리하여 유연성을 높일 수 있습니다. 기본적으로 WYSIWYG과 문서 기반 작성을 모두 사용하여 양식을 만들 수 있으므로 다양한 컨텐츠 형식을 원활하게 통합할 수 있습니다.

* **기술 전문가가 아닌 사용자도 쉽게 사용할 수 있습니다**: Edge Delivery Services을 사용하면 프로그래머가 아닌 사용자가 광범위한 프로그래밍 지식 없이도 양식을 쉽게 관리하고 게시할 수 있습니다.

* **향상된 사용자 환경**: 빠른 로드 시간과 원활한 상호 작용을 보장하여 사용자에게 대기 시간을 최소화하고 직관적인 양식 작성 환경을 제공합니다.

* **서버를 사용하지 않는 실행**: Edge Delivery Services에서 양식 논리의 서버를 사용하지 않는 실행을 사용합니다. 여기에는 다음이 포함됩니다.

   * **클라이언트측 유효성 검사**: 양식 필드 유효성 검사가 클라이언트측에서 수행되므로 왕복 지연이 줄어듭니다.

   * **미리 채우기 및 Personalization**: 원활한 사용자 환경을 위해 양식 데이터 미리 채우기가 클라이언트측에서 처리됩니다.

   * **제출 처리**: 양식 제출이 확인되고 중앙 서버 없이 안전하게 전달됩니다.

## Edge Delivery Services Forms 작동 방식

사용자는 Google 드라이브, SharePoint 또는 범용 편집기(WYSIWYG 작성)와 같은 문서 기반 작성 도구를 사용하여 Edge Delivery Services Forms을 작성하는 동시에 GitHub 저장소에서 사용할 수 있는 기본 스타일, 동작 및 구성 요소를 활용할 수 있습니다. 작성되면 Edge Delivery Services Forms은 Forms 제출 서비스를 사용하여 모든 플랫폼으로 데이터를 전송할 수 있습니다.

![Edge Delivery Services Forms 작동 방식](/help/edge/docs/forms/assets/eds-forms-working.png)

### Edge Delivery Services Forms의 주요 구성 요소

Edge Delivery Services Forms의 주요 구성 요소는 다음과 같습니다.

* **GitHub 저장소**: GitHub 저장소는 Edge Delivery Services Forms을 만드는 데 중요한 역할을 합니다. 양식은 저장소의 기본 스타일 및 기능을 활용하며 사용자가 Edge Delivery Services Forms에 사용자 지정 및 사용자 지정 구성 요소를 추가할 수 있도록 합니다.

* **양식 작성**: Edge Delivery Services Forms에서는 WYSIWYG 및 문서 기반 작성의 두 가지 작성 유형을 지원합니다. 문서 기반 작성을 통해 사용자는 Google Docs 및 Microsoft Office와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다. WYSIWYG 작성을 통해 사용자는 유니버설 편집기를 사용하여 시각적으로 양식을 디자인할 수 있으므로 기술 전문가가 아닌 사용자도 양식을 쉽게 만들고 관리할 수 있습니다. 유니버설 편집기는 직관적인 양식 작성 환경을 제공하며 다양한 양식 기능에 대한 액세스를 제공합니다.

* **Forms 제출 서비스**: Forms 제출 서비스를 사용하면 OneDrive, SharePoint 또는 Google Sheets와 같은 모든 플랫폼에서 양식 제출의 데이터를 저장할 수 있으므로 선호하는 시스템 내에서 양식 데이터에 쉽게 액세스하고 관리할 수 있습니다.

## 양식 작성

Adobe Experience Manager는 양식을 작성할 수 있는 여러 편집기를 지원하고 제공합니다. 다음과 같은 기능을 사용할 수 있습니다.
* [범용 편집기 (WYSIWYG 작성용)](#universal-editor-for-wysiwyg-authoring)
* [Microsoft Excel 또는 Google Sheets (문서 기반 작성이라고도 함)](#microsoft-excel-or-google-sheets-known-as-document-based-authoring)

### 범용 편집기 (WYSIWYG 작성용)

범용 편집기는 WYSIWYG(What-You-See-Is-What-You Get) 기능을 제공하는 다목적 비주얼 편집기로서 직관적인 양식 생성 경험을 지원합니다. 새 양식을 생성할 때 사용자 친화적인 최신 디자인과 편리한 드래그 앤 드롭 인터페이스를 제공하는 범용 편집기를 사용하는 것이 좋습니다.

범용 편집기를 사용하여 양식을 생성하려면 AEM 환경에 제공되는 Edge Delivery Services 템플릿을 사용합니다. 이러한 양식은 Edge Delivery Services GitHub 저장소 구성의 디자인을 상속합니다. [AEM 환경과 Edge Delivery Services GitHub 저장소 간의 연결](/help/edge/docs/forms/publishing-forms.md)이 설정되어 Edge Delivery Services에서 이러한 양식을 게시할 수 있습니다.

범용 편집기를 사용하여 작성하는 자세한 단계는 [범용 편집기를 사용하여 콘텐츠 작성](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring) 문서를 참조하십시오.

### Microsoft Excel 또는 Google Sheets (문서 기반 작성이라고도 함)

Microsoft Excel 또는 Google Sheets 파일에서 문서 기반 작성을 사용하여 양식을 작성하면 Google Sheets, Microsoft Excel, Microsoft SharePoint의 강력한 에코시스템과 API를 활용할 수 있습니다. 이러한 접근 방식은 고급 제출 서비스를 사용하지 않고도 간단한 양식을 생성할 때 특히 유용합니다.

Microsoft Excel 또는 Google Sheets로 양식 만들기를 시작하려면 [AEM Forms 상용구를 사용하여 AEM 프로젝트를 설정하고](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) 로컬 컴퓨터에 해당 GitHub 저장소를 복제합니다. AEM Forms Edge Delivery는 양식 만들기 프로세스를 간소화하여 데이터를 캡처하고 저장하는 적응형 양식 블록이라는 기능을 제공합니다. Edge Delivery Services의 적응형 양식 블록을 사용하여 양식을 만들고 게시하는 방법을 알아보려면 [ 양식 만들기](/help/edge/docs/forms/create-forms.md)를 참조하십시오.

<!--
## Adaptive Forms editors (for Core Components or foundation components based authoring)

You can author forms that are engaging, responsive and dynamic. The Adaptive Form editor provides a user-friendly wizard that allows you to quickly create Adaptive Forms. The form wizard features easy tab navigation, enabling you to select pre-configured templates for foundation or core components, themes, data models, and submission options to create a form efficiently. 

[Authoring forms with Core Components](/help/forms/creating-adaptive-form-core-components.md) allows you to leverage standardized data capture components that can be customized, reducing development time and lowering maintenance costs for digital enrollment experiences. These forms can be published using the Adaptive Forms Block on Edge Delivery Services or through the AEM Publish instance. 

[Authoring forms with Foundation Components](/help/forms/create-an-adaptive-form.md) uses classic data capture components. These forms can only be published using the AEM Publish instance. 

You can also publish forms created using Adaptive Forms Editors on Edge Delivery Services by establishing [connection between your AEM environment and the Edge Delivery Services GitHub repository](/help/edge/docs/forms/publishing-forms.md).


| **Adaptive Forms editors** | Provides a wizard-driven approach to quickly start forms authoring using templates, styling, and predefined fields. | Use these editors to create Core Components based forms or Foundation Components based forms. | These forms can be published on Edge Delivery Services or via AEM Publish instances.  | Use these editors to create Core Components based forms or Foundation Components based forms. Ideal for scenarios involving complex forms, complex workflows, custom actions, or integrations with external systems. |  



## Types of Publishing for Edge Delivery Services Forms

You can publish Edge Delivery Services Forms on one of the following:

* **Edge Delivery Services Form Submission**: Edge Delivery Services Form Submissions ensure that form interactions, including submission and data processing, are handled efficiently and securely. This enables a faster and more reliable user experience, particularly during high traffic periods. By processing form submissions at the edge, Edge Delivery Services minimizes the reliance on a centralized server.

* **AEM Publish instance**: The AEM Forms server offers a publish instance that manages the forms and related assets available to end users.
-->

### 다양한 유형의 양식 작성을 어떻게 선택할 수 있습니까?

다음 표에서 간략히 소개된 각 작성 편집기의 기능 및 사용 사례를 기반으로 사용자 요구 사항과 양식 제출 요구 조건에 따라 올바른 편집기를 선택할 수 있습니다.

| **양식 작성 편집기** | **주요 접근 방식** | **기능** | **게시 방법** | **사용 사례** |
|--------|-----------|-------|-------|------------------------------------------------|
| **문서 기반 작성** | Google Docs와 Microsoft Office와 같은 익숙한 도구를 활용하여 양식을 만듭니다. | 양식은 스프레드시트를 사용하여 디자인되어 Google Sheets 또는 Microsoft Excel 시트에 직접 데이터를 제출할 수 있습니다. </br> </br> 이러한 양식은 더 빠르게 만들어 배포할 수 있습니다. 이러한 양식의 사용자 정의 구성 요소와 스타일을 개발하는 경우 AEM에 대한 사전 정보가 필요하지 않습니다. | 이러한 양식은 Edge Delivery Services에 게시되고 Google Lighthouse 점수가 매우 높습니다. </br> </br> 점수가 높으면 렌더링 속도가 빨라지고 SEO가 더 좋아집니다. | 이러한 양식은 신속한 프로토타이핑이나 고급 제출 서비스를 사용하지 않는 기본 양식에 적합합니다. </br> </br> 해당 양식은 스프레드시트에 데이터를 저장해야 하는 설문 조사, 등록이나 피드백 양식에 매우 적합합니다. 이러한 양식은 Edge Delivery Services에 게시됩니다. |
| **범용 편집기** </br> </br> 새 양식을 만드는 경우 범용 편집기를 사용하여 양식을 만듭니다. | 직관적인 양식을 생성하는 WYSIWYG 인터페이스를 제공합니다. | 양식은 직관적인 드래그 앤 드롭 인터페이스를 사용하여 디자인되었습니다. </br> </br> 이러한 양식은 해당 양식에 구성된 Edge Delivery Services GitHub 저장소의 디자인을 차용합니다. | 이러한 양식은 Edge Delivery Services에 게시되고 Google Lighthouse 점수가 매우 높습니다. </br> </br> 점수가 높으면 렌더링 속도가 빨라지고 SEO가 더 좋아집니다. | 이러한 양식은 Edge Delivery Service 사이트 및 페이지용 양식을 생성하는 경우에 적합합니다. 이러한 양식 시나리오에는 복잡한 양식, 복잡한 워크플로, 사용자 정의 액션 또는 외부 시스템과의 통합이 수반됨 |

>[!NOTE]
>
>
> 이전에는 적응형 양식 편집기에 제공되었던 기능이 범용 편집기에 없는 경우 공식 이메일 주소를 사용하여 mailto:aem-forms-ea@adobe.com로 이메일을 보내 해당 기능을 요청할 수 있습니다.

## 추가 참조

{{see-more-forms-eds}}
