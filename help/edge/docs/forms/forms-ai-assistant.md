---
title: AEM Forms용 AI Assistant(Forms Experience Builder)
description: 양식 조각을 사용하여 강력한 양식을 더 빠르게 제작
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 2db966405b5326d735083a66b2625d6d973ad7db
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 1%

---


# AEM Forms용 AI Assistant(Forms Experience Builder)

>[!NOTE]
>
>
> AEM Forms용 AI Assistant(Forms Experience Builder) 기능은 **얼리어답터 프로그램**&#x200B;에서 사용할 수 있습니다. 관심이 있는 경우, 기능에 대한 액세스를 요청하려면 회사 주소에서 mailto:aem-forms-ea@adobe.com으로 빠른 이메일을 보내십시오.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 설명서는 현재 제품에 대해 테스트 중이며 업데이트 및 개정이 적용됩니다. AEM Forms용 AI Assistant가 얼리어답터 프로그램 동안 계속 발전함에 따라 기능, 명령 및 예제가 변경될 수 있습니다.

AEM Forms용 AI 지원(Forms Experience Builder)은 자연어 프롬프트를 통해 일반적인 양식 작성 작업을 간소화함으로써 작성 경험을 향상시킵니다. Forms 관리 UI, 적응형 Forms 편집기 및 유니버설 편집기에서 사용할 수 있으며, 작성 및 구성 작업을 모두 지원하여 보다 스마트하고 빠르게 빌드할 수 있습니다. 이 안내서는 기능을 시작하고 최대한 활용하는 데 도움이 됩니다.

## 시작하기

자세히 살펴보기 전에 AI Assistant에 액세스하고 상호 작용하는 기본 사항을 다룹니다.

### AI Assistant 액세스

AEM Forms의 세 위치에서 AI Assistant에 액세스할 수 있습니다.

1. **Forms 관리 UI**
   - Adobe Experience Manager > Forms > Forms 및 문서로 이동합니다.
   - 인터페이스 왼쪽에 있는 AI Assistant 아이콘을 찾습니다
   - 아이콘을 클릭하여 AI 지원 패널을 엽니다

   ![AI Assistant 아이콘*](/help/edge/docs/forms/assets/forms-manager.gif)

2. **적응형 Forms 편집기**
   - Adobe Experience Manager > Forms > Forms 및 문서로 이동합니다.
   - 편집할 양식 선택 및 열기
   - 편집기 인터페이스에서 AI Assistant 아이콘을 클릭합니다

   ![AI Assistant 아이콘*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif)

3. **범용 편집기**

   - Adobe Experience Manager > Forms > Forms 및 문서로 이동합니다.
   - 인터페이스 왼쪽에 있는 AI Assistant 아이콘을 찾습니다
   - 편집기 인터페이스에서 AI Assistant 아이콘을 클릭합니다

AI Assistant는 현재 위치 및 작업을 기반으로 기능을 조정하며 각 컨텍스트에 대한 관련 지원을 제공합니다.

### 상호 작용 방법:

- 요청을 자연어로 입력하기만 하면 됩니다.
- 사용 가능한 명령 또는 빠른 작업 목록을 보려면 `/`을(를) 사용하십시오.
- 도우미가 특정 필드를 구성하거나 업데이트하도록 하려면 `@fieldName`(예: `@firstName`, `@emailAddress`)을(를) 사용하여 특정 양식 필드를 참조합니다.
- 이미지, PDF, Figure 파일 또는 기타 디자인 에셋을 업로드하여 AI Assistant가 요구 사항을 더 잘 이해할 수 있도록 할 수 있습니다.


### 빠른 시작

소개 비디오를 통해 빠르게 시작하고 실행:

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)


이 비디오에서는 모든 환경에서 Assistant 실행, 기본 상호 작용 및 기능에 대한 개요를 다룹니다.

## AI 지원 명령 참조

