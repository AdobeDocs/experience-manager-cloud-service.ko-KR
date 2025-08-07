---
title: Edge Delivery Services를 사용하여 AEM Forms에 제출 액션 구성
description: Edge Delivery Services를 사용하여 AEM Forms에서 제출 액션을 구성하는 방법을 알아봅니다. 안전하고 효율적으로 양식 데이터를 처리하려면 Forms 제출 서비스와 AEM Publish 제출 액션 중에서 선택합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 12%

---

# AEM Forms에 대한 제출 액션 구성

양식 제출 처리를 구성하여 Edge Delivery Services과 함께 AEM Forms을 사용하여 데이터를 스프레드시트, 이메일 또는 백엔드 시스템으로 라우팅합니다.

## 빠른 결정 안내서

제출 방법 선택:

| 메서드 | 가장 적합한 형식 | 설정 복잡성 | 사용 사례 |
|--------|----------|------------------|-----------|
| **Forms 제출 서비스** | 간단한 데이터 캡처 | 낮음 | 연락처 양식, 설문 조사, 기본 데이터 수집 |
| **AEM 게시 제출** | 복잡한 워크플로우 | 높음 | 엔터프라이즈 통합, 사용자 정의 처리, 워크플로우 |

## 사전 요구 사항

제출 작업을 구성하기 전에 다음 사항을 확인합니다.

- AEM Forms as a Cloud Service 인스턴스
- Edge Delivery Services 프로젝트 구성됨
- 문서 작성 또는 유니버설 편집기를 사용하여 만든 양식
- 타겟 대상(스프레드시트, 이메일 시스템 또는 AEM)에 필요한 권한

+++ 방법 1: Forms 제출 서비스

Forms 제출 서비스는 간단한 데이터 캡처 시나리오에 적합한 Adobe 호스팅 엔드포인트입니다.

### 지원되는 대상

- **스프레드시트**: Google Sheets, Microsoft Excel(OneDrive/SharePoint)
- **전자 메일**: 지정된 전자 메일 주소로 양식 데이터를 보냅니다.

### 구성 단계

1. **대상 액세스 설정**
   - 스프레드시트의 경우: 대상 스프레드시트의 `forms@adobe.com`에 대한 편집 권한 부여
   - 이메일의 경우: 수신자 이메일 주소에 액세스할 수 있는지 확인

2. **양식 제출 구성**
   - 작성 환경에서 양식을 엽니다
   - 제출 액션을 &quot;Forms 제출 서비스&quot;로 설정
   - 대상 스프레드시트 URL 또는 이메일 주소 지정
   - 양식 저장 및 게시

3. **제출 테스트**
   - 양식을 통해 테스트 데이터 제출
   - 데이터가 대상 대상에 표시되는지 확인
   - 제출 실패 시 오류 로그 확인

### 중요 정보

- 서비스 계정 `forms@adobe.com`에 대상 스프레드시트에 대한 편집 액세스 권한이 필요합니다.
- 양식 제출 즉시 이메일 알림이 전송됩니다.
- 서비스 수준에서 데이터 유효성 검사 수행

![Forms 제출 서비스 흐름](/help/forms/assets/eds-fss.png)

+++

+++ 방법 2: AEM 게시 제출

복잡한 처리를 위해 양식 데이터를 AEM as a Cloud Service 게시 인스턴스에 직접 제출합니다.

### AEM 게시를 사용해야 하는 경우

- 제출 후 필요한 사용자 지정 AEM 워크플로
- 데이터베이스와의 양식 데이터 모델(FDM) 통합
- 타사 서비스 통합(Marketo, Power Automate, Workfront Fusion)
- Azure Blob Storage 또는 SharePoint 문서 라이브러리
- 복잡한 서버측 유효성 검사 또는 처리 논리

### 사용 가능한 제출 작업

