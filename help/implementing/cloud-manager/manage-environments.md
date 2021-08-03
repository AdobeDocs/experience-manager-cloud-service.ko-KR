---
title: 환경 관리 - Cloud Service
description: 환경 관리 - Cloud Service
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: 529fbdcba9fc4c1432beef1b63ff89079a900224
workflow-type: tm+mt
source-wordcount: '1618'
ht-degree: 1%

---

# 환경 관리 {#manage-environments}

다음 섹션에서는 사용자가 만들 수 있는 환경 유형과 사용자가 환경을 만드는 방법에 대해 설명합니다.

## 환경 유형 {#environment-types}

필수 권한을 가진 사용자는 다음 환경 유형을 만들 수 있습니다(특정 테넌트에 사용할 수 있는 범위 내).

* **프로덕션 및 스테이지 환경**: 프로덕션과 스테이지는 듀오로 제공되며 테스트 및 프로덕션 용도로 사용됩니다.

* **개발**: 개발 환경은 개발 및 테스트 목적으로 만들 수 있으며 비프로덕션 파이프라인에만 연결됩니다.

   >[!NOTE]
   >샌드박스 프로그램에서 자동으로 만들어지는 개발 환경은 사이트 및 자산 솔루션을 포함하도록 구성됩니다.

   다음 표에는 환경 유형 및 해당 속성이 요약되어 있습니다.

   | 이름 | 작성 계층 | 게시 계층 | 사용자가 만들 수 있음 | 사용자가 삭제할 수 있음 | 환경과 연결할 수 있는 파이프라인 |
   |--- |--- |--- |--- |---|---|
   | 프로덕션 | 예 | 예 사이트가 포함된 경우 | 예 | 아니오 | 프로덕션 파이프라인 |
   | 단계 | 예 | 예 사이트가 포함된 경우 | 예 | 아니오 | 프로덕션 파이프라인 |
   | 개발 | 예 | 예 사이트가 포함된 경우 | 예 | 예 | 비프로덕션 파이프라인 |

   >[!NOTE]
   >프로덕션과 스테이지는 듀오로 제공되며 테스트 및 프로덕션 용도로 사용됩니다.  사용자는 스테이지나 프로덕션 환경만 만들 수 없습니다.

## 환경 추가 {#adding-environments}

1. **환경 추가**&#x200B;를 클릭하여 환경을 추가합니다. 이 단추는 **환경** 화면에서 액세스할 수 있습니다.
   ![](assets/environments-tab.png)

   프로그램에 환경이 없는 경우 **환경 추가** 옵션도 **환경** 카드에서 사용할 수 있습니다.

   ![](assets/no-environments.png)

   >[!NOTE]
   >**환경 추가** 옵션은 권한 부족 또는 계약을 체결할 수 있는 항목에 따라 비활성화됩니다.

1. **환경 추가** 대화 상자가 나타납니다.사용자는 **환경 유형** 및 **환경 이름** 및 **환경 설명** 등의 세부 정보를 제출해야 합니다(특정 테넌트에 사용 가능한 범위 내에서 환경을 만드는 사용자의 목표에 따라 다름).

   ![](assets/add-environment2.png)

   >[!NOTE]
   >환경을 만들 때 Adobe I/O에 하나 이상의 *통합*&#x200B;이 만들어집니다. 이는 Adobe I/O 콘솔에 액세스할 수 있는 고객 사용자가 볼 수 있으며 삭제할 수 없습니다. 이는 Adobe I/O 콘솔의 설명에서 나타나지 않습니다.

   ![](assets/add-environment-image1.png)

1. **저장** 을 클릭하여 채워진 기준이 있는 환경을 추가합니다.  이제 *개요* 화면에는 파이프라인을 설정할 수 있는 카드가 표시됩니다.

   >[!NOTE]
   >비프로덕션 파이프라인을 아직 설정하지 않은 경우 *개요* 화면에는 비프로덕션 파이프라인을 생성할 수 있는 카드가 표시됩니다.

## 환경 세부 사항 {#viewing-environment}

개요 페이지의 **환경** 카드는 최대 3개의 환경을 나열합니다.

1. **모두 표시** 단추를 선택하여 **환경** 요약 페이지로 이동하여 전체 환경 목록이 있는 테이블을 봅니다.

   ![](/help/implementing/cloud-manager/assets/environment-showall.png)

1. **환경** 페이지에는 모든 기존 환경의 목록이 표시됩니다.

   ![](assets/environment-view-2.png)

1. 목록에서 환경을 선택하여 환경 세부 사항을 확인합니다.

   ![](assets/environ-preview1.png)


### 미리 보기 서비스 액세스 {#access-preview-service}

미리 보기 서비스 기능은 Cloud Manager를 통해 각 AEM as a Cloud Service 환경으로 추가 미리 보기(게시) 서비스를 제공합니다.

웹 사이트가 게시 환경에 도달하기 전에 웹 사이트의 최종 경험을 미리 보고 공개적으로 사용할 수 있습니다. 미리 보기 서비스를 보고 사용하기 전에 다음 몇 가지 포인터를 볼 수 있습니다.

