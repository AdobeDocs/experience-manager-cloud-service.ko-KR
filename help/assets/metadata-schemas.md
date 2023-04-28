---
title: 메타데이터 스키마는 메타데이터 속성 페이지의 레이아웃을 정의합니다.
description: 메타데이터 스키마는 속성에 대해 표시되는 속성 페이지의 레이아웃과 메타데이터 속성을 정의합니다. 사용자 지정 메타데이터 스키마를 만들고, 메타데이터 스키마를 편집하고, 자산에 메타데이터 스키마를 적용하는 방법을 알아보십시오.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 9e94afeb-1c54-4653-bf52-b0910c0cb6c1
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '2620'
ht-degree: 10%

---

# 메타데이터 스키마 {#metadata-schemas}

조직은 자산 검색, 사용, 상호 운용성 등을 향상시키는 메타데이터 모델을 제안합니다. 올바른 메타데이터 응용 프로그램은 메타데이터 기반의 워크플로우 및 프로세스를 유지하기 위해 매우 민감합니다. 조직 전체 메타데이터 전략 및 표준을 준수하려면 DAM 사용자가 정렬하는 데 도움이 되는 메타데이터 스키마를 사용할 수 있습니다. [!DNL Adobe Experience Manager] 쉽고 유연한 방법으로 메타데이터 스키마를 생성, 유지 관리 및 적용할 수 있습니다.

in [!DNL Adobe Experience Manager Assets], 스키마에는 채울 특정 정보에 대한 특정 필드가 포함되어 있습니다. 또한 사용자에게 친숙한 방식으로 메타데이터 필드를 표시하는 레이아웃 정보도 포함되어 있습니다. 메타데이터 속성에는 제목, 설명, MIME 유형, 태그 등이 포함됩니다. 를 사용할 수 있습니다 [!UICONTROL 메타데이터 스키마 Forms] 기존 스키마를 수정하거나 사용자 지정 메타데이터 스키마를 추가하려면 편집기를 사용하십시오.

자산에 대한 속성 페이지를 보고 편집하려면 다음 단계를 수행합니다.

1. 을(를) 클릭합니다. **[!UICONTROL 속성 보기]** 카드 보기의 자산 타일에 있는 빠른 작업 옵션. 또는, 자산을 선택한 다음 를 클릭합니다 **[!UICONTROL 속성]** ![속성 보기](assets/do-not-localize/info-circle-icon.png) 를 클릭합니다.

