---
title: AEM as a Cloud Service에 대한 로그 전달
description: AEM as a Cloud Service의 Splunk 및 기타 로깅 공급업체에 로그를 전달하는 방법에 대해 알아봅니다
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 29d2a759f5b3fdbccfa6a219eebebe2b0443d02e
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 1%

---

# 로그 전달 {#log-forwarding}

>[!NOTE]
>
>이 기능은 아직 릴리스되지 않았으며 일부 로깅 대상은 릴리스 시점에 사용하지 못할 수 있습니다. 그동안 로그를 전달할 지원 티켓을 열 수 있습니다. **스플렁크**&#x200B;에 설명된 대로 [기록 문서](/help/implementing/developing/introduction/logging.md).

로깅 공급업체나 로깅 제품 호스트에 대한 라이센스가 있는 고객은 AEM 로그(Apache/Dispatcher 포함) 및 CDN 로그를 관련 로깅 대상으로 전달할 수 있습니다. AEM as a Cloud Service은 다음 로깅 대상을 지원합니다.

* Azure Blob 저장소
* DataDog
* Elasticsearch 또는 OpenSearch
* HTTPS
* 스플렁크

로그 전달은 Git에서 구성을 선언하고 Cloud Manager 구성 파이프라인을 통해 프로덕션(샌드박스가 아닌) 프로그램의 개발, 스테이지 및 프로덕션 환경 유형에 배포하여 셀프서비스 방식으로 구성됩니다.

AEM 및 Apache/Dispatcher 로그를 전용 이그레스 IP와 같은 AEM의 고급 네트워킹 인프라를 통해 라우팅하는 옵션이 있습니다.

로깅 대상으로 전송된 로그와 관련된 네트워크 대역폭은 조직의 네트워크 I/O 사용의 일부로 간주됩니다.


## 이 문서를 구성하는 방식 {#how-organized}

이 문서는 다음 방법으로 구성됩니다.

* 설정 - 모든 로깅 대상에 대해 공통입니다.
* 대상 구성 로깅 - 각 대상의 형식이 약간 다릅니다.
* 로그 항목 형식 - 로그 항목 형식에 대한 정보
* 고급 네트워킹 - 전용 이그레스 또는 VPN을 통해 AEM 및 Apache/Dispatcher 로그 전송


## 설정 {#setup}

1. Git의 프로젝트에서 최상위 폴더에 다음 폴더 및 파일 구조를 만듭니다.

   ```
   config/
        logForwarding.yaml
   ```

1. `logForwarding.yaml` 에는 메타데이터와 다음 형식과 유사한 구성이 포함되어야 합니다(예제로 Splunk 사용).

   ```
   kind: "LogForwarding"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     splunk:
       default:
         enabled: true
         host: "splunk-host.example.com"
         token: "${{SPLUNK_TOKEN}}"
         index: "AEMaaCS"
   ```

   다음 **종류** 매개 변수는 다음으로 설정해야 합니다. `LogForwarding` 버전은 1인 스키마 버전으로 설정해야 합니다.

   구성의 토큰(예: `${{SPLUNK_TOKEN}}`)는 비밀을 나타내며 Git에 저장해서는 안 됩니다. 대신 Cloud Manager으로 선언하십시오.  [환경 변수](/help/implementing/cloud-manager/environment-variables.md) 유형 **비밀**. 다음을 선택하십시오. **모두** 적용된 서비스 필드의 드롭다운 값으로, 로그를 작성자, 게시 및 미리보기 계층에 전달할 수 있습니다.

   추가 정보를 포함하여 CDN 로그와 AEM 로그(Apache/Dispatcher 포함) 간에 다른 값을 설정할 수 있습니다 **cdn** 및/또는 **aem** 다음 이후 차단 **기본값** 블록입니다. 여기서 속성은 다음에 정의된 속성을 재정의할 수 있습니다. **기본값** 블록, 활성화된 속성만 필요합니다. 아래 예제에서 보듯이 CDN 로그에 대해 다른 Splunk 인덱스를 사용하는 것이 사용 사례일 수 있습니다.

   ```
      kind: "LogForwarding"
      version: "1"
      metadata:
        envTypes: ["dev"]
      data:
        splunk:
          default:
            enabled: true
            host: "splunk-host.example.com"
            token: "${{SPLUNK_TOKEN}}"
            index: "AEMaaCS"
          cdn:
            enabled: true
            token: "${{SPLUNK_TOKEN_CDN}}"
            index: "AEMaaCS_CDN"   
   ```

   또 다른 시나리오는 CDN 로그 또는 AEM 로그(Apache/Dispatcher 포함)의 전달을 비활성화하는 것입니다. 예를 들어 CDN 로그만 전달하려면 다음을 구성할 수 있습니다.

   ```
      kind: "LogForwarding"
      version: "1"
      metadata:
        envTypes: ["dev"]
      data:
        splunk:
          default:
            enabled: true
            host: "splunk-host.example.com"
            token: "${{SPLUNK_TOKEN}}"
            index: "AEMaaCS"
          aem:
            enabled: false
   ```

