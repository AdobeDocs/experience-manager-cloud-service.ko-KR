---
title: 이미지 품질 최적화 모범 사례
description: Dynamic Media을 사용하여 이미지 에셋의 품질을 최적화하는 데 도움이 되는 모범 사례에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 2efc4a27-01d7-427f-9701-393497314402
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '1478'
ht-degree: 5%

---

# 이미지 품질 최적화 모범 사례 {#best-practices-for-optimizing-the-quality-of-your-images}

많은 요소가 허용되는 결과를 렌더링하는 데 기여하므로 이미지 품질을 최적화하는 것은 시간이 오래 걸리는 프로세스일 수 있습니다. 결과는 개인들이 이미지 품질을 다르게 인식하기 때문에 부분적으로 주관적이다. 구조화된 실험이 핵심입니다.

Adobe Experience Manager에는 이미지 및 렌더링 결과를 조정 및 최적화하기 위한 100개 이상의 Dynamic Media 이미지 게재 명령이 포함되어 있습니다. 다음 지침은 몇 가지 필수 명령과 모범 사례를 사용하여 프로세스를 간소화하고 좋은 결과를 빠르게 얻을 수 있도록 도와줍니다.

## 이미지 형식 우수 사례(`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG 또는 PNG는 최상의 품질과 관리 가능한 크기 및 무게로 이미지를 전달하는 데 가장 적합한 옵션입니다.
* URL에 format 명령이 제공되지 않으면 Dynamic Media 이미지 게재의 기본값은 게재 JPG입니다.
* JPG은 10:1의 비율로 압축되며 일반적으로 더 작은 이미지 파일 크기를 생성합니다. 이미지에 흰색 배경이 포함된 경우를 제외하고 PNG는 약 2:1의 비율로 압축됩니다. 일반적으로 PNG 파일 크기는 JPG 파일보다 큽니다.
* JPG은 손실 압축을 사용합니다. 즉, 압축하는 동안 그림 요소(픽셀)가 삭제됩니다. 반면에 PNG는 무손실 압축을 사용합니다.
* JPG은 종종 예리한 가장자리와 대비를 갖는 합성 이미지보다 더 충실도 높은 사진 이미지를 압축합니다.
* 이미지에 투명도가 포함되어 있는 경우 JPG이 투명도를 지원하지 않으므로 PNG를 사용합니다.

이미지 형식에 대한 우수 사례로서, 가장 일반적인 설정으로 시작합니다 `&fmt=JPG`.

## 이미지 크기에 대한 우수 사례 {#best-practices-for-image-size}

이미지 크기를 동적으로 줄이는 것은 가장 일반적인 작업 중 하나입니다. 이것은 크기를 지정하는 것과, 선택적으로, 이미지를 다운스케일링하기 위해 사용되는 다운샘플링 모드를 지정하는 것을 포함한다.

* 이미지 크기 조절의 경우 가장 좋은 방법은 를 사용하는 것입니다 `&wid=<value>` 및 `&hei=<value>,`또는 `&hei=<value>`. 이러한 매개 변수는 종횡비에 따라 이미지 폭을 자동으로 설정합니다.
* `&resMode=<value>`다운샘플링에 사용되는 알고리즘을 제어합니다. 다음으로 시작 `&resMode=sharp2`. 이 값은 최상의 이미지 품질을 제공합니다. 다운샘플링을 사용하는 동안 `value =bilin` 가 빠를 경우 종종 아티팩트의 앨리어싱이 발생합니다.

이미지 크기 조정에 대한 우수 사례로, `&wid=<value>&hei=<value>&resMode=sharp2` 또는 `&hei=<value>&resMode=sharp2`

## 이미지 선명하게 하기 우수 사례 {#best-practices-for-image-sharpening}

이미지 선명하게 하기는 웹 사이트에서 이미지를 제어하는 가장 복잡한 측면이며 많은 실수가 발생하는 곳입니다. 다음 유용한 리소스를 참조하여 Experience Manager에서 선명하게 하기 및 언샵 마스킹이 작동하는 방식에 대해 자세히 알아보십시오.

* 모범 사례 백서 [Adobe Dynamic Media Classic 이미지 품질 및 선명하게 하기 우수 사례](/help/assets/dynamic-media/assets/sharpening_images.pdf) Experience Manager에 적용됩니다.

