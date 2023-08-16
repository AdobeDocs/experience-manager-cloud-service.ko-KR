---
title: 적응형 양식을 만드는 방법은?
description: 단계별 튜토리얼을 통해 모바일 반응이 좋은 적응형 양식을 만드는 방법에 대해 알아봅니다. 이러한 양식은 여러 디바이스에 매끄럽게 적응하여 원활한 경험을 보장합니다.
keywords: 적응형 양식, 모바일 양식, 반응형 양식, HTML5 양식
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '2780'
ht-degree: 97%

---


# 적응형 양식 만들기 {#creating-an-adaptive-form}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html) |
| AEM as a Cloud Service | 이 문서 |

적응형 양식을 사용하면 멋지고, 반응이 빠르고, 동적이고, 적응력이 뛰어난 양식을 만들 수 있습니다. AEM Forms는 적응형 양식을 신속하게 만들 수 있는 비즈니스 사용자 친화적 마법사를 제공합니다. 마법사에는 미리 구성된 템플릿, 스타일, 필드 및 제출 옵션을 손쉽게 선택하여 적응형 양식을 만들 수 있는 빠른 탭 탐색 기능이 있습니다.

![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png){width="100%" align="center"}

시작하기 전에 사용할 수 있는 Forms 구성 요소 유형에 대해 알아봅니다.

