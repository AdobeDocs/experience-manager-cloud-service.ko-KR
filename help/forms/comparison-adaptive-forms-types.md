---
title: 적응형 Forms 핵심 구성 요소와 Edge Delivery Services Forms 및 기초 구성 요소
description: AEM Forms 작성 접근 방식(핵심 구성 요소, Edge Delivery Services Forms 및 기초 구성 요소)의 기술 비교. 아키텍처, 렌더링, 기능 및 사용 사례.
keywords: 적응형 양식 비교, 핵심 구성 요소, 기초 구성 요소, edge delivery services 양식, AEM 양식 비교, 양식 빌더 비교
role: Architect, Developer, Admin
level: Intermediate
feature: Adaptive Forms, Core Components, Edge Delivery Services
exl-id: adaptive-forms-comparison
source-git-commit: 37799555babb15809409ec5cda8a1c46ceff24f2
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 8%

---


# 적응형 Forms: 핵심 구성 요소와 Edge Delivery Services Forms 대 기초 구성 요소

Adobe Experience Manager(AEM) Forms은 데이터 캡처 경험을 구축하기 위해 핵심 구성 요소를 기반으로 하는 적응형 Forms, Edge Delivery Services Forms 및 기초 구성 요소를 기반으로 하는 적응형 Forms의 세 가지 접근 방식을 제공합니다. 각 접근 방식에는 다른 아키텍처, 렌더링 모델 및 대상 사용 사례가 있습니다. 이 문서에서는 솔루션 설계자, 개발자 및 AEM 고객이 요구 사항에 적합한 접근 방식을 선택하는 데 도움이 되는 기술 비교를 제공합니다.

## 개요

세 가지 양식 유형 모두 사용자 데이터를 캡처하고 백엔드 시스템과 통합하는 역할을 합니다. 그러나 기본 아키텍처, 양식 렌더링 위치, 전달 방법 및 지원하는 기능은 다릅니다.

| 접근법 | 상태 | 기본 사용 사례 |
|----------|--------|------------------|
| **핵심 구성 요소** | 새 양식에 권장 | 유연한 게시 옵션을 통해 AEM 작성이 필요한 현대적이고 확장 가능한 양식 |
| **Edge Delivery Services Forms** | 성능이 중요한 사이트에 권장 | 신속한 배포로 엣지에서 제공되는 고성능 양식 |
| **기초 구성 요소** | 유지 관리 모드 | 기존 기능 지원이 필요한 기존 양식 |

## 핵심 구성 요소 기반 적응형 Forms

### 정의

적응형 Forms 코어 구성 요소는 Adobe Experience Manager WCM 코어 구성 요소 를 기반으로 구축된 30개의 오픈 소스 BEM 호환 구성 요소 세트입니다. 새로운 적응형 Forms을 제작하기 위해 Adobe이 권장하는 접근 방식을 나타내며 최신 아키텍처, 향상된 성능 및 자동 Headless 양식 생성을 제공합니다.

### 아키텍처

핵심 구성 요소는 표준화된 모듈식 구성 요소 아키텍처를 사용합니다.

