---
title: 더 이상 사용되지 않는/제거된 기능
description: ' [!DNL Adobe Experience Manager]  [!DNL Cloud Service]에서 더 이상 사용되지 않으며 제거된 기능에 관련된 릴리스 정보입니다.'
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 459e6cbf91f9b7f995bd1fd9c8758962c41c9341
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 100%

---

# 더 이상 사용되지 않는/제거된 기능 {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="AEM as a Cloud Service에서 더 이상 사용되지 않는/제거된 기능"
>abstract="AEM as a Cloud Service에는 클라우드 기반 배포 모델이 있습니다. 일부 기능은 클라우드 기반 기능으로 대체되었으며 이 탭에서 이들 기능이 표시됩니다."


Adobe는 항상 이전 기능과의 호환성을 신중하게 고려하면서 전반적인 고객 가치를 향상하도록 오랜 시간에 걸쳐 오래된 기능을 새롭게 만들거나 더 현대적인 대안으로 교체하기 위해 제품 기능을 지속해서 평가합니다. 또한 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]에서 클라우드 기반 배포 모델을 제공함에 따라, 일부 기능이 클라우드 기반 기능으로 대체되었습니다.

[!DNL Experience Manager] 기능의 제거/교체가 임박했음을 알리기 위해 다음 규칙이 적용됩니다.

1. 사용 중지 공지가 먼저 표시됩니다. 더 이상 사용되지 않는 기능은 계속 사용할 수 있지만 추가로 개선되지 않습니다.
1. 이제 사용되지 않는다고 발표된 기능은 이른 시일 내에 후속 주 릴리스에서 제거됩니다. 제거할 실제 목표 날짜는 발표됩니다.

이 프로세스에서 고객에게 하나 이상의 릴리스 주기를 제공하여, 실제 제거 전에 더 이상 사용되지 않는 기능의 새 버전이나 후속 버전에 대한 구현을 채택할 수 있도록 합니다.

## 더 이상 사용되지 않는 기능 {#deprecated-features}

이 섹션에서는 [!DNL Experience Manager] as a [!DNL Cloud Service]에서 더 이상 사용되지 않는다고 표시된 기능이 나열됩니다. 일반적으로 향후 릴리스에서 제거되는 기능은 먼저 대체 기능이 제공되며 더 이상 사용되지 않도록 설정됩니다.

현재 배포에서 해당 기능을 사용 중인지 검토하고 이들 구현을 변경하여 제공되는 대체 기능을 사용하도록 계획을 세우는 것이 좋습니다.

