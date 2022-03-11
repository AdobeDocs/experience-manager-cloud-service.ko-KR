---
title: 화면에서 비디오 표현물 만들기 as a Cloud Service
description: 이 페이지에서는 Screens에서 비디오 표현물을 as a Cloud Service으로 만드는 방법을 설명합니다.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# 화면에서 비디오 표현물 만들기 as a Cloud Service {#creating-screens-video-renditions}

## 소개 {#introduction}

이 섹션에서는 Screens 플레이어에서 사용되는 비디오 표현물을 만드는 방법을 설명합니다.

>[!IMPORTANT]
>스크린 채널에서 비디오를 사용하려는 경우 이 섹션에서 강조 표시된 단계를 구성해야 합니다.

## Screens에서 비디오 렌디션을 만드는 단계 as a Cloud Service {#steps-creating-screens-video-renditions}

Screens 컨텐츠 제공업체에서 as a Cloud Service으로 Screens에서 비디오 표현물을 만들려면 아래 절차를 따르십시오.

1. 스크린 컨텐츠 제공자에서 채널로 이동합니다.

   >[!NOTE]
   >을(를) 참조하십시오. [스크린 컨텐츠 공급자 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider) 자세한 내용

1. 왼쪽 탐색 막대에서 도구 섹션을 클릭하고 을(를) 클릭합니다. **자산** 그런 다음 **처리 프로필**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. 클릭 **만들기** 새 처리 프로필을 만들려면

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. 을(를) 입력합니다. **이름**, 예 **ScreensProcessingProfile**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. 다음으로 이동 **비디오** 탭을 사용하여 비디오 인코딩을 추가하고 을(를) 클릭합니다. **새로 추가**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. 을(를) 입력합니다. **인코딩 이름** 예: **screens-fullhd** 그리고 **비트율** 로서의 **2500년**.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >&quot;screens-&quot;로 시작하는 인코딩 이름을 사용해야 하며 이러한 비디오 표현물만 Screens에서 비디오 경험을 as a Cloud Service으로 재생하는 것으로 간주됩니다. 비디오를 작동하는 비트율(720px 비디오의 경우 2500kbps, 1080px의 경우 5000kbps)을 입력합니다.

   >[!NOTE]
   >비디오를 작동시키기 위해 다양한 너비/높이/비트율을 사용하여 여러 비디오 표현물을 추가할 수 있습니다. 장치가 비디오 표현물만 재생하지만 모든 화면 - 표현물은 스크린 장치에서 다운로드됩니다.

1. 클릭 **저장**.

1. 처리 프로필을 선택하고 을(를) 클릭합니다 **폴더에 프로필 적용**.

   ![](/help/screens-cloud/assets/configure/screens-video-5.png)

1. 스크린 비디오를 유지하는 폴더를 선택하고 을(를) 클릭합니다 **적용**.

   ![](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >* 여러 처리 프로필을 만들어 해당 폴더에 적용할 수 있으므로 해당 폴더의 비디오에서 특정 비디오 표현물을 가져올 수 있습니다.
   >* 처리 프로필이 적용되는 폴더에 비디오를 업로드하면, 비디오가 처리되고 구성된 표현물이 만들어지고, 이 표현물은 스크린 장치에서 비디오를 재생하는 데 추가로 사용됩니다.

