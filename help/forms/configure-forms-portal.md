---
title: Experience Manager Sites 페이지에서 Forms 포털을 만드는 방법
description: AEM Sites 페이지에서 Forms Portal을 만들고 기본 제공 코어 구성 요소를 사용하는 방법을 알아봅니다.
exl-id: 13cfe3ba-2e85-46bf-a029-2673de69c626
source-git-commit: 05bdc24974d2b82c1350bf6f75873cd7027f7d4a
workflow-type: tm+mt
source-wordcount: '1764'
ht-degree: 1%

---

# 포털에 적응형 Forms 나열 {#publish-forms-on-portal}

일반적인 양식 중심의 포털 배포 시나리오에서 양식 개발 및 포털 개발은 두 가지 서로 다른 작업입니다. Form Designer가 양식을 디자인하고 저장소에 저장하는 동안 Web Developers에서 양식을 나열하고 양식 제출을 처리하는 웹 응용 프로그램을 만듭니다. Forms은 forms 리포지토리와 웹 애플리케이션 간에 통신이 없으므로 웹 계층에 복사됩니다.

이러한 시나리오는 종종 관리 문제와 프로덕션 지연을 초래합니다. 예를 들어 리포지토리에서 사용할 수 있는 최신 버전의 양식이 있는 경우 웹 계층의 양식을 바꾸고 웹 응용 프로그램을 수정한 다음 공용 사이트에서 양식을 재배포해야 합니다. 웹 응용 프로그램을 다시 배포하면 서버 다운타임이 발생할 수 있습니다. 일반적으로 서버 다운타임은 계획된 활동이므로 변경 사항을 즉시 공용 사이트에 푸시할 수 없습니다.

AEM Forms은 관리 오버헤드 및 프로덕션 지연을 줄이는 포털 구성 요소를 제공합니다. 이 구성 요소는 Adobe Experience Manager(AEM)을 사용하여 작성된 웹 사이트에서 Forms 포털을 만들고 사용자 지정할 수 있도록 웹 개발자를 제공합니다.

양식 포털 구성 요소를 사용하여 다음 기능을 추가할 수 있습니다.

* 양식을 사용자 지정된 레이아웃으로 나열합니다. 기본적으로 목록 보기 및 카드 보기 레이아웃이 제공됩니다. 자신만의 사용자 정의 레이아웃을 만들 수 있습니다.
* 나열하는 동안 사용자 지정 메타데이터 및 사용자 지정 작업을 표시할 수 있습니다.
* Forms Portal 구성 요소가 사용되는 게시 인스턴스에 AEM Forms UI에서 게시한 양식을 나열합니다.
* 최종 사용자가 양식을 HTML 및 PDF 형식으로 렌더링할 수 있도록 허용합니다.
* 제목 및 설명을 기반으로 양식 검색을 활성화합니다.
* 사용자 지정 CSS를 사용하여 포털의 모양과 느낌을 사용자 지정합니다.
* 양식에 대한 링크를 만듭니다.
* 최종 사용자가 만든 적응형 Forms과 관련된 초안 및 제출을 나열합니다.

## Forms 포털 페이지의 구성 요소 {#forms-portal-components}

AEM Forms은 즉시 다음과 같은 포털 구성 요소를 제공합니다.

* 검색 및 목록: 이 구성 요소로 양식 리포지토리의 양식을 포털 페이지로 나열할 수 있으며, 지정된 기준에 따라 양식을 나열하는 구성 옵션을 제공합니다.

* 초안 및 제출: Search &amp; Lister 구성 요소는 Forms 작성자가 공개한 양식을 표시하는 동안 초안 및 제출 구성 요소는 나중 및 제출된 양식을 완료하기 위해 초안으로 저장된 양식을 표시합니다. 이 구성 요소는 로그인한 모든 사용자에게 개인화된 경험을 제공합니다.

* 링크: 이 구성 요소로 페이지의 어디에서나 양식에 대한 링크를 만들 수 있습니다.

