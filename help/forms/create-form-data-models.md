---
title: 양식 데이터 모델을 만드는 방법
description: Experience Manager Forms 데이터 통합은 양식 데이터 모델을 만들고 작업할 수 있는 직관적인 사용자 인터페이스를 제공합니다. 구성된 데이터 소스를 사용하거나 사용하지 않고 양식 데이터 모델을 만드는 방법을 알아봅니다.
feature: Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: 1f3104d4a986018675f751afa04fe0ed3b7f5c26
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 0%

---

# 양식 데이터 모델 만들기 {#create-form-data-model}

![데이터 통합](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] 데이터 통합은 양식 데이터 모델을 만들고 사용할 수 있는 직관적인 사용자 인터페이스를 제공합니다. 양식 데이터 모델은 데이터 교환을 위해 데이터 소스를 사용합니다. 그러나 데이터 소스를 사용하거나 사용하지 않고 양식 데이터 모델을 만들 수 있습니다. 데이터 소스를 구성했는지 여부에 따라 데이터 모델에서 을 만드는 두 가지 방법이 있습니다.

* **사전 구성된 데이터 소스 사용**: 에 설명된 대로 데이터 소스를 구성한 경우 [데이터 소스 구성](configure-data-sources.md)양식 데이터 모델을 만드는 동안 선택할 수 있습니다. 선택한 데이터 소스의 모든 데이터 모델 개체, 속성 및 서비스를 양식 데이터 모델에서 사용할 수 있도록 합니다.

* **데이터 소스 없음**: 양식 데이터 모델에 대해 데이터 소스를 구성하지 않은 경우 데이터 소스 없이 만들 수 있습니다. 양식 데이터 모델을 사용하여 적응형 Forms을 작성할 수 있습니다 <!--and interactive communication--> 샘플 데이터를 사용하여 테스트해 보십시오. 데이터 소스를 사용할 수 있으면 연결된 적응형 Forms에 자동으로 반영되는 양식 데이터 모델을 데이터 소스에 바인딩할 수 있습니다<!--and interactive communications-->.

>[!NOTE]
>
>둘 다 구성원이어야 합니다 **fdm-author** 및 **forms-user** 양식 데이터 모델을 만들고 사용할 수 있는 그룹입니다. 다음 사항에 문의하십시오. [!DNL Experience Manager] 관리자가 그룹의 구성원이 될 수 있습니다.

## 양식 데이터 모델 만들기 {#data-sources}

에 설명된 대로 양식 데이터 모델에 사용할 데이터 소스를 구성했는지 확인합니다. [데이터 소스 구성](configure-data-sources.md). 구성된 데이터 소스를 기반으로 양식 데이터 모델을 만들려면 다음을 수행하십시오.

1. in [!DNL Experience Manager] 작성자 인스턴스, 탐색 **[!UICONTROL Forms > 데이터 통합]**.
1. 탭 **[!UICONTROL 만들기 > 양식 데이터 모델]**.
1. 양식 데이터 모델 만들기 대화 상자에서 다음을 수행합니다.

   * 양식 데이터 모델의 이름을 지정합니다.
   * (**선택 사항입니다**) 양식 데이터 모델의 제목, 설명 및 태그를 지정합니다.
   * (**데이터 소스가 구성된 경우에만 선택 사항 및 적용 가능**) 확인 표시 아이콘을 탭합니다 **[!UICONTROL 데이터 소스 구성]** 필드를 선택하고 사용할 데이터 소스에 대한 클라우드 서비스가 있는 구성 노드를 선택합니다. 여기서는 다음 페이지에서 선택할 수 있는 데이터 소스 목록을 선택한 구성 노드에서 사용할 수 있는 데이터 소스 목록으로 제한합니다. 하지만, [!DNL Experience Manager] 사용자 프로필 데이터 소스는 기본적으로 나열됩니다. 구성 노드를 선택하지 않으면 모든 구성 노드의 데이터 소스가 나열됩니다.

