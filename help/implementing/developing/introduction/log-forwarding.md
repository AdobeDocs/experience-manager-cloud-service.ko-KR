---
title: AEM as a Cloud Service에 대한 로그 전달
description: AEM as a Cloud Service의 로깅 공급업체에 로그를 전달하는 방법에 대해 알아봅니다.
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Developer
source-git-commit: 3a46db9c98fe634bf2d4cffd74b54771de748515
workflow-type: tm+mt
source-wordcount: '2478'
ht-degree: 3%

---

# 로그 전달 {#log-forwarding}

>[!NOTE]
>
>이제 로그 전달이 Adobe 지원 티켓을 제출해야 했던 기존 방법과 달리 셀프서비스 방식으로 구성됩니다. Adobe에서 로그 전달을 설정한 경우 [마이그레이션](#legacy-migration) 섹션을 참조하십시오.

로깅 공급업체에 라이센스가 있거나 로깅 제품을 호스팅하는 고객은 AEM 로그(Apache/Dispatcher 포함) 및 CDN 로그를 관련 로깅 대상에 전달할 수 있습니다. AEM as a Cloud Service은 다음 로깅 대상을 지원합니다.

<table>
  <tbody>
    <tr>
      <th>로그 기술</th>
      <th>AEM</th>
      <th>Dispatcher</th>
      <th>CDN</th>
    </tr>
    <tr>
      <td>Amazon</td>
      <td>예</td>
      <td>예</td>
      <td style="background-color: #ffb3b3;">미래</td>
    </tr>
    <tr>
      <td>Azure Blob 저장소</td>
      <td>예</td>
      <td>예</td>
      <td>예</td>
    </tr>
    <tr>
      <td>DataDog</td>
      <td>예</td>
      <td>예</td>
      <td>예</td>
    </tr>
    <tr>
      <td>Dynatrace</td>
      <td>예</td>
      <td>예</td>
      <td style="background-color: #ffb3b3;">미래</td>
    </tr>
    <tr>
      <td>Elasticsearch<br>OpenSearch</td>
      <td>예</td>
      <td>예</td>
      <td>예</td>
    </tr>
    <tr>
      <td>HTTPS</td>
      <td>예</td>
      <td>예</td>
      <td>예</td>
    </tr>
    <tr>
      <td>New Relic</td>
      <td>예</td>
      <td>예</td>
      <td style="background-color: #ffb3b3;">미래</td>
    </tr>
    <tr>
      <td>스플렁크</td>
      <td>예</td>
      <td>예</td>
      <td>예</td>
    </tr>
    <tr>
      <td>스모 논리</td>
      <td>예</td>
      <td>예</td>
      <td style="background-color: #ffb3b3;">미래</td>
    </tr>
  </tbody>
</table>

>[!NOTE]
>
> 향후 예정된 CDN 로그 기술에 대해서는 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)에 전자 메일을 보내 관심 영역을 등록하십시오.

로그 전달은 Git에서 구성을 선언하여 셀프서비스 방식으로 구성되며 Cloud Manager 구성 파이프라인을 통해 개발, 스테이지 및 프로덕션 환경 유형에 배포할 수 있습니다. 구성 파일은 명령줄 도구를 사용하여 신속한 개발 환경(RDE)에 배포될 수 있습니다.

AEM 및 Apache/Dispatcher 로그가 전용 이그레스 IP와 같은 AEM의 고급 네트워킹 인프라를 통해 라우팅되는 옵션이 있습니다.

로깅 대상으로 전송된 로그와 관련된 네트워크 대역폭은 조직의 네트워크 I/O 사용의 일부로 간주됩니다.

## 이 문서를 구성하는 방식 {#how-organized}

이 문서는 다음 방법으로 구성됩니다.

* 설정 - 모든 로깅 대상에 대해 공통입니다.
* 전송 및 고급 네트워킹 - 로깅 구성을 만들기 전에 네트워크 설정을 고려해야 합니다.
* 대상 구성 로깅 - 각 대상의 형식이 약간 다릅니다.
* 로그 항목 형식 - 로그 항목 형식에 대한 정보
* 이전 로그 전달에서 마이그레이션 - Adobe에서 이전에 설정한 로그 전달에서 셀프서비스 접근 방식으로 이동하는 방법

## 설정 {#setup}

