---
title: 페이지 속성 편집
description: 페이지의 필수 속성 정의
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: 73adc2a9cad7f3e5dde723d1b3d695f8cec3ca69
workflow-type: tm+mt
source-wordcount: '1987'
ht-degree: 98%

---

# 페이지 속성 편집 {#editing-page-properties}

페이지에 필요한 속성을 정의할 수 있습니다. 이러한 속성은 페이지의 특성에 따라 다를 수 있습니다. 예를 들어 일부 페이지는 Live Copy에 연결되어 있을 수 있지만 어떤 페이지는 연결되지 않고 Live Copy 정보를 적절하게 사용할 수 있습니다.

## 페이지 속성 {#page-properties}

속성은 여러 탭에 분산되어 있습니다.

### 기본 {#basic}

* **제목 및 태그**

   * **제목** - 페이지 제목은 여러 위치에 표시됩니다(예: **웹 사이트** 탭 목록 및 **사이트** 카드/목록 보기).
      * 필수 필드입니다.
   * **태그** - 선택 상자의 목록을 업데이트하여 페이지에서 태그를 추가하거나 제거할 수 있습니다.
      * 태그를 선택하면 선택 상자 아래에 나열됩니다. 이 목록에서 x를 사용하여 태그를 제거할 수 있습니다.
      * 빈 선택 상자에 이름을 입력하여 완전히 새로운 태그를 입력할 수 있습니다.
         * Enter 키를 누르면 새 태그가 생성됩니다.
         * 그러면 새 태그가 표시되고 태그 오른쪽에는 새 태그임을 가리키는 작은 별이 표시됩니다.
      * 드롭다운 기능을 통해 기존 태그에서 선택할 수 있습니다.
      * 선택 상자에서 태그 항목을 마우스로 가리키면 x가 표시됩니다. 이를 통해 이 페이지에서 해당 태그를 제거할 수 있습니다.
      * 태그에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md)을 참조하십시오.
   * **탐색 숨기기** - 최종 사이트의 페이지 탐색에서 페이지를 표시할지 또는 숨길지 여부를 나타냅니다.

* **브랜딩**

   각 페이지 제목에 브랜드 슬러그를 추가하여 페이지 전체에서 일관된 브랜드 정체성을 적용합니다. 이 기능을 사용하려면 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)의 릴리스 2.14.0 이상에서 페이지 구성 요소를 사용해야 합니다.

   * **오버라이드** - 이 페이지의 브랜드 슬러그를 정의하려면 선택합니다.
      * 하위 페이지에 **오버라이드** 값이 설정되지 않은 경우 이 값이 모든 하위 페이지에 상속됩니다.
   * **오버라이드 값** - 페이지 제목에 추가될 브랜드 슬러그의 텍스트입니다.
      * 이 값은 페이지에서 파이프 문자 뒤에 추가됩니다(예: “Cycling Tuscany | Always ready for the WKND”)

* **HTML ID**

   * **ID** - 구성 요소에 적용할 HTML ID입니다.

* **기타 제목 및 설명**

   * **페이지 제목** - 페이지에서 사용할 제목입니다. 일반적으로 제목 구성 요소별로 사용됩니다. 비어 있으면 **제목**&#x200B;이 사용됩니다.
   * **탐색 제목** - 탐색에서 사용할 별도의 제목을 지정할 수 있습니다(예: 간결하게 나타내고자 하는 경우). 비어 있는 경우 **제목**&#x200B;이 사용됩니다.
   * **부제** - 페이지에서 사용할 부제입니다.
   * **설명** - 페이지, 페이지 용도 또는 추가하고자 하는 기타 세부 정보에 대한 설명입니다.

