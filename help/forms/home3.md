---
title: AEM Forms as a Cloud Service - 디지털 양식 플랫폼
description: 모듈식 구성 요소를 사용하여 디지털 양식을 구축, 통합 및 최적화합니다. 적응형 양식, Data Connectors, 워크플로우 자동화, 분석 및 관리 도구 중에서 선택하여 강력한 양식 경험을 만들 수 있습니다.
landing-page-description: 양식 생성, 데이터 통합, 프로세스 자동화, 분석 및 거버넌스를 위한 독립 구성 요소가 포함된 모듈식 디지털 양식 플랫폼입니다.
keywords: AEM Forms, 디지털 양식, 양식 빌더, 적응형 양식, 양식 통합, 워크플로우 자동화, 양식 분석, 문서 서비스
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
index: false
exl-id: e8c37209-4d8e-4eaf-9e29-ffe32b841eb1
source-git-commit: eca09e1bf2ba4466f54e915e01218cc89cf5b116
workflow-type: tm+mt
source-wordcount: '1932'
ht-degree: 1%

---

# AEM Forms as a Cloud Service {#aem-forms-platform}

모듈식 구성 요소를 사용하여 디지털 양식을 구축, 통합 및 최적화합니다. AEM Forms은 비즈니스 요구 사항에 맞는 강력한 양식 경험을 만들기 위해 함께 작동하는 독립 제품이나 독립 실행형 제품을 제공합니다.

간단한 양식 작성에서 복잡한 문서 워크플로, 데이터 통합 및 고급 분석에 이르기까지 필요한 구성 요소를 선택합니다.

## 새로운 기능 {#whats-new}

**최신 릴리스 특징:**

- **날짜 및 시간 입력 구성 요소** - 달력 및 시계 인터페이스를 통한 사용자 입력 개선
- **파일 업로드 보안 향상** - 자동 유효성 검사 및 콘텐츠 형식 확인
- **향상된 오류 처리** - 사용자 지정 제출 작업에 대한 특정 오류 코드로 디버깅 개선
- **기록 향상 문서** - 더 깨끗한 문서 생성을 위해 숨겨진 필드를 제외하는 옵션

**시험판 기능:**

- **AFP 형식 지원** - 통신 API를 통한 엔터프라이즈급 인쇄 기능
- **규칙 편집기 개선 사항** - 최신 JavaScript 지원 및 동적 변수
- **향상된 유효성 검사 메서드** - 패널, 필드 및 양식 수준 유효성 검사 개선 사항

