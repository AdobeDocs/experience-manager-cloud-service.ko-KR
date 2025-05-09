---
title: Dynamic Media, Part II에 여정
description: Dynamic Media 여정은 Dynamic Media의 기본 사항, 작동 방식, 무엇을 수행할 수 있으며 작업 및 고객에게 어떤 가치를 제공하는지 설명합니다.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles,Best Practices
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: cdca41ad-a2cd-4f68-aaa4-5eec33c30f0b
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '2621'
ht-degree: 0%

---

# Dynamic Media 여정: 기본 사항, 2부  {#dm-journey-part2}

{{see-also-dm}}

Dynamic Media 여정 시작: 다음을 배울 수 있는 기본 사항, 2부

* Dynamic Media URL의 구조 및 Dynamic Media가 콘텐츠를 전달하는 방법입니다.
* 자산을 렌더링할 이미지 사전 설정을 만드는 기본 사항.
* 이미지 세트, 스핀 세트 및 혼합 미디어 세트입니다.

[Dynamic Media 여정; 기본 사항, 파트 I](/help/assets/dynamic-media/dm-journey-part1.md)도 참조하세요.

>[!TIP]
>
>최상의 결과를 얻으려면 데스크톱 컴퓨터에서 이 Dynamic Media 여정을 읽고 볼 것을 Adobe에 권장합니다.

## Dynamic Media URL의 구조 및 Dynamic Media가 콘텐츠를 제공하는 방법 {#dm-journey-d}

Dynamic Media 에셋이 업로드되고 게시된 후 에셋에서 생성된 URL을 복사하여 브라우저에 붙여넣어 에셋이 고객에게 어떻게 표시되는지 확인할 수 있습니다. 시계 이미지에 대해 다음과 같이 복사된 URL은 읽고 이해하기 쉽도록 색상별로 분류됩니다.

