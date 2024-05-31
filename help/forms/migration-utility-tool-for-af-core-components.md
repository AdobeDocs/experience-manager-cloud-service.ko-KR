---
title: 기초 구성 요소 기반의 적응형 Forms을 핵심 구성 요소 기반 양식으로 전환하는 마이그레이션 유틸리티
description: 마이그레이션 유틸리티를 설치하고 사용하여 Foundation 구성 요소 기반의 적응형 Forms을 핵심 구성 요소 기반 양식으로 변환하는 방법에 대해 알아봅니다.
Keywords: Migration Utility tool, Convert Adaptive Forms based on foundation components to core component based forms, Convert Foundation forms to Core components forms, Using Modernizer tool to convert Foundation Components to Core components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 1%

---


# 소개

마이그레이션 유틸리티를 사용하여 기초 구성 요소 기반의 적응형 Forms을 핵심 구성 요소 기반 양식으로 변환할 수 있습니다. 다음을 사용할 수 있습니다. [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/) 마이그레이션 유틸리티 도구로 사용하십시오. 다음 [AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/) 기초 구성 요소 기반의 적응형 Forms을 핵심 구성 요소의 현대적이고 지원되는 기능으로 변환하는 데 사용되는 유틸리티 제품군을 제공합니다.

## AEM 현대화 도구란 무엇입니까?

