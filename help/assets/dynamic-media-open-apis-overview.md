---
title: OpenAPI 기능이 포함된 Dynamic Media
description: OpenAPI 기능이 포함된 Dynamic Media를 사용하는 이유 및 활성화 방법과 같은 주요 개념을 알아봅니다.
role: User
exl-id: 658b6eff-9f5a-4166-9ff6-5dc8eb92ada3
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 97%

---

# OpenAPI 기능이 포함된 Dynamic Media {#new-dynaminc-media-apis-overview}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
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
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>OpenAPI 기능이 포함된 Dynamic Media 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE OpenAPI 기능이 포함된 Dynamic Media 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

빠르게 변화하는 오늘날의 디지털 세계에서 브랜드 디지털 자산의 잠재력을 최대한 활용하는 것은 경쟁에서 앞서 나가기 위해 매우 중요합니다. 총체적인 디지털 자산 관리(DAM) 솔루션은 자산 거버넌스를 촉진하고, 브랜드 일관성을 촉진하며, 콘텐츠 게재를 가속화하는 동시에 브랜드 무결성과 탁월한 고객 경험을 보장합니다.

OpenAPI 기능 포함 Dynamic Media는 민첩하고 효율적인 콘텐츠 공급망 생태계의 핵심에 DAM을 배치하여 자산 거버넌스와 게재를 보장합니다.

## OpenAPI 기능이 포함된 Dynamic Media을 사용해야 하는 이유 {#dynamic-media-open-api-features}

OpenAPI 기능이 포함된 Dynamic Media는 다음과 같은 주요 이점을 제공합니다.

* **원활한 통합**: OpenAPI 기능이 포함된 Dynamic Media는 포괄적인 검색 및 게재 API 세트를 제공합니다. 이를 통해 개발자가 [자산 게재를 애플리케이션과 쉽게 통합](/help/assets/integrate-dynamic-media-open-apis.md)할 수 있습니다. 이러한 애플리케이션에는 Adobe 및 서드파티 애플리케이션이 포함됩니다. 승인된 자산을 검색하고 선택할 수 있는 [마이크로 프론트엔드 자산 선택기 사용자 인터페이스](/help/assets/overview-asset-selector.md)를 제공합니다. 선택기는 React JS, Angular JS, Vanilla JS와 같은 JavaScript 프레임워크를 기반으로 하는 모든 애플리케이션과 쉽게 통합할 수 있습니다.

* **디지털 자산의 중앙 관리**: DAM은 모든 디지털 자산에 대한 단일 정보 소스입니다. 디지털 자산은 AEM Assets에서 중앙 집중식으로 관리되며, 자산 바이너리를 복사하지 않고 게재 URL을 사용한 참조를 통해 소비 애플리케이션에 전달됩니다.

* **실시간 업데이트**: 버전 업데이트 및 메타데이터 수정을 포함하여 DAM에서 승인된 자산에 대한 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통해 OpenAPI 기능이 갖춘 Dynamic Media에 대해 10분이라는 짧은 TTL(Time-to-Live) 값을 구성하면 모든 작성 및 게시 인터페이스에서 10분 이내에 업데이트가 표시됩니다.

* **브랜드 일관성**: [브랜드 승인 자산](/help/assets/approve-assets.md)만 다운스트림 애플리케이션에 노출됩니다. [브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 통제권을 유지합니다](/help/assets/restrict-assets-delivery.md). 승인된 최신 버전의 자산만 사용할 수 있어 모든 채널과 애플리케이션에서 브랜드 일관성을 보장합니다.

* **웹에 최적화된 게재**: 디지털 자산은 웹에 최적화된 형식으로 제공되어 디지털 경험의 핵심 웹 바이탈을 향상시킵니다. 여기에는 이미지에 대한 WebP 렌디션 지원, 비디오에 대한 HLS 또는 DASH 프로토콜을 통한 적응형 스트리밍, 문서에 대한 원본 렌디션이 포함됩니다.

