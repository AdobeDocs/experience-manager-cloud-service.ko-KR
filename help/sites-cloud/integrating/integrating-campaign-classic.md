---
title: Adobe Campaign Classic과 통합
description: AEM as a Cloud Service과 Adobe Campaign Classic을 통합하여 캠페인에 적합한 매력적인 컨텐츠를 만드는 방법을 알아봅니다.
feature: Administering
role: Admin
exl-id: 23874955-bdf3-41be-8a06-53d2afdd7f2b
source-git-commit: 9ad97fdb26c0049f1b6a4b0958c93e2d4af803fb
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 0%

---

# Adobe Campaign Classic과 통합 {#integrating-campaign-classic}

AEM as a Cloud Service과 Adobe Campaign을 통합하면 AEM에서 직접 이메일 게재, 컨텐츠 및 양식을 관리할 수 있습니다. as a Cloud Service 솔루션 간에 양방향 통신을 활성화하려면 Adobe Campaign Classic과 AEM as a Cloud Service 모두에서 구성 단계가 필요합니다.

이 통합을 통해 AEM as a Cloud Service 및 Adobe Campaign Classic을 독립적으로 사용할 수 있습니다. 마케터는 캠페인을 만들고 Adobe Campaign에서 타깃팅을 사용할 수 있지만 동시에 컨텐츠 작성자는 AEM as a Cloud Service에서 컨텐츠 디자인에서 작업할 수 있습니다. 통합을 통해 AEM에서 캠페인의 콘텐츠와 디자인을 Campaign에서 타깃팅하고 전달할 수 있습니다.

## 통합 단계 {#integration-steps}

AEM과 Campaign 간의 통합에는 두 솔루션에서 많은 단계가 필요합니다.

