---
title: WYSIWYG 기반 작성을 위한 양식 조각을 만드는 방법
description: 범용 편집기에서 양식 조각을 만들고 양식에 추가하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, User, Developer
exl-id: 7b0d4c7f-f82f-407b-8e25-b725108f8455
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 96%

---

# 범용 편집기에서 양식 조각 만들기

<span class="preview"> 이 기능은 얼리 액세스 프로그램을 통해 사용할 수 있습니다. 액세스 권한을 요청하려면 공식 주소를 통해 GitHub 조직 이름과 저장소 이름을 포함한 이메일을 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>으로 보내 주십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc, 조직 이름이 adobe, 저장소 이름이 abc인 경우입니다.</span>

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)을 통해 액세스할 수 있습니다. </span>

양식에는 연락처 정보, 신원 정보, 동의 계약과 같은 일반적인 섹션이 포함되는 경우가 많습니다. 양식 개발자는 새로운 양식을 작성할 때마다 이러한 섹션을 만드는데, 이는 반복적이고 시간이 많이 소요되는 작업입니다.
이러한 중복 작업을 없애기 위해 범용 편집기는 패널이나 필드 그룹 등의 재사용 가능한 양식 세그먼트를 한 번만 만들어 다양한 양식에서 재사용할 수 있는 방법을 제공합니다. 이러한 재사용 가능한 모듈식 독립 세그먼트를 양식 조각이라고 합니다. 예를 들어 동일한 비상 연락처 조각을 직원 및 감독자의 연락처 정보 등 양식의 다른 섹션에서도 사용할 수 있습니다.

이 문서를 끝까지 읽으면 범용 편집기를 사용하여 양식에서 조각을 만들고 사용하는 방법을 배울 수 있습니다.

## Edge Delivery Services 양식 조각의 특징

* **양식 조각을 사용하여 일관성 유지**
조각을 다양한 양식에 통합하여 일관된 레이아웃과 표준화된 콘텐츠를 유지할 수 있습니다.

  >[!NOTE]
  >
  > 미리보기 모드에서는 “한번 변경하여 전체 반영”이라는 접근 방식을 통해 조각에 적용된 모든 업데이트가 모든 양식에 자동으로 적용됩니다. 그러나 게시 모드에서 변경 사항을 반영하려면 조각을 게시하거나 양식을 다시 게시해야 합니다.

* **양식 내에서 양식 조각을 여러 번 추가**
양식 내에서 양식 조각을 여러 번 추가하고 데이터 소스나 스키마에 대한 데이터 바인딩 속성을 구성할 수 있습니다.

* **조각 내에서 조각 사용**
중첩된 양식 조각을 만들 수 있습니다. 즉, 조각 안에 다른 조각을 추가할 수 있으며, 중첩된 조각 구조를 가질 수 있습니다.

  >[!NOTE]
  >
  > 조각을 그 자체 내에 중첩할 수는 없습니다. 순환 참조와 의도치 않은 동작을 유발하여 오류나 렌더링 문제가 발생할 수 있기 때문입니다.

## Edge Delivery Services 양식 조각 사용 시 고려 사항

* 조각과 조각을 사용하려는 양식 모두에 동일한 GitHub URL을 추가해야 합니다.
* 양식 내에서 양식 조각을 편집할 수 없습니다. 변경하려면 독립 실행형 양식 조각을 수정해야 합니다.

## 사전 요구 사항

* [GitHub 저장소를 설정](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)하여 AEM 환경과 GitHub 저장소 간의 연결을 구축합니다.
* 이미 Edge Delivery Services를 사용하고 있는 경우 최신 버전의 [적응형 양식 블록](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)을 GitHub 저장소에 추가합니다.
* AEM Forms 작성자 인스턴스에는 Edge Delivery Services 기반 템플릿이 포함됩니다.
* AEM Forms as a Cloud Service 작성자 인스턴스 및 GitHub 저장소의 URL을 바로 사용할 수 있습니다.

## Edge Delivery Services 양식 조각을 사용하여 작업

범용 편집기에서 Edge Delivery Services 양식 조각을 만들고 생성된 조각을 Edge Delivery Services 양식에 추가할 수 있습니다. Edge Delivery Services 양식 조각을 사용하면 다음 액션을 수행할 수 있습니다.

