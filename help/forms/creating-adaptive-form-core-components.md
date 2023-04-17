---
title: 적응형 양식을 만드는 방법
description: 을 사용하여 적응형 양식을 만드는 방법을 알아봅니다 [!DNL Experience Manager Forms]. 적응형 Forms은 정보 수집 및 처리를 간소화하는 반응형 HTML5 양식입니다. 양식 데이터 모델 및 XML 또는 JSON 스키마를 기반으로 적응형 양식을 만드는 방법에 대해 자세히 알아보십시오.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: a4fd268cb143c1356de3db9d55b16ccb58b67d4b
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 2%

---


# 적응형 양식 만들기(핵심 구성 요소) {#creating-an-adaptive-form-core-components}

적응형 양식을 사용하여 멋지고, 반응이 빠르고, 동적이고, 적응력이 뛰어난 양식을 만들 수 있습니다. AEM Forms은 적응형 Forms을 신속하게 만들 수 있는 비즈니스 사용자에게 친숙한 마법사를 제공합니다. 마법사에는 적응형 양식을 만들기 위해 사전 구성된 템플릿, 스타일 지정, 필드 및 제출 옵션을 쉽게 선택할 수 있는 빠른 탭 탐색 기능이 있습니다.

시작하기 전에 사용 가능한 Forms 구성 요소의 유형에 대해 알아봅니다.

* [응용 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko): 표준화된 데이터 캡처 구성 요소입니다. 이러한 구성 요소는 디지털 등록 환경을 위한 사용자 정의 기능, 개발 시간 단축 및 유지 관리 비용을 제공합니다. 개발자는 이러한 구성 요소를 쉽게 사용자 지정하고 스타일을 지정할 수 있습니다. Adobe은 이러한 현대적이고 확장 가능한 구성 요소를 활용하여 적응형 Forms을 개발할 것을 권장합니다.

* [응용 Forms 기초 구성 요소](creating-adaptive-form.md): 클래식(이전) 데이터 캡처 구성 요소입니다. 적응형 양식을 기반으로 하는 기존 기초 구성 요소를 계속 사용하여 편집할 수 있습니다. 새 양식을 만드는 경우  [응용 Forms 핵심 구성 요소](creating-adaptive-form-core-components.md) 적용형 Forms을 만들려면

![적응형 양식 만들기 마법사](/help/release-notes/assets/wizard.png)


## 사전 요구 사항

적응형 양식을 만들려면 다음 항목이 필요합니다.

* **환경을 위한 적응형 Forms 핵심 구성 요소 활성화**: 새 프로그램을 만들 때 환경에 대해 응용 Forms 코어 구성 요소 가 이미 활성화되었습니다. Archetype 39 이하 버전을 기반으로 하는 Forms as a Cloud Service 환경이 있는 경우, [환경을 위한 적응형 Forms 핵심 구성 요소 활성화](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). 환경에 대한 코어 구성 요소 활성화 시 **응용 Forms(핵심 구성 요소)** 템플릿 및 캔버스 테마가 환경에 추가됩니다. AEM SDK 버전이 2023.02.0보다 오래된 경우, [확인 `prerelease` 환경에 활성화된 플래그](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) 적응형 Forms 코어 구성 요소는 2023.02.0 릴리스 전 사전 릴리스의 일부입니다.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 여기에는 특정 속성 및 컨텐츠 구조를 포함하는 사전 형식의 구성 요소가 있습니다. 또한 테마 및 제출 작업을 정의하는 옵션을 제공합니다. 테마는 모양과 느낌을 정의하고 제출 작업을 정의하여 적응형 양식 제출 시 수행할 작업을 정의합니다. 예를 들어, 수집된 데이터를 데이터 소스로 전송합니다. 클라우드 서비스는 라는 OOTB 템플릿을 제공합니다.

   * 다음 `blank` 템플릿은 모든 새로운 AEM Forms as a Cloud Service 프로그램에 포함되어 있습니다.
   * 패키지 관리자를 통해 참조 패키지를 설치하여 `blank` 템플릿을 AEM Forms as a Cloud Service 프로그램에 추가합니다.
   * 다음을 수행할 수도 있습니다 [새 적응형 Forms 템플릿(핵심 구성 요소) 만들기](template-editor.md) 처음부터

