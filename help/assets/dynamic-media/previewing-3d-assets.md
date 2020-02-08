---
title: 3D 자산 미리 보기
description: 3D 자산을 미리 보는 방법 살펴보기
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# 3D 자산 미리 보기{#previewing-3d-assets}

Adobe Experience Manager는 제작 프로세스의 일환으로 3D 자산의 업로드, 전달 및 대화형 미리 보기를 지원합니다.

대화형 3D 뷰어는 AEM의 자산 세부 사항 페이지에서 사용할 수 있습니다. 이 뷰어에는 3D 자산을 궤도를 따라 이동하고, 확대/축소하고, 패닝할 수 있는 대화형 카메라 컨트롤 컬렉션이 포함되어 있습니다.

## 지원되는 3D 미리 보기 포맷{#supported-3d-previewing-assets}

대화형 3D 미리 보기는 다음 파일 형식을 지원합니다.

| 3D 파일 확장명 | 파일 포맷 | MIME 유형 | 메모 |
|---|---|---|---|
| GLB | 이진 GL 전송 | model/gltf-binary |  |
| GLTF | GL 전송 형식 | model/gltf+json | 아래 **참고** 자료를 참조하십시오. |
| OBJ | WaveFront 3D 개체 파일 | application/x-tgif |  |
| STL | 입체사진 | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | 통합 전용 지원;미리 보기를 사용할 수 없습니다. |
| USDZ | 범용 장면 설명 Zip 아카이브 | model/vnd.usdz+zip | 통합 전용 지원;미리 보기를 사용할 수 없습니다. |

**참고**:자료가 gLTF 모델의 미리 보기에서 렌더링되지 않는 경우 이름이 적절하게 지정되고 모델과 동일한 루트 폴더의 `textures` 폴더에 있는지 확인합니다. 이 폴더는 다음과 같습니다.

    자산(폴더)
    model.
    gltfmodel.
    binteexits (폴더)
    material_0_baseColor.
    jpegmaterial_0_normal.jpeg

## Performance considerations when you preview 3D assets{#performance-3d-previewing-assets}

자산 세부 사항 보기 페이지에서 3D 자산을 여는 데 걸리는 시간은 대역폭, 이미지 복잡도, 서버 지연 등과 같은 여러 요인에 따라 다릅니다.

또한 워크스테이션, 노트북 또는 모바일 터치 디바이스와 같은 클라이언트 컴퓨터의 기능도 인터랙티브하게 카메라를 조작할 때 고려해야 합니다. 그래픽 성능이 좋은 강력한 시스템에서는 대화형 3D 보기 환경이 좀 더 원활하고 유용할 수 있습니다.

**3D 자산을 미리 보려면**

1. 3D 자산을 AEM에 업로드했는지 확인합니다.
3D [미리 보기](#supported-3d-previewing-assets) 및 자산 [업로드를 위해 지원되는 형식을](/help/assets/manage-digital-assets.md#uploading-assets)참조하십시오.
1. AEM의 탐색 페이지에서 **[!UICONTROL 자산]** > **[!UICONTROL 파일을 누릅니다]**.

   ![탐색 페이지](/help/assets/dynamic-media/assets/navigation-assets.png)

1. 페이지의 오른쪽 위 모서리 근처에 있는 보기 드롭다운 목록에서 카드 **[!UICONTROL 보기를]**&#x200B;탭한 다음 미리 보기할 3D 자산으로 이동합니다.

   ![3D 카드 선택](/help/assets/dynamic-media/assets/3d-card-select.png)
   _카드 보기에서 미리 보기할 3D 자산의 카드를 누릅니다._

1. 3D 자산의 카드를 눌러 자산 세부 사항 보기 페이지에서 엽니다.

   ![인터랙티브한 3D 미리 보기](/help/assets/dynamic-media/assets/3d-preview.png)
   _자산 세부 사항 보기 페이지에서 3D 자산의 대화형 미리 보기._
1. 3D 자산에 대한 자산 세부 사항 보기 페이지에서 다음 중 하나를 수행합니다.
   * **카메라**&#x200B;회전 - 3D 장면 및 개체 주위로 보기를 회전할 수 있습니다.
      * _마우스_:마우스 왼쪽 단추를 클릭하고 드래그합니다.
      * _터치 스크린_:한 손가락으로 누르고 드래그합니다.
   * **카메라**&#x200B;이동—보기를 왼쪽, 오른쪽, 위쪽 또는 아래쪽으로 이동합니다.
      * _마우스_:마우스 오른쪽 단추를 클릭하고 드래그합니다.
      * _터치 스크린_:두 손가락으로 누르고 드래그합니다.
   * **카메라**&#x200B;확대 - 3D 장면 영역 안팎으로 카메라를 확대할 수 있습니다.
      * _마우스_:스크롤 휠입니다.
      * _터치 스크린_:두 손가락으로 집는다.
   * **카메라**&#x200B;다시 입력 - 3D 장면의 개체 지점에 맞게 카메라를 다시 입력합니다.
      * _마우스_:두 번 클릭합니다.
      * _터치 스크린_:두 번 누릅니다.
   * **재설정**- 페이지의 오른쪽 아래 모서리 근처에 있는 재설정 아이콘을 눌러 보기 대상 포인트를 3D 자산의 중심으로 복원합니다. 또한 재설정은 카메라를 더 가깝게 또는 더 멀리 이동하여 에셋을 전체적으로 적절한 보기 크기로 표시합니다.
   * **전체 화면 모드**- 전체 화면 모드로 전환하려면 페이지의 오른쪽 아래에 있는 전체 화면 아이콘을 누릅니다.

1. 완료되면 페이지의 오른쪽 위 모서리 근처에 있는 닫기를 **[!UICONTROL 누릅니다]**.
