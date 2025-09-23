---
title: AEM Forms as a Cloud Service 소개
description: 적응형 양식 만들기, 워크플로우 자동화 및 디지털 문서 관리를 위한 AEM Forms 기능을 살펴보십시오. 양식 중심의 비즈니스 프로세스를 위한 완벽한 플랫폼
landing-page-description: 적응형 양식 만들기, 문서 처리 및 비즈니스 워크플로 자동화를 위해 AEM Forms as a Cloud Service을 사용하는 방법을 이해할 수 있습니다.
keywords: AEM Forms, 적응형 양식, 양식 빌더, 디지털 양식, 워크플로우 자동화, 문서 서비스, 양식 데이터 모델
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
index: false
source-git-commit: 51d9fed937ea5f12544ed476974d2812843fb457
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---


# AEM Forms as a Cloud Service 소개 {#introduction}



Adobe Experience Manager Forms as a Cloud Service은 디지털 양식 환경을 생성, 관리 및 최적화할 수 있는 포괄적인 플랫폼을 제공합니다. 조직에서는 AEM Forms을 사용하여 종이 문서 기반 프로세스를 디지털화하고, 반응형 웹 양식을 만들고, 문서 워크플로를 자동화하고, 규모에 맞게 개인화된 커뮤니케이션을 제공합니다.

이 플랫폼은 양식 작성 기능과 강력한 백엔드 서비스를 결합하므로 간단한 연락처 양식부터 복잡한 다단계 비즈니스 애플리케이션에 이르기까지 모든 것을 빌드할 수 있습니다. 클라우드 기반 아키텍처를 사용하면 인프라를 관리하지 않고도 자동 업데이트, 탄력적인 확장, 엔터프라이즈급 보안을 구현할 수 있습니다.

이 안내서에서는 초기 설계부터 지속적인 최적화에 이르기까지 전체 양식 라이프사이클에 대해 구성된 핵심 기능을 소개합니다.

## AEM Forms의 새로운 기능 {#whats-new}

**최신 릴리스 특징:**

- **날짜 및 시간 입력 구성 요소** - 정확한 날짜 및 시간 선택을 위한 달력 및 시계 인터페이스를 통한 사용자 입력 개선
- **파일 업로드 보안 향상** - 지원되지 않는 파일 형식을 방지하기 위한 자동 유효성 검사 및 콘텐츠 형식 검사
- **향상된 오류 처리** - 사용자 지정 제출 작업에 대한 특정 오류 코드로 디버깅 개선
- **기록 향상 문서** - 더 깨끗한 문서 생성을 위해 숨겨진 필드를 제외하는 옵션

**시험판 기능:**

- **AFP 형식 지원** - 통신 API를 통한 엔터프라이즈급 인쇄 기능
- **규칙 편집기 개선 사항** - 최신 JavaScript 지원, 동적 변수 및 컨텍스트 인식 패널 규칙
- **향상된 유효성 검사 메서드** - 패널, 필드 및 양식 수준 유효성 검사와 향상된 유연성

