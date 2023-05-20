---
title: 콘텐츠를 Target으로 수집(이전)
description: 대상에 콘텐츠 수집
hide: true
hidefromtoc: true
exl-id: 326b3e98-5055-49b5-a005-63fd3ca35202
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 27%

---

# 콘텐츠를 Target으로 수집(이전) {#ingesting-content}

## 컨텐츠 전송 도구에서 수집 프로세스 {#ingestion-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.
>[!NOTE]
>선택적 사전 복사 단계를 실행하여 수집 단계를 크게 가속화할 수 있습니다. 을(를) 참조하십시오 [AzCopy로 수집](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) 을 참조하십시오.

1. 다음에서 마이그레이션 세트 선택 **컨텐츠 전송** 페이지 및 클릭 **수집** 수집을 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. **마이그레이션 세트 수집** 대화 상자가 표시됩니다. 한 번에 작성자 인스턴스 또는 게시 인스턴스로 콘텐츠를 수집할 수 있습니다. 컨텐츠를 수집할 인스턴스를 선택합니다. 클릭 **수집** 수집 단계를 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >S3 또는 Azure Data Store의 경우 사전 복사를 사용한 수집을 사용하는 경우 먼저 작성자 수집을 실행하는 것이 좋습니다. 이렇게 하면 나중에 실행할 때 게시 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   >다음의 경우 **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 이 옵션을 활성화하면 기존 저장소 전체가 삭제되고 컨텐츠를 수집할 새 저장소가 만들어집니다. 즉, 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정이 재설정됩니다. 에 추가된 관리자 사용자에게도 마찬가지입니다. **관리자** 그룹입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   또한 을(를) 클릭합니다 **고객 지원 센터** 아래 그림과 같이 티켓을 기록합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)

   또한 다음을 참조하십시오. [컨텐츠 전송 도구 사용에 대한 중요한 고려 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) 자세히 알아보십시오.

1. 수집이 완료되면 상태는 다음과 같습니다. **작성자 수집** 에 대한 업데이트 **완료됨**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png)

## 추가 수집 {#top-up-ingestion-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

수집 프로세스가 완료되면 추가 수집 방법을 사용하여 델타 컨텐츠를 사용할 수 있습니다. 아래 단계를 따르십시오.

1. 다음 위치로 이동 **컨텐츠 전송** 추가 수집을 수행할 마이그레이션 세트를 마법사에서 선택하고 선택합니다. **수집**&#x200B;을 클릭하여 추가 추출을 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. **마이그레이션 세트 수집** 대화 상자가 표시됩니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >다음을 비활성화해야 합니다. **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 옵션을 사용하여 이전 수집 활동에서 기존 컨텐츠를 삭제하지 못하도록 합니다. 또한 을(를) 클릭합니다 **고객 지원 센터** 이전 그림과 같이 티켓을 기록합니다.

## 다음 단계 {#whats-next}

컨텐츠 전송 도구에서 Target으로 컨텐츠 수집에 대해 학습한 후에는 각 단계(추출 및 수집)가 완료되면 로그를 보고 오류를 검색할 수 있습니다. 다음을 참조하십시오 [마이그레이션 세트에 대한 로그 보기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) 자세히 알아보십시오.