- [REST 엔드포인트에 제출](/help/forms/configure-submit-action-restpoint.md)
- [AEM 메일 서비스를 통해 이메일 보내기](/help/forms/configure-submit-action-send-email.md)
- [Forms 데이터 모델을 사용하여 제출](/help/forms/configure-data-sources.md)
- [AEM 워크플로 호출](/help/forms/aem-forms-workflow-step-reference.md)
- [SharePoint에 제출](/help/forms/configure-submit-action-sharepoint.md)
- [OneDrive에 제출](/help/forms/configure-submit-action-onedrive.md)
- [Azure Blob Storage에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Microsoft Power Automate에 제출](/help/forms/forms-microsoft-power-automate-integration.md)
- [Adobe Workfront Fusion에 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Adobe Marketo Engage에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![AEM 게시 제출 흐름](/help/forms/assets/eds-aem-publish.png)

### 구성 요구 사항

#### &#x200B;1. AEM Dispatcher 구성

AEM 게시 인스턴스에서 Dispatcher을 구성합니다.

- **제출 경로 허용**: `filters.any`에 대한 POST 요청을 허용하도록 `/adobe/forms/af/submit/...`을(를) 수정하십시오.
- **리디렉션 없음**: Dispatcher 규칙이 양식 제출 경로를 리디렉션하지 않는지 확인

#### &#x200B;2. OSGi 레퍼러 필터

AEM OSGi 콘솔(`/system/console/configMgr`)에서:

1. &quot;Apache Sling Referrer Filter&quot; 찾기
2. &quot;호스트 허용&quot; 목록에 Edge Delivery 도메인 추가
3. `https://your-eds-domain.hlx.page`과(와) 같은 도메인 포함

#### &#x200B;3. CDN 리디렉션 규칙

제출을 라우팅하도록 Edge Delivery CDN을 구성합니다.

- `/adobe/forms/af/submit/...`에서 AEM 게시 인스턴스로 요청 라우팅
- 구현은 CDN 공급자(Fastly, Akamai, Cloudflare)에 따라 다릅니다.

#### &#x200B;4. 양식 구성

1. 유니버설 편집기에서 양식 만들기
2. Target AEM Forms 작업에 제출 액션 구성
3. 제출 엔드포인트 경로 지정
4. Edge Delivery 사이트에 양식 게시

+++

+++ 양식 포함(선택 사항)

한 위치에서 만든 양식을 다른 웹 페이지나 사이트에 임베드합니다.

### 사용 사례

- 여러 랜딩 페이지에서 표준 양식 재사용
- 문서 작성 컨텐츠에 전문 양식 포함
- 여러 EDS 프로젝트에서 단일 양식 유지 관리

### CORS 구성

양식 원본에서 원본 간 리소스 공유 구성:

1. **CORS 헤더를 추가하여** 원본 응답을 만듭니다.
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`
   - `Access-Control-Allow-Headers: Content-Type`

2. **예제 구성**:

   양식을 호스팅하는 사이트에 대한     # 구성
       헤더:
       - 경로: /forms/**
       사용자 지정:
       Access-Control-Allow-Origin: https://host-domain.com
       Access-Control-Allow-Methods: GET, OPTIONS
   
### 단계 포함

1. **양식 만들기 및 게시**
   - 문서 작성 또는 유니버설 편집기를 사용하여 양식 작성
   - 제출 방법 구성(FSS 또는 AEM 게시)
   - 독립 실행형 URL에 게시

2. **CORS 구성**
   - 양식 소스 사이트에서 CORS 헤더 설정
   - 호스트 페이지 도메인에서 양식 가져오기 허용

3. **호스트 페이지에 포함**
   - 호스트 페이지에 양식 포함 블록 추가
   - 게시된 양식 URL로 블록 지정
   - 호스트 페이지 게시

![임베드된 양식 아키텍처](/help/forms/assets/eds-embedded-form.png)

+++

+++ 일반적인 문제

| 문제 | 솔루션 |
|-------|----------|
| **양식 제출 실패** | 콘솔 오류 확인, 끝점 URL 확인, 권한 확인 |
| **포함된 양식이 표시되지 않음** | 양식 소스에서 CORS 헤더 구성, 양식 URL 확인 |
| AEM에서 **403/401 오류 발생** | Sling 레퍼러 필터 업데이트, 인증 설정 확인 |
| **데이터가 스프레드시트에 도달하지 않음** | `forms@adobe.com`에 편집 액세스 권한이 있는지 확인하고 스프레드시트 URL을 확인하십시오. |
| **CORS 오류** | 양식 원본에 적절한 `Access-Control-Allow-Origin` 헤더 추가 |

+++

## 구성 예

+++ 스프레드시트 제출이 있는 문서 기반 양식

1. Google Docs/Sheets에서 양식 구조 만들기
2. Forms 제출 서비스 엔드포인트 구성
3. 대상 스프레드시트에 `forms@adobe.com` 편집 액세스 권한 부여
4. Edge Delivery 사이트에 문서 게시
5. 양식 제출 및 데이터 흐름 테스트

+++

+++ AEM 워크플로가 포함된 유니버설 편집기 양식

1. 유니버설 편집기에서 양식 작성
2. 제출 액션을 &quot;AEM 워크플로 호출&quot;로 구성
3. AEM Publish에서 Dispatcher 및 레퍼러 필터 설정
4. CDN 라우팅 규칙 구성
5. 양식 게시 및 워크플로우 실행 테스트

+++

## 모범 사례

- 간단한 데이터 캡처 시나리오에 **Forms 제출 서비스 사용**
- 복잡한 처리 또는 통합이 필요한 경우 **AEM 게시 선택**
- 프로덕션 배포 전에 스테이징 환경에서 **철저하게 테스트**
- AEM 로그 및 콘솔 오류를 사용하여 **제출 모니터링**
- 실패한 제출에 대해 **올바른 오류 처리 구현**
- 클라이언트 및 서버 수준 모두에서 **데이터 유효성 검사**
- 모든 양식 제출 및 데이터 전송에 **HTTPS 사용**

## 관련 항목

- [EDS Forms을 사용한 문서 기반 작성](/help/edge/docs/forms/tutorial.md)
- [EDS Forms을 사용한 유니버설 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [AEM Forms 제출 서비스](/help/forms/forms-submission-service.md)
- [데이터 소스 구성](/help/forms/configure-data-sources.md)
- [AEM Forms 워크플로우 참조](/help/forms/aem-forms-workflow-step-reference.md)
