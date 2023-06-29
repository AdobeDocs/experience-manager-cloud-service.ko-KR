---
title: TXT 레코드 추가
description: Cloud Manager에서 TXT 레코드를 추가하여 사용자 정의 도메인 이름을 추가하는 방법을 알아봅니다.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 96%

---

# TXT 레코드 추가 {#adding-txt}

DNS TXT 레코드는 도메인이 CDN 서비스에서 호스팅되도록 승인합니다. Cloud Manager가 사용자 정의 도메인을 사용하여 CDN 서비스를 배포하고 이를 백엔드 서비스와 연결하도록 권한을 부여한 영역에서 DNS TXT 레코드를 생성해야 합니다. 이 연결은 전적으로 사용자의 통제 하에 있으며 Cloud Manager가 서비스에서 도메인으로 콘텐츠를 제공하도록 인증합니다. 이 인증은 승인 및 철회될 수 있습니다. TXT 레코드는 도메인 및 Cloud Manager 환경에 따라 다릅니다.

TXT 레코드를 추가하기 전에 이러한 요구 사항을 충족해야 합니다.

* 조직의 도메인에 대한 DNS 레코드를 수정할 수 있어야 하며 그렇지 않은 경우 수정할 수 있는 적절한 담당자에게 문의해야 합니다.
* 도메인 호스트 또는 등록자를 아직 모르는 경우 이를 확인해야 합니다.

도메인 인증을 시작하면 Cloud Manager가 인증에 사용할 이름과 TXT 값을 제공합니다. 지정된 이름과 값을 사용하여 도메인의 DNS 서버에 TXT 레코드를 추가합니다.

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 찾습니다.
1. **이름** 값으로 `_aemverification.[yourdomainname]`을 추가하고 나타나는 대로 TXT 값을 정확하게 추가합니다.

이 표의 예를 참조하십시오.

| 도메인 | 이름 | TXT 값 |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 이 값은 도메인 및 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 이 값은 도메인 및 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

작업이 완료되면 다음 명령을 실행하여 결과를 확인할 수 있습니다.

```shell
dig _aemverification.[yourdomainname] -t txt
```

예상 결과는 Cloud Manager UI에 제공된 TXT 값을 표시해야 합니다.

예를 들어 도메인이 `example.com`이면 다음을 실행합니다.

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>여러 [DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup)를 사용할 수 있습니다. Google DoH를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었거나 오류가 있는지 식별할 수 있습니다.
