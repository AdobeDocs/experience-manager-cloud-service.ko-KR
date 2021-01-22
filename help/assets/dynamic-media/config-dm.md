---
title: Dynamic Media Cloud Service 구성
description: Adobe Experience Manager에서 Cloud Service을 구성하는 방법에 대한 정보입니다.
translation-type: tm+mt
source-git-commit: 83ad14d49a5250c3070eed4d4962443da6faf5f5
workflow-type: tm+mt
source-wordcount: '3869'
ht-degree: 1%

---


# Dynamic Media Cloud Service {#configuring-dynamic-media} 구성 정보

개발 환경, 스테이징용 환경 및 라이브 프로덕션용 환경 등 서로 다른 환경에 대해 Adobe Experience Manager 설정을 사용하는 경우 해당 환경 각각에 대해 Dynamic Media Cloud Services을 구성해야 합니다.

## Dynamic Media {#architecture-diagram-of-dynamic-media}의 아키텍처 다이어그램

다음 아키텍처 다이어그램에서는 Dynamic Media 작동 방식을 설명합니다.

새로운 아키텍처에서는 AEM이 기본 소스 에셋을 담당하고 에셋 처리 및 게시를 위해 Dynamic Media과 동기화합니다.

1. 기본 소스 에셋이 AEM에 업로드되면 Dynamic Media에 복제됩니다. 이때 Dynamic Media은 이미지의 비디오 인코딩 및 동적 변형과 같은 모든 에셋 처리 및 변환 생성을 처리합니다.
1. 변환이 생성되면 AEM은 안전하게 원격 Dynamic Media 변환에 액세스하고 미리 볼 수 있습니다(이진 파일은 AEM 인스턴스로 다시 전송되지 않음).
1. 컨텐츠가 게시 및 승인될 준비가 되면, Dynamic Media 서비스는 컨텐츠를 전달 서버로 푸시하고 CDN의 컨텐츠를 캐시하도록 트리거합니다.

![chlimage_1-550](assets/chlimage_1-550.png)

<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading AEM Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your AEM instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Cloud Services {#configuring-dynamic-media-cloud-services}에 새 Dynamic Media 구성 만들기

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다.
1. 콘솔 왼쪽에서 도구 아이콘을 누른 다음 **[!UICONTROL Cloud Services > Dynamic Media 구성]**&#x200B;을 누릅니다.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL global]**(**[!UICONTROL global]** 왼쪽에 있는 폴더 아이콘을 탭하거나 선택하지 않음)을 누른 다음 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.
1. **[!UICONTROL Dynamic Media 구성 만들기]** 페이지에서 제목, Dynamic Media 계정 이메일 주소, 암호를 입력한 다음 지역을 선택합니다. Adobe이 제공 이메일의 내용을 통해 제공합니다. 수신하지 못한 경우 지원 센터에 문의하십시오.
1. **[!UICONTROL Dynamic Media에 연결]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 암호 변경]** 대화 상자의 **[!UICONTROL 새 암호]** 필드에 8-25자로 구성된 새 암호를 입력합니다. 암호는 다음 중 하나 이상을 포함해야 합니다.

   * 대문자
   * 소문자
   * 번호
   * 특수 문자:`# $ & . - _ : { }`

   **[!UICONTROL 현재 암호]** 필드는 상호 작용에서 의도적으로 미리 채워지고 숨겨집니다.

   필요한 경우 암호 눈 아이콘을 눌러 입력하거나 다시 입력한 암호의 맞춤법을 확인하여 암호를 표시할 수 있습니다. 암호를 숨기려면 아이콘을 다시 누릅니다.

