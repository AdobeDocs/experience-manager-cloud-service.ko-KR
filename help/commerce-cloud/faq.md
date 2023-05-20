---
title: AEM - Commerce Integration Framework를 사용하여 Commerce 통합 FAQ
description: AEM - Commerce Integration Framework를 사용하여 Commerce 통합 FAQ
exl-id: 0a946d98-22c7-445d-984a-9e09c306ce45
source-git-commit: d925310603961f1f3721c283fc247105459e9c0f
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 0%

---

# AEM - Commerce Integration Framework를 사용하여 Commerce 통합 FAQ

## 1. CIF GraphQL은 상거래에만 사용됩니까? 또는 AEM JCR에서 작성된 콘텐츠를 쿼리하는 데 사용할 수 있습니까?

Adobe은 모든 상거래 관련 데이터를 위한 공식 상거래 API로 Adobe Commerce의 GraphQL API를 채택했습니다. 따라서 AEM은 GraphQL을 사용하여 I/O Runtime을 통해 Adobe Commerce 및 상거래 엔진과 상거래 데이터를 교환합니다. 이 GraphQL API는 콘텐츠 조각에 액세스하기 위해 AEM GraphQL API와 독립적입니다.

## 2. Adobe Commerce 관리자를 통해 AEM에서 제품 에셋(이미지)을 저장하고 참조할 수 있습니까? Dynamic Media의 에셋은 어떻게 사용할 수 있습니까?

