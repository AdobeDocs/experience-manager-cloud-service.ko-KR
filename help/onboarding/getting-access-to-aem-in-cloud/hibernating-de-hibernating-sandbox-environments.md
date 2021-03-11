---
title: '동면작업 및 동면제거 샌드박스 환경 '
description: '동면작업 및 동면제거 샌드박스 환경 '
translation-type: tm+mt
source-git-commit: 5a4353cb31337882a1c13b0ed830ea64f617181a
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---


# 최대 절전 모드 해제 및 최대 절전 모드 해제 환경 {#hibernating-introduction}

샌드박스 프로그램 환경은 특정 기간 동안 활동이 감지되지 않는 경우 *최대 절전 모드*&#x200B;를 입력합니다.

>[!NOTE]
>최대 절전 모드는 샌드박스 프로그램 환경에만 적용됩니다. 프로덕션 프로그램 환경은 최대 절전 모드를 사용하지 않습니다.

## 최대 절전 모드 {#hibernation-introduction}

최대 절전 모드를 사용하면 자동으로 또는 수동으로 실행할 수 있습니다. 샌드박스 프로그램 환경에서 *최대 절전 모드*&#x200B;에 들어가는 데 최대 몇 분이 걸릴 수 있습니다. 최대 절전 모드 동안 데이터가 유지됩니다.

최대 최대 최대 최대 최대 최대 최대 최대 최대 최대 절전 모드:

* **AutomaticSandbox**  프로그램 환경은 8시간 동안 활동하지 않은 후 자동으로 동면됩니다. 즉, 작성자 및 게시 서비스가 요청을 받지 않습니다.

* **수동**:사용자는 샌드박스 프로그램 환경에 수동으로 절전 모드를 적용할 수 있지만, 일정 기간(8시간) 동안 사용하지 않으면 자동으로 최대 절전 모드가 수행되므로 그럴 필요가 없습니다.

>[!CAUTION]
>최신 릴리스에서는 Cloud Manager에서 바로 개발자 콘솔에 연결할 수 있지만 샌드박스 프로그램 환경의 최대 절전 모드를 제공하는 옵션이 제공되지 않습니다. 해결 방법은 Developer Console에서 한 번 다음 패턴을 url `#release-cm-p1234-e5678 where 1234` 1234의 끝에 추가합니다. 이 패턴은 *프로그램 ID* 이고 5678은 *환경 ID*&#x200B;입니다.

### 수동 최대 절전 모드 사용 {#using-manual-hibernation}

다음 두 가지 방법으로 개발자 콘솔에서 샌드박스 프로그램의 최대 절전 모드를 수동으로 실행할 수 있습니다.

* 환경 세부 정보 화면
* 환경 목록 화면

>[!NOTE]
>Cloud Manager의 모든 사용자는 샌드박스 프로그램의 개발자 콘솔에 액세스할 수 있습니다.

아래의 단계에 따라 샌드박스 프로그램 환경을 수동으로 최대 절전 모드로 전환하십시오.

1. **개발자 콘솔**로 이동합니다.
**환경** 카드의 **개발자 콘솔**&#x200B;에 액세스하는 방법에 대해 알아보려면 [개발자 콘솔 액세스](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console)을 참조하십시오.
   >[!IMPORTANT]
   >Cloud Manager에서 바로 **개발자 콘솔**&#x200B;에 연결해도 샌드박스 프로그램 환경에 최대 절전 모드를 적용할 수 있는 옵션이 제공되지 않습니다. 해결 방법은 Developer Console에서 한 번 다음 패턴을 url `#release-cm-p1234-e5678 where 1234` 1234의 끝에 추가합니다. 이 패턴은 *프로그램 ID* 이고 5678은 *환경 ID*&#x200B;입니다.

1. 아래 그림과 같이 **Hibernate**&#x200B;를 클릭합니다.

   ![](assets/hibernate-1.png)

   또는,

   아래 그림과 같이 왼쪽 위에 있는 **환경** 링크를 클릭하여 환경 목록을 확인한 다음 **Hibernate**&#x200B;를 클릭합니다.

   ![](assets/hibernate-1b.png)

1. **Hibernate**&#x200B;를 클릭하여 단계를 확인합니다.

   ![](assets/hibernate-2.png)

1. 최대 절전 모드에 성공하면 환경의 최대 절전 모드 완료 알림이 **개발자 콘솔** 화면에 표시됩니다.

   ![](assets/hibernate-4.png)


## 최대 절전 모드 해제 {#de-hibernation-introduction}

