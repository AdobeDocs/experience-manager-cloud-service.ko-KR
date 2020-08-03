---
title: 컨텐츠 전송 도구 사용
description: 컨텐츠 전송 도구 사용
translation-type: tm+mt
source-git-commit: 1a2172a35c3409dd98f4ce93d621762b935d122f
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 97%

---


# 컨텐츠 전송 도구 사용 {#using-content-transfer-tool}

## 컨텐츠 전송 도구 사용에 대한 중요한 고려 사항 {#pre-reqs}

아래 섹션을 따라 수행하여 컨텐츠 전송 도구를 실행하는 동안 중요한 고려 사항을 이해하십시오.

* 컨텐츠 전송 도구의 최소 시스템 요구 사항은 AEM 6.3 이상 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 컨텐츠 저장소를 AEM 6.5로 업그레이드해야 컨텐츠 전송 도구를 사용할 수 있습니다.

* 컨텐츠 전송 도구는 다음 유형의 데이터 저장소와 함께 사용할 수 있습니다. 파일 데이터 저장소, S3 데이터 저장소 및 공유 S3 데이터 저장소. 현재 Azure Blob 저장소 데이터 저장소를 지원하지 않습니다.

* *샌드박스 환경*&#x200B;을 사용 중인 경우 환경이 2020년 6월 10일 이후 릴리스로 업그레이드되었는지 확인하십시오. *프로덕션 환경*&#x200B;을 사용하는 경우 자동으로 업데이트됩니다.

* 컨텐츠 전송 도구를 사용하려면 소스 인스턴스의 관리 사용자여야 하며, 컨텐츠를 전송하는 클라우드 서비스 인스턴스의 AEM 관리 그룹에 속해 있어야 합니다. 권한이 없는 사용자는 액세스 토큰을 검색하여 컨텐츠 전송 도구를 사용할 수 없습니다.

* 추출 단계 중에 컨텐츠 전송 도구는 활성 AEM 소스 인스턴스에서 실행됩니다.

* 작성자에 대한 *수집 단계*&#x200B;는 전체 작성자 배포를 축소합니다. 즉, 전체 수집 프로세스 중에 작성자 AEM을 사용할 수 없습니다.

* 컨텐츠 전송 도구가 한 번에 지원할 수 있는 저장소 크기에 대한 권장 상한은 20GB입니다.

## 사용 가능 {#availability}

소프트웨어 배포 포털에서 컨텐츠 전송 도구를 zip 파일(컨텐츠 전송 도구 v1.0.0)로 다운로드할 수 있습니다. 패키지 관리자를 통해 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지를 설치할 수 있습니다.

