---
title: 적응형 양식을 만드는 방법
description: 을 사용하여 적응형 양식을 만드는 방법 알아보기 [!DNL Experience Manager Forms]. 적응형 Forms은 정보 수집 및 처리를 간소화하는 반응형 HTML 5 양식입니다. 양식 데이터 모델 및 XML 또는 JSON 스키마를 기반으로 적응형 양식을 만드는 방법에 대해 자세히 알아보십시오.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: 4279b4a880429f535cf341d35ac38c9b4dc55ae2
workflow-type: tm+mt
source-wordcount: '1495'
ht-degree: 7%

---

# 적응형 양식 만들기(핵심 구성 요소) {#creating-an-adaptive-form-core-components}

적응형 Forms을 사용하면 매력적인 반응형, 동적 및 적응형 양식을 만들 수 있습니다. AEM Forms은 적응형 Forms을 신속하게 만들 수 있는 비즈니스 사용자 친화적 마법사를 제공합니다. 마법사에는 미리 구성된 템플릿, 스타일, 필드 및 제출 옵션을 손쉽게 선택하여 적응형 양식을 만들 수 있는 빠른 탭 탐색 기능이 있습니다.

시작하기 전에 사용 가능한 Forms 구성 요소 유형에 대해 알아보십시오.

* [적응형 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko): 표준화된 데이터 캡처 구성 요소입니다. 이러한 구성 요소는 사용자 지정 기능, 개발 시간 단축 및 디지털 등록 환경에 대한 유지 관리 비용 절감을 제공합니다. 개발자는 이러한 구성 요소를 손쉽게 맞춤화하고 스타일을 지정할 수 있습니다. Adobe은 이러한 현대적이고 확장 가능한 구성 요소를 활용하여 적응형 Forms을 개발할 것을 권장합니다.

* [적응형 Forms Foundation 구성 요소](creating-adaptive-form.md): 클래식(이전) 데이터 캡처 구성 요소입니다. 적응형 양식 기반의 기존 기초 구성 요소를 편집하는 데 계속 사용할 수 있습니다. Adobe 새 양식을 만드는 경우 다음을 사용하는 것이 좋습니다.  [적응형 Forms 핵심 구성 요소](creating-adaptive-form-core-components.md) 를 클릭하여 적응형 Forms을 만듭니다.

![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)


## 전제 조건

적응형 양식을 만들려면 다음 항목이 필요합니다.

* **환경에 맞는 적응형 Forms 핵심 구성 요소 활성화**: 새 프로그램을 만들 때 환경에 대한 적응형 Forms 핵심 구성 요소가 이미 활성화되었습니다. Archetype 39 또는 이전 버전을 기반으로 하는 Forms as a Cloud Service 환경을 이용하는 경우, [해당 환경에 대해 적응형 양식 핵심 구성 요소를 활성화](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project)하십시오. 환경에 대해 핵심 구성 요소를 활성화하면 **적응형 양식 (핵심 구성 요소)** 템플릿 및 캔버스 테마가 해당 환경에 추가됩니다. 적응형 양식 핵심 구성 요소는 2023.02.0 릴리스 이전의 프리릴리스 일부로 제공되었으므로 사용 중인 AEM SDK 버전이 2023.02.0 이전 버전이라면 [해당 환경에서 `prerelease` 플래그가 활성화](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)되어 있어야 합니다.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 여기에는 특정 속성 및 콘텐츠 구조를 포함하는 미리 형식이 지정된 구성 요소가 있습니다. 또한 테마 및 제출 액션을 정의하는 옵션을 제공합니다. 테마는 모양과 느낌을 정의하고 제출 작업은 적응형 양식 제출 시 수행할 작업을 정의합니다. (예: 수집된 데이터를 데이터 소스로 전송) 클라우드 서비스는 비어 있는 OOTB 템플릿을 제공합니다.

   * 다음 `blank` 템플릿은 모든 최신 AEM Forms as a Cloud Service 프로그램에 포함됩니다.
   * 패키지 관리자를 통해 참조 패키지를 설치하여 `blank` AEM Forms as a Cloud Service 프로그램에 대한 템플릿입니다.
   * 다음을 수행할 수도 있습니다. [새 적응형 Forms 템플릿(핵심 구성 요소) 만들기](template-editor.md) 처음부터.

