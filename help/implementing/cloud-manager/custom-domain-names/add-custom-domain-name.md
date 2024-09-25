---
title: 사용자 정의 도메인 이름 추가
description: Cloud Manager의 도메인 설정을 사용하여 사용자 정의 도메인 이름을 추가하는 방법에 대해 알아봅니다.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b9fb178760b74cb0e101506b6a9ff5ae30c18490
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 18%

---


# 사용자 정의 도메인 이름 추가 {#adding-cdn}

Cloud Manager에서 **도메인 설정**&#x200B;을 사용하여 사용자 정의 도메인 이름을 추가하는 방법을 알아봅니다.

## 요구 사항 {#requirements}

Cloud Manager에서 사용자 정의 도메인 이름을 추가하기 전에 이러한 요구 사항을 충족하십시오.

* [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) 문서에 설명된 대로 사용자 정의 도메인 이름을 추가하기 전에 추가할 도메인에 대한 도메인 SSL 인증서를 추가해야 합니다.
* Cloud Manager에서 사용자 정의 도메인 이름을 추가하려면 **비즈니스 소유자** 또는 **배포 관리자** 역할이 있어야 합니다.
* Fastly 또는 기타 CDN(Content Delivery Network)을 사용하고 있습니다.

>[!IMPORTANT]
>
>비 Adobe CDN을 사용하는 경우에도 도메인을 Cloud Manager에 추가해야 합니다.

## 사용자 정의 도메인 이름을 추가할 위치 {#where-to-add-cdn}

Cloud Manager의 다음 두 위치에서 사용자 정의 도메인 이름을 추가할 수 있습니다.

