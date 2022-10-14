---
title: 환경 만들기
description: Cloud Manager를 사용하여 첫 번째 환경을 만드는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 100%

---

# 환경 만들기 {#create-environments}

이 [온보딩 여정](overview.md) 부분에서는 Cloud Manager를 사용하여 첫 번째 환경을 만드는 방법을 배웁니다.

## 목표 {#objective}

이 온보딩 여정의 이전 문서인 [프로그램 만들기](create-program.md) 단계를 진행하고 나면 이제 고유한 Cloud Manager 프로그램을 만들어졌을 것입니다. 이제 Cloud Manager를 사용하여 해당 프로그램에 대한 첫 번째 환경을 만드는 방법을 배울 수 있습니다.

이 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* 환경이 무엇인지 이해합니다.
* 다양한 환경의 차이점을 알게 됩니다.
* 자신만의 환경을 만들 수 있습니다.

## 환경이란? {#environments}

환경은 Cloud Manager 계층 구조 내에서 프로그램 아래에 있습니다. 프로그램을 통해 솔루션을 구성하고 특정 팀원에게 해당 프로그램에 대한 액세스 권한을 부여할 수 있지만 환경은 특정 프로그램에 속하며 해당 프로그램 내 Adobe 솔루션의 개별 인스턴스입니다. 환경은 콘텐츠 작성 또는 새로운 개발 테스트와 같은 특정 목적으로 사용됩니다. Cloud Manager의 CI/CD 파이프라인은 git 저장소에서 이러한 환경으로 코드를 쉽게 배포할 수 있습니다.

여행 관련 미디어를 주로 다루는 테넌트인 이론적 WKND Travel and Adventure Enterprises의 예를 들자면, WKND Magazine 부서를 위한 Sites 프로그램과 WKND Media 부서를 위한 Assets 프로그램이라는 두 가지 프로그램이 있을 수 있습니다. 각 프로그램에는 사이트의 실제 트래픽을 처리하는 프로덕션 환경과 새로운 애플리케이션 코드를 테스트하기 위한 개발 환경과 같은 몇 가지 환경이 있을 수 있습니다.

환경에는 세 가지 유형이 있습니다.

* **프로덕션 및 스테이징** - 프로덕션 환경 및 스테이징 환경은 쌍으로 구성되며 각각 프로덕션 및 테스트 목적으로 사용됩니다.
* **개발** - 개발 환경은 개발 목적뿐만 아니라 테스트 목적으로도 만들 수 있으며 비프로덕션 파이프라인에만 연결할 수 있습니다.

이 온보딩 여정의 목적을 위해 여기서는 개발 환경을 만듭니다.

## 환경 만들기 {#creating-environments}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 환경을 추가할 프로그램을 클릭합니다.

1. **프로그램 개요** 페이지에서 **환경** 카드의 **환경 추가**&#x200B;를 클릭하여 환경을 추가합니다.

   ![환경 카드](/help/implementing/cloud-manager/assets/no-environments.png)

   * **환경 추가** 옵션은 **환경** 탭에서도 사용할 수 있습니다.

      ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab.png)

   * 사용 권한이 없거나 사용 허가된 리소스에 따라 **환경 추가** 옵션이 비활성화될 수 있습니다.

1. **환경 추가** 대화 상자가 나타나면 다음 작업을 수행하십시오.

   * **환경 유형**&#x200B;을 선택합니다.
      * 사용 가능한/사용된 환경의 수가 개발 환경 유형 뒤의 괄호 안에 표시됩니다.
   * **환경 이름**&#x200B;을 제공합니다.
   * **환경 설명**&#x200B;을 제공합니다.
   * **클라우드 영역**&#x200B;을 선택합니다.

   ![환경 추가 대화 상자](/help/implementing/cloud-manager/assets/add-environment2.png)

1. **저장**&#x200B;을 클릭하여 지정된 환경을 추가합니다.

환경을 사용할 수 있게 되면 **개발자** 제품 프로필에 할당된 조직의 멤버가 Cloud Manager에 로그인하여 Cloud Manager git 저장소를 관리할 수 있습니다.

## 다음 단계 {#whats-next}

온보딩 여정의 이 부분을 읽은 후에는 다음과 같은 작업을 수행할 수 있습니다.

* 환경이 무엇인지 이해합니다.
* 다양한 환경의 차이점을 알게 됩니다.
* 자신만의 환경을 만들 수 있습니다.

클라우드 리소스가 만들어지고 팀에서 액세스할 수 있습니다. 시스템 관리자는 먼저 팀원이 해당 리소스에 액세스할 수 있도록 Adobe Admin Console에서 AEM as a Cloud Service 제품 프로필을 할당해야 합니다.

따라서 다음에 [AEM as a Cloud Service 제품 프로필에 팀원 할당](assign-profiles-aem.md) 문서를 검토하여 온보딩 여정을 계속해야 합니다. 이 문서에서는 팀원에게 새 환경에 액세스하는 데 필요한 권한을 부여하는 방법을 배워봅니다.

## 추가 리소스 {#additional-resources}

자세한 내용은 추가 리소스를 참조하십시오.

* [환경 관리](/help/implementing/cloud-manager/manage-environments.md) - 만들 수 있는 환경 유형과 Cloud Manager 프로젝트용으로 환경을 만드는 방법에 대해 알아봅니다.
* [Adobe Cloud Manager 사용 - 환경](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) - Cloud Manager 환경은 AEM 작성, 게시 및 Dispatcher 서비스로 구성됩니다. 서로 다른 환경에서 역할을 지원하고 다양한 CI/CD 파이프라인을 사용하여 관여하는 방법을 알아봅니다.
