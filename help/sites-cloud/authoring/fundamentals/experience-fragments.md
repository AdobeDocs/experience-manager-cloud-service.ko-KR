---
title: 경험 조각
description: Adobe Experience Manager를 클라우드 서비스 경험 조각으로 사용하여 경험을 재사용 및 유연하게 만들 수 있습니다.
translation-type: tm+mt
source-git-commit: b7a2e86de27dbfcdecaf3a2bc1984678b7b69375

---


# 경험 조각 {#experience-fragments}

클라우드 서비스로 Adobe Experience Manager 내에서 경험 조각:
* 은 하나 이상의 구성 요소 그룹입니다.
* 콘텐트 및 레이아웃 모두 포함
* 페이지 내에서 참조할 수 있음
* 모든 구성 요소를 포함할 수 있습니다.

경험 조각:

* 경험(페이지)의 일부입니다.
* 여러 페이지에서 사용할 수 있습니다.
* 구조 및 구성 요소를 정의하기 위한 템플릿(편집만 가능)을 기반으로 합니다.
* 단락 시스템에서 레이아웃이 있는 하나 이상의 구성 요소로 구성되어 있습니다.
* 다른 경험 조각을 포함할 수 있습니다.
* 다른 조각(다른 경험 조각 포함)과 결합하여 전체 페이지(경험)를 형성할 수 있습니다.
* 다른 변형이 있을 수 있으며, 이 변형이 컨텐츠 및/또는 구성 요소를 공유할 수 있습니다.
* 조각의 여러 변형에서 사용할 수 있는 빌딩 블록으로 분할할 수 있습니다.

경험 조각을 사용할 수 있습니다.

* 작성자가 페이지의 부분(경험의 조각)을 다시 사용하려는 경우
경험 조각이 없으면 작성자는 해당 조각을 복사하여 붙여 넣어야 합니다. 이러한 복사/붙여넣기 경험을 생성하고 유지 관리하는 데는 시간이 오래 걸리고 사용자 오류가 발생합니다.
경험 조각은 복사/붙여넣기가 필요하지 않습니다.
* 헤드리스 CMS 사용 사례를 지원하기 위해
작성자는 작성용으로만 AEM을 사용하려고 하지만 고객에게 전달하기 위한 것은 아닙니다. 타사 시스템/터치포인트는 이러한 경험을 소모한 다음 최종 사용자에게 전달합니다.

>[!NOTE]
>
>경험 조각에 대한 쓰기 액세스 권한을 사용하려면 그룹에 사용자 계정을 등록해야 합니다.
>
>* `experience-fragments-editors`
>
>
문제가 발생하는 경우 시스템 관리자에게 문의하십시오.

## 언제 경험 조각을 사용해야 합니까? {#when-should-you-use-experience-fragments}

경험 조각은 다음과 같은 경우 사용해야 합니다.

* 경험을 재사용하려고 할 때
   * 경험을 동일하거나 유사한 컨텐츠에서 재사용.
* 타사의 컨텐츠 전달 플랫폼으로 AEM을 사용할 때
   * AEM을 컨텐츠 전달 플랫폼으로 사용하려는 솔루션.
   * 타사 터치포인트에 컨텐츠 포함.
* 다양한 변형 또는 표현물에 대한 경험이 있는 경우
   * 채널 또는 컨텍스트별 변형.
   * 그룹에 적합한 경험예를 들어, 여러 채널에 걸쳐 서로 다른 경험이 있는 캠페인이 있습니다.
