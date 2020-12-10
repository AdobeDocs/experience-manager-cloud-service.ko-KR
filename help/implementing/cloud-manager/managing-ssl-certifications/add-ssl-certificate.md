---
title: SSL 인증서 추가 - SSL 인증서 관리
description: SSL 인증서 추가 - SSL 인증서 관리
translation-type: tm+mt
source-git-commit: 1e7855661220f69038edf35d4c45b7d45b5c6bce
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# SSL 인증서 {#adding-an-ssl-certificate} 추가

>[!NOTE]
>AEM은 OV(조직 유효성 검사) 또는 EV(확장 유효성 검사) 인증서만 받습니다. DV(도메인 유효성 검사) 인증서가 허용되지 않습니다. 또한 모든 인증서는 2048비트 RSA 개인 키가 일치하는 신뢰할 수 있는 인증 기관(CA)의 X.509 TLS 인증서여야 합니다.

인증서를 프로비저닝하는 데 며칠이 소요되며 인증서를 몇 개월 전에 프로비저닝하는 것이 좋습니다. 자세한 내용은 [SSL 인증서 가져오기](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md)를 참조하십시오.

## 인증서 형식 {#certificate-format}

Cloud Manager에 설치하려면 SSL 파일이 PEM 형식이어야 합니다. PEM 형식 내에 있는 일반적인 파일 확장자는 `.pem,`입니다.`crt`, `.cer`, 및 `.cert`.

아래 절차에 따라 SSL 파일의 형식을 PEM으로 변환하십시오.

* PFX를 PEM으로 변환

   `openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

* P7B를 PEM으로 변환

   `openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

* DER를 PEM으로 변환

   `openssl x509 -inform der -in certificate.cer -out certificate.pem`

## 중요 고려 사항 {#important-considerations}

* 클라우드 관리자에서 SSL 인증서를 설치하려면 사용자가 비즈니스 소유자 또는 배포 관리자 역할에 있어야 합니다.

* Cloud Manager는 인증서가 만료되더라도 프로그램 전체에서 하나 이상의 환경과 연결할 수 있는 최대 10개의 SSL 인증서를 허용합니다. 그러나 Cloud Manager UI에서는 이 제한 사항이 있는 프로그램에 최대 50개의 SSL 인증서를 설치할 수 있습니다.

## 인증서 {#adding-a-cert} 추가

아래 절차에 따라 인증서를 추가하십시오.

1. Cloud Manager에 로그인합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. 왼쪽 탐색 메뉴에서 **SSL 인증서**&#x200B;를 클릭합니다. 기존 SSL 인증서에 대한 세부 정보가 있는 표가 이 화면에 표시됩니다.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. **SSL 인증서 추가**&#x200B;를 클릭하여 **SSL 인증서 추가** 대화 상자를 엽니다.

   * **인증서 이름**&#x200B;에 인증서 이름을 입력합니다. 인증서를 쉽게 참조할 수 있는 이름이 될 수 있습니다.
   * **인증서**, **개인 키** 및 **인증서 체인**을 해당 필드에 붙여 넣습니다. 입력 상자 오른쪽에 있는 붙여넣기 아이콘을 사용합니다.
세 필드 모두 선택 사항이 아니므로 포함되어야 합니다.

      ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)


      >[!NOTE]
      >검색된 모든 오류가 표시됩니다. 인증서를 저장하려면 모든 오류를 해결해야 합니다. 일반적인 오류 해결에 대한 자세한 내용은 [인증서 오류](#certificate-errors)를 참조하십시오.

1. 인증서를 제출하려면 **저장**&#x200B;을 클릭합니다. 표에 새 행으로 표시되는 것을 확인할 수 있습니다.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

## 인증서 오류 {#certificate-errors}

### 올바른 인증서 순서 {#correct-certificate-order}

인증서 배포가 실패하는 가장 일반적인 이유는 중간 인증서 또는 체인 인증서가 올바른 순서가 아니기 때문입니다. 특히 중간 인증서 파일은 루트 인증서 또는 인증서와 가장 가까운 인증서로 끝나야 하며 `main/server` 인증서에서 루트로 내림차순으로 끝나야 합니다.

다음 명령을 사용하여 중간 파일의 순서를 결정할 수 있습니다.

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

다음 명령을 사용하여 개인 키와 `main/server` 인증서가 일치하는지 확인할 수 있습니다.

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>이 두 명령의 출력은 정확하게 동일해야 합니다. `main/server` 인증서에 일치하는 개인 키를 찾을 수 없는 경우, 새 CSR을 생성하고 SSL 공급자로부터 업데이트된 인증서를 요청하여 인증서를 다시 키워야 합니다.

### 인증서 유효 날짜 {#certificate-validity-dates}

Cloud Manager에서는 SSL 인증서가 향후 90일 이상 유효할 것으로 예상하고 있습니다. 인증서 체인의 유효성을 확인해야 합니다.
