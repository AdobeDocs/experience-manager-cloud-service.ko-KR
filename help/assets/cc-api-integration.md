---
title: Creative Cloud 통합을 위한 컨텐츠 자동화
description: Creative Cloud 통합을 사용하여 자산의 변형 생성
contentOwner: AG
feature: Upload,Asset Processing,Publishing,Asset Compute Microservices,Workflow
role: User,Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: 87306ae90f6411d2d4e48f3afdb66e5e848073fe
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# [!DNL Adobe Creative Cloud] 통합을 사용하여 자산의 변형을 생성합니다. {#content-automation}

컨텐츠 자동화 추가 기능은 [!DNL Adobe Experience Manager Assets]을 [!DNL Cloud Service] 및 [!DNL Adobe Creative Cloud] API로 통합하여 자산을 규모에 맞게 창의적으로 처리합니다. [!DNL Experience Manager] 는 클라우드 기반  [자산 ](/help/assets/asset-microservices-overview.md) 마이크로 서비스를 사용하여  [!DNL Adobe Creative Cloud] 기능을 사용하고 자산 작성 및 미디어 처리를 자동화합니다.

[!DNL Adobe Photoshop] 및 [!DNL Adobe Lightroom]에서 자산을 편집하려면 [!DNL Experience Manager Assets]에서 자산을 다운로드하여 편집하고 다시 업로드할 필요가 없습니다. [!DNL Experience Manager]에서 처리 프로필을 만들고 구성하고, 프로필을 폴더에 적용하고, 자산을 폴더에 업로드합니다. 업로드된 자산은 처리 프로필을 기반으로 다시 처리되며, 이러한 자산의 변형을 받습니다. 일관되고 간편하게 일괄 처리를 수행할 수 있으므로 수작업을 줄일 수 있고 컨텐츠 속도를 높일 수 있으므로 탁월한 크리에이티브 기술이 필요하지 않습니다. 또한 개발자와 파트너는 이러한 API에 직접 액세스하여 자산 마이크로서비스를 확장하고 사용자 지정 논리를 포함할 수 있습니다.

사용자는 처리 프로필을 만들어 자산에서 다음과 같은 크리에이티브 작업을 자동화할 수 있습니다.

* **자동 톤**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 고유한 속성에 따라 지능적으로 빛과 색상을 수정합니다.

* **자동 직립**: 인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 기울어진 원근감을 수정합니다. 예를 들어 수준 범위를 만듭니다.

   ![자동 톤](/help/assets/assets/content-automation-autotone.png)

   *그림: 자동 톤 및 자동 맞춤은 기울어진 이미지를 개선하는 데 도움이 됩니다.*

* **Lightroom 사전 설정**: 사용자 정의 사전 설정을 사용하여 이미지에 사용자 정의 모양을 적용하여 일관된 모양을 얻을 수 있습니다.

   ![Lightroom 사전 설정](/help/assets/assets/content-automation-lrpresets.png)

   *그림: Adobe Lightroom 사전 설정은 많은 이미지에 일관된 방식으로 이미지 품질을 개선합니다.*

* **이미지 컷아웃**: 인공 지능을 사용하여 돌출된 객체 주위에 선택 영역을 만들고 단일 명령으로 배경을 제거합니다.

   ![배경 제거 및 사진 이미지 잘라내기](/help/assets/assets/content-automation-backgroundremove.png)

* **이미지 마스크**: 인공 지능을 사용하여 하나의 명령으로 침목 객체 주위에 마스크를 만듭니다.

   ![AI를 사용하여 이미지 마스크](/help/assets/assets/content-automation-mask.png)

* **Photoshop 작업**: 파일 또는  [!DNL Adobe Photoshop] 파일 배치에 일련의 작업을 적용합니다.

   ![Photoshop 작업](/help/assets/assets/content-automation-psactions.png)

* **스마트 개체 바꾸기**: PSD 파일 내에 적용된 모든 효과 및 조정을 그대로 유지하면서 이미지를 교환하도록 하여 규모에 맞게 개인화를 수행합니까?

   ![개체를 깔끔하게 바꾸기](/help/assets/assets/content-automation-objectreplace.png)

## 처리 프로필을 사용하여 크리에이티브 자산을 일괄적으로 편집 {#process-assets}

처리 프로필을 사용하여 변형을 자동으로 만들려면 다음 단계를 수행합니다.

1. 라이센스를 받으려면 [고객 지원 Adobe](https://experienceleague.adobe.com/#support)에 문의하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**&#x200B;로 이동합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하고 **[!UICONTROL 이름]**&#x200B;을 지정합니다.

1. **[!UICONTROL Creative]** 탭을 선택하고 출력 폴더를 지정하고 **[!UICONTROL 새로 추가]**&#x200B;를 선택하여 크리에이티브 구성을 추가합니다.

1. **[!UICONTROL 표현물 이름]**(또는 출력 이름), **[!UICONTROL 확장]**(또는 파일 유형)을 제공하고, **[!UICONTROL 품질]**(또는 출력 매개 변수)을 선택하고, **[!UICONTROL 포함]** 및 **[!UICONTROL 제외]** MIME 유형 목록(또는 입력 자산 필터)을 선택한 다음 필요한 크리에이티브 작업을 선택합니다.

   ![ 처리 프로필의  [!UICONTROL Creativeab]](assets/creative-processing-profile.png)

1. 일부 작업에는 추가 매개 변수(자산)가 필요합니다. 필요한 경우 이러한 추가 매개 변수에 대한 값을 제공합니다.

1. 동일한 처리 프로필의 일부로 크리에이티브 작업을 더 추가하거나 프로필을 저장합니다.

1. 처리 프로필을 폴더에 적용합니다. 폴더의 **[!UICONTROL 속성]** 페이지에서 **[!UICONTROL 자산 처리]**&#x200B;를 선택하고 적용할 처리 프로필을 선택합니다.

처리 프로필을 DAM 폴더에 적용하면 이 폴더에서 업로드하거나 업데이트된 모든 자산이 표준 처리 외에도 정의된 작업을 실행합니다. 하위 폴더는 상위 폴더에 적용된 프로필과 동일한 프로필을 상속합니다. 사용자는 이 상속을 무시할 수 있습니다.

기존 자산을 처리하려면 자산을 선택하고 **[!UICONTROL 재처리]** 옵션을 선택한 다음 필요한 처리 프로필을 선택합니다.

## 팁 및 제한 사항 {#limitations-best-practices}

* [!DNL Experience Manager] 자산 처리를 환경당 분당 300개의 요청 및 조직당 분당 700개의 요청으로 제한합니다.
* 파일 크기는 [!DNL Adobe Photoshop] API 작업의 경우 4GB, [!DNL Adobe Lightroom] 작업의 경우 1GB로 제한됩니다.

>[!MORELIKETHIS]
>
>* [처리 프로필을 통해 자산 마이크로서비스 를 구성하고 사용합니다](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md) [!DNL Experience Manager] 과 통합됩니다.
>* [자산 마이크로서비스를 사용한 자산 수집 및 처리: 개요](/help/assets/asset-microservices-overview.md).

