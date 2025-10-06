---
title: SSL 인증서 소개
description: Cloud Manager에서 SSL 인증서를 설치하고 관리하는 데 제공하는 셀프서비스 도구에 대해 알아봅니다.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 90527b1a160e6bde35562d58407a9056ae1f0a3a
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 17%

---


# SSL 인증서 소개{#introduction}

Cloud Manager에서 SSL(Secure Socket Layer) 인증서를 설치하고 관리하는 데 제공하는 셀프서비스 도구에 대해 알아봅니다.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="SSL 인증서 관리"
>abstract="Cloud Manager가 SSL 인증서를 설치하고 관리하기 위한 셀프서비스 도구로 사용자의 사이트를 보호하는 방법에 대해 알아봅니다. Cloud Manager는 플랫폼 TLS 서비스를 사용하여 고객이 소유하고 서드파티 인증 기관에서 얻은 SSL 인증서 및 개인 키를 관리합니다."
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="SSL 인증서 보기, 업데이트 및 바꾸기"
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="SSL 인증서 상태 확인"

## SSL 인증서란 무엇입니까? {#overview}

기업과 조직은 SSL(Secure Socket Layer) 인증서를 사용하여 웹 사이트를 보호하고 고객이 웹 사이트를 신뢰할 수 있도록 합니다. SSL 프로토콜을 사용하려면 웹 서버에 SSL 인증서가 필요합니다.

조직 또는 비즈니스와 같은 엔티티가 CA(인증 기관)에 인증서를 요청하면 CA가 확인 프로세스를 완료합니다. 이 프로세스는 도메인 이름 제어 확인에서 회사 등록 문서 및 구독자 계약서 수집에 이르기까지 다양합니다. 엔티티의 정보가 확인된 후, CA는 CA의 개인 키를 사용하여 공개 키에 서명합니다. 모든 주요 인증 기관은 웹 브라우저에 루트 인증서를 가지고 있기 때문에 엔티티의 인증서는 *신뢰 체인*&#x200B;을 통해 연결되고 웹 브라우저는 이를 신뢰할 수 있는 인증서로 인식합니다.

>[!IMPORTANT]
>
>Cloud Manager는 SSL 인증서 또는 개인 키를 제공하지 않습니다. 이러한 부품은 신뢰할 수 있는 타사 조직인 인증 기관에서 받아야 합니다. 일부 잘 알려진 인증 기관에는 *DigiCert*, *암호화하겠습니다*, *GlobalSign*, *Entrust* 및 *Verisign*&#x200B;이(가) 있습니다.

## Cloud Manager을 사용하여 인증서 관리 {#cloud-manager}

Cloud Manager은 SSL 인증서를 설치하고 관리하는 셀프서비스 도구를 제공하여 사용자의 사이트 보안을 보장합니다. Cloud Manager은 인증서 관리를 위한 두 가지 모델을 지원합니다.

