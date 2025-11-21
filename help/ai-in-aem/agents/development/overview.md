---
title: Experience Development 에이전트 개요
description: AEM의 Experience Development Agent가 Cloud Manager에서 실패한 파이프라인을 분석하고 로그를 빌드하여 코드 수정을 제안하고 디버깅 속도를 높이는 방법을 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 1f20d2825befa0345f9ebde3a9854cab591de0f6
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 1%

---


# Experience Development 에이전트 개요 {#development-agent-overview}

Experience Development Agent는 AEM 개발자와 관리자가 코드를 보다 효율적으로 생성, 디버그, 배포 및 최적화할 수 있도록 지원합니다.

현재 에이전트는 파이프라인 상태를 검색하고 수정 사항을 제안하여 빌드 단계의 오류를 해결하는 데 도움이 되며 개발, 스테이지 및 프로덕션 환경에 대한 AEM as a Cloud Service 배포를 디버깅할 때 시간을 절약할 수 있습니다. 빌드 로그 및 관련 코드를 검사하여 수동으로 적용할 수 있는 수정 사항을 권장합니다.

>[!IMPORTANT]
>
>AI가 생성한 응답은 정확하지 않거나 오해의 소지가 있을 수 있습니다. 제안된 수정 사항과 응답을 다시 확인하십시오.
>
>[Adobe Experience Cloud Generative AI 사용 지침](https://www.adobe.com/kr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)도 참조하세요.

<!-- 
## Cloud Manager Pipeline Troubleshooting  {#cloud-manager-pipeline-troubleshooting}
-->

## Cloud Manager을 통해 Experience Development Agent에 액세스 {#how-to-access-the-agent}

Cloud Manager 또는 Experience Hub 등의 사용자 인터페이스에 있는 AI Assistant를 통해 Experience Development Agent에 액세스합니다.

**Cloud Manager을 통해 Experience Development Agent에 액세스하려면:**

1. 시작하려면 [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home)을 클릭하여 홈 페이지를 엽니다.

   ![Adobe Experience Cloud 홈 페이지](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. 왼쪽 레일의 **서비스** 제목 아래에서 **Cloud Manager**&#x200B;을 클릭합니다.

   ![콘텐츠 작성자 사전 설정을 표시하는 드롭다운 목록이 선택되었습니다](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >표시되는 위젯, 도구 및 아티팩트는 사용자 페르소나, 권한 및 AEM 배포 유형(AEM as a Cloud Service 또는 Managed Services 6.5/6.5 LTS)에 따라 다릅니다.

1. 왼쪽 레일의 **프로그램**&#x200B;에서 **![개요 아이콘](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) 개요**&#x200B;를 클릭합니다.

1. **프로그램 개요** 페이지의 **파이프라인** 카드에서 파이프라인을 클릭합니다.

   ![선택한 파이프라인](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-select.png)

1. **빌드 및 코드 검색** 페이지에서 실패한 파이프라인을 확인합니다.

   ![빌드 및 코드 검색 페이지에 표시되는 파이프라인 오류](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-failure.png)

1. AEM 사용자 인터페이스(Cloud Manager 페이지 또는 AEM 환경의 작성자 인스턴스)의 오른쪽 상단 모서리 근처에서 **AI Assistant** 아이콘을 클릭합니다.

   도구 모음의 ![AI 길잡이 아이콘](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   AEM의 [AI 길잡이](/help/implementing/cloud-manager/ai-assistant-in-aem.md)도 참조하세요.

1. 아래쪽 근처에 있는 **AI Assistant** 패널 텍스트 상자에 질문이나 프롬프트를 입력한 다음 `Enter`을 누르거나 ![보내기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg)을 클릭합니다.

   예:
   *&quot;eda-org-01-no-access&quot; 프로그램에서 &quot;no-access&quot; 파이프라인 오류를 분석하고 문제를 해결합니다.*

   프롬프트에서 다음 응답을 표시합니다.

   ![AI Assistant 프롬프트 및 결과 응답](/help/ai-in-aem/agents/development/assets/dev-agent-prompt-response.png)


## 권한 {#permissions}

Experience Development Agent의 파이프라인 문제 해결 작업을 수행하려면 Cloud Manager - 개발자 역할 또는 Cloud Manager - 프로그램 관리자 역할이 필요합니다.



## 샘플 프롬프트 {#sample-prompts}

| 프롬프트 | 결과 |
| --- | --- |
| *기본 프로그램에 대해 실패한 파이프라인을 나열합니다.* | 결과가 달라질 수 있지만 이 프롬프트는 분석할 특정 파이프라인을 참조하기 위한 후속 제안과 함께 실패한 파이프라인 테이블을 출력해야 합니다. |
| *실패한 내 파이프라인을 &quot;개발 파이프라인&quot;이라고 분석합니다.* | 이 프롬프트를 통해 실패한 파이프라인을 분석하고 수정 사항을 제시해야 합니다. |

## 범위를 벗어난 기능 {#out-of-scope-features}

파이프라인 문제 해결은 전체 스택 파이프라인의 빌드 단계에서 작동합니다. 다른 파이프라인 유형 및 단계의 경우 로그를 다운로드하고 검사하여 오류를 디버그합니다.

[로그 액세스 및 다운로드](/help/implementing/cloud-manager/manage-logs.md)를 참조하세요.

BYOGIT(Bring Your Own Git)을 사용하는 프로그램에서는 파이프라인 문제 해결이 지원되지 않습니다.

