---
title: 메타데이터 관리
seo-title: Manage [!DNL AEM Forms] metadata
description: 메타데이터를 사용하면 에셋을 보다 쉽게 분류하고 구성할 수 있으며 특정 에셋을 찾는 사용자에게 도움이 됩니다.
seo-description: Metadata allows for easier categorization and organization of assets and helps users who are looking for a specific asset.
exl-id: 8527246a-37f0-4d43-a49e-1c76c265514e
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '1658'
ht-degree: 2%

---

# 적응형 양식의 메타데이터 추가, 제거 또는 편집 {#manage-form-metadata}

메타데이터를 사용하면 에셋을 보다 쉽게 분류하고 구성할 수 있으며 특정 에셋을 찾는 사용자에게 도움이 됩니다.

[!DNL AEM Forms]는 기본적으로 각 에셋 유형에 대해 정의된 메타데이터 세트를 제공합니다. 기본 메타데이터 외에도 각 에셋 유형에 사용자 지정 메타데이터를 추가할 수 있습니다. [!DNL AEM Forms] 또한 에서는 양식에 대해 이러한 모든 메타데이터를 효율적으로 생성, 관리 및 교환할 수 있는 적절한 수단을 제공합니다.

<!-- If you are a developer or a site owner, you can customize Forms Portal, the end-user interface for [!DNL AEM Forms] to reflect the metadata you are using in your organization. For more information abouts Forms Portal, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md). -->

## [!DNL AEM Forms]의 메타데이터 {#metadata-in-aem-forms}

위치 [!DNL AEM Forms]: 에셋과 연결된 메타데이터 속성 목록은 에셋의 유형에 따라 다릅니다. 또한 사용자 지정 메타데이터 속성을 추가하면 해당 사용자 지정 메타데이터가 추가된 유형의 모든 에셋에 추가됩니다.

### 자산 유형 {#asset-types}

지원되는 자산 유형은 다음과 같습니다 [!DNL AEM Forms]:

* 양식 템플릿(XFA 양식)
* PDF forms
* 문서(플랫 PDF)
* 적응형 양식
* Forms 데이터 모델
* XFS

#### 광범위한 메타데이터 목록 {#extensive-list-of-metadata}

다음은에서 지원되는 메타데이터 속성의 광범위한 목록입니다 [!DNL AEM Forms]:

