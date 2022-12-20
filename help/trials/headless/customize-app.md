---
title: 샘플 React 앱에서 콘텐츠 사용자 정의
description: 샘플 React 앱을 사용하여 AEM as a Cloud Service로 설정된 headless 기능으로 콘텐츠를 사용자 정의하는 방법에 대해 알아보십시오.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
source-git-commit: 1456891dc3b13b3d79fa8ee9f3ded37e92cfbc85
workflow-type: tm+mt
source-wordcount: '1481'
ht-degree: 95%

---

# 샘플 React 앱에서 콘텐츠 사용자 정의 {#customize-app}

headless용 AEM 체험판에는 headless 콘텐츠를 선보일 수 있는 간단한 React 앱이 미리 로드되어 있습니다. 이 모듈에서는 이미지를 교체하고 구매 가능한 순간을 만들어 해당 앱을 미리보고 콘텐츠를 수정하는 방법에 대해 배우게 됩니다.

앱 자체는 콘텐츠 조각 구조를 기반으로 합니다. AEM에서 콘텐츠 조각 편집기를 사용하여 앱 콘텐츠를 수정할 수 있습니다. 빠른 대화형 둘러보기를 통해 프로세스를 안내하는 이 AEM 체험판 모듈에서는 해당 작업을 수행하는 방법에 대해 알아볼 수 있습니다. 이 문서는 대화형 둘러보기를 보완하는 역할을 하며, 동일한 단계를 다루고 해당하는 경우 추가 리소스에 대한 링크를 제공합니다.

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app"
>title="샘플 React 앱에서 콘텐츠 사용자 정의"
>abstract="Adobe에서 설정한 최신 React 앱을 통해 헤드리스 기능 세트를 사용하여 콘텐츠를 맞춤화하는 방법에 대해 알아볼 수 있습니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide"
>title="컨텐츠 조각 편집기를 시작합니다"
>abstract="headless용 AEM 체험판에는 headless 콘텐츠를 선보일 수 있는 간단한 React 앱이 미리 로드되어 있습니다. 앱은 컨텐츠 조각의 구조를 기반으로 합니다. AEM에서 컨텐츠 조각 편집기를 사용하여 앱의 컨텐츠를 수정할 수 있습니다.<br><br>아래 를 클릭하여 새 탭에서 기능을 시작한 다음 이 안내서를 따르십시오."
>additional-url="https://video.tv.adobe.com/v/328618" text="소개 비디오의 자리 표시자"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home_c1.png" text="비디오 축소판: flash에서 앱 콘텐츠 수정"

## 콘텐츠 조각 편집기 {#fragment-editor}

샘플 앱의 콘텐츠 조각 편집기에서 시작합니다.

![콘텐츠 조각 편집기](assets/customize-app/content-fragment-editor.png)

인앱 지침을 벗어나 직접 콘텐츠 조각 편집기로 이동하려면 페이지 왼쪽 상단에 있는 Adobe 아이콘을 사용하여 찾을 수 있습니다. 그러면 AEM의 전역 탐색이 열립니다. 여기에서 **탐색** 탭을 선택한 다음 **콘텐츠 조각**&#x200B;을 선택합니다.

![콘텐츠 조각 콘솔에서 앱으로 이동](assets/customize-app/navigate-to-app.png)

콘텐츠 조각 콘솔이 열립니다. 여기에서 왼쪽 패널의 콘텐츠 트리를 사용하여 앱 콘텐츠 위치로 이동합니다. 이 경우 **콘텐츠 조각** -> **샘플 WKND 앱** -> **영어** -> **콘텐츠 조각** -> **페이지**&#x200B;에 있습니다.

콘텐츠 트리의 오른쪽에 있는 콘솔에 표시된 **WKND Home** 페이지 조각을 탭하거나 클릭하여 앱 콘텐츠에 대한 편집기를 시작합니다.