* **동적 자산 변환**: 당사 시스템은 이미지 수정자로 알려진 URL 매개변수를 사용하여 즉석에서 이미지를 변환할 수 있습니다. [예: 폭, 높이, 회전, 뒤집기, 품질, 자르기, 포맷 및 스마트 자르기](/help/assets/deliver-assets-apis.md). 변환된 렌디션은 동적으로 생성되며 CDN을 통해 원활하게 게재됩니다.

* **자산의 안전한 게재**: OpenAPI 기능 포함 Dynamic Media는 디지털 자산에 대한 액세스를 제어할 수 있는 메커니즘을 제공합니다. 보안 대상 자산의 메타데이터로 사용자 역할 또는 그룹을 지정하고 [승인된 사용자만 이러한 자산에 액세스](/help/assets/restrict-assets-delivery.md)할 수 있는 사전 정의 기간을 설정할 수 있습니다. 보안 자산의 게재 URL은 제한된 기간 동안 승인되지 않은 사용자가 접근할 수 없습니다.

* **정보에 입각한 의사 결정을 내릴 수 있는 데이터 인사이트(향후 예정)**: 자산 관리 및 게재 외에도 CDN의 자산 게재에 대한 배송 데이터 인사이트를 확보하여 브랜드 관리자가 여러 채널에서 게재 지표를 추적할 수 있도록 지원합니다. 이를 통해 자산 거버넌스 및 게재 전략의 지속적인 최적화를 위해 데이터 기반 의사 결정을 내릴 수 있습니다.

![Dynamic Media Open API 데이터 흐름 다이어그램](assets/dm-openapi-dfd.png)

## OpenAPI 기능이 포함된 Dynamic Media에 액세스하기 위한 전제 조건 {#prerequisites-dynaminc-media-open-apis}

OpenAPI 기능이 포함된 Dynamic Media에 액세스하려면 다음 라이선스가 있어야 합니다.

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## OpenAPI 기능이 포함된 Dynamic Media를 활성화하는 방법은 무엇입니까? {#enable-dynamic-media-open-apis}

AEM as a Cloud Service에 OpenAPI 기능이 포함된 Dynamic Media를 활성화하는 요청을 제출하기 전에 이미 활성화되어 있지 않은지 확인합니다.

