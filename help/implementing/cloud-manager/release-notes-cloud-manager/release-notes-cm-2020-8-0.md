---
title: AEM as a Cloud Service 릴리스 2020.8.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2020.8.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: 70674e16-f9ba-4777-98fe-34161e90a481
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# Adobe Experience Manager as a Cloud Service 2020.8.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2020.8.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2020.8.0의 Cloud Manager 릴리스 날짜는 2020년 8월 6일입니다.

## 새로운 기능 {#whats-new-cloud-manager}

* 컨텐츠 감사 는 Cloud Manager Sites 프로덕션 파이프라인에서 사용할 수 있는 기능입니다. 이제 사이트 가 있는 프로그램에 대한 프로덕션 파이프라인 구성에 이름이 인 세 번째 탭이 포함됩니다. **컨텐츠 감사**. 프로덕션 파이프라인이 실행될 때마다 사용자 정의 기능 테스트 후 새로운 컨텐츠 감사 단계가 파이프라인에 포함되며, 이 테스트에서는 성능, SEO(검색 엔진 최적화), 접근성, 모범 사례 및 PWA(점진적 웹 앱)을 비롯한 다양한 차원에 대해 사이트를 평가하게 됩니다.


   >[!NOTE]
   >이후 콘텐츠 감사 이름이 Experience Auditor로 변경되었습니다.

   을(를) 참조하십시오. [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md) 자세한 내용

* 이제 자산 프로그램에서 새로 만든 환경이 스마트 컨텐츠 서비스로 자동 구성됩니다.

* Cloud Manager에서 최대 절전 모드 환경을 해제할 수 있습니다 **개요** 페이지.

* Google Lighthouse에서 제공하는 페이지에서 경험 확인을 수행할 수 있습니다. Cloud Manager 파이프라인의 일부로서 경험 KPI에 대해 최대 25페이지의 유효성 검사와 확인을 수행할 수 있으며 점수는 Cloud Manager UI에 표시됩니다.

### 버그 수정 {#bug-fixes-cm}

* 일부 불필요하고 원치 않는 SonarQube 플러그인이 코드 품질 스캔의 일부로 실행되었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 경우에 따라 완료된 파이프라인 실행이 완료된 것으로 기록되지 않아 파이프라인의 새로운 실행이 방지됩니다.

* 파이프라인 실행은 가끔 *정지* 내부 통신 문제로 인해

* 새 조직을 프로비저닝할 때 시스템 관리자 이외의 관리자 역할을 가진 일부 사용자에게 Cloud Manager에 대한 액세스 권한이 잘못 부여되었습니다.

* 특정 조건에서 인덱스 업데이트 작업이 여러 번 동시에 시작되어 배포 오류가 발생합니다.

* 프로그램 카드의 도구 설명이 일관되게 올바르지 않습니다.

* 사용자 인터페이스가 삭제되는 동안 환경에서 작업을 시도할 수 있도록 잘못 허용되었습니다.

* Cloud Manager의 색상이 일치하지 않습니다 **개요** 페이지.

### 알려진 문제 {#known-issues-cm}

* 잘못된 페이지가 포함되어 컨텐츠 감사 평균 점수가 최저 점수보다 낮아집니다.

* 컨텐츠 감사 탭에 게시 도메인 대신 작성자 도메인을 사용하는 기본 URL이 잘못 표시됩니다.

* 컨텐츠 감사 단계를 활성화하려면 파이프라인을 편집하고 선택적으로 페이지를 추가해야 합니다. 페이지가 추가되지 않으면 홈 페이지가 감사됩니다.
