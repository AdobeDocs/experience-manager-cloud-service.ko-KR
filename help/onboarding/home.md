---
title: Adobe Experience Manager as a Cloud Service에 대한 온보딩
description: Adobe Experience Manager as a Cloud Service 온보딩 자습 리소스 및 설명서 링크
translation-type: tm+mt
source-git-commit: 2779b20f3b4c13ef604fa2ad61f17c836e228422
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 39%

---


# Experience Manager as a Cloud Service에 온보딩{#aem-onboarding-guide}

Cloud Service으로 AEM을 사용해 주셔서 감사합니다! 새 응용 프로그램을 배포하거나 기존 응용 프로그램을 마이그레이션하는 것과 상관없이 이 안내서는 응용 프로그램이 Cloud Service에 맞게 최적화되어 성공을 이룰 수 있도록 도와주는 시작 지점 역할을 합니다.

이 가이드는 사용자와 팀이 Cloud Manager를 신속하게 시작할 수 있는 체크리스트를 제공합니다. Cloud Manager에 사용자가 할당된 역할(Admin Console의 제품 프로필이라고 함) 및 관련 권한에 추가하도록 하려면 Adobe ID 및 시스템 관리자의 도움이 필요합니다. 시스템 관리자가 Admin Console을 통해 이 작업을 수행하는 방법에 대한 지침은 [여기](/help/onboarding/what-is-required/add-users-assign-cm-roles.md)에 설명되어 있습니다. Admin Console에서 제품 프로필이라고 하는 클라우드 관리자 역할 목록과 관련 권한은 조직의 다양한 사용자에게 어떤 역할이 필요한지 결정할 수 있도록 자세히 설명되어 있습니다.

다음 이미지는 온보딩 여정을 보여주고, 시스템 관리자가 받은 환영 이메일을 시작으로 AEM용 Cloud Manager를 Cloud Service으로 액세스하는 사용자에게 그 절정에 이릅니다.

![](/help/onboarding/what-is-required/assets/cust-journey.png)

## 주요 온보딩 문서 {#key-articles}

이 섹션에서는 Cloud Service으로 AEM을 시작할 때 여정에 초점을 맞춘 주요 아티클을 다룹니다.

**온보딩 작업 시 예상되는 사항**

계약이 체결되면 다음 이벤트가 발생합니다.

1. Adobe은 조직의 시스템 관리자가 환영 이메일을 받을 조직에 대한 프로비저닝을 완료하여 [관리자 작업](/help/onboarding/what-is-required/add-users-assign-cm-roles.md)에 사용자 추가, 역할에 할당 및 적절한 [Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md)에 대한 액세스 권한을 부여합니다.

