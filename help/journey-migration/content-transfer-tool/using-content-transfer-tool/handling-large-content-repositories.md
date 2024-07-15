---
title: 대형 콘텐츠 저장소 처리
description: 이 섹션에서는 대용량 콘텐츠 저장소 처리에 대해 설명합니다
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1800'
ht-degree: 8%

---

# 대형 콘텐츠 저장소 처리 {#handling-large-content-repositories}

## 개요 {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="대형 콘텐츠 저장소 처리"
>abstract="콘텐츠 전송 활동의 추출 및 수집 단계를 크게 가속화하여 콘텐츠를 AEM as a Cloud Service로 이동하기 위해 CTT(콘텐츠 전송 도구)는 선택 사항인 사전 복사 단계로 AzCopy를 사용할 수 있습니다. 이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3 또는 Azure Blob 저장소에서 마이그레이션 세트 Blob 저장소로 Blob을 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 Blob 저장소의 Blob을 대상 AEM as a Cloud Service Blob 저장소로 복사합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step" text="사전 복사 단계로 AzCopy 시작"

CTT(콘텐츠 전송 도구)를 사용하여 많은 Blob을 복사하는 데 며칠이 걸릴 수 있습니다.
컨텐츠 전송 활동의 추출 및 수집 단계 속도를 높여 컨텐츠를 AEM as a Cloud Service으로 이동하려면 CTT에서 [AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)를 선택적 사전 복사 단계로 사용할 수 있습니다. 이 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3, Azure Blob Storage 데이터 저장소 또는 파일 데이터 저장소를 사용하도록 구성된 경우 사용할 수 있습니다. 사전 복사 단계는 첫 번째 전체 추출 및 수집에 가장 효과적입니다. 그러나 전체 프로세스에 시간이 추가될 수 있으므로 후속 추가 작업에 사전 복사를 사용하지 않는 것이 좋습니다(추가 크기가 200GB 미만인 경우). 이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3, Azure Blob Storage 또는 파일 데이터 저장소의 Blob을 마이그레이션 세트 Blob 저장소로 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 Blob 저장소의 Blob을 대상 AEM as a Cloud Service Blob 저장소로 복사합니다.

## 시작하기 전에 고려해야 할 중요한 사항 {#important-considerations}

시작하기 전에 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* CTT 버전 2.0.16부터 번들을 설치하면 사전 복사 설정이 자동으로 수행됩니다. 또한 마이그레이션 세트 크기가 200GB보다 큰 경우 추출 프로세스에서 자동으로 사전 복사 기능을 사용합니다. azcopy.config 파일은 crx-quickstart/cloud-migration/ 디렉토리에 생성됩니다. CTT 버전 2.0.16 이상을 사용하는 경우에는 사전 복사 설정을 수동으로 수행할 필요가 없습니다.

* Source AEM 버전은 6.3 - 6.5여야 합니다.

* Source AEM의 데이터 저장소가 Amazon S3 또는 Azure Blob 저장소를 사용하도록 구성되었습니다. 자세한 내용은 [AEM에서 노드 저장소 및 데이터 저장소 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html)을 참조하세요.

* 각 마이그레이션 세트는 전체 데이터 저장소를 복제하므로 단일 마이그레이션 세트만 사용해야 합니다.

* 원본 AEM 인스턴스를 실행하는 인스턴스(또는 VM)에 [AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)을(를) 설치하려면 액세스 권한이 필요합니다.

