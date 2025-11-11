---
title: 대화형 통신 동기화 API를 설정하는 방법
description: Adobe Experience Manager Forms as a Cloud Service용 Interactive Communications Synchronous API의 개발 환경 설정
role: Admin, Developer, User
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: cbf640e0c4643616638de96e9daa460cdcf2a4a5
workflow-type: tm+mt
source-wordcount: '2574'
ht-degree: 2%

---


# AEM Forms as a Cloud Service Communications 동기 API 처리

이 안내서에서는 AEM Forms Communications 동기 API 설정 및 사용에 대한 포괄적인 지침을 제공합니다.

OAuth 서버 간 인증을 사용하여 AEM as a Cloud Service 환경을 구성하고, API 액세스를 활성화하고, 통신 API를 호출하는 방법에 대해 알아봅니다.

## 사전 요구 사항

AEM Forms Communications API를 실행하고 테스트하기 위한 환경을 설정하려면 다음 사항이 있는지 확인하십시오.

### 액세스 및 권한

Communications API 구성을 시작하기 전에 필요한 액세스 권한 및 권한이 있는지 확인하십시오.

**사용자 및 역할 권한**

- Adobe ID이 [https://account.adobe.com/](https://account.adobe.com/)에 만들어졌습니다.
- 조직의 이메일과 연결된 Adobe ID
- Adobe Managed Services 제품 컨텍스트 할당됨
- Adobe Admin Console에서 할당된 개발자 역할
- Adobe Developer Console에서 프로젝트를 만들 수 있는 권한

>[!NOTE]
>
> 역할을 할당하고 사용자에게 액세스 권한을 부여하는 방법에 대한 자세한 내용은 [사용자 및 역할 추가](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-manager/content/requirements/users-and-roles) 문서를 참조하십시오.

**Cloud Manager 액세스**

- [Cloud Manager](https://my.cloudmanager.adobe.com)에 대한 로그인 자격 증명
- 프로그램의 환경을 보고 관리하는 액세스 권한
- CI/CD 파이프라인을 만들고 실행할 수 있는 권한
- 환경 세부 정보 및 구성에 대한 액세스

**Git 저장소 액세스**

- Cloud Manager Git 저장소에 액세스
- 변경 사항 복제 및 푸시용 Git 자격 증명

### 개발 도구

- 샘플 응용 프로그램을 실행하기 위한 **Node.js**
- 최신 버전의 **Git**
- **터미널/명령줄**&#x200B;에 액세스
- 구성 파일(VS 코드, IntelliJ 등)을 편집하기 위한 **텍스트 편집기 또는 IDE**
- API 테스트용 **Postman** 또는 유사한 도구

>[!NOTE]
>
> AEM Forms Communications API 설정을 진행하기 전에 완료해야 하는 환경당 1회 프로세스입니다.

이제 각 단계를 자세히 살펴보겠습니다.

### 1단계: AEM 인스턴스 업데이트

AEM 인스턴스를 업데이트하려면:

1. **Adobe Cloud Manager에 로그인**
   1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)&#x200B;(으)로 이동
   2. Adobe ID으로 로그인

2. **프로그램 개요로 이동**
   1. 목록에서 프로그램을 선택합니다. 프로그램 개요 페이지로 리디렉션됩니다.

3. **환경 세부 정보 찾기**
   1. 환경 이름 옆의 `ellipsis`(...) 아이콘을 선택하고 **업데이트**&#x200B;를 클릭합니다
   2. **제출** 단추를 클릭하고 제안된 Fullstack 파이프라인을 실행합니다.

      ![환경 업데이트](/help/forms/assets/update-env.png)

### 2단계: Git 저장소 복제

Cloud Manager Git 저장소를 복제하여 API 구성 파일을 관리합니다.

1. **저장소 섹션 찾기**
   1. **프로그램 개요** 페이지에서 **저장소** 탭을 클릭합니다
   2. 저장소 이름을 찾고 줄임표 메뉴(...)를 클릭합니다.
   3. 저장소 URL 복사

      >[!NOTE]
      >
      > URL 형식은 일반적으로 `https://git.cloudmanager.adobe.com/<org>/<program>/`입니다.

2. **Git 명령을 사용하여 복제**

   1. 명령 프롬프트 또는 터미널을 엽니다
   2. `git clone` 명령을 실행하여 Git 저장소를 복제합니다.

      ```bash
      git clone [repository-url]
      ```

      >[!NOTE]
      >
      > Git 저장소를 복제하려면 Adobe Cloud Manager에서 제공한 자격 증명을 사용하십시오.

      예를 들어 Git 저장소를 복제하려면 다음 명령을 실행합니다.

      ```bash
      https://git.cloudmanager.adobe.com/formsinternal01/AEMFormsInternal-ReleaseSanity-p43162-uk59167/
      ```

      ![Git 리포지토리 복제](/help/forms/assets/repo-clone.png)


**Git 저장소 통합 옵션**

Adobe Cloud Manager은 다음 두 가지 저장소 옵션을 모두 지원합니다.

- **Cloud Manager의 Git 리포지토리 직접 사용**
   - Cloud Manager의 기본 Git 저장소 사용
   - 파이프라인과 내장된 통합

- **고객 관리 Git 저장소와 통합**
   - 고유한 Git 저장소(GitHub, GitLab, Bitbucket 등) 연결
   - Adobe Cloud Manager과의 동기화 구성

Adobe Cloud Manager과 Adobe Cloud Manager을 통합하는 방법에 대한 자세한 내용은 [Git 통합 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/git-integration.html)를 참조하세요.

### 3단계: AEM Cloud Service 환경 및 AEM Forms 엔드포인트 액세스

AEM Cloud Service 환경 세부 정보에 액세스하여 API 구성에 필요한 URL 및 식별자를 얻습니다.

1. **Adobe Cloud Manager에 로그인**
   1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)&#x200B;(으)로 이동
   2. Adobe ID으로 로그인

