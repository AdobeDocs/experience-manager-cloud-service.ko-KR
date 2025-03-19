---
title: WYSIWYG 기반 작성을 위한 양식 조각을 만드는 방법
description: 범용 편집기에서 양식 조각을 만들어 양식에 추가하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, User, Developer
hide: true
hidefromtoc: true
source-git-commit: 62c58ceb2d2d659bad591b3eba1bfd924f2a848b
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 8%

---


# 범용 편집기에서 Edge Delivery Services 양식 조각 만들기 및 사용

Forms에는 연락처 정보, 식별 세부 정보 또는 동의 계약과 같은 일반적인 섹션이 포함되어 있는 경우가 많습니다. 양식 개발자는 새 양식을 작성할 때마다 이러한 섹션을 만들며, 이 작업은 반복적이고 시간이 오래 걸립니다.
이러한 작업 중복을 방지하기 위해 범용 편집기는 패널 또는 필드 그룹과 같은 재사용 가능한 양식 세그먼트를 한 번만 만들어 다양한 양식에서 재사용할 수 있는 방법을 제공합니다. 이러한 재사용 가능한 모듈식 독립 세그먼트를 양식 조각이라고 합니다. 예를 들어, 직원 및 감독자 연락처 세부 정보 등 양식의 여러 섹션에서 동일한 긴급 연락처 조각을 사용할 수 있습니다.

이 문서의 마지막 부분에서는 범용 편집기를 사용하여 양식의 조각을 만들고 사용하는 방법에 대해 알아봅니다.

## Edge Delivery Services 양식 조각의 기능

* **양식 조각과 일관성 유지**
조각을 다른 양식으로 통합하여 일관된 레이아웃과 표준화된 콘텐츠를 유지하는 데 도움이 될 수 있습니다. &quot;한 번 변경, 모든 곳에 반영하기&quot; 접근 방식을 사용하면 조각에 대한 모든 업데이트가 자동으로 모든 양식에 적용됩니다.

* **양식 내에 양식 단편을 여러 번 추가**
양식 내에 양식 조각을 여러 번 추가하고 해당 데이터 바인딩 속성을 데이터 소스 또는 스키마에 구성할 수 있습니다.

* **조각 내에서 조각 사용**
중첩된 양식 조각을 만들 수 있습니다. 즉, 다른 조각에 조각을 추가할 수 있으며 중첩된 조각 구조를 가질 수 있습니다.

  >[!NOTE]
  >
  > 재귀 참조 및 의도하지 않은 비헤이비어가 발생하여 오류 또는 렌더링 문제가 발생할 수 있으므로 조각 자체를 중첩시킬 수 없습니다.

## Edge Delivery Services 양식 조각을 사용하는 동안 고려 사항

* 조각과 조각을 사용할 양식에 동일한 GitHub URL을 추가해야 합니다.
* 참조에 의해 삽입된 양식 조각은 양식 내에서 편집할 수 없습니다. 편집하려면 독립 실행형 양식 조각을 수정합니다.

## Edge Delivery Services 양식 조각을 만들기 위한 사전 요구 사항

* [GitHub 저장소를 설정](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)하여 AEM 환경과 GitHub 저장소 간의 연결을 구축합니다.
* 이미 Edge Delivery Services를 사용하고 있는 경우 최신 버전의 [적응형 양식 블록](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)을 GitHub 저장소에 추가합니다.
* AEM Forms 작성자 인스턴스에는 Edge Delivery Services 기반 템플릿이 포함됩니다. 사용자 환경에 [최신 버전의 핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)가 설치되어 있는지 확인합니다.
* AEM Forms as a Cloud Service 작성자 인스턴스 및 GitHub 저장소의 URL을 바로 사용할 수 있습니다.

## Edge Delivery Services 양식 조각을 사용한 작업

범용 편집기에서 Edge Delivery Services 양식 조각을 만들고 만든 조각을 Edge Delivery Services 양식에 추가할 수 있습니다. Edge Delivery Services 양식 조각으로 다음 작업을 수행할 수 있습니다.

