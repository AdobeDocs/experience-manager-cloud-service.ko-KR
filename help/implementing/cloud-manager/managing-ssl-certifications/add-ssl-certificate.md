---
title: SSL 인증서 추가
description: Cloud Manager의 셀프서비스 도구를 사용하여 자체 SSL 인증서를 추가하는 방법을 알아봅니다.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 83c9c6a974b427317aa2f83a3092d0775aac1d53
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 82%

---

# SSL 인증서 추가 {#adding-an-ssl-certificate}

Cloud Manager의 셀프서비스 도구를 사용하여 자체 SSL 인증서를 추가하는 방법을 알아봅니다.

>[!TIP]
>
>인증서를 프로비저닝하는 데 며칠이 걸릴 수 있습니다. 따라서 Adobe는 인증서를 미리 프로비저닝할 것을 권장합니다.

## 인증서 요구 사항 {#certificate-requirements}

[SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) 문서의 **인증서 요구 사항** 섹션을 검토하여 추가하려는 인증서가 AEM as a Cloud Service에서 지원되는지 확인하십시오.

## 인증서 추가 {#adding-a-cert}

Cloud Manager를 사용하여 인증서를 추가하려면 다음 단계를 수행합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직 선택

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **개요** 페이지에서 **환경** 화면으로 이동합니다.

1. 왼쪽 탐색 패널에서 **SSL 인증서**&#x200B;를 클릭합니다. 기존 SSL 인증서의 세부 정보가 포함된 표가 기본 화면에 표시됩니다.

   ![SSL 인증서 추가](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. **SSL 인증서 추가**&#x200B;를 클릭하여 **SSL 인증서 추가** 대화 상자를 엽니다.

   * **인증서 이름**&#x200B;에 인증서 이름을 입력합니다.
      * 이 이름은 정보 제공의 목적으로만 사용되며 인증서를 쉽게 참조하는 데 도움이 되는 모든 이름을 사용할 수 있습니다.
   * **인증서**, **비공개 키** 및 **인증서 체인** 값을 해당 필드에 붙여넣습니다. 세 필드는 모두 필수입니다.

   ![SSL 인증서 추가 대화 상자](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * 감지된 모든 오류가 표시됩니다.
      * 인증서를 저장하려면 먼저 모든 오류를 해결해야 합니다.
      * 일반적인 오류를 해결하는 방법에 대한 자세한 내용은 [인증서 오류](#certificate-errors) 섹션을 참조하십시오.

1. 인증서를 저장하려면 **저장**&#x200B;을 클릭합니다.

저장되면 인증서가 표에 새 행으로 표시됩니다.

![저장된 SSL 인증서](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

>[!NOTE]
>
>Cloud Manager에서 SSL 인증서를 설치하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

## 인증서 오류 {#certificate-errors}

인증서가 제대로 설치되지 않았거나 Cloud Manager의 요구 사항을 충족하지 않으면 특정 오류가 발생할 수 있습니다.

### 클라이언트 인증서 제거 {#client-certificates}

인증서를 추가할 때 다음과 유사한 오류가 표시되는 경우:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

인증서 체인에 클라이언트 인증서를 포함했을 수 있습니다. 체인에 클라이언트 인증서가 포함되어 있지 않은지 확인하고 다시 시도하십시오.

### 인증서 정책 {#certificate-policy}

다음 오류가 표시되면 인증서 정책을 확인하십시오.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

일반적으로 인증서 정책은 임베드된 OID 값으로 식별됩니다. 인증서를 텍스트로 출력하고 OID를 검색하면 인증서의 정책이 드러납니다.

다음 예를 안내서로 사용하여 인증서 세부 정보를 텍스트로 출력할 수 있습니다.

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

| 패턴 | 정책 | Cloud Manager에서 허용 여부 |
|---|---|---|
| `2.23.140.1.1` | EV | 예 |
| `2.23.140.1.2.2` | OV | 예 |
| `2.23.140.1.2.1` | DV | 아니요 |

출력 인증서 텍스트에서 OID 패턴에 대해 `grep`을 수행하여 인증서 정책을 확인할 수 있습니다.

```shell
# "EV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5

# "OV Policy"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5

# "DV Policy - Not Accepted"
openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
```

### 올바른 인증서 순서 {#correct-certificate-order}

인증서 배포가 실패하는 가장 일반적인 이유는 중간 또는 체인 인증서의 순서가 올바르지 않기 때문입니다.

중간 인증서 파일은 루트 인증서 또는 루트에 가장 가까운 인증서로 끝나야 합니다. `main/server` 인증서에서 루트까지 내림차순이어야 합니다.

다음 명령을 사용하여 중간 파일의 순서를 결정할 수 있습니다.

```shell
openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout
```

다음 명령을 사용하여 개인 키와 `main/server` 인증서가 일치하는지 확인할 수 있습니다.

```shell
openssl x509 -noout -modulus -in certificate.pem | openssl md5
```

```shell
openssl rsa -noout -modulus -in ssl.key | openssl md5
```

>[!NOTE]
>
>이 두 명령의 출력은 정확히 동일해야 합니다. `main/server` 인증서에 대해 일치하는 개인 키를 찾을 수 없는 경우, 새 CSR을 생성하거나 SSL 공급업체에 업데이트된 인증서를 요청하여 인증서 키를 다시 지정해야 합니다.

### 인증서 유효 날짜 {#certificate-validity-dates}

Cloud Manager는 SSL 인증서가 현재 날짜로부터 최소 90일 동안 유효할 것으로 예상합니다. 인증서 체인의 유효성을 확인해야 합니다.