1. **AEM 버전**: 환경은 AEM 버전  `2021.05.5368.20210529T101701Z` 이상이어야 합니다. 이 작업을 수행하려면 업데이트 파이프라인이 사용자 환경에서 성공적으로 실행되었는지 확인하십시오.

1. **기본 IP 허용 목록 잠금**: 생성 시 미리 보기 서비스에는 기본 IP 허용 목록이 적용되며, 여기에 레이블이  `Preview Default [Env ID]`지정됩니다.

   >[!NOTE]
   >처음 생성 시 액세스 권한을 활성화하려면 환경의 미리 보기 서비스에서 기본 IP 허용 목록을 적극적으로 적용 취소해야 합니다.

   *미리 보기 서비스에 대한 잠금을 해제하고 원하는 액세스를 제공하려면 필수 권한을 가진 사용자가 다음 중 하나를 수행해야 합니다.*

   * 적절한 IP 허용 목록을 만들어 미리 보기 서비스에 적용합니다. 미리 보기 서비스에서 `Preview Default [Env ID] IP Allow List`을(를) 적용 취소하여 즉시 이 작업을 수행합니다. 자세한 내용은 [IP 허용 목록 적용 취소](/help/implementing/cloud-manager/ip-allow-lists/unapply-ip-allow-list.md)를 참조하십시오.

      *또는*,

   * IP 허용 목록 업데이트 워크플로우를 사용하여 기본 IP를 제거하고 IP를 적절하게 추가합니다. 자세한 내용은 [IP 허용 목록 보기 및 업데이트](/help/implementing/cloud-manager/ip-allow-lists/view-update-ip-allow-list.md)를 참조하십시오.

      >[!NOTE]
      >팀의 적절한 구성원이 미리 보기 URL에 액세스할 수 있도록 미리 보기 서비스 URL을 팀과 공유하기 전에 위의 단계를 수행해야 합니다.

      미리 보기 서비스에 대한 액세스 권한이 해제되면 잠금 아이콘(아래 그림에 표시된 대로)이 더 이상 표시되지 않습니다.

      ![](/help/implementing/cloud-manager/assets/preview-service1.png)

1. **미리 보기에 컨텐츠 게시**: AEM 내의 게시 관리 UI를 사용하여 미리 보기 서비스에 컨텐츠를 게시할 수 있습니다. 자세한 내용은 [컨텐츠 미리 보기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/fundamentals/previewing-content.html?lang=en)를 참조하십시오.

## 환경 업데이트 {#updating-dev-environment}

스테이지 및 프로덕션 환경의 업데이트는 Adobe에 의해 자동으로 관리됩니다.

개발 환경에 대한 업데이트는 프로그램 사용자가 관리합니다. 환경에서 최근에 공개적으로 사용 가능한 AEM 릴리스를 실행하고 있지 않으면 홈 화면의 환경 카드의 상태에 **UPDATE AVAILABLE**&#x200B;이 표시됩니다.

![](assets/environ-update.png)


**업데이트** 옵션은 **환경** 카드에서 사용할 수 있습니다.
이 옵션은 **환경** 카드에서 **세부 정보**&#x200B;를 클릭하면 사용할 수도 있습니다. **환경** 페이지가 열리고 개발 환경을 선택하면 **...**&#x200B;을(를) 선택하고 **업데이트**&#x200B;를 선택합니다.

![](assets/environ-update2.png)

이 옵션을 선택하면 배포 관리자가 이 환경과 연결된 파이프라인을 최신 릴리스로 업데이트한 다음 파이프라인을 실행할 수 있습니다.

파이프라인이 이미 업데이트된 경우 파이프라인을 실행하라는 메시지가 표시됩니다.

## 환경 삭제 {#deleting-environment}

필수 권한이 있는 사용자는 개발 환경을 삭제할 수 있습니다.

**삭제** 옵션은 **환경** 카드의 드롭다운 메뉴에서 사용할 수 있습니다. **클릭..삭제할 개발 환경의**

![](assets/environ-delete.png)

**환경** 카드에서 **세부 정보**&#x200B;를 클릭하면 삭제 옵션도 사용할 수 있습니다. **환경** 페이지가 열리고 개발 환경을 선택하면 **...**&#x200B;을(를) 선택하고 **삭제**&#x200B;를 선택합니다.

![](assets/environ-delete2.png)


>[!NOTE]
>이 기능은 프로덕션 목적으로 설정된 프로덕션 프로그램의 프로덕션/스테이지 환경 설정에는 사용할 수 없습니다. 하지만 이 기능은 샌드박스 프로그램의 프로덕션/스테이지 환경에 사용할 수 있습니다.

## 액세스 관리 {#managing-access}

**환경** 카드의 드롭다운 메뉴에서 **액세스 관리**&#x200B;를 선택합니다. 작성자 인스턴스로 직접 이동하고 환경에 대한 액세스를 관리할 수 있습니다.

