---
title: Cloud Service에 콘텐츠 수집
description: Cloud Acceleration Manager을 사용하여 마이그레이션 세트의 컨텐츠를 대상 Cloud Service 인스턴스로 수집하는 방법을 알아봅니다.
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
feature: Migration
role: Admin
source-git-commit: 766573bfeb5190d212e87b18331e41820ddd3e32
workflow-type: tm+mt
source-wordcount: '3137'
ht-degree: 11%

---

# Cloud Service에 콘텐츠 수집 {#ingesting-content}

## Cloud Acceleration Manager의 수집 프로세스 {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="콘텐츠 수집"
>abstract="수집은 마이그레이션 세트의 콘텐츠를 대상 Cloud Service 인스턴스로 수집하는 것입니다. 콘텐츠 전송 도구에는 이전 콘텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 콘텐츠 추가를 지원하는 기능이 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html#top-up-extraction-process" text="추가 추출"

Cloud Acceleration Manager을 사용하여 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.

1. Cloud Acceleration Manager으로 이동합니다. 프로젝트 카드를 클릭하고 컨텐츠 전송 카드를 클릭합니다. **수집 작업**(으)로 이동한 다음 **새 수집**&#x200B;을 클릭합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. 수집 체크리스트를 검토하고 모든 단계가 완료되었는지 확인합니다. 이러한 단계는 성공적인 수집을 보장하기 위해 필요합니다. 검사 목록이 완료된 경우에만 **다음** 단계로 진행합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. 수집을 만드는 데 필요한 정보를 제공합니다.

   * **마이그레이션 세트:** 추출된 데이터가 포함된 마이그레이션 세트를 Source으로 선택합니다.
      * 마이그레이션 세트는 장기간 사용하지 않으면 만료되므로 추출이 수행된 후 비교적 곧 수집이 발생할 것으로 예상됩니다. 자세한 내용은 [마이그레이션 세트 만료](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry)를 검토하십시오.

   >[!TIP]
   > 추출이 실행 중인 경우 대화 상자에 추출이 표시됩니다. 추출이 완료되면 자동으로 수집이 시작됩니다. 추출이 실패하거나 중지되면 수집 작업이 취소됩니다.

   * **대상:** 대상 환경을 선택합니다. 이 환경에서는 마이그레이션 세트의 콘텐츠가 수집됩니다.
      * 수집은 RDE(신속한 개발 환경) 또는 미리보기 유형의 대상을 지원하지 않으며, 사용자가 액세스할 수 있는 경우에도 가능한 대상 선택으로 표시되지 않습니다.
      * 마이그레이션 세트를 여러 대상에 동시에 수집할 수 있지만 대상은 한 번에 실행 중이거나 대기 중인 수집 하나만 대상으로 할 수 있습니다.

   * **계층:** 계층을 선택합니다. (작성자/Publish).
      * 소스가 `Author`인 경우 타겟의 `Author` 계층으로 수집하는 것이 좋습니다. 마찬가지로 소스가 `Publish`인 경우 타겟도 `Publish`이어야 합니다.

   >[!NOTE]
   > 대상 계층이 `Author`인 경우 작성자 인스턴스는 수집 기간 동안 종료되며 사용자(예: 작성자 또는 유지 관리를 수행하는 모든 사용자)가 사용할 수 없게 됩니다. 그 이유는 시스템을 보호하기 위해서이며, 손실되거나 수집 충돌을 야기할 수 있는 모든 변경 사항을 방지합니다. 팀이 이 사실을 알고 있는지 확인합니다. 또한 환경은 작성자 수집 중에 최대 절전 모드로 표시됩니다.

   * **지우기:** `Wipe` 값을 선택합니다.
      * **지우기** 옵션은 대상의 수집 시작점을 설정합니다. **지우기**&#x200B;를 사용하면 모든 콘텐츠를 포함하는 대상이 Cloud Manager에 지정된 AEM 버전으로 재설정됩니다. 활성화되지 않은 경우 대상은 현재 콘텐츠를 시작점으로 유지합니다.
      * 이 옵션은 콘텐츠 수집 방법에 영향을 주지 **않습니다**. 수집은 항상 컨텐츠 대체 전략을 사용하고 _컨텐츠 병합 전략을_&#x200B;하지 않습니다. 따라서 **지우기**&#x200B;와 **지우지 않음**&#x200B;의 경우 모두 마이그레이션 세트 수집이 대상에 있는 동일한 경로의 컨텐츠를 덮어씁니다. 예를 들어 마이그레이션 세트에 `/content/page1`이(가) 포함되어 있고 대상에 이미 `/content/page1/product1`이(가) 포함되어 있는 경우 수집은 전체 `page1` 경로와 `product1`을(를) 포함한 하위 페이지를 제거하고 마이그레이션 세트의 콘텐츠로 대체합니다. 즉, 유지해야 하는 콘텐츠가 포함된 대상에 대해 **지우지 않음** 수집을 수행할 때는 신중하게 계획해야 합니다.

   >[!IMPORTANT]
   > **지우기** 설정이 수집에 대해 활성화된 경우 대상 Cloud Service 인스턴스에 대한 사용자 권한을 포함하여 전체 기존 저장소를 재설정합니다. 이 재설정은 **관리자** 그룹에 추가된 관리자 사용자에 대해서도 적용되며 수집을 시작하려면 해당 사용자를 관리자 그룹에 다시 추가해야 합니다.

   * **사전 복사:** `Pre-copy` 값을 선택합니다.
      * 선택적 사전 복사 단계를 실행하여 수집 속도를 크게 높일 수 있습니다. 자세한 내용은 [AzCopy로 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy)을 참조하십시오.
      * S3 또는 Azure Data Store의 경우 사전 복사를 사용하여 수집하는 경우 먼저 `Author` 수집만 실행하는 것이 좋습니다. 이렇게 하면 나중에 실행될 때 `Publish` 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   > 대상 Cloud Service 작성자 서비스의 로컬 **AEM 관리자** 그룹에 속해 있는 경우에만 대상 환경에 대한 수집을 시작할 수 있습니다. 수집을 시작할 수 없는 경우 자세한 내용은 [수집을 시작할 수 없음](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion)을 참조하십시오.

