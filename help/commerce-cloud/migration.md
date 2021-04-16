---
title: AEM CIF(Commerce Integration Framework) Add-on으로의 마이그레이션
description: 이전 버전에서 AEM CIF(Commerce Integration Framework) Add-On으로 마이그레이션하는 방법
translation-type: tm+mt
source-git-commit: cda25048e171f6aacd5349706ad4192965e703db
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 4%

---

# Experience Manager Cloud Service {#cif-migration} 마이그레이션 안내서

이 가이드는 Experience Manager Cloud Service 마이그레이션을 위해 업데이트해야 하는 영역을 식별하는 데 도움이 됩니다.

## CIF 추가 기능

Cloud Service의 경우 CIF Add-On은 Adobe Commerce 및 제3자 상거래 솔루션을 위해 유일하게 지원되는 상거래 통합 솔루션입니다. CIF Add-On은 Cloud Service을 사용하는 고객을 위해 자동으로 배포되므로 수동으로 배포할 필요가 없습니다. [Cloud Service](getting-started.md)으로 AEM Commerce 시작을 참조하십시오.

CIF Adobe 배포 프로젝트를 지원하려면 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)를 제공합니다.

CIF Add-on은 AEM 6.5뿐만 아니라 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)을 통해 사용할 수 있습니다. 호환 가능하고 Cloud Service용 CIF 추가 기능과 동일한 기능을 제공하므로 조정이 필요 없습니다.

종속성이 있는 클래식 CIF는 더 이상 사용할 수 없습니다. `com.adobe.cq.commerce.api` Java API를 사용하는 이 CIF 버전에 의존하는 코드는 CIF Add-on 및 해당 원칙에 따라 조정되어야 합니다.

이전에 사용할 수 있었던 CIF 커넥터를 더 이상 설치할 수 없습니다. 이 커넥터에 의존하는 코드는 CIF 추가 기능 및 해당 원칙에 맞게 조정해야 합니다.

## 프로젝트 구조

[AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 및 Cloud Service의 특성에 대해 알아봅니다. 프로젝트 설정을 Cloud Service 레이아웃으로 AEM에 맞게 조정할 수 있습니다.
AEM 6.5 배포와 비교할 때 다음과 같은 두 가지 주요 차이점이 있습니다.

* GraphQL 클라이언트 OSGI 번들 **은(는) 더 이상 AEM 프로젝트에 포함되지 않아야 하며 CIF Add-on을 통해 배포됩니다.**
* GraphQL 클라이언트 및 Graphql 데이터 서비스 **에 대한 OSGI 구성은 더 이상 AEM 프로젝트에 포함되지 않아야 합니다.**

>[!TIP]
>
>GitHub에서 [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) 프로젝트를 확인하십시오. 이 프로젝트는 서로 다른 프레임워크 조건을 고려하여 Cloud Service 및 온-프레미스 배포로 AEM용 Maven 프로필을 제공합니다.

## 제품 카탈로그

제품 카탈로그 데이터 가져오기는 더 이상 지원되지 않습니다. CIF Add-on 주도자의 제품 및 카탈로그 요청은 외부 상거래 솔루션에 대한 실시간 호출을 통해 On-Demand 방식으로 이루어집니다. 상거래 솔루션 통합에 대한 자세한 내용은 통합으로 이동합니다.

>[!TIP]
>
>실시간 API를 사용할 수 없는 경우 API가 포함된 외부 제품 캐시를 통합에 사용해야 합니다. 예 [Magento open-source](https://magento.com/products/magento-open-source).

## AEM 렌더링을 통한 제품 카탈로그 경험

Classic CIF에서 카탈로그 블루프린트를 사용하는 경우 제품 카탈로그 워크플로우를 업데이트해야 합니다. 이제 CIF Add-on은 AEM 카탈로그 템플릿을 사용하여 제품 카탈로그 경험을 신속하게 렌더링합니다. 더 이상 제품 데이터 또는 제품 페이지를 복제할 필요가 없습니다.

## 액세스 불가능한 데이터 및 쇼핑 상호 작용

액세스 불가능한 데이터 및 상호 작용(예: 장바구니에 추가, 검색)에 대한 클라이언트측 요청은 CDN/Dispatcher를 통해 상거래 끝점(상거래 솔루션 또는 통합 레이어)으로 바로 이동해야 합니다. AEM이 프록시였던 모든 호출을 제거합니다.
