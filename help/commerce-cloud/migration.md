---
title: CIF(AEM Commerce integration framework) 추가 기능으로 마이그레이션
description: 이전 버전에서 AEM Commerce integration framework(CIF) 추가 기능으로 마이그레이션하는 방법
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 20%

---

# Experience Manager Cloud Service에 대한 마이그레이션 안내서 {#cif-migration}

이 안내서는 Experience Manager Cloud Service 마이그레이션을 위해 업데이트해야 하는 영역을 식별하는 데 도움이 됩니다.

## CIF 추가 기능

Experience Manageras a Cloud Service 의 경우 CIF 추가 기능은 Adobe Commerce 및 서드파티 상거래 솔루션에서만 지원됩니다. Experience Manager as a Cloud Service의 고객에 대해 CIF 추가 기능이 자동으로 배포되므로 수동으로 배포하지 않아도 됩니다. [AEM Commerce as a Cloud Service 시작하기](getting-started.md)를 참조하십시오.

CIF AdobeAEM 를 배포하는 프로젝트를 지원하려면 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)를 제공하십시오.

[소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)을 통해 AEM 6.5에서도 CIF 추가 기능을 사용할 수 있습니다. 이는 Experience Manager as a Cloud Service와 호환되며 Experience Manager as a Cloud Service용 CIF 추가 기능과 동일한 기능을 제공하므로 따로 조정하지 않아도 됩니다.

클래식 CIF와 그 종속성은 더 이상 사용할 수 없습니다. `com.adobe.cq.commerce.api`개의 Java API를 사용하는 이 CIF 버전에 의존하는 코드는 CIF 추가 기능 및 그 원칙에 맞게 조정해야 합니다.

이전에 사용 가능했던 CIF 커넥터는 더 이상 설치할 수 없습니다. 이 커넥터에 의존하는 코드는 CIF 추가 기능 및 그 원칙에 맞게 조정해야 합니다.

## 프로젝트 구조

[AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 및 AEM as a Cloud Service의 특성에 대해 알아봅니다. 프로젝트 설정을 AEM as a Cloud Service 레이아웃으로 조정합니다.
AEM 6.5 배포와 비교하여 두 가지 주요 차이점이 있습니다.

* GraphQL 클라이언트 OSGI 번들 **은(는) 더 이상 AEM 프로젝트에 포함되지 않아야**, CIF 추가 기능을 통해 배포됩니다.
* GraphQL 클라이언트 및 Graphql 데이터 서비스 **용 OSGI 구성은 더 이상 AEM 프로젝트에 포함되지 않아야** 합니다

>[!TIP]
>
>GitHub에서 [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia) 프로젝트를 확인하십시오. 이 프로젝트는 다양한 프레임워크 조건을 고려한 AEM as a Cloud Service 및 온프레미스 배포용 Maven 프로필을 제공합니다.

## 제품 카탈로그

제품 카탈로그 데이터 가져오기는 더 이상 지원되지 않습니다. CIF 추가 기능 주도자 제품 및 카탈로그 요청은 외부 상거래 솔루션에 대한 실시간 호출을 통해 온디맨드로 수행됩니다. 상거래 솔루션 통합에 대한 자세한 내용을 보려면 통합 장으로 이동합니다.

>[!TIP]
>
>사용 가능한 실시간 API가 없는 경우 API가 있는 외부 제품 캐시를 사용하여 통합해야 합니다. 예제 [Magento 오픈 소스](https://business.adobe.com/products/magento/open-source.html).

## AEM 렌더링을 통한 제품 카탈로그 경험

클래식 CIF과 함께 카탈로그 블루프린트를 사용하는 경우 제품 카탈로그 워크플로우를 업데이트해야 합니다. 이제 CIF 추가 기능은 AEM 카탈로그 템플릿을 사용하여 제품 카탈로그 경험을 즉시 렌더링합니다. 더 이상 제품 데이터 또는 제품 페이지 복제가 필요하지 않습니다.

## 캐시 불가능 데이터 및 쇼핑 상호 작용

캐시할 수 없는 데이터 및 상호 작용(예: 장바구니에 추가, 검색)에 대한 클라이언트측 요청은 CDN/Dispatcher을 통해 상거래 끝점(상거래 솔루션 또는 통합 계층)으로 직접 이동해야 합니다. AEM이 프록시였던 모든 호출을 제거합니다.
