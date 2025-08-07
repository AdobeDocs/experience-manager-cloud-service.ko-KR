---
title: 제출 액션
description: 적응형 양식에 대한 제출 액션을 구성합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
hide: true
hidefromToC: true
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 100%

---

# 적응형 양식 제출 액션

## 개요

양식 제출은 사용자 여정의 중요한 마지막 단계이며, 수집된 데이터가 처리되고 작업이 수행되는 단계입니다. 이 문서에서는 범용 편집기에서 적응형 양식의 제출 작업을 구성하고 관리하는 방법에 대한 포괄적인 안내서를 제공합니다.

### 학습 내용

이 문서를 끝까지 읽으면 다음을 수행하는 방법에 대해 이해할 수 있습니다.

- 양식에 대한 다양한 유형의 제출 작업 구성
- 외부 시스템과의 통합을 위해 REST 엔드포인트 제출 설정
- 양식 응답에 대한 이메일 제출 구성
- 특정 비즈니스 요구 사항에 맞게 사용자 정의 제출 작업 구현
- 제출 중 양식 유효성 검사 및 오류 시나리오 처리

### 타깃 대상자

이 안내서는 다음을 위해 설계되었습니다.

- 제출 논리를 구현하는 **양식 개발자**
- 양식을 백엔드 시스템에 연결하는 **시스템 통합업체**
- 양식 워크플로를 정의하는 **비즈니스 분석가**
- 양식 제출 프로세스를 설계하는 **기술 설계자**

### 사용 가능한 제출 작업

범용 편집기는 두 가지 기본 제출 작업 유형을 제공합니다.

1. **REST 엔드포인트에 제출** * 양식 데이터를 API 엔드포인트로 보내기
2. **이메일 보내기** * 이메일을 통해 양식 응답 게재

### 사전 요구 사항

제출 작업을 구성하기 전에 다음 사항을 확인합니다.

- 범용 편집기에 대한 액세스
- 양식 구성에 대한 적절한 권한
- 대상 제출 엔드포인트 또는 이메일 구성에 대한 이해

제출 액션은 적응형 양식을 통해 수집된 데이터의 대상을 지정합니다. 제출 절차는 사용자가 양식의 **[!UICONTROL 제출]** 버튼을 클릭하면 시작됩니다. AEM Forms는 아래에 설명된 두 가지 유형의 제출 액션을 제공하며, 특정 요구 사항을 충족하는 사용자 정의 제출 액션을 만들고 사용할 수 있습니다. 기본 제공 제출 액션은 다음과 같습니다.

<!--To define a Submit Action for an Adaptive Form, you use the Properties dialog of the **Adaptive Form block** in the **Editor**-->

