---
title: TXT 레코드 추가
description: Cloud Manager에서 사용할 사용자 정의 도메인의 소유권을 확인하기 위해 TXT 레코드를 추가하는 방법을 알아봅니다.
exl-id: d441de29-af41-4d3e-9155-531af9702841
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 28%

---


# TXT 레코드 추가 {#adding-txt}

Cloud Manager에서 사용할 사용자 정의 도메인의 소유권을 확인하기 위해 TXT 레코드를 추가하는 방법을 알아봅니다.

## TXT 레코드란 무엇입니까? {#what-is}

텍스트 레코드(TXT 레코드라고도 함)는 DNS(Domain Name System)에 있는 리소스 레코드 유형입니다. 임의의 텍스트를 서버 또는 네트워크 정보와 같은 호스트 이름에 대해 사람이 읽을 수 있는 정보와 같은 호스트 이름과 연결할 수 있는 기능을 제공합니다.

Cloud Manager은 특정 TXT 레코드를 사용하여 CDN 서비스에서 호스팅할 도메인을 승인합니다. Cloud Manager이 사용자 정의 도메인과 함께 CDN 서비스를 배포하고 이를 백엔드 서비스와 연결하도록 권한을 부여한 영역에서 DNS TXT 레코드를 생성해야 합니다. 이 연결은 전적으로 사용자의 통제 하에 있으며 Cloud Manager가 서비스에서 도메인으로 콘텐츠를 제공하도록 인증합니다. 이 인증은 허가될 수도 있고 철회될 수도 있습니다. TXT 레코드는 도메인 및 Cloud Manager 환경에 따라 다릅니다.

## 요구 사항 {#requirements}

TXT 레코드를 추가하기 전에 이러한 요구 사항을 충족해야 합니다.

* 도메인 호스트 또는 등록자를 아직 모르는 경우 이를 확인해야 합니다.
* 조직의 도메인에 대한 DNS 레코드를 편집하거나 편집할 수 있는 적절한 담당자에게 문의할 수 있어야 합니다.
* [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 문서에 설명된 대로 먼저 사용자 지정 도메인 이름을 추가해야 합니다.

## 확인을 위해 TXT 레코드 추가 {#verification}

Cloud Manager에서 사용할 사용자 정의 도메인 이름 확인의 일부로 TXT 레코드가 추가됩니다.

1. [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 문서에 설명된 대로 먼저 사용자 지정 도메인 이름을 추가해야 합니다.

1. **도메인 이름 추가** 대화 상자의 **확인** 탭에서 Cloud Manager은 확인에 사용할 이름과 TXT 값을 표시합니다. 이 값을 복사합니다.

   ![도메인 이름 확인](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 찾습니다.

1. `_aemverification.[yourdomainname]`을(를) 값의 **이름**(으)로 추가하고 **도메인 이름 추가** 대화 상자에 표시되는 대로 TXT 값을 정확하게 추가합니다.

   * 다음 섹션의 [예제를 참조하십시오](#examples).

1. TXT 레코드를 도메인 호스트에 저장합니다.

## TXT 레코드 예 {#examples}

| 도메인 | 이름 | TXT 값 |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 이 값은 도메인 및 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Cloud Manager UI에 표시된 전체 값을 복사합니다. 이 값은 도메인 및 환경에 따라 다릅니다. 예:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

## TXT 레코드 확인 {#verify}

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
>Cloud Manager는 소유권을 확인하고 도메인 설정 표에 표시되는 상태를 업데이트합니다. 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.

## 다음 단계 {#next-steps}

이제 TXT 항목을 만들었으므로 도메인 이름 상태를 확인할 수 있습니다. 사용자 정의 도메인 이름을 계속 설정하려면 [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 문서로 진행하십시오.

>[!TIP]
>
>TXT 항목과 CNAME 또는 A 레코드를 관리 DNS 서버에서 동시에 설정할 수 있으므로 시간이 절약됩니다.
>
>이렇게 하려면 먼저 [사용자 정의 도메인 이름 소개](/help/implementing/cloud-manager/custom-domain-names/introduction.md) 문서에 설명된 대로 사용자 정의 도메인 이름을 설정하는 전체 프로세스를 검토하고 [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) 문서에 특별한 메모를 붙여 DNS 설정을 적절히 업데이트하십시오.