1. 수집 선택 사항을 선택하면 예상 기간이 표시됩니다. 이는 유사한 수집의 내역 데이터를 기반으로 한 최적 예상 작업입니다.

   * 이 추정치는 추출의 &#39;Check Size&#39; 값이 수집되고 사용 가능한 경우에만 계산되어 표시됩니다.
   * 이 값은 예상치이며, 지능적으로 계산되지만 정확하게 간주해서는 안 됩니다. 다양한 요인들이 실제 기간을 변화시킬 수 있다.
   * 수집이 실행되는 동안 이 값은 수집의 &quot;**기간 보기**&quot; 작업을 통해 액세스하는 기간 대화 상자에서도 사용할 수 있습니다.

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_estimate"
>title="수집 기간 예측"
>abstract="소요 시간을 가늠할 수 있도록 특정 수집의 대략적인 지속 시간을 표시할 수 있습니다. 다만 정확성에는 한계가 있습니다."

![이미지](/help/journey-migration/content-transfer-tool/assets/estimate.png)

1. **수집**&#x200B;을 클릭합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. 그런 다음 수집 작업 목록 보기에서 수집을 모니터링하고 수집의 작업 메뉴를 사용하여 지속 시간을 보고 수집 진행 상황을 기록할 수 있습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. 수집 작업에 대한 자세한 내용을 보려면 행의 **(i)** 단추를 클릭하십시오. **..**&#x200B;을(를) 클릭한 다음 **기간 보기**&#x200B;를 클릭하여 실행 중이거나 완료된 수집 단계의 각 기간을 확인할 수 있습니다. 추출에서 얻은 정보도 수집되는 내용을 인식하는 것으로 표시됩니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23b.png)

## 추가 수집 {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="추가 수집"
>abstract="추가 기능을 사용하여 이전 콘텐츠 전송 활동 이후 수정된 콘텐츠를 이동합니다. 수집이 완료되면 로그에서 오류 또는 경고를 확인하십시오. 모든 오류는 보고된 문제를 처리하거나 Adobe 고객 지원 센터에 문의하여 즉시 해결해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html" text="로그 보기"

콘텐츠 전송 도구에는 마이그레이션 세트의 *추가*&#x200B;를 수행하여 차등 콘텐츠를 추출할 수 있는 기능이 있습니다. 이렇게 하면 모든 콘텐츠를 다시 추출할 필요 없이 이전 추출 후 변경된 콘텐츠만 포함하도록 마이그레이션 세트를 수정할 수 있습니다.

