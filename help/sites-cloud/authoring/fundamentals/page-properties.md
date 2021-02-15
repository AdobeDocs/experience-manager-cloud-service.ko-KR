---
title: 페이지 속성 편집
description: 페이지의 필수 속성 정의
translation-type: tm+mt
source-git-commit: c3fd7b5a6311eded51b13ab9fea1ca6af4a050eb
workflow-type: tm+mt
source-wordcount: '1894'
ht-degree: 60%

---


# 페이지 속성 편집 {#editing-page-properties}

페이지에 필요한 속성을 정의할 수 있습니다. 이러한 속성은 페이지의 특성에 따라 다를 수 있습니다. 예를 들어, 일부 페이지는 Live Copy에 연결되어 있을 수 있지만 어떤 페이지는 연결되지 않고 Live Copy 정보를 적절하게 사용할 수 있습니다.

## 페이지 속성 {#page-properties}

속성은 여러 탭에 분산되어 있습니다.

### 기본 {#basic}

* **제목 및 태그**

   * **제목**  - 페이지 제목은 다양한 위치에 표시됩니다.예를 들어 웹 사이트  **** 탭 목록 및  **** 사이트 카드/목록 보기
      * 필수 필드입니다.
   * **태그** - 선택 상자의 목록을 업데이트하여 페이지에서 태그를 추가하거나 제거할 수 있습니다.
      * 태그를 선택하면 선택 상자 아래에 나열됩니다. 이 목록에서 x를 사용하여 태그를 제거할 수 있습니다.
      * 빈 선택 상자에 이름을 입력하여 완전히 새로운 태그를 입력할 수 있습니다.
         * Enter 키를 누르면 새 태그가 생성됩니다.
         * 그러면 새 태그가 표시되고 태그 오른쪽에는 새 태그임을 가리키는 작은 별이 표시됩니다.
      * 드롭다운 기능을 통해 기존 태그에서 선택할 수 있습니다.
      * 선택 상자에서 태그 항목을 마우스로 가리키면 x가 표시됩니다. 이를 통해 이 페이지에서 해당 태그를 제거할 수 있습니다.
      * 태그에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md)을 참조하십시오.
   * **탐색**  시 숨기기 - 결과 사이트의 페이지 탐색 시 페이지를 표시할지 아니면 숨길지를 나타냅니다.

