---
title: 에셋 업로드 제한 사항 구성
description: MIME 유형에 따라 사용자가 업로드할 수 있는 자산 유형을 제한하도록 Adobe Experience Manager Assets를 구성합니다. 원치 않는 포맷과 악성 파일이 우발적으로 업로드되는 것을 방지할 수 있습니다.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
source-git-commit: 472b670623e77957ff9a366359ebef8c6c0604ae
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 4%

---

# 에셋 업로드 제한 사항 구성 {#configure-asset-upload-restrictions}

MIME 유형에 따라 사용자가 업로드할 수 있는 자산 유형을 제한하도록 Adobe Experience Manager Assets를 구성할 수 있습니다.

>[!IMPORTANT]
>
>기본적으로 Experience Manager Assets에서는 사용자가 모든 MIME 유형의 자산을 업로드할 수 있습니다. 그러나 특정 MIME 유형의 파일만 업로드하도록 사용자가 제한하도록 설정을 구성할 수 있습니다.

## 사전 요구 사항 {#prerequisites-asset-upload-restrictions}

자산 업로드 제한을 구성하려면 관리자 권한이 있어야 합니다.

## 자산 업로드에 제한 적용 {#apply-restrictions-asset-uploadsssssss}

구성하려면 [!DNL Experience Manager] 특정 MIME 유형의 파일을 업로드하도록 사용자를 제한하려면:

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 자산 구성]**.

1. 클릭 **[!UICONTROL 업로드 제한]**.

1. 클릭 **[!UICONTROL 추가]** 허용되는 MIME 유형을 정의하려면

1. 텍스트 상자에 MIME 유형을 지정합니다. 을(를) 클릭합니다 **[!UICONTROL 추가]** 허용되는 추가 MIME 유형을 다시 지정합니다. 을 클릭할 수도 있습니다 ![아이콘 삭제](assets/delete-icon.svg) 목록에서 모든 MIME 유형을 삭제하려면 다음을 수행하십시오.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

**예제 1: 모든 이미지 및 PDF 파일을 Experience Manager Assets에 업로드할 수 있습니다**

모든 형식의 이미지를 업로드하고 Experience Manager Assets에 PDF 파일을 업로드하도록 허용하려면 다음 설정을 수행합니다.

![에셋 업로드 제한 사항](assets/asset-upload-restrictions.png)

`image/*` mime 유형으로 모든 형식의 이미지를 업로드할 수 있습니다. `application/pdf` mime 유형으로 Experience Manager Assets에 PDF 파일을 업로드할 수 있습니다.

**예제 2: Experience Manager Assets에 특정 이미지 형식 업로드 허용**

허용되는 MIME 유형에 특정 이미지 형식을 추가하고 다른 모든 자산 형식 업로드를 제한하려면 다음 설정을 수행하십시오.

![자산 제한](assets/asset-restrictions.png)

이미지에 표시된 설정에 따라 .JPG, .PNG 및 .GIF 형식의 이미지를 Experience Manager Assets에 업로드할 수 있습니다.
