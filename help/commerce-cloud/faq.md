---
title: AEM - Commerce Integration Framework를 사용한 Magento 통합 FAQ
description: AEM - Commerce Integration Framework를 사용한 Magento 통합 FAQ
translation-type: tm+mt
source-git-commit: cafe8825fe34f158c74b94b95b7252394de26e4d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---


# AEM - Commerce Integration Framework를 사용한 Magento 통합 FAQ


## 1. GraphQL은 Magento에만 사용됩니까 아니면 AEM에서 제작된 컨텐츠를 쿼리하는 데 사용할 수 있습니까?

Adobe은 모든 상거래 관련 데이터에 대한 공식 상거래 API로 Magento의 GraphQL API를 채택했습니다. 따라서 AEM은 GraphQL을 사용하여 Magento 및 I/O 런타임을 통해 모든 상거래 엔진과 상거래 데이터를 교환합니다.

## 2. Adobe I/O은 어떻게 작동하는가? AEM이 Magento과 직접 대화합니까?

AEM은 입출력 런타임 레이어 없이 Magento에 직접 연결할 수 있습니다. Magento이 아닌 상거래 백엔드(제3자 솔루션)를 AEM과 통합해야 하는 경우 I/O 런타임 플랫폼을 사용하여 매핑 레이어를 호스팅하여 Magento GraphQL API를 제3자 솔루션 API에 연결할 수 있습니다. 자세한 내용은 이 [참조 구현](https://github.com/adobe/commerce-cif-graphql-integration-reference)을 참조하십시오. Magento이 아닌 솔루션의 경우 AEM이 I/O 런타임 끝점을 가리키도록 구성됩니다.

I/O 런타임 플랫폼을 사용하여 커머스 서비스를 확장하거나 사용자 정의할 수도 있습니다. 이러한 사용 사례의 경우 I/O 런타임 끝점을 호출하면 해당 서비스의 사용자 지정된 구현을 호스트합니다. 통합 및 확장 사용 사례를 결합할 수 있습니다.

## 3. 제품 자산(이미지)을 Magento 관리자를 통해 AEM에서 저장 및 참조할 수 있습니까? Dynamic Media의 에셋을 어떻게 소비할 수 있습니까?

현재 AEM Assets - Magento 통합이 없습니다. 해결책은 제품 자산(이미지)을 AEM Assets에 저장할 수 있지만, 자산 URL을 Magento에 수동으로 저장해야 합니다. Dynamic Media은 이제 AEM Assets에 포함되어 있으므로 동일한 방식으로 작업할 수 있습니다.

## 4. Magento이 배포되는 곳이 중요합니까? (온프레미스 또는 클라우드에서)

Magento이 배포되는 위치와 상관없이 통합 및 새로운 AEM Venia 스토어 전선은 배포 모델에 상관없이 작동합니다. 그러나 승인된 E2E 참조 아키텍처를 기반으로 배포되는 경우 기업 고객의 프로파일을 나타내는 수집된 성능 KPI에 대해 E2E 테스트가 실행됩니다. 따라서 벤치마크로 사용할 수 있는 추가 정보가 제공됩니다.

## 5. AEM에서 만든 카탈로그 페이지 또는 제품 페이지는 어떻게 됩니까? AEM에서는 어떻게 지속됩니까?

카탈로그 페이지와 제품 페이지는 범용 카탈로그 및 제품 페이지 템플릿을 기반으로 AEM에서 동적으로 만들어지고 캐시됩니다. AEM에서 제품 또는 카탈로그 데이터를 가져와 저장하지 않습니다.

## 6. Dispatcher를 통해 가격 및 기타 데이터를 캐시합니까? 이렇게 하면 빈번한 캐시 무효화 문제가 발생합니까?

가격 또는 인벤토리와 같은 동적 데이터는 Dispatcher에 캐시되지 않습니다. 동적 데이터는 GraphQL API를 통해 웹 구성 요소를 사용하여 클라이언트측에서 가져옵니다. 정적 데이터(예: 제품 또는 카테고리 데이터)만 디스패처에 캐시됩니다. 제품 데이터가 변경되면 캐시 무효화가 필요합니다.

## 7. AEM Dispatcher의 캐시 무효화는 AEM-Magento에서 어떻게 작동합니까?

디스패처에 캐시된 페이지에 대해 TTL 기반 캐시 무효화를 설정하는 것이 좋습니다. 가격 또는 재고 등의 동적 정보에 대해서는 클라이언트측 날짜를 렌더링하는 것이 좋습니다. TTL 기반 캐시 무효화에 대한 자세한 내용은 [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html)를 참조하십시오.

## 8. We.Retail을 사용하지 않는 이유는 무엇입니까?

Magento에서 개발한 Venia 테마는 먼저 모바일이며 Magento PWA에 맞춰 정렬되어 있는 테마입니다. Venia 테마는 CSS 스타일링 및 AEM 핵심 구성 요소의 최신 용어를 나타냅니다.

## 9. Magento에서 제품 데이터를 업데이트할 때 AEM에 대한 실시간 푸시 것입니까? 아니면 일괄 처리입니까?

AEM Cloud Service에 사용되는 CIF 추가 기능을 사용하면 데이터를 Magento에서 AEM on-demand로 전달할 수 있습니다. 따라서 Magento에 업데이트가 있는 경우 실시간 푸시 또는 일괄 처리가 아닙니다.

## 10. 상거래를 통해 AEM 컨텐츠 간의 통합 검색에 대한 권장 사항이 있습니까?

제품 검색 참조 구현이 제공되지만 컨텐츠를 사용한 통합 검색은 제공되지 않습니다. 이 기능은 일반적으로 매우 고객에 맞게 특별히 제공되며 프로젝트별 수준에서 보다 잘 해결되었습니다.

## 11. CIF를 사용하여 AEM-Magento에서 검색은 어떻게 작동합니까?

CIF는 검색 막대 및 검색 결과 구성 요소를 제공합니다. 검색 막대 구성 요소는 검색어와 함께 GraphQL 요청을 Magento으로 전송합니다. 그런 다음 Magento은 제품 이름, 가격, SLUG 등이 포함된 제품 목록을 반환합니다. 그런 다음 검색 결과 구성 요소는 AEM에서 만든 검색 결과 페이지의 갤러리 보기에 검색 결과를 표시합니다. 검색은 기본적인 전체 텍스트 검색을 지원합니다. SLUG/url 키를 사용하여 PDP 참조를 만듭니다.

## 11. 제품 데이터를 MSM이나 번역에 어떻게 사용할 수 있습니까?

제품 데이터는 일반적으로 PIM 또는 Magento에서 이미 번역되었습니다. AEM - Magento 통합은 여러 Magento 스토어 및 스토어 보기에 대한 연결을 지원합니다. MSM 설정에서 일반적으로 한 AEM 사이트가 하나의 Magento 스토어 보기에 연결되어 있습니다.

## 13. CIF는 다른 상거래 플랫폼과 어떻게 작동합니까?

다른 상거래 솔루션(Magento 아님)과 같은 타사 솔루션과의 통합은 I/O 런타임 플랫폼을 통해 이루어집니다.  이 작업을 수행하는 방법을 보여주기 위해 [참조 구현](https://github.com/adobe/commerce-cif-graphql-integration-reference)을(를) 만들었습니다. 이렇게 하면 타사 상거래 플랫폼 위에 Magento GraphQL API를 노출하여 [AEM CIF 클라우드 커넥터](https://github.com/adobe/commerce-cif-connector) 및 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)를 다시 사용할 수 있습니다. 최고의 유연성과 확장성을 제공하기 위해 이 통합 레이어는 서버리스 [Adobe I/O Runtime 플랫폼](https://www.adobe.io/apis/experienceplatform/runtime.html)에 배포됩니다.

## 14. 상업용 텍스트로 제품 데이터를 향상시키는 방법이 있습니까? 이걸 어디서 하는 거야? AEM 또는 Magento에서?

이를 실현하는 방법은 여러 가지가 있으며 사용 사례에 따라 다릅니다. 한 가지 방법은 사용자 지정 속성을 사용하는 것입니다. AEM 작성자가 AEM 제품 편집기에서 이러한 필드를 변경하고 데이터를 PIM에 다시 동기화할 수 있습니다. 또 다른 옵션은 제품 페이지에 삽입되는 AEM 경험 조각을 활용하는 것입니다.

## 15. Adobe I/O Runtime 플랫폼이 사용될 때 AEM-Magento의 통합이 변경됩니까?

상거래 서비스를 확장하려는 고객은 I/O 런타임 플랫폼에 호스팅된 동일한 통합 및 작업 시퀀스를 사용하여 비즈니스 논리를 주입하고 상거래 서비스를 강화할 수 있습니다.

## 16. AEM은 AEM에서 일반 템플릿을 기반으로 제품 및 카탈로그 페이지를 동적으로 생성하므로 CRXDE Lite을 열고 컨텐츠를 확인하려고 하면 어떻게 됩니까? Magento의 제품을 기반으로 한 전체 제품 트리를 볼 수 있습니까? 그렇지 않은 경우 작성자는 해당 페이지를 어떻게 향상시킬 수 있습니까?

더 이상 JCR 카탈로그 또는 제품 페이지가 없습니다. 질문 12를 참조하십시오.

## 17. SPA은 AEM SPA 편집기와 함께 프런트 스토어를 사용할 수 있습니까?

AEM은 모든 유형의 스토어 전면을 위한 저작 도구로 사용할 수 있습니다. 현재, 하이브리드 렌더링은 새 스토어 전선에 사용됩니다. 앞으로 AEM은 SPA 및 PWA을 사용한 저작 시 사용됩니다.

## 18. PIM은 이 프레임워크에 어떻게 구현됩니까?

PIM 데이터는 GraphQL 요청을 통해 AEM 및 클라이언트에 노출됩니다. PIM을 상거래 엔진(Magento 등)과 통합하여 PIM 데이터를 상거래 엔진에서 검색할 수 있도록 하는 것이 좋습니다.

## 19. 전체 프레젠테이션 레이어에 AEM을 사용할 때 PCI 규정 준수를 어떻게 보장할 수 있습니까?

AMS 및 Magento 클라우드 배포에서 AEM을 사용하는 경우 추상화된 결제 방법을 사용해야 합니다. 이렇게 하면 브라우저 클라이언트가 결제 게이트웨이 공급자와 직접 통신하기 때문에 Adobe 또는 Magento 클라우드가 데이터를 보유하거나 카드 소유자 데이터를 전달할 수 없습니다. 이 접근 방식은 기술 스택과 데이터 센터에 대한 PCI 규정 준수를 위한 지원 범위를 제공합니다. 그러나 직원이 시스템 및 데이터와 상호 작용하는 방법 등 PCI를 완벽하게 준수하도록 고려해야 할 추가 사항이 있습니다. Magento PCI 규정 준수에 대한 자세한 내용은 https://magento.com/pci-compliance을 참조하십시오.

## 20. I/O 런타임 시험버전 라이선스를 어떻게 요청합니까?

I/O 런타임 [여기](https://github.com/AdobeDocs/adobeio-runtime/blob/master/overview/request_a_trial.md)에서 사용할 수 있도록 시험버전 라이선스를 요청할 수 있습니다.