* [도메인 설정 페이지](#adding-cdn-settings)
* [환경 페이지](#adding-cdn-environments)

사용자 정의 도메인 이름을 추가하면 도메인이 가장 구체적이고 유효한 인증서를 사용하여 제공됩니다. 여러 인증서에 동일한 도메인이 있으면 가장 최근에 업데이트된 이 선택됩니다. Adobe은 도메인이 겹치지 않도록 인증서를 관리할 것을 권장합니다.

이 문서에 설명된 두 메서드의 단계는 Fastly를 기반으로 합니다. 다른 CDN(Content Delivery Network)을 사용한 경우 사용하기로 선택한 CDN으로 도메인을 구성합니다.

## 사용자 정의 도메인 이름 추가 {#adding-cdn-settings}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 측면 메뉴의 **서비스**&#x200B;에서 ![설정 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **도메인 설정**&#x200B;을 선택합니다.

   ![도메인 설정 창](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)으로 이동합니다.

1. **도메인 설정** 페이지의 오른쪽 상단 모서리에서 **도메인 추가**&#x200B;를 클릭합니다.

1. **도메인 추가** 대화 상자의 **도메인 이름** 필드에 사용 중인 사용자 지정 도메인 이름을 입력합니다.
도메인을 입력할 때 `http://`, `https://` 또는 공백을 포함하지 마십시오.

1. **만들기**&#x200B;를 클릭합니다.

1. **도메인 확인** 대화 상자의 **이 도메인에 사용할 인증서 종류를 선택하십시오.** 드롭다운 목록에서 다음 옵션 중 하나를 선택하십시오.

   | 인증서 유형 옵션 | 설명 |
   | --- | --- |
   | Adobe 관리 인증서 | DV(도메인 유효성 검사) 인증서를 사용하려면 이 인증서 유형을 선택합니다. 이 옵션은 기본 도메인 유효성 검사를 제공하는 대부분의 경우에 이상적입니다. Adobe이 자동으로 인증서를 관리하고 갱신합니다. |
   | 고객 관리 인증서 | EV/OV 인증서를 사용하려면 이 인증서 유형을 선택합니다. 이 옵션은 EV(확장 유효성 검사) 또는 OV(조직 유효성 검사)를 통해 향상된 보안을 제공합니다. 더 엄격한 인증, 더 높은 신뢰 수준 또는 인증서에 대한 사용자 지정 제어가 필요한 경우 사용합니다. |

1. **도메인 확인** 대화 상자에서 선택한 인증서 유형에 따라 다음 중 하나를 수행합니다.

   | 인증서 유형을 선택한 경우 | 설명 |
   | --- | ---  |
   | Adobe 관리 인증서 | 다음 단계를 계속하기 전에 [Adobe 관리 인증서 단계](#adobe-managed-cert-steps)를 완료하십시오. |
   | 고객 관리 인증서 | 다음 단계를 계속하기 전에 [고객 관리 인증서 단계](#customer-managed-cert-steps)를 완료하십시오. |

1. **확인**&#x200B;을 클릭합니다.

1. 이제 [SSL 인증서를 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)할 준비가 되었습니다.

   >[!NOTE]
   >
   >고객 관리 SSL 인증서 및 고객 관리 CDN 공급자를 사용하는 경우 SSL 인증서 추가를 건너뛰고 준비가 되면 바로 [CDN 구성 추가](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)(으)로 이동할 수 있습니다.


### Adobe 관리 인증서 단계 {#adobe-managed-cert-steps}

인증서 유형 *Adobe 관리 인증서*&#x200B;를 선택한 경우 **도메인 확인** 대화 상자에서 다음 단계를 완료하십시오.

![Adobe 관리 인증서 단계](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

사용 중인 도메인을 확인하려면 CNAME을 추가하고 확인해야 합니다.

`CNAME` 또는 A 레코드가 프로비저닝되면 도메인의 모든 인터넷 트래픽이 지정된 위치로 라우팅됩니다. 해당 위치에서 트래픽을 처리할 수 있도록 프로비저닝되지 않은 경우, 중단이 발생합니다. 테스트를 거치지 않은 경우 콘텐츠에 오류가 발생할 수 있습니다. 이러한 이유로 이 단계는 항상 테스트가 완료되고 실행 준비가 된 후에 수행됩니다.

이러한 설정을 구성하려면 사용자 정의 도메인 이름이 Cloud Manager 도메인 이름을 가리키도록 `CNAME` 또는 apex 레코드를 구성해야 하는지 여부를 결정하십시오. 이 문서의 다음 섹션에서는 DNS 구성에 적합한 레코드 유형을 결정하는 데 도움이 됩니다.

>[!NOTE]
>
>Adobe 관리 CDN의 경우 DV(도메인 유효성 검사) 인증서를 사용할 때는 ACME 유효성 검사가 있는 사이트만 허용됩니다.

#### 요구 사항 {#adobe-managed-cert-dv-requirements}

DNS 레코드를 구성하기 전에 이러한 요구 사항을 충족하십시오.

* 도메인 호스트 또는 등록자를 아직 모르는 경우 이를 확인합니다.
* 조직의 도메인에 대한 DNS 레코드를 편집하거나, 편집할 수 있는 적절한 담당자에게 문의할 수 있습니다.
* [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 문서에 설명된 대로 구성된 사용자 정의 도메인 이름을 이미 확인했어야 합니다.

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


### 고객 관리 인증서 단계 {#customer-managed-cert-steps}

인증서 유형 *고객 관리 인증서*&#x200B;를 선택한 경우 **도메인 확인** 대화 상자에서 다음 단계를 완료하십시오.

![고객 관리 인증서 단계](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

사용 중인 도메인을 확인하려면 TXT 레코드를 추가하고 확인해야 합니다.

텍스트 레코드(TXT 레코드라고도 함)는 DNS(Domain Name System)에 있는 리소스 레코드 유형입니다. 임의의 텍스트를 호스트 이름과 연결할 수 있습니다. 이 텍스트에는 서버 또는 네트워크 정보와 같이 사람이 읽을 수 있는 세부 정보가 포함될 수 있습니다.

Cloud Manager은 특정 TXT 레코드를 사용하여 CDN 서비스에서 호스팅할 도메인을 승인합니다. Cloud Manager에서 사용자 지정 도메인과 함께 CDN 서비스를 배포하고 이를 백엔드 서비스와 연결하도록 권한을 부여하는 영역에 DNS TXT 레코드를 만듭니다. 이 연결은 전적으로 사용자의 통제 하에 있으며 Cloud Manager가 서비스에서 도메인으로 콘텐츠를 제공하도록 인증합니다. 이 인증은 허가될 수도 있고 철회될 수도 있습니다. TXT 레코드는 도메인 및 Cloud Manager 환경에 따라 다릅니다.

#### 요구 사항 {#customer-managed-cert-requirements}

TXT 레코드를 추가하기 전에 이러한 요구 사항을 충족하십시오.

* 도메인 호스트 또는 등록자를 아직 모르는 경우 이를 확인합니다.
* 조직의 도메인에 대한 DNS 레코드를 편집하거나, 편집할 수 있는 적절한 담당자에게 문의할 수 있습니다.
* 먼저 이 문서의 앞부분에서 설명한 대로 사용자 정의 도메인 이름을 추가합니다.

#### 확인을 위해 TXT 레코드 추가 {#customer-managed-cert-verification}

1. **도메인 확인** 대화 상자에서 Cloud Manager은 확인에 사용할 이름과 TXT 값을 표시합니다. 이 값을 복사합니다.

1. DNS 서비스 공급자에 로그인하고 DNS 레코드 섹션을 찾습니다.

1. `aemverification.[yourdomainname]`을(를) 값의 **Name**(으)로 추가하고 **도메인 이름** 필드에 나타나는 대로 TXT 값을 정확하게 추가합니다.

   **TXT 레코드 예**

   | 도메인 | 이름 | TXT 값 |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 이 값은 도메인 및 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 이 값은 도메인 및 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. TXT 레코드를 도메인 호스트에 저장합니다.

#### TXT 레코드 확인 {#customer-managed-cert-verify}

작업이 완료되면 다음 명령을 실행하여 결과를 확인할 수 있습니다.

```shell
dig _aemverification.[yourdomainname] -t txt
```

예상 결과는 Cloud Manager UI의 **도메인 이름 추가** 대화 상자의 **확인** 탭에 제공된 TXT 값을 표시해야 합니다.

예를 들어 도메인이 `example.com`이면 다음을 실행합니다.

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>[DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup)를 사용할 수 있습니다. Google DoH를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었거나 오류가 있는지 식별할 수 있습니다.

>[!NOTE]
>
>DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.
>
>Cloud Manager은 소유권을 확인하고 도메인 설정 표에 표시되는 상태를 업데이트합니다. 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.

<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->

>[!TIP]
>
>TXT 항목과 CNAME 또는 A 레코드를 관리 DNS 서버에서 동시에 설정할 수 있으므로 시간이 절약됩니다.
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


## 환경 페이지에서 사용자 정의 도메인 이름 추가 {#adding-cdn-environments}

<!-- I DON'T SEE THIS ABILITY ANYMORE IN THE UI -->

**환경** 페이지에서 사용자 지정 도메인 이름을 추가하는 단계는 [도메인 설정 페이지에서 사용자 지정 도메인 이름을 추가](#adding-cdn-settings)하는 단계와 동일하지만 시작 지점이 다릅니다. **환경** 페이지에서 사용자 정의 도메인 이름을 추가하려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 관심 환경의 **환경 세부 정보** 세부 정보 페이지로 이동합니다.

   ![환경 세부 정보 페이지에 도메인 이름 입력](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. **도메인 이름** 표를 사용하여 사용자 정의 도메인 이름을 제출합니다.

   1. 사용자 정의 도메인 이름을 입력합니다.
   1. 드롭다운 목록에서 이 이름과 연결된 SSL 인증서를 선택합니다.
   1. ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **추가**&#x200B;를 클릭합니다.

   ![사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. **도메인 이름 추가** 대화 상자가 열리고 **도메인 이름** 탭이 표시됩니다. [도메인 설정 페이지에서 사용자 지정 도메인 이름을 추가](#adding-cdn-settings)하는 것처럼 계속합니다.
