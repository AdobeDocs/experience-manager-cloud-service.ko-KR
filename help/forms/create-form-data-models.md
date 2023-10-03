---
title: 양식 데이터 모델을 만드는 방법
description: 적응형 양식 또는 AEM Workflow를 사용하여 양식 데이터 모델(FDM)을 만들고, 데이터를 데이터 소스로 전송하거나 검색하는 방법에 대해 알아봅니다.
feature: Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: e2f2aa18e2412bc92d1385a125281ecfb81f2ce8
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 1%

---

# 양식 데이터 모델 만들기 {#create-form-data-model}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html) |
| AEM as a Cloud Service | 이 문서 |


![데이터 통합](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] 데이터 통합은 양식 데이터 모델을 만들고 작업할 수 있는 직관적인 사용자 인터페이스를 제공합니다. 양식 데이터 모델은 데이터 교환을 위해 데이터 소스를 사용합니다. 그러나 데이터 소스를 사용하거나 사용하지 않고 양식 데이터 모델을 만들 수 있습니다. 데이터 소스를 구성했는지 여부에 따라 데이터 모델에서 를 만드는 두 가지 방법이 있습니다.

* **사전 구성된 데이터 소스 사용**: 다음에 설명된 대로 데이터 소스를 구성한 경우 [데이터 소스 구성](configure-data-sources.md), 양식 데이터 모델을 만드는 동안 선택할 수 있습니다. 선택한 데이터 소스의 모든 데이터 모델 개체, 속성 및 서비스를 양식 데이터 모델에서 사용할 수 있도록 합니다.

* **데이터 소스 제외**: 양식 데이터 모델에 대해 데이터 소스를 구성하지 않은 경우에도 데이터 소스 없이 만들 수 있습니다. 양식 데이터 모델을 사용하여 적응형 Forms을 작성할 수 있습니다 <!--and interactive communication--> 샘플 데이터를 사용하여 테스트합니다. 데이터 소스를 사용할 수 있으면 양식 데이터 모델을 데이터 소스에 바인딩할 수 있으며, 이는 연결된 적응형 Forms에 자동으로 반영됩니다<!--and interactive communications-->.

>[!NOTE]
>
>두 그룹의 멤버여야 합니다. **fdm-author** 및 **forms-user** 양식 데이터 모델을 만들고 작업할 수 있는 그룹입니다. 다음으로 연락 [!DNL Experience Manager] 관리자가 그룹의 구성원이 되도록 합니다.

## 양식 데이터 모델 만들기 {#data-sources}

에 설명된 대로 양식 데이터 모델에서 사용할 데이터 소스를 구성했는지 확인합니다. [데이터 소스 구성](configure-data-sources.md). 구성된 데이터 소스를 기반으로 양식 데이터 모델을 만들려면 다음을 수행하십시오.

1. 위치 [!DNL Experience Manager] 작성자 인스턴스, 다음으로 이동 **[!UICONTROL Forms > 데이터 통합]**.
1. 누르기 **[!UICONTROL 만들기 > 양식 데이터 모델]**.
1. 양식 데이터 모델 만들기 대화 상자에서

   * 양식 데이터 모델의 이름을 지정합니다.
   * (**선택 사항**) 양식 데이터 모델의 제목, 설명 및 태그를 지정합니다.
   * (**선택 사항이며 데이터 소스가 구성된 경우에만 적용할 수 있습니다**) 옆에 있는 확인 표시 아이콘을 누릅니다. **[!UICONTROL 데이터 소스 구성]** 필드 를 선택하고 사용할 데이터 소스에 대한 클라우드 서비스가 있는 구성 노드를 선택합니다. 다음 페이지에서 선택할 수 있는 데이터 소스 목록을 선택한 구성 노드에서 사용할 수 있는 데이터 소스로 제한합니다. 단, 모두 [!DNL Experience Manager] 사용자 프로필 데이터 소스는 기본적으로 나열됩니다. 구성 노드를 선택하지 않으면 모든 구성 노드의 데이터 소스가 나열됩니다.

