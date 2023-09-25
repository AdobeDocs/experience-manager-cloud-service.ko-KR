---
title: 범용 편집기를 사용한 로컬 AEM 개발
description: 범용 편집기가 개발 목적으로 로컬 AEM 인스턴스에서 편집을 지원하는 방법에 대해 알아봅니다.
source-git-commit: bf09c31baf209f5315e35f47c0d79c2b4365d3d3
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---


# 범용 편집기를 사용한 로컬 AEM 개발 {#local-dev-ue}

범용 편집기가 개발 목적으로 로컬 AEM 인스턴스에서 편집을 지원하는 방법에 대해 알아봅니다.

이 문서에서는 범용 편집기를 사용하여 AEM에서 로컬로 개발할 수 있도록 범용 편집기 서비스의 로컬 복사본과 함께 HTTPS로 AEM을 실행하는 방법을 설명합니다.

## HTTPS에서 실행되도록 AEM 설정 {#aem-https}

HTTPS로 보호되는 외부 프레임 내에서는 비보안 HTTP 프레임을 로드할 수 없습니다. 범용 편집기 서비스는 HTTPS에서 실행되므로 AEM 또는 다른 원격 페이지도 HTTPS에서 실행해야 합니다.

이렇게 하려면 HTTPS에서 실행하도록 AEM을 설정해야 합니다. 개발 목적으로 자체 서명된 인증서를 사용할 수 있습니다.

사용할 수 있는 자체 서명된 인증서를 포함하여 HTTPS에서 실행되는 AEM을 설정하는 방법은 이 문서를 참조하십시오.

## 범용 편집기 서비스 설치 {#install-ue-service}

범용 편집기 서비스는 범용 편집기 및 백엔드 시스템을 바인딩합니다. 공식 범용 편집기 서비스는 전 세계적으로 호스팅되므로 로컬 AEM 인스턴스를 인터넷에 노출해야 합니다. 이를 방지하기 위해 범용 편집기 서비스의 로컬 복사본을 실행할 수 있습니다.

[NodeJS 버전 16](https://nodejs.org/en/download/releases) 는 범용 편집기 서비스의 로컬 복사본을 실행하는 데 필요합니다.

범용 편집기 서비스는 AEM Engineering에서 직접 배포합니다. 로컬 사본은 VIP 프로그램의 엔지니어링 담당자에게 문의하십시오.

엔지니어링에서 다음을 제공합니다. `universal-editor-service.cjs` 파일. 로컬 개발 환경에 저장합니다.

## HTTPS로 유니버설 편집기 서비스를 실행할 인증서 만들기 {#ue-https}

또한 개발 환경에서 HTTPS로 실행하려면 유니버설 편집기 서비스에 인증서가 필요합니다.

다음 명령을 실행합니다.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

이 명령은 `key.pem` 및 a `certificate.pem` 파일. 이 파일을 와 동일한 경로에 저장합니다. `universal-editor-service.cjs` 파일.

## 범용 편집기 서비스 구성 설정 {#setting-up-service}

범용 편집기 서비스를 로컬로 실행하려면 NodeJS에 여러 환경 변수를 설정해야 합니다.

과 동일한 경로에서 `universal-editor-service.cjs`, `key.pem` 및 `certificate.pem` 파일, 만들기 `.env` 다음 내용이 포함된 파일입니다.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

변수에는 다음과 같은 의미가 있습니다.

* `EXPRESS_PORT`: 유니버설 편집기 서비스가 수신하는 포트를 정의합니다
* `EXPRESS_PRIVATE`: 를 가리킵니다. [이전에 만든 개인 키,](#ue-https) `key.pem`
* `EXPRESS_CERT`: 를 가리킵니다. [이전에 만든 인증서,](#ue-https) `certificate.pem`
* `NODE_TLS_REJECT_UNAUTHORIZED=0`: 자체 서명된 인증서 수락

## 범용 편집기 서비스 실행 {#running-ue}

범용 편집기 서비스를 시작하려면 다음 명령을 실행합니다.

```text
$ node ./universal-editor-service.cjs
```

터미널에 다음 정보를 출력해야 합니다.

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

서비스가 HTTP 서버가 아닌 HTTPS 서버를 시작하는지 확인합니다.

## 글로벌 서비스 대신 로컬 범용 편집기 서비스 사용 {#using-local-ue}

범용 편집기는 페이지 계측 방법을 기반으로 페이지를 편집하는 데 사용할 범용 편집기 서비스를 알고 있습니다. 이 작업은 범용 편집기에 로드된 페이지의 메타 태그를 통해 수행됩니다.

로컬 범용 편집기 서비스를 사용하여 페이지를 편집하려면 다음 메타 태그를 설정해야 합니다.

```
<meta name="urn:adobe:aem:editor:endpoint" content="https://localhost:8000">
```

설정되면 모든 콘텐츠 업데이트 호출이 `https://localhost:8000` 기본 범용 편집기 서비스 대신

>[!TIP]
>
>페이지가 전역 유니버설 편집기 서비스를 사용하도록 계측되는 방법에 대한 자세한 내용은 문서를 참조하십시오 [AEM에서 유니버설 편집기 시작하기](/help/implementing/universal-editor/getting-started.md#instrument-page)

## 로컬 범용 편집기 서비스를 사용하여 페이지 편집 {#editing}

포함 [로컬에서 실행되는 유니버설 편집기 서비스](#running-ue) 및 내 [로컬 서비스를 사용하도록 계측된 콘텐츠 페이지](#using-loca-ue) 이제 편집기를 시작할 수 있습니다.

1. 브라우저를 열고 다음 작업을 수행합니다. `https://localhost:8000/`.
1. 브라우저에서 수락하도록 지시합니다. [자체 서명된 인증서.](#ue-https)
1. 자체 서명된 인증서를 신뢰할 수 있으면 로컬 유니버설 편집기 서비스를 사용하여 페이지를 편집할 수 있습니다.
