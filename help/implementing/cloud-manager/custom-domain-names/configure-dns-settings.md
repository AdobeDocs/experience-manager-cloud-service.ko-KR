---
title: DNS 설정 구성
description: 사용자 정의 도메인 이름에 대한 DNS 설정을 구성하는 방법에 대해 알아봅니다.
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: 9fd7c17fce8c11809eabcc6387cbace0ebdc64a2
workflow-type: ht
source-wordcount: '338'
ht-degree: 100%

---

# DNS 설정 구성 {#configure-dns}

사용자 정의 도메인 이름이 정상적으로 확인 및 배포되면 DNS 공급자를 통해 사용자 정의 도메인 이름에 대한 DNS 레코드를 업데이트할 수 있습니다. 이렇게 하면 사이트에서 방문자에게 서비스를 제공할 수 있습니다. 따라서 이 활동은 일반적으로 라이브로 전환되기 전에 수행됩니다.

## DNS 설정이란? {#dns-settings}

`CNAME` 또는 A 레코드가 프로비저닝되면 도메인의 모든 인터넷 트래픽이 지정된 위치로 라우팅됩니다. 해당 위치에서 트래픽을 처리할 수 있도록 프로비저닝되지 않은 경우, 중단이 발생합니다. 테스트를 거치지 않은 경우 콘텐츠에 오류가 발생할 수 있습니다. 따라서 이 단계는 항상 테스트가 완료되고 실행 준비가 된 후에 수행됩니다.

이러한 설정을 구성하려면 사용자 정의 도메인 이름이 Cloud Manager 도메인 이름을 가리키도록 `CNAME` 또는 Apex 레코드를 구성해야 하는지 여부를 결정해야 합니다. 다음 섹션에서는 DNS 구성에 적합한 레코드 유형을 결정하는 데 도움이 되는 정보를 제공합니다.

>[!NOTE]
>
>귀하 또는 귀하의 조직에서 적절한 개인이 로그인하거나 DNS 공급자(도메인을 구입한 회사)에 연락하여 DNS 설정을 업데이트할 수 있어야 합니다.

## CNAME 레코드 {#cname-record}

정식 이름 또는 CNAME 레코드는 별칭 이름을 실제 또는 정식 도메인 이름에 매핑하는 DNS 레코드 유형입니다. CNAME 레코드는 일반적으로 `www.example.com`과 같은 하위 도메인을 해당 하위 도메인의 콘텐츠를 호스팅하는 도메인에 매핑하는 데 사용됩니다.

도메인 등록자에 로그인하고 다음 표와 같이 사용자 정의 도메인 이름이 대상을 가리키도록 `CNAME` 레코드를 만듭니다.

| CNAME | 사용자 정의 도메인 이름 대상 지정 |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## APEX 레코드 {#apex-record}

Apex 도메인은 `example.com`과 같은 하위 도메인을 포함하지 않는 사용자 정의 도메인입니다. Apex 도메인은 DNS 공급자를 통해 `A`, `ALIAS` 또는 `ANAME` 레코드로 구성됩니다. Apex 도메인은 특정 IP 주소를 가리켜야 합니다.

도메인 공급자를 통해 도메인의 DNS 설정에 다음 `A` 레코드를 모두 추가합니다.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