1. 이름이 `logForwarding.yaml`인 파일을 생성합니다. [구성 파이프라인](/help/operations/config-pipeline.md#common-syntax) 문서에 설명된 대로 메타데이터가 포함되어야 합니다(**종류**&#x200B;은(는) `LogForwarding`(으)로 설정되어야 하며 버전은 &quot;1&quot;(으)로 설정되어야 합니다). 다음과 유사한 구성을 사용해야 합니다(예를 들어 Splunk 사용).

   ```yaml
   kind: "LogForwarding"
   version: "1"
   data:
     splunk:
       default:
         enabled: true
         host: "splunk-host.example.com"
         token: "${{SPLUNK_TOKEN}}"
         index: "AEMaaCS"
   ```

1. *구성 파이프라인 사용*&#x200B;에 설명된 대로 파일을 [config](/help/operations/config-pipeline.md#folder-structure) 또는 유사한 최상위 폴더 아래에 배치합니다.

1. RDE(명령줄 도구 사용) 이외의 환경 유형의 경우 [이 섹션](/help/operations/config-pipeline.md#creating-and-managing)에서 참조한 대로 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 만듭니다. 전체 스택 파이프라인 및 웹 계층 파이프라인은 구성 파일을 배포하지 않습니다.

1. 구성 배포.

구성의 토큰(예: `${{SPLUNK_TOKEN}}`)은 비밀을 나타내며 Git에 저장해서는 안 됩니다. 대신 Cloud Manager [보안 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)(으)로 선언하십시오. 로그를 작성자, 게시 및 미리보기 계층에 전달할 수 있도록 서비스 적용 필드의 드롭다운 값으로 **모두**&#x200B;를 선택해야 합니다.

**default** 블록 뒤에 추가 **cdn** 및/또는 **aem** 블록을 포함하여 CDN 로그와 AEM 로그(Apache/Dispatcher 포함) 간에 다른 값을 설정할 수 있습니다. 여기서 속성은 **default** 블록에 정의된 값을 무시할 수 있습니다. 활성화된 속성만 필요합니다. 아래 예제에서 보듯이 CDN 로그에 대해 다른 Splunk 인덱스를 사용하는 것이 사용 사례일 수 있습니다.

```yaml
   kind: "LogForwarding"
   version: "1"
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

```yaml
   kind: "LogForwarding"
   version: "1"
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

## 전송 및 고급 네트워킹 {#transport-advancednetworking}

일부 조직에서는 로깅 대상에 의해 수신될 수 있는 트래픽을 제한하도록 선택하고, 다른 조직에서는 HTTPS(443) 이외의 포트를 사용해야 할 수 있습니다.  이 경우 로그 전달 구성을 배포하기 전에 [고급 네트워킹](/help/security/configuring-advanced-networking.md)을 구성해야 합니다.

아래 표를 사용하여 포트 443을 사용하는지 여부와 고정 IP 주소에서 로그를 표시해야 하는지 여부를 기준으로 고급 네트워킹 및 로깅 구성에 대한 요구 사항을 확인할 수 있습니다.

<table>
  <tbody>
    <tr>
      <th>대상 포트</th>
      <th>고정 IP에서 로그가 나타나도록 요구 사항</th>
      <th>고급 네트워킹 필요</th>
      <th>LogForwarding.yaml 포트 정의 필요</th>
    </tr>
    <tr>
      <td rowspan="2" ro>HTTPS(443)</td>
      <td>아니요</td>
      <td>아니요</td>
      <td>아니요</td>
    </tr>
    <tr>
      <td>예</td>
      <td>예, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address">전용 이그레스</a></td>
      <td>아니요</td>
    <tr>
    <tr>
      <td rowspan="2">비표준 포트(예: 8088)</td>
      <td>아니요</td>
      <td>예, <a href="/help/security/configuring-advanced-networking.md#flexible-port-egress-flexible-port-egress">유연한 이그레스</a></td>
      <td>예</td>
    </tr>
    <tr>
      <td>예</td>
      <td>예, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address">전용 이그레스</a></td>
      <td>예</td>
  </tbody>
</table>

>[!NOTE]
>단일 IP 주소에서 로그가 표시되는지 여부는 고급 네트워킹 구성 선택에 따라 결정됩니다.  이 작업을 용이하게 하려면 전용 이그레스를 사용해야 합니다.
>
> 고급 네트워킹 구성은 프로그램 및 환경 수준에서 활성화가 필요한 [2단계 프로세스](/help/security/configuring-advanced-networking.md#configuring-and-enabling-advanced-networking-configuring-enabling)입니다.

AEM 로그(Apache/Dispatcher 포함)의 경우 [고급 네트워킹](/help/security/configuring-advanced-networking.md)을 구성한 경우 `aem.advancedNetworking` 속성을 사용하여 전용 이그레스 IP 주소 또는 VPN을 통해 해당 로그를 전달할 수 있습니다.

아래 예는 고급 네트워킹을 사용하여 표준 HTTPS 포트에서 로깅을 구성하는 방법을 보여줍니다.

```yaml
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      port: 443
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
    aem:
      advancedNetworking: true
```

CDN 로그의 경우 [Fastly 설명서 - 공개 IP 목록](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/)에 설명된 대로 IP 주소를 허용 목록에 추가할 수 있습니다. 공유 IP 주소 목록이 너무 큰 경우, 알려진 IP에서 로그를 최종 대상으로 전송하도록 논리를 작성할 수 있는 https 서버 또는 (Adobe이 아닌) Azure Blob Store로 트래픽을 보내는 것이 좋습니다.

>[!NOTE]
>
>AEM 로그가 표시되는 IP 주소와 동일한 IP 주소에서 CDN 로그가 표시될 수 없습니다. 이는 로그가 AEM Cloud Service가 아닌 Fastly에서 직접 전송되기 때문입니다.
>
>이러한 이유로 고급 네트워킹 VPN 구성과 함께 로그 전달을 사용할 수 없습니다.

## 대상 구성 로깅 중 {#logging-destinations}

특정 고려 사항과 함께 지원되는 로깅 대상에 대한 구성이 아래에 나와 있습니다.

### Amazon {#amazons3}

Amazon S3에 대한 로그 전달은 AEM 및 Dispatcher 로그를 지원하며 CDN 로그는 아직 지원되지 않습니다.

>[!NOTE]
>
>각 로그 파일 유형에 대해 10분마다 정기적으로 S3에 기록되는 로그  이로 인해 기능이 전환되면 로그가 S3에 기록되는 초기 지연이 발생할 수 있습니다.  [이 동작에 대한 추가 정보](https://docs.fluentbit.io/manual/pipeline/outputs/s3#differences-between-s3-and-other-fluent-bit-outputs).

```yaml
kind: "LogForwarding"
version: "1"
data:
  awsS3:
    default:
      enabled: true
      region: "your-bucket-region"
      bucket: "your_bucket_name"
      accessKey: "${{AWS_S3_ACCESS_KEY}}"
      secretAccessKey: "${{AWS_S3_SECRET_ACCESS_KEY}}"
```

S3 로그 전달자를 사용하려면 S3 버킷에 액세스하기 위한 적절한 정책으로 AWS IAM 사용자를 사전 구성해야 합니다.  IAM 사용자 자격 증명을 만드는 방법은 [AWS IAM 사용자 설명서](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)를 참조하십시오.

IAM 정책은 사용자가 `s3:putObject`을(를) 사용할 수 있도록 허용해야 합니다.  예:

```json
 {
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": [
            "s3:PutObject"
        ],
        "Resource": "arn:aws:s3:::your_bucket_name/*"
    }]
}
```

구현 방법에 대한 자세한 내용은 [AWS 버킷 정책 설명서](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html)를 참조하십시오.

>[!NOTE]
>AWS S3에 대한 CDN 로그 지원은 향후에 제공될 예정입니다. 관심 영역을 등록하려면 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)에 전자 메일을 보내십시오.

### Azure Blob 저장소 {#azureblob}

```yaml
kind: "LogForwarding"
version: "1"
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

이전에 제대로 작동한 후 로그 전달이 중지된 경우 구성한 SAS 토큰이 만료되었을 수 있으므로 여전히 유효한지 확인하십시오.

#### Azure Blob 저장소 CDN 로그 {#azureblob-cdn}

전역으로 분산된 각 로깅 서버는 `aemcdn` 폴더 아래에서 몇 초마다 새 파일을 생성합니다. 파일이 만들어지면에 더 이상 추가되지 않습니다. 파일 이름 형식은 YYYY-MM-DDThh:mm:ss.sss-uniqueid.log입니다. 예: 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

예를 들어, 특정 시점에서 다음과 같은 작업을 수행할 수 있습니다.

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

30초 후:

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

각 파일에는 여러 JSON 로그 항목이 포함되어 있으며 각 항목은 별도의 줄에 있습니다. 로그 항목 형식은 [AEM as a Cloud Service에 대한 로깅](/help/implementing/developing/introduction/logging.md)에 설명되어 있으며 각 로그 항목에는 아래 [로그 항목 형식](#log-formats) 섹션에 언급된 추가 속성도 포함되어 있습니다.

#### Azure Blob 저장소 AEM 로그 {#azureblob-aem}

AEM 로그(Apache/Dispatcher 포함)는 다음 명명 규칙을 사용하여 폴더 아래에 표시됩니다.

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpdererror

각 폴더 아래에 하나의 파일이 만들어지고 추가됩니다. 고객은 이 파일의 크기가 너무 커지지 않도록 처리 및 관리를 담당합니다.

[AEM as a Cloud Service에 대한 로깅](/help/implementing/developing/introduction/logging.md)에서 로그 항목 형식을 참조하십시오. 로그 항목에는 아래의 [로그 항목 형식](#log-formats) 섹션에서 언급한 추가 속성도 포함됩니다.

### Datadog {#datadog}

```yaml
kind: "LogForwarding"
version: "1"
data:
  datadog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      tags:
         tag1: value1
         tag2: value2
      
```

#### 고려 사항

* 특정 클라우드 공급자와의 통합 없이 API 키를 만듭니다.
* 태그 속성은 선택 사항입니다
* AEM 로그의 경우 Datadog 소스 태그가 `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` 또는 `aemhttpderror` 중 하나로 설정되어 있습니다
* CDN 로그의 경우 Datadog 소스 태그가 `aemcdn`(으)로 설정됩니다.
* Datadog 서비스 태그가 `adobeaemcloud`(으)로 설정되어 있지만 태그 섹션에서 덮어쓸 수 있습니다
* 수집 파이프라인이 Datadog 태그를 사용하여 전달 로그에 대한 적절한 인덱스를 결정하는 경우 이러한 태그가 로그 전달 YAML 파일에 올바르게 구성되어 있는지 확인하십시오. 태그가 누락되면 파이프라인이 종속된 경우 성공적인 로그 수집이 방해될 수 있습니다.

### Elasticsearch 및 OpenSearch {#elastic}

```yaml
kind: "LogForwarding"
version: "1"
data:
  elasticsearch:
    default:
      enabled: true
      host: "example.com"
      user: "${{ELASTICSEARCH_USER}}"
      password: "${{ELASTICSEARCH_PASSWORD}}"
      pipeline: "ingest pipeline name"
```

#### 고려 사항

* 기본적으로 포트는 443입니다. 선택적으로 `port` 속성으로 재정의할 수 있습니다.
* 자격 증명의 경우 계정 자격 증명이 아닌 배포 자격 증명을 사용해야 합니다. 다음은 이 이미지와 유사할 수 있는 화면에서 생성된 자격 증명입니다.

![탄력적인 배포 자격 증명](/help/implementing/developing/introduction/assets/ec-creds.png)

* AEM 로그의 경우 `index`이(가) `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` 또는 `aemhttpderror` 중 하나로 설정되어 있습니다.
* 선택적 파이프라인 속성은 로그 항목을 적절한 인덱스로 라우팅하도록 구성할 수 있는 Elasticsearch 또는 OpenSearch 수집 파이프라인의 이름으로 설정해야 합니다. 파이프라인의 프로세서 유형을 *script*(으)로 설정하고 스크립트 언어를 *painless*(으)로 설정해야 합니다. 다음은 aemaccess_dev_26_06_2024와 같은 인덱스로 로그 항목을 라우팅하는 샘플 스크립트 스니펫입니다.

```text
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```yaml
kind: "LogForwarding"
version: "1"
data:
  https:
    default:
      enabled: true
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

#### 고려 사항

* URL 문자열에 **https://**&#x200B;이(가) 포함되어야 합니다. 그렇지 않으면 유효성 검사가 실패합니다.
* URL은 포트를 포함할 수 있습니다. 예를 들어, `https://example.com:8443/aem_logs/aem`과 같이 입력합니다. URL 문자열에 포트가 포함되지 않으면 포트 443(기본 HTTPS 포트)이 가정됩니다.

#### HTTPS CDN 로그 {#https-cdn}

웹 요청(POST)은 로그 항목의 배열인 json 페이로드와 함께 지속적으로 전송되며, 로그 항목 형식은 [AEM as a Cloud Service에 대한 로깅](/help/implementing/developing/introduction/logging.md#cdn-log)에 설명되어 있습니다. 추가 속성은 아래의 [로그 항목 형식](#log-formats) 섹션에 설명되어 있습니다.

`sourcetype` 값으로 설정된 `aemcdn` 속성도 있습니다.

>[!NOTE]
>
> 첫 번째 CDN 로그 항목이 전송되기 전에 HTTP 서버가 일회성 요청을 성공적으로 완료해야 합니다. ``/.well-known/fastly/logging/challenge`` 경로로 전송된 요청은 본문의 별표 ``*`` 및 200 상태 코드로 응답해야 합니다.

#### HTTPS AEM 로그 {#https-aem}

AEM 로그(apache/dispatcher 포함)의 경우 [AEM as a Cloud Service에 대한 로깅](/help/implementing/developing/introduction/logging.md)에 설명된 대로 다양한 로그 항목 형식이 포함된 로그 항목의 배열인 json 페이로드와 함께 웹 요청(POST)이 지속적으로 전송됩니다. 추가 속성은 아래의 [로그 항목 형식](#log-formats) 섹션에 설명되어 있습니다.

다음 값 중 하나로 설정된 `Source-Type` 속성도 있습니다.

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpdererror

### New Relic 로그 API {#newrelic-https}

New Relic으로 로그 전달에서는 수집에 New Relic HTTPS API를 활용합니다.  현재 AEM 및 Dispatcher의 로그만 지원하며 CDN 로그는 아직 지원되지 않습니다.

```yaml
  kind: "LogForwarding"
  version: "1"
  data:
    newRelic:
      default:
        enabled: true
        uri: "https://log-api.newrelic.com/log/v1"
        apiKey: "${{NR_API_KEY}}"
```

>[!NOTE]
>
>New Relic에 대한 로그 전달은 고객 소유 New Relic 계정에만 사용할 수 있습니다.
>
>New Relic 로그 API에 대한 CDN 로그 지원이 향후 예정되어 있습니다. 관심 영역을 등록하려면 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)에 전자 메일을 보내십시오.
>
>New Relic은 New Relic 계정이 프로비저닝된 위치를 기반으로 지역별 엔드포인트를 제공합니다.  자세한 내용은 [New Relic 설명서](https://docs.newrelic.com/docs/logs/log-api/introduction-log-api/#endpoint)를 참조하세요.

### Dynatrace 로그 API {#dynatrace-https}

Dynatrace으로 로그 전달에서는 수집에 Dynatrace HTTPS API를 활용합니다.  현재 AEM 및 Dispatcher의 로그만 지원하며 CDN 로그는 아직 지원되지 않습니다.

토큰에 &quot;로그 수집&quot; 범위 속성이 필요합니다.

```yaml
  kind: "LogForwarding"
  version: "1"
  data:
    dynatrace:
      default:
        enabled: true
        environmentId: "${{DYNATRACE_ENVID}}"
        token: "${{DYNATRACE_TOKEN}}"  
```

>[!NOTE]
>Dynatrace 로그 API에 대한 CDN 로그 지원이 향후 예정되어 있습니다. 관심 영역을 등록하려면 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)에 전자 메일을 보내십시오.

### 스플렁크 {#splunk}

```yaml
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
```

#### 고려 사항

* 기본적으로 포트는 443입니다. 필요한 경우 이름이 `port`인 속성으로 재정의할 수 있습니다.
* Sourcetype 필드는 특정 로그에 따라 다음 값 중 하나를 갖습니다. *aemaccess*, *aemerror*,
  *aemrequest*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*
* 필요한 IP가 허용 목록에추가된으로 제공되었지만 로그가 계속 전달되지 않는 경우 Splunk 토큰 유효성 검사를 적용하는 방화벽 규칙이 없는지 확인하십시오. Fastly는 잘못된 Splunk 토큰이 의도적으로 전송되는 초기 유효성 검사 단계를 수행합니다. 방화벽이 잘못된 Splunk 토큰으로 연결을 종료하도록 설정된 경우 유효성 검사 프로세스가 실패하여 Fastly가 로그를 Splunk 인스턴스에 전달할 수 없습니다.

>[!NOTE]
>
> [이전 로그 전달에서 이 셀프 서비스 모델로 마이그레이션](#legacy-migration)하는 경우 Splunk 인덱스로 전송된 `sourcetype` 필드의 값이 변경되었을 수 있으므로 적절하게 조정하십시오.

### 스모 논리 {#sumologic}

Sumo Logic으로의 로그 전달은 AEM 및 Dispatcher 로그를 지원합니다. CDN 로그는 아직 지원되지 않습니다.

데이터 수집을 위해 Sumo 논리를 구성할 때 단일 문자열에 호스트, receiverURI 및 개인 키를 제공하는 &quot;HTTP Source 주소&quot;가 표시됩니다.  예:

`https://collectors.de.sumologic.com/receiver/v1/http/ZaVnC...`

위의 `/`설정[&#x200B; 섹션에 설명된 대로 URL의 마지막 섹션(](/help/operations/config-pipeline.md#secret-env-vars) 없이)을 복사한 다음 [CloudManager 보안 환경 변수](#setup)(으)로 추가한 다음 구성에서 해당 변수를 참조해야 합니다.  예가 아래에 제공됩니다.

```yaml
kind: "LogForwarding"
version: "1"
data:
  sumoLogic:
    default:
      enabled: true
      collectorURL: "https://collectors.de.sumologic.com/receiver/v1/http"
      privateKey: "${{SUMOLOGIC_PRIVATE_KEY}}"
      index: "aem-logs"
```

>[!NOTE]
>SumoLogic에 대한 CDN 로그 지원이 향후 예정되어 있습니다. 관심 영역을 등록하려면 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)에 전자 메일을 보내십시오.
>
> &quot;색인&quot; 필드 기능을 사용하려면 Sumo Logic Enterprise 구독이 필요합니다.  Enterprise가 아닌 구독의 로그는 기본적으로 `sumologic_default` 파티션으로 라우팅됩니다.  자세한 내용은 [Sumo 논리 분할 설명서](https://help.sumologic.com/docs/search/optimize-search-partitions/)를 참조하십시오.

## 로그 항목 형식 {#log-formats}

각 로그 유형(CDN 로그 및 Apache/Dispatcher을 포함한 AEM 로그)의 형식은 [AEM as a Cloud Service에 대한 로깅](/help/implementing/developing/introduction/logging.md)을 참조하십시오.

여러 프로그램 및 환경의 로그를 동일한 로깅 대상으로 전달할 수 있으므로 로깅 문서에 설명된 출력 외에 각 로그 항목에는 다음 속성이 포함됩니다.

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

예를 들어 속성은 다음 값을 가질 수 있습니다.

```text
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## 이전 로그 전달에서 마이그레이션 {#legacy-migration}

셀프서비스 모델을 통해 로그 전달 구성을 수행하기 전에 고객에게 지원 티켓을 열도록 요청했으며, 여기서 Adobe이 통합을 시작합니다.

Adobe에서 이러한 방식으로 설정했던 고객은 편리하게 셀프서비스 모델에 적응할 수 있습니다. 이렇게 전환하는 데는 몇 가지 이유가 있습니다.

* 새 환경(예: 새 개발 환경 또는 RDE)이 프로비저닝되었습니다.
* 기존 Splunk 끝점 또는 자격 증명에 대한 변경.
* Adobe은 CDN 로그를 사용하기 전에 로그 전달을 설정했으며 CDN 로그를 수신하려고 합니다.
* 시간에 민감한 변화가 필요하기 전에 조직에서 지식을 갖도록 셀프서비스 모델에 적극적으로 적응하려는 의식적인 결정입니다.

마이그레이션할 준비가 되면 이전 섹션에서 설명한 대로 YAML 파일을 구성하면 됩니다. Cloud Manager 구성 파이프라인을 사용하여 구성을 적용해야 하는 각 환경에 배포합니다.

구성이 모든 환경에 배포되어 모두 셀프서비스 제어 하에 있는 것이 좋지만 필수는 아닙니다. 구성하지 않은 경우 Adobe에서 구성한 환경과 셀프 서비스 방식으로 구성한 환경을 잊어버릴 수 있습니다.

>[!NOTE]
>
>Splunk 인덱스로 전송된 `sourcetype` 필드의 값이 변경되었을 수 있으므로 적절하게 조정하십시오.
>
>이전에 Adobe 지원에서 구성한 환경에 로그 전달이 배포되면 최대 몇 시간 동안 중복 로그를 받을 수 있습니다. 이 문제는 결국 자동으로 해결됩니다.
