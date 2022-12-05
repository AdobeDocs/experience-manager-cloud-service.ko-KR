---
title: Dynamic Media으로 여정, 2부
description: Dynamic Media 여정은 Dynamic Media의 기본 사항, 작동 방법, 사용자에게 유용한 정보, 작업 및 고객에게 제공하는 가치 등을 다룹니다.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: cdca41ad-a2cd-4f68-aaa4-5eec33c30f0b
source-git-commit: 1200dc41af22ae8f34f33d176de1c0db7c7ae424
workflow-type: tm+mt
source-wordcount: '2900'
ht-degree: 0%

---

# Dynamic Media 여정: 기초, 2부  {#dm-journey-part2}

Dynamic Media 여정 시작: 다음 사항을 학습할 수 있는 기본 사항, 2부.

* Dynamic Media URL의 구조 및 Dynamic Media이 컨텐츠를 제공하는 방법
* 자산을 렌더링하기 위해 이미지 사전 설정을 만드는 기본 사항
* 이미지 세트, 스핀 세트 및 혼합 미디어 세트

참조 - [Dynamic Media 여정; 기본 사항, 제 1부](/help/assets/dynamic-media/dm-journey-part1.md).

>[!TIP]
>
>최상의 결과를 얻으려면 데스크톱 컴퓨터에서 이 Dynamic Media 여정을 읽고 보는 것이 좋습니다.

## Dynamic Media URL의 구조 및 Dynamic Media이 컨텐츠를 제공하는 방법 {#dm-journey-d}

Dynamic Media 자산이 업로드 및 게시되면, 자산의 생성 URL을 복사하여 브라우저에 붙여넣어 자산이 고객에게 어떻게 표시되는지 확인할 수 있습니다. 감시 이미지의 다음의 복사된 URL은 읽고 이해할 수 있도록 색상으로 구분됩니다.

