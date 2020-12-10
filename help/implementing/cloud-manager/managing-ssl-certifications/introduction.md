---
title: 소개 - SSL 인증서 관리
description: 소개 - SSL 인증서 관리
translation-type: tm+mt
source-git-commit: 5ebe94c8562b952521effa3b67267c3eab925d16
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# 소개 {#introduction}

Cloud Manager는 고객에게 Cloud Manager UI를 통해 SSL 인증서를 설치하는 셀프 서비스 기능을 제공합니다. Cloud Manager는 Platform TLS 서비스를 사용하여 고객이 소유하고 일반적으로 타사 인증 당국으로부터 입수한 SSL 인증서 및 개인 키를 관리합니다(예: 암호화 허용).

>[!IMPORTANT]
>클라우드 관리자는 SSL 인증서 또는 개인 키를 제공하지 않습니다. 제3자 인증 기관에서 받아야 합니다. 자세한 내용은 [SSL 인증서 가져오기](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md)를 참조하십시오.

>[!NOTE]
>CLOUD SERVICE으로 AEM은 보안 https 사이트만 지원합니다. 여러 사용자 지정 도메인을 가진 고객은 도메인을 추가할 때마다 인증서를 업로드하지 않습니다. 따라서 여러 도메인이 있는 하나의 인증서를 가져오는 것이 좋습니다.

Cloud Manager는 다음과 같은 고객 SSL 인증서 요구 사항을 지원합니다.

* SSL 인증서는 여러 환경에서 사용할 수 있습니다. 즉, 한 번 추가하고 여러 번 사용할 수 있습니다.
* 각 클라우드 관리자 환경에서는 여러 인증서를 사용할 수 있습니다.
* 개인 키는 여러 SSL 인증서를 발급할 수 있습니다.
* 각 인증서에는 일반적으로 여러 개의 도메인이 포함됩니다.
* 플랫폼 TLS 서비스는 종료에 사용되는 SSL 인증서와 해당 도메인을 호스팅하는 CDN 서비스를 기준으로 고객의 CDN 서비스에 요청을 라우팅합니다.

권한을 가진 사용자는 Cloud Manager UI SSL 인증서 페이지를 사용하여 프로그램에 대한 SSL 인증서를 관리하기 위해 몇 가지 작업을 수행할 수 있습니다.

* SSL 인증서 추가
* SSL 인증서 보기, 업데이트 또는 교체
   >[!NOTE]
   >이러한 작업을 통해 세부 사항을 보거나 만료될 인증서를 바꿀 수 있습니다.
* SSL 인증서 삭제