1. 누르기 **[!UICONTROL 다음]**.

1. (**데이터 소스가 구성된 경우에만 적용 가능**) **[!UICONTROL 데이터 소스 선택]** 화면에 사용 가능한 데이터 소스(있는 경우)가 나열됩니다. 양식 데이터 모델에서 사용할 데이터 소스를 선택합니다.
1. 누르기 **[!UICONTROL 만들기]** 확인 대화 상자에서 다음을 누릅니다. **[!UICONTROL 열기]** 을 클릭하여 양식 데이터 모델 편집기를 엽니다.

   양식 데이터 모델 편집기 UI의 다양한 구성 요소를 검토해 보겠습니다.

   ![RESTful 서비스, [!DNL Experience Manager] 사용자 프로필 및 RDBMS](assets/fdm-ui.png)

   A. **[!UICONTROL 데이터 소스]** 양식 데이터 모델의 데이터 소스를 나열합니다. 데이터 소스를 확장하여 해당 데이터 모델 개체 및 서비스를 봅니다.

   B. **[!UICONTROL 데이터 소스 정의 새로 고침]** 구성된 데이터 소스의 데이터 소스 정의에서 모든 변경 사항을 가져오고 양식 데이터 모델 편집기의 데이터 소스 탭에서 업데이트합니다.

   C. **[!UICONTROL 모델]** 추가된 데이터 모델 개체가 표시되는 콘텐츠 영역입니다.

   D. **[!UICONTROL 서비스]** 추가된 데이터 소스 작업 또는 서비스가 표시되는 컨텐츠 영역입니다.

   E. **[!UICONTROL 도구 모음]** 양식 데이터 모델을 사용하여 작업하는 도구입니다. 도구 모음에는 양식 데이터 모델에서 선택한 개체에 따라 더 많은 옵션이 표시됩니다.

   F **[!UICONTROL 선택 항목 추가]** 선택한 데이터 모델 개체 및 서비스를 양식 데이터 모델에 추가합니다.

양식 데이터 모델 편집기에 대한 자세한 내용과 이 편집기로 양식 데이터 모델을 편집하고 구성하는 방법에 대한 자세한 내용은 [양식 데이터 모델 작업](work-with-form-data-model.md).

## 데이터 소스 업데이트 {#update}

기존 양식 데이터 모델에 데이터 소스를 추가하거나 업데이트하려면 다음을 수행합니다.

1. 다음으로 이동 **[!UICONTROL Forms > 데이터 통합]**&#x200B;데이터 소스를 추가하거나 업데이트할 양식 데이터 모델을 선택한 다음 를 누릅니다 **[!UICONTROL 속성]**.
1. 양식 데이터 모델 속성에서 **[!UICONTROL 소스 업데이트]** 탭.

   다음에서 **[!UICONTROL 소스 업데이트]** 탭:

   * 에서 찾아보기 아이콘을 탭합니다. **[!UICONTROL 컨텍스트 인식 구성]** 필드를 지정하고 추가하려는 데이터 소스에 대한 클라우드 구성이 있는 구성 노드를 선택합니다. 노드를 선택하지 않으면 클라우드 구성은 `global` 을 탭하면 노드가 나열됩니다. **[!UICONTROL 소스 추가]**.

   * 새 데이터 소스를 추가하려면 **[!UICONTROL 소스 추가]** 및 양식 데이터 모델에 추가할 데이터 소스를 선택합니다. 모든 데이터 소스가에 구성됨 `global` 선택한 구성 노드가 있으면 표시됩니다.

   * 기존 데이터 소스를 동일한 유형의 다른 데이터 소스로 바꾸려면 **[!UICONTROL 편집]** ( 데이터 소스 아이콘)을 클릭하고 사용 가능한 데이터 소스 목록에서 을 선택합니다.
   * 기존 데이터 소스를 삭제하려면 **[!UICONTROL 삭제]** 데이터 소스에 대한 아이콘. 데이터 소스의 데이터 모델 객체가 양식 데이터 모델에 추가되는 경우 삭제 아이콘이 비활성화됩니다.

     ![fdm-properties](assets/fdm-properties.png)

