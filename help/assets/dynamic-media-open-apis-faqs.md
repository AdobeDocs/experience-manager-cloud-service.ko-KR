---
title: OpenAPI 기능이 포함된 Dynamic Media FAQ
description: OpenAPI 기능이 포함된 Dynamic Media FAQ
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '1495'
ht-degree: 0%

---

# OpenAPI 기능이 포함된 Dynamic Media FAQ {#new-dynaminc-media-apis-frequently-asked-questions}

+++**Experience Manager Assets as a Cloud Service 저장소의 모든 에셋을 OpenAPI 기능이 있는 Dynamic Media을 사용하여 검색하고 게재할 수 있습니까?**

아니요, 만 [승인된 에셋과 최신 버전의 에셋](/help/assets/approve-assets.md) 는 OpenAPI 기능과 함께 Dynamic Media을 사용하여 검색 및 게재에 사용할 수 있으므로 모든 채널 및 애플리케이션에서 브랜드 일관성을 보장합니다.

+++

+++**관리자는 폴더에 추가된 새 에셋과 기존 에셋을 승인됨으로 어떻게 표시할 수 있습니까?**

Experience Manager Assets의 에셋 상태는 다음에 의해 관리됩니다. `jcr:content/metadata/dam:status` 속성. 이 속성의 값은 다음과 같을 수 있습니다.

* 승인됨

* 거부됨

* 변경 요청

Experience Manager Assets은 관리자 및 자산 보기에 대한 다음 이미지에 표시된 대로 자산 카드에 사용할 수 있는 승인된 아이콘을 사용하여 승인됨 상태를 구분합니다.

**관리자 보기**

![관리자 보기에서 승인된 에셋](/help/assets/assets/approved-assets-thumbs-up.png)

**Assets 보기**

