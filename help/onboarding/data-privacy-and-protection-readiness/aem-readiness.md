---
title: 데이터 보호 및 데이터 개인 정보 보호 규정 - 클라우드 서비스 준비로서의 Adobe Experience Manager
description: '다양한 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 클라우드 서비스 지원으로서 Adobe Experience Manager에 대해 알아봅니다.여기에는 EU GDPR(General Data Protection Regulation), California Consumer Privacy Act 및 새로운 AEM을 클라우드 서비스 프로젝트로 구현할 때 준수하는 방법이 포함됩니다. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247

---


# Adobe Experience Manager, 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 클라우드 서비스 준비 {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 내용은 법률적 조언을 구성하지 않으며 법적 자문을 대체하기 위한 것이 아닙니다.
>
>데이터 보호 및 데이터 개인 정보 보호 규정에 대한 자세한 내용은 회사의 법무팀에 문의하십시오.

>[!NOTE]
>
>개인정보 보호 문제에 대한 Adobe의 응답 및 Adobe 고객으로서 귀하에게 의미하는 사항에 대한 자세한 내용은 Adobe [의 개인정보 보호 센터를 참조하십시오](https://www.adobe.com/privacy.html).

Adobe는 고객 개인 정보 관리자 또는 AEM 관리자가 데이터 보호 및 데이터 개인 정보 보호 요청을 처리하고 고객이 이러한 규정을 준수할 수 있도록 지원하기 위해 설명서 및 절차(사용 가능한 경우 API 포함)를 제공합니다. 문서화된 절차를 통해 고객은 수동으로 또는 외부 포털 또는 서비스에서 API로 전화하여 규정 요청을 실행할 수 있습니다.

>[!CAUTION]
>
>여기에 설명된 세부 사항은 클라우드 서비스로서 Adobe Experience Manager로 제한됩니다.
>
>다른 Adobe On-Demand Service의 데이터와 관련 개인 정보 보호 요청은 해당 서비스에 대한 조치를 필요로 합니다.
>
>자세한 내용은 [Adobe의 개인 정보 보호 센터를 참조하십시오](https://www.adobe.com/privacy.html).

## 소개 {#introduction}

Adobe Experience Manager를 클라우드 서비스로 사용하는 인스턴스와 이러한 인스턴스에서 실행되는 애플리케이션은 Adobe 고객이 소유하고 관리합니다.

그 결과 GDPR, CCPA 및 기타 업체와 같은 데이터 보호 규정은 고객의 책임입니다.

간단한 소개로, 데이터 개인 정보 보호 및 보호에 대한 규정에는 다음의 역할이 따라야 하는 새로운 규칙이 포함됩니다.

* CCPA(Business Entity) 및/또는 GDPR(Data Controller)

* CCPA(Service Providers) 및/또는 GDPR(Data Processor)

이러한 규정의 주요 내용은 다음과 같습니다.

1. 모든 고유 ID를 포함하도록 개인 데이터의 확장된 정의를 사용할 수 있습니다.

2. 동의 요건 강화

3. 삭제 권한에 대한 집중(데이터 삭제)

4. 데이터 판매 거부.

클라우드 서비스로 Adobe Experience Manager 사용:

* 인스턴스와 애플리케이션에서 실행되는 애플리케이션은 고객이 소유하거나 관리합니다.

   * 따라서 고객은 비즈니스 기업 및 서비스 제공업체, 데이터 컨트롤러, 데이터 프로세서 등 규정 역할을 효율적으로 관리할 수 있습니다.

   * 아래 다이어그램에 나와 있는 바와 같이 Adobe Experience Platform 개인 정보 보호 서비스는 AEM에 대한 워크플로우의 일부가 아닙니다.

* AEM에는 고객의 개인 정보 관리자 및/또는 AEM 관리자가 개인 정보 보호 규정 요청을 실행하기 위한 설명서 및 절차가 포함되어 있습니다.수동으로 또는 API를 통해(가능한 경우)

* 새 서비스 또는 UI가 추가되지 않았습니다.

   * 대신 개인 정보 보호 규정 요청을 처리하는 고객 UI/포털에서 사용하기 위해 절차 및 API를 문서화합니다.

* AEM에는 개인 정보 요청 워크플로우를 지원하기 위한 기본 도구가 포함되어 있지 않습니다.

   * Adobe는 고객의 개인 정보 관리자 및/또는 AEM 관리자에 대한 문서 및 절차를 제공하여 고객이 개인 정보 보호 규정과 관련된 요청을 수동으로 실행할 수 있도록 합니다.

Adobe는 Adobe Experience Manager에 대한 액세스, 삭제 및 옵트아웃 관련 개인 정보 요청을 클라우드 서비스로 처리하는 절차를 제공하고 있습니다. 경우에 따라 고객이 개발한 포털이나 스크립트에서 자동화를 지원하는 API를 호출할 수 있습니다.

다음 다이어그램은 개인 정보 요청 워크플로우의 모양을 보여줍니다(Adobe Experience Manager 6.5를 사용하여 표시됨).

![데이터 보호 및 개인 정보 보호](assets/data-protection-and-privacy-01.png)

## 클라우드 서비스로서의 Adobe Experience Manager 및 규정 준수 {#aem-as-a-cloud-service-and-regulatory-readiness}

클라우드 서비스로 AEM의 제품 영역에 대한 규정 문서는 아래 섹션을 참조하십시오.

## 클라우드 서비스 기반인 Adobe Experience Manager {#aem-foundation}

AEM [Foundation 데이터 보호 및 데이터 개인 정보 보호 규정을 참조하십시오](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## 클라우드 서비스 사이트로서의 Adobe Experience Manager {#aem-sites}

AEM [Sites 데이터 보호 및 데이터 개인 정보 보호 규정을 참조하십시오.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Target 및 Adobe Analytics와 클라우드 서비스 통합으로 Adobe Experience Manager 통합 {#aem-integration-with-adobe-target-adobe-analytics}

Adobe Experience Manager는 클라우드 서비스 통합으로, 데이터 보호 및 개인 정보 보호(예: GDPR)를 위한 서비스와 통합됩니다. 통합과 관련하여 Adobe Target 또는 Adobe Analytics의 개인 데이터는 AEM에 저장되지 않습니다.
자세한 내용은 다음을 참조하십시오.

* [Adobe Target - 개인 정보 개요](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics 데이터 개인 정보 보호 워크플로우](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
