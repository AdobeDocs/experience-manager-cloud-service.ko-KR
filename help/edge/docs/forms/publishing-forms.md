---
title: Edge Delivery Services용 양식 게시
description: Edge Delivery Services를 통한 콘텐츠 양식 방법과 Edge Delivery Services를 사용한 AEM 양식 게시 방법을 알아보십시오.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: b90c27e3-22ea-4b18-b16e-a5c5a0ed58b8
source-git-commit: 67384a9141ced3bf5be63c8489dd5c329a288056
workflow-type: ht
source-wordcount: '993'
ht-degree: 100%

---

# Edge Delivery Services용 양식 게시

이 문서는 AEM Edge Delivery Services에 양식을 게시하는 과정에 대해 안내합니다.
Edge Delivery Services에 양식을 게시하려면 먼저 AEM 환경과 GitHub 저장소 간에 연결을 설정해야 합니다. 연결되면 WYSIWYG(What You See Is What You Get) 접근 방식을 따르는 범용 편집기를 사용하여 양식을 작성할 수 있으므로 Sites에 원활하고 일관된 사용자 경험을 제공할 수 있습니다.

## 전제 조건

* 적응형 양식을 처음 사용하십니까? 제공된 [튜토리얼](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)에 따라 GitHub 저장소를 설정합니다.
* 이미 Edge Delivery Services를 사용하고 있는 경우 최신 버전의 [적응형 양식 블록](/help/edge/docs/forms/tutorial.md#)을 GitHub 저장소에 추가합니다.
* AEM Forms 작성자 인스턴스에는 Edge Delivery Services 기반 템플릿이 포함됩니다. 사용자 환경에 [최신 버전의 핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)가 설치되어 있는지 확인합니다.
* AEM Forms as a Cloud Service 작성자 인스턴스 및 GitHub 저장소의 URL을 바로 사용할 수 있습니다.

## Edge Delivery Services용 양식 게시

Edge Delivery Services용 양식을 게시하도록 아래 단계를 수행합니다.

[1. AEM 인스턴스에 GitHub 저장소 연결](#link-github-repository-to-aem-instance)

[2. GitHub 저장소에 AEM 인스턴스 연결](#link-aem-instance-to-github-repository)

### AEM 인스턴스에 GitHub 저장소 연결

[GitHub 저장소의 프로젝트](/help/edge/docs/forms/tutorial.md)를 AEM Forms 작성자 인스턴스에 연결하도록 다음 단계를 수행합니다.

1. Edge Delivery Services용으로 생성되거나 구성된 GitHub 저장소로 이동합니다.
1. 편집할 `fstab.yaml` 페이지를 엽니다.
1. GitHub 저장소의 `fstab.yaml` 파일을 AEM Forms as a Cloud Service의 URL로 업데이트합니다.

   ```javascript
    mountpoints:
    /:
        url: [author-instance-url]/bin/franklin.delivery/[Github owner]/[Github Repository]/[Github branch] 
        type: "markup"
        suffix: ".html"
   ```

   예를 들어 GitHub 저장소의 이름이 “aemcrosswalk“이고 “wkndform” 계정 아래에서 “main” 분기를 사용하는 경우 작성자 인스턴스 URL은 다음과 같습니다.

   ```
        mountpoints:
            /:
            url: https://author-p133911-e1313554.adobeaemcloud.com/bin/franklin.delivery/wkndform/aemcrosswalk/main
            type: "markup"
            suffix: ".html"
   ```

1. 변경 사항을 `fstab.yaml` 파일에 커밋합니다.

### GitHub 저장소에 AEM 인스턴스 연결

AEM Forms 작성자 인스턴스를 [GitHub 저장소의 프로젝트](/help/edge/docs/forms/tutorial.md)에 연결하도록 다음 단계를 수행합니다.

[1. Edge Delivery Services 템플릿 기반 적응형 양식 만들기](#1-create-an-adaptive-form-based-on-the-edge-delivery-services-template)

[2. AEM 작성자 인스턴스에서 양식의 구성 컨테이너 찾기](#2-locate-your-forms-configuration-container-in-aem-author-instance)

[3. 범용 편집기에서 양식 작성](#3-author-the-form-in-the-universal-editor)

[4. 양식 게시 및 미리보기](#4-publish-and-preview-the-form)

#### 1. Edge Delivery Services 템플릿 기반 적응형 양식 만들기

1. AEM Forms as a Cloud Service 작성자 인스턴스에 액세스합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다. 1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 마법사가 열립니다. 소스 탭에서 FormTemplate 기반 Edge Delivery Services를 선택합니다.

   ![EDS 양식 만들기](/help/edge/assets/create-eds-forms.png){width=50%, align-center}

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하면 **양식 만들기** 마법사가 나타납니다.
1. **GitHub URL**을 지정합니다. 예를 들어 GitHub 저장소의 이름이 “aemcrosswalk”이고 “wkndform” 계정 아래에 있는 경우 URL은 다음과 같습니다.
   `https://github.com/wkndform/aemcrosswalk`
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![생성 마법사 만들기](/help/edge/assets/create-form-wizard.png){width=50%, align-center}

   **[!UICONTROL 만들기]**&#x200B;를 클릭하자마자 범용 편집기에서 작성할 양식이 열립니다.

   ![양식 작성](/help/edge/assets/author-form.png){width=50%, align-center}

   >[!NOTE]
   >
   > 양식의 구성 컨테이너에 Edge Delivery Services 템플릿 기반 양식에 대한 Edge Delivery Services 구성이 자동으로 생성됩니다.

#### 2. AEM 작성자 인스턴스에서 양식의 구성 컨테이너 찾기

1. AEM Forms as a Cloud Service 작성자 인스턴스에서 **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Edge Delivery Services 구성]**&#x200B;으로 이동합니다.
1. 양식 이름과 일치하는 폴더를 선택합니다. 예를 들어 양식 이름이 “contact-us”인 경우 폴더 `forms/contact-us`를 선택한 다음 구성을 선택하고 구성을 게시합니다.

   ![Edge Delivery Services 구성](/help/forms/assets/aem-instance-eds-configuration.png){width=50%, align-center}

1. **[!UICONTROL 속성]**&#x200B;을 클릭하여 구성을 확인합니다.\
   ![자동으로 생성된 구성](/help/edge/assets/aem-forms-create-configuration-github.png){width=50%, align-center}

   Edge Host 옵션을 그대로 둘 수 있습니다. 양식은 미리보기(.page) 및 라이브(.live) 환경 모두에 게시됩니다.

1. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 구성이 저장됩니다.

#### 3. 범용 편집기에서 양식 작성

**[!UICONTROL 만들기]**&#x200B;를 클릭하면 범용 편집기에서 작성할 양식이 열립니다.

1. 콘텐츠 브라우저를 열고 **콘텐츠 트리**&#x200B;의 **[!UICONTROL 적응형 양식]** 구성 요소로 이동합니다.

   ![콘텐츠 트리](/help/edge/assets/content-tree.png){width=50%, align-center}

1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성요소** 목록에서 원하는 구성 요소를 추가합니다.

   ![구성 요소 추가](/help/edge/assets/add-component.png){width=50%, align-center}

1. 추가된 적응형 양식 구성요소를 선택하고 **[!UICONTROL 속성]**&#x200B;을 사용하여 해당 속성을 업데이트합니다.

   ![속성 열기](/help/edge/assets/component-properties.png){width=50%, align-center}

   아래 스크린샷에 범용 편집기에서 작성된 간단한 “문의” 양식이 표시됩니다.

   ![문의 양식](/help/edge/assets/contact-us.png){width=50%, align-center}

#### 4. 양식 게시 및 미리보기

이제 범용 편집기 오른쪽 상단의 **[!UICONTROL 게시]** 버튼을 클릭하여 양식을 Edge Delivery Services에 게시합니다.

![양식 게시](/help/edge/assets/publish-form.png){width=50%, align-center}


Edge Delivery Services에서 양식에 액세스하는 방법은 다음과 같습니다.

* **스테이징된 버전(테스트용)**: 스테이징된 버전에 테스트 목적으로 게시 취소된 양식의 작업 버전이 표시됩니다. 다음 URL 형식을 사용하여 양식이 라이브로 전환되기 전에 미리 봅니다.

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  예를 들어 프로젝트 저장소의 이름이 “aemcrosswalk”이고 “wkndform” 계정 아래에서 “main” 분기 및 양식을 “문의”로 사용하는 경우 스테이징된 버전 URL은 다음과 같습니다.
https://main--aemcrosswalk--wkndform.aem.page/content/forms/af/contact-us

* **라이브 버전(게시된 양식)**: 라이브 버전에 최종 사용자가 액세스할 수 있는 최근 게시된 양식 버전이 표시됩니다. 다음 URL 형식을 사용하여 게시된 양식의 라이브 버전에 액세스합니다.

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  예를 들어 프로젝트 저장소의 이름이 “aemcrosswalk”이고 “wkndform” 계정 아래에서 “main” 분기 및 양식을 “문의”로 사용하는 경우 스테이징된 버전 URL은 다음과 같습니다.
https://main--aemcrosswalk--wkndform.aem.live/content/forms/af/contact-us

URL 구조는 스테이징된 버전과 라이브 버전 모두에서 동일하게 유지됩니다. 단, 컨텍스트에 따라 표시되는 콘텐츠가 달라집니다.

![게시된 양식 보기](/help/edge/assets/eds-view-publish-form.png){width=50%, align-center}

## 문제 해결

양식을 로딩하는 데 문제가 있습니까? 여기 몇 가지 일반적인 문제와 해결 방법이 있습니다.

* **양식 URL**: 양식의 URL 끝에 “.html” 확장 기능이 포함되어 있지 않은지 두 번 확인합니다. Edge Deliver Service에는 이 확장 기능이 필요하지 않습니다.

* **AEM 작성자 UR** L: `fstab.yaml` 파일에 나열된 AEM 작성자 URL 형식이 올바른지 확인합니다. 다음 세부 정보가 포함되어야 합니다.

   * 올바른 GitHub 소유자
   * 올바른 저장소 이름
   * Edge Delivery Services에 사용 중인 특정 분기

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## 추가 참조

{{see-more-forms-eds}}
