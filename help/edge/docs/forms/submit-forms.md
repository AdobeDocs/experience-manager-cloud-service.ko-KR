---
title: 데이터를 허용하도록 스프레드시트 준비
description: 스프레드시트 및 양식 블록 필드를 사용하여 강력한 양식을 더 빨리 만드십시오!
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: bd8c4fbfd7f740baa6abd7a91fb8d1dcdaff6c28
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 61%

---


# 데이터를 허용하도록 스프레드시트 준비

다음 작업을 완료하면 [양식을 만들고 미리보기](/help/edge/docs/forms/create-forms.md)해당 스프레드시트가 데이터 수신을 시작할 수 있도록 활성화해야 합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

스프레드시트를 활성화하려면 다음을 수행합니다.

1. 양식이 있는 스프레드시트를 열고 새 시트를 추가하고 이름을 로 변경합니다. `incoming`.

   >[!WARNING]
   >
   > 다음과 같은 경우 `incoming` 시트가 없으면 AEM에서 데이터를 스프레드시트로 보내지 않습니다.

1. 양식 필드 이름, 값 대칭복사 `Name` 열의`shared-default` 시트, 머리글에 추가 `incoming` 시트.

   의 각 값 `Name` 열 `shared-default` 제출 단추를 제외한 시트는에서 머리글 역할을 합니다. `incoming` 시트. 예를 들어 &quot;contact-us&quot; 양식의 헤더를 보여 주는 다음 이미지를 생각해 보십시오.

   ![contact-us 양식의 필드](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. 사이드 킥을 사용하여 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 보았더라도 를 생성한 후 다시 미리 보아야 합니다 `incoming` 첫 번째 시트입니다.


필드 이름이 추가되면 `incoming` 시트, 양식을 제출할 준비가 되었습니다. 양식을 미리 보고 이를 사용하여 시트에 데이터를 제출할 수 있습니다.

스프레드시트에서 다음 변경 사항도 관찰할 수 있습니다.

“Slack”이라는 시트가 Excel 통합 문서 또는 Google 시트에 추가됩니다. 이 시트에서는 새 데이터가 스프레드시트에 수집될 때마다 지정된 Slack 채널에 대한 자동 알림을 구성할 수 있습니다. 현재 AEM은 AEM Engineering Slack 조직 및 Adobe Enterprise Support 조직에만 알림을 지원합니다.

1. Slack 알림을 설정하려면 Slack 작업 영역의 “teamId”와 “채널 이름” 또는 “ID”를 입력합니다. 디버그 명령을 사용하여 slack-bot에 “teamId” 및 “채널 ID”를 요청할 수도 있습니다. “채널 이름” 대신 “채널 ID”를 사용하는 것이 채널 이름을 변경해도 유지되므로 더 이상적입니다.

   >[!NOTE]
   >
   > 이전 양식에는 “teamId” 열이 없었습니다. “teamId”는 “#” 또는 “/”로 구분된 채널 열에 포함되어 있었습니다.

1. 원하는 제목을 입력하고 필드 아래에 Slack 알림에 표시할 필드 이름을 입력합니다. 각 제목은 쉼표로 구분되어야 합니다(예: 이름, 이메일).

   >[!WARNING]
   >
   >  “shared-default” 시트에는 공개적으로 액세스 가능해서는 안 되는 개인 식별 정보나 민감한 데이터가 포함되어서는 안 됩니다.


## (선택 사항) 스프레드시트가 데이터를 수용할 수 있도록 하려면 관리 API를 사용하십시오

양식에 POST 요청을 전송하여 데이터를 승인하고 의 헤더를 구성할 수도 있습니다. `incoming` 시트. POST 요청을 받으면 서비스는 요청 본문을 분석하고 데이터 수집에 필요한 필수 헤더와 시트를 자체적으로 생성합니다.

Admin API를 사용하여 스프레드시트에서 데이터를 허용하도록 설정하려면 다음 작업을 수행하십시오.


1. 만든 통합 문서를 열고 기본 시트의 이름을 로 변경합니다. `incoming`.

   >[!WARNING]
   >
   > 다음과 같은 경우 `incoming` 시트가 없습니다. AEM이 이 통합 문서에 데이터를 전송하지 않습니다.

1. 사이드 킥에서 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 보았더라도 를 생성한 후 다시 미리 보아야 합니다 `incoming` 첫 번째 시트입니다.

1. 에서 적절한 헤더를 생성하도록 POST 요청을 보냅니다. `incoming` 시트 및 추가 `shared-default` 시트가 아직 없는 경우 스프레드 시트에 추가합니다.

   시트 설정을 위해 POST 요청 형식을 지정하는 방법을 이해하려면 [Admin API 설명서](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile)를 참조하십시오. 아래에 제공된 예제를 볼 수 있습니다.

   **요청**

   ```JSON
   POST 'https://admin.hlx.page/form/{owner}/{repo}/{branch}/contact-us.json' \
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
   curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

   위에서 언급한 POST 요청은 양식 필드와 각 샘플 값을 모두 포함하는 샘플 데이터를 제공합니다. 이 데이터는 관리 서비스에서 양식을 설정하는 데 사용됩니다.

   이제 양식을 사용하여 데이터를 수락할 수 있습니다. 스프레드시트에서 다음 변경 사항도 관찰할 수 있습니다.

“Slack”이라는 시트가 Excel 통합 문서 또는 Google 시트에 추가됩니다. 이 시트에서는 새 데이터가 스프레드시트에 수집될 때마다 지정된 Slack 채널에 대한 자동 알림을 구성할 수 있습니다. 현재 AEM은 AEM Engineering Slack 조직 및 Adobe Enterprise Support 조직에만 알림을 지원합니다.

1. Slack 알림을 설정하려면 Slack 작업 영역의 “teamId”와 “채널 이름” 또는 “ID”를 입력합니다. 디버그 명령을 사용하여 slack-bot에 “teamId” 및 “채널 ID”를 요청할 수도 있습니다. “채널 이름” 대신 “채널 ID”를 사용하는 것이 채널 이름을 변경해도 유지되므로 더 이상적입니다.

   >[!NOTE]
   >
   > 이전 양식에는 “teamId” 열이 없었습니다. “teamId”는 “#” 또는 “/”로 구분된 채널 열에 포함되어 있었습니다.

1. 원하는 제목을 입력하고 필드 아래에 Slack 알림에 표시할 필드 이름을 입력합니다. 각 제목은 쉼표로 구분되어야 합니다(예: 이름, 이메일).


이제 시트가 데이터를 수신하도록 설정되었으며, [양식 블록을 사용하여 양식을 미리 보거나](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page)  [POST 요청을 사용](#use-admin-apis-to-send-data-to-your-sheet)하여 시트로 데이터 전송을 시작할 수 있습니다.

>[!WARNING]
>
>  “shared-default” 시트에는 공개적으로 액세스 가능해서는 안 되는 개인 식별 정보나 민감한 데이터가 포함되어서는 안 됩니다.

## 시트로 데이터 전송 {#send-data-to-your-sheet}

데이터를 수신하도록 시트를 설정한 후 [양식 블록을 사용하여 양식을 미리 보거나](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page)  [Admin API를 사용](#use-admin-apis-to-send-data-to-your-sheet)하여 시트로 데이터 전송을 시작할 수 있습니다.

### Admin API를 사용하여 시트에 데이터 전송

hlx.page, hlx.live 또는 프로덕션 도메인을 사용하여 양식에 직접 POST 요청을 보내 데이터를 전송할 수 있습니다.


```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> URL에는 .json 확장자가 없어야 합니다. `.live` 또는 프로덕션 도메인에서 작동하려면 POST 작업에 대한 시트를 게시해야 합니다.

#### 양식 데이터 형식 지정

POST 본문에서 양식 데이터의 형식을 지정할 수 있는 몇 가지 방법이 있습니다. 다음과 같은 기능을 사용할 수 있습니다.

* `name:value` 쌍의 배열:

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

  예

  ```JSON
  curl -s -i -X POST 'https://main--portal--wkndforms.hlx.page/contact-us' \
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



* `key:value` 쌍이 있는 오브젝트:

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

  예:

  ```JSON
  curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

* URL 인코딩(`x-www-form-urlencoded`) 본문(`content-type` 헤더가 `application/x-www-form-urlencoded`로 설정됨)

  ```Shell
  'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'
  ```

  예:

  ```Shell
  curl -s -i -X POST \
    -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
    https://main--portal--wkndforms.hlx.live/contact-us
  ```

다음으로 감사 메시지를 사용자 지정할 수 있습니다. [감사 페이지 구성](/help/edge/docs/forms/thank-you-page-form.md), 또는 [리디렉션 설정](/help/edge/docs/forms/thank-you-page-form.md).

## 더 보기

* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [양식을 활성화하여 데이터 전송](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-eds-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [양식의 테마 및 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)