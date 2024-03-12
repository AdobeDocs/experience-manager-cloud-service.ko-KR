---
title: 양식 제출 후 사용자 정의 감사 메시지 표시
description: 양식 블록에 대한 감사 페이지와 리디렉션을 구성하여 사용자 경험을 최적화하고 사용자 여정을 간소화하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
source-git-commit: 6d4b194d17cc27a6a8596825401dc723bebe7b27
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 13%

---

# 양식 제출 후 사용자 정의 감사 메시지 표시

사용자가 양식을 제출한 후 감사 메시지를 통해 원활한 경험을 제공하는 것이 중요합니다. 이는 성공적인 제출을 확인해줄 뿐만 아니라, 사용자의 만족도를 높이고 여정에서 이를 더욱 안내한다.

## 사용자 정의 감사 메시지 구성

적응형 Forms 블록의 기본 동작은 제출 시 다음과 같은 감사 메시지를 표시하는 것입니다. 메시지가 양식 맨 위에 표시됩니다.

![기본 감사 메시지](/help/edge/assets/thank-you-message.png)


적응형 Forms 블록에 대한 사용자 정의 감사 메시지를 구성하려면 아래 단계를 따르십시오.

1. 로컬 컴퓨터 또는 GitHub 저장소에서 AEM 프로젝트에 액세스합니다.

1. 다음으로 이동 [AEM 프로젝트 폴더]편집할 \blocks\form\submit.js 파일입니다.

1. 다음 코드를 찾습니다

   ```JavaScript
       thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Thanks for your submission';
   ```

1. 기본 메시지를 사용자 지정 메시지로 바꿉니다. 예:


   ```JavaScript
       thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Your submission has been received and noted.';
   ```


1. 파일을 저장합니다. 업데이트된 파일을 GitHub 저장소에 커밋합니다. 이제 양식을 제출할 때 사용자 정의 감사 메시지가 표시됩니다. 예:

![사용자 정의 감사 메시지](/help/edge/assets/custom-thank-you-message.png)

<!-- 

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

-->

## 참고 항목

{{see-more-forms-eds}}