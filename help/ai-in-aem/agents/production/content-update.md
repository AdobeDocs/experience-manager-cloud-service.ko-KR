---
title: 콘텐츠 업데이트 스킬
description: Experience Production Agent의 콘텐츠 업데이트 스킬이 무엇이며 이를 통해 어떤 작업을 수행할 수 있는지 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 8b7bdb86c3d1b537b536173b6307c486fe436636
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 1%

---


# 콘텐츠 업데이트 스킬 {#content-update}

Experience Production Agent의 콘텐츠 업데이트 기술은 콘텐츠 프로덕션을 자동화하여 Adobe Experience Manager(AEM) as a Cloud Service 및 Edge Delivery Services의 일상적인 작업을 가속화합니다.

콘텐츠 업데이트 스킬은 콘텐츠 조각, 페이지, 양식 및 에셋을 포함하여 CMS 전체의 기존 콘텐츠를 업데이트합니다. 에이전트는 경험을 정확하고 최신 상태로 유지하기 위해 콘텐츠 요소를 업데이트, 제거, 대체 또는 추가하는 등의 작업을 수행할 수 있습니다. 입력은 자연어 설명이 될 수 있으며, Jira PDF 및 스크린샷과 함께 사용할 경우 입력도 제공할 수 있습니다.

## 개요 {#overview}

콘텐츠 업데이트 스킬은 자연어 또는 시각화를 통해 제공하는 세부 정보를 페이지의 콘텐츠 업데이트로 변환합니다. 업데이트가 필요한 페이지의 URL과 업데이트가 필요한 세부 정보를 입력하면 에이전트 스킬이 작업을 완료합니다.

## 기능 {#capabilities}

다음 위치에서 콘텐츠 업데이트 스킬에 액세스할 수 있습니다.

