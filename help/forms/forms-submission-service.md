---
Title: How to use forms submission service for submitting forms?
Description: Learn how to use forms submission service for submitting forms.
Keywords: Use form submission service, Submit form using form submission service
feature: Edge Delivery Services
Role: User, Developer
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 67416999d068af6350748d610e7c1c7b1d991bc4
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 6%

---

# Edge Delivery Services Forms을 사용한 Forms 제출 서비스

<span class="preview"> 이 기능은 얼리 액세스 프로그램을 통해 사용할 수 있습니다. 액세스 권한을 요청하려면 공식 주소를 통해 GitHub 조직 이름과 저장소 이름을 포함한 이메일을 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>으로 보내 주십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc, 조직 이름이 adobe, 저장소 이름이 abc인 경우입니다.</span>

Forms 제출 서비스를 사용하면 양식 제출의 데이터를 OneDrive, SharePoint 또는 Google Sheets와 같은 스프레드시트에 저장할 수 있으므로 원하는 스프레드시트 플랫폼 내에서 양식 데이터에 쉽게 액세스하고 관리할 수 있습니다.

![Forms 제출 서비스](/help/forms/assets/form-submission-service.png)

## Forms 제출 서비스 사용 시 이점

스프레드시트와 함께 Forms 제출 서비스를 사용하면 다음과 같은 몇 가지 이점이 있습니다.

* **직접 통합**: 데이터를 지정된 스프레드시트로 직접 제출하도록 양식을 구성할 수 있으므로 수동으로 데이터를 전송할 필요가 없습니다.
* **데이터 구조**: 제출을 설정할 때 양식 필드를 구성된 데이터 저장을 위해 해당 스프레드시트 열에 매핑할 수 있습니다.
* **액세스 제어**: 기존 권한을 활용하여 선택한 스프레드시트 서비스에 따라 제출된 양식 데이터에 액세스하고 수정할 수 있는 사용자를 제어할 수 있습니다.

## 사전 요구 사항

Forms 제출 서비스를 사용하기 위한 사전 요구 사항은 다음과 같습니다.

* AEM 프로젝트에 최신 적응형 양식 블록이 있는지 확인합니다.
* Forms 제출 서비스를 사용하기 위해 Git 저장소가 허용 목록에 추가하다에 추가되었는지 확인합니다. Forms 제출 서비스를 사용하려면 GitHub 조직 이름과 저장소 이름을 사용하여 [mailto:aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)을(를) 허용 목록에 추가하다 이름에 추가하세요.

## Forms 제출 서비스 구성

적응형 Forms 블록으로 구성된 새 AEM 프로젝트를 만듭니다. 새 AEM 프로젝트를 만드는 방법을 알아보려면 [시작하기 - 개발자 자습서](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial) 문서를 참조하십시오. 프로젝트에서 `fstab.yaml` 파일을 업데이트합니다. 기존 참조를 `forms@adobe.com`과(와) 공유한 폴더의 경로로 바꿉니다.

