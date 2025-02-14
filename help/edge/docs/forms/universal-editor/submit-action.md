---
title: 제출 액션
description: 적응형 양식에 대한 제출 액션을 구성합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 2cb18eb1bf755df48e2d9d10fabf3cdb95e79e57
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 12%

---


# 적응형 양식 제출 액션

제출 액션은 적응형 양식을 통해 수집된 데이터의 대상을 지정합니다. 사용자가 양식에서 **[!UICONTROL 제출]** 단추를 클릭하면 제출 프로세스가 시작됩니다. AEM Forms은 아래에 설명된 두 가지 유형의 제출 액션을 제공하며, 이를 통해 특정 요구 사항에 맞게 사용자 지정 제출 액션을 만들고 사용할 수 있습니다. 기본 제출 작업은 다음과 같습니다.

<!--To define a Submit Action for an Adaptive Form, you use the Properties dialog of the **Adaptive Form block** in the **Editor**-->

* [REST 엔드포인트에 제출](#rest-endpoint-submission-ue)
* [이메일 보내기](#email-submission-ue)


### REST 엔드포인트에 제출 {#rest-endpoint-submission-ue}

REST 끝점에 제출 액션은 제출된 양식 데이터를 지정된 REST 끝점으로 전송하는 데 사용됩니다. 끝점은 폼이 호스팅되는 내부 서버에 속하거나 상대 경로나 절대 경로를 사용하여 외부 서버에 속할 수 있습니다. 양식을 호스팅하는 AEM 서버에 데이터를 제출하려면 AEM 서버 루트 경로에 해당되는 상대 경로를 사용합니다. 예, `/content/forms/af/SampleForm.html`. 다른 서버에 데이터를 제출하려면 절대 경로를 사용하십시오.

<!--Configuring the Submit Action to REST Endpoint for Adaptive Forms offers several benefits such as:  
* It facilitates seamless integration of form data with external systems and services via RESTful APIs.  
* Offers flexibility in managing data submissions from Adaptive Forms, accommodating dynamic and complex data structures.  
* Allows dynamic mapping of form fields to parameters within the REST endpoint URL, enabling adaptable and customizable data submissions.
-->



REST 끝점을 구성하려면 다음을 수행합니다.

1. **[!UICONTROL 편집기]**&#x200B;에서 적응형 양식을 여십시오.
1. **[!UICONTROL 적응형 양식 블록]**&#x200B;을(를) 선택하십시오.
1. 속성 ![속성](/help/forms/assets/Smock_Properties_18_N.svg) 아이콘을 클릭합니다.
1. **[!UICONTROL 제출 동작]** 드롭다운 목록에서 **[!UICONTROL REST 끝점에 제출]**&#x200B;을 선택합니다.
1. REST 끝점 URL을 지정합니다.
1. **POST 요청을 활성화**&#x200B;하고 요청을 게시할 URL을 제공할 수도 있습니다.

{width=50%,height=50%}![적응형 양식에 대한 사후 요청 활성화](/help/forms/assets/enable-post-request-ue.png)

>
>
> * 데이터를 내부 서버에 게시하려면 리소스의 경로를 제공합니다. 데이터는 리소스의 경로에 게시됩니다. 예, `/content/restEndPoint`. 해당 게시 요청이 있는 경우 제출 요청에 대한 인증 정보가 사용됩니다.
> * 데이터를 외부 서버에 게시하려면 URL을 제공합니다. URL 형식은 `https://host:port/path_to_rest_end_point`입니다. POST 요청을 익명으로 처리하는 경로를 구성해야 합니다.

### 이메일 보내기 {#email-submission-ue}

전자 메일 제출 액션을 사용하면 양식 제출에 성공하면 한 명 이상의 수신자에게 전자 메일을 보낼 수 있습니다. 이메일 보내기 구성은 양식 데이터를 사전 정의된 형식으로 포함할 수 있는 이메일을 만드는 데 도움이 됩니다. 예를 들어 제출된 양식 데이터에서 고객 이름, 배송 주소, 상태 이름 및 우편 번호를 검색하는 다음 템플릿을 고려해 보십시오. [적응형 Forms에서 전자 메일 템플릿에 대해 자세히 알아보세요](/help/forms/html-email-templates-in-adaptive-forms.md). 이메일 전송 제출 액션을 사용하여 적응형 양식을 구성할 때의 몇 가지 장점은 다음과 같습니다.

1. 양식 데이터가 지정된 이메일 수신자에게 직접 전송되므로 빠른 통신이 가능합니다.
1. 양식 제출을 이메일 알림에 직접 통합하여 워크플로를 간소화하는 데 도움이 됩니다.
1. 조직이 이메일 콘텐츠를 사용자 정의할 수 있도록 지원하므로 특정 통신 요구 사항에 적합합니다.

{width=50%,height=50%}![유니버설 편집기의 적응형 양식 속성](/help/forms/assets/submit-actions-ue.png)


양식 제출을 위해 제출 액션을 이메일로 구성하려면 다음 작업을 수행하십시오.

1. **편집기**&#x200B;에서 적응형 양식을 여십시오.
1. **[!UICONTROL 적응형 양식 블록]**&#x200B;을(를) 선택하십시오.
1. 속성 ![속성](/help/forms/assets/Smock_Properties_18_N.svg) 아이콘을 클릭합니다.
1. **[!UICONTROL 작업 제출]** 드롭다운 목록에서 **[!UICONTROL 전자 메일 보내기]** 옵션을 선택합니다.
1. 이메일 전송 옵션을 선택하면 아래 이미지에 표시된 대로 다음 속성을 구성할 수 있습니다.

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
    <td>보낸 사람의 이메일 주소를 지정합니다.</td>
    </tr>
    <tr>
      <td><b>끝</td>
      <td>이메일의 기본 수신자를 지정하고 쉼표로 구분하여 여러 이메일 주소를 추가할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>참조</td>
      <td>전자 메일의 참조(CC)를 받을 수신자를 지정합니다.</td>
    </tr>
    <tr>
      <td><b>숨은 참조</td>
      <td>이메일의 숨은 참조(BCC)를 받을 수신자를 지정합니다.</td>
    </tr>
    <tr>
      <td><b>제목</td>
      <td>이메일의 제목 줄을 지정합니다.</td>
    </tr>
    <tr>
      <td><b>외부 템플릿 사용</td>
      <td>외부 이메일 템플릿을 사용하여 이메일 콘텐츠 형식을 지정할 수 있습니다. AEM Assets 폴더에 호스팅되는 미리 디자인된 이메일 템플릿을 통합하려면 외부 템플릿에 대한 URL 또는 경로를 제공하십시오.</td>
    </tr>
    <tr>
      <td><b>첨부 파일 포함</td>
      <td>제출된 양식 데이터에 양식을 통해 제출된 첨부 파일을 이메일에 포함할지 여부를 지정합니다. 지원되는 첨부 파일 형식은 PDF, XML 및 JSON입니다.</td>
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

    {width=50%,height=50%}![Enable post request for adaptive forms](/help/forms/assets/email-config-ue.png)

-->

## 적응형 양식 제출 시 사용자 정의 감사 메시지 표시 {#submit-action-message-ue}

제출 시 옵션을 사용하면 적응형 양식 제출 시 제출 액션 메시지를 구성할 수 있습니다. 양식에 대한 제출 액션 메시지를 구성하려면 다음을 수행합니다.

1. **편집기**&#x200B;에서 적응형 양식을 여십시오.
1. **[!UICONTROL 적응형 양식 블록]**&#x200B;을(를) 선택하십시오.
1. 속성 ![속성](/help/forms/assets/Smock_Properties_18_N.svg) 아이콘을 클릭합니다.
1. 클릭하면 다음 옵션이 표시됩니다.
   * **[!UICONTROL 제출 시]**: 제출 시 양식을 제출할 때 표시할 메시지를 사용자 지정할 수 있습니다. 기본적으로 양식이 성공적으로 제출되면 &quot;양식을 제출해 주셔서 감사합니다&quot;라는 사용자 정의 메시지가 사용자에게 표시됩니다.
**[!UICONTROL 메시지 표시]** 옵션을 선택하여 양식 제출 시 감사 메시지를 사용자 지정하고 서식 있는 텍스트 **편집기**&#x200B;에서 메시지를 추가/편집할 수도 있습니다.


