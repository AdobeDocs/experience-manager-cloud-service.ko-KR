---
title: 스마트 이미징
description: Adobe Sensei AI를 사용한 스마트 이미징이 각 사용자의 고유한 보기 특성을 적용하여 환경에 최적화된 적합한 이미지를 자동으로 제공하므로 향상된 성능과 참여를 제공합니다.
feature: Asset Management,Renditions
role: User
exl-id: 863784d9-0c91-4deb-8edd-1354a21581c3
source-git-commit: 743782e2716aa79491adee2f32da6d746bcc40a7
workflow-type: tm+mt
source-wordcount: '2629'
ht-degree: 1%

---

# 스마트 이미징 {#smart-imaging}

## 스마트 이미징이란 무엇입니까? {#what-is-smart-imaging}

스마트 이미징 기술은 Adobe Sensei AI 기능을 적용하고 기존 &quot;이미지 사전 설정&quot;에서 작동합니다. 클라이언트 브라우저 기능을 기반으로 이미지 형식, 크기 및 품질을 자동으로 최적화하여 이미지 전달 성능을 향상시키는 데 도움이 됩니다.

>[!IMPORTANT]
>
>스마트 이미징을 사용하려면 Adobe Experience Manager - Dynamic Media과 번들로 제공되는 기본 CDN(Content Delivery Network)을 사용해야 합니다. 다른 모든 사용자 지정 CDN은 이 기능에서 지원되지 않습니다.

또한 스마트 이미징은 Adobe의 동급 최강의 프리미엄 CDN(Content Delivery Network) 서비스와 완전히 통합되는 향상된 성능 증대의 이점을 제공합니다. 이 서비스는 서버, 네트워크 및 피어링 지점 간의 최적의 인터넷 경로를 찾습니다. 인터넷에서 기본 경로를 사용하는 대신 지연 시간이 가장 짧고 패킷 손실률이 가장 낮은 경로를 찾습니다.

다음 이미지 자산 예는 추가된 스마트 이미징 최적화를 보여줍니다.