<table>
 <tbody> 
  <tr> 
   <td><strong>속성 이름</strong></td> 
   <td><strong>에셋 유형</strong></td> 
   <td><strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>제목</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>에셋의 표시 이름입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>에셋에 대한 설명. 사용자는 이 값을 지정할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>유형</td> 
   <td>모두</td> 
   <td><p>에셋 유형을 지정하는 읽기 전용 값입니다. 다음 값 중 하나를 가질 수 있습니다.</p> 
    <ul> 
     <li>양식 템플릿</li> 
     <li>PDF 양식, PDF 양식(Acroform) 또는 PDF 양식(Signed)</li> 
     <li>문서, 문서(서명됨)</li> 
     <li>적응형 양식</li> 
     <li>양식 데이터 모델</li>
     <li>리소스</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>작성일</td> 
   <td>모두</td> 
   <td>에셋 생성 시간을 지정하는 읽기 전용 값입니다.</td> 
  </tr> 
  <tr> 
   <td>마지막 수정 날짜</td> 
   <td>모두</td> 
   <td>에셋을 마지막으로 수정한 시간을 지정하는 읽기 전용 값입니다.</td> 
  </tr> 
  <tr> 
   <td>작성자</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td><p>양식 유형에 따라 자동으로 계산되는 읽기 전용 값입니다.</p> 
    <ul> 
     <li>PDF/양식 템플릿/문서 - 업로드된 이진 파일에서 가져옵니다.</li> 
     <li>적응형 양식 - 양식 작성 시 로그인한 사용자</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>상태</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td><p> 양식의 다음 상태 중 하나를 정의하는 읽기 전용 값입니다.</p> 
    <ul> 
     <li>값 없음: 양식이 게시된 적이 없는 경우.</li> 
     <li>게시됨: 양식이 게시될 때.</li> 
     <li>수정됨: 한 번 게시된 후 양식이 수정된 경우.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>마지막 게시 날짜</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>양식을 마지막으로 게시한 시간을 지정하는 읽기 전용 값입니다.</td> 
  </tr> 
  <tr> 
   <td>게시 설정/해제 시간</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td><p>양식이 자동으로 게시/게시 취소되도록 예약된 시간입니다. 사용자가 메타데이터 편집 시 이 값을 설정합니다.</p> 
    <ul> 
     <li>게시 켜기 및 끄기 시간은 모두 현재 날짜 이후여야 합니다. </li> 
     <li>게시 해제 시간은 게시 설정 시간 이후여야 합니다. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>URL 제출</td> 
   <td><p>양식 템플릿</p> <p>PDF 양식</p> </td> 
   <td><p>양식 데이터를 서블릿에 제출하기 위해 사용자 지정 URL을 구성하려면 다음 작업을 수행하십시오.</p> <p>제출 URL은 우선순위 순서로 나열된 다음 방법 중 하나를 사용하여 구성할 수 있습니다.</p> 
    <ul> 
     <li>AEM Forms Designer에서 XFA 양식을 만들 때 HTTP 제출 단추를 사용하여 양식 템플릿에서 직접 제출 URL을 지정합니다.</li> 
     <li>AEM Forms UI에서 양식을 선택하고 메타데이터 속성 편집 시 제출 URL을 지정합니다.</li> 
     <!-- <li>In Forms Portal, edit the Search &amp; Lister component and specify a submit URL under the Form Link tab.</li> -->
    </ul> </td> 
  </tr> 
  <tr> 
   <td>HTML 렌더링 프로필</td> 
   <td>양식 템플릿</td> 
   <td>양식 템플릿을 HTML 형식으로 렌더링하는 동안 사용되는 HTML 렌더링 프로필입니다.</td> 
  </tr> 
  <tr> 
   <td>렌더링 형식</td> 
   <td><p>양식 템플릿</p> <p>적응형 양식</p> </td> 
   <td><p>이 옵션을 사용하면 양식을 게시할 때 양식의 렌더링 형식을 지정할 수 있습니다.</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>모두</li> 
    </ul> <p>이 옵션은 최종 사용자가 볼 수 있는 Forms 포털에서만 양식의 렌더링 형식을 제한하는 데 사용됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>태그</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>빠르고 간편한 검색을 위해 양식과 관련된 레이블입니다.</td> 
  </tr> 
  <tr> 
   <td>참조</td> 
   <td><p>적응형 양식</p> <p>양식 템플릿</p> <p>리소스</p> </td> 
   <td><p>이 양식과 관련된 에셋(기타 양식 또는 리소스) 목록입니다. 이러한 에셋은 다음 두 가지 카테고리에 속할 수 있습니다.</p> 
    <ul> 
     <li>참조: 현재 양식이 참조하는 에셋입니다.</li> 
     <li>참조: 현재 자산을 참조하는 자산.</li> 
    </ul> <p>이러한 에셋은 링크로 표시되며, 해당 에셋을 클릭하면 해당 메타데이터에 직접 액세스할 수 있습니다.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>양식 모델(XDP/XSD) 선택</td> 
   <td>적응형 양식</td> 
   <td><p>적응형 양식을 작성하는 동안 사용할 양식 모델을 지정합니다. 이 속성은 다음 값을 가질 수 있습니다.</p> 
    <ul> 
      <li>양식 데이터 모델 </li>
      <li>스키마: JSON 스키마의 XML</li>
     <!-- <li>Form template: A form template is selected from the ones existing in the repository. This value can be updated.</li> 
     <li>XML schema: An XSD file is uploaded. This value can be updated.</li> -->
     <li>없음</li> 
    </ul> 
    <div>
      선택한 양식 모델은 업데이트할 수 있지만 제거할 수는 없습니다. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## 양식 메타데이터 보기 {#view-form-metadata}

자산에는 읽기 전용 모드에서 볼 수 있는 기존 속성 값이 있습니다. 이 메타데이터는 양식 업로드 또는 양식 생성 시 생성됩니다.

1. 메타데이터를 보려는 에셋의 위치로 이동합니다.

1. 다음 방법 중 하나를 사용하여 속성 페이지를 엽니다.

   * 다음을 클릭합니다. **[!UICONTROL 속성]** ![속성](assets/Smock_Info_18_N.svg) 아이콘을 클릭합니다.

     >[!NOTE]
     >
     >빠른 작업은 마우스를 가져가면 썸네일 위에 표시되는 작업 항목입니다.

   * 양식을 선택하고 **[!UICONTROL 속성]** ![속성](assets/Smock_Info_18_N.svg) 아이콘: 도구 모음에 표시됩니다.
   * 선택 모드에 있지 않을 때 양식 썸네일을 클릭하여 양식 세부 정보 페이지로 이동합니다. 이제 ![속성](assets/Smock_Info_18_N.svg) 오른쪽 상단에 있는 눈 모양 아이콘을 클릭한 다음 아래 목록에서 속성 을 클릭합니다.

