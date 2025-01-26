---
title: 데이터를 수신할 스프레드시트 준비
description: 스프레드시트 및 적응형 양식 블록 필드를 사용하여 강력한 양식을 더 빠르게 작성할 수 있습니다.
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: ae31df22c723c58addd13485259e92abb4d4ad54
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 79%

---

# Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수신 시작


[양식을 만들고 미리 보기](/help/edge/docs/forms/create-forms.md)했으면 해당 스프레드시트가 데이터 수신을 시작할 수 있도록 설정해야 합니다. 다음을 수행할 수 있습니다.

* [데이터를 수락하도록 스프레드시트를 수동으로 활성화](#manually-enable-the-spreadsheet-to-accept-data)
* [Admin API를 사용하여 스프레드시트에서 데이터를 허용하도록 설정](#use-admin-apis-to-enable-a-spreadsheet-to-accept-data)

![문서 기반 작성 생태계](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)


<!--

>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->

[Forms 제출 서비스를 수동으로 구성](#configuring-the-forms-submission-service-manually)하거나 [API를 사용하여 Forms 제출 서비스를 구성](#configuring-the-forms-submission-service-using-api)할 수 있습니다.


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


## Admin API를 사용하여 스프레드시트에서 데이터를 허용하도록 설정

양식에 POST 요청을 보내 양식이 데이터를 받아들이고 `incoming` 시트의 헤더를 구성할 수 있도록 할 수도 있습니다. POST 요청을 받으면 서비스는 요청 본문을 분석하고 데이터 수집에 필요한 필수 헤더와 시트를 자동으로 생성합니다.

Admin API를 사용하여 스프레드시트에서 데이터를 수신하도록 설정하려면 다음 작업을 수행하십시오.


1. 만든 통합 문서를 열고 기본 시트의 이름을 `incoming`으로 변경합니다.

   >[!WARNING]
   >
   > `incoming` 시트가 존재하지 않는 경우 AEM은 이 통합 문서에 데이터를 전송하지 않습니다.

1. Sidekick에서 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 본 적이 있더라도 처음으로 `incoming` 시트를 만든 후에는 다시 미리보기로 확인해야 합니다.

1. `incoming` 시트에 적절한 헤더를 생성하도록 POST 요청을 보내고 시트가 아직 존재하지 않는 경우 스프레드시트에 `shared-default` 시트를 추가합니다.

   시트 설정을 위해 POST 요청 형식을 지정하는 방법을 이해하려면 [Admin API 설명서](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile)를 참조하십시오. 아래 제공된 예를 살펴볼 수도 있습니다.

   **요청**

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


   **응답**

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

   아래와 같이 curl이나 Postman과 같은 도구를 사용하여 이 POST 요청을 실행할 수 있습니다.

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

   위에서 언급한 POST 요청은 양식 필드와 해당 샘플 값을 모두 포함하는 샘플 데이터를 제공합니다. 이 데이터는 관리 서비스에서 양식을 설정하는 데 사용됩니다.

   이제 양식이 데이터를 수신할 수 있습니다. 또한 스프레드시트에서 다음과 같은 변경 내용을 확인할 수 있습니다.

## 데이터를 수락하도록 활성화되면 시트가 자동으로 변경됩니다.

시트가 데이터를 수신하도록 설정되면 스프레드시트에서 다음과 같은 변경 사항을 확인할 수 있습니다.

“Slack”이라는 시트가 Excel 통합 문서 또는 Google 시트에 추가됩니다. 이 시트에서는 새 데이터가 스프레드시트에 수집될 때마다 지정된 Slack 채널에 대한 자동 알림을 구성할 수 있습니다. 현재 AEM은 AEM Engineering Slack 조직 및 Adobe Enterprise Support 조직에만 알림을 지원합니다.

1. Slack 알림을 설정하려면 Slack 작업 영역의 “teamId”와 “채널 이름” 또는 “ID”를 입력합니다. 디버그 명령을 사용하여 slack-bot에 “teamId” 및 “채널 ID”를 요청할 수도 있습니다. “채널 이름” 대신 “채널 ID”를 사용하는 것이 채널 이름을 변경해도 유지되므로 더 이상적입니다.

   >[!NOTE]
   >
   > 이전 양식에는 “teamId” 열이 없었습니다. “teamId”는 “#” 또는 “/”로 구분된 채널 열에 포함되어 있었습니다.

1. 원하는 제목을 입력하고 필드 아래에 Slack 알림에 표시할 필드 이름을 입력합니다. 각 제목은 쉼표로 구분되어야 합니다(예: 이름, 이메일).

   >[!WARNING]
   >
   >  “shared-default” 시트에는 공개적으로 액세스 가능해서는 안 되는 개인 식별 정보나 민감한 데이터가 포함되어서는 안 됩니다.



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
