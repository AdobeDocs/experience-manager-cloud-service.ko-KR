---
title: TXT 레코드 추가
description: 사용자 지정 도메인 이름 추가
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 1edf27dbe0d12c195674190d37aaf4529d29e6b9
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# TXT 레코드 추가 {#adding-txt}

DNS TXT 레코드는 CDN 서비스에서 호스팅될 도메인을 허용합니다. 고객은 Cloud Manager가 사용자 지정 도메인과 CDN 서비스를 배포하고 이를 백엔드 서비스에 연결할 수 있도록 하는 영역에 DNS TXT 레코드를 만들어야 합니다. 이 연관성은 전적으로 고객의 제어하에 있으며 Cloud Manager가 서비스에서 도메인으로 컨텐츠를 제공할 수 있도록 강력하게 허용합니다. 그 승인은 취소될 수도 있다.

TXT 레코드를 만들기 전에 아래 단계를 따라야 합니다.

* 조직의 도메인에 대한 DNS 레코드를 수정하거나 권한이 있는 담당자에게 문의하십시오.
* 도메인 호스트 또는 등록자를 식별하십시오.

도메인 확인을 시작하면 Cloud Manager에서 확인을 위해 사용할 이름과 TXT 값을 제공합니다. 지정된 이름 및 값을 사용하여 도메인의 DNS 서버에 TXT 레코드를 추가합니다.

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 참조하십시오.
1. 추가 `_aemverification.[yourdomainname]` 를 이름으로 추가하고 TXT 값을 표시되는 그대로 추가합니다.
아래 표에 나와 있는 예를 참조하십시오.

| 도메인 | 이름 | TXT 값 |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 도메인과 환경에 따라 다릅니다. `Ex:<br>adobe-aem-verification=example.com/[program]/[env]/..` |
| `www.example.com` | `_aemverification.www.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 도메인과 환경에 따라 다릅니다. `Ex:<br>adobe-aem-verification=www.example.com/[program]/[env]/..` |

완료되면 다음을 실행하여 결과를 확인할 수 있습니다. `dig _aemverification.[yourdomainname] -t txt`.
예상되는 결과에 Cloud Manager UI에 제공된 TXT 값이 표시됩니다.

예를 들어 도메인이 `example.com`를 실행한 후 다음을 실행합니다. `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>다양합니다 [DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup), Google DoH 를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었는지 확인할 수 있습니다.
