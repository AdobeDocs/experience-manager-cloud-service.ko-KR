---
title: 사용자 정의 도메인 이름 추가
description: Cloud Manager의 도메인 설정을 사용하여 사용자 정의 도메인 이름을 추가하는 방법에 대해 알아봅니다.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d6d34c2818ecb07c9d610844f6b868fe6a5918c6
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 15%

---


# 사용자 정의 도메인 이름 추가 {#adding-custom-domain-name}

Cloud Manager에서 **도메인 설정**&#x200B;을 사용하여 사용자 정의 도메인 이름을 추가하는 방법을 알아봅니다.

## 요구 사항 {#requirements}

Cloud Manager에서 사용자 정의 도메인 이름을 추가하기 전에 이러한 요구 사항을 충족하십시오.

* *SSL 인증서 추가* 문서에 설명된 대로 [사용자 정의 도메인 이름을 추가하기 전에](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)추가하려는 도메인에 대해 도메인 SSL 인증서를 추가해야 합니다.
* Cloud Manager에서 사용자 정의 도메인 이름을 추가하려면 **비즈니스 소유자** 또는 **배포 관리자** 역할이 있어야 합니다.
* Fastly 또는 기타 CDN(Content Delivery Network)을 사용합니다.

>[!IMPORTANT]
>
>Adobe 관리 CDN을 사용하는 경우에도 Cloud Manager에 도메인을 추가해야 합니다.

## 사용자 정의 도메인 이름을 추가할 위치 {#where-to-add-custom-domain-name}

