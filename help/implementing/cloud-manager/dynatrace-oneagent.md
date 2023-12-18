---
title: Dynatrace OneAgent
description: Dynatrace의 OneAgent를 AEM과 함께 as a Cloud Service으로 사용하는 방법에 대해 알아봅니다.
source-git-commit: 2e70c8be73915bea860b98e02c08772bb4f5dcd2
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Dynatrace OneAgent {#dynatrace-oneagent}

Adobe은 엔터프라이즈 배포의 일부로 AEMas a Cloud Service 을 모니터링하고, 잠재적인 문제의 원인을 파악하고, 필요에 따라 문제를 해결하기 위한 조치를 취하는 Dynatrace의 OneAgent를 사용하는 기능을 제공합니다. <!-- When GA, add: Read this [Dynatrace article](https://www.dynatrace.com/hub/detail/adobe-experience-manager/) about AEM monitoring to learn more. -->

## OneAgent와 AEM as a Cloud Service 통합 {#integrating-oneagent-with-aem-as-a-cloud-service}

Dynatrace OneAgent 고객은 고객 지원 티켓을 통해 연결을 요청하여 AEM 사용을 모니터링할 수 있습니다.

연결 요청에 필요한 세부 정보는 아래에 설명되어 있습니다.

| **필드** | **설명** |
|---|---|
| Dynatrace 환경 URL | Dynatrace 환경 URL.<br><br>Dynatrace SaaS 고객의 경우 형식은 다음과 같습니다. `https://<environment>.live.dynatrace.com`.<br><br>Dynatrace Managed 고객의 경우 형식은 다음과 같습니다 `https://<your-managed-url>/e/<environmentId>` |
| Dynatrace 환경 ID | 환경 URL에서 찾을 수 있는 Dynatrace 환경 ID |
| Dynatrace 환경 토큰 | OneAgent 환경 토큰입니다. 이 항목을 만드는 방법은 Dynatrace 설명서 를 참조하십시오.<br><br>이는 비밀로 간주되어야 하므로 적절한 보안 방법을 사용하십시오. 예를 들어 암호는 와 같은 웹 사이트에서 보호합니다. **zerobin.net**&#x200B;고객 지원 티켓에서 암호와 함께 참조할 수 있는 입니다. |
| Dynatrace API 액세스 토큰 | Dynatrace 환경의 API 액세스 토큰입니다. 이 항목을 만드는 방법은 Dynatrace 설명서 를 참조하십시오.<br><br>이는 비밀로 간주되어야 하므로 적절한 보안 방법을 사용하십시오. 예를 들어 암호는 와 같은 웹 사이트에서 보호합니다. **zerobin.net**&#x200B;고객 지원 티켓에서 암호와 함께 참조할 수 있는 입니다.<br><br>참고: 이는 Dynatrace Managed에만 필요합니다. |
| Dynatrace 대상 포트 | Dynatrace 대상 포트입니다.<br><br>참고: 이는 Dynatrace Managed에만 필요합니다. |
| AEM 환경 ID | 모니터링할 AEM 환경 ID. |


