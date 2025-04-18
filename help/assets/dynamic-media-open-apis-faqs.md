---
title: OpenAPI 기능이 포함된 Dynamic Media에 대해 자주 묻는 질문
description: OpenAPI 기능이 포함된 Dynamic Media에 대해 자주 묻는 질문
role: User
exl-id: 3450e050-4b0b-4184-8e71-5e667d9ca721
source-git-commit: c36938e80d0b159c5f89d450aaa228c37c4f5276
workflow-type: ht
source-wordcount: '1600'
ht-degree: 100%

---

# OpenAPI 기능이 포함된 Dynamic Media에 대해 자주 묻는 질문 {#new-dynaminc-media-apis-frequently-asked-questions}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services와의 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 활성화</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>OpenAPI 기능이 포함된 Dynamic Media 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE OpenAPI 기능이 포함된 Dynamic Media 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

+++**Experience Manager Assets as a Cloud Service 저장소의 모든 자산을 OpenAPI 기능이 포함된 Dynamic Media를 사용하여 검색하고 게재할 수 있습니까?**

아니요, 모든 채널과 애플리케이션에서 브랜드 일관성을 보장하는 OpenAPI 기능이 포함된 Dynamic Media를 사용하여 [승인된 최신 버전의 자산](/help/assets/approve-assets.md)만 검색 및 게재할 수 있습니다.

+++

+++**관리자가 폴더에 추가된 신규 자산과 기존 자산을 승인된 것으로 표시하려면 어떻게 해야 합니까?**

Experience Manager Assets에서 자산의 상태는 `jcr:content/metadata/dam:status` 속성에 따라 달라집니다. 이 속성의 값은 다음 상태여야 합니다.

* 승인됨

* 거부됨

* 변경 요청됨

Experience Manager Assets은 관리 및 자산 보기의 다음 이미지에 표시된 것처럼 자산 카드에서 사용할 수 있는 승인 아이콘을 사용하여 승인 상태를 구분합니다.

**관리 보기**

![관리 보기에서 승인된 자산](/help/assets/assets/approved-assets-thumbs-up.png)

**자산 보기**

![자산 보기에서 승인된 자산](/help/assets/assets/approved-assets-thumbs-up-assets-view.png)


폴더의 모든 자산을 승인하려면 [폴더의 자산을 일괄 승인하는 방법](/help/assets/approve-assets.md#bulk-approve-assets)에 대한 지침을 참조하십시오. 전체 프로세스를 보여 주는 비디오도 있습니다.

일괄 승인을 위해 폴더를 설정하면 폴더에 추가되는 모든 새 자산이 자동으로 승인됩니다. 기존의 모든 자산은 자산을 재처리한 후 승인됩니다. 자산을 재처리하는 방법에 대한 지침은 [디지털 자산 재처리](/help/assets/reprocessing.md)를 참조하십시오. 다른 폴더에서 승인되지 않은 자산을 복사하거나 이동하는 경우 [해당 자산을 재처리](/help/assets/reprocessing.md)해야 합니다.

관리자가 `Rejected` 또는 `Changes requested`값을 지정하는 경우 자산은 `Rejected`로 표시됩니다. Experience Manager Assets는 관리 보기의 자산 카드에서 사용할 수 있는 ![자산 거부](/help/assets/assets/do-not-localize/reject-assets.svg)를 사용하여 거부 상태를 구분합니다.

마찬가지로 Experience Manager Assets는 자산 카드의 다음 거부 상태를 사용하여 자산 보기에서 거부 상태를 구분합니다.

![자산 보기에서 거부된 자산](/help/assets/assets/rejected-assets-admin-view.png)


+++

+++**게재 및 검색 환경을 보호하기 위해 Experience Manager 관리 보기에서 자산에 대한 역할을 설정하는 데 Adobe IMS(Adobe Identity Management Services) 사용자 또는 그룹 ID를 사용하도록 하려면 어떻게 해야 합니까?**

Experience Manager 작성자 환경에 대한 액세스가 필요한 사용자는 Adobe Admin Console의 Adobe IMS 사용자로 관리됩니다. Adobe IMS 사용자에 대한 정보, Admin Console에서 액세스 및 관리되는 방식에 대한 자세한 내용은 [Adobe IMS 사용자](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/adobe-ims-users.html?lang=ko)를 참조하십시오.

+++

+++**폴더 내에서 여러 자산을 동시에 승인할 수 있습니까?**

예, 폴더 내에서 여러 자산을 동시에 승인할 수 있습니다.

[!DNL Experience Manager Assets Admin view]에서 여러 자산을 동시에 승인하려면 다음 단계를 실행하십시오.

1. 자산을 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 기본]** 탭에서 아래로 스크롤하여 **[!UICONTROL 상태 검토]**&#x200B;를 선택합니다.
1. 검토 상태를 **[!UICONTROL 승인됨]**&#x200B;으로 변경합니다.
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

마찬가지로 자산 보기에서 폴더 내에서 여러 자산을 동시에 승인하려면 다음 작업을 수행합니다.

