---
title: 환경 관리
description: 만들 수 있는 환경 유형과 Cloud Manager 프로젝트용으로 환경을 만드는 방법에 대해 알아봅니다.
exl-id: 93fb216c-c4a7-481a-bad6-057ab3ef09d3
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '2325'
ht-degree: 93%

---


# 환경 관리 {#managing-environments}

만들 수 있는 환경 유형과 Cloud Manager 프로젝트용으로 환경을 만드는 방법에 대해 알아봅니다.

## 환경 유형 {#environment-types}

필수 권한이 있는 사용자는 특정 테넌트가 사용할 수 있는 범위 내에서 다음과 같은 환경 유형을 만들 수 있습니다.

* **프로덕션 + 스테이징** - 프로덕션 환경 및 스테이징 환경은 쌍으로 구성되며 각각 프로덕션 및 테스트 목적으로 사용됩니다.

* **개발** - 개발 환경은 개발 목적뿐만 아니라 테스트 목적으로도 만들 수 있으며 비프로덕션 파이프라인에만 연결할 수 있습니다.

* **신속한 개발** - 개발자는 신속한 개발 환경(RDE)을 통해 변경 사항을 신속하게 배포하고 검토할 수 있으므로 로컬 개발 환경에서 작동하는 것으로 입증된 기능을 테스트하는 데 필요한 시간을 최소화할 수 있습니다. RDE 사용 방법에 대한 자세한 내용은 [신속한 개발 환경 설명서](/help/implementing/developing/introduction/rapid-development-environments.md)를 참조하십시오.

개별 환경의 기능은 환경의 [프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)에서 활성화된 솔루션에 따라 다릅니다.

* [Sites](/help/sites-cloud/home.md)
* [Assets](/help/assets/home.md)
* [Forms](/help/forms/home.md)
* [Screens](/help/screens-cloud/home.md)

>[!NOTE]
>
>프로덕션 및 스테이징 환경은 쌍으로만 생성됩니다. 스테이징만 만들거나 프로덕션 환경만 만들 수는 없습니다.

## 환경 추가 {#adding-environments}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 환경을 추가할 프로그램을 클릭합니다.

1. **프로그램 개요** 페이지에서 **환경** 카드의 **환경 추가**&#x200B;를 클릭하여 환경을 추가합니다.

   ![환경 카드](assets/no-environments.png)

   * **환경 추가** 옵션은 **환경** 탭에서도 사용할 수 있습니다.

     ![환경 탭](assets/environments-tab.png)

   * 사용 권한이 없거나 사용 허가된 리소스에 따라 **환경 추가** 옵션이 비활성화될 수 있습니다.