| 명령 | 설명 | 용도 | 사용 컨텍스트 | 예 | 주요 기능 |
|---------|-------------|---------|---------------|----------|--------------|
| /create-form | Forms 관리 UI 또는 Forms 편집기에서 새 양식 시작 | 처음부터 완전히 새로운 양식 작성 시작 | Forms 관리 UI, 적응형 Forms 편집기 | 첨부된 PDF을 기반으로 하는 /create-form 고객 피드백 설문 조사 | 양식 구조에 대한 옵션을 제공하고 양식을 만듭니다. 디자인 참조에 대해 **첨부 파일 지원** |
| /add-form | 유니버설 편집기에서 새 양식 추가 | 유니버설 편집기 내에 새 양식 블록 또는 구성 요소를 추가합니다. | Edge Delivery Services용 유니버설 편집기 | /add-form 이름 및 전자 메일이 포함된 연락처 양식 | 블록 기반 편집에서 작동하는 양식 블록을 삽입합니다. 레이아웃 지침을 위해 **첨부 파일 지원** |
| /update-layout | 양식의 레이아웃을 아코디언, 탭 기반, 마법사 또는 단일 페이지 반응형 디자인으로 변경 | 전반적인 구조적 레이아웃 및 탐색 패턴을 수정합니다. | 모든 편집 환경 | 3단계로 구성된 /update-layout 마법사 | 아코디언, 탭, 마법사, 단일 페이지 반응형 옵션 |
| /update-field | 기존 양식 필드의 속성 및 구성 수정 | 레이블, 유효성 검사, 서식 지정, 비헤이비어와 같은 필드 속성을 변경합니다. | 모든 편집 환경 | /update-field@email 유효성 검사와 함께 필수입니다. | 레이블, 유효성 검사 규칙, 필드 유형, 기본값, 가시성 필드 디자인 예제에 대해 **첨부 파일 지원** |
| /create-rule | 양식에 대한 동적 동작 및 조건부 논리 만들기 | 비즈니스 논리, 계산, 조건부 상호 작용 구현 | 모든 편집 환경 | /create-rule 이벤트@spouseName &quot;Married@maritalStatus과 같은 경우 | 조건부 가시성, 계산, 유효성 검사, 값 설정 |
| /create-panel | 새 패널 만들기(관련 필드 그룹화용 컨테이너) | 구조적 컨테이너를 추가하여 양식 필드를 논리적으로 구성합니다. | 모든 편집 환경 | /create-panel 이름, 이메일, 전화를 포함한 개인 정보 | 필드 그룹화, 제목, 레이아웃 옵션, 축소 가능한 섹션. 패널 레이아웃 참조에 대해 **첨부 파일 지원** |
| /add-panel | 범용 편집기에서 이미지를 양식 패널로 변환 | AI를 사용하여 업로드된 이미지를 분석하고 구조화된 양식 패널로 변환 | 범용 편집기 | 업로드된 양식 이미지의 /add-panel | 이미지 인식, 기능 간 전환, 레이아웃 보존. 이미지 분석을 위해 **첨부 파일 필요** |
| /configure-submit | 양식 제출 작업 및 데이터 처리 설정 | 사용자가 완료된 양식을 제출할 때 수행되는 작업 정의 | 모든 편집 환경 | `support@company.com`(으)로 전자 메일을 보내려면 /configure-submit을 사용하십시오. | 이메일, REST API, 워크플로우, 스프레드시트, 데이터베이스, Power Automate |
| /help | AI Assistant의 액세스 지원 및 설명서 | AEM Forms에 대한 상황별 도움말, 지침 및 답변을 제공합니다. | 모든 편집 환경 | /help 다단계 양식을 만들려면 어떻게 해야 합니까? | 기능 설명, 안내서, 모범 사례, 문제 해결 |

### 명령 범주

| 범주 | 명령 | 기본 사용 사례 |
|----------|----------|-------------------|
| 양식 생성 | /create-form, /add-form | 새 양식 시작, 양식 블록 추가 |
| 구조 및 레이아웃 | /update-layout, /create-panel, /add-panel | 양식 구조 구성, 시각적 디자인 |
| 필드 관리 | /update-field | 개별 양식 요소 구성 |
| 논리 및 규칙 | /create-rule | 동적 비헤이비어 및 유효성 검사 추가 |
| 제출 | /configure-submit | 데이터 처리 및 워크플로우 설정 |
| 지원 | /help | 지원 및 설명서 받기 |