* 데이터 저장소 가비지 수집이 소스에서 이전 7일 내에 실행되었습니다. 자세한 내용은 [데이터 저장소 가비지 수집](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#data-store-garbage-collection)을 참조하십시오.

### 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob 저장 공간 데이터 저장소를 사용하도록 구성된 경우 추가 고려 사항 {#additional-considerations-amazons3-azure}

* Amazon S3 및 Azure Blob Storage에서 데이터를 전송하는 것과 관련된 비용이 있습니다. 전송 비용은 기존 저장소 컨테이너의 총 데이터 양(AEM에서 참조되었는지 여부)과 상대적입니다. 자세한 내용은 [Amazon S3](https://aws.amazon.com/s3/pricing/) 및 [Azure Blob 저장소](https://azure.microsoft.com/en-us/pricing/details/bandwidth/)를 참조하세요.

* 기존 소스 Amazon S3 버킷에 대한 액세스 키 및 비밀 키 쌍 또는 기존 소스 Azure Blob 스토리지 컨테이너에 대한 SAS URI가 필요합니다(읽기 전용 액세스는 가능).

### 소스 AEM 인스턴스가 파일 데이터 저장소를 사용하도록 구성된 경우 추가 고려 사항 {#additional-considerations-aem-instance-filedatastore}

* 로컬 시스템의 사용 가능한 공간은 소스 데이터 저장소의 1/256 크기보다 엄격히 커야 합니다. 예를 들어 데이터 저장소의 크기가 3테라바이트이면 AzCopy가 작동하려면 소스의 `crx-quickstart/cloud-migration` 폴더에 11.72GB보다 큰 사용 가능한 공간이 있어야 합니다. 최소한 소스 시스템의 여유 공간은 1GB여야 합니다. Linux® 인스턴스에서는 `df -h` 명령을 사용하고 Windows 인스턴스에서는 dir 명령을 사용하여 사용 가능한 공간을 확보할 수 있습니다.

* AzCopy를 활성화한 상태로 추출을 실행할 때마다 전체 파일 데이터 저장소가 병합되고 클라우드 마이그레이션 컨테이너에 복사됩니다. 마이그레이션 세트가 데이터 저장소의 크기보다 작은 경우 AzCopy 추출이 최적의 접근 방식이 아닙니다.

* AzCopy를 사용하여 기존 데이터 저장소를 복사한 후에는 델타 또는 추가 추출에 대해 비활성화하십시오.

## 사전 복사 단계로 AzCopy를 사용하도록 설정 {#setting-up-pre-copy-step}

>[!NOTE]
>CTT 버전 2.0.16부터 번들을 설치하면 사전 복사 설정이 자동으로 수행됩니다. 또한 마이그레이션 세트 크기가 200GB보다 큰 경우 추출 프로세스에서 자동으로 사전 복사 기능을 사용합니다. azcopy.config 파일은 crx-quickstart/cloud-migration/ 디렉토리에 생성됩니다. 파일의 구성을 수동으로 업데이트하려면 아래 섹션을 검토하십시오.

이 섹션을 따라 수행하여 컨텐츠 전송 도구로 AzCopy를 사전 복사 단계로 사용하여 컨텐츠를 AEM as a Cloud Service으로 마이그레이션하도록 설정하는 방법을 알아보십시오.

### 0. 데이터 저장소에 있는 모든 컨텐츠의 총 크기 결정 {#determine-total-size}

다음 두 가지 이유로 데이터 저장소의 총 크기를 결정하는 것이 중요합니다.

* 소스 AEM이 파일 데이터 저장소를 사용하도록 구성된 경우 로컬 시스템의 사용 가능한 공간은 소스 데이터 저장소의 1/256 크기보다 엄격히 커야 합니다.

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage}

Azure 포털의 기존 컨테이너 속성 페이지에서 **크기 계산** 단추를 사용하여 컨테이너에 있는 모든 콘텐츠의 크기를 결정합니다. 예:

![이미지](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 데이터 저장소 {#amazon-data}

컨테이너의 지표 탭을 사용하여 컨테이너에 있는 모든 콘텐츠의 크기를 결정할 수 있습니다. 예:


![이미지](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### 파일 데이터 저장소 {#file-data-store-determine-size}

* Mac, UNIX® 시스템의 경우 데이터 저장소 디렉토리에서 du 명령을 실행하여 해당 크기를 가져옵니다.
  `du -sh [path to datastore on the instance]`. 예를 들어 데이터 저장소가 `/mnt/author/crx-quickstart/repository/datastore`에 있으면 다음 명령을 사용하여 해당 크기를 가져옵니다. `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Windows의 경우 데이터 저장소 디렉토리에서 dir 명령을 사용하여 해당 크기를 가져옵니다.
  `dir /a/s [location of datastore]`

### 1. AzCopy 설치 {#install-azcopy}

[AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)은(는) Microsoft®에서 제공하는 명령줄 도구이며 이 기능을 사용하려면 원본 인스턴스에서 사용할 수 있어야 합니다.

즉, [AzCopy 문서 페이지](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)에서 Linux® x86-64 바이너리를 다운로드하고 /usr/bin과 같은 위치로 자르기를 해제합니다.

>[!IMPORTANT]
>나중 단계에서 이진에 대한 전체 경로가 필요하므로 이진의 위치를 기록해 두십시오.

### 2. AzCopy 지원을 통해 CTT(Content Transfer Tool) 릴리스 설치 {#install-ctt-azcopy-support}

>[!IMPORTANT]
>가장 최근에 릴리스된 CTT 버전을 사용해야 합니다.

Amazon S3, Azure Blob Storage 및 파일 데이터 저장소에 대한 AzCopy 지원이 최신 CTT 릴리스에 포함되어 있습니다.
[소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털에서 최신 CTT 릴리스를 다운로드할 수 있습니다.
버전 2.0.0 이상만 지원되며 최신 버전을 사용하는 것이 좋습니다.

### 3. azcopy.config 파일 구성 {#configure-azcopy-config-file}

원본 AEM 인스턴스의 `crx-quickstart/cloud-migration`에서 `azcopy.config` 파일을 만듭니다.

>[!NOTE]
>이 구성 파일의 내용은 소스 AEM 인스턴스가 Azure 또는 Amazon S3 데이터 저장소를 사용하는지 또는 파일 데이터 저장소를 사용하는지에 따라 다릅니다.

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage-data}

azcopy.config 파일에는 다음 속성이 포함되어야 합니다(인스턴스에 올바른 azCopyPath 및 azureSas를 사용해야 함).

>[!NOTE]
>
> 기존 blob 저장소 컨테이너에 대한 쓰기 액세스 권한을 부여하지 않으려는 경우 읽기 및 목록 권한만 있는 새 SAS URI를 생성할 수 있습니다.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3 데이터 저장소 {#amazon-sdata-store}

azcopy.config 파일에는 다음 속성이 포함되어야 합니다(인스턴스에 올바른 값을 사용해야 함).

>[!NOTE]
>
> 인스턴스가 IAM 역할을 사용하여 AEM이 S3에 액세스할 수 있도록 하는 경우 S3 버킷에 대해 ListBucket 및 GetObject 작업이 활성화된 정책 및 사용자를 생성해야 합니다. 설정되면 이 사용자의 액세스 키와 비밀 키를 사용합니다.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

#### 파일 데이터 저장소 {#file-data-store-azcopy-config}

`azcopy.config` 파일에는 azCopyPath 속성과 파일 데이터 저장소의 위치를 가리키는 선택적 repository.home 속성이 있어야 합니다. 인스턴스에 올바른 값을 사용하십시오.
파일 데이터 저장소

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

azCopyPath 속성은 azCopy 명령줄 도구가 소스 AEM 인스턴스에 설치된 위치의 전체 경로를 포함해야 합니다. azCopyPath 속성이 누락된 경우 Blob 사전 복사 단계가 수행되지 않습니다.

`repository.home` 속성이 azcopy.config에 없으면 기본 데이터 저장소 위치 `/mnt/crx/author/crx-quickstart/repository/datastore`을(를) 사용하여 사전 복사를 수행합니다.

### 4. AzCopy로 추출 {#extracting-azcopy}

위의 구성 파일이 있는 경우 AzCopy 사전 복사 단계는 모든 후속 추출의 일부로 실행됩니다. 실행을 방지하기 위해 이 파일의 이름을 바꾸거나 제거할 수 있습니다.

>[!NOTE]
>AzCopy가 올바르게 구성되지 않으면 로그에 다음 메시지가 표시됩니다.
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. CTT UI에서 추출을 시작합니다. 자세한 내용은 [콘텐츠 전송 도구 시작하기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) 및 [추출 프로세스](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)를 참조하십시오.

1. 추출 로그에 다음 줄이 인쇄되었는지 확인합니다.

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

축하합니다! 이 로그 항목은 구성이 유효한 것으로 간주되었으며 AzCopy가 소스 컨테이너의 모든 블롭을 마이그레이션 컨테이너로 복사하고 있음을 의미합니다.

AzCopy의 로그 항목은 추출 로그에 나타나며 앞에 c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy 사전 복사]가 붙습니다.

>[!CAUTION]
>
> 추출의 처음 몇 분 동안은 추출 로그에서 문제의 징후를 면밀히 확인하십시오. 예를 들어 소스 Azure 컨테이너를 찾을 수 없는 경우 기록되는 내용은 다음과 같습니다.

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason > github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

AzCopy에 문제가 있으면 추출이 즉시 실패하고 추출 로그에 실패에 대한 세부 정보가 포함됩니다.

오류 전에 복사된 모든 블롭은 후속 실행 시 AzCopy에 의해 자동으로 건너뛰므로 다시 복사할 필요가 없습니다.

>[!TIP]
>이제 추출 성공 직후 수집이 자동으로 시작되도록 예약할 수 있습니다. 자세한 내용은 [Target으로 콘텐츠 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)을 참조하십시오.

#### 파일 데이터 저장소용 {#file-data-store-extract}

소스 파일 dataStore에 대해 AzCopy가 실행 중이면 다음과 같은 메시지가 로그에 표시되는데, 이는 폴더가 처리 중임을 나타냅니다.
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. AzCopy로 수집 {#ingesting-azcopy}

&quot;새 수집&quot; 대화 상자에서 AzCopy(사전 복사) 사용 여부에 대한 지침을 포함하여 Cloud Acceleration Manager(CAM)에서 대상으로 컨텐츠를 수집하는 방법에 대한 일반 정보는 [Ingesting Content ingesting](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)을 참조하십시오.

수집 중에 AzCopy를 활용하려면 Adobe 시 버전 2021.6.5561 이상의 AEM as a Cloud Service 버전을 사용하고 있어야 합니다.

진행 상황을 확인할 수 있도록 Cloud Acceleration Manager의 &quot;수집 작업&quot; 목록 및 수집 로그를 참조하십시오. 와 관련된 로그 항목
성공한 AzCopy 작업은 다음과 같이 표시됩니다(일부 차이 허용). 로그를 가끔 확인하면 문제가 발생할 수 있습니다.
일찍이 모든 문제에 대한 빠른 해결책을 찾는 데 도움이 됩니다.

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination does not have full folder support
INFO: azcopy: A newer version 10.11.0 is available to download
 
Job 419d98da-fc05-2a45-70cc-797fee632031 has started
Log file is located at: /root/.azcopy/419d98da-fc05-2a45-70cc-797fee632031.log
 
0.0 %, 0 Done, 0 Failed, 886 Pending, 0 Skipped, 886 Total,
 
Job 419d98da-fc05-2a45-70cc-797fee632031 summary
Elapsed Time (Minutes): 0.0334
Number of File Transfers: 886
Number of Folder Property Transfers: 0
Total Number of Transfers: 886
Number of Transfers Completed: 17
Number of Transfers Failed: 0
Number of Transfers Skipped: 869
TotalBytesTransferred: 248350
Final Job Status: CompletedWithSkipped
 
*************** Completed AzCopy pre-copy phase ***************
```

## 다음 단계 {#whats-next}

이제 AEM as a Cloud Service으로 콘텐츠를 이동하기 위한 콘텐츠 전송 활동의 추출 및 수집 단계 속도를 높이기 위해 대규모 콘텐츠 저장소 처리에 대해 배웠습니다. 이제 콘텐츠 전송 도구를 사용하여 추출 프로세스를 배울 준비가 되었습니다. 콘텐츠 전송 도구에서 마이그레이션 세트를 추출하는 방법을 배울 수 있도록 [콘텐츠 전송 도구에서 Source에서 콘텐츠 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)을 참조하십시오.
