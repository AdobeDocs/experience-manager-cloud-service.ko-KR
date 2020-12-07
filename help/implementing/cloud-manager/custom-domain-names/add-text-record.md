---
title: TXT 레코드 추가
description: 사용자 지정 도메인 이름 추가
translation-type: tm+mt
source-git-commit: 8d97bedc8c473c13e3378849741104b2c85492e2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# TXT 레코드 {#adding-txt} 추가

DNS TXT 레코드는 CDN 서비스에서 호스팅될 도메인을 허용합니다. 고객은 CDN 서비스를 사용자 지정 도메인과 배포하고 이를 백엔드 서비스에 연결할 수 있도록 클라우드 관리자를 인증하는 영역에 DNS TXT 레코드를 생성해야 합니다. 이러한 연관성은 전적으로 고객의 통제하에 있으며 Cloud Manager가 서비스의 컨텐츠를 도메인에 서비스하도록 강력하게 승인합니다. 그 승인은 철회될 수도 있다.

TXT 레코드를 만들기 전에 아래 단계를 따를 수 있습니다.

* 조직의 도메인에 대한 DNS 레코드를 수정하거나 권한이 있는 사람에게 연락할 수 있습니다.
* 도메인 호스트 또는 등록업체를 식별할 수 있습니다.

도메인 확인을 시작할 때 Cloud Manager는 확인에 사용할 이름과 TXT 값을 제공합니다. 지정된 이름 및 값을 사용하여 도메인의 DNS 서버에 TXT 레코드를 추가합니다.

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 방문하십시오.
1. `_aemverification.[yourdomainname]`을 이름으로 추가하고 TXT 값을 표시되는 대로 정확하게 추가합니다.
아래 표에 나와 있는 예제를 참조하십시오.

| 도메인 | 이름 | TXT 값 |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Cloud Manager UI에 표시되고 도메인 및 클라우드 관리자 환경에 따라 다릅니다. |
| `test.example.com` | `_aemverification.test.example.com` | Cloud Manager UI에 표시되고 도메인 및 클라우드 관리자 환경에 따라 다릅니다. |

완료되면 다음을 실행하여 결과를 확인할 수 있습니다.`dig _aemverification.[yourdomainname] -t txt`.
예상되는 결과는 Cloud Manager UI에 제공된 TXT 값을 표시해야 합니다.

예를 들어 도메인이 `example.com`인 경우 다음을 실행합니다.`dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>또한 다양한 [DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup)가 있습니다. Google DoH를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었거나 오류가 있는지 식별할 수 있습니다.

