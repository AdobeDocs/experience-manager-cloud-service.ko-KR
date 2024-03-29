---
title: Dynatrace
description: AEMas a Cloud Service 와 함께 Dynatrace을 사용하는 방법에 대해 알아봅니다.
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
source-git-commit: 4fe8ed9c3f7b6589878da3317d15fede819bad54
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe은 DynatraceAEM 를 사용하여 엔터프라이즈 배포의 일부로 as a Cloud Service을 모니터링하고, 잠재적 문제의 원인을 파악하고, 필요에 따라 이를 해결하기 위한 조치를 취하는 기능을 제공합니다.

Dynatrace을 사용하면 모든 AEM 애플리케이션을 원활하게 확인할 수 있습니다. Dynatrace은 AEM 애플리케이션을 자동으로 감지하고 웹 사이트에서 컨테이너, 클라우드 서비스에 이르기까지 애플리케이션의 종속성을 시각화함으로써 최종 사용자 경험에 대한 포괄적인 가시성을 제공합니다. 모든 계층의 엔드 투 엔드 추적 및 Real User Monitoring과 얽혀 AEM 콘텐츠 주도 경험을 공백이나 사각지대 없이 한 차원 높입니다. 예외 항목이 발생하면 Dynatrace은 Davis AI 엔진을 사용하여 실시간으로 이를 진단하고 고객이 영향을 받기 전에 근본 원인을 손상된 코드로 찾아내어 평균 복구 시간을 최소화합니다.

Dynatrace에 대한 자세한 내용은 [Adobe AEM Cloud Service 통합](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![AEM 작성자 및 게시자 성능 지표](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## AEMas a Cloud Service 과 Dynatrace 통합 {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace 고객은 고객 지원 티켓을 통해 연결을 요청하여 AEM 환경을 모니터링할 수 있습니다.

연결 요청에 필요한 세부 정보는 아래에 설명되어 있습니다.

| **필드** | **설명** |
|---|---|
| [!DNL Dynatrace Environment URL] | Dynatrace 환경 URL.<br><br>Dynatrace SaaS 고객의 경우 형식은 다음과 같습니다. `https://<your-environment-id>.live.dynatrace.com`.<br><br>Dynatrace 관리 고객의 경우 형식은 입니다. `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Dynatrace 환경 ID입니다. 다음을 참조하십시오. [Dynatrace 연결 세부 정보를 가져오려면 어떻게 해야 합니까?](#how-do-i-get-my-dynatrace-connection-details) 이걸 어떻게 구해야 할지. |
| [!DNL Dynatrace Environment Token] | Dynatrace 환경 토큰. 다음을 참조하십시오. [Dynatrace 연결 세부 정보를 가져오려면 어떻게 해야 합니까?](#how-do-i-get-my-dynatrace-connection-details) 이걸 어떻게 구해야 할지.<br><br>이는 비밀로 간주되어야 하므로 적절한 보안 방법을 사용하십시오. 예를 들어 암호는 와 같은 웹 사이트에서 보호합니다. **zerobin.net**&#x200B;고객 지원 티켓에서 암호와 함께 참조할 수 있는 입니다. |
| [!DNL Dynatrace API access token] | Dynatrace 환경의 API 액세스 토큰.  다음을 참조하십시오. [Dynatrace API 액세스 토큰 만들기](#create-dynatrace-access-token) 을(를) 만드는 방법에 대해 설명합니다.<br><br>이는 비밀로 간주되어야 하므로 적절한 보안 방법을 사용하십시오. 예를 들어 암호는 와 같은 웹 사이트에서 보호합니다. **zerobin.net**&#x200B;고객 지원 티켓에서 암호와 함께 참조할 수 있는 입니다.<br><br>참고: Dynatrace Managed에만 필요합니다. |
| [!DNL Dynatrace ActiveGate Port] | AEM 통합이 연결해야 하는 Dynatrace ActiveGate 포트입니다.<br><br>참고: Dynatrace Managed에만 필요합니다. |
| [!DNL Dynatrace ActiveGate Network Zone] | 사용자 [Dynatrace ActiveGate 네트워크 영역](https://docs.dynatrace.com/docs/manage/network-zones) 데이터 센터 및 네트워크 지역 간에 AEM 모니터링 데이터를 효율적으로 라우팅합니다.<br><br>참고: Dynatrace ActiveGate 네트워크 영역은 선택 사항입니다. |
| [!DNL AEM Environment ID(s)] | Dynatrace에서 모니터링할 AEM 환경 ID. |

>[!NOTE]
>
>Dynatrace이 통합되면 이전에 활성화한 경우 데이터가 더 이상 New Relic과 같은 다른 APM 도구로 흐르지 않습니다.

## FAQ {#faq}

### Dynatrace AEM Monitoring에 필요한 라이선스는 무엇입니까? {#which-license-do-i-need-for-AEM-monitoring}

Dynatrace AEM 모니터링에는 Dynatrace 라이선스가 필요합니다. Dynatrace AEM 라이선스는 다음을 기반으로 합니다. [Kubernetes 컨테이너에 대한 전체 스택 모니터링](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). 모니터링되는 AEM 컨테이너(작성자 및 게시자 서비스)의 메모리 크기가 자동으로 감지됩니다.

AEM 환경당 Adobe 배포 사양은 다음과 같습니다.

* 프로덕션: 평균적으로 컨테이너 4개, 각각 16GB 메모리
* 비프로덕션: 평균적으로 컨테이너 4개, 각각 8GB 메모리

Dynatrace 라이선싱에 대한 자세한 내용은 [Dynatrace Platform 구독](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

### Dynatrace 연결 세부 정보를 가져오려면 어떻게 해야 합니까? {#how-do-i-get-my-dynatrace-connection-details}

1. Dynatrace 환경에 대한 다음 API 요청을 실행합니다.

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   바꾸기 `<environmentUrl>` Dynatrace 환경 URL 및 `<accessToken>` API 액세스 토큰을 생성합니다.

1. 다음을 복사합니다. `<environmentId>` 및 `<environmentToken>` 응답 페이로드에서 가져온 다음 안전한 위치에 저장합니다.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Dynatrace API 액세스 토큰 만들기 {#create-dynatrace-access-token}

1. Dynatrace 환경에 로그인합니다.
1. 다음으로 이동 **[!DNL Access tokens]** 및 선택 **[!DNL Generate new token]**.
1. 정의 [!DNL token name].
1. 토큰 범위를 다음으로 설정 **[!DNL PaaS integration - Installer download]**.
1. 선택 **[!DNL Generate token]**.
1. 생성된 액세스 토큰을 복사하여 안전한 장소에 저장합니다.





