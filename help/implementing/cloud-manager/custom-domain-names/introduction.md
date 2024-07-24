---
title: 사용자 정의 도메인 이름 소개
description: Cloud Manager의 UI를 사용하면 사용자 정의 도메인을 추가하여 셀프서비스 방식을 사용하여 사이트를 고유한 브랜드 이름으로 식별할 수 있습니다.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1c9924b4477d53d86bb72eda8597a02304450195
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 65%

---


# 사용자 정의 도메인 이름 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="사용자 정의 도메인 이름 관리"
>abstract="Cloud Manager의 UI를 사용하면 사용자 정의 도메인을 추가하여 셀프서비스 방식을 사용하여 사이트를 고유한 브랜드 이름으로 식별할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="사용자 정의 도메인 이름 추가"
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="사용자 정의 도메인 이름 보기 및 업데이트"

Adobe Experience Manager as a Cloud Service는 `*.adobeaemcloud.com`으로 끝나는 기본 도메인 이름으로 프로비저닝됩니다. Cloud Manager의 UI를 사용하여 사용자 정의 도메인을 추가하여 셀프서비스 방식으로 사이트를 고유한 브랜드 이름으로 식별할 수 있습니다. 사용자 지정 도메인 이름을 웹 사이트에 연결한 후에도 기본 `*.adobeaemcloud.com` 도메인 이름이 유지됩니다.

## 사용자 정의 도메인 이름이란? {#what-are-custom-domain-names}

각 웹 사이트에는 `184.33.123.64`와 같이 기계가 읽을 수 있는 고유한 숫자 주소가 연결되어 있습니다. DNS(도메인 이름 시스템)를 사용하면 숫자 주소를 `wknd.com`과 같은 기억할 수 있는 주소로 변환하여 웹 사이트에 사용자 정의 브랜드 도메인을 연결할 수 있습니다.

고객의 기억에 남고 브랜드를 잘 나타내는 도메인 이름을 사이트에 사용하는 것이 좋습니다.

도메인 이름 등록자, 도메인 이름을 관리 및 판매하는 회사 또는 조직에서 도메인 이름을 구입할 수 있습니다. 도메인 이름 등록자는 DNS 서버의 도메인 이름을 관리합니다.

>[!IMPORTANT]
>
>Cloud Manager는 도메인 이름 등록자가 아니므로 DNS 서비스를 제공하지 않습니다.

## 사용자 정의 도메인 이름 및 BYO CDN {#byo-cdn}

AEM as a Cloud Service는 내장된 콘텐츠 게재 네트워크(CDN) 서비스를 제공하지만 BYO(Bring-Your-Own) CDN 방식에 따라 AEM과 함께 사용할 수 있습니다. 사용자 정의 도메인은 AEM 관리 CDN 또는 자체 관리 CDN에 설치할 수 있습니다.

* AEM 관리 CDN에 설치된 사용자 정의 도메인의 이름(및 인증서)은 Cloud Manager를 통해 관리됩니다.
* 자체 CDN에 설치된 사용자 정의 도메인의 이름(및 인증서)은 해당 특정 CDN을 통해 관리됩니다.

자체 CDN에서 관리되는 **도메인은 Cloud Manager을 통해 설치할 필요가 없습니다.** X-Forwarded-Host를 통해 AEM에서 사용할 수 있으며 Dispatcher에 정의된 vhost와 일치합니다. [CDN 설명서를 참조하십시오.](/help/implementing/dispatcher/cdn.md)

하나의 환경에서 두 도메인을 AEM 관리 CDN과 자체 CDN에 설치할 수 있습니다.

## 워크플로 {#workflow}

사용자 정의 도메인 이름을 추가하려면 DNS 서비스와 Cloud Manager 간의 상호 작용이 필요합니다. 따라서 사용자 정의 도메인 이름을 설치, 구성 및 확인하는 데 몇 가지 단계가 필요합니다. 다음 표는 이러한 단계를 완료하는 데 필요한 설명서 리소스에 대한 링크를 포함하여 필요한 단계에 대한 개요를 제공합니다.

| 단계 | 설명 | 설명서 |
|---|---|---|
| 1 | Cloud Manager에 SSL 인증서 추가 | [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | Cloud Manager에 사용자 정의 도메인 추가 | [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | TXT 레코드를 추가하여 도메인 확인 | [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 4 | 도메인 확인 상태 검토 | [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 5 | AEM as a Cloud Service를 가리키는 DNS CNAME 또는 APEX 레코드를 추가하여 DNS 설정 구성 | [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 6 | DNS 레코드 상태 확인 | [DNS 레코드 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>AEM as a Cloud Service를 사용하여 사용자 정의 도메인 이름을 설정하는 것은 일반적으로 간단한 프로세스입니다. 그러나 경우에 따라 도메인 위임 문제가 발생할 수 있으며 해결하는 데 영업일 기준 1~2일이 소요될 수 있습니다. 이러한 이유로 Go-Live 날짜 이전에 도메인을 설치하는 것이 좋습니다. 자세한 내용은 [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 문서를 참조하십시오.

## 제한 사항 {#limitations}

AEMaaCS에서 사용자 정의 도메인 이름을 사용하는 데에는 몇 가지 제한 사항이 있습니다.

* 사용자 정의 도메인 이름은 Cloud Manager에서 Sites 프로그램의 게시 및 미리보기 서비스에 대해서만 지원됩니다.
   * 작성자 서비스를 위한 사용자 정의 도메인은 지원되지 않습니다.
* 각 Cloud Manager 환경은 환경당 최대 500개의 사용자 정의 도메인을 호스팅할 수 있습니다.
* 현재 실행 중인 파이프라인이 해당 환경에 연결되어 있는 동안에는 환경에 도메인 이름을 추가할 수 없습니다.
* 동일한 도메인 이름을 둘 이상의 환경에서 사용할 수 없습니다.
* 한 번에 하나의 도메인 이름만 추가할 수 있습니다.
* AEM as a Cloud Service는 `*.example.com`와 같은 와일드카드 도메인을 지원하지 않습니다.
* 사용자 정의 도메인 이름을 추가하기 전에 사용자 정의 도메인 이름(와일드카드 인증서가 유효함)이 포함된 유효한 SSL 인증서가 프로그램에 설치되어 있어야 합니다.

## 시작! {#get-started}

* [SSL 인증서를 추가하여 프로젝트에 대한 새 사용자 정의 도메인 이름 구성을 시작하십시오.](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [사용자 정의 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) 문서를 검토하여 기존 도메인 이름을 관리합니다.
