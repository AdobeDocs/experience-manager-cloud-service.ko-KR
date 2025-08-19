---
title: AEM - Commerce Integration Framework를 사용한 전자 상거래 통합 FAQ
description: AEM - Commerce Integration Framework를 사용한 전자 상거래 통합 FAQ
exl-id: 0a946d98-22c7-445d-984a-9e09c306ce45
feature: Commerce Integration Framework
role: Admin, Architect, User
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 97%

---


# AEM - Commerce Integration Framework를 사용한 전자 상거래 통합 FAQ

## &#x200B;1. CIF GraphQL은 상거래에만 사용됩니까 아니면 AEM JCR에서 작성된 콘텐츠를 쿼리하는 데 사용할 수 있습니까? {#faq-1}

Adobe는 모든 상거래 관련 데이터용 공식 상거래 API로 Adobe Commerce의 GraphQL API를 채택했습니다. 따라서 AEM은 GraphQL을 사용하여 I/O Runtime을 통해 Adobe Commerce 및 모든 상거래 엔진과 상거래 데이터를 교환합니다. 이 GraphQL API는 콘텐츠 조각에 액세스하도록 AEM의 GraphQL API와 별개입니다.

## &#x200B;2. Adobe Commerce 관리자를 통해 AEM에서 제품 자산(이미지)을 저장하고 참조할 수 있습니까? Dynamic Media의 자산을 어떻게 사용할 수 있습니까? {#faq-2}

