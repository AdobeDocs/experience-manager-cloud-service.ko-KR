---
title: OAuth 서버 간 인증을 설정하는 방법
description: Adobe Experience Manager Forms as a Cloud Service에 대한 OAuth 서버 간 인증을 구성하는 방법에 대해 알아봅니다.
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: 6bd2e1698cceaf8fe47e19e0645d0782c916644a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 3%

---


# OAuth 서버 간 인증

OAuth 서버 간 인증을 사용하면 사용자 상호 작용 없이 AEM Forms Communications API에 대한 토큰 기반의 보안 액세스를 수행할 수 있습니다. OAuth 서버 간 인증은 Adobe Developer Console에서 지원됩니다.

## 사전 요구 사항

시작하기 전에 다음 전제 조건이 충족되는지 확인하십시오.

* 사용하는 환경에 맞는 [Adobe Developer Console에 대한 액세스](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-manager/content/requirements/access-rights)가 있는지 확인하십시오.
* [Adobe Admin Console에서 시스템 관리자 또는 개발자 역할을 할당](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions)하여 Adobe Developer Console에 액세스할 수 있도록 설정합니다.

## OAuth 서버 간 인증을 사용하여 액세스 토큰을 생성하는 방법

아래 단계에 따라 Adobe Developer 콘솔에서 액세스 토큰을 생성하고 OAuth 서버 간 인증을 통해 첫 번째 API 호출을 수행하십시오.

### &#x200B;1. Adobe Developer Console 프로젝트 설정

