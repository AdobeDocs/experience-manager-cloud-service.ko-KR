---
title: AEM Forms Edge Delivery Service에 대한 문서 기반 작성을 사용하여 양식 만들기
description: 완벽한 양식을 빠르게 제작하십시오. ⚡ AEM Forms Edge Delivery + 문서 기반 작성 = 놀라운 속도 및 만족도가 높은 사용자를 위한 SEO 친화적 양식과 검색 엔진.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: ht
source-wordcount: '889'
ht-degree: 100%

---


# AEM Forms Edge Delivery Service에 대한 문서 기반 작성을 사용하여 양식 만들기

오늘날의 디지털 시대에는 사용자 친화적인 양식을 만드는 것이 모든 조직에 필수적입니다. AEM Forms Edge Delivery의 문서 기반 작성을 사용하면 Word 또는 Google Docs와 같은 익숙한 도구를 사용하여 양식을 만들 수 있습니다. 이러한 양식은 데이터를 Microsoft Excel 또는 Google Sheets 파일에 직접 제출하므로 Google Sheets, Microsoft Excel 및 Microsoft Sharepoint의 활발한 에코시스템과 강력한 API를 사용하여 쉽게 제출 데이터를 처리하거나 기존 비즈니스 워크플로를 시작할 수 있습니다.

이 안내서에서는 다음과 같은 사항을 다룹니다.

* 스프레드시트 준비: 데이터 수집을 위해 Excel 또는 Google Sheets 파일을 설정하고 여기에 양식 필드를 추가하는 방법을 알아봅니다.
* 시트로 데이터 전송: POST 요청을 사용하여 시트로 데이터를 전송하는 방법을 알아봅니다.
* 양식 게시: 양식을 AEM Sites 페이지에 통합하거나 독립 실행형 페이지로 게시합니다.

초보자든 전문가든 이 안내서를 통해 사용자의 마음에 드는 아름답고 기능적인 양식을 빌드할 수 있습니다. 지금 바로 효율적인 양식 만들기를 시작해 보십시오.

## 시작하기 전

`WIP`

## 데이터를 수신할 스프레드시트 준비

1. Microsoft Excel 통합 문서 또는 Google 시트를 Microsoft OneDrive 또는 Google Drive의 AEM Edge Delivery 프로젝트 디렉터리 아래에 만듭니다. 이 문서에서는 Adobe Experience Manager(AEM) 프로젝트의 루트에 있는 `contact-us.xlsx`라는 Google 시트를 사용합니다.

1. 프로젝트에 대해 구성된 AEM 사용자(예: helix@adobe.com)에게 시트에 대한 편집 권한이 있어야 합니다.

1. 만든 통합 문서를 열고 기본 시트의 이름을 “incoming”으로 변경합니다.

   >[!NOTE]
   >
   > “incoming” 시트가 존재하지 않는 경우 AEM은 이 통합 문서에 데이터를 전송하지 않습니다.

1. 사이드 킥에서 시트를 미리 봅니다.

   >[!NOTE]
   >
   >이전에 시트를 미리 본 적이 있더라도 처음으로 “incoming” 시트를 만든 후에는 다시 미리보기로 확인해야 합니다.

1. 입력하는 데이터와 일치하는 헤더를 추가하여 시트를 준비합니다. 다음 예에서는 “contact-us” 양식의 필드를 표시합니다.

   ![contact-us 양식의 필드](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   이 작업은 수동으로 수행하거나 AEM 관리 서비스의 양식 경로에 대한 POST 요청을 사용하여 수행할 수 있습니다. 관리 서비스는 POST 본문의 데이터를 검사하고, 데이터를 효과적으로 수집하고 양식 서비스를 최대한 활용하는 데 필요한 적절한 헤더, 테이블 및 시트를 생성합니다.

   시트 설정을 위해 POST 요청 형식을 지정하는 방법을 이해하려면 [Admin API 설명서](https://www.hlx.live/docs/admin.html#tag/form)를 참조하십시오. 또한 아래 제공된 예를 살펴보십시오.

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

앞서 언급한 POST 요청은 양식 필드와 해당 샘플 값을 모두 포함하는 샘플 데이터를 제공합니다. 이 데이터는 관리 서비스에서 양식을 설정하는 데 사용됩니다.

관리 서비스에서는 시트 구성을 권장하지만, 헤더를 수동으로 만들려는 경우 [수동 양식 시트 설정](https://www.hlx.live/docs/manual-forms-sheet-setup)이라는 제목의 문서를 참조하십시오.

관리 서비스에 POST 요청을 제출하면 통합 문서에서 다음과 같은 변경 사항을 확인할 수 있습니다.

* “shared-default”라는 새 시트가 Excel 통합 문서 또는 Google 시트에 추가됩니다. “shared-default” 시트에 있는 데이터는 시트에 GET 요청을 하면 검색됩니다. 이 시트는 스프레드시트 공식을 사용하여 수신 데이터를 요약하는 최적의 위치 역할을 하므로 다른 상황에서 사용하는 데 도움이 됩니다.

  어떤 경우에도 “shared-default” 시트에는 공개적으로 액세스 가능해서는 안 되는 개인 식별 정보나 민감한 데이터가 포함되어서는 안 됩니다.

* “slack”이라는 시트가 Excel 통합 문서 또는 Google 시트에 추가됩니다. 이 시트에서는 새 데이터가 스프레드시트에 수집될 때마다 지정된 Slack 채널에 대한 자동 알림을 구성할 수 있습니다. 현재 AEM은 AEM Engineering Slack 조직 및 Adobe Enterprise Support 조직에만 알림을 지원합니다.

   1. Slack 알림을 설정하려면 Slack 작업 영역의 “teamId”와 “채널 이름” 또는 “ID”를 입력합니다. 디버그 명령을 사용하여 slack-bot에 “teamId” 및 “채널 ID”를 요청할 수도 있습니다. “채널 이름” 대신 “채널 ID”를 사용하는 것이 채널 이름을 변경해도 유지되므로 더 이상적입니다.

      >[!NOTE]
      >
      > 이전 양식에는 “teamId” 열이 없었습니다. “teamId”는 “#” 또는 “/”로 구분된 채널 열에 포함되어 있었습니다.

   1. 원하는 제목을 입력하고 필드 아래에 Slack 알림에 표시할 필드 이름을 입력합니다. 각 제목은 쉼표로 구분되어야 합니다(예: 이름, 이메일).

이제 시트가 데이터를 수신하도록 설정되었으며 hlx.page, hlx.live 또는 프로덕션 도메인을 사용하여 직접 POST 요청을 보낼 수 있습니다.


## 시트로 데이터 전송 {#send-data-to-your-sheet}

시트가 데이터를 수신하도록 설정되면 hlx.page, hlx.live 또는 프로덕션 도메인을 사용하여 직접 POST 요청을 보내 데이터를 전송할 수 있습니다.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> URL에는 .json 확장자가 없어야 합니다. .live 또는 프로덕션 도메인에서 작동하려면 POST 작업에 대한 시트를 게시해야 합니다.

### EDS 양식의 데이터 형식 지정

POST 본문에서 양식 데이터의 형식을 지정할 수 있는 몇 가지 방법이 있습니다.

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
  
* 키:값 쌍이 있는 오브젝트

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

* `x-www-form-urlencoded` 본문(`content-type` 헤더를 `application/x-www-form-urlencoded`로 설정해야 함)
&#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



