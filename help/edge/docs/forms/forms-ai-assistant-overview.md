---
title: Forms Experience Builder
description: Forms Experience Builder 소개
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 69f17a4abddf025207448caed11f138c275e7b33
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 100%

---


# Forms Experience Builder 소개

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 설명서는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 Forms Experience Builder가 계속 발전함에 따라 기능, 명령 및 예제가 변경될 수 있습니다.

AEM Forms Experience Builder는 생성형 AI의 힘을 활용하여 디지털 폼 경험의 생성 및 업데이트를 민주화하고 가속화합니다. 자연어 인터랙션을 통해 의도 기반 워크플로를 활성화함으로써 사용자가 빠르고 간단하게 양식을 디자인, 수정 및 최적화할 수 있습니다.

최신 웹 기술을 기반으로 빌드되고 고급 AI 서비스로 구동되는 Forms Experience Builder로 기술 사용자와 비기술 사용자 모두 대화형 인터페이스를 통해 정교한 전문가 수준의 양식을 만들 수 있습니다. 이 혁신적인 접근 방식은 가치 창출 시간을 며칠에서 몇 시간으로 단축하고, 인터페이스 단순화를 통해 기술적 장벽을 제거하며, 전체 양식 에코시스템으로 현대화 노력을 확장합니다.

## 핵심 기능

Forms Experience Builder는 강력한 디지털 양식을 만드는 데 필요한 두 가지 기본 워크플로를 제공합니다.

### &#x200B;1. AI 기반 양식 생성

**자연어 양식 생성**

쉬운 영어 설명을 사용하여 처음부터 완전한 양식을 만듭니다. “평가 척도와 댓글 필드가 포함된 고객 피드백 양식 만들기”와 같은 요구 사항을 간단히 설명하면 Forms Experience Builder가 적절한 양식 구조를 생성합니다. 시각적 편집기의 경험 빌더를 사용하여 더 많은 필드, 유효성 검사 규칙 및 제출 논리를 추가할 수 있습니다.

**동적 필드 관리**

대화형 명령을 통해 양식 필드를 추가, 수정 또는 제거합니다. AI는 컨텍스트를 이해하고 요구 사항에 따라 필드 유형, 유효성 검사 규칙 및 사용자 인터페이스 개선 사항을 지능적으로 제안할 수 있습니다.

**레이아웃 최적화**

자연어를 통해 양식 레이아웃과 구성을 업데이트합니다. “양식 레이아웃을 마법사 레이아웃으로 변경”과 같은 변경 사항을 요청하면 Forms Experience Builder가 적절한 스타일과 레이아웃 조정을 적용합니다.

**종합적인 제출 액션 구성**

기존 비즈니스 시스템과 통합되도록 양식 제출을 구성:

- **이메일 통합**: 자동 이메일 알림 및 확인 설정
- **REST API 엔드포인트**: 사용자 정의 애플리케이션 및 서비스에 연결
- **클라우드 스토리지**: Azure Blob Storage, SharePoint 및 OneDrive와 통합
- **워크플로 자동화**: Power Automate 및 Workfront Fusion에 연결
- **마케팅 플랫폼**: 리드 관리를 위해 Marketo와 직접 통합
- **AEM 워크플로**: 기존 AEM 워크플로 기능 활용

### &#x200B;2. 지능형 가져오기 및 변환

**지원되는 가져오기 포맷**

기존 양식과 문서를 대화형 디지털 환경으로 변환합니다. Forms Experience Builder는 다음을 지원합니다.

- **Acroforms**: 기존 필드 구조를 갖춘 대화형 PDF forms
- **XFA PDF**: 복잡한 XML 기반 양식 아키텍처
- **플랫 PDF**: 정적 문서를 대화형 양식으로 변환
- **이미지 및 스크린샷**: JPG, PNG 포맷 (크기 제한 사항은 팀에 문의)
- **손으로 그린 양식**: 스케치와 종이 양식 사진

**지능형 변환 프로세스**

업로드된 콘텐츠는 다음으로 분석됩니다.

- 필드 유형 및 관계 감지
- 가능한 한 레이아웃 유지
- 현대적인 반응형 디자인으로 개선
- 고급 유효성 검사 및 조건 논리 추가
- 접근성 및 모바일 경험 최적화

## 작동 방법

Forms Experience Builder는 간단한 대화형 접근 방식을 따릅니다.

    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
    │  1. 설명    │───▶│  2. AI 생성  │───▶│  3. 조정 및    │
    │  사용자 양식      │    │  초기 양식   │    │  구성      │
    │  요구사항   │    │                 │    │                 │
    └─────────────────┘    └─────────────────┘    └─────────────────┘
    │                       │                       │
    │                       │                       │
    ▼                       ▼                       ▼
    ┌───────────────────────────────────────────────────────────────────────────┐
    │  “대출 신청서 만들기”  →  관련 내용을 기재한 양식                  │
    │  “이메일 필드 추가”           →  필드 및 기본                          │
    │  “@firstname@gmail.com에 제출된 이메일 값을 설정” →  유효성 검사 규칙   │
    └───────────────────────────────────────────────────────────────────────────┘

