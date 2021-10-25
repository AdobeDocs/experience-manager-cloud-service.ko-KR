---
title: 'DNS 설정 구성 '
description: DNS 설정 구성
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: 0b24f8c8b88f476a0d1073e873e46441b1b8b821
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# DNS 설정 구성 {#configure-dns}

사용자 지정 도메인 이름이 확인되고 배포되면 사용자 지정 도메인 이름에 대한 DNS 레코드를 DNS 공급자로 업데이트할 준비가 되었습니다. 이렇게 하면 사이트에서 방문자를 제공할 수 있습니다. 따라서 이 활동은 일반적으로 Go-live 전에 수행됩니다.

>[!NOTE]
>본인 또는 조직의 해당 개인은 DNS 공급자(도메인을 구매한 회사)에 로그인하거나 문의하고 DNS 설정을 업데이트할 수 있어야 합니다.

이렇게 하려면 DNS 설정을 `CNAME` 또는 Apex 레코드가 사용자 지정 도메인 이름을 Cloud Manager 도메인 이름으로 가리킵니다. A `CNAME` 또는 레코드가 제공되면 도메인에 대한 모든 인터넷 트래픽이 가리킬 때마다 라우팅됩니다. 해당 위치에 트래픽을 제공하도록 프로비저닝되지 않으면 중단이 발생합니다. 테스트하지 않은 경우 콘텐츠에 오류가 있을 수 있습니다. 테스트가 완료되고 고객이 Go-live를 준비 한 후 이 단계를 항상 수행하는 이유입니다.

아래 표에 표시된 대로 다음 단계를 완료해야 합니다.

| 단계 |  | 책임 | 추가 정보 |
|--- |--- |--- |---|
| SLL 인증서 추가 | SLL 인증서 추가 | 고객 | [SSL 인증서 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) |
| 도메인 확인 | TXT 레코드 추가 | 고객 | [TXT 레코드 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-text-record.html?lang=en) |
| 도메인 확인 상태 검토 |  | 고객 |  |
|  | 상태: 도메인 확인 실패 | 고객 | [도메인 이름 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
|  | 상태: 확인됨, 배포 실패 | Adobe 담당자에게 문의하십시오 | [도메인 이름 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
| CNAME 또는 APEX 레코드를 추가하여 AEM as a Cloud Service을 가리키는 DNS 레코드를 추가합니다 | DNS 설정 구성 | 고객 | [DNS 설정 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/configure-dns-settings.html?lang=en) |
| DNS 레코드 상태 확인 |  | 고객 | [DNS 레코드 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | 상태: DNS 상태가 검색되지 않음 | 고객 | [DNS 레코드 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | 상태: DNS가 잘못 확인됨 | 고객 |  |


## CNAME 레코드 {#cname-record}

다음 섹션에서는 DNS 구성에 적합한 레코드 유형을 결정하는 데 도움이 됩니다.

정식 이름 또는 `CNAME` 레코드는 별칭 이름을 true 또는 정식 도메인 이름에 매핑하는 DNS 레코드 유형입니다. CNAME 레코드는 일반적으로 다음과 같은 하위 도메인을 매핑하는 데 사용됩니다 `www.example.com`  해당 하위 도메인의 컨텐츠를 호스팅하는 도메인에 속해 있어야 합니다.

아래 표시된 대로 도메인 등록기관에 로그인하고 CNAME 레코드를 만들어 사용자 지정 도메인 이름을 대상에 지정합니다.

| CNAME | Target 지정 도메인 이름 지점 |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## 에이펙스 레코드 {#apex-record}

apex 도메인은 example.com과 같은 하위 도메인을 포함하지 않는 사용자 지정 도메인입니다. 에이펙스 도메인은 `A` , `ALIAS` , 또는 `ANAME` DNS 공급자를 통해 기록합니다. Apex 도메인은 특정 IP 주소를 가리켜야 합니다.

도메인 공급자를 통해 도메인의 DNS 설정에 다음 모든 A 레코드를 추가합니다.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
