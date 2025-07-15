---
title: 핵심 구성 요소 또는 Edge Delivery Services 템플릿을 기반으로 독립 실행형 양식을 만들고 Edge Delivery Services에 게시하는 방법
description: 이 문서에서는 양식 생성 마법사에서 핵심 구성 요소 기반 템플릿 또는 Edge Delivery Services 기반 템플릿을 선택하여 적응형 양식을 만드는 방법을 설명합니다. AEM Edge Delivery Services에 양식을 게시할 수도 있습니다.
feature: Edge Delivery Services
role: User
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 95%

---


# 작성에서 게시까지: Edge Delivery Services의 AEM Forms

<span class="preview"> 이 기능은 얼리 액세스 프로그램을 통해 사용할 수 있습니다. 액세스 권한을 요청하려면 공식 주소를 통해 GitHub 조직 이름과 저장소 이름을 포함한 이메일을 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>으로 보내 주십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc, 조직 이름이 adobe, 저장소 이름이 abc인 경우입니다.</span>

Adobe Experience Manager(AEM)를 사용하면 매력적이고 반응성이 뛰어나며 역동적인 양식을 만들 수 있습니다. AEM은 다양한 요구 사항과 사용자 전문성 수준에 맞는 여러 작성 방법을 제공합니다.&#x200B;

이 문서에서는 AEM 환경 내에서 양식을 작성하고 Edge Delivery Services를 통해 게시하는 접근 방식에 중점을 둡니다. 핵심 구성 요소 기반 템플릿을 사용하여 작성된 양식은 AEM과 Edge Delivery Services 모두에 게시할 수 있으므로 배포의 유연성을 제공합니다 반면, Edge Delivery Services 기반 템플릿을 사용하여 작성한 양식은 Edge Delivery Services에만 게시할 수 있습니다.&#x200B;

![적응형 양식 작성 및 게시](/help/edge/docs/forms/universal-editor/assets/author-publish-af.png){width=50% align=center}

## AEM에서 양식을 작성하고 Edge Delivery Services를 사용하여 게시할 때의 이점:

* **기존 AEM 워크플로 보존**: 조직은 기존 AEM 워크플로 및 거버넌스 구조를 계속 사용하여 콘텐츠 생성에 대한 일관성과 컨트롤을 확보할 수 있습니다.&#x200B;

* **향상된 성능**: Edge Delivery Services를 통해 게시하면 렌더링 시간이 빨라지고, 사용자 경험이 향상되며 페이지 로드 시간이 단축됩니다.&#x200B;

* **향상된 SEO**: Edge Delivery Services는 높은 Google Lighthouse 점수를 받은 콘텐츠를 게재하도록 설계되어 이를 통해 검색 엔진 최적화가 향상되고 가시성이 증가할 수 있습니다.&#x200B;

* **유연한 배포 옵션**: 핵심 구성 요소를 사용하여 작성된 양식은 AEM과 Edge Delivery Services 모두에 게시할 수 있으므로 배포 전략에 유연성을 제공합니다.&#x200B;

## 시작하기 전

AEM에서 양식을 작성하고 Edge Delivery Services를 통해 게시하기 전에 다음 사전 요구 사항이 충족되는지 확인하십시오.

* Edge Delivery Services에 대해 Github 저장소가 구성되어 있는지 확인합니다.
   * 저장소가 없는 경우 [적응형 양식 블록으로 사전 구성된 새 AEM 프로젝트](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)를 만드십시오.
   * 저장소가 있는 경우 기존 저장소에 적응형 양식 블록을 추가하십시오. 자세한 지침은 [AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)에서 확인할 수 있습니다.
* AEM 환경과 GitHub 저장소 간의 연결을 설정합니다. [방법 확인](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)

적응형 양식 설정 및 게시 방법을 안내하는 의사 결정 흐름 다이어그램:

![Github 저장소 워크플로](/help/forms/assets/repo-workflow.png){width=auto}

## AEM에서 양식을 작성하고 Edge Delivery Services에 게시

다음 단계에 따라 AEM에서 양식을 작성하고 Edge Delivery Services에 게시할 수 있습니다.

