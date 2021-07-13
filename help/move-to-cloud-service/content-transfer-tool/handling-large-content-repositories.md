---
title: 대용량 컨텐츠 저장소 처리
description: 이 섹션에서는 대용량 컨텐츠 리포지토리의 처리에 대해 설명합니다
source-git-commit: 67c6c8af76b414600975fe349f025c7bf7acef5e
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 1%

---


# 대용량 컨텐츠 저장소 처리 {#handling-large-content-repositories}

## 개요 {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="대용량 컨텐츠 저장소 처리"
>abstract="컨텐츠 전송 활동의 추출 및 수집 단계를 크게 단축하여 컨텐츠를 Cloud Service으로 AEM으로 이동하기 위해 CTT는 AzCopy를 선택적 사전 복사 단계로 활용할 수 있습니다. 이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3 또는 Azure Blob 저장소에서 마이그레이션 세트 blob 저장소로 블롭을 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 blob 저장소에서 대상 AEM에 Cloud Service Blob 저장소를 복사합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step" text="AzCopy를 사전 복제 단계로 시작하기"

CTT(컨텐츠 전송 도구)를 사용하여 많은 수의 블롭을 복사하는 데 여러 날이 걸릴 수 있습니다.
컨텐츠 전송 활동의 추출 및 섭취 단계를 크게 단축하여 컨텐츠를 Cloud Service으로 AEM으로 이동하기 위해 CTT는 [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 를 선택적 사전 복사 단계로 활용할 수 있습니다. 이 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob 저장 공간 데이터 저장소를 사용하도록 구성된 경우 사용할 수 있습니다.  이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3 또는 Azure Blob 저장소에서 마이그레이션 세트 blob 저장소로 블롭을 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 blob 저장소에서 대상 AEM에 Cloud Service Blob 저장소를 복사합니다.

>[!NOTE]
> 이 기능은 CTT 1.5.4 릴리스에서 도입되었습니다.

## 시작하기 전에 중요한 고려 사항 {#important-considerations}

시작하기 전에 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* 소스 AEM 버전은 6.3 - 6.5여야 합니다.
* 소스 AEM 데이터 저장소는 Amazon S3 또는 Azure Blob 저장소를 사용하도록 구성되어 있습니다. 자세한 내용은 [AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en)에서 노드 저장소 및 데이터 저장소 구성 을 참조하십시오.
* 추출 중에 전체 데이터 저장소가 복사됩니다. Amazon S3 및 Azure Blob 저장소에서 데이터를 전송하는 데 드는 비용이 있으므로 전송 비용은 저장소 컨테이너의 총 데이터 양(AEM에서 참조되었는지 여부에 상관없이)에 상대적입니다. 자세한 내용은 [Amazon S3](https://aws.amazon.com/s3/pricing/) 및 [Azure Blob 저장 공간](https://azure.microsoft.com/en-us/pricing/details/bandwidth/)을 참조하십시오.
* 각 마이그레이션 세트는 전체 데이터 저장소를 복사하므로 단일 마이그레이션 세트만 사용해야 합니다.
* 소스 AEM 인스턴스를 실행하는 인스턴스(또는 VM)에 [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)를 설치하려면 액세스 권한이 필요합니다.
* 소스 Amazon S3 버킷에 대한 액세스 키 및 비밀 키 쌍 또는 소스 Azure Blob 저장소 컨테이너의 SAS URI가 필요합니다(읽기 전용 액세스 권한이 양호함).
* 데이터 저장소 가비지 수집이 소스의 이전 7일 이내에 실행되었습니다. 자세한 내용은 [데이터 저장소 가비지 컬렉션](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en#data-store-garbage-collection)을 참조하십시오.
* 소스 인스턴스의 대부분의 데이터가 마이그레이션에 포함됩니다.

## AzCopy를 사전 복사 단계로 사용하도록 설정 {#setting-up-pre-copy-step}

이 섹션을 따라 컨텐츠 전송 도구와 함께 AzCopy를 사전 복사 단계로 사용하여 컨텐츠를 AEM as a Cloud Service으로 마이그레이션하도록 설정하는 방법을 알아보십시오.

### 0. 데이터 저장소에 있는 모든 콘텐츠의 총 크기를 결정합니다 {#determine-total-size}

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage}

Azure 포털의 컨테이너 속성 페이지에서 **크기 계산** 단추를 사용하여 컨테이너에 있는 모든 콘텐츠의 크기를 결정합니다. 예:

![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 데이터 저장소 {#amazon-data}

컨테이너의 지표 탭을 사용하여 컨테이너에 있는 모든 컨텐츠의 크기를 결정할 수 있습니다. 예:


![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/amazon-s3-data-store.png)

### 1. AzCopy 설치 {#install-azcopy}

[](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) AzCopyis는 Microsoft에서 제공하는 명령줄 도구이며 이 기능을 사용하려면 소스 인스턴스에서 사용할 수 있어야 합니다.

즉, [AzCopy 문서 페이지](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10)에서 Linux x86-64 바이너리를 다운로드하고 /usr/bin과 같은 위치로 비타르 해제할 수 있습니다. 나중 단계에서 바이너리에 대한 전체 경로가 필요하므로 바이너리를 배치한 위치를 기록해 두십시오.

### 2. AzCopy 지원을 사용하여 CTT(Content Transfer Tool) 릴리스 설치 {#install-ctt-azcopy-support}

AzCopy 지원은 CTT 1.5.4 릴리스에 포함되어 있습니다. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털에서 최신 CTT 릴리스를 다운로드할 수 있습니다.

### 3. azcopy.config 파일 구성 {#configure-azcopy-config-file}

소스 AEM 인스턴스의 crx-quickstart/cloud-migration에서 azcopy.config 라는 새 파일을 만듭니다.

이 구성 파일의 내용은 소스 AEM 인스턴스가 Azure 또는 Amazon S3 데이터 저장소를 사용하는지에 따라 달라집니다.

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage-data}

azcopy.config 파일에는 다음 속성이 포함되어야 합니다(인스턴스에 올바른 azCopyPath 및 azureSas를 사용해야 함).

>[!NOTE]
>
> Blob 저장소 컨테이너에 대한 쓰기 액세스 권한을 부여하지 않고 읽기 및 목록 권한만 가진 새 SAS URI를 생성할 수 있습니다.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3 데이터 저장소 {#amazon-sdata-store}

azcopy.config 파일에는 다음 속성이 포함되어야 합니다(인스턴스에 올바른 값을 사용해야 함).

>[!NOTE]
>
> 인스턴스에서 IAM 역할을 사용하여 AEM에서 S3에 액세스할 수 있도록 하는 경우 S3 버킷에 대해 ListBucket 및 GetObject 작업이 활성화된 정책과 사용자를 만들어야 합니다. 설정되면 이 사용자의 액세스 키와 비밀 키를 사용합니다.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

### 4. AzCopy로 추출 {#extracting-azcopy}

위의 구성 파일이 준비되면 AzCopy 사전 복사 단계는 모든 후속 추출의 일부로 실행됩니다. 이 파일이 실행되지 않도록 하려면 이 파일의 이름을 바꾸거나 제거할 수 있습니다.

1. CTT UI에서 추출을 시작합니다. 자세한 내용은 [컨텐츠 전송 도구 실행](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool) 및 [추출 프로세스](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process)를 참조하십시오.
1. 추출 로그에 다음 줄이 인쇄되었는지 확인합니다.

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

축하합니다! 이 로그 항목은 구성이 유효하다고 간주되었으며 AzCopy가 현재 소스 컨테이너에서 마이그레이션 컨테이너로 모든 블롭을 복사하고 있음을 의미합니다.

AzCopy의 로그 항목은 추출 로그에 나타나고 c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy 사전 복사] 가 접두사로 추가됩니다.

>[!CAUTION]
>
> 추출 후 처음 몇 분 동안 문제 징후가 있는지 추출 로그를 자세히 확인합니다. 예를 들어, 소스 Azure 컨테이너를 찾을 수 없는 경우 기록할 내용은 다음과 같습니다.


```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

AzCopy에 문제가 발생하면 즉시 추출이 실패하며 추출 로그에 오류에 대한 세부 정보가 포함됩니다.

오류 전에 복사된 모든 블롭은 이후 실행 시 AzCopy에 의해 자동으로 생략되며 다시 복사할 필요가 없습니다.

### 5. AzCopy를 사용한 수집 {#ingesting-azcopy}

컨텐츠 전송 도구 1.5.4가 릴리스된 후 작성자 처리에 AzCopy 지원을 추가했습니다.

>[!NOTE]
>작성자 수집만 먼저 실행하는 것이 좋습니다. 이 경우 나중에 실행될 때 게시 수집 속도가 빨라집니다.

수집 중에 AzCopy를 활용하려면 AEM에서 버전 2021.6.5561 이상의 Cloud Service 버전으로 사용해야 합니다.

CTT UI에서 작성자 수집을 시작합니다. 자세한 내용은 [수집 프로세스](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process)를 참조하십시오.
AzCopy의 로그 항목이 수집 로그에 나타납니다. 이러한 기능은 다음과 같습니다.

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
