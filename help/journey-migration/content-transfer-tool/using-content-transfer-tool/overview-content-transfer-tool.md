---
title: 콘텐츠 전송 도구 개요
description: 컨텐츠 전송 도구를 사용하여 컨텐츠를 온-프레미스 AEM 인스턴스에서 AEM as a Cloud Service으로 전송하는 방법에 대해 알아봅니다
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 52%

---

# 개요 {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="개요"
>abstract="콘텐츠 전송 도구는 Adobe에서 개발한 도구로, 기존 콘텐츠를 소스 AEM 인스턴스(온프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 마이그레이션하는 데 사용할 수 있습니다. 이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html" text="지침 및 모범 사례"

컨텐츠 전송 도구는 Adobe에서 개발한 도구로, 소스 AEM 인스턴스(온-프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 기존 컨텐츠를 마이그레이션하는 데 사용할 수 있습니다.

이 도구는 주체(사용자 또는 그룹)도 자동으로 전송합니다.  다음을 참조하십시오 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) 추가 정보.

컨텐츠 전송 도구는 컨텐츠 전송 프로세스를 Cloud Acceleration Manager와 통합합니다. 이를 통해 사용자는 다음과 같은 이점을 얻을 수 있습니다.

* 마이그레이션 세트를 한 번 추출하여 동시에 여러 환경에서 수집하는 셀프서비스 방식
* 로드 상태, 보호 기능 및 오류 처리를 개선하여 사용자 경험 개선
* 수집 로그는 유지되고 문제 해결에 항시 사용 가능합니다.
* 검증 및 주도자 마이그레이션 보고서를 검증에 사용할 수 있습니다.

## 콘텐츠 전송 도구의 단계 {#phases-content-transfer-tool}

콘텐츠 전송과 관련된 다음 두 가지 단계가 있습니다.

1. **추출**: 추출이란 소스 AEM 인스턴스에서 *마이그레이션 세트*&#x200B;라고 하는 임시 영역으로 콘텐츠를 추출하는 것입니다. *마이그레이션 세트*&#x200B;는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 콘텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다.

   다음을 참조하십시오 [컨텐츠 전송의 추출 프로세스](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) 을 참조하십시오.

   >[!NOTE]
   >사용자 매핑은 이제 작성자에서 추출 단계의 일부로 자동으로 실행됩니다(그러나 선택적으로 작성자에서 비활성화하거나 게시할 때 활성화할 수 있음). 다음을 참조하십시오 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) 을 참조하십시오.

1. **수집**: 수집은 *마이그레이션 세트*&#x200B;의 콘텐츠를 대상 클라우드 서비스 인스턴스로 수집하는 것입니다.

   자세한 내용은 [콘텐츠 전송의 수집 프로세스](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)를 참조하십시오.

## 마이그레이션 세트 속성 {#attributes-migration-set}

마이그레이션 세트에는 다음 속성이 있습니다.

* 새 버전을 사용하면 Cloud Acceleration Manager에서 만든 프로젝트 내에 최대 20개의 마이그레이션 세트를 만들 수 있습니다.
* 각 마이그레이션 세트의 이름은 고유해야 합니다.

콘텐츠 전송 도구에는 이전 콘텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 콘텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 콘텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 콘텐츠 전송에 대한 콘텐츠 고정 기간을 단축하기 위해 자주 차등 콘텐츠 추가를 수행하는 것이 좋습니다.

추출 단계에서 기존 마이그레이션 세트를 ***추가***&#x200B;하려면 *덮어쓰기* 옵션을 비활성화해야 합니다. 다음을 참조하십시오 [추가 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) 을 참조하십시오.

수집 단계에서 델타 콘텐츠를 현재 콘텐츠 위에 적용하려면 *지우기* 옵션을 비활성화해야 합니다. 다음을 참조하십시오 [추가 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) 을 참조하십시오.

## 마이그레이션 세트 만료 {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="마이그레이션 세트 만료"
>abstract="마이그레이션 세트 만료에 대해 알아보십시오."

모든 마이그레이션 세트는 약 90일 동안 비활성 상태가 지속되면 만료됩니다. 일정 기간 동안 프로젝트 카드 및 마이그레이션 작업 테이블 행에 표시기가 표시되면 마이그레이션 세트가 만료되어 해당 데이터를 더 이상 사용할 수 없게 됩니다. 다음과 같이 설정된 마이그레이션에 따라 쉽게 만료 시간을 연장할 수 있습니다.

* 설명 편집
* 추출 키를 가져오는 중
* 추출 수행
* 수집 수행

마이그레이션 세트 행에서 마이그레이션 세트의 만료를 모니터링할 수 있습니다. 마이그레이션 세트가 만료 날짜에 도달하고 있다는 유용한 시각적 표시기도 프로젝트 카드를 추가했습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)


## 다음 단계 {#whats-next}

콘텐츠 전송 도구에 대해 알아보고 이 도구를 설명하는 개요를 사용하여 기존 콘텐츠를 소스 AEM 인스턴스(온프레미스 또는 AMS)에서 대상 AEM Cloud Service 인스턴스로 이동한 경우 [콘텐츠 전송 도구 사전 요구 사항](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md)을 검토해야 합니다.
