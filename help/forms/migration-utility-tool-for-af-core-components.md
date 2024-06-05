---
title: 마이그레이션 유틸리티 도구/AEM 현대화 도구 를 사용하여 기초 구성 요소 기반의 적응형 Forms을 핵심 구성 요소 기반 양식으로 변환
description: 마이그레이션 유틸리티/AEM 현대화 도구를 설치 및 사용하여 적응형 Forms 기반 구성 요소를 핵심 구성 요소 기반 양식으로 변환하는 방법에 대해 알아봅니다.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
source-git-commit: cc1f3e2f0ddaed67de541c730c0b97f68c1e0d02
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 1%

---


# 소개

Forms 전환 유틸리티, 일부 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-Tools/) 제품군에서는 레거시 Foundation 구성 요소로 구축된 적응형 Forms을 핵심 구성 요소의 현대적이고 지원되는 기능을 활용하는 양식으로 쉽게 변환할 수 있습니다.

## AEM 현대화 도구란 무엇입니까?

[AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-Tools/) 는 AEM(Adobe Experience Manager) 프로젝트를 현대화하거나 업데이트하는 프로세스를 용이하게 하기 위해 고안된 유틸리티 또는 소프트웨어 애플리케이션 세트를 나타냅니다. 이러한 도구는 일반적으로 AEM 내의 이전 구성 요소 또는 기능을 보다 효율적이고 지원되는 최신 대체 요소로 전환하는 데 도움이 됩니다. Forms 전환 유틸리티는 AEM 현대화 도구 아래에 설치되어 적응형 Forms 기반 기초 구성 요소를 핵심 구성 요소 기반 양식으로 변환합니다.

Forms 전환 유틸리티는 이전 기초 구성 요소를 기반으로 하는 적응형 Forms을 최신 핵심 구성 요소 기반 양식으로 전환합니다. 이러한 변환 프로세스를 통해 양식이 최신 표준 및 기능에 맞게 조정되므로 AEM 환경 내에서 성능, 호환성 및 유지 관리의 용이성이 잠재적으로 향상될 수 있습니다.

