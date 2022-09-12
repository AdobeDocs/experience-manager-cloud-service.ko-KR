---
title: 작성 기본 사항 학습
description: 컨텐츠 조각을 사용하여 헤드리스 CMS용 컨텐츠를 작성하는 개념과 역학에 대해 알아봅니다.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
source-git-commit: 60ddcb3f2fd2219b0b1672791703582920825e81
workflow-type: tm+mt
source-wordcount: '1668'
ht-degree: 12%

---

# AEM을 통한 Headless 작성 기본 사항 - 소개 {#author-headless-basics}

## 지금까지 이야기 {#story-so-far}

의 시작 [AEM Headless Content Author 여정](overview.md) a [소개](introduction.md) 헤드리스용 작성과 관련된 기본 개념 및 용어를 다룹니다.

이 문서는 AEM 헤드리스 프로젝트에 대한 자체 콘텐츠를 작성하는 방법을 이해할 수 있도록 이러한 내용을 기반으로 합니다.

## 목표 {#objective}

* **Audience**: 초보
* **목표**: 헤드리스 CMS 작성에 대한 기본 사항을 소개합니다.
   * AEMaaCS를 사용한 작성 소개
   * 컨텐츠 조각 소개

## 기본 처리 {#basic-handling}

컨텐츠 조각을 이해하기 전에 AEM 사용에 대한 빠른 소개입니다..그러나 어떤 것도 이 시스템을 사용하고 로그인하는 경험을 대신하지는 못합니다.

### 작성자 및 게시 {#author-preview-publish}

AEM 설치는 일반적으로 두 개 이상의 환경으로 구성됩니다.

* 작성
* 게시

로그인하고 작성 환경을 사용하여 컨텐츠를 생성합니다. 준비가 되면 컨텐츠를 일반적으로 사용할 수 있도록 게시합니다. 헤드리스의 경우 다른 응용 프로그램에 해당하며, 웹 페이지의 경우 웹의 판독기에 해당됩니다.

자세한 내용은 작성 개념을 참조하십시오.

### 로그인 중 {#signing-in}

대부분의 시스템과 마찬가지로 로그인해야 합니다. 작성자는 다음과 같이 제공됩니다.

* 사용자(계정) 이름
* 암호
* 로그인 화면에 액세스할 수 있는 링크

필요한 권한을 사용하여 계정이 구성되었습니다. 문제가 있는 경우 사내 프로젝트 지원 팀에 문의하는 것이 좋습니다.

### 탐색 {#navigation}

작은 온라인 자습서에 처음 로그인하면 사용자 인터페이스의 몇 가지 주요 기능이 강조 표시됩니다.

그런 다음 탐색 패널을 사용하여 AEM의 주요 영역에 액세스할 수 있습니다. 컨텐츠 조각의 경우 **컨텐츠 조각** 콘솔(일부 작업의 경우 **자산** 콘솔).

왼쪽 상단의 Adobe 아이콘을 선택한 다음 작은 나침반 아이콘을 선택하여 탐색 패널을 열 수 있습니다.

<!--
The Navigation Panel can be opened by selecting Adobe icon at the top left, followed by the small compass icon:

![Navigation panel](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)
-->

>[!NOTE]
>컨텐츠 조각은 AEM의 기능입니다 **Sites**&#x200B;로 저장되고 **자산**. 이는 사용자에게 영향을 미치지 않지만 도움이 될 수 있는 기술적인 세부 사항입니다.

콘솔 내에서 왼쪽 패널의 폴더를 선택하여 컨텐츠 조각으로 이동할 수 있습니다. 필터링 및/또는 검색할 수도 있습니다.

![컨텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/assets/cfc-console-filter.png)

### 작업, 선택, 보기 {#actions-selecting-viewing}

**콘텐츠 조각** 콘솔에서는 도구 모음에서 콘텐츠 조각에 대해 다양한 작업을 사용할 수 있습니다.

<!-- ![Console actions](assets/cfm-managing-cf-console-01.png) -->

* **에셋에서 열기**
* **만들기**
* **참조자** 열은 해당 조각의 모든 상위 참조를 표시하는 직접 링크도 제공합니다. 여기에는 콘텐츠 조각, 경험 조각 및 페이지 참조가 포함됩니다.
* 폴더 이름에 마우스를 가져다 대면 JCR 경로가 표시됩니다.

