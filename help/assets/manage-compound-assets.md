---
title: 복합 자산 관리
description: Adobe Indesign, Adobe Illustrator 및 Adobe Photoshop 파일에서 AEM 자산에 대한 참조를 만드는 방법을 알아봅니다. 또한 페이지 뷰어 기능을 사용하여 PDF, INDD, PPT, PPTX 및 AI 파일을 비롯한 여러 페이지 파일의 개별 페이지를 보는 방법을 살펴봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# 복합 자산 관리 {#managing-compound-assets}

AEM(Adobe Experience Manager) 자산은 업로드된 파일에 이미 저장소에 있는 자산에 대한 참조가 포함되어 있는지 식별할 수 있습니다. 이 기능은 지원되는 파일 포맷에서만 사용할 수 있습니다. 업로드된 자산에 AEM 자산에 대한 참조가 포함되어 있으면 업로드된 자산과 참조된 자산 사이에 양방향 링크가 만들어집니다.

중복성을 제거할 수 있을 뿐만 아니라 Adobe Creative Cloud 애플리케이션에서 AEM 자산을 참조하면 공동 작업을 향상시킬 수 있고 사용자의 효율성과 생산성을 향상시킬 수 있습니다.

AEM Assets는 **양방향 참조를**&#x200B;지원합니다. 업로드된 파일의 자산 세부 사항 페이지에서 참조된 자산을 찾을 수 있습니다. 또한 참조된 자산의 자산 세부 사항 페이지에서 AEM 자산에 대한 참조 파일을 볼 수 있습니다.

참조는 참조된 자산의 경로, 문서 ID 및 인스턴스 ID를 기반으로 결정됩니다.

## Adobe Illustrator에서 AEM 자산을 참조로 추가 {#refai}

Adobe Illustrator 파일 내에서 기존 AEM 자산을 참조할 수 있습니다.

