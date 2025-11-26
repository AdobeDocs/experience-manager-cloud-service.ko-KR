---
title: 양식 작성 스킬
description: Experience Production Agent의 양식 작성 기술과 자연어를 사용하여 양식을 처음부터 만드는 방법에 대해 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: aa8369979c99535f0fd77e6a51af10cc17afd971
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---


# 양식 작성 스킬 {#form-creation-skill}

양식 작성 기술은 자연어 프롬프트를 사용하여 양식을 개발하도록 설계된 Experience Production Agent의 기능입니다. 이 스킬은 적절한 양식 구조 및 필드 유형을 자동으로 생성합니다. 이 기술은 AI 비서를 통해 제공됩니다.

양식 작성 기술의 주요 이점은 다음과 같습니다.

* **양식 개발 가속화**:
간단한 자연어 명령으로 기존 제품 인터페이스를 학습할 필요가 없습니다.
* **일관된 브랜드 경험**: 승인된 템플릿과 스타일을 사용하여 조직의 브랜딩, 템플릿 및 스타일 지침을 따르는 양식을 만듭니다.
* **낮은 기술 장벽**: 고급 기술 전문가 또는 심층적인 제품 전문 지식 없이도 비즈니스 사용자가 양식을 쉽게 만들 수 있습니다.

## 기능 {#capabilitiess}

* **일반 텍스트 프롬프트를 사용하여 새 양식을 만듭니다**: 일반 언어로 요구 사항을 제출하여 양식을 만들 수 있습니다. 에이전트는 자연어 설명 및 지정된 템플릿을 기반으로 적절한 양식 구조, 필드 유형 및 브랜드 내 경험을 자동으로 생성합니다. 이 기능은 브랜드 및 규정 준수 표준이 유지되도록 하면서 양식 생성을 가속화합니다.

* **PDF 문서를 가져와서 양식으로 변환**: 기존 PDF 문서를 가져와서 양식으로 변환할 수 있습니다. 에이전트는 업로드된 콘텐츠를 분석하여 브랜드 및 규정 준수 표준이 유지되도록 하면서 반응형 디자인 및 유효성 검사 논리를 통해 필드 유형을 감지하고 레이아웃을 보존하며 양식을 향상시킵니다.

  위의 기능 중 하나를 사용하는 경우 만들 양식 유형을 선택하고, 핵심 구성 요소 기반 적응형 양식 템플릿 또는 Edge Delivery Services 기반 적응형 양식 템플릿을 지정하고, 양식을 저장할 기본 경로를 표시하라는 메시지가 표시됩니다. Edge Delivery Services을 기반으로 양식을 만드는 경우 저장소의 GitHub URL을 지정할 수도 있습니다.


### 샘플 프롬프트 {#sample-prompts}

