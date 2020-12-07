---
title: 'DNS 설정 구성 '
description: DNS 설정 구성
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# DNS 설정 구성 {#configure-dns}

사용자 지정 도메인 이름을 확인하고 배포한 후 DNS 공급자로 사용자 지정 도메인 이름에 대한 DNS 레코드를 업데이트할 준비가 되었습니다. 이렇게 하면 사이트에서 방문자를 지원할 수 있습니다. 따라서 이 활동은 일반적으로 Go-Live 전에 수행됩니다.

>[!NOTE]
>귀하 또는 조직의 해당 개인은 DNS 공급자(도메인을 구매한 회사)에 로그인하거나 연락하여 DNS 설정을 업데이트할 수 있어야 합니다.

이렇게 하려면 사용자 지정 도메인 이름을 Cloud Manager 도메인 이름으로 가리키는 `CNAME` 또는 Apex 레코드로 DNS 설정을 구성해야 하는지 결정해야 합니다. `CNAME` 또는 A 레코드는 제공되면 도메인에 대한 모든 인터넷 트래픽을 가리키는 위치로 라우팅됩니다. 해당 위치가 트래픽을 제공하도록 제공되지 않으면 중단됩니다. 테스트를 거치지 않은 경우 컨텐츠에 오류가 있을 수 있습니다. 이러한 이유로 테스트가 완료되고 고객이 Go-Live를 사용할 준비가 되면 이 단계가 항상 수행됩니다.

## CNAME 레코드 {#cname-record}

다음 섹션에서는 DNS 구성에 적합한 레코드 유형을 결정하는 데 도움이 됩니다.

표준 이름 또는 `CNAME` 레코드는 별칭 이름을 참 또는 표준 도메인 이름으로 매핑하는 DNS 레코드 유형입니다. CNAME 레코드는 일반적으로 하위 도메인의 컨텐츠를 호스팅하는 도메인에 `www.example.com` 같은 하위 도메인을 매핑하는 데 사용됩니다.

도메인 등록업체에 로그인하고 CNAME 레코드를 만들어 아래와 같이 타겟에 사용자 지정 도메인 이름을 지정합니다.

| CNAME | 사용자 지정 도메인 이름이 Target을 가리킵니다. |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## APEX 레코드 {#apex-record}

Apex 도메인은 example.com과 같은 하위 도메인을 포함하지 않는 사용자 지정 도메인입니다. Apex 도메인이 DNS 공급자를 통해 `A`, `ALIAS` 또는 `ANAME` 레코드로 구성됩니다. Apex 도메인은 특정 IP 주소를 가리켜야 합니다.

도메인 공급자를 통해 다음 모든 A 레코드를 도메인의 DNS 설정에 추가합니다.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