## 예시

<!--
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Transform PDF Forms to Digital Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Transform PDF Forms to Digital Forms</p>
                    <p class="is-size-6">Convert Acroforms, XFA PDFs, or flat PDF documents into responsive, interactive digital forms with enhanced functionality.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Modernize Legacy XFA Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Modernize Legacy XFA Forms</p>
                    <p class="is-size-6">Transform complex XFA applications into modern, accessible digital experiences with improved user workflows.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Convert Screenshots to Digital Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Convert Screenshots to Digital Forms</p>
                    <p class="is-size-6">Turn images, screenshots, or hand-drawn forms into fully functional digital experiences.</p>
                </div>
            </div>
        </div>
    </div>
</div>
-->

<!-- #### Import and Enhance Web Forms

Import existing HTML forms and enhance them with advanced features while preserving existing functionality.

**Key benefits:**

- Advanced validation and business logic
- Conditional field behaviors
- Multi-channel submission options
- Enhanced user experience design -->

## Forms Experience Builder와 기존 개발 비교

| 측면 | 전통적 양식 생성 | Forms Experience Builder |
|--------|---------------------------|----------------------|
| **생성 시간** | 2-3 일 | 2-3 시간 |
| **기술적인 지식** | 필수 | 불필요 |
| **유효성 검사 규칙** | 수동 코딩 | 자연어 |
| **접근성** | 수동 구현 | 기본 제공 규정 준수 |


## 조직의 이점

<!--
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Democratized Form Creation">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Democratized Form Creation</p>
                    <p class="is-size-6">Empower non-technical users to create sophisticated forms without programming knowledge through natural language conversations.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Reduced Time to Value (TTV)">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Reduced Time to Value (TTV)</p>
                    <p class="is-size-6">Dramatically accelerate form development from days to hours, enabling faster go-to-market for digital initiatives.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Interface Simplicity">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Interface Simplicity</p>
                    <p class="is-size-6">Eliminate the learning curve with an intuitive conversational interface, reducing training time and increasing adoption.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Scaling Modernization Efforts">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Scaling Modernization Efforts</p>
                    <p class="is-size-6">Modernize legacy form portfolios efficiently, preserving business logic and enhancing user experience across your entire form ecosystem.</p>
                </div>
            </div>
        </div>
    </div>
</div>
-->

## 온보딩

Forms Experience Builder는 현재 얼리 액세스(EA) 프로그램의 일부로 제공됩니다. 참여하고 접근하려면 다음 정보가 필요합니다.

### 필수 정보

- **IMS 조직 ID**: Adobe 조직 식별자
- **프로그램 ID**: Adobe Experience Cloud 내의 특정 프로그램 식별자
- **프로젝트 세부 정보**: 타임라인, 범위 및 의도된 사용 사례
- **공식 업무 이메일**: 조직의 Adobe 계정과 연결됨

### IMS 조직 ID 및 프로그램 ID를 얻는 방법

IMS 조직 ID와 프로그램 ID를 찾는 자세한 단계는 다음을 참조하십시오.

- [Adobe Experience Cloud 조직 설정 안내서](/help/onboarding/cloud-manager-introduction.md)
- [프로그램 및 환경 관리](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

### 액세스 요청

1. 위의 안내서를 사용하여 IMS 조직 ID 및 프로그램 ID 수집
2. [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)으로 이메일을 보내 액세스 요청
3. 요청에 포함되어야 하는 내용:
   - 조직 이름 및 IMS 조직 ID
   - 프로그램 ID
   - 프로젝트 타임라인 및 범위
   - 의도된 사용 사례 및 비즈니스 목표

>[!IMPORTANT]
>
> **제한된 가용성 프로그램**: Forms Experience Builder 액세스는 내부 이해 당사자의 승인을 받아야 합니다. Adobe는 프로그램 용량과 얼리 액세스 기준과의 일치성을 기준으로 요청을 검토합니다. 승인 여부는 보장되지 않으며 현재 프로그램 가용성 여부에 따라 달라집니다.

얼리 액세스 프로그램과 그 기능에 대한 자세한 내용은 [AEM Forms 얼리 액세스 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

## 시작하기

Forms Experience Builder를 시작하려면 [Forms Experience Builder 설명서](forms-ai-assistant-getting-started.md)를 방문하십시오. 선호하는 워크플로에 따라 AEM Forms 편집기 또는 범용 편집기를 통해 Forms Experience Builder에 액세스할 수 있습니다.

양식 생성 프로세스를 혁신하고자 하는 조직을 위해 Forms Experience Builder는 대화형 AI의 유연성과 엔터프라이즈급 양식 관리의 견고성을 결합한 강력하고 직관적인 솔루션을 제공합니다.
