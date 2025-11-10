---
title: JWT(JSON 웹 토큰) 인증을 설정하는 방법
description: Adobe Experience Manager Forms as a Cloud Service에 대한 JWT(JSON 웹 토큰) 인증을 구성하는 방법에 대해 알아봅니다
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromToC: true
index: false
source-git-commit: 69704ca8de41c655b59ce6652a4a43b788ba75ec
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 3%

---


# JWT(JSON 웹 토큰) 인증 - 더 이상 사용되지 않음

특히 AEM Forms과의 서버측 통합을 위한 AEM as a Cloud Service의 JWT 인증에는 AEM 서비스와 안전하게 상호 작용하기 위한 특정 프로세스가 포함됩니다.

## 고려 사항

JWT에서 생성된 액세스 토큰은 현재 인증서가 만료되거나 2026년 3월 1일 중 빠른 날짜 이후에는 작동하지 않습니다. 따라서 새 [OAuth 서버 간 자격 증명](/help/forms/oauth-api-authetication.md)을 사용하도록 통합을 마이그레이션해야 합니다.

OAuth 서버 간 자격 증명으로 프로젝트를 마이그레이션하는 것은 애플리케이션 및 통합에 대한 다운타임 없이 마이그레이션할 수 있는 간단한 2단계 프로세스입니다. OAuth 서버 간 자격 증명으로 마이그레이션하려면 [마이그레이션 안내서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration)를 읽어 보십시오.


## 사전 요구 사항

시작하기 전에 다음 전제 조건이 충족되는지 확인하십시오.

* 사용하는 환경에 맞는 [Adobe Cloud Manager](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html)에 액세스할 수 있는지 확인하십시오.
* Adobe Cloud Manager에 액세스하려면 시스템 관리자 또는 개발자 역할을 할당합니다.

## JWT 자격 증명을 사용하여 액세스 토큰을 생성하는 방법

JWT 자격 증명에서 액세스 토큰을 생성하는 방법을 보여주는 아래 단계를 따르십시오.

1. **Adobe Cloud Manager**

   1. [Cloud Manager 계정](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html)에 로그인합니다.
   2. 선택한 프로그램에서 **[!UICONTROL 프로그램 개요]**&#x200B;를 클릭합니다.

      ![Cloud Manager 계정](/help/forms/assets/jwt-cloud-manager-landing.png)

   3. 프로그램에서 세 점 메뉴를 클릭하고 **[!UICONTROL Developer Console]**&#x200B;을(를) 선택합니다.

      ![개발자 콘솔](/help/forms/assets/jwt-developer-console.png)

2. **AEM Developer Console**
   1. AEM Developer Console에 로그인
   2. 상단 메뉴 모음에 있는 **[!UICONTROL 통합]**&#x200B;을 클릭합니다.

      ![통합](/help/forms/assets/jwt-integrations.png)

   3. **[!UICONTROL 새 기술 계정을 만듭니다]** 옵션을 클릭합니다.

      ![새 기술 계정 만들기](/help/forms/assets/jwt-creae-new-tech-account.png)

   새 기술 계정 만들기를 클릭하면 개인 키, 공개 키, 만료 날짜를 포함한 기타 기술 계정 정보와 함께 클라이언트 ID 및 클라이언트 암호와 같은 액세스 토큰을 생성하는 데 필요한 정보가 생성됩니다.

   ![JWT 자격 증명](/help/forms/assets/jwt-credentials.png)


3. 자격 증명 생성 및 저장

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

4. 액세스 토큰 생성

   Adobe IMS API를 사용하여 프로그래밍 방식으로 토큰 생성:

   **필요한 자격 증명:**

   * 클라이언트 ID
   * 클라이언트 비밀
   * 범위(일반적으로 `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **토큰 끝점:**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **샘플 요청(curl):**

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

이제 생성된 액세스 토큰을 사용하여 개발, 스테이지 또는 프로덕션 환경에 대한 API를 호출할 수 있습니다.

## 다음 단계

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