>[!TIP]
>
>AEM 탐색에 대해 자세히 알아보려면 이 문서의 [추가 리소스 섹션](#additional-resources)에서 AEM 기본 처리에 대한 내용을 참조하십시오.

## 앱 미리보기 {#preview}

앱 수정을 시작하기 전에 먼저 현재 상태를 미리보고 앱에 익숙해집니다. 편집기 화면의 오른쪽 상단에서 **미리보기** 버튼을 탭하거나 클릭합니다.

데모 앱이 새 탭에서 열립니다.

![데모 앱 미리보기](assets/customize-app/preview-demo-app.png)

앱 자체는 React로 구현된 가상의 WKND 아웃도어 라이프스타일 브랜드를 위한 간단한 e커머스 앱입니다. 주변을 클릭하여 샘플 콘텐츠를 탐색합니다.

계속하려면 콘텐츠 조각 편집기의 탭으로 돌아갑니다.

## 앱에서 텍스트 편집 {#edit-app}

앞서 언급했듯이 앱 자체는 콘텐츠 조각으로 구성됩니다. 이러한 조각은 하나의 구조로 함께 연결되어 앱을 만듭니다.

콘텐츠 조각 편집기는 앱의 기본 레이아웃을 페이지로 표시합니다. 이 페이지는 그 자체로 다른 조각 모음인 콘텐츠 조각입니다. **패널**&#x200B;은 각각 고유한 콘텐츠 조각인 앱의 여러 페이지를 나타냅니다. 이 조각을 수정하면 앱 콘텐츠를 변경할 수 있습니다.

1. **패널** 섹션에서 **캐년의 산악 바이커**&#x200B;를 탭하거나 클릭합니다.

   ![캐년의 산악 바이커 조각 탭하기](assets/customize-app/mtn-biker-in-canyon.png)

1. 편집기는 산악 바이커에 대한 헤더 패널을 엽니다. 각 패널은 레이어로 구성되어 있으며, 앱 페이지 내의 다양한 콘텐츠를 나타냅니다.

   ![패널](assets/customize-app/panels.png)

1. **캐년의 산악 바이커 텍스트 레이어** 텍스트 레이어를 선택합니다. 이렇게 하면 편집기에서 레이어의 세부 정보가 열립니다. 레이어는 여러 콘텐츠 조각으로 구성됩니다.

   ![캐년의 산악 바이커 제목 선택](assets/customize-app/mtn-biker-in-canyon-text-layer.png)

1. **캐년의 산악 바이커 제목** 텍스트 항목을 선택합니다. 이렇게 하면 콘텐츠 조각 편집기가 열리고, 이 조각의 콘텐츠가 표시되며 수정할 수 있습니다.

   ![캐년의 산악 바이커 제목 텍스트 항목 선택](assets/customize-app/mtn-biker-in-canyon-title.png)

1. 텍스트를 `Your next great adventure is calling`에서 `Choose your own adventure`로 변경합니다. 편집기에 변경 사항이 자동으로 저장됩니다.

1. 변경 사항을 보려면 미리보기를 클릭합니다. 데모 앱이 새 탭에서 열립니다.

   ![데모 앱 미리보기](assets/customize-app/preview-demo-app-text.png)

모듈을 계속하려면 콘텐츠 조각 편집기의 탭으로 돌아갑니다.

## 앱의 기본 이미지 변경 {#change-image}

앱에서 일부 텍스트를 수정했으므로 앱의 기본 이미지를 변경해 보십시오. 먼저 해당 콘텐츠를 찾아야 합니다.

편집기의 왼쪽 상단에 있는 이동 경로는 콘텐츠 계층에서 현재 위치를 보여 줍니다.

1. 이동 경로에서 **캐년의 산악 바이커**&#x200B;를 탭하거나 클릭하여 해당 페이지로 돌아갑니다.

   ![탐색 표시](assets/customize-app/breadcrumbs.png)

1. 앱의 다양한 레이어가 있는 패널로 돌아갑니다. 레이어는 텍스트 콘텐츠만 나타내는 것이 아닙니다. 앱의 모든 콘텐츠를 나타냅니다. 따라서 콘텐츠 조각 편집기를 사용하여 이미지를 교체할 수도 있습니다.

   ![패널](assets/customize-app/panels.png)

1. **산악 바이킹 - 바이커** 이미지 레이어를 선택합니다. 이렇게 하면 콘텐츠 조각 편집기가 열리고, 이 조각의 콘텐츠가 표시되며 수정할 수 있습니다.

   ![이미지 조각 편집](assets/customize-app/mtn-biking-biker.png)

1. 바이커 이미지를 제거하려면 **X**&#x200B;를 탭하거나 클릭합니다. 이 콘텐츠 조각 모델에 필요한 데이터이므로 이미지가 사라지고 편집기에 오류가 표시됩니다.

   ![조각에서 제거된 이미지](assets/customize-app/mtn-biking-biker-no-image.png)

1. **에셋 추가**&#x200B;를 탭하거나 클릭하고 **sample-wknd-app** > **en** > **image-file**&#x200B;에서 노란색 바이커 이미지를 찾습니다. 콘텐츠 계층을 탐색하려면 **에셋 선택** 대화 상자의 왼쪽에 있는 트리 보기를 사용합니다.

   ![에셋 선택 대화 상자](assets/customize-app/select-assets.png)

1. `yellow` 텍스트를 필터링합니다. **에셋 선택** 창 상단의 **모든 에셋 검색** 필드를 사용하여 이미지를 검색합니다. 검색 텍스트를 입력하고 Enter 키를 누르거나 검색으로 돌아갑니다.

   ![에셋 검색](assets/customize-app/search-assets.png)

1. `biker-yellow.png`이미지를 탭하거나 클릭하여 선택한 다음 **선택**&#x200B;을 탭하거나 클릭합니다.

   ![에셋 선택](assets/customize-app/select-asset.png)

1. 바이커 이미지가 선택한 이미지로 교체되었습니다. 편집기는 변경 사항을 자동으로 저장합니다.

   ![바이커 이미지의 편집된 조각](assets/customize-app/mtn-biking-biker-edited.png)

## 구매 가능한 순간 만들기 {#create-moment}

바이커 이미지를 업데이트했으므로 이제 바이커의 노란색 반바지에 구매할 수 있는 순간을 추가할 수 있습니다.

1. 페이지 조각에 대한 콘텐츠 조각 편집기로 돌아가서 시작합니다. 편집기의 왼쪽 상단에 있는 이동 경로는 콘텐츠 계층에서 현재 위치를 보여 줍니다. 이동 경로에서 **WKND Home**&#x200B;을 탭하거나 클릭하여 해당 페이지로 돌아갑니다.

   ![레이아웃 화면으로 다시 이동](assets/customize-app/breadcrumbs-2.png)

1. **WKND Yellow를 타는 산악 바이커** 패널을 선택합니다.

   ![구매 가능한 순간 만들기](assets/customize-app/mtn-biker-on-wknd-yellow.png)

1. 이제 바이커 이미지를 구성하는 레이어를 볼 수 있습니다. **산악 바이킹 - 구매 가능** 레이어를 선택하여 바이커의 노란색 반바지에 구매 가능한 순간을 추가합니다.

   ![구매 가능한 순간 레이어 선택](assets/customize-app/mtn-biking-shoppable.png)

1. 구매 가능한 순간을 만들려면 해당 순간을 나타내는 새 콘텐츠 조각을 만들어야 합니다. **+ 새 조각 만들기** 버튼을 탭하거나 클릭하여 바이커 반바지에 구매 가능한 순간을 추가합니다.

   ![구매 가능한 순간 추가](assets/customize-app/create-new-fragment.png)

1. 콘텐츠 조각은 구조화된 headless 데이터를 나타내므로 콘텐츠 조각을 만들 때마다 먼저 기준이 될 모델을 선택해야 합니다. **콘텐츠 조각 모델** 드롭다운에서 **구매 가능한 순간 항목** 모델을 선택합니다.

   이러한 ![콘텐츠 조각 모델 선택](assets/customize-app/new-content-fragment.png)

1. 새로운 구매 가능한 순간을 나타내는 콘텐츠 조각에 이름을 지정합니다. 예를 들어 `Shorts`를 **이름** 필드에 입력합니다.

   ![구매 가능한 순간 이름 지정](assets/customize-app/new-content-fragment.png)

1. **만들기 및 열기**&#x200B;를 탭하거나 클릭합니다.

1. 새 콘텐츠 조각에 대한 편집기가 열립니다.
   * 구매 가능한 순간에 **텍스트** 필드에 `Yellow shorts`와 같은 이름을 지정합니다.
   * 구매 가능한 순간이 겹쳐야 하는 위치인 X 및 Y를 설정합니다.
      * **X**: `-18`
      * **Y**: `-28`
   * 조각에 대한 변경 사항은 편집기에서 자동으로 저장됩니다.

   ![구매 가능한 순간 편집](assets/customize-app/edit-shoppable-moment.png)

1. **미리보기**&#x200B;를 탭하거나 클릭하여 이 위치를 테스트하고 필요에 따라 조정합니다.

   ![새로운 구매 가능한 순간 미리보기](assets/customize-app/preview-demo-app-shoppable.png)

## 샘플 React 앱을 사용자 정의하는 방법을 배웠습니다! {#conclusion}

이 모듈에서는 샘플 React 앱을 사용자 정의하는 방법을 배웠습니다. 먼저 기존 텍스트를 편집하는 방법을 배웠습니다. 그런 다음 이미지가 해당 이미지의 다른 인스턴스와 교체되었습니다. 마지막으로 구매 가능한 순간 항목이 생성되고 배치되는 방법을 확인했습니다.

AEM 및 해당 콘텐츠 조각 사용에 대한 추가 리소스는 [추가 리소스 섹션](#additional-resources)을 확인하십시오.

사용자 정의 앱에서 사용하기 위해 콘텐츠 조각 및 headless 콘텐츠를 만드는 방법을 알아보려면 [앱의 콘텐츠 구조 만들기](content-structure.md) 모듈을 검토하여 시작할 수 있습니다.

탐색 막대의 오른쪽 상단에 있는 **솔루션** 버튼을 클릭하고 **Experience Manager**&#x200B;를 선택하여 체험판 홈 화면으로 돌아갈 수 있습니다.

![홈 탐색](assets/customize-app/home.png)

## 추가 리소스 {#additional-resources}

콘텐츠 조각 및 AEM에 대한 자세한 내용은 이 추가 설명서를 검토하십시오.

* [콘텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md) - 콘텐츠 조각 모델에 대한 전체 설명서
* [콘텐츠 조각](/help/assets/content-fragments/content-fragments.md) - 콘텐츠 조각 개요 및 콘텐츠 조각에 대한 전체 설명서 링크
* [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 신규 사용자를 위한 AEM 탐색 및 사용 방법에 대한 설명서
