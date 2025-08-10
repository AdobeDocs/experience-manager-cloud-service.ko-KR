---
title: Edge Delivery Services용 Forms 제출 서비스
description: Adobe의 호스팅된 Forms 제출 서비스를 사용하여 스프레드시트에 양식 제출을 직접 저장합니다. Google Sheets, OneDrive 및 SharePoint 통합에 대한 설정, 구성 및 API 사용에 대해 알아봅니다.
keywords: Forms 제출 서비스, Edge Delivery Services 양식, 스프레드시트 통합, Google Sheets 양식, OneDrive 양식, SharePoint 양식, 양식 데이터 수집
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner, Intermediate
hide: true
hidefromtoc: true
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 60e693593778a558e91d68da41025277438c6f03
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 1%

---

# Edge Delivery Services용 Forms 제출 서비스

Forms 제출 서비스는 양식 제출 데이터를 원하는 스프레드시트(Google Sheets, Microsoft OneDrive 또는 SharePoint)에 직접 자동으로 저장하는 Adobe의 호스팅 솔루션입니다. 따라서 실시간 데이터 수집 및 관리를 제공하면서 복잡한 백엔드 인프라가 필요하지 않습니다.

## 개요

![Forms 제출 서비스](/help/forms/assets/form-submission-service.png)
*그림: Forms 제출 서비스 워크플로 - 양식 제출에서 스프레드시트 저장소로*

+++ 이 서비스를 사용해야 하는 사용자

**완벽한 대상:**

- 간단한 데이터 수집 양식을 작성하는 **콘텐츠 작성자**
- 빠른 양식-스프레드시트 워크플로우가 필요한 **중소기업**
- **마케팅 팀** 리드 정보 수집
- **이벤트 이끌이** 등록 관리

**다음 항목에 대한 대체 요소 고려:**

- 사용자 지정 논리가 필요한 복잡한 워크플로
- 데이터베이스와 엔터프라이즈 통합
- 고급 유효성 검사 또는 처리가 필요한 Forms

+++

+++ 일반적인 사용 사례

| 사용 사례 | 예 | 스프레드시트 이점 |
|----------|---------|-------------------|
| **Forms에 문의** | Google Sheets→ 웹 사이트 문의 | 간편한 후속 작업 및 CRM 가져오기 |
| **이벤트 등록** | Excel Online→ 전화 회의 등록 | 실시간 참석자 추적 |
| **리드 생성** | SharePoint→ 뉴스레터 등록 | 마케팅 캠페인 분석 |
| **피드백 컬렉션** | Google Sheets→ 설문 응답 | 빠른 데이터 시각화 |

+++

## 주요 이점

Forms 제출 서비스는 간소화된 데이터 수집을 위한 몇 가지 이점을 제공합니다.

+++ 간소화된 설정

- **백엔드 인프라가 필요 없음** - Adobe이 제출 엔드포인트를 호스팅함
- 많이 사용하는 스프레드시트 플랫폼과 **직접 통합**
- 양식 필드에서 스프레드시트 열로 **자동 데이터 매핑**

+++


+++ 실시간 데이터 관리

- **즉시 데이터 캡처** - 제출물이 스프레드시트에 즉시 나타납니다.
- **구조화된 저장소** - 쉽게 분석할 수 있도록 구성된 열
- **실시간 공동 작업** - 여러 팀원이 데이터에 액세스하고 데이터를 분석할 수 있습니다.

+++

+++ 내장 보안 및 액세스 제어

- **기존 사용 권한 활용** - 스프레드시트 플랫폼의 공유 컨트롤을 사용합니다.
- **Adobe 관리 보안** - 엔터프라이즈급 보호를 사용하는 보안 제출 엔드포인트
- **데이터 소유권** - 데이터가 선택한 스프레드시트 플랫폼에 있습니다.

+++

## 사전 요구 사항

Forms 제출 서비스를 설정하기 전에 다음을 확인하십시오.



+++ 기술 요구 사항

- 최신 적응형 Forms 블록이 설치된 Edge Delivery Services 프로젝트에 대해 **GitHub 저장소** 설정
- **액세스 승인** - 저장소가 허용 목록에 추가하다에 추가됨

+++

+++ 스프레드시트 플랫폼 설정


지원되는 플랫폼 중 하나를 선택하십시오.