* **적응형 양식 테마**: 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소에 반영됩니다.  다음 `Canvas` 템플릿은 모든 최신 AEM Forms as a Cloud Service 프로그램에 포함됩니다.

   <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **권한**: 사용자 추가 [!DNL forms-users] 그룹입니다. 의 멤버 [!DNL forms-users] 그룹은 적응형 양식을 만들 수 있는 권한이 있습니다. 양식별 사용자 그룹의 자세한 목록은 다음을 참조하십시오. [그룹 및 권한](forms-groups-privileges-tasks.md).


## 적응형 양식 만들기(핵심 구성 요소) {#create-an-adaptive-form-core-components}

1. 에 로그인 [!DNL Experience Manager Forms] 작성자 인스턴스. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에 자격 증명을 입력합니다. 로그인 후 왼쪽 상단 모서리에서 을 누릅니다 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

1. 누르기 **[!UICONTROL 만들기]**  > **[!UICONTROL 적응형 Forms]**. 마법사가 열립니다. 소스 탭에서 템플릿을 선택합니다.

   ![핵심 구성 요소 템플릿](/help/forms/assets/core-components-template.png)

   템플릿을 선택하면 템플릿에 지정된 테마 및 제출 액션이 자동으로 선택되고 **[!UICONTROL 만들기]** 버튼이 활성화되었습니다. 다음 페이지로 이동할 수 있습니다. **[!UICONTROL 스타일]** 또는 **[!UICONTROL 제출]** 탭을 사용하여 다른 테마를 선택하거나 작업을 제출할 수 있습니다. 선택한 템플릿에서 테마를 지정하지 않으면 만들기 버튼이 비활성화됩니다. 다음 페이지로 이동할 수 있습니다. **[!UICONTROL 스타일]** 탭을 사용하여 테마를 수동으로 선택할 수 있습니다.

   >[!NOTE]
   >
   >
   > 없으시면, **적응형 Forms(핵심 구성 요소)** 사용자 환경의 템플릿, [환경에 맞는 적응형 Forms 핵심 구성 요소 활성화](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). 환경에 대한 핵심 구성 요소 활성화 시 **적응형 Forms(핵심 구성 요소)** 템플릿이 환경에 추가됩니다.

1. 다음에서 **[!UICONTROL 스타일]** 탭에서 테마를 선택합니다.

   * 선택한 템플릿에서 테마를 지정하면 마법사에서 테마가 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.

   * 선택한 템플릿에서 테마를 지정하지 않은 경우 스타일 탭을 사용하여 테마를 선택할 수 있습니다. 다음 **[!UICONTROL 만들기]** 테마를 선택한 후에만 버튼이 활성화됩니다.

1. (선택 사항) 데이터 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: A [양식 데이터 모델](data-integration.md) 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식에 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서 데이터를 가져와 작성하는 작업이 포함된 경우 양식 데이터 모델 을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md) 핵심 구성 요소 기반 적응형 양식을 통해 생성 또는 소비되는 데이터 구조를 나타내는 JSON 스키마를 연결할 수 있으므로 조직의 백엔드 시스템과 원활하게 통합할 수 있습니다. 이 연결을 통해 작성자는 스키마의 요소를 사용하여 적응형 양식에 콘텐츠를 동적으로 추가할 수 있습니다. 작성 프로세스 중에 컨텐츠 브라우저의 데이터 모델 개체 탭에서 스키마 요소에 쉽게 액세스할 수 있으며, 모든 필드는 새로 만든 적응형 양식에 자동으로 추가됩니다.

   기본적으로 연결된 JSON 스키마의 모든 필드가 자동으로 선택되고 해당 적응형 양식 구성 요소로 변환되어 작성 프로세스가 간소화됩니다. 마법사는 확인란을 사용하여 적응형 양식에 포함할 필드를 선택적으로 선택할 수 있는 편리성을 제공합니다.

