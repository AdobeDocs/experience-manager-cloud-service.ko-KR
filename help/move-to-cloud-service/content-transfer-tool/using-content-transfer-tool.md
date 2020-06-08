---
title: 컨텐츠 전송 도구 사용
description: 컨텐츠 전송 도구 사용
translation-type: tm+mt
source-git-commit: f154ffacbeeee1993a9cc3bd3bd274be33dca7a7
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 1%

---


# 컨텐츠 전송 도구 사용 {#using-content-transfer-tool}

## 컨텐츠 전송 도구 사용에 대한 중요 고려 사항 {#pre-reqs}

컨텐츠 전송 도구를 실행하는 동안 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* 컨텐츠 전송 도구에 대한 최소 시스템 요구 사항은 AEM 6.3 + 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 콘텐츠 저장소를 AEM 6.5로 업그레이드하여 콘텐츠 전송 도구를 사용해야 합니다.

* 샌드박스 환경을 사용 중인 경우 *환경이 2020년 5월 29일*&#x200B;이후 릴리스로 업그레이드되었는지 확인하십시오. 프로덕션 환경을 사용하는 경우 *자동으로*&#x200B;업데이트됩니다.

* 콘텐츠 전송 도구를 사용하려면 소스 인스턴스의 관리자 사용자여야 하며, 콘텐츠를 전송하는 클라우드 서비스 인스턴스의 관리 그룹에 속해 있어야 합니다. 권한이 없는 사용자는 액세스 토큰을 검색하여 콘텐츠 전송 도구를 사용할 수 없습니다.

* 추출 단계 동안 컨텐츠 전송 도구는 활성 AEM 소스 인스턴스에서 실행됩니다.

* 작성자의 *통합* 단계는 전체 작성자 배포를 축소합니다. 이는 전체 통합 프로세스 동안 작성자 AEM을 사용할 수 없음을 의미합니다.

## 사용 가능 {#availability}

소프트웨어 배포 포털에서 컨텐트 전송 도구를 zip 파일로 다운로드할 수 있습니다. 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지 관리자를 통해 패키지를 설치할 수 있습니다.

