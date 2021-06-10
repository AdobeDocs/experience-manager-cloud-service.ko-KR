---
title: 로그 관리 - Cloud Service
description: 로그 관리 - Cloud Service
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: 8a70a343be8a6843436f1df26adae5b1935ad4c3
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 6%

---

# 로그 액세스 및 관리 {#manage-logs}

사용자는 환경 카드를 사용하여 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다. 사용자는 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다.

## 로그 {#download-logs} 다운로드

이러한 파일은 **개요** 페이지의 **환경** 카드에서 UI를 통해 다운로드할 수 있습니다.

![](assets/download-logs1.png)

또는 환경 세부 사항 페이지에서 다음을 수행합니다.

![](assets/download-logs.png)

>[!NOTE]
>열려 있는 위치에 관계없이 동일한 대화 상자가 표시되고 개별 로그 파일을 다운로드할 수 있습니다.

![](assets/download-logs2.png)

## 미리 보기 서비스 {#download-preview-service}에 대한 로그 다운로드

미리 보기 서비스에 대한 로그를 다운로드하려면 아래 단계를 따르십시오

1. Cloud Manager의 **개요** 페이지에서 **환경** 카드로 이동합니다.

1. **에서**&#x200B;다운로드 로그&#x200B;**를 선택합니다.** 메뉴.

1. **서비스** 드롭다운 메뉴에서 **미리 보기** 또는 **Dispatcher 미리 보기**&#x200B;를 선택한 후 다운로드 아이콘을 클릭합니다.

   >[!NOTE]
   >이 작업은 환경 세부 사항 페이지에서 수행할 수도 있습니다.

   ![](assets/download-preview.png)


## API {#logs-through-api}를 통해 로그

UI를 통해 로그를 다운로드하는 것 외에도 API 및 명령줄 인터페이스를 통해 로그를 사용할 수 있습니다.

예를 들어, 특정 환경에 대한 로그 파일을 다운로드하려면 명령은

```java
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

다음 명령을 사용하면 로그를 추적할 수 있습니다.

```java
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

환경 ID(이 경우 1884)와 사용 가능한 서비스 또는 로그 이름 옵션을 가져오려면 다음을 사용할 수 있습니다.

```java
$ aio cloudmanager:list-environments
Environment Id Name                     Type  Description                          
1884           FoundationInternal_dev   dev   Foundation Internal Dev environment  
1884           FoundationInternal_stage stage Foundation Internal STAGE environment
1884           FoundationInternal_prod  prod  Foundation Internal Prod environment
 
 
$ aio cloudmanager:list-available-log-options 1884
Environment Id Service    Name         
1884           author     aemerror     
1884           author     aemrequest   
1884           author     aemaccess    
1884           publish    aemerror     
1884           publish    aemrequest   
1884           publish    aemaccess    
1884           dispatcher httpderror   
1884           dispatcher aemdispatcher
1884           dispatcher httpdaccess
```

>[!NOTE]
>**로그 다운로드**&#x200B;는 UI와 API를 모두 통해 사용할 수 있지만 **로그 추적**&#x200B;은 API/CLI만 사용할 수 있습니다.

### 추가 리소스 {#resources}

Cloud Manager API 및 Adobe I/O CLI에 대한 자세한 내용은 다음 추가 리소스를 참조하십시오.

* [Cloud Manager API 설명서](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)
* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)