- **구성 요소 기초**: AEM WCM 핵심 구성 요소를 기반으로 합니다.
- **스타일 방법론**: BEM(Block Element Modifier) CSS 규칙
- **콘텐츠 저장소**: 구조화된 콘텐츠 노드가 있는 JCR 저장소
- **렌더링**: 선택적 클라이언트측 Headless 렌더링으로 AEM의 서버측 렌더링
- **Source**: 오픈 소스([GitHub](https://github.com/adobe/aem-core-forms-components)에서 사용 가능)

### 렌더링 모델

코어 구성 요소는 여러 렌더링 모델을 지원합니다.

1. **SSR(서버측 렌더링)**: AEM 서버에서 Forms을 렌더링하고 브라우저에 전체 HTML을 전달합니다.
2. **헤드리스 렌더링**: Forms은 React, Angular 또는 기타 프레임워크의 클라이언트측 렌더링을 위해 API를 통해 JSON 표현을 노출합니다.
3. **하이브리드 렌더링**: 최적의 성능을 위한 서버 및 클라이언트 렌더링 조합

### 게시 옵션

- AEM 게시 인스턴스
- Edge Delivery Services (구성된 경우)
- 사용자 정의 프론트엔드 애플리케이션용 헤드리스 API

### 주요 기능

| 범주 | 기능 |
|----------|-------------|
| **구성 요소** | 텍스트 상자, 숫자 상자, 날짜 선택기, 드롭다운, 확인란 그룹, 라디오 버튼, 파일 첨부, 마법사, 아코디언, 가로/세로 탭을 포함한 30개의 표준화된 구성 요소 |
| **양식 모델** | JSON 스키마(v4 및 2020-12), 양식 데이터 모델(FDM), XDP/XFA 템플릿(제한적) |
| **규칙 엔진** | 조건부 논리, 유효성 검사, 서비스 호출 및 사용자 지정 함수가 있는 시각적 규칙 편집기 |
| **제출 액션** | REST 엔드포인트, 이메일, AEM 워크플로, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion, 양식 데이터 모델 |
| **미리 채우기** | 양식 데이터 모델 미리 채우기 서비스, 사용자 지정 미리 채우기 서비스 |
| **CAPTCHA** | reCAPTCHA, hCaptcha, Turnstile |
| **기록 문서** | 사용자 지정 또는 OOTB 템플릿을 사용한 PDF 생성 |
| **접근성** | WCAG 준수, ARIA 레이블, 키보드 탐색, 화면 판독기 지원 |
| **현지화** | AEM 번역 워크플로를 통한 다국어 지원 |
| **버전 관리** | AEM Sites에서 상속된 컨텐츠 버전 관리 |

### 사전 요구 사항

- **AEM Forms as a Cloud Service**: 기본적으로 핵심 구성 요소 사용
- **AEM 6.5 Forms**: AEM Archetype을 통해 활성화해야 함
- **사용자 권한**: 사용자는 `forms-users` 그룹에 있어야 합니다.
- **템플릿**: 적응형 양식(핵심 구성 요소) 템플릿 필요
- **테마**: 캔버스 테마(OOTB) 또는 사용자 지정 테마

### 제한 사항

- **JSON 스키마 제약 조건**: Null 형식, 유니온 형식(any), OneOf/AnyOf/AllOf/NOT 구문은 지원되지 않습니다.
- **구성 요소 간격**: Adobe Sign 블록, 스크리블 서명, 차트, 이미지 선택을 사용할 수 없음(Foundation 구성 요소에서 사용 가능)
- **사용자 지정 함수**: 생성기 함수, 비동기/대기, 클래스 메서드는 지원되지 않습니다.
- **디지털 서명**: Foundation 구성 요소와 달리 기본적으로 사용할 수 없습니다.

### 사용 시기

**추천 대상:**

- 새 양식 개발 프로젝트
- 유지 관리가 가능한 현대적 아키텍처를 필요로 하는 조직
- 유연한 게시가 필요한 프로젝트(AEM + Edge Delivery + Headless)
- Headless API를 통한 맞춤형 프론트엔드 애플리케이션(React, Angular)
- 성능 및 접근성 우선 순위 프로젝트
- 옴니채널 게재 요구 사항(웹, 모바일, 키오스크)

**권장되지 않음:**

- Adobe Sign 통합이 필요한 Forms(기초 구성 요소 사용)
- Edge Delivery Services 성능이 중요한 간단한 양식
- 기존 기초 구성 요소 기반 양식(마이그레이션하지 않는 한 Foundation에서 유지)

## Edge Delivery Services 양식

### 정의

EDS(Edge Delivery Services) Forms은 Adobe Experience Manager Edge Delivery Services을 통해 양식을 만들고 전달하기 위한 구성 가능한 서비스 세트입니다. 또한 Edge 기반 제공, 클라이언트측 렌더링 및 여러 작성 방법을 통해 탁월한 성능을 발휘하며 신속한 양식 개발을 수행할 수 있습니다.

### 아키텍처

EDS Forms은 분리된 에지 우선 아키텍처를 사용합니다.

- **콘텐츠 원본**: Microsoft SharePoint, Google 드라이브(문서 기반) 또는 유니버설 편집기(WYSIWYG)
- **코드 저장소**: GitHub
- **컨텐츠 전달**: Edge Delivery Services CDN
- **렌더링**: 바닐라 JavaScript을 사용하는 클라이언트측 렌더링
- **양식 블록**: 적응형 Forms 블록은 양식 정의를 처리하고 HTML을 생성합니다.

### 렌더링 모델

EDS Forms은 클라이언트측 렌더링만 사용합니다.

1. JSON으로 저장된 양식 정의(스프레드시트에서 변환되거나 범용 편집기에서 작성됨)
2. Edge에서 가져온 JSON: `https://<branch>--<repo>--<owner>.aem.live/<form>.json`
3. 적응형 Forms 블록 JavaScript 프로세스 JSON
4. 브라우저에서 동적으로 생성된 HTML 구조
5. 스타일링에 적용된 CSS

**HTML 구조 패턴:**

```html
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required="{Required}">
   <label for="{FieldId}" class="field-label">Label</label>
   <input type="{Type}" id="{FieldId}" name="{Name}">
   <div class="field-description" id="{FieldId}-description">Help text</div>
</div>
```

### 작성 방법

EDS Forms은 두 가지 작성 방법을 지원합니다.

#### Universal Editor (WYSIWYG)

- 시각적 드래그 앤 드롭 인터페이스
- 장치 시뮬레이션을 사용한 실시간 미리 보기
- 조건부 논리에 대한 고급 규칙 편집기
- 양식 데이터 모델(FDM) 통합
- AEM 워크플로우 통합
- 사용자 지정 구성 요소 지원
- 템플릿 기반 만들기

#### 문서 기반 작성

- Microsoft Excel 또는 Google Sheets 작성
- 스프레드시트 기반 양식 정의
- 즉시 게시(변경 사항은 즉시 반영됨)
- 간단하거나 중간 수준의 복잡성 양식에 적합

### 제출 옵션

**Forms 제출 서비스(FSS):**

- Google Sheets에 제출
- Microsoft Excel(OneDrive/SharePoint)에 제출
- 이메일 알림

**AEM 게시 제출 동작:**

- REST 엔드포인트
- AEM 메일 서비스
- 양식 데이터 모델
- AEM 워크플로우
- SharePoint/OneDrive
- Azure Blob 저장소
- Microsoft 전원 자동화
- Adobe Workfront Fusion
- Adobe Marketo Engage

### 주요 기능

| 범주 | 기능 |
|----------|-------------|
| **구성 요소** | 모든 HTML5 입력 유형, 확인란 그룹, 라디오 그룹, 드롭다운, 패널, 반복 가능한 섹션, 파일 첨부, 아코디언, 마법사, 모달 |
| **유효성 검사** | 필드 수준 유효성 검사(필수, 최소/최대, 패턴), 사용자 지정 유효성 검사 메시지 |
| **규칙** | 조건부 가시성, 값 표현식, 이벤트 기반 규칙 |
| **통합** | Adobe Sign, Salesforce, Microsoft Dynamics, A/B 테스트 |
| **보안** | reCAPTCHA Enterprise, hCaptcha, CORS 구성 |
| **분석** | Adobe Experience Platform Web SDK, 양식 보기 및 제출 추적 |

### 사전 요구 사항

**문서 기반 작성의 경우:**

- GitHub 계정
- Google 드라이브 또는 Microsoft SharePoint 계정
- 로컬 개발용 노드/npm
- 적응형 Forms 블록이 구성된 AEM 프로젝트
- `forms@adobe.com`과(와) 폴더 공유(편집 권한)

**유니버설 편집기의 경우:**

- AEM Forms as a Cloud Service 인스턴스
- Edge Delivery Services 프로젝트 구성
- 대상 대상에 대한 필수 권한

**AEM 게시 제출용:**

- AEM Cloud Service 인스턴스 URL 구성됨
- OSGi 레퍼러 필터 구성
- Edge Delivery 사이트 도메인에 대한 CORS 구성

### 제한 사항

**문서 기반 작성:**

- 시트 이름 지정이 `helix-default` 및 `shared-aem`(으)로 제한됨
- 복잡성이 낮은 양식에 적합
- 제한된 규칙 기능
- AEM 워크플로우 없음(AEM 게시 제출 없음)
- 양식 데이터 모델 통합 없음

**유니버설 편집기:**

- 사용자 지정 함수에서 정적/동적 가져오기가 지원되지 않음
- 양식 조각은 독립 실행형만 편집할 수 있습니다.
- 개발의 양식 포함 기능

**일반:**

- `shared-aem`장의 시트에 PII(공개적으로 액세스할 수 있음)가 포함되어서는 안 됩니다.
- 원본 간 제출을 위한 CORS 구성 필요
- AEM 게시 제출에 필요한 OSGi 레퍼러 필터

### 사용 시기

**추천 대상:**

- 높은 등대 점수를 요구하는 성능 크리티컬 웹 사이트
- 사이트에서 이미 Edge Delivery Services을 사용 중
- 신속한 양식 개발 및 구축
- 단순하고 중간 수준의 복잡성 데이터 캡처
- 팀이 스프레드시트 기반 작성을 선호함(문서 기반)
- 신속한 시장 출시 필요 프로젝트

**권장되지 않음:**

- 광범위한 서버측 처리가 필요한 Forms
- REST API가 없는 레거시 시스템과의 긴밀한 통합
- 오프라인 양식 요구 사항
- 전체 제어를 통해 특정 JavaScript 프레임워크(React, Angular)가 필요한 조직

## 기초 구성 요소 기반 적응형 Forms

### 정의

기초 구성 요소는 클래식 AEM Forms 작성 접근 방식을 나타냅니다. AEM Forms에서 수년 동안 사용할 수 있었던 원본 적응형 Forms 구성 요소입니다. Adobe에서는 여전히 지원되지만 기초 구성 요소를 새로 만드는 것보다 기존 양식을 유지 관리하는 것이 좋습니다.

### 아키텍처

기초 구성 요소는 기존 AEM 아키텍처를 사용합니다.

- **콘텐츠 모델**: JCR 콘텐츠 구조가 있는 WCM `cq:Page` 구성 요소
- **루트 구조**: `guideContainer`(루트) → `rootPanel` → `items`(양식 필드)
- **렌더링**: 클라이언트측 JavaScript을 사용한 서버측 렌더링
- **SOM 식**: 양식 개체를 참조하기 위한 개체 모델 스크립팅

### 렌더링 모델

Foundation 구성 요소는 서버측 렌더링을 사용합니다.

1. JCR 저장소에 저장된 양식 콘텐츠
2. AEM 서버 프로세스 양식 구조
3. 렌더링하고 브라우저로 전송한 HTML 완료
4. 클라이언트측 JavaScript은 상호 작용 및 유효성 검사를 처리합니다

### 주요 기능

| 범주 | 기능 |
|----------|-------------|
| **구성 요소** | 모든 핵심 구성 요소에 해당하는 40개 이상의 구성 요소 +: Adobe Sign 블록, 차트, 스크리블 서명, 이미지 선택, 요약 단계, 파일 첨부 목록 |
| **양식 모델** | 양식 데이터 모델(FDM), XDP/XFA 템플릿, XML 스키마(XSD), JSON 스키마 |
| **규칙 엔진** | 시각적 편집기 + 코드 편집기 (forms-power-users 그룹용) |
| **디지털 서명** | Adobe Sign 통합, 스크리블 서명 |
| **제출 액션** | 핵심 구성 요소와 유사한 여러 OOTB 작업 |

### 기초 전용 구성 요소

다음 구성 요소는 Foundation 구성 요소에서 **사용할 수 있습니다**.

- Adobe Sign 차단
- 차트
- 첨부 파일 나열
- 각주 플레이스홀더
- 이미지 선택
- 스크리블 서명
- 요약 단계
- Turnstile Captcha

### 사전 요구 사항

- AEM Forms as a Cloud Service 또는 AEM 6.5 Forms
- 적응형 양식 템플릿(Foundation)
- `forms-users` 그룹의 사용자

### 제한 사항

- **게시**: AEM 전용(Edge Delivery Services 또는 Headless API 없음)
- **성능**: 표준 성능(Lighthouse 점수에 최적화되지 않음)
- **아키텍처**: BEM 규정 준수 없이 레거시 아키텍처
- **Source 열기**: 오픈 소스 아님
- **향후 개발**: 유지 관리 모드; 핵심 구성 요소에 새로운 기능이 주로 추가됨

### 사용 시기

**추천 대상:**

- 기존 Foundation 기반 양식 유지 관리
- Adobe Sign 또는 스크리블 서명 통합이 필요한 Forms
- 기존 기초 기능에 종속된 워크플로
- AEM 전용 게시 요구 사항이 있는 프로젝트
- Foundation 전용 구성 요소가 필요한 Forms(차트, 이미지 선택)

**권장되지 않음:**

- 새 양식 개발(핵심 구성 요소 사용)
- Edge Delivery Services 게시가 필요한 프로젝트
- 헤드리스 양식 API
- 성능에 중요한 구현
- 미래 지향적 아키텍처에 우선 순위를 두는 프로젝트

## 비교 테이블

| 매개변수 | 핵심 구성 요소 | Edge Delivery Services 양식 | 기초 구성 요소 |
|-----------|-----------------|-----------------------------|-----------------------|
| **상태** | 새 양식에 권장 | 고성능 사이트에 권장 | 유지 관리 모드 |
| **아키텍처** | 모듈식, BEM 호환 | Edge 우선, 분리됨 | 기존 WCM |
| **렌더링** | 서버측 + Headless | 클라이언트측 전용 | 서버측 |
| **게시** | AEM + Edge Delivery + 헤드리스 API | Edge Delivery Services 전용 | AEM만 |
| **작성** | AEM Forms 편집기 | 범용 편집기 또는 스프레드시트 | AEM Forms 편집기 |
| **성능** | 양호(기초보다 개선됨) | 훌륭함(높은 등대 점수) | 표준 |
| **구성 요소 수** | 30 | 20+(모든 HTML5 입력 유형) | 40+ |
| **Source 열기** | 예(GitHub) | 예 | 아니요 |
| **양식 데이터 모델** | ✅ | ✅(유니버설 편집기에만 해당) | ✅ |
| **JSON 스키마** | ✅ | 제한적 | ✅ |
| **XDP/XFA 지원** | 제한적 | ❌ | ✅ |
| **XML 스키마** | ❌ | ❌ | ✅ |
| **규칙 엔진** | 고급 비주얼 편집기 | 고급(범용 편집기) / 제한적(문서 기반) | 고급 시각적 + 코드 편집기 |
| **디지털 서명** | ❌ | ❌ | ✅ |
| **Adobe Sign** | ❌ | 통합을 통해 | ✅(기본 블록) |
| **기록 문서** | ✅ | ✅ | ✅ |
| **CAPTCHA 옵션** | reCAPTCHA, hCaptcha | reCAPTCHA Enterprise, hCaptcha | reCAPTCHA, hCaptcha, Turnstile |
| **AEM 워크플로** | ✅ | ✅(AEM 게시를 통해) | ✅ |
| **헤드리스 API** | ✅(자동) | ❌ | ❌ |
| **접근성** | WCAG 호환 | WCAG 호환 | 기본 |
| **배포 속도** | 파이프라인 기반 | 인스턴트(Commit to live) | 파이프라인 기반 |
| **스타일링** | BEM CSS, 테마 | CSS, 프로젝트 수준 테마 | CSS, 테마 |
| **버전 관리** | ✅(사이트에서 상속) | Git 기반 | ✅ |
| **현지화** | AEM 번역 워크플로 | 수동 / AEM Sites 워크플로 | AEM 번역 워크플로 |

## 결정 매트릭스

| 요구 사항 | 권장 방법 |
|-------------|---------------------|
| 새 양식 개발 | 핵심 구성 요소 |
| 기존 양식 유지 관리 | 기초 구성 요소(마이그레이션 전까지) |
| 성능에 중요한 성능(높은 등대 점수) | Edge Delivery Services 양식 |
| 헤드리스 / 옴니채널 게재 | 핵심 구성 요소 |
| Adobe Sign 통합 | 기초 구성 요소 |
| 스프레드시트 기반 작성 | Edge Delivery Services(문서 기반) |
| Edge 전달을 통한 Visual WYSIWYG 작성 | Edge Delivery Services (유니버설 편집기) |
| 복잡한 엔터프라이즈 통합 | 핵심 구성 요소 또는 기초 구성 요소 |
| 래피드 프로토타이핑 | Edge Delivery Services(문서 기반) |
| XFA/XDP 템플릿 지원 | 기초 구성 요소 |
| 사용자 지정 React/Angular 프론트엔드 | 핵심 구성 요소(Headless API) |

## 마이그레이션 고려 사항

### 기초 구성 요소를 핵심 구성 요소

- **도구**: AEM 현대화 도구(Forms 전환 유틸리티)
- **노력**: 양식 복잡성에 따라 보통~높음
- **고려 사항**:
   - 규칙은 수동 재구성이 필요합니다.
   - 기초 전용 구성 요소(Adobe Sign 블록, 스크리블 서명, 차트)가 마이그레이션 도중 삭제됩니다.
   - 번역 설정이 이월되지 않음
   - 사용자 정의 기능을 다시 작성해야 함

### 기존 - Edge Delivery Services

- **방법**: 유니버설 편집기 또는 문서 기반 작성을 사용하여 양식을 다시 빌드합니다.
- **노력**: 복잡한 양식에서는 높음, 간단한 양식에서는 낮음
- **이점**: 상당한 성능 향상, 최신 개발 경험

## 설명서 간 차이 및 불명확성

다음 영역에는 설명서가 불완전하거나 모호합니다.

1. **핵심 구성 요소 XDP/XFA 지원**: 설명서는 &quot;제한된&quot; 지원을 나타내지만 정확한 제한 사항을 지정하지 않습니다.
2. **Edge Delivery Services 양식 포함**: 설명서에서 &quot;곧 제공 예정&quot;으로 표시됨, 현재 상태 불명확함
3. **향후 기초 구성 요소**: 명시적 사용 중단 타임라인이 없습니다. &quot;유지 관리 모드&quot;로 설명되어 있습니다.
4. **Headless API 범위**: 서버 렌더링과 Headless 양식 간의 정확한 기능 패리티가 문서화되지 않음
5. **성능 벤치마크**: 접근 방식 간의 특정 등대 점수 비교가 제공되지 않았습니다.

## 관련 리소스

- [적응형 양식(핵심 구성 요소) 만들기](/help/forms/creating-adaptive-form-core-components.md)
- [적응형 양식(기초 구성 요소) 만들기](/help/forms/creating-adaptive-form.md)
- [Edge Delivery Services Forms 개요](/help/edge/docs/forms/overview.md)
- [유니버설 편집기 시작](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
- [문서 기반 작성 자습서](/help/edge/docs/forms/tutorial.md)
- [마이그레이션 유틸리티 도구](/help/forms/migration-utility-tool-for-af-core-components.md)
- [GitHub의 AEM Forms 핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)
