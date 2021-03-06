---
title: 로그 액세스 및 관리
description: AEM as a Cloud Service에서 개발 프로세스를 지원하기 위해 로그에 액세스하고 관리하는 방법을 알아봅니다.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: a9303c659730022b7417fc9082dedd26d7cbccca
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 3%

---


# 로그 액세스 및 관리 {#manage-logs}

AEM as a Cloud Service에서 개발 프로세스를 지원하기 위해 로그에 액세스하고 관리하는 방법을 알아봅니다.

을 사용하여 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다 **환경** 카드로부터 **개요** 페이지 또는 환경 세부 사항 페이지를 참조하십시오.

## 로그 다운로드 {#download-logs}

다음 단계에 따라 로그를 다운로드합니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **환경** 카드로부터 **개요** 페이지.

1. 선택 **다운로드 로그** 를 클릭합니다.

   ![로그 메뉴 항목 다운로드](assets/download-logs1.png)

1. 에서 **다운로드 로그** 대화 상자에서 적절한 를 선택합니다 **서비스** 드롭다운 메뉴에서

   ![로그 다운로드 대화 상자](assets/download-preview.png)

1. 서비스를 선택하면 검색할 로그 옆에 있는 다운로드 아이콘을 클릭합니다.

또한 **환경** 페이지.

![환경 화면의 로그](assets/download-logs.png)

## API를 통한 로그 {#logs-through-api}

UI를 통해 로그를 다운로드하는 것 외에도 API 및 명령줄 인터페이스를 통해 로그를 사용할 수 있습니다.

특정 환경에 대한 로그 파일을 다운로드하려면 명령은 다음과 비슷합니다.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

명령줄 인터페이스를 통해 로그를 추적할 수도 있습니다.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

이 예에서 환경 ID(1884) 및 사용 가능한 서비스 또는 로그 이름 옵션을 얻으려면 다음 명령을 사용할 수 있습니다.

```shell
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

### 추가 리소스 {#resources}

Cloud Manager API 및 Adobe I/O CLI에 대한 자세한 내용은 다음 추가 리소스를 참조하십시오.

* [Cloud Manager API 설명서](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)
* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)
