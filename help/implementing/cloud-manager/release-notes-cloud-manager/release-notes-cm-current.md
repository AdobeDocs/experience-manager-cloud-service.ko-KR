---
title: AEM as a Cloud Service 릴리스 2021.11.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.11.0의 Cloud Manager 릴리스 노트
feature: Release Information
source-git-commit: 14042b45b14f2c5575fc96979579bb0aaffc9a17
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 2%

---

# Adobe Experience Manager as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service Manager에 대한 릴리스 노트를 간략하게 설명합니다2021.11.0.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR).

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.11.0의 Cloud Manager 릴리스 날짜는 2021년 11월 4일입니다.
다음 릴리스는 2021년 12월 16일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new}

* 이제 사용자는 새로운 프런트 엔드 파이프라인을 활용하여 프런트 엔드 코드만 신속하게 배포할 수 있습니다. 자세한 내용은 [Cloud Manager 프런트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) 추가 정보

   >[!IMPORTANT]
   >AEM 버전을 사용해야 합니다. `2021.10.5933.20211012T154732Z` 최신 프런트 엔드 파이프라인을 활용합니다.

* 코드 품질 파이프라인 기간은 전체 AEM 이미지를 작성하지 않고도 보다 효율적인 방식으로 코드 분석을 수행하므로 크게 줄어듭니다. 이 변경 사항은 릴리스 후 몇 주에 걸쳐 점진적으로 롤아웃됩니다.

* 이제 Git 커밋 ID가 파이프라인 실행 세부 사항에 표시되므로 빌드된 코드를 쉽게 추적할 수 있습니다.

* 이제 공개적으로 노출된 API를 통해 프로그램 생성을 사용할 수 있습니다.

* 이제 공개적으로 노출된 API를 통해 환경 만들기를 사용할 수 있습니다.

* 다음 `x-request-id` 이제 응답 헤더가 의 API Playground에 표시됩니다. [www.adobe.io](https://www.adobe.io/). 이 헤더는 문제 해결을 위해 고객 지원 문제를 제출할 때 유용합니다.

* 사용자는 파이프라인이 없는 파이프라인 카드에 적절한 지침이 제공됩니다.

* 이제 연관된 세부 사항과 함께 파이프라인 및 코드 실행과 같은 활동을 볼 수 있는 새로운 활동 페이지를 사용할 수 있습니다. 시간이 지나면서 이 페이지에 나열된 활동은 제공된 세부 정보와 함께 범위가 확장됩니다.

* 이제 세부 사항 요약을 쉽게 볼 수 있도록 마우스로 가리키면 상태 팝오버가 있는 새 파이프라인 페이지를 사용할 수 있습니다. 파이프라인 실행은 연관된 세부 정보와 함께 볼 수 있습니다.

* 이제 파이프라인 편집 API에서 배포 단계에서 사용되는 환경 변경을 지원합니다.

* 큰 패키지에 대해 OakPal 검색 프로세스의 최적화가 도입되었습니다.

* 이제 품질 문제 CSV 파일에 각 품질 문제에 대한 타임스탬프가 포함됩니다.

### 버그 수정 {#bug-fixes}

* 특정 비정형 빌드 구성은 빌드 컨테이너를 시작 및 중지할 때 외부 네트워크 I/O를 발생시킨 파이프라인의 Maven 아티팩트 캐시에 불필요한 파일이 저장되었습니다.

* 배포 단계가 없는 경우 파이프라인 PATCH API가 실패합니다.

* 다음 `ClientlibProxyResourceCheck` 일반적인 기본 경로가 있는 클라이언트 라이브러리가 있을 때 품질 규칙이 긍정 오류(false positive)를 생성하는 것이었습니다.

* 최대 저장소 수에 도달했을 때 오류 메시지에 오류 이유를 지정하지 않았습니다.

* 드문 경우이지만 특정 응답 코드를 잘못 처리하여 파이프라인이 실패했습니다.