### 구문 지침

| 요소 | 포맷 | 예 | 메모 |
|---------|--------|---------|-------|
| 명령 | /command-name | /create-form | 항상 슬래시로 시작 |
| 필드 참조 | @fieldName | @email, @firstName | 기존 필드에 @ 기호 사용 |
| 자연어 | 명령 + 설명 | /create-rule 조건인 경우 필드 표시 | 명령을 설명 텍스트와 결합 |
| 여러 작업 | 별도의 명령 | /create-panel 및 /update-layout | 한 번에 하나의 명령 적용 |


### 환경별 기능

| 환경 | 사용 가능한 명령 | 특별 기능 |
|-------------|-------------------|------------------|
| Forms 관리 UI | /create-form, /help | 양식 수준 생성 및 관리 |
| 적응형 Forms 편집기 및 유니버설 편집기 | 모든 명령 | 전체 기능 세트, 세부 구성 |



### 필드 참조 구문(컨텍스트 요소)

기존 필드를 참조하려면 `@fieldName`을(를) 사용하십시오.

- `@firstName` - 이름 필드
- `@email` - 전자 메일 필드
- `@phoneNumber` - 전화 번호 필드
- `@dateOfBirth` - 생년월일 필드

### 구성 요소 유형

이 목록에서는 일반적인 구성 요소 유형을 다룹니다. AI는 변형 또는 더 많은 전문 유형을 인식할 수 있지만 이러한 정확한 용어를 사용하면 최상의 결과를 얻을 수 있습니다.

- `text input` - 한 줄 텍스트 필드
- `text area` - 여러 줄 텍스트 필드
- `dropdown` - 목록 선택
- `checkbox` - 단일 확인란
- `checkbox group` - 여러 확인란
- `radio group` - 라디오 단추 그룹
- `date picker` - 날짜 선택
- `file upload` - 첨부 파일
- `panel` - 필드 그룹화를 위한 컨테이너


## 핵심 기능 및 확장된 프롬프트 예

AI 어시스턴트는 다양한 명령을 이해합니다. 다음은 그 힘을 보여주는 몇 가지 예입니다. 패널, 텍스트 입력, 확인란 등의 구성 요소에 정확한 용어를 사용하십시오.