1. 탭 **[!UICONTROL 다음]**.

1. (**데이터 소스가 구성된 경우에만 적용 가능합니다**) **[!UICONTROL 데이터 소스 선택]** 화면에 사용 가능한 데이터 소스가 표시됩니다(있는 경우). 양식 데이터 모델에 사용할 데이터 소스를 선택합니다.
1. 탭 **[!UICONTROL 만들기]** 확인 대화 상자에서 **[!UICONTROL 열기]** 를 클릭하여 양식 데이터 모델 편집기를 엽니다.

   양식 데이터 모델 편집기 UI의 다양한 구성 요소를 검토하겠습니다.

   ![세 가지 데이터 소스를 포함하는 양식 데이터 모델(RESTful 서비스, [!DNL Experience Manager] 사용자 프로파일 및 RDBMS](assets/fdm-ui.png)

   A. **[!UICONTROL 데이터 소스]** 양식 데이터 모델의 데이터 소스를 나열합니다. 데이터 소스를 확장하여 해당 데이터 모델 개체 및 서비스를 봅니다.

   B. **[!UICONTROL 데이터 소스 정의 새로 고침]** 구성된 데이터 소스에서 데이터 소스 정의의 변경 사항을 가져오고 양식 데이터 모델 편집기의 데이터 소스 탭에서 업데이트합니다.

   C. **[!UICONTROL 모델]** 추가된 데이터 모델 개체가 표시되는 콘텐츠 영역입니다.

   D. **[!UICONTROL 서비스]** 추가된 데이터 소스 작업 또는 서비스가 표시되는 콘텐츠 영역입니다.

   E. **[!UICONTROL 도구 모음]** 양식 데이터 모델로 작업하는 도구입니다. 도구 모음에는 양식 데이터 모델에서 선택한 객체에 따라 더 많은 옵션이 표시됩니다.

   F. **[!UICONTROL 선택 항목 추가]** 선택한 데이터 모델 개체 및 서비스를 양식 데이터 모델에 추가합니다.

양식 데이터 모델 편집기와 양식 데이터 모델을 편집하고 구성하는 데 사용할 수 있는 방법에 대한 자세한 내용은 다음을 참조하십시오 [양식 데이터 모델 작업](work-with-form-data-model.md).

## 데이터 소스 업데이트 {#update}

데이터 소스를 기존 양식 데이터 모델에 추가하거나 업데이트하려면 다음을 수행하십시오.

1. 이동 **[!UICONTROL Forms > 데이터 통합]**&#x200B;데이터 소스를 추가하거나 업데이트할 양식 데이터 모델 을 선택하고 **[!UICONTROL 속성]**.
1. 양식 데이터 모델 속성에서 **[!UICONTROL 소스 업데이트]** 탭.

   에서 **[!UICONTROL 소스 업데이트]** 탭:

   * 에서 찾아보기 아이콘을 누릅니다 **[!UICONTROL 컨텍스트 인식 구성]** 필드를 선택하고 추가할 데이터 소스에 대한 클라우드 구성이 있는 구성 노드를 선택합니다. 노드를 선택하지 않으면 `global` 노드를 탭하면 나열된 상태로 표시됩니다 **[!UICONTROL 소스 추가]**.

   * 새 데이터 소스를 추가하려면 **[!UICONTROL 소스 추가]** 양식 데이터 모델에 추가할 데이터 소스를 선택합니다. 에 구성된 모든 데이터 소스 `global` 및 선택된 구성 노드가 있으면 표시됩니다.

   * 기존 데이터 소스를 동일한 유형의 다른 데이터 소스로 바꾸려면 **[!UICONTROL 편집]** 아이콘을 클릭하고 사용 가능한 데이터 소스 목록에서 를 선택합니다.
   * 기존 데이터 소스를 삭제하려면 **[!UICONTROL 삭제]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 데이터 소스의 데이터 모델 개체가 양식 데이터 모델에 추가되면 삭제 아이콘이 비활성화됩니다.

      ![fdm-properties](assets/fdm-properties.png)

1. 탭 **[!UICONTROL 저장 및 닫기]** 업데이트를 저장하려면 을 클릭합니다.

>[!NOTE]
>
>양식 데이터 모델에서 새 데이터 소스를 추가하거나 기존 데이터 소스를 업데이트하면 적응형 Forms에서 바인딩 참조를 적절하게 업데이트해야 합니다<!--and interactive communications--> 업데이트된 양식 데이터 모델을 사용합니다.

## 특정 실행 모드에 대한 컨텍스트 인식 구성 {#runmode-specific-context-aware-config}

[!UICONTROL 양식 데이터 모델] 활용 [Sling 컨텍스트 인식 구성](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/context-aware-configs.html) 다른 데이터 소스 매개 변수를 지원하여 다른 데이터 소스와 연결하도록 지원 [!DNL Experience Manager] 모드를 실행합니다.

When [!UICONTROL 양식 데이터 모델] 클라우드 구성을 사용하여 매개 변수를 저장합니다. 이 구성 요소는 체크 인하고 소스 제어(Cloud-Manager GIT 저장소)를 통해 배포될 때 모든 실행 모드(개발, 스테이지 및 프로덕션)에 대해 동일한 매개 변수로 클라우드 구성을 만듭니다. 그러나 테스트 및 프로덕션 환경에 대해 다른 데이터 세트가 있어야 하는 사용 사례의 경우 다른 용도로 데이터 소스 매개 변수(예: 데이터 소스 URL)를 사용합니다 [!DNL Experience Manager] 모드를 실행합니다.

이를 위해서는 데이터 소스 매개 변수-값 쌍을 포함하는 OSGi 구성을 만들어야 합니다. 이 값은 같은 쌍을 [!UICONTROL 양식 데이터 모델] 런타임 시 클라우드 구성. OSGi 구성은 이러한 실행 모드를 기본적으로 지원하므로 실행 모드에 따라 데이터 소스 매개 변수를 다른 값으로 재정의할 수 있습니다.

에서 배포별 클라우드 구성을 활성화하려면 [!UICONTROL 양식 데이터 모델]:

1. 로컬 개발 인스턴스에서 클라우드 구성을 만듭니다. 자세한 단계는 [데이터 소스를 구성하는 방법](/help/forms/configure-data-sources.md).

1. 클라우드 구성을 파일 시스템에 저장합니다.
   1. 필터를 사용하여 패키지 만들기 `/conf/{foldername}/settings/cloudconfigs/fdm`. 동일한 항목 사용 `{foldername}` 로서의. 및 바꾸기 `fdm` with `azurestorage` Azure 저장소 구성용.
   1. 패키지를 빌드하고 다운로드합니다. 자세한 내용은 [패키지 작업](/help/implementing/developing/tools/package-manager.md).

1. 의 클라우드 구성 통합 [!DNL Experience Manager] Archetype 프로젝트.
   1. 다운로드한 패키지의 압축을 해제합니다.
   1. 복사 `jcr_root` 폴더를 만들고 `ui.content` > `src` > `main` > `content`.
   1. 업데이트 `ui.content` > `src` > `main` > `content` > `META-INF` > `vault` > `filter.xml` 필터를 포함하십시오. `/conf/{foldername}/settings/cloudconfigs/fdm`. 자세한 내용은 [AEM Project Archetype의 ui.content 모듈](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uicontent.html). 이 원형 프로젝트가 CM 파이프라인을 통해 배포되면 모든 환경(또는 실행 모드)에 동일한 클라우드 구성이 설치됩니다. 환경을 기반으로 클라우드 구성의 필드(예: URL)를 변경하려면 다음 단계에서 설명한 OSGi 구성을 사용하십시오.

1. Apache Sling 컨텍스트 인식 구성을 만듭니다. OSGi 구성을 만들려면:
   1. **에서 OSGi 구성 파일 설정 [!DNL Experience Manager] 원형 프로젝트.**
PID를 사용하여 OSGi Factory 구성 파일 만들기 
`org.apache.sling.caconfig.impl.override.OsgiConfigurationOverrideProvider`. 실행 모드별로 값을 변경해야 하는 각 실행 모드 폴더 아래에 동일한 이름으로 파일을 만듭니다. 자세한 내용은 [에 대한 OSGi 구성 [!DNL Adobe Experience Manager]](/help/implementing/deploying/configuring-osgi.md#creating-sogi-configurations).

   1. **OSGI 구성 json을 설정합니다.** Apache Sling 컨텍스트 인식 구성 무시 공급자를 사용하려면 다음을 수행하십시오.
      1. 로컬 개발 인스턴스에서 `/system/console/configMgr`, 이름이 인 공장 OSGi 구성을 선택합니다. **[!UICONTROL Apache Sling 컨텍스트 인식 구성 무시 공급자: OSGi 구성]**.
      1. 설명을 제공합니다.
      1. 선택 **[!UICONTROL 활성화됨]**.
      1. 재정의에서 sling 재정의 구문의 환경을 기반으로 변경해야 하는 필드를 제공합니다. 자세한 내용은 [Apache Sling 컨텍스트 인식 구성 - 재정의](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration-override.html#override-syntax). (예: `cloudconfigs/fdm/{configName}/url="newURL"`)
여러 항목을 선택하여 추가할 수 있습니다 **[!UICONTROL +]**.
      1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.
      1. OSGi 구성 JSON을 가져오려면 다음 단계를 수행하십시오. [AEM SDK Quickstart를 사용하여 OSGi 구성 생성](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart).
      1. 이전 단계에서 만든 OSGi Factory 구성 파일에 JSON을 배치합니다.
      1. 값 변경 `newURL` 환경(또는 런타임 모드)을 기반으로 합니다.
      1. 런타임 모드를 기반으로 암호 값을 변경하려면 [cloud manager API](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) 및에서 나중에 참조할 수 있습니다. [OSGi 구성](/help/implementing/deploying/configuring-osgi.md#secret-configuration-values).
이 원형 프로젝트가 CM 파이프라인을 통해 배포되면 재정의는 다른 환경(또는 실행 모드)에서 다른 값을 제공합니다.

      >[!NOTE]
      >
      >[!DNL Adobe Managed Service] 사용자는 crypto 지원을 사용하여 암호 값을 암호화할 수 있습니다(자세한 내용은 [구성 속성에 대한 암호화 지원](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/encryption-support-for-configuration-properties.html#enabling-encryption-support) 다음 값 안에 암호화된 텍스트를 배치합니다. [컨텍스트 인식 구성은 서비스 팩 6.5.13.0에서 사용할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html#runmode-specific-context-aware-config).

1. 옵션을 사용하여 데이터 소스 정의를 새로 고침하여 [양식 데이터 모델 편집기](#data-sources) FDM UI를 통해 FDM 캐시를 새로 고치고 최신 구성을 가져오려면 다음을 수행하십시오.

## 다음 단계 {#next-steps}

이제 데이터 소스가 추가된 양식 데이터 모델이 있습니다. 그런 다음 양식 데이터 모델을 편집하여 데이터 모델 개체 및 서비스를 추가 및 구성하고, 데이터 모델 개체 간의 연결을 추가하고, 속성을 편집하고, 사용자 지정 데이터 모델 개체 및 속성을 추가하고, 샘플 데이터를 생성하는 등의 작업을 수행할 수 있습니다.

자세한 내용은 [양식 데이터 모델 작업](work-with-form-data-model.md).
