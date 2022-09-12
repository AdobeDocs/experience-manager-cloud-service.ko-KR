---
title: AEM as a Cloud Service 릴리스 2021.12.0의 Cloud Manager 릴리스 노트
description: 다음은 AEM as a Cloud Service 릴리스의 Cloud Manager에 대한 릴리스 2021.12.0.
feature: Release Information
exl-id: ee920bc5-cad7-4fac-bf73-bc1178699f90
source-git-commit: 1b7183421b9acd30697f1dc228dd9e2728d24ba6
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 1%

---

# Adobe Experience Manager as a Cloud Service 2021.12.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.12.0의 Cloud Manager 릴리스 날짜는 2021년 12월 16일입니다. 다음 릴리스는 2022년 1월 20일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* UI에 이미 표시되는 커밋 해시가 이제 API에서도 제공됩니다.
* 이제 활동 페이지에 파이프라인 세부 사항을 요약하여 제공하는 파이프라인 실행을 위한 팝오버가 포함되어 있습니다.
* 활동 페이지에 제공된 추가 세부 사항을 포함하도록 업데이트를 추가했습니다.
* 이제 Cloud Manager의 학습 탭에 API 안내서 및 관련 리소스에 빠르게 액세스할 수 있습니다.
* 이제 배포 관리자 역할을 가진 사용자는 저장소 페이지의 작업 메뉴에서 분기가 없는 저장소에 대한 프로젝트/분기 생성 마법사를 시작할 수 있습니다.
* 이제 파이프라인 추가 또는 편집 워크플로우에 있는 배포 관리자에 선택한 저장소에 분기가 없는 경우 분기나 프로젝트를 생성하는 방법에 대한 정보를 제공합니다.
* 에 새로운 Cloud Manager 셀프 서비스 기능이 추가되었습니다. [환경 수준에서 자유 형식 변수 및 암호 추가.](/help/implementing/cloud-manager/environment-variables.md)
* 새로운 [참조 데모 추가 기능](/help/journey-sites/demos-add-on/overview.md) (2021년 12월 17일에 제공) AEM 제품에 대한 최신 데모 코드 베이스를 설치하고 새로운 기능을 통해 배포할 준비가 되었습니다 [빠른 사이트 생성 도구](/help/journey-sites/quick-site/overview.md) 참조하십시오.
* 이제 프런트엔드 파이프라인이 파이프라인 변수를 지원합니다.
* 이제 모든 샌드박스에 대한 프로그램 편집 대화 상자에서 화면을 활성화할 수 있습니다.
* 개요 페이지에서 클릭유도문안 카드에서 제공하는 지침은 프로덕션 전체 스택 파이프라인과의 연결을 정확하게 반영하도록 새로 고침되었습니다.
* 소스 코드, 커밋 ID 등을 포함하여 파이프라인에 적용할 수 있는 추가 세부 사항을 표시하는 활동 페이지 개선 사항이 추가되었습니다.
* 잠재적인 혼동을 제거하기 위해 TXT 항목(&quot;TXT 레코드&quot; 대신 &quot;TXT 값&quot;)을 복사할 때 UI가 약간 업데이트되었습니다.
* [인증서 오류와 관련된 설명서입니다](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-errors) 문제 해결 단계와 함께 추가 예를 포함하도록 가 업데이트되었습니다.
* 이제 프로덕션에 배포하기 전에 프런트엔드 파이프라인 실행에서 옵션을 사용하여 거부하거나 승인할 수 있습니다.
* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 32로 업데이트되었습니다.


## 버그 수정 {#bug-fixes}

* 기능 및 UI 테스트 가공물이 빌드 단계 로그에 포함되지 않았습니다.
* 제품, 기능 및 UI 테스트 단계의 로그에 공개 API를 통해 액세스할 수 없었습니다.
* 환경 세부 사항 페이지에서 게시 또는 미리 보기 서비스로의 링크가 작동하지 않는 경우가 드물게 나타납니다.
* 사용자가 이름 필드에 다른 이름을 입력할 때에도 전체 스택 프로덕션 파이프라인의 이름이 &quot;프로덕션 파이프라인&quot;으로 유지됩니다.
