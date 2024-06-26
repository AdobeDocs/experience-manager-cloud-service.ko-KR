---
title: OpenAPI 기능이 포함된 Dynamic Media
description: OpenAPI 기능과 함께 Dynamic Media을 사용하는 이유 및 활성화 방법과 같은 주요 개념을 알아봅니다.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 0%

---

# OpenAPI 기능이 포함된 Dynamic Media {#new-dynaminc-media-apis-overview}

오늘날 빠르게 변화하는 디지털 세계에서 브랜드 디지털 자산의 잠재력을 최대한 발휘하는 것은 경쟁에서 앞서가는 데 매우 중요합니다. 전체적인 디지털 Assets 관리(DAM) 솔루션은 자산 거버넌스를 촉진하고, 브랜드 일관성을 증진하며, 브랜드 무결성과 탁월한 고객 경험을 보장하면서 컨텐츠 제공을 가속화합니다.

Dynamic Media의 OpenAPI 기능은 DAM을 애자일 기반의 효율적인 콘텐츠 공급망 생태계의 핵심으로 하여 에셋 거버넌스 및 전달을 보장합니다.

## OpenAPI 기능과 함께 Dynamic Media을 사용하는 이유는 무엇입니까? {#dynamic-media-open-api-features}

OpenAPI 기능이 포함된 Dynamic Media은 다음과 같은 주요 이점을 제공합니다.

* **원활한 통합**: OpenAPI 기능을 갖춘 Dynamic Media은 포괄적인 검색 및 게재 API 세트를 제공합니다. 개발자가 쉽게 다음을 수행할 수 있습니다. [자산과 애플리케이션 통합 제공](/help/assets/integrate-dynamic-media-open-apis.md). 애플리케이션에는 Adobe 및 타사 애플리케이션이 포함됩니다. 다음을 제공합니다. [Micro Frontend 자산 선택기 사용자 인터페이스](/help/assets/asset-selector.md) 을 눌러 승인된 에셋을 검색하고 선택합니다. 선택기는 React JS, Angular JS 및 Vanilla JS와 같은 JavaScript 프레임워크를 기반으로 하는 모든 애플리케이션과 손쉽게 통합할 수 있습니다.

* **디지털 자산의 중앙 집중식 관리**: DAM은 모든 디지털 에셋에 대한 신뢰할 수 있는 단일 소스입니다. 디지털 에셋은 AEM Assets에서 중앙에서 관리되며 에셋 바이너리를 복사하지 않고 게재 URL을 사용하여 참조함으로써 소비되는 애플리케이션에 전달됩니다.

* **실시간 업데이트**: 버전 업데이트 및 메타데이터 수정 등 DAM에서 승인된 에셋에 대한 모든 변경 사항이 자동으로 배달 URL에 반영됩니다. CDN을 통해 OpenAPI 기능이 있는 Dynamic Media에 대해 10분의 짧은 TTL(Time-to-Live) 값을 구성하면 10분 이내에 모든 작성 및 게시된 인터페이스에 업데이트가 표시됩니다.

* **브랜드 일관성**: 만 [브랜드 승인 자산](/help/assets/approve-assets.md) 다운스트림 애플리케이션에 노출됩니다. [브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 제어를 유지합니다](/help/assets/restrict-assets-delivery.md). 모든 채널 및 애플리케이션에서 브랜드 일관성을 보장하기 위해 승인된 최신 버전의 자산만 사용할 수 있습니다.

* **웹에 최적화된 게재**: 디지털 자산은 디지털 경험의 핵심 웹 활성화를 향상시키기 위해 웹에 최적화된 형식으로 제공됩니다. 여기에는 이미지에 대한 WebP 렌디션, 비디오에 대한 HLS 또는 DASH 프로토콜을 통한 적응형 스트리밍 및 문서에 대한 원본 렌디션 지원이 포함됩니다.

* **동적 자산 변환**: 당사 시스템에서는 이미지 수정자로 알려진 URL 매개 변수를 사용하여 즉석으로 이미지 변환을 허용합니다. [예: 너비, 높이, 회전, 뒤집기, 품질, 자르기, 형식 및 스마트 자르기](/help/assets/deliver-assets-apis.md). 변환된 렌디션은 동적으로 생성되고 CDN을 통해 원활하게 전달됩니다.

* **자산의 안전한 전달**: OpenAPI 기능이 있는 Dynamic Media은 디지털 에셋에 대한 액세스를 제어하는 메커니즘을 제공합니다. 사용자 역할 또는 그룹을 보안 자산에 대한 메타데이터로 지정하고 사전 정의된 기간을 설정합니다. [승인된 사용자만 이러한 에셋에 액세스할 수 있습니다.](/help/assets/restrict-assets-delivery.md). 제한된 기간 동안 권한이 없는 사용자에 대해 보안 자산의 게재 URL이 확인되지 않습니다.

* **정보에 입각한 결정을 내리는 데이터 인사이트(향후 예정)**: 에셋 관리 및 전달 외에도 CDN의 에셋 게재에 대한 게재 데이터 인사이트를 캡처하여 Brand Manager가 채널 전반에서 게재 지표를 추적할 수 있습니다. 이를 통해 자산 거버넌스의 지속적인 최적화와 전달 전략을 위한 데이터 중심의 의사 결정을 내릴 수 있습니다.

