---
title: TXT 레코드 추가
description: 사용자 지정 도메인 이름 추가
exl-id: d441de29-af41-4d3e-9155-531af9702841
translation-type: tm+mt
source-git-commit: 4903f97c1bf0e7c8e96d604feb005d9611a7d9bb
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# TXT 레코드 {#adding-txt} 추가

DNS TXT 레코드는 CDN 서비스에서 호스팅할 도메인을 허용합니다. 고객은 Cloud Manager가 사용자 지정 도메인과 CDN 서비스를 배포하고 이를 백엔드 서비스와 연결할 수 있도록 하는 DNS TXT 레코드를 해당 영역에 만들어야 합니다. 이러한 연관성은 전적으로 고객의 통제하에 있으며 Cloud Manager가 서비스의 컨텐츠를 도메인에 제공하도록 적극 승인합니다. 그 승인이 철회될 수도 있다.

TXT 레코드를 만들기 전에 아래 단계를 따를 수 있습니다.

* 조직의 도메인에 대한 DNS 레코드를 수정하거나 권한이 있는 사람에게 연락할 수 있습니다.
* 이미 모르는 경우 도메인 호스트 또는 등록업체를 식별합니다.

도메인 확인을 시작할 때 Cloud Manager는 확인에 사용할 이름과 TXT 값을 제공합니다. 지정된 이름 및 값을 사용하여 도메인의 DNS 서버에 TXT 레코드를 추가합니다.

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 참조하십시오.
1. `_aemverification.[yourdomainname]`을 이름으로 추가하고 TXT 값을 표시되는 대로 정확하게 추가합니다.
아래 표에 나와 있는 예를 참조하십시오.

| 도메인 | 이름 | TXT 값 |
|--- |--- |---|
| `example.com` | `_aemverification` | Cloud Manager UI에 표시되며 도메인 및 클라우드 관리자 환경에 따라 다릅니다. |
| `test.example.com` | `_aemverification` | Cloud Manager UI에 표시되며 도메인 및 클라우드 관리자 환경에 따라 다릅니다. |

완료되면 다음을 실행하여 결과를 확인할 수 있습니다.`dig _aemverification.[yourdomainname] -t txt`.
예상되는 결과는 Cloud Manager UI에 제공된 TXT 값을 표시해야 합니다.

예를 들어 도메인이 `example.com`인 경우 다음을 실행합니다.`dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>또한 다양한 [DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup)가 있습니다. Google DoH를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었거나 오류가 있는지 식별할 수 있습니다.
