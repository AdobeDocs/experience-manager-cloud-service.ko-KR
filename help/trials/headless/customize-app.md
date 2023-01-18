---
title: 샘플 React 앱에서 콘텐츠 사용자 정의
description: 샘플 React 앱을 사용하여 AEM as a Cloud Service로 설정된 headless 기능으로 콘텐츠를 사용자 정의하는 방법에 대해 알아보십시오.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 38%

---


# 샘플 React 앱에서 콘텐츠 사용자 정의 {#customize-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app"
>title="샘플 React 앱에서 콘텐츠 사용자 정의"
>abstract="AEM 헤드리스 체험판은 사용자 지정할 수 있는 샘플 React 앱과 통합되었습니다."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide"
>title="콘텐츠 조각 편집기 실행"
>abstract="AEM 헤드리스 평가판은 샘플 React 앱과 통합되어 있으므로 개발되지 않은 시간에 누구나 컨텐츠를 독립적으로 관리하는 것이 얼마나 쉬운지 알 수 있습니다.<br><br>아래 를 클릭하여 새 탭에서 이 모듈을 시작한 다음 이 안내서를 따르십시오."
>additional-url="https://video.tv.adobe.com/v/328618" text="앱 소개 비디오 사용자 지정"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide_footer"
>title="이 모듈에서는 샘플 React 앱을 사용자 정의하는 방법을 배웠습니다.<br><br>출시 시기: 가속화!<br>개발 주기: 감소!<br><br>이제 AEM 헤드리스 기능을 기반으로 하는 웹 사이트 및 앱에 대해 헤드리스 콘텐츠를 쉽게 관리하는 방법을 이해합니다."
>abstract=""

## 앱 미리보기 {#preview}

클릭 **컨텐츠 조각 편집기를 시작합니다** 위의 버튼을 클릭하면 새 탭에서 컨텐츠 조각 편집기가 열립니다.

![콘텐츠 조각 편집기](assets/customize-app/content-fragment-editor.png)

AEM 헤드리스 체험판과 함께 제공되는 샘플 앱은 GraphQL을 통해 전달된 컨텐츠 조각에서 제공합니다. 컨텐츠 조각 편집기를 사용하여 샘플을 미리 보고 컨텐츠를 익숙해지십시오.

1. 편집기 화면의 오른쪽 상단에서 **미리보기** 버튼을 탭하거나 클릭합니다.

1. 데모 앱이 새 탭에서 열립니다. 가상의 WKND 아웃도어 라이프스타일 브랜드를 위한 앱이다. 주변을 클릭하여 샘플 콘텐츠를 탐색합니다.

   ![데모 앱 미리보기](assets/customize-app/preview-demo-app.png)

1. 계속하려면 컨텐츠 조각 편집기의 브라우저 탭으로 돌아갑니다.

## 앱에서 헤더 편집 {#edit-app}

컨텐츠 조각 편집기는 앱의 기본 레이아웃을 페이지 컨텐츠 조각으로 표시합니다. **패널**&#x200B;은 각각 고유한 콘텐츠 조각인 앱의 여러 페이지를 나타냅니다. 이 조각을 수정하면 앱 콘텐츠를 변경할 수 있습니다.

1. **패널** 섹션에서 **캐년의 산악 바이커**&#x200B;를 탭하거나 클릭합니다.

   ![캐년의 산악 바이커 조각 탭하기](assets/customize-app/mtn-biker-in-canyon.png)

1. 편집기에서 산악 바이커용 앱의 헤더 패널을 엽니다. 각 패널은 경험을 구성하는 서로 다른 이미지와 텍스트를 나타내는 레이어로 구성됩니다.

   ![패널](assets/customize-app/panels.png)

1. **캐년의 산악 바이커 텍스트 레이어** 텍스트 레이어를 선택합니다. 이렇게 하면 편집기에서 레이어의 세부 정보가 열립니다. 계층은 앱의 이 패널에 표시되는 텍스트를 제어하는 여러 컨텐츠 조각으로 구성됩니다.

   ![캐년의 산악 바이커 제목 선택](assets/customize-app/mtn-biker-in-canyon-text-layer.png)

1. **캐년의 산악 바이커 제목** 텍스트 항목을 선택합니다. 그러면 컨텐츠 조각 편집기가 열립니다.

   ![캐년의 산악 바이커 제목 텍스트 항목 선택](assets/customize-app/mtn-biker-in-canyon-title.png)

1. 텍스트를 `Your next great adventure is calling`에서 `Choose your own adventure`로 변경합니다. 편집기에 변경 사항이 자동으로 저장됩니다.

1. 탭 또는 클릭 **미리 보기** 창 오른쪽 상단에서 변경 내용을 확인합니다. 데모 앱 미리 보기가 새 탭에서 열립니다.

   ![데모 앱 미리보기](assets/customize-app/preview-demo-app-text.png)

이렇게 하면 AEM 헤드리스 CMS에 통합할 때 React 앱 내의 컨텐츠를 쉽게 업데이트할 수 있습니다.

## 앱에서 이미지 교체 {#change-image}

앱에서 헤드라인을 수정했으므로 이미지를 변경해 보십시오.

1. 컨텐츠 조각 편집기의 브라우저 탭으로 돌아갑니다.