| 기능 범주 | 설명 | 프롬프트 예 |
| ------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **양식 만들기** | 처음부터 또는 설명을 기반으로 새 양식을 시작합니다. | `Create a new form titled 'Employee Onboarding'.` <br> `Generate a customer feedback form with fields for name, email, rating (1-5 stars), and comments.` <br> `Start a simple contact form with name, email, and message fields.` <br> `Design a multi-page registration form for an event.` <br> `Create a form based on the attached PDF template.` |
| **디자인 가져오기** | 기존 디자인(이미지, Figma, PDF)을 AEM Form으로 변환합니다. | `Import the form design from this uploaded PDF file.` <br> `Convert the uploaded Figma design into an adaptive form, focusing on the 'User Profile' frame.` <br> `Use this JPEG image of our old paper form to create a new digital version.` <br> `Create a form based on the layout of the attached PNG.` <br> `Recreate the form shown in the attached screenshot with modern styling.` |
| **구성 요소 및 패널 추가** | 다양한 양식 필드 및 구조적 컨테이너(패널)를 추가합니다. | `Add a text input field for 'First Name'.` <br> `Add a 'Personal Details' panel with fields for full name, date of birth, and phone number.` <br> `Insert a checkbox group for 'Interests' with options: Technology, Sports, Music.` <br> `Add a file upload component for 'Resume'.` <br> `Create a repeatable panel named 'WorkExperience' with fields for company, title, and dates.` <br> `Add a panel matching the layout shown in the attached design mockup.` |
| **레이아웃 조정** | 양식 레이아웃의 구조와 모양을 수정합니다. | `Change the 'Personal Details' panel to a two-column layout.` <br> `Set the overall form layout to a wizard (multi-step) navigation.` <br> `Make the header section span the full width of the form.` <br> `Adjust the spacing between fields in the 'Address' panel to be compact.` <br> `Align all field labels to the left.` <br> `Update the form layout to match the attached wireframe.` |
| **규칙 만들기 및 논리** | 동적 비헤이비어, 계산 및 조건부 가시성을 구현합니다. | `Make the 'Spouse Name' field visible only if 'Marital Status' is selected as 'Married'.` <br> `Calculate the 'Total Amount' by multiplying @quantity and @price.` <br> `Enable the submit button only when the @termsAndConditions checkbox is checked.` <br> `Set the value of @countryCode to '+1' if @country is 'United States'.` <br> `If @age is less than 18, show a message 'Must be 18 or older'.` |
| **필드 속성 업데이트** | 레이블, 자리 표시자 등과 같은 특정 양식 필드의 속성을 수정합니다. | `Change the label of @email to 'Primary Email Address'.` <br> `Set the @comment field to be a multi-line text area.` <br> `Make the @phoneNumber field mandatory.` <br> `Add placeholder text 'Enter your ZIP code' to the @zipCode field.` <br> `Change the @country field to a dropdown and populate it with: USA, Canada, UK, Germany.` <br> `Update the help description for @password to 'Must include an uppercase letter, a number, and be at least 8 characters long.'` <br> `Set the maximum length of the @username field to 15 characters.` <br> `Configure the @dateOfBirth field to use a date picker.` <br> `Style the @email field to match the design shown in the attached image.` |
| **제출 액션** | 사용자가 양식을 제출할 때 수행되는 작업을 정의합니다. | `Configure the form to submit data to the REST endpoint /api/v2/application-submit.` <br> `Set up an email submission to hr@example.com and sales@example.com on successful submission.` <br> `Trigger an AEM workflow named 'NewLeadProcessing' when this form is submitted.` <br> `On submit, redirect the user to a thank you page at /content/thankyou.html.` |
| **테마 설정** | 기존 AEM Forms 테마를 적용하여 양식 스타일을 지정합니다. | `Apply the 'Modern Business' theme to this form.` <br> `Switch to the 'Accessible Dark' theme.` <br> `Revert to the default canvas theme.` <br> `Apply styling that matches the brand guidelines shown in the attached style guide.` |
| **탐색 및 구조** | 탐색 요소를 추가하거나 양식의 일부를 재구성합니다. | `Add a 'Next' button to the current panel and a 'Previous' button to the next panel.` <br> `Create a Table of Contents based on the form's panels.` <br> `Move the 'Address' panel to be before the 'Contact Information' panel.` |
| **유효성 검사** | 필드에 대한 특정 유효성 검사 규칙을 설정합니다. | `Set a regex pattern for the @employeeID field to be 'EMP\d{5}'.` <br> `Ensure the @age field only accepts numeric values between 18 and 99.` <br> `Validate the @email field to ensure it is a valid email format.` |
| **계획 검토**(유니버설 편집기) | 실행 전에 도우미가 제안한 변경 사항을 미리 봅니다. | `Add a contact form with fields for name, email, subject, and message.`(도우미가 만들 구성 요소 및 속성의 계획을 표시한 다음 &quot;적용&quot;을 클릭합니다.) <br> `Create a form based on the attached design file.`(도우미가 첨부 파일을 분석하고 구현 전에 세부 계획을 표시합니다.) |

## 최적의 결과를 위한 모범 사례

AI Assistant를 최대한 활용하려면 다음 팁을 염두에 두십시오.

