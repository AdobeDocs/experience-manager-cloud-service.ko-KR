---
title: 데이터 보호 및 데이터 개인정보 보호 규정 - Adobe Experience Manager as a Cloud Service 준비
description: 다양한 데이터 보호 및 데이터 개인정보 보호 규정에 대한 Adobe Experience Manager as a Cloud Service 지원 및 새로운 AEM as a Cloud Service 프로젝트를 구현할 때 준수하는 방법에 대해 알아봅니다. 이러한 규정에는 EU 일반 데이터 보호 규정(GDPR), 캘리포니아 소비자 개인정보 보호법이 포함됩니다.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: 1473c1ffccc87cb3a0033750ee26d53baf62872f
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 45%

---

# 데이터 보호 및 데이터 개인정보 보호 규정을 위한 Adobe Experience Manager as a Cloud Service 준비 {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 콘텐츠는 법률적인 조언을 포함하지 않으며, 법률적인 조언을 대체하지 않습니다.
>
>데이터 보호 및 데이터 개인정보 보호 규정에 대한 자세한 내용은 귀사의 법무 부서에 문의하십시오.

>[!NOTE]
>
>개인 정보 보호 문제에 대한 Adobe의 응답 및 Adobe 고객으로서의 이러한 응답이 의미하는 바에 대한 자세한 내용은 다음을 참조하십시오. [Adobe 개인정보 보호 센터](https://www.adobe.com/privacy.html).

Adobe 고객이 이러한 규정을 준수할 수 있도록 지원하기 위해 Adobe은 고객 개인정보 보호 관리자 및 AEM 관리자를 위한 설명서 및 절차(가능한 경우 API 포함)를 제공하고 있습니다.

* 이 설명서는 관리자가 데이터 보호 및 데이터 개인 정보 보호 요청을 처리하는 데 도움이 됩니다.
* 고객은 문서화된 절차를 통해 규정 요청을 수동으로 실행하거나 가능한 경우 외부 포털 또는 서비스에서 API를 호출할 수 있습니다.

>[!CAUTION]
>
>해당 문서에 설명된 세부 내용은 Adobe Experience Manager as a Cloud Service로 제한됩니다.
>
>다른 Adobe 온디맨드 서비스의 데이터와 관련 개인 정보 보호 요청은 해당 서비스에 대한 조치가 필요합니다.
>
>자세한 내용은 [Adobe 개인정보 보호 센터](https://www.adobe.com/privacy.html).

## 소개 {#introduction}

Adobe Experience Manager as a Cloud Service의 인스턴스 및 해당 인스턴스에서 실행되는 애플리케이션은 Adobe 고객이 소유 및 운영합니다.

따라서 GDPR, CCPA 및 기타 데이터 보호 규정에 대한 책임은 고객에게 있습니다.

간략하게 소개하면 데이터 개인정보 보호 및 보호에 대한 규정에는 다음 역할이 따라야 할 새 규칙이 포함되어 있습니다.

* 비즈니스 엔티티(CCPA) 및/또는 데이터 컨트롤러(GDPR)

* 서비스 공급자(CCPA) 및/또는 데이터 프로세서(GDPR)

이들 규정에서의 주요 프로비전은 다음과 같습니다.

1. 직접 또는 간접적으로 식별 가능한 데이터와 같이 모든 고유 ID를 포함하도록 개인 데이터의 정의 확장

2. 동의 요구 사항 강화

3. 삭제 권한(데이터 삭제)에 대한 집중 강화

4. 데이터 판매 옵트아웃

Adobe Experience Manager as a Cloud Service에 대해

* 인스턴스 및 해당 인스턴스에서 실행되는 애플리케이션은 고객이 소유 및 운영합니다.

   * 소유권은 고객이 비즈니스 엔티티, 서비스 공급자, 데이터 컨트롤러 및 데이터 프로세서를 포함한 규제 역할을 관리함을 의미합니다.

   * 아래 다이어그램에 표시된 대로 Adobe Experience Platform Privacy Service은 AEM 워크플로의 일부가 아닙니다.

* AEM에는 고객의 개인정보 보호 관리자 및/또는 AEM 관리자가 수동으로 또는 가능한 경우 API를 통해 개인정보 보호 규정 요청을 실행하도록 하는 문서 및 절차가 포함되어 있습니다.

* 새 서비스나 UI는 추가되지 않았습니다.

   * 대신 개인정보 보호 규정 요청을 처리하는 고객 UI/포털에서 사용할 수 있도록 절차 및 API가 문서화되었습니다.

* AEM에는 개인 정보 보호 요청 워크플로를 지원하는 기본 툴링이 포함되어 있지 않습니다.

   * Adobe은 고객의 개인 정보 보호 관리자, AEM 관리자 또는 두 관리자 모두를 위한 문서 및 절차를 제공하여 개인 정보 보호 규정과 관련된 요청을 수동으로 실행할 수 있도록 합니다.

Adobe은 Adobe Experience Manager as a Cloud Service에 대한 액세스, 삭제 및 옵트아웃과 관련된 개인 정보 보호 요청 처리를 위한 절차를 제공하고 있습니다. 고객 개발 포털에서 호출할 수 있는 API 또는 자동화에 도움이 되는 스크립트가 있는 경우가 있습니다.

다음 다이어그램은 개인정보 보호 요청 워크플로의 형태를 보여 줍니다(Adobe Experience Manager 6.5를 사용하여 설명함).

![데이터 보호 및 개인정보 보호](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager as a Cloud Service 및 규제 준비 {#aem-as-a-cloud-service-and-regulatory-readiness}

AEMas a Cloud Service 의 제품 영역에 대한 규제 설명서는 아래 섹션을 참조하십시오.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

[데이터 보호 및 데이터 개인정보 보호 규정을 위한 AEM Foundation 준비](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md)를 참조하십시오.

## Adobe Experience Manager as a Cloud Service Sites {#aem-sites}

[데이터 보호 및 데이터 개인정보 보호 규정을 위한 AEM Sites 준비](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md)를 참조하십시오

## Adobe Target 및 Adobe Analytics와의 Adobe Experience Manager as a Cloud Service 통합 {#aem-integration-with-adobe-target-adobe-analytics}

Adobe Experience Manager as a Cloud Service과 Adobe Target 및 Adobe Analytics의 통합은 데이터 보호 및 개인정보 보호(예: GDPR) 준비 서비스를 사용하여 구현됩니다. 해당 통합과 관련하여 어떠한 Adobe Target 또는 Adobe Analytics의 개인 데이터도 AEM에 저장되지 않습니다.
자세한 내용은 다음을 참조하십시오.

* [Adobe Target - 개인정보 보호 개요](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/cmp-privacy-and-general-data-protection-regulation.html)

* [Adobe Analytics 데이터 개인정보 보호 워크플로](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html)
