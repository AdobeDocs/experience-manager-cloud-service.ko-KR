---
title: 데이터를 수신할 스프레드시트 준비
description: 스프레드시트 및 적응형 양식 블록 필드를 사용하여 강력한 양식을 더 빠르게 작성할 수 있습니다.
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: 64a8b363cff079aa0a6f56effd77830ac797deca
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 65%

---

# Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수신 시작


[양식을 만들고 미리 보기](/help/edge/docs/forms/create-forms.md)했으면 해당 스프레드시트가 데이터 수신을 시작할 수 있도록 설정해야 합니다. 스프레드시트가 데이터를 수신하도록 수동으로 활성화하거나, 관리 API를 사용하여 스프레드시트가 데이터를 수신하도록 활성화할 수 있습니다.

![문서 기반 작성 생태계](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)


>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)



## 데이터를 수신하도록 스프레드시트를 수동으로 활성화

데이터를 수신하도록 스프레드시트를 활성화하는 방법

1. 폼이 있는 스프레드시트를 열고 새 시트를 추가하고 이름을 `incoming`(으)로 변경합니다. 예를 들어, [조회](/help/edge/assets/enquiry.xlsx) 양식은 Microsoft Excel 통합 문서입니다.

   >[!WARNING]
   >
   > `incoming` 시트가 없는 경우 AEM은 스프레드시트에 데이터를 보내지 않습니다.

1. 이 시트에 “intake_form”이라는 테이블을 삽입합니다. 양식 필드 이름과 일치하는 데 필요한 열 수를 선택합니다. 그런 다음 도구 모음에서 삽입 > 테이블로 이동하고 ‘확인’을 클릭합니다.

1. 테이블 이름을 “intake_form”으로 변경합니다. Microsoft Excel에서 테이블 이름을 변경하려면 테이블을 선택하고 테이블 디자인을 클릭합니다.

1. 다음으로 양식 필드 이름을 테이블 헤더로 추가합니다. 필드가 정확하게 동일한지 확인하기 위해 &quot;shared-aem&quot; 시트에서 필드를 복사하여 붙여넣을 수 있습니다.  &quot;shared-aem&quot; 시트에서 &quot;Name&quot; 열 아래에 나열된 양식 ID를 선택하고 복사합니다. 단, 제출 필드는 예외입니다.

1. “incoming” 시트에서 선택하여 붙여넣기 > 행을 열로 바꾸기를 선택하여 필드 ID를 이 새 시트의 열 헤더로 복사합니다. 데이터를 캡처해야 하는 필드만 유지합니다. 다른 필드는 무시할 수 있습니다.

   제출 버튼을 제외한 `shared-aem` 시트의 각 `Name` 열 값은 `incoming` 시트에서 헤더 역할을 할 수 있습니다. 예를 들어 &quot;조회&quot; 양식의 헤더를 보여 주는 다음 이미지를 생각해 보십시오.

   ![문의 양식의 필드](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) 확장을 사용하여 양식 업데이트를 미리 봅니다. 이제 시트가 수신 양식 제출을 수락할 준비가 되었습니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 본 적이 있더라도 처음으로 `incoming` 시트를 만든 후에는 다시 미리보기로 확인해야 합니다.


필드 이름이 `incoming` 시트에 추가되면 양식 제출을 수락할 준비가 됩니다. 양식을 미리 보고 이를 사용하여 시트에 데이터를 제출할 수 있습니다.

