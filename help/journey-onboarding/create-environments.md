---
title: 환경 만들기
description: Cloud Manager를 사용하여 첫 번째 환경을 만드는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 3%

---

# 환경 만들기 {#create-environments}

의 이 부분에서 [온보딩 여정,](overview.md) 클라우드 관리자를 사용하여 첫 번째 환경을 만드는 방법을 알아봅니다.

## 목표 {#objective}

이 온보딩 여정에서 이전 문서를 읽은 후 [프로그램 만들기,](create-program.md) 이제 고유한 Cloud Manager 프로그램이 제공됩니다. 이제 Cloud Manager를 사용하여 해당 프로그램에 대한 첫 번째 환경을 만드는 방법을 살펴볼 수 있습니다.

이 문서를 읽은 후 다음을 수행합니다.

* 환경이 무엇인지 파악합니다.
* 다른 환경 간의 차이점을 파악합니다.
* 자신만의 환경을 만들 수 있습니다.

## 환경이란 무엇입니까? {#environments}

환경은 Cloud Manager 계층 구조에서 프로그램 아래에 있습니다. 프로그램을 사용하면 솔루션을 구성하고 특정 팀 구성원에게 해당 프로그램에 대한 액세스 권한을 부여할 수 있지만, 환경은 특정 프로그램에 속하며 해당 프로그램 내의 Adobe 솔루션의 개별 인스턴스입니다. 환경은 컨텐츠 작성이나 새로운 개발 사항 테스트와 같은 특정 용도로 사용됩니다. Cloud Manager의 CI/CD 파이프라인을 통해 Git 리포지토리에서 이러한 환경에 코드를 쉽게 배포할 수 있습니다.

여행 관련 미디어에 중점을 둔 임차인인 이론적 WKND Travel and Adventure Enterprises의 예를 생각해보면 두 가지 프로그램이 있을 수 있습니다. WKND매거진사업부와 WKND미디어사업부의 자산 프로그램 1종. 각 프로그램에는 사이트의 실제 트래픽을 제공하는 프로덕션 환경과 새 애플리케이션 코드를 테스트하는 하나의 개발 환경과 같은 두 가지 환경이 있을 수 있습니다.

다음과 같은 세 가지 유형의 환경이 있습니다.

* **프로덕션 및 스테이지** - 프로덕션 및 스테이징 환경은 쌍으로 사용할 수 있으며, 각각 프로덕션 및 테스트 용도로 사용됩니다.
* **개발** - 개발 환경은 개발 및 테스트 목적으로 만들 수 있으며 비프로덕션 파이프라인에만 연결할 수 있습니다.

이 온보딩 여정을 위해 개발 환경을 만듭니다.

## 환경 만들기 {#creating-environments}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 환경을 추가할 프로그램을 클릭합니다.

1. 에서 **프로그램 개요** 페이지를 클릭합니다. **환경 추가** on **환경** 환경을 추가할 카드입니다.

   ![환경 카드](/help/implementing/cloud-manager/assets/no-environments.png)

   * 다음 **환경 추가** 옵션을 사용할 수도 있습니다 **환경** 탭.

      ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab.png)

   * 다음 **환경 추가** 권한이 없거나 라이선스가 부여된 리소스에 따라 옵션을 사용할 수 없습니다.

1. 에서 **환경 추가** 대화 상자가 표시됩니다.

   * 선택 **환경 유형**.
      * 사용 가능한/사용된 환경 수는 개발 환경 유형 뒤에 괄호로 표시됩니다.
   * 다음을 제공합니다. **환경 이름**.
   * 다음을 제공합니다. **환경 설명**.
   * 선택 **클라우드 지역**.

   ![환경 추가 대화 상자](/help/implementing/cloud-manager/assets/add-environment2.png)

1. 클릭 **저장** 지정된 환경을 추가하려면

환경을 사용할 수 있게 되면 조직의 구성원에게 **개발자** 제품 프로필은 Cloud Manager에 로그인하고 Cloud Manager git 리포지토리를 관리할 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

온보딩 여정의 이 부분을 읽으셨으므로 다음을 수행해야 합니다.

* 환경이 무엇인지 파악합니다.
* 다른 환경 간의 차이점을 파악합니다.
* 자신만의 환경을 만들 수 있습니다.

클라우드 리소스가 만들어져서 팀이 액세스할 수 있습니다. 시스템 관리자는 먼저 팀 구성원을 Adobe Admin Console의 as a Cloud Service 제품 프로필에 할당하여 해당 리소스에 액세스해야 합니다.

따라서 다음 번에 문서를 검토하여 온보딩 여정을 계속해야 합니다 [AEM as a Cloud Service 제품 프로필에 팀 구성원을 할당합니다.](assign-profiles-aem.md)  이 문서에서는 팀 구성원에게 새 환경에 액세스하는 데 필요한 권한을 부여하는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [환경 관리](/help/implementing/cloud-manager/manage-environments.md) - 만들 수 있는 환경 유형과 Cloud Manager 프로젝트용 환경 유형을 만드는 방법에 대해 알아봅니다
* [Cloud Manager 사용 - 환경](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) - Cloud Manager 환경은 AEM 작성, 게시 및 디스패처 서비스로 구성됩니다. 다양한 환경이 역할을 지원하고 다른 CI/CD 파이프라인을 사용하여 참여할 수 있는 방법을 알아봅니다.
