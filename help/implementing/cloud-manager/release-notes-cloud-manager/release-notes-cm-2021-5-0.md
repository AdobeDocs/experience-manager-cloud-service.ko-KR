---
title: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: 8ae3cf2f-1865-427a-b612-bdf56e2f0304
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 3%

---

# Adobe Experience Manager as a Cloud Service 2021.5.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.5.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=ko-kr).

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.5.0의 Cloud Manager 릴리스 날짜는 2021년 5월 6일입니다.

### 새로운 기능 {#what-is-new}

* 이제 PackageOverlap 품질 규칙은 동일한 패키지가 동일한 배포된 패키지 세트에서 여러 포함된 위치에 여러 번 배포된 사례를 검색합니다.

* 이제 공용 API의 저장소 끝점에 Git URL이 포함됩니다.

* Cloud Manager 사용자가 다운로드한 배포 로그는 더 통찰력 있게 작성되며 이제는 실패 및 성공 시나리오에 대한 세부 정보를 포함합니다.

* 이제 코드를 Adobe git으로 푸시하는 동안 발생한 간헐적인 오류가 해결되었습니다.

* 이제 프로그램 편집 워크플로우 동안 샌드박스 프로그램에 상거래 추가 기능을 적용할 수 있습니다.

* 다음 *프로그램 편집* 경험을 새로 고쳤습니다.

* 환경 세부 사항 페이지의 도메인 이름 테이블에는 페이지 매김을 통해 최대 250개의 도메인 이름이 표시됩니다.

* 다음 **솔루션 및 추가 기능** 탭 **프로그램 추가** 및 **프로그램 편집** 프로그램에 솔루션을 하나만 사용할 수 있는 경우에도 워크플로우에 솔루션이 표시됩니다.

* 빌드가 배포된 컨텐츠 패키지를 생성하지 않은 경우 빌드 단계 로그에 오류 메시지가 표시되지 않았습니다.

### 버그 수정 {#bug-fixes}

* 경우에 따라 해당 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* 파이프라인 변수 API는 &#39;삭제됨&#39; 변수를 제거하는 대신 상태로만 표시합니다 **삭제됨**.

* 일부 코드 냄새 유형 품질 문제가 안정성 등급에 잘못 영향을 주었습니다.

* 와일드카드 도메인은 지원되지 않으므로 사용자가 와일드카드 도메인을 제출할 수 없도록 UI에서 합니다.

* 자정~오전 1UTC 사이에 파이프라인 실행이 시작되면 Cloud Manager에서 생성한 아티팩트 버전이 전날 작성된 버전보다 클 수 없습니다.

* 샌드박스 프로그램 설정 중에 샘플 코드가 있는 프로젝트가 성공적으로 만들어지면 개요 페이지에서 Git 관리 가 대표 카드의 링크로 표시됩니다.