>[!NOTE]
>초기 컨텐츠 전송 후 Cloud Service으로 시작하기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다. 첫 번째 수집에 사전 복사 단계를 사용한 경우 후속 추가 수집에 대해 사전 복사를 건너뛸 수 있습니다(추가 마이그레이션 세트 크기가 200GB 미만인 경우). 그 이유는 전체 과정에 시간이 추가될 수 있기 때문이다.

일부 수집이 완료된 후 차등 콘텐츠를 수집하려면 [추가 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)을 실행한 다음 **지우기** 옵션 **사용 안 함**&#x200B;과 함께 수집 방법을 사용해야 합니다. 대상에 이미 있는 콘텐츠가 손실되지 않도록 위의 **지우기** 설명을 읽으십시오.

다음과 같이 수집 작업을 만들고 수집 중에 **지우기**&#x200B;가 비활성화되었는지 확인하십시오.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## 문제 해결 {#troubleshooting}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_troubleshooting"
>title="콘텐츠 수집 문제 해결"
>abstract="수집 로그 및 설명서를 참조하여 수집이 실패할 수 있는 일반적인 이유에 대한 솔루션을 찾고 문제를 해결하는 방법을 찾으십시오. 문제가 해결되면 수집을 다시 실행할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html" text="콘텐츠 전송 확인"

### CAM에서 마이그레이션 토큰을 검색할 수 없음 {#cam-unable-to-retrieve-the-migration-token}

대상 Cloud Service 환경에서 [Cloud Manager을 통해 IP 허용 목록을 설정](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)하는 등의 여러 가지 이유로 마이그레이션 토큰의 자동 검색이 실패할 수 있습니다. 이러한 시나리오에서는 수집을 시작할 때 다음과 같은 대화 상자가 표시됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

대화 상자에서 &quot;토큰 가져오기&quot; 링크를 클릭하여 마이그레이션 토큰을 수동으로 검색합니다. 토큰을 표시하는 다른 탭이 열립니다. 그런 다음 토큰을 복사하여 **마이그레이션 토큰 입력** 필드에 붙여넣을 수 있습니다. 이제 수집을 시작할 수 있습니다.

>[!NOTE]
>
>대상 Cloud Service 작성자 서비스의 로컬 **AEM 관리자** 그룹에 속하는 사용자는 토큰을 사용할 수 있습니다.

### 수집을 시작할 수 없음 {#unable-to-start-ingestion}

대상 Cloud Service 작성자 서비스의 로컬 **AEM 관리자** 그룹에 속해 있는 경우에만 대상 환경에 대한 수집을 시작할 수 있습니다. AEM 관리자 그룹에 속하지 않는 경우 수집을 시작하려고 하면 아래와 같은 오류가 표시됩니다. 관리자에게 사용자를 로컬 **AEM 관리자**&#x200B;에 추가하도록 요청하거나 토큰 자체를 요청하여 **마이그레이션 토큰 입력** 필드에 붙여넣을 수 있습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### 마이그레이션 서비스에 연결할 수 없음 {#unable-to-reach-migration-service}

수집이 요청되면 다음과 같은 메시지가 사용자에게 표시될 수 있습니다. &quot;대상 환경의 마이그레이션 서비스에 연결할 수 없습니다. 이 경우 나중에 다시 시도하거나 Adobe 지원 센터에 문의하십시오.&quot;

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

이 메시지는 Cloud Acceleration Manager이 수집을 시작하기 위해 대상 환경의 마이그레이션 서비스에 연결할 수 없음을 나타냅니다. 이러한 상황은 다양한 이유로 발생할 수 있습니다.

>[!NOTE]
> 
> 몇 가지 경우에 해당 토큰을 검색하는 것이 실제로 허용되지 않으므로 &quot;마이그레이션 토큰&quot; 필드가 표시됩니다. 수동으로 제공될 수 있게 함으로써, 이는 사용자가 어떠한 추가적인 도움 없이도 수집을 신속하게 시작할 수 있게 할 수 있다. 토큰을 제공하고 메시지가 여전히 나타나면, 토큰을 검색하는 것은 문제가 되지 않습니다.