2. **프로그램 개요로 이동**
목록에서 프로그램을 선택합니다. 프로그램 개요 페이지로 리디렉션됩니다.

3. **AEM Cloud Service 환경 액세스 및 보기**

   다음 두 옵션 중 하나를 사용하여 AEM Cloud Service 환경 세부 사항을 보거나 액세스할 수 있습니다.

   - **옵션 1: 개요 페이지에서**

      1. **프로그램 개요** 페이지에서
      2. 왼쪽 메뉴에서 **&quot;환경&quot;**&#x200B;을(를) 클릭합니다.  모든 환경 목록을 볼 수 있습니다

         ![모든 환경 보기](/help/forms/assets/all-env.png)

      3. 세부 정보를 보려면 특정 환경 이름을 클릭하십시오.

         ![Option1-환경 세부 정보](/help/forms/assets/option1-env.png)

   - **옵션 2: 환경 섹션**

      1. 프로그램 개요 페이지에서
      2. **환경** 섹션을 찾습니다.
      3. 모든 환경을 보려면 **&quot;모두 표시&quot;**&#x200B;를 클릭하십시오.
      4. 환경 옆에 있는 **줄임표 메뉴(...)**&#x200B;를 클릭합니다
         ![Option1-환경 세부 정보](/help/forms/assets/option2-env-details.png)
      5. **&quot;세부 정보 보기&quot;** 선택

         ![Option1-환경 세부 정보](/help/forms/assets/option1-env.png)

4. **AEM Forms 끝점 찾기**

   **환경** 세부 정보 페이지에서 다음 세부 정보를 참고하십시오.

   **작성자 서비스 URL**

   - URL: `https://author-pXXXXX-eYYYYY.adobeaemcloud.com`
   - 버킷: author-pXXXXX-eYYYY
예: `https://author-p43162-e177398.adobeaemcloud.com`

   **게시 서비스 URL**

   - URL: `https://publish-pXXXXX-eYYYYY.adobeaemcloud.com`
   - 버킷: publish-pXXXXX-eYYYY
예: `https://publish-author-p43162-e177398.adobeaemcloud.com`

>[!NOTE]
>
> AEM 클라우드 서비스 환경 및 AEM Forms 끝점에 액세스하는 방법을 보려면 [환경 관리 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=ko)를 참조하십시오.

### 4단계: API 액세스 구성

AEM Forms Communications API를 구성하려면 다음 단계를 수행하십시오.

#### 4.1 Adobe Developer Console 프로젝트 설정

