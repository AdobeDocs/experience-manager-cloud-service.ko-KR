---
title: 양식 데이터 모델(FDM)을 만드는 방법
description: 적응형 양식 또는 AEM Workflow를 사용하여 양식 데이터 모델(FDM)을 만들고, 데이터를 데이터 소스로 전송하거나 검색하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner, Intermediate
exl-id: b17b7441-912c-44c7-a835-809f014a8c86
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '1543'
ht-degree: 1%

---

# 양식 데이터 모델(FDM) 생성 {#create-form-data-model}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html) |
| AEM as a Cloud Service | 이 문서 |


![데이터 통합](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] 데이터 통합은 양식 데이터 모델을 만들고 작업할 수 있는 직관적인 사용자 인터페이스를 제공합니다. FDM(양식 데이터 모델)은 데이터 교환을 위해 데이터 소스를 사용합니다. 하지만 데이터 소스를 포함하거나 포함하지 않고 FDM(양식 데이터 모델)을 만들 수 있습니다. 데이터 소스를 구성했는지 여부에 따라 데이터 모델에서 를 만드는 두 가지 방법이 있습니다.

* **미리 구성된 데이터 소스 사용**: [데이터 소스 구성](configure-data-sources.md)에 설명된 대로 데이터 소스를 구성한 경우 양식 데이터 모델(FDM)을 만드는 동안 선택할 수 있습니다. 선택한 데이터 소스의 모든 데이터 모델 개체, 속성 및 서비스를 FDM(양식 데이터 모델)에서 사용할 수 있도록 합니다.

* **데이터 소스 없음**: 양식 데이터 모델(FDM)에 대한 데이터 소스를 구성하지 않은 경우에도 데이터 소스 없이 만들 수 있습니다. FDM(양식 데이터 모델)을 사용하여 적응형 Forms <!--and interactive communication-->을(를) 작성하고 샘플 데이터를 사용하여 테스트할 수 있습니다. 데이터 소스를 사용할 수 있으면 FDM(양식 데이터 모델)을 데이터 소스와 바인딩할 수 있습니다. 이 데이터 소스는 연결된 적응형 Forms<!--and interactive communications-->에 자동으로 반영됩니다.

>[!NOTE]
>
>양식 데이터 모델(FDM)을 만들고 작업하려면 **fdm-author** 및 **forms-user** 그룹의 멤버여야 합니다. 그룹의 구성원이 되려면 [!DNL Experience Manager] 관리자에게 문의하십시오.

## 양식 데이터 모델(FDM) 생성 {#data-sources}

[데이터 소스 구성](configure-data-sources.md)에 설명된 대로 양식 데이터 모델(FDM)에서 사용할 데이터 소스를 구성했는지 확인합니다. 구성된 데이터 소스를 기반으로 양식 데이터 모델(FDM)을 생성하려면 다음을 수행합니다.

1. [!DNL Experience Manager] 작성자 인스턴스에서 **[!UICONTROL Forms > 데이터 통합]**(으)로 이동합니다.
1. **[!UICONTROL 만들기 > 양식 데이터 모델]**&#x200B;을 선택합니다.
1. 양식 데이터 모델 만들기 대화 상자에서

   * 양식 데이터 모델(FDM)의 이름을 지정합니다.
   * (**선택 사항**) 양식 데이터 모델(FDM)의 제목, 설명 및 태그를 지정합니다.
   * (**데이터 원본이 구성된 경우에만 적용 가능**) **[!UICONTROL 데이터 Source 구성]** 필드 옆에 있는 확인 표시 아이콘을 선택하고 사용할 데이터 원본에 대한 클라우드 서비스가 있는 구성 노드를 선택합니다. 다음 페이지에서 선택할 수 있는 데이터 소스 목록을 선택한 구성 노드에서 사용할 수 있는 데이터 소스로 제한합니다. 그러나 기본적으로 [!DNL Experience Manager]개의 사용자 프로필 데이터 원본이 나열됩니다. 구성 노드를 선택하지 않으면 모든 구성 노드의 데이터 소스가 나열됩니다.

1. **[!UICONTROL 다음]**&#x200B;을 선택합니다.

