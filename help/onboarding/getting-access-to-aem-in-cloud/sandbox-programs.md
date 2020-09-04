---
title: 샌드박스 프로그램 - Cloud Service
description: 샌드박스 프로그램 - Cloud Service
translation-type: tm+mt
source-git-commit: 81f2d4f4f956edbf88135a703df0162afd92bc43
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 0%

---


# 샌드박스 프로그램 {#sandbox-programs}

## 소개 {#introduction}

샌드박스 프로그램은 AEM Cloud Service에서 사용할 수 있는 두 가지 유형의 프로그램 중 하나이며 다른 프로그램은 정규 프로그램 중 하나입니다.

샌드박스는 일반적으로 교육, 실행 데모, 지원 또는 POC(Proof of of of Concept)의 목적을 위해 만들어집니다.그들은 라이브 트래픽을 운반하기 위한 것이 아니다. Cloud Service 약정 [으로 AEM의 적용을 받지 않습니다](https://www.adobe.com/legal/service-commitments.html).

샌드박스에서 생성된 환경은 자동 크기 조정을 위해 구성되지 않습니다. 따라서 성능이나 로드 테스트에 적합하지 않습니다.

샌드박스 프로그램에는 사이트 및 에셋이 포함되며 Git 저장소, 개발 환경 및 비프로덕션 파이프라인으로 자동 채워집니다.  Git 리포지토리는 AEM 프로젝트 원형을 기반으로 하는 샘플 프로젝트로 채워집니다.

프로그램 [유형에 대한 자세한 내용은 프로그램 및 프로그램 유형](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html) 이해를 참조하십시오.

### 샌드박스 프로그램의 속성 {#attributes-sandbox}

샌드박스 프로그램에는 다음과 같은 속성이 있습니다.

1. **프로그램 제작:** 샌드박스 프로그램 생성에는 자동이 포함됩니다.
   * 샘플 코드 및 컨텐츠로 프로젝트 설정
   * 개발 환경 조성
   * 개발 환경에 배포되는 비프로덕션 파이프라인 제작(개발 환경에 배포할 마스터 지점)

1. **솔루션:** 샌드박스 프로그램에는 AEM Sites 및 에셋이 포함됩니다.

1. **AEM 업데이트:** AEM 업데이트는 샌드박스 프로그램의 환경에 수동으로 적용할 수 있으며 자동으로 푸시되지 않습니다.

1. **최대 절전 모드:** 샌드박스 프로그램의 환경은 특정 기간 동안 활동이 감지되지 않으면 자동으로 동면됩니다. 최대 절전 모드 환경을 수동으로 해제할 수 있습니다.

### 샌드박스 프로그램 만들기 {#creating-sandbox-program}

프로그램 생성 마법사를 사용하면 샌드박스 프로그램을 만들 수 있습니다.

샌드박스 프로그램 생성 방법에 대해 알아보려면 [샌드박스 프로그램](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-sandbox-program) 만들기를 참조하십시오.

### 샌드박스 환경 만들기 {#creating-sandbox-environments}

샌드박스 프로그램은 프로그램 생성 시 자동 생성 방식으로 개발 환경에 전달됩니다. 개발 환경에는 기본적으로 작성자 및 게시 계층이 포함됩니다.

프로덕션-스테이지 환경 세트는 사용자가 프로덕션 파이프라인을 설정할 준비가 되면 샌드박스 프로그램에 수동으로 추가할 수 있습니다.

수동으로 환경을 만드는 방법에 대해 알아보려면 환경 [추가를](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments) 참조하십시오.

### 샌드박스 환경 삭제 {#deleting-sandbox-environments}

필요한 권한을 가진 사용자는 개발 또는 프로덕션/스테이지 환경 또는 세트를 삭제할 수 있습니다.

환경을 삭제하려면 환경 [삭제를](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment) 참조하십시오.


## 동면작업 및 동면제거 샌드박스 환경 {#hibernating-introduction}

특정 기간 동안 활동이 감지되지 않으면 샌드박스 프로그램 *환경이 최대* 절전 모드로 전환됩니다.

>[!NOTE]
>최대 최대 최대 최대 최대 최대 최대 절전 모드 일반 프로그램 환경은 절전 모드를 사용하지 않습니다.

### 최대 절전 모드 {#hibernation-introduction}

최대 절전 모드 실행 시 자동 또는 수동으로 실행할 수 있습니다. 샌드박스 프로그램 환경이 *최대 몇 분 정도 걸릴 수 있습니다*. 최대 절전 모드 동안 데이터가 유지됩니다.

최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 절전 모드

* **자동** 샌드박스 프로그램 환경은 8시간의 비활동 후 자동으로 최대 절전 상태로 전환되며 이는 작성자 및 게시 서비스가 요청을 받지 않음을 의미합니다.

* **수동**:사용자는 샌드박스 프로그램 환경에 수동으로 절전 모드를 해제할 수 있지만, 일정 기간(8시간)의 비활동 후에 자동으로 최대 절전 모드가 실행되므로 그럴 필요는 없습니다.

>[!CAUTION]
>최신 릴리스에서는 Cloud Manager에서 바로 개발자 콘솔로 링크해도 샌드박스 프로그램 환경의 최대 절전 모드를 사용할 수 없습니다. 해결 방법은 개발자 콘솔에서 한 번, url `#release-cm-p1234-e5678 where 1234` 1234의 끝에 다음 패턴을 추가하여 사용자 *프로그램 ID이고* 5678은 사용자 *환경 ID입니다*.

#### 수동 최대 절전 모드 사용 {#using-manual-hibernation}

다음 두 가지 방법으로 개발자 콘솔에서 샌드박스 프로그램의 최대 절전 모드를 수동으로 수행할 수 있습니다.

* 환경 세부 사항 화면
* 환경 목록 화면

>[!NOTE]
>Cloud Manager의 모든 사용자는 샌드박스 프로그램의 개발자 콘솔에 액세스할 수 있습니다.

아래의 단계에 따라 샌드박스 프로그램 환경을 수동으로 절전 모드로 전환하십시오.

1. 개발자 **콘솔로 이동합니다**.
환경 [카드](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) 에서 **개발자 콘솔에** 액세스하는 방법을 **알아보려면 개발자 콘솔** 액세스를참조하십시오.
   >[!IMPORTANT]
   >Cloud Manager에서 바로 **개발자 콘솔에** 연결해도 샌드박스 프로그램 환경의 최대 절전 모드를 수행할 수 있는 옵션이 제공되지 않습니다. 해결 방법은 개발자 콘솔에서 한 번, url `#release-cm-p1234-e5678 where 1234` 1234의 끝에 다음 패턴을 추가하여 사용자 *프로그램 ID이고* 5678은 사용자 *환경 ID입니다*.

1. Click **Hibernate**, as shown in the figure below:

   ![](assets/hibernate-1.png)

   또는,

   왼쪽 **상단에 있는 환경** 링크를 클릭하여 환경 목록을 확인한 다음 아래 그림과 같이 **Hibernate**&#x200B;를 클릭합니다.

   ![](assets/hibernate-1b.png)

1. Hibernate **를** 클릭하여 단계를 확인합니다.

   ![](assets/hibernate-2.png)

1. 최대 절전 모드에 성공하면 **개발자 콘솔** 화면에 환경에 대한 최대 절전 모드 프로세스 완료 알림이 표시됩니다.

   ![](assets/hibernate-4.png)


### 동면 해제 {#de-hibernation-introduction}

1. 개발자 **콘솔로 이동합니다**.
환경 [카드](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) 에서 **개발자 콘솔에** 액세스하는 방법을 **알아보려면 개발자 콘솔** 액세스를참조하십시오.

   >[!IMPORTANT]
   >Cloud Manager에서 바로 **개발자 콘솔에** 연결해도 샌드박스 프로그램 환경의 절전 모드를 해제할 수 있는 옵션이 제공되지 않습니다. 해결 방법은 개발자 콘솔에서 한 번, url `#release-cm-p1234-e5678 where 1234` 1234의 끝에 다음 패턴을 추가하여 사용자 *프로그램 ID이고* 5678은 사용자 *환경 ID입니다*.

   >[!NOTE]
   >또는 이미 최대 절전 **상태인 환경의 작성자 또는 게시 서비스에 액세스하려고 하면 개발자 콘솔로** 이동하여 최대 절전 모드 해제 기능을 수행할 수 있습니다.이 경우, 랜딩 페이지가 개발자 콘솔로의 링크와 함께 나타납니다. 아래의 동면자 환경 액세스 섹션을 참조하십시오.

   >[!IMPORTANT]
   >개발자 콘솔에 대한 액세스는 **Admin Console의** 클라우드 관리자 - 개발자 **역할에 의해 정의됩니다**. 개발자 역할 권한이 있는 사용자는 샌드박스 프로그램 환경의 절전 모드를 해제할 수 있습니다.

1. 아래 **그림과 같이 절전**&#x200B;해제 기능을 클릭합니다.

   ![](assets/de-hibernation-img1.png)

   또는,

   왼쪽 **상단에 있는 환경** 링크를 클릭하여 환경 목록을 확인한 다음 아래 그림에 표시된 대로 절전 **해제**&#x200B;옵션을 클릭합니다

   ![](assets/de-hibernate-1b.png)


1. 단계를 확인하려면 **절전 모드** 를 클릭합니다.

   ![](assets/de-hibernation-img2.png)

1. 최대 절전 모드 해제 프로세스가 시작되었다는 알림을 받게 되고 진행 내용이 업데이트됩니다.

   ![](assets/de-hibernation-img3.png)

1. 프로세스가 완료되면 샌드박스 프로그램 환경이 다시 활성화됩니다.

   ![](assets/de-hibernation-img4.png)

#### 최대 절전 모드 해제 권한 {#permissions-de-hibernate}

Cloud Service으로 AEM에 액세스할 수 있는 제품 프로필을 보유한 모든 사용자는 **개발자 콘솔에**&#x200B;액세스하여 환경의 최대 절전 모드를 해제할 수 있습니다.

사용자 권한 [설정에 대해서는 Cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html) Manager에서 사용자 및 역할 추가를 참조하십시오.

#### 동면기 환경 액세스 {#accessing-hibernated-environment}

최대 절전 모드 환경의 작성자 또는 게시 계층에 대해 브라우저를 요청하는 경우 아래 그림과 같이 사용자는 최대 절전 모드 상태를 설명하는 랜딩 페이지가 나타납니다.

![](assets/de-hibernation-img5.png)

### 중요 고려 사항 {#important-considerations}

최대 절전 모드 및 최대 절전 모드 해제 환경과 관련된 주요 고려 사항은 다음과 같습니다.

* 사용자는 파이프라인을 사용하여 최대 절전 모드 환경에 사용자 정의 코드를 배포할 수 있습니다. 이 환경은 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 절전 모드이며 새로운 코드는 최대 최대 절전 모드일 때 최대 절전 모드일 수 있습니다.

* AEM 업그레이드는 고객이 Cloud Manager에서 수동으로 트리거할 수 있는 최대 절전 모드 환경에 적용할 수 있습니다. 이 환경은 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 절전 환경이다.

>[!NOTE]
>현재 Cloud Manager는 환경이 최대 절전 모드인지 여부를 표시하지 않습니다.

## AEM 샌드박스 환경 업데이트 {#aem-updates-sandbox}

자세한 내용은 [AEM 버전 업데이트를](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates) 참조하십시오.

사용자는 샌드박스 프로그램의 환경에 AEM 업데이트를 수동으로 적용할 수 있습니다.

환경 [을](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#updating-dev-environment) 업데이트하는 방법에 대해서는 환경 업데이트를 참조하십시오.

>[!NOTE]
>* 수동 업데이트는 타깃팅된 환경에 제대로 구성된 파이프라인이 있는 경우에만 실행할 수 있습니다.
>* 프로덕션 *또는* 스테이지 *환경* 에 대한 수동업데이트는 다른 환경을 자동으로 업데이트합니다. Production+Stage 환경 세트는 동일한 AEM 릴리스에 있어야 합니다.






