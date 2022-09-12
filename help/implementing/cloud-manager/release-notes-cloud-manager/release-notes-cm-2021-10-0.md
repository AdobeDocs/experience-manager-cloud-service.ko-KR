---
title: AEM as a Cloud Service 릴리스 2021.10.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.10.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: f8a87b00-52ce-42a6-a955-45cb14703b40
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 3%

---

# Adobe Experience Manager as a Cloud Service 2021.10.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service Manager에 대한 릴리스 노트를 간략하게 설명합니다2021.10.0.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=ko-kr).

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.10.0의 Cloud Manager 릴리스 날짜는 2021년 10월 14일입니다.


### 새로운 기능 {#what-is-new}

* 향후 몇 가지 변경 사항에 대비하기 위해 기존 배포 파이프라인은 이제 사용자 인터페이스에서 다음과 같이 참조되고 레이블이 지정됩니다. **전체 스택** 파이프라인.

* 이제 파이프라인 카드가 새로 고쳐져서 프로덕션 파이프라인과 비프로덕션 파이프라인을 모두 표시하는 통합된 단일 면을 표시할 수 있으며, 사용자는 각 파이프라인과 연관된 작업 메뉴에서 직접 실행/일시 중지/재개 를 선택할 수 있습니다.

* 이제 배포 관리자 역할의 사용자는 UI를 통해 셀프 서비스 방식으로 프로덕션 파이프라인을 삭제할 수 있습니다.

* 이제 익숙하고 현대적인 모듈을 사용할 수 있도록 파이프라인 경험을 추가 및 편집할 수 있습니다.

* 이제 Cloud Manager 사용자는 **피드백** 랜딩 페이지의 오른쪽 위에 있는 단추.

* 이제 Cloud Manager의 사용자 인터페이스에서 연간 SLA 그래프를 다운로드할 수 있습니다.

* 이제 코드 품질 및 비프로덕션 파이프라인 실행에서는 빌드 단계에서 보다 효율적인 약식 복제 프로세스를 사용하므로 고객이 특히 큰 git 저장소를 사용하는 경우 빌드 시간이 빨라집니다.

* 이제 IP 허용 목록 추가 마법사가 허용된 최대 IP 허용 목록 수에 도달했는지 사용자에게 알려줍니다.

* 이제 Cloud Manager API 설명서에는 로그인한 사용자가 브라우저에서 API를 실험할 수 있도록 해주는 대화형 필드가 포함되어 있습니다. 자세한 내용은 [Cloud Manager API 놀이터](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) 자세한 내용

* &#39;탐색 대상&#39; 아래의 선택 옵션이 비활성화되어 있으면 프로그램 카드의 도구 설명이 더 설명적입니다. 이제 &quot;프로덕션 환경이 없습니다.&quot;가 표시됩니다.

### 버그 수정 {#bug-fixes}

* 드문 경우이지만, Adobe 직원이 고객의 환경을 복원할 경우 환경이 완전히 작동하기 전에 복구가 완료된 것으로 간주됩니다.

* 환경을 만드는 동안 수행된 특정 내부 요청이 다시 시도되지 않았습니다.

* 도메인 이름 확인 후 배포 실패 오류가 발생하면 고객이 Adobe 담당자에게 문의하도록 오류 메시지가 수정되었습니다.
