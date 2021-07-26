---
title: Screens에서 Cloud Service으로 스크린 비디오 표현물 만들기
description: 이 페이지에서는 Screens에서 Cloud Service으로 화면 비디오 표현물을 만드는 방법을 설명합니다.
source-git-commit: ec939ac6a91523a9ba64a555943eba8e6da071eb
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Screens에서 Cloud Service으로 스크린 비디오 표현물 만들기 {#creating-screens-video-renditions}

## 소개 {#introduction}

이 안내서에서는 Screens 플레이어에서 사용되는 비디오 표현물을 만드는 방법을 설명합니다.

>[!IMPORTANT]
>[스크린] 채널에서 비디오를 사용하려는 경우 이 섹션에서 강조 표시된 단계를 구성해야 합니다.

## Screens에서 Cloud Service으로 화면 비디오 표현물을 만드는 절차 {#steps-creating-screens-video-renditions}

1. 스크린 컨텐츠 제공자에서 채널로 이동합니다.

   >[!NOTE]
   >자세한 내용은 [스크린 컨텐츠 공급자 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider)을 참조하십시오.

1. 왼쪽 탐색 막대에서 도구 섹션을 클릭하고 **자산**&#x200B;을 클릭한 다음 **처리 프로필**&#x200B;을 클릭합니다.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. **만들기**&#x200B;를 클릭하여 새 처리 프로필을 만듭니다.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. **이름**(예: **ScreensProcessingProfile**)을 입력합니다.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. **비디오** 탭으로 이동하여 비디오 인코딩을 추가하고 **새로 추가**&#x200B;를 클릭합니다.


   >[!IMPORTANT]
   >&quot;screens-&quot;로 시작하는 인코딩 이름을 사용해야 합니다. 이러한 비디오 표현물만 Screens As a Cloud Service에서 비디오 경험을 재생하는 것으로 간주됩니다. 비디오에 맞는 비트율(720px 비디오의 경우 2500kbps, 1080px의 경우 5000kbps)을 입력합니다

   >[!NOTE]
   >필요에 따라 다양한 너비/높이/비트율을 사용하여 여러 비디오 표현물을 추가할 수 있지만, 장치가 비디오 표현물만 재생하더라도 모든 화면-표현물은 스크린 장치에서 다운로드됩니다.

1. Save 를 클릭합니다.

1. 처리 프로필을 선택하고 &quot;폴더에 프로필 적용&quot;을 클릭합니다

1. 스크린 비디오가 유지되는 폴더를 선택하고 적용을 클릭합니다

1. 여러 처리 프로필을 만들어 해당 폴더에 적용할 수 있으므로 해당 폴더의 비디오에서 특정 비디오 표현물을 가져올 수 있습니다

1. 처리 프로필이 적용되는 폴더에 비디오를 업로드하면, 비디오가 처리되고 구성된 표현물이 만들어지고, 이 표현물은 스크린 장치에서 비디오를 재생하는 데 사용됩니다.

