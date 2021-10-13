---
title: 컨텐츠 전송 도구 사용
description: 컨텐츠 전송 도구 사용
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: 04494e116fcdd38622ae2d4434d7cf8e4034d5aa
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 52%

---

# 컨텐츠 전송 도구 사용 {#using-content-transfer-tool}

## 컨텐츠 전송의 추출 프로세스 {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="컨텐츠 추출"
>abstract="추출이란 소스 AEM 인스턴스에서 마이그레이션 세트라는 임시 영역으로 컨텐츠를 추출하는 것입니다. 마이그레이션 세트는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 컨텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="추출 추가"

컨텐츠 전송 도구에서 마이그레이션 세트를 추출하려면 아래 단계를 따르십시오.
>[!NOTE]
>Amazon S3 또는 Azure 데이터 저장소가 데이터 저장소 유형으로 사용되는 경우 선택적 사전 복사 단계를 실행하여 추출 단계를 크게 단축할 수 있습니다. 이렇게 하려면 추출을 실행하기 전에 `azcopy.config` 파일을 구성해야 합니다. 자세한 내용은 [큰 컨텐츠 저장소 처리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 를 참조하십시오.

1. *개요* 페이지에서 마이그레이션 세트를 선택하고 **추출**&#x200B;을 클릭하여 추출을 시작합니다. **마이그레이션 세트 추출** 대화 상자가 표시되고 **추출**&#x200B;을 클릭하여 추출 단계를 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >추출 단계 중에 스테이징 컨테이너를 덮어쓰는 옵션이 제공됩니다.


1. 이제 **EXTRACTION** 필드에 **RUNNING** 상태가 표시되어 추출이 진행 중임을 나타냅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   추출이 완료되면 마이그레이션 세트의 상태가 **완료됨**&#x200B;으로 업데이트되고 *녹색* 클라우드 아이콘이 **정보**&#x200B;필드 아래에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >UI에는 30초마다 개요 페이지를 다시 로드하는 자동 재로드 기능이 있습니다.
   >추출 단계가 시작되면 *60초* 후 쓰기 잠금이 만들어지고 해제됩니다. 따라서 추출이 중지된 경우 다시 추출을 시작하기 전에 잠금이 해제될 때까지 잠시 기다려야 합니다.

### 추가 추출 {#top-up-extraction-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.
>또한 기존 컨텐츠의 컨텐츠 구조는 초기 추출을 수행한 때부터 추가 추출을 실행할 때까지의 변경되지 않는 것이 중요합니다. 초기 추출 후 구조가 변경된 컨텐츠에서는 추가를 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

추출 프로세스가 완료되면 추가 추출 방법을 사용하여 델타 컨텐츠를 전송할 수 있습니다. 아래 단계를 따르십시오.

1. *개요* 페이지로 이동하고 추가 추출을 수행할 마이그레이션 세트를 선택합니다. **추출**&#x200B;을 클릭하여 추가 추출을 시작합니다. **마이그레이션 세트 추출** 대화 상자가 표시됩니다.

   >[!IMPORTANT]
   >
   >**추출 중에 스테이징 컨테이너 덮어쓰기** 옵션을 비활성화해야 합니다.
   >
   >![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

## 컨텐츠 전송의 수집 프로세스 {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="컨텐츠 수집"
>abstract="수집은 마이그레이션 세트 의 컨텐츠를 대상 Cloud Service 인스턴스로 수집하는 것입니다. 컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="추가 수집"

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.
>[!NOTE]
>Amazon S3 또는 Azure Data Store가 데이터 저장소 유형으로 사용되는 경우 선택적 사전 복사 단계를 실행하여 수집 단계를 크게 단축할 수 있습니다. 자세한 내용은 [AzCopy를 사용하여 수집](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy)을 참조하십시오.

1. *개요* 페이지에서 마이그레이션 세트를 선택하고 **수집**&#x200B;을 클릭하여 수집을 시작합니다. **마이그레이션 세트 수집** 대화 상자가 표시됩니다. 컨텐츠를 한 번에 작성자 인스턴스 또는 게시 인스턴스에 수집할 수 있습니다. 컨텐츠를 수집할 인스턴스를 선택합니다. **수집**&#x200B;을 클릭하여 수집 단계를 시작합니다.

   >[!IMPORTANT]
   >사전 복사로 섭취를 사용하는 경우(S3 또는 Azure Data Store용) 먼저 작성자 수집만 실행하는 것이 좋습니다. 이 경우 나중에 실행될 때 게시 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   >**수집** 옵션이 활성화되기 전에 클라우드 인스턴스에서 기존 컨텐츠를 지우는 경우 기존 저장소 전체를 삭제하고 컨텐츠를 수집 할 새 저장소를 만듭니다. 즉, Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정합니다. **administrators** 그룹에 추가된 관리자 사용자에게도 적용됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-03.png)

   또한 **고객 지원 센터**&#x200B;를 클릭하여 위의 그림과 같이 티켓을 기록합니다. 또한 자세한 내용은 [컨텐츠 전송 도구 사용에 대한 중요한 고려 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs)을 참조하십시오.

1. 수집이 완료되면 상태가 **FINISHED**&#x200B;로 업데이트됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

### 추가 수집 {#top-up-ingestion-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

수집 프로세스가 완료되면 추가 수집 방법을 사용하여 델타 컨텐츠를 사용할 수 있습니다. 아래 단계를 따르십시오.

1. *개요* 페이지로 이동하고 추가 수집을 수행할 마이그레이션 세트를 선택합니다. **수집**&#x200B;을 클릭하여 추가 추출을 시작합니다. **마이그레이션 세트 수집** 대화 상자가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-02.png)

   >[!IMPORTANT]
   >이전 수집 활동에서 기존 컨텐츠를 삭제하지 않으려면 먼저 클라우드 인스턴스에서 기존 컨텐츠를 지우는 **옵션을 비활성화해야 합니다.** 또한 **고객 지원 센터**&#x200B;를 클릭하여 이전 그림과 같이 티켓을 기록합니다.


### 마이그레이션 세트에 대한 로그 보기 {#viewing-logs-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="로그 보기"
>abstract="수집 추출이 완료되면 로그에서 오류/경고를 확인합니다. 오류는 보고된 문제를 처리하거나 Adobe 지원에 연락하여 즉시 해결해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="문제 해결"
>additional-url="https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/support-for-experience-cloud.ug.html" text="Adobe 지원에 문의"

각 단계(추출 및 수집)가 완료되면 로그를 확인하고 오류를 찾습니다.  오류는 보고된 문제를 처리하거나 Adobe 지원에 연락하여 즉시 해결해야 합니다.

*개요* 페이지에서 기존 마이그레이션 세트에 대한 로그를 볼 수 있습니다.
아래 단계를 따르십시오.

1. *개요* 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 표시줄에서 **로그 보기**&#x200B;를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. **로그** 대화 상자가 표시됩니다. **추출 로그**&#x200B;를 클릭하여 새 탭에서 로그를 확인합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)
또는,

   *개요* 화면에서 마이그레이션 세트에 대한 로그를 볼 수도 있습니다. 마이그레이션 세트를 선택하고 **추출** 필드 아래에서 상태를 클릭합니다. 이 경우 **완료됨**&#x200B;을 클릭하여 새 탭에서 로그를 봅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

1. 사용자 인터페이스를 사용하지 않고 로그를 추적하려면 소스 AEM 환경에 SSH를 사용하여 `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`를 추적할 수 있습니다.

### 마이그레이션 세트 삭제 {#deleting-migration-set}

*개요* 페이지에서 마이그레이션 세트를 삭제할 수 있습니다.
아래 단계를 따르십시오.

1. *개요* 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 표시줄에서 **삭제**&#x200B;를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. **마이그레이션 세트 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭하여 삭제를 확인합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)


## 게시 인스턴스에서 컨텐츠 전송 도구 실행 {#running-ctt-on-publish}

컨텐츠를 게시 인스턴스로 이동하는 동안 컨텐츠를 대상 게시 인스턴스로 이동하기 위해 CTT를 소스 게시 인스턴스에 설치하는 것이 좋습니다. 아래 설명된 대로 권장되는 방법을 따르십시오.

* 작성자 인스턴스에서 사용한 것과 동일한 버전의 CTT를 사용합니다.

* 단일 게시 노드만 마이그레이션해야 합니다. 추출 작업을 시작하기 전에 로드 밸런서에서 제거해야 합니다.

* 마이그레이션 세트를 만들 때 작성 AEMaaCS 환경의 URL을 사용합니다.

* 게시하기 위해 수집하는 동안 게시 계층의 크기가 조정되지 않습니다(작성자와 다름). 따라서 다음과 같은 쓰기 작업을 시작하지 마십시오.

   * AEM AaCS 작성자에서 해당 환경의 게시로 컨텐츠 배포
   * 게시 인스턴스 간 사용자 동기화


## 문제 해결 {#troubleshooting}

### Blob ID가 누락됨 {#missing-blobs}

아래에 언급했듯이 보고된 Blob ID가 누락된 경우 기존 저장소에서 일관성 검사를 실행하고 누락된 Blob를 복원해야 합니다.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

다음 명령이 실행됩니다.

>[!NOTE]
>
>`--verbose` 플래그는 BLOB을 참조하는 노드 경로를 보고하는 데 필요합니다.

**저장소 AEM 6.5(Oak 1.8 이하)의 경우**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Oak 1.10 이상이 있는 저장소의 경우**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

자세한 내용은 [Oak 실행 가능 Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)를 참조하십시오.

일관성을 위해 위에 지정된 *OUT_DIR*&#x200B;에 생성된 파일에서 경로에 바이너리가 누락되고, 백업에서 복원, 경로 삭제, 색인 재지정 등과 같은 적절한 조치를 취했는지 확인할 수 있습니다. 


### UI 동작 {#ui-behavior}

사용자는 컨텐츠 전송 도구에 대한 UI(사용자 인터페이스)에서 다음과 같은 동작 변경 사항을 볼 수 있습니다.

* 컨텐츠 전송 도구 UI의 아이콘이 이 안내서에 표시된 스크린샷과 다르거나 소스 AEM 인스턴스의 버전에 따라 전혀 표시되지 않을 수 있습니다.
