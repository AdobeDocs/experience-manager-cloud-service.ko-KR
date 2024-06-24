---
title: Dynamic Media 모범 사례
description: Dynamic Media의 이미지 및 비디오 작업 모범 사례에 대해 알아봅니다.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Adaptive Streaming, Best Practices, Smart Imaging, Image Profiles, Rulesets, Viewers, Smart Crop, SEO Optimization, Publishing, Video, Renditions, Asset Management
role: User, Admin
mini-toc-levels: 4
exl-id: 39e491bb-367d-4c72-b4ca-aab38d513ac5
source-git-commit: de1116ee39024d30e14838f8b36f9ab087a45f85
workflow-type: tm+mt
source-wordcount: '3571'
ht-degree: 0%

---

# Dynamic Media 모범 사례{#about-dm-best-practices}

<!--**Organizations today must connect with their customers through an ever-growing array of channels and devices.** The customer experience spans physical stores, websites, mobile apps, social media, email, and e-commerce platforms. This diversity requires organizations to create many more versions of each piece of content. Personalization adds complexity by increasing the number of variations needed for each item. Despite budget constraints for content creation, there's still a need to produce more campaigns in the same timeframe, on a global scale. AEM Dynamic Media offers a comprehensive set of tools to meet these challenges, providing consistent, personalized, high-performance, and optimized brand experiences across all channels and devices. 

Key Features of AEM Dynamic Media:

* **Single File Approach:** Save on storage costs by storing just one master file. AEM Dynamic Media generates all size variations and visual effects on-demand, at the time of delivery, eliminating workflow complexity and last-minute creative changes.
* **Global Reach:** With Smart Imaging, images are automatically optimized during delivery, significantly reducing file size and page weight without sacrificing visual quality. This optimization is tailored for network bandwidth and device pixel ratio.
* **AI-Powered Efficiency:** Smart Crop uses AI to automate the cropping of images and videos, focusing on points of interest. This feature saves countless hours of manual editing and is designed for large-scale enterprise production.
* **Video Made Simple:** Upload a master video file and AEM Dynamic Media will adaptively stream it in multiple languages and with descriptive audio, ensuring a broad reach.
* **Customizable Experience Viewer:** Select, customize, and brand the experience viewers for images and videos with ease. These viewers can be seamlessly integrated into any digital experience.
* **Support for Emerging Formats:** AEM Dynamic Media is also your solution for delivering immersive 3D and panoramic experiences.

In the accompanying guide, you'll find a comprehensive list of best practices for maximizing the benefits of AEM Dynamic Media. As you embark on your Dynamic Media journey, make sure to consult these expert recommendations and resources.

Stage Business Problem Best Practice Recommendation: This section will outline specific business challenges and provide targeted best practices and recommendations to address them effectively. -->

조직에서는 사용자와 소통하기 위한 채널 및 장치가 폭증하고 있습니다. 고객 여정은 물리적 상점, 웹, 모바일, 소셜 미디어, 이메일 및 상거래를 포괄합니다. 이러한 요구 사항을 충족하기 위해 Adobe Experience Manager(AEM)의 Dynamic Media은 포괄적인 솔루션을 제공합니다. 자산 전달을 최적화하고 개인화를 처리하며 채널 및 장치 간에 일관되고 성능이 뛰어나며 브랜드 중심 경험을 보장합니다.

Dynamic Media의 몇 가지 주요 개념에는 다음이 포함됩니다.

* **단일 파일 방식:** Dynamic Media을 사용하면 하나의 기본 소스 파일을 저장할 수 있으며, 모든 크기 변형과 시각 효과는 게재 시 동적으로 생성되고 최적화됩니다. 이 방법을 사용하면 스토리지 비용을 절감하고 워크플로우의 복잡성을 줄일 수 있습니다.
* **실제로 글로벌:** 컨텐츠 전달 중에 적용된 스마트 이미징은 시각적 품질을 손상시키지 않고 이미지 크기와 페이지 무게를 크게 줄입니다. 네트워크 대역폭 및 장치 픽셀 비율에 최적화되어 있습니다.
* **AI 기반:** AI 기반 기능인 스마트 자르기는 이미지 및 비디오 관심 영역 자르기를 자동화합니다. 수작업으로 인한 부담을 줄이고 효율적으로 확장할 수 있습니다.
* **간편한 비디오:** 기본 소스 비디오를 Dynamic Media에 업로드하고 설명 오디오를 사용하여 여러 언어에서 적응적으로 스트리밍합니다.
* **경험 뷰어 라이브러리:** 이미지 및 비디오에 대한 경험 뷰어를 사용자 지정하고 브랜드화할 수 있습니다. 이러한 뷰어는 디지털 경험에 원활하게 통합됩니다.
* **새로운 형식 지원:** Dynamic Media을 사용하면 3D 및 파노라마 경험을 전달할 수 있습니다.

