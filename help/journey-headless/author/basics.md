---
title: 작성 기본 사항에 대해 알아보기
description: 콘텐츠 조각을 사용하여 Headless CMS용 콘텐츠를 작성하는 개념 및 메커니즘에 대해 알아봅니다.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
source-git-commit: 60ddcb3f2fd2219b0b1672791703582920825e81
workflow-type: tm+mt
source-wordcount: '1668'
ht-degree: 100%

---

# AEM을 통한 Headless 작성 기본 사항 - 소개 {#author-headless-basics}

## 지금까지의 스토리 {#story-so-far}

[AEM Headless 콘텐츠 작성자 여정](overview.md) 시작 부분의 [소개](introduction.md)에서는 Headless 작성과 관련된 기본 개념 및 용어를 다룹니다.

이 문서는 해당 사항을 기본으로 하며, 이를 통해 자체 AEM Headless 프로젝트의 콘텐츠를 작성하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

* **대상자**: 초급
* **목표**: Headless CMS 작성의 기본 사항 소개:
   * AEMaaCS를 사용한 작성 작업 소개
   * 콘텐츠 조각 소개

## 기본 처리 {#basic-handling}

콘텐츠 조각을 파악하기 전에 AEM 사용에 대한 (매우) 빠른 소개를 제공합니다.하지만 시스템에 로그인하고 시스템을 사용하려는 경험은 실제로 대체할 수 없습니다.

### 작성 및 게시 {#author-preview-publish}

AEM 설치는 일반적으로 두 개 이상의 환경으로 구성됩니다.

* 작성
* 게시

작성 환경에 로그인하고 작성 환경을 사용하여 콘텐츠를 생성합니다. 준비가 되면 콘텐츠를 일반적으로 사용할 수 있도록 게시합니다. Headless는 기타 애플리케이션에 게시하고, 웹 페이지는 웹에서 독자에게 게시합니다.

자세한 내용은 작성 개념을 참조하십시오.

### 로그인 {#signing-in}

대부분의 시스템과 마찬가지로 로그인해야 합니다. 다음 사항이 작성자에게 제공됩니다.

* 사용자 (계정) 이름
* 암호
* 로그인 화면 액세스 권한에 대한 링크

필요한 모든 권한으로 계정을 구성합니다. 문제가 발생한 경우 사내 프로젝트 지원 팀에 문의하는 것이 좋습니다.

### 탐색 {#navigation}

작은 온라인 튜토리얼에 처음 로그인하면 사용자 인터페이스의 주요 기능 중 일부가 강조 표시됩니다.

그런 다음 탐색 패널을 사용하여 AEM의 주요 영역에 액세스할 수 있습니다. 콘텐츠 조각의 경우 **콘텐츠 조각** 콘솔을 사용합니다(일부 액션의 경우 **에셋** 콘솔을 사용하기도 함).

왼쪽 상단의 Adobe 아이콘과 작은 나침반 아이콘을 차례로 선택하여 탐색 패널을 열 수 있습니다.

<!--
The Navigation Panel can be opened by selecting Adobe icon at the top left, followed by the small compass icon:

![Navigation panel](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)
-->

>[!NOTE]
>콘텐츠 조각은 AEM **Sites**&#x200B;의 일부 기능이지만 **에셋**&#x200B;으로 저장됩니다. 이는 영향을 미치지 않지만 알아두면 유용한 기술 세부 사항입니다.

콘솔 내 왼쪽 패널에서 폴더를 선택하여 콘텐츠 조각으로 이동할 수 있습니다. 필터링 및/또는 검색할 수도 있습니다.

![콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/assets/cfc-console-filter.png)

### 액션, 선택, 보기 {#actions-selecting-viewing}

**콘텐츠 조각** 콘솔에서는 도구 모음에서 콘텐츠 조각에 대해 다양한 작업을 사용할 수 있습니다.

<!-- ![Console actions](assets/cfm-managing-cf-console-01.png) -->

* **에셋에서 열기**
* **만들기**
* **참조자** 열은 해당 조각의 모든 상위 참조를 표시하는 직접 링크도 제공합니다. 여기에는 콘텐츠 조각, 경험 조각 및 페이지 참조가 포함됩니다.
* 폴더 이름에 마우스를 가져다 대면 JCR 경로가 표시됩니다.

조각 선택 후 모든 적절한 작업을 사용할 수 있습니다.

<!-- ![Console actions - fragment selected](assets/cfm-managing-cf-console-selected-01.png) -->

* **열기**
* **게시** (및 **게시 취소**)
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

## 콘텐츠 조각 작성 {#authoring-content-fragments}

지금까지 AEM 사용자 인터페이스(UI)에 대해 매우 간략하게 소개했습니다. 기회가 되면 사용해 보시기 바랍니다. 이제 핵심 주제인 Headless용 콘텐츠 조각에 대해 알아보겠습니다.

