---
title: Forms Experience Builder
description: 양식 조각을 사용하여 강력한 양식을 더 빠르게 제작
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 6134772ea9916fc17fb7fc8a30e18799a81d4994
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 3%

---


# Forms Experience Builder 소개

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 설명서는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. Forms Experience Builder가 얼리어답터 프로그램 동안 계속 발전함에 따라 기능, 명령 및 예가 변경될 수 있습니다.

AEM Forms Experience Builder는 생성 AI의 기능을 활용하여 디지털 양식 경험을 대중화하고 생성 및 업데이트를 가속화합니다. 자연어 상호 작용을 통한 의도 기반 워크플로를 활성화하여 사용자가 빠르고 간편하게 양식을 원활하게 디자인, 수정 및 최적화할 수 있도록 합니다.

최신 웹 기술을 기반으로 하고 고급 AI 서비스를 기반으로 하는 Forms Experience Builder를 사용하면 기술 사용자와 비기술 사용자 모두 대화 인터페이스를 통해 정교한 전문가 수준의 양식을 만들 수 있습니다. 이 혁신적인 접근 방식은 가치 창출 시간을 수일에서 수시간으로 단축하고, 인터페이스 단순화를 통해 기술 장벽을 제거하며, 전체 양식 생태계에서 현대화 노력을 확대합니다.



## 핵심 기능

Forms Experience Builder는 강력한 디지털 양식을 만들기 위한 두 가지 기본 워크플로우를 제공합니다.

### &#x200B;1. AI 기반 양식 만들기

**자연어 양식 생성**

간단한 영어 설명을 사용하여 처음부터 완전한 양식을 작성하십시오. 간단히 &quot;등급 눈금 및 댓글 필드가 있는 고객 피드백 양식 만들기&quot;와 같은 요구 사항을 설명하면 Forms Experience Builder가 적절한 양식 구조를 생성합니다. 시각적 편집기의 경험 빌더를 사용하여 더 많은 필드, 유효성 검사 규칙 및 제출 논리를 추가할 수 있습니다.

**동적 필드 관리**

대화 명령을 통해 양식 필드를 추가, 수정 또는 제거합니다. AI는 컨텍스트를 이해하고 요구 사항에 따라 필드 유형, 유효성 검사 규칙 및 사용자 인터페이스 개선 사항을 지능적으로 제안할 수 있습니다.

**레이아웃 최적화**

자연어를 통해 양식 레이아웃 및 구성을 업데이트합니다. &quot;양식 레이아웃을 마법사 레이아웃으로 변경&quot;과 같은 변경 사항을 요청하면 Forms Experience Builder가 적절한 스타일 및 레이아웃 조정을 적용합니다.

**포괄적인 제출 액션 구성**

기존 비즈니스 시스템과 통합하도록 양식 제출을 구성합니다.

- **이메일 통합**: 자동 이메일 알림 및 확인을 설정합니다.
- **REST API 끝점**: 사용자 지정 응용 프로그램 및 서비스에 연결합니다.
- **클라우드 저장소**: Azure Blob 저장소, SharePoint 및 OneDrive와 통합
- **워크플로 자동화**: Power Automate 및 Workfront Fusion에 연결
- **마케팅 플랫폼**: 잠재 고객 관리를 위해 Marketo과 직접 통합
- **AEM 워크플로**: 기존 AEM 워크플로 기능 활용


### &#x200B;2. 지능적인 가져오기 및 전환

**지원되는 가져오기 형식**

기존 양식 및 문서를 대화형 디지털 경험으로 변환합니다. Forms Experience Builder는 다음을 지원합니다.

- **Acroforms**: 기존 필드 구조를 사용하는 대화형 PDF forms
- **XFA PDF**: 복잡한 XML 기반 양식 아키텍처
- **플랫 PDF**: 대화형 양식으로 변환된 정적 문서
- **이미지 및 스크린샷**: JPG, PNG 형식(크기 제한 사항은 팀에 확인)
- **손으로 그린 Forms**: 스케치 및 종이 양식 사진


**지능형 변환 프로세스**

업로드된 콘텐츠는 다음으로 분석됩니다.

- 필드 유형 및 관계 감지
- 가능한 한 레이아웃 유지
- 최신 반응형 디자인으로 향상
- 고급 유효성 검사 및 조건부 논리 추가
- 접근성 및 모바일 환경에 최적화

## 작동 방법

Forms Experience Builder는 다음과 같은 간단한 대화형 접근 방식을 따릅니다.

    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
    │ 1. 설명    │───▶│ 2. AI가 │───▶│ 3을(를) 만듭니다. 세분화 및    │
    │ 내 양식      │    │ 초기 양식   │    │ 구성      │
    │ 요구 사항   │    │                 │    │                 │
    └─────────────────┘    └─────────────────┘    └─────────────────┘
    │                       │                       │
    │                       │                       │
    ▼                       ▼                       ▼
    ┌───────────────────────────────────────────────────────────────────────────┐
    │ 관련 내용이 있는 &quot;대출 신청서 양식 만들기&quot; → 양식                  │
    │ &quot;전자 메일 필드 추가&quot;           → 필드 및 기본                          │
    │ &quot;이메일을 @firstname@gmail.com에 값 설정&quot; → 유효성 검사 규칙   │
    └───────────────────────────────────────────────────────────────────────────┘

