---
title: 컨텐츠 전송 도구 개요
description: 컨텐츠 전송 도구 개요
exl-id: 4715937e-4c4c-4680-af15-016db4fe7db9
translation-type: tm+mt
source-git-commit: ca03de9095a5b85bd93edba93097356fbcd2e9c8
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 81%

---

# 개요 {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="개요"
>abstract="컨텐츠 전송 도구는 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용할 수 있는 Adobe에서 개발한 도구입니다. 이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#extraction-process" text="추출 프로세스"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#ingestion-process" text="통합 프로세스"

컨텐츠 전송 도구는 Adobe에서 개발한 도구로, 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM 클라우드 서비스 인스턴스로 이동하는 데 사용할 수 있습니다.

이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다.

컨텐츠 전송과 관련된 다음 두 가지 단계가 있습니다.

1. **추출**: 추출이란 소스 AEM 인스턴스에서 *마이그레이션 세트*&#x200B;라고 하는 임시 영역으로 컨텐츠를 추출하는 것입니다. *마이그레이션 세트*&#x200B;는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 컨텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다.

   자세한 내용은 [컨텐츠 전송의 추출 프로세스](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process)를 참조하십시오.

>[!NOTE]
>
> 추출 단계의 일부로 사용자 매핑 도구를 실행하는 것이 좋습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration)을 참조하십시오.

1. **수집**: 수집은 *마이그레이션 세트*&#x200B;의 컨텐츠를 대상 클라우드 서비스 인스턴스로 수집하는 것입니다.

   자세한 내용은 [컨텐츠 전송의 수집 프로세스](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process)를 참조하십시오.

*마이그레이션 세트*&#x200B;에는 다음 속성이 있습니다.

* 컨텐츠 전송 작업 중에 한 번에 최대 4개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
* 각 마이그레이션 세트의 이름은 고유해야 합니다.
* 마이그레이션 세트가 30일 이상 비활성 상태이면 자동으로 삭제됩니다.
* 마이그레이션 세트를 만들 때마다 특정 환경과 연결됩니다. 동일한 환경의 작성자 또는 게시 인스턴스로만 수집할 수 있습니다.

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

추출 단계에서 기존 마이그레이션 세트를 ***추가***&#x200B;하려면 *덮어쓰기* 옵션을 비활성화해야 합니다. 자세한 내용은 [추출 추가](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process)를 참조하십시오.

수집 단계에서 델타 컨텐츠를 현재 컨텐츠 위에 적용하려면 *지우기* 옵션을 비활성화해야 합니다. 자세한 내용은 [수집 추가](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process)를 참조하십시오.


## 지침 및 우수 사례 {#best-practices}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="지침 및 우수 사례"
>abstract="수정 정리 작업, 디스크 공간 고려 사항 등 컨텐츠 전송 툴을 사용하기 위한 지침과 모범 사례를 검토합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="컨텐츠 전송 도구 사용에 대한 중요 고려 사항"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="사용자 매핑 도구 사용에 대한 중요 고려 사항"

컨텐츠 전송 도구를 사용하기 위한 지침과 우수 사례를 이해하려면 아래 섹션을 따르십시오.

* 잠재적인 문제를 식별하고 저장소의 크기를 줄이기 위해 [소스](https://docs.adobe.com/content/help/ko-KR/experience-manager-65/deploying/deploying/revision-cleanup.html) 저장소에서 [수정 정리](https://helpx.adobe.com/kr/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) 및 **데이터 저장소 일관성 검사**&#x200B;를 실행하는 것이 좋습니다.

* AEM 클라우드 작성자 CDN(Content Delivery Network) 구성이 IP의 허용 목록을 포함하도록 구성된 경우 소스 환경과 AEM 클라우드 환경이 서로 통신할 수 있도록 소스 환경 IP가 허용 목록에도 추가되도록 해야 합니다.

* 수집 단계에서는 대상 AEM 클라우드 서비스 환경의 기존 저장소(작성자 또는 게시)가 완전히 삭제된 후 마이그레이션 세트 데이터로 업데이트되는 *지우기* 모드를 사용하여 수집을 실행하는 것이 좋습니다. 이 모드는 현재 컨텐츠 위에 마이그레이션 세트가 적용되는 지우지 않음 모드보다 훨씬 빠릅니다.

* 컨텐츠 전송 활동이 완료되면 클라우드 서비스 환경에서 컨텐츠가 성공적으로 렌더링되도록 하려면 클라우드 서비스 환경에 올바른 프로젝트 구조가 필요합니다.

* 컨텐츠 전송 도구를 실행하기 전에 소스 AEM 인스턴스의 `crx-quickstart` 하위 디렉토리에 디스크 공간이 충분한지 확인해야 합니다. 이는 컨텐츠 전송 도구가 나중에 마이그레이션 세트에 업로드된 저장소의 로컬 복사본을 만들기 때문입니다.
필요한 여유 디스크 공간을 계산하는 일반 공식은 다음과 같습니다.
   `data store size + node store size * 1.5`

   * *데이터 저장소 크기*: 컨텐츠 전송 도구는 실제 데이터 저장소가 더 큰 경우에도 64GB를 사용합니다.
   * *노드 저장소 크기*: 세그먼트 저장소 디렉토리 크기 또는 MongoDB 데이터베이스 크기입니다.
따라서 세그먼트 저장소 크기가 20GB인 경우 필요한 여유 디스크 공간은 94GB입니다.
