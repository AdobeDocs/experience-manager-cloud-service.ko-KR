---
title: WYSIWYG 기반 작성을 위한 양식 조각을 만드는 방법
description: 범용 편집기에서 양식 조각을 만들고 양식에 추가하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, User, Developer
exl-id: 7b0d4c7f-f82f-407b-8e25-b725108f8455
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: ht
source-wordcount: '1693'
ht-degree: 100%

---

# 범용 편집기에서 양식 조각 만들기

양식 조각은 반복적인 개발 작업을 없애고 조직의 양식 전반에 걸쳐 일관성을 보장하는 재사용 가능한 구성 요소입니다. 모든 양식에 대해 연락처 정보, 주소 세부 사항 또는 동의 계약과 같은 일반적인 섹션을 다시 만들 필요 없이 이러한 요소를 조각으로 한 번 빌드하고 여러 양식에 걸쳐 재사용할 수 있습니다.

**이 문서에서 다룰 내용:**

- 양식 조각의 비즈니스 가치 및 기술적 기능 이해
- 범용 편집기를 사용하여 재사용 가능한 양식 조각 만들기
- 적절한 구성으로 기존 양식에 조각 통합
- 조각 수명 주기 관리 및 양식 전반의 일관성 유지

**비즈니스 이점:**

- **개발 시간 단축**: 일반적인 양식 섹션을 한 번 빌드하고 모든 곳에서 재사용합니다.
- **향상된 일관성**: 모든 양식에서 표준화된 레이아웃 및 콘텐츠를 제공합니다.
- **간소화된 유지 관리**: 조각을 한 번 업데이트하여 조각을 사용하는 모든 양식에 변경 사항을 반영합니다.
- **향상된 규정 준수**: 규정 섹션이 일관되고 최신 상태로 유지되도록 합니다.

Edge Delivery Services의 양식 조각은 중첩 조각, 단일 양식 내 다중 인스턴스 및 데이터 소스와의 원활한 통합을 포함한 고급 기능을 지원합니다.

## 양식 조각 이해

Edge Delivery Services의 양식 조각은 모듈식 양식 개발을 위한 강력한 기능을 제공합니다.

**핵심 기능:**

- **일관성 관리**: 조각은 여러 양식에서 동일한 레이아웃 및 콘텐츠를 유지합니다. “한번 변경하여 전체 반영”이라는 접근 방식을 통해 조각에 적용된 업데이트가 미리보기 모드의 모든 양식에 자동으로 적용됩니다.
- **다중 사용**: 단일 양식 내에 동일한 조각을 여러 번 추가할 수 있으며, 각 조각은 다른 데이터 소스 또는 스키마 요소에 대한 독립적인 데이터 바인딩을 사용합니다.
- **중첩 구조**: 조각 내에 다른 조각을 임베드하여 정교한 양식 아키텍처를 위한 복잡한 계층을 만듭니다.

**기술 요구 사항:**

- **GitHub URL 일관성**: 조각과 이를 사용하는 양식 모두 동일한 GitHub 저장소 URL을 지정해야 합니다.
- **독립형 편집**: 조각은 독립형 양식에서만 수정할 수 있으며, 호스트 양식 내에서는 변경할 수 없습니다.

**게시 비헤이비어:**

>[!IMPORTANT]
>
>미리보기 모드에서는 조각 변경 사항이 모든 양식에 즉시 반영됩니다. 게시 모드에서는 업데이트를 확인하기 위해 조각과 이를 사용하는 모든 양식을 다시 게시해야 합니다.

>[!CAUTION]
>
>순환 조각 참조(조각 자체 내에 조각을 중첩하는 것)는 렌더링 오류 및 예기치 않은 비헤이비어를 유발하므로 피해야 합니다.

## 사전 요구 사항

**기술 설정 요구 사항:**

