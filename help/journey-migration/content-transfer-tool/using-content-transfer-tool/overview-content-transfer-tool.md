---
title: 컨텐츠 전송 도구 개요
description: 컨텐츠 전송 도구 개요
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: 8a55e011a93ce069f067192f58bd36399a39130b
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 44%

---

# 개요 {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="개요"
>abstract="컨텐츠 전송 도구는 Adobe에서 개발한 도구로, 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용할 수 있습니다. 이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html" text="지침 및 우수 사례"

컨텐츠 전송 도구는 Adobe에서 개발한 도구로, 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM 클라우드 서비스 인스턴스로 이동하는 데 사용할 수 있습니다.

이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다.

컨텐츠 전송 프로세스를 Cloud Acceleration Manager와 통합하는 새로운 버전의 컨텐츠 전송 도구를 사용할 수 있습니다. 이 새로운 버전으로 전환하여 제공되는 모든 이점을 활용하는 것이 좋습니다.

* 마이그레이션 세트를 한 번 추출하여 여러 환경에 동시에 수집하는 셀프 서비스 방법
* 향상된 로드 상태, 보호 기능 및 오류 처리를 통해 사용자 경험이 개선되었습니다
* 수집 로그는 지속되며 문제 해결에 항상 사용할 수 있습니다

새 버전을 사용하려면 도구에 주요 아키텍처 변경 사항이 있으므로 이전 버전의 컨텐츠 전송 도구를 제거해야 합니다.

>[!NOTE]
>
> 마이그레이션이 이미 진행 중인 경우 마이그레이션이 완료될 때까지 이전 버전의 CTT를 계속 사용할 수 있습니다. 이전 버전의 CTT와 관련된 설명서는 [이전 설명서](/help/journey-migration/content-transfer-tool/ctt-legacy/overview-content-transfer-tool-legacy.md).

## 컨텐츠 전송 도구의 단계 {#phases-content-transfer-tool}

컨텐츠 전송과 관련된 다음 두 가지 단계가 있습니다.

1. **추출**: 추출이란 소스 AEM 인스턴스에서 *마이그레이션 세트*&#x200B;라고 하는 임시 영역으로 컨텐츠를 추출하는 것입니다. *마이그레이션 세트*&#x200B;는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 컨텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다.

   자세한 내용은 [컨텐츠 전송의 추출 프로세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html)를 참조하십시오.

   >[!NOTE]
   > 추출 단계의 일부로 사용자 매핑 도구를 실행하는 것이 좋습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html) 자세한 내용

1. **수집**: 수집은 *마이그레이션 세트*&#x200B;의 컨텐츠를 대상 클라우드 서비스 인스턴스로 수집하는 것입니다.

   자세한 내용은 [컨텐츠 전송의 수집 프로세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html) 자세한 내용

## 마이그레이션 세트의 속성 {#attributes-migration-set}

마이그레이션 세트에는 다음 속성이 있습니다.

* 새 버전을 사용하면 Cloud Acceleration Manager에서 만든 프로젝트 내에 최대 5개의 마이그레이션 세트를 만들 수 있습니다.
* 각 마이그레이션 세트의 이름은 고유해야 합니다.

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

추출 단계에서 기존 마이그레이션 세트를 ***추가***&#x200B;하려면 *덮어쓰기* 옵션을 비활성화해야 합니다. 자세한 내용은 [추출 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en#top-up-extraction-process)를 참조하십시오.

수집 단계에서 델타 컨텐츠를 현재 컨텐츠 위에 적용하려면 *지우기* 옵션을 비활성화해야 합니다. 자세한 내용은 [수집 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en#top-up-ingestion-process)를 참조하십시오.

## 다음 단계 {#whats-next}

컨텐츠 전송 도구 및 이 도구를 설명하는 개요를 알고 나면 기존 컨텐츠를 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동하는 데 사용할 수 있습니다 [컨텐츠 전송 도구 사전 요구 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en).