>[!NOTE]
>Adobe [Experience Cloud에서 콘텐츠 전송 도구를 다운로드합니다](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## 컨텐츠 전송 도구 실행 {#running-tool}

콘텐츠 전송 도구를 사용하여 콘텐츠를 클라우드 서비스로 AEM으로 마이그레이션하는 방법(작성자/게시)을 배우려면 이 섹션을 따르십시오.

1. Adobe Experience Manager를 선택하고 도구 -> **작업** -> **컨텐츠 전송으로 이동합니다**.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. 마이그레이션 세트 **만들기를** 클릭하여 새 마이그레이션 세트를 만듭니다. 컨텐츠 **마이그레이션 세트 세부 정보가** 표시됩니다.

   >[!NOTE]
   >현재 상태로 이 화면에서 기존 마이그레이션 세트를 봅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. 아래 설명된 대로 **컨텐츠 마이그레이션 세트 세부** 정보 화면에서 필드를 채웁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **이름**: 마이그레이션 세트의 이름을 입력합니다.
      >[!NOTE]
      >마이그레이션 세트 이름에는 특수 문자가 허용되지 않습니다.

   1. **클라우드 서비스 구성**: 대상 AEM을 클라우드 서비스 작성자 URL로 입력합니다.

      >[!NOTE]
      >컨텐츠 전송 작업 중에 한 번에 최대 4개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
      >또한 특정 환경( *스테이지*, 개발 또는 *프로덕션*)마다 개별적으로 마이그레이션을 만들어야 *합니다*.

   1. **액세스 토큰**: 액세스 토큰을 입력합니다.

      >[!NOTE]
      >로 이동하여 작성 인스턴스에서 액세스 토큰을 검색할 수 있습니다 `/libs/granite/migration/token.json`.

   1. **매개 변수**: 다음 매개 변수를 선택하여 마이그레이션 세트를 만듭니다.

      1. **버전**&#x200B;포함: 필요에 따라 선택합니다.

      1. **포함할 경로**: 경로 브라우저를 사용하여 마이그레이션해야 하는 경로를 선택합니다.

         >[!IMPORTANT]
         >마이그레이션 세트를 만드는 동안 다음 경로가 제한됩니다.
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. [ **컨텐츠 마이그레이션** 세트 세부 사항] 화면에서 모든 필드를 채운 후 **저장을** 클릭합니다.

1. 마이그레이션 세트는 *개요* 페이지에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   이 화면의 모든 기존 마이그레이션 세트가 *개요* 페이지에 표시되어 현재 상태 및 상태 정보를 제공합니다.

   * 빨간색 *클라우드는* 추출 프로세스를 완료할 수 없음을 나타냅니다.
   * 녹색 *클라우드는* 추출 과정을 완료할 수 있음을 나타냅니다.
   * 노란색 아이콘 ** 은 기존 마이그레이션 세트를 만들지 않았으며 특정 마이그레이션은 동일한 인스턴스에 있는 다른 사용자가 작성했음을 나타냅니다.

1. 개요 페이지에서 마이그레이션 세트를 선택하고 속성 **을** 클릭하여 마이그레이션 세트 속성을 보거나 편집합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### 컨텐츠 전송의 추출 프로세스 {#extraction-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 추출하려면 아래 절차를 따르십시오.

1. [ *개요* ] 페이지에서 마이그레이션 세트를 선택하고 **추출을** 시작하려면 [추출]을 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. 마이그레이션 **세트 추출** 대화 상자가 표시되고 추출 **을 클릭하여 추출** 단계를 완료합니다.

   >[!NOTE]
   >추출 단계 동안 스테이징 컨테이너를 덮어쓸 수 있습니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. 이제 **추출** 필드 **에** 진행 중인 추출 프로세스에 대한 실행상태가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   추출을 완료하면 마이그레이션 세트의 상태가 **FINISHED로** 업데이트되고 *단색 녹색***클라우드 아이콘이** INFO필드 아래에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   >업데이트된 상태를 보려면 페이지를 새로 고쳐야 합니다.
   >추출 단계가 시작되면 *60초*&#x200B;후 쓰기 잠금이 만들어지고 해제됩니다. 따라서 추출을 중지한 경우 다시 추출을 시작하기 전에 잠금이 해제될 때까지 잠시 기다려야 합니다.

#### 위쪽 추출 {#top-up-extraction-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 상업을 지원하는 기능이 있습니다.

>[!NOTE]
>초기 컨텐츠 전송 후 Cloud Service에서 라이브하기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 상업을 수행하는 것이 좋습니다.

추출 프로세스가 완료되면 위쪽 추출 방법을 사용하여 델타 컨텐츠를 전송할 수 있습니다. 아래 단계를 따르십시오.

1. [ *개요* ] 페이지로 이동하고 위쪽 추출을 수행할 마이그레이션 세트를 선택합니다.

1. 추출 **을** 클릭하여 위쪽 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. 마이그레이션 **세트 추출** 대화 상자가 표시됩니다.

   >[!IMPORTANT]
   >추출 중에 준비 컨테이너 **덮어쓰기** 옵션을 비활성화해야 합니다.
   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### 컨텐츠 전송의 수집 프로세스 {#ingestion-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 인제스트하려면 아래 절차를 따르십시오.

1. [ *개요* ] 페이지에서 마이그레이션 세트를 선택하고 [인제스트] **를 클릭하여** 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. [ **마이그레이션 집합 통합** ] 대화 상자가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   데모용으로 [컨텐츠를 **작성자에게 인제스트] 옵션을 사용할 수** 없습니다. 컨텐츠를 작성자 및 게시에 동시에 인제스트할 수 있습니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   수집 **단계를** 완료하려면 인제스트를 클릭합니다.

1. 처리가 완료되면 **작성자 통합** 필드의 상태가 **완료됨으로** 업데이트되고 단색 녹색 클라우드 아이콘은 **정보(INFO)에**표시됩니다.
   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > 업데이트된 상태를 보려면 페이지를 새로 고쳐야 합니다.

#### 위로 처리 {#top-up-ingestion-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *최상위* 기능을 지원합니다.

>[!NOTE]
>초기 컨텐츠 전송 후 Cloud Service에서 라이브하기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 상업을 수행하는 것이 좋습니다.

처리 과정이 완료되면, 최상위 처리 방법을 사용하여 델타 컨텐츠를 사용할 수 있습니다. 아래 단계를 따르십시오.

1. [ *개요* ] 페이지로 이동하여 최상위 질문을 수행할 마이그레이션 세트를 선택합니다.

1. 인제스트 **를** 클릭하여 위쪽 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. [ **마이그레이션 세트 통합** ] 대화 상자가 표시됩니다.

   >[!NOTE]
   >이전 수집 활동에서 기존 컨텐츠를 삭제하지 않으려면 *지우기* 옵션을 비활성화해야 합니다.
   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

### 마이그레이션 세트에 대한 로그 보기 {#viewing-logs-migration-set}

[ *개요* ] 페이지에서 기존 마이그레이션 세트에 대한 로그를 볼 수 있습니다.
아래 단계를 따르십시오.

1. [ *개요* ] 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 표시줄에서 [로그 **보기** ]를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. [ **로그** ] 대화 상자가 표시됩니다. 추출 **로그를** 클릭하여 새 탭에서 로그를 확인합니다.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)Or,

   [ *개요] 화면에서 마이그레이션 세트에 대한 로그를 볼 수도* 있습니다. 마이그레이션 세트를 선택하고 추출 필드 아래에서 상태를 **클릭합니다** . 이 경우 [마침] **을** 클릭하여 새 탭에서 로그를 봅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

