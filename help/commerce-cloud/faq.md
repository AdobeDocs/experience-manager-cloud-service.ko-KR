---
title: AEM - Commerce Integration Framework를 사용하여 상거래 통합 FAQ
description: AEM - Commerce Integration Framework를 사용하여 상거래 통합 FAQ
exl-id: 0a946d98-22c7-445d-984a-9e09c306ce45
source-git-commit: 05a412519a2d2d0cba0a36c658b8fed95e59a0f7
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# AEM - Commerce Integration Framework를 사용하여 상거래 통합 FAQ

## 1. CIF GraphQL은 상거래에 대해서만 사용되거나 AEM에서 작성된 콘텐츠를 쿼리하는 데 사용할 수 있습니까? JCR?

Adobe은 모든 상거래 관련 데이터에 대해 Adobe Commerce의 GraphQL API를 공식적인 상거래 API로 채택했습니다. 따라서 AEM은 GraphQL을 사용하여 I/O Runtime을 통해 Adobe Commerce 및 모든 상거래 엔진과 상거래 데이터를 교환합니다. 이 GraphQL API는 AEM GraphQL API와 독립적으로 컨텐츠 조각에 액세스합니다.

## 2. 제품 자산(이미지)을 Adobe Commerce 관리자를 통해 AEM에서 저장 및 참조할 수 있습니까? Dynamic Media의 자산을 어떻게 사용할 수 있습니까?

