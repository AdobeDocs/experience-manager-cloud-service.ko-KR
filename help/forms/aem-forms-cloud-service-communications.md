---
title: AEM Forms as a Cloud Service - 통신
description: 데이터를 XDP 및 PDF 템플릿과 자동으로 병합하거나 PCL, ZPL 및 PostScript 형식으로 출력을 생성합니다
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 1%

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

### 다중 임차인 API

* 문서 유틸리티 API

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

### 다중 임차인 API 인증

#### 인증 헤더

Cloud Manager API에 대한 모든 인바운드 HTTP API 호출에는 다음 세 개의 헤더를 포함해야 합니다.

* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

에서 전송해야 하는 값 `x-api-key` 및 `x-gw-ims-org-id` 머리글은 [Adobe Developer 콘솔](https://developer.adobe.com/console). 의 값 `x-api-key` header 는 클라이언트 ID이고 `x-gw-ims-org-id` header 는 조직 ID입니다.

#### 액세스 토큰을 생성하도록 Adobe Developer 콘솔 구성

인증 API를 설정하려면 Adobe Developer Console에서 프로젝트를 만들고 Communication API를 Adobe Developer Console의 프로젝트에 추가합니다. 통합은 API 키, 클라이언트 암호, 페이로드(JWT)를 생성합니다.

1. Adobe Developer 콘솔 관리자에게 문의하십시오. 개발자로 추가하도록 관리자에게 요청합니다.
1. 에 로그인합니다. `https://developer.adobe.com/console/`. 관리자가 Adobe Developer 콘솔에 로그인하도록 제공한 개발자 계정을 사용합니다.
1. 오른쪽 상단 모서리에서 조직을 선택합니다. 조직을 모르는 경우에는 관리자에게 문의하십시오.
1. 탭 **[!UICONTROL 새 프로젝트 만들기]**. 새 프로젝트를 시작할 화면이 나타납니다. 탭 **[!UICONTROL API 추가]**. 계정에 대해 모든 API 목록이 활성화된 화면이 나타납니다.
1. 선택 **[!UICONTROL AEM Forms - 통신]** 탭 **[!UICONTROL 다음]**. API를 구성하는 화면이 나타납니다.
1. 선택 **[!UICONTROL 옵션 1 키 쌍 생성]** 탭 **[!UICONTROL 키 쌍 생성]**. 구성 파일을 만들고 다운로드합니다. 다운로드한 구성 파일에는 모든 앱 설정과 개인 키의 유일한 사본이 포함되어 있습니다. Adobe이 개인 키를 기록하지 않으므로 다운로드한 파일을 안전하게 저장해야 합니다. 탭 **[!UICONTROL 다음]**.
1. 선택 **[!UICONTROL 통합 - Cloud Service]** 탭 **[!UICONTROL 구성된 API 저장]**. 탭 **[!UICONTROL 서비스 계정(JWT)]** api 키, 클라이언트 암호 및 API에 액세스하는 데 필요한 기타 정보를 보려면 다음을 수행하십시오. 토큰을 사용하여 API에 액세스하도록 설정합니다.

#### 프로그래밍 방식으로 액세스 토큰을 생성하고 사용합니다

액세스 토큰을 프로그래밍 방식으로 생성하려면 JSON 웹 토큰(JWT)을 생성하고 액세스 토큰을 위한 IMS(Adobe Identity Management Service)와 교환하십시오.

JWT JSON 개체를 구성하려면 청구라고도 하는 다음 키를 사용합니다.

* `exp`- 1970년 1월 1일 GMT 이후 시간(초)으로 표시되는 액세스 토큰의 요청된 만료. 대부분의 사용 사례에서 이는 상대적으로 작은 값입니다. 예를 들어 5분, 지금부터 5분 동안 이 값은 1670923791이어야 합니다.
* `iss` - Adobe Developer 콘솔 프로젝트의 조직 ID는 org_ident@AdobeOrg 형식입니다.
* `sub` - Adobe Developer 콘솔 통합에서 기술 계정 ID(다음 형식)입니다. id@techacct.adobe.com
* `aud` - Adobe Developer 콘솔 통합에서 가져온 클라이언트 ID 앞에 `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - 리터럴 값으로 설정 `true`

그런 다음 이 JSON 개체는 base64로 인코딩되고 프로젝트의 개인 키를 사용하여 서명해야 합니다. 마지막으로 인코딩된 값은 POST 요청 본문에 `https://ims-na1.adobelogin.com/ims/exchange/jwt` ( 는 프로젝트에 대한 클라이언트 ID 및 클라이언트 암호 와 함께 사용됩니다.

##### 예

```JSON
    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache
```

#### JWT에 대한 언어 지원

사용자 지정 코드에서 전체 JWT 생성 및 교환 프로세스를 수행할 수 있지만 더 높은 수준의 라이브러리를 사용하는 것이 일반적입니다. 이러한 라이브러리 수는 [Adobe I/O JWT 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

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