[AEM 현대화 도구](https://opensource.adobe.com/aem-modernize-tools/) 는 AEM(Adobe Experience Manager) 프로젝트를 현대화하거나 업데이트하는 프로세스를 용이하게 하기 위해 고안된 유틸리티 또는 소프트웨어 애플리케이션 세트를 나타냅니다. 이러한 도구는 일반적으로 AEM 내의 이전 구성 요소 또는 기능을 새롭고 보다 효율적이며 지원되는 대안으로 전환하는 데 도움이 됩니다.

AEM 현대화 도구는 이전 기초 구성 요소를 기반으로 하는 적응형 Forms을 최신 핵심 구성 요소 기반 양식으로 변환합니다. 이러한 변환 프로세스를 통해 양식이 최신 표준 및 기능에 맞게 조정되므로 AEM 환경 내에서 성능, 호환성 및 유지 관리의 용이성이 잠재적으로 향상될 수 있습니다.

![AEM 현대화 도구](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> 로컬 AEM 설정에 AEM 현대화 도구 를 설치하는 것이 좋습니다. 기초 기반 양식을 핵심 구성 요소 기반 양식으로 마이그레이션합니다. 에셋과 함께 양식을 다운로드합니다. 그런 다음 양식과 해당 에셋을 필요한 환경에 업로드합니다.

## AEM 현대화 도구 사용을 위한 전제 조건

* [AEM Forms을 위한 로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md)
* [환경에 맞는 적응형 Forms 핵심 구성 요소를 활성화합니다.](/help/forms/enable-adaptive-forms-core-components.md)

* 에 사용자 추가 [!DNL forms-users] 그룹입니다. 의 멤버 [!DNL forms-users] 그룹은 적응형 양식을 만들 수 있는 권한이 있습니다.

* 다음 역할이 있는 사용자는 AEM 환경 내에 AEM 현대화 도구 를 설치할 수 있는 권한이 있습니다.
   * 개발자 역할
   * 관리자 역할 양식별 사용자 그룹의 자세한 목록은 다음을 참조하십시오. [그룹 및 권한](forms-groups-privileges-tasks.md).

## AEM 현대화 도구 설치 및 구성

AEM 현대화 도구 설치 및 구성 단계:

1. [로컬 AEM Forms 환경에 AEM 현대화 도구 설치](#install-aem-modernize-tools)
2. [로컬 AEM Forms 환경을 위해 AEM 현대화 도구 활성화](#enable-aem-modernize-tools)

### 로컬 AEM Forms 환경에 AEM 현대화 도구 설치 {#install-aem-modernize-tools}

로컬 AEM Forms 환경에 AEM 현대화 도구 를 설치하려면 다음 단계를 수행하십시오.

1. 명령줄에서 다음을 실행하여 로컬 AEM 작성자 서비스를 시작합니다.

   `java -jar aem-author-p4502.jar`

   >[!NOTE]
   >
   > 관리자 암호 입력 `admin`. 모든 관리자 암호는 사용할 수 있지만, 로컬 개발에 기본값을 사용하여 재구성할 필요가 없도록 하는 것이 좋습니다.

1. 복제 [AEM 현대화 도구](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) 로컬 시스템의 저장소입니다.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tools]
   ```
   바꾸기 [AEM 현대화 도구의 Git 저장소 경로] (AEM 현대화 도구) 의 해당 Git 저장소의 실제 URL 포함
명령을 성공적으로 실행하면 컴퓨터에서 AEM 현대화 도구 저장소의 로컬 복사본을 사용할 수 있습니다.

1. 다음 위치로 이동`[AEM Modernize Tools Repository]`  로컬 시스템에서 사용할 수 있습니다.
1. 다음 명령을 실행합니다.

   ```Shell
       mvn clean install 
   ```
![설치 이미지 성공](/help/forms/assets/aem-modernize-install-steps.png)

설치가 완료되면 AEM 현대화 도구 를 해당 환경에서 사용할 수 있습니다.

![AEM 현대화 도구 활성화](/help/forms/assets/enable-aem-modernizer-tools.png)


### 로컬 AEM Forms 환경을 위해 AEM 현대화 도구 활성화{#enable-aem-modernize-tools}

AEM 환경에 AEM 현대화 도구 를 활성화하고 사용하려면 기초 구성 요소를 핵심 구성 요소로 마이그레이션하는 규칙을 매핑하는 것이 중요합니다.

1. 작성자 인스턴스에 로그인합니다.
1. 다음으로 이동 `http://[host]:[port]/system/console/configMgr`
1. 찾기 및 편집 `AEM Modernize Tools - Component Rewrite Rule Service`.
1. 추가 `Component Rule Paths` 다음으로: `/apps/forms-modernizer/rules`.
1. 클릭 **저장** 변경 내용을 저장합니다.

![AEM 현대화 구성 요소 규칙](/help/forms/assets/aem-modernize-tools-component-rule.png)

## AEM 현대화 도구 를 실행하여 기초 구성 요소 기반 양식을 핵심 구성 요소 기반 양식으로 변환

1. 다음으로 이동 **[!UICONTROL 도구 > AEM 현대화 도구 > Forms 변환]**.

   ![AEM 현대화 도구 선택](/help/forms/assets/aem-modernize-tools-select.png)

1. 다음 항목 선택 **[!UICONTROL Forms 전환]** 옵션을 선택합니다.

   ![Forms 전환 옵션 선택](/help/forms/assets/aem-modernize-forms-conversion.png)

1. 클릭 **만들기** 새 작업을 만듭니다.

   ![AEM 현대화 도구 작업 만들기](/help/forms/assets/aem-modernize-tools-create-job.png)

1. 다음을 지정합니다. **[!UICONTROL 작업 이름]**.
1. 다음에서 **[!UICONTROL 양식]** 탭에서 다음 옵션 중 하나를 선택할 수 있습니다.
   * **없음** : 양식 처리가 필요하지 않은 경우 이 옵션을 선택합니다.
   * **복원** : 이 옵션을 선택하여 양식을 마지막 변환 전 상태로 복원합니다.
   * **Target에 복사**: 전환을 수행하기 전에 양식을 복사하려면 이 옵션을 선택합니다.
이 예제에서는 **Target에 복사** 옵션이 선택되어 있습니다. 다음과 같은 경우 **Target에 복사** 옵션을 선택한 경우 **[!UICONTROL 소스 경로]** 및 **[!UICONTROL 대상 경로]** 옵션이 표시됩니다.

1. 다음을 지정합니다. `source folder` 의 이름 **[!UICONTROL 소스 경로]**.
1. 다음을 지정합니다. `target folder` 의 이름 **[!UICONTROL 대상 경로]**.
1. **[!UICONTROL 다음]**&#x200B;을 선택합니다.
1. 클릭 **[!UICONTROL Forms 추가]**. 의 모든 양식 `source folder` 화면에 표시됩니다.
1. 기초 구성 요소를 기반으로 하는 양식을 선택하여 핵심 구성 요소를 기반으로 하는 양식으로 변환합니다. 여러 양식을 선택할 수도 있습니다.

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

## 마이그레이션 유틸리티 도구를 사용하는 동안 고려 사항 {#considerations}

* 기초 구성 요소에 빌드된 양식에 사용자 정의 함수 규칙이 포함되어 있는 경우 핵심 구성 요소를 기반으로 변환된 양식에 대해 이러한 규칙을 다시 작성해야 합니다.
* 변환된 양식에는 규칙 편집기에 규칙이 포함되어 있지 않으므로 변환된 양식에 대한 규칙을 다시 작성해야 합니다.
* 변환된 양식에 대한 번역 작업을 다시 만들어야 합니다.

## 모범 사례 {#best-practices}

* 기초 구성 요소를 기반으로 빌드된 양식에는 핵심 구성 요소 기반 구성 요소에 있는 구성 요소만 포함됩니다.
* 규칙의 형식이 XML로 지정되어 있는지 확인합니다.


