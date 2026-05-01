---
title: 승인된 비디오에 비디오 스마트 자르기 적용
description: OpenAPI 기능이 있는 Dynamic Media를 사용하면 Adobe Experience Manager(AEM)에서 승인된 비디오 자산에 대해 비디오 스마트 자르기 출력을 자동으로 생성할 수 있습니다.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: video-smartcrop-dmwoapi
source-git-commit: 8ddd2ade491069e4592becf3b77c04e6bbb2c06a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 2%

---


# 승인된 비디오에 비디오 스마트 자르기 적용 {#apply-video-smart-crops-dmwoapi}

[!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하면 [!DNL Adobe Experience Manager (AEM)]의 비디오 자산에 대해 비디오 스마트 자르기 출력을 자동으로 생성할 수 있습니다. 비디오 스마트 자르기는 비디오 콘텐츠를 분석하고 프레임화를 동적으로 조정하여 주요 주제가 다양한 종횡비와 장치에서 초점을 맞추도록 합니다.

기능이 활성화되고 비디오 자산이 승인되면 비디오 스마트 자르기가 자동으로 생성됩니다

## 시작하기에 앞서 {#prerequisites-for-video-smart-crops}

다음을 확인합니다.

* [!DNL AEM Assets as a Cloud Service]에 액세스.
* 메타데이터 스키마를 편집할 수 있는 권한.
* OpenAPI 기능이 환경에 대해 활성화된 Dynamic Media.
* **[!UICONTROL 승인됨]**(으)로 표시할 수 있는 비디오 자산입니다.

## 비디오에 비디오 스마트 자르기 활성화 {#enable-video-smart-crops}

비디오 스마트 자르기를 활성화하려면 비디오 자산에 사용되는 메타데이터 스키마를 구성합니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.
2. 적용 가능한 메타데이터 스키마를 엽니다(예: **default**).
3. **비디오** 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
4. 새 **[!UICONTROL 드롭다운 필드]**&#x200B;을(를) 추가하고 다음을 구성하십시오.

   * **필드 레이블**: 비디오 스마트 자르기 만들기
   * **속성에 매핑**: `./jcr:content/dam:applyVideoSmartCrop`

5. 다음 값을 수동으로 추가합니다.

   * 예 → true
   * → 없음 false

6. 스키마를 저장합니다.

이제 비디오 자산 메타데이터 양식에서 **비디오 스마트 자르기 만들기** 옵션을 사용할 수 있습니다.

![비디오 Smartcrops 필드 만들기](/help/assets/assets/video-smartcrop-metadata-field.png)

## 승인된 비디오에 비디오 스마트 자르기 적용 {#apply-video-smart-crops}

메타데이터 필드를 활성화하고 자산을 승인하여 비디오 자산에 비디오 스마트 자르기를 적용할 수 있습니다.

다음 단계를 실행합니다.

1. [!DNL Assets View]에서 **[!UICONTROL Assets]**&#x200B;을(를) 선택하고 폴더로 이동합니다.
2. 비디오 자산을 선택합니다.
3. **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.
4. 메타데이터 패널에서 **[!UICONTROL 비디오 스마트 자르기 만들기]**&#x200B;를 찾습니다.
5. 값을 **예**(으)로 설정한 다음 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
6. 에셋 상태를 **[!UICONTROL 승인됨]**(으)로 설정합니다.

에셋이 승인되면 비디오 스마트 자르기 출력이 자동으로 생성됩니다.

## 비디오 스마트 자른 출력 보기 {#view-video-smart-crops}

비디오 스마트 자르기가 생성되면 다음 작업을 수행하십시오.

* 출력은 비디오 재생 중에 사용할 수 있습니다.
* Dynamic Media 뷰어는 장치 및 종횡비에 따라 가장 적절한 자르기를 자동으로 선택합니다.
* 비디오 재생이 동적으로 조정되어 주요 주제가 초점을 맞추게 됩니다.

## 비디오 스마트 자르기 비디오 사용 {#use-video-smart-crops}

다음과 같이 비디오 에셋이 전달되는 모든 곳에서 비디오 스마트 자르기 출력을 사용할 수 있습니다.

* 웹 페이지
* 애플리케이션
* 임베디드 비디오 플레이어

재생 중에 뷰어가 적절한 스마트 자르기를 자동으로 적용합니다.

>[!NOTE]
>
>* 비디오 스마트 자르기는 **승인됨** 비디오 자산에 대해서만 생성됩니다.
>* 자산을 승인하기 전에 **비디오 Smartcrops 만들기** 필드가 **예**(으)로 설정되어 있는지 확인하십시오.
>* 비디오 스마트 자르기는 원본 에셋을 수정하지 않습니다. 자르기 는 재생 중에 동적으로 적용됩니다.