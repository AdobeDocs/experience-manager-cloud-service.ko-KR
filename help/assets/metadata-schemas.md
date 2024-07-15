---
title: 메타데이터 스키마는 메타데이터 속성 페이지의 레이아웃을 정의합니다.
description: 메타데이터 스키마는 에셋에 대해 표시되는 메타데이터 속성 페이지 및 속성 페이지의 레이아웃을 정의합니다. 사용자 지정 메타데이터 스키마를 만들고, 메타데이터 스키마를 편집하고, 메타데이터 스키마를 에셋에 적용하는 방법을 알아봅니다.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 9e94afeb-1c54-4653-bf52-b0910c0cb6c1
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '2634'
ht-degree: 10%

---

# 메타데이터 스키마 {#metadata-schemas}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-schemas.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

조직은 자산 검색, 사용, 상호 운용성 등을 향상시키는 메타데이터 모델을 고안합니다. 올바른 메타데이터 애플리케이션은 메타데이터 기반 워크플로우 및 프로세스를 유지 관리하는 데 불가항력적입니다. 조직 전체의 메타데이터 전략 및 표준을 준수하기 위해 DAM 사용자가 조정할 수 있도록 도와주는 메타데이터 스키마를 사용할 수 있습니다. [!DNL Adobe Experience Manager]을(를) 사용하면 쉽고 유연한 방법으로 메타데이터 스키마를 만들고 유지 관리하고 적용할 수 있습니다.

[!DNL Adobe Experience Manager Assets]에서 스키마에는 채울 특정 정보에 대한 특정 필드가 포함되어 있습니다. 또한 사용자에게 친숙한 방식으로 메타데이터 필드를 표시하기 위한 레이아웃 정보가 포함되어 있습니다. 메타데이터 속성에는 제목, 설명, MIME 유형, 태그 등이 포함됩니다. [!UICONTROL 메타데이터 스키마 Forms] 편집기를 사용하여 기존 스키마를 수정하거나 사용자 지정 메타데이터 스키마를 추가할 수 있습니다.

에셋의 속성 페이지를 보고 편집하려면 다음 단계를 따르십시오.

1. 카드 보기의 자산 타일에 대한 빠른 작업에서 **[!UICONTROL 속성 보기]** 옵션을 클릭합니다. 또는 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 속성]** ![속성 보기](assets/do-not-localize/info-circle-icon.png)를 클릭합니다.