* [양식 조각 만들기](#creating-form-fragments)
* [양식에 양식 단편 추가](#adding-form-fragments-to-a-form)
* [양식 조각 관리](#managing-form-fragments)

### 양식 조각 만들기

범용 편집기에서 양식 조각을 만들려면 다음 단계를 수행하십시오.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;를 선택합니다.
1. **만들기 > 적응형 양식 조각**&#x200B;을 클릭합니다.

   ![조각 만들기](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   **적응형 양식 단편 만들기** 마법사가 나타납니다.
1. **템플릿 선택** 탭에서 레거시 배달 서비스 기반 템플릿을 선택하고 **[!UICONTROL 다음]**을 클릭합니다.
   ![Edge Delivery Services 템플릿 선택](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. 조각의 제목, 이름, 설명 및 태그를 지정합니다. 조각에 고유한 이름을 지정해야 합니다. 동일한 이름의 다른 조각이 존재하는 경우 조각을 생성하지 못합니다.
1. **GitHub URL**&#x200B;을 지정합니다. 예를 들어 GitHub 리포지토리의 이름이 `edsforms`이고 `wkndforms` 계정 아래에 있는 경우 URL은 `https://github.com/wkndforms/edsforms`입니다.

   ![기본 속성](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (선택 사항) 클릭하여 **양식 모델** 탭을 열고 **다음에서 선택** 드롭다운 메뉴에서 조각에 대해 다음 모델 중 하나를 선택합니다.

   ![양식 모델 탭에 모델 유형을 표시합니다](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   * **양식 데이터 모델(FDM)**: 데이터 소스의 데이터 모델 개체와 서비스를 조각에 통합합니다. 양식에 여러 소스에서 데이터를 읽고 써야 하는 경우 양식 데이터 모델(FDM)을 선택합니다.

   * **JSON 스키마**: 데이터 구조를 정의하는 JSON 스키마를 연결하여 양식을 백엔드 시스템과 통합합니다. 스키마 요소를 사용하여 다이내믹 콘텐츠를 추가할 수 있습니다.
   * **없음**: 양식 모델을 사용하지 않고 조각을 처음부터 만들도록 지정합니다.

   >[!NOTE]
   >
   > 범용 편집기에서 양식 또는 조각을 FDM(양식 데이터 모델)과 통합하여 다양한 백엔드 데이터 소스를 사용하는 방법에 대해 알아보려면 [여기를 클릭](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)하십시오.

1. (선택 사항) **고급** 탭에서 조각에 대한 **게시 날짜** 또는 **게시 취소 날짜**&#x200B;를 지정합니다.

   ![고급 탭](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. **만들기**&#x200B;를 클릭하면 마법사가 나타납니다.

   ![조각 편집](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. **편집**&#x200B;을 클릭하면 기본 템플릿을 사용하여 만든 조각이 작성을 위해 유니버설 편집기에서 열립니다.

   ![작성을 위한 유니버설 편집기의 조각](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

   편집 모드에서는 양식 구성 요소를 조각에 추가할 수 있습니다. 유니버설 편집기에서 조각을 만드는 방법에 대해 알아보려면 [유니버설 편집기를 사용하여 Edge Delivery Services for AEM Forms 시작하기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) 문서를 참조하십시오.

   아래 스크린샷에는 유니버설 편집기에서 만든 `contact fragment`이(가) 표시됩니다.

   ![연락처 조각](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

   조각을 만든 후에는 [Edge Delivery Services Forms에서 만든 조각을 추가](#adding-form-fragments-in-forms)할 수 있습니다.

### 양식에 양식 단편 추가

직원과 감독자 정보를 모두 포함하는 간단한 `Employee Details` 양식을 만들어 보겠습니다. 직원 패널과 감독자 패널 모두에서 `Contact Details` 조각을 사용할 수 있습니다. 양식에서 양식 단편을 사용하려면 다음 단계를 수행하십시오.

1. 편집 모드로 양식을 엽니다.
1. 양식에 양식 조각 구성 요소를 추가합니다.
1. 콘텐츠 브라우저를 열고 **콘텐츠 트리**&#x200B;의 **[!UICONTROL 적응형 양식]** 구성 요소로 이동합니다.
1. 조각을 추가하려는 섹션으로 이동합니다. 예를들어 **직원 세부 정보** 패널로 이동합니다.

   ![섹션으로 이동](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 **[!UICONTROL 양식 조각]** 구성 요소를 추가합니다.
   ![양식 단편 추가](/help/edge/docs/forms/universal-editor/assets/add-fragment.png)

   **[!UICONTROL 양식 조각]** 구성 요소를 선택하면 조각이 양식에 추가됩니다. **속성**&#x200B;을 열어 추가된 조각의 속성을 구성할 수 있습니다. 예를 들어 조각의 제목을 해당 **속성**&#x200B;에서 숨깁니다.

   ![조각의 속성을 구성하는 중](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. **기본** 탭에서 **조각 참조**&#x200B;를 선택합니다. 양식의 모델에 따라 양식에 사용할 수 있는 모든 조각이 표시됩니다.

   예를 들어 `/content/forms/af`(으)로 이동하여 `Contact Details` 조각을 선택합니다.

   ![조각 선택](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. **[!UICONTROL 선택]**&#x200B;을 클릭합니다.

   양식 조각은 양식에 대한 참조로 추가되며 독립 실행형 양식 조각과 동기화된 상태로 유지됩니다. 이는 조각에 대한 수정 사항이 양식 내에 조각이 통합된 모든 인스턴스에 미러링됨을 의미합니다.

   ![양식의 조각](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   양식을 미리 보고 **미리 보기** 모드에서 나타나는 방식을 확인할 수 있습니다.

   ![미리보기](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   마찬가지로 3단계부터 7단계까지 반복하여 `Supervisor Details` 패널에 대한 `Contact Details` 조각을 삽입할 수 있습니다.

   ![직원 세부 정보 양식](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

### 양식 조각 관리

AEM Forms 사용자 인터페이스를 사용하여 양식 조각에 대해 여러 작업을 수행할 수 있습니다.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;를 선택합니다.

1. 양식 조각을 선택하면 도구 모음에 선택한 조각에서 수행할 수 있는 다음 작업이 표시됩니다.

   ![조각 관리](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

   <table>
    <tbody>
    <tr>
   <td><p><strong>작업</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
    </tr>
    <tr>
   <td><p>편집</p> </td>
   <td><p>양식 단편을 편집 모드로 엽니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>속성</p> </td>
   <td><p>양식 조각의 속성을 수정하는 옵션을 제공합니다.<br /> <br /> </p> </td>
    </tr>
    <td><p>복사</p> </td>
   <td><p> 양식 조각을 복사하여 원하는 위치에 붙여넣는 옵션을 제공합니다. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>미리보기</p> </td>
   <td><p>조각을 HTML으로 미리 보거나 XML 파일의 데이터를 조각과 병합하여 사용자 지정 미리 보기를 수행하는 옵션을 제공합니다. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>다운로드</p> </td>
   <td><p>선택한 조각을 다운로드합니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>검토 시작/검토 관리</p> </td>
   <td><p>선택한 조각의 검토를 시작하고 관리할 수 있습니다.<br /> <br /> </p> </td>
    </tr>
    <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
    </tr>-->
    <tr>
   <td><p>게시 / 게시 취소</p> </td>
   <td><p>선택한 조각을 게시/게시 취소합니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>삭제</p> </td>
   <td><p>선택한 조각을 삭제합니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>비교</p> </td>
   <td><p>미리 보기 목적으로 서로 다른 두 양식 조각을 비교합니다.<br /> <br /> </p> </td>
    </tr>
    </tbody>
    </table>

## 모범 사례

* 조각 이름이 고유한지 확인합니다. 같은 이름의 기존 조각이 있는 경우 조각을 만들 수 없습니다.
* 독립형 양식 조각의 모든 표현식, 스크립트 또는 스타일은 참조로 삽입되거나 양식에 임베드될 때 유지됩니다.
* 양식을 게시하면 양식 내에서 참조에 의해 삽입된 양식 조각이 자동으로 게시됩니다.

## 추가 참조

{{universal-editor-see-also}}