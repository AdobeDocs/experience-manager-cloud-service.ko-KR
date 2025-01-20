---
title: Edge Delivery Services을 위한 Forms 게시
description: Forms 게시가 Edge Delivery Services에서 작동하는 방법 및 Edge Delivery Services에서 AEM Forms를 게시하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---


# Edge Delivery Services을 위한 Forms 게시

이 문서에서는 AEM Edge Delivery Services에 양식을 게시하는 프로세스를 안내합니다.
양식을 Edge Delivery Services에 게시하려면 먼저 AEM 환경과 GitHub 리포지토리 간에 연결을 설정해야 합니다. 연결되면 범용 편집기를 사용하여 양식을 작성할 수 있습니다. 이 편집기는 WYSIWYG(What You See Is What You Get) 접근 방식을 따라 Sites를 사용하여 매끄럽고 일관된 사용자 경험을 제공합니다.

## 전제 조건

* 적응형 Forms을 처음 사용하십니까? 제공된 [자습서](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)에 따라 GitHub 리포지토리를 설정합니다.
* 이미 Edge Delivery Services을 사용 중인 경우 [적응형 Forms 블록](/help/edge/docs/forms/tutorial.md#)의 최신 버전을 GitHub 저장소에 추가하십시오.
* AEM Forms 작성자 인스턴스에는 Edge Delivery Services 기반의 템플릿이 포함되어 있습니다. [최신 버전의 핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)가 환경에 설치되어 있는지 확인하십시오.
* AEM Forms as a Cloud Service 작성자 인스턴스와 GitHub 리포지토리의 URL을 바로 사용할 수 있습니다.

## Edge Delivery Services용 Publish Forms

Edge Delivery Services에 대한 양식을 게시하려면 아래 단계를 수행하십시오.

[1. AEM 인스턴스에 GitHub 저장소 연결](#link-github-repository-to-aem-instance)

[2. AEM 인스턴스를 GitHub 저장소에 연결](#link-aem-instance-to-github-repository)

### AEM 인스턴스에 GitHub 저장소 연결

[GitHub 저장소의 프로젝트](/help/edge/docs/forms/tutorial.md)를 AEM Forms 작성자 인스턴스에 연결하려면 다음 단계를 수행하십시오.

1. Edge Delivery Services에 대해 만들거나 구성한 GitHub 저장소로 이동합니다.
1. 편집할 `fstab.yaml` 페이지를 엽니다.
1. AEM Forms as a Cloud Service 인스턴스의 URL을 사용하여 GitHub 저장소의 `fstab.yaml` 파일을 업데이트합니다.

   ```javascript
    mountpoints:
    /:
        url: [author-instance-url]/bin/franklin.delivery/[Github owner]/[Github Repository]/[Github branch] 
        type: "markup"
        suffix: ".html"
   ```

   예를 들어 GitHub 리포지토리의 이름이 &quot;aem횡단보도&quot;이고 계정 &quot;wkndform&quot; 아래에 있으며 &quot;주&quot; 분기를 사용하는 경우 작성자 인스턴스 URL은 다음과 같습니다.

   ```
        mountpoints:
            /:
            url: https://author-p133911-e1313554.adobeaemcloud.com/bin/franklin.delivery/wkndform/aemcrosswalk/main
            type: "markup"
            suffix: ".html"
   ```

1. `fstab.yaml` 파일에 변경 내용을 커밋합니다.

### GitHub 저장소에 AEM 인스턴스 연결

AEM Forms 작성자 인스턴스를 [GitHub 저장소의 프로젝트](/help/edge/docs/forms/tutorial.md)에 연결하려면 다음 단계를 수행하십시오.

[1. Edge Delivery Services 템플릿을 기반으로 적응형 양식 만들기](#1-create-an-adaptive-form-based-on-the-edge-delivery-services-template)

[2. AEM 작성자 인스턴스에서 양식의 구성 컨테이너를 찾습니다](#2-locate-your-forms-configuration-container-in-aem-author-instance)

[3. 유니버설 편집기에서 양식 작성](#3-author-the-form-in-the-universal-editor)

[4. Publish 및 양식 미리 보기](#4-publish-and-preview-the-form)

#### 1. Edge Delivery Services 템플릿을 기반으로 적응형 양식 만들기

1. AEM Forms as a Cloud Service 작성자 인스턴스에 액세스합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.1을 선택합니다. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 Forms]**&#x200B;을(를) 선택합니다. 마법사가 열립니다. Source 탭에서 Edge Delivery Services 기반 양식 템플릿을 선택합니다.

   ![EDS Forms 만들기](/help/edge/assets/create-eds-forms.png){width=50%, align-center}

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하면 **양식 만들기** 마법사가 나타납니다.
1. **GitHub URL**을(를) 지정하십시오. 예를 들어 GitHub 리포지토리의 이름이 &quot;aemcrossway&quot;이고, &quot;wkndform&quot; 계정 아래에 있는 경우 URL은 다음과 같습니다.
   `https://github.com/wkndform/aemcrosswalk`
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![양식 만들기 마법사](/help/edge/assets/create-form-wizard.png){width=50%, align-center}

   **[!UICONTROL 만들기]**&#x200B;를 클릭하면 작성용 유니버설 편집기에서 양식이 열립니다.

   ![양식 작성자](/help/edge/assets/author-form.png){width=50%, align-center}

   >[!NOTE]
   >
   > Edge Delivery Services 템플릿을 기반으로 하는 양식에 대한 Edge Delivery Services 구성은 양식의 구성 컨테이너에서 자동으로 만들어집니다.

#### 2. AEM 작성자 인스턴스에서 양식의 구성 컨테이너를 찾습니다

1. AEM Forms as a Cloud Service 작성자 인스턴스의 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Edge Delivery Services 구성]**(으)로 이동합니다.
1. 양식 이름과 일치하는 폴더를 선택합니다. 예를 들어 양식을 &#39;contact-us&#39;라고 하는 경우 `forms/contact-us` 폴더를 선택하고 구성을 선택한 다음 구성을 게시합니다.

   ![Edge Delivery Services 구성](/help/forms/assets/aem-instance-eds-configuration.png){width=50%, align-center}

1. 구성을 보려면 **[!UICONTROL 속성]**&#x200B;을 클릭하세요.\
   ![자동으로 생성된 구성](/help/edge/assets/aem-forms-create-configuration-github.png){width=50%, align-center}

   Edge 호스트 옵션은 그대로 둘 수 있습니다. 양식은 미리보기(.page) 및 라이브(.live) 환경 모두에 게시됩니다.

1. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 구성이 저장됩니다.

#### 3. 유니버설 편집기에서 양식 작성

**[!UICONTROL 만들기]**&#x200B;를 클릭하면 작성을 위해 유니버설 편집기에서 양식이 열립니다.

1. 콘텐츠 브라우저를 열고 **콘텐츠 트리**&#x200B;에서 **[!UICONTROL 적응형 양식]** 구성 요소로 이동합니다.

   ![콘텐츠 트리](/help/edge/assets/content-tree.png){width=50%, align-center}

1. **[!UICONTROL 추가]** 아이콘을 클릭하고 **적응형 양식 구성 요소** 목록에서 원하는 구성 요소를 추가하십시오.

   ![구성 요소 추가](/help/edge/assets/add-component.png){width=50%, align-center}

1. 추가된 적응형 양식 구성 요소를 선택하고 **[!UICONTROL 속성]**&#x200B;을 사용하여 속성을 업데이트합니다.

   ![속성 열기](/help/edge/assets/component-properties.png){width=50%, align-center}

   아래 스크린샷에는 범용 편집기에서 작성된 간단한 &quot;Contact Us&quot; 양식이 표시됩니다.

   ![문의하기 양식](/help/edge/assets/contact-us.png){width=50%, align-center}

#### 4. Publish 및 양식 미리 보기

이제 범용 편집기의 오른쪽 상단에 있는 **[!UICONTROL Publish]** 단추를 클릭하여 양식을 Edge Delivery Services에 게시합니다.

![양식 게시](/help/edge/assets/publish-form.png){width=50%, align-center}


다음은 Edge Delivery Services에서 양식에 액세스하는 방법입니다.

* **테스트용 준비 버전**: 준비 버전에는 테스트 목적으로 양식의 게시되지 않은 작업 버전이 표시됩니다. 다음 URL 형식을 사용하여 양식을 시작하기 전에 미리 봅니다.

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  예를 들어 프로젝트의 저장소 이름이 &quot;aemcrossway&quot;이고 계정 &quot;wkndform&quot; 아래에 있으며 &quot;main&quot; 분기 및 양식을 &quot;contact us&quot;로 사용하는 경우 스테이징된 버전 URL은 다음과 같습니다.
https://main--aemcrosswalk--wkndform.aem.page/content/forms/af/contact-us

* **라이브 버전(게시된 양식)**:   라이브 버전에는 최종 사용자가 액세스할 수 있는 가장 최근에 게시된 양식 버전이 표시됩니다. 다음 URL 형식을 사용하여 양식의 게시된 라이브 버전에 액세스합니다.

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  예를 들어 프로젝트의 저장소 이름이 &quot;aemcrossway&quot;이고 계정 &quot;wkndform&quot; 아래에 있으며 &quot;main&quot; 분기 및 양식을 &quot;contact us&quot;로 사용하는 경우 스테이징된 버전 URL은 다음과 같습니다.
https://main--aemcrosswalk--wkndform.aem.live/content/forms/af/contact-us

URL 구조는 스테이징된 버전과 라이브 버전 모두에 대해 동일하게 유지됩니다. 하지만 표시되는 콘텐츠는 컨텍스트에 따라 다릅니다.

![게시된 양식 보기](/help/edge/assets/eds-view-publish-form.png){width=50%, align-center}

## 문제 해결

양식을 로드하는 데 문제가 있습니까? 다음은 몇 가지 일반적인 문제와 해결 방법입니다.

* **양식 URL**: 양식의 URL에 끝에 &quot;.html&quot; 확장명이 포함되어 있지 않은지 다시 확인하십시오. Edge Deliver Service에는 이 확장이 필요하지 않습니다.

* **AEM 작성자 URL** L: `fstab.yaml` 파일에 나열된 AEM 작성자 URL의 형식이 올바른지 확인하십시오. 여기에는 다음 세부 정보가 포함되어야 합니다.

   * 올바른 GitHub 소유자
   * 올바른 저장소 이름
   * Edge Delivery Services에 사용하는 특정 분기

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## 추가 참조

{{see-more-forms-eds}}