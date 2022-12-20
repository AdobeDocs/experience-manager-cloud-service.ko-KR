---
title: AEM Forms as a Cloud Service - 통신
description: 데이터를 XDP 및 PDF 템플릿과 자동으로 병합하거나 PCL, ZPL 및 PostScript 형식으로 출력을 생성합니다
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 33e59ce272223e081710294a2e2508edb92eba52
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---


# 동기 처리 사용 {#sync-processing-introduction}

Forms as a Cloud Service - Communications API를 사용하면 비즈니스 서신, 문서, 명세서, 청구 처리 편지, 혜택 공지, 청구 처리 편지, 월별 청구서 및 환영 키트와 같은 브랜드 지향적이고 개인화된 커뮤니케이션을 생성, 조합 및 제공할 수 있습니다. Communications API를 사용하여 템플릿(XFA 또는 PDF)을 고객 데이터와 결합하여 PDF, PS, PCL, DPL, IPL 및 ZPL 형식으로 문서를 생성할 수 있습니다.

각 템플릿에 대해 하나 이상의 템플릿과 여러 개의 XML 데이터 레코드가 있는 시나리오를 생각해 보십시오. Communications API를 사용하여 각 레코드에 대한 인쇄 문서를 생성할 수 있습니다. <!-- You can also combine the records into a single document. --> 그 결과는 비대화형 PDF 문서입니다. 비대화형 PDF 문서에서는 사용자가 해당 필드에 데이터를 입력할 수 없습니다.

Forms as a Cloud Service - Communications에서는 예약된 문서 생성을 위해 온디맨드 및 배치 API(비동기 API)를 제공합니다.

* 동기 API는 온디맨드, 지연 시간 및 단일 레코드 문서 생성 사용 사례에 적합합니다. 이러한 API는 사용자 작업 기반 사용 사례에 더 적합합니다. 예를 들어, 사용자가 양식을 입력한 후 문서를 생성합니다.

* 배치 API(비동기 API)는 예약된 높은 처리량 다중 문서 생성 사용 사례에 적합합니다. 이러한 API는 문서를 일괄로 생성합니다. 예를 들어, 매월 생성된 전화 요금 청구서, 신용 카드 명세서 및 혜택 명세서 등이 있습니다.

## 동기 작업 사용 {#batch-operations}

동기 작업은 선형 방식으로 문서를 생성하는 프로세스입니다. 이러한 API는 단일 임차인 API 및 다중 임차인 API로 분류됩니다.

### 단일 임차인 API

* 문서 생성 API
* 문서 조작 API

<!-- 
### Multi-tenant APIs

* Document utility APIs -->


### 단일 테넌트 API 인증

단일 임차인 API 작업은 두 가지 유형의 인증을 지원합니다.

* **기본 인증**: 기본 인증은 HTTP 프로토콜에 빌드된 간단한 인증 체계입니다. 클라이언트는 Basic 다음에 공백 및 base64로 인코딩된 문자열 username:password를 포함하는 Authorization 헤더를 사용하여 HTTP 요청을 보냅니다. 예를 들어, 클라이언트가 Basic을 전송하는 관리자/관리자로 승인합니다 [base64로 인코딩된 문자열 사용자 이름]: [base64로 인코딩된 문자열 암호].

