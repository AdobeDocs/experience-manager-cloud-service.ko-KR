---
title: OpenAPI 기능이 포함된 Dynamic Media FAQ
description: OpenAPI 기능이 포함된 Dynamic Media FAQ
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 0%

---

# OpenAPI 기능이 포함된 Dynamic Media FAQ {#new-dynaminc-media-apis-frequently-asked-questions}

+++**Experience Manager Assets as a Cloud Service Dynamic Media 저장소의 모든 자산을 OpenAPI 기능을 사용하여 검색하고 게재할 수 있습니까?**

아니요. OpenAPI 기능이 있는 Dynamic Media을 사용하여 검색 및 게재할 수 있는 자산은 [승인됨 및 최신 버전](/help/assets/approved-assets.md)뿐이며, 모든 채널 및 애플리케이션에서 브랜드 일관성을 보장합니다.

+++

+++**관리자가 폴더에 추가된 새 자산 및 기존 자산을 승인된 것으로 표시할 수 있습니까?**

Experience Manager Assets의 에셋 상태는 `jcr:content/metadata/dam:status` 속성에 의해 관리됩니다. 이 속성의 값은 다음과 같을 수 있습니다.

* 승인됨

* 거부됨

* 변경 요청

Experience Manager Assets은 다음 이미지에 표시된 대로 에셋 카드에서 사용할 수 있는 ![Assets 승인](assets/thumbs-up-icon.svg)을 사용하여 승인됨 상태를 구분합니다.

![승인된 에셋의 아이콘](/help/assets/assets/approved-assets-thumbs-up.png)

폴더의 모든 자산을 승인하려면 [폴더에서 자산을 일괄 승인하는 방법](/help/assets/approved-assets.md#bulk-approve-assets)에 대한 지침을 참조하십시오. 전체 과정을 묘사한 영상도 있다.

벌크 승인을 위해 폴더를 설정하면 폴더에 추가된 모든 새 자산이 자동으로 승인됩니다. 모든 기존 에셋은 에셋을 재처리한 후 승인됩니다. 자산을 재처리하는 방법에 대한 지침은 [디지털 자산 재처리](/help/assets/reprocessing.md)를 참조하십시오. 다른 폴더에서 승인되지 않은 자산을 복사하거나 이동하는 경우 [자산을 재처리](/help/assets/reprocessing.md)해야 합니다.

관리자가 `Rejected` 또는 `Changes requested` 값을 지정한 경우 자산이 `Rejected`(으)로 표시됩니다. Experience Manager Assets은 자산 카드에서 사용할 수 있는 ![Assets 거부](/help/assets/assets/do-not-localize/reject-assets.svg)를 사용하여 거부됨 상태를 구분합니다.

+++

+++**Experience Manager 관리 보기에서 에셋에 대한 역할을 설정하는 데 사용할 Adobe IMS(Adobe Identity Management Services) 사용자 또는 그룹 ID를 확보하여 배달 및 검색 환경을 보호하려면 어떻게 해야 합니까?**

Experience Manager 작성자 환경에 액세스해야 하는 사용자는 Adobe Admin Console에서 Adobe IMS 사용자로 관리됩니다. Adobe IMS 사용자 정의 및 Admin Console에서 액세스 및 관리하는 방법에 대한 자세한 내용은 [Adobe IMS 사용자](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en)를 참조하십시오.

+++

+++**폴더 내에서 여러 자산을 동시에 승인할 수 있습니까?**

예. 한 폴더 내에서 여러 자산을 동시에 승인할 수 있습니다.

[!DNL Experience Manager Assets]에서 여러 자산을 동시에 승인하려면 다음 단계를 실행하십시오.

1. 자산을 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 기본]** 탭에서 **[!UICONTROL 검토 상태]**(으)로 스크롤합니다.
1. 검토 상태를 **[!UICONTROL 승인됨]**(으)로 변경합니다.
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

+++

+++**자산 배달의 보안을 유지하고 Dynamic Media OpenAPI를 검색하려면 어떻게 합니까?**

Experience Manager의 중앙 자산 거버넌스를 사용하면 DAM 관리자 또는 브랜드 관리자가 자산에 대한 액세스를 관리할 수 있습니다. 작성 측, 특히 AEM as a Cloud Service 작성자 인스턴스에서 승인된 에셋에 대한 역할을 구성하여 액세스를 제한할 수 있습니다.

게재 URL을 검색하거나 활용하는 최종 사용자는 인증 프로세스를 성공적으로 통과하면 제한된 에셋에 액세스할 수 있습니다.

