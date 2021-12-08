---
title: 더 이상 사용되지 않는 및 제거된 기능
description: 의 사용 중단되거나 제거된 기능에 관한 릴리스 노트입니다. [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 9410b061278d916c95233ecba7f7f946fccc51ed
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 32%

---

# 더 이상 사용되지 않는 및 제거된 기능 {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="AEM as a Cloud Service에서 사용이 중단되거나 제거된 기능"
>abstract="AEM as a Cloud Service에는 클라우드 기반의 배포 모델이 있습니다. 특정 기능과 기능은 클라우드 기반의 대응 기능으로 개선되었으며 이 탭에는 해당 기능이 표시됩니다."


Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다. 또한, 다음과 같습니다. [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 은 클라우드 기반의 배포 모델을 제공하며, 특정 기능과 기능은 클라우드 기반의 대응 기능으로 대체되었습니다.

곧 제거/교체될 [!DNL Experience Manager] 기능, 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 사용 중단되는 기능은 계속 사용할 수는 있지만 더 이상 향상되지 않습니다.
1. 이제 사용되지 않는다고 발표된 기능은 이른 시일 내에 후속 주 릴리스에서 제거됩니다. 제거할 실제 목표 날짜는 발표됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## 더 이상 사용되지 않는 기능 {#deprecated-features}

이 섹션에는 의 사용 중단으로 표시된 기능이 나열됩니다. [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. 일반적으로 향후 릴리스에서 제거될 기능은 먼저 사용 중지로 설정되고 대체 기능이 제공됩니다.

고객은 현재 배포에서 기능/성능을 사용하는지 검토하고 제공된 대체 기능을 사용하기 위해 구현 변경을 계획해야 합니다.

| 기능 | 사용되지 않는 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | 에 대한 경험 조각 속성 **소셜 미디어 상태**. | 이 기능은 곧 제거됩니다. |
| [!DNL Sites] | 템플릿 기반 단순 컨텐츠 조각. | [모델 기반의 구조화된 컨텐츠 조각](/help/assets/content-fragments/content-fragments-models.md) 지금 |
| [!DNL Assets] | `DAM Asset Update` 수집된 이미지를 처리하는 워크플로우입니다. | 이제 자산 수집은 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. |
| [!DNL Assets] | 자산을 로 바로 업로드 [!DNL Experience Manager]. 자세한 내용은 [더 이상 사용되지 않는 자산 업로드 API](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | [다이렉트 이진 업로드](/help/assets/add-assets.md)를 사용합니다. 자세한 내용은 [직접 업로드 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오. |
| [!DNL Assets] | [특정 워크플로우 단계](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) in `DAM Asset Update` 워크플로우는 과 같은 명령줄 도구 호출을 포함하여 지원되지 않습니다. [!DNL ImageMagick]. | [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)는 많은 워크플로우에 대한 대체 기능을 제공합니다. 사용자 지정 처리에는 [사후 처리 워크플로우](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용하십시오. |
| [!DNL Assets] | 비디오의 FFmpeg 코드 변환. | FFmpeg 썸네일 생성의 경우 [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. FFmpeg 코드 변환의 경우 [Dynamic Media](/help/assets/manage-video-assets.md)를 사용합니다. |
| [!DNL Foundation] | 복제 에이전트의 &quot;분배&quot; 탭에 있는 트리 복제 UI(2021년 9월 30일 이후 제거) | [게시 관리](/help/operations/replication.md#manage-publication) 또는 [컨텐츠 트리 워크플로우 게시](/help/operations/replication.md#publish-content-tree-workflow) 접근 방식 |

## 제거된 기능 {#removed-features}

이 섹션에는 제거된 기능과 기능이 나열됩니다. [!DNL Experience Manager] with [!DNL Experience Manager] 로서의 [!DNL Cloud Service].

| 영역 | 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| 사용자 인터페이스 | 클래식 UI가 제품 사용자 인터페이스에서 제거됩니다. 몇 가지 클래식 UI 대화 상자는 링크 확인, 버전 삭제 및 일부 Cloud Service 구성과 같은 몇 가지 선별된 기능에 사용할 수 있습니다. 예정된 날짜 [제품 업데이트](/help/release-notes/home.md) 클래식 UI 가용성을 더 이상 제거할 수 있습니다. | 표준 UI |
| [!DNL Dynamic Media] | 과의 이전 통합 [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) 및 [Dynamic Media 하이브리드 모드](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic) 에서 사용할 수 없음 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. | 사용 [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) 제공 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. |
| [!DNL Sites] | 포털 디렉터 및 포틀릿 구성 요소 | 이 기능은에서 더 이상 사용되지 않습니다. [!DNL Experience Manager] 6.4 및에서 제거됨 [!DNL Experience Manager]. |
| [!DNL Sites] | 디자인 가져오기 | 이 기능은 [!DNL Experience Manager] 저장소는 런타임 시 액세스할 수 없습니다. |
| [!DNL Assets] | [!DNL Assets]Marketing Cloud 자산 핵심 서비스 및 Creative Cloud 서비스와 공유하는 를 사용할 수 없습니다. | 통합 [!DNL Adobe Creative Cloud], 사용 [Adobe 자산 링크](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html). |
| [!DNL Foundation] | Apache Sling 데이터 소스(OSGi 번들 org.apache.sling.datasource)에 대한 지원. | N/A |

## Java API {#java-api}

자세한 내용은 [이 페이지](/help/release-notes/deprecated-apis.md) 경우에 따라 도입된 더 이상 사용되지 않거나 제거된 Java API에 대해

## OSGI 구성 {#osgi-configuration}

자세한 내용은 [이 문서](/help/implementing/deploying/osgi-configuration-api.md) 의 경우 OSGI 속성 구성에 대한 모든 제한 사항과 관련하여 시간이 지남에 따라 도입될 수 있습니다.