* AEM as a Cloud Service은 환경 상태를 유지하고 있으며, 경우에 따라 다양한 일반적인 이유로 마이그레이션 서비스를 다시 시작해야 합니다. 서비스를 다시 시작하는 경우에는 해당 서비스에 연결할 수 없지만 결국 사용할 수 있습니다.
* 인스턴스에서 다른 프로세스가 실행되고 있을 수 있습니다. 예를 들어 [AEM 버전 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html)에서 업데이트를 적용하는 경우 시스템이 사용 중이고 마이그레이션 서비스를 정기적으로 사용할 수 없습니다. 해당 프로세스가 완료되면 수집 시작을 다시 시도할 수 있습니다.
* Cloud Manager을 통해 [IP 허용 목록이 적용](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)된 경우 Cloud Acceleration Manager이 마이그레이션 서비스에 도달하는 것이 차단됩니다. 주소가 동적이므로 수집에 IP 주소를 추가할 수 없습니다. 현재, 유일한 해결책은 수집 및 인덱싱 프로세스 동안 IP 허용 목록을 비활성화하는 것이다.
* 조사가 필요한 다른 이유가 있을 수 있다. 수집 또는 색인화에 계속 오류가 발생하면 Adobe 고객 지원 센터에 문의하십시오.

### AEM 버전 업데이트 및 수집 {#aem-version-updates-and-ingestions}

[AEM 버전 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html)는 최신 AEM as a Cloud Service 버전을 최신 상태로 유지하기 위해 환경에 자동으로 적용됩니다. 수집이 수행될 때 업데이트가 트리거되면 환경 손상 등 예측할 수 없는 결과가 발생할 수 있습니다.

대상 프로그램에 &quot;AEM 버전 업데이트&quot;가 온보딩되면 수집 프로세스는 시작하기 전에 해당 대기열을 비활성화하려고 시도합니다. 수집이 완료되면 버전 업데이트 프로그램 상태가 수집이 시작되기 전의 상태로 반환됩니다.

>[!NOTE]
>
> &quot;AEM 버전 업데이트&quot;를 비활성화하기 위해 더 이상 지원 티켓을 기록할 필요가 없습니다.

&quot;AEM 버전 업데이트&quot;가 활성 상태인 경우(즉, 업데이트가 실행 중이거나 실행 대기 중인 경우) 수집이 시작되지 않고 사용자 인터페이스에 다음 메시지가 표시됩니다. 업데이트가 완료되면 수집을 시작할 수 있습니다. Cloud Manager을 사용하여 프로그램의 파이프라인의 현재 상태를 볼 수 있습니다.

>[!NOTE]
>
> &quot;AEM 버전 업데이트&quot;는 환경의 파이프라인에서 실행되며 파이프라인이 지워질 때까지 기다립니다. 업데이트가 예상보다 오래 큐에 있는 경우 사용자 지정 워크플로우에 의도하지 않게 파이프라인이 잠겨 있지 않은지 확인하십시오.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_active.png)

### 고유성 제한 사항 위반으로 인한 추가 수집 실패 {#top-up-ingestion-failure-due-to-uniqueness-constraint-violation}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_uuid"
>title="고유성 제한 사항 위반"
>abstract="비삭제 수집 실패의 일반적인 원인은 노드 ID에서의 충돌입니다. 충돌하는 노드 중 하나만 존재할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html#top-up-ingestion-process" text="추가 수집"

[추가 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) 실패의 일반적인 원인은 노드 ID의 충돌입니다. 이 오류를 식별하려면 Cloud Acceleration Manager UI를 사용하여 수집 로그를 다운로드하고 다음과 같은 항목을 찾습니다.

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: 고유성 제약 조건이 값 a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content을 가진 속성 [jcr:uuid]을 위반했습니다.

AEM의 각 노드에는 고유한 UUID가 있어야 합니다. 이 오류는 수집되는 노드의 UUID가 대상 인스턴스의 다른 경로에 있는 노드의 UUID와 동일함을 나타냅니다. 이러한 상황은 다음 두 가지 이유로 발생할 수 있습니다.

* 노드가 소스에서 추출 및 후속 [추가 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) 사이에 이동됩니다.
   * _기억_: 추가 추출의 경우 노드가 더 이상 소스에 존재하지 않더라도 마이그레이션 세트에 계속 존재합니다.
* 대상의 노드가 수집과 후속 추가 수집 사이에서 이동됩니다.

이 충돌은 수동으로 해결해야 합니다. 콘텐츠에 익숙한 사용자는 두 노드 중 삭제할 노드를 참조하는 다른 콘텐츠를 염두에 두고 결정해야 합니다. 해결책은 불쾌한 노드 없이 다시 추가 추출이 수행될 것을 요구할 수 있다.