1. 그러면 시스템 관리자가 추가한 사용자가 클라우드 관리자](/help/onboarding/what-is-required/navigate-to-cloud-manager.md)에 대한 액세스 권한이 있음을 알리는 환영 이메일을 받게 됩니다. [ 이제 사용자는 자신의 [Adobe ID](/help/onboarding/what-is-required/get-your-adobe-id.md)을(를) 사용하여 로그인하고 여기에서 Cloud Manager로 여정을 시작할 수 있습니다.


1. 개발용으로 AEM 인스턴스](/help/onboarding/what-is-required/accessing-aem-instance.md)에 대한 액세스 권한을 추가로 사용자에게 부여할 수 있습니다.[

**[사용자 역할 및 권한](/help/onboarding/what-is-required/user-roles-permissions.md)**

시스템 관리자는 사용자를 추가하고 Cloud Manager 역할에 할당할 수 있습니다. 이 섹션에서는 시작하기 전에 *클라우드 관리자 역할*&#x200B;이(가) 역할과 연관된 권한을 이해하는 데 도움이 됩니다.

**[시스템 관리자 작업](/help/onboarding/what-is-required/add-users-assign-cm-roles.md)**

시스템 관리자는 액세스 권한에서부터 사용 권한에 이르기까지 사용자의 모든 측면을 관리합니다. 이 사용자는 Admin Console 및 Cloud Manager 내에서 작업을 시작할 수 있는 첫 번째 액세스 권한이 있습니다.
다음 설명서 페이지에는 기본적인 조직 작업을 설명하는 정보가 포함되어 있습니다.

* 사용자 추가
* Cloud Manager 역할 및 권한에 사용자 할당

**[클라우드 관리자로 이동](/help/onboarding/what-is-required/navigate-to-cloud-manager.md)**

사용자로 추가되고 Cloud Manager 역할에 할당되었으므로 Cloud Manager에 액세스하여 AEM에서 클라우드 여정을 시작할 수 있습니다. 사용자는 [프로그램 만들기](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md), [환경](/help/implementing/cloud-manager/manage-environments.md) 추가, [Git](/help/implementing/cloud-manager/accessing-git.md) 액세스, [파이프라인 구성](/help/implementing/cloud-manager/configure-pipeline.md) 및 [코드](/help/implementing/cloud-manager/deploy-code.md) 배포와 같은 다양한 작업을 수행할 준비가 되었습니다.
Cloud Manager는 Cloud Service에서 AEM의 중요한 부분입니다. 이를 통해 조직은 클라우드에서 Experience Manager을 직접 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다. 사용자 인터페이스를 사용하여 CI/CD 파이프라인을 구성하고 시작할 수 있습니다.

**[AEM 인스턴스에 대한 사용자 액세스 권한 부여](/help/onboarding/what-is-required/accessing-aem-instance.md)**

시스템 관리자 또는 환경을 만든 사용자가 AEM 인스턴스에 대한 액세스 권한을 다른 사용자에게 부여할 수 있는 방법을 알아보려면 이 섹션을 따르십시오.

## Experience Manager as a Cloud Service 안내서 {#aem-guides}

| 사용 안내서 | 설명 |
|---|---|
| [Experience Manager as a Cloud Service 홈](/help/landing/home.md) | Experience Manager as a Cloud Service 설명서에 대한 개요를 살펴보려면 여기에서 시작하십시오. |
| [개요](/help/overview/home.md) | 이 안내서에서는 Experience Manager as a Cloud Service 소개, 용어 등 개요를 제공합니다. |
| [릴리스 정보](/help/release-notes/home.md) | 이 안내서에서는 새로운 기능, 더 이상 사용되지 않거나 제거된 기능 및 알려진 문제 등 Experience Manager as a Cloud Service의 최신 릴리스에 대한 중요 정보를 제공합니다. |
| [핵심 개념](/help/core-concepts/home.md) | 이 안내서에서는 이 새로운 서비스의 아키텍처를 포함하여 Experience Manager as a Cloud Service의 핵심 개념을 소개합니다. |
| [보안 사용 안내서](/help/security/home.md) | Experience Manager as a Cloud Service에 대한 중요 보안 항목에 대해 알아봅니다. |
| [사이트 사용 안내서](/help/sites-cloud/home.md) | Experience Manager Sites as a Cloud Service를 제작 및 관리하는 방법을 이해합니다. |
| [자산 사용 안내서](/help/assets/home.md) | Experience Manager Assets as a Cloud Service를 사용 및 관리하는 방법을 이해합니다. |
| [AEM as a Cloud Service로 이동](/help/move-to-cloud-service/home.md) | 클라우드 서비스로의 전환 여정을 이해합니다 |
| [구현 사용 안내서](/help/implementing/home.md) | 개발 및 배포 항목을 비롯한 Experience Manager as a Cloud Service 배포를 사용자 지정하는 방법에 대해 알아봅니다. |
| [커넥터 사용 안내서](/help/connectors/home.md) | Experience Manager as a Cloud Service에 커넥터를 통합하는 방법을 알아봅니다. |
| [작업 사용 안내서](/help/operations/home.md) | 색인 지정 및 유지 관리 작업과 같은 Experience Manager as a Cloud Service가 수행하는 백엔드 작업에 대해 알아봅니다. |
| [상거래 사용 안내서](/help/commerce-cloud/home.md) | Cloud Service으로 AEM 기반의 Commerce Integration Framework에 대해 알아봅니다. |

## 기타 Experience Manager 리소스 {#other-resources}

* [최근 설명서 업데이트](https://helpx.adobe.com/kr/experience-manager/documentation-updates.html#AEMasaCloudService)
* [디스패처 설명서](/help/implementing/dispatcher/overview.md)
* [HTL 설명서](https://docs.adobe.com/content/help/ko-KR/experience-manager-htl/using/overview.html)
* [핵심 구성 요소 설명서](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html)
* [Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/first-time-login.html)
* [GDPR 준비 완료](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md)
* [Adobe Experience Manager as a Cloud Service 자습서](https://docs.adobe.com/content/help/ko-KR/experience-manager-learn/cloud-service/overview.html)
* [Experience League](https://guided.adobe.com/?promoid=K42KVXHD&amp;mv=other#solutions/experience-manager)
* [AEM 커뮤니티 포럼](https://forums.adobe.com/community/experience-cloud/marketing-cloud/experience-manager)