공식 AEM Assets - Adobe Commerce 통합이 제공되지 않습니다. [마켓플레이스에서 사용할 수 있는 파트너 커넥터가 있습니다.](https://commercemarketplace.adobe.com)

또는 차선책으로 AEM Assets에 제품 자산(이미지)을 저장할 수 있지만 Adobe Commerce에 자산 URL을 수동으로 저장해야 합니다. 이제 Dynamic Media는 AEM Assets 일부이며 동일한 방식으로 작동합니다.

## &#x200B;3. 상거래 솔루션의 배포 위치가 중요합니까? (On-prem 또는 클라우드에서) {#faq-3}

아니요, 상거래 솔루션의 배포 위치는 중요하지 않습니다. CIF 및 AEM Storefront는 배포 모델에 관계없이 작동합니다. 단, 권장되는 E2E 참조 아키텍처를 사용하여 솔루션을 배포하는 경우에는 일반적인 기업 고객 프로필을 나타내는 성능 KPI에 대해 E2E 테스트를 실행할 수 있습니다. 이 메서드는 벤치마크로 사용할 수 있는 추가 정보를 제공합니다.

## &#x200B;4. AEM에서 카탈로그 페이지 또는 제품 페이지는 어떻게 생성됩니까? AEM에서 어떻게 지속됩니까? {#faq-4}

카탈로그 페이지 및 제품 페이지는 일반 카탈로그 및 제품 페이지 템플릿을 기반으로 AEM에서 동적으로 생성되고 캐시됩니다. 제품 또는 카탈로그 데이터는 AEM에 가져와서 저장되지 않습니다.

## &#x200B;5. 상거래 솔루션에서 제품 데이터를 업데이트하면 AEM에 실시간으로 푸시됩니까? 아니면 일괄 처리됩니까? {#faq-5}

AEM Cloud Service와 함께 사용되는 CIF 추가 기능을 사용하면 데이터가 상거래 솔루션에서 AEM 온디맨드로 흐를 수 있습니다. 상거래 솔루션에 업데이트가 있는 경우, 이는 실시간 푸시 또는 일괄 처리가 아닙니다.

## &#x200B;6. CIF가 포함된 AEM은 어떤 카탈로그 크기를 지원합니까? {#faq-6}

이는 고려해야 할 몇 가지 추가 측면에 따라 달라집니다. 카탈로그 데이터 및 페이지의 캐시 비율은 얼마입니까? 피크 시간대의 동시 요청 수는 몇 개로 예상됩니까? 상거래 솔루션의 API는 얼마나 확장 가능합니까?

## &#x200B;7. PIM은 이 프레임워크에서 어떤 역할을 합니까? {#faq-7}

PIM 데이터는 GraphQL 요청을 통해 AEM 및 클라이언트에 노출됩니다. PIM을 상거래 엔진(Adobe Commerce 등)과 통합하여 PIM 데이터를 상거래 엔진에서 검색할 수 있도록 하는 것을 권장합니다.

## &#x200B;8. Dispatcher를 통해 가격 및 기타 데이터도 캐시합니까? 캐시 무효화 문제가 자주 발생합니까? {#faq-8}

가격이나 인벤토리와 같은 동적 데이터는 Dispatcher에 캐시되지 않습니다. 동적 데이터는 GraphQL API를 통해 직접 웹 구성 요소를 사용하여 클라이언트측에서 가져옵니다. Dispatcher에는 정적 데이터(예: 제품 또는 카테고리 데이터)만 캐시됩니다. 제품 데이터가 변경되면 캐시 무효화가 필요합니다.

## &#x200B;9. AEM Dispatcher에 대한 캐시 무효화는 AEM 및 상거래에서 어떻게 작동합니까? {#faq-9}

Adobe는 Dispatcher에 캐시된 페이지에 대해 TTL 기반의 캐시 무효화를 설정할 것을 권장합니다. 가격이나 재고와 같은 동적 정보의 경우, Adobe는 클라이언트측에서 데이터를 렌더링할 것을 권장합니다. TTL 기반의 캐시 무효화에 대한 자세한 내용은 [Dispatcher 캐시 최적화](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17458.html?lang=ko)를 참조하십시오.

## &#x200B;10. Commerce가 포함된 AEM 콘텐츠 전반의 통합 검색에 대한 권장 사항이 있습니까? {#faq-10}

제품 검색 참조 구현이 제공되지만 콘텐츠가 포함된 통합 검색은 제공되지 않습니다. 이 기능은 고객별로 다르며 프로젝트별 수준에서 더 잘 해결됩니다.

## &#x200B;11. CIF를 사용하여 AEM 및 상거래에서 검색은 어떻게 작동합니까? {#faq-11}

CIF는 검색창과 검색 결과 구성 요소를 제공합니다. 검색창 구성 요소는 검색어와 함께 GraphQL 요청을 상거래 솔루션으로 보낸 다음 제품 이름, 가격, SLUG 등이 포함된 제품 목록을 반환합니다. 그런 다음 검색 결과 구성 요소는 AEM에서 생성된 검색 결과 페이지의 갤러리 보기에 검색 결과를 표시합니다. 검색은 기본 전체 텍스트 검색을 지원합니다. SLUG/URL 키를 사용하여 PDP에 대한 참조를 빌드합니다.

## &#x200B;12. MSM이나 번역에서 제품 데이터를 어떻게 사용할 수 있습니까? {#faq-12}

제품 데이터는 이미 PIM 또는 Adobe Commerce에서 번역되었습니다. AEM - Adobe Commerce 통합은 여러 Adobe Commerce 스토어 및 스토어 조회수에 대한 연결을 지원합니다. MSM 설정에서는 일반적으로 하나의 AEM 사이트가 하나의 Adobe Commerce 스토어 보기에 연결됩니다.

## &#x200B;13. 상업용 텍스트로 제품 데이터를 향상할 수 있는 방법이 있습니까? 이 작업은 어디에서 실행됩니까? AEM 또는 상거래 솔루션일까요? {#faq-13}

Adobe는 AEM에서 마케팅 관련된 데이터 및 콘텐츠를 관리할 것을 권장합니다. 콘텐츠 조각을 사용하여 추가 속성으로 상거래 솔루션의 제품 데이터를 장식하거나 구조화되지 않은 콘텐츠에 대한 경험 조각을 만들어 제품과 연결합니다.

## &#x200B;14. 전체 프레젠테이션 레이어에 AEM을 사용할 때 PCI 규정 준수를 어떻게 보장할 수 있습니까? {#faq-14}

Adobe는 추상화된 결제 방법을 사용할 것을 권장합니다. 이를 통해 브라우저 클라이언트는 결제 게이트웨이 공급자와 직접 통신할 수 있으므로 Adobe 또는 상거래 솔루션은 카드 소지자 데이터를 보유하거나 전달하지 않습니다. 이 접근 방식에는 수준 3 PCI 규정 준수만 필요합니다. 단, 직원이 시스템 및 데이터와 상호 작용하는 방식과 같이 PCI를 완전히 준수하기 위해 고려해야 할 추가 사항이 있습니다. Adobe Commerce PCI 규정 준수에 대한 자세한 내용은 [PCI 규정 준수 요구 사항](https://business.adobe.com/products/magento/pci-compliance.html)을 참조하십시오.

## &#x200B;15. AEM 및 Adobe Commerce 클라우드 버전을 사용하는 경우, 이 공동 솔루션은 PCI를 준수합니까? {#faq-15}

예, 요청 시 자체 평가 설문지 D와 규정 준수 증명서를 제공해 드립니다.

## &#x200B;16. I/O Runtime 체험판 라이선스를 요청하려면 어떻게 해야 합니까? {#faq-16}

I/O Runtime을 사용하기 위한 체험판 라이선스 요청에 대한 자세한 내용은 [액세스 권한 받기](https://developer.adobe.com/runtime/docs/guides/overview/getting_access/)를 참조하십시오.
