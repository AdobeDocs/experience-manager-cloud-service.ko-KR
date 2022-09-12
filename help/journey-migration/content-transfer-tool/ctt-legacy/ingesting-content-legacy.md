---
title: Target에 컨텐츠 수집(이전)
description: 대상에 콘텐츠 수집
hide: true
hidefromtoc: true
exl-id: 326b3e98-5055-49b5-a005-63fd3ca35202
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 27%

---

# Target에 컨텐츠 수집(이전) {#ingesting-content}

## 컨텐츠 전송 도구의 수집 프로세스 {#ingestion-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.
>[!NOTE]
>선택적 사전 복사 단계를 실행하여 수집 단계를 크게 단축할 수 있습니다. 을(를) 참조하십시오. [AzCopy를 사용한 수집](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) 자세한 내용

1. 마이그레이션 세트 선택 **컨텐츠 전송** 페이지를 클릭하고 **수집** 수집

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. **마이그레이션 세트 수집** 대화 상자가 표시됩니다. 컨텐츠를 한 번에 작성자 인스턴스 또는 게시 인스턴스에 수집할 수 있습니다. 컨텐츠를 수집할 인스턴스를 선택합니다. 클릭 **수집** 수집 단계를 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >사전 복사로 섭취를 사용하는 경우(S3 또는 Azure Data Store용) 먼저 작성자 수집만 실행하는 것이 좋습니다. 이 경우 나중에 실행될 때 게시 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   >이 **수집하기 전에 클라우드 인스턴스에서 기존 컨텐츠를 지웁니다.** 옵션이 활성화되면 기존 저장소 전체를 삭제하고 컨텐츠를 수집할 새 저장소를 만듭니다. 즉, Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정합니다. 또한 **관리자** 그룹에 속해 있어야 합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   또한 **고객 지원 센터** 를 입력하여 티켓을 기록하십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)

   또한 [컨텐츠 전송 도구 사용에 대한 중요한 고려 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) 추가 정보

1. 수집이 완료되면 **작성자 수집** 업데이트 **완료됨**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png)

## 추가 수집 {#top-up-ingestion-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

수집 프로세스가 완료되면 추가 수집 방법을 사용하여 델타 컨텐츠를 사용할 수 있습니다. 아래 단계를 따르십시오.

1. 로 이동합니다 **컨텐츠 전송** 마법사를 열고 추가 수집을 수행할 마이그레이션 세트를 선택합니다. **수집**&#x200B;을 클릭하여 추가 추출을 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. **마이그레이션 세트 수집** 대화 상자가 표시됩니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >를 비활성화해야 합니다 **수집하기 전에 클라우드 인스턴스에서 기존 컨텐츠를 지웁니다.** 옵션을 선택합니다. 또한 **고객 지원 센터** 를 입력하여 티켓을 기록하십시오.

## 다음 단계 {#whats-next}

컨텐츠 전송 도구에서 컨텐츠를 Target에 섭취한 후 각 단계가 완료되면(추출 및 섭취) 로그를 보고 오류를 찾을 수 있습니다. 자세한 내용은 [마이그레이션 세트에 대한 로그 보기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) 추가 정보