* 시청 [Experience Manager에서 이미지 선명하게 하기 사용 - Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html#dynamic-media).

Experience Manager을 사용하면 수집, 게재 또는 둘 다에 대해 이미지를 선명하게 할 수 있습니다. 그러나 일반적으로 이미지를 선명하게 하는 데는 한 가지 방법이나 다른 방법만 사용하는 것이 가장 좋지만 둘 다 사용하지 않는 것이 좋습니다. URL에서 전달 시 이미지를 선명하게 하면 일반적으로 최상의 결과를 얻을 수 있습니다.

사용할 수 있는 이미지 선명하게 하기 방법에는 두 가지가 있습니다.

* 단순 선명하게 하기( `&op_sharpen`) - Photoshop에서 사용되는 선명 효과 필터와 유사하게, 간단한 선명 효과는 동적 크기 조정 후 이미지의 최종 보기에 기본 선명 효과를 적용합니다. 그러나 이 메서드는 사용자가 구성할 수 없습니다. 가장 좋은 방법은 필요한 경우가 아니면 &amp;op_sharpen을 사용하지 않는 것입니다.
* 언샵 마스킹( `&op_USM`) - 언샵 마스킹은 업계 표준 선명하게 하기 필터입니다. 가장 좋은 방법은 아래 지침에 따라 선명하지 않은 마스킹으로 이미지를 선명하게 하는 것입니다. 언샵 마스킹을 사용하면 다음 세 가지 매개 변수를 제어할 수 있습니다.

   * `&op_sharpen=`양,반경,임계값

      * **[!UICONTROL 금액]** (0-5, 효과의 강도.)
      * **[!UICONTROL 반경]** (0-250, 선명하게 표시된 개체 주위에 그려진 &quot;선명하게 하기 선&quot;의 폭(픽셀 단위)입니다.)

      매개변수 반경과 양은 서로 영향을 받습니다. 감소된 반경은 양을 증가시킴으로써 보상될 수 있다. [반경]을 사용하면 값이 낮을수록 가장자리 픽셀만 선명하게 되고 값이 높을수록 넓은 폭의 픽셀이 선명하게 되므로 더 세밀하게 제어할 수 있습니다.

      * **[!UICONTROL 임계값]** (0-255, 효과 민감도)
      This parameter determines how different the sharpened pixels must be from the surrounding area before they are considered edge pixels and the filter sharpens them. 다음 **[!UICONTROL 임계값]** 매개 변수를 사용하면 피부 색조와 같이 유사한 색상으로 영역을 너무 선명하게 하지 않도록 할 수 있습니다. For example, a threshold value of 12 ignores slight variations in skin tone brightness to avoid adding &quot;noise&quot;, while still adding edge contrast to high contrast areas, such as where eyelashes meet skin.

      필터에 사용하는 모범 사례를 포함하여 이러한 세 매개 변수를 설정하는 방법에 대한 자세한 내용은 다음 리소스를 참조하십시오.

      * 모범 사례 백서 [Adobe Dynamic Media Classic 이미지 품질 및 선명하게 하기 우수 사례](/help/assets/dynamic-media/assets/sharpening_images.pdf) Experience Manager에 적용됩니다.

      * 시청 [Experience Manager에서 이미지 선명하게 하기 사용 - Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html#dynamic-media).

      * Experience Manager을 사용하면 네 번째 매개 변수인 모노크롬(0,1)을 제어할 수도 있습니다. 이 매개 변수는 값 0을 사용하여 각 색상 구성 요소에 언샵 마스킹을 별도로 적용할지 또는 값 1을 사용하여 이미지 밝기/강도에 적용할지 여부를 결정합니다.



언샵 마스크 반경 매개 변수로 시작하는 것이 좋습니다. 다음으로 시작할 수 있는 반경 설정은 다음과 같습니다.

* **[!UICONTROL 웹 사이트]**: 0.2-0.3픽셀
* **[!UICONTROL 사진 인쇄(250-300ppi)]**: 0.3-0.5픽셀
* **[!UICONTROL 오프셋 인쇄(266-300ppi)]**: 0.7~1.0픽셀
* **[!UICONTROL 캔버스 인쇄(150ppi)]**: 1.5-2.0픽셀

1.75에서 4로 서서히 늘립니다. 선명하게 하기가 여전히 원하는 방식이 아닌 경우 반지름을 소수점 단위로 늘리고 1.75에서 4로 다시 실행합니다. 필요에 따라 반복합니다.

모노크롬 매개 변수 설정을 0으로 둡니다.

### JPEF 압축에 대한 우수 사례(`&qlt=`) {#best-practices-for-jpef-compression-qlt}

* 이 매개 변수는 JPG 인코딩 품질을 제어합니다. 값이 높을수록 이미지 품질은 높지만 파일 크기는 커집니다. 또는 값이 낮을수록 이미지 품질은 낮지만 파일 크기는 작아집니다. 이 매개 변수의 범위는 0~100입니다.
* 품질을 최적화하려면 매개 변수 값을 100으로 설정하지 마십시오. 90 또는 95 및 100 설정의 차이는 거의 감지할 수 없지만 100이 있으면 이미지 파일의 크기가 불필요하게 증가합니다. 따라서 품질을 최적화하지만 이미지 파일이 너무 커지지 않도록 하려면 다음을 설정하십시오. `qlt= value` 90 또는 95로 업그레이드했습니다.
* 이미지 파일 크기는 작지만 이미지 품질을 허용 가능한 수준으로 유지하려면 `qlt= value` 80까지. 70 내지 75 미만의 값은 상당한 이미지 품질 저하를 초래한다.
* 가장 좋은 방법은 중간에 머물기 위해 `qlt= value` 85세까지...
* 에서 크로마 플래그 사용 `qlt=`

   * 다음 `qlt=` 매개 변수에는 값을 사용하여 RGB 색도 다운샘플링을 켤 수 있는 두 번째 설정이 있습니다 `,1` 또는 값을 사용하여 끄기 `,0`.
   * 단순성을 유지하려면 RGB 색도 다운샘플링을 끄기(`,0`). 이 설정을 사용하면 일반적으로 이미지 품질이 향상됩니다. 특히 가장자리가 선명하고 대비가 많은 합성 이미지의 경우 더욱 그렇습니다.

JPG 압축 사용에 대한 우수 사례로서 `&qlt=85,0`.

## JPEG 크기 조정 우수 사례(`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

매개 변수 `jpegSize` 는 메모리가 제한된 장치에 전달할 때 이미지가 특정 크기를 초과하지 않도록 하려는 경우 유용합니다.

* 이 매개 변수는 KB 단위로 설정됩니다(`jpegSize=&lt;size_in_kilobytes&gt;`). 이미지 게재에 허용되는 최대 크기를 정의합니다.
* `&jpegSize=` 이 JPG 압축 매개 변수와 상호 작용합니다. `&qlt=`. JPG 응답이 지정된 JPG 압축 매개 변수를 사용하는 경우(`&qlt=`)이 jpegSize 값을 초과하지 않으면 이미지가 `&qlt=` 정의된 대로. 그렇지 않으면, `&qlt=` 이미지가 최대 허용 크기에 맞을 때까지 또는 시스템이 이미지가 맞지 않는다고 판단하여 오류를 반환할 때까지 점차적으로 감소합니다.

모범 사례로서 다음을 설정합니다. `&jpegSize=` 매개 변수 추가 `&qlt=` 메모리가 제한된 장치에 JPG 이미지를 전달하는 경우.

## 모범 사례 요약 {#best-practices-summary}

높은 이미지 품질과 작은 파일 크기를 달성하려면 다음 매개 변수 조합으로 시작하는 것이 좋습니다.

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

이러한 설정 제품의 조합은 대부분의 상황에서 뛰어난 결과를 제공합니다.

이미지를 추가로 최적화해야 하는 경우 반지름이 0.2 또는 0.3으로 설정된 것부터 시작하여 선명하게 하기(언샵 마스킹) 매개 변수를 점진적으로 미세 조정합니다. 그런 다음 양을 1.75에서 최대 4까지 점진적으로 늘립니다(Photoshop의 경우 400%에 해당). 원하는 결과가 달성되었는지 확인합니다.

선명하게 하기 결과가 만족스럽지 않은 경우 반지름을 소수점 단위로 늘립니다. 소수점 증가마다 1.75로 재시작하고 점차 4로 늘립니다. 원하는 결과가 나올 때까지 이 프로세스를 반복합니다. 위의 값은 Creative Studios가 검증한 접근 방식이지만 다른 가치로 시작하고 다른 전략을 따를 수 있음을 기억하십시오. 결과가 만족스러운지 아닌지는 주관적인 문제이므로 구조화된 실험이 핵심이다.

실험할 때 워크플로를 최적화하는 데 도움이 되는 일반적인 제안은 다음과 같습니다.

* URL에서 직접 다양한 매개 변수를 실시간으로 테스트해 보십시오.
* 가장 좋은 방법은 Dynamic Media 이미지 제공 명령을 이미지 사전 설정으로 그룹화하는 것입니다. 이미지 사전 설정은 기본적으로 다음과 같은 사용자 정의 사전 설정 이름이 있는 URL 명령 매크로입니다. `$thumb_low$` 및 `&product_high$`. URL 경로의 사용자 지정 사전 설정 이름은 이러한 사전 설정을 호출합니다. 이러한 기능은 웹 사이트에서 이미지의 다양한 사용 패턴에 대한 명령 및 품질 설정을 관리하고 URL의 전체 길이를 줄이는 데 도움이 됩니다.
* Experience Manager은 또한 수집 시 이미지 선명하게 하기 적용과 같이, 이미지 품질을 조정하는 고급 방법을 제공합니다. 렌더링 결과를 조정하고 최적화하려면 [Adobe 컨설팅 서비스](https://business.adobe.com/customers/consulting-services/main.html) 는 사용자 지정된 통찰력과 모범 사례를 통해 도움이 될 수 있습니다.