자세한 내용은 [Experience Manager의 자산에 대한 액세스 제한](restrict-assets-delivery.md#authoring)을 참조하십시오.

+++

+++**에셋의 승인 상태를 편집할 수 있는 권한을 얻는 방법은 무엇입니까?**

DAM 사용자는 [자산을 승인](approved-assets.md#approve-assets)할 권한이 없을 수 있습니다. 에셋의 승인 상태를 편집할 수 있는 권한을 얻으려면 관리자는 에셋 폴더에 적용된 기본 또는 기타 메타데이터 스키마를 편집하여 **[!UICONTROL 검토 상태]** 필드에 편집 권한을 제공할 수 있습니다. 자세한 내용은 [검토 상태에 대한 편집을 비활성화하는 방법](approved-assets.md#configuration) 필드를 참조하십시오.

+++

+++**OpenAPI 기능이 포함된 Dynamic Media과 Dynamic Media 솔루션은 어떻게 다릅니까?**

OpenAPI 기능이 있는 Dynamic Media과 Dynamic Media은 각각 특화된 제공 기능을 제공하는 고유한 솔루션을 나타냅니다. 구체적인 요구 사항을 철저히 검토하여 요구 사항에 가장 적합한 솔루션을 결정해야 합니다.

다음은 OpenAPI 기능을 제공하는 Dynamic Media과 Dynamic Media의 주요 차이점입니다.

| OpenAPI 기능이 포함된 Dynamic Media | Dynamic Media |
|---|---|
| [Assetsas a Cloud Service 에서만 사용 가능](/help/assets/new-dynamic-media-overview.md#prerequisites-new-dynaminc-media-apis) | 추가 구성 및 프로비저닝 단계가 포함된 온프레미스 또는 Adobe Managed Services에서도 사용할 수 있습니다. |
| [너비, 높이, 회전, 뒤집기, 품질 및 형식과 같은 지원되는 이미지 수정자의 제한된 집합](/help/assets/deliver-assets-apis.md) | 사용 가능한 다양한 이미지 수정자 세트 |
| [사용자 및 역할에 따라 제한된 에셋 배달](/help/assets/restrict-assets-delivery.md) | Dynamic Media에 게시된 Assets은 모든 사용자가 액세스할 수 있습니다 |
| 이미지 스마트 자르기 지원 | 이미지 및 비디오 스마트 자르기 지원 |
| 대부분의 개발자가 익숙한 OpenAPI 사양을 기반으로 합니다. [Micro Frontend 자산 선택기](/help/assets/asset-selector.md)를 사용하면 AEM Assets 확장이 매우 간단해집니다. | SOAP 기반 API를 사용하십시오. |
| 버전 업데이트 및 메타데이터 수정 사항을 포함하여 DAM의 승인된 에셋에 대한 모든 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통해 OpenAPI 기능이 있는 Dynamic Media에 대해 10분의 짧은 TTL(Time-to-Live) 값을 구성하면 10분 이내에 모든 작성 및 게시된 인터페이스에 업데이트가 표시됩니다. | 권장 CDN TTL: 10시간. 캐시 무효화 작업을 사용하여 TTL 값을 재정의할 수 있습니다. |
| 승인된 자산만 다운스트림 애플리케이션으로의 자산 전달에 사용할 수 있으므로 디지털 경험의 브랜드 승인된 자산에 대해 활성화합니다. 전달된 에셋은 AEM as a Cloud Service 저장소의 작성자 인스턴스에서 에셋 만료 상태를 따릅니다. | Dynamic Media에 게시된 에셋에 대한 모든 업데이트는 승인 작업 과정 없이 자동으로 게시되며 디지털 경험의 브랜드 승인 에셋에 대해서는 게시되지 않습니다. 내재된 자산 만료 없음. 에셋은 AEM as a Cloud Service 저장소에서 삭제될 때까지 공개 상태로 유지됩니다. |
| 게재된 에셋 수를 기반으로 한 사용량 보고서. | 사용량 보고서를 사용할 수 없습니다. |

+++

+++**OpenAPI 기능이 있는 Dynamic Media은 연결된 Assets 기능의 제한 사항을 어떻게 해결합니까?**

아래 표에는 두 솔루션의 주요 차이점이 나와 있습니다.

| OpenAPI 기능이 포함된 Dynamic Media | 연결된 자산 |
|---|---|
| 원격 DAM 배포의 Assets은 AEM as a Cloud Service에서 사용할 수 있습니다. | 원격 DAM 배포의 Assets은 AEM as a Cloud Service 또는 Managed Services Adobe에서 사용할 수 있습니다. |
| 원격 DAM 배포의 자산을 AEM Sites 인스턴스에서 사용할 수 있는 경우 자산 바이너리가 복사되지 않습니다. | 자산 바이너리는 원격 DAM 배포의 자산을 AEM Sites 인스턴스에서 사용할 수 있을 때 복사됩니다. |
| AEM Assets에서 지원하는 모든 에셋 형식 유형을 지원합니다. | 비디오가 지원되지 않습니다. |
| 이미지 스마트 자르기를 지원합니다. | Dynamic Media 이미지 스마트 자르기 및 이미지 사전 설정 지원. |
| 원격 DAM 배포에서 자산을 가져오는 동안 로컬 사이트 배포에서 Dynamic Media을 사용할 수 있습니다. | 로컬 Sites 배포의 Dynamic Media은 읽기 전용입니다. |
| 원격 DAM 배포에 연결된 AEM Sites 인스턴스 수에 대한 제한 없음. 원격 DAM의 승인된 자산에 대해 [역할을 구성하여 Sites 인스턴스의 자산에 대한 액세스를 제한](/help/assets/restrict-assets-delivery.md)할 수 있습니다. | 4개 이하의 AEM Sites 인스턴스를 원격 DAM 배포에 연결하는 제한 사항입니다. 숫자가 증가하면 추가 테스트가 필요합니다. |
| OpenAPI 기능이 있는 Asset Selector와 Dynamic Media을 모두 확장하여 사용자 정의 통합을 할 수 있습니다. | 사용자 정의 통합을 허용하도록 연결된 Assets API를 확장할 수 없습니다. |
| 버전 업데이트 및 메타데이터 수정 등 원격 DAM 배포에서 사용할 수 있는 승인된 에셋에 대한 모든 변경 사항은 10분의 짧은 TTL(Time-to-Live) 값 내에서 Sites 인스턴스에 자동으로 반영됩니다. | 원격 DAM 배포의 자산 업데이트는 라이프사이클 이벤트를 통해 자동으로 처리되지만 OpenAPI 기능이 있는 Dynamic Media에 비해 훨씬 많은 시간이 소요됩니다. |
| 원격 DAM의 자산 메타데이터는 AEM Sites 인스턴스에서도 사용할 수 있습니다. | 원격 DAM의 자산 메타데이터를 AEM Sites 인스턴스에서 사용할 수 없습니다. |

+++