1. 사용 가능한 탭에서 편집 가능한 다양한 메타데이터 속성을 편집할 수 있습니다. 그러나 속성 페이지의 [!UICONTROL 기본] 탭에서 자산 [!UICONTROL 유형]을(를) 수정할 수 없습니다.

   ![자산 속성의 기본 탭입니다. 여기서 자산 유형을 변경할 수 없습니다.](assets/asset-properties-basic-tab.png)

   *그림: 에셋 [!UICONTROL 속성]의 기본 탭.*

   에셋의 MIME 유형을 수정하려면 사용자 지정 메타데이터 스키마 양식을 사용하거나 기존 양식을 수정합니다. 자세한 내용은 [메타데이터 스키마 편집 Forms](#edit-metadata-schema-forms)을 참조하십시오. MIME 유형의 메타데이터 스키마를 수정하면 에셋 및 모든 하위 유형에 대한 속성 페이지 레이아웃이 수정됩니다. 예를 들어 `default/image`에서 jpeg 스키마를 수정하면 MIME 유형이 `image/jpeg`인 에셋에 대한 메타데이터 레이아웃(에셋 속성)만 수정됩니다. 그러나 기본 스키마를 편집하면 변경 사항이 모든 유형의 에셋에 대한 메타데이터 레이아웃을 수정합니다.

## 메타데이터 스키마 양식 {#default-metadata-schema-forms}

양식 또는 템플릿 목록을 보려면 [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**(으)로 이동합니다.

[!DNL Experience Manager]은(는) 다음 메타데이터 스키마 양식 서식 파일을 제공합니다.

| 템플릿 | | 설명 |
|---|---|---|
| [!UICONTROL 기본값] | | 에셋의 기본 메타데이터 스키마 양식. |
| | 다음 자식 양식은 [!UICONTROL default] 양식의 속성을 상속합니다. | |
| | <ul><li>[!UICONTROL dm_video]</li></ul> | Dynamic Media 비디오용 스키마 양식. |
| | <ul><li>[!UICONTROL 이미지]</li></ul> | `image/jpeg` 및 `image/png` 등 MIME 형식의 이미지에 대한 스키마 양식입니다. <br> [!UICONTROL 이미지] 양식에 다음 하위 양식 서식 파일이 있습니다. <ul><li> [!UICONTROL jpeg]: 하위 유형 [!UICONTROL jpeg]의 에셋에 대한 스키마 양식입니다.</li> <li>[!UICONTROL tiff]: 하위 유형 TIFF을 가진 자산의 스키마 양식입니다.</li></ul> |
| | <ul><li>[!UICONTROL 응용 프로그램]</li></ul> | `application/pdf` 및 `application/zip`과(와) 같은 MIME 유형의 자산에 대한 스키마 양식입니다. <br>[!UICONTROL pdf]: 하위 유형 PDF이 있는 에셋의 스키마 양식입니다. |
| | <ul><li>[!UICONTROL 비디오]</li></ul> | `video/avi` 및 `video/mp4`과(와) 같은 MIME 유형의 비디오 자산에 대한 스키마 양식입니다. |
| [!UICONTROL 컬렉션] | | 컬렉션에 대한 스키마 양식입니다. |
| [!UICONTROL contentfragment] | | 콘텐츠 조각에 대한 스키마 양식. |
| [!UICONTROL 양식] | | 이 스키마 양식은 [!DNL Adobe Experience Manager Forms]과(와) 관련이 있습니다. |
| [!UICONTROL ugc_contentfragment] | | 소셜 미디어에서 Experience Manager에 통합된 사용자 생성 콘텐츠 부분 및 에셋에 대한 스키마 양식입니다. |

>[!NOTE]
>
>스키마 양식의 하위 양식을 보려면 스키마 양식 이름을 누릅니다.

## 메타데이터 스키마 양식 추가 {#add-a-metadata-schema-form}

메타데이터 스키마 양식을 추가하려면 다음 단계를 수행합니다.

1. 목록에 사용자 지정 템플릿을 추가하려면 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >편집되지 않은 템플릿과 함께 잠금 기호가 표시됩니다. 템플릿을 사용자 지정하는 경우 잠기지 않습니다. ![잠금이 닫힘](assets/do-not-localize/lock_closed_icon.svg).

1. 대화 상자에서 스키마 양식의 제목을 입력하고 **[!UICONTROL 만들기]**&#x200B;를 클릭하여 양식 만들기 프로세스를 완료합니다.

## 메타데이터 스키마 양식 편집 {#edit-metadata-schema-forms}

새로 추가된 메타데이터 스키마 양식 또는 기존 메타데이터 스키마 양식을 편집할 수 있습니다. 메타데이터 스키마 양식에는 탭과 탭 내의 양식 항목이 포함됩니다. 이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내에 있는 필드에 매핑/구성할 수 있습니다. 메타데이터 스키마 양식에 탭이나 양식 항목을 추가할 수 있습니다. 상위 항목에서 파생된 탭과 양식 항목이 잠긴 상태입니다. 하위 수준에서는 변경할 수 없습니다.

1. [!UICONTROL 메타데이터 스키마 Forms] 페이지에서 양식을 선택하고 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 메타데이터 스키마 양식 편집기]** 페이지에서 메타데이터 양식을 사용자 지정합니다. **[!UICONTROL 양식 작성]** 탭에서 필요한 구성 요소를 탭 중 하나로 드래그합니다.

   ![자산 속성 페이지를 사용자 지정할 메타데이터 스키마 편집기](assets/metadata-schema-editor.png)

   *그림: 사용 가능한 탭이 있는 [!UICONTROL 메타데이터 스키마 양식 편집기] 페이지.*

1. 구성 요소를 구성하려면 구성 요소를 선택하고 **[!UICONTROL 설정]** 탭에서 속성을 수정하십시오.

### [!UICONTROL 양식 작성] 탭의 구성 요소 {#components-within-the-build-form-tab}

**[!UICONTROL 양식 작성]** 탭에는 스키마 양식에서 사용하는 양식 항목이 나열됩니다. **[!UICONTROL 설정]** 탭은 **[!UICONTROL 양식 작성]** 탭에서 선택한 각 항목의 특성을 제공합니다. 다음 표에는 **[!UICONTROL 양식 작성]** 탭에서 사용할 수 있는 양식 항목이 나열되어 있습니다.

| 구성 요소 이름 | 설명 |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| [!UICONTROL 섹션 머리글] | 공통 구성 요소 목록의 섹션 머리글을 추가합니다. |
| [!UICONTROL 한 줄 텍스트] | 한 줄 텍스트 속성을 추가합니다. 문자열로 저장됩니다. |
| [!UICONTROL 다중 값 텍스트] | 다중 값 텍스트 속성을 추가합니다. 문자열 배열로 저장됩니다. |
| [!UICONTROL 숫자] | 숫자 구성 요소를 추가합니다. |
| [!UICONTROL 날짜] | 날짜 구성 요소를 추가합니다. |
| [!UICONTROL 드롭다운] | 드롭다운 목록을 추가합니다. |
| [!UICONTROL 표준 태그] | 태그를 추가합니다. |
| [!UICONTROL 스마트 태그] | 메타데이터 태그를 자동으로 추가하여 검색 기능을 보강합니다. |
| [!UICONTROL 숨겨진 필드] | 숨겨진 필드를 추가합니다. 에셋이 저장될 때 POST 매개 변수로 전송됩니다. |
| [!UICONTROL 자산 참조자] | 자산이 참조하는 자산 목록을 보려면 이 구성 요소를 추가하십시오. |
| [!UICONTROL 자산 참조] | 를 추가하여 에셋을 참조하는 에셋 목록을 표시합니다. |
| [!UICONTROL 제품 참조] | 를 추가하여 자산과 연결된 제품 목록을 표시합니다. |
| [!UICONTROL 컨텍스트 메타데이터] | 를 추가하여 자산의 속성 페이지에서 다른 메타데이터 탭의 표시를 제어합니다. |

<!-- TBD: Ratings are not available in Experience Manager as a Cloud Service. Removed via cqdoc-18089 ticket. 
| [!UICONTROL Asset Rating]        | Add to display options for rating the asset.                                       |
-->

#### 메타데이터 구성 요소 편집 {#edit-the-metadata-component}

양식에 대한 메타데이터 구성 요소의 속성을 편집하려면 구성 요소를 클릭하여 **[!UICONTROL 설정]** 탭에서 다음 속성의 전체 또는 하위 집합을 편집합니다. 메타데이터 스키마의 특정 속성에 필드를 매핑하는 것이 좋습니다. 그렇지 않으면 속성에 매핑된 최신 추가 필드가 시스템에 의해 선택됩니다.

**필드 레이블**: 에셋의 속성 페이지에 표시되는 메타데이터 속성의 이름입니다.

**속성에 매핑**: 이 속성은 에셋 노드가 CRX 저장소에 저장되는 에셋 노드의 상대 경로 또는 이름을 지정합니다. `./`(으)로 시작하여 경로가 자산의 노드 아래에 있음을 나타냅니다.

다음은 속성에 유효한 값의 예입니다.

* `./jcr:content/metadata/dc:title`: Stores the value at the asset&#39;s metadata node as the property `dc:title`.

* `./jcr:created`: 에셋의 생성 날짜 및 시간을 저장합니다. 보호 속성입니다. 이러한 속성을 구성하는 경우, Adobe은 해당 속성을 편집 비활성화로 표시할 것을 권장합니다. Otherwise, the error &quot;Asset(s) failed to modify&quot; occurs when you save the asset&#39;s properties.

구성 요소가 메타데이터 스키마 양식에 제대로 표시되도록 하려면 속성 경로에 공백을 포함해서는 안 됩니다.

* **자리 표시자**: 이 속성을 사용하여 메타데이터 속성과 관련된 관련 자리 표시자 텍스트를 지정합니다.
* **필수**: 이 속성을 사용하여 메타데이터 속성을 속성 페이지에서 필수로 표시합니다.
* **편집 사용 안 함**: 속성 페이지에서 속성을 편집할 수 없도록 하려면 이 속성을 사용하십시오.
* **읽기 전용에 빈 필드 표시**: 값이 없는 경우에도 속성 페이지에 메타데이터 속성을 표시하려면 이 속성을 표시하십시오. 기본적으로 메타데이터 속성에 값이 없으면 속성 페이지에 나열되지 않습니다.
* **정렬된 목록 표시**: 이 속성을 사용하여 정렬된 선택 목록을 표시합니다.
* **선택 항목**: 목록에서 선택 항목을 지정하려면 이 속성을 사용하십시오.
* **설명** : 이 속성을 사용하여 메타데이터 구성 요소에 대한 간단한 설명을 추가합니다.
* **클래스**: 속성이 연결된 개체 클래스입니다.
* **삭제**: 스키마 양식에서 구성 요소를 삭제하려면 [!UICONTROL 삭제]를 클릭하십시오.

>[!NOTE]
>
>[!UICONTROL 숨김 필드] 구성 요소에 이러한 특성이 포함되어 있지 않습니다. 대신 속성 이름, 값, 필드 레이블 및 설명과 같은 속성이 포함됩니다. 숨김 필드 구성 요소에 대한 값은 에셋이 저장될 때마다 POST 매개 변수로 전송됩니다. 에셋의 메타데이터로 저장되지 않습니다.

If you select the **[!UICONTROL Required]** option, you can search for assets missing mandatory metadata. From the **[!UICONTROL Filters]** panel, expand the **[!UICONTROL Metadata Validation]** predicate and select the **[!UICONTROL Invalid]** option. The search results display assets missing mandatory metadata that you configured through the schema form.

컨텍스트 메타데이터 구성 요소를 스키마 양식의 탭에 추가하면 구성 요소가 특정 스키마가 적용되는 에셋의 속성 페이지에 목록으로 표시됩니다. 이 목록에는 컨텍스트 메타데이터 구성 요소를 적용한 탭을 제외한 다른 모든 탭이 포함되어 있습니다. 현재, 이 기능은 컨텍스트를 기반으로 메타데이터 표시를 제어하는 기본 기능을 제공합니다.

컨텍스트 메타데이터 구성 요소가 적용되는 탭 외에 속성 페이지에 탭을 표시하려면 목록에서 탭을 선택합니다. 탭이 속성 페이지에 추가됩니다.

### JSON 파일의 속성 지정 {#specify-properties-in-json-file}

Instead of specifying properties for the options in the **[!UICONTROL Settings]** tab, you can define the options in a JSON file by specifying corresponding key-value pairs. Specify the path of the JSON file in the **[!UICONTROL JSON Path]** field.

#### 스키마 양식에서 탭 추가 또는 삭제 {#add-delete-a-tab-in-the-schema-form}

The schema editor lets you add or delete a tab. 기본 스키마 양식에는 **[!UICONTROL 기본]**, **[!UICONTROL 고급]**, **[!UICONTROL IPTC]** 및 **[!UICONTROL IPTC 확장]** 탭이 있습니다.

![메타데이터 스키마 양식의 기본 탭](assets/metadata-schema-form-tabs.png)

스키마 양식에 탭을 추가하려면 `+`을(를) 클릭하십시오. 기본적으로 새 탭의 이름은 `Unnamed-1`입니다. **[!UICONTROL 설정]** 탭에서 이름을 수정할 수 있습니다. 탭을 삭제하려면 `X`을(를) 클릭하십시오.

![메타데이터 스키마 편집기를 사용하여 탭을 추가하거나 삭제](assets/metadata-schema-form-new-tab.png)

## 메타데이터 스키마 양식 삭제 {#deleting-metadata-schema-forms}

Experience Manager을 사용하면 사용자 정의 스키마 양식만 삭제할 수 있습니다. 기본 스키마 양식/템플릿을 삭제할 수는 없습니다. 그러나 이러한 양식에서 사용자 정의 변경 사항을 삭제할 수 있습니다.

양식을 삭제하려면 양식을 선택하고 삭제 아이콘을 클릭합니다.

>[!NOTE]
>
>기본 양식에 대한 사용자 지정 변경 사항을 삭제한 후 메타데이터 스키마 인터페이스에서 양식 앞에 잠금 아이콘이 다시 표시되어 양식이 기본 상태로 되돌아갔음을 나타냅니다.

>[!NOTE]
>
>* 기본 양식에 대한 사용자 지정 변경 내용을 삭제한 후 양식 앞에 ![잠금 닫힘](assets/do-not-localize/lock_closed_icon.svg) 잠금이 다시 나타납니다. 양식이 기본 상태로 되돌려짐을 나타냅니다.
>* [!DNL Assets]에서 기본 메타데이터 스키마 양식을 삭제할 수 없습니다.

## MIME 유형에 대한 스키마 양식 {#schema-forms-for-mime-types}

[!DNL Experience Manager]은(는) 다양한 MIME 형식에 대한 기본 양식을 제공합니다. 하지만 다양한 MIME 유형의 자산에 대한 사용자 정의 양식을 추가할 수 있습니다.

### MIME 유형에 대한 새 양식 추가 {#adding-new-forms-for-mime-types}

적절한 양식 유형에서 양식을 만듭니다. 예를 들어 `image/png` 하위 유형에 대한 템플릿을 추가하려면 &quot;이미지&quot; 양식 아래에 양식을 만드십시오. The title for the schema form is the subtype name. 이 경우 제목은 `png`입니다.

#### 다양한 MIME 유형에 기존 스키마 템플릿 사용 {#use-an-existing-schema-template-for-various-mime-types}

다른 MIME 유형에 기존 템플릿을 사용할 수 있습니다. 예를 들어 MIME 유형 `image/png`의 자산에 대해 `image/jpeg` 양식을 사용하십시오.

이 경우 CRX 저장소의 `/etc/dam/metadataeditor/mimetypemappings`에 노드를 만듭니다. 노드 이름을 지정하고 다음 속성을 정의합니다.

| 이름 | 설명 | 유형 | 값 |
|------|-------------|------|-------|
| `exposedmimetype` | 매핑할 기존 양식의 이름 | `String` | `image/jpeg` |
| `mimetypes` | `exposedmimetype` 특성에 정의된 양식을 사용하는 MIME 유형 목록 | `String` | `image/png` |

[!DNL Assets]이(가) 다음 MIME 형식 및 스키마 양식을 매핑합니다.

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
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## 메타데이터 스키마에 대한 액세스 권한 부여 {#grant-access-to-metadata-schemas}

메타데이터 스키마 기능은 관리자만 사용할 수 있습니다. 그러나 관리자는 일부 권한을 수정하여 관리자가 아닌 사용자에게 액세스 권한을 제공할 수 있습니다. 관리자가 아닌 사용자에게 `/conf` 폴더에 대한 만들기, 수정 및 삭제 권한을 제공합니다.

## 폴더별 메타데이터 적용 {#applying-folder-specific-metadata}

[!DNL Assets]을(를) 사용하면 메타데이터 스키마의 변형을 정의하고 특정 폴더에 적용할 수 있습니다.

예를 들어, 기본 메타데이터 스키마의 변형을 정의하여 폴더에 적용할 수 있습니다. 수정된 스키마를 적용하면 폴더 내의 에셋에 적용된 원래 기본 메타데이터 스키마를 재정의합니다.

이 스키마가 적용되는 폴더에 업로드된 자산만 변형 메타데이터 스키마에 정의된 수정된 메타데이터를 따릅니다. 원본 스키마가 적용되는 다른 폴더의 [!DNL Assets]은(는) 원본 스키마에 정의된 메타데이터를 계속 따릅니다.

에셋의 메타데이터 상속은 계층의 최상위 폴더에 적용되는 스키마를 기반으로 합니다. 동일한 스키마가 하위 폴더에 적용되거나 하위 폴더에 상속됩니다. 하위 폴더 수준에서 다른 스키마가 적용되면 상속이 중지됩니다.

1. [!DNL Experience Manager] 인터페이스에서 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다. The **[!UICONTROL Metadata Schema Forms]** page is displayed.
1. 기본 메타데이터 양식과 같은 양식 앞에 있는 확인란을 선택하고 **[!UICONTROL 복사]**&#x200B;를 클릭하여 사용자 지정 양식으로 저장합니다. 양식에 대한 사용자 지정 이름(예: `my_default`)을 지정하십시오. 또는 사용자 정의 양식을 만들 수 있습니다.

1. **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에서 `my_default` 양식을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 메타데이터 스키마 편집기]** 페이지에서 스키마 양식에 텍스트 필드를 추가합니다. 예를 들어 레이블이 **[!UICONTROL Category]**&#x200B;인 필드를 추가합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정된 양식이 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에 나열됩니다.
1. 사용자 지정 메타데이터를 폴더에 적용하려면 도구 모음에서 **[!UICONTROL 폴더에 적용]**&#x200B;을 선택합니다.
1. 수정된 스키마를 적용할 폴더를 선택한 다음 **[!UICONTROL 적용]**&#x200B;을 선택합니다.
1. 폴더에 다른 메타데이터 스키마가 적용된 경우 기존 메타데이터 스키마를 덮어쓰려고 한다는 경고 메시지가 나타납니다. **덮어쓰기**&#x200B;를 클릭합니다.
1. 성공 메시지를 닫으려면 **확인**&#x200B;을 클릭하세요.
1. 수정된 메타데이터 스키마를 적용한 폴더로 이동합니다.