탐색 시 [Dynamic Media 여정](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1)를 통해 아래 통합된 모범 사례 목록을 검토하면 해당 기능을 최대한 활용하는 데 도움이 될 수 있습니다. 이러한 Dynamic Media 모범 사례를 특정 컨텍스트 및 프로젝트 요구 사항에 맞게 조정하면 채널 및 디바이스 전반에 걸쳐 경험을 최적화할 수 있습니다.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>이 문서의 Dynamic Media 우수 사례는 Dynamic Media의 새로운 기술이 등장함에 따라 시간이 지남에 따라 발전할 수 있습니다. 아래 정보는 최신 버전의 Dynamic Media에 대한 최신 정보입니다.


## Dynamic Media에 자산 수집

**비즈니스 사례:** *대량의 에셋을 효율적으로 관리하고 승인된 관련 콘텐츠만 최종 사용자에게 전달되도록 합니다.*

대량의 자산을 효율적으로 관리할 수 있습니다. Dynamic Media의 **선택적 동기화** 및 **선택적 게시** 기능.

* **선택적 동기화:**
Dynamic Media과 동기화할 자산을 선택할 수 있는 사전 예방 기능입니다. 예를 들어 최종 승인을 받은 에셋이 포함된 폴더만 동기화하기로 결정할 수 있습니다. 이 워크플로우는 고객에게 전달하기 위해 준비되는 자산을 제어하는 데 도움이 됩니다.

* **선택적 게시:**
자산을 동기화하면 선택적 게시를 통해 고객에게 표시되는 자산을 제어할 수 있습니다. 즉, 채널을 통해 실제로 전달되는 승인된 에셋을 관리하여 고객이 가장 연관성 높은 최적의 콘텐츠만 볼 수 있도록 할 수 있습니다.

이 두 가지 모범 사례는 리치 미디어 콘텐츠에 대한 제어, 거버넌스 및 생산성을 개선하는 데 도움이 됩니다.

자세히 알아보시겠습니까? 다음으로 이동 [Dynamic Media의 폴더 수준에서 선택적 게시 구성](/help/assets/dynamic-media/selective-publishing.md).


## 게재를 위한 자산 준비

### 에셋 구성

**비즈니스 사례:** *자산을 효율적으로 구성하여 워크플로우를 간소화합니다.*

워크플로우를 간소화하는 효율적인 자산 구성을 위해 다음 모범 사례 중 하나 이상을 사용하십시오.