* **적응형 양식 테마**: 테마에는 구성 요소 및 패널에 대한 스타일 세부 사항이 포함되어 있습니다. 스타일은 배경색, 상태 색상, 투명도, 정렬 및 크기와 같은 속성을 포함합니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소를 반영합니다.  다음 `Canvas` 템플릿은 모든 새로운 AEM Forms as a Cloud Service 프로그램에 포함되어 있습니다.

   <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **권한**: 사용자를 [!DNL forms-users] 그룹에 속해 있어야 합니다. 의 구성원 [!DNL forms-users] 그룹에는 적응형 양식을 만들 수 있는 권한이 있습니다. 양식의 특정 사용자 그룹에 대한 자세한 목록은 [그룹 및 권한](forms-groups-privileges-tasks.md).


## 적응형 양식 만들기(핵심 구성 요소) {#create-an-adaptive-form-core-components}

1. 에 로그인합니다. [!DNL Experience Manager Forms] 작성자 인스턴스. 클라우드 인스턴스 또는 로컬 개발 인스턴스일 수 있습니다.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인하고 왼쪽 위 모서리에서 을(를) 탭합니다 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.

1. 탭 **[!UICONTROL 만들기]**  > **[!UICONTROL 응용 Forms]**. 마법사가 열립니다. 소스 탭에서 템플릿을 선택합니다.

   ![핵심 구성 요소 템플릿](/help/forms/assets/core-components-template.png)

   템플릿을 선택하면 템플릿에 지정된 테마 및 제출 작업이 자동으로 선택되고 **[!UICONTROL 만들기]** 단추가 활성화되어 있습니다. 로 이동할 수 있습니다. **[!UICONTROL 스타일]** 또는 **[!UICONTROL 제출]** 탭하여 다른 테마를 선택하거나 작업을 제출합니다. 선택한 템플릿에서 테마를 지정하지 않으면 만들기 단추가 비활성화된 상태로 유지됩니다. 로 이동할 수 있습니다. **[!UICONTROL 스타일]** 탭을 클릭하여 수동으로 테마를 선택합니다.

   >[!NOTE]
   >
   >
   > 없는 경우 **응용 Forms(핵심 구성 요소)** 환경에 있는 템플릿, [환경을 위한 적응형 Forms 핵심 구성 요소 활성화](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). 환경에 대한 코어 구성 요소 활성화 시 **응용 Forms(핵심 구성 요소)** 템플릿이 환경에 추가됩니다.

1. 에서 **[!UICONTROL 스타일]** 탭에서 테마를 선택합니다.

   * 선택한 서식 파일이 테마를 지정하면 마법사에서 테마가 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.

   * 선택한 서식 파일에서 테마를 지정하지 않으면 [스타일] 탭을 사용하여 테마를 선택할 수 있습니다. 다음 **[!UICONTROL 만들기]** 테마를 선택한 후에만 단추가 활성화됩니다.

1. (선택 사항) 데이터 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: A [양식 데이터 모델](data-integration.md) 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식에 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서 데이터를 가져오고 쓰는 작업이 포함된 경우 양식 데이터 모델 을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](adaptive-form-json-schema-form-model.md) Adobe의 핵심 구성 요소 기반 적응형 양식을 사용하면 생성 또는 사용되는 데이터의 구조를 나타내는 JSON 스키마를 연결하는 기능을 제공하여 조직의 백엔드 시스템과 원활하게 통합할 수 있습니다. 이 연결을 통해 작성자는 스키마 요소를 사용하여 적응형 양식에 컨텐츠를 동적으로 추가할 수 있습니다. 스키마 요소는 작성 프로세스 중에 컨텐츠 브라우저의 데이터 모델 개체 탭에서 쉽게 액세스할 수 있으며 모든 필드는 새로 만든 적응형 양식에 자동으로 추가됩니다.

   기본적으로 연결된 JSON 스키마의 모든 필드는 자동으로 선택되어 해당 적응형 양식 구성 요소로 변환되므로 작성 프로세스가 간소화됩니다. 마법사는 확인란을 사용하여 적응형 양식에 포함해야 하는 필드를 선택적으로 선택할 수 있는 추가 편의성을 제공합니다.

