---
title: 디지털 자산에 워터마크 추가
description: 워터마크 기능을 사용하여 디지털 워터마크를 자산에 추가하는 방법을 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# 원본에 쓰기 {#watermarking}

AEM(Adobe Experience Manager) 자산의 워터마크 기능을 사용하면 디지털 워터마크를 자산에 추가할 수 있으므로, 사용자는 자산의 신뢰성 및 저작권 소유권을 확인할 수 있습니다. AEM Assets는 PNG 및 JPEG 파일에서 워터마크로 사용할 텍스트를 지원합니다.

자산에 워터마크를 적용하려면 DAM 자산 업데이트 워크플로우에서 워터마크 단계를 추가하십시오.

1. AEM 로고를 탭/클릭하고 도구 > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델로]** 이동합니다 ****.
1. 워크플로우 모델 페이지에서 DAM 자산 업데이트 **[!UICONTROL 워크플로우를 선택하고]** 편집을 **[!UICONTROL 클릭합니다]**.

1. 사이드 패널에서 워터마크 **[!UICONTROL 추가]** 단계를 DAM 자산 업데이트 워크플로우로 드래그합니다.

<!--  ![Darg add watermark step in the DAM update asset workflow](assets/add_watermark_step_aem_assets.png) -->

>[!NOTE]
>
>[프로세스 축소판] 단계 전에 [워터마크 추가] 단계를 배치합니다.

1. 워터마크 **[!UICONTROL 추가]** 단계를 열어 속성을 표시합니다.
1. 인수 **[!UICONTROL 탭에서]** 텍스트, 글꼴 유형, 크기, 색상, 위치, 방향 등 다양한 필드에 유효한 값을 지정합니다. 변경 내용을 확인하려면 완료 아이콘을 탭/클릭합니다.

<!--   ![Provide the arguments in the add watermark step in Assets](assets/arguments_add_watermark_aem_assets.png) -->

1. 워터마크 **[!UICONTROL 단계를 사용하여 DAM 자산]** 업데이트 워크플로우를 저장합니다.
1. 자산 사용자 인터페이스에서 샘플 자산을 업로드합니다. 위 단계에서 구성한 위치에 워터마크가 글꼴 크기, 색상 등과 함께 나타납니다.