1. RDE 이외의 환경 유형(현재 지원되지 않음)의 경우 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 생성합니다.

   * [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)을 참조하십시오.
   * [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)을 참조하십시오.

## 대상 구성 로깅 중 {#logging-destinations}

특정 고려 사항과 함께 지원되는 로깅 대상에 대한 구성이 아래에 나와 있습니다.

### Azure Blob 저장소 {#azureblob}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  azureBlob:
    default:
      enabled: true       
      storageAccountName: "example_acc"
      container: "aem_logs"
      sasToken: "${{AZURE_BLOB_SAS_TOKEN}}
      
```

인증에 SAS 토큰을 사용해야 합니다. 공유 액세스 토큰 페이지가 아닌 공유 액세스 서명 페이지에서 만들어야 하며 다음 설정으로 구성해야 합니다.

* 허용된 서비스: Blob을 선택해야 합니다.
* 허용된 리소스: 개체를 선택해야 합니다.
* 허용된 권한: 쓰기, 추가, 만들기 를 선택해야 합니다.
* 유효한 시작 및 만료 날짜/시간.

다음은 샘플 SAS 토큰 구성의 스크린샷입니다.

![Azure Blob SAS 토큰 구성](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

#### Azure Blob 저장소 CDN 로그 {#azureblob-cdn}

전역적으로 분산된 각 로깅 서버는 `aemcdn` 폴더를 삭제합니다. 파일이 만들어지면에 더 이상 추가되지 않습니다. 파일 이름 형식은 YYYY-MM-DDThh입니다.:mm:ss.sss-uniqueid.log. 예: 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

예를 들어, 특정 시점에서 다음과 같은 작업을 수행할 수 있습니다.

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

30초 후:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

각 파일에는 여러 JSON 로그 항목이 포함되어 있으며 각 항목은 별도의 줄에 있습니다. 로그 항목 형식은 다음에 설명되어 있습니다 [기록 문서](/help/implementing/developing/introduction/logging.md), 각 로그 항목에는 다음에 언급된 추가 속성도 포함됩니다. [로그 항목 형식](#log-format) 아래 섹션.

#### Azure Blob 저장소 AEM 로그 {#azureblob-aem}

AEM 로그(Apache/Dispatcher 포함)는 다음 명명 규칙을 사용하여 폴더 아래에 표시됩니다.

* aemaccess
* aemerror
* aemdispatcher
* httpdaccess
* httpdererror

각 폴더 아래에 하나의 파일이 만들어지고 추가됩니다. 고객은 이 파일의 크기가 너무 커지지 않도록 처리 및 관리를 담당합니다.

다음에서 로그 항목 형식 확인: [기록 문서](/help/implementing/developing/introduction/logging.md). 로그 항목에는 다음에 언급된 추가 속성도 포함됩니다. [로그 항목 형식](#log-formats) 아래 섹션.


### Datadog {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  dataDog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      tags:
         tag1: value1
         tag2: value2
      
```

고려 사항:

* 특정 클라우드 공급자와의 통합 없이 API 키를 만듭니다.
* 태그 속성은 선택 사항입니다.


### Elasticsearch 및 OpenSearch {#elastic}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  elasticsearch:
    default:
      enabled: true
      host: "example.com"
      user: "${{ELASTICSEARCH_USER}}"
      password: "${{ELASTICSEARCH_PASSWORD}}"
      pipeline: "ingest pipeline name"
```

고려 사항:

* 자격 증명의 경우 계정 자격 증명이 아닌 배포 자격 증명을 사용해야 합니다. 다음은 이 이미지와 유사할 수 있는 화면에서 생성된 자격 증명입니다.

![탄력적인 배포 자격 증명](/help/implementing/developing/introduction/assets/ec-creds.png)

* 선택적 파이프라인 속성은 로그 항목을 적절한 인덱스로 라우팅하도록 구성할 수 있는 Elasticsearch 또는 OpenSearch 수집 파이프라인의 이름으로 설정되어야 합니다. 파이프라인의 프로세서 유형을 로 설정해야 합니다. *script* 스크립트 언어는 다음으로 설정해야 합니다. *고통 없이*. 다음은 aemaccess_dev_26_06_2024와 같은 인덱스로 로그 항목을 라우팅하는 샘플 스크립트 스니펫입니다.

```
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

