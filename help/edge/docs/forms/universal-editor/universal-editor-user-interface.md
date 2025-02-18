---
title: 범용 편집기 이해 - 개발자 자습서
description: 이 자습서는 범용 편집기 인터페이스를 시작하고 실행하는 데 도움이 됩니다. 범용 편집기에서 나만의 Edge Delivery Services 양식을 만들 수 있는 사용자 인터페이스를 이해하는 데 도움이 됩니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
source-git-commit: f62bccacd3252422899a35d2b431450c919982de
workflow-type: tm+mt
source-wordcount: '1495'
ht-degree: 5%

---


# 범용 편집기(WYSIWYG) 인터페이스 살펴보기

[유니버설 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)는 Adobe EDS(Edge Delivery Services) Forms을 위한 간단하고, 시각적이며, 직관적인 What You See Is What You Get(WYSIWYG) 인터페이스를 제공합니다. 효율적인 양식 작성을 위한 드래그 앤 드롭 기능이 있는 최신 인터페이스를 제공합니다.

![유니버설 편집기 사용자 인터페이스](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## 범용 편집기 인터페이스 이해

양식 작성자가 범용 편집기를 사용하여 양식을 편집하면 콘솔에서 대화형 WYSIWYG 인터페이스가 열리고 사용자가 양식 편집을 시작할 수 있습니다.

>[!NOTE]
>
> 범용 편집기를 사용하여 양식을 작성하는 방법에 대해 알아보려면 문서 [범용 편집기를 사용하여 Edge Delivery Services for AEM Forms 시작하기(WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)를 참조하십시오.

![유니버설 편집기 사용자 인터페이스](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

범용 편집기 인터페이스는 다음 네 가지 부분으로 나뉘어져 있습니다.

* **[A: Experience Cloud 헤더](#experience-cloud-header)**
* **[B: 유니버설 편집기 도구 모음](#universal-editor-toolbar)**
* **[C: 속성 패널](#properties-panel)**
* **[D: 편집기](#editor)**

### Experience Cloud 헤더

Experience Cloud 헤더는 콘솔의 맨 위에 있습니다. Experience Cloud 내의 현재 위치에 대한 정보를 제공합니다. 또한 다른 Experience Cloud 애플리케이션으로 이동할 수도 있습니다.

![유니버설 편집기 Experience Cloud 헤더](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)


각 구성 요소를 살펴보겠습니다.

* **Adobe Experience Cloud**

  화면 왼쪽에 있는 **Adobe Experience Cloud** 링크를 클릭하여 Experience Manager 솔루션의 루트로 이동하고 Experience Manager Sites, Experience Manager Assets 및 Experience Manager Guides과 같은 도구에 액세스할 수 있습니다.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png){width=50%,height=50%}

* **조직 이름**

  **조직 이름**&#x200B;에 현재 로그인한 IMS 조직의 이름이 표시됩니다. 다른 조직에 대한 액세스 권한이 있는 경우 드롭다운 목록에서 을(를) 선택하여 다른 IMS 조직으로 전환할 수 있습니다. 예를 들어 현재 선택한 IMS 조직 이름은 `AEM Forms Internal01`입니다.

  ![조직](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png){width=50%,height=50%}


* **도움말**

  도움말 아이콘을 통해 학습 및 지원 리소스에 빠르게 액세스할 수 있습니다. 양식 작성자는 **도움말** 섹션에서 피드백을 추가할 수도 있습니다.
  ![도움말](/help/edge/docs/forms/universal-editor/assets/ue-help.png){width=50%,height=50%}


* **알림**

  **알림** 섹션에는 IMS 조직에서 현재 할당된 불완전한 알림, 요청 및 현재 작업의 수가 표시됩니다.

  ![알림](/help/edge/docs/forms/universal-editor/assets/ue-notification.png){width=50%,height=50%}


* **솔루션**

  **솔루션** 링크를 사용하여 다른 Experience Cloud 솔루션으로 전환할 수 있습니다.
  ![솔루션](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png){width=50%,height=50%}


* **작성자**
아이콘은 양식 작성자의 세부 정보를 나타내며, 작성자가 현재 로그인한 IMS 조직의 이름을 표시합니다.
  ![작성자](/help/edge/docs/forms/universal-editor/assets/ue-author.png){width=50%,height=50%}

### 범용 편집기 도구 모음

도구 모음을 사용하여 다른 양식으로 이동하여 편집할 수 있습니다. 또한 양식을 게시 또는 게시 취소하고, 양식의 속성을 편집하고, 규칙 편집기에 액세스할 수 있습니다.
![유니버설 편집기 도구 모음](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

각 구성 요소를 살펴보겠습니다.

* **홈 단추**
홈 버튼을 사용하면 범용 편집기의 시작 페이지로 이동할 수 있습니다. 범용 편집기를 사용하여 편집할 양식의 URL을 직접 입력할 수도 있습니다.
  ![유니버설 편집기 홈](/help/edge/docs/forms/universal-editor/assets/ue-home.png)



* **위치 표시줄**
**위치 표시줄**&#x200B;에는 작성자가 편집 중인 양식 주소가 표시됩니다. 위치 표시줄을 클릭하여 다른 양식 URL을 입력할 수도 있습니다. 위치 표시줄을 여는 바로 가기 키는 `l` 키입니다.
  ![위치 표시줄](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png){width=50%,height=50%}



* **규칙 편집기**

  **규칙 편집기**&#x200B;는 규칙을 만들고 관리하기 위한 직관적인 시각적 인터페이스를 제공합니다. 규칙 편집기를 사용하여 동적 양식 동작을 추가할 수 있습니다.

  ![규칙 편집기](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > * 범용 편집기에서 규칙 편집기 확장은 기본적으로 활성화되어 있지 않습니다. 규칙 편집기 확장을 사용하려면 공식 전자 메일 ID에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)에 전자 메일을 보내십시오.
  > * 규칙을 만드는 방법에 대해 알아보려면 문서 [WYSIWYG 작성의 규칙 편집기 소개](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md)를 참조하십시오.

* **양식 속성 편집**
**양식 속성 편집** 옵션을 클릭하여 양식 데이터 모델 및 게시 날짜와 같은 양식 속성을 편집할 수 있습니다.
  ![양식 속성 편집](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)



* **인증 헤더 설정**
작성자는 **인증 헤더 설정**을 통해 로컬 개발을 위해 사용자 지정 인증 헤더를 설정할 수 있습니다.
  ![인증 헤더](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png){width=50%,height=50%}



* **응답형 모드**
  **응답형 모드** 옵션을 사용하면 유니버설 편집기에서 양식을 렌더링하는 방법을 정의할 수 있습니다. 기본적으로 편집기는 데스크탑 레이아웃으로 열리고, 여기서 높이와 너비는 브라우저에 의해 자동으로 결정됩니다. 또는 모바일 장치를 에뮬레이션하고 양식이 모바일 장치에 어떻게 표시되는지 확인하도록 선택할 수 있습니다.

  ![응답형 모드](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=50%,height=50%}


* **미리 보기 모드**
미리보기 모드에서 양식은 게시되는 대로 편집기에 나타납니다. 이렇게 하면 작성자는 링크 및 버튼을 클릭하여 양식을 탐색할 수 있습니다. 편집한 내용이 만족스러우면 작성자는 라이브 사용자를 위해 양식을 게시할 수 있습니다. 편집 모드와 미리 보기 모드 간에 전환하는 바로 가기 키는 `p`입니다.
  ![미리보기](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

* **페이지 열기**
**페이지 열기** 옵션을 사용하면 미리 볼 수 있도록 새 탭에서 양식이 열립니다. 새 탭에서 미리 보기 모드로 양식을 여는 바로 가기 키는 `o`입니다.
  ![페이지 열기](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

* **게시**

  **게시** 단추를 사용하여 Live 사용자가 양식을 사용할 수 있도록 할 수 있습니다.
  ![게시](/help/edge/docs/forms/universal-editor/assets/ue-publish.png){width=50%,height=50%}

* **줄임표**
작성자가 줄임표(...) 옵션을 클릭하면 **게시 취소** 옵션이 나타납니다. **게시 취소** 옵션을 사용하여 양식 게시를 취소할 수 있습니다.
  ![줄임표](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png){width=50%,height=50%}

### 속성 패널

**속성 패널**은(는) 편집기의 오른쪽에 있습니다. 양식의 계층에서 선택한 구성 요소에 대한 세부 정보가 표시됩니다. 이 구조는 선택한 구성 요소가 없을 때의 기본 구조입니다.
![ue-properties 패널](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png){width=50%,height=50%}


각 구성 요소를 살펴보겠습니다.


* **속성 모드**
**속성** 옵션에서 편집기에서 선택한 구성 요소의 속성을 표시합니다. 예를 들어 선택한 숫자 입력 구성 요소의 속성이 이미지에 표시됩니다. 이 옵션을 사용하여 구성 요소의 속성을 수정할 수 있습니다. 구성 요소의 속성을 여는 바로 가기 키는 `d`입니다.

  ![ue-properties](/help/edge/docs/forms/universal-editor/assets/ue-properties.png){width=50%,height=50%}


* **콘텐츠 트리**
**콘텐츠 트리** 옵션은 양식의 계층을 표시합니다. 작성자가 콘텐츠 트리에서 항목을 클릭하면 편집기가 해당 구성 요소를 선택하고 스크롤합니다. 콘텐츠 트리 보기 간에 전환할 바로 가기 키는 `f` 키입니다.

  ![콘텐츠 트리](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png){width=50%,height=50%}


* **변형 생성**
  **변형 생성**&#x200B;은(는) 인공 지능을 사용하여 특정 프롬프트에 따라 다른 버전의 양식을 생성합니다. 이러한 프롬프트는 Adobe에서 제공하거나 양식 작성자가 제작 및 관리할 수 있습니다.

  ![변형](/help/edge/docs/forms/universal-editor/assets/ue-variations.png){width=50%,height=50%}


  >[!NOTE]
  >
  > 양식의 변형 생성 사용에 대한 지침은 [변형 생성](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/generative-ai/generate-variations) 문서를 참조하십시오

* **실험**:

  **실험**은(는) 사용자 경험과 성능을 최적화하기 위해 다양한 양식 및 레이아웃을 테스트하는 데 사용되는 기술을 말합니다.
  ![실험](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png){width=50%,height=50%}


* **Personalization**
**Personalization** 옵션은 Adobe 에코시스템 또는 외부 응용 프로그램의 일부인 양식과 Adobe Experience Platform(AEP) 간에 연결을 설정하도록 설정을 구성합니다.
  ![Personalization](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png){width=50%,height=50%}


* **A/B 테스트**:
  **A/B 테스트**는 사용자 경험과 성능을 최적화하기 위해 다양한 양식 및 레이아웃을 테스트하는 데 사용되는 기술을 말합니다.
  ![A/B 테스트](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png){width=50%,height=50%}



* **작업 관리**:
**작업 관리** 기능을 사용하면 팀에서 양식의 사용자 지정 및 최적화와 관련된 작업을 관리, 추적 및 실행할 수 있으므로 워크플로를 간소화하고 공동 작업을 향상시킬 수 있습니다
  ![작업 관리](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png){width=50%,height=50%}

.
* **콘텐츠 초안**

  **콘텐츠 초안** 옵션을 사용하면 서식 있는 텍스트 요소에 대한 초안을 만들 수 있습니다. 초안은 기존 양식 텍스트를 사용하거나 처음부터 만들 수 있습니다. 필요에 따라 초안을 편집하거나 삭제할 수 있습니다. 기본적으로 3개의 초안만 표시되지만 **모두 표시**&#x200B;를 클릭하면 나머지 초안이 표시됩니다.

  ![작업 관리](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png){width=50%,height=50%}


* **데이터 Source**

  **데이터 Source** 옵션을 사용하면 FDM(양식 데이터 모델)을 만들 때 데이터 소스를 구성하고 선택할 수 있습니다. 선택한 데이터 소스의 모든 데이터 모델 개체, 속성 및 서비스를 양식 데이터 모델에서 사용할 수 있도록 합니다.
  ![데이터 Source](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png){width=50%,height=50%}

* **추가**

  **추가** 옵션을 사용하면 선택한 컨테이너에 추가할 수 있는 구성 요소의 드롭다운 목록이 열립니다. 예를 들어 적응형 양식 섹션의 목록에는 양식에 추가할 수 있는 사용 가능한 구성 요소가 표시됩니다. 구성 요소 목록을 여는 바로 가기 키는 `a`입니다.
  ![아이콘 추가](/help/edge/docs/forms/universal-editor/assets/ue-add.png){width=50%,height=50%}

* **복제**

  **복제** 옵션은 콘텐츠 트리 또는 편집기에서 선택한 구성 요소의 복사본을 만듭니다.
  ![중복 아이콘](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png){width=50%,height=50%}


* **삭제**
**삭제** 옵션은 콘텐츠 트리 또는 편집기에서 선택한 구성 요소를 삭제합니다.

  ![삭제](/help/edge/docs/forms/universal-editor/assets/ue-delete.png){width=50%,height=50%}

### 편집기

편집기에서 양식을 편집할 수 있고 위치 표시줄에 지정된 양식이 편집 영역에서 렌더링됩니다. 편집기가 미리보기 모드일 경우 사용 가능한 버튼과 링크를 사용하여 양식을 탐색할 수 있습니다.
![편집기](/help/edge/docs/forms/universal-editor/assets/ue-editor.png){width=50%,height=50%}

## 추가 참조

* [AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/tutorial.md)
* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수신 시작&#x200B;](/help/edge/docs/forms/submit-forms.md)
* [양식 게시 및 데이터 수집 시작](/help/edge/docs/forms/publish-forms.md)
* [양식 모양 사용자 정의&#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [양식에 반복 가능한 섹션 추가&#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [양식 제출 후 사용자 정의 감사 메시지 표시&#x200B;](/help/edge/docs/forms/thank-you-page-form.md)
* [적응형 양식 블록 구성 요소 및 해당 속성](/help/edge/docs/forms/form-components.md)
* [실제 사용 모니터링](https://www.aem.live/developer/rum#authentication)


