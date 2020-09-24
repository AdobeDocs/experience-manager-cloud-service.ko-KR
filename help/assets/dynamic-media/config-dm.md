---
title: Dynamic Media Cloud Service 구성
description: Adobe Experience Manager Cloud Service에서 다이내믹 미디어를 구성하는 방법에 대한 정보입니다.
translation-type: tm+mt
source-git-commit: e2efa569a216e2156425a5ad596ec90a75b39e58
workflow-type: tm+mt
source-wordcount: '5124'
ht-degree: 0%

---


# Dynamic Media Cloud Service 구성 정보 {#configuring-dynamic-media-scene-mode}

개발 환경, 스테이징용 환경 및 라이브 프로덕션용 환경 등과 같은 다른 환경에 대해 설정한 Adobe Experience Manager을 사용하는 경우 해당 환경 각각에 대해 Dynamic Media Cloud Services을 구성해야 합니다.

## 다이내믹 미디어 아키텍처 다이어그램 {#architecture-diagram-of-dynamic-media-scene-mode}

다음 아키텍처 다이어그램에서는 다이내믹 미디어가 작동하는 방식을 설명합니다.

새로운 아키텍처로 AEM은 기본 소스 자산을 담당하고 에셋 처리 및 게시를 위해 Dynamic Media와 동기화합니다.

1. 기본 소스 자산이 AEM에 업로드되면 Dynamic Media에 복제됩니다. 이때 Dynamic Media는 이미지의 비디오 인코딩 및 동적 변형과 같은 모든 자산 처리 및 변환 생성을 처리합니다.
1. 변환이 생성되면 AEM은 안전하게 원격 Dynamic Media 변환에 액세스하고 미리 볼 수 있습니다(이진 파일은 AEM 인스턴스로 다시 전송되지 않음).
1. 컨텐츠가 게시 및 승인될 준비가 되면, Dynamic Media 서비스가 컨텐츠를 전달 서버로 푸시하고 CDN의 컨텐츠를 캐시하도록 트리거합니다.

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

## Dynamic Media Cloud Service 구성 {#configuring-dynamic-media-cloud-services}

**Dynamic Media Cloud Service을 구성하기 전**:Dynamic Media 자격 증명으로 프로비저닝 이메일을 받은 후 Dynamic Media Classic에 [로그인해야](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) 암호를 변경할 수 있습니다. 프로비저닝 이메일에 제공된 암호는 시스템에서 생성되며 임시 암호에만 사용됩니다. Dynamic Media Cloud Service이 올바른 자격 증명으로 설정되도록 암호를 업데이트해야 합니다.

