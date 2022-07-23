---
title: SSL 인증서 관리 소개
description: Cloud Manager에서 SSL 인증서를 설치하는 셀프 서비스 도구를 제공하는 방법을 알아봅니다.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: f69a26c6156c1f9038d612a00b16cac0e51e17ca
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 2%

---


# SSL 인증서 관리 소개{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL 인증서 관리"
>abstract="Cloud Manager는 사용자를 위한 사이트를 보호하기 위해 SSL 인증서를 설치 및 관리하는 셀프 서비스 도구를 제공하는 방법을 알아봅니다. Cloud Manager는 플랫폼 TLS 서비스를 사용하여 고객이 소유하며 타사 인증 기관에서 얻은 SSL 인증서 및 개인 키를 관리합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html" text="SSL 인증서 보기, 업데이트 및 바꾸기"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html" text="SSL 인증서 상태 확인"

Cloud Manager는 사용자를 위한 사이트를 보호하기 위해 SSL 인증서를 설치 및 관리하는 셀프서비스 도구를 제공합니다. Cloud Manager는 플랫폼 TLS 서비스를 사용하여 고객이 소유하며 Let&#39;s Encrypt와 같은 타사 인증 기관에서 얻은 SSL 인증서 및 개인 키를 관리합니다.

## 인증서 소개 {#certificates}

기업들은 웹 사이트를 안전하게 보호하고 고객이 신뢰할 수 있도록 하기 위해 SSL 인증서를 사용합니다. SSL 프로토콜을 사용하려면 웹 서버에서 SSL 인증서를 사용해야 합니다.

엔티티가 인증 기관에서 인증서를 요청하면 CA가 확인 프로세스를 완료합니다. 도메인 이름 제어를 확인하는 것부터 회사 등록 문서 및 가입자 계약 수집까지 다양할 수 있습니다. 엔티티의 정보가 확인되면 CA는 CA의 개인 키를 사용하여 공개 키에 서명합니다. 모든 주요 인증 기관에는 웹 브라우저에 루트 인증서가 있으므로 엔터티의 인증서는 *신뢰 체인* 그리고 웹 브라우저는 이 인증서를 신뢰할 수 있는 인증서로 인식합니다.

>[!IMPORTANT]
>
>Cloud Manager는 SSL 인증서 또는 개인 키를 제공하지 않습니다. 인증 기관(CA)에서 받아야 합니다.

## Cloud Manager SSL 관리 기능 {#features}

Cloud Manager는 다음과 같은 고객 SSL 인증서 사용 옵션을 지원합니다.

* SSL 인증서는 여러 환경에서 사용할 수 있습니다. 즉, 한 번 추가하고 여러 번 사용할 수 있습니다.
* 각 Cloud Manager 환경에서는 여러 인증서를 사용할 수 있습니다.
* 개인 키는 여러 SSL 인증서를 발급할 수 있습니다.
* 각 인증서는 일반적으로 여러 도메인을 포함합니다.
* 플랫폼 TLS 서비스는 종료에 사용되는 SSL 인증서 및 해당 도메인을 호스팅하는 CDN 서비스를 기반으로 고객의 CDN 서비스에 요청을 라우팅합니다.
* AEM as a Cloud Service은 도메인의 와일드카드 SSL 인증서를 허용합니다.

## 추천 {#recommendations}

AEM as a Cloud Service만 보안 지원 `https` 사이트.

* 여러 사용자 지정 도메인을 가진 고객은 도메인을 추가할 때마다 인증서를 업로드하지 않으려고 합니다.
* 이러한 고객은 여러 도메인이 있는 하나의 인증서를 받게 되므로 이점이 있습니다.

## 요구 사항 {#requirements}

* AEM as a Cloud Service은 OV(조직 유효성 검사) 또는 EV(확장 유효성 검사) 정책을 준수하는 인증서만 허용합니다.
* 모든 인증서는 2048비트 RSA 개인 키가 일치하는 신뢰할 수 있는 CA(인증 기관)의 X.509 TLS 인증서여야 합니다.
* DV(도메인 유효성 검사) 정책이 허용되지 않습니다.
* 자체 서명된 인증서는 허용되지 않습니다.

OV 및 EV 인증서는 사용자에게 웹 사이트의 소유자, 전자 메일의 보낸 사람 또는 실행 코드나 PDF 문서의 디지털 서명자가 신뢰할 수 있는지 여부를 결정하는 데 사용할 수 있는 추가적인 CA 인증 정보를 제공합니다. DV 인증서는 이러한 소유권 확인을 허용하지 않습니다.

## 제한 사항 {#limitations}

언제든지 Cloud Manager에서는 최대 50개의 SSL 인증서를 설치할 수 있습니다. 이러한 환경은 프로그램 전체에서 하나 이상의 환경과 연결될 수 있으며 만료된 인증서도 모두 포함할 수 있습니다.

한도에 도달하면 인증서를 검토하고 다음 사항을 고려하십시오.

* 만료된 인증서를 삭제하는 중입니다.
* 인증서는 여러 도메인(최대 100개의 SAN)을 포함할 수 있으므로 동일한 인증서에 여러 도메인을 그룹화합니다.

## 추가 정보 {#learn-more}

필요한 권한이 있는 사용자는 Cloud Manager를 사용하여 프로그램의 SSL 인증서를 관리할 수 있습니다. 이러한 기능 사용에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [SSL 인증서 보기, 업데이트 또는 바꾸기](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
* [SSL 인증서 삭제](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