자세한 내용은 [작성자 인스턴스에 대한 액세스 관리](/help/onboarding/what-is-required/accessing-aem-instance.md) 를 참조하십시오.

![](assets/environ-access.png)


## 개발자 콘솔 액세스 {#accessing-developer-console}

**환경** 카드의 드롭다운 메뉴에서 **개발자 콘솔**&#x200B;을 선택합니다. 이렇게 하면 브라우저에서 **개발자 콘솔**&#x200B;에 대한 로그인 페이지가 열립니다.

개발자 역할의 사용자만 **개발자 콘솔**&#x200B;에 액세스할 수 있습니다. 단, Cloud Manager 샌드박스 프로그램에 액세스할 수 있는 모든 사용자가 **개발자 콘솔**&#x200B;에 액세스할 수 있는 샌드박스 프로그램에 대한 예외입니다.

자세한 내용은 [최대 절전 모드 및 최대 절전 모드 해제 샌드박스 환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html#hibernating-introduction)을 참조하십시오.


![](assets/environ-devconsole.png)

이 옵션은 **환경** 카드에서 **세부 정보**&#x200B;를 클릭하면 사용할 수도 있습니다. **환경** 페이지가 열리고 환경을 선택하면 **..** 를 선택하고 **개발자 콘솔**&#x200B;을 선택합니다.

## 로컬로 로그인 {#login-locally}

**환경** 카드의 드롭다운 메뉴에서 **로컬 로그인**&#x200B;을 선택하여 Adobe Experience Manager에 로컬로 로그인합니다.

![](assets/environ-login-locally.png)

또한 **환경** 요약 페이지에서 로컬로 로그인할 수 있습니다.

![](assets/environ-login-locally-2.png)


## 사용자 지정 도메인 이름 관리 {#manage-cdn}

환경 요약 페이지에서 **환경** 세부 정보 페이지로 이동합니다.

>[!NOTE]
>이제 사용자 지정 도메인 이름이 게시 및 미리 보기 서비스 모두에 대한 사이트 프로그램의 Cloud Manager에서 지원됩니다. 각 Cloud Manager 환경은 환경당 최대 250개의 사용자 지정 도메인을 호스팅할 수 있습니다.

아래 설명된 대로 사용자 환경의 게시 서비스에서 다음 작업을 수행할 수 있습니다.

1. [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

1. [사용자 지정 도메인 이름 보기 및 업데이트](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md)

1. [사용자 지정 도메인 이름 삭제](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md)

1. [사용자 지정 도메인 이름 ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) 또는  [SSL 인증서 상태 확인](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn).

1. [IP 허용 목록 상태 확인](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn)


## IP 허용 목록 관리 {#manage-ip-allow-lists}

환경 요약 페이지에서 환경 세부 사항 페이지로 이동합니다. 여기에 있는 환경에 대한 게시 및/또는 작성 서비스에서 다음 작업을 수행할 수 있습니다.

>[!NOTE]
>이제 IP 허용 목록 기능은 Cloud Manager for Author, Publish 및 Preview Services(사이트 프로그램에서 사용 가능)에서 지원됩니다.

### IP 허용 목록 적용 {#apply-ip-allow-list}

IP 허용 목록을 적용하는 것은 허용 목록 정의에 포함된 모든 IP 범위를 환경의 작성자 또는 게시 서비스와 연결하는 프로세스입니다. IP 허용 목록을 적용하려면 비즈니스 소유자 또는 배포 관리자 역할의 사용자가 로그인해야 합니다.

>[!NOTE]
>환경 서비스에 적용하려면 Cloud Manager에 IP 허용 목록이 있어야 합니다. Cloud Manager의 IP 허용 목록에 대한 자세한 내용은 [Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)의 IP 허용 목록 소개으로 이동하십시오.

IP 허용 목록을 적용하려면 아래 단계를 따르십시오.

1. **환경** 세부 정보 페이지에서 특정 환경으로 이동하고 **IP 허용 목록** 테이블로 이동합니다.
1. IP 허용 목록 테이블 상단에 있는 입력 필드를 사용하여 적용할 IP 허용 목록 및 작성자 또는 게시 서비스를 선택합니다.
1. **적용**&#x200B;을 클릭하고 제출을 확인합니다.

### IP 허용 목록 적용 취소 {#unapply-ip-allow-list}

IP 허용 목록 적용 취소는 허용 목록 정의에 포함된 모든 IP 범위가 환경의 작성자 또는 게시자 서비스와 연관되지 않는 프로세스입니다. IP 허용 목록을 적용 해제하려면 비즈니스 소유자 또는 배포 관리자 역할의 사용자가 로그인해야 합니다.

IP 허용 목록을 적용하려면 아래 단계를 따르십시오.

1. 환경 화면에서 특정 **환경** 세부 정보 페이지로 이동하고 **IP 허용 목록** 테이블로 이동합니다.
1. 적용하지 않을 IP 허용 목록 규칙이 나열된 행을 식별합니다.
1. **선택...행의 맨 오른쪽 끝에 있는** 메뉴
1. **적용 취소** 옵션을 선택하고 제출을 확인합니다.
