---
title: Experience Manager에서 에셋 승인
description: 에서 에셋을 승인하는 방법 알아보기 [!DNL Experience Manager].
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 1%

---

# 에서 에셋 승인 [!DNL Experience Manager]

브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 제어를 유지합니다. 모든 채널 및 애플리케이션에서 브랜드 일관성을 보장하기 위해 승인된 최신 버전의 자산만 사용할 수 있습니다.

AEM Assets에서 에셋을 승인하여 에셋 관리를 간소화하여 에셋 처리에 대한 통제되고 효율적인 프로세스를 보장할 수 있습니다.

## 시작하기에 앞서 {#pre-requisites}

다음을 편집하려면 AEM Assets as a Cloud Service 액세스 권한 및 권한이 있어야 합니다. **[!UICONTROL 상태 검토]** 에셋에 대한 속성입니다.

## 구성

에서 적용 가능한 메타데이터 스키마를 한 번 업데이트해야 합니다. [!DNL Experience Manager] 에셋을 승인하려면 먼저 다음 기간 동안 이 구성을 건너뛸 수 있습니다. [!DNL Experience Manager Assets]. 메타데이터 스키마를 구성하려면 다음 단계를 따르십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 에셋]** > **[!UICONTROL 메타데이터 스키마]**.
1. 적용 가능한 메타데이터 스키마를 선택하고 **[!UICONTROL 편집]**. <br>다음 **[!UICONTROL 메타데이터 스키마 양식 편집기]** 을 사용하여 열림 **[!UICONTROL 기본]** 강조 표시된 탭입니다.
1. 아래로 스크롤하여 클릭 **[!UICONTROL 상태 검토]**.
1. 다음을 클릭합니다. **[!UICONTROL 규칙]** 오른쪽 패널의 탭입니다.
1. 선택 취소 **[!UICONTROL 편집 비활성화]** 및 클릭 **[!UICONTROL 저장]**.

>[!NOTE]
>
>에셋 또는 폴더에 다른 기본 스키마가 있는 경우 해당 특정 스키마에서 이 업데이트를 수행해야 합니다.

## 에셋 승인 {#approve-assets}

두 가지 모두에서 에셋을 승인할 수 있습니다. [!DNL Experience Manager] 및 [!DNL Experience Manager Assets]. 에서 에셋을 승인하려면 [!DNL Experience Manager], 다음 단계를 수행합니다.

1. 에셋을 선택하고 **[!UICONTROL 속성]** 을 클릭합니다.
1. 다음에서 **[!UICONTROL 기본]** 탭, 아래로 스크롤하여 **[!UICONTROL 상태 검토]**.
1. 검토 상태를 다음으로 변경 **[!UICONTROL 승인됨]**.
   ![이미지](/help/assets/assets/approve-old-ui.png)
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427430)

   마찬가지로 [새 자산 보기](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-organize.html?lang=en#manage-asset-status).

## 자산 일괄 승인 {#bulk-approve-assets}

여러 에셋을 한 번에 빠르게 승인하여 워크플로를 간소화합니다. 자산을 일괄 승인하여 승인 프로세스를 신속하게 진행할 수 있으므로 시간을 절약하고 생산성을 향상시킬 수 있습니다.
<br>에서 일괄 에셋을 승인하려면 다음 단계를 따르십시오 [!DNL Experience Manager]:

1. 작성 환경(https://author-pXXX-eYYY.adobeaemcloud.com)에 폴더를 만듭니다. 바꾸기 _XXX_ (프로그램 ID 및 _YYY_ (Experience Manager의 환경 ID 포함)
1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 에셋]** > **[!UICONTROL 메타데이터 프로필]**.
1. 클릭 **[!UICONTROL 만들기]** 페이지의 오른쪽 상단에 있습니다.
1. 프로필 제목 추가 및 클릭 **[!UICONTROL 만들기]**. 메타데이터 프로필이 정상적으로 생성되었습니다.
1. 새로 만든 메타데이터 프로필을 선택하고 **[!UICONTROL 편집 _마._]**. <br>다음&#x200B;**[!UICONTROL 메타데이터 프로필 편집]**양식이 로 열립니다.**[!UICONTROL 기본]**강조 표시된 탭입니다.
1. 드래그 앤 드롭 **[!UICONTROL 한 줄 텍스트 필드]** 다음에서 **[!UICONTROL 양식 작성]** 섹션에 있는 마지막 항목이 될 필요가 없습니다.
1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널:
   1. 변경 **[!UICONTROL 필드 레이블]** 끝 _승인된 에셋_.
   1. 업데이트 **[!UICONTROL 속성에 매핑]** 끝 _./jcr:content/metadata/dam:status_.
   1. 기본값을 다음으로 변경 _승인됨_.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 다음에서 **[!UICONTROL 메타데이터 프로필]** 페이지에서 새로 만든 메타데이터 프로필을 선택합니다.
1. 클릭 **[!UICONTROL 폴더에 메타데이터 프로필 적용]** 맨 위의 작업 표시줄에서
1. 승인해야 하는 폴더를 선택하고 **[!UICONTROL 적용]**.
   <br> 전체 폴더에 대한 권한이 승인을 위해 설정되고 이 폴더에 업로드된 모든 자산이 자동으로 승인됩니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3427431)

>[!NOTE]
> 
>이 접근 방법에서는 폴더에 새로 생성된 에셋을 승인합니다. 폴더의 기존 에셋에 대해서는 해당 에셋을 수동으로 선택하고 승인해야 합니다. <br> 또는 **[!UICONTROL 재처리]** 메타데이터 프로필의 변경 사항을 이전 에셋에 적용하는 옵션입니다.
