---
title: 환경 관리
description: 만들 수 있는 환경 유형과 Cloud Manager 프로젝트용 환경 유형을 만드는 방법에 대해 알아봅니다.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: 7174b398040acbf9b18b5ac2aa20fdba4f98ca78
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 2%

---

# 환경 관리 {#managing-environments}

만들 수 있는 환경 유형과 Cloud Manager 프로젝트용 환경 유형을 만드는 방법에 대해 알아봅니다.

## 환경 유형 {#environment-types}

필수 권한을 가진 사용자는 다음 환경 유형을 만들 수 있습니다(특정 테넌트에 사용할 수 있는 범위 내).

* **프로덕션 및 스테이지** - 프로덕션 및 스테이징 환경은 쌍으로 사용할 수 있으며, 각각 프로덕션 및 테스트 용도로 사용됩니다.

* **개발** - 개발 환경은 개발 및 테스트 목적으로 만들 수 있으며 비프로덕션 파이프라인에만 연결할 수 있습니다.


개별 환경의 기능은 포함 내용에서 활성화된 솔루션에 따라 다릅니다 [프로그램.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

* [Sites](/help/sites-cloud/home.md)
* [에셋](/help/assets/home.md)
* [양식](/help/forms/home.md)
* [스크린](/help/screens-cloud/home.md)

>[!NOTE]
>
>프로덕션 및 스테이징 환경은 쌍으로만 작성됩니다. 스테이징만 만들거나 프로덕션 환경만 만들 수는 없습니다.

## 환경 추가 {#adding-environments}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 환경을 추가할 프로그램을 클릭합니다.

1. 에서 **프로그램 개요** 페이지를 클릭합니다. **환경 추가** on **환경** 환경을 추가할 카드입니다.

   ![환경 카드](assets/no-environments.png)

   * 다음 **환경 추가** 옵션을 사용할 수도 있습니다 **환경** 탭.

      ![환경 탭](assets/environments-tab.png)

   * 다음 **환경 추가** 권한이 없거나 라이선스가 부여된 리소스에 따라 옵션을 사용할 수 없습니다.

1. 에서 **환경 추가** 대화 상자가 표시됩니다.

   * 선택 **환경 유형**.
      * 사용 가능한/사용된 환경 수는 개발 환경 유형 뒤에 괄호로 표시됩니다.
   * 다음을 제공합니다. **환경 이름**.
   * 다음을 제공합니다. **환경 설명**.
   * 선택 **클라우드 지역**.

   ![환경 추가 대화 상자](assets/add-environment2.png)

1. 클릭 **저장** 지정된 환경을 추가하려면

다음 **개요** 이제 화면에 새 환경이 **환경** 카드. 이제 새 환경에 대한 파이프라인을 설정할 수 있습니다.

## 환경 세부 사항 {#viewing-environment}

를 사용할 수 있습니다 **환경** 두 가지 방법으로 환경 세부 사항에 액세스할 수 있는 개요 페이지의 카드입니다.

1. 에서 **개요** 페이지를 클릭하고 **환경** 화면 상단에 있는 탭입니다.

   ![환경 탭](assets/environments-tab2.png)

   * 또는, **모두 표시** 단추 **환경** 바로 이동할 카드 **환경** 탭.

      ![모두 표시 옵션](assets/environment-showall.png)

1. 다음 **환경** 프로그램의 모든 환경을 열고 나열합니다.

   ![환경 탭](assets/environment-view-2.png)

1. 목록에서 환경을 클릭하여 세부 사항을 표시합니다.

   ![환경 세부 사항](assets/environ-preview1.png)

또는 원하는 환경의 줄임표 단추를 클릭한 다음 을 선택합니다 **세부 사항 보기**.

![환경 세부 사항 보기](assets/view-environment-details.png)

>[!NOTE]
>
>다음 **환경** 카드는 세 개의 환경만 나열합니다. 을(를) 클릭합니다. **모두 표시** 이전에 설명한 대로 단추를 사용하여 프로그램의 모든 환경을 볼 수 있습니다.

### 미리 보기 서비스 액세스 {#access-preview-service}

Cloud Manager는 각 AEM as a Cloud Service 환경에 미리 보기 서비스(추가 게시 서비스로 제공)를 제공합니다.

이 서비스를 사용하면 실제 게시 환경에 도달하기 전에 웹 사이트의 최종 경험을 미리 볼 수 있으며 공개적으로 사용할 수 있습니다.

생성 시 미리 보기 서비스에는 기본 IP 허용 목록이 적용되며, 이 서비스에는 레이블이 지정됩니다 `Preview Default [<envId>]`: 미리 보기 서비스로의 모든 트래픽을 차단합니다. 액세스를 활성화하려면 미리 보기 서비스에서 기본 IP 허용 목록의 적용을 적극적으로 취소해야 합니다.

![미리 보기 서비스 및 해당 허용 목록](assets/preview-ip-allow.png)

미리 보기 URL에 액세스하려면 미리 보기 서비스 URL을 팀과 공유하기 전에 필수 권한이 있는 사용자가 다음 옵션 단계를 완료해야 합니다.

1. 적절한 IP 허용 목록을 만들어 미리 보기 서비스에 적용한 후 즉시 적용 취소 `Preview Default [<envId>]` 허용 목록.

   * 문서를 참조하십시오 [IP 허용 목록 적용 및 적용 해제](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) 자세한 내용

1. 업데이트 사용 **IP 허용 목록** 기본 IP를 제거하고 IP를 적절히 추가하는 워크플로우입니다. 을(를) 참조하십시오. [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md) 추가 정보

미리 보기 서비스에 대한 액세스 잠금이 해제되면 미리 보기 서비스 이름 앞에 있는 잠금 아이콘이 더 이상 표시되지 않습니다.

활성화되면 AEM 내의 게시 관리 UI를 사용하여 미리 보기 서비스에 컨텐츠를 게시할 수 있습니다. 문서를 참조하십시오 [컨텐츠 미리 보기](/help/sites-cloud/authoring/fundamentals/previewing-content.md) 자세한 내용

>[!NOTE]
>
>환경이 AEM 버전이어야 합니다. `2021.05.5368.20210529T101701Z` 또는 그 이상 이 작업을 수행하려면 업데이트 파이프라인이 사용자 환경에서 성공적으로 실행되었는지 확인하십시오.

## 환경 업데이트 {#updating-dev-environment}

클라우드 기반의 서비스로서, 프로덕션 프로그램 내의 스테이징 및 프로덕션 환경의 업데이트는 Adobe에서 자동으로 관리합니다.

하지만 샌드박스 프로그램의 환경 및 개발 환경에 대한 업데이트는 프로그램 내에서 관리됩니다. 이러한 환경에서 최신 공개 AEM 버전을 실행하고 있지 않으면 의 상태가 됩니다. **환경** 카드 **개요** 프로그램 화면이 표시됩니다 **업데이트 사용 가능**.

![환경 업데이트 상태](assets/environ-update.png)

### 업데이트 및 파이프라인 {#updates-pipelines}

파이프라인이 유일한 [AEM as a Cloud Service 환경에 코드를 배포합니다.](deploy-code.md) 이러한 이유로 각 파이프라인은 특정 AEM 버전과 연결됩니다.

Cloud Manager에서 파이프라인과 함께 마지막으로 배포한 버전보다 사용 가능한 최신 AEM 버전이 있음을 감지하면 가 표시됩니다 **업데이트 사용 가능** 환경의 상태입니다.

따라서 업데이트 프로세스는 두 단계로 진행됩니다.

1. 최신 AEM 버전으로 파이프라인 업데이트
1. 파이프라인을 실행하여 새로운 버전의 AEM을 환경에 배포

### 환경 업데이트 {#updating-your-environments}

다음 **업데이트** 옵션은 **환경** 환경의 줄임표 단추를 클릭하여 샌드박스 프로그램의 개발 환경 및 환경을 위한 카드입니다.

![환경 카드에서 옵션 업데이트](assets/environ-update2.png)

이 옵션은 **환경** 프로그램의 탭을 클릭한 다음 환경의 줄임표 단추를 선택합니다.

![환경 탭에서 옵션 업데이트](assets/environ-update3.png)

을 사용하는 사용자 **배포 관리자** 역할은 이 옵션을 사용하여 이 환경과 연결된 파이프라인을 최신 AEM 버전으로 업데이트할 수 있습니다.

파이프라인 버전이 최근에 공개적으로 사용 가능한 AEM 버전으로 업데이트되면 연관된 파이프라인을 실행하여 최신 버전을 환경에 배포하라는 메시지가 표시됩니다.

![환경을 업데이트하기 위해 파이프라인을 실행하라는 메시지 표시](assets/update-run-pipeline.png)

다음 **업데이트** 옵션의 동작은 프로그램의 구성 및 현재 상태에 따라 다릅니다.

* 파이프라인이 이미 업데이트된 경우 **업데이트** 옵션을 선택하면 파이프라인을 실행할 것인지 묻는 메시지가 표시됩니다.
* 파이프라인이 이미 업데이트되고 있는 경우 **업데이트** 선택 사항은 업데이트가 이미 실행 중임을 사용자에게 알려줍니다.
* 적절한 파이프라인이 종료되지 않으면 **업데이트** 옵션을 선택하면 사용자에게 하나를 만들라는 메시지가 표시됩니다.

## 개발 환경 삭제 {#deleting-environment}

필수 권한이 있는 사용자는 개발 환경을 삭제할 수 있습니다.

에서 **개요** 프로그램 화면 **환경** 카드를 클릭한 다음 삭제할 개발 환경의 줄임표 단추를 클릭합니다.

![삭제 옵션](assets/environ-delete.png)

삭제 옵션은 **환경** 의 탭 **개요** 프로그램의 창. 환경의 줄임표 단추를 클릭하고 을 선택합니다 **삭제**.

![환경 탭에서 삭제 선택 사항](assets/environ-delete2.png)

>[!NOTE]
>
>* 프로덕션 프로그램에서 만든 프로덕션 및 스테이징 환경은 삭제할 수 없습니다.
>* 샌드박스 프로그램의 프로덕션 및 스테이징 환경을 삭제할 수 있습니다.


## 액세스 관리 {#managing-access}

선택 **액세스 관리** 환경의 줄임표 메뉴에서 **환경** 카드. 작성자 인스턴스로 직접 이동하고 환경에 대한 액세스를 관리할 수 있습니다.

![액세스 관리 옵션](assets/environ-access.png)

## 개발자 콘솔 액세스 {#accessing-developer-console}

선택 **개발자 콘솔** 환경의 줄임표 메뉴에서 **환경** 카드. 이렇게 하면 브라우저에서 새 탭이 열리고 **개발자 콘솔**.

![](assets/environ-devconsole.png)

을 사용하는 사용자만 **개발자** 역할은 **개발자 콘솔**. 하지만 샌드박스 프로그램의 경우 샌드박스 프로그램에 액세스할 수 있는 모든 사용자는 **개발자 콘솔**.

문서를 참조하십시오 [최대 절전 모드 및 최대 절전 모드 해제 샌드박스 환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html#hibernating-introduction) 자세한 내용

이 옵션은 **환경** 의 탭 **개요** 개별 환경의 줄임표 메뉴를 클릭할 때의 창입니다.

## 로컬로 로그인 {#login-locally}

선택 **로컬 로그인** 를 클릭합니다. **환경** Adobe Experience Manager에 로컬로 로그인할 카드입니다.

![로컬로 로그인](assets/environ-login-locally.png)

또한 **환경** 의 탭 **개요** 페이지.

![환경 탭에서 로컬로 로그인](assets/environ-login-locally-2.png)

## 맞춤형 도메인 이름 관리 {#manage-cdn}

사용자 지정 도메인 이름은 게시 및 미리 보기 서비스 모두에 대한 Cloud Manager for Sites 프로그램에서 지원됩니다. 각 Cloud Manager 환경은 최대 250개의 사용자 지정 도메인을 호스팅할 수 있습니다.

사용자 지정 도메인 이름을 구성하려면 **환경** 탭을 클릭하고 환경을 클릭하여 환경 세부 사항을 확인합니다.

![환경 세부 사항](assets/domain-names.png)

환경에 대한 게시 서비스에서 다음 작업을 수행할 수 있습니다.

* [맞춤형 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

* [맞춤형 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

* [사용자 지정 도메인 이름의 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) 또는 [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn).

* [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn)


## IP 허용 목록 관리 {#manage-ip-allow-lists}

IP 허용 목록은 Cloud Manager에서 사이트 프로그램을 위한 작성자, 게시 및 미리 보기 서비스를 지원합니다.

IP 허용 목록을 관리하려면 **환경** 의 탭 **개요** 프로그램의 페이지입니다. 개별 환경을 클릭하여 세부 사항을 관리합니다.

### IP 허용 목록 적용 {#apply-ip-allow-list}

IP 허용 목록을 적용하면 허용 목록 정의에 포함된 모든 IP 범위를 환경의 작성자 또는 게시 서비스와 연결합니다. 의 사용자 **비즈니스 소유자** 또는 **배포 관리자** IP 허용 목록을 적용하려면 역할이 로그인해야 합니다.

환경에 적용하려면 Cloud Manager에 IP 허용 목록이 있어야 합니다. Cloud Manager의 IP 허용 목록에 대한 자세한 내용은 문서를 참조하십시오[Cloud Manager의 IP 허용 목록 소개.](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)

다음 단계에 따라 IP 허용 목록을 적용합니다.

1. 에서 특정 환경으로 이동합니다 **환경** 프로그램의 탭 **개요** 화면으로 이동하여 **IP 허용 목록** 테이블.
1. IP 허용 목록 테이블 상단에 있는 입력 필드를 사용하여 적용할 IP 허용 목록 및 작성자 또는 게시 서비스를 선택합니다.
1. 클릭 **적용** 제출 서류를 확인합니다.

### IP 허용 목록 적용 취소 {#unapply-ip-allow-list}

IP 허용 목록 적용 해제 는 환경의 작성자 또는 게시자 서비스에서 허용 목록 정의에 포함된 모든 IP 범위를 연관시킵니다. 의 사용자 **비즈니스 소유자** 또는 **배포 관리자** IP 허용 목록의 적용을 취소하려면 역할이 로그인되어 있어야 합니다.

IP 허용 목록 적용을 취소하려면 다음 단계를 따르십시오.

1. 에서 특정 환경으로 이동합니다 **환경** 프로그램의 탭 **개요** 화면으로 이동하여 **IP 허용 목록** 테이블.
1. 적용을 취소하려는 IP 허용 목록 규칙이 나열되는 행을 식별합니다.
1. 행 끝에서 줄임표 단추를 선택합니다.
1. 선택 **적용 취소** 제출 서류를 확인합니다.