데이터를 수신하도록 시트가 설정되면 [양식을 미리 볼 수 있습니다](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) <!--or [use POST requests](#use-admin-apis-to-send-data-to-your-sheet)--> 데이터를 시트에 보내기 시작할 수 있습니다.

>[!WARNING]
>
>  &quot;공유 aem&quot; 시트에는 공개적으로 액세스하는 데 익숙하지 않은 개인 식별 정보나 중요한 데이터가 포함되어서는 안 됩니다.

<!--
### Use Admin APIs to enable a spreadsheet to accept data

You can also send a POST request to the form to enable it to accept data and configure headers for the `incoming` sheet. Upon receiving the POST request, the service analyzes the body of request and autonomously generates the essential headers and sheets needed for data ingestion.

To use Admin APIs to enable a spreadsheet to accept data: 


1. Open the workbook that you have created and change the name of the default sheet to `incoming`. 

    >[!WARNING] 
    >
    > If the `incoming` sheet doesn't exist, AEM won't send any data to this workbook.

1. Preview the sheet in the sidekick.

    >[!NOTE] 
    >
    >Even if you have previewed the sheet before, you must preview it again after creating the `incoming` sheet for the first time.

1. Send the POST request to generate the appropriate headers in the `incoming` sheet, and add the `shared-default` sheets to your spread sheet, if it does not exist already.

    To understand how to format the POST request for setting up your sheet, refer to the [Admin API documentation](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). You can look at the example provided below: 

    **Request** 
    
    ```JSON

    POST 'https://admin.aem.page/form/{owner}/{repo}/{branch}/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "john@wknd.com",
            "Name": "John",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```


    **Response**

    ```JSON

    HTTP/2 200 
    content-type: application/json
    x-invocation-id: 1b3bd30a-8cfb-4f85-a662-4b1f7cf367c5
    cache-control: no-store, private, must-revalidate
    accept-ranges: bytes
    date: Sat, 10 Feb 2024 09:26:48 GMT
    via: 1.1 varnish
    x-served-by: cache-del21736-DEL
    x-cache: MISS
    x-cache-hits: 0
    x-timer: S1707557205.094883,VS0,VE3799
    strict-transport-security: max-age=31557600
    content-length: 138

    {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country",      "PreferredContactMethod","SubscribeToNewsletter"]}%

    ```

    You can use tools like curl or Postman to execute this POST request, as demonstrated below:

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
        --header 'Content-Type: application/json' \
        --data '{
            "data": {
                "Email": "john@wknd.com",
                "Name": "John",
                "Subject": "Regarding Product Inquiry",
                "Message": "I have some questions about your products.",
                "Phone": "123-456-7890",
                "Company": "Wknd Inc.",
                "Country": "United States",
                "PreferredContactMethod": "Email",
                "SubscribeToNewsletter": true
        }
    }'

    ```

    The above mentioned POST request provides sample data, including both form fields and their respective sample values. This data is used by the Admin service to set up the form.

    Your form is now enabled to accept data. You also observe the following changes in your spreadsheet: 

## Automatic changes to sheet once it is enabled to accept data. 

Once the sheet is set to recieve data, you observe the following changes in your spreadsheet: 

A sheet named "Slack" is added to your Excel Workbook or Google Sheet. In this sheet, you can configure automatic notifications for a designated Slack channel whenever new data is ingested into your spreadsheet. At present, AEM supports notifications exclusively to the AEM Engineering Slack organization and the Adobe Enterprise Support organization.

1. To set up Slack notifications enter the "teamId" of the Slack workspace and the "channel name" or "ID". You can also ask the slack-bot (with the debug command) for the "teamId" and the "channel ID". Using the "channel ID" instead of the "channel name" is preferable, as it survives channel renames.

    >[!NOTE] 
    >
    > Older forms didn't have the "teamId" column. The "teamId" was included in the channel column, separated by a "#" or "/".

1. Enter any title that you want and under fields enter the names of the fields you want to see in the Slack notification. Each heading should be separated by a comma (For example name, email).

    >[!WARNING] 
    >
    >  Never should the "shared-default" sheets contain any personally identifiable information or sensitive data that you are not comfortable with being publicly accessible.



<!--
## Send data to your sheet {#send-data-to-your-sheet}

After the sheet is set to receive data, you can [preview the form using Adaptive Forms Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) or [use Admin APIs](#use-admin-apis-to-send-data-to-your-sheet) to start sending data to the sheet.

### Use Admin APIs to send data to your sheet

You can send POST requests directly to your form using aem.page, aem.live, or your production domain, to send data. 


```JSON

POST https://branch–repo–owner.aem.(page|live)/email-form
POST https://my-domain.com/email-form

```

>[!NOTE] 
>
> The URL should not have the .json extension. You must publish the sheet for POST operations to function on `.live` or on the production domain.

#### Formatting the form data

There are a few different ways that you can format the form data in the POST body. You can use: 

* array of `name:value` pairs: 
    
    ```JSON
    
    {
      "data": [
        { "name": "name", "value": "Clark Kent" },
        { "name": "email", "value": "superman@example.com" },
        { "name": "subject", "value": "Regarding Product Inquiry" },
        { "name": "message", "value": "I have some questions about your products." },
        { "name": "phone", "value": "123-456-7890" },
        { "name": "company", "value": "Example Inc." },
        { "name": "country", "value": "United States" },
        { "name": "preferred_contact_method", "value": "Email" },
        { "name": "newsletter_subscribe", "value": true }
      ]
    }

    ```

    For example

    ```JSON

    curl -s -i -X POST 'https://main--wefinance--wkndform.aem.page/contact-us' \
        --header 'Content-Type: application/json' \
        --data '{
        "data": [
            { "name": "name", "value": "Clark Kent" },
            { "name": "email", "value": "superman@example.com" },
            { "name": "subject", "value": "Regarding Product Inquiry" },
            { "name": "message", "value": "I have some questions about your        products." },
            { "name": "phone", "value": "123-456-7890" },
            { "name": "company", "value": "Example Inc." },
            { "name": "country", "value": "United States" },
            { "name": "preferred_contact_method", "value": "Email" },
            { "name": "newsletter_subscribe", "value": true }
        ]
    }'

    ```



* an object with `key:value` pairs:

    ```JSON

        {
          "data": {
            "name": "Jessica Jones",
            "email": "jj@example.com",
            "subject": "Regarding Product Inquiry",
            "message": "I have some questions about your products.",
            "phone": "123-456-7890",
            "company": "Example Inc.",
            "country": "United States",
            "preferred_contact_method": "Email",
            "newsletter_subscribe": true
          }
        }

    ```

    For example,

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "khushwant@wknd.com",
            "Name": "khushwant",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```

* URL encoded (`x-www-form-urlencoded`) body (with `content-type` header set to `application/x-www-form-urlencoded`)

    ```Shell

    'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'

    ```

    For example, if your project's repository is named "wefinance", it's located under the account owner "wkndform", and you're using the "main" branch.,

    ```Shell

    curl -s -i -X POST \
      -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
      https://main--wefinance--wkndform.aem.live/contact-us

    ```
-->

다음으로, [감사 메시지를 사용자 정의](/help/edge/docs/forms/thank-you-page-form.md)할 수 있습니다.

## 추가 참조

{{see-more-forms-eds}}
