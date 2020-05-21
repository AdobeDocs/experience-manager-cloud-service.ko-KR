---
title: 샌드박스 프로그램 - 클라우드 서비스
description: 샌드박스 프로그램 - 클라우드 서비스
translation-type: tm+mt
source-git-commit: eb874176c71d7f3d03d953f7bae4cb3db2ffb3b9
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# 샌드박스 프로그램 {#sandbox-programs}

## 소개 {#introduction}

샌드박스 프로그램은 AEM Cloud Service에서 사용할 수 있는 두 가지 유형의 프로그램 중 하나이며, 다른 프로그램은 정규 프로그램 중 하나입니다.

샌드박스는 일반적으로 교육, 실행 데모, 지원 또는 POC의 목적을 위해 만들어집니다. 그들은 라이브 트래픽을 운반하기 위한 것이 아니다.

샌드박스 프로그램에는 사이트 및 에셋이 포함되며 샘플 코드, 개발 환경 및 비프로덕션 파이프라인이 포함된 Git 분기로 자동 채워집니다.

프로그램 유형에 대한 자세한 내용은 프로그램 및 프로그램 유형 [이해를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html).

### 샌드박스 프로그램의 속성 {#attributes-sandbox}

샌드박스 프로그램에는 다음과 같은 속성이 있습니다.

1. **프로그램 제작:** 샌드박스 프로그램 생성에는 자동이 포함됩니다.
   * 샘플 코드 및 컨텐츠로 프로젝트 설정
   * 개발 환경 조성
   * 개발 환경에 배포되는 비프로덕션 파이프라인 제작(개발 환경에 배포하는 마스터 지점)

1. **포함된 솔루션:** 샌드박스 프로그램에는 사이트 및 자산이 포함됩니다.

1. **AEM 업데이트:** AEM 업데이트는 샌드박스 프로그램의 환경에 수동으로 적용할 수 있으며 자동으로 푸시되지 않습니다.

1. **최대 절전 모드:** 특정 기간 동안 활동이 감지되지 않으면 샌드박스 프로그램의 환경에서 자동으로 동면됩니다. 최대 절전 모드 환경을 수동으로 해제할 수 있습니다.

### 샌드박스 프로그램 만들기 {#creating-sandbox-program}

프로그램 만들기 마법사가 사용자에게 세부 사항을 제출하도록 요청합니다.

샌드박스 프로그램을 만드는 방법에 대한 자세한 내용은 샌드박스 프로그램 [만들기를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-demo-program).

### 샌드박스 환경 만들기 {#creating-sandbox-environments}

샌드박스 프로그램은 프로그램 생성 시 자동 생성 방식으로 개발 환경을 제공합니다. 개발 환경은 기본적으로 작성자 및 게시 계층과 함께 제공됩니다.

프로덕션-스테이지 환경 세트는 사용자가 프로덕션 파이프라인을 설정할 준비가 되면 샌드박스 프로그램에 수동으로 추가할 수 있습니다.

환경을 수동으로 만드는 방법에 대한 자세한 내용은 환경 [추가를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments).

### 샌드박스 환경 삭제  {#deleting-sandbox-environments}

필요한 권한을 가진 사용자는 개발 또는 프로덕션/스테이지 환경/세트를 삭제할 수 있습니다.

환경 삭제 방법에 대한 자세한 내용은 환경 [삭제를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment).


## 동면작업 및 동면제거 샌드박스 환경 {#hibernating-introduction}

샌드박스 프로그램 환경은 활동하지 않은 기간 후에 *최대 절전 모드* 모드로 전환됩니다.

>[!NOTE]
>최대 최대 최대 최대 절전 모드 설정 정규 프로그램 환경은 최대 절전 환경이다.

### 최대 절전 모드 {#hibernation-introduction}

최대 절전 모드 실행 시 자동 또는 수동으로 실행할 수 있습니다. 환경이 겨울잠을 자는 데 최대 몇 분이 걸릴 수 있습니다. 최대 절전 모드 동안 데이터가 유지됩니다.

최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 절전 모드

* **자동** 샌드박스 프로그램 환경은 8시간 동안 활동이 없는 경우 자동으로 동면됩니다. 즉, 작성자 또는 게시 서비스가 요청을 받지 않습니다.

* **수동**: 고객은 샌드박스 프로그램 환경에 수동으로 절전 모드를 적용할 수 있지만, 사용하지 않는 기간이 지나면 최대 절전 모드가 자동으로 수행되므로 그럴 필요는 없습니다.

#### 수동 최대 절전 모드 사용 {#using-manual-hibernation}


개발자 콘솔의 두 화면 중 하나에서 수동 동면을 수행할 수 있습니다.

아래 단계에 따라 프로그램 환경을 수동으로 절전 모드로 전환하십시오.

1. 개발자 콘솔로 이동합니다.
1. 최대 절전 모드 클릭
1. Hibernate를 클릭하여 확인합니다.
1. 최대 절전 모드에 성공하면 다음 화면이 나타납니다.
1. 환경 목록 화면에서 환경 세부 사항 화면에서 환경 링크를 클릭하여 액세스할 수 있는 환경 목록 화면에서 의도한 환경의 행에서 Hibernate 단추를 클릭할 수 있습니다. 그러면 확인 화면이 나타납니다.

### 동면 해제 {#de-hibernation-introduction}

>[!IMPORTANT]
>개발자 콘솔에 대한 액세스는 관리 콘솔의 &quot;클라우드 관리자 - 개발자 역할&quot;에 의해 정의됩니다. 이러한 권한을 통해 사용자는 환경의 절전 모드를 해제할 수 있습니다.

### 동면기 환경 액세스 {#accessing-hibernated-environment}

최대 절전 모드 환경의 작성자 또는 게시 계층에 대해 브라우저 요청이 있을 경우 사용자는 아래 그림과 같이 최대 절전 모드 상태를 설명하는 랜딩 페이지가 나타납니다.

&quot;클라우드 관리자 - 개발자 역할&quot;을 사용하는 사용자는 개발자 콘솔 버튼을 클릭하여 개발자 콘솔에 액세스하고 환경의 최대 절전 모드를 해제할 수 있습니다. 역할 설정에 대한 정보는 Cloud Manager 문서에서 확인할 수 있습니다.

조직의 사용자가 개발자 콘솔 단추를 클릭하여 개발자 콘솔로 이동할 수 없는 경우 &quot;클라우드 관리자 - 개발자 역할&quot;이 표시될 수 있습니다.




## 샌드박스 환경에 대한 AEM 업데이트 {#aem-updates-sandbox}


AEM [버전 업데이트를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates).

사용자는 샌드박스 프로그램의 환경에 AEM 업데이트를 수동으로 적용할 수 있습니다(아래 그림 참조). 표시된 상태가 UPDATE AVAILABLE일 때 이 작업을 수행할 수 있습니다. 환경 카드의 드롭다운 메뉴에서 업데이트 옵션을 사용할 수 있습니다. 환경 화면에서 관리 메뉴에서 선택할 수도 있습니다.

>[!NOTE]
>수동 업데이트 파이프라인을 시작하려면 관심 개발 환경에 배포되는 비프로덕션 파이프라인을 구성해야 합니다.

>[!NOTE]
>Production+Stage 환경으로의 수동 업데이트 파이프라인을 시작하려면 프로덕션 파이프라인을 구성해야 합니다.

>[!NOTE]
>프로덕션 또는 스테이지 환경에 대한 수동 업데이트는 다른 환경에 자동으로 업데이트됩니다. Production+Stage 환경 세트는 동일한 AEM 릴리스에 있어야 합니다.