1. **Adobe Developer Console 액세스**
   1. [Adobe Developer Console](https://developer.adobe.com/console)&#x200B;(으)로 이동
   2. Adobe ID으로 로그인

2. **새 프로젝트 만들기**
   1. **빠른 시작** 섹션에서 **새 프로젝트 만들기**&#x200B;를 클릭하세요.
   2. 기본 이름으로 새 프로젝트가 만들어집니다.

      ![ADC 프로젝트 만들기](/help/forms/assets/adc-home.png)

   3. 오른쪽 상단 모서리에서 **프로젝트 편집**&#x200B;을 클릭합니다.

      ![프로젝트 편집](/help/forms/assets/adc-edit-project.png)

   4. 의미 있는 이름(예: &quot;formsproject&quot;) 제공
   5. **저장** 클릭

      ![프로젝트 이름 편집](/help/forms/assets/adc-edit-projectname.png)

#### 4.2 Forms Communication API 추가

요구 사항에 따라 다양한 AEM Forms Communications API를 추가할 수 있습니다.

**A. 문서 서비스 API용**

1. **API 추가** 클릭

   ![API 추가](/help/forms/assets/adc-add-api.png)

2. **Forms 통신 API** 선택
   1. _API 추가_ 대화 상자에서 **Experience Cloud**(으)로 필터링합니다.
   2. **&quot;Forms 통신 API&quot;** 선택

   ![Forms 통신 API 추가](/help/forms/assets/adc-add-forms-api.png)


3. **OAuth 서버 간** 인증 방법 선택

   ![인증 방법 선택](/help/forms/assets/adc-add-authentication-method.png)

**B. Forms 런타임 API용**

1. **API 추가 클릭**
   - 프로젝트에서 **API 추가** 단추를 클릭합니다.

   ![API 추가](/help/forms/assets/adc-add-api.png)

2. **AEM Forms 배달 및 런타임 API 선택**
   - _API 추가_ 대화 상자에서 **Experience Cloud**(으)로 필터링합니다.
   - **&quot;AEM Forms 배달 및 런타임 API&quot;** 선택
   - **다음** 클릭

   ![런타임 API 추가](/help/forms/assets/add-runtime-api.png)


3. **인증 방법**
   - **OAuth 서버 간** 인증 방법을 선택하십시오.


   ![인증 방법 선택](/help/forms/assets/add-authentication-for-runtime-apis.png)

#### 4.3 제품 프로필 추가

다음 단계에 따라 제품 프로필을 추가합니다.

1. 필요한 액세스 수준에 따라 적절한 **제품 프로필**&#x200B;을(를) 선택하십시오.

   | 액세스 유형 | 제품 프로필 |
   |------------------|----------------------|
   | 읽기 전용 액세스 | `AEM Users - author - Program XXX - Environment XXX` |
   | 읽기/쓰기 액세스 | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
   | 전체 관리 액세스 | `AEM Administrators - author - Program XXX - Environment XXX` |

2. 작성자 서비스 URL(**)과 일치하는**&#x200B;제품 프로필`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`을 선택하십시오. 예: `https://author-pXXXXX-eYYYYY.adobeaemcloud.com` 선택.

3. **구성된 API 저장**&#x200B;을 클릭합니다. API 및 제품 프로필이 프로젝트에 추가됩니다

   ![프로젝트 구성 선택](/help/forms/assets/adc-add-product-profile.png)

#### 4.4 자격 증명 생성 및 저장

1. **자격 증명에 액세스**

   1. Adobe Developer Console에서 프로젝트로 이동
   2. **OAuth 서버 간** 자격 증명을 클릭합니다.
   3. **자격 증명 세부 정보** 섹션 보기

   ![자격 증명 보기](/help/forms/assets/adc-view-credential.png)

2. **API 자격 증명 기록**

   ```text
   API Credentials:
   ================
   Client ID: <your_client_id>
   Client Secret: <your_client_secret>
   Technical Account ID: <tech_account_id>
   Organization ID: <org_id>
   Scopes: AdobeID,openid,read_organizations
   ```

#### 4.5 액세스 토큰 생성

**A. 테스트용**

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
   > 액세스 토큰이 **24시간** 동안 유효합니다.

**B. 프로덕션용**

Adobe IMS API를 사용하여 프로그래밍 방식으로 토큰 생성:

**필요한 자격 증명:**

- 클라이언트 ID
- 클라이언트 비밀
- 범위(일반적으로 `AdobeID,openid,read_organizations`)

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

#### 4.6 AEM 환경에 클라이언트 ID 등록

ADC 프로젝트의 클라이언트 ID가 AEM 인스턴스와 통신할 수 있도록 하려면 YAML 구성 파일을 사용하여 ID를 등록하고 구성 파이프라인을 통해 배포해야 합니다.

1. **구성 디렉터리 찾기 또는 만들기**

   1. 복제된 AEM 프로젝트 리포지토리로 이동하여 `config` 폴더로 이동합니다.
   2. 존재하지 않는 경우 프로젝트 루트 수준에서 만듭니다.

   ```bash
   mkdir config
   ```

2. `api.yaml` 디렉터리에 이름이 `config`인 새 파일을 만듭니다.

   ```bash
   touch config/api.yaml
   ```

3. `api.yaml` 파일에 다음 코드를 추가합니다.

   ```yaml
   kind: "API"
   version: "1"
   metadata:
   envTypes: ["dev"]  # or ["prod", "stage"] for production environments
   data:
   allowedClientIDs:
       author:
       - "<your_client_id>"
       publish:
       - "<your_client_id>"
       preview:
       - "<your_client_id>"
   ```

   다음은 구성 매개 변수에 대해 설명합니다.

   - **종류**: 항상 `"API"`(으)로 설정됨(API 구성으로 식별됨)
   - **버전**: API 버전(일반적으로 `"1"` 또는 `"1.0"`)
   - **envTypes**: 이 구성이 적용되는 환경 유형의 배열
      - `["dev"]` - 개발 환경만 해당
      - `["stage"]` - 스테이징 환경만
      - `["prod"]` - 프로덕션 환경만
   - **allowedClientIDs**: AEM 인스턴스에 액세스할 수 있는 클라이언트 ID입니다
      - **작성자**: 작성자 계층의 클라이언트 ID
      - **게시**: 게시 계층의 클라이언트 ID
      - **미리 보기**: 미리 보기 계층의 클라이언트 ID

   예를 들어 `allowedClientIDs`을(를) `6bc4589785e246eda29a545d3ca55980`(으)로, envTypes를 `dev`(으)로 추가합니다.

   ![구성 파일 추가](/help/forms/assets/create-api-yaml-file.png)

4. **변경 내용 커밋 및 푸시**

   1. 복제된 저장소의 루트 폴더로 이동하고 아래 명령을 실행합니다.


   ```bash
       git add config/api.yaml
       git commit -m "Whitelist client id for api invocation"
       git push origin <your-branch>
   ```

   ![Git 변경 사항 푸시](/help/forms/assets/push-yaml-changes-in-git.png)


5. **구성 파이프라인 설정**

   1. **Cloud Manager에 로그인**
      1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)&#x200B;(으)로 이동
      2. Adobe ID으로 로그인

   2. **내 프로그램으로 이동**