- **단순하게 시작, 증분 빌드:** 처음에 너무 복잡한 여러 단계 요청이 아닌 더 작고 구체적인 명령으로 시작합니다(예: &quot;First Name&quot;에 대한 텍스트 입력 추가&quot;).
- **AEM Forms 용어 사용:** 도우미가 더 잘 이해할 수 있도록 &quot;패널&quot;, &quot;텍스트 입력 필드&quot;, &quot;확인란 그룹&quot;, &quot;제출 액션&quot;, &quot;규칙&quot; 등의 용어를 사용합니다.
- **필드 참조:** 기존 필드를 구성할 때는 `@fieldName` 표기법(예: `Make @firstName mandatory`)을 사용하십시오.
- **계획 검토** &quot;적용&quot;을 클릭하기 전에 항상 유니버설 편집기의 도우미가 제안한 변경 사항에 대해 계획을 주의 깊게 검토하십시오.
- **수동으로 유효성 검사:** 도우미가 변경한 후에는 항상 양식을 미리 보고 테스트하여 양식이 예상대로 작동하고 보이는지 확인하십시오. AI는 강력한 도구이지만 최종 검증이 핵심이다.
- **반복 및 세분화:** 첫 번째 프롬프트에서 정확한 결과를 얻지 못한 경우 요청을 더 작은 단계로 바꾸거나 바꿔 보십시오.
- **피드백 제공:** 기본 제공 피드백 메커니즘을 사용하여 도우미가 배우고 개선할 수 있도록 합니다(&quot;피드백 및 지원&quot; 섹션 참조).

## AI Assistant의 제품 도움말

AEM Forms용 AI 도우미는 단순한 빌드가 아닙니다. AEM Forms의 다양한 기능을 학습하고, 이해하고, 사용하는 데 도움이 될 수도 있습니다.

### 지원되는 도움말 항목

다음과 같은 보조 질문을 할 수 있습니다.

- &quot;새 적응형 양식을 처음부터 만들려면 어떻게 합니까?&quot;
- &quot;적응형 Forms의 패널은 무엇이며 어떻게 사용됩니까?&quot;
- &quot;양식에 테마를 적용하는 방법을 설명합니다.&quot;
- &quot;양식 및 패널에 지원되는 레이아웃 유형은 무엇입니까?&quot;
- &quot;이메일 전송과 같은 다양한 제출 액션을 구성하려면 어떻게 해야 합니까?&quot;
- &quot;Figma 디자인을 사용하여 양식을 만드는 방법을 안내해 줄 수 있습니까?&quot;
- &quot;여러 단계로 구성된 양식을 만드는 가장 좋은 방법은 무엇입니까?&quot;

### 도움을 요청하는 방법:

1. Forms 관리 UI 또는 적응형 Forms 편집기에서 AI 비서를 엽니다.
2. 질문을 자연어로 입력합니다(예: &quot;반복 가능한 패널을 추가하려면 어떻게 합니까?&quot;).
3. 보조자는 다음과 같이 응답합니다.
   - 단계별 지침
   - AEM Forms 개념에 대한 설명.
   - 관련 Adobe Experience League 설명서에 대한 링크(해당하는 경우).

### 도움말 보기 팁:

- **구체적으로 표시:** 한 번에 하나의 명확한 질문을 합니다.
- **키워드 사용:** AEM Forms 기능 또는 UI 요소와 관련된 키워드를 포함합니다(예: &quot;적응형 양식 편집기&quot;, &quot;규칙 편집기&quot;, &quot;테마&quot;).
- **필요한 경우 다시 표시:** 도우미가 원하는 정보를 이해하지 못하거나 제공하지 않으면 질문을 단순화하거나 다른 용어를 사용하십시오.


## 일반적인 문제 해결

- **도우미가 응답하지 않음:**
   - 지원되는 환경(Forms 관리 UI, 적응형 Forms 편집기 또는 유니버설 편집기)에서 활발하게 작업하고 있는지 확인하십시오.
   - 인터넷 연결을 확인합니다.
   - AI 지원 패널을 닫았다가 다시 열어 보십시오.

- **부정확하거나 예기치 않은 응답:**
   - 요청을 더 구체화하거나 더 간단하게 구문을 변경합니다.
   - 복잡한 요청을 더 작은 개별 명령으로 분류합니다.
   - 표준 AEM Forms 용어를 사용하고 있는지 확인합니다.

- **디자인 가져오기 문제(PDF/Figma/Image):**
   - 디자인 파일이 명확하고, 구조가 잘 되어 있으며 읽기 가능한지 확인합니다.
   - 파일 형식이 지원되는지 확인합니다(PDF, Figma 링크, PNG, JPG과 같은 일반적인 이미지 유형).
   - Figma의 경우 타깃팅하는 프레임이 명확하게 정의되어 있고 액세스할 수 있는지 확인합니다.

