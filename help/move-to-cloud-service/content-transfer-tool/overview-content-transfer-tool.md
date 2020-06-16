---
title: 컨텐츠 전송 툴 개요
description: 컨텐츠 전송 툴 개요
translation-type: tm+mt
source-git-commit: bb5cedab9bb3f7413d323e21bb6112364a38b2bb
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---


# 개요 {#overview-content-transfer-tool}

컨텐츠 전송 도구는 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용할 수 있는 Adobe에서 개발한 도구입니다.

이 도구는 주도자(사용자 또는 그룹)도 자동으로 전송합니다.

컨텐츠 전송과 연관된 두 가지 단계가 있습니다.

1. **추출**:  추출을 참조하여 소스 AEM 인스턴스에서 *마이그레이션 세트라는 임시 영역으로 컨텐츠를 추출합니다*. 마이그레이션 세트 ** 는 소스 AEM 인스턴스와 Cloud Service AEM 인스턴스 간에 전송된 컨텐츠를 임시로 저장할 수 있도록 Adobe가 제공하는 클라우드 스토리지 영역입니다.

   자세한 내용은 [컨텐츠 전송의](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process) 추출 프로세스를 참조하십시오.

2. **통합**: 인제스트는 *마이그레이션 세트의 컨텐츠를 대상 Cloud Service 인스턴스로* 인제스트하는 것을 말합니다.

   자세한 [내용은 컨텐츠 전송의 처리](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process) 과정을 참조하십시오.

마이그레이션 *세트에는* 다음 속성이 있습니다.

* 컨텐츠 전송 작업 중에 한 번에 최대 4개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
* 각 마이그레이션 집합에는 고유한 이름이 있어야 합니다.
* 마이그레이션 세트가 30일 이상 비활성 상태이면 자동으로 삭제됩니다.
* 마이그레이션 세트를 만들 때마다 특정 환경과 연결됩니다. 동일한 환경의 작성자 또는 게시 인스턴스에만 인제스트할 수 있습니다.

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 상업을 지원하는 기능이 있습니다.

>[!NOTE]
> 초기 컨텐츠 전송 후, Cloud Service에서 라이브하기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 상업을 수행하는 것이 좋습니다.

추출 단계에서 기존 마이그레이션 세트를 ***맨 위로*** 설정하려면 *덮어쓰기* 옵션을 비활성화해야 합니다. 자세한 내용은 [위쪽](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process) 추출을 참조하십시오.

통합 단계에서 델타 컨텐츠를 현재 컨텐츠 위에 적용하려면 *지우기* 옵션을 비활성화해야 합니다. 자세한 내용은 [위쪽](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process) 질문을 참조하십시오.


## 지침 및 우수 사례 {#best-practices}

컨텐츠 전송 툴을 사용하기 위한 지침과 모범 사례를 이해하려면 아래 섹션을 따르십시오.

* 잠재적인 문제를 찾아 저장소에 있는 불필요한 쓰레기를 줄이기 위해 이전에 저장소에서 구성, 데이터 저장소 일관성 검사를 실행하는 것이 좋습니다.

* AEM Cloud CDN(Author Content Delivery Network) 구성이 IP의 허용 목록을 포함하도록 구성된 경우 소스 환경과 AEM Cloud 환경이 서로 통신할 수 있도록 소스 환경 IP도 허용 목록에 추가되는지 확인해야 합니다.

* 통합 단계에서는 대상 AEM Cloud Service 환경의 기존 저장소(작성자 또는 게시)가 완전히 삭제된 후 마이그레이션 세트 데이터로 업데이트되는 *지우기* 모드를 사용하여 질문을 실행하는 것이 좋습니다. 이 모드는 현재 컨텐츠 위에 마이그레이션 세트가 적용되는 닦이지 않는 모드보다 훨씬 빠릅니다.

* 컨텐츠 전송 활동이 완료되면 Cloud Service 환경에서 컨텐츠가 성공적으로 렌더링되도록 올바른 프로젝트 구조가 필요합니다.

* 콘텐츠 전송 도구를 실행하기 전에 소스 AEM 인스턴스의 하위 디렉터리에 디스크 공간이 충분한지 확인해야 `crx-quickstart` 합니다. 이는 컨텐츠 전송 도구가 나중에 마이그레이션 세트에 업로드된 저장소의 로컬 복사본을 만들기 때문입니다.
필요한 여유 디스크 공간을 계산하는 일반 공식은 다음과 같습니다.
   `data store size + node store size * 1.5`

   * *데이터 저장소 크기*: 컨텐츠 전송 도구는 실제 데이터 저장소가 더 큰 경우에도 64GB를 사용합니다.
   * *노드 저장소 크기*: 세그먼트 저장소 디렉터리 크기 또는 MongoDB 데이터베이스 크기입니다.
따라서 세그먼트 저장소 크기가 20GB인 경우 필요한 여유 디스크 공간은 94GB입니다.