처음부터 끝까지 전체를 살펴보아야 하지만 인스턴스에 이미 생성된 폴더 및/또는 조각들이 서로 다른 위치에 배치될 수 있습니다. 원칙은 동일합니다.

### 구성 및 탐색 {#organizing-and-navigating}

콘텐츠 조각이 거의 없는 경우를 제외하고는 사용자(및 다른 사용자)가 다시 탐색할 수 있도록 조각을 구성하는 것이 좋습니다.

#### 폴더 만들기 {#creating-folder}

**에셋** 콘솔의 **파일** 섹션에서 일련의 폴더를 만들어 이 작업을 수행할 수 있습니다. **만들기** 옵션(오른쪽 상단)을 선택한 다음 **폴더**&#x200B;를 선택합니다.

![폴더 만들기 옵션](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

세부 정보를 입력할 수 있는 대화 상자를 연 다음 **만들기**&#x200B;로 확인합니다.

![폴더 만들기 대화 상자](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### 경로 및 태그를 사용하여 폴더에 제공되는 콘텐츠 조각 모델 제한 {#tags-paths-for-models-in-folder}

다소 개선된 고급 섹션입니다. 조각은 작업을 시작하고 시도하면 실제로 필요하지 않지만 조각이 많으면 *매우* 유용합니다. 그래서 조각을 아직 사용하지 않더라도 알아두면 좋습니다.

콘텐츠 설계자는 현재 프로젝트와 일부 다른 프로젝트에도 필요한 모든 콘텐츠 조각 모델을 생성했습니다. 사용자와 다른 작성자의 작업을 간단하게 유지할 수 있도록 특정 폴더에 제공되는 모델 목록을 제한할 수 있습니다.

폴더를 만든 후에는 **속성** 폴더를 열 수 있습니다. 여기에는 폴더에 대한 정보와 구성 세부 정보가 포함된 다양한 탭이 있습니다. 특히 콘텐츠 조각의 경우 **정책** 탭을 사용하여 이 폴더의 특정 경로 및/또는 태그를 정의할 수 있습니다. 이 폴더에서 조각을 생성하는 데 콘텐츠 조각 모델을 사용하기 전에 해당 요구 사항이 충족되어야 하므로 폴더에서 사용할 수 있는 콘텐츠 조각 모델을 제한합니다.

![폴더 속성 만들기 - 정책](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>콘텐츠 조각 모델 - 에셋 폴더에서 콘텐츠 조각 모델 허용에 대한 자세한 내용을 읽을 수 있습니다.

그리고 해당 폴더를 탐색하여 콘텐츠 조각을 만들고 편집합니다.

#### 해당되는 경우에만 - 폴더 Cloud Services 구성 {#cloud-services-folder}

해당되는 경우에만...

폴더를 만들 수 있는 초기 폴더가 제공될 수 있습니다. (일반적으로 개발자 또는 시스템 관리자에 의해) 일부 구성 세부 정보가 루트 폴더에 적용되어야 하기 때문입니다. 관심은 없지만 필요한 경우 폴더 **속성**&#x200B;의 **Cloud Services**&#x200B;에서 **구성**&#x200B;을 확인할 수 있습니다.

![폴더 속성 만들기 - 구성](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>에셋 폴더에 구성 적용에 대한 자세한 내용을 읽을 수 있습니다.

### 콘텐츠 조각 만들기 {#creating-fragment}

**콘텐츠 조각** 콘솔에서 **만들기**&#x200B;를 사용하여 **새 콘텐츠 조각** 대화 상자를 엽니다.

![콘텐츠 조각 콘솔 - 새 조각 만들기](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

다음을 지정합니다.

* **위치**
* **콘텐츠 조각 모델**
* **제목**
* **이름**
* **설명**

그런 다음 **만들기** 또는 **만들기 및 열기**&#x200B;로 확인합니다.

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

조각을 만든 직후에 또는 콘텐츠 조각 콘솔에서(에셋 콘솔에서도) 선택하여 조각을 열 수 있습니다.

편집기가 처음 열리면 다음을 확인할 수 있습니다.

* 왼쪽의 아이콘 목록 - 다양한 기능 영역에 액세스할 수 있습니다. 편집기가 **변형** 탭에서 열리고 대부분의 편집이 여기서 이뤄집니다. **주석** 및 **메타데이터** 탭에도 관심을 가질 수 있습니다.

* 조각에 대한 정보와 다양한 액션에 대한 액세스 권한이 포함된 헤더입니다.

* 기본 편집 영역 - 조각을 만드는 데 사용되는 모델에 따라 다릅니다.

예를 들면:

* 특정 유형의 정보를 포함하여 정보의 여러 부분만 필요로 하는 조각입니다. Headless 콘텐츠의 경우 여정 후반부에서 주요 참조에 대해 알아봅니다.

   ![콘텐츠 조각 편집기 - 내 조각](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* 긴 텍스트 섹션을 작성할 수 있는 조각입니다. 추가 옵션으로 텍스트를 관리하고 서식을 지정할 수 있습니다. 전체 화면 편집기에서 개별 텍스트 필드를 열 수도 있습니다(오른쪽 작은 화면 모양의 아이콘 사용).

   ![콘텐츠 조각 편집기 - Alaska Spirits](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>작성자가 일부 필드를 성공적으로 완료하는 방법에 대한 자세한 내용을 파악하는 데 프로젝트 관련 설명서가 필요할 수 있습니다.
>
>일반적인 내용은 콘텐츠 조각 모델 - 데이터 유형 및 속성을 참조하십시오.

**저장** 또는 **저장 및 닫기**&#x200B;로 업데이트를 확인합니다.

>[!NOTE]
>
>자세한 내용은 변형 - 콘텐츠 조각 작성을 참조하십시오.

#### 다음에 대해서는 걱정하지 않아도 됩니다. {#what-you-probably-do-not-need-to-worry-about}

예. 이 섹션은 약간 이상하게 보일지 모르지만, 콘텐츠 조각 편집기를 열고 탐색을 시작하면 Headless 여정에 적용되지 않는 다양한 옵션이 콘텐츠 작성자로 표시됩니다. 이는 Headless 컨텍스트에서 무시할 수 있는 콘텐츠에 대한 간략한 참고 사항입니다.

* **콘텐츠 조각 모델**

   조각 이름 바로 아래 편집기 상단에 콘텐츠 조각 모델 이름이 표시됩니다. 이는 모델 편집기로 이동하는 링크이기도 합니다.
콘텐츠 조각 모델은 사용하는 구조를 정의하므로 실제로 콘텐츠 조각에 핵심적인 요소입니다. 하지만 조각을 만들고 편집하는 것은 (일반적으로) 다른 담당자인 콘텐츠 설계자가 해야 하는 일입니다.

   >[!NOTE]
   >
   >자세히 알아보려면 AEM Headless 콘텐츠 설계자 여정을 참조하십시오.

* **관련 콘텐츠**

   이 콘텐츠는 분명히 편집기의 탭입니다.

   상당수의 AEM 버전에서 콘텐츠 조각을 사용할 수 있습니다. 페이지를 작성할 때 원래는 “기존” 용도로 사용할 수 있도록 제작되었습니다.여전히 이 컨텍스트에서 사용됩니다. 조각에는 임베드되지 않지만 페이지를 작성할 때 작성자가 사용할 수 있는 에셋(예: 이미지) 연결이 여기에 포함될 수 있습니다.

* **미리보기**

   이는 편집기의 다른 탭으로 주로 개발자용 기술 보기가 제공됩니다.

* **페이지 참조 업데이트**

   이 액션은 **...**(줄임표) 드롭다운에서 사용할 수 있습니다. 이는 페이지 작성과 관련이 있으므로 Headless 작성자는 별 관심이 없습니다.

### 게시 {#publishing}

<!-- needs more details -->

조각이 완료되면 Headless 애플리케이션에서 사용할 수 있도록 **게시**&#x200B;해야 합니다.

게시 액션은 편집기에서(또는 **콘텐츠 조각** 콘솔 또는 **에셋** 콘솔 도구 모음에서) 사용할 수 있습니다.

![콘텐츠 조각 편집기 - 내 조각](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

## 다음 단계 {#whats-next}

이제 기본 사항을 배웠으므로 다음 단계는 [참조에 대해 알아보기](references.md)입니다. 이 단계에서 Headless 작성의 핵심 부분이라 할 수 있는 다양한 참조와 조각 참조를 사용하여 구조 수준을 만드는 방법을 소개하고 자세히 설명합니다.

## 추가 리소스 {#additional-resources}

* [작성 개념](/help/sites-cloud/authoring/getting-started/concepts.md)

* [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 이 페이지는 주로 **Sites** 콘솔을 기반으로 하지만 여러/대부분의 기능은 **에셋** 콘솔에서의 **콘텐츠 조각** 작성과 관련성이 있기도 합니다.

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

      * [에셋 폴더에 구성 적용](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [콘텐츠 조각 만들기](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#creating-a-content-fragment)
   * [변형 - 콘텐츠 조각 작성](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md)

   * [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)

      * [콘텐츠 조각 모델 - 데이터 형식](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#data-types)

      * [콘텐츠 조각 모델 - 속성](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#properties)

      * [콘텐츠 조각 모델 - 에셋 폴더에서 콘텐츠 조각 모델 허용](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)


* 시작 안내서
   * [에셋 폴더 만들기 Headless 설정](/help/headless/setup/create-assets-folder.md)

* AEM Headless 콘텐츠 설계자 여정

* AEM Headless 번역 여정