- [REST 엔드포인트에 제출](#rest-endpoint-submission-ue)
- [이메일 보내기](#email-submission-ue)


### REST 엔드포인트에 제출 {#rest-endpoint-submission-ue}

REST 엔드포인트에 제출 액션은 제출된 양식 데이터를 지정된 REST 엔드포인트로 보내는 데 사용됩니다. 엔드포인트는 양식이 호스팅되는 내부 서버에 속하거나 상대 경로 또는 절대 경로를 사용하여 외부 서버에 속할 수 있습니다. 양식을 호스팅하는 AEM 서버에 데이터를 제출하려면 AEM 서버 루트 경로에 해당되는 상대 경로를 사용합니다. 예, `/content/forms/af/SampleForm.html`. 데이터를 다른 서버에 제출하려면 절대 경로를 사용하십시오.

<!--Configuring the Submit Action to REST Endpoint for Adaptive Forms offers several benefits such as:  
- It facilitates seamless integration of form data with external systems and services via RESTful APIs.  
- Offers flexibility in managing data submissions from Adaptive Forms, accommodating dynamic and complex data structures.  
- Allows dynamic mapping of form fields to parameters within the REST endpoint URL, enabling adaptable and customizable data submissions.
-->



REST 엔드포인트를 구성하려면 다음 작업을 수행하십시오.

1. **[!UICONTROL 편집기]**&#x200B;에서 적응형 양식을 엽니다.
1. **[!UICONTROL 적응형 양식 블록]**&#x200B;을 선택합니다.
1. 속성 ![properties](/help/forms/assets/Smock_Properties_18_N.svg) 아이콘을 클릭합니다.
1. **[!UICONTROL 제출 액션]** 드롭다운 목록에서 **[!UICONTROL REST 엔드포인트에 제출]**&#x200B;을 선택합니다.
1. REST 엔드포인트 URL을 지정합니다.
1. 또한 **POST 요청을 활성화**&#x200B;하고 요청을 게시하는 URL을 제공할 수 있습니다.

![URL 입력 및 양식 제출을 위한 POST 요청 토글 활성화를 포함한 REST 엔드포인트 구성 필드를 보여 주는 범용 편집기 속성 패널의 스크린샷](/help/forms/assets/enable-post-request-ue.png)

>[!NOTE]
>
> - 데이터를 내부 서버에 게시하려면 리소스 경로를 제공합니다. 데이터는 리소스 경로에 게시됩니다. 예, `/content/restEndPoint`. 해당 게시 요청이 있는 경우 제출 요청에 대한 인증 정보가 사용됩니다.
> - 데이터를 외부 서버에 게시하려면 URL을 제공합니다. URL 형식은 `https://host:port/path_to_rest_end_point`입니다. POST 요청을 익명으로 처리하는 경로를 구성해야 합니다.

### 이메일 보내기 {#email-submission-ue}

이메일 보내기 제출 액션을 통해 양식을 성공적으로 제출하면 한 명 이상의 수신자에게 이메일을 보낼 수 있습니다. 이메일 보내기 구성은 양식 데이터를 미리 정의된 형식으로 포함할 수 있는 이메일을 작성하는 데 유용합니다. 예를 들어 제출된 양식 데이터에서 고객 이름, 배송 주소, 주 이름과 우편번호를 검색하는 다음 템플릿을 고려합니다. [적응형 양식의 이메일 템플릿에 대해 자세히 알아보기](/help/forms/html-email-templates-in-adaptive-forms.md). 이메일 보내기 제출 액션을 사용하여 적응형 양식을 구성하면 다음과 같은 장점이 있습니다.

1. 양식 데이터가 지정된 이메일 수신자에게 직접 전송되므로 빠른 커뮤니케이션이 가능합니다.
1. 양식 제출을 이메일 알림에 직접 통합하여 워크플로를 간소화할 수 있습니다.
1. 조직은 이메일 콘텐츠를 사용자 정의하여 특정 커뮤니케이션 요구 사항에 적합하게 만들 수 있습니다.

![범용 편집기의 적응형 양식 속성](/help/forms/assets/submit-actions-ue.png)


양식 제출에 대한 제출 액션을 이메일로 구성하려면 다음 작업을 수행하십시오.

1. **편집기**&#x200B;에서 적응형 양식을 엽니다.
1. **[!UICONTROL 적응형 양식 블록]**&#x200B;을 선택합니다.
1. 속성 ![properties](/help/forms/assets/Smock_Properties_18_N.svg) 아이콘을 클릭합니다.
1. **[!UICONTROL 제출 액션]** 드롭다운 목록에서 **[!UICONTROL 이메일 보내기]** 옵션을 선택합니다.
1. 이메일 보내기 옵션을 선택하면 아래 이미지와 같이 다음 속성을 구성할 수 있습니다.

<table>
  <thead>
    <tr>
      <th>이미지</th>
      <th>속성</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
    <td rowspan="7"><img src="/help/forms/assets/email-config-ue.png" alt="이메일 구성"></td> 
    <td><b>출처</td>
    <td>발신자의 이메일을 지정합니다.</td>
    </tr>
    <tr>
      <td><b>끝</td>
      <td>이메일의 기본 수신자를 지정하고, 여러 이메일을 쉼표로 구분하여 추가할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>참조</td>
      <td>이메일의 참조 사본(CC)을 받아야 하는 수신자를 지정합니다.</td>
    </tr>
    <tr>
      <td><b>숨은 참조</td>
      <td>이메일의 숨은 참조 사본(BCC)을 받아야 하는 수신자를 지정합니다.</td>
    </tr>
    <tr>
      <td><b>제목</td>
      <td>이메일의 제목을 지정합니다.</td>
    </tr>
    <tr>
      <td><b>외부 템플릿 사용</td>
      <td>외부 이메일 템플릿을 사용하여 이메일 내용을 서식화할 수 있습니다. 외부 템플릿의 URL 또는 경로를 제공하여 AEM Assets 폴더에 호스팅된 사전 설계 이메일 템플릿을 통합합니다.</td>
    </tr>
    <tr>
      <td><b>첨부파일 포함</td>
      <td>이메일의 양식을 통해 제출된 첨부파일을 제출된 양식 데이터에 포함할지 여부를 지정합니다. 지원되는 첨부파일 형식은 PDF, XML 및 JSON입니다.</td>
    </tr>
  </tbody>
</table>






<!--
        
        * **From**: The email address of the sender.
        * **To**: Specify the primary recipients of the email, multiple email addresses can be added, separated by commas.
        * **CC**: Specify the recipients who should receive a carbon copy (CC) of the email.
        * **BCC**: Specify the recipients who should receive a blind carbon copy (BCC) of the email.
        * **Subject**: Specify the subject line of the email.
        * **Use External Template**: Enables the use of an external email template for formatting the email content. Provide the URL or path to the External template path to integrate a pre-designed email template hosted in your AEM Assets folder.
        * **Include Attachment**: Specifies whether the submitted form data should include an attachment submitted through the form in the email.

    ![Screenshot of the Universal Editor email configuration panel showing fields for From, To, CC, BCC, Subject, and options for external templates and attachments](/help/forms/assets/email-config-ue.png)

-->

## 적응형 양식 제출 후 사용자 정의 감사 메시지 표시 {#submit-action-message-ue}

제출 시 옵션을 사용하면 적응형 양식 제출 시 제출 액션 메시지를 구성할 수 있습니다. 양식에 대한 제출 액션 메시지를 구성하려면 다음 작업을 수행하십시오.

1. **편집기**&#x200B;에서 적응형 양식을 엽니다.
1. **[!UICONTROL 적응형 양식 블록]**&#x200B;을 선택합니다.
1. 속성 ![properties](/help/forms/assets/Smock_Properties_18_N.svg) 아이콘을 클릭합니다.
1. 클릭하면 다음 옵션이 표시됩니다.
   - **[!UICONTROL 제출 시]**: 제출 시 양식을 제출할 때 표시되는 메시지를 사용자 정의할 수 있습니다. 기본적으로 양식이 성공적으로 제출되면 사용자에게 “양식을 제출해 주셔서 감사합니다”라는 사용자 정의 메시지가 표시됩니다.
양식 제출 시 감사 메시지를 사용자 정의할 수도 있으며, **[!UICONTROL 메시지 표시]** 옵션을 선택하고 리치 텍스트 **편집기**&#x200B;에서 메시지를 추가하거나 편집할 수도 있습니다.