- **Google 시트** - 시트 만들기 권한이 있는 Google 계정
- **Microsoft OneDrive** - Excel Online에 액세스할 수 있는 Microsoft 365 계정
- **SharePoint** - 목록/라이브러리 권한을 가진 SharePoint 액세스

+++

+++ 권한 및 액세스

- 대상 스프레드시트의 **권한 편집**
- **에 대한 액세스 권한을 부여하기 위해**&#x200B;기능 공유`forms@adobe.com`
- 선택한 플랫폼에 대한 **링크 생성** 권한

+++

>[!TIP]
>
>Edge Delivery Services을 처음 사용하십니까?**&#x200B;** 프로젝트 기반을 설정하려면 [시작 자습서](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial)&#x200B;(으)로 시작하십시오.

## 구성 메서드

Forms 제출 서비스는 두 가지 구성 접근 방식을 제공합니다. 워크플로에 가장 적합한 방법 선택:


+++ 구성 방법 선택

| 메서드 | 가장 적합한 형식 | 필요한 시간 | 기술 수준 |
|--------|----------|---------------|-----------------|
| **[수동 설정](#manual-configuration)** | 콘텐츠 크리에이터, 1회 설정 | 10-15분 | 초급자 |
| **[API 구성](#api-configuration)** | 개발자, 자동화된 워크플로 | 5-10분 | 중간 |

+++

+++ 프로젝트 설정

두 방법 중 하나를 구성하기 전에 AEM 프로젝트 기반이 준비되었는지 확인하십시오.

1. 최신 적응형 Forms 블록(**시작 자습서**)을 사용하여 [AEM 프로젝트 만들기 또는 업데이트](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial)
1. **프로젝트 루트에서`fstab.yaml`** 업데이트:

   ```yaml
   # Replace with the path to your shared folder
   mountpoints:
     /: https://drive.google.com/drive/folders/your-shared-folder-id
   ```

1. **과(와)**&#x200B;프로젝트 폴더 공유`forms@adobe.com`(편집 권한 필요)

+++

## 수동 구성

![양식 제출 서비스에 대한 워크플로](/help/forms/assets/forms-submission-service-workflow.png)
*그림: 수동 Forms 제출 서비스 설정에 대한 전체 워크플로*

다음 단계별 지침에 따라 스프레드시트 제출을 사용하여 양식을 설정합니다.



+++ 1단계: 양식 정의 만들기

Google Sheets 또는 Microsoft Excel을 사용하여 양식 구조를 만듭니다.

**양식 만들기 단계:**

1. **스프레드시트 플랫폼을 엽니다**(Google Sheets 또는 Microsoft Excel)
1. 양식 프로젝트용 **새 스프레드시트 만들기**
1. **시트 이름 지정**(`helix-default` 또는 `shared-aem`이어야 함)
1. **양식 만들기 가이드**&#x200B;를 사용하여 [양식 구조를 정의](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)

![양식 정의](/help/forms/assets/form-submission-definition.png)
*예: 필드 유형, 레이블 및 유효성 검사 규칙을 사용한 양식 정의*

>[!IMPORTANT]
>
>**시트 이름 지정 요구 사항**
>
>양식 정의 시트의 이름은 다음 중 하나여야 합니다.
>
>- `helix-default`(단일 양식에 권장)
>- `shared-aem`(다중 양식 프로젝트의 경우)
>
>다른 시트 이름은 시스템에서 인식되지 않습니다.

**유효성 검사 검사점:**

- 양식 구조가 모든 필수 필드로 완료되었습니다.
- 시트 이름이 올바르게 지정됨(`helix-default` 또는 `shared-aem`)
- 필드 유형 및 유효성 검사 규칙이 올바르게 구성됨

+++

+++ 2단계: 데이터 수집 시트 만들기

양식 제출 데이터를 받을 전용 시트를 설정합니다.

**데이터 시트 설정:**

1. 기존 스프레드시트에 **새 시트 추가**
1. **시트 이름을 정확히`incoming`**&#x200B;로 지정합니다(대/소문자 구분).
1. 양식 필드와 일치하는 **열 머리글 설정**
1. 변경 내용을 유지하려면 **스프레드시트를 저장**&#x200B;하세요.

![받는 시트](/help/forms/assets/form-submission-incoming-sheet.png)
*예: 양식 필드와 일치하는 열 머리글이 있는 시트를 가져오는 중*

>[!WARNING]
>
>**중요 요구 사항**
>
>시트 이름은 정확히 `incoming`(소문자)이어야 합니다. 이 시트 제외:
>
>- 양식 제출이 거부됨
>- 데이터가 저장되지 않습니다.
>- 사용자에게 제출 오류가 표시됩니다.

**유효성 검사 검사점:**

- 스프레드시트에 `incoming`장이 있음
- 열 헤더가 양식 필드 이름과 일치함
- 시트가 올바르게 저장되고 액세스할 수 있음

>[!TIP]
>
>**Pro 팁:** 양식 필드와 스프레드시트 열 간에 완벽하게 일치하도록 양식 정의에서 정확한 필드 이름을 복사합니다.

+++

+++ 3단계: Adobe Service와 스프레드시트 공유

Adobe Forms 제출 서비스에 스프레드시트에 대한 액세스 권한을 부여합니다.

**공유 프로세스:**

1. 스프레드시트의 오른쪽 상단에 있는 **공유 단추를 클릭합니다**
1. **Adobe 서비스 계정 추가:**

   - 전자 메일: `forms@adobe.com`
   - 권한 수준: **편집기**(데이터 쓰기에 필요)

1. **공유 초대 보내기**
1. 다음 단계를 위해 **스프레드시트 링크 복사**

   ![수신 시트 공유](/help/forms/assets/form-submission-share-incoming.png)
   *Adobe 서비스 액세스 권한을 부여하기 위한 단계별 공유 프로세스*

**플랫폼별 지침:**

**Google 시트:**

- `forms@adobe.com`을(를) 편집기로 추가
- &quot;링크가 있는 모든 사용자가 볼 수 있음&quot;이 활성화되었는지 확인합니다.
- 공유 가능한 링크 복사

**Microsoft Excel(OneDrive/SharePoint):**

- 편집 권한이 있는 `forms@adobe.com` 추가
- 링크 공유를 &quot;링크가 있는 모든 사용자가 편집할 수 있음&quot;으로 설정
- 공유 URL 복사

  ![수신 시트의 링크 복사](/help/forms/assets/form-submission-copy-link.png)
  *예: 양식 구성에 대한 공유 가능한 링크 복사*

**유효성 검사 검사점:**

- `forms@adobe.com`이(가) 스프레드시트에 대한 편집기 액세스 권한이 있습니다.
- 스프레드시트 링크가 복사되어 사용할 수 있습니다.
- 권한을 공유하면 외부 액세스가 허용됨

+++

+++ 4단계: 스프레드시트에 양식 연결

양식 정의를 제출 스프레드시트에 연결합니다.

**양식 스프레드시트 연결:**

1. **양식 정의 스프레드시트 열기**(`helix-default` 또는 `shared-aem`시트가 있는 스프레드시트)
1. 양식 정의에서 **제출 필드 행 찾기**
1. **복사한 스프레드시트 링크**&#x200B;를 제출 필드의 **Action** 열에 붙여 넣습니다.
1. 양식 정의에 **변경 내용을 저장**

   ![스프레드시트 연결](/help/forms/assets/form-submission-sheet-linking.png)
   *예: 데이터 수집 스프레드시트에 제출 동작 연결*

**양식 게시:**

1. 브라우저에서 **AEM Sidekick 열기**
1. 구성을 테스트하려면 **양식 미리 보기**
1. 라이브로 만들려면 **양식을 게시**

**최종 유효성 검사:**

- 스프레드시트 링크가 제출 필드 작업에 올바르게 추가됩니다.
- 양식 정의가 저장되고 게시됨
- 양식 미리 보기에 모든 필드가 올바르게 표시됨
- 제출 버튼이 올바르게 구성됨

>[!SUCCESS]
>
>**설치가 완료되었습니다.** 이제 양식이 Forms 제출 서비스에 연결되어 있습니다. 샘플 데이터를 제출하고 `incoming` 시트를 확인하여 테스트합니다.

**참조 자료:**

- 적절한 구성이 있는 [예제 스프레드시트](/help/forms/assets/spreadsheet.xlsx) 작성
- 게시 지침에 대한 [AEM Sidekick 설명서](https://www.aem.live/docs/sidekick)

+++

## API 구성

API 메서드를 사용하면 개발자가 자동화된 워크플로우 및 사용자 정의 통합에 이상적인 Forms 제출 서비스에 데이터를 프로그래밍 방식으로 제출할 수 있습니다.


+++ API 사용 시기

**완벽한 대상:**

- 자동화된 데이터 수집 시스템
- 사용자 정의 양식 구현
- 기존 애플리케이션과 통합
- 대량 데이터 제출 워크플로우

+++

+++ API 사전 요구 사항

API를 사용하기 전에 다음을 확인하십시오.

- **스프레드시트 설정** 완료(`incoming`장 포함)
- **에게** Adobe 서비스 액세스`forms@adobe.com` 부여
- 게시된 양식의 **양식 ID**
- **저장소 정보**(조직 및 사이트 이름)

>[!IMPORTANT]
>
>**필요한 설정 단계**
>
>API를 사용하려면 수동 구성과 동일한 스프레드시트 설정이 필요합니다.
>
>- `incoming`장이 있어야 합니다.
>- `forms@adobe.com`에 편집기 액세스 권한이 있어야 합니다.
>- 시트는 AEM Sidekick을 통해 게시해야 합니다.

+++

+++ API 끝점 및 인증

**기본 URL:** `https://forms.adobe.com/adobe/forms/af/submit/{id}`

**필수 헤더:**

- `Content-Type: application/json`
- `x-adobe-routing: tier=live,bucket=main--[repository]--[organization]`

**API 설명서:** [전체 API 참조](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)

+++

+++ Postman 사용

Postman은 API 제출을 테스트할 수 있는 사용자 친화적인 인터페이스를 제공합니다.

**설치 지침:**

1. Postman에서 **새 POST 요청 만들기**
1. **끝점 구성:** `https://forms.adobe.com/adobe/forms/af/submit/{id}`
1. **자리 표시자 바꾸기:**

   - 실제 양식 ID→ `{id}`
   - GitHub 저장소 이름→ `[repository]`
   - GitHub 조직/사용자 이름→ `[organization]`

**요청 구성:**

```json
POST https://forms.adobe.com/adobe/forms/af/submit/your-form-id

Headers:
Content-Type: application/json
x-adobe-routing: tier=live,bucket=main--your-repo--your-org

Body (JSON):
{
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
}
```

**예상 응답:**

- **상태 코드:** `201 Created`
- **스프레드시트 시트에**&#x200B;데이터가 즉시 표시됨`incoming`

![postman 화면](/help/forms/assets/postman-api.png)
*예: Postman 인터페이스를 사용하여 API를 제출했습니다*

+++

+++ 명령줄 사용(curl)

터미널/명령 프롬프트를 선호하는 개발자의 경우 curl을 사용하여 데이터를 프로그래밍 방식으로 제출하십시오.

**명령줄 설정:**

아래 명령에서 다음 자리 표시자를 바꿉니다.

- 실제 양식 ID→ `{id}`
- GitHub 저장소 이름→ `[repository]`
- GitHub 조직/사용자 이름→ `[organization]`

>[!BEGINTABS]

>[!TAB macOS/Linux]

```bash
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" \
    --header "Content-Type: application/json" \
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" \
    --data '{
        "data": {
            "startDate": "2025-01-10",
            "endDate": "2025-01-25",
            "destination": "Australia",
            "class": "First Class",
            "budget": "2000",
            "amount": "1000000",
            "name": "Joe",
            "age": "35",
            "subscribe": null,
      "email": "joe@example.com"
                }
            }'
```

>[!TAB Windows 명령 프롬프트]

```cmd
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" ^
    --header "Content-Type: application/json" ^
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" ^
  --data "{\"data\": {\"startDate\": \"2025-01-10\", \"endDate\": \"2025-01-25\", \"destination\": \"Australia\", \"class\": \"First Class\", \"budget\": \"2000\", \"amount\": \"1000000\", \"name\": \"Joe\", \"age\": \"35\", \"subscribe\": null, \"email\": \"joe@example.com\"}}"
```

>[!TAB Windows PowerShell]

```powershell
$body = @{
  data = @{
    startDate = "2025-01-10"
    endDate = "2025-01-25"
    destination = "Australia"
    class = "First Class"
    budget = "2000"
    amount = "1000000"
    name = "Joe"
    age = "35"
    subscribe = $null
    email = "joe@example.com"
  }
} | ConvertTo-Json -Depth 3

Invoke-RestMethod -Uri "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" `
  -Method POST `
  -Headers @{"Content-Type"="application/json"; "x-adobe-routing"="tier=live,bucket=main--your-repo--your-org"} `
  -Body $body
```

>[!ENDTABS]

+++

+++ API 응답 및 확인

**성공한 응답:**

```http
HTTP/1.1 201 Created
Connection: keep-alive
Content-Length: 0
X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
Date: Fri, 10 Jan 2025 13:06:10 GMT
Access-Control-Allow-Origin: *
```

**데이터 확인:**

제출 후 스프레드시트에 데이터가 표시되는지 확인합니다.

![업데이트된 시트](/help/forms/assets/updated-sheet.png)
*예: API를 통해 들어오는 시트에 데이터를 썼습니다*

**응답 유효성 검사:**

- **HTTP 상태:** `201 Created`은(는) 성공적으로 제출했음을 나타냅니다.
- **X-Request-Id:** 제출 추적을 위한 고유 식별자
- **데이터가** 시트에 `incoming`초 이내에 표시됨
- **모든 양식 필드**&#x200B;이(가) 스프레드시트 열에 올바르게 매핑되었습니다.

+++

## 문제 해결



+++ 일반적인 문제 및 솔루션

**문제: 403 사용할 수 없는 오류**

```
Causes: Missing or incorrect access permissions
Solutions:
- Verify forms@adobe.com has Editor access to your spreadsheet
- Check that your repository is added to the allowlist
- Confirm the x-adobe-routing header format
```

**문제: 404 찾을 수 없음 오류**

```
Causes: Incorrect Form ID or endpoint URL
Solutions:  
- Verify your Form ID is correct
- Check the API endpoint URL format
- Ensure your form is published and live
```


**문제: 스프레드시트에 데이터가 표시되지 않음**

```
Causes: Missing 'incoming' sheet or permission issues
Solutions:
- Confirm 'incoming' sheet exists (case-sensitive)
- Verify column headers match form field names exactly
- Check forms@adobe.com has edit permissions
- Ensure spreadsheet is shared properly
```


**문제: 잘못된 JSON 형식 오류**

```
Causes: Malformed request body
Solutions:
- Validate JSON syntax using online JSON validators
- Ensure proper escaping of special characters
- Check quote marks and brackets are balanced
```


+++

+++ 도움말 보기

**지원 채널:**

- **조기 액세스 문제:** 전자 메일 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)
- **API 설명서:** [개발자 참조](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)
- **커뮤니티 지원:** [Adobe Experience League 커뮤니티](https://experienceleaguecommunities.adobe.com/?profile.language=ko)

+++

## 다음 단계

Forms 제출 서비스를 구성했으므로 이제 다음 관련 항목을 살펴보십시오.


+++ Forms 기능 향상

- **[고급 Forms 만들기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)** - 유효성 검사, 조건부 논리 및 사용자 지정 스타일 추가
- **[양식 구성 요소 안내서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/forms-components)** - 사용 가능한 양식 필드 형식 살펴보기

+++

+++ 대체 제출 방법

- **[AEM 게시 제출](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)** - 복잡한 워크플로 및 엔터프라이즈 통합용
- **[사용자 지정 제출 액션](/help/forms/configure-submit-actions-core-components.md)** - 고급 제출 처리

+++

+++ 데이터 관리

- **[양식 분석](/help/forms/view-understand-aem-forms-analytics-reports.md)** - 양식 성능 및 사용 추적
- **[데이터 통합](/help/forms/configure-data-sources.md)** - 양식을 데이터베이스 및 CRM 시스템에 연결

+++

## 요약

Forms 제출 서비스는 양식 데이터를 스프레드시트로 직접 수집할 수 있는 강력한 코드 없는 솔루션을 제공합니다. 주요 이점은 다음과 같습니다.

- **빠른 설정** - 백엔드 인프라가 필요하지 않습니다.
- **실시간 데이터** - 즉시 제출 캡처
- **유연한 플랫폼** - Google Sheets, OneDrive 또는 SharePoint
- **API 액세스** - 프로그래밍 방식 제출 기능
- **엔터프라이즈 보안** - 액세스 제어가 포함된 Adobe 관리 끝점

**시작할 준비가 되셨습니까?** 시각적 설정을 보려면 [수동 구성](#manual-configuration) 안내서를 따르거나 프로그래밍 통합을 위해 [API 구성](#api-configuration)(으)로 이동하십시오.
