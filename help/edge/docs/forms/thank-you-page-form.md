---
title: 양식 제출 후 사용자 정의 감사 메시지 표시
description: 양식 블록에 대한 감사 페이지와 리디렉션을 구성하여 사용자 경험을 최적화하고 사용자 여정을 간소화하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 4356fcc73a9c33a11365b1eb3f2ebee5c9de24f0
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 51%

---

# 양식 제출 후 사용자 정의 감사 메시지 표시

사용자가 양식을 제출한 후 감사 메시지를 통해 원활한 경험을 제공하는 것이 중요합니다. 성공적인 제출을 확인하는 것은 물론, 사용자 만족도를 높이고 여정에 있어 더욱 안내한다.

* **감사 메시지**: 감사 메시지는 사용자 경험의 초석으로, 브랜드 정체성을 강화하는 동시에 안심할 수 있고 중요한 정보를 전달할 수 있습니다. 이는 작업 완성도와 사용자의 만족도를 높이면서 사용자의 작업을 직접적으로 승인합니다.

* **리디렉션**: 리디렉션은 사용자를 관련 대상으로 유도한 다음 사용자 참여도를 최적화하여 최종적으로 전환율을 높이는 데 핵심적인 역할을 합니다. 리디렉션은 사용자에게 고객 여정의 다음 단계를 원활하게 안내함으로써 원활한 탐색 경험을 제공할 수 있습니다. 예를 들어 초기 세부 정보를 수집한 후 사용자를 결제 페이지로 리디렉션합니다.

양식 제출 시 후속 감사 메시지 표시는 적응형 양식 블록의 기본 비헤이비어입니다. 메시지가 양식 제출에 성공하면 양식 맨 위에 표시됩니다.

![기본 감사 메시지](/help/edge/assets/thank-you-message.png)

단, 특정 요구 사항에 따라 이 환경을 유연하게 조정할 수 있습니다. 옵션은 다음과 같습니다.

* 양식 제출 후 사용자 정의 감사 메시지 표시
* 추가 작업을 위해 사용자를 다른 페이지 사후 제출로 리디렉션

>[!NOTE]
>
> 다음 [조회 스프레드시트](/help/edge/docs/forms/assets/enquiry.xlsx)를 참조하여 요구 사항에 따라 감사 메시지를 사용자 지정할 수 있습니다.

## 사용자 정의 감사 메시지 구성

양식 제출 시 개인화된 감사 메시지를 표시하려는 경우 스프레드시트를 구성하여 표시할 수 있습니다.

적응형 양식 블록에 대한 사용자 정의 감사 메시지를 구성하려면 아래 단계를 따릅니다.

