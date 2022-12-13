---
title: 대상에 콘텐츠 수집
description: 대상에 콘텐츠 수집
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: b40f8808bad50b759c8cdc669dbcf9ca0e8bbd31
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 11%

---

# 대상에 콘텐츠 수집 {#ingesting-content}

## 컨텐츠 전송 도구의 수집 프로세스 {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="컨텐츠 수집"
>abstract="수집은 마이그레이션 세트 의 컨텐츠를 대상 Cloud Service 인스턴스로 수집하는 것입니다. 컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="추가 수집"

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.
>[!NOTE]
>선택적 사전 복사 단계를 실행하여 수집 단계를 크게 단축할 수 있습니다. 사전 복사 단계는 첫 번째 전체 추출 및 통합에 가장 효과적입니다. 을(를) 참조하십시오. [AzCopy를 사용한 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) 자세한 내용

>[!NOTE]
>이 통합에 대한 지원 티켓을 기록해야 합니까? 자세한 내용은 [컨텐츠 전송 도구를 사용하기 전에 고려해야 할 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) 을 참조하십시오.

1. Cloud Acceleration Manager로 이동합니다. 프로젝트 카드를 클릭하고 컨텐츠 전송 카드를 클릭합니다. 다음으로 이동 **수집 작업** 을(를) 클릭합니다. **새 수집**

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)


1. 수집 확인 목록을 검토하고 모든 단계가 완료되었는지 확인합니다. 이는 성공적인 수집을 위해 필요한 단계입니다. 을(를) 진행할 수 있습니다. **다음** 검사 목록이 완료된 경우에만 단계입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. 새 수집을 만드는 데 필요한 정보를 제공합니다.

   * 소스로 추출한 마이그레이션 세트를 선택합니다
   * 대상 환경을 선택합니다. 여기서 마이그레이션 세트의 컨텐츠를 수집합니다. 계층을 선택합니다. (작성자/게시).

   >[!NOTE]
   >
   >소스가 작성자인 경우 타겟의 작성자 계층으로 가져오는 것이 좋습니다. 마찬가지로 소스가 게시인 경우 Target도 게시여야 합니다.

   >[!NOTE]
   >
   >대상 계층이 `Author`를 입력하면 수집 시간 중에 작성자 인스턴스가 종료되며 사용자(예: 작성자 또는 유지 관리를 수행하는 모든 사용자)는 사용할 수 없습니다. 시스템을 보호하고, 변경 사항이 손실되거나 수집 충돌이 발생할 수 있는 것을 방지하기 위한 것입니다. 팀이 이 사실을 알고 있는지 확인하십시오. 또한 환경은 작성 중에 최대 절전 모드로 전환됩니다.

   >[!NOTE]
   >
   >선택적 사전 복사 단계를 실행하여 수집 단계를 크게 단축할 수 있습니다. 을(를) 참조하십시오. [AzCopy를 사용한 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) 자세한 내용
   > 
   >사전 복사로 섭취를 사용하는 경우(S3 또는 Azure Data Store용) 먼저 작성자 수집만 실행하는 것이 좋습니다. 이 경우 나중에 실행될 때 게시 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   >
   >로컬 환경에 속하는 경우에만 대상 환경에 대한 수집을 시작할 수 있습니다 **AEM 관리자** 대상 Cloud Service 작성자 서비스의 그룹입니다. 수집을 시작할 수 없는 경우 다음을 참조하십시오. [수집을 시작할 수 없음](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) 자세한 내용

   >[!IMPORTANT]
   >
   >설정이 **지우기** 수집 전에 활성화되어 있으면 기존 저장소 전체가 삭제되고 컨텐츠를 수집할 새 저장소가 만들어집니다. 즉, Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정합니다. 또한 **관리자** 그룹에 속해 있어야 합니다. 수집을 시작하려면 관리자 그룹에 다시 추가해야 합니다.

1. 클릭 **수집**

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. 그런 다음 수집 작업 목록 보기에서 수집 단계를 모니터링하고 수집 작업 메뉴를 사용하여 처리가 진행될 때 로그를 볼 수 있습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. 수집이 완료되면 화면 오른쪽 위의 (i) 버튼을 클릭하여 수집 작업에 대한 자세한 정보를 얻습니다.

<!-- Alexandru: hiding temporarily, until it's reviewed 

