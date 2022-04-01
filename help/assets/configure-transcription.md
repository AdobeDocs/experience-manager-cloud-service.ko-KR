---
title: 설명 서비스 구성
seo-title: Configure transcription service
description: Adobe Experience Manager 자산이 [!DNL Azure Media Services] 에서는 지원 오디오 또는 비디오 파일에서 WebVTT(Vtt) 형식으로 음성 언어의 텍스트 스크립트를 자동으로 생성합니다.
seo-description: When an audio or video asset is processed in Experience Manager Assets, the AI-based transcription service automatically generates the text transcript rendition of the audio or video asset and stores it at the same location within your Assets repository where the original asset resides. The Experience Manager Assets transcription service allows marketers to effectively manage their audio and video content with added discoverability of the text content as well as increase the ROI of these assets by supporting accessibility and localization.
products: SG_EXPERIENCEMANAGER/ASSETS and Experience Manager as a Cloud Service
sub-product: assets
content-type: reference
contentOwner: Vishabh Gupta
topic-tags: Configuration
feature: Asset Management, Configuration
role: Admin
source-git-commit: feef8159a01393baebe11c014ae6093b79df72d1
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 0%

---


# 설명 구성 [!DNL Experience Manager Assets] {#configure-transcription-service}

전사란 음성 인식 기술을 사용하여 오디오나 비디오 파일의 오디오를 텍스트(음성으로 텍스트)로 변환시키는 프로세스입니다.
[!DNL Adobe Experience Manager Assets] 는 [!DNL Azure Media Services] 에서는 WebVTT(.vtt) 형식으로 지원되는 오디오 또는 비디오 파일에서 음성 언어의 텍스트 스크립트를 자동으로 생성합니다. 오디오 또는 비디오 자산에서 처리되는 경우 [!DNL Experience Manager Assets]를 지정하는 경우, 설명 서비스는 오디오 또는 비디오 자산의 텍스트 스크립트 렌디션을 자동으로 생성하여 원래 자산이 있는 자산 저장소 내의 동일한 위치에 저장합니다. 다음 [!DNL Experience Manager Assets] 전사적인 서비스를 통해 마케터는 텍스트 컨텐츠에 대한 추가 검색 기능을 통해 오디오 및 비디오 컨텐츠를 효과적으로 관리할 수 있을 뿐만 아니라 접근성 및 로컬라이제이션을 지원하여 이러한 자산의 ROI를 향상시킬 수 있습니다.

텍스트 스크립트는 컨텐츠에 대한 텍스트 버전입니다. 예제는 OTT 플랫폼에서 보고 있는 영화입니다. 이 플랫폼에는 액세서빌러티 또는 다른 언어로 된 콘텐츠 사용을 돕기 위한 캡션 또는 자막이 종종 포함됩니다. 또는 마케팅, 학습 또는 엔터테인먼트 용도로 사용되는 오디오 또는 비디오 파일입니다. 이러한 경험은 서식이 지정되거나 적절하게 번역되는 전사로 시작됩니다. 오디오 또는 비디오를 전송하는 것은 수동으로 수행할 때 시간이 많이 걸리고 오류가 발생하기 쉬운 프로세스입니다. 또한 오디오 비디오 컨텐츠가 점점 더 많이 필요하므로 수동 프로세스를 확장해야 하는 과제입니다. [!DNL Experience Manager Assets] 에서는 오디오 및 비디오 자산을 대규모로 처리할 수 있고 타임스탬프 세부 사항과 함께 텍스트 스크립트(.vtt 파일)를 생성하는 Azure의 AI 기반 변환을 사용합니다. Assets와 함께 전사 기능도 Dynamic Media에서 지원됩니다.

