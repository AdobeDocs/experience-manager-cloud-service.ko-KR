---
title: AEM as a Cloud Service에서 CDN
description: AEM as a Cloud Service에서 CDN
translation-type: tm+mt
source-git-commit: 40119f7b3bdf36af668b79afbcb2802a0b2a6033
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 7%

---


# AEM as a Cloud Service에서 CDN {#cdn}

AEM as Cloud Service은 내장된 CDN과 함께 출하됩니다. 주 목적은 브라우저 근처의 가장자리에 있는 CDN 노드에서 캐쉬가능 컨텐츠를 전달하여 지연을 줄이는 것입니다. AEM 애플리케이션 최적의 성능을 위해 완벽하게 관리 및 구성됩니다.

AEM 관리 CDN은 대부분의 고객의 성능 및 보안 요구 사항을 만족시킵니다. 게시 계층의 경우, 고객은 선택적으로 관리해야 하는 자체 CDN에서 해당 CDN을 가리킬 수 있습니다. 이것은 포기하기 어려운 기존 CDN 공급업체와의 통합을 비롯하여, 이에 국한되지 않고, 특정 사전 요구 사항을 충족하는 것을 기준으로, 사례별로 허용됩니다.

## AEM 관리 CDN {#aem-managed-cdn}

아래의 섹션에 따라 Cloud Manager 셀프 서비스 UI를 사용하여 Adobe의 기본 CDN을 사용하여 컨텐츠 전달을 준비하십시오.

1. [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**트래픽 제한**

기본적으로 Adobe 관리 CDN 설정의 경우 모든 공용 트래픽은 프로덕션 및 비프로덕션(개발 및 스테이지) 환경 모두에 대해 게시 서비스로 갈 수 있습니다. 지정된 환경에 대한 게시 서비스로 트래픽을 제한하려는 경우(예: IP 주소 범위로 스테이징을 제한하는 경우) Cloud Manager UI를 통해 셀프 서비스 방식으로 이 작업을 수행할 수 있습니다.

자세한 내용은 [IP 허용 목록 관리](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)를 참조하십시오.

## 고객 CDN은 AEM Managed CDN {#point-to-point-CDN}을 가리킵니다.

고객은 기존 CDN을 사용해야 하는 경우, 다음을 충족한 경우 이를 관리하고 Adobe의 관리 CDN을 가리킬 수 있습니다.

* 고객은 교체해야 하는 기존 CDN이 있어야 합니다.
* 고객은 이를 관리해야 합니다.
* 고객은 AEM에서 Cloud Service으로 작동하도록 CDN을 구성할 수 있어야 합니다. 아래 구성 지침을 참조하십시오.
* 고객은 관련 문제가 발생할 경우 호출되는 엔지니어링 CDN 전문가가 있어야 합니다.
* 고객은 프로덕션으로 이동하기 전에 로드 테스트를 성공적으로 수행하고 통과해야 합니다.

구성 지침:

1. 도메인 이름으로 `X-Forwarded-Host` 헤더를 설정합니다.
1. Adobe의 CDN의 수신인 원본 도메인에 호스트 헤더를 설정합니다. 값은 Adobe에서 와야 합니다.
1. SNI 헤더를 원본으로 보냅니다. 호스트 헤더와 마찬가지로 sni 헤더는 원본 도메인이어야 합니다.
1. 트래픽을 AEM 서버로 올바르게 라우팅하는 데 필요한 `X-Edge-Key`을 설정합니다. 값은 Adobe에서 와야 합니다.

라이브 트래픽을 수락하기 전에 엔드 투 엔드 트래픽 라우팅이 올바르게 작동하는지 Adobe 고객 지원으로 확인해야 합니다.

고객 CDN에서 Adobe의 관리 CDN으로의 홉이 효율적일 수 있지만, 추가적인 홉으로 인한 작은 성능 히트가 있을 수 있습니다.

이 고객 CDN 구성은 게시 계층에 대해 지원되지만 작성자 계층 앞에는 지원되지 않습니다.
