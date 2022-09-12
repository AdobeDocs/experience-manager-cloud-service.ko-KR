---
title: 사용자 지정 도메인 이름 소개
description: Cloud Manager의 UI를 사용하면 사용자 지정 도메인을 추가하여 셀프 서비스 방식으로 고유한 브랜드 이름으로 사이트를 식별할 수 있습니다.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: cc1b0d653706150c616ceafd002dc7594b6c7072
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 9%

---


# 사용자 지정 도메인 이름 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="사용자 지정 도메인 이름 관리"
>abstract="Cloud Manager의 UI를 사용하면 사용자 지정 도메인을 추가하여 셀프 서비스 방식으로 고유한 브랜드 이름으로 사이트를 식별할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html" text="맞춤형 도메인 이름 추가"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.html" text="사용자 지정 도메인 이름 보기 및 업데이트"

Cloud Manager의 UI를 사용하면 사용자 지정 도메인을 추가하여 셀프 서비스 방식으로 고유한 브랜드 이름으로 사이트를 식별할 수 있습니다. Adobe Experience Manager as a Cloud Service에 기본 도메인 이름이 제공되어 `*.adobeaemcloud.com`. 이 기본 도메인 이름은 사용자 지정 도메인 이름을 웹 사이트에 연결한 후에도 계속 유지됩니다.

## 사용자 지정 도메인 이름은 무엇입니까? {#what-are-custom-domain-names}

각 웹 사이트에는 다음과 같이 시스템과 읽을 수 있는 고유한 숫자 주소가 있습니다 `184.33.123.64`. DNS(Domain Name System)는 숫자 주소를 기억하기 쉬운 주소로 변환하여 웹 사이트에 맞춤형 브랜드 도메인을 연결할 수 있도록 하는 것입니다 `wknd.com`.

고객에게 기억에 남고 브랜드를 반영하는 사이트용 도메인 이름을 갖는 것이 좋습니다.

도메인 이름 등록 기관, 도메인 이름을 관리 및 판매하는 회사 또는 조직에서 도메인 이름을 구입할 수 있습니다. 도메인 이름 등록자는 DNS 서버의 도메인 이름을 관리합니다.

>[!IMPORTANT]
>
>Cloud Manager는 도메인 이름 등록자가 아니며 DNS 서비스를 제공하지 않습니다.

## 제한 사항 {#limitations}

AEMaaCS에서 사용자 지정 도메인 이름을 사용하는 데에는 많은 제한 사항이 있습니다.

* 사용자 지정 도메인 이름은 Cloud Manager에서 Sites 프로그램에 대한 게시 및 미리 보기 서비스를 모두 지원합니다. 작성자 측의 사용자 지정 도메인은 지원되지 않습니다.
* 각 Cloud Manager 환경은 환경당 최대 500개의 사용자 지정 도메인을 호스팅할 수 있습니다.
* AEM as a Cloud Service은 와일드카드 도메인을 지원하지 않습니다.
* 사용자 지정 도메인 이름을 추가하기 전에 사용자 지정 도메인 이름이 포함된 유효한 SSL 인증서를 프로그램에 설치해야 합니다. 자세한 내용은 SSL 인증서 추가 를 참조하십시오.
* 해당 환경에 연결된 현재 실행 중인 파이프라인이 있는 동안에는 도메인 이름을 환경에 추가할 수 없습니다.
* 한 번에 하나의 도메인 이름만 추가할 수 있습니다.
* 두 개 이상의 환경에서 동일한 도메인 이름을 사용할 수 없습니다.

## 워크플로 {#workflow}

사용자 지정 도메인 이름을 추가하려면 DNS 서비스와 Cloud Manager 간의 상호 작용이 필요합니다. 따라서 사용자 지정 도메인 이름을 설치, 구성 및 확인하는 데 필요한 단계가 많습니다. 다음 표에서는 일반적인 오류가 발생할 때 수행할 작업을 포함하여 필요한 단계에 대한 개요를 제공합니다.

| 단계 | 설명 | 책임 | 추가 정보 |
|--- |--- |--- |---|
| 1 | Cloud Manager에 SLL 인증서 추가 | 고객 | [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | TXT 레코드를 추가하여 도메인 확인 | 고객 | [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 3 | 도메인 확인 상태 검토 | 고객 | [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3a | 도메인 확인이 실패하고 상태가 표시됩니다. `Domain Verification Failure` | 고객 | [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3b | 도메인 확인이 실패하고 상태가 표시됩니다. `Verified, Deployment Failed`, 연락처 Adobe | 고객 지원 Adobe | [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 4 | AEM as a Cloud Service을 가리키는 DNS CNAME 또는 APEX 레코드를 추가하여 DNS 설정을 구성합니다 | 고객 | [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 5 | DNS 레코드 상태 확인 | 고객 | [DNS 레코드 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5a | DNS 레코드 상태가 `DNS status not detected` | 고객 | [DNS 레코드 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5b | DNS 레코드 상태가 `DNS resolves incorrectly` | 고객 | [DNS 레코드 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
