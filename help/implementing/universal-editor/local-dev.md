---
title: 자체 범용 편집기 서비스 실행
description: 로컬 개발 또는 자체 인프라의 일부로 자체 범용 편집기 서비스를 실행하는 방법에 대해 알아봅니다.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 100%

---


# 자체 범용 편집기 서비스 실행 {#local-ue-service}

로컬 개발 또는 자체 인프라의 일부로 자체 범용 편집기 서비스를 실행하는 방법에 대해 알아봅니다.

>[!NOTE]
>
>로컬 범용 편집기 서비스는 Edge Delivery Services를 사용하여 AEM 작성을 사용하는 프로젝트에 필요하지 않거나 지원되지 않습니다.

## 개요 {#overview}

범용 편집기 서비스는 범용 편집기와 백엔드 시스템을 바인딩하는 서비스입니다. 범용 편집기를 위해 로컬에서 개발하려면 범용 편집기 서비스의 로컬 사본을 실행해야 합니다. 그 이유는 다음과 같습니다.

* Adobe의 공식 범용 편집기 서비스는 전역적으로 호스팅되므로 로컬 AEM 인스턴스가 인터넷에 노출되어야 합니다.
* 로컬 AEM SDK로 개발하는 경우 Adobe의 범용 편집기 서비스는 인터넷에서 액세스할 수 없습니다.
* AEM 인스턴스에 IP 제한이 있고 Adobe의 범용 편집기 서비스가 정의된 IP 범위에 있지 않으면 직접 호스팅할 수 있습니다.

## 사용 사례 {#use-cases}

자체 범용 편집기 서비스 사본은 다음과 같은 경우에 유용합니다.

* 범용 편집기와 함께 사용하기 위해 AEM에서 로컬로 개발합니다.
* Adobe의 범용 편집기 서비스와 독립적으로 자체 인프라의 일부로 자체 범용 편집기 서비스를 실행합니다.

두 가지 사용 사례가 모두 지원됩니다. 이 문서는 범용 편집기 서비스의 로컬 사본과 함께 HTTPS에서 AEM을 실행하는 방법을 설명합니다.

자체 인프라의 일부로 자체 범용 편집기 서비스를 실행하려면 로컬 개발 예시와 동일한 단계를 따르면 됩니다.

## HTTPS에서 실행할 AEM 설정 {#aem-https}

HTTPS로 보호되는 외부 프레임 내에서 비보안 HTTP 프레임을 로드할 수 없습니다. 범용 편집기 Service가 HTTPS에서 실행되므로 AEM 또는 다른 원격 페이지도 HTTPS에서 실행되어야 합니다.

이를 위해 HTTPS에서 실행하려면 AEM을 설정해야 합니다. 개발 목적으로 자체 서명된 인증서를 사용할 수 있습니다.

제공되는 자체 서명된 인증서를 포함하여 HTTPS에서 실행 중인 AEM을 설정하는 방법에 대한 자세한 내용은 [이 문서를 참조](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html)하십시오.

## 범용 편집기 서비스 설치 {#install-ue-service}

범용 편집기 서비스는 범용 편집기의 전체 사본이 아니라 해당 기능의 하위 집합일 뿐이며, 로컬 AEM 환경에서 발생하는 호출이 인터넷을 통해 라우팅되지 않고 사용자가 제어하는 정의된 엔드포인트에서 라우팅되도록 보장합니다.