* [적응형 양식 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko): 표준화된 데이터 캡처 구성 요소입니다. 이 구성 요소는 맞춤화 기능을 제공하고, 개발 시간을 단축하고, 유지 관리 비용을 줄여 디지털 등록 경험을 개선합니다. 개발자는 이러한 구성 요소를 손쉽게 사용자 정의하고 스타일링할 수 있습니다. [https://aemcomponents.dev/](https://aemcomponents.dev/)에 방문하여 작동 중인 사용 가능한 핵심 구성 요소를 확인할 수 있습니다.**이 확장 가능한 최신 구성 요소를 사용하여 적응형 양식을 개발하는 것이 좋습니다**.

* [적응형 양식 기초 구성 요소](creating-adaptive-form.md): 클래식(이전) 데이터 캡처 구성 요소입니다. 이를 계속 사용하여 기존의 기초 구성 요소 기반 적응형 양식을 편집할 수 있습니다. 새 양식을 만드는 경우 [적응형 양식을 만드는 적응형 양식 핵심 구성 요소](#create-an-adaptive-form-core-components)를 사용하는 것이 좋습니다.

>[!BEGINTABS]

>[!TAB 핵심 구성 요소로 적응형 양식 만들기(권장)]

적응형 양식을 만들려면 다음이 필요합니다.

* **해당 환경에 대해 적응형 양식 핵심 구성 요소를 활성화**: 프로그램을 새로 만들 때 적응형 양식 핵심 구성 요소가 이미 환경에 대해 활성화되어 있습니다. Archetype 39 또는 이전 버전을 기반으로 하는 Forms as a Cloud Service 환경을 이용하는 경우, [해당 환경에 대해 적응형 양식 핵심 구성 요소를 활성화](enable-adaptive-forms-core-components.md)하십시오. 환경에 대해 핵심 구성 요소를 활성화하면 **적응형 양식 (핵심 구성 요소)** 템플릿 및 캔버스 테마가 해당 환경에 추가됩니다. 적응형 양식 핵심 구성 요소는 2023.02.0 릴리스 이전의 프리릴리스 일부로 제공되었으므로 사용 중인 AEM SDK 버전이 2023.02.0 이전 버전이라면 [해당 환경에서 `prerelease` 플래그가 활성화](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)되어 있어야 합니다.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 특정 속성과 콘텐츠 구조를 포함하는 서식이 미리 지정된 구성 요소가 있습니다. 또한 테마와 제출 액션을 정의하는 옵션이 제공됩니다. 테마는 모양과 느낌을 정의하고 제출 액션은 적응형 양식 제출 시 수행할 작업을 정의합니다. 예: 수집된 데이터를 데이터 소스로 보내기. 클라우드 서비스는 blank라는 OOTB 템플릿을 제공합니다.

   * `blank` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다.
   * 패키지 관리자를 통해 참조 패키지를 설치하여 `blank` 템플릿을 AEM Forms as a Cloud Service 프로그램에 추가할 수 있습니다.
   * 처음부터 [새 적응형 양식 템플릿(핵심 구성 요소)](template-editor.md)을 만들 수도 있습니다.

* **적응형 양식 테마**: 테마에 구성 요소 및 패널에 대한 스타일링 세부 정보가 포함됩니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬과 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일은 해당 구성 요소에 반영됩니다.  `Canvas` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다.
  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **권한**: 사용자를 [!DNL forms-users] 그룹에 추가합니다. [!DNL forms-users] 그룹의 멤버는 적응형 양식을 만들 수 있는 권한이 있습니다. 양식별 사용자 그룹에 대한 세부 목록은 [그룹 및 권한](forms-groups-privileges-tasks.md)을 참조하십시오.


## 적응형 양식 만들기 {#create-an-adaptive-form-core-components}

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인한 후 왼쪽 상단에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 탭합니다.

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 탭합니다. 마법사가 열립니다. 소스 탭에서 템플릿을 선택합니다.

   ![핵심 구성 요소 템플릿](/help/forms/assets/core-components-template.png){width="100%" align="center"}

   템플릿을 선택하면 템플릿에 지정된 테마와 제출 액션이 자동으로 선택되고 **[!UICONTROL 만들기]** 버튼이 활성화됩니다. **[!UICONTROL 스타일]** 또는 **[!UICONTROL 제출]** 탭으로 이동하여 다른 테마를 선택하거나 액션을 제출할 수 있습니다. 선택한 템플릿이 테마를 지정하지 않으면 만들기 버튼은 비활성화된 상태로 유지됩니다. **[!UICONTROL 스타일]** 탭으로 이동하여 테마를 수동으로 선택할 수 있습니다.

   >[!NOTE]
   >
   >
   > 환경에 대해 **적응형 양식(핵심 구성 요소)** 템플릿이 없다면 [해당 환경에 대해 적응형 양식 핵심 구성 요소를 활성화합니다](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). 환경에 대해 핵심 구성 요소를 활성화하면 **적응형 양식(핵심 구성 요소)** 템플릿이 해당 환경에 추가됩니다.

1. **[!UICONTROL 스타일]** 탭에서 테마를 선택합니다.

   * 선택한 템플릿이 테마를 지정하면 테마가 마법사에서 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.

   * 선택한 템플릿이 테마를 지정하지 않으면 스타일 탭을 사용하여 테마를 선택할 수 있습니다. **[!UICONTROL 만들기]** 버튼은 테마가 선택된 후에만 활성화됩니다.

1. (선택 사항) 데이터 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: [양식 데이터 모델](data-integration.md)을 통해 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식으로 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서의 데이터 가져오기 및 쓰기 작업이 포함된 경우 양식 데이터 모델을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md) 핵심 구성 요소 기반의 적응형 양식을 통해 생성 또는 사용 중인 데이터의 구조를 나타내는 JSON 스키마를 연결함으로써 조직의 백엔드 시스템과 원활하게 통합할 수 있습니다. 이 연결을 통해 작성자는 스키마 요소를 사용하여 콘텐츠를 적응형 양식에 동적으로 추가할 수 있습니다. 작성 프로세스 중에 컨텐츠 브라우저의 데이터 모델 개체 탭에서 스키마 요소에 쉽게 액세스할 수 있으며, 모든 필드가 새로 만든 적응형 양식에 자동으로 추가됩니다.

   기본적으로 연결된 JSON 스키마의 모든 필드는 자동으로 선택되고 해당 적응형 구성 요소로 변환되어 작성 프로세스를 간소화합니다. 편리성을 추가하기 위해 마법사는 확인란을 통해 적응형 양식에 포함되어야 하는 필드를 선택할 수 있습니다.

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 액션이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에 사용 가능한 모든 제출 액션이 표시됩니다.

   * 선택한 템플릿이 제출 액션을 지정하지 않은 경우 **[!UICONTROL 제출]** 탭을 사용하여 제출 액션을 선택할 수 있습니다.

1. (선택사항) **[!UICONTROL 게재]** 탭에서 적응형 양식의 게시 또는 게시 취소 일자를 지정할 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 제목, 이름과 위치를 지정하여 적응형 양식을 저장할 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]**&#x200B;은 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스에서 형식을 식별하는 데 도움이 됩니다.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 이름이 지정된 노드가 저장소에서 만들어집니다. 제목 입력이 시작되면 이름 필드 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자 문자, 하이픈 및 밑줄만 포함될 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 적응형 양식을 `/content/dam/formsanddocuments`에서 바로 저장하거나 `/content/dam/formsanddocuments/adaptiveforms`와 같은 폴더를 만들어 적응형 양식을 저장할 수 있습니다. 경로에서 사용하기 전에 폴더를 만들어야 합니다. **[!UICONTROL 경로]** 필드는 폴더를 자동으로 만들지 않습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 편집기에 템플릿에서 사용 가능한 콘텐츠가 표시됩니다.  적응형 양식 유형에 따라 연결된 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델에 존재하는 양식 요소가 사이드바에 있는 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;의 **[!UICONTROL 데이터 모델 오브젝트]** 탭에 표시됩니다.

