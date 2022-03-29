---
title: SSL 인증서 추가
description: Cloud Manager의 셀프 서비스 도구를 사용하여 자체 SSL 인증서를 추가하는 방법을 알아봅니다.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
source-git-commit: 2c87d5fb33b83ca77b97391e4b0baaf38f8dd026
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 2%

---

# SSL 인증서 추가 {#adding-an-ssl-certificate}

Cloud Manager의 셀프 서비스 도구를 사용하여 자체 SSL 인증서를 추가하는 방법을 알아봅니다.

>[!TIP]
>
>인증서를 프로비저닝하는 데 며칠이 걸릴 수 있습니다. 따라서 Adobe은 미리 인증서를 프로비저닝할 것을 권장합니다.

## 인증서 형식 {#certificate-format}

Cloud Manager와 함께 설치하려면 SSL 인증서 파일이 PEM 형식이어야 합니다. PEM 형식의 일반적인 파일 확장자는 다음과 같습니다 `.pem,` .`crt`, `.cer`, 및 `.cert`.

다음 `openssl` 명령은 비 PEM 인증서를 변환하는 데 사용할 수 있습니다.

* PFX를 PEM으로 변환

   ```shell
   openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
   ```

* P7B를 PEM으로 변환

   ```shell
   openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
   ```

* DER를 PEM으로 변환

   ```shell
   openssl x509 -inform der -in certificate.cer -out certificate.pem
   ```

## 인증서 추가 {#adding-a-cert}

Cloud Manager를 사용하여 인증서를 추가하려면 다음 단계를 따르십시오.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **환경** 화면 **개요** 페이지.

1. 클릭 **SSL 인증서** 왼쪽 탐색 패널 기존 SSL 인증서 세부 사항이 포함된 테이블이 기본 화면에 표시됩니다.

   ![SSL 인증서 추가](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. 클릭 **SSL 인증서 추가** 열기 **SSL 인증서 추가** 대화 상자

   * 에 인증서 이름을 입력합니다. **인증서 이름**.
      * 이 이름은 정보 제공용으로만, 인증서를 쉽게 참조할 수 있는 모든 이름일 수 있습니다.
   * 붙여넣기 **인증서**, **개인 키**, 및 **인증서 체인** 값을 해당 필드에 입력할 수 있습니다.
      * 입력 상자의 오른쪽에 있는 붙여넣기 아이콘을 사용할 수 있습니다.
      * 세 필드는 모두 필수입니다.

   ![SSL 인증서 추가 대화 상자](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * 감지된 오류가 표시됩니다.
      * 인증서를 저장하려면 먼저 모든 오류를 해결해야 합니다.
      * 자세한 내용은 [인증서 오류](#certificate-errors) 일반적인 오류 해결에 대해 자세히 알아보려면 섹션을 참조하십시오.


1. 클릭 **저장** 인증서를 저장하려면 을 클릭합니다.

저장하면 표에 새 행으로 표시된 인증서가 표시됩니다.

![저장된 SSL 인증서](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

>[!NOTE]
>
>사용자는 **비즈니스 소유자** 또는 **배포 관리자** Cloud Manager에서 SSL 인증서를 설치하기 위한 역할입니다.

## 인증서 오류 {#certificate-errors}

인증서가 제대로 설치되지 않았거나 Cloud Manager의 요구 사항을 충족하면 특정 오류가 발생할 수 있습니다.

### 인증서 정책 {#certificate-policy}

다음 오류가 표시되면 인증서의 정책을 확인하십시오.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

일반적으로 인증서 정책은 포함된 OID 값으로 식별됩니다. 인증서를 텍스트에 출력하고 OID를 검색하면 인증서의 정책이 표시됩니다.

다음 예를 안내서로 사용하여 인증서 세부 사항을 텍스트로 출력할 수 있습니다.

```text
openssl x509 -in 9178c0f58cb8fccc.pem -text
certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            91:78:c0:f5:8c:b8:fc:cc
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = US, ST = Arizona, L = Scottsdale, O = "GoDaddy.com, Inc.", OU = http://certs.godaddy.com/repository/, CN = Go Daddy Secure Certificate Authority - G2
        Validity
            Not Before: Nov 10 22:55:36 2021 GMT
            Not After : Dec  6 15:35:06 2022 GMT
        Subject: C = US, ST = Colorado, L = Denver, O = Alexandra Alwin, CN = adobedigitalimpact.com
        Subject Public Key Info:
...
```

텍스트의 OID 패턴은 인증서의 정책 유형을 정의합니다.

| 패턴 | 정책 | Cloud Manager에서 허용 가능 |
|---|---|---|
| `2.23.140.1.1` | EV | 예 |
| `2.23.140.1.2.2` | OV | 예 |
| `2.23.140.1.2.1` | DV | 아니오 |

기준 `grep`출력 인증서 텍스트의 OID 패턴을 ping할 수 있습니다. 인증서 정책을 확인할 수 있습니다.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```

### 올바른 인증서 순서 {#correct-certificate-order}

인증서 배포가 실패하는 가장 일반적인 이유는 중간 또는 체인 인증서가 올바른 순서가 아니라는 것입니다.

중간 인증서 파일은 루트 인증서 또는 루트와 가장 가까운 인증서로 끝나야 합니다. 그들은 반드시 `main/server` 인증서를 루트에 추가합니다.

다음 명령을 사용하여 중간 파일의 순서를 결정할 수 있습니다.

```shell
openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout
```

개인 키와 `main/server` 인증서는 다음 명령을 사용하여 일치합니다.

```shell
openssl x509 -noout -modulus -in certificate.pem | openssl md5
```

```shell
openssl rsa -noout -modulus -in ssl.key | openssl md5
```

>[!NOTE]
>
>이 두 명령의 출력은 정확히 동일해야 합니다. 에 대해 일치하는 개인 키를 찾을 수 없는 경우 `main/server` 인증서를 사용하면 새 CSR을 생성하고 SSL 공급업체에서 업데이트된 인증서를 요청하여 인증서를 다시 키 대조해야 합니다.

### 인증서 유효성 날짜 {#certificate-validity-dates}

Cloud Manager에서는 현재 날짜부터 최소 90일 동안 SSL 인증서가 유효할 것으로 예상하고 있습니다. 인증서 체인의 유효성을 확인해야 합니다.