1. 다음에서 **[!UICONTROL 제출]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 작업이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. 다음 **[!UICONTROL 제출]** 탭에는 사용 가능한 모든 제출 작업이 표시됩니다.

   * 선택한 템플릿에서 제출 액션을 지정하지 않은 경우 **[!UICONTROL 제출]** 제출 액션을 선택할 수 있는 탭

1. (선택 사항) **[!UICONTROL 게재]** 탭에서 적응형 양식의 게시 또는 게시 취소 날짜를 지정할 수 있습니다.

1. 누르기 **[!UICONTROL 만들기]**. 적응형 양식을 저장할 제목, 이름 및 위치를 지정하는 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]** 양식의 표시 이름을 지정합니다. 제목을 통해 다음에서 양식을 식별할 수 있습니다. [!DNL Experience Manager Forms] 사용자 인터페이스.
   * **[!UICONTROL 이름:]** 양식 이름을 지정합니다. 지정된 이름의 노드가 저장소에 생성됩니다. 제목 입력을 시작하면 이름 필드에 대한 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자, 하이픈 및 밑줄만 포함할 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 다음 위치에서 적응형 양식을 직접 저장할 수 있습니다. `/content/dam/formsanddocuments` 또는 다음과 같은 폴더를 생성합니다. `/content/dam/formsanddocuments/adaptiveforms` 을 클릭하여 적응형 양식을 저장하십시오. 경로에서 폴더를 사용하기 전에 폴더를 만들어야 합니다. 다음 **[!UICONTROL 경로]** 필드는 폴더를 자동으로 만들지 않습니다.

1. 누르기 **[!UICONTROL 만들기]**. 적응형 양식이 만들어지고 적응형 Forms 편집기에서 열립니다. 템플릿에서 사용할 수 있는 콘텐츠가 편집기에 표시됩니다.  적응형 양식 유형에 따라 연관된 양식 요소에 있는 양식 요소 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델은 **[!UICONTROL 데이터 모델 개체]** 의 탭 **[!UICONTROL 컨텐츠 브라우저]** 를 클릭합니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

이제 적응형 Forms 핵심 구성 요소를 적응형 Forms 컨테이너로 드래그 앤 드롭하여 양식을 디자인하고 만들 수 있습니다.

## 사용 가능한 적응형 Forms 핵심 구성 요소

적응형 Forms 핵심 구성 요소는 표준화된 데이터 캡처 구성 요소입니다. 이러한 구성 요소는 사용자 지정 기능을 제공하고, 개발 시간을 줄이고, 디지털 등록 경험에 대한 유지 관리 비용을 절감하는 데 도움이 됩니다. [적응형 Forms 핵심 구성 요소 설명서](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko) 에는 사용 가능한 구성 요소 목록과 함께 각 구성 요소의 기능에 대한 자세한 정보가 포함되어 있습니다. 다음을 방문하실 수도 있습니다. [https://aemcomponents.dev/](https://aemcomponents.dev/) 사용 가능한 핵심 구성 요소 보기

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

1. 적응형 양식을 선택하고 을 누릅니다 ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 속성 열기]**. 양식 속성 페이지가 열립니다.

1. 로 이동 **[!UICONTROL 양식 모델]** 을(를) 탭하고 양식 모델을 선택합니다. 적응형 양식에 양식 모델이 없는 경우 JSON 스키마 또는 양식 데이터 모델을 선택할 수 있습니다. 반면에 적응형 양식이 이미 양식 모델을 기반으로 하는 경우 동일한 유형의 다른 양식 모델로 전환할 수 있는 옵션이 있습니다. 예를 들어 양식이 JSON 스키마를 사용하는 경우 다른 JSON 스키마로 쉽게 전환할 수 있으며, 마찬가지로 양식이 양식 데이터 모델을 사용하는 경우 다른 양식 데이터 모델로 전환할 수 있습니다.

1. 누르기 **[!UICONTROL 저장]** 속성을 저장합니다.
