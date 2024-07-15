---
title: 적응형 양식에서 Adobe Sign을 사용하려면 어떻게 해야 합니까?
description: 적응형 양식의 Adobe Sign을 사용하여 양식 수신자가 선택한 장치 및 위치에서 양식에 전자 서명할 수 있습니다.
topic-tags: develop
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: cde9523e-5409-4edd-af0f-2c2575cc22ea
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '3243'
ht-degree: 2%

---

# 적응형 양식에서 [!DNL Adobe Sign] 사용 {#using-adobe-sign-in-an-adaptive-form}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) |
| AEM as a Cloud Service | 이 문서 |


[!DNL Adobe Sign]은 적응형 양식용 전자 서명 워크플로를 가능하게 합니다. 전자 서명은 법무, 판매, 급여, 인사 관리 등의 분야에서 문서를 처리하는 워크플로를 개선합니다.

일반적인 [!DNL Adobe Sign] 및 적응형 Forms 시나리오에서 사용자는 적응형 양식에 정보를 입력하여 한 명 이상의 당사자의 서명이 필요한 서비스를 신청합니다. 예를 들어, 모기지 및 신용 카드 신청에는 모든 차입자 및 공동 신청자의 법적 서명이 필요합니다. 유사한 시나리오에 전자 서명 워크플로를 사용하려면 [!DNL Adobe Sign]을(를) 적응형 양식과 통합할 수 있습니다. 몇 가지 예가 더 있습니다. [!DNL Adobe Sign]을(를) 사용하여 다음을 수행할 수 있습니다.

* 제안, 견적 및 계약 프로세스가 완전히 자동화된 모든 장치에서 거래를 성사시킵니다.
* 인적 자원 프로세스를 보다 빠르게 완료하고 직원에게 디지털 환경을 제공하십시오.
* 계약 주기 시간을 단축하고 공급업체를 더 빨리 온보딩하십시오.
* 일반적인 프로세스를 자동화하는 디지털 워크플로를 만듭니다.

[!DNL AEM Forms]과(와)의 [!DNL Adobe Sign] 통합은 다음을 지원합니다.

