---
title: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2021.5.0
description: Cloud Service 릴리스로 AEM의 Cloud Manager 릴리스 노트 2021.5.0
feature: 릴리스 정보
translation-type: tm+mt
source-git-commit: 29bc3d02295fb04f3aacda41c43d1733092e1f27
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 3%

---


# Adobe Experience Manager에서 Cloud Service 2021.5.0 {#release-notes}으로 Cloud Manager에 대한 릴리스 노트

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2021.5.0으로 간략하게 설명합니다.

>[!NOTE]
>Adobe Experience Manager의 현재 릴리스 노트를 Cloud Service으로 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR)를 클릭하십시오.

## 릴리스 날짜 {#release-date}

AEM의 Cloud Service 2021.5.0 Cloud Manager에 대한 릴리스 날짜는 2021년 5월 6일입니다.
다음 릴리스는 2021년 6월 3일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new}

* 이제 PackageOverlaps 품질 규칙은 동일한 패키지가 동일한 배포된 패키지 세트에서 여러 위치(예: 여러 포함된 위치)에 여러 번 배포된 경우를 검색합니다.

* 이제 공개 API의 리포지토리 끝점에 Git URL이 포함됩니다.

* Cloud Manager 사용자가 다운로드한 배포 로그는 더 알아보기 쉬워졌으며 이제 오류 및 성공 시나리오에 대한 세부 정보를 포함합니다.

* 코드를 Adobe git으로 푸시하는 동안 가끔씩 발생하는 오류가 해결되었습니다.

* 이제 코드 추가 기능은 편집 프로그램 워크플로우 동안 샌드박스 프로그램에 적용할 수 있습니다.

* *편집 프로그램* 환경이 새로 고침되었습니다.

* 환경 세부 사항 페이지의 도메인 이름 테이블에는 페이지 매김을 통해 최대 250개의 도메인 이름이 표시됩니다.

* **프로그램 추가** 및 **프로그램 편집** 워크플로우에 있는 **솔루션 및 추가 기능** 탭은 솔루션에 대해 하나만 사용할 수 있는 경우에도 표시됩니다.

* 빌드에서 배포된 콘텐츠 패키지를 생성하지 않았을 때의 빌드 단계 로그의 오류 메시지가 명확하지 않았습니다.

### 버그 수정 {#bug-fixes}

* IP 허용 목록 옆에 해당 구성이 배포되지 않았더라도 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* &#39;deleted&#39; 변수를 제거하는 대신 파이프라인 변수 API는 **DELETED** 상태로만 표시합니다.

* 일부 코드 후각 유형 품질 문제가 안정성 등급에 잘못 영향을 주었습니다.

* 와일드카드 도메인은 지원되지 않으므로 UI는 사용자가 와일드카드 도메인을 제출하지 못하도록 합니다.

* 자정~오전 1시 UTC 사이에 파이프라인 실행이 시작되었을 때 Cloud Manager에서 생성된 아티팩트 버전이 전날 생성된 버전보다 클 것으로 보장되지 않았습니다.

* 샌드박스 프로그램 설정 중에 샘플 코드가 있는 프로젝트가 성공적으로 만들어지면 개요 페이지에 메인 카드의 링크로 Git 관리가 표시됩니다.