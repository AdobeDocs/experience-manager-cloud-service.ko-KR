---
title: AEM CIF(Commerce Integration Framework) 추가 기능으로 마이그레이션
description: 이전 버전에서 CIF(AEM Commerce Integration Framework) 추가 기능으로 마이그레이션하는 방법
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 27%

---

# Experience Manager Cloud Service 마이그레이션 안내서 {#cif-migration}

이 안내서는 Experience Manager Cloud Service 마이그레이션을 위해 업데이트해야 하는 영역을 식별하는 데 도움이 됩니다.

## CIF 추가 기능

Experience Manager as a Cloud Service의 경우 CIF 추가 기능은 Adobe Commerce 및 서드파티 상업 솔루션에 대해 유일하게 지원되는 상업 통합 솔루션입니다. Experience Manager as a Cloud Service의 고객에 대해 CIF 추가 기능이 자동으로 배포되므로 수동으로 배포하지 않아도 됩니다. [AEM Commerce as a Cloud Service 시작하기](getting-started.md)를 참조하십시오.

CIF Adobe 배포를 지원하는 경우 다음을 제공합니다. [AEM CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components).

[소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)을 통해 AEM 6.5에서도 CIF 추가 기능을 사용할 수 있습니다. 이는 Experience Manager as a Cloud Service와 호환되며 Experience Manager as a Cloud Service용 CIF 추가 기능과 동일한 기능을 제공하므로 따로 조정하지 않아도 됩니다.

클래식 CIF와 그 종속성은 더 이상 사용할 수 없습니다. 다음을 사용하여 이 CIF 버전에 의존하는 코드 `com.adobe.cq.commerce.api` Java API는 CIF 추가 기능 및 해당 원칙에 맞게 조정해야 합니다.

이전에 사용 가능한 CIF 커넥터를 더 이상 설치할 수 없습니다. 이 커넥터에 의존하는 코드는 CIF 추가 기능 및 해당 원칙에 맞게 조정해야 합니다.

## 프로젝트 구조

학습 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 그리고 AEM as a Cloud Service의 특징들. 프로젝트 설정을 AEM as a Cloud Service 레이아웃으로 조정하십시오.
AEM 6.5 배포에 비해 다음과 같은 두 가지 주요 차이점이 있습니다.

* GraphQL 클라이언트 OSGI 번들 **필수가 아니어야 합니다.** 더 이상 AEM 프로젝트에 포함되며, CIF 추가 기능을 통해 배포됩니다
* GraphQL 클라이언트 및 Graphql 데이터 서비스용 OSGI 구성 **필수가 아니어야 합니다.** 더 이상 AEM 프로젝트에 포함됨

>[!TIP]
>
>다음을 확인하십시오 [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia) GitHub에 대한 프로젝트. 이 프로젝트에서는 다른 프레임워크 조건을 고려하는 AEM as a Cloud Service 및 온-프레미스 배포에 대한 Maven 프로필을 제공합니다.

## 제품 카탈로그

제품 카탈로그 데이터 가져오기는 더 이상 지원되지 않습니다. CIF 추가 기능 주체 제품 및 카탈로그 요청을 사용하는 것은 외부 상거래 솔루션에 대한 실시간 호출을 통해 온디맨드 상태입니다. 전자 상거래 솔루션 통합에 대한 자세한 내용을 보려면 통합 장으로 이동하십시오.

>[!TIP]
>
>실시간 API를 사용할 수 없는 경우 통합에 API가 있는 외부 제품 캐시를 사용해야 합니다. 예 [Magento 오픈 소스](https://business.adobe.com/products/magento/open-source.html).

## AEM 렌더링을 사용한 제품 카탈로그 경험

클래식 CIF에서 카탈로그 블루프린트를 사용하는 경우 제품 카탈로그 워크플로우를 업데이트해야 합니다. 이제 CIF 추가 기능이 AEM 카탈로그 템플릿을 사용하여 제품 카탈로그 경험을 즉시 렌더링합니다. 더 이상 제품 데이터 또는 제품 페이지를 복제할 필요가 없습니다.

## 캐시할 수 없는 데이터 및 쇼핑 상호 작용

캐시할 수 없는 데이터 및 상호 작용(예: 장바구니에 추가, 검색)에 대한 클라이언트측 요청은 CDN/Dispatcher를 통해 상거래 종단점(상거래 솔루션 또는 통합 계층)으로 직접 이동해야 합니다. AEM이 단지 프록시였던 모든 호출을 제거합니다.
