---
title: 대상에 콘텐츠 수집
description: 대상에 콘텐츠 수집
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 7e5a966693b139efa42111d8b6d675674516cfc6
workflow-type: tm+mt
source-wordcount: '1693'
ht-degree: 7%

---

# 대상에 콘텐츠 수집 {#ingesting-content}

## 컨텐츠 전송 도구에서 수집 프로세스 {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="컨텐츠 수집"
>abstract="수집은 마이그레이션 세트의 컨텐츠를 대상 Cloud Service 인스턴스로 수집하는 것입니다. 콘텐츠 전송 도구에는 이전 콘텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 콘텐츠 추가를 지원하는 기능이 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#top-up-ingestion-process" text="추가 수집"

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.
>[!NOTE]
>선택적 사전 복사 단계를 실행하여 수집 단계를 크게 가속화할 수 있습니다. 사전 복사 단계는 첫 번째 전체 추출 및 수집에 가장 효과적입니다. 을(를) 참조하십시오 [AzCopy로 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) 을 참조하십시오.

>[!NOTE]
>이 수집에 대한 지원 티켓을 기록하는 것을 잊지 않았습니까? 다음을 참조하십시오 [컨텐츠 전송 도구 사용 전 중요 고려 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) 을 비롯한 여러 고려 사항이 수집에 도움이 됩니다.

1. Cloud Acceleration Manager 로 이동합니다. 프로젝트 카드를 클릭하고 컨텐츠 전송 카드를 클릭합니다. 다음으로 이동 **수집 작업** 및 클릭 **새 수집**

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)


1. 수집 체크리스트를 검토하고 모든 단계가 완료되었는지 확인합니다. 이러한 단계는 수집을 성공적으로 수행하기 위해 필요한 단계입니다. 다음으로 진행할 수 있습니다. **다음** 체크리스트가 완료된 경우에만 단계를 수행합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. 새 수집을 만드는 데 필요한 정보를 제공합니다.

   * 추출된 데이터가 포함된 마이그레이션 세트를 소스로 선택합니다.
      * 마이그레이션 세트는 장기간 사용하지 않으면 만료되므로 추출이 수행된 후 비교적 곧 수집이 발생할 것으로 예상됩니다. 리뷰 [마이그레이션 세트 만료](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) 을 참조하십시오.
   * 대상 환경을 선택합니다. 여기에서 마이그레이션 세트의 콘텐츠를 수집할 수 있습니다. 계층을 선택합니다. (작성자/게시).

   >[!NOTE]
   >
   >소스가 작성자인 경우 타겟의 작성자 계층으로 수집하는 것이 좋습니다. 마찬가지로 소스가 Publish인 경우 타겟도 Publish여야 합니다.

   >[!NOTE]
   >
   >대상 계층이 `Author`, 작성자 인스턴스는 수집 기간 동안 종료되며 사용자(예: 작성자 또는 유지 관리 등을 수행하는 모든 사용자)는 사용할 수 없습니다. 이는 시스템을 보호하고 손실되거나 수집 충돌을 야기할 수 있는 변경 사항을 방지하기 위함입니다. 팀이 이 사실을 알고 있는지 확인하십시오. 또한 환경은 작성자 수집 중에 최대 절전 모드로 표시됩니다.

   >[!NOTE]
   >
   >선택적 사전 복사 단계를 실행하여 수집 단계를 크게 가속화할 수 있습니다. 을(를) 참조하십시오 [AzCopy로 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy) 을 참조하십시오.
   > 
   >S3 또는 Azure Data Store의 경우 사전 복사를 사용한 수집을 사용하는 경우 먼저 작성자 수집을 실행하는 것이 좋습니다. 이렇게 하면 나중에 실행할 때 게시 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   >
   >로컬에 속해 있는 경우에만 대상 환경으로의 수집을 시작할 수 있습니다 **AEM 관리자** 대상 Cloud Service 작성자 서비스의 그룹입니다. 수집을 시작할 수 없는 경우 다음을 참조하십시오. [수집을 시작할 수 없음](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) 을 참조하십시오.

   >[!IMPORTANT]
   >
   >다음과 같은 경우 **지우기** 수집 전에 활성화되며, 기존 저장소 전체를 삭제하고 컨텐츠를 수집할 새 저장소를 만듭니다. 즉, 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정이 재설정됩니다. 에 추가된 관리자 사용자에게도 마찬가지입니다. **관리자** 그룹입니다. 수집을 시작하려면 관리자 그룹에 다시 추가해야 합니다.

