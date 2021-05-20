---
title: 메타데이터 편집 또는 추가 방법
description: 자산 메타데이터를 편집할 수 있는 다양한 방법으로 [!DNL Experience Manager Assets] 의 자산 메타데이터에 대해 알아봅니다.
contentOwner: AG
feature: 메타데이터
role: Business Practitioner,Administrator
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# 메타데이터 {#how-to-edit-or-add-metadata} 을 편집하거나 추가하는 방법

메타데이터는 검색할 수 있는 자산에 대한 추가 정보입니다. 이미지를 업로드할 때 자동으로 추출됩니다. 기존 메타데이터를 편집하거나 기존 필드에 새 메타데이터 속성을 추가할 수 있습니다(예: 메타데이터 필드가 비어 있는 경우).

회사는 제어되고 안정적인 메타데이터 어휘가 필요하므로 [!DNL Experience Manager Assets]에서는 새 메타데이터 속성을 임시로 추가할 수 없습니다. 작성자가 자산에 새 메타데이터 필드를 추가할 수 없지만 개발자는 추가할 수 있습니다. [Assets](meta-edit.md#editing-metadata-schema)에 대한 새 메타데이터 속성 만들기를 참조하십시오.

## 자산 {#editing-metadata-for-an-asset}에 대한 메타데이터 편집

메타데이터를 편집하려면 다음을 수행하십시오.

1. 다음 중 하나를 수행하십시오.

   * Assets UI에서 자산을 선택하고 도구 모음에서 **[!UICONTROL 속성 보기]** 아이콘을 클릭/탭합니다.
   * 자산 축소판에서 **[!UICONTROL 속성 보기]** 빠른 작업을 선택합니다.
   * 자산 페이지의 도구 모음에서 **[!UICONTROL 속성 보기]**&#x200B;를 클릭/탭합니다.

   자산 페이지에 자산의 모든 메타데이터가 표시됩니다. 이 메타데이터는 AEM Assets에 업로드(수집)될 때 자동으로 추출됩니다.

1. 필요에 따라 다양한 탭 아래에서 메타데이터를 편집하고, 완료되면 도구 모음에서 **[!UICONTROL 저장]** 을 클릭/탭하여 변경 사항을 저장합니다. **[!UICONTROL 닫기]**&#x200B;를 클릭/탭하여 Assets 웹 인터페이스로 돌아갑니다.

   >[!NOTE]
   >
   >텍스트 필드가 비어 있으면 기존 메타데이터 세트가 없습니다. 필드에 값을 입력하고 저장하여 해당 메타데이터 속성을 추가할 수 있습니다.

자산의 메타데이터에 대한 모든 변경 사항은 XMP 데이터의 일부로서 원래 바이너리에 다시 작성됩니다. 이 작업은 AEM 메타데이터 다시 쓰기 작업 과정을 통해 수행됩니다. 기존 속성(예: `dc:title`)에 대한 변경 사항을 덮어쓰고 새로 만든 속성(`cq:tags` 등의 사용자 지정 속성 포함)이 스키마와 함께 추가됩니다.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## 메타데이터 스키마 편집 {#editing-metadata-schema}

메타데이터 스키마를 편집하는 방법에 대한 자세한 내용은 [메타데이터 스키마 양식 편집](metadata-schemas.md#edit-metadata-schema-forms)을 참조하십시오.

## AEM {#registering-a-custom-namespace-within-aem} 내에서 사용자 지정 네임스페이스 등록

AEM 내에 고유한 네임스페이스를 추가할 수 있습니다. cq, jcr 및 sling과 같이 사전 정의된 네임스페이스가 있는 것처럼 저장소 메타데이터 및 xml 처리를 위한 네임스페이스를 가질 수 있습니다.

1. 노드 유형 관리 페이지 *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*&#x200B;로 이동합니다.
1. 페이지 맨 위에서 **[!UICONTROL 네임스페이스]**&#x200B;를 클릭하거나 탭합니다. 네임스페이스 관리 페이지가 창에 표시됩니다.

1. 네임스페이스를 추가하려면 맨 아래에서 **[!UICONTROL 새로 만들기]** 를 클릭하거나 탭합니다.
1. XML 네임스페이스 규칙에서 사용자 지정 네임스페이스를 지정합니다(URI 형식으로 ID를 지정하고 ID에 연결된 접두사를 지정). **[!UICONTROL 저장]**&#x200B;을 클릭하거나 탭합니다.