공식적인 AEM Assets - Adobe Commerce 통합을 사용할 수 없습니다. 에는 파트너 커넥터가 있습니다 [marketplace](https://marketplace.magento.com/bounteous-dam.html).

또는 해결 방법으로, 제품 자산(이미지)을 AEM Assets에 저장할 수 있지만, Adobe Commerce에 자산 URL을 수동으로 저장해야 합니다. Dynamic Media은 현재 AEM Assets의 일부이며 동일한 방식으로 작동합니다.

## 3. 상거래 솔루션이 배포되는 위치에 문제가 있습니까? (온프레미스 또는 클라우드에서)

아니요. 상거래 솔루션이 배포되는 위치에는 문제가 없습니다. CIF 및 AEM 스토어프런트는 배포 모델에 관계없이 작동합니다. 그러나 솔루션이 권장 E2E 참조 아키텍처와 함께 배포되는 경우 일반적인 엔터프라이즈 고객 프로필을 나타내는 성능 KPI에 대해 E2E 테스트를 실행할 수 있습니다. 벤치마크로 사용할 수 있는 추가 정보가 제공됩니다.

## 4. AEM에서 카탈로그 페이지 또는 제품 페이지를 작성하는 방법 AEM에서는 어떻게 지속됩니까?

카탈로그 페이지와 제품 페이지는 일반 카탈로그 및 제품 페이지 템플릿을 기반으로 AEM에서 동적으로 만들어지고 캐시됩니다. 제품 또는 카탈로그 데이터를 AEM에 가져와서 저장하지 않습니다.

## 5. 상거래 솔루션에서 제품 데이터를 업데이트할 때 이것이 AEM에 대한 실시간 푸시 입니까? 아니면 일괄 처리인가요?

AEM Cloud Service과 함께 사용되는 CIF 추가 기능을 사용하면 데이터를 상거래 솔루션에서 AEM 온디맨드 로 전달할 수 있습니다. 따라서 상거래 솔루션에 업데이트가 있는 경우 실시간 푸시 또는 배치 프로세스가 아닙니다.

## 6. CIF를 지원하는 AEM은 어떤 카탈로그 크기를 지원합니까?

이것은 고려해야 할 몇 가지 추가 사항에 따라 다릅니다. 카탈로그 데이터 및 페이지의 캐시 비율은 얼마입니까? 최대 시간 동안 동시 요청이 몇 개 예상됩니까? 상거래 솔루션의 API는 얼마나 확장 가능합니까?

## 7. PIM은 이 프레임워크로 어떻게 재생됩니까?

PIM 데이터는 GraphQL 요청을 통해 AEM 및 클라이언트에 노출됩니다. PIM을 상거래 엔진(Adobe Commerce 등)과 통합하여 상거래 엔진에서 PIM 데이터를 검색할 수 있도록 하는 것이 좋습니다.

## 8. Dispatcher를 통해 가격 및 기타 데이터를 캐시합니까? 이 경우 캐시 무효화 문제가 자주 발생합니까?

가격 또는 재고와 같은 동적 데이터는 Dispatcher에 캐시되지 않습니다. GraphQL API를 통해 직접 웹 구성 요소를 사용하여 클라이언트 측에서 동적 데이터를 가져옵니다. 정적 데이터(예: 제품 또는 카테고리 데이터)만 Dispatcher에 캐시됩니다. 제품 데이터가 변경되면 캐시 무효화가 필요합니다.

## 9. AEM Dispatcher에 대한 캐시 무효화는 AEM 및 Commerce에서 어떻게 작동합니까?

Dispatcher에 캐시된 페이지에 대해 TTL 기반 캐시 무효화를 설정하는 것이 좋습니다. 가격 또는 주식 등의 동적 정보는 데이터 클라이언트측에서 렌더링하는 것이 좋습니다. TTL 기반 캐시 무효화에 대한 자세한 내용은 다음을 참조하십시오. [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 10. Commerce를 사용하여 AEM 컨텐츠 간에 통합 검색에 대한 권장 사항이 있습니까?

제품 검색 참조 구현이 제공되지만 콘텐츠가 있는 통합 검색이 없습니다. 이 기능은 일반적으로 고객별로 다르며 프로젝트별 수준에서 더 잘 해결됩니다.

## 11. CIF를 사용하여 Search는 AEM 및 Commerce에서 어떻게 작동합니까?

CIF에서는 검색 창 및 검색 결과 구성 요소를 제공합니다. 검색 막대 구성 요소는 검색어가 있는 GraphQL 요청을 상거래 솔루션으로 보낸 다음, 제품 이름, 가격, SLUG 등을 포함하는 제품 목록을 반환합니다. 그러면 검색 결과 구성 요소가 AEM에서 만든 검색 결과 페이지의 갤러리 보기에 검색 결과를 표시합니다. 검색은 기본 전체 텍스트 검색을 지원합니다. SLUG/url 키를 사용하여 PDP에 대한 참조를 빌드합니다.

## 12. MSM 또는 번역에서 제품 데이터를 어떻게 사용할 수 있습니까?

제품 데이터는 일반적으로 PIM 또는 Adobe Commerce에서 이미 번역됩니다. AEM - Adobe Commerce 통합은 여러 Adobe Commerce 스토어 및 저장소 보기에 대한 연결을 지원합니다. MSM 설정에서 일반적으로 하나의 AEM 사이트가 하나의 Adobe Commerce 저장소 보기에 연결됩니다.

## 13. 상업용 텍스트로 제품 데이터를 향상시키는 방법이 있습니까? 이 작업은 어디에서 수행합니까? AEM에서 또는 상거래 솔루션에서는?

AEM에서 마케팅 관련 데이터 및 컨텐츠를 관리하는 것이 좋습니다. 컨텐츠 조각을 사용하여 상거래 솔루션의 제품 데이터를 추가 특성으로 장식하거나, 비정형 컨텐츠에 대한 경험 조각을 만들어 제품에 연결합니다.

## 14. 전체 프레젠테이션 계층에서 AEM을 사용할 때 PCI 규정 준수를 어떻게 보장할 수 있습니까?

추상적인 결제 방법을 사용하는 것이 좋습니다. 이렇게 하면 브라우저 클라이언트가 결제 게이트웨이 공급자와 직접 통신하므로 Adobe 또는 상거래 솔루션도 카드 소지자 데이터를 보유하거나 전달할 수 없습니다. 이 접근 방식에서는 레벨 3 PCI 규정 준수가 필요합니다. 그러나 직원이 시스템 및 데이터와 상호 작용하는 방법과 같이 PCI를 완벽하게 준수하도록 고려해야 할 추가 사항이 있습니다. Adobe Commerce PCI 준수에 대한 자세한 내용은 다음을 참조하십시오. [PCI 규정 준수 요구 사항](https://business.adobe.com/products/magento/pci-compliance.html).

## 15. AEM 및 Adobe Commerce 클라우드 버전을 사용하는 경우 이 공동 솔루션 PCI를 준수합니까?

예. 요청 시 자체 평가 질문 D 및 규정 준수 증명을 사용할 수 있습니다.

## 16. I/O Runtime 평가판 라이센스를 요청하려면 어떻게 해야 합니까?

I/O Runtime을 사용하도록 평가판 라이센스를 요청할 수 있습니다 [여기](https://developer.adobe.com/app-builder/trial/).