다이내믹 미디어 클라우드 서비스를 구성하려면:

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다.
1. 콘솔 왼쪽의 **[!UICONTROL 도구]** 머리글 아래에서 **[!UICONTROL Cloud Services > Dynamic Media 구성을 누릅니다]**.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL 글로벌]** ( **[!UICONTROL 전역]**&#x200B;왼쪽에 있는 폴더 아이콘을 탭하거나 선택하지 않음)을 탭한 다음 **[!UICONTROL 만들기를]**&#x200B;탭합니다.
1. [다이내믹 미디어 구성 만들기] 페이지에서 제목과 Dynamic Media 계정 이메일 주소, 암호를 입력한 다음 지역을 선택합니다. Adobe이 제공 이메일에 제공합니다. 수신하지 못한 경우 지원 센터에 문의하십시오.
1. Click **[!UICONTROL Connect to Dynamic Media]**.

   >[!NOTE]
   >
   >Dynamic Media 자격 증명으로 프로비저닝 이메일을 받은 후 Dynamic Media Classic에 [로그인하여](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) 암호를 변경하십시오. 프로비저닝 이메일에 제공된 암호는 시스템에서 생성되며 임시 암호에만 사용됩니다. Dynamic Media 클라우드 서비스가 올바른 자격 증명으로 설정되도록 암호를 업데이트해야 합니다.

1. 연결이 성공하면 다음을 설정할 수 있습니다.

   * **[!UICONTROL 회사]** - Dynamic Media 계정의 이름입니다. 다양한 하위 브랜드, 사업부 또는 다른 스테이징/프로덕션 환경에 대해 여러 개의 Dynamic Media 계정이 있을 수 있습니다.

   * **[!UICONTROL 회사 루트 폴더 경로]**

   * **[!UICONTROL 자산 게시]** - 다음 세 가지 옵션 중에서 선택할 수 있습니다.
      * **[!UICONTROL 에셋이 업로드되면 시스템이 에셋을 인제스트하고 URL/포함을 즉시 제공함을 의미합니다]** . 자산을 게시하는 데 필요한 사용자 개입은 없습니다.
      * **[!UICONTROL 활성화]** 시 URL/포함 링크를 제공하기 전에 먼저 자산을 명시적으로 게시해야 함을 의미합니다.
      * **[!UICONTROL 선택적 게시]** (Selective Publish)는 에셋이 보안 미리 보기만을 위해 자동으로 게시되며 공개 도메인에 전달을 위해 DMS7에 게시하지 않고도 AEM에 명시적으로 게시할 수 있음을 의미합니다. 앞으로 Adobe은 상호 배타적인 AEM에 자산을 게시하고 Dynamic Media에 자산을 게시하는 이 옵션을 개선하게 됩니다. 즉, DMS7에 자산을 게시하여 스마트 자르기 또는 동적 표현물과 같은 기능을 사용할 수 있습니다. 또는 미리 보기 전용 AEM에서만 에셋을 게시할 수 있습니다.동일한 에셋은 공용 도메인에 전달되기 위해 DMS7에 게시되지 않습니다.
   * **[!UICONTROL 보안 미리 보기 서버]** - 보안 변환 미리 보기 서버에 대한 URL 경로를 지정할 수 있습니다. 즉, 변환이 생성된 후 AEM은 안전하게 원격 Dynamic Media 변환에 액세스하고 미리 볼 수 있습니다(이진 파일은 AEM 인스턴스로 다시 전송되지 않음).
회사 서버 또는 특수 서버를 사용할 특별한 계획이 없는 경우 이 설정을 지정한 대로 유지하는 것이 좋습니다.

   * **[!UICONTROL 모든 콘텐츠]** 동기화 - 기본적으로 선택되어 있습니다. Dynamic Media와의 동기화에서 자산을 선택적으로 포함 또는 제외하려면 이 옵션을 선택 취소합니다. 이 옵션을 선택 해제하면 다음 두 가지 Dynamic Media 동기화 모드 중에서 선택할 수 있습니다.

   * **[!UICONTROL Dynamic Media 동기화 모드]**
      * **[!UICONTROL 기본적으로]** 활성화됨 - 제외용으로 특별히 폴더를 표시하지 않는 한 기본적으로 모든 폴더에 구성이 적용됩니다. <!-- you can then deselect the folders that you do not want the configuration applied to.-->
      * **[!UICONTROL 기본적으로]** 비활성화됨 - 선택한 폴더를 Dynamic Media에 동기화하도록 명시적으로 표시해야만 구성이 어떤 폴더에도 적용되지 않습니다.
선택한 폴더를 Dynamic Media에 동기화하도록 표시하려면 자산 폴더의 속성 페이지를 엽니다. 세부 **[!UICONTROL 정보]** 탭을 누른 다음 **[!UICONTROL Dynamic Media 동기화 모드]** 드롭다운 목록에서 다음 세 옵션 중에서 선택한 다음 저장을 **[!UICONTROL 탭합니다]**.
         * **[!UICONTROL 상속됨]** - 폴더에 명시적 동기화 값이 없습니다.대신 폴더는 상위 폴더 중 하나 또는 클라우드 구성의 기본 모드에서 동기화 값을 상속합니다. 상속된 항목에 대한 세부 상태는 도구 설명을 통해 표시됩니다.
         * **[!UICONTROL 하위 폴더]** 사용 - Dynamic Media에 동기화할 수 있도록 이 하위 트리에 있는 모든 것을 포함합니다. 폴더별 설정은 클라우드 구성에서 기본 모드를 덮어씁니다.
         * **[!UICONTROL 하위 폴더에]** 대해 비활성화됨 - 이 하위 트리의 모든 항목을 Dynamic Media로 동기화에서 제외합니다.

   >[!NOTE]
   >
   >Dynamic Media에서는 버전 관리가 지원되지 않습니다. 또한, 지연된 활성화는 [다이내믹 미디어 구성 편집] 페이지의 **[!UICONTROL 자산]** 게시가 활성화 **[!UICONTROL 시]**&#x200B;로 설정된 경우에만 적용되며, 처음 자산이 활성화될 때까지만 적용됩니다.
   >
   >
   >자산이 활성화되면 모든 업데이트가 즉시 S7 전달에 실시간으로 게시됩니다.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. 저장을 **[!UICONTROL 누릅니다]**.
1. Dynamic Media 컨텐츠를 게시하기 전에 안전하게 미리 보려면 AEM 작성자 인스턴스를 &quot;&quot;하여 Dynamic Media에 연결해야 합니다.

   * Dynamic Media Classic 계정에 로그온합니다. [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html). 프로비전 시 Adobe에서 자격 증명 및 로그온을 제공했습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.
   * 페이지 오른쪽 상단의 탐색 막대에서 **[!UICONTROL 설정 > 애플리케이션 설정 > 게시 설정 > 이미지 서버를 클릭합니다]**.

   * 이미지 서버 게시 페이지의 게시 컨텍스트 드롭다운 목록에서 이미지 제공 **[!UICONTROL 테스트를 선택합니다]**.
   * 클라이언트 주소 필터에서 추가를 **[!UICONTROL 누릅니다]**.
   * 주소를 활성화(켜기)하려면 확인란을 선택하고 AEM 작성자 인스턴스의 IP 주소(발송자 IP가 아님)를 입력합니다.
   * **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

이제 기본 구성이 완료되었습니다.Dynamic Media를 사용할 준비가 되었습니다.

구성을 추가로 사용자 지정하려면 Dynamic Media에서 고급 설정 [구성 아래의 작업을 선택적으로 완료할 수 있습니다](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## (선택 사항) Dynamic Media에서 고급 설정 구성{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Dynamic Media의 구성 및 설정을 사용자 정의하거나 성능을 최적화하려는 경우 다음 *선택* 작업 중 하나 이상을 완료할 수 있습니다.

* [다이내믹 미디어 설정 및 구성](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(선택 사항) 다이내믹 미디어 성능 조정](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (선택 사항) 다이내믹 미디어 설정 및 구성 {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Dynamic Media Classic(Scene7) 사용자 인터페이스를 사용하여 다이내믹 미디어 설정을 변경합니다.

위의 작업 중 일부는 여기에서 Dynamic Media Classic(Scene7)에 로그인해야 합니다. [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

설정 및 구성 작업은 다음과 같습니다.

* [이미지 서버에 대한 게시 설정](#publishing-setup-for-image-server)
* [응용 프로그램 일반 설정 구성](#configuring-application-general-settings)
* [색상 관리 구성](#configuring-color-management)
* [자산 처리 구성](#configuring-asset-processing)
* [지원되지 않는 포맷에 대한 사용자 지정 MIME 형식 추가](#adding-custom-mime-types-for-unsupported-formats)
* [이미지 세트 및 스핀 세트를 자동으로 생성하기 위한 일괄 세트 사전 설정 만들기](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### 이미지 서버에 대한 게시 설정 {#publishing-setup-for-image-server}

게시 설정 설정에 따라 기본적으로 Dynamic Media에서 자산이 제공되는 방법이 결정됩니다. 설정이 지정되지 않은 경우, Dynamic Media는 제작 설정에 정의된 기본 설정에 따라 자산을 전달합니다. 예를 들어 해상도 속성이 포함되지 않은 이미지를 전달하라는 요청은 기본 개체 해상도 설정이 있는 이미지를 생성합니다.

게시 설정을 구성하려면:Dynamic Media Classic에서 **[!UICONTROL 설정 > 응용 프로그램 설정 > 게시 설정 > 이미지 서버를 클릭합니다]**.

[이미지 서버] 화면은 이미지를 전달하기 위한 기본 설정을 설정합니다. 각 설정에 대한 설명은 UI 화면을 참조하십시오.

* **[!UICONTROL 요청 속성]** - 이러한 설정은 서버에서 전달할 수 있는 이미지에 제한을 적용합니다.
* **[!UICONTROL 기본 요청 속성]** - 이 설정은 이미지의 기본 모양과 관련이 있습니다.
* **[!UICONTROL 공통 축소판 속성]** - 이 설정은 축소판 이미지의 기본 모양과 관련이 있습니다.
* **[!UICONTROL 카탈로그 필드의 기본값]**- 이 설정은 이미지의 해상도 및 기본 축소판 유형과 관련이 있습니다.
* **[!UICONTROL 색상 관리 속성]** - 이 설정에 따라 어떤 ICC 색상 프로파일이 사용되는지 결정됩니다.
* **[!UICONTROL 호환성 속성]** - 이 설정을 사용하면 텍스트 레이어의 선행 및 후행 단락을 이전 버전과의 호환성을 위해 버전 3.6에서와 같이 처리할 수 있습니다.
* **[!UICONTROL 로컬라이제이션 지원]** - 이 설정을 통해 여러 로케일 특성을 관리할 수 있습니다. 또한 로케일 맵 문자열을 지정할 수 있으므로 뷰어에서 다양한 도구 설명을 지원할 언어를 정의할 수 있습니다. 현지화 지원 설정에 대한 자세한 내용은 **[!UICONTROL 자산 현지화]**&#x200B;설정 시 [고려 사항](https://help.adobe.com/en_US/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html)을 참조하십시오.

#### 응용 프로그램 일반 설정 구성 {#configuring-application-general-settings}

응용 프로그램 일반 설정 페이지를 열려면 Dynamic Media Classic 전역 탐색 막대에서 **[!UICONTROL 설정 > 응용 프로그램 설정 > 일반 설정을 클릭합니다.]**

* **[!UICONTROL 서버]** - 계정 프로비저닝에서 Dynamic Media는 자동으로 회사에 할당된 서버를 제공합니다. 이러한 서버는 웹 사이트 및 응용 프로그램에 대한 URL 문자열을 구성하는 데 사용됩니다. 이러한 URL 호출은 계정에 따라 다릅니다. AEM 지원에 의해 명시적으로 지시된 경우를 제외하고 서버 이름을 변경하지 마십시오.
* **[!UICONTROL 이미지]** 덮어쓰기 - Dynamic Media에서는 두 파일의 이름이 같은 것을 허용하지 않습니다. 각 항목의 URL ID(파일 이름 - 확장명)는 고유해야 합니다. 다음 옵션은 대체 자산이 업로드되는 방식을 지정합니다.원본을 대체할지 또는 중복되게 할지 여부. 중복 에셋의 이름이 &quot;-1&quot;으로 바뀝니다(예: chair.tif의 이름이 chair-1.tif로 변경됨). 이러한 옵션은 원본과 다른 폴더에 업로드된 에셋이나 원본 파일 이름 확장자가 다른 에셋에 영향을 줍니다(예: JPG, TIF 또는 PNG).
* **[!UICONTROL 현재 폴더에 덮어쓰기, 동일한 기본 이미지 이름/확장명]** - 이 옵션은 교체에 가장 강력한 규칙입니다. 교체 이미지를 원본과 동일한 폴더에 업로드하고 교체 이미지의 파일 이름 확장자는 원본과 같아야 합니다. 이러한 요구 사항이 충족되지 않으면 복제본이 만들어집니다.
   >[!NOTE]
   >
   >AEM과의 일관성을 유지하려면 항상 이 설정을 선택하십시오. **현재 폴더에 동일한 기본 이미지 이름/확장명으로 덮어쓰기**
* **[!UICONTROL 동일한 기본 에셋 이름/확장명으로]** 모든 폴더에 덮어쓰기 - 대체 이미지의 파일 이름 확장명이 원본 이미지와 동일해야 합니다(예: chair.jpg는 chair.tif가 아니라 chair.jpg를 대체해야 합니다). 그러나 원본 이미지와 다른 폴더에 교체 이미지를 업로드할 수 있습니다. 업데이트된 이미지는 새 폴더에 있습니다.원본 위치에서 파일을 더 이상 찾을 수 없습니다.
* **[!UICONTROL 확장자와]** 상관없이 동일한 기본 자산 이름으로 모든 폴더에 덮어쓰기 - 이 옵션은 가장 포괄적인 대체 규칙입니다. 원본 파일과 다른 폴더에 교체 이미지를 업로드하고 파일 이름 확장자가 다른 파일을 업로드한 다음 원본 파일을 바꿀 수 있습니다. 원본 파일이 다른 폴더에 있는 경우 교체 이미지는 업로드된 새 폴더에 있습니다.
* **[!UICONTROL 기본 색상 프로필]** - 자세한 내용은 [색상 관리](#configuring-color-management) 구성을 참조하십시오.
   >[!NOTE]
   >
   >기본적으로 자산의 세부 정보 보기에서 뷰어 **[!UICONTROL 를]** 선택하면 변환 **[!UICONTROL 및 15개의 뷰어 사전 설정을 선택하면]** 15개의 변환이표시됩니다. 이 한도를 늘릴 수 있습니다. 표시되는 [이미지 사전](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) 설정 수 증가 또는 감소 [또는 표시되는 뷰어 사전](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display)설정 수 증가 또는 감소를 참조하십시오.

#### 색상 관리 구성 {#configuring-color-management}

다이내믹 미디어 색상 관리를 사용하면 올바른 에셋에 색상을 적용할 수 있습니다. 색상 교정을 통해 인제스트된 에셋은 색상 공간(RGB, CMYK, 회색) 및 임베드된 색상 프로파일을 유지합니다. 동적 변환을 요청하면 이미지 색상이 CMYK, RGB 또는 회색 출력을 사용하여 대상 색상 공간으로 교정할 수 있습니다. See [Configuring Image Presets](/help/assets/dynamic-media/managing-image-presets.md).

이미지를 요청할 때 색상 교정을 사용하도록 기본 색상 속성을 구성하려면 다음을 수행하십시오.

1. [프로비전 중에 제공된 자격 증명을](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) 사용하여 Dynamic Media Classic에 로그인합니다. 설정 **[!UICONTROL > 애플리케이션 설정으로 이동합니다]**.
1. [ **[!UICONTROL 게시 설정]** ] 영역을 확장하고 [ **[!UICONTROL 이미지 서버]를 선택합니다]**. 게시 인스턴스 **[!UICONTROL 에]** 대한 기본값 **[!UICONTROL 을]** 설정할 때 게시 컨텍스트를 이미지 제공으로 설정합니다.
1. 변경해야 할 속성(예: 색상 관리 속성 **[!UICONTROL 영역의 속성)으로]** 스크롤합니다.

   다음 색상 교정 속성을 설정할 수 있습니다.

   * **[!UICONTROL CMYK 기본 색상 공간]** - 기본 CMYK 색상 프로파일의 이름입니다.
   * **[!UICONTROL 회색 크기 조절 기본 색상 공간]** - 기본 회색 색상 프로파일의 이름입니다.
   * **[!UICONTROL RGB 기본 색상 공간]** - 기본 RGB 색상 프로필의 이름입니다.
   * **[!UICONTROL 색상 변환 렌더링 의도]** - 렌더링 의도를 지정합니다. 허용되는 값은 다음과 같습니다. **[!UICONTROL perception]**, **[!UICONTROL 상대]** colorometric **[!UICONTROL ,]**&#x200B;채도 **[!UICONTROL ,절대소량측정]** Adobe은 **[!UICONTROL 상대]** 를 기본값으로 권장합니다.

1. 저장을 **[!UICONTROL 누릅니다]**.

예를 들어 **[!UICONTROL RGB 기본 색상 공간]** 을 sRGB *로*&#x200B;설정하고 **[!UICONTROL CMYK 기본 색상 공간]** 을 WebCoated가 되도록 설정할 수 **&#x200B;있습니다.

이렇게 하면 다음이 수행됩니다.

* RGB 및 CMYK 이미지의 색상 교정을 활성화합니다.
* 색상 프로필이 없는 RGB 이미지는 *sRGB* 색상 공간에 있는 것으로 간주됩니다.
* 색상 프로필이 없는 CMYK 이미지는 *WebCoated* 색상 공간에 있다고 가정합니다.
* RGB 출력을 반환하는 동적 변환은 *sRGB *색상 공간에 반환됩니다.
* CMYK 출력을 반환하는 동적 변환은 *WebCoated* 색상 공간에 반환됩니다.

#### 자산 처리 구성 {#configuring-asset-processing}

Dynamic Media에서 처리해야 하는 자산 유형을 정의하고 고급 자산 처리 매개 변수를 사용자 정의할 수 있습니다. 예를 들어 자산 처리 매개 변수를 지정하여 다음을 수행할 수 있습니다.

* Adobe PDF을 eCatalog 자산으로 변환
* Adobe Photoshop 문서(.PSD)를 배너 템플릿 에셋으로 변환하여 개인화합니다.
* Adobe Illustrator 파일(.AI) 또는 Adobe Photoshop Encapsulated Postscript 파일(.EPS)을 래스터화합니다.
* 참고:비디오 프로필 및 이미징 프로필을 사용하여 각각 비디오와 이미지 처리를 정의할 수 있습니다.

[자산 업로드](/help/assets/add-assets.md)를 참조하십시오.

자산 처리를 구성하려면:

1. AEM에서 AEM 로고를 클릭하여 글로벌 탐색 콘솔에 액세스한 다음 **[!UICONTROL 일반 > CRXDE Lite을 클릭합니다]**.
1. 왼쪽 레일에서 다음 항목으로 이동합니다.

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. mimeTypes 폴더에서 MIME 형식을 선택합니다.
1. CRXDE Lite 페이지 오른쪽의 아래 부분:

   * enabled **[!UICONTROL 필드를 두 번]** 클릭합니다. 기본적으로 모든 자산 MIME 유형이 활성화되어 있습니다( **[!UICONTROL true로]**&#x200B;설정). 즉, 자산은 처리를 위해 Dynamic Media에 동기화됩니다. 이 자산 MIME 형식을 처리 대상에서 제외하려면 이 설정을 **[!UICONTROL false로 변경하십시오]**.

   * jobParam **[!UICONTROL 을]** 두 번 클릭하여 연관된 텍스트 필드를 엽니다. 지정된 [MIME 유형에 사용할 수 있는 허용된 처리 매개 변수 값 목록은 지원되는 MIME 형식을](/help/assets/file-format-support.md) 참조하십시오.

1. 다음 중 하나를 수행하십시오.
   * 추가 MIME 유형을 편집하려면 3-4단계를 반복합니다.
   * CRXDE Lite 페이지의 메뉴 모음에서 모두 **[!UICONTROL 저장을 클릭합니다.]**

1. 페이지의 왼쪽 위 모서리에서 **[!UICONTROL CRXDE Lite]** 를 눌러 AEM으로 돌아갑니다.

#### 지원되지 않는 포맷에 대한 사용자 지정 MIME 형식 추가 {#adding-custom-mime-types-for-unsupported-formats}

AEM Assets에서 지원되지 않는 형식에 대해 사용자 지정 MIME 형식을 추가할 수 있습니다. CRXDE Lite에 추가하는 새 노드가 AEM에서 삭제되지 않도록 하려면 먼저 MIME 형식을 이동해야 하며 `image_` 이 활성화된 값은 **[!UICONTROL false로 설정되어 있어야 합니다]**.

지원되지 않는 형식에 대한 사용자 지정 MIME 형식을 추가하려면:

1. AEM에서 **[!UICONTROL 도구 > 작업 > 웹 콘솔을 누릅니다.]**

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. [ **[!UICONTROL Adobe Experience Manager 웹 콘솔 구성] 페이지에 새 브라우저 탭이]** 열립니다.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. 페이지에서 다음 스크린샷과 같이 *Adobe CQ Scene7 자산 MIME 유형 서비스* 이름으로 아래로 스크롤합니다. 이름 오른쪽에 있는 구성 값 **[!UICONTROL 편집]** (연필 아이콘)을 누릅니다.

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. Adobe CQ **Scene7 자산 MIME 유형 서비스** 페이지에서 더하기 기호 아이콘 &lt;+>을 클릭합니다. 표에 있는 더하기 기호를 클릭하여 새 MIME 형식을 추가하는 위치는 매우 작습니다.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. 방금 추가한 빈 텍스트 필드 `DWG=image/vnd.dwg` 를 입력합니다.

   이 예제는 일러스트레이션 `DWG=image/vnd.dwg` 을 위한 것입니다. 여기에 추가하는 MIME 형식은 지원되지 않는 다른 형식일 수 있습니다.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. In the lower-right corner of the page, tap **[!UICONTROL Save]**.

   이때, 열려 있는 Adobe Experience Manager 웹 콘솔 구성 페이지가 있는 브라우저 탭을 닫을 수 있습니다.

1. 열린 AEM 콘솔이 있는 브라우저 탭으로 돌아갑니다.
1. AEM에서 **[!UICONTROL 도구 > 일반 > CRXDE Lite을 누릅니다]**.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. 왼쪽 레일에서 다음 항목으로 이동합니다.

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. 다음 스크린샷과 같이 MIME 유형 `image_vnd.dwg` 을 트리 위 `image_` 에 바로 놓습니다.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. 속성 `image_vnd.dwg` 탭 **[!UICONTROL 의 속성]** 탭 **[!UICONTROL 에서]** 활성화된 **[!UICONTROL 행의 값]** **** 열 헤더 아래에서 값을 두 번 클릭하여 값을 ValueValue 드롭다운 목록을 엽니다.
1. 필드 `false` 를 입력하거나 드롭다운 목록에서 **[!UICONTROL false]** 를 선택합니다.

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. CRXDE Lite 페이지의 왼쪽 위 모서리 근처에 있는 [모두 **[!UICONTROL 저장]을 클릭합니다]**.

#### 이미지 세트 및 스핀 세트를 자동으로 생성하기 위한 일괄 세트 사전 설정 만들기 {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

자산을 Dynamic Media로 업로드하는 동안 일괄 세트 사전 설정을 사용하여 이미지 세트 또는 스핀 세트 생성을 자동화할 수 있습니다.

먼저 자산을 집합으로 그룹화하는 방법에 대한 이름 지정 규칙을 정의합니다. 그런 다음 사전 설정 레서피에서 정의된 이름 지정 규칙과 일치하는 이미지를 사용하여 세트를 구성하는 방법을 정의하는 고유한 이름의 자체 지침 세트인 배치 집합 사전 설정을 만들 수 있습니다.

파일을 업로드하면 Dynamic Media는 활성 사전 설정에서 정의된 이름 지정 규칙과 일치하는 모든 파일이 포함된 세트를 자동으로 만듭니다.

**기본 이름 지정 구성**

일괄 세트 사전 설정 레서피에서 사용되는 기본 이름 지정 규칙을 만듭니다. 배치 세트 사전 설정 정의에서 선택한 기본 이름 지정 규칙은 회사에서 세트를 일괄 생성하는 데 필요한 모든 것일 수 있습니다. 정의된 기본 이름 지정 규칙을 사용하도록 일괄 세트 사전 설정이 만들어집니다. 회사 정의된 기본 이름 지정에 대한 예외가 있는 경우 특정 컨텐츠 세트에 필요한 대체 사용자 정의 이름 지정 규칙이 있는 여러 개의 일괄 세트 사전 설정을 만들 수 있습니다.

일괄 세트 사전 설정 기능을 사용할 때는 기본 이름 지정 규칙을 설정할 필요가 없지만, 묶음 세트 생성을 간소화할 수 있도록 기본 이름 지정 규칙을 사용하여 한 세트에 그룹화할 이름 지정 규칙의 요소를 원하는 만큼 정의하는 것이 좋습니다.

대신 사용 가능한 양식 필드가 없는 코드 **[!UICONTROL 보기를]** 사용할 수 있습니다. 이 보기에서는 정규 표현식을 사용하여 이름 지정 규칙 정의를 완전히 생성합니다.

두 요소를 정의하면 일치 및 기본 이름을 사용할 수 있습니다. 이러한 필드를 사용하면 이름 지정 규칙의 모든 요소를 정의하고 해당 항목이 포함된 세트의 이름을 지정하는 데 사용되는 규칙의 일부를 식별할 수 있습니다. 회사의 개별 명명 규칙은 이러한 각 요소에 대해 하나 이상의 정의 라인을 사용할 수 있습니다. 고유 정의에 대해 여러 개의 선을 사용하고 기본 이미지, 색상 요소, 대체 보기 요소 및 견본 요소와 같은 별개의 요소로 그룹화할 수 있습니다.

기본 이름 지정을 구성하려면:

1. Dynamic Media Classic(Scene7) 계정에 로그온합니다. [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   프로비전 시 Adobe에서 자격 증명 및 로그온을 제공했습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.

1. 페이지 상단 근처의 내비게이션 막대에서 **[!UICONTROL 설정 > 애플리케이션 설정 > 배치 집합 사전 설정 > 기본 이름 지정을 누릅니다]**.
1. 양식 **[!UICONTROL 보기]** 또는 **[!UICONTROL 코드]** 보기를 선택하여각 요소에 대한 정보를 보고 입력할 방법을 지정합니다.

   코드 **[!UICONTROL 보기]** 확인란을 선택하여 양식 선택 사항과 함께 빌드되는 정규 표현식 값을 볼 수 있습니다. 양식 보기가 어떤 이유에서든 사용자를 제한하는 경우 이러한 값을 입력하거나 변경하여 이름 지정 규칙의 요소를 정의할 수 있습니다. 양식 보기에서 값을 구문 분석할 수 없는 경우 양식 필드가 비활성화됩니다.

   >[!NOTE]
   >
   >양식 필드가 비활성화되면 일반 표현식이 올바른지 확인하지 않습니다. 결과 라인 뒤에 각 요소에 대해 빌드하는 정규 표현식 결과가 표시됩니다. 전체 정규 표현식은 페이지 하단에 표시됩니다.

1. 필요에 따라 각 요소를 확장하고 사용할 명명 규칙을 입력합니다.
1. 필요에 따라 다음 중 하나를 수행합니다.

   * 추가 **[!UICONTROL 를]** 눌러 요소에 대한 다른 명명 규칙을 추가합니다.
   * 요소 **[!UICONTROL 에]** 대한 명명 규칙을 삭제하려면 제거를 누릅니다.

1. 다음 중 하나를 수행하십시오.

   * 다른 **[!UICONTROL 이름으로]** 저장을 누르고 사전 설정의 이름을 입력합니다.
   * 기존 사전 **[!UICONTROL 설정을]** 편집하는 경우 저장을 누릅니다.

**배치 세트 사전 설정 만들기**

Dynamic Media는 뷰어에 표시하기 위해 일괄 세트 사전 설정을 사용하여 에셋을 이미지 세트(대체 이미지, 색상 옵션, 360 회전)로 구성합니다. Dynamic Media의 자산 업로드 프로세스와 함께 일괄 세트 사전 설정이 자동으로 실행됩니다.

배치 세트 사전 설정을 생성, 편집 및 관리할 수 있습니다. 두 가지 형태의 일괄 세트 사전 설정 정의가 있습니다.하나는 설정한 기본 이름 지정 규칙과 시간에 만드는 사용자 지정 이름 지정 규칙에 대한 것입니다.

양식 필드 메서드를 사용하여 묶음 집합 사전 설정이나 코드 메서드를 정의할 수 있습니다. 이 방법을 사용하면 정규식을 사용할 수 있습니다. 기본 이름 지정에서와 마찬가지로 양식 보기에서 정의하는 동시에 코드 보기를 선택하고 정규 표현식을 사용하여 정의를 작성할 수 있습니다. 또는 뷰를 선택 취소하여 하나 또는 다른 뷰를 독점적으로 사용할 수도 있습니다.

배치 세트 사전 설정을 만들려면:

1. Dynamic Media Classic(Scene7) 계정에 로그온합니다. [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   프로비전 시 Adobe에서 자격 증명 및 로그온을 제공했습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.

1. 페이지 상단 근처의 내비게이션 막대에서 **[!UICONTROL 설정 > 애플리케이션 설정 > 배치 집합 사전 설정 > 배치 집합 사전 설정을 누릅니다]**.

   [ **[!UICONTROL 세부 사항]**] 페이지의 오른쪽 위 모서리에 설정된 [양식 보기]가 기본 보기입니다.

1. 사전 설정 목록 패널에서 **[!UICONTROL 추가를]** 눌러 화면 오른쪽의 세부 사항 패널에서 정의 필드를 활성화합니다.
1. 세부 사항 패널의 사전 설정 이름 필드에 사전 설정 이름을 입력합니다.
1. 배치 세트 유형 드롭다운 메뉴에서 사전 설정 유형을 선택합니다.
1. 다음 중 하나를 수행하십시오.

   * 이전에 [ **[!UICONTROL 애플리케이션 설정] > [배치 집합 사전 설정] > [기본 이름 지정]에서 설정한 기본 이름 지정 규칙을 사용 중인 경우]**&#x200B;자산 이름 지정 규칙 **[!UICONTROL 을 확장한 다음]**&#x200B;파일 이름 지정 **[!UICONTROL 드롭다운 목록에서 기본값을]**&#x200B;누릅니다.

   * 사전 설정을 설정할 때 새 이름 지정 규칙을 정의하려면 **[!UICONTROL 자산 이름 지정 규칙]**&#x200B;을 확장한 다음 파일 이름 지정 드롭다운 목록에서 사용자 지정 **[!UICONTROL 을 클릭합니다]**.

1. 시퀀스 순서의 경우, 세트가 Dynamic Media로 그룹화된 후 이미지가 표시되는 순서를 정의합니다.

   기본적으로 자산은 영숫자 순서가 지정됩니다. 그러나, 정규 표현식의 쉼표로 구분된 목록을 사용하여 순서를 정의할 수 있습니다.

1. [이름 지정 및 생성 규칙 설정]에 [자산 이름 지정 규칙]에서 정의한 기본 이름에 접미사 또는 접두사를 지정합니다. 또한, Dynamic Media 폴더 구조 내에서 세트를 만들 위치를 정의합니다.

   많은 수의 세트를 정의하는 경우 자산 자체가 포함된 폴더와 이러한 세트를 구분하도록 할 수 있습니다. 예를 들어 이미지 세트 폴더를 만들고 여기에 생성된 세트를 배치할 수 있습니다.

1. 세부 사항 패널에서 저장을 **[!UICONTROL 누릅니다]**.
1. 새 **[!UICONTROL 사전 설정 이름]** 옆에 있는 활성을 누릅니다.

   사전 설정을 활성화하면 자산을 Dynamic Media에 업로드할 때 배치 세트 사전 설정이 적용되어 세트를 생성합니다.

**2D 스핀 세트의 자동 생성을 위한 배치 세트 사전 설정 만들기**

배치 세트 유형 **[!UICONTROL 다중 축 스핀]** 세트를 사용하여 2D 스핀 세트 생성을 자동화하는 레서피를 생성할 수 있습니다. 이미지 그룹화에서는 행 및 열 정규 표현식을 사용하므로 이미지 에셋이 다차원 배열의 해당 위치에 올바르게 정렬됩니다. 다중 축 회전 집합에 포함해야 하는 최소 또는 최대 행 수 또는 최대 개수가 없습니다.

예를 들어 이름이 지정된 다중 축 회전 집합을 만든다고 가정합니다 `spin-2dspin`. 행에 대해 12개의 이미지가 포함된 3개의 행을 포함하는 스핀 세트 이미지 세트가 있습니다. 이미지 이름은 다음과 같습니다.

```
spin-01-01
 spin-01-02
 …
 spin-01-12
 spin-02-01
 …
 spin-03-12
```

이 정보를 사용하여 다음과 같이 배치 세트 유형 레서피를 생성할 수 있습니다.

![chlimage_1-560](assets/chlimage_1-560.png)

스핀 세트의 공유 에셋 이름 부분에 대한 그룹화가 **일치** 필드(강조 표시)에 추가됩니다. 행과 열이 포함된 자산 이름의 변수 부분이 **행** 및 **열** 필드에 각각 추가됩니다.

스핀 세트를 업로드하고 게시하면 **업로드 작업 옵션** 대화 상자의 배치 세트 사전 설정 아래에 나열된 2D 스핀 세트 레시피 **** 이름을 활성화합니다.

**2D 스핀 세트의 자동 생성을 위한 배치 세트 사전 설정을 만들려면**

1. Dynamic Media Classic(Scene7) 계정에 로그온합니다. [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   프로비전 시 Adobe에서 자격 증명 및 로그온을 제공했습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.

1. 페이지 상단 근처의 내비게이션 막대에서 **[!UICONTROL 설정 > 애플리케이션 설정]>[!UICONTROL 배치 집합 사전 설정]>[!UICONTROL 배치 집합 사전 설정을 클릭합니다]**.

   [ **[!UICONTROL 세부 사항]**] 페이지의 오른쪽 위 모서리에 설정된 [양식 보기]가 기본 보기입니다.

1. 사전 설정 목록 패널에서 **[!UICONTROL 추가]** 를 클릭하여 화면 오른쪽의 세부 사항 패널에서 정의 필드를 활성화합니다.
1. 세부 사항 패널의 사전 설정 이름 필드에 사전 설정 이름을 입력합니다.
1. 배치 세트 유형 드롭다운 메뉴에서 자산 **[!UICONTROL 세트를 선택합니다]**.
1. 하위 유형 드롭다운 목록에서 **[!UICONTROL 다축 스핀 세트를 선택합니다]**.
1. 자산 **[!UICONTROL 이름 지정 규칙을 확장한]**&#x200B;다음 파일 이름 지정 드롭다운 목록에서 사용자 **[!UICONTROL 지정을 클릭합니다]**.
1. 일치 **[!UICONTROL 및]** 원할 경우 **[!UICONTROL 기본 이름]** 속성을 사용하여 그룹화를 구성하는 이미지 자산의 이름 지정에 대한 정규 표현식을 정의합니다.

   예를 들어 문자 일치 정규식은 다음과 같이 표시될 수 있습니다.

   `(w+)-w+-w+`

1. 행 **[!UICONTROL 열 위치를 확장한]**&#x200B;다음 2D 회전 집합 배열 내에서 이미지 자산의 위치에 대한 이름 형식을 정의합니다.

   괄호를 사용하여 파일 이름의 행 또는 열 위치를 가져옵니다.

   예를 들어 행 정규 표현식의 경우 다음과 같이 표시될 수 있습니다.

   `\w+-R([0-9]+)-\w+`

   또는

   `\w+-(\d+)-\w+`

   열 정규 표현식의 경우 다음과 같이 표시될 수 있습니다.

   `\w+-\w+-C([0-9]+)`

   또는

   `\w+-\w+-C(\d+)`

   이것들이 단지 예시라는 것을 기억하세요. 필요에 따라 정규 표현식을 만들 수 있습니다.

   >[!NOTE]
   >
   >행과 열 정규 표현식의 조합이 다차원 스핀셋 배열 내의 자산의 위치를 확인할 수 없는 경우 해당 자산이 세트에 추가되지 않고 오류가 기록됩니다.

1. [이름 지정 및 생성 규칙 설정]에 [자산 이름 지정 규칙]에서 정의한 기본 이름에 접미사 또는 접두사를 지정합니다.

   또한, Dynamic Media Classic 폴더 구조 내에서 스핀 세트를 만들 위치를 정의합니다.

   많은 수의 세트를 정의하는 경우 자산 자체가 포함된 폴더와 이러한 세트를 구분하도록 할 수 있습니다. 예를 들어, 여기서 생성된 세트를 배치할 회전 집합 폴더를 만듭니다.

1. 세부 사항 패널에서 저장을 **[!UICONTROL 클릭합니다]**.
1. 새 **[!UICONTROL 사전 설정 이름]** 옆에 있는 활성을 클릭합니다.

   사전 설정을 활성화하면 자산을 Dynamic Media에 업로드할 때 배치 세트 사전 설정이 적용되어 세트를 생성합니다.

### (선택 사항) 다이내믹 미디어 성능 조정 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Dynamic Media를 원활하게 <!--(with `dynamicmedia_scene7` run mode)--> 실행하려면 다음과 같은 동기화 성능/확장성 세부 조정 팁을 권장합니다.

* 다양한 파일 형식을 처리하기 위해 사전 정의된 작업 매개 변수 업데이트
* 미리 정의된 [granite workflow(비디오 에셋) 큐 작업자 스레드 업데이트
* 미리 정의된 [화강암 임시 작업 과정(이미지 및 비비디오 자산) 큐 작업자 스레드를 업데이트합니다.
* Dynamic Media Classic 서버에 대한 최대 업로드 연결 업데이트

#### 다양한 파일 형식을 처리하기 위해 사전 정의된 작업 매개 변수 업데이트

파일을 업로드할 때 작업 매개 변수를 조정하여 보다 신속하게 처리할 수 있습니다. 예를 들어 PSD 파일을 업로드하지만 템플릿으로 처리하지는 않으려는 경우 레이어 추출을 false(off)로 설정할 수 있습니다. 이 경우 조정된 작업 매개 변수가 로 나타납니다 `process=None&createTemplate=false`.

Adobe은 PDF, Postscript 및 PSD 파일에 대해 다음과 같은 &quot;조정된&quot; 작업 매개 변수를 사용하는 것이 좋습니다.

| 파일 유형 | 권장 작업 매개 변수 |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| Postscript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

이러한 매개 변수를 업데이트하려면 MIME 유형 기반 자산/ [Dynamic Media Classic 업로드 작업 매개 변수 지원의 단계를 따릅니다](#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

#### [MOCK] Updating the Granite Temporary Workflow queue {#updating-the-granite-transient-workflow-queue}

[DAM 자산 업데이트] 작업 과정에는 [GRANITE Transit 작업 과정 큐 **[!UICONTROL 가]** 사용됩니다. Dynamic Media에서 이미지 수집 및 처리에 사용됩니다.

**[MOCK] To update the Granite Temporary Workflow queue**

1. https://&lt; [server>/system/console/configMgr](https://localhost:4502/system/console/configMgr) 로 이동하고 **큐 검색:[MOCK] Granite Temporary Workflow Queue**.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. 최대 **[!UICONTROL 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   기본적으로 최대 병렬 작업 수는 사용 가능한 CPU 코어 수에 따라 달라집니다. 예를 들어 4코어 서버에서는 2개의 작업자 스레드를 할당합니다. (0.0과 1.0 사이의 값은 비율 기반이거나 1보다 큰 숫자는 작업자 스레드의 수를 지정합니다.)

   Adobe은 Dynamic Media Classic(Scene7)에 대용량 파일 업로드를 지원하기 위해 **[!UICONTROL 최대 병렬 작업]** 32개를 구성할 것을 권장합니다.

   ![chlimage_1](assets/chlimage_1.jpeg)

1. 저장을 **[!UICONTROL 누릅니다]**.

#### [MOCK] Updating the Granite Workflow queue {#updating-the-granite-workflow-queue}

[MOCK] The Granite Workflow queue is used for non-temporary workflows. Dynamic Media에서는 **[!UICONTROL 다이내믹 미디어 인코딩 비디오]** 워크플로우로 비디오를 처리했습니다.

[MOCK] To update the Granite Workflow queue:

1. 대기열로 `https://<server>/system/console/configMgr` 이동 및 **검색:[MOCK] Granite Workflow Queue**.

   >[!NOTE]
   >
   >OSGi PID가 동적으로 생성되므로 직접 URL 대신 텍스트 검색이 필요합니다.

1. 최대 **[!UICONTROL 병렬 작업]** 필드에서 숫자를 원하는 값으로 변경합니다.

   기본적으로 최대 병렬 작업 수는 사용 가능한 CPU 코어 수에 따라 달라집니다. 예를 들어 4코어 서버에서는 2개의 작업자 스레드를 할당합니다. (0.0과 1.0 사이의 값은 비율 기반이거나 1보다 큰 숫자는 작업자 스레드의 수를 지정합니다.)

   대부분의 사용 사례에서 기본 설정 0.5이면 충분합니다.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. 저장을 **[!UICONTROL 누릅니다]**.

#### Scene7 업로드 연결 업데이트 {#updating-the-scene-upload-connection}

Scene7 업로드 연결 설정은 AEM 자산을 Dynamic Media Classic 서버에 동기화합니다.

Scene7 업로드 연결을 업데이트하려면:

1. 다음으로 이동 `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. 연결 **[!UICONTROL 수]** 필드 및/또는 **[!UICONTROL 활성 작업 시간 초과]** 필드에서 원하는 대로 숫자를 변경합니다.

   연결 **[!UICONTROL 수]** 설정은 AEM에서 Dynamic Media로 업로드할 수 있는 최대 HTTP 연결 수를 제어합니다.일반적으로 사전 정의된 10개 연결 값이면 충분합니다.

   [ **[!UICONTROL 활성 작업 시간 초과]** ] 설정은 업로드된 Dynamic Media 자산이 배달 서버에 게시되는 대기 시간을 결정합니다. 이 값은 기본적으로 2100초 또는 35분입니다.

   대부분의 경우 2100으로 설정하면 충분합니다.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. 저장을 **[!UICONTROL 누릅니다.]**

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