이제 [적응형 양식 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko#components) 또는 스키마 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수 있습니다.


## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model-core-components-based-adaptive-forms}

1. 적응형 양식을 선택하고 ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 속성 열기]**&#x200B;를 탭합니다. 양식 속성 페이지가 열립니다.

1. **[!UICONTROL 양식 모델]** 탭으로 이동하고 양식 모델을 선택합니다. 적응형 양식에 양식 모델이 없는 경우 JSON 스키마 또는 양식 데이터 모델 중 하나를 자유롭게 선택할 수 있습니다. 반면에 적응형 양식이 이미 양식 모델을 기반으로 하는 경우 같은 유형의 다른 양식 모델로 전환할 수 있는 옵션이 있습니다. 예를 들어 양식이 JSON 스키마를 사용하는 경우 다른 JSON 스키마로 쉽게 전환할 수 있고, 마찬가지로 양식이 양식 데이터 모델을 사용하는 경우 다른 양식 데이터 모델로 전환할 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 탭하여 변경 내용을 저장합니다.

>[!TAB 기초 구성 요소로 적응형 양식 만들기]

적응형 양식을 만들려면 다음이 필요합니다.

* **권한**: 사용자를 [!DNL forms-users]에 추가하여 적응형 양식을 만들 수 있는 권한을 제공합니다. 양식별 사용자 그룹에 대한 세부 목록은 [그룹 및 권한](forms-groups-privileges-tasks.md)을 참조하십시오.

