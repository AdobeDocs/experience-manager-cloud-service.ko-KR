---
title: 온보딩 여정
description: 온보딩 여정을 시작하는 방법을 알려면 이 페이지를 따르십시오
hide: true
index: false
source-git-commit: 4ef8c167e24a18af578d58c21fd1079a080f71d1
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 2%

---

# 온보딩 여정 {#onboarding-jourrney}

AEM as a Cloud Service으로 여정을 시작한 것을 축하합니다! 여기셔서 매우 기쁘게 생각하며 온보딩 여정을 시작할 때까지 기다릴 수 없습니다. 새 응용 프로그램을 배포하거나 기존 응용 프로그램을 마이그레이션하는 경우 이 안내서는 팀이 설정되고 AEM as a Cloud Service에 액세스할 수 있도록 하는 시작점 역할을 합니다.

## 소개 {#introduction}

이 안내서에서는 가장 중요한 주제를 안내하여 완료되면 다음과 같은 내용을 볼 수 있습니다.

* AEM as a Cloud Service 온보딩 여정 동안 예상되는 사항에 대한 전체 이해
* 팀을 활성화하여 실행 중이며 AEM용 컨텐츠를 Cloud Service 애플리케이션으로서 작성 및 개발하는 방법을 학습하는 첫 번째 단계를 수행할 수 있습니다.

이것의 의미는 다음과 같습니다.

* 팀이 설정되고 클라우드 리소스에 대한 액세스 권한이 있습니다.
* AEM 작성자는 AEM as a Cloud Service에 액세스할 수 있습니다.
* AEM 개발자 및 배포 관리자는 AEM as a Cloud Service에 액세스할 수 있습니다.


## 속성을 확인하는 {#audience}

온보딩은 지정된 [시스템 관리자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=en)가 AEM을 조직의 Cloud Service으로 설정하는 프로세스입니다. 여기에는 각 구성원이 Cloud Service 리소스로 AEM에 로그인하고 액세스할 수 있는 작업 권한에 따라 적절한 역할에 클라우드 리소스의 초기 프로비저닝 및 사용자 할당이 포함됩니다.

온보딩 여정은 아래에 표시되어 있고 여정의 각 단계는 다음 섹션에 자세히 설명되어 있습니다.

![](/help/onboarding/onboarding-journey/assets/onboarding-journey.png)

이 여정은 요구 사항, 단계 및 접근 방식을 제시하는 시스템 관리자 사용자에 맞게 설계되었습니다. 여정은 성공적인 프로젝트를 위해 시스템 관리자가 상호 작용해야 하는 추가 가상 사용자를 정의하지만 여정의 관점은 관리자의 것입니다.

다음은 이 여정에서 상호 작용하는 가상 정보입니다.

| 모습 | 설명 | 여정의 역할 |
|---|---|---|
| 시스템 관리자 | 각 구성원이 AEM을 Cloud Service 리소스로 로그인하고 액세스할 수 있는 작업 권한에 따라 클라우드 리소스의 초기 프로비저닝 및 적절한 역할에 사용자를 할당합니다. | 액세스 권한부터 사용자의 모든 측면을 관리합니다. |
| AEM Author | 컨텐츠를 만들고 검토합니다. (컨텐츠는 여러 유형일 수 있습니다. 예를 들어, 페이지, 자산, 게시물)은 웹 사이트에 게시되기 전에 게시됩니다. | 권한이 부여되면 에서는 자체 배포 관리자의 여정을 시작할 수 있습니다. |
| 개발자 | 다른 소스의 컨텐츠를 소비하는 AEM 애플리케이션을 개발하는 경험이 있습니다 | 권한이 부여되면 자신의 개발자 여정을 시작할 수 있습니다 |
| 배포 관리자 | 환경을 추가 또는 업데이트하고, 파이프라인을 실행하고, 코드를 AEM 환경 또는 코드 품질에 배포합니다. | 권한이 부여되면 에서는 자체 배포 관리자의 여정을 시작할 수 있습니다. |

## 온보딩 여정 탐색 {#exploring-onboarding-journey}

이 여정에서 많은 주제를 살펴봅니다. 다음 문서는 AEM as a Cloud Service에 대한 온보딩 단계에 대한 기본 지식을 제공합니다. 여정의 특정 부분으로 직접 이동할 수 있지만 많은 개념이 이전 문서의 개념에 구축됩니다. 따라서 온보딩을 처음 사용하는 경우에는 시작 부분부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 기사 | 설명 |
|---|---|---|
| 0 | 온보딩 여정 | 이 문서 |
| 1 | <br>[시스템 관리자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=en)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en)<br>[Adobe Identity Management 시스템](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/ims.html?lang=en)<br>[](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/adobe-id.html?lang=en)<br>[Adobe ID 소개](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=en)<br>[Cloud Service 팀으로서 AEM 및 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en)<br>[Adobe 지원에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/onboarding-help-resources.html?lang=en)<br>[ | 온보딩 개념에 대해 알아봅니다. |
| 2 | 온보딩 시작하기 | Admin Console에 로그인하고 시스템 관리자로 프로파일을 확인하는 방법에 대해 알아봅니다 |
| 3 | Cloud Manager 제품 프로필에 팀 구성원 할당 | Cloud Manager 제품 프로필을 검토하고 팀 구성원을 Cloud Manager 제품 프로필에 할당하는 방법을 알아보십시오. |
| 4 | Cloud Manager를 통해 Cloud 리소스 설정 | 클라우드 리소스를 만드는 방법과 이를 수행할 수 있는 사용자를 알아봅니다. 또한 클라우드 프로그램 및 환경을 만드는 방법을 알아봅니다. |
| 5 | AEM에 Cloud Service 제품 프로필로 팀 구성원 할당 | 시스템 관리자가 Cloud Service 제품 프로필로 팀 구성원을 AEM에 할당하는 방법을 알아보십시오. |
| 6 | AEM 개발자 및 배포 관리자를 위한 학습 경로 | 개발자로서 Cloud Manager Git에 액세스 및 관리할 수 있는 방법과 배포 관리자로서 Cloud Manager에서 파이프라인을 설정하고 코드를 배포할 수 있는 방법을 알아봅니다. |
| 7 | AEM 사용자를 위한 학습 경로 | AEM 작성자로서 AEM as a Cloud Service 인스턴스에 액세스하고 AEM as a Cloud Service용 컨텐츠를 작성하는 방법에 대해 알아봅니다. |

## 다음은 무엇입니까? {#what-is-next}

이제 온보딩 여정을 시작할 준비가 되었습니다. 여정의 다음 부분으로 계속 이동하여 온보딩 프로세스 시작 문서를 읽어 보십시오.