* **설정/해제 시간**

   >[!NOTE]
   >
   > 관련된 자동 복제를 구성하는 방법에 대한 자세한 내용은 [설정/해제 시간 - 트리거 구성](/help/operations/replication.md#on-and-off-times-trigger-configuration)을 참조하십시오.

   >[!NOTE]
   >**설정 시간** 또는 **해제 시간** 중 하나가 과거이고 자동 복제가 구성되어 있는 경우 관련된 작업이 즉시 트리거됩니다.

   * **설정 시간** - 게시된 페이지가 게시 환경에 표시되는(렌더링되는) 날짜 및 시간입니다. 수동으로 또는 사전 구성된 자동 복제를 통해 페이지를 게시해야 합니다.

      * 이미 [(수동으로) 게시](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)한 경우 이 페이지는 지정된 시간에 렌더링할 때까지 휴면 상태(숨겨짐)로 유지됩니다.
      * 이 페이지가 게시되지 않았으며 자동 복제에 대해 구성되어 있는 경우 지정된 시간에 자동으로 게시된 다음 렌더링됩니다.
      * 이 페이지가 게시되지 않았으며 자동 복제에 대해 구성되어 있지 않은 경우 페이지가 자동으로 게시되지 않으므로 페이지에 액세스하려고 하면 404 오류가 표시됩니다.
   * **해제 시간** - **설정 시간**&#x200B;과 유사하며 이와 함께 사용됩니다. 해제 시간은 게시된 페이지가 게시 환경에서 숨겨지는 날짜 및 시간입니다.

   * 페이지를 즉시 게시하고 이를 비활성화하기 전까지 게시 환경에서 사용하고자 하는 경우 이들 필드(**설정 시간** 및 **해제 시간**)를 비워두십시오(일반적인 시나리오).


* **별칭 URL**

   * 이 페이지에 대한 별칭 URL을 입력할 수 있으므로 더 짧고 구체적인 URL을 사용할 수 있습니다.
   * 예를 들어 웹 사이트 `http://example.com`에 대해 경로 `/v1.0/startpage`로 식별되는 페이지에 대한 별칭 URL을 `welcome`으로 설정하면 `http://example.com/welcome`이 `http://example.com/content/v1.0/startpage`의 별칭 URL이 됩니다.

   >[!CAUTION]
   >
   >별칭 URL:
   >
   >* 이 URL은 고유해야 하므로 이 값이 다른 페이지에 이미 사용되고 있지는 않은지 주의해야 합니다.
   >* 정규식 패턴을 지원하지 않습니다.
   >* 기존 페이지로 설정하면 안 됩니다.


   * **추가** - 페이지의 vanity URL을 정의할 필드를 표시하려면 탭하거나 클릭합니다.
      * 여러 vanity URL을 추가하려면 다시 탭하거나 클릭합니다.
      * vanity URL을 삭제하려면 **제거** 아이콘을 탭하거나 클릭합니다.
   * **vanity URL 리디렉션** - 페이지에서 vanity URL을 사용할지 여부를 나타냅니다.


### 고급 {#advanced}

* **설정**

   * **언어** - 페이지 언어
   * **언어 루트** - 페이지가 언어 사본의 루트인 경우 선택해야 합니다.
   * **리디렉션** - 이 페이지를 자동으로 리디렉션할 페이지를 나타냅니다. HTML 사용 `302 Found` 상태.
      * **영구 리디렉션** - 이 확인란을 선택하면 페이지가 HTML과 함께 제공된 대상 경로로 리디렉션됩니다 `301 Moved Permanently` 상태.
   * **디자인** - 최종 사이트의 페이지 탐색에서 페이지를 표시할지 또는 숨길지 여부를 나타냅니다.
   * **별칭** - 이 페이지와 사용할 별칭을 지정합니다.
      * 예를 들어 페이지 `/content/wknd/us/en/magazine/members-only`에 대한 `private`의 별칭을 정의하면 `/content/wknd/us/en/magazine/private`을 통해서도 이 페이지에 액세스할 수 있습니다.
      * 별칭을 만들면 페이지 노드의 `sling:alias` 속성이 설정되며, 이는 저장소 경로가 아닌 리소스에만 영향을 미칩니다.
      * 편집기의 별칭을 통해 액세스하는 페이지는 게시할 수 없습니다. 편집기의 [게시 옵션](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)은 실제 경로를 통해 액세스하는 페이지에 대해서만 사용할 수 있습니다.

   <!--
  >For further details see [Localized page names under SEO and URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names).
  -->

* **구성**

   * **클라우드 구성** - 구성으로의 경로

* **템플릿 설정**

   * **허용된 템플릿** - 이 하위 분기 내에서 [사용할 수 있는 템플릿 목록을 정의](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author)합니다.

* **인증 요구 사항**

   * **활성화** - 페이지 액세스를 위한 인증 사용 활성화

      >[!NOTE]
      >
      >페이지의 닫힌 사용자 그룹은 **[권한](#permissions)** 탭에 정의됩니다.

   * **로그인 페이지** - 로그인에 사용할 페이지

* **내보내기**

   * **내보내기 구성** - 내보내기 구성 지정

### 썸네일 {#thumbnail}

페이지 썸네일 구성

* **미리보기 생성** - 썸네일로 사용할 페이지의 미리보기를 생성합니다.
* **이미지 업로드** - 썸네일로 사용할 이미지를 업로드합니다.
* **이미지 선택** - 썸네일로 사용할 기존 에셋을 선택합니다.
* **되돌리기** - 이 옵션은 썸네일에 변경 내용을 적용한 다음 사용할 수 있습니다. 변경 사항을 유지하지 않으려면 저장하기 전에 해당 변경 사항을 되돌릴 수 있습니다.

### 소셜 미디어 {#social-media}

* **소셜 미디어 공유**

   페이지에서 사용 가능한 공유 옵션을 정의합니다. [핵심 구성 요소 공유](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/sharing.html)에 사용 가능한 옵션이 표시됩니다.

   * **Facebook에 대한 사용자 공유 활성화**
   * **Pinterest에 대한 사용자 공유 활성화**
   * **선호하는 XF 변형**
      * 페이지에 대한 메타데이터를 생성하는 데 사용되는 경험 조각 변형을 정의합니다.

### 클라우드 서비스 {#cloud-services}

* **클라우드 서비스 구성** - 클라우드 서비스 속성을 정의합니다.

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### 개인화 {#personalization}

* **ContextHub 구성**

   * **ContextHub 경로** - [ContextHub 구성](/help/sites-cloud/authoring/personalization/contexthub.md)을 정의합니다.
   * **세그먼트 경로** - [세그먼트 경로](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)를 정의합니다.

* **타겟팅 구성**

   * **브랜드** - [브랜드를 정의하여 타겟팅할 범위를 지정](/help/sites-cloud/authoring/personalization/targeted-content.md)합니다.
   >[!NOTE]
   >이 옵션을 사용하려면 사용자 계정이 `Target Administrators`그룹에 있어야 합니다.

### 권한 {#permissions}

* **권한**

   * 권한 추가
   * 폐쇄된 사용자 그룹 편집
   * 유효 권한 보기

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### 블루프린트 {#blueprint}

이 탭은 블루프린트 역할을 하는 페이지에만 표시됩니다. 블루프린트는 [다중 사이트 관리](/help/sites-cloud/administering/msm/overview.md)의 일부인 라이브 카피의 기반이 됩니다.

* **현재 라이브 카피** - 이 블루프린트 페이지를 기반으로 하는(이 블루프린트 페이지의 라이브 카피인) 페이지를 나열합니다.

* **롤아웃 구성** - 수정 사항이 라이브 카피에 반영되는 상황을 제어합니다.

### 라이브 카피 {#live-copy}

* **동기화** - 로컬 수정 사항을 유지하면서 라이브 카피와 블루프린트를 동기화합니다.
* **재설정** - 로컬 수정 사항을 제거하고 라이브 카피를 블루프린트 상태로 재설정합니다.
* **일시 중단** - 라이브 카피에 이후 롤아웃 수정 사항이 적용되지 않도록 일시 중단합니다.
* **분리** - 라이브 카피를 블루프린트에서 분리합니다.

* **소스**

   * 이 라이브 카피에 대한 블루프린트 경로를 표시합니다.

* **상태**

   * 페이지의 현재 라이브 카피 상태를 나열합니다.

* **구성**

   * **라이브 카피 상속** - 이 옵션이 선택되어 있으면 라이브 카피 구성이 모든 하위 항목에 적용됩니다.
   * **상위 항목에서 롤아웃 구성 상속** - 이 옵션이 선택되어 있으면 페이지의 상위 항목에서 롤아웃 구성이 상속됩니다.
   * **롤아웃 구성 선택** - 블루프린트에서 수정 사항이 반영되는 상황을 정의하며, **상위 항목에서 롤아웃 구성 상속**&#x200B;이 선택되어 있지 않은 경우에만 사용할 수 있습니다.

### 미리보기 {#preview}

미리보기 환경이 활성화되어 있으면 다음이 표시됩니다.

* 미리보기 URL - 미리보기 환경의 콘텐츠에 액세스하는 데 사용되는 URL

## 페이지 속성 편집 {#editing-page-properties-1}

* **사이트** 콘솔에서:
   * [새 페이지 만들기](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page)(속성 하위 집합)
   * **속성** 클릭 또는 탭
      * 단일 페이지의 경우
      * 여러 페이지의 경우(속성의 하위 집합만 편집 가능)
* 페이지 편집기에서
   * **페이지 정보**&#x200B;를 사용하여 **속성 열기**

### 사이트 콘솔에서 - 단일 페이지 {#from-the-sites-console-single-page}

**속성**&#x200B;을 클릭하거나 탭하여 페이지 속성을 정의하십시오.

1. **사이트** 콘솔에서 속성을 보고 편집할 페이지의 위치로 이동합니다.
1. 다음 중 하나를 사용하여 필요한 페이지에 대한 **속성** 옵션을 선택합니다.
   * [빠른 작업](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * 페이지 속성이 해당 탭을 사용하여 표시됩니다.
1. 필요에 따라 속성을 보거나 편집합니다.
1. 그런 다음 **저장**&#x200B;을 사용하여 업데이트를 저장한 후 **닫기**&#x200B;를 클릭하여 콘솔로 돌아갑니다.

### 페이지 편집 시 {#when-editing-a-page}

페이지 편집 시 **페이지 정보**&#x200B;를 사용하여 페이지 속성을 정의할 수 있습니다.

1. 속성을 편집할 페이지를 엽니다.
1. **페이지 정보** 아이콘을 선택하여 다음과 같은 선택 메뉴를 엽니다.
1. **속성 열기**&#x200B;를 선택합니다. 해당 탭별로 정렬된 속성을 편집할 수 있는 대화 상자가 열립니다. The following buttons are also available at the right of the toolbar:
   * **취소**
   * **저장 및 닫기**
1. **저장 및 닫기** 버튼을 사용하여 변경 사항을 저장합니다.

### 사이트 콘솔에서 - 다중 페이지 {#from-the-sites-console-multiple-pages}

From the **Sites** console you can select several pages then use **View Properties** to view and/or edit the page properties. This is referred to as bulk editing of page properties.

>[!NOTE]
>
>속성의 벌크 편집은 에셋에 대해서도 사용할 수 있습니다. 비슷하지만 몇 가지 차이점이 있습니다. 자세한 내용은 다중 에셋의 속성 편집을 참조하십시오.
>
>GQL(Google 쿼리 언어)을 사용하여 여러 페이지에서 콘텐츠를 검색한 다음 변경 사항을 원래 페이지에 저장하기 전에 벌크 편집기에서 직접 콘텐츠를 편집할 수 있으므로 벌크 편집기라고도 합니다.

<!--
>Bulk editing of properties is also available for Assets. It is very similar, but differs in a few points. See [Editing Properties of Multiple Assets](/help/assets/managing-multiple-assets.md) for details.
>
>There is also the [Bulk Editor](/help/sites-administering/bulk-editor.md), which allows you to search for content from multiple pages using GQL (Google Query Language) and then edit the content directly in the bulk editor before saving your changes to the originating pages.
-->

다음을 비롯하여 다양한 방법으로 벌크 편집할 여러 페이지를 선택할 수 있습니다.

* **사이트** 콘솔을 찾아볼 때
* **검색**&#x200B;을 사용하여 일련의 페이지를 찾은 후

페이지를 선택한 다음 **속성 옵션**&#x200B;을 클릭하거나 탭하면 벌크 속성이 표시됩니다.

![페이지 속성 벌크 편집](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

다음과 같은 페이지에 대해서만 벌크 편집을 수행할 수 있습니다.

* 동일한 리소스 유형 공유
* Live Copy의 일부가 아님
   * 페이지가 Live Copy에 있을 경우 속성을 열면 메시지가 표시됩니다.

벌크 편집을 시작하면 다음과 같은 작업을 수행할 수 있습니다.

* **보기**

   * 영향 받는 페이지 목록
      * 필요한 경우 선택/선택 취소할 수 있습니다.
      * 탭
         * 단일 페이지의 속성을 볼 때처럼 탭 아래에 속성이 정렬됩니다.
   * 속성 하위 집합
      * 선택한 모든 페이지에서 사용할 수 있고 벌크 편집에서 사용할 수 있다고 명시적으로 정의된 속성이 표시됩니다.
      * 페이지 선택을 한 페이지로 제한하면 모든 속성이 보입니다.
   * 공통 값을 갖는 공통 속성
      * 공통 값을 갖는 속성만 보기 모드에 표시됩니다.
      * 필드가 다중 값이면(예: 태그) *모두* 공통된 경우에만 값이 표시됩니다. 일부만 공통된 경우에는 편집할 때만 표시됩니다.
      * 공통 값이 있는 속성이 없으면 메시지가 표시됩니다.

* **편집**

   * 사용 가능한 필드의 값을 업데이트할 수 있습니다.
      * **완료**&#x200B;를 선택하면 선택한 모든 페이지에 새 값이 적용됩니다.
      * 필드가 다중 값(예: 태그)이면 새 값을 추가하거나 공통 값을 제거할 수 있습니다.
   * 공통되지만 여러 페이지에서 값이 다른 필드는 텍스트 `<Mixed Entries>`와 같은 특수한 값으로 표시됩니다. 이러한 필드를 편집할 때는 데이터가 손실되지 않도록 주의해야 합니다.

>[!NOTE]
>
>벌크 편집에 사용할 수 있는 필드를 지정하도록 페이지 구성 요소를 구성할 수 있습니다. 자세한 내용은 페이지 속성의 벌크 편집을 위한 페이지 구성을 참조하십시오.

<!--
>The page component can be configured to specify the fields available for bulk editing. See [Configuring your page for bulk editing of page properties](/help/sites-developing/bulk-editing.md).
-->