1. 누르기 **[!UICONTROL 저장 및 닫기]** 업데이트를 저장합니다.

>[!NOTE]
>
>양식 데이터 모델에서 새 데이터 소스를 추가하거나 기존 데이터 소스를 업데이트한 후에는 적응형 Forms에서 바인딩 참조를 적절하게 업데이트해야 합니다<!--and interactive communications--> 업데이트된 양식 데이터 모델을 사용합니다.

## 특정 실행 모드에 대한 컨텍스트 인식 구성 {#runmode-specific-context-aware-config}

[!UICONTROL 양식 데이터 모델] 활용 [슬링 컨텍스트 인식 구성](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/context-aware-configs.html) 다양한 데이터 소스 매개 변수를 지원하여 다양한 데이터 소스에 연결 [!DNL Experience Manager] 실행 모드.

날짜 [!UICONTROL 양식 데이터 모델] 클라우드 구성을 사용하여 매개 변수를 저장합니다. 이 매개 변수는 체크 인하고 소스 제어(Cloud-Manager GIT 저장소)를 통해 배포하면 모든 실행 모드(개발, 스테이징 및 프로덕션)에 대해 동일한 매개 변수로 클라우드 구성이 만들어집니다. 그러나 테스트 및 프로덕션 환경에 대해 서로 다른 데이터 세트를 가져야 하는 사용 사례의 경우 서로 다른 데이터 소스 매개 변수(예: 데이터 소스 URL)를 사용합니다 [!DNL Experience Manager] 실행 모드.

이를 위해서는 데이터 소스 매개변수-값 쌍을 포함하는 OSGi 구성을 생성해야 합니다. 이는 의 동일한 쌍을 재정의합니다. [!UICONTROL 양식 데이터 모델] 런타임에 클라우드 구성 OSGi 구성은 기본적으로 이러한 실행 모드를 지원하기 때문에 실행 모드에 따라 데이터 소스 매개변수를 다른 값으로 재정의할 수 있습니다.

에서 배포별 클라우드 구성을 활성화하려면 [!UICONTROL 양식 데이터 모델]:

1. 로컬 개발 인스턴스에 클라우드 구성을 만듭니다. 자세한 단계는 를 참조하십시오. [데이터 소스 구성 방법](/help/forms/configure-data-sources.md).

1. 클라우드 구성을 파일 시스템에 저장합니다.
   1. 필터로 패키지 만들기 `/conf/{foldername}/settings/cloudconfigs/fdm`. 동일한 항목 사용 `{foldername}` 1단계에서와 같습니다. 및 바꾸기 `fdm` 포함 `azurestorage` Azure 스토리지 구성용
   1. 패키지 빌드 및 다운로드. 자세한 내용은 [패키지 작업](/help/implementing/developing/tools/package-manager.md).

1. 에서 클라우드 구성 통합 [!DNL Experience Manager] Archetype 프로젝트
   1. 다운로드한 패키지의 압축을 풉니다.
   1. 복사 `jcr_root` 폴더를 삭제하고 다음 위치에 저장합니다. `ui.content` > `src` > `main` > `content`.
   1. 업데이트 `ui.content` > `src` > `main` > `content` > `META-INF` > `vault` > `filter.xml` 필터를 포함합니다. `/conf/{foldername}/settings/cloudconfigs/fdm`. 자세한 내용은 [AEM Project Archetype의 ui.content 모듈](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uicontent.html). 이 Archetype 프로젝트가 CM 파이프라인을 통해 배포되면 모든 환경(또는 실행 모드)에 동일한 클라우드 구성이 설치됩니다. 환경을 기반으로 클라우드 구성의 필드(예: URL) 값을 변경하려면 다음 단계에서 설명한 OSGi 구성을 사용하십시오.

