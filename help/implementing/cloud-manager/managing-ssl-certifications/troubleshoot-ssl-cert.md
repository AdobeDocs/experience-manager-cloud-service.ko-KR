---
title: SSL 인증서 오류 문제 해결
description: 보안 연결을 유지할 수 있도록 일반적인 원인을 식별하여 SSL 인증서 오류를 해결하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b387fee62500094d712f5e1f6025233c9397f8ec
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 56%

---


# SSL 인증서 오류 문제 해결 {#certificate-errors}

인증서가 제대로 설치되지 않았거나 Cloud Manager의 요구 사항을 충족하지 않으면 특정 오류가 발생할 수 있습니다.

+++**잘못된 인증서**

이 오류는 고객이 암호화된 개인 키를 사용하고 DER 형식으로 키를 제공했기 때문에 발생합니다.

+++

+++**개인 키가 PKCS 8 형식이어야 합니다**

이 오류는 고객이 암호화된 개인 키를 사용하고 DER 형식으로 키를 제공했기 때문에 발생합니다.

+++

+++**올바른 인증서 순서**

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

+++

+++**클라이언트 인증서 제거**

인증서를 추가할 때 다음과 유사한 오류가 표시되는 경우:

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

인증서 체인에 클라이언트 인증서를 포함했을 수 있습니다. 체인에 클라이언트 인증서가 포함되어 있지 않은지 확인하고 다시 시도하십시오.

+++

+++**인증서 정책**

다음 오류가 표시되면 인증서 정책을 확인하십시오.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

포함된 OID 값은 일반적으로 인증서 정책을 식별합니다. 인증서를 텍스트로 출력하고 OID를 검색하면 인증서의 정책이 표시됩니다.

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

+++

+++**인증서 유효 날짜**

Cloud Manager는 SSL 인증서가 현재 날짜로부터 최소 90일 동안 유효할 것으로 예상합니다. 인증서 체인의 유효성을 확인합니다.

+++