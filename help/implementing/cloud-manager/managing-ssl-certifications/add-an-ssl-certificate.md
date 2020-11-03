---
title: SSL 인증서 추가 - SSL 인증서 관리
description: SSL 인증서 추가 - SSL 인증서 관리
translation-type: tm+mt
source-git-commit: 9026befea071777dd2b97c16cdc5c623c86c1c8d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---


# SSL 인증서 추가 {#adding-an-ssl-certificate}

>[!NOTE]
>인증서를 프로비저닝하는 데 며칠이 소요되며 인증서를 몇 개월 전에 프로비저닝하는 것이 좋습니다. SSL 인증서를 가져오는 방법을 자세히 알아보십시오.링크 삽입

## 인증서 형식 {#certificate-format}

Cloud Manager에 설치하려면 SSL 파일이 PEM 형식이어야 합니다. PEM 형식 내에 있는 일반적인 파일 확장자는 .pem, .crt, .cer 및 .cert입니다.

아래 절차에 따라 SSL 파일의 형식을 PEM으로 변환하십시오.

1. PFX를 PEM으로 변환

`openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

1. P7B를 PEM으로 변환

`openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

1. DER를 PEM으로 변환

`openssl x509 -inform der -in certificate.cer -out certificate.pem`

## 인증서 추가 {#adding-certificate}

>[!NOTE]
>* 클라우드 관리자에서 SSL 인증서를 설치하려면 사용자가 비즈니스 소유자 또는 배포 관리자 역할에 있어야 합니다.
>* Cloud Manager는 인증서가 만료되더라도 프로그램 전체에서 하나 이상의 환경과 연결할 수 있는 최대 5개의 SSL 인증서를 허용합니다. 그러나 Cloud Manager UI에서는 이 제한 사항이 있는 프로그램에 최대 50개의 SSL 인증서를 설치할 수 있습니다.


1. Cloud Manager에 로그인합니다.
1. 개요 페이지에서 환경 화면으로 이동합니다.
1. 왼쪽 탐색 메뉴에서 SSL 인증서 화면으로 이동합니다. 기존 SSL 인증서에 대한 세부 정보가 있는 표가 이 화면에 표시됩니다.이미지 삽입
1. 인증서 **추가** 단추를 선택하여 마법사를 시작합니다.
1. 인증서 이름을 입력합니다. 인증서를 쉽게 참조할 수 있는 이름이 될 수 있습니다.
1. 인증서, 개인 키 및 체인 내용을 해당 필드에 붙여 넣습니다. 입력 상자 오른쪽에 있는 붙여넣기 아이콘을 사용합니다.
1. **저장**&#x200B;을 선택합니다.

   >[!NOTE]
   >검색된 모든 오류가 표시됩니다. 인증서를 저장하려면 모든 오류를 해결해야 합니다. 일반적인 오류 해결에 대한 자세한 내용은 인증서 삽입 링크 오류를 참조하십시오.

   인증서를 제출하면 표에 새 행으로 표시됩니다.

## 인증서 오류 {#certificate-errors}

### 올바른 인증서 순서 {#correct-certificate-order}

인증서 배포가 실패하는 가장 일반적인 이유는 중간 인증서 또는 체인 인증서가 올바른 순서가 아니기 때문입니다. 특히 중간 인증서 파일은 루트 인증서 또는 인증서와 가장 가까운 인증서로 끝나야 하며 인증서에서 루트로 `main/server` 내림차순으로 끝나야 합니다.

다음 명령을 사용하여 중간 파일의 순서를 결정할 수 있습니다.

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

다음 명령을 사용하여 개인 키와 `main/server` 인증서가 일치하는지 확인할 수 있습니다.

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>이 두 명령의 출력은 정확하게 동일해야 합니다. 인증서에 일치하는 개인 키를 찾을 수 없는 경우 `main/server` 새 CSR을 생성하거나 SSL 공급자로부터 업데이트된 인증서를 요청하여 인증서를 다시 키워야 합니다.

### 인증서 유효 날짜 {#certificate-validity-dates}

Cloud Manager에서는 SSL 인증서가 향후 90일 동안 유효할 것으로 예상하고 있습니다

인증서 체인의 유효성을 확인합니다.