조각 선택 후 모든 적절한 작업을 사용할 수 있습니다.

<!-- ![Console actions - fragment selected](assets/cfm-managing-cf-console-selected-01.png) -->

* **열기**
* **게시**(및 **게시 취소**)
* **복사**
* **이동**
* **이름 변경**
* **삭제**

>[!NOTE]
>
>게시, 게시 취소, 삭제, 이동, 이름 변경, 복사, 비동기 작업 트리거와 같은 작업입니다. AEM 비동기 작업 UI를 통해 해당 작업의 진행 상태를 모니터링할 수 있습니다.

<!--
The **Assets** console has dedicated **Action Toolbars**, and **Quick Actions** that you can use after selecting a resource (for example, a folder or content fragment).

The Quick Actions are available for a single resource, see **Basel** in the example below:

![Quick Actions](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

The Actions Toolbar provides access to the full range of actions - applicable for the current scenario. The actions available can change; for example, dependent on your location, or whether you have selected multiple resources:

![Action Toolbar](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

You can select the format for viewing your resources with the View Selector:

![View Selector](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

You can view additional information about items using the Rail Selector. This also gives access to additional actions.

![Left Rail](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)
-->

## 컨텐츠 조각 작성 {#authoring-content-fragments}

따라서 AEM 사용자 인터페이스(UI)를 빠르게 소개했지만 사용해 볼 기회가 있었기를 바랍니다. 이제 관심사 - 헤드리스용 컨텐츠 조각 을 살펴보겠습니다.

처음부터 끝까지 작업을 수행해야 하지만 인스턴스에는 이미 폴더 및/또는 조각이 만들어졌고 다른 위치에 있을 수 있습니다. 원칙은 동일합니다.

### 구성 및 탐색 {#organizing-and-navigating}

컨텐츠 조각이 거의 없는 경우를 제외하고 컨텐츠 조각을 다시 찾을 수 있도록 구성할 수 있습니다.

#### 폴더 만들기 {#creating-folder}

내에서 일련의 폴더를 만들어 이 작업을 수행할 수 있습니다 **파일** 섹션 **자산** 콘솔. 을(를) 선택합니다 **만들기** 옵션(오른쪽 상단)을 누른 다음 **폴더**:

![폴더 만들기 옵션](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

세부 정보를 입력한 다음 확인할 수 있는 대화 상자가 열립니다. **만들기**:

![폴더 만들기 대화 상자](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### 경로 및 태그를 사용하여 폴더에서 사용할 수 있는 컨텐츠 조각 모델을 제한합니다 {#tags-paths-for-models-in-folder}

이 섹션은 약간 더 고급입니다. 단지 시작해서 뭔가를 시도하고 있다면, 그것은 정말로 필요하지 않지만, 그것은 *매우* 조각이 많을 때 유용합니다. 따라서, 당신이 그것을 아직 사용하지 않더라도 그것에 대해 아는 것은 좋습니다.

컨텐츠 설계자는 현재 프로젝트에 필요한 모든 컨텐츠 조각 모델을 생성했으며, 일부 다른 프로젝트도 생성할 수 있습니다. 자신과 다른 작성자가 작업을 단순하게 유지하기 위해 특정 폴더에 사용할 수 있는 모델 목록을 제한할 수 있습니다.

폴더를 만든 후 폴더를 열 수 있습니다 **속성**. 여기에는 폴더에 대한 정보 및 구성 세부 정보가 있는 다양한 탭이 있습니다. 특히 컨텐츠 조각의 경우 **정책** 탭하여 이 폴더의 특정 경로 및/또는 태그를 정의합니다. 이로 인해 폴더에서 사용할 수 있는 컨텐츠 조각 모델이 제한됩니다. 이는 컨텐츠 조각 모델이 이러한 요구 사항을 충족해야 이 폴더에서 조각을 생성할 수 있음을 의미합니다.

![폴더 속성 만들기 - 정책](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>컨텐츠 조각 모델 - 자산 폴더에서 컨텐츠 조각 모델 허용에서 자세한 내용을 읽을 수 있습니다.

그런 다음 이러한 폴더를 통해 컨텐츠 조각을 만들고 편집합니다.

#### 경우에 따라 - 폴더 Cloud Services 구성 {#cloud-services-folder}

혹시...

폴더를 만들 수 있는 초기 폴더가 주어질 것입니다. 이는 일부 구성 세부 사항을 루트 폴더에 적용해야 합니다(일반적으로 개발자 또는 시스템 관리자). 이것은 당신에게 흥미가 없을 수도 있지만, 필요할 경우, 당신은 그것을 확인할 수 있습니다 **구성** 에서 **Cloud Services** 폴더 **속성**:

![폴더 속성 만들기 - 구성](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>자산 폴더에 구성 적용 아래에서 자세히 읽어볼 수 있습니다.

### 콘텐츠 조각 만들기 {#creating-fragment}

에서 **컨텐츠 조각** 콘솔 **만들기** 열다 **새 컨텐츠 조각** 대화 상자:

![콘텐츠 조각 콘솔 - 새 조각 만들기](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

다음을 지정합니다.

* **위치**
* **컨텐츠 조각 모델**
* **제목**
* **이름**
* **설명**

그런 다음 다음 를 사용하여 확인합니다. **만들기** 또는 **만들기 및 열기**.

<!--
Creating a Content Fragment is very similar - you just use the **Content Fragment** option instead:

![Create Content Fragment option](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

This time a wizard opens. The first step is to select the Content Fragment Model that your fragment will be based on:

![Create Content Fragment - select Model](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

After continuing with **Next** you can supply the details (**Basic** and **Advanced**) for your fragment:

![Create Content Fragment - provide Name](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Confirm with **Create** and you can then **Open** your fragment in the editor.
-->

### 조각 편집 {#editing-fragment}

조각을 만든 직후 또는 컨텐츠 조각 콘솔(자산 콘솔에서도)에서 선택하여 조각을 열 수 있습니다.

편집기가 처음 열리면 다음을 볼 수 있습니다.

* 왼쪽에 있는 아이콘 목록 - 다양한 기능 영역에 액세스할 수 있습니다. 편집기는 **변형** 탭으로 이동하여 대부분의 편집 작업을 수행합니다. 또한 **주석** 및 **메타데이터** 탭.

* 조각에 대한 정보와 다양한 작업에 대한 액세스 권한이 있는 헤더입니다.

* 기본 편집 영역 - 조각을 만드는 데 사용되는 모델에 따라 다릅니다.

예:

* 조각은 여러 개의 정보만 필요로 하고, 일부는 특정 유형을 사용합니다. 헤드리스 컨텐츠의 경우 참조가 키이므로 여정에서 나중에 이러한 컨텐츠에 대해 학습할 수 있습니다.

   ![컨텐츠 조각 편집기 - 내 조각](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* 긴 텍스트 섹션을 작성할 수 있는 조각입니다. 텍스트를 관리하고 서식을 지정하는 추가 옵션이 있습니다. 전체 화면 편집기에서 개별 텍스트 필드를 열 수도 있습니다(오른쪽의 작은 화면과 같은 아이콘 사용)

   ![컨텐츠 조각 편집기 - 알래스카 주령](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>작성자가 일부 필드를 성공적으로 완료하는 방법에 대한 세부 정보를 만드는 데 프로젝트별 설명서가 필요할 수 있습니다.
>
>일반 세부 사항은 컨텐츠 조각 모델 - 데이터 유형 및 속성 을 참조하십시오.

다음 중 하나를 사용하여 업데이트를 확인합니다. **저장** 또는 **저장 및 닫기**.

>[!NOTE]
>
>자세한 내용은 변형 - 컨텐츠 조각 작성을 참조하십시오.

#### 여러분이(아마도)는 걱정할 필요가 없습니다 {#what-you-probably-do-not-need-to-worry-about}

좋습니다. 이 섹션은 약간 이상하게 보일 수 있지만, 컨텐츠 조각 편집기를 열고 탐색을 시작하면 컨텐츠 작성자로서 헤드리스 여정에 적용되지 않는 다양한 옵션이 표시됩니다(아마도). 따라서 이것은 헤드리스 컨텍스트에서 무시해야 하는 것에 대한 간단한 의견입니다.

* **콘텐츠 조각 모델**

   조각 이름 바로 아래에 편집기 맨 위에 있는 컨텐츠 조각 모델의 이름이 표시됩니다. 모델 편집기로 이동하는 링크이기도 합니다.
컨텐츠 조각 모델은 실제로 사용하는 구조를 정의할 때 컨텐츠 조각에 필수적입니다. 그러나 이러한 구성 요소를 만들고 편집하는 것은 일반적으로 다른 개인, 컨텐츠 설계자의 책임입니다.

   >[!NOTE]
   >
   >자세한 내용을 알아보려면 AEM Headless Content Architect 여정을 읽을 수 있습니다.

* **관련 콘텐츠**

   이것은 편집자의 입장이므로 아주 명백하다.

   컨텐츠 조각은 AEM에서 상당히 많은 버전 동안 사용할 수 있었습니다. 원래 이 템플릿은 페이지를 작성할 때 &quot;기존&quot; 용도로 사용할 수 있도록 만들어졌습니다..그리고 여전히 이런 맥락에서 사용됩니다. 여기에는 조각에 임베드되지 않았더라도 페이지를 작성할 때 작성자가 사용할 수 있어야 하는 자산(예: 이미지)과 연관될 수 있습니다.

* **미리보기**

   이는 편집기의 다른 탭이며, 주로 개발자를 위한 기술 보기를 제공합니다.

* **페이지 참조 업데이트**

   이 작업은 **...** (줄임표) 드롭다운. 머리글 없는 작성자는 페이지 작성과 관련되어 있으므로 흥미롭지는 않습니다.

### 게시 {#publishing}

<!-- needs more details -->

조각을 완료하면 다음을 수행할 수 있습니다 **게시** 헤드리스 애플리케이션에서 사용할 수 있도록 해줍니다.

게시 작업은 편집기(또는 **컨텐츠 조각** 콘솔 또는 **자산** 콘솔):

![컨텐츠 조각 편집기 - 내 조각](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

## 다음 단계 {#whats-next}

이제 기본 사항을 익혔으므로 다음 단계는 다음과 같습니다 [참조에 대해 알아보기](references.md). 이 페이지에서는 사용 가능한 다양한 참조 및 헤드리스를 위한 작성의 주요 부분인 조각 참조를 사용하여 구조 수준을 만드는 방법을 소개하고 설명합니다.

## 추가 리소스 {#additional-resources}

* [작성 개념](/help/sites-cloud/authoring/getting-started/concepts.md)

* [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 이 페이지는 주로 **Sites** 콘솔은 하지만 대부분의 기능은 작성에도 관련이 있습니다 **컨텐츠 조각** 아래에 **자산** 콘솔.

   * [탐색 패널](/help/sites-cloud/authoring/getting-started/basic-handling.md#navigation-panel)

   * [헤더](/help/sites-cloud/authoring/getting-started/basic-handling.md#the-header)

   * [액션 툴바](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)

   * [빠른 작업](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)

   * [리소스 보기 및 선택](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   * [레일 선택기](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)

   * 게시

      * [빠른 게시](/help/assets/manage-publication.md#quick-publish)

      * [게시 관리](/help/assets/manage-publication.md#manage-publication)

* [콘텐츠 조각을 사용하여 작업](/help/sites-cloud/administering/content-fragments/content-fragments.md)

   * [콘텐츠 조각 관리](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md)

      * [자산 폴더에 구성 적용](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [콘텐츠 조각 만들기](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#creating-a-content-fragment)
   * [변형 - 컨텐츠 조각 작성](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md)

   * [컨텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)

      * [컨텐츠 조각 모델 - 데이터 유형](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#data-types)

      * [컨텐츠 조각 모델 - 속성](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#properties)

      * [컨텐츠 조각 모델 - 자산 폴더에서 컨텐츠 조각 모델 허용](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)


* 시작 안내서
   * [자산 폴더 헤드리스 설정 만들기](/help/headless/setup/create-assets-folder.md)

* AEM 헤드리스 콘텐츠 설계 여정

* AEM 헤드리스 번역 여정
