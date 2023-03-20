---
title: 대형 콘텐츠 저장소 처리
description: 이 섹션에서는 대용량 컨텐츠 리포지토리의 처리에 대해 설명합니다
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
source-git-commit: cf09c7774b633ae2cf1c5b28fee2bd8191d80bb3
workflow-type: tm+mt
source-wordcount: '1846'
ht-degree: 8%

---

# 대형 콘텐츠 저장소 처리 {#handling-large-content-repositories}

## 개요 {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="대형 콘텐츠 저장소 처리"
>abstract="콘텐츠 전송 활동의 추출 및 수집 단계를 크게 가속화하여 콘텐츠를 AEM as a Cloud Service로 이동하기 위해 CTT는 선택 사항인 사전 복사 단계로 AzCopy를 활용할 수 있습니다. 이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3 또는 Azure Blob 저장소에서 마이그레이션 세트 Blob 저장소로 Blob을 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 Blob 저장소의 Blob을 대상 AEM as a Cloud Service Blob 저장소로 복사합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step" text="사전 복사 단계로 AzCopy 시작"

CTT(컨텐츠 전송 도구)를 사용하여 많은 수의 블롭을 복사하는 데 여러 날이 걸릴 수 있습니다.
컨텐츠 전송 활동의 추출 및 수집 단계를 크게 단축하여 컨텐츠를 AEM as a Cloud Service으로 이동하려면 CTT를 활용할 수 있습니다 [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 는 선택적 사전 복사 단계입니다. 이 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3, Azure Blob 저장 공간 데이터 저장소 또는 파일 데이터 저장소를 사용하도록 구성된 경우 사용할 수 있습니다. 사전 복사 단계는 첫 번째 전체 추출 및 통합에 가장 효과적입니다. 그러나 후속 추가 작업에 사전 복사를 사용하는 것은 권장되지 않습니다(추가 크기가 200GB 미만인 경우). 이 경우 전체 프로세스에 시간을 추가할 수 있습니다. 이 사전 단계가 구성되면 추출 단계에서 AzCopy는 Amazon S3, Azure Blob 저장소 또는 파일 데이터 저장소에서 마이그레이션 세트 blob 저장소로 블롭을 복사합니다. 수집 단계에서 AzCopy는 마이그레이션 세트 Blob 저장소의 Blob을 대상 AEM as a Cloud Service Blob 저장소로 복사합니다.

## 시작하기 전에 중요한 고려 사항 {#important-considerations}

시작하기 전에 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* CTT 버전 2.0.16부터 번들이 설치되면 사전 복사 설정이 자동으로 수행됩니다. 또한 마이그레이션 세트 크기가 200GB를 초과하는 경우 추출 프로세스는 자동으로 사전 복사 기능을 활용합니다. azcopy.config 파일은 crx-quickstart/cloud-migration/ 디렉토리에 생성됩니다. CTT 버전 2.0.16 이상을 사용하는 경우에는 사전 복사 설정을 수동으로 수행하지 않아도 됩니다.

* 소스 AEM 버전은 6.3 - 6.5여야 합니다.

* 소스 AEM 데이터 저장소는 Amazon S3 또는 Azure Blob 저장소를 사용하도록 구성되어 있습니다. 자세한 내용은 [AEM 6에서 노드 저장소 및 데이터 저장소 구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html).

* 각 마이그레이션 세트는 전체 데이터 저장소를 복사하므로 단일 마이그레이션 세트만 사용해야 합니다.

* 설치 액세스 권한이 필요합니다 [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 소스 AEM 인스턴스를 실행 중인 인스턴스(또는 VM)에서 사용할 수 있습니다.

* 데이터 저장소 가비지 수집이 소스의 이전 7일 이내에 실행되었습니다. 자세한 내용은 [데이터 저장소 가비지 수집](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#data-store-garbage-collection).

### 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob 저장 공간 데이터 저장소를 사용하도록 구성된 경우 추가적인 고려 사항 {#additional-considerations-amazons3-azure}

* Amazon S3 및 Azure Blob 저장소에서 데이터를 전송하는 데 드는 비용이 있으므로 전송 비용은 기존 저장소 컨테이너의 총 데이터 양(AEM에서 참조되었는지 여부에 상관없이)과 상대적입니다. 을(를) 참조하십시오. [Amazon S3](https://aws.amazon.com/s3/pricing/) 및 [Azure Blob 저장소](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) 자세한 내용

* 기존 소스 Amazon S3 버킷에 대한 액세스 키 및 비밀 키 쌍 또는 기존 소스 Azure Blob 저장소 컨테이너의 SAS URI가 필요합니다(읽기 전용 액세스 권한이 양호함).

### 소스 AEM 인스턴스가 파일 데이터 저장소를 사용하도록 구성된 경우 추가적인 고려 사항 {#additional-considerations-aem-instance-filedatastore}

* 로컬 시스템의 사용 가능한 공간이 원본 데이터 저장소1/256 크기보다 훨씬 크어야 합니다. 예를 들어 데이터 저장소 크기가 3TB이면 11.72GB보다 큰 여유 공간이 `crx-quickstart/cloud-migration` AzCopy를 사용할 소스의 폴더입니다. 적어도 소스 시스템의 여유 공간은 1GB여야 합니다. 사용 가능한 공간은 `df -h` Linux 인스턴스의 명령 및 Windows 인스턴스의 dir 명령

* AzCopy가 활성화된 상태에서 추출을 실행할 때마다 전체 파일 데이터 저장소가 변환되어 클라우드 마이그레이션 컨테이너에 복사됩니다. 마이그레이션 세트가 데이터 저장소 크기보다 상당히 작은 경우 AzCopy 추출이 최적의 방법이 아닙니다.

* AzCopy를 사용하여 기존 데이터 저장소를 복사하면 델타 또는 추가 압출을 비활성화합니다.

## AzCopy를 사전 복사 단계로 사용하도록 설정 {#setting-up-pre-copy-step}

>[!NOTE]
>CTT 버전 2.0.16부터 번들이 설치되면 사전 복사 설정이 자동으로 수행됩니다. 또한 마이그레이션 세트 크기가 200GB를 초과하는 경우 추출 프로세스는 자동으로 사전 복사 기능을 활용합니다. azcopy.config 파일은 crx-quickstart/cloud-migration/ 디렉토리에 생성됩니다. 파일의 구성을 수동으로 업데이트하려면 아래 섹션을 검토하십시오.

이 섹션을 따라 컨텐츠 전송 도구를 사용하여 컨텐츠를 AEM as a Cloud Service으로 마이그레이션하도록 AzCopy를 사전 복사 단계로 사용하도록 설정하는 방법을 알아보십시오.

### 0. 데이터 저장소에 있는 모든 콘텐츠의 총 크기를 결정합니다 {#determine-total-size}

다음 두 가지 이유로 데이터 저장소의 총 크기를 결정하는 것이 중요합니다.

* 소스 AEM이 파일 데이터 저장소를 사용하도록 구성된 경우 로컬 시스템의 사용 가능한 공간이 소스 데이터 저장소1/256 크기보다 훨씬 커야 합니다.

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage}

Azure 포털의 기존 컨테이너 속성 페이지에서 **크기 계산** 단추을 눌러 컨테이너에 있는 모든 컨텐츠의 크기를 결정합니다. 예:

![이미지](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 데이터 저장소 {#amazon-data}

컨테이너의 지표 탭을 사용하여 컨테이너에 있는 모든 컨텐츠의 크기를 결정할 수 있습니다. 예:


![이미지](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### 파일 데이터 저장소 {#file-data-store-determine-size}

* mac, UNIX 시스템의 경우 데이터 저장소 디렉토리에서 du 명령을 실행하여 크기를 가져옵니다.
   `du -sh [path to datastore on the instance]`을 따르지 않는 경우입니다. 예를 들어 데이터 저장소가 `/mnt/author/crx-quickstart/repository/datastore`로 지정하는 경우, 다음 명령을 실행하면 크기가 표시됩니다. `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Windows의 경우 데이터 저장소 디렉터리에서 dir 명령을 사용하여 크기를 가져옵니다.
   `dir /a/s [location of datastore]`.

### 1. AzCopy 설치 {#install-azcopy}

[AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) 는 Microsoft에서 제공하는 명령줄 도구이며 이 기능을 활성화하기 위해 소스 인스턴스에서 사용할 수 있어야 합니다.

즉, Linux x86-64 바이너리를 [AzCopy 문서 페이지](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) /usr/bin과 같은 위치로 이 명령을 해제합니다.

>[!IMPORTANT]
>나중 단계에서 바이너리에 대한 전체 경로가 필요하므로 바이너리를 배치한 위치를 기록해 두십시오.

### 2. AzCopy 지원을 통해 CTT(Content Transfer Tool) 릴리스 설치 {#install-ctt-azcopy-support}

>[!IMPORTANT]
>가장 최근에 릴리스된 CTT 버전을 사용해야 합니다.

Amazon S3, Azure Blob 저장 공간 및 파일 데이터 저장소에 대한 AzCopy 지원이 최신 CTT 릴리스에 포함되어 있습니다.
에서 CTT 최신 릴리스를 다운로드할 수 있습니다 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털.
버전 2.0.0 이상만 지원되며 최신 버전을 사용하는 것이 좋습니다.

### 3. azcopy.config 파일 구성 {#configure-azcopy-config-file}

소스 AEM 인스턴스에서 `crx-quickstart/cloud-migration`에서 라는 새 파일을 만듭니다. `azcopy.config`.

>[!NOTE]
>이 구성 파일의 내용은 소스 AEM 인스턴스가 Azure 또는 Amazon S3 데이터 저장소를 사용하는지 또는 파일 데이터 저장소를 사용하는지에 따라 달라집니다.

#### Azure Blob 저장소 데이터 저장소 {#azure-blob-storage-data}

azcopy.config 파일에는 다음 속성이 포함되어야 합니다(인스턴스에 올바른 azCopyPath 및 azureSas를 사용해야 함).

>[!NOTE]
>
> 기존 Blob 저장소 컨테이너에 대한 쓰기 액세스 권한을 부여하지 않고 읽기 및 목록 권한만 있는 새 SAS URI를 생성할 수 있습니다.

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

#### 파일 데이터 저장소 {#file-data-store-azcopy-config}

사용자 `azcopy.config` 파일에는 파일 데이터 저장소의 위치를 가리키는 azCopyPath 속성과 선택적 repository.home 속성이 있어야 합니다. 인스턴스에 올바른 값을 사용하십시오.
파일 데이터 저장소

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

azCopyPath 속성은 소스 AEM 인스턴스에 azCopy 명령줄 도구가 설치된 위치의 전체 경로를 포함해야 합니다. azCopyPath 속성이 없으면 Blob 사전 복사 단계가 수행되지 않습니다.

If `repository.home` azcopy.config에 속성이 없으면 기본 데이터 저장소 위치가 없습니다 `/mnt/crx/author/crx-quickstart/repository/datastore` 는 사전 복사를 수행하는 데 사용됩니다.

### 4. AzCopy로 추출 {#extracting-azcopy}

위의 구성 파일이 준비되면 AzCopy 사전 복사 단계는 모든 후속 추출의 일부로 실행됩니다. 이 파일이 실행되지 않도록 하려면 이 파일의 이름을 바꾸거나 제거할 수 있습니다.

>[!NOTE]
>AzCopy가 올바르게 구성되지 않으면 로그에 다음 메시지가 표시됩니다.
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. CTT UI에서 추출을 시작합니다. 을(를) 참조하십시오. [컨텐츠 전송 도구 시작하기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) 그리고 [추출 프로세스](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) 자세한 내용

1. 추출 로그에 다음 줄이 인쇄되었는지 확인합니다.

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

축하합니다! 이 로그 항목은 구성이 유효하다고 간주되었으며 AzCopy가 현재 소스 컨테이너에서 마이그레이션 컨테이너로 모든 블롭을 복사하고 있음을 의미합니다.

AzCopy의 로그 항목이 추출 로그에 나타나고 c.a.g.s.m.azcopy.AzCopyBlobPreCopy - 접두사가 추가됩니다. [AzCopy 사전 복사]

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

#### 파일 데이터 저장소 {#file-data-store-extract}

소스 파일 dataStore에 대해 AzCopy가 실행 중인 경우 다음과 같은 메시지가 로그에 표시되어야 합니다. 이는 폴더가 처리됨을 나타냅니다.
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. AzCopy를 사용한 수집 {#ingesting-azcopy}

을(를) 참조하십시오. [Target에 컨텐츠 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
&quot;새 수집&quot; 대화 상자에서 AzCopy(사전 복사)를 사용하거나 사용하지 않는 방법에 대한 지침을 포함하여 CAM(Cloud Acceleration Manager)에서 대상으로 컨텐츠를 수집하는 방법에 대한 일반적인 정보입니다.

수집 중에 AzCopy를 활용하려면 버전 2021.6.5561 이상인 AEM as a Cloud Service 버전을 사용해야 합니다.

진행 상황을 알려면 Cloud Acceleration Manager의 &quot;수집 작업&quot; 목록 및 수집 로그를 참조하십시오.  성공한 AzCopy 작업과 관련된 로그 항목은 다음과 같이 나타납니다(몇 가지 차이가 있을 경우 허용됨). 가끔 로그를 확인하면 문제를 조기에 발견할 수 있으며 문제를 신속하게 해결할 수 있습니다.

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

## 다음 단계 {#whats-next}

대규모 컨텐츠 저장소 처리 를 통해 컨텐츠 전송 활동의 추출 및 수집 단계를 대폭 단축하여 컨텐츠를 AEM as a Cloud Service으로 이동하는 것을 배웠다면, 이제 컨텐츠 전송 도구를 사용하여 추출 프로세스를 배울 수 있습니다. 자세한 내용은 [컨텐츠 전송 도구에서 소스에서 컨텐츠 추출](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) 컨텐츠 전송 도구에서 마이그레이션 세트를 추출하는 방법을 알아봅니다.
