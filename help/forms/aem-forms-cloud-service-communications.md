---
title: AEM Forms as a Cloud Service - 통신
description: 데이터를 XDP 및 PDF 템플릿과 자동으로 병합하거나 PCL, ZPL 및 PostScript 형식으로 출력을 생성합니다
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: fdbb927dbd7f6d640100d444431f931d95414ebc
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# 동기 처리 사용 {#sync-processing-introduction}

커뮤니케이션 기능을 사용하면 비즈니스 서신, 명세서, 청구 처리 편지, 혜택 공지, 월별 청구서 또는 환영 키트와 같은 브랜드 승인, 개인화 및 표준화된 문서를 만들 수 있습니다.

이 기능은 문서를 생성하고 조작하는 API를 제공합니다. 필요에 따라 문서를 생성 또는 조작하거나 배치 작업을 만들어 정의된 간격으로 여러 문서를 생성할 수 있습니다.

통신은 주문형 및 예약된 문서 생성을 위한 API를 제공합니다. 예약된 문서 생성을 위해 온디맨드 및 배치 API(비동기 API)에 동기 API를 사용할 수 있습니다.

* 동기 API는 온디맨드, 지연 시간 및 단일 레코드 문서 생성 사용 사례에 적합합니다. 이러한 API는 사용자 작업 기반 사용 사례에 더 적합합니다. 예를 들어, 사용자가 양식을 입력한 후 문서를 생성합니다.

* 배치 API(비동기 API)는 예약된 높은 처리량 다중 문서 생성 사용 사례에 적합합니다. 이러한 API는 문서를 일괄로 생성합니다. 예를 들어, 매월 생성된 전화 요금 청구서, 신용 카드 명세서 및 혜택 명세서 등이 있습니다.

## 동기 작업 사용 {#batch-operations}

동기 작업은 문서를 선형 방식으로 생성하거나 조작하는 프로세스입니다. 이 서비스는 두 가지 유형의 인증을 지원합니다.

* **기본 인증**: 기본 인증은 HTTP 프로토콜에 빌드된 간단한 인증 체계입니다. 클라이언트는 Basic 다음에 공백 및 base64로 인코딩된 문자열 username:password를 포함하는 Authorization 헤더를 사용하여 HTTP 요청을 보냅니다. 예를 들어, 클라이언트가 Basic을 전송하는 관리자/관리자로 승인합니다 [base64로 인코딩된 문자열 사용자 이름]: [base64로 인코딩된 문자열 암호].

* **토큰 기반 인증:** 토큰 기반 인증은 액세스 토큰(베어러 인증 토큰)을 사용하여 as a Cloud Service으로 Experience Manager을 요청합니다. AEM Forms as a Cloud Service은 액세스 토큰을 안전하게 검색하기 위한 API를 제공합니다. 토큰을 검색하고 사용하여 요청을 인증하려면:

   1. [개발자 콘솔에서 Experience Manager as a Cloud Service 자격 증명을 검색합니다](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [환경에 Experience Manager as a Cloud Service 자격 증명 설치](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (Application Server, Web Server 또는 기타 비 AEM 서버)가 클라우드 서비스에 요청을 전송(호출)하도록 구성되어 있습니다.
   1. [JWT 토큰을 생성하고 이 토큰을 Adobe IMS API와 교환하여 액세스 토큰을 받았습니다](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. 액세스 토큰을 사용하여 Experience Manager API를 Bearer 인증 토큰으로 실행합니다.
   1. [Experience Manager 환경에서 기술 계정 사용자에 대한 적절한 권한 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe은 프로덕션 환경에서 토큰 기반 인증을 사용하는 것을 권장합니다.

### (문서 생성 API만 해당)사전 요구 사항 {#pre-requisites}

문서 생성에 동기 API를 사용하려면 다음 조건을 충족해야 합니다.

* PDF 또는 XDP 템플릿
* [템플릿과 병합할 데이터](#form-data)
* Experience Manager 관리자 권한이 있는 사용자
* 템플릿 및 기타 자산을 Experience Manager Forms Cloud Service 인스턴스에 업로드합니다

#### 템플릿 및 기타 자산을 Experience Manager 인스턴스에 업로드합니다

조직에는 일반적으로 여러 템플릿이 있습니다. 예를 들어, 신용 카드 명세서, 복리후생 명세서 및 클레임 신청에 대해 각각 하나의 템플리트가 있습니다. 이러한 모든 XDP 및 PDF 템플릿을 Experience Manager 인스턴스에 업로드합니다. 템플릿을 업로드하려면:

1. Experience Manager 인스턴스를 엽니다.
1. Forms > Forms 및 문서로 이동합니다.
1. 만들기 > 폴더 를 클릭하고 폴더를 만듭니다. 폴더를 엽니다.
1. 만들기 > 파일 업로드 를 클릭하고 템플릿을 업로드합니다.

### 동기 API를 사용하여 문서 생성

별도의 API를 사용할 수 있는 대상:

* 템플릿에서 PDF 문서를 생성하고 여기에 데이터를 병합합니다.
* XDP 파일 또는 PDF 문서에서 PS(PostScript), PCL(Printer Command Language), ZPL(Zebra Printing Language) 문서를 생성합니다.

다음 [API 참조 설명서](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/Communications-Services) 는 API에서 제공하는 모든 매개 변수, 인증 방법 및 다양한 서비스에 대한 자세한 정보를 제공합니다. API 참조 설명서는 .yaml 형식으로도 사용할 수 있습니다. .yaml을 다운로드할 수 있습니다 [동기 API](assets/sync.yaml) 를 postman에 업로드하여 API의 기능을 확인합니다.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>forms-users 그룹의 구성원만 Communications API에 액세스할 수 있습니다.