목록에서 프로그램을 선택하면 프로그램 개요 페이지에서 리디렉션됩니다.

   3. **파이프라인 카드 찾기**
      1. 프로그램 개요 페이지에서 **파이프라인** 카드를 찾습니다
      1. **&quot;추가&quot;** 단추 클릭

   4. **파이프라인 유형 선택**

      - **개발 환경의 경우**: **&quot;비프로덕션 파이프라인 추가&quot;**&#x200B;를 선택합니다. 비프로덕션 파이프라인은 개발 및 스테이징 환경을 위한 것입니다.

      - **프로덕션 환경의 경우**: **&quot;프로덕션 파이프라인 추가&quot;**&#x200B;를 선택합니다. 프로덕션 파이프라인에는 추가 승인이 필요합니다.

        >[!NOTE]
        >
        > 이 경우 개발 환경을 사용할 수 있으므로 비프로덕션 파이프라인을 생성합니다.

   5. **파이프라인 구성 - 구성 탭**

      **구성** 탭에서:

      a. **파이프라인 유형**
      - **&quot;배포 파이프라인&quot;** 선택

      b. **파이프라인 이름**
      - 수사적 이름을 지정하십시오. 예를 들어 파이프라인 이름을 `api-config-pipieline`(으)로 지정하십시오.

      c. **배포 트리거**
      - **수동**: 수동으로 트리거할 때만 배포(초기 설정에 권장)
      - **Git 변경 시**: 변경 내용이 분기에 푸시될 때 자동 배포

      d. **중요한 지표 오류 동작**
      - **항상 묻기**: 실패 시 작업을 묻기(기본값)
      - **즉시 실패**: 지표 실패 시 파이프라인을 자동으로 실패
      - **즉시 계속**: 실패에도 불구하고 계속

      e. **Source 코드** 탭으로 진행하려면 **&quot;계속&quot;**&#x200B;을 클릭합니다

      ![파이프라인 구성](/help/forms/assets/add-config-pipeline.png)

   6. **파이프라인 구성 - Source 코드 탭**

      **Source 코드** 탭에서:

      a. **배포 유형**
      - **&quot;대상 배포&quot;** 선택

      b. **배포 옵션**
      - **&quot;Config&quot;**&#x200B;을(를) 선택합니다(구성 파일만 배포). 이는 Cloud Manager에 구성 배포라고 알려줍니다.

      c. **적합한 배포 환경 선택**
      - 구성을 배포할 환경을 선택합니다. 이 경우 `dev` 환경입니다.

      d. **Source 코드 세부 정보 정의**

      - **저장소**: `api.yaml` 파일이 포함된 저장소를 선택합니다. 예를 들어 `AEMFormsInternal-ReleaseSanity-p43162-uk59167` 리포지토리를 선택합니다.
      - **Git 분기**: 분기를 선택합니다. 예를 들어 이 경우 코드가 `main` 분기에 배포됩니다.
      - **코드 위치**: `config` 디렉터리의 경로를 입력하십시오. `api.yaml`이(가) 루트의 `config` 폴더에 있으므로 `/config`을(를) 입력하십시오.

      e. 파이프라인을 만들려면 **&quot;저장&quot;**&#x200B;을 클릭합니다

      ![파이프라인 구성](/help/forms/assets/confirm-pipeline-1.png)

