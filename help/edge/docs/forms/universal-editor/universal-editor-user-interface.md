---
title: 범용 편집기 이해
description: 이 자습서는 범용 편집기 인터페이스를 시작하고 실행하는 데 도움이 됩니다. 범용 편집기에서 나만의 Edge Delivery Services 양식을 만들 수 있는 사용자 인터페이스를 이해하는 데 도움이 됩니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 1%

---


# 범용 편집기(WYSIWYG) 인터페이스 살펴보기

[범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)에서는 Adobe Edge Delivery Services Forms에 대해 간단하고, 시각적이며, 직관적인 WYSIWYG(What You See Is What You Get) 인터페이스를 제공합니다. 효율적인 양식 작성을 위한 드래그 앤 드롭 기능이 있는 최신 인터페이스를 제공합니다.

![유니버설 편집기 사용자 인터페이스](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## 학습 내용

이 자습서를 마치면 다음 작업을 수행할 수 있습니다.

- 범용 편집기 인터페이스의 기본 구성 요소 이해
- 다양한 인터페이스 섹션을 자신 있게 탐색합니다.
- 필수 양식 작성 도구에 액세스하고 사용하는 방법을 이해할 수 있습니다
- 생산성을 높이는 키보드 단축키 숙지

## 범용 편집기 인터페이스 이해

범용 편집기를 사용하여 양식을 편집하면 콘솔에서 편집을 바로 시작할 수 있는 대화형 WYSIWYG 인터페이스가 열립니다. 이 인터페이스는 작업하는 동안 폼이 최종 사용자에게 표시되는 방식을 정확하게 보여 주는 실시간 시각적 피드백을 제공합니다.

>[!NOTE]
>
> 범용 편집기를 사용하여 양식을 작성하는 방법에 대해 알아보려면 문서 [범용 편집기를 사용하여 Edge Delivery Services for AEM Forms 시작하기(WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)를 참조하십시오.

![유니버설 편집기 사용자 인터페이스](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

유니버설 편집기 인터페이스는 다음 네 가지 논리적 부분으로 나뉘어져 있습니다.

- **[A: Experience Cloud 헤더](#experience-cloud-header)**
- **[B: 유니버설 편집기 도구 모음](#universal-editor-toolbar)**
- **[C: 속성 패널](#properties-panel)**
- **[D: 편집기](#editor)**

각 섹션을 자세히 살펴보겠습니다.

### Experience Cloud 헤더

Experience Cloud 헤더는 콘솔 상단에 표시되며 더 광범위한 Adobe Experience Cloud 에코시스템 내에서 탐색 컨텍스트를 제공합니다. 사용자의 현재 위치를 표시하고 다른 Experience Cloud 애플리케이션에 빠르게 액세스할 수 있습니다.

![유니버설 편집기 Experience Cloud 헤더](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

각 구성 요소를 살펴보겠습니다.

- **Adobe Experience Cloud**

  화면 왼쪽에 있는 **Adobe Experience Cloud** 링크를 클릭하면 Experience Manager 솔루션의 루트로 이동할 수 있습니다. 여기에서 Experience Manager Sites, Experience Manager Assets 및 Experience Manager Guides과 같은 다른 도구에 액세스할 수 있습니다.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png)

- **조직 이름**

  **조직 이름**&#x200B;에 현재 로그인한 Identity Management System(IMS) 조직의 이름이 표시됩니다. 여러 조직에 대한 액세스 권한이 있는 경우 이 드롭다운 메뉴를 사용하여 조직 간을 전환할 수 있습니다. 예를 들어 스크린샷에서 현재 선택한 IMS 조직은 &quot;AEM Forms Internal01&quot;입니다.

  ![조직](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png)

- **도움말**

  도움말 아이콘을 통해 학습 및 지원 리소스에 빠르게 액세스할 수 있습니다. 이 기능은 문제가 발생하거나 특정 기능에 대한 지침이 필요한 경우에 특히 유용합니다. 이 섹션을 통해 피드백을 제출할 수도 있습니다.

  ![도움말](/help/edge/docs/forms/universal-editor/assets/ue-help.png)

- **알림**

  **알림** 섹션에는 IMS 조직에서 현재 할당된 불완전한 알림, 요청 및 현재 작업의 수가 표시됩니다. 이 섹션을 주시하면 워크플로우를 최신 상태로 유지하는 데 도움이 됩니다.

  ![알림](/help/edge/docs/forms/universal-editor/assets/ue-notification.png)

- **솔루션**

  **솔루션** 메뉴를 사용하면 다른 Adobe Experience Cloud 솔루션으로 전환할 수 있으므로 워크플로우의 다양한 도구 간에 쉽게 이동할 수 있습니다.

  ![솔루션](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png)

- **사용자 프로필**

  이 아이콘에는 현재 로그인한 IMS 조직의 이름과 함께 프로필 정보가 표시됩니다. 계정 설정 및 로그아웃 옵션에 액세스하려면 이 아이콘을 클릭하십시오.

  ![작성자](/help/edge/docs/forms/universal-editor/assets/ue-author.png)

### 범용 편집기 도구 모음

도구 모음에서는 필수 탐색 및 편집 도구를 제공합니다. 이를 통해 양식 간에 이동하거나, 양식을 게시 또는 게시 취소하고, 양식 속성을 편집하고, 규칙 편집기에 액세스하여 동적 동작을 추가할 수 있습니다.

![유니버설 편집기 도구 모음](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

각 구성 요소가 제공하는 기능은 다음과 같습니다.

- **홈 단추**

  홈 버튼을 누르면 유니버설 편집기의 시작 페이지로 돌아갑니다. 이 기능은 다른 양식에서 작업을 시작해야 할 때 유용합니다. 위치 표시줄에 URL을 직접 입력하여 편집할 양식으로 이동할 수도 있습니다.

  ![유니버설 편집기 홈](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

- **위치 표시줄**

  **위치 표시줄**&#x200B;에 현재 편집 중인 양식 주소가 표시됩니다. 다른 양식으로 전환하려면 위치 표시줄을 클릭하고 해당 URL을 입력하면 됩니다. 위치 표시줄의 포커스를 설정하는 키보드 단축키는 `l`입니다.

  ![위치 표시줄](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

- **규칙 편집기**

  **규칙 편집기**&#x200B;를 사용하면 직관적인 시각적 인터페이스를 통해 양식에 동적 동작을 추가할 수 있습니다. 이를 통해 사용자 입력에 응답하는 조건, 유효성 검사 및 작업을 만들어 양식을 대화형 및 지능적으로 만들 수 있습니다.

  ![규칙 편집기](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > - 규칙 편집기 확장은 범용 편집기에서 기본적으로 활성화되어 있지 않습니다. 이 강력한 기능을 사용하려면 공식 전자 메일 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 문의하세요.
  > - 규칙을 만들고 관리하는 방법에 대해 알아보려면 문서 [WYSIWYG 작성의 규칙 편집기 소개](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md)를 참조하십시오.

- **양식 속성 편집**

  **양식 속성 편집** 옵션을 사용하면 FDM(양식 데이터 모델) 및 게시 날짜와 같은 중요한 양식 설정을 구성할 수 있습니다. 이러한 속성은 폼이 백 엔드 시스템에서 작동하고 통합되는 방식에 영향을 줍니다.

  ![양식 속성 편집](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

- **인증 헤더 설정**

  **인증 헤더 설정** 옵션을 사용하면 로컬 개발 목적으로 사용자 지정 인증 헤더를 설정할 수 있습니다. 이 기능은 인증 자격 증명이 필요한 양식을 테스트할 때 특히 유용합니다.

  ![인증 헤더](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

- **응답형 모드**

  **응답 모드** 기능을 사용하면 양식이 다양한 장치에 어떻게 표시되는지 테스트할 수 있습니다. 기본적으로 편집기는 데스크탑 레이아웃으로 열리지만, 모바일 보기로 전환하여 작은 화면에서 양식을 사용할 수 있고 매력적인 상태로 유지할 수 있습니다.

  ![응답형 모드](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

- **미리 보기 모드**

  **미리 보기 모드**&#x200B;는 게시할 때 표시되는 양식과 동일하게 양식을 표시합니다. 이렇게 하면 사용자와 마찬가지로 링크 및 단추를 클릭하여 양식과 상호 작용할 수 있습니다. 모든 것이 예상대로 작동하는지 확인하기 위해 게시하기 전에 반드시 수행해야 하는 단계입니다. 키보드 단축키 `p`을(를) 사용하여 편집 모드와 미리 보기 모드 간을 전환합니다.

  ![미리보기](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

- **페이지 열기**

  **페이지 열기** 단추를 사용하면 미리 볼 수 있도록 새 브라우저 탭에서 양식이 열립니다. 이렇게 하면 편집기 인터페이스 없이 폼의 전체 화면을 볼 수 있습니다. 이 작업의 바로 가기 키는 `o`입니다.

  ![페이지 열기](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

- **게시**

  양식을 사용자가 사용할 수 있게 되면 **게시** 버튼을 통해 양식을 실시간으로 사용할 수 있습니다. 양식 만들기 워크플로의 마지막 단계입니다.

  ![게시](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

- **줄임표 메뉴**

  줄임표(...)를 클릭하면 현재 라이브 상태인 양식을 **게시 취소**&#x200B;하는 기능을 포함한 추가 옵션이 표시됩니다. 이 기능은 공용 액세스에서 양식을 일시적으로 제거하거나 업데이트된 버전으로 대체해야 할 때 유용합니다.

  ![줄임표](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

### 속성 패널

**속성 패널**&#x200B;은 인터페이스 오른쪽에 나타나며 양식에서 선택한 내용에 따라 상황별 정보를 표시합니다. 선택한 구성 요소가 없으면 전체 양식 구조가 표시됩니다.

![속성 패널](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

주요 구성 요소를 살펴보겠습니다.

- **속성 모드**

  **속성** 모드에서는 현재 선택한 구성 요소에 대한 설정 및 옵션이 표시됩니다. 여기에서 특정 요구 사항을 충족하도록 양식의 개별 요소를 사용자 정의할 수 있습니다. 선택한 구성 요소의 속성을 여는 키보드 단축키는 `d`입니다.

  ![속성](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

- **콘텐츠 트리**

  **콘텐츠 트리**&#x200B;에 양식의 계층 구조가 표시됩니다. 이 시각적 표현은 구성 요소가 서로 어떻게 중첩되는지를 이해하는 데 도움이 됩니다. 트리에서 항목을 클릭하면 편집기에서 해당 항목이 선택되고 해당 위치로 스크롤됩니다. 이는 복잡한 형식에서 특히 유용합니다. 키보드 단축키 `f`을(를) 사용하여 콘텐츠 트리 보기를 전환합니다.

  ![콘텐츠 트리](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

- **변형 생성**

  **변형 생성** 기능은 인공 지능을 사용하여 특정 프롬프트에 따라 다른 버전의 양식을 만듭니다. 이렇게 하면 각 변형을 수동으로 만들지 않고도 다양한 접근 방식 및 디자인을 실험할 수 있습니다. 프롬프트는 Adobe에서 제공하거나 사용자가 사용자 정의할 수 있습니다.

  ![변형 생성](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

  >[!NOTE]
  >
  > 양식의 변형 생성 사용에 대한 자세한 지침은 [변형 생성](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/generative-ai/generate-variations) 문서를 참조하십시오.

- **실험**

  **실험** 기능을 사용하면 다양한 양식 디자인과 레이아웃을 비교하는 제어된 테스트를 실행할 수 있습니다. 사용자가 각 변형과 상호 작용하는 방법을 분석함으로써 전환율과 사용자 경험을 최적화하기 위해 데이터 중심의 결정을 내릴 수 있습니다.

  ![실험](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

- **개인화**

  **Personalization** 설정을 통해 양식을 Adobe Experience Platform(AEP) 또는 외부 응용 프로그램에 연결할 수 있습니다. 이 연결을 통해 사용자 데이터 및 동작을 기반으로 맞춤 양식 경험을 만들 수 있으므로 관련성과 참여도를 높일 수 있습니다.

  ![개인화](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

- **A/B 테스트**

  **A/B 테스트**&#x200B;를 통해 양식의 특정 변형을 비교하여 더 나은 성과를 확인할 수 있습니다. 광범위한 실험과 달리, A/B 테스트는 일반적으로 가장 효과적인 옵션을 식별하기 위해 특정 요소 또는 변경 사항을 비교하는 데 중점을 둡니다.

  ![A/B 테스트](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

- **작업 관리**

  **작업 관리** 기능을 사용하면 팀이 양식 만들기 및 최적화와 관련된 작업을 구성하고, 추적하고, 완료할 수 있으므로 공동 작업을 간소화할 수 있습니다. 따라서 명확한 책임감을 갖고 프로젝트를 효율적으로 진행할 수 있습니다.

  ![작업 관리](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

- **콘텐츠 초안**

  **콘텐츠 초안** 기능을 사용하면 양식에 텍스트 요소의 임시 버전을 만들고 저장할 수 있습니다. 기존 양식 텍스트를 사용하여 초안을 만들거나 처음부터 시작한 다음 필요에 따라 편집하거나 삭제할 수 있습니다. 기본적으로 3개의 초안이 표시되지만 **모두 표시**&#x200B;를 클릭하면 추가 초안이 표시됩니다.

  ![콘텐츠 초안](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

- **데이터 Source**

  **데이터 Source** 옵션을 사용하면 FDM(양식 데이터 모델)의 데이터 소스를 구성하고 선택할 수 있습니다. 이 통합을 통해 선택한 소스의 모든 데이터 모델 개체, 속성 및 서비스를 양식에서 사용할 수 있으므로 동적 데이터 검색 및 제출이 가능합니다.

  ![데이터 Source](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

- **추가**

  **추가** 단추에 현재 선택한 컨테이너에 추가할 수 있는 구성 요소의 드롭다운 목록이 표시됩니다. 예를 들어 적응형 양식 섹션을 선택하면 이 목록에는 해당 섹션에 추가할 수 있는 모든 구성 요소가 표시됩니다. 이 구성 요소 목록을 여는 키보드 단축키는 `a`입니다.

  ![아이콘 추가](/help/edge/docs/forms/universal-editor/assets/ue-add.png)

- **복제**

  **복제** 옵션을 사용하면 선택한 구성 요소의 정확한 복사본이 만들어집니다. 이렇게 하면 처음부터 만드는 대신 복제한 다음 수정할 수 있으므로 유사한 여러 요소가 필요할 때 시간을 절약할 수 있습니다.

  ![중복 아이콘](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)

- **삭제**

  **삭제** 옵션을 사용하면 선택한 구성 요소가 양식에서 제거됩니다. 이 옵션은 확인 프롬프트 없이 요소가 즉시 제거되므로 이 옵션을 사용할 때는 주의하십시오.

  ![삭제](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### 편집기

편집기는 양식을 만들고 수정하는 중앙 작업 영역입니다. 이 보고서는 위치 표시줄에 지정된 양식을 표시하고 양식이 사용자에게 표시되는 방식을 정확하게 보여 주는 WYSIWYG 환경을 제공합니다. 미리 보기 모드에서는 사용자와 마찬가지로 양식과 상호 작용하여 버튼과 링크를 통한 탐색을 테스트할 수 있습니다.

![편집기](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

편집기에서 구성 요소를 추가하고, 속성을 구성하고, 배열하여 직관적이고 효과적인 양식 경험을 만들 수 있습니다.

## 키보드 단축키 요약

생산성을 향상시키려면 다음과 같은 중요한 키보드 단축키를 기억하십시오.

- `l` - 위치 표시줄에 포커스 지정
- `p` - 편집 모드와 미리 보기 모드 간 전환
- `o` - 새 탭에서 양식을 엽니다.
- `d` - 선택한 구성 요소의 속성 열기
- `f` - 콘텐츠 트리 보기 전환
- `a` - 추가할 구성 요소 목록을 엽니다.