* **적응형 양식 테마**: 테마에 구성 요소 및 패널에 대한 스타일링 세부 정보가 포함됩니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬과 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일은 해당 구성 요소에 반영됩니다. [테마를 새로 만들거나](themes.md) [기존 테마를 가져올 수 있습니다](import-export-forms-templates.md#uploading-a-theme). 일부 샘플 테마에 [최신 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html#create-project)을 배포할 수도 있습니다.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 특정 속성과 콘텐츠 구조를 포함하는 서식이 미리 지정된 구성 요소가 있습니다. 또한 테마와 제출 액션을 정의하는 옵션이 제공됩니다. 테마는 모양과 느낌을 정의하고 제출 액션은 적응형 양식 제출 시 수행할 작업을 정의합니다. 예: 수집된 데이터를 데이터 소스로 보내기. 클라우드 서비스는 두 가지 유형의 템플릿을 지원합니다.

   * **편집 가능한 템플릿**: [템플릿을 새로 만들거나](template-editor.md) [편집 가능한 기존 템플릿을 가져올 수 있습니다](migrate-to-forms-as-a-cloud-service.md). 또한 [최신 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=ko#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.)을 배포하여 일부 편집 가능한 샘플 템플릿을 가져올 수 있습니다.

   * **정적 템플릿**: 레거시 템플릿으로서 Adobe Managed Services(AMS) 및 온프레미스 AEM Forms 설치(AEM 6.5 Forms 이하)에서 마이그레이션하는 고객에게만 권장됩니다. 이를 통해 정적 템플릿에 대한 기존의 투자를 계속 이용할 수 있습니다. 적응형 양식을 새로 만들 때 편집 가능한 템플릿을 사용하는 것이 좋습니다.


## 적응형 양식 만들기 {#create-an-adaptive-form-foundation-components}

1. [!DNL Experience Manager Forms] 작성자 인스턴스 액세스. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다.

   로그인한 후 왼쪽 상단에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 탭합니다.

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 탭합니다. 마법사가 열립니다.
1. 소스 탭에서 템플릿을 선택합니다.

   * 편집 가능한 템플릿을 선택하면 템플릿에 지정된 테마와 제출 액션이 자동으로 선택되고 **[!UICONTROL 만들기]** 버튼이 활성화됩니다. **[!UICONTROL 스타일]** 또는 **[!UICONTROL 제출]** 탭으로 이동하여 다른 테마를 선택하거나 액션을 제출할 수 있습니다. 선택한 편집 가능한 템플릿이 테마를 지정하지 않으면 만들기 버튼은 비활성화된 상태로 유지됩니다. **[!UICONTROL 스타일]** 탭으로 이동하여 테마를 수동으로 선택할 수 있습니다.

     >[!NOTE]
     >
     > 또한 적응형 양식 편집기를 사용하여 [!UICONTROL 기록 문서] 템플릿을 만들 수 있습니다. 자세한 내용은 [ 적응형 양식 편집기에서 기록 문서 지원](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)을 참조하십시오.

   * 정적 템플릿을 선택하면 데이터, 스타일, 제출, 게재 및 미리보기 옵션은 사용할 수 없습니다. 적응형 양식을 새로 만들 때 편집 가능한 템플릿을 사용하는 것이 좋습니다.

1. **[!UICONTROL 스타일]** 탭에서 테마를 선택합니다.

   * 선택한 템플릿이 테마를 지정하면 테마가 마법사에서 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.
   * 선택한 템플릿이 테마를 지정하지 않으면 스타일 탭을 사용하여 테마를 선택할 수 있습니다. **[!UICONTROL 만들기]** 버튼은 테마가 선택된 후에만 활성화됩니다.

1. (선택 사항) **[!UICONTROL 데이터]** 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: [양식 데이터 모델](data-integration.md)을 통해 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식으로 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서의 데이터 가져오기 및 쓰기 작업이 포함된 경우 양식 데이터 모델을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md)는 조직의 백엔드 시스템에서 데이터를 생성 또는 사용하는 구조를 나타냅니다. 스키마를 적응형 양식에 연결하고 해당 요소를 사용하여 동적 콘텐츠를 적응형 양식에 추가할 수 있습니다. 적응형 Forms을 작성할 때 콘텐츠 브라우저의 데이터 모델 개체 탭에서 스키마 요소를 사용할 수 있으며 모든 필드는 새로 만든 적응형 양식에도 추가됩니다.

   기본적으로 데이터 모델의 모든 필드가 선택됩니다. 적응형 양식을 만들 때 선택한 모든 데이터 모델 필드가 해당되는 적응형 양식 구성 요소로 변환됩니다. 마법사는 적응형 양식에 포함되어야 하는 해당 필드만 선택할 수 있는 확인란을 제공합니다.

   <!-- 
   
   If your JSON schema contains a fragment, the fragment is considered a single unit. You can select or deselect a complete fragment and all the fields of the fragment are selected or deselected accordingly. 
   
   -->

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 액션이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에 사용 가능한 모든 제출 액션이 표시됩니다.

   * 선택한 템플릿이 제출 액션을 지정하지 않은 경우 **[!UICONTROL 제출]** 탭을 사용하여 제출 액션을 선택할 수 있습니다.

1. (선택사항) 게재 탭에서 적응형 양식의 게시 또는 게시 취소 일자를 지정할 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 제목, 이름과 위치를 지정하여 적응형 양식을 저장할 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]**&#x200B;은 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스에서 형식을 식별하는 데 도움이 됩니다.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 이름이 지정된 노드가 저장소에서 만들어집니다. 제목 입력이 시작되면 이름 필드 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자 문자, 하이픈 및 밑줄만 포함될 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 적응형 양식을 `/content/dam/formsanddocuments`에서 바로 저장하거나 `/content/dam/formsanddocuments/adaptiveforms`와 같은 폴더를 만들어 적응형 양식을 저장할 수 있습니다. 경로에서 사용하기 전에 폴더를 만들어야 합니다. **[!UICONTROL 경로:]** 필드는 폴더를 자동으로 만들지 않습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다. 적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 편집기에 템플릿에서 사용 가능한 콘텐츠가 표시됩니다. 또한 필요에 따라 새로 만든 양식을 사용자 지정할 수 있는 사이드바가 표시됩니다.

   적응형 양식 유형에 따라 연결된 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델에 존재하는 양식 요소가 사이드바에 있는 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;의 **[!UICONTROL 데이터 모델 오브젝트]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

