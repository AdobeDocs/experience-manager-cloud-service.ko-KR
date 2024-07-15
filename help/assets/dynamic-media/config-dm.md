---
title: Dynamic Media 구성 Cloud Service
description: Adobe Experience Manager as a Cloud Service에서 Dynamic Media을 구성하는 방법에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Configuration,Dynamic Media
role: Admin,User
exl-id: 8e07bc85-ef26-4df4-8e64-3c69eae91e11
source-git-commit: 26afff3a39a2a80c1f730287b99f3fb33bff0673
workflow-type: tm+mt
source-wordcount: '3811'
ht-degree: 2%

---

# Dynamic Media 구성 Cloud Service {#configuring-dynamic-media}

개발, 스테이징 및 라이브 프로덕션과 같은 다양한 환경에 Adobe Experience Manager을 사용하는 경우 이러한 각 환경에 대해 Dynamic Media Cloud Service을 구성합니다.

[Dynamic Media 회사 별칭 계정 구성](/help/assets/dynamic-media/dm-alias-account.md)도 참조하세요.

## Dynamic Media의 아키텍처 다이어그램 {#architecture-diagram-of-dynamic-media}

다음 아키텍처 다이어그램은 Dynamic Media의 작동 방식을 설명합니다.

새 아키텍처를 통해 Experience Manager은 기본 소스 자산을 담당하며 자산 처리 및 게시를 위해 Dynamic Media과 동기화합니다.

1. 기본 소스 자산이 Adobe Experience Manager as a Cloud Service에 업로드되면 Dynamic Media에 복제됩니다. 이때 Dynamic Media은 비디오 인코딩 및 이미지의 동적 변형과 같은 모든 에셋 처리 및 렌디션 생성을 처리합니다.
1. 렌디션이 생성되면 Experience Manager은 원격 Dynamic Media 렌디션에 안전하게 액세스하고 미리 볼 수 있습니다(Experience Manager as a Cloud Service as a Cloud Service 인스턴스로 다시 전송되는 바이너리가 없음).
1. 콘텐츠를 게시하고 승인할 준비가 되면 Dynamic Media 서비스를 트리거하여 콘텐츠를 게재 서버로 푸시하고 CDN(Content Delivery Network)에서 콘텐츠를 캐시합니다.

![chlimage_1-550](assets/chlimage_1-550.png)

