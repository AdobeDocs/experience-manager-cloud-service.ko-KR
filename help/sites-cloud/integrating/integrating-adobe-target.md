---
title: Adobe Target과 통합
description: 'Adobe Target과 통합 '
translation-type: tm+mt
source-git-commit: f2ed74afd2df43e31ff1002cd42a60f372d0b769
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 2%

---


# Adobe Target과 통합{#integrating-with-adobe-target}

Adobe Target을 사용하면 모든 채널에서 타깃팅과 측정을 통해 컨텐츠 관련성을 높일 수 있습니다. Adobe Target과 AEM을 Cloud Service으로 통합하려면 다음을 수행해야 합니다.

* 터치 UI를 사용하여 AEM에서 Analytics 구성을 Cloud Service(IMS 구성 필요)로 만듭니다.
* Adobe Launch의 확장으로 Adobe Analytics 추가 및 [구성](https://docs.adobe.com/content/help/en/launch/using/intro/get-started/quick-start.html).

Adobe 실행은 AEM 페이지의 Analytics 및 Target 모두에 대한 클라이언트측 속성을 관리하는 데 필요합니다(JS 라이브러리/태그). 즉, &quot;경험 타깃팅&quot;을 위해 Launch와의 통합이 필요합니다. 경험 조각을 Target으로 내보내려면 Adobe Target 구성 및 IMS만 있으면 됩니다.

>[!NOTE]
>
>Adobe Experience Manager은 기존 Target 계정이 없는 Cloud Service 고객으로 Experience Cloud에 대한 Target Foundation Pack 액세스를 요청할 수 있습니다. Foundation Pack은 Target의 볼륨 사용을 제한합니다.

## Adobe Target 구성 만들기 {#create-configuration}

1. 도구 **→** Cloud Service으로 **이동합니다**.
   ![탐색](assets/cloudservice1.png "탐색")
2. Adobe Target을 **선택합니다**.
3. 만들기 **단추를** 선택합니다.
   ![만들기](assets/tenant1.png "만들기")
4. 세부 사항을 채우고(아래 참조) **Connect를 선택합니다**.
   ![](assets/open_screen1.png "Connect")

### IMS 구성

Target을 AEM 및 Launch와 제대로 통합하려면 론치와 Target 모두에 대한 IMS 구성이 필요합니다. Launch에 대한 IMS 구성은 AEM에서 Cloud Service으로 미리 구성되지만 Target IMS 구성을 만들어야 합니다(Target이 프로비저닝된 후). Target IMS 구성 [을 만드는 방법을 알아보려면 이 비디오](https://helpx.adobe.com/kr/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html) 및 [이 페이지를](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html) 참조하십시오.

### Target 구성 편집 {#edit-target-configuration}

Target 구성을 편집하려면 다음 단계를 수행합니다.

1. 기존 구성을 선택하고 속성 **을 클릭합니다**.
2. 속성을 편집합니다.
3. Adobe Target **에 다시 연결을 선택합니다**.
   ![다시](assets/edit_config_page1.png "연결다시 연결")
4. **저장 후 닫기**&#x200B;를 선택합니다.

### 사이트에 구성 추가 {#add-configuration}

사이트에 터치 UI 구성을 적용하려면 다음으로 이동하십시오. **사이트** 사이트 페이지 **를** 선택합니다. 속성 **을** 선택합니다. 고급 **→구성** **** →구성 테넌트를 선택합니다.

## Adobe 론치를 사용하여 AEM 사이트에서 Adobe Target 통합 {#integrate-target-launch}

AEM은 Experience Platform Launch과 간편하게 통합할 수 있습니다. Experience Platform Launch에 Adobe Target 확장을 추가하면 AEM 웹 페이지에서 Adobe Target의 기능을 사용할 수 있습니다.Target 라이브러리는 론치를 사용해서만 렌더링됩니다.

>[!NOTE]
>
>기존(기존) 프레임워크는 여전히 작동하지만 터치 UI에서는 구성할 수 없습니다. Launch에서 변수 매핑 구성을 다시 구성하는 것이 좋습니다.

일반적인 개요로서 통합 단계는 다음과 같습니다.

1. 론치 속성 만들기
2. 필요한 확장 기능 추가
3. 컨텍스트 허브 매개 변수를 캡처하려면 데이터 요소 만들기
4. 페이지 규칙 만들기
5. 빌드 및 게시

### 론치 속성 만들기 {#create-property}

속성은 확장, 규칙, 데이터 요소로 채워지는 컨테이너입니다.

1. 새 속성 **단추를** 선택합니다.
2. 속성의 이름을 입력합니다.
3. 도메인이 론치 라이브러리를 로드할 IP/호스트를 입력합니다.
4. 저장 **단추를** 선택합니다.
   ![Launchproperty](assets/properties_newproperty1.png "Launchproperty")

### 필요한 확장 추가 {#add-extension}

**익스텐션은** 핵심 라이브러리 설정을 관리하는 컨테이너입니다. Adobe Target 익스텐션은 최신 웹 at.js에 Target JavaScript SDK를 사용하여 클라이언트측 구현을 지원합니다. Adobe Target **및** Adobe ContextHub **** 확장을 모두 추가해야 합니다.

1. [확장 카탈로그] 옵션을 선택하고 필터에서 Target을 검색합니다.
2. at.js **를** 선택하고 설치 옵션을 클릭합니다.
   ![Target](assets/search_ext1.png "SearchTarget 검색")
3. Select the **Configure** button. Target 계정 자격 증명을 가져온 구성 창과 이 확장 기능에 대한 at.js 버전을 확인하십시오.
4. 저장 **을** 선택하여 Target 확장을 Launch 속성에 추가합니다. 설치된 확장 목록 아래에 Target 확장 기능이 **나열되어** 있어야 합니다.
   ![확장](assets/configure_extension1.png "저장 확장 기능 저장")
5. 위의 단계를 반복하여 **Adobe ContextHub** 확장 기능을 검색하고 설치합니다(타깃팅이 수행되는 대상에 따라 contexthub 매개 변수를 통합하는 데 필요합니다).

### 데이터 요소 만들기 {#data-element}

**데이터 요소는** 컨텍스트 허브 매개 변수를 매핑할 수 있는 자리 표시자입니다.

1. 데이터 **요소를 선택합니다**.
2. 데이터 **요소 추가를 선택합니다**.
3. 데이터 요소의 이름을 입력하고 컨텍스트 허브 매개 변수에 매핑합니다.
4. select **Save**.
   ![데이터](assets/data_elem1.png "요소데이터 요소")

### 페이지 규칙 만들기 {#page-rule}

규칙 **에서** 타깃팅을 수행하기 위해 사이트에서 실행되는 일련의 작업을 정의하고 순서를 지정합니다.

1. 스크린샷에 나타난 것처럼 일련의 동작을 추가합니다.
   ![작업](assets/rules1.png "작업")
2. 모든 mbox에 매개 변수 추가에서 이전에 구성된 데이터 요소(위의 데이터 요소 참조)를 mbox 호출에서 전송할 매개 변수에 추가합니다.
   ![mbox](assets/map_data1.png "Actions")

### 빌드 및 게시 {#build-publish}

빌드 및 게시 방법에 대한 자세한 내용은 이 [페이지를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html).

## 클래식 및 터치 UI 구성 간의 컨텐츠 구조 변경 {#changes-content-structure}

| **변경** | **클래식 UI 구성** | **터치 UI 구성** | **결과** |
|---|---|---|---|
| Target 구성의 위치입니다. | /etc/cloudservices/testandtarget/ | /conf/tenant/settings/cloudservices/target | 이전에 여러 구성이 /etc/cloudservices/testandtarget 아래에 있었으나 이제 단일 구성이 테넌트 아래에 있게 됩니다. |

>[!NOTE]
>
>기존 구성은 기존 고객을 위해 계속 지원됩니다(새 구성을 편집하거나 만들 수 있는 옵션 없음). 기존 구성은 고객이 VSTS를 사용하여 업로드한 컨텐츠 패키지의 일부가 됩니다.
