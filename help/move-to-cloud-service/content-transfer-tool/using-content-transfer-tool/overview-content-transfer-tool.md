---
title: 컨텐츠 전송 도구 개요
description: 컨텐츠 전송 도구 개요
exl-id: 4715937e-4c4c-4680-af15-016db4fe7db9
source-git-commit: bdcc5cfc229fd5b1fd1f70e37c7231ed3f727e72
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 74%

---

# 개요 {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="개요"
>abstract="컨텐츠 전송 도구는 Adobe에서 개발한 도구로, 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용할 수 있습니다. 이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#extraction-process" text="추출 프로세스"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#ingestion-process" text="수집 프로세스"

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

* 컨텐츠 전송 작업 중에 한 번에 최대 10개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
* 각 마이그레이션 세트의 이름은 고유해야 합니다.
* 마이그레이션 세트가 30일 이상 비활성 상태이면 자동으로 삭제됩니다.
* 마이그레이션 세트를 만들 때마다 특정 환경과 연결됩니다. 동일한 환경의 작성자 또는 게시 인스턴스로만 수집할 수 있습니다.


컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

추출 단계에서 기존 마이그레이션 세트를 ***추가***&#x200B;하려면 *덮어쓰기* 옵션을 비활성화해야 합니다. 자세한 내용은 [추출 추가](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process)를 참조하십시오.

수집 단계에서 델타 컨텐츠를 현재 컨텐츠 위에 적용하려면 *지우기* 옵션을 비활성화해야 합니다. 자세한 내용은 [수집 추가](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process)를 참조하십시오.