1. 에서 **[!UICONTROL 제출]** 탭에서 제출 작업을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 작업이 자동으로 선택됩니다. 제출 탭에서 다른 제출 작업을 선택할 수 있습니다. 다음 **[!UICONTROL 제출]** 탭에는 사용 가능한 모든 제출 작업이 표시됩니다.

   * 선택한 템플릿에서 전송 작업을 지정하지 않으면 **[!UICONTROL 제출]** 탭하여 제출 작업을 선택합니다.

1. (선택 사항)에서 **[!UICONTROL 배달]** 적응형 양식의 게시 또는 게시 취소 날짜를 지정할 수 있습니다.

1. 탭 **[!UICONTROL 만들기]**. 적응형 양식을 저장할 제목, 이름 및 위치를 지정하는 대화 상자가 나타납니다.

   * **[!UICONTROL 제목]** 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스.
   * **[!UICONTROL 이름:]** 양식의 이름을 지정합니다. 지정된 이름의 노드가 저장소에 생성됩니다. 제목을 입력을 시작하면 이름 필드의 값이 자동으로 생성됩니다. 제안된 값을 변경할 수 있습니다. 이름 필드에는 영숫자, 하이픈 및 밑줄만 포함할 수 있습니다. 잘못된 입력은 모두 하이픈으로 대체됩니다.
   * **[!UICONTROL 경로:]** 적응형 양식을 저장할 위치를 지정합니다. 에 바로 적응형 양식을 저장할 수 있습니다 `/content/dam/formsanddocuments` 또는 다음과 같은 폴더를 만듭니다. `/content/dam/formsanddocuments/adaptiveforms` 적응형 양식을 저장하려면 을 클릭합니다. 경로에 폴더를 사용하기 전에 폴더를 만들어야 합니다. 다음 **[!UICONTROL 경로]** 필드가 폴더를 자동으로 만들지 않습니다.

1. 탭 **[!UICONTROL 만들기]**. 적응형 양식이 만들어지고 적응형 Forms 편집기에서 열립니다. 편집기에 템플릿에서 사용할 수 있는 컨텐츠가 표시됩니다.  적응형 양식 유형에 따라 연결된 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델은 **[!UICONTROL 데이터 모델 개체]** 의 탭 **[!UICONTROL 컨텐츠 브라우저]** 을 클릭합니다. 이러한 요소를 드래그하여 놓아 적응형 양식을 작성할 수도 있습니다.

이제 적용형 Forms 코어 구성 요소를 적응형 Forms 컨테이너에 드래그 앤 드롭하여 양식을 디자인하고 만들 수 있습니다.

## 사용 가능한 응용 Forms 핵심 구성 요소

응용 Forms 코어 구성 요소는 표준화된 데이터 캡처 구성 요소입니다. 이러한 구성 요소는 사용자 정의 기능을 제공하고 개발 시간을 단축하며 디지털 등록 경험에 대한 유지 관리 비용을 절감합니다. [응용 Forms 코어 구성 요소 설명서](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko) 에는 각 구성 요소의 기능에 대한 자세한 정보와 함께 사용 가능한 구성 요소의 세부 목록이 있습니다. 또한 [https://aemcomponents.dev/](https://aemcomponents.dev/) 사용 가능한 핵심 구성 요소를 보려면 클릭하십시오.

## 적응형 양식의 양식 모델 속성 편집 {#edit-form-model}

1. 적응형 양식을 선택하고 탭합니다 ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 속성 열기]**. 양식 속성 페이지가 열립니다.

1. 로 이동합니다. **[!UICONTROL 양식 모델]** 탭을 선택하고 양식 모델을 선택합니다. 적응형 양식에 양식 모델이 없는 경우 JSON 스키마 또는 양식 데이터 모델을 선택할 수 있습니다. 반면에 적응형 양식이 이미 양식 모델을 기반으로 하는 경우 동일한 유형의 다른 양식 모델로 전환할 수 있는 옵션이 있습니다. 예를 들어, 양식에 JSON 스키마를 사용하는 경우 다른 JSON 스키마로 쉽게 전환할 수 있으며, 양식에서 양식 데이터 모델을 사용하는 경우처럼 다른 양식 데이터 모델로 전환할 수 있습니다.

1. 탭 **[!UICONTROL 저장]** 속성을 저장합니다.
