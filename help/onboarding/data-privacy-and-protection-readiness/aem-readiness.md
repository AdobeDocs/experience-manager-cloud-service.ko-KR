---
title: 데이터 보호 및 데이터 개인 정보 보호 규정 - Adobe Experience Manager as a Cloud Service 준비 완료
description: 다양한 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 지원으로서 Adobe Experience Manager에 대해 알아보십시오.에는 유럽 연합 개인 정보 보호 규정(GDPR), 캘리포니아 소비자 개인 정보 보호법 및 새 AEM을 Cloud Service 프로젝트로 구현할 때 준수하는 방법이 포함되어 있습니다.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 2%

---

# Adobe Experience Manager은 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 준비 완료 {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 컨텐츠는 법률적인 조언을 구성하지 않으며 법률적인 조언을 대체하지 않습니다.
>
>데이터 보호 및 데이터 개인 정보 보호 규정에 대한 자세한 내용은 회사의 법무 부서에 문의하십시오.

>[!NOTE]
>
>개인 정보 보호 문제에 대한 Adobe의 응답 및 Adobe 고객으로서 사용자에게 의미하는 바에 대한 자세한 내용은 [Adobe의 개인 정보 센터](https://www.adobe.com/privacy.html)를 참조하십시오.

Adobe은 고객 개인 정보 보호 관리자 또는 AEM 관리자가 데이터 보호 및 데이터 개인 정보 보호 요청을 처리하고 고객이 이러한 규정을 준수하도록 지원하는 API와 함께 문서 및 절차를 제공합니다. 정리된 절차를 통해 고객은 수동으로 또는 외부 포털 또는 서비스에서 API를 호출하여 규정 요청을 실행할 수 있습니다.

>[!CAUTION]
>
>여기에 설명된 세부 사항은 Cloud Service으로 Adobe Experience Manager으로 제한됩니다.
>
>다른 Adobe 온디맨드 서비스의 데이터와 관련 개인 정보 보호 요청은 해당 서비스에 대해 조치를 취해야 합니다.
>
>자세한 내용은 [Adobe의 개인 정보 보호 센터](https://www.adobe.com/privacy.html)를 참조하십시오.

## 소개 {#introduction}

Cloud Service로서의 Adobe Experience Manager 인스턴스와 이러한 인스턴스에서 실행되는 애플리케이션은 고객이 소유하고 관리합니다.

따라서 GDPR, CCPA 등과 같은 데이터 보호 규정은 고객의 책임입니다.

매우 간략하게 소개되는 데이터 개인 정보 보호 및 보호에 대한 규정에는 다음과 같은 역할이 따라야 하는 새로운 규칙이 포함됩니다.

* CCPA(Business Entity) 및/또는 GDPR(데이터 통제자)

* CCPA(서비스 공급자) 및/또는 GDPR(데이터 프로세서)

이러한 규정의 주요 내용은 다음과 같습니다.

1. 모든 고유 ID를 포함하도록 개인 데이터의 확장된 정의를 직접 및 간접적으로 식별 가능한 데이터에서 사용할 수 있습니다.

2. 강화된 동의 요구 사항.

3. 삭제 권한 (데이터 삭제)에 중점을 둡니다.

4. 데이터 판매 거부.

Adobe Experience Manager as a Cloud Service의 경우:

* 인스턴스 및 이 인스턴스에서 실행되는 응용 프로그램은 고객이 소유하여 운영하고 있습니다.

   * 이는 고객이 비즈니스 엔터티 및 서비스 공급자, 데이터 컨트롤러, 데이터 프로세서 등 규정 역할을 관리함을 효과적으로 의미합니다.

   * 아래 다이어그램에 나와 있는 대로 Adobe Experience Platform Privacy Service은 AEM용 워크플로우의 일부가 아닙니다.

* AEM에는 고객의 개인 정보 보호 관리자 및/또는 AEM 관리자가 개인 정보 보호 규정 요청을 실행하기 위한 설명서 및 절차가 포함되어 있습니다.수동으로 또는 API를 통해 가능한 경우 선택할 수 있습니다.

* 새 서비스 또는 UI가 추가되지 않았습니다.

   * 대신 개인 정보 보호 규정 요청을 처리하는 고객 UI/포털에서 사용하기 위해 절차 및 API를 문서화합니다.

* AEM에는 개인 정보 요청 워크플로우를 지원하는 기본 도구 모음이 포함되지 않습니다.

   * Adobe은 고객의 개인 정보 보호 관리자 및/또는 AEM 관리자에 대한 설명서 및 절차를 제공하며, 이 절차를 통해 개인 정보 보호 규정과 관련된 요청을 수동으로 실행할 수 있습니다.

Adobe은 Cloud Service으로 Adobe Experience Manager에 대한 액세스, 삭제 및 옵트아웃과 관련된 개인 정보 보호 요청을 처리하는 절차를 제공하고 있습니다. 경우에 따라 고객이 개발한 포털이나 스크립트에서 자동화를 지원하기 위해 호출할 수 있는 API가 있습니다.

다음 다이어그램은 개인 정보 보호 요청 워크플로우의 모양을 보여줍니다(Adobe Experience Manager 6.5 사용 그림).

![데이터 보호 및 개인 정보](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager을 Cloud Service 및 규제 준비 완료 {#aem-as-a-cloud-service-and-regulatory-readiness}

AEM as a Cloud Service의 제품 영역에 대한 규정 설명서는 아래 섹션을 참조하십시오.

## Adobe Experience Manager as a Cloud Service 기반 {#aem-foundation}

[데이터 보호 및 데이터 개인 정보 보호 규정에 대한 AEM 기초 준비 완료](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md)를 참조하십시오.

## Adobe Experience Manager as a Cloud Service 사이트 {#aem-sites}

[데이터 보호 및 데이터 개인 정보 보호 규정에 대한 AEM Sites 준비 완료 를 참조하십시오.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager as a Adobe Target &amp; Adobe Analytics과 Cloud Service 통합 {#aem-integration-with-adobe-target-adobe-analytics}

이러한 Adobe Experience Manager as a Cloud Service 통합은 데이터 보호 및 개인 정보 보호(예: GDPR) 지원 서비스와 통합됩니다. Adobe Target 또는 Adobe Analytics의 개인 데이터는 통합과 관련하여 AEM에 저장되지 않습니다.
자세한 내용은 다음을 참조하십시오.

* [Adobe Target - 개인 정보 보호 개요](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/privacy.html)

* [Adobe Analytics 데이터 개인 정보 보호 워크플로우](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html)