* [양식 조각 만들기](#creating-form-fragments)
* [양식에 양식 조각 추가](#adding-form-fragments-to-a-form)
* [양식 조각 관리](#managing-form-fragments)

### 양식 조각 만들기

범용 편집기에서 양식 조각을 만들려면 다음 단계를 수행합니다.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.
1. **만들기 > 적응형 양식 조각**&#x200B;을 클릭합니다.

   ![조각 만들기](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   **적응형 양식 조각 만들기** 마법사가 나타납니다.
1. **템플릿 선택**&#x200B;탭에서 Edge Delivery Services 기반 템플릿을 선택하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
   ![Edge Delivery Services 템플릿 선택](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. 조각의 제목, 이름, 설명 및 태그를 지정합니다. 조각에 고유한 이름을 지정해야 합니다. 동일한 이름의 다른 조각이 존재하는 경우 조각은 생성되지 않습니다.
1. **GitHub URL**&#x200B;을 지정합니다. 예를 들어 GitHub 저장소의 이름이 `edsforms`이고 `wkndforms` 계정 아래에 있는 경우 URL은 `https://github.com/wkndforms/edsforms`입니다.

   ![기본 속성](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (선택 사항) **양식 모델** 탭을 클릭하여 열고 **다음에서 선택** 드롭다운 메뉴에서 다음 조각 모델 중 하나를 선택합니다.

   ![양식 모델 탭에서 모델 유형 표시](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   * **양식 데이터 모델(FDM)**: 데이터 소스의 데이터 모델 오브젝트와 서비스를 조각에 통합합니다. 양식에 여러 소스의 데이터를 읽고 써야 하는 경우 양식 데이터 모델(FDM)을 선택하십시오.

   * **JSON 스키마**: 데이터 구조를 정의하는 JSON 스키마를 연결하여 양식을 백엔드 시스템과 통합합니다. 이렇게 하면 스키마 요소를 사용하여 동적 콘텐츠를 추가할 수 있습니다.
   * **없음**: 양식 모델을 사용하지 않고 처음부터 조각을 만들도록 지정합니다.

   >[!NOTE]
   >
   > 범용 편집기에서 양식 데이터 모델(FDM)과 양식 또는 조각을 통합하여 다양한 백엔드 데이터 소스를 사용하는 방법을 알아보려면 [여기를 클릭](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)하십시오.

1. (선택 사항) **고급** 탭에서 조각의 **게시 일자** 또는 **게시 취소 일자**&#x200B;를 지정합니다.

   ![고급 탭](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. **만들기**&#x200B;를 클릭하면 마법사가 나타납니다.

   ![조각 편집](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. **편집**&#x200B;을 클릭하면 기본 템플릿이 적용된 생성된 조각이 작성용 범용 편집기에서 열립니다.

   ![작성용 범용 편집기의 조각](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

   편집 모드에서는 모든 양식 구성 요소를 조각에 추가할 수 있습니다. 범용 편집기를 사용하여 조각을 만드는 방법에 대한 자세한 내용은 [범용 편집기를 사용한 AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) 문서를 참조하십시오.

   아래 스크린샷은 범용 편집기에서 생성된 `contact fragment`를 보여 줍니다.

   ![유니버설 편집기에서 이름, 전화 번호, 전자 메일 및 주소에 대한 필드를 보여주는 완료된 연락처 세부 정보 양식 조각의 스크린샷](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

   조각을 만든 후에는 [Edge Delivery Services 양식에 만든 조각을 추가](#adding-form-fragments-in-forms)할 수 있습니다.

### 양식에 양식 조각 추가

직원과 감독자 정보를 모두 포함하는 간단한 `Employee Details` 양식을 만들어 보겠습니다. 직원 및 감독자 패널 모두에서 `Contact Details` 조각을 사용할 수 있습니다. 양식에서 양식 조각을 사용하려면 다음 단계를 수행합니다.

1. 편집 모드에서 양식을 엽니다.
1. 양식에 양식 조각 구성 요소를 추가합니다.
1. 콘텐츠 브라우저를 열고 **콘텐츠 트리**&#x200B;의 **[!UICONTROL 적응형 양식]** 구성 요소로 이동합니다.
1. 조각을 추가하려는 섹션으로 이동합니다. 예를 들어 **직원 세부 정보** 패널로 이동할 수 있습니다.

   ![섹션으로 이동](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 원하는 **[!UICONTROL 양식 조각]** 구성 요소를 추가합니다.
   ![양식 조각 추가](/help/edge/docs/forms/universal-editor/assets/add-fragment.png)

   **[!UICONTROL 양식 조각]** 구성 요소를 선택하면 해당 조각이 양식에 추가됩니다. 추가된 조각의 **속성**&#x200B;을 열어 해당 속성을 구성할 수 있습니다. 예를 들어 조각의 **속성**&#x200B;에서 제목을 숨길 수 있습니다.

   ![조각 속성 구성](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. **기본** 탭에서 **조각 참조**&#x200B;를 선택합니다. 양식 모델에 따라 양식에 사용할 수 있는 모든 조각이 나타납니다.

   예를 들어 `/content/forms/af` 조각으로 이동하여 `Contact Details` 조각을 선택할 수 있습니다.

   ![조각 선택](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. **[!UICONTROL 선택]**&#x200B;을 클릭합니다.

   양식 조각은 양식에 대한 참조를 통해 추가되며 독립형 양식 조각과 동기화 상태를 유지합니다.

   ![연락처 세부 정보 조각이 유니버설 편집기 내에서 직원 양식에 성공적으로 통합되었음을 보여 주는 스크린샷으로, 조각을 다시 사용할 때 해당 구조를 유지하는 방법을 보여 줍니다.](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   **미리보기 모드**&#x200B;에서 양식을 미리 보고 양식이 어떻게 나타나는지 확인할 수 있습니다.

   ![미리보기](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   마찬가지로 3~7단계를 반복하여 `Supervisor Details` 패널에도 `Contact Details` 조각을 삽입할 수 있습니다.

   ![직원 세부 정보 양식](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

### 양식 조각 관리

AEM Forms 사용자 인터페이스를 사용하여 양식 조각에 대해 여러 작업을 수행할 수 있습니다.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

1. 양식 조각을 선택하면 다음과 같이 도구 모음에 선택한 조각에서 수행할 수 있는 작업이 표시됩니다.

   ![조각 관리](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

   <table>
    <tbody>
    <tr>
   <td><p><strong>작업</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
    </tr>
    <tr>
   <td><p>편집</p> </td>
   <td><p>편집 모드에서 양식 조각을 엽니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>속성</p> </td>
   <td><p>양식 조각의 속성을 수정할 수 있습니다.<br /> <br /> </p> </td>
    </tr>
    <td><p>복사</p> </td>
   <td><p> 양식 조각을 복사하여 원하는 위치에 붙여넣을 수 있습니다. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>미리보기</p> </td>
   <td><p>조각을 HTML로 미리 보거나 XML 파일의 데이터를 조각과 병합하여 사용자 정의 미리보기를 수행할 수 있습니다. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>다운로드</p> </td>
   <td><p>선택한 조각을 다운로드합니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>검토 시작/검토 관리</p> </td>
   <td><p>선택한 조각에 대한 검토를 시작하고 관리할 수 있습니다.<br /> <br /> </p> </td>
    </tr>
    <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
    </tr>-->
    <tr>
   <td><p>게시/게시 취소</p> </td>
   <td><p>선택한 조각을 게시/게시 취소합니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>삭제</p> </td>
   <td><p>선택한 조각을 삭제합니다.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>비교</p> </td>
   <td><p>미리보기 목적으로 두 개의 조각을 비교합니다.<br /> <br /> </p> </td>
    </tr>
    </tbody>
    </table>

## 모범 사례

* 조각 이름이 고유한지 확인하십시오. 동일한 이름의 조각이 이미 있는 경우 조각을 만들 수 없습니다.
* 독립형 양식 조각의 모든 표현식, 스크립트 또는 스타일은 참조로 삽입되거나 양식에 임베드되어도 유지됩니다.
* 양식을 게시하면 양식 내에 참조로 삽입된 양식 조각도 자동으로 게시됩니다.

## 추가 참조

{{universal-editor-see-also}}