[Forms 제출 서비스를 수동으로 구성](#configuring-the-forms-submission-service-manually)하거나 [API를 사용하여 Forms 제출 서비스를 구성](#configuring-the-forms-submission-service-using-api)할 수 있습니다.

### Forms 제출 서비스 수동 구성

![양식 제출 서비스에 대한 워크플로](/help/forms/assets/forms-submission-service-workflow.png)

#### &#x200B;1. 양식 정의를 사용하여 양식 만들기

Google Sheets 또는 Microsoft Excel을 사용하여 양식을 작성합니다. Microsoft Excel 또는 Google Sheets에서 양식 정의를 사용하여 양식을 만드는 방법에 대해 알아보려면 [여기를 클릭](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)하십시오.

아래 스크린샷에는 양식을 만드는 데 사용된 양식 정의가 표시됩니다.

![양식 정의](/help/forms/assets/form-submission-definition.png)

>[!IMPORTANT]
>
>**폼이 작성된 시트에는 이름을 지정할 수 있는 내용에 제한이 있습니다. `helix-default` 및 `shared-aem`만 시트 이름으로 사용할 수 있습니다.**

#### &#x200B;2. 스프레드시트가 데이터를 수락하도록 설정합니다.

양식을 만들고 미리 본 후 해당 스프레드시트를 활성화하여 데이터 수신을 시작합니다. 새 시트를 `incoming`(으)로 추가합니다. [스프레드시트가 데이터를 수락하도록 수동으로 설정](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/submit-forms#manually-enable-the-spreadsheet-to-accept-data)할 수 있습니다.

![받는 시트](/help/forms/assets/form-submission-incoming-sheet.png)

>[!WARNING]
>
> `incoming` 시트가 없으면 AEM에서 이 통합 문서로 데이터를 전송하지 않습니다.

#### &#x200B;3. 스프레드시트를 공유하고 링크를 생성합니다.

스프레드시트를 `forms@adobe.com` 계정에 공유하고 링크를 생성하려면 다음 단계를 수행하십시오.

1. Excel 또는 Google Sheets에서 오른쪽 상단의 **공유** 단추를 클릭합니다.
1. `forms@adobe.com` 계정 추가 및
눈 모양 아이콘을 클릭하고 **편집** 액세스를 선택한 다음 **보내기**&#x200B;를 클릭합니다.

   ![수신 시트 공유](/help/forms/assets/form-submission-share-incoming.png)

1. 스프레드시트 링크를 복사하려면 오른쪽 상단의 **공유** 단추를 클릭하고 **링크 복사**&#x200B;를 선택합니다.

   ![수신 시트의 링크 복사](/help/forms/assets/form-submission-copy-link.png)

#### &#x200B;4. 양식 정의에서 스프레드시트를 연결합니다

Google Sheets 또는 Microsoft Excel을 사용하여 Forms 제출 서비스를 구성하려면 다음 단계를 수행하십시오.

1. 양식 정의가 포함된 스프레드시트를 엽니다.
1. **제출** 필드에 해당하는 행에서 복사한 스프레드시트 링크를 **Action** 열에 붙여 넣습니다.

   ![스프레드시트 연결](/help/forms/assets/form-submission-sheet-linking.png)

1. 업데이트된 양식 제출 서비스와 함께 [AEM Sidekick](https://www.aem.live/docs/sidekick)을(를) 사용하여 시트를 미리 보고 게시합니다.

>[!NOTE]
>
> [스프레드시트](/help/forms/assets/spreadsheet.xlsx)를 참조하여 Forms 제출 서비스를 사용할 수 있습니다.

### API를 사용하여 Forms 제출 서비스 구성

**POST** 요청을 양식으로 전송하여 `incoming` 시트를 데이터로 업데이트할 수도 있습니다.

>[!NOTE]
>
> * `incoming` 시트가 없으면 AEM에서 이 통합 문서로 데이터를 전송하지 않습니다.
> * `forms@adobe.com`을(를) 통해 Adobe Experience Manager과 `incoming` 시트를 공유하고 편집 액세스 권한을 부여합니다.
> * 사이드 킥에서 `incoming` 시트를 미리 보고 게시합니다.

시트 설정에 대한 POST 요청의 형식을 지정하는 방법을 이해하려면 [API 설명서](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)를 참조하십시오. 아래 제공된 예를 살펴볼 수도 있습니다.

아래에서 보듯이 curl 또는 Postman과 같은 도구를 사용하여 이 POST 요청을 실행할 수 있습니다.

* **Postman 사용**:

예를 들어 을 교체한 후 Postman에서 아래 요청을 보냅니다.
* 양식 ID가 있는 `{id}`
* GitHub 리포지토리 또는 사이트 이름이 있는 `site or repository`
* GitHub 사용자 이름이 있는 `organization`

  ```json
  POST 'https://forms.adobe.com/adobe/forms/af/submit/{id}' \
  --header 'Content-Type: application/json' \
  --header 'x-adobe-routing: tier=live,bucket=main--[site/repository]--[organization]' \
  --data '{
      "data": {
          "startDate": "2025-01-10",
          "endDate": "2025-01-25",
          "destination": "Australia",
          "class": "First Class",
          "budget": "2000",
          "amount": "1000000",
          "name": "Mary",
          "age": "35",
          "subscribe": null,
          "email": "mary@gmail.com"
              }
          }'
  ```

Postman에서 **보내기** 단추를 클릭하면 `201 Created` 응답이 반환되고 `incoming` 시트가 제출된 데이터로 업데이트됩니다.

![postman 화면](/help/forms/assets/postman-api.png)

* **Curl 명령 사용**:

예를 들어 를 교체한 후 터미널 또는 명령 프롬프트에서 아래 명령을 실행합니다.
* 양식 ID가 있는 `{id}`
* GitHub 리포지토리 또는 사이트 이름이 있는 `site or repository`
* GitHub 사용자 이름이 있는 `organization`


>[!BEGINTABS]

>[!TAB macOS용]

    &quot;json
    curl -X POST &quot;https://forms.adobe.com/adobe/forms/af/submit/{id}&quot; \
    —헤더 &quot;Content-Type: application/json&quot; \
    —헤더 &quot;x-adobe-routing: tier=live,bucket=main—[site/repository]—[organization]&quot; \
    —데이터 &#39;&lbrace;
    &quot;data&quot;: &lbrace;
    &quot;startDate&quot;: &quot;2025-01-10&quot;,
    &quot;endDate&quot;: &quot;2025-01-25&quot;,
    &quot;destination&quot;: &quot;Australia&quot;,
    &quot;class&quot;: &quot;First Class&quot;,
    &quot;budget&quot;: &quot;200000&quot;,&lbrace;amount&quot;: &quot;1000000&quot;,
    &quot;name&quot;: &quot;Joe&quot;,
    &quot;age&quot;: &quot;35&quot;,
    &quot;subscribe&quot;: null,
    &quot;email&quot;: &quot;mary@gmail.com&quot;
    &rbrace;
    &#39;
    
    &quot;

    
>[!TAB Windows OS용]

    &quot;json
    
    curl -X POST &quot;https://forms.adobe.com/adobe/forms/af/submit/{id}&quot; ^
    —header &quot;Content-Type: application/json&quot; ^
    —header &quot;x-adobe-routing: tier=live,bucket=main—[site/repository]—[organization]&quot; ^
    —data &quot;{\&quot;data\&quot;: {\&quot;startDate\&quot;: \&quot;2025-01-10\&quot;, \&quot;endDate\&quot;: \&quot;2025-01-25\&quot;, \&quot;destination\&quot;: \&quot;Australia\&quot;, \&quot;class\&quot;: \&quot;first Class\&quot;, \&quot;amount\&quot;: \&quot;1000000\&quot;, \&quot;name\&quot;: \&quot;Joe\&quot;, \&quot;age\&quot;: \&quot;35\&quot;, \&quot;subscribe\&quot;: null, \&quot;email\&quot;: \&quot;mary@gmail.com\&quot;}}&quot;
    
    &quot;

>[!ENDTABS]

위에서 언급한 POST 요청은 아래 응답으로 `incoming` 시트를 업데이트합니다.

```json
    < HTTP/1.1 201 Created
    < Connection: keep-alive
    < Content-Length: 0
    < X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
    < X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
    < Accept-Ranges: bytes
    < Date: Fri, 10 Jan 2025 13:06:10 GMT
    < Via: 1.1 varnish
    < Access-Control-Allow-Origin: *
    < X-Served-By: cache-del21750-DEL
    < X-Cache: MISS
    < X-Cache-Hits: 0
    < X-Timer: S1736514370.704084,VS0,VE1234
```

아래 화면에는 API를 사용하여 보낸 데이터로 업데이트된 `incoming` 시트의 스크린샷이 표시됩니다.

![업데이트된 시트](/help/forms/assets/updated-sheet.png)

## 추가 참조

{{see-more-forms-eds}}