[&#x200B;1. 템플릿 선택 및 양식 만들기](#choose-a-template-and-create-the-form)

[&#x200B;2. 양식 작성](#author-the-form)

[&#x200B;3. 양식 게시](#publish-a-form)

### 템플릿 선택 및 양식 만들기

다음을 사용하여 Edge Delivery Services에 게시할 AEM 인스턴스에서 양식을 만들 수 있습니다.

>[!BEGINTABS]

>[!TAB Edge Delivery Services 기반 템플릿]

다음 단계에 따라 템플릿을 선택하고 양식을 만드십시오.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.
1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 마법사가 열립니다.
1. **소스** 탭에서 **Edge Delivery Services 기반 템플릿**&#x200B;을 선택합니다.

   ![EDS 양식 만들기](/help/edge/assets/create-eds-forms.png)

   **Edge Delivery Services 기반 템플릿**&#x200B;을 선택하면 **[!UICONTROL 만들기]** 버튼이 활성화됩니다.
1. (선택 사항) **[!UICONTROL 데이터 소스]** 또는 **[!UICONTROL 제출]** 탭에서 데이터 소스를 선택하거나 액션을 제출할 수 있습니다.
1. (선택 사항) **[!UICONTROL 게재]** 탭에서 양식의 게시 또는 게시 취소 일자를 지정할 수 있습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하면 **양식 생성** 마법사가 나타납니다.

   1. **이름**&#x200B;과 **제목**&#x200B;을 지정합니다.
   1. **GitHub URL**&#x200B;을 지정합니다. 예를 들어 GitHub 저장소의 이름이 `edsforms`이고 `wkndforms` 계정 아래에 있는 경우 URL은 다음과 같습니다.

      `https://github.com/wkndforms/edsforms`

   ![양식 생성 마법사](/help/edge/assets/create-form-wizard.png)

   **[!UICONTROL 만들기]**&#x200B;를 클릭하면 범용 편집기에서 작성할 양식이 열립니다.

   ![왼쪽에 구성 요소 팔레트, 중앙에 양식 캔버스, 오른쪽에 속성 패널이 있는 작성 중인 양식을 표시하는 유니버설 편집기의 스크린샷](/help/edge/assets/author-form.png)
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하여 양식을 만듭니다. 이제 [범용 편집기를 사용하여 양식을 작성](#author-the-form)할 수 있습니다.

>[!TAB 핵심 구성 요소 기반 템플릿]

다음 단계에 따라 템플릿을 선택하고 양식을 만드십시오.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.
1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 마법사가 열립니다.
1. **소스** 탭에서 **핵심 구성 요소 기반 템플릿**&#x200B;과 **테마**&#x200B;를 선택하면 **[!UICONTROL 만들기]** 버튼이 활성화됩니다.

   ![핵심 구성 요소 기반 템플릿](/help/forms/assets/core-component-based-template.png)

1. (선택 사항) **[!UICONTROL 데이터 소스]** 또는 **[!UICONTROL 제출]** 탭에서 데이터 소스를 선택하거나 액션을 제출할 수 있습니다.
1. (선택 사항) **[!UICONTROL 게재]** 탭에서 양식의 게시 또는 게시 취소 일자를 지정할 수 있습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하면 **양식 생성** 마법사가 나타납니다.
   1. **이름**&#x200B;과 **제목**&#x200B;을 지정합니다.
   1. **경로** 필드에 적응형 양식을 저장할 위치를 지정합니다.

   ![양식 생성 마법사](/help/forms/assets/create-cc-form.png)

   **[!UICONTROL 만들기]**&#x200B;를 클릭하면 적응형 양식 편집기에서 작성할 양식이 열립니다.

   ![적응형 양식 편집기](/help/forms/assets/af-editor-form.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하여 양식을 만듭니다. 이제 [적응형 양식 편집기를 사용하여 양식을 작성](#author-the-form)할 수 있습니다.

>[!ENDTABS]

### 양식 작성

Edge Delivery Services 기반 템플릿을 사용하여 만든 양식은 작성을 위해 [범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)에서 열립니다. 그러나 핵심 구성 요소 기반 템플릿을 사용하여 만든 양식은 작성을 위해 적응형 양식 편집기에서 열립니다.

Edge Delivery Services 기반 템플릿을 사용하여 범용 편집기로 양식을 작성하거나 핵심 구성 요소 기반 템플릿을 사용하여 적응형 양식 편집기로 양식을 작성하려면 다음 단계를 수행하십시오.

>[!BEGINTABS]

>[!TAB Edge Delivery Services 기반 템플릿]


1. 콘텐츠 브라우저를 열고 **콘텐츠 트리**&#x200B;의 **[!UICONTROL 적응형 양식]** 구성 요소로 이동합니다.

   ![콘텐츠 트리](/help/edge/assets/content-tree.png)

1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 원하는 구성 요소를 추가합니다.
   ![구성 요소 추가](/help/edge/assets/add-component.png)

   아래 스크린샷에 범용 편집기에서 작성된 `Registration Form`이 표시됩니다.

   ![이름, 전자 메일, 휴대폰 및 메시지에 대한 양식 필드에 적절한 스타일 및 레이아웃을 표시하는 범용 편집기의 연락처 양식 스크린샷](/help/edge/assets/contact-us.png)

>[!NOTE]
>
> 범용 편집기를 사용하여 적응형 양식을 작성하는 방법에 대한 자세한 지침을 보려면 [여기를 클릭하십시오](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

이제 [양식 제출 작업을 구성하고 사용자 정의](/help/edge/docs/forms/universal-editor/submit-action.md)할 수 있습니다.

>[!TAB 핵심 구성 요소 기반 템플릿]

1. **여기로 구성 요소 드래그** 섹션에서 **[!UICONTROL 구성 요소 삽입]**&#x200B;을 클릭합니다.

   ![여기로 구성 요소 드래그](/help/forms/assets/drag-components-af-editor.png)

1. **적응형 양식 구성 요소** 목록에서 원하는 구성 요소를 추가합니다.

   ![구성 요소 추가](/help/forms/assets/add-component-af.png)

아래 스크린샷에 적응형 양식 편집기에서 작성된 `Enrollment Form`이 표시됩니다.

![적응형 양식 편집기](/help/forms/assets/af-editor-form.png)

>[!NOTE]
>
> 핵심 구성 요소 템플릿을 기반으로 적응형 양식을 만드는 방법에 대한 자세한 지침을 보려면 [여기를 클릭하십시오](/help/forms/creating-adaptive-form-core-components.md).

이제 [양식 제출 작업을 구성](/help/forms/configure-submit-actions-core-components.md)할 수 있습니다.

>[!ENDTABS]

### 양식 게시

Edge Delivery Services에서 적응형 양식을 게시하려면 [AEM 인스턴스에서 Edge Delivery Services 구성을 만들어야](#create-an-edge-delivery-services-configuration) 합니다.

#### Edge Delivery Services 구성 만들기

Edge Delivery Services 구성을 만들려면 다음 단계를 수행하십시오.

>[!BEGINTABS]
>[!TAB Edge Delivery Services 기반 템플릿]


양식의 구성 컨테이너에 Edge Delivery Services 기반 템플릿 기반 양식에 대한 Edge Delivery Services 구성이 자동으로 생성됩니다.

![Edge Delivery Services 구성](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB 핵심 구성 요소 기반 템플릿]

1. AEM Forms as a Cloud Service 작성자 인스턴스에서 **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Edge Delivery Services 구성]**&#x200B;으로 이동합니다.

   ![Edge Delivery Services 구성 선택](/help/edge/assets/select-eds-conf.png)

2. 양식 이름과 일치하는 폴더를 선택합니다. 예를 들어 양식의 이름이 `enrollment-form`인 경우 `forms/enrollment-form` 폴더를 선택하고 **[!UICONTROL 만들기]** > **[!UICONTROL 구성]**&#x200B;을 클릭합니다.

   ![Edge Delivery Services 구성](/help/forms/assets/create-eds-conf.png)

3. **[!UICONTROL Edge Delivery Services 구성]**&#x200B;을 클릭하고 **[!UICONTROL 속성]**&#x200B;을 클릭하여 속성을 엽니다.

   ![자동으로 생성된 구성](/help/forms/assets/eds-conf.png)

   Edge Delivery Services 구성이 나타납니다.

4. Edge Delivery Services 구성에서 다음을 지정합니다.

   * **조직**: GitHub 조직 이름을 지정합니다.

   * **사이트 이름**: GitHub 저장소 이름을 지정합니다.
   * **분기**: 분기 이름을 지정합니다. 주 분기를 사용하는 경우 텍스트 상자를 비워 두십시오.
   * **(선택 사항) Edge Host**: Edge Host 옵션을 그대로 둡니다. 양식은 미리보기(.page) 및 라이브(.live) 환경 모두에 게시됩니다.
   * **(선택 사항) 사이트 인증 토큰**: 사이트 인증 토큰을 사용하여 AEM 인스턴스와 Edge Delivery Services 간의 요청을 안전하게 인증할 수 있습니다.

5. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 구성이 생성됩니다.

>[!ENDTABS]

#### Edge Delivery Services에서 양식에 액세스

Edge Delivery Services에서 양식에 액세스하려면 양식을 게시해야 합니다. 양식을 게시하려면 다음 단계를 수행하십시오.

>[!BEGINTABS]
>[!TAB 범용 편집기에서]

1. 범용 편집기 오른쪽 상단의 **[!UICONTROL 게시]** 버튼을 클릭하여 양식을 게시합니다.

![양식 게시 옵션 및 확인 단추가 있는 게시 대화 상자를 표시하는 유니버설 편집기의 스크린샷](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Edge Delivery Services에 양식을 게시하는 방법은 [게시 및 배포](/help/edge/docs/forms/universal-editor/publish-forms.md) 설명서를 참조하십시오.

>[!TAB 적응형 양식 편집기에서]

1. Experience Manager Forms 콘솔에서 상위 폴더로 이동하여 게시하려는 양식을 선택합니다.

1. 도구 모음에서 **[!UICONTROL 게시]** 옵션을 클릭하고 양식과 함께 게시될 모든 참조 자산을 살펴봅니다.

![적응형 양식 편집기에서 양식 게시](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> 적응형 양식 편집기에서 양식을 게시하는 방법을 알아보려면 [Experience Manager Forms에서 게시 관리](/help/forms/manage-publication.md) 문서를 참조하십시오.

>[!ENDTABS]

* **스테이징된 버전(테스트용)**: 스테이징된 버전에 테스트 목적으로 게시 취소된 양식의 작업 버전이 표시됩니다. 다음 URL 형식을 사용하여 양식이 라이브로 전환되기 전에 미리 봅니다.

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`



* **라이브 버전(게시된 양식)**: 라이브 버전에 최종 사용자가 액세스할 수 있는 최근 게시된 양식 버전이 표시됩니다. 다음 URL 형식을 사용하여 게시된 양식의 라이브 버전에 액세스합니다.

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  URL 구조는 스테이징된 버전과 라이브 버전 모두에서 동일하게 유지됩니다. 단, 컨텍스트에 따라 표시되는 콘텐츠가 달라집니다.

아래 스크린샷은 Edge Delivery Services 기반 템플릿과 핵심 구성 요소 기반 템플릿을 사용하여 만든 양식의 스테이징된 양식과 라이브 양식의 URL 및 시각적 미리보기를 비교한 것입니다.

>[!BEGINTABS]
>[!TAB Edge Delivery Services 기반 템플릿]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
    <thead>
    <tr>
      <th style="width: 20%;"><strong>버전</strong></th>
      <th style="width: 80%;"><strong>이미지</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr>
      <td>스테이징된 버전</td>
      <td><img src="/help/forms/assets/registration-form-staged-version.png" alt="등록 양식의 스테이징된 버전" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>라이브 버전</td>
      <td><img src="/help/forms/assets/registration-form-live-version.png" alt="등록 양식의 라이브 버전" style="width: 100%; height: auto;" /></td>
    </tr>
    </tbody>
  </table>

>[!TAB 핵심 구성 요소 기반 템플릿]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr>
      <th style="width: 20%;"><strong>버전</strong></th>
      <th style="width: 80%;"><strong>이미지</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>스테이징된 버전</td>
      <td><img src="/help/forms/assets/enrollment-form-staged-version.png" alt="등록 양식의 스테이징된 버전" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>라이브 버전</td>
      <td><img src="/help/forms/assets/enrollment-form-live-version.png" alt="등록 양식의 라이브 버전" style="width: 100%; height: auto;" /></td>
    </tr>
  </tbody>
  </table>

>[!ENDTABS]

## 문제 해결

양식을 로딩하는 데 문제가 있습니까? 여기 몇 가지 일반적인 문제와 해결 방법이 있습니다.

* **양식 URL**: 양식의 URL 끝에 “.html” 확장 기능이 포함되어 있지 않은지 다시 한 번 확인합니다. Edge Deliver Service에는 이 확장 기능이 필요하지 않습니다.

* **AEM 작성자 UR** L: `fstab.yaml` 파일에 나열된 AEM 작성자 URL 형식이 올바른지 확인합니다. 다음 세부 정보가 포함되어야 합니다.

   * 올바른 GitHub 소유자
   * 올바른 저장소 이름
   * Edge Delivery Services에 사용 중인 특정 분기

## 양식 만들기 시작

{{universal-editor-see-also}}

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.

### Managing a form

You can perform several operations on form using the AEM Forms user interface.

1. Login into your AEM Forms as a Cloud Service author instance.
1. Select **[!UICONTROL Adobe Experience Manager]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Forms & Documents]**.

1. Select a form and the toolbar displays the following operations you can perform on the selected form.

<table>
 <tbody>
  <tr>
   <td><p><strong>Operation</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>Edit</p> </td>
   <td><p>Opens the form in edit mode.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>Properties</p> </td>
   <td><p>Provides options to modify the properties of the form.<br /> <br /> </p> </td>
  </tr>
  <td><p>Copy</p> </td>
   <td><p> Provides options to copy the form  and paste it at the desired location. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Preview</p> </td>
   <td><p>Provides options to preview the form as HTML or perform a custom preview by merging data from an XML file with the form. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Download</p> </td>
   <td><p>Downloads the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Start Review/Manage Review</p> </td>
   <td><p>Allows initiating and managing a review of the selected form.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publish / Unpublish</p> </td>
   <td><p>Publishes / unpublishes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Delete</p> </td>
   <td><p>Deletes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Compare</p> </td>
   <td><p>Compares two different form for previewing purposes.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table> 


## How Edge Delivery Services Forms Work?

Users can author Edge Delivery Services Forms using document-based authoring tools such as Google Drive, SharePoint, or the Universal Editor (WYSIWYG authoring), while leveraging the basic styling, behaviour and components available in the GitHub repository. Once authored, Edge Delivery Services Forms can send data to any platform using the Forms Submission Service.

![How Edge Delivery Services Forms works](/help/edge/docs/forms/assets/eds-forms-working.png)

### Key components of Edge Delivery Services Forms

The key components of Edge Delivery Servies Forms are:

* **GitHub Repository**: The GitHub repository serves as a boilerplate for creating Edge Delivery Services Forms. The forms leverage basic styling and functionality from the repository and allow users to add customizations and custom components to the Edge Delivery Services Forms.

* **Form Authoring**: Edge Delivery Services Forms support two types of authoring: WYSIWYG and document-based authoring. Document-based authoring enables users to create forms using familiar tools like Google Docs and Microsoft Office. WYSIWYG authoring allows users to design forms visually using the Universal Editor, making it easy for non-technical users to create and manage forms. Universal Editor offers an intuitive form creation experience and provides access to numerous form capabilities.

* **Forms Submission Service**: The Forms Submission Service allows you to store data from forms submissions on any platform, such as OneDrive, SharePoint, or Google Sheets, making it easy to access and manage form data within your preferred system.-->
