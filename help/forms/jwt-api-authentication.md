---
title: How to set up JWT (JSON Web Token) Authentication?
description: Learn how to configure JWT (JSON Web Token) authentication for Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
badgeSaas: label="AEM Forms" type="Positive" tooltip="AEM Forms에 적용됩니다)."
exl-id: e7747b21-f680-4b3a-bf05-d0fcf0af0999
hide: true
hidefromToC: true
index: false
source-git-commit: 44d7e7357c86183d1ddfa8dce9c26b48448554f6
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 2%

---

# JWT (JSON Web Token) Server-to-Server Authentication

JWT server-to-server authentication in AEM Forms, particularly for server-side integrations with AEM as a Cloud Service, involves a specific process to securely interact with AEM services. JWT server-to-server authentication is supported by AEM Developer Console.

## 사전 요구 사항

시작하기 전에 다음 전제 조건이 충족되는지 확인하십시오.

* Ensure that you have access to the [Adobe Cloud Manager](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html) specific to the environment you use.
* Assign the [System Administrator or Developer role to access Adobe Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/access-rights).

## How to Generate an Access Token Using JWT Credentials?

Follow the steps below which shows you how to generate an access token from the JWT credentials.

1. **Adobe Cloud Manager**

   1. Log in to your [Cloud Manager account](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html).
   2. On your selected program, click **[!UICONTROL Program Overview]**.

      ![Cloud Manager Account](/help/forms/assets/jwt-cloud-manager-landing.png)

   3. On your program, click three-dots menu and select **[!UICONTROL Developer Console]**.

      ![개발자 콘솔](/help/forms/assets/jwt-developer-console.png)

2. **AEM Developer Console**
   1. Login in AEM Developer Console
   2. Click **[!UICONTROL Integrations]** located on the upper menu bar.

      ![통합](/help/forms/assets/jwt-integrations.png)

   3. Click the option to **[!UICONTROL Create new technical account]**.

      ![Create new technical account](/help/forms/assets/jwt-creae-new-tech-account.png)

   새 기술 계정 만들기를 클릭하면 개인 키, 공개 키, 만료 날짜를 포함한 기타 기술 계정 정보와 함께 클라이언트 ID 및 클라이언트 암호와 같은 액세스 토큰을 생성하는 데 필요한 정보가 생성됩니다.

   ![JWT 자격 증명](/help/forms/assets/jwt-credentials.png)


3. **자격 증명 생성 및 저장**

   1. API 자격 증명 기록

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

4. **액세스 토큰 생성**

   cURL 명령을 사용하여 프로그래밍 방식으로 토큰을 생성합니다.

   **필요한 자격 증명:**

   * 클라이언트 ID
   * 클라이언트 비밀
   * 범위(일반적으로 `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **토큰 끝점:**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **샘플 요청(cURL):**

   ```bash
   curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
   -H 'Content-Type: application/x-www-form-urlencoded' \
   -d 'grant_type=client_credentials' \
   -d 'client_id=<YOUR_CLIENT_ID>' \
   -d 'client_secret=<YOUR_CLIENT_SECRET>' \
   -d 'scope=AdobeID,openid,read_organizations'
   ```

   **응답:**

   ```json
   {
   "access_token": "eyJhbGciOiJSUz...",
   "token_type": "bearer",
   "expires_in": 86399
   }
   ```


>[!NOTE]
>
> 서비스 자격 증명과 Adobe IMS API를 사용하여 액세스 토큰을 생성하는 방법에 대해 자세히 알아보려면 [여기를 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials)하십시오.

이제 생성된 액세스 토큰을 사용하여 개발, 스테이지 또는 프로덕션 환경에 대한 API를 호출할 수 있습니다.

## 관련 문서

동기식(온디맨드) 및 비동기식(일괄 처리) Forms Communications API에 대한 환경을 설정하는 방법에 대해 알아봅니다.

<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <!-- Synchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Synchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" title="동기 API" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/sync-api.png" alt="동기 API"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" title="AEM Forms Communications API - 동기">AEM Forms Communications API - 동기</a>
                    </p>
                    <p class="is-size-6">문서를 즉시 생성하거나 처리하는 동기식(온디맨드) Forms Communications API용 환경을 설정하는 방법에 대해 알아봅니다. </p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">자세히 알아보기</span>
                </a>
            </div>
        </div>
    </div>
    <!-- Asynchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Asynchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" title="AEM Forms Communications API - 비동기" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/async-api.png" alt="비동기 API"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" title="비동기 API">AEM Forms Communications API - 비동기(일괄 처리)</a>
                    </p>
                    <p class="is-size-6">예약된 방식으로 여러 문서를 생성하거나 처리하는 비동기(일괄 처리) Forms Communications API에 대한 환경을 설정하는 방법에 대해 알아봅니다.</p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">자세히 알아보기</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->


>[!MORELIKETHIS]
>
>* [AEM Forms as a Cloud Service Communications 소개](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* 적응형 Forms 및 통신 API를 위한 [AEM Forms as a Cloud Service 아키텍처](/help/forms/aem-forms-cloud-service-architecture.md)
>* [통신 처리 - 동기 API](/help/forms/aem-forms-cloud-service-communications.md)
>* [통신 처리 - 일괄 처리 API](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [Forms Communications API - 자습서](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)