1. (**데이터 원본이 구성된 경우에만 적용 가능**) **[!UICONTROL 데이터 원본 선택]** 화면에 사용 가능한 데이터 원본이 있는 경우 표시됩니다. 양식 데이터 모델에서 사용할 데이터 소스를 선택합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택하고 확인 대화 상자에서 **[!UICONTROL 열기]**&#x200B;를 선택하여 양식 데이터 모델 편집기를 엽니다.

   양식 데이터 모델 편집기 UI의 다양한 구성 요소를 검토해 보겠습니다.

   ![RESTful 서비스, [!DNL Experience Manager] 사용자 프로필 및 RDBMS의 세 가지 데이터 원본이 있는 양식 데이터 모델](assets/fdm-ui.png)

   A. **[!UICONTROL 데이터 원본]** 양식 데이터 모델의 데이터 원본을 나열합니다. 데이터 소스를 확장하여 해당 데이터 모델 개체 및 서비스를 봅니다.

   B. **[!UICONTROL 데이터 Source 정의 새로 고침]** 구성된 데이터 원본에서 데이터 원본 정의의 변경 내용을 가져와서 양식 데이터 모델 편집기의 데이터 원본 탭에서 업데이트합니다.

   C. 추가된 데이터 모델 개체가 표시되는 **[!UICONTROL 모델]** 콘텐츠 영역입니다.

   D. 추가된 데이터 원본 작업 또는 서비스가 표시되는 **[!UICONTROL 서비스]** 콘텐츠 영역입니다.

   예. **[!UICONTROL 도구 모음]** 양식 데이터 모델(FDM) 을 사용하는 도구입니다. 도구 모음에는 양식 데이터 모델(FDM)에서 선택한 객체에 따라 더 많은 옵션이 표시됩니다.

   F. **[!UICONTROL 선택한 항목 추가]** 선택한 데이터 모델 개체 및 서비스를 양식 데이터 모델에 추가합니다.

양식 데이터 모델 편집기에 대한 자세한 내용과 이 편집기로 양식 데이터 모델(FDM)을 편집하고 구성하는 방법에 대한 자세한 내용은 [양식 데이터 모델 작업](work-with-form-data-model.md)을 참조하십시오.

## 데이터 소스 업데이트 {#update}

기존 양식 데이터 모델(FDM)에 데이터 소스를 추가하거나 업데이트하려면 다음을 수행합니다.

1. **[!UICONTROL Forms > 데이터 통합]**(으)로 이동하여 데이터 소스를 추가하거나 업데이트할 양식 데이터 모델(FDM)을 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. 양식 데이터 모델 속성에서 **[!UICONTROL Source 업데이트]** 탭으로 이동합니다.

   **[!UICONTROL Source 업데이트]** 탭에서:

   * **[!UICONTROL 컨텍스트 인식 구성]** 필드에서 찾아보기 아이콘을 선택하고 추가하려는 데이터 원본에 대한 클라우드 구성이 있는 구성 노드를 선택하십시오. 노드를 선택하지 않으면 **[!UICONTROL 소스 추가]**&#x200B;를 선택하면 `global` 노드에만 있는 클라우드 구성이 나열됩니다.

   * 새 데이터 소스를 추가하려면 **[!UICONTROL 소스 추가]**&#x200B;를 선택하고 양식 데이터 모델(FDM)에 추가할 데이터 소스를 선택합니다. `global`에 구성된 모든 데이터 원본과 선택한 구성 노드(있는 경우)가 표시됩니다.

   * 기존 데이터 소스를 같은 유형의 다른 데이터 소스로 바꾸려면 데이터 소스에 대한 **[!UICONTROL 편집]** 아이콘을 선택하고 사용 가능한 데이터 소스 목록에서 선택하십시오.
   * 기존 데이터 원본을 삭제하려면 데이터 원본에 대한 **[!UICONTROL 삭제]** 아이콘을 선택하십시오. 데이터 소스의 데이터 모델 객체가 양식 데이터 모델(FDM)에 추가된 경우 삭제 아이콘이 비활성화됩니다.

     ![fdm-properties](assets/fdm-properties.png)

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하여 업데이트를 저장합니다.