1. Apache Sling 컨텍스트 인식 구성을 만듭니다. OSGi 구성을 생성하려면 다음을 수행합니다.
   1. **에서 OSGi 구성 파일 설정 [!DNL Experience Manager] Archetype 프로젝트**
PID로 OSGi 출하 시 구성 파일 생성 `org.apache.sling.caconfig.impl.override.OsgiConfigurationOverrideProvider`. 실행 모드별로 값을 변경해야 하는 각 실행 모드 폴더에 이름이 동일한 파일을 만듭니다. 자세한 내용은 [다음에 대한 OSGi 구성 [!DNL Adobe Experience Manager]](/help/implementing/deploying/configuring-osgi.md#creating-sogi-configurations).

   1. **OSGI 구성 json을 설정합니다.** Apache Sling 컨텍스트 인식 구성 재정의 공급자를 사용하려면 다음을 수행하십시오.
      1. 로컬 개발 인스턴스에서 `/system/console/configMgr`를 클릭하고, 다음과 같은 이름의 공장 OSGi 구성을 선택합니다. **[!UICONTROL Apache Sling 컨텍스트 인식 구성 재정의 공급자: OSGi 구성]**.
      1. 설명을 입력합니다.
      1. 선택 **[!UICONTROL 활성화됨]**.
      1. 재정의에서 sling 재정의 구문에서 환경에 따라 변경해야 하는 필드를 제공합니다. 자세한 내용은 [Apache Sling 컨텍스트 인식 구성 - 재정의](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration-override.html#override-syntax). 예: `cloudconfigs/fdm/{configName}/url="newURL"`
을(를) 선택하여 여러 재정의를 추가할 수 있습니다. **[!UICONTROL +]**.
      1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.
      1. OSGi 구성 JSON을 가져오려면 의 단계를 따릅니다. [AEM SDK 빠른 시작을 사용하여 OSGi 구성 생성](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart).
      1. 이전 단계에서 생성한 OSGi 팩토리 구성 파일에 JSON을 배치합니다.
      1. 값 변경 `newURL` 환경(또는 실행 모드)을 기반으로 합니다.
      1. 실행 모드에 따라 비밀 값을 변경하려면 다음을 사용하여 비밀 변수를 만들 수 있습니다. [cloud manager API](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) 및에서 참조할 수 있습니다. [OSGi 구성](/help/implementing/deploying/configuring-osgi.md#secret-configuration-values).
이 Archetype 프로젝트가 CM 파이프라인을 통해 배포되면 재정의는 다른 환경(또는 실행 모드)에서 다른 값을 제공합니다.
      >[!NOTE]
      >
      >[!DNL Adobe Managed Service] 사용자는 암호화 지원을 사용하여 비밀 값을 암호화할 수 있습니다(자세한 내용은 다음을 참조하십시오.) [구성 속성에 대한 암호화 지원](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/encryption-support-for-configuration-properties.html#enabling-encryption-support) 다음 뒤에 있는 값에 암호화된 텍스트 넣기 [컨텍스트 인식 구성은 서비스 팩 6.5.13.0에서 사용할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html#runmode-specific-context-aware-config).

1. 에서 데이터 소스 정의를 새로 고치는 옵션을 사용하여 데이터 소스 정의를 새로 고칩니다. [양식 데이터 모델 편집기](#data-sources) 를 사용하여 FDM UI를 통해 FDM 캐시를 새로 고치고 최신 구성을 가져올 수 있습니다.

## 다음 단계 {#next-steps}

이제 데이터 소스가 추가된 양식 데이터 모델이 있습니다. 그런 다음 양식 데이터 모델을 편집하여 데이터 모델 개체 및 서비스를 추가 및 구성하고, 데이터 모델 개체 간의 연결을 추가하고, 속성을 편집하고, 사용자 지정 데이터 모델 개체 및 속성을 추가하고, 샘플 데이터를 생성하는 등의 작업을 수행할 수 있습니다.

자세한 내용은 [양식 데이터 모델 작업](work-with-form-data-model.md).
