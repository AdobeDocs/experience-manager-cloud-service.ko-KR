---
title: AEM as a Cloud Service 릴리스 2021.2.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.2.0의 Cloud Manager 릴리스 노트
exl-id: 281f9523-dec2-44f1-9459-5a45d48489d9
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 2%

---

# Adobe Experience Manager as a Cloud Service 2021.2.0 {#release-notes} 의 Cloud Manager 릴리스 노트

이 페이지에서는 AEM as a Cloud Service 2021.2.0 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.2.0의 Cloud Manager 릴리스 날짜는 2021년 2월 11일입니다.

## Cloud Manager {#cloud-manager}

### 새로운 기능 {#what-is-new}

* 이제 자산 고객은 Cloud Manager UI를 통해 셀프 서비스 방식으로 Brand Portal 인스턴스를 배포할 시기 및 위치를 선택할 수 있습니다. 자산 솔루션이 있는 일반(샌드박스 아님) 프로그램의 경우 이제 프로덕션 환경에서 Brand Portal을 프로비저닝할 수 있습니다. 프로비저닝은 프로덕션 환경에서 한 번만 수행할 수 있습니다.

* 프로젝트 및 샌드박스 만들기에 사용된 AEM 프로젝트 원형이 버전 25로 업데이트되었습니다.

* 코드 스캔 중에 식별된 더 이상 사용되지 않는 API 목록은 최신 Cloud Service SDK 릴리스에서 더 이상 사용되지 않는 추가 클래스 및 메서드를 포함하도록 개선되었습니다.

* Cloud Manager용 SonarQube 프로필이 Sonar 규칙 squid:S2142를 제거하도록 업데이트되었습니다. 스레드 중단 확인과 더 이상 충돌하지 않습니다.

* Cloud Manager UI는 연관된 환경에 연결된 실행 중인 파이프라인이 있거나 현재 승인 단계를 기다리는 중이므로 도메인 이름을 일시적으로 추가/업데이트할 수 없는 사용자에게 알려줍니다.

* Sonar가 접두사로 추가된 고객 `pom.xml` 파일에 설정된 속성이 이제 빌드 및 품질 검사 오류를 방지하기 위해 동적으로 제거됩니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알려줍니다.

* Cloud Service 호환성 문제를 다루는 추가적인 코드 품질 규칙이 추가되었습니다.

### 버그 수정  {#bug-fixes}

* 도메인 이름과 일치하는 SSL 인증서는 더 이상 대/소문자를 구분하지 않습니다.

* 이제 Cloud Manager UI에서 인증서 개인 키가 적절한 오류 메시지와 함께 2048비트 제한을 충족하지 않는지 사용자에게 알려줍니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알려줍니다.

* 경우에 따라 내부 문제로 인해 환경 삭제가 중단될 수 있습니다.

* 일부 파이프라인 오류가 파이프라인 오류로 잘못 보고되었습니다.
