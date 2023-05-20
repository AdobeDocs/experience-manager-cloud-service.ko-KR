---
title: 대용량 콘텐츠 저장소 처리(이전)
description: 이 섹션에서는 대용량 콘텐츠 저장소 처리에 대해 설명합니다
hide: true
hidefromtoc: true
exl-id: 19021f40-d0a5-4e0c-a213-c421338cedeb
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 4%

---

# 대용량 콘텐츠 저장소 처리(이전) {#handling-large-content-repositories}

## 개요 {#overview}

CTT(콘텐츠 전송 도구)를 사용하여 많은 수의 Blob를 복사하는 데 여러 날이 걸릴 수 있습니다.
컨텐츠 전송 활동의 추출 및 수집 단계 속도를 크게 향상시켜 컨텐츠를 AEM as a Cloud Service으로 이동하려면 CTT를 활용할 수 있습니다 [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 선택적 사전 복사 단계입니다. 이 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3, Azure Blob Storage 데이터 저장소 또는 파일 데이터 저장소를 사용하도록 구성된 경우 사용할 수 있습니다. 이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3, Azure Blob Storage 또는 파일 데이터 저장소의 Blob을 마이그레이션 세트 Blob 저장소로 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 Blob 저장소의 Blob을 대상 AEM as a Cloud Service Blob 저장소로 복사합니다.

>[!NOTE]
> 이 기능은 CTT 1.5.4 릴리스에서 도입되었습니다.

## 시작하기 전에 고려해야 할 중요한 사항 {#important-considerations}

시작하기 전에 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* 소스 AEM 버전은 6.3 - 6.5여야 합니다.

* 소스 AEM 데이터 저장소가 Amazon S3 또는 Azure Blob 저장소를 사용하도록 구성되었습니다. 자세한 내용은 다음을 참조하십시오. [AEM 6에서 노드 저장소 및 데이터 저장소 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en).

* 각 마이그레이션 세트는 전체 데이터 저장소를 복사하므로 단일 마이그레이션 세트만 사용해야 합니다.

* 설치하려면 액세스 권한이 필요합니다. [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 소스 AEM 인스턴스를 실행하는 인스턴스(또는 VM)에서

* 데이터 저장소 가비지 수집이 소스에서 이전 7일 내에 실행되었습니다. 자세한 내용은 다음을 참조하십시오. [데이터 저장소 가비지 수집](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en#data-store-garbage-collection).


### 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob 저장 공간 데이터 저장소를 사용하도록 구성된 경우 추가 고려 사항 {#additional-considerations-amazons3-azure}

* Amazon S3 및 Azure Blob Storage 모두에서 데이터를 전송하는 것과 관련된 비용이 있으므로 전송 비용은 스토리지 컨테이너의 총 데이터 양(AEM에서 참조되는지 여부)에 상대적입니다. 을(를) 참조하십시오 [Amazon](https://aws.amazon.com/s3/pricing/) 및 [Azure Blob 저장소](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) 을 참조하십시오.

* 소스 Amazon S3 버킷에 대한 액세스 키 및 비밀 키 쌍 또는 소스 Azure Blob 스토리지 컨테이너에 대한 SAS URI가 필요합니다(읽기 전용 액세스는 사용 가능).

### 소스 AEM 인스턴스가 파일 데이터 저장소를 사용하도록 구성된 경우 추가 고려 사항 {#additional-considerations-aem-instance-filedatastore}

* 로컬 시스템의 사용 가능한 공간은 소스 데이터 저장소의 1/256 크기보다 엄격히 커야 합니다. 예를 들어 데이터 저장소의 크기가 3TB인 경우 11.72GB보다 큰 사용 가능한 공간이 `crx-quickstart/cloud-migration` AzCopy가 작동하도록 소스에 있는 폴더입니다. 최소한 소스 시스템의 여유 공간은 1GB여야 합니다. 사용 가능한 공간은 다음을 사용하여 얻을 수 있습니다. `df -h` linux 인스턴스의 명령 및 Windows 인스턴스의 dir 명령

* AzCopy를 활성화한 상태로 추출을 실행할 때마다 전체 파일 데이터 저장소가 병합되고 클라우드 마이그레이션 컨테이너에 복사됩니다. 마이그레이션 세트가 데이터 저장소의 크기보다 훨씬 작은 경우 AzCopy 추출이 최적의 접근 방식이 아닙니다.

* AzCopy를 사용하여 데이터 저장소를 통해 복사한 후에는 델타 또는 추가 추출에 대해 비활성화하십시오.

## 사전 복사 단계로 AzCopy를 사용하도록 설정 {#setting-up-pre-copy-step}

이 섹션을 따라 AzCopy를 컨텐츠 전송 도구를 사용하여 AzCopy를 사전 복사 단계로 사용하여 컨텐츠를 AEM as a Cloud Service으로 마이그레이션하도록 설정하는 방법을 알아보십시오.

### 0. 데이터 저장소에 있는 모든 컨텐츠의 총 크기 결정 {#determine-total-size}

다음 두 가지 이유로 데이터 저장소의 총 크기를 결정하는 것이 중요합니다.

* 소스 AEM이 파일 데이터 저장소를 사용하도록 구성된 경우 로컬 시스템의 사용 가능한 공간은 소스 데이터 저장소의 1/256 크기보다 엄격히 커야 합니다.

* 데이터 저장소의 총 크기를 알면 추출 및 수집 시간을 추정하는 데 도움이 됩니다. 사용 [컨텐츠 전송 도구 계산기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en#content-transfer) 위치: [Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/introduction-cam/overview-cam.html?lang=en) 추출 및 수집 시간을 추정하기 위해

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage}

Azure 포털의 컨테이너 속성 페이지에서 **크기 계산** 컨테이너에 있는 모든 콘텐츠의 크기를 결정하는 단추입니다. 예:

![이미지](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 데이터 저장소 {#amazon-data}

컨테이너의 지표 탭을 사용하여 컨테이너에 있는 모든 콘텐츠의 크기를 결정할 수 있습니다. 예:


![이미지](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### 파일 데이터 저장소 {#file-data-store-determine-size}

* mac, UNIX 시스템의 경우 데이터 저장소 디렉토리에서 du 명령을 실행하여 크기를 가져옵니다.
   `du -sh [path to datastore on the instance]`을 따르지 않는 경우입니다. 예를 들어 데이터 저장소가에 있는 경우 `/mnt/author/crx-quickstart/repository/datastore`, 다음 명령을 실행하면 크기가 표시됩니다. `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Windows의 경우 데이터 저장소 디렉토리에서 dir 명령을 사용하여 해당 크기를 가져옵니다.
   `dir /a/s [location of datastore]`.

### 1. AzCopy 설치 {#install-azcopy}

[AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 는 이 기능을 활성화하기 위해 소스 인스턴스에서 사용할 수 있어야 하는 Microsoft에서 제공하는 명령줄 도구입니다.

즉, Linux x86-64 바이너리를 [AzCopy 문서 페이지](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) /usr/bin과 같은 위치로 tar을 해제합니다.

>[!IMPORTANT]
>나중 단계에서 이진에 대한 전체 경로가 필요하므로 이진의 위치를 기록해 두십시오.

### 2. AzCopy 지원을 통해 CTT(Content Transfer Tool) 릴리스 설치 {#install-ctt-azcopy-support}

Amazon S3 및 Azure Blob Storage에 대한 AzCopy 지원은 CTT 1.5.4 릴리스에 포함되어 있습니다.
파일 데이터 저장소에 대한 지원은 CTT 1.7.2 릴리스에 포함되어 있습니다. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털.


### 3. azcopy.config 파일 구성 {#configure-azcopy-config-file}

소스 AEM 인스턴스의 `crx-quickstart/cloud-migration`, 라는 새 파일을 만듭니다. `azcopy.config`.

>[!NOTE]
>이 구성 파일의 내용은 소스 AEM 인스턴스가 Azure 또는 Amazon S3 데이터 저장소를 사용하는지 또는 파일 데이터 저장소를 사용하는지에 따라 달라집니다.

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage-data}

azcopy.config 파일에는 다음 속성이 포함되어야 합니다(인스턴스에 올바른 azCopyPath 및 azureSas를 사용해야 함).

>[!NOTE]
>
> Blob 저장소 컨테이너에 대한 쓰기 액세스 권한을 부여하지 않는 경우 읽기 및 목록 권한만 있는 새 SAS URI를 생성할 수 있습니다.

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

사용자 `azcopy.config` 파일에는 파일 데이터 저장소의 위치를 가리키는 선택적 repository.home 속성과 azcopyPath 속성이 포함되어야 합니다. 인스턴스에 올바른 값을 사용하십시오.
파일 데이터 저장소

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

azcopyPath 속성은 azCopy 명령줄 도구가 소스 AEM 인스턴스에 설치된 위치의 전체 경로를 포함해야 합니다. azCopyPath 속성이 없으면 blob 사전 복사 단계가 수행되지 않습니다.

If `repository.home` 속성이 azcopy.config에 없으면 기본 데이터 저장소 위치가 누락됩니다. `/mnt/crx/author/crx-quickstart/repository/datastore` 는 사전 복사를 수행하는 데 사용됩니다.

### 4. AzCopy로 추출 {#extracting-azcopy}

위의 구성 파일이 있는 경우 AzCopy 사전 복사 단계는 모든 후속 추출의 일부로 실행됩니다. 실행을 방지하기 위해 이 파일의 이름을 바꾸거나 제거할 수 있습니다.

>[!NOTE]
>AzCopy가 올바르게 구성되지 않으면 로그에 이 메시지가 표시됩니다.
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. CTT UI에서 추출을 시작합니다. 을(를) 참조하십시오 [컨텐츠 전송 도구 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) 및 [추출 프로세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en) 을 참조하십시오.

1. 추출 로그에 다음 줄이 인쇄되었는지 확인합니다.

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

축하합니다! 이 로그 항목은 구성이 유효한 것으로 간주되었으며 AzCopy가 현재 소스 컨테이너의 모든 블롭을 마이그레이션 컨테이너로 복사하고 있음을 의미합니다.

AzCopy의 로그 항목은 추출 로그에 표시되고 접두사로 c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy 사전 복사]

>[!CAUTION]
>
> 추출의 처음 몇 분 동안은 추출 로그에서 문제의 징후를 면밀히 확인하십시오. 예를 들어 소스 Azure 컨테이너를 찾을 수 없는 경우 기록되는 내용은 다음과 같습니다.

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

AzCopy에 문제가 발생하면 추출이 즉시 실패하고 추출 로그에 실패에 대한 세부 정보가 포함됩니다.

오류 이전에 복사된 모든 블롭은 후속 실행 시 AzCopy에서 자동으로 건너뛰므로 다시 복사할 필요가 없습니다.

#### 파일 데이터 저장소용 {#file-data-store-extract}

소스 파일 dataStore에 대해 AzCopy가 실행 중이면 다음과 같은 메시지가 로그에 표시되는데, 이는 폴더가 처리 중임을 나타냅니다.
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. AzCopy로 수집 {#ingesting-azcopy}

콘텐츠 전송 도구 1.5.4가 출시되면서 AzCopy 지원이 작성자 수집에 추가되었습니다.

>[!NOTE]
>먼저 작성자 수집만 실행하는 것이 좋습니다. 이렇게 하면 나중에 실행할 때 게시 수집 속도가 빨라집니다.

수집 중에 AzCopy를 활용하려면 최소 버전 2021.6.5561의 AEM as a Cloud Service 버전을 사용해야 합니다.

CTT UI에서 작성자 수집을 시작합니다. 다음을 참조하십시오. [수집 프로세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en) 을 참조하십시오.
AzCopy의 로그 항목이 수집 로그에 표시됩니다. 이러한 세그먼트는 다음과 같이 표시됩니다.

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination doesn't have full folder support
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

## AzCopy 비활성화 {#disable-azcopy}

AzCopy를 비활성화하려면 `azcopy.config` 파일.

예를 들어 azcopy 추출은 다음과 같이 비활성화할 수 있습니다. `mv /mnt/crx/author/crx-quickstart/cloud-migration/azcopy.config /mnt/crx/author/crx-quickstart/cloud-migration/noazcopy.config`.

## 다음 단계 {#whats-next}

AEM 대형 콘텐츠 저장소 처리를 통해 콘텐츠 전송 활동의 추출 및 수집 단계 속도를 크게 높여 콘텐츠를 as a Cloud Service으로 이동하는 방법을 학습했다면 이제 콘텐츠 전송 도구에서 추출 프로세스를 학습할 준비가 된 것입니다. 다음을 참조하십시오 [컨텐츠 전송 도구에서 소스에서 컨텐츠 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) 콘텐츠 전송 도구에서 마이그레이션 세트를 추출하는 방법을 알아봅니다.
