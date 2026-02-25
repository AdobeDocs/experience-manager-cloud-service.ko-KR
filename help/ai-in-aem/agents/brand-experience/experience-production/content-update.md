---
title: 콘텐츠 업데이트 작업
description: Brand Experience Agent의 콘텐츠 업데이트 작업이 무엇이며 이를 통해 어떤 작업을 수행할 수 있는지 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 71e3770a7a26b8d3144717513f3ec1c997b3b435
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 2%

---


# 콘텐츠 업데이트 작업 {#content-update}

[Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md)의 콘텐츠 업데이트 작업은 콘텐츠 프로덕션을 자동화하여 Adobe Experience Manager(AEM) as a Cloud Service 및 Edge Delivery Services의 일상적인 작업을 가속화합니다.

## 개요 {#overview}

콘텐츠 업데이트 작업은 콘텐츠 조각, 페이지, 양식 및 에셋을 포함한 기존 콘텐츠를 업데이트합니다. 작업은 경험을 정확하고 최신 상태로 유지하기 위해 콘텐츠 요소를 업데이트, 제거, 바꾸기 또는 추가하는 등의 작업을 수행할 수 있습니다. 입력은 자연어 설명이 될 수 있으며, Jira PDF 및 스크린샷과 함께 사용할 경우 입력도 제공할 수 있습니다.

콘텐츠 업데이트 작업은 자연어 또는 시각화를 통해 제공하는 세부 정보를 페이지의 콘텐츠 업데이트로 변환합니다. 업데이트가 필요한 페이지의 URL과 업데이트가 필요한 세부 정보를 입력하면 에이전트 스킬이 작업을 완료합니다.

## 기능 {#capabilities}

다음 위치에서 콘텐츠 업데이트 스킬에 액세스할 수 있습니다.

* [AI Assistant](#ai-assistant)
* [Jira](#jira)

## AI 어시스턴트 {#ai-assistant}

AI Assistant를 통해 AEM에서 작업에 액세스할 수 있습니다.

[`experience.adobe.com`,](https://experience.adobe.com)에서 AI Assistant를 열고 `Ask AI Assistant anything` 필드를 사용하여 자연어로 프롬프트를 지정하여 상호 작용을 시작하십시오.

![콘텐츠 업데이트 작업](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### 샘플 프롬프트 {#sample-prompts}

콘텐츠 업데이트를 시작하려면 다양한 자연어 프롬프트를 제공할 수 있습니다. 업데이트할 페이지의 공개 URL도 지정해야 합니다. 예:

* 다음 페이지 수정 `https://www.your-url.com/sale` &quot;블랙 프라이데이 메가 세일 - 최대 70% 할인&quot;으로 향하는 주요 영웅 업데이트, 카운트다운 타이머를 &quot;48시간 후 종료&quot;로 변경, &quot;업데이트 등록&quot;을 제거, &quot;지금 쇼핑&quot; 단추를 모두 &quot;거래 잡기&quot;로 변경

* `https://www.your-url.com/laptops/your-laptop-model` 배너 사본을 &quot;오늘 하루만 미화 300달러를 절약하십시오&quot;로 업데이트하고, 가격을 1,299달러에서 999달러로 업데이트하며, 금융 옵션 배너를 제거하십시오.

* `https://www.your-url.com/your-sneaker` 재고 상태를 &quot;재고 부족&quot;에서 &quot;재고 부족 - 제한된 수량&quot;으로 업데이트하고, 크기 선택기를 변경하여 사용 가능한 크기를 녹색으로 강조 표시하고, &quot;곧 제공될&quot; 배지를 제거합니다.

* `https://www.your-url.com/your-sneaker` 새 색상을 표시하도록 제품 이미지를 업데이트하십시오

>[!NOTE]
>
>[Jira](#jira)을(를) 사용하여 상호 작용할 때 파일 업로드를 사용할 수 있지만 AI Assistant에서는 지원되지 않습니다.

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

작업을 사용하려면 티켓에 주석을 추가합니다. 주석에서 실행할 명령과 함께 `@` 기호가 있는 작업을 언급합니다. 예:

* `@aemagent@adobe.com process`

현재 작업은 다음 명령을 이해합니다.

* `process` - 요청을 처리합니다.
* `cancel` - 처리 요청 취소
* `retry` - 요청 재처리
* `feedback` - 이전 세대에 피드백 적용
* `reprocess` - 원본 요청을 재처리합니다.

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

통신 만들기 작업을 활성화하고 액세스하려면 Adobe에 문의해야 합니다. 시작하려면 다음 중 하나를 수행합니다.

* 연락처 `experience-production-agent@adobe.com`
* 또는 계정 팀에 문의하십시오.

프로세스 속도를 높이기 위해 다음 정보를 제공하는 데 도움이 됩니다.

* AEM as a Cloud Service의 경우 다음을 제공해야 합니다.
   * 조직 ID
   * `product_id`
   * `profile_id`

   * 이러한 값은 다음 단계에 따라 찾을 수 있습니다.
      1. 관리자가 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)을(를) 방문해야 합니다.
      1. **Adobe Experience Manager as a Cloud Service** 선택
      1. 적절한 AEM 인스턴스 선택
      1. 해당 콘텐츠에 대한 읽기 및 쓰기 작업을 허용하는 프로필을 선택하십시오.
      1. 브라우저 URL 확인
      1. URL에서 `product_id` 및 `profile_id`을(를) 추출합니다.
예, `https://adminconsole.adobe.com/products/profiles/users`

* Edge Delivery 문서 작성
   * Adobe 팀에 다음 정보를 제공합니다.
      * 관련 도메인
      * 관련 Github 정보:
         * 조직
         * 레포
         * 분기

## 제한 사항 {#limitations}

다음 제한 사항을 알아 두십시오.

* [Jira](#jira)와 상호 작용할 때는 파일 업로드를 사용할 수 있지만 [AI 길잡이와 상호 작용할 때는 지원되지 않습니다.](#ai-assistant)