공식 AEM Assets - Adobe Commerce 통합을 사용할 수 없습니다. 에서 사용할 수 있는 파트너 커넥터가 있습니다. [마켓플레이스](https://marketplace.magento.com) <!-- THIS IS THE OLD URL THAT WAS USED. IT WAS 404 (https://marketplace.magento.com/bounteous-dam.html) -->

또는 해결 방법으로 AEM Assets에 제품 에셋(이미지)을 저장할 수 있지만 Adobe Commerce에 에셋 URL을 수동으로 저장해야 합니다. Dynamic Media은 현재 AEM Assets의 일부이며 동일한 방식으로 작동합니다.

## 3. 커머스 솔루션이 어디에 배포되었는지가 중요합니까? (온프레미스 또는 클라우드)

아니요. 상거래 솔루션이 배포되는 위치는 중요하지 않습니다. CIF와 AEM Storefront는 배포 모델에 관계없이 작동합니다. 그러나 솔루션이 권장 E2E 참조 아키텍처를 사용하여 배포된 경우 일반적인 엔터프라이즈 고객 프로필을 나타내는 성능 KPI에 대해 E2E 테스트를 실행할 수 있습니다. 이 방법은 벤치마크로 사용할 수 있는 추가 정보를 제공합니다.

## 4. AEM에서 카탈로그 페이지 또는 제품 페이지는 어떻게 생성됩니까? AEM에서는 어떻게 지속됩니까?

카탈로그 페이지 및 제품 페이지는 일반 카탈로그 및 제품 페이지 템플릿을 기반으로 AEM에서 동적으로 생성되고 캐시됩니다. 제품 또는 카탈로그 데이터를 가져와서 AEM에 저장하지 않습니다.

## 5. 상거래 솔루션에서 제품 데이터를 업데이트할 때 AEM에 실시간으로 푸시됩니까? 아니면 일괄 처리입니까?

AEM Cloud Service과 함께 사용되는 CIF 추가 기능을 사용하면 데이터를 상거래 솔루션에서 AEM on-demand로 전달할 수 있습니다. 따라서 상거래 솔루션에 업데이트가 있는 경우 실시간 푸시 또는 일괄 처리 프로세스가 아닙니다.

## 6. CIF가 포함된 AEM은 어떤 카탈로그 크기를 지원합니까?

이는 고려해야 하는 몇 가지 추가 측면에 따라 다릅니다. 카탈로그 데이터 및 페이지의 캐시 비율은 얼마입니까? 피크 시간 동안 몇 개의 동시 요청을 예상합니까? 상거래 솔루션의 API는 얼마나 확장 가능합니까?

## 7. PIM은 이 프레임워크에서 어떻게 작동합니까?

PIM 데이터는 GraphQL 요청을 통해 AEM 및 클라이언트에 노출됩니다. 권장 사항은 PIM을 상거래 엔진(Adobe Commerce 또는 기타)과 통합하여 PIM 데이터를 상거래 엔진에서 검색할 수 있도록 하는 것입니다.

## 8. Dispatcher를 통해 가격 책정 및 기타 데이터도 캐시합니까? 자주 발생하는 캐시 무효화 문제가 있습니까?

가격 또는 인벤토리와 같은 동적 데이터는 Dispatcher에 캐시되지 않습니다. 동적 데이터는 GraphQL API를 통해 웹 구성 요소로 클라이언트측에서 직접 가져옵니다. 정적 데이터(예: 제품 또는 범주 데이터)만 Dispatcher에 캐시됩니다. 제품 데이터가 변경되면 캐시 무효화가 필요합니다.

## 9. AEM Dispatcher에 대한 캐시 무효화는 AEM 및 commerce에서 어떻게 작동합니까?

Dispatcher에 캐시된 페이지에 대한 TTL 기반 캐시 무효화를 설정하는 것이 좋습니다. 가격 또는 주식과 같은 동적 정보의 경우 클라이언트측 데이터를 렌더링하는 것이 좋습니다. TTL 기반 캐시 무효화에 대한 자세한 내용은 [Dispatcher 캐시 최적화](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17458.html) 및 [AEM 성능 최적화](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/performance.html).

## 10. Commerce를 사용하는 AEM 콘텐츠 전반에 대한 통합 검색에 대한 권장 사항이 있습니까?

제품 검색 참조 구현이 제공되지만 콘텐츠가 포함된 통합 검색은 제공되지 않습니다. 이 기능은 고객별로 다르며 프로젝트별 수준에서 더 잘 해결됩니다.

## 11. Search는 AEM 및 commerce에서 CIF를 사용하여 어떻게 작동합니까?

CIF는 검색 창 및 검색 결과 구성 요소를 제공합니다. 검색 창 구성 요소는 검색어와 함께 GraphQL 요청을 상거래 솔루션으로 보낸 다음, 제품 이름, 가격, SLUG 등이 포함된 제품 목록을 반환합니다. 그런 다음 검색 결과 구성 요소는 AEM에서 만든 검색 결과 페이지의 갤러리 보기에 검색 결과를 표시합니다. 검색은 기본 전체 텍스트 검색을 지원합니다. SLUG/url 키를 사용하여 PDP에 대한 참조를 빌드합니다.

## 12. 제품 데이터를 MSM이나 번역에서 어떻게 사용할 수 있습니까?

제품 데이터는 이미 PIM 또는 Adobe Commerce에서 번역되었습니다. AEM - Adobe Commerce 통합은 여러 Adobe Commerce 스토어 및 스토어 보기에 대한 연결을 지원합니다. MSM 설정에서 일반적으로 한 AEM 사이트가 한 Adobe Commerce 스토어 보기에 연결됩니다.

## 13. 상업용 텍스트로 제품 데이터를 향상시킬 수 있는 방법이 있습니까? 이거 어디서 하는 거야? AEM에서? 상거래 솔루션에서?

AEM에서 마케팅 관련 데이터 및 콘텐츠를 관리하는 것이 좋습니다. 콘텐츠 조각을 사용하여 상거래 솔루션의 제품 데이터를 추가 속성으로 장식하거나 비정형 콘텐츠에 대한 경험 조각을 만들어 제품과 연결할 수 있습니다.

## 14. 전체 프레젠테이션 레이어에서 AEM을 사용할 때 PCI 규정 준수를 보장하려면 어떻게 해야 합니까?

추상화된 결제 방법을 사용하는 것이 좋습니다. 이렇게 하면 브라우저 클라이언트가 결제 게이트웨이 공급자와 직접 통신하므로 Adobe 또는 상거래 솔루션이 카드 소지자 데이터를 보관하거나 전달하지 못합니다. 이 방식에서는 레벨 3 PCI 규정 준수만 필요합니다. 그러나 직원이 시스템 및 데이터와 상호 작용하는 방식과 같이 완전한 PCI 준수로 간주할 추가 사항이 있습니다. Adobe Commerce PCI 규정 준수에 대한 자세한 내용은 다음을 참조하십시오. [PCI 규정 준수 요구 사항](https://business.adobe.com/products/magento/pci-compliance.html).

## 15. AEM 및 Adobe Commerce 클라우드 버전을 사용하는 경우 이 공동 솔루션은 PCI를 준수합니까?

예. 자체 평가 설문지 D와 규정 준수 증명서는 요청 시 제공됩니다.

## 16. I/O 런타임 체험판 라이센스를 요청하려면 어떻게 해야 합니까?

I/O Runtime을 사용하기 위해 체험판 라이센스를 요청할 수 있습니다. [여기](https://developer.adobe.com/app-builder/trial/).
