---
title: Adobe Experience Manager as a Cloud Service에 대한 온보딩
description: Adobe Experience Manager as a Cloud Service 온보딩 자습 리소스 및 설명서 링크
exl-id: 24cc7ad9-3556-4462-89c7-5bc1fc18218a
source-git-commit: a37b460d467e6e86394ae4baa61f044486c73b24
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 19%

---

# [!DNL Experience Manager as a Cloud Service]에 온보딩 시작 {#aem-onboarding-guide}

>[!CONTEXTUALHELP]
>id="aemcloud_onboarding_overview"
>title="온보딩 개요"
>abstract="새 응용 프로그램을 배포하거나 기존 응용 프로그램을 마이그레이션하든 관계없이 이 안내서는 응용 프로그램이 최적화되어 Cloud Service에서 성공할 수 있도록 하는 시작점 역할을 합니다. Cloud Manager에 추가된 사용자를 할당된 역할 및 관련 권한에 액세스하려면 Adobe ID 및 시스템 관리자의 도움이 필요합니다."

AEM as a Cloud Service으로 여정을 시작한 것을 축하합니다! 새 응용 프로그램을 배포하거나 기존 응용 프로그램을 마이그레이션하든 관계없이 이 안내서는 응용 프로그램이 최적화되어 Cloud Service에서 성공할 수 있도록 하는 시작점 역할을 합니다.

이 안내서는 Cloud Manager를 신속하게 시작하는 데 도움이 됩니다. Cloud Manager에 추가된 사용자를 할당된 역할(Admin Console의 제품 프로필이라고 함) 및 관련 권한에 가져오려면 Adobe ID 및 시스템 관리자의 도움이 필요합니다. 시스템 관리자가 Admin Console을 통해 이 작업을 수행하는 방법에 대한 지침은 설명되어 있습니다. Admin Console에서 제품 프로필이라고 하는 Cloud Manager 역할 목록 및 관련 권한이 자세히 설명되므로 조직의 다양한 사용자에게 필요한 역할을 결정할 수 있습니다.

다음 이미지는 시스템 관리자가 받은 환영 이메일부터 시작하여 AEM용 Cloud Manager를 Cloud Service으로 액세스하는 사용자에게 이르기까지 온보딩 여정을 보여줍니다.

![](/help/onboarding/what-is-required/assets/cust-journey.png)

## 주요 온보딩 문서 {#key-articles}

이 섹션에서는 AEM as a Cloud Service으로 시작할 때 여정에 초점을 둔 주요 문서를 다룹니다.

**온보딩 시 기대 사항**

계약이 체결되면 다음 이벤트가 발생합니다.

1. Adobe은 조직의 시스템 관리자가 사용자를 추가하고, 역할에 할당하여 Cloud Manager에 적절한 액세스 권한을 부여하는 것을 포함하여 [시스템 관리자 작업](/help/onboarding/what-is-required/add-users-assign-cm-roles.md)을 수행할 수 있는 환영 이메일을 받게 되는 조직에 대한 프로비저닝을 완료합니다.

1. 시스템 관리자가 추가한 사용자는 다시 환영 이메일을 받게 되므로 Cloud Manager로 성공적으로 이동할 수 있습니다. 이제 사용자는 Adobe ID을 사용하여 여기에서 Cloud Manager로 로그인하여 여정을 시작할 수 있습니다.

1. 시스템 관리자는 개발용으로 AEM 인스턴스에 대한 액세스 권한을 사용자에게 부여할 수 있습니다.

**Adobe ID 가져오기**

Cloud Manager에 추가된 사용자를 할당된 역할에 가져오려면 Adobe ID 및 시스템 관리자의 도움이 필요합니다.

**[Cloud Manager 역할](/help/onboarding/what-is-required/user-roles-permissions.md)**

시스템 관리자는 사용자를 추가하고 Cloud Manager 역할에 할당할 수 있습니다. 이 섹션은 시작하기 전에 *Cloud Manager 역할*&#x200B;이 역할과 역할과 연관된 권한을 이해하는 데 도움이 됩니다.

**[시스템 관리자 작업](/help/onboarding/what-is-required/add-users-assign-cm-roles.md)**

시스템 관리자는 액세스 권한부터 사용자의 모든 측면을 관리합니다. 이 사용자는 Admin Console 및 Cloud Manager 내에서 작업을 시작할 수 있는 첫 번째 액세스 권한자입니다.
다음 설명서 페이지에는 기본 조직 작업을 설명하는 정보가 포함되어 있습니다.

* 사용자 추가
* Cloud Manager 역할 및 권한에 사용자 할당

* **Cloud Manager로 이동**