>[!NOTE]
>
>다음 기능 목록을 사용하려면 Adobe Experience Manager - Dynamic Media과 함께 번들로 제공되는 기본 CDN을 사용해야 합니다. 이러한 기능에서는 다른 모든 사용자 지정 CDN이 지원되지 않습니다.
>
>* [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md)
>* [캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
>* [핫링크 보호](/help/assets/dynamic-media/hotlink-protection.md)
>* [컨텐츠의 HTTP/2 전달](/help/assets/dynamic-media/http2faq.md)
>* CDN 수준에서 URL 리디렉션
>* Akamai ChinaCDN(중국에서 최적의 전송을 위해)

<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading Experience Manager as a Cloud Service Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your Experience Manager as a Cloud Service instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Cloud Service에서 Dynamic Media 구성 만들기 {#configuring-dynamic-media-cloud-services}

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. Experience Manager as a Cloud Service 콘솔에서 Experience Manager as a Cloud Service 로고를 선택하여 글로벌 내비게이션 콘솔에 액세스합니다.
1. 콘솔 왼쪽에서 도구 아이콘을 선택한 다음 **[!UICONTROL Cloud Service > Dynamic Media 구성]**(으)로 이동합니다.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL 전역]**&#x200B;을(를) 선택합니다(**[!UICONTROL 전역]** 왼쪽에 있는 폴더 아이콘을 선택하지 마십시오). **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL Dynamic Media 구성 만들기]** 페이지에서 Dynamic Media 계정의 회사 관리자의 제목, Dynamic Media 계정 전자 메일 주소 및 암호를 입력한 다음 지역을 선택합니다. 이 정보는 프로비저닝 이메일에서 Adobe으로 제공됩니다. 이 이메일을 받지 못한 경우 Adobe 고객 지원 센터에 문의하십시오.
1. **[!UICONTROL Dynamic Media에 연결]**&#x200B;을 선택합니다.
1. **[!UICONTROL 암호 변경]** 대화 상자의 **[!UICONTROL 새 암호]** 필드에 8~25자로 구성된 새 암호를 입력합니다. 암호에는 다음 각 항목 중 하나 이상이 포함되어야 합니다.

   * 대문자
   * 소문자
   * 숫자
   * 특수 문자: `# $ & . - _ : { }`

   **[!UICONTROL 현재 암호]** 필드는 의도적으로 미리 채워져 있으며 상호 작용에서 숨겨집니다.

   필요한 경우 비밀번호 눈 아이콘을 선택하여 비밀번호를 표시하고 입력한 비밀번호의 철자를 확인할 수 있습니다. 암호를 숨기려면 아이콘을 다시 선택합니다.

1. **[!UICONTROL 암호 반복]** 필드에서 새 암호를 다시 입력한 다음 **[!UICONTROL 완료]**&#x200B;를 선택합니다.

   **[!UICONTROL Dynamic Media 구성 만들기]** 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장]**&#x200B;을 선택하면 새 암호가 저장됩니다.

   **[!UICONTROL 암호 변경]** 대화 상자에서 **[!UICONTROL 취소]**&#x200B;를 선택한 경우 만든 Dynamic Media 구성을 저장할 때 새 암호를 입력해야 합니다.

   [Dynamic Media 암호 변경](#change-dm-password)도 참조하세요.

1. 연결에 성공하면 다음을 설정할 수 있습니다.

   | 속성 | 설명 |
   |---|---|
   | 회사 | Dynamic Media 계정의 이름입니다.<br>**중요**: Cloud Service의 Dynamic Media 구성은 Experience Manager 인스턴스에서만 지원됩니다. 구성을 두 개 이상 추가하지 마십시오. Experience Manager 인스턴스의 여러 Dynamic Media 구성이 Adobe에서 지원되거나 권장되지 _않습니다_.<!-- CQDOC-19579 and CQDOC-19612 --><br>또한 [Dynamic Media 회사 별칭 계정 구성](/help/assets/dynamic-media/dm-alias-account.md)을 참조하십시오. |
   | 회사 루트 폴더 경로 | 회사의 루트 폴더 경로입니다. |
   | Assets 게시 | 다음 세 가지 옵션 중 하나를 선택할 수 있습니다.<br>**[!UICONTROL 즉시&#x200B;]**- 에셋이 업로드되면 시스템이 에셋을 수집하고 URL/임베드를 즉시 제공합니다. 에셋을 게시하는 데 필요한 사용자 개입이 없습니다.<br>**[!UICONTROL 활성화 시]** - URL/포함 링크가 제공되기 전에 먼저 자산을 명시적으로 게시해야 합니다.<br>**[!UICONTROL 선택적 Publish ]**- Assets은 보안 미리 보기용으로만 자동 게시됩니다. 또한 공개 도메인에서 제공하기 위해 DMS7에 게시하지 않고 Experience Manageras a Cloud Service 에 명시적으로 게시할 수도 있습니다. 향후에 이 옵션은 자산을 Experience Manageras a Cloud Service 에 게시하고 상호 배타적으로 자산을 Dynamic Media에 게시합니다. 즉, 스마트 자르기 또는 동적 변환과 같은 기능을 사용할 수 있도록 자산을 DMS7에 게시할 수 있습니다. 또는 Experience Manageras a Cloud Service 에서만 자산을 미리 보기 위해 게시할 수 있습니다. 이러한 동일한 자산은 공개 도메인에서 제공하기 위해 DMS에 게시되지 않습니다. |
   | 보안 미리 보기 서버 | 보안 변환 미리 보기 서버에 대한 URL 경로를 지정할 수 있습니다. 즉, 렌디션이 생성되면 Experience Manager이 원격 Dynamic Media 렌디션에 안전하게 액세스하고 미리 볼 수 있습니다(Experience Manager as a Cloud Service as a Cloud Service 인스턴스로 바이너리가 다시 전송되지 않음).Adobe <br>회사 서버나 특수 서버를 사용할 수 있는 특별한 방법이 없으면 이 설정을 지정된 대로 두는 것이 좋습니다. |
   | 모든 컨텐츠 동기화 | 기본적으로 선택됩니다. Dynamic Media 동기화에서 자산을 선택적으로 포함하거나 제외하려면 이 옵션을 선택 취소합니다. 이 옵션을 선택 해제하면 다음 두 가지 Dynamic Media 동기화 모드 중에서 선택할 수 있습니다.<br>**[!UICONTROL Dynamic Media 동기화 모드]**<br>**[!UICONTROL 기본적으로 활성화&#x200B;]**- 제외를 위해 폴더를 표시하지 않는 한 구성은 기본적으로 모든 폴더에 적용됩니다. <!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL 기본적으로 비활성화됨]** - 선택한 폴더를 Dynamic Media에 동기화하도록 명시적으로 표시할 때까지 구성이 폴더에 적용되지 않습니다.<br>선택한 폴더를 Dynamic Media에 동기화하도록 표시하려면 자산 폴더를 선택한 다음 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 선택합니다. **[!UICONTROL 세부 정보]** 탭의 **[!UICONTROL Dynamic Media 동기화 모드]** 드롭다운 목록에서 다음 세 가지 옵션 중 하나를 선택하십시오. 완료되면 **[!UICONTROL 저장]**&#x200B;을 선택합니다. _다음 세 가지 옵션은 이전에&#x200B;**모든 콘텐츠 동기화**를 선택한 경우 사용할 수 없습니다._ 또한 [Dynamic Media의 폴더 수준에서 선택적 Publish 작업](/help/assets/dynamic-media/selective-publishing.md)을 참조하십시오.<br>**[!UICONTROL 상속됨&#x200B;]**- 폴더에 명시적 동기화 값이 없습니다. 대신 폴더는 상위 폴더 중 하나 또는 클라우드 구성의 기본 모드에서 동기화 값을 상속합니다. 상속된 의 자세한 상태는 도구 설명을 통해 표시됩니다.<br>**[!UICONTROL 하위 폴더에 대해 사용]** - Dynamic Media에 동기화하려면 이 하위 트리의 모든 항목을 포함하십시오. 폴더별 설정은 클라우드 구성의 기본 모드를 재정의합니다.<br>**[!UICONTROL 하위 폴더에 대해 사용 안 함&#x200B;]**- 이 하위 트리의 모든 항목을 Dynamic Media으로 동기화하지 못하도록 제외합니다. |

   >[!NOTE]
   >
   >There is no support for versioning in Dynamic Media. 또한 지연된 활성화는 Dynamic Media 구성 편집 페이지의 **[!UICONTROL Publish Assets]**&#x200B;이(가) **[!UICONTROL 활성화 시]**(으)로 설정된 경우에만 적용됩니다. 그런 다음 에셋이 처음 활성화될 때까지만 을 선택합니다.
   >
   >
   >자산이 활성화되면 모든 업데이트가 즉시 S7 Delivery에 라이브로 게시됩니다.

   ![dynamicmediaconfiguration2updated](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다. 새 Dynamic Media 암호 및 구성이 저장됩니다. 대신 **[!UICONTROL 취소]**&#x200B;를 선택한 경우 암호가 업데이트되지 않습니다.
1. **[!UICONTROL Dynamic Media 구성]** 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 선택하여 구성을 시작합니다.

   >[!IMPORTANT]
   >
   >새 Dynamic Media 구성의 설정을 마치면 Experience Manager as a Cloud Service의 받은 편지함 내에 상태 알림을 받게 됩니다.
   >
   >이 받은 편지함 알림은 구성이 성공했는지 여부를 알려줍니다.
   > 자세한 내용은 [새 Dynamic Media 구성 문제 해결](#troubleshoot-dm-config) 및 [받은 편지함](/help/sites-cloud/authoring/inbox.md)을 참조하세요.

1. Dynamic Media 컨텐츠가 게시되기 전에 안전하게 미리 보기 위해 Experience Manageras a Cloud Service 은 토큰 기반 유효성 검사를 사용하므로 Experience Manager 작성자는 기본적으로 Dynamic Media 컨텐츠를 미리 봅니다. 그러나 사용자가 안전하게 컨텐츠를 미리 볼 수 있도록 IP를 *허용 목록*&#x200B;할 수 있습니다. Experience Manager Publish에서 이 작업을 설정하려면 [이미지 서버에 대한 as a Cloud Service Dynamic Media 설정 구성 - 보안 탭](/help/assets/dynamic-media/dm-publish-settings.md#security-tab)을 참조하십시오. <!-- To securely preview Dynamic Media content before it gets published, you must "allowlist" the Experience Manager as a Cloud Service author instance to connect to Dynamic Media. To set up this action, do the following: -->

<!--
    * Open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account. Your credentials and sign-in details were provided by Adobe at the time of provisioning. If you do not have this information, contact Adobe Customer Support.
    * On the navigation bar near the upper right corner of the page, go to **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**.
    * On the Image Server Publish page, in the **[!UICONTROL Publish Context]** drop-down list, select **[!UICONTROL Test Image Serving]**.
    * For the Client Address Filter, select **[!UICONTROL Add]**.
    * To enable (turn on) the address, select the check box, then enter the IP address of the Experience Manager Author instance (not Dispatcher IP).
    * Select **[!UICONTROL Save]**. -->

이제 기본 구성이 완료되었습니다. Dynamic Media을 사용할 준비가 되었습니다.

ACL(액세스 제어 목록) 권한 사용과 같이 구성을 추가로 사용자 지정하려면 [Dynamic Media에서 고급 설정 구성](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode)에 있는 작업을 선택적으로 완료할 수 있습니다.

### 새 Dynamic Media 구성 문제 해결 {#troubleshoot-dm-config}

새 Dynamic Media 구성의 설정을 마치면 Experience Manager as a Cloud Service의 받은 편지함 내에 상태 알림을 받게 됩니다. 이 알림은 받은 편지함의 다음 각 이미지에 표시된 대로 구성이 성공했는지 여부를 알려줍니다.

![받은 편지함 Experience Manager 성공](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![받은 편지함 Experience Manager 실패](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

[받은 편지함](/help/sites-cloud/authoring/inbox.md)도 참조하세요.

**새 Dynamic Media 구성 문제를 해결하려면:**

1. Experience Manager as a Cloud Service 페이지의 오른쪽 상단 모서리 근처에서 종 아이콘을 선택한 다음 **[!UICONTROL 모두 보기]**&#x200B;를 선택합니다.
1. 받은 편지함 페이지에서 성공 알림을 선택하여 구성의 상태 및 로그에 대한 개요를 읽습니다.

   구성이 실패한 경우 다음 스크린샷과 유사한 실패 알림을 선택합니다.

   ![Dynamic Media 설치 실패](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. **[!UICONTROL DMSETUP]** 페이지에서 오류를 설명하는 구성 세부 정보를 검토하십시오. 특히 모든 오류 메시지 또는 오류 코드를 기록합니다. 이 정보는 Adobe 고객 지원 센터에 문의하십시오.

   ![Dynamic Media 설정 페이지](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### Dynamic Media 암호 변경 {#change-dm-password}

Dynamic Media의 암호 만료는 현재 시스템 날짜로부터 100년으로 설정되어 있습니다.

암호에는 다음 각 항목 중 하나 이상이 포함되어야 합니다.

* 대문자
* 소문자
* 숫자
* 특수 문자: `# $ & . - _ : { }`

필요한 경우 비밀번호 눈 아이콘을 선택하여 비밀번호를 표시하고 입력한 비밀번호의 철자를 확인할 수 있습니다. 암호를 숨기려면 아이콘을 다시 선택합니다.

**[!UICONTROL Dynamic Media 구성 편집]** 페이지의 오른쪽 상단에서 **[!UICONTROL 저장]**&#x200B;을 선택하면 변경된 암호가 저장됩니다.

1. Experience Manager as a Cloud Service 콘솔에서 Experience Manager as a Cloud Service 로고를 선택하여 글로벌 내비게이션 콘솔에 액세스합니다.
1. 콘솔 왼쪽에서 도구 아이콘을 선택한 다음 **[!UICONTROL Cloud Service > Dynamic Media 구성]**(으)로 이동합니다.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL 전역]**&#x200B;을(를) 선택합니다. **[!UICONTROL global]** 왼쪽에 있는 폴더 아이콘을 선택하지 마십시오. 그런 다음 **[!UICONTROL 편집]**&#x200B;을 선택합니다.
1. **[!UICONTROL Dynamic Media 구성 편집]** 페이지의 **[!UICONTROL 암호]** 필드 바로 아래에서 **[!UICONTROL 암호 변경]**&#x200B;을 선택합니다.
1. **[!UICONTROL 암호 변경]** 대화 상자에서 다음 작업을 수행합니다.

   * **[!UICONTROL 새 암호]** 필드에 새 암호를 입력합니다.

     **[!UICONTROL 현재 암호]** 필드는 의도적으로 미리 채워져 있으며 상호 작용에서 숨겨집니다.

   * **[!UICONTROL 암호 반복]** 필드에서 새 암호를 다시 입력한 다음 **[!UICONTROL 완료]**&#x200B;를 선택합니다.

1. **[!UICONTROL Dynamic Media 구성 편집]** 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장]**&#x200B;을 선택한 다음 **[!UICONTROL 확인]**&#x200B;을 선택합니다.

## (선택 사항) Dynamic Media에서 고급 설정 구성{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Dynamic Media의 구성 및 설정을 추가로 사용자 지정하거나 성능을 최적화하려면 다음 _옵션_ 작업 중 하나 이상을 완료할 수 있습니다.

* [(선택 사항) Dynamic Media에서 ACL 권한 활성화](#optional-enable-acl)
* [(선택 사항) Dynamic Media 설정 설정 및 구성](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(선택 사항) Dynamic Media 성능 조정](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (선택 사항) Dynamic Media에서 액세스 제어 목록 권한 활성화 {#optional-enable-acl}

AEM에서 Dynamic Media을 실행할 때 현재 PlatformServerServlet에 대한 ACL(액세스 제어 목록) 권한을 확인하지 않고 `/is/image`개의 요청을 보안 미리 보기 이미지 제공에 전달합니다. 그러나 ACL 권한을 _활성화_&#x200B;할 수 있습니다. 승인된 `/is/image` 요청을 전달합니다. 사용자에게 에셋에 액세스할 권한이 없는 경우 &quot;403 - 금지됨&quot; 오류가 표시됩니다.

**Dynamic Media에서 ACL 권한을 사용하려면**

1. Experience Manager에서 **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**&#x200B;로 이동합니다.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 페이지에 새 브라우저 탭이 열립니다.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. 페이지에서 _Adobe CQ Scene7 PlatformServer_(으)로 스크롤합니다.

1. 이름 오른쪽에서 연필 아이콘(**[!UICONTROL 구성 값 편집]**)을 선택합니다.

1. **com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.name** 페이지에서 다음 두 가지 설정에 대한 확인란을 선택합니다.

   * `com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.cache.enable.name` - 활성화되면 이 설정은 저장할 2분(기본값) 동안 권한 결과를 캐시합니다.
   * `com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.validate.userAccess.name` - 활성화되면 이 설정은 Dynamic Media 이미지 서버를 통해 에셋을 미리 보는 동안 사용자의 액세스를 확인합니다.

   ![Dynamic Media - Scene7 모드에서 액세스 제어 목록 설정 사용](/help/assets/dynamic-media/assets/acl.png)

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### (선택 사항) Dynamic Media 설정 설정 및 구성 {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Dynamic Media Classic 사용자 인터페이스를 사용하여 Dynamic Media 설정을 변경합니다.

<!-- Some of the tasks above require that you open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account. -->

설정 및 구성 작업에는 다음이 포함됩니다.

* [이미지 서버에 대한 Dynamic Media Publish 설정 구성](#publishing-setup-for-image-server)
* [Dynamic Media 일반 설정 구성](#configuring-application-general-settings)
* [색상 관리 구성](#configuring-color-management)
* [지원되는 형식의 MIME 유형 편집](#editing-mime-types-for-supported-formats)
* [지원되지 않는 형식에 대한 MIME 유형 추가](#adding-mime-types-for-unsupported-formats)
<!-- OBSOLETE BUT LEAVE FOR POSSIBLE FUTURE* [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### 이미지 서버에 대한 Dynamic Media Publish 설정 구성 {#publishing-setup-for-image-server}

Dynamic Media Publish 설정 페이지는 Adobe Dynamic Media 서버에서 웹 사이트 또는 애플리케이션으로 에셋을 전달하는 방법을 결정하는 기본 설정을 구성합니다.

[이미지 서버에 대한 Dynamic Media Publish 설치 구성](/help/assets/dynamic-media/dm-publish-settings.md)을 참조하십시오.

#### Dynamic Media 일반 설정 구성 {#configuring-application-general-settings}

Dynamic Media **[!UICONTROL Publish 서버 이름]** URL과 **[!UICONTROL 원본 서버 이름]** URL을 구성합니다. 특정 사용 사례에 따라 **[!UICONTROL 응용 프로그램에 업로드]** 설정 및 **[!UICONTROL 기본 업로드 옵션]**&#x200B;을 지정할 수도 있습니다.

[Dynamic Media 일반 설정 구성](/help/assets/dynamic-media/dm-general-settings.md)을 참조하십시오.

#### 색상 관리 구성 {#configuring-color-management}

Dynamic Media 색상 관리를 사용하면 올바른 에셋에 색상을 지정할 수 있습니다. 색상 수정을 사용하면 수집된 에셋의 색상 공간(RGB, CMYK, 회색) 및 임베드된 색상 프로파일이 유지됩니다. 동적 렌디션을 요청하면 CMYK, RGB 또는 회색 출력을 사용하여 이미지 색상이 대상 색상 공간으로 수정됩니다.

[이미지 사전 설정 구성](/help/assets/dynamic-media/managing-image-presets.md)을 참조하십시오.

이미지 요청 시 색상 교정을 활성화하기 위한 기본 색상 속성을 구성하려면 다음과 같이 하십시오.

1. [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 프로비전하는 동안 제공된 자격 증명을 사용하여 계정에 로그인합니다.
1. **[!UICONTROL 설정 > 응용 프로그램 설정]**(으)로 이동합니다.
1. Expand the **[!UICONTROL Publish Setup]** area and select **[!UICONTROL Image Server]**. Set **[!UICONTROL Publish Context]** to **[!UICONTROL Image Serving]** when setting defaults for publish instances.
1. 변경해야 하는 속성(예: **[!UICONTROL 색상 관리 특성]** 영역의 속성)으로 스크롤합니다.
다음과 같은 색상 교정 속성을 설정할 수 있습니다.

   | 속성 | 설명 |
   |---|---|
   | CMYK 기본 색상 공간 | 기본 CMYK 색상 프로파일의 이름입니다. |
   | 회색 음영 기본 색상 공간 | 기본 회색 색상 프로파일의 이름입니다. |
   | RGB 기본 색상 공간 | 기본 RGB 색상 프로필의 이름입니다. |
   | 색상 변환 렌더링 의도 | 렌더링 의도를 지정합니다. 허용되는 값은 다음과 같습니다. **[!UICONTROL perceptual]**, **[!UICONTROL 상대 색도계]**, **[!UICONTROL 채도]**, **[!UICONTROL 절대 색도계]**. Adobe은 **[!UICONTROL relative]**&#x200B;을(를) 기본값으로 권장합니다. |

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

For example, you could set the **[!UICONTROL RGB Default Color Space]** to *sRGB*, and **[!UICONTROL CMYK Default Color Space]** to *WebCoated*.

이렇게 하면 다음 작업이 수행됩니다.

* RGB 및 CMYK 이미지에 대해 색상 교정을 활성화합니다.
* 색상 프로파일이 없는 RGB 이미지는 *sRGB* 색상 공간에 있는 것으로 간주됩니다.
* 색상 프로필이 없는 CMYK 이미지는 *WebCoated* 색상 공간에 있는 것으로 간주됩니다.
* RGB 출력을 반환하고 *sRGB* 색상 공간으로 반환하는 동적 변환입니다.
* CMYK 출력을 반환하고 *WebCoated* 색상 공간으로 반환하는 동적 변환입니다.

#### 지원되는 형식의 MIME 유형 편집 {#editing-mime-types-for-supported-formats}

Dynamic Media에서 처리하는 자산 유형을 정의하고 고급 자산 처리 매개 변수를 사용자 지정할 수 있습니다. 예를 들어, 다음을 수행할 자산 처리 매개 변수를 지정할 수 있습니다.

* Adobe PDF을 eCatalog 자산으로 변환합니다.
* 개인화를 위해 Adobe Photoshop PSD 문서(.personalization)를 배너 템플릿 자산으로 변환합니다.
* Adobe Illustrator 파일(.AI) 또는 Adobe Photoshop Encapsulated PostScript® 파일(.EPS)을 래스터화합니다.
* [비디오 프로필](/help/assets/dynamic-media/video-profiles.md) 및 [이미지 프로필](/help/assets/dynamic-media/image-profiles.md)을 사용하여 각각 비디오 및 이미지 처리를 정의할 수 있습니다.

[자산 업로드](/help/assets/add-assets.md)를 참조하세요.

**지원되는 형식의 MIME 형식을 편집하려면:**

1. 제품 관리자로 Experience Manageras a Cloud Service 에 로그인합니다.
1. Experience Manager as a Cloud Service 콘솔에서 Experience Manager as a Cloud Service 로고를 선택하고 **[!UICONTROL 일반 > CRXDE Lite]**(으)로 이동합니다.

   CRXDE Lite 액세스 권한이 없는 경우 [CRXDE Lite 사용](/help/implementing/developing/tools/crxde.md)을 참조하세요.

1. 왼쪽 레일에서 다음과 같이 이동합니다.

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![MIME 유형](assets/mimetypes.png)

1. mimeTypes 폴더에서 MIME 유형을 선택합니다.
1. CRXDE Lite 페이지 오른쪽의 아래쪽에서 다음을 수행합니다.

   * **[!UICONTROL enabled]** 필드를 두 번 선택합니다. 기본적으로 모든 에셋 MIME 유형이 활성화됩니다(**[!UICONTROL true]**(으)로 설정). 즉, 에셋이 처리를 위해 Dynamic Media에 동기화됩니다. 이 자산 MIME 형식을 처리 대상에서 제외하려면 이 설정을 **[!UICONTROL false]**(으)로 변경하십시오.

   * 연결된 텍스트 필드를 열려면 **[!UICONTROL jobParam]**&#x200B;을(를) 두 번 선택하십시오. 특정 MIME 유형에 사용할 수 있는 허용되는 처리 매개 변수 값의 목록은 [지원되는 MIME 유형](/help/assets/file-format-support.md)을 참조하십시오.

1. 다음 중 하나를 수행하십시오.
   * 더 많은 MIME 유형을 편집하려면 3-4단계를 반복합니다.
   * CRXDE Lite 페이지의 메뉴 표시줄에서 **[!UICONTROL 모두 저장]**&#x200B;을 선택합니다.

1. Experience Manager as a Cloud Service 왼쪽 상단 모서리에서 **[!UICONTROL CRXDE Lite]**&#x200B;을(를) 선택하여 페이지로 돌아갑니다.

#### 지원되지 않는 형식에 대한 MIME 유형 추가 {#adding-mime-types-for-unsupported-formats}

Experience Manager Assets에서 지원되지 않는 형식에 대한 사용자 지정 MIME 유형을 추가할 수 있습니다. CRXDE Lite에 추가한 새 노드가 Experience Manager에 의해 삭제되지 않도록 하려면 MIME 형식을 `image_` 앞으로 이동하십시오. 또한 활성화된 값이 **[!UICONTROL false]**(으)로 설정되어 있는지 확인하십시오.

**지원되지 않는 형식의 MIME 형식을 추가하려면:**

1. 제품 관리자로 Experience Manageras a Cloud Service 에 로그인합니다.
1. Experience Manager as a Cloud Service 도구 > 웹 콘솔&#x200B;**[!UICONTROL 로 이동합니다]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성]** 페이지에 새 브라우저 탭이 열립니다.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. On the page, scroll down to the name *Adobe CQ Scene7 Asset MIME type Service* as seen the following screenshot. 이름 오른쪽에서 **[!UICONTROL 구성 값 편집]**&#x200B;을 선택합니다(연필 아이콘).

   ![구성 값 편집](assets/2019-08-02_16-44-56.png)

1. **Adobe CQ Scene7 자산 MIME 유형 서비스** 페이지에서 더하기 기호 아이콘 &lt;+>을 선택합니다. 표에서 새 MIME 유형을 추가할 더하기 기호를 선택하는 위치는 사소합니다.

   ![Adobe CQ Scene7 에셋 Mime 유형 서비스](assets/2019-08-02_16-27-27.png)

1. 방금 추가한 빈 텍스트 필드에 `DWG=image/vnd.dwg`을(를) 입력하십시오.

   `DWG=image/vnd.dwg` MIME 형식은 샘플용으로만 사용됩니다. 여기에 추가하는 MIME 유형은 지원되지 않는 다른 형식일 수 있습니다.

   ![DWG mime 유형 추가](assets/2019-08-02_16-36-36.png)

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   이제 Adobe Experience Manager 웹 콘솔 구성 페이지가 열려 있는 브라우저 탭을 닫을 수 있습니다.

1. 열려 있는 Experience Manager as a Cloud Service 콘솔이 있는 브라우저 탭으로 돌아갑니다.
1. Experience Manager as a Cloud Service 도구 > 도구&#x200B;**[!UICONTROL 일반 > CRXDE Lite]**&#x200B;로 이동합니다.

   CRXDE Lite 액세스 권한이 없는 경우 [CRXDE Lite 사용](/help/implementing/developing/tools/crxde.md)을 참조하세요.

   ![도구 > 일반 > CRXDE Lite](assets/2019-08-02_16-55-41.png)

1. 왼쪽 레일에서 다음과 같이 이동합니다.

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. MIME 유형 `image_vnd.dwg`을(를) 다음 스크린샷과 같이 트리의 `image_` 바로 위에 끌어다 놓습니다.

   ![CRXDE Lite에서 DWG 파일 편집](assets/crxdelite_cqdoc-14627.png)

1. MIME 형식 `image_vnd.dwg`이(가) 여전히 선택된 상태에서 **[!UICONTROL 속성]** 탭의 **[!UICONTROL enabled]** 행의 **[!UICONTROL 값]** 열 헤더 아래에서 값을 두 번 선택합니다. **[!UICONTROL 값]** 드롭다운 목록이 열립니다.
1. 필드에 `false`을(를) 입력하거나 드롭다운 목록에서 **[!UICONTROL false]**&#x200B;을(를) 선택하십시오.

   ![CRXDE Lite에서 MIME 유형 편집](assets/2019-08-02_16-60-30.png)

1. CRXDE Lite 페이지의 왼쪽 상단 모서리 근처에서 **[!UICONTROL 모두 저장]**&#x200B;을 선택합니다.

### (선택 사항) Dynamic Media 성능 조정 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Dynamic Media Adobe <!--(with `dynamicmedia_scene7` run mode)-->이(가) 원활하게 실행되도록 하려면 다음 동기화 성능/확장성 미세 조정 팁을 권장합니다.

* [다른 파일 형식을 처리하기 위해 미리 정의된 작업 매개 변수를 업데이트합니다](#update-job-para).
* [사전 정의된 Granite 워크플로우 큐(비디오 자산) 작업자 스레드 업데이트](#update-granite-workflow-queue-worker-threads-video)
* [미리 정의된 Granite 임시 워크플로 큐(이미지 및 비비디오 자산) 작업자 스레드를 업데이트합니다](#update-granite-transient-workflow-queue-worker-threads-images).
* [Dynamic Media Classic(Scene7) 서버에 대한 최대 업로드 연결 업데이트](#update-max-s7-upload-connections).

#### 다양한 파일 형식 처리를 위해 사전 정의된 작업 매개 변수 업데이트 {#update-job-para}

파일을 업로드할 때 처리 속도를 높이기 위해 작업 매개 변수를 조정할 수 있습니다. 예를 들어 PSD 파일을 업로드하지만 템플릿으로 처리하지 않으려는 경우 레이어 추출을 false(꺼짐)로 설정할 수 있습니다. 이 경우 튜닝된 작업 매개 변수는 다음과 같이 표시됩니다. `process=None&createTemplate=false`.

템플릿 만들기를 켜려면 다음 매개 변수를 사용합니다. `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- THIS PARAGRAPH WAS REPLACED WITH THE TWO PARAGRAPHS DIRECTLY ABOVE BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe은 PDF, PostScript® 및 PSD 파일에 대해 다음 &quot;조정된&quot; 작업 매개 변수를 사용할 것을 권장합니다.

| 파일 유형 | 권장 작업 매개 변수 |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

이러한 매개 변수를 업데이트하려면 [지원되는 형식에 대한 MIME 형식 편집](#editing-mime-types-for-supported-formats)을 참조하십시오.

[지원되지 않는 형식에 대한 MIME 형식 추가](#adding-mime-types-for-unsupported-formats)도 참조하세요.

#### 사전 정의된 Granite 워크플로우 큐(비디오 자산) 작업자 스레드 업데이트 {#update-granite-workflow-queue-worker-threads-video}

Granite Workflow 큐는 임시 워크플로우에 사용됩니다. Dynamic Media에서는 **[!UICONTROL Dynamic Media 인코딩 비디오]** 워크플로우로 비디오를 처리하는 데 사용되었습니다.

>[!NOTE]
>
>이 작업을 완료하려면 Experience Manageras a Cloud Service 에 제품 관리자로 로그인해야 합니다.

OSGi 액세스 권한이 없는 경우 [OSGi 구성](/help/implementing/developing/components/overview.md#osgi-configuration)을 참조하십시오.

**미리 정의된 Granite 워크플로 큐(비디오 자산) 작업자 스레드를 업데이트하려면:**

1. `https://<server>/system/console/configMgr`(으)로 이동하여 **큐: Granite 워크플로 큐**&#x200B;를 검색합니다.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. **[!UICONTROL 최대 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   기본적으로 최대 병렬 작업 수는 사용 가능한 CPU 코어 수에 따라 달라집니다. 예를 들어, 4코어 서버에서는 두 개의 작업자 스레드를 할당합니다. (0.0과 1.0 사이의 값은 비율을 기반으로 하거나, 1보다 큰 숫자는 작업자 스레드 수를 할당합니다.)

   대부분의 사용 사례에서는 0.5 기본 설정으로 충분합니다.

   ![작업 처리 큐 구성](assets/chlimage_1-1.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

#### 미리 정의된 Granite 임시 워크플로우 큐 작업자 스레드 업데이트 {#update-granite-transient-workflow-queue-worker-threads-images}

Granite Transit Workflow 큐는 **[!UICONTROL DAM 자산 업데이트]** 워크플로에 사용됩니다. Dynamic Media에서 이미지 및 비비디오 에셋 수집 및 처리에 사용됩니다.

>[!NOTE]
>
>이 작업을 완료하려면 Experience Manageras a Cloud Service 에 제품 관리자로 로그인해야 합니다.

**미리 정의된 Granite 임시 워크플로 큐 작업자 스레드를 업데이트하려면:**

1. `http://<host>:<port>/system/console/configMgr`의 **Adobe Experience Manager 웹 콘솔 구성**(으)로 이동
1. **큐: Granite Transient 워크플로 큐**&#x200B;를 검색합니다.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. **[!UICONTROL 최대 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   **[!UICONTROL 최대 병렬 작업]**&#x200B;을 늘려 Dynamic Media에 대량의 파일을 업로드할 수 있습니다. 정확한 값은 하드웨어 용량에 따라 다릅니다. 초기 마이그레이션 또는 일회성 일괄 업로드와 같은 특정 시나리오에서는 큰 값을 사용할 수 있습니다. 그러나 큰 값(예: 코어 수의 2배)을 사용하면 다른 동시 활동에 부정적인 영향을 줄 수 있습니다. 따라서 특정 사용 사례를 기반으로 값을 테스트하고 조정합니다.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

#### Dynamic Media Classic(Scene7) 서버에 대한 최대 업로드 연결 업데이트 {#update-max-s7-upload-connections}

Dynamic Media Classic(Scene7) 업로드 연결 설정은 Experience Manager 에셋을 Dynamic Media Classic 서버에 동기화합니다.

>[!NOTE]
>
>이 작업을 완료하려면 Experience Manageras a Cloud Service 에 제품 관리자로 로그인해야 합니다.

**Dynamic Media Classic(Scene7) 서버에 대한 최대 업로드 연결을 업데이트하려면:**

1. `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`(으)로 이동
1. **[!UICONTROL 연결 수]** 필드 또는 **[!UICONTROL 활성 작업 시간 초과]** 필드 또는 두 필드 모두에서 원하는 대로 수를 변경합니다.

   **[!UICONTROL 연결 수]** 설정은 Dynamic Media 업로드에 대한 Experience Manager에 허용된 최대 HTTP 연결 수를 제어합니다. 일반적으로 10개의 연결로 미리 정의된 값으로 충분합니다.

   **[!UICONTROL 활성 작업 시간 초과]** 설정은 업로드된 Dynamic Media 자산이 게재 서버에 게시될 대기 시간을 결정합니다. 이 값은 기본적으로 2100초 또는 35분입니다.

   대부분의 사용 사례에서는 2100으로 설정하면 충분합니다.

   ![Adobe Scene7 업로드 서비스](assets/chlimage_1-2.jpeg)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your Experience Manager as a Cloud Service author environment to the Experience Manager as a Cloud Service publish node. This workflow is necessary because the Experience Manager as a Cloud Service publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to Experience Manager as a Cloud Service publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the Experience Manager as a Cloud Service publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the Experience Manager as a Cloud Service publish node.

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

1. In Experience Manager as a Cloud Service, select the Experience Manager as a Cloud Service logo to access the global navigation console and select the **[!UICONTROL Tools > General > CRXDE Lite]**.
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