Cloud Manager의 [도메인 설정 페이지](#adding-cdn-settings)에서 사용자 지정 도메인 이름을 추가할 수 있습니다.

사용자 정의 도메인 이름을 추가하면 도메인이 가장 구체적이고 유효한 인증서를 사용하여 제공됩니다. 여러 인증서에 동일한 도메인이 있으면 가장 최근에 업데이트된 이 선택됩니다. Adobe에서는 도메인이 겹치지 않도록 인증서를 관리하는 것이 좋습니다.

이 문서에 설명된 두 메서드의 단계는 Fastly를 기반으로 합니다. 다른 CDN(Content Delivery Network)을 사용한 경우 사용하기로 선택한 CDN으로 도메인을 구성합니다.

## 사용자 정의 도메인 이름 추가 {#adding-custom-domain-name-settings}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 측면 메뉴의 **서비스**&#x200B;에서 ![설정 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **도메인 설정**&#x200B;을 클릭합니다.

   ![도메인 설정 창](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)으로 이동합니다.

1. **도메인 설정** 페이지의 오른쪽 상단 모서리에서 **도메인 추가**&#x200B;를 클릭합니다.

1. **도메인 추가** 대화 상자의 **도메인 이름** 필드에 사용 중인 사용자 지정 도메인 이름을 입력합니다.
도메인 이름을 입력할 때 `http://`, `https://` 또는 공백을 포함하지 마십시오.

   >[!NOTE]
   >
   >`www` 및 `non-www` 버전의 도메인이 모두 필요한 경우 별도로 추가해야 합니다. 예: `example.com` 및 `www.example.com`.
   <!-- Marius Petria on SLACK tmp-skyline-cdn-certificates - Actually  my opinion is that this option should be explicit in UI (that was present in the initial mocks of the design but for some reason it was dropped). I think when adding a domain there should be a check mark to also add www.domain. When adding example.com Customer should be prompted with the following options: Do you also want to add www.example.com and have a redirect example.com -> www.example.com?Do you also want to add www.example.com and have a redirect www.example.com -> example.com? -->

1. **만들기**&#x200B;를 클릭합니다.

1. **도메인 확인** 대화 상자의 **이 도메인에 사용할 인증서 종류를 선택하십시오.** 드롭다운 목록에서 다음 옵션 중 하나를 선택하십시오.

   | 인증서 유형 옵션 | 설명 |
   | --- | --- |
   | Adobe 관리(DV) SSL 인증서 | DV(도메인 유효성 검사) 인증서를 사용하려면 이 인증서 유형을 선택합니다. 이 옵션은 기본 도메인 유효성 검사를 제공하는 대부분의 경우에 이상적입니다. Adobe은 인증서를 자동으로 관리하고 갱신합니다. |
   | 고객 관리(OV/EV) SSL 인증서 | EV/OV SSL 인증서를 사용하여 도메인을 보호하려면 이 인증서 유형을 선택합니다. 이 옵션은 OV(조직 유효성 검사) 또는 EV(확장 유효성 검사)를 통해 향상된 보안을 제공합니다. 더 엄격한 인증, 더 높은 신뢰 수준 또는 인증서에 대한 사용자 지정 제어가 필요한 경우 사용합니다. |

1. **도메인 확인** 대화 상자에서 선택한 인증서 유형에 따라 다음 중 하나를 수행합니다.

   | 인증서 유형을 선택한 경우 | 설명 |
   | --- | ---  |
   | Adobe 관리 인증서 | a. 아래의 [Adobe 관리 인증서 단계](#adobe-managed-cert-steps)를 완료합니다. 단계를 완료하면 **도메인 확인** 대화 상자에서 **확인**&#x200B;을 클릭합니다.<ul><li>DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.</li><li>Cloud Manager은 결국 도메인 이름 소유권을 확인하고 **도메인 설정** 테이블의 상태를 업데이트합니다. 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.</li>![도메인 상태 확인](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. 이제 [DV(Adobe 관리) SSL 인증서를 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert)할 준비가 되었습니다.</li></ul> |
   | 고객 관리 인증서 | a. **확인**&#x200B;을 클릭합니다.<br>b. 이제 [고객 관리(OV/EV) SSL 인증서를 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert)할 준비가 되었습니다.<br>인증서를 추가한 후 도메인 이름이 **도메인 설정** 표에 확인된 것으로 표시됩니다. 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.</li></ul><br>![고객 관리 EV/OV 인증서에 대한 도메인 확인](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |

   >[!NOTE]
   >
   >자체 고객 관리(OV/EV 또는 DV) SSL 인증서를 사용하는 경우 SSL 인증서를 추가할 필요가 없습니다. 이 규칙은 고객 관리 CDN(Content Delivery Network) ***provider***&#x200B;을(를) 사용하려는 경우에도 적용됩니다. 대신 준비가 되면 바로 [도메인 매핑 추가](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md)(으)로 이동합니다.


### Adobe 관리 인증서 단계 {#adobe-managed-cert-steps}

인증서 유형 *Adobe 관리 인증서*&#x200B;를 선택한 경우 **도메인 확인** 대화 상자에서 다음 단계를 완료하십시오.

![Adobe 관리 인증서 단계](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

사용 중인 도메인을 확인하려면 CNAME을 추가하고 확인해야 합니다.

`CNAME` 레코드 형식 또는 `A` 레코드 형식이 프로비저닝되면 도메인의 모든 인터넷 트래픽이 지정된 위치로 라우팅됩니다. 해당 위치에서 트래픽을 처리할 수 있도록 프로비저닝되지 않은 경우, 중단이 발생합니다. 테스트를 거치지 않은 경우 콘텐츠에 오류가 발생할 수 있습니다. 이러한 이유로 이 단계는 항상 테스트가 완료되고 실행 준비가 된 후에 수행됩니다.

이러한 설정을 구성하려면 사용자 정의 도메인 이름이 Cloud Manager 도메인 이름을 가리키도록 `CNAME` 또는 apex 레코드를 구성해야 하는지 여부를 결정하십시오. 이 문서의 다음 섹션에서는 DNS 구성에 적합한 레코드 유형을 결정하는 데 도움이 됩니다.

>[!NOTE]
>
>Adobe 관리 CDN의 경우 DV(도메인 유효성 검사) 인증서를 사용할 때는 ACME 유효성 검사가 있는 사이트만 허용됩니다.


### DNS 구성{#config-dns}

>[!WARNING]
>
>&quot;광고하기 전에 등록&quot; 원칙은 여기에 적용됩니다. 즉, 도메인 매핑을 성공적으로 추가한 *after*&#x200B;에만 DNS 구성을 수행해야 합니다. 이렇게 하면 Cloud Manager이 자체 구성에 도메인이 있는지 확인하고 인식한 후에 요청에 응답할 수 있습니다. 또한 모든 도메인 인계 시도를 방지합니다.

DNS 레코드를 구성하기 전에 *다음 요구 사항을 충족해야 합니다*.

* 도메인 호스트 또는 등록자를 아직 모르는 경우 이를 확인합니다.
* 조직의 도메인에 대한 DNS 레코드를 편집하거나, 편집할 수 있는 적절한 담당자에게 문의할 수 있습니다.
* [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 문서에 설명된 대로 구성된 사용자 정의 도메인 이름을 이미 확인했습니다.

#### CNAME 레코드 {#adobe-managed-cert-cname-record}

정식 이름 또는 CNAME 레코드는 별칭 이름을 실제 또는 정식 도메인 이름에 매핑하는 DNS 레코드 유형입니다. CNAME 레코드는 일반적으로 `www.example.com`과 같은 하위 도메인을 해당 하위 도메인의 콘텐츠를 호스팅하는 도메인에 매핑하는 데 사용됩니다.

DNS 서비스 공급자에 로그인하고 다음 표와 같이 사용자 지정 도메인 이름이 대상을 가리키도록 `CNAME` 레코드를 만듭니다.

| CNAME | 사용자 정의 도메인 담이 타겟을 가리킴 |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

#### APEX 레코드 {#adobe-managed-cert-apex-record}

Apex 도메인은 `example.com`과 같은 하위 도메인을 포함하지 않는 사용자 정의 도메인입니다. DNS 공급자를 통해 Apex 도메인이 `A`, `ALIAS` 또는 `ANAME` 레코드로 구성되어 있습니다. Apex 도메인은 특정 IP 주소를 가리켜야 합니다.

도메인 공급자를 통해 도메인의 DNS 설정에 다음 `A` 레코드를 추가합니다.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

>[!TIP]
>
>*CNAME 레코드* 또는 *A 레코드*&#x200B;을(를) 관리 DNS 서버에서 설정하여 시간을 절약할 수 있습니다.

<!--
![Customer managed certificate steps](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

To verify the domain in use, you are required to add and verify a TXT record.

A text record (also known as a TXT record) is a type of resource record in the Domain Name System (DNS). It lets you associate arbitrary text with a hostname. This text could include human-readable details like server or network information.

Cloud Manager uses a specific TXT record to authorize a domain to be hosted in a CDN service. Create a DNS TXT record in the zone that authorizes Cloud Manager to deploy the CDN service with the custom domain and associate it with the backend service. This association is entirely under your control and authorizes Cloud Manager to serve content from the service to a domain. This authorization may be granted and withdrawn. The TXT record is specific to the domain and the Cloud Manager environment.

#### Requirements {#customer-managed-cert-requirements}

Fulfill these requirements before adding a TXT record.

* Identify your domain host or registrar if you do not know it already.
* Be able to edit the DNS records for your organization's domain, or contact the appropriate person who can.
* First, add a custom domain name as described earlier in this article.

#### Add a TXT record for verification {#customer-managed-cert-verification}

1. In the **Verify domain** dialog box, Cloud Manager displays the name and TXT value to use for verification. Copy this value.

1. Log in to your DNS service provider and find the DNS records section. 

1. Add `aemverification.[yourdomainname]` as the **Name** of the value and add the TXT value exactly as it appears in the **Domain Name** field.

   **TXT record examples**

   | Domain | Name | TXT Value |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Save the TXT record to your domain host.

#### Verify TXT record {#customer-managed-cert-verify}

When you are done, you can verify the result by running the following command.

```shell
dig _aemverification.[yourdomainname] -t txt
```

The expected result should display the TXT value provided on the **Verification** tab of the **Add Domain Name** dialog of the Cloud Manager UI.

For example, if your domain is `example.com`, then run:

```shell
dig TXT _aemverification.example.com -t txt
```


>[!TIP]
>
>There are several [DNS lookup tools](https://www.ultratools.com/tools/dnsLookup) available. Google DoH can be used to look up TXT record entries and identify if the TXT record is missing or erroneous.

-->



<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->


><!-- The TXT entry and the CNAME or A Record can be set simultaneously on the governing DNS server, thus saving time. -->
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


