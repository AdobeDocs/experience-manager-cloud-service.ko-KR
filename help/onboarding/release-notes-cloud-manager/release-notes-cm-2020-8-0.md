---
title: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2020.8.0
description: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2020.8.0
feature: Release Information
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# Adobe Experience Manager에서 Cloud Service 2020.8.0 {#release-notes}으로 Cloud Manager에 대한 릴리스 노트

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2020.8.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

2020년 8월 06일 Cloud Service으로 AEM의 Cloud Manager에 대한 릴리스 날짜는 2020.8.0.

## 새로운 기능 {#whats-new-cloud-manager}

* 콘텐츠 감사는 Cloud Manager Sites Production Pipeline에서 활성화된 기능입니다. 이제 사이트가 있는 프로그램에 대한 프로덕션 파이프라인 구성에는 **컨텐트 감사**&#x200B;이라는 세 번째 탭이 포함됩니다. 프로덕션 파이프라인이 실행될 때마다 사용자 정의 기능 테스트 후 파이프라인에 새로운 컨텐츠 감사 단계가 포함되며, 이는 성능, SEO(검색 엔진 최적화), 접근성, 우수 사례 및 PWA(점진적 웹 앱)를 비롯한 다양한 차원과 사이트를 평가합니다.


   >[!NOTE]
   >콘텐츠 감사가 경험 감사로 이름이 변경되었습니다.

   자세한 내용은 [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md)를 참조하십시오.

* 자산 프로그램에서 새로 생성된 환경이 이제 스마트 콘텐츠 서비스로 자동으로 구성됩니다.

* 최대 절전 모드 환경에서는 Cloud Manager의 **개요** 페이지에서 최대 절전 모드를 해제할 수 있습니다.

* Google Lighthouse를 기반으로 한 페이지에서 경험 확인을 수행하는 기능 Cloud Manager 파이프라인의 일부로 최대 25개의 페이지를 확인 및 검증하여 경험 KPI에 대해 확인할 수 있으며 Cloud Manager UI에 점수가 표시됩니다.

### 버그 수정 {#bug-fixes-cm}

* 불필요하고 원하지 않는 일부 SonarQube 플러그인이 코드 품질 스캐닝의 일부로 실행 중이었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 경우에 따라 완료된 파이프라인 실행이 완료된 것으로 기록되지 않아 파이프라인의 새로운 실행을 방지할 수 없습니다.

* 내부 통신 문제로 인해 파이프라인 실행이 *중단되는 경우가 있습니다.*

* 새 조직을 프로비저닝할 때 시스템 관리자 이외의 관리자 역할을 가진 일부 사용자에게 Cloud Manager에 대한 액세스 권한이 잘못 부여되었습니다.

* 특정 조건에서 색인 업데이트 작업이 여러 번 동시에 시작되어 배포 오류가 발생했습니다.

* 프로그램 카드의 도구 설명이 일관되게 올바르지 않습니다.

* 삭제된 환경에서 작업을 시도하도록 사용자 인터페이스가 잘못 허용되었습니다.

* 클라우드 관리자의 **개요** 페이지에 색상 불일치가 있습니다.

### 알려진 문제 {#known-issues-cm}

* 잘못된 페이지가 포함되므로 콘텐츠 감사 평균 점수가 최저 점수로 표시됩니다.

* 컨텐츠 감사 탭에 게시 도메인 대신 작성자 도메인을 사용하여 기본 URL이 잘못 표시됩니다.

* 컨텐츠 감사 단계를 활성화하려면 파이프라인을 편집하고 선택적으로 페이지를 추가해야 합니다. 페이지가 추가되지 않으면 홈 페이지가 감사됩니다.