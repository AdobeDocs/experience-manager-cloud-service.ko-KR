---
title: Adobe Express과 AEM Assets 기본 통합
description: Adobe Express과 AEM Assets 기본 통합을 사용하면 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 에셋에 직접 액세스할 수 있습니다.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
source-git-commit: 8bbf9a2ba8f708a5a03d11bc0388d39b32d4c7b3
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 30%

---

# Adobe Express과 기본 통합 {#native-integration-adobe-express}

AEM Assets은 기본적으로 Adobe Express과 통합되어 있으므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 에셋에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Express 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다. 통합은 다음과 같은 주요 이점을 제공합니다.

* AEM에서 새 자산을 편집하고 저장하여 콘텐츠 재사용을 개선했습니다.

* 새 에셋을 만들거나 기존 에셋의 새 버전을 만드는 데 드는 전반적인 시간과 노력이 감소했습니다.

## 사전 요구 사항 {#prerequisites}

AEM Assets 내에서 Adobe Express 및 하나 이상의 환경에 액세스할 수 있는 권한. 환경은 Assets as a Cloud Service 또는 Assets Essentials 내에 있는 저장소 중 하나일 수 있습니다.


## Adobe Express 편집기 내 AEM Assets 사용 {#use-aem-assets-in-express}

Adobe Express 편집기에서 AEM Assets을 사용하려면 다음 단계를 수행하십시오.

1. Adobe Express 웹 애플리케이션을 엽니다.

1. 새 템플릿 또는 프로젝트를 로드하거나 에셋을 만들어 새 빈 캔버스를 엽니다.

1. 클릭 **[!UICONTROL 에셋]** 왼쪽 탐색 창에서 사용할 수 있습니다. Adobe Express은 루트 수준에서 사용할 수 있는 에셋 및 폴더 목록과 함께 액세스할 수 있는 저장소 목록을 표시합니다.

1. 저장소에서 에셋을 찾아보거나 검색하여 캔버스로 드래그 앤 드롭합니다. 파일 유형, MIME 유형 및 차원과 같은 다양한 사용 가능한 필터를 사용하여 에셋을 필터링할 수 있습니다.

   ![Assets 추가 기능에서 자산 포함](assets/adobe-express-native-integration.png)


## AEM Assets에 Adobe Express 프로젝트 저장 {#save-express-projects-in-assets}

Express 캔버스에 해당 수정 사항을 통합한 후에 AEM Assets 저장소에 저장할 수 있습니다.

1. 클릭 **[!UICONTROL 공유]** 을(를) 열려면 **[!UICONTROL 공유]** 대화 상자.

   ![AEM에 자산 저장](assets/adobe-express-share.png)

1. 선택 **[!UICONTROL AEM Assets]** 다음에서 **[!UICONTROL 스토리지]** 오른쪽 창에서 섹션을 사용할 수 있습니다. Adobe Express에 업로드 대화 상자가 표시됩니다.
1. 자산의 이름 및 형식을 지정합니다. 캔버스의 콘텐츠를 PNG 또는 JPEG 포맷 유형으로 저장할 수 있습니다.

1. **[!UICONTROL 위치]** 필드에 인접한 폴더 아이콘을 클릭하고 자산을 저장해야 하는 위치로 이동한 다음 **[!UICONTROL 선택]**&#x200B;을 클릭합니다. 폴더 이름이 **[!UICONTROL 위치]** 필드에 표시됩니다.

   ![AEM에 자산 저장](assets/adobe-express-upload.png)

1. 선택 사항: 다음을 사용하여 업로드에 대한 캠페인 메타데이터를 추가할 수 있습니다. **[!UICONTROL 프로젝트 또는 캠페인 이름]** 필드. 기존 이름을 사용하거나 새 이름을 만들 수 있습니다. 업로드할 여러 프로젝트 또는 캠페인 이름을 정의할 수 있습니다. 이름을 입력하는 동안 대화 상자 내의 아무 곳이나 클릭하거나 `,` (쉼표) 키를 눌러 이름을 등록합니다.

   업로드한 에셋에 대해 향상된 Adobe 경험을 만들 뿐만 아니라 나머지 필드에 값을 지정하는 것이 좋습니다.
1. 마찬가지로 다음에 대한 값을 정의합니다 **[!UICONTROL 키워드]** 및 **[!UICONTROL 채널]** 필드.

1. **[!UICONTROL 업로드]**&#x200B;를 클릭하여 자산을 AEM Assets에 업로드합니다.




## 제한 사항 {#limitations}

여러 저장소의 자산으로 문서를 저장할 때 두 개 이상의 Assets 저장소에 액세스할 수 있는 일부 사용자가 경험하는 알려진 버그가 있습니다.