* **폴더에서 에셋 구성:**
에셋을 구성하려면 컴퓨터의 파일 구성과 마찬가지로 에셋을 폴더로 분류하는 것이 효과적입니다. 이러한 폴더 내의 적절한 이름 지정, 하위 폴더 구조 및 파일 관리는 효율적인 에셋 처리에 중요합니다. 체계적인 이름 지정 규칙 및 메타데이터 사례를 구현하면 디지털 에셋 저장소의 유틸리티를 최대화할 수 있습니다.
자세히 알아보시겠습니까? 다음으로 이동 [폴더에서 에셋 구성](/help/assets/organize-assets.md#organize-using-folders).
* **태그를 사용하여 에셋 구성:**
자산에 태그를 지정하면 검색 가능성, 컬렉션 만들기 및 검색 순위가 향상됩니다. Adobe Sensei의 AI는 정확한 태깅을 위해 자체 학습 알고리즘을 사용하여 빠른 자산 검색을 가능하게 합니다. 또한 Adobe Sensei은 관련 태그(사용자 지정 태그 포함)를 자산에 인식 및 할당하여 자동 설명 태깅을 통해 자산 관리를 간소화합니다.
자세히 알아보시겠습니까? 다음으로 이동 [태그를 사용하여 에셋 구성](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **자산을 컬렉션으로 구성:**
Dynamic Media과 Experience Manager Assets을 함께 사용하면 에셋 컬렉션을 효율적으로 생성, 편집 및 공유할 수 있습니다. 정적 목록 및 동적 검색 기반 컴파일을 포함하여 다양한 컬렉션 유형을 설정할 수 있습니다. 이러한 컬렉션 유형은 사용자 정의 가능한 액세스 및 편집 권한을 사용하여 다양한 위치에서 공유할 수 있습니다.
자세히 알아보시겠습니까? 다음으로 이동 [자산을 컬렉션으로 구성](/help/assets/manage-collections.md).
* **프로필을 사용하여 에셋 구성:**
처리 프로필은 지정된 폴더의 자산 처리를 자동화하여 조직을 간소화합니다. 메타데이터, 파일 이름 및 폴더 구조를 표준화하면 디지털 자산 컬렉션이 확장될 때 이러한 프로필을 일관되고 정확하게 적용할 수 있습니다.
자세히 알아보시겠습니까? 다음으로 이동 [프로필을 사용하여 에셋 구성](/help/assets/organize-assets.md#organize-to-use-profiles).



### 이미지 품질 최적화

**비즈니스 사례:** *Dynamic Media에서 좋은 품질의 이미지를 얻을 수 있습니다.*

이미지 품질을 높이기 위해서는 다양한 요인에 대한 세심한 고려가 필요하다. 시간이 많이 소요되는 프로세스일 수 있습니다. 그러나 바람직한 결과를 얻는 데 도움이 되는 몇 가지 시도되고 참된 관행이 있습니다. 이러한 모범 사례 중 일부에는 최적의 이미지 크기 조정, 이미지 선명하게 하기 및 사용할 최상의 이미지 형식을 얻는 방법이 포함됩니다.

자세히 알아보시겠습니까? 다음으로 이동 [이미지 품질 최적화 우수 사례](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

화질 인식은 사람마다 다르기 때문에 바람직한 결과를 얻기 위해서는 때로는 실험에 대한 체계적인 접근이 필수적이다. Adobe Experience Manager은 이미지 향상을 위해 100개 이상의 Dynamic Media 명령으로 이 프로세스를 지원합니다.

자세히 알아보시겠습니까? 시청 [Dynamic Media 스냅샷](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3분 17초).

이러한 다양한 명령이 이미지 품질에 미치는 영향을 평가하기 위해 이미지를 Dynamic Media에 업로드하고, 지정된 URL에서 도구 인터페이스를 사용한 다음, 시도하려는 명령을 적용할 수 있습니다.

먹어볼래? 시작 [Dynamic Media 스냅샷](https://snapshot.scene7.com/)

### 이미지에 적용된 스타일을 표준화합니다.

**비즈니스 사례:** *내 이미지 에셋에 적용되는 스타일 및 변형을 효율적으로 표준화합니다.*

Dynamic Media에서 이미지 사전 설정을 정기적으로 사용하면 이미지 크기, 형식 및 속성을 일관되고 동적으로 조정할 수 있습니다. 이미지 사전 설정을 매크로로 생각해 보십시오. 이는 크기 조정 및 서식을 지정하는 명명된 명령 집합입니다. 예를 들어, 사이트에 데스크탑 및 모바일에 대한 특정 압축을 사용하여 다양한 크기와 형식의 제품 이미지가 필요한 경우 이미지 사전 설정은 이 프로세스를 효율적으로 자동화합니다.

먹어볼래? 다음으로 이동 [자산 렌더링용 이미지 사전 설정 만들기의 기본 사항](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### 이미지 및 비디오의 포커스 및 프레임 조정

**비즈니스 사례:** *내 이미지 또는 비디오의 주요 관심 영역이 여러 장치에서 포커스에 유지되는지 확인합니다.*

스마트 자르기는 Adobe의 AI 및 머신 러닝 프레임워크인 Adobe Sensei을 사용하여 이미지와 비디오 자르기를 자동화하는 Dynamic Media의 기능입니다. 이미지나 동영상의 주요 주제나 관심 지점을 지능적으로 탐지하고 집중한다. 이 인텔리전스는 데스크톱 컴퓨터 및 모바일 장치에서 다양한 화면 크기에 걸쳐 초점이 유지되도록 보장합니다.

가장 좋은 방법은 스마트 자르기로 이미지 프로필을 만드는 것입니다. 프로필에서 다양한 화면 크기를 정의하고 Adobe Sensei에서 나머지 작업을 수행하도록 하여 이미지와 비디오가 항상 뷰어의 장치에 최적화되도록 할 수 있습니다.

자세히 알아보시겠습니까? 시청 [AEM Assets Dynamic Media에서 스마트 자르기 사용](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6분 35초) 및 [비디오용 Dynamic Media 스마트 자르기 사용](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6분, 22초).

### SEO 등급 개선

**비즈니스 사례:** *향상된 SEO 등급을 얻도록 Dynamic Media을 구성합니다.*

이미지가 전체 SEO 전략에 효과적으로 기여하도록 하려면 다음 권장 사항을 정기적으로 사용하십시오.

* **의미 있는 이미지 파일 이름:**
이미지 내용을 반영하는 수사적 파일 이름을 사용합니다. 예:
   * `myCompany-Silver-Wrist-Watch` 사용
   * *피함* `myCompany_Silver_Wrist_Watch` 또는 `myCompanySilverWristWatch`

  이렇게 하면 검색 엔진이 이미지 컨텍스트를 이해하고 SEO를 개선하는 데 도움이 됩니다. Google에서는 파일 이름에서 밑줄 또는 공백보다 하이픈을 선호합니다. 또한 파일 이름에 단어를 연결하지 마십시오.
* **사용자 정의 도메인:**
브랜드 인지도와 신뢰를 강화하기 위해 회사 또는 브랜드 이름을 포함하는 사용자 정의 도메인을 구현합니다. 예:
   * `http://images.mycompany.com/is/image/companyname/` 사용
   * *피함* `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`
* **SEO 친화적인 폴더 구조:**
다음과 같이 더 나은 색인화를 위해 회사 이름이나 브랜드를 포함하는 폴더 구조로 이미지를 구성합니다. `http://images.mycompany.com/is/image/companyname/`.
* **Dynamic Media 규칙 세트:**
다양한 요소를 기반으로 URL을 조건부로 변환하여 SEO 및 사용자 경험을 향상시키는 방법을 알아봅니다.
자세히 알아보시겠습니까? 다음으로 이동 [규칙 세트를 사용하여 URL 변환](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md).
* **스마트 이미징 및 스마트 자르기:**
Dynamic Media의 스마트 이미징 및 스마트 자르기 기능을 사용하여 최적화되고 반응형 이미지를 제공할 수 있습니다. 이렇게 하면 페이지 로드 시간이 향상될 뿐만 아니라 SEO 등급에 긍정적인 영향을 줍니다.
자세히 알아보시겠습니까? 다음으로 이동 [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md), 또는 시계 [AEM Assets Dynamic Media에서 스마트 자르기 사용](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6분 35초).

이러한 모범 사례는 Google의 이미지 SEO 모범 사례와 잘 일치합니다. 이러한 사례는 적절한 이름 지정 규칙, 구조화된 데이터 및 최적화된 이미지 제공을 통해 검색 엔진에 컨텍스트와 명확성을 제공하는 것의 중요성을 강조합니다.

자세히 알아보시겠습니까? 다음으로 이동 [Google을 위한 URL 구조 우수 사례](https://developers.google.com/search/docs/crawling-indexing/url-structure) 및 [Google 이미지 SEO 모범 사례](https://developers.google.com/search/docs/appearance/google-images)


### 명령을 사용하여 이미지를 동적으로 향상시키고 시각적 효과를 만듭니다.

**비즈니스 사례:** *이미지에 다양한 시각적 효과를 적용합니다.*

Dynamic Media은 여러 정적 에셋을 사용하지 않고도 이미지를 개선하고 시각적 효과를 동적으로 만들기 위한 명령 세트를 제공합니다. 다음은 이러한 프로세스 중 몇 가지에 대한 간략한 설명과 몇 가지 안내할 예입니다.

#### 소스 이미지 내의 효과

| 작업 | 할 일 |
| --- | --- |
| **원본 이미지 업로드 및 게시** | · Dynamic Media에 원본 이미지를 업로드하여 시작합니다.<br>· URL을 통해 게시되고 액세스할 수 있는지 확인하십시오.<br>· 이 예에서는 흰색 배경의 시계 스톡 이미지(&quot;Image X&quot;라고 함)가 Dynamic Media에 업로드됩니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer) |
| **마스크 만들기** | · 주제(효과를 적용할 영역)와 배경(변경할 영역)을 정의하는 마스크를 개발합니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)<br>· 마스크는 일반적으로 회색 음영 이미지이며, 흰색은 피사체를 나타내고 검은색은 배경을 나타냅니다. Adobe Photoshop과 같은 도구를 사용하여 마스크를 만들 수 있습니다.<br>자세히 알아보시겠습니까? 다음으로 이동 [Photoshop에서 빠른 마스크 만들기 및 편집](https://helpx.adobe.com/in/photoshop/using/create-temporary-quick-mask.html).<br>· &quot;Image X&quot;의 경우 향상시키고자 하는 대상을 정확하게 윤곽을 나타내는 마스크를 만듭니다. 예를 들어, 사람, 객체 등이 있습니다. |
| **효과에 Dynamic Media URL 명령 적용** | 마스크가 있으면 URL 명령을 사용하여 그림자와 같은 효과를 적용하거나 배경색을 &quot;이미지 X&quot;로 변경합니다. 다음은 두 가지 예입니다.<br><br> · **그림자 효과:**<br>&#x200B;주체의 경계를 따라 그림자 효과를 추가하려면 다음과 같이 URL을 편집합니다.<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25)<br>이 URL에서 `$shadow$` 매개 변수는 그림자 효과를 만들고, `color=0,0,0` 그림자 색상을 검정으로 설정합니다.<br>· **배경색 변경:**<br>&#x200B;배경색을 변경하려면 다른 배경색 값이 있는 URL을 사용하십시오.<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0)<br> 이 예에서는 `color=255,255,0` 배경색을 노란색으로 설정합니다. 시각적 효과를 위해 배경을 특정 색상으로 편집합니다. |

#### 이미지 테두리 추가

Dynamic Media을 사용하면 URL을 통해 직접 이미지를 조작할 수 있으므로 동적 디지털 경험을 만들 수 있는 강력한 도구가 됩니다. 다음은 몇 가지 예입니다. 다음 원본 이미지 URL로 시작하겠습니다. [https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| 작업 | 할 일 |
| --- | --- |
| **흰색 테두리** | 흰색 테두리를 추가하려면 다음 URL을 사용하십시오.<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10)<br>이 URL에서 `extend=10,10,10,10` 매개 변수는 모든 면에서 10픽셀의 테두리 크기를 지정합니다. |
| **흰색 테두리를 따라 흐림** | 흰색 테두리를 따라 흐림 효과를 추가하려면 다음과 같이 URL을 편집할 수 있습니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0)<br>이 URL에서 `effect=-1` 매개 변수는 흐림 효과를 적용하고 `op_blur=60` 흐림 효과 강도를 제어합니다. |
| **외부 경계를 따라 그림자 효과** | 외부 경계를 따라 그림자 효과를 추가하려면 다음 URL을 사용합니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0)<br>다음 `$shadow$` 매개 변수는 그림자 효과를 만들고, `color=0,0,0` 그림자 색상을 검정으로 설정합니다. |

원하는 시각적 효과를 얻기 위해 이러한 URL을 자유롭게 실험해 보십시오.

#### 이미지 오버레이 만들기

기존 이미지에 로고나 아이콘을 중첩하려는 경우, Dynamic Media에서 URL 명령을 사용하여 이를 쉽게 수행할 수 있습니다. 단계를 분류해 봅시다.

| 단계 | 할 일 |
| --- | --- |
| **기본 이미지 업로드 및 게시** | 먼저 로고나 아이콘을 겹칠 기본 이미지를 업로드하고 게시합니다. 모든 이미지를 기반으로 사용할 수 있습니다.<br>예를 들어 다음은 기본 이미지입니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **로고 또는 아이콘 이미지 업로드 및 게시** | 그런 다음 기본 이미지 위에 겹칠 이미지를 업로드하고 게시합니다. 이 이미지는 오버레이할 로고 또는 아이콘이 있는 투명 PNG여야 합니다.<br>다음은 겹쳐질 투명 효과가 있는 별 오브젝트의 투명 PNG 이미지입니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/decorate-star](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **Dynamic Media URL 적용** | 이제 기본 이미지와 로고 또는 아이콘 이미지를 결합하는 Dynamic Media URL을 만듭니다. URL 명령을 사용하여 이 효과를 얻을 수 있습니다.<br>URL 구조는 다음과 같습니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png)<br>위치<br>· `hotspotRetailBaseImage` 는 기본 이미지입니다.<br>· `starxp` 는 로고/아이콘 이미지입니다.<br>· `layer=1` 로고나 아이콘이 기본 이미지 위에 겹치도록 지정합니다.<br>· `scale=1.25` 로고/아이콘의 크기를 조정합니다.<br>· `posN=0.33,-.25` 기본 이미지를 기준으로 로고/아이콘의 위치를 결정합니다.<br>· `fmt=png` 는 출력이 PNG 형식인지 확인합니다. |

자세한 내용 다음으로 이동 [src](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src) 에 대한 자세한 내용은 `src` 명령 및 기타 Dynamic Media URL 명령.


#### 홍보 텍스트 오버레이

다음은 HTML 및 CSS를 사용하여 홍보용 텍스트 메시지를 이미지에 오버레이하는 단계입니다.

| 단계 | 할 일 |
| --- | --- |
| **기본 이미지 업로드 및 게시** | 먼저 텍스트를 겹칠 기본 이미지를 업로드하고 게시합니다. 원하는 이미지를 사용할 수 있습니다. 다음은 샘플 기본 이미지입니다.<br>[https://s7g2.scene7.com/is/image/genaibeta/leather-sofa](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa)<br> |
| **Dynamic Media 텍스트 연산자 적용** | Dynamic Media을 사용하여 텍스트 연산자를 적용하여 다이내믹 텍스트를 이미지에 직접 오버레이할 수 있습니다. 다음 샘플 URL은 이 기능을 보여 줍니다.<br>[https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fontbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF333&amp;wid=600&amp;hei=600](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fontbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF333&amp;wid=600&amp;hei=600) |

#### 다양한 사용 사례를 위한 크기 조정 및 자르기

##### 이미지 크기 조정 기본 사항

이미지 크기 조정에는 이미지의 치수, 해상도 및 파일 크기가 변경됩니다. 다음은 고려해야 할 몇 가지 주요 사항입니다.

* **픽셀 구성:**
디지털 이미지는 픽셀이라는 작은 점으로 구성됩니다. 이미지가 만들어지면 특정 픽셀 수가 됩니다. 크기 조정에는 이미지의 크기, 해상도 및 파일 크기를 변경하기 위해 픽셀을 추가하거나 빼는 작업이 포함됩니다.
* **종횡비:**
가로세로비(가로와 세로의 관계)를 유지하는 것은 왜곡을 방지하는 데 중요합니다. 이미지를 더 크게(업스케일링) 또는 더 작게(다운스케일링) 만드는지에 관계없이, 종횡비를 유지하면 시각적 일관성이 보장됩니다.
* **품질 고려 사항:**
크기를 조정하면 이미지 품질에 영향을 줄 수 있습니다. 과도한 업스케일링은 픽셀화를 초래할 수 있으므로 피하십시오. 대신 이미지를 더 큰 크기와 해상도로 재현하는 것이 좋습니다. 더 작은 이미지의 경우 적절한 도구를 사용하여 해상도를 유지합니다.

##### 자르기 대 크기 조정

자르기 및 크기 조정은 썸네일, 제품 표시 이미지 또는 배너 만들기에 관계없이 다양한 사용 사례에 맞게 이미지를 변환할 수 있는 Dynamic Media의 기술입니다.

* **자르기:**
이미지의 일부를 제거하여 컴포지션과 프레이밍을 변경합니다. 전체 차원을 변경하지 않고 특정 영역에 중점을 둡니다.
* **크기 조정:**
종횡비를 유지하면서 전체 이미지의 크기, 해상도 및 파일 크기를 조정합니다.

다음 거실 이미지가 포함된 사용 사례를 살펴보겠습니다.

* **원본 거실 이미지:**
  [https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **썸네일(200px x 200px):**
빠른 로드 또는 표시에 적합한 더 작은 버전.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop)
* **자르기 썸네일(200px x 200px):**
소파 구역에 집중하기 위해 짧게 깎았다.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **제품 디스플레이 이미지(800px x 600px):**
소파를 표시하기 위해 자르고 크기를 조정합니다.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **배너(1720px x 820px):**
공간을 강조하는 원본 이미지에서 파생됩니다.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop)

특정 요구 사항에 맞게 이러한 변형을 자유롭게 탐색할 수 있습니다.
URL 내에서 사용할 수 있는 명령에 대해 자세히 알아보시겠습니까? 다음으로 이동 [명령 참조](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### 내 웹 사이트에 대한 비디오 게시

**비즈니스 사례:** *마케팅 사이트에 대한 비디오를 빠르게 게시합니다.*

* **비디오 프로필 선택:**
먼저 Dynamic Media에서 적절한 비디오 프로필을 선택해야 합니다. 다음을 선택할 수 있습니다. *응용 비디오 인코딩* AEM Assets의 비디오 프로필에서 사용할 수 있는 프로필입니다. 이러한 사전 정의된 인코딩 설정을 통해 다양한 장치 및 대역폭 조건에서 비디오가 재생되도록 최적화됩니다. 또는 고유한 응용 비디오 프로필을 만들 수 있습니다.
* **프로필 할당:**
선택한 비디오 프로필을 비디오가 업로드될 폴더에 할당합니다. 이 단계에서는 업로드 프로세스 중에 올바른 인코딩 설정이 적용되도록 합니다.
* **원본 비디오 업로드:**
원본 비디오 파일을 업로드합니다. 좋은 품질의 고해상도 비디오인지 확인하십시오. 소스 비디오가 좋을수록 최종 결과도 좋습니다.
* **미리 보기 및 게시:**
모든 것이 예상대로 보이도록 비디오를 미리 봅니다. 만족스러우면 게시하십시오. 이 단계에서는 대상자가 비디오에 액세스할 수 있습니다.
* **링크 또는 포함:**
게시 후 두 가지 옵션이 있습니다.
   * **직접 연결:**
제공된 URL을 사용하여 비디오에 직접 연결합니다. 마케팅 사이트에서 적절하게 하이퍼링크를 지정합니다.
   * **비디오 포함:**
제공된 포함 코드를 복사하여 비디오를 표시할 웹 페이지의 HTML에 붙여넣습니다. 이렇게 하면 사이트에서 비디오를 직접 재생할 수 있습니다.

자세히 알아보시겠습니까? 다음으로 이동 [비디오](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### 최적의 품질과 참여를 위한 비디오 구성

**비즈니스 사례:** *최상의 품질과 참여를 위해 비디오를 설정하십시오.*

최상의 품질과 비디오 참여를 보장하려면 다음 모범 사례 전략의 조합을 구현하는 것이 좋습니다.

* **내장된 HTML5 비디오 뷰어 사용:**
Dynamic Media HTML5 비디오 뷰어 사전 설정은 강력한 비디오 플레이어입니다. HTML5 비디오 재생 및 모바일 장치와 관련된 일반적인 문제를 방지하려면 이 도구를 사용하십시오.
이러한 사전 설정은 적응형 비트율 스트리밍 전달 및 제한된 데스크탑 브라우저 도달과 같은 문제를 해결합니다.
자세히 알아보시겠습니까? 다음으로 이동 [우수 사례: HTML 5 비디오 뷰어 사용](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Dynamic Media 비디오 프로필 사용:**
Dynamic Media의 비디오 프로필은 효율적인 비디오 관리, 일관된 품질 및 적응형 스트리밍에 도움이 됩니다.
자세히 알아보시겠습니까? 다음으로 이동 [Dynamic Media 비디오 프로필](/help/assets/dynamic-media/video-profiles.md).

* **비디오 인코딩에 대한 모범 사례를 따르십시오.**
인코딩 중에 과도한 다운스케일링 없이 원래 비디오 품질을 유지하는 비디오 인코딩 프로필을 적용합니다.
자세히 알아보시겠습니까? 다음으로 이동 [비디오 인코딩 모범 사례](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **점진적 스트리밍 대신 적응형 스트리밍 채택:**
적응형 스트리밍은 시청자의 인터넷 연결 속도와 기기 기능에 따라 영상 품질을 조절한다.
HLS(HTTP 라이브 스트리밍) 또는 DASH(`Dynamic Adaptive Streaming over HTTP`)를 클릭하여 최적의 재생 품질을 보장합니다.
비디오를 선형적으로 전달하는 점진적 스트리밍과 달리 적응형 스트리밍은 버퍼링을 최소화하고 원활한 시청 경험을 제공합니다.

* **계정에서 DASH 활성화(HTTP를 통한 디지털 적응형 스트리밍):**
DASH는 적응적 스트리밍을 통해 비디오 컨텐츠를 동적으로 서비스한다.
DASH를 활성화하려면 환경에 대한 지원 티켓을 만듭니다.
자세히 알아보시겠습니까? 다음으로 이동 [Dynamic Media 계정에서 DASH 활성화](/help/assets/dynamic-media/video.md#enable-dash).

### 다국어 사용을 위한 비디오 다국어화

**비즈니스 사례:** *비디오를 다국어 소비에 맞게 준비합니다.*

다국어 소비를 위한 비디오를 국제화하는 것은 전 세계 대상자에게 도달하기 위해 필수적입니다. Dynamic Media은 이 목표를 달성하는 데 도움이 되는 기능을 제공합니다.

* **비디오 업로드:**
   * 먼저 비디오 인코딩 프로필을 만듭니다. Dynamic Media과 함께 제공되는 사전 정의된 적응형 비디오 인코딩 프로필을 사용하거나 사용자 지정 프로필을 만들 수 있습니다.
   * 기본 소스 비디오를 업로드하는 하나 이상의 폴더와 비디오 처리 프로필을 연결합니다.
   * 기본 소스 비디오를 이러한 폴더에 업로드합니다. Dynamic Media은 지정된 비디오 처리 프로필에 따라 인코딩합니다.
   * Dynamic Media은 최소 해상도가 25× 25보다 큰 짧은 형식의 비디오를 주로 지원합니다(최대 30분). 각각 최대 15GB의 비디오 파일을 업로드할 수 있습니다1.

* **비디오 관리:**
   * AEM 내에서 비디오 자산을 구성, 탐색 및 검색합니다.
   * 비디오 자산을 미리 보고 게시합니다.
   * 소스 비디오와 인코딩된 변환을 관련 썸네일과 함께 봅니다.
   * 제목, 설명 및 태그2 등의 비디오 속성을 편집합니다.

* **현지화:**
   * 각 대상 지역/언어에 대해 오디오 트랙 및 자막을 만듭니다.
   * AEM 인터페이스에서 비디오에 이러한 오디오 및 자막 트랙을 추가합니다.
   * 사용자가 동영상을 재생하면서 자신이 원하는 언어를 선택해 오디오와 자막을 재생할 수 있다.

* **게시:**
   * AEM을 WCM(웹 컨텐츠 관리) 시스템으로 사용하는 경우 웹 페이지에 비디오를 직접 추가할 수 있습니다.
   * 서드파티 WCM 시스템을 사용하는 경우 URL 또는 포함 코드를 사용하여 웹 페이지에 비디오를 연결하거나 포함할 수 있습니다.

자세히 알아보시겠습니까? 다음으로 이동 [Dynamic Media의 비디오에 대한 여러 캡션 및 오디오 트랙 지원 정보](/help/assets/dynamic-media/video.md#about-msma) 또는 시계 [비디오에 여러 캡션 및 오디오 트랙 추가](https://delivery-p106302-e1008131.adobeaemcloud.com/adobe/assets/urn:aaid:aem:daf9a222-9f7f-4333-b167-98cb4c63a1f8/play) (1분 41초).


## 고객에게 에셋 전달

### 이미지 크기 최적화 및 페이지 로드 시간 최소화

**비즈니스 사례:** *브라우저 또는 화면에 맞게 이미지 크기를 최적화하고 페이지 로드 시간을 줄입니다.*

Dynamic Media 스마트 이미징은 클라이언트의 브라우저 기능을 기반으로 이미지의 형식, 크기 및 품질을 자동으로 최적화하여 이미지 제공 성능을 향상시키는 강력한 도구입니다.

Adobe은 이미지 형식을 수동으로 설정하는 대신 스마트 이미징 기능을 사용할 것을 권장합니다. `webp` 또는 `avif`. 이유는 다음과 같습니다.

* **브라우저 호환성:**
스마트 이미징을 사용하면 제공된 이미지 형식이 사용자의 브라우저와 호환됩니다.
* **최적의 압축:**
특정 브라우저, 네트워크 조건 및 화면 해상도를 기준으로 압축에 가장 적합한 형식을 선택합니다.
* **최신 형식:**
While `avif` 는 더 나은 압축을 제공하는 최신 형식이며 아직 모든 브라우저에서 보편적으로 지원되지 않습니다.
* **모범 사례:**
최상의 웹 최적화 형식을 보장하기 위해 명령을 수동으로 사용하는 대신 스마트 이미징에서 형식을 선택하도록 신뢰할 수 있습니다 `fmt=webp` 또는 `fmt=avif`.

스마트 이미징을 사용하면 각 사용자의 검색 환경에 맞게 가능한 가장 효율적인 방식으로 이미지가 제공되도록 할 수 있습니다. 이 접근법은 프로세스를 단순화하고 이미지 로딩 시간 및 전반적인 사용자 경험의 관점에서 개선된 성능으로 이어질 수 있다.

자세히 알아보시겠습니까? 다음으로 이동 [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md).