사용자로 추가되고 Cloud Manager 역할에 할당되었으므로 Cloud Manager에 액세스하여 AEM에서 클라우드 여정을 시작할 수 있습니다. 사용자는 프로그램 만들기, 환경 추가, Git 액세스, [파이프라인 구성](/help/implementing/cloud-manager/configure-pipeline.md) 및 [코드 배포](/help/implementing/cloud-manager/deploy-code.md)와 같은 다양한 작업을 수행할 준비가 되었습니다.
Cloud Manager는 AEM as a Cloud Service의 중요한 부분입니다. 조직에서 자체적으로 클라우드에서 [!DNL Experience Manager]을 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다. 사용자 인터페이스를 사용하여 CI/CD 파이프라인을 구성하고 시작할 수 있습니다.

* **AEM 인스턴스에 사용자 액세스 권한 부여**

시스템 관리자 또는 환경을 만든 사용자가 다른 사용자에게 AEM 인스턴스에 대한 액세스 권한을 부여할 수 있는 방법을 알려면 이 섹션을 따르십시오.

## [!DNL Experience Manager as a Cloud Service] 안내서 {#aem-guides}

| 사용 안내서 | 설명 |
|---|---|
| [Experience Manager as a Cloud Service 홈](/help/landing/home.md) | Experience Manager as a Cloud Service 설명서에 대한 개요를 살펴보려면 여기에서 시작하십시오. |
| [개요](/help/overview/home.md) | 이 안내서에서는 [!DNL Experience Manager as a Cloud Service] 소개, 용어 등 개요를 제공합니다. |
| [릴리스 정보](/help/release-notes/home.md) | 이 안내서에서는 새로운 기능, 더 이상 사용되지 않거나 제거된 기능 및 알려진 문제 등 [!DNL Experience Manager as a Cloud Service] 의 최신 릴리스에 대한 중요 정보를 제공합니다. |
| [핵심 개념](/help/core-concepts/home.md) | 이 안내서에서는 새 서비스의 아키텍처를 포함하여 [!DNL Experience Manager as a Cloud Service]의 핵심 개념을 소개합니다. |
| [보안 사용 안내서](/help/security/home.md) | [!DNL Experience Manager as a Cloud Service]에 대한 중요한 보안 항목에 대해 알아봅니다. |
| [사이트 사용 안내서](/help/sites-cloud/home.md) | [!DNL Experience Manager Sites] 을 Cloud Service으로 작성하고 관리하는 방법을 이해합니다. |
| [자산 사용 안내서](/help/assets/home.md) | [!DNL Experience Manager Assets as a Cloud Service] 사용 및 관리 방법을 이해합니다. |
| [AEM as a Cloud Service로 이동](/help/move-to-cloud-service/home.md) | 클라우드 서비스로의 전환 여정을 이해합니다 |
| [구현 사용 안내서](/help/implementing/home.md) | 이러한 개발 및 배포 항목을 탐색하여 AEM의 강력한 기능을 사용하여 경험을 만들고 사용자 지정하는 방법을 이해합니다. |
| [헤드리스 개발자 여정](/help/journey-headless/developer/overview.md) | AEM의 강력하고 유연한 헤드리스 기능을 통해 안내식 여정을 탐색하여 첫 번째 헤드리스 프로젝트를 준비할 수 있습니다. |
| [커넥터 사용 안내서](/help/connectors/home.md) | 커넥터를 [!DNL Experience Manager as a Cloud Service]에 통합하는 방법을 알아봅니다. |
| [작업 사용 안내서](/help/operations/home.md) | 색인 지정 및 유지 관리 작업과 같은 [!DNL Experience Manager as a Cloud Service] 의 백엔드 작업에 대해 알아봅니다. |
| [상거래 사용 안내서](/help/commerce-cloud/home.md) | [!DNL Experience Manager as a Cloud Service]의 Commerce Integration Framework에 대해 알아봅니다. |

## 기타 [!DNL Experience Manager] 리소스 {#other-resources}

* [최근 설명서 업데이트](https://helpx.adobe.com/kr/experience-manager/documentation-updates.html#AEMasaCloudService)
* [디스패처 설명서](/help/implementing/dispatcher/overview.md)
* [HTL 설명서](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=ko-KR)
* [핵심 구성 요소 설명서](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR)
* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/first-time-login.html)
* [GDPR 준비 완료](/help/compliance/data-privacy-and-protection-readiness/aem-readiness.md)
* [Adobe Experience Manager as a Cloud Service 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)
* [Experience League](https://guided.adobe.com/?promoid=K42KVXHD&amp;mv=other#solutions/experience-manager)
* [AEM 커뮤니티 포럼](https://forums.adobe.com/community/experience-cloud/marketing-cloud/experience-manager)