## 예제 시나리오

<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Transform PDF Forms to Digital Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">PDF forms을 디지털 Forms으로 변환</p>
                    <p class="is-size-6">Acroforms, XFA PDF 또는 플랫 PDF 문서를 기능이 향상된 반응형 대화형 디지털 양식으로 변환할 수 있습니다.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Modernize Legacy XFA Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">기존 XFA Forms 현대화</p>
                    <p class="is-size-6">향상된 사용자 워크플로우를 통해 복잡한 XFA 애플리케이션을 현대적이고 액세스 가능한 디지털 환경으로 변환합니다.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Convert Screenshots to Digital Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">스크린샷을 디지털 Forms으로 변환</p>
                    <p class="is-size-6">이미지, 스크린샷 또는 손으로 그린 양식을 완전한 기능의 디지털 경험으로 만들 수 있습니다.</p>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- #### Import and Enhance Web Forms

Import existing HTML forms and enhance them with advanced features while preserving existing functionality.

**Key benefits:**

- Advanced validation and business logic
- Conditional field behaviors
- Multi-channel submission options
- Enhanced user experience design -->

## Forms Experience Builder와 기존 개발 비교

| 측면 | 기존 양식 만들기 | Forms Experience Builder |
|--------|---------------------------|----------------------|
| **만들 시간** | 2-3일 | 2-3시간 |
| **기술 정보** | 필수 | 필요하지 않음 |
| **유효성 검사 규칙** | 수동 코딩 | 자연어 |
| **접근성** | 수동 구현 | 기본 제공 규정 준수 |


## 조직에 대한 이점

<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Democratized Form Creation">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">민주화된 양식 만들기</p>
                    <p class="is-size-6">기술 전문가가 아닌 사용자도 자연어 대화를 통해 지식을 프로그래밍하지 않고도 정교한 양식을 만들 수 있습니다.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Reduced Time to Value (TTV)">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">가치 창출 시간(TTV) 단축</p>
                    <p class="is-size-6">며칠씩 걸리던 양식 개발을 몇 시간에 걸쳐 크게 가속화하여 디지털 이니셔티브의 출시 시기를 앞당길 수 있습니다.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Interface Simplicity">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">인터페이스 단순성</p>
                    <p class="is-size-6">직관적인 대화 인터페이스로 학습 곡선을 제거하여 교육 시간을 줄이고 채택률을 높입니다.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Scaling Modernization Efforts">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">현대화 노력 확장</p>
                    <p class="is-size-6">기존 양식 포트폴리오를 효율적으로 현대화하여 비즈니스 논리를 유지하고 전체 양식 에코시스템에서 사용자 경험을 향상시킵니다.</p>
                </div>
            </div>
        </div>
    </div>
</div>

## 온보딩

Forms Experience Builder는 현재 조기 액세스(EA) 프로그램의 일부로 사용할 수 있습니다. 참가하여 액세스 권한을 얻으려면 다음 정보가 필요합니다.

### 필수 정보

- **IMS 조직 ID**: Adobe 조직 식별자
- **프로그램 ID**: Adobe Experience Cloud 내의 특정 프로그램 식별자
- **프로젝트 세부 정보**: 타임라인, 범위 및 사용 사례
- **공식 작업 전자 메일**: 조직의 Adobe 계정과 연결됨


### IMS 조직 ID 및 프로그램 ID를 가져오는 방법

IMS 조직 ID 및 프로그램 ID를 찾는 자세한 단계는 다음을 참조하십시오.

- [Adobe Experience Cloud 조직 설정 안내서](/help/onboarding/cloud-manager-introduction.md)
- [프로그램 및 환경 관리](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

### 액세스 요청

1. 위의 안내서를 사용하여 IMS 조직 ID 및 프로그램 ID 수집
2. [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 액세스를 요청하는 전자 메일 보내기
3. 요청에 포함:
   - 조직 이름 및 IMS 조직 ID
   - 프로그램 ID
   - 프로젝트 타임라인 및 범위
   - 의도한 사용 사례 및 비즈니스 목표

>[!IMPORTANT]
>
> **제한된 가용성 프로그램**: Forms Experience Builder에 대한 액세스는 내부 이해 당사자의 승인을 받아야 합니다. Adobe은 프로그램 용량 및 조기 액세스 기준에 따라 요청을 검토합니다. 승인은 보장되지 않으며 현재 프로그램 가용성에 따라 다릅니다.

조기 액세스 프로그램 및 기능에 대한 자세한 내용은 [AEM Forms 조기 액세스 설명서](/help/forms/early-access-ea-features.md)를 참조하세요.


## 시작하기

Forms Experience Builder를 시작하려면 [Forms Experience Builder 설명서](forms-ai-assistant-getting-started.md)를 참조하십시오. 선호하는 워크플로우에 따라 Forms 편집기 또는 유니버설 편집기를 통해 AEM Forms Experience Builder에 액세스할 수 있습니다.

양식 생성 프로세스를 혁신하려는 조직을 위해 Forms Experience Builder는 대화식 AI의 유연성과 엔터프라이즈급 양식 관리의 견고성을 결합한 강력하고 직관적인 솔루션을 제공합니다.
