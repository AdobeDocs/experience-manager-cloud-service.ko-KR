---
title: 메타데이터 관리
seo-title: Manage [!DNL AEM Forms] metadata
description: 메타데이터를 사용하면 자산을 보다 쉽게 분류하고 구성할 수 있으며 특정 자산을 찾는 사용자를 지원합니다.
seo-description: Metadata allows for easier categorization and organization of assets and helps users who are looking for a specific asset.
exl-id: 8527246a-37f0-4d43-a49e-1c76c265514e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1660'
ht-degree: 2%

---

# 적응형 양식의 메타데이터 추가, 제거 또는 편집 {#manage-form-metadata}

메타데이터를 사용하면 자산을 보다 쉽게 분류하고 구성할 수 있으며 특정 자산을 찾는 사용자를 지원합니다.

[!DNL AEM Forms]기본적으로 각 자산 유형에 대해 정의된 메타데이터 세트를 제공합니다. 기본 메타데이터 외에도 각 자산 유형에 사용자 지정 메타데이터를 추가할 수 있습니다. [!DNL AEM Forms] 또한 양식을 위해 이 모든 메타데이터를 효율적으로 생성, 관리 및 교환할 수 있는 올바른 방법을 제공합니다.

<!-- If you're a developer or a site owner, you can customize Forms Portal, the end-user interface for [!DNL AEM Forms] to reflect the metadata you're using in your organization. For more information abouts Forms Portal, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md). -->

## 의 메타데이터 [!DNL AEM Forms] {#metadata-in-aem-forms}

in [!DNL AEM Forms], 자산과 연결된 메타데이터 속성 목록은 해당 유형에 따라 다릅니다. 또한 사용자 지정 메타데이터 속성을 추가하면 사용자 지정 메타데이터가 추가된 유형의 모든 자산에 추가됩니다.

### 자산 유형 {#asset-types}

다음 자산 유형은에서 지원됩니다. [!DNL AEM Forms]:

* 양식 템플릿(XFA 양식)
* PDF forms
* 문서(플랫 PDF)
* 적응형 양식
* Forms 데이터 모델
* XFS

#### 광범위한 메타데이터 목록 {#extensive-list-of-metadata}

다음은 에서 지원되는 광범위한 메타데이터 속성 목록입니다 [!DNL AEM Forms]:

<table>
 <tbody> 
  <tr> 
   <td><strong>속성 이름</strong></td> 
   <td><strong>자산 유형</strong></td> 
   <td><strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>제목</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>자산의 이름을 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>설명</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>자산에 대한 설명입니다. 사용자는 이 값을 지정할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td>유형</td> 
   <td>모든</td> 
   <td><p>자산 유형을 지정하는 읽기 전용 값입니다. 다음 값 중 하나를 보유할 수 있습니다.</p> 
    <ul> 
     <li>양식 템플릿</li> 
     <li>PDF 양식, PDF 양식(Acroform) 또는 PDF 양식(서명됨)</li> 
     <li>문서, 문서(서명됨)</li> 
     <li>적응형 양식</li> 
     <li>양식 데이터 모델</li>
     <li>리소스</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>작성일</td> 
   <td>모든</td> 
   <td>자산 생성 시간을 지정하는 읽기 전용 값입니다.</td> 
  </tr> 
  <tr> 
   <td>마지막 수정 날짜</td> 
   <td>모든</td> 
   <td>자산을 마지막으로 수정한 시간을 지정하는 읽기 전용 값입니다.</td> 
  </tr> 
  <tr> 
   <td>작성</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td><p>양식 유형에 따라 자동으로 계산되는 읽기 전용 값입니다.</p> 
    <ul> 
     <li>PDF/양식 템플릿/문서 - 업로드된 이진 파일에서 가져옵니다.</li> 
     <li>적응형 양식 - 양식을 만들 때 로그인한 사용자입니다.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>상태</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td><p> 양식의 다음 상태 중 하나를 정의하는 읽기 전용 값입니다.</p> 
    <ul> 
     <li>값 없음: 양식이 게시되지 않은 경우</li> 
     <li>게시됨: 양식을 게시할 때.</li> 
     <li>수정됨: 한 번 게시한 후 양식을 수정한 경우</li> 
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
   <td><p>양식을 자동으로 게시/게시 취소하도록 예약하는 시간입니다. 사용자는 메타데이터 편집에서 이 값을 설정합니다.</p> 
    <ul> 
     <li>게시 설정 및 해제 시간은 모두 현재 날짜를 초과해야 합니다. </li> 
     <li>게시 해제 시간은 게시 설정 시간 이후여야 합니다. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>제출 URL</td> 
   <td><p>양식 템플릿</p> <p>PDF 양식</p> </td> 
   <td><p>양식 데이터를 서블릿에 제출하기 위해 사용자가 지정한 URL을 구성하려면</p> <p>제출 URL은 우선순위 순서로 나열된 다음 방법 중 하나를 사용하여 구성할 수 있습니다.</p> 
    <ul> 
     <li>AEM Forms 디자이너에서 XFA 양식을 만드는 동안 HTTP 제출 단추를 사용하여 양식 템플릿에서 직접 제출 URL을 지정합니다.</li> 
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
    </ul> <p>이 옵션은 최종 사용자가 볼 수 있는 forms 포털에서만 양식의 렌더링 형식을 제한하는 데 사용됩니다.</p> </td> 
  </tr> 
  <tr> 
   <td>태그</td> 
   <td>리소스를 제외한 모든 항목</td> 
   <td>빠르고 쉽게 검색할 수 있도록 양식에 연결된 레이블입니다.</td> 
  </tr> 
  <tr> 
   <td>참조</td> 
   <td><p>적응형 양식</p> <p>양식 템플릿</p> <p>리소스</p> </td> 
   <td><p>이 양식과 관련된 자산(다른 양식 또는 리소스) 목록입니다. 이러한 자산은 다음 두 가지 카테고리에 포함될 수 있습니다.</p> 
    <ul> 
     <li>참조: 현재 양식이 참조하는 자산입니다.</li> 
     <li>참조: 현재 자산을 참조하는 자산.</li> 
    </ul> <p>이러한 자산은 링크로 표시되며, 이 자산을 클릭하여 해당 메타데이터에 직접 액세스할 수 있습니다.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>양식 모델(XDP/XSD) 선택</td> 
   <td>적응형 양식</td> 
   <td><p>적응형 양식을 작성하는 동안 사용할 양식 모델을 지정합니다. 이 속성에는 다음 값이 있을 수 있습니다.</p> 
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