| | 모델 | 설명 |
| --- | --- | --- |
| A | **[Adobe 관리 SSL 인증서(DV)](#adobe-managed)** | Cloud Manager을 사용하면 빠른 도메인 설정을 위해 Adobe에서 제공하는 DV(도메인 유효성 검사) 인증서를 구성할 수 있습니다. |
| B | **[고객 관리 SSL 인증서(OV/EV)](#customer-managed)** | Cloud Manager은 사용자가 소유한 OV 및 EV SSL 인증서와 *암호화하겠습니다*. |

두 모델 모두 인증서 관리를 위한 다음과 같은 일반 기능을 제공합니다.

* 각 Cloud Manager 환경은 여러 인증서를 사용할 수 있습니다.
* 하나의 개인 키로 여러 SSL 인증서를 발급할 수 있습니다.
* 플랫폼 TLS 서비스는 종료하는 데 사용된 SSL 인증서와 해당 도메인을 호스팅하는 CDN 서비스를 기반으로 고객의 CDN 서비스로 요청을 라우팅합니다.

>[!IMPORTANT]
>
>[사용자 지정 도메인을 환경에 추가 및 연결하려면](/help/implementing/cloud-manager/custom-domain-names/introduction.md) 해당 도메인을 다루는 올바른 SSL 인증서가 있어야 합니다.

### DV(Adobe 관리) SSL 인증서 {#adobe-managed}

DV 인증서는 가장 기본적인 수준의 SSL 인증서이며 테스트 목적이나 기본 암호화를 사용하는 웹 사이트 보호에 사용되는 경우가 많습니다. DV 인증서는 [프로덕션 프로그램 및 샌드박스 프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)에서 모두 사용할 수 있습니다.

DV 인증서가 만들어지면 Adobe에서 삭제하지 않는 한 3개월마다 자동으로 갱신합니다.

>[!IMPORTANT]
>
>환경에서 CNAME 기반 유효성 검사가 포함된 (DV) SSL 인증서를 사용하는 경우 자동 인증서 갱신 전에 CNAME 레코드를 제거하면 갱신에 실패할 수 있습니다. 제거하면 인증서가 만료되고 서비스가 중단될 수 있습니다. 이 문제가 발생하지 않도록 하려면 전체 갱신 프로세스를 통해 CNAME 레코드가 제자리에 남아 있는지 확인하십시오. 갱신 프로세스는 도메인 소유권 확인을 위한 CNAME 레코드의 존재 여부에 따라 달라집니다.

### 고객 관리(OV/EV) SSL 인증서 {#customer-managed}

OV 및 EV 인증서는 CA 검증 정보를 제공합니다. 이러한 정보는 사용자가 웹 사이트 소유자, 이메일 발신자 또는 코드 또는 PDF 문서의 디지털 서명자를 신뢰할 수 있는지 평가하는 데 도움이 됩니다. DV 인증서는 이러한 소유권 확인을 허용하지 않습니다.

OV 및 EV는 Cloud Manager의 DV 인증서에 대해 이러한 기능을 추가로 제공합니다.

* 여러 환경에서 OV/EV 인증서를 사용할 수 있습니다. 즉, 한 번 추가할 수 있지만 여러 번 사용됩니다.
* 각 OV/EV 인증서는 일반적으로 여러 도메인을 포함합니다.
* Cloud Manager은 도메인에 대한 와일드카드 OV/EV 인증서를 허용합니다.

>[!TIP]
>
>사용자 정의 도메인이 여러 개인 경우 새 도메인을 추가할 때마다 인증서를 업로드하지 않을 수 있습니다. 이 경우 여러 도메인을 포함하는 단일 인증서를 얻을 수 있습니다.

#### 고객 관리 OV/EV SSL 인증서 요구 사항 {#requirements}

자체 고객 관리 SSL 인증서를 추가하도록 선택하는 경우 이 인증서는 다음과 같은 업데이트된 요구 사항을 충족해야 합니다.

* DV(도메인 유효성 검사) 인증서 및 자체 서명된 인증서는 지원되지 않습니다.
* 인증서는 OV(조직 유효성 검사) 또는 EV(확장 유효성 검사) 정책을 준수해야 합니다.
* 인증서는 신뢰할 수 있는 CA(인증 기관)에서 발급한 X.509 TLS 인증서여야 합니다.
* 지원되는 암호화 키 유형은 다음과 같습니다.

   * RSA 2048비트 표준 지원
2048비트보다 큰 RSA 키(예: 3072비트 또는 4096비트 RSA 키)는 현재 지원되지 않습니다.
   * 타원 곡선(EC) 키 `prime256v1`(`secp256r1`) 및 `secp384r1`
   * 타원 곡선 ECDSA(디지털 서명 알고리즘) 인증서. 이러한 인증서는 성능, 보안 및 효율성 향상을 위해 RSA보다 Adobe에서 권장됩니다.

* 유효성 검사를 통과하려면 인증서의 형식이 올바르게 지정되어야 합니다. 개인 키는 `PKCS#8` 형식이어야 합니다.

>[!NOTE]
>조직에서 3072비트 RSA 키를 사용하여 준수해야 하는 경우 Adobe에서 권장하는 대체 방법은 ECDSA 인증서(`secp256r1` 또는 `secp384r1`)를 사용하는 것입니다.


#### 인증서 관리 우수 사례

* **겹치는 인증서 방지:**

   * 원활한 인증서 관리를 위해 동일한 도메인과 일치하는 중복 인증서를 배포하지 마십시오. 예를 들어 특정 인증서(*.example.com)와 함께 와일드카드 인증서(*dev.example.com)가 있으면 혼동이 발생할 수 있습니다.
   * TLS 계층은 가장 구체적이고 최근에 배포된 인증서의 우선 순위를 지정합니다.

  예제 시나리오:

   * &quot;개발 인증서&quot;는 `dev.example.com`을(를) 포함하며 `dev.example.com`에 대한 도메인 매핑으로 배포됩니다.
   * &quot;단계 인증서&quot;는 `stage.example.com`을(를) 포함하며 `stage.example.com`에 대한 도메인 매핑으로 배포됩니다.
   * &quot;스테이지 인증서&quot;가 *이후* &quot;개발 인증서&quot;에 배포/업데이트되면 `dev.example.com`에 대한 요청도 제공됩니다.

     이러한 충돌을 방지하려면 인증서의 범위가 의도한 도메인으로 지정되어 있는지 확인하십시오.

* **와일드카드 인증서:**

  와일드카드 인증서(예: `*.example.com`)는 지원되지만 필요한 경우에만 사용해야 합니다. 중복될 경우에는 보다 구체적인 인증서가 우선됩니다. 예를 들어 특정 인증서는 와일드카드(`dev.example.com`) 대신 `*.example.com`을(를) 제공합니다.

* **확인 및 문제 해결:**
Cloud ManagerAdobe 을 사용하여 인증서를 설치하기 전에 `openssl`과 같은 도구를 사용하여 로컬에서 인증서의 무결성을 확인하는 것이 좋습니다. 예:

  `openssl verify -untrusted intermediate.pem certificate.pem`


<!--
>[!NOTE]
>
>If two certificates cover the same domain are installed, the one that is more exact is applied.
>
>For example, if your domain is `dev.adobe.com` and you have one certificate for `*.adobe.com` and another for `dev.adobe.com`, the more specific one (`dev.adobe.com`) is used.
-->

#### 고객 관리 인증서 형식 {#certificate-format}

Cloud Manager와 함께 설치하려면 SSL 인증서 파일이 PEM 포맷이어야 합니다. PEM 형식의 일반적인 파일 확장명은 `.pem,`입니다. `crt`, `.cer` 및 `.cert`입니다.

다음 `openssl` 명령을 사용하여 비PEM 인증서를 변환할 수 있습니다.

* PFX를 PEM으로 변환

  ```shell
  openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
  ```

* P7B를 PEM으로 변환

  ```shell
  openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
  ```

* DER을 PEM으로 변환

  ```shell
  openssl x509 -inform der -in certificate.cer -out certificate.pem
  ```

## 설치된 SSL 인증서 수 제한 {#limitations}

Cloud Manager은 설치된 인증서를 최대 70개까지 지원합니다. 이러한 인증서는 프로그램에서 하나 이상의 환경과 연결될 수 있으며 만료된 인증서도 포함됩니다.

한도에 도달한 경우 인증서를 검토하고 만료된 인증서를 삭제하는 것을 고려하십시오. 또는 인증서에 여러 도메인(최대 100개의 SAN)을 포함할 수 있으므로 동일한 인증서에서 여러 도메인을 그룹화합니다.

## 자세히 알아보기 {#learn-more}

필요한 권한이 있는 사용자는 Cloud Manager를 사용하여 프로그램의 SSL 인증서를 관리할 수 있습니다. 이러한 기능을 사용하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->

