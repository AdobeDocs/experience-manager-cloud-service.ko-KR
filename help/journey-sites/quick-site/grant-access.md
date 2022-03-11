---
title: 프런트엔드 개발자에게 액세스 권한 부여
description: 프런트 엔드 개발자를 Cloud Manager에 온보딩하여 AEM 사이트 git 리포지토리 및 파이프라인에 액세스할 수 있습니다.
exl-id: 58e95c92-b859-4bb9-aa62-7766510486fd
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 0%

---

# 프런트엔드 개발자에게 액세스 권한 부여 {#grant-fed-access}

프런트 엔드 개발자를 Cloud Manager에 온보딩하여 AEM 사이트 git 리포지토리 및 파이프라인에 액세스할 수 있습니다.

## 지금까지 그 이야기 {#story-so-far}

AEM 빠른 사이트 만들기 여정의 이전 문서에서, [파이프라인을 설정합니다.](pipeline-setup.md) 프런트 엔드 파이프라인을 만들어 사이트 테마의 사용자 지정을 관리하는 방법을 배웠으며, 이제 다음을 수행해야 합니다.

* 프런트엔드 파이프라인이 무엇인지 파악합니다.
* Cloud Manager에서 프런트엔드 파이프라인을 설정하는 방법을 알아봅니다.

이제 프런트 엔드 개발자가 AEM git 리포지토리 및 생성한 파이프라인에 액세스할 수 있도록 온보딩 프로세스를 통해 Cloud Manager에 대한 프런트 엔드 개발자 액세스 권한을 부여해야 합니다.

## 목표 {#objective}

Cloud Manager에 대한 액세스 권한을 부여하고 사용자 역할을 사용자에게 할당하는 프로세스를 온보딩이라고 합니다. 이 문서에서는 프런트 엔드 개발자에게 온보딩하는 데 가장 중요한 단계에 대한 개요를 제공하며 다음 내용을 읽고 나면 이를 알 수 있습니다.

* 프런트엔드 개발자를 사용자로 추가하는 방법
* 프런트 엔드 개발자에게 필요한 역할을 부여하는 방법입니다.

>[!TIP]
>
>팀에에 연결된 AEM as a Cloud Service에 온보딩에 대한 전체 설명서 여정이 있습니다. [추가 리소스 섹션](#additional-resources) 프로세스에 대한 추가 세부 정보가 필요한 경우 이 문서를 참조하십시오.

## 책임 역할 {#responsible-role}

이 여정 부분은 Cloud Manager 관리자에게 적용됩니다.

## 요구 사항 {#requirements}

* 회원이어야 합니다. **비즈니스 소유자** Cloud Manager의 역할.
* 다음을 수행해야 합니다. **Sys 관리** ( Cloud Manager)를 참조하십시오.
* Admin Console에 액세스할 수 있어야 합니다.

## 사용자로 프런트엔드 개발자 추가 {#add-fed-user}

먼저 Admin Console을 사용하여 프런트엔드 개발자를 사용자로 추가해야 합니다.

1. 에서 Admin Console에 로그인합니다. [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).

1. 로그인하면 다음 이미지와 유사한 개요 페이지가 표시됩니다.

   ![Admin Console 개요](assets/admin-console.png)

1. 화면의 오른쪽 상단 모서리에서 조직 이름을 확인하여 해당 조직에 있는지 확인하십시오.

   ![조직 이름 확인](assets/correct-org.png)

1. 선택 **Adobe Experience Manager as a Cloud Service** 에서 **제품 및 서비스** 카드.

   ![AEMaaCS 선택](assets/select-aemaacs.png)

1. 사전 구성된 Cloud Manager 제품 프로필 목록이 표시됩니다. 이러한 프로필이 표시되지 않으면 조직에 올바른 권한이 없을 수 있으므로 Cloud Manager 관리자에게 문의하십시오.

   ![제품 프로필](assets/product-profiles.png)

1. 프런트엔드 개발자를 올바른 프로필에 할당하려면 **사용자** 탭한 다음 **사용자 추가** 버튼을 클릭합니다.

   ![사용자 추가](assets/add-user.png)

1. 에서 **팀에 사용자 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID을 선택합니다.

   ![팀에 사용자 추가](assets/add-to-team.png)

1. 에서 **제품** 선택, 더하기 기호를 탭하거나 클릭한 다음, **Adobe Experience Manager as a Cloud Service** 그리고 **배포 관리자** 및 **개발자** 제품 프로필을 사용자에게 표시합니다.

   ![팀 프로필 할당](assets/assign-team.png)

1. 탭 또는 클릭 **저장** 또한 사용자로 추가한 프런트 엔드 개발자에게 환영 이메일을 보냅니다.

초대받은 프런트 엔드 개발자는 환영 이메일에서 링크를 클릭하고 Adobe ID을 사용하여 로그인하여 Cloud Manager에 액세스할 수 있습니다.

## 프런트엔드 개발자로 핸드오버 {#handover}

프런트 엔드 개발자에게 가는 도중에 Cloud Manager에 대한 이메일 초대를 받으면 이제 사용자와 AEM 관리자는 사용자 지정을 시작하는 데 필요한 나머지 정보를 프런트 엔드 개발자에게 제공할 수 있습니다.

* A [일반 컨텐츠에 대한 경로](#example-page)
* 다음과 같은 테마 소스 [다운로드했습니다.](#download-theme)
* 다음 [프록시 사용자 자격 증명](#proxy-user)
* 프로그램 이름 또는 프로그램 URL입니다 [cloud Manager에서 복사](pipeline-setup.md#login)
* 프런트엔드 설계 요구 사항

## 다음은 무엇입니까? {#what-is-next}

이제 AEM 빠른 사이트 만들기 여정의 이 부분을 완료했으므로 다음 사항을 알아야 합니다.

* 프런트엔드 개발자를 사용자로 추가하는 방법
* 프런트 엔드 개발자에게 필요한 역할을 부여하는 방법입니다.

이 지식을 바탕으로 작성하고 다음 문서를 검토하여 AEM 빠른 사이트 만들기 여정을 계속 진행합니다 [Git 리포지토리 액세스 정보 검색,](retrieve-access.md) 프런트 엔드 개발자에게만 중점을 두고 전환하며 프런트 엔드 개발자 사용자가 Cloud Manager에서 git 리포지토리 정보에 액세스하는 방법에 대해 설명합니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 빠른 사이트 만들기 여정의 다음 부분으로 이동하는 것이 좋습니다 [프런트엔드 개발자 자격 증명 검색,](retrieve-access.md) 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [온보딩 여정](/help/journey-onboarding/home.md) - 이 안내서는 AEM as a Cloud Service에 대한 액세스 및 팀 설정을 위한 시작점 역할을 합니다.
