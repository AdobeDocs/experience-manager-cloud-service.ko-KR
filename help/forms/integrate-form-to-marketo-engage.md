---
title: Marketo Engage을 AEM Forms과 통합하는 방법
description: Marketo Engage 인스턴스를 AEM Forms과 통합하는 방법을 알아봅니다.
keywords: Marketo 인스턴스를 양식과 연결하는 방법 , 양식을 Marketo에 연결, 양식을 Marketo Engage과 통합, 적응형 양식을 Marketo 인스턴스와 통합.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 74cd25f9-1ee1-4f3f-8e02-8714071e7c86
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 5%

---

# AEM Forms와 Marketo Engage 통합

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

AEM Forms을 [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)과(와) 통합하면 사용자가 Marketo Engage의 기능을 활용하여 캡처된 데이터에서 비즈니스 논리를 만들고 스마트 캠페인 및 이메일 자동화를 비롯한 워크플로우를 자동화할 수 있습니다. 구성된 양식은 캡처된 데이터를 처리를 위해 Marketo Engage으로 전송할 수 있습니다.

## Marketo Engage과 양식 통합의 이점

다음은 AEM 양식을 Adobe Marketo Engage과 연결할 때 얻을 수 있는 몇 가지 장점입니다.

* **간소화된 통합**: Marketo Engage과 양식을 연결하면 별도의 양식 데이터 모델을 만들 필요가 없습니다. 통합 프로세스는 간단하고 사용자 친화적입니다.
* **자동화된 데이터 캡처**: 양식 제출을 자동으로 캡처하여 Marketo에 저장하는 데 도움이 되므로 수동으로 데이터를 입력할 필요가 없고 오류가 줄어듭니다.

* **리드 관리**: 양식 제출을 마케팅 데이터베이스에 직접 통합하여 리드 관리 프로세스를 간소화하므로 리드를 보다 효율적으로 추적하고 관리할 수 있습니다.

* **캠페인 성과 개선**: 양식 데이터를 사용하여 마케팅 캠페인을 분석하고 최적화하여 전반적인 성능과 ROI(투자 수익률)를 개선합니다.

* **Analytics 및 보고**: Marketo 내에서 Munchkin과 같은 강력한 분석 및 보고 도구에 액세스하여 양식 및 캠페인의 효과를 측정할 수 있습니다.

* **후속 자동화**: 양식 제출을 통해 트리거된 후속 전자 메일 및 워크플로를 자동화하여 리드와 적시에 통신할 수 있도록 지원합니다.

## 대체 양식 솔루션에 대한 AEM Forms 사용의 주요 이점

아래 표에는 다른 대체 양식 솔루션보다 AEM Forms을 선택하는 몇 가지 이유가 간략하게 나와 있습니다.

| **기능** | **AEM Forms** | **기타 양식 솔루션** |
|-------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **사용자 지정** | 특정 사용자 정의 함수를 추가하고, 양식 작업을 조정하고, 필드 동작을 수정하여 양식 상호 작용 및 복잡한 워크플로우를 개선할 수 있습니다. | 사용자 정의 지원 없음 |
| **규칙 편집기** | 는 논리 및 조건 추가를 위한 기본 제공 규칙 편집기를 지원합니다. | 규칙 편집기 지원 없음 |
| **레이아웃 옵션** | 여러 레이아웃 옵션 지원 | 제한된 레이아웃 옵션 |
| **미리 채우기 서비스** | 양식 데이터를 자동으로 채우는 미리 채우기 서비스를 제공합니다. | 사용 가능한 미리 채우기 서비스 없음 |
| **사이트에 포함** | iFrame을 사용하여 Sites에 임베드할 수 있음 | iFrame을 사용하여 Sites에 포함할 수 없음 |
| **사이트와의 통합 용이성** | 추가 학습이 필요하지 않습니다. AEM Forms은 Sites와 동일한 기술을 사용합니다. | 추가 학습이 필요할 수 있습니다 |
| **데이터 제출** | SharePoint에 연결, OneDrive에 연결, Salesforce에 연결 등과 같은 다양한 플랫폼에 데이터를 제출하고 여러 커넥터를 제공할 수 있습니다. | 제한된 커넥터(예: Salesforce)에 데이터를 제출할 수 있습니다. |