### 참조 노드 삭제 불가로 인한 추가 수집 실패 {#top-up-ingestion-failure-due-to-unable-to-delete-referenced-node}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_referenced_node"
>title="참조된 노드를 삭제할 수 없음"
>abstract="비삭제 수집 실패의 일반적인 원인은 대상 인스턴스의 특정 노드에 대한 버전 충돌입니다. 노드 버전을 수정해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html#top-up-ingestion-process" text="추가 수집"

[추가 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) 실패의 또 다른 일반적인 원인은 대상 인스턴스의 특정 노드에 대한 버전 충돌입니다. 이 오류를 식별하려면 Cloud Acceleration Manager UI를 사용하여 수집 로그를 다운로드하고 다음과 같은 항목을 찾습니다.

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakIntegrity0001: 참조된 노드를 삭제할 수 없음: 8a2289f4-b904-4bd0-8410-15e41e0976a8

대상의 노드가 수집과 후속 **비지우기** 수집 사이에 수정되어 새 버전이 만들어지는 경우 이 문제가 발생할 수 있습니다. 마이그레이션 세트가 &quot;버전 포함&quot;을 활성화한 상태로 추출된 경우 대상에 버전 내역 및 기타 콘텐츠에서 참조되는 최신 버전이 있으므로 충돌이 발생할 수 있습니다. 수정 버전 노드가 참조되기 때문에 수집 프로세스에서 수정 버전 노드를 삭제할 수 없습니다.

해결책은 불쾌한 노드 없이 다시 추가 추출이 수행될 것을 요구할 수 있다. 또는 문제가 되는 노드의 소규모 마이그레이션 세트를 만들지만 &quot;버전 포함&quot;은 비활성화되어 있습니다.

모범 사례에 따르면 버전을 포함하는 마이그레이션 세트를 사용하여 **지우지 않음** 수집을 실행해야 하는 경우 마이그레이션 여정이 완료될 때까지 대상의 콘텐츠를 가능한 한 적게 수정하는 것이 중요합니다. 그렇지 않으면 이러한 충돌이 발생할 수 있습니다.

### 대형 노드 속성 값으로 인한 수집 실패 {#ingestion-failure-due-to-large-node-property-values}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_bson"
>title="대형 노드 속성"
>abstract="수집 실패의 일반적인 원인은 노드 속성 값의 최대 크기를 초과하는 것입니다. 이러한 상황을 해결하려면 BPA 보고서와 관련된 문서를 포함한 설명서를 따르십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html" text="마이그레이션 사전 요구 사항"

MongoDB에 저장된 노드 속성 값은 16MB를 초과할 수 없습니다. 노드 값이 지원되는 크기를 초과하면 수집이 실패하고 로그에 다음 중 하나가 포함됩니다.

* `BSONObjectTooLarge` 오류 및 최대값을 초과하는 노드 지정 또는
* 최대 크기를 초과하는 유니코드 문자가 포함되어 있을 수 있는 노드가 있음을 나타내는 `BsonMaximumSizeExceededException` **

MongoDB 제한 사항입니다.

자세한 내용 및 모든 큰 노드를 찾는 데 도움이 될 수 있는 Oak 도구에 대한 링크는 [콘텐츠 전송 도구를 위한 필수 구성 요소](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md)의 `Node property value in MongoDB` 메모를 참조하십시오. 크기가 큰 모든 노드가 복구되면 추출 및 수집을 다시 실행합니다.

이러한 제한을 방지하려면 소스 AEM 인스턴스에서 [모범 사례 분석기](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md)를 실행하고 표시되는 결과, 특히 [&quot;지원되지 않는 저장소 구조&quot;(URS)](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/urs) 패턴을 검토하십시오.

>[!NOTE]
>
>[모범 사례 분석기](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md) 버전 2.1.50+는 최대 크기를 초과하는 유니코드 문자를 포함하는 큰 노드에 대해 보고합니다. 최신 버전을 실행 중인지 확인하십시오. 2.1.50 이전 버전의 BPA는 이러한 큰 노드를 식별하고 보고하지 않으며 위에서 언급한 사전 요구 사항 Oak 도구를 사용하여 개별적으로 검색해야 합니다.