1. The **Migration Set ingestion** dialog box displays. Content can be ingested to either Author instance or Publish instance at a time. Select the instance to ingest content to. Click on **Ingest** to start the ingestion phase. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >If ingesting with pre-copy is used (for S3 or Azure Data Store), it is recommended to run Author ingestion first alone. This will speed up the Publish ingestion when it is run later. 

   >[!IMPORTANT]
   >When the **Wipe existing content on Cloud instance before ingestion** option is enabled, it deletes the entire existing repository and creates a new repository to ingest content into. This means that it resets all settings including permissions on the target Cloud Service instance. This is also true for an admin user added to the **administrators** group.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Additionally, click on **Customer Care** to log a ticket, as shown in the figure below. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## 추가 수집 {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="추가 수집"
>abstract="이전 컨텐츠 전송 활동 이후 수정된 컨텐츠를 이동하려면 상단 기능을 사용하십시오. 수집이 완료되면 로그에서 오류/경고를 확인합니다. 오류는 보고된 문제를 처리하거나 Adobe 고객 지원 센터에 문의하여 즉시 해결되어야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en" text="로그 보기"

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다. 첫 번째 전체 처리에 사전 복사 단계를 사용한 경우, 전체 프로세스에 시간을 추가할 수 있으므로 후속 추가 수집 시 사전 복사를 건너뛸 수 있습니다(추가 마이그레이션 세트 크기가 200GB 미만인 경우).

수집 프로세스가 완료되면 델타 컨텐츠를 수집하려면 다음을 실행해야 합니다. [추가 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) 그런 다음 추가 수집 방법을 사용합니다.

이렇게 하려면 새 수집 작업을 만들고 다음을 확인합니다 **지우기** 은 아래와 같이 수집 단계 동안 비활성화됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## 문제 해결 {#troubleshooting}

### CAM에서 마이그레이션 토큰을 검색할 수 없습니다. {#cam-unable-to-retrieve-the-migration-token}

사용자를 포함하여 다양한 이유로 마이그레이션 토큰의 자동 검색이 실패할 수 있습니다 [Cloud Manager를 통해 IP 허용 목록 설정](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) 설정 및 해제 할 수 있습니다. 이러한 시나리오에서는 수집을 시작하려고 하면 다음 대화 상자가 표시됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

대화 상자에서 &quot;토큰 가져오기&quot; 링크를 클릭하여 마이그레이션 토큰을 수동으로 검색해야 합니다. 그러면 토큰이 표시되는 다른 탭이 열립니다. 그런 다음 토큰을 복사하여 **마이그레이션 토큰 입력** 필드. 이제 수집을 시작할 수 있습니다.

>[!NOTE]
>
>토큰은 로컬 그룹에 속하는 사용자가 사용할 수 있습니다 **AEM 관리자** 대상 Cloud Service 작성자 서비스의 그룹입니다.

### 수집을 시작할 수 없음 {#unable-to-start-ingestion}

로컬 환경에 속하는 경우에만 대상 환경에 대한 수집을 시작할 수 있습니다 **AEM 관리자** 대상 Cloud Service 작성자 서비스의 그룹입니다. AEM 관리자 그룹에 속하지 않는 경우 수집을 시작하려고 하면 아래에 표시된 오류가 표시됩니다. 관리자에게 사용자를 로컬 그룹에 추가하도록 요청할 수 있습니다 **AEM 관리자** 토큰에 붙여넣을 수 있는 토큰 자체를 요청하거나 **마이그레이션 토큰 입력** 필드.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Release Orchestrator를 통한 자동 업데이트가 계속 활성화되어 있습니다.

Release Orchestrator는 업데이트를 자동으로 적용하여 환경을 최신 상태로 자동으로 유지합니다. 수집이 수행될 때 업데이트가 트리거되면 환경의 손상을 포함하여 예기치 않은 결과가 발생할 수 있습니다. 이는 수집을 시작하기 전에 지원 티켓을 기록해야 하는 이유 중 하나입니다(위의 &quot;참고&quot; 참조). 이때 Release Orchestrator를 일시적으로 비활성화할 수 있습니다.

수집을 시작할 때 Release Orchestrator가 여전히 실행 중인 경우 UI에 이 오류 메시지가 표시됩니다. 위험을 감수하면서 계속 진행할 수도 있습니다. 필드를 확인하고 버튼을 다시 누르면 됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

## 다음 단계 {#whats-next}

Target으로 컨텐츠 섭취를 완료하면 각 단계의 로그(추출 및 수집)를 보고 오류를 찾을 수 있습니다. 자세한 내용은 [마이그레이션 세트에 대한 로그 보기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) 추가 정보