## Marketo Engage과 양식 통합을 위한 고려 사항

Marketo Engage과 AEM Forms을 통합하는 동안 고려할 사항:

* AEM은 다양한 Marketo 데이터베이스 중 사람(잠재 고객) 데이터베이스만 지원합니다.
* Marketo을 사용하면 [10개의 사용자 지정 개체를 만들 수](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-custom-objects/add-marketo-custom-object-fields)을(를) 사용자 정의 개체로 만들어 Lead의 표준 필드 이상의 특수 데이터를 저장할 수 있으므로 고유한 비즈니스 요구 사항을 지원합니다.
* AEM은 사용자 정의 객체가 리드 데이터베이스와 연결된 경우에만 액세스할 수 있습니다

## Marketo Engage과 양식 통합을 위한 사전 요구 사항

Marketo Engage을 AEM Forms과 연결하기 위한 사전 요구 사항은 다음과 같습니다.

* 유효한 Adobe Marketo Engage 라이선스
* 클라우드 구성을 만들기 위해 [클라이언트 ID 및 클라이언트 암호를 검색](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api)하는 Marketo Engage의 작업 인스턴스.

## AEM Forms(적응형 Forms)와 Marketo Engage을 연결하는 클라우드 서비스 구성 만들기

![워크플로](/help/forms/assets/workflow-marketo-1.png)

>[!VIDEO](https://video.tv.adobe.com/v/3442865/engage-marketo-aem-forms-aem)

<span> 이 비디오는 핵심 구성 요소에만 적용됩니다. UE/Foundation 구성 요소에 대해서는 문서를 참조하십시오.</span>

클라우드 구성은 Experience Manager 인스턴스를 Adobe Marketo Engage 인스턴스에 연결합니다. Marketo Engage 클라우드 구성을 만들려면 다음 단계를 수행하십시오.

1. **도구** > **클라우드 서비스** > **Marketo Engage**(으)로 이동합니다.

   ![Marketo Engage](/help/forms/assets/marketo-engage.png)

1. 구성을 호스팅할 폴더를 열고 **만들기**&#x200B;를 클릭합니다. **Marketo Engage 구성 만들기** 창이 나타납니다.

   >[!NOTE]
   >
   > [클라우드 서비스 구성에 대한 폴더를 구성](/help/forms/configure-data-sources.md#configure-folder-for-cloud-service-configurations)할 수도 있습니다.

1. 서비스에 연결할 구성 및 자격 증명의 **제목**&#x200B;을 지정하십시오. Adobe Marketo Engage 대시보드에서 인증 자격 증명을 검색할 수 있습니다.

   * **클라이언트 ID** 및 **클라이언트 암호**&#x200B;은(는) 사용자 지정 서비스를 선택하고 **세부 정보 보기**&#x200B;를 클릭하여 **관리자** > **통합** > **LaunchPoint**&#x200B;에서 사용할 수 있습니다.
   * **ID URL**&#x200B;은(는) **관리자** > **통합** > **웹 서비스**&#x200B;에서 **REST API** 섹션의 **ID**(으)로 사용할 수 있습니다.

1. **연결**&#x200B;을 클릭합니다.  연결이 완료되면 `Authentication Successful` 메시지가 나타납니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하여 클라우드 구성 설정을 저장합니다.

![Marketo Engage 클라우드 구성](/help/forms/assets/marketo-engage-cloud-configuration.png)

이제 생성된 클라우드 서비스 구성을 사용하여 Marketo Engage 데이터 소스를 적응형 양식에 연결할 수 있습니다.

## 다음 단계

Adobe Marketo Engage을 AEM Forms과 통합하기 위한 클라우드 서비스 구성을 만들었습니다. 이제 다음을 통합할 수 있습니다.

* [Marketo Engage을 사용한 새 적응형 양식](/help/forms/integrate-adaptive-form-with-marketo-engage.md)
* [Marketo Engage이 있는 기존 적응형 양식](/help/forms/use-marketo-engage-data-source-in-form.md)

## 관련 문서

{{af-submit-action}}

## 추가 참조

{{marketo-engage-see-also}}