1. **환경 추가** 대화 상자가 나타나면 다음 작업을 수행하십시오.

   * [**환경 유형**&#x200B;을 선택합니다.](#environment-types)
      * 사용 가능한/사용된 환경의 수가 환경 유형 이름 뒤의 괄호 안에 표시됩니다.
   * 환경 **이름**&#x200B;을 제공합니다.
   * 환경 **설명**&#x200B;을 제공합니다.
   * **프로덕션 + 스테이징** 환경을 추가하는 경우 프로덕션 환경과 스테이징 환경 모두에 대해 환경 이름 및 설명을 제공해야 합니다.
   * 드롭다운에서 **기본 지역**&#x200B;을 선택합니다.
      * 만든 후에는 이 정보를 변경할 수 없습니다.
      * 사용 가능한 권한에 따라 [여러 지역](#multiple-regions)을 구성할 수 있습니다.

   ![환경 추가 대화 상자](assets/add-environment2.png)

1. **저장**&#x200B;을 클릭하여 지정된 환경을 추가합니다.

이제 **개요** 화면의 **환경** 카드에 새 환경이 표시됩니다. 이제 새 환경에 대한 파이프라인을 설정할 수 있습니다.

## 여러 게시 지역 {#multiple-regions}

**비즈니스 소유자** 역할을 가진 사용자는 기본 지역 외에 최대 3개의 추가 게시 지역을 포함하도록 프로덕션 및 스테이징 환경을 구성할 수 있습니다. 추가 게시 지역은 가용성을 높일 수 있습니다. 자세한 내용은 [추가 게시 지역 설명서](/help/operations/additional-publish-regions.md)를 참조하십시오.

>[!TIP]
>
>[Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/api-usage/creating-programs-and-environments/#creating-aem-cloud-service-environments)를 사용하여 사용 가능한 지역의 현재 목록을 쿼리할 수 있습니다.

### 새 환경에 여러 게시 지역 추가 {#add-regions}

새 환경을 추가할 때 기본 지역 외에 추가 지역 구성을 선택할 수 있습니다.

1. **기본 지역**&#x200B;을 선택합니다.
   * 환경이 생성된 후에는 이 정보를 변경할 수 없습니다.
1. **추가 게시 지역 추가** 옵션을 선택하면 새 **추가 게시 지역** 드롭다운이 표시됩니다.
1. **추가 게시 지역** 드롭다운에서 추가 지역을 선택합니다.
1. 드롭다운 아래에 선택한 지역을 추가하여 선택 사항을 표시합니다.
   * 선택한 지역 옆 x를 탭하거나 클릭하여 지역 선택을 해제합니다.
1. **추가 게시 지역** 드롭다운에서 다른 지역을 선택하여 다른 지역을 추가합니다.
1. 환경을 만들 준비가 되면 **저장**&#x200B;을 탭하거나 클릭합니다.

![여러 지역 선택](assets/select-multiple-regions.png)

선택한 지역은 프로덕션 환경과 스테이징 환경 모두에 적용됩니다.

추가 지역을 지정하지 않으면 [환경을 만든 후 나중에 지정할 수 있습니다.](#edit-regions)

프로그램의 [고급 네트워킹](/help/security/configuring-advanced-networking.md)을 프로비저닝하려면 Cloud Manager API를 사용하여 추가 게시 지역을 환경에 추가하기 전에 이 작업을 수행하는 것이 좋습니다. 그렇지 않은 경우 추가 게시 지역의 트래픽이 기본 지역의 프록시로 이동합니다.

### 여러 게시 지역 편집 {#edit-regions}

처음에 추가 지역을 지정하지 않으면 환경을 만들고 필요한 권한이 있는 경우 지정할 수 있습니다.

추가 게시 지역을 제거할 수도 있습니다. 단, 한 번의 트랜잭션에서만 지역을 추가 또는 제거할 수 있습니다. 하나의 지역을 추가하고 하나의 지역을 제거해야 하는 경우 먼저 지역을 추가하고 변경 사항을 저장한 다음 제거합니다(또는 그 반대).

1. 내 프로그램의 프로그램 개요 콘솔에서 프로덕션 환경의 줄임표 버튼을 클릭하고 메뉴에서 **편집**&#x200B;을 선택합니다.

   ![환경 편집](assets/select-edit-environment.png)

1. **프로덕션 환경 편집** 대화 상자에서 필요에 따라 추가 게시 지역을 변경합니다.
   * **추가 게시 지역** 드롭다운을 사용하여 추가 지역을 선택합니다.
   * 선택한 추가 지역 옆 x를 클릭하여 지역 선택을 해제합니다.

   ![환경 편집](assets/edit-environment.png)

1. **저장**&#x200B;을 탭하거나 클릭하여 변경 내용을 저장합니다.

프로덕션 환경에 대한 변경 사항은 프로덕션 환경과 스테이징 환경 모두에 적용됩니다. 여러 게시 지역에 대한 변경 사항은 프로덕션 환경에서만 편집할 수 있습니다.

프로그램의 [고급 네트워킹](/help/security/configuring-advanced-networking.md)을 프로비저닝하려면 추가 게시 지역을 환경에 추가하기 전에 이 작업을 수행하는 것이 좋습니다. 그렇지 않은 경우 추가 게시 지역의 트래픽이 기본 지역의 프록시로 이동합니다.

## 환경 세부 정보 {#viewing-environment}

개요 페이지의 **환경** 카드를 사용하여 두 가지 방법으로 환경 세부 정보에 액세스할 수 있습니다.

1. **개요** 페이지에서 화면 상단의 **환경** 탭을 클릭합니다.

   ![환경 탭](assets/environments-tab2.png)

   * 또는 **환경** 카드에서 **모두 표시** 버튼을 클릭하여 **환경** 탭으로 직접 이동합니다.

     ![모두 표시 옵션](assets/environment-showall.png)

1. **환경**&#x200B;이 열리고 프로그램에 대한 모든 환경이 나열됩니다.

   ![환경 탭](assets/environment-view-2.png)

1. 목록에서 환경을 클릭하여 세부 정보를 표시합니다.

   ![환경 세부 정보](assets/environ-preview1.png)

또는 원하는 환경의 줄임표 버튼을 클릭한 다음 **세부 정보 보기**&#x200B;를 선택합니다.

![환경 세부 정보 보기](assets/view-environment-details.png)

>[!NOTE]
>
>**환경** 카드에는 세 가지 환경만 나열됩니다. 프로그램의 모든 환경을 보려면 앞에서 설명한 대로 **모두 표시** 버튼을 클릭합니다.

### 미리보기 서비스 액세스 {#access-preview-service}

Cloud Manager는 AEM as a Cloud Service 환경에 미리보기 서비스(추가 게시 서비스로 제공)를 제공합니다.

서비스를 사용하면 웹 사이트의 최종 경험이 실제 게시 환경에 도달하고 공개적으로 사용할 수 있게 되기 전에 이를 미리 볼 수 있습니다.

생성 시 미리보기 서비스에는 `Preview Default [<envId>]`이라는 레이블이 지정된 기본 IP 허용 목록이 적용되는데, 이는 미리보기 서비스에 대한 모든 트래픽을 차단합니다. 액세스를 활성화하려면 미리보기 서비스에서 기본 IP 허용 목록을 적용 취소해야 합니다.

![미리보기 서비스 및 해당 허용 목록](assets/preview-ip-allow.png)

필요한 권한이 있는 사용자는 미리보기 서비스 URL을 공유하기 전에 다음 단계를 완료하여 해당 URL에 액세스할 수 있어야 합니다.

1. 적절한 IP 허용 목록을 만들어 미리보기 서비스에 적용하고 `Preview Default [<envId>]` 허용 목록을 즉시 적용 취소합니다.

   * 자세한 내용은 [IP 허용 목록 적용 및 적용 취소](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) 문서를 참조하십시오.

1. **IP 허용 목록** 업데이트 워크플로를 사용하여 기본 IP를 제거하고 적절하게 IP를 추가합니다. 자세한 내용은 [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md)를 참조하십시오.

미리보기 서비스에 대한 액세스가 잠금 해제되면 미리보기 서비스 이름 앞의 잠금 아이콘이 더 이상 표시되지 않습니다.

활성화되면 AEM 내 게시 관리 UI를 사용하여 미리보기 서비스에 콘텐츠를 게시할 수 있습니다. 자세한 내용은 [콘텐츠 미리보기](/help/sites-cloud/authoring/fundamentals/previewing-content.md) 문서를 참조하십시오.

>[!NOTE]
>
>환경이 AEM 버전 `2021.05.5368.20210529T101701Z` 이상이어야 미리보기 서비스를 사용할 수 있습니다. 이를 수행하려면 업데이트 파이프라인이 환경에서 성공적으로 실행되었는지 확인하십시오.

## 환경 업데이트 {#updating-dev-environment}

클라우드 네이티브 서비스인 프로덕션 프로그램 내의 스테이징 및 프로덕션 환경 업데이트는 Adobe에서 자동으로 관리합니다.

단, 샌드박스 프로그램의 환경뿐만 아니라 개발 환경의 업데이트도 프로그램 내에서 관리됩니다. 이러한 환경에서 공개적으로 사용 가능한 최신 AEM 버전을 실행하지 않는 경우 프로그램의 **개요** 화면에 있는 **환경** 카드의 상태에 **업데이트 사용 가능**&#x200B;이 표시됩니다.

![환경 업데이트 상태](assets/environ-update.png)

### 업데이트 및 파이프라인 {#updates-pipelines}

파이프라인은 [AEM as a Cloud Service 환경에 코드를 배포](deploy-code.md)하는 유일한 방법입니다. 이러한 이유로 각 파이프라인은 특정 AEM 버전과 연결됩니다.

Cloud Manager는 파이프라인과 함께 마지막으로 배포된 버전보다 최신 버전의 AEM이 있음을 감지하면 환경에 대해 **업데이트 사용 가능** 상태를 표시합니다.

따라서 업데이트 프로세스는 2단계 프로세스입니다.

1. 최신 AEM 버전으로 파이프라인 업데이트
1. 파이프라인을 실행하여 환경에 AEM의 새 버전 배포

### 환경 업데이트 {#updating-your-environments}

**업데이트** 옵션은 환경의 줄임표 버튼을 클릭하여 표시되는 개발 환경 및 샌드박스 프로그램의 환경에 대한 **환경** 카드에서 사용할 수 있습니다.

![환경 카드의 업데이트 옵션](assets/environ-update2.png)

이 옵션은 프로그램의 **환경** 탭을 클릭한 다음 환경의 줄임표 버튼을 선택하여 사용할 수도 있습니다.

![환경 탭의 업데이트 옵션](assets/environ-update3.png)

**배포 관리자** 역할을 가진 사용자는 이 옵션을 사용하여 이 환경과 연결된 파이프라인을 최신 AEM 버전으로 업데이트할 수 있습니다.

파이프라인 버전이 공개적으로 사용 가능한 최신 AEM 버전으로 업데이트되면 관련 파이프라인을 실행하여 최신 버전을 환경에 배포하라는 메시지가 표시됩니다.

![파이프라인을 실행하여 환경을 업데이트하라는 메시지 표시](assets/update-run-pipeline.png)

**업데이트** 옵션의 비헤이비어는 구성 및 프로그램의 현재 상태에 따라 달라집니다.

* 파이프라인이 이미 업데이트된 경우 **업데이트** 옵션은 사용자에게 파이프라인을 실행하라는 메시지를 표시합니다.
* 파이프라인이 이미 업데이트되고 있는 경우 **업데이트** 옵션은 업데이트가 이미 실행 중임을 사용자에게 알립니다.
* 적절한 파이프라인이 종료되지 않으면 **업데이트** 옵션이 사용자에게 파이프라인을 생성하라는 메시지를 표시합니다.

## 개발 환경 삭제 {#deleting-environment}

필수 권한이 있는 사용자는 개발 환경을 삭제할 수 있습니다.

**환경** 카드에 있는 프로그램의 **개요** 화면에서 삭제하려는 개발 환경의 줄임표 버튼을 클릭합니다.

![삭제 옵션](assets/environ-delete.png)

삭제 옵션은 프로그램 **개요** 창의 **환경** 탭에서도 사용할 수 있습니다. 환경의 줄임표 버튼을 클릭하고 **삭제**&#x200B;를 선택합니다.

![환경 탭의 삭제 옵션](assets/environ-delete2.png)

>[!NOTE]
>
>* 프로덕션 프로그램에서 생성된 프로덕션 및 스테이징 환경은 삭제할 수 없습니다.
>* 샌드박스 프로그램의 프로덕션 및 스테이징 환경은 삭제할 수 있습니다.

## 액세스 관리 {#managing-access}

**환경** 카드에 있는 환경의 줄임표 메뉴에서 **액세스 관리**&#x200B;를 선택합니다. 작성자 인스턴스로 직접 이동하여 환경에 대한 액세스를 관리할 수 있습니다.

![액세스 관리 옵션](assets/environ-access.png)

>[!TIP]
>
>문서 보기 [AEM as a Cloud Service 팀 및 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md) AEM as a Cloud Service 팀 및 제품 프로필로 라이선스가 부여된 Adobe 솔루션에 대한 액세스 권한을 부여하고 제한하는 방법에 대해 알아봅니다.

## Developer Console 액세스 {#accessing-developer-console}

**환경** 카드에 있는 환경의 줄임표 메뉴에서 **Developer Console**&#x200B;을 선택합니다. 그러면 브라우저에서 **Developer Console** 로그인 페이지가 있는 새 탭이 열립니다.

![](assets/environ-devconsole.png)

**개발자** 역할을 가진 사용자만 **Developer Console**&#x200B;에 액세스할 수 있습니다. 단, 샌드박스 프로그램의 경우 샌드박스 프로그램에 대한 액세스 권한이 있는 모든 사용자가 **Developer Console**&#x200B;에 액세스할 수 있습니다.

자세한 내용은 [샌드박스 환경 최대 절전 모드 설정 및 해제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html#hibernating-introduction) 문서를 참조하십시오.

이 옵션은 개별 환경의 줄임표 메뉴를 클릭할 때 표시되는 **개요** 창의 **환경** 탭에서도 사용할 수 있습니다.

## 로컬 로그인 {#login-locally}

Adobe Experience Manager에 로컬로 로그인하려면 **환경** 카드에 있는 환경의 줄임표 메뉴에서 **로컬 로그인**&#x200B;을 선택합니다.

![로컬 로그인](assets/environ-login-locally.png)

또한 **개요** 페이지의 **환경** 탭에서도 로컬로 로그인할 수 있습니다.

![환경 탭의 로컬 로그인](assets/environ-login-locally-2.png)

## 사용자 정의 도메인 이름 관리 {#manage-cdn}

사용자 정의 도메인 이름은 Cloud Manager for Sites 프로그램에서 게시 및 미리보기 서비스 모두에 대해 지원됩니다. 각 Cloud Manager 환경은 최대 250개의 사용자 정의 도메인을 호스팅할 수 있습니다.

사용자 정의 도메인 이름을 구성하려면 **환경** 탭으로 이동하고 환경을 클릭하여 환경 세부 정보를 봅니다.

![환경 세부 정보](assets/domain-names.png)

사용자 환경의 게시 서비스에서 다음 작업을 수행할 수 있습니다.

* [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

* [사용자 정의 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

* [사용자 정의 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) 또는 [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) 상태 확인

* [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn)


## IP 허용 목록 관리 {#manage-ip-allow-lists}

IP 허용 목록은 Cloud Manager에서 Sites 프로그램의 작성자, 게시 및 미리보기 서비스를 위해 지원됩니다.

IP 허용 목록을 관리하려면 프로그램 **개요** 페이지에 있는 **환경** 탭으로 이동합니다. 세부 정보를 관리하려면 개별 환경을 클릭합니다.

### IP 허용 목록 적용 {#apply-ip-allow-list}

IP 허용 목록을 적용하면 허용 목록 정의에 포함된 모든 IP 범위가 환경의 작성자 또는 게시 서비스와 연결됩니다. 의 사용자 **비즈니스 소유자** 또는 **배포 관리자** ip 역할을 적용하려면 허용 목록이 로그인해야 합니다.

IP 허용 목록을 환경에 적용하려면 Cloud Manager에 IP 환경이 있어야 합니다. Cloud Manager의 IP 허용 목록에 대한 자세한 내용은 [Cloud Manager의 IP 허용 목록 소개](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) 문서를 참조하십시오.

다음 단계를 따라 IP 허용 목록을 적용하십시오.

1. 프로그램 **개요** 화면의 **환경** 탭에서 특정 환경으로 이동하고 **IP 허용 목록** 표로 이동합니다.
1. IP 허용 목록 표 상단의 입력 필드를 사용하여 IP 허용 목록과 이를 적용할 작성자 또는 게시 서비스를 선택합니다.
1. **적용**&#x200B;을 클릭하여 제출을 확인합니다.

### IP 허용 목록 적용 취소 {#unapply-ip-allow-list}

IP 허용 목록의 적용을 취소하면 환경의 작성자 또는 게시자 서비스에서 허용 목록 정의에 포함된 모든 IP 범위의 연결이 해제됩니다. 의 사용자 **비즈니스 소유자** 또는 **배포 관리자** ip 허용 목록을 적용 취소하려면 역할이 로그인해야 합니다.

다음 단계를 따라 IP 허용 목록을 적용 취소하십시오.

1. 프로그램 **개요** 화면의 **환경** 탭에서 특정 환경으로 이동하고 **IP 허용 목록** 표로 이동합니다.
1. 적용을 취소하려는 IP 허용 목록 규칙이 나열된 행을 식별합니다.
1. 행의 끝에 있는 줄임표 버튼을 선택합니다.
1. **적용 취소**&#x200B;를 선택하여 제출을 확인합니다.
