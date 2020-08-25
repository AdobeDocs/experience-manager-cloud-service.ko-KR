---
title: 이제 사용되지 않는 기능과 제거된 기능
description: 클라우드 서비스로서의 Adobe Experience Manager의 이제 사용되지 않는 기능과 제거된 기능에 관한 릴리스 노트입니다.
translation-type: tm+mt
source-git-commit: 0a9a462f1b92a0dcb712163574bbf57582f8145c
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 100%

---


# 이제 사용되지 않는 기능과 제거된 기능 {#deprecated-and-removed-features}

Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다. 또한 클라우드 서비스로서의 Adobe Experience Manager에서는 클라우드 기반의 배포 모델을 제공하므로 특정 기능과 기능은 클라우드 기반의 대응 기능으로 대체되었습니다.

예정된 AEM 기능의 제거/교체를 알리려면 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 이제 사용되지 않는 기능은 계속 사용할 수는 있지만 더는 향상되지 않습니다.
1. 이제 사용되지 않는다고 발표된 기능은 이른 시일 내에 후속 주 릴리스에서 제거됩니다. 제거할 실제 목표 날짜는 발표됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## 이제 사용되지 않는 기능 {#deprecated-features}

이 섹션에는 클라우드 서비스로서의 Experience Manager에서 이제 사용되지 않는 것으로 표시된 기능이 나열됩니다. 일반적으로 향후 릴리스에서 제거될 예정인 기능은 먼저 이제 사용되지 않음으로 설정되며, 대안 기능이 제공됩니다.

고객은 현재 배포에서 기능을 사용할지 검토하고 대체 기능을 사용할 수 있도록 구현 변경을 계획하는 것이 좋습니다.

| 기능 | 사용되지 않는 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| 자산 | `DAM Asset Update` 수집된 이미지를 처리하는 워크플로우입니다. | 이제 자산 수집은 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. |
| 자산 | 자산을 AEM에 바로 업로드합니다. [이제 사용하지 않는 자산 업로드 API](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api)를 참조하십시오. | [다이렉트 이진 업로드](/help/assets/add-assets.md)를 사용합니다. 자세한 내용은 [직접 업로드 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오. |
| 자산 | ImageMagick와 같은 명령줄 도구 호출을 포함하여 [ 워크플로우의 ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps)특정 워크플로우 단계`DAM Asset Update`는 지원되지 않습니다. | [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)는 많은 워크플로우에 대한 대체 기능을 제공합니다. 사용자 지정 처리에는 [사후 처리 워크플로우](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용하십시오. |
| 자산 | 비디오의 FFmpeg 코드 변환. | FFmpeg 썸네일 생성의 경우 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. FFmpeg 코드 변환의 경우 [Dynamic Media](/help/assets/manage-video-assets.md)를 사용합니다. |

## 제거된 기능 {#removed-features}

이 섹션에는 클라우드 서비스로서의 Experience Manager와 함께 AEM에서 제거된 기능이 나열됩니다.

| 영역 | 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| UI | 일부 클래식 UI 대화 상자는 링크 확인, 버전 삭제 및 일부 클라우드 서비스 구성과 같은 몇 가지 선별된 기능을 위해 유지되지만, 일반적으로 클래식 UI에 대한 액세스는 AEM 제품 UI에서 제거되었습니다. | 표준 UI |
| 다이내믹 미디어 | [Dynamic Media 클래식(Scene7)](https://helpx.adobe.com/kr/experience-manager/6-5/sites/administering/using/scene7.html) 및 [Dynamic Media 하이브리드 모드](https://helpx.adobe.com/kr/experience-manager/6-5/assets/using/config-dynamic.html)와의 이전 통합을 클라우드 서비스로서의 AEM에서 사용할 수 없습니다. | 클라우드 서비스로서의 Experience Manager과 함께 제공된 [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md)를 사용하십시오. |
| 사이트 | 포털 디렉터 및 포틀릿 구성 요소 | 이 기능들은 AEM 6.4에서 이제 사용되지 않으며, 이제 AEM에서 제거되었습니다. |
| 사이트 | 디자인 가져오기 | 런타임 시 AEM 리포지토리의 변경할 수 없는 섹션을 액세스할 수 없어서 이 기능은 제거되었습니다. |
| 자산 | [Marketing Cloud 자산 핵심 서비스 및 Creative Cloud 서비스와 공유하는 AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html)를 사용할 수 없습니다. | Creative Cloud와 통합하려면 [Adobe 자산 링크](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)를 사용하십시오. |