변환 기능은 [!DNL Experience Manager Assets]. 그러나 관리자는에서 변환 서비스를 구성하려면 사용자의 Azure 자격 증명이 필요합니다 [!DNL Experience Manager Assets]. 다음을 수행할 수도 있습니다 [평가판 자격 증명 가져오기](https://azure.microsoft.com/en-us/pricing/details/media-services/) Microsoft®에서 바로 Assets의 오디오 또는 비디오 전사 기능을 이용할 수 있습니다.

## 전사 사전 요구 사항 {#prerequisites}

1. 실행 [!DNL Experience Manager Assets as a Cloud Service] 인스턴스.
1. 의 구성에 다음 Azure 자격 증명이 필요합니다 [!DNL Experience Manager Assets]:

   * 클라이언트 ID(API 키)
   * 클라이언트 암호 키
   * 테넌트 끝점(도메인)
   * 미디어 계정
   * 리소스 그룹
   * 구독 ID

   자세한 내용은 [Azure 설명서](https://docs.microsoft.com/en-us/azure/media-services/latest/access-api-howto?tabs=portal) azure Media Services API에 액세스하기 위한 자격 증명을 가져올 수 있습니다.

1. Azure 계정에 새 요청을 처리할 수 있는 충분한 크레딧이 있는지 확인하십시오.

## 설명 구성 [!DNL Experience Manager Assets] {#configure-transcription}

다음은 에서 설명 기능을 활성화하는 데 필요한 구성입니다 [!DNL Experience Manager Assets]:

1. [Azure Media Services 구성](#configure-azure-media-service)
1. [오디오/비디오 추적에 대한 처리 프로필 구성](#configure-processing-profile-for-transcription)


### Azure Media Services 구성 {#configure-azure-media-services}

[!DNL Experience Manager Assets] 사용 [!DNL Azure Media Services] 음성 언어의 텍스트 스크립트를 자동으로 생성합니다 [지원되는 오디오 또는 비디오 파일](#supported-file-formats-for-transcription) 를 반환합니다. 관리자는 다음을 구성할 수 있습니다 [!DNL Azure Media Services] in [!DNL Experience Manager Assets] azure 자격 증명을 사용하여 문제를 해결할 수 있습니다. 다음 [사전 요구 사항](#transcription-prerequisites) list [!DNL Azure] 구성에 필요한 자격 증명입니다. 없는 경우 [!DNL Azure] 계정 및 자격 증명 [Azure Media Services 설명서](https://azure.microsoft.com/en-us/pricing/details/media-services/) 체험판 자격 증명을 받으려면

![configure-transcription-service](assets/configure-transcription-service.png)

이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Media Services 구성]**. 왼쪽 레일에서 폴더(위치)를 선택하고 [!UICONTROL 만들기] 단추를 클릭하여 연결을 구성합니다. [!DNL Azure] 계정이 필요합니다. 이 폴더는 [!DNL Azure] 클라우드 구성은 Experience Manager Assets에 저장됩니다. 을(를) 입력합니다. [!DNL Azure] 자격 증명 및 클릭 **[!UICONTROL 저장 및 닫기]**.

### 전사용 처리 프로필 구성 {#configure-processing-profile}

한 번 [!DNL Azure Media Services] 가 Experience Manager Assets에 구성되어 있으면 다음 단계는 오디오 및 비디오 자산의 AI 기반 변환을 생성할 자산 처리 프로필을 만드는 것입니다. AI 기반 처리 프로필은 [지원되는 오디오 또는 비디오 자산](#supported-file-formats-for-transcription) Experience Manager Assets에서 렌디션으로 사용하고 텍스트 스크립트(.vtt 파일)는 원래 자산이 있는 동일한 폴더에 저장합니다. 따라서 사용자가 자산 및 해당 텍스트 표현물을 검색하고 찾기가 쉬워집니다.

이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]** 을(를) 클릭하고 **[!UICONTROL 만들기]** 단추를 클릭하여 오디오 및 비디오 파일의 변환을 생성할 AI 기반 처리 프로필을 만듭니다. 기본적으로 처리 프로필 페이지에는 이미지, 비디오 및 사용자 지정 탭을 세 개만 반영합니다. 하지만, **[!UICONTROL 콘텐츠 AI]** 구성한 경우 탭이 표시됩니다 [!DNL Azure Media Services] 다음 위치에서 [!DNL Experience Manager Assets] 인스턴스. 확인 [!DNL Azure] 자격 증명이 표시되지 않으면 **[!UICONTROL 콘텐츠 AI]** 처리 프로필을 만드는 동안 탭합니다.

에서 **[!UICONTROL 콘텐츠 AI]** 탭에서 을(를) 클릭합니다. **[!UICONTROL 새로 추가]** 변환을 구성하는 단추입니다. 여기에서 드롭다운 목록에서 파일 유형을 선택하여 스크립트를 생성할 파일 형식(MIME 유형)을 포함하거나 제외할 수 있습니다. 다음 그림에서 지원되는 모든 오디오 및 비디오 파일이 포함되고 텍스트 파일은 제외됩니다.

를 활성화합니다 **[!UICONTROL 동일한 디렉터리에 VTT 텍스트 만들기]** 를 전환하여 원본 자산이 있는 동일한 폴더에 텍스트 변환(.vtt 파일)을 만들고 저장합니다. 다른 표현물은 이 설정에 관계 없이 기본 DAM 자산 처리 워크플로우에 의해 생성됩니다.

![configure-transcription-service](assets/configure-transcription-profile.png)

다음 그림은 Experience Manager Assets에서 만든 사용자 지정 비디오 프로필에 대해 자세히 설명합니다.

![configure-transcription-service](assets/video-processing-profile.png)

비디오 프로필에는 다음과 같은 사용자 지정 구성도 포함되어 있습니다. 자세한 내용은 [프로필 설명서 처리](/help/assets/asset-microservices-configure-and-use.md) 사용자 지정 처리 프로필을 만드는 방법에 대한 자세한 내용을 참조하십시오.

![configure-transcription-service](assets/video-processing-profile2.png)

이제 이 비디오 프로필에서 전사자를 구성하겠습니다. 로 이동합니다 **[!UICONTROL 콘텐츠 AI]** 탭을 클릭하고 **[!UICONTROL 새로 추가]** 버튼을 클릭합니다. 모든 오디오 및 비디오 파일을 포함하고 이미지 및 애플리케이션 파일을 제외합니다. 를 활성화합니다 **[!UICONTROL 동일한 디렉터리에 VTT 텍스트 만들기]** 구성을 전환하고 저장합니다.

![configure-transcription-service](assets/video-processing-profile1.png)

처리 프로필이 오디오 및 비디오 파일 전송을 위해 구성되면 다음 방법 중 하나를 사용하여 이 처리 프로필을 폴더에 적용할 수 있습니다.

* 에서 처리 프로필 정의 선택 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**, 및 사용 **[!UICONTROL 폴더에 프로필 적용]** 작업. 컨텐츠 브라우저를 사용하면 특정 폴더로 이동하고, 폴더를 선택하고, 프로필 애플리케이션을 확인할 수 있습니다.
* 자산 사용자 인터페이스에서 폴더를 선택하고 을(를) 클릭합니다 **[!UICONTROL 속성]** 폴더 속성을 여는 작업입니다. 을(를) 클릭합니다. **[!UICONTROL 자산 처리]** 탭에서 폴더에 대한 적절한 처리 프로필을 선택합니다 **[!UICONTROL 처리 프로필]** 목록. 변경 사항을 저장하려면 **[!UICONTROL 저장 및 닫기]**.

   ![configure-transcription-service](assets/video-processing-profile3.png)

* 사용자는 자산 사용자 인터페이스에서 폴더 또는 특정 자산을 선택하여 처리 프로필을 적용한 다음 을 선택할 수 있습니다 **[!UICONTROL 자산 재처리]** 옵션을 선택합니다.

>[!TIP]
>하나의 처리 프로필만 폴더에 적용할 수 있습니다.
>
>처리 프로필이 폴더에 적용되면, 이 폴더 또는 해당 하위 폴더에 업로드된 모든 새 자산(또는 업데이트됨)이 구성된 추가 처리 프로필을 사용하여 처리됩니다. 이 처리에는 표준 기본 프로필 외에도 추가됩니다.

>[!NOTE]
>
>폴더에 적용된 처리 프로필은 전체 트리에 대해 작동하지만 하위 폴더에 적용된 다른 프로필과 함께 오버라이드할 수 있습니다.
>
>자산을 폴더에 업로드하면 Experience Manager은 포함된 폴더의 속성과 통신하여 처리 프로필을 식별합니다. 적용되지 않으면 처리 프로필이 적용되도록 계층의 상위 폴더가 선택됩니다.


## 오디오 또는 비디오 자산의 전사 생성 {#generate-transcription}

비디오 자산을 처리할 때 [AI 기반 처리 프로필](#configure-processing-profile-for-transcription) 는 텍스트 스크립트(.vtt 파일)를 동일한 폴더의 원래 자산과 함께 표현물로 자동으로 생성합니다.

![configure-transcription-service](assets/transcript1.png)

원본 비디오 자산의 표현물에 액세스하여 텍스트 스크립트를 볼 수도 있습니다. 에 액세스하려면 **[!UICONTROL 표현물]** 패널에서 원래 비디오 자산을 선택하고 왼쪽 레일을 엽니다. 텍스트 변환(.vtt 파일)이 **[!UICONTROL TRANSCRIPTVTT]** 머리.

![configure-transcription-service](assets/transcript.png)

텍스트 스크립트(.vtt 텍스트 파일)는 폴더에서 직접 또는 **[!UICONTROL 표현물]** 자산의 모든 표현물을 다운로드하여 원래 자산의 패널입니다.

현재 Experience Manager은 기본적으로 VTT 파일의 전체 텍스트 미리 보기 또는 편집을 지원하지 않습니다. 그러나 텍스트 스크립트 변환을 다운로드하고 텍스트 편집기를 사용하여 텍스트 스크립트를 편집하거나 확인할 수 있습니다. 텍스트 스크립트는 비디오에서 지정된 타임스탬프에 음성 언어를 텍스트로 반영하며 전환의 신뢰 점수(정확도)가 있습니다.

![configure-transcription-service](assets/transcript-text.png)

## Dynamic Media에서 설명 사용 {#using-transcription-in-dynamic-media}

만약 [구성된 Dynamic Media](/help/assets/dynamic-media/config-dm.md) Experience Manager Assets 인스턴스에서 자산(오디오 또는 비디오 파일)과 텍스트 스크립트(.vtt 파일)를 Dynamic Media에 게시할 수 있습니다. 이렇게 하면 원래 자산(오디오 또는 비디오 파일)과 변환된 표현물(.vtt 파일)이 동일한 폴더의 Dynamic Media에 게시됩니다. Dynamic Media 관리자는 다음을 수행할 수 있습니다 [CC Closed 캡션 경험 활성화](/help/assets/dynamic-media/video.md#adding-captions-to-video) 변환(.vtt 파일)을 사용하는 오디오 또는 비디오 파일의 경우

참고 항목:

* [Dynamic Media 비디오에 CC Closed Caption 추가 방법에 대한 비디오 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html#add-cc-closed-captioning-to-dynamic-media-video)
* [YouTube에 Dynamic Media 비디오 게시](/help/assets/dynamic-media/video.md#publishing-videos-to-youtube)

다음 그림에서 URL은 텍스트 스크립트(.vtt 파일)를 참조하는 캡션 부분을 반영합니다. 이 비디오는 사용 언어(전사된 텍스트)를 **[!UICONTROL 닫힌 캡션]** 비디오의 해당 타임스탬프에서 확인하십시오. 사용자는 **[!UICONTROL CC]** 버튼을 클릭합니다.

![configure-transcription-service](assets/transcript-example.png)

## 전사하도록 지원되는 파일 형식 {#supported-file-format}

다음 오디오 및 비디오 파일 형식이 전사적으로 지원됩니다.

| 지원되는 오디오/비디오 형식 | 확장 |
|----|----|
| FLV(H.264 및 AAC 코덱이 있음) | (.flv) |
| MXF | (.mxf) |
| MPEG2-PS, MPEG2-TS, 3GP | (.ts, .ps, .3gp, .3gpp, .mpg) |
| Windows Media 비디오(WMV)/ASF | (.wmv, .asf) |
| AVI(압축되지 않은 8비트/10비트) | (.avi) |
| MP4 | (.mp4, .m4a, .m4v) |
| Microsoft® 디지털 비디오 기록(DVR-MS) | (.dvr-ms) |
| Matroska/WebM | (.mkv) |
| 물결/물결 | (.wav) |
| QuickTime | (.mov) |


>[!NOTE]
>
>애플리케이션 유형의 자산(오디오 또는 비디오 파일)은 전사 시 지원되지 않습니다.

## 알려진 제한 사항 {#known-limitations}

* 변환 기능은 최대 10분 길이의 비디오에 대해 지원됩니다.
* 비디오 제목은 길이가 80자 미만이어야 합니다.
* 지원되는 파일 크기는 최대 15GB입니다.
* 지원되는 최대 처리 기간은 60분입니다.
* 유료 [!DNL Azure] 계정: 분당 최대 50개의 영화를 업로드할 수 있습니다. 하지만 체험판 계정에서는 분당 최대 5개의 영화를 업로드할 수 있습니다.

## 문제 해결 팁 {#troubleshooting}

에 로그인합니다. [!DNL Azure Media Services] 계정에 동일한 자격 증명(구성에 사용함)을 사용하여 요청 상태를 확인합니다. 연락처 [!DNL Azure] 요청이 성공적으로 처리되지 않는 경우 을 지원합니다.