1. 사용 가능한 탭 아래에서 다양한 편집 가능한 메타데이터 속성을 편집할 수 있습니다. 하지만 자산을 수정할 수는 없습니다 [!UICONTROL 유형] 에서 [!UICONTROL 기본] 속성 페이지의 탭.

   ![자산 유형을 변경할 수 없는 자산 속성의 기본 탭](assets/asset-properties-basic-tab.png)

   *그림: 자산의 기본 탭 [!UICONTROL 속성].*

   자산에 대한 MIME 유형을 수정하려면 사용자 지정 메타데이터 스키마 양식을 사용하거나 기존 양식을 수정합니다. 자세한 내용은 [메타데이터 스키마 Forms 편집](#edit-metadata-schema-forms) 추가 정보. MIME 유형의 메타데이터 스키마를 수정하는 경우 자산 및 모든 하위 유형에 대한 속성 페이지 레이아웃이 수정됩니다. 예를 들어, 다음 위치에서 jpeg 스키마를 수정합니다 `default/image` mime 유형을 사용하는 자산에 대한 메타데이터 레이아웃(자산 속성)만 수정합니다 `image/jpeg`. 그러나 기본 스키마를 편집하는 경우, 변경 사항은 모든 유형의 자산에 대한 메타데이터 레이아웃을 수정합니다.

## 메타데이터 스키마 양식 {#default-metadata-schema-forms}

양식 또는 템플릿 목록을 보려면 [!DNL Experience Manager] 인터페이스 탐색 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**.

[!DNL Experience Manager] 은 다음의 메타데이터 스키마 양식 템플릿을 제공합니다.

| 템플릿 |  | 설명 |
|---|---|---|
| [!UICONTROL 기본값] |  | 자산에 대한 기본 메타데이터 스키마 양식입니다. |
|  | 다음 하위 양식은 [!UICONTROL 기본] 양식: |  |
|  | <ul><li>[!UICONTROL dm_video]</li></ul> | Dynamic Media 비디오용 스키마 양식입니다. |
|  | <ul><li>[!UICONTROL 이미지]</li></ul> | MIME 유형을 사용하는 이미지에 대한 스키마 양식(예: ) `image/jpeg` 및 `image/png`. <br> 다음 [!UICONTROL 이미지] 양식에는 다음과 같은 하위 양식 템플릿이 있습니다. <ul><li> [!UICONTROL jpeg]: 하위 유형이 있는 자산에 대한 스키마 양식 [!UICONTROL jpeg].</li> <li>[!UICONTROL tiff]: 하위 유형 TIFF이 있는 자산에 대한 스키마 양식입니다.</li></ul> |
|  | <ul><li>[!UICONTROL 애플리케이션]</li></ul> | MIME 유형이 있는 자산에 대한 스키마 양식(예: ) `application/pdf` 및 `application/zip`. <br>[!UICONTROL pdf]: 하위 유형 PDF이 있는 자산에 대한 스키마 양식입니다. |
|  | <ul><li>[!UICONTROL 비디오]</li></ul> | MIME 유형을 사용하는 비디오 자산에 대한 스키마 양식 `video/avi` 및 `video/mp4`. |
| [!UICONTROL 컬렉션] |  | 컬렉션에 대한 스키마 양식입니다. |
| [!UICONTROL contentfragment] |  | Schema form for Content Fragments. |
| [!UICONTROL forms] |  | 이 스키마 양식은 [!DNL Adobe Experience Manager Forms]. |
| [!UICONTROL ugc_contentfragment] |  | 사용자가 생성한 컨텐츠 조각 및 소셜 미디어의 Experience Manager에 통합된 자산에 대한 스키마 양식입니다. |

>[!NOTE]
>
>스키마 양식의 하위 양식을 보려면 스키마 양식 이름을 클릭합니다.

## 메타데이터 스키마 양식 추가 {#add-a-metadata-schema-form}

메타데이터 스키마 양식을 추가하려면 다음 단계를 수행합니다.

1. 목록에 사용자 지정 템플릿을 추가하려면 **[!UICONTROL 만들기]** 를 클릭합니다.

   >[!NOTE]
   >
   >편집되지 않은 템플릿과 함께 잠금 기호가 표시됩니다. 템플릿을 사용자 지정하는 경우에는 잠겨 있지 않습니다 ![잠김](assets/do-not-localize/lock_closed_icon.svg).

1. 대화 상자에서 스키마 양식의 제목을 제공하고 **[!UICONTROL 만들기]** 을 눌러 양식 작성 프로세스를 완료합니다.

## 메타데이터 스키마 양식 편집 {#edit-metadata-schema-forms}

새로 추가되거나 기존 메타데이터 스키마 양식을 편집할 수 있습니다. 메타데이터 스키마 양식은 탭 내의 탭 및 양식 항목을 포함합니다. 이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내의 필드에 매핑/구성할 수 있습니다. 탭 또는 양식 항목을 메타데이터 스키마 양식에 추가할 수 있습니다. 상위에서 파생된 탭 및 양식 항목은 잠긴 상태입니다. 하위 수준에서 변경할 수 없습니다.

1. 설정 [!UICONTROL 메타데이터 스키마 Forms] 페이지에서 양식을 선택하고 **[!UICONTROL 편집]** 클릭합니다.

1. 설정 **[!UICONTROL 메타데이터 스키마 양식 편집기]** 페이지에서 메타데이터 양식을 사용자 지정합니다. 필요한 구성 요소를 **[!UICONTROL 양식 작성]** 탭 중 하나에 탭으로 이동합니다.

   ![자산 속성 페이지를 사용자 지정하는 메타데이터 스키마 편집기](assets/metadata-schema-editor.png)

   *그림: A [!UICONTROL 메타데이터 스키마 양식 편집기] 사용 가능한 탭이 있는 페이지입니다.*

1. 구성 요소를 구성하려면 구성 요소를 선택하고 에서 해당 속성을 수정합니다 **[!UICONTROL 설정]** 탭.

### 내의 구성 요소 [!UICONTROL 양식 작성] 탭 {#components-within-the-build-form-tab}

다음 **[!UICONTROL 양식 작성]** 탭에는 스키마 양식에서 사용하는 양식 항목이 나열됩니다. 다음 **[!UICONTROL 설정]** 탭에서는 **[!UICONTROL 양식 작성]** 탭. 다음 표에는 **[!UICONTROL 양식 작성]** 탭:

| 구성 요소 이름 | 설명 |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| [!UICONTROL 섹션 머리글] | 공통 구성 요소 목록에 대한 섹션 머리글을 추가합니다. |
| [!UICONTROL 한 줄 텍스트] | 단일 행 텍스트 속성을 추가합니다. 문자열로 저장됩니다. |
| [!UICONTROL 다중 값 텍스트] | 다중 값 텍스트 속성을 추가합니다. 문자열 배열로 저장됩니다. |
| [!UICONTROL 숫자] | 숫자 구성 요소를 추가합니다. |
| [!UICONTROL 날짜] | 날짜 구성 요소를 추가합니다. |
| [!UICONTROL 드롭다운] | 드롭다운 목록을 추가합니다. |
| [!UICONTROL 표준 태그] | 태그 추가. |
| [!UICONTROL 스마트 태그] | 을(를) 추가하여 메타데이터 태그를 자동으로 추가하여 검색 기능을 보강합니다. |
| [!UICONTROL 숨김 필드] | 숨김 필드를 추가합니다. 자산을 저장할 때 POST 매개 변수로 전송됩니다. |
| [!UICONTROL 자산 참조자] | 이 구성 요소를 추가하여 자산에서 참조하는 자산 목록을 표시합니다. |
| [!UICONTROL 자산 참조] | 를 추가하여 자산을 참조하는 자산 목록을 표시합니다. |
| [!UICONTROL 제품 참조] | 를 추가하여 자산과 연결된 제품 목록을 표시합니다. |
| [!UICONTROL 상황에 맞는 메타데이터] | 를 추가하여 자산의 속성 페이지에서 다른 메타데이터 탭 표시를 제어합니다. |

<!-- TBD: Ratings are not available in Experience Manager as a Cloud Service. Removed via cqdoc-18089 ticket. 
| [!UICONTROL Asset Rating]        | Add to display options for rating the asset.                                       |
-->

#### 메타데이터 구성 요소 편집 {#edit-the-metadata-component}

양식에서 메타데이터 구성 요소의 속성을 편집하려면 구성 요소를 클릭하여 **[!UICONTROL 설정]** 탭. 메타데이터 스키마의 주어진 속성에 필드를 하나만 매핑하는 것이 좋습니다. 그렇지 않으면 시스템에 의해 속성에 매핑된 최신 추가 필드가 선택됩니다.

**필드 레이블**: 자산의 속성 페이지에 표시되는 메타데이터 속성의 이름입니다.

**속성에 매핑**: 이 속성은 CRX 저장소에 저장되는 자산 노드의 상대 경로 또는 이름을 지정합니다. 다음으로 시작 `./` 경로가 자산의 노드 아래에 있음을 나타냅니다.

다음은 속성에 유효한 값의 예입니다.

* `./jcr:content/metadata/dc:title`: Stores the value at the asset&#39;s metadata node as the property `dc:title`.

* `./jcr:created`: 자산의 생성 날짜 및 시간을 저장합니다. 보호된 속성입니다. 이러한 속성을 구성하는 경우 해당 속성을 편집 비활성화로 표시하는 것이 좋습니다. Otherwise, the error &quot;Asset(s) failed to modify&quot; occurs when you save the asset&#39;s properties.

구성 요소가 메타데이터 스키마 양식에 올바르게 표시되는지 확인하려면 속성 경로에 공백이 없어야 합니다.

* **자리 표시자**: 이 속성을 사용하여 메타데이터 속성과 관련된 관련 자리 표시자 텍스트를 지정합니다.
* **필수 여부**: 이 속성을 사용하여 속성 페이지에서 메타데이터 속성을 필수로 표시합니다.
* **편집 비활성화**: 이 속성을 사용하여 속성 페이지에서 속성에 대한 편집 내용을 허용하지 않습니다.
* **읽기 전용에 빈 필드 표시**: 값이 없는 경우에도 속성 페이지에 메타데이터 속성을 표시하려면 이 속성을 표시합니다. 기본적으로 메타데이터 속성에 값이 없으면 속성 페이지에 나열되지 않습니다.
* **순서가 지정된 목록 표시**: 이 속성을 사용하여 선택 항목의 순서가 지정된 목록을 표시합니다.
* **선택 사항**: 이 속성을 사용하여 목록에서 선택 사항을 지정합니다.
* **설명** : 이 속성을 사용하여 메타데이터 구성 요소에 대한 간단한 설명을 추가합니다.
* **클래스**: 속성이 연결된 객체 클래스입니다.
* **삭제**: 클릭 [!UICONTROL 삭제] 스키마 양식에서 구성 요소를 삭제하려면 다음을 수행하십시오.

>[!NOTE]
>
>다음 [!UICONTROL 숨김 필드] 구성 요소에는 이러한 속성이 포함되지 않습니다. 대신 속성 이름, 값, 필드 레이블 및 설명과 같은 속성을 포함합니다. 숨김 필드 구성 요소에 대한 값은 자산이 저장될 때마다 POST 매개 변수로 전송됩니다. 자산에 대한 메타데이터로 저장되지 않습니다.

If you select the **[!UICONTROL Required]** option, you can search for assets missing mandatory metadata. From the **[!UICONTROL Filters]** panel, expand the **[!UICONTROL Metadata Validation]** predicate and select the **[!UICONTROL Invalid]** option. The search results display assets missing mandatory metadata that you configured through the schema form.

컨텍스트 메타데이터 구성 요소를 스키마 양식의 모든 탭에 추가하는 경우 구성 요소는 특정 스키마가 적용되는 자산의 속성 페이지에 목록으로 표시됩니다. 목록에는 상황별 메타데이터 구성 요소를 적용한 탭을 제외한 다른 모든 탭이 포함되어 있습니다. 현재 이 기능은 컨텍스트에 따라 메타데이터 표시를 제어하는 기본 기능을 제공합니다.

컨텍스트 메타데이터 구성 요소가 적용되는 탭 외에 속성 페이지에 탭을 표시하려면 목록에서 탭을 선택합니다. 탭이 속성 페이지에 추가됩니다.

### JSON 파일에 속성 지정 {#specify-properties-in-json-file}

Instead of specifying properties for the options in the **[!UICONTROL Settings]** tab, you can define the options in a JSON file by specifying corresponding key-value pairs. Specify the path of the JSON file in the **[!UICONTROL JSON Path]** field.

#### 스키마 양식에서 탭 추가 또는 삭제 {#add-delete-a-tab-in-the-schema-form}

The schema editor lets you add or delete a tab. The default schema form includes the **[!UICONTROL Basic]**, **[!UICONTROL Advanced]** , **[!UICONTROL IPTC]**, and **[!UICONTROL IPTC Extension]** tabs.

![메타데이터 스키마 양식의 기본 탭](assets/metadata-schema-form-tabs.png)

클릭 `+` 스키마 양식에 탭을 추가하려면 다음을 수행합니다. 기본적으로 새 탭의 이름은 다음과 같습니다 `Unnamed-1`. 에서 이름을 수정할 수 있습니다. **[!UICONTROL 설정]** 탭. 클릭 `X` 탭을 삭제하려면 다음을 수행하십시오.

![메타데이터 스키마 편집기를 사용하여 탭 추가 또는 삭제](assets/metadata-schema-form-new-tab.png)

## 메타데이터 스키마 양식 삭제 {#deleting-metadata-schema-forms}

Experience Manager을 사용하면 사용자 지정 스키마 양식만 삭제할 수 있습니다. 기본 스키마 양식/템플릿은 삭제할 수 없습니다. 그러나 이러한 양식에서 사용자 지정 변경 사항을 삭제할 수 있습니다.

양식을 삭제하려면 양식을 선택하고 삭제 아이콘을 클릭합니다.

>[!NOTE]
>
>기본 양식에 대한 사용자 지정 변경 사항을 삭제한 후 양식이 기본 상태로 복귀했음을 나타내기 위해 메타데이터 스키마 인터페이스에서 잠금 아이콘이 다시 나타납니다.

>[!NOTE]
>
>* 기본 양식에 대한 사용자 지정 변경 내용을 삭제한 후 잠금이 잠깁니다 ![잠김](assets/do-not-localize/lock_closed_icon.svg) 양식 앞에 다시 나타납니다. 양식이 기본 상태로 복귀되었음을 나타냅니다.
>* 에서 기본 메타데이터 스키마 양식을 삭제할 수 없습니다 [!DNL Assets].


## MIME 유형에 대한 스키마 양식 {#schema-forms-for-mime-types}

[!DNL Experience Manager] 에서는 즉시 사용 가능한 다양한 MIME 유형에 대한 기본 양식을 제공합니다. 그러나 다양한 MIME 유형의 자산에 사용자 지정 양식을 추가할 수 있습니다.

### MIME 유형에 새 양식 추가 {#adding-new-forms-for-mime-types}

Create a form under the appropriate form type. For example, to add a template for the `image/png` subtype, create the form under the &quot;image&quot; forms. The title for the schema form is the subtype name. In this case, the title is `png`.

#### 다양한 MIME 유형에 기존 스키마 템플릿 사용 {#use-an-existing-schema-template-for-various-mime-types}

다른 MIME 유형에 기존 템플릿을 사용할 수 있습니다. 예를 들어, `image/jpeg` MIME 유형의 자산에 대한 양식입니다 `image/png`.

이 경우, `/etc/dam/metadataeditor/mimetypemappings` 를 입력합니다. 노드의 이름을 지정하고 다음 속성을 정의합니다.

| 이름 | 설명 | 유형 | 값 |
|------|-------------|------|-------|
| `exposedmimetype` | 매핑할 기존 양식의 이름 | `String` | `image/jpeg` |
| `mimetypes` | 에 정의된 양식을 사용하는 MIME 유형 목록입니다 `exposedmimetype` 특성 | `String` | `image/png` |

[!DNL Assets] 는 다음 MIME 유형 및 스키마 양식을 매핑합니다.

| 스키마 양식 | MIME 유형 |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| 비디오/avi | video/avi, video/msvideo, video/x-msvideo |
| 비디오/wmv | video/x-ms-wmv |
| 비디오/flv | video/x-flv |

## 메타데이터 스키마에 대한 액세스 권한 부여 {#grant-access-to-metadata-schemas}

메타데이터 스키마 기능은 관리자만 사용할 수 있습니다. 그러나 관리자는 일부 권한을 수정하여 관리자가 아닌 사용자에게 액세스 권한을 제공할 수 있습니다. 관리자가 아닌 사용자가 `/conf` 폴더를 입력합니다.

## 폴더별 메타데이터 적용 {#applying-folder-specific-metadata}

[!DNL Assets] 메타데이터 스키마의 변형을 정의하고 특정 폴더에 적용할 수 있도록 해줍니다.

예를 들어, 기본 메타데이터 스키마의 변형을 정의하고 폴더에 적용할 수 있습니다. 수정된 스키마를 적용하면 이 스키마가 폴더 내의 자산에 적용되는 원래 기본 메타데이터 스키마를 무시합니다.

이 스키마가 적용되는 폴더에 업로드된 자산만 변형 메타데이터 스키마에 정의된 수정된 메타데이터에 따라야 합니다. [!DNL Assets] 원본 스키마가 적용되는 다른 폴더에서는 원본 스키마에 정의된 메타데이터를 계속 따릅니다.

자산의 메타데이터 상속은 계층의 최상위 폴더에 적용되는 스키마를 기반으로 합니다. 하위 폴더에 동일한 스키마가 적용되거나 상속됩니다. 하위 폴더 수준에서 다른 스키마를 적용하면 상속이 중지됩니다.

1. in [!DNL Experience Manager] 인터페이스, 탐색 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**. The **[!UICONTROL Metadata Schema Forms]** page is displayed.
1. 양식 앞에 있는 확인란(예: 기본 메타데이터 양식)을 선택하고 **[!UICONTROL 복사]** 사용자 지정 양식으로 저장합니다. 양식의 사용자 지정 이름(예: )을 지정합니다 `my_default`. 또는 사용자 지정 양식을 만들 수 있습니다.

1. 에서 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에서 을 선택합니다 `my_default` 양식을 만든 다음 **[!UICONTROL 편집]**.
1. 에서 **[!UICONTROL 메타데이터 스키마 편집기]** 페이지에서 스키마 양식에 텍스트 필드를 추가합니다. 예를 들어 레이블이 있는 필드를 추가합니다 **[!UICONTROL 카테고리]**.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정된 양식은 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지.
1. 클릭/탭 **[!UICONTROL 폴더에 적용]** 도구 모음에서 사용자 지정 메타데이터를 폴더에 적용합니다.
1. 수정된 스키마를 적용할 폴더를 선택한 다음 클릭/탭합니다 **[!UICONTROL 적용]**.
1. 폴더에 다른 메타데이터 스키마가 적용된 경우 기존 메타데이터 스키마를 덮어쓸 것이라는 메시지가 나타납니다. 클릭 **덮어쓰기**.
1. 클릭 **확인** 을 클릭하여 성공 메시지를 닫습니다.
1. 수정된 메타데이터 스키마를 적용한 폴더로 이동합니다.

## 필수 메타데이터 정의 {#defining-mandatory-metadata}

폴더 수준에서 필수 필드를 정의할 수 있습니다. 이 필드는 폴더에 업로드된 자산에 적용됩니다. 이전에 정의한 필수 필드에 대해 누락된 메타데이터가 있는 자산을 업로드하면 카드 보기의 자산에 누락된 메타데이터에 대한 시각적 표시가 나타납니다.

>[!NOTE]
>
>메타데이터 필드는 다른 필드의 값을 기준으로 필수로 정의할 수 있습니다. 카드 보기에서는 이러한 필수 메타데이터 필드에 대한 누락된 메타데이터에 대한 경고 메시지가 표시되지 않습니다.

1. Experience Manager 로고를 클릭한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**. The **[!UICONTROL Metadata Schema Forms]** page is displayed.
1. 기본 메타데이터 양식을 사용자 지정 양식으로 저장합니다. 예를 들어 다른 이름으로 저장합니다 `my_default`.
1. 사용자 지정 양식을 편집합니다. 필수 필드를 추가합니다. 예를 들어 **[!UICONTROL 카테고리]** 필드를 필수 필드로 만듭니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정된 양식은 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지. 양식을 선택한 다음 을(를) 클릭하거나 탭합니다 **[!UICONTROL 폴더에 적용]** 도구 모음에서 사용자 지정 메타데이터를 폴더에 적용합니다.
1. 폴더로 이동하고 사용자 지정 양식에 추가한 필수 필드에 대한 메타데이터가 없는 일부 자산을 업로드합니다. 필수 필드에 대한 누락된 메타데이터에 대한 메시지가 자산의 카드 보기에 표시됩니다.
1. (선택 사항) 액세스 `https://[server]:[port]/system/console/components/`. 구성 및 활성화 `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` 기본적으로 비활성화된 구성 요소입니다. Experience Manager이 자산에 대한 메타데이터의 유효성을 확인하는 빈도를 설정합니다.

   이 구성은 속성을 추가합니다 `hasValidMetadata` to `jcr:content` 자산입니다. 이 속성을 사용하면 Experience Manager이 검색 결과를 필터링할 수 있습니다.

   >[!NOTE]
   >
   >예약된 확인 후 자산이 추가되면, 자산에 플래그가 지정되지 않습니다 `hasValidMetadata` 다음 예약된 확인까지 자산이 중간 검색 결과에 표시되지 않습니다.

   >[!CAUTION]
   >
   >메타데이터 유효성 검사는 리소스를 많이 사용하므로 시스템 성능에 영향을 줄 수 있습니다. 그에 따라 검사를 예약합니다. 서버가 부하를 처리할 수 없는 경우 이 작업을 사용하지 않도록 설정하십시오

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