1. 클릭 **수집**

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. 그런 다음 수집 작업 목록 보기에서 수집 단계를 모니터링하고 수집의 작업 메뉴를 사용하여 수집이 진행될 때 로그를 볼 수 있습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. 수집이 완료되면 화면의 오른쪽 상단 모서리에 있는 (i) 버튼을 클릭하여 수집 작업에 대한 자세한 내용을 확인합니다.

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
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## 추가 수집 {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="추가 수집"
>abstract="이전 컨텐츠 전송 활동 이후 수정된 컨텐츠를 이동하려면 추가 기능을 사용합니다. 수집이 완료되면 로그에서 모든 오류/경고를 확인하십시오. 모든 오류는 보고된 문제를 처리하거나 Adobe 고객 지원 센터에 문의하여 즉시 해결해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en" text="로그 보기"

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 콘텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 콘텐츠 전송에 대한 콘텐츠 고정 기간을 단축하기 위해 자주 차등 콘텐츠 추가를 수행하는 것이 좋습니다. 첫 번째 전체 수집에 사전 복사 단계를 사용한 경우 전체 프로세스에 시간이 추가될 수 있으므로 후속 추가 수집에 대해 사전 복사를 건너뛸 수 있습니다(추가 마이그레이션 세트 크기가 200GB 미만인 경우).

수집 프로세스가 완료되면 델타 컨텐츠를 수집하려면 다음을 실행해야 합니다. [추가 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) 그런 다음 추가 수집 방법을 사용합니다.

새 수집 작업을 생성하여 다음을 확인할 수 있습니다. **지우기** 은 아래와 같이 수집 단계 중에 비활성화됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## 문제 해결 {#troubleshooting}

### CAM에서 마이그레이션 토큰을 검색할 수 없음 {#cam-unable-to-retrieve-the-migration-token}

다음을 포함한 다양한 이유로 마이그레이션 토큰의 자동 검색이 실패할 수 있습니다. [Cloud Manager를 통해 IP 허용 목록 설정](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) 대상 Cloud Service 환경에서. 이러한 시나리오에서는 수집을 시작하려고 할 때 다음 대화 상자가 표시됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

대화 상자에서 &quot;토큰 가져오기&quot; 링크를 클릭하여 마이그레이션 토큰을 수동으로 검색해야 합니다. 그러면 토큰을 표시하는 다른 탭이 열립니다. 그런 다음 토큰을 복사하여 **마이그레이션 토큰 입력** 필드. 이제 수집을 시작할 수 있습니다.

>[!NOTE]
>
>로컬 그룹에 속한 사용자가 토큰을 사용할 수 있습니다. **AEM 관리자** 대상 Cloud Service 작성자 서비스의 그룹입니다.

### 수집을 시작할 수 없음 {#unable-to-start-ingestion}

로컬에 속해 있는 경우에만 대상 환경으로의 수집을 시작할 수 있습니다 **AEM 관리자** 대상 Cloud Service 작성자 서비스의 그룹입니다. AEM 관리자 그룹에 속하지 않는 경우 수집을 시작하려고 하면 아래와 같이 오류가 표시됩니다. 관리자에게 사용자를 로컬 그룹에 추가하도록 요청할 수 있습니다. **AEM 관리자** 또는 토큰 자체를 요청하십시오. 그러면 토큰에 붙여 넣을 수 있습니다 **마이그레이션 토큰 입력** 필드.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### 마이그레이션 서비스에 연결할 수 없음 {#unable-to-reach-migration-service}

수집이 요청되면 다음과 같은 메시지가 사용자에게 표시될 수 있습니다. &quot;대상 환경의 마이그레이션 서비스에 현재 연결할 수 없습니다. 나중에 다시 시도하거나 Adobe 지원 센터에 문의하십시오.&quot;

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

이는 Cloud Acceleration Manager가 대상 환경의 마이그레이션 서비스에 도달하여 수집을 시작할 수 없음을 나타냅니다. 이는 여러 가지 이유로 인해 발생할 수 있습니다.

