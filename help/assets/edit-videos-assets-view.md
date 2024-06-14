---
title: 비디오 편집
description: 다음을 사용하여 비디오 편집 [!DNL Adobe Express] 옵션을 제공하고 업데이트된 비디오를 버전으로 저장합니다.
role: User
exl-id: 42b25935-e2ff-444f-97c8-b4ed56f3ef9e
source-git-commit: afdab9a7b449673ecf15bc9ab31307388da7b64e
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 17%

---

# 에서 비디오 편집 [!DNL Assets view] {#edit-videos}

에셋 사용자는 에셋이 포함되어 있어 비디오 컨텐츠의 변형을 손쉽게 만들 수 있습니다 [!DNL Adobe Express] 비디오에 대한 빠른 작업 의 빠른 작업 [!DNL Assets view] 제공: [!DNL Adobe Express] 비디오 자르기, 비디오 크기 조정, 비디오 트리밍 및 비디오를 GIF으로 변환 등 사용자에게 친숙한 비디오 편집 옵션을 제공합니다.

비디오를 편집하려면 비디오 세부 정보로 이동하여 [!UICONTROL 비디오 편집]. 또는 에셋을 선택하고 세부 정보 를 클릭한 다음 를 클릭합니다 ![가위](assets/do-not-localize/cut.svg) 오른쪽 창에서 사용할 수 있는 아이콘. 비디오를 편집한 후 새 비디오를 새 버전 또는 새 에셋으로 저장할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

액세스 권한 [!DNL Adobe Express] 및 하나 이상의 환경이 AEM Assets 내에 있습니다. 환경은 [!DNL Assets as a Cloud Service] 또는 [!DNL Assets view] 내의 저장소 중 하나일 수 있습니다.

## Adobe Express을 사용하여 비디오 편집 {#edit-video-using-express}

임베디드 기능을 사용하여 비디오를 완벽한 크기 및 방향으로 쉽게 변환할 수 있습니다 [!DNL Adobe Express] 빠른 작업.

### 비디오 자르기 {#crop-video-using-express}

임베디드 기능을 사용하여 비디오에서 원하지 않는 부분을 제거할 수 있습니다 [!DNL Adobe Express] 빠른 작업. 이렇게 하려면 아래 단계를 수행합니다.

1. 비디오를 선택하고 **[!UICONTROL 편집]**.
2. 클릭 **[!UICONTROL 비디오 자르기]** 왼쪽 창에서 사용할 수 있는 빠른 작업
3. 비디오 모서리에 있는 핸들을 드래그하여 원하는 자르기를 만들거나 기존 화면 크기 중에서 원하는 크기를 선택합니다.
4. 비디오를 음소거 또는 음소거 해제하도록 선택할 수 있습니다.
5. **[!UICONTROL 적용]**을 클릭합니다.
   ![Adobe Express로 비디오 자르기](assets/adobe-express-crop-video.png)

   자른 비디오를 다운로드할 수 있습니다. 편집된 에셋을 동일한 에셋의 새 버전으로 저장하거나 새 에셋으로 저장할 수 있습니다. ![Adobe Express으로 비디오 저장](assets/adobe-express-save-video.png)

### 비디오 크기 조정 {#resize-video-using-express}

DAM의 최종 비디오 콘텐츠는 특정 채널에 배포하기 위해 크기를 조정해야 하는 경우가 많습니다. [!DNL Assets view] 에서는 일반적인 소셜 채널에 필요한 크기에 맞게 비디오의 크기를 쉽게 조정할 수 있으며 사용자 지정 해상도에도 맞출 수 있습니다. 을 사용하여 비디오 크기를 조정하려면 [!DNL Assets view]를 클릭하고 아래 단계를 수행하십시오.