자산에는 기존 속성 값이 있으며, 이 값은 읽기 전용 모드로 볼 수 있습니다. 이 메타데이터는 양식 업로드 또는 양식 작성 시 생성됩니다.

1. 메타데이터를 볼 자산의 위치로 이동합니다.

1. 다음 방법 중 하나를 사용하여 속성 페이지를 엽니다.

   * 을(를) 클릭합니다. **[!UICONTROL 속성]** ![속성](assets/Smock_Info_18_N.svg) ( 빠른 작업)의 아이콘을 사용하여 작업을 수행할 수 있습니다.

      >[!NOTE]
      >
      >빠른 작업은 마우스로 가리키면 축소판 위에 표시되는 작업 항목입니다.

   * 양식을 선택하고 **[!UICONTROL 속성]** ![속성](assets/Smock_Info_18_N.svg) 도구 모음에 표시되는 아이콘입니다.
   * 선택 모드에 있지 않은 경우 양식 섬네일을 클릭하여 양식 세부 사항 페이지로 이동합니다. 이제 ![속성](assets/Smock_Info_18_N.svg) 오른쪽 상단의 눈 아이콘을 클릭한 다음 아래 목록에서 속성 을 클릭합니다.

1. 열리는 속성 페이지에는 일부 값이 있는 메타데이터 속성만 들어 있는 스키마가 표시됩니다.

   <!-- The properties page has a toolbar containing two action icons:

    * Edit: ![Edit](assets/Smock_Edit_18_N.svg) Edit the metadata property values
    * View: ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) Navigate to the form details page, which opens the form in the preview mode. -->

   컨텐츠 부분은 다음 두 부분으로 나누어집니다.

   * 왼쪽 패널에는 양식의 축소판이 포함되어 있습니다
   * 오른쪽 패널에는 다양한 탭에 분산되어 있는 읽기 전용 모드의 메타데이터 속성이 있습니다.

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

### 양식 축소판 업데이트 {#update-the-form-thumbnail}

속성 페이지의 왼쪽 패널에 양식의 축소판이 표시됩니다. 기본적으로 표시되는 축소판은 양식을 만들 때(적응형 양식) 또는 양식 업로드 시 생성되는 축소판입니다.

모든 양식 유형의 경우, **[!UICONTROL 이미지 업로드]** 로컬 디렉토리에서 이미지 파일을 검색하는 중입니다. 선택한 이미지가 기본 이미지가 아닌 축소판으로 사용됩니다.

적응형 Forms의 경우 사용자가 현재 적응형 양식 미리 보기의 스냅숏으로 축소판을 생성할 수 있는 추가 기능이 제공됩니다. 이후 [!DNL AEM Forms] 또한 응용 Forms 작성을 지원합니다. 적응형 양식을 변경할 때마다 적응형 양식의 미리 보기가 변경될 수 있습니다. 축소판을 생성하는 이 기능은 현재 미리 보기 상태에 따라 적응형 양식의 새 축소판을 가져오는 데 도움이 됩니다. 클릭 **[!UICONTROL 미리 보기 생성]** 를 클릭하여 이 작업을 수행합니다.

>[!NOTE]
>
>* 축소판에 사각형 이미지를 사용합니다. 사각형이 아닌 이미지를 사용하고 목록 보기에서 축소판을 보면 축소판이 잘림으로 나타납니다.
>* 새 이미지를 업로드하거나 생성한 후에는 축소판이 이 이미지로 대체되며 이전 이미지로 재설정할 수 없습니다.

>


## 사용자 지정 메타데이터 추가 {#add-custom-metadata}