1. **[!UICONTROL 반복 암호]** 필드에서 새 암호를 다시 입력한 다음 **[!UICONTROL 완료를 누릅니다.]**

   **[!UICONTROL Dynamic Media 구성 만들기]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 저장]**&#x200B;을 탭하면 새 암호가 저장됩니다.

   **[!UICONTROL 암호 변경]** 대화 상자에서 **[!UICONTROL 취소]**&#x200B;를 탭한 경우 새로 만든 Dynamic Media 구성을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 탭해도 새 암호를 입력해야 합니다.

   [암호를 Dynamic Media](#change-dm-password)로 변경을 참조하십시오.

1. 연결이 성공하면 다음을 설정할 수 있습니다.

   | 속성 | 설명 |
   |---|---|
   | 회사 | Dynamic Media 계정의 이름입니다. 다양한 하위 브랜드, 사업부 또는 다른 스테이징/프로덕션 환경에 대해 여러 Dynamic Media 계정을 보유할 수도 있습니다. |
   | 회사 루트 폴더 경로 | 회사의 루트 폴더 경로입니다. |
   | 자산 게시 | 다음 옵션 중 하나를 선택할 수 있습니다.<br>**[!UICONTROL 즉시&#x200B;]**.자산이 업로드되면 시스템은 자산을 인제스트하고 URL/포함을 즉시 제공합니다. 자산을 게시하는 데 필요한 사용자 개입은 없습니다.<br>**[!UICONTROL 활성화 시]**:URL/포함 링크가 제공되기 전에 먼저 자산을 명시적으로 게시해야 합니다.<br>**[!UICONTROL 선택적 게시&#x200B;]**:에셋은 보안 미리 보기만을 위해 자동으로 게시되며 공개 도메인에 제공하기 위해 DMS7에 게시하지 않고도 AEM에 명시적으로 게시할 수 있습니다. 앞으로 Adobe은 상호 배타적인 AEM에 에셋을 게시하고 Dynamic Media에 에셋을 게시하기 위한 이 옵션을 강화하게 됩니다. 즉, 스마트 자르기 또는 동적 표현물과 같은 기능을 사용할 수 있도록 자산을 DMS7에 게시할 수 있습니다. 또는 미리 보기 전용 AEM에서만 에셋을 게시할 수 있습니다.동일한 에셋은 공용 도메인에 전달되기 위해 DMS7에 게시되지 않습니다. |
   | 보안 미리 보기 서버 | 보안 변환 미리 보기 서버에 대한 URL 경로를 지정할 수 있습니다. 즉, 변환이 생성된 후 AEM은 원격 Dynamic Media 변환에 안전하게 액세스하고 미리 볼 수 있습니다(이진 파일은 AEM 인스턴스로 다시 전송되지 않음).<br>회사 서버 또는 특수 서버를 사용하기 위해 특별한 준비가 되어 있지 않은 경우, Adobe Systems에서는 이 설정을 지정한 대로 유지하는 것이 좋습니다. |
   | 모든 컨텐츠 동기화 | 기본적으로 선택됩니다. Dynamic Media에 대한 동기화에서 자산을 선택적으로 포함하거나 제외하려면 이 옵션을 선택 취소합니다. 이 옵션을 선택 해제하면 다음 두 가지 Dynamic Media 동기화 모드:<br>**[!UICONTROL Dynamic Media 동기화 모드]**<br>**[!UICONTROL 기본적으로 활성화&#x200B;]**에서 선택할 수 있습니다.특별히 제외하도록 폴더를 표시하지 않는 한 기본적으로 모든 폴더에 구성이 적용됩니다. <!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL 기본적으로 비활성화됨]**:Dynamic Media에 동기화할 선택한 폴더를 명시적으로 표시할 때까지 해당 구성은 어떤 폴더에도 적용되지 않습니다.<br>Dynamic Media에 동기화할 선택한 폴더를 표시하려면 자산 폴더를 선택한 다음 도구 모음에서 속성을  **[!UICONTROL 탭합니다]**. **[!UICONTROL 세부 사항]** 탭의 **[!UICONTROL Dynamic Media 동기화 모드]** 드롭다운 목록에서 다음 3가지 옵션 중에서 선택합니다. 완료되면 **[!UICONTROL 저장]**&#x200B;을 탭합니다. *기억:이 3가지 옵션은 [모든 내용&#x200B;**동기화]를 선택한 경우 사용할 수**없습니다.* Dynamic Media [의 폴더 수준에서 선택적 게시로 작업을 참조하십시오.](/help/assets/dynamic-media/selective-publishing.md)<br>**[!UICONTROL 상속됨&#x200B;]**:폴더에 명시적 동기화 값이 없습니다.대신 폴더는 상위 폴더 중 하나 또는 클라우드 구성의 기본 모드에서 동기화 값을 상속합니다. 상속된 도구 설명을 통해 표시되는 세부 상태입니다.<br>**[!UICONTROL 하위 폴더에 대해 활성화]**:Dynamic Media에 동기화할 수 있도록 이 하위 트리에 모든 것을 포함하십시오. 폴더 특정 설정은 클라우드 구성에서 기본 모드를 덮어씁니다.<br>**[!UICONTROL 하위 폴더에 대해 비활성화됨&#x200B;]**:이 하위 트리의 모든 항목을 Dynamic Media에 동기화하지 않도록 제외합니다. |

   >[!NOTE]
   >
   >Dynamic Media에서는 버전 관리가 지원되지 않습니다. 또한, Dynamic Media 구성 편집 페이지의 **[!UICONTROL 자산 게시]**&#x200B;이 **[!UICONTROL 활성화 시]**&#x200B;로 설정된 경우에만 지연된 활성화가 적용됩니다. 그런 다음 자산이 처음 활성화될 때까지만 적용됩니다.
   >
   >
   >자산이 활성화되면 모든 업데이트가 즉시 S7 전달에 실시간으로 게시됩니다.

   ![dynamicmediaconficonfiguration2업데이트](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다. 새 Dynamic Media 암호 및 구성이 저장됩니다. 대신 **[!UICONTROL 취소]**&#x200B;를 탭하면 암호 업데이트가 발생하지 않습니다.
1. **[!UICONTROL Dynamic Media]** 구성 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 눌러 구성을 시작합니다.

   >[!IMPORTANT]
   >
   >새 Dynamic Media 구성이 설정을 완료하면 AEM 받은 편지함 내에서 상태 알림을 받게 됩니다.
   >
   >이 받은 편지함 알림은 구성이 성공했는지 여부를 알려줍니다.
   > 자세한 내용은 [새 Dynamic Media 구성 문제 해결](#troubleshoot-dm-config) 및 [받은 편지함](/help/sites-cloud/authoring/getting-started/inbox.md)을 참조하십시오.

1. Dynamic Media 컨텐츠를 게시하기 전에 안전하게 미리 보려면 Dynamic Media에 연결하려면 AEM 작성자 인스턴스를 &quot;허용 목록에 추가하다&quot;해야 합니다. 이를 설정하려면 다음을 수행합니다.

   * [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을(를) 열고 계정에 로그인합니다. 자격 증명 및 로그인 세부 정보는 프로비저닝 시 Adobe에서 제공되었습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.
   * 페이지 오른쪽 상단의 탐색 막대에서 **[!UICONTROL 설정 > 응용 프로그램 설정 > 게시 설정 > 이미지 서버]**&#x200B;를 클릭합니다.

   * 이미지 서버 게시 페이지의 게시 컨텍스트 드롭다운 목록에서 **[!UICONTROL 테스트 이미지 제공]**&#x200B;을 선택합니다.
   * 클라이언트 주소 필터의 경우 **[!UICONTROL 추가]**&#x200B;를 누릅니다.
   * 주소를 활성화(켜기)하려면 확인란을 선택한 다음 AEM 작성자 인스턴스의 IP 주소(발송자 IP 아님)를 입력합니다.
   * **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

이제 기본 구성으로 완료되었습니다.dynamic media을 사용할 준비가 되었습니다.

구성을 추가로 사용자 정의하려면 Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode)에서 [고급 설정 구성 아래의 작업을 선택적으로 완료할 수 있습니다.

### 새 Dynamic Media 구성 문제 해결 {#troubleshoot-dm-config}

새 Dynamic Media 구성이 설정을 완료하면 AEM 받은 편지함 내에서 상태 알림을 받게 됩니다. 이 알림은 구성이 성공했는지 여부를 받은 편지함의 다음 이미지와 같이 알려줍니다.

![aeminboxsuccess](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![aeminboxfailure](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

[받은 편지함](/help/sites-cloud/authoring/getting-started/inbox.md)도 참조하십시오.

**새 Dynamic Media 구성 문제를 해결하려면**

1. AEM 페이지의 오른쪽 위 모서리 근처에 있는 벨 아이콘을 탭한 다음 **[!UICONTROL 모두 보기]**&#x200B;를 탭합니다.
1. 받은 편지함 페이지에서 성공 알림을 탭하여 구성의 상태 및 로그에 대한 개요를 읽습니다.

   구성에 실패하면 다음 스크린샷과 유사한 실패 알림을 탭합니다.

   ![dmsetupfailed](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. **[!UICONTROL DMSETUP]** 페이지에서 오류를 설명하는 구성 세부 사항을 검토하십시오. 특히 오류 메시지 또는 오류 코드를 메모해 둡니다. 이 정보는 Adobe 지원 센터에 문의해야 합니다.

   ![dmsetuppage](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### 암호를 Dynamic Media {#change-dm-password}으로 변경

Dynamic Media의 암호 만료는 현재 시스템 날짜로부터 100년으로 설정됩니다.

암호는 다음 중 하나 이상을 포함해야 합니다.

* 대문자
* 소문자
* 번호
* 특수 문자:`# $ & . - _ : { }`

필요한 경우 암호 눈 아이콘을 눌러 입력하거나 다시 입력한 암호의 맞춤법을 확인하여 암호를 표시할 수 있습니다. 암호를 숨기려면 아이콘을 다시 누릅니다.

변경된 암호는 **[!UICONTROL Dynamic Media 구성 편집]** 페이지의 오른쪽 위 모서리에 있는 **[!UICONTROL 저장]**&#x200B;을 탭하면 저장됩니다.

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다.
1. 콘솔 왼쪽에서 도구 아이콘을 누른 다음 **[!UICONTROL Cloud Services > Dynamic Media 구성을 누릅니다.]**
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL global]**(**[!UICONTROL global]** 왼쪽에 있는 폴더 아이콘을 탭하거나 선택하지 않음)을 누른 다음 **[!UICONTROL 편집을 탭합니다.]**
1. **[!UICONTROL Dynamic Media 구성 편집]** 페이지의 **[!UICONTROL 암호]** 필드 바로 아래에 있는 **[!UICONTROL 암호 변경을 탭합니다.]**
1. **[!UICONTROL 암호 변경]** 대화 상자에서 다음을 수행합니다.

   * **[!UICONTROL 새 암호]** 필드에 새 암호를 입력합니다.

      **[!UICONTROL 현재 암호]** 필드는 상호 작용에서 의도적으로 미리 채워지고 숨겨집니다.

   * **[!UICONTROL 반복 암호]** 필드에서 새 암호를 다시 입력한 다음 **[!UICONTROL 완료를 누릅니다.]**

1. **[!UICONTROL Dynamic Media 구성 편집]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 저장]**&#x200B;을 누른 다음 **[!UICONTROL 확인을 누릅니다.]**

## (선택 사항) Dynamic Media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}에서 고급 설정 구성

Dynamic Media의 구성 및 설정을 추가로 사용자 정의하거나 성능을 최적화하려는 경우 다음 *선택적* 작업 중 하나 이상을 완료할 수 있습니다.

* [Dynamic Media 설정 및 구성](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(선택 사항) Dynamic Media 성능 조정](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (선택 사항) Dynamic Media 설정 {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings} 설정 및 구성

Dynamic Media Classic 사용자 인터페이스를 사용하여 Dynamic Media 설정을 변경합니다.

위의 작업 중 일부는 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을(를) 연 다음 계정에 로그인해야 합니다.

설정 및 구성 작업은 다음과 같습니다.

* [이미지 서버에 대한 게시 설정](#publishing-setup-for-image-server)
* [응용 프로그램 일반 설정 구성](#configuring-application-general-settings)
* [색상 관리 구성](#configuring-color-management)
* [지원되는 형식에 대한 MIME 유형 편집](#editing-mime-types-for-supported-formats)
* [지원되지 않는 형식에 대한 MIME 유형 추가](#adding-mime-types-for-unsupported-formats)

<!-- * [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### 이미지 서버 {#publishing-setup-for-image-server}에 대한 게시 설정

제작 설정 설정은 Dynamic Media에서 기본적으로 자산을 제공하는 방법을 결정합니다. 설정이 지정되지 않은 경우 Dynamic Media은 제작 설정에 정의된 기본 설정에 따라 자산을 제공합니다. 예를 들어 해상도 특성을 포함하지 않는 이미지를 전달하도록 요청하면 기본 개체 해상도 설정이 있는 이미지가 생성됩니다.

게시 설정을 구성하려면:dynamic media Classic에서 **[!UICONTROL 설정 > 응용 프로그램 설정 > 게시 설정 > 이미지 서버]**&#x200B;를 클릭합니다.

[이미지 서버] 화면은 이미지 전달을 위한 기본 설정을 설정합니다. 각 설정에 대한 설명은 UI 화면을 참조하십시오.

**[!UICONTROL 요청 속성]**  - 이러한 설정은 서버에서 전달할 수 있는 이미지에 대한 제한을 적용합니다.
**[!UICONTROL 기본 요청 속성]**  - 이 설정은 이미지의 기본 모양과 관련이 있습니다.
**[!UICONTROL 공통 축소판 속성]**  - 이 설정은 축소판 이미지의 기본 모양과 관련이 있습니다.
**[!UICONTROL 카탈로그 필드의 기본값]** - 이 설정은 이미지의 해상도 및 기본 축소판 유형과 관련이 있습니다.
**[!UICONTROL 색상 관리 속성]**  - 이 설정에 따라 사용되는 ICC 색상 프로파일이 결정됩니다.
**[!UICONTROL 호환성 속성]**  - 이 설정을 사용하면 텍스트 레이어의 맨 앞 및 뒤에 있는 단락이 이전 버전과의 호환성을 위해 버전 3.6에서와 같이 처리됩니다.
**[!UICONTROL 현지화 지원]**  - 이 설정을 사용하여 여러 로케일 속성을 관리할 수 있습니다. 또한 로케일 맵 문자열을 지정할 수 있으므로 뷰어에서 다양한 도구 설명을 지원할 언어를 정의할 수 있습니다. **[!UICONTROL 현지화 지원]** 설정에 대한 자세한 내용은 자산 현지화 설정 시 [고려 사항](https://experienceleague.corp.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#considerations-when-setting-up-localization-of-assets)을 참조하십시오.

#### 응용 프로그램 일반 설정 구성 중 {#configuring-application-general-settings}

[응용 프로그램 일반 설정] 페이지를 열려면 Dynamic Media Classic 전역 탐색 막대에서 **[!UICONTROL 설정 > 응용 프로그램 설정 > 일반 설정을 클릭합니다.]**

**[!UICONTROL 서버]**  - Dynamic Media은 계정을 프로비저닝할 때 자동으로 회사에 할당된 서버를 제공합니다. 이러한 서버는 웹 사이트 및 응용 프로그램의 URL 문자열을 구성하는 데 사용됩니다. 이러한 URL 호출은 계정에 따라 다릅니다. AEM 지원에 의해 명시적으로 지시하지 않는 한 서버 이름을 변경하지 마십시오.
**[!UICONTROL 이미지]**  덮어쓰기 - Dynamic Media에서는 두 파일의 이름이 같은 파일을 허용하지 않습니다. 각 항목의 URL ID(파일 이름은 확장자를 뺀 값)는 고유해야 합니다. 다음 옵션은 대체 자산을 업로드하는 방법을 지정합니다.원본을 바꾸거나 복제할 것인지 여부입니다. 중복 에셋은 &quot;-1&quot;으로 이름이 바뀝니다. 예를 들어 chair.tif는 chair-1.tif로 이름이 변경되었습니다. 이러한 옵션은 원본과 다른 폴더에 업로드된 에셋이나 원본 파일 이름 확장자가 다른 에셋(예: JPG, TIF 또는 PNG)에 영향을 줍니다.
**[!UICONTROL 현재 폴더에 덮어쓰기, 동일한 기본 이미지 이름/확장명]**  - 이 옵션은 바꿀 수 있는 가장 엄격한 규칙입니다. 교체 이미지를 원본과 동일한 폴더에 업로드하고 교체 이미지의 파일 이름 확장명은 원본과 같아야 합니다. 이러한 요구 사항이 충족되지 않으면 복사본이 만들어집니다. AEM와의 일관성을 유지하려면 항상 현재 폴더에 **[!UICONTROL 덮어쓰기를 선택합니다(동일한 기본 이미지 이름/확장명]**).
**[!UICONTROL 모든 폴더에 덮어쓰기, 동일한 기본 자산 이름/확장자]**  - 대체 이미지의 파일 이름 확장명이 원본 이미지와 동일해야 합니다(예: chair.jpg는 chair.tif가 아니라 chair.jpg를 대체해야 함). 그러나 교체 이미지를 원본과 다른 폴더에 업로드할 수 있습니다. 업데이트된 이미지는 새 폴더에 있습니다.파일을 원래 위치에서 더 이상 찾을 수 없습니다.
**[!UICONTROL 확장명에 관계없이 동일한 기본 자산 이름으로 모든 폴더에 덮어쓰기]**  - 이 옵션은 가장 포괄적인 교체 규칙입니다. 교체 이미지를 원본과 다른 폴더에 업로드하고 파일 이름 확장자가 다른 파일을 업로드하고 원본 파일을 바꿀 수 있습니다. 원본 파일이 다른 폴더에 있는 경우 대체 이미지는 업로드된 새 폴더에 있습니다.
**[!UICONTROL 기본 색상 프로필]**  - 자세한  [내용은 ](#configuring-color-management) 색상관리 구성을 참조하십시오. 자산의 세부 정보 보기에서 **[!UICONTROL 뷰어]**&#x200B;를 선택하면 기본적으로 시스템은 **[!UICONTROL 표현물]** 및 15개의 뷰어 사전 설정을 선택할 때 15개의 표현물을 표시합니다. 이 한도를 늘릴 수 있습니다. [표시](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) 또는 [표시되는 이미지 사전 설정 수 증가 또는 감소](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display)를 참조하십시오.

#### 색상 관리 구성 {#configuring-color-management}

다이내믹 미디어 색상 관리를 사용하면 올바른 에셋에 색상을 적용할 수 있습니다. 색상 교정을 통해 인제스트한 에셋은 색상 공간(RGB, CMYK, 회색) 및 포함된 색상 프로파일을 유지합니다. 동적 변환을 요청하면 이미지 색상이 CMYK, RGB 또는 회색 출력을 사용하여 대상 색상 공간으로 교정됩니다. [이미지 사전 설정 구성](/help/assets/dynamic-media/managing-image-presets.md)을 참조하십시오.

이미지를 요청할 때 색상 보정을 사용하도록 기본 색상 속성을 구성하려면 다음을 수행하십시오.

1. [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을(를) 연 다음 프로비저닝 동안 제공된 자격 증명을 사용하여 계정에 로그인합니다.
1. **[!UICONTROL 설정 > 응용 프로그램 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 제작 설정]** 영역을 확장하고 **[!UICONTROL 이미지 서버]**&#x200B;를 선택합니다. 게시 인스턴스의 기본값을 설정할 때 **[!UICONTROL 게시 컨텍스트]**&#x200B;를 **[!UICONTROL 이미지 제공]**&#x200B;으로 설정합니다.
1. 변경해야 할 속성(예: **[!UICONTROL 색상 관리 속성]** 영역의 속성)으로 스크롤합니다.
다음 색상 교정 속성을 설정할 수 있습니다.

   | 속성 | 설명 |
   |---|---|
   | CMYK 기본 색상 공간 | 기본 CMYK 색상 프로파일의 이름입니다. |
   | 회색 크기 조절 기본 색상 공간 | 기본 회색 색상 프로파일의 이름입니다. |
   | RGB 기본 색상 공간 | 기본 RGB 색상 프로필의 이름입니다. |
   | 색상 변환 렌더링 의도 | 렌더링 의도를 지정합니다. 사용할 수 있는 값은 다음과 같습니다.**[!UICONTROL perceptual]**, **[!UICONTROL 상대 colorometric]**, **[!UICONTROL 채도]**, **[!UICONTROL 절대 열 도표.]** Adobe에서는  **** 기본적으로 관계를 권장합니다. |

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

예를 들어 **[!UICONTROL RGB 기본 색상 공간]**&#x200B;을 *sRGB* 및 **[!UICONTROL CMYK 기본 색상 공간]**&#x200B;을 *WebCoated*&#x200B;으로 설정할 수 있습니다.

이렇게 하면 다음이 수행됩니다.

* RGB 및 CMYK 이미지에 대한 색상 교정을 활성화합니다.
* 색상 프로필이 없는 RGB 이미지는 *sRGB* 색상 공간에 있는 것으로 간주됩니다.
* 색상 프로필이 없는 CMYK 이미지는 *WebCoated* 색상 공간에 있는 것으로 가정합니다.
* RGB 출력을 반환하는 동적 변환은 *sRGB* 색상 공간에 반환됩니다.
* CMYK 출력을 반환하는 동적 변환은 *WebCoated* 색상 공간에 반환됩니다.

#### 지원되는 형식 {#editing-mime-types-for-supported-formats}에 대한 MIME 유형 편집

Dynamic Media에서 처리할 자산 유형을 정의하고 고급 자산 처리 매개 변수를 사용자 정의할 수 있습니다. 예를 들어 자산 처리 매개 변수를 지정하여 다음을 수행할 수 있습니다.

* Adobe PDF을 eCatalog 에셋으로 변환합니다.
* 개인화를 위해 Adobe Photoshop 문서(.PSD)를 배너 템플릿 에셋으로 변환합니다.
* Adobe Illustrator 파일(.AI) 또는 Adobe Photoshop Encapsulated Postscript 파일(.EPS)을 래스터화합니다.
* [비디오 ](/help/assets/dynamic-media/video-profiles.md) 프로필 및  [이미징 프로필](/help/assets/dynamic-media/image-profiles.md) 을 사용하여 각각 비디오와 이미지 처리를 정의할 수 있습니다.

[자산 업로드](/help/assets/add-assets.md)를 참조하십시오.

**지원되는 형식에 대해 MIME 형식을 편집하려면**

1. AEM에서 AEM 로고를 클릭하여 글로벌 탐색 콘솔에 액세스한 다음 **[!UICONTROL 일반 > CRXDE Lite]**&#x200B;을 클릭합니다.
1. 왼쪽 레일에서 다음 항목으로 이동합니다.

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimeetypes](assets/mimetypes.png)

1. mimeTypes 폴더 아래에서 MIME 유형을 선택합니다.
1. CRXDE Lite 페이지의 오른쪽에서:

   * **[!UICONTROL enabled]** 필드를 두 번 클릭합니다. 기본적으로 모든 자산 MIME 유형이 활성화되어 있습니다(이 유형은 **[!UICONTROL true]**). 즉, 자산은 처리를 위해 Dynamic Media에 동기화됩니다. 이 자산 MIME 형식을 처리하지 않도록 제외하려면 이 설정을 **[!UICONTROL false]**&#x200B;로 변경하십시오.

   * **[!UICONTROL jobParam]**&#x200B;을 두 번 클릭하여 연관된 텍스트 필드를 엽니다. 지정된 MIME 유형에 사용할 수 있는 허용된 처리 매개 변수 값 목록은 [지원되는 MIME 유형](/help/assets/file-format-support.md)을 참조하십시오.

1. 다음 중 하나를 수행하십시오.
   * 추가 MIME 유형을 편집하려면 3-4단계를 반복합니다.
   * CRXDE Lite 페이지의 메뉴 모음에서 **[!UICONTROL 모두 저장을 클릭합니다.]**

1. 페이지의 왼쪽 위 모서리에서 **[!UICONTROL CRXDE Lite]**&#x200B;을 눌러 AEM으로 돌아갑니다.

#### 지원되지 않는 형식 {#adding-mime-types-for-unsupported-formats}에 대한 MIME 형식을 추가하는 중

AEM Assets에서 지원되지 않는 형식에 대해 사용자 지정 MIME 형식을 추가할 수 있습니다. CRXDE Lite에 추가하는 새 노드가 AEM에서 삭제되지 않도록 하려면 `image_` 이전에 MIME 유형을 이동해야 하며 해당 활성 값이 **[!UICONTROL false]**&#x200B;로 설정되어 있어야 합니다.

**지원되지 않는 형식에 대해 MIME 형식을 추가하려면**

1. AEM에서 **[!UICONTROL 도구 > 작업 > 웹 콘솔을 누릅니다.]**

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. 새 브라우저 탭이 **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 페이지에 열립니다.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. 페이지에서 다음 스크린샷과 같이 *Adobe CQ Scene7 Asset MIME 유형 서비스* 이름으로 아래로 스크롤합니다. 이름 오른쪽에 있는 **[!UICONTROL 구성 값 편집]**(연필 아이콘)을 누릅니다.

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. **Adobe CQ Scene7 Asset MIME 유형 서비스** 페이지에서 더하기 기호 아이콘 &lt;+>을 클릭합니다. 새 MIME 형식을 추가하기 위해 더하기 기호를 클릭하는 표 상의 위치는 사소한 것입니다.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. 방금 추가한 빈 텍스트 필드에 `DWG=image/vnd.dwg`을 입력합니다.

   `DWG=image/vnd.dwg` 예제는 그림 용도로만 사용됩니다. 여기에 추가하는 MIME 유형은 지원되지 않는 다른 형식일 수 있습니다.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.

   이때 열린 Adobe Experience Manager 웹 콘솔 구성 페이지가 있는 브라우저 탭을 닫을 수 있습니다.

1. 열린 AEM 콘솔이 있는 브라우저 탭으로 돌아갑니다.
1. AEM에서 **[!UICONTROL 도구 > 일반 > CRXDE Lite]**&#x200B;을 탭합니다.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. 왼쪽 레일에서 다음 항목으로 이동합니다.

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. MIME 유형 `image_vnd.dwg`을 드래그하고 다음 스크린샷에 표시된 것처럼 트리의 `image_` 바로 위에 놓습니다.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. MIME 유형 `image_vnd.dwg`이 여전히 선택된 상태에서 **[!UICONTROL 속성]** 탭의 **[!UICONTROL enabled]** 행의 **[!UICONTROL 값]** 열 헤더 아래에서 값을 두 번 클릭하여 **[!UICONTROL 값]** 드롭다운 목록을 엽니다.
1. 필드에 `false`을 입력합니다(또는 드롭다운 목록에서 **[!UICONTROL false]**&#x200B;를 선택합니다).

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 저장]**&#x200B;을 클릭합니다.



### (선택 사항) Dynamic Media {#optional-tuning-the-performance-of-dynamic-media-scene-mode} 성능 조정

Dynamic Media <!--(with `dynamicmedia_scene7` run mode)-->을(를) 원활하게 실행하려면 Adobe은 다음과 같은 동기화 성능/확장성 세부 조정 팁을 권장합니다.

* 다양한 파일 형식을 처리하기 위해 사전 정의된 작업 매개 변수를 업데이트합니다.
* 미리 정의된 Granite 워크플로(비디오 자산) 큐 작업자 스레드를 업데이트하는 중입니다.
* 미리 정의된 [화강암 임시 워크플로(이미지 및 비비디오 자산) 큐 작업자 스레드 업데이트
* Dynamic Media Classic 서버에 대한 최대 업로드 연결을 업데이트하는 중입니다.

#### 다양한 파일 형식을 처리하기 위해 사전 정의된 작업 매개 변수 업데이트

파일을 업로드할 때 작업 매개 변수를 조정하여 보다 신속하게 처리할 수 있습니다. 예를 들어 PSD 파일을 업로드하지만 템플릿으로 처리하지는 않으려는 경우 레이어 추출을 false(off)로 설정할 수 있습니다. 이 경우 조정된 작업 매개 변수는 `process=None&createTemplate=false`으로 표시됩니다.

Adobe은 PDF, Postscript 및 PSD 파일에 대해 다음과 같은 &quot;조정된&quot; 작업 매개 변수를 사용하는 것이 좋습니다.

| 파일 유형 | 권장 작업 매개 변수 |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| Postscript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- To update any of these parameters, follow the steps in [Enabling MIME type-based Assets/Dynamic Media Classic upload job parameter support](#enabling-mime-type-based-assets-scene-upload-job-parameter-support). -->

#### Granite Tranent Workflow 큐 {#updating-the-granite-transient-workflow-queue} 업데이트

Granite Transit 워크플로 큐는 **[!UICONTROL DAM Update Asset]** 작업 과정에 사용됩니다. Dynamic Media에서 이미지 수집 및 처리에 사용됩니다.

**Granite Traniment Workflow 큐를 업데이트하려면**

1. [https://&lt;server>/system/console/configMgr](https://localhost:4502/system/console/configMgr)로 이동하여 **큐:Granite Tranent Workflow Queue**.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. **[!UICONTROL 최대 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   **[!UICONTROL 최대 병렬 작업]**&#x200B;을 증가시켜 Dynamic Media에 대한 대용량 파일 업로드를 적절하게 지원할 수 있습니다. 정확한 값은 하드웨어 용량에 따라 다릅니다. 초기 마이그레이션 또는 일회성 벌크 업로드와 같은 특정 시나리오에서는 큰 값을 사용할 수 있습니다. 하지만 큰 값(예: 코어 수의 2배)을 사용하면 다른 동시 활동에 부정적인 영향을 줄 수 있습니다. 따라서 특정 사용 사례에 따라 값을 테스트 및 조정해야 합니다.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

#### Granite Workflow 큐 {#updating-the-granite-workflow-queue} 업데이트

[Granite Workflow 큐]는 비임시 워크플로우에 사용됩니다. Dynamic Media에서는 **[!UICONTROL Dynamic Media 인코딩 비디오]** 작업 과정으로 비디오를 처리하는 데 사용됩니다.

Granite Workflow 큐를 업데이트하려면:

1. `https://<server>/system/console/configMgr`으로 이동하여 **대기열:Granite Workflow Queue**.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. **[!UICONTROL 최대 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   기본적으로 최대 병렬 작업 수는 사용 가능한 CPU 코어 수에 따라 달라집니다. 예를 들어 4코어 서버에서는 2개의 작업자 스레드를 할당합니다. (0.0과 1.0 사이의 값은 비율 기반이거나 1보다 큰 숫자는 작업자 스레드 수를 할당합니다.)

   대부분의 사용 사례에서 기본 설정 0.5이면 충분합니다.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 누릅니다.

#### Scene7 업로드 연결 업데이트 중 {#updating-the-scene-upload-connection}

Scene7 업로드 연결 설정은 AEM 자산을 Dynamic Media Classic 서버에 동기화합니다.

Scene7 업로드 연결을 업데이트하려면:

1. 다음으로 이동 `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. **[!UICONTROL 연결 수]** 필드 및/또는 **[!UICONTROL 활성 작업 시간 초과]** 필드에서 원하는 대로 번호를 변경합니다.

   **[!UICONTROL 연결 수]** 설정은 AEM에서 Dynamic Media 업로드를 위해 허용되는 최대 HTTP 연결 수를 제어합니다.일반적으로 미리 정의된 10개의 연결 값이면 충분합니다.

   **[!UICONTROL 활성 작업 시간 초과]** 설정은 업로드된 Dynamic Media 에셋이 배달 서버에 게시될 때까지 기다리는 시간을 결정합니다. 이 값은 기본적으로 2100초 또는 35분입니다.

   대부분의 경우 2100으로 설정하면 충분합니다.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. **[!UICONTROL 저장을 탭합니다.]**

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your AEM author environment to the AEM publish node. This workflow is necessary because the AEM publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to AEM publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the AEM publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the AEM publish node.

#### Using default asset filters for replication {#using-default-asset-filters-for-replication}

If you are using Dynamic Media for imaging and/or video, then you can use the default filters that we provide as-is. The following filters are active by default:

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Filter</strong></td>
   <td><strong>Mimetype</strong></td>
   <td><strong>Renditions</strong></td>
  </tr>
  <tr>
   <td>Dynamic Media Image Delivery</td>
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td>
   <td><p>Starts with <strong>image/</strong></p> <p>Contains <strong>application/</strong> and ends with <strong>set</strong>.</p> </td>
   <td>The out-of-the-box "filter-images" (applies to single images assets, including interactive images) and "filter-sets" (applies to Spin Sets, Image Sets, Mixed Media Sets, and Carousel Sets) will:
    <ul>
     <li>Exclude from replication the original image and static image renditions.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dynamic Media Video Delivery</td>
   <td>filter-video</td>
   <td>Starts with <strong>video/</strong></td>
   <td>The out-of-the-box "filter-video" will:
    <ul>
     <li>Exclude from replication the original video and static thumbnail renditions.<br /> <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Filters apply to mime types and cannot be path specific.

#### Customizing asset filters for replication {#customizing-asset-filters-for-replication}

1. In AEM, tap the AEM logo to access the global navigation console and tap the **[!UICONTROL Tools > General > CRXDE Lite]**.
1. In the left folder tree, navigate to `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` to review the filters.

   ![chlimage_1-17](assets/chlimage_1-2.png)

1. To define the Mime Type for the filter, you can locate the Mime Type as follows:

   In the left rail, expand `content > dam > <locate_your_asset> > jcr:content > metadata`, and then in the table, locate `dc:format`.

   The following graphic is an example of an asset's path to `dc:format`.

   ![chlimage_1-18](assets/chlimage_1-3.png)

   Notice that the `dc:format` for the asset `Fiji Red.jpg` is `image/jpeg`.

   To have this filter apply to all images, regardless of their format, set the value to `image/*` where `*` is a regular expression that is applied to all images of any format.

   To have the filter apply only to images of the type JPEG, enter a value of `image/jpeg`.

1. Define what renditions you want to include or exclude from replication.

   Characters that you can use to filter for replication include the following:

<table>
 <tbody>
  <tr>
   <td><strong>Character to use</strong></td>
   <td><strong>How it filters assets for replication</strong></td>
  </tr>
  <tr>
   <td>*</td>
   <td>Wildcard character<br /> </td>
  </tr>
  <tr>
   <td>+</td>
   <td>Includes assets for replication.</td>
  </tr>
  <tr>
   <td>-</td>
   <td>Excludes assets from replication.</td>
  </tr>
 </tbody>
</table>

   Navigate to `content/dam/<locate your asset>/jcr:content/renditions`.

   The following graphic is an example of an asset's renditions.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   If you only wanted to replicate the original, then you would enter `+original`.

   -->