>[!NOTE]
>[소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털에서 컨텐츠 전송 도구를 다운로드합니다.

## 컨텐츠 전송 도구 실행 {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)

이 섹션을 따라 컨텐츠 전송 도구를 사용하여 컨텐츠를 클라우드 서비스로서 AEM(작성자/게시)에 마이그레이션하는 방법을 알아보십시오.

1. Adobe Experience Manager를 선택하고 도구 -> **작업** -> **컨텐츠 전송**&#x200B;으로 이동합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. **마이그레이션 세트 만들기**&#x200B;를 클릭하여 새 마이그레이션 세트를 만듭니다. **컨텐츠 마이그레이션 세트 세부 정보**&#x200B;가 표시됩니다.

   >[!NOTE]
   >현재 상태로 이 화면에서 기존 마이그레이션 세트를 봅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. 아래 설명된 대로 **컨텐츠 마이그레이션 세트 세부 정보 화면**&#x200B;의 필드를 채웁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **이름**: 마이그레이션 세트의 이름을 입력합니다.
      >[!NOTE]
      >마이그레이션 세트 이름에는 특수 문자를 사용할 수 없습니다.

   1. **클라우드 서비스 구성**: 대상 AEM을 클라우드 서비스 작성자 URL로 입력합니다.

      >[!NOTE]
      >컨텐츠 전송 작업 중에 한 번에 최대 4개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
      >또한 특정 환경 - *단계*, *개발* 또는 *프로덕션*&#x200B;마다 개별적으로 마이그레이션을 만들어야 합니다.

   1. **액세스 토큰**: 액세스 토큰을 입력합니다.

      >[!NOTE]
      >`/libs/granite/migration/token.json`으로 이동하여 작성자 인스턴스에서 액세스 토큰을 검색할 수 있습니다. 액세스 토큰이 클라우드 서비스 작성자 인스턴스에서 검색됩니다.

   1. **매개 변수**: 다음 매개 변수를 선택하여 마이그레이션 세트를 만듭니다.

      1. **버전 포함**: 필요에 따라 선택합니다.

      1. **포함할 경로**: 경로 브라우저를 사용하여 마이그레이션해야 하는 경로를 선택합니다.

         >[!IMPORTANT]
         >마이그레이션 세트를 만드는 동안 다음 경로가 제한됩니다.
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. **컨텐츠 마이그레이션 세트 세부 사항** 화면에서 모든 필드를 채운 후 **저장**&#x200B;을 클릭합니다.

1. 마이그레이션 세트는 *개요* 페이지에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   이 화면의 모든 기존 마이그레이션 세트가 현재 상태 및 상태 정보와 함께 *개요* 페이지에 표시됩니다.

   * *빨간색 클라우드*&#x200B;는 추출 프로세스를 완료할 수 없음을 나타냅니다.
   * *녹색 클라우드*&#x200B;는 추출 과정을 완료할 수 있음을 나타냅니다.
   * *노란색 아이콘*&#x200B;은 기존 마이그레이션 세트를 만들지 않았으며, 특정 마이그레이션은 동일한 인스턴스에 있는 다른 사용자가 작성했음을 나타냅니다.

1. 개요 페이지에서 마이그레이션 세트를 선택하고 **속성**&#x200B;을 클릭하여 마이그레이션 세트 속성을 보거나 편집합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### 컨텐츠 전송의 추출 프로세스 {#extraction-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 추출하려면 아래 단계를 따르십시오.

1. *개요* 페이지에서 마이그레이션 세트를 선택하고 **추출**&#x200B;을 클릭하여 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. **마이그레이션 세트 추출** 대화 상자가 표시되면 **추출**&#x200B;을 클릭하여 추출 단계를 완료합니다.

   >[!NOTE]
   >추출 단계 중에 스테이징 컨테이너를 덮어쓰는 옵션이 제공됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. 이제 **추출** 필드에 진행 중인 추출 프로세스에 대한 **실행** 상태가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   추출이 완료되면 마이그레이션 세트의 상태가 **완료됨**&#x200B;으로 업데이트되고 *녹색* 클라우드 아이콘이 **정보**&#x200B;필드 아래에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   >업데이트된 상태를 보려면 페이지를 새로 고쳐야 합니다.
   >추출 단계가 시작되면 *60초* 후 쓰기 잠금이 만들어지고 해제됩니다. 따라서 추출이 중지된 경우 다시 추출을 시작하기 전에 잠금이 해제될 때까지 잠시 기다려야 합니다.

#### 추가 추출 {#top-up-extraction-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

추출 프로세스가 완료되면 추가 추출 방법을 사용하여 델타 컨텐츠를 전송할 수 있습니다. 아래 단계를 따르십시오.

1. *개요* 페이지로 이동하고 추가 추출을 수행할 마이그레이션 세트를 선택합니다.

1. **추출**&#x200B;을 클릭하여 추가 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. **마이그레이션 세트 추출** 대화 상자가 표시됩니다.

   >[!IMPORTANT]
   >**추출 중에 스테이징 컨테이너 덮어쓰기** 옵션을 비활성화해야 합니다.
   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### 컨텐츠 전송의 수집 프로세스 {#ingestion-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.

1. *개요* 페이지에서 마이그레이션 세트를 선택하고 **수집**&#x200B;을 클릭하여 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. **마이그레이션 세트 수집** 대화 상자가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   데모 목적으로 **컨텐츠를 작성자 인스턴스에 수집** 옵션이 비활성화됩니다. 컨텐츠를 작성자와 게시에 동시에 수집할 수 있습니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   **수집**&#x200B;을 클릭하여 수집 단계를 완료합니다.

1. 수집이 완료되면 **작성자 수집** 필드의 상태가 **완료됨**&#x200B;으로 업데이트되고, 녹색 클라우드 아이콘이 **정보** 아래에 표시됩니다.
   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > 업데이트된 상태를 보려면 페이지를 새로 고쳐야 합니다.

#### 추가 수집 {#top-up-ingestion-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

수집 프로세스가 완료되면 추가 수집 방법을 사용하여 델타 컨텐츠를 사용할 수 있습니다. 아래 단계를 따르십시오.

1. *개요* 페이지로 이동하고 추가 수집을 수행할 마이그레이션 세트를 선택합니다.

1. **수집**&#x200B;을 클릭하여 추가 추출을 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. **마이그레이션 세트 수집** 대화 상자가 표시됩니다.

   >[!NOTE]
   >이전 수집 활동에서 기존 컨텐츠를 삭제하지 않으려면 *지우기* 옵션을 비활성화해야 합니다.
   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

### 마이그레이션 세트에 대한 로그 보기 {#viewing-logs-migration-set}

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

* 사용자는 작성자 URL(개발/스테이지/프로덕션)에 대한 마이그레이션 세트를 만들고 추출 및 수집을 성공적으로 수행합니다.

* 그런 다음 동일한 작성자 URL에 대한 새 마이그레이션 세트를 만들고 새 마이그레이션 세트에 대해 추출 및 수집을 수행합니다. UI에 첫 번째 마이그레이션 세트의 수집 상태가 **실패**&#x200B;로 변경되고 로그를 사용할 수 없다고 표시됩니다.

* 이는 첫 번째 마이그레이션 세트에 대한 수집이 실패했음을 의미하지 않습니다. 이 동작은 새로운 수집 작업이 시작되면 이전 수집 작업이 삭제되기 때문에 표시되는 것입니다. 따라서 첫 번째 마이그레이션 세트의 변경 상태는 무시해도 됩니다.

* 컨텐츠 전송 도구 UI의 아이콘이 이 안내서에 표시된 스크린샷과 다르거나 소스 AEM 인스턴스의 버전에 따라 전혀 표시되지 않을 수 있습니다.


