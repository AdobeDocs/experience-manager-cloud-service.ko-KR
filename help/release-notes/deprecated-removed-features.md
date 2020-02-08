---
title: 사용 중단되거나 제거된 기능
description: 클라우드 서비스로 Adobe Experience Manager의 사용 중단되거나 제거된 기능에 대한 릴리스 노트입니다.
translation-type: tm+mt
source-git-commit: b31ae32285080075d2531edd2c4976cf801d1c89

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe는 제품 기능을 지속적으로 평가하며, 시간이 지남에 따라 이전 기능을 더 현대적인 대체 제품으로 교체하여 전반적인 고객 가치를 높이며 이전 버전과의 호환성을 항상 신중하게 고려합니다. 또한 클라우드 서비스로서 Adobe Experience Manager가 클라우드 기반의 배포 모델을 제공하므로 특정 기능과 기능은 클라우드 기반의 대응 제품으로 대체되었습니다.

예정된 AEM 기능의 제거/교체를 알리려면 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 더 이상 사용되지 않는 기능은 계속 사용할 수 있지만 더 이상 향상되지 않습니다.
1. 더 이상 사용되지 않는다고 발표된 기능은 빠른 시일 내에 후속 주 릴리스에서 제거됩니다. 제거에 대한 실제 목표 날짜가 표시됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## Deprecated features {#deprecated-features}

이 섹션에는 Experience Manager에서 클라우드 서비스로 더 이상 사용되지 않는 것으로 표시된 기능 및 기능이 나열됩니다. 일반적으로 향후 릴리스에서 제거될 예정인 기능은 먼저 더 이상 사용되지 않도록 설정되며, 대신 제공된 기능이 있습니다.

고객은 현재 배포에서 기능을 사용할지 검토하고 대체 기능을 사용할 수 있도록 구현 변경을 계획하는 것이 좋습니다.

| 영역 | 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| 자산 | 자산 수집 및 처리가 더 이상 `DAM Asset Update` 워크플로우를 사용하지 않음 | 자산 수집은 [자산 마이크로 서비스를](/help/assets/asset-microservices-overview.md) 사용합니다. |
| 자산 | AEM에 바로 자산 업로드 - [가치 하락 자산 업로드 API 참조](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api) | [직접 이진 업로드는](/help/assets/add-assets.md) Experience Manager에서 클라우드 서비스로 사용됩니다. 자세한 내용은 [직접 업로드 API를 참조하십시오](/help/assets/developer-reference-material-apis.md#overview-binary-upload). |
| 자산 | [ImageMagick과 같은 명령줄 도구 호출을 포함하여](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) `DAM Asset Update` 워크플로우의 특정 워크플로우 단계는 지원되지 않습니다 | [자산 마이크로서비스는](/help/assets/asset-microservices-overview.md) 다양한 워크플로우를 대체할 수 있습니다. 사용자 정의 처리를 위해 [사후 처리 워크플로우를](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)사용합니다. |

## Removed features {#removed-features}

이 섹션에는 Experience Manager를 클라우드 서비스로 사용하여 AEM에서 제거된 기능과 기능이 나열됩니다.

| 영역 | 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| UI | 일부 클래식 UI 대화 상자는 당분간 링크 검사기, 버전 제거 및 일부 클라우드 서비스 구성과 같은 일부 특정 기능에 대해 유지되지만, 일반적으로 클래식 UI에 대한 액세스는 AEM 제품 UI에서 제거되었습니다. | 표준 UI |
| 다이내믹 미디어 | Dynamic Media [Classic(Scene7)](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/scene7.html) 및 Dynamic Media [Hybrid 모드와의](https://helpx.adobe.com/experience-manager/6-5/assets/using/config-dynamic.html) 이전 통합은 AEM에서 클라우드 서비스로 사용할 수 없습니다. | Experience [Manager](/help/assets/dynamic-media/dynamic-media.md) 와 함께 제공되는 Dynamic Media를 클라우드 서비스로 사용하십시오. |
| 사이트 | 포털 디렉터 및 포틀릿 구성 요소 | 이러한 기능은 AEM 6.4에서 더 이상 사용되지 않으며, 이제 AEM에서 제거되었습니다. |
| 사이트 | 디자인 가져오기 | 런타임 시 AEM 저장소의 변경할 수 없는 섹션에 액세스할 수 없으므로 이 기능이 제거되었습니다. |
| 자산 | [Marketing Cloud 자산 핵심 서비스 및 Creative Cloud 서비스와](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) 공유하는 AEM 자산을 사용할 수 없습니다. | Creative Cloud와 통합하려면 Adobe Asset [Link를 사용하십시오](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). |
