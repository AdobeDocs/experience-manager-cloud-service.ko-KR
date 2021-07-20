---
title: Cloud Manager를 통해 Cloud 리소스 설정
description: Cloud Manager를 통해 클라우드 리소스를 설정하는 방법을 배우려면 이 페이지를 따르십시오
hide: true
hidefromtoc: true
index: false
source-git-commit: 021146e4e1d65c7fe81ed3dba70b32daf34b9704
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# Cloud Manager를 통해 Cloud 리소스 설정 {#setup-cloud-resources}

&#39;비즈니스 소유자&#39; 역할에 할당된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다. 뒤이어 &#39;비즈니스 소유자&#39; 제품 프로필에 할당된 팀 구성원은 Cloud Manager에 로그인하여 클라우드 프로그램 및 환경을 만들어야 전문가 팀을 시작할 수 있습니다.

## 목표 {#objective}

이 문서는 클라우드 리소스를 만드는 방법과 이 작업을 수행할 수 있는 사용자를 이해하는 데 도움이 됩니다.

이 섹션을 읽은 후에는 다음을 수행해야 합니다.

* &#39;비즈니스 소유자&#39; 역할에 할당된 시스템 관리자가 Cloud Manager에 먼저 액세스하여 로그인해야 한다는 것을 이해합니다
* 클라우드 프로그램 및 환경을 만드는 방법을 이해합니다.

## 소개 {#introduction}

클라우드 리소스 추가는 Cloud Manager 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이 Cloud Manager를 통해 수행됩니다. 일반적으로 비즈니스 요구 사항을 이해하고 초기 Cloud Manager 설정을 완료하는 사용자입니다.

아래 섹션을 따라 [클라우드 서비스 프로그램](#create-cloud-service-program) 및 [환경](#create-cloud-environments)을 만드는 방법을 알아보십시오.

### 전제 조건 {#prerequisites}

* &#39;비즈니스 소유자&#39; 역할에 할당된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다.

* Cloud Manager 탐색 및 로그인 방법을 이해합니다

* Cloud Manager 제품 프로필을 숙지하십시오

* 프로그램을 만들기 위한 고려 사항을 이해합니다. 자세한 내용은 이 비디오를 참조하십시오.

* Cloud Manager 프로그램 및 환경의 개념 이해

## Cloud Manager로 이동 {#navigate-cloud-manager}

1. 비즈니스 소유자 사용자는 시작할 수 있는 위치에서 환영 이메일을 받거나 찾을 수 없는 경우 experience.adobe.com으로 직접 이동하여 Adobe ID을 사용하여 로그인합니다.

1. Experience Cloud 홈페이지에서 Experience Manager을 선택합니다.


1. AEM 홈 페이지로 이동합니다. 여기에서 Cloud Manager를 선택합니다.


1. 아래와 같이 Cloud Manager 랜딩 페이지로 이동합니다.


1. 이제 비즈니스 소유자 제품 프로필이 할당되었는지 확인합니다. 이렇게 하려면 오른쪽 상단에서 아래 표시된 대로 프로필을 선택합니다.


1. 이제 사용자 역할을 선택하고 비즈니스 소유자에게 할당되었는지 확인합니다.


   잘했어요! Cloud Manager를 비즈니스 소유자로 로그인했습니다!

## Cloud Service 프로그램 만들기 {#create-cloud-service-program}


1. 아래 표시된 대로 Cloud Manager 랜딩 페이지로 이동합니다.

   >[!NOTE]
   >이 단계를 성공적으로 완료하려면 Cloud Manager 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이어야 합니다.

1. 여기에서 프로그램 추가 마법사를 시작하려면 프로그램 추가를 선택합니다. 프로그램을 만들기 전에 AEMaaCS 프로그램을 만드는 방법과 중요한 고려 사항을 살펴보려면 비디오를 시청하십시오.

1. 프로그램 추가 마법사를 사용하는 방법에 대한 단계별 지침을 보려면 여기 로 이동하십시오.

   >[!CAUTION]
   >만든 후에는 프로그램 이름을 변경할 수 없습니다. 프로그램에 어떤 이름을 지정할 것인지 확인하는 것이 좋습니다.

   프로그램 이름을 변경해야 하는 경우, Adobe 지원이 있는 사례를 열거나 Adobe 담당자에게 문의하십시오. 그들은 프로그램을 효과적으로 삭제하는 데 도움을 줄 것이다. 팀원들이 한 잠재적인 업무 손실과 함께 처음부터 다시 시작해야 합니다.

1. 클라우드 프로그램을 성공적으로 만들면 프로그램으로 이동하여 아래와 같이 프로그램의 개요 페이지를 볼 수 있습니다.

1. 개발자 구성원을 아직 추가하지 않은 경우 지금이 Cloud Manager 팀에 추가할 적기입니다. 개발자 제품 프로필에 사용자 추가 로 이동하여 요약된 단계를 수행하십시오.

1. 개발자 제품 프로필에 할당된 구성원은 Cloud Manager에 로그인하고 Cloud Manager Git을 관리할 수 있습니다.


   잘했어요! 이제 프로그램이 성공적으로 만들어지면 개발자가 액세스할 수 있는 Cloud Manager Git을 사용할 수 있습니다.


## 클라우드 환경 만들기 {#create-cloud-environments}

1. 클라우드 프로그램을 성공적으로 만든 후에는 Cloud Manager 개요 페이지로 이동하고 환경 카드에서 추가 를 선택하여 클라우드 환경을 만듭니다.

   >[!NOTE]
   >이 단계를 성공적으로 완료하려면 비즈니스 소유자 또는 배포 관리자 역할의 Cloud Manager 사용자가 로그인해야 합니다.

   또한 빠른 비디오 자습서를 시청하여 Cloud Manager 환경과 이를 프로그램에 추가하는 방법을 알아보십시오.

1. 이렇게 하면 환경 추가를 안내하는 환경 추가 마법사가 시작됩니다. 먼저 개발 환경을 추가하여 익숙해지십시오.

1. 아직 추가하지 않은 경우 계속해서 개발자 구성원을 Cloud Manager 팀에 추가하고 개발자 제품 프로필에 사용자 추가로 이동하여 요약된 단계를 따를 수 있습니다. 이러한 방식으로 개발자는 Cloud Manager로 이동 및 Cloud Manager Git 관리를 시작할 수 있습니다.


   축하합니다! 이제 클라우드 프로그램 환경이 만들어졌고 개발자가 팀에 추가되었습니다!

## 다음은 무엇입니까? {#whats-next}

이제 Cloud Manager 관리 권한이 충분하지 않으므로 팀 구성원에게 인스턴스에 대한 권한을 부여해야 합니다. 클라우드 리소스가 만들어지고 팀이 액세스할 준비가 되었으므로 시스템 관리자는 팀 구성원을 AEM에 Admin Console의 Cloud Service 제품 프로필로 할당해야 합니다.

>[!NOTE]
>Cloud Service 사용자로 AEM에 대한 액세스 권한을 부여받으려면 두 제품 프로필 &#39;AEM 사용자&#39; 또는 &#39;AEM 관리자&#39; 중 하나에 속해야 합니다. 추가 정보.

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* 프로그램 유형 및 프로그램 추가
* 환경 유형 및 환경 추가
* Cloud Manager Git 관리
* Admin Console에서 AEM as a Cloud Service에 대한 액세스 구성
