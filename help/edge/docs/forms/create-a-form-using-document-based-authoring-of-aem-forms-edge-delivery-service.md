---
title: AEM Forms Edge Delivery Service용 문서 기반 작성을 사용하여 양식 만들기
description: 완벽한 형태를 만들어, 빨리! ⚡ AEM Forms Edge Delivery + doc 기반 작성 = 더 행복한 사용자 및 검색 엔진을 위한 놀라운 속도 및 SEO 친화적인 양식.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: f2752673dcaa0762bb55719cee23765aa8ecde96
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---


# AEM Forms Edge Delivery Service용 문서 기반 작성을 사용하여 양식 만들기

오늘날 디지털 시대에서는 모든 조직에 사용자 친화적인 양식을 만드는 것이 필수적입니다. AEM Forms Edge Delivery의 문서 기반 작성을 통해 Word 또는 Google Docs와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다. 이러한 양식은 Microsoft Excel 또는 Google Sheets 파일에 직접 데이터를 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft Sharepoint의 강력한 API와 생생한 에코시스템을 사용하여 제출된 데이터를 쉽게 처리하거나 기존 비즈니스 워크플로우를 시작할 수 있습니다.

이 안내서에서는 다음 사항을 안내합니다.

* 스프레드시트 준비: 데이터 수집을 위해 Excel 또는 Google Sheets 파일을 설정하고 여기에 양식 필드를 추가하는 방법을 알아봅니다.
* 시트에 데이터 보내기: POST 요청을 사용하여 시트에 데이터를 보내는 방법에 대해 알아봅니다.
* 양식 게시: 양식을 AEM Sites 페이지에 통합하거나 독립 실행형 페이지로 게시합니다.

초보자든 프로든 이 안내서를 통해 사용자가 좋아하는 아름답고 기능적인 양식을 작성할 수 있습니다. 효율적인 양식 생성을 시작하겠습니다. 지금 바로 사용해 보십시오!

## 시작하기 전

`WIP`

## 데이터를 받을 스프레드시트 준비

1. Microsoft OneDrive 또는 Google Drive의 AEM Edge 배달 프로젝트 디렉터리 아래 아무 곳에나 Microsoft Excel 통합 문서 또는 Google 시트를 만듭니다. 이 문서에서는 이름이 인 Google 시트를 사용합니다. `contact-us.xlsx`: Adobe Experience Manager(AEM) 프로젝트의 루트에 있습니다.

1. 프로젝트에 대해 구성된 AEM 사용자(예: helix@adobe.com)에게 시트에 대한 편집 권한이 있는지 확인합니다.

1. 만든 통합 문서를 열고 기본 시트의 이름을 &quot;수신&quot;으로 변경합니다.

   >[!NOTE]
   >
   > 받는 시트가 없으면 AEM에서 이 통합 문서로 데이터를 전송하지 않습니다.

1. 사이드 킥에서 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 본 적이 있더라도 &quot;가져오는&quot; 시트를 처음 만든 후 다시 미리 보아야 합니다.

