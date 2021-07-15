---
title: AEM as a Cloud Service 릴리스 2021.7.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.7.0의 Cloud Manager 릴리스 노트
feature: 릴리스 정보
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 40e5d00abc3caceadbbb26097d6891f62e2cdbd6
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 4%

---

# Adobe Experience Manager as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.7.0 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service에 대한 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR)를 클릭하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.7.0의 Cloud Manager 릴리스 날짜는 2021년 7월 15일입니다.
다음 릴리스는 2021년 8월 12일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new}

* 고객은 이제 Cloud Manager 빌드 프로세스에 Azul 8 및 11개의 JDK를 사용할 수 있으며 이러한 JDK 중 하나를 도구 체인 호환 Maven 플러그인 *또는 전체 Maven 프로세스 실행에 사용하도록 선택할 수 있습니다.*

* 이제 아웃바운드 송신 IP가 빌드 단계 로그 파일에 기록됩니다.

* 이전 버전의 AEM을 실행하는 단계 및 프로덕션 환경에서는 **Update Available** 상태를 보고합니다.

* 지원되는 최대 SSL 인증서는 프로그램당 20개로 증가했습니다.

* 구성할 수 있는 최대 도메인 수가 환경당 500개로 늘어났습니다.

* **Git** 관리 단추가 **Access Git Info**&#x200B;로 변경되었으며 대화 상자가 시각적으로 새로 고침되었습니다.

* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 28로 업데이트되었습니다.

### 버그 수정 {#bug-fixes}

* 경우에 따라 IP 허용 목록을 환경에 바인딩할 때 미리 보기 옵션을 사용할 수 없었습니다.

* 존재하지 않는 실행을 위한 실행 세부 사항 페이지로 수동으로 탐색해도 오류가 표시되지 않고 끝없이 로드되는 화면만 표시됩니다.

* 최대 SSL 인증서 수에 도달했을 때 표시되는 오류 메시지가 표시되지 않습니다.

* 경우에 따라 개요 페이지의 파이프라인 카드에 표시된 릴리스 버전에서 차이가 있을 수 있습니다.

* 프로그램 추가 마법사에서 생성 후 이름을 변경할 수 없다고 잘못 명시했습니다.

* 경우에 따라 IP 허용 목록을 환경에 바인딩할 때 미리 보기 옵션을 사용할 수 없었습니다.

### 알려진 문제 {#known-issues}

Azul JDK를 사용하도록 전환하는 고객은 Azul JDK에 오류가 없는 모든 기존 애플리케이션이 컴파일되는 것은 아니라는 것을 알고 있어야 합니다. 전환하기 전에 로컬로 테스트하는 것이 좋습니다.