| 기능 | 사용되지 않는 기능 | 대체 |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | **소셜 미디어 상태**&#x200B;에 대한 경험 조각 속성. | 해당 기능은 곧 제거됩니다. |
| [!DNL Sites] | 템플릿 기반 간단 콘텐츠 조각. | 현재는 [모델 기반 구조 콘텐츠 조각](/help/assets/content-fragments/content-fragments-models.md)입니다. |
| [!DNL Assets] | `DAM Asset Update` 수집된 이미지를 처리하는 워크플로입니다. | 이제 에셋 수집은 [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. |
| [!DNL Assets] | 에셋을 [!DNL Experience Manager]에 바로 업로드할 수 있습니다. [더 이상 사용되지 않는 에셋 업로드 API](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api)를 참조하십시오. | [다이렉트 이진 업로드](/help/assets/add-assets.md)를 사용합니다. 기술적인 세부 정보는 [직접 업로드 API](/help/assets/developer-reference-material-apis.md#upload-binary)를 참조하십시오. |
| [!DNL Assets] | [!DNL ImageMagick]과 같은 호출 명령줄 도구를 포함하여 `DAM Asset Update` 워크플로의 [일부 워크플로 단계](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps)는 지원되지 않습니다. | [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)는 많은 워크플로에 대한 대체 기능을 제공합니다. 사용자 정의 처리에는 [사후 처리 워크플로](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 사용하십시오. |
| [!DNL Assets] | 비디오의 FFmpeg 코드 변환. | FFmpeg 썸네일 생성의 경우 [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)를 사용합니다. FFmpeg 코드 변환의 경우 [Dynamic Media](/help/assets/manage-video-assets.md)를 사용합니다. |
| [!DNL Foundation] | 복제 에이전트의 “배치” 탭 아래에 있는 트리 복제 UI(2021년 9월 30일 이후 제거) | [게시 관리](/help/operations/replication.md#manage-publication) 또는 [콘텐츠 트리 게시 워크플로](/help/operations/replication.md#publish-content-tree-workflow) 접근 방식 |
| [!DNL Foundation] | 복제 에이전트 관리 화면의 배포 탭과 복제 API를 사용하면 10MB가 넘는 콘텐츠 패키지를 복제할 수 없습니다(2022년 9월 12일 이후 적용). | [게시 관리](/help/operations/replication.md#manage-publication) 또는 [콘텐츠 트리 게시 워크플로](/help/operations/replication.md#publish-content-tree-workflow) 접근 방식 |


| [!DNL Foundation]       | 복제 에이전트 관리 화면의 배포 탭과 복제 API를 사용하면 10MB가 넘는 콘텐츠 패키지를 복제할 수 없습니다. 대신 [게시 관리](/help/operations/replication.md#manage-publication) 또는 [콘텐츠 트리 게시 워크플로](/help/operations/replication.md#publish-content-tree-workflow)를 사용하십시오. |

## 제거된 기능 {#removed-features}

이 섹션에서는 [!DNL Experience Manager] 및 [!DNL Experience Manager] as a [!DNL Cloud Service]에서 제거된 기능이 나열됩니다.

| 영역 | 특별 포함 | 대체 | 목표 제거 날짜 |
| ------------ | ------------------ | ----------- | ------------------- |
| 사용자 인터페이스 | 클래식 UI는 제품 사용자 인터페이스에서 제거됩니다. 링크 검사기, 버전 제거 및 일부 클라우드 서비스 구성과 같은 일부 선택 기능에서 몇 가지 클래식 UI 대화 상자를 사용할 수 있습니다. 예정된 [제품 업데이트](/help/release-notes/home.md) 이후에는 클래식 UI를 사용할 수 없습니다. | 표준 UI | 제거됨 |
| [!DNL Dynamic Media] | [!DNL Experience Manager] as a [!DNL Cloud Service]에서 [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=ko-KR#integration)과 [Dynamic Media 하이브리드 모드](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=ko-KR#dynamic)와의 이전 통합을 사용할 수 없습니다. | [!DNL Experience Manager] as a [!DNL Cloud Service]에 제공되는 [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md)를 사용하십시오. | 제거됨 |
| [!DNL Sites] | 포털 디렉터 및 포틀릿 구성 요소 | 이들 기능은 [!DNL Experience Manager] 6.4에서 더 이상 사용되지 않으며 이제 [!DNL Experience Manager]에서 제거되었습니다. | 제거됨 |
| [!DNL Sites] | 디자인 가져오기 | 런타임 시 [!DNL Experience Manager] 저장소의 변경 불가능한 섹션을 사용할 수 없으므로 이 기능은 제거되었습니다. | 제거됨 |
| [!DNL Assets] | Marketing Cloud Assets 핵심 서비스 및 Creative Cloud 서비스와 공유 중인 [!DNL Assets]를 사용할 수 없습니다. | [!DNL Adobe Creative Cloud]와의 통합은 [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)를 사용하십시오. | 제거됨 |
| [!DNL Foundation] | Apache Sling 데이터 소스 지원(OSGi 번들 org.apache.sling.datasource) | 해당 없음 | 제거됨 |
| [!DNL Foundation] | JST 스크립팅 템플릿 지원(OSGi 번들 org.apache.sling.scripting.jst) | 해당 없음 | 제거됨 |
| [!DNL Foundation] | Apache Felix Http Whiteboard 지원 | OSGi Http Whiteboard | 2022년 3월 |
| [!DNL Foundation] | com.adobe.granite.oauth.server 지원 | Adobe IMS 통합 | 2023년 3월 |


## Java API {#java-api}

더 이상 사용되지 않거나 제거된 Java API에 대한 내용은 [이 페이지](/help/release-notes/deprecated-apis.md)를 참조하십시오.

## OSGi 구성 {#osgi-configuration}

OSGi 속성 구성에 있는 제한 사항에 대한 내용은 [이 문서](/help/implementing/deploying/osgi-configuration-api.md)를 참조하십시오. 그 중 일부는 시간이 지남에 따라 도입될 수 있습니다.