- **필드 `@fieldName`을(를) 인식할 수 없음:**
   - 양식에 있는 필드의 정확한 이름을 다시 확인합니다. 필드 이름은 대소문자를 구분하므로 정확하게 일치해야 합니다.
   - 필드를 수정하려는 경우 필드가 이미 있는지 확인합니다.


## 피드백 및 지원

귀하의 입력은 AI Assistant의 지속적인 개선에 유용합니다.

- **피드백 제공:** AI Assistant 인터페이스에서 기본 제공 **&quot;피드백 제공&quot; 명령 또는 단추**&#x200B;를 사용하여 경험을 공유하거나 문제를 보고하거나 개선 사항을 제안하십시오. (예: `/feedback`을(를) 입력하거나 피드백 아이콘을 찾을 수 있습니다).
- **공식 지원:** 중요한 문제나 추가 지원이 필요한 경우 공식 Adobe 지원 채널 또는 조직의 지정 지원 연락처를 통해 연락하십시오.



## 첨부 파일 작업

AI Assistant는 파일 첨부를 지원하여 양식 작성 및 구성 경험을 향상시킵니다. 다양한 파일 형식을 연결하여 변환할 시각적 컨텍스트, 디자인 참조 또는 기존 양식을 제공할 수 있습니다.

### 지원되는 첨부 파일 유형

| 파일 유형 | 사용 사례 | 첨부 파일을 지원하는 명령 | 예 |
|-----------|-----------|-----------------------------------|----------|
| **이미지**(PNG, JPG, JPEG, GIF) | 양식 레이아웃 참조, UI mockup, 종이 양식 스캔 | /create-form, /add-form, /create-panel, /add-panel, /update-field | 원하는 레이아웃의 스크린샷 업로드 |
| **PDF 파일** | 변환할 기존 양식, 디자인 사양 | /create-form, /add-form, /create-panel, /add-panel | PDF 애플리케이션 양식 변환 |
| **그림 파일** | 시스템 참조, UI 프로토타입 디자인 | /create-form, /add-form, /create-panel | Figure 디자인 프레임 가져오기 |
| **디자인 파일**(스케치, Adobe XD 내보내기) | 시각적 디자인 참조 | /create-form, /add-form, /create-panel | 참조 디자인 시스템 구성 요소 |

### 첨부 파일 사용 방법

1. **다음 명령을 사용하여 첨부:**

   - AI Assistant 인터페이스에서 첨부 아이콘 클릭
   - 장치에서 파일 선택
   - 첨부 파일을 참조하는 명령을 입력합니다.

2. **명령의 첨부 파일 참조:**

   ```
   /create-form based on the attached PDF application form
   /add-panel using the layout shown in the uploaded image
   /create-panel following the design in the attached Figma file
   /update-field @email to match the style in the attached screenshot
   ```

3. **여러 첨부 파일:**

   - 비교 또는 참조를 위해 여러 파일을 첨부할 수 있습니다
   - 사용할 첨부 파일 지정: &quot;첫 번째 첨부된 이미지 사용&quot; 또는 &quot;PDF 파일 기반&quot;

### 첨부 파일 우수 사례

- **선명한 고품질 이미지:** AI 분석을 위해 업로드된 이미지가 선명하고 읽기 쉽도록 합니다.
- **관련 파일 이름:** AI가 컨텍스트를 이해하는 데 도움이 되도록 설명 파일 이름을 사용합니다.
- **단일 포커스:** 각 첨부 파일은 한 가지 특정 측면(레이아웃, 필드 디자인 등)에 중점을 두어야 합니다.
- **지원되는 형식:** 최상의 호환성을 위해 일반 형식(PNG, JPG, PDF)에 고정됨
- **파일 크기:** 최적의 처리 속도를 위해 첨부 파일을 10MB 미만으로 유지

### 첨부 파일 워크플로 예

**용지 양식 변환:**

1. 종이 서식을 명확하게 스캔하거나 촬영합니다.
2. 이미지 파일 업로드
3. 명령 사용: `/create-form based on the attached form image, converting all fields to digital equivalents`

