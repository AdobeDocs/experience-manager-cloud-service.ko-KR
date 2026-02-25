---
title: 콘텐츠 업데이트 작업
description: Brand Experience Agent의 콘텐츠 업데이트 작업이 무엇이며 이를 통해 어떤 작업을 수행할 수 있는지 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 36f4ba8207da67b8e68c9c9851311defc909b495
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 2%

---


# 콘텐츠 업데이트 작업 {#content-update}

[Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md)의 콘텐츠 업데이트 작업은 콘텐츠 프로덕션을 자동화하여 Adobe Experience Manager(AEM) as a Cloud Service 및 Edge Delivery Services의 일상적인 작업을 가속화합니다.

## 개요 {#overview}

콘텐츠 업데이트 작업은 콘텐츠 조각, 페이지, 양식 및 에셋을 포함한 기존 콘텐츠를 업데이트합니다. 작업은 경험을 정확하고 최신 상태로 유지하기 위해 콘텐츠 요소를 업데이트, 제거, 바꾸기 또는 추가하는 등의 작업을 수행할 수 있습니다. 입력은 자연어 설명이 될 수 있으며, Jira PDF 및 스크린샷과 함께 사용할 경우 입력도 제공할 수 있습니다.

콘텐츠 업데이트 작업은 자연어 또는 시각화를 통해 제공하는 세부 정보를 페이지의 콘텐츠 업데이트로 변환합니다. 업데이트가 필요한 페이지의 URL과 업데이트가 필요한 세부 정보를 입력하면 에이전트 스킬이 작업을 완료합니다. Adobe Experience Manager(AEM) as a Cloud Service에서 사용하는 경우 작업은 새 [launch](/help/sites-cloud/authoring/launches/overview.md)을(를) 만들어 적용하기 전에 업데이트를 검토할 수 있습니다. 문서 작성에 사용하면 작업은 새 [버전](https://experienceleague.adobe.com/en/docs/experience-manager-learn/sites/document-authoring/how-to/document-versions#)을(를) 만듭니다.

## 기능 {#capabilities}

다음 위치에서 콘텐츠 업데이트 스킬에 액세스할 수 있습니다.

* [AI Assistant](#ai-assistant)
* [Jira](#jira)

## AI 어시스턴트 {#ai-assistant}

AI Assistant를 통해 AEM에서 작업에 액세스할 수 있습니다.

[`experience.adobe.com`,](https://experience.adobe.com)에서 AI Assistant를 열고 `Ask AI Assistant anything` 필드를 사용하여 자연어로 프롬프트를 지정하여 상호 작용을 시작하십시오.

![콘텐츠 업데이트 작업](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### 게시 URL 구성 {#configuring-the-publish-url}

게시(공개) URL을 사용하려면 일회성 구성을 수행해야 합니다.

* 사전 요구 사항:

   * 구성을 만들려면 사용자에게 시스템 관리자 또는 제품 관리자 권한이 있어야 합니다.

* 구성:

   1. URL에 대한 콘텐츠 업데이트를 요청하여 콘텐츠 업데이트 스킬을 호출합니다.
   1. 도우미는 여러 가지 질문을 통해 구성을 안내합니다.
   1. 완료되면 게시 URL이 구성되고 사용할 수 있습니다.

예:

![콘텐츠 업데이트 스킬 - 게시 URL 구성](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-publish-url-configuration.png)

### 프롬프트 {#prompts}

콘텐츠 업데이트를 시작하려면 다양한 자연어 프롬프트를 제공할 수 있습니다. 업데이트할 페이지의 공개(게시) URL 또는 작성 환경 URL을 지정해야 합니다. 지원되는 동사의 일부는 그렇지만 전부는 아닙니다. 바꾸기, 업데이트, 제거, 변경, 수정, 수정, 조정, 삭제.

>[!NOTE]
>
>[Jira](#jira)을(를) 사용하여 상호 작용할 때 파일 업로드를 사용할 수 있지만 AI Assistant에서는 지원되지 않습니다.

### 샘플 프롬프트 {#sample-prompts}

샘플 프롬프트는 다음과 같습니다.

* `<your-publish-URL>` 업데이트에서 &quot;완벽한 커피가 4개 질문 남았습니다!&quot; &quot;네 커피, 네 방법!&quot;
* `<your-author-env-URL>`에서 이미지를 &quot;holdingcup.png&quot;에서 &quot;stairhead.png&quot;로 바꿉니다.
* `<your-publish-URL>`에서 &quot;Take our Coffee Quiz&quot; 단추를 더 매력적인 버전으로 변경합니다.&quot;
* `<your-author-env-URL>`에서 &quot;미청구 보상은 누락된 선물입니다!&quot; 섹션을 제거합니다.

## Jira {#jira}

Jira에서 콘텐츠 업데이트 작업을 사용하면 편집을 자동화하는 지침을 사용하여 티켓을 만들 수 있습니다.

### 티켓 만들기 {#create-a-ticket}

(모든 유형의) Jira 티켓을 만듭니다. 티켓의 **설명** 필드에 두 가지 필수 세부 정보가 필요합니다.

1. 편집할 페이지의 공개 URL입니다.

1. 변경이 필요했습니다.

   작업은 변경 사항을 설명하는 다음과 같은 다양한 형식을 지원합니다.

   * 티켓 설명의 자연어
      * 예: &quot;헤드라인을 X에서 Y로 변경&quot;
   * 주석이 있는 PDF이 첨부됨
      * 예를 들어 페이지의 PDF을 만들고 변경할 사항을 자세히 설명하는 주석을 추가합니다
   * 첨부된 PDF의 댓글
      * 예를 들어 페이지의 PDF을 만들고 변경할 사항을 자세히 설명하는 주석을 추가합니다
   * 주석이 있는 스크린샷 첨부됨
      * 예를 들어 페이지 일부의 스크린샷을 캡처하고 변경할 내용을 자세히 설명하는 주석을 추가합니다
   * 자연어 변경 사항이 포함된 Microsoft Word 파일이 첨부됨

### 티켓에서 작업 호출 {#invoke-the-job-from-your-ticket}

작업을 사용하려면 티켓에 주석을 추가합니다. 주석에서 지침과 함께 `@` 기호가 있는 작업을 언급합니다.

예:

* `@aemagent@adobe.com process this ticket`

### 작업이 상호 작용하는 방법 {#how-the-agent-interacts}

작업에 명령을 실행하면 Jira의 주석으로 응답합니다. 주석은 작업의 진행 상황과 수행한 작업에 대해 자세히 설명합니다.

업데이트를 트리거하기 위한 `process` 명령의 경우 응답이 다음 순서를 따를 수 있습니다.

* 초기 주석은 작업이 시작되었음을 확인합니다.

* 작업이 완료되면 작업이 수행된 작업의 세부 정보가 포함된 다른 주석으로 응답합니다.
   * 작업에서 수행한 콘텐츠 업데이트는 비파괴적입니다. 즉, 미리보기 인스턴스로 수행됩니다.
   * 의견에는 업데이트에 대한 링크가 포함되어 있으므로 필요에 따라 검토하고 게시하거나 책임자에게 Jira를 할당할 수 있습니다.

* 다음 이미지는 콘텐츠 업데이트 작업에 대해 `process`명령을 트리거하는 예제 Jira를 보여 줍니다.

  ![Experience Production Agent의 콘텐츠 업데이트 작업을 사용하는 Jira 예](assets/content-update-jira-example.png)

## 활성화 {#activation}

[플레이그라운드](https://www.aem.live/developer/aem-playground)를 통해 AEM 에이전트를 탐색하거나 CSM 또는 TAM과 연결하여 Agentic SKU를 통한 액세스에 대해 논의할 수 있습니다.

## 제한 사항 {#limitations}

다음 제한 사항을 알아 두십시오.

* [Jira](#jira)와 상호 작용할 때는 파일 업로드를 사용할 수 있지만 [AI 길잡이와 상호 작용할 때는 지원되지 않습니다.](#ai-assistant)
