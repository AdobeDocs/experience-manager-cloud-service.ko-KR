---
title: TXT 레코드 추가
description: Cloud Manager에서 사용자 지정 도메인 이름을 추가하기 위해 TXT 레코드를 추가하는 방법을 알아봅니다.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 491e710223c5878bfa81c4b0a57d18ec0ec29479
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# TXT 레코드 추가 {#adding-txt}

DNS TXT 레코드는 CDN 서비스에서 호스팅될 도메인을 허용합니다. Cloud Manager가 사용자 지정 도메인에 CDN 서비스를 배포하고 이를 백엔드 서비스에 연결할 수 있도록 하는 영역에 DNS TXT 레코드를 만들어야 합니다. 이 연결은 전적으로 귀하의 제어하에 있으며 Cloud Manager가 서비스의 컨텐츠를 도메인에서 도메인으로 제공하도록 허용합니다. 이 인가는 또한 취소될 수 있다. TXT 레코드는 도메인 및 Cloud Manager 환경에 따라 다릅니다.

TXT 레코드를 추가하기 전에 이러한 요구 사항을 충족해야 합니다.

* 조직의 도메인에 대한 DNS 레코드를 수정할 수 있는 권한이 있거나, 가능한 담당자에게 문의해야 합니다.
* 도메인 호스트나 등록기관을 아직 모르는 경우 식별해야 합니다.

도메인 확인을 시작하면 Cloud Manager에서 확인을 위해 사용할 이름과 TXT 값을 제공합니다. 지정된 이름과 값을 사용하여 도메인의 DNS 서버에 TXT 레코드를 추가합니다.

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 찾습니다.
1. 추가 `_aemverification.[yourdomainname]` 로서의 **이름** 값을 지정한 다음 표시되는 대로 TXT 값을 추가합니다.

이 표의 예를 참조하십시오.

| 도메인 | 이름 | TXT 값 |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 도메인과 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 도메인과 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

완료되면 다음 명령을 실행하여 결과를 확인할 수 있습니다

```shell
dig _aemverification.[yourdomainname] -t txt
```

예상되는 결과에 Cloud Manager UI에 제공된 TXT 값이 표시됩니다.

예를 들어 도메인이 `example.com`를 실행한 후 다음을 실행합니다.

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>몇 가지 [DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup) 사용할 수 있습니다. Google DoH를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었는지 확인할 수 있습니다.