#### HTTPS CDN 로그 {#https-cdn}

웹 요청(POST)은 로그 항목의 배열인 JSON 페이로드와 함께 연속적으로 전송되며 로그 항목 형식은 다음에 설명되어 있습니다. [기록 문서](/help/implementing/developing/introduction/logging.md#cdn-log). 추가 속성은에 설명되어 있습니다. [로그 항목 형식](#log-formats) 아래 섹션.

이름이 인 속성도 있습니다. `sourcetype`, 값으로 설정됨 `aemcdn`.

>[!NOTE]
>
> 첫 번째 CDN 로그 항목이 전송되기 전에 HTTP 서버는 경로로 전송된 요청을 성공적으로 완료해야 합니다 ``wellknownpath`` 다음으로 응답해야 함 ``*``.


#### HTTPS AEM 로그 {#https-aem}

AEM 로그(apache/dispatcher 포함)의 경우 웹 요청(POST)이 로그 항목의 배열인 json 페이로드와 함께 지속적으로 전송되며, 여기에 설명된 다양한 로그 항목 형식이 사용됩니다. [기록 문서](/help/implementing/developing/introduction/logging.md). 추가 속성은에 설명되어 있습니다. [로그 항목 형식](#log-format) 아래 섹션.

이름이 인 속성도 있습니다. `sourcetype`: 다음 값 중 하나로 설정됩니다.

* aemaccess
* aemerror
* aemdispatcher
* httpdaccess
* httpdererror

### 스플렁크 {#splunk}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

<!--
### Sumo Logic {#sumologic}

   ```
   kind: "LogForwarding"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     splunk:
       default:
         enabled: true
         host: "https://collectors.de.sumologic.com"
         uri: "/receiver/v1/http"
         privateKey: "${{SomeOtherToken}}"
   
   ```   
-->

## 로그 항목 형식 {#log-formats}

일반 참조 [기록 문서](/help/implementing/developing/introduction/logging.md) 각 로그 유형의 형식용(CDN 로그 및 Apache/Dispatcher을 포함한 AEM 로그)

여러 프로그램 및 환경의 로그를 동일한 로깅 대상으로 전달할 수 있으므로 로깅 문서에 설명된 출력 외에 각 로그 항목에는 다음 속성이 포함됩니다.

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

예를 들어 속성은 다음 값을 가질 수 있습니다.

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## 고급 네트워킹 {#advanced-networking}

>[!NOTE]
>
>이 기능은 아직 얼리 어답터에게 준비되지 않았습니다.


일부 조직에서는 로깅 대상에서 수신할 수 있는 트래픽을 제한하도록 선택합니다.

CDN 로그의 경우에서 설명한 대로 IP 주소를 허용 목록에 추가할 수 있습니다 [이 문서](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). 공유 IP 주소 목록이 너무 크면 (Adobe이 아닌) Azure Blob Store에 트래픽을 보내는 것이 좋습니다. 여기서 논리를 작성하여 전용 IP에서 로그를 최종 대상으로 보낼 수 있습니다.

AEM 로그(Apache/Dispatcher 포함)의 경우 다음을 거치도록 로그 전달을 구성할 수 있습니다 [고급 네트워킹](/help/security/configuring-advanced-networking.md). 선택 사항을 사용하는 아래 세 가지 고급 네트워킹 유형에 대한 패턴을 참조하십시오 `port` 매개 변수, `host` 매개 변수.

### 유연한 포트 이그레스 {#flex-port}

로그 트래픽이 443 이외의 포트(예: 아래 8443)로 이동하는 경우 다음과 같이 고급 네트워킹을 구성합니다.

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 8443, # something other than 443
            "portOrig": 30443
        }    
    ]
}
```

와 같이 yaml 파일을 구성합니다.

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      host: "${{AEM_PROXY_HOST}}"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### 전용 이그레스 IP {#dedicated-egress}


로그 트래픽이 전용 이그레스 IP에서 나와야 하는 경우 다음과 같이 고급 네트워킹을 구성합니다.

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443, 
            "portOrig": 30443
        }    
    ]
}
```

와 같이 yaml 파일을 구성합니다.

```
      
kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443    
```

### VPN {#vpn}

로그 트래픽이 VPN을 통과해야 하는 경우 다음과 같이 고급 네트워킹을 구성합니다.

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443,
            "portOrig": 30443
        }    
    ]
}

kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443     
```
