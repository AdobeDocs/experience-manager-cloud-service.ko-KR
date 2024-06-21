---
title: Screens에서 비디오 표현물 as a Cloud Service 만들기
description: 이 페이지에서는 Screens as a Cloud Service으로 비디오 렌디션을 만드는 방법에 대해 설명합니다.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Screens에서 비디오 표현물 as a Cloud Service 만들기 {#creating-screens-video-renditions}

## 소개 {#introduction}

이 섹션에서는 Screens 플레이어에서 사용되는 비디오 표현물을 만드는 방법을 설명합니다.

>[!IMPORTANT]
>Screens 채널에서 비디오를 사용하려는 경우 이 섹션에서 강조 표시된 단계를 구성해야 합니다.

## Screens에서 비디오 표현물을 as a Cloud Service으로 만드는 단계 {#steps-creating-screens-video-renditions}

Screens Content Provider에서 as a Cloud Service으로 비디오 렌디션을 만들려면 아래 단계를 따르십시오.

1. Screens Content Provider에서 내 채널로 이동합니다.

   >[!NOTE]
   >다음을 참조하십시오 [Screens Content Provider 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html#screens-content-provider) 을 참조하십시오.

1. 왼쪽 탐색 모음에서 도구 섹션을 클릭하고 를 클릭합니다. **에셋** 그런 다음 을 클릭합니다. **처리 프로필**.

   ![처리 프로필 을 클릭합니다](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. 클릭 **만들기** 처리 프로필을 만들려면

   ![만들기 를 클릭합니다](/help/screens-cloud/assets/configure/screens-video-2.png)

1. 다음을 입력합니다. **이름**, 예: **ScreensProcessingProfile**.

   ![[이름] 필드를 강조 표시하는 [처리 프로필] 대화 상자](/help/screens-cloud/assets/configure/screens-video-3.png)

1. 다음으로 이동 **비디오** 비디오 인코딩을 추가할 수 있도록 탭한 다음 **새로 추가**.

   ![새로 추가 버튼이 강조 표시된 처리 프로필 대화 상자](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. 다음을 입력합니다. **인코딩 이름** 예: , **screens-fullhd** 및 **비트율** 다음으로: **2500**.

   ![저장 버튼이 강조 표시된 처리 프로필 대화 상자.](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >&quot;screens-&quot;로 시작하는 인코딩 이름을 사용하십시오. 이러한 비디오 표현물만 Screens에서 비디오 경험을 as a Cloud Service으로 재생하는 것으로 간주됩니다. 비디오를 작동하는 비트율을 입력합니다(720px 비디오의 경우 2500kbps, 1080px의 경우 5000kbps).

   >[!NOTE]
   >다양한 폭/높이/비트율로 여러 비디오 표현물을 추가하여 비디오를 작동할 수 있습니다. 모든 화면, 렌디션은 장치가 비디오 렌디션만 재생하더라도 Screens 장치에 의해 다운로드됩니다.

1. **저장**&#x200B;을 클릭합니다.

1. 처리 프로필을 선택하고 **폴더에 프로필 적용**.

   ![폴더에 프로필 적용](/help/screens-cloud/assets/configure/screens-video-5.png)

1. 스크린 비디오가 보관되는 폴더를 선택하고 **적용**.

   ![적용 을 클릭합니다](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >
   >* 여러 처리 프로필을 만들고 해당 폴더에 적용하여 해당 폴더의 비디오가 특정 비디오 렌디션을 가져오도록 할 수 있습니다.
   >* 처리 프로필이 적용된 폴더에 비디오를 업로드하면 비디오가 처리됩니다. Screens 디바이스에서 비디오를 재생하는 데 사용되는 구성된 렌디션이 생성됩니다.
