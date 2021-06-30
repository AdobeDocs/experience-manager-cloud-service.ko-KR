---
title: Creative Cloud 통합을 위한 컨텐츠 자동화
description: Creative Cloud 통합을 사용하여 자산의 변형 생성
contentOwner: AG
feature: 업로드,자산 처리,게시,Asset compute 마이크로서비스,워크플로우
role: Business Practitioner,Administrator
source-git-commit: ffca94ef8d93cf95011d7e3128c49929f69cdc28
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# [!DNL Adobe Creative Cloud] 통합을 사용하여 자산의 변형을 생성합니다. {#content-automation}

컨텐츠 자동화 추가 기능은 Experience Manager Assets를 Cloud Service으로 통합하고 Adobe Creative Cloud API를 통합하여 자산을 규모에 맞게 창의적으로 처리합니다. Experience Manager은 클라우드 기반 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용하여 Adobe Creative Cloud 기능을 활용하고 자산 작성 및 미디어 처리를 자동화합니다.

[!DNL Adobe Photoshop] 및 [!DNL Adobe Lightroom]에서 자산을 편집하려면 을(를) 다운로드하여 편집하고 [!DNL Experience Manager Assets]에 업로드할 필요가 없습니다. 처리 프로필을 만들고 구성하고, 프로필을 폴더에 적용하고, 자산을 폴더에 업로드하기만 하면 됩니다. 폴더에 업로드된 자산은 해당 자산의 다른 변형을 만들기 위해 처리됩니다. 자산을 일관되고 간편하게 일괄 처리 및 편집하면 수동 작업이 절약되고 컨텐츠 속도가 빨라집니다. 또한 개발자 및 파트너는 이러한 API에 직접 액세스하여 자산 마이크로서비스를 확장하고 사용자 지정 논리를 포함할 수 있습니다.

사용자는 처리 프로필을 만들어 자산에서 다음과 같은 크리에이티브 작업을 자동화할 수 있습니다.

* **자동 톤**:인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 고유한 속성에 따라 지능적으로 빛과 색상을 수정합니다.
* **자동 직립**:인공 지능을 사용하여 이미지의 내용을 분석하고 이미지의 기울어진 관점을 수정합니다. 예를 들어 수준 범위를 만듭니다.
* **Lightroom 사전 설정**:사용자 정의 사전 설정을 사용하여 이미지에 사용자 정의 모양을 적용하여 일관된 모양을 얻을 수 있습니다.
* **이미지 컷아웃**:인공 지능을 사용하여 돌출된 객체 주위에 선택 영역을 생성하고 하나의 명령으로 배경을 제거합니다.
* **이미지 마스크**:인공 지능을 활용하여 하나의 명령으로 돌출형 객체 주위에 마스크를 생성합니다.
* **Photoshop 작업**:파일 또는 파일 배치에 일련의 작업(Photoshop)을 적용합니다.
* **스마트 개체 바꾸기**:PSD 파일 내에 적용된 모든 효과와 조정을 그대로 유지하면서 이미지를 교환하도록 하여 규모에 맞게 개인화를 수행합니다.

## 처리 프로필을 사용하여 자산 처리 {#process-assets}

처리 프로필을 사용하여 변형을 자동으로 만들려면 다음 단계를 수행합니다.

1. 라이센스를 받으려면 [고객 지원 센터 Adobe](https://experienceleague.adobe.com/#support)에 문의하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 처리 프로필]**&#x200B;로 이동합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하고 **[!UICONTROL 이름]**&#x200B;을 지정합니다.

1. **[!UICONTROL Creative]** 탭을 선택하고 출력 폴더를 지정하고 **[!UICONTROL 새로 추가]**&#x200B;를 선택하여 크리에이티브 구성을 추가합니다.

1. **[!UICONTROL 표현물 이름]**(또는 출력 이름), **[!UICONTROL 확장]**(또는 파일 유형)을 제공하고, **[!UICONTROL 품질]**(또는 출력 매개 변수)을 선택하고, MIME 유형 목록 포함 및 제외(또는 입력 자산 필터)를 선택한 다음 필요한 크리에이티브 작업을 선택합니다.

1. 일부 작업에는 추가 매개 변수(자산)가 필요합니다. 필요한 경우 이러한 추가 매개 변수에 대한 값을 제공합니다.

1. 동일한 처리 프로필의 일부로 크리에이티브 작업을 더 추가하거나 프로필을 저장합니다.

1. 처리 프로필을 폴더에 적용합니다. 폴더의 **[!UICONTROL 속성]** 페이지에서 **[!UICONTROL 자산 처리]**&#x200B;를 선택하고 적용할 처리 프로필을 선택합니다.

처리 프로필이 DAM 폴더에 적용되면, 이 폴더에서 업로드되거나 업데이트된 모든 자산이 표준 처리 외에도 정의된 작업을 실행합니다. 하위 폴더는 상위 폴더에 적용된 프로필과 동일한 프로필을 상속합니다. 사용자는 이 상속을 무시할 수 있습니다.

기존 자산을 처리하려면 자산을 선택하고 **[!UICONTROL 재처리]** 옵션을 선택한 다음 필요한 처리 프로필을 선택합니다.

## 팁 및 제한 사항 {#limitations-best-practices}

* [!DNL Experience Manager] 자산 처리를 환경당 분당 300개의 요청 및 조직당 분당 700개의 요청으로 제한합니다.
* 파일 크기는 [!DNL Adobe Photoshop] API 작업의 경우 4GB, [!DNL Adobe Lightroom] 작업의 경우 1GB로 제한됩니다.

>[!MORELIKETHIS]
>
>* [처리 프로필을 통해 자산 마이크로서비스 를 구성하고 사용합니다](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager]  [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md)과 통합됩니다.