* **토큰 기반 인증:** 토큰 기반 인증은 액세스 토큰(베어러 인증 토큰)을 사용하여 as a Cloud Service으로 Experience Manager을 요청합니다. AEM Forms as a Cloud Service은 액세스 토큰을 안전하게 검색하기 위한 API를 제공합니다. 토큰을 검색하고 사용하여 요청을 인증하려면:

   1. [개발자 콘솔에서 Experience Manager as a Cloud Service 자격 증명을 검색합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [환경에 Experience Manager as a Cloud Service 자격 증명 설치](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (Application Server, Web Server 또는 기타 비 AEM 서버)가 클라우드 서비스에 요청을 전송(호출)하도록 구성되어 있습니다.
   1. [JWT 토큰을 생성하고 이 토큰을 Adobe IMS API와 교환하여 액세스 토큰을 받았습니다](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. 액세스 토큰을 사용하여 Experience Manager API를 Bearer 인증 토큰으로 실행합니다.
   1. [Experience Manager 환경에서 기술 계정 사용자에 대한 적절한 권한 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe은 프로덕션 환경에서 토큰 기반 인증을 사용하는 것을 권장합니다.

<!-- 

### Authenticate a multi-tenant API

#### Authentication Headers

Every inbound HTTP API call to the multi-tenant API must contain these three headers:


* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

The values which should be sent in the `x-api-key` and `x-gw-ims-org-id` headers are provided in the Credentials details screen in the [Adobe Developer Console](https://developer.adobe.com/console). The value of the `x-api-key` header is the Client ID and the value for the `x-gw-ims-org-id` header is the Organization ID.

#### Configure Adobe Developer console to generate an access token

To set up authentication APIs, create a project in Adobe Developer Console and add Communication APIs to the project on Adobe Developer Console. The integration generates API Key, Client Secret, Payload (JWT):

1. Contact you Adobe Developer Console administrator. Ask the administrator to add as a developer.
1. Log in to `https://developer.adobe.com/console/`. Use your developer account that your administrator has provisioned to log in to Adobe Developer Console.
1. Select your organization from the top-right corner. If you do not know your organization, contact your administrator.
1. Tap **[!UICONTROL Create new project]**. A screen to get started with your new project appears. Tap **[!UICONTROL Add API]**. A screen with list of all the APIs enabled for your account appears.
1. Select **[!UICONTROL AEM Forms - Communications]** and tap **[!UICONTROL Next]**. A screen to configure the API appears.
1. Select **[!UICONTROL OPTION 1 Generate a key pair]** and tap **[!UICONTROL Generate keypair]**. It creates and downloads the configuration file. The downloaded configuration file contains all your app settings, along with the only copy of your private key. Adobe does not record your private key, make sure to securely store the downloaded file. Tap **[!UICONTROL Next]**.
1. Select **[!UICONTROL Integrations - Cloud Service]** and tap **[!UICONTROL Save configured API]**. Tap **[!UICONTROL Service Account (JWT)]** to view the API Key, Client Secret, and other information required to access the APIs. You set to use the token to access the APIs.

#### Programmatically generate and use an access token

To programmatically generate an access token, generate a JSON Web Token (JWT) and exchange it with the Adobe Identity Management Service (IMS) for an access token.

Use the following keys, referred to as claims, to construct JWT JSON object:


* `exp`- the requested expiration of the access token, expressed as a number of seconds since January 1, 1970 GMT. For most use cases, this is a relatively small value. For example, 5 minutes, for five minutes from now, this value should be 1670923791.
* `iss` - the Organization ID from the Adobe Developer Console project, in the format org_ident@AdobeOrg.
* `sub` - the Technical Account ID from the Adobe Developer Console integration, in the format: id@techacct.adobe.com.
* `aud` - the Client ID from the Adobe Developer Console integration prepended with `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - set to the literal value `true`

This JSON object must be then base64 encoded and signed using the private key for the project. Finally, the encoded value is sent in the body of a POST request to `https://ims-na1.adobelogin.com/ims/exchange/jwt` along with the Client ID and Client Secret for the project.

##### Example

```JSON

    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache

```

#### Language Support for JWT

While it is possible to do the entire JWT generation and exchange process in custom code, it is more common to use a higher-level library to do so. A number of such libraries are listed on the [Adobe I/O JWT Documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

-->

### (문서 생성 API에 대해서만) 자산 및 권한 구성

동기 API를 사용하려면 다음 조건을 충족해야 합니다.

* Experience Manager 관리자 권한이 있는 사용자
* 템플릿 및 기타 자산을 Experience Manager Forms Cloud Service 인스턴스에 업로드합니다

### (문서 생성 API에 대해서만) 템플릿 및 기타 자산을 Experience Manager 인스턴스에 업로드합니다

조직에는 일반적으로 여러 템플릿이 있습니다. 예를 들어, 신용 카드 명세서, 복리후생 명세서 및 클레임 신청에 대해 각각 하나의 템플리트가 있습니다. 이러한 모든 XDP 및 PDF 템플릿을 Experience Manager 인스턴스에 업로드합니다. 템플릿을 업로드하려면:

1. Experience Manager 인스턴스를 엽니다.
1. Forms > Forms 및 문서로 이동합니다.
1. 만들기 > 폴더 를 클릭하고 폴더를 만듭니다. 폴더를 엽니다.
1. 만들기 > 파일 업로드 를 클릭하고 템플릿을 업로드합니다.

### API 호출

다음 [API 참조 설명서](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) 는 API에서 제공하는 모든 매개 변수, 인증 방법 및 다양한 서비스에 대한 자세한 정보를 제공합니다. API 참조 설명서는 .yaml 형식의 API 정의 파일도 제공합니다. .yaml 파일을 다운로드하여 업로드할 수 있습니다. [Postman](https://www.postman.com/) 를 클릭하여 API의 기능을 확인합니다.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>forms-users 그룹의 구성원만 Communications API에 액세스할 수 있습니다.