![Dynamic Media URL 구조](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Dynamic Media URL 구조._

빨간색 URL의 첫 번째 부분이 서버 도메인 자체를 참조합니다. 이 경우 Dynamic Media은 일반 서버 도메인에서 실행되며, `https://s7d1.scene7.com/is/image/`. 서버 도메인을 보기만 해도 이미지 세트를 쉽게 보고 Dynamic Media에서 이미지 세트를 제공하는지 여부를 알 수 있습니다. URL은 상당히 일관됩니다. 그러나 일부 Dynamic Media 고객이 서버 전용 도메인으로 전환했을 수도 있습니다 `name-of-your-company.scene7.com`. 스마트 이미징에는 전용 서버 도메인이 필요합니다.

계정 이름은 자주색 부분입니다. 이 경우 계정을 라고 합니다 `jpearldemo`.

자산 ID 또는 이름, `AdobeStock_28563982` 녹색입니다. 자산이 _아니요_ 파일 확장명(예: `.png` 또는 `.jpg`. 자산을 Dynamic Media에 수집하면 파일 확장명이 제거되고 다른 종류의 파일이 만들어집니다. 피라미드 TIFF 파일. 피라미드형 TIFF을 사용하면 Dynamic Media에서 신속하게 렌디션을 만들 수 있습니다.

그리고 마지막으로, 몇 가지 이미지 처리 매개 변수가 있는데 `?wid=1000&fmt=jpeg&qlt=85`끝에 노란색으로 표시됩니다.

전체 URL 경로가 라이브입니다. [사용해 보세요](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85){target=&quot;_blank&quot;}.

브라우저 창이 여전히 Dynamic Media URL 및 감시 이미지에 열려 있으므로 URL을 변경하여 이미지의 렌디션을 만들 수 있는 방법을 자세히 살펴보겠습니다.

### URL을 통해 시계 이미지 렌더링

먼저 URL 경로에 있는 이미지 처리 규칙만 수동으로 삭제합니다. 서버 이름, 계정 이름 및 자산 ID 또는 이미지 이름을 그대로 둡니다. [사용해 보세요](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982){target=&quot;_blank&quot;}.

이제 이미지 처리 매개 변수를 URL 끝에 추가합니다. 이미지 이름의 오른쪽에 있는 URL 필드에 다음을 입력합니다 `?wid=500`, 그런 다음 키를 누릅니다. **[!UICONTROL Enter 키]**. [사용해 보세요](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500){target=&quot;_blank&quot;}.

시계의 새 표현물이 생성된다는 점에 주의하십시오. 이미지의 너비를 변경하는 간단한 연습에서 이해하려면 보이는 이미지가 동적으로 100% 생성된다는 것입니다.

이제 너비 값을 `500` 픽셀 단위 `1000` 픽셀을 누르고 **[!UICONTROL Enter 키]**. [사용해 보세요](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000).
당신이 압박하는 순간 **[!UICONTROL Enter 키]**&#x200B;로 설정되면 브라우저가 Dynamic Media 이미지 서버로 돌아갑니다. 방금 입력한 새 너비 값에 따라 시계의 새 렌디션을 생성하고 새 이미지를 다시 브라우저에 전달하고 캐시합니다.

Dynamic Media에는 웹 페이지에서 이미지 자산을 세밀하게 조정하는 데 사용할 수 있는 다양한 이미지 처리 매개 변수가 있습니다. 다음을 수행할 수 있습니다 [여기 있는 목록 보기](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=en).

이제 감시 이미지에 회전 매개 변수를 추가해 보십시오. URL 경로의 끝은 바로 다음에 옵니다 `wid=1000`, 유형 `&rotate=90`를 누른 다음 키를 누릅니다. **[!UICONTROL Enter 키]**. [사용해 보세요](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90){target=&quot;_blank&quot;}.

그 시계는 여전히 왼쪽으로 약간 기울어져 있다. 의 회전 값 변경 `90` to `92`를 누른 다음 키를 누릅니다. **[!UICONTROL Enter 키]**. [사용해 보세요](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9){target=&quot;_blank&quot;}.

다시 한번, 당신이 압박하는 순간 **[!UICONTROL Enter 키]**&#x200B;를 입력하면 시계의 새 표현물이 즉시 생성됩니다. 제공되는 성능의 종류를 확인할 수 있으므로 Dynamic Media에서 80만 개 이상의 이미지 요청을 제공하는 이유를 설명합니다. _초당_&#x200B;바쁜 주말, 또는 주요 공휴일에.

이미지별 URL로 이미지 처리 매개 변수를 변경할 수 있지만, 특히 웹 사이트를 구성하는 수만 개의 이미지가 있는 경우에는 효율적이지 않습니다. 이미지 사전 설정을 사용하는 것이 훨씬 좋습니다.

## 자산을 렌더링하기 위해 이미지 사전 설정을 만드는 기본 사항 {#dm-journey-e}

이미지를 만들거나 이미지를 사용할 수 있도록 하려는 다양한 방법과 위치가 있습니다. 일반적으로 Creative는 Adobe Photoshop에 들어가서 이러한 다양한 표현물을 정적 이미지로 저장합니다.

![정적 이미지](/help/assets/dynamic-media/assets/dm-static-images.png)
_좋습니다: 정적 이미지, 각각 수동으로 만든 이미지._

이제 창조형 Director이 이미지를 보고 이렇게 말한다고 상상해보세요.

_&quot;저는 이 샷을 정말 원해서 큰 손이 4개를 가리키고 작은 손이 1을 가리키면 시계를 더 쉽게 볼 수 있게 됩니다.&quot;_

창의성은 이 새로운 정적 이미지를 다시 촬영해야 할 것이다.

그러나 Dynamic Media을 사용하면 서로 다른 이미지 사전 설정이 있는 경우 이미지가 필요한 곳에 해당 이미지를 사용할 수 있습니다. 이미지 사전 설정은 표준을 적용합니다.

![기본 파일 접근 방식](/help/assets/dynamic-media/assets/dm-onefile.png)
_최고: 예를 들어, 이미지 사전 설정을 사용하여 즉시 생성된 여러 표현물이 있는 하나의 파일 `Search_Grid` 및 `Thumbnail`._

| **이미지 사전 설정을 사용하는 이유는 무엇입니까?** |  |
|---|---|
| 표준 | 이미지 사전 설정은 요청한 이미지에 표준 이미지 처리 처리를 적용합니다. |
| 변경 관리 | 이미지 처리를 변경해야 하는 경우, 기존 이미지 사전 설정의 매개 변수를 편집하기만 하면 됩니다. 업데이트된 정의는 자동으로 모든 요청에 전파됩니다. |

특정 유형의 이미지가 필요한 모든 위치(예:

* 제품 세부 사항 페이지,
* 검색 표,
* 축소판,
* 쇼핑 카드 또는
* 영웅 이미지

어디에 사용하든 동일한 매개 변수와 함께 해당 이미지를 전달하려고 합니다.

잠시 Dynamic Media에서 이미지 사전 설정이 어떻게 생성되는지 살펴보겠습니다.

![기본 탭으로 시작하는 이미지 사전 설정 만들기](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
_기본 탭으로 시작하는 이미지 사전 설정 만들기_

위의 예에서는 이름이 인 새 이미지 사전 설정이 만들어졌는지 확인할 수 있습니다 _Medium_. Dynamic Media에서는 이미지 사전 설정을 만들 때 그 특성을 볼 수 있도록 기본 제공 이미지(백팩)의 예를 사용합니다.

다음 _Medium_ 이미지 사전 설정은 너비 500픽셀과 높이 800픽셀입니다. 이 여정의 1부에서 다양한 형식으로 자산 전달에 대해 읽습니다. 에서 **[!UICONTROL 형식]** 풀다운 메뉴에서 자산을 JPEG, PNG, TIFF 또는 기타 여러 형식으로 전달하도록 선택할 수 있습니다. 여기 융통성이 있습니다

선택 **[!UICONTROL 고급]** 탭에는 자산의 색상 공간에 대한 옵션이 있습니다. 에서 선택한 형식에 따라 **[!UICONTROL 기본]** 탭 - 위의 예에서 JPEG이 선택되었습니다. RGB, 회색 음영 또는 CMYK로 자산을 제공할 수 있습니다. 에서 **[!UICONTROL 색상 프로필]** 풀다운 메뉴에서 인쇄에 사용할 CMYK 이미지 자산을 전달하는 방법을 선택할 수 있습니다. 또한 이미지를 선명하게 하기 위해 적용할 수 있는 추가 매개 변수가 있습니다. 이 경우 **[!UICONTROL 언샵 마스크]** 이 적용되었습니다.

![고급 탭에서 옵션을 선택하여 이미지 사전 설정 작성](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_고급 탭에서 옵션을 선택하여 이미지 사전 설정을 만듭니다._

네가 생각하기에 [Dynamic Media URL 구조](#dm-journey-d) 이전에는 Dynamic Media URL과 이 URL이 빌드된 방법에 대해 읽었습니다. 다음 **[!UICONTROL 이미지 수정자]** 텍스트 상자에 원하는 추가 이미지 처리 매개 변수를 입력할 수 있습니다. 매개 변수는 사전 설정을 사용하여 이미지를 전달할 때 URL의 사전 설정 이름에 포함됩니다. 위의 스크린샷에서 매개 변수는 `bgc=451B15` 이 추가되었습니다. 즉, 짙은 갈색의 배경색이 추가되었습니다.

이미지 사전 설정을 이미지의 조리법으로 생각할 수 있습니다. 이 서비스는 항상 사전 설정을 사용하는 모든 이미지를 제공합니다. 그것은 같을 것입니다. 매개 변수 `&op_brightness=+10` 밝기를 약간 늘리기 위해 도 추가되었습니다.

완료되면 사전 설정을 저장하고 있는 모든 이미지에 사용 가능합니다. 이 경우 _Medium_ 액체 초콜릿 한 그릇 이미지에 미리 설정된 이미지.

![이미지 사전 설정 적용 *Medium* 이미지의 렌디션을 생성하려면](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
_이미지 사전 설정 Medium을 적용하여 이미지의 렌디션을 생성합니다._

URL을 복사한 다음 브라우저에 붙여 넣어 이미지의 모양을 확인합니다. [사용해 보세요](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$){target=&quot;_blank&quot;}. 브라우저에서 이미지 사전 설정의 이름을 확인합니다 _Medium_ 를 입력합니다.

이미지에 표시되는 명확성의 종류를 볼 수 있습니다. 그 질은 부분적으로 초콜릿 그릇이 탄 방식 때문입니다. 또한 Dynamic Media을 사용하면 디지털 채널에 전달되는 이미지보다 더 큰 이미지를 저장할 수 있기 때문입니다.

초콜릿에 대한 모든 것이 만족스러우면 URL을 웹 페이지에 붙여 넣어 이미지를 웹 사이트에 표시할 수 있습니다.

아래 감시 이미지를 다시 보면 `Cart` 이미지 사전 설정, `Grid` 사전 설정, `Large` 사전 설정, `PDP-page` (제품 세부 사항 페이지) 사전 설정 및 기타 여러 페이지가 있습니다.

![정적 및 동적 이미지 사전 설정](/help/assets/dynamic-media/assets/dm-image-presets.png)
_정적 및 동적 이미지 사전 설정. 시계 이미지가 `PDP-page` 이미지 사전 설정._

하지만 웹 사이트에서 이미지를 변경해야 한다면 어떻게 됩니까? 예를 들어, 일부 테스트를 수행했으며 120 x 120의 이미지( `Cart` 이미지 사전 설정)이 제대로 수신되지 않습니다. 너비를 175픽셀로 늘리고 높이를 175픽셀로 증가시켜 이미지를 더 크게 만들어야 합니다. 일반적으로 Adobe Photoshop으로 이동하여 이러한 모든 장바구니 이미지를 다시 만들어야 합니다. 그러나 Dynamic Media을 사용하면 아래 예와 같이 폭과 높이 값을 175로 업데이트하여 이미지 사전 설정을 편집하고 사전 설정을 저장하면 됩니다.

![이미지 사전 설정 편집](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_너비와 높이 편집 `Cart` 이미지 사전 설정._

이미지 사전 설정을 변경하고 캐시를 플러시하면 모든 이미지가 업데이트되고 해당 사전 설정과 함께 사용 중인 모든 URL이 업데이트됩니다 _not_ 아무 곳이나 변경합니다. 즉, 끊어진 링크가 없으며 웹 페이지 리디렉션이 필요하지 않습니다.

## 이미지 세트, 스핀 세트 및 혼합 미디어 세트 {#dm-journey-f}

Dynamic Media의 가장 일반적인 사용 중 일부는 이미지 세트, 스핀 세트 및 혼합 미디어 세트를 만드는 기능입니다.

이미지 세트는 일반적으로 단일 엔티티로 표시되는 일련의 이미지 자산으로 구성됩니다. 이러한 종류의 세트는 사용자에게 축소판 이미지를 클릭하여 항목의 다른 보기를 볼 수 있는 통합된 보기 환경을 제공합니다. 이미지 세트를 사용하면 어떤 것의 대체 보기를 표시할 수 있으며 뷰어는 이미지를 자세히 검사할 수 있는 확대/축소 도구를 제공합니다. [플라이아웃 뷰어를 사용하는 &quot;실행 중&quot;이라는 이미지 세트를 봅니다](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running).

여기 Dynamic Media에서 운동화 몇 가지 이미지를 볼 수 있습니다. 이 시리즈는 판매 및 마케팅에서 고객이 단일 프레젠테이션으로 보기를 원하는 제품 라인 시리즈입니다. 이미지 세트.

![이미지 세트 만들기](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_이미지 세트를 만들기 시작합니다._

이미지 세트를 만들려면 **[!UICONTROL 이미지 세트]** 에서 **[!UICONTROL 만들기]** 풀다운 메뉴. 메뉴를 통해 다음을 생성할 수 있는 옵션도 있습니다. **[!UICONTROL 혼합 미디어 세트]**, **[!UICONTROL 스핀 세트]**, 및 **[!UICONTROL 회전판 세트]**. 이미지 세트와 거의 동일한 방법으로 이러한 세트를 만듭니다.

혼합 미디어 세트에는 이미지, 견본 세트, 스핀 세트, 비디오 및 응용 비디오 세트가 포함될 수 있습니다. [사용해 보세요](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). 스핀 세트는 개체를 돌려 검사하는 실제 동작을 시뮬레이션합니다. 스핀 세트를 사용하면 모든 각도에서 주요 시각적 세부 사항을 볼 수 있습니다. [사용해 보세요](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400){target=&quot;_blank&quot;}.

이미지 세트를 만드는 것은 간단합니다. 세트에 포함할 이미지 자산을 추가하면 됩니다.

![이미지 세트 만들기](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_이미지 세트 편집기를 사용하면 이미지 자산을 추가하고 세트에서 모양 순서를 변경할 수 있습니다._

세트에 이름을 지정해야 합니다. 나중에 편집할 수 없으므로 이름을 신중하게 선택하십시오. 위의 예에서 이 세트를 라고 합니다 `Running`. 완료되면 세트를 저장합니다.

그리고 여기 `Running` Experience Manager Assets에 설정된 이미지.

![Experience Manager Assets, 카드 보기의 실행 이미지 세트](/help/assets/dynamic-media/assets/dm-image-set.png)
_다음 `Running` Experience Manager Assets, 카드 보기에서 설정된 이미지._

이미지 세트, 혼합 미디어 세트, 스핀 세트 또는 기타 대화형 미디어를 만들었는지 여부에 관계없이 세트를 만든 후에 해당 이미지가 어떻게 나타나는지, 고객을 위해 동작하는지를 확인해야 합니다. Dynamic Media에는 바로 사용할 수 있는 다양한 내장된 뷰어가 있습니다.

다음 예와 같이 미리 보기에서 열 기본 이미지 세트를 선택하여 시작합니다.

![뷰어를 선택한 상태로 미리 보기에서 실행 중인 이미지 세트](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_다음 `Running` 뷰어 옵션을 선택한 상태로 미리 보기에 설정된 이미지._

미리 보기에서는 실행 중인 신발 견본을 선택하고 신발을 확대 및 축소할 수 있습니다. 집합에 뷰어를 적용하려면 **[!UICONTROL 뷰어]** 를 클릭합니다.

![플라이아웃 뷰어가 적용된 실행 중인 이미지 세트](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
_다음 `Running` 플라이아웃 뷰어가 적용된 이미지 세트입니다._

이 경우 `Flyout` 뷰어를 선택했습니다. 이 시점에서 뷰어에서 이미지 세트를 미리 볼 수 있습니다. 그러나 고객이 보는 방식으로 브라우저에서 확인하는 것이 가장 좋습니다. 다음을 선택합니다 **[!UICONTROL URL]** 왼쪽 아래에서 URL을 복사하여 브라우저에 붙여넣습니다. [사용해 보세요](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout){target=&quot;_blank&quot;}.

단일 URL을 사용하면 웹 사이트에서 필요한 이미지 세트와 뷰어를 사용할 수 있습니다. 이전 예에서 **[!UICONTROL 포함]** 는 URL 단추 오른쪽에 있습니다. 선택 **[!UICONTROL 포함]**&#x200B;로 지정하는 경우 이 이미지 세트/뷰어의 코드를 복사하여 웹 페이지 또는 Experience Manager Sites 구성 요소에 추가할 수 있습니다.

플라이아웃 뷰어는 속성을 편집할 수 있는 기본 기본 제공 뷰어입니다. 또는 이미지 사전 설정을 만드는 것처럼 사용자 지정 뷰어를 직접 만들 수도 있습니다.

이제, 영업 팀과 마케팅 팀이 플라이아웃 뷰어를 좋아하지 않는다고 가정하겠습니다. 확대/축소 기능을 좋아하지만 고객이 신발을 통해 바로 확대/축소 효과를 볼 수 있도록 할 것입니다. 이 경우 이미지 세트에 InlineZoom 뷰어를 적용하고 브라우저에서 해당 URL을 복사하여 붙여 넣어 어떻게 동작하는지 확인하면 됩니다. [사용해 보세요](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom){target=&quot;_blank&quot;}.

마우스 포인터를 신발 위로 이동하면 해당 이미지를 확대하면 포인터를 이동할 때 더 자세히 볼 수 있습니다. 그리고 그 이유는 단순히 Dynamic Media에 처음 업로드된 이미지의 크기입니다.

여러분이 소비자로 살고 있다고 생각하거나, 일상적인 역할을 하고, 다른 웹 사이트에 갈 때, 여러분은 이와 같은 것들을 보게 됩니다. 이러한 작업이 어떻게 수행되는지, 작업 및 회사 웹 사이트에서 Dynamic Media의 강력한 기능을 사용하는 방법에 대해 생각해 보십시오.

이미지 세트와 뷰어에 대해 조금 읽으셨네요. 다른 시청자 몇 명을 보고 단일 자산에 대해 알아보겠습니다. 뷰어를 재설정하려면 **[!UICONTROL 새로 고침]** 왼쪽 아래 모서리에 있는 버튼.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* `ZoomVertical_dark` 이미지 자산에 적용된 뷰어. [사용해 보세요](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark){target=&quot;_blank&quot;}.
* `Zoom_light` 이미지에 적용된 뷰어. [사용해 보세요](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light){target=&quot;_blank&quot;}.

## 선택 사항 - 자세히 알아보기

방금 읽은 내용을 자세히 알아보려면 아래 자료를 사용하여 개념을 자세히 살펴보십시오. 그렇지 않으면 Dynamic Media 여정이 완료되었습니다!

_Dynamic Media 도움말 항목_

* [이미지 사전 설정을 만드는 방법](/help/assets/dynamic-media/image-presets.md)
* 목록 [이미지 처리 매개 변수](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) 이미지 사전 설정을 생성할 때 이미지 수정자 필드에서 사용할 수 있습니다
* [자산을 미리 보는 방법](/help/assets/dynamic-media/previewing-assets.md)
* [3D 자산을 미리 보는 방법](/help/assets/dynamic-media/previewing-3d-assets.md)
* [이미지 세트를 만드는 방법](/help/assets/dynamic-media/image-sets.md)
* [스핀 세트를 만드는 방법](/help/assets/dynamic-media/spin-sets.md)
* [혼합 미디어 세트를 만드는 방법](/help/assets/dynamic-media/mixed-media-sets.md)

_Dynamic Media 자습서_

* [Experience Manager Assets과 Dynamic Media 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [Adobe Experience Manager 콘텐츠 라이브러리](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager) (검색) _Dynamic Media_)

_Dynamic Media 뷰어_

* [라이브 데모](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) 각 뷰어의

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->