---
title: 메타데이터를 편집하거나 추가하는 방법
description: 자산 메타데이터를 편집할 수 있는 다양한 방법으로 AEM Assets의 자산 메타데이터에 대해 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---


# 메타데이터를 편집하거나 추가하는 방법 {#how-to-edit-or-add-metadata}

메타데이터는 검색할 수 있는 자산에 대한 추가 정보입니다. 이미지를 업로드할 때 자동으로 압축이 해제됩니다. 기존 메타데이터를 편집하거나 기존 필드에 새 메타데이터 속성을 추가할 수 있습니다(예: 메타데이터 필드가 비어 있는 경우).

기업은 제어 및 안정적인 메타데이터 어휘가 필요하기 때문에 AEM Assets은 새로운 메타데이터 속성을 임시 추가하는 것을 허용하지 않습니다. 작성자는 에셋에 대한 새 메타데이터 필드를 추가할 수 없지만 개발자는 이를 수행할 수 있습니다. 자산에 [대한 새 메타데이터 속성 만들기를 참조하십시오](meta-edit.md#editing-metadata-schema).

## 자산에 대한 메타데이터 편집 {#editing-metadata-for-an-asset}

메타데이터를 편집하려면:

1. 다음 중 하나를 수행하십시오.

   * 자산 UI에서 자산을 선택하고 도구 모음에서 속성 **[!UICONTROL 보기]** 아이콘을 클릭/탭합니다.
   * 자산 축소판에서 속성 **[!UICONTROL 보기 빠른 작업을]** 선택합니다.
   * 자산 페이지의 도구 모음에서 **[!UICONTROL 속성]** 보기를 클릭/탭합니다.

   자산 페이지에는 자산의 모든 메타데이터가 표시됩니다. 이 메타데이터는 AEM Assets에 업로드(인제스트됨)되었을 때 자동으로 추출되었습니다.

1. 필요에 따라 다양한 탭에서 메타데이터를 편집하고, 완료되면 도구 모음에서 **[!UICONTROL 저장을 클릭/탭하여 변경]** 내용을 저장합니다. 닫기를 클릭/ **[!UICONTROL 탭하여]** 자산 웹 인터페이스로 돌아갑니다.

   >[!NOTE]
   >
   >텍스트 필드가 비어 있으면 기존 메타데이터 세트가 없습니다. 필드에 값을 입력하고 저장하여 해당 메타데이터 속성을 추가할 수 있습니다.

자산의 메타데이터에 대한 모든 변경 사항은 XMP 데이터의 일부로서 원본 바이너리에 다시 기록됩니다. 이 작업은 AEM 메타데이터 다시 쓰기 워크플로우를 통해 수행됩니다. 기존 속성(예:)에 대한 변경 사항 `dc:title``cq:tags`이 덮어쓰기되고 새로 생성된 속성(예: 사용자 정의 속성 포함)이 스키마와 함께 추가됩니다.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## 메타데이터 스키마 편집 {#editing-metadata-schema}

메타데이터 스키마를 편집하는 방법에 대한 자세한 내용은 메타데이터 스키마 양식 [편집을 참조하십시오](metadata-schemas.md#edit-metadata-schema-forms).

## AEM 내에서 사용자 지정 네임스페이스 등록 {#registering-a-custom-namespace-within-aem}

AEM 내에서 고유한 네임스페이스를 추가할 수 있습니다. cq, jcr 및 sling과 같은 사전 정의된 네임스페이스가 있는 것처럼 저장소 메타데이터 및 xml 처리를 위한 네임스페이스를 가질 수 있습니다.

1. 노드 유형 관리 페이지 *https://&lt;호스트>:&lt;포트>/crx/explorer/nodetypes/index.jsp으로 이동합니다*.
1. 페이지 상단에서 **[!UICONTROL 네임스페이스]** 를 클릭하거나 탭합니다. 네임스페이스 관리 페이지가 창에 표시됩니다.

1. 네임스페이스를 추가하려면 아래쪽에 있는 **[!UICONTROL 새로]** 만들기를 클릭하거나 탭합니다.
1. XML 네임스페이스 규칙에서 사용자 지정 네임스페이스를 지정합니다(URI 형식으로 ID를 지정하고 ID에 연결된 접두어를 지정합니다). [저장]을 클릭하거나 **[!UICONTROL 탭합니다]**.