1. 비디오를 선택하고 **[!UICONTROL 편집]**.
2. 클릭 **[!UICONTROL 비디오 크기 조정]** 왼쪽 창에서 사용할 수 있는 빠른 작업
3. 아래의 소셜 미디어 플랫폼에서 적절한 차원을 선택합니다. **[!UICONTROL 크기 조정]** 드롭다운 목록입니다. 또는 비디오 모서리의 핸들을 드래그하여 원하는 자르기를 만듭니다.
4. 필요한 경우 **[!UICONTROL 비디오 크기 조절]** 필드.
5. 비디오를 음소거 또는 음소거 해제하도록 선택할 수 있습니다.
6. **[!UICONTROL 적용]**을 클릭하여 변경 내용을 적용합니다.
   ![Adobe Express을 통한 비디오 크기 조정](assets/adobe-express-resize-video.png)

크기 조정된 비디오를 다운로드할 수 있습니다. 편집한 자산을 동일한 자산의 새 버전으로 저장하거나 새 자산으로 저장할 수 있습니다.

### 비디오 트리밍 {#trim-video-using-express}

더 큰 비디오의 클립을 사용해야 하는 경우 **[!UICONTROL 비디오 트리밍]** 비디오의 섹션을 선택하고 트림하는 기능입니다. 아래 단계를 수행합니다.

1. 비디오를 선택하고 **[!UICONTROL 편집]**.
2. 클릭 **[!UICONTROL 비디오 트리밍]** 왼쪽 창에서 사용할 수 있는 빠른 작업
3. 비디오의 시작 및 종료 시간을 지정하여 비디오의 특정 부분을 트리밍합니다. 또는 비디오 모서리의 핸들을 드래그하여 원하는 트리밍을 만듭니다.
4. 에서 적절한 차원을 선택합니다. **[!UICONTROL 크기]** 드롭다운 목록입니다.
5. 비디오를 음소거 또는 음소거 해제하도록 선택할 수 있습니다.
6. **[!UICONTROL 적용]**을 클릭하여 변경 내용을 적용합니다.
   ![Adobe Express을 통한 비디오 크기 조정](assets/adobe-express-trim-video.png)

트리밍한 비디오를 다운로드할 수 있습니다. 편집한 자산을 동일한 자산의 새 버전으로 저장하거나 새 자산으로 저장할 수 있습니다.

### 비디오를 GIF으로 변환 {#convert-mp4-to-gif-using-express}

Adobe Express을 사용하여 MP4 비디오를 GIF 형식으로 빠르게 변환할 수 있습니다. 다음 단계를 실행합니다.

1. 비디오를 선택하고 **[!UICONTROL 편집]**.
2. 클릭 **[!UICONTROL GIF으로 변환]** 왼쪽 창에서 사용할 수 있는 빠른 작업
3. 원하는 품질에 따라 적절한 파일 크기를 선택합니다. 또한 가로, 세로 또는 사각형의 방향을 선택합니다.
4. 비디오 모서리에 있는 핸들을 드래그하여 원하는 자르기를 만듭니다.
5. **[!UICONTROL 적용]**&#x200B;을 클릭합니다.

   ![Adobe Express을 사용하여 비디오를 GIF으로 변환](assets/adobe-express-convert-video-to-gif.png)

비디오를 GIF 형식으로 다운로드할 수 있습니다. 편집한 자산을 동일한 자산의 새 버전으로 저장하거나 새 자산으로 저장할 수 있습니다.

## 제한 사항 {#limitations-video-adobe-express}

* MP4 형식의 비디오만 편집할 수 있습니다.

* 지원되는 최대 소스 파일 크기는 1GB입니다.

* 지원되는 비디오는 46픽셀보다 크고 모든 면에서 3840픽셀보다 작습니다.

* 지원되는 웹 브라우저는 Google Chrome, Firefox, Safari 및 Edge입니다.

* 웹 브라우저의 시크릿 모드에서 기능을 열 수 없습니다.

### 다음 단계 {#next-steps}

* 다음을 사용하여 제품 피드백 제공 [!UICONTROL 피드백] 옵션은 자산 보기 사용자 인터페이스에서 사용할 수 있습니다.

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백을 제공합니다.

* [고객 지원 센터](https://experienceleague.adobe.com/?support-solution=General#support)에 문의하십시오.

>[!MORELIKETHIS]
>
>* [자산 보기에서 이미지 편집](edit-images-assets-view.md)
>* [에셋 미리보기](navigate-assets-view.md)
