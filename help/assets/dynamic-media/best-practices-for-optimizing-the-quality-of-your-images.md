---
title: 이미지 품질 최적화 모범 사례
description: Dynamic Media을 사용하여 이미지 에셋의 품질을 최적화하는 데 도움이 되는 모범 사례에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management, Best Practices
role: User
exl-id: 2efc4a27-01d7-427f-9701-393497314402
source-git-commit: 62af768370ee0affa4003a7ae0c520ad1a065e8c
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 1%

---

# 이미지 품질 최적화 모범 사례 {#best-practices-for-optimizing-the-quality-of-your-images}

많은 요소가 허용되는 결과를 렌더링하는 데 기여하므로 이미지 품질을 최적화하는 것은 시간이 오래 걸리는 프로세스일 수 있습니다. 결과는 개인들이 이미지 품질을 다르게 인식하기 때문에 부분적으로 주관적이다. 구조화된 실험이 핵심입니다.

Adobe Experience Manager에는 이미지 및 렌더링 결과를 조정 및 최적화하기 위한 100개 이상의 Dynamic Media 이미지 게재 명령이 포함되어 있습니다. 다음 지침은 몇 가지 필수 명령과 모범 사례를 사용하여 프로세스를 간소화하고 좋은 결과를 빠르게 얻을 수 있도록 도와줍니다.

