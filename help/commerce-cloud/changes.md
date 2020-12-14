---
title: Cloud Service으로 AEM Commerce에 대한 주목할 만한 변경 사항
description: Adobe Experience Manager 6.5와 비교하여 AEM Commerce가 Cloud Service으로 눈에 띄게 변경되었습니다.
translation-type: tm+mt
source-git-commit: 2934d0d8d3977bb7884bae9654ac26e9fa57b34f
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 5%

---


# Cloud Service {#notable-changes}으로 AEM Commerce에 대한 주목할 만한 변경 사항

Adobe Experience Manager은 Cloud Service으로 AEM 프로젝트를 관리할 수 있는 새로운 기능과 다양한 기능을 제공합니다. 이 문서에서는 온-프레미스, Adobe 관리 서비스 및 Cloud Service에 대한 CIF(Commerce Integration Framework) 간의 상거래 기능에 대한 중요한 차이점을 강조 표시합니다. 다른 변경 사항은 Experience Manager에 대한 일반 [변경 사항을 Cloud Service](/help/release-notes/aem-cloud-changes.md)으로 참조하십시오.

Experience Manager 6.5와 비교할 때 주요 차이점은 다음과 같습니다.
* [CIF Classic 지원](#cif-classic)
* [CIF 작성 도구 배포](#cif-tools)
* [온-프레미스 및 Adobe 관리 서비스에서 이동](#moving-cif-cs)

## Cloud Service {#cif-classic}(으)로 Experience Manager에서 CIF Classic/Quickstart 지원

제품 카탈로그를 Experience Manager에 가져오고 저장하기 위한 제품 가져오기가 포함된 Classic Commerce Integration Framework는 Experience Manager에서 더 이상 Cloud Service으로 사용할 수 없습니다. Classic CIF의 사용은 Cloud Service에서 지원되지 않으며, Classic CIF를 사용하는 프로젝트는 Classic CIF 구현을 Cloud Service의 [CIF에 설명된 대로 지원되는 버전으로 대체해야 합니다](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/commerce/architecture/magento.html#overview)

## CIF {#deployment} 배포

아래에는 다양한 AEM 제품에 대한 상거래 통합 프레임워크에 대한 다양한 배포 모델이 표시됩니다.

|  | AEM 온프레미스 | AEM Managed Services | AEM Cloud Service |
|-------------     |-----------|-----------|-----------|
| Magento 백엔드를 위한 CIF 작성 도구를 배포하는 방법 | [AEM 6.5](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) 에서 지원되는 CIF Connectors를 참조하십시오. | [AEM 6.5](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) 에서 지원되는 CIF Connectors를 참조하십시오. | AEM을 Cloud Service으로 프로비저닝해야 CEF Add-On을 사용할 수 있습니다. 자세한 내용은 영업 담당자에게 문의 |
| [CIF Venia Project를 배포하는 방법](https://github.com/adobe/aem-cif-guides-venia) | AEM 패키지 설치 | 배포 완료: [클라우드 관리자](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | 프로젝트가 [클라우드 관리자 Git 리포지토리](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html)로 이동되었고 [클라우드 관리자](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/deploying/overview.html)를 통해 배포되었습니다. |

>[!NOTE]
>
>AEM Managed Service 또는 AEM 온프레미스에서 CIF를 사용하는 방법에 대한 추가 문서는 [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)를 참조하십시오.

>[!NOTE]
>
>CIF Classic/Quickstart 버전의 Commerce Integration Framework는 AEM 온프레미스 오퍼링에서 매우 제한된 사용 사례에 대해 사용할 수 있습니다. 그러나 이는 권장되지 않는 솔루션입니다.

## 온-프레미스 및 Managed Services {#moving-cif-cs}에서 Cloud Service으로 AEM Commerce로 이동

Cloud Service으로 AEM 온프레미스 또는 Managed Services 설치에서 AEM으로 전환하는 고객은 AEM 프로젝트에서 몇 가지 사소한 조정을 해야 합니다.

위에서 설명한 대로 CIF Connector에 첫 번째 조정이 필요합니다. CIF 커넥터는 Adobe에 의해 배포된 CIF 추가 기능으로 대체됩니다. 따라서 AEM에 CIF 커넥터를 Cloud Service으로 설치하지 마십시오. 또한 로컬 AEM Cloud SDK와 함께 사용하는 것은 지원되지 않으며 Adobe은 [로컬 개발](develop.md)에도 CIF 추가 기능을 제공합니다.

둘째, [AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)와 AEM의 Cloud Service 특성을 파악합니다. 프로젝트 설정을 Cloud Service 레이아웃으로 AEM에 맞게 조정할 수 있습니다.
여기에서 주요 차이점은 다음과 같습니다.

* GraphQL 클라이언트 OSGI 번들 **은(는) 더 이상 AEM 프로젝트에 포함되지 않아야 하며 CIF Add-on을 통해 배포됩니다.**
* GraphQL 클라이언트 및 Graphql 데이터 서비스 **에 대한 OSGI 구성은 더 이상 AEM 프로젝트에 포함되지 않아야 합니다.**

>[!TIP]
>
>GitHub에서 [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) 프로젝트를 확인하십시오. 이 프로젝트는 서로 다른 프레임워크 조건을 고려하여 Cloud Service 및 온-프레미스 배포로 AEM용 Maven 프로필을 제공합니다.