![Assets 보기에서 승인된 에셋](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


폴더의 모든 에셋을 승인하려면 의 지침을 참조하십시오. [폴더의 자산을 일괄 승인하는 방법](/help/assets/approve-assets.md#bulk-approve-assets). 전체 과정을 묘사한 영상도 있다.

벌크 승인을 위해 폴더를 설정하면 폴더에 추가된 모든 새 자산이 자동으로 승인됩니다. 모든 기존 에셋은 에셋을 재처리한 후 승인됩니다. 다음을 참조하십시오 [디지털 자산 재처리](/help/assets/reprocessing.md) 에셋을 재처리하는 방법에 대한 지침을 참조하십시오. 다른 폴더에서 승인되지 않은 자산을 복사하거나 이동하는 경우 [에셋 재처리](/help/assets/reprocessing.md).

자산이 다음으로 표시됨: `Rejected`: 관리자가 `Rejected` 또는 `Changes requested` 값. Experience Manager Assets은 다음을 사용하여 거부됨 상태를 구분합니다. ![Assets 거부](/help/assets/assets/do-not-localize/reject-assets.svg) 관리 보기의 자산 카드에서 사용할 수 있습니다.

마찬가지로 Experience Manager Assets은 에셋 카드에서 다음 거부됨 상태를 사용하여 Assets 보기에서 거부됨 상태를 구별합니다.

![Assets 보기에서 거부된 자산](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**배달 및 검색 환경을 보호하기 위해 Experience Manager 관리 보기에서 에셋에 대한 역할을 설정하는 데 사용할 Adobe IMS(Adobe Identity Management Services) 사용자 또는 그룹 ID를 얻으려면 어떻게 해야 합니까?**

Experience Manager 작성자 환경에 액세스해야 하는 사용자는 Adobe Admin Console에서 Adobe IMS 사용자로 관리됩니다. Adobe IMS 사용자 정의 및 Admin Console에서 액세스 및 관리되는 방식에 대한 자세한 내용은 [Adobe IMS 사용자](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=en).

+++

+++**폴더 내에서 여러 자산을 동시에 승인할 수 있습니까?**

예. 한 폴더 내에서 여러 자산을 동시에 승인할 수 있습니다.

다음 단계를 실행하여에서 여러 자산을 동시에 승인합니다. [!DNL Experience Manager Assets Admin view]:

1. 에셋을 선택하고 **[!UICONTROL 속성]**.
1. 다음에서 **[!UICONTROL 기본]** 탭, 아래로 스크롤하여 **[!UICONTROL 상태 검토]**.
1. 검토 상태를 다음으로 변경 **[!UICONTROL 승인됨]**.
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

마찬가지로 Assets 보기의 폴더 내에서 여러 자산을 동시에 승인하려면 다음을 수행합니다.

1. 에셋을 선택하고 **[!UICONTROL 벌크 메타데이터 편집]**.

1. 선택 **[!UICONTROL 승인됨]** 다음에서 **[!UICONTROL 상태]** 에서 사용할 수 있는 필드 [!UICONTROL 속성] 섹션에 있는 마지막 항목이 될 필요가 없습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.


+++

+++**에셋 전달을 보호하고 Dynamic Media OpenAPI를 검색하려면 어떻게 합니까?**

Experience Manager의 중앙 자산 거버넌스를 사용하면 DAM 관리자 또는 브랜드 관리자가 자산에 대한 액세스를 관리할 수 있습니다. 역할을 구성하거나 작성 측(특히 AEM as a Cloud Service 작성자 인스턴스)에서 승인된 에셋의 활성화 및 비활성화 시간을 설정하여 액세스를 제한할 수 있습니다.

게재 URL을 검색하거나 활용하는 최종 사용자는 인증 프로세스를 성공적으로 통과하면 제한된 에셋에 액세스할 수 있습니다.

자세한 내용은 [Experience Manager의 자산에 대한 액세스 제한](restrict-assets-delivery.md#authoring).

+++

+++**에셋의 승인 상태를 편집할 수 있는 권한을 얻으려면 어떻게 해야 합니까?**

DAM 사용자는 다음에 대한 권한이 없을 수 있습니다. [에셋 승인](approve-assets.md#approve-assets). 에셋의 승인 상태를 편집할 수 있는 권한을 얻으려면 관리자는 에셋 폴더에 적용된 기본 또는 기타 메타데이터 스키마를 편집하여 에셋에 편집 권한을 제공할 수 있습니다. **[!UICONTROL 상태 검토]** 필드. 자세한 내용은 [검토 상태에 대한 편집을 비활성화하는 방법](approve-assets.md#configuration) 필드.

+++

+++**OpenAPI 기능이 포함된 Dynamic Media은 Dynamic Media 솔루션과 어떻게 다릅니까?**

OpenAPI 기능이 있는 Dynamic Media과 Dynamic Media은 각각 특화된 제공 기능을 제공하는 고유한 솔루션을 나타냅니다. 구체적인 요구 사항을 철저히 검토하여 요구 사항에 가장 적합한 솔루션을 결정해야 합니다.

Adobe의 일반적인 지침은 통합 사용 사례(자사 또는 타사 앱)에 대해 OpenAPI 스택과 함께 Dynamic Media을 활용하는 것입니다. Dynamic Media 스택과의 통합이 이미 있는 경우 OpenAPI 스택 URL의 구조가 다르므로 변경하지 않는 것이 좋습니다. 새로운 통합 사용 사례에 대해서만 OpenAPI 스택을 활용합니다. 사용 사례에서 OpenAPI 스택에서 사용할 수 없는 고급 수정자가 필요한 경우, Adobe이 간격을 브리징할 때까지 OpenAPI 스택을 사용하지 마십시오. AEM Assets Cloud Service의 기본 네이티브 게재라도 사용 사례에 OpenAPI 스택에 사용할 수 있는 수정자가 포함되어 있으면 OpenAPI 스택을 평가할 수 있습니다. 결론적으로, 사용 사례의 특성에 따라 OpenAPI 스택이 포함된 Dynamic Media과 Dynamic Media이 함께 사용할 수 있습니다.

다음은 OpenAPI 기능을 제공하는 Dynamic Media과 Dynamic Media의 주요 차이점입니다.

| OpenAPI 기능이 포함된 Dynamic Media | Dynamic Media |
|---|---|
| [Assetsas a Cloud Service 에서만 사용 가능](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | 추가 구성 및 프로비저닝 단계가 포함된 온프레미스 또는 Adobe Managed Services에서도 사용할 수 있습니다. |
| [폭, 높이, 회전, 뒤집기, 품질 및 형식 등 지원되는 이미지 수정자의 제한된 집합](/help/assets/deliver-assets-apis.md) | 사용 가능한 다양한 이미지 수정자 세트 |
| [사용자, 역할, 날짜 및 시간에 따라 제한된 자산 전달](/help/assets/restrict-assets-delivery.md) | Dynamic Media에 게시된 Assets은 모든 사용자가 액세스할 수 있습니다 |
| 대부분의 개발자는 OpenAPI 사양에 익숙합니다. 를 사용하면 AEM Assets 확장이 매우 간단해집니다. [마이크로 프론트엔드 자산 선택기](/help/assets/asset-selector.md). | SOAP 기반 API를 사용하십시오. |
| 버전 업데이트 및 메타데이터 수정 사항을 포함하여 DAM의 승인된 에셋에 대한 모든 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통해 OpenAPI 기능이 있는 Dynamic Media에 대해 10분의 짧은 TTL(Time-to-Live) 값을 구성하면 10분 이내에 모든 작성 및 게시된 인터페이스에 업데이트가 표시됩니다. | 권장 CDN TTL: 10시간. 캐시 무효화 작업을 사용하여 TTL 값을 재정의할 수 있습니다. |
| 승인된 자산만 다운스트림 애플리케이션으로의 자산 전달에 사용할 수 있으므로 디지털 경험의 브랜드 승인된 자산에 대해 활성화합니다. | Dynamic Media에 게시된 에셋에 대한 모든 업데이트는 승인 작업 과정 없이 자동으로 게시되며 디지털 경험의 브랜드 승인 에셋에 대해서는 게시되지 않습니다. |
| 게재된 에셋 수를 기반으로 한 사용량 보고서. 이 기능은 곧 사용할 수 있습니다. | 사용량 보고서를 사용할 수 없습니다. 이 기능은 곧 사용할 수 있습니다. |
| Assets as a Cloud Service 저장소에서 만료됨으로 표시된 Assets은 더 이상 다운스트림 애플리케이션에서 사용할 수 없습니다. | 내재된 자산 만료 없음. 에셋은 AEM as a Cloud Service 저장소에서 삭제될 때까지 공개 상태로 유지됩니다. |
| 이미지 사전 설정 및 비디오 스마트 자르기 기능을 지원하지 않습니다. | 이미지 사전 설정 및 비디오 스마트 자르기 기능을 지원합니다. |
| 입력 비디오에 따라 최고의 인코딩이 제공되도록 하는 동적 비디오 인코딩입니다. 기본 비디오 제공에는 설정이 필요하지 않습니다. | 표준 3은 입력 비디오에 관계없이 인코딩합니다(비디오 게재 성능에 영향을 줄 수 있음). 비디오 비트 전송률에 따라 다른 인코딩을 수동으로 설정해야 합니다. |
| 자산 UID 기반 URL을 추측하기 어려우나(URL 난독화를 활성화함) SEO가 최적화되었습니다. | URL 난독화는 URL 쿼리 매개 변수에만 사용할 수 있습니다. URL의 Assets ID(자산 이름)를 인식할 수 있습니다. |

+++

+++**OpenAPI가 포함된 Dynamic Media 기능은 연결된 Assets 기능의 제한을 어떻게 해결합니까?**

아래 표에는 두 솔루션의 주요 차이점이 나와 있습니다.

| OpenAPI 기능이 포함된 Dynamic Media | 연결된 자산 |
|---|---|
| 원격 DAM 배포의 Assets은 AEM as a Cloud Service에서 사용할 수 있습니다. | 원격 DAM 배포의 Assets은 AEM as a Cloud Service 또는 Managed Services Adobe에서 사용할 수 있습니다. |
| 원격 DAM 배포의 자산을 AEM Sites 인스턴스에서 사용할 수 있는 경우 자산 바이너리가 복사되지 않습니다. | 자산 바이너리는 원격 DAM 배포의 자산을 AEM Sites 인스턴스에서 사용할 수 있을 때 복사됩니다. |
| AEM Assets에서 지원하는 모든 에셋 형식 유형을 지원합니다. | 비디오가 지원되지 않습니다. |
| 원격 DAM 배포에서 자산을 가져오는 동안 로컬 사이트 배포에서 Dynamic Media을 사용할 수 있습니다. | 로컬 Sites 배포의 Dynamic Media은 읽기 전용입니다. |
| 원격 DAM 배포에 연결된 AEM Sites 인스턴스 수에 대한 제한 없음. 다음을 수행할 수 있습니다. [역할을 구성하여 사이트 인스턴스의 자산에 대한 액세스 제한](/help/assets/restrict-assets-delivery.md) 원격 DAM의 승인된 에셋의 경우. | 4개 이하의 AEM Sites 인스턴스를 원격 DAM 배포에 연결하는 제한 사항입니다. 숫자가 증가하면 추가 테스트가 필요합니다. |
| OpenAPI 기능이 있는 Asset Selector와 Dynamic Media을 모두 확장하여 사용자 정의 통합을 할 수 있습니다. | 사용자 정의 통합을 허용하도록 연결된 Assets API를 확장할 수 없습니다. |
| 버전 업데이트 및 메타데이터 수정 등 원격 DAM 배포에서 사용할 수 있는 승인된 에셋에 대한 모든 변경 사항은 10분의 짧은 TTL(Time-to-Live) 값 내에서 Sites 인스턴스에 자동으로 반영됩니다. | 원격 DAM 배포의 자산 업데이트는 라이프사이클 이벤트를 통해 자동으로 처리되지만 OpenAPI 기능이 있는 Dynamic Media에 비해 훨씬 많은 시간이 소요됩니다. |
| 원격 DAM의 자산 메타데이터는 AEM Sites 인스턴스에서도 사용할 수 있습니다. | 원격 DAM의 자산 메타데이터를 AEM Sites 인스턴스에서 사용할 수 없습니다. |

+++