6. **구성 배포**

   파이프라인이 만들어졌으므로 `api.yaml` 구성을 배포하십시오.

   1. **파이프라인 개요에서**
      1. 프로그램 개요 페이지에서 **파이프라인** 카드를 찾습니다
      2. 목록에서 새로 생성된 구성 파이프라인으로 이동합니다. 예를 들어 생성한 파이프라인 이름(예: &quot;api-config-pipeline&quot;)을 찾습니다. 상태 및 마지막 실행을 포함한 파이프라인 세부 정보를 볼 수 있습니다.

   2. **배포 시작**
      1. 파이프라인 옆에 있는 **&quot;빌드&quot;** 단추(또는 재생 아이콘 ▶)를 클릭합니다
      2. 메시지가 표시되고 파이프라인 실행이 시작되면 배포를 확인합니다.

      ![파이프라인 실행](/help/forms/assets/run-config-pipeline.png)

   3. **배포 확인**
      - 파이프라인이 완료될 때까지 기다립니다.
         - 성공하면 상태가 &quot;성공&quot;(녹색 확인 표시 ✓)으로 바뀝니다.
         - 실패하면 상태가 &quot;실패&quot;(빨간색 십자 ✗)로 바뀝니다. 오류 세부 정보를 보려면 **로그 다운로드**&#x200B;를 클릭하십시오.

           ![파이프라인 성공](/help/forms/assets/pipeline-suceess.png)

      이제 Forms Communications API 테스트를 시작할 수 있습니다. 테스트 목적으로 Postman, curl 또는 기타 REST 클라이언트를 사용하여 API를 호출할 수 있습니다.

### 5단계: API 사양 및 테스트