[전제 조건](#prerequisites-dynaminc-media-open-apis)이 충족되고 AEM as a Cloud Service 인스턴스에서 OpenAPI 기능이 포함된 Dynamic Media를 활성화하면 저장소에 승인된 각 자산에 대해 게재 URL을 사용할 수 있습니다. 게재 URL을 복사하는 방법에 대한 자세한 내용은 [승인된 자산의 게재 URL 복사](approve-assets.md#copy-delivery-url-approved-assets)를 참조하십시오. Adobe는 이 방법을 사용하여 지원 티켓을 제출하기 전에 AEM as a Cloud Service에서 OpenAPI 기능 포함 Dynamic Media가 활성화되어 있는지 확인할 것을 권장합니다.

AEM as a Cloud Service에서 OpenAPI 기능 포함 Dynamic Media를 활성화하려면 다음의 세부 정보가 포함된 Adobe 지원 티켓을 제출하십시오.

* Cloud Services 프로그램 및 환경 ID

* OpenAPI 기능이 포함된 Dynamic Media 통합으로 해결해야 할 사용 사례에 대한 세부 정보.

* OpenAPI 기능이 포함된 Dynamic Media와 통합할 다운스트림 애플리케이션에 대한 세부 정보.

  >[!NOTE]
  >
  >Adobe 이외의 애플리케이션과 통합하려면 애플리케이션이 호스팅되는 허용 목록에 도메인 이름을 입력합니다.

* 통합 프로젝트에 참여한 주요 고객 연락처의 세부 정보.

* 주요 Adobe 계정 팀원 목록(이메일).

지원 티켓을 제출하면 Adobe는 Cloud Services 환경에서 OpenAPI 기능이 포함된 Dynamic Media를 활성화하고 IMS 클라이언트 ID와 같은 세부 정보를 공유하여 통합을 진행할 수 있습니다.

>[!NOTE]
>
>OpenAPI 기능이 포함된 Dynamic Media의 비활성화를 방지하기 위해 콘텐츠 패키지에서 `/conf/global/settings/dam/assets-configurations/assetdelivery`를 제외합니다.

## 주요 기능에 대해 자세히 알아보기 {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Experience Manager Assets에서 자산 승인" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
      <strong>Experience Manager Assets에서 자산 승인</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets에서 자산을 승인하여 자산 관리를 간소화하고, 자산 처리에 대한 통제되고 효율적인 프로세스를 보장합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="다운스트림 애플리케이션과 AEM Assets 통합" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong>다운스트림 애플리케이션과 AEM Assets 통합</strong>
      </a>
   </div>
   <p>
      <em>검색 및 게재 API를 사용하여 사용자 정의 사용자 인터페이스를 Experience Manager Assets 저장소와 통합하거나 Adobe의 마이크로 프론트엔드 자산 선택기를 사용합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Adobe의 자산 선택기" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>Adobe의 마이크로 프론트엔드 자산 선택기</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 저장소와 상호작용하여 자산을 검색한 다음 애플리케이션 작성 환경에서 사용할 수 있는 사용자 인터페이스입니다.</em>
   </p>
</td>
</table>
<table>



<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="Experience Manager Assets 저장소에서 자산 검색" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
      <strong>Experience Manager Assets 저장소에서 자산 검색</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 저장소에서 자산을 검색하여 다운스트림 애플리케이션에 게재할 수 있습니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="다운스트림 애플리케이션에 자산 게재" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
      <strong>다운스트림 애플리케이션에 자산 게재</strong>
      </a>
   </div>
   <p>
      <em>게재 URL을 사용하여 통합된 다운스트림 애플리케이션에 자산을 게재합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Experience Manager에서 자산에 대한 액세스 제한" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Experience Manager에서 자산에 대한 액세스 제한</strong>
      </a>
   </div>
   <p>
      <em> DAM 관리자 또는 브랜드 관리자는 AEM as a Cloud Service 작성자 인스턴스에서 승인된 자산에 대한 역할을 구성하여 액세스를 제한합니다.</em>
   </p>
</td>

</table>
<table>
<td>
   <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
   <img alt="원격 AEM Assets를 AEM Sites와 통합" src="./assets/connected-assets-rdam.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
      <strong>원격 AEM Assets를 AEM Sites와 통합</strong>
      </a>
   </div>
   <p>
      <em>원격 AEM Assets를 AEM Sites 환경과 통합하는 방법을 알아봅니다. </em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media-open-apis-faqs.md">
   <img alt="OpenAPI 기능이 포함된 Dynamic Media에 대해 자주 묻는 질문" src="./assets/dynamic-media-faqs.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-faqs.md">
      <strong>OpenAPI 기능이 포함된 Dynamic Media에 대해 자주 묻는 질문</strong>
      </a>
   </div>
   <p>
      <em>OpenAPI 기능 포함 Dynamic Media와 관련하여 가장 많이 묻는 질문에 대한 답변을 받아보십시오.</em>
   </p>
</td>
<td>
   <a href="/help/assets/configure-custom-domain.md">
   <img alt="사용자 정의 도메인 구성" src="./assets/configure-custom-domain.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-custom-domain.md">
      <strong>사용자 정의 도메인 구성</strong>
      </a>
   </div>
   <p>
      <em>AEM as a Cloud Service에는 기본 도메인이 제공되지만 사용자의 필요에 따라 사용자 정의할 수 있습니다.</em>
   </p>
</td>

</table>