![AEM 현대화 도구](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> 로컬 AEM 설정에 AEM 현대화 도구 를 설치하는 것이 좋습니다. 적응형 Forms 기반 기초 구성 요소를 핵심 구성 요소 기반 양식으로 마이그레이션합니다. 에셋과 함께 양식을 다운로드합니다. 그런 다음 양식과 해당 에셋을 필요한 환경에 업로드합니다.

## AEM 현대화 도구 사용 시 고려 사항 {#considerations}

* 성공적으로 전환되면 양식에 적용된 모든 규칙이 제거됩니다. 규칙은 자동으로 마이그레이션되지 않습니다. 이러한 규칙을 수동으로 다시 만들어 변환된 양식에 적용해야 합니다.
* 원본 양식에 사용된 번역 설정은 이전되지 않습니다. 변환된 양식의 번역을 다시 구성합니다.
  <!-- * If the form built on Foundation Components contains custom function rules, you have to rewrite these rules for the converted form based on Core Components.-->

## AEM 현대화 도구 사용을 위한 전제 조건

* [AEM Forms을 위한 로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md)
* [환경에 대한 적응형 Forms 핵심 구성 요소 를 활성화합니다.](/help/forms/enable-adaptive-forms-core-components.md)

* 에 사용자 추가 [!DNL forms-users] 그룹입니다. 의 멤버 [!DNL forms-users] 그룹은 적응형 양식을 만들 수 있는 권한이 있습니다.

* 다음 역할이 있는 사용자는 AEM 환경 내에 AEM 현대화 도구 를 설치할 수 있는 권한이 있습니다.
   * 개발자 역할
   * 책임자 역할

양식별 사용자 그룹의 자세한 목록은 다음을 참조하십시오. [그룹 및 권한](forms-groups-privileges-tasks.md).

## AEM 현대화 도구 설치 및 구성

AEM 현대화 도구 설치 및 구성 방법:

1. [로컬 AEM Forms 환경에 AEM 현대화 도구 설치](#install-aem-modernize-Tools)
2. [로컬 AEM Forms 환경을 위해 AEM 현대화 도구 활성화](#enable-aem-modernize-Tools)

### 로컬 AEM Forms 환경에 AEM 현대화 도구 설치 {#install-aem-modernize-Tools}

로컬 AEM Forms 환경에 AEM 현대화 도구 를 설치하려면 다음 단계를 수행하십시오.

1. 명령 프롬프트 또는 터미널을 엽니다.
1. 로컬 AEM 작성자 서비스를 시작합니다. 예를 들어에서 다음 코드를 실행하여 로컬 AEM 작성자 인스턴스를 시작합니다.

   `java -jar aem-author-p4502.jar`

1. 복제 [AEM 현대화 도구](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) 로컬 시스템의 저장소입니다.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   명령을 성공적으로 실행하면 컴퓨터에서 AEM 현대화 도구 저장소의 로컬 복사본을 사용할 수 있습니다.

1. 다음 위치로 이동`[AEM Modernize Tool Repository]`  로컬 시스템에서 사용할 수 있습니다.
1. 다음 명령을 실행합니다.

   ```Shell
       mvn clean install 
   ```
![설치 이미지 성공](/help/forms/assets/aem-modernize-install-steps.png)

성공적으로 설치하면 AEM 현대화 도구 를 해당 환경에서 사용할 수 있게 됩니다.

![AEM 마이그레이션 유틸리티 도구 활성화](/help/forms/assets/enable-aem-modernizer-tools.png)


### 로컬 AEM Forms 환경을 위해 AEM 현대화 도구 활성화{#enable-aem-modernize-Tools}

AEM 환경을 위해 AEM 현대화 도구 를 활성화하고 사용하려면 Foundation 구성 요소를 핵심 구성 요소로 마이그레이션하기 위한 규칙을 매핑해야 합니다.

1. 작성자 인스턴스에 로그인합니다.
1. 다음으로 이동 `http://[host]:[port]/system/console/configMgr`
1. 찾기 및 편집 `AEM Modernize Tools - Component Rewrite Rule Service`.
1. 추가 `Component Rule Paths` 다음으로: `/apps/forms-modernizer/rules`.
1. 클릭 **저장** 변경 내용을 저장합니다.

![AEM 현대화 구성 요소 규칙](/help/forms/assets/aem-modernize-tools-component-rule.png)

## 양식 변환 유틸리티를 실행하여 기초 구성 요소 기반 양식을 핵심 구성 요소 기반 양식으로 변환

1. 다음으로 이동 **[!UICONTROL 도구 > AEM 현대화 도구 > Forms 변환]**.

   ![AEM 현대화 도구 선택](/help/forms/assets/aem-modernize-tools-select-form.png)

1. 다음 항목 선택 **[!UICONTROL Forms 전환]** 옵션을 선택합니다.

   ![Forms 전환 옵션 선택](/help/forms/assets/aem-modernize-forms-conversion.png)

1. 클릭 **만들기** 새 작업을 만듭니다.

   ![AEM 현대화 도구 작업 만들기](/help/forms/assets/aem-modernize-tools-create-job.png)

1. 다음을 지정합니다. **[!UICONTROL 작업 이름]**.
1. 다음에서 **[!UICONTROL 양식]** 탭에서 다음 옵션 중 하나를 선택할 수 있습니다.
   * **없음** : 양식 전환을 시작하기 전에 기초 구성 요소 기반 양식의 사본을 만들지 않으려면 옵션을 선택합니다.
   * **복원** : 양식 전환을 시작하기 전의 상태로 양식을 복원하려면 옵션을 선택합니다.
   * **Target에 복사**: 양식 전환을 시작하기 전에 기초 구성 요소 기반 양식의 사본을 만들려면 옵션을 선택합니다.
이 예제에서는 **Target에 복사** 옵션이 선택되어 있습니다. 다음과 같은 경우 **Target에 복사** 옵션을 선택한 경우 **[!UICONTROL 소스 경로]** 및 **[!UICONTROL 대상 경로]** 옵션이 표시됩니다.

1. 다음을 지정합니다. `source folder` 의 이름 **[!UICONTROL 소스 경로]**.
1. 다음을 지정합니다. `target folder` 의 이름 **[!UICONTROL 대상 경로]**.
1. **[!UICONTROL 다음]**&#x200B;을 선택합니다.
1. 클릭 **[!UICONTROL Forms 추가]**. 의 모든 양식 `source folder` 화면에 표시됩니다.
1. 적응형 Forms 기반 기초 구성 요소 를 선택하여 핵심 구성 요소 기반 양식으로 전환합니다. 여러 양식을 선택할 수도 있습니다.

   ![AEM 현대화 도구 선택 양식](/help/forms/assets/aem-modernize-tools-select-form.png)

1. 클릭 **[!UICONTROL 선택]**.
1. 클릭 **[!UICONTROL 작업 예약]** 변환 프로세스를 시작합니다.
1. 클릭 **[!UICONTROL 전환]** 다음에서 **[!UICONTROL 페이지 변환]** 대화 상자.

   ![AEM 현대화 도구 페이지 변환](/help/forms/assets/aem-modernize-tools-convert-form.png)

   프로세스 상태가 (으)로 변경된 경우 `success`. 다음 위치로 이동 `target folder` 변환 양식을 봅니다.

   ![AEM 현대화 도구 성공](/help/forms/assets/aem-modernize-tools-success.png)

1. 적응형 양식을 선택하고 > **[!UICONTROL 속성]**. 양식 속성 페이지가 열립니다.
   ![AEM 현대화 도구 대상 폴더](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. 선택 **[!UICONTROL 저장 및 닫기]** 변환 양식의 속성을 다시 저장합니다.
   ![AEM 현대화 도구 적응형 양식 속성](/help/forms/assets/aem-modernize-tools-af-properties.png)

이제 기초 구성 요소에 구축된 적응형 양식이 핵심 구성 요소에 구축된 적응형 양식으로 변환됨을 알 수 있습니다.

## 모범 사례 {#best-practices}

* 기초 구성 요소 기반 양식인지 확인하고, 동일한 구성 요소가 있는 구성 요소만 사용하십시오. [핵심 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) 사용 가능. 동일한 핵심 구성 요소가 없는 기초 구성 요소를 사용하는 경우 기초 구성 요소는 변환되지 않습니다. 따라서 양식을 작성하는 동안에는 제대로 작동하지 않습니다
* 기초 구성 요소를 핵심 구성 요소로 변환하는 규칙의 형식이 XML로 지정되어 있는지 확인합니다.