![Dynamic Media URL의 구조](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Dynamic Media URL의 구조._

빨간색으로 표시된 URL의 첫 번째 부분은 서버 도메인 자체를 참조합니다. 이 경우 Dynamic Media는 일반 서버 도메인(`https://s7d1.scene7.com/is/image/`)에서 실행되고 있습니다. 서버 도메인만 보면 이미지 집합을 보고 Dynamic Media에서 이 이미지를 제공하는지 여부를 쉽게 이해할 수 있습니다. URL은 일관되게 유지됩니다. 그러나 일부 Dynamic Media 고객이 전용 서버 도메인으로 전환하여 `name-of-your-company.scene7.com`이(가) 될 수 있습니다. 스마트 이미징에는 전용 서버 도메인이 필요합니다.

계정 이름은 자주색으로 된 부분입니다. 이 경우 계정을 `jpearldemo`이라고 합니다.

자산 ID 또는 이름 `AdobeStock_28563982`이(가) 녹색으로 표시되어 있습니다. 자산에 `.png` 또는 `.jpg`과(와) 같은 _no_ 파일 확장명이 있습니다. 에셋을 Dynamic Media에 수집하면 파일 확장자가 제거되고 다른 종류의 파일이 생성됩니다. 피라미드 TIFF 파일입니다. Pyramic-TIFF을 사용하면 Dynamic Media가 신속하게 표현물을 즉석에서 만들 수 있습니다.

마지막으로 이미지 처리 매개 변수 `?wid=1000&fmt=jpeg&qlt=85`이(가) 끝에 노란색으로 표시됩니다.

전체 URL 경로는 라이브입니다. [사용해 보기](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85){target="_blank"}.

브라우저 창에서 Dynamic Media URL과 시계 이미지를 볼 수 있지만 URL을 변경하는 것만으로 이미지 렌디션을 만드는 방법에 대해 자세히 살펴보겠습니다.

### URL을 통해 시계 이미지 렌더링

먼저 URL 경로에서 이미지 처리 규칙만 수동으로 삭제하고 서버 이름, 계정 이름 및 자산 ID 또는 이미지 이름을 그대로 둡니다. [사용해 보기](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982){target="_blank"}.

이제 URL 끝에 이미지 처리 매개 변수를 추가합니다. URL 필드에서 이미지 이름 오른쪽에 `?wid=500`을(를) 입력한 다음 **[!UICONTROL Enter]**&#x200B;를 누릅니다. [사용해 보기](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500){target="_blank"}.

시계의 새 렌디션이 생성됩니다. 이미지의 폭을 변경하는 이러한 간단한 연습에서 이해하는 핵심은 표시되는 이미지가 100% 동적으로 생성된다는 것입니다.

이제 너비 값 `500`픽셀을 `1000`픽셀로 변경한 다음 **[!UICONTROL Enter]**&#x200B;을 누릅니다. [사용해 보기](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000){target="_blank}.
**[!UICONTROL Enter]**&#x200B;를 누른 후 브라우저가 Dynamic Media 이미지 서버로 돌아갑니다. 방금 입력한 새 너비 값을 기반으로 시계의 새 렌디션을 생성한 다음 새 이미지를 브라우저에 다시 전달하고 캐시합니다.

Dynamic Media에는 웹 페이지에서 이미지 자산을 미세 조정하는 데 사용할 수 있는 다양한 이미지 처리 매개 변수가 있습니다. [목록을 여기에서 볼 수 있습니다](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=ko).

이제 시계 이미지에 회전 매개 변수를 추가해 보십시오. `wid=1000` 바로 다음에 오는 URL 경로의 끝에 `&rotate=90`을(를) 입력한 다음 **[!UICONTROL Enter]**&#x200B;를 누릅니다. [사용해 보기](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90){target="_blank"}.

그 시계는 아직도 약간 왼쪽으로 기울어져 있다. 회전 값 `90`을(를) `92`(으)로 변경한 다음 **[!UICONTROL Enter]**&#x200B;를 누릅니다. [사용해 보기](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9){target="_blank"}.

다시 **[!UICONTROL Enter]**&#x200B;를 누르는 순간 시계의 새 렌디션이 거의 즉시 생성됩니다. 성능이 어느 정도인지 확인할 수 있습니다. 이렇게 하면 Dynamic Media가 바쁜 주말 또는 주요 휴일에 초당 _개_&#x200B;의 800,000개 이상의 이미지 요청을 제공할 수 있습니다.

이미지별로 URL의 이미지 처리 매개 변수를 변경할 수 있지만, 특히 웹 사이트를 구성하는 이미지가 수만 개 있는 경우에는 효율적인 방법이 아닙니다. 이미지 사전 설정을 사용하는 것이 훨씬 좋습니다.

## 자산 렌더링용 이미지 사전 설정 만들기의 기본 사항 {#dm-journey-e}

이미지를 만들거나 이미지를 사용할 수 있는 다양한 방법과 위치가 있습니다. 일반적으로 Creative은 Adobe Photoshop으로 이동하여 이러한 다양한 렌디션을 각각 정적 이미지로 저장합니다.

![정적 이미지](/help/assets/dynamic-media/assets/dm-static-images.png)
_좋음: 정적 이미지, 각 이미지를 수동으로 만들었습니다._

이제 Creative 감독이 이미지를 보고 이렇게 말하는 것을 상상해 보십시오.

_&quot;큰 손이 4개를 가리키고 작은 손이 1을 가리키도록 하여 시계 다이얼을 더 쉽게 볼 수 있게 하고 싶었습니다.&quot;_

크리에이티브는 모든 새로운 정적 이미지를 다시 촬영해야 할 것이다.

그러나 Dynamic Media를 사용하면 다른 이미지 사전 설정이 있는 경우 필요할 때마다 이러한 이미지를 사용할 수 있습니다. 이미지 사전 설정은 표준을 적용합니다.

![기본 파일 접근 방식](/help/assets/dynamic-media/assets/dm-onefile.png)
_최상: `Search_Grid` 및 `Thumbnail`과 같은 이미지 사전 설정을 사용하여 즉석에서 만들어지는 여러 표현물이 있는 파일 하나._

| **이미지 사전 설정을 사용하는 이유는 무엇입니까?** | |
|---|---|
| 표준 | 이미지 사전 설정은 요청된 이미지에 표준 이미지 처리 처리를 적용합니다. |
| 변경 관리 | 이미지 처리를 변경해야 하는 경우 기존 이미지 사전 설정의 매개 변수를 편집하면 됩니다. 업데이트된 정의는 자동으로 모든 요청에 전파됩니다. |

특정 유형의 이미지를 보유해야 하는 모든 위치(예:

* 제품 세부 사항 페이지,
* 검색 그리드,
* 축소판,
* 쇼핑 카드 또는
* 영웅 이미지

사용할 위치에 관계없이 동일한 매개 변수와 함께 해당 이미지를 전달하려고 합니다.

잠시 Dynamic Media에서 이미지 사전 설정을 만드는 방법을 살펴보겠습니다.

![기본 탭으로 시작하는 이미지 사전 설정 만들기](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
_기본 탭으로 시작하는 이미지 사전 설정을 만드는 중입니다._

위의 예에서는 이름이 _Medium_&#x200B;인 새 이미지 사전 설정을 만든 것을 볼 수 있습니다. Dynamic Media는 예제 기본 제공 이미지(배낭)를 사용하여 이미지 사전 설정을 만들 때 이미지 특성을 볼 수 있도록 합니다.

_Medium_ 이미지 사전 설정의 너비는 500픽셀이고 높이는 800픽셀입니다. 이 여정의 Part I에서 에셋을 다양한 형식으로 제공하는 방법에 대해 읽었습니다. **[!UICONTROL 형식]** 풀다운 메뉴에서 자산을 JPEG, PNG, TIFF 또는 기타 여러 형식으로 전달하도록 선택할 수 있습니다. 여기는 융통성이 있으시군요.

**[!UICONTROL 고급]** 탭을 선택하면 에셋의 색상 공간에 대한 옵션이 제공됩니다. **[!UICONTROL 기본]** 탭에서 선택한 형식에 따라(위의 예에서는 JPEG이 선택됨) RGB, 회색 음영 또는 CMYK로 자산을 전달할 수 있습니다. **[!UICONTROL 색상 프로필]** 풀다운 메뉴에서 인쇄에 사용할 CMYK 이미지 에셋을 전달하는 방법을 선택할 수 있습니다. 이미지를 선명하게 하기 위해 적용할 수 있는 추가 매개 변수도 있습니다. 이 경우 **[!UICONTROL 언샵 마스크]**&#x200B;가 적용되었습니다.

![고급 탭에서 옵션을 선택하여 이미지 사전 설정 만들기](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_고급 탭에서 옵션을 선택하여 이미지 사전 설정을 만듭니다._

이전에 [Anatomy of a Dynamic Media URL](#dm-journey-d)에서 Dynamic Media URL 및 빌드 방법에 대해 읽은 것을 상기했습니다. **[!UICONTROL 이미지 수정자]** 텍스트 상자에 원하는 추가 이미지 처리 매개 변수를 입력할 수 있습니다. 매개 변수는 사전 설정을 사용하여 이미지가 전달될 때 URL의 사전 설정 이름에 포함됩니다. 위의 스크린샷에 `bgc=451B15` 매개 변수가 추가되었습니다. 즉, 어두운 갈색의 배경색을 추가하였다.

이미지 사전 설정은 이미지의 레시피로 생각할 수 있습니다. 사전 설정을 사용하는 모든 이미지를 항상 일관되게 전달합니다. 항상 동일합니다. 밝기를 약간 늘리기 위해 매개 변수 `&op_brightness=+10`도 추가되었습니다.

완료되면 사전 설정을 저장하면 이제 보유한 모든 이미지에 사용할 수 있습니다. 이 경우 _Medium_ 이미지 사전 설정을 액체 초콜릿 그릇의 이미지에 적용하려고 합니다.

![이미지 사전 설정 *Medium*&#x200B;을(를) 적용하여 이미지 렌디션 생성](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
_이미지 사전 설정 Medium을 적용하여 이미지 렌디션을 생성합니다._

URL을 복사한 다음 브라우저에 붙여넣어 이미지의 모양을 확인합니다. [사용해 보기](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$){target="_blank"}.

브라우저에서 전체 URL 경로에 있는 이미지 사전 설정 _Medium_&#x200B;의 이름을 확인합니다.

이미지에 표시되는 선명도 종류를 확인할 수 있습니다. 그 품질은 부분적으로 초콜릿 그릇을 찍은 방식 때문입니다. 또한 Dynamic Media를 사용하면 디지털 채널에 제공되는 이미지보다 더 큰 이미지를 저장할 수 있기 때문입니다.

모든 것이 초콜릿 그릇에 만족스럽게 보이는 경우 웹 페이지에 이미지를 표시할 URL을 붙여 넣습니다.

아래 시계 이미지를 다시 보면 `Cart` 이미지 사전 설정, `Grid` 사전 설정, `Large` 사전 설정, `PDP-page`(제품 세부 정보 페이지) 사전 설정 등이 있습니다.

![정적 및 동적 이미지 사전 설정](/help/assets/dynamic-media/assets/dm-image-presets.png)
_정적 및 동적 이미지 사전 설정. 시계 이미지가 `PDP-page` 이미지 사전 설정을 사용하여 렌더링되었습니다._

하지만 만약 웹사이트의 이미지를 변경해야 한다면? 예를 들어 일부 테스트를 수행했으며 120 x 120의 이미지(`Cart` 이미지 사전 설정)가 생각대로 수신되지 않고 있다고 가정합니다. 너비를 175픽셀로 늘리고 높이를 175픽셀로 늘려 이미지를 더 크게 만들어야 합니다. 일반적으로 Adobe Photoshop으로 이동하여 이러한 모든 장바구니 이미지를 다시 만들어야 합니다. 하지만 Dynamic Media를 사용하면 아래 예와 같이 [폭] 및 [높이] 값을 175로 업데이트하여 이미지 사전 설정을 편집하고 사전 설정을 저장하면 됩니다.

![이미지 사전 설정 편집](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_`Cart` 이미지 사전 설정의 너비와 높이를 편집하는 중입니다._

이미지 사전 설정을 변경하고 캐시를 플러시하면 모든 이미지가 업데이트되고, 해당 사전 설정과 함께 사용 중인 모든 URL은 아무 곳에서도 변경하지 _마십시오_. 즉, 링크가 끊기지 않고 웹 페이지 리디렉션이 필요하지 않습니다.

## 이미지 세트, 스핀 세트 및 혼합 미디어 세트 {#dm-journey-f}

Dynamic Media의 가장 일반적인 용도 중 일부는 이미지 세트, 스핀 세트 및 혼합 미디어 세트를 만들 수 있는 기능입니다.

이미지 세트는 일반적으로 단일 엔티티로 표시되는 일련의 이미지 에셋으로 구성됩니다. 이러한 종류의 세트는 사용자에게 썸네일 이미지를 클릭하여 항목의 다양한 보기를 볼 수 있는 통합된 보기 환경을 제공합니다. 이미지 집합을 사용하면 대체 보기를 표시할 수 있으며 뷰어는 이미지를 면밀하게 검사하는 확대/축소 도구를 제공합니다. [플라이아웃 뷰어를 사용하는 &quot;실행 중&quot;이라는 이미지 집합을 봅니다](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running).

여기 Dynamic Media 내에서 운동화의 여러 이미지를 볼 수 있습니다. 영업 및 마케팅 부서에서 하나의 프레젠테이션 ( 이미지 세트 ) 로 볼 수 있도록 하는 제품 라인 시리즈입니다.

![이미지 집합을 만드는 중](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_이미지 집합 만들기를 시작합니다._

이미지 집합을 만들려면 **[!UICONTROL 만들기]** 풀다운 메뉴에서 **[!UICONTROL 이미지 집합]**&#x200B;을(를) 선택합니다. **[!UICONTROL 혼합 미디어 집합]**, **[!UICONTROL 회전 집합]** 및 **[!UICONTROL 회전 메뉴 집합]**&#x200B;을 만드는 옵션도 있습니다. 이러한 세트는 이미지 세트와 매우 동일한 방식으로 만듭니다.

혼합 미디어 세트에는 이미지, 견본 세트, 스핀 세트, 비디오 및 응용 비디오 세트가 포함될 수 있습니다. [사용해 보기](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). 스핀 세트는 물체를 돌아보고 검토하는 실세계 행위를 시뮬레이션한다. 스핀 세트를 사용하면 모든 각도에서 주요 시각적 세부 사항을 볼 수 있습니다. [사용해 보기](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400){target="_blank"}.

이미지 세트를 만드는 것은 간단합니다. 세트에 포함할 이미지 에셋을 추가하면 됩니다.

![이미지 집합을 만드는 중](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_이미지 집합 편집기를 사용하여 이미지 에셋을 추가하고 집합 내의 모양 순서를 변경할 수 있습니다._

세트의 이름을 지정해야 합니다. 나중에 편집할 수 없으므로 이름을 신중하게 선택하십시오. 위의 예에서 집합 이름은 `Running`입니다. 완료되면 세트를 저장합니다.

Experience Manager Assets에 설정된 `Running` 이미지입니다.

![Experience Manager Assets, 카드 보기에서 실행 중인 이미지 집합](/help/assets/dynamic-media/assets/dm-image-set.png)
_Experience Manager Assets, 카드 보기에서 설정된 `Running` 이미지_

이미지 세트, 혼합 미디어 세트, 스핀 세트 또는 기타 대화형 미디어를 만든 적이 있는지 여부에 관계없이, 세트를 만든 후에 고객을 위해 어떻게 표시되고 동작하는지 확인해야 합니다. Dynamic Media에는 그러한 기능을 제공하는 많은 기본 뷰어가 있습니다.

다음 예제와 같이 미리보기에서 열려면 먼저 빌드된 이미지 세트를 선택합니다.

![뷰어 옵션이 선택된 미리 보기에서 실행 중인 이미지 설정](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_Viewers 옵션을 선택한 미리 보기에서 설정된 `Running` 이미지._

미리 보기에서 실행 중인 신발 견본을 선택하고 신발을 확대하거나 축소할 수 있습니다. 세트에 뷰어를 적용하려면 풀다운 메뉴에서 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

![플라이아웃 뷰어가 적용된 실행 중인 이미지 집합](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
_플라이아웃 뷰어가 적용된 `Running` 이미지 집합입니다._

이 경우 `Flyout` 뷰어가 선택되었습니다. 이 시점에서 뷰어에 설정된 이미지를 미리 볼 수 있습니다. 그러나 고객이 보는 방식대로 브라우저에서 보는 것이 가장 좋습니다. 왼쪽 아래에서 **[!UICONTROL URL]**&#x200B;을(를) 선택한 다음 URL을 복사하여 브라우저에 붙여넣습니다. [사용해 보기](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout){target="_blank"}.

단일 URL을 사용하면 웹 사이트에서 필요한 이미지 세트와 뷰어를 사용할 수 있습니다. 앞의 예제에서 **[!UICONTROL Embed]**&#x200B;이(가) URL 단추 오른쪽에 있음을 알 수 있습니다. **[!UICONTROL 포함]**&#x200B;을 선택하면 이 이미지 집합/뷰어의 코드를 복사하여 웹 페이지나 Experience Manager Sites 구성 요소에 추가할 수 있습니다.

플라이아웃 뷰어는 속성을 편집할 수 있는 기본 기본 뷰어입니다. 또는 이미지 사전 설정을 만드는 것처럼 자신만의 사용자 지정 뷰어를 만들 수 있습니다.

판매 및 마케팅 팀이 플라이아웃 뷰어를 좋아하지 않는다고 가정합니다. 그들은 줌 기능을 좋아하지만 고객들이 신발 위로 바로 줌 효과를 보기를 원합니다. 이러한 경우 이미지 세트에 InlineZoom 뷰어를 적용하고 브라우저에 해당 URL을 복사하여 붙여넣어 작동 방식을 확인하면 됩니다. [사용해 보기](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom){target="_blank"}.

마우스 포인터를 신발 위로 이동하면 해당 이미지를 확대하여 포인터가 움직일 때 더 자세한 내용을 볼 수 있습니다. 그 이유는 단순히 처음에 Dynamic Media에 업로드된 이미지의 크기입니다.

소비자로 살거나 일상적인 역할을 하면서, 또 다른 웹 사이트로 이동하면, 이와 같은 것들을 보게 됩니다. 이를 수행하는 방법과 Dynamic Media의 기능을 자신의 작업과 회사 웹 사이트에서 어떻게 사용할 수 있는지 생각해 보십시오.

이미지 세트와 뷰어에 대해 읽어보십시오. 두 명의 다른 시청자를 보고 단일 자산에 대해 시도해 보겠습니다. 뷰어를 재설정하려면 왼쪽 하단의 **[!UICONTROL 새로 고침]** 단추를 클릭하십시오.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* 이미지 자산에 `ZoomVertical_dark` 뷰어가 적용되었습니다. [사용해 보기](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark){target="_blank"}.
* 이미지에 `Zoom_light` 뷰어가 적용되었습니다. [사용해 보기](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light){target="_blank"}.

## 선택 사항 - 자세히 알아보기

방금 읽은 내용에 대해 자세히 알아보려면 아래 자료를 사용하여 개념을 자세히 살펴보십시오. 그렇지 않으면 Dynamic Media 여정이 완료됩니다!

<!--
_Dynamic Media Help topics_

* [How to create image presets](/help/assets/dynamic-media/image-presets.md)
* A list of [image processing parameters](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=ko) that you can use in the Image Modifier field when you create an image preset
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to create Image sets](/help/assets/dynamic-media/image-sets.md)
* [How to create Spin sets](/help/assets/dynamic-media/spin-sets.md)
* [How to create Mixed Media sets](/help/assets/dynamic-media/mixed-media-sets.md) -->

_Dynamic Media 튜토리얼_

* [Experience Manager Assets에서 Dynamic Media 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html?lang=ko)
* [Adobe Experience Manager 컨텐츠 라이브러리](https://experienceleague.adobe.com/ko?lang=en#recommended/solutions/experience-manager)&#x200B;(_Dynamic Media_&#x200B;에서 검색)

_Dynamic Media 뷰어_

* 각 뷰어의 [실시간 데모](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html)

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->