* *이름, 전자 메일 및 메시지 필드를 사용하여 피드백 수집을 위한 양식을 만듭니다*
* *제품 등급(별 1~5개), 댓글 필드 및 선택적 전자 메일이 포함된 고객 피드백 양식 만들기*
* *이름, 전자 메일, 제목 드롭다운 및 메시지 필드를 사용하여 연락처 양식을 만듭니다*
* *개인 정보, 계정 환경 설정 및 약관 수락으로 등록 양식을 만듭니다*
* *PDF 파일(&#39;https://[aem-author-url]/path/to/pdf/file*)을 가져와서 신용 카드 응용 프로그램 양식을 만듭니다.
* *&#39;<https://github.com/wkndforms/wesecure>&#39;에서 상용구를 사용하여 피드백 양식 만들기*

## 양식 세분화 {#refine-with-forms-experience-builder}

AI Assistant를 사용하여 초기 양식 구조를 만든 후 Forms Experience Builder 를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* **양식 업데이트**: 필드를 추가 또는 수정하고, 필드 유형을 조정하고, 필요에 따라 비주얼 편집기를 통해 스타일을 업데이트합니다.

* **레이아웃 업데이트**: 섹션, 그룹 또는 필드를 다시 정렬하고, 간격을 조정하고, 시각적 계층 구조를 수정하여 유용성을 높이고, 대상자가 양식을 명확하고 직관적으로 사용할 수 있도록 합니다.

* **비즈니스 논리 추가**: 조건부 논리를 만들고, 규칙을 표시하거나 숨기고, 필드 종속성을 확인하고, 유효성 검사 규칙을 정의합니다.

* **제출 구성**: 전자 메일 알림 설정, 워크플로우와의 통합 또는 외부 시스템에 대한 연결을 포함하여 양식 데이터를 제출하는 위치를 구성합니다.

자세한 내용은 [Forms Experience Builder 설명서](/help/forms/experience-builder/product-overview.md)를 참조하십시오.


## 활성화 {#activation}

조직에 대해 Experience Production Agent를 활성화하려면 Adobe을 통해 활성화를 시작해야 합니다. 다음을 통해 연락하여 프로세스를 시작합니다.

* 전자 메일: `experience-production-agent@adobe.com`
* 또는 지정된 Adobe 계정 팀에 문의하십시오.

효율적인 온보딩 경험을 위해 다음 세부 정보를 준비하고 제공합니다.

**AEM as a Cloud Service**&#x200B;의 경우 다음 식별자를 공유하십시오.

* 조직 ID
* `product_id`
* `profile_id`

AEM 관리자는 다음 방법으로 찾을 수 있습니다.

1. <https://adminconsole.adobe.com/>로 이동 중
1. **Adobe Experience Manager as a Cloud Service** 선택 중
1. 환경에서 적절한 AEM 인스턴스 선택
1. 관련 컨텐츠에 대한 읽기/쓰기 권한이 있는 프로필 선택
1. 이 페이지에서 전체 브라우저 URL 복사
1. URL에서 `product_id` 및 `profile_id` 값 추출\
   (예: `https://adminconsole.adobe.com/products/profiles/users`과(와) 같은 URL에 이러한 매개 변수가 포함되어 있습니다).

**Edge Delivery 문서 작성**&#x200B;의 경우 Adobe 팀에 다음 사항을 제공하십시오.

* Edge Delivery Services 환경을 위한 도메인
* 해당 GitHub 세부 사항:
   * 조직(조직)
   * 저장소(저장소)
   * 분기

완전하고 정확한 정보를 제공하면 활성화 프로세스가 빨라지고 Experience Production Agent가 적시에 프로비저닝될 수 있습니다.

<!-- 
#### Import and convert {#import-and-convert}

Transform existing documents into interactive digital forms. The agent analyzes uploaded content to detect field types, preserve layouts, and enhance forms with responsive design and validation logic. Supported formats include Acroforms, XFA PDFs, flat PDFs, images (JPG, PNG), and hand-drawn form photographs.

>[!VIDEO](https://video.tv.adobe.com/v/3474042)

**Prompt examples:**

* *Convert the attached PDF file to an adaptive form*
* *Transform this scanned form image into an interactive digital form*
* *Import the employee onboarding PDF and create an editable form*
* *Convert this paper form photograph into a digital form with validation*
-->

<!-- 
### Embed an existing form to a sites page {#embed-existing-form}

The form creation skill enables seamless integration of existing forms into any sites page through natural language commands. Rather than manually locating, copying, and embedding form components, users can simply specify which form to add and where to place it. The agent handles the technical implementation, ensuring proper rendering and functionality.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Embed the contact form to the homepage*
* *Add the existing customer feedback form to the support page*
* *Insert the newsletter signup form into the footer section*
* *Place the registration form on /content/site/signup*
* *Add form "contact-us-2024" to the current page*
-->

<!-- 
### Build and add a form to an existing sites page {#build-and-add-form}

The form creation skill combines form creation and site integration in a single conversational workflow. Users can describe the form they need and specify where to add it, and the agent creates the form and embeds it into the specified page automatically. This eliminates the traditional multi-step process of creating a form separately and then manually adding it to a page.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Create a newsletter signup form with email field and add it to the footer*
* *Build a quick contact form with name, email, and message, then add it to /content/about-us*
* *Add a feedback form with rating stars and comment field to this page*
* *Create a simple survey form with 5 questions and embed it on the customer portal homepage*
* *Build an event registration form with name, email, and date selection, then add it to /content/events/conference-2025*
-->