[전체 릴리스 정보 보기 →](/help/release-notes/release-notes-cloud/release-notes-current.md#forms)

## 조기 액세스 프로그램 {#early-access}

혁신적인 최신 AEM Forms에 독점적으로 액세스하십시오.

- **🤖AEM Forms AI Assistant** - 자동화된 양식 생성 및 최적화를 위한 생성 AI
- **✍️스크리블 서명 구성 요소** - 양식 내에서 직접 서명 캡처
- **🔗직접 API 통합** - 양식 데이터 모델 설정 없이 API에 연결
- **📊Forms 최적화** - AI 기반 성능 분석 및 전환 개선 사항

[액세스 요청 →](mailto:aem-forms-ea@adobe.com) | [자세히 →](/help/forms/early-access-ea-features.md)

## 📋 양식 만들기 및 작성 {#form-creation}

사용자의 요구 사항과 기술 요구 사항에 가장 적합한 작성 접근 방식을 사용하여 양식을 작성합니다.

### 핵심 구성 요소 Forms {#core-components}

| **핵심 구성 요소 Forms** |
|---|
| 최신 웹 표준을 사용하는 현대적이고 반응형 양식 구축. 여러 장치에서 자동으로 작동하는 적응형 양식을 만들고 API 기반 전달을 위한 Headless 양식을 생성합니다. |
| **기능:** 최신 구성 요소, 자동 반응형 디자인 및 기본 제공 접근성 기능이 포함된 시각적 드래그 앤 드롭 양식 빌더입니다. |
| **사용 시기:** 새 프로젝트, 최신 웹 경험, Headless 양식 게재, 모바일 우선 디자인 |
| ✅ 반응형 디자인 ✅ 접근성 준수 ✅ Headless 기능 ✅ 최신 UI 구성 요소 |
| [핵심 구성 요소 시작 →](/help/forms/creating-adaptive-form-core-components.md) |

### 기초 구성 요소 Forms {#foundation-components}

| **기초 구성 요소 Forms** |
|---|
| 기존 프로젝트 및 레거시 통합을 위한 양식 구축 접근 방식을 확립했습니다. 광범위한 맞춤화 옵션을 제공하는 검증된 구성 요소 |
| **기능:** 포괄적인 구성 요소 라이브러리와 광범위한 사용자 지정 기능을 갖춘 기존의 적응형 양식 작성. |
| **사용 시기:** 기존 프로젝트, 레거시 시스템 통합, 특정 사용자 지정 요구 사항, 확립된 워크플로 |
| ✅ 확장 구성 요소 라이브러리 ✅ 세부 사용자 지정 ✅ 레거시 호환성 ✅ 입증된 안정성 |
| [기초 구성 요소 시작 →](/help/forms/creating-adaptive-form.md) |

### Edge Delivery Forms {#edge-delivery}

| **Edge Delivery Forms** |
|---|
| Microsoft Excel과 같은 익숙한 도구를 사용하여 고성능 양식을 작성합니다. 탁월한 로딩 속도와 SEO 성능을 구현합니다. |
| **수행할 작업:** Excel 스프레드시트를 사용하여 양식을 만들고 최적의 Google Lighthouse 점수로 고성능 에지 전달 네트워크에 게시합니다. |
| **사용 시기:** 성능 중요한 응용 프로그램, SEO 중심의 프로젝트, 콘텐츠 작성자 중심의 양식 만들기, 글로벌 콘텐츠 전달. |
| ⚡ Excel 기반 작성 ⚡ 빠르게 로드 ⚡ 최적의 SEO ⚡ 전역 CDN 게재 |
| [Edge Delivery → 시작](/help/edge/docs/forms/overview.md) |

### HTML5 양식 {#html5-forms}

| **HTML5 양식** |
|---|
| 모바일 장치 및 레거시 브라우저에 대해 XFA 기반 양식을 HTML5로 렌더링합니다. 기본 모바일 경험을 제공하면서 양식 논리를 유지합니다. |
| **기능:** XFA 양식 템플릿을 기본 모바일 환경과 브라우저 간 호환성을 갖춘 HTML5 양식으로 변환합니다. |
| **사용할 시기:** XFA 양식 현대화, 모바일 최적화, 레거시 브라우저 지원, 기존 XDP 투자. |
| 📱 XFA 호환성 📱 모바일 최적화 📱 교차 브라우저 지원 📱 플러그인 요구 사항 없음 |
| [HTML5 Forms →](/help/forms/introductionhtml5.md) 시작 |

### 대화형 통신 {#interactive-communications}

| **대화형 통신** |
|---|
| 동적 데이터 통합이 포함된 시각적 편집기를 사용하여 명령문, 송장 및 공지 등의 문서 중심 통신을 만들 수 있습니다. |
| **수행할 작업:** 인쇄 및 디지털 채널용 동적 데이터와 정적 콘텐츠를 결합하는 개인화된 통신을 디자인합니다. |
| **사용 시기:** 고객 명세서, 청구서, 알림, 개인화된 커뮤니케이션, 문서 중심의 워크플로 |
| 📄 시각적 문서 디자인 📄 동적 데이터 통합 📄 다중 채널 출력 📄 Personalization |
| [대화형 통신 → 시작](/help/forms/interactive-communication/create-interactive-communication.md) |

## 🔗 데이터 및 통합 {#data-integration}

양식을 백엔드 시스템 및 데이터 소스에 연결하여 원활한 정보 흐름과 실시간 데이터 교환을 지원합니다.

### 양식 데이터 모델 {#form-data-model}

| **양식 데이터 모델** |
|---|
| 미리 채우기, 유효성 검사 및 제출 기능을 갖춘 여러 데이터 소스에 대한 통합 인터페이스입니다. 일관된 모델 이면의 추상적 통합 복잡성. |
| **기능:** 일관된 인터페이스 및 데이터 흐름 관리를 사용하여 양식을 여러 백엔드 시스템에 연결하는 통합 데이터 계층을 만듭니다. |
| **사용할 시기:** 여러 데이터 소스 통합, 복잡한 데이터 관계, 미리 채우기 요구 사항, 라이브 데이터에 대한 유효성 검사. |
| 🔄 다중 소스 통합 🔄 데이터 모델링 🔄 미리 채우기 🔄 유효성 검사 규칙 🔄 통합 인터페이스 |
| [양식 데이터 모델 →](/help/forms/create-form-data-models.md) |

### RESTful 커넥터 {#restful-connectors}

| **RESTful 커넥터** |
|---|
| RESTful API를 통해 웹에 액세스할 수 있는 서비스와 직접 통합됩니다. 사용자 지정 API 및 웹 서비스에 연결합니다. |
| **기능:** 웹 서비스에 대한 실시간 연결을 위해 제출 동작 또는 데이터 통합을 통해 양식에서 직접 API 호출을 사용할 수 있습니다. |
| **사용 시기:** 사용자 지정 API 통합, 웹 서비스 연결, 실시간 데이터 교환, 서드파티 서비스 통합. |
| 🌐 직접 API 호출 🌐 실시간 연결 🌐 유연한 통합 🌐 사용자 지정 서비스 지원 |
| [REST 끝점 구성 →](/help/forms/configure-submit-action-restpoint.md) \| [데이터 통합 설정 →](/help/forms/data-integration.md) |

### Salesforce 커넥터 {#salesforce-connector}

| **Salesforce 커넥터** |
|---|
| 리드 관리, 고객 데이터 동기화 및 영업 프로세스 자동화를 위해 Salesforce CRM과 기본적으로 통합됩니다. |
| **기능:** 양식 데이터 동기화, 잠재 고객 생성 및 고객 레코드 관리와 함께 Salesforce용 사전 빌드된 커넥터입니다. |
| **사용 시기:** Salesforce CRM 통합, 리드 생성 양식, 고객 데이터 관리, 영업 프로세스 자동화. |
| 🏢 미리 빌드된 커넥터 🏢 리드 관리 🏢 데이터 동기화 🏢 판매 자동화 |
| [Salesforce 통합 → 구성](/help/forms/configure-salesforce.md) |

### Microsoft Dynamics 커넥터 {#dynamics-connector}

| **Microsoft Dynamics 커넥터** |
|---|
| 포괄적인 비즈니스 프로세스 지원을 통해 ERP 및 CRM 연결을 위한 Microsoft Dynamics과의 엔터프라이즈 통합 |
| **기능:** 고객 관리, 비즈니스 프로세스 통합 및 엔터프라이즈 데이터 흐름을 위해 양식을 Microsoft Dynamics에 연결합니다. |
| **사용 시기:** Microsoft Dynamics 통합, 엔터프라이즈 워크플로, 고객 관리, 비즈니스 프로세스 자동화 |
| 🏭 엔터프라이즈 연결 🏭 비즈니스 프로세스 통합 🏭 고객 관리 🏭 데이터 동기화 |
| [Dynamics 통합 →](/help/forms/configure-msdynamics.md) |

### SharePoint 커넥터 {#sharepoint-connector}

| **SharePoint 커넥터** |
|---|
| 파일 저장, 공동 작업 및 문서 워크플로 자동화를 위해 SharePoint과 문서 관리 통합 |
| **기능:** 자동화된 문서 관리 및 공동 작업 기능을 사용하여 양식 제출 및 생성된 문서를 SharePoint에 저장합니다. |
| **사용 시기:** 문서 관리, 팀 공동 작업, 파일 저장소, SharePoint 기반 워크플로 |
| 📁 문서 저장소 📁 Collaboration 기능 📁 자동화된 워크플로 📁 SharePoint 통합 |
| [SharePoint 통합 → 구성](/help/forms/connect-forms-to-sharepoint-document-library.md) |

## 프로세스 및 워크플로 {#process-workflow}

포괄적인 워크플로우 및 처리 기능을 통해 비즈니스 프로세스, 승인 및 문서 생성을 자동화합니다.

### AEM 워크플로 {#aem-workflows}

복잡한 양식 기반 워크플로우를 위한 다단계 승인, 작업 할당 및 프로세스 조정을 통한 비즈니스 프로세스 자동화

**기능:** 승인 체인, 작업 라우팅 및 양식 제출을 위한 프로세스 모니터링을 사용하여 자동화된 비즈니스 프로세스를 만듭니다.

**사용 시기:** 승인 프로세스, 비즈니스 자동화, 작업 관리, 복잡한 워크플로, 프로세스 오케스트레이션.

**주요 기능:** 프로세스 자동화, 승인 체인, 작업 라우팅, 프로세스 모니터링, 비즈니스 규칙

[AEM 워크플로 시작 →](/help/forms/aem-forms-workflow.md)

### Adobe Sign 통합 {#adobe-sign}

법적 구속력이 있는 디지털 서명을 사용하는 전자 서명 워크플로우는 원활한 서명 프로세스를 위해 양식 경험에 직접 통합됩니다.

**기능:** 법적 구속력이 있는 전자 서명 기능과 자동 서명 워크플로를 사용하여 양식 내에서 디지털 서명을 사용하도록 설정합니다.

**사용 시기:** 계약 서명, 법률 문서, 승인 워크플로, 준수 요구 사항, 서명 자동화.

**주요 기능:** 법적 전자 서명, 서명 워크플로, 규정 준수 지원, 자동화된 프로세스

[Adobe Sign → 구성](/help/forms/working-with-adobe-sign.md)

### 제출 액션 {#submit-actions}

이메일, 데이터베이스 저장소, 워크플로우 트리거 및 사용자 정의 처리 등 여러 처리 옵션을 사용하여 양식 제출을 처리합니다.

**기능:** 사용자가 양식을 제출할 때 발생하는 작업(데이터를 이메일, 데이터베이스, 워크플로우 또는 외부 시스템으로 라우팅)을 정의합니다.

**사용할 시기:** 양식 제출 처리, 데이터 라우팅, 알림 시스템, 통합 트리거.

**주요 기능:** 여러 전송 옵션, 데이터 라우팅, 알림 시스템, 통합 트리거.

[제출 액션 구성 →](/help/forms/configure-submit-actions-core-components.md)

### 통신 API {#communication-apis}

대용량 문서 처리 및 자동화를 위한 RESTful API를 통한 프로그래밍 방식 문서 생성, 조작 및 보안.

**기능:** PDF 생성, 문서 어셈블리 및 일괄 처리를 위한 API를 사용하여 프로그래밍 방식으로 문서를 생성하고, 조작하고, 보호합니다.

**사용할 시기:** 문서 자동화, 대량 처리, 프로그래밍 방식 생성, 문서 어셈블리, 일괄 처리 작업.

**주요 기능:** 문서 생성, 일괄 처리, 프로그래밍 방식 제어, 문서 보안, API 자동화.

[통신 API → 시작](/help/forms/aem-forms-cloud-service-communications-introduction.md)

## 분석 및 최적화 {#analytics-optimization}

포괄적인 분석 및 테스트 기능을 사용하여 양식 성능을 모니터링하고, 사용자 행동을 이해하고, 전환율을 최적화합니다.

### Adobe Analytics 통합 {#adobe-analytics}

데이터 기반 최적화를 위한 완료율, 중단 패턴 및 사용자 동작에 대한 자세한 분석을 통해 성능 추적을 구성합니다.

**수행할 작업:** 포괄적인 보고를 통해 양식 상호 작용, 완료율, 필드 수준 분석 및 사용자 동작 패턴을 추적합니다.

**사용 시기:** 성능 모니터링, 전환 최적화, 사용자 동작 분석, 데이터 기반 개선 사항.

**주요 기능:** 성능 추적, 사용자 동작 분석, 전환 지표, 세부 보고.

[Analytics 통합 → 구성](/help/forms/integrate-aem-forms-with-adobe-analytics.md)

### 트랜잭션 보고서 {#transaction-reports}

배포 전반에 걸친 API 호출, 문서 생성 및 청구 가능 트랜잭션에 대한 세부 보고서를 통한 사용량 모니터링 및 청구 투명성.

**수행 방법:** 자세한 사용량 보고 및 비용 추적을 통해 API 사용, 문서 생성 볼륨 및 청구 가능한 트랜잭션을 모니터링합니다.

**사용 시기:** 사용량 모니터링, 비용 추적, 용량 계획, 규정 준수 보고, 리소스 최적화

**주요 기능:** 사용량 추적, 비용 모니터링, 용량 계획, 규정 준수 보고

[트랜잭션 보고서 보기 →](/help/forms/transaction-reports-billable-apis.md)

### A/B 테스팅 통합 {#ab-testing}

전환 개선을 위한 통계 분석으로 다양한 레이아웃, 필드 배열 및 사용자 흐름을 테스트하여 양식을 최적화합니다.

**수행 방법:** 다양한 양식 변형을 테스트하여 다양한 사용자 세그먼트와 사용 사례에 가장 효과적인 접근 방식을 식별하십시오.

**사용할 시기:** 변환 최적화, 사용자 경험 테스트, 성능 개선, 데이터 기반 디자인 결정

**주요 기능:** 양식 테스트, 통계 분석, 전환 최적화, 성능 비교.

[양식 최적화 설정에 대해 →](/help/forms/view-understand-aem-forms-analytics-reports.md)

## 관리 및 거버넌스 {#management-governance}

엔터프라이즈 규모의 양식 구축을 위한 중앙 집중식 양식 관리, 사용자 액세스 제어 및 거버넌스 기능

### Forms 포털 {#forms-portal}

통합 인터페이스에서 검색 기능, 양식 분류, 초안 관리 및 제출 추적을 제공하는 중앙 집중식 양식 저장소입니다.

**기능:** 사용자가 검색 및 범주화를 통해 초안을 검색, 액세스, 관리하고 제출을 추적할 수 있는 중앙 집중식 양식 저장소를 만듭니다.

**사용할 시기:** 양식 검색, 중앙 관리, 사용자 셀프서비스, 초안 관리, 제출 추적

**주요 기능:** 양식 검색, 검색 기능, 초안 관리, 제출 추적, 사용자 인터페이스.

[Forms 포털 구성 →](/help/forms/configure-forms-portal.md)

### 사용자 관리 {#user-management}

조직 전체에서 양식 작성, 편집, 게시 및 관리에 대한 세분화된 권한을 가진 역할 기반 액세스 제어.

**기능:** 세분화된 액세스 제어 및 보안을 통해 다양한 양식 관리 측면에 대한 사용자 역할 및 권한을 정의합니다.

**사용할 시기:** 액세스 제어, 보안 관리, 역할 정의, 권한 관리, 조직 거버넌스

**주요 기능:** 역할 기반 액세스, 권한 관리, 보안 제어, 조직 거버넌스

[사용자 관리 → 구성](/help/forms/forms-groups-privileges-tasks.md)

### 버전 제어 {#version-control}

버전 추적, 변경 내역, 롤백 기능, 규정 준수 및 거버넌스를 위한 감사 추적 등을 통해 수명주기 관리 구성

**수행할 작업:** 양식 버전을 추적하고 변경 기록을 유지 관리하며, 롤백을 활성화하고, 규정 준수 및 거버넌스 요구 사항에 대한 감사 추적을 제공합니다.

**사용 시기:** 변경 관리, 규정 준수 요구 사항, 감사 추적, 버전 추적, 거버넌스 프로세스

**주요 기능:** 버전 추적, 변경 내역, 롤백 기능, 감사 추적, 규정 준수 지원.

[버전 관리에 대해 →](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)

## 제품별 시작하기 {#getting-started}

즉각적인 요구 사항 및 기술 요구 사항을 기반으로 시작 지점을 선택합니다.

### 양식 작성 빠른 시작 {#form-creation-start}

**최신 프로젝트의 경우:** [핵심 구성 요소 Forms](/help/forms/creating-adaptive-form-core-components.md)(으)로 시작

**고성능:** [Edge Delivery Forms](/help/edge/docs/forms/overview.md)(으)로 시작

**기존 프로젝트:** [기초 구성 요소 Forms](/help/forms/creating-adaptive-form.md)(으)로 시작

**XFA 현대화의 경우:** [HTML5 Forms](/help/forms/introductionhtml5.md)(으)로 시작

**문서 통신의 경우:** [대화형 통신으로 시작](/help/forms/interactive-communication/create-interactive-communication.md)

### 데이터 통합 빠른 시작 {#integration-start}

**여러 데이터 원본의 경우:** [양식 데이터 모델](/help/forms/create-form-data-models.md)(으)로 시작

**Salesforce CRM용:** [Salesforce 커넥터](/help/forms/configure-salesforce.md)(으)로 시작

**Microsoft Dynamics의 경우:** [Dynamics 커넥터로 시작](/help/forms/configure-msdynamics.md)

**사용자 지정 API의 경우:** [RESTful 커넥터로 시작](/help/forms/configure-submit-action-restpoint.md)

**문서 저장소:** [SharePoint 커넥터](/help/forms/connect-forms-to-sharepoint-document-library.md)(으)로 시작

### 프로세스 자동화 빠른 시작 {#workflow-start}

**승인 프로세스:** [AEM 워크플로](/help/forms/aem-forms-workflow.md)(으)로 시작

**전자 서명의 경우:** [Adobe Sign 통합](/help/forms/working-with-adobe-sign.md)

**제출 처리용:** [제출 액션](/help/forms/configure-submit-actions-core-components.md)(으)로 시작

**문서 생성의 경우:** [통신 API](/help/forms/aem-forms-cloud-service-communications-introduction.md)(으)로 시작

### Analytics 빠른 시작 {#analytics-start}

**성능 추적:** [Adobe Analytics 통합](/help/forms/integrate-aem-forms-with-adobe-analytics.md)(으)로 시작

**사용 모니터링의 경우:** [트랜잭션 보고서](/help/forms/transaction-reports-billable-apis.md)(으)로 시작

**최적화 인사이트의 경우:** [Analytics 보고서](/help/forms/view-understand-aem-forms-analytics-reports.md)(으)로 시작

### 관리 빠른 시작 {#management-start}

**양식 검색:** [Forms 포털](/help/forms/configure-forms-portal.md)(으)로 시작

**액세스 제어의 경우:** [사용자 관리](/help/forms/forms-groups-privileges-tasks.md)(으)로 시작

**변경 내용 추적:** [버전 제어로 시작](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)

## 아키텍처 및 배포 {#architecture}

포괄적인 구현 지침의 경우:

- 확장 가능한 배포를 위한 **[아키텍처 패턴 검토](/help/forms/aem-forms-cloud-service-architecture.md)**
- 팀 공동 작업을 위한 **[개발 환경 설정](/help/forms/setup-local-development-environment.md)**
- 기존 시스템의 **[마이그레이션 전략 계획](/help/forms/migrate-to-forms-as-a-cloud-service.md)**

## 지원 및 리소스 {#support}

- **도움말 센터** - 구현 및 문제 해결에 대한 지원 받기
- **커뮤니티 포럼** - 다른 AEM Forms 사용자 및 전문가와 연결
- **전문 서비스** - 기업 배포를 위한 Adobe 컨설팅
- **교육 및 인증** - AEM Forms 기능에 대한 전문 지식 개발

*강력한 양식 환경을 만드는 데 필요한 구성 요소를 선택하십시오. 각 제품은 독립적으로 작동하거나 다른 제품과 결합하여 비즈니스 요구 사항에 맞는 포괄적인 솔루션을 만듭니다.*