### 마이그레이션 세트 삭제 {#deleting-migration-set}

[ *개요* ] 페이지에서 마이그레이션 세트를 삭제할 수 있습니다.
아래 단계를 따르십시오.

1. [ *개요* ] 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 모음에서 **삭제를** 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. [마이그레이션 **세트** **삭제** ] 대화 상자에서 삭제를 클릭하여 삭제를 확인합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)

## 문제 해결 {#troubleshooting}

### Blob ID가 없습니다. {#missing-blobs}

아래에 언급했듯이 보고된 Blob ID가 없는 경우 기존 저장소에서 일관성 검사를 실행하고 누락된 Blob를 복원해야 합니다.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

다음 명령이 실행됩니다

>[!NOTE]
> `--verbose` 플래그는 BLOB가 참조되는 노드 경로를 보고하는 데 필요합니다.

**저장소 AEM 6.5(Oak 1.8 이하)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Oak > 1.10이 있는 저장소의 경우**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

자세한 내용은 [Oak 실행 가능](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) 항아리를 참조하십시오.

일관성을 위해 위에 지정된 *OUT_DIR에서* 생성된 파일은 누락된 경로 및 백업에서 복원, 경로 삭제, 다시 인덱싱 등과 같이 수행되는 적절한 작업을 확인할 수 있습니다.

### UI 동작 {#ui-behavior}

사용자는 컨텐츠 전송 도구에 대한 사용자 인터페이스(UI)에서 다음과 같은 동작 변경 사항을 볼 수 있습니다.

* 사용자는 작성자 URL(개발/스테이지/프로덕션)에 대한 마이그레이션 세트를 만들고 추출 및 회수를 성공적으로 수행합니다.

* 그런 다음 사용자는 동일한 작성자 URL에 대한 새 마이그레이션 세트를 만들고 새 마이그레이션 세트에 대해 추출 및 질문을 수행합니다. UI에 첫 번째 마이그레이션 세트의 통합 상태가 FAILED로 **변경되고** 로그를 사용할 수 없음을 보여줍니다.

* 이는 첫 번째 마이그레이션 세트에 대한 회합이 실패했음을 의미하지 않습니다. 이 동작은 새 통합 작업이 시작되면 이전 통합 작업이 삭제되기 때문에 표시됩니다. 따라서 첫 번째 마이그레이션 세트의 변경 상태는 무시되어야 합니다.

* 컨텐츠 전송 도구 UI의 아이콘은 이 안내서에 표시된 스크린샷과 다르거나 소스 AEM 인스턴스의 버전에 따라 전혀 표시되지 않을 수 있습니다.