<!-- ## Create an Adaptive Form based on a Form Data Model {#fdm}

[Data integration](data-integration.md) lets you integrate multiple data sources and bring their entities and services together to create a form data model. It is an extension of JSON schema. You can use a Form Data Model to create an Adaptive Form. The entities or data model objects configured in a Form Data Model are available as data model objects for form authoring. They are bound to respective data sources and used to prefill a form and write submitted data back to the respective data sources. You can also call services configured in a Form Data Model using Adaptive Form rules.

To use a Form Data Model for creating an Adaptive Form:

1. In Form Model tab on Add Properties screen, select **[!UICONTROL Form Data Model]** in the **[!UICONTROL Select From]** drop-down list.

   ![Create an Adaptive Form](assets/create-af-1-1.png)

1. Tap to expand **[!UICONTROL Select Form Data Model]**. All available form data models are listed.Select a from data model.

>[!NOTE]
>
>You can also change the Form Data Model for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model).

## Create an Adaptive Form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate a schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available in the Data Model Object tab of the content browser for authoring Adaptive Forms. You can drag-drop the schema elements to build the form.

See the following documents to understand how to design XML or JSON schema for authoring Adaptive Forms.

* [Creating Adaptive Forms using XML schema](adaptive-form-xml-schema-form-model.md)
* [Creating Adaptive Forms using JSON schema](adaptive-form-json-schema-form-model.md)

Do the following to use XML or JSON schema as form model for an Adaptive Form:

1. On the **[!UICONTROL Add Properties]** step of Adaptive Form creation page, tap on the **[!UICONTROL Form Model]** tab.
1. In the Form Model tab, select **[!UICONTROL Schema]** from the **[!UICONTROL Select From]** drop-down field.

1. Tap **[!UICONTROL Select Schema]** and do one of the following:

    * **[!UICONTROL Upload from disk]** - Select this option and tap Upload Schema Definition to browse and upload an XML schema or JSON schema from your file system. The uploaded schema file resides with the form and is not accessible to other Adaptive Forms.
    * **[!UICONTROL Search in repository]** - Select this option to select from the list of schema definition files available in the repository. Select the XML or JSON schema file as form model. The selected schema is associated with the form by reference and is accessible for use in other Adaptive Forms.

      Ensure that the JSON schema filename ends with **.schema.json**. For example: mySchema.schema.json

   ![Selecting XML or JSON schema](assets/upload-schema.png)
