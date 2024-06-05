---
title: AEM as a Cloud Service에 대한 로그 전달
description: AEM에서 Splunk 및 기타 로깅 공급업체로의 로그 전달에 대해 as a Cloud Service으로 알아보기
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 3%

---

# 로그 전달 {#log-forwarding}

>[!NOTE]
>
>이 기능은 아직 릴리스되지 않았으며 일부 로깅 대상은 릴리스 시점에 사용하지 못할 수 있습니다. 그동안 로그를 전달할 지원 티켓을 열 수 있습니다. **스플렁크**&#x200B;에 설명된 대로 [기록 문서](/help/implementing/developing/introduction/logging.md).

로깅 공급업체나 로깅 제품 호스트에 대한 라이센스가 있는 고객은 AEM, Apache/Dispatcher 및 CDN 로그를 관련 로깅 대상으로 전달할 수 있습니다. AEM as a Cloud Service은 다음 로깅 대상을 지원합니다.

* Azure Blob 저장소
* DataDog
* Elasticsearch 또는 OpenSearch
* HTTPS
* 스플렁크

로그 전달은 Git에서 구성을 선언하고 Cloud Manager 구성 파이프라인을 통해 프로덕션(샌드박스가 아닌) 프로그램의 개발, 스테이지 및 프로덕션 환경 유형에 배포하여 셀프서비스 방식으로 구성됩니다.

로깅 대상으로 전송된 로그와 관련된 네트워크 대역폭은 조직의 네트워크 I/O 사용의 일부로 간주됩니다.


## 이 문서를 구성하는 방식 {#how-organized}

이 문서는 다음 방법으로 구성됩니다.

* 설정 - 모든 로깅 대상에 대해 공통입니다.
* 대상 구성 로깅 - 각 대상의 형식이 약간 다릅니다.
* 고급 네트워킹 - 전용 이그레스 또는 VPN을 통해 AEM 및 Apache/Dispatcher 로그 전송


## 설정 {#setup}

1. Git의 프로젝트에서 최상위 폴더에 다음 폴더 및 파일 구조를 만듭니다.

   ```
   config/
        logForwarding.yaml
   ```

1. logForwarding.yaml에는 메타데이터와 다음 형식과 유사한 구성이 포함되어야 합니다(예제로 Splunk 사용).

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

   다음 **종류** 매개 변수는 LogForwarding으로 설정해야 합니다. 버전은 스키마 버전(1)으로 설정해야 합니다.

   구성의 토큰(예: `${{SPLUNK_TOKEN}}`)는 비밀을 나타내며 Git에 저장해서는 안 됩니다. 대신 Cloud Manager로 선언합니다.  [환경 변수](/help/implementing/cloud-manager/environment-variables.md) 유형 **비밀**. 다음을 선택하십시오. **모두** 적용된 서비스 필드의 드롭다운 값으로, 로그를 작성자, 게시 및 미리보기 계층에 전달할 수 있습니다.

   추가 정보를 포함하여 cdn 로그와 다른 모든 항목(AEM 및 apache 로그) 간에 다른 값을 설정할 수 있습니다 **cdn** 및/또는 **aem** 다음 이후 차단 **기본값** 블록입니다. 여기서 속성은 다음에 정의된 속성을 재정의할 수 있습니다. **기본값** 블록, 활성화된 속성만 필요합니다. 아래 예제에서 보듯이 CDN 로그에 대해 다른 Splunk 인덱스를 사용하는 것이 사용 사례일 수 있습니다.

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

   또 다른 시나리오는 CDN 로그 또는 기타 모든 로그(AEM 및 apache 로그)의 전달을 비활성화하는 것입니다. 예를 들어 CDN 로그만 전달하려면 다음을 구성할 수 있습니다.

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
      
```

고려 사항:

* 특정 클라우드 공급자와의 통합 없이 API 키를 만듭니다.


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
```

고려 사항:

* 자격 증명의 경우 계정 자격 증명이 아닌 배포 자격 증명을 사용해야 합니다. 다음은 이 이미지와 유사할 수 있는 화면에서 생성된 자격 증명입니다.

![탄력적인 배포 자격 증명](/help/implementing/developing/introduction/assets/ec-creds.png)

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

## 고급 네트워킹 {#advanced-networking}

로깅 대상에 대한 트래픽을 잠그는 조직 요구 사항이 있는 경우 통과하도록 로그 전달을 구성할 수 있습니다 [고급 네트워킹](/help/security/configuring-advanced-networking.md). 선택 사항을 사용하는 아래 세 가지 고급 네트워킹 유형에 대한 패턴을 참조하십시오 `port` 매개 변수, `host` 매개 변수.

### 유연한 포트 이그레스 {#flex-port}

로그 트래픽이 443 이외의 포트(예: 아래 8443)로 이동하는 경우 다음과 같이 고급 네트워킹을 구성합니다.

```
{
    "portForwards": [
        {
            "name": "mylogging.service.logger.com",
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
      host: "proxy.tunnel"
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
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
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
      host: "proxy.tunnel"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### VPN {#vpn}

로그 트래픽이 VPN을 통과해야 하는 경우 다음과 같이 고급 네트워킹을 구성합니다.

```
{
    "portForwards": [
        {
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
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
      host: "mylogging.service.com"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```
