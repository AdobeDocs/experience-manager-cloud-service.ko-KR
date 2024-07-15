---
title: Dynatrace
description: AEM as a Cloud Service과 함께 Dynatrace을 사용하는 방법 알아보기
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 8d5d8910a906e2adf17fa9c75f17634602c2e0b9
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe은 Dynatrace을 사용하여 엔터프라이즈 배포의 일부로 AEM as a Cloud Service을 모니터링하고, 잠재적 문제의 원인을 파악하고, 필요에 따라 이를 해결하기 위한 조치를 취하는 기능을 제공합니다.

Dynatrace을 사용하면 모든 AEM 애플리케이션을 원활하게 확인할 수 있습니다. Dynatrace은 AEM 애플리케이션을 자동으로 감지하고 웹 사이트에서 컨테이너, 클라우드 서비스에 이르기까지 애플리케이션의 종속성을 시각화함으로써 최종 사용자 경험에 대한 포괄적인 가시성을 제공합니다. 모든 계층의 엔드 투 엔드 추적 및 Real Use 모니터링과 상호 작용하여 AEM 콘텐츠 주도 경험을 공백이나 사각지대 없이 한 차원 높은 수준으로 끌어올리십시오. 예외 항목이 발생하면 Dynatrace은 Davis AI 엔진을 사용하여 실시간으로 이를 진단하고 고객이 영향을 받기 전에 근본 원인을 손상된 코드로 찾아내어 평균 복구 시간을 최소화합니다.

Dynatrace에 대한 자세한 내용은 [AEM Cloud Service 통합 Adobe](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/)를 참조하세요.

![AEM 작성자 및 게시자 성능 지표](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Dynatrace과 AEM as a Cloud Service 통합 {#integrating-dynatrace-with-aem-as-a-cloud-service}

Dynatrace 고객은 고객 지원 티켓을 통해 연결을 요청하여 AEM 환경을 모니터링할 수 있습니다.

연결 요청에 필요한 세부 정보는 아래에 설명되어 있습니다.

| **필드** | **설명** |
|---|---|
| [!DNL Dynatrace Environment URL] | Dynatrace 환경 URL.<br><br>Dynatrace SaaS 고객의 경우 형식은 `https://<your-environment-id>.live.dynatrace.com`입니다.<br><br>Dynatrace 관리 고객의 경우 형식은 `https://<your-managed-url>/e/<environmentId>`입니다. |
| [!DNL Dynatrace Environment ID] | Dynatrace 환경 ID입니다. [Dynatrace 연결 세부 정보를 어떻게 얻습니까?](#how-do-i-get-my-dynatrace-connection-details)을(를) 참조하십시오. |
| [!DNL Dynatrace Environment Token] | Dynatrace 환경 토큰. [Dynatrace 연결 세부 정보를 어떻게 얻습니까?](#how-do-i-get-my-dynatrace-connection-details)을(를) 참조하십시오.<br><br>비밀로 간주해야 하므로 적절한 보안 방법을 사용하십시오. 예를 들어 고객 지원 티켓에서 암호와 함께 참조할 수 있는 **zerobin.net**&#x200B;과(와) 같은 웹 사이트에서 암호로 보호합니다. |
| [!DNL Dynatrace API access token] | Dynatrace 환경의 API 액세스 토큰.  만드는 방법은 [Dynatrace API 액세스 토큰 만들기](#create-dynatrace-access-token)를 참조하십시오.<br><br>비밀로 간주해야 하므로 적절한 보안 방법을 사용하십시오. 예를 들어 고객 지원 티켓에서 암호와 함께 참조할 수 있는 **zerobin.net**&#x200B;과(와) 같은 웹 사이트에서 암호로 보호합니다.<br><br>참고: Dynatrace 관리에만 필요합니다. |
| [!DNL Dynatrace ActiveGate Port] | AEM 통합이 연결해야 하는 Dynatrace ActiveGate 포트입니다.<br><br>참고: Dynatrace 관리에만 필요합니다. |
| [!DNL Dynatrace ActiveGate Network Zone] | [Dynatrace ActiveGate 네트워크 영역](https://docs.dynatrace.com/docs/manage/network-zones)을 통해 데이터 센터 및 네트워크 지역 간에 AEM 모니터링 데이터를 효율적으로 라우팅합니다.<br><br>참고: Dynatrace ActiveGate 네트워크 영역은 선택 사항입니다. |
| [!DNL AEM Environment ID(s)] | Dynatrace에서 모니터링할 AEM 환경 ID. |

>[!NOTE]
>
>Dynatrace이 통합되면 이전에 활성화한 경우 데이터가 더 이상 New Relic과 같은 다른 APM 도구로 흐르지 않습니다.

## FAQ {#faq}

### Dynatrace AEM Monitoring에 필요한 라이선스는 무엇입니까? {#which-license-do-i-need-for-AEM-monitoring}

Dynatrace AEM 모니터링에는 Dynatrace 라이선스가 필요합니다. Dynatrace AEM 라이선스는 Kubernetes 컨테이너에 대한 [전체 스택 모니터링](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring)을 기반으로 합니다. 모니터링되는 AEM 컨테이너(작성자 및 게시자 서비스)의 메모리 크기가 자동으로 감지됩니다.

AEM 환경당 Adobe 배포 사양은 다음과 같습니다.

* 프로덕션: 평균적으로 컨테이너 4개, 각각 16GB 메모리
* 비프로덕션: 평균적으로 컨테이너 4개, 각각 8GB 메모리

Dynatrace 라이선싱에 대한 자세한 내용은 [Dynatrace Platform 구독](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription)을 참조하세요.

### Dynatrace 연결 세부 정보를 가져오려면 어떻게 해야 합니까? {#how-do-i-get-my-dynatrace-connection-details}

1. Dynatrace 환경에 대한 다음 API 요청을 실행합니다.

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   `<environmentUrl>`을(를) Dynatrace 환경 URL로 바꾸고 `<accessToken>`을(를) 생성된 API 액세스 토큰으로 바꿉니다.

1. 응답 페이로드에서 `<environmentId>` 및 `<environmentToken>`을(를) 복사하여 보안 위치에 저장합니다.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Dynatrace API 액세스 토큰 만들기 {#create-dynatrace-access-token}

1. Dynatrace 환경에 로그인합니다.
1. **[!DNL Access tokens]**(으)로 이동하여 **[!DNL Generate new token]**&#x200B;을(를) 선택합니다.
1. [!DNL token name] 정의.
1. 토큰 범위를 **[!DNL PaaS integration - Installer download]**(으)로 설정합니다.
1. **[!DNL Generate token]**&#x200B;을(를) 선택합니다.
1. 생성된 액세스 토큰을 복사하여 안전한 장소에 저장합니다.