1. Microsoft SharePoint 또는 Google Workspace의 Edge Delivery 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.
1. 스프레드시트의 `submit` 필드 형식에 대해 사용자 지정된 감사 메시지를 `value` 열에 추가합니다.

   ![사용자 지정 감사 메시지](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   예를 들어 `submit` 필드 형식에 대해 `value` 열에 `Submission Successful!` 메시지를 추가합니다.

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

   ![사용자 지정 감사 메시지](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## 양식 제출 후 사용자를 다른 페이지로 리디렉션

양식 제출 후 사용자를 다른 페이지로 리디렉션하면 관련 정보를 제공하고, 작업을 확인하고, 사용자가 원하는 결과를 얻도록 유도함으로써 사용자 경험을 향상시킬 수 있습니다. 예:

* 사용자가 구매 양식을 작성하면 사용자는 결제 페이지로 리디렉션되어 거래를 안전하게 완료할 수 있습니다.
* 이벤트나 웨비나용 등록 양식 제출 시 사용자는 날짜, 시간, 위치 등 이벤트 세부 정보를 표시하는 확인 페이지로 리디렉션됩니다.

사용자를 다른 페이지로 리디렉션하려면 아래 단계를 따르십시오.

1. Microsoft SharePoint 또는 Google Workspace의 Edge Delivery 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.
1. 양식 제출 시 사용자를 리디렉션하려면 스프레드시트의 `submit` 필드 형식에 대한 `value` 열에 URL을 붙여 넣으십시오.
페이지를 다른 페이지로 리디렉션하려면 [Edge Delivery 설명서](https://www.aem.live/docs/) 페이지 URL을 사용하십시오.

   ![리디렉션 URL에 감사드립니다](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

   ![감사 메시지 리디렉션](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

새 문서 파일을 만들고 `submit` 필드 형식에 대한 `value` 열에 미리 보기 URL을 추가할 수도 있습니다.

사용자가 양식을 제출한 후 명확한 감사 메시지를 제공하는 것이 중요합니다. 제출 성공 여부를 확인하고 사용자 만족도를 향상시킵니다.

## 추가 참조

{{see-more-forms-eds}}

<!--
## Configuring a custom thank you message

The default behavior of Adaptive Forms Block is to display the following thank you message on submission. The message is displayed on the top of the form. 

![default thank you message](/help/edge/assets/thank-you-message.png)


Follow the below steps to configure a custom thank you message for your Adaptive Forms Block:

1. Access your AEM Project on your local machine or GitHub repository.

2. Navigate to [AEM Project Folder]\blocks\form\submit.js file for editing.

3. Locate the following code 

    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Thanks for your submission';

    ```

4. Replace the default message with your custom message. For example, 


    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Your submission has been received and noted.';

    ```


1. Save the file. Commit the updated file to your GitHub Repository. Now, when you submit a form, the custom thank you message is displayed. For example,

![Custom thank you message](/help/edge/assets/custom-thank-you-message.png)

* **Thank you message**: A thank you message is a cornerstone of user experience, offering reassurance and conveying important information while reinforcing brand identity. It serves as a direct acknowledgment of the user's action, fostering a sense of completion and satisfaction.

* **Redirect**: A redirect plays a pivotal role in steering users towards relevant destinations, optimizing engagement, and ultimately boosting conversion rates. By seamlessly guiding users to the next step in their journey, a redirect ensures a smooth navigation experience. For example, redirecting user to payments page after collecting initial details. 

In the Adaptive Forms Block, the default behavior is to display a thank you message. However, you have the flexibility to tailor this experience to meet your specific needs. Options include:

* [Configuring a custom thank you message to align with your brand and communication goals](#configuring-the-thank-you-page-and-message) 
* [Redirecting users to another page post-submission for further action](#redirect-users-to-another-page-post-submission)

## Redirect users to another page post-submission

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 





1. Access your AEM Edge Delivery project folder on Microsoft SharePoint or Google Workspace.
1. Create a Microsoft Word or Google Docs file named "thankyou" within your project directory.
1. Add your thank you message to the "thankyou" file. </br>
   
    ![Example thank you page](/help/edge/assets/sample-thankyou-page.png) 

1. Use AEM Sidekick to preview and publish the "thankyou" file.

 Your Adaptive Forms Block displays the "thankyou" page on form submission. 

## Redirect users to another page post-submission

By default, the Adaptive Forms Block redirects the users to the "thankyou" page. To redirect users to a page other than the default "thankyou" page, you have two options: 

* [Replace the "thankyou" page with a different page](#replace-the-existing-thankyou-page) 
* [Use website redirects for "thankyou" page redirection](#use-website-redirects-for-thankyou-page-redirection) 

### Replace the "thankyou" page

1. Open the "[EDS Project]/blocks/form/form.js" file for editing.
1. Change the `thankyou` page in the following line to page of your choice:

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'thankyou';

    ```

    For example,

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'payment';
        
    ```
    
    >[!NOTE]
    >
    > Ensure that a page with the same name exists in your Edge Delivery Services project folder on either Microsoft SharePoint or Google Workspace. If the page does not exist, proceed to create and publish it.  

1. Proceed to check in the updated 'form.js' folder and its underlying files to your Edge Delivery Services project on GitHub. This update ensures that the form now redirects to the updated page as specified.

1. Ensure that the page exists in your EDS project folder and publish it.


### Use website redirects for "thankyou" page redirection

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 



## See also

{{see-more-forms-eds}}