### 예기치 않은 간헐적 오류로 인해 수집 실패 {#ingestion-failure-due-to-unexpected-intermittent-errors}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_intermittent_errors"
>title="예기치 않은 간헐적 오류"
>abstract="때때로 예기치 않은 간헐적인 다운스트림 서비스 오류가 발생할 수 있으며, 안타깝게도 유일한 요구는 수집을 다시 시도하는 것입니다."

때때로 예상치 못한 간헐적인 문제가 발생하면 실패한 수집에 도움이 될 수 있으며, 안타깝게도 수집을 다시 시도하는 것만이 유일한 요구입니다. 수집 로그를 조사하여 실패의 원인을 파악하고 다시 시도해야 하는 아래 나열된 오류와 일치하는지 확인합니다.

## MongoDB 문제 {#mongo-db-issues}

* `Atlas prescale timeout error` - 수집 단계에서 대상 클라우드 데이터베이스를 수집 중인 마이그레이션 세트 콘텐츠의 크기에 맞는 크기로 미리 조정하려고 합니다. 드물게 이 작업이 예상 기간 내에 완료되지 않습니다.
* `Exhausted mongo restore retries` - 수집된 마이그레이션 세트 컨텐츠의 로컬 덤프를 클라우드 데이터베이스로 복원하려고 시도했습니다. 이는 MongoDB의 전반적인 상태/네트워크 문제를 나타내며 몇 분 후에 해결되는 경우가 많습니다.

### 수집 취소됨 {#ingestion-rescinded}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_ingestion_troubleshooting_rescinded"
>title="수집 취소됨"
>abstract="수집 대기 중인 추출이 정상적으로 완료되지 않았습니다. 실행이 불가능하여 수집이 취소되었습니다."

실행 중인 추출을 소스 마이그레이션 세트로 사용하여 생성된 수집은 해당 추출이 성공할 때까지 잠시 기다렸다가 이 시점에서 정상적으로 시작됩니다. 추출이 실패하거나 중지되면 수집 및 색인 지정 작업이 시작되지 않고 취소됩니다. 이 경우 추출을 확인하여 실패한 이유를 확인하고 문제를 해결한 다음 추출을 다시 시작합니다. 고정 추출이 실행되면 새 수집을 예약할 수 있습니다.

### 수집을 다시 실행한 후 삭제된 자산이 없음

일반적으로 수집 사이에 있는 클라우드 환경 데이터는 수정하지 않는 것이 좋습니다.

Assets Touch UI를 사용하여 Cloud Service 대상에서 에셋이 삭제되면 노드 데이터는 삭제되지만 이미지가 있는 에셋 blob는 즉시 삭제되지 않습니다. 이 ID는 삭제하도록 표시되어 더 이상 UI에 표시되지 않지만 가비지 수집이 발생하고 BLOB가 제거될 때까지 데이터 저장소에 남아 있습니다.

이전에 마이그레이션된 자산이 삭제되고 가비지 수집기가 자산 삭제를 완료하기 전에 다음 수집이 실행되는 시나리오에서는 동일한 마이그레이션 세트를 수집해도 삭제된 자산은 복원되지 않습니다. 수집이 클라우드 환경에서 에셋을 확인하면 노드 데이터가 없습니다. 따라서 수집은 노드 데이터를 클라우드 환경에 복사합니다. 하지만 Blob 저장소를 확인하면 Blob가 있는 것을 확인하고 Blob 복사를 건너뜁니다. 이것이 Touch UI에서 에셋을 볼 때 메타데이터가 수집 후 표시되지만 이미지는 표시되지 않는 이유입니다. 마이그레이션 세트 및 콘텐츠 수집은 이 사례를 처리하도록 설계되지 않았습니다. 클라우드 환경에 새 콘텐츠를 추가하고 이전에 마이그레이션된 콘텐츠를 복원하지 않는 것을 목표로 합니다.

## 다음 단계 {#whats-next}

수집이 성공하면 AEM 색인화가 자동으로 시작됩니다. 자세한 내용은 [콘텐츠 마이그레이션 후 색인화](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/indexing-content.md)를 참조하십시오.

Cloud Service에 컨텐츠 수집을 완료하면 각 단계(추출 및 수집)의 로그를 보고 오류를 검색할 수 있습니다. 자세한 내용은 [마이그레이션 세트에 대한 로그 보기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/viewing-logs.md)를 참조하십시오.
