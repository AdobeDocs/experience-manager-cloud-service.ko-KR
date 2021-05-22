---
title: 이제 사용되지 않는 기능과 제거된 기능
description: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]에서 사용 중단되거나 제거된 기능에 관한 릴리스 노트입니다.'
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 8c26dbcc77113b86ab28ab52e0b6564fa5ed538a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 44%

---

# 이제 사용되지 않는 기능과 제거된 기능 {#deprecated-and-removed-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다. 또한 [!DNL Adobe Experience Manager] 은(는) 클라우드 기반의 배포 모델을 제공하므로 특정 기능과 기능은 클라우드 기반의 대응 기능으로 대체되었습니다.[!DNL Cloud Service]

[!DNL Experience Manager] 기능을 제거/교체하기 위해 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 사용 중단되는 기능은 계속 사용할 수는 있지만 더 이상 향상되지 않습니다.
1. 이제 사용되지 않는다고 발표된 기능은 이른 시일 내에 후속 주 릴리스에서 제거됩니다. 제거할 실제 목표 날짜는 발표됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## 이제 사용되지 않는 기능 {#deprecated-features}

이 섹션에는 [!DNL Experience Manager]에서 [!DNL Cloud Service]으로 더 이상 사용되지 않는 것으로 표시된 기능이 나열됩니다. 일반적으로 향후 릴리스에서 제거될 기능은 먼저 사용 중지로 설정되고 대체 기능이 제공됩니다.

고객은 현재 배포에서 기능/성능을 사용하는지 검토하고 제공된 대체 기능을 사용하기 위해 구현 변경을 계획해야 합니다.

| 기능 | 사용되지 않는 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| [!DNL Assets] | `DAM Asset Update` 수집된 이미지를 처리하는 워크플로우입니다. | 이제 자산 수집은 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. |
| [!DNL Assets] | 자산을 [!DNL Experience Manager]에 바로 업로드합니다.[더 이상 사용되지 않는 자산 업로드 API](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api)를 참조하십시오. | [다이렉트 이진 업로드](/help/assets/add-assets.md)를 사용합니다. 자세한 내용은 [직접 업로드 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오. |
| [!DNL Assets] | ImageMagick와 같은 명령줄 도구 호출을 포함하여 [ 워크플로우의 ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps)특정 워크플로우 단계`DAM Asset Update`는 지원되지 않습니다. | [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)는 많은 워크플로우에 대한 대체 기능을 제공합니다. 사용자 지정 처리에는 [사후 처리 워크플로우](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용하십시오. |
| [!DNL Assets] | 비디오의 FFmpeg 코드 변환. | FFmpeg 썸네일 생성의 경우 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. FFmpeg 코드 변환의 경우 [Dynamic Media](/help/assets/manage-video-assets.md)를 사용합니다. |

## 제거된 기능 {#removed-features}

이 섹션에는 [!DNL Experience Manager]이 [!DNL Cloud Service]로 있는 [!DNL Experience Manager]에서 제거된 기능이 나열됩니다.

| 영역 | 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| 사용자 인터페이스 | 클래식 UI가 제품 사용자 인터페이스에서 제거됩니다. 몇 가지 클래식 UI 대화 상자는 링크 확인, 버전 삭제 및 일부 Cloud Service 구성과 같은 몇 가지 선별된 기능에 사용할 수 있습니다. 예정된 [제품 업데이트](/help/release-notes/home.md)에 따라 클래식 UI 가용성이 더 제거될 수 있습니다. | 표준 UI |
| [!DNL Dynamic Media] | [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) 및 [Dynamic Media Hybrid 모드](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic)와의 이전 통합은 [!DNL Experience Manager]에서 [!DNL Cloud Service]로 사용할 수 없습니다. | [!DNL Experience Manager]와 함께 제공된 [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md)을 [!DNL Cloud Service]로 사용하십시오. |
| [!DNL Sites] | 포털 디렉터 및 포틀릿 구성 요소 | 이러한 기능은 [!DNL Experience Manager] 6.4에서 더 이상 사용되지 않으며, 이제 [!DNL Experience Manager]에서 제거되었습니다. |
| [!DNL Sites] | 디자인 가져오기 | 런타임 시 [!DNL Experience Manager] 리포지토리의 변경할 수 없는 섹션을 액세스할 수 없어서 이 기능은 제거되었습니다. |
| [!DNL Assets] | [!DNL Assets]Marketing Cloud 자산 핵심 서비스 및 Creative Cloud 서비스와 공유하는 를 사용할 수 없습니다. | [!DNL Adobe Creative Cloud]과 통합하려면 [자산 링크 Adobe](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)를 사용하십시오. |