1. 열리는 속성 페이지에는 일부 값을 포함하는 메타데이터 속성만 포함된 스키마가 표시됩니다.

   <!-- The properties page has a toolbar containing two action icons:

    * Edit: ![Edit](assets/Smock_Edit_18_N.svg) Edit the metadata property values
    * View: ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) Navigate to the form details page, which opens the form in the preview mode. -->

   콘텐츠 부분은 두 부분으로 나뉘어져 있습니다.

   * 왼쪽 패널에 양식의 축소판이 포함됨
   * 오른쪽 패널에는 여러 탭에 분산되어 있는 읽기 전용 모드의 메타데이터 속성이 포함되어 있습니다.

## 양식 메타데이터 값 추가/업데이트 {#add-update-form-metadata-values}

기존 메타데이터 속성의 값을 편집하거나 기존 메타데이터 속성 필드에 새 값을 추가할 수 있습니다(예: 메타데이터 필드가 비어 있는 경우).

<!-- ### Update metadata property values {#update-metadata-property-values}

1. Follow the steps mentioned in the previous section to open the properties page where existing metadata of the selected form can be viewed.  

1. From the toolbar, click the Edit icon ![Edit](assets/Smock_Edit_18_N.svg) to change the mode of the page from read-only to read/write.  

1. The properties page that opens holds a schema that contains a mix of editable input fields and static text.  

1. The properties displayed in static text are the ones that you cannot edit.  

1. You can navigate to other tabs to find input fields for metadata properties placed under them.

   This page has a toolbar containing two action icons different from those in view mode:

    * Cancel: ![aem6forms_close](assets/aem6forms_close.svg_w24.png) Cancel any changes made to metadata property values so far
    * Done: ![aem6forms_check](assets/aem6forms_check.png) Save all the changes made to metadata property values so far

   Both these actions direct the user back to read-only mode of the properties page containing the updated values.-->

### 양식 썸네일 업데이트 {#update-the-form-thumbnail}

속성 페이지의 왼쪽 패널에 양식의 썸네일이 표시됩니다. 기본적으로 표시되는 축소판은 양식 작성 시(적응형 양식) 또는 양식 업로드 시 생성된 축소판입니다.

모든 양식 유형의 경우 다음을 클릭하여 이미지를 업로드할 수 있습니다. **[!UICONTROL 이미지 업로드]** 로컬 디렉토리에서 이미지 파일을 검색하는 중입니다. 선택한 이미지가 기본 이미지가 아닌 썸네일로 사용됩니다.

적응형 Forms의 경우 사용자가 현재 적응형 양식 미리 보기의 스냅숏으로 썸네일을 생성할 수 있는 추가 기능이 제공됩니다. 다음 이후 [!DNL AEM Forms] 또한 적응형 Forms 작성을 지원합니다. 적응형 양식은 적응형 양식을 변경할 때마다 미리 보기가 변경될 수 있습니다. 이 썸네일 생성 기능을 사용하면 현재 미리보기 상태를 기반으로 적응형 양식에 대한 최신 썸네일을 가져올 수 있습니다. 클릭 **[!UICONTROL 미리보기 생성]** 을 클릭하여 이 작업을 수행하십시오.

>[!NOTE]
>
>* 썸네일에 사각형 이미지를 사용합니다. 정사각형이 아닌 이미지를 사용하고 목록 보기에서 축소판을 보면 축소판이 잘린 상태로 나타납니다.
>* 새 이미지가 업로드되거나 생성되면 썸네일이 이 이미지로 대체되며 이전 이미지로 재설정할 수 없습니다.
>

## 사용자 지정 메타데이터 추가 {#add-custom-metadata}

기본 제공되는 메타데이터 외에도 [!DNL AEM Forms] 는 새 사용자 지정 메타데이터를 지원합니다.

메타데이터 레이아웃(에 표시되는 레이아웃)에 대한 스키마를 정의하는 도구(메타데이터 스키마 편집기)가 제공됩니다. **[!UICONTROL 속성]** 양식의 페이지입니다. 메타데이터 스키마 편집기를 사용하면 에셋에 대한 사용자 지정 스키마를 추가하거나 수정할 수 있습니다.

[!DNL AEM Forms] 은 이 도구에서 지원되는 양식 유형의 메타데이터 스키마를 노출합니다. 이렇게 하면 이러한 스키마에 액세스하고 메타데이터 스키마 편집기에 제공된 기능을 사용하여 사용자 지정 속성을 추가할 수 있습니다.