즉시 제공되는 메타데이터와는 별도로 [!DNL AEM Forms] 는 새 사용자 지정 메타데이터를 지원합니다.

메타데이터 레이아웃에 대한 스키마를 정의하기 위한 도구(메타데이터 스키마 편집기)가 제공됩니다. 즉, **[!UICONTROL 속성]** 한 페이지의 데이터를 채우는 방법을 설명합니다. 메타데이터 스키마 편집기를 사용하면 자산에 대한 사용자 지정 스키마를 추가 또는 수정할 수 있습니다.

[!DNL AEM Forms] 이 도구에서 지원되는 양식 유형의 메타데이터 스키마를 표시합니다. 이러한 방법으로 이러한 스키마에 액세스하고 메타데이터 스키마 편집기에 제공된 기능을 사용하여 사용자 지정 속성을 추가할 수 있습니다.

### 메타데이터 스키마 편집기 탐색 {#navigate-the-metadata-schema-editor}

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 메타데이터 스키마]**.

1. 클릭 **[!UICONTROL forms]** 나열된 스키마 양식에서 생성합니다.

1. 열리는 목록에서 사용자 지정 메타데이터를 추가할 자산 유형을 클릭합니다.

   >[!NOTE]
   >
   >이러한 스키마에는 즉시 제공되는 메타데이터 속성이 포함되어 있으며, 기능 문제를 방지하기 위해 변경/편집하지 않아야 합니다(확인란을 선택하고 도구 모음에서 편집 클릭).

1. 클릭한 자산 유형은 `extendedmetadata` 선택 사항입니다. 이 스키마를 편집합니다.

1. 옆의 확인란을 선택합니다 `extendedmetadata` 그런 다음 편집 ![편집](assets/Smock_Edit_18_N.svg) 도구 모음에 표시되는 아이콘입니다.

1. [!DNL AEM Forms] 선택한 자산 유형의 메타데이터 스키마 편집기/양식 빌더를 엽니다(이 경우 적응형 양식).

   메타데이터 편집기

   1. 왼쪽 패널에는 필드가 배치되는 탭 섹션과 오른쪽 패널에 사용 가능한 모든 UI 구성 요소와 왼쪽 패널에서 선택한 필드의 속성이 표시됩니다.

   1. 잠긴 섹션은 편집할 수 없으며 즉시 제공되는 모든 메타데이터 속성에 대한 필드를 포함합니다.

   1. + 기호를 클릭하여 탭을 추가할 수 있습니다.

   1. 필드 구성 요소를 **[!UICONTROL 양식 작성]** 스키마 페이지의 섹션을 참조하십시오.
   1. 이 필드에 대한 사양은 **[!UICONTROL 설정]** 섹션을 클릭합니다.

### 스키마 편집기에서 사용자 지정 메타데이터 속성 추가 {#add-custom-metadata-property-in-schema-editor}

1. 사용자 지정 속성을 추가할 탭(기존 또는 신규)으로 이동합니다.

1. 원하는 유형의 구성 요소를 **[!UICONTROL 양식 작성]** 섹션을 왼쪽 패널로 이동하여 편리한 위치에 배치합니다.

   >[!NOTE]
   >
   >잠긴 섹션은 이동할 수 없지만 구성 요소를 빈 공간에 배치할 수 있습니다.

1. 방금 드래그한 구성 요소를 클릭합니다. 오른쪽 패널에 열리는 설정 탭에서 다음 필드에 대한 정보를 입력합니다.

   1. 스키마에 배치된 필드 위에 표시 이름으로 사용할 필드 레이블을 지정합니다(예: 부서)
   1. 속성에 매핑 필드에서 미리 채워진 값을 확인할 수 있습니다 **&#39;/jcr:content/metadata/default&#39;**. &#39; 변경&#x200B;**기본**` 를 crx 저장소에 속성을 저장하는 데 사용되는 원하는 속성 이름으로 이동합니다(예: &#39;/jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >접두사 &#39;./jcr:content/metadata/&#39;는 속성이 저장되는 경로를 정의합니다.
      >
      >또한 저장소의 동일한 위치에 두 개 이상의 속성에 대한 값을 작성하지 않으려면 속성 이름이 고유해야 합니다. 따라서 &#39;default&#39; 값을 변경하는 것이 좋습니다.

   1. 요구 사항에 따라 다른 설정을 입력합니다. 예: 필드를 필수로 만들려면 필수 옵션을 선택합니다.
   1. 추가한 필드를 삭제하려면 필드를 선택한 다음 삭제를 클릭합니다 ![삭제](assets/Smock_Delete_18_N.svg) 아이콘.

1. 필요한 경우 1-3단계에 따라 다른 속성을 추가합니다.
1. 클릭 **[!UICONTROL 저장]** 모든 변경 작업을 수행한 후.

   사용자 지정 메타데이터 속성을 추가했습니다.

의 모든 적응형 Forms [!DNL AEM Forms] 이제 이 추가 메타데이터 속성을 포함합니다. 속성 페이지에서 편집할 수 있습니다.
