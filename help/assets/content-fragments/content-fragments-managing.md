---
title: 컨텐츠 조각 관리
description: 컨텐츠 조각은 자산으로 저장되므로 자산 콘솔에서 주로 관리됩니다.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# 컨텐츠 조각 관리{#managing-content-fragments}

컨텐츠 조각은 **자산으로**&#x200B;저장되므로 기본적으로 자산 **콘솔에서 관리됩니다** .

>[!NOTE]
>
>그런 다음 컨텐츠 조각을 작성 페이지에 사용합니다.컨텐츠 [조각으로 페이지 작성을 참조하십시오](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

## 컨텐츠 조각 만들기 {#creating-content-fragments}

### 컨텐츠 모델 만들기 {#creating-a-content-model}


[구조화된 컨텐츠로 컨텐츠 조각을 만들기 전에 컨텐츠 조각 모델을](/help/assets/content-fragments/content-fragments-models.md) 활성화하고 생성할 수 있습니다.

>[!NOTE]
>
>템플릿에 대한 자세한 내용은 컨텐츠 조각 개발을 참조하십시오.단순 컨텐츠 조각에 사용됩니다.

<!--
>[!NOTE]
>
>See [Developing Content Fragments](/help/sites-developing/customizing-content-fragments.md) for further information on templates; used for simple content fragments.
-->

### 컨텐츠 조각 만들기 {#creating-a-content-fragment}

컨텐츠 조각을 만드는 방법은 (기본적으로) 단순 조각과 구조화된 조각 모두에 대해 동일합니다.

1. 조각을 **만들 자산** 폴더로 이동합니다.
2. 만들기를 **선택한**&#x200B;다음 **컨텐츠** 조각을 선택하여 마법사를 엽니다.
3. 마법사의 첫 번째 단계에서는 새 조각의 기준을 지정해야 합니다.

   * 다음과 같은 경우일 수 있습니다.

      * 템플릿 - 예: **단순 조각**<!-- [Template](/help/sites-developing/content-fragment-templates.md) - for example **Simple Fragment** -->

      * [모델](/help/assets/content-fragments/content-fragments-models.md) - 구조화된 컨텐츠가 필요한 조각을 만드는 데 사용됩니다.예를 들어 **공항** 모델
   * 사용 가능한 모든 템플릿과 모델이 표시됩니다.
   선택 후 다음을 **사용하여** 계속 진행합니다.

   ![조각](assets/cfm-managing-01.png)

4. 속성 **단계에서** 다음을 지정합니다.

   * **기본**

      * **제목**

         조각 제목입니다.

         필수.

      * **설명**

      * **태그**
   * **고급**

      * **이름**

         이름;URL을 구성하는 데 사용됩니다.

         필수;는 제목에서 자동으로 파생되지만 업데이트할 수 있습니다.


5. 만들기를 **선택하여** 작업을 완료한 다음 **편집할 조각** 열기 또는 완료를 사용하여 콘솔로 돌아갑니다 ****.

## 컨텐츠 조각에 대한 작업 {#actions-for-a-content-fragment}

자산 **콘솔에서** 컨텐츠 조각에 대한 다양한 작업을 사용할 수 있습니다.

* 도구 모음에서;조각을 선택한 후 모든 적절한 작업을 사용할 수 있습니다.
* 신속한 [작업](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions);개별 조각 카드에 사용할 수 있는 작업의 하위 집합입니다.

![액션](assets/cfm-managing-02.png)

조각을 선택하여 해당 작업과 함께 도구 모음을 표시합니다.

* **만들기**
* **다운로드**

   * 조각을 ZIP 파일로 저장합니다.요소, 변형, 메타데이터를 포함할지 여부를 정의할 수 있습니다.

* **체크아웃**
* **속성**

   * 조각의 메타데이터를 보거나 편집할 수 있습니다.

* **편집**

   * 요소, 변형, 관련 컨텐츠 및 메타데이터와 함께 컨텐츠를 [편집할 조각을](/help/assets/content-fragments/content-fragments-variations.md) 열 수 있습니다.

* **태그 관리**
* **대상 컬렉션**

   * 조각을 컬렉션에 추가합니다.
   * 컬렉션을 조각과 [연결할](/help/assets/content-fragments/content-fragments-assoc-content.md#adding-associated-content)때도 이 작업을 수행할 수 있습니다.

* **복사**/**붙여넣기**

* **이동**
* **빠른 게시**
* **게시 관리**
* **삭제**

>[!NOTE]
>
>이러한 작업 중 대부분은 자산 및/또는 AEM [데스크톱 앱에](/help/assets/manage-digital-assets.md) 대한 [표준](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)작업입니다.

## 조각 편집기 열기 {#opening-the-fragment-editor}

편집할 조각을 열려면 다음을 수행합니다.

<!--
>[!CAUTION]
>
>To edit a content fragment you need [the appropriate permissions](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Please contact your system administrator if you are experiencing issues.
-->

>[!CAUTION]
>
>컨텐츠 조각을 편집하려면 적절한 권한이 필요합니다. 문제가 발생하면 시스템 관리자에게 문의하십시오.

1. 자산 **콘솔을** 사용하여 컨텐츠 조각 위치로 이동합니다.
2. 다음 방법 중 하나를 사용하여 편집할 조각을 엽니다.

   * 조각 또는 조각 링크를 클릭/탭합니다(콘솔 보기에 따라 다름).
   * 조각을 선택한 다음 **도구 모음에서** 편집을 선택합니다.
   조각 편집기가 열립니다.

   ![조각 편집기](assets/cfm-managing-03.png)

   >[!NOTE]
   >
   >1. 조각이 컨텐츠 페이지에서 이미 참조되면 메시지가 표시됩니다.
      >
      >
      >

   2. 사이드 패널은 사이드 패널 전환 **아이콘을 사용하여 숨기거나 표시할 수** 있습니다.


3. 사이드 패널의 아이콘을 사용하여 세 가지 모드를 탐색합니다.

   * 변형:컨텐츠 [편집](#editing-the-content-of-your-fragment) 및 [변형 관리](#creating-and-managing-variations-within-your-fragment)

   * [주석](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
   * [관련 컨텐츠](#associating-content-with-your-fragment)
   * [메타데이터](#viewing-and-editing-the-metadata-properties-of-your-fragment)
   ![모드](assets/cfm-managing-04.png)

4. 변경한 후에는 필요에 따라 **저장** 또는 **취소를** 사용합니다.

   >[!NOTE]
   >
   >저장 ******및** 취소 모두 [편집기를 종료합니다. 컨텐츠 조각에 대해 두](#save-cancel-and-versions) 옵션 작동 방법에 대한 자세한 내용은 저장, 취소 및버전을 참조하십시오.

## 저장, 취소 및 버전 {#save-cancel-and-versions}

>[!NOTE]
>
>타임라인에서 버전을 [만들고 비교하고 되돌릴 수도 있습니다](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

편집기에는 두 가지 옵션이 있습니다.

* **저장**

   최신 변경 내용을 저장하고 편집기를 종료합니다.

   >[!CAUTION]
   >
   >컨텐츠 조각을 편집하려면 적절한 권한이 필요합니다. 문제가 발생하면 시스템 관리자에게 문의하십시오.

   <!-- 
  >[!CAUTION]
  >
  >To edit a content fragment you need [the appropriate permissions](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Please contact your system administrator if you are experiencing issues. 
  -->

   >[!NOTE]
   >
   >저장을 선택하기 전에 편집기에 남아 있고 일련의 변경을 수행할 수 **있습니다**.

   >[!CAUTION]
   >
   >Save는 변경 내용을 저장할 뿐만 아니라 **모든** 참조도 업데이트하고 필요에 따라 디스패처가 플러시되도록 합니다. 이러한 변경 사항을 처리하는 데 시간이 걸릴 수 있습니다. 이로 인해 대규모/복잡한/과도하게 로드된 시스템에 성능에 영향을 줄 수 있습니다.
   >
   >
   >저장을 사용하는 **다음 조각** 편집기를 신속하게 다시 입력하여 추가 변경을 수행하고 저장할 때 유의하십시오.

* **취소**

   최신 변경 내용을 저장하지 않고 편집기를 종료합니다.

컨텐츠 조각을 편집하는 동안 AEM은 자동으로 버전을 만들어 변경 사항을 취소할 경우 이전 컨텐츠를 복원할 **수** 있습니다.

1. AEM 편집을 위해 컨텐츠 조각을 열면 *편집 세션이* 존재하는지 여부를 나타내는 쿠키 기반 토큰이 있는지 확인합니다.

   1. 토큰이 발견되면 조각이 기존 편집 세션의 일부로 간주됩니다.
   2. 토큰을 사용할 수 *없고* 사용자가 컨텐츠 편집을 시작하는 경우 버전이 만들어지고 이 새 편집 세션에 대한 토큰이 클라이언트에 보내져 쿠키에 저장됩니다.

2. 활성 ** 편집 세션이 있는 동안 편집되는 컨텐츠는 600초마다 자동으로 저장됩니다(기본값).

   >[!NOTE]
   >
   >자동 저장 간격은 `/conf` 메커니즘을 사용하여 구성할 수 있습니다.
   >
   >기본값은 다음을 참조하십시오.
   >  `/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

3. 사용자가 편집을 **취소하도록** 선택하면 편집 세션이 시작될 때 만들어진 버전이 복원되고 토큰이 제거되어 편집 세션이 종료됩니다.
4. 사용자가 편집 내용을 **저장하도록** 선택하면 업데이트된 요소/변형이 유지되고 편집 세션을 종료하기 위해 토큰이 제거됩니다.

## 조각 컨텐츠 편집 {#editing-the-content-of-your-fragment}

조각을 연 후에는 변형 [탭을 사용하여](/help/assets/content-fragments/content-fragments-variations.md) 컨텐츠를 작성할 수 있습니다.

## 조각 내 변형 만들기 및 관리 {#creating-and-managing-variations-within-your-fragment}

마스터 컨텐츠를 만든 후에는 해당 컨텐츠의 변형을 만들고 관리할 [수](/help/assets/content-fragments/content-fragments-variations.md) 있습니다.

## 조각과 컨텐츠 연결 {#associating-content-with-your-fragment}

컨텐츠를 [](/help/assets/content-fragments/content-fragments-assoc-content.md) 조각에 연결할 수도 있습니다. 컨텐츠 페이지에 추가될 때 조각과 함께 자산(예: 이미지)을 사용할 수 있도록 연결을 제공합니다(선택 사항).

## 조각의 메타데이터(속성) 보기 및 편집 {#viewing-and-editing-the-metadata-properties-of-your-fragment}

메타데이터 탭을 사용하여 조각의 속성을 보고 편집할 [수](/help/assets/content-fragments/content-fragments-metadata.md) 있습니다.

## 컨텐츠 조각에 대한 타임라인 {#timeline-for-content-fragments}

표준 옵션 외에도 타임라인은 [컨텐츠](/help/assets/manage-digital-assets.md#timeline) 조각에 대한 정보와 작업을 모두 제공합니다.

* 버전, 주석 및 주석에 대한 정보 보기
* 버전에 대한 작업

   * **[이 버전으로 되돌리기](#reverting-to-a-version)**(기존 조각, 특정 버전 선택)

   * **[현재](#comparing-fragment-versions)**조각과 비교(기존 조각, 특정 버전 선택)

   * 레이블 **및** /또는 **주석** 추가(기존 조각, 특정 버전 선택)

   * **버전으로 저장** (기존 조각을 선택한 다음 타임라인의 아래쪽에 있는 위쪽 화살표)

* 주석에 대한 작업

   * **삭제**

>[!NOTE]
의견은 다음과 같습니다.
* 모든 자산에 대한 표준 기능
* 타임라인에서 제작
* 조각 자산 관련

주석(컨텐츠 조각에 대해)은 다음과 같습니다.
* 조각 편집기에 입력됨
* 조각 내에서 선택한 텍스트 세그먼트에 고유합니다.



예:

![타임라인](assets/cfm-managing-05.png)

## 조각 버전 비교 {#comparing-fragment-versions}

현재 **버전과 비교** 작업은 특정 버전을 선택한 [후 타임라인에서](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) 사용할 수 있습니다.

그러면 다음과 같이 열립니다.

* 현재 **버전** (최신)(왼쪽)

* 선택한 버전 **v&lt;*x.y*>** (오른쪽)

They will be shown by-side, where:

* 차이점이 강조 표시됩니다.

   * 삭제된 텍스트 - 빨간색
   * 삽입된 텍스트 - 녹색
   * 바뀐 텍스트 - 파란색

* 전체 화면 아이콘을 사용하면 두 버전 중 하나를 직접 열 수 있습니다.그런 다음 병렬 보기로 다시 전환합니다
* 특정 **버전으로** 되돌릴 수 있습니다.
* **완료를** 선택하면 콘솔로 돌아갑니다.

>[!NOTE]
조각을 비교할 때는 조각 컨텐츠를 편집할 수 없습니다.

![비교](assets/cfm-managing-06.png)

## Reverting to a Version  {#reverting-to-a-version}

조각의 특정 버전으로 되돌릴 수 있습니다.

* 타임라인에서 바로 [사용할 수 있습니다](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

   필요한 버전을 선택한 다음 이 버전으로 **되돌리기 작업을** 선택합니다.

* 버전을 [현재 버전과](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) 비교하는 동안 선택한 **버전으로 되돌릴** 수 있습니다.

## 조각 게시 및 참조 {#publishing-and-referencing-a-fragment}

>[!CAUTION]
조각이 모델을 기반으로 하는 경우 [모델이 게시되었는지](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model)확인해야 합니다.
모델이 아직 게시되지 않은 컨텐츠 조각을 게시하면 선택 목록에 이것이 표시되고 모델이 조각과 함께 게시됩니다.

컨텐츠 조각은 게시 환경에서 사용할 수 있도록 게시되어야 합니다. 게시물을 게시할 수 있습니다.

* 제작 후;를 **클릭합니다** .
* 조각을 [사용하는 페이지를](/help/sites-cloud/authoring/fundamentals/content-fragments.md#publishing)게시할 때;조각은 페이지 참조에 나열됩니다.

>[!CAUTION]
조각이 게시되고 참조되면 작성자가 편집을 위해 조각을 다시 열면 AEM에 경고가 표시됩니다. 이것은 조각의 변경 사항이 참조된 페이지에도 영향을 준다는 것을 경고하기 위한 것입니다.

## 조각 삭제 {#deleting-a-fragment}

조각을 삭제하려면

1. 자산 **콘솔에서** 컨텐츠 조각의 위치로 이동합니다.
2. 조각을 선택합니다.

   >[!NOTE]
   The **Delete** action is not available as a quick action.

3. Select **Delete** from the toolbar.
4. 삭제 **작업을** 확인합니다.

   >[!CAUTION]
   조각을 페이지에서 이미 참조한 경우 경고 메시지가 표시되고 강제 삭제를 **수행할지 확인해야 합니다**. 조각은 컨텐츠 조각 구성 요소와 함께 컨텐츠 페이지에서 삭제됩니다.