![Dynamic Media Open API 데이터 흐름 다이어그램](assets/dm-openapi-dfd.png)

## OpenAPI 기능을 사용하여 Dynamic Media에 액세스하기 위한 사전 요구 사항 {#prerequisites-dynaminc-media-open-apis}

OpenAPI 기능을 사용하여 Dynamic Media에 액세스하려면 다음에 대한 라이센스가 있어야 합니다.

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## OpenAPI 기능을 사용하여 Dynamic Media을 활성화하는 방법 {#enable-dynamic-media-open-apis}

AEM as a Cloud Service에서 OpenAPI 기능을 사용하는 Dynamic Media을 활성화하기 위한 요청을 제출하기 전에 이미 활성화되어 있지 않은지 확인하십시오.

한 번 [전제 조건](#prerequisites-dynaminc-media-open-apis) 이 충족되며 AEM as a Cloud Service 인스턴스에서 OpenAPI 기능을 사용하는 Dynamic Media이 활성화된 경우 저장소의 각 승인된 에셋에 대해 게재 URL이 제공됩니다. 게재 URL을 복사하는 방법에 대한 자세한 내용은 [승인된 에셋의 게재 URL 복사](approve-assets.md#copy-delivery-url-approved-assets) . Adobe은 이 메서드를 사용하여 OpenAPI 기능이 있는 Dynamic MediaAEM as a Cloud Service 가 활성화되었는지 확인한 후 활성화를 위한 지원 티켓을 제출하는 것이 좋습니다.

AEM as a Cloud Service에서 OpenAPI 기능을 사용하는 Dynamic Media을 활성화하려면 다음 세부 정보가 포함된 Adobe 지원 티켓을 제출하십시오.

* Cloud Service 프로그램 및 환경 ID

* OpenAPI 기능 통합을 통해 Dynamic Media을 해결하는 사용 사례에 대한 세부 사항입니다.

* OpenAPI 기능과 Dynamic Media과 통합할 다운스트림 애플리케이션에 대한 세부 정보입니다.

  >[!NOTE]
  >
  > Adobe이 아닌 애플리케이션과 통합하려면 애플리케이션이 호스팅되는 화이트리스트에 도메인 이름을 제공하십시오.

* 통합 프로젝트와 관련된 주요 고객 연락처 세부 정보.

* 주요 Adobe 계정 팀원 목록(이메일).

지원 티켓을 제출하면 Adobe에서 Cloud Service 환경에서 OpenAPI 기능을 사용하는 Dynamic Media을 활성화하고 IMS 클라이언트 ID 등의 세부 정보를 공유하여 통합을 계속할 수 있습니다.

>[!NOTE]
>
>제외 `/conf/global/settings/dam/assets-configurations/assetdelivery` 모든 컨텐츠 패키지에서 OpenAPI 기능으로 Dynamic Media이 비활성화되지 않도록 합니다.

## 주요 기능에 대해 자세히 알아보기 {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Experience Manager Assets에서 에셋 승인" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
      <strong>Experience Manager Assets에서 에셋 승인</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets에서 에셋을 승인하여 에셋 관리를 간소화하여 에셋 처리에 대한 통제되고 효율적인 프로세스를 보장합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="AEM Assets을 다운스트림 애플리케이션과 통합" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong>AEM Assets을 다운스트림 애플리케이션과 통합</strong>
      </a>
   </div>
   <p>
      <em>검색 및 게재 API를 사용하여 자체 사용자 지정 사용자 인터페이스를 Experience Manager Assets 저장소와 통합하거나 Adobe의 Micro-Frontend 자산 선택기를 사용하십시오.</em>
   </p>
</td>
<td>
   <a href="/help/assets/asset-selector.md">
   <img alt="Adobe의 자산 선택기" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/asset-selector.md">
      <strong>Adobe의 마이크로 프론트엔드 자산 선택기</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 저장소와 상호 작용하여 에셋을 검색한 다음 애플리케이션 작성 환경에서 사용하는 사용자 인터페이스입니다.</em>
   </p>
</td>
</table>
<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="에셋 검색 Experience Manager Assets 저장소" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
      <strong>Experience Manager Assets 저장소에서 에셋 검색</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 저장소에서 에셋을 검색하여 다운스트림 애플리케이션에 전달할 수 있습니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="다운스트림 애플리케이션에 자산 제공" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
      <strong>다운스트림 애플리케이션에 자산 제공</strong>
      </a>
   </div>
   <p>
      <em>게재 URL을 사용하여 통합 다운스트림 애플리케이션에 자산을 게재합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Experience Manager의 자산에 대한 액세스 제한" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Experience Manager의 자산에 대한 액세스 제한</strong>
      </a>
   </div>
   <p>
      <em> DAM 관리자 또는 브랜드 관리자는 AEM as a Cloud Service 작성자 인스턴스에서 승인된 에셋에 대한 역할을 구성하여 액세스를 제한합니다.</em>
   </p>
</td>
</table>