## 필수 메타데이터 정의 {#defining-mandatory-metadata}

폴더에 업로드된 에셋에 적용되는 폴더 수준에서 필수 필드를 정의할 수 있습니다. 앞에서 정의한 필수 필드에 대해 누락된 메타데이터가 있는 에셋을 업로드하면 누락된 메타데이터에 대한 시각적 표시가 카드 보기의 에셋에 나타납니다.

>[!NOTE]
>
>메타데이터 필드는 다른 필드의 값을 기반으로 필수로 정의할 수 있습니다. 카드 보기에서 Experience Manager은 이러한 필수 메타데이터 필드에 대한 메타데이터 누락에 대한 경고 메시지를 표시하지 않습니다.

1. Experience Manager 로고를 클릭한 다음 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다. The **[!UICONTROL Metadata Schema Forms]** page is displayed.
1. 기본 메타데이터 양식을 사용자 정의 양식으로 저장합니다. 예를 들어 `my_default`(으)로 저장합니다.
1. 사용자 정의 양식을 편집합니다. 필수 필드를 추가합니다. 예를 들어 **[!UICONTROL Category]** 필드를 추가하고 필드를 필수 항목으로 만듭니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정된 양식이 **[!UICONTROL 메타데이터 스키마 Forms]** 페이지에 나열됩니다. 양식을 선택한 다음 도구 모음에서 **[!UICONTROL 폴더에 적용]**&#x200B;을 선택하여 폴더에 사용자 지정 메타데이터를 적용합니다.
1. 폴더로 이동하고 사용자 정의 양식에 추가한 필수 필드에 대해 메타데이터가 누락된 일부 에셋을 업로드합니다. 필수 필드의 누락된 메타데이터에 대한 메시지가 에셋의 카드 보기에 표시됩니다.
1. (선택 사항) `https://[server]:[port]/system/console/components/`에 액세스합니다. 기본적으로 사용하지 않도록 설정된 `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` 구성 요소를 구성하고 사용하도록 설정합니다. Experience Manager이 에셋에 대한 메타데이터의 유효성을 확인하는 빈도를 설정하십시오.

   이 구성은 자산 `jcr:content`에 속성 `hasValidMetadata`을(를) 추가합니다. 이 속성을 사용하면 Experience Manager이 검색 결과를 필터링할 수 있습니다.

   >[!NOTE]
   >
   >예약된 검사 후에 자산이 추가되면 다음 예약된 검사까지 자산에 `hasValidMetadata` 플래그가 지정되지 않습니다. 자산이 중간 검색 결과에 표시되지 않습니다.

   >[!CAUTION]
   >
   >메타데이터 유효성 검사는 리소스를 많이 사용하며 시스템 성능에 영향을 줄 수 있습니다. 그에 따라 검사를 예약합니다. 서버가 부하를 처리할 수 없는 경우 이 작업을 비활성화하십시오

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)