### 메타데이터 스키마 편집기 탐색 {#navigate-the-metadata-schema-editor}

1. 다음으로 이동 **[!UICONTROL 도구 > 에셋 > 메타데이터 스키마]**.

1. 클릭 **[!UICONTROL 양식]** 나열된 스키마 양식.

1. 열리는 목록에서 사용자 지정 메타데이터를 추가할 에셋 유형을 클릭합니다.

   >[!NOTE]
   >
   >이러한 스키마에는 즉시 제공되는 메타데이터 속성이 포함되어 있으며 기능 문제를 방지하기 위해 확인란을 선택하고 도구 모음에서 편집을 클릭하여 변경/편집해서는 안 됩니다.

1. 클릭한 모든 에셋 유형은 `extendedmetadata` 옵션을 선택합니다. 이 스키마를 편집합니다.

1. 옆에 있는 확인란을 선택합니다. `extendedmetadata` 그런 다음 편집을 클릭합니다 ![편집](assets/Smock_Edit_18_N.svg) 아이콘: 도구 모음에 표시됩니다.

1. [!DNL AEM Forms] 선택한 에셋 유형(이 경우 적응형 양식)의 메타데이터 스키마 편집기/양식 빌더를 엽니다.

   메타데이터 편집기

   1. 왼쪽 패널에는 필드가 배치되는 탭 섹션이 있으며 오른쪽 패널에는 사용 가능한 모든 UI 구성 요소와 왼쪽 패널에서 선택한 필드의 속성이 표시됩니다.

   1. 잠긴 섹션은 편집할 수 없으며 즉시 제공되는 모든 메타데이터 속성에 대한 필드를 포함합니다.

   1. + 기호를 클릭하여 탭을 더 추가할 수 있습니다.

   1. 에서 필드 구성 요소를 끌어 원하는 유형의 사용자 정의 필드를 추가할 수 있습니다. **[!UICONTROL 양식 작성]** 섹션에 대해 설명합니다.
   1. 이 필드에 대한 사양은 아래에 제공됩니다. **[!UICONTROL 설정]** 섹션을 만드십시오.

### 스키마 편집기에서 사용자 지정 메타데이터 속성 추가 {#add-custom-metadata-property-in-schema-editor}

1. 사용자 지정 속성을 추가할 탭(기존 또는 신규)으로 이동합니다.

1. 에서 원하는 유형의 구성 요소를 드래그합니다. **[!UICONTROL 양식 작성]** 왼쪽 패널에 정렬하여 편리한 위치에 배치합니다.

   >[!NOTE]
   >
   >잠긴 섹션은 이동할 수 없지만 구성 요소를 빈 공간에 배치할 수 있습니다.

1. 방금 드래그한 구성 요소를 클릭합니다. 오른쪽 패널에 열리는 설정 탭에서 다음 필드에 대한 정보를 입력합니다.

   1. 스키마에 배치된 필드 위에 표시 이름으로 사용할 필드 레이블 지정(예: 부서)
   1. 속성에 매핑 필드에서 미리 채워진 값을 볼 수 있습니다 **&#39;./jcr:content/metadata/default&#39;**. &#39; 변경&#x200B;**기본값** crx 저장소에 속성을 저장하는 데 사용되는 원하는 속성 이름으로 &#39; &#39;를 입력합니다(예: &#39;)./jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >접두사 &#39;(을)를 변경하지 마십시오./jcr:content/metadata/&#39; 속성을 저장하는 경로를 정의합니다.
      >
      >또한 저장소의 동일한 위치에 두 개 이상의 속성에 대한 값을 쓰지 않도록 하려면 속성 이름이 고유해야 합니다. 따라서 &#39;default&#39; 값을 변경하는 것이 좋습니다.

   1. 요구 사항에 따라 다른 설정을 채웁니다. 예를 들어 필드를 필수 항목으로 만들려면 필수 옵션을 선택합니다.
   1. 추가한 필드를 삭제하려면 필드를 선택한 다음 삭제를 클릭합니다 ![삭제](assets/Smock_Delete_18_N.svg) 아이콘.

1. 필요한 경우 1-3단계에 따라 다른 속성을 추가합니다.
1. 클릭 **[!UICONTROL 저장]** 모든 변경 작업을 수행한 후에

   사용자 지정 메타데이터 속성을 추가했습니다.

의 모든 적응형 Forms [!DNL AEM Forms] 이제 이 추가 메타데이터 속성을 포함합니다. 속성 페이지에서 편집할 수 있습니다.