1. [Adobe Developer Console](https://developer.adobe.com/console)&#x200B;(으)로 이동
2. Adobe ID으로 로그인

3. 새 프로젝트 만들기 또는 기존 프로젝트로 이동

>[!BEGINTABS]

>[!TAB 새 프로젝트를 만들려면]

1. **빠른 시작** 섹션에서 **새 프로젝트 만들기**&#x200B;를 클릭하세요.
2. 기본 이름으로 새 프로젝트가 만들어집니다.

   ![ADC 프로젝트 만들기](/help/forms/assets/adc-home.png)

3. 오른쪽 상단 모서리에서 **프로젝트 편집**&#x200B;을 클릭합니다.

   ![프로젝트 편집](/help/forms/assets/adc-edit-project.png)

4. 의미 있는 이름(예: &quot;formsproject&quot;) 제공
5. **저장** 클릭

   ![프로젝트 이름 편집](/help/forms/assets/adc-edit-projectname.png)

>[!TAB 기존 프로젝트로 이동]

1. Adobe Developer Console에서 **모든 프로젝트** 클릭

   ![프로젝트 검색](/help/forms/assets/search-adc-project.png)

2. 프로젝트를 찾은 다음 를 클릭하여 엽니다.

   ![프로젝트 찾기](/help/forms/assets/locate-adc-project.png)

>[!ENDTABS]

### &#x200B;2. Forms API 추가

원하는 작업을 기반으로 Forms API를 추가합니다.

* **AEM Forms Communications API**: 문서(PDF 및 관련 형식)를 생성, 변환, 결합 또는 보호해야 할 때 사용합니다.
* **적응형 Forms 런타임 API** - 런타임 시 적응형 Forms을 렌더링, 제출 또는 처리해야 할 때 사용합니다.

>[!BEGINTABS]

>[!TAB AEM Forms Communications API용]

1. **API 추가** 클릭

   ![API 추가](/help/forms/assets/adc-add-api.png)

2. **Forms 통신 API** 선택
   1. _API 추가_ 대화 상자에서 **Experience Cloud**(으)로 필터링합니다.
   2. **&quot;Forms 통신 API&quot;** 선택

      ![Forms 통신 API 추가](/help/forms/assets/adc-add-forms-api.png)

   3. **다음** 클릭
   4. **OAuth 서버 간** 인증 방법 선택

      ![인증 방법 선택](/help/forms/assets/adc-add-authentication-method.png)

>[!TAB 적응형 Forms 런타임 API용]

1. **API 추가 클릭**

   ![API 추가](/help/forms/assets/adc-add-api.png)

2. **AEM Forms 배달 및 런타임 API 선택**
   1. _API 추가_ 대화 상자에서 **Experience Cloud**(으)로 필터링합니다.
   2. **&quot;AEM Forms 배달 및 런타임 API&quot;** 선택
      ![Forms 통신 API 추가](/help/forms/assets/adc-add-runtime-api.png)

   3. **다음** 클릭
   4. **OAuth 서버 간** 인증 방법을 선택하십시오.
      ![인증 방법 선택](/help/forms/assets/adc-add-authentication-method.png)

>[!ENDTABS]

**프로젝트에 추가** > **API**&#x200B;를 클릭하여 API 및 인증 방법을 기존 프로젝트에 추가할 수도 있습니다.\
![기존 프로젝트에 API 추가](/help/forms/assets/add-api-existing-project.png)

### &#x200B;3. 제품 프로필 추가

제품 프로필은 AEM 리소스에 액세스할 수 있는 자격 증명에 대한 권한(또는 인증)을 제공합니다.

1. AEM 인스턴스 URL(**)과 일치하는**&#x200B;제품 프로필`https://Service Type -Environment Type-Program XXX-Environment XXX.adobeaemcloud.com`을 선택하십시오.

   * **서비스 유형** - AEM 인스턴스와 연결된 서비스 또는 권한을 지정합니다.

   * **환경 유형** - 환경이 Author 또는 Publish 서비스용인지 지정합니다.

   * **프로그램 XXX** - Cloud Manager 프로그램 ID를 식별합니다

   * **환경 XXX** - 해당 프로그램 내의 특정 환경 ID를 식별합니다.

   >[!NOTE]
   >
   > 제품 프로필은 특정 AEM 인스턴스(프로그램 + 환경)에 연결되어 있습니다. 항상 인스턴스 URL과 일치하는 프로필을 선택합니다.

2. **구성된 API 저장**&#x200B;을 클릭합니다. API 및 제품 프로필이 프로젝트에 추가됩니다

   ![프로젝트 구성 선택](/help/forms/assets/adc-add-product-profile.png)

### &#x200B;4. 자격 증명 생성 및 저장

1. Adobe Developer Console에서 프로젝트로 이동
2. **OAuth 서버 간** 자격 증명을 클릭합니다.
3. **자격 증명 세부 정보** 섹션 보기

   ![자격 증명 보기](/help/forms/assets/adc-view-credential.png)

**API 자격 증명 기록**

```text
    API Credentials:
    ================
    Client ID: <your_client_id>
    Client Secret: <your_client_secret>
    Technical Account ID: <tech_account_id>
    Organization ID: <org_id>
    Scopes: AdobeID,openid,read_organizations
```

### &#x200B;5. 액세스 토큰 생성

Access 토큰을 수동 또는 프로그래밍 방식으로 생성합니다.

>[!BEGINTABS]

>[!TAB 테스트용]

Adobe Developer Console에서 액세스 토큰을 수동으로 생성합니다.

1. **프로젝트로 이동**
   1. Adobe Developer Console에서 프로젝트를 엽니다.
   2. **OAuth 서버 간** 클릭

2. **액세스 토큰 생성**
   1. 프로젝트의 API 섹션에서 **&quot;액세스 토큰 생성&quot;** 단추를 클릭합니다.
   2. 생성된 액세스 토큰 복사

   ![액세스 토큰 생성](/help/forms/assets/adc-access-token.png)

   >[!NOTE]
   >
   > 액세스 토큰은 **24시간** 동안만 유효합니다.

>[!TAB 프로덕션용]

[Adobe IMS](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service) API를 사용하여 프로그래밍 방식으로 토큰 생성:

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

>[!ENDTABS]

이제 생성된 액세스 토큰을 사용하여 개발, 스테이지 또는 프로덕션 환경에 대한 API를 호출할 수 있습니다.

>
>
> 액세스 토큰을 생성하고 API를 호출하기 위한 OAuth 서버 간 구현에 대해 자세히 알아보려면 [여기를 클릭](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)하십시오.

## 우수 사례: 개발, 스테이징 및 프로덕션을 위한 자격 증명 관리

* 개발, 스테이징 및 프로덕션에 항상 별도의 자격 증명을 사용하십시오.

* 각 자격 증명을 올바른 AEM 환경 URL에 매핑합니다.

* 비밀을 안전하게 저장하고 소스 제어에 커밋하지 마십시오.

* 토큰은 24시간 동안만 유효하므로 액세스 토큰 유효성을 추적합니다.

## 다음 단계

동기 Forms Communication API용 환경을 설정하는 방법에 대해 알아보려면 [AEM Forms as a Cloud Service Communications 동기 처리](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)를 참조하십시오.


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