* 단일 및 다중 사용자 서명 워크플로
* 순차 및 동시 서명 워크플로
* 양식을 익명 또는 로그인한 사용자로 서명
* 동적 서명 프로세스([!DNL AEM Forms] 워크플로우와 통합)
* 기술 자료, 전화, 소셜 프로필 및 정부 ID를 통한 인증
* 각 계약 수신자에게 역할을 할당합니다. 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign에는 계약 수신자의 [역할](#addsignerstoanadaptiveform)을 확장하는 옵션이 있습니다.

<!-- * In-form and out-of-form signing experiences -->

## 사전 요구 사항 {#prerequisites}

적응형 양식에서 [!DNL Adobe Sign]을(를) 사용하기 전에:

* as a Cloud Service [!DNL AEM Forms]이(가) Adobe Sign을 사용하도록 구성되어 있는지 확인합니다. 자세한 내용은 [Adobe Sign과 통합 [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md)을 참조하세요.
* 수신자 목록을 준비하십시오. 모든 수신자에 대해 최소 하나의 이메일 주소가 필요합니다.

## 적응형 양식에 대해 [!DNL Adobe Sign] 구성 {#configure-adobe-sign-for-an-adaptive-form}

적응형 양식에 대해 [!DNL Adobe Sign]을(를) 구성하려면:

1. [적응형 양식에 대해  [!DNL Adobe Sign] 사용](#enableadobsignforanadaptiveform)
1. [적응형 양식에  [!DNL Adobe Sign] 필드 추가](#addadobesignfieldstoanadaptiveform)
1. [적응형 양식에 대해  [!DNL Adobe Sign] Cloud Service 선택](#select-adobe-sign-cloud-service-and-signing-order)

1. [적응형 양식에  [!DNL Adobe Sign] 받는 사람 추가](#addsignerstoanadaptiveform)
1. [적응형 양식에 대한 제출 액션 선택](#selectsubmitactionforanadaptiveform)

![받는 사람 세부 정보](assets/signer_details_new.png)

### 적응형 양식에 [!DNL Adobe Sign] 사용  {#enableadobesign}

기존 적응형 양식에 대해 [!DNL Adobe Sign]을(를) 활성화하거나 [!DNL Adobe Sign]이(가) 활성화된 적응형 양식을 만들 수 있습니다. 다음 중 하나를 선택합니다.

* [ [!DNL Adobe Sign] 활성화된 적응형 양식 만들기](#create-an-adaptive-form-for-adobe-sign)
* 기존 적응형 양식에 대해 [사용 [!DNL Adobe Sign] 합니다](#editafsign).

#### Adobe Sign용 적응형 양식 만들기 {#create-an-adaptive-form-for-adobe-sign}

Sign이 활성화된 적응형 양식을 만들려면 다음 작업을 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택하고 **[!UICONTROL 적응형 양식]**&#x200B;을 선택하세요. 템플릿 목록이 나타납니다. 템플릿을 선택하고 **[!UICONTROL 다음]**&#x200B;을(를) 선택하십시오.
1. **[!UICONTROL 기본]** 탭에서:

   1. 적응형 양식에 대해 **[!UICONTROL 이름]** 및 **[!UICONTROL 제목]**&#x200B;을 지정하십시오.

   1. [통합 [!DNL Adobe Sign] 을(를)  [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md)하는 동안 만든 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms)를 선택하십시오.

   구성 컨테이너에는 환경에 대해 구성된 [!DNL Adobe Sign] Cloud Service이 포함되어 있습니다. 이러한 서비스는 적응형 양식 편집기에서 선택할 수 있습니다.

1. **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   * 사용자 지정 양식 서식 파일이 있고 양식 서식 파일을 기반으로 기록 문서가 필요한 경우 **[!UICONTROL 양식 서식 파일을 기록 문서 서식 파일로 연결]** 옵션을 선택하고 기록 문서 서식 파일을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 관련 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적응형 양식의 모든 필드가 표시되지는 않습니다.

   * 사용자 지정 양식 서식 파일이 없는 경우 **[!UICONTROL 기록 문서 생성]** 옵션을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. **[!UICONTROL 만들기를 선택합니다.]** 기호가 활성화된 적응형 양식이 만들어집니다. [!DNL Adobe Sign] 필드를 양식에 추가하고 서명을 위해 보낼 수 있습니다.

#### 적응형 양식에 [!DNL Adobe Sign] 사용 {#editafsign}

기존 적응형 양식에서 [!DNL Adobe Sign]을(를) 사용하려면:

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. 적응형 양식을 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 기본]** 탭에서 [!DNL Adobe Sign]을(를) [!DNL AEM Forms]과(와) 통합하는 동안 만든 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms)을(를) 선택합니다.
1. **[!UICONTROL 양식 모드]** 탭에서 다음 옵션 중 하나를 선택합니다.

   * 사용자 지정 양식 서식 파일이 있고 양식 서식 파일을 기반으로 기록 문서가 필요한 경우 **[!UICONTROL 양식 서식 파일을 기록 문서 서식 파일로 연결]** 옵션을 선택하고 기록 문서 서식 파일을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 관련 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적응형 양식의 모든 필드가 표시되지는 않습니다.

   * 사용자 지정 양식 서식 파일이 없는 경우 **[!UICONTROL 기록 문서 생성]** 옵션을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다. [!DNL Adobe Sign]에 대해 적응형 양식을 사용할 수 있습니다. 이제 양식에 [!DNL Adobe Sign] 필드를 추가하고 서명을 위해 전송할 수 있습니다.

### 적응형 양식에 [!DNL Adobe Sign] 필드 추가 {#addadobesignfieldstoanadaptiveform}

[!DNL Adobe Sign]에는 적응형 양식에 배치할 수 있는 다양한 필드가 있습니다. 이러한 필드에는 서명, 이니셜, 회사 또는 제목과 같은 다양한 유형의 데이터가 허용되며 서명과 함께 서명 중에 추가 정보를 수집하는 데 도움이 됩니다. [!DNL Adobe Sign] 블록 구성 요소를 사용하여 적응형 양식의 다양한 위치에 [!DNL Adobe Sign] 필드를 배치할 수 있습니다.

적응형 양식에 필드를 추가하고 이러한 필드와 관련된 다양한 옵션을 사용자 지정하려면 다음을 수행하십시오.

1. 구성 요소 브라우저에서 **[!UICONTROL Adobe Sign 블록]** 구성 요소를 적응형 양식으로 드래그 앤 드롭하십시오. [!DNL Adobe Sign] 블록 구성 요소에 지원되는 모든 [!DNL Adobe Sign] 필드가 있습니다. 기본적으로 적응형 양식에 **[!UICONTROL 서명]** 필드를 추가합니다.

   ![블록 서명](assets/sign_block_new.png)

   기본적으로 [!DNL Adobe Sign] 블록은 게시된 적응형 양식에 표시되지 않습니다. 서명 문서에만 표시됩니다. [!DNL Adobe Sign] 블록 구성 요소의 속성에서 [!DNL Adobe Sign] 블록의 가시성을 변경할 수 있습니다.

   >[!NOTE]
   >
   >  * 적응형 양식에서 [!DNL Adobe Sign]을(를) 사용하려면 [!DNL Adobe Sign] 블록을 사용해야 하는 것은 아닙니다. [!DNL Adobe Sign] 블록을 사용하지 않고 받는 사람의 필드를 추가하는 경우 서명 문서 하단에 기본 서명 필드가 표시됩니다.
   >  * 기록 문서를 자동으로 생성하는 적응형 Forms에 대해서만 [!DNL Adobe Sign] 블록을 사용하십시오. 기록 문서 또는 적응형 양식 기반의 양식 템플릿을 생성하는 데 사용자 지정 XDP를 사용하는 경우 [!DNL Adobe Sign] 블록이 지원되지 않습니다.


1. **[!UICONTROL Adobe Sign 블록]** 구성 요소를 선택하고 **[!UICONTROL 편집]** ![편집](assets/Smock_Edit_18_N.svg) 아이콘을 선택합니다. 필드를 추가하고 필드의 형식 지정을 지정하는 옵션을 표시합니다.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** [!DNL Adobe Sign] 필드를 선택하고 추가하십시오. **B.** [!DNL Adobe Sign] 블록을 전체 화면 보기로 확장합니다.

1. **[!UICONTROL Adobe Sign]** 필드 ![Adobe Sign](assets/adobesign.png) 아이콘을 선택합니다. [!DNL Adobe Sign] 필드를 선택하고 추가하는 옵션이 표시됩니다.

   **[!UICONTROL Type]** 드롭다운 필드를 확장하여 [!DNL Adobe Sign] 필드를 선택하고 ![저장](assets/save_icon.svg) 완료 아이콘을 선택하여 [!DNL Adobe Sign] 블록에 선택한 필드를 추가합니다. **[!UICONTROL Type]** 드롭다운 필드에는 서명, 받는 사람 정보 및 데이터 필드 형식이 포함됩니다. [!UICONTROL Type] 드롭다운 상자에만 나열된 AEM [!DNL Forms] 지원 필드와 [!DNL Adobe Sign] 통합 [!DNL Adobe Sign] 필드에 대한 자세한 내용은 [Adobe Sign 설명서](https://helpx.adobe.com/sign/help/field-types.html)를 참조하세요.

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   필드에 고유한 이름을 입력해야 합니다. 필수 옵션을 선택하여 필드를 필수 항목으로 표시할 수도 있습니다. **[!UICONTROL 이름]** 및 **[!UICONTROL 필수]** 옵션 외에 일부 [!DNL Adobe Sign] 필드에 더 많은 옵션이 있습니다. 예: 마스크 및 여러 줄. 또한 필드가 같은 [!DNL Adobe Sign] 블록에 있는지 아니면 다른  블록에 있는지 여부에 관계없이 각 [!DNL Adobe Sign] 필드에 고유한 이름을 지정하십시오.

   드롭다운 목록에서 **[!UICONTROL 디지털 서명]**&#x200B;을(를) 선택하면 적응형 양식에 디지털 서명을 적용할 수 있습니다.

   * 클라우드 서명을 사용하여 트러스트 서비스 공급자가 호스팅하는 [디지털 ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html)(으)로 서명하는 온라인
   * 스마트 카드, USB 토큰 또는 파일 기반 디지털 ID를 사용하여 Adobe Acrobat 또는 Reader으로 문서를 로컬로 다운로드합니다.

### 적응형 양식에 [!DNL Adobe Sign] 사용 {#enableadobsignforanadaptiveform}

기본적으로 [!DNL Adobe Sign]은(는) 적응형 양식에 사용할 수 없습니다. 활성화하려면

1. 콘텐츠 브라우저에서 **[!UICONTROL 양식 컨테이너]**&#x200B;를 선택하고 **[!UICONTROL 구성]** ![구성](assets/Smock_Wrench_18_N.svg) 아이콘을 선택합니다. 속성 브라우저를 열고 적응형 양식 컨테이너 속성을 표시합니다.
1. 속성 브라우저에서 **[!UICONTROL 전자 서명]** 아코디언을 확장하고 **[!UICONTROL Adobe Sign 사용]** 옵션을 선택합니다. 적응형 양식에 [!DNL Adobe Sign]을(를) 사용합니다.

### [!DNL Adobe Sign] Cloud Service 및 서명 순서 선택 {#select-adobe-sign-cloud-service-and-signing-order}

AEM [!DNL Forms]의 인스턴스에 대해 여러 [!DNL Adobe Sign] 서비스를 구성할 수 있습니다. 각 기능(인적 자원, 금융 등)별로 별도의 서비스 세트를 두는 것이 바람직하다. 서명된 문서의 추적 및 보고를 더 쉽게 만듭니다. 예를 들어, A은행에는 여러 부서가 있습니다. 문서 추적을 향상시키기 위해 각 부서에 대해 별도의 구성을 가질 수 있습니다.

문서에 여러 수신자가 있을 수도 있습니다. 예를 들어 신용 카드 신청서에는 여러 명의 신청자가 있을 수 있습니다. 은행은 신청서 처리를 시작하기 전에 모든 신청자의 서명을 필요로 한다. 여러 수신자 시나리오의 경우 문서를 순차적 또는 동시 순서로 서명하도록 선택할 수 있습니다.

서명 Cloud Service 및 순서를 선택하려면 다음을 수행하십시오.

![클라우드 서비스](/help/forms/assets/adobe-sign-cloud-service.png)

1. 콘텐츠 브라우저에서 **[!UICONTROL 양식 컨테이너]**&#x200B;를 선택하고 **[!UICONTROL 구성]** ![구성](assets/Smock_Wrench_18_N.svg) 아이콘을 선택합니다. 속성 브라우저를 열고 적응형 양식 컨테이너 속성을 표시합니다.
1. 속성 브라우저에서 **[!UICONTROL 전자 서명]** 아코디언을 확장하고 **[!UICONTROL Adobe Sign 사용]** 옵션을 선택합니다. 적응형 양식에 [!DNL Adobe Sign]을(를) 사용합니다.
1. 이미 구성된 [!DNL Adobe Sign] Cloud Services 목록에서 Cloud Service을 선택하십시오.

   **[!UICONTROL Adobe Sign Cloud Service]** 목록이 비어 있으면 [구성 [!DNL Adobe Sign] 사용 [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md) 문서에 따라 서비스를 구성하십시오.

   드롭다운에는 도구 > **[!UICONTROL Cloud Service]** > **[!UICONTROL Adobe Sign]**&#x200B;의 `global` 폴더에 있는 Cloud Service이 나열됩니다. 또한 드롭다운 목록에는 적응형 양식을 만들 때 **[!UICONTROL 구성 Cloud Service]** 필드에서 선택한 폴더에 있는 컨테이너도 나열됩니다.

1. **[!UICONTROL 양식 제출]**&#x200B;을 사용하여 제출 액션을 구성하려면 옵션을 선택하십시오. 다음 중 한 가지 옵션을 선택할 수 있습니다.
   * **양식을 제출하고 서명용 계약서를 보냅니다.**: 이 옵션은 양식을 즉시 제출한 다음 서명용 양식을 받는 사람에게 보냅니다.
   * **양식 제출(모든 수신자가 서명식을 완료한 후)**: 이 옵션은 모든 서명자가 서명 프로세스를 완료한 후에만 적응형 Forms을 제출합니다. 모든 서명자에 대한 서명 상태를 확인하도록 간격을 구성할 수 있습니다. 자세한 내용은 [구성 [!DNL Adobe Acrobat Sign] 스케줄러](/help/forms/adobe-sign-integration-adaptive-forms.md#configure-dnl-adobe-acrobat-sign-scheduler-to-sync-the-signing-status)를 참조하십시오.

1. **[!UICONTROL 받는 사람이 완료할 수 있음]** 대화 상자에서 서명 순서를 선택하십시오. 수신자는 적응형 양식 **[!UICONTROL 순차적으로]**&#x200B;에 서명할 수 있습니다(한 명의 수신자가 차례로 또는 **[!UICONTROL 동시에]**).

   한 번에 한 명의 수신자가 Adobe Sign 계약을 순차적으로 받습니다. 수신자가 지정된 작업을 완료하면 계약이 다음 수신자에게 전송됩니다.

   동시 순서로 모든 수신자들이 Adobe Sign 협약을 받고 서로 병렬적으로 행동할 수 있다.

1. 계약 ID 필드를 사용하여 bindref를 계약 ID(agreementId)에 연결합니다. 스키마 기반 양식에 대한 제출 데이터의 afBoundData 섹션에 계약 ID를 추가합니다. 계약 ID는 모든 Adobe Sign 지원 양식에 대해 제출된 데이터의 afSubmissionInfo 섹션에도 추가됩니다. 사용자 지정 코드를 사용하여 계약 상태를 추적하는 데 계약 ID를 사용할 수 있습니다(사용자 지정 구현 필요).

   >[!NOTE]
   >
   > 적응형 양식이 양식 데이터 모델(FDM)을 사용하여 생성된 경우, 계약 ID 필드가 대화 상자에 표시됩니다.

1. [적응형 양식에 수신자를 추가](working-with-adobe-sign.md#addsignerstoanadaptiveform)하고 ![저장](assets/save_icon.svg) 완료 아이콘을 선택하여 변경 내용을 저장합니다.

### 적응형 양식에 수신자 추가 {#addsignerstoanadaptiveform}

Adobe Sign 계약에 대해 한 명 또는 여러 명의 수신자가 있을 수 있습니다. 수신자를 추가할 때 수신자에 대한 인증 세부 정보를 구성하고 양식 작성기와 수신자가 동일한 사람인지 선택할 수도 있습니다. 수신자에 대한 다양한 세부 정보를 추가하고 제공하려면 다음 단계를 수행하십시오.

1. 콘텐츠 브라우저에서 **[!UICONTROL 양식 컨테이너]**&#x200B;를 선택하고 **[!UICONTROL 구성]** ![구성](assets/Smock_Wrench_18_N.svg) 아이콘을 선택합니다. 적응형 양식 컨테이너 속성이 있는 속성 브라우저를 엽니다.
1. 속성 브라우저에서 **[!UICONTROL 전자 서명]** 아코디언을 확장하고 **[!UICONTROL Adobe Sign 사용]** 옵션을 선택합니다. 적응형 양식에 [!DNL Adobe Sign]을(를) 사용합니다.
1. **[!UICONTROL 받는 사람 추가]**를 선택합니다. 적응형 양식에 수신자를 추가합니다. 적응형 양식에 여러 수신자를 추가할 수 있습니다. 모든 수신자는 적응형 양식 제출에 대한 Adobe Sign 동의를 받습니다.
   ![전화 정보](assets/recipient-settings.png)

1. **[!UICONTROL 편집]** ![편집](assets/Smock_Edit_18_N.svg) 아이콘을 클릭하여 받는 사람에 대한 다음 정보를 지정하십시오.

   * **[!UICONTROL 제목]:** 수신자를 고유하게 식별할 제목을 지정합니다.

   * **[!UICONTROL 받는 사람과 양식 작성자가 같습니까?]:** 양식 작성기와 첫 번째 받는 사람이 같은 경우 **[!UICONTROL 예]**&#x200B;를 선택합니다. <!-- If the option is set to **No,** then do not use the signature step component in the Adaptive Form. If the form contains a Signature Step component, then the field is automatically set to Yes. -->

   * **[!UICONTROL 받는 사람 역할]:** 받는 사람의 역할을 선택합니다. 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign에는 워크플로 요구 사항에 보다 잘 부합하도록 계약 수신자의 [역할](https://helpx.adobe.com/sign/using/set-up-signer-approver-roles.html)을(를) **서명자** 이상으로 확장하는 옵션이 있습니다.

   * **[!UICONTROL 받는 사람 전자 메일 주소]:** 받는 사람의 전자 메일 주소를 지정합니다. 수신자는 지정된 이메일 주소에 대한 Adobe Sign 계약을 수신합니다. 양식 필드, 로그인한 사용자의 Experience Manager 사용자 프로필에 제공된 이메일 주소를 사용하도록 선택하거나 이메일 주소를 수동으로 입력할 수 있습니다. 필수 단계입니다.

     >[!NOTE]
     >
     >첫 번째 받는 사람 또는 유일한 받는 사람(받는 사람이 한 명인 경우)의 전자 메일 주소가 AEM Cloud Service 구성에 사용된 [!DNL Adobe Sign] 계정과 동일하지 않은지 확인하십시오.

   * **[!UICONTROL 받는 사람 인증 방법]:** Adobe Sign 계약을 열기 전에 받는 사람을 인증하는 방법을 지정하십시오. 전화, 기술 자료, 소셜 ID 기반 인증 및 [!DNL Adobe Acrobat Sign]의 [정부 ID](https://helpx.adobe.com/sign/using/adobesign-authentication-government-id.html) 중에서 선택할 수 있습니다. [!DNL Adobe Acrobat Sign for Government]의 경우 전화 인증과 기술 자료 인증 중에서 선택할 수 있습니다.

   >[!NOTE]
   >
   >    * 기본적으로 소셜 ID 기반 인증은 Facebook, Google 및 LinkedIn을 사용하여 인증할 수 있는 옵션을 제공합니다. [!DNL Adobe Sign] 지원팀에 연락하여 다른 소셜 인증 공급자를 사용하도록 설정할 수 있습니다.
   >

   * 입력하거나 서명할 필드 **[!DNL Adobe Sign]개:** 받는 사람의 필드 [!DNL Adobe Sign]개를 선택하십시오. 적응형 양식에는 여러 [!DNL Adobe Sign] 필드가 있을 수 있습니다. 수신자에 대해 특정 필드를 활성화하도록 선택할 수 있습니다. 필드에 사용 가능한 모든 [!DNL Adobe Sign] 블록이 표시됩니다. 블록을 선택하면 블록의 모든 필드가 선택됩니다. X 아이콘을 사용하여 필드를 선택 취소할 수 있습니다.

   ![받는 사람-세부 정보](assets/signer-details.png)

   위의 이미지에는 [!DNL Adobe Sign] 블록의 두 가지 예가 있습니다. 개인 정보 및 Office 세부 정보

   ![저장](assets/save_icon.svg) 아이콘을 선택합니다. 수신자가 추가됩니다.

### 적응형 양식에 대한 제출 액션 선택 {#selectsubmitactionforanadaptiveform}

적응형 양식에 [!DNL Adobe Sign] 필드를 추가하고, 양식 컨테이너에서 [!DNL Adobe Sign]을(를) 활성화하고, [!DNL Adobe Sign] Cloud Service을 선택하고, Adobe Sign 계약 수신자를 추가한 후 적응형 양식에 적절한 제출 액션을 선택하십시오. 적응형 Forms 제출 액션에 대한 자세한 내용은 [제출 액션 구성](configuring-submit-actions.md)을 참조하십시오.

양식에 서명하고 제출하는 것은 서로 독립적입니다. 사용자가 양식을 제출한 후 Adobe Sign 계약이 만들어지는 즉시 적응형 양식 제출이 이루어집니다. as a Cloud Service [!DNL AEM Forms]은(는) 받는 사람이 적응형 양식을 제출하기 위해 서명하거나 다른 작업을 완료할 때까지 기다리지 않습니다. 사용자가 제출 버튼을 클릭하거나 요약 단계에 양식 요약이 표시되는 즉시 양식이 제출됩니다.

또한 [!DNL Adobe Sign] 사용 적응형 양식은 데이터를 제출하기 위해 Adobe Sign 계약 ID를 임베드합니다. 사용자 지정 코드를 사용하여 계약 상태를 추적하는 데 계약 ID를 사용할 수 있습니다(사용자 지정 구현 필요).

Adobe Sign 계약 ID(agreementId)는 적응형 양식의 제출 데이터에 포함됩니다. 기본적으로 계약 ID는 제출된 데이터의 `afSubmissionInfo` 노드에 있습니다.

```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <afData>
      <afUnboundData>
         <data>
            <textbox1613455050902>ff</textbox1613455050902>
         </data>
      </afUnboundData>
      <afBoundData>
         <data xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/" />
      </afBoundData>
      <afSubmissionInfo>
         <lastFocusItem>guide[0].guide1[0].guideRootPanel[0].textbox1613455050902[0]</lastFocusItem>
         <stateOverrides />
         <signers>
            <signer0>
               <email />
            </signer0>
         </signers>
         <afPath>/content/dam/formsanddocuments/testsign</afPath>
         <afSubmissionTime>20210311031009</afSubmissionTime>
         <agreementId>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</agreementId>
      </afSubmissionInfo>
   </afData>
```

원할 경우 계약 ID(agreementId)에 bindref를 연결할 수도 있습니다. 제출된 데이터의 afBoundData 섹션에 계약 ID를 추가합니다. 예를 들어 다음 제출된 데이터에서 계약 ID가 `<userName>` 노드에 바인딩됩니다.

```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <afData>
         <afUnboundData>
            <data />
         </afUnboundData>
         <afBoundData>
            <config xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
               <userName>3AAABLblqZhC2MWu7GFauKh45j_t2ih8mAtmbdIcNSl1HgQubhMJfDaDfylyN7NQiYRam_44ISKm45enIOafHqWZrdaxShf9r</userName>
               <dateOfBirth>0001-01-01</dateOfBirth>
            </config>
         </afBoundData>
         <afSubmissionInfo>
            <lastFocusItem>guide[0].guide1[0].guideRootPanel[0].projectDetails[0]</lastFocusItem>
            <stateOverrides />
            <signers>
               <signer0>
                  <email />
               </signer0>
            </signers>
            <afPath>/content/dam/formsanddocuments/testathon2021-1/gaurav/xsd-based</afPath>
            <afSubmissionTime>20210311095211</afSubmissionTime>
            <agreementId>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</agreementId>
         </afSubmissionInfo>
      </afData>
```

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the Adaptive Form is stored temporarily on Forms Portal. Adobe recommends using [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. 
-->

양식 서명 경험이 준비되었습니다. 양식을 미리 보고 서명 환경을 확인할 수 있습니다. 받는 사람이 전자 메일을 통해 서명할 양식을 받을 때 게시된 양식에 [!DNL Adobe Sign] 블록 필드가 표시됩니다. **[!UICONTROL 받는 사람과 양식을 작성하는 사람이 같은 경우]** 옵션이 예로 표시되어 있고 조건이 충족되었습니다. 제출 후 사용자가 Adobe Sign 계약으로 리디렉션되고 전자 메일에 계약이 나타나기를 기다리는 대신 문서에 즉시 서명할 수 있습니다.

## 적응형 양식에 대한 클라우드 서명 구성 {#configure-cloud-signatures-for-an-adaptive-form}

클라우드 기반 디지털 서명 또는 원격 서명은 데스크탑, 모바일 및 웹에서 작동하는 새로운 세대의 디지털 서명으로, 수신자 인증을 위한 최고 수준의 규정 준수 및 보증을 충족합니다. 클라우드 기반 디지털 서명을 사용하여 적응형 양식에 서명할 수 있습니다.

[Adobe Sign에 대한 적응형 양식 속성을 편집](working-with-adobe-sign.md#enableadobesign)한 후 다음 단계를 수행하여 적응형 양식에 클라우드 서명 필드를 추가하십시오.

1. 구성 요소 브라우저에서 **[!UICONTROL Adobe Sign 블록]** 구성 요소를 적응형 양식으로 드래그 앤 드롭하십시오. [!UICONTROL Adobe Sign 블록] 구성 요소에 지원되는 모든 [!DNL Adobe Sign] 필드가 있습니다. 기본적으로 적응형 양식에 **[!UICONTROL 서명]** 필드를 추가합니다.

   ![블록 서명](assets/sign-block-new.png)

1. **[!UICONTROL Adobe Sign 블록]** 구성 요소를 선택하고 **[!UICONTROL 편집]** ![편집](assets/Smock_Edit_18_N.svg) 아이콘을 선택합니다. 필드를 추가하고 필드의 형식 지정을 지정하는 옵션을 표시합니다.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** [!DNL Adobe Sign] 필드를 선택하고 추가하십시오. **B.** [!DNL Adobe Sign] 블록을 전체 화면 보기로 확장합니다.

1. **[!UICONTROL Adobe Sign 필드]** ![Adobe Sign](assets/adobesign.png) 아이콘을 선택합니다. [!DNL Adobe Sign] 필드를 선택하고 추가하는 옵션이 표시됩니다.

   **[!UICONTROL 유형]** 드롭다운 필드를 확장하여 **[!UICONTROL 디지털 서명]**&#x200B;을(를) 선택하고 **[!UICONTROL 완료]** 아이콘을 선택하여 [!DNL Adobe Sign] 블록에 선택한 필드를 추가합니다.

   ![디지털 서명](assets/digital_signatures_new.png)

   필드에 고유한 이름을 입력해야 합니다.

   다음을 사용하여 적응형 양식에 디지털 서명 적용:

   * 클라우드 서명: 트러스트 서비스 공급자가 호스팅하는 [디지털 ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html)로 서명합니다.
   * Adobe Acrobat 또는 Reader: Adobe Acrobat 또는 Reader으로 문서를 다운로드하여 열고 스마트 카드, USB 토큰 또는 파일 기반 디지털 ID를 사용하여 서명합니다.

     >[!NOTE]
     >
     > 디지털 서명은 [!DNL Adobe Acrobat Sign for Government]에도 적용되지만 클라우드 서명을 사용하여 적용할 수 없습니다.

   클라우드 서명 필드를 적응형 양식에 추가한 후 다음 단계를 수행하여 구성 프로세스를 완료합니다.

   * [적응형 양식에 Adobe Sign 활성화](#enableadobsignforanadaptiveform)
   * [적응형 양식에 대한 Adobe Sign Cloud Service 선택](#selectadobesigncloudserviceforanadaptiveform)
   * [적응형 양식에 수신자 추가](#addsignerstoanadaptiveform)
   * [적응형 양식에 대한 제출 액션 선택](#selectsubmitactionforanadaptiveform)

### 감사 페이지 또는 요약 단계 구성 요소 구성 {#configure-the-thank-you-page-or-summary-step-component}

**[!UICONTROL 요약 단계]** 구성 요소는 자동으로 양식을 제출하고 사용자 지정된 요약 페이지 내에 정보를 입력한 다음 제출된 양식의 요약을 표시합니다. 요약 단계 구성 요소는 양식에 사용할 수 있는 전체 폭을 차지합니다. 요약 단계 구성 요소가 포함된 섹션에는 다른 구성 요소가 없는 것이 좋습니다.

## 자주 묻는 질문 {#frequently-asked-questions}

**Q:** 적응형 양식을 다른 적응형 양식에 포함할 수 있습니다. 임베드된 적응형 양식을 [!DNL Adobe Sign] 활성화할 수 있습니까?
**Ans:** 아니요, Experience Manager Forms에서는 서명을 위해 [!DNL Adobe Sign]이(가) 활성화된 적응형 양식을 임베드하는 적응형 양식 사용을 지원하지 않습니다.

**Q:** 고급 템플릿을 사용하여 적응형 양식을 만들고 편집하기 위해 열면 &quot;전자 서명 또는 받는 사람이 올바르게 구성되지 않았습니다.&quot;라는 오류 메시지가 표시됩니다. 가 표시됩니다. 오류 메시지를 해결하는 방법
고급 템플릿을 사용하여 만든 **Ans:** 적응형 양식이 [!DNL Adobe Sign]을(를) 사용하도록 구성되어 있습니다. 오류를 해결하려면 [!DNL Adobe Sign] 클라우드 구성을 만들고 선택한 다음 적응형 양식에 대해 [!DNL Adobe Sign] 받는 사람을 구성하십시오.

**Q:** 적응형 양식의 정적 텍스트 구성 요소에서 [!DNL Adobe Sign] 텍스트 태그를 사용할 수 있습니까?
**Ans:** 예, 텍스트 구성 요소의 텍스트 태그를 사용하여 [!DNL Adobe Sign] 필드를 기록 문서(자동 생성된 기록 문서 옵션만 해당)가 활성화된 적응형 양식에 추가할 수 있습니다. 텍스트 태그를 만드는 절차 및 규칙에 대해 알아보려면 [Adobe Sign 설명서](https://helpx.adobe.com/sign/using/text-tag.html)를 참조하세요. 또한 적응형 Forms은 텍스트 태그에 대한 지원이 제한적입니다. 텍스트 태그를 사용하여 [Adobe Sign 블록](working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form)에서 지원하는 필드만 만들 수 있습니다.

## 문제 해결 {#troubleshoot}

### [!DNL Adobe Sign]개 계약 실패 {#adobe-sign-agreement-failures}

**문제**
[!DNL Adobe Sign] 서비스가 적응형 양식에 대해 구성된 경우, 기본 적응형 양식에 대한 [!DNL Adobe Sign] 계약을 만들지 못했습니다.

**해결**

* 적응형 양식에 사용된 [Adobe Sign Cloud Service 구성](adobe-sign-integration-adaptive-forms.md)을(를) 확인하십시오.
* [!DNL Adobe Sign] Cloud Service을 구성하는 데 사용되는 [!DNL Adobe Sign] 서버의 API 응용 프로그램에 필요한 권한이 있는지 확인하십시오.
* 여러 [!DNL Adobe Sign] Cloud Service을 사용하는 경우 모든 서비스의 **[!UICONTROL oAuth URL]**&#x200B;을(를) 동일한 **[!UICONTROL Adobe Sign Shard]**(으)로 지정합니다.

* [!DNL Adobe Sign] 계정 및 첫 번째 또는 한 명의 받는 사람에 대해 별도의 전자 메일 주소를 사용하여 구성하십시오. 첫 번째 받는 사람 또는 유일한 받는 사람(단일 받는 사람이 있는 경우)의 전자 메일 주소는 AEM Cloud Service 구성에 사용된 [!DNL Adobe Sign] 계정과 같을 수 없습니다.

>[!MORELIKETHIS]
>
>* [통합 [!DNL Adobe Sign] 와 [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md)
>* [적응형 Forms과 함께 [!DNL Adobe Sign] 사용하기 위한 모범 사례](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)


## 추가 참조 {#see-also}

{{see-also}}