---
title: 도메인 확인
description: 도메인 확인
source-git-commit: d2a98cf340dc755407250a9a9649addb75ad87d2
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# 도메인 {#verify-domain-name} 확인 중

DNS TXT 레코드는 CDN 서비스에서 호스팅될 도메인을 허용합니다. 고객은 Cloud Manager가 사용자 지정 도메인과 CDN 서비스를 배포하고 이를 백엔드 서비스에 연결할 수 있도록 하는 영역에 DNS TXT 레코드를 만들어야 합니다. 이 연관성은 전적으로 고객의 제어하에 있으며 Cloud Manager가 서비스에서 도메인으로 컨텐츠를 제공할 수 있도록 강력하게 허용합니다. 그 승인은 취소될 수도 있다. TXT 레코드는 도메인 및 Cloud Manager 환경에 따라 다릅니다.

1. 도메인 호스트에 로그인하고 DNS 레코드 섹션을 참조하십시오.
1. TXT 항목을 복사하여 사용자 정의 도메인이 있는 DNS 영역에 붙여넣습니다. 항목에 &quot;name&quot;이 필요한 경우 `@`을 지정합니다.

>[!NOTE]
>[DNS 조회 도구](https://www.ultratools.com/tools/dnsLookup)와 같은 다양한 DNS 조회 도구, Google DoH를 사용하여 TXT 레코드 항목을 조회하고 TXT 레코드가 누락되었는지 확인할 수 있습니다.