**디자인 시스템과 일치:**

1. 관련 디자인 구성 요소 내보내기 또는 스크린샷
2. 디자인 참조 첨부
3. 명령 사용: `/create-panel following the visual style and layout shown in the attached design`

**필드 스타일 참조:**

1. 원하는 필드 모양의 스크린샷 첨부
2. 명령 사용: `/update-field @email to match the styling and layout shown in the attached image`

## 관련 컨텐츠

[AEM Forms AI Assistant - 프롬프트 라이브러리](/help/edge/docs/forms/ai-assistant-prompt-library.md)

## 첨부 파일 작업

AI Assistant는 파일 첨부를 지원하여 양식 작성 및 구성 경험을 향상시킵니다. 다양한 파일 형식을 연결하여 변환할 시각적 컨텍스트, 디자인 참조 또는 기존 양식을 제공할 수 있습니다.

### 지원되는 첨부 파일 유형

| 파일 유형 | 사용 사례 | 첨부 파일을 지원하는 명령 | 예 |
|-----------|-----------|-----------------------------------|----------|
| **이미지**(PNG, JPG, JPEG, GIF) | 양식 레이아웃 참조, UI mockup, 종이 양식 스캔 | /create-form, /add-form, /create-panel, /add-panel, /update-field | 원하는 레이아웃의 스크린샷 업로드 |
| **PDF 파일** | 변환할 기존 양식, 디자인 사양 | /create-form, /add-form, /create-panel, /add-panel | PDF 애플리케이션 양식 변환 |
| **그림 파일** | 시스템 참조, UI 프로토타입 디자인 | /create-form, /add-form, /create-panel | Figure 디자인 프레임 가져오기 |
| **디자인 파일**(스케치, Adobe XD 내보내기) | 시각적 디자인 참조 | /create-form, /add-form, /create-panel | 참조 디자인 시스템 구성 요소 |

### 첨부 파일 사용 방법

1. **다음 명령을 사용하여 첨부:**

   - AI Assistant 인터페이스에서 첨부 아이콘 클릭
   - 장치에서 파일 선택
   - 첨부 파일을 참조하는 명령을 입력합니다.

2. **명령의 첨부 파일 참조:**

   ```
   /create-form based on the attached PDF application form
   /add-panel using the layout shown in the uploaded image
   /create-panel following the design in the attached Figma file
   /update-field @email to match the style in the attached screenshot
   ```

3. **여러 첨부 파일:**

   - 비교 또는 참조를 위해 여러 파일을 첨부할 수 있습니다
   - 사용할 첨부 파일 지정: &quot;첫 번째 첨부된 이미지 사용&quot; 또는 &quot;PDF 파일 기반&quot;

### 첨부 파일 우수 사례

- **선명한 고품질 이미지:** AI 분석을 위해 업로드된 이미지가 선명하고 읽기 쉽도록 합니다.
- **관련 파일 이름:** AI가 컨텍스트를 이해하는 데 도움이 되도록 설명 파일 이름을 사용합니다.
- **단일 포커스:** 각 첨부 파일은 한 가지 특정 측면(레이아웃, 필드 디자인 등)에 중점을 두어야 합니다.
- **지원되는 형식:** 최상의 호환성을 위해 일반 형식(PNG, JPG, PDF)에 고정됨
- **파일 크기:** 최적의 처리 속도를 위해 첨부 파일을 10MB 미만으로 유지

### 첨부 파일 워크플로 예

**용지 양식 변환:**

1. 종이 서식을 명확하게 스캔하거나 촬영합니다.
2. 이미지 파일 업로드
3. 명령 사용: `/create-form based on the attached form image, converting all fields to digital equivalents`

**디자인 시스템과 일치:**

1. 관련 디자인 구성 요소 내보내기 또는 스크린샷
2. 디자인 참조 첨부
3. 명령 사용: `/create-panel following the visual style and layout shown in the attached design`

**필드 스타일 참조:**

1. 원하는 필드 모양의 스크린샷 첨부
2. 명령 사용: `/update-field @email to match the styling and layout shown in the attached image`
