---
title: 3D 에셋 미리보기
description: Experience Manager에서 3D 자산을 미리 보는 방법을 알아봅니다.
feature: 3D Assets
role: User
exl-id: e873bd25-f841-4063-824f-7e48f40bb678
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 10%

---

# Adobe Experience Manager에서 3D 자산 미리 보기{#previewing-3d-assets}

Experience Manager은 작성 프로세스의 일부로 3D 자산 업로드, 전달 및 대화형 미리 보기를 지원합니다.

대화형 3D 뷰어는 Experience Manager의 자산 세부 사항 페이지에서 사용할 수 있습니다. 이 뷰어에는 3D 에셋을 궤도를 따라 이동하고, 확대/축소하고, 패닝할 수 있는 대화형 카메라 컨트롤 컬렉션이 포함되어 있습니다.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md). -->

## Experience Manager에서 3D 미리 보기에 대해 지원되는 형식{#supported-3d-previewing-assets}

Experience Manager의 대화형 3D 미리 보기는 다음 파일 형식을 지원합니다.

| 3D 파일 확장명 | 파일 형식 | MIME 유형 | 메모 |
|---|---|---|---|
| GLB | 이진 GL 전송 | model/gltf-binary |  |
| GLTF | GL 전송 형식 | model/gltf+json | 자세한 내용은 **참고** 아래의 제품에서 사용할 수 있습니다. |
| OBJ | WaveFront 3D 개체 파일 | application/x-tgif |  |
| STL | 입체광조형 | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | 수집만 지원 미리 보기를 사용할 수 없습니다. |
| USDZ | 범용 장면 설명 Zip 아카이브 | model/vnd.usdz+zip | 수집만 지원 미리 보기를 사용할 수 없습니다. |

>[!NOTE]
>
>자료가 gLTF 모델의 미리 보기에서 렌더링되지 않는 경우 재료 이름이 올바르게 지정되었는지 확인합니다. `textures` 모델과 동일한 루트 폴더의 폴더(다음과 유사):

    자산(폴더)
    model.gltf
    model.bin
    텍스처(폴더)
    material_0_baseColor.jpeg
    material_0_normal.jpeg

## Experience Manager에서 3D 자산을 미리 볼 때의 성능 고려 사항{#performance-3d-previewing-assets}

자산 세부 사항 보기 페이지에서 3D 자산을 여는 데 걸리는 시간은 대역폭, 이미지 복잡성, 서버에 대한 지연 시간과 같은 몇 가지 요인에 따라 다릅니다.

또한 워크스테이션, 노트북 또는 모바일 터치 장치와 같은 클라이언트 컴퓨터의 기능도 대화식으로 카메라를 조작할 때 고려해야 합니다. 그래픽 성능이 좋은 강력한 시스템에서는 대화형 3D 보기 환경이 좀 더 원활하고 유용할 수 있습니다.

**Experience Manager에서 3D 자산을 미리 보려면 다음을 수행하십시오.**

1. 3D 자산을 Experience Manager에 업로드했는지 확인합니다.
자세한 내용은 [3D 미리 보기에 대해 지원되는 형식](#supported-3d-previewing-assets) 및 [자산 업로드](/help/assets/manage-digital-assets.md#uploading-assets).
1. Experience Manager에서 **[!UICONTROL 탐색]** 페이지로 이동하여 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**.

   ![탐색 페이지](/help/assets/dynamic-media/assets/navigation-assets.png)

1. 페이지의 오른쪽 위 모서리 근처에 있는 보기 드롭다운 목록에서 을(를) 선택합니다 **[!UICONTROL 카드 보기]**&#x200B;를 클릭한 다음 미리 보려는 3D 자산으로 이동합니다.

   ![3D 카드 선택](/help/assets/dynamic-media/assets/3d-card-select.png)
   _카드 보기에서 미리 보려는 3D 자산의 카드를 선택합니다._

1. 3D 자산의 카드를 선택합니다.

   ![대화형 3D 미리 보기](/help/assets/dynamic-media/assets/3d-preview.png)
   _자산 세부 사항 보기 페이지에서 3D 자산의 대화형 미리 보기._
1. 3D 자산에 대한 자산 세부 사항 보기 페이지에서 다음 중 하나를 수행합니다.

   | 보기 | 설명 | 마우스 동작 | 터치 화면 작업 |
   | --- | --- | --- | --- |
   | **카메라 회전** | 3D 장면 및 개체 주위로 보기를 궤도 회전합니다. | 왼쪽 클릭 + 드래그. | 한 손가락으로 누르기 + 드래그. |
   | **카메라 팬** | 왼쪽, 오른쪽, 위 또는 아래로 뷰를 패닝합니다. | 마우스 오른쪽 단추 클릭 + 드래그. | 두 손가락으로 누르기 + 드래그. |
   | **카메라 확대/축소** | 3D 장면 영역 내외로 이동합니다. | 스크롤 휠입니다. | 두 손가락에 끼어요 |
   | **카메라 다시 입력** | 3D 장면에서 개체의 한 지점으로 카메라를 다시 입력합니다. | 두 번 클릭. | 두 번 탭하세요. |
   | **재설정** | 페이지의 오른쪽 아래 모서리 근처에 있는 재설정 아이콘을 선택하여 보기 대상 포인트를 3D 자산의 중심으로 복원합니다. 또한 재설정을 수행하면 카메라가 더 가깝거나 더 멀게 이동되어 자산이 전체적으로 적절한 보기 크기로 표시됩니다. |  |  |
   | **전체 화면 모드** | 전체 화면 모드로 전환하려면 페이지의 오른쪽 아래 모서리에서 전체 화면 아이콘을 선택합니다. |  |  |

1. 완료되면 페이지의 오른쪽 위 모서리 근처에 있는 를 선택합니다. **[!UICONTROL 닫기]**.