디지털 자산을 추가하려면 AEM [데스크톱 앱을](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) 사용하거나 AEM 사용자 인터페이스를 사용하여 [업로드하십시오](/help/assets/manage-digital-assets.md#uploading-assets) .

워크플로우가 완료되면 자산의 자산 세부 사항 페이지로 이동합니다. 기존 AEM 자산에 대한 참조는 참조 **열의 종속성** 아래에 **나열됩니다** . 종속성 아래에 표시되는 참조된 **자산은** 현재 자산 이외의 파일에서도 참조할 수 있습니다.

자산에 대한 참조 파일 목록을 보려면 종속성 아래의 자산을 **클릭합니다**. 도구 모음에서 **속성** 보기 아이콘을 클릭합니다. 속성 페이지에서 현재 자산을 참조하는 파일 목록이 기본 **탭의 참조** 열 아래에 **나타납니다** .

## Adobe InDesign에서 AEM 자산을 참조로 추가 {#add-aem-assets-as-references-in-adobe-indesign}

InDesign 파일 내에서 AEM 자산을 참조하려면 AEM 자산을 InDesign 파일로 드래그하거나 InDesign 파일을 ZIP 파일로 내보내십시오.

참조된 자산이 AEM 자산에 이미 있습니다. Adobe InDesign 서버를 구성하여 하위 자산을 추출할 수 있습니다. InDesign 파일에 포함된 에셋은 하위 에셋으로 추출됩니다.

>[!NOTE]
>
>InDesign 서버가 프록시되면 InDesign 파일의 미리 보기가 XMP 메타데이터 내에 임베드되어 있습니다. 이 경우 축소판 추출이 명시적으로 필요하지 않습니다. 그러나 InDesign 서버가 프록시되지 않은 경우 InDesign 파일에 대해 축소판을 명시적으로 추출해야 합니다.

### AEM 자산을 드래그하여 참조 만들기 {#create-references-by-dragging-aem-assets}

이 절차는 Adobe Illustrator [에서 AEM 자산을 참조로 추가하는 것과 비슷합니다](#refai).

### ZIP 파일을 내보내 에셋에 대한 참조 만들기 {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. 새 워크플로우 만들기.
1. Adobe InDesign의 패키지 기능을 사용하여 문서를 내보냅니다.
Adobe InDesign에서 문서와 연결된 에셋을 패키지로 내보낼 수 있습니다. 이 경우 내보낸 폴더에는 InDesign 파일의 하위 자산이 들어 있는 링크 폴더가 포함됩니다.
1. ZIP 파일을 만들어 AEM 저장소에 업로드합니다.
1. 보관 해제 워크플로우를 시작합니다.
1. 워크플로우가 완료되면 링크 폴더의 참조는 자동으로 하위 자산으로 참조됩니다. 참조된 자산 목록을 보려면 자산 세부 사항 페이지로 이동합니다.

## Adobe Photoshop에서 AEM 자산을 참조로 추가 {#refps}

디지털 자산을 추가하려면 AEM [데스크톱 앱을](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) 사용하거나 AEM 사용자 인터페이스를 사용하여 [업로드하십시오](/help/assets/manage-digital-assets.md#uploading-assets) .

워크플로우가 완료되면 기존 AEM 자산에 대한 참조가 자산 세부 사항 페이지에 나열됩니다. 참조된 자산에는 참조되는 자산의 목록도 포함되어 있습니다. 참조된 자산 목록을 보려면 자산 세부 사항 페이지로 이동합니다.

>[!NOTE]
>
>복합 자산 내의 자산은 문서 ID 및 인스턴스 ID를 기반으로 참조할 수도 있습니다. 이 기능은 Adobe Illustrator 및 Adobe Photoshop 버전에서만 사용할 수 있습니다. 다른 경우, 참조는 이전 버전의 AEM에서와 마찬가지로 기본 복합 자산에서 연결된 자산의 상대 경로를 기준으로 수행됩니다.

## 여러 페이지 파일의 페이지 보기 {#view-pages-of-a-multi-page-file}

AEM 자산의 페이지 뷰어 기능을 사용하면 PDF, INDD, PPT, PPTX 및 Ai 파일을 비롯한 여러 페이지 파일의 개별 페이지를 볼 수 있습니다. InDesign의 경우 InDesign 서버를 사용하여 페이지를 추출할 수 있습니다. InDesign 파일을 만드는 동안 페이지 미리 보기가 저장된 경우 페이지 추출을 위해 InDesign Server가 필요하지 않습니다.

자산 페이지에서 파일의 개별 페이지를 검색할 수 있습니다. 도구 모음의 옵션을 사용하여 파일의 개별 페이지에 주석을 달 수 있습니다. 페이지 개요 옵션을 사용하여 **모든** 페이지를 동시에 볼 수도 있습니다.

1. 다중 페이지 파일이 포함된 AEM 자산의 폴더로 이동합니다.
1. 자산을 클릭하여 자산 페이지를 봅니다.
1. 글로벌 탐색 아이콘을 클릭한 다음 메뉴에서 **페이지를** 선택합니다.
1. 이미지 아래의 왼쪽 또는 오른쪽 화살표를 클릭하여 파일의 개별 페이지로 이동합니다.
1. 페이지에 주석을 달려면 도구 모음에서 **주석** 아이콘을 클릭하고 주석을 추가합니다.
1. 파일을 다운로드하려면 다운로드 **아이콘을 클릭합니다** .
1. 파일의 모든 페이지를 동시에 보려면 페이지 개요 **아이콘을 클릭합니다** .
1. 주석 및 다운로드를 포함한 파일의 활동 스트림을 보려면 AEM 아이콘을 클릭한 다음 **메뉴에서 타임라인을** 선택합니다.
1. 페이지의 메타데이터 속성을 보고 편집하려면 도구 모음에서 속성 **보기** 아이콘을 클릭합니다.