다음을 수행할 수 있습니다 [즉시 사용 가능한 Forms Portal 구성 요소 가져오기](#import-forms-portal-components-aem-archetype) AEM 프로젝트 원형 가져온 후 다음 구성을 수행합니다.
* [외부 저장소 구성](#configure-azure-storage-adaptive-forms)
* [Forms Portal 구성 요소 활성화](#enable-forms-portal-components)
* [Forms Portal 구성 요소 구성](#configure-forms-portal-components)

## Forms Portal 구성 요소 가져오기 {#import-forms-portal-components-aem-archetype}

AEM Forms as a Cloud Service에서 바로 사용 가능한 Forms Portal 구성 요소를 가져오려면 다음 단계를 수행하십시오.

1. **로컬 개발 인스턴스에서 Cloud Manager Git 리포지토리 복제:**  Cloud Manager Git 리포지토리에는 기본 AEM 프로젝트가 포함되어 있습니다. 이것은 [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Cloud Manager UI에서 셀프 서비스 Git 계정 관리를 사용하여 Cloud Manager Git 리포지토리를 복제하여 로컬 개발 환경에서 프로젝트를 가져올 수 있습니다. 리포지토리 액세스에 대한 자세한 내용은 [저장소 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html).

1. **만들기 [!DNL Experience Manager Forms] 로서의 [Cloud Service] 프로젝트:** 만들기 [!DNL Experience Manager Forms] 로서의 [Cloud Service] 프로젝트 기반 [AEM Archetype 27](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) 또는 나중에 사용합니다. Archetype은 개발자가 을 위한 개발을 쉽게 시작할 수 있도록 지원합니다 [!DNL AEM Forms] as a Cloud Service. 또한 빠르게 시작할 수 있도록 몇 가지 샘플 테마 및 템플릿이 포함되어 있습니다.

   만들려면 [!DNL Experience Manager Forms] as a Cloud Service 프로젝트에서 명령 프롬프트를 열고 아래 명령을 실행합니다. 포함하려면 [!DNL Forms] 특정 구성, 테마 및 템플릿, `includeForms=y`.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   또한, `appTitle`, `appId`, 및 `groupId`를 입력하여 환경을 반영하십시오.

   프로젝트가 준비되면 `<core.forms.components.version>x.y.z</core.forms.components.version>` 최상위 수준의 속성 `pom.xml` 최신 버전의 Archetype을 반영하도록 Archetype 프로젝트 [core-forms-components](https://github.com/adobe/aem-core-forms-components) 다음 위치에서 `AEM Archetype` 프로젝트.

1. **프로젝트를 로컬 개발 환경에 배포합니다.** 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

   `mvn -PautoInstallPackage clean install`

   전체 명령 목록이 필요하면 [빌드 및 설치](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing)

1. [코드를 [!DNL AEM Forms] as a Cloud Service 환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#embeddeds).


## 응용 Forms에 대한 Azure 저장소 구성 {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md) 제공 [!DNL Azure] 양식을 와 통합하기 위한 스토리지 구성 [!DNL Azure] 스토리지 서비스. 양식 데이터 모델 을 사용하여 와 상호 작용하는 적응형 Forms을 만들 수 있습니다 [!DNL Azure] 비즈니스 워크플로우를 사용하도록 설정하는 서버입니다.

### 스토리지 구성 경로 {#create-azure-storage-configuration}

이 단계를 실행하기 전에 Azure 저장소 계정 및 액세스 키가 있어야 액세스 권한을 부여할 수 있습니다 [!DNL Azure] 저장소 계정.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure 저장소]**.
1. 구성을 만들 폴더를 선택하고 탭합니다. **[!UICONTROL 만들기]**.
1. 에서 구성의 제목을 지정합니다 **[!UICONTROL 제목]** 필드.
1. 이름 지정 [!DNL Azure] 스토리지 계정 **[!UICONTROL Azure 저장소 계정]** 필드.

### Forms 포털용 통합 스토리지 커넥터 구성 {#configure-usc-forms-portal}

AEM Workflows용 Unified Storage Connector를 구성하려면 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Forms]** > **[!UICONTROL 통합 스토리지 커넥터]**.
1. 에서 **[!UICONTROL Forms 포털]** 섹션, **[!UICONTROL Azure]** 에서 **[!UICONTROL 스토리지]** 드롭다운 목록.
1. 을(를) 지정합니다. [Azure 저장소 구성에 대한 구성 경로](#create-azure-storage-configuration) 에서 **[!UICONTROL 스토리지 구성 경로]** 필드.
1. 탭 **[!UICONTROL 게시]** 그런 다음 **[!UICONTROL 저장]** 구성을 저장합니다.

## Forms Portal 구성 요소 활성화 {#enable-forms-portal-components}

Adobe Experience Manager(AEM) 사이트에서 핵심 구성 요소(기본 제공 포털 구성 요소 포함)를 사용하려면 프록시 구성 요소를 만들어 사이트에 활성화해야 합니다. 프록시 구성 요소를 만들고 포털 구성 요소를 활성화하려면 [핵심 구성 요소 사용](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=en#create-proxy-components).

포털 구성 요소가 활성화되어 있으면 사이트 페이지의 작성자 인스턴스에서 해당 구성 요소를 사용할 수 있습니다.

## Forms Portal 구성 요소 추가 및 구성 {#configure-forms-portal-components}

포털 구성 요소를 추가 및 구성하여 AEM을 사용하여 작성된 웹 사이트에서 Forms 포털을 만들고 사용자 지정할 수 있습니다. 다음을 확인합니다. [구성 요소가 활성화되어 있습니다.](#enable-forms-portal-components) Forms 포털에서 사용하기 전에

구성 요소를 추가하려면 구성 요소 창에서 구성 요소를 페이지의 레이아웃 컨테이너로 끌어다 놓거나 레이아웃 컨테이너에서 추가 아이콘을 탭하고 구성 요소에서 구성 요소를 추가하십시오 [!UICONTROL 새 구성 요소 삽입] 대화 상자.

### 초안 및 제출 구성 요소 구성 {#configure-drafts-submissions-component}

초안 및 제출 구성 요소는 나중 및 제출된 양식을 완료하기 위해 초안으로 저장된 양식을 표시합니다. 구성하려면 구성 요소를 탭한 다음, ![구성 아이콘](assets/configure_icon.png). 에서 [!UICONTROL 초안 및 제출] 대화 상자에서 양식 목록을 초안 또는 제출된 양식으로 표시할 제목을 지정합니다. 또한 구성 요소에서 초안 양식을 나열할지 또는 제출된 양식을 카드 또는 목록 형식으로 나열할지 여부를 선택합니다.

![초안 아이콘](assets/drafts-component.png)

![제출 아이콘](assets/submission-listing.png)

### Search &amp; List 구성 요소 구성 {#configure-search-lister-component}

검색 및 목록 구성 요소는 페이지에 적응형 양식을 나열하고 나열된 양식에서 검색을 구현하는 데 사용됩니다.

![검색 및 목록 아이콘](assets/search-and-lister-component.png)

구성하려면 구성 요소를 탭한 다음, ![구성 아이콘](assets/configure_icon.png). 다음 [!UICONTROL 검색 및 목록] 대화 상자가 열립니다.

1. 에서 [!UICONTROL 표시] 탭에서 다음을 구성합니다.
   * in **[!UICONTROL 제목]**, Search &amp; Lister 구성 요소의 제목을 지정합니다. 지시 제목을 사용하면 사용자가 양식 목록에서 빠른 검색을 수행할 수 있습니다.
   * 에서 **[!UICONTROL 레이아웃]** 목록에서 레이아웃을 선택하여 양식을 카드 또는 목록 형식으로 표시합니다.
   * 선택 **[!UICONTROL 검색 숨기기]** 및 **[!UICONTROL 정렬 숨기기]** 를 클릭하여 검색 및 기능을 기준으로 정렬합니다.
   * in **[!UICONTROL 도구 설명]**&#x200B;를 누르고 있으면 구성 요소 위에 나타나는 도구 설명을 제공합니다.
1. 에서 [!UICONTROL 자산 폴더] 탭에서 양식을 가져와 페이지에 나열하는 위치를 지정합니다. 여러 폴더 위치를 구성할 수 있습니다.
1. 에서 [!UICONTROL 결과] 탭에서 페이지당 표시할 최대 양식 수를 구성합니다. 기본값은 페이지당 8개의 양식입니다.

### 링크 구성 요소 구성 {#configure-link-component}

링크 구성 요소를 사용하면 페이지에서 적응형 양식에 대한 링크를 제공할 수 있습니다. 구성하려면 구성 요소를 탭한 다음, ![구성 아이콘](assets/configure_icon.png). 다음 [!UICONTROL 링크 구성 요소 편집] 대화 상자가 열립니다.

1. 에서 [!UICONTROL 표시] 탭에서 링크 캡션과 도구 설명을 제공하여 링크로 표시되는 양식을 쉽게 식별할 수 있습니다.
1. 에서 [!UICONTROL 자산 정보] 탭에서 자산이 저장되는 저장소 경로를 지정합니다.
1. 에서 [!UICONTROL 쿼리 매개 변수] 탭에서 추가 매개 변수를 키-값 쌍 형식으로 지정합니다. 링크를 클릭하면 이러한 추가 매개 변수가 양식과 함께 전달됩니다.

## Adobe Sign을 사용하여 비동기 양식 제출 구성 {#configure-asynchronous-form-submission-using-adobe-sign}

모든 수신자가 서명식을 완료한 경우에만 적응형 양식을 제출하도록 구성할 수 있습니다. 아래 절차에 따라 Adobe Sign을 사용하여 설정을 구성하십시오.

1. 작성자 인스턴스의 편집 모드에서 적응형 양식을 엽니다.
1. 왼쪽 창에서 속성 아이콘을 탭하고 **[!UICONTROL 전자 서명]** 선택 사항입니다.
1. 선택 **[!UICONTROL Adobe Sign 활성화]**. 다양한 구성 옵션이 표시됩니다.
1. 에서 [!UICONTROL 양식 제출] 섹션에서 **[!UICONTROL 모든 수신자가 서명식을 완료함]** 옵션을 사용하여 양식 제출 작업을 구성할 수 있습니다. 여기서 서명을 위해 양식이 모든 수신자에게 처음 전송됩니다. 모든 수신자가 양식에 서명하면 양식만 제출됩니다.

## 적응형 Forms을 초안으로 저장 {#save-adaptive-forms-as-drafts}

양식을 나중에 완료할 수 있도록 초안 양식으로 저장할 수 있습니다. 양식을 초안으로 저장하는 방법에는 두 가지가 있습니다.
* 양식 구성 요소에 단추 같은 &quot;양식 저장&quot; 규칙을 만듭니다. 버튼을 클릭하면 규칙이 트리거되고 양식이 초안으로 저장됩니다.
* 지정된 이벤트 또는 구성된 시간 간격 이후에 양식을 저장하는 자동 저장 기능을 활성화합니다.

### 적응형 양식을 초안으로 저장하는 규칙 만들기 {#rule-to-save-adaptive-form-as-draft}

예를 들어, 양식 구성 요소에 &quot;양식 저장&quot; 규칙을 만들려면, 아래 단계를 수행하십시오.

1. 작성자 인스턴스에서 편집 모드에서 적응형 양식을 엽니다.
1. 왼쪽 창에서 ![구성 요소 아이콘](assets/components_icon.png) 그리고 [!UICONTROL 단추] 구성 요소를 생성하지 않습니다.
1. 탭하기 [!UICONTROL 단추] 구성 요소를 클릭한 다음 ![구성 아이콘](assets/configure_icon.png).
1. 탭하기 [!UICONTROL 규칙 편집] 아이콘을 클릭하여 규칙 편집기를 엽니다.
1. 탭 **[!UICONTROL 만들기]** 를 입력하여 규칙을 구성하고 만들 수 있습니다.
1. 에서 [!UICONTROL When] 섹션에서 &quot;클릭됨&quot;을 선택하고 [!UICONTROL Then] 섹션에서 &quot;양식 저장&quot; 옵션을 선택합니다.
1. 탭 **[!UICONTROL 완료]** 규칙을 저장하려면 을 클릭합니다.

### 자동 저장 활성화 {#enable-auto-save}

적응형 양식에 대해 다음과 같이 자동 저장 기능을 구성할 수 있습니다.

1. 작성자 인스턴스에서 편집 모드에서 적응형 양식을 엽니다.
1. 왼쪽 창에서 ![속성 아이콘](assets/configure_icon.png) 를 확장하고 [!UICONTROL 자동 저장] 선택 사항입니다.
1. 을(를) 선택합니다 **[!UICONTROL 활성화]** 양식의 자동 저장을 활성화하려면 확인란을 선택합니다. 다음 내용을 구성할 수 있습니다.
* 기본적으로 [!UICONTROL 적응형 양식 이벤트] 가 &quot;true&quot;로 설정되어 있으면 모든 이벤트 후 양식이 자동으로 저장됨을 의미합니다.
* in [!UICONTROL 트리거]를 사용하면 이벤트가 발생하거나 특정 시간 간격을 기준으로 자동 저장을 트리거하도록 구성할 수 있습니다.