1. 입력하는 데이터와 일치하는 헤더를 추가하여 시트를 준비합니다. 다음 예제에서는 &quot;contact-us&quot; 양식에 대한 필드를 표시합니다.

   ![담당자 양식 필드](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   이 작업은 수동으로 또는 AEM Admin Service에서 양식 경로에 대한 POST 요청을 사용하여 수행할 수 있습니다. Admin Service는 POST 본문의 데이터를 검사하고 데이터를 효과적으로 수집하고 Forms 서비스를 최대한 활용하는 데 필요한 적절한 헤더, 테이블 및 시트를 생성합니다.

   시트 설정을 위한 POST 요청 서식을 지정하는 방법을 이해하려면 [관리 API 설명서](https://www.hlx.live/docs/admin.html#tag/form). 또한 아래에 제공된 예제를 살펴보십시오.

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
   
   {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country","PreferredContactMethod","SubscribeToNewsletter"]}%
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

앞서 언급한 POST 요청은 양식 필드 및 해당 샘플 값을 모두 포함하는 샘플 데이터를 제공합니다. 이 데이터는 Admin Service에서 양식 설정에 사용됩니다.

시트를 구성하는 데 Admin Service가 권장되지만 헤더를 수동으로 만들려면 제목이 있는 문서를 참조하십시오 [수동 Forms 시트 설정](https://www.hlx.live/docs/manual-forms-sheet-setup).

Admin Service에 POST 요청을 제출하면 통합 문서에 다음과 같은 변경 사항이 표시됩니다.

* 이름이 &quot;shared-default&quot;인 새 시트가 Excel 통합 문서나 Google 시트에 추가됩니다. &quot;shared-default&quot; 시트에 있는 데이터는 시트에 대한 GET 요청 시 검색됩니다. 이 시트는 스프레드시트 공식을 사용하여 들어오는 데이터를 요약하기에 최적의 위치 역할을 하므로 다른 컨텍스트에서 사용하기에 좋습니다.

  어떠한 경우에도 &quot;공유-기본값&quot; 시트에는 공개적으로 액세스할 수 있는 데 익숙하지 않은 개인 식별 정보나 중요한 데이터가 포함되지 않아야 합니다.

* 이름이 &quot;slack&quot;인 시트가 Excel 통합 문서 또는 Google 시트에 추가됩니다. 이 시트에서 스프레드시트로 새 데이터가 수집될 때마다 지정된 Slack 채널에 대한 자동 알림을 구성할 수 있습니다. 현재 AEM은 AEM Engineering Slack 조직 및 Adobe 엔터프라이즈 지원 조직에만 통지를 지원합니다.

   1. Slack 알림을 설정하려면 Slack 작업 영역의 &quot;teamId&quot;와 &quot;채널 이름&quot; 또는 &quot;ID&quot;를 입력합니다. debug 명령을 사용하는 slack-bot에 &quot;teamId&quot; 및 &quot;channel ID&quot;를 요청할 수도 있습니다. 채널 이름 대신 &quot;채널 ID&quot;를 사용하는 것이 좋습니다. 채널 이름은 계속 변경되기 때문입니다.

      >[!NOTE]
      >
      > 이전 양식에는 &quot;teamId&quot; 열이 없습니다. &quot;teamId&quot;가 채널 열에 포함되었으며, &quot;#&quot; 또는 &quot;/&quot;로 구분되었습니다.

   1. 원하는 제목을 입력하고 필드 아래에 Slack 알림에 표시할 필드 이름을 입력합니다. 각 제목은 쉼표로 구분해야 합니다(예: 이름, 이메일).

이제 데이터를 수신하도록 시트가 설정되었으며 hlx.page, hlx.live 또는 프로덕션 도메인을 사용하여 POST 요청을 직접 전송할 수 있습니다.


## 시트에 데이터 보내기 {#send-data-to-your-sheet}

시트가 데이터를 수신하도록 설정되면 데이터를 전송하기 위해 hlx.page, hlx.live 또는 프로덕션 도메인을 사용하여 POST 요청을 직접 전송할 수 있습니다.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> URL에는 .json 확장명이 없어야 합니다. POST 작업이 .live 또는 프로덕션 도메인에서 작동하려면 시트를 게시해야 합니다.

### EDS Forms에 대한 데이터 형식 지정

POST 본문에서 양식 데이터의 서식을 지정할 수 있는 방법에는 몇 가지가 있습니다.

* 이름:값 쌍의 배열:

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
              { "name": "message", "value": "I have some questions about your products." },
              { "name": "phone", "value": "123-456-7890" },
              { "name": "company", "value": "Example Inc." },
              { "name": "country", "value": "United States" },
              { "name": "preferred_contact_method", "value": "Email" },
              { "name": "newsletter_subscribe", "value": true }
              ]
          }'
  
* 키:값 쌍을 포함한 개체

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

* `x-www-form-urlencoded` 본문(`content-type` 헤더를으로 설정해야 합니다. `application/x-www-form-urlencoded`) &#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