>[!NOTE]
>
>양식 데이터 모델(FDM)에서 새 데이터 소스를 추가하거나 기존 데이터 소스를 업데이트한 후에는 업데이트된 양식 데이터 모델(FDM)을 사용하는 적응형 Forms<!--and interactive communications-->에서 바인딩 참조를 적절하게 업데이트해야 합니다.

## 특정 실행 모드에 대한 컨텍스트 인식 구성 {#runmode-specific-context-aware-config}

[!UICONTROL 양식 데이터 모델(FDM)]은 [Sling 컨텍스트 인식 구성](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/context-aware-configs.html)을 사용하여 다양한 [!DNL Experience Manager] 실행 모드에 대한 데이터 소스와 연결할 수 있도록 다양한 데이터 소스 매개 변수를 지원합니다.

[!UICONTROL 양식 데이터 모델(FDM)]이 클라우드 구성을 사용하여 매개 변수를 저장하는 경우, 체크 인하고 소스 제어(Cloud-Manager GIT 저장소)를 통해 배포하면 모든 실행 모드(개발, 스테이지 및 프로덕션)에 대해 동일한 매개 변수를 사용하여 클라우드 구성이 만들어집니다. 그러나 테스트 및 프로덕션 환경에 대해 서로 다른 데이터 세트를 사용해야 하는 사용 사례의 경우, 서로 다른 [!DNL Experience Manager] 실행 모드에 대해 데이터 소스 매개 변수(예: 데이터 소스 URL)를 사용합니다.

이를 위해서는 데이터 소스 매개변수-값 쌍을 포함하는 OSGi 구성을 생성해야 합니다. 런타임에 [!UICONTROL FDM(양식 데이터 모델)] 클라우드 구성에서 동일한 쌍을 재정의합니다. OSGi 구성은 기본적으로 이러한 실행 모드를 지원하기 때문에 실행 모드에 따라 데이터 소스 매개변수를 다른 값으로 재정의할 수 있습니다.

[!UICONTROL 양식 데이터 모델(FDM)]에서 배포별 클라우드 구성을 활성화하려면 다음을 수행하십시오.

1. 로컬 개발 인스턴스에 클라우드 구성을 만듭니다. 자세한 단계는 [데이터 원본을 구성하는 방법](/help/forms/configure-data-sources.md)을 참조하세요.

1. 클라우드 구성을 파일 시스템에 저장합니다.
   1. 필터 `/conf/{foldername}/settings/cloudconfigs/fdm`을(를) 사용하여 패키지를 만듭니다. 1단계와 동일한 `{foldername}`을(를) 사용합니다. Azure 저장소 구성을 위해 `fdm`을(를) `azurestorage`(으)로 바꾸십시오.
   1. 패키지 빌드 및 다운로드. 자세한 내용은 [패키지 작업](/help/implementing/developing/tools/package-manager.md)을 참조하세요.

1. [!DNL Experience Manager] Archetype 프로젝트에 클라우드 구성을 통합합니다.
   1. 다운로드한 패키지의 압축을 풉니다.
   1. `jcr_root` 폴더를 복사하여 `ui.content` > `src` > `main` > `content`에 넣습니다.
   1. 필터 `/conf/{foldername}/settings/cloudconfigs/fdm`을(를) 포함하도록 `ui.content` > `src` > `main` > `content` > `META-INF` > `vault` > `filter.xml`을(를) 업데이트합니다. 자세한 내용은 AEM Project Archetype의 [ui.content 모듈](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uicontent.html)을 참조하십시오. 이 Archetype 프로젝트가 CM 파이프라인을 통해 배포되면 모든 환경(또는 실행 모드)에 동일한 클라우드 구성이 설치됩니다. 환경을 기반으로 클라우드 구성의 필드(예: URL) 값을 변경하려면 다음 단계에서 설명한 OSGi 구성을 사용하십시오.

1. Apache Sling 컨텍스트 인식 구성을 만듭니다. OSGi 구성을 생성하려면 다음을 수행합니다.
   1. **[!DNL Experience Manager] Archetype 프로젝트에서 OSGi 구성 파일을 설정합니다.**
