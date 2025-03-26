---
title: 범용 편집기를 사용하여 Edge Delivery Services 템플릿을 기반으로 독립형 양식을 만드는 방법
description: 이 문서에서는 양식 만들기 마법사에서 Edge Delivery Services 기반 템플릿을 선택하여 범용 편집기를 사용하여 양식을 만드는 방법을 설명합니다. 양식을 AEM Edge Delivery Services에 게시할 수도 있습니다.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 979aad24ebbd0ef1d4d1fc92d402fca20bc27a44
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 83%

---

# 범용 편집기에서 독립 실행형 양식 만들기에 대한 단계별 안내서

<span class="preview"> 이 기능은 얼리 액세스 프로그램을 통해 사용할 수 있습니다. 액세스 권한을 요청하려면 공식 주소를 통해 GitHub 조직 이름과 저장소 이름을 포함한 이메일을 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>으로 보내 주십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc, 조직 이름이 adobe, 저장소 이름이 abc인 경우입니다.</span>

이 문서에서는 양식 만들기 마법사에서 Edge Delivery Services 기반 템플릿을 선택하여 유니버설 편집기로 독립 실행형 양식을 만들고 작성하는 프로세스를 안내합니다. 또한 범용 편집기를 사용해 작성한 양식을 AEM Edge Delivery Services에 게시할 수 있습니다.

