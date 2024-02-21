---
title: 스프레드시트에서 Forms으로 - 양식 블록 필드 유효성 검사 마스터하기
description: 스프레드시트 및 양식 블록 필드를 사용하여 강력한 양식을 더 빨리 만드십시오! 이 안내서는 EDS Forms 블록 필드에 대한 사용자 지정 유효성 검사를 작성하는 데 도움이 됩니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---


# 양식을 활성화하여 데이터 보내기

양식을 만들고 미리 본 후 해당 시트를 활성화하여 데이터를 적용합니다. 데이터 수신을 시작하려면 수집하려는 데이터와 일치하는 헤더를 포함하도록 스프레드시트를 설정합니다. &#39;shared-default&#39; 시트에 추가된 모든 헤더는 표 아래의 &#39;incoming&#39; 시트에도 있어야 합니다.

다음 예제에서는 &quot;contact-us&quot; 양식에 대한 필드를 표시합니다.

![담당자 양식 필드](/help/edge/assets/contact-us-form-excel-sheet-fields.png)


이 설정이 완료되면 양식에서 제출을 수락할 수 있습니다. 다음 방법 중 하나를 사용하여 스프레드시트가 데이터를 수락하도록 할 수 있습니다.

* [데이터를 허용하도록 스프레드시트 수동 구성](#manually-configure-a-spreadsheet-to-receive-data)

* [스프레드시트가 데이터를 수락하도록 하려면 관리 API를 사용하십시오](#use-admin-apis-to-enable-a-spreadsheet-to-receive-data-use-admin-apis-to-enable-a-spreadsheet-to-recieve-data)

## 데이터를 허용하도록 스프레드시트 수동 구성

데이터를 허용하도록 스프레드시트를 수동으로 구성하려면 다음을 수행합니다.


1. 만든 통합 문서를 열고 기본 시트의 이름을 &quot;수신&quot;으로 변경합니다.

   >[!WARNING]
   >
   > 받는 시트가 없으면 AEM에서 이 통합 문서로 데이터를 전송하지 않습니다.

1. 입력하는 데이터와 일치하는 헤더를 추가하여 시트를 준비합니다. 다음 예제에서는 &quot;contact-us&quot; 양식에 대한 필드를 표시합니다.

   ![담당자 양식 필드](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. 사이드 킥에서 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 본 적이 있더라도 &quot;가져오는&quot; 시트를 처음 만든 후 다시 미리 보아야 합니다.


## 스프레드시트가 데이터를 수락하도록 하려면 관리 API를 사용하십시오

AEM Admin Service 내에서 양식 경로에 대한 POST 요청을 시작할 수 있습니다. POST 본문 데이터가 수신되면 관리 서비스가 이를 분석하고 데이터 수집에 필요한 필수 헤더, 테이블 및 시트를 자체적으로 생성하여 양식 서비스의 기능을 최적화합니다.

관리 API를 사용하여 스프레드시트가 데이터를 수락할 수 있도록 하려면 다음을 수행합니다.


1. 만든 통합 문서를 열고 기본 시트의 이름을 &quot;수신&quot;으로 변경합니다.

   >[!WARNING]
   >
   > 받는 시트가 없으면 AEM에서 이 통합 문서로 데이터를 전송하지 않습니다.

1. 사이드 킥에서 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 본 적이 있더라도 &quot;가져오는&quot; 시트를 처음 만든 후 다시 미리 보아야 합니다.

1. 입력하는 데이터와 일치하는 헤더를 추가하여 시트를 준비합니다.

   이 작업은 AEM Admin Service의 양식 경로로 POST 요청을 전송하여 수행할 수 있습니다. 관리 서비스는 POST 본문의 데이터를 검사하고 데이터를 효과적으로 수집하고 Forms 서비스를 최대한 활용하는 데 필요한 적절한 헤더, 테이블 및 시트를 생성합니다.

   시트 설정을 위한 POST 요청 서식을 지정하는 방법을 이해하려면 [관리 API 설명서](https://www.hlx.live/docs/admin.html#tag/form). 또한 아래에 제공된 예제를 참조하십시오.

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

   아래와 같이 curl 또는 Postman과 같은 도구를 사용하여 이 POST 요청을 실행할 수 있습니다.

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

   앞에서 언급한 POST 요청은 양식 필드와 각 샘플 값을 모두 포함하는 샘플 데이터를 제공합니다. 이 데이터는 Admin Service에서 양식을 설정하는 데 사용됩니다.

   Admin Service에 POST 요청을 제출하면 통합 문서에 다음과 같은 변경 사항이 표시됩니다.

* 이름이 &quot;shared-default&quot;인 새 시트가 Excel 통합 문서나 Google 시트에 추가됩니다. &quot;shared-default&quot; 시트에 있는 데이터는 시트에 대한 GET 요청 시 검색됩니다. 이 시트는 스프레드시트 공식을 사용하여 수신 데이터를 요약하기에 최적의 위치 역할을 하므로 다른 컨텍스트에서 사용하기에 좋습니다.

  &quot;공유 기본값&quot; 시트에는 공개적으로 액세스할 수 없는 개인 식별 정보나 중요한 데이터가 포함되어서는 안 됩니다.

* 이름이 &quot;Slack&quot;인 시트가 Excel 통합 문서나 Google 시트에 추가됩니다. 이 시트에서 스프레드시트로 새 데이터가 수집될 때마다 지정된 Slack 채널에 대한 자동 알림을 구성할 수 있습니다. 현재 AEM은 AEM Engineering Slack 조직 및 Adobe 엔터프라이즈 지원 조직에만 통지를 지원합니다.

   1. Slack 알림을 설정하려면 Slack 작업 영역의 &quot;teamId&quot;와 &quot;채널 이름&quot; 또는 &quot;ID&quot;를 입력합니다. debug 명령을 사용하는 slack-bot에 &quot;teamId&quot; 및 &quot;channel ID&quot;를 요청할 수도 있습니다. 채널 이름 대신 &quot;채널 ID&quot;를 사용하는 것이 좋습니다. 채널 이름은 계속 변경되기 때문입니다.

      >[!NOTE]
      >
      > 이전 양식에는 &quot;teamId&quot; 열이 없습니다. &quot;teamId&quot;가 채널 열에 포함되었으며, &quot;#&quot; 또는 &quot;/&quot;로 구분되었습니다.

   1. 원하는 제목을 입력하고 필드 아래에 Slack 알림에 표시할 필드 이름을 입력합니다. 각 제목은 쉼표로 구분해야 합니다(예: 이름, 이메일).

이제 데이터를 수신하도록 시트가 설정되어 있습니다. 다음을 수행할 수 있습니다. [양식 블록을 사용하여 양식 미리 보기](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) 또는 [POST 요청 사용](#use-admin-apis-to-send-data-to-your-sheet) 데이터를 시트로 보내기 시작합니다.



## 시트에 데이터 보내기 {#send-data-to-your-sheet}

시트가 데이터를 수신하도록 설정되면 다음 작업을 수행할 수 있습니다 [양식 블록을 사용하여 양식 미리 보기](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) 또는 [관리 API 사용](#use-admin-apis-to-send-data-to-your-sheet) 데이터를 시트로 보내기 시작합니다.

### 관리 API를 사용하여 시트로 데이터 보내기

hlx.page, hlx.live 또는 프로덕션 도메인을 사용하여 양식에 직접 POST 요청을 전송하여 데이터를 보낼 수 있습니다.


```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> URL에는 .json 확장명이 없어야 합니다. POST 작업이 작동하려면 시트를 게시해야 합니다. `.live` 또는 프로덕션 도메인에서

#### 양식 데이터 서식 지정

POST 본문에서 양식 데이터의 서식을 지정할 수 있는 방법에는 몇 가지가 있습니다. 다음과 같은 기능을 사용할 수 있습니다.

* 배열 `name:value` 쌍:

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



* 이 있는 오브젝트 `key:value` 쌍:

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

* URL 인코딩됨(`x-www-form-urlencoded`) 본문(포함 `content-type` 헤더 설정 `application/x-www-form-urlencoded`)

  ```Shell
  'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'
  ```

  예:

  ```Shell
  curl -s -i -X POST \
    -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
    https://main--portal--wkndforms.hlx.live/contact-us
  ```

다음으로, 사용자 메시지를 사용자 지정할 수 있습니다. [감사 페이지 구성](/help/edge/docs/forms/thank-you-page-form.md), 또는 [리디렉션 설정](/help/edge/docs/forms/thank-you-page-form.md).

## 더 보기

* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [데이터를 전송할 양식 활성화](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-eds-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [테마 및 양식 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)