>[!NOTE]
> 
> 몇 가지 경우에 해당 토큰을 검색하는 것이 실제로 허용되지 않으므로 &quot;마이그레이션 토큰&quot; 필드가 표시됩니다. 수동으로 제공될 수 있게 함으로써, 이는 사용자가 어떠한 추가적인 도움 없이도 수집을 신속하게 시작할 수 있게 할 수 있다. 토큰을 제공하고 메시지가 계속 나타나는 경우 토큰을 검색하는 것은 문제가 되지 않았습니다.

* AEM은 환경 상태를 as a Cloud Service으로 유지하며, 경우에 따라 여러 가지 일반적인 이유로 마이그레이션 서비스를 다시 시작해야 할 수 있습니다. 서비스를 다시 시작하는 경우에는 연결할 수 없지만 곧 사용할 수 있습니다.
* 인스턴스에서 다른 프로세스가 실행되고 있을 수 있습니다. 예를 들어 Release Orchestrator가 업데이트를 적용하는 경우 시스템이 사용 중이고 마이그레이션 서비스를 정기적으로 사용할 수 없습니다. 따라서 스테이지나 프로덕션 인스턴스가 손상될 가능성이 있으므로 수집 중에 업데이트를 일시 중지하는 것이 매우 좋습니다.
* 다음과 같은 경우 [IP 허용 목록이 적용되었습니다.](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) cloud Manager를 통해 Cloud Acceleration Manager가 마이그레이션 서비스에 도달하는 것을 차단합니다. 주소가 매우 동적이므로 수집에 IP 주소를 추가할 수 없습니다. 현재 유일한 해결 방법은 수집이 실행되는 동안 IP 허용 목록을 비활성화하는 것입니다.
* 조사가 필요한 다른 이유가 있을 수 있다. 수집이 계속 실패하는 경우 Adobe 고객 지원 센터에 문의하십시오.

### Release Orchestrator를 통한 자동 업데이트가 여전히 활성화되어 있음

Release Orchestrator는 자동으로 업데이트를 적용하여 환경을 최신 상태로 자동 유지합니다. 수집이 수행될 때 업데이트가 트리거되면 환경 손상 등 예측할 수 없는 결과가 발생할 수 있습니다. 이는 수집을 시작하기 전에 지원 티켓을 기록해야 하는 이유 중 하나입니다(위의 &quot;메모&quot; 참조). 따라서 일시적으로 Release Orchestrator를 비활성화하도록 예약할 수 있습니다.

수집이 시작될 때 Release Orchestrator가 여전히 실행 중인 경우 UI에서 이 메시지를 표시합니다. 필드를 확인하고 버튼을 다시 눌러 위험을 감수하고 계속 진행하도록 선택할 수 있습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

### 추가 수집 실패

의 일반적인 원인 [추가 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) 실패는 노드 id의 충돌입니다. 이 오류를 식별하려면 Cloud Acceleration Manager UI를 사용하여 수집 로그를 다운로드하고 다음과 같은 항목을 찾습니다.

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: 고유성 제약 조건이 속성을 위반했습니다 [jcr:uuid] 값 a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

AEM의 각 노드에는 고유한 UUID가 있어야 합니다. 이 오류는 수집 중인 노드의 UUID가 대상 인스턴스의 다른 경로에 이미 존재하는 노드의 UUID와 동일함을 나타냅니다.
이는 노드가 소스에서 추출과 후속 추출 사이에서 이동되면 발생할 수 있습니다 [추가 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).
타겟의 노드가 수집과 후속 추가 수집 사이에서 이동된 경우에도 이 문제가 발생할 수 있습니다.

이 충돌은 수동으로 해결해야 합니다. 콘텐츠에 익숙한 사용자는 두 노드 중 삭제할 노드를 참조하는 다른 콘텐츠를 염두에 두고 결정해야 합니다. 해결책은 불쾌한 노드 없이 다시 추가 추출이 수행될 것을 요구할 수 있다.

## 다음 단계 {#whats-next}

Target에 컨텐츠 수집을 완료하면 각 단계(추출 및 수집)의 로그를 보고 오류를 검색할 수 있습니다. 다음을 참조하십시오 [마이그레이션 세트에 대한 로그 보기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) 자세히 알아보십시오.
