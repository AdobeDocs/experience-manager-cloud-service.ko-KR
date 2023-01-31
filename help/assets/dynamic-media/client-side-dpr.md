---
title: 클라이언트 측 장치 픽셀 비율이 있는 스마트 이미징 사용
description: Dynamic Media에서 Adobe Experience Manager as a Cloud Service의 스마트 이미징을 사용하여 클라이언트측 장치 픽셀 비율을 사용하는 방법을 알아봅니다.
contentOwner: Rick Brough
role: Admin,User
exl-id: 556710c7-133c-487a-8cd9-009a5912e94c
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# 클라이언트측 장치 픽셀 비율(DPR)이 있는 스마트 이미징 정보 {#client-side-dpr}

현재 스마트 이미징 솔루션은 사용자 에이전트 문자열을 사용하여 사용 중인 장치(데스크탑, 태블릿, 모바일 등)의 유형을 결정합니다.

장치 탐지 기능 - 사용자 에이전트 문자열을 기반으로 하는 DPR은 특히 Apple 장치의 경우 부정확합니다. 또한 새 장치를 시작할 때마다 유효성을 검사해야 합니다.

클라이언트측 DPR은 Apple이든 다른 새로운 장치이든 간에 100% 정확한 값을 제공하고 모든 장치에 대해 작동합니다.

<!-- See also [About network bandwidth optimization](/help/assets/dynamic-media/imaging-faq.md#network-bandwidth-optimization). -->

## 클라이언트측 DPR 코드 사용

**서버 측 렌더링 앱**

1. 서비스 작업자 초기화 로드(`srvinit.js`)을 클릭하여 HTML 페이지의 헤더 섹션에 다음 스크립트를 포함합니다.

   ```javascript
   <script type="text/javascript" src="srvinit.js"></script>
   ```

   Adobe은 이 스크립트를 로드하는 것을 권장합니다 _이전_ 서비스 작업자가 바로 초기화를 시작할 수 있도록 다른 모든 스크립트.

1. HTML 페이지의 본문 섹션 맨 위에 다음 DPR 이미지 태그 코드를 포함합니다.

   ```html
   <img src="aem_dm_dpr_1x.jpg" style="width:1px;height:1px;display:none"
       srcset="aem_dm_dpr_1x.jpg 1x, aem_dm_dpr_1.1x.jpg 1.1x, aem_dm_dpr_1.2x.jpg 1.2x, aem_dm_dpr_1.3x.jpg 1.3x, aem_dm_dpr_1.4x.jpg 1.4x, aem_dm_dpr_1.5x.jpg 1.5x, aem_dm_dpr_1.6x.jpg 1.6x,          aem_dm_dpr_1.7x.jpg 1.7x, aem_dm_dpr_1.8x.jpg 1.8x, aem_dm_dpr_1.9x.jpg 1.9x,
       aem_dm_dpr_2x.jpg 2x, aem_dm_dpr_2.1x.jpg 2.1x, aem_dm_dpr_2.2x.jpg 2.2x, aem_dm_dpr_2.3x.jpg 2.3x, aem_dm_dpr_2.4x.jpg 2.4x, aem_dm_dpr_2.5x.jpg 2.5x, aem_dm_dpr_2.6x.jpg 2.6x, aem_dm_dpr_2.7x.jpg 2.7x, aem_dm_dpr_2.8x.jpg 2.8x, aem_dm_dpr_2.9x.jpg 2.9x,
       aem_dm_dpr_3x.jpg 3x, aem_dm_dpr_3.1x.jpg 3.1x, aem_dm_dpr_3.2x.jpg 3.2x, aem_dm_dpr_3.3x.jpg 3.3x, aem_dm_dpr_3.4x.jpg 3.4x, aem_dm_dpr_3.5x.jpg 3.5x, aem_dm_dpr_3.6x.jpg 3.6x, aem_dm_dpr_3.7x.jpg 3.7x, aem_dm_dpr_3.8x.jpg 3.8x, aem_dm_dpr_3.9x.jpg 3.9x,
       aem_dm_dpr_4x.jpg 4x, aem_dm_dpr_4.1x.jpg 4.1x, aem_dm_dpr_4.2x.jpg 4.2x, aem_dm_dpr_4.3x.jpg 4.3x, aem_dm_dpr_4.4x.jpg 4.4x, aem_dm_dpr_4.5x.jpg 4.5x, aem_dm_dpr_4.6x.jpg 4.6x, aem_dm_dpr_4.7x.jpg 4.7x, aem_dm_dpr_4.8x.jpg 4.8x, aem_dm_dpr_4.9x.jpg 4.9x,
       aem_dm_dpr_5x.jpg 5x">
   ```

   이 DPR 이미지 태그 코드를 포함해야 합니다 _이전_ HTML 페이지의 모든 정적 이미지입니다.

**클라이언트 측 렌더링 앱**

1. HTML 페이지의 헤더 섹션에 다음 DPR 스크립트를 포함하십시오.

   ```javascript
   <script type="text/javascript" src="srvinit.js"></script>
   <script type="text/javascript" src="dprImageInjection.js"></script>
   ```

   두 DPR 스크립트를 하나로 결합하여 여러 네트워크 요청을 방지할 수 있습니다.

   Adobe은 이러한 스크립트를 로드할 것을 권장합니다 _이전_ HTML 페이지의 다른 모든 스크립트.
또한 Adobe은 본문 요소가 아닌 차이 HTML 태그 아래에서 앱을 Bootstrap하는 것을 권장합니다. 이유는 `dprImageInjection.js` HTML 페이지에서 body 섹션의 맨 위에 있는 이미지 태그를 동적으로 삽입합니다.

## JavaScript 파일 다운로드 {#client-side-dpr-script}

다운로드에 있는 다음 JavaScript 파일은 예제 참조로서 사용자에게 제공됩니다. HTML 페이지에서 이러한 파일을 사용하려면 해당 요구 사항에 맞게 각 파일의 코드를 편집해야 합니다.

* `dprImageInjection.js`
* `srvinit.js`
* `srvwrk.js`

[JavaScript 파일 다운로드](/help/assets/dynamic-media/assets/aem-dynamicmedia-smartimaging-dpr.zip)

>[!MORELIKETHIS]
>
>* [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md)