- AEM 환경과 GitHub 저장소 간에 연결이 설정된 [GitHub 저장소 구성](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)
- 기존 Edge Delivery Services 프로젝트의 경우 GitHub 저장소에 추가된 [최신 적응형 양식 블록](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- Edge Delivery Services 템플릿을 사용할 수 있는 AEM Forms 작성자 인스턴스
- AEM Forms as a Cloud Service 작성자 인스턴스 URL 및 GitHub 저장소 URL에 대한 액세스 권한

**필요한 지식 및 권한:**

- 양식 디자인 개념 및 구성 요소 계층에 대한 기본 이해
- 범용 편집기 인터페이스 및 양식 만들기 워크플로에 대한 지식
- 양식 자산을 만들고 관리하기 위한 AEM Forms의 작성자 수준 권한
- 조직의 양식 표준 및 재사용 가능한 구성 요소 요구 사항에 대한 이해

## Edge Delivery Services 양식 조각을 사용하여 작업

범용 편집기에서 Edge Delivery Services 양식 조각을 만들고 생성된 조각을 Edge Delivery Services 양식에 추가할 수 있습니다. Edge Delivery Services 양식 조각을 사용하면 다음 액션을 수행할 수 있습니다.

- [범용 편집기에서 양식 조각 만들기](#creating-form-fragments-in-universal-editor)
   - [양식 조각 이해](#understanding-form-fragments)
   - [사전 요구 사항](#prerequisites)
   - [Edge Delivery Services 양식 조각을 사용하여 작업](#working-with-edge-delivery-services-form-fragments)
   - [모범 사례](#best-practices)
   - [요약](#summary)

+++ 양식 조각 만들기

범용 편집기에서 양식 조각을 만들려면 다음 단계를 수행합니다.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.
1. **만들기 > 적응형 양식 조각**&#x200B;을 클릭합니다.

   ![조각 만들기](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   **적응형 양식 조각 만들기** 마법사가 나타납니다.
1. **템플릿 선택**&#x200B;탭에서 Edge Delivery Services 기반 템플릿을 선택하고 **[!UICONTROL 다음]**을 클릭합니다.
   ![Edge Delivery Services 템플릿 선택](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. 조각의 제목, 이름, 설명 및 태그를 지정합니다. 조각에 고유한 이름을 지정해야 합니다. 동일한 이름의 다른 조각이 존재하는 경우 조각은 생성되지 않습니다.
1. **GitHub URL**&#x200B;을 지정합니다. 예를 들어 GitHub 저장소의 이름이 `edsforms`이고 `wkndforms` 계정 아래에 있는 경우 URL은 `https://github.com/wkndforms/edsforms`입니다.

   ![기본 속성](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (선택 사항) **양식 모델** 탭을 클릭하여 열고 **다음에서 선택** 드롭다운 메뉴에서 다음 조각 모델 중 하나를 선택합니다.

   ![양식 모델 탭에서 모델 유형 표시](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   - **양식 데이터 모델(FDM)**: 데이터 소스의 데이터 모델 오브젝트와 서비스를 조각에 통합합니다. 양식에 여러 소스의 데이터를 읽고 써야 하는 경우 양식 데이터 모델(FDM)을 선택하십시오.

   - **JSON 스키마**: 데이터 구조를 정의하는 JSON 스키마를 연결하여 양식을 백엔드 시스템과 통합합니다. 이렇게 하면 스키마 요소를 사용하여 동적 콘텐츠를 추가할 수 있습니다.
   - **없음**: 양식 모델을 사용하지 않고 처음부터 조각을 만들도록 지정합니다.

   >[!NOTE]
   >
   > 범용 편집기에서 양식이나 조각을 양식 데이터 모델(FDM)과 통합하여 다양한 백엔드 데이터 소스를 사용하는 방법을 알아보려면 [범용 편집기에서 양식 데이터 모델과 양식 통합](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)을 참조하십시오.

1. (선택 사항) **고급** 탭에서 조각의 **게시 일자** 또는 **게시 취소 일자**&#x200B;를 지정합니다.

   ![고급 탭](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. **만들기**&#x200B;를 클릭하여 조각을 생성합니다. 편집 옵션이 포함된 성공 대화 상자가 나타납니다.

   ![조각 편집](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. **편집**&#x200B;을 클릭하여 기본 템플릿이 적용된 범용 편집기에서 조각을 엽니다.

   ![작성용 범용 편집기의 조각](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

1. **조각 콘텐츠 디자인**: 양식 구성 요소(텍스트 필드, 드롭다운, 확인란)를 추가하여 재사용 가능한 섹션을 빌드합니다. 자세한 구성 요소 지침은 [범용 편집기를 사용하여 AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg)를 참조하십시오.

1. **구성 요소 속성 구성**: 사용 사례에 따라 필드 이름, 유효성 검사 규칙 및 기본값을 설정합니다.

1. **저장 및 미리보기**: 조각을 저장하고 미리보기 모드를 사용하여 레이아웃과 기능을 확인합니다.

   ![이름, 전화번호, 이메일, 주소 필드를 보여 주는 범용 편집기의 완성된 연락처 세부 정보의 스크린샷은 여러 양식에 걸쳐 재사용할 수 있습니다.](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

**유효성 검사 체크포인트:**

- 범용 편집기에서 오류 없이 조각이 로드됩니다.
- 모든 양식 구성 요소가 올바르게 렌더링됩니다.
- 필드 속성 및 유효성 검사 규칙이 예상대로 작동합니다.
- 조각이 저장되고 양식 및 문서 콘솔에서 사용할 수 있습니다.

조각이 완료되면 [모든 Edge Delivery Services 양식에 통합](#adding-form-fragments-to-a-form)할 수 있습니다.

+++


+++ 양식에 양식 조각 추가

이 예에서는 직원 및 감독자 정보 섹션 모두에 `Contact Details` 조각을 사용하는 `Employee Details` 양식을 만드는 방법을 보여 줍니다. 이 접근 방식을 사용하면 개발 노력을 줄이면서 일관된 데이터 수집을 보장할 수 있습니다.

양식에 양식 조각을 통합하려면 다음을 수행하십시오.

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

   ![범용 편집기 내의 직원 양식에 연락처 세부 정보 조각이 성공적으로 통합된 모습을 보여 주는 스크린샷으로, 조각이 재사용될 때 구조를 유지하는 방법을 보여 줍니다.](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   >[!NOTE]
   >
   > **조각 편집** 버튼을 사용하면 편집할 양식 조각으로 직접 이동할 수 있습니다.

   **미리보기 모드**&#x200B;에서 양식을 미리 보고 양식이 어떻게 나타나는지 확인할 수 있습니다.

   ![미리보기](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   마찬가지로 3~7단계를 반복하여 `Supervisor Details` 패널에도 `Contact Details` 조각을 삽입할 수 있습니다.

   ![직원 세부 정보 양식](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

+++



+++ 양식 조각 관리

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

+++ 

## 모범 사례

**조각 디자인 및 이름 지정:**

- **설명적이고 고유한 이름 사용**: 조각의 용도를 명확하게 나타내는 이름(예: “fragment1” 대신 “contact-details-with-validation”)을 선택합니다.
- **재사용성 계획**: 조각을 상황에 구애받지 않도록 설계하여 다양한 양식 유형에서 작동하도록 합니다.
- **조각에 집중**: 복잡하고 다기능적인 구성 요소 대신 단일 용도의 조각을 만듭니다.

**개발 워크플로:**

- **조각을 독립적으로 테스트**: 양식에 통합하기 전에 조각 기능의 유효성을 검사합니다.
- **일관된 GitHub URL 유지**: 모든 관련 조각 및 양식에서 동일한 저장소 URL이 사용되는지 확인합니다.
- **조각 용도 문서화**: 팀원이 각 조각을 사용해야 하는 시기를 이해하는 데 도움이 되도록 명확한 설명 및 태그를 포함합니다.

**게시 및 유지 관리:**

- **게시 조정**: 조각을 업데이트할 때 종속된 모든 양식을 동시에 다시 게시하도록 계획합니다.
- **버전 제어**: 조각을 업데이트할 때 의미 있는 커밋 메시지를 사용하여 시간 경과에 따른 변경 사항을 추적합니다.
- **종속성 모니터링**: 업데이트 영향을 평가하기 위해 각 조각을 사용하는 양식을 추적합니다.

>[!TIP]
>
>조각 스타일, 스크립트 및 표현식은 임베드될 때 유지되므로 이 상속을 염두에 두고 디자인합니다.

## 요약

Edge Delivery Services에서 양식 조각을 활용하여 개발 효율성을 개선하고 조직의 양식 전반에 걸쳐 일관성을 유지하는 방법을 성공적으로 알아보았습니다.

**주요 성과:**

- **이해**: 양식 조각의 비즈니스 가치 및 기술적 기능을 파악했습니다.
- **생성**: 올바른 구성으로 범용 편집기를 사용하여 재사용 가능한 양식 조각을 빌드했습니다.
- **통합**: 올바른 참조 설정 및 속성 구성으로 양식에 조각을 추가했습니다.
- **관리**: 조각 수명 주기 작업 및 유지 관리 워크플로를 살펴보았습니다.

**다음 단계:**

- 조직에 일반적으로 사용되는 조각 라이브러리를 만듭니다.
- 조각 사용에 대한 명명 규칙 및 거버넌스 정책을 수립합니다.
- 동적 데이터 기반 조각에 대한 [양식 데이터 모델](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)과의 고급 통합을 탐색합니다.
- 일관된 사용자 경험을 위해 조각 기반의 양식 템플릿을 구현합니다.

이제 양식은 프로젝트 전반에서 효율적으로 확장되는 동시에 일관된 사용자 경험을 보장하는 모듈식의 유지 관리가 용이한 아키텍처의 이점을 누릴 수 있습니다.