* Omnichannel Commerce를 사용하는 경우
   * [소셜 미디어](/help/implementing/developing/extending/experience-fragments.md#social-variations) 채널에서 대규모로 상거래 관련 컨텐츠 공유.
   * 터치포인트를 거래와 관련시키기.

## 경험 조각 구성 {#organizing-your-experience-fragments}

권장 사항:
* 폴더를 사용하여 경험 조각 구성,

* [이러한 폴더에](#configure-allowed-templates-folder)허용된 템플릿을 구성합니다.

폴더를 만들면 다음 작업을 수행할 수 있습니다.

* 경험 조각에 의미 있는 구조를 만듭니다.예를 들어 분류에 따라

   >[!NOTE]
   >
   >경험 조각의 구조를 사이트의 페이지 구조에 정렬할 필요는 없습니다.

* [폴더 수준에서 허용되는 템플릿 할당](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >[템플릿 편집기](/help/sites-cloud/authoring/features/templates.md)를 사용하여 나만의 템플릿을 생성할 수 있습니다.

WKND 프로젝트는 몇 가지 경험 조각을 그에 따라 `Contributors`구성합니다. 사용된 구조는 다중 사이트 관리(언어 사본 포함)와 같은 다른 기능을 사용할 수 있는 방법도 보여줍니다.

다음을 참조하십시오.

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![경험 조각에 대한 폴더](/help/sites-cloud/authoring/assets/xf-folders.png)

## 경험 조각에 대한 폴더 만들기 및 구성 {#creating-and-configuring-a-folder-for-your-experience-fragments}

경험 조각에 대한 폴더를 만들고 구성하려면 다음을 수행하는 것이 좋습니다.

1. [폴더를](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-folder)만듭니다.

1. [해당 폴더에](#configure-allowed-templates-folder)대해 허용되는 경험 조각 템플릿을 구성합니다.

>[!NOTE]
>
>인스턴스에 [대해 허용되는 템플릿을 구성할 수도 있지만 업그레이드 시](#configure-allowed-templates-instance)값을 덮어쓸 수 있으므로 이 방법은 **권장되지** 않습니다.

### 폴더에 대해 허용되는 템플릿 구성 {#configure-allowed-templates-folder}

>[!NOTE]
>
>업그레이드 시 값을 덮어쓰지 않으므로 허용된 **템플릿을**&#x200B;지정하는 데 권장되는 방법입니다.

1. 필수 **경험 조각** 폴더로 이동합니다.

1. 폴더를 선택한 다음 속성을 **선택합니다**.

1. 허용된 템플릿 필드에서 필요한 템플릿을 검색할 정규 **표현식을 지정합니다** .

   예:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   다음을 참조하십시오.
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![경험 조각 속성 - 허용된 템플릿](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >자세한 내용은 [경험 조각용 템플릿](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments)을 참조하십시오.

1. 저장 **및 닫기를 선택합니다**.

### 인스턴스에 대해 허용되는 템플릿 구성 {#configure-allowed-templates-instance}

>[!CAUTION]
>
>지정된 템플릿은 업그레이드 시 **덮어쓸 수 있으므로 이** 방법으로 허용된 템플릿을 변경하지 않는 것이 좋습니다.
>
>이 대화 상자는 정보 용도로만 사용하십시오.

1. Navigate to the required **Experience Fragments** console.

1. **구성 옵션**&#x200B;을 선택합니다.

   ![구성 단추](/help/sites-cloud/authoring/assets/xf-18.png)

1. **경험 조각 구성** 대화 상자에서 필요한 템플릿을 지정합니다.

   ![경험 구성요소 구성](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >자세한 내용은 [경험 조각용 템플릿](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments)을 참조하십시오.

1. **저장**&#x200B;을 선택합니다.


## 경험 조각 생성 {#creating-an-experience-fragment}

경험 조각을 생성하려면 다음을 수행하십시오.

1. Select **Experience Fragments** from the Global Navigation.

   ![탐색 패널의 경험 조각](/help/sites-cloud/authoring/assets/xf-01.png)

1. 필요한 폴더로 이동하고 만들기를 **선택합니다**.

   ![경험 조각에 대한 폴더 만들기](/help/sites-cloud/authoring/assets/xf-02.png)

1. 경험 **조각을** 선택하여 경험 조각 **만들기 마법사를** 엽니다.

   필요한 **템플릿**&#x200B;을 선택하고 **다음**&#x200B;을 선택합니다.

   ![경험 조각 템플릿 선택](/help/sites-cloud/authoring/assets/xf-03.png)


1. **경험 조각**&#x200B;에 대한 **속성**&#x200B;을 입력합니다.

   **제목**&#x200B;은 필수입니다. **이름**&#x200B;을 비워 두면 **제목**&#x200B;에서 파생됩니다.

   ![경험 조각 속성](/help/sites-cloud/authoring/assets/xf-04.png)

1. **만들기**&#x200B;를 클릭합니다.

   메시지가 표시됩니다. 선택:

   * **완료**: 콘솔로 돌아갑니다. 
   * **열기**: 조각 편집기를 엽니다.

## 경험 조각 편집 {#editing-your-experience-fragment}

경험 조각 편집기는 일반 페이지 편집기와 유사한 기능을 제공합니다.

>[!NOTE]
>
>페이지 편집기 사용 방법에 대한 자세한 내용은 [페이지 컨텐츠 편집](/help/sites-cloud/authoring/fundamentals/editing-content.md)을 참조하십시오.

다음 예제 프로시저는 제품에 대한 티저를 작성하는 방법을 보여 줍니다.

1. 구성 요소 브라우저에서 필요한 구성 요소를 드래그하여 [놓습니다](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

1. 구성 요소에 따라 다음을 수행합니다.
   * 필요에 따라 컨텐츠 및/또는 자산을 추가합니다.
   * 필요에 따라 속성을 구성합니다.

1. 필요에 따라 구성 요소를 더 추가합니다.

예를 들어,`http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![페이지의 경험 조각](/help/sites-cloud/authoring/assets/xf-05.png)

## 경험 조각 변형 만들기 {#creating-an-experience-fragment-variation}

필요에 따라 경험 조각의 변형을 만들 수 있습니다.

1. [편집](#editing-your-experience-fragment)할 조각을 엽니다.
1. **변형** 탭을 엽니다.

   ![경험 조각 변형 만들기](/help/sites-cloud/authoring/assets/xf-06.png)

1. **만들기**&#x200B;를 사용하여 다음을 생성할 수 있습니다.

   * **변형**
   * **변형을 Live Copy로**.

1. 필수 속성을 정의합니다.

   * **템플릿**
   * **제목**
   * **이름** - 비워 두면 제목에서 파생됩니다.
   * **설명**
   * **변형 태그**
   예:

   ![변형 속성](/help/sites-cloud/authoring/assets/xf-07.png)

1. Confirm with **Done**, the new variation will be shown in the panel.

## 경험 조각 사용 {#using-your-experience-fragment}

이제 페이지를 작성할 때 경험 조각을 사용할 수 있습니다.

1. 편집할 페이지를 엽니다.

1. 페이지 단락 시스템 내에서 경험 조각 구성 요소의 인스턴스를 만듭니다.

1. 다음 중 한 방법으로 실제 경험 조각을 구성 요소 인스턴스에 추가합니다.

   * 자산 브라우저에서 필요한 조각을 구성 요소에 끌어다 놓기.
   * Select **Configure** from the component toolbar and specify the fragment to use, confirm with **Done**.
   >[!NOTE]
   >
   >구성 요소 도구 모음의 편집은 조각 편집기에서 조각을 여는 단축키로 작동합니다.

예를 들어,`http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![페이지 편집기에서 경험 조각](/help/sites-cloud/authoring/assets/xf-08.png)

## 빌딩 블록 {#building-blocks}

한 개 이상의 구성 요소를 선택하여 조각 내에서 재활용할 빌딩 블록을 생성할 수 있습니다.

### 빌딩 블록 작성 {#creating-a-building-block}

새 빌딩 블록을 작성하려면 다음을 수행하십시오.

1. 경험 조각 편집기에서 재사용할 구성 요소를 선택합니다.

   ![빌딩 블록의 구성 요소 선택](/help/sites-cloud/authoring/assets/xf-09.png)

1. 구성 요소 도구 모음에서 **빌딩 블록으로 변환**&#x200B;을 선택합니다.

   ![블록 작성 단추](/help/sites-cloud/authoring/assets/xf-10.png)

1. **빌딩 블록**&#x200B;의 이름을 입력하고 **변환**&#x200B;으로 확인합니다.

   ![이름 작성 블록](/help/sites-cloud/authoring/assets/xf-11.png)

1. 빌딩 **블록은** 왼쪽 탭(로컬&#x200B;**)에 표시되며 추가 작업을 위해**&#x200B;선택할 수 있습니다.

   ![철도의 빌딩 블록](/help/sites-cloud/authoring/assets/xf-12.png)

#### 빌딩 블록 관리 {#managing-a-building-block}

빌딩 블록은 **빌딩 블록** 탭에서 볼 수 있습니다. 각 블록에서 다음 작업을 수행할 수 있습니다.

* ****&#x200B;마스터로 이동: 새 탭에서 마스터 변형을 엽니다.
* **이름 변경**
* **삭제**

![빌딩 블록 관리](/help/sites-cloud/authoring/assets/xf-13.png)

#### 빌딩 블록 사용 {#using-a-building-block}

빌딩 블록을 구성 요소처럼, 조각의 단락 시스템으로 끌 수 있습니다.

사용 가능한 경험 조각 구성 블록을 편집할 때 왼쪽-손 탭에 표시됩니다. 다음에 따라 필터링할 수 있습니다.

* **로컬** - 현재 경험 조각에서 빌딩 블록
* **모두** - 모든 조각에서 빌딩 블록

![빌딩 블록 선택](/help/sites-cloud/authoring/assets/xf-14.png)

## 경험 조각 세부 사항 {#details-of-your-experience-fragment}

조각의 세부 사항을 볼 수 있습니다.

1. 경험 조각의 위치로 이동합니다(조각 내에서 변형을 더 아래로 탐색하지 마십시오).
Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an export to Target: <!--Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an [export to Target](/help/sites-administering/experience-fragments-target.md):-->

   ![경험 조각 세부 사항](/help/sites-cloud/authoring/assets/xf-15.png)

1. 경험 조각의 **속성**&#x200B;을 연 경우:

   ![속성 단추](/help/sites-cloud/authoring/assets/xf-16.png)

   속성은 여러 탭에서 사용할 수 있습니다.

   >[!CAUTION]
   >
   >이러한 탭은 경험 조각 콘솔에서 **속성을** 열면 표시됩니다.
   >
   >경험 **조각을** 편집할 때 속성을 열면 해당 페이지 [속성이](/help/sites-cloud/authoring/fundamentals/page-properties.md) 표시됩니다.

   ![경험 조각 속성](/help/sites-cloud/authoring/assets/xf-17.png)

   * **기본**
      * **제목** - 필수
      * **설명**
      * **태그**
      * **총 변형 수** - 정보만
      * **웹 변형 수** - 정보만
      * **비웹 변형** 수 - 정보만
      * **이 조각을 사용하는 페이지 수** - 정보만
   * **클라우드 서비스**
      * **클라우드 구성**
      * **클라우드 서비스 구성**
      * **Facebook 페이지 ID**
      * **Pinterest 보드**
   * **참조**
      * 참조 목록입니다
   * **소셜 미디어 상태**
      * 소셜 미디어 변형의 세부 사항입니다

## 일반 HTML 렌디션 {#the-plain-html-rendition}

Using the `.plain.` selector in the URL, you can access the plain HTML rendition from the browser.

>[!NOTE]
>
>브라우저에서 직접 사용할 수 있지만 [기본 목적은 다른 애플리케이션(예: 타사 웹 앱, 사용자 지정 모바일 구현)이 URL만 사용하여 경험 조각의 컨텐츠에 직접 액세스할 수 있도록 하는 것입니다.](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition)

## 경험 조각 내보내기 {#exporting-experience-fragments}

기본적으로 경험 조각은 HTML 형식으로 제공됩니다. 이는 AEM과 타사 채널에서 모두 동일하게 사용할 수 있습니다.

Adobe Target으로 내보내기 위해 JSON을 사용할 수도 있습니다. 자세한 내용은 경험 조각과 Target 통합을 참조하십시오. <!--For export to Adobe Target, JSON can also be used. See [Target Integration with Experience Fragments](/help/sites-administering/experience-fragments-target.md) for full information.-->