1. **개발자 콘솔**로 이동합니다.
**환경** 카드의 **개발자 콘솔**&#x200B;에 액세스하는 방법에 대해 알아보려면 [개발자 콘솔 액세스](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console)을 참조하십시오.

   >[!IMPORTANT]
   >Cloud Manager에서 바로 **개발자 콘솔**&#x200B;에 연결해도 샌드박스 프로그램 환경의 최대 절전 모드를 해제할 수 있는 옵션이 제공되지 않습니다. 해결 방법은 Developer Console에서 한 번 다음 패턴을 url `#release-cm-p1234-e5678 where 1234` 1234의 끝에 추가합니다. 이 패턴은 *프로그램 ID* 이고 5678은 *환경 ID*&#x200B;입니다.

   >[!NOTE]
   >또는 이미 동면된 환경의 작성자 또는 게시 서비스에 액세스하려고 할 때 **개발자 콘솔**&#x200B;로 이동하여 절전 모드를 해제할 수 있습니다.이 경우, 랜딩 페이지가 개발자 콘솔에 대한 링크와 함께 표시됩니다. 아래의 동면자 환경 액세스 섹션을 참조하십시오.

   >[!IMPORTANT]
   >개발자 콘솔에 대한 액세스는 **Admin Console**&#x200B;의 **클라우드 관리자 - 개발자 역할**&#x200B;에 의해 정의됩니다. 개발자 역할 권한이 있는 사용자는 샌드박스 프로그램 환경에 절전 모드를 해제할 수 있습니다.

1. 아래 그림과 같이 **최대 절전 모드 해제**&#x200B;를 클릭합니다.

   ![](assets/de-hibernation-img1.png)

   또는,

   왼쪽 위에 있는 **환경** 링크를 클릭하여 환경 목록을 확인한 다음 아래 그림과 같이 **최대 절전 모드 해제**&#x200B;를 클릭합니다.

   ![](assets/de-hibernate-1b.png)


1. **De Hibernate**&#x200B;를 클릭하여 단계를 확인합니다.

   ![](assets/de-hibernation-img2.png)

1. 최대 절전 모드 해제 프로세스가 시작되었다는 알림을 받게 되고 진행 상태가 업데이트됩니다.

   ![](assets/de-hibernation-img3.png)

1. 프로세스가 완료되면 샌드박스 프로그램 환경이 다시 활성화됩니다.

   ![](assets/de-hibernation-img4.png)

### 최대 절전 모드 해제 권한 {#permissions-de-hibernate}

Cloud Service으로 AEM에 액세스할 수 있는 제품 프로필을 보유한 모든 사용자는 **개발자 콘솔**&#x200B;에 액세스하여 환경의 최대 절전 모드를 해제할 수 있어야 합니다.

## 최대 절전 모드 실행 환경 {#accessing-hibernated-environment} 액세스

브라우저에서 동면하는 환경의 작성자 또는 게시 계층에 대해 요청을 할 때 사용자는 아래 그림과 같이 동면하는 환경의 상태를 설명하는 랜딩 페이지가 표시됩니다.

![](assets/de-hibernation-img5.png)

## 중요 고려 사항 {#important-considerations}

동면기 및 동면해제 환경과 관련하여 고려해야 할 주요 사항은 거의 없습니다.

* 사용자는 파이프라인을 사용하여 사용자 정의 코드를 동면 환경에 배포할 수 있습니다. 이 환경은 동면기를 유지할 것이며 새로운 코드는 일단 동면기를 제거한 후에 환경에 나타날 것이다.

* AEM 업그레이드는 최대 절전 모드 상태에 적용할 수 있으며 고객이 Cloud Manager에서 수동으로 시작할 수 있습니다. 이 환경은 동면기를 유지할 것이며 새로운 릴리스는 일단 동면기를 제거한 후에 환경에 나타날 것이다.

>[!NOTE]
>현재 Cloud Manager는 환경에서 동면하는 상태를 나타내지 않습니다.

## 샌드박스 환경에 대한 AEM 업데이트 {#aem-updates-sandbox}

자세한 내용은 [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md)를 참조하십시오.

사용자는 샌드박스 프로그램의 환경에 AEM 업데이트를 수동으로 적용할 수 있습니다.

환경을 업데이트하는 방법에 대해 알아보려면 [환경 업데이트](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment)를 참조하십시오.

>[!NOTE]
>* 수동 업데이트는 타깃팅된 환경에 제대로 구성된 파이프라인이 있는 경우에만 실행할 수 있습니다.
>* *Production* 또는 *Stage* 환경에 대한 수동 업데이트는 다른 내용을 자동으로 업데이트합니다. Production+Stage 환경 설정은 동일한 AEM 릴리스에 있어야 합니다.