| 이미지<br>(URL) | 썸네일 | 크기<br> (JPEG) | 크기(WebP)<br> (스마트 이미징 사용) | % 감소 |
|---|---|---|---|---|
| [이미지 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![그림1](/help/assets/assets-dm/picture1.png) | 73.75KB | 45.92KB | 38% |
| [이미지 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![그림2](/help/assets/assets-dm/picture2.png) | 191KB | 70.66KB | 63% |
| [이미지 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![그림3](/help/assets/assets-dm/picture3.png) | 96.64KB | 39.44KB | 59% |
| [이미지 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![그림 4](/help/assets/assets-dm/picture4.png) | 315.80KB | 178.19KB | 44% |
|  |  |  |  | 평균 = 51% |

위와 유사하게, Adobe은 라이브 고객 사이트에서 7009 URL을 사용하는 테스트도 실행했습니다. 이들은 JPEG을 위해 평균 38%의 파일 크기 최적화를 달성할 수 있었습니다. WebP 포맷의 PNG의 경우 평균 31% 더 많은 파일 크기 최적화를 수행할 수 있었습니다. 스마트 이미징의 기능 때문에 이러한 유형의 최적화가 가능합니다.

모바일 웹에서는 두 가지 요소로 인해 이러한 문제가 더 복잡해집니다.

* 폼 팩터와 고해상도 디스플레이가 서로 다른 다양한 장치입니다.
* 제한된 네트워크 대역폭입니다.

이미지 측면에서 볼 때, 가장 좋은 품질의 이미지를 가능한 효율적으로 제공하는 것이 목표입니다.

### 장치 픽셀 비율 최적화 기본 정보 {#dpr}

CSS 픽셀 비율이라고도 하는 DPR(장치 픽셀 비율)은 장치의 실제 픽셀과 논리 픽셀 간의 관계입니다. 특히 최신 모바일 기기들의 화소 해상도는 망막 스크린의 출현으로 빠른 속도로 높아지고 있다.

장치 픽셀 비율 최적화를 활성화하면 이미지가 화면의 기본 해상도로 렌더링되어 선명하게 표시됩니다.

스마트 이미징 DPR 구성을 켜면 요청이 제공되는 디스플레이의 픽셀 밀도를 기반으로 요청된 이미지가 자동으로 조정됩니다. 현재 디스플레이의 픽셀 밀도는 Akamai CDN 헤더 값에서 가져옵니다.

| 이미지의 URL에 허용되는 값 | 설명 |
|---|---|
| `dpr=off` | 개별 이미지 URL 수준에서 DPR 최적화를 끄십시오. |
| `dpr=on,dprValue` | 스마트 이미징에서 감지한 DPR 값을 사용자 지정 값(클라이언트측 논리 또는 기타 방법으로 감지됨)으로 재정의합니다. 허용되는 값 `dprValue` 0보다 큰 숫자입니다. 지정한 값 1.5, 2 또는 3은 일반적입니다. |

>[!NOTE]
>
>* 다음을 사용할 수 있습니다 `dpr=on,dprValue` 회사 수준 DPR이 설정된 경우라도.
>* DPR 최적화로 인해 결과 이미지가 MaxPix Dynamic Media 설정보다 클 때 이미지의 종횡비를 유지하여 MaxPix 너비가 항상 인식됩니다.


| 요청한 이미지 크기 | DPR 값 | 배달된 이미지 크기 |
|---|---|---|
| 816x500 | 1 | 816x500 |
| 816x500 | 2 | 1632x1000 |

참조 - [이미지 작업 시](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) 및 [스마트 자르기 작업](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### 네트워크 대역폭 최적화 기본 정보 {#network-bandwidth-optimization}

네트워크 대역폭을 켜면 실제 네트워크 대역폭을 기반으로 제공되는 이미지 품질이 자동으로 조정됩니다. 낮은 네트워크 대역폭의 경우 이미 켜져 있어도 DPR 최적화가 자동으로 꺼집니다.

원하는 경우, 회사는 다음을 추가하여 개별 이미지 수준에서 네트워크 대역폭 최적화를 옵트아웃할 수 있습니다 `network=off` 추가 작업이 필요합니다.

| 이미지의 URL에 허용되는 값 | 설명 |
|---|---|
| `network=off` | 개별 이미지 URL 수준에서 네트워크 최적화를 해제합니다. |

DPR 및 네트워크 대역폭 값은 번들 CDN의 감지된 클라이언트측 값을 기반으로 합니다. 이러한 값은 때때로 부정확합니다. 예를 들어, DPR=2가 있는 iPhone 5 및 iPhone12 `dpr=3`, 둘 다 표시 `dpr=2`. 여전히 고해상도 장치의 경우 `dpr=2` 보내는 것보다 낫습니다. `dpr=1`. <!-- The best way to overcome this inaccuracy, however, is to use client-side DPR to give you 100% accurate values. And it works for any device, whether it is Apple or any other device that was launched. See [Use Smart Imaging with client-side Device Pixel Ratio](/help/assets/dynamic-media/client-side-dpr.md) -->


클라이언트측 DPR은 100% 정확한 값을 제공하며, Apple이든 방금 시작한 다른 새로운 장치이든 관계없이 모든 장치에서 작동합니다.

## 최신 스마트 이미징의 주요 이점은 무엇입니까? {#what-are-the-key-benefits-of-smart-imaging}

이미지는 페이지 로드 시간의 대부분을 구성합니다. 이와 같이, 모든 성능 향상은 전환율, 사이트에서 보낸 시간, 사이트 바운스 비율 하락에 지대한 영향을 줄 수 있습니다.

최신 버전의 스마트 이미징 개선 사항:

* 최신 스마트 이미징을 사용하는 웹 페이지의 Google SEO 등급을 개선했습니다.
* 런타임 시 최적화된 컨텐츠를 즉시 제공합니다.
* Adobe Sensei 기술을 사용하여 품질에 따라 변환(`qlt`)가 이미지 요청에 지정됩니다.
* 스마트 이미징은 `bfc` URL 매개 변수.
* TTL(Time To Live)과 독립적입니다. 이전에는 스마트 이미징이 작동하려면 최소 TTL이 12시간이었습니다.
* 이전에는 원본 이미지와 파생 이미지가 모두 캐시되었으며 캐시를 무효화하는 2단계 프로세스였습니다. 최신 Smart Imaging에서는 파생자만 캐시되므로 단일 단계 캐시 무효화 프로세스를 허용합니다.
* 규칙 세트에 사용자 지정 헤더를 사용하는 고객은 이전 버전의 Smart Imaging과 달리 이러한 헤더가 차단되지 않으므로 최신 Smart Imaging을 활용할 수 있습니다. 예를 들어, &quot;Timing Allow Origin&quot;, &quot;X-Robot&quot;에서 설명한 대로 [이미지 응답에 사용자 지정 헤더 값 추가|Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html).

## 스마트 이미징과 관련된 라이센스 비용이 있습니까? {#are-there-any-licensing-costs-associated-with-smart-imaging}

아니요. 스마트 이미징은 기존 라이선스에 포함되어 있습니다. 이 규칙은 Dynamic Media Classic 또는 Experience Manager - Dynamic Media(On-prem, AMS 및 Experience Manager)에 대해 적용됩니다.

>[!NOTE]
>
>Dynamic Media - 하이브리드 고객은 스마트 이미징을 사용할 수 없습니다.

## 스마트 이미징은 어떻게 작동합니까? {#how-does-smart-imaging-work}

소비자가 이미지를 요청하면 스마트 이미징은 사용자 특성을 확인하고 사용 중인 브라우저를 기반으로 적절한 이미지 형식으로 변환합니다. 이러한 형식 변환은 시각적 품질을 저하시키지 않는 방식으로 수행됩니다. 스마트 이미징은 다음과 같은 방식으로 브라우저 기능에 따라 이미지를 다른 형식으로 자동으로 변환합니다.

<!--   * Safari 14.0 +
    * Safari 14 only with iOS 14.0 and above and macOS BigSur and above -->

* 다음 브라우저의 경우 자동으로 WebP로 변환합니다.
   * Chrome
   * Firefox
   * Microsoft® Edge
   * Safari(iOS, macOS, iPadOS에서), 제공된 브라우저 및 OS 버전에서 WebP를 지원합니다
   * Android™
   * Opera
* 기존 브라우저는 다음을 지원합니다.

   | 브라우저 | 브라우저/OS 버전 | 형식 |
   | --- | --- | --- |
   | Safari | iOS/iPad 14.0 또는 macOS BigSur 이전 | JPEG2000 |
   | Edge | 18보다 이전 | JPEGXR |
   | Internet Explorer | 9+ | JPEGXR |
* 이러한 형식을 지원하지 않는 브라우저의 경우 원래 요청한 이미지 형식이 제공됩니다.

원본 이미지 크기가 스마트 이미징에서 만드는 이미지 크기보다 작으면 원본 이미지가 제공됩니다.

## 지원되는 이미지 형식은 무엇입니까? {#what-image-formats-are-supported}

스마트 이미징에 대해 다음 이미지 형식이 지원됩니다.

* JPEG
* PNG

<!-- For any other format mentioned in a URL, you should explicity turn off Smart Imaging.  Append modifier `bfc=off` to the URL for file formats other than JPEG and PNG. You can accomplish this by using either one of the following methods:

* Use a ruleset if the `fmt` modifier is mentioned in the URL. 
* Append in URL modifiers field of the presets concerned.

Adobe is working on a permanent fix that does not require you to append `bfc=off` for `fmt !=JPEG` or `fmt !=PNG`. This topic will be updated after the fix is delivered. -->

## 이미 사용 중인 기존 이미지 사전 설정에서 스마트 이미징은 어떻게 작동합니까? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

스마트 이미징은 기존의 &quot;이미지 사전 설정&quot;에서 작동합니다. 품질을 제외한 모든 이미지 설정을 준수합니다(`qlt`) 및 format( )`fmt`) 요청된 파일 형식이 JPEG 또는 PNG인 경우 형식 변환을 위해 스마트 이미징은 이미지 사전 설정 설정에 정의된 대로 전체 시각적 품질을 유지하지만 더 작은 파일 크기로 유지합니다. 원본 이미지 크기가 스마트 이미징에서 만드는 이미지 크기보다 작으면 원본 이미지가 제공됩니다.

<!-- In addition, if your image presets are used to return `fmt !=JPEG` or `fmt !=PNG`, be sure append `bfc=off` in the preset modifier field to return the requested file format. -->

## URL, 이미지 사전 설정을 변경하거나 스마트 이미징을 위해 내 사이트에 새 코드를 배포해야 합니까? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

기존 사용자 지정 도메인에서 스마트 이미징을 구성하는 경우 스마트 이미징이 기존 이미지 URL 및 이미지 사전 설정과 원활하게 작동합니다. 또한 스마트 이미징에서는 사용자의 브라우저를 감지하기 위해 웹 사이트에 코드를 추가할 필요가 없습니다. 모두 자동으로 처리됩니다.

스마트 이미징을 사용하도록 새 사용자 지정 도메인을 구성해야 하는 경우 이 사용자 지정 도메인을 반영하도록 URL을 업데이트해야 합니다.

스마트 이미징의 사전 요구 사항을 이해하려면 다음을 참조하십시오 [스마트 이미징을 사용할 수 있습니까?](#am-i-eligible-to-use-smart-imaging)

<!-- OLD No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. All of this is handled automatically. -->

<!-- OLD As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## 스마트 이미징이 HTTPS에서 작동합니까? HTTP/2는 어떻습니까? {#does-smart-imaging-working-with-https-how-about-http}

스마트 이미징은 HTTP 또는 HTTPS를 통해 전달된 이미지에서 작동합니다. 또한 HTTP/2에서도 작동합니다.

## 스마트 이미징을 사용할 수 있습니까? {#am-i-eligible-to-use-smart-imaging}

Smart Imaging을 사용하려면 회사의 Experience Manager 또는 Dynamic Media Classic 계정의 Dynamic Media이 다음 요구 사항을 충족해야 합니다.

* Adobe 번들 CDN(Content Delivery Network)을 라이센스의 일부로 사용합니다.
* 전용 도메인 사용(예: `images.company.com` 또는 `mycompany.scene7.com`). 일반 도메인이 아닙니다(예: `s7d1.scene7.com`, `s7d2.scene7.com`, 또는 `s7d13.scene7.com`).

도메인을 찾으려면 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)그런 다음 회사 계정 또는 계정에 로그인합니다.

이동 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일반 설정]**. 레이블이 지정된 필드를 찾습니다 **[!UICONTROL 게시된 서버 이름]**. 현재 일반 도메인을 사용하는 경우 사용자 지정 도메인으로 이동을 요청할 수 있습니다. 기술 지원 티켓을 제출할 때 이 전환 요청을 수행합니다.

첫 번째 사용자 지정 도메인은 Dynamic Media 라이센스를 통해 추가 비용이 들지 않습니다.

## 내 계정에 대해 스마트 이미징을 활성화하는 프로세스는 무엇입니까? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

스마트 이미징 사용 요청을 시작합니다. 자동으로 활성화되지 않습니다.

기본적으로 Dynamic Media 회사 계정에 대해 스마트 이미징 DPR 및 네트워크 최적화가 비활성화(꺼짐)됩니다. 이러한 기본 개선 사항 중 하나 또는 둘 다 활성화(켜기)하려면 아래 설명된 지원 사례를 만드십시오.

<!-- NOW AVAILABLE IN ALL THREE REGIONS AS OF AUGUST 2. 2021. SEE CQDOC- 17915 The release schedule for Smart Imaging DPR and network optimization is available in North as follows:

| Region | Target date |
|---|---|
| North America | Live | 
| Europe, Middle East, Africa | 13 August 2021 | 
| Asia-Pacific | 22 July 2021 | -->

1. [Admin Console을 사용하여 지원 사례를 만듭니다](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).
1. 지원 사례에 다음 정보를 제공하십시오.

   1. 기본 연락처 이름, 이메일, 전화
   1. 스마트 이미징에 사용할 수 있는 모든 도메인(즉, `images.company.com` 또는 `mycompany.scene7.com`).

      도메인을 찾으려면 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)그런 다음 회사 계정 또는 계정에 로그인합니다.

      이동 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일반 설정]**.

      레이블이 지정된 필드를 찾습니다 **[!UICONTROL 게시된 서버 이름]**.
   1. Adobe을 통해 CDN을 사용하고 있으며 직접 관계로 관리하지 않는지 확인합니다.
   1. 다음과 같은 전용 도메인을 사용하고 있는지 확인합니다. `images.company.com` 또는 `mycompany.scene7.com`, 및 과 같은 일반 도메인이 아님 `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

      도메인을 찾으려면 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)그런 다음 회사 계정 또는 계정에 로그인합니다.

      이동 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일반 설정]**.

      레이블이 지정된 필드를 찾습니다 **[!UICONTROL 게시된 서버 이름]**. 현재 일반 Dynamic Media Classic 도메인을 사용 중인 경우, 이 전환의 일부로 고유한 사용자 지정 도메인으로 이동을 요청할 수 있습니다.
   1. HTTP/2에서 작동하도록 할지 여부를 지정합니다.

1. Adobe 고객 지원 팀에서는 요청을 제출한 순서에 따라 스마트 이미징 고객 대기 목록에 추가합니다.
1. Adobe이 요청을 처리할 준비가 되면 고객 지원 팀에서 대상 날짜를 조정하고 설정해야 합니다.
1. **선택 사항입니다**: Adobe이 새 기능을 프로덕션에 푸시하기 전에 스테이징에서 스마트 이미징을 선택적으로 테스트할 수 있습니다.
1. 고객 지원 센터에서 완료 후 알림을 받습니다.
1. 스마트 이미징의 성능 향상을 극대화하려면 Adobe에서 TTL(Time To Live)을 24시간 이상으로 설정하는 것이 좋습니다. TTL은 CDN에 의해 자산이 캐시되는 기간을 정의합니다. 이 설정을 변경하려면 다음을 수행하십시오.

   1. Dynamic Media Classic을 사용하는 경우 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 게시 설정]** > **[!UICONTROL 이미지 서버]**. 설정 **[!UICONTROL 기본 클라이언트 캐시 Time To Live]** 값 을 24 이상으로 설정합니다.
   1. Dynamic Media을 사용하는 경우 다음을 수행합니다 [이러한 지침은](config-dm.md). 설정 **[!UICONTROL 만료]** 값 24시간 이상

## 언제 내 계정이 스마트 이미징으로 활성화될 수 있습니까? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

요청은 대기 목록에 따라 고객 지원에서 수신하는 순서로 처리됩니다.

>[!NOTE]
>
>스마트 이미징을 활성화하면 Adobe이 캐시를 지우므로 리드 타임이 오래 걸릴 수 있습니다. 따라서 지정된 시간에 몇 개의 고객 전환만 처리할 수 있습니다.

## 스마트 이미징을 사용하도록 전환하면 어떤 위험이 있습니까? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

고객 웹 페이지에는 위험이 없습니다. 그러나 스마트 이미징으로 전환하면 CDN 캐시가 지워집니다. 이 작업에는 Experience Manager 시 Dynamic Media Classic 또는 Dynamic Media의 새 구성으로 이동하는 작업이 포함됩니다.

초기 전환 중에 캐싱되지 않은 이미지는 캐시가 다시 빌드될 때까지 Adobe의 원본 서버에 직접 연결됩니다. 따라서 Adobe은 한 번에 몇 개의 고객 전환을 처리하여 오리진에서 요청을 가져올 때 허용되는 성능을 유지할 수 있도록 계획합니다. 대부분의 고객의 경우 캐시가 1~2일 내에 CDN에서 다시 완전히 빌드됩니다.

## 스마트 이미징이 예상대로 작동하는지 확인하려면 어떻게 해야 합니까?{#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. 계정이 스마트 이미징으로 구성된 후 브라우저에서 Dynamic Media Classic 또는 Adobe Experience Manager - Dynamic Media 이미지 URL을 로드합니다.
1. 로 이동하여 Chrome 개발자 창을 엽니다. **[!UICONTROL 보기]** > **[!UICONTROL 개발자]** > **[!UICONTROL 개발자 도구]** 클릭합니다. 또는 원하는 브라우저 개발자 도구를 선택합니다.

1. 개발자 도구가 열려 있을 때 캐시가 비활성화되어 있는지 확인합니다.

   * Windows®에서 개발자 도구 창의 설정으로 이동한 후 를 선택합니다 **[!UICONTROL 캐시 비활성화(devtools가 열려 있는 동안)]** 확인란을 선택합니다.
   * macOS의 개발자 창에서 **[!UICONTROL 네트워크]** 탭, 선택 **[!UICONTROL 캐시 비활성화]**.

1. 컨텐츠 유형이 적절한 형식으로 변형됩니다. 다음 스크린샷은 Chrome에서 WebP로 동적으로 변환되는 PNG 이미지를 보여줍니다.
1. 다른 브라우저 및 사용자 조건에서 이 테스트를 반복합니다.

>[!NOTE]
>
>일부 이미지는 변환되지 않습니다. 스마트 이미징에서는 전환이 성능을 향상시킬 수 있는지 여부를 결정합니다. 예상 성능 이점이 없거나 형식이 JPEG 또는 PNG가 아닌 경우 이미지가 변환되지 않는 경우가 있습니다.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## 요청에 대해 스마트 이미징을 끌 수 있습니까?{#turning-off-smart-imaging}

예. 수정자를 추가하여 스마트 이미징을 끌 수 있습니다 `bfc=off` 아래와 같이 변경하는 것을 의미합니다.

## 회사 수준에서 DPR 및 네트워크 최적화를 끄도록 요청할 수 있습니까? {#dpr-companylevel-turnoff}

예. 회사에서 DPR 및 네트워크 최적화를 비활성화하려면 이 주제의 앞부분에서 설명한 대로 지원 사례를 만드십시오.

## &quot;조정&quot;은 무엇입니까? 정의할 수 있는 설정이나 동작이 있습니까? {#tuning-settings}

현재 선택적으로 스마트 이미징을 활성화하거나 비활성화할 수 있습니다. 다른 튜닝은 사용할 수 없습니다.

## 스마트 이미징이 품질 설정을 관리하는 경우 설정할 수 있는 최소값과 최대값이 있습니까? 예를 들어 &quot;60보다 크지 않음&quot; 및 &quot;80보다 크지 않음&quot;을 설정할 수 있습니까? {#minimum-maximum}

현재 Smart Imaging에는 이러한 프로비저닝 기능이 없습니다.

## 경우에 따라 JPEG 이미지가 WebP 이미지 대신 Chrome으로 반환됩니다. 왜 이런 변화가 일어납니까? {#jpeg-webp}

스마트 이미징은 전환이 유용한지 여부를 결정합니다. 비교 가능한 품질과 함께 파일 크기가 더 작은 경우에만 새 이미지를 반환합니다.

스마트 이미징 DPR 최적화는 Adobe Experience Manager Sites 구성 요소 및 Dynamic Media 뷰어와 어떻게 작동합니까?

* Experience Manager Sites 코어 구성 요소 는 기본적으로 DPR 최적화를 위해 구성됩니다. 서버측 스마트 이미징 DPR 최적화로 인해 큰 이미지가 발생하지 않도록 하려면, `dpr=off` 는 항상 Experience Manager Sites 핵심 구성 요소 Dynamic Media 이미지에 추가됩니다.
* 주어진 Dynamic Media 기초 구성 요소는 서버측 스마트 이미징 DPR 최적화로 인해 큰 이미지가 발생하지 않도록 DPR 최적화에 대해 기본적으로 구성되어 있습니다. `dpr=off` 는 항상 Dynamic Media Foundation 구성 요소 이미지에 추가됩니다. 고객이 DM 기초 구성 요소에서 DPR 최적화를 선택 취소하더라도 서버측 스마트 이미징 DPR이 시작되지 않습니다. 요약하면 DM 기초 구성 요소에서 DPR 최적화는 DM 기초 구성 요소 수준 설정에만 적용됩니다.
* 모든 뷰어 측 DPR 최적화는 서버 측 스마트 이미징 DPR 최적화와 함께 작동하며 과도한 크기의 이미지를 생성하지 않습니다. 즉, 확대/축소 지원 뷰어의 기본 보기처럼 DPR이 뷰어에 의해 처리되는 모든 위치에서 서버 측 스마트 이미징 DPR 값이 트리거되지 않습니다. 마찬가지로 색상 견본 및 축소판과 같은 뷰어 요소에 DPR 처리가 없으면 서버측 스마트 이미징 DPR 값이 트리거됩니다.

참조 - [이미지 작업 시](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) 및 [스마트 자르기 작업](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

>[!MORELIKETHIS]
>
>* [차세대 이미지 포맷인 WebP 및 AVIF를 사용한 이미지 최적화.](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)
>

