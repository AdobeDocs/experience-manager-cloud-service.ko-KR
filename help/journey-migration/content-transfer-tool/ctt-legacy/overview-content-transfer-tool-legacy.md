---
title: 콘텐츠 전송 도구 개요 (레거시)
description: 콘텐츠 전송 도구 개요
hide: true
hidefromtoc: true
exl-id: dd031580-e9d7-461e-8689-9bc3dbb2121b
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: ht
source-wordcount: '476'
ht-degree: 100%

---

# 콘텐츠 전송 도구 개요 (레거시) {#overview-content-transfer-tool}

콘텐츠 전송 도구는 Adobe에서 개발한 도구로, 기존 콘텐츠를 소스 AEM 인스턴스(온프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용할 수 있습니다.

이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다.

## 콘텐츠 전송 도구의 단계 {#phases-content-transfer-tool}

콘텐츠 전송과 관련된 다음 두 가지 단계가 있습니다.

1. **추출**: 추출이란 소스 AEM 인스턴스에서 *마이그레이션 세트*&#x200B;라고 하는 임시 영역으로 콘텐츠를 추출하는 것입니다. *마이그레이션 세트*&#x200B;는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 콘텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다.

   자세한 내용은 [콘텐츠 전송의 추출 프로세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html)를 참조하십시오.

   >[!NOTE]
   > 사용자 매핑 도구를 추출 단계의 일부로 실행하는 것이 좋습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html)을 참조하십시오.

1. **수집**: 수집은 *마이그레이션 세트*&#x200B;의 콘텐츠를 대상 클라우드 서비스 인스턴스로 수집하는 것입니다.

   자세한 내용은 [콘텐츠 전송의 수집 프로세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html)를 참조하십시오.

## 마이그레이션 세트 속성 {#attributes-migration-set}

마이그레이션 세트에는 다음 속성이 있습니다.

* 콘텐츠 전송 작업 중에 한 번에 최대 10개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
* 각 마이그레이션 세트의 이름은 고유해야 합니다.
* 마이그레이션 세트가 30일 이상 비활성 상태이면 자동으로 삭제됩니다.
* 마이그레이션 세트를 만들 때마다 특정 환경과 연결됩니다. 동일한 환경의 작성자 또는 게시 인스턴스로만 수집할 수 있습니다.


콘텐츠 전송 도구에는 이전 콘텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 콘텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 콘텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 콘텐츠 전송에 대한 콘텐츠 고정 기간을 단축하기 위해 자주 차등 콘텐츠 추가를 수행하는 것이 좋습니다.

추출 단계에서 기존 마이그레이션 세트를 ***추가***&#x200B;하려면 *덮어쓰기* 옵션을 비활성화해야 합니다. 자세한 내용은 [추출 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en#top-up-extraction-process)를 참조하십시오.

수집 단계에서 델타 콘텐츠를 현재 콘텐츠 위에 적용하려면 *지우기* 옵션을 비활성화해야 합니다. 자세한 내용은 [수집 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en#top-up-ingestion-process)를 참조하십시오.

## 다음 단계 {#whats-next}

콘텐츠 전송 도구에 대해 알아보고 이 도구를 설명하는 개요를 사용하여 기존 콘텐츠를 소스 AEM 인스턴스(온프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동한 경우 [콘텐츠 전송 도구 사전 요구 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en)을 검토해야 합니다.
