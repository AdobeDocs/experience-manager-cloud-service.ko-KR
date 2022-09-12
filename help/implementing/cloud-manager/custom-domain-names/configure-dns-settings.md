---
title: DNS 설정 구성
description: DNS 설정 구성
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: 60b496024b3d012033309632999851c08f43c5d7
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 2%

---

# DNS 설정 구성 {#configure-dns}

사용자 지정 도메인 이름이 확인되고 배포되면 사용자 지정 도메인 이름에 대한 DNS 레코드를 DNS 공급자로 업데이트할 준비가 되었습니다. 이렇게 하면 사이트에서 방문자를 제공할 수 있습니다. 따라서 이 활동은 일반적으로 라이브로 전환되기 전에 수행됩니다.

## DNS 설정이란 무엇입니까? {#dns-settings}

A `CNAME` 또는 레코드가 제공되면 도메인에 대한 모든 인터넷 트래픽이 가리킬 때마다 라우팅됩니다. 해당 위치에 트래픽을 제공하도록 프로비저닝되지 않으면 중단이 발생합니다. 테스트하지 않은 경우 콘텐츠에 오류가 있을 수 있습니다. 테스트가 완료되고 라이브로 전환할 준비가 되면 이 단계가 항상 수행되는 이유입니다.

이러한 설정을 구성하려면 `CNAME` 또는 Apex 레코드를 구성하여 사용자 지정 도메인 이름을 Cloud Manager 도메인 이름으로 지정해야 합니다. 다음 섹션에서는 DNS 구성에 적합한 레코드 유형을 결정하는 데 도움이 됩니다.

>[!NOTE]
>
>본인 또는 조직의 해당 개인은 DNS 공급자(도메인을 구입한 회사)에 로그인하거나 문의하고 DNS 설정을 업데이트할 수 있어야 합니다.

## CNAME 레코드 {#cname-record}

정식 이름 또는 CNAME 레코드는 별칭 이름을 true 또는 정식 도메인 이름에 매핑하는 DNS 레코드 유형입니다. CNAME 레코드는 일반적으로 다음과 같은 하위 도메인을 매핑하는 데 사용됩니다 `www.example.com` 해당 하위 도메인의 컨텐츠를 호스팅하는 도메인에 속해 있어야 합니다.

도메인 등록기관에 로그인하고 `CNAME` 다음 표와 같이 사용자 지정 도메인 이름을 대상에 가리키도록 기록합니다.

| CNAME | Target 지정 도메인 이름 지점 |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## 에이펙스 레코드 {#apex-record}

apex 도메인은 하위 도메인이 포함되지 않은 사용자 지정 도메인입니다(예: ) `example.com`. 에이펙스 도메인은 `A` , `ALIAS` , 또는 `ANAME` DNS 공급자를 통해 기록합니다. Apex 도메인은 특정 IP 주소를 가리켜야 합니다.

다음을 모두 추가합니다 `A` 은 도메인 공급자를 통해 도메인의 DNS 설정에 기록됩니다.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