* [AI 어시스턴트](#ai-assistant)

* [Jira](#jira)

## AI 어시스턴트 {#ai-assistant}

AI Assistant를 통해 AEM의 에이전트에 액세스할 수 있습니다.

experience.adobe.com에서 AI Assistant를 연 다음 `Ask AI Assistant anything` 필드를 사용하여 자연어로 프롬프트를 지정하여 상호 작용을 시작하십시오.

![검색 에이전트 액세스](/help/ai-in-aem/agents/production/assets/content-update-ai-assistant-example.png)

### 샘플 프롬프트 {#sample-prompts}

콘텐츠 업데이트를 시작하려면 다양한 자연어 프롬프트를 제공할 수 있습니다. 업데이트할 페이지의 공개 URL도 지정해야 합니다. 예:

* 다음 페이지를 수정 https://www.your-url.com/sale 블랙 프라이데이 메가 세일 - 최대 70% 할인&quot;으로 향하는 주요 영웅을 업데이트하고, 카운트다운 타이머를 &quot;48시간 후에 끝남&quot;으로 변경하고, &quot;업데이트에 등록&quot;을 제거하고, &quot;지금 쇼핑&quot; 단추를 모두 &quot;Grab the Deal&quot;으로 변경합니다.

* https://www.your-url.com/laptops/your-laptop-model 배너 사본을 "오늘 하루에만 미화 300달러를 절약하십시오"로 업데이트하고, 가격을 1,299 USD에서 999 USD로 업데이트하며, 금융 옵션 배너를 제거하십시오.

* https://www.your-url.com/your-sneaker 재고 상태를 "재고 부족"에서 "재고 부족 - 제한된 수량"으로 업데이트하고, 크기 선택기를 변경하여 사용 가능한 크기를 녹색으로 강조 표시하고, "곧 제공될" 배지를 제거합니다.

* https://www.your-url.com/your-sneaker 새로운 컬러웨이를 표시하도록 제품 이미지를 업데이트합니다.

>[!NOTE]
>
>[Jira](#jira)을(를) 사용하여 상호 작용할 때 파일 업로드를 사용할 수 있지만 AI Assistant에서는 지원되지 않습니다.

## Jira {#jira}

Jira를 사용하여 콘텐츠 업데이트 스킬을 사용하면 편집을 자동화하는 지침을 사용하여 티켓을 만들 수 있습니다.

### 티켓 만들기 {#create-a-ticket}

(모든 유형의) Jira 티켓을 만듭니다.

티켓의 **설명** 필드에 두 가지 필수 세부 정보가 필요합니다.

1. 편집할 페이지의 공개 URL입니다.

1. 변경이 필요했습니다.

   현재 스킬은 변경 사항을 설명하는 다음과 같은 다양한 형식을 지원합니다.

   * 티켓 설명의 자연어
      * 예: &quot;헤드라인을 X에서 Y로 변경&quot;
   * 주석이 있는 PDF이 첨부됨
      * 예를 들어 페이지의 PDF을 만들고 변경할 사항을 자세히 설명하는 주석을 추가합니다
   * 첨부된 PDF의 댓글
      * 예를 들어 페이지의 PDF을 만들고 변경할 사항을 자세히 설명하는 주석을 추가합니다
   * 주석이 있는 스크린샷 첨부됨
      * 예를 들어 페이지 일부의 스크린샷을 캡처하고 변경할 내용을 자세히 설명하는 주석을 추가합니다
   * 자연어 변경 사항이 포함된 Microsoft Word 파일이 첨부됨

### 티켓에서 에이전트 호출 {#invoke-the-agent-from-your-ticket}

에이전트를 사용하려면 티켓에 댓글을 추가합니다. 주석에서는 에이전트가 실행해야 하는 명령과 함께 `@` 기호가 있는 에이전트를 언급합니다. 예를 들면 다음과 같습니다.

* `@aemagent@adobe.com process`

현재 에이전트는 다음 명령을 인식합니다.

* `process` - 요청을 처리합니다.
* `cancel` - 처리 요청 취소
* `retry` - 요청 재처리
* `feedback` - 이전 세대에 피드백 적용
* `reprocess` - 원본 요청을 재처리합니다.

### 에이전트와 상호 작용하는 방법 {#how-the-agent-interacts}

에이전트에 명령을 실행하면 Jira의 주석에 응답합니다. 이 주석은 에이전트의 진행 상황과 수행한 작업에 대해 자세히 설명합니다.

업데이트를 트리거하기 위한 `process` 명령의 경우 응답이 다음 순서를 따를 수 있습니다.

* 초기 주석은 에이전트가 시작되었음을 확인합니다.

* 작업이 완료되면. 에이전트는 수행한 작업의 세부 정보가 포함된 다른 주석으로 응답합니다.
   * 에이전트가 수행한 콘텐츠 업데이트는 비파괴적입니다. 즉, 미리보기 인스턴스가 수행됩니다.
   * 의견에는 업데이트에 대한 링크가 포함되어 있으므로 필요에 따라 검토하고 게시하거나 책임자에게 Jira를 할당할 수 있습니다.

* 다음 이미지는 콘텐츠 업데이트 스킬에 대한 `process` 명령을 트리거하는 예제 Jira를 보여 줍니다.

  ![Experience Production Agent의 콘텐츠 업데이트 기술을 사용한 Jira 예제](assets/content-update-jira-example.png)

## 활성화 {#activation}

Experience Production Agent를 활성화하고 액세스 권한을 얻으려면 Adobe에 문의해야 합니다. 시작하려면 다음으로 문의할 수 있습니다.

* `experience-production-agent@adobe.com`
* 또는 계정 팀에 문의하십시오.

프로세스 속도를 높이기 위해 다음 정보를 제공하는 데 도움이 됩니다.

* AEM as a Cloud Service용
   * 다음을 제공해야 합니다.
      * 조직 ID
      * `product_id`
      * `profile_id`

   * 이러한 값은 다음 단계를 사용하여 찾을 수 있습니다.
      * 관리자가 <https://adminconsole.adobe.com/>을(를) 방문해야 합니다
      * **Adobe Experience Manager as a Cloud Service** 선택
      * 적절한 AEM 인스턴스 선택
      * 해당 콘텐츠에 대한 읽기 및 쓰기 작업을 허용하는 프로필을 선택하십시오.
      * 브라우저 URL 확인
      * URL에서 `product_id` 및 `profile_id`을(를) 추출합니다.
예, <https://adminconsole.adobe.com/products/profiles/users>

* Edge Delivery 문서 작성
   * Adobe 팀에 다음 정보를 제공합니다.
      * 관련 도메인
      * 관련 Github 정보:
         * 조직
         * 레포
         * 분기

## 제한 사항 {#limitations}

현재 Content Updater의 제한 사항은 다음과 같습니다.

* [Jira](#jira)와 상호 작용할 때는 파일 업로드를 사용할 수 있지만 [AI Assistant](#ai-assistant)와 상호 작용할 때는 지원되지 않습니다.
