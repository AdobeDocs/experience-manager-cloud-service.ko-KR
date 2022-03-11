---
title: 소개 - SSL 인증서 관리
description: 소개 - SSL 인증서 관리
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: 828490e12d99bc8f4aefa0b41a886f86fee920b4
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 2%

---

# 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL 인증서 관리"
>abstract="Cloud Manager는 Cloud Manager UI를 통해 SSL 인증서를 설치하는 셀프 서비스 기능을 고객에게 제공합니다. Cloud Manager는 Platform TLS 서비스를 사용하여 고객이 소유하며 일반적으로 타사 인증 기관에서 얻은 SSL 인증서 및 개인 키를 관리합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/view-update-replace-ssl-certificate.html" text="SSL 인증서 보기, 업데이트 및 바꾸기"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/check-status-ssl-certificate.html" text="SSL 인증서 상태 확인"


Cloud Manager는 Cloud Manager UI를 통해 SSL 인증서를 설치하는 셀프 서비스 기능을 고객에게 제공합니다. Cloud Manager는 Platform TLS 서비스를 사용하여 고객이 소유하며 일반적으로 타사 인증 기관에서 얻은 SSL 인증서 및 개인 키를 관리합니다. 예를 들면 다음과 같습니다. *암호화*.

## 중요 고려 사항 {#important-considerations}

* Cloud Manager는 SSL 인증서 또는 개인 키를 제공하지 않습니다. 제3자 인증 기관에서 받아야 합니다. 을(를) 참조하십시오. [SSL 인증서 가져오기](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) 추가 정보

* AEM as a Cloud Service만 보안 지원 `https` 사이트. 여러 사용자 지정 도메인을 가진 고객은 도메인을 추가할 때마다 인증서를 업로드하지 않으려고 합니다. 따라서 이러한 고객은 여러 도메인이 있는 하나의 인증서를 받게 되므로 이점이 있습니다.

* AEM as a Cloud Service은 OV(조직 유효성 검사) 또는 EV(확장 유효성 검사) 정책을 준수하는 인증서만 허용합니다. DV(도메인 유효성 검사) 정책이 허용되지 않습니다. 또한 모든 인증서는 2048비트 RSA 개인 키가 일치하는 신뢰할 수 있는 CA(인증 기관)의 X.509 TLS 인증서여야 합니다.

* AEM as a Cloud Service은 도메인에 대한 와일드카드 SSL 인증서를 허용합니다.

* 언제든지, Cloud Manager에서는 인증서가 만료된 경우에도 프로그램 전체에서 하나 이상의 환경과 연결할 수 있는 최대 20개의 SSL 인증서를 허용합니다. 그러나 Cloud Manager UI에서는 이 제한을 사용하여 프로그램에 최대 50개의 SSL 인증서를 설치할 수 있습니다. 일반적으로 인증서는 여러 도메인(최대 100개의 SAN)을 포함할 수 있으므로 동일한 인증서에 여러 도메인을 그룹화하여 이 제한을 유지하는 것을 고려해 보십시오.

Cloud Manager는 다음과 같은 고객 SSL 인증서 요구 사항을 지원합니다.

* SSL 인증서는 여러 환경에서 사용할 수 있습니다. 즉, 한 번 추가하고 여러 번 사용합니다.
* 각 Cloud Manager 환경에서는 여러 인증서를 사용할 수 있습니다.
* 개인 키는 여러 SSL 인증서를 발급할 수 있습니다.
* 각 인증서에는 일반적으로 여러 도메인이 포함됩니다.
* 플랫폼 TLS 서비스는 종료에 사용된 SSL 인증서 및 해당 도메인을 호스팅하는 CDN 서비스를 기반으로 고객의 CDN 서비스에 요청을 라우팅합니다.

권한이 있는 사용자는 Cloud Manager UI SSL 인증서 페이지를 사용하여 프로그램에 대한 SSL 인증서를 관리하기 위해 여러 작업을 수행할 수 있습니다.

* [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [SSL 인증서 보기, 업데이트 또는 바꾸기](/help/implementing/cloud-manager/managing-ssl-certifications/view-update-replace-ssl-certificate.md)
   >[!NOTE]
   >이러한 작업을 사용하면 세부 사항을 보거나 곧 만료되는 인증서를 대체할 수 있습니다.
* [SSL 인증서 삭제](/help/implementing/cloud-manager/managing-ssl-certifications/delete-ssl-certificate.md)