[NodeJS 버전 20](https://nodejs.org/en/download/releases)은 범용 편집기 서비스의 로컬 사본을 실행하는 데 필요합니다.

범용 편집기 서비스는 소프트웨어 배포를 통해 사용할 수 있습니다. 액세스 방법에 자세한 내용은 [소프트웨어 배포 설명서](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)를 참조하십시오.

`universal-editor-service.cjs` 파일을 소프트웨어 배포에서 로컬 개발 환경으로 저장합니다.

## HTTPS를 사용하여 범용 편집기 Service를 실행할 인증서 만들기 {#ue-https}

또한 범용 편집기 Service를 사용하려면 개발 환경의 HTTPS에서 실행할 인증서가 필요합니다.

다음 명령을 실행합니다.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

명령은 `key.pem` 및 `certificate.pem` 파일을 생성합니다. 이 파일을 `universal-editor-service.cjs` 파일과 같은 경로로 저장합니다.

## 범용 편집기 서비스 구성 설정 {#setting-up-service}

범용 편집기 Service를 로컬에서 실행하려면 NodeJS에서 여러 환경 변수를 설정해야 합니다.

`universal-editor-service.cjs`, `key.pem` 및 `certificate.pem` 파일과 같은 경로에서 다음 콘텐츠로 `.env` 파일을 만듭니다.

```text
UES_PORT=8000
UES_PRIVATE_KEY=./key.pem
UES_CERT=./certificate.pem
UES_TLS_REJECT_UNAUTHORIZED=false
UES_CORS_PRIVATE_NETWORK=true
```

이것은 예시의 로컬 개발에 필요한 최소값입니다.

>[!NOTE]
>
>Chrome 버전 130 이상을 실행하는 경우 `UES_CORS_PRIVATE_NETWORK` 옵션을 사용하여 [비공개 네트워크 액세스](https://wicg.github.io/private-network-access/#private-network-request)에 대한 CORS 헤더 전송을 활성화해야 합니다.


다음 표는 이러한 값과 사용 가능한 추가 값을 자세히 설명합니다.

| 값 | 선택 사항 | 기본값 | 설명 |
|---|---|---|---|
| `UES_PORT` | 예 | `8080` | 서버가 실행되는 포트 |
| `UES_PRIVATE_KEY` | 예 | 없음 | HTTPS 서버의 비공개 키 경로 |
| `UES_CERT` | 예 | 없음 | HTTPS 서버의 인증 파일 경로 |
| `UES_TLS_REJECT_UNAUTHORIZED` | 예 | `true` | 승인되지 않은 TLS 연결 거부 |
| `UES_DISABLE_IMS_VALIDATION` | 예 | `false` | IMS 유효성 검사 비활성화 |
| `UES_ENDPOINT_MAPPING` | 예 | 비어 있음 | 내부 재작성을 위한 엔드포인트 매핑<br>예시: `UES_ENDPOINT_MAPPING='[{"https://your-public-facing-author-domain.net": "http://10.0.0.1:4502"}]'`<br>결과: 범용 편집기 서비스는 제공된 연결 `https://your-public-facing-author-domain.net` 대신 `http://10.0.0.1:4502`에 연결합니다. |
| `UES_LOG_LEVEL` | 예 | `info` | 서버에 대한 로그 수준, 가능한 값은 `silly`, `trace`, `debug`, `verbose`, `info`, `log`, `warn`, `error`, 및 `fatal`입니다. |
| `UES_SPLUNK_HEC_URL` | 예 | 없음 | Splunk 엔드포인트에 대한 HEC URL |
| `UES_SPLUNK_TOKEN` | 예 | 없음 | Splunk 토큰 |
| `UES_SPLUNK_INDEX` | 예 | 없음 | 로그를 쓸 인덱스 |
| `UES_SPLUNK_SOURCE` | 예 | `universal-editor-service` | Splunk 로그에 있는 소스 이름 |
| `UES_CORS_PRIVATE_NETWORK` | 예 | `false` | [비공개 네트워크](https://wicg.github.io/private-network-access/#private-network-request)를 허용하기 위해 CORS 헤더 전송을 활성화합니다. Chrome 버전 130 이상 사용자를 위해 필요합니다. |

>[!NOTE]
>
>범용 편집기의 [2024.08.13 릴리스](/help/release-notes/universal-editor/current.md) 이전에는 `.env` 파일에 다음 변수가 필요했습니다. 이러한 값은 이전 버전과의 호환성을 위해 2024년 10월 1일까지 지원됩니다.
>
>`EXPRESS_PORT=8000`
>`EXPRESS_PRIVATE_KEY=./key.pem`
>`EXPRESS_CERT=./certificate.pem`
>`NODE_TLS_REJECT_UNAUTHORIZED=0`

## 범용 편집기 Service 실행 {#running-ue}

범용 편집기 서비스를 시작하려면 다음 명령을 실행합니다.

```text
$ node ./universal-editor-service.cjs
```

터미널로 다음 항목이 출력되어야 합니다.

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

서비스가 HTTP 서버가 아닌 HTTPS 서버를 시작하는지 확인합니다.

## 글로벌 서비스 대신 로컬 범용 편집기 Service 사용 {#using-local-ue}

범용 편집기는 페이지 구성 방식에 따라 페이지를 편집하는 데 사용할 범용 편집기 Service를 인식합니다. 이는 범용 편집기에 로드된 페이지의 메타 태그를 통해 수행됩니다.

로컬 범용 편집기 Service를 사용하여 페이지를 편집하려면 다음 메타 태그를 설정해야 합니다.

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

설정되면 모든 콘텐츠 업데이트 호출이 기본 범용 편집기 Service 대신 `https://localhost:8000`으로 이동하는 것을 확인할 수 있습니다.

>[!NOTE]
>
>`https://localhost:8000`에 직접 액세스를 시도하면 `404` 오류가 발생합니다. 이는 예상된 비헤이비어입니다.
>
>로컬 범용 편집기 서비스에 대한 액세스를 테스트하려면 `https://localhost:8000/corslib/LATEST`를 사용합니다. 자세한 내용은 [다음 섹션](#editing)을 참조하십시오.

>[!TIP]
>
>페이지를 구성하여 글로벌 범용 편집기 Service를 사용하는 방법에 대한 자세한 내용은 [AEM에서 범용 편집기 시작하기](/help/implementing/universal-editor/getting-started.md#instrument-page) 문서를 참조하십시오.

## 로컬 범용 편집기 Service를 사용하여 페이지 편집 {#editing}

[범용 편집기 서비스가 로컬에서 실행](#running-ue)되고 [콘텐츠 페이지가 로컬 서비스를 사용하도록 계측](/help/implementing/universal-editor/getting-started.md)되면 편집기를 시작할 수 있습니다.

1. 브라우저를 열고 `https://localhost:8000/ping`으로 이동합니다.
1. [자체 서명된 인증서](#ue-https)를 허용하도록 브라우저를 내보냅니다.
1. 자체 서명된 인증서를 신뢰하는 경우 로컬 범용 편집기 서비스를 사용하여 페이지를 편집할 수 있습니다.

