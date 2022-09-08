---
title: 프로그램 제작
description: Cloud Manager를 사용하여 첫 번째 프로그램을 만드는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
source-git-commit: fbf1e0b7cefb1dc981d7ee106283280fb2225007
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 4%

---

# 프로그램 제작 {#create-program}

의 이 부분에서 [온보딩 여정,](overview.md) 클라우드 관리자를 사용하여 첫 번째 프로그램을 만드는 방법을 알아봅니다.

## 목표 {#objective}

이 온보딩 여정에서 이전 문서를 검토한 후 [Cloud Manager에 액세스,](cloud-manager.md) Cloud Manager에 대한 적절한 액세스 권한이 있는지 확인했습니다. 이제 첫 번째 프로그램을 만들 수 있습니다.

이 문서를 읽은 후에는 다음 작업을 수행합니다.

* 프로그램이 무엇인지 파악합니다.
* 프로덕션 프로그램과 샌드박스 프로그램의 차이점을 파악합니다.
* 자신만의 프로그램을 만들 수 있습니다.

## 프로그램이란 무엇입니까? {#programs}

프로그램은 Cloud Manager에서 가장 높은 수준의 조직입니다. Adobe을 사용하는 라이선스에 따라 프로그램을 통해 솔루션을 구성하고 해당 프로그램에 특정 팀 구성원에게 액세스 권한을 부여할 수 있습니다.

Cloud Manager 프로그램은 Cloud Manager 환경 세트를 나타냅니다. 이러한 프로그램은 일반적으로 SLA(Service Level Agreement)에 해당하는 비즈니스 이니셔티브의 논리적 집합을 지원합니다. 예를 들어, 한 프로그램은 조직에 대한 글로벌 공개 웹 사이트를 지원하는 AEM 리소스를 나타내고, 다른 프로그램은 내부 중앙 DAM을 나타냅니다.

여행 관련 미디어에 중점을 둔 임차인인 이론적 WKND Travel and Adventure Enterprises의 예를 생각해보면 두 가지 프로그램이 있을 수 있습니다. WKND매거진사업부와 WKND미디어사업부의 자산 프로그램 1종. 다른 팀원들도 그들 자신의 노동 요구 사항 때문에 다른 프로그램에 접근할 수 있을 것이다.

다음과 같은 두 가지 유형의 프로그램이 있습니다.

* A **생산 프로그램** 사이트에 대해 라이브 트래픽을 활성화하도록 가 생성되었습니다. 실제 환경입니다.
* A **샌드박스 프로그램** 는 일반적으로 교육, 데모 실행, 사용, POC 또는 설명서 용도로 사용됩니다.

다른 용도로 사용되기 때문에 다른 환경에 다른 옵션이 있습니다. 하지만 만드는 과정은 비슷합니다. 이 온보딩 여정을 위해 샌드박스 환경을 만듭니다.

>[!NOTE]
>
>기본적으로 AEM 환경에 액세스할 수 있는 사용자도 Cloud >Manager 사용자 역할을 갖습니다. 의 이 역할 자체는 사용자에게 프로그램 세부 사항 보기에 대한 액세스 권한을 제공하기에 충분하지 않습니다. 이러한 Cloud Manager 사용자 역할만 있는 사용자는 프로그램 메뉴 옵션을 통해 AEM 환경 작성자 URL로 이동할 수 있습니다(환경이 있는 경우). 이러한 사용자는 프로그램 수준 액세스 권한을 얻으려면 관리자에게 문의해야 합니다.

## 샌드박스 프로그램 만들기 {#create-sandbox}

다음 단계에 따라 샌드박스 프로그램을 만듭니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. Cloud Manager의 랜딩 페이지에서 클릭 **프로그램 추가** 화면 오른쪽 상단 모서리에서 을(를) 클릭합니다.

   ![Cloud Manager 랜딩 페이지](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

1. 프로그램 만들기 마법사에서 **샌드박스 설정**&#x200B;에서 프로그램 이름을 제공한 다음 **만들기**.

   ![프로그램 유형 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

설정 프로세스가 진행되면 상태 표시기가 있는 새 샌드박스 프로그램 카드가 랜딩 페이지에 표시됩니다.

![개요 페이지에서 샌드박스 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

프로그램이 완료되면 조직의 구성원이 **개발자** 제품 프로필은 Cloud Manager에 로그인하고 Cloud Manager git 리포지토리를 관리할 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

첫 번째 프로그램이 만들어지면 이를 위한 환경을 만들 수 있습니다. 다음에 문서를 검토하여 온보딩 여정을 계속해야 합니다 [환경을 만듭니다.](create-environments.md)

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [프로그램 및 프로그램 유형](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) - Cloud Manager의 계층 구조, 다양한 유형의 프로그램이 해당 구조에 어떻게 적합한지, 그리고 어떻게 다른지 알아봅니다.
* [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) - Cloud Manager를 사용하여 교육, 데모, POC 또는 기타 비프로덕션 목적으로 자체 샌드박스 프로그램을 만드는 방법을 알아봅니다.
* [프로덕션 프로그램 생성](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) - Cloud Manager를 사용하여 라이브 트래픽을 호스팅하기 위한 자체 프로덕션 프로그램을 만드는 방법을 알아봅니다.
* [Cloud Manager 사용 - 프로그램](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) - Cloud Manager 프로그램은 일반적으로 구매한 SLA(서비스 수준 계약)에 해당하는 비즈니스 이니셔티브의 논리적 집합을 지원하는 AEM 환경의 집합을 나타냅니다.