1. 자산을 선택하고 **[!UICONTROL 일괄 메타데이터 편집]**&#x200B;을 클릭합니다.

1. 오른쪽 창 **[!UICONTROL 속성]** 섹션의 사용 가능한 **[!UICONTROL 상태]** 필드에서 [!UICONTROL 승인됨]을 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.


+++

+++**Dynamic Media OpenAPI에 대한 자산 게재 및 검색을 보호하려면 어떻게 해야 합니까?**

Experience Manager의 중앙 자산 거버넌스를 통해 DAM 관리자 또는 브랜드 관리자가 자산에 대한 액세스를 관리할 수 있습니다. 작성자 측, 특히 AEM as a Cloud Service 작성자 인스턴스에서 역할을 구성하거나 승인된 자산에 대한 활성화 및 비활성화 시간을 설정하여 액세스를 제한할 수 있습니다.

게재 URL을 검색하거나 활용하는 최종 사용자가 승인 절차에 성공적으로 통과하면 제한된 자산에 액세스할 수 있습니다.

자세한 내용은 [Experience Manager의 자산에 대한 액세스 제한](restrict-assets-delivery.md#authoring)을 참조하십시오.

+++

+++**자산의 승인 상태를 편집할 수 있는 권한을 얻으려면 어떻게 해야 합니까?**

DAM 사용자는 [승인된 자산](approve-assets.md#approve-assets)에 대한 권한이 없을 수 있습니다. 자산의 승인 상태를 편집할 수 있는 권한을 얻으려면 관리자는 기본 또는 자산 폴더에 적용된 기타 메타데이터 스키마를 편집하여 **[!UICONTROL 검토 상태]** 필드에 대한 편집 권한을 제공할 수 있습니다. 자세한 내용은 [검토 상태 필드에 대한 편집을 비활성화하는 방법](approve-assets.md#configuration)을 참조하십시오.

+++

+++**비디오에 지원되는 파일 크기는 얼마입니까?**

OpenAPI 기능이 포함된 Dynamic Media는 긴 양식의 비디오를 지원합니다. 최대 50GB와 2시간의 비디오를 지원할 수 있습니다.

+++

+++**OpenAPI 기능 포함 Dynamic Media와 Dynamic Media 솔루션의 차이점은 무엇입니까?**

OpenAPI 기능 포함 Dynamic Media와 Dynamic Media는 각각 특수한 게재 기능을 제공하는 별개의 솔루션을 나타냅니다. 특정 요구 사항을 철저히 검토하여 필요에 가장 적합한 솔루션을 결정하는 것이 중요합니다.

Adobe의 일반적인 지침은 모든 통합 사용 사례(퍼스트 또는 서드파티 앱)에 OpenAPI 스택이 포함된 Dynamic Media를 활용하는 것입니다. Dynamic Media 스택과 이미 통합되어 있는 경우 OpenAPI 스택 URL의 구조가 다르므로 변경하지 않는 것이 좋습니다. 완전히 새로운 통합 사용 사례의 경우에만 OpenAPI 스택을 활용하십시오. 사용 사례에서 OpenAPI 스택에서 고급 수정자를 사용할 수 없는 경우 Adobe가 차이를 해결할 때까지 OpenAPI 스택은 사용하지 마십시오. AEM Assets Cloud Services의 기본 게재의 경우에도 사용 사례에 OpenAPI 스택에서 사용할 수 있는 수정자가 포함되어 있는 한 OpenAPI 스택을 평가할 수 있습니다. 결론적으로, Dynamic Media와 OpenAPI 스택이 포함된 Dynamic Media는 사용 사례의 특성에 따라 공존할 수 있습니다.

OpenAPI 기능이 포함된 Dynamic Media와 Dynamic Media의 주요 차이점은 다음과 같습니다.

| OpenAPI 기능이 포함된 Dynamic Media | Dynamic Media |
|---|---|
| [Assets as a Cloud Service에서만 사용 가능](/help/assets/dynamic-media-open-apis-overview.md#prerequisites-dynaminc-media-open-apis) | 추가 구성 및 프로비저닝 단계와 함께 On-Premise 또는 Adobe Managed Services에서도 사용할 수 있습니다. |
| [폭, 높이, 회전, 뒤집기, 품질 및 형식과 같이 지원되는 이미지 수정자 세트가 제한됨](/help/assets/deliver-assets-apis.md) | 다양한 이미지 수정자 세트 사용 가능 |
| [사용자, 역할, 날짜 및 시간에 따라 자산 게재가 제한됨](/help/assets/restrict-assets-delivery.md) | Dynamic Media에 게시된 자산에 모든 사용자가 액세스 가능 |
| 대부분의 개발자가 OpenAPI 사양에 익숙합니다. AEM Assets 확장성은 [마이크로 프론트엔드 자산 선택기](/help/assets/overview-asset-selector.md)를 사용하면 정말 간단해집니다. | 통합 커스터마이징을 개발하는 동안 장애물이 되는 SOAP 기반 API. |
| 버전 업데이트 및 메타데이터 수정을 포함하여 DAM에서 승인된 자산에 대한 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통해 OpenAPI 기능이 갖춘 Dynamic Media에 대해 10분이라는 짧은 TTL(Time-to-Live) 값을 구성하면 모든 작성 및 게시 인터페이스에서 10분 이내에 업데이트가 표시됩니다. | 권장 CDN TTL은 10시간입니다. 캐시 무효화 작업을 사용하여 TTL 값을 재정의할 수 있습니다. |
| 다운스트림 애플리케이션에 대한 자산 게재에는 승인된 자산만 사용할 수 있으며, 디지털 환경에서 브랜드 승인 자산을 사용할 수 있습니다. | Dynamic Media에 게시된 자산에 대한 업데이트는 승인 워크플로 없이 자동으로 게시되므로 디지털 환경에서 브랜드 승인 자산을 보장할 수 없습니다. |
| 게재된 자산 수를 기준으로 한 사용량 보고서. 이 기능은 곧 제공될 예정입니다. | 사용 보고서를 사용할 수 없습니다. 이 기능은 곧 제공될 예정입니다. |
| Assets as a Cloud Service 저장소에서 만료됨으로 표시된 자산은 더 이상 다운스트림 애플리케이션에서 사용할 수 없습니다. | 고유 자산 만료가 없습니다. 자산은 AEM as a Cloud Service 저장소에서 삭제될 때까지 공개 상태로 유지됩니다. |
| 이미지 사전 설정 및 비디오 스마트 자르기 기능을 지원하지 않습니다. | 이미지 사전 설정 및 비디오 스마트 자르기 기능을 지원합니다. |
| Dynamic Video 인코딩은 입력된 비디오를 기반으로 최상의 인코딩을 제공합니다. 기본 비디오 게재에는 설정이 필요하지 않습니다. | 표준 3은 입력 비디오와 관계없이 인코딩합니다(비디오 게재 성능에 영향을 미칠 수 있습니다). 비디오 비트 전송률에 따라 서로 다른 인코딩을 수동으로 설정해야 합니다. |
| 자산 UID 기반 URL을 추측하기는 어렵지만(URL 난독화 활성화) SEO는 최적화되어 있습니다. | URL 난독화는 URL 쿼리 매개변수에만 사용할 수 있습니다. URL의 Assets ID(자산 이름)를 인식할 수 있습니다. |

+++

+++**OpenAPI 기능 포함 Dynamic Media는 연결된 자산 기능의 한계를 어떻게 해결합니까?**

아래 테이블에는 두 솔루션의 주요 차이점이 요약되어 있습니다.

| OpenAPI 기능이 포함된 Dynamic Media | 연결된 자산 |
|---|---|
| 원격 DAM 배포의 자산은 AEM as a Cloud Service에서 사용할 수 있습니다. | 원격 DAM 배포의 자산은 AEM as a Cloud Service 또는 Adobe Managed Services에서 사용할 수 있습니다. |
| 원격 DAM 배포의 자산을 AEM Sites 인스턴스에서 사용할 수 있는 경우 자산 바이너리는 복사되지 않습니다. | 원격 DAM 배포의 자산을 AEM Sites 인스턴스에서 사용할 수 있는 경우 자산 바이너리가 복사됩니다. |
| AEM Assets에서 지원하는 모든 자산 형식 유형을 지원합니다. | 비디오는 지원되지 않습니다. |
| 원격 DAM 배포에서 자산을 가져오는 동안 로컬 Sites 배포에서 Dynamic Media를 사용할 수 있습니다. | 로컬 Sites 배포의 Dynamic Media는 읽기 전용입니다. |
| 원격 DAM 배포에 연결된 AEM Sites 인스턴스 수에는 제한이 없습니다. 원격 DAM에서 승인된 자산의 [역할을 구성하여 Sites 인스턴스의 자산에 대한 액세스를 제한](/help/assets/restrict-assets-delivery.md)할 수 있습니다. | 원격 DAM 배포에는 최대 4개의 AEM Sites 인스턴스를 연결할 수 있도록 제한됩니다. 이 한도를 늘리려면 추가적인 테스트가 요구됩니다. |
| 자산 선택기와 OpenAPI 기능 포함 Dynamic Media는 모두 사용자 정의 통합이 가능하도록 확장할 수 있습니다. | 연결된 자산 API는 사용자 정의 통합이 가능하도록 확장할 수 없습니다. |
| 버전 업데이트 및 메타데이터 수정을 포함하여 원격 DAM 배포에서 사용 가능한 승인된 자산에 대한 변경 사항은 10분의 짧은 TTL(수명) 값 내에 Sites 인스턴스로 자동 반영됩니다. | 원격 DAM 배포에 대한 자산 업데이트는 라이프사이클 이벤트를 통해 자동으로 처리되지만 OpenAPI 기능 포함 Dynamic Media에 비해 훨씬 더 많은 시간이 걸립니다. |
| 원격 DAM의 자산 메타데이터도 AEM Sites 인스턴스에서 사용할 수 있습니다. | 원격 DAM의 자산 메타데이터를 AEM Sites 인스턴스에서 사용할 수 없습니다. |

+++