1. [Campaign에 AEM 통합 패키지를 설치합니다.](#install-package)
1. [Campaign에서 AEM용 연산자 만들기](#create-operator)
1. [AEM에서 Campaign 통합 구성](#campaign-integration)
1. [AEM Externalizer 구성](#externalizer)
1. [AEM에서 campaign-remote 사용자 구성](#configure-user)
1. [Campaign에서 AEM 외부 계정 구성](#acc-setup)

이 문서에서는 이러한 각 단계를 자세히 설명합니다

## 사전 요구 사항 {#prerequisites}

* Adobe Campaign Classic에 대한 관리자 액세스
   * 통합을 수행하려면 구성된 데이터베이스를 포함하여 작업 중인 Adobe Campaign Classic 인스턴스가 필요합니다.
   * Adobe Campaign Classic 설정 및 구성 방법에 대한 자세한 내용은 [Adobe Campaign Classic 설명서,](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html) 특히 설치 및 구성 안내서를 참조하십시오.

* AEM as a Cloud Service 관리자 액세스

## Campaign에 AEM 통합 패키지 설치 {#install-package}

다음 **AEM 통합** Adobe Campaign의 패키지에는 AEM에 연결하는 데 필요한 다양한 표준 구성이 포함되어 있습니다.

1. 관리자는 클라이언트 콘솔을 사용하여 Adobe Campaign 인스턴스에 로그인합니다.

1. 선택 **도구** > **고급** > **패키지 가져오기...**.

   ![패키지 가져오기](assets/import-package.png)

1. 클릭 **표준 패키지 설치** 을 클릭한 다음 **다음**.

1. 을(를) 확인합니다. **AEM 통합** 패키지.

   ![표준 패키지 설치](assets/select-package.png)

1. 클릭 **다음**, 그런 다음 **시작** 설치를 시작하려면 다음을 수행하십시오.

   ![설치 진행률](assets/installation.png)

1. 클릭 **닫기** 설치가 완료되면

이제 통합 패키지가 설치되었습니다.

## Campaign에서 AEM용 연산자 만들기 {#create-operator}

통합 패키지는 자동으로 `aemserver` AEM에서 Adobe Campaign에 연결하는 데 사용하는 연산자입니다. 이 연산자의 보안 영역을 정의하고 암호를 설정해야 합니다.

1. 클라이언트 콘솔을 사용하여 Adobe Campaign에 관리자로 로그인합니다.

1. 선택 **도구** -> **탐색기** 메뉴 모음에서 를 클릭합니다.

1. 탐색기에서 **관리** > **액세스 관리** > **연산자** 노드 아래에 있어야 합니다.

1. 을(를) 선택합니다 `aemserver` 연산자를 사용할 수 있습니다.

1. 설정 **편집** 연산자의 탭에서 **액세스 권한** 하위 탭을 클릭한 다음 **액세스 매개 변수 편집..** 링크를 클릭합니다.

   ![보안 영역 설정](assets/access-rights.png)

1. 적절한 보안 영역을 선택하고 필요에 따라 신뢰할 수 있는 IP 마스크를 정의합니다.

1. **저장**&#x200B;을 클릭합니다.

1. Adobe Campaign 클라이언트에서 로그아웃합니다.

1. Adobe Campaign 서버의 파일 시스템에서 Campaign 설치 위치로 이동하여 `serverConf.xml` 파일로 저장할 수 있습니다. 이 파일은 일반적으로 다음 위치에 있습니다.
   * `C:\Program Files\Adobe\Adobe Campaign Classic v7\conf` 입니다.
   * `/usr/local/neolane/nl6/conf/eng` Linux.

1. 검색 대상 `securityZone` 및 AEM 연산자의 보안 영역에 대해 다음 매개 변수가 설정되어 있는지 확인합니다.

   * `allowHTTP="true"`
   * `sessionTokenOnly="true"`
   * `allowUserPassword="true"`.

1. 파일을 저장합니다.

1. 보안 영역이 `config-<server name>.xml` 파일.

   * 구성 파일에 별도의 보안 영역 설정이 포함되어 있으면 `allowUserPassword` 속성 `true`.

1. Adobe Campaign Classic 서버 포트를 변경하려면 `8080` 원하는 포트를 사용하여 데이터를 검색합니다.

>[!CAUTION]
>
>기본적으로 연산자에 대해 구성된 보안 영역이 없습니다. AEM에서 Adobe Campaign에 연결하려면 이전 단계에 자세히 설명된 영역을 선택해야 합니다.
>
>Adobe은 보안 문제를 방지하기 위해 AEM 전용 보안 영역을 만들 것을 강력히 권장합니다. 이 항목에 대한 자세한 내용은 [Adobe Campaign Classic 설명서.](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/security-zones.html)

1. Campaign 클라이언트에서 `aemserver` 연산자를 선택하고 **일반** 탭.

1. 을(를) 클릭합니다. **암호 재설정..** 링크를 클릭합니다.

1. 암호를 지정하고 나중에 사용할 수 있도록 안전한 위치에 저장합니다.

1. 클릭 **확인** 의 암호를 저장하려면 `aemserver` 연산자를 사용할 수 있습니다.

## AEM에서 Campaign 통합 구성 {#campaign-integration}

AEM 사용 [이미 Campaign에서 설정한 연산자](#create-operator) Campaign과 통신하기 위해

1. 관리자로 AEM 작성 인스턴스에 로그인합니다.

1. 전역 탐색 사이드 레일에서 를 선택합니다. **도구** > **Cloud Services** > **기존 Cloud Services** > **Adobe Campaign**&#x200B;를 클릭한 다음 **지금 구성**.

   ![Adobe Campaign 구성](assets/configure-campaign-service.png)

1. 대화 상자에서 다음을 입력하여 Campaign 서비스 구성을 만듭니다. **제목** 을(를) 클릭합니다. **만들기**.

   ![캠페인 구성 대화 상자](assets/configure-campaign-dialog.png)

1. 구성을 편집할 새 창과 대화 상자가 열립니다. 필요한 정보를 제공합니다.

   * **사용자 이름** - 다음 [이전 단계에서 생성된 Adobe Campaign AEM 통합 패키지 연산자입니다.](#create-operator) 기본적으로 다음과 같습니다 `aemserver`.
   * **암호** - 다음 암호입니다. [이전 단계에서 생성된 Adobe Campaign AEM 통합 패키지 연산자입니다.](#create-operator)
   * **API 종료 지점** - Adobe Campaign 인스턴스 URL입니다.

   ![AEM에서 Adobe Campaign 구성](assets/configure-campaign.png)

1. 선택 **Adobe Campaign에 연결** 연결을 확인하려면 **확인**.

이제 AEM은 Adobe Campaign과 통신할 수 있습니다.

>[!NOTE]
>
>인터넷을 통해 Adobe Campaign 서버에 연결할 수 있는지 확인하십시오. AEM as a Cloud Service은 개인 네트워크에 액세스할 수 없습니다.

## AEM Externalizer 구성 {#externalizer}

Externalizer는 AEM에서 리소스 경로를 외부 및 절대 URL로 변환하는 OSGi 서비스로서, AEM에서 Campaign에서 사용할 수 있는 컨텐츠를 제공하는 데 필요합니다.

1. 관리자로 AEM 작성 인스턴스에 로그인합니다.
1. 에서 OSGi 서비스의 상태 덤프를 확인하여 Externalizer 구성에서 게시 인스턴스를 확인합니다 [개발자 콘솔.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#osgi-services)
1. 올바르지 않은 경우 해당 인스턴스 git 리포지토리에서 필요한 변경 작업을 수행한 다음 [cloud manager를 사용하여 구성을 배포합니다.](/help/implementing/cloud-manager/deploy-code.md)

```text
Service 3310 - [com.day.cq.commons.externalizer] (pid: com.day.cq.commons.impl.externalizerImpl)",
"  from Bundle 420 - Day Communique 5 Commons Library (com.day.cq.cq-commons), version 5.12.16",
"    component.id: 2149",
"    component.name: com.day.cq.commons.impl.externalizerImpl",
"    externalizer.contextpath: ",
"    externalizer.domains: [local https://author-p17558-e33255-cmstg.adobeaemcloud.com, author https://author-p17558-e33255-cmstg.adobeaemcloud.com,
     publish https://publish-p17558-e33255-cmstg.adobeaemcloud.com]",
"    externalizer.encodedpath: false",
"    externalizer.host: ",
"    feature-origins: [com.day.cq:cq-quickstart:slingosgifeature:cq-platform-model_quickstart_author:6.6.0-V23085]",
"    service.bundleid: 420",
"    service.description: Creates absolute URLs",
"    service.scope: bundle",
"    service.vendor: Adobe Systems Incorporated",
```

>[!NOTE]
>
>Adobe Campaign 서버에서 게시 인스턴스에 연결할 수 있어야 합니다.

## AEM에서 campaign-remote 사용자 구성 {#configure-user}

Campaign이 AEM과 통신하려면 `campaign-remote` AEM의 사용자.

1. 관리자로 AEM에 로그인합니다.
1. 기본 탐색 콘솔에서 을(를) 클릭합니다. **도구** 왼쪽 레일에 있습니다.
1. 그런 다음 **보안** -> **사용자** 를 클릭하여 사용자 관리 콘솔을 엽니다.
1. 을(를) 찾습니다 `campaign-remote` 사용자.
1. 을(를) 선택합니다 `campaign-remote` user and click **속성** 를 눌러 사용자를 편집합니다.
1. 에서 **사용자 설정 편집** 창 **암호 변경**.
1. 사용자에게 새 암호를 제공하고 나중에 사용할 수 있도록 안전한 위치에 암호를 기록해 두십시오.
1. 클릭 **저장** 암호 변경 내용을 저장하려면 을 클릭합니다.
1. 클릭 **저장 및 닫기** 변경 내용을 `campaign-remote` 사용자.

## Campaign에서 AEM 외부 계정 구성 {#acc-setup}

When [설치 **AEM 통합** 패키지,](#install-package) AEM용으로 외부 계정이 만들어집니다. 이 외부 계정을 구성함으로써 Adobe Campaign은 AEM as a Cloud Service에 연결하여 솔루션 간에 양방향 통신을 가능하게 할 수 있습니다.

1. 클라이언트 콘솔을 사용하여 Adobe Campaign에 관리자로 로그인합니다.

1. 선택 **도구** -> **탐색기** 메뉴 모음에서 를 클릭합니다.

1. 탐색기에서 **관리** > **플랫폼** > **외부 계정** 노드 아래에 있어야 합니다.

   ![외부 계정](assets/external-accounts.png)

1. 외부 AEM 계정을 찾습니다. 기본적으로 다음과 같은 값이 있습니다.

   * **유형** - AEM
   * **레이블** - AEM 인스턴스
   * **내부 이름** - aemInstance

1. 설정 **일반** 이 계정의 탭에서 [campaign-remote 사용자 암호 설정](#set-campaign-remote-password) 단계.

   * **서버** - AEM 작성자 서버 주소
      * Adobe Campaign Classic 서버 인스턴스에서 AEM 작성자 서버에 연결할 수 있어야 합니다.
      * 서버 주소가 **not** 후행 슬래시로 끝남.
   * **계정** - 기본적으로 다음과 같습니다 `campaign-remote` AEM에서 설정한 사용자 [campaign-remote 사용자 암호 설정](#set-campaign-remote-password) 단계.
   * **암호** - 이 암호는 `campaign-remote` AEM에서 설정한 사용자 [campaign-remote 사용자 암호 설정](#set-campaign-remote-password) 단계.

1. 을(를) 선택합니다 **활성화됨** 확인란을 선택합니다.

1. **저장**&#x200B;을 클릭합니다.

이제 Adobe Campaign은 AEM과 통신할 수 있습니다.

## 다음 단계 {#next-steps}

Adobe Campaign Classic과 AEM as a Cloud Service이 모두 구성되어 이제 통합이 완료됩니다.

이제 다음을 계속 진행하여 Adobe Experience Manager에서 뉴스레터를 만드는 방법을 배울 수 있습니다 [이 문서는](/help/sites-cloud/integrating/creating-newsletter.md)
