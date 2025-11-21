---
title: 사이트 마이그레이션 스킬
description: 사이트 마이그레이션 기술은 AI 및 Adobe FDE(Forward Deployed Engineers)의 도움을 받아 웹 사이트를 Edge Delivery Services에 게시합니다.
feature: Edge Delivery Services, Agentic AI
role: Admin, Architect, Developer
source-git-commit: 67d3081be74a654788eab96ae98f88ef7ce4203c
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---


# 사이트 마이그레이션 스킬 {#site-migration}

사이트 마이그레이션 기술은 AI 및 Adobe FDE(Forward Deployed Engineers)의 도움을 받아 웹 사이트를 Edge Delivery Services에 게시합니다. 이 기술은 콘텐츠 및 스타일 마이그레이션을 자동화하고 코드 AEM 작성을 통해 추가로 조정할 수 있는 작성자 전용 Edge Delivery Services 구현을 준비합니다.

## 개요 {#overview}

사이트 마이그레이션 기술은 기존 사이트 또는 디자인을 Edge Delivery Services 프로젝트로 변환합니다. 이 스킬을 사용하는 마이그레이션에는 다음 구성 요소가 있습니다.

* CMS **소스**: 기존 웹 사이트(AEM Publish 포함), 디자인 시스템 또는 디자인 모음(예: Figma)
* **출력**: 블록과 스타일이 적용된 프로덕션 준비 Edge Delivery Services 리포지토리입니다.
* **대상**: 모든 Edge Delivery Services 플랫폼 및 작성 메서드가 대상으로 지원됩니다
* **운영 모델**: 에이전트를 운영하고 마이그레이션을 안내하여 품질과 거버넌스를 보장하는 Adobe Forward Deployed 엔지니어가 제공

## 기능 {#capabilities}

사이트 마이그레이션 기술은 다음과 같은 높은 수준의 작업을 수행합니다.

1. **컨텐츠 마이그레이션** - 페이지 및 자산을 기본 컨텐츠와 선택한 블록 라이브러리에 정렬된 블록을 사용하여 구조화된 Edge Delivery Services 컨텐츠로 변환합니다.

2. **스타일 응용 프로그램** - 다음 방법 중 하나로 Edge Delivery Services의 스타일을 만듭니다.

   * 현재 사이트에서 **현재 스타일 마이그레이션**
   * 제공된 모크(예: Figma)를 사용하여 **다시 디자인**
   * 기존 Edge Delivery Services 구현에서 **기존 블록 디자인 재사용**

일반적인 결과물은 다음과 같습니다.

* Edge Delivery Services 저장소(블록, 스타일, 구성)
* 마이그레이션된 컨텐츠 및 자산
* 작성 구성(문서 작성 또는 유니버설 편집기)
* 마이그레이션된 사이트가 배포된 Edge Delivery Services 환경(미리보기 및 라이브)

그 결과, 문서 작성 또는 유니버설 편집기를 통해 완전히 편집할 수 있는 성능(핵심 웹 바이탈/등대), 접근성 및 중단점 간 반응형 레이아웃에 최적화된 프로덕션 준비 웹 사이트가 만들어집니다.

## 제한 사항 {#limitations}

사이트 마이그레이션 기술은 콘텐츠 및 스타일에 중점을 둡니다. 다음 사용 사례에서는 사이트 마이그레이션 기술 외에 추가적인 구현 노력이 필요합니다.

* 사용자 정의 통합(예: 상거래, CRM, 검색 커넥터)
* 다이내믹 콘텐츠 또는 렌더링(예: 비동기적으로 로드된 콘텐츠, 단일 페이지 애플리케이션 또는 맞춤형 JavaScript 프레임워크)
* 마이그레이션된 환경과 무관한 새로운 기능 개발

이러한 기능이 필요한 경우 Adobe Consulting Services 또는 구현 파트너는 제공된 Edge Delivery 프로젝트를 확장할 수 있습니다.

## 참여 모델 {#engagement}

사이트 마이그레이션 기술은 현재 Adobe Forward Deployed Engineers가 운영하는 참여를 통해 이용할 수 있습니다. 각 프로젝트는 소스 복잡성, 디자인 목표, 콘텐츠 규모 및 거버넌스 요구 사항에 따른 범위 지정 연습으로 시작됩니다.

마이그레이션을 탐색하려면 다음 작업을 수행하십시오.

* 범위 지정 및 일정을 시작하려면 Adobe 담당자 또는 계정 팀에 문의하십시오.
* Adobe은 자격 조건을 확인하고 참여를 예측하며 마이그레이션 계획을 제안합니다.