1. 컨텐츠 조각 편집기에서 올바른 위치로 돌아가야 합니다. 편집기의 왼쪽 상단에 있는 이동 경로는 콘텐츠 계층에서 현재 위치를 보여 줍니다. 이동 경로에서 **캐년의 산악 바이커**&#x200B;를 탭하거나 클릭하여 해당 페이지로 돌아갑니다.

   ![탐색 표시](assets/customize-app/breadcrumbs.png)

1. **산악 바이킹 - 바이커** 이미지 레이어를 선택합니다. 그러면 컨텐츠 조각 편집기가 열립니다

   ![이미지 조각 편집](assets/customize-app/mtn-biking-biker.png)

1. 바이커 이미지를 제거하려면 **X**&#x200B;를 탭하거나 클릭합니다. 이 콘텐츠 조각 모델에 필요한 데이터이므로 이미지가 사라지고 편집기에 오류가 표시됩니다.

   ![조각에서 제거된 이미지](assets/customize-app/mtn-biking-biker-no-image.png)

1. 탭 또는 클릭 **자산 추가**.

1. 다음 **자산 선택** 대화 상자가 열리고 경로가 표시됩니다 **sample-wknd-app** > **en** > **이미지 파일** 자동으로 선택됩니다.

1. 이미지를 선택합니다 `biker-yellow.png` 그런 다음 탭하거나 클릭합니다. **선택**.

   ![에셋 선택](assets/customize-app/select-asset.png)

1. 바이커의 이미지가 선택한 이미지로 바뀝니다. 편집기는 변경 사항을 자동으로 저장합니다.

   ![바이커 이미지의 편집된 조각](assets/customize-app/mtn-biking-biker-edited.png)

1. 탭 또는 클릭 **미리 보기** 창 오른쪽 상단에서 변경 내용을 확인합니다. 데모 앱 미리 보기가 새 탭에서 열립니다. 브라우저에서 새로 고침 을 클릭하면 앱에 노란색 반바지가 있는 새 바이커 이미지가 표시됩니다.

AEM 헤드리스 CMS를 사용하여 앱에서 이미지와 자산을 쉽게 업데이트할 수 있습니다.

## 앱의 새 컨텐츠 조각에 대한 참조를 추가합니다 {#create-moment}

이제 바이커의 이미지를 업데이트했으므로 새 컨텐츠 조각을 만들고 참조하여 앱에 새 컨텐츠를 추가하는 방법을 살펴보겠습니다. &quot;쇼퍼블(Shoppable) 순간&quot; 컨텐츠 조각에 의해 관리되는 제품 호출을 앱의 두 번째 패널에 추가합니다.

![쇼퍼블 상태의 예](assets/customize-app/example-shoppable-moment.png)

1. 컨텐츠 조각 편집기의 브라우저 탭으로 돌아갑니다.

1. 컨텐츠 조각 편집기에서 올바른 위치로 돌아가야 합니다. 편집기의 왼쪽 상단에 있는 이동 경로는 콘텐츠 계층에서 현재 위치를 보여 줍니다. 이동 경로에서 **WKND Home**&#x200B;을 탭하거나 클릭하여 해당 페이지로 돌아갑니다.

   ![레이아웃 화면으로 다시 이동](assets/customize-app/breadcrumbs-2.png)

1. **WKND Yellow를 타는 산악 바이커** 패널을 선택합니다.

   ![구매 가능한 순간 만들기](assets/customize-app/mtn-biker-on-wknd-yellow.png)

1. 을(를) 선택합니다 **Mtn Biking - 쇼퍼블** 레이어.

   ![구매 가능한 순간 레이어 선택](assets/customize-app/mtn-biking-shoppable.png)

1. 이 패널에서 새 콜아웃을 만들려면 새로운 쇼퍼블 순간인 컨텐츠 조각을 만들어야 합니다. 을(를) 탭하거나 클릭합니다 **+ 새 조각 만들기** 버튼을 클릭합니다.

   ![구매 가능한 순간 추가](assets/customize-app/create-new-fragment.png)

1. 먼저 새 컨텐츠 조각을 기반으로 할 모델을 선택해야 합니다. **콘텐츠 조각 모델** 드롭다운에서 **구매 가능한 순간 항목** 모델을 선택합니다.

1. 컨텐츠 조각에 이름을 지정합니다. 예를 들어 `Shorts`를 **이름** 필드에 입력합니다.

   ![구매 가능한 순간 이름 지정](assets/customize-app/new-content-fragment.png)

1. **만들기 및 열기**&#x200B;를 탭하거나 클릭합니다.

1. 새 콘텐츠 조각에 대한 편집기가 열립니다.

1. 구매 가능한 순간에 **텍스트** 필드에 `Yellow shorts`와 같은 이름을 지정합니다.

1. 값 설정 **X** 및 **Y**. 여기에서 이 콜아웃을 패널에서 오버레이해야 합니다. 조각에 대한 변경 사항은 편집기에서 자동으로 저장됩니다.
   * **X**: `-18`
   * **Y**: `-28`

   ![구매 가능한 순간 편집](assets/customize-app/edit-shoppable-moment.png)

1. 탭 또는 클릭 **미리 보기** 창 오른쪽 상단에서 변경 내용을 확인합니다. 데모 앱 미리 보기가 새 탭에서 열립니다. 브라우저에서 새로 고침 을 클릭하여 위치를 테스트하고 편집기에서 필요에 따라 조정합니다.

이제 개발 주기 없이 새 컨텐츠를 만들고 이를 앱에서 컨텐츠 조각으로 참조하는 방법을 이해합니다.
