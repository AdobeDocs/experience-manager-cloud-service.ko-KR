---
title: 비디오 변환
description: 비디오 변환
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Video renditions {#video-renditions}

AEM(Adobe Experience Manager) 자산은 OGG, FLV 등을 비롯한 다양한 형식의 비디오 자산에 대한 비디오 변환을 생성합니다.

AEM Assets는 미디어 자산에 대한 정적 표현물 및 동적 표현물(DM 인코딩 표현물)을 지원합니다.

정적 변환은 기본적으로 FFMPEG(시스템 경로에 설치되고 사용 가능)를 사용하여 생성되며 컨텐츠 저장소에 저장됩니다.

DM 인코딩 변환은 프록시 서버에 저장되며 런타임 시 제공됩니다.

AEM 자산은 클라이언트측에서 이러한 변환에 대한 재생 지원을 제공합니다.

특정 비디오 자산의 변환을 보려면 해당 자산 페이지를 열고 전역 탐색 아이콘을 누릅니다. 그런 다음 **[!UICONTROL 목록에서]** 표현물을 선택합니다.

비디오 표현물의 목록은 표현물 **[!UICONTROL 패널에 표시됩니다]** .

DM 인코딩 변환에 대한 프록시 서버를 구성하려면 Dynamic Media Cloud 서비스를 구성합니다.

<!-- To generate video renditions with desired parameters, [create a corresponding video profile](video-profiles.md). -->

프록시 서버를 구성하고 비디오 프로필을 만든 후 처리 프로필에 이 비디오 사전 설정을 포함시키고 처리 프로필을 폴더에 적용할 수 있습니다.

>[!NOTE]
>
>Internet Explorer 11의 OGG 및 WAV 파일에 오디오 재생이 작동하지 않습니다. 익스텐션 OGG 또는 WAV가 있는 자산의 자산 세부 정보 페이지에 &quot;잘못된 소스&quot;라는 오류가 표시됩니다. MS Edge 및 iPad의 경우 OGG 파일이 재생되지 않고 지원되지 않는 형식 오류가 발생합니다.