PID `org.apache.sling.caconfig.impl.override.OsgiConfigurationOverrideProvider`을(를) 사용하여 OSGi 팩토리 구성 파일을 만듭니다. 실행 모드별로 값을 변경해야 하는 각 실행 모드 폴더에 이름이 동일한 파일을 만듭니다. 자세한 내용은 [OSGi 구성 [!DNL Adobe Experience Manager]](/help/implementing/deploying/configuring-osgi.md#creating-sogi-configurations)을 참조하십시오.

   1. **OSGI 구성 json을 설정합니다.Apache Sling 컨텍스트 인식 구성 재정의 공급자를 사용하려면**:
      1. 로컬 개발 인스턴스 `/system/console/configMgr`에서 이름이 **[!UICONTROL Apache Sling 컨텍스트 인식 구성 재정의 공급자: OSGi 구성]**&#x200B;인 팩터리 OSGi 구성을 선택하십시오.
      1. 설명을 입력합니다.
      1. **[!UICONTROL 사용]**&#x200B;을 선택하세요.
      1. 재정의에서 sling 재정의 구문에서 환경에 따라 변경해야 하는 필드를 제공합니다. 자세한 내용은 [Apache Sling 컨텍스트 인식 구성 - 재정의](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration-override.html#override-syntax)을 참조하십시오. 예: `cloudconfigs/fdm/{configName}/url="newURL"`.
**[!UICONTROL +]**&#x200B;을(를) 선택하여 여러 개의 재정의를 추가할 수 있습니다.
      1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.
      1. OSGi 구성 JSON을 가져오려면 [AEM SDK 빠른 시작을 사용하여 OSGi 구성 생성](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)의 단계를 따릅니다.
      1. 이전 단계에서 생성한 OSGi 팩토리 구성 파일에 JSON을 배치합니다.
      1. 환경(또는 실행 모드)을 기준으로 `newURL`의 값을 변경합니다.
      1. 실행 모드에 따라 비밀 값을 변경하려면 [Cloud Manager API](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties)를 사용하여 비밀 변수를 만들 수 있습니다. 이상 버전은 [OSGi 구성](/help/implementing/deploying/configuring-osgi.md#secret-configuration-values)에서 참조할 수 있습니다.
이 Archetype 프로젝트가 CM 파이프라인을 통해 배포되면 재정의는 다른 환경(또는 실행 모드)에서 다른 값을 제공합니다.
      >[!NOTE]
      >
      >[!DNL Adobe Managed Service] 사용자는 암호화 지원을 사용하여 비밀 값을 암호화할 수 있습니다(자세한 내용은 [구성 속성에 대한 암호화 지원](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/encryption-support-for-configuration-properties.html#enabling-encryption-support)을 참조하고 [서비스 팩 6.5.13.0](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html#runmode-specific-context-aware-config)에서 컨텍스트 인식 구성을 사용할 수 있게 되면 다음 값에 암호화된 텍스트를 배치할 수 있습니다.

1. [양식 데이터 모델 편집기](#data-sources)에서 데이터 소스 정의를 새로 고치는 옵션을 사용하여 데이터 소스 정의를 새로 고쳐 FDM UI를 통해 FDM 캐시를 새로 고치고 최신 구성을 가져옵니다.

## 다음 단계 {#next-steps}

이제 데이터 소스가 추가된 양식 데이터 모델(FDM)이 있습니다. 그런 다음 FDM(양식 데이터 모델)을 편집하여 데이터 모델 개체 및 서비스를 추가 및 구성하고, 데이터 모델 개체 간의 연결을 추가하고, 속성을 편집하고, 사용자 정의 데이터 모델 개체 및 속성을 추가하고, 샘플 데이터를 생성하는 등의 작업을 수행할 수 있습니다.

자세한 내용은 [양식 데이터 모델 작업](work-with-form-data-model.md)을 참조하세요.


>[!MORELIKETHIS]
>
>* [양식 데이터 모델(FDM) 사용](/help/forms/using-form-data-model.md)