**Figure:** *Selecting XML or JSON schema*

1. (For XML schema only) After you select or upload an XML Schema, specify a root element of the selected XSD file to map with the Adaptive Form.

   ![Selecting XSD root element](assets/xsd-root-element.png)
**Figure:** *Selecting XSD root element*

>[!NOTE]
>
>You can also change the schema for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model2). -->

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model-foundation-components}

적응형 양식(JSON 기반 또는 양식 데이터 모델)의 양식 모델을 변경할 수 있습니다. 한 양식 모델에서 다른 양식 모델로 변경할 수 없습니다.

1. 적응형 양식을 선택하고 **속성** 아이콘을 탭합니다.
1. **[!UICONTROL 양식 모델]** 탭을 열고 다음 중 하나를 수행합니다.

   * 적응형 양식에 양식 모델이 없는 경우 다른 양식 모델을 선택하고 그에 따라 <!-- a form template, --> XML 내지 JSON 스키마 또는 양식 데이터 모델을 선택할 수 있습니다.
   * 적응형 양식이 양식 모델을 기반으로 하는 경우 다른 <!-- form template, --> XML 내지 JSON 스키마 또는 동일한 양식 모델에 대한 양식 데이터 모델을 선택할 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 탭하여 변경 내용을 저장합니다.

적응형 양식 편집기나 적응형 양식 템플릿 편집기에서 양식 모델 속성을 수정할 수도 있습니다.

1. **[!UICONTROL 적응형 양식 컨테이너(루트)]** 구성 요소를 선택합니다.
1. ![아이콘 구성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭하여 적응형 양식 컨테이너의 **[!UICONTROL 속성]**&#x200B;을 엽니다.
1. **[!UICONTROL 데이터 모델]** 탭을 선택하고 다음 중 하나를 수행합니다.

   * 적응형 양식에 양식 모델이 없는 경우 양식 모델을 선택하고 그에 따라 <!-- a form template, --> XML 내지 JSON 스키마 또는 양식 데이터 모델을 선택할 수 있습니다.
   * 적응형 양식이 양식 모델을 기반으로 하는 경우 양식 모델을 변경할 수 없습니다. 다른 <!-- form template, --> XML 내지 JSON 스키마 또는 (해당되는 경우) 동일한 양식 모델에 대한 양식 데이터 모델을 선택할 수 있습니다.
1. ![저장](/help/forms/assets/check-button.png)을 탭하여 변경 내용을 저장합니다.

![FDM 스키마 지원](/help/forms/assets/fdmsupport.png){width="100%" align="center"}

>[!NOTE]
>
> 또한 적응형 양식을 템플릿으로 저장할 수 있습니다. 자세한 내용은 [ 적응형 양식을 사용하여 템플릿 만들기](/help/forms/template-editor.md#saving-an-adaptive-form-as-template-saving-adaptive-form-as-template)를 참조하십시오.

>[!ENDTABS]


## 다음 단계

* [Forms와 함께 Adobe Sign 사용](working-with-adobe-sign.md)
* [Forms와 함께 Google reCaptcha 사용](captcha-adaptive-forms.md)
* [양식에 반복 가능한 섹션 추가](create-forms-repeatable-sections.md)
* [양식 필드 미리 채우기](prepopulate-adaptive-form-fields.md)

>[!MORELIKETHIS]
>
>* [AEM Sites 페이지 또는 경험 조각에서 적응형 양식 만들기](create-or-add-an-adaptive-form-to-aem-sites-page.md)
>* [사용자 정의 적응형 양식 테마 만들기](using-themes-in-core-components.md)
>* [양식의 제출 액션 구성](configuring-submit-actions.md)
>* [사용 가능한 적응형 양식 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#components)
