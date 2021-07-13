---
title: SSL 인증서 추가 - SSL 인증서 관리
description: SSL 인증서 추가 - SSL 인증서 관리
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
source-git-commit: 3b4a9d7c04a5f4feecad0f34c27a894c187152e7
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# SSL 인증서 추가 {#adding-an-ssl-certificate}

>[!NOTE]
>AEM as a Cloud Service은 OV(조직 유효성 검사) 또는 EV(확장 유효성 검사) 인증서만 허용합니다. DV(도메인 유효성 검사) 인증서가 허용되지 않습니다. 또한 모든 인증서는 2048비트 RSA 개인 키가 일치하는 신뢰할 수 있는 CA(인증 기관)의 X.509 TLS 인증서여야 합니다. AEM as a Cloud Service은 도메인에 대한 와일드카드 SSL 인증서를 허용합니다.

인증서를 프로비저닝하는 데 며칠이 걸리며, 몇 개월 전에 인증서를 프로비저닝하는 것이 좋습니다. 자세한 내용은 [SSL 인증서 가져오기](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md)를 참조하십시오.

## 인증서 형식 {#certificate-format}

Cloud Manager에 설치하려면 SSL 파일이 PEM 형식이어야 합니다. PEM 형식 내의 일반적인 파일 확장자는 `.pem,` 입니다.`crt`, `.cer`, 및 `.cert`.

SSL 파일의 형식을 PEM으로 변환하려면 아래 절차를 따르십시오.

* PFX를 PEM으로 변환

   `openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

* P7B를 PEM으로 변환

   `openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

* DER를 PEM으로 변환

   `openssl x509 -inform der -in certificate.cer -out certificate.pem`

## 중요 고려 사항 {#important-considerations}

* Cloud Manager에서 SSL 인증서를 설치하려면 비즈니스 소유자 또는 배포 관리자 역할에 사용자가 있어야 합니다.

* 언제든지, Cloud Manager에서는 인증서가 만료된 경우에도 프로그램 전체에서 하나 이상의 환경과 연결할 수 있는 최대 10개의 SSL 인증서를 허용합니다. 그러나 Cloud Manager UI에서는 이 제한을 사용하여 프로그램에 최대 50개의 SSL 인증서를 설치할 수 있습니다. 일반적으로 인증서는 여러 도메인(최대 100개의 SAN)을 포함할 수 있으므로 동일한 인증서에 여러 도메인을 그룹화하여 이 제한 범위를 유지하는 것을 고려해 보십시오.


## 인증서 추가 {#adding-a-cert}

아래 절차에 따라 인증서를 추가하십시오.

1. Cloud Manager에 로그인합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. 왼쪽 탐색 메뉴에서 **SSL 인증서**&#x200B;를 클릭합니다. 기존 SSL 인증서 세부 사항이 포함된 테이블이 이 화면에 표시됩니다.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. **SSL 인증서 추가**&#x200B;를 클릭하여 **SSL 인증서 추가** 대화 상자를 엽니다.

   * **인증서 이름**&#x200B;에 인증서 이름을 입력합니다. 인증서를 쉽게 참조할 수 있는 모든 이름일 수 있습니다.
   * **인증서**, **개인 키** 및 **인증서 체인**을 각각의 필드에 붙여 넣습니다. 입력 상자의 오른쪽에 있는 붙여넣기 아이콘을 사용합니다.
세 필드는 모두 선택 사항이 아니므로 포함해야 합니다.

      ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)


      >[!NOTE]
      >감지된 오류가 표시됩니다. 인증서를 저장하려면 먼저 모든 오류를 해결해야 합니다. 일반적인 오류 해결에 대한 자세한 내용은 [인증서 오류](#certificate-errors)를 참조하십시오.

1. **저장**&#x200B;을 클릭하여 인증서를 제출합니다. 표에 새 행으로 표시되는 것을 볼 수 있습니다.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

## 인증서 오류 {#certificate-errors}

### 올바른 인증서 순서 {#correct-certificate-order}

인증서 배포가 실패하는 가장 일반적인 이유는 중간 또는 체인 인증서가 올바른 순서가 아니라는 것입니다. 특히 중간 인증서 파일은 루트 인증서 또는 인증서로 끝나야 하며 `main/server` 인증서에서 루트로 내림차순으로 끝나야 합니다.

다음 명령을 사용하여 중간 파일의 순서를 결정할 수 있습니다.

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

다음 명령을 사용하여 개인 키 및 `main/server` 인증서가 일치하는지 확인할 수 있습니다.

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>이 두 명령의 출력은 정확히 동일해야 합니다. `main/server` 인증서에 일치하는 개인 키를 찾을 수 없는 경우에는 새 CSR을 생성하거나 SSL 공급업체에서 업데이트된 인증서를 요청하여 인증서를 다시 키 대조해야 합니다.

### 인증서 유효성 날짜 {#certificate-validity-dates}

Cloud Manager는 향후 최소 90일 동안 SSL 인증서가 유효할 것으로 예상하고 있습니다. 인증서 체인의 유효성을 확인해야 합니다.