[전체 릴리스 정보 보기 →](/help/release-notes/release-notes-cloud/release-notes-current.md#forms)

## 조기 액세스 프로그램 {#early-access}

최첨단 AEM Forms 혁신이 일반적으로 제공되기 전에 독점적으로 액세스할 수 있습니다.

**현재 조기 액세스 기능:**

- **AEM Forms AI Assistant** - 자동화된 양식 생성, 패널 생성 및 최적화 권장 사항을 위한 생성 AI
- **스크리블 서명 구성 요소** - 마우스, 스타일러스 또는 터치스크린을 사용하여 양식 내에서 직접 서명 캡처
- **직접 API 통합** - 양식 데이터 모델을 설정하지 않고도 규칙 편집기의 API에 연결
- **Forms 최적화** - AI 기반 성능 분석 및 전환율 개선 제안

**프로그램에 참여:**
혁신적인 기술에 먼저 액세스하고 AEM Forms의 미래를 형성하는 데 도움을 받으십시오.

[액세스 요청 →](mailto:aem-forms-ea@adobe.com) | [자세히 →](/help/forms/early-access-ea-features.md)


## 핵심 기능 {#core-capabilities}

AEM Forms은 초기 생성에서 지속적인 최적화에 이르기까지 전체 디지털 양식 여정을 지원합니다. 각 단계는 이전 단계를 기반으로 하며 양식 기반 비즈니스 프로세스를 위한 포괄적인 플랫폼을 만듭니다.

**AEM Forms 워크플로 여정:**

    →을 만들고 → 게시 → 캡처 → 프로세스→ 만들고 → 추적 → 보관 →을 통합합니다
    ↓        ↓        ↓         ↓         ↓         ↓          ↓       ↓        ↓
    디자인   리뷰   배포   수집   핸들   연결   저장소 모니터링   최적화
    ↑                                                                              ↓
    ←←←←←←←←←←←←←←← 지속적인 개선 루프 ←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←

### 만들기: 양식 디자인 및 개발 {#create}

다양한 요구 사항 및 기술 요구 사항에 맞게 조정된 여러 작성 접근 방식을 사용하여 적응형 양식을 작성하십시오.

**Visual Form Builder**
[핵심 구성 요소](/help/forms/creating-adaptive-form-core-components.md), [기초 구성 요소](/help/forms/creating-adaptive-form.md) 또는 [Edge Delivery Services](/help/edge/docs/forms/overview.md)을(를) 사용하여 드래그 앤 드롭 인터페이스를 통해 응답형 양식을 디자인할 수 있습니다. 시각적 편집기는 장치 및 보조 기술 간에 작동하는 깔끔한 의미 체계 마크업을 유지하면서 즉각적인 피드백을 제공합니다.

**문서 기반 작성**
[Edge Delivery Services](/help/edge/docs/forms/overview.md)을 통해 Microsoft Excel과 같은 익숙한 도구를 사용하여 양식을 만듭니다. 이 접근 방식을 통해 콘텐츠 작성자는 기술적 전문 지식 없이도 고성능 양식을 구축할 수 있을 뿐만 아니라 Google Lighthouse의 탁월한 점수를 달성할 수 있습니다.

**템플릿 및 테마**
구조 및 초기 콘텐츠를 정의하는 미리 작성된 [템플릿](/help/forms/template-editor-core-components.md)을(를) 사용하여 양식 만들기를 가속화하십시오. 여러 양식의 시각적 스타일을 제어하는 [테마](/help/forms/using-themes-in-core-components.md)를 사용하여 일관된 브랜딩을 적용하여 디자인 일관성을 보장하고 개발 시간을 단축합니다.

**데이터 통합**
디자인 단계에서 양식을 백엔드 시스템에 연결합니다. [양식 데이터 모델](/help/forms/create-form-data-models.md)은(는) 여러 데이터 원본에 대한 통합 인터페이스를 제공하여 [미리 채우기](/help/forms/prepopulate-adaptive-form-fields.md), [유효성 검사 규칙](/help/forms/rule-editor-core-components.md)을(를) 가능하게 하고 양식과 비즈니스 시스템 간의 원활한 데이터 흐름을 가능하게 합니다.

**유효성 검사 및 조건부 논리**
[조건부 논리](/help/forms/rule-editor-core-components.md), 점진적 공개 및 적응형 유효성 검사를 구현하여 복잡한 프로세스를 통해 사용자를 안내합니다. [기능 저장 및 다시 시작](/help/forms/save-core-component-based-form-as-draft.md)을 통해 사용자는 여러 세션에서 양식을 작성할 수 있습니다.

**HTML5 Forms**
모바일 장치 및 레거시 브라우저에 대해 XFA 기반 양식을 [HTML5 양식](/help/forms/introductionhtml5.md)(으)로 렌더링합니다. HTML5 Forms은 원래 XDP 템플릿에서 양식 논리 및 유효성 검사를 유지하면서 플러그인 없이 기본 모바일 경험을 제공합니다.

**대화형 통신**
시각적 편집기를 사용하여 명세서, 청구서 및 공지 등의 문서 중심 통신을 만들 수 있습니다. [대화형 통신](/help/forms/introduction-to-interactive-communication.md) 정적 콘텐츠와 동적 데이터를 결합하여 인쇄 및 디지털 채널 전체에 개인화된 통신을 생성합니다.

### 관리: 검토 및 규정 준수 {#govern}

양식이 조직 표준 및 규정 요구 사항을 충족하도록 감독 및 승인 프로세스를 수립합니다.

**워크플로 기반 승인**
역할 기반 할당이 있는 여러 단계 검토 프로세스를 통해 양식 디자인을 라우팅합니다. 이해 당사자는 게시 전에 [검토](/help/forms/create-reviews-forms.md), [댓글](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)을 수행하고 양식을 승인할 수 있으며, [AEM 워크플로](/help/forms/aem-forms-workflow.md)를 사용하여 품질 관리와 준수 감독을 유지합니다.

**버전 관리**
규정 준수를 위해 양식 버전을 추적하고 감사 추적을 유지 관리합니다. 기본 제공 [버전 관리](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)를 통해 변경 내용을 롤백하고, 반복을 비교하고, 준수 감사를 위해 기록 레코드를 유지 관리할 수 있습니다.

**액세스 제어 및 권한**
양식 작성, 편집 및 게시에 대한 세분화된 권한을 정의합니다. [역할 기반 액세스](/help/forms/forms-groups-privileges-tasks.md)를 통해 권한이 있는 사용자만 양식을 수정할 수 있으며 중요한 비즈니스 프로세스에 대한 업무 분리는 유지됩니다.

### 게시: 다중 채널 배포 {#publish}

여러 채널 및 터치포인트에 양식을 배포하여 어디에서나 사용자에게 연락할 수 있습니다.

**옴니채널 게시**
[AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md), 독립 실행형 웹 페이지, 모바일 응용 프로그램 또는 [서드파티 시스템에 임베드](/help/forms/embed-adaptive-form-core-components-external-web-page.md)에 양식을 게시합니다. 단일 소스 게시는 서로 다른 채널 요구 사항에 맞게 조정하면서 일관성을 보장합니다.

**로컬라이제이션 및 Personalization**
[왼쪽에서 오른쪽 및 오른쪽에서 왼쪽 언어](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md)를 모두 지원하고 [AEM의 번역 워크플로](/help/forms/right-left-languages.md)를 사용하여 여러 언어로 양식을 전달합니다. Adobe Target과 통합하여 사용자 세그먼트, 동작 또는 컨텍스트 데이터를 기반으로 양식 경험을 개인화할 수 있습니다.

**성능 최적화**
번개처럼 빠른 양식 로드와 최적의 SEO 성능을 위해 Edge Delivery Services을 활용하십시오. 컨텐츠 전달 네트워크는 지연 시간을 최소화하면서 글로벌 접근성을 보장합니다.

**Forms 포털**
사용자가 양식을 검색, 액세스 및 관리할 수 있는 중앙 집중식 양식 저장소를 만듭니다. [Forms 포털](/help/forms/configure-forms-portal.md)은(는) 향상된 사용자 경험을 위해 통합 인터페이스에서 검색 기능, 양식 분류, 초안 관리 및 제출 추적을 제공합니다.

### 캡처: 사용자 경험 및 데이터 수집 {#capture}

양식 채우기 환경을 최적화하여 완료율 및 데이터 품질을 극대화하십시오.

**응답형 디자인**
Forms은 자동으로 다양한 화면 크기와 입력 방식에 맞게 조정됩니다. 터치에 적합한 컨트롤, 키보드 탐색 및 화면 판독기 호환성으로 모든 사용자 유형에서 [접근성](/help/forms/creating-accessible-adaptive-forms.md)을 보장합니다.

**디지털 서명**
양식 환경에서 전자 서명을 법적으로 구속하려면 [Adobe Sign](/help/forms/working-with-adobe-sign.md)을(를) 통합하십시오. 사용자는 양식을 종료하지 않고 문서에 서명할 수 있으므로 승인 프로세스를 간소화하고 포기를 줄일 수 있습니다.

**작업 제출**
[제출 액션](/help/forms/configure-submit-actions-core-components.md)을 구성하여 사용자가 양식을 작성 및 제출할 때 발생할 작업을 정의합니다. 사용자에게 즉각적인 피드백과 확인을 제공하면서 데이터를 이메일, 데이터베이스, 워크플로우 또는 외부 시스템으로 라우팅합니다.

### 프로세스: 실행 처리 및 공정순서 {#process}

강력한 처리, 유효성 검사 및 라우팅 기능을 사용하여 양식 제출을 처리합니다.

**데이터 유효성 검사 및 처리**
서버 측 유효성 검사 및 자동화된 처리 규칙을 통해 데이터 무결성을 보장합니다. 제출된 데이터를 변환, 검증 및 라우팅하는 동시에 사용자를 위한 영수증, 확인 또는 후속 자료를 생성할 수 있습니다.

**통신 API**
[RESTful API](/help/forms/aem-forms-cloud-service-communications-introduction.md)를 통해 프로그래밍 방식으로 문서를 생성, 조작 및 보호합니다. PDF 만들기, 인쇄 준비 형식, 문서를 조합하고, 디지털 서명을 적용하고, 엔터프라이즈급 문서 워크플로를 위한 대용량 [일괄 처리 작업](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)을(를) 처리합니다.

**기록 문서**
준수 및 사용자 확인을 위해 양식 제출에 대한 PDF 레코드를 자동으로 생성합니다. [기록 문서](/help/forms/generate-document-of-record-core-components.md)는 제출된 데이터가 있는 완성된 양식의 서식 있는 인쇄 가능한 버전을 만들어 거래 및 규정 요구 사항에 대한 공식 문서를 제공합니다.

**워크플로 오케스트레이션**
양식 제출을 기반으로 복잡한 비즈니스 프로세스를 트리거합니다. 승인 체인을 통해 데이터를 라우팅하고, 특정 사용자에게 작업을 할당하고, 감사 추적을 유지하면서 일상적인 작업을 자동화할 수 있습니다.

**오류 처리 및 복구**
내장된 재시도 메커니즘 및 폴백 처리를 통해 제출 내용이 손실되지 않습니다. 포괄적인 로깅을 통해 문제를 해결하고 SLA( 서비스 수준 계약 ) 를 유지할 수 있습니다.

### 통합: 백엔드 연결 {#integrate}

양식을 기존 비즈니스 시스템 및 데이터 소스에 연결하여 원활한 정보 흐름을 제공합니다.

**미리 빌드된 커넥터**
[Salesforce](/help/forms/configure-salesforce.md), [Microsoft Dynamics](/help/forms/configure-msdynamics.md), [SharePoint](/help/forms/connect-forms-to-sharepoint-document-library.md) 및 Adobe Experience Cloud 솔루션과 네이티브 통합. 사전 설치된 커넥터는 안정적인 데이터 동기화를 보장하면서 개발 시간을 줄입니다.

**RESTful API 통합**
[제출 액션](/help/forms/configure-submit-action-restpoint.md) 또는 [데이터 통합](/help/forms/data-integration.md)을 통해 RESTful API를 통해 웹에 액세스할 수 있는 서비스에 연결합니다. 양식 데이터 모델은 통합 복잡성을 추상화하여 기본 시스템 아키텍처에 관계없이 일관된 인터페이스를 제공합니다.

**실시간 데이터 교환**
양식과 비즈니스 시스템 간의 양방향 데이터 흐름을 가능하게 합니다. 포괄적인 [데이터 통합](/help/forms/data-integration.md)을 통해 제출 시 기존 레코드에서 양식을 미리 채우고, 라이브 데이터에 대해 검증하고, 여러 시스템을 동시에 업데이트합니다.

### 추적: 분석 및 성능 모니터링 {#track}

포괄적인 분석 및 모니터링을 통해 양식 성능 및 사용자 행동을 이해합니다.

**양식 분석**
[Adobe Analytics 통합](/help/forms/integrate-aem-forms-with-adobe-analytics.md)을 통해 완료율, 포기 패턴 및 필드 수준 상호 작용을 추적합니다. 마찰점을 식별하고, 전환 단계를 측정하고, 다양한 세그먼트 간의 사용자 행동을 이해합니다.

**성능 모니터링**
양식 로드 시간, 제출 성공률 및 시스템 성능 모니터링 실시간 대시보드는 기술 상태 및 사용자 경험 지표에 대한 통찰력을 제공합니다.

**Business Intelligence**
양식 사용, 제출 볼륨 및 프로세스 효율성에 대한 보고서를 생성합니다. Analytics는 용량 계획, 사용자 환경 최적화 및 비즈니스 프로세스 개선 사항을 알려줍니다.

**거래 보고서**
AEM Forms 배포에서 API 사용, 문서 생성 볼륨 및 [청구 가능한 트랜잭션](/help/forms/transaction-reports-billable-apis.md)을 모니터링합니다. 소비 패턴을 추적하고 리소스 할당을 최적화하고 사용 기반 라이선스 요구 사항을 준수합니다.

### 아카이브: 문서 관리 및 규정 준수 {#archive}

양식 제출 및 생성된 문서를 안전하게 저장 및 관리하여 장기간 보존 및 규정 준수

**문서 저장소**
생성된 문서 및 양식 제출을 AEM의 Digital Asset Management 시스템에 저장하거나 [SharePoint](/help/forms/configure-submit-action-sharepoint.md), [OneDrive](/help/forms/configure-submit-action-onedrive.md) 또는 [Azure Blob 저장소](/help/forms/configure-submit-action-azure-blob-storage.md)와 같은 외부 문서 리포지토리와 통합합니다.

**규정 준수 및 유지**
GDPR, CCPA 및 HIPAA를 비롯한 규정 요구 사항을 준수하는 데이터 보존 정책을 구현합니다. [자동화된 보관 프로세스](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) 문서를 필요한 기간 동안 보관하고 필요할 때 안전하게 폐기하도록 합니다.

**보안 및 액세스 제어**
보관된 문서에 암호화, 디지털 서명 및 [역할 기반 액세스 제어](/help/forms/forms-groups-privileges-tasks.md)를 적용합니다. 감사 추적은 규정 준수 보고 및 보안 감독을 위해 문서 액세스 및 수정 사항을 추적합니다.

### 개선 사항: 최적화 및 개선 사항 {#improve}

데이터 기반 인사이트 및 테스트를 통해 양식 성능 및 사용자 경험을 지속적으로 최적화합니다.

**A/B 테스트 통합**
Adobe Target을 사용하여 다양한 양식 레이아웃, 필드 배열 및 사용자 흐름을 테스트합니다. 통계 분석은 다양한 사용자 세그먼트 및 사용 사례에 대한 가장 효과적인 접근 방식을 식별하는 데 도움이 됩니다.

**Analytics 기반 최적화**
사용자 행동 데이터를 분석하여 개선 기회를 파악합니다. 반복 설계 개선 사항을 알리기 위한 열 매핑, 필드 상호 작용 분석 및 포기 패턴 인식에 대한 [분석 보고서 보기 및 이해](/help/forms/view-understand-aem-forms-analytics-reports.md).

**반복적 개선**
사용자 피드백, 성능 지표 및 비즈니스 요구 사항을 기반으로 지속적인 개선 프로세스를 구현합니다. [버전 제어](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) 및 롤백 기능을 통해 안전한 실험과 빠른 반복이 가능합니다.

## 시작하기 {#getting-started}

접근 방식은 사용자의 즉각적인 요구 사항과 장기적인 목표에 따라 다릅니다.

### 빠른 시작: 간단한 Forms {#quick-start}

기술 배경 및 성능 요구 사항에 따라 선호하는 작성 접근 방식을 선택합니다.

**시각적 양식 작성:**

1. 최신 반응형 양식을 위한 **[핵심 구성 요소를 사용하여 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)**
2. 양식 데이터를 처리할 수 있도록 **[전송 작업 구성](/help/forms/configure-submit-actions-core-components.md)**
3. **[AEM Sites에 양식 포함](/help/forms/embed-adaptive-form-aem-sites.md)** 또는 직접 링크를 통해 공유

**문서 기반 작성:**

1. 고성능 양식용 Edge Delivery Services을 사용하여 **[Excel을 사용하여 양식 작성](/help/edge/docs/forms/create-forms.md)**
2. 최적의 로드 속도 및 SEO를 위해 **[Edge Delivery에 게시](/help/edge/docs/forms/publish-forms.md)**

**레거시 양식 지원:**

- 모바일에 최적화된 XFA 양식 렌더링용 **[HTML5 Forms](/help/forms/introductionhtml5.md)**

### 고급 구현: 비즈니스 프로세스 {#advanced-implementation}

여러 시스템, 문서 생성 및 승인 워크플로와 관련된 복잡한 요구 사항의 경우:

**데이터 통합 및 워크플로:**

1. 백 엔드 시스템에 연결하려면 **[양식 데이터 모델을 설정](/help/forms/create-form-data-models.md)**
2. 승인 및 라우팅에 대한 **[워크플로 프로세스 디자인](/help/forms/aem-forms-workflow.md)**
3. 성능을 측정하도록 **[분석을 구성](/help/forms/integrate-aem-forms-with-adobe-analytics.md)**

**문서 서비스 및 통신:**

1. 자동화된 문서 생성을 위해 **[통신 API 구현](/help/forms/aem-forms-cloud-service-communications-introduction.md)**
2. 개인 맞춤화된 문 및 알림을 위한 **[대화형 통신 만들기](/help/forms/introduction-to-interactive-communication.md)**
3. 중앙 집중식 양식 관리를 위해 **[Forms 포털 설정](/help/forms/configure-forms-portal.md)**

### 엔터프라이즈 배포: 확장 및 거버넌스 {#enterprise-deployment}

거버넌스, 규정 준수 및 모니터링이 필요한 조직 전체의 구축 환경:

**아키텍처 및 거버넌스:**

1. 확장 가능한 배포를 위한 **[아키텍처 패턴 검토](/help/forms/aem-forms-cloud-service-architecture.md)**
2. **[사용자 관리 구성](/help/forms/forms-groups-privileges-tasks.md)** 및 액세스 제어
3. 팀 공동 작업을 위한 **[개발 워크플로 설정](/help/forms/setup-local-development-environment.md)**

**마이그레이션 및 모니터링:**

1. 기존 시스템의 **[마이그레이션 전략 계획](/help/forms/migrate-to-forms-as-a-cloud-service.md)**
2. 사용 추적 및 규정 준수를 위해 **[트랜잭션 모니터링 구현](/help/forms/transaction-reports-billable-apis.md)**

<details>
<summary><strong>❓ 자주 묻는 질문</strong></summary>

**양식 빌더란 무엇입니까?**
양식 빌더는 코딩하지 않고 디지털 양식을 만들 수 있는 도구입니다. 드래그 앤 드롭 인터페이스를 사용하여 양식을 디자인하고, 텍스트 상자 및 드롭다운과 같은 필드를 추가하고, 온라인으로 게시하여 사용자로부터 데이터를 수집할 수 있습니다.

**온라인 양식을 만드는 방법**
AEM Forms을 사용하면 시각적 드래그 앤 드롭 편집기를 통해 핵심 구성 요소를 사용하여 적응형 양식을 만들거나 Edge Delivery Services으로 고성능 양식을 작성하거나 기존 워크플로우에 Foundation 구성 요소를 사용할 수 있습니다. 먼저 템플릿을 선택하고, 양식 필드를 추가하고, 데이터 연결을 구성하고, 여러 채널에 게시합니다.

**온라인 양식이 좋은 이유는 무엇입니까?**
좋은 온라인 양식은 모바일에 응답하고, 빠르게 로드하고, 명확한 레이블을 가지고, 논리적 필드 순서를 사용하고, 오류를 방지하기 위한 유효성 검사를 포함하고, 제출 시 사용자에게 즉시 피드백을 제공합니다.

**양식을 다른 비즈니스 시스템과 통합할 수 있습니까?**
예. 최신 양식 빌더는 광범위한 통합 기능을 제공합니다. 양식을 CRM 시스템, 이메일 마케팅 플랫폼, 데이터베이스, 클라우드 스토리지 및 워크플로우 자동화 도구에 연결하여 비즈니스 프로세스를 간소화할 수 있습니다.

**온라인 양식은 안전합니까?**
전문적인 양식 빌더에는 데이터 암호화, 안전한 데이터 전송, 액세스 제어, GDPR, HIPAA, CCPA와 같은 규정 준수와 같은 엔터프라이즈급 보안 기능이 포함되어 중요한 정보를 보호합니다.

**양식에 전자 서명을 추가하는 방법**
디지털 서명은 Adobe Sign 또는 기타 전자 서명 공급자를 사용하여 양식에 직접 통합할 수 있습니다. 이렇게 하면 사용자가 양식 경험 내에서 문서에 서명할 수 있으므로 별도의 서명 워크플로가 필요하지 않고 양식 유기를 줄일 수 있습니다.

**양식에서 PDF 문서를 자동으로 생성할 수 있습니까?**
예. 최신 양식 플랫폼은 양식 제출 시 PDF 영수증, 확인 또는 기록 문서를 자동으로 생성할 수 있습니다. 이는 규정 준수, 기록 보관 및 사용자에게 즉각적인 확인을 제공하는 데 필수적입니다.

**양식 성능 및 분석을 추적하는 방법**
양식 분석을 통해 완료율, 중단 패턴 및 사용자 행동을 이해할 수 있습니다. Adobe Analytics과 같은 분석 플랫폼과의 통합은 마찰을 일으키는 필드와 전환율을 최적화하는 방법에 대한 통찰력을 제공합니다.

**양식 워크플로우 자동화란 무엇입니까?**
양식 워크플로우 자동화는 승인 프로세스를 통해 제출을 라우팅하고, 팀 구성원에게 작업을 할당하고, 다른 비즈니스 시스템에서 작업을 트리거합니다. 따라서 수작업 없이 간편하게 처리할 수 있으며 양식 데이터를 일관되게 처리할 수 있습니다.

**장애가 있는 사용자가 양식에 액세스할 수 있도록 하려면 어떻게 해야 합니까?**
[액세스 가능한 양식](/help/forms/creating-accessible-adaptive-forms.md)에는 적절한 레이블 지정, 키보드 탐색, 화면 판독기 호환성 및 WCAG 지침 준수가 포함됩니다. 이렇게 하면 모든 사용자가 자신의 능력이나 보조 기술에 관계없이 양식을 작성할 수 있습니다.

**양식 빌더 비용은 얼마입니까?**
AEM Forms as a Cloud Service 요금은 특정 요구 사항, 사용량 및 기능 요구 사항에 따라 다릅니다. 자세한 가격 정보를 확인하고 조직에 맞는 솔루션에 대해 논의하려면 Adobe Sales 또는 Adobe 담당자에게 문의하십시오.

</details>

## 다음 단계 {#next-steps}

현재 우선 순위와 일치하는 기능을 살펴보십시오.

- 작성 환경을 경험하려면 **[첫 번째 양식을 작성](/help/forms/creating-adaptive-form-core-components.md)**&#x200B;하십시오.
- 배포 계획에 대한 **[아키텍처 옵션 검토](/help/forms/aem-forms-cloud-service-architecture.md)**
- 팀 공동 작업을 위해 **[개발 환경 설정](/help/forms/setup-local-development-environment.md)**
- 기존 시스템 연결을 위한 **[통합 옵션 살펴보기](/help/forms/data-integration.md)**

포괄적인 구현 지침의 경우 Adobe Professional Services을 사용하여 배포를 가속화하고 처음부터 모범 사례를 확인하십시오.
