---
title: 헤드리스 컨텐츠 만들기
description: 이전에 만든 컨텐츠 조각 모델을 사용하여 페이지 작성에 사용하거나 헤드리스 컨텐츠의 기반으로 사용할 수 있는 컨텐츠를 만들 수 있습니다.
hidefromtoc: true
index: false
source-git-commit: 7d5161d97a93d4731e33eda586179560a6a55ef3
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 1%

---


# 헤드리스 컨텐츠 만들기 {#create-content}

제품 내 학습 모듈에 따라 사용 방법을 알아봅니다 [이전에 만든 컨텐츠 조각 모델](content-structure.md) 를 사용하여 페이지 작성에 사용하거나 헤드리스 컨텐츠의 기반으로 사용할 수 있는 컨텐츠를 만들 수 있습니다. 이 문서는 대화형 투어의 추가 기능으로서 동일한 단계를 적용하고 적절한 추가 리소스에 연결합니다.

## 콘텐츠 조각 {#introduction}

AEM as a Cloud Service에서 컨텐츠 조각은 컨텐츠 조각 모델에 정의된 구조를 기반으로 헤드리스 컨텐츠 조각입니다. 컨텐츠 조각 콘솔에서 시작하여 고유한 컨텐츠 조각을 만들 수 있습니다. 컨텐츠 조각 콘솔은 헤드리스 컨텐츠의 라이브러리로 생각할 수 있습니다. 콘솔을 사용하여 새 컨텐츠 조각을 만들고 기존 조각을 관리할 수 있습니다. 콘솔이 비어 시작되므로 새 조각을 만들어 보겠습니다!

![조각의 컨텐츠 편집](assets/create-content/content-fragment-console.png)

인앱 지침 외부에서 직접 컨텐츠 조각 콘솔로 이동하려면 페이지 왼쪽 상단에 있는 Adobe 아이콘을 사용하여 찾습니다. 이렇게 하면 AEM의 전역 탐색이 열립니다. 여기에서 **탐색** 탭한 다음 **컨텐츠 조각**.

>[!TIP]
>
>AEM의 탐색에 대한 자세한 내용은 [추가 리소스 섹션](#additional-resources) AEM 기본 처리에 대한 자세한 내용은 이 문서를 참조하십시오.

## 컨텐츠 조각 만들기 {#create-fragment}

컨텐츠 조각은 헤드리스 컨텐츠를 나타냅니다. 하지만 미리 정의된 컨텐츠 구조를 기반으로만 만들 수 있습니다. 이전에 만든 컨텐츠 조각 모델은 해당 구조로 사용됩니다.

1. 을(를) 탭하거나 클릭합니다 **만들기** 콘솔 오른쪽 상단의 단추를 클릭하여 **새 컨텐츠 조각** 대화 상자에서 새 컨텐츠 조각 만들기를 시작합니다.

   ![컨텐츠 조각 만들기 대화 상자](assets/create-content/create-content-fragment.png)

1. 인앱 지침을 따르는 경우, **위치** 자동으로 채워집니다.

   1. 지침을 따르지 않는 경우 경로 브라우저를 사용하여 프로젝트 폴더를 선택하십시오.

   1. 에서 **새 컨텐츠 조각** 대화 상자에서 탭하거나 클릭합니다. **위치 선택** 단추(폴더처럼 보이는 아이콘)를 **위치** 필드.

      ![위치 선택 대화 상자](assets/create-content/choose-location.png)
   * 또는 을 클릭하기 전에 컨텐츠 조각 콘솔의 왼쪽 탐색 패널에서 경로를 선택합니다 **만들기**.


1. 에서 **컨텐츠 조각 모델** 드롭다운에서 이전에 드롭다운에서 만든 컨텐츠 조각 모델을 선택합니다.

1. 추가 **제목** 컨텐츠 조각에 사용할 수 있습니다.

1. 탭 또는 클릭 **만들기 및 열기**.

## 콘텐츠 조각 편집기 {#edit-fragment}

새 컨텐츠 조각을 저장하면 컨텐츠 조각 편집기가 열리고 조각의 실제 컨텐츠를 제공할 수 있습니다.

1. 편집기에 선택한 모델에서 정의한 필드가 표시됩니다. 여기에서 이러한 조각을 편집하여 컨텐츠 조각을 완료할 수 있습니다. 진행 상태가 자동으로 저장됩니다.

   ![컨텐츠 조각 편집기](assets/create-content/content-fragment-editor.png)

1. 컨텐츠 조각 모델에 필드가 많은 경우 를 사용하여 모든 필드로 빠르게 이동할 수 있습니다. **변수** 편집기 왼쪽에 있는 패널. 오류가 있는 필드는 여기에 플래그가 지정됩니다.

1. 컨텐츠 조각을 외부 앱에서 사용할 수 있도록 하려면 게시해야 합니다. 을(를) 탭하거나 클릭합니다 **게시** 편집기의 오른쪽 상단에 있는 단추.

1. 선택 **지금** 드롭다운 나중에 게시하도록 예약할 수도 있습니다.

   ![게시 단추](assets/create-content/publish.png)

   >[!TIP]
   >
   >AEM에서 컨텐츠 게시에 대한 자세한 내용은 [추가 리소스 섹션](#additional-resources) 자세한 내용은 이 문서를 참조하십시오.

1. AEM은 자동으로 참조 검사를 수행하여 컨텐츠 조각에 필요한 모든 리소스가 게시되었는지 확인합니다. 이 경우 생성한 모델을 게시해야 합니다. **게시**&#x200B;를 탭하거나 클릭합니다.

   ![참조 확인](assets/create-content/references.png)

1. 게시가 배너로 확인된다.

   ![게시 확인](assets/create-content/publish-confirm.png)

## 컨텐츠 조각을 만드는 방법을 배웠습니다! {#conclusion}

이 모듈에서는 이전에 만든 모델을 기반으로 컨텐츠 조각을 만드는 방법을 알아보았습니다. 컨텐츠 작성자가 구조화된 헤드리스 컨텐츠를 만드는 방법입니다.

이제 컨텐츠가 생성되어 게시되었으므로 AEM API를 통해 Graph QL을 통해 해당 컨텐츠를 추출할 수 있습니다. 이 방법은 모듈에서 학습합니다 [GraphQL API를 통해 컨텐츠를 추출합니다.](extract-content.md)

를 클릭하여 체험판 홈 화면으로 돌아갈 수 있습니다. **솔루션** 탐색 막대의 오른쪽 상단에 있는 버튼 및 선택 **Experience Manager**.

![홈 탐색](assets/create-content/home.png)

## 추가 리소스 {#additional-resources}

컨텐츠 조각 및 AEM에 대한 자세한 내용은 이 추가 설명서를 참조하십시오.

* [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 새 사용자를 위한 AEM 탐색 및 사용 방법에 대한 설명서
* [컨텐츠 조각 관리 - 게시 및 참조](/help/assets/content-fragments/content-fragments-managing.md#publishing-and-referencing-a-fragment) - AEM에서 컨텐츠를 게시하는 방법에 대한 세부 정보
* [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md) - 컨텐츠 조각 및 컨텐츠 조각에 대한 전체 설명서 링크 개요
* [컨텐츠 조각 관리](/help/assets/content-fragments/content-fragments-managing.md) - 컨텐츠 조각을 만들고 관리하는 방법