* **브랜딩**

   각 페이지 제목에 브랜드 슬러그를 추가하여 페이지 전반에 일관된 브랜드 아이덴티티를 적용할 수 있습니다. 이 기능을 사용하려면 [핵심 구성 요소의 릴리스 2.14.0 이상에서 페이지 구성 요소를 사용해야 합니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

   * **재정의**  - 이 페이지에서 브랜드 슬러그를 정의하려면 선택합니다.
      * 값이 **Override** 값도 설정되어 있지 않으면 모든 하위 페이지에서 값이 상속됩니다.
   * **값**  무시 - 페이지 제목에 추가할 브랜드 슬러그의 텍스트입니다.
      * 이 값은 &quot;Cycling Tuscany&quot;와 같은 파이프 문자 뒤에 페이지 제목에 추가됩니다. | 항상 WKND 준비&quot;

* **HTML ID**

   * **ID**  - 구성 요소에 적용할 HTML ID.

* **기타 제목 및 설명**

   * **페이지 제목**  - 페이지에 사용할 제목입니다. 일반적으로 제목 구성 요소별로 사용됩니다. 비어 있으면 **제목**&#x200B;이 사용됩니다.
   * **탐색 제목**  - 탐색에 사용할 별도의 제목을 지정할 수 있습니다(예를 들어 더욱 간결한 제목을 원할 경우). 비어 있으면 제목이  **** 사용됩니다.
   * **자막**  - 페이지에서 사용할 자막입니다.
   * **설명**  - 페이지 설명, 목적 또는 추가하려는 기타 세부 사항입니다.

* **설정/해제 시간**

   * **설정**  - 게시 환경에서 게시된 페이지를 표시(렌더링됨)할 날짜와 시간입니다. 페이지를 수동으로 게시하거나 사전 구성된 자동 복제를 통해 게시해야 합니다.

      >[!NOTE]
      >
      > 관련 자동 복제를 구성하는 방법에 대한 자세한 내용은 [설정 및 해제 시간 - 트리거 구성](/help/operations/replication.md#on-and-off-times-trigger-configuration)을 참조하십시오.

      * 이미 [게시된 경우(수동으로)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)이 페이지는 지정된 시간에 렌더링될 때까지 비활성 상태로 유지됩니다(숨김).
      * 게시되지 않고 자동 복제를 위해 구성된 경우 페이지가 자동으로 게시되고 지정된 시간에 렌더링됩니다.
      * 게시되지 않았거나 자동 복제에 대해 구성되지 않은 경우 페이지가 자동으로 게시되지 않으므로 페이지 액세스를 시도하면 404가 표시됩니다.
   * **해제 시간**  - 설정 시간과 유사하며  **종종** 함께 사용됩니다. 게시 환경에서 게시된 페이지를 숨길 시간을 정의합니다.

   * 즉시 게시하고, 페이지가 비활성화될 때까지 게시 환경에서 사용할 수 있도록(일반적인 시나리오) 페이지에 대해 이러한 필드(**On Time** 및 **해제 시간**)를 비워 둡니다.


* **별칭 URL**

   * 이 페이지에 대한 별칭 URL을 입력할 수 있으므로 더 짧고 구체적인 URL을 사용할 수 있습니다.
   * 예를 들어 웹 사이트 `http://example.com`에 대해 경로 `/v1.0/startpage`로 식별되는 페이지에 대한 별칭 URL을 `welcome`으로 설정하면, `http://example.com/welcome`이 `http://example.com/content/v1.0/startpage`의 별칭 URL이 됩니다.

   >[!CAUTION]
   >
   >별칭 URL:
   >
   >* 이 URL은 고유해야 하므로 이 값이 다른 페이지에 이미 사용되고 있지는 않은지 주의해야 합니다.
   >* 정규식 패턴을 지원하지 않습니다.
   >* 기존 페이지로 설정하면 안 됩니다.


   * **추가**  - 페이지에 대한 별칭 URL을 정의하는 필드를 표시하려면 탭하거나 클릭합니다.
      * 여러 항목을 추가하려면 을(를) 다시 탭하거나 클릭합니다.
      * 별칭 URL을 삭제하려면 **제거** 아이콘을 탭하거나 클릭합니다.
   * **별칭 URL**  리디렉션 - 페이지에서 별칭 URL을 사용할지 여부를 나타냅니다.




### 고급 {#advanced}

* **설정**

   * **언어**  - 페이지 언어
   * **언어 루트**  - 페이지가 언어 사본의 루트인 경우 선택해야 합니다.
   * **리디렉션**  - 이 페이지에서 자동으로 리디렉션할 페이지를 나타냅니다.
   * **디자인**  - 결과 사이트의 페이지 탐색 시 페이지를 표시할지 아니면 숨길지를 나타냅니다.
   * **별칭**  - 이 페이지에 사용할 별칭을 지정합니다.

   >[!NOTE]
   >
   >별칭은 리소스의 별칭 이름을 정의하기 위해 `sling:alias` 속성을 설정합니다. 이 이름은 경로에는 영향을 주지 않고 리소스에만 영향을 줍니다.
   >
   >예를 들어 `/content/we-retail/spanish` 노드에 대해 `latin-lang`이라는 별칭을 정의하면, 이 페이지는 `/content/we-retail/latin-language`를 통해 액세스할 수 있습니다.
   >
   >자세한 내용은 SEO 및 URL 관리 우수 사례 아래의 로컬라이제이션된 페이지 이름을 참조하십시오.

   <!--
  >For further details see [Localized page names under SEO and URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names).
  -->

* **구성**

   * **클라우드 구성**  - 구성 경로

* **템플릿 설정**

   * **허용된 템플릿**  -  [이 하위 분기 내에서 사용할 수 ](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) 있는 템플릿 목록을 정의합니다.

* **인증 요구 사항**

   * **활성화**  - 페이지에 액세스하려면 인증을 사용합니다.

      >[!NOTE]
      >
      >페이지의 닫힌 사용자 그룹은 **[권한](#permissions)** 탭에 정의됩니다.

   * **로그인 페이지**  - 로그인에 사용할 페이지입니다.

* **내보내기**

   * **내보내기 구성**  - 내보내기 구성을 지정합니다.

### 썸네일 {#thumbnail}

페이지 축소판 구성

* **미리 보기**  생성 - 축소판으로 사용할 페이지의 미리 보기를 생성합니다.
* **이미지 업로드**  - 축소판으로 사용할 이미지를 업로드합니다.
* **이미지**  선택 - 축소판으로 사용할 기존 에셋을 선택합니다.
* **되돌리기**  - 축소판을 변경하면 이 옵션을 사용할 수 있습니다. 변경 사항을 유지하지 않으려면 저장하기 전에 해당 변경 사항을 되돌릴 수 있습니다.

### 소셜 미디어 {#social-media}

* **소셜 미디어 공유**

   페이지에서 사용 가능한 공유 옵션을 정의합니다. [핵심 구성 요소 공유](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/components/sharing.html)에 사용 가능한 옵션이 표시됩니다.

   * **Facebook에 대한 사용자 공유 활성화**
   * **Pinterest에 대한 사용자 공유 활성화**
   * **선호하는 XF 변형**
      * 페이지에 대한 메타데이터를 생성하는 데 사용되는 경험 조각 변형을 정의합니다.

### 클라우드 서비스 {#cloud-services}

* **클라우드 서비스 구성** - 클라우드 서비스에 대한 속성을 정의합니다

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### 개인화 {#personalization}

* **ContextHub 구성**

   * **ContextHub 경로**  -  [ContextHub 구성 정의](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **세그먼트 경로**  - 세그먼트  [경로 정의](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **타깃팅 구성**

   * **브랜드**  - 타게팅 [의 범위를 지정할 브랜드를 정의합니다](/help/sites-cloud/authoring/personalization/targeted-content.md).
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

이 탭은 Blueprint로 사용되는 페이지에만 표시됩니다.

* **현재 Live Copy**  - 이 블루프린트 페이지를 기반으로(즉, Live Copy)하는 페이지를 나열합니다.

   <!--Define properties for a Blueprint page within [multi-site management](/help/sites-administering/msm.md).-->
* **롤아웃 구성**  - 수정 내용이 Live Copy에 전파되는 상황을 제어합니다.

### Live Copy {#live-copy}

* **동기화**  - Live Copy를 블루프린트와 동기화하여 로컬 수정 유지
* **재설정**  - Live Copy를 블루프린트 상태로 재설정하고 로컬 수정 내용 제거
* **일시 중단**  - 추가 롤아웃 수정에서 Live Copy 일시 중단
* **분리**  - 블루프린트에서 Live Copy 분리

* **소스**

   * 이 Live Copy의 블루프린트 경로를 표시합니다.

* **상태**

   * 페이지의 현재 Live Copy 상태를 나열합니다.

* **구성**

   * **Live Copy 상속**  - 선택하면 Live Copy 구성이 모든 하위 항목에 적용됩니다.
   * **상위 항목에서 롤아웃 구성**  상속 - 이 확인란을 선택하면 롤아웃 구성이 페이지의 상위에서 상속됩니다
   * **롤아웃 구성 선택**  - 수정 내용이 블루프린트에서 전파되는 상황을 정의하고 상위 구성에서 롤아웃 구성  **상속을 선택하지 않은 경우에만 사용할 수** 있습니다.

## 페이지 속성 편집 {#editing-page-properties-1}

* **사이트** 콘솔에서:
   * [새 페이지 만들기](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page)(속성 하위 집합)
   * **속성** 클릭 또는 탭
      * 단일 페이지의 경우
      * 여러 페이지의 경우(속성의 하위 집합만 편집 가능)
* 페이지 편집기에서:
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
1. **속성 열기**&#x200B;를 선택합니다. 해당 탭별로 정렬된 속성을 편집할 수 있는 대화 상자가 열립니다. 다음 단추들은 도구 모음의 오른쪽에서도 사용할 수 있습니다.
   * **취소**
   * **저장 및 닫기**
1. **저장 및 닫기** 단추를 사용하여 변경 사항을 저장합니다.

### 사이트 콘솔에서 - 다중 페이지 {#from-the-sites-console-multiple-pages}

**사이트** 콘솔에서 여러 페이지를 선택한 다음 **속성 보기**&#x200B;를 사용하여 페이지 속성을 보거나 편집할 수 있습니다. 이를 페이지 속성의 벌크 편집이라고 합니다.

>[!NOTE]
>
>속성의 벌크 편집은 자산에 대해서도 사용할 수 있습니다. 비슷하지만 몇 가지 차이점이 있습니다. 자세한 내용은 다중 자산의 속성 편집을 참조하십시오.
>
>GQL(Google 쿼리 언어)을 사용하여 여러 페이지에서 컨텐츠를 검색한 다음 변경 사항을 원래 페이지에 저장하기 전에 벌크 편집기에서 직접 컨텐츠를 편집할 수 있으므로 벌크 편집기라고도 합니다.

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

벌크 편집을 시작하면 다음을 수행할 수 있습니다.

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
