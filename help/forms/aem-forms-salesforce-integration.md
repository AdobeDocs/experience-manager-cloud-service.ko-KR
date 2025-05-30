---
title: OAuth 2.0 클라이언트 자격 증명 플로우를 사용하여 AEM Forms과 Salesforce를 통합하는 방법은 무엇입니까?
description: OAuth 2.0 클라이언트 자격 증명 플로우를 사용하여 Salesforce를 AEM Forms과 통합하는 방법에 대해 알아봅니다. AEM Forms Salesforce 통합 단계가 표시됩니다.
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration, AEM Forms Salesforce integration
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2c2029ab-6fb4-41a6-846c-175c3a79d921
source-git-commit: 9eb15dda5f56938d686d0b863cb1ffa841f8228b
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 56%

---

# 적응형 양식을 Salesforce과(와) 통합 {#configure-salesforce-with-ouath-2.0-client-credential}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

Adobe Experience Manager(AEM) Forms과 Salesforce를 통합하면 조직에서 양식 생성 및 관리 기능을 Salesforce 플랫폼과 연결하여 프로세스를 간소화할 수 있습니다. 적응형 양식을 Salesforce와 연결하면 두 플랫폼 간에 원활한 데이터 교환이 가능합니다. 사용자가 양식을 제출하면 데이터가 자동으로 Salesforce와 동기화됩니다. 모든 고객 정보가 최신 상태로 시스템 내에서 중앙 집중식으로 관리됩니다.

OAuth 2.0 클라이언트 자격 증명을 사용하여 AEM Forms를 Salesforce 애플리케이션과 통합할 수 있습니다. OAuth 2.0 클라이언트 자격 증명은 사용자 개입 없는 직접 통신을 위한 표준 보안 방법입니다.

![AEM Forms과 Salesforce 응용 프로그램 간의 통신을 설정하는 동안 워크플로우](/help/forms/assets/salesforce-workflow.png)

AEM Forms은 Salesforce 연결 애플리케이션에 정의된 클라이언트 자격 증명(소비자 키 및 소비자 암호)을 교환하여 액세스 토큰을 얻습니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

인증 코드 흐름 인증을 통한 인증에 OAuth 2.0 클라이언트 자격 증명을 사용하면 여러 가지 이점이 있습니다.

* OAuth 2.0 클라이언트 자격 증명 인증은 사용자당 5개가 넘는 연결을 허용합니다.
* AEM 데이터 소스 구성은 AEM 사용자에 대한 비활성화, 액세스 변경, 암호 업데이트 작업을 계속합니다.

## 사전 요구 사항 {#prerequisites}

Salesforce 애플리케이션과 AEM 환경 간의 통신을 설정하기 전에 다음 작업을 수행하십시오.

* [OAuth 2.0 클라이언트 자격 증명 흐름이 있는 Salesforce 연결 앱](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) 및 조직의 API 전용 사용자를 만들고 앱에 대한 소비자 키 및 소비자 암호를 받습니다.

* Swagger 파일이 조직의 API와 일치하도록 적절하게 구성되었는지 확인합니다. 또는 AEM 환경에서 활용하는 데 맞춤형으로 직접 [Swagger 파일을 만들](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=ko) 수도 있습니다.


## OAuth 2.0 클라이언트 자격 증명 흐름을 사용한 Salesforce 애플리케이션 구성 {#steps-to-create-aem-datasource-configuration}

OAuth 2.0 클라이언트 자격 증명 인증 설정을 사용하여 적응형 양식을 Salesforce 애플리케이션에 연결하려면 다음 단계를 수행하십시오.

1. 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL 데이터 소스]**&#x200B;로 이동합니다.
1. 구성 폴더를 선택합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 그러면 **[!UICONTROL 데이터 소스 구성 만들기]**&#x200B;가 나타납니다.
1. **[!UICONTROL 제목]**&#x200B;을 지정하고 **[!UICONTROL 서비스 유형]**&#x200B;을 **[!UICONTROL RESTful 서비스]**&#x200B;로 선택합니다.
1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Swagger 소스]**&#x200B;를 **[!UICONTROL 파일]로 선택합니다.**

   >[!NOTE]
   >
   > Swagger 파일을 선택하면 구성표, 호스트 이름 및 기본 경로가 자동으로 채워집니다.

1. **[!UICONTROL 찾아보기]**&#x200B;를 클릭하여 로컬 컴퓨터에서 만든 Swagger 파일을 업로드합니다.
1. **[!UICONTROL 인증 유형]**&#x200B;을 **[!UICONTROL OAuth 2.0]**&#x200B;으로 선택합니다. 그러면 **[!UICONTROL 인증 설정]** 패널이 나타납니다.
1. **[!UICONTROL 부여 유형]**&#x200B;을 **[!UICONTROL 클라이언트 자격 증명]**&#x200B;으로 선택합니다.
1. Salesforce 연결된 앱에서 받은 **[!UICONTROL 클라이언트 ID]** 및 **[!UICONTROL 클라이언트 보안]**&#x200B;을 지정합니다.
1. **[!UICONTROL 액세스 토큰 URL]**&#x200B;을 다음과 같은 형식으로 지정합니다.
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`

   >[!NOTE]
   >
   > 각 조직에는 고유한 특정 도메인 이름이 있습니다.

1. **[!UICONTROL 연결 테스트]**&#x200B;를 클릭합니다.
1. 연결에 성공하면 **[!UICONTROL 만들기]** 버튼을 클릭합니다.


Salesforce 응용 프로그램을 구성한 후 FDM(양식 데이터 모델)을 만드는 동안 구성을 사용할 수 있습니다. 자세한 내용은 [FDM(양식 데이터 모델) 만들기](create-form-data-models.md)를 참조하십시오. 적응형 양식에 대해 [양식 데이터 모델 제출 액션을 구성하여 Salesforce 응용 프로그램에 데이터를 보냅니다](/help/forms/using-form-data-model.md).

비즈니스 워크플로우에서 양식 데이터 모델(FDM)을 만들고 사용하는 방법에 대한 자세한 내용은 [데이터 통합](data-integration.md)을 참조하십시오.

## 관련 문서

{{af-submit-action}}