AEM Forms는 데이터를 캡처하고 캡처한 데이터를 저장하는 Edge Delivery Services 양식을 쉽게 만들 수 있는 적응형 양식 블록이라는 블록을 제공합니다. [적응형 양식 블록으로 사전 구성된 새 AEM 사이트 프로젝트를 만들거나](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [기존 AEM 프로젝트에 적응형 양식 블록을 추가](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)할 수 있습니다.

![Github 저장소 워크플로](/help/edge/assets/repo-workflow.png)

## 사전 요구 사항

* [GitHub 저장소를 설정](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)하여 AEM 환경과 GitHub 저장소 간의 연결을 구축합니다.
* 이미 Edge Delivery Services를 사용하고 있는 경우 최신 버전의 [적응형 양식 블록](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)을 GitHub 저장소에 추가합니다.
* AEM Forms 작성자 인스턴스에는 Edge Delivery Services 기반 템플릿이 포함됩니다. 사용자 환경에 [최신 버전의 핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)가 설치되어 있는지 확인합니다.
* AEM Forms as a Cloud Service 작성자 인스턴스 및 GitHub 저장소의 URL을 바로 사용할 수 있습니다.

## 범용 편집기에서 양식 작업

범용 편집기를 사용하면 텍스트 필드, 체크박스, 라디오 버튼 등과 같은 기본 제공 구성 요소를 활용하여 반응형 및 대화형 독립 실행형 양식을 손쉽게 생성할 수 있습니다. 동적 규칙, 매끄러운 데이터 통합 및 사용자 지정 옵션과 같은 강력한 기능을 제공하여 정확한 요구 사항에 따라 양식을 작성할 수 있습니다. 양식을 AEM Edge Delivery Services에 게시할 수도 있습니다. 범용 편집기에서 양식에 대해 다음 작업을 수행할 수 있습니다.
* [양식 만들기](#create-a-form)
* [양식 작성](#author-a-form)
* [양식 게시](#publish-a-form)
* [양식 관리](#manage-a-form)

>[!NOTE]
>
> 또한 [범용 편집기의 Edge Delivery Services 사이트 템플릿을 사용하여 AEM 사이트에서 양식을 작성하고 Edge Delivery Services에 게시할](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project) 수도 있습니다.


### 양식 만들기

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.
1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 마법사가 열립니다.
1. **소스** 탭에서 양식 템플릿 기반 Edge Delivery Services를 선택합니다.

   ![EDS 양식 만들기](/help/edge/assets/create-eds-forms.png)


   Edge Delivery Services 기반 템플릿을 선택하면 **[!UICONTROL 만들기]** 버튼이 활성화됩니다.
1. (선택 사항) **[!UICONTROL 데이터 소스]** 또는 **[!UICONTROL 제출]** 탭에서 데이터 소스를 선택하거나 액션을 제출할 수 있습니다.
1. (선택 사항) **[!UICONTROL 게재]** 탭에서 양식의 게시 또는 게시 취소 날짜를 지정할 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하면 **양식 생성** 마법사가 나타납니다.
1. **이름**&#x200B;과 **제목**&#x200B;을 지정합니다.
1. **GitHub URL**&#x200B;을 지정합니다. 예를 들어 GitHub 저장소의 이름이 `edsforms`이고 `wkndforms` 계정 아래에 있는 경우 URL은 다음과 같습니다.
   `https://github.com/wkndforms/edsforms`
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![양식 생성 마법사](/help/edge/assets/create-form-wizard.png)

   **[!UICONTROL 만들기]**&#x200B;를 클릭하자마자 범용 편집기에서 작성할 양식이 열립니다.

   ![작성자 양식](/help/edge/assets/author-form.png)

   <!-- >[!NOTE]
        >
        > The Edge Delivery Services configuration for the forms based on Edge Delivery Services template is created automatically at the form's configuration container.-->

   **[!UICONTROL 만들기]**&#x200B;를 클릭하면 범용 편집기에서 작성할 양식이 열립니다.

### 양식 작성

1. 콘텐츠 브라우저를 열고 **콘텐츠 트리**&#x200B;의 **[!UICONTROL 적응형 양식]** 구성 요소로 이동합니다.

   ![콘텐츠 트리](/help/edge/assets/content-tree.png)

1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 원하는 구성 요소를 추가합니다.

   ![구성 요소 추가](/help/edge/assets/add-component.png)

1. 추가된 적응형 양식 구성요소를 선택하고 **[!UICONTROL 속성]**&#x200B;을 사용하여 해당 속성을 업데이트합니다.

   ![속성 열기](/help/edge/assets/component-properties.png)

   아래 스크린샷에 범용 편집기에서 작성된 간단한 `Registration Form` 양식이 표시됩니다.

   ![문의 양식](/help/edge/assets/contact-us.png)

   이제 [양식 제출 작업을 구성하고 사용자 정의](/help/edge/docs/forms/universal-editor/submit-action.md)할 수 있습니다.


<!--
## **Edge Delivery Services configuration of form**



   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Edge Delivery Services Configuration]** on your AEM Forms as a Cloud Service author instance.

        ![Select Edge Delivery Services Configuration](/help/edge/assets/select-eds-conf.png)
   1. Select the folder that matches the form's name. For example, if your form is called 'registration-form' choose the folder `forms/registration-form` and selct the configuration and publish the configuration:

        ![Edge Delivery Services Configuration](/help/edge/assets/aem-instance-eds-configuration.png)

   1. Click **[!UICONTROL Properties]** to see the configuration.   
        ![Automatically created configuration](/help/edge/assets/aem-forms-create-configuration-github.png)

        You can leave the Edge Host option as it is. The form would be published to both preview (.page) and live (.live) environments. 

   1. Click **[!UICONTROL Save and Close]**. The configuration is saved. -->

### 양식 게시

이제 범용 편집기 오른쪽 상단의 **[!UICONTROL 게시]** 버튼을 클릭하여 독립 실행형 양식을 Edge Delivery Services에 게시합니다.

![양식 게시](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Edge Delivery Services에 양식을 게시하는 방법은 [게시 및 배포](/help/edge/docs/forms/universal-editor/publish-forms.md) 설명서를 참조하십시오.

Edge Delivery Services에서 양식에 액세스하는 방법은 다음과 같습니다.

* **스테이징된 버전(테스트용)**: 스테이징된 버전에 테스트 목적으로 게시 취소된 양식의 작업 버전이 표시됩니다. 다음 URL 형식을 사용하여 양식이 라이브로 전환되기 전에 미리 봅니다.

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  예를 들어 프로젝트 저장소의 이름이 “edsforms”이고 “wkndforms” 계정 아래에서 “main” 분기 및 양식을 “등록 양식”으로 사용하는 경우 스테이징된 버전 URL은 다음과 같습니다.
  `https://main--edsforms--wkndforms.aem.page/content/forms/af/registration-form`

* **라이브 버전(게시된 양식)**: 라이브 버전에 최종 사용자가 액세스할 수 있는 최근 게시된 양식 버전이 표시됩니다. 다음 URL 형식을 사용하여 게시된 양식의 라이브 버전에 액세스합니다.

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  예를 들어 프로젝트 저장소의 이름이 “edsforms”이고 “wkndforms” 계정 아래에서 “main” 분기 및 양식을 “등록 양식”으로 사용하는 경우 스테이징된 버전 URL은 다음과 같습니다.
  `https://main--edsforms--wkndforms.aem.live/content/forms/af/registration-form`

URL 구조는 스테이징된 버전과 라이브 버전 모두에서 동일하게 유지됩니다. 단, 컨텍스트에 따라 표시되는 콘텐츠가 달라집니다.

![게시된 양식 보기](/help/edge/assets/eds-view-publish-form.png)

### 양식 관리

AEM Forms 사용자 인터페이스를 사용하여 양식에 대해 여러 작업을 수행할 수 있습니다.

1. AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

1. 양식을 선택하면 다음과 같이 도구 모음에 선택한 양식에서 수행할 수 있는 작업이 표시됩니다.

<table>
 <tbody>
  <tr>
   <td><p><strong>작업</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
  </tr>
  <tr>
   <td><p>편집</p> </td>
   <td><p>편집 모드에서 양식을 엽니다.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>속성</p> </td>
   <td><p>양식의 속성을 수정할 수 있습니다.<br /> <br /> </p> </td>
  </tr>
  <td><p>복사</p> </td>
   <td><p> 양식을 복사하여 원하는 위치에 붙여넣을 수 있습니다. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>미리보기</p> </td>
   <td><p>양식을 HTML로 미리 보거나 XML 파일의 데이터를 양식과 병합하여 사용자 정의 미리보기를 수행할 수 있습니다. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>다운로드</p> </td>
   <td><p>선택한 양식을 다운로드합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>검토 시작/검토 관리</p> </td>
   <td><p>선택한 양식에 대한 검토를 시작하고 관리할 수 있습니다.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>-->
  <tr>
   <td><p>게시/게시 취소</p> </td>
   <td><p>선택한 양식을 게시/게시 취소합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>삭제</p> </td>
   <td><p>선택한 양식을 삭제합니다.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>비교</p> </td>
   <td><p>미리보기 목적으로 두 개의 양식을 비교합니다.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## 문제 해결

양식을 로딩하는 데 문제가 있습니까? 여기 몇 가지 일반적인 문제와 해결 방법이 있습니다.

* **양식 URL**: 양식의 URL 끝에 “.html” 확장 기능이 포함되어 있지 않은지 다시 한 번 확인합니다. Edge Deliver Service에는 이 확장 기능이 필요하지 않습니다.

* **AEM 작성자 UR** L: `fstab.yaml` 파일에 나열된 AEM 작성자 URL 형식이 올바른지 확인합니다. 다음 세부 정보가 포함되어야 합니다.

   * 올바른 GitHub 소유자
   * 올바른 저장소 이름
   * Edge Delivery Services에 사용 중인 특정 분기

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## 양식 만들기 시작

{{universal-editor-see-also}}