<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Dynamic Media에서 스마트 이미징 활성화 {#bp-enable-smart-imaging}

**스마트 이미징:**

* Dynamic Media에서 스마트 이미징을 활성화하면 클라이언트 브라우저 기능을 기반으로 이미지 형식, 크기 및 품질을 자동으로 최적화할 수 있습니다.
자세히 알아보시겠습니까? [스마트 이미징](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/imaging-faq)(으)로 이동합니다.
* 이러한 매개 변수를 동적으로 조정하여 이미지 전달 성능을 향상시킵니다.
* 자동 평가 도구 [스냅숏](https://snapshot.scene7.com/)을(를) 사용하여 스마트 이미징을 평가할 수 있습니다.

**이미지 형식:**

* 사용 사례에 특별히 필요한 경우가 아니면 URL에서 명시적 `fmt=webp` 또는 `fmt=avif` 명령을 사용하지 마십시오.
* Smart Imaging은 최적의 포맷을 자동으로 선택하므로 최적의 대역폭을 확보할 수 있습니다.

**기본 동작:**

* URL에 format 명령이 지정되지 않고 스마트 이미징이 활성화되지 않은 경우 Dynamic Media 이미지 게재는 기본적으로 JPEG 형식을 사용합니다.

이미지 형식에 대한 정보에 입각한 선택을 하고 스마트 이미징을 활성화하면 성능과 사용자 경험에 상당한 영향을 미칠 수 있습니다.


<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## 소스 이미지 선택 모범 사례 {#bp-select-source-image}

소스 이미지 작업에 대한 필수 고려 사항:

* **Source 이미지 형식:**
   * PNG, TIFF 또는 PSD과 같은 무손실 형식을 사용하면 압축 아티팩트 없이 이미지 품질이 높게 유지됩니다.
   * 이러한 형식은 모든 원본 데이터를 보존하므로 편집과 추가 처리에 이상적입니다.
* **Source 이미지 크기:**
   * 고해상도 이미지로 시작하면 보다 디테일과 유연성이 제공됩니다.
   * 여러 디바이스 또는 화면 해상도와 같이 서로 다른 크기로 이미지를 표시해야 하는 경우 소스 이미지의 크기가 클수록 더 나은 스케일링이 가능합니다.
   * 확대/축소를 지원하는 이미지(예: 제품 사진)의 경우 가장 긴 면에서 약 2,000픽셀 이상의 치수를 대상으로 합니다.
   * 확대/축소가 필요하지 않은 로고 또는 배너는 의도한 사용에 필요한 최대 크기로 업로드할 수 있습니다.

소스 수준에서 이러한 신중하게 선택함으로써 시각적 콘텐츠의 전반적인 품질에 크게 기여할 수 있습니다.

<!-- REMOVED TOPIC AS PER CQDOC-21594
## Best practices for image format (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG or PNG are the best choices to deliver images in good quality and with manageable size and weight.
* If no format command is supplied in the URL, Dynamic Media Image Delivery defaults to JPG for delivery.
* JPG compresses at a ratio of 10:1 and usually produces smaller image file sizes. PNG compresses at a ratio of about 2:1, except when images contain a white background. Typically though, PNG file sizes are larger than JPG files.
* JPG uses lossy compression, meaning that picture elements (pixels) are dropped during compression. PNG on the other hand uses lossless compression.
* JPG often compresses photographic images with better fidelity than synthetic images with sharp edges and contrast.
* If your images contain transparency, use PNG because JPG does not support transparency.

As a best practice for image format, start with the most common setting `&fmt=JPG`. -->

## 이미지 크기에 대한 우수 사례 {#best-practices-for-image-size}

이미지 크기를 동적으로 줄이는 것은 가장 일반적인 작업 중 하나입니다. 이것은 크기를 지정하는 것과, 선택적으로, 이미지를 다운스케일링하기 위해 사용되는 다운샘플링 모드를 지정하는 것을 포함한다.

* 이미지 크기를 조정할 때 가장 좋은 방법은 `&wid=<value>`과(와) `&hei=<value>,` 또는 `&hei=<value>`을(를) 사용하는 것입니다. 이러한 매개 변수는 종횡비에 따라 이미지 폭을 자동으로 설정합니다.
* `&resMode=<value>`다운샘플링에 사용되는 알고리즘을 제어합니다. `&resMode=sharp2`(으)로 시작합니다. 이 값은 최상의 이미지 품질을 제공합니다. 다운샘플링 `value =bilin`을(를) 사용하는 속도가 더 빠르지만 아티팩트의 앨리어싱을 가져오는 경우가 많습니다.

이미지 크기 조정에 대한 우수 사례로 `&wid=<value>&hei=<value>&resMode=sharp2` 또는 `&hei=<value>&resMode=sharp2`을(를) 사용하십시오.

## 이미지 선명하게 하기 우수 사례 {#best-practices-for-image-sharpening}

이미지 선명하게 하기는 웹 사이트에서 이미지를 제어하는 가장 복잡한 측면이며 많은 실수가 발생하는 곳입니다. 다음 유용한 리소스를 참조하여 Experience Manager에서 선명하게 하기 및 언샵 마스킹이 작동하는 방식에 대해 자세히 알아보십시오.

* 모범 사례 백서 [Adobe Dynamic Media Classic 이미지 품질 및 선명하게 하기 모범 사례](/help/assets/dynamic-media/assets/sharpening_images.pdf)는 Experience Manager에도 적용됩니다.

* [Experience Manager에서 이미지 선명하게 하기 사용 - Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media)을 시청하십시오.

Experience Manager을 사용하면 수집, 게재 또는 둘 다에 대해 이미지를 선명하게 할 수 있습니다. 그러나 일반적으로 이미지를 선명하게 하는 데는 한 가지 방법이나 다른 방법만 사용하는 것이 가장 좋지만 둘 다 사용하지 않는 것이 좋습니다. URL에서 전달 시 이미지를 선명하게 하면 일반적으로 최상의 결과를 얻을 수 있습니다.

사용할 수 있는 이미지 선명하게 하기 방법에는 두 가지가 있습니다.

* 단순 선명하게 하기( `&op_sharpen`) - Photoshop에서 사용되는 선명하게 필터와 유사하게, 단순 선명하게 하기는 동적 크기 조정 후 이미지의 최종 보기에 기본 선명하게 하기를 적용합니다. 그러나 이 메서드는 사용자가 구성할 수 없습니다. 필요한 경우가 아니면 `&op_sharpen`을(를) 사용하지 않는 것이 좋습니다.
* 언샵 마스킹(`&op_USM`) - 언샵 마스킹은 업계 표준 선명하게 하기 필터입니다. 가장 좋은 방법은 아래 지침에 따라 선명하지 않은 마스킹으로 이미지를 선명하게 하는 것입니다. 언샵 마스킹을 사용하면 다음 세 가지 매개 변수를 제어할 수 있습니다.

   * `&op_sharpen=`양, 반경, 임계값

      * **[!UICONTROL 금액]**(0-5, 효과의 강도)
      * **[!UICONTROL radius]** (0-250, 선명하게 표시된 개체 주위에 그려진 &quot;선명하게 하기 선&quot;의 너비(픽셀 단위)입니다.)

     매개변수 반경과 양은 서로 영향을 받습니다. 감소된 반경은 양을 증가시킴으로써 보상될 수 있다. [반경]을 사용하면 값이 낮을수록 가장자리 픽셀만 선명하게 되고 값이 높을수록 넓은 폭의 픽셀이 선명하게 되므로 더 세밀하게 제어할 수 있습니다.

      * **[!UICONTROL 임계값]**(0-255, 효과 민감도)

     이 매개 변수는 가장자리 픽셀로 간주되기 전에 선명해진 픽셀이 주변 영역과 얼마나 달라야 하는지 결정하고 필터가 선명하게 합니다. **[!UICONTROL threshold]** 매개 변수를 사용하면 피부 색조와 같이 비슷한 색상의 영역을 너무 선명하게 하지 않도록 할 수 있습니다. 예를 들어, 임계값 12는 피부 색조 밝기의 미세한 변화를 무시하여 &quot;노이즈&quot;를 추가하는 것을 피하는 동시에 속눈썹이 피부와 만나는 지점과 같은 고대비 영역에 가장자리 대비를 추가합니다.

     필터에 사용하는 모범 사례를 포함하여 이러한 세 매개 변수를 설정하는 방법에 대한 자세한 내용은 다음 리소스를 참조하십시오.

      * 모범 사례 백서 [Adobe Dynamic Media Classic 이미지 품질 및 선명하게 하기 모범 사례](/help/assets/dynamic-media/assets/sharpening_images.pdf)는 Experience Manager에도 적용됩니다.

      * [Experience Manager에서 이미지 선명하게 하기 사용 - Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media)을 시청하십시오.

      * Experience Manager을 사용하면 네 번째 매개 변수인 모노크롬(0,1)을 제어할 수도 있습니다. 이 매개 변수는 값 0을 사용하여 각 색상 구성 요소에 언샵 마스킹을 별도로 적용할지 또는 값 1을 사용하여 이미지 밝기/강도에 적용할지 여부를 결정합니다.

언샵 마스크 반경 매개 변수로 시작하는 것이 좋습니다. 다음으로 시작할 수 있는 반경 설정은 다음과 같습니다.

* **[!UICONTROL 웹 사이트]**: 0.2-0.3픽셀
* **[!UICONTROL 사진 인쇄(250-300ppi)]**: 0.3-0.5픽셀
* **[!UICONTROL 오프셋 인쇄(266-300ppi)]**: 0.7-1.0픽셀
* **[!UICONTROL 캔버스 인쇄(150ppi)]**: 1.5-2.0픽셀

1.75에서 4로 서서히 늘립니다. 선명하게 하기가 여전히 원하는 방식이 아닌 경우 반지름을 소수점 단위로 늘리고 1.75에서 4로 다시 실행합니다. 필요에 따라 반복합니다.

모노크롬 매개 변수 설정을 0으로 둡니다.

### JPEF 압축 모범 사례(`&qlt=`) {#best-practices-for-jpef-compression-qlt}

* 이 매개 변수는 JPG 인코딩 품질을 제어합니다. 값이 높을수록 이미지 품질은 높지만 파일 크기는 커집니다. 또는 값이 낮을수록 이미지 품질은 낮지만 파일 크기는 작아집니다. 이 매개 변수의 범위는 0~100입니다.
* 품질을 최적화하려면 매개 변수 값을 100으로 설정하지 마십시오. 90 또는 95와 100 사이의 차이는 거의 감지할 수 없다. 그러나 100은 불필요하게 이미지 파일의 크기를 늘립니다. 따라서 품질을 최적화하지만 이미지 파일이 너무 커지지 않도록 하려면 `qlt= value`을(를) 90 또는 95로 설정하십시오.
* 이미지 파일 크기는 작지만 이미지 품질을 허용 가능한 수준으로 유지하려면 `qlt= value`을(를) 80으로 설정합니다. 70 내지 75 미만의 값은 상당한 이미지 품질 저하를 초래한다.
* 가장 좋은 방법은 중간에 머무르려면 `qlt= value`을(를) 85로 설정하여 중간에 머무르는 것입니다.
* `qlt=`에서 크로마 플래그 사용

   * `qlt=` 매개 변수에는 값 `,1`을(를) 사용하여 RGB 색도 다운샘플링을 켜거나 값 `,0`을(를) 사용하여 끌 수 있는 두 번째 설정이 있습니다.
   * 단순하게 유지하려면 RGB 색도 다운샘플링을 끄기(`,0`)로 시작하십시오. 이 설정을 사용하면 일반적으로 이미지 품질이 향상됩니다. 특히 가장자리가 선명하고 대비가 많은 합성 이미지의 경우 더욱 그렇습니다.

JPG 압축에 대한 우수 사례로 `&qlt=85,0`을(를) 사용하십시오.

## JPEG 크기 조정(`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}에 대한 모범 사례

`jpegSize` 매개 변수는 메모리가 제한된 장치에 전달할 때 이미지가 특정 크기를 초과하지 않도록 하려는 경우에 유용합니다.

* 이 매개 변수는 KB(`jpegSize=&lt;size_in_kilobytes&gt;`) 단위로 설정되어 있습니다. 이미지 게재에 허용되는 최대 크기를 정의합니다.
* `&jpegSize=`이(가) JPG 압축 매개 변수 `&qlt=`과(와) 상호 작용합니다. 지정된 JPG 압축 매개 변수(`&qlt=`)의 JPG 응답이 jpegSize 값을 초과하지 않으면 정의된 대로 이미지가 `&qlt=`(으)로 반환됩니다. 그렇지 않으면 이미지가 최대 허용 크기에 맞출 때까지 `&qlt=`이(가) 점차적으로 줄어듭니다. 또는 시스템이 적합할 수 없다고 판단하고 오류를 반환할 때까지.

메모리가 제한된 장치에 JPG 이미지를 전달하는 경우에는 `&jpegSize=`을(를) 설정하고 `&qlt=` 매개 변수를 추가하는 것이 좋습니다.

## 모범 사례 요약 {#best-practices-summary}

높은 이미지 품질과 작은 파일 크기를 달성하려면 다음 매개 변수 조합으로 시작하는 것이 좋습니다.

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

이러한 설정의 조합은 대부분의 상황에서 탁월한 결과를 생성합니다.

이미지를 추가로 최적화해야 하는 경우 반지름이 0.2 또는 0.3으로 설정된 것부터 시작하여 선명하게 하기(언샵 마스킹) 매개 변수를 점진적으로 미세 조정합니다. 그런 다음 양을 1.75에서 최대 4까지 점진적으로 늘립니다(Photoshop의 경우 400%에 해당). 원하는 결과가 달성되었는지 확인합니다.

선명하게 하기 결과가 만족스럽지 않은 경우 반지름을 소수점 단위로 늘립니다. 소수점 증가마다 1.75로 재시작하고 점차 4로 늘립니다. 원하는 결과가 나올 때까지 이 프로세스를 반복합니다. 위의 값은 Creative Studios가 검증한 접근 방식이지만 다른 가치로 시작하고 다른 전략을 따를 수 있음을 기억하십시오. 결과가 만족스러운지 아닌지는 주관적인 문제이므로 구조화된 실험이 핵심이다.

실험할 때 워크플로를 최적화하는 데 도움이 되는 일반적인 제안은 다음과 같습니다.

* URL에서 직접 다양한 매개 변수를 실시간으로 테스트해 보십시오.
* 가장 좋은 방법은 Dynamic Media 이미지 제공 명령을 이미지 사전 설정으로 그룹화하는 것입니다. 이미지 사전 설정은 기본적으로 `$thumb_low$` 및 `&product_high$`과(와) 같은 사용자 지정 사전 설정 이름이 있는 URL 명령 매크로입니다. URL 경로의 사용자 지정 사전 설정 이름은 이러한 사전 설정을 호출합니다. 이러한 기능은 웹 사이트에서 이미지의 다양한 사용 패턴에 대한 명령 및 품질 설정을 관리하고 URL의 전체 길이를 줄이는 데 도움이 됩니다.
* Experience Manager은 또한 수집 시 이미지 선명하게 하기 적용과 같이, 이미지 품질을 조정하는 고급 방법을 제공합니다. 렌더링 결과를 조정하고 최적화하기 위해 [Adobe의 컨설팅 서비스](https://business.adobe.com/customers/consulting-services/main.html)를 통해 사용자 지정된 통찰력과 모범 사례를 확인할 수 있습니다.