이제 환경이 구성되었으므로 [Swagger UI](#a-using-swagger-ui-for-api-testing)를 사용하거나 NodeJS 애플리케이션을 개발하여 프로그래밍 방식으로 AEM Forms Communication API 테스트를 시작할 수 있습니다.

이 예제에서는 템플릿과 XDP 파일을 사용하여 문서 서비스 API를 사용하여 PDF을 생성해 보겠습니다.

#### A. API 테스트에 Swagger UI 사용

Swagger UI는 코드를 작성하지 않고 API를 테스트하기 위한 대화형 인터페이스를 제공합니다. **사용해 보기** 기능을 사용하여 [PDF 생성](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) 문서 서비스 API를 호출하고 테스트하십시오.

1. API 설명서로 이동
   - Forms API: [Forms API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
   - 문서 서비스: [문서 서비스 API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
브라우저에서 [문서 서비스 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document) 설명서를 엽니다.
2. **문서 생성** 섹션을 확장하고 [XDP 또는 PDF 템플릿에서 입력 가능한 PDF 양식을 생성합니다(선택적으로 데이터 병합 포함)](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm)을(를) 선택합니다.
3. 오른쪽 창에서 **시도**&#x200B;를 클릭합니다.

   ![API에 대한 Swagger 테스트](/help/forms/assets/api-doc-generation.png)
4. 다음 값을 입력합니다.

   | **섹션** | **매개 변수** | **값** |
   |--------------|---------------|------------|
   | 버킷 | AEM 인스턴스 | Adobe 도메인 이름(`.adobeaemcloud.com`)이 없는 AEM 인스턴스 이름. 예를 들어 `p43162-e177398`을(를) 버킷으로 사용합니다. |
   | 보안 | 전달자 토큰 | Adobe Developer Console 프로젝트의 OAuth 서버 간 자격 증명에서 액세스 토큰 사용 |
   | 본문 | 템플릿 | XDP를 업로드하여 PDF 양식을 생성합니다. 예를 들어 [이 XDP](/help/forms/assets/ClosingForm.xdp)를 사용하여 PDF을 생성할 수 있습니다. |
   | 본문 | 데이터 | 템플릿과 병합하여 미리 채워진 PDF 양식을 생성할 데이터가 포함된 선택적 XML 파일입니다. 예를 들어 [이 XML](/help/forms/assets/ClosingForm.xml)을 사용하여 PDF을 생성할 수 있습니다. |
   | 매개변수 | X-Adobe-Accept-Experimental | 1 |

5. API를 호출하려면 **보내기**&#x200B;를 클릭하십시오.

   ![API 보내기](/help/forms/assets/api-send.png)

6. **응답** 탭에서 응답을 확인하십시오.
   - 응답 코드가 `200`이면 PDF이 성공적으로 만들어졌습니다.
   - 응답 코드가 `400`이면 요청 매개 변수가 잘못되었거나 형식이 잘못되었음을 의미합니다.
   - 응답 코드가 `500`이면 내부 서버 오류가 있음을 의미합니다.

   이 경우 응답 코드는 `200`입니다. 이는 PDF이 성공적으로 생성되었음을 의미합니다.

   ![응답 검토](/help/forms/assets/api-success.png)

   이제 [다운로드](/help/forms/assets/create-pdf.pdf) 단추를 사용하여 **만든 PDF**&#x200B;을(를) 다운로드하고 PDF 뷰어에서 볼 수 있습니다.

   ![PDF 보기](/help/forms/assets/create-pdf.png)

>[!NOTE]
>
> 테스트 목적으로 [Postman](https://www.postman.com/), [curl](https://curl.se/) 또는 기타 REST 클라이언트를 사용하여 AEM API를 호출할 수도 있습니다.

#### B. NodeJS 응용 프로그램을 개발하여 프로그래밍 방식으로

**문서 서비스 API**&#x200B;를 사용하여 **XDP** 템플릿과 **XML** 데이터 파일에서 입력 가능한 PDF 양식을 생성하도록 Node.js 응용 프로그램을 개발하십시오.

##### 사전 요구 사항

- 시스템에 설치된 Node.js
- 활성 AEM as a Cloud Service 인스턴스
- Adobe Developer Console의 API 인증을 위한 전달자 토큰
- 샘플 XDP 파일: [ClosingForm.xdp](/help/forms/assets/ClosingForm.xdp)
- 샘플 XML 파일: [ClosingForm.xml](/help/forms/assets/ClosingForm.xml)

Node.js 애플리케이션을 개발하려면 단계별 개발을 따르십시오.

##### 1단계: 새 Node.js 프로젝트 만들기

cmd/terminal을 열고 다음 명령을 실행합니다.

```bash
# Create a new directory
mkdir demo-nodejs-generate-pdf
cd demo-nodejs-generate-pdf

##### Initialize Node.js project
npm init -y
```

![새 노드 js 프로젝트 만들기](/help/forms/assets/api-1.png)

##### 2단계: 필요한 종속성 설치

**node-fetch**, **dotenv** 및 **form-data** 라이브러리를 설치하여 HTTP 요청을 하고, 환경 변수를 읽고, 양식 데이터를 각각 처리합니다.

```bash
npm install node-fetch
npm install dotenv
npm install form-data
```

![npm 종속성 설치](/help/forms/assets/api-2.png)

##### 3단계: package.json 업데이트

1. cmd/terminal을 열고 다음 명령을 실행합니다.

   ```bash
   code .
   ```

   ![편집기에서 프로젝트 열기](/help/forms/assets/api-3.png)

   코드 편집기에서 프로젝트가 열립니다.

2. `package.json` 파일을 업데이트하여 `type`을(를) `module`에 추가합니다.

   ```bash
   {
   "name": "demo-nodejs-generate-pdf",
   "version": "1.0.0",
   "type": "module",
   "main": "index.js",
   }
   ```

   ![패키지 파일 업데이트](/help/forms/assets/api-4.png)

##### 4단계: .env 파일 만들기

1. 프로젝트의 루트 수준에서 .env 파일 만들기
2. 다음 구성을 추가하고 자리 표시자를 ADC 프로젝트의 OAuth 서버 간 자격 증명의 실제 값으로 바꿉니다.

   ```bash
   CLIENT_ID=<ADC Project OAuth Server-to-Server credential ClientID>
   CLIENT_SECRET=<ADC Project OAuth Server-to-Server credential Client Secret>
   SCOPES=<ADC Project OAuth Server-to-Server credential Scopes>
   ```

   ![환경 파일 만들기](/help/forms/assets/api-5.png)

   >[!NOTE]
   >
   > Adobe Developer Console 프로젝트에서 `CLIENT_ID`, `CLIENT_SECRET` 및 `SCOPES`을(를) 복사할 수 있습니다.

##### 5단계: src/index.js 만들기

1. 프로젝트의 루트 수준에서 `index.js` 파일 만들기
2. 다음 코드를 추가하고 자리 표시자를 실제 값으로 바꿉니다.

```javascript
// Import the dotenv configuration to load environment variables from the .env file
import "dotenv/config";

// Import fetch for making HTTP requests
import fetch from "node-fetch";
import fs from "fs";
import FormData from "form-data";

// REPLACE THE FOLLOWING VALUE WITH YOUR OWN
const bucket = <bucket-value>; // Your AEM Cloud Service Bucket name
const xdpFilePath = <xdp-file>;
const xmlFilePath = <xml-file>;

// Load environment variables
const clientId = process.env.CLIENT_ID;
const clientSecret = process.env.CLIENT_SECRET;
const scopes = process.env.SCOPES;

// Adobe IMS endpoint for obtaining an access token
const adobeIMSV3TokenEndpointURL = "https://ims-na1.adobelogin.com/ims/token/v3";

// Function to get an access token
const getAccessToken = async () => {
    console.log("Getting access token from IMS...");

    const options = {
        method: "POST",
        headers: {
            "Content-Type": "application/x-www-form-urlencoded",
        },
        body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}&scope=${scopes}`,
    };

    const response = await fetch(adobeIMSV3TokenEndpointURL, options);
    const responseJSON = await response.json();

    console.log("Access token received.");
    return responseJSON.access_token;
};

// Function to generate PDF form from XDP and XML
const generatePDF = async () => {
    const accessToken = await getAccessToken();

    console.log("Generating PDF form from XDP and XML...");

    // Read XDP and XML files
    const xdpFile = fs.readFileSync(xdpFilePath);
    const xmlFile = fs.readFileSync(xmlFilePath);

    const url = `https://${bucket}.adobeaemcloud.com/adobe/document/generate/pdfform`;

    const formData = new FormData();
    formData.append("template", xdpFile, {
        filename: "form.xdp",
        contentType: "application/vnd.adobe.xdp+xml"
    });
    formData.append("data", xmlFile, {
        filename: "data.xml",
        contentType: "application/xml"
    });

    const response = await fetch(url, {
        method: "POST",
        headers: {
            Authorization: `Bearer ${accessToken}`,
            "X-Api-Key": clientId,
            "X-Adobe-Accept-Experimental": "1",
            ...formData.getHeaders()
        },
        body: formData,
    });

    if (response.ok) {
        const arrayBuffer = await response.arrayBuffer();
        fs.writeFileSync("generatedForm.pdf", Buffer.from(arrayBuffer));
        console.log("✅ PDF form generated successfully (saved as generatedForm.pdf)");
    } else {
        console.error("❌ Failed to generate PDF. Status:", response.status);
        console.error(await response.text());
    }
};

// Run the PDF generation function
generatePDF();
```

![index.js 만들기](/help/forms/assets/api-6.png)

##### 6단계: 응용 프로그램 실행

```bash
node src/index.js
```

![응용 프로그램 실행](/help/forms/assets/api-7.png)

`demo-nodejs-generate-pdf` 폴더에 PDF이 만들어집니다. 생성된 파일 `generatedForm.pdf`을(를) 찾으려면 폴더로 이동합니다.

![만들어진 pdf 보기](/help/forms/assets/api-8.png)

[생성된 PDF](/help/forms/assets/create-pdf.png)을(를) 열어 볼 수 있습니다.

## 문제 해결

### 일반적인 문제 및 가능한 원인

#### 문제 1: 403 금지된 오류

**증상:**

- API 요청이 `403 Forbidden`을(를) 반환함
- 오류 메시지: *액세스 거부* 또는 *권한 부족*
- 올바른 액세스 토큰이 있어도 발생

**가능한 원인:**

- OAuth 서버 간 자격 증명에 연결된 제품 프로필에 권한이 충분하지 않음
- AEM Author의 서비스 사용자 그룹에 필요한 콘텐츠 경로에 대한 권한이 없습니다.

#### 문제 2: 401 승인되지 않은 오류

**증상:**

- API 요청이 `401 Unauthorized`을(를) 반환함
- 오류 메시지: *유효하지 않거나 만료된 토큰*

**가능한 원인:**

- 액세스 토큰이 만료됨(24시간 동안만 유효함)
- 클라이언트 ID와 클라이언트 암호가 잘못되었거나 일치하지 않습니다.
- API 요청에 인증 헤더가 누락되었거나 형식이 잘못되었습니다.

#### 문제 3: 404 찾을 수 없음 오류

**증상:**

- API 요청이 `404 Not Found`을(를) 반환함
- 오류 메시지: *리소스를 찾을 수 없음* 또는 *API 끝점을 찾을 수 없음*

**가능한 원인:**

- AEM 인스턴스의 `api.yaml` 구성에 등록되지 않은 클라이언트 ID
- 잘못된 버킷 매개 변수(AEM 인스턴스 식별자와 일치하지 않음)
- 잘못되었거나 존재하지 않는 리소스 ID(양식 또는 에셋)

#### 문제 4: 서버 간 인증 옵션을 사용할 수 없음

**증상:**

- Adobe Developer Console에서 OAuth 서버 간 옵션이 누락되었거나 비활성화되었습니다.

**가능한 원인:**

- 통합을 만드는 사용자가 연결된 제품 프로필에 **개발자**(으)로 추가되지 않았습니다.

#### 문제 5: 파이프라인 배포 실패

**증상:**

- 구성 파이프라인 실행 실패
- 배포 로그에 `api.yaml`과(와) 관련된 오류가 표시됩니다.

**가능한 원인:**

- 잘못된 YAML 구문(들여쓰기, 인용 부호 또는 배열 형식 문제)
- `api.yaml`이(가) 잘못된 디렉터리에 배치되었습니다.
- 구성에서 클라이언트 ID의 형식이 잘못되었거나 잘못되었습니다.


## 관련 문서

일괄 처리(비동기 API)를 위한 환경을 설정하는 방법에 대해 알아보려면 [AEM Forms as a Cloud Service Communications 일괄 처리](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)를 참조하십시오.
