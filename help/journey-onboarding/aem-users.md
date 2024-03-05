---
title: AEM 사용자 작업
description: 시스템 관리자가 필요한 클라우드 리소스를 설정한 후 AEM 사용자가 AEM as a Cloud Service에 액세스하여 콘텐츠를 작성하는 방법을 알아봅니다.
feature: Onboarding
role: Admin, User, Developer
exl-id: 86700cce-139f-451e-9c21-b38b6332f773
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: ht
source-wordcount: '576'
ht-degree: 100%

---


# AEM 사용자 작업 {#aem-user-tasks}

[온보딩 여정](overview.md)의 이 선택적 부분에서는 AEM 사용자가 AEM as a Cloud Service에 액세스하여 콘텐츠를 작성하는 방법을 배웁니다.

## 지금까지의 스토리 {#story-so-far}

온보딩 여정의 먼 길을 진행하시느라 수고하셨습니다. 축하합니다! 시스템 관리자가 [AEM 제품 프로필](assign-profiles-aem.md) 할당 문서를 통해 필요한 클라우드 리소스를 설정하고 액세스 권한을 부여하는 온보딩 여정을 완료했습니다.

이 시점에서 AEM 사용자는 콘텐츠 작성을 시작할 수 있습니다. 이러한 의미에서 온보딩이 완료되었으며 이제 이 문서에서 설명하는 새 AEM as a Cloud Service 시스템을 사용할 수 있습니다.

## 대상자 {#audience}

이 문서는 **AEM 사용자**&#x200B;의 관점에서 작성되었습니다.

시스템 관리자도 이와 동일한 작업을 수행할 수 있지만 일반적으로 이러한 역할은 다른 사용자가 담당합니다.

## 목표 {#objective}

이 문서는 시스템 관리자가 온보딩 여정의 이 시점까지 설명한 대로 모든 사용자를 온보딩하고 필요한 클라우드 리소스를 생성한 후 AEM 사용자의 기본 작업을 보여 주기 위한 온보딩 프로세스의 보충 자료입니다.

이 문서를 읽고 난 후에는 다음 방법을 이해할 수 있습니다.

* Cloud Manager 액세스
* AEM as a Cloud Service의 인스턴스 로그인

## 사전 요구 사항 {#prerequisites}

AEM 사용자로서 이 문서에 설명된 작업을 시작하기 전에 시스템 관리자가 이 온보딩 여정의 모든 단계를 완료했는지 확인하십시오. 이 의미는 다음과 같습니다.

* 시스템 관리자가 **AEM 사용자** 또는 **AEM 관리자** 제품 프로필에 사용자를 할당했습니다.
* 클라우드 리소스가 설정되었습니다.

## AEM 로그인 {#login-aem}

AEM 작성자는 AEM에 로그인해야 콘텐츠 생성을 시작할 수 있습니다.

1. Cloud Manager의 로그인 페이지([`https://my.cloudmanager.adobe.com`.](https://my.cloudmanager.adobe.com/))로 이동합니다.

1. Cloud Manager의 **프로그램 및 제품** 페이지에서 적절한 프로그램을 선택하여 **개요** 페이지를 시작합니다. 액세스할 프로그램이 확실하지 않은 경우 시스템 관리자에게 문의하십시오.

1. Cloud Manager의 **개요** 페이지에서 **환경** 카드의 작성자 링크를 클릭합니다.

   ![환경 카드](/help/journey-onboarding/assets/author-environ.png)

1. 그러면 Adobe ID를 사용하여 작성자 환경에 로그인할 수 있는 새 탭이 열립니다.

축하합니다! 이제 작성자에 성공적으로 로그인했습니다.

>[!TIP]
>
>AEM 작성자 인스턴스에 대한 링크에 책갈피를 표시하면 매번 Cloud Manager를 거치지 않고 직접 열 수 있습니다.

## 다음 단계 {#whats-next}

지금까지 이 문서를 통해 다음과 같은 작업을 수행하는 방법에 대해 알아보았습니다.

* Cloud Manager 액세스
* AEM as a Cloud Service의 인스턴스 로그인

축하합니다! 이제 AEM 콘텐츠를 작성하고 게시할 준비가 되었습니다. AEM에서 콘텐츠를 작성하고 관리하는 방법에 대한 자세한 내용은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

개발자와 배포 관리자가 AEM as a Cloud Service에 대한 사용자 정의 애플리케이션을 만들고 관리하는 방법에 관심이 있는 경우 온보딩 여정의 두 번째 선택적 부분인 [AEM 개발자 작업](developers.md)을 계속 진행하십시오.

>[!TIP]
>
>이제 온보딩되었으므로 최소한의 AEM 구성으로 [AEM 참조 데모 추가 기능을 샌드박스 환경에 손쉽게 추가](/help/journey-sites/demos-add-on/overview.md)하는 방법을 배우고 모범 사례를 기반으로 하는 풍부한 예를 통해 AEM의 강력한 기능을 테스트할 수 있습니다.

## 추가 리소스 {#additional-resources}

온보딩 여정의 콘텐츠를 능가하려는 경우 다음은 추가적인 옵션 리소스입니다.

[페이지 작성에 대한 빠른 시작 안내서](/help/sites-cloud/authoring/quick-start.md) - AEM의 작성 기본 사항에 대한 간략한 개요를 보려면 여기에서 시작하십시오.
[Headless 제작 여정](/help/journey-headless/author/overview.md) - Headless 콘텐츠를 작성하려면 이 안내서